---
title: Optimizar imágenes en páginas de sitio modernas de SharePoint Online
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
description: Aprenda cómo optimizar imágenes en páginas de sitio modernas de SharePoint Online
ms.openlocfilehash: b5b1af0e78b3be7f84b1ee83048010feabddf82e
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571133"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="673b2-103">Optimizar imágenes en páginas de sitio modernas de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="673b2-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="673b2-104">Lea este artículo para averiguar cómo optimizar imágenes en páginas de sitio modernas de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="673b2-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="673b2-105">Para obtener información sobre cómo optimizar imágenes en sitios de publicación clásicos, vea [Optimización de imágenes para SharePoint Online](image-optimization-for-sharepoint-online.md).</span><span class="sxs-lookup"><span data-stu-id="673b2-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="673b2-106">Para obtener más información sobre el rendimiento de los portales modernos de SharePoint Online, vea [Rendimiento en la experiencia moderna de SharePoint.](https://docs.microsoft.com/sharepoint/modern-experience-performance)</span><span class="sxs-lookup"><span data-stu-id="673b2-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="673b2-107">Use la herramienta de Diagnóstico de página de SharePoint para analizar la optimización de imágenes</span><span class="sxs-lookup"><span data-stu-id="673b2-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="673b2-108">La herramienta de Diagnóstico de páginas para SharePoint es una extensión de explorador para los nuevos exploradores de Microsoft Edge (https://www.microsoft.com/edge) y Chrome que analiza las páginas del sitio de publicación clásicas y las modernas del portal de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="673b2-108">The Page Diagnostics for SharePoint tool is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="673b2-109">La herramienta le ofrece un informe para cada página analizada en el que se muestra el rendimiento de la página respecto a un conjunto definido de criterios de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="673b2-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="673b2-110">Para instalar e informarse de la herramienta Diagnóstico de página de SharePoint, visite [Usar la herramienta Diagnóstico de página para SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="673b2-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="673b2-111">La herramienta de Diagnóstico de páginas solo funciona para SharePoint Online y no se puede usar en una página del sistema de SharePoint. </span><span class="sxs-lookup"><span data-stu-id="673b2-111">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="673b2-112">Cuando analice un sitio moderno de SharePoint con la herramienta Diagnóstico de página de SharePoint, puede ver información sobre imágenes grandes en el panel _Pruebas de diagnóstico_.</span><span class="sxs-lookup"><span data-stu-id="673b2-112">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="673b2-113">Puede encontrarse con los siguientes resultados:</span><span class="sxs-lookup"><span data-stu-id="673b2-113">Possible results include:</span></span>

- <span data-ttu-id="673b2-114">**Atención requerida** (rojo): la página contiene **una o más** imágenes con un tamaño mayor a 300 KB</span><span class="sxs-lookup"><span data-stu-id="673b2-114">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="673b2-115">**No se requiere ninguna acción** (verde): la página no contiene imágenes con un tamaño mayor a 300 KB</span><span class="sxs-lookup"><span data-stu-id="673b2-115">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="673b2-116">Si aparece **Se han detectado imágenes grandes** en la sección **Atención requerida** de los resultados, puede hacer clic en el propio resultado para ver más detalles.</span><span class="sxs-lookup"><span data-stu-id="673b2-116">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![Resultados de la herramienta Diagnóstico de página](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="673b2-118">Corrección de problemas causados por imágenes grandes</span><span class="sxs-lookup"><span data-stu-id="673b2-118">Remediate large image issues</span></span>

<span data-ttu-id="673b2-119">Si una página contiene imágenes con un tamaño superior a 300 KB, seleccione el resultado **Se han detectado imágenes grandes** para ver qué imágenes superan ese tamaño.</span><span class="sxs-lookup"><span data-stu-id="673b2-119">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="673b2-120">En las páginas de SharePoint Online modernas, las imágenes se representan automáticamente con un tamaño ajustado, dependiendo del tamaño de la ventana del explorador y la resolución del monitor del cliente.</span><span class="sxs-lookup"><span data-stu-id="673b2-120">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="673b2-121">Siempre debe optimizar las imágenes para su uso en la web antes de cargarlas en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="673b2-121">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="673b2-122">Las imágenes muy grandes se reducen automáticamente en tamaño y resolución, lo que puede afectar a cómo se representan.</span><span class="sxs-lookup"><span data-stu-id="673b2-122">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="673b2-123">Antes de realizar revisiones de página para corregir problemas de rendimiento, anote el tiempo de carga de la página en los resultados del análisis.</span><span class="sxs-lookup"><span data-stu-id="673b2-123">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="673b2-124">Ejecute la herramienta de nuevo después de la revisión y compruebe si los nuevos resultados están en línea con su valor de referencia. Luego, compruebe el nuevo tiempo de carga de la página para ver si se ha producido alguna mejora.</span><span class="sxs-lookup"><span data-stu-id="673b2-124">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Resultados de tiempo de carga de la página](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="673b2-126">El tiempo de carga de la página puede variar en función de varios factores, como la carga de la red, la hora del día y otras condiciones transitorias.</span><span class="sxs-lookup"><span data-stu-id="673b2-126">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="673b2-127">Debe probar el tiempo de carga de la página varias veces, antes y después de realizar cambios, para obtener un promedio.</span><span class="sxs-lookup"><span data-stu-id="673b2-127">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="673b2-128">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="673b2-128">Related topics</span></span>

[<span data-ttu-id="673b2-129">Ajustar el rendimiento de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="673b2-129">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="673b2-130">Ajustar el rendimiento de Office 365</span><span class="sxs-lookup"><span data-stu-id="673b2-130">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="673b2-131">Rendimiento en la experiencia moderna de SharePoint</span><span class="sxs-lookup"><span data-stu-id="673b2-131">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="673b2-132">Redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="673b2-132">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="673b2-133">Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="673b2-133">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
