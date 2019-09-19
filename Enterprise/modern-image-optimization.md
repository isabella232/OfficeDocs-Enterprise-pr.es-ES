---
title: Optimizar imágenes en páginas de sitio modernas de SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/18/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Aprenda cómo optimizar imágenes en páginas de sitio modernas de SharePoint Online
ms.openlocfilehash: 3884758dfb2f2a81a0a6ac10abcf51932abec666
ms.sourcegitcommit: c7764503422922cb333b05d54e8ebbdb894df2f9
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2019
ms.locfileid: "37028237"
---
# <a name="optimize-images-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="303a0-103">Optimizar imágenes en páginas de sitio modernas de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="303a0-103">Optimize images in SharePoint Online modern site pages</span></span>

<span data-ttu-id="303a0-104">Lea este artículo para averiguar cómo optimizar imágenes en páginas de sitio modernas de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="303a0-104">This article will help you understand how to optimize images in SharePoint Online modern site pages.</span></span>

<span data-ttu-id="303a0-105">Para obtener información sobre cómo optimizar imágenes en sitios de publicación clásicos, vea Optimización de imágenes para SharePoint Online](image-optimization-for-sharepoint-online.md).</span><span class="sxs-lookup"><span data-stu-id="303a0-105">For information about optimizing images in classic publishing sites, see [Image optimization for SharePoint Online](image-optimization-for-sharepoint-online.md)..</span></span>

