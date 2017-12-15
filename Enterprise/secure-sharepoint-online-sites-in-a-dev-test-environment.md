---
title: Sitios de SharePoint Online seguros en un entorno de pruebas y desarrollo
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.custom:
- DecEntMigration
- Strat_O365_Enterprise
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: "Resumen: Crear sitios de equipo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en un entorno de pruebas y desarrollo."
ms.openlocfilehash: 17abee7a293996194a097693607b4b4d9c117046
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="c473a-103">Sitios de SharePoint Online seguros en un entorno de pruebas y desarrollo</span><span class="sxs-lookup"><span data-stu-id="c473a-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="c473a-104">**Resumen:** Crear sitios de equipo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en un entorno de pruebas y desarrollo.</span><span class="sxs-lookup"><span data-stu-id="c473a-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="c473a-105">Este artículo proporciona instrucciones paso a paso para crear un entorno de pruebas y desarrollo que incluye los cuatro tipos diferentes de sitios SharePoint Online de equipo para la solución de [archivos y los sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md) .</span><span class="sxs-lookup"><span data-stu-id="c473a-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![Los cuatro sitios de grupo del entorno de pruebas y desarrollo de SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="c473a-107">Utilizar este entorno de desarrollo y prueba para experimentar con los comportamientos de protección de la información y ajustar la configuración para sus necesidades específicas antes de implementar SharePoint Online sitios de equipo de producción.</span><span class="sxs-lookup"><span data-stu-id="c473a-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="c473a-108">Fase 1: Crear el entorno de pruebas y desarrollo</span><span class="sxs-lookup"><span data-stu-id="c473a-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="c473a-109">En esta fase, se puede obtener las suscripciones de prueba de Office 365 + seguridad y movilidad en la empresa de una organización ficticia.</span><span class="sxs-lookup"><span data-stu-id="c473a-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="c473a-110">En primer lugar, siga las instrucciones en la **fase 2** del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="c473a-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="c473a-111">A continuación, registrarse para la suscripción de prueba de EMS y agregarlo a la misma organización que su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="c473a-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="c473a-p101">Si es necesario, iniciar sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global de su suscripción de prueba. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c473a-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c473a-114">Haga clic en el mosaico de **Admin** .</span><span class="sxs-lookup"><span data-stu-id="c473a-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c473a-115">En la ficha del **Centro de administración de Office** en el explorador, en la exploración de la izquierda, haga clic en **de facturación > adquirir servicios**.</span><span class="sxs-lookup"><span data-stu-id="c473a-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="c473a-p102">En la página **Servicios de compra** , busque el elemento de **seguridad E5 + de movilidad en la empresa** . Sitúe el puntero del mouse sobre él y haga clic en **iniciar la versión de prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="c473a-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="c473a-118">En la página **confirmar su pedido** , haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="c473a-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="c473a-119">En la página de **confirmación del pedido** , haga clic en **continuar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="c473a-120">A continuación, habilitar la movilidad en la empresa + licencia E5 de seguridad para la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="c473a-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="c473a-121">En la ficha del **Centro de administración de Office 365** en el explorador, en la exploración de la izquierda, haga clic en **los usuarios > usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="c473a-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="c473a-122">Haga clic en la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.</span><span class="sxs-lookup"><span data-stu-id="c473a-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="c473a-123">En el panel de **licencias de producto** , activar la licencia del producto de **movilidad en la empresa + seguridad E5** en **On**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="c473a-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="c473a-124">Fase 2: Crear y configurar los usuarios y grupos de Azure de Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="c473a-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="c473a-125">En esta fase, crear y configurar los usuarios y grupos de AD Azure para su organización ficticia.</span><span class="sxs-lookup"><span data-stu-id="c473a-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="c473a-126">Primero, cree un conjunto de grupos de una organización típica con el portal de Azure.</span><span class="sxs-lookup"><span data-stu-id="c473a-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="c473a-127">Crear una ficha independiente en el explorador y, a continuación, vaya al portal de Azure en [https://portal.azure.com](https://portal.azure.com). Si es necesario, inicie sesión con las credenciales de la cuenta de administrador global para la suscripción de prueba de Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="c473a-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="c473a-128">En el portal de Azure, haga clic en **Azure Active Directory > usuarios y grupos > grupos de todos los**.</span><span class="sxs-lookup"><span data-stu-id="c473a-128">In the Azure portal, click **Azure Active Directory > Users and groups > All groups**.</span></span>
    
