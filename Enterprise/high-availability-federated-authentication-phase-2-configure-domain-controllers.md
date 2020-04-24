---
title: Fase 2 de la autenticación federada de alta disponibilidad configurar controladores de dominio
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
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Resumen: Configure los controladores de dominio y el servidor de sincronización de directorios para la autenticación federada de alta disponibilidad para Office 365 en Microsoft Azure.'
ms.openlocfilehash: 80b413f8a6d415378e384b1625fc756f96dd00db
ms.sourcegitcommit: a578baeb0d8b85941c13afa268447d2592f89fae
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2020
ms.locfileid: "43793823"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="40e91-103">Fase 2 de la autenticación federada de alta disponibilidad: Configurar controladores de dominio</span><span class="sxs-lookup"><span data-stu-id="40e91-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

<span data-ttu-id="40e91-104">En esta fase de implementación de alta disponibilidad para la autenticación federada de Office 365 en los servicios de infraestructura de Azure, se configuran dos controladores de dominio y el servidor de sincronización de directorios en la red virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="40e91-104">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the directory synchronization server in the Azure virtual network.</span></span> <span data-ttu-id="40e91-105">Después, las solicitudes web de los clientes para la autenticación se pueden autenticar en la red virtual de Azure, en lugar de enviar ese tráfico de autenticación por la conexión VPN de sitio a sitio a la red local.</span><span class="sxs-lookup"><span data-stu-id="40e91-105">Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="40e91-106">Los servicios de Federación de Active Directory (AD FS) no pueden usar los servicios de dominio de Active Directory de Azure como sustituto de los controladores de dominio de servicios de dominio de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="40e91-106">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Active Directory Domain Services domain controllers.</span></span> 
  
