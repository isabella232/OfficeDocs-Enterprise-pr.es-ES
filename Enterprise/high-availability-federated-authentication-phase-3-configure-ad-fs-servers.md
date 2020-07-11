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
description: 'Resumen: cree y configure los servidores de los servicios de Federación de Active Directory (AD FS) para la autenticación federada de alta disponibilidad para Microsoft 365 en Microsoft Azure.'
ms.openlocfilehash: e4fa1ac49d9c9a60567d587416347093ff0784c9
ms.sourcegitcommit: d8ca7017b25d5ddc2771e662e02b62ff2058383b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102518"
---
# <a name="high-availability-federated-authentication-phase-3-configure-ad-fs-servers"></a><span data-ttu-id="ca14d-103">Fase 3 de la autenticación federada de alta disponibilidad: Configurar servidores de AD FS</span><span class="sxs-lookup"><span data-stu-id="ca14d-103">High availability federated authentication Phase 3: Configure AD FS servers</span></span>

<span data-ttu-id="ca14d-104">En esta fase de implementación de alta disponibilidad para la autenticación federada de Microsoft 365 en los servicios de infraestructura de Azure, se crea un equilibrador de carga interno y dos servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="ca14d-104">In this phase of deploying high availability for Microsoft 365 federated authentication in Azure infrastructure services, you create an internal load balancer and two AD FS servers.</span></span>
  