3. <span data-ttu-id="c473a-129">En la hoja de **todos los grupos** , haga clic en **+ nuevo grupo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-129">On the **All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="c473a-130">En la hoja de **grupo** :</span><span class="sxs-lookup"><span data-stu-id="c473a-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="c473a-131">Tipo **C-Suite** en **nombre**.</span><span class="sxs-lookup"><span data-stu-id="c473a-131">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="c473a-132">Seleccione **asignados** en la **suscripción**.</span><span class="sxs-lookup"><span data-stu-id="c473a-132">Select **Assigned** in **Membership**.</span></span>
    
  - <span data-ttu-id="c473a-133">Haga clic en **Sí** para **Habilitar Office características**.</span><span class="sxs-lookup"><span data-stu-id="c473a-133">Click **Yes** for **Enable Office features**.</span></span>
    
5. <span data-ttu-id="c473a-134">Haga clic en **crear**y, a continuación, cierre la hoja de **grupo** .</span><span class="sxs-lookup"><span data-stu-id="c473a-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="c473a-135">Repita los pasos 3 a 5 para los nombres de grupo siguientes:</span><span class="sxs-lookup"><span data-stu-id="c473a-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="c473a-136">Personal de TI</span><span class="sxs-lookup"><span data-stu-id="c473a-136">IT staff</span></span>
    
  - <span data-ttu-id="c473a-137">Personal de investigación</span><span class="sxs-lookup"><span data-stu-id="c473a-137">Research staff</span></span>
    
  - <span data-ttu-id="c473a-138">Personal estatutario</span><span class="sxs-lookup"><span data-stu-id="c473a-138">Regular staff</span></span>
    
  - <span data-ttu-id="c473a-139">Personal de marketing</span><span class="sxs-lookup"><span data-stu-id="c473a-139">Marketing staff</span></span>
    
  - <span data-ttu-id="c473a-140">Personal de ventas</span><span class="sxs-lookup"><span data-stu-id="c473a-140">Sales staff</span></span>
    
7. <span data-ttu-id="c473a-141">Mantener la ficha portal Azure en su explorador se abre.</span><span class="sxs-lookup"><span data-stu-id="c473a-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="c473a-142">A continuación, configure el licenciamiento automático para que los miembros de los grupos se asignan automáticamente licencias para sus suscripciones a Office 365 y EMS.</span><span class="sxs-lookup"><span data-stu-id="c473a-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="c473a-143">En el portal de Azure, haga clic en **Azure Active Directory > licencias > todos los productos**.</span><span class="sxs-lookup"><span data-stu-id="c473a-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="c473a-144">En la lista, seleccione **seguridad E5 + de movilidad en la empresa** y **Office 365 Enterprise E5**y, a continuación, haga clic en **asignar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="c473a-145">En la hoja **asignar licencias** , haga clic en **usuarios y grupos**.</span><span class="sxs-lookup"><span data-stu-id="c473a-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="c473a-146">En la lista de grupos, seleccione lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c473a-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="c473a-147">C-Suite</span><span class="sxs-lookup"><span data-stu-id="c473a-147">C-Suite</span></span>
    
  - <span data-ttu-id="c473a-148">Personal de TI</span><span class="sxs-lookup"><span data-stu-id="c473a-148">IT staff</span></span>
    
  - <span data-ttu-id="c473a-149">Personal de investigación</span><span class="sxs-lookup"><span data-stu-id="c473a-149">Research staff</span></span>
    
  - <span data-ttu-id="c473a-150">Personal estatutario</span><span class="sxs-lookup"><span data-stu-id="c473a-150">Regular staff</span></span>
    
  - <span data-ttu-id="c473a-151">Personal de marketing</span><span class="sxs-lookup"><span data-stu-id="c473a-151">Marketing staff</span></span>
    
  - <span data-ttu-id="c473a-152">Personal de ventas</span><span class="sxs-lookup"><span data-stu-id="c473a-152">Sales staff</span></span>
    
