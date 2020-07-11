---
title: Fase 4 de la autenticación federada de alta disponibilidad configurar servidores proxy de aplicación Web
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
ms.assetid: 1c903173-67cd-47da-86d9-d333972dda80
description: 'Resumen: Configure los servidores proxy de aplicación web para la autenticación federada de alta disponibilidad para Microsoft 365 en Microsoft Azure.'
ms.openlocfilehash: 005497f9da7986fb4538b4d4c9699e55fe26fa65
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102498"
---
# <a name="high-availability-federated-authentication-phase-4-configure-web-application-proxies"></a><span data-ttu-id="1e348-103">Fase 4 de la autenticación federada de alta disponibilidad: Configurar los proxy de aplicación web</span><span class="sxs-lookup"><span data-stu-id="1e348-103">High availability federated authentication Phase 4: Configure web application proxies</span></span>

<span data-ttu-id="1e348-104">En esta fase de implementación de alta disponibilidad para la autenticación federada de Microsoft 365 en los servicios de infraestructura de Azure, se crea un equilibrador de carga interno y dos servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="1e348-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="1e348-105">Debe completar esta fase antes de pasar a la [fase 5: configurar la autenticación federada para Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span><span class="sxs-lookup"><span data-stu-id="1e348-105">You must complete this phase before moving on to [Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md).</span></span> <span data-ttu-id="1e348-106">Consulte [implementar la autenticación federada de alta disponibilidad para Microsoft 365 en Azure en](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) todas las fases.</span><span class="sxs-lookup"><span data-stu-id="1e348-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-internet-facing-load-balancer-in-azure"></a><span data-ttu-id="1e348-107">Crear el equilibrador de carga accesible desde Internet en Azure</span><span class="sxs-lookup"><span data-stu-id="1e348-107">Create the Internet-facing load balancer in Azure</span></span>

