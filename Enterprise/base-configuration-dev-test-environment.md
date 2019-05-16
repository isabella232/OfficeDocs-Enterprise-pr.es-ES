---
title: Entorno de desarrollo y prueba de la configuración básica
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/15/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6fcbb50c-ac68-4be7-9fc5-dd0f275c1e3d
description: 'Resumen: Cree una intranet simplificada como entorno de desarrollo y prueba en Microsoft Azure.'
ms.openlocfilehash: 80011fced526ecf38cf31a89015ff0bbe7fa8b7a
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068296"
---
# <a name="base-configuration-devtest-environment"></a><span data-ttu-id="e3268-103">Entorno de desarrollo y prueba de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="e3268-103">Base Configuration dev/test environment</span></span>

 <span data-ttu-id="e3268-104">**Resumen:** Cree una intranet simplificada como entorno de desarrollo y prueba en Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="e3268-104">**Summary:** Create a simplified intranet as a dev/test environment in Microsoft Azure.</span></span>
  
<span data-ttu-id="e3268-105">En este artículo se ofrecen instrucciones para crear el siguiente entorno de desarrollo y prueba de la configuración básica en Azure:</span><span class="sxs-lookup"><span data-stu-id="e3268-105">This article provides you with instructions to create the following Base Configuration dev/test environment in Azure:</span></span>
  
![Configuración básica de Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="e3268-107">**Figura 1: Entorno de desarrollo y prueba de la configuración básica**</span><span class="sxs-lookup"><span data-stu-id="e3268-107">**Figure 1: The Base Configuration dev/test environment**</span></span>

<span data-ttu-id="e3268-p101">El entorno de desarrollo y prueba de la configuración básica de la figura 1 consta de la subred de la red corporativa en una red virtual de Azure solo de nube denominada TestLab que simula una intranet simplificada y privada conectada a Internet. Contiene tres máquinas virtuales de Azure con Windows Server 2016:</span><span class="sxs-lookup"><span data-stu-id="e3268-p101">The Base Configuration dev/test environment in Figure 1 consists of the Corpnet subnet in a cloud-only Azure virtual network named TestLab that simulates a simplified, private intranet connected to the Internet. It has three Azure virtual machines running Windows Server 2016:</span></span>
  
- <span data-ttu-id="e3268-110">DC1 está configurado como controlador de dominio de intranet y servidor del Sistema de nombres de dominio (DNS)</span><span class="sxs-lookup"><span data-stu-id="e3268-110">DC1 is configured as an intranet domain controller and Domain Name System (DNS) server</span></span>
    
- <span data-ttu-id="e3268-111">App1 está configurada como servidor web y de aplicación general</span><span class="sxs-lookup"><span data-stu-id="e3268-111">APP1 is configured as a general application and web server</span></span>
    
- <span data-ttu-id="e3268-112">CLIENT1 actúa como cliente de intranet</span><span class="sxs-lookup"><span data-stu-id="e3268-112">CLIENT1 acts as an intranet client</span></span>
    
<span data-ttu-id="e3268-113">Con esta configuración, DC1, APP1, CLIENT1 y otros equipos de la subred de red corporativa pueden:</span><span class="sxs-lookup"><span data-stu-id="e3268-113">This configuration lets DC1, APP1, CLIENT1, and additional Corpnet subnet computers to be:</span></span> 
  
- <span data-ttu-id="e3268-114">Conectarse a Internet para instalar actualizaciones, obtener acceso a recursos de Internet en tiempo real y participar en tecnologías de nube pública como Office 365 y otros servicios de Azure.</span><span class="sxs-lookup"><span data-stu-id="e3268-114">Connected to the Internet to install updates, access Internet resources in real time, and participate in public cloud technologies such as Microsoft Office 365 and other Azure services.</span></span>
    
- <span data-ttu-id="e3268-115">Administrarse de manera remota con conexiones a Escritorio remoto desde el equipo que está conectado a Internet o la red de su organización.</span><span class="sxs-lookup"><span data-stu-id="e3268-115">Remotely managed using Remote Desktop connections from your computer that is connected to the Internet or your organization network.</span></span>
    
<span data-ttu-id="e3268-116">Puede usar el entorno de pruebas resultante:</span><span class="sxs-lookup"><span data-stu-id="e3268-116">You can use the resulting test environment:</span></span>
  
- <span data-ttu-id="e3268-117">Para desarrollar y probar aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="e3268-117">For application development and testing.</span></span>
    
- <span data-ttu-id="e3268-118">Como configuración inicial de un entorno de pruebas ampliado que haya diseñado usted mismo y que incluya máquinas virtuales adicionales, servicios de Azure u otras ofertas de nube de Microsoft tales como Office 365 y Enterprise Mobility + Security (EMS).</span><span class="sxs-lookup"><span data-stu-id="e3268-118">As the initial configuration of an extended test environment of your own design that includes additional virtual machines, Azure services, or other Microsoft cloud offerings such as Office 365 and Enterprise Mobility + Security (EMS).</span></span>
    
<span data-ttu-id="e3268-119">Existen dos métodos para crear este entorno:</span><span class="sxs-lookup"><span data-stu-id="e3268-119">There are two methods to creating this environment:</span></span>

1. <span data-ttu-id="e3268-120">Una plantilla de Azure Resource Manager</span><span class="sxs-lookup"><span data-stu-id="e3268-120">An Azure Resource Manager template</span></span>
2. <span data-ttu-id="e3268-121">Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3268-121">Azure Powershell</span></span>

## <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a><span data-ttu-id="e3268-122">Método 1: Crear la intranet simulada con una plantilla de Azure Resource Manager.</span><span class="sxs-lookup"><span data-stu-id="e3268-122">Method 1: Build your simulated intranet with an Azure Resource Manager template</span></span>

<span data-ttu-id="e3268-p102">En este método, usará una plantilla de Azure Resource Manager (ARM) para crear la intranet simulada. Las plantillas ARM contienen todas las instrucciones para crear y configurar la infraestructura de red de Azure y las máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="e3268-p102">In this method, you use an Azure Resource Manager (ARM) template to build out the simulated intranet. ARM templates contain all of the instructions to create and configure the Azure networking infrastructure and the virtual machines.</span></span>

<span data-ttu-id="e3268-125">Antes de implementar la plantilla, lea la [Página de plantilla Léame](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) y prepare la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="e3268-125">Prior to deploying the template, read through the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) and have the following information ready:</span></span>

