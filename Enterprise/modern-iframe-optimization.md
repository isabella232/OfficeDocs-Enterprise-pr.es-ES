---
title: Optimizar los iFrames en las páginas de sitio de publicación moderna y clásica de SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/17/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
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
description: Aprenda cómo optimizar el rendimiento de los iFrames en las páginas de sitio de publicación moderna y clásica de SharePoint Online
ms.openlocfilehash: e7a66492e18272525d854e376db49f20233d6820
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844871"
---
# <a name="optimize-iframes-in-sharepoint-online-modern-and-classic-publishing-site-pages"></a><span data-ttu-id="5c86f-103">Optimizar los iFrames en las páginas de sitio de publicación moderna y clásica de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5c86f-103">Optimize iFrames in SharePoint Online modern and classic publishing site pages</span></span>

<span data-ttu-id="5c86f-104">los iFrames pueden ser útiles para obtener una vista previa del contenido enriquecido, como vídeos u otros elementos multimedia.</span><span class="sxs-lookup"><span data-stu-id="5c86f-104">iFrames can be useful for previewing rich content such as videos or other media.</span></span> <span data-ttu-id="5c86f-105">Sin embargo, dado que cargan una página independiente en la página del sitio de SharePoint, pueden contener imágenes, vídeos u otros elementos de gran tamaño que alarguen los tiempos de carga de la página sin que usted los pueda controlar desde la propia página.</span><span class="sxs-lookup"><span data-stu-id="5c86f-105">However, because iFrames load a separate page within the SharePoint site page, content loaded in the iFrame could contain large images, videos or other elements that can contribute to overall page load times and that you cannot control on the page.</span></span> <span data-ttu-id="5c86f-106">Este artículo le mostrará cómo los iFrames afectan a la latencia que percibe el usuario en sus páginas, y cómo corregir los problemas más comunes.</span><span class="sxs-lookup"><span data-stu-id="5c86f-106">This article will help you understand how to determine how iFrames in your pages affect user perceived latency, and how to remediate common issues.</span></span>

>[!NOTE]
><span data-ttu-id="5c86f-107">Para obtener más información sobre el rendimiento de los sitios modernos de SharePoint Online, vea [Rendimiento en la experiencia moderna de SharePoint.](https://docs.microsoft.com/sharepoint/modern-experience-performance)</span><span class="sxs-lookup"><span data-stu-id="5c86f-107">For more information about performance in SharePoint Online modern sites, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-web-parts-using-iframes"></a><span data-ttu-id="5c86f-108">Use la herramienta de Diagnóstico de páginas de SharePoint para analizar los elementos web con iFrames</span><span class="sxs-lookup"><span data-stu-id="5c86f-108">Use the Page Diagnostics for SharePoint tool to analyze web parts using iFrames</span></span>

<span data-ttu-id="5c86f-109">La **herramienta Diagnóstico de página de SharePoint** es una extensión de explorador para Chrome y la [versión 77 o posteriores de Microsoft Edge](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) que le permite analizar páginas de sitios de publicación modernos y clásicos en SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5c86f-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="5c86f-110">La herramienta le ofrece un informe para cada página analizada en el que se muestra el rendimiento de la página respecto a un conjunto definido de criterios de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="5c86f-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="5c86f-111">Para instalar e informarse de la herramienta Diagnóstico de página de SharePoint, visite [Usar la herramienta Diagnóstico de página para SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="5c86f-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="5c86f-112">Cuando analice una página de sitio de SharePoint con la herramienta Diagnóstico de páginas de SharePoint, puede ver información sobre los elementos web que contengan iFrames en el panel _Pruebas de diagnóstico_.</span><span class="sxs-lookup"><span data-stu-id="5c86f-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about web parts containing iFrames in the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="5c86f-113">El valor de referencia es el mismo para las páginas modernas y las clásicas.</span><span class="sxs-lookup"><span data-stu-id="5c86f-113">The baseline metric is the same for modern and classic pages.</span></span>

<span data-ttu-id="5c86f-114">Puede encontrarse con los siguientes resultados:</span><span class="sxs-lookup"><span data-stu-id="5c86f-114">Possible results include:</span></span>

- <span data-ttu-id="5c86f-115">**Atención requerida** (rojo): la página contiene **tres o más** elementos web con iFrames.</span><span class="sxs-lookup"><span data-stu-id="5c86f-115">**Attention required** (red): The page contains **three or more** web parts using iFrames</span></span>
- <span data-ttu-id="5c86f-116">**Oportunidades de mejora** (amarillo): la página **contiene uno o dos** elementos web con iFrames</span><span class="sxs-lookup"><span data-stu-id="5c86f-116">**Improvement opportunities** (yellow): The page contains **one or two** web parts using iFrames</span></span>
- <span data-ttu-id="5c86f-117">**No se requiere ninguna acción** (verde): la página no contiene elementos web con iFrames</span><span class="sxs-lookup"><span data-stu-id="5c86f-117">**No action required** (green): The page contains no web parts using iFrames</span></span>

<span data-ttu-id="5c86f-118">Si se muestra el resultado **se han detectado elementos Web que usan iFrames** en la sección **Oportunidades de mejora** o **Atención requerida** de los resultados, puede hacer clic en el resultado para ver los elementos web que contienen iFrames.</span><span class="sxs-lookup"><span data-stu-id="5c86f-118">If the **Web parts using iFrames detected** result appears in either the **Improvement opportunities** or **Attention required)** section of the results, you can click the result to see the web parts that contain iFrames.</span></span>

