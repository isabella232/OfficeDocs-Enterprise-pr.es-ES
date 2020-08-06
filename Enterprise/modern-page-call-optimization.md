---
title: Optimizar las llamadas de página en las páginas de sitios de publicación modernos y clásicos de SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 03/11/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Obtenga información sobre cómo optimizar las páginas de sitios de publicación modernos y clásicos en SharePoint Online limitando el número de llamadas a los puntos de conexión de servicios de SharePoint Online.
ms.openlocfilehash: 063cf6d8c14f139f90e8bb19ca7ccd0833fc36ec
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571143"
---
# <a name="optimize-page-calls-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="24bde-103">Optimizar las llamadas de página en las páginas de sitios de publicación modernos y clásicos de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="24bde-103">Optimize page calls in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="24bde-104">Los sitios de publicación de SharePoint Online modernos y clásicos contienen vínculos que cargan datos de (o hacen llamadas a) características de SharePoint y CDN.</span><span class="sxs-lookup"><span data-stu-id="24bde-104">Both SharePoint Online modern and classic publishing sites contain links that load data from (or make calls to) SharePoint features and CDNs.</span></span> <span data-ttu-id="24bde-105">Cuanto más llamadas realiza una página, más tiempo tarda la carga en cargar.</span><span class="sxs-lookup"><span data-stu-id="24bde-105">The more calls made by a page, the longer the page takes to load.</span></span> <span data-ttu-id="24bde-106">Esto se conoce como **latencia percibida por el usuario final** o **EUPL**.</span><span class="sxs-lookup"><span data-stu-id="24bde-106">This is known as **end user perceived latency** or **EUPL**.</span></span>

<span data-ttu-id="24bde-107">Este artículo le ayudará a comprender cómo determinar el número y el impacto de las llamadas a puntos de conexión externos desde las páginas de sitios de publicación modernos y clásicos y cómo limitar su efecto en la latencia percibida por el usuario final.</span><span class="sxs-lookup"><span data-stu-id="24bde-107">This article will help you understand how to determine the number and impact of calls to external endpoints from your modern and classic publishing site pages and how to limit their effect on end user perceived latency.</span></span>