- <span data-ttu-id="e3268-p103">El nombre de la suscripción de Azure. Tendrá que escribir esta etiqueta en el campo **suscripción** de la página **Implementación personalizada**.</span><span class="sxs-lookup"><span data-stu-id="e3268-p103">The Azure subscription name. You’ll need to enter this label in the **Subscription** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="e3268-p104">El nombre del grupo de recursos de Azure. Tendrá que escribir esta etiqueta en el campo **grupo de recursos** de la página **Implementación personalizada**.</span><span class="sxs-lookup"><span data-stu-id="e3268-p104">The Azure resource group name. You’ll need to enter this label in the **Resource group** field of the **Custom deployment** page.</span></span>
- <span data-ttu-id="e3268-p105">Un prefijo de etiqueta DNS para las URL de las direcciones IP públicas de sus máquinas virtuales. Tendrá que escribir esta etiqueta en el campo **Prefijo de etiqueta Dns** de la página **implementación personalizada**.</span><span class="sxs-lookup"><span data-stu-id="e3268-p105">A DNS label prefix for the URLs of the public IP addresses of your virtual machines. You’ll need to enter this label in the **Dns Label Prefix** field of the **Custom deployment** page.</span></span>

<span data-ttu-id="e3268-132">Después de leer las instrucciones, haga clic en **Implementar en Azure** en la [página de plantilla Léame](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) para empezar.</span><span class="sxs-lookup"><span data-stu-id="e3268-132">After reading through the instructions, click **Deploy to Azure** on the [template README page](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm) to get started.</span></span>

>[!Note]
><span data-ttu-id="e3268-133">La intranet simulada creada por la plantilla ARM requiere una suscripción pagada de Azure.</span><span class="sxs-lookup"><span data-stu-id="e3268-133">The simulated intranet built by the ARM template requires a paid Azure subscription.</span></span>
>

<span data-ttu-id="e3268-134">Esta es la configuración una vez completada la plantilla.</span><span class="sxs-lookup"><span data-stu-id="e3268-134">Here is your configuration after the template is complete.</span></span>

![Configuración básica de Azure](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)


## <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a><span data-ttu-id="e3268-136">Método 2: Crear la intranet simulada con Azure PowerShell</span><span class="sxs-lookup"><span data-stu-id="e3268-136">Method 2: Build your simulated intranet with Azure PowerShell</span></span>

<span data-ttu-id="e3268-137">En este método, utilizará Windows PowerShell y el módulo de Azure PowerShell para crear la infraestructura de red, las máquinas virtuales y su configuración.</span><span class="sxs-lookup"><span data-stu-id="e3268-137">In this method, you use Windows PowerShell and the Azure PowerShell module to build out the networking infrastructure, the virtual machines, and their configuration.</span></span>

<span data-ttu-id="e3268-p106">Use este método si desea obtener experiencia en la creación de elementos de una infraestructura de Azure añadiendo uno a uno los bloques de comando con PowerShell. Puede personalizar los bloques de comandos de PowerShell para la implementación de otras máquinas virtuales en Azure.</span><span class="sxs-lookup"><span data-stu-id="e3268-p106">Use this method if you want to get experience creating elements of Azure infrastructure one command block at a time with PowerShell. You can then customize the PowerShell command blocks for your own deployment of other virtual machines in Azure.</span></span>

<span data-ttu-id="e3268-140">Existen cuatro pasos para configurar el entorno de pruebas de configuración básica en Azure PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e3268-140">There are four steps to setting up the Base Configuration test environment using Azure PowerShell:</span></span>
  
1. <span data-ttu-id="e3268-141">Crear la red virtual.</span><span class="sxs-lookup"><span data-stu-id="e3268-141">Create the virtual network.</span></span>
    
2. <span data-ttu-id="e3268-142">Configurar DC1.</span><span class="sxs-lookup"><span data-stu-id="e3268-142">Configure DC1.</span></span>
    
3. <span data-ttu-id="e3268-143">Configurar APP1.</span><span class="sxs-lookup"><span data-stu-id="e3268-143">Configure APP1.</span></span>
    