![Resultados de la herramienta Diagnóstico de página](media/modern-portal-optimization/pagediag-iframe-yellow.png)

## <a name="remediate-iframe-performance-issues"></a><span data-ttu-id="5c86f-120">Corrección de problemas de rendimiento de iFrame</span><span class="sxs-lookup"><span data-stu-id="5c86f-120">Remediate iFrame performance issues</span></span>

<span data-ttu-id="5c86f-121">Use el resultado **Se han detectado elementos web con iFrames** en la herramienta de Diagnóstico de páginas para determinar qué elementos web contienen iFrames y pueden alargar el tiempo de carga de la página.</span><span class="sxs-lookup"><span data-stu-id="5c86f-121">Use the **Web parts using iFrames detected** result in the Page Diagnostic tool to determine which web parts contain iFrames and may be contributing to slow page load times.</span></span>

<span data-ttu-id="5c86f-122">Los iFrames son inherentemente lentos porque cargan una página externa independiente que incluye todo un contenido asociado, como JavaScript, CSS y elementos del marco de trabajo, lo que puede multiplicar por dos o más el tiempo de carga de la página del sitio.</span><span class="sxs-lookup"><span data-stu-id="5c86f-122">iFrames are inherently slow because they load a separate external page including all associated content such as javascript, CSS and framework elements, potentially increasing the overhead of the site page by a factor of two or more.</span></span>

<span data-ttu-id="5c86f-123">Siga las instrucciones que se indican a continuación para hacer un uso óptimo de los iFrames.</span><span class="sxs-lookup"><span data-stu-id="5c86f-123">Follow the guidance below to ensure optimal use of iFrames.</span></span>

- <span data-ttu-id="5c86f-124">Siempre que sea posible, use imágenes en lugar de iFrames si la vista previa es pequeña y no es interactiva.</span><span class="sxs-lookup"><span data-stu-id="5c86f-124">When possible, use images instead of iFrames if the preview is small to begin with or non-interactive.</span></span>
- <span data-ttu-id="5c86f-125">Si es necesario usar iFrames, minimice el número de los mismos o sáquelos de la ventanilla.</span><span class="sxs-lookup"><span data-stu-id="5c86f-125">If iFrames must be used, minimize the number and/or move them out of the viewport.</span></span>
- <span data-ttu-id="5c86f-126">Los archivos de Office incrustados, como los de Word, Excel y PowerPoint, son interactivos, pero ralentizan la carga.</span><span class="sxs-lookup"><span data-stu-id="5c86f-126">Embedded Office files like Word, Excel and PowerPoint are interactive, but are slow to load.</span></span> <span data-ttu-id="5c86f-127">A menudo es más eficiente usar imágenes en miniatura con un vínculo al documento completo.</span><span class="sxs-lookup"><span data-stu-id="5c86f-127">Image thumbnails with a link to the full document will often perform better.</span></span>
- <span data-ttu-id="5c86f-128">Los vídeos de YouTube insertados y las fuentes de Twitter suelen tener un mejor rendimiento en iFrames, pero le recomendamos que los use de forma selectiva.</span><span class="sxs-lookup"><span data-stu-id="5c86f-128">Embedded YouTube videos and Twitter feeds tend to perform better in iFrames, but use these kinds of embeds judiciously.</span></span>
- <span data-ttu-id="5c86f-129">Los elementos web aislados son una excepción razonable, pero reduzca su número y sáquelos de la ventanilla.</span><span class="sxs-lookup"><span data-stu-id="5c86f-129">Isolated web parts are a reasonable exception, but minimize their number and placement in the viewport.</span></span>
- <span data-ttu-id="5c86f-130">Si un iFrame se encuentra fuera de la ventanilla, considere la posibilidad de usar _IntersectionObserver_ para retrasar el procesamiento del iFrame hasta que aparezca en la vista.</span><span class="sxs-lookup"><span data-stu-id="5c86f-130">If an iFrame is located out of the viewport, consider using an _IntersectionObserver_ to delay rendering the iFrame until it comes into view.</span></span>

<span data-ttu-id="5c86f-131">Antes de realizar revisiones de página para corregir problemas de rendimiento, anote el tiempo de carga de la página en los resultados del análisis.</span><span class="sxs-lookup"><span data-stu-id="5c86f-131">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="5c86f-132">Ejecute la herramienta de nuevo después de la revisión y compruebe si los nuevos resultados están en línea con su valor de referencia. Luego, compruebe el nuevo tiempo de carga de la página para ver si se ha producido alguna mejora.</span><span class="sxs-lookup"><span data-stu-id="5c86f-132">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Resultados de tiempo de carga de la página](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="5c86f-134">El tiempo de carga de la página puede variar en función de varios factores, como la carga de la red, la hora del día y otras condiciones transitorias.</span><span class="sxs-lookup"><span data-stu-id="5c86f-134">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="5c86f-135">Debe probar el tiempo de carga de la página varias veces, antes y después de realizar cambios, para obtener un promedio.</span><span class="sxs-lookup"><span data-stu-id="5c86f-135">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="5c86f-136">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="5c86f-136">Related topics</span></span>

[<span data-ttu-id="5c86f-137">Ajustar el rendimiento de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5c86f-137">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="5c86f-138">Ajustar el rendimiento de Office 365</span><span class="sxs-lookup"><span data-stu-id="5c86f-138">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="5c86f-139">Rendimiento en la experiencia moderna de SharePoint</span><span class="sxs-lookup"><span data-stu-id="5c86f-139">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)
