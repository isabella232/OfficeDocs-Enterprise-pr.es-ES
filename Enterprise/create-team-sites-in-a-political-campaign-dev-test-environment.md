---
title: "Crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.service: o365-solutions
localization_priority: None
ms.custom: Strat_O365_Enterprise
ms.assetid: c2112ce8-1c4b-424f-b200-59e161db2d21
description: "Resumen: Crear sitios de equipo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en su entorno de pruebas y desarrollo de campaña política."
ms.openlocfilehash: 3a2e507d17a558452fe0c2f0a062098e7c9c6407
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="create-team-sites-in-a-political-campaign-devtest-environment"></a><span data-ttu-id="4b4be-103">Crear sitios de equipo en un entorno de pruebas y desarrollo de campaña política</span><span class="sxs-lookup"><span data-stu-id="4b4be-103">Create team sites in a political campaign dev/test environment</span></span>

 <span data-ttu-id="4b4be-104">**Resumen:** Crear sitios de equipo de SharePoint Online públicos, privados, confidenciales y altamente confidenciales en su entorno de pruebas y desarrollo de campaña política.</span><span class="sxs-lookup"><span data-stu-id="4b4be-104">**Summary:** Create public, private, sensitive, and highly confidential SharePoint Online team sites in your political campaign dev/test environment.</span></span> 
  
<span data-ttu-id="4b4be-p101">Siga las instrucciones de este artículo para crear un entorno de pruebas y desarrollo que incluye los cuatro tipos diferentes de sitios de grupo de SharePoint Online para obtener la [Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solución. Estos sitios se describen detalladamente en el tema 10, titulado **SharePoint y OneDrive para el negocio**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-p101">Use the instructions in this article to create a dev/test environment that includes the four different types of SharePoint Online team sites for the [Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md) solution. These sites are described in detail on Topic 10, titled **SharePoint and OneDrive for Business**.</span></span>
  
## <a name="phase-1-create-your-political-campaign-devtest-environment"></a><span data-ttu-id="4b4be-107">Fase 1: Crear el entorno de pruebas y desarrollo de campaña política</span><span class="sxs-lookup"><span data-stu-id="4b4be-107">Phase 1: Create your political campaign dev/test environment</span></span>

<span data-ttu-id="4b4be-108">En primer lugar, siga las instrucciones de [Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) para crear suscripciones, usuarios y grupos.</span><span class="sxs-lookup"><span data-stu-id="4b4be-108">First, follow the instructions in [Configure groups and users for a political campaign dev/test environment](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md) to create your subscriptions, users, and groups.</span></span>
  
## <a name="phase-2-create-office-365-labels"></a><span data-ttu-id="4b4be-109">Fase 2: Crear etiquetas de Office 365</span><span class="sxs-lookup"><span data-stu-id="4b4be-109">Phase 2: Create Office 365 labels</span></span>

<span data-ttu-id="4b4be-110">En esta fase, crear las etiquetas para los diferentes niveles de seguridad de carpetas de documentos de SharePoint Online team site.</span><span class="sxs-lookup"><span data-stu-id="4b4be-110">In this phase, you create the labels for the different levels of security for SharePoint Online team site document folders.</span></span>
  
1. <span data-ttu-id="4b4be-p102">Si es necesario, iniciar sesión en el portal de Office 365 con las credenciales de la cuenta de administrador global de su suscripción de prueba. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="4b4be-p102">If needed, sign in to the Office 365 portal with the credentials of the global administrator account of your trial subscription. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="4b4be-113">Desde la ficha **Página de inicio de Microsoft Office** , haga clic en el mosaico de **Admin** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-113">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="4b4be-114">Desde la ficha del **Centro de administración de Office** nueva del explorador, haga clic en **centros de administración > seguridad &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-114">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="4b4be-115">Desde la nueva **Inicio - seguridad &amp; Compliance** ficha del explorador, haga clic en **las clasificaciones > etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-115">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="4b4be-116">Desde el **Home > etiquetas** panel, haga clic en **crear una etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-116">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="4b4be-117">En el panel **nombre de la etiqueta** , tipo **interno**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-117">On the **Name your label** pane, type **Internal**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="4b4be-118">En el panel de **configuración de etiquetas** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-118">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="4b4be-119">En el panel **Revisar la configuración** , haga clic en **crear esta etiqueta**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-119">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="4b4be-120">Repita los pasos 5 a 8 para estas etiquetas adicionales:</span><span class="sxs-lookup"><span data-stu-id="4b4be-120">Repeat steps 5-8 for these additional labels:</span></span>
    
  - <span data-ttu-id="4b4be-121">Privada</span><span class="sxs-lookup"><span data-stu-id="4b4be-121">Private</span></span>
    
  - <span data-ttu-id="4b4be-122">Confidencial</span><span class="sxs-lookup"><span data-stu-id="4b4be-122">Sensitive</span></span>
    
  - <span data-ttu-id="4b4be-123">Altamente confidencial</span><span class="sxs-lookup"><span data-stu-id="4b4be-123">Highly Confidential</span></span>
    
10. <span data-ttu-id="4b4be-124">Desde el **Home > etiquetas** panel, haga clic en **etiquetas de publicar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-124">From the **Home > Labels** pane, click **Publish labels**.</span></span>
    
11. <span data-ttu-id="4b4be-125">En el panel **etiquetas elegir publicar** , haga clic en **Elegir etiquetas para publicar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-125">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
12. <span data-ttu-id="4b4be-126">En el panel **etiquetas de elegir** , haga clic en **Agregar** y seleccione todas las etiquetas de cuatro.</span><span class="sxs-lookup"><span data-stu-id="4b4be-126">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
13. <span data-ttu-id="4b4be-127">Haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-127">Click **Done**.</span></span>
    
14. <span data-ttu-id="4b4be-128">En el panel **etiquetas elegir publicar** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-128">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
15. <span data-ttu-id="4b4be-129">En el panel **Elegir ubicaciones** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-129">On the **Choose locations** pane, click **Next**.</span></span>
    
16. <span data-ttu-id="4b4be-130">En el panel **nombre de la directiva** , escriba **nombre de** **campaña** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-130">On the **Name your policy** pane, type **Campaign** in **Name**, and then click **Next**.</span></span>
    
17. <span data-ttu-id="4b4be-131">En el panel **Revisar la configuración** , haga clic en **etiquetas de publicar**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-131">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
## <a name="phase-3-create-your-sharepoint-online-team-sites"></a><span data-ttu-id="4b4be-132">Fase 3: Crear sus sitios de equipo de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="4b4be-132">Phase 3: Create your SharePoint Online team sites</span></span>

<span data-ttu-id="4b4be-133">En esta fase, crear y configurar sitios de equipo de SharePoint Online para la campaña de política correspondientes a los cuatro tipos de sitios de grupo de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="4b4be-133">In this phase, you create and configure SharePoint Online team sites for your political campaign corresponding to the four types of SharePoint Online team sites.</span></span>
  
### <a name="campaign-wide-team-site"></a><span data-ttu-id="4b4be-134">Sitio de grupo amplio de campaña</span><span class="sxs-lookup"><span data-stu-id="4b4be-134">Campaign wide team site</span></span>

<span data-ttu-id="4b4be-135">Para crear un sitio de equipo de SharePoint Online público previsto, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4b4be-135">To create a baseline public SharePoint Online team site, do the following:</span></span>
  
1. <span data-ttu-id="4b4be-136">Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) mediante la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="4b4be-136">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="4b4be-137">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-137">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="4b4be-138">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-138">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="4b4be-139">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-139">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="4b4be-140">En **nombre del sitio**, escriba **campaña amplia**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-140">In **Site name**, type **Campaign wide**.</span></span> 
    
