---
title: "Entorno de desarrollo y pruebas de la configuración básica"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- jan17entnews
- Strat_O365_Enterprise
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Resumen: Crear una intranet simplificada como un entorno de pruebas y desarrollo de Microsoft Azure.'
ms.openlocfilehash: 672486f62a940d812c821fda67d3e92a4164eea8
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="ea125-103">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="ea125-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="ea125-104">**Resumen:** Crear una intranet simplificada como un entorno de pruebas y desarrollo de Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="ea125-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="ea125-105">Este artículo contiene las instrucciones paso a paso para crear el siguiente entorno de desarrollo y pruebas de la configuración básica en Azure:</span><span class="sxs-lookup"><span data-stu-id="ea125-105">This article provides you with step-by-step instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
<span data-ttu-id="ea125-106">**Figura 1: El entorno de desarrollo y prueba de configuración básica**</span><span class="sxs-lookup"><span data-stu-id="ea125-106">**Figure 1: The Base Configuration dev/test environment**</span></span>

![Fase 4 de la configuración base en Azure con la red virtual CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="ea125-p101">El entorno de desarrollo y pruebas de la configuración básica de la figura 1 consta de la subred de la red corporativa en una red virtual de Azure solo de nube denominada TestLab que simula una intranet simplificada y privada conectada a Internet. Contiene tres máquinas virtuales de Azure que ejecutan Windows Server 2016:</span><span class="sxs-lookup"><span data-stu-id="ea125-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It contains three Azure virtual machines running Windows Server 2016:</span></span>
  
- <span data-ttu-id="ea125-110">DC1 está configurada como un controlador de dominio de intranet y un servidor de Sistema de nombres de dominio (DNS)</span><span class="sxs-lookup"><span data-stu-id="ea125-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="ea125-111">App1 está configurada como servidor web y de aplicación general</span><span class="sxs-lookup"><span data-stu-id="ea125-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="ea125-112">	CLIENT1 actúa como cliente de intranet</span><span class="sxs-lookup"><span data-stu-id="ea125-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="ea125-113">Esta configuración permite que DC1, APP1, CLIENT1 y otros equipos de la subred de red corporativa: </span><span class="sxs-lookup"><span data-stu-id="ea125-113">This configuration allows DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="ea125-114">Conectado a Internet para instalar las actualizaciones, obtener acceso a recursos de Internet en tiempo real y participar en las tecnologías de nube pública como Microsoft Office 365 y otros servicios de Azure.</span><span class="sxs-lookup"><span data-stu-id="ea125-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="ea125-115">	Se administren de manera remota mediante conexiones a Escritorio remoto desde el equipo que está conectado a Internet o la red de su organización.</span><span class="sxs-lookup"><span data-stu-id="ea125-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="ea125-116">Puede usar el entorno de pruebas resultante:</span><span class="sxs-lookup"><span data-stu-id="ea125-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="ea125-117">Para desarrollar y probar aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="ea125-117">For application development and testing.</span></span>
    
- <span data-ttu-id="ea125-118">Como la configuración inicial de un entorno de pruebas ampliadas de su propio diseño que incluye máquinas virtuales adicionales, servicios de Azure u otras ofertas de nube de Microsoft, como Office 365 + movilidad y seguridad empresarial.</span><span class="sxs-lookup"><span data-stu-id="ea125-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Security + Mobility.</span></span>
    
<span data-ttu-id="ea125-119">Existen cuatro fases para configurar el entorno de pruebas de configuración de base en Azure:</span><span class="sxs-lookup"><span data-stu-id="ea125-119">There are four phases to setting up the Base Configuration test environment in Azure:</span></span>
  
1. <span data-ttu-id="ea125-120">	Crear la red virtual.</span><span class="sxs-lookup"><span data-stu-id="ea125-120">Create the virtual network.</span></span>
    
2. <span data-ttu-id="ea125-121">	Configurar DC1.</span><span class="sxs-lookup"><span data-stu-id="ea125-121">Configure DC1.</span></span>
    
3. <span data-ttu-id="ea125-122">	Configurar APP1.</span><span class="sxs-lookup"><span data-stu-id="ea125-122">Configure APP1.</span></span>
    
4. <span data-ttu-id="ea125-123">	Configurar CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="ea125-123">Configure CLIENT1.</span></span>
    
<span data-ttu-id="ea125-p102">Si no dispone de una suscripción de Azure, puede suscribirse para una prueba gratuita en [Tratar de Azure](https://azure.microsoft.com/pricing/free-trial/). Si tiene una suscripción a MSDN o Visual Studio, vea [crédito Azure mensual para los suscriptores de Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span><span class="sxs-lookup"><span data-stu-id="ea125-p102">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="ea125-p103">Máquinas virtuales en Azure incurre en un costo económico constante cuando se están ejecutando. Este costo se facturó contra su suscripción de MSDN de prueba, libre o de pago. Para obtener más información acerca de los costos de Azure máquinas virtuales en ejecución, ver [Detalles de precios de máquinas virtuales](https://azure.microsoft.com/pricing/details/virtual-machines/) y [Calculadora de precios de Azure](https://azure.microsoft.com/pricing/calculator/). Para mantener los costos bajos, consulte [minimizar los costos de máquinas de prueba entorno virtual en Azure](base-configuration-dev-test-environment.md#mincost).</span><span class="sxs-lookup"><span data-stu-id="ea125-p103">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Guías de laboratorio de prueba en Microsoft Cloud](images/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="ea125-131">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ea125-131">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-create-the-virtual-network"></a><span data-ttu-id="ea125-132">Fase 1: Crear la red virtual</span><span class="sxs-lookup"><span data-stu-id="ea125-132">Phase 1: Create the virtual network</span></span>

<span data-ttu-id="ea125-133">En primer lugar, abra un símbolo del sistema de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea125-133">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ea125-p104">Los siguientes conjuntos de comandos utilice la última versión de PowerShell de Azure. Consulte [Introducción a los cmdlets de PowerShell de Azure](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span><span class="sxs-lookup"><span data-stu-id="ea125-p104">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="ea125-136">Inicie sesión en su cuenta de Azure con el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="ea125-136">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

> [!TIP]
> <span data-ttu-id="ea125-137">Haga clic [aquí](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) para obtener un archivo de texto que contiene todos los comandos de PowerShell en este artículo.</span><span class="sxs-lookup"><span data-stu-id="ea125-137">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that contains all the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="ea125-138">Obtenga su nombre de suscripción mediante el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="ea125-138">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="ea125-p105">Configure su suscripción de Azure. Cambie todo el contenido entrecomillado, incluidos los caracteres < y >, por los nombres correctos.</span><span class="sxs-lookup"><span data-stu-id="ea125-p105">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="ea125-p106">Después, cree un nuevo grupo de recursos para su entorno de pruebas de configuración básica. Para determinar un nombre único de grupo de recursos, use este comando a fin de enumerar los grupos de recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="ea125-p106">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="ea125-p107">Cree el nuevo grupo de recursos con estos comandos. Reemplace todo el contenido entrecomillado, incluidos los caracteres < y >, por los nombres correctos.</span><span class="sxs-lookup"><span data-stu-id="ea125-p107">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="ea125-145">Después, cree la red virtual de TestLab que hospedará la subred de la red corporativa de la configuración básica y la protegerá con un grupo de seguridad de red.</span><span class="sxs-lookup"><span data-stu-id="ea125-145">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
```

<span data-ttu-id="ea125-146">Esta es su configuración actual.</span><span class="sxs-lookup"><span data-stu-id="ea125-146">This is your current configuration.</span></span>
  
![Fase 1 de la configuración base en Azure con la red virtual y la subred](images/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
## <a name="phase-2-configure-dc1"></a><span data-ttu-id="ea125-148">Fase 2: Configurar DC1</span><span class="sxs-lookup"><span data-stu-id="ea125-148">Phase 2: Configure DC1</span></span>

<span data-ttu-id="ea125-149">A continuación, creamos la máquina virtual DC1 y la configuramos como controlador de dominio para el dominio corp.contoso.com de Windows Server Active Directory (AD) y como servidor DNS para las máquinas virtuales de la red virtual TestLab.</span><span class="sxs-lookup"><span data-stu-id="ea125-149">In this phase, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Windows Server Active Directory (AD) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>
  
<span data-ttu-id="ea125-150">Para crear una máquina virtual Azure para DC1, proporcione el nombre de su grupo de recursos y ejecutar estos comandos en el símbolo del sistema de PowerShell de Azure en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="ea125-150">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzureRMVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
$diskConfig=New-AzureRmDiskConfig -AccountType "StandardLRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzureRmDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzureRmVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="ea125-p108">Se le pedirá un nombre de usuario y una contraseña para la cuenta de administrador local en DC1. Use una contraseña segura y registre el nombre de usuario y la contraseña en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="ea125-p108">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="ea125-153">Después conéctese a la máquina virtual DC1.</span><span class="sxs-lookup"><span data-stu-id="ea125-153">Next, connect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-local-administrator-account-credentials"></a><span data-ttu-id="ea125-154">Conectarse a DC1 usando las credenciales de la cuenta de administrador local</span><span class="sxs-lookup"><span data-stu-id="ea125-154">Connect to DC1 using local administrator account credentials</span></span>

1. <span data-ttu-id="ea125-155">En el [portal de Azure](https://portal.azure.com), haga clic en **grupos de recursos >** <the name of your new resource group> **> DC1 > conectar**.</span><span class="sxs-lookup"><span data-stu-id="ea125-155">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** <the name of your new resource group> **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="ea125-156">Abra el archivo DC1.rdp que se descarga y, a continuación, haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="ea125-156">Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="ea125-157">Especifique el nombre de cuenta de administrador local de DC1:</span><span class="sxs-lookup"><span data-stu-id="ea125-157">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="ea125-158">Para Windows 7:</span><span class="sxs-lookup"><span data-stu-id="ea125-158">For Windows 7:</span></span>
    
    <span data-ttu-id="ea125-p109">En el cuadro de diálogo **Seguridad de Windows** , haga clic en **usar otra cuenta**. En **nombre de usuario**, escriba **DC1\\**[nombre de la cuenta de administrador Local].</span><span class="sxs-lookup"><span data-stu-id="ea125-p109">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="ea125-161">Para Windows 8 o Windows 10:</span><span class="sxs-lookup"><span data-stu-id="ea125-161">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="ea125-p110">En el cuadro de diálogo **Seguridad de Windows** , haga clic en **más opciones**y, a continuación, haga clic en **utilizar una cuenta diferente**. En **nombre de usuario**, escriba **DC1\\**[nombre de la cuenta de administrador Local].</span><span class="sxs-lookup"><span data-stu-id="ea125-p110">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="ea125-164">En **contraseña**, escriba la contraseña de la cuenta de administrador local y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ea125-164">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="ea125-165">Cuando se le pida, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="ea125-165">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="ea125-166">A continuación, agregue un disco de datos adicionales como un nuevo volumen con la letra de unidad F: con este comando en un símbolo de Windows PowerShell de nivel de administrador en DC1.</span><span class="sxs-lookup"><span data-stu-id="ea125-166">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="ea125-p111">A continuación, configure DC1 como controlador de dominio y servidor DNS para el dominio corp.contoso.com. En un símbolo del sistema de Windows PowerShell con el nivel de administrador, ejecute estos comandos:</span><span class="sxs-lookup"><span data-stu-id="ea125-p111">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\\NTDS" -SysvolPath "F:\\SYSVOL" -LogPath "F:\\Logs"
```

<span data-ttu-id="ea125-p112">Debe especificar una contraseña de administrador de modo seguro. Guarde esta contraseña en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="ea125-p112">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="ea125-171">Tenga en cuenta que estos comandos pueden tardan unos minutos en completarse.</span><span class="sxs-lookup"><span data-stu-id="ea125-171">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="ea125-172">Después de que DC1 se reinicie, vuelva a conectarse a la máquina virtual de DC1.</span><span class="sxs-lookup"><span data-stu-id="ea125-172">After DC1 restarts, reconnect to the DC1 virtual machine.</span></span>
  
### <a name="connect-to-dc1-using-domain-credentials"></a><span data-ttu-id="ea125-173">Conectarse a DC1 usando las credenciales de dominio</span><span class="sxs-lookup"><span data-stu-id="ea125-173">Connect to DC1 using domain credentials</span></span>

1. <span data-ttu-id="ea125-174">En el [portal de Azure](https://portal.azure.com), haga clic en **grupos de recursos >** <your resource group name> **> DC1 > conectar**.</span><span class="sxs-lookup"><span data-stu-id="ea125-174">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** <your resource group name> **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="ea125-175">Ejecute el archivo DC1.rdp que se descarga y, a continuación, haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="ea125-175">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="ea125-p113">En la **Seguridad de Windows**, haga clic en **usar otra cuenta**. En **nombre de usuario**, escriba **CORP\\**[nombre de la cuenta de administrador Local].</span><span class="sxs-lookup"><span data-stu-id="ea125-p113">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="ea125-178">En **contraseña**, escriba la contraseña de la cuenta de administrador local y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ea125-178">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="ea125-179">Cuando se le pida, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="ea125-179">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="ea125-p114">A continuación, cree una cuenta de usuario en Active Directory que se usará al iniciar sesión en equipos de miembros del dominio CORP. En un símbolo del sistema de Windows PowerShell con un nivel de administrador, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="ea125-p114">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="ea125-p115">Tenga en cuenta que este comando le solicita que proporcione la contraseña de la cuenta User1. Dado que esta cuenta se usará para las conexiones de Escritorio remoto en todos los equipos miembros del dominio CORP, elija una contraseña segura. Anote la contraseña de la cuenta User1 y almacénela en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="ea125-p115">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="ea125-p116">Después, configure la nueva cuenta User1 como administrador de organización. En un símbolo del sistema de Windows PowerShell con el nivel de administrador, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="ea125-p116">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="ea125-187">Cerrar la sesión de escritorio remoto con DC1 y, a continuación, volver a conectar mediante el CORP\\cuenta de Usuario1.</span><span class="sxs-lookup"><span data-stu-id="ea125-187">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="ea125-188">Después, para permitir el tráfico desde la herramienta Ping, ejecute este comando desde un símbolo del sistema de Windows PowerShell con el nivel de administrador:</span><span class="sxs-lookup"><span data-stu-id="ea125-188">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="ea125-189">Esta es su configuración actual.</span><span class="sxs-lookup"><span data-stu-id="ea125-189">This is your current configuration.</span></span>
  
![Fase 2 de la configuración base en Azure con la máquina virtual DC1](images/49069908-29c3-4d73-87f7-debbea067261.png)
  
## <a name="phase-3-configure-app1"></a><span data-ttu-id="ea125-191">Fase 3: Configurar APP1</span><span class="sxs-lookup"><span data-stu-id="ea125-191">Phase 3: Configure APP1</span></span>

<span data-ttu-id="ea125-192">App1 proporciona servicios de uso compartido de archivos y web.</span><span class="sxs-lookup"><span data-stu-id="ea125-192">APP1 provides web and file sharing services.</span></span>
  
<span data-ttu-id="ea125-193">Para crear una máquina virtual de Azure para APP1, indique el nombre de su grupo de recursos, ubicación de Azure y nombre de la cuenta de almacenamiento, y ejecute estos comandos en el símbolo del sistema de Azure PowerShell en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="ea125-193">To create an Azure Virtual Machine for APP1, fill in the name of your resource group, Azure location, and storage account name and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="ea125-194">Después, conéctese a la máquina virtual de APP1 usando el nombre y la contraseña de la cuenta de administrador local de APP1 y abra un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea125-194">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="ea125-195">Para comprobar la comunicación de red y de resolución de nombre entre APP1 y DC1, ejecute el comando **ping dc1.corp.contoso.com** y compruebe que hay cuatro respuestas.</span><span class="sxs-lookup"><span data-stu-id="ea125-195">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and verify that there are four replies.</span></span>
  
<span data-ttu-id="ea125-196">Después, una la máquina virtual de APP1 al dominio CORP con estos comandos en un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea125-196">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="ea125-197">Nota que debe proporcionar el CORP\\Usuario1 credenciales de cuenta de dominio después de ejecutar el comando **Agregar equipo** .</span><span class="sxs-lookup"><span data-stu-id="ea125-197">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="ea125-198">Una vez reiniciado APP1, conectarse a ella mediante el CORP\\cuenta usuario1 y una de Windows PowerShell de nivel de administrador abra símbolo del sistema.</span><span class="sxs-lookup"><span data-stu-id="ea125-198">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="ea125-199">Después, convierta a APP1 en un servidor web con este comando en el símbolo del sistema de Windows PowerShell en APP1.</span><span class="sxs-lookup"><span data-stu-id="ea125-199">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="ea125-200">Por último, cree una carpeta compartida y un archivo de texto dentro de la carpeta en APP1 con estos comandos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea125-200">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\\files -type directory
Write-Output "This is a shared file." | out-file c:\\files\\example.txt
New-SmbShare -name files -path c:\\files -changeaccess CORP\\User1
```

<span data-ttu-id="ea125-201">Esta es su configuración actual.</span><span class="sxs-lookup"><span data-stu-id="ea125-201">This is your current configuration.</span></span>
  
![Fase 3 de la configuración base en Azure con la máquina virtual APP1](images/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
## <a name="phase-4-configure-client1"></a><span data-ttu-id="ea125-203">Fase 4: Configurar CLIENT1</span><span class="sxs-lookup"><span data-stu-id="ea125-203">Phase 4: Configure CLIENT1</span></span>

<span data-ttu-id="ea125-204">CLIENT1 sirve de portátil, tableta o equipo de escritorio común en la intranet de Contoso.</span><span class="sxs-lookup"><span data-stu-id="ea125-204">CLIENT1 acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>
  
> [!NOTE]
> <span data-ttu-id="ea125-p117">El siguiente conjunto de comandos crea CLIENTE1 ejecuta Windows Server 2016 Datacenter, lo que puede realizar para todos los tipos de suscripciones de Azure. Si tiene una suscripción de Azure basada en Visual Studio, puede crear CLIENTE1 ejecutando Windows 10, Windows 8 o Windows 7 con el [portal de Azure](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="ea125-p117">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10, Windows 8, or Windows 7 with the [Azure portal](https://portal.azure.com).</span></span> 
  
<span data-ttu-id="ea125-207">Para crear una máquina virtual de Azure para CLIENT1, indique el nombre de su grupo de recursos, ubicación de Azure y nombre de la cuenta de almacenamiento, y ejecute estos comandos en el símbolo del sistema de Azure PowerShell en el equipo local.</span><span class="sxs-lookup"><span data-stu-id="ea125-207">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group, Azure location, and storage account name and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzureRmResourceGroup -Name $rgName).Location
$vnet=Get-AzureRMVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzureRMPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="ea125-208">Después, conéctese a la máquina virtual de CLIENT1 usando el nombre y la contraseña de la cuenta de administrador local de CLIENT1, y abra un símbolo del sistema de nivel de administrador de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea125-208">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="ea125-209">Para comprobar la comunicación de red y de resolución de nombre entre CLIENTE1 y DC1, ejecute el comando **ping dc1.corp.contoso.com** en un símbolo del sistema de Windows PowerShell y compruebe que hay cuatro respuestas.</span><span class="sxs-lookup"><span data-stu-id="ea125-209">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and verify that there are four replies.</span></span>
  
<span data-ttu-id="ea125-210">Después, una la máquina virtual de CLIENT1 al dominio CORP con estos comandos en un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea125-210">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="ea125-211">Nota que debe proporcionar el CORP\\Usuario1 credenciales de cuenta de dominio después de ejecutar el comando **Agregar equipo** .</span><span class="sxs-lookup"><span data-stu-id="ea125-211">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="ea125-212">Cuando se reinicie CLIENTE1, conectarse a ella mediante el CORP\\Usuario1 nombre de cuenta y contraseña y, a continuación, abra un símbolo del sistema de nivel de administrador de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ea125-212">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="ea125-213">Después, compruebe que puede tener acceso a recursos compartidos de web y archivos en APP1 desde CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="ea125-213">Next, verify that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
### <a name="verify-client-access-to-app1"></a><span data-ttu-id="ea125-214">Comprobar el acceso de CLIENT a APP1</span><span class="sxs-lookup"><span data-stu-id="ea125-214">Verify CLIENT access to APP1</span></span>

1. <span data-ttu-id="ea125-215">En el administrador del servidor, en el panel de árbol, haga clic en **Servidor Local**.</span><span class="sxs-lookup"><span data-stu-id="ea125-215">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="ea125-216">En **Propiedades de CLIENTE1**, haga clic **en** junto a la **Configuración de seguridad mejorada de Internet Explorer**.</span><span class="sxs-lookup"><span data-stu-id="ea125-216">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="ea125-217">En **La configuración de seguridad mejorada de Internet Explorer**, haga clic en **desactivado** para **los administradores** y **los usuarios**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ea125-217">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="ea125-218">Desde la pantalla de inicio, haga clic en **Internet Explorer**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="ea125-218">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="ea125-p118">En la barra Dirección, escriba **http://app1.corp.contoso.com/**y, a continuación, presione ENTRAR. Debe ver la página web de servicios de Internet Information Server de forma predeterminada para APP1.</span><span class="sxs-lookup"><span data-stu-id="ea125-p118">In the Address bar, type **http://app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="ea125-221">En la barra de tareas de escritorio, haga clic en el icono del Explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="ea125-221">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="ea125-p119">En la barra Dirección, escriba ** \\ \\app1\\archivos**, y, a continuación, presione ENTRAR. Debería ver una ventana de carpeta con el contenido de la carpeta compartida de archivos.</span><span class="sxs-lookup"><span data-stu-id="ea125-p119">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="ea125-p120">En la ventana de carpeta compartida de **archivos** , haga doble clic en el archivo **ejemplo.txt** . Debería ver el contenido del archivo ejemplo.txt.</span><span class="sxs-lookup"><span data-stu-id="ea125-p120">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="ea125-226">Cierre el **ejemplo.txt - Bloc de notas** y las ventanas de carpeta de **archivos** compartidos.</span><span class="sxs-lookup"><span data-stu-id="ea125-226">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="ea125-227">Esta es su configuración final.</span><span class="sxs-lookup"><span data-stu-id="ea125-227">This is your final configuration.</span></span>
  
![Fase 4 de la configuración base en Azure con la red virtual CLIENT1](images/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="ea125-229">La configuración básica de Azure está preparada para desarrollar y probar aplicaciones o para crear entornos de prueba adicionales.</span><span class="sxs-lookup"><span data-stu-id="ea125-229">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="ea125-230">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos en la pila de una guía de laboratorio de prueba de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ea125-230">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="ea125-231">Minimizar los costos del entorno de pruebas de máquinas virtuales en Azure</span><span class="sxs-lookup"><span data-stu-id="ea125-231">Minimizing the costs of test environment virtual machines in Azure</span></span>
<span data-ttu-id="ea125-232"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="ea125-232"></span></span>

<span data-ttu-id="ea125-233">Para minimizar el costo de ejecutar máquinas virtuales de entorno de pruebas, puede realizar una de las siguientes acciones:</span><span class="sxs-lookup"><span data-stu-id="ea125-233">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="ea125-p121">Crear el entorno de pruebas y realizar las pruebas necesarias y la demostración lo más rápidamente posible. Cuando haya terminado, elimine el grupo de recursos del entorno de pruebas.</span><span class="sxs-lookup"><span data-stu-id="ea125-p121">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="ea125-236">	Ponga las máquinas virtuales del entorno de pruebas virtual en un estado desasignado.</span><span class="sxs-lookup"><span data-stu-id="ea125-236">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="ea125-237">Para apagar las máquinas virtuales con Azure PowerShell, rellene el nombre del grupo de recursos y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="ea125-237">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzureRMVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="ea125-238">Para asegurarse de que las máquinas virtuales funcionan correctamente al iniciarlas todas desde el estado Detenido (Desasignado), debe iniciarlas en el orden siguiente:</span><span class="sxs-lookup"><span data-stu-id="ea125-238">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="ea125-239">DC1</span><span class="sxs-lookup"><span data-stu-id="ea125-239">DC1</span></span>
    
2. <span data-ttu-id="ea125-240">APP1</span><span class="sxs-lookup"><span data-stu-id="ea125-240">APP1</span></span>
    
3. <span data-ttu-id="ea125-241">CLIENTE1</span><span class="sxs-lookup"><span data-stu-id="ea125-241">CLIENT1</span></span>
    
<span data-ttu-id="ea125-242">Para iniciar las máquinas virtuales en orden con Azure PowerShell, rellene el nombre del grupo de recursos y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="ea125-242">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzureRMVM -ResourceGroupName $rgName -Name "DC1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "APP1"
Start-AzureRMVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="ea125-243">See Also</span><span class="sxs-lookup"><span data-stu-id="ea125-243">See Also</span></span>

<span data-ttu-id="ea125-244"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="ea125-244"></span></span>

[<span data-ttu-id="ea125-245">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="ea125-245">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="ea125-246">Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="ea125-246">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="ea125-247">Seguridad de la aplicación de nube para su entorno de pruebas y desarrollo de Office 365</span><span class="sxs-lookup"><span data-stu-id="ea125-247">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="ea125-248">Una protección avanzada para su entorno de pruebas y desarrollo de Office 365</span><span class="sxs-lookup"><span data-stu-id="ea125-248">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
  
[<span data-ttu-id="ea125-249">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="ea125-249">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


