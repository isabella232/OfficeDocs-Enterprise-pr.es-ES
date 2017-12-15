---
title: Entorno de pruebas y desarrollo de SharePoint Online team sitio aislado
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- TLG
- Ent_TLGs
ms.assetid: d1795031-beef-49ea-a6fc-5da5450d320d
description: "Resumen: Configurar un sitio de grupo SharePoint Online que está aislado del resto de la organización en su entorno de pruebas y desarrollo de Office 365."
ms.openlocfilehash: a5e36060ed54213f555ab75a1d4ace7300b7667c
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="isolated-sharepoint-online-team-site-devtest-environment"></a><span data-ttu-id="14447-103">Entorno de pruebas y desarrollo de SharePoint Online team sitio aislado</span><span class="sxs-lookup"><span data-stu-id="14447-103">Isolated SharePoint Online team site dev/test environment</span></span>

 <span data-ttu-id="14447-104">**Resumen:** Configurar un sitio de grupo SharePoint Online que está aislado del resto de la organización en su entorno de pruebas y desarrollo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="14447-104">**Summary:** Configure a SharePoint Online team site that is isolated from the rest of the organization in your Office 365 dev/test environment.</span></span>
  
<span data-ttu-id="14447-p101">Sitios de equipo de SharePoint Online en Office 365 son ubicaciones para la colaboración mediante una biblioteca de documentos comunes, un bloc de notas de OneNote y otros servicios. En muchos casos, desea amplio acceso y la colaboración entre departamentos y organizaciones. Sin embargo, en algunos casos, desea controlar rigurosamente el acceso y los permisos para la colaboración entre un pequeño grupo de personas.</span><span class="sxs-lookup"><span data-stu-id="14447-p101">SharePoint Online team sites in Office 365 are locations for collaboration using a common document library, a OneNote notebook, and other services. In many cases, you want wide access and collaboration across departments or organizations. However, in some cases, you want to tightly control the access and permissions for collaboration among a small group of people.</span></span>
  
<span data-ttu-id="14447-p102">Acceso a sitios de equipo de SharePoint Online y qué pueden hacer los usuarios se controla mediante grupos de SharePoint y los niveles de permisos. De forma predeterminada, los sitios de SharePoint Online tienen tres niveles de acceso:</span><span class="sxs-lookup"><span data-stu-id="14447-p102">Access to SharePoint Online team sites and what users can do is controlled by SharePoint groups and permission levels. By default, SharePoint Online sites have three levels of access:</span></span>
  
- <span data-ttu-id="14447-110">**Miembros**, que puede ver, crear y modificar los recursos en el sitio.</span><span class="sxs-lookup"><span data-stu-id="14447-110">**Members**, who can view, create, and modify resources on the site.</span></span>
    
- <span data-ttu-id="14447-111">**Los propietarios**, que tiene el control total del sitio, incluida la capacidad para cambiar los permisos.</span><span class="sxs-lookup"><span data-stu-id="14447-111">**Owners**, who have complete control of the site, including the ability to change permissions.</span></span>
    
- <span data-ttu-id="14447-112">**Los visitantes**, que sólo puede ver los recursos en el sitio.</span><span class="sxs-lookup"><span data-stu-id="14447-112">**Visitors**, who only can view resources on the site.</span></span>
    
<span data-ttu-id="14447-p103">En este artículo pasos es a través de la configuración de un sitio de grupo de SharePoint Online aislado para un proyecto de investigación secreta denominan ProjectX. Los requisitos de acceso son:</span><span class="sxs-lookup"><span data-stu-id="14447-p103">This article steps you through the configuration of an isolated SharePoint Online team site for a secret research project named ProjectX. The access requirements are:</span></span>
  
- <span data-ttu-id="14447-115">Solo los miembros del proyecto pueden acceder al sitio y a su contenido (documentos, Bloc de notas de OneNote y páginas), con niveles de permiso de SharePoint de edición y visualización controlados a través de la pertenencia al grupo.</span><span class="sxs-lookup"><span data-stu-id="14447-115">Only members of the project can access the site and its contents (documents, OneNote Notebook, Pages), with edit and view SharePoint permission levels controlled through group membership.</span></span>
    
- <span data-ttu-id="14447-116">Únicamente el creador del sitio y los miembros de un grupo de administradores del sitio pueden llevar a cabo tareas relacionadas con la administración, lo que incluye la modificación de los permisos del sitio.</span><span class="sxs-lookup"><span data-stu-id="14447-116">Only the site creator and members of an Admins group for the site can perform site administration, which includes modifying site-level permissions.</span></span>
    