6. <span data-ttu-id="4b4be-141">En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para toda la campaña**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-141">In **Team site description**, type **SharePoint site for the entire campaign**.</span></span>
    
7. <span data-ttu-id="4b4be-142">En **la configuración de privacidad**, seleccione **pública - cualquier persona de la organización puede tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-142">In **Privacy settings**, select **Public - anyone in the organization can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4b4be-143">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-143">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="4b4be-144">A continuación, configure la carpeta de documentos del sitio del grupo amplia campaña para la etiqueta interna.</span><span class="sxs-lookup"><span data-stu-id="4b4be-144">Next, configure the documents folder of the Campaign wide team site for the Internal label.</span></span>
  
1. <span data-ttu-id="4b4be-145">En la ficha **toda la página de inicio de la campaña** del explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-145">In the **Campaign wide-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="4b4be-146">Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-146">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="4b4be-147">En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-147">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="4b4be-148">En **Aplicar configuración de etiqueta**, seleccione **interna**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-148">In **Settings-Apply Label**, select **Internal**, and then click **Save**.</span></span>
    
### <a name="campaign-project-1-team-site"></a><span data-ttu-id="4b4be-149">Sitio del grupo 1 de proyecto de campaña</span><span class="sxs-lookup"><span data-stu-id="4b4be-149">Campaign project 1 team site</span></span>

<span data-ttu-id="4b4be-150">Para crear un sitio de grupo de línea de base privado SharePoint Online para un proyecto dentro de la campaña, realice lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4b4be-150">To create a baseline private SharePoint Online team site for a project within the campaign, do the following:</span></span>
  
1. <span data-ttu-id="4b4be-151">Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) mediante la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="4b4be-151">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="4b4be-152">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-152">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="4b4be-153">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-153">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="4b4be-154">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-154">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="4b4be-155">En **nombre del sitio**, escriba **proyecto campaña 1**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-155">In **Site name**, type **Campaign project 1**.</span></span> 
    
