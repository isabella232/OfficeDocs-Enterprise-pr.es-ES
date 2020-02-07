---
title: Fase 3 de la autenticación federada de alta disponibilidad configurar los servidores de AD FS
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 202b76ff-74a6-4486-ada1-a9bf099dab8f
description: 'Resumen: Cree y configure los servidores de los Servicios de federación de Active Directory (AD FS) para la autenticación federada de alta disponibilidad para Office 365 en Microsoft Azure.'
ms.openlocfilehash: 5ac87b0d19c43e8711e188d1a0f6a7f33a37871f
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840157"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="8ac02-103">Fase 3 de la autenticación federada de alta disponibilidad: Configurar servidores de AD FS</span><span class="sxs-lookup"><span data-stu-id="8ac02-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

<span data-ttu-id="8ac02-104">En esta fase de la implementación de alta disponibilidad para la autenticación federada de Office 365 en servicios de infraestructura de Azure, se crea un equilibrador de carga interno y dos servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="8ac02-104">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="8ac02-105">Debe completar esta fase antes de continuar con la [fase 4: configurar servidores proxy de aplicación web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span><span class="sxs-lookup"><span data-stu-id="8ac02-105">You must complete this phase before moving on to [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span></span> <span data-ttu-id="8ac02-106">Consulte todas las fases en [Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="8ac02-106">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="8ac02-107">Crear las máquinas virtuales del servidor de AD FS en Azure</span><span class="sxs-lookup"><span data-stu-id="8ac02-107">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="8ac02-p102">Use el siguiente bloque de comandos de PowerShell para crear las máquinas virtuales de los dos servidores de AD FS. En este conjunto de comandos de PowerShell se usan valores de las tablas siguientes:</span><span class="sxs-lookup"><span data-stu-id="8ac02-p102">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers. This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="8ac02-110">Tabla N, para las máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="8ac02-110">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="8ac02-111">Tabla R, para los grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="8ac02-111">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="8ac02-112">Tabla V, para la configuración de la red virtual</span><span class="sxs-lookup"><span data-stu-id="8ac02-112">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="8ac02-113">Tabla S, para las subredes</span><span class="sxs-lookup"><span data-stu-id="8ac02-113">Table S, for your subnets</span></span>
    
- <span data-ttu-id="8ac02-114">Tabla I, para las direcciones IP estáticas</span><span class="sxs-lookup"><span data-stu-id="8ac02-114">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="8ac02-115">Tabla A, para los conjuntos de disponibilidad</span><span class="sxs-lookup"><span data-stu-id="8ac02-115">Table A, for your availability sets</span></span>
    
<span data-ttu-id="8ac02-116">Recuerde que ha definido la tabla M en la [fase 2: configurar los controladores de dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) y las tablas R, V, S, I y A en la [fase 1: configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="8ac02-116">Recall that you defined Table M in [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="8ac02-117">Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ac02-117">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="8ac02-118">Consulte Introducción [a Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span><span class="sxs-lookup"><span data-stu-id="8ac02-118">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="8ac02-119">Primero, cree un equilibrador de carga interno de Azure para los dos servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="8ac02-119">First, you create an Azure internal load balancer for the two AD FS servers.</span></span> <span data-ttu-id="8ac02-120">Especifique los valores de las variables, quitando \< y > caracteres.</span><span class="sxs-lookup"><span data-stu-id="8ac02-120">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="8ac02-121">Después de especificar todos los valores correctos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8ac02-121">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="8ac02-122">Para generar bloques de comandos de PowerShell listos para ejecutar en función de la configuración personalizada, use este [libro de configuración de Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span><span class="sxs-lookup"><span data-stu-id="8ac02-122">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up key variables
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$privIP="<Table I - Item 4 - Value column>"
$rgName=<Table R - Item 4 - Resource group name column>"

$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$frontendIP=New-AzLoadBalancerFrontendIpConfig -Name "ADFSServers-LBFE" -PrivateIPAddress $privIP -Subnet $subnet
$beAddressPool=New-AzLoadBalancerBackendAddressPoolConfig -Name "ADFSServers-LBBE"

$healthProbe=New-AzLoadBalancerProbeConfig -Name WebServersProbe -Protocol "TCP" -Port 443 -IntervalInSeconds 15 -ProbeCount 2
$lbrule=New-AzLoadBalancerRuleConfig -Name "HTTPSTraffic" -FrontendIpConfiguration $frontendIP -BackendAddressPool $beAddressPool -Probe $healthProbe -Protocol "TCP" -FrontendPort 443 -BackendPort 443
New-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers" -Location $locName -LoadBalancingRule $lbrule -BackendAddressPool $beAddressPool -Probe $healthProbe -FrontendIpConfiguration $frontendIP
```

<span data-ttu-id="8ac02-123">Después, cree las máquinas virtuales del servidor de AD FS.</span><span class="sxs-lookup"><span data-stu-id="8ac02-123">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="8ac02-124">Después de especificar todos los valores correctos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8ac02-124">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table R - Item 2 - Subnet name column>"
$avName="<Table A - Item 2 - Availability set name column>"
$rgNameTier="<Table R - Item 2 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName
$backendSubnet=Get-AzVirtualNetworkSubnetConfig -Name $subnetName -VirtualNetwork $vnet
$webLB=Get-AzLoadBalancer -ResourceGroupName $rgName -Name "ADFSServers"

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName

# Create the first ADFS server virtual machine
$vmName="<Table M - Item 4 - Virtual machine name column>"
$vmSize="<Table M - Item 4 - Minimum size column>"
$staticIP="<Table I - Item 5 - Value column>"
$diskStorageType="<Table M - Item 4 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second AD FS virtual machine
$vmName="<Table M - Item 5 - Virtual machine name column>"
$vmSize="<Table M - Item 5 - Minimum size column>"
$staticIP="<Table I - Item 6 - Value column>"
$diskStorageType="<Table M - Item 5 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName  -Subnet $backendSubnet -LoadBalancerBackendAddressPool $webLB.BackendAddressPools[0] -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second AD FS server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

```

> [!NOTE]
> <span data-ttu-id="8ac02-p105">Como estas máquinas virtuales son para una aplicación de intranet, no se les asigna una dirección IP pública ni una etiqueta de nombre de dominio DNS, ni se exponen a Internet. Pero esto también quiere decir que no podrá conectarse a estas desde Azure Portal. La opción **Conectar** no estará disponible al ver las propiedades de la máquina virtual. Use la herramienta Conexión a Escritorio remoto u otra herramienta de Escritorio remoto para conectarse a la máquina virtual con su dirección IP privada o con el nombre DNS de la intranet.</span><span class="sxs-lookup"><span data-stu-id="8ac02-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="8ac02-p106">Por cada máquina virtual, use el cliente de Escritorio remoto que prefiera y cree una conexión a Escritorio remoto. Use el nombre DNS de la intranet o el nombre de equipo y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="8ac02-p106">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="8ac02-131">Para cada máquina virtual, únase al dominio de servicios de dominio de Active Directory (AD DS) adecuado con estos comandos en el símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ac02-131">For each virtual machine, join them to the appropriate Active Directory Domain Services (AD DS) domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="8ac02-132">Esta es la configuración completada después de la finalización correcta de esta fase, con los nombres de equipo de marcadores de posición.</span><span class="sxs-lookup"><span data-stu-id="8ac02-132">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="8ac02-133">**Fase 3: Equilibrador de carga interno y servidores de AD FS para la infraestructura de autenticación federada de alta disponibilidad en Azure**</span><span class="sxs-lookup"><span data-stu-id="8ac02-133">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 3 de la infraestructura de autenticación federada de Office 365 de alta disponibilidad en Azure con los servidores de AD FS](media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="8ac02-135">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="8ac02-135">Next step</span></span>

<span data-ttu-id="8ac02-136">Use [Phase 4: configure Web Application proxys](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) para seguir configurando esta carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="8ac02-136">Use [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="8ac02-137">Vea también</span><span class="sxs-lookup"><span data-stu-id="8ac02-137">See Also</span></span>

[<span data-ttu-id="8ac02-138">Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="8ac02-138">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="8ac02-139">Identidad federada para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="8ac02-139">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)