<span data-ttu-id="14447-117">La configuración de un sitio de grupo de SharePoint Online aislado en su entorno para desarrollo y pruebas de Office 365 se divide en tres fases:</span><span class="sxs-lookup"><span data-stu-id="14447-117">There are three phases to setting up an isolated SharePoint Online team site in your Office 365 dev/test environment:</span></span>
  
1. <span data-ttu-id="14447-118">Crear el entorno de desarrollo y pruebas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="14447-118">Create the Office 365 dev/test environment.</span></span>
    
2. <span data-ttu-id="14447-119">Crear los usuarios y los grupos de ProyectoX.</span><span class="sxs-lookup"><span data-stu-id="14447-119">Create the users and groups for ProjectX.</span></span>
    
3. <span data-ttu-id="14447-120">Crear un sitio de grupo de SharePoint Online para ProyectoX y aislarlo.</span><span class="sxs-lookup"><span data-stu-id="14447-120">Create a new ProjectX SharePoint Online team site and isolate it.</span></span>
    
> [!TIP]
> <span data-ttu-id="14447-121">Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual para todos los artículos de la pila de una guía de laboratorio de prueba de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="14447-121">Click [here](http://aka.ms/catlgstack) for a visual map to all the articles in the One Microsoft Cloud Test Lab Guide stack.</span></span>
  
## <a name="phase-1-build-out-your-lightweight-or-simulated-enterprise-office-365-devtest-environment"></a><span data-ttu-id="14447-122">Fase 1: Crear un entorno de desarrollo y pruebas ligero o de una empresa simulada de Office 365</span><span class="sxs-lookup"><span data-stu-id="14447-122">Phase 1: Build out your lightweight or simulated enterprise Office 365 dev/test environment</span></span>

<span data-ttu-id="14447-123">Si desea crear un sitio de grupo SharePoint Online aislado de una manera ligera con los requisitos mínimos, siga las instrucciones que aparecen en las fases 2 y 3 del [entorno de desarrollo y prueba de Office 365](office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="14447-123">If you just want to create an isolated SharePoint Online team site in a lightweight way with the minimum requirements, follow the instructions in phases 2 and 3 of [Office 365 dev/test environment](office-365-dev-test-environment.md).</span></span>
  
<span data-ttu-id="14447-124">Si desea crear un sitio de grupo SharePoint Online aislado en una configuración de empresa simulada, siga las instrucciones de [sincronización de directorios para el entorno de desarrollo y prueba de Office 365](dirsync-for-your-office-365-dev-test-environment.md).</span><span class="sxs-lookup"><span data-stu-id="14447-124">If you want to create an isolated SharePoint Online team site in a simulated enterprise configuration, follow the instructions in [DirSync for your Office 365 dev/test environment](dirsync-for-your-office-365-dev-test-environment.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="14447-p104">Crear un sitio de SharePoint Online aislado no requiere un entorno para desarrollo y pruebas empresarial simulado que incluya una intranet simulada conectada a Internet y una sincronización de directorios para un bosque de Windows Server AD. Se proporciona aquí como opción para que pueda probar un sitio de SharePoint Online aislado y experimentar con él en un entorno que representa una organización típica.</span><span class="sxs-lookup"><span data-stu-id="14447-p104">Creating an isolated SharePoint Online site does not require the simulated enterprise dev/test environment, which includes a simulated intranet connected to the Internet and directory synchronization for a Windows Server AD forest. It is provided here as an option so that you can test an isolated SharePoint Online site and experiment with it in an environment that represents a typical organization.</span></span> 
  
## <a name="phase-2-create-user-accounts-and-access-groups"></a><span data-ttu-id="14447-127">Fase 2: Crear cuentas de usuario y tener acceso a los grupos</span><span class="sxs-lookup"><span data-stu-id="14447-127">Phase 2: Create user accounts and access groups</span></span>

<span data-ttu-id="14447-128">Siga las instrucciones de [conectarse a Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) para conectarse a su suscripción de rastro de Office 365 con la cuenta de administrador global desde:</span><span class="sxs-lookup"><span data-stu-id="14447-128">Use the instructions in [Connect to Office 365 PowerShell](https://technet.microsoft.com/library/dn975125.aspx) to connect to your Office 365 trail subscription with your global administrator account from:</span></span>
  
- <span data-ttu-id="14447-129">Su equipo (para el entorno de desarrollo y pruebas ligero de Office 365).</span><span class="sxs-lookup"><span data-stu-id="14447-129">Your computer (for the lightweight Office 365 dev/test environment).</span></span>
    
- <span data-ttu-id="14447-130">La máquina virtual CLIENT1 (para el entorno de desarrollo y pruebas de una empresa simulada de Office 365).</span><span class="sxs-lookup"><span data-stu-id="14447-130">The CLIENT1 virtual machine (for the simulated enterprise Office 365 dev/test environment).</span></span>
    
<span data-ttu-id="14447-131">Para crear los nuevos grupos de acceso para el sitio de equipo ProjectX SharePoint Online, ejecutar estos comandos desde el símbolo del sistema de Windows Azure Active Directory módulo para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="14447-131">To create the new access groups for the ProjectX SharePoint Online team site, run these commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$groupName="ProjectX-Members"
$groupDesc="People allowed to collaborate for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Admins"
$groupDesc="People allowed to administer SharePoint for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
$groupName="ProjectX-Viewers"
$groupDesc="People allowed to view the SharePoint resources for ProjectX."
New-MsolGroup -DisplayName $groupName -Description $groupDesc
```

> [!TIP]
> <span data-ttu-id="14447-132">Haga clic [aquí](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) para un archivo de texto que contiene todos los comandos de PowerShell en este artículo.</span><span class="sxs-lookup"><span data-stu-id="14447-132">Click [here](https://gallery.technet.microsoft.com/PowerShell-commands-for-an-b2608df1) for a text file that contains all of the PowerShell commands in this article.</span></span>
  
<span data-ttu-id="14447-133">Rellene el nombre de la organización (ejemplo: contosotoycompany), el código de país de dos caracteres para su ubicación y, después, ejecute los comandos siguientes desde el símbolo del sistema de Módulo Microsoft Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="14447-133">Fill in your organization name (example: contosotoycompany), the two-character country code for your location, and then run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$licAssignment= $orgName + ":ENTERPRISEPREMIUM"
$userName= "designer@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Designer" -FirstName Lead -LastName Designer -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="14447-134">En la pantalla del comando **MsolUser de nuevo** , anote la contraseña para la cuenta de plomo diseñador generada y grabarlo en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="14447-134">From the display of the **New-MsolUser** command, note the generated password for the Lead Designer account and record it in a safe location.</span></span>
  
<span data-ttu-id="14447-135">Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="14447-135">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "researcher@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Lead Researcher" -FirstName Lead -LastName Researcher -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="14447-136">En la pantalla del comando **MsolUser de nuevo** , anote la contraseña para la cuenta de cliente potencial investigador generada y grabarlo en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="14447-136">From the display of the **New-MsolUser** command, note the generated password for the Lead Researcher account and record it in a safe location.</span></span>
  
<span data-ttu-id="14447-137">Ejecute los siguientes comandos desde el símbolo del sistema del Módulo de Windows Azure Active Directory para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="14447-137">Run the following commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$userName= "devvp@" + $orgName + ".onmicrosoft.com"
New-MsolUser -DisplayName "Development VP" -FirstName Development -LastName VP -UserPrincipalName $userName -UsageLocation $loc -LicenseAssignment $licAssignment -ForceChangePassword $false
```

<span data-ttu-id="14447-138">En la pantalla del comando **MsolUser de nuevo** , tenga en cuenta la contraseña generada para la cuenta de Vicepresidente de desarrollo y grabarlo en un lugar seguro.</span><span class="sxs-lookup"><span data-stu-id="14447-138">From the display of the **New-MsolUser** command, note the generated password for the Development VP account and record it in a safe location.</span></span>
  
<span data-ttu-id="14447-139">A continuación, para agregar las cuentas nuevas a los nuevos grupos de acceso, ejecute estos comandos de PowerShell desde el símbolo del sistema de Windows Azure Active Directory módulo para Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="14447-139">Next, to add the new accounts to the new access groups, run these PowerShell commands from the Windows Azure Active Directory Module for Windows PowerShell prompt:</span></span>
  
```
$grpName="ProjectX-Members"
$userUPN="designer@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$userUPN="researcher@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Admins"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userCredential.UserName }).ObjectID -GroupMemberType "User"
$grpName="ProjectX-Viewers"
$userUPN="devvp@" + $orgName + ".onmicrosoft.com"
Add-MsolGroupMember -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $grpName }).ObjectID -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupMemberType "User"
```

<span data-ttu-id="14447-140">Resultados:</span><span class="sxs-lookup"><span data-stu-id="14447-140">Results:</span></span>
  
- <span data-ttu-id="14447-141">El grupo de acceso de miembros de ProjectX contiene las cuentas de usuario del Diseñador de plomo y el investigador de plomo</span><span class="sxs-lookup"><span data-stu-id="14447-141">The ProjectX-Members access group contains the Lead Designer and Lead Researcher user accounts</span></span>
    
- <span data-ttu-id="14447-142">El grupo de acceso de administradores de ProjectX contiene la cuenta de administrador global para la suscripción de prueba</span><span class="sxs-lookup"><span data-stu-id="14447-142">The ProjectX-Admins access group contains the global administrator account for your trial subscription</span></span>
    
- <span data-ttu-id="14447-143">El grupo de acceso de ProjectX visores contiene la cuenta de usuario de Vicepresidente de desarrollo</span><span class="sxs-lookup"><span data-stu-id="14447-143">The ProjectX-Viewers access group contains the Development VP user account</span></span>
    
<span data-ttu-id="14447-144">La figura 1 muestra los grupos de acceso y su pertenencia.</span><span class="sxs-lookup"><span data-stu-id="14447-144">Figure 1 shows the access groups and their membership.</span></span>
  
<span data-ttu-id="14447-145">**Figura 1**</span><span class="sxs-lookup"><span data-stu-id="14447-145">**Figure 1**</span></span>

![Los grupos de Office 365 y su pertenencia a un sitio de grupo de SharePoint Online aislado](images/5b7373b9-2a80-4880-afe5-63ffb17237e6.png)
  
## <a name="phase-3-create-a-new-projectx-sharepoint-online-team-site-and-isolate-it"></a><span data-ttu-id="14447-147">Fase 3: Crear un sitio de grupo de SharePoint Online para ProyectoX y aislarlo</span><span class="sxs-lookup"><span data-stu-id="14447-147">Phase 3: Create a new ProjectX SharePoint Online team site and isolate it</span></span>

<span data-ttu-id="14447-148">Para crear un sitio de grupo de SharePoint Online para ProyectoX, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="14447-148">To create a SharePoint Online team site for ProjectX, do the following:</span></span>
  
1. <span data-ttu-id="14447-149">Con un navegador desde cualquiera del equipo local (configuración ligero) o en CLIENTE1 (configuración de empresa simulada), inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) mediante la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="14447-149">Using a browser on either your local computer (lightweight configuration) or on CLIENT1 (simulated enterprise configuration), sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="14447-150">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="14447-150">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="14447-151">En la ficha nuevo de SharePoint en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="14447-151">On the new SharePoint tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="14447-p105">En **nombre de sitio de equipo**, escriba **ProjectX**. En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**.</span><span class="sxs-lookup"><span data-stu-id="14447-p105">In **Team site name**, type **ProjectX**. In **Privacy settings**, select **Private - only members can access this site**.</span></span>
    
5. <span data-ttu-id="14447-154">En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para ProjectX**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="14447-154">In **Team site description**, type **SharePoint site for ProjectX**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="14447-155">¿En la **que desea agregar**? panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="14447-155">On the **Who do you want to add**? pane, click **Finish**.</span></span>
    
7. <span data-ttu-id="14447-156">En la nueva ficha de **Inicio de ProjectX** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="14447-156">On the new **ProjectX-Home** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
8. <span data-ttu-id="14447-157">En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.</span><span class="sxs-lookup"><span data-stu-id="14447-157">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
9. <span data-ttu-id="14447-158">En el nuevo **permisos: proyecto X** ficha en el explorador, haga clic en **Configuración de solicitud de acceso**.</span><span class="sxs-lookup"><span data-stu-id="14447-158">In the new **Permissions: Project X** tab in your browser, click **Access Request Settings**.</span></span>
    
10. <span data-ttu-id="14447-159">En el cuadro de diálogo **Configuración de las solicitudes de acceso** , desactive **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **Permitir las solicitudes de acceso** (de modo que todas las casillas de verificación está desactivadas) y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="14447-159">In the **Access Requests Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow access requests** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
11. <span data-ttu-id="14447-160">En la lista, haga clic en **Miembros de ProjectX** .</span><span class="sxs-lookup"><span data-stu-id="14447-160">Click **ProjectX Members** in the list.</span></span>
    
12. <span data-ttu-id="14447-161">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="14447-161">On the **People and Groups** page, click **New**.</span></span>
    
13. <span data-ttu-id="14447-162">En el cuadro de diálogo **Compartir** , **ProjectX miembros**de tipo, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="14447-162">In the **Share** dialog box, type **ProjectX-Members**, select it, and then click **Share**.</span></span>
    
14. <span data-ttu-id="14447-163">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="14447-163">Click the back button on your browser.</span></span>
    
15. <span data-ttu-id="14447-164">En la lista, haga clic en **Propietarios de ProjectX** .</span><span class="sxs-lookup"><span data-stu-id="14447-164">Click **ProjectX Owners** in the list.</span></span>
    
16. <span data-ttu-id="14447-165">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="14447-165">On the **People and Groups** page, click **New**.</span></span>
    
17. <span data-ttu-id="14447-166">En el cuadro de diálogo **Compartir** , escriba **Administradores de ProjectX**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="14447-166">In the **Share** dialog box, type **ProjectX-Admins**, select it, and then click **Share**.</span></span>
    
18. <span data-ttu-id="14447-167">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="14447-167">Click the back button on your browser.</span></span>
    
19. <span data-ttu-id="14447-168">En la lista, haga clic en **ProjectX a los visitantes** .</span><span class="sxs-lookup"><span data-stu-id="14447-168">Click **ProjectX Visitors** in the list.</span></span>
    
20. <span data-ttu-id="14447-169">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="14447-169">On the **People and Groups** page, click **New**.</span></span>
    
21. <span data-ttu-id="14447-170">En el cuadro de diálogo **Compartir** , escriba **ProjectX visores**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="14447-170">In the **Share** dialog box, type **ProjectX-Viewers**, select it, and then click **Share**.</span></span>
    
22. <span data-ttu-id="14447-171">Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **Inicio de ProjectX** en el explorador y, a continuación, cierre el panel de **permisos del sitio** .</span><span class="sxs-lookup"><span data-stu-id="14447-171">Close the **People and Groups** tab in your browser, click the **ProjectX-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="14447-172">A continuación se indican los resultados de la configuración de permisos:</span><span class="sxs-lookup"><span data-stu-id="14447-172">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="14447-173">El grupo de SharePoint miembros de ProjectX contiene sólo el grupo de acceso de miembros de ProjectX (que contiene sólo las cuentas de usuario Diseñador de plomo y plomo investigador) y el grupo de ProjectX (que contiene sólo la cuenta de usuario de administrador global).</span><span class="sxs-lookup"><span data-stu-id="14447-173">The ProjectX Members SharePoint group contains only the ProjectX-Members access group (which contains only the Lead Designer and Lead Researcher user accounts) and the ProjectX group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="14447-174">El grupo de SharePoint propietarios de ProjectX contiene sólo el grupo de acceso de administradores de ProjectX (que contiene sólo la cuenta de usuario de administrador global).</span><span class="sxs-lookup"><span data-stu-id="14447-174">The ProjectX Owners SharePoint group contains only the ProjectX-Admins access group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="14447-175">El grupo de SharePoint visitantes de ProjectX contiene sólo el grupo de acceso de ProjectX visores (que contiene sólo la cuenta de usuario de Vicepresidente de desarrollo).</span><span class="sxs-lookup"><span data-stu-id="14447-175">The ProjectX Visitors SharePoint group contains only the ProjectX-Viewers access group (which contains only the Development VP user account).</span></span>
    
- <span data-ttu-id="14447-176">Los miembros no pueden modificar los permisos del nivel del sitio (solo los miembros del grupo “Administradores del ProyectoX” pueden realizar esta acción).</span><span class="sxs-lookup"><span data-stu-id="14447-176">Members cannot modify site-level permissions (this can only be done by members of the ProjectX-Admins group).</span></span>
    
- <span data-ttu-id="14447-177">El resto de cuentas de usuario no pueden tener acceso al sitio ni a sus recursos, y tampoco pueden solicitar acceso al sitio.</span><span class="sxs-lookup"><span data-stu-id="14447-177">Other user accounts cannot access the site or its resources or request access to the site.</span></span>
    
<span data-ttu-id="14447-178">En la figura 2 se muestran los grupos de SharePoint y su pertenencia.</span><span class="sxs-lookup"><span data-stu-id="14447-178">Figure 2 shows the SharePoint groups and their membership.</span></span>
  
<span data-ttu-id="14447-179">**Figura 2**</span><span class="sxs-lookup"><span data-stu-id="14447-179">**Figure 2**</span></span>

![Los grupos de SharePoint Online y su pertenencia a un sitio de grupo de SharePoint Online aislado](images/595abff4-64f9-49de-a37a-c70c6856936b.png)
  
<span data-ttu-id="14447-181">Ahora vamos a demostrar el acceso utilizando la cuenta de usuario del Diseñador de plomo:</span><span class="sxs-lookup"><span data-stu-id="14447-181">Now let's demonstrate access using the Lead Designer user account:</span></span>
  
1. <span data-ttu-id="14447-182">Cierre la ficha **Inicio de ProjectX** en el explorador y, a continuación, haga clic en la ficha **Página de inicio de Microsoft Office** en el explorador.</span><span class="sxs-lookup"><span data-stu-id="14447-182">Close the **ProjectX-Home** tab in your browser, and then click the **Microsoft Office Home** tab in your browser.</span></span>
    
2. <span data-ttu-id="14447-183">Haga clic en el nombre de su administrador global y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="14447-183">Click the name of your global administrator, and then click **Sign out**.</span></span>
    
3. <span data-ttu-id="14447-184">Iniciar sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) con el nombre de cuenta de Lead Designer y su contraseña.</span><span class="sxs-lookup"><span data-stu-id="14447-184">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Lead Designer account name and its password.</span></span>
    
4. <span data-ttu-id="14447-185">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="14447-185">In the list of tiles, click **SharePoint**.</span></span>
    
5. <span data-ttu-id="14447-p106">En la ficha nuevo de **SharePoint** en el explorador, escriba **ProjectX** en el cuadro de búsqueda, activar la búsqueda y, a continuación, haga clic en el sitio del equipo **ProjectX** . Debería ver una nueva pestaña en el explorador del sitio de grupo ProjectX.</span><span class="sxs-lookup"><span data-stu-id="14447-p106">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
6. <span data-ttu-id="14447-p107">Haga clic en el icono Configuración. Observe que no hay ninguna opción para **Permisos del sitio**. Esto es correcto, ya que sólo los miembros del grupo Administradores de ProjectX pueden modificar los permisos en el sitio</span><span class="sxs-lookup"><span data-stu-id="14447-p107">Click the settings icon. Notice that there is no option for **Site Permissions**. This is correct because only the members of the ProjectX-Admins group can modify permissions on the site</span></span>
    
7. <span data-ttu-id="14447-191">Abra el Bloc de notas o el editor de texto que prefiera.</span><span class="sxs-lookup"><span data-stu-id="14447-191">Open Notepad or a text editor of your choice.</span></span>
    
8. <span data-ttu-id="14447-192">Copie la dirección URL del sitio de grupo de ProyectoX y péguela en una nueva línea del Bloc de notas o su editor de texto.</span><span class="sxs-lookup"><span data-stu-id="14447-192">Copy the URL of the ProjectX team site and paste it on a new line in Notepad or your text editor.</span></span>
    
9. <span data-ttu-id="14447-193">En la nueva ficha de **Inicio de ProjectX** en el explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="14447-193">On the new **ProjectX-Home** tab in your browser, click **Documents**.</span></span>
    
10. <span data-ttu-id="14447-194">Copie la dirección URL de la carpeta de documentos del ProyectoX y péguela en una nueva línea del Bloc de notas o del editor de texto.</span><span class="sxs-lookup"><span data-stu-id="14447-194">Copy the URL of the ProjectX documents folder and paste it on a new line in Notepad or your text editor.</span></span>
    
11. <span data-ttu-id="14447-195">En la nueva ficha de **ProjectX documentos** en el explorador, haga clic en **Nuevo > documento de Word**.</span><span class="sxs-lookup"><span data-stu-id="14447-195">On the new **ProjectX-Documents** tab in your browser, click **New > Word document**.</span></span>
    
12. <span data-ttu-id="14447-p108">Escriba algún texto en la página de **Word en línea** , espere a que el estado indicar el **guardado**, haga clic en el botón Atrás del explorador y, a continuación, actualice la página. Debería ver una nueva **Document.docx** en la carpeta **documentos** .</span><span class="sxs-lookup"><span data-stu-id="14447-p108">Type some text in the **Word Online** page, wait for the status to indicate **Saved**, click the back button on your browser, and then refresh the page. You should see a new **Document.docx** in the **Documents** folder.</span></span>
    
13. <span data-ttu-id="14447-198">Haga clic en el botón de puntos suspensivos para el documento de **Document.docx** y, a continuación, haga clic en **obtener un vínculo**.</span><span class="sxs-lookup"><span data-stu-id="14447-198">Click the ellipsis for the **Document.docx** document, and then click **Get a link**.</span></span>
    
14. <span data-ttu-id="14447-199">Copie la dirección URL en el cuadro de diálogo de **Compartir 'Document.docx'** y pegarla en una nueva línea en el Bloc de notas o el editor de texto y, a continuación, cierre el cuadro de diálogo **Compartir 'Document.docx'** .</span><span class="sxs-lookup"><span data-stu-id="14447-199">Copy the URL in the **Share 'Document.docx'** dialog box and paste it on a new line in Notepad or your text editor, and then close the **Share 'Document.docx'** dialog box.</span></span>
    
15. <span data-ttu-id="14447-200">Cierra las fichas de **Documentos de ProjectX** y **SharePoint** en el explorador y, a continuación, haga clic en la ficha **Página de inicio de Microsoft Office** .</span><span class="sxs-lookup"><span data-stu-id="14447-200">Close the **ProjectX-Documents** and **SharePoint** tabs in your browser, and then click the **Microsoft Office Home** tab.</span></span>
    
16. <span data-ttu-id="14447-201">Haga clic en el nombre del **Diseñador de plomo** y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="14447-201">Click the **Lead Designer** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="14447-202">Ahora vamos a explicar con la cuenta de usuario de Vicepresidente de desarrollo de acceso:</span><span class="sxs-lookup"><span data-stu-id="14447-202">Now let's demonstrate access using the Development VP user account:</span></span>
  
1. <span data-ttu-id="14447-203">Iniciar sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) con el nombre de cuenta del Vicepresidente de desarrollo y su contraseña.</span><span class="sxs-lookup"><span data-stu-id="14447-203">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the Development VP account name and its password.</span></span>
    
2. <span data-ttu-id="14447-204">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="14447-204">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="14447-p109">En la ficha nuevo de **SharePoint** en el explorador, escriba **ProjectX** en el cuadro de búsqueda, activar la búsqueda y, a continuación, haga clic en el sitio del equipo **ProjectX** . Debería ver una nueva pestaña en el explorador del sitio de grupo ProjectX.</span><span class="sxs-lookup"><span data-stu-id="14447-p109">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box, activate the search, and then click the **ProjectX** team site. You should see a new tab in your browser for the ProjectX team site.</span></span>
    
4. <span data-ttu-id="14447-207">Haga clic en **documentos**y, a continuación, haga clic en el archivo **Document.docx** .</span><span class="sxs-lookup"><span data-stu-id="14447-207">Click **Documents**, and then click the **Document.docx** file.</span></span>
    
5. <span data-ttu-id="14447-p110">En la ficha **Document.docx** en el explorador, intente modificar el texto. Debería ver un mensaje que indica **este documento es de sólo lectura.** Esto ocurre porque la cuenta de usuario de Vicepresidente de desarrollo sólo tiene permisos de vista para el sitio.</span><span class="sxs-lookup"><span data-stu-id="14447-p110">In the **Document.docx** tab in your browser, try to modify the text. You should see a message stating **This document is read-only.** This is expected because the Development VP user account only has view permissions for the site.</span></span>
    
6. <span data-ttu-id="14447-211">Cierra las fichas **Document.docx**, **Documentos de ProjectX**y **SharePoint** en el explorador.</span><span class="sxs-lookup"><span data-stu-id="14447-211">Close the **Document.docx**, **ProjectX-Documents**, and **SharePoint** tabs in your browser.</span></span>
    
7. <span data-ttu-id="14447-212">Haga clic en la ficha **Página de inicio de Microsoft Office** , haga clic en el nombre del **Vicepresidente de desarrollo** y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="14447-212">Click the **Microsoft Office Home** tab, click the **Development VP** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="14447-213">Ahora vamos a explicar el acceso con una cuenta de usuario que no tiene permisos:</span><span class="sxs-lookup"><span data-stu-id="14447-213">Now let's demonstrate access with a user account that has no permissions:</span></span>
  
1. <span data-ttu-id="14447-214">Iniciar sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) con el nombre de la cuenta de usuario 3 y su contraseña.</span><span class="sxs-lookup"><span data-stu-id="14447-214">Sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using the User 3 account name and its password.</span></span>
    