6. <span data-ttu-id="4b4be-156">En la **Descripción del sitio de equipo,** escriba **el sitio de SharePoint para el proyecto de campaña 1**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-156">In **Team site description,** type **SharePoint site for Campaign project 1**.</span></span>
    
7. <span data-ttu-id="4b4be-157">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-157">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4b4be-158">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-158">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
<span data-ttu-id="4b4be-159">A continuación, configure la carpeta de documentos del sitio del grupo 1 proyecto campaña para la etiqueta privada.</span><span class="sxs-lookup"><span data-stu-id="4b4be-159">Next, configure the documents folder of the Campaign project 1 team site for the Private label.</span></span>
  
1. <span data-ttu-id="4b4be-160">En la ficha **proyecto 1-Inicio de la campaña** del explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-160">In the **Campaign project 1-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="4b4be-161">Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-161">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="4b4be-162">En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-162">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="4b4be-163">En **Aplicar configuración de etiqueta**, seleccione **privado**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-163">In **Settings-Apply Label**, select **Private**, and then click **Save**.</span></span>
    
### <a name="campaign-marketing-team-site"></a><span data-ttu-id="4b4be-164">Sitio de grupo de marketing de campaña</span><span class="sxs-lookup"><span data-stu-id="4b4be-164">Campaign marketing team site</span></span>

<span data-ttu-id="4b4be-165">Para crear un nivel sensible aislado SharePoint Online team sitio para la campaña de marketing de recursos, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4b4be-165">To create a sensitive-level isolated SharePoint Online team site for campaign marketing resources, do the following:</span></span>
  
1. <span data-ttu-id="4b4be-166">Mediante un explorador en el equipo local, inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) mediante la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="4b4be-166">Using a browser on your local computer, sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="4b4be-167">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-167">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="4b4be-168">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-168">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="4b4be-169">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-169">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="4b4be-170">En **nombre de sitio de equipo**, tipo de **campaña de marketing**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-170">In **Team site name**, type **Campaign marketing**.</span></span>
    
6. <span data-ttu-id="4b4be-171">En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para la campaña de marketing (confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-171">In **Team site description**, type **SharePoint site for campaign marketing (sensitive)**.</span></span>
    
7.  <span data-ttu-id="4b4be-172">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-172">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4b4be-173">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-173">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="4b4be-174">En la nueva ficha de **campaña de marketing** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-174">On the new **Campaign marketing** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="4b4be-175">En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-175">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="4b4be-176">En la ficha **permisos** de nuevo en el explorador, haga clic en **Configuración de solicitud de acceso**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-176">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="4b4be-177">En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive las casillas de verificación **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **miembros de permitir invitar a otras personas al grupo de miembros del sitio** , escriba **ITAdmin1 @** <your organization name> **. onmicrosoft.com** en **Enviar todas las solicitudes de acceso**y, a continuación, haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-177">In the **Access Request Settings** dialog box, clear the **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** check boxes, type **ITAdmin1@**<your organization name> **.onmicrosoft.com** in **Send all requests for access**, and then click **OK**.</span></span>
    
13. <span data-ttu-id="4b4be-178">Haga clic en **campaña de marketing a integrantes** de la lista.</span><span class="sxs-lookup"><span data-stu-id="4b4be-178">Click **Campaign marketing Members** in the list.</span></span>
    
14. <span data-ttu-id="4b4be-179">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-179">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="4b4be-180">En el cuadro de diálogo **Compartir** , escriba **Senior y personal estratégico**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-180">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="4b4be-181">Repita los pasos 14 y 15 para el grupo de **personal de análisis** y de la cuenta de usuario **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-181">Repeat steps 14 and 15 for the **Analytics staff** group and the **Regular1** user account.</span></span>
    
17. <span data-ttu-id="4b4be-182">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="4b4be-182">Click the back button on your browser.</span></span>
    
18. <span data-ttu-id="4b4be-183">En la lista, haga clic en **campaña de marketing a los propietarios** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-183">Click **Campaign marketing Owners** in the list.</span></span>
    
19. <span data-ttu-id="4b4be-184">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-184">On the **People and Groups** page, click **New**.</span></span>
    
20. <span data-ttu-id="4b4be-185">En el cuadro de diálogo **Compartir** , escriba **personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-185">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
21. <span data-ttu-id="4b4be-186">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="4b4be-186">Click the back button on your browser.</span></span>
    
22. <span data-ttu-id="4b4be-187">Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha de la **Página inicial de marketing de campaña** en el explorador y, a continuación, cierre el panel de **permisos del sitio** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-187">Close the **People and Groups** tab in your browser, click the **Campaign marketing-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="4b4be-188">A continuación se indican los resultados de la configuración de permisos:</span><span class="sxs-lookup"><span data-stu-id="4b4be-188">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="4b4be-189">El grupo de SharePoint de **Integrantes de marketing campaña** contiene sólo el **Director y el personal estratégico** grupo (que contiene las cuentas de usuario de candidato, ChiefOfStaff y Strategic1), el grupo de **campaña de marketing** (que contiene el cuenta de usuario de administrador global), el grupo de **personal de Analytics** (que contiene la cuenta de usuario de DataScientist1) y la cuenta de usuario **Regular1** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-189">The **Campaign marketing-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains the Candidate, ChiefOfStaff, and Strategic1 user accounts), the **Campaign marketing** group (which contains the global administrator user account), the **Analytics staff** group (which contains the DataScientist1 user account), and the **Regular1** user account.</span></span>
    
