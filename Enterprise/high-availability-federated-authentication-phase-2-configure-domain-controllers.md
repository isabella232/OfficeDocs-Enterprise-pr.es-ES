---
title: Fase 2 de la autenticación federada de alta disponibilidad configurar controladores de dominio
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Resumen: Configure los controladores de dominio y el servidor de DirSync para la autenticación federada de alta disponibilidad para Office 365 en Microsoft Azure.'
ms.openlocfilehash: bda22a1df0165724f660019e28a9f088280fea4f
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741256"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="1994b-103">Fase 2 de la autenticación federada de alta disponibilidad: Configurar controladores de dominio</span><span class="sxs-lookup"><span data-stu-id="1994b-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="1994b-104">**Resumen:** Configure los controladores de dominio y el servidor de DirSync para la autenticación federada de alta disponibilidad para Office 365 en Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="1994b-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="1994b-p101">En esta fase de la implementación de alta disponibilidad para la autenticación federada de Office 365 en servicios de infraestructura de Azure, se configuran dos controladores de dominio y el servidor de DirSync en la red virtual de Azure. Después, las solicitudes web de los clientes para la autenticación se pueden autenticar en la red virtual de Azure, en lugar de enviar ese tráfico de autenticación por la conexión VPN de sitio a sitio a la red local.</span><span class="sxs-lookup"><span data-stu-id="1994b-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1994b-107">Los servicios de Federación de Active Directory (AD FS) no pueden usar los servicios de dominio de Active Directory de Azure como sustituto de los controladores de dominio de servicios de dominio de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="1994b-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Active Directory Domain Services domain controllers.</span></span> 
  
