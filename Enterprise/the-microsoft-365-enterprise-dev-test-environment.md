---
title: Entorno de desarrollo y prueba de Microsoft 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: 'Resumen: Use esta guía del laboratorio de pruebas para crear un entorno de desarrollo y prueba que incluya Office 365 E5, Enterprise Mobility + Security (EMS) E5 y un equipo con Windows 10 Enterprise.'
ms.openlocfilehash: 03fa8e0a4e8d90fcb834eeb2491d3dd39b67ff05
ms.sourcegitcommit: 771f227d3049498fcbd7cfbeaf649e3d77e73c86
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "19178652"
---
# <a name="the-microsoft-365-enterprise-devtest-environment"></a><span data-ttu-id="f72cc-103">Entorno de desarrollo y prueba de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="f72cc-103">The Microsoft 365 Enterprise dev/test environment</span></span>

 <span data-ttu-id="f72cc-104">**Resumen:** Use esta guía del laboratorio de pruebas para crear un entorno de desarrollo y prueba que incluya Office 365 E5, Enterprise Mobility + Security (EMS) E5 y un equipo con Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="f72cc-104">**Summary:** Use this Test Lab Guide to create a dev/test environment that includes Office 365 E5, Enterprise Mobility + Security (EMS) E5, and a computer running Windows 10 Enterprise.</span></span>
  
<span data-ttu-id="f72cc-105">En este artículo se ofrecen instrucciones paso a paso para crear un entorno simplificado para probar las características y funcionalidades de [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="f72cc-105">This article provides you with step-by-step instructions to create a simplified environment to test the features and functionality of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="phase-1-create-your-office-365-e5-subscription"></a><span data-ttu-id="f72cc-106">Fase 1: Crear la suscripción de Office 365 E5</span><span class="sxs-lookup"><span data-stu-id="f72cc-106">Phase 1: Create your Office 365 dev/test environment</span></span>

<span data-ttu-id="f72cc-107">Siga los pasos los pasos 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md) para crear un entorno de desarrollo y prueba ligero de Office 365, tal y como se muestra en la figura 1.</span><span class="sxs-lookup"><span data-stu-id="f72cc-107">Follow the steps in Phase 2 and Phase 3 of the [Office 365 dev/test environment](office-365-dev-test-environment.md) to create a lightweight Office 365 dev/test environment, as shown in Figure 1.</span></span>
  
<span data-ttu-id="f72cc-108">**Figura 1: Suscripción de Office 365 E5 con las cuentas de usuario y de espacio empresarial de Azure Active Directory (AD)**</span><span class="sxs-lookup"><span data-stu-id="f72cc-108">**Figure 1: Your Office 365 E5 subscription with its Azure Active Directory (AD) tenant and user accounts**</span></span>

![Fase 1 del entorno de desarrollo y prueba de Microsoft 3656 Enterprise](images/65bb027b-fb59-46eb-aec2-38c0af425168.png)

> [!NOTE]
> <span data-ttu-id="f72cc-p101">La duración de la suscripción de prueba de Office 365 E5 es de 30 días, que puede ampliarse fácilmente a 60 días. Si quiere usar un entorno de desarrollo y prueba permanente, cree una suscripción de pago con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p101">The Dynamics 365 Plan 1 Enterprise Edition trial subscription is 30 days. You can easily extend the trail subscription for another 30 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
## <a name="phase-2-add-ems"></a><span data-ttu-id="f72cc-112">Fase 2: Agregar EMS</span><span class="sxs-lookup"><span data-stu-id="f72cc-112">Phase 2: Add EMS</span></span>

<span data-ttu-id="f72cc-113">En esta fase se inscribe en la suscripción de evaluación de EMS E5 y la agrega a la misma organización de la suscripción de evaluación de Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="f72cc-113">In this phase, you sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
<span data-ttu-id="f72cc-114">En primer lugar, agregue la suscripción de evaluación de EMS E5 y asigne una licencia EMS a su cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="f72cc-114">First, add the EMS E5 trial subscription and assign an EMS license to your global administrator account.</span></span>
  
1. <span data-ttu-id="f72cc-p102">Con una instancia privada de un explorador de Internet, inicie sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).</span><span class="sxs-lookup"><span data-stu-id="f72cc-p102">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="f72cc-117">Haga clic en el icono **Administrador**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-117">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="f72cc-118">En la pestaña **Centro de administración de Office** del explorador, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-118">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="f72cc-p103">En la página **Servicios de compra**, busque el elemento **Enterprise Mobility + Security E5**. Mantenga el puntero del mouse sobre ese elemento y haga clic en **Iniciar prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p103">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="f72cc-121">En la página **Confirmar pedido**, haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-121">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="f72cc-122">En la página **Recibo del pedido**, haga clic en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-122">On the **Order receipt** page, click **Continue**.</span></span>
    