5. <span data-ttu-id="c473a-153">Haga clic en **Seleccionar**y, a continuación, haga clic en **asignar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="c473a-154">Cierre la ficha portal Azure en el explorador.</span><span class="sxs-lookup"><span data-stu-id="c473a-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="c473a-155">A continuación, puede [Conectar con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="c473a-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="c473a-156">Rellene el nombre de su organización, su ubicación y una contraseña común y, a continuación, ejecutar estos comandos desde el símbolo del sistema de PowerShell o el entorno de secuencias de comandos integrado (ISE) para crear cuentas de usuario y agregarlos a sus grupos:</span><span class="sxs-lookup"><span data-stu-id="c473a-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
```
$orgName="<organization name, such as contoso for the contoso.onmicrosoft.com trial subscription domain name>"
$location="<the ISO ALPHA2 country code, such as US for the United States>"
$commonPassword="<common password for all the new accounts>"

$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPassword

$groupName="C-Suite"
$userNames=@("CEO","CFO","CIO") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="IT staff"
$userNames=@("ITAdmin1","ITAdmin2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Research staff"
$userNames=@("Researcher1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Regular staff"
$userNames=@("Regular1", "Regular2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Marketing staff"
$userNames=@("Marketing1", "Marketing2") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
$groupName="Sales staff"
$userNames=@("SalesPerson1") 
$groupID=(Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
ForEach ($element in $userNames){ 
New-AzureADUser -DisplayName $element -PasswordProfile $PasswordProfile -UserPrincipalName ($element + "@" + $orgName + ".onmicrosoft.com") -AccountEnabled $true -MailNickName $element -UsageLocation $location 
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $element }).ObjectID -ObjectId $groupID
}
```

> [!NOTE]
> <span data-ttu-id="c473a-p103">El uso de una contraseña común aquí es para la automatización y la facilidad de configuración para un entorno de pruebas y desarrollo. Esto no es recomendable para las suscripciones de producción.</span><span class="sxs-lookup"><span data-stu-id="c473a-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="c473a-159">Siga estos pasos para comprobar que están basado en el grupo de licencias funciona correctamente.</span><span class="sxs-lookup"><span data-stu-id="c473a-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="c473a-160">Desde la ficha **Página de inicio de Microsoft Office** del explorador, haga clic en el mosaico de **Admin** .</span><span class="sxs-lookup"><span data-stu-id="c473a-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="c473a-161">Desde la ficha del **Centro de administración de Office** nueva del explorador, haga clic en **usuarios**.</span><span class="sxs-lookup"><span data-stu-id="c473a-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="c473a-162">En la lista de usuarios, haga clic en **Director ejecutivo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="c473a-163">En el panel que muestra las propiedades de la cuenta de usuario del **Director general** , compruebe que se ha asignado las licencias de **movilidad en la empresa + seguridad E5** y **E5 Enterprise de Office 365** (en **licencias de producto**).</span><span class="sxs-lookup"><span data-stu-id="c473a-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="c473a-164">Fase 3: Crear etiquetas de Office 365</span><span class="sxs-lookup"><span data-stu-id="c473a-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="c473a-165">En esta fase, crear las etiquetas para los diferentes niveles de seguridad para SharePoint Online carpetas de documentos del sitio de equipo.</span><span class="sxs-lookup"><span data-stu-id="c473a-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="c473a-p104">Si es necesario, utilice una instancia privada de su explorador de Internet e iniciar sesión en el portal de Office 365 con la cuenta de gestor global de su suscripción de prueba de Office 365 E5. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c473a-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c473a-168">Desde la ficha **Página de inicio de Microsoft Office** , haga clic en el mosaico de **Admin** .</span><span class="sxs-lookup"><span data-stu-id="c473a-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="c473a-169">Desde la ficha del **Centro de administración de Office** nueva del explorador, haga clic en **centros de administración > seguridad &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="c473a-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="c473a-170">Desde la nueva **Inicio - seguridad &amp; Compliance** ficha del explorador, haga clic en **las clasificaciones > etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="c473a-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="c473a-171">Desde el **Home > etiquetas** panel, haga clic en **crear una etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="c473a-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="c473a-172">En el panel de **la etiqueta de nombre** , escriba **Público interno**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c473a-173">En el panel de **configuración de etiquetas** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="c473a-174">En el panel **Revisar la configuración** , haga clic en **crear esta etiqueta**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="c473a-175">Repita los pasos 5 a 8 para estas etiquetas adicionales:</span><span class="sxs-lookup"><span data-stu-id="c473a-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="c473a-176">Privada</span><span class="sxs-lookup"><span data-stu-id="c473a-176">Private</span></span>
    
  - <span data-ttu-id="c473a-177">Confidencial</span><span class="sxs-lookup"><span data-stu-id="c473a-177">Sensitive</span></span>
    
  - <span data-ttu-id="c473a-178">Altamente confidencial</span><span class="sxs-lookup"><span data-stu-id="c473a-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="c473a-179">Desde el **Home > etiquetas** panel, haga clic en **etiquetas de publicar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="c473a-180">En el panel **etiquetas elegir publicar** , haga clic en **Elegir etiquetas para publicar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="c473a-181">En el panel **etiquetas de elegir** , haga clic en **Agregar** y seleccione todas las etiquetas de cuatro.</span><span class="sxs-lookup"><span data-stu-id="c473a-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="c473a-182">Haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="c473a-183">En el panel **etiquetas elegir publicar** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="c473a-184">En el panel **Elegir ubicaciones** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="c473a-185">En el panel **nombre de la directiva** , escriba **nombre de** **organización de ejemplo** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="c473a-186">En el panel **Revisar la configuración** , haga clic en **etiquetas de publicar**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="c473a-187">Fase 4: Crear sus sitios de equipo de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c473a-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="c473a-188">En esta fase, cree y configure los cuatro tipos de sitios de grupo de SharePoint Online para su organización de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="c473a-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="c473a-189">Sitio de grupo amplio de organización</span><span class="sxs-lookup"><span data-stu-id="c473a-189">Organization wide team site</span></span>