<span data-ttu-id="1994b-108">Debe completar esta fase para poder pasar a la [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span><span class="sxs-lookup"><span data-stu-id="1994b-108">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md).</span></span> <span data-ttu-id="1994b-109">Consulte todas las fases en [Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md).</span><span class="sxs-lookup"><span data-stu-id="1994b-109">See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="1994b-110">Crear las máquinas virtuales del controlador de dominio en Azure</span><span class="sxs-lookup"><span data-stu-id="1994b-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="1994b-111">Primero, necesita rellenar la columna de **Nombre de la máquina virtual** de la Tabla M y modificar los tamaños de las máquinas virtuales según sea necesario en la columna **Tamaño mínimo**.</span><span class="sxs-lookup"><span data-stu-id="1994b-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|**<span data-ttu-id="1994b-112">Item</span><span class="sxs-lookup"><span data-stu-id="1994b-112">Item</span></span>**|**<span data-ttu-id="1994b-113">Nombre de máquina virtual</span><span class="sxs-lookup"><span data-stu-id="1994b-113">Virtual machine name</span></span>**|**<span data-ttu-id="1994b-114">Imagen de la galería</span><span class="sxs-lookup"><span data-stu-id="1994b-114">Gallery image</span></span>**|**<span data-ttu-id="1994b-115">Tipo de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="1994b-115">Storage type</span></span>**|**<span data-ttu-id="1994b-116">Tamaño mínimo</span><span class="sxs-lookup"><span data-stu-id="1994b-116">Minimum size</span></span>**|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="1994b-117">1.</span><span class="sxs-lookup"><span data-stu-id="1994b-117">1.</span></span>  <br/> |![](./media/Common-Images/TableLine.png) <span data-ttu-id="1994b-118"> (primer controlador de dominio, ejemplo DC1)</span><span class="sxs-lookup"><span data-stu-id="1994b-118">(first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="1994b-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1994b-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1994b-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="1994b-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="1994b-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="1994b-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="1994b-122">2.</span><span class="sxs-lookup"><span data-stu-id="1994b-122">2.</span></span>  <br/> |![](./media/Common-Images/TableLine.png) <span data-ttu-id="1994b-123"> (segundo controlador de dominio, ejemplo DC2)</span><span class="sxs-lookup"><span data-stu-id="1994b-123">(second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="1994b-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1994b-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1994b-125">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="1994b-125">Standard_LRS</span></span>  <br/> |<span data-ttu-id="1994b-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="1994b-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="1994b-127">3.</span><span class="sxs-lookup"><span data-stu-id="1994b-127">3.</span></span>  <br/> |![](./media/Common-Images/TableLine.png) <span data-ttu-id="1994b-128">(Servidor de sincronización de directorios, ejemplo DS1)</span><span class="sxs-lookup"><span data-stu-id="1994b-128">(DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="1994b-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1994b-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1994b-130">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="1994b-130">Standard_LRS</span></span>  <br/> |<span data-ttu-id="1994b-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="1994b-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="1994b-132">4.</span><span class="sxs-lookup"><span data-stu-id="1994b-132">4.</span></span>  <br/> |![](./media/Common-Images/TableLine.png) <span data-ttu-id="1994b-133">(primer servidor de AD FS, ejemplo ADFS1)</span><span class="sxs-lookup"><span data-stu-id="1994b-133">(first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="1994b-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1994b-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1994b-135">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="1994b-135">Standard_LRS</span></span>  <br/> |<span data-ttu-id="1994b-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="1994b-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="1994b-137">5.</span><span class="sxs-lookup"><span data-stu-id="1994b-137">5.</span></span>  <br/> |![](./media/Common-Images/TableLine.png) <span data-ttu-id="1994b-138">(segundo servidor de AD FS, ejemplo ADFS2)</span><span class="sxs-lookup"><span data-stu-id="1994b-138">(second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="1994b-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1994b-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1994b-140">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="1994b-140">Standard_LRS</span></span>  <br/> |<span data-ttu-id="1994b-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="1994b-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="1994b-142">6.</span><span class="sxs-lookup"><span data-stu-id="1994b-142">6.</span></span>  <br/> |![](./media/Common-Images/TableLine.png) <span data-ttu-id="1994b-143">(primer servidor proxy de aplicación Web, ejemplo WEB1)</span><span class="sxs-lookup"><span data-stu-id="1994b-143">(first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="1994b-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1994b-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1994b-145">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="1994b-145">Standard_LRS</span></span>  <br/> |<span data-ttu-id="1994b-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="1994b-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="1994b-147">7.</span><span class="sxs-lookup"><span data-stu-id="1994b-147">7.</span></span>  <br/> |![](./media/Common-Images/TableLine.png) <span data-ttu-id="1994b-148">(segundo servidor de proxy de aplicación Web, de ejemplo, WEB2)</span><span class="sxs-lookup"><span data-stu-id="1994b-148">(second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="1994b-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="1994b-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="1994b-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="1994b-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="1994b-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="1994b-151">Standard_D2</span></span>  <br/> |
   
 **<span data-ttu-id="1994b-152">Tabla M: máquinas virtuales para la autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="1994b-152">Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure</span></span>**
  
<span data-ttu-id="1994b-153">Para obtener la lista completa de tamaños de máquinas virtuales, vea [Tamaños de máquinas virtuales](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="1994b-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="1994b-154">El siguiente bloque de comandos de Azure PowerShell crea las máquinas virtuales de los dos controladores de dominio.</span><span class="sxs-lookup"><span data-stu-id="1994b-154">The following Azure PowerShell command block creates the virtual machines for the two domain controllers.</span></span> <span data-ttu-id="1994b-155">Especifique los valores de las variables, quitando \< los caracteres y >.</span><span class="sxs-lookup"><span data-stu-id="1994b-155">Specify the values for the variables, removing the \< and > characters.</span></span> <span data-ttu-id="1994b-156">Tenga en cuenta que este bloque de comandos de Azure PowerShell usa valores de las siguientes tablas:</span><span class="sxs-lookup"><span data-stu-id="1994b-156">Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="1994b-157">Tabla N, para las máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="1994b-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="1994b-158">Tabla R, para los grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="1994b-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="1994b-159">Tabla V, para la configuración de la red virtual</span><span class="sxs-lookup"><span data-stu-id="1994b-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="1994b-160">Tabla S, para las subredes</span><span class="sxs-lookup"><span data-stu-id="1994b-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="1994b-161">Tabla I, para las direcciones IP estáticas</span><span class="sxs-lookup"><span data-stu-id="1994b-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="1994b-162">Tabla A, para los conjuntos de disponibilidad</span><span class="sxs-lookup"><span data-stu-id="1994b-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="1994b-163">Recuerde que definió las tablas R, V, S, I y A en la [fase 1 de la autenticación federada de alta disponibilidad: configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="1994b-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="1994b-p104">Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell. Visite [Get started with Azure PowerShell cmdlets (Introducción a los cmdlets de Azure)](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="1994b-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="1994b-166">Después de especificar todos los valores correctos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en el Entorno de scripting integrado (ISE) de PowerShell en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="1994b-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
<!--
> [!TIP]
> For a text file that has all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
-->
  
```
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

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="1994b-p105">Como estas máquinas virtuales son para una aplicación de intranet, no se les asigna una dirección IP pública ni una etiqueta de nombre de dominio DNS, ni se exponen a Internet. Pero esto también quiere decir que no podrá conectarse a estas desde Azure Portal. La opción **Conectar** no estará disponible al ver las propiedades de la máquina virtual. Use la herramienta Conexión a Escritorio remoto u otra herramienta de Escritorio remoto para conectarse a la máquina virtual con su dirección IP privada o con el nombre DNS de la intranet.</span><span class="sxs-lookup"><span data-stu-id="1994b-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="1994b-171">Configurar el primer controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="1994b-171">Configure the first domain controller</span></span>

<span data-ttu-id="1994b-p106">Use el cliente de Escritorio remoto que prefiera y cree una conexión a Escritorio remoto a la máquina virtual del primer controlador de dominio. Use el nombre DNS de la intranet o el nombre de equipo y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="1994b-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="1994b-174">A continuación, agregue el disco de datos adicional al primer controlador de dominio con este comando desde un símbolo del sistema de Windows PowerShell **en la máquina virtual del primer controlador de dominio**:</span><span class="sxs-lookup"><span data-stu-id="1994b-174">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="1994b-175">El paso siguiente es probar la conectividad del primer controlador de dominio a las ubicaciones en la red de la organización con el comando **ping** para hacer ping a los nombres y direcciones IP de los recursos en la red de la organización.</span><span class="sxs-lookup"><span data-stu-id="1994b-175">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="1994b-p107">Este procedimiento garantiza que la resolución de nombres DNS funciona correctamente (que la máquina virtual está configurada correctamente con los servidores DNS locales) y que se pueden enviar y recibir paquetes de la red virtual entre locales. Si esta prueba básica produce errores, póngase en contacto con el departamento de TI para solucionar los problemas de resolución de nombres DNS y de entrega de paquetes.</span><span class="sxs-lookup"><span data-stu-id="1994b-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="1994b-178">Después, desde el símbolo del sistema de Windows PowerShell en el primer controlador de dominio, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="1994b-178">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="1994b-p108">Se le pedirá que especifique las credenciales de una cuenta de administrador de dominio. Se reiniciará el equipo.</span><span class="sxs-lookup"><span data-stu-id="1994b-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="1994b-181">Configurar el segundo controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="1994b-181">Configure the second domain controller</span></span>

<span data-ttu-id="1994b-p109">Use el cliente de Escritorio remoto que prefiera y cree una conexión a Escritorio remoto a la máquina virtual del segundo controlador de dominio. Use el nombre DNS de la intranet o el nombre de equipo y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="1994b-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="1994b-184">A continuación, necesita agregar el disco de datos adicional al segundo controlador de dominio con este comando desde un símbolo del sistema de Windows PowerShell **en la máquina virtual del segundo controlador de dominio**:</span><span class="sxs-lookup"><span data-stu-id="1994b-184">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="1994b-185">Después, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="1994b-185">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="1994b-p110">Se le pedirá que especifique las credenciales de una cuenta de administrador de dominio. Se reiniciará el equipo.</span><span class="sxs-lookup"><span data-stu-id="1994b-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="1994b-188">Después, tendrá que actualizar los servidores DNS de la red virtual para que Azure asigne a las máquinas virtuales las direcciones IP de los dos nuevos controladores de dominio para que las usen como sus servidores DNS.</span><span class="sxs-lookup"><span data-stu-id="1994b-188">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers.</span></span> <span data-ttu-id="1994b-189">ReLlene las variables y, a continuación, ejecute estos comandos desde un símbolo del sistema de Windows PowerShell en el equipo local:</span><span class="sxs-lookup"><span data-stu-id="1994b-189">Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
```
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

<span data-ttu-id="1994b-p112">Tenga en cuenta que reiniciamos los dos controladores de dominio para que no estén configurados con los servidores DNS locales como los servidores DNS. Como ambos son servidores DNS, se configuraron automáticamente con los servidores DNS locales como reenviadores DNS cuando se promovieron a controladores de dominio.</span><span class="sxs-lookup"><span data-stu-id="1994b-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="1994b-p113">Después, es necesario crear un sitio de replicación de Active Directory para garantizar que los servidores de la red virtual de Azure usen los controladores de dominio locales. Conéctese al controlador de dominio con una cuenta de administrador de dominio y ejecute los comandos siguientes desde un símbolo del sistema de Windows PowerShell con permisos de administrador:</span><span class="sxs-lookup"><span data-stu-id="1994b-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="1994b-194">Configurar el servidor de DirSync</span><span class="sxs-lookup"><span data-stu-id="1994b-194">Configure the DirSync server</span></span>

<span data-ttu-id="1994b-195">Use el cliente de escritorio remoto que prefiera y cree una conexión a escritorio remoto a la máquina virtual del servidor de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="1994b-195">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine.</span></span> <span data-ttu-id="1994b-196">Use el nombre DNS de la intranet o el nombre de equipo y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="1994b-196">Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="1994b-197">Después, únase al dominio de AD DS adecuado con estos comandos en el símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1994b-197">Next, join it to the appropriate AD DS domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<AD DS domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="1994b-198">Esta es la configuración completada después de la finalización correcta de esta fase, con los nombres de equipo de marcadores de posición.</span><span class="sxs-lookup"><span data-stu-id="1994b-198">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
**<span data-ttu-id="1994b-199">Fase 2: Controladores de dominio y servidor de DirSync para la autenticación federada de alta disponibilidad en Azure</span><span class="sxs-lookup"><span data-stu-id="1994b-199">Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure</span></span>**

![Fase 2 de la infraestructura de autenticación federada de Office 365 de alta disponibilidad en Azure con controladores de dominio](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="1994b-201">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="1994b-201">Next step</span></span>

<span data-ttu-id="1994b-202">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) para seguir configurando esta carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="1994b-202">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1994b-203">Vea también</span><span class="sxs-lookup"><span data-stu-id="1994b-203">See Also</span></span>

[<span data-ttu-id="1994b-204">Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="1994b-204">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="1994b-205">Identidad federada para el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="1994b-205">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="1994b-206">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="1994b-206">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="1994b-207">Opciones de autenticación federada</span><span class="sxs-lookup"><span data-stu-id="1994b-207">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