- <span data-ttu-id="4b4be-190">El grupo de SharePoint **Propietarios de marketing campaña** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="4b4be-190">The **Campaign marketing-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="4b4be-191">El grupo de SharePoint **Visitantes de marketing de campaña** no contiene grupos o cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="4b4be-191">The **Campaign marketing-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="4b4be-192">Los miembros no pueden modificar los permisos de nivel de sitio (Esto sólo es posible miembros del grupo **Propietarios de marketing de campaña** ).</span><span class="sxs-lookup"><span data-stu-id="4b4be-192">Members cannot modify site-level permissions (this can only be done by members of the **Campaign marketing-Owners** group).</span></span>
    
- <span data-ttu-id="4b4be-193">Otras cuentas de usuario no tiene acceso a sus recursos o el sitio, pero pueden solicitar el acceso al sitio, que enviará un correo electrónico al buzón de la cuenta de usuario de ITAdmin1.</span><span class="sxs-lookup"><span data-stu-id="4b4be-193">Other user accounts cannot access the site or its resources, but can request access to the site, which will send an email to the ITAdmin1 user account mailbox.</span></span>
    
<span data-ttu-id="4b4be-194">A continuación, configure la carpeta de documentos del sitio grupo marketing campaña para la etiqueta sensible.</span><span class="sxs-lookup"><span data-stu-id="4b4be-194">Next, configure the documents folder of the Campaign marketing team site for the Sensitive label.</span></span>
  
1. <span data-ttu-id="4b4be-195">En la ficha de la **Página inicial de marketing de campaña** del explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-195">In the **Campaign marketing-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="4b4be-196">Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-196">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="4b4be-197">En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-197">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="4b4be-198">En **Aplicar configuración de etiqueta**, seleccione **confidencial**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-198">In **Settings-Apply Label**, select **Sensitive**, and then click **Save**.</span></span>
    
<span data-ttu-id="4b4be-p103">A continuación, configurar una directiva de prevention (DLP) de pérdida de datos que notifica a los usuarios que comparten un documento en un sitio de grupo SharePoint Online con la etiqueta confidencial fuera de la organización. Esta directiva DLP se aplicará a los recursos en el sitio de marketing de la campaña.</span><span class="sxs-lookup"><span data-stu-id="4b4be-p103">Next, configure a data loss prevention (DLP) policy that notifies users when they share a document on a SharePoint Online team site with the Sensitive label outside the organization. This DLP policy will apply to resources in the Campaign marketing site.</span></span>
  
1. <span data-ttu-id="4b4be-201">En la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; Compliance** mosaico.</span><span class="sxs-lookup"><span data-stu-id="4b4be-201">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="4b4be-202">En el nuevo **seguridad &amp; Compliance** , haga clic en el explorador **prevención de pérdidas de datos > directiva de**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-202">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="4b4be-203">En el panel de **prevención de pérdidas de datos** , haga clic en **+ crear una directiva**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-203">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="4b4be-204">En el **comenzar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-204">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="4b4be-205">En el panel **nombre de la directiva** , escriba **sitios de equipo de SharePoint Online etiqueta sensible** en **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-205">In the **Name your policy** pane, type **Sensitive label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="4b4be-206">En el panel **Elegir ubicaciones** , haga clic en **Dejarme elegir ubicaciones específicas**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-206">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="4b4be-207">En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-207">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4b4be-208">En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-208">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="4b4be-209">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-209">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="4b4be-210">En el panel **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-210">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="4b4be-211">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-211">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="4b4be-212">En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-212">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="4b4be-213">En la **¿Qué desea hacer si se detecta información sensible?** panel, haga clic en **Personalizar la sugerencia y correo electrónico**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-213">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="4b4be-214">En el panel de **sugerencias de directiva personalizar y notificaciones por correo electrónico** , haga clic en **Personalizar el texto de sugerencia de directiva**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-214">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="4b4be-215">En el cuadro texto, escriba o pegue lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4b4be-215">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="4b4be-p104">Para compartir con otros usuarios fuera de la organización, descargue el archivo y, a continuación, ábralo. Haga clic en archivo, a continuación, Proteger documento y a continuación, cifrar con contraseña y, a continuación, especifique una contraseña segura. Enviar la contraseña en un correo electrónico u otros medios de comunicación.</span><span class="sxs-lookup"><span data-stu-id="4b4be-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
16. <span data-ttu-id="4b4be-219">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-219">Click **OK**.</span></span>
    