4. <span data-ttu-id="e3268-144">Configurar CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="e3268-144">Configure CLIENT1.</span></span>
    
<span data-ttu-id="e3268-p107">Si no dispone de una suscripción de Azure, puede registrarse para obtener una evaluación gratuita en [Cree su cuenta gratuita de Azure hoy mismo](https://azure.microsoft.com/pricing/free-trial/). Si tiene una suscripción a MSDN o a Visual Studio, vea [Crédito mensual de Azure para suscriptores de Visual Studio](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/). </span><span class="sxs-lookup"><span data-stu-id="e3268-p107">If you do not already have an Azure subscription, you can sign up for a free trial at [Try Azure](https://azure.microsoft.com/pricing/free-trial/). If you have an MSDN or Visual Studio subscription, see [Monthly Azure credit for Visual Studio subscribers](https://azure.microsoft.com/pricing/member-offers/msdn-benefits-details/).</span></span>
  
> [!NOTE]
> <span data-ttu-id="e3268-p108">Las máquinas virtuales de Azure implican un costo económico constante cuando se ejecutan. Este costo se factura a la evaluación gratuita, la suscripción a MSDN o la suscripción de pago. Para obtener más información sobre los costos de las máquinas virtuales de Azure en ejecución, vea [Máquinas virtuales Precios](https://azure.microsoft.com/pricing/details/virtual-machines/) y [Calculadora de precios de Azure](https://azure.microsoft.com/pricing/calculator/). Para mantener los costos bajos, consulte [Minimizar los costos del entorno de pruebas de máquinas virtuales en Azure](base-configuration-dev-test-environment.md#mincost).</span><span class="sxs-lookup"><span data-stu-id="e3268-p108">Virtual machines in Azure incur an ongoing monetary cost when they are running. This cost is billed against your free trial, MSDN subscription, or paid subscription. For more information about the costs of running Azure virtual machines, see [Virtual Machines Pricing Details](https://azure.microsoft.com/pricing/details/virtual-machines/) and [Azure Pricing Calculator](https://azure.microsoft.com/pricing/calculator/). To keep costs down, see [Minimizing the costs of test environment virtual machines in Azure](base-configuration-dev-test-environment.md#mincost).</span></span> 
  
![Guías del laboratorio de pruebas de Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
> [!TIP]
> <span data-ttu-id="e3268-152">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del entorno de pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="e3268-152">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the Office 365 Test Lab Guide stack.</span></span>
  
### <a name="step-1-create-the-virtual-network"></a><span data-ttu-id="e3268-153">Paso 1: Crear la red virtual</span><span class="sxs-lookup"><span data-stu-id="e3268-153">Step 1: Create the virtual network</span></span>

<span data-ttu-id="e3268-154">En este paso, creará la red virtual de TestLab en Azure.</span><span class="sxs-lookup"><span data-stu-id="e3268-154">In this step, you the TestLab virtual network in Azure.</span></span>

<span data-ttu-id="e3268-155">En primer lugar, abra un símbolo del sistema de Azure PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3268-155">First, start an Azure PowerShell prompt.</span></span>
  
> [!NOTE]
> <span data-ttu-id="e3268-p109">Los siguientes conjuntos de comandos utilizan la última versión de Azure PowerShell. Vea [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/es-ES/powershell/azureps-cmdlets-docs/) (Introducción a los cmdlets de Azure PowerShell).</span><span class="sxs-lookup"><span data-stu-id="e3268-p109">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/en-us/powershell/azureps-cmdlets-docs/).</span></span> 
  
<span data-ttu-id="e3268-158">Inicie sesión en su cuenta de Azure con el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="e3268-158">Sign in to your Azure account with the following command.</span></span>
  
```
Connect-AzAccount
```

> [!TIP]
> <span data-ttu-id="e3268-159">Para obtener un archivo de texto que contenga todos los comandos de PowerShell de este artículo, haga clic [aquí](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d).</span><span class="sxs-lookup"><span data-stu-id="e3268-159">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-ba957d3d) to get a text file that has all the PowerShell commands in this article.</span></span>

<span data-ttu-id="e3268-160">Obtenga su nombre de suscripción mediante el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="e3268-160">Get your subscription name using the following command.</span></span>
  
```
Get-AzSubscription | Sort Name | Select Name
```

<span data-ttu-id="e3268-p110">Configure su suscripción de Azure. Cambie todo el contenido entrecomillado, incluidos los caracteres < y >, por los nombres correctos.</span><span class="sxs-lookup"><span data-stu-id="e3268-p110">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

<span data-ttu-id="e3268-p111">Después, cree un nuevo grupo de recursos para su entorno de pruebas de configuración básica. Para determinar un nombre único de grupo de recursos, use este comando a fin de enumerar los grupos de recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="e3268-p111">Next, create a new resource group for your Base Configuration test lab. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="e3268-p112">Cree el nuevo grupo de recursos con estos comandos. Reemplace todo el contenido entrecomillado, incluidos los caracteres < y >, por los nombres correctos.</span><span class="sxs-lookup"><span data-stu-id="e3268-p112">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="e3268-167">Después, cree la red virtual de TestLab que hospedará la subred de la red corporativa de la configuración básica y la protegerá con un grupo de seguridad de red.</span><span class="sxs-lookup"><span data-stu-id="e3268-167">Next, you create the TestLab virtual network that will host the Corpnet subnet of the base configuration and protect it with a network security group.</span></span>
  
```
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

<span data-ttu-id="e3268-168">Esta es su configuración actual.</span><span class="sxs-lookup"><span data-stu-id="e3268-168">This is your current configuration.</span></span>
  
![Paso 1 de la configuración básica en Azure con la red virtual y la subred](media/0b5634fc-4e1c-469d-873d-97ed7e587411.png)
  
### <a name="step-2-configure-dc1"></a><span data-ttu-id="e3268-170">Paso 2: Configurar DC1</span><span class="sxs-lookup"><span data-stu-id="e3268-170">Step 2: Configure DC1</span></span>

<span data-ttu-id="e3268-171">En este paso, creamos la máquina virtual DC1 y la configuramos como controlador de dominio para el dominio corp.contoso.com de Servicios de dominio de Active Directory (AD DS) y como servidor DNS para las máquinas virtuales de la red virtual TestLab.</span><span class="sxs-lookup"><span data-stu-id="e3268-171">In this step, we create the DC1 virtual machine and configure it as a domain controller for the corp.contoso.com Active Directory Domain Services (AD DS) domain and a DNS server for the virtual machines of the TestLab virtual network.</span></span>

> [!NOTE]
> <span data-ttu-id="e3268-p113">Antes de ejecutar el bloque de comandos siguiente, asegúrese de que la región de Azure (ubicación) que ha elegido es compatible con el tamaño de la máquina virtual de Azure, que está establecido por defecto en Standard_A1. Haga clic [aquí](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) para ver la información más reciente sobre los tamaños y ubicaciones de la máquina virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="e3268-p113">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="e3268-174">Para crear una máquina virtual de Azure para DC1, indique el nombre de su grupo de recursos y ejecute estos comandos desde el símbolo del sistema de Azure PowerShell en su equipo local.</span><span class="sxs-lookup"><span data-stu-id="e3268-174">To create an Azure virtual machine for DC1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="e3268-p114">Se le pedirá un nombre de usuario y una contraseña para la cuenta de administrador local en DC1. Use una contraseña segura y registre el nombre de usuario y la contraseña en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="e3268-p114">You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.</span></span>
  
<span data-ttu-id="e3268-177">Después conéctese a la máquina virtual DC1.</span><span class="sxs-lookup"><span data-stu-id="e3268-177">Next, connect to the DC1 virtual machine.</span></span>
  
1. <span data-ttu-id="e3268-178">En el [Azure Portal](https://portal.azure.com), haga clic en **Grupos de recursos** [nombre del nuevo grupo de recursos nuevo] **> DC1 > Conectar**.</span><span class="sxs-lookup"><span data-stu-id="e3268-178">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [the name of your new resource group] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="e3268-p115">En el panel abierto, haga clic en **Descargar archivo RDP**. Abra el archivo DC1.rdp descargado y, después, haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="e3268-p115">In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="e3268-181">Especifique el nombre de la cuenta del administrador local de DC1:</span><span class="sxs-lookup"><span data-stu-id="e3268-181">Specify the DC1 local administrator account name:</span></span>
    
  - <span data-ttu-id="e3268-182">Para Windows 7:</span><span class="sxs-lookup"><span data-stu-id="e3268-182">For Windows 7:</span></span>
    
    <span data-ttu-id="e3268-p116">En el cuadro de diálogo **Seguridad de Windows**, haga clic en **Usar otra cuenta**. En **Nombre de usuario**, escriba **DC1\\**[nombre de la cuenta de administrador local].</span><span class="sxs-lookup"><span data-stu-id="e3268-p116">In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
  - <span data-ttu-id="e3268-185">Para Windows 8 o Windows 10:</span><span class="sxs-lookup"><span data-stu-id="e3268-185">For Windows 8 or Windows 10:</span></span>
    
    <span data-ttu-id="e3268-p117">En el cuadro de diálogo **Seguridad de Windows**, haga clic en **Más opciones** y luego en **Usar una cuenta diferente**. En **Nombre de usuario**, escriba **DC1\\**[nombre de la cuenta de administrador local]</span><span class="sxs-lookup"><span data-stu-id="e3268-p117">In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="e3268-188">En **Contraseña**, escriba la contraseña de la cuenta de administrador local y luego haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="e3268-188">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="e3268-189">Cuando se le solicite, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="e3268-189">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="e3268-190">Después, agregue otro disco de datos como nuevo volumen con la letra de unidad F: con este comando en un símbolo del sistema de Windows PowerShell con nivel de administrador en DC1.</span><span class="sxs-lookup"><span data-stu-id="e3268-190">Next, add an extra data disk as a new volume with the drive letter F: with this command at an administrator-level Windows PowerShell command prompt on DC1.</span></span>
  
```
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

<span data-ttu-id="e3268-p118">A continuación, configure DC1 como controlador de dominio y servidor DNS para el dominio corp.contoso.com. En un símbolo del sistema de Windows PowerShell con el nivel de administrador, ejecute estos comandos:</span><span class="sxs-lookup"><span data-stu-id="e3268-p118">Next, configure DC1 as a domain controller and DNS server for the corp.contoso.com domain. Run these commands at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName corp.contoso.com -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
<span data-ttu-id="e3268-p119">Debe especificar una contraseña de administrador de modo seguro. Guarde esta contraseña en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="e3268-p119">You will need to specify a safe mode administrator password. Store this password in a secure location.</span></span>
  
<span data-ttu-id="e3268-195">Tenga en cuenta que estos comandos pueden tardan unos minutos en completarse.</span><span class="sxs-lookup"><span data-stu-id="e3268-195">Note that these commands can take a few minutes to complete.</span></span>
  
<span data-ttu-id="e3268-196">Después de que DC1 se reinicie, vuelva a conectarse a la máquina virtual de DC1 con las credenciales del dominio.</span><span class="sxs-lookup"><span data-stu-id="e3268-196">After DC1 restarts, reconnect to the DC1 virtual machine using domain credentials.</span></span>
  
1. <span data-ttu-id="e3268-197">En [Azure Portal](https://portal.azure.com), haga clic en **Grupos de recursos >** [nombre del grupo de recursos] **> DC1 > Conectar**.</span><span class="sxs-lookup"><span data-stu-id="e3268-197">In the [Azure portal](https://portal.azure.com), click **Resource Groups >** [your resource group name] **> DC1 > Connect**.</span></span>
    
2. <span data-ttu-id="e3268-198">Ejecute el archivo DC1.rdp que se descarga y luego haga clic en **Conectar**.</span><span class="sxs-lookup"><span data-stu-id="e3268-198">Run the DC1.rdp file that is downloaded, and then click **Connect**.</span></span>
    
3. <span data-ttu-id="e3268-p120">En **Seguridad de Windows**, haga clic en **Usar otra cuenta**. En **Nombre de usuario**, escriba **CORP\\**[nombre de la cuenta de administrador local].</span><span class="sxs-lookup"><span data-stu-id="e3268-p120">In **Windows Security**, click **Use another account**. In **User name**, type **CORP\\**[Local administrator account name].</span></span>
    
4. <span data-ttu-id="e3268-201">En **Contraseña**, escriba la contraseña de la cuenta de administrador local y luego haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="e3268-201">In **Password**, type the password of the local administrator account, and then click **OK**.</span></span>
    
5. <span data-ttu-id="e3268-202">Cuando se le solicite, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="e3268-202">When prompted, click **Yes**.</span></span>
    
<span data-ttu-id="e3268-p121">A continuación, cree una cuenta de usuario en Active Directory que se usará al iniciar sesión en equipos de miembros del dominio CORP. En un símbolo del sistema de Windows PowerShell con un nivel de administrador, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="e3268-p121">Next, create a user account in Active Directory that will be used when logging in to CORP domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

<span data-ttu-id="e3268-p122">Tenga en cuenta que este comando le solicita que proporcione la contraseña de la cuenta User1. Dado que esta cuenta se usará para las conexiones de Escritorio remoto en todos los equipos miembros del dominio CORP, elija una contraseña segura. Anote la contraseña de la cuenta User1 y almacénela en una ubicación segura.</span><span class="sxs-lookup"><span data-stu-id="e3268-p122">Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all CORP domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.</span></span>
  
<span data-ttu-id="e3268-p123">Después, configure la nueva cuenta User1 como administrador de empresa. En un símbolo del sistema de Windows PowerShell con nivel de administrador, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="e3268-p123">Next, configure the new User1 account as an Enterprise Administrator. Run this command at the administrator-level Windows PowerShell command prompt.</span></span>
  
```
Add-ADPrincipalGroupMembership -Identity "CN=User1,CN=Users,DC=corp,DC=contoso,DC=com" -MemberOf "CN=Enterprise Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Domain Admins,CN=Users,DC=corp,DC=contoso,DC=com","CN=Schema Admins,CN=Users,DC=corp,DC=contoso,DC=com"
```

<span data-ttu-id="e3268-210">Cierre la sesión de Escritorio remoto con DC1 y vuelva a conectarse con la cuenta CORP\\User1.</span><span class="sxs-lookup"><span data-stu-id="e3268-210">Close the Remote Desktop session with DC1 and then reconnect using the CORP\\User1 account.</span></span>
  
<span data-ttu-id="e3268-211">Después, para permitir el tráfico desde la herramienta Ping, ejecute este comando desde un símbolo del sistema de Windows PowerShell con nivel de administrador:</span><span class="sxs-lookup"><span data-stu-id="e3268-211">Next, to allow traffic for the Ping tool, run this command at an administrator-level Windows PowerShell command prompt.</span></span>
  
```
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

<span data-ttu-id="e3268-212">Esta es su configuración actual.</span><span class="sxs-lookup"><span data-stu-id="e3268-212">This is your current configuration.</span></span>
  
![Paso 2 de la configuración básica en Azure con la máquina virtual DC1](media/49069908-29c3-4d73-87f7-debbea067261.png)
  
### <a name="step-3-configure-app1"></a><span data-ttu-id="e3268-214">Paso 3: Configurar APP1</span><span class="sxs-lookup"><span data-stu-id="e3268-214">Step 3: Configure APP1</span></span>

<span data-ttu-id="e3268-215">En este paso, creará y configurará APP1, que proporciona servicios de uso compartido de archivos y web.</span><span class="sxs-lookup"><span data-stu-id="e3268-215">In this step, you create and configure APP1, which provides web and file sharing services.</span></span>

> [!NOTE]
> <span data-ttu-id="e3268-p124">Antes de ejecutar el bloque de comandos siguiente, asegúrese de que la región de Azure (ubicación) que ha elegido es compatible con el tamaño de la máquina virtual de Azure, que está establecido por defecto en Standard_A1. Haga clic [aquí](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) para ver la información más reciente sobre los tamaños y ubicaciones de la máquina virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="e3268-p124">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="e3268-218">Para crear una máquina virtual de Azure para APP1, indique el nombre de su grupo de recursos y ejecute estos comandos desde el símbolo del sistema de Azure PowerShell en su equipo local.</span><span class="sxs-lookup"><span data-stu-id="e3268-218">To create an Azure Virtual Machine for APP1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="e3268-219">Después, conéctese a la máquina virtual de APP1 usando el nombre y la contraseña de la cuenta de administrador local de APP1 y abra un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3268-219">Next, connect to the APP1 virtual machine using the APP1 local administrator account name and password, and then open a Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e3268-220">Para comprobar la comunicación de red y la resolución de nombres entre APP1 y DC1, ejecute el comando **ping dc1.corp.contoso.com** y compruebe que hay cuatro respuestas.</span><span class="sxs-lookup"><span data-stu-id="e3268-220">To check name resolution and network communication between APP1 and DC1, run the **ping dc1.corp.contoso.com** command and check that there are four replies.</span></span>
  
<span data-ttu-id="e3268-221">Después, una la máquina virtual de APP1 al dominio CORP con estos comandos en un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3268-221">Next, join the APP1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="e3268-222">Recuerde que debe indicar las credenciales de la cuenta de dominio CORP\\User1 después de ejecutar el comando **Add-Computer**.</span><span class="sxs-lookup"><span data-stu-id="e3268-222">Note that you must supply the CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="e3268-223">Una vez reiniciado APP1, conéctese a él con la cuenta CORP\\User1 y luego abra un símbolo del sistema de Windows PowerShell con nivel de administrador.</span><span class="sxs-lookup"><span data-stu-id="e3268-223">After APP1 restarts, connect to it using the CORP\\User1 account, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e3268-224">Después, convierta a APP1 en un servidor web con este comando en el símbolo del sistema de Windows PowerShell en APP1.</span><span class="sxs-lookup"><span data-stu-id="e3268-224">Next, make APP1 a web server with this command at the Windows PowerShell command prompt on APP1.</span></span>
  
```
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

<span data-ttu-id="e3268-225">Por último, cree una carpeta compartida y un archivo de texto dentro de la carpeta en APP1 con estos comandos de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3268-225">Next, create a shared folder and a text file within the folder on APP1 with these PowerShell commands.</span></span>
  
```
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess CORP\User1
```

<span data-ttu-id="e3268-226">Esta es su configuración actual.</span><span class="sxs-lookup"><span data-stu-id="e3268-226">This is your current configuration.</span></span>
  
![Paso 3 de la configuración básica en Azure con la máquina virtual APP1](media/92cfabb0-7f9d-4291-964d-ac32d52748d7.png)
  
### <a name="step-4-configure-client1"></a><span data-ttu-id="e3268-228">Paso 4: Configurar CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="e3268-228">Step 4: Configure CLIENT1</span></span>

<span data-ttu-id="e3268-229">En este paso, creará y configurará CLIENT1, que actúa como un equipo de escritorio, una tableta o un portátil típico de la intranet de Contoso.</span><span class="sxs-lookup"><span data-stu-id="e3268-229">In this step, you create and configure CLIENT1, which acts as a typical laptop, tablet, or desktop computer on the Contoso intranet.</span></span>

> [!NOTE]  
> <span data-ttu-id="e3268-p125">El siguiente conjunto de comandos crea CLIENT1 con Windows Server 2016 Datacenter, lo que se puede realizar en todos los tipos de suscripciones de Azure. Si tiene una suscripción de Azure basada en Visual Studio, puede crear CLIENT1 con Windows 10 en [Azure Portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="e3268-p125">The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have an Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com).</span></span> 
  

> [!NOTE]
> <span data-ttu-id="e3268-p126">Antes de ejecutar el bloque de comandos siguiente, asegúrese de que la región de Azure (ubicación) que ha elegido es compatible con el tamaño de la máquina virtual de Azure, que está establecido por defecto en Standard_A1. Haga clic [aquí](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) para ver la información más reciente sobre los tamaños y ubicaciones de la máquina virtual de Azure.</span><span class="sxs-lookup"><span data-stu-id="e3268-p126">Before executing the following command block, ensure that the Azure region (location) that you have chosen supports the Azure virtual machine size, which by default is set to Standard_A1. Click [here](https://azure.microsoft.com/global-infrastructure/services/?products=virtual-machines) to see the latest information on Azure virtual machine sizes and locations.</span></span>
  
<span data-ttu-id="e3268-234">Para crear una máquina virtual de Azure para CLIENT1, indique el nombre de su grupo de recursos y ejecute estos comandos desde el símbolo del sistema de Azure PowerShell en su equipo local.</span><span class="sxs-lookup"><span data-stu-id="e3268-234">To create an Azure Virtual Machine for CLIENT1, fill in the name of your resource group and run these commands at the Azure PowerShell command prompt on your local computer.</span></span>
  
```
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A1
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

<span data-ttu-id="e3268-235">Después, conéctese a la máquina virtual de CLIENT1 usando el nombre y la contraseña de la cuenta de administrador local de CLIENT1, y abra un símbolo del sistema de nivel de administrador de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3268-235">Next, connect to the CLIENT1 virtual machine using the CLIENT1 local administrator account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e3268-236">Para comprobar la comunicación de red y la resolución de nombres entre CLIENT1 y DC1, ejecute el comando **ping dc1.corp.contoso.com** en un símbolo del sistema de Windows PowerShell y compruebe que hay cuatro respuestas.</span><span class="sxs-lookup"><span data-stu-id="e3268-236">To check name resolution and network communication between CLIENT1 and DC1, run the **ping dc1.corp.contoso.com** command at a Windows PowerShell command prompt and check that there are four replies.</span></span>
  
<span data-ttu-id="e3268-237">Después, una la máquina virtual de CLIENT1 al dominio CORP con estos comandos en un símbolo del sistema de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3268-237">Next, join the CLIENT1 virtual machine to the CORP domain with these commands at the Windows PowerShell prompt.</span></span>
  
```
Add-Computer -DomainName corp.contoso.com
Restart-Computer
```

<span data-ttu-id="e3268-238">Recuerde que debe indicar las credenciales de la cuenta de dominio CORP\\User1 después de ejecutar el comando **Add-Computer**.</span><span class="sxs-lookup"><span data-stu-id="e3268-238">Note that you must supply your CORP\\User1 domain account credentials after running the **Add-Computer** command.</span></span>
  
<span data-ttu-id="e3268-239">Una vez reiniciado CLIENT1, conéctese a él con el nombre y contraseña de la cuenta CORP\\User1 y luego abra un símbolo del sistema de nivel de administrador de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e3268-239">After CLIENT1 restarts, connect to it using the CORP\\User1 account name and password, and then open an administrator-level Windows PowerShell command prompt.</span></span>
  
<span data-ttu-id="e3268-240">Después, compruebe que tiene acceso a recursos compartidos de archivos y web en APP1 desde CLIENT1.</span><span class="sxs-lookup"><span data-stu-id="e3268-240">Next, check that you can access web and file share resources on APP1 from CLIENT1.</span></span>
  
1. <span data-ttu-id="e3268-241">En el panel de árbol del Administrador del servidor, haga clic en **Servidor Local**.</span><span class="sxs-lookup"><span data-stu-id="e3268-241">In Server Manager, in the tree pane, click **Local Server**.</span></span>
    
2. <span data-ttu-id="e3268-242">En **Propiedades de CLIENT1**, haga clic en la opción **Activada** al lado de **Configuración de seguridad mejorada de IE**.</span><span class="sxs-lookup"><span data-stu-id="e3268-242">In **Properties for CLIENT1**, click **On** next to **IE Enhanced Security Configuration**.</span></span>
    
3. <span data-ttu-id="e3268-243">En **Configuración de seguridad mejorada de Internet Explorer**, haga clic en **Desactivada** para **Administradores** y **Usuarios** y luego, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="e3268-243">In **Internet Explorer Enhanced Security Configuration**, click **Off** for **Administrators** and **Users**, and then click **OK**.</span></span>
    
4. <span data-ttu-id="e3268-244">En la pantalla Inicio, haga clic en **Internet Explorer** y, después, en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="e3268-244">From the Start screen, click **Internet Explorer**, and then click **OK**.</span></span>
    
5. <span data-ttu-id="e3268-p127">En la barra de direcciones, escriba **http:\//app1.corp.contoso.com/** y, después, presione ENTRAR. Verá la página web predeterminada de Internet Information Services para APP1.</span><span class="sxs-lookup"><span data-stu-id="e3268-p127">In the Address bar, type **http:\//app1.corp.contoso.com/**, and then press ENTER. You should see the default Internet Information Services web page for APP1.</span></span>
    
6. <span data-ttu-id="e3268-247">En la barra de tareas del escritorio, haga clic en el icono del Explorador de archivos.</span><span class="sxs-lookup"><span data-stu-id="e3268-247">From the desktop taskbar, click the File Explorer icon.</span></span>
    
7. <span data-ttu-id="e3268-p128">En la barra de direcciones, escriba **\\\\app1\\Files** y luego presione ENTRAR. Debería ver una ventana de carpeta con el contenido de la carpeta compartida Archivos.</span><span class="sxs-lookup"><span data-stu-id="e3268-p128">In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.</span></span>
    
8. <span data-ttu-id="e3268-p129">En la ventana de la carpeta compartida **Archivos**, haga doble clic en el archivo **Example.txt**. Debería ver el contenido del archivo Example.txt.</span><span class="sxs-lookup"><span data-stu-id="e3268-p129">In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.</span></span>
    
9. <span data-ttu-id="e3268-252">Cierre las ventanas de **Example.txt: Bloc de notas** y de la carpeta compartida **Archivos**.</span><span class="sxs-lookup"><span data-stu-id="e3268-252">Close the **example.txt - Notepad** and the **Files** shared folder windows.</span></span>
    
<span data-ttu-id="e3268-253">Esta es la configuración final.</span><span class="sxs-lookup"><span data-stu-id="e3268-253">This is your final configuration.</span></span>
  
![Paso 4 de la configuración básica en Azure con la máquina virtual CLIENT1](media/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
<span data-ttu-id="e3268-255">La configuración básica de Azure está preparada para desarrollar y probar aplicaciones o para crear entornos de prueba adicionales.</span><span class="sxs-lookup"><span data-stu-id="e3268-255">Your Base Configuration in Azure is now ready for application development and testing or for building additional test environments.</span></span> 
  
> [!TIP]
> <span data-ttu-id="e3268-256">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos de la pila de la guía del entorno de pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="e3268-256">Click [here](http://aka.ms/catlgstack) for a visual map to all of the articles in the Office 365 Test Lab Guide stack.</span></span>
  
<span data-ttu-id="e3268-257"><a name="mincost"> </a></span><span class="sxs-lookup"><span data-stu-id="e3268-257"><a name="mincost"> </a></span></span>
## <a name="minimizing-the-costs-of-test-environment-virtual-machines-in-azure"></a><span data-ttu-id="e3268-258">Minimizar los costos del entorno de pruebas de máquinas virtuales en Azure</span><span class="sxs-lookup"><span data-stu-id="e3268-258">Minimizing the costs of test environment virtual machines in Azure</span></span>

<span data-ttu-id="e3268-259">Para minimizar el costo de ejecutar máquinas virtuales de entorno de pruebas, puede realizar una de las siguientes acciones:</span><span class="sxs-lookup"><span data-stu-id="e3268-259">To minimize the cost of running the test environment virtual machines, you can do one of the following:</span></span>
  
- <span data-ttu-id="e3268-p130">Crear el entorno de pruebas y realizar las pruebas necesarias y la demostración lo más rápidamente posible. Cuando haya terminado, elimine el grupo de recursos del entorno de pruebas.</span><span class="sxs-lookup"><span data-stu-id="e3268-p130">Create the test environment and perform your needed testing and demonstration as quickly as possible. When complete, delete the resource group for the test environment.</span></span>
    
- <span data-ttu-id="e3268-262">Ponga las máquinas virtuales del entorno de pruebas virtual en un estado desasignado.</span><span class="sxs-lookup"><span data-stu-id="e3268-262">Shut down your test environment virtual machines into a deallocated state.</span></span>
    
<span data-ttu-id="e3268-263">Para apagar las máquinas virtuales con Azure PowerShell, rellene el nombre del grupo de recursos y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="e3268-263">To shut down the virtual machines with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Stop-AzVM -ResourceGroupName $rgName -Name "CLIENT1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "APP1" -Force
Stop-AzVM -ResourceGroupName $rgName -Name "DC1" -Force
```

<span data-ttu-id="e3268-264">Para asegurarse de que las máquinas virtuales funcionan correctamente al iniciarlas todas desde el estado Detenido (Desasignado), debe iniciarlas en el orden siguiente:</span><span class="sxs-lookup"><span data-stu-id="e3268-264">To ensure that your virtual machines work properly when starting all of them from the Stopped (Deallocated) state, you should start them in the following order:</span></span>
  
1. <span data-ttu-id="e3268-265">DC1</span><span class="sxs-lookup"><span data-stu-id="e3268-265">DC1</span></span>
2. <span data-ttu-id="e3268-266">APP1</span><span class="sxs-lookup"><span data-stu-id="e3268-266">APP1</span></span>
3. <span data-ttu-id="e3268-267">CLIENT1</span><span class="sxs-lookup"><span data-stu-id="e3268-267">CLIENT1</span></span>
    
<span data-ttu-id="e3268-268">Para iniciar las máquinas virtuales en orden con Azure PowerShell, indique el nombre del grupo de recursos y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="e3268-268">To start the virtual machines in order with Azure PowerShell, fill in the resource group name and run these commands.</span></span>
  
```
$rgName="<your resource group name>"
Start-AzVM -ResourceGroupName $rgName -Name "DC1"
Start-AzVM -ResourceGroupName $rgName -Name "APP1"
Start-AzVM -ResourceGroupName $rgName -Name "CLIENT1"
```

## <a name="see-also"></a><span data-ttu-id="e3268-269">Vea también</span><span class="sxs-lookup"><span data-stu-id="e3268-269">See Also</span></span>

- [<span data-ttu-id="e3268-270">Entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="e3268-270">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
- [<span data-ttu-id="e3268-271">Sincronización de directorios (DirSync) para el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="e3268-271">DirSync for your Office 365 dev/test environment</span></span>](dirsync-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="e3268-272">Seguridad de Cloud App para su entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="e3268-272">Cloud App Security for your Office 365 dev/test environment</span></span>](cloud-app-security-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="e3268-273">Protección contra amenazas avanzada en el entorno de desarrollo y prueba de Office 365</span><span class="sxs-lookup"><span data-stu-id="e3268-273">Advanced Threat Protection for your Office 365 dev/test environment</span></span>](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
- [<span data-ttu-id="e3268-274">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="e3268-274">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
