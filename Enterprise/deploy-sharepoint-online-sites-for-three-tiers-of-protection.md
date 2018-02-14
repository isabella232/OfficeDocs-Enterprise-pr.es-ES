---
title: "Implemente sitios de SharePoint Online para tres niveles de protección"
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
- Strat_O365_Enterprise
ms.custom:
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: "Resumen: Crear y configurar sitios de equipo de SharePoint Online para varios niveles de protección de la información."
ms.openlocfilehash: f015ce8d7c91d02ce5dc0a7791ba22a53bc2933f
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="e9fd4-103">Implemente sitios de SharePoint Online para tres niveles de protección</span><span class="sxs-lookup"><span data-stu-id="e9fd4-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="e9fd4-104">**Resumen:** Crear y configurar sitios de equipo de SharePoint Online para varios niveles de protección de la información.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="e9fd4-p101">Utilice los pasos de este artículo para diseñar e implementar la línea de base, sensibles y altamente confidenciales SharePoint Online sitios de equipo. Para obtener más información acerca de estos tres niveles de protección, vea [archivos y sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="e9fd4-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="e9fd4-107">Sitios de equipo de SharePoint Online de línea de base</span><span class="sxs-lookup"><span data-stu-id="e9fd4-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="e9fd4-p102">Protección básica incluye ambos sitios de equipo público y privado. Sitios de equipo público pueden ser detectados y acceso a alguien de la organización. Sitios privados sólo pueden ser detectados y tener acceso a los miembros del grupo Office 365 asociado con el sitio del equipo. Ambos tipos de sitios de grupo permiten miembros compartir el sitio con otras personas.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="e9fd4-112">Público</span><span class="sxs-lookup"><span data-stu-id="e9fd4-112">Public</span></span>

<span data-ttu-id="e9fd4-113">Para crear un sitio de grupo de SharePoint Online de línea de base con acceso público y los permisos, siga este procedimiento:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="e9fd4-p103">Iniciar sesión en el portal de Office 365 con una cuenta que se utilizará para administrar el sitio de grupo de SharePoint Online (un administrador de SharePoint Online). Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e9fd4-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e9fd4-116">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="e9fd4-117">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="e9fd4-118">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="e9fd4-119">En **nombre del sitio**, escriba un nombre para el sitio del grupo público.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="e9fd4-120">En la **Descripción del sitio de equipo**, escriba una descripción del propósito del sitio.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="e9fd4-121">En **la configuración de privacidad**, seleccione **pública - cualquier persona de la organización puede tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e9fd4-122">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="e9fd4-123">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-123">Here is your resulting configuration.</span></span>
  