17. <span data-ttu-id="4b4be-220">En la **¿Qué desea hacer si se detecta información sensible?** panel, desactive la casilla de verificación **Bloquear personas compartan y restringir el acceso al contenido compartido** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-220">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="4b4be-221">En el **¿desea activar las cosas de la política o prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-221">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="4b4be-222">En el panel **Revisar la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-222">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
### <a name="campaign-strategy-team-site"></a><span data-ttu-id="4b4be-223">Sitio de grupo de estrategia de campaña</span><span class="sxs-lookup"><span data-stu-id="4b4be-223">Campaign strategy team site</span></span>

<span data-ttu-id="4b4be-224">Para crear un sitio de grupo SharePoint Online aislado en el nivel de recursos de estrategia de campaña altamente confidencial, haga lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4b4be-224">To create an isolated SharePoint Online team site at the highly confidential level for campaign strategy resources, do the following:</span></span>
  
1. <span data-ttu-id="4b4be-225">Si es necesario, utilice un explorador en el equipo local e inicie sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) mediante la cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="4b4be-225">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) using your global administrator account.</span></span>
    
2. <span data-ttu-id="4b4be-226">En la lista de fichas, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-226">In the list of tiles, click **SharePoint**.</span></span>
    
3. <span data-ttu-id="4b4be-227">En la ficha nuevo de **SharePoint** en el explorador, haga clic en **Crear sitio +**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-227">On the new **SharePoint** tab in your browser, click **+ Create site**.</span></span>
    
4. <span data-ttu-id="4b4be-228">En la página **crear un sitio Web** , haga clic en **sitio de equipo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-228">On the **Create a site** page, click **Team site**.</span></span>
    
5. <span data-ttu-id="4b4be-229">En **nombre de sitio de equipo**, escriba **la estrategia de campaña**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-229">In **Team site name**, type **Campaign strategy**.</span></span>
    
6. <span data-ttu-id="4b4be-230">En **Descripción del sitio de equipo**, escriba el **sitio de SharePoint para la estrategia de campaña (confidencial)**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-230">In **Team site description**, type **SharePoint site for campaign strategy (highly confidential)**.</span></span>
    
7.  <span data-ttu-id="4b4be-231">En **la configuración de privacidad**, seleccione **Private: sólo los miembros pueden tener acceso a este sitio**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-231">In **Privacy settings**, select **Private - only members can access this site**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4b4be-232">En el **que desea agregar?** panel, haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-232">On the **Who do you want to add?** pane, click **Finish**.</span></span>
    
9. <span data-ttu-id="4b4be-233">En la ficha nuevo de **la estrategia de campaña** en el explorador, en la barra de herramientas, haga clic en el icono de configuración y, a continuación, haga clic en **permisos del sitio**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-233">On the new **Campaign strategy** tab in your browser, in the tool bar, click the settings icon, and then click **Site permissions**.</span></span>
    
10. <span data-ttu-id="4b4be-234">En el panel **permisos de sitio** , haga clic en **configuración de permisos avanzados**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-234">In the **Site permissions** pane, click **Advanced permissions settings**.</span></span>
    
11. <span data-ttu-id="4b4be-235">En la ficha **permisos** de nuevo en el explorador, haga clic en **Configuración de solicitud de acceso**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-235">In the new **Permissions** tab in your browser, click **Access Request Settings**.</span></span>
    
12. <span data-ttu-id="4b4be-236">En el cuadro de diálogo **Configuración de solicitud de acceso** , desactive **Permitir miembros para compartir el sitio y archivos y carpetas individuales** y **miembros de permitir invitar a otras personas al grupo de miembros del sitio** (de modo que todas las casillas de verificación está desactivadas) y, a continuación, haga clic en ** Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-236">In the **Access Request Settings** dialog box, clear **Allow members to share the site and individual files and folders** and **Allow members to invite others to the site members group** (so that all three check boxes are cleared), and then click **OK**.</span></span>
    
13. <span data-ttu-id="4b4be-237">En la lista, haga clic en **los miembros de la estrategia de campaña** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-237">Click **Campaign strategy Members** in the list.</span></span>
    
14. <span data-ttu-id="4b4be-238">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-238">On the **People and Groups** page, click **New**.</span></span>
    
15. <span data-ttu-id="4b4be-239">En el cuadro de diálogo **Compartir** , escriba **Senior y personal estratégico**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-239">In the **Share** dialog box, type **Senior and strategic staff**, select it, and then click **Share**.</span></span>
    
