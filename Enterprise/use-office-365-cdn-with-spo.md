---
title: Usar la red de entrega de contenido de Office 365 con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Se describe el uso integradas Content Delivery Network de Office 365 (CDN) para acelerar la entrega de los activos de SharePoint Online para todos los usuarios independientemente de dónde se encuentren o cómo tener acceso a su contenido.
ms.openlocfilehash: 958f01419a74e4b8cd007b2627585884496bdfdf
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542732"
---
# <a name="use-the-office-365-content-delivery-network-with-sharepoint-online"></a><span data-ttu-id="7122d-103">Usar la red de entrega de contenido de Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7122d-103">Use the Office 365 content delivery network with SharePoint Online</span></span>

<span data-ttu-id="7122d-p101">Puede hospedar estáticos activos en la red de entrega de contenido (CDN) de Office 365 para proporcionar un mejor rendimiento para las páginas de SharePoint Online. Activos estáticos son archivos que no cambian muy a menudo, como imágenes, vídeo y audio, hojas de estilos, fuentes y archivos de JavaScript. La CDN funciona como un proxy de almacenamiento en memoria caché distribuido geográficamente, al almacenar en caché estáticos activos más cerca de los exploradores que lo soliciten.</span><span class="sxs-lookup"><span data-stu-id="7122d-p101">You can host static assets in the Office 365 content delivery network (CDN) to provide better performance for your SharePoint Online pages. Static assets are files that don't change very often, like images, video and audio, style sheets, fonts, and JavaScript files. The CDN works as a geographically distributed caching proxy, by caching static assets closer to the browsers requesting them.</span></span> 
  
<span data-ttu-id="7122d-p102">Si ya está familiarizado con el modo en que las CDN funcionen, sólo necesita para llevar a cabo algunos pasos para configurarla. En este tema se describe cómo. Siga leyendo para obtener información acerca de la CDN de Office 365 y cómo empezar a usar los activos de estáticos de hospedaje.</span><span class="sxs-lookup"><span data-stu-id="7122d-p102">If you are already familiar with the way that CDNs work, you only need to complete a few steps to set it up. This topic describes how. Read on for information about the Office 365 CDN and how to get started hosting your static assets.</span></span>
  
 <span data-ttu-id="7122d-110">**Realizar una copia de Head a la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).**</span><span class="sxs-lookup"><span data-stu-id="7122d-110">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>
  
## <a name="office-365-cdn-basics"></a><span data-ttu-id="7122d-111">Conceptos básicos de CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-111">Office 365 CDN basics</span></span>