<span data-ttu-id="c473a-190">Para crear un sitio de equipo de SharePoint Online público previsto, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c473a-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="c473a-p105">Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 mediante su cuenta de administrador global. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c473a-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c473a-193">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c473a-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c473a-194">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="c473a-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c473a-195">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c473a-196">En **nombre del sitio**, escriba la **organización extensa**.</span><span class="sxs-lookup"><span data-stu-id="c473a-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="c473a-197">En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para toda la organización**.</span><span class="sxs-lookup"><span data-stu-id="c473a-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="c473a-198">En **la configuración de privacidad**, seleccione **pública - cualquier persona de la organización puede tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c473a-199">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="c473a-200">A continuación, configure la carpeta de documentos del sitio del grupo gran organización de la etiqueta interna pública.</span><span class="sxs-lookup"><span data-stu-id="c473a-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="c473a-201">En la ficha **Home de toda la organización** del explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="c473a-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c473a-202">Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c473a-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c473a-203">En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c473a-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c473a-204">En **Aplicar configuración de etiqueta**, seleccione **Público interno**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="c473a-205">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="c473a-205">Here is your resulting configuration.</span></span>
  
![Protección de nivel de línea base del sitio de grupo de SharePoint Online público de toda la organización.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="c473a-207">Sitio de grupo de proyecto 1</span><span class="sxs-lookup"><span data-stu-id="c473a-207">Project 1 team site</span></span>

<span data-ttu-id="c473a-208">Para crear un sitio de grupo de línea de base privado SharePoint Online para un proyecto dentro de la organización, realice lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c473a-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="c473a-p106">Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 mediante su cuenta de administrador global. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c473a-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c473a-211">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c473a-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c473a-212">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="c473a-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c473a-213">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c473a-214">En **nombre del sitio**, escriba **1 proyecto**.</span><span class="sxs-lookup"><span data-stu-id="c473a-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="c473a-215">En la **Descripción del sitio de equipo,** escriba **el sitio de SharePoint para el proyecto 1**.</span><span class="sxs-lookup"><span data-stu-id="c473a-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="c473a-216">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c473a-217">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="c473a-218">A continuación, configure la carpeta de documentos del sitio del grupo 1 de proyecto para la etiqueta privada.</span><span class="sxs-lookup"><span data-stu-id="c473a-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="c473a-219">En la ficha **proyecto 1 Inicio** del explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="c473a-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c473a-220">Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c473a-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c473a-221">En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c473a-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c473a-222">En **Aplicar configuración de etiqueta**, seleccione **privado**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="c473a-223">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="c473a-223">Here is your resulting configuration.</span></span>
  
![Protección de nivel de línea base del sitio de grupo de SharePoint Online privado Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="c473a-225">Sitio de grupo de campañas de marketing</span><span class="sxs-lookup"><span data-stu-id="c473a-225">Marketing campaigns team site</span></span>

<span data-ttu-id="c473a-226">Para crear un nivel sensible aislado SharePoint Online team sitio para recursos de campaña de marketing, realice lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c473a-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="c473a-p107">Mediante un explorador en el equipo local, inicie sesión en el portal de Office 365 mediante su cuenta de administrador global. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c473a-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c473a-229">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c473a-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c473a-230">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="c473a-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c473a-231">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c473a-232">En **nombre de sitio de equipo**, escriba **campañas de Marketing**.</span><span class="sxs-lookup"><span data-stu-id="c473a-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="c473a-233">En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para recursos de campaña de marketing (confidenciales)**.</span><span class="sxs-lookup"><span data-stu-id="c473a-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="c473a-234">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c473a-235">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="c473a-236">En la nueva ficha de **campañas de Marketing** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="c473a-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="c473a-237">En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.</span><span class="sxs-lookup"><span data-stu-id="c473a-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="c473a-238">En la ficha **permisos** de nuevo en el explorador, haga clic en **Configuración de solicitud de acceso**.</span><span class="sxs-lookup"><span data-stu-id="c473a-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="c473a-239">En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive las casillas de verificación **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **miembros de permitir invitar a otras personas al grupo de miembros del sitio** , escriba **ITAdmin1 @**\<su nombre de la organización >**. onmicrosoft.com** en **Enviar todas las solicitudes de acceso**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="c473a-240">En la lista, haga clic en **los miembros de las campañas de Marketing** .</span><span class="sxs-lookup"><span data-stu-id="c473a-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="c473a-241">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="c473a-242">En el cuadro de diálogo **Compartir** , escriba **personal de Marketing**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="c473a-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="c473a-243">Repita los pasos 14 y 15 para la cuenta de usuario de **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="c473a-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="c473a-244">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="c473a-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="c473a-245">En la lista, haga clic en **campañas de Marketing propietarios** .</span><span class="sxs-lookup"><span data-stu-id="c473a-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="c473a-246">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="c473a-247">En el cuadro de diálogo **Compartir** , escriba **personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="c473a-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="c473a-248">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="c473a-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="c473a-249">Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **Inicio de campañas de Marketing** en el explorador y, a continuación, cierre el panel de **permisos del sitio** .</span><span class="sxs-lookup"><span data-stu-id="c473a-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="c473a-250">A continuación se indican los resultados de la configuración de permisos:</span><span class="sxs-lookup"><span data-stu-id="c473a-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="c473a-251">El grupo de SharePoint de **Integrantes de campañas de Marketing** contiene sólo el grupo de **campañas de Marketing** (que contiene la cuenta de usuario de administrador global), en el grupo de **personal de Marketing** (que contiene los usuarios Marketing1 y Marketing2 cuentas) y la cuenta de usuario de **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="c473a-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="c473a-252">El grupo de SharePoint **Propietarios de campañas de Marketing** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="c473a-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="c473a-253">El grupo de SharePoint **Visitantes de campañas de Marketing** no contiene grupos o cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="c473a-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="c473a-254">Los miembros no pueden modificar los permisos de nivel de sitio (Esto sólo es posible miembros del grupo **Propietarios de campañas de Marketing** ).</span><span class="sxs-lookup"><span data-stu-id="c473a-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="c473a-255">Otras cuentas de usuario no tiene acceso a sus recursos o el sitio, pero pueden solicitar el acceso al sitio, que enviará un correo electrónico al buzón de la cuenta de usuario de ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="c473a-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="c473a-256">A continuación, configure la carpeta de documentos del sitio de grupo de campañas de Marketing para la etiqueta sensible.</span><span class="sxs-lookup"><span data-stu-id="c473a-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="c473a-257">En la ficha **Inicio de campañas de Marketing** del explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="c473a-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c473a-258">Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c473a-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c473a-259">En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c473a-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c473a-260">En **Aplicar configuración de etiqueta**, seleccione **confidencial**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="c473a-261">A continuación, configurar una directiva de prevention (DLP) de pérdida de datos que notifica a los usuarios que comparten un documento en un sitio de grupo SharePoint Online con la etiqueta confidencial, que incluye el sitio de campañas de Marketing, fuera de la organización.</span><span class="sxs-lookup"><span data-stu-id="c473a-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="c473a-262">En la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; Compliance** mosaico.</span><span class="sxs-lookup"><span data-stu-id="c473a-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="c473a-263">En el nuevo **seguridad &amp; Compliance** , haga clic en el explorador **prevención de pérdidas de datos > directiva de**.</span><span class="sxs-lookup"><span data-stu-id="c473a-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="c473a-264">En el panel de **prevención de pérdidas de datos** , haga clic en **+ crear una directiva**.</span><span class="sxs-lookup"><span data-stu-id="c473a-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="c473a-265">En el **comenzar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="c473a-266">En el panel **nombre de la directiva** , escriba **sitios de equipo de SharePoint Online etiqueta sensible** en **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="c473a-267">En el panel **Elegir ubicaciones** , haga clic en **Dejarme elegir ubicaciones específicas**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c473a-268">En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c473a-269">En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="c473a-270">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="c473a-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="c473a-271">En el panel **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="c473a-272">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="c473a-273">En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="c473a-274">En la **¿Qué desea hacer si se detecta información sensible?** panel, haga clic en **Personalizar la sugerencia y correo electrónico**.</span><span class="sxs-lookup"><span data-stu-id="c473a-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="c473a-275">En el panel de **sugerencias de directiva personalizar y notificaciones por correo electrónico** , haga clic en **Personalizar el texto de sugerencia de directiva**.</span><span class="sxs-lookup"><span data-stu-id="c473a-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="c473a-276">En el cuadro texto, escriba o pegue lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c473a-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="c473a-p108">Para compartir con otros usuarios fuera de la organización, descargue el archivo y, a continuación, ábralo. Haga clic en archivo, a continuación, Proteger documento y a continuación, cifrar con contraseña y, a continuación, especifique una contraseña segura. Enviar la contraseña en un correo electrónico u otros medios de comunicación.</span><span class="sxs-lookup"><span data-stu-id="c473a-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="c473a-280">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="c473a-281">En la **¿Qué desea hacer si se detecta información sensible?** panel, desactive la casilla de verificación **Bloquear personas compartan y restringir el acceso al contenido compartido** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="c473a-282">En el **¿desea activar las cosas de la política o prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="c473a-283">En el panel **Revisar la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="c473a-284">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="c473a-284">Here is your resulting configuration.</span></span>
  
![Protección de nivel confidencial del sitio de grupo de SharePoint Online aislado de campañas de marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="c473a-286">Sitio de grupo de estrategia de la empresa</span><span class="sxs-lookup"><span data-stu-id="c473a-286">Company strategy team site</span></span>

<span data-ttu-id="c473a-287">Para crear un sitio de grupo SharePoint Online aislado en el nivel de recursos de empresa estratégico de los ejecutivos de la organización altamente confidencial, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c473a-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="c473a-p109">Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 mediante su cuenta de administrador global. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c473a-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c473a-290">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c473a-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="c473a-291">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="c473a-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="c473a-292">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="c473a-293">En **nombre de sitio de equipo**, escriba la **estrategia de la empresa**.</span><span class="sxs-lookup"><span data-stu-id="c473a-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="c473a-294">En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para la estrategia de la empresa (confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="c473a-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="c473a-295">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c473a-296">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="c473a-297">En la ficha nuevo de la **estrategia de la empresa** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="c473a-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="c473a-298">En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.</span><span class="sxs-lookup"><span data-stu-id="c473a-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="c473a-299">En la ficha **permisos** de nuevo en el explorador, haga clic en **Configuración de solicitud de acceso**.</span><span class="sxs-lookup"><span data-stu-id="c473a-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="c473a-300">En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **miembros de permitir invitar a otras personas al grupo de miembros del sitio** (de modo que todas las casillas de verificación está desactivadas) y, a continuación, haga clic en ** Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="c473a-301">En la lista, haga clic en **miembros de estrategia de la empresa** .</span><span class="sxs-lookup"><span data-stu-id="c473a-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="c473a-302">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="c473a-303">En el cuadro de diálogo **Compartir** , escriba **C-Suite**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="c473a-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="c473a-304">En la lista, haga clic en **la estrategia de la empresa propietarios** .</span><span class="sxs-lookup"><span data-stu-id="c473a-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="c473a-305">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="c473a-306">En el cuadro de diálogo **Compartir** , escriba **personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="c473a-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="c473a-307">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="c473a-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="c473a-308">Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **Página principal de estrategia de la empresa** en el explorador y, a continuación, cierre el panel de **permisos del sitio** .</span><span class="sxs-lookup"><span data-stu-id="c473a-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="c473a-309">A continuación se indican los resultados de la configuración de permisos:</span><span class="sxs-lookup"><span data-stu-id="c473a-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="c473a-310">El grupo de SharePoint **Miembros de estrategia de la compañía** contiene sólo el grupo **Ejecutivos** (que contiene sólo las cuentas de usuario de director ejecutivo, director financiero y director) y el grupo de **estrategia de la empresa** (que contiene sólo la cuenta de usuario de administrador global).</span><span class="sxs-lookup"><span data-stu-id="c473a-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="c473a-311">El grupo de SharePoint **Propietarios de estrategia de la compañía** contiene el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="c473a-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="c473a-312">El grupo de SharePoint **Visitantes de estrategia de la compañía** no contiene grupos o cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="c473a-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="c473a-313">Los miembros no pueden modificar los permisos de nivel de sitio (Esto sólo es posible miembros del grupo **Propietarios de estrategia de la empresa** ).</span><span class="sxs-lookup"><span data-stu-id="c473a-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="c473a-p110">Otras cuentas de usuario no pueden tener acceso a sus recursos o el sitio o solicitar acceso al sitio. Permisos adicionales para el sitio deben realizarse por el administrador global o por un miembro del grupo de **Propietarios de estrategia de la empresa** .</span><span class="sxs-lookup"><span data-stu-id="c473a-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="c473a-316">A continuación, configure la carpeta de documentos del sitio del grupo empresa estrategia para la etiqueta altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="c473a-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="c473a-317">En la ficha **Página principal de estrategia de la compañía** del explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="c473a-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="c473a-318">Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c473a-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="c473a-319">En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="c473a-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="c473a-320">En **Aplicar configuración de etiqueta**, seleccione **Confidencial**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="c473a-321">A continuación, configure una directiva DLP que impide a los usuarios cuando se comparten un documento en un sitio de grupo SharePoint Online con la etiqueta altamente confidencial, que incluye el sitio de la estrategia de la empresa, fuera de la organización.</span><span class="sxs-lookup"><span data-stu-id="c473a-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="c473a-p111">Si es necesario, utilizar un explorador en el equipo local e iniciar sesión en el portal de Office 365 con una cuenta que tiene la función de administrador de seguridad o de la empresa. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c473a-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c473a-324">En la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; Compliance** mosaico.</span><span class="sxs-lookup"><span data-stu-id="c473a-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="c473a-325">En el nuevo **seguridad &amp; Compliance** , haga clic en el explorador **prevención de pérdidas de datos > directiva de**.</span><span class="sxs-lookup"><span data-stu-id="c473a-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="c473a-326">En el panel de **prevención de pérdidas de datos** , haga clic en **+ crear una directiva**.</span><span class="sxs-lookup"><span data-stu-id="c473a-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="c473a-327">En el **comenzar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="c473a-328">En el panel **nombre de la directiva** , escriba **sitios de equipo de SharePoint Online de etiqueta altamente confidencial** en **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="c473a-329">En el panel **Elegir ubicaciones** , haga clic en **Dejarme elegir ubicaciones específicas**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="c473a-330">En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="c473a-331">En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="c473a-332">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="c473a-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="c473a-333">En el panel **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **Altamente confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="c473a-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="c473a-334">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="c473a-335">En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="c473a-336">En la **¿Qué desea hacer si se detecta información sensible?** panel, haga clic en **Personalizar la sugerencia y correo electrónico**.</span><span class="sxs-lookup"><span data-stu-id="c473a-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="c473a-337">En el panel de **sugerencias de directiva personalizar y notificaciones por correo electrónico** , haga clic en **Personalizar el texto de sugerencia de directiva**.</span><span class="sxs-lookup"><span data-stu-id="c473a-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="c473a-338">En el cuadro texto, escriba o pegue lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="c473a-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="c473a-p112">Para compartir con otros usuarios fuera de la organización, descargue el archivo y, a continuación, ábralo. Haga clic en archivo, a continuación, Proteger documento y a continuación, cifrar con contraseña y, a continuación, especifique una contraseña segura. Enviar la contraseña en un correo electrónico u otros medios de comunicación.</span><span class="sxs-lookup"><span data-stu-id="c473a-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="c473a-342">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="c473a-343">En la **¿Qué desea hacer si se detecta información sensible?** panel, seleccione **requerir una justificación comercial para reemplazar**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="c473a-344">En el **¿desea activar las cosas de la política o prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c473a-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="c473a-345">En el panel **Revisar la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="c473a-346">A continuación, siga las instrucciones en [Activar Azure RMS con el centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="c473a-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="c473a-347">A continuación, configurar la protección de la información de Azure con una nueva directiva con ámbito y Sub-etiqueta de protección y los permisos con los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="c473a-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="c473a-p113">Iniciar sesión en el portal de Office 365 con una cuenta que tiene la función de administrador de seguridad o de la empresa. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="c473a-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="c473a-350">En una ficha independiente del explorador, vaya al portal de Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="c473a-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="c473a-351">Si es la primera vez se configura la protección de la información de Azure, consulte estas [instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="c473a-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="c473a-352">En el panel lista, haga clic en **más servicios**, escriba la **información**y, a continuación, haga clic en **Protección de la información de Azure**.</span><span class="sxs-lookup"><span data-stu-id="c473a-352">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="c473a-353">En la hoja de **protección de la información de Azure** , haga clic en **ámbito directivas > + Agregar una nueva directiva de**.</span><span class="sxs-lookup"><span data-stu-id="c473a-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="c473a-354">Escriba **CompanyStrategy** en el **nombre de directiva** y **etiqueta de documentos en el sitio de grupo de estrategia de la empresa** en la **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="c473a-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="c473a-355">Haga clic en **Seleccionar qué usuarios o grupos Obtén esta directiva > grupos de usuarios/**y, a continuación, seleccione **Conjunto de C**.</span><span class="sxs-lookup"><span data-stu-id="c473a-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="c473a-356">Haga clic en **Seleccionar > Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="c473a-357">Para la etiqueta **Altamente confidencial** , haga clic en los puntos suspensivos (...) y, a continuación, haga clic en **Agregar una etiqueta Sub**.</span><span class="sxs-lookup"><span data-stu-id="c473a-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="c473a-358">Escriba un nombre para la Sub-etiqueta de **nombre** y una descripción de la etiqueta de **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="c473a-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="c473a-359">**Establecer permisos para documentos y correos electrónicos con esta etiqueta**, haga clic en **proteger**.</span><span class="sxs-lookup"><span data-stu-id="c473a-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="c473a-360">En la sección de **protección** , haga clic en **Azure (clave de nube)**.</span><span class="sxs-lookup"><span data-stu-id="c473a-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="c473a-361">En la hoja de **protección** , en **configuración de protección**, haga clic en **+ Agregar permisos**.</span><span class="sxs-lookup"><span data-stu-id="c473a-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="c473a-362">En la hoja de **permisos para agregar** , en **especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.</span><span class="sxs-lookup"><span data-stu-id="c473a-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="c473a-363">En el panel de **DAA usuarios y grupos** , seleccione **Conjunto de C**y, a continuación, haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="c473a-364">En **Elija el ajuste preestablecido los permisos**, desactive las casillas de verificación **Imprimir**, **Copiar y extraer contenido**y **hacia delante** .</span><span class="sxs-lookup"><span data-stu-id="c473a-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="c473a-365">Haga clic en **Aceptar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="c473a-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="c473a-366">En la hoja **secundario-etiqueta** , haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c473a-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="c473a-367">Cierre el nuevo blade de ámbito de la política.</span><span class="sxs-lookup"><span data-stu-id="c473a-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="c473a-368">En el módulo de **protección de la información de Azure - directivas de ámbito** , haga clic en **Publicar**y, a continuación, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="c473a-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="c473a-369">Para proteger un documento con la protección de la información de Azure y esta nueva etiqueta, debe [instalar al cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en un equipo de prueba, instalar Office desde el portal de Office 365 y, a continuación, iniciar sesión en desde Microsoft Word con una cuenta en el ** C-Suite** grupo de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="c473a-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="c473a-370">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="c473a-370">Here is your resulting configuration.</span></span>
  
![Protección de nivel alto de confidencialidad de un sitio de grupo de SharePoint Online aislado de estrategia de empresa.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="c473a-372">Ahora está listo para crear documentos en estos cuatro sitios y probar el acceso a ellos con varias cuentas de usuario en su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="c473a-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="c473a-373">Aquí está la configuración global para todos los sitios de equipo de SharePoint Online cuatro.</span><span class="sxs-lookup"><span data-stu-id="c473a-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![Los cuatro sitios de grupo del entorno de pruebas y desarrollo de SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="c473a-375">Siguiente paso</span><span class="sxs-lookup"><span data-stu-id="c473a-375">Next step</span></span>

<span data-ttu-id="c473a-376">Cuando esté listo para la implementación de producción de sitios de SharePoint Online seguros, vea [archivos y sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md) para obtener información detallada y vínculos a artículos de implementación paso a paso.</span><span class="sxs-lookup"><span data-stu-id="c473a-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c473a-377">See Also</span><span class="sxs-lookup"><span data-stu-id="c473a-377">See Also</span></span>

[<span data-ttu-id="c473a-378">Proteger los archivos y los sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c473a-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="c473a-379">Soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="c473a-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="c473a-380">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="c473a-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="c473a-381">Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile</span><span class="sxs-lookup"><span data-stu-id="c473a-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)