<span data-ttu-id="40e91-107">Debe completar esta fase antes de continuar con la [fase 3: configurar servidores de AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span><span class="sxs-lookup"><span data-stu-id="40e91-107">You must complete this phase before moving on to [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="40e91-108">Consulte todas las fases en [Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="40e91-108">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="40e91-109">Crear las máquinas virtuales del controlador de dominio en Azure</span><span class="sxs-lookup"><span data-stu-id="40e91-109">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="40e91-110">Primero, necesita rellenar la columna de **Nombre de la máquina virtual** de la Tabla M y modificar los tamaños de las máquinas virtuales según sea necesario en la columna **Tamaño mínimo**.</span><span class="sxs-lookup"><span data-stu-id="40e91-110">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="40e91-111">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="40e91-111">**Item**</span></span>|<span data-ttu-id="40e91-112">**Nombre de máquina virtual**</span><span class="sxs-lookup"><span data-stu-id="40e91-112">**Virtual machine name**</span></span>|<span data-ttu-id="40e91-113">**Imagen de la galería**</span><span class="sxs-lookup"><span data-stu-id="40e91-113">**Gallery image**</span></span>|<span data-ttu-id="40e91-114">**Tipo de almacenamiento**</span><span class="sxs-lookup"><span data-stu-id="40e91-114">**Storage type**</span></span>|<span data-ttu-id="40e91-115">**Tamaño mínimo**</span><span class="sxs-lookup"><span data-stu-id="40e91-115">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="40e91-116">1.</span><span class="sxs-lookup"><span data-stu-id="40e91-116">1.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png) <span data-ttu-id="40e91-118"> (primer controlador de dominio, ejemplo DC1)</span><span class="sxs-lookup"><span data-stu-id="40e91-118">(first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="40e91-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="40e91-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="40e91-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="40e91-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="40e91-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="40e91-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="40e91-122">2.</span><span class="sxs-lookup"><span data-stu-id="40e91-122">2.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png) <span data-ttu-id="40e91-124"> (segundo controlador de dominio, ejemplo DC2)</span><span class="sxs-lookup"><span data-stu-id="40e91-124">(second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="40e91-125">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="40e91-125">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="40e91-126">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="40e91-126">Standard_LRS</span></span>  <br/> |<span data-ttu-id="40e91-127">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="40e91-127">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="40e91-128">3.</span><span class="sxs-lookup"><span data-stu-id="40e91-128">3.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png) <span data-ttu-id="40e91-130">(servidor de sincronización de directorios, ejemplo DS1)</span><span class="sxs-lookup"><span data-stu-id="40e91-130">(directory synchronization server, example DS1)</span></span>  <br/> |<span data-ttu-id="40e91-131">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="40e91-131">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="40e91-132">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="40e91-132">Standard_LRS</span></span>  <br/> |<span data-ttu-id="40e91-133">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="40e91-133">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="40e91-134">4.</span><span class="sxs-lookup"><span data-stu-id="40e91-134">4.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png) <span data-ttu-id="40e91-136">(primer servidor de AD FS, ejemplo ADFS1)</span><span class="sxs-lookup"><span data-stu-id="40e91-136">(first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="40e91-137">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="40e91-137">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="40e91-138">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="40e91-138">Standard_LRS</span></span>  <br/> |<span data-ttu-id="40e91-139">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="40e91-139">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="40e91-140">5.</span><span class="sxs-lookup"><span data-stu-id="40e91-140">5.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png) <span data-ttu-id="40e91-142">(segundo servidor de AD FS, ejemplo ADFS2)</span><span class="sxs-lookup"><span data-stu-id="40e91-142">(second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="40e91-143">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="40e91-143">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="40e91-144">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="40e91-144">Standard_LRS</span></span>  <br/> |<span data-ttu-id="40e91-145">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="40e91-145">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="40e91-146">6.</span><span class="sxs-lookup"><span data-stu-id="40e91-146">6.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png) <span data-ttu-id="40e91-148">(primer servidor proxy de aplicación Web, ejemplo WEB1)</span><span class="sxs-lookup"><span data-stu-id="40e91-148">(first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="40e91-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="40e91-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="40e91-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="40e91-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="40e91-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="40e91-151">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="40e91-152">7.</span><span class="sxs-lookup"><span data-stu-id="40e91-152">7.</span></span>  <br/> |![línea](./media/Common-Images/TableLine.png) <span data-ttu-id="40e91-154">(segundo servidor de proxy de aplicación Web, de ejemplo, WEB2)</span><span class="sxs-lookup"><span data-stu-id="40e91-154">(second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="40e91-155">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="40e91-155">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="40e91-156">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="40e91-156">Standard_LRS</span></span>  <br/> |<span data-ttu-id="40e91-157">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="40e91-157">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="40e91-158">**Tabla M: máquinas virtuales para la autenticación federada de alta disponibilidad para Office 365 en Azure**</span><span class="sxs-lookup"><span data-stu-id="40e91-158">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="40e91-159">Para obtener la lista completa de tamaños de máquinas virtuales, vea [Tamaños de máquinas virtuales](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="40e91-159">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="40e91-160">El siguiente bloque de comandos de Azure PowerShell crea las máquinas virtuales de los dos controladores de dominio.</span><span class="sxs-lookup"><span data-stu-id="40e91-160">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="40e91-161">Especifique los valores de las variables, quitando \< y > caracteres.</span><span class="sxs-lookup"><span data-stu-id="40e91-161">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="40e91-162">Tenga en cuenta que este bloque de comandos de Azure PowerShell usa valores de las siguientes tablas:</span><span class="sxs-lookup"><span data-stu-id="40e91-162">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="40e91-163">Tabla N, para las máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="40e91-163">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="40e91-164">Tabla R, para los grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="40e91-164">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="40e91-165">Tabla V, para la configuración de la red virtual</span><span class="sxs-lookup"><span data-stu-id="40e91-165">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="40e91-166">Tabla S, para las subredes</span><span class="sxs-lookup"><span data-stu-id="40e91-166">Table S, for your subnets</span></span>
    
- <span data-ttu-id="40e91-167">Tabla I, para las direcciones IP estáticas</span><span class="sxs-lookup"><span data-stu-id="40e91-167">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="40e91-168">Tabla A, para los conjuntos de disponibilidad</span><span class="sxs-lookup"><span data-stu-id="40e91-168">Table A, for your availability sets</span></span>
    
<span data-ttu-id="40e91-169">Recuerde que definió las tablas R, V, S, I y A en la [fase 1: configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="40e91-169">Recall that you defined Tables R, V, S, I, and A in [Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="40e91-170">Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40e91-170">The following command sets use the latest version of Azure PowerShell.</span></span> <span data-ttu-id="40e91-171">Consulte Introducción [a Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span><span class="sxs-lookup"><span data-stu-id="40e91-171">See [Get started with Azure PowerShell](https://docs.microsoft.com/powershell/azure/get-started-azureps).</span></span> 
  
<span data-ttu-id="40e91-172">Después de especificar todos los valores correctos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en el Entorno de scripting integrado (ISE) de PowerShell en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="40e91-172">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="40e91-173">Para generar bloques de comandos de PowerShell listos para ejecutar en función de la configuración personalizada, use este [libro de configuración de Microsoft Excel](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span><span class="sxs-lookup"><span data-stu-id="40e91-173">To generate ready-to-run PowerShell command blocks based on your custom settings, use this [Microsoft Excel configuration workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/deploy-high-availability-federated-authentication-for-office-365-in-azure/O365FedAuthInAzure_Config.xlsx).</span></span> 

```powershell
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Active Directory Domain Services (AD DS) data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for AD DS data in GB>

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the directory synchronization server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the directory synchronization server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="40e91-p105">Como estas máquinas virtuales son para una aplicación de intranet, no se les asigna una dirección IP pública ni una etiqueta de nombre de dominio DNS, ni se exponen a Internet. Pero esto también quiere decir que no podrá conectarse a estas desde Azure Portal. La opción **Conectar** no estará disponible al ver las propiedades de la máquina virtual. Use la herramienta Conexión a Escritorio remoto u otra herramienta de Escritorio remoto para conectarse a la máquina virtual con su dirección IP privada o con el nombre DNS de la intranet.</span><span class="sxs-lookup"><span data-stu-id="40e91-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="40e91-178">Configurar el primer controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="40e91-178">Configure the first domain controller</span></span>

<span data-ttu-id="40e91-p106">Use el cliente de Escritorio remoto que prefiera y cree una conexión a Escritorio remoto a la máquina virtual del primer controlador de dominio. Use el nombre DNS de la intranet o el nombre de equipo y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="40e91-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="40e91-181">A continuación, agregue el disco de datos adicional al primer controlador de dominio con este comando desde un símbolo del sistema de Windows PowerShell **en la máquina virtual del primer controlador de dominio**:</span><span class="sxs-lookup"><span data-stu-id="40e91-181">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="40e91-182">El paso siguiente es probar la conectividad del primer controlador de dominio a las ubicaciones en la red de la organización con el comando **ping** para hacer ping a los nombres y direcciones IP de los recursos en la red de la organización.</span><span class="sxs-lookup"><span data-stu-id="40e91-182">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="40e91-p107">Este procedimiento garantiza que la resolución de nombres DNS funciona correctamente (que la máquina virtual está configurada correctamente con los servidores DNS locales) y que se pueden enviar y recibir paquetes de la red virtual entre locales. Si esta prueba básica produce errores, póngase en contacto con el departamento de TI para solucionar los problemas de resolución de nombres DNS y de entrega de paquetes.</span><span class="sxs-lookup"><span data-stu-id="40e91-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="40e91-185">Después, desde el símbolo del sistema de Windows PowerShell en el primer controlador de dominio, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="40e91-185">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="40e91-p108">Se le pedirá que especifique las credenciales de una cuenta de administrador de dominio. Se reiniciará el equipo.</span><span class="sxs-lookup"><span data-stu-id="40e91-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="40e91-188">Configurar el segundo controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="40e91-188">Configure the second domain controller</span></span>

<span data-ttu-id="40e91-p109">Use el cliente de Escritorio remoto que prefiera y cree una conexión a Escritorio remoto a la máquina virtual del segundo controlador de dominio. Use el nombre DNS de la intranet o el nombre de equipo y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="40e91-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="40e91-191">A continuación, necesita agregar el disco de datos adicional al segundo controlador de dominio con este comando desde un símbolo del sistema de Windows PowerShell **en la máquina virtual del segundo controlador de dominio**:</span><span class="sxs-lookup"><span data-stu-id="40e91-191">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="40e91-192">Después, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="40e91-192">Next, run the following commands:</span></span>
  
```powershell
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="40e91-p110">Se le pedirá que especifique las credenciales de una cuenta de administrador de dominio. Se reiniciará el equipo.</span><span class="sxs-lookup"><span data-stu-id="40e91-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="40e91-195">Después, tendrá que actualizar los servidores DNS de la red virtual para que Azure asigne a las máquinas virtuales las direcciones IP de los dos nuevos controladores de dominio para que las usen como sus servidores DNS.</span><span class="sxs-lookup"><span data-stu-id="40e91-195">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="40e91-196">Rellene las variables y, a continuación, ejecute estos comandos desde un símbolo del sistema de Windows PowerShell en el equipo local:</span><span class="sxs-lookup"><span data-stu-id="40e91-196">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```powershell
$rgName="<Table R - Item 4 - Resource group name column>"
$adrgName="<Table R - Item 1 - Resource group name column>"
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$onpremDNSIP1="<Table D - Item 1 - DNS server IP address column>"
$onpremDNSIP2="<Table D - Item 2 - DNS server IP address column>"
$staticIP1="<Table I - Item 1 - Value column>"
$staticIP2="<Table I - Item 2 - Value column>"
$firstDCName="<Table M - Item 1 - Virtual machine name column>"
$secondDCName="<Table M - Item 2 - Virtual machine name column>"

$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="40e91-p112">Tenga en cuenta que reiniciamos los dos controladores de dominio para que no estén configurados con los servidores DNS locales como los servidores DNS. Como ambos son servidores DNS, se configuraron automáticamente con los servidores DNS locales como reenviadores DNS cuando se promovieron a controladores de dominio.</span><span class="sxs-lookup"><span data-stu-id="40e91-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="40e91-p113">Después, es necesario crear un sitio de replicación de Active Directory para garantizar que los servidores de la red virtual de Azure usen los controladores de dominio locales. Conéctese al controlador de dominio con una cuenta de administrador de dominio y ejecute los comandos siguientes desde un símbolo del sistema de Windows PowerShell con permisos de administrador:</span><span class="sxs-lookup"><span data-stu-id="40e91-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```powershell
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-directory-synchronization-server"></a><span data-ttu-id="40e91-201">Configurar el servidor de sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="40e91-201">Configure the directory synchronization server</span></span>

<span data-ttu-id="40e91-202">Use el cliente de escritorio remoto que prefiera y cree una conexión a escritorio remoto a la máquina virtual del servidor de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="40e91-202">Use the remote desktop client of your choice and create a remote desktop connection to the directory synchronization server virtual machine.</span></span> <span data-ttu-id="40e91-203">Use el nombre DNS de la intranet o el nombre de equipo y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="40e91-203">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="40e91-204">Después, únase al dominio de AD DS adecuado con estos comandos en el símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="40e91-204">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```powershell
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="40e91-205">Esta es la configuración completada después de la finalización correcta de esta fase, con los nombres de equipo de marcadores de posición.</span><span class="sxs-lookup"><span data-stu-id="40e91-205">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="40e91-206">**Fase 2: los controladores de dominio y el servidor de sincronización de directorios para la infraestructura de autenticación federada de alta disponibilidad en Azure**</span><span class="sxs-lookup"><span data-stu-id="40e91-206">**Phase 2: The domain controllers and directory synchronization server for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 2 de la infraestructura de autenticación federada de Office 365 de alta disponibilidad en Azure con controladores de dominio](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="40e91-208">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="40e91-208">Next step</span></span>

<span data-ttu-id="40e91-209">Use [Phase 3: Configure los servidores de AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) para seguir configurando esta carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="40e91-209">Use [Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="40e91-210">Vea también</span><span class="sxs-lookup"><span data-stu-id="40e91-210">See Also</span></span>

[<span data-ttu-id="40e91-211">Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="40e91-211">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="40e91-212">Identidad federada para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="40e91-212">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="40e91-213">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="40e91-213">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.yml)