<span data-ttu-id="7122d-p103">La CDN de Office 365 se incluye como parte de su suscripción de SharePoint Online. No es necesario que pagar por él. Office 365 proporciona acceso público y soporte técnico para ambos privado y permite a los activos estática de host en varias ubicaciones u orígenes. La CDN de Office 365 no es la misma que la CDN de Azure. Si necesita obtener más información acerca de por qué usar una CDN o acerca de los conceptos generales de CDN, vea [redes de entrega de contenido](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="7122d-p103">The Office 365 CDN is included as part of your SharePoint Online subscription. You don't have to pay extra for it. Office 365 provides support for both private and public access and allows you to host static assets in multiple locations, or origins. The Office 365 CDN is not the same as the Azure CDN. If you need more information about why to use a CDN or about general CDN concepts, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="how-the-cdn-grants-access-to-end-users"></a><span data-ttu-id="7122d-117">Cómo la CDN concede acceso a los usuarios finales</span><span class="sxs-lookup"><span data-stu-id="7122d-117">How the CDN grants access to end users</span></span>

<span data-ttu-id="7122d-p104">Acceso privado a activos estáticos en la CDN de Office 365 se concede por tokens generados por SharePoint Online. Los usuarios que ya tienen permiso para obtener acceso a la carpeta o biblioteca designado por el origen se les otorgará automáticamente los tokens. SharePoint Online admite los permisos de nivel de elemento para la CDN.</span><span class="sxs-lookup"><span data-stu-id="7122d-p104">Private access to static assets in the Office 365 CDN is granted by tokens generated by SharePoint Online. Users who already have permission to access to the folder or library designated by the origin will automatically be granted tokens. SharePoint Online does not support item-level permissions for the CDN.</span></span>
  
<span data-ttu-id="7122d-121">Por ejemplo, para un archivo que se encuentra en `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, dado lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="7122d-121">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, given the following:</span></span>
  
- <span data-ttu-id="7122d-122">El usuario 1 tiene acceso a Carpeta1 y a image1.jpg</span><span class="sxs-lookup"><span data-stu-id="7122d-122">User 1 has access to folder1 and to image1.jpg</span></span>
    
- <span data-ttu-id="7122d-123">El usuario 2 no tiene acceso a carpeta1</span><span class="sxs-lookup"><span data-stu-id="7122d-123">User 2 does not have access to folder1</span></span>
    
- <span data-ttu-id="7122d-124">3 de usuario no tiene acceso a carpeta1 pero se concede permiso explícito para tener acceso a image1.jpg a través de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7122d-124">User 3 does not have access to folder1 but is granted explicit permission to access image1.jpg through SharePoint Online</span></span>
    
- <span data-ttu-id="7122d-125">Usuario 4 tiene acceso a carpeta1, pero tiene denegado explícitamente el acceso a image1.jpg</span><span class="sxs-lookup"><span data-stu-id="7122d-125">User 4 has access to folder1 but has been explicitly denied access to image1.jpg</span></span>
    
<span data-ttu-id="7122d-126">A continuación, las siguientes condiciones es verdadera:</span><span class="sxs-lookup"><span data-stu-id="7122d-126">Then the following are true:</span></span>
  
- <span data-ttu-id="7122d-127">El usuario 1 y 4 de usuario podrán tener acceso a image1.jpg a través de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7122d-127">User 1 and User 4 will be able to access image1.jpg through the CDN.</span></span>
    
- <span data-ttu-id="7122d-128">El usuario 2 y 3 de usuario no podrá tener acceso a image1.jpg a través de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7122d-128">User 2 and User 3 will not be able to access image1.jpg through the CDN.</span></span>
    
    <span data-ttu-id="7122d-129">Sin embargo, 3 de usuario puede tener acceso a la image1.jpg activos directamente a través de SharePoint Online mientras 4 de usuario no se puede obtener acceso a los activos a través de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7122d-129">However, User 3 can still access the asset image1.jpg directly through SharePoint Online while User 4 cannot access the asset through SharePoint Online.</span></span>
    
## <a name="overview-of-working-with-the-office-365-cdn"></a><span data-ttu-id="7122d-130">Información general de trabajar con la CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-130">Overview of working with the Office 365 CDN</span></span>

<span data-ttu-id="7122d-131">Para configurar la CDN de Office 365, siga estos pasos básicos:</span><span class="sxs-lookup"><span data-stu-id="7122d-131">To set up the Office 365 CDN, you follow these basic steps:</span></span>
  
- <span data-ttu-id="7122d-132">Planeación de la implementación de CDN:</span><span class="sxs-lookup"><span data-stu-id="7122d-132">Plan for CDN deployment:</span></span>
    
  - <span data-ttu-id="7122d-p105">Determinar qué activos estáticos que desea hospedar en la CDN de Office 365. Para obtener información detallada acerca de cómo realizar estas opciones, consulte [las redes de entrega de contenido](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="7122d-p105">Determine which static assets you want to host on the Office 365 CDN. For detailed information about how to make these choices, refer to [Content delivery networks](content-delivery-networks.md).</span></span>
    
  - <span data-ttu-id="7122d-p106">[Determine dónde desea almacenar los activos](use-office-365-cdn-with-spo.md#CDNStoreAssets). Esta ubicación es una carpeta o biblioteca de SharePoint y se llama a un origen.</span><span class="sxs-lookup"><span data-stu-id="7122d-p106">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets). This location is a folder or SharePoint library and is called an origin.</span></span>
    
  - <span data-ttu-id="7122d-p107">Determinar si los activos deben hacerse públicos o mantener como privados. Hacerlo cuando se [Elija si cada origen debe ser público o privado](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). Si lo desea, puede tener varios orígenes en la que algunas son públicas, y algunas son privados.</span><span class="sxs-lookup"><span data-stu-id="7122d-p107">Determine whether the assets should be made public or kept private. You do this when you [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate). If you want, you can have multiple origins in which some are public, and some are private.</span></span>
    
- <span data-ttu-id="7122d-p108">[Establecer de seguridad y configurar la CDN de Office 365 mediante el Shell de administración de SharePoint Online](use-office-365-cdn-with-spo.md#CDNSetupinPShell). Cuando haya terminado este paso, debe:</span><span class="sxs-lookup"><span data-stu-id="7122d-p108">[Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#CDNSetupinPShell). When you complete this step, you will have:</span></span>
    
  - <span data-ttu-id="7122d-142">Habilita la CDN para su organización.</span><span class="sxs-lookup"><span data-stu-id="7122d-142">Enabled the CDN for your organization.</span></span>
    
  - <span data-ttu-id="7122d-p109">Se agregó las orígenes. Identificar cada origen como público o privado.</span><span class="sxs-lookup"><span data-stu-id="7122d-p109">Added your origins. You identify each origin as public or private.</span></span>
    
<span data-ttu-id="7122d-145">Una vez haya terminado con el programa de instalación, [Administrar la CDN de Office 365](use-office-365-cdn-with-spo.md#CDNManage) a través del tiempo por:</span><span class="sxs-lookup"><span data-stu-id="7122d-145">Once you're done with setup, [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span> 
  
- <span data-ttu-id="7122d-146">Agregar, actualizar y eliminación de activos</span><span class="sxs-lookup"><span data-stu-id="7122d-146">Adding, updating, and removing assets</span></span>
    
- <span data-ttu-id="7122d-147">Agregar y quitar orígenes</span><span class="sxs-lookup"><span data-stu-id="7122d-147">Adding and removing origins</span></span>
    
- <span data-ttu-id="7122d-148">Configuración de directivas de CDN</span><span class="sxs-lookup"><span data-stu-id="7122d-148">Configuring CDN policies</span></span>
    
- <span data-ttu-id="7122d-149">Si es necesario, deshabilitar la CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-149">If necessary, disabling the Office 365 CDN</span></span>
    
## <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="7122d-150">Determine dónde desea almacenar los activos de</span><span class="sxs-lookup"><span data-stu-id="7122d-150">Determine where you want to store your assets</span></span>

<span data-ttu-id="7122d-p110">La CDN de captura los activos desde una ubicación que se denomina un origen. Para Office 365, un origen es una biblioteca de SharePoint o la carpeta que sea accesible para una dirección URL. Tener gran flexibilidad al especificar orígenes para su organización. Por ejemplo, puede especificar varios orígenes, o bien, un único origen donde desea colocar todos los activos de CDN. Puede elegir tener orígenes públicos o privados para su organización. La mayoría de las organizaciones se optan por implementar una combinación de ambas.</span><span class="sxs-lookup"><span data-stu-id="7122d-p110">The CDN fetches your assets from a location called an origin. For Office 365, an origin is a SharePoint library or folder that is accessible by a URL. You have great flexibility when you specify origins for your organization. For example, you can specify multiple origins, or, a single origin where you want to put all your CDN assets. You can choose to have both public or private origins for your organization. Most organizations will choose to implement a combination of the two.</span></span>
  
<span data-ttu-id="7122d-p111">Si define cientos de orígenes, probablemente tendrá un impacto negativo en el tiempo que se tarda en procesar las solicitudes. Se recomienda que si tiene más de aproximadamente 100 orígenes es posible que desee reconsiderar la arquitectura.</span><span class="sxs-lookup"><span data-stu-id="7122d-p111">If you define hundreds of origins, it will likely have a negative impact on the time it takes to process requests. We recommend that if you have more than about 100 origins you might want to rethink your architecture.</span></span>
  
## <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="7122d-159">Elija si cada origen debe ser público o privado</span><span class="sxs-lookup"><span data-stu-id="7122d-159">Choose whether each origin should be public or private</span></span>

<span data-ttu-id="7122d-p112">Al identificar un origen, se especifica si se debe establecer público o privado. Independientemente de la opción que elija, Microsoft hace todo el trabajo pesado por usted lo que respecta a la administración de la CDN de sí mismo. Además, puede cambiar de opinión más adelante, después de configurar la CDN e identificado los orígenes.</span><span class="sxs-lookup"><span data-stu-id="7122d-p112">When you identify an origin, you specify whether it should be made public or private. Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself. Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>
  
<span data-ttu-id="7122d-163">Opciones públicas y privadas proporcionan mejoras de rendimiento, pero cada uno tiene ventajas y atributos únicos.</span><span class="sxs-lookup"><span data-stu-id="7122d-163">Both public and private options provide performance improvements, but each has unique attributes and advantages.</span></span>
  
 <span data-ttu-id="7122d-164">**Los atributos y las ventajas de los activos en un origen público de hospedaje**</span><span class="sxs-lookup"><span data-stu-id="7122d-164">**Attributes and advantages of hosting assets in a public origin**</span></span>
  
- <span data-ttu-id="7122d-165">Forma anónima son accesibles para todos los activos expuestos en un origen público.</span><span class="sxs-lookup"><span data-stu-id="7122d-165">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="7122d-166">Si se identifica un origen público en su CDN, nunca debe colocar los recursos que se consideran confidenciales de su organización en un origen público o biblioteca de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7122d-166">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in a public origin or SharePoint Online library.</span></span> 
  
- <span data-ttu-id="7122d-167">Si quita un activo de un origen público, puede continuar el activo esté disponible para un máximo de 30 días desde la memoria caché; Sin embargo, se invalidará vínculos a los activos en la CDN dentro de 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7122d-167">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="7122d-p113">Al hospedar hojas de estilos (archivos CSS) en un origen pública, puede usar rutas de acceso relativas y URI dentro del código. Esto significa que puede hacer referencia a la ubicación de las imágenes de fondo y otros objetos con relación a la ubicación de los activos que se está llamando a.</span><span class="sxs-lookup"><span data-stu-id="7122d-p113">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code. This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
    
- <span data-ttu-id="7122d-p114">Mientras que puede codificar dirección URL de un origen pública, si lo hace por lo que no se recomienda. El motivo es que si el acceso a la red CDN deja de estar disponible, la dirección URL no se puede resolver automáticamente a la organización en SharePoint Online y que podría provocar la ruptura de vínculos y otros errores.</span><span class="sxs-lookup"><span data-stu-id="7122d-p114">While you can hard code a public origin's URL, doing so is not recommended. The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
    
- <span data-ttu-id="7122d-p115">Los tipos de archivo predeterminados que se incluyen para orígenes públicas son .css, .eot, .gif, .ico, .jpeg, .jpg, .js, Map, .png, .svg, .ttf y .woff. Puede especificar los tipos de archivo adicionales.</span><span class="sxs-lookup"><span data-stu-id="7122d-p115">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff. You can specify additional file types.</span></span>
    
- <span data-ttu-id="7122d-p116">Si lo desea, puede configurar una directiva para excluir los activos que se han identificado por clasificaciones de sitio que especifique. Por ejemplo, puede elegir excluir todos los activos que están marcados como "restringido" o "confidential" incluso si son un tipo de archivo permitido y se encuentran en un origen público.</span><span class="sxs-lookup"><span data-stu-id="7122d-p116">If you want, you can configure a policy to exclude assets that have been identified by site classifications that you specify. For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>
    
 <span data-ttu-id="7122d-176">**Los atributos y las ventajas de los activos en un origen privado de hospedaje**</span><span class="sxs-lookup"><span data-stu-id="7122d-176">**Attributes and advantages of hosting assets in a private origin**</span></span>
  
- <span data-ttu-id="7122d-p117">Los usuarios solo pueden obtener acceso los activos desde un origen privado si están autorizados para hacerlo. No se les permita el acceso anónimo a estos activos.</span><span class="sxs-lookup"><span data-stu-id="7122d-p117">Users can only access the assets from a private origin if they are authorized to do so. Anonymous access to these assets is prevented.</span></span>
    
- <span data-ttu-id="7122d-179">Si quita un activo desde el origen privado, puede continuar el activo esté disponible para hasta una hora de la memoria caché; Sin embargo, se invalidará vínculos a los activos en la CDN dentro de 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7122d-179">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
    
- <span data-ttu-id="7122d-p118">Los tipos de archivo predeterminados que se incluyen para orígenes privadas son .gif, .ico, .jpeg, .jpg, .js y .png. Puede especificar los tipos de archivo adicionales.</span><span class="sxs-lookup"><span data-stu-id="7122d-p118">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png. You can specify additional file types.</span></span>
    
- <span data-ttu-id="7122d-182">Al igual que orígenes públicas, puede configurar una directiva para excluir los activos que se han identificado por las clasificaciones de sitio que especifique incluso si usar caracteres comodín para incluir todos los activos dentro de una carpeta o una biblioteca de sitios.</span><span class="sxs-lookup"><span data-stu-id="7122d-182">Just like public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or Site Library.</span></span>
    
## <a name="default-office-365-cdn-origins"></a><span data-ttu-id="7122d-183">Orígenes de Office 365 CDN predeterminada</span><span class="sxs-lookup"><span data-stu-id="7122d-183">Default Office 365 CDN origins</span></span>

<span data-ttu-id="7122d-p119">A menos que se especifique lo contrario, Office 365 configura algunos orígenes predeterminada para usted cuando se habilita la CDN de Office 365. Si excluir inicialmente, puede agregar estos orígenes después de completar el programa de instalación.</span><span class="sxs-lookup"><span data-stu-id="7122d-p119">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN. If you initially exclude them, you can add these origins after you complete setup.</span></span>
  
<span data-ttu-id="7122d-186">De forma predeterminada privados orígenes:</span><span class="sxs-lookup"><span data-stu-id="7122d-186">Default private origins:</span></span>
  
- <span data-ttu-id="7122d-187">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="7122d-187">\*/userphoto.aspx</span></span>
    
- <span data-ttu-id="7122d-188">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="7122d-188">\*/siteassets</span></span>
    
<span data-ttu-id="7122d-189">De forma predeterminada públicas orígenes:</span><span class="sxs-lookup"><span data-stu-id="7122d-189">Default public origins:</span></span>
  
- <span data-ttu-id="7122d-190">\*/MasterPage</span><span class="sxs-lookup"><span data-stu-id="7122d-190">\*/masterpage</span></span>
    
- <span data-ttu-id="7122d-191">\*biblioteca de Sheets</span><span class="sxs-lookup"><span data-stu-id="7122d-191">\*/style library</span></span>
    
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="7122d-192">Instalar y configurar la CDN de Office 365 mediante el uso de la consola de administración de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7122d-192">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>

<span data-ttu-id="7122d-p120">Los procedimientos de este tema requieren que se va a usar el Shell de administración de SharePoint Online para conectarse a SharePoint Online. Para obtener instrucciones, vea [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="7122d-p120">The procedures in this topic require you to use the SharePoint Online Management Shell to connect to SharePoint Online. For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>
  
<span data-ttu-id="7122d-195">Complete estos pasos para instalar y configurar la CDN de Office 365 para hospedar los activos de estáticos en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7122d-195">Complete these steps to set up and configure the Office 365 CDN to host your static assets in SharePoint Online.</span></span>
  
### <a name="to-enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="7122d-196">Para habilitar la organización usar la CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-196">To enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="7122d-p121">Use el cmdlet **Set-SPOTenantCdnEnabled** para habilitar la organización usar la CDN de Office 365. Puede habilitar a usar orígenes públicas, orígenes privadas o ambos, con la CDN de su organización. También puede configurar la CDN de Office 365 para omitir la configuración de orígenes de forma predeterminada cuando se habilita. Siempre puede agregar estos orígenes más adelante, tal como se describe en este tema.</span><span class="sxs-lookup"><span data-stu-id="7122d-p121">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN. You can enable your organization to use either public origins, private origins, or both with the CDN. You can also configure the Office 365 CDN to skip the setup of default origins when you enable it. You can always add these origins later as described in this topic.</span></span> 
  
<span data-ttu-id="7122d-201">En Windows Powershell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="7122d-201">In Windows Powershell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="7122d-202">Por ejemplo, para habilitar a usar orígenes públicos y privados con la CDN de su organización, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7122d-202">For example, to enable your organization to use both public and private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="7122d-203">Para habilitar la organización usar orígenes públicos y privados con la CDN pero omitir la configuración de los orígenes de forma predeterminada, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7122d-203">To enable your organization to use both public and private origins with the CDN but skip setting up the default origins, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="7122d-204">Para habilitar a usar orígenes públicas con la CDN de su organización, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7122d-204">To enable your organization to use public origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="7122d-205">Para habilitar a usar orígenes privadas con la CDN de su organización, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7122d-205">To enable your organization to use private origins with the CDN, type the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="7122d-206">Para obtener más información acerca de este cmdlet, vea [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-206">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-file-types-to-include-in-the-office-365-cdn"></a><span data-ttu-id="7122d-207">(Opcional) Para cambiar la lista de tipos de archivo que deben incluirse en la CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-207">(Optional) To change the list of file types to include in the Office 365 CDN</span></span>
<span data-ttu-id="7122d-208"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-208"></span></span>

> [!TIP]
> <span data-ttu-id="7122d-p122">Al definir tipos de archivo mediante el cmdlet **Set-SPOTenantCdnPolicy** , sobrescribir la lista definida actualmente. Si desea agregar otros tipos de archivo a la lista, use el cmdlet en primer lugar para averiguar qué tipos de archivo que ya están permitidos e incluyen en la lista junto con las nuevas.</span><span class="sxs-lookup"><span data-stu-id="7122d-p122">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span> 
  
<span data-ttu-id="7122d-p123">Use el cmdlet **Set-SPOTenantCdnPolicy** para definir tipos de archivos estáticos que se pueden hospedar orígenes públicos y privados en la CDN. De forma predeterminada, se permiten tipos comunes de activos para .js, .gif, .jpg y .css de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7122d-p123">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN. By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span> 
  
<span data-ttu-id="7122d-213">En Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="7122d-213">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="7122d-214">Para ver qué tipos de archivo se permiten actualmente por la CDN, use el cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="7122d-214">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="7122d-215">Para obtener más información acerca de estos cmdlets, consulte [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) y [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-215">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="optional-to-change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="7122d-216">(Opcional) Para cambiar la lista de clasificaciones de sitio que desea excluir desde la CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-216">(Optional) To change the list of site classifications you want to exclude from the Office 365 CDN</span></span>
<span data-ttu-id="7122d-217"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-217"></span></span>

> [!TIP]
> <span data-ttu-id="7122d-p124">Cuando se excluyen las clasificaciones de sitio mediante el cmdlet **Set-SPOTenantCdnPolicy** , sobrescribir la lista definida actualmente. Si desea excluir las clasificaciones de sitios adicionales, use el cmdlet en primer lugar para averiguar qué clasificaciones están ya excluidas y agregarlos a continuación, junto con las nuevas.</span><span class="sxs-lookup"><span data-stu-id="7122d-p124">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list. If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span> 
  
<span data-ttu-id="7122d-p125">Use el cmdlet **Set-SPOTenantCdnPolicy** para excluir las clasificaciones de sitio que no desea que esté disponible a través de la red CDN. De forma predeterminada, no se excluyen ningún clasificaciones de sitio.</span><span class="sxs-lookup"><span data-stu-id="7122d-p125">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN. By default, no site classifications are excluded.</span></span> 
  
<span data-ttu-id="7122d-222">En Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="7122d-222">In Windows PowerShell for SharePoint Online:</span></span>
  
```
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="7122d-223">Para ver qué clasificaciones de sitio están actualmente restringidas, use el cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="7122d-223">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span> 
  
```
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="7122d-224">Para obtener más información acerca de estos cmdlets, consulte [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) y [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-224">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/en-us/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/en-us/library/mt800838.aspx).</span></span>
  
### <a name="to-add-an-origin-for-your-assets"></a><span data-ttu-id="7122d-225">Para agregar un origen de los activos</span><span class="sxs-lookup"><span data-stu-id="7122d-225">To add an origin for your assets</span></span>
<span data-ttu-id="7122d-226"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-226"></span></span>

<span data-ttu-id="7122d-p126">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir un origen. Puede definir varios orígenes. El origen es una dirección URL que apunta a una biblioteca de SharePoint o la carpeta que contiene los activos que desea que se hospeda la CDN.</span><span class="sxs-lookup"><span data-stu-id="7122d-p126">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin. You can define multiple origins. The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span> 
  
> [!IMPORTANT]
> <span data-ttu-id="7122d-230">Si se identifica un origen público en su CDN, nunca debe colocar los recursos que se consideran confidenciales de su organización en el origen público o la biblioteca de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7122d-230">If you identify a public origin in your CDN, you should never place resources that are considered sensitive to your organization in the public origin or SharePoint Online library.</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path >
```

<span data-ttu-id="7122d-p127">Donde ruta de acceso es la ruta de acceso a la carpeta que contiene los activos. Puede usar caracteres comodín además de rutas de acceso relativas. Por ejemplo, para incluir todos los activos en la carpeta masterpages para todos los sitios como un origen público dentro de la red CDN, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7122d-p127">Where path is the path to the folder that contains the assets. You can use wildcards in addition to relative paths. For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>
  
```
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

<span data-ttu-id="7122d-234">Para obtener más información acerca de este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-234">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="7122d-p128">Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de datos. Esto tarda 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7122d-p128">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="7122d-237">Ejemplo: Configurar un origen público para las páginas maestras y para la biblioteca de estilos de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7122d-237">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>
<span data-ttu-id="7122d-238"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-238"></span></span>

<span data-ttu-id="7122d-p129">Normalmente, estos orígenes se configuran para de forma predeterminada cuando se habilitan orígenes públicas para la CDN de Office 365. Sin embargo, si desea habilitarlos manualmente, siga estos pasos.</span><span class="sxs-lookup"><span data-stu-id="7122d-p129">Normally, these origins are set up for you by default when you enable public origins for the Office 365 CDN. However, if you want to enable them manually, follow these steps.</span></span>
  
- <span data-ttu-id="7122d-241">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la biblioteca de estilos como un origen público dentro de la CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7122d-241">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

- <span data-ttu-id="7122d-242">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir las páginas maestras como un origen público dentro de la CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7122d-242">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

- <span data-ttu-id="7122d-243">Para obtener más información acerca de este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-243">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="7122d-p130">Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de datos. Esto tarda 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7122d-p130">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="7122d-246">Ejemplo: Configurar un origen privado para los activos del sitio, las páginas del sitio e imágenes de publicación de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7122d-246">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>
<span data-ttu-id="7122d-247"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-247"></span></span>

- <span data-ttu-id="7122d-248">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta de activos de sitios como un origen privado dentro de la CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7122d-248">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

- <span data-ttu-id="7122d-249">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta de páginas de sitio como un origen privado dentro de la CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7122d-249">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

- <span data-ttu-id="7122d-250">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta de imágenes de publicación como un origen privado dentro de la CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7122d-250">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin within the Office 365 CDN.</span></span> 
    
  ```
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

    <span data-ttu-id="7122d-251">Para obtener más información acerca de este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-251">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
    
    <span data-ttu-id="7122d-p131">Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de datos. Esto tarda 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7122d-p131">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
    
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="7122d-254">Ejemplo: Configurar un origen privado para una colección de sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7122d-254">Example: Configure a private origin for a site collection for SharePoint Online</span></span>
<span data-ttu-id="7122d-255"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-255"></span></span>

<span data-ttu-id="7122d-p132">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir una colección de sitios como un origen privado dentro de la CDN de Office 365. Por ejemplo,</span><span class="sxs-lookup"><span data-stu-id="7122d-p132">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin within the Office 365 CDN. For example,</span></span> 
  
```
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="7122d-258">Para obtener más información acerca de este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-258">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="7122d-p133">Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de datos. Esto tarda 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7122d-p133">Once you've run the command, the system synchronizes the configuration across the datacenter. This takes 15 minutes.</span></span>
  
## <a name="manage-the-office-365-cdn"></a><span data-ttu-id="7122d-261">Administrar Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="7122d-261">Manage the Office 365 CDN</span></span>
<span data-ttu-id="7122d-262"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-262"></span></span>

<span data-ttu-id="7122d-263">Una vez haya configurado la CDN, puede realizar los cambios en la configuración como actualizar contenido o a medida que cambian las necesidades, tal como se describe en esta sección.</span><span class="sxs-lookup"><span data-stu-id="7122d-263">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
### <a name="to-add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="7122d-264">Para agregar, actualizar o quitar activos desde la CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-264">To add, update, or remove assets from the Office 365 CDN</span></span>
<span data-ttu-id="7122d-265"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-265"></span></span>

<span data-ttu-id="7122d-p134">Una vez que haya completado los pasos del programa de instalación, puede agregar nuevos activos y actualizar o quitar activos existentes siempre que lo desee. Simplemente, realice los cambios en los activos de la carpeta o biblioteca de SharePoint que ha identificado como un origen. Si agrega un nuevo activo, está disponible a través de la red CDN inmediatamente. Sin embargo, si actualiza los activos, se tardará hasta 15 minutos para la nueva copia propagar y dejarán de estar disponibles en la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7122d-p134">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want. Just make your changes to the assets in the folder or SharePoint library that you identified as an origin. If you add a new asset, it is available through the CDN immediately. However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="7122d-p135">Si necesita recuperar la ubicación del origen, puede usar el cmdlet **Get-SPOTenantCdnOrigins** . Para obtener información acerca de cómo usar este cmdlet, vea [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-p135">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet. For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/en-us/library/mt790770.aspx).</span></span>
  
### <a name="to-remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="7122d-272">Para quitar un origen desde la CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-272">To remove an origin from the Office 365 CDN</span></span>
<span data-ttu-id="7122d-273"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-273"></span></span>

<span data-ttu-id="7122d-p136">Si necesita, puede quitar el acceso a una carpeta o biblioteca de SharePoint que ha identificado como un origen. Para ello, use el cmdlet **Remove-SPOTenantCdnOrigin** . Para obtener información acerca de cómo usar este cmdlet, vea [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-p136">If you need to, you can remove access to a folder or SharePoint library that you identified as an origin. To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet. For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/en-us/library/mt790761.aspx).</span></span>
  
### <a name="to-modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="7122d-277">Para modificar un origen en la CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-277">To modify an origin in the Office 365 CDN</span></span>
<span data-ttu-id="7122d-278"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-278"></span></span>

<span data-ttu-id="7122d-p137">No se puede modificar un origen que se ha creado. En su lugar, quite el origen y, a continuación, agregar una nueva. Para obtener más información, vea [para quitar un origen desde la CDN de Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) y [para agregar un origen para los activos](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="7122d-p137">You can't modify an origin you've created. Instead, remove the origin and then add a new one. For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>
  
### <a name="to-disable-the-office-365-cdn"></a><span data-ttu-id="7122d-282">Para deshabilitar la CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7122d-282">To disable the Office 365 CDN</span></span>
<span data-ttu-id="7122d-283"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-283"></span></span>

<span data-ttu-id="7122d-p138">Use el cmdlet **Set-SPOTenantCdnEnabled** para deshabilitar la CDN para su organización. Si dispone de los orígenes públicos y privados habilitados para la CDN, debe ejecutar el cmdlet dos veces como se muestra en los ejemplos siguientes.</span><span class="sxs-lookup"><span data-stu-id="7122d-p138">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization. If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span> 
  
<span data-ttu-id="7122d-286">Para deshabilitar el uso de orígenes públicas en la CDN de Windows Powershell para SharePoint Online, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7122d-286">To disable use of public origins in the CDN, in Windows Powershell for SharePoint Online, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="7122d-287">Para deshabilitar el uso de los orígenes de privada en la red CDN, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7122d-287">To disable use of the private origins in the CDN, enter the following command:</span></span>
  
```
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="7122d-288">Para obtener más información acerca de este cmdlet, vea [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="7122d-288">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/en-us/library/mt790765.aspx).</span></span>
  
## <a name="troubleshooting-your-office-365-cdn-configuration"></a><span data-ttu-id="7122d-289">Solución de problemas de la configuración de Office 365 CDN</span><span class="sxs-lookup"><span data-stu-id="7122d-289">Troubleshooting your Office 365 CDN configuration</span></span>
<span data-ttu-id="7122d-290"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="7122d-290"></span></span>

<span data-ttu-id="7122d-p139">El extremo no inmediatamente estará disponible para su uso, como sea necesario hora para el registro en propagarse a través de la red CDN. Configuración tarda 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7122d-p139">The endpoint will not immediately be available for use, as it takes time for the registration to propagate through the CDN. Configuration takes 15 minutes.</span></span>
  

