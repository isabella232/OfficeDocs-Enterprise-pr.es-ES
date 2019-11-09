---
title: Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 10/22/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: bebb285f-1d54-4f79-90a5-94985afc6af8
description: Describe cómo usar la red de entrega de contenido (CDN) de Office 365 para acelerar la entrega de los activos de SharePoint Online a todos los usuarios, independientemente de dónde se encuentren o de la forma en que tengan acceso al contenido.
ms.openlocfilehash: eedbbbf143890e336ae16f80a135f611b9e65f26
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077959"
---
# <a name="use-the-office-365-content-delivery-network-cdn-with-sharepoint-online"></a><span data-ttu-id="7e2a4-103">Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-103">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>

<span data-ttu-id="7e2a4-104">Puede usar la red de entrega de contenido (CDN) de Office 365 integrada para hospedar archivos estáticos y mejorar el rendimiento de las páginas de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-104">You can use the built-in Office 365 Content Delivery Network (CDN) to host static assets to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="7e2a4-105">La CDN de Office 365 mejora el rendimiento al almacenamiento en caché los archivos estáticos más cerca de los exploradores que los solicitan, lo que ayuda a acelerar descargas y reducir la latencia.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="7e2a4-106">Además, la red CDN de Office 365 usa el [protocolo http/2](https://en.wikipedia.org/wiki/HTTP/2) para mejorar la compresión y la canalización http.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-106">Also, the Office 365 CDN uses the [HTTP/2 protocol](https://en.wikipedia.org/wiki/HTTP/2) for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="7e2a4-107">La red CDN de Office 365 se incluye como parte de la suscripción a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2a4-108">La red CDN de Office 365 solo está disponible para los inquilinos en la nube de **producción** (en todo el mundo).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-108">The Office 365 CDN is only available to tenants in the **Production** (worldwide) cloud.</span></span> <span data-ttu-id="7e2a4-109">Actualmente, los inquilinos de las nubes del gobierno de Estados Unidos, China y Alemania no admiten la red CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-109">Tenants in the US Government, China and Germany clouds do not currently support the Office 365 CDN.</span></span>

<span data-ttu-id="7e2a4-110">La CDN de Office 365 se compone de varias redes CDN que permite hospedar archivos estáticos en varias ubicaciones u _orígenes_ y a realizar la entrega desde redes de alta velocidad globales.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-110">The Office 365 CDN is composed of multiple CDNs that allow you to host static assets in multiple locations, or _origins_, and serve them from global high-speed networks.</span></span> <span data-ttu-id="7e2a4-111">Según el tipo de contenido que quiera hospedar en la CDN de Office 365, puede agregar orígenes **públicos**, **privados** o ambos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-111">Depending on the kind of content you want to host in the Office 365 CDN, you can add **public** origins, **private** origins or both.</span></span> <span data-ttu-id="7e2a4-112">Vea [elegir si cada origen debe ser público o privado](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) para obtener más información sobre la diferencia entre los orígenes públicos y privados.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-112">See [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate) for more information on the difference between public and private origins.</span></span>

<span data-ttu-id="7e2a4-113">![Diagrama conceptual de la red CDN de Office 365](media/O365-CDN/o365-cdn-flow-transparent.svg "Diagrama conceptual de la red CDN de Office 365")</span><span class="sxs-lookup"><span data-stu-id="7e2a4-113">![Office 365 CDN conceptual diagram](media/O365-CDN/o365-cdn-flow-transparent.svg "Office 365 CDN conceptual diagram")</span></span>

<span data-ttu-id="7e2a4-114">Si ya está familiarizado con la forma en que las redes CDN funcionan, solo tiene que realizar algunos pasos para habilitar la red CDN de Office 365 para su inquilino.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-114">If you are already familiar with the way that CDNs work, you only need to complete a few steps to enable the Office 365 CDN for your tenant.</span></span> <span data-ttu-id="7e2a4-115">En este tema se describe cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-115">This topic describes how.</span></span> <span data-ttu-id="7e2a4-116">Siga leyendo para obtener información sobre cómo empezar a hospedar sus activos estáticos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-116">Read on for information about how to get started hosting your static assets.</span></span>

> [!TIP]
> <span data-ttu-id="7e2a4-117">Hay otras CDN hospedadas por Microsoft que se pueden usar con Office 365 para escenarios de uso especializados, pero que no se tratan en este tema porque quedan fuera del ámbito de la red CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-117">There are other Microsoft-hosted CDNs that can be used with Office 365 for specialized usage scenarios, but are not discussed in this topic because they fall outside the scope of the Office 365 CDN.</span></span> <span data-ttu-id="7e2a4-118">Para obtener más información, consulte [otros CDN de Microsoft](content-delivery-networks.md#other-microsoft-cdns).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-118">For more information, see [Other Microsoft CDNs](content-delivery-networks.md#other-microsoft-cdns).</span></span>

 <span data-ttu-id="7e2a4-119">**Vuelva a la [planeación de red y ajuste del rendimiento para Office 365](https://aka.ms/tune).**</span><span class="sxs-lookup"><span data-stu-id="7e2a4-119">**Head back to [Network planning and performance tuning for Office 365](https://aka.ms/tune).**</span></span>

## <a name="overview-of-working-with-the-office-365-cdn-in-sharepoint-online"></a><span data-ttu-id="7e2a4-120">Información general sobre el uso de la red CDN de Office 365 en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-120">Overview of working with the Office 365 CDN in SharePoint Online</span></span>

<span data-ttu-id="7e2a4-121">Para configurar la red CDN de Office 365 para su organización, siga estos pasos básicos:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-121">To set up the Office 365 CDN for your organization, you follow these basic steps:</span></span>

+ [<span data-ttu-id="7e2a4-122">Planeación de la implementación de la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-122">Plan for deployment of the Office 365 CDN</span></span>](use-office-365-cdn-with-spo.md#plan-for-deployment-of-the-office-365-cdn)

  + <span data-ttu-id="7e2a4-123">[Determine qué activos estáticos desea hospedar en la red CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-123">[Determine which static assets you want to host on the CDN](use-office-365-cdn-with-spo.md#CDNAssets).</span></span>
  + <span data-ttu-id="7e2a4-124">[Determine dónde desea almacenar los activos](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-124">[Determine where you want to store your assets](use-office-365-cdn-with-spo.md#CDNStoreAssets).</span></span> <span data-ttu-id="7e2a4-125">Esta ubicación puede ser un sitio de SharePoint, una biblioteca o una carpeta y se denomina _origen_.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-125">This location can be a SharePoint site, library or folder and is called an _origin_.</span></span>
  + <span data-ttu-id="7e2a4-126">[Elija si cada origen debe ser público o privado](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-126">[Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span> <span data-ttu-id="7e2a4-127">Puede agregar varios orígenes de tipos públicos y privados.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-127">You can add multiple origins of both public and private types.</span></span>

+ <span data-ttu-id="7e2a4-128">Instalar y configurar la red CDN mediante PowerShell o la CLI de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-128">Set up and configure the CDN, using either PowerShell or the SharePoint Online CLI</span></span>

  + [<span data-ttu-id="7e2a4-129">Instalar y configurar la red CDN mediante el shell de administración de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-129">Set up and configure the CDN by using the SharePoint Online Management Shell</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinPShell)
  + [<span data-ttu-id="7e2a4-130">Instalar y configurar la red CDN mediante la CLI de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-130">Set up and configure the CDN by using the Office 365 CLI</span></span>](use-office-365-cdn-with-spo.md#CDNSetupinCLI)

  <span data-ttu-id="7e2a4-131">Cuando haya completado este paso, tendrá:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-131">When you complete this step, you will have:</span></span>

  + <span data-ttu-id="7e2a4-132">Habilitó la red CDN para su organización.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-132">Enabled the CDN for your organization.</span></span>
  + <span data-ttu-id="7e2a4-133">Se agregaron sus orígenes, identificando cada origen como público o privado.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-133">Added your origins, identifying each origin as public or private.</span></span>

<span data-ttu-id="7e2a4-134">Una vez que haya terminado con el programa de instalación, puede [administrar la red CDN de Office 365](use-office-365-cdn-with-spo.md#CDNManage) con el tiempo:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-134">Once you're done with setup, you can [Manage the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNManage) over time by:</span></span>
  
+ <span data-ttu-id="7e2a4-135">Adición, actualización y eliminación de activos</span><span class="sxs-lookup"><span data-stu-id="7e2a4-135">Adding, updating, and removing assets</span></span>
+ <span data-ttu-id="7e2a4-136">Agregar y quitar orígenes</span><span class="sxs-lookup"><span data-stu-id="7e2a4-136">Adding and removing origins</span></span>
+ <span data-ttu-id="7e2a4-137">Configuración de directivas de CDN</span><span class="sxs-lookup"><span data-stu-id="7e2a4-137">Configuring CDN policies</span></span>
+ <span data-ttu-id="7e2a4-138">Si es necesario, deshabilitar la red CDN</span><span class="sxs-lookup"><span data-stu-id="7e2a4-138">If necessary, disabling the CDN</span></span>

<span data-ttu-id="7e2a4-139">Por último, vea [usar los activos de la red CDN](use-office-365-cdn-with-spo.md#using-your-cdn-assets) para obtener información sobre cómo obtener acceso a los recursos de la red CDN desde orígenes públicos y privados.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-139">Finally, see [Using your CDN assets](use-office-365-cdn-with-spo.md#using-your-cdn-assets) to learn about accessing your CDN assets from both public and private origins.</span></span>

<span data-ttu-id="7e2a4-140">Consulte [Troubleshooting The Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) para obtener instrucciones sobre cómo resolver problemas comunes.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-140">See [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) for guidance on resolving common issues.</span></span>

## <a name="plan-for-deployment-of-the-office-365-cdn"></a><span data-ttu-id="7e2a4-141">Planeación de la implementación de la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-141">Plan for deployment of the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-142">Antes de implementar la red CDN de Office 365 para su inquilino de Office 365, debe tener en cuenta los siguientes factores como parte del proceso de planeación.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-142">Before you deploy the Office 365 CDN for your Office 365 tenant, you should consider the following factors as part of your planning process.</span></span>

  + [<span data-ttu-id="7e2a4-143">Determinación de los activos estáticos que desea hospedar en la red CDN</span><span class="sxs-lookup"><span data-stu-id="7e2a4-143">Determine which static assets you want to host on the CDN</span></span>](use-office-365-cdn-with-spo.md#CDNAssets)
  + [<span data-ttu-id="7e2a4-144">Determinar dónde desea almacenar los activos</span><span class="sxs-lookup"><span data-stu-id="7e2a4-144">Determine where you want to store your assets</span></span>](use-office-365-cdn-with-spo.md#CDNStoreAssets)
  + [<span data-ttu-id="7e2a4-145">Elegir si cada origen debe ser público o privado</span><span class="sxs-lookup"><span data-stu-id="7e2a4-145">Choose whether each origin should be public or private</span></span>](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate)

<span data-ttu-id="7e2a4-146"><a name="CDNAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-146"></span></span>
### <a name="determine-which-static-assets-you-want-to-host-on-the-cdn"></a><span data-ttu-id="7e2a4-147">Determinación de los activos estáticos que desea hospedar en la red CDN</span><span class="sxs-lookup"><span data-stu-id="7e2a4-147">Determine which static assets you want to host on the CDN</span></span>

<span data-ttu-id="7e2a4-148">En general, las CDN son más eficaces para hospedar _activos estáticos_o activos que no cambian muy a menudo.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-148">In general, CDNs are most effective for hosting _static assets_, or assets that don't change very often.</span></span> <span data-ttu-id="7e2a4-149">Una buena regla general es identificar los archivos que cumplan algunas o todas estas condiciones:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-149">A good rule of thumb is to identify files that meet some or all of these conditions:</span></span>

+ <span data-ttu-id="7e2a4-150">Archivos estáticos incrustados en una página (como scripts e imágenes) que pueden tener un impacto incremental importante en los tiempos de carga de la página</span><span class="sxs-lookup"><span data-stu-id="7e2a4-150">Static files embedded in a page (like scripts and images) that may have a significant incremental impact on page load times</span></span>
+ <span data-ttu-id="7e2a4-151">Archivos grandes como archivos ejecutables y archivos de instalación</span><span class="sxs-lookup"><span data-stu-id="7e2a4-151">Large files like executables and installation files</span></span>
+ <span data-ttu-id="7e2a4-152">Bibliotecas de recursos que admiten código del lado cliente</span><span class="sxs-lookup"><span data-stu-id="7e2a4-152">Resource libraries that support client-side code</span></span>

<span data-ttu-id="7e2a4-153">Por ejemplo, los archivos pequeños que se solicitan repetidamente como las imágenes de sitio y las secuencias de comandos pueden mejorar significativamente el rendimiento de la representación del sitio y reducir de forma incremental la carga en los sitios de SharePoint Online cuando se agregan a un origen de CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-153">For example, small files that are repeatedly requested like site images and scripts can significantly improve site rendering performance and incrementally reduce the load on your SharePoint Online sites when you add them to a CDN origin.</span></span> <span data-ttu-id="7e2a4-154">Los archivos de mayor tamaño, como los ejecutables de instalación, se pueden descargar desde la red CDN, lo que ofrece un impacto positivo en el rendimiento y una reducción posterior de la carga en el sitio de SharePoint Online, incluso si no se tiene acceso a ellos con tanta frecuencia.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-154">Larger files such as installation executables can be downloaded from the CDN, delivering a positive performance impact and subsequent reduction of the load on your SharePoint Online site, even if they are not accessed as often.</span></span>

<span data-ttu-id="7e2a4-155">La mejora del rendimiento para cada archivo depende de muchos factores, como la proximidad del cliente al extremo de la red CDN más cercano, las condiciones transitorias de la red local, etc.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-155">Performance improvement on a per-file basis is dependent on many factors, including the client's proximity to the nearest CDN endpoint, transient conditions on the local network, and so forth.</span></span> <span data-ttu-id="7e2a4-156">Muchos archivos estáticos son muy pequeños y se pueden descargar de Office 365 en menos de un segundo.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-156">Many static files are quite small, and can be downloaded from Office 365 in less than a second.</span></span> <span data-ttu-id="7e2a4-157">Sin embargo, una página web puede contener muchos archivos incrustados con un tiempo de descarga acumulado de varios segundos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-157">However, a web page may contain many embedded files with a cumulative download time of several seconds.</span></span> <span data-ttu-id="7e2a4-158">El servicio de estos archivos desde la red CDN puede reducir significativamente el tiempo de carga de página general.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-158">Serving these files from the CDN can significantly reduce the overall page load time.</span></span> <span data-ttu-id="7e2a4-159">Consulte [¿Qué beneficios de rendimiento proporciona una red CDN?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) para obtener un ejemplo.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-159">See [What performance gains does a CDN provide?](content-delivery-networks.md#what-performance-gains-does-a-cdn-provide) for an example.</span></span>

<span data-ttu-id="7e2a4-160"><a name="CDNStoreAssets"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-160"></span></span>
### <a name="determine-where-you-want-to-store-your-assets"></a><span data-ttu-id="7e2a4-161">Determinar dónde desea almacenar los activos</span><span class="sxs-lookup"><span data-stu-id="7e2a4-161">Determine where you want to store your assets</span></span>

<span data-ttu-id="7e2a4-162">La red CDN recopila los activos de una ubicación denominada _origen_.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-162">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="7e2a4-163">Un origen puede ser un sitio de SharePoint, una biblioteca de documentos o una carpeta a la que se pueda tener acceso mediante una dirección URL.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-163">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span> <span data-ttu-id="7e2a4-164">Tiene gran flexibilidad al especificar los orígenes de su organización.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-164">You have great flexibility when you specify origins for your organization.</span></span> <span data-ttu-id="7e2a4-165">Por ejemplo, puede especificar varios orígenes o un único origen donde desea colocar todos los activos de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-165">For example, you can specify multiple origins or a single origin where you want to put all your CDN assets.</span></span> <span data-ttu-id="7e2a4-166">Puede elegir entre los orígenes públicos o privados de su organización.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-166">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="7e2a4-167">La mayoría de las organizaciones optarán por implementar una combinación de ambos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-167">Most organizations will choose to implement a combination of the two.</span></span>

<span data-ttu-id="7e2a4-168">Puede crear un nuevo contenedor para sus orígenes, como carpetas o bibliotecas de documentos, y agregar archivos que desee que estén disponibles desde la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-168">You can create new container for your origins such as folders or document libraries, and add files you want to make available from the CDN.</span></span> <span data-ttu-id="7e2a4-169">Este es un buen enfoque si tiene un conjunto específico de activos que desea que esté disponible desde la red CDN y desea restringir el conjunto de activos de la red CDN solo a los archivos del contenedor.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-169">This is a good approach if you have a specific set of assets you want to be available from the CDN, and want to restrict the set of CDN assets to only those files in the container.</span></span>

<span data-ttu-id="7e2a4-170">También puede configurar una colección de sitios, un sitio, una biblioteca o una carpeta existentes como un origen, lo que hará que todos los activos elegibles del contenedor estén disponibles desde la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-170">You can also configure an existing site collection, site, library or folder as an origin, which will make all eligible assets in the container available from the CDN.</span></span> <span data-ttu-id="7e2a4-171">Antes de agregar un contenedor existente como origen, es importante asegurarse de que está al tanto de su contenido y permisos para que no exponga involuntariamente los activos al acceso anónimo o a los usuarios no autorizados.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-171">Before you add an existing container as an origin, it's important to make sure you are aware of its contents and permissions so you do not inadvertently expose assets to anonymous access or unauthorized users.</span></span>

<span data-ttu-id="7e2a4-172">Puede definir _directivas de CDN_ para excluir el contenido de los orígenes de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-172">You can define _CDN policies_ to exclude content in your origins from the CDN.</span></span> <span data-ttu-id="7e2a4-173">Las directivas de CDN excluyen los activos de los orígenes públicos o privados mediante atributos como el _tipo de archivo_ y la _clasificación del sitio_, y se aplican a todos los orígenes del CdnType (privado o público) que especifique en la Directiva.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-173">CDN policies exclude assets in public or private origins by attributes such as _file type_ and _site classification_, and are applied to all origins of the CdnType (private or public) you specify in the policy.</span></span> <span data-ttu-id="7e2a4-174">Por ejemplo, si agrega un origen privado que consta de un sitio que contiene varios subsitios, puede definir una directiva para excluir los sitios marcados como **confidenciales** para que el contenido de los sitios con esa clasificación aplicada no se atienda desde la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-174">For example, if you add a private origin consisting of a site that contains multiple subsites, you can define a policy to exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span> <span data-ttu-id="7e2a4-175">La Directiva se aplicará al contenido de _todos los_ orígenes privados que haya agregado a la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-175">The policy will apply to content from _all_ private origins you have added to the CDN.</span></span>
  
<span data-ttu-id="7e2a4-176">Tenga en cuenta que cuanto mayor sea el número de orígenes, mayor será el impacto en el tiempo que tarda el servicio de la red CDN en procesar las solicitudes.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-176">Keep in mind that the greater the number of origins, the greater the impact on the time it takes the CDN service to process requests.</span></span> <span data-ttu-id="7e2a4-177">Le recomendamos que limite el número de orígenes tanto como sea posible.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-177">We recommend that you limit the number of origins as much as possible.</span></span>
  
<span data-ttu-id="7e2a4-178"><a name="CDNOriginChoosePublicPrivate"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-178"></span></span>
### <a name="choose-whether-each-origin-should-be-public-or-private"></a><span data-ttu-id="7e2a4-179">Elegir si cada origen debe ser público o privado</span><span class="sxs-lookup"><span data-stu-id="7e2a4-179">Choose whether each origin should be public or private</span></span>

<span data-ttu-id="7e2a4-180">Cuando se identifica un origen, se especifica si se debe hacer _público_ o _privado_.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-180">When you identify an origin, you specify whether it should be made _public_ or _private_.</span></span> <span data-ttu-id="7e2a4-181">El acceso a los activos de CDN en los orígenes públicos es anónimo y el contenido de la red CDN en los orígenes privados está protegido mediante tokens generados dinámicamente para una mayor seguridad.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-181">Access to CDN assets in public origins is anonymous, and CDN content in private origins is secured by dynamically generated tokens for greater security.</span></span> <span data-ttu-id="7e2a4-182">Independientemente de la opción que elija, Microsoft realiza todo el levantamiento en su caso cuando se trata de administrar la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-182">Regardless of which option you choose, Microsoft does all the heavy lifting for you when it comes to administration of the CDN itself.</span></span> <span data-ttu-id="7e2a4-183">Además, puede cambiar de opinión más adelante, una vez que haya configurado la red CDN y identificado sus orígenes.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-183">Also, you can change your mind later, after you've set up the CDN and identified your origins.</span></span>

<span data-ttu-id="7e2a4-184">Tanto las opciones públicas como las privadas proporcionan mejoras de rendimiento similares, pero cada una tiene atributos y ventajas únicos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-184">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span>

<span data-ttu-id="7e2a4-185">Se puede obtener acceso a los orígenes **públicos** de la red CDN de Office 365 de forma anónima y cualquier usuario que tenga la dirección URL para el activo podrá acceder a los recursos hospedados.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-185">**Public** origins within the Office 365 CDN are accessible anonymously, and hosted assets can be accessed by anyone who has the URL to the asset.</span></span> <span data-ttu-id="7e2a4-186">Como el acceso al contenido en orígenes públicos es anónimo, solo debe usarlos para almacenar en caché contenido genérico y no confidencial, como archivos javascript, scripts, iconos e imágenes.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-186">Because access to content in public origins is anonymous, you should only use them to cache non-sensitive generic content such as javascript files, scripts, icons and images.</span></span>

<span data-ttu-id="7e2a4-187">Los orígenes **privados** de la red CDN de Office 365 proporcionan acceso privado al contenido del usuario, como las bibliotecas de documentos de SharePoint Online, los sitios y las imágenes de propietario.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-187">**Private** origins within the Office 365 CDN provide private access to user content such as SharePoint Online document libraries, sites and proprietary images.</span></span> <span data-ttu-id="7e2a4-188">El acceso al contenido de orígenes privados está protegido por tokens generados dinámicamente, por lo que solo los usuarios con permisos para la biblioteca de documentos o la ubicación de almacenamiento originales pueden tener acceso a ellos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-188">Access to content in private origins is secured by dynamically generated tokens so it can only be accessed by users with permissions to the original document library or storage location.</span></span> <span data-ttu-id="7e2a4-189">Los orígenes privados de la red CDN de Office 365 solo se pueden usar para el contenido de SharePoint Online y solo puede tener acceso a activos en orígenes privados mediante el redireccionamiento desde su espacio empresarial de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-189">Private origins in the Office 365 CDN can only be used for SharePoint Online content, and you can only access assets in private origins through redirection from your SharePoint Online tenant.</span></span>

<span data-ttu-id="7e2a4-190">Puede obtener más información sobre cómo el acceso de la red CDN a los activos de un origen privado trabaja en el [uso de activos en orígenes privados](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-190">You can read more about how CDN access to assets in a private origin works in [Using assets in private origins](use-office-365-cdn-with-spo.md#using-assets-in-private-origins).</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-public-origins"></a><span data-ttu-id="7e2a4-191">Atributos y ventajas de hospedar activos en orígenes públicos</span><span class="sxs-lookup"><span data-stu-id="7e2a4-191">Attributes and advantages of hosting assets in public origins</span></span>
  
+ <span data-ttu-id="7e2a4-192">Cualquier persona puede acceder a los activos expuestos en un origen público de forma anónima.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-192">Assets exposed in a public origin are accessible by everyone anonymously.</span></span>
    > [!IMPORTANT]
    > <span data-ttu-id="7e2a4-193">Nunca debe poner recursos que contengan información de usuario o que se consideren confidenciales para su organización en un origen público.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-193">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>
+ <span data-ttu-id="7e2a4-194">Si elimina un activo de un origen público, el activo podría continuar disponible durante un máximo de 30 días desde la memoria caché. Sin embargo, se invalidarán los vínculos a los activos en la red CDN en 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-194">If you remove an asset from a public origin, the asset may continue to be available for up to 30 days from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes.</span></span>
+ <span data-ttu-id="7e2a4-195">Si hospeda hojas de estilo (archivos CSS) en un origen público, puede usar las rutas relativas y URI dentro del código.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-195">When you host style sheets (CSS files) in a public origin, you can use relative paths and URIs within the code.</span></span> <span data-ttu-id="7e2a4-196">Esto significa que puede hacer referencia a la ubicación de las imágenes de fondo y otros objetos con respecto a la ubicación del activo que está llamando.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-196">This means that you can reference the location of background images and other objects relative to the location of the asset that's calling it.</span></span>
+ <span data-ttu-id="7e2a4-197">Aunque puede integrar una dirección URL de un origen público, no se recomienda.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-197">While you can hard code a public origin's URL, doing so is not recommended.</span></span> <span data-ttu-id="7e2a4-198">El motivo de esto es que, si no está disponible el acceso a la red CDN, la dirección URL no resolverá automáticamente su organización en SharePoint Online y podría producir vínculos rotos y otros errores.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-198">The reason for this is that if access to the CDN becomes unavailable, the URL will not automatically resolve to your organization in SharePoint Online and might result in broken links and other errors.</span></span>
+ <span data-ttu-id="7e2a4-199">Los tipos de archivo predeterminado que se incluyen en los orígenes públicos son: css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf y .woff.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-199">The default file types that are included for public origins are .css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff.</span></span> <span data-ttu-id="7e2a4-200">Puede especificar tipos de archivo adicionales.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-200">You can specify additional file types.</span></span>
+ <span data-ttu-id="7e2a4-201">Puede configurar una directiva para excluir los activos que han sido identificados por las clasificaciones de sitio que especifique.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-201">You can configure a policy to exclude assets that have been identified by site classifications that you specify.</span></span> <span data-ttu-id="7e2a4-202">Por ejemplo, puede elegir excluir todos los activos que están marcados como restringidos o confidenciales aunque sean un tipo de archivo permitido y se encuentren en un origen público.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-202">For example, you can choose to exclude all assets that are marked as "confidential" or "restricted" even if they are an allowed file type and are located in a public origin.</span></span>

#### <a name="attributes-and-advantages-of-hosting-assets-in-private-origins"></a><span data-ttu-id="7e2a4-203">Atributos y ventajas de hospedar activos en orígenes privados</span><span class="sxs-lookup"><span data-stu-id="7e2a4-203">Attributes and advantages of hosting assets in private origins</span></span>

+ <span data-ttu-id="7e2a4-204">Los orígenes privados solo pueden usarse para los activos de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-204">Private origins can only be used for SharePoint Online assets.</span></span>
+ <span data-ttu-id="7e2a4-205">Los usuarios solo pueden tener acceso a los activos desde un origen privado si tienen permisos de acceso al contenedor.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-205">Users can only access the assets from a private origin if they have permissions to access the container.</span></span> <span data-ttu-id="7e2a4-206">Se impide el acceso anónimo a estos activos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-206">Anonymous access to these assets is prevented.</span></span>
+ <span data-ttu-id="7e2a4-207">Los activos en orígenes privados deben remitirse desde el espacio empresarial de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-207">Assets in private origins must be referred from the SharePoint Online tenant.</span></span> <span data-ttu-id="7e2a4-208">El acceso directo a los activos de la red CDN privada no funciona.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-208">Direct access to private CDN assets does not work.</span></span>
+ <span data-ttu-id="7e2a4-209">Si quita un activo del origen privado, el activo puede seguir estando disponible hasta una hora de la caché; sin embargo, se invalidarán los vínculos al activo en la red CDN en un plazo de 15 minutos a partir de la eliminación del activo.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-209">If you remove an asset from the private origin, the asset may continue to be available for up to an hour from the cache; however, we will invalidate links to the asset in the CDN within 15 minutes of the asset's removal.</span></span>
+ <span data-ttu-id="7e2a4-210">Los tipos de archivo predeterminados que se incluyen en el origen privado son .gif, .ico, .jpeg, .jpg, .js y .png.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-210">The default file types that are included for private origins are .gif, .ico, .jpeg, .jpg, .js, and .png.</span></span> <span data-ttu-id="7e2a4-211">Puede especificar tipos de archivo adicionales.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-211">You can specify additional file types.</span></span>
+ <span data-ttu-id="7e2a4-212">Al igual que con los orígenes públicos, puede configurar una directiva para excluir los activos que se han identificado mediante las clasificaciones de sitio que especifique incluso si usa caracteres comodín para incluir todos los activos dentro de una carpeta o una biblioteca de documentos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-212">Just like with public origins, you can configure a policy to exclude assets that have been identified by site classifications that you specify even if you use wildcards to include all assets within a folder or document library.</span></span>

<span data-ttu-id="7e2a4-213">Para obtener más información sobre por qué usar la red CDN de Office 365, los conceptos generales de CDN y otros CDN de Microsoft que puede usar con el inquilino de Office 365, consulte [redes de entrega de contenido](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-213">For more information about why to use the Office 365 CDN, general CDN concepts, and other Microsoft CDNs you can use with your Office 365 tenant, see [Content Delivery Networks](content-delivery-networks.md).</span></span>

### <a name="default-cdn-origins"></a><span data-ttu-id="7e2a4-214">Orígenes de red CDN predeterminados</span><span class="sxs-lookup"><span data-stu-id="7e2a4-214">Default CDN origins</span></span>

<span data-ttu-id="7e2a4-215">A menos que especifique lo contrario, Office 365 configura algunos orígenes predeterminados cuando habilita la red CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-215">Unless you specify otherwise, Office 365 sets up some default origins for you when you enable the Office 365 CDN.</span></span> <span data-ttu-id="7e2a4-216">Si inicialmente opta por no aprovisionarlos, puede agregar estos orígenes después de completar la instalación.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-216">If you initially opt not to provision them, you can add these origins after you complete setup.</span></span> <span data-ttu-id="7e2a4-217">A menos que comprenda las consecuencias de omitir la configuración de orígenes predeterminados y tenga una razón específica para hacerlo, debería permitir que se creen al habilitar la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-217">Unless you understand the consequences of skipping the setup of default origins and have a specific reason for doing so, you should allow them to be created when you enable the CDN.</span></span>
  
<span data-ttu-id="7e2a4-218">Orígenes de red CDN privados predeterminados:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-218">Default private CDN origins:</span></span>
  
+ <span data-ttu-id="7e2a4-219">\*/userphoto.aspx</span><span class="sxs-lookup"><span data-stu-id="7e2a4-219">\*/userphoto.aspx</span></span>
+ <span data-ttu-id="7e2a4-220">\*/siteassets</span><span class="sxs-lookup"><span data-stu-id="7e2a4-220">\*/siteassets</span></span>

<span data-ttu-id="7e2a4-221">Orígenes de la red CDN pública predeterminada:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-221">Default public CDN origins:</span></span>
  
+ <span data-ttu-id="7e2a4-222">\*/masterpage</span><span class="sxs-lookup"><span data-stu-id="7e2a4-222">\*/masterpage</span></span>
+ <span data-ttu-id="7e2a4-223">\*Biblioteca/Style</span><span class="sxs-lookup"><span data-stu-id="7e2a4-223">\*/style library</span></span>
+ <span data-ttu-id="7e2a4-224">\*/clientsideassets</span><span class="sxs-lookup"><span data-stu-id="7e2a4-224">\*/clientsideassets</span></span>

> [!NOTE]
> <span data-ttu-id="7e2a4-225">_clientsideassets_ es un origen público predeterminado que se agregó al servicio de la red CDN de Office 365 en diciembre de 2017.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-225">_clientsideassets_ is a default public origin that was added to the Office 365 CDN service in December 2017.</span></span> <span data-ttu-id="7e2a4-226">Este origen debe estar presente para que funcionen las soluciones de SharePoint Framework en la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-226">This origin must be present in order for SharePoint Framework solutions in the CDN to work.</span></span> <span data-ttu-id="7e2a4-227">Si habilitó la red CDN de Office 365 antes de diciembre de 2017 o si ha omitido la configuración de los orígenes predeterminados cuando habilitó la red CDN, puede Agregar este origen manualmente.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-227">If you enabled the Office 365 CDN prior to December 2017, or if you skipped setup of default origins when you enabled the CDN, you can manually add this origin.</span></span> <span data-ttu-id="7e2a4-228">Para obtener más información, vea [el elemento Web del lado cliente o la solución de SharePoint Framework no funciona](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-228">For more information, see [My client-side web part or SharePoint Framework solution isn't working](use-office-365-cdn-with-spo.md#my-client-side-web-part-or-sharepoint-framework-solution-isnt-working).</span></span>

<span data-ttu-id="7e2a4-229"><a name="CDNSetupinPShell"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-229"></span></span>
## <a name="set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell"></a><span data-ttu-id="7e2a4-230">Instalar y configurar la red CDN de Office 365 mediante el shell de administración de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-230">Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell</span></span>

<span data-ttu-id="7e2a4-231">Los procedimientos de esta sección requieren que use el shell de administración de SharePoint Online para conectarse a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-231">The procedures in this section require you to use the SharePoint Online Management Shell to connect to SharePoint Online.</span></span> <span data-ttu-id="7e2a4-232">Para obtener instrucciones, consulte [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-232">For instructions, see [Connect to SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps).</span></span>

<span data-ttu-id="7e2a4-233">Siga estos pasos para configurar y configurar la red CDN para hospedar los activos en SharePoint Online mediante el shell de administración de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-233">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the SharePoint Online Management Shell.</span></span>

<details>
  <summary><span data-ttu-id="7e2a4-234">Haga clic para expandir</span><span class="sxs-lookup"><span data-stu-id="7e2a4-234">Click to expand</span></span></summary>

### <a name="enable-your-organization-to-use-the-office-365-cdn"></a><span data-ttu-id="7e2a4-235">Habilitación de la organización para que use la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-235">Enable your organization to use the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-236">Antes de realizar cambios en la configuración de la red CDN del inquilino, debe recuperar el estado actual de la configuración de la red CDN privada en su inquilino de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-236">Before you make changes to the tenant CDN settings, you should retrieve the current status of the private CDN configuration in your Office 365 tenant.</span></span> <span data-ttu-id="7e2a4-237">Conéctese a su inquilino mediante el shell de administración de SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-237">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

``` powershell
Connect-SPOService -Url https://contoso-admin.sharepoint.com
```

<span data-ttu-id="7e2a4-238">Ahora, use el cmdlet **Get-SPOTenantCdnEnabled** para recuperar la configuración de estado de la red CDN del espacio empresarial:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-238">Now use the **Get-SPOTenantCdnEnabled** cmdlet to retrieve the CDN status settings from the tenant:</span></span>

``` powershell
Get-SPOTenantCdnEnabled -CdnType <Public | Private>
```

<span data-ttu-id="7e2a4-239">El estado de la red CDN para el CdnType especificado se mostrará en la pantalla.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-239">The status of the CDN for the specified CdnType will output to the screen.</span></span>

<span data-ttu-id="7e2a4-240">Use el cmdlet **set-SPOTenantCdnEnabled** para permitir que su organización use la red CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-240">Use the **Set-SPOTenantCdnEnabled** cmdlet to enable your organization to use the Office 365 CDN.</span></span> <span data-ttu-id="7e2a4-241">Puede habilitar a su organización para que use orígenes públicos, orígenes privados o ambos a la vez.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-241">You can enable your organization to use public origins, private origins, or both at once.</span></span> <span data-ttu-id="7e2a4-242">También puede configurar la red CDN para omitir la configuración de los orígenes predeterminados al habilitarla.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-242">You can also configure the CDN to skip the setup of default origins when you enable it.</span></span> <span data-ttu-id="7e2a4-243">Siempre puede agregar estos orígenes más adelante, tal y como se describe en este tema.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-243">You can always add these origins later as described in this topic.</span></span>
  
<span data-ttu-id="7e2a4-244">En Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-244">In Windows Powershell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType <Public | Private | Both> -Enable $true
```

<span data-ttu-id="7e2a4-245">Por ejemplo, para permitir que su organización use orígenes públicos y privados, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-245">For example, to enable your organization to use both public and private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="7e2a4-246">Para permitir que su organización use orígenes públicos y privados, pero omitir la configuración de los orígenes predeterminados, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-246">To enable your organization to use both public and private origins but skip setting up the default origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true -NoDefaultOrigins
```

<span data-ttu-id="7e2a4-247">Vea [orígenes de la red CDN predeterminados](use-office-365-cdn-with-spo.md#default-cdn-origins) para obtener información sobre los orígenes que se aprovisionan de forma predeterminada al habilitar la red CDN de Office 365 y el impacto potencial de omitir la configuración de orígenes predeterminados.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-247">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN, and the potential impact of skipping the setup of default origins.</span></span>

<span data-ttu-id="7e2a4-248">Para permitir que su organización use orígenes públicos, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-248">To enable your organization to use public origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $true
```

<span data-ttu-id="7e2a4-249">Para permitir que su organización use orígenes privados, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-249">To enable your organization to use private origins, type the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $true
```

<span data-ttu-id="7e2a4-250">Para obtener más información sobre este cmdlet, vea [set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-250">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span></span>

<span data-ttu-id="7e2a4-251"><a name="Office365CDNforSPOFileType"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-251"></span></span>
### <a name="change-the-list-of-file-types-to-include-in-the-office-365-cdn-optional"></a><span data-ttu-id="7e2a4-252">Cambiar la lista de tipos de archivo que se van a incluir en la red CDN de Office 365 (opcional)</span><span class="sxs-lookup"><span data-stu-id="7e2a4-252">Change the list of file types to include in the Office 365 CDN (Optional)</span></span>

> [!TIP]
> <span data-ttu-id="7e2a4-253">Al definir los tipos de archivo con el cmdlet **set-SPOTenantCdnPolicy** , se sobrescribe la lista definida actualmente.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-253">When you define file types by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="7e2a4-254">Si desea agregar otros tipos de archivo a la lista, use primero el cmdlet para averiguar qué tipos de archivo ya están permitidos e incluirlos en la lista junto con los nuevos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-254">If you want to add additional file types to the list, use the cmdlet first to find out what file types are already allowed and include them in the list along with your new ones.</span></span>
  
<span data-ttu-id="7e2a4-255">Use el cmdlet **set-SPOTenantCdnPolicy** para definir los tipos de archivo estáticos que se pueden hospedar en orígenes públicos y privados en la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-255">Use the **Set-SPOTenantCdnPolicy** cmdlet to define static file types that can be hosted by public and private origins in the CDN.</span></span> <span data-ttu-id="7e2a4-256">De forma predeterminada, se permiten los tipos de activos comunes, por ejemplo,. CSS,. gif,. jpg y. js.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-256">By default, common asset types are allowed, for example .css, .gif, .jpg, and .js.</span></span>

<span data-ttu-id="7e2a4-257">En Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-257">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType IncludeFileExtensions -PolicyValue "<Comma-separated list of file types >"
```

<span data-ttu-id="7e2a4-258">Por ejemplo, para permitir que la red CDN hospede archivos. CSS y. png, tendría que escribir el comando:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-258">For example, to enable the CDN to host .css and .png files, you would enter the command:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType Private -PolicyType IncludeFileExtensions -PolicyValue "CSS,PNG"
```

<span data-ttu-id="7e2a4-259">Para ver qué tipos de archivo están permitidos actualmente en la red CDN, use el cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="7e2a4-259">To see what file types are currently allowed by the CDN, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="7e2a4-260">Para obtener más información acerca de estos cmdlets, consulte [set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) y [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-260">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span></span>

<span data-ttu-id="7e2a4-261"><a name="Office365CDNforSPOSiteClassification"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-261"></span></span>
### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn-optional"></a><span data-ttu-id="7e2a4-262">Cambiar la lista de clasificaciones de sitio que desea excluir de la red CDN de Office 365 (opcional)</span><span class="sxs-lookup"><span data-stu-id="7e2a4-262">Change the list of site classifications you want to exclude from the Office 365 CDN (Optional)</span></span>

> [!TIP]
> <span data-ttu-id="7e2a4-263">Cuando excluya las clasificaciones de sitios con el cmdlet **set-SPOTenantCdnPolicy** , se sobrescribirá la lista definida actualmente.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-263">When you exclude site classifications by using the **Set-SPOTenantCdnPolicy** cmdlet, you overwrite the currently defined list.</span></span> <span data-ttu-id="7e2a4-264">Si quiere excluir clasificaciones de sitios adicionales, use primero el cmdlet para averiguar qué clasificaciones ya se excluyen y, a continuación, agréguelos junto con los nuevos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-264">If you want to exclude additional site classifications, use the cmdlet first to find out what classifications are already excluded and then add them along with your new ones.</span></span>

<span data-ttu-id="7e2a4-265">Use el cmdlet **Set-SPOTenantCdnPolicy** para excluir las clasificaciones de sitio que no desee que estén disponibles en la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-265">Use the **Set-SPOTenantCdnPolicy** cmdlet to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="7e2a4-266">De forma predeterminada, no se excluyen clasificaciones de sitio.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-266">By default, no site classifications are excluded.</span></span>

<span data-ttu-id="7e2a4-267">En Windows PowerShell para SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-267">In Windows PowerShell for SharePoint Online:</span></span>

``` powershell
Set-SPOTenantCdnPolicy -CdnType <Public | Private> -PolicyType ExcludeRestrictedSiteClassifications  -PolicyValue "<Comma-separated list of site classifications >"
```

<span data-ttu-id="7e2a4-268">Para ver qué clasificaciones de sitio están restringidas actualmente, use el cmdlet **Get-SPOTenantCdnPolicies** :</span><span class="sxs-lookup"><span data-stu-id="7e2a4-268">To see what site classifications are currently restricted, use the **Get-SPOTenantCdnPolicies** cmdlet:</span></span>

``` powershell
Get-SPOTenantCdnPolicies -CdnType <Public | Private>
```

<span data-ttu-id="7e2a4-269">Las propiedades que se devolverán son _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ y _ExcludeIfNoScriptDisabled_.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-269">The properties that will be returned are _IncludeFileExtensions_, _ExcludeRestrictedSiteClassifications_ and _ExcludeIfNoScriptDisabled_.</span></span>

<span data-ttu-id="7e2a4-270">La propiedad _IncludeFileExtensions_ contiene la lista de extensiones de archivo que se servirán desde la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-270">The _IncludeFileExtensions_ property contains the list of file extensions that will be served from the CDN.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2a4-271">Las extensiones de archivo predeterminadas son diferentes entre la pública y la privada.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-271">The default file extensions are different between public and private.</span></span>

<span data-ttu-id="7e2a4-272">La propiedad _ExcludeRestrictedSiteClassifications_ contiene las clasificaciones de sitio que desea excluir de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-272">The _ExcludeRestrictedSiteClassifications_ property contains the site classifications that you want to exclude from the CDN.</span></span> <span data-ttu-id="7e2a4-273">Por ejemplo, puede excluir los sitios marcados como **confidenciales** para que el contenido de los sitios con esa clasificación aplicada no se atienda desde la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-273">For example, you can exclude sites marked as **Confidential** so content from sites with that classification applied will not be served from the CDN.</span></span>

<span data-ttu-id="7e2a4-274">La propiedad _ExcludeIfNoScriptDisabled_ excluye el contenido de la red CDN en función de la configuración del atributo _NoScript_ en el nivel de sitio.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-274">The _ExcludeIfNoScriptDisabled_ property excludes content from the CDN based on the site-level _NoScript_ attribute settings.</span></span> <span data-ttu-id="7e2a4-275">De forma predeterminada, el atributo _NoScript_ está establecido en **habilitado** para los sitios _modernos_ y **deshabilitado** para los sitios _clásicos_ .</span><span class="sxs-lookup"><span data-stu-id="7e2a4-275">By default, the _NoScript_ attribute is set to **Enabled** for _Modern_ sites and **Disabled** for _Classic_ sites.</span></span> <span data-ttu-id="7e2a4-276">Esto depende de la configuración del espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-276">This depends on your tenant settings.</span></span>

<span data-ttu-id="7e2a4-277">Para obtener más información acerca de estos cmdlets, consulte [set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) y [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-277">For more information about these cmdlets, see [Set-SPOTenantCdnPolicy](https://technet.microsoft.com/library/mt800839.aspx) and [Get-SPOTenantCdnPolicies](https://technet.microsoft.com/library/mt800838.aspx).</span></span>

<span data-ttu-id="7e2a4-278"><a name="Office365CDNforSPOOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-278"></span></span>
### <a name="add-an-origin-for-your-assets"></a><span data-ttu-id="7e2a4-279">Adición de un origen a los activos</span><span class="sxs-lookup"><span data-stu-id="7e2a4-279">Add an origin for your assets</span></span>

<span data-ttu-id="7e2a4-280">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir un origen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-280">Use the **Add-SPOTenantCdnOrigin** cmdlet to define an origin.</span></span> <span data-ttu-id="7e2a4-281">Puede definir varios orígenes.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-281">You can define multiple origins.</span></span> <span data-ttu-id="7e2a4-282">El origen es una dirección URL que apunta a una biblioteca de SharePoint o la carpeta que contiene los activos que desea que se hospeden mediante la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-282">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="7e2a4-283">Nunca debe poner recursos que contengan información de usuario o que se consideren confidenciales para su organización en un origen público.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-283">You should never place resources that contain user information or are considered sensitive to your organization in a public origin.</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType <Public | Private> -OriginUrl <path>
```

<span data-ttu-id="7e2a4-284">El valor de _path_ es la ruta de acceso relativa a la biblioteca o carpeta que contiene los activos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-284">The value of _path_ is the relative path to the library or folder that contains the assets.</span></span> <span data-ttu-id="7e2a4-285">Puede usar caracteres comodín además de rutas relativas.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-285">You can use wildcards in addition to relative paths.</span></span> <span data-ttu-id="7e2a4-286">Los orígenes admiten caracteres comodín que van precedidos de la dirección URL.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-286">Origins support wildcards prepended to the URL.</span></span> <span data-ttu-id="7e2a4-287">Esto le permite crear orígenes que abarquen varios sitios.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-287">This allows you to create origins that span multiple sites.</span></span> <span data-ttu-id="7e2a4-288">Por ejemplo, para incluir todos los activos de la carpeta MasterPages para todos los sitios como origen público en la red CDN, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-288">For example, to include all of the assets in the masterpages folder for all of your sites as a public origin within the CDN, type the following command:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
```

+ <span data-ttu-id="7e2a4-289">El modificador de comodín**/** \* solo se puede usar al principio de la ruta de acceso y coincidirá con todos los segmentos de dirección URL en la dirección URL especificada.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-289">The wildcard modifier \***/** can only be used at the beginning of the path, and will match all URL segments under the specified URL.</span></span>
+ <span data-ttu-id="7e2a4-290">La ruta de acceso puede apuntar a una biblioteca de documentos, carpeta o sitio.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-290">The path can point to a document library, folder or site.</span></span> <span data-ttu-id="7e2a4-291">Por ejemplo, la ruta de acceso _\*/site1_ coincidirá con todas las bibliotecas de documentos del sitio.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-291">For example, the path _\*/site1_ will match all the document libraries under the site.</span></span>

<span data-ttu-id="7e2a4-292">Puede Agregar un origen con una ruta de acceso relativa específica.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-292">You can add an origin with a specific relative path.</span></span> <span data-ttu-id="7e2a4-293">No se puede Agregar un origen mediante la ruta de acceso completa.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-293">You cannot add an origin using the full path.</span></span>

<span data-ttu-id="7e2a4-294">En este ejemplo se agrega un origen privado de la biblioteca siteassets en un sitio específico:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-294">This example adds a private origin of the siteassets library on a specific site:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="7e2a4-295">En este ejemplo se agrega un origen privado de la carpeta _Folder1_ en la biblioteca de activos del sitio de la colección de sitios:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-295">This example adds a private origin of the _folder1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder1
```

<span data-ttu-id="7e2a4-296">Si hay un espacio en la ruta de acceso, puede poner la ruta entre comillas dobles o reemplazar el espacio con la codificación de la dirección URL %20.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-296">If there is a space in the path, you can either surround the path in double quotes or replace the space with the URL encoding %20.</span></span> <span data-ttu-id="7e2a4-297">En los ejemplos siguientes se agrega un origen privado de la carpeta de la _carpeta 1_ en la biblioteca de activos del sitio de la colección de sitios:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-297">The following examples add a private origin of the _folder 1_ folder in the site collection's site assets library:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/test/siteassets/folder%201
```

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl "sites/test/siteassets/folder 1"
```

<span data-ttu-id="7e2a4-298">Para obtener más información sobre este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-298">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>

> [!NOTE]
> <span data-ttu-id="7e2a4-299">En orígenes privados, los activos que se compartan a partir de un origen deben tener una versión principal publicada antes de que se pueda tener acceso a ellos desde la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-299">In private origins, assets being shared from an origin must have a major version published before they can be accessed from the CDN.</span></span>
  
<span data-ttu-id="7e2a4-300">Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de recursos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-300">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="7e2a4-301">Esto puede tardar hasta 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-301">This can take up to 15 minutes.</span></span>

<span data-ttu-id="7e2a4-302"><a name="ExamplePublicOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-302"></span></span>
### <a name="example-configure-a-public-origin-for-your-master-pages-and-for-your-style-library-for-sharepoint-online"></a><span data-ttu-id="7e2a4-303">Ejemplo: configurar un origen público para las páginas maestras y para la biblioteca de estilos para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-303">Example: Configure a public origin for your master pages and for your style library for SharePoint Online</span></span>

<span data-ttu-id="7e2a4-304">Normalmente, estos orígenes se configuran de forma predeterminada al habilitar la red CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-304">Normally, these origins are set up for you by default when you enable the Office 365 CDN.</span></span> <span data-ttu-id="7e2a4-305">Sin embargo, si desea habilitarlos manualmente, siga estos pasos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-305">However, if you want to enable them manually, follow these steps.</span></span>
  
+ <span data-ttu-id="7e2a4-306">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la biblioteca de estilos como un origen público.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-306">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the style library as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */style%20library
  ```

+ <span data-ttu-id="7e2a4-307">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir las páginas maestras como un origen público.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-307">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the master pages as a public origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */masterpage
  ```

<span data-ttu-id="7e2a4-308">Para obtener más información sobre este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-308">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>

<span data-ttu-id="7e2a4-309">Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de recursos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-309">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="7e2a4-310">Esto puede tardar hasta 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-310">This can take up to 15 minutes.</span></span>

<span data-ttu-id="7e2a4-311"><a name="ExamplePrivateOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-311"></span></span>
### <a name="example-configure-a-private-origin-for-your-site-assets-site-pages-and-publishing-images-for-sharepoint-online"></a><span data-ttu-id="7e2a4-312">Ejemplo: configurar un origen privado para los activos del sitio, las páginas del sitio y las imágenes de publicación para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-312">Example: Configure a private origin for your site assets, site pages, and publishing images for SharePoint Online</span></span>

+ <span data-ttu-id="7e2a4-313">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta activos del sitio como un origen privado.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-313">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site assets folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */siteassets
  ```

+ <span data-ttu-id="7e2a4-314">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta páginas del sitio como un origen privado.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-314">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the site pages folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */sitepages
  ```

+ <span data-ttu-id="7e2a4-315">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir la carpeta de publicación de imágenes como un origen privado.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-315">Use the **Add-SPOTenantCdnOrigin** cmdlet to define the publishing images folder as a private origin.</span></span>

``` powershell
  Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl */publishingimages
  ```

<span data-ttu-id="7e2a4-316">Para obtener más información sobre este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-316">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>

<span data-ttu-id="7e2a4-317">Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de recursos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-317">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="7e2a4-318">Esto puede tardar hasta 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-318">This can take up to 15 minutes.</span></span>

<span data-ttu-id="7e2a4-319"><a name="ExamplePrivateOriginSiteCollection"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-319"></span></span>
### <a name="example-configure-a-private-origin-for-a-site-collection-for-sharepoint-online"></a><span data-ttu-id="7e2a4-320">Ejemplo: configurar un origen privado para una colección de sitios de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-320">Example: Configure a private origin for a site collection for SharePoint Online</span></span>

<span data-ttu-id="7e2a4-321">Use el cmdlet **Add-SPOTenantCdnOrigin** para definir una colección de sitios como un origen privado.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-321">Use the **Add-SPOTenantCdnOrigin** cmdlet to define a site collection as a private origin.</span></span> <span data-ttu-id="7e2a4-322">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-322">For example:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Private -OriginUrl sites/site1/siteassets
```

<span data-ttu-id="7e2a4-323">Para obtener más información sobre este comando y su sintaxis, consulte [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-323">For more information about this command and its syntax, see [Add-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790772.aspx).</span></span>
  
<span data-ttu-id="7e2a4-324">Una vez que haya ejecutado el comando, el sistema sincroniza la configuración en el centro de recursos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-324">Once you've run the command, the system synchronizes the configuration across the datacenter.</span></span> <span data-ttu-id="7e2a4-325">Es posible que vea un mensaje de _configuración pendiente_ que se espera que el inquilino de SharePoint Online se conecte al servicio de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-325">You may see a _Configuration pending_ message which is expected as the SharePoint Online tenant connects to the CDN service.</span></span> <span data-ttu-id="7e2a4-326">Esto puede tardar hasta 15 minutos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-326">This can take up to 15 minutes.</span></span>

<span data-ttu-id="7e2a4-327"><a name="CDNManage"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-327"></span></span>
### <a name="manage-the-office-365-cdn"></a><span data-ttu-id="7e2a4-328">Administrar la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-328">Manage the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-329">Una vez que haya configurado la red CDN, puede realizar cambios en la configuración a medida que actualiza el contenido o según sus necesidades de cambio, tal y como se describe en esta sección.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-329">Once you've set up the CDN, you can make changes to your configuration as you update content or as your needs change, as described in this section.</span></span>
  
<span data-ttu-id="7e2a4-330"><a name="Office365CDNforSPOaddremoveasset"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-330"></span></span>
#### <a name="add-update-or-remove-assets-from-the-office-365-cdn"></a><span data-ttu-id="7e2a4-331">Agregar, actualizar o quitar activos de la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-331">Add, update, or remove assets from the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-332">Una vez que haya completado los pasos de configuración, puede agregar nuevos activos y actualizar o quitar activos existentes cuando lo desee.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-332">Once you've completed the setup steps, you can add new assets, and update or remove existing assets whenever you want.</span></span> <span data-ttu-id="7e2a4-333">Solo tiene que realizar los cambios en los activos de la carpeta o biblioteca de SharePoint que identificó como origen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-333">Just make your changes to the assets in the folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="7e2a4-334">Si agrega un nuevo activo, estará disponible inmediatamente a través de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-334">If you add a new asset, it is available through the CDN immediately.</span></span> <span data-ttu-id="7e2a4-335">Sin embargo, si actualiza el activo, la nueva copia tardará hasta 15 minutos en propagarse y estar disponible en la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-335">However, if you update the asset, it will take up to 15 minutes for the new copy to propagate and become available in the CDN.</span></span>
  
<span data-ttu-id="7e2a4-336">Si necesita recuperar la ubicación del origen, puede usar el cmdlet **Get-SPOTenantCdnOrigins** .</span><span class="sxs-lookup"><span data-stu-id="7e2a4-336">If you need to retrieve the location of the origin, you can use the **Get-SPOTenantCdnOrigins** cmdlet.</span></span> <span data-ttu-id="7e2a4-337">Para obtener información sobre cómo usar este cmdlet, consulte [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/library/mt790770.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-337">For information on how to use this cmdlet, see [Get-SPOTenantCdnOrigins](https://technet.microsoft.com/library/mt790770.aspx).</span></span>

<span data-ttu-id="7e2a4-338"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-338"></span></span>
#### <a name="remove-an-origin-from-the-office-365-cdn"></a><span data-ttu-id="7e2a4-339">Quitar un origen de la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-339">Remove an origin from the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-340">Puede quitar el acceso a una carpeta o biblioteca de SharePoint que haya identificado como origen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-340">You can remove access to a folder or SharePoint library that you identified as an origin.</span></span> <span data-ttu-id="7e2a4-341">Para ello, use el cmdlet **Remove-SPOTenantCdnOrigin** .</span><span class="sxs-lookup"><span data-stu-id="7e2a4-341">To do this, use the **Remove-SPOTenantCdnOrigin** cmdlet.</span></span>

``` powershell
Remove-SPOTenantCdnOrigin -OriginUrl <path> -CdnType <Public | Private | Both>
```

<span data-ttu-id="7e2a4-342">Para obtener información sobre cómo usar este cmdlet, vea [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790761.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-342">For information on how to use this cmdlet, see [Remove-SPOTenantCdnOrigin](https://technet.microsoft.com/library/mt790761.aspx).</span></span>

<span data-ttu-id="7e2a4-343"><a name="Office365CDNforSPORemoveOrigin"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-343"></span></span>
#### <a name="modify-an-origin-in-the-office-365-cdn"></a><span data-ttu-id="7e2a4-344">Modificar un origen en la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-344">Modify an origin in the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-345">No puede modificar el origen que ha creado.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-345">You cannot modify an origin you've created.</span></span> <span data-ttu-id="7e2a4-346">En su lugar, quite el origen y, a continuación, agregue uno nuevo.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-346">Instead, remove the origin and then add a new one.</span></span> <span data-ttu-id="7e2a4-347">Para obtener más información, vea [para quitar un origen de la red CDN de Office 365](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) y [Agregar un origen a los activos](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-347">For more information, see [To remove an origin from the Office 365 CDN](use-office-365-cdn-with-spo.md#Office365CDNforSPORemoveOrigin) and [To add an origin for your assets](use-office-365-cdn-with-spo.md#Office365CDNforSPOOrigin).</span></span>

<span data-ttu-id="7e2a4-348"><a name="Office365CDNforSPODisable"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-348"></span></span>
#### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="7e2a4-349">Deshabilitar la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-349">Disable the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-350">Use el cmdlet **set-SPOTenantCdnEnabled** para deshabilitar la red CDN de su organización.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-350">Use the **Set-SPOTenantCdnEnabled** cmdlet to disable the CDN for your organization.</span></span> <span data-ttu-id="7e2a4-351">Si tiene los orígenes públicos y privados habilitados para la red CDN, debe ejecutar el cmdlet dos veces, como se muestra en los siguientes ejemplos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-351">If you have both the public and private origins enabled for the CDN, you need to run the cmdlet twice as shown in the following examples.</span></span>
  
<span data-ttu-id="7e2a4-352">Para deshabilitar el uso de orígenes públicos en la red CDN, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-352">To disable use of public origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Public -Enable $false
```

<span data-ttu-id="7e2a4-353">Para deshabilitar el uso de los orígenes privados en la red CDN, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-353">To disable use of the private origins in the CDN, enter the following command:</span></span>

``` powershell
Set-SPOTenantCdnEnabled -CdnType Private -Enable $false
```

<span data-ttu-id="7e2a4-354">Para obtener más información sobre este cmdlet, vea [set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-354">For more information about this cmdlet, see [Set-SPOTenantCdnEnabled](https://technet.microsoft.com/library/mt790765.aspx).</span></span>

</details>

<span data-ttu-id="7e2a4-355"><a name="CDNSetupinCLI"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-355"></span></span>
## <a name="set-up-and-configure-the-office-365-cdn-using-the-office-365-cli"></a><span data-ttu-id="7e2a4-356">Instalar y configurar la red CDN de Office 365 con la CLI de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-356">Set up and configure the Office 365 CDN using the Office 365 CLI</span></span>

<span data-ttu-id="7e2a4-357">Los procedimientos de esta sección requieren que tenga instalada la [CLI 365 de Office](https://aka.ms/o365cli).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-357">The procedures in this section require that you have installed the [Office 365 CLI](https://aka.ms/o365cli).</span></span> <span data-ttu-id="7e2a4-358">Después, conéctese al inquilino de SharePoint Online mediante el comando [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-358">Next, connect to your SharePoint Online tenant using the [spo connect](https://pnp.github.io/office365-cli/cmd/spo/connect/) command.</span></span>

<span data-ttu-id="7e2a4-359">Siga estos pasos para configurar y configurar la red CDN para hospedar los activos en SharePoint Online mediante la CLI de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-359">Complete these steps to set up and configure the CDN to host your assets in SharePoint Online using the Office 365 CLI.</span></span>

<details>
  <summary><span data-ttu-id="7e2a4-360">Haga clic para expandir</span><span class="sxs-lookup"><span data-stu-id="7e2a4-360">Click to expand</span></span></summary>

### <a name="enable-the-office-365-cdn"></a><span data-ttu-id="7e2a4-361">Habilitar la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-361">Enable the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-362">Puede administrar el estado de la red CDN de Office 365 en su cuenta empresarial con el comando [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-362">You can manage the state of the Office 365 CDN in your tenant using the [spo cdn set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-set/) command.</span></span>

<span data-ttu-id="7e2a4-363">Para habilitar la red CDN pública de Office 365 en su cuenta empresarial ejecute:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-363">To enable the Office 365 Public CDN in your tenant execute:</span></span>

```sh
spo cdn set --type Public --enabled true
```

<span data-ttu-id="7e2a4-364">Para habilitar la red CDN de Office 365 SharePoint, ejecute:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-364">To enable the Office 365 SharePoint CDN, execute:</span></span>

```sh
spo cdn set --type Private --enabled true
```

#### <a name="view-the-current-status-of-the-office-365-cdn"></a><span data-ttu-id="7e2a4-365">Vea el estado actual de la red CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-365">View the current status of the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-366">Para comprobar si el tipo particular de la red CDN de Office 365 está habilitado o deshabilitado, use el comando [SPO CDN Get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) .</span><span class="sxs-lookup"><span data-stu-id="7e2a4-366">To check if the particular type of Office 365 CDN is enabled or disabled, use the [spo cdn get](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-get/) command.</span></span>

<span data-ttu-id="7e2a4-367">Para comprobar si la red CDN pública de Office 365 está habilitada, ejecute:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-367">To check if the Office 365 Public CDN is enabled, execute:</span></span>

```sh
spo cdn get --type Public
```

### <a name="view-the-office-365-cdn-origins"></a><span data-ttu-id="7e2a4-368">Ver los orígenes de la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-368">View the Office 365 CDN origins</span></span>

<span data-ttu-id="7e2a4-369">Para ver los orígenes configurados actualmente de la red CDN pública de Office 365, ejecute:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-369">To view the currently configured Office 365 Public CDN origins execute:</span></span>

```sh
spo cdn origin list --type Public
```

<span data-ttu-id="7e2a4-370">Vea [orígenes de la red CDN predeterminados](use-office-365-cdn-with-spo.md#default-cdn-origins) para obtener información sobre los orígenes que se aprovisionan de forma predeterminada al habilitar la red CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-370">See [Default CDN origins](use-office-365-cdn-with-spo.md#default-cdn-origins) for information about the origins that are provisioned by default when you enable the Office 365 CDN.</span></span>

### <a name="add-an-office-365-cdn-origin"></a><span data-ttu-id="7e2a4-371">Agregar un origen de red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-371">Add an Office 365 CDN origin</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7e2a4-372">Nunca debe poner recursos considerados confidenciales para su organización en una biblioteca de documentos de SharePoint configurada como un origen público.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-372">You should never place resources that are considered sensitive to your organization in a SharePoint document library configured as a public origin.</span></span>

<span data-ttu-id="7e2a4-373">Use el comando [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) definir un origen de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-373">Use the [spo cdn origin add](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-add/) command to define a CDN origin.</span></span> <span data-ttu-id="7e2a4-374">Puede definir varios orígenes.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-374">You can define multiple origins.</span></span> <span data-ttu-id="7e2a4-375">El origen es una dirección URL que apunta a una biblioteca de SharePoint o la carpeta que contiene los activos que desea que se hospeden mediante la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-375">The origin is a URL that points to a SharePoint library or folder that contains the assets that you want to be hosted by the CDN.</span></span>

```sh
spo cdn origin add --type [Public | Private] --origin <path>
```

<span data-ttu-id="7e2a4-376">Donde `path` es la ruta de acceso relativa a la carpeta que contiene los activos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-376">Where `path` is the relative path to the folder that contains the assets.</span></span> <span data-ttu-id="7e2a4-377">Puede usar caracteres comodín además de rutas relativas.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-377">You can use wildcards in addition to relative paths.</span></span>

<span data-ttu-id="7e2a4-378">Para incluir todos los activos de la **Galería de páginas maestras** de todos los sitios como origen público, ejecute:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-378">To include all assets in the **Master Page Gallery** of all sites as a public origin, execute:</span></span>

```sh
spo cdn origin add --type Public --origin */masterpage
```

<span data-ttu-id="7e2a4-379">Para configurar un origen privado para una colección de sitios específica, ejecute:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-379">To configure a private origin for a specific site collection, execute:</span></span>

```sh
spo cdn origin add --type Private --origin sites/site1/siteassets
```

> [!NOTE]
> <span data-ttu-id="7e2a4-380">Después de agregar un origen de la red CDN, puede tardar hasta 15 minutos para poder recuperar archivos mediante el servicio de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-380">After adding a CDN origin, it might take up to 15 minutes for you to be able to retrieve files via the CDN service.</span></span> <span data-ttu-id="7e2a4-381">Puede comprobar si ya se ha habilitado el origen particular con el comando [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-381">You can verify if the particular origin has already been enabled using the [spo cdn origin list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command.</span></span>

### <a name="remove-an-office-365-cdn-origin"></a><span data-ttu-id="7e2a4-382">Quitar un origen de la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-382">Remove an Office 365 CDN origin</span></span>

<span data-ttu-id="7e2a4-383">Use el comando [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) para eliminar un origen de la red CDN para el tipo de red CDN especificado.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-383">Use the [spo cdn origin remove](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-remove/) command to remove a CDN origin for the specified CDN type.</span></span>

<span data-ttu-id="7e2a4-384">Para quitar un origen público de la configuración de la red CDN, ejecute:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-384">To remove a public origin from the CDN configuration, execute:</span></span>

```sh
spo cdn origin remove --type Public --origin */masterpage
```

> [!NOTE]
> <span data-ttu-id="7e2a4-385">La eliminación de un origen de red CDN no afecta a los archivos almacenados en cualquier biblioteca de documentos que coincida con ese origen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-385">Removing a CDN origin doesn't affect the files stored in any document library matching that origin.</span></span> <span data-ttu-id="7e2a4-386">Si se ha hecho referencia a estos activos mediante su dirección URL de SharePoint, SharePoint cambiará automáticamente de nuevo a la dirección URL original que apunta a la biblioteca de documentos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-386">If these assets have been referenced using their SharePoint URL, SharePoint will automatically switch back to the original URL pointing to the document library.</span></span> <span data-ttu-id="7e2a4-387">Sin embargo, si se ha hecho referencia a los activos mediante una dirección URL de red CDN pública, al quitar el origen se romperá el vínculo y tendrá que cambiarlo manualmente.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-387">If, however, assets have been referenced using a public CDN URL, then removing the origin will break the link and you will need to manually change them.</span></span>

### <a name="modify-an-office-365-cdn-origin"></a><span data-ttu-id="7e2a4-388">Modificación de un origen de red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-388">Modify an Office 365 CDN origin</span></span>

<span data-ttu-id="7e2a4-389">No es posible modificar un origen de la red CDN existente.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-389">It's not possible to modify an existing CDN origin.</span></span> <span data-ttu-id="7e2a4-390">En su lugar, debe eliminar el origen de la red CDN definido anteriormente con el comando `spo cdn origin remove` y agregar uno nuevo con el comando `spo cdn origin add`.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-390">Instead, you should remove the previously defined CDN origin using the `spo cdn origin remove` command and add a new one using the `spo cdn origin add` command.</span></span>

### <a name="change-the-types-of-files-to-include-in-the-office-365-cdn"></a><span data-ttu-id="7e2a4-391">Cambiar los tipos de archivos que se van a incluir en la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-391">Change the types of files to include in the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-392">De forma predeterminada, se incluyen los siguientes tipos de archivo en la red CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf y .woff_.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-392">By default, the following file types are included in the CDN: _.css, .eot, .gif, .ico, .jpeg, .jpg, .js, .map, .png, .svg, .ttf, and .woff_.</span></span> <span data-ttu-id="7e2a4-393">Si tiene que incluir otros tipos de archivo en la red CDN, puede cambiar la configuración de la red CDN con el comando [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-393">If you need to include additional file types in the CDN, you can change the CDN configuration using the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2a4-394">Al cambiar la lista de tipos de archivo, se sobrescribe la lista definida actualmente.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-394">When changing the list of file types, you overwrite the currently defined list.</span></span> <span data-ttu-id="7e2a4-395">Si desea incluir otros tipos de archivo, use el comando [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) para averiguar qué tipos de archivos están configurados en este momento.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-395">If you want to include additional file types, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-origin-list/) command to find out which file types are currently configured.</span></span>

<span data-ttu-id="7e2a4-396">Para agregar el tipo de archivo _JSON_ a la lista predeterminada de tipos de archivo incluidos en la red CDN pública, ejecute:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-396">To add the _JSON_ file type to the default list of file types included in the public CDN, execute:</span></span>

```sh
spo cdn policy set --type Public --policy IncludeFileExtensions --value "CSS,EOT,GIF,ICO,JPEG,JPG,JS,MAP,PNG,SVG,TTF,WOFF,JSON"
```

### <a name="change-the-list-of-site-classifications-you-want-to-exclude-from-the-office-365-cdn"></a><span data-ttu-id="7e2a4-397">Cambiar la lista de clasificaciones de sitio que desea excluir de la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-397">Change the list of site classifications you want to exclude from the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-398">Use el comando [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) para excluir las clasificaciones de sitio que no desee que estén disponibles en la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-398">Use the [spo cdn policy set](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-set/) command to exclude site classifications that you do not want to make available over the CDN.</span></span> <span data-ttu-id="7e2a4-399">De forma predeterminada, no se excluyen clasificaciones de sitio.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-399">By default, no site classifications are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2a4-400">Al cambiar la lista de clasificaciones de sitio excluidas, se sobrescribe la lista definida actualmente.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-400">When changing the list of excluded site classifications, you overwrite the currently defined list.</span></span> <span data-ttu-id="7e2a4-401">Si quiere excluir clasificaciones adicionales, use el comando [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) para averiguar qué clasificaciones están configuradas en este momento.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-401">If you want to exclude additional classifications, first use the [spo cdn policy list](https://pnp.github.io/office365-cli/cmd/spo/cdn/cdn-policy-list/) command to find out which classifications are currently configured.</span></span>

<span data-ttu-id="7e2a4-402">Para excluir los sitios clasificados como _HBI_ desde la red CDN pública, ejecute</span><span class="sxs-lookup"><span data-stu-id="7e2a4-402">To exclude sites classified as _HBI_ from the public CDN, execute</span></span>

```sh
spo cdn policy set --type Public --policy ExcludeRestrictedSiteClassifications --value "HBI"
```

### <a name="disable-the-office-365-cdn"></a><span data-ttu-id="7e2a4-403">Deshabilitar la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-403">Disable the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-404">Para deshabilitar la red CDN de Office 365, use el comando `spo cdn set`, por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-404">To disable the Office 365 CDN use the `spo cdn set` command, for example:</span></span>

```sh
spo cdn set --type Public --enabled false
```

</details>

## <a name="using-your-cdn-assets"></a><span data-ttu-id="7e2a4-405">Uso de los activos de la red CDN</span><span class="sxs-lookup"><span data-stu-id="7e2a4-405">Using your CDN assets</span></span>

<span data-ttu-id="7e2a4-406">Ahora que ha habilitado la red CDN y las directivas y los orígenes configurados, puede empezar a usar los activos de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-406">Now that you have enabled the CDN and configured origins and policies, you can begin using your CDN assets.</span></span>

<span data-ttu-id="7e2a4-407">Esta sección le ayudará a usar direcciones URL de la red CDN en el contenido y las páginas de SharePoint para que SharePoint redirija las solicitudes de activos en los orígenes públicos y privados a la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-407">This section will help you understand how to use CDN URLs in your SharePoint pages and content so that SharePoint redirects requests for assets in both public and private origins to the CDN.</span></span>

+ [<span data-ttu-id="7e2a4-408">Actualización de vínculos a activos de la red CDN</span><span class="sxs-lookup"><span data-stu-id="7e2a4-408">Updating links to CDN assets</span></span>](use-office-365-cdn-with-spo.md#updating-links-to-cdn-assets)
+ [<span data-ttu-id="7e2a4-409">Usar activos en orígenes públicos</span><span class="sxs-lookup"><span data-stu-id="7e2a4-409">Using assets in public origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-public-origins)
+ [<span data-ttu-id="7e2a4-410">Uso de activos en orígenes privados</span><span class="sxs-lookup"><span data-stu-id="7e2a4-410">Using assets in private origins</span></span>](use-office-365-cdn-with-spo.md#using-assets-in-private-origins)

<span data-ttu-id="7e2a4-411">Para obtener información sobre cómo usar la red CDN para hospedar elementos Web del lado cliente, vea el tema [hospedar un elemento Web del lado cliente de la red CDN de Office 365 (parte 4 de Hello World)](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-411">For information on how to use the CDN for hosting client-side web parts, see the topic [Host your client-side web part from Office 365 CDN (Hello World part 4)](https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn).</span></span>

### <a name="updating-links-to-cdn-assets"></a><span data-ttu-id="7e2a4-412">Actualización de vínculos a activos de la red CDN</span><span class="sxs-lookup"><span data-stu-id="7e2a4-412">Updating links to CDN assets</span></span>

<span data-ttu-id="7e2a4-413">Para usar activos que ha agregado a un origen, solo tiene que actualizar los vínculos al archivo original con la ruta de acceso al archivo en el origen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-413">To use assets that you have added to an origin, you simply update links to the original file with the path to the file in the origin.</span></span>

+ <span data-ttu-id="7e2a4-414">Edite la página o el contenido que contiene vínculos a los activos que ha agregado a un origen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-414">Edit the page or content that contains links to assets you have added to an origin.</span></span> <span data-ttu-id="7e2a4-415">También puede usar uno de varios métodos para buscar y reemplazar vínculos globalmente en un sitio o una colección de sitios si desea actualizar el vínculo a un activo determinado en cualquier lugar en el que aparezca.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-415">You can also use one of several methods to globally search and replace links across an enter site or site collection if you want to update the link to a given asset everywhere it appears.</span></span>
+ <span data-ttu-id="7e2a4-416">Para cada vínculo a un activo en un origen, reemplace la ruta de acceso por la ruta de acceso al archivo en el origen de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-416">For each link to an asset in an origin, replace the path with the path to the file in the CDN origin.</span></span> <span data-ttu-id="7e2a4-417">Puede usar rutas relativas.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-417">You can use relative paths.</span></span>
+ <span data-ttu-id="7e2a4-418">Guarde la página o el contenido.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-418">Save the page or content.</span></span>

<span data-ttu-id="7e2a4-419">Por ejemplo, considere la imagen _/site/SiteAssets/images/Image.png_, que ha copiado a la carpeta de la biblioteca de documentos _/site/CDN_origins/Public/_.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-419">For example, consider the image _/site/SiteAssets/images/image.png_, which you have copied to the document library folder _/site/CDN_origins/public/_.</span></span> <span data-ttu-id="7e2a4-420">Para usar el recurso de red CDN, reemplace la ruta de acceso original a la ubicación del archivo de imagen por la ruta de acceso al origen para que la nueva dirección URL _/site/CDN_origins/Public/Image.png_.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-420">To use the CDN asset, replace the original path to the image file location with the path to the origin to make the new URL _/site/CDN_origins/public/image.png_.</span></span>

<span data-ttu-id="7e2a4-421">Si desea usar la dirección URL completa para el activo en lugar de una ruta de acceso relativa, construya el siguiente vínculo:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-421">If you want to use the full URL to the asset instead of a relative path, construct the link like so:</span></span>

`https://<TenantHostName>.sharepoint.com/sites/site/CDN_origins/public/image.png`

> [!NOTE]
> <span data-ttu-id="7e2a4-422">En general, no se deben codificar las direcciones URL directamente en los activos en la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-422">In general, you should not hardcode URLs directly to assets in the CDN.</span></span> <span data-ttu-id="7e2a4-423">Sin embargo, si es necesario, puede construir manualmente direcciones URL para activos en los orígenes públicos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-423">However, you can manually construct URLs for assets in public origins if needed.</span></span> <span data-ttu-id="7e2a4-424">Para obtener más información, vea [direcciones URL de la red CDN de Hardcoding para activos públicos](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-424">For more information, see [Hardcoding CDN URLs for public assets](use-office-365-cdn-with-spo.md#hardcoding-cdn-urls-for-public-assets).</span></span>

<span data-ttu-id="7e2a4-425">Para obtener información sobre cómo comprobar que los activos se atienden desde la red CDN, vea [¿Cómo puedo confirmar que la red CDN atiende los activos?](use-office-365-cdn-with-spo.md#CDNConfirm) en la sección [solución de problemas de la red cdn de Office 365](use-office-365-cdn-with-spo.md#CDNTroubleshooting) .</span><span class="sxs-lookup"><span data-stu-id="7e2a4-425">To learn about how to verify that assets are being served from the CDN, see [How do I confirm that assets are being served by the CDN?](use-office-365-cdn-with-spo.md#CDNConfirm) in the [Troubleshooting the Office 365 CDN](use-office-365-cdn-with-spo.md#CDNTroubleshooting) section.</span></span>

### <a name="using-assets-in-public-origins"></a><span data-ttu-id="7e2a4-426">Usar activos en orígenes públicos</span><span class="sxs-lookup"><span data-stu-id="7e2a4-426">Using assets in public origins</span></span>

<span data-ttu-id="7e2a4-427">La **característica de publicación** de SharePoint Online reescribe automáticamente direcciones URL de activos almacenados en orígenes públicos en sus equivalentes de CDN para que los activos se puedan atender desde el servicio de la red CDN en lugar de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-427">The **Publishing feature** in SharePoint Online automatically rewrites URLs of assets stored in public origins to their CDN equivalents so that assets are served from the CDN service instead of SharePoint.</span></span>

<span data-ttu-id="7e2a4-428">Si su origen está en un sitio con la característica de publicación habilitada, y los activos que desea descargar en la red CDN están en una de las siguientes categorías, SharePoint rescribirá automáticamente las direcciones URL de los activos en el origen, siempre que el activo no se haya excluido por una CDN.  normativa.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-428">If your origin is in a site with the Publishing feature enabled, and the assets you want to offload to the CDN are in one of the following categories, SharePoint will automatically rewrite URLs for assets in the origin, provided that the asset has not been excluded by a CDN policy.</span></span>

<span data-ttu-id="7e2a4-429">A continuación, se muestra información general sobre los vínculos que la característica de publicación de SharePoint reescribe automáticamente:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-429">The following is an overview of which links are automatically rewritten by the SharePoint Publishing feature:</span></span>

+ <span data-ttu-id="7e2a4-430">URL de IMG/LINK/CSS en respuestas de HTML de página de publicación clásica</span><span class="sxs-lookup"><span data-stu-id="7e2a4-430">IMG/LINK/CSS URLs in classic publishing page HTML responses</span></span>
  + <span data-ttu-id="7e2a4-431">Esto incluye imágenes que han agregado autores en el contenido HTML de una página</span><span class="sxs-lookup"><span data-stu-id="7e2a4-431">This includes images added by authors within the HTML content of a page</span></span>
+ <span data-ttu-id="7e2a4-432">URL de las imágenes del elemento web de presentación de la biblioteca de imágenes</span><span class="sxs-lookup"><span data-stu-id="7e2a4-432">Picture Library SlideShow webpart image URLs</span></span>
+ <span data-ttu-id="7e2a4-433">Campos de imagen de los resultados de la API de REST SPList (RenderListDataAsStream)</span><span class="sxs-lookup"><span data-stu-id="7e2a4-433">Image fields in SPList REST API (RenderListDataAsStream) results</span></span>
  + <span data-ttu-id="7e2a4-434">Use la nueva propiedad _ImageFieldsToTryRewriteToCdnUrls_ para proporcionar una lista de campos separados por comas.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-434">Use the new property _ImageFieldsToTryRewriteToCdnUrls_ to provide a comma separated list of fields</span></span>
  + <span data-ttu-id="7e2a4-435">Admite campos de hipervínculos y campos de PublishingImage</span><span class="sxs-lookup"><span data-stu-id="7e2a4-435">Supports hyperlink fields and PublishingImage fields</span></span>
+ <span data-ttu-id="7e2a4-436">Representaciones de imágenes de SharePoint</span><span class="sxs-lookup"><span data-stu-id="7e2a4-436">SharePoint image renditions</span></span>

<span data-ttu-id="7e2a4-437">El siguiente diagrama ilustra el flujo de trabajo cuando SharePoint recibe una solicitud para una página que contiene activos de un origen público.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-437">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a public origin.</span></span>

<span data-ttu-id="7e2a4-438">![Diagrama de flujo de trabajo: recuperar activos de la red CDN de Office 365 desde un origen público](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Flujo de trabajo: recuperación de recursos de la red CDN de Office 365 desde un origen público")</span><span class="sxs-lookup"><span data-stu-id="7e2a4-438">![Workflow diagram: Retrieving Office 365 CDN assets from a public origin](media/O365-CDN/o365-cdn-public-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a public origin")</span></span>

> [!TIP]
> <span data-ttu-id="7e2a4-439">Si desea deshabilitar la reescritura automática de direcciones URL específicas en una página, puede desproteger la página y agregar el parámetro de la cadena de consulta. \*\* NoAutoReWrites = true\*\* al final de cada vínculo que desee deshabilitar.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-439">If you want to disable auto-rewriting for specific URLs on a page, you can check out the page and add the query string parameter **?NoAutoReWrites=true** to the end of each link you want to disable.</span></span>

#### <a name="hardcoding-cdn-urls-for-public-assets"></a><span data-ttu-id="7e2a4-440">Direcciones URL de CDN de Hardcoding para activos públicos</span><span class="sxs-lookup"><span data-stu-id="7e2a4-440">Hardcoding CDN URLs for public assets</span></span>

<span data-ttu-id="7e2a4-441">Si la característica de _publicación_ no está habilitada para un origen público o el activo no es uno de los tipos de vínculos que admite la característica de reescritura automática del servicio de red CDN, puede crear manualmente las direcciones URL en la ubicación de la red CDN de los activos y usar estas direcciones URL en el contenido.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-441">If the _Publishing_ feature is not enabled for a public origin, or the asset is not one of the link types supported by the auto-rewrite feature of the CDN service, you can manually construct URLs to the CDN location of the assets and use these URLs in your content.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2a4-442">No puede codificar direcciones URL de CDN con activos de un origen privado porque el token de acceso necesario que forma la última sección de la dirección URL se genera en el momento en que se solicita el recurso.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-442">You cannot hardcode CDN URLs to assets in a private origin because the required access token that forms the last section of the URL is generated at the time the resource is requested.</span></span>

<span data-ttu-id="7e2a4-443">Para los activos de la red CDN pública, el formato de la dirección URL será similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-443">For public CDN assets, the URL format will look like the following:</span></span>

``` html
https://publiccdn.sharepointonline.com/<TenantHostName>/sites/site/library/asset.png
```

<span data-ttu-id="7e2a4-444">Reemplace **TenantHostName** por el nombre del espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-444">Replace **TenantHostName** with your tenant name.</span></span> <span data-ttu-id="7e2a4-445">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-445">Example:</span></span>

``` html
https://publiccdn.sharepointonline.com/contoso.sharepoint.com/sites/site/library/asset.png
```

### <a name="using-assets-in-private-origins"></a><span data-ttu-id="7e2a4-446">Uso de activos en orígenes privados</span><span class="sxs-lookup"><span data-stu-id="7e2a4-446">Using assets in private origins</span></span>

<span data-ttu-id="7e2a4-447">No se necesita ninguna configuración adicional para usar activos en orígenes privados.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-447">No additional configuration is required to use assets in private origins.</span></span> <span data-ttu-id="7e2a4-448">SharePoint Online reescribe automáticamente direcciones URL para activos en orígenes privados para que las solicitudes de dichos activos siempre se atiendan desde la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-448">SharePoint Online automatically rewrites URLs for assets in private origins so requests for those assets will always be served from the CDN.</span></span> <span data-ttu-id="7e2a4-449">No puede crear manualmente direcciones URL a activos de CDN en orígenes privados porque estas direcciones contienen tokens que SharePoint Online debe generar automáticamente en el momento en que se solicita el activo.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-449">You cannot manually build URLs to CDN assets in private origins because these URLs contain tokens that must be auto-generated by SharePoint Online at the time the asset is requested.</span></span>

<span data-ttu-id="7e2a4-450">El acceso a activos en orígenes privados está protegido por tokens generados dinámicamente en función de los permisos de usuario para el origen, con las advertencias descritas en las siguientes secciones.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-450">Access to assets in private origins is protected by dynamically generated tokens based on user permissions to the origin, with the caveats described in the following sections.</span></span> <span data-ttu-id="7e2a4-451">Los usuarios deben tener al menos acceso de **lectura** a los orígenes para que la red CDN represente contenido.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-451">Users must have at least **read** access to the origins for the CDN to render content.</span></span>

<span data-ttu-id="7e2a4-452">El siguiente diagrama ilustra el flujo de trabajo cuando SharePoint recibe una solicitud para una página que contiene activos de un origen privado.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-452">The following diagram illustrates the workflow when SharePoint receives a request for a page containing assets from a private origin.</span></span>

<span data-ttu-id="7e2a4-453">![Diagrama de flujo de trabajo: recuperar activos de la red CDN de Office 365 de un origen privado](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Flujo de trabajo: recuperar activos de la red CDN de Office 365 de un origen privado")</span><span class="sxs-lookup"><span data-stu-id="7e2a4-453">![Workflow diagram: Retrieving Office 365 CDN assets from a private origin](media/O365-CDN/o365-cdn-private-steps-transparent.svg "Workflow: Retrieving Office 365 CDN assets from a private origin")</span></span>

#### <a name="token-based-authorization-in-private-origins"></a><span data-ttu-id="7e2a4-454">Autorización basada en token en orígenes privados</span><span class="sxs-lookup"><span data-stu-id="7e2a4-454">Token-based authorization in private origins</span></span>

<span data-ttu-id="7e2a4-455">El acceso a los activos de orígenes privados en la red CDN de Office 365 se concede mediante tokens generados por SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-455">Access to assets in private origins in the Office 365 CDN is granted by tokens generated by SharePoint Online.</span></span> <span data-ttu-id="7e2a4-456">Los usuarios que ya tienen permiso para obtener acceso a la carpeta o a la biblioteca designada por el origen reciben automáticamente tokens que permiten al usuario tener acceso al archivo en función de su nivel de permisos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-456">Users who already have permission to access to the folder or library designated by the origin are automatically granted tokens that permit the user to access the file based on their permission level.</span></span> <span data-ttu-id="7e2a4-457">Estos tokens de acceso son válidos durante 30 a 90 minutos después de que se generen para ayudar a evitar ataques de reproducción de tokens.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-457">These access tokens are valid for 30 to 90 minutes after they are generated to help prevent token replay attacks.</span></span>

<span data-ttu-id="7e2a4-458">Una vez que se genera el token de acceso, SharePoint Online devuelve un URI personalizado al cliente que contiene dos parámetros de autorización _comer_ (token de autorización perimetral) y _OAT_ (token Authorization Authorization).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-458">Once the access token is generated, SharePoint Online returns a custom URI to the client containing two authorization parameters _eat_ (edge authorization token) and _oat_ (origin authorization token).</span></span> <span data-ttu-id="7e2a4-459">La estructura de cada token es _< ' tiempo de expiración en formato de hora en tiempo de duración ' >__< >' firma segura ' _.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-459">The structure of each token is _<'expiration time in Epoch time format'>__<'secure signature'>_.</span></span> <span data-ttu-id="7e2a4-460">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-460">For example:</span></span>

``` html
https://privatecdn.sharepointonline.com/contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg?eat=1486154359_cc59042c5c55c90b26a2775323c7c8112718431228fe84d568a3795a63912840&oat=1486154359_7d73c2e3ba4b7b1f97242332900616db0d4ffb04312
```

> [!NOTE]
> <span data-ttu-id="7e2a4-461">Cualquier persona que posea el token puede tener acceso al recurso en la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-461">Anyone in possession of the token can access the resource in the CDN.</span></span> <span data-ttu-id="7e2a4-462">Sin embargo, las direcciones URL que contienen estos tokens de acceso solo se comparten a través de HTTPS, por lo que, a menos que un usuario final comparta explícitamente la dirección URL antes de que expire el token, el activo no será accesible para los usuarios no autorizados.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-462">However, URLs containing these access tokens are only shared over HTTPS, so unless the URL is explicitly shared by an end user before the token expires, the asset won’t be accessible to unauthorized users.</span></span>

#### <a name="item-level-permissions-are-not-supported-for-assets-in-private-origins"></a><span data-ttu-id="7e2a4-463">No se admiten permisos de nivel de elemento para activos en orígenes privados</span><span class="sxs-lookup"><span data-stu-id="7e2a4-463">Item-level permissions are not supported for assets in private origins</span></span>

<span data-ttu-id="7e2a4-464">Es importante tener en cuenta que SharePoint Online no admite permisos de nivel de elemento para activos en orígenes privados.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-464">It is important to note that SharePoint Online does not support item-level permissions for assets in private origins.</span></span> <span data-ttu-id="7e2a4-465">Por ejemplo, para un archivo que se `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`encuentra en, los usuarios tienen acceso efectivo al archivo teniendo en cuenta las siguientes condiciones:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-465">For example, for a file located at `https://contoso.sharepoint.com/sites/site1/library1/folder1/image1.jpg`, users have effective access to the file given the following conditions:</span></span>

|<span data-ttu-id="7e2a4-466">Usuario</span><span class="sxs-lookup"><span data-stu-id="7e2a4-466">User</span></span>  |<span data-ttu-id="7e2a4-467">Permisos</span><span class="sxs-lookup"><span data-stu-id="7e2a4-467">Permissions</span></span>  |<span data-ttu-id="7e2a4-468">Acceso efectivo</span><span class="sxs-lookup"><span data-stu-id="7e2a4-468">Effective access</span></span>  |
|---------|---------|---------|
|<span data-ttu-id="7e2a4-469">Usuario 1</span><span class="sxs-lookup"><span data-stu-id="7e2a4-469">User 1</span></span>     |<span data-ttu-id="7e2a4-470">Tiene acceso a la carpeta1</span><span class="sxs-lookup"><span data-stu-id="7e2a4-470">Has access to folder1</span></span>         |<span data-ttu-id="7e2a4-471">Puede tener acceso a image1. jpg desde la red CDN</span><span class="sxs-lookup"><span data-stu-id="7e2a4-471">Can access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="7e2a4-472">Usuario 2</span><span class="sxs-lookup"><span data-stu-id="7e2a4-472">User 2</span></span>     |<span data-ttu-id="7e2a4-473">No tiene acceso a la carpeta1</span><span class="sxs-lookup"><span data-stu-id="7e2a4-473">Does not have access to folder1</span></span>         |<span data-ttu-id="7e2a4-474">No se puede tener acceso a image1. jpg desde la red CDN</span><span class="sxs-lookup"><span data-stu-id="7e2a4-474">Cannot access image1.jpg from the CDN</span></span>         |
|<span data-ttu-id="7e2a4-475">Usuario 3</span><span class="sxs-lookup"><span data-stu-id="7e2a4-475">User 3</span></span>     |<span data-ttu-id="7e2a4-476">No tiene acceso a la carpeta1, pero se le ha concedido el permiso explícito para obtener acceso a image1. jpg en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-476">Does not have access to folder1, but is granted explicit permission to access image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="7e2a4-477">Puede tener acceso al elemento image1. jpg directamente desde SharePoint Online, pero no desde la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-477">Can access the asset image1.jpg directly from SharePoint Online, but not from the CDN</span></span>         |
|<span data-ttu-id="7e2a4-478">Usuario 4</span><span class="sxs-lookup"><span data-stu-id="7e2a4-478">User 4</span></span>     |<span data-ttu-id="7e2a4-479">Tiene acceso a la carpeta1, pero se ha denegado explícitamente el acceso a image1. jpg en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-479">Has access to folder1, but has been explicitly denied access to image1.jpg in SharePoint Online</span></span>         |<span data-ttu-id="7e2a4-480">No se puede obtener acceso al activo desde SharePoint Online, pero puede tener acceso al recurso desde la red CDN a pesar de que se le deniegue el acceso al archivo en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-480">Cannot access the asset from SharePoint Online, but can access the asset from the CDN despite being denied access to the file in SharePoint Online</span></span>         |

<span data-ttu-id="7e2a4-481"><a name="CDNTroubleshooting"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-481"></span></span>
## <a name="troubleshooting-the-office-365-cdn"></a><span data-ttu-id="7e2a4-482">Solución de problemas de la red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-482">Troubleshooting the Office 365 CDN</span></span>

<span data-ttu-id="7e2a4-483"><a name="CDNConfirm"> </a></span><span class="sxs-lookup"><span data-stu-id="7e2a4-483"></span></span>
### <a name="how-do-i-confirm-that-assets-are-being-served-by-the-cdn"></a><span data-ttu-id="7e2a4-484">¿Cómo puedo confirmar que la red CDN atiende los activos?</span><span class="sxs-lookup"><span data-stu-id="7e2a4-484">How do I confirm that assets are being served by the CDN?</span></span>

<span data-ttu-id="7e2a4-485">Una vez que haya agregado los vínculos a los activos de la red CDN a una página, puede confirmar que el recurso se atiende desde la red CDN; para ello, haga clic en la imagen una vez representada y revisar la dirección URL de la imagen.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-485">Once you have added links to CDN assets to a page, you can confirm that the asset is being served from the CDN by browsing to the page, right clicking on the image once it has rendered and reviewing the image URL.</span></span>

<span data-ttu-id="7e2a4-486">También puede usar las herramientas de desarrollo del explorador para ver la dirección URL de cada activo en una página o usar una herramienta de seguimiento de red de terceros.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-486">You can also use your browser's developer tools to view the URL for each asset on a page, or use a third party network trace tool.</span></span>

> [!NOTE]
> <span data-ttu-id="7e2a4-487">Si usa una herramienta de red como Fiddler para probar los activos fuera de la representación del activo desde una página de SharePoint, debe agregar manualmente el encabezado de referencia "referrer: `https://yourdomain.sharepoint.com`" a la solicitud GET, donde la dirección URL es la dirección URL raíz del inquilino de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-487">If you use a network tool such as Fiddler to test your assets outside of rendering the asset from a SharePoint page, you must manually add the referrer header “Referrer: `https://yourdomain.sharepoint.com`” to the GET request where the URL is the root URL of your SharePoint Online tenant.</span></span>

<span data-ttu-id="7e2a4-488">No se pueden probar direcciones URL de CDN directamente en un explorador web porque debe haber un sitio de referencia que provenga de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-488">You cannot test CDN URLs directly in a web browser because you must have a referrer coming from SharePoint Online.</span></span> <span data-ttu-id="7e2a4-489">Sin embargo, si agrega la dirección URL de los activos de la red CDN a una página de SharePoint y, a continuación, abre la página en un explorador, verá el activo de la red CDN representado en la página.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-489">However, if you add the CDN asset URL to a SharePoint page and then open the page in a browser, you will see the CDN asset rendered on the page.</span></span>

<span data-ttu-id="7e2a4-490">Para obtener más información sobre el uso de las herramientas de desarrollo en el explorador de Microsoft Edge, consulte [herramientas de desarrollo de Microsoft Edge](https://docs.microsoft.com/microsoft-edge/devtools-guide).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-490">For more information on using the developer tools in the Microsoft Edge browser, see [Microsoft Edge Developer Tools](https://docs.microsoft.com/microsoft-edge/devtools-guide).</span></span>

<span data-ttu-id="7e2a4-491">Para ver un vídeo corto hospedado en el [canal de YouTube de procedimientos y patrones para desarrolladores de SharePoint](https://aka.ms/sppnp-videos) que muestra cómo comprobar que su red CDN está funcionando, consulte [comprobar el uso de la red CDN y garantizar la conectividad de red óptima](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).</span><span class="sxs-lookup"><span data-stu-id="7e2a4-491">To watch a short video hosted in the [SharePoint Developer Patterns and Practices YouTube channel](https://aka.ms/sppnp-videos) demonstrating how to verify that your CDN is working, please see [Verifying your CDN usage and ensuring optimal network connectivity](https://www.youtube.com/watch?v=ClCtBAtGjE8&list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA&index=5).</span></span>

### <a name="why-are-assets-from-a-new-origin-unavailable"></a><span data-ttu-id="7e2a4-492">¿Por qué no están disponibles los activos de un nuevo origen?</span><span class="sxs-lookup"><span data-stu-id="7e2a4-492">Why are assets from a new origin unavailable?</span></span>
<span data-ttu-id="7e2a4-493">Los activos en nuevos orígenes no estarán disponibles para su uso inmediatamente, ya que el registro se propagará a través de la red CDN y se cargarán los activos del origen al almacenamiento de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-493">Assets in new origins will not immediately be available for use, as it takes time for the registration to propagate through the CDN and for the assets to be uploaded from the origin to CDN storage.</span></span> <span data-ttu-id="7e2a4-494">El tiempo necesario para que los activos estén disponibles en la red CDN depende de cuántos activos y el tamaño de los archivos.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-494">The time required for assets to be available in the CDN depends on how many assets and the files sizes.</span></span>

### <a name="my-client-side-web-part-or-sharepoint-framework-solution-isnt-working"></a><span data-ttu-id="7e2a4-495">Mi elemento Web del lado cliente o solución de SharePoint Framework no funciona</span><span class="sxs-lookup"><span data-stu-id="7e2a4-495">My client-side web part or SharePoint Framework solution isn't working</span></span>

<span data-ttu-id="7e2a4-496">Cuando se habilita la red CDN de Office 365 para orígenes públicos, el servicio de red CDN crea automáticamente estos orígenes predeterminados:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-496">When you enable the Office 365 CDN for public origins, the CDN service automatically creates these default origins:</span></span>

+ <span data-ttu-id="7e2a4-497">\*/MASTERPAGE</span><span class="sxs-lookup"><span data-stu-id="7e2a4-497">\*/MASTERPAGE</span></span>
+ <span data-ttu-id="7e2a4-498">\* BIBLIOTECA/STYLE</span><span class="sxs-lookup"><span data-stu-id="7e2a4-498">\*/STYLE LIBRARY</span></span>
+ <span data-ttu-id="7e2a4-499">\*/CLIENTSIDEASSETS</span><span class="sxs-lookup"><span data-stu-id="7e2a4-499">\*/CLIENTSIDEASSETS</span></span>

<span data-ttu-id="7e2a4-500">Si falta el origen \*/clientsideassets, se producirá un error en las soluciones de SharePoint Framework y no se generará ningún mensaje de advertencia ni de error.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-500">If the \*/clientsideassets origin is missing, SharePoint Framework solutions will fail, and no warning or error messages are generated.</span></span> <span data-ttu-id="7e2a4-501">Este origen puede faltar porque la red CDN se habilitó con el parámetro _-NoDefaultOrigins_ establecido en **$true**o porque el origen se eliminó manualmente.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-501">This origin may be missing either because the CDN was enabled with the _-NoDefaultOrigins_ parameter set to **$true**, or because the origin was manually deleted.</span></span>

<span data-ttu-id="7e2a4-502">Puede comprobar si el origen \*/CLIENTSIDEASSETS está presente con el siguiente comando de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-502">You can check to see if the \*/CLIENTSIDEASSETS origin is present with the following PowerShell command:</span></span>

``` powershell
Get-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="7e2a4-503">O bien, puede consultar con la CLI de Office 365:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-503">Or you can check with the Office 365 CLI:</span></span>

``` powershell
spo cdn origin list
```

<span data-ttu-id="7e2a4-504">Para agregar el origen en PowerShell:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-504">To add the origin in PowerShell:</span></span>

``` powershell
Add-SPOTenantCdnOrigin -CdnType Public -OriginUrl */CLIENTSIDEASSETS
```

<span data-ttu-id="7e2a4-505">Para agregar el origen en la CLI de Office 365:</span><span class="sxs-lookup"><span data-stu-id="7e2a4-505">To add the origin in the Office 365 CLI:</span></span>

``` powershell
spo cdn origin add --origin */CLIENTSIDEASSETS
```

### <a name="what-powershell-modules-and-cli-shells-do-i-need-to-work-with-the-office-365-cdn"></a><span data-ttu-id="7e2a4-506">¿Qué módulos de PowerShell y shells de CLI necesito para trabajar con la red CDN de Office 365?</span><span class="sxs-lookup"><span data-stu-id="7e2a4-506">What PowerShell modules and CLI shells do I need to work with the Office 365 CDN?</span></span>

<span data-ttu-id="7e2a4-507">Puede elegir trabajar con la red CDN de Office 365 usando el módulo de PowerShell de **SharePoint Online Management Shell** o la **CLI de Office 365**.</span><span class="sxs-lookup"><span data-stu-id="7e2a4-507">You can choose to work with the Office 365 CDN using either the **SharePoint Online Management Shell** PowerShell module or the **Office 365 CLI**.</span></span>

+ [<span data-ttu-id="7e2a4-508">Introducción al shell de administración de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="7e2a4-508">Getting started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online?view=sharepoint-ps)
+ [<span data-ttu-id="7e2a4-509">Instalar Office 365 CLI</span><span class="sxs-lookup"><span data-stu-id="7e2a4-509">Installing the Office 365 CLI</span></span>](https://pnp.github.io/office365-cli/user-guide/installing-cli/)

## <a name="see-also"></a><span data-ttu-id="7e2a4-510">Vea también</span><span class="sxs-lookup"><span data-stu-id="7e2a4-510">See also</span></span>

[<span data-ttu-id="7e2a4-511">Redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="7e2a4-511">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="7e2a4-512">Planeamiento de red y ajuste del rendimiento para Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-512">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="7e2a4-513">Series de rendimiento de SharePoint: serie de vídeos de red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="7e2a4-513">SharePoint Performance Series - Office 365 CDN video series</span></span>](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
