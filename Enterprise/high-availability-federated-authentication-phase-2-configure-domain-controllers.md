---
title: Alta disponibilidad federados controladores de dominio de fase 2 Configuración de autenticación
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Solutions
ms.assetid: 6b0eff4c-2c5e-4581-8393-a36f7b36a72f
description: 'Resumen: Configure los controladores de dominio y el servidor de DirSync para la autenticación federada de alta disponibilidad para Office 365 en Microsoft Azure.'
ms.openlocfilehash: 1e66403348bc2cd9a6dfab56f32735d62c986035
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915155"
---
# <a name="high-availability-federated-authentication-phase-2-configure-domain-controllers"></a><span data-ttu-id="e45d8-103">Fase 2 de la autenticación federada de alta disponibilidad: Configurar controladores de dominio</span><span class="sxs-lookup"><span data-stu-id="e45d8-103">High availability federated authentication Phase 2: Configure domain controllers</span></span>

 <span data-ttu-id="e45d8-104">**Resumen:** Configure los controladores de dominio y el servidor de DirSync para la autenticación federada de alta disponibilidad para Office 365 en Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e45d8-104">**Summary:** Configure the domain controllers and DirSync server for your high availability federated authentication for Office 365 in Microsoft Azure.</span></span>
  
<span data-ttu-id="e45d8-p101">En esta fase de la implementación de alta disponibilidad para la autenticación federada de Office 365 en servicios de infraestructura de Azure, se configuran dos controladores de dominio y el servidor de DirSync en la red virtual de Azure. Después, las solicitudes web de los clientes para la autenticación se pueden autenticar en la red virtual de Azure, en lugar de enviar ese tráfico de autenticación por la conexión VPN de sitio a sitio a la red local.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p101">In this phase of deploying high availability for Office 365 federated authentication in Azure infrastructure services, you configure two domain controllers and the DirSync server in the Azure virtual network. Client web requests for authentication can then be authenticated in the Azure virtual network, rather than sending that authentication traffic across the site-to-site VPN connection to your on-premises network.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e45d8-107">Servicios de federación de Active Directory (AD FS) no puede usar Azure Active Directory Domain Services como un sustituto para los controladores de dominio de Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="e45d8-107">Active Directory Federation Services (AD FS) cannot use Azure Active Directory Domain Services as a substitute for Windows Server AD domain controllers.</span></span> 
  