2. <span data-ttu-id="14447-215">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="14447-215">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="14447-p111">En la ficha nuevo de **SharePoint** en el explorador, escriba **ProjectX** en el cuadro Buscar y, a continuación, activar la búsqueda. Debería ver el mensaje **nada aquí coincide con la búsqueda.**</span><span class="sxs-lookup"><span data-stu-id="14447-p111">On the new **SharePoint** tab in your browser, type **ProjectX** in the search box and then activate the search. You should see the message **Nothing here matches your search.**</span></span>
    
4. <span data-ttu-id="14447-p112">Desde la instancia abierta de Bloc de notas o el editor de texto, copie la dirección URL para el sitio de ProjectX en la barra de direcciones del explorador y presione **ENTRAR**. Debería ver una página de **Acceso denegado** .</span><span class="sxs-lookup"><span data-stu-id="14447-p112">From the open instance of Notepad or your text editor, copy the URL for the ProjectX site into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
5. <span data-ttu-id="14447-p113">En el Bloc de notas o su editor de texto, copie la dirección URL de la carpeta documentos de ProjectX en la barra de direcciones del explorador y presione **ENTRAR**. Debería ver una página de **Acceso denegado** .</span><span class="sxs-lookup"><span data-stu-id="14447-p113">From Notepad or your text editor, copy the URL for the ProjectX Documents folder into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
6. <span data-ttu-id="14447-p114">En el Bloc de notas o su editor de texto, copie la dirección URL para el archivo Documents.docx en la barra de direcciones del explorador y presione **ENTRAR**. Debería ver una página de **Acceso denegado** .</span><span class="sxs-lookup"><span data-stu-id="14447-p114">From Notepad or your text editor, copy the URL for the Documents.docx file into the address bar of your browser and press **Enter**. You should see an **Access Denied** page.</span></span>
    