<span data-ttu-id="ca14d-105">Debe completar esta fase antes de continuar con la [fase 4: configurar servidores proxy de aplicación web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span><span class="sxs-lookup"><span data-stu-id="ca14d-105">You must complete this phase before moving on to [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md).</span></span> <span data-ttu-id="ca14d-106">Consulte [implementar la autenticación federada de alta disponibilidad para Microsoft 365 en Azure en](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) todas las fases.</span><span class="sxs-lookup"><span data-stu-id="ca14d-106">See [Deploy high availability federated authentication for Microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-ad-fs-server-virtual-machines-in-azure"></a><span data-ttu-id="ca14d-107">Crear las máquinas virtuales del servidor de AD FS en Azure</span><span class="sxs-lookup"><span data-stu-id="ca14d-107">Create the AD FS server virtual machines in Azure</span></span>

<span data-ttu-id="ca14d-108">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers.</span><span class="sxs-lookup"><span data-stu-id="ca14d-108">Use the following block of PowerShell commands to create the virtual machines for the two AD FS servers.</span></span> <span data-ttu-id="ca14d-109">This PowerShell command set uses values from the following tables:</span><span class="sxs-lookup"><span data-stu-id="ca14d-109">This PowerShell command set uses values from the following tables:</span></span>
  
- <span data-ttu-id="ca14d-110">Tabla N, para las máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="ca14d-110">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="ca14d-111">Tabla R, para los grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="ca14d-111">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="ca14d-112">Tabla V, para la configuración de la red virtual</span><span class="sxs-lookup"><span data-stu-id="ca14d-112">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="ca14d-113">Tabla S, para las subredes</span><span class="sxs-lookup"><span data-stu-id="ca14d-113">Table S, for your subnets</span></span>
    
- <span data-ttu-id="ca14d-114">Tabla I, para las direcciones IP estáticas</span><span class="sxs-lookup"><span data-stu-id="ca14d-114">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="ca14d-115">Tabla A, para los conjuntos de disponibilidad</span><span class="sxs-lookup"><span data-stu-id="ca14d-115">Table A, for your availability sets</span></span>
    
<span data-ttu-id="ca14d-116">Recuerde que ha definido la tabla M en la [fase 2: configurar los controladores de dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) y las tablas R, V, S, I y A en la [fase 1: configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="ca14d-116">Recall that you defined Table M in [Phase 2: Configure domain controllers](high-availability-federated-authentication-phase-2-configure-domain-controllers.md) and Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="ca14d-117">Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca14d-117">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="ca14d-118">Consulte Introducción [a Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span><span class="sxs-lookup"><span data-stu-id="ca14d-118">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="ca14d-119">Primero, cree un equilibrador de carga interno de Azure para los dos servidores de AD FS.</span><span class="sxs-lookup"><span data-stu-id="ca14d-119">First, you create an Azure internal load balancer for the two AD FS servers.</span></span> <span data-ttu-id="ca14d-120">Especifique los valores de las variables, quitando los \< and > caracteres.</span><span class="sxs-lookup"><span data-stu-id="ca14d-120">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="ca14d-121">Después de especificar todos los valores correctos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ca14d-121">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
> [!TIP]
> <span data-ttu-id="ca14d-122">Para generar bloques de comandos de PowerShell listos para ejecutar en función de la configuración personalizada, use este [libro de configuración de Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span><span class="sxs-lookup"><span data-stu-id="ca14d-122">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/O365FedAuthInAzure_Config.xlsx).</span></span> 

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

<span data-ttu-id="ca14d-123">Después, cree las máquinas virtuales del servidor de AD FS.</span><span class="sxs-lookup"><span data-stu-id="ca14d-123">Next, create the AD FS server virtual machines.</span></span>
  
<span data-ttu-id="ca14d-124">Después de especificar todos los valores correctos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ca14d-124">When you have supplied all the proper values, run the resulting block at the Azure PowerShell command prompt or in the PowerShell ISE.</span></span>
  
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
> <span data-ttu-id="ca14d-125">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span><span class="sxs-lookup"><span data-stu-id="ca14d-125">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet.</span></span> <span data-ttu-id="ca14d-126">However, this also means that you cannot connect to them from the Azure portal.</span><span class="sxs-lookup"><span data-stu-id="ca14d-126">However, this also means that you cannot connect to them from the Azure portal.</span></span> <span data-ttu-id="ca14d-127">The **Connect** option is unavailable when you view the properties of the virtual machine.</span><span class="sxs-lookup"><span data-stu-id="ca14d-127">The **Connect** option is unavailable when you view the properties of the virtual machine.</span></span> <span data-ttu-id="ca14d-128">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span><span class="sxs-lookup"><span data-stu-id="ca14d-128">Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
<span data-ttu-id="ca14d-129">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection.</span><span class="sxs-lookup"><span data-stu-id="ca14d-129">For each virtual machine, use the remote desktop client of your choice and create a remote desktop connection.</span></span> <span data-ttu-id="ca14d-130">Use its intranet DNS or computer name and the credentials of the local administrator account.</span><span class="sxs-lookup"><span data-stu-id="ca14d-130">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="ca14d-131">Para cada máquina virtual, únase al dominio de servicios de dominio de Active Directory (AD DS) adecuado con estos comandos en el símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca14d-131">For each virtual machine, join them to the appropriate Active Directory Domain Services (AD DS) domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="ca14d-132">Esta es la configuración completada después de la finalización correcta de esta fase, con los nombres de equipo de marcadores de posición.</span><span class="sxs-lookup"><span data-stu-id="ca14d-132">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="ca14d-133">**Fase 3: Equilibrador de carga interno y servidores de AD FS para la infraestructura de autenticación federada de alta disponibilidad en Azure**</span><span class="sxs-lookup"><span data-stu-id="ca14d-133">**Phase 3: The AD FS servers and internal load balancer for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 3 de la infraestructura de autenticación federada de Microsoft 365 de alta disponibilidad en Azure con los servidores de AD FS](media/f39b2d2f-8a5b-44da-b763-e1f943fcdbc4.png)
  
## <a name="next-step"></a><span data-ttu-id="ca14d-135">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="ca14d-135">Next step</span></span>

<span data-ttu-id="ca14d-136">Use [Phase 4: configure Web Application proxys](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) para seguir configurando esta carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="ca14d-136">Use [Phase 4: Configure web application proxies](high-availability-federated-authentication-phase-4-configure-web-application-pro.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ca14d-137">Vea también</span><span class="sxs-lookup"><span data-stu-id="ca14d-137">See Also</span></span>

[<span data-ttu-id="ca14d-138">Implementar la autenticación federada de alta disponibilidad para Microsoft 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="ca14d-138">Deploy high availability federated authentication for Microsoft 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="ca14d-139">Identidad federada para el entorno de prueba y desarrollo de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ca14d-139">Federated identity for your Microsoft 365 dev/test environment</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment)


