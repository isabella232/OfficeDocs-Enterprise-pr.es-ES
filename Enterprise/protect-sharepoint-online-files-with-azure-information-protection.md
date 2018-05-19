---
title: Protección de archivos de SharePoint Online con Azure Information Protection
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 5b9c8e41-25d2-436d-89bb-9aecb9ec2b80
description: 'Resumen: aplique Azure Information Protection para proteger los archivos en un sitio de grupo de SharePoint Online altamente confidencial.'
ms.openlocfilehash: a5df4d7289ec31686ad74f78a4797e1aa3eaa447
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="19998-103">Protección de archivos de SharePoint Online con Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="19998-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="19998-104">**Resumen:** aplique Azure Information Protection para proteger los archivos en un sitio de grupo de SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="19998-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="19998-p101">Siga los pasos que se indican en este artículo para configurar Azure Information Protection para ofrecer cifrado y permisos para archivos en un sitio de grupo de SharePoint Online altamente confidencial. La protección del cifrado y los permisos viaja con los archivos, incluso cuando se descarguen del sitio. Para obtener más información sobre los sitios de grupo de SharePoint Online altamente confidenciales, vea [Proteger archivos y sitios de SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="19998-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files in a highly confidential SharePoint Online team site. The encryption and permissions protection travels with a file even when it is downloaded from the site. For more information about highly confidential SharePoint Online team sites, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span>
  
> [!NOTE]
> <span data-ttu-id="19998-p102">Cuando se aplica el cifrado de Azure Information Protection a los archivos almacenados en Office 365, el servicio no puede procesar el contenido de estos archivos. No funcionan algunas características de colaboración, como la coautoría, eDiscovery, la búsqueda y Delve. Las directivas de prevención de pérdida de datos (DLP) solo pueden trabajar con los metadatos (incluidas las etiquetas de Office 365), pero no con el contenido de estos archivos (por ejemplo, números de tarjeta de crédito incluidos en los archivos).</span><span class="sxs-lookup"><span data-stu-id="19998-p102">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span> 
  
<span data-ttu-id="19998-111">Primero, siga las instrucciones que se indican en [Activar Azure RMS desde el Centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) para su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="19998-111">First, follow the instructions in [Activate Azure RMS with the Office 365 admin center for your Office 365 subscription](https://docs.microsoft.com/information-protection/deploy-use/activate-office365).</span></span>
  
<span data-ttu-id="19998-112">Después, siga estos pasos para configurar Azure Information Protection con una nueva directiva con ámbito y una subetiqueta para la protección y los permisos relacionados con el sitio de grupo de SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="19998-112">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions for your highly confidential SharePoint Online team site by following these steps:</span></span>
  
1. <span data-ttu-id="19998-p103">Inicie sesión en el portal de Office 365 con una cuenta que tenga el rol Administrador de seguridad o Administrador de la compañía. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).</span><span class="sxs-lookup"><span data-stu-id="19998-p103">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="19998-115">En una pestaña independiente del explorador, vaya a Azure Portal ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="19998-115">In a separate tab of your browser, go to the Azure portal (https://portal.azure.com).</span></span>
    
3. <span data-ttu-id="19998-116">Si es la primera vez que configura Azure Information Protection, vea [estas instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="19998-116">If this is the first time you are configuring Azure Information Protection, see [these instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="19998-117">En el panel de lista, haga clic en **Más servicios**, escriba **information** y haga clic en **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="19998-117">In the list pane, click **More services**, type **information**, and click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="19998-118">En la hoja **Azure Information Protection**, haga clic en **Directivas con ámbito > + Agregar una directiva**.</span><span class="sxs-lookup"><span data-stu-id="19998-118">On the **Azure Information protection** blade, click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="19998-119">Escriba un nombre de la nueva directiva en **Nombre de la directiva** y una descripción en **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="19998-119">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="19998-120">Haga clic en **Seleccionar a qué usuarios o grupos se aplica esta directiva > Usuarios o grupos** y, luego, seleccione el grupo de acceso de los miembros del sitio para su sitio de grupo de SharePoint Online extremadamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="19998-120">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="19998-121">Haga clic en **Seleccionar > Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="19998-121">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="19998-122">Para la etiqueta **Extremadamente confidencial**, haga clic en el botón de puntos suspensivos (...) y, luego, en **Agregar una subetiqueta**.</span><span class="sxs-lookup"><span data-stu-id="19998-122">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="19998-123">Escriba un nombre para la subetiqueta en **Nombre** y una descripción en **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="19998-123">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="19998-124">En **Establecer permisos para documentos y correos electrónicos que contengan esta etiqueta**, haga clic en **Proteger**.</span><span class="sxs-lookup"><span data-stu-id="19998-124">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="19998-125">En la sección **Protección**, haga clic en **Azure (clave de nube)**.</span><span class="sxs-lookup"><span data-stu-id="19998-125">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="19998-126">En la hoja **Protección**, en **Configuración de protección**, haga clic en **+ Agregar permisos**.</span><span class="sxs-lookup"><span data-stu-id="19998-126">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="19998-127">En la hoja **Agregar permisos**, en **Especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.</span><span class="sxs-lookup"><span data-stu-id="19998-127">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="19998-128">En el panel **Usuarios y grupos de AAD**, seleccione el grupo de acceso de miembros del sitio para el sitio de grupo de SharePoint Online extremadamente confidencial y haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="19998-128">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and click **Select**.</span></span>
    
16. <span data-ttu-id="19998-129">En **Elegir permisos entre los preestablecidos**, desactive las casillas **Imprimir**, **Copiar y extraer contenido** y **Reenviar**.</span><span class="sxs-lookup"><span data-stu-id="19998-129">Under Choose permissions from the preset, clear the Print, Copy and extract content, and Forward check boxes.</span></span>
    
17. <span data-ttu-id="19998-130">Haga clic en **Aceptar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="19998-130">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="19998-131">En la hoja **Subetiqueta**, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="19998-131">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="19998-132">Cierre la nueva hoja de directiva con ámbito.</span><span class="sxs-lookup"><span data-stu-id="19998-132">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="19998-133">En la hoja **Azure Information Protection: Directivas con ámbito**, haga clic en **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="19998-133">On the **Azure Information Protection – Scoped policies** blade, click **Publish**, and then click Yes.</span></span>
    
<span data-ttu-id="19998-134">Esta es la configuración resultante del sitio de grupo de SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="19998-134">This is the resulting configuration for your highly confidential SharePoint Online team site.</span></span>
  
![Etiqueta de Azure Information Protection de un sitio de grupo de SharePoint Online aislado.](images/8cc92aa4-e7bc-4c2f-a4a4-3b034b21aebf.png)
  
<span data-ttu-id="19998-136">Ya está listo para empezar a crear documentos y protegerlos con Azure Information Protection y su nueva etiqueta.</span><span class="sxs-lookup"><span data-stu-id="19998-136">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="19998-p104">Necesita [instalar el cliente de Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en el dispositivo o equipo basado en Windows. Puede generar scripts y automatizar la instalación, o bien los usuarios pueden instalar el cliente de forma manual. Vea los recursos siguientes:</span><span class="sxs-lookup"><span data-stu-id="19998-p104">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually.</span></span>
  
- [<span data-ttu-id="19998-140">El lado cliente de Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="19998-140">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="19998-141">Instalación del cliente de Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="19998-141">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="19998-142">Página de descarga para la instalación manual</span><span class="sxs-lookup"><span data-stu-id="19998-142">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="19998-p105">Cuando se complete la instalación, los usuarios ejecutarán y, después, iniciarán sesión desde una aplicación de Office (como Microsoft Word) con su cuenta de Office 365. Una nueva barra de **Information Protection** permite a los usuarios seleccionar la nueva etiqueta. Asegúrese de que los usuarios conozcan el sitio de grupo de SharePoint Online y la etiqueta que necesitan usar para proteger sus archivos altamente confidenciales.</span><span class="sxs-lookup"><span data-stu-id="19998-p105">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="19998-146">Si tiene varios sitios de grupo de SharePoint Online extremadamente confidenciales, deberá crear varias directivas con ámbito de Azure Information Protection que contengan subetiquetas con la configuración anterior, con los permisos de cada subetiqueta establecidos en el grupo de acceso de miembros de sitio de un equipo de grupo concreto de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="19998-146">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="19998-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="19998-147">See Also</span></span>

[<span data-ttu-id="19998-148">Protección de archivos y sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="19998-148">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="19998-149">Proteger sitios de SharePoint Online en un entorno de desarrollo y pruebas</span><span class="sxs-lookup"><span data-stu-id="19998-149">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="19998-150">Guía de seguridad de Microsoft para campañas políticas, ONG y otras organizaciones ágiles</span><span class="sxs-lookup"><span data-stu-id="19998-150">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="19998-151">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="19998-151">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