7. <span data-ttu-id="14447-224">Cerrar la pestaña de **SharePoint** en el explorador, haga clic en la ficha **Página de inicio de Microsoft Office** , haga clic en el nombre de **usuario 3** y, a continuación, haga clic en **Cerrar sesión**.</span><span class="sxs-lookup"><span data-stu-id="14447-224">Close the **SharePoint** tab in your browser, click the **Microsoft Office Home** tab, click the **User 3** name, and then click **Sign out**.</span></span>
    
<span data-ttu-id="14447-225">El sitio de SharePoint Online aislado está preparado para la experimentación adicional.</span><span class="sxs-lookup"><span data-stu-id="14447-225">Your isolated SharePoint Online site is now ready for your additional experimentation.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="14447-226">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="14447-226">Next Step</span></span>

<span data-ttu-id="14447-227">Cuando esté listo para implementar un sitio de equipo de SharePoint Online aislado de producción, consulte las consideraciones de diseño paso a paso en el [Diseño de un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="14447-227">When you are ready to deploy an isolated SharePoint Online team site in production, see the step-by-step design considerations in [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="14447-228">See Also</span><span class="sxs-lookup"><span data-stu-id="14447-228">See Also</span></span>

[<span data-ttu-id="14447-229">Sitios de equipo de SharePoint Online aislados</span><span class="sxs-lookup"><span data-stu-id="14447-229">Isolated SharePoint Online team sites</span></span>](isolated-sharepoint-online-team-sites.md)
  
[<span data-ttu-id="14447-230">Guías del laboratorio de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="14447-230">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="14447-231">Entorno de desarrollo y pruebas de la configuración básica</span><span class="sxs-lookup"><span data-stu-id="14447-231">Base Configuration dev/test environment</span></span>](base-configuration-dev-test-environment.md)
  
[<span data-ttu-id="14447-232">Entorno de desarrollo y pruebas de Office 365</span><span class="sxs-lookup"><span data-stu-id="14447-232">Office 365 dev/test environment</span></span>](office-365-dev-test-environment.md)
  
[<span data-ttu-id="14447-233">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="14447-233">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