>[!NOTE]
><span data-ttu-id="303a0-106">Para obtener más información sobre el rendimiento de los portales modernos de SharePoint Online, vea [Rendimiento en la experiencia moderna de SharePoint.](https://docs.microsoft.com/es-ES/sharepoint/modern-experience-performance)</span><span class="sxs-lookup"><span data-stu-id="303a0-106">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/es-ES/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-image-optimization"></a><span data-ttu-id="303a0-107">Use la herramienta de Diagnóstico de página de SharePoint para analizar la optimización de imágenes</span><span class="sxs-lookup"><span data-stu-id="303a0-107">Use the Page Diagnostics for SharePoint tool to analyze image optimization</span></span>

<span data-ttu-id="303a0-108">La **herramienta Diagnóstico de página de SharePoint** es una extensión de explorador para Chrome y la [versión 77 o posteriores de Microsoft Edge](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) que le permite analizar páginas de sitios de publicación modernos y clásicos en SharePoint.</span><span class="sxs-lookup"><span data-stu-id="303a0-108">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/en-us/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="303a0-109">Le ofrece un informe para cada página analizada en el que se muestra el rendimiento de la página respecto a un conjunto definido de criterios.</span><span class="sxs-lookup"><span data-stu-id="303a0-109">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="303a0-110">Para instalar e informarse de la herramienta Diagnóstico de página de SharePoint, visite [Usar la herramienta Diagnóstico de página para SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="303a0-110">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="303a0-111">Cuando analice un sitio moderno de SharePoint con la herramienta Diagnóstico de página de SharePoint, puede ver información sobre imágenes grandes en el panel _Pruebas de diagnóstico_.</span><span class="sxs-lookup"><span data-stu-id="303a0-111">When you analyze a SharePoint modern site with the Page Diagnostics for SharePoint tool, you can see information about large images in the _Diagnostic tests_ pane.</span></span>

<span data-ttu-id="303a0-112">Puede encontrarse con los siguientes resultados:</span><span class="sxs-lookup"><span data-stu-id="303a0-112">Possible results include:</span></span>

- <span data-ttu-id="303a0-113">**Atención requerida** (rojo): la página contiene **una o más** imágenes con un tamaño mayor a 300 KB</span><span class="sxs-lookup"><span data-stu-id="303a0-113">**Attention required** (red): The page contains **one or more** images over 300KB in size</span></span>
- <span data-ttu-id="303a0-114">**No se requiere ninguna acción** (verde): la página no contiene imágenes con un tamaño mayor a 300 KB</span><span class="sxs-lookup"><span data-stu-id="303a0-114">**No action required** (green): The page contains no images over 300KB in size</span></span>

<span data-ttu-id="303a0-115">Si aparece **Se han detectado imágenes grandes** en la sección **Atención requerida** de los resultados, puede hacer clic en el propio resultado para ver más detalles.</span><span class="sxs-lookup"><span data-stu-id="303a0-115">If the **Large images detected** result appears in the **Attention required** section of the results, you can click the result to see additional details.</span></span>

![Resultados de la herramienta Diagnóstico de página](media/modern-portal-optimization/pagediag-large-images.png)

## <a name="remediate-large-image-issues"></a><span data-ttu-id="303a0-117">Corrección de problemas causados por imágenes grandes</span><span class="sxs-lookup"><span data-stu-id="303a0-117">Remediate large image issues</span></span>

<span data-ttu-id="303a0-118">Si una página contiene imágenes con un tamaño superior a 300 KB, seleccione el resultado **Se han detectado imágenes grandes** para ver qué imágenes superan ese tamaño.</span><span class="sxs-lookup"><span data-stu-id="303a0-118">If a page contains images over 300KB in size, select the **Large images detected** result to see which images are too large.</span></span> <span data-ttu-id="303a0-119">En las páginas de SharePoint Online modernas, las imágenes se representan automáticamente con un tamaño ajustado, dependiendo del tamaño de la ventana del explorador y la resolución del monitor del cliente.</span><span class="sxs-lookup"><span data-stu-id="303a0-119">In modern SharePoint Online pages, renditions of images are automatically provided and sized depending on the size of the browser window and the resolution of the client monitor.</span></span> <span data-ttu-id="303a0-120">Siempre debe optimizar las imágenes para su uso en la web antes de cargarlas en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="303a0-120">You should always optimize images for web use prior to upload to SharePoint Online.</span></span> <span data-ttu-id="303a0-121">Las imágenes muy grandes se reducen automáticamente en tamaño y resolución, lo que puede afectar a cómo se representan.</span><span class="sxs-lookup"><span data-stu-id="303a0-121">Very large images will be automatically reduced in size and resolution which can result in unexpected rendering characteristics.</span></span>

<span data-ttu-id="303a0-122">Antes de realizar revisiones de página para corregir problemas de rendimiento, anote el tiempo de carga de la página en los resultados del análisis.</span><span class="sxs-lookup"><span data-stu-id="303a0-122">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="303a0-123">Ejecute la herramienta de nuevo después de la revisión y compruebe si los nuevos resultados están en línea con su valor de referencia. Luego, compruebe el nuevo tiempo de carga de la página para ver si se ha producido alguna mejora.</span><span class="sxs-lookup"><span data-stu-id="303a0-123">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Resultados de tiempo de carga de la página](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="303a0-125">El tiempo de carga de la página puede variar según una serie de factores, como la carga de la red, la hora del día y otras condiciones transitorias.</span><span class="sxs-lookup"><span data-stu-id="303a0-125">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="303a0-126">Debe probar el tiempo de carga de la página varias veces, antes y después de realizar cambios, para obtener un promedio.</span><span class="sxs-lookup"><span data-stu-id="303a0-126">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="303a0-127">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="303a0-127">Related topics</span></span>

[<span data-ttu-id="303a0-128">Ajustar el rendimiento de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="303a0-128">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="303a0-129">Ajustar el rendimiento de Office 365</span><span class="sxs-lookup"><span data-stu-id="303a0-129">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="303a0-130">Rendimiento en la experiencia moderna de SharePoint</span><span class="sxs-lookup"><span data-stu-id="303a0-130">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/es-ES/sharepoint/modern-experience-performance.md)

[<span data-ttu-id="303a0-131">Redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="303a0-131">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="303a0-132">Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="303a0-132">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
