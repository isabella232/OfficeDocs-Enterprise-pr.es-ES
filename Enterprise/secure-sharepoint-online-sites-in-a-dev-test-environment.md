---
title: Protección de sitios de SharePoint Online en un entorno de prueba y desarrollo
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/14/2018
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: Priority
ms.custom: ''
ms.assetid: 06af70f3-e7dc-4ee2-a385-fb4d61a5e93b
description: 'Resumen: Cree sitios de grupo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en un entorno de desarrollo o prueba.'
ms.openlocfilehash: 004a1614330f220b31be640cd822d9fdcbb49b99
ms.sourcegitcommit: 29c8571ca4912549bac55ec9d1642d21eba5b0e4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/16/2018
---
# <a name="secure-sharepoint-online-sites-in-a-devtest-environment"></a><span data-ttu-id="08f62-103">Protección de sitios de SharePoint Online en un entorno de prueba y desarrollo</span><span class="sxs-lookup"><span data-stu-id="08f62-103">Secure SharePoint Online sites in a dev/test environment</span></span>

 <span data-ttu-id="08f62-104">**Resumen:** Crear sitios de grupo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en un entorno de desarrollo o prueba.</span><span class="sxs-lookup"><span data-stu-id="08f62-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in a dev/test environment.</span></span>
  
<span data-ttu-id="08f62-105">Este artículo proporciona instrucciones paso a paso para crear un entorno de desarrollo y prueba que incluye los cuatro tipos diferentes de sitios de grupo de SharePoint Online para la solución de [archivos y sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md) .</span><span class="sxs-lookup"><span data-stu-id="08f62-105">This article provides step-by-step instructions to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) solution.</span></span>
  
