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
ms.openlocfilehash: 2c4776f5795a5a0b07be0f04b4872abadb4d31ca
ms.sourcegitcommit: b39b8ae3b4268d6475b54e2fdb62982b2c7d9943
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/12/2018
ms.locfileid: "20319291"
---
# <a name="protect-sharepoint-online-files-with-azure-information-protection"></a><span data-ttu-id="1c33c-103">Protección de archivos de SharePoint Online con Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="1c33c-103">Protect SharePoint Online files with Azure Information Protection</span></span>

 <span data-ttu-id="1c33c-104">**Resumen:** Aplique Azure Information Protection para proteger los archivos en un sitio de grupo de SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="1c33c-104">**Summary:** Apply Azure Information Protection to protect files in a highly confidential SharePoint Online team site.</span></span>
  
<span data-ttu-id="1c33c-p101">Siga los pasos de este artículo para configurar Azure Information Protection para proporcionar cifrado y permisos para archivos. Estos archivos pueden agregarse a una biblioteca de SharePoint configurada para protección altamente confidencial. O bien, puede abrir un archivo directamente desde el sitio y usar al cliente de Azure Information Protection para agregar el cifrado. La protección mediante cifrado y permisos viaja con un archivo, incluso cuando se descarga desde el sitio.</span><span class="sxs-lookup"><span data-stu-id="1c33c-p101">Use the steps in this article to configure Azure Information Protection to provide encryption and permissions for files. These files can be added to a SharePoint library configured for highly confidential protection. Or, you can open a file directly from the site and use the Azure Information Protection client to add encryption. The encryption and permissions protection travels with a file even when it is downloaded from the site.</span></span> 

<span data-ttu-id="1c33c-p102">Estos pasos son parte de una solución más grande para la configuración de protección confidencial para sitios de SharePoint y los archivos de estos sitios. Para obtener más información, consulte [Protección de archivos y sitios de SharePoint Online](secure-sharepoint-online-sites-and-files.md).</span><span class="sxs-lookup"><span data-stu-id="1c33c-p102">These steps are part of a larger solution for configuring highly confidential protection for SharePoint sites and the files within these sites. For more information, see [Secure SharePoint Online sites and files](secure-sharepoint-online-sites-and-files.md).</span></span> 

<span data-ttu-id="1c33c-111">Usar Azure Information Protection para los archivos de SharePoint Online no es recomendable para todos los clientes, pero es una opción para aquellos que necesitan este nivel de protección de un subconjunto de archivos.</span><span class="sxs-lookup"><span data-stu-id="1c33c-111">Using Azure Information Protection for files in SharePoint Online is not recommended for all customers, but is an option for customers who need this level of protection for a subset of files.</span></span>

