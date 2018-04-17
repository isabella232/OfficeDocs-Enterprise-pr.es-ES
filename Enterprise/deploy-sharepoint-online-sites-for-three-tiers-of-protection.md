---
title: Implemente sitios de SharePoint Online para tres niveles de protección
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
- Ent_Solutions
ms.assetid: 1e8e3cfd-b878-4088-b941-9940363a5fae
description: 'Resumen: Crear y configurar sitios de equipo de SharePoint Online para varios niveles de protección de la información.'
ms.openlocfilehash: ddeb1885cbc74be6e7098660eb1d9906d43739fd
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="deploy-sharepoint-online-sites-for-three-tiers-of-protection"></a><span data-ttu-id="3e3f4-103">Implemente sitios de SharePoint Online para tres niveles de protección</span><span class="sxs-lookup"><span data-stu-id="3e3f4-103">Deploy SharePoint Online sites for three tiers of protection</span></span>

 <span data-ttu-id="3e3f4-104">**Resumen:** Crear y configurar sitios de equipo de SharePoint Online para varios niveles de protección de la información.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-104">**Summary:** Create and configure SharePoint Online team sites for various levels of information protection.</span></span>
  
<span data-ttu-id="3e3f4-p101">Siga los pasos de este artículo para diseñar e implementar sitios de grupo de base de referencia, confidenciales y extremadamente confidenciales de SharePoint Online. Para más información sobre estos tres niveles de protección, vea [Proteger sitios y archivos de SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="3e3f4-p101">Use the steps in this article to design and deploy baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="baseline-sharepoint-online-team-sites"></a><span data-ttu-id="3e3f4-107">Sitios de grupo de base de referencia de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3e3f4-107">Baseline SharePoint Online team sites</span></span>

<span data-ttu-id="3e3f4-p102">La protección de base de referencia incluye sitios de grupo públicos y privados. Todo el personal de la organización puede acceder a los sitios de grupo públicos. Solo los miembros del grupo de Office 365 asociado al sitio de grupo pueden detectar sitios privados y acceder a ellos. Ambos tipos de sitios de grupo permiten a los miembros compartir el sitio con otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-p102">Baseline protection includes both public and private team sites. Public team sites can be discovered and accessed by anybody in the organization. Private sites can only be discovered and accessed by members of the Office 365 group associated with the team site. Both of these types of team sites allow members to share the site with others.</span></span>
  
### <a name="public"></a><span data-ttu-id="3e3f4-112">Público</span><span class="sxs-lookup"><span data-stu-id="3e3f4-112">Public</span></span>

<span data-ttu-id="3e3f4-113">Para crear un sitio de grupo de SharePoint Online de base de referencia con acceso y permisos públicos, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-113">To create a baseline SharePoint Online team site with public access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="3e3f4-p103">Iniciar sesión en el portal de Office 365 con una cuenta que se utilizará para administrar el sitio de grupo de SharePoint Online (un administrador de SharePoint Online). Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="3e3f4-p103">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="3e3f4-116">En la lista de iconos, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-116">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="3e3f4-117">En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-117">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="3e3f4-118">En la página **Crear un sitio**, haga clic en **Sitio de grupo**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-118">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="3e3f4-119">En **Nombre del sitio**, escriba un nombre para el sitio de grupo público.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-119">In **Site name**, type a name for the public team site.</span></span> 
    
6. <span data-ttu-id="3e3f4-120">En la **descripción del sitio de grupo**, escriba una descripción de la finalidad del sitio.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-120">In **Team site description**, type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="3e3f4-121">En **la configuración de privacidad**, seleccione **pública - cualquier persona de la organización puede tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-121">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="3e3f4-122">En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-122">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="3e3f4-123">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-123">Here is your resulting configuration.</span></span>
  
![Protección de nivel de línea base de un sitio de grupo de SharePoint Online público.](images/bcd46b8d-3f89-4398-80ce-4da17ee85e03.png)
  
### <a name="private"></a><span data-ttu-id="3e3f4-125">Private</span><span class="sxs-lookup"><span data-stu-id="3e3f4-125">Private</span></span>

<span data-ttu-id="3e3f4-126">Para crear un sitio de grupo de SharePoint Online de base de referencia con acceso y permisos privados, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-126">To create a baseline SharePoint Online team site with private access and permissions, do the following:</span></span>
  
1. <span data-ttu-id="3e3f4-p104">Iniciar sesión en el portal de Office 365 con una cuenta que se utilizará para administrar el sitio de grupo de SharePoint Online (un administrador de SharePoint Online). Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="3e3f4-p104">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="3e3f4-129">En la lista de iconos, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-129">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="3e3f4-130">En la nueva pestaña **SharePoint** del explorador, haga clic en **+ Crear sitio**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-130">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="3e3f4-131">En la página **Crear un sitio**, haga clic en **Sitio de grupo**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-131">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="3e3f4-132">En **Nombre del sitio**, escriba un nombre para el sitio de grupo privado.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-132">In **Site name**, type a name for the private team site.</span></span> 
    
6. <span data-ttu-id="3e3f4-133">En la **Descripción del sitio de equipo,** escriba una descripción del propósito del sitio.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-133">In **Team site description,** type a description of the purpose of the site.</span></span>
    
7. <span data-ttu-id="3e3f4-134">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-134">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="3e3f4-135">En el panel de **Who do you want to add?** (Usuarios que quiere agregar), en **Agregar miembros**, escriba los nombres de cuentas de usuario que tengan acceso a este sitio de grupo privado.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-135">On the **Who do you want to add?** pane, in **Add members**, type the names of user accounts that have access to this private team site.</span></span>
    
9. <span data-ttu-id="3e3f4-136">Cuando haya terminado agregando el conjunto inicial de miembros al sitio, haga clic en **Finalizar**</span><span class="sxs-lookup"><span data-stu-id="3e3f4-136">When you are done adding the initial set of members to the site, click **Finish**</span></span>
    
<span data-ttu-id="3e3f4-137">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-137">Here is your resulting configuration.</span></span>
  
![Protección de nivel de línea base de un sitio de grupo de SharePoint Online privado.](images/91769026-37e3-4383-ac3c-dbf7aca98e41.png)
  
## <a name="sensitive-sharepoint-online-team-sites"></a><span data-ttu-id="3e3f4-139">Sitios de grupo confidenciales de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3e3f4-139">Sensitive SharePoint Online team sites</span></span>

<span data-ttu-id="3e3f4-140">Un sitio de grupo de SharePoint Online confidencial es un sitio de grupo aislado, lo que significa que los permisos se controlan mediante la pertenencia a grupos de SharePoint en lugar de la pertenencia al grupo de Office 365 asociado al sitio de grupo.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-140">A sensitive SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="3e3f4-141">Para crear un sitio de grupo aislado, hay dos pasos principales.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-141">To create an isolated team site, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="3e3f4-142">Paso 1: Diseñar el sitio aislado</span><span class="sxs-lookup"><span data-stu-id="3e3f4-142">Step 1: Design your isolated site</span></span>

<span data-ttu-id="3e3f4-143">Para diseñar el sitio de grupo aislado, debe determinar:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-143">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="3e3f4-144">Los grupos y niveles de permisos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-144">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="3e3f4-145">El conjunto de grupos de acceso que serán miembros de los grupos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-145">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="3e3f4-146">El conjunto de grupos de acceso recomendado es uno de los integrantes del sitio, uno para los visitantes y uno para los administradores del sitio.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-146">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="3e3f4-147">Si va a usar grupos anidados dentro de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-147">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="3e3f4-148">Por ejemplo, la estructura del grupo y los niveles de permisos recomendados tienen este aspecto:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-148">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="3e3f4-149">**Grupo de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="3e3f4-149">**SharePoint group**</span></span>|<span data-ttu-id="3e3f4-150">**Nivel de permisos**</span><span class="sxs-lookup"><span data-stu-id="3e3f4-150">**Permission level**</span></span>|<span data-ttu-id="3e3f4-151">**Grupo de acceso (ejemplos)**</span><span class="sxs-lookup"><span data-stu-id="3e3f4-151">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3e3f4-152">Miembros de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-152">[site name] Members</span></span>  <br/> |<span data-ttu-id="3e3f4-153">Editar</span><span class="sxs-lookup"><span data-stu-id="3e3f4-153">Edit</span></span>  <br/> |<span data-ttu-id="3e3f4-154">Miembros de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-154">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="3e3f4-155">Visitantes de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-155">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="3e3f4-156">Lectura</span><span class="sxs-lookup"><span data-stu-id="3e3f4-156">Read</span></span>  <br/> |<span data-ttu-id="3e3f4-157">Lectores de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-157">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="3e3f4-158">Propietarios de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-158">[site name] Owners</span></span>  <br/> |<span data-ttu-id="3e3f4-159">Control total</span><span class="sxs-lookup"><span data-stu-id="3e3f4-159">Full control</span></span>  <br/> |<span data-ttu-id="3e3f4-160">Administradores de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-160">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="3e3f4-p105">Los niveles de permisos y los grupos de SharePoint se crean de forma predeterminada para un sitio de grupo. Debe determinar los nombres de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-p105">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="3e3f4-163">Para obtener los detalles del proceso de diseño, vea [Diseñar un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="3e3f4-163">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="3e3f4-164">Paso 2: Implementar el sitio aislado</span><span class="sxs-lookup"><span data-stu-id="3e3f4-164">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="3e3f4-165">Para implementar el sitio aislado, primero debe:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-165">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="3e3f4-166">Determinar las cuentas de usuario y los grupos que va a agregar a cada uno de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-166">Determine the user accounts and groups to add to each of your access groups.</span></span>
    
- <span data-ttu-id="3e3f4-167">Crear los grupos de acceso y agregar a miembros de grupos y usuarios.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-167">Create the access groups and add the user and group members.</span></span>
    
<span data-ttu-id="3e3f4-168">Para obtener los pasos detallados, vea la **fase 1** de [Implementar un sitio de grupo SharePoint Online aislado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="3e3f4-168">For the detailed steps, see **Phase 1** of [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="3e3f4-169">A continuación, crear el sitio de grupo SharePoint Online con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-169">Next, you create the SharePoint Online team site with these steps.</span></span>
  
1. <span data-ttu-id="3e3f4-p106">Iniciar sesión en el portal de Office 365 con una cuenta que se utilizará para administrar el sitio de grupo de SharePoint Online (un administrador de SharePoint Online). Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="3e3f4-p106">Sign in to the Office 365 portal with an account that will also be used to administer the SharePoint Online team site (a SharePoint Online administrator). For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="3e3f4-172">En la lista de iconos, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-172">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="3e3f4-173">En la nueva ficha de **SharePoint** del explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-173">In the new **SharePoint** tab of your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="3e3f4-174">En la página **Crear un sitio**, haga clic en **Sitio de grupo**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-174">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="3e3f4-175">En **Nombre del sitio**, escriba un nombre para el sitio de grupo privado.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-175">In **Site name**, type a name for the private team site.</span></span>
    
6. <span data-ttu-id="3e3f4-176">En la **Descripción del sitio de equipo**, escriba una descripción opcional.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-176">In **Team site description**, type an optional description.</span></span>
    
7. <span data-ttu-id="3e3f4-177">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-177">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="3e3f4-178">En el panel **Who do you want to add?** (Usuarios que quiere agregar), haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-178">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="3e3f4-179">Luego, desde el nuevo sitio de grupo de SharePoint Online, configure los permisos con estos pasos.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-179">Next, from the new SharePoint Online team site, configure permissions with these steps.</span></span>
  
1. <span data-ttu-id="3e3f4-p107">Determinar el nombre Principal de usuario (UPN) del Administrador de TI o de otra persona que será responsable de responder a y direccionamiento de las solicitudes de acceso al sitio (belindan@contoso.com es un ejemplo de un UPN). Escriba aquí ese UPN: ___.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-p107">Determine the User Principal Name (UPN) of the IT administrator or other person who will be responsible for responding to and addressing requests for access to the site (belindan@contoso.com is an example of a UPN). Write that UPN here: _________________________________________.</span></span>
    
2. <span data-ttu-id="3e3f4-182">En la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-182">In the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
3. <span data-ttu-id="3e3f4-183">En el panel **Permisos del sitio**, haga clic en **Advanced permissions settings** (Configuración de permisos avanzada).</span><span class="sxs-lookup"><span data-stu-id="3e3f4-183">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
4. <span data-ttu-id="3e3f4-184">En la nueva pestaña **Permisos** del explorador, haga clic en **Configuración de solicitud de acceso**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-184">On the new **Permissions** tab of your browser, click **Access Request Settings**.</span></span>
    
5. <span data-ttu-id="3e3f4-185">En el cuadro de diálogo **Configuración de solicitud de acceso**:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-185">In the **Access Requests Settings** dialog box:</span></span>
    
  - <span data-ttu-id="3e3f4-186">Desactive las casillas de verificación **Permitir que los miembros compartan el sitio y archivos y carpetas individuales** y **Permitir a los miembros invitar a otros al grupo de miembros del sitio**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-186">Clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes.</span></span>
    
  - <span data-ttu-id="3e3f4-187">Escriba el UPN del administrador de TI del paso 1 en **Enviar todas las solicitudes de acceso**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-187">Type the UPN of your IT administrator from step 1 in **Send all requests for access**.</span></span>
    
  - <span data-ttu-id="3e3f4-188">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-188">Click **OK**.</span></span>
    
6. <span data-ttu-id="3e3f4-189">En la pestaña **Permisos** del explorador, haga clic en **Miembros de [nombre del sitio]** en la lista.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-189">On the **Permissions** tab of your browser, click **[site name] Members** in the list.</span></span>
    
7. <span data-ttu-id="3e3f4-190">En **personas y grupos**, haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-190">In **People and Groups**, click **New**.</span></span>
    
8. <span data-ttu-id="3e3f4-191">En el cuadro de diálogo **Compartir** , escriba el nombre de su grupo de acceso de miembros de sitios para este sitio, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-191">In the **Share** dialog box, type the name of your site members access group for this site, select it, and then click **Share**.</span></span>
    
9. <span data-ttu-id="3e3f4-192">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-192">Click the back button on your browser.</span></span>
    
10. <span data-ttu-id="3e3f4-193">En la lista, haga clic en **[nombre del sitio] propietarios** .</span><span class="sxs-lookup"><span data-stu-id="3e3f4-193">Click **[site name] Owners** in the list.</span></span>
    
11. <span data-ttu-id="3e3f4-194">En **personas y grupos**, haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-194">In **People and Groups**, click **New**.</span></span>
    
12. <span data-ttu-id="3e3f4-195">En el cuadro de diálogo **Compartir** , escriba el nombre del grupo de acceso de los administradores de sitio para este sitio, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-195">In the **Share** dialog box, type the name of the site administrators access group for this site, select it, and then click **Share**.</span></span>
    
13. <span data-ttu-id="3e3f4-196">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-196">Click the back button on your browser.</span></span>
    
14. <span data-ttu-id="3e3f4-197">En la lista, haga clic en **[nombre del sitio] a los visitantes** .</span><span class="sxs-lookup"><span data-stu-id="3e3f4-197">Click **[site name] Visitors** in the list.</span></span>
    
15. <span data-ttu-id="3e3f4-198">En **personas y grupos**, haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-198">In **People and Groups**, click **New**.</span></span>
    
16. <span data-ttu-id="3e3f4-199">En el cuadro de diálogo **Compartir** , escriba el nombre del grupo de acceso de los visores de sitio para este sitio, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-199">In the **Share** dialog box, type the name of the site viewers access group for this site, select it, and then click **Share**.</span></span>
    
17. <span data-ttu-id="3e3f4-200">Cierre la pestaña **Permisos** del explorador.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-200">Close the **Permissions** tab of your browser.</span></span>
    
<span data-ttu-id="3e3f4-201">Los resultados de estos valores de permisos son:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-201">The results of these permission settings are:</span></span>
  
- <span data-ttu-id="3e3f4-202">El grupo de SharePoint **Propietarios de [nombre del sitio]** contiene el grupo de acceso de administradores de sitio, en el que todos los miembros tienen el nivel de permisos **Control total**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-202">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="3e3f4-203">El grupo de SharePoint **Miembros de [nombre del sitio]** contiene el grupo de acceso de miembros de sitio, en el que todos los miembros tienen el nivel de permisos **Editar**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-203">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="3e3f4-204">El grupo de SharePoint **Visitantes de [nombre del sitio]** contiene el grupo de acceso de lectores de sitio, en el que todos los miembros tienen el nivel de permisos **Leer**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-204">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="3e3f4-205">La capacidad de los miembros de invitar a otros miembros está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-205">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="3e3f4-206">La capacidad de los miembros de solicitar acceso está habilitada.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-206">The ability for non-members to request access is enabled.</span></span>
    
<span data-ttu-id="3e3f4-207">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-207">Here is your resulting configuration.</span></span>
  
![Protección de nivel confidencial de un sitio de grupo de SharePoint Online aislado.](images/7a6ab9c6-560a-4674-ac39-8175644dbe6f.png)
  
<span data-ttu-id="3e3f4-209">Los miembros del sitio, a través de la pertenencia a grupos en uno de los grupos de acceso, ahora pueden colaborar de forma segura en los recursos del sitio.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-209">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="highly-confidential-sharepoint-online-team-sites"></a><span data-ttu-id="3e3f4-210">Sitios de grupo de SharePoint Online extremadamente confidenciales</span><span class="sxs-lookup"><span data-stu-id="3e3f4-210">Highly confidential SharePoint Online team sites</span></span>

<span data-ttu-id="3e3f4-211">Un sitio de grupo de SharePoint Online extremadamente confidencial es un sitio de grupo aislado, lo que significa que los permisos se controlan mediante la pertenencia a grupos de SharePoint en lugar de la pertenencia al grupo de Office 365 asociado al sitio de grupo.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-211">A highly confidential SharePoint Online team site is an isolated team site, which means that permissions are controlled through membership in SharePoint groups instead of membership in the Office 365 group associated with the team site.</span></span>
  
<span data-ttu-id="3e3f4-212">Para crear un sitio de grupo aislado para información y colaboración extremadamente confidenciales, hay dos pasos principales.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-212">To create an isolated team site for highly confidential information and collaboration, there are two main steps.</span></span>
  
### <a name="step-1-design-your-isolated-site"></a><span data-ttu-id="3e3f4-213">Paso 1: Diseñar el sitio aislado</span><span class="sxs-lookup"><span data-stu-id="3e3f4-213">Step 1: Design your isolated site</span></span>

<span data-ttu-id="3e3f4-214">Para diseñar el sitio de grupo aislado, debe determinar:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-214">To design your isolated team site, you need to determine:</span></span>
  
- <span data-ttu-id="3e3f4-215">Los grupos y niveles de permisos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-215">Your SharePoint groups and permission levels.</span></span>
    
- <span data-ttu-id="3e3f4-216">El conjunto de grupos de acceso que serán miembros de los grupos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-216">The set of access groups that will be members of your SharePoint groups.</span></span>
    
     <span data-ttu-id="3e3f4-217">El conjunto de grupos de acceso recomendado es uno de los integrantes del sitio, uno para los visitantes y uno para los administradores del sitio.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-217">The recommended set of access groups is one for site members, one for site viewers, and one for site administrators.</span></span>
    
- <span data-ttu-id="3e3f4-218">Si va a usar grupos anidados dentro de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-218">Whether you will use nested groups within your access groups.</span></span>
    
<span data-ttu-id="3e3f4-219">Por ejemplo, la estructura del grupo y los niveles de permisos recomendados tienen este aspecto:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-219">For example, the recommended group structure and permission levels look like this:</span></span>
  
|<span data-ttu-id="3e3f4-220">**Grupo de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="3e3f4-220">**SharePoint group**</span></span>|<span data-ttu-id="3e3f4-221">**Nivel de permisos**</span><span class="sxs-lookup"><span data-stu-id="3e3f4-221">**Permission level**</span></span>|<span data-ttu-id="3e3f4-222">**Grupo de acceso (ejemplos)**</span><span class="sxs-lookup"><span data-stu-id="3e3f4-222">**Access group (examples)**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="3e3f4-223">Miembros de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-223">[site name] Members</span></span>  <br/> |<span data-ttu-id="3e3f4-224">Editar</span><span class="sxs-lookup"><span data-stu-id="3e3f4-224">Edit</span></span>  <br/> |<span data-ttu-id="3e3f4-225">Miembros de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-225">[site name] Members</span></span>  <br/> |
|<span data-ttu-id="3e3f4-226">Visitantes de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-226">[site name] Visitors</span></span>  <br/> |<span data-ttu-id="3e3f4-227">Lectura</span><span class="sxs-lookup"><span data-stu-id="3e3f4-227">Read</span></span>  <br/> |<span data-ttu-id="3e3f4-228">Lectores de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-228">[site name] Viewers</span></span>  <br/> |
|<span data-ttu-id="3e3f4-229">Propietarios de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-229">[site name] Owners</span></span>  <br/> |<span data-ttu-id="3e3f4-230">Control total</span><span class="sxs-lookup"><span data-stu-id="3e3f4-230">Full control</span></span>  <br/> |<span data-ttu-id="3e3f4-231">Administradores de [nombre del sitio]</span><span class="sxs-lookup"><span data-stu-id="3e3f4-231">[site name] Admins</span></span>  <br/> |
   
<span data-ttu-id="3e3f4-p108">Los niveles de permisos y los grupos de SharePoint se crean de forma predeterminada para un sitio de grupo. Debe determinar los nombres de los grupos de acceso.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-p108">The SharePoint groups and permission levels are created by default for a team site. You need to determine the names of your access groups.</span></span>
  
<span data-ttu-id="3e3f4-234">Para obtener los detalles del proceso de diseño, vea [Diseñar un sitio de grupo SharePoint Online aislado](design-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="3e3f4-234">For the details of the design process, see [Design an isolated SharePoint Online team site](design-an-isolated-sharepoint-online-team-site.md).</span></span>
  
### <a name="step-2-deploy-your-isolated-site"></a><span data-ttu-id="3e3f4-235">Paso 2: Implementar el sitio aislado</span><span class="sxs-lookup"><span data-stu-id="3e3f4-235">Step 2: Deploy your isolated site</span></span>

<span data-ttu-id="3e3f4-236">Para implementar el sitio aislado, primero debe:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-236">To deploy your isolated site, you first need to:</span></span>
  
- <span data-ttu-id="3e3f4-237">Determinar a los miembros de grupo y usuario de cada uno de los grupos de acceso</span><span class="sxs-lookup"><span data-stu-id="3e3f4-237">Determine the user and group members of each of your access groups</span></span>
    
- <span data-ttu-id="3e3f4-238">Crear los grupos de acceso y agregar a los miembros del grupo y de usuario</span><span class="sxs-lookup"><span data-stu-id="3e3f4-238">Create the access groups and add the user and group members</span></span>
    
- <span data-ttu-id="3e3f4-239">Crear un sitio de grupo aislado que usa los grupos de acceso</span><span class="sxs-lookup"><span data-stu-id="3e3f4-239">Create an isolated team site that uses your access groups</span></span>
    
<span data-ttu-id="3e3f4-240">Para obtener los pasos detallados, vea [Implementar un sitio de grupo SharePoint Online aislado](deploy-an-isolated-sharepoint-online-team-site.md).</span><span class="sxs-lookup"><span data-stu-id="3e3f4-240">For the detailed steps, see [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).</span></span>
  
<span data-ttu-id="3e3f4-241">Los resultados de la configuración de permisos son:</span><span class="sxs-lookup"><span data-stu-id="3e3f4-241">The results of the permission settings are:</span></span>
  
- <span data-ttu-id="3e3f4-242">El grupo de SharePoint **Propietarios de [nombre del sitio]** contiene el grupo de acceso de administradores de sitio, en el que todos los miembros tienen el nivel de permisos **Control total**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-242">The **[site name] Owners** SharePoint group contains the site administrators access group, in which all the members have the **Full control** permission level.</span></span>
    
- <span data-ttu-id="3e3f4-243">El grupo de SharePoint **Miembros de [nombre del sitio]** contiene el grupo de acceso de miembros de sitio, en el que todos los miembros tienen el nivel de permisos **Editar**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-243">The **[site name] Members** SharePoint group contains the site members access group, in which all the members have the **Edit** permission level.</span></span>
    
- <span data-ttu-id="3e3f4-244">El grupo de SharePoint **Visitantes de [nombre del sitio]** contiene el grupo de acceso de lectores de sitio, en el que todos los miembros tienen el nivel de permisos **Leer**.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-244">The **[site name] Visitors** SharePoint group contains the site viewers access group, in which all the members have the **Read** permission level.</span></span>
    
- <span data-ttu-id="3e3f4-245">La capacidad de los miembros de invitar a otros miembros está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-245">The ability for members to invite other members is disabled.</span></span>
    
- <span data-ttu-id="3e3f4-246">La capacidad de los no miembros de solicitar acceso está deshabilitada.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-246">The ability for non-members to request access is disabled.</span></span>
    
<span data-ttu-id="3e3f4-247">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-247">Here is your resulting configuration.</span></span>
  
![Protección de nivel alto de confidencialidad de un sitio de grupo de SharePoint Online aislado.](images/196359ab-d7ed-4fcf-97b4-61820a74aca4.png)
  
<span data-ttu-id="3e3f4-249">Los miembros del sitio, a través de la pertenencia a grupos en uno de los grupos de acceso, ahora pueden colaborar de forma segura en los recursos del sitio.</span><span class="sxs-lookup"><span data-stu-id="3e3f4-249">The members of the site, through group membership in one of the access groups, can now securely collaborate on the resources of the site.</span></span>
  
## <a name="next-step"></a><span data-ttu-id="3e3f4-250">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="3e3f4-250">Next step</span></span>

[<span data-ttu-id="3e3f4-251">Proteger archivos de SharePoint Online con etiquetas de Office 365 y DLP</span><span class="sxs-lookup"><span data-stu-id="3e3f4-251">Protect SharePoint Online files with Office 365 labels and DLP</span></span>](protect-sharepoint-online-files-with-office-365-labels-and-dlp.md)
    
## <a name="see-also"></a><span data-ttu-id="3e3f4-252">Consulte también</span><span class="sxs-lookup"><span data-stu-id="3e3f4-252">See Also</span></span>

[<span data-ttu-id="3e3f4-253">Protección de archivos y sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3e3f4-253">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="3e3f4-254">Protección de sitios de SharePoint Online en un entorno de prueba y desarrollo</span><span class="sxs-lookup"><span data-stu-id="3e3f4-254">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="3e3f4-255">Instrucciones de seguridad de Microsoft para campañas políticas, organizaciones sin ánimo de lucro y otras organizaciones ágiles</span><span class="sxs-lookup"><span data-stu-id="3e3f4-255">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="3e3f4-256">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="3e3f4-256">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