<span data-ttu-id="e45d8-p102">Debe completar esta fase antes de pasar a en [alta disponibilidad federados de autenticación en la fase 3: configuración de servidores de AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Vea [autenticación federada de alta disponibilidad de implementación para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para todas las fases.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p102">You must complete this phase before moving on to [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). See [Deploy high availability federated authentication for Office 365 in Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) for all of the phases.</span></span>
  
## <a name="create-the-domain-controller-virtual-machines-in-azure"></a><span data-ttu-id="e45d8-110">Crear las máquinas virtuales del controlador de dominio en Azure</span><span class="sxs-lookup"><span data-stu-id="e45d8-110">Create the domain controller virtual machines in Azure</span></span>

<span data-ttu-id="e45d8-111">Primero, necesita rellenar la columna de **Nombre de la máquina virtual** de la Tabla M y modificar los tamaños de las máquinas virtuales según sea necesario en la columna **Tamaño mínimo**.</span><span class="sxs-lookup"><span data-stu-id="e45d8-111">First, you need to fill out the **Virtual machine name** column of Table M and modify virtual machine sizes as needed in the **Minimum size** column.</span></span>
  
|<span data-ttu-id="e45d8-112">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e45d8-112">**Item**</span></span>|<span data-ttu-id="e45d8-113">**Nombre de máquina virtual**</span><span class="sxs-lookup"><span data-stu-id="e45d8-113">**Virtual machine name**</span></span>|<span data-ttu-id="e45d8-114">**Imagen de la galería**</span><span class="sxs-lookup"><span data-stu-id="e45d8-114">**Gallery image**</span></span>|<span data-ttu-id="e45d8-115">**Tipo de almacenamiento**</span><span class="sxs-lookup"><span data-stu-id="e45d8-115">**Storage type**</span></span>|<span data-ttu-id="e45d8-116">**Tamaño mínimo**</span><span class="sxs-lookup"><span data-stu-id="e45d8-116">**Minimum size**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
|<span data-ttu-id="e45d8-117">1.</span><span class="sxs-lookup"><span data-stu-id="e45d8-117">1.</span></span>  <br/> |<span data-ttu-id="e45d8-118">![](./media/Common-Images/TableLine.png) (primer controlador de dominio, ejemplo DC1)</span><span class="sxs-lookup"><span data-stu-id="e45d8-118">![](./media/Common-Images/TableLine.png) (first domain controller, example DC1)</span></span>  <br/> |<span data-ttu-id="e45d8-119">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e45d8-119">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e45d8-120">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e45d8-120">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e45d8-121">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e45d8-121">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e45d8-122">2.</span><span class="sxs-lookup"><span data-stu-id="e45d8-122">2.</span></span>  <br/> |<span data-ttu-id="e45d8-123">![](./media/Common-Images/TableLine.png) (segundo controlador de dominio, ejemplo DC2)</span><span class="sxs-lookup"><span data-stu-id="e45d8-123">![](./media/Common-Images/TableLine.png) (second domain controller, example DC2)</span></span>  <br/> |<span data-ttu-id="e45d8-124">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e45d8-124">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e45d8-125">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e45d8-125">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e45d8-126">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e45d8-126">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e45d8-127">3.</span><span class="sxs-lookup"><span data-stu-id="e45d8-127">3.</span></span>  <br/> |<span data-ttu-id="e45d8-128">![](./media/Common-Images/TableLine.png)(Servidor de sincronización de directorios, ejemplo DS1)</span><span class="sxs-lookup"><span data-stu-id="e45d8-128">![](./media/Common-Images/TableLine.png) (DirSync server, example DS1)</span></span>  <br/> |<span data-ttu-id="e45d8-129">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e45d8-129">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e45d8-130">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e45d8-130">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e45d8-131">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e45d8-131">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e45d8-132">4.</span><span class="sxs-lookup"><span data-stu-id="e45d8-132">4.</span></span>  <br/> |<span data-ttu-id="e45d8-133">![](./media/Common-Images/TableLine.png)(primer servidor AD FS, ejemplo ADFS1)</span><span class="sxs-lookup"><span data-stu-id="e45d8-133">![](./media/Common-Images/TableLine.png) (first AD FS server, example ADFS1)</span></span>  <br/> |<span data-ttu-id="e45d8-134">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e45d8-134">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e45d8-135">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e45d8-135">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e45d8-136">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e45d8-136">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e45d8-137">5.</span><span class="sxs-lookup"><span data-stu-id="e45d8-137">5.</span></span>  <br/> |<span data-ttu-id="e45d8-138">![](./media/Common-Images/TableLine.png)(segundo servidor AD FS, ejemplo ADFS2)</span><span class="sxs-lookup"><span data-stu-id="e45d8-138">![](./media/Common-Images/TableLine.png) (second AD FS server, example ADFS2)</span></span>  <br/> |<span data-ttu-id="e45d8-139">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e45d8-139">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e45d8-140">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e45d8-140">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e45d8-141">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e45d8-141">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e45d8-142">6.</span><span class="sxs-lookup"><span data-stu-id="e45d8-142">6.</span></span>  <br/> |<span data-ttu-id="e45d8-143">![](./media/Common-Images/TableLine.png)(primera aplicación servidor proxy web, ejemplo WEB1)</span><span class="sxs-lookup"><span data-stu-id="e45d8-143">![](./media/Common-Images/TableLine.png) (first web application proxy server, example WEB1)</span></span>  <br/> |<span data-ttu-id="e45d8-144">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e45d8-144">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e45d8-145">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e45d8-145">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e45d8-146">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e45d8-146">Standard_D2</span></span>  <br/> |
|<span data-ttu-id="e45d8-147">7.</span><span class="sxs-lookup"><span data-stu-id="e45d8-147">7.</span></span>  <br/> |<span data-ttu-id="e45d8-148">![](./media/Common-Images/TableLine.png)(segunda aplicación servidor proxy web, ejemplo WEB2)</span><span class="sxs-lookup"><span data-stu-id="e45d8-148">![](./media/Common-Images/TableLine.png) (second web application proxy server, example WEB2)</span></span>  <br/> |<span data-ttu-id="e45d8-149">Windows Server 2016 Datacenter</span><span class="sxs-lookup"><span data-stu-id="e45d8-149">Windows Server 2016 Datacenter</span></span>  <br/> |<span data-ttu-id="e45d8-150">Standard_LRS</span><span class="sxs-lookup"><span data-stu-id="e45d8-150">Standard_LRS</span></span>  <br/> |<span data-ttu-id="e45d8-151">Standard_D2</span><span class="sxs-lookup"><span data-stu-id="e45d8-151">Standard_D2</span></span>  <br/> |
   
 <span data-ttu-id="e45d8-152">**Tabla M - máquinas virtuales para la autenticación federada de alta disponibilidad para Office 365 en Azure**</span><span class="sxs-lookup"><span data-stu-id="e45d8-152">**Table M - Virtual machines for the high availability federated authentication for Office 365 in Azure**</span></span>
  
<span data-ttu-id="e45d8-153">Para obtener la lista completa de tamaños de máquinas virtuales, vea [Tamaños de máquinas virtuales](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span><span class="sxs-lookup"><span data-stu-id="e45d8-153">For the complete list of virtual machine sizes, see [Sizes for virtual machines](https://docs.microsoft.com/azure/virtual-machines/virtual-machines-windows-sizes).</span></span>
  
<span data-ttu-id="e45d8-p103">El siguiente bloque de comandos de Windows Azure PowerShell crea las máquinas virtuales para los dos controladores de dominio. Especifique los valores para las variables, quitar el \< y > caracteres. Tenga en cuenta que este bloque de comandos de Windows Azure PowerShell usa los valores de las tablas siguientes:</span><span class="sxs-lookup"><span data-stu-id="e45d8-p103">The following Azure PowerShell command block creates the virtual machines for the two domain controllers. Specify the values for the variables, removing the \< and > characters. Note that this Azure PowerShell command block uses values from the following tables:</span></span>
  
- <span data-ttu-id="e45d8-157">Tabla N, para las máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="e45d8-157">Table M, for your virtual machines</span></span>
    
- <span data-ttu-id="e45d8-158">Tabla R, para los grupos de recursos</span><span class="sxs-lookup"><span data-stu-id="e45d8-158">Table R, for your resource groups</span></span>
    
- <span data-ttu-id="e45d8-159">Tabla V, para la configuración de la red virtual</span><span class="sxs-lookup"><span data-stu-id="e45d8-159">Table V, for your virtual network settings</span></span>
    
- <span data-ttu-id="e45d8-160">Tabla S, para las subredes</span><span class="sxs-lookup"><span data-stu-id="e45d8-160">Table S, for your subnets</span></span>
    
- <span data-ttu-id="e45d8-161">Tabla I, para las direcciones IP estáticas</span><span class="sxs-lookup"><span data-stu-id="e45d8-161">Table I, for your static IP addresses</span></span>
    
- <span data-ttu-id="e45d8-162">Tabla A, para los conjuntos de disponibilidad</span><span class="sxs-lookup"><span data-stu-id="e45d8-162">Table A, for your availability sets</span></span>
    
<span data-ttu-id="e45d8-163">Recuerde que definido tablas R, V, S, I y A en [alta disponibilidad federados autenticación fase 1: configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span><span class="sxs-lookup"><span data-stu-id="e45d8-163">Recall that you defined Tables R, V, S, I, and A in [High availability federated authentication Phase 1: Configure Azure](high-availability-federated-authentication-phase-1-configure-azure.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e45d8-p104">Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell. Visite [Get started with Azure PowerShell cmdlets (Introducción a los cmdlets de Azure)](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="e45d8-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="e45d8-166">Después de especificar todos los valores correctos, ejecute el bloque resultante en el símbolo del sistema de Azure PowerShell o en el Entorno de scripting integrado (ISE) de PowerShell en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="e45d8-166">When you have supplied all the correct values, run the resulting block at the Azure PowerShell prompt or in the PowerShell Integrated Script Environment (ISE) on your local computer.</span></span>
  
> [!TIP]
> <span data-ttu-id="e45d8-167">Para un archivo de texto que contiene todos los comandos de PowerShell en este artículo y un libro de configuración de Microsoft Excel que genera bloques de comando de PowerShell listos para ejecutarse en función de su configuración personalizada, vea la autenticación federada para Office 365 [en Kit de implementación de Azure](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span><span class="sxs-lookup"><span data-stu-id="e45d8-167">For a text file that contains all of the PowerShell commands in this article and a Microsoft Excel configuration workbook that generates ready-to-run PowerShell command blocks based on your custom settings, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664).</span></span> 
  
```
# Set up variables common to both virtual machines
$locName="<your Azure location>"
$vnetName="<Table V - Item 1 - Value column>"
$subnetName="<Table S - Item 1 - Value column>"
$avName="<Table A - Item 1 - Availability set name column>"
$rgNameTier="<Table R - Item 1 - Resource group name column>"
$rgNameInfra="<Table R - Item 4 - Resource group name column>"

$rgName=$rgNameInfra
$vnet=Get-AzureRMVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$subnet=Get-AzureRmVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $subnetName

$rgName=$rgNameTier
$avSet=Get-AzureRMAvailabilitySet -Name $avName -ResourceGroupName $rgName 

# Create the first domain controller
$vmName="<Table M - Item 1 - Virtual machine name column>"
$vmSize="<Table M - Item 1 - Minimum size column>"
$staticIP="<Table I - Item 1 - Value column>"
$diskStorageType="<Table M - Item 1 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the first domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the second domain controller
$vmName="<Table M - Item 2 - Virtual machine name column>"
$vmSize="<Table M - Item 2 - Minimum size column>"
$staticIP="<Table I - Item 2 - Value column>"
$diskStorageType="<Table M - Item 2 - Storage type column>"
$diskSize=<size of the extra disk for Windows Server AD data in GB>

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize -AvailabilitySetId $avset.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
$diskConfig=New-AzureRmDiskConfig -AccountType $diskStorageType -Location $locName -CreateOption Empty -DiskSizeGB $diskSize
$dataDisk1=New-AzureRmDisk -DiskName ($vmName + "-DataDisk1") -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name ($vmName + "-DataDisk1") -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for the second domain controller." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm

# Create the DirSync server
$vmName="<Table M - Item 3 - Virtual machine name column>"
$vmSize="<Table M - Item 3 - Minimum size column>"
$staticIP="<Table I - Item 3 - Value column>"
$diskStorageType="<Table M - Item 3 - Storage type column>"

$nic=New-AzureRMNetworkInterface -Name ($vmName +"-NIC") -ResourceGroupName $rgName -Location $locName -Subnet $subnet -PrivateIpAddress $staticIP
$vm=New-AzureRMVMConfig -VMName $vmName -VMSize $vmSize

$cred=Get-Credential -Message "Type the name and password of the local administrator account for the DirSync server." 
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName $vmName -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name ($vmName +"-OS") -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType $diskStorageType
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> <span data-ttu-id="e45d8-p105">Debido a que estas máquinas virtuales son para una aplicación de intranet, no se asigna una dirección IP pública o una etiqueta de nombre de dominio DNS y expuestos a Internet. Sin embargo, esto también significa que no se puede conectar a ellos desde el portal de Azure. La opción **Conectar** no está disponible cuando se visualizan las propiedades de la máquina virtual. Utilice el accesorio de conexión a Escritorio remoto u otra herramienta de escritorio remoto para conectarse a la máquina virtual con su privada dirección IP o intranet DNS nombre.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p105">Because these virtual machines are for an intranet application, they are not assigned a public IP address or a DNS domain name label and exposed to the Internet. However, this also means that you cannot connect to them from the Azure portal. The **Connect** option is unavailable when you view the properties of the virtual machine. Use the Remote Desktop Connection accessory or another Remote Desktop tool to connect to the virtual machine using its private IP address or intranet DNS name.</span></span>
  
## <a name="configure-the-first-domain-controller"></a><span data-ttu-id="e45d8-172">Configurar el primer controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="e45d8-172">Configure the first domain controller</span></span>

<span data-ttu-id="e45d8-p106">Use el cliente de Escritorio remoto que prefiera y cree una conexión a Escritorio remoto a la máquina virtual del primer controlador de dominio. Use el nombre DNS de la intranet o el nombre de equipo y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p106">Use the remote desktop client of your choice and create a remote desktop connection to the first domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="e45d8-175">A continuación, agregue el disco de datos adicionales para el primer controlador de dominio con este comando desde un Windows PowerShell el símbolo del sistema **en la primera máquina virtual de controlador de dominio**:</span><span class="sxs-lookup"><span data-stu-id="e45d8-175">Next, add the extra data disk to the first domain controller with this command from a Windows PowerShell command prompt **on the first domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="e45d8-176">El paso siguiente es probar la conectividad del primer controlador de dominio a las ubicaciones en la red de la organización con el comando **ping** para hacer ping a los nombres y direcciones IP de los recursos en la red de la organización.</span><span class="sxs-lookup"><span data-stu-id="e45d8-176">Next, test the first domain controller's connectivity to locations on your organization network by using the **ping** command to ping names and IP addresses of resources on your organization network.</span></span>
  
<span data-ttu-id="e45d8-p107">Este procedimiento garantiza que la resolución de nombres DNS funciona correctamente (que la máquina virtual está configurada correctamente con los servidores DNS locales) y que se pueden enviar y recibir paquetes de la red virtual entre locales. Si esta prueba básica produce errores, póngase en contacto con el departamento de TI para solucionar los problemas de resolución de nombres DNS y de entrega de paquetes.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p107">This procedure ensures that DNS name resolution is working correctly (that the virtual machine is correctly configured with on-premises DNS servers) and that packets can be sent to and from the cross-premises virtual network. If this basic test fails, contact your IT department to troubleshoot the DNS name resolution and packet delivery issues.</span></span>
  
<span data-ttu-id="e45d8-179">Después, desde el símbolo del sistema de Windows PowerShell en el primer controlador de dominio, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="e45d8-179">Next, from the Windows PowerShell command prompt on the first domain controller, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred
```

<span data-ttu-id="e45d8-p108">Se le pedirá que especifique las credenciales de una cuenta de administrador de dominio. Se reiniciará el equipo.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p108">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
## <a name="configure-the-second-domain-controller"></a><span data-ttu-id="e45d8-182">Configurar el segundo controlador de dominio</span><span class="sxs-lookup"><span data-stu-id="e45d8-182">Configure the second domain controller</span></span>

<span data-ttu-id="e45d8-p109">Use el cliente de Escritorio remoto que prefiera y cree una conexión a Escritorio remoto a la máquina virtual del segundo controlador de dominio. Use el nombre DNS de la intranet o el nombre de equipo y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p109">Use the remote desktop client of your choice and create a remote desktop connection to the second domain controller virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="e45d8-185">A continuación, deberá agregar el disco de datos adicionales para el segundo controlador de dominio con este comando desde un Windows PowerShell el símbolo del sistema **en la máquina virtual de controlador de dominio segundo**:</span><span class="sxs-lookup"><span data-stu-id="e45d8-185">Next, you need to add the extra data disk to the second domain controller with this command from a Windows PowerShell command prompt **on the second domain controller virtual machine**:</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="e45d8-186">Después, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="e45d8-186">Next, run the following commands:</span></span>
  
```
$domname="<DNS domain name of the domain for which this computer will be a domain controller, such as corp.contoso.com>"
$cred = Get-Credential -Message "Enter credentials of an account with permission to join a new domain controller to the domain"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -InstallDns -DomainName $domname  -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs" -Credential $cred

```

<span data-ttu-id="e45d8-p110">Se le pedirá que especifique las credenciales de una cuenta de administrador de dominio. Se reiniciará el equipo.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p110">You will be prompted to supply the credentials of a domain administrator account. The computer will restart.</span></span>
  
<span data-ttu-id="e45d8-p111">A continuación, deberá actualizar los servidores DNS de la red virtual, por lo que Azure asigna a las máquinas virtuales en las direcciones IP de los dos nuevos controladores de dominio que se utilizará como sus servidores DNS. Rellenar las variables y, a continuación, ejecute estos comandos desde un símbolo del sistema de Windows PowerShell en el equipo local:</span><span class="sxs-lookup"><span data-stu-id="e45d8-p111">Next, you need to update the DNS servers for your virtual network so that Azure assigns virtual machines the IP addresses of the two new domain controllers to use as their DNS servers. Fill in the variables and then run these commands from a Windows PowerShell command prompt on your local computer:</span></span>
  
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

$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$vnet.DhcpOptions.DnsServers.Add($staticIP1)
$vnet.DhcpOptions.DnsServers.Add($staticIP2) 
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP1)
$vnet.DhcpOptions.DnsServers.Remove($onpremDNSIP2) 
Set-AzureRMVirtualNetwork -VirtualNetwork $vnet
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $firstDCName
Restart-AzureRMVM -ResourceGroupName $adrgName -Name $secondDCName
```

<span data-ttu-id="e45d8-p112">Tenga en cuenta que reiniciamos los dos controladores de dominio para que no estén configurados con los servidores DNS locales como los servidores DNS. Como ambos son servidores DNS, se configuraron automáticamente con los servidores DNS locales como reenviadores DNS cuando se promovieron a controladores de dominio.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p112">Note that we restart the two domain controllers so that they are not configured with the on-premises DNS servers as DNS servers. Because they are both DNS servers themselves, they were automatically configured with the on-premises DNS servers as DNS forwarders when they were promoted to domain controllers.</span></span>
  
<span data-ttu-id="e45d8-p113">Después, es necesario crear un sitio de replicación de Active Directory para garantizar que los servidores de la red virtual de Azure usen los controladores de dominio locales. Conéctese al controlador de dominio con una cuenta de administrador de dominio y ejecute los comandos siguientes desde un símbolo del sistema de Windows PowerShell con permisos de administrador:</span><span class="sxs-lookup"><span data-stu-id="e45d8-p113">Next, we need to create an Active Directory replication site to ensure that servers in the Azure virtual network use the local domain controllers. Connect to either domain controller with a domain administrator account and run the following commands from an administrator-level Windows PowerShell prompt:</span></span>
  
```
$vnet="<Table V - Item 1 - Value column>"
$vnetSpace="<Table V - Item 4 - Value column>"
New-ADReplicationSite -Name $vnet 
New-ADReplicationSubnet -Name $vnetSpace -Site $vnet
```

## <a name="configure-the-dirsync-server"></a><span data-ttu-id="e45d8-195">Configurar el servidor de DirSync</span><span class="sxs-lookup"><span data-stu-id="e45d8-195">Configure the DirSync server</span></span>

<span data-ttu-id="e45d8-p114">Use el cliente de escritorio remoto de su elección y crear una conexión a Escritorio remoto en la máquina virtual de servidor de sincronización de directorios. Use su nombre de equipo o DNS de intranet y las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="e45d8-p114">Use the remote desktop client of your choice and create a remote desktop connection to the DirSync server virtual machine. Use its intranet DNS or computer name and the credentials of the local administrator account.</span></span>
  
<span data-ttu-id="e45d8-198">Después, únala al dominio de Windows Server AD adecuado con estos comandos en el símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e45d8-198">Next, join it to the appropriate Windows Server AD domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
$domName="<Windows Server AD domain name to join, such as corp.contoso.com>"
$cred=Get-Credential -Message "Type the name and password of a domain acccount."
Add-Computer -DomainName $domName -Credential $cred
Restart-Computer
```

<span data-ttu-id="e45d8-199">Esta es la configuración completada después de la finalización correcta de esta fase, con los nombres de equipo de marcadores de posición.</span><span class="sxs-lookup"><span data-stu-id="e45d8-199">Here is the configuration resulting from the successful completion of this phase, with placeholder computer names.</span></span>
  
<span data-ttu-id="e45d8-200">**Fase 2: Controladores de dominio y servidor de DirSync para la autenticación federada de alta disponibilidad en Azure**</span><span class="sxs-lookup"><span data-stu-id="e45d8-200">**Phase 2: The domain controllers and DirSync server for your high availability federated authentication infrastructure in Azure**</span></span>

![Fase 2 de la infraestructura de la autenticación federada de Office 365 con alta disponibilidad en Azure con los controladores de dominio](media/b0c1013b-3fb4-499e-93c1-bf310d8f4c32.png)
  
## <a name="next-step"></a><span data-ttu-id="e45d8-202">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="e45d8-202">Next step</span></span>

<span data-ttu-id="e45d8-203">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) para seguir configurando esta carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="e45d8-203">Use [High availability federated authentication Phase 3: Configure AD FS servers](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md) to continue configuring this workload.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e45d8-204">Vea también</span><span class="sxs-lookup"><span data-stu-id="e45d8-204">See Also</span></span>

[<span data-ttu-id="e45d8-205">Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure</span><span class="sxs-lookup"><span data-stu-id="e45d8-205">Deploy high availability federated authentication for Office 365 in Azure</span></span>](deploy-high-availability-federated-authentication-for-office-365-in-azure.md)
  
[<span data-ttu-id="e45d8-206">Identidad federada para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="e45d8-206">Federated identity for your Office 365 dev/test environment</span></span>](federated-identity-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="e45d8-207">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="e45d8-207">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)

[<span data-ttu-id="e45d8-208">Opciones de autenticación federada</span><span class="sxs-lookup"><span data-stu-id="e45d8-208">Federated authentication options</span></span>](about-office-365-identity.md#federated-authentication-options)