16. <span data-ttu-id="4b4be-240">En la lista, haga clic en **la estrategia de campaña propietarios** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-240">Click **Campaign strategy Owners** in the list.</span></span>
    
17. <span data-ttu-id="4b4be-241">En la página **personas y grupos** , haga clic en **nuevo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-241">On the **People and Groups** page, click **New**.</span></span>
    
18. <span data-ttu-id="4b4be-242">En el cuadro de diálogo **Compartir** , escriba **personal de TI**, selecciónelo y, a continuación, haga clic en **Compartir**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-242">In the **Share** dialog box, type **IT staff**, select it, and then click **Share**.</span></span>
    
19. <span data-ttu-id="4b4be-243">Haga clic en el botón Atrás del explorador.</span><span class="sxs-lookup"><span data-stu-id="4b4be-243">Click the back button on your browser.</span></span>
    
20. <span data-ttu-id="4b4be-244">Cierre la ficha **personas y grupos** en el explorador, haga clic en la ficha **principal de la estrategia de campaña** en el explorador y, a continuación, cierre el panel de **permisos del sitio** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-244">Close the **People and Groups** tab in your browser, click the **Campaign strategy-Home** tab in your browser, and then close the **Site permissions** pane.</span></span>
    
<span data-ttu-id="4b4be-245">A continuación se indican los resultados de la configuración de permisos:</span><span class="sxs-lookup"><span data-stu-id="4b4be-245">Here are the results of configuring permissions:</span></span>
  
- <span data-ttu-id="4b4be-246">El grupo de SharePoint **Miembros de estrategia de campaña** contiene sólo el grupo de **personal estratégico y Senior** (que contiene sólo las cuentas de usuario de candidato, ChiefOfStaff y Strategic1) y el grupo de **estrategia de campaña** (que contiene sólo la cuenta de administrador global).</span><span class="sxs-lookup"><span data-stu-id="4b4be-246">The **Campaign strategy-Members** SharePoint group contains only the **Senior and strategic staff** group (which contains only the Candidate, ChiefOfStaff, and Strategic1 user accounts) and the **Campaign strategy** group (which contains only the global administrator user account).</span></span>
    
- <span data-ttu-id="4b4be-247">El grupo de SharePoint **Propietarios de estrategia de campaña** contiene sólo el grupo de **personal de TI** (que contiene sólo las cuentas de usuario ITAdmin1 y ITAdmin2).</span><span class="sxs-lookup"><span data-stu-id="4b4be-247">The **Campaign strategy-Owners** SharePoint group contains only the **IT staff** group (which contains only the ITAdmin1 and ITAdmin2 user accounts).</span></span>
    
- <span data-ttu-id="4b4be-248">El grupo de SharePoint **Visitantes de estrategia de campaña** no contiene grupos o cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="4b4be-248">The **Campaign strategy-Visitors** SharePoint group contains no groups or user accounts.</span></span>
    
- <span data-ttu-id="4b4be-249">Los miembros no pueden modificar los permisos de nivel de sitio (Esto sólo es posible miembros del grupo **Propietarios de estrategia de campaña** ).</span><span class="sxs-lookup"><span data-stu-id="4b4be-249">Members cannot modify site-level permissions (this can only be done by members of the **Campaign strategy-Owners** group).</span></span>
    
- <span data-ttu-id="4b4be-p105">Otras cuentas de usuario no pueden tener acceso a sus recursos o el sitio o solicitar acceso al sitio. Permisos adicionales para el sitio deben realizarse por el administrador global o por un miembro del grupo de **Propietarios de estrategia de campaña** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-p105">Other user accounts cannot access the site or its resources or request access to the site. Additional permissions to the site must be done by the global administrator or by a member of the **Campaign strategy-Owners** group.</span></span>
    
<span data-ttu-id="4b4be-252">A continuación, configure la carpeta de documentos del sitio de grupo de estrategia de campaña para la etiqueta altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="4b4be-252">Next, configure the documents folder of the Campaign strategy team site for the Highly Confidential label.</span></span>
  
1. <span data-ttu-id="4b4be-253">En la ficha **principal de la estrategia de campaña** del explorador, haga clic en **documentos**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-253">In the **Campaign strategy-Home** tab of your browser, click **Documents**.</span></span>
    
2. <span data-ttu-id="4b4be-254">Haga clic en el icono de configuración y, a continuación, haga clic en **configuración de la biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-254">Click the settings icon, and then click **Library settings**.</span></span>
    
3. <span data-ttu-id="4b4be-255">En **permisos y administración**, haga clic en **Aplicar etiqueta a los elementos de esta biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-255">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
4. <span data-ttu-id="4b4be-256">En **Aplicar configuración de etiqueta**, seleccione **Confidencial**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-256">In **Settings-Apply Label**, select **Highly Confidential**, and then click **Save**.</span></span>
    
