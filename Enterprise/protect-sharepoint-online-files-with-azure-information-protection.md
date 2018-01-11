---
title: "Proteger archivos de SharePoint Online con protección de la información de Azure"
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
- Strat_O365_Enterprise
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: "Resumen: Aplicar la protección de la información de Azure para proteger los archivos en un sitio de grupo SharePoint Online altamente confidencial."
ms.openlocfilehash: 03a10c5d856c4c5518f18b9d02ffe76f2c8d2e7a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="0d4f5-103">Proteger archivos de SharePoint Online con protección de la información de Azure</span><span class="sxs-lookup"><span data-stu-id="0d4f5-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="0d4f5-104">**Resumen:** Aplicar la protección de la información de Azure para proteger los archivos en un sitio de grupo SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="0d4f5-p101">Utilice los pasos de este artículo para configurar la protección de la información de Azure para proporcionar cifrado y los permisos de archivos en un sitio de grupo SharePoint Online altamente confidencial. La protección de cifrado y permisos viaja con un archivo, incluso cuando se descarga desde el sitio. Para obtener más información acerca de los sitios de equipo de SharePoint Online altamente confidenciales, vea [archivos y sitios de SharePoint Online seguro](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="0d4f5-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="0d4f5-p102">Cuando se aplica el cifrado de protección de la información de Azure a archivos almacenados en Office 365, el servicio no puede procesar el contenido de estos archivos. Co-autoría, eDiscovery, búsqueda, Delve y otras características de colaboración no funcionan. Políticas de datos Loss Prevention (DLP) sólo pueden trabajar con los metadatos (incluidos los rótulos de Office 365), pero no el contenido de estos archivos (como números de tarjeta de crédito dentro de los archivos).</span><span class="sxs-lookup"><span data-stu-id="0d4f5-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="0d4f5-111">En primer lugar, siga las instrucciones de [Activar Azure RMS con el centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) para la suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-111">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="0d4f5-112">A continuación, configure la protección de la información de Azure con una nueva directiva con ámbito y Sub-etiqueta de protección y los permisos de su sitio de grupo de SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="0d4f5-p103">Iniciar sesión en el portal de Office 365 con una cuenta que tiene la función de administrador de seguridad o de la empresa. Para obtener ayuda, visite [dónde puede iniciar sesión en Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span><span class="sxs-lookup"><span data-stu-id="0d4f5-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="0d4f5-115">En una ficha independiente del explorador, vaya al portal de Azure ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="0d4f5-115">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="0d4f5-116">Si es la primera vez se configura la protección de la información de Azure, consulte estas [instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="0d4f5-116">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="0d4f5-117">En el panel lista, haga clic en **más servicios**, escriba la **información**y, a continuación, haga clic en **Protección de la información de Azure**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-117">In the list pane, click **More services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="0d4f5-118">En la hoja de **protección de la información de Azure** , haga clic en **ámbito directivas > + Agregar una nueva directiva de**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-118">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="0d4f5-119">En **nombre de directiva** y una descripción, en **Descripción**, escriba un nombre para la nueva directiva.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="0d4f5-120">Haga clic en **Seleccionar qué usuarios o grupos Obtén esta directiva > usuario/grupos**, y, a continuación, seleccione el sitio acceso a miembros grupo para el sitio de grupo SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="0d4f5-121">Haga clic en **Seleccionar > Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="0d4f5-122">Para la etiqueta **Altamente confidencial** , haga clic en los puntos suspensivos (...) y, a continuación, haga clic en **Agregar una etiqueta Sub**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="0d4f5-123">Escriba un nombre para la Sub-etiqueta de **nombre** y una descripción de la etiqueta de **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="0d4f5-124">**Establecer permisos para documentos y correos electrónicos con esta etiqueta**, haga clic en **proteger**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="0d4f5-125">En la sección de **protección** , haga clic en **Azure (clave de nube)**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="0d4f5-126">En la hoja de **protección** , en **configuración de protección**, haga clic en **+ Agregar permisos**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="0d4f5-127">En la hoja de **permisos para agregar** , en **especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="0d4f5-128">En el panel de **DAA usuarios y grupos** , seleccione el grupo de acceso de miembros de sitio para el sitio de grupo SharePoint Online muy confidencial y, a continuación, haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="0d4f5-129">En **Elija el ajuste preestablecido los permisos**, desactive las casillas de verificación **Imprimir**, **Copiar y extraer contenido**y **hacia delante** .</span><span class="sxs-lookup"><span data-stu-id="0d4f5-129">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="0d4f5-130">Haga clic en **Aceptar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="0d4f5-131">En la hoja **secundario-etiqueta** , haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="0d4f5-132">Cierre el nuevo blade de ámbito de la política.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="0d4f5-133">En el módulo de **protección de la información de Azure - directivas de ámbito** , haga clic en **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-133">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
<span data-ttu-id="0d4f5-134">Ésta es su configuración resultante para el sitio de grupo SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-134">This is your resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![Etiqueta de protección de información de Azure de un sitio de grupo de SharePoint Online aislado.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="0d4f5-136">Ahora está listo para empezar a crear documentos y protegerlas con protección de la información de Azure y la nueva etiqueta.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="0d4f5-p104">Debe [instalar al cliente de protección de la información de Azure](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en el dispositivo o el equipo basado en Windows. Puede automatizar la instalación y secuencia de comandos o los usuarios pueden instalar al cliente manualmente. Consulte los siguientes recursos:</span><span class="sxs-lookup"><span data-stu-id="0d4f5-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="0d4f5-140">El lado del cliente de protección de la información de Azure</span><span class="sxs-lookup"><span data-stu-id="0d4f5-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="0d4f5-141">Instalación del cliente de protección de la información de Azure</span><span class="sxs-lookup"><span data-stu-id="0d4f5-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="0d4f5-142">Página de descarga para una instalación manual</span><span class="sxs-lookup"><span data-stu-id="0d4f5-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="0d4f5-p105">Una vez instalado, los usuarios ejecutaron y, a continuación, inicio de sesión a partir de una aplicación de Office (como Microsoft Word) con su cuenta de Office 365. Una nueva barra de **Protección de la información** permite a los usuarios seleccionar la nueva etiqueta. Asegúrese de que los usuarios saben el sitio de grupo SharePoint Online y que la etiqueta a utilizar, para proteger sus archivos altamente confidenciales.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="0d4f5-146">Si tiene varios sitios de equipo de SharePoint Online altamente confidenciales, debe crear varias directivas de protección de la información de Azure ámbito con subetiquetas con la configuración anterior, con los permisos para cada Sub-etiqueta establecer al grupo acceso de miembros del sitio de un sitio de grupo SharePoint Online específico.</span><span class="sxs-lookup"><span data-stu-id="0d4f5-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="0d4f5-147">Consulte también</span><span class="sxs-lookup"><span data-stu-id="0d4f5-147">See Also</span></span>

[<span data-ttu-id="0d4f5-148">Proteger los archivos y los sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="0d4f5-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="0d4f5-149">Sitios de SharePoint Online seguros en un entorno de pruebas y desarrollo</span><span class="sxs-lookup"><span data-stu-id="0d4f5-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="0d4f5-150">Guía de seguridad de Microsoft para campañas políticas, las ONG y otras organizaciones de Agile</span><span class="sxs-lookup"><span data-stu-id="0d4f5-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="0d4f5-151">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="0d4f5-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




