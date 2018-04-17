---
title: Proteger archivos de SharePoint Online con etiquetas de Office 365 y DLP
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
ms.assetid: c9f837af-8d71-4df1-a285-dedb1c5618b3
description: 'Resumen: Aplicar Office 365 rótulos y datos pérdida prevention (DLP) directivas para sitios de equipo de SharePoint Online con varios niveles de protección de la información.'
ms.openlocfilehash: a6413ac556cf63cbe7491180d65b4425cd0dba3d
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="protect-sharepoint-online-files-with-office-365-labels-and-dlp"></a><span data-ttu-id="7e80f-103">Proteger archivos de SharePoint Online con etiquetas de Office 365 y DLP</span><span class="sxs-lookup"><span data-stu-id="7e80f-103">Protect SharePoint Online files with Office 365 labels and DLP</span></span>

 <span data-ttu-id="7e80f-104">**Resumen:** Aplicar Office 365 rótulos y datos pérdida prevention (DLP) directivas para sitios de equipo de SharePoint Online con varios niveles de protección de la información.</span><span class="sxs-lookup"><span data-stu-id="7e80f-104">**Summary:** Apply Office 365 labels and data loss prevention (DLP) policies for SharePoint Online team sites with various levels of information protection.</span></span>
  
<span data-ttu-id="7e80f-p101">Utilice los pasos de este artículo para diseñar e implementar Office 365 etiquetas y las directivas DLP de línea de base, sensibles y altamente confidenciales SharePoint Online sitios team. Para obtener más información acerca de estos tres niveles de protección, vea [archivos y sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="7e80f-p101">Use the steps in this article to design and deploy Office 365 labels and DLP policies for baseline, sensitive, and highly confidential SharePoint Online team sites. For more information about these three tiers of protection, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
## <a name="office-365-labels-for-your-sharepoint-online-sites"></a><span data-ttu-id="7e80f-107">Etiquetas de Office 365 para los sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e80f-107">Office 365 labels for your SharePoint Online sites</span></span>

<span data-ttu-id="7e80f-108">Hay tres fases para crear y asignarle Office 365 etiquetas a los sitios de equipo de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e80f-108">There are three phases to creating and then assigning Office 365 labels to SharePoint Online team sites.</span></span>
  
### <a name="phase-1-determine-the-office-365-label-names"></a><span data-ttu-id="7e80f-109">Fase 1: Determinar los nombres de etiqueta de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e80f-109">Phase 1: Determine the Office 365 label names</span></span>

<span data-ttu-id="7e80f-p102">En esta fase se determinan los nombres de las etiquetas de Office 365 para los cuatro niveles de protección de la información aplicados a los sitios de grupo de SharePoint Online. En la siguiente tabla se indican los nombres recomendados para cada nivel.</span><span class="sxs-lookup"><span data-stu-id="7e80f-p102">In this phase, you determine the names of your Office 365 labels for the four levels of information protection applied to SharePoint Online team sites. The following table lists the recommended names for each level.</span></span>
  
|<span data-ttu-id="7e80f-112">**Nivel de protección de sitio de grupo de SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="7e80f-112">**SharePoint Online team site protection level**</span></span>|<span data-ttu-id="7e80f-113">**Nombre de etiqueta**</span><span class="sxs-lookup"><span data-stu-id="7e80f-113">**Label name**</span></span>|
|:-----|:-----|
|<span data-ttu-id="7e80f-114">Base de referencia-Público</span><span class="sxs-lookup"><span data-stu-id="7e80f-114">Baseline-Public</span></span>  <br/> |<span data-ttu-id="7e80f-115">Interno público</span><span class="sxs-lookup"><span data-stu-id="7e80f-115">Internal public</span></span>  <br/> |
|<span data-ttu-id="7e80f-116">Base de referencia-Privado</span><span class="sxs-lookup"><span data-stu-id="7e80f-116">Baseline-Private</span></span>  <br/> |<span data-ttu-id="7e80f-117">Private</span><span class="sxs-lookup"><span data-stu-id="7e80f-117">Private</span></span>  <br/> |
|<span data-ttu-id="7e80f-118">Confidencial</span><span class="sxs-lookup"><span data-stu-id="7e80f-118">Sensitive</span></span>  <br/> |<span data-ttu-id="7e80f-119">Confidencial</span><span class="sxs-lookup"><span data-stu-id="7e80f-119">Sensitive</span></span>  <br/> |
|<span data-ttu-id="7e80f-120">Extremadamente confidencial</span><span class="sxs-lookup"><span data-stu-id="7e80f-120">Highly Confidential</span></span>  <br/> |<span data-ttu-id="7e80f-121">Extremadamente confidencial</span><span class="sxs-lookup"><span data-stu-id="7e80f-121">Highly Confidential</span></span>  <br/> |
   
### <a name="phase-2-create-the-office-365-labels"></a><span data-ttu-id="7e80f-122">Fase 2: Crear las etiquetas de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e80f-122">Phase 2: Create the Office 365 labels</span></span>

<span data-ttu-id="7e80f-123">En esta fase se crean y luego se publican las etiquetas determinadas para los diferentes niveles de protección de la información.</span><span class="sxs-lookup"><span data-stu-id="7e80f-123">In this phase, you create and then publish your determined labels for the different levels of information protection.</span></span>
  
<span data-ttu-id="7e80f-124">Para crear las etiquetas, puede usar el Centro de administración de Office 365 o Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7e80f-124">To create the labels, you can use the Office 365 Admin center or Microsoft PowerShell.</span></span>
  
### <a name="create-office-365-labels-with-the-office-365-admin-center"></a><span data-ttu-id="7e80f-125">Crear etiquetas de Office 365 con el centro de administración de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e80f-125">Create Office 365 labels with the Office 365 Admin center</span></span>

1. <span data-ttu-id="7e80f-p103">Iniciar sesión en el portal de Office 365 con una cuenta que tiene la función de administrador de seguridad o de la empresa. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="7e80f-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="7e80f-128">En la pestaña de **inicio de Microsoft Office**, haga clic en el icono **Administración**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-128">From the **Microsoft Office Home** tab, click the **Admin** tile.</span></span>
    
3. <span data-ttu-id="7e80f-129">Desde la ficha del **Centro de administración de Office** nueva del explorador, haga clic en **centros de administración > seguridad &amp; Compliance**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-129">From the new **Office Admin center** tab of your browser, click **Admin centers > Security &amp; Compliance**.</span></span>
    
4. <span data-ttu-id="7e80f-130">Desde la nueva **Inicio - seguridad &amp; Compliance** ficha del explorador, haga clic en **las clasificaciones > etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-130">From the new **Home - Security &amp; Compliance** tab of your browser, click **Classifications > Labels**.</span></span>
    
5. <span data-ttu-id="7e80f-131">En el panel **Inicio > Etiquetas**, haga clic en **Crear una etiqueta**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-131">From the **Home > Labels** pane, click **Create a label**.</span></span>
    
6. <span data-ttu-id="7e80f-132">En el panel **nombre de la etiqueta** , escriba el nombre de la etiqueta y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-132">On the **Name your label** pane, type the name of the label, and then click **Next**.</span></span>
    
7. <span data-ttu-id="7e80f-133">En el panel **Configuración de etiquetas**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-133">On the **Label settings** pane, click **Next**.</span></span>
    
8. <span data-ttu-id="7e80f-134">En el panel **Revisar la configuración** , haga clic en **crear esta etiqueta**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-134">On the **Review your settings** pane, click **Create this label**, and then click **Close**.</span></span>
    
9. <span data-ttu-id="7e80f-135">Repita los pasos del 5 al 8 para las etiquetas adicionales.</span><span class="sxs-lookup"><span data-stu-id="7e80f-135">Repeat steps 5-8 for your additional labels.</span></span>
    
### <a name="create-office-365-labels-with-powershell"></a><span data-ttu-id="7e80f-136">Crear etiquetas de Office 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="7e80f-136">Create Office 365 labels with PowerShell</span></span>

1. <span data-ttu-id="7e80f-137">[Conectar con la seguridad de Office 365 &amp; centro de cumplimiento de normas mediante PowerShell remoto](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) y especifique las credenciales de una cuenta que tiene la función de administrador de seguridad o de la empresa.</span><span class="sxs-lookup"><span data-stu-id="7e80f-137">[Connect to the Office 365 Security &amp; Compliance Center using remote PowerShell](http://go.microsoft.com/fwlink/?LinkID=799771&amp;clcid=0x409) and specify the credentials of an account that has the Security Administrator or Company Administrator role.</span></span>
    
2. <span data-ttu-id="7e80f-138">Rellene la lista de nombres de etiqueta y luego ejecute estos comandos en el símbolo del sistema de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7e80f-138">Fill out the list of label names, and then run these commands at the PowerShell command prompt:</span></span>
    
  ```
  $labelNames=@(<list of label names, each enclosed in quotes and separated by commas>)
ForEach ($element in $labelNames){ New-ComplianceTag -Name $element }
  ```

<span data-ttu-id="7e80f-139">Luego siga estos pasos para publicar las nuevas etiquetas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e80f-139">Next, use these steps to publish the new Office 365 labels.</span></span>
  
1. <span data-ttu-id="7e80f-140">Desde el **Home > etiquetas** panel la seguridad &amp; centro de cumplimiento de normas, haga clic en **etiquetas de publicar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-140">From the **Home > Labels** pane the Security &amp; Compliance Center, click **Publish labels**.</span></span>
    
2. <span data-ttu-id="7e80f-141">En el panel para **elegir las etiquetas que se van a publicar**, haga clic para **elegir las etiquetas que se van a publicar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-141">On the **Choose labels to publish** pane, click **Choose labels to publish**.</span></span>
    
3. <span data-ttu-id="7e80f-142">En el panel de **elección de etiquetas**, haga clic en **Agregar** y seleccione las cuatro etiquetas.</span><span class="sxs-lookup"><span data-stu-id="7e80f-142">On the **Choose labels** pane, click **Add** and select all four labels.</span></span>
    
4. <span data-ttu-id="7e80f-143">Haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-143">Click **Done**.</span></span>
    
5. <span data-ttu-id="7e80f-144">En el panel **Choose labels to publish** (Elegir las etiquetas que se van a publicar), haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-144">On the **Choose labels to publish** pane, click **Next**.</span></span>
    
6. <span data-ttu-id="7e80f-145">En el panel **Elegir ubicaciones**, haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-145">On the **Choose locations** pane, click **Next**.</span></span>
    
7. <span data-ttu-id="7e80f-146">En el panel **nombre de la directiva** , escriba un nombre para el conjunto de etiquetas de **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-146">On the **Name your policy** pane, type a name for your set of labels in **Name**, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7e80f-147">En el panel **Revisar la configuración** , haga clic en **etiquetas de publicar**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-147">On the **Review your settings** pane, click **Publish labels**, and then click **Close**.</span></span>
    
### <a name="phase-3-apply-the-office-365-labels-to-your-sharepoint-online-sites"></a><span data-ttu-id="7e80f-148">Fase 3: Aplicar las etiquetas de Office 365 a los sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e80f-148">Phase 3: Apply the Office 365 labels to your SharePoint Online sites</span></span>

<span data-ttu-id="7e80f-149">Siga estos pasos para aplicar las etiquetas de Office 365 a las carpetas de documentos de los sitios de grupo de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e80f-149">Use these steps to apply the Office 365 labels to the documents folders of your SharePoint Online team sites.</span></span>
  
1. <span data-ttu-id="7e80f-150">En la pestaña **Inicio de Microsoft Office** del explorador, haga clic en el icono **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-150">From the **Microsoft Office Home** tab of your browser, click the **SharePoint** tile.</span></span>
    
2. <span data-ttu-id="7e80f-151">En la nueva pestaña **SharePoint** del explorador, haga clic en un sitio al que haya que asignarle una etiqueta de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e80f-151">On the new **SharePoint** tab in your browser, click a site that needs an Office 365 label assigned.</span></span>
    
3. <span data-ttu-id="7e80f-152">En la nueva pestaña del sitio de SharePoint del explorador, haga clic en **Documentos**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-152">In the new SharePoint site tab of your browser, click **Documents**.</span></span>
    
4. <span data-ttu-id="7e80f-153">Haga clic en el icono de configuración y luego en **Configuración de biblioteca**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-153">Click the settings icon, and then click **Library settings**.</span></span>
    
5. <span data-ttu-id="7e80f-154">En **Permisos y administración**, haga clic en **Apply label to items in this library** (Aplicar la etiqueta a los elementos de esta biblioteca).</span><span class="sxs-lookup"><span data-stu-id="7e80f-154">Under **Permissions and Management**, click **Apply label to items in this library**.</span></span>
    
6. <span data-ttu-id="7e80f-155">En **Aplicar configuración de etiqueta**, seleccione la etiqueta adecuada y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-155">In **Settings-Apply Label**, select the appropriate label, and then click **Save**.</span></span>
    
7. <span data-ttu-id="7e80f-156">Cierre la pestaña del sitio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e80f-156">Close the tab for the SharePoint Online site.</span></span>
    
8. <span data-ttu-id="7e80f-157">Repita los pasos del 3 al 8 para asignar etiquetas de Office 365 a otros sitios de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e80f-157">Repeat steps 3-8 to assign Office 365 labels to your additional SharePoint Online sites.</span></span>
    
<span data-ttu-id="7e80f-158">Esta es la configuración resultante.</span><span class="sxs-lookup"><span data-stu-id="7e80f-158">Here is your resulting configuration.</span></span>
  
![Etiquetas de Office 365 para los cuatro tipos de sitios de grupo de SharePoint Online.](images/e0a4fdd2-1c30-4d93-8af4-a6f0c6c29966.png)
  
## <a name="dlp-policies-for-your-sharepoint-online-sites"></a><span data-ttu-id="7e80f-160">Directivas de DLP para los sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e80f-160">DLP policies for your SharePoint Online sites</span></span>

<span data-ttu-id="7e80f-161">Siga estos pasos para configurar una directiva de DLP que notifique a los usuarios cada vez que compartan un documento en un sitio de grupo confidencial de SharePoint Online de fuera de la organización.</span><span class="sxs-lookup"><span data-stu-id="7e80f-161">Use these steps to configure a DLP policy that notifies users when they share a document on a SharePoint Online sensitive team site outside the organization.</span></span>
  
1. <span data-ttu-id="7e80f-162">En la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; Compliance** mosaico.</span><span class="sxs-lookup"><span data-stu-id="7e80f-162">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="7e80f-163">En el nuevo **seguridad &amp; Compliance** , haga clic en el explorador **prevención de pérdidas de datos > directiva de**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-163">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="7e80f-164">En el panel **Prevención de pérdida de datos**, haga clic en **+ Crear una directiva**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-164">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="7e80f-165">En el **comenzar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-165">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="7e80f-166">En el panel **nombre de la directiva** , escriba el nombre de la directiva DLP nivel confidencial en **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-166">In the **Name your policy** pane, type the name for the sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="7e80f-167">En el panel **Elegir ubicaciones**, haga clic para que se le **permita elegir ubicaciones concretas** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-167">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="7e80f-168">En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-168">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7e80f-169">En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-169">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="7e80f-170">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-170">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="7e80f-171">En el panel **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-171">In the **Labels** pane, click **+ Add**, select the **Sensitive** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="7e80f-172">En el panel **Choose the types of content to protect** (Elegir los tipos de contenido que se va a proteger), haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-172">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="7e80f-173">En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-173">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="7e80f-174">En el panel **What do you want to do if we detect sensitive info?** (¿Qué quiere hacer si se detecta información confidencial?), haga clic en **Customize the tip and email** (Personalizar la sugerencia y el correo electrónico).</span><span class="sxs-lookup"><span data-stu-id="7e80f-174">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="7e80f-175">En el panel **Customize policy tips and email notifications** (Personalizar sugerencias de directiva y notificaciones de correo electrónico), haga clic en **Customize the policy tip text** (Personalizar el texto de la sugerencia de directiva).</span><span class="sxs-lookup"><span data-stu-id="7e80f-175">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="7e80f-176">En el cuadro de texto, escriba o pegue lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7e80f-176">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="7e80f-p104">Para compartir con un usuario de fuera de la organización, descargue el archivo y luego ábralo. Haga clic en Archivo, Proteger documento y Cifrar con contraseña y, luego, especifique una contraseña segura. Envíe la contraseña en un correo electrónico diferente u otro medio de comunicación.</span><span class="sxs-lookup"><span data-stu-id="7e80f-p104">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="7e80f-180">Como alternativa, escriba o pegue en su propia sugerencia de directiva que indica a los usuarios sobre cómo compartir un archivo fuera de la organización.</span><span class="sxs-lookup"><span data-stu-id="7e80f-180">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="7e80f-181">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-181">Click **OK**.</span></span>
    
17. <span data-ttu-id="7e80f-182">En la **¿Qué desea hacer si se detecta información sensible?** panel, desactive la casilla de verificación **Bloquear personas compartan y restringir el acceso al contenido compartido** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-182">In the **What do you want to do if we detect sensitive info?** pane, clear the **Block people from sharing, and restrict access to shared content** check box, and then click **Next**.</span></span>
    
18. <span data-ttu-id="7e80f-183">En el **¿desea activar las cosas de la política o prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-183">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="7e80f-184">En el panel **Revisar la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-184">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="7e80f-185">A continuación se muestra la configuración resultante para los sitios de grupo confidenciales de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e80f-185">Here is your resulting configuration for sensitive SharePoint Online team sites.</span></span>
  
![Directiva de DLP de un sitio de grupo de SharePoint Online aislado que utiliza la etiqueta Office 365 confidencial.](images/2ff4cc53-87a8-43e3-b637-3068d88409f3.png)
  
<span data-ttu-id="7e80f-187">Ahora siga estos pasos para configurar una directiva de DLP que impida a los usuarios compartir un documento en un sitio de grupo extremadamente confidencial de SharePoint Online de fuera de la organización.</span><span class="sxs-lookup"><span data-stu-id="7e80f-187">Next, use these steps to configure a DLP policy that blocks users when they share a document on a SharePoint Online highly confidential team site outside the organization.</span></span>
  
1. <span data-ttu-id="7e80f-188">En la ficha **Página de inicio de Microsoft Office** en el explorador, haga clic en el **seguridad &amp; Compliance** mosaico.</span><span class="sxs-lookup"><span data-stu-id="7e80f-188">From the **Microsoft Office Home** tab in your browser, click the **Security &amp; Compliance** tile.</span></span>
    
2. <span data-ttu-id="7e80f-189">En el nuevo **seguridad &amp; Compliance** , haga clic en el explorador **prevención de pérdidas de datos > directiva de**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-189">On the new **Security &amp; Compliance** tab in your browser, click **Data loss prevention > Policy**.</span></span>
    
3. <span data-ttu-id="7e80f-190">En el panel **Prevención de pérdida de datos**, haga clic en **+ Crear una directiva**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-190">In the **Data loss prevention** pane, click **+ Create a policy**.</span></span>
    
4. <span data-ttu-id="7e80f-191">En el **comenzar con una plantilla o crear una directiva personalizada** panel, haga clic en **personalizado**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-191">In the **Start with a template or create a custom policy** pane, click **Custom**, and then click **Next**.</span></span>
    
5. <span data-ttu-id="7e80f-192">En el panel **nombre de la directiva** , escriba el nombre de la directiva DLP nivel muy confidencial en **nombre**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-192">In the **Name your policy** pane, type the name for the highly sensitive level DLP policy in **Name**, and then click **Next**.</span></span>
    
6. <span data-ttu-id="7e80f-193">En el panel **Elegir ubicaciones**, haga clic para que se le **permita elegir ubicaciones concretas** y luego haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-193">In the **Choose locations** pane, click **Let me choose specific locations**, and then click **Next**.</span></span>
    
7. <span data-ttu-id="7e80f-194">En la lista de ubicaciones, deshabilitar las ubicaciones de **correo electrónico de Exchange** y **cuentas de OneDrive** y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-194">In the list of locations, disable the **Exchange email** and **OneDrive accounts** locations, and then click **Next**.</span></span>
    
8. <span data-ttu-id="7e80f-195">En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-195">In the **Customize the types of sensitive info you want to protect** pane, click **Edit**.</span></span>
    
9. <span data-ttu-id="7e80f-196">En el panel **Elija los tipos de contenido para proteger** , haga clic en **Agregar** en el cuadro de lista desplegable y, a continuación, haga clic en **etiquetas**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-196">In the **Choose the types of content to protect** pane, click **Add** in the drop-down box, and then click **Labels**.</span></span>
    
10. <span data-ttu-id="7e80f-197">En el panel **etiquetas** , haga clic en **+ Agregar**, seleccione la etiqueta **Altamente confidencial** , haga clic en **Agregar**y, a continuación, haga clic en **Listo**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-197">In the **Labels** pane, click **+ Add**, select the **Highly Confidential** label, click **Add**, and then click **Done**.</span></span>
    
11. <span data-ttu-id="7e80f-198">En el panel **Choose the types of content to protect** (Elegir los tipos de contenido que se va a proteger), haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-198">In the **Choose the types of content to protect** pane, click **Save**.</span></span>
    
12. <span data-ttu-id="7e80f-199">En el panel **Customize the types of sensitive info you want to protect** (Personalizar los tipos de información confidencial que quiere proteger), haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-199">In the **Customize the types of sensitive info you want to protect** pane, click **Next**.</span></span>
    
13. <span data-ttu-id="7e80f-200">En el panel **What do you want to do if we detect sensitive info?** (¿Qué quiere hacer si se detecta información confidencial?), haga clic en **Customize the tip and email** (Personalizar la sugerencia y el correo electrónico).</span><span class="sxs-lookup"><span data-stu-id="7e80f-200">In the **What do you want to do if we detect sensitive info?** pane, click **Customize the tip and email**.</span></span>
    
14. <span data-ttu-id="7e80f-201">En el panel **Customize policy tips and email notifications** (Personalizar sugerencias de directiva y notificaciones de correo electrónico), haga clic en **Customize the policy tip text** (Personalizar el texto de la sugerencia de directiva).</span><span class="sxs-lookup"><span data-stu-id="7e80f-201">In the **Customize policy tips and email notifications** pane, click **Customize the policy tip text**.</span></span>
    
15. <span data-ttu-id="7e80f-202">En el cuadro de texto, escriba o pegue lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7e80f-202">In the text box, type or paste in the following:</span></span>
    
  - <span data-ttu-id="7e80f-p105">Para compartir con un usuario de fuera de la organización, descargue el archivo y luego ábralo. Haga clic en Archivo, Proteger documento y Cifrar con contraseña y, luego, especifique una contraseña segura. Envíe la contraseña en un correo electrónico diferente u otro medio de comunicación.</span><span class="sxs-lookup"><span data-stu-id="7e80f-p105">To share with a user outside the organization, download the file and then open it. Click File, then Protect Document, and then Encrypt with Password, and then specify a strong password. Send the password in a separate email or other means of communication.</span></span>
    
    <span data-ttu-id="7e80f-206">Como alternativa, escriba o pegue en su propia sugerencia de directiva que indica a los usuarios sobre cómo compartir un archivo fuera de la organización.</span><span class="sxs-lookup"><span data-stu-id="7e80f-206">Alternately, type or paste in your own policy tip that instructs users on how to share a file outside your organization.</span></span>
    
16. <span data-ttu-id="7e80f-207">Haga clic en **Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-207">Click **OK**.</span></span>
    
17. <span data-ttu-id="7e80f-208">En la **¿Qué desea hacer si se detecta información sensible?** panel, seleccione **requerir una justificación comercial para reemplazar**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-208">In the **What do you want to do if we detect sensitive info?** pane, select **Require a business justification to override**, and then click **Next**.</span></span>
    
18. <span data-ttu-id="7e80f-209">En el **¿desea activar las cosas de la política o prueba primero?** panel, haga clic en **Sí, activarlo inmediatamente**y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-209">In the **Do you want to turn on the policy or test things out first?** pane, click **Yes, turn it on right away**, and then click **Next**.</span></span>
    
19. <span data-ttu-id="7e80f-210">En el panel **Revisar la configuración** , haga clic en **crear**y, a continuación, haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="7e80f-210">In the **Review your settings** pane, click **Create**, and then click **Close**.</span></span>
    
<span data-ttu-id="7e80f-211">A continuación se muestra la configuración resultante para sitios de grupo extremadamente confidenciales de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e80f-211">Here is your resulting configuration for high confidentiality SharePoint Online team sites.</span></span>
  
![Directiva de DLP de un sitio de grupo de SharePoint Online aislado que utiliza la etiqueta Office 365 muy confidencial.](images/f705d3d0-23c9-4333-8b70-ad3b91f835ea.png)
  
## <a name="next-step"></a><span data-ttu-id="7e80f-213">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="7e80f-213">Next step</span></span>

[<span data-ttu-id="7e80f-214">Protección de archivos de SharePoint Online con Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="7e80f-214">Protect SharePoint Online files with Azure Information Protection</span></span>](protect-sharepoint-online-files-with-azure-information-protection.md)
    
## <a name="see-also"></a><span data-ttu-id="7e80f-215">Consulte también</span><span class="sxs-lookup"><span data-stu-id="7e80f-215">See Also</span></span>

[<span data-ttu-id="7e80f-216">Protección de archivos y sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e80f-216">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="7e80f-217">Protección de sitios de SharePoint Online en un entorno de prueba y desarrollo</span><span class="sxs-lookup"><span data-stu-id="7e80f-217">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="7e80f-218">Instrucciones de seguridad de Microsoft para campañas políticas, organizaciones sin ánimo de lucro y otras organizaciones ágiles</span><span class="sxs-lookup"><span data-stu-id="7e80f-218">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="7e80f-219">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="7e80f-219">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)