>[!NOTE]
><span data-ttu-id="24bde-108">Para obtener más información sobre el rendimiento de los portales modernos de SharePoint Online, consulte [Rendimiento en la experiencia moderna de SharePoint](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span><span class="sxs-lookup"><span data-stu-id="24bde-108">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-calls"></a><span data-ttu-id="24bde-109">Use la herramienta Diagnóstico de páginas para SharePoint para analizar las llamadas</span><span class="sxs-lookup"><span data-stu-id="24bde-109">Use the Page Diagnostics for SharePoint tool to analyze page calls</span></span>

<span data-ttu-id="24bde-110">La herramienta de Diagnóstico de páginas para SharePoint es una extensión de explorador para los nuevos exploradores de Microsoft Edge (https://www.microsoft.com/edge) y Chrome que analiza las páginas del sitio de publicación clásicas y las modernas del portal de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="24bde-110">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="24bde-111">La herramienta le ofrece un informe para cada página analizada en el que se muestra el rendimiento de la página respecto a un conjunto definido de criterios de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="24bde-111">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="24bde-112">Para instalar e informarse de la herramienta Diagnóstico de página de SharePoint, visite [Usar la herramienta Diagnóstico de página para SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="24bde-112">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="24bde-113">La herramienta de Diagnóstico de páginas solo funciona para SharePoint Online y no se puede usar en una página del sistema de SharePoint. </span><span class="sxs-lookup"><span data-stu-id="24bde-113">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="24bde-114">Cuando analice la página de un sitio de SharePoint con la herramienta Diagnóstico de páginas para SharePoint, puede ver información sobre llamadas externas en el resultado de _Solicitudes a SharePoint_ del panel **Pruebas de diagnóstico**.</span><span class="sxs-lookup"><span data-stu-id="24bde-114">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about external calls in the **Requests to SharePoint** result in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="24bde-115">La línea aparecerá en verde si la página del sitio contiene un número de llamadas inferior al número de referencia y en rojo si la página supera el número de referencia.</span><span class="sxs-lookup"><span data-stu-id="24bde-115">The line will appear in green if the site page contains fewer than the baseline number of calls, and red if the page exceeds the baseline number.</span></span> <span data-ttu-id="24bde-116">El número de referencia es diferente para las páginas modernas y clásicas porque las páginas de sitio clásicas usan HTTP 1.1 y las páginas modernas usan HTTP 2.0:</span><span class="sxs-lookup"><span data-stu-id="24bde-116">The baseline number is different for modern and classic pages because classic site pages use HTTP1.1 and modern pages use HTTP2.0:</span></span>

- <span data-ttu-id="24bde-117">Las páginas del sitio modernas no deben contener más de **25** llamadas.</span><span class="sxs-lookup"><span data-stu-id="24bde-117">Modern site pages should contain no more than **25** calls</span></span>
- <span data-ttu-id="24bde-118">Las páginas de publicación clásicas no deben contener más de **6** llamadas.</span><span class="sxs-lookup"><span data-stu-id="24bde-118">Classic publishing pages should contain no more than **6** calls</span></span>

<span data-ttu-id="24bde-119">Puede encontrarse con los siguientes resultados:</span><span class="sxs-lookup"><span data-stu-id="24bde-119">Possible results include:</span></span>

- <span data-ttu-id="24bde-120">**Requiere atención** (rojo): la página supera el número de referencia de llamadas</span><span class="sxs-lookup"><span data-stu-id="24bde-120">**Attention required** (red): The page exceeds the baseline number of calls</span></span>
- <span data-ttu-id="24bde-121">**No se requiere ninguna acción** (verde): la página contiene un número de llamadas inferior al número de referencia.</span><span class="sxs-lookup"><span data-stu-id="24bde-121">**No action required** (green): The page contains fewer than the baseline number of calls</span></span>

<span data-ttu-id="24bde-122">Si el resultado de **Solicitudes a SharePoint** aparece en la sección **Requiere atención**, puede hacer clic en el resultado para obtener detalles, incluido el número total de llamadas en la página y una lista de direcciones URL.</span><span class="sxs-lookup"><span data-stu-id="24bde-122">If the **Requests to SharePoint** result appears in the **Attention required** section, you can click the result for details, including the total number of calls on the page and a list of the URLs.</span></span>

![Resultados de solicitudes a SharePoint](media/modern-portal-optimization/pagediag-requests.png)

## <a name="remediate-performance-issues-related-to-too-many-calls-on-a-page"></a><span data-ttu-id="24bde-124">Corrección de problemas de rendimiento relacionados con demasiadas llamadas en una página</span><span class="sxs-lookup"><span data-stu-id="24bde-124">Remediate performance issues related to too many calls on a page</span></span>

<span data-ttu-id="24bde-125">Si una página contiene demasiadas llamadas, puede usar la lista de direcciones URL de los resultados de **Solicitudes a SharePoint** para determinar si hay llamadas repetidas, llamadas que deben procesarse por lotes o las llamadas que devuelven datos que deberían almacenarse en caché.</span><span class="sxs-lookup"><span data-stu-id="24bde-125">If a page contains too many calls, you can use the list of URLs in the **Requests to Sharepoint** results to determine whether there are any repeated calls, calls that should be batched, or calls that return data that should be cached.</span></span>

<span data-ttu-id="24bde-126">**El procesamiento por lotes de llamadas REST** puede ayudar a reducir la sobrecarga de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="24bde-126">**Batching REST calls** can help to reduce performance overhead.</span></span> <span data-ttu-id="24bde-127">Para más información sobre el procesamiento por lotes de llamadas de API, consulte [Realizar solicitudes de lote con las API de REST](https://docs.microsoft.com/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).</span><span class="sxs-lookup"><span data-stu-id="24bde-127">For more information about API call batching, see [Make batch requests with the REST APIs](https://docs.microsoft.com/sharepoint/dev/sp-add-ins/make-batch-requests-with-the-rest-apis).</span></span>

<span data-ttu-id="24bde-128">**El uso de una caché** para almacenar los resultados de una llamada de API puede mejorar el rendimiento de una solicitud semiactiva al permitir que el cliente use los datos en caché en lugar de realizar una llamada adicional para cada carga de página posterior.</span><span class="sxs-lookup"><span data-stu-id="24bde-128">**Using a cache** to store the results of an API call can improve the performance of a warm request by allowing the client to use the cached data instead of making an additional call for each subsequent page load.</span></span> <span data-ttu-id="24bde-129">Hay varias formas de enfocar esta solución en función de las necesidades empresariales.</span><span class="sxs-lookup"><span data-stu-id="24bde-129">There are multiple ways to approach this solution depending on the business requirement.</span></span> <span data-ttu-id="24bde-130">Por lo general, si los datos van a ser los mismos para todos los usuarios, usar un servicio de almacenamiento en caché de nivel intermedio como [_Azure Redis_ Cache](https://azure.microsoft.com/services/cache/) es una opción excelente para reducir significativamente el tráfico de API en un sitio, puesto que los usuarios solicitarían los datos del servicio de almacenamiento en caché en lugar de directamente desde SPO.</span><span class="sxs-lookup"><span data-stu-id="24bde-130">Typically if the data will be the same for all users, using a middle-tier caching service like [_Azure Redis_ cache](https://azure.microsoft.com/services/cache/) is a great option to significantly reduce API traffic against a site, as the users would request the data from the caching service instead of directly from SPO.</span></span> <span data-ttu-id="24bde-131">Las únicas llamadas a SPO necesarias serían para actualizar la memoria caché de nivel intermedio.</span><span class="sxs-lookup"><span data-stu-id="24bde-131">The only SPO calls needed would be to refresh the middle-tier's cache.</span></span> <span data-ttu-id="24bde-132">Si los datos fluctúan en base a un usuario individual, puede que sea mejor implementar una caché de cliente, como LocalStorage o incluso una cookie.</span><span class="sxs-lookup"><span data-stu-id="24bde-132">If the data will fluctuate on an individual user basis, it may be best to implement a client side cache, like LocalStorage or even a Cookie.</span></span> <span data-ttu-id="24bde-133">De esta forma, se reducirá el volumen de llamadas al eliminar las solicitudes siguientes que realiza el mismo usuario durante la duración de la caché, pero será menos eficaz que un servicio de almacenamiento en caché dedicado.</span><span class="sxs-lookup"><span data-stu-id="24bde-133">This will still reduce call volumes by eliminating subsequent requests made by the same user for the cache duration, but will be less efficient than a dedicated caching service.</span></span> <span data-ttu-id="24bde-134">PnP le permite usar LocalStorage con poco de desarrollo adicional.</span><span class="sxs-lookup"><span data-stu-id="24bde-134">PnP allows you to use LocalStorage with little additional development required.</span></span>

<span data-ttu-id="24bde-135">Antes de realizar revisiones de página para corregir problemas de rendimiento, anote el tiempo de carga de la página en los resultados del análisis.</span><span class="sxs-lookup"><span data-stu-id="24bde-135">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="24bde-136">Ejecute la herramienta de nuevo después de la revisión y compruebe si los nuevos resultados están en línea con su valor de referencia. Luego, compruebe el nuevo tiempo de carga de la página para ver si se ha producido alguna mejora.</span><span class="sxs-lookup"><span data-stu-id="24bde-136">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Resultados de tiempo de carga de la página](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="24bde-138">El tiempo de carga de la página puede variar en función de varios factores, como la carga de la red, la hora del día y otras condiciones transitorias.</span><span class="sxs-lookup"><span data-stu-id="24bde-138">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="24bde-139">Debe probar el tiempo de carga de la página varias veces, antes y después de realizar cambios, para obtener un promedio.</span><span class="sxs-lookup"><span data-stu-id="24bde-139">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="24bde-140">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="24bde-140">Related topics</span></span>

[<span data-ttu-id="24bde-141">Ajustar el rendimiento de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="24bde-141">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="24bde-142">Ajustar el rendimiento de Office 365</span><span class="sxs-lookup"><span data-stu-id="24bde-142">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="24bde-143">Rendimiento en la experiencia moderna de SharePoint</span><span class="sxs-lookup"><span data-stu-id="24bde-143">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="24bde-144">Redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="24bde-144">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="24bde-145">Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="24bde-145">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
