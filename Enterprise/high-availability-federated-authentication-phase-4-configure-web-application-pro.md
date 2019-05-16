---
title: Fase 4 de la autenticación federada de alta disponibilidad configurar servidores proxy de aplicación Web
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'Resumen: Configure los servidores proxy de aplicación web para la autenticación federada de alta disponibilidad para Office 365 en Microsoft Azure.'
ms.openlocfilehash: fa8f5d278283f66bda0aa9efb0dddf40e52ee1a6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067336"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a>Fase 4 de la autenticación federada de alta disponibilidad: Configurar los proxy de aplicación web

 **Resumen:** Configure los servidores proxy de aplicación web para la autenticación federada de alta disponibilidad para Office 365 en Microsoft Azure.
  
En esta fase de la implementación de alta disponibilidad para la autenticación federada de Office 365 en servicios de infraestructura de Azure, se crea un equilibrador de carga interno y dos servidores de AD FS.
  
Debe completar esta fase antes de pasar a la [fase 5 de la autenticación federada de alta disponibilidad: configurar la autenticación federada para Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Consulte todas las fases en [Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a>Crear el equilibrador de carga accesible desde Internet en Azure

Debe crear un equilibrador de carga accesible desde Internet para que Azure distribuya el tráfico de autenticación de cliente entrante desde Internet uniformemente entre los dos servidores proxy de aplicación Web.
  
> [!NOTE]
> Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell. Visite [Get started with Azure PowerShell cmdlets (Introducción a los cmdlets de Azure)](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/). 
  
Cuando haya proporcionado los valores de ubicación y grupo de recursos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en PowerShell ISE.
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
# Set up key variables
$locName="<your Azure location>"
$rgName="<Table R - Item 4 - Resource group name column>"

$publicIP=New-AzPublicIpAddress -ResourceGroupName $rgName -Name "WebProxyPublicIP" -Location $LocName -AllocationMethod "Static"
$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "WebAppProxyServers-LBFE" -PublicIpAddress $publicIP
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "WebAppProxyServers-LBBE"
$healthProbe=New-AzLoadBalancerProbeConfig -Name "WebServersProbe" -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "WebTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

Para mostrar la dirección IP pública asignada al equilibrador de carga accesible desde Internet, ejecute estos comandos en el símbolo del sistema de Azure PowerShell en el equipo local:
  
```
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a>Determinar el FQDN del servicio de Federación y crear registros DNS

Debe determinar el nombre DNS para identificar el nombre del servicio de Federación en Internet. Azure AD Connect configurará Office 365 con este nombre en la fase 5, que pasará a formar parte de la dirección URL que Office 365 envía a los clientes que se conectan para obtener un token de seguridad. Un ejemplo es fs.contoso.com (FS significa servicio de Federación).
  
Una vez que tenga el servicio de Federación FQDN, cree un registro de dominio DNS público a para el servicio de Federación FQDN que se resuelve en la dirección IP pública del equilibrador de carga de Azure accesible desde Internet.
  
|**Name**|**Type**|**TTL**|**Value**|
|:-----|:-----|:-----|:-----|
|servicio de Federación FQDN  <br/> |A  <br/> |3600  <br/> |Dirección IP pública del equilibrador de carga de Azure accesible desde Internet (mostrado por el comando **write-host** en la sección anterior) <br/> |
   
Aquí le mostramos un ejemplo:
  
|**Name**|**Type**|**TTL**|**Value**|
|:-----|:-----|:-----|:-----|
|fs.contoso.com  <br/> |A  <br/> |3600  <br/> |131.107.249.117  <br/> |
   
A continuación, agregue un registro de dirección DNS al espacio de nombres DNS privado de su organización que resuelva el FQDN del servicio de Federación en la dirección IP privada asignada al equilibrador de carga interno para los servidores AD FS (tabla I, elemento 4, columna valor).
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a>Crear las máquinas virtuales del servidor de proxy de aplicación web en Azure

Use el siguiente bloque de comandos de Azure PowerShell para crear las máquinas virtuales para los dos servidores proxy de aplicación Web. 
  
Tenga en cuenta que los siguientes conjuntos de comandos de Azure PowerShell usan valores de las tablas siguientes:
  
- Tabla N, para las máquinas virtuales
    
- Tabla R, para los grupos de recursos
    
- Tabla V, para la configuración de la red virtual
    
- Tabla S, para las subredes
    
- Tabla I, para las direcciones IP estáticas
    
- Tabla A, para los conjuntos de disponibilidad
    
Recuerde que ha definido la tabla M en la [fase 2 de la autenticación federada de alta disponibilidad: configurar los controladores de dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) y las tablas R, V, S, I y A en la [fase 1 de la autenticación federada de alta disponibilidad: configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md).
  
Después de especificar todos los valores correctos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en PowerShell ISE.
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 3 - Subnet name column>"
$avName="<Table A - Item 3 - Availability set name column>"
$rgNameTier="<Table R - Item 3 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "WebAppProxyServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first web application proxy server virtual machine
$vmName="<Table M - Item 6 - Virtual machine name column>"
$vmSize="<Table M - Item 6 - Minimum size column>"
$staticIP="<Table I - Item 7 - Value column>"
$diskStorageType="<Table M - Item 6 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second web application proxy virtual machine
$vmName="<Table M - Item 7 - Virtual machine name column>"
$vmSize="<Table M - Item 7 - Minimum size column>"
$staticIP="<Table I - Item 8 - Value column>"
$diskStorageType="<Table M - Item 7 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second web application proxy server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Como estas máquinas virtuales son para una aplicación de intranet, no se les asigna una dirección IP pública ni una etiqueta de nombre de dominio DNS, ni se exponen a Internet. Pero esto también quiere decir que no podrá conectarse a estas desde Azure Portal. La opción **Conectar** no estará disponible al ver las propiedades de la máquina virtual. Use el accesorio conexión a escritorio remoto u otra herramienta de escritorio remoto para conectarse a la máquina virtual usando su dirección IP privada o el nombre DNS de la intranet y las credenciales de la cuenta de administrador local.
  
Esta es la configuración completada después de la finalización correcta de esta fase, con los nombres de equipo de marcadores de posición.
  
**Fase 4: el equilibrador de carga accesible desde Internet y los servidores proxy de aplicación web para la infraestructura de autenticación federada de alta disponibilidad en Azure**

![Fase 4 de la infraestructura de autenticación federada de Office 365 de alta disponibilidad en Azure con los servidores proxy de aplicación Web](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a>Paso siguiente

Use la [fase 5 de la autenticación federada de alta disponibilidad: configurar la autenticación federada para Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) para seguir configurando esta carga de trabajo.
  
## <a name="see-also"></a>Vea también

[Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[Identidad federada para el entorno de desarrollo y pruebas de Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
  
[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)

[Opciones de autenticación federada](about-office-365-identity.md#federated-authentication-options)