7. <span data-ttu-id="f72cc-123">En el panel de navegación izquierdo de la pestaña **Centro de administración de Office 365** del explorador, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-123">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
8. <span data-ttu-id="f72cc-124">Haga clic en la cuenta de administrador global y, después, en **Editar** para **Licencias de productos**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-124">Click your global administrator account, and then click Edit for Product licenses.</span></span>
    
9. <span data-ttu-id="f72cc-125">En el panel **Licencias de productos**, cambie la licencia del producto de **Enterprise Mobility + Security E5** a **Activada**, seleccione **Guardar** y, después, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="f72cc-125">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
> [!NOTE]
> <span data-ttu-id="f72cc-p104">La suscripción de prueba a Enterprise Mobility + Security E5 tiene una duración de 90 días. Si quiere usar un entorno de pruebas y desarrollo permanente, cree una nueva suscripción de pago con un número reducido de licencias.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p104">The Enterprise Mobility + Security E5 trial subscription is 90 days. For a permanent dev/test environment, create a new paid subscription with a small number of licenses.</span></span> 
  
 <span data-ttu-id="f72cc-128">***Si ha completado la fase 3 del*** [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md), repita los pasos 8 y 9 del procedimiento anterior para las demás cuentas (usuario 2, usuario 3, usuario 4 y usuario 5).</span><span class="sxs-lookup"><span data-stu-id="f72cc-128">***If you completed Phase 3 of the*** [Office 365 dev/test environment](office-365-dev-test-environment.md), repeat steps 8 and 9 of the previous procedure for all of your other accounts (User 2, User 3, User 4, and User 5).</span></span>
  
<span data-ttu-id="f72cc-129">Ahora su entorno de desarrollo y prueba tiene:</span><span class="sxs-lookup"><span data-stu-id="f72cc-129">Your Office 365 dev/test environment now has:</span></span>
  
- <span data-ttu-id="f72cc-130">Suscripciones de evaluación de Office 365 E5 Enterprise y EMS E5 que comparten el mismo espacio empresarial de AD Azure con la lista de cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="f72cc-130">Office 365 E5 Enterprise and EMS trial subscriptions sharing the same organization and the same Azure AD tenant with your list of user accounts.</span></span>
- <span data-ttu-id="f72cc-131">Todas las cuentas de usuario adecuadas (ya sea solo la cuenta de administrador global o las cinco cuentas de usuario) están habilitadas para usar Office 365 E5 y EMS E5.</span><span class="sxs-lookup"><span data-stu-id="f72cc-131">All your appropriate user accounts (either just the global administrator or all five user accounts) are enabled to use Office 365 E5 and EMS E5.</span></span>
    
<span data-ttu-id="f72cc-132">La figura 2 muestra la configuración resultante, que agrega EMS.</span><span class="sxs-lookup"><span data-stu-id="f72cc-132">Figure 2 shows your resulting configuration, which adds EMS.</span></span>
  
<span data-ttu-id="f72cc-133">**Figura 2: Adición de la suscripción de evaluación de EMS**</span><span class="sxs-lookup"><span data-stu-id="f72cc-133">**Figure 2: Adding the EMS trial subscription**</span></span>

![Fase 2 del entorno de desarrollo y prueba Microsoft 3656 Enterprise](images/8a01a483-3de2-41f3-a845-141c7edd0cb0.png)
  
## <a name="phase-3-create-a-windows-10-enterprise-computer"></a><span data-ttu-id="f72cc-135">Fase 3: Crear un equipo con Windows 10 Enterprise</span><span class="sxs-lookup"><span data-stu-id="f72cc-135">Phase 3: Create a Windows 10 Enterprise computer</span></span>

<span data-ttu-id="f72cc-136">En esta fase se crea un equipo independiente con Windows 10 Enterprise.</span><span class="sxs-lookup"><span data-stu-id="f72cc-136">In this phase, you create a standalone computer running Windows 10 Enterprise.</span></span>
  
### <a name="physical-computer"></a><span data-ttu-id="f72cc-137">Equipo físico</span><span class="sxs-lookup"><span data-stu-id="f72cc-137">Physical computer</span></span>