<span data-ttu-id="4b4be-p106">A continuación, configure una directiva DLP que impide a los usuarios cuando se comparten un documento en un sitio de grupo SharePoint Online con la etiqueta altamente confidencial fuera de la organización. Esta directiva DLP se aplicará a los recursos en el sitio de la estrategia de campaña.</span><span class="sxs-lookup"><span data-stu-id="4b4be-p106">Next, configure a DLP policy that blocks users when they share a document on a SharePoint Online team site with the Highly Confidential label outside the organization. This DLP policy will apply to resources in the Campaign strategy site.</span></span>
  
1. <span data-ttu-id="4b4be-259">Si es necesario, utilizar un explorador en el equipo local e iniciar sesión en el portal de Office 365 ([https://portal.office.com](https://portal.office.com)) con una cuenta que tiene la función de administrador de seguridad o de la empresa.</span><span class="sxs-lookup"><span data-stu-id="4b4be-259">If needed, use a browser on your local computer and sign in to the Office 365 portal ([https://portal.office.com](https://portal.office.com)) with an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="4b4be-260">En la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; Compliance** mosaico.</span><span class="sxs-lookup"><span data-stu-id="4b4be-260">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
3. <span data-ttu-id="4b4be-261">En el nuevo **seguridad &amp; Compliance** , haga clic en el explorador **prevención de pérdidas de datos > directiva de**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-261">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
4. <span data-ttu-id="4b4be-262">En el panel de **prevención de pérdidas de datos** , haga clic en **+ crear una directiva**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-262">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
5. <span data-ttu-id="4b4be-263">En el **comenzar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-263">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="4b4be-264">En el panel **nombre de la directiva** , escriba **sitios de equipo de SharePoint Online de etiqueta altamente confidencial** en **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-264">In the **Name your policy** pane, type **Highly Confidential label SharePoint Online team sites** in **Name**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="4b4be-265">En el panel **Elegir ubicaciones** , haga clic en **Dejarme elegir ubicaciones específicas**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-265">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="4b4be-266">En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-266">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
9. <span data-ttu-id="4b4be-267">En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-267">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
10. <span data-ttu-id="4b4be-268">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-268">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
11. <span data-ttu-id="4b4be-269">En el panel **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **Altamente confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-269">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
12. <span data-ttu-id="4b4be-270">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-270">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
13. <span data-ttu-id="4b4be-271">En el panel **Personalizar los tipos de información confidencial que desea proteger** , haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-271">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
14. <span data-ttu-id="4b4be-272">En la **¿Qué desea hacer si se detecta información sensible?** panel, haga clic en **Personalizar la sugerencia y correo electrónico**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-272">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
15. <span data-ttu-id="4b4be-273">En el panel de **sugerencias de directiva personalizar y notificaciones por correo electrónico** , haga clic en **Personalizar el texto de sugerencia de directiva**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-273">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
16. <span data-ttu-id="4b4be-274">En el cuadro texto, escriba o pegue lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="4b4be-274">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="4b4be-p107">Para compartir con otros usuarios fuera de la organización, descargue el archivo y, a continuación, ábralo. Haga clic en archivo, a continuación, Proteger documento y a continuación, cifrar con contraseña y, a continuación, especifique una contraseña segura. Enviar la contraseña en un correo electrónico u otros medios de comunicación.</span><span class="sxs-lookup"><span data-stu-id="4b4be-p107">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
17. <span data-ttu-id="4b4be-278">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-278">Click **OK**.</span></span>
    
18. <span data-ttu-id="4b4be-279">En la **¿Qué desea hacer si se detecta información sensible?** panel, seleccione **requerir una justificación comercial para reemplazar**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-279">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="4b4be-280">En el **¿desea activar las cosas de la política o prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-280">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
20. <span data-ttu-id="4b4be-281">En el panel **Revisar la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-281">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="4b4be-282">Siga las instrucciones de [Activar Azure RMS con el centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span><span class="sxs-lookup"><span data-stu-id="4b4be-282">Use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="4b4be-283">A continuación, configurar la protección de la información de Azure con una nueva directiva con ámbito y Sub-etiqueta de protección y los permisos con los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="4b4be-283">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions with the following steps:</span></span>
  
1. <span data-ttu-id="4b4be-p108">Iniciar sesión en el portal de Office 365 con una cuenta que tiene la función de administrador de seguridad o de la empresa. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="4b4be-p108">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="4b4be-286">En una ficha independiente del explorador, vaya al portal de Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="4b4be-286">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="4b4be-287">Si es la primera vez se configura la protección de la información de Azure, consulte estas [instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="4b4be-287">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="4b4be-288">En el panel lista, haga clic en **más servicios**, escriba la **información**y, a continuación, haga clic en **Protección de la información de Azure**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-288">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="4b4be-289">En la hoja de **protección de la información de Azure** , haga clic en **ámbito directivas > + Agregar una nueva directiva de**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-289">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="4b4be-290">En **nombre de directiva** y la **etiqueta para los documentos en el sitio del equipo de estrategia de campaña** en **Descripción**, escriba **CampaignStrategy** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-290">Type **CampaignStrategy** in **Policy name** and **Label for documents in the Campaign strategy team site** in **Description**.</span></span>
    
7. <span data-ttu-id="4b4be-291">Haga clic en **Seleccionar qué usuarios o grupos Obtén esta directiva > usuario/grupos**y luego seleccione **Senior y personal estratégico**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-291">Click **Select which users or groups get this policy > User/Groups**, and then select **Senior and strategic staff**.</span></span>
    
8. <span data-ttu-id="4b4be-292">Haga clic en **Seleccionar > Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-292">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="4b4be-293">Para la etiqueta **Altamente confidencial** , haga clic en los puntos suspensivos (...) y, a continuación, haga clic en **Agregar una etiqueta Sub**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-293">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="4b4be-294">Escriba un nombre para la Sub-etiqueta de **nombre** y una descripción de la etiqueta de **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-294">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="4b4be-295">**Establecer permisos para documentos y correos electrónicos con esta etiqueta**, haga clic en **proteger**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-295">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="4b4be-296">En la sección de **protección** , haga clic en **Azure (clave de nube)**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-296">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="4b4be-297">En la hoja de **protección** , en **configuración de protección**, haga clic en **+ Agregar permisos**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-297">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="4b4be-298">En la hoja de **permisos para agregar** , en **especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-298">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="4b4be-299">En el panel de **DAA usuarios y grupos** , seleccione el **Director y el personal estratégico**y, a continuación, haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-299">On the **AAD Users and Groups** pane, select **Senior and strategic staff**, and then click **Select**.</span></span>
    
16. <span data-ttu-id="4b4be-300">En **Elija el ajuste preestablecido los permisos**, desactive las casillas de verificación **Imprimir**, **Copiar y extraer contenido**y **hacia delante** .</span><span class="sxs-lookup"><span data-stu-id="4b4be-300">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="4b4be-301">Haga clic en **Aceptar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="4b4be-301">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="4b4be-302">En la hoja **secundario-etiqueta** , haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-302">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="4b4be-303">Cierre el nuevo blade de ámbito de la política.</span><span class="sxs-lookup"><span data-stu-id="4b4be-303">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="4b4be-304">En el módulo de **protección de la información de Azure - directivas de ámbito** , haga clic en **Publicar**y, a continuación, haga clic en **Sí**.</span><span class="sxs-lookup"><span data-stu-id="4b4be-304">On the **Azure Information protection - Scoped policies** blade, click **Publish**, and then click **Yes**.</span></span>
    
<span data-ttu-id="4b4be-305">Ahora está listo para empezar a crear documentos en estos cuatro sitios y probar el acceso a ellos con varias cuentas de usuario en su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="4b4be-305">You are now ready to begin creating documents in these four sites and test access to them with various user accounts in your trial subscription.</span></span> 
  
<span data-ttu-id="4b4be-306">Para proteger un documento con la protección de la información de Azure y esta nueva etiqueta, debe [instalar al cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en un equipo de prueba, instalar Office desde el portal de Office 365 y, a continuación, iniciar sesión en desde Microsoft Word con una cuenta en el ** Director y el personal estratégico** grupo de su suscripción de prueba.</span><span class="sxs-lookup"><span data-stu-id="4b4be-306">To protect a document with Azure Information Protection and this new label, you must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on a test machine, install Office from the Office 365 portal, and then sign in from Microsoft Word with an account in the **Senior and strategic staff** group of your trial subscription.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4b4be-307">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4b4be-307">See Also</span></span>

[<span data-ttu-id="4b4be-308">Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile</span><span class="sxs-lookup"><span data-stu-id="4b4be-308">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="4b4be-309">Configurar grupos y usuarios de un entorno de pruebas y desarrollo de campaña política</span><span class="sxs-lookup"><span data-stu-id="4b4be-309">Configure groups and users for a political campaign dev/test environment</span></span>](configure-groups-and-users-for-a-political-campaign-dev-test-environment.md)
  
[<span data-ttu-id="4b4be-310">Guías de entorno de pruebas de adopción de la nube (TLG)</span><span class="sxs-lookup"><span data-stu-id="4b4be-310">Cloud adoption Test Lab Guides (TLGs)</span></span>](cloud-adoption-test-lab-guides-tlgs.md)
  
[<span data-ttu-id="4b4be-311">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="4b4be-311">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