<span data-ttu-id="1c33c-112">Algunas notas importantes sobre esta solución:</span><span class="sxs-lookup"><span data-stu-id="1c33c-112">Some important notes about this solution:</span></span>
- <span data-ttu-id="1c33c-p103">Cuando se aplica el cifrado de Azure Information Protection a los archivos almacenados en Office 365, el servicio no puede procesar el contenido de estos archivos. No funcionan algunas características de colaboración, como la coautoría, eDiscovery, la búsqueda y Delve. Las directivas de prevención de pérdida de datos (DLP) solo pueden trabajar con los metadatos (incluidas las etiquetas de Office 365), pero no con el contenido de estos archivos (por ejemplo, números de tarjeta de crédito incluidos en los archivos).</span><span class="sxs-lookup"><span data-stu-id="1c33c-p103">When Azure Information Protection encryption is applied to files stored in Office 365, the service cannot process the contents of these files. Co-authoring, eDiscovery, search, Delve, and other collaborative features do not work. Data Loss Prevention (DLP) policies can only work with the metadata (including Office 365 labels) but not the contents of these files (such as credit card numbers within files).</span></span>
- <span data-ttu-id="1c33c-p104">Esta solución requiere que un usuario seleccione la etiqueta que aplica la protección de Azure Information Protection. Si necesita cifrado automático y que SharePoint sea capaz de indexar y comprobar los archivos, puede usar Information Rights Management (IRM) en SharePoint Online. Al configurar una biblioteca de SharePoint para IRM, los archivos se cifrarán automáticamente cuando se descarguen para su edición. IRM de SharePoint incluye limitaciones que podrían influir en su decisión. Para obtener más información, consulte [Configurar Information Rights Management (IRM) en el Centro de administración de SharePoint](https://support.office.com/es-ES/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span><span class="sxs-lookup"><span data-stu-id="1c33c-p104">This solution requires a user to select a label that applies the protection from Azure Information Protection. If you require automatic encryption and the ability for SharePoint to index and inspect the files, consider using Information Rights Management (IRM) in SharePoint Online. When you configure a SharePoint library for IRM, files are automatically encrypted when they are downloaded for editing.  SharePoint IRM includes limitations that might influence your decision. For more information, see [Set up Information Rights Management (IRM) in SharePoint admin center](https://support.office.com/es-ES/article/Set-up-Information-Rights-Management-IRM-in-SharePoint-admin-center-239CE6EB-4E81-42DB-BF86-A01362FED65C).</span></span>

##<a name="admin-setup"></a><span data-ttu-id="1c33c-121">Configuración de administración</span><span class="sxs-lookup"><span data-stu-id="1c33c-121">Admin setup</span></span>
<span data-ttu-id="1c33c-122">Primero, siga las instrucciones que se indican en [Activar Azure RMS desde el Centro de administración de Office 365](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) para su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="1c33c-122">First, use the instructions in [Activate Azure RMS with the Office 365 admin center](https://docs.microsoft.com/information-protection/deploy-use/activate-office365) for your Office 365 subscription.</span></span>
  
<span data-ttu-id="1c33c-123">Después, siga estos pasos para configurar Azure Information Protection con una nueva directiva con ámbito y una subetiqueta para la protección y los permisos relacionados con el sitio de grupo de SharePoint Online altamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="1c33c-123">Next, configure Azure Information Protection with a new scoped policy and sub-label for protection and permissions of your highly confidential SharePoint Online team site.</span></span>
  
1. <span data-ttu-id="1c33c-p105">Inicie sesión en el portal de Office 365 con una cuenta que tenga el rol Administrador de seguridad o Administrador de la compañía. Para obtener ayuda, vea [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4) (Dónde iniciar sesión en Office 365).</span><span class="sxs-lookup"><span data-stu-id="1c33c-p105">Sign in to the Office 365 portal with an account that has the Security Administrator or Company Administrator role. For help, see [Where to sign in to Office 365](https://support.office.com/Article/Where-to-sign-in-to-Office-365-e9eb7d51-5430-4929-91ab-6157c5a050b4).</span></span>
    
2. <span data-ttu-id="1c33c-126">En una pestaña independiente del explorador, vaya a Azure Portal ([https://portal.azure.com](https://portal.azure.com)).</span><span class="sxs-lookup"><span data-stu-id="1c33c-126">In a separate tab of your browser, go to the Azure portal ([https://portal.azure.com](https://portal.azure.com)).</span></span>
    
3. <span data-ttu-id="1c33c-127">Si es la primera vez que configura Azure Information Protection, vea [estas instrucciones](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span><span class="sxs-lookup"><span data-stu-id="1c33c-127">If this is the first time you are configuring Azure Information Protection, see these [instructions](https://docs.microsoft.com/information-protection/deploy-use/configure-policy#to-access-the-azure-information-protection-blade-for-the-first-time).</span></span>
    
4. <span data-ttu-id="1c33c-128">En el panel de lista, haga clic en **Más servicios**, escriba **information** y haga clic en **Azure Information Protection**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-128">In the list pane, click **All services**, type **information**, and then click **Azure Information Protection**.</span></span>
    
5. <span data-ttu-id="1c33c-129">En la hoja **Azure Information Protection**, haga clic en **Directivas con ámbito > + Agregar una directiva**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-129">On the **Azure Information protection** blade, , click **Scoped policies > + Add a new policy**.</span></span>
    
6. <span data-ttu-id="1c33c-130">Escriba un nombre de la nueva directiva en **Nombre de la directiva** y una descripción en **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-130">Type a name for the new policy in **Policy name** and a description in **Description**.</span></span>
    
7. <span data-ttu-id="1c33c-131">Haga clic en **Seleccionar a qué usuarios o grupos se aplica esta directiva > Usuarios o grupos** y, luego, seleccione el grupo de acceso de los miembros del sitio para su sitio de grupo de SharePoint Online extremadamente confidencial.</span><span class="sxs-lookup"><span data-stu-id="1c33c-131">Click **Select which users or groups get this policy > User/Groups**, and then select the site members access group for your highly sensitive SharePoint Online team site.</span></span> 
    
8. <span data-ttu-id="1c33c-132">Haga clic en **Seleccionar > Aceptar**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-132">Click **Select > OK**.</span></span>
    
9. <span data-ttu-id="1c33c-133">Para la etiqueta **Extremadamente confidencial**, haga clic en el botón de puntos suspensivos (...) y, luego, en **Agregar una subetiqueta**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-133">For the **Highly Confidential** label, click the ellipses (…), and then click **Add a sub-label**.</span></span>
    
10. <span data-ttu-id="1c33c-134">Escriba un nombre para la subetiqueta en **Nombre** y una descripción en **Descripción**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-134">Type a name for the sub-label in **Name** and a description of the label in **Description**.</span></span>
    
11. <span data-ttu-id="1c33c-135">En **Establecer permisos para documentos y correos electrónicos que contengan esta etiqueta**, haga clic en **Proteger**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-135">In **Set permissions for documents and emails containing this label**, click **Protect**.</span></span>
    
12. <span data-ttu-id="1c33c-136">En la sección **Protección**, haga clic en **Azure (clave de nube)**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-136">In the **Protection** section, click **Azure (cloud key)**.</span></span>
    
13. <span data-ttu-id="1c33c-137">En la hoja **Protección**, en **Configuración de protección**, haga clic en **+ Agregar permisos**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-137">On the **Protection** blade, under **Protection settings**, click **+ Add permissions**.</span></span>
    
14. <span data-ttu-id="1c33c-138">En la hoja **Agregar permisos**, en **Especificar usuarios y grupos**, haga clic en **+ Examinar directorio**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-138">On the **Add permissions** blade, under **Specify users and groups**, click **+ Browse directory**.</span></span>
    
15. <span data-ttu-id="1c33c-139">En el panel **Usuarios y grupos de AAD**, seleccione el grupo de acceso de miembros del sitio para el sitio de grupo de SharePoint Online extremadamente confidencial y haga clic en **Seleccionar**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-139">On the **AAD Users and Groups** pane, select the site members access group for your highly sensitive SharePoint Online team site, and then click **Select**.</span></span>
    
16. <span data-ttu-id="1c33c-140">En **Elegir permisos entre los preestablecidos**, desactive las casillas **Imprimir**, **Copiar y extraer contenido** y **Reenviar**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-140">Under **Choose permissions from the preset**, clear the **Print**, **Copy and extract content**, and **Forward** check boxes.</span></span>
    
17. <span data-ttu-id="1c33c-141">Haga clic en **Aceptar** dos veces.</span><span class="sxs-lookup"><span data-stu-id="1c33c-141">Click **OK** twice.</span></span>
    
18. <span data-ttu-id="1c33c-142">En la hoja **Subetiqueta**, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-142">On the **Sub-label** blade, click **Save**.</span></span>
    
19. <span data-ttu-id="1c33c-143">Cierre la nueva hoja de directiva con ámbito.</span><span class="sxs-lookup"><span data-stu-id="1c33c-143">Close the new scoped policy blade.</span></span>
    
20. <span data-ttu-id="1c33c-144">En la hoja **Azure Information Protection: Directivas con ámbito**, haga clic en **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1c33c-144">On the **Azure Information protection - Scoped policies** blade, click **Publish**.</span></span>
    
 
##<a name="client-setup"></a><span data-ttu-id="1c33c-145">Instalación del cliente</span><span class="sxs-lookup"><span data-stu-id="1c33c-145">Client setup</span></span>
<span data-ttu-id="1c33c-146">Ya está listo para empezar a crear documentos y protegerlos con Azure Information Protection y su nueva etiqueta.</span><span class="sxs-lookup"><span data-stu-id="1c33c-146">You are now ready to begin creating documents and protecting them with Azure Information Protection and your new label.</span></span>
  
<span data-ttu-id="1c33c-p106">Necesita [instalar el cliente de Azure Information Protection](https://docs.microsoft.com/information-protection/rms-client/install-client-app) en el dispositivo o equipo basado en Windows. Puede generar scripts y automatizar la instalación, o bien los usuarios pueden instalar el cliente de forma manual. Vea los recursos siguientes:</span><span class="sxs-lookup"><span data-stu-id="1c33c-p106">You must [install the Azure Information Protection client](https://docs.microsoft.com/information-protection/rms-client/install-client-app) on your device or Windows-based computer. You can script and automate the installation, or users can install the client manually. See the following resources:</span></span>
  
- [<span data-ttu-id="1c33c-150">El lado cliente de Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="1c33c-150">The client side of Azure Information Protection</span></span>](https://docs.microsoft.com/information-protection/rms-client/use-client)
    
- [<span data-ttu-id="1c33c-151">Instalación del cliente de Azure Information Protection</span><span class="sxs-lookup"><span data-stu-id="1c33c-151">Installing the Azure Information Protection client</span></span>](https://docs.microsoft.com/information-protection/rms-client/client-admin-guide)
    
- [<span data-ttu-id="1c33c-152">Página de descarga para la instalación manual</span><span class="sxs-lookup"><span data-stu-id="1c33c-152">Download page for manual installation</span></span>](https://www.microsoft.com/download/details.aspx?id=53018)
    
<span data-ttu-id="1c33c-p107">Cuando se complete la instalación, los usuarios ejecutarán y, después, iniciarán sesión desde una aplicación de Office (como Microsoft Word) con su cuenta de Office 365. Una nueva barra de **Information Protection** permite a los usuarios seleccionar la nueva etiqueta. Asegúrese de que los usuarios conozcan el sitio de grupo de SharePoint Online y la etiqueta que necesitan usar para proteger sus archivos altamente confidenciales.</span><span class="sxs-lookup"><span data-stu-id="1c33c-p107">Once installed, your users run and then sign-in from an Office application (such as Microsoft Word) with their Office 365 account. A new **Information Protection** bar allows users to select the new label. Make sure that your users know the SharePoint Online team site and which label to use, to protect their highly confidential files.</span></span>
  
> [!NOTE]
> <span data-ttu-id="1c33c-156">Si tiene varios sitios de grupo de SharePoint Online extremadamente confidenciales, deberá crear varias directivas con ámbito de Azure Information Protection que contengan subetiquetas con la configuración anterior, con los permisos de cada subetiqueta establecidos en el grupo de acceso de miembros de sitio de un equipo de grupo concreto de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1c33c-156">If you have multiple highly sensitive SharePoint Online team sites, you should create multiple Azure Information Protection scoped policies with sub-labels with the above settings, with the permissions for each sub-label set to the site members access group of a specific SharePoint Online team site.</span></span> 
  
##<a name="adding-permissions-for-external-users"></a><span data-ttu-id="1c33c-157">Agregar permisos para usuarios externos</span><span class="sxs-lookup"><span data-stu-id="1c33c-157">Adding permissions for external users</span></span>
<span data-ttu-id="1c33c-p108">Hay dos maneras de conceder a los usuarios externos el acceso a archivos protegidos con Azure Information Protection. En ambos casos, los usuarios externos necesitan tener una cuenta de Azure AD. Si los usuarios externos no son miembros de una organización que usa Azure AD, pueden obtener una cuenta de Azure AD como usuario individual a través de esta página de suscripción: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span><span class="sxs-lookup"><span data-stu-id="1c33c-p108">There are two ways you can grant external users access to files protected with Azure Information Protection. In both these cases, external users must have an Azure AD account. If external users aren't members of an organization that uses Azure AD, they can obtain an Azure AD account as an individual by using this sign-up page: [https://aka.ms/aip-signup](https://aka.ms/aip-signup).</span></span>

 - <span data-ttu-id="1c33c-p109">Agregar usuarios externos a un grupo de Azure AD que se usa para configurar la protección para una etiqueta. Primero, tendrá que agregar la cuenta como usuario B2B en el directorio. Puede tardar un par de horas con [Caché de pertenencia al grupo por Azure Rights Management](https://docs.microsoft.com/es-ES/azure/information-protection/plan-design/prepare#group-membership-caching-by-azure-information-protection).</span><span class="sxs-lookup"><span data-stu-id="1c33c-p109">Add external users to an Azure AD group that is used to configure protection for a label. You’ll need to first add the account as a B2B user in your directory. It can take a couple of hours for group membership caching by Azure Rights Management. With this method, permissions are granted to all existing files protected with the label (even files protected before a user is added to the Azure AD group).</span></span>  
 - <span data-ttu-id="1c33c-p110">Agregar usuarios externos directamente a la protección de etiqueta. Puede agregar todos los usuarios de una organización (por ejemplo, Fabrikam.com), un usuario o un grupo de Azure AD (como un grupo de finanzas dentro de una organización). Puede agregar, por ejemplo, un grupo de reguladores externo para la protección de una etiqueta.</span><span class="sxs-lookup"><span data-stu-id="1c33c-p110">Add external users directly to the label protection. You can add all users from an organization (e.g. Fabrikam.com), an Azure AD group (such as a finance group within an organization), or an individual user. For example, you can add an external team of regulators to the protection for a label. With this method, permissions are granted only to files protected with the label after the external entity is added to the protection.</span></span>

## <a name="see-also"></a><span data-ttu-id="1c33c-167">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1c33c-167">See Also</span></span>

[<span data-ttu-id="1c33c-168">Protección de archivos y sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1c33c-168">Secure SharePoint Online sites and files</span></span>](secure-sharepoint-online-sites-and-files.md)
  
[<span data-ttu-id="1c33c-169">Proteger sitios de SharePoint Online en un entorno de desarrollo y pruebas</span><span class="sxs-lookup"><span data-stu-id="1c33c-169">Secure SharePoint Online sites in a dev/test environment</span></span>](secure-sharepoint-online-sites-in-a-dev-test-environment.md)
  
[<span data-ttu-id="1c33c-170">Guía de seguridad de Microsoft para campañas políticas, ONG y otras organizaciones ágiles</span><span class="sxs-lookup"><span data-stu-id="1c33c-170">Microsoft Security Guidance for Political Campaigns, Nonprofits, and Other Agile Organizations</span></span>](microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o.md)
  
[<span data-ttu-id="1c33c-171">Adopción de la nube y soluciones híbridas</span><span class="sxs-lookup"><span data-stu-id="1c33c-171">Cloud adoption and hybrid solutions</span></span>](cloud-adoption-and-hybrid-solutions.md)