<span data-ttu-id="f72cc-p105">Obtenga un equipo personal e instale Windows 10 Enterprise en él. Puede descargar la versión de evaluación de Windows 10 Enterprise [aquí](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="f72cc-p105">Obtain a personal computer and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine"></a><span data-ttu-id="f72cc-140">Máquina virtual</span><span class="sxs-lookup"><span data-stu-id="f72cc-140">Virtual machine</span></span>

<span data-ttu-id="f72cc-p106">Cree una máquina virtual con el hipervisor que prefiera e instale Windows 10 Enterprise en ella. Puede descargar la versión de evaluación de Windows 10 Enterprise [aquí](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span><span class="sxs-lookup"><span data-stu-id="f72cc-p106">Create a virtual machine using the hypervisor of your choice and install Windows 10 Enterprise on it. You can download the Windows 10 Enterprise trial [here](https://www.microsoft.com/evalcenter/evaluate-windows-10-enterprise).</span></span>
  
### <a name="virtual-machine-in-azure"></a><span data-ttu-id="f72cc-143">Máquina virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="f72cc-143">Virtual machine size in Azure</span></span>

<span data-ttu-id="f72cc-p107">Para crear una máquina virtual con Windows 10 en Microsoft Azure ***necesita tener una suscripción basada en Visual Studio***, que tiene acceso a la imagen de Windows 10 Enterprise. Otros tipos de suscripciones de Azure, como las suscripciones de prueba y suscripciones de pago, no tienen acceso a esta imagen. Para obtener la información más reciente, vea [Usar el cliente de Windows en Azure para escenarios de desarrollo y pruebas](https://docs.microsoft.com/azure/virtual-machines/windows/client-images).</span><span class="sxs-lookup"><span data-stu-id="f72cc-p107">To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image. For the latest information, see [Use Windows client in Azure for dev/test scenarios](https://docs.microsoft.com/azure/virtual-machines/windows/client-images).</span></span>
  
> [!NOTE]
> <span data-ttu-id="f72cc-p108">Los siguientes conjuntos de comandos usan la versión más reciente de Azure PowerShell. Vea [Introducción a los cmdlets de Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). Estos conjuntos de comandos compilan una máquina virtual con Windows 10 Enterprise llamada WIN10 y toda la infraestructura necesaria, que incluye un grupo de recursos, una cuenta de almacenamiento y una red virtual. Si ya está familiarizado con los servicios de infraestructura de Azure, adapte estas instrucciones para que se ajusten a la infraestructura implementada actualmente.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p108">The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). These command sets build a Windows 10 Enterprise virtual machine named WIN10 and all of its required infrastructure, including a resource group, a storage account, and a virtual network. If you are already familiar with Azure infrastructure services, please adapt these instructions to suit your currently deployed infrastructure.</span></span> 
  
<span data-ttu-id="f72cc-151">En primer lugar, abra un símbolo del sistema de Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f72cc-151">First, start a Microsoft PowerShell prompt.</span></span>
  
<span data-ttu-id="f72cc-152">Inicie sesión en su cuenta de Azure con el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="f72cc-152">Sign in to your Azure account with the following command.</span></span>
  
```
Login-AzureRMAccount
```

<span data-ttu-id="f72cc-153">Obtenga su nombre de suscripción mediante el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="f72cc-153">Get your subscription name using the following command.</span></span>
  
```
Get-AzureRMSubscription | Sort Name | Select Name
```

<span data-ttu-id="f72cc-p109">Configure su suscripción de Azure. Cambie todo el contenido entrecomillado, incluidos los caracteres \< y >, por los nombres correctos.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p109">Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.</span></span>
  
```
$subscr="<subscription name>"
Get-AzureRmSubscription -SubscriptionName $subscr | Select-AzureRmSubscription
```

<span data-ttu-id="f72cc-p110">Después, cree un nuevo grupo de recursos. Para determinar un nombre único de grupo de recursos, use este comando a fin de enumerar los grupos de recursos existentes.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p110">Next, create a new resource group. To determine a unique resource group name, use this command to list your existing resource groups.</span></span>
  
```
Get-AzureRMResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

<span data-ttu-id="f72cc-p111">Cree el nuevo grupo de recursos con estos comandos. Reemplace todo el contenido entrecomillado, incluidos los caracteres \< y > , por los nombres correctos.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p111">Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.</span></span>
  
```
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzureRMResourceGroup -Name $rgName -Location $locName
```

<span data-ttu-id="f72cc-p112">Después, cree una red virtual y la máquina virtual WIN10 con estos comandos. Cuando se le pida, indique el nombre y contraseña de la cuenta de administrador local para WIN10 y guárdelos en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p112">Next, you create a new virtual network and the WIN10 virtual machine with these commands. When prompted, provide the name and password of the local administrator account for WIN10 and store these in a secure location.</span></span>
  
```
$corpnetSubnet=New-AzureRMVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzureRMVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzureRMNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzureRMVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzureRMNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzureRMVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$pip=New-AzureRMPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzureRMNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzureRMVMConfig -VMName WIN10 -VMSize Standard_D1_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzureRMVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzureRMVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzureRMVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzureRmVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "StandardLRS"
New-AzureRMVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-4-join-your-windows-10-computer-to-azure-ad"></a><span data-ttu-id="f72cc-162">Fase 4: Unir el equipo con Windows 10 a Azure AD</span><span class="sxs-lookup"><span data-stu-id="f72cc-162">Phase 4: Join your Windows 10 computer to Azure AD</span></span>

<span data-ttu-id="f72cc-163">Después de crear la máquina física o virtual con Windows 10 Enterprise, inicie sesión con una cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="f72cc-163">After the physical or virtual machine with Windows 10 Enterprise is created, sign in with a local administrator account.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f72cc-p113">En una máquina virtual en Azure, conéctese con [estas instrucciones](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Inicie sesión con las credenciales de la cuenta de administrador local.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p113">For a virtual machine in Azure, connect to it using [these instructions](https://docs.microsoft.com/azure/virtual-machines/windows/connect-logon). Sign in with the credentials of the local administrator account.</span></span> 
  
<span data-ttu-id="f72cc-166">Después, una el equipo WIN10 al espacio empresarial de Azure AD de las suscripciones de Office 365 y EMS.</span><span class="sxs-lookup"><span data-stu-id="f72cc-166">Next, join the WIN10 computer to the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="f72cc-167">En el escritorio del equipo WIN10, haga clic en **Inicio > Configuración > Cuentas > Obtener acceso a trabajo o escuela > Conectarse**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-167">At the desktop of the WIN10 computer, click **Start > Settings > Accounts > Access work or school > Connect**.</span></span>
    
2. <span data-ttu-id="f72cc-168">En el cuadro de diálogo **Set up a work or school account** (Configurar una cuenta profesional o educativa), haga clic en **Join this device to Azure Active Directory** (Unir este dispositivo a Azure Active Directory).</span><span class="sxs-lookup"><span data-stu-id="f72cc-168">In the **Set up a work or school account** dialog box, click **Join this device to Azure Active Directory**.</span></span>
    
3. <span data-ttu-id="f72cc-169">En **Cuenta profesional o educativa**, escriba el nombre de la cuenta de administrador global de la suscripción de Office 365 y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-169">In **Work or school account**, type the global administrator account name of your Office 365 subscription, and then click **Next**.</span></span>
    
4. <span data-ttu-id="f72cc-170">En **Escribir contraseña**, escriba la contraseña de la cuenta de administrador global y luego haga clic en **Iniciar sesión**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-170">In **Enter password**, type the password for your global administrator account, and then click **Sign in**.</span></span>
    
5. <span data-ttu-id="f72cc-171">Cuando se le pida que confirme que es su organización, haga clic en **Unir** y luego en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-171">When prompted to make sure this is your organization, click **Join**, and then click **Done**.</span></span>
    
6. <span data-ttu-id="f72cc-172">Cierre la ventana de configuración.</span><span class="sxs-lookup"><span data-stu-id="f72cc-172">Close the Help window.</span></span>
    
<span data-ttu-id="f72cc-173">Después, instale Office 365 ProPlus en el equipo con Windows 10.</span><span class="sxs-lookup"><span data-stu-id="f72cc-173">Next, install Office 365 ProPlus on the WIN10 computer.</span></span>
  
1. <span data-ttu-id="f72cc-p114">Abra el explorador Microsoft Edge e inicie sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global. Para obtener ayuda, vea [Dónde iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="f72cc-p114">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="f72cc-176">En la pestaña **Inicio de Microsoft Office**, haga clic en **Instalar Office 2016**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-176">On the **Microsoft Office Home** tab, click **Install Office 2016**.</span></span>
    
3. <span data-ttu-id="f72cc-177">Cuando se le pregunte qué hacer, haga clic en **Ejecutar** y luego en **Sí** para **Control de cuentas de usuario**.</span><span class="sxs-lookup"><span data-stu-id="f72cc-177">When prompted with what to do, click **Run**, and then click **Yes** for **User Account Control**.</span></span>
    
4. <span data-ttu-id="f72cc-p115">Espere hasta que se complete la instalación de Office. Cuando vea **Ya está listo**, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="f72cc-p115">Wait for Office to complete its installation. When you see **You're all set!**, click **Close** twice.</span></span>
    
<span data-ttu-id="f72cc-180">En la ilustración 3, se muestra el entorno resultante con el equipo con Windows 10 que:</span><span class="sxs-lookup"><span data-stu-id="f72cc-180">Figure 3 shows your resulting environment, which includes the WIN10 computer that has:</span></span>

- <span data-ttu-id="f72cc-181">Se unió al espacio empresarial de Azure AD de sus suscripciones de Office 365 y EMS.</span><span class="sxs-lookup"><span data-stu-id="f72cc-181">Joined the Azure AD tenant of your Office 365 and EMS subscriptions.</span></span>
- <span data-ttu-id="f72cc-182">Se inscribió como un dispositivo de Azure AD en Intune (EMS).</span><span class="sxs-lookup"><span data-stu-id="f72cc-182">Enrolled as an Azure AD device in Intune (EMS).</span></span>
- <span data-ttu-id="f72cc-183">Tiene instalado Office 365 ProPlus.</span><span class="sxs-lookup"><span data-stu-id="f72cc-183">Has Office 365 ProPlus installed.</span></span>
  
<span data-ttu-id="f72cc-184">**Ilustración 3: La configuración final del entorno de desarrollo y pruebas de Microsoft 365**</span><span class="sxs-lookup"><span data-stu-id="f72cc-184">**Figure 3: The final configuration of the Microsoft 365 dev/test environment**</span></span>

![Fase 4 del entorno de desarrollo y pruebas de Microsoft 365 Enterprise](images/20680f6a-f77e-4333-aaa9-f7cf5e4b0d03.png)
  
<span data-ttu-id="f72cc-186">Ahora está preparado para experimentar con otras características de [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span><span class="sxs-lookup"><span data-stu-id="f72cc-186">You are now ready to experiment with additional features of [Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise).</span></span>
  
## <a name="next-steps"></a><span data-ttu-id="f72cc-187">Siguientes pasos</span><span class="sxs-lookup"><span data-stu-id="f72cc-187">Next steps</span></span>

<span data-ttu-id="f72cc-188">Use estos artículos adicionales para explorar las características de Microsoft 365 Enterprise:</span><span class="sxs-lookup"><span data-stu-id="f72cc-188">Use these additional articles to explore features of Microsoft 365 Enterprise:</span></span>
  
- [<span data-ttu-id="f72cc-189">Agregar directivas de administración de aplicaciones móviles (MAM)</span><span class="sxs-lookup"><span data-stu-id="f72cc-189">Add mobile application management (MAM) policies</span></span>](https://technet.microsoft.com/library/mt764059.aspx)
    
- <span data-ttu-id="f72cc-190">[Inscribir dispositivos iOS y Android](https://technet.microsoft.com/library/mt743077.aspx)</span><span class="sxs-lookup"><span data-stu-id="f72cc-190">[Intune/EMS:](https://technet.microsoft.com/library/mt743077.aspx) Manage iOS and Android devices.</span></span>
    
- <span data-ttu-id="f72cc-191">[Configure and test Advanced Security Management](https://technet.microsoft.com/library/mt757250.aspx) (Configurar y probar la administración de seguridad avanzada)</span><span class="sxs-lookup"><span data-stu-id="f72cc-191">[Configure and test Advanced Security Management](https://technet.microsoft.com/library/mt757250.aspx)</span></span>
    
- [<span data-ttu-id="f72cc-192">Configurar y probar Protección contra amenazas avanzada</span><span class="sxs-lookup"><span data-stu-id="f72cc-192">Configure and test Advanced Threat Protection</span></span>](https://technet.microsoft.com/library/mt490479.aspx)
    
## <a name="see-also"></a><span data-ttu-id="f72cc-193">Vea también</span><span class="sxs-lookup"><span data-stu-id="f72cc-193">See also</span></span>

- [<span data-ttu-id="f72cc-194">Documentación y recursos de Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="f72cc-194">Microsoft 365 Enterprise documentation and resources</span></span>](https://docs.microsoft.com/microsoft-365-enterprise/)
- [<span data-ttu-id="f72cc-195">Implementar Microsoft 365 Enterprise</span><span class="sxs-lookup"><span data-stu-id="f72cc-195">Deploy Microsoft 365 Enterprise</span></span>](https://docs.microsoft.com/microsoft-365/enterprise/deploy-microsoft-365-enterprise)
- [<span data-ttu-id="f72cc-196">Entorno de desarrollo y prueba de One Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="f72cc-196">The One Microsoft Cloud dev/test environment</span></span>](the-one-microsoft-cloud-dev-test-environment.md)
- [<span data-ttu-id="f72cc-197">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="f72cc-197">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