![Los cuatro sitios de grupo del entorno de pruebas y desarrollo de SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
<span data-ttu-id="08f62-107">Con este entorno de prueba y desarrollo podrá experimentar con los comportamientos de protección de la información y ajustar la configuración a sus necesidades concretas antes de implementar sitios de grupo de SharePoint Online en producción.</span><span class="sxs-lookup"><span data-stu-id="08f62-107">Use this dev/test environment to experiment with the information protection behaviors and fine-tune settings for your specific needs before deploying SharePoint Online team sites in production.</span></span>
  
## <a name="phase-1-create-your-devtest-environment"></a><span data-ttu-id="08f62-108">Fase 1: Crear el entorno de prueba y desarrollo</span><span class="sxs-lookup"><span data-stu-id="08f62-108">Phase 1: Create your dev/test environment</span></span>

<span data-ttu-id="08f62-109">En esta fase se obtienen suscripciones de evaluación para Office 365 y Enterprise Mobility + Security para una organización ficticia.</span><span class="sxs-lookup"><span data-stu-id="08f62-109">In this phase, you obtain trial subscriptions for Office 365 and Enterprise Mobility + Security for a fictional organization.</span></span>
  
<span data-ttu-id="08f62-110">Primero siga las instrucciones de la **fase 2** del [entorno de prueba y desarrollo de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="08f62-110">First, follow the instructions in **Phase 2** of the [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="08f62-111">A continuación, registrarse para la suscripción de prueba de EMS y agregarlo a la misma organización que su suscripción de prueba de Office 365.</span><span class="sxs-lookup"><span data-stu-id="08f62-111">Next, sign up for the EMS trial subscription and add it to the same organization as your Office 365 trial subscription.</span></span>
  
1. <span data-ttu-id="08f62-p101">Si es necesario, inicie sesión el portal de Office 365 con las credenciales de la cuenta de administrador global de su suscripción de prueba. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="08f62-p101">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="08f62-114">Haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="08f62-114">Click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="08f62-115">En la pestaña **Centro de administración de Office** del explorador, en el panel de navegación izquierdo, haga clic en **Facturación > Servicios de compra**.</span><span class="sxs-lookup"><span data-stu-id="08f62-115">On the **Office Admin center** tab in your browser, in the left navigation, click **Billing > Purchase services**.</span></span>
    
4. <span data-ttu-id="08f62-p102">En la página **Servicios de compra** , busque el elemento de **movilidad en la empresa + E5 de seguridad** . Sitúe el puntero del mouse sobre él y haga clic en **iniciar la versión de prueba gratuita**.</span><span class="sxs-lookup"><span data-stu-id="08f62-p102">On the **Purchase services** page, find the **Enterprise Mobility + Security E5** item. Hover your mouse pointer over it and click **Start free trial**.</span></span>
    
5. <span data-ttu-id="08f62-118">En la página **Confirmar pedido**, haga clic en **Probar ahora**.</span><span class="sxs-lookup"><span data-stu-id="08f62-118">On the **Confirm your order** page, click **Try now**.</span></span>
    
6. <span data-ttu-id="08f62-119">En la página **Recibo del pedido**, haga clic en **Continuar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-119">On the **Order receipt** page, click **Continue**.</span></span>
    
<span data-ttu-id="08f62-120">Después, habilite la licencia de Enterprise Mobility + Security E5 para la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="08f62-120">Next, enable the Enterprise Mobility + Security E5 license for your global administrator account.</span></span>
  
1. <span data-ttu-id="08f62-121">En la pestaña **Centro de administración de Office 365** del explorador, en el panel de navegación izquierdo, haga clic en **Usuarios > Usuarios activos**.</span><span class="sxs-lookup"><span data-stu-id="08f62-121">On the **Office 365 Admin center** tab in your browser, in the left navigation, click **Users > Active users**.</span></span>
    
2. <span data-ttu-id="08f62-122">Haga clic en la cuenta de administrador global y, a continuación, haga clic en **Editar** para **licencias de producto**.</span><span class="sxs-lookup"><span data-stu-id="08f62-122">Click your global administrator account, and then click **Edit** for **Product licenses**.</span></span>
    
3. <span data-ttu-id="08f62-123">En el panel de **licencias de producto** , activar la licencia del producto para **movilidad de la empresa + seguridad E5** **activado**, haga clic en **Guardar** y, a continuación, haga clic en **Cerrar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="08f62-123">On the **Product licenses** pane, turn the product license for **Enterprise Mobility + Security E5** to **On**, click **Save,** and then click **Close** twice.</span></span>
    
## <a name="phase-2-create-and-configure-your-azure-active-directory-ad-groups-and-users"></a><span data-ttu-id="08f62-124">Fase 2: Crear y configurar los usuarios y grupos de Azure Active Directory (AD)</span><span class="sxs-lookup"><span data-stu-id="08f62-124">Phase 2: Create and configure your Azure Active Directory (AD) groups and users</span></span>

<span data-ttu-id="08f62-125">En esta fase se crean y configuran los grupos y usuarios de Azure AD para la organización ficticia.</span><span class="sxs-lookup"><span data-stu-id="08f62-125">In this phase, you create and configure the Azure AD groups and users for your fictional organization.</span></span>
  
<span data-ttu-id="08f62-126">En primer lugar, cree un conjunto de grupos para una organización típica en Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="08f62-126">First, create a set of groups for a typical organization with the Azure portal.</span></span>
  
1. <span data-ttu-id="08f62-127">Crear una ficha independiente en el explorador y, a continuación, vaya al portal de Azure en [https://portal.azure.com](https://portal.azure.com). Si es necesario, inicie sesión con las credenciales de la cuenta de administrador global para la suscripción de prueba de Office 365 E5.</span><span class="sxs-lookup"><span data-stu-id="08f62-127">Create a separate tab in your browser, and then go to the Azure portal at [https://portal.azure.com](https://portal.azure.com). If needed, sign in with the credentials of the global administrator account for your Office 365 E5 trial subscription.</span></span>
    
2. <span data-ttu-id="08f62-128">En el portal de Azure, haga clic en **Azure Active Directory > grupos**.</span><span class="sxs-lookup"><span data-stu-id="08f62-128">In the Azure portal, click **Azure Active Directory > Groups**.</span></span>
    
3. <span data-ttu-id="08f62-129">En el servidor blade de **grupos: todos los grupos** , haga clic en **+ nuevo grupo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-129">On the **Groups - All groups** blade, click **+ New group**.</span></span>
    
4. <span data-ttu-id="08f62-130">En la hoja **Grupo**:</span><span class="sxs-lookup"><span data-stu-id="08f62-130">On the **Group** blade:</span></span>
    
  - <span data-ttu-id="08f62-131">En **tipo de grupo**, seleccione **Office 365** .</span><span class="sxs-lookup"><span data-stu-id="08f62-131">Select **Office 365** in **Group type**.</span></span>
    
  - <span data-ttu-id="08f62-132">Escriba **C-Suite** en **Nombre**.</span><span class="sxs-lookup"><span data-stu-id="08f62-132">Type **C-Suite** in **Name**.</span></span>
    
  - <span data-ttu-id="08f62-133">Seleccione **asignadas** en **tipo de pertenencia**.</span><span class="sxs-lookup"><span data-stu-id="08f62-133">Select **Assigned** in **Membership type**.</span></span>
      
5. <span data-ttu-id="08f62-134">Haga clic en **Crear** y, luego, cierre la hoja **Grupo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-134">Click **Create**, and then close the **Group** blade.</span></span>
    
6. <span data-ttu-id="08f62-135">Repita los pasos del 3 al 5 para los siguientes nombres de grupo:</span><span class="sxs-lookup"><span data-stu-id="08f62-135">Repeat steps 3-5 for the following group names:</span></span>
    
  - <span data-ttu-id="08f62-136">IT staff (Personal de TI)</span><span class="sxs-lookup"><span data-stu-id="08f62-136">IT staff</span></span>
    
  - <span data-ttu-id="08f62-137">Research staff (Personal de investigación)</span><span class="sxs-lookup"><span data-stu-id="08f62-137">Research staff</span></span>
    
  - <span data-ttu-id="08f62-138">Regular staff (Personal normal)</span><span class="sxs-lookup"><span data-stu-id="08f62-138">Regular staff</span></span>
    
  - <span data-ttu-id="08f62-139">Marketing staff (Personal de marketing)</span><span class="sxs-lookup"><span data-stu-id="08f62-139">Marketing staff</span></span>
    
  - <span data-ttu-id="08f62-140">Sales staff (Personal de ventas)</span><span class="sxs-lookup"><span data-stu-id="08f62-140">Sales staff</span></span>
    
7. <span data-ttu-id="08f62-141">Mantenga la pestaña de Azure Portal abierta en el explorador.</span><span class="sxs-lookup"><span data-stu-id="08f62-141">Keep the Azure portal tab in your browser open.</span></span>
    
<span data-ttu-id="08f62-142">A continuación, configure la acción de licencias automático para que los miembros de los grupos se les asigna automáticamente licencias para las suscripciones de Office 365 y EMS.</span><span class="sxs-lookup"><span data-stu-id="08f62-142">Next, you configure automatic licensing so that members of your groups are automatically assigned licenses for your Office 365 and EMS subscriptions.</span></span>
  
1. <span data-ttu-id="08f62-143">En Azure Portal, haga clic en **Azure Active Directory > Licencias > Todos los productos**.</span><span class="sxs-lookup"><span data-stu-id="08f62-143">In the Azure portal, click **Azure Active Directory > Licenses > All products**.</span></span>
    
2. <span data-ttu-id="08f62-144">En la lista, seleccione **seguridad E5 + de movilidad en la empresa** y **Office 365 Enterprise E5**y, a continuación, haga clic en **asignar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-144">In the list, select **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5**, and then click **Assign**.</span></span>
    
3. <span data-ttu-id="08f62-145">En la hoja **Asignar licencia**, haga clic en **Usuarios y grupos**.</span><span class="sxs-lookup"><span data-stu-id="08f62-145">In the **Assign license** blade, click **Users and groups**.</span></span>
    
4. <span data-ttu-id="08f62-146">En la lista de grupos, seleccione lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="08f62-146">In the list of groups, select the following:</span></span>
    
  - <span data-ttu-id="08f62-147">C-Suite (Directivos)</span><span class="sxs-lookup"><span data-stu-id="08f62-147">C-Suite</span></span>
    
  - <span data-ttu-id="08f62-148">IT staff (Personal de TI)</span><span class="sxs-lookup"><span data-stu-id="08f62-148">IT staff</span></span>
    
  - <span data-ttu-id="08f62-149">Research staff (Personal de investigación)</span><span class="sxs-lookup"><span data-stu-id="08f62-149">Research staff</span></span>
    
  - <span data-ttu-id="08f62-150">Regular staff (Personal normal)</span><span class="sxs-lookup"><span data-stu-id="08f62-150">Regular staff</span></span>
    
  - <span data-ttu-id="08f62-151">Marketing staff (Personal de marketing)</span><span class="sxs-lookup"><span data-stu-id="08f62-151">Marketing staff</span></span>
    
  - <span data-ttu-id="08f62-152">Sales staff (Personal de ventas)</span><span class="sxs-lookup"><span data-stu-id="08f62-152">Sales staff</span></span>
    
5. <span data-ttu-id="08f62-153">Haga clic en **Seleccionar**y, a continuación, haga clic en **asignar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-153">Click **Select**, and then click **Assign**.</span></span>
    
6. <span data-ttu-id="08f62-154">Cierre la pestaña Azure Portal del explorador.</span><span class="sxs-lookup"><span data-stu-id="08f62-154">Close the Azure portal tab in your browser.</span></span>
    
<span data-ttu-id="08f62-155">Después, debe [conectarse al módulo PowerShell de Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="08f62-155">Next, you [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
<span data-ttu-id="08f62-156">Rellene el nombre de la organización, su ubicación y una contraseña común y, a continuación, ejecute estos comandos desde el símbolo del sistema de PowerShell o el entorno de secuencia de comandos integrado (ISE) para crear cuentas de usuario y agregarlos a sus grupos de:</span><span class="sxs-lookup"><span data-stu-id="08f62-156">Fill in your organization name, your location, and a common password, and then run these commands from the PowerShell command prompt or Integrated Script Environment (ISE) to create user accounts and add them to their groups:</span></span>
  
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
> <span data-ttu-id="08f62-p103">Se usa una contraseña común para automatizar y facilitar la configuración de un entorno de prueba y desarrollo. No se recomienda para suscripciones de producción.</span><span class="sxs-lookup"><span data-stu-id="08f62-p103">The use of a common password here is for automation and ease of configuration for a dev/test environment. This is not recommended for production subscriptions.</span></span> 
  
<span data-ttu-id="08f62-159">Siga estos pasos para comprobar que basadas en grupos de licencias está funcionando correctamente.</span><span class="sxs-lookup"><span data-stu-id="08f62-159">Use these steps to verify that group-based licensing is working correctly.</span></span>
  
1. <span data-ttu-id="08f62-160">En la pestaña de **inicio de Microsoft Office** del explorador, haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="08f62-160">From the **Microsoft Office Home** tab of your browser, click the **Admin** tile.</span></span>
    
2. <span data-ttu-id="08f62-161">En la nueva pestaña **Centro de administración de Office** del explorador, haga clic en **Usuarios**.</span><span class="sxs-lookup"><span data-stu-id="08f62-161">From the new **Office Admin center** tab of your browser, click **Users**.</span></span>
    
3. <span data-ttu-id="08f62-162">En la lista de usuarios, haga clic en **CEO** (Consejero delegado).</span><span class="sxs-lookup"><span data-stu-id="08f62-162">In the list of users, click **CEO**.</span></span>
    
4. <span data-ttu-id="08f62-163">En el panel que muestra las propiedades de la cuenta de usuario **CEO**, compruebe que se le han asignado las licencias **Enterprise Mobility + Security E5** y **Office 365 Enterprise E5** (en **Licencias de productos**).</span><span class="sxs-lookup"><span data-stu-id="08f62-163">In the pane that lists the properties of the **CEO** user account, verify that it has been assigned the **Enterprise Mobility + Security E5** and **Office 365 Enterprise E5** licenses (in **Product licenses**).</span></span>
    
## <a name="phase-3-create-office-365-labels"></a><span data-ttu-id="08f62-164">Fase 3: Crear etiquetas de Office 365</span><span class="sxs-lookup"><span data-stu-id="08f62-164">Phase 3: Create Office 365 labels</span></span>

<span data-ttu-id="08f62-165">En esta fase se crean las etiquetas para los diferentes niveles de seguridad de las carpetas de documentos de sitios de grupo de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="08f62-165">In this phase, you create the labels for the different levels of security for SharePoint Online team site documents folders.</span></span>
  
1. <span data-ttu-id="08f62-p104">Si es necesario, use una instancia privada de su explorador de Internet e inicie sesión el portal de Office 365 con la cuenta de administrador global de su suscripción de prueba de Office 365 E5. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="08f62-p104">If needed, use a private instance of your Internet browser and sign in to the Office 365 portal with the global administrator account of your Office 365 E5 trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="08f62-168">En la pestaña de **inicio de Microsoft Office**, haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="08f62-168">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="08f62-169">En la ficha del **Centro de administración de Office de** nuevo del explorador, haga clic en **centros de administración > seguridad &amp; cumplimiento**.</span><span class="sxs-lookup"><span data-stu-id="08f62-169">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="08f62-170">Desde la nueva **principal - seguridad &amp; cumplimiento** ficha del explorador, haga clic en **clasificaciones > etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="08f62-170">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="08f62-171">En el panel **Inicio > Etiquetas**, haga clic en **Crear una etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="08f62-171">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="08f62-172">En el panel de **la etiqueta de nombre** , escriba **Público interno**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-172">On the **Name your label** pane, type **Internal Public**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="08f62-173">En el panel **Configuración de etiquetas**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-173">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="08f62-174">En el panel de **revisión de la configuración** , haga clic en **crear esta etiqueta**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-174">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="08f62-175">Repita los pasos del 5 al 8 para estas etiquetas adicionales:</span><span class="sxs-lookup"><span data-stu-id="08f62-175">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="08f62-176">Private</span><span class="sxs-lookup"><span data-stu-id="08f62-176">Private</span></span>
    
  - <span data-ttu-id="08f62-177">Confidencial</span><span class="sxs-lookup"><span data-stu-id="08f62-177">Sensitive</span></span>
    
  - <span data-ttu-id="08f62-178">Extremadamente confidencial</span><span class="sxs-lookup"><span data-stu-id="08f62-178">Highly Confidential</span></span>
    
10. <span data-ttu-id="08f62-179">En el panel **Inicio > Etiquetas**, haga clic para **Publish labels** (Publicar etiquetas).</span><span class="sxs-lookup"><span data-stu-id="08f62-179">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="08f62-180">En el panel **Choose labels to publish** (Elegir las etiquetas que se van a publicar), haga clic en **Choose labels to publish**.</span><span class="sxs-lookup"><span data-stu-id="08f62-180">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="08f62-181">En el panel de **elección de etiquetas**, haga clic en **Agregar** y seleccione las cuatro etiquetas.</span><span class="sxs-lookup"><span data-stu-id="08f62-181">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="08f62-182">Haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-182">Click **Done**.</span></span>
    
14. <span data-ttu-id="08f62-183">En el panel **Choose labels to publish** (Elegir las etiquetas que se van a publicar), haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-183">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="08f62-184">En el panel **Elegir ubicaciones**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-184">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="08f62-185">En el panel de **nombre de la directiva** , escriba **organización de ejemplo** en **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-185">On the **Name your policy** pane, type **Example organization** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="08f62-186">En el panel de **revisión de la configuración** , haga clic en **etiquetas de publicar**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-186">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-4-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="08f62-187">Fase 4: Crear los sitios de grupo de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="08f62-187">Phase 4: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="08f62-188">En esta fase se crean y configuran los cuatro tipos de sitios de grupo de SharePoint Online de la organización de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="08f62-188">In this phase, you create and configure the four types of SharePoint Online team sites for your example organization.</span></span>
  
### <a name="organization-wide-team-site"></a><span data-ttu-id="08f62-189">Sitio de grupo De organización</span><span class="sxs-lookup"><span data-stu-id="08f62-189">Organization wide team site</span></span>

<span data-ttu-id="08f62-190">Para crear un sitio de grupo público de base de referencia de SharePoint Online, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="08f62-190">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="08f62-p105">Si es necesario, use un explorador en el equipo local e inicie sesión en el portal de Office 365 con la cuenta de administrador global. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).</span><span class="sxs-lookup"><span data-stu-id="08f62-p105">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="08f62-193">En la lista de iconos, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="08f62-193">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="08f62-194">En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.</span><span class="sxs-lookup"><span data-stu-id="08f62-194">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="08f62-195">En la página **Crear un sitio**, haga clic en **Sitio de grupo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-195">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="08f62-196">En **Nombre del sitio**, escriba **En toda la organización**.</span><span class="sxs-lookup"><span data-stu-id="08f62-196">In **Site name**, type **Organization wide**.</span></span> 
    
6. <span data-ttu-id="08f62-197">En **Team site description** (Descripción de sitio de grupo), escriba **Sitio de SharePoint para toda la organización**.</span><span class="sxs-lookup"><span data-stu-id="08f62-197">In **Team site description**, type **SharePoint site for the entire organization**.</span></span>
    
7. <span data-ttu-id="08f62-198">En **la configuración de privacidad**, seleccione **pública - cualquier persona de la organización puede tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-198">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="08f62-199">En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-199">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="08f62-200">Después configure la carpeta de documentos del sitio de grupo En toda la organización para la etiqueta Interno público.</span><span class="sxs-lookup"><span data-stu-id="08f62-200">Next, configure the documents folder of the Organization wide team site for the Internal Public label.</span></span>
  
1. <span data-ttu-id="08f62-201">En la ficha **Home de toda la organización** del explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="08f62-201">In the **Organization wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="08f62-202">Haga clic en el icono de configuración y luego en **Configuración de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="08f62-202">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="08f62-203">En **Permisos y administración**, haga clic en **Apply label to items in this library** (Aplicar la etiqueta a los elementos de esta biblioteca).</span><span class="sxs-lookup"><span data-stu-id="08f62-203">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="08f62-204">En **Aplicar a la configuración de etiqueta**, seleccione **Interna pública**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-204">In **Settings-Apply Label**, select **Internal Public**, and then click **Save**.</span></span>
    
<span data-ttu-id="08f62-205">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="08f62-205">Here is your resulting configuration.</span></span>
  
![Protección de nivel de línea base del sitio de grupo de SharePoint Online público de toda la organización.](images/25c86847-a38d-49ad-bb5f-c7c04206b6dc.png)
  
### <a name="project-1-team-site"></a><span data-ttu-id="08f62-207">Sitio de grupo Proyecto 1</span><span class="sxs-lookup"><span data-stu-id="08f62-207">Project 1 team site</span></span>

<span data-ttu-id="08f62-208">Para crear un sitio de grupo privado de base de referencia de SharePoint Online para un proyecto dentro de la organización, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="08f62-208">To create a baseline private SharePoint Online team site for a project within the organization, do the following:</span></span>
  
1. <span data-ttu-id="08f62-p106">Si es necesario, use un explorador en el equipo local e inicie sesión en el portal de Office 365 con la cuenta de administrador global. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).</span><span class="sxs-lookup"><span data-stu-id="08f62-p106">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="08f62-211">En la lista de iconos, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="08f62-211">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="08f62-212">En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.</span><span class="sxs-lookup"><span data-stu-id="08f62-212">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="08f62-213">En la página **Crear un sitio**, haga clic en **Sitio de grupo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-213">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="08f62-214">En **Nombre del sitio**, escriba **Proyecto 1**.</span><span class="sxs-lookup"><span data-stu-id="08f62-214">In **Site name**, type **Project 1**.</span></span> 
    
6. <span data-ttu-id="08f62-215">En **Descripción del sitio del equipo,** escriba el **sitio de SharePoint para el proyecto 1**.</span><span class="sxs-lookup"><span data-stu-id="08f62-215">In **Team site description,** type **SharePoint site for Project 1**.</span></span>
    
7. <span data-ttu-id="08f62-216">En **la configuración de privacidad**, seleccione **privada - sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-216">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="08f62-217">En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-217">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="08f62-218">Después, configure la carpeta de documentos del sitio de grupo Proyecto 1 para la etiqueta Privado.</span><span class="sxs-lookup"><span data-stu-id="08f62-218">Next, configure the documents folder of the Project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="08f62-219">En la pestaña **Proyecto 1-Inicio** del explorador, haga clic en **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="08f62-219">In the **Project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="08f62-220">Haga clic en el icono de configuración y luego en **Configuración de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="08f62-220">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="08f62-221">En **Permisos y administración**, haga clic en **Apply label to items in this library** (Aplicar la etiqueta a los elementos de esta biblioteca).</span><span class="sxs-lookup"><span data-stu-id="08f62-221">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="08f62-222">En la **Configuración se aplica la etiqueta**, seleccione **privada**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-222">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
<span data-ttu-id="08f62-223">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="08f62-223">Here is your resulting configuration.</span></span>
  
![Protección de nivel de línea base del sitio de grupo de SharePoint Online privado Project1.](images/ecd96376-b5dc-4042-9cbd-b3765507ace7.png)
  
### <a name="marketing-campaigns-team-site"></a><span data-ttu-id="08f62-225">Sitio de grupo Campañas de marketing</span><span class="sxs-lookup"><span data-stu-id="08f62-225">Marketing campaigns team site</span></span>

<span data-ttu-id="08f62-226">Para crear un sitio de grupo aislado de SharePoint Online que tenga el nivel confidencial para recursos de campañas de marketing, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="08f62-226">To create a sensitive-level isolated SharePoint Online team site for marketing campaign resources, do the following:</span></span>
  
1. <span data-ttu-id="08f62-p107">Uso de un explorador en su equipo local, inicie sesión en el portal de Office 365 con su cuenta de administrador global. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="08f62-p107">Using a browser on your local computer, sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="08f62-229">En la lista de iconos, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="08f62-229">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="08f62-230">En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.</span><span class="sxs-lookup"><span data-stu-id="08f62-230">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="08f62-231">En la página **Crear un sitio**, haga clic en **Sitio de grupo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-231">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="08f62-232">En **Team site name** (Nombre del sitio de grupo), escriba **Campañas de marketing**.</span><span class="sxs-lookup"><span data-stu-id="08f62-232">In **Team site name**, type **Marketing campaigns**.</span></span>
    
6. <span data-ttu-id="08f62-233">En **Team site description** (Descripción del sitio de grupo), escriba **Sitio de SharePoint para recursos de campaña de marketing (confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="08f62-233">In **Team site description**, type **SharePoint site for marketing campaign resources (sensitive)**.</span></span>
    
7.  <span data-ttu-id="08f62-234">En **la configuración de privacidad**, seleccione **privada - sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-234">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="08f62-235">En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-235">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="08f62-236">En la ficha nuevo de **campañas de Marketing** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="08f62-236">On the new **Marketing campaigns** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="08f62-237">En el panel **Permisos del sitio**, haga clic en **Advanced permissions settings** (Configuración de permisos avanzada).</span><span class="sxs-lookup"><span data-stu-id="08f62-237">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="08f62-238">En la nueva pestaña **Permisos** del explorador, haga clic en **Configuración de solicitud de acceso**.</span><span class="sxs-lookup"><span data-stu-id="08f62-238">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="08f62-239">En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive las casillas de verificación **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **Permitir miembros para invitar a otras personas al grupo de miembros del sitio** , escriba **ITAdmin1 @**\<su nombre de la organización >**. onmicrosoft.com** en **Enviar todas las solicitudes de acceso**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-239">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**\<your organization name>**.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="08f62-240">Haga clic en **Campañas de Marketing-Miembros** en la lista.</span><span class="sxs-lookup"><span data-stu-id="08f62-240">Click **Marketing campaigns Members** in the list.</span></span>
    
14. <span data-ttu-id="08f62-241">En la página **Personas y grupos**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-241">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="08f62-242">En el cuadro de diálogo **Compartir** , escriba **personal de Marketing**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="08f62-242">In the **Share** dialog box, type **Marketing staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="08f62-243">Repita los pasos 14 y 15 para la cuenta de usuario **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="08f62-243">Repeat steps 14 and 15 for the **Researcher1** user account.</span></span>
    
17. <span data-ttu-id="08f62-244">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="08f62-244">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="08f62-245">En la lista, haga clic en **campañas de Marketing propietarios** .</span><span class="sxs-lookup"><span data-stu-id="08f62-245">Click **Marketing campaigns Owners** in the list.</span></span>
    
19. <span data-ttu-id="08f62-246">En la página **Personas y grupos**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-246">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="08f62-247">En el cuadro de diálogo **Compartir** , escriba **el personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="08f62-247">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="08f62-248">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="08f62-248">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="08f62-249">Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **principal de campañas de Marketing** en el explorador y, a continuación, cierre el panel de **los permisos del sitio** .</span><span class="sxs-lookup"><span data-stu-id="08f62-249">Close the **People and Groups** tab in your browser, click the **Marketing campaigns-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="08f62-250">Estos son los resultados de la configuración de los permisos:</span><span class="sxs-lookup"><span data-stu-id="08f62-250">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="08f62-251">El grupo de SharePoint de **Integrantes de campañas de Marketing** contiene sólo el grupo de **campañas de Marketing** (que contiene la cuenta de usuario de administrador global), el grupo de **personal de Marketing** (que contiene el usuario Marketing1 y Marketing2 las cuentas) y la cuenta de usuario **Researcher1** .</span><span class="sxs-lookup"><span data-stu-id="08f62-251">The **Marketing campaigns-Members** SharePoint group contains only the **Marketing campaigns** group (which contains the global administrator user account), the **Marketing staff** group (which contains the Marketing1 and Marketing2 user accounts), and the **Researcher1** user account.</span></span>
    
- <span data-ttu-id="08f62-252">El grupo de SharePoint **Propietarios de las campañas de Marketing** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="08f62-252">The **Marketing campaigns-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="08f62-253">El grupo de SharePoint **Campañas de marketing-Visitantes** no contiene grupos ni cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="08f62-253">The **Marketing campaigns-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="08f62-254">Los miembros no pueden modificar los permisos de nivel de sitio (esto solo pueden hacerlo los miembros del grupo **Campañas de marketing-Propietarios**).</span><span class="sxs-lookup"><span data-stu-id="08f62-254">Members cannot modify site-level permissions (this can only be done by members of the **Marketing campaigns-Owners** group).</span></span>
    
- <span data-ttu-id="08f62-255">Otras cuentas de usuario no pueden obtener acceso a sus recursos o el sitio, pero pueden solicitar acceso al sitio, que enviará un correo electrónico al buzón de la cuenta de usuario de ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="08f62-255">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="08f62-256">Después, configure la carpeta de documentos del sitio de grupo Campañas de marketing para la etiqueta Confidencial.</span><span class="sxs-lookup"><span data-stu-id="08f62-256">Next, configure the documents folder of the Marketing campaigns team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="08f62-257">En la pestaña **Campañas de marketing-Inicio** del explorador, haga clic en **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="08f62-257">In the **Marketing campaigns-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="08f62-258">Haga clic en el icono de configuración y luego en **Configuración de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="08f62-258">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="08f62-259">En **Permisos y administración**, haga clic en **Apply label to items in this library** (Aplicar la etiqueta a los elementos de esta biblioteca).</span><span class="sxs-lookup"><span data-stu-id="08f62-259">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="08f62-260">En la **Configuración se aplica la etiqueta**, seleccione **confidencial**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-260">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="08f62-261">Luego configure una directiva de prevención de pérdida de datos (DLP) que notifique a los usuarios cada vez que compartan un documento en un sitio de grupo de SharePoint Online con la etiqueta Confidencial, que incluye el sitio Campañas de marketing, fuera de la organización.</span><span class="sxs-lookup"><span data-stu-id="08f62-261">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label, which includes the Marketing campaigns site, outside the organization.</span></span>
  
1. <span data-ttu-id="08f62-262">En la ficha **Página principal de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; cumplimiento** colocar en mosaico.</span><span class="sxs-lookup"><span data-stu-id="08f62-262">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="08f62-263">En el nuevo **seguridad &amp; cumplimiento** , haga clic en el explorador **prevención de pérdida de datos > directiva**.</span><span class="sxs-lookup"><span data-stu-id="08f62-263">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="08f62-264">En el panel **Prevención de pérdida de datos**, haga clic en **+ Crear una directiva**.</span><span class="sxs-lookup"><span data-stu-id="08f62-264">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="08f62-265">En la **empezar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-265">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="08f62-266">En el panel de **nombre de la directiva** , escriba **sitios de grupo de SharePoint Online de etiqueta confidencial** en **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-266">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="08f62-267">En el panel **Elegir ubicaciones**, haga clic para que se le **permita elegir ubicaciones concretas** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-267">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="08f62-268">En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **las cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-268">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="08f62-269">En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-269">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="08f62-270">En el panel **Elegir los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="08f62-270">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="08f62-271">En el panel de **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-271">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="08f62-272">En el panel **Choose the types of content to protect** (Elegir los tipos de contenido que se va a proteger), haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-272">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="08f62-273">En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-273">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="08f62-274">En el panel **What do you want to do if we detect sensitive info?** (¿Qué quiere hacer si se detecta información confidencial?), haga clic en **Customize the tip and email** (Personalizar la sugerencia y el correo electrónico).</span><span class="sxs-lookup"><span data-stu-id="08f62-274">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="08f62-275">En el panel **Customize policy tips and email notifications** (Personalizar sugerencias de directiva y notificaciones de correo electrónico), haga clic en **Customize the policy tip text** (Personalizar el texto de la sugerencia de directiva).</span><span class="sxs-lookup"><span data-stu-id="08f62-275">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="08f62-276">En el cuadro de texto, escriba o pegue lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="08f62-276">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="08f62-p108">Para compartir con un usuario de fuera de la organización, descargue el archivo y luego ábralo. Haga clic en Archivo, Proteger documento y Cifrar con contraseña y, luego, especifique una contraseña segura. Envíe la contraseña en un correo electrónico diferente u otro medio de comunicación.</span><span class="sxs-lookup"><span data-stu-id="08f62-p108">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="08f62-280">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-280">Click **OK**.</span></span>
    
17. <span data-ttu-id="08f62-281">En la **¿Qué desea hacer si se detecta información confidencial?** panel, desactive la casilla de verificación **Bloquear personas de uso compartido y restringir el acceso al contenido compartido** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-281">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="08f62-282">En el **¿desea activar las acciones de directiva o de prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-282">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="08f62-283">En el panel de **revisión de la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-283">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="08f62-284">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="08f62-284">Here is your resulting configuration.</span></span>
  
![Protección de nivel confidencial del sitio de grupo de SharePoint Online aislado de campañas de marketing.](images/33992bd5-96ee-4bfb-9ecf-c8a6736dd100.png)
  
### <a name="company-strategy-team-site"></a><span data-ttu-id="08f62-286">Sitio de grupo Estrategia de empresa</span><span class="sxs-lookup"><span data-stu-id="08f62-286">Company strategy team site</span></span>

<span data-ttu-id="08f62-287">Para crear un sitio de grupo aislado de SharePoint Online que tenga el nivel extremadamente confidencial para recursos estratégicos de empresa dirigido a los directores ejecutivos de la organización, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="08f62-287">To create an isolated SharePoint Online team site at the highly confidential level for strategic company resources of the chief executives of the organization, do the following:</span></span>
  
1. <span data-ttu-id="08f62-p109">Si es necesario, use un explorador en el equipo local e inicie sesión en el portal de Office 365 con la cuenta de administrador global. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).</span><span class="sxs-lookup"><span data-stu-id="08f62-p109">If needed, use a browser on your local computer and sign in to the Office 365 portal using your global administrator account. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="08f62-290">En la lista de iconos, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="08f62-290">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="08f62-291">En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.</span><span class="sxs-lookup"><span data-stu-id="08f62-291">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="08f62-292">En la página **Crear un sitio**, haga clic en **Sitio de grupo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-292">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="08f62-293">En **Team site name** (Nombre de sitio de grupo), escriba **Estrategia de empresa**.</span><span class="sxs-lookup"><span data-stu-id="08f62-293">In **Team site name**, type **Company strategy**.</span></span>
    
6. <span data-ttu-id="08f62-294">En **Team site description** (Descripción de sitio de grupo), escriba **Sitio de SharePoint para la estrategia de empresa (extremadamente confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="08f62-294">In **Team site description**, type **SharePoint site for company strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="08f62-295">En **la configuración de privacidad**, seleccione **privada - sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-295">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="08f62-296">En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-296">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="08f62-297">En la ficha nuevo de la **estrategia de la empresa** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="08f62-297">On the new **Company strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="08f62-298">En el panel **Permisos del sitio**, haga clic en **Advanced permissions settings** (Configuración de permisos avanzada).</span><span class="sxs-lookup"><span data-stu-id="08f62-298">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="08f62-299">En la nueva pestaña **Permisos** del explorador, haga clic en **Configuración de solicitud de acceso**.</span><span class="sxs-lookup"><span data-stu-id="08f62-299">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="08f62-300">En el cuadro de diálogo **Configuración de acceso de la petición** , desactive **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **Permitir miembros para invitar a otras personas al grupo de miembros del sitio** (de manera que se desactivan todas las casillas de verificación tres) y, a continuación, haga clic en ** Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-300">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="08f62-301">Haga clic en **la estrategia de la empresa (miembros de)** en la lista.</span><span class="sxs-lookup"><span data-stu-id="08f62-301">Click **Company strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="08f62-302">En la página **Personas y grupos**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-302">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="08f62-303">En el cuadro de diálogo **Compartir** , escriba **C-Suite**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="08f62-303">In the **Share** dialog box, type **C-Suite**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="08f62-304">En la lista, haga clic en **estrategia los propietarios de la empresa** .</span><span class="sxs-lookup"><span data-stu-id="08f62-304">Click **Company strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="08f62-305">En la página **Personas y grupos**, haga clic en **Nuevo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-305">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="08f62-306">En el cuadro de diálogo **Compartir** , escriba **el personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="08f62-306">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="08f62-307">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="08f62-307">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="08f62-308">Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **Página principal de estrategia de la empresa** en el explorador y, a continuación, cierre el panel de **los permisos del sitio** .</span><span class="sxs-lookup"><span data-stu-id="08f62-308">Close the **People and Groups** tab in your browser, click the **Company strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="08f62-309">Estos son los resultados de la configuración de los permisos:</span><span class="sxs-lookup"><span data-stu-id="08f62-309">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="08f62-310">El grupo de SharePoint de la **Estrategia de la empresa: los miembros** contiene sólo el grupo de **Conjunto de aplicaciones de C** (que contiene sólo las cuentas de usuario consejero Delegado, director financiero y director) y el grupo de **estrategia de la empresa** (que contiene sólo la cuenta de usuario de administrador global).</span><span class="sxs-lookup"><span data-stu-id="08f62-310">The **Company strategy-Members** SharePoint group contains only the **C-Suite** group (which contains only the CEO, CFO, and CIO user accounts) and the **Company strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="08f62-311">El grupo de SharePoint **Propietarios de estrategia de compañía** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="08f62-311">The **Company strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="08f62-312">El grupo de SharePoint **Estrategia de empresa-Visitantes** no contiene grupos ni cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="08f62-312">The **Company strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="08f62-313">Los miembros no pueden modificar los permisos de nivel de sitio (esto solo pueden hacerlo los miembros del grupo **Estrategia de empresa-Propietarios**).</span><span class="sxs-lookup"><span data-stu-id="08f62-313">Members cannot modify site-level permissions (this can only be done by members of the **Company strategy-Owners** group).</span></span>
    
- <span data-ttu-id="08f62-p110">Otras cuentas de usuario no pueden acceder al sitio o a sus recursos ni pedir acceso al sitio. Los permisos adicionales para el sitio deben ser asignados por el administrador global o por un miembro del grupo **Estrategia de empresa-Propietarios**.</span><span class="sxs-lookup"><span data-stu-id="08f62-p110">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Company strategy-Owners** group.</span></span>
    
<span data-ttu-id="08f62-316">Después, configure la carpeta de documentos del sitio de grupo Estrategia de empresa para la etiqueta Extremadamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="08f62-316">Next, configure the documents folder of the Company strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="08f62-317">En la pestaña **Estrategia de empresa-Inicio** del explorador, haga clic en **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="08f62-317">In the **Company strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="08f62-318">Haga clic en el icono de configuración y luego en **Configuración de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="08f62-318">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="08f62-319">En **Permisos y administración**, haga clic en **Apply label to items in this library** (Aplicar la etiqueta a los elementos de esta biblioteca).</span><span class="sxs-lookup"><span data-stu-id="08f62-319">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="08f62-320">En la **Configuración se aplica la etiqueta**, seleccione **Altamente confidencial**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-320">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="08f62-321">Después, configure una directiva de DLP que impida a los usuarios compartir un documento en un sitio de grupo de SharePoint Online con la etiqueta Extremadamente confidencial, que incluye el sitio Estrategia de empresa, fuera de la organización.</span><span class="sxs-lookup"><span data-stu-id="08f62-321">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label, which includes the Company strategy site, outside the organization.</span></span>
  
1. <span data-ttu-id="08f62-p111">Si es necesario, use un explorador en su equipo local e inicie sesión el portal de Office 365 con una cuenta que tenga el rol de administrador de seguridad o administrador de la compañía. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="08f62-p111">If needed, use a browser on your local computer and sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="08f62-324">En la ficha **Página principal de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; cumplimiento** colocar en mosaico.</span><span class="sxs-lookup"><span data-stu-id="08f62-324">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="08f62-325">En el nuevo **seguridad &amp; cumplimiento** , haga clic en el explorador **prevención de pérdida de datos > directiva**.</span><span class="sxs-lookup"><span data-stu-id="08f62-325">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="08f62-326">En el panel **Prevención de pérdida de datos**, haga clic en **+ Crear una directiva**.</span><span class="sxs-lookup"><span data-stu-id="08f62-326">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="08f62-327">En la **empezar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-327">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="08f62-328">En el panel de **nombre de la directiva** , escriba **altamente confidencial sitios de grupo de SharePoint Online etiqueta** en **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-328">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="08f62-329">En el panel **Elegir ubicaciones**, haga clic para que se le **permita elegir ubicaciones concretas** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-329">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="08f62-330">En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **las cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-330">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="08f62-331">En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-331">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="08f62-332">En el panel **Elegir los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="08f62-332">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="08f62-333">En el panel de **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **Altamente confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="08f62-333">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="08f62-334">En el panel **Choose the types of content to protect** (Elegir los tipos de contenido que se va a proteger), haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-334">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="08f62-335">En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-335">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="08f62-336">En el panel **What do you want to do if we detect sensitive info?** (¿Qué quiere hacer si se detecta información confidencial?), haga clic en **Customize the tip and email** (Personalizar la sugerencia y el correo electrónico).</span><span class="sxs-lookup"><span data-stu-id="08f62-336">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="08f62-337">En el panel **Customize policy tips and email notifications** (Personalizar sugerencias de directiva y notificaciones de correo electrónico), haga clic en **Customize the policy tip text** (Personalizar el texto de la sugerencia de directiva).</span><span class="sxs-lookup"><span data-stu-id="08f62-337">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="08f62-338">En el cuadro de texto, escriba o pegue lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="08f62-338">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="08f62-p112">Para compartir con un usuario de fuera de la organización, descargue el archivo y luego ábralo. Haga clic en Archivo, Proteger documento y Cifrar con contraseña y, luego, especifique una contraseña segura. Envíe la contraseña en un correo electrónico diferente u otro medio de comunicación.</span><span class="sxs-lookup"><span data-stu-id="08f62-p112">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="08f62-342">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-342">Click **OK**.</span></span>
    
18. <span data-ttu-id="08f62-343">En la **¿Qué desea hacer si se detecta información confidencial?** panel, seleccione **requerir una justificación comercial para reemplazar**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-343">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="08f62-344">En el **¿desea activar las acciones de directiva o de prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="08f62-344">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="08f62-345">En el panel de **revisión de la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-345">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="08f62-346">Luego siga las instrucciones de [Activación de Azure Rights Management desde el Centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="08f62-346">Next, follow the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="08f62-347">A continuación, siga estos pasos para configurar Azure Information Protection con una nueva directiva de ámbito y la etiqueta secundaria para la protección y permisos:</span><span class="sxs-lookup"><span data-stu-id="08f62-347">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="08f62-p113">Inicie sesión el portal de Office 365 con una cuenta que tenga el rol de administrador de seguridad o administrador de la compañía. Para obtener ayuda, consulte [Where iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="08f62-p113">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="08f62-350">En una ficha independiente del explorador, vaya al portal de Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="08f62-350">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="08f62-351">Si se trata de la primera vez que se va a configurar la protección de la información de Azure, vea estas [instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="08f62-351">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="08f62-352">En el panel de lista, haga clic en **todos los servicios**, escriba la **información**y, a continuación, haga clic en **Protección de la información de Azure**.</span><span class="sxs-lookup"><span data-stu-id="08f62-352">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="08f62-353">En el servidor blade de **protección de la información de Azure** , haga clic en **con ámbito de directivas > + Agregar una nueva directiva de**.</span><span class="sxs-lookup"><span data-stu-id="08f62-353">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="08f62-354">Escriba **EstrategiaEmpresa** en **Nombre de la directiva** y **Etiqueta para los documentos del sitio de grupo Estrategia de empresa** en **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="08f62-354">Type **CompanyStrategy** in **Policy name** and **Label for documents in the Company strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="08f62-355">Haga clic en **Seleccionar a qué usuarios o grupos se aplica esta directiva > Usuarios o grupos** y seleccione **C-Suite**.</span><span class="sxs-lookup"><span data-stu-id="08f62-355">Click **Select which users or groups get this policy > User/Groups**, and then select **C-Suite**.</span></span>
    
8. <span data-ttu-id="08f62-356">Haga clic en **Seleccionar > Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-356">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="08f62-357">Para la etiqueta **Extremadamente confidencial**, haga clic en el botón de puntos suspensivos (...) y, luego, en **Agregar una subetiqueta**.</span><span class="sxs-lookup"><span data-stu-id="08f62-357">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="08f62-358">Escriba un nombre para la subetiqueta en **Nombre** y una descripción en **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="08f62-358">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="08f62-359">En **Establecer permisos para documentos y correos electrónicos que contengan esta etiqueta**, haga clic en **Proteger**.</span><span class="sxs-lookup"><span data-stu-id="08f62-359">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="08f62-360">En la sección **Protección**, haga clic en **Azure (clave de nube)**.</span><span class="sxs-lookup"><span data-stu-id="08f62-360">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="08f62-361">En la hoja **Protección**, en **Configuración de protección**, haga clic en **+ Agregar permisos**.</span><span class="sxs-lookup"><span data-stu-id="08f62-361">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="08f62-362">En la hoja **Agregar permisos**, en **Especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.</span><span class="sxs-lookup"><span data-stu-id="08f62-362">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="08f62-363">En el panel de **AAD usuarios y grupos** , seleccione el **Conjunto de aplicaciones de C**y, a continuación, haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-363">On the **AAD Users and Groups** pane, select **C-Suite**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="08f62-364">En **elija permisos del ajuste preestablecido**, desactive las casillas de verificación **Imprimir**, **Copiar y extraer contenido**y **hacia delante** .</span><span class="sxs-lookup"><span data-stu-id="08f62-364">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="08f62-365">Haga clic en **Aceptar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="08f62-365">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="08f62-366">En la hoja **Subetiqueta**, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="08f62-366">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="08f62-367">Cierre la hoja de directiva en la que acaba de agregar el ámbito.</span><span class="sxs-lookup"><span data-stu-id="08f62-367">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="08f62-368">En el servidor blade de **protección de la información de Azure - las directivas de ámbito** , haga clic en **Publicar**y, a continuación, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="08f62-368">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="08f62-369">Para proteger un documento con la protección de la información de Azure y esta nueva etiqueta, debe [instalar al cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en un equipo de prueba, instalar Office desde el portal de Office 365 y, a continuación, iniciar sesión en desde Microsoft Word con una cuenta en el ** Conjunto de aplicaciones de C** grupo de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="08f62-369">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **C-Suite** group of your trial subscription.</span></span>
  
<span data-ttu-id="08f62-370">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="08f62-370">Here is your resulting configuration.</span></span>
  
![Protección de nivel alto de confidencialidad de un sitio de grupo de SharePoint Online aislado de estrategia de empresa.](images/c22695f9-50a1-4abf-a0dd-344b0c92cf94.png)
  
<span data-ttu-id="08f62-372">Ahora está listo para crear documentos en estos cuatro sitios y probar el acceso a ellos con diferentes cuentas de usuario de la suscripción de evaluación.</span><span class="sxs-lookup"><span data-stu-id="08f62-372">You are now ready to create documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span>
  
<span data-ttu-id="08f62-373">Esta es la configuración global de los cuatro sitios de grupo de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="08f62-373">Here is the overall configuration for all four SharePoint Online team sites.</span></span>
  
![Los cuatro sitios de grupo del entorno de pruebas y desarrollo de SharePoint Online seguro.](images/b0fea489-359c-4c85-a0ad-e4efb4a1e47f.png)
  
## <a name="next-step"></a><span data-ttu-id="08f62-375">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="08f62-375">Next step</span></span>

<span data-ttu-id="08f62-376">Cuando esté listo para la implementación en producción de sitios seguros de SharePoint Online, vea [Protección de archivos y sitios de SharePoint Online](secure-sharepoint-online-sites-and-files.md) para obtener información detallada y vínculos a artículos de implementación paso a paso.</span><span class="sxs-lookup"><span data-stu-id="08f62-376">When you are ready for production deployment of secure SharePoint Online sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md) for detailed information and links to step-by-step deployment articles.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="08f62-377">Consulte también</span><span class="sxs-lookup"><span data-stu-id="08f62-377">See Also</span></span>

[<span data-ttu-id="08f62-378">Protección de archivos y sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="08f62-378">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="08f62-379">Soluciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="08f62-379">Security solutions</span></span>](security-solutions.md)
  
[<span data-ttu-id="08f62-380">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="08f62-380">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)
  
[<span data-ttu-id="08f62-381">Instrucciones de seguridad de Microsoft para campañas políticas, organizaciones sin ánimo de lucro y otras organizaciones ágiles</span><span class="sxs-lookup"><span data-stu-id="08f62-381">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)