![Protección de nivel de línea base de un sitio de grupo de SharePoint Online público.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="e9fd4-125">Privada</span><span class="sxs-lookup"><span data-stu-id="e9fd4-125">Private</span></span>

<span data-ttu-id="e9fd4-126">Para crear un sitio de grupo de SharePoint Online de línea de base con permisos y acceso privado, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="e9fd4-p104">Iniciar sesión en el portal de Office 365 con una cuenta que se utilizará para administrar el sitio de grupo de SharePoint Online (un administrador de SharePoint Online). Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e9fd4-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e9fd4-129">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="e9fd4-130">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="e9fd4-131">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="e9fd4-132">En **nombre del sitio**, escriba un nombre para el sitio de equipo privado.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="e9fd4-133">En la **Descripción del sitio de equipo,** escriba una descripción del propósito del sitio.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="e9fd4-134">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e9fd4-135">En el **que desea agregar?** panel, en **Agregar integrantes**, escriba los nombres de cuentas de usuario que tienen acceso a este sitio de equipo privado.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="e9fd4-136">Cuando haya terminado agregando el conjunto inicial de miembros al sitio, haga clic en **Finalizar**</span><span class="sxs-lookup"><span data-stu-id="e9fd4-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="e9fd4-137">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-137">Here is your resulting configuration.</span></span>
  
![Protección de nivel de línea base de un sitio de grupo de SharePoint Online privado.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="e9fd4-139">Sitios de equipo de SharePoint Online confidenciales</span><span class="sxs-lookup"><span data-stu-id="e9fd4-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="e9fd4-140">Un sitio de grupo SharePoint Online confidencial es un sitio de grupo aislado, lo que significa que los permisos se controlan mediante la pertenencia a grupos de SharePoint en lugar de pertenecer al grupo de Office 365 asociado con el sitio del equipo.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="e9fd4-141">Para crear un sitio de grupo aislado, hay dos pasos principales.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="e9fd4-142">Paso 1: Diseñe su sitio aislado</span><span class="sxs-lookup"><span data-stu-id="e9fd4-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="e9fd4-143">Para diseñar el sitio del grupo aislado, debe determinar:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="e9fd4-144">Los grupos de SharePoint y los niveles de permiso.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="e9fd4-145">El conjunto de grupos de acceso que serán miembros de los grupos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="e9fd4-146">El conjunto de grupos de acceso recomendado es uno de los integrantes del sitio, uno para los visitantes y uno para los administradores del sitio.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="e9fd4-147">Si se utilizar grupos anidados dentro de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="e9fd4-148">Por ejemplo, los niveles de permisos y la estructura de grupo recomendado tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="e9fd4-149">**Grupo de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="e9fd4-149">**SharePoint group**</span></span>|<span data-ttu-id="e9fd4-150">**Nivel de permisos**</span><span class="sxs-lookup"><span data-stu-id="e9fd4-150">**Permission level**</span></span>|<span data-ttu-id="e9fd4-151">**Grupo de acceso (ejemplos)**</span><span class="sxs-lookup"><span data-stu-id="e9fd4-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="e9fd4-152">[nombre del sitio] Miembros de</span><span class="sxs-lookup"><span data-stu-id="e9fd4-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="e9fd4-153">Editar</span><span class="sxs-lookup"><span data-stu-id="e9fd4-153">Edit</span></span>  <br/> |<span data-ttu-id="e9fd4-154">[nombre del sitio] Miembros de</span><span class="sxs-lookup"><span data-stu-id="e9fd4-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="e9fd4-155">[nombre del sitio] Visitantes</span><span class="sxs-lookup"><span data-stu-id="e9fd4-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="e9fd4-156">Lectura</span><span class="sxs-lookup"><span data-stu-id="e9fd4-156">Read</span></span>  <br/> |<span data-ttu-id="e9fd4-157">[nombre del sitio] Visores</span><span class="sxs-lookup"><span data-stu-id="e9fd4-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="e9fd4-158">[nombre del sitio] Propietarios</span><span class="sxs-lookup"><span data-stu-id="e9fd4-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="e9fd4-159">Control total</span><span class="sxs-lookup"><span data-stu-id="e9fd4-159">Full control</span></span>  <br/> |<span data-ttu-id="e9fd4-160">[nombre del sitio] Administradores</span><span class="sxs-lookup"><span data-stu-id="e9fd4-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="e9fd4-p105">Los niveles de permisos y grupos de SharePoint se crean de forma predeterminada para un sitio de equipo. Debe determinar los nombres de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="e9fd4-163">Para los detalles del proceso de diseño, consulte [Diseño de un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="e9fd4-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="e9fd4-164">Paso 2: Implemente su sitio aislado</span><span class="sxs-lookup"><span data-stu-id="e9fd4-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="e9fd4-165">Para implementar el sitio aislado, primero debe:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="e9fd4-166">Determinar las cuentas de usuario y grupos para agregar a cada uno de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="e9fd4-167">Cree los grupos de acceso y agregar a los miembros de grupo y usuario.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="e9fd4-168">Para ver los pasos detallados, consulte la **fase 1** de [implementar un sitio de grupo SharePoint Online aislado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="e9fd4-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="e9fd4-169">A continuación, crear el sitio de grupo SharePoint Online con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="e9fd4-p106">Iniciar sesión en el portal de Office 365 con una cuenta que se utilizará para administrar el sitio de grupo de SharePoint Online (un administrador de SharePoint Online). Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="e9fd4-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="e9fd4-172">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="e9fd4-173">En la nueva ficha de **SharePoint** del explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="e9fd4-174">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="e9fd4-175">En **nombre del sitio**, escriba un nombre para el sitio de equipo privado.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="e9fd4-176">En la **Descripción del sitio de equipo**, escriba una descripción opcional.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="e9fd4-177">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="e9fd4-178">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="e9fd4-179">A continuación, desde el nuevo sitio de grupo de SharePoint Online, configurar permisos con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="e9fd4-p107">Determinar el nombre Principal de usuario (UPN) del Administrador de TI o de otra persona que será responsable de responder a y direccionamiento de las solicitudes de acceso al sitio (belindan@contoso.com es un ejemplo de un UPN). Escriba aquí ese UPN: ___.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="e9fd4-182">En la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="e9fd4-183">En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="e9fd4-184">En la nueva ficha de **permisos** del explorador, haga clic en **Configuración de solicitud de acceso**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="e9fd4-185">En el cuadro de diálogo **Configuración de las solicitudes de acceso** :</span><span class="sxs-lookup"><span data-stu-id="e9fd4-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="e9fd4-186">Desactive las casillas de verificación **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **miembros de permitir invitar a otras personas al grupo de miembros del sitio** .</span><span class="sxs-lookup"><span data-stu-id="e9fd4-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="e9fd4-187">Escriba el UPN de su administrador de TI desde el paso 1 en **Enviar todas las solicitudes de acceso**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="e9fd4-188">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="e9fd4-189">En la ficha **permisos** del explorador, haga clic en **miembros de [nombre del sitio]** en la lista.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="e9fd4-190">En **personas y grupos**, haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="e9fd4-191">En el cuadro de diálogo **Compartir** , escriba el nombre de su grupo de acceso de miembros de sitios para este sitio, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="e9fd4-192">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="e9fd4-193">En la lista, haga clic en **[nombre del sitio] propietarios** .</span><span class="sxs-lookup"><span data-stu-id="e9fd4-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="e9fd4-194">En **personas y grupos**, haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="e9fd4-195">En el cuadro de diálogo **Compartir** , escriba el nombre del grupo de acceso de los administradores de sitio para este sitio, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="e9fd4-196">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="e9fd4-197">En la lista, haga clic en **[nombre del sitio] a los visitantes** .</span><span class="sxs-lookup"><span data-stu-id="e9fd4-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="e9fd4-198">En **personas y grupos**, haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="e9fd4-199">En el cuadro de diálogo **Compartir** , escriba el nombre del grupo de acceso de los visores de sitio para este sitio, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="e9fd4-200">Cierre la ficha de **permisos** de tu navegador.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="e9fd4-201">Los resultados de estos valores de permisos son:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="e9fd4-202">El grupo de SharePoint **propietarios de [nombre del sitio]** contiene el grupo de acceso de los administradores de sitio, en que todos los miembros tienen el nivel de permiso **control total** .</span><span class="sxs-lookup"><span data-stu-id="e9fd4-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="e9fd4-203">El grupo de SharePoint **miembros de [nombre del sitio]** contiene el grupo de acceso de los miembros de sitio en el que todos los miembros tienen el nivel de permisos **Editar** .</span><span class="sxs-lookup"><span data-stu-id="e9fd4-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="e9fd4-204">El grupo de SharePoint **visitantes de [nombre del sitio]** contiene el grupo de acceso de visores de sitio en el que todos los miembros tienen el nivel de permiso de **lectura** .</span><span class="sxs-lookup"><span data-stu-id="e9fd4-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="e9fd4-205">Se deshabilita la capacidad de los miembros invitar a otros miembros.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="e9fd4-206">Se habilita la capacidad de los miembros solicitar acceso.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="e9fd4-207">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-207">Here is your resulting configuration.</span></span>
  
![Protección de nivel confidencial de un sitio de grupo de SharePoint Online aislado.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="e9fd4-209">Los miembros del sitio, a través de la pertenencia a grupos en uno de los grupos de acceso ahora pueden colaborar de forma segura en los recursos del sitio.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="e9fd4-210">Sitios de equipo de SharePoint Online altamente confidenciales</span><span class="sxs-lookup"><span data-stu-id="e9fd4-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="e9fd4-211">Un sitio de grupo SharePoint Online altamente confidencial es un sitio de grupo aislado, lo que significa que los permisos se controlan mediante la pertenencia a grupos de SharePoint en lugar de pertenecer al grupo de Office 365 asociado con el sitio del equipo.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="e9fd4-212">Para crear un sitio de grupo aislado para información confidencial y la colaboración, hay dos pasos principales.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="e9fd4-213">Paso 1: Diseñe su sitio aislado</span><span class="sxs-lookup"><span data-stu-id="e9fd4-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="e9fd4-214">Para diseñar el sitio del grupo aislado, debe determinar:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="e9fd4-215">Los grupos de SharePoint y los niveles de permiso.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="e9fd4-216">El conjunto de grupos de acceso que serán miembros de los grupos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="e9fd4-217">El conjunto de grupos de acceso recomendado es uno de los integrantes del sitio, uno para los visitantes y uno para los administradores del sitio.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="e9fd4-218">Si se utilizar grupos anidados dentro de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="e9fd4-219">Por ejemplo, los niveles de permisos y la estructura de grupo recomendado tiene este aspecto:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="e9fd4-220">**Grupo de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="e9fd4-220">**SharePoint group**</span></span>|<span data-ttu-id="e9fd4-221">**Nivel de permisos**</span><span class="sxs-lookup"><span data-stu-id="e9fd4-221">**Permission level**</span></span>|<span data-ttu-id="e9fd4-222">**Grupo de acceso (ejemplos)**</span><span class="sxs-lookup"><span data-stu-id="e9fd4-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="e9fd4-223">[nombre del sitio] Miembros de</span><span class="sxs-lookup"><span data-stu-id="e9fd4-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="e9fd4-224">Editar</span><span class="sxs-lookup"><span data-stu-id="e9fd4-224">Edit</span></span>  <br/> |<span data-ttu-id="e9fd4-225">[nombre del sitio] Miembros de</span><span class="sxs-lookup"><span data-stu-id="e9fd4-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="e9fd4-226">[nombre del sitio] Visitantes</span><span class="sxs-lookup"><span data-stu-id="e9fd4-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="e9fd4-227">Lectura</span><span class="sxs-lookup"><span data-stu-id="e9fd4-227">Read</span></span>  <br/> |<span data-ttu-id="e9fd4-228">[nombre del sitio] Visores</span><span class="sxs-lookup"><span data-stu-id="e9fd4-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="e9fd4-229">[nombre del sitio] Propietarios</span><span class="sxs-lookup"><span data-stu-id="e9fd4-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="e9fd4-230">Control total</span><span class="sxs-lookup"><span data-stu-id="e9fd4-230">Full control</span></span>  <br/> |<span data-ttu-id="e9fd4-231">[nombre del sitio] Administradores</span><span class="sxs-lookup"><span data-stu-id="e9fd4-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="e9fd4-p108">Los niveles de permisos y grupos de SharePoint se crean de forma predeterminada para un sitio de equipo. Debe determinar los nombres de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="e9fd4-234">Para los detalles del proceso de diseño, consulte [Diseño de un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="e9fd4-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="e9fd4-235">Paso 2: Implemente su sitio aislado</span><span class="sxs-lookup"><span data-stu-id="e9fd4-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="e9fd4-236">Para implementar el sitio aislado, primero debe:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="e9fd4-237">Determinar a los miembros de grupo y usuario de cada uno de los grupos de acceso</span><span class="sxs-lookup"><span data-stu-id="e9fd4-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="e9fd4-238">Crear los grupos de acceso y agregar a los miembros del grupo y de usuario</span><span class="sxs-lookup"><span data-stu-id="e9fd4-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="e9fd4-239">Crear un sitio de grupo aislado que usa los grupos de acceso</span><span class="sxs-lookup"><span data-stu-id="e9fd4-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="e9fd4-240">Para ver los pasos detallados, vea [implementar un sitio de grupo SharePoint Online aislado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="e9fd4-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="e9fd4-241">Los resultados de la configuración de permisos son:</span><span class="sxs-lookup"><span data-stu-id="e9fd4-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="e9fd4-242">El grupo de SharePoint **propietarios de [nombre del sitio]** contiene el grupo de acceso de los administradores de sitio, en que todos los miembros tienen el nivel de permiso **control total** .</span><span class="sxs-lookup"><span data-stu-id="e9fd4-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="e9fd4-243">El grupo de SharePoint **miembros de [nombre del sitio]** contiene el grupo de acceso de los miembros de sitio en el que todos los miembros tienen el nivel de permisos **Editar** .</span><span class="sxs-lookup"><span data-stu-id="e9fd4-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="e9fd4-244">El grupo de SharePoint **visitantes de [nombre del sitio]** contiene el grupo de acceso de visores de sitio en el que todos los miembros tienen el nivel de permiso de **lectura** .</span><span class="sxs-lookup"><span data-stu-id="e9fd4-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="e9fd4-245">Se deshabilita la capacidad de los miembros invitar a otros miembros.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="e9fd4-246">Se deshabilita la capacidad de los miembros solicitar acceso.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="e9fd4-247">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-247">Here is your resulting configuration.</span></span>
  
![Protección de nivel alto de confidencialidad de un sitio de grupo de SharePoint Online aislado.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="e9fd4-249">Los miembros del sitio, a través de la pertenencia a grupos en uno de los grupos de acceso ahora pueden colaborar de forma segura en los recursos del sitio.</span><span class="sxs-lookup"><span data-stu-id="e9fd4-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="e9fd4-250">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="e9fd4-250">Next step</span></span>

[<span data-ttu-id="e9fd4-251">Proteger archivos de SharePoint Online con etiquetas de Office 365 y DLP</span><span class="sxs-lookup"><span data-stu-id="e9fd4-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="e9fd4-252">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e9fd4-252">See Also</span></span>

[<span data-ttu-id="e9fd4-253">Proteger los archivos y los sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e9fd4-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="e9fd4-254">Sitios de SharePoint Online seguros en un entorno de pruebas y desarrollo</span><span class="sxs-lookup"><span data-stu-id="e9fd4-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="e9fd4-255">Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile</span><span class="sxs-lookup"><span data-stu-id="e9fd4-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="e9fd4-256">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="e9fd4-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