<span data-ttu-id="1e348-108">Debe crear un equilibrador de carga accesible desde Internet para que Azure distribuya el tráfico de autenticación de cliente entrante desde Internet uniformemente entre los dos servidores proxy de aplicación Web.</span><span class="sxs-lookup"><span data-stu-id="1e348-108">You must create an Internet-facing load balancer so that Azure distributes the incoming client authentication traffic from the Internet evenly among the two web application proxy servers.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1e348-109">Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e348-109">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="1e348-110">Consulte Introducción [a Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span><span class="sxs-lookup"><span data-stu-id="1e348-110">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="1e348-111">Cuando haya proporcionado los valores de ubicación y grupo de recursos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1e348-111">When you have supplied location and resource group values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="1e348-112">Para generar bloques de comandos de PowerShell listos para ejecutar en función de la configuración personalizada, use este [libro de configuración de Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span><span class="sxs-lookup"><span data-stu-id="1e348-112">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
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

<span data-ttu-id="1e348-113">Para mostrar la dirección IP pública asignada al equilibrador de carga accesible desde Internet, ejecute estos comandos en el símbolo del sistema de Azure PowerShell en el equipo local:</span><span class="sxs-lookup"><span data-stu-id="1e348-113">To display the public IP address assigned to your Internet-facing load balancer, run these commands at the Azure PowerShell command prompt on your local computer:</span></span>
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "WebProxyPublicIP" -ResourceGroup $rgName).IPAddress
```

## <a name="determine-your-federation-service-fqdn-and-create-dns-records"></a><span data-ttu-id="1e348-114">Determinar el FQDN del servicio de Federación y crear registros DNS</span><span class="sxs-lookup"><span data-stu-id="1e348-114">Determine your federation service FQDN and create DNS records</span></span>

<span data-ttu-id="1e348-115">Debe determinar el nombre DNS para identificar el nombre del servicio de Federación en Internet.</span><span class="sxs-lookup"><span data-stu-id="1e348-115">You need to determine the DNS name to identify your federation service name on the Internet.</span></span> <span data-ttu-id="1e348-116">Azure AD Connect configurará Microsoft 365 con este nombre en la fase 5, que pasará a formar parte de la dirección URL que Microsoft 365 envía a los clientes que se conectan para obtener un token de seguridad.</span><span class="sxs-lookup"><span data-stu-id="1e348-116">Azure AD Connect will configure Microsoft 365 with this name in Phase 5, which will become part of the URL that Microsoft 365 sends to connecting clients to get a security token.</span></span> <span data-ttu-id="1e348-117">Un ejemplo es fs.contoso.com (FS significa servicio de Federación).</span><span class="sxs-lookup"><span data-stu-id="1e348-117">An example is fs.contoso.com (fs stands for federation service).</span></span>
  
<span data-ttu-id="1e348-118">Una vez que tenga el servicio de Federación FQDN, cree un registro de dominio DNS público a para el servicio de Federación FQDN que se resuelve en la dirección IP pública del equilibrador de carga de Azure accesible desde Internet.</span><span class="sxs-lookup"><span data-stu-id="1e348-118">Once you have your federation service FDQN, create a public DNS domain A record for the federation service FDQN that resolves to the public IP address of the Azure Internet-facing load balancer.</span></span>
  
|<span data-ttu-id="1e348-119">**Name**</span><span class="sxs-lookup"><span data-stu-id="1e348-119">**Name**</span></span>|<span data-ttu-id="1e348-120">**Type**</span><span class="sxs-lookup"><span data-stu-id="1e348-120">**Type**</span></span>|<span data-ttu-id="1e348-121">**TTL**</span><span class="sxs-lookup"><span data-stu-id="1e348-121">**TTL**</span></span>|<span data-ttu-id="1e348-122">**Valor**</span><span class="sxs-lookup"><span data-stu-id="1e348-122">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1e348-123">servicio de Federación FQDN</span><span class="sxs-lookup"><span data-stu-id="1e348-123">federation service FDQN</span></span>  <br/> |<span data-ttu-id="1e348-124">A</span><span class="sxs-lookup"><span data-stu-id="1e348-124">A</span></span>  <br/> |<span data-ttu-id="1e348-125">3600</span><span class="sxs-lookup"><span data-stu-id="1e348-125">3600</span></span>  <br/> |<span data-ttu-id="1e348-126">Dirección IP pública del equilibrador de carga de Azure accesible desde Internet (mostrado por el comando **write-host** en la sección anterior)</span><span class="sxs-lookup"><span data-stu-id="1e348-126">public IP address of the Azure Internet-facing load balancer (displayed by the **Write-Host** command in the previous section)</span></span> <br/> |
   
<span data-ttu-id="1e348-127">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="1e348-127">Here is an example:</span></span>
  
|<span data-ttu-id="1e348-128">**Name**</span><span class="sxs-lookup"><span data-stu-id="1e348-128">**Name**</span></span>|<span data-ttu-id="1e348-129">**Type**</span><span class="sxs-lookup"><span data-stu-id="1e348-129">**Type**</span></span>|<span data-ttu-id="1e348-130">**TTL**</span><span class="sxs-lookup"><span data-stu-id="1e348-130">**TTL**</span></span>|<span data-ttu-id="1e348-131">**Valor**</span><span class="sxs-lookup"><span data-stu-id="1e348-131">**Value**</span></span>|
|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1e348-132">fs.contoso.com</span><span class="sxs-lookup"><span data-stu-id="1e348-132">fs.contoso.com</span></span>  <br/> |<span data-ttu-id="1e348-133">A</span><span class="sxs-lookup"><span data-stu-id="1e348-133">A</span></span>  <br/> |<span data-ttu-id="1e348-134">3600</span><span class="sxs-lookup"><span data-stu-id="1e348-134">3600</span></span>  <br/> |<span data-ttu-id="1e348-135">131.107.249.117</span><span class="sxs-lookup"><span data-stu-id="1e348-135">131.107.249.117</span></span>  <br/> |
   
<span data-ttu-id="1e348-136">A continuación, agregue un registro de dirección DNS al espacio de nombres DNS privado de su organización que resuelva el FQDN del servicio de Federación en la dirección IP privada asignada al equilibrador de carga interno para los servidores AD FS (tabla I, elemento 4, columna valor).</span><span class="sxs-lookup"><span data-stu-id="1e348-136">Next, add a DNS address record to your organization's private DNS namespace that resolves your federation service FQDN to the private IP address assigned to the internal load balancer for the AD FS servers (Table I, item 4, Value column).</span></span>
  
## <a name="create-the-web-application-proxy-server-virtual-machines-in-azure"></a><span data-ttu-id="1e348-137">Crear las máquinas virtuales del servidor de proxy de aplicación web en Azure</span><span class="sxs-lookup"><span data-stu-id="1e348-137">Create the web application proxy server virtual machines in Azure</span></span>

<span data-ttu-id="1e348-138">Use el siguiente bloque de comandos de Azure PowerShell para crear las máquinas virtuales para los dos servidores proxy de aplicación Web.</span><span class="sxs-lookup"><span data-stu-id="1e348-138">Use the following block of Azure PowerShell commands to create the virtual machines for the two web application proxy servers.</span></span> 
  
<span data-ttu-id="1e348-139">Tenga en cuenta que los siguientes conjuntos de comandos de Azure PowerShell usan valores de las tablas siguientes:</span><span class="sxs-lookup"><span data-stu-id="1e348-139">Note that the following Azure PowerShell command sets use values from the following tables:</span></span>
  
- <span data-ttu-id="1e348-140">Tabla N, para las máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="1e348-140">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="1e348-141">Tabla R, para los grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="1e348-141">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="1e348-142">Tabla V, para la configuración de la red virtual</span><span class="sxs-lookup"><span data-stu-id="1e348-142">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="1e348-143">Tabla S, para las subredes</span><span class="sxs-lookup"><span data-stu-id="1e348-143">Table S, for your subnets</span></span>
    
- <span data-ttu-id="1e348-144">Tabla I, para las direcciones IP estáticas</span><span class="sxs-lookup"><span data-stu-id="1e348-144">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="1e348-145">Tabla A, para los conjuntos de disponibilidad</span><span class="sxs-lookup"><span data-stu-id="1e348-145">Table A, for your availability sets</span></span>
    
<span data-ttu-id="1e348-146">Recuerde que ha definido la tabla M en la [fase 2: configurar los controladores de dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) y las tablas R, V, S, I y A en la [fase 1: configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="1e348-146">Recall that you defined Table M in [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
<span data-ttu-id="1e348-147">Después de especificar todos los valores correctos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1e348-147">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
```powershell
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
> <span data-ttu-id="1e348-148">Como estas máquinas virtuales son para una aplicación de intranet, no se les asigna una dirección IP pública ni una etiqueta de nombre de dominio DNS, ni se exponen a Internet.</span><span class="sxs-lookup"><span data-stu-id="1e348-148">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span></span> <span data-ttu-id="1e348-149">Pero esto también quiere decir que no podrá conectarse a estas desde Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="1e348-149">However, this also means that you cannot connect to them from the Azure portal.</span></span> <span data-ttu-id="1e348-150">La opción **Conectar** no estará disponible al ver las propiedades de la máquina virtual.</span><span class="sxs-lookup"><span data-stu-id="1e348-150">The **Connect** option is unavailable when you view the properties of the virtual machine.</span></span> <span data-ttu-id="1e348-151">Use el accesorio conexión a escritorio remoto u otra herramienta de escritorio remoto para conectarse a la máquina virtual usando su dirección IP privada o el nombre DNS de la intranet y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="1e348-151">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="1e348-152">Esta es la configuración completada después de la finalización correcta de esta fase, con los nombres de equipo de marcadores de posición.</span><span class="sxs-lookup"><span data-stu-id="1e348-152">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="1e348-153">**Fase 4: el equilibrador de carga accesible desde Internet y los servidores proxy de aplicación web para la infraestructura de autenticación federada de alta disponibilidad en Azure**</span><span class="sxs-lookup"><span data-stu-id="1e348-153">**Phase 4: The Internet-facing load balancer and web application proxy servers for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 4 de la infraestructura de autenticación federada de Microsoft 365 de alta disponibilidad en Azure con los servidores proxy de aplicación Web](media/7e03183f-3b3b-4cbe-9028-89cc3f195a63.png)
  
## <a name="next-step"></a><span data-ttu-id="1e348-155">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="1e348-155">Next step</span></span>

<span data-ttu-id="1e348-156">Use [Phase 5: configure Federated Authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) para seguir configurando esta carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="1e348-156">Use [Phase 5: Configure federated authentication for Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1e348-157">Vea también</span><span class="sxs-lookup"><span data-stu-id="1e348-157">See Also</span></span>

[<span data-ttu-id="1e348-158">Implementar la autenticación federada de alta disponibilidad para Microsoft 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="1e348-158">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="1e348-159">Identidad federada para el entorno de prueba y desarrollo de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="1e348-159">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)
  
[<span data-ttu-id="1e348-160">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="1e348-160">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)

