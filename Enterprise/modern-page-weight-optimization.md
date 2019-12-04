---
title: Optimizar el peso de la página en páginas de sitio modernas de SharePoint Online
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
- SPO_Content
ms.custom: Adm_O365
ms.reviewer: sstewart
search.appverid:
- MET150
description: Aprenda a optimizar el peso de la página en páginas de sitio modernas de SharePoint Online
ms.openlocfilehash: 96341402cb6f1ca89e7a1602d77adf70e4a69607
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "39814218"
---
# <a name="optimize-page-weight-in-sharepoint-online-modern-site-pages"></a><span data-ttu-id="27bff-103">Optimizar el peso de la página en páginas de sitio modernas de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="27bff-103">Optimize page weight in SharePoint Online modern site pages</span></span>

<span data-ttu-id="27bff-104">Las páginas de sitio modernas de SharePoint Online contienen código serializado que es necesario para representar el contenido de la página, como imágenes, texto, objetos en el área de contenido debajo de las barras de navegación y comandos, así como otros códigos HTML que conforman el marco de la página.</span><span class="sxs-lookup"><span data-stu-id="27bff-104">SharePoint Online modern site pages contain serialized code that is required to render page content of the page, including images, text, objects in the content area underneath navigation/command bars and other HTML code that forms the framework of the page.</span></span> <span data-ttu-id="27bff-105">El peso de página es una medida de este código HTML y se debe limitar para asegurar tiempos de carga de página óptimos.</span><span class="sxs-lookup"><span data-stu-id="27bff-105">Page weight is a measurement of this HTML code, and should be limited to ensure optimal page load times.</span></span>

<span data-ttu-id="27bff-106">Este artículo le ayudará a comprender cómo reducir el peso de página en las páginas de sitio modernas.</span><span class="sxs-lookup"><span data-stu-id="27bff-106">This article will help you understand how to reduce page weight in your modern site pages.</span></span>

>[!NOTE]
><span data-ttu-id="27bff-107">Para obtener más información sobre el rendimiento de los portales modernos de SharePoint Online, vea [Rendimiento en la experiencia moderna de SharePoint.](https://docs.microsoft.com/sharepoint/modern-experience-performance)</span><span class="sxs-lookup"><span data-stu-id="27bff-107">For more information about performance in SharePoint Online modern portals, see [Performance in the modern SharePoint experience](https://docs.microsoft.com/sharepoint/modern-experience-performance).</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-analyze-page-weight"></a><span data-ttu-id="27bff-108">Use la herramienta de Diagnóstico de páginas para SharePoint para analizar el peso de la página</span><span class="sxs-lookup"><span data-stu-id="27bff-108">Use the Page Diagnostics for SharePoint tool to analyze page weight</span></span>

<span data-ttu-id="27bff-109">La **herramienta Diagnóstico de páginas para SharePoint** es una extensión de explorador para Chrome y la [versión 77 o posteriores de Microsoft Edge](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) que le permite analizar páginas de sitios de publicación modernos y clásicos en SharePoint.</span><span class="sxs-lookup"><span data-stu-id="27bff-109">The **Page Diagnostics for SharePoint tool** is a browser extension for Chrome and [Microsoft Edge version 77 or later](https://www.microsoftedgeinsider.com/download?form=MI13E8&OCID=MI13E8) you can use to analyze SharePoint both modern and classic publishing site pages.</span></span> <span data-ttu-id="27bff-110">La herramienta le ofrece un informe para cada página analizada en el que se muestra el rendimiento de la página respecto a un conjunto definido de criterios de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="27bff-110">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="27bff-111">Para instalar e informarse sobre la herramienta Diagnóstico de páginas para SharePoint, visite [Usar la herramienta Diagnóstico de página para SharePoint Online](page-diagnostics-for-spo.md).</span><span class="sxs-lookup"><span data-stu-id="27bff-111">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](page-diagnostics-for-spo.md).</span></span>

<span data-ttu-id="27bff-112">Cuando analice la página de un sitio de SharePoint con la herramienta Diagnóstico de páginas para SharePoint, puede ver información sobre la página en el resultado _Peso de página inferior a 500KB_ del panel **Pruebas de diagnóstico**.</span><span class="sxs-lookup"><span data-stu-id="27bff-112">When you analyze a SharePoint site page with the Page Diagnostics for SharePoint tool, you can see information about page in the **Page weight under 500KB** result of the _Diagnostic tests_ pane.</span></span> <span data-ttu-id="27bff-113">El resultado se mostrará en verde si el peso de la página es inferior al valor de referencia y rojo si el peso de la página es superior al valor de referencia.</span><span class="sxs-lookup"><span data-stu-id="27bff-113">The result will appear in green if the page weight is under the baseline value, and red if the page weight exceeds the baseline value.</span></span>

<span data-ttu-id="27bff-114">Puede encontrarse con los siguientes resultados:</span><span class="sxs-lookup"><span data-stu-id="27bff-114">Possible results include:</span></span>

- <span data-ttu-id="27bff-115">**Requiere atención** (rojo): el peso de la página supera 500KB</span><span class="sxs-lookup"><span data-stu-id="27bff-115">**Attention required** (red): Page weight exceeds 500KB</span></span>
- <span data-ttu-id="27bff-116">**No es necesario realizar ninguna acción** (verde): el peso de la página es inferior a 500KB</span><span class="sxs-lookup"><span data-stu-id="27bff-116">**No action required** (green): Page weight is under 500KB</span></span>

<span data-ttu-id="27bff-117">Si el resultado **Peso de página inferior a 500KB** aparece en la sección **Requiere atención**, puede hacer clic en el resultado para obtener detalles.</span><span class="sxs-lookup"><span data-stu-id="27bff-117">If the **Page weight under 500KB** result appears in the **Attention required** section, you can click the result for details.</span></span>

![Solicitudes a resultados de SharePoint](media/modern-portal-optimization/pagediag-page-weight.png)

## <a name="remediate-page-weight-issues"></a><span data-ttu-id="27bff-119">Corrección de problemas de peso de página</span><span class="sxs-lookup"><span data-stu-id="27bff-119">Remediate page weight issues</span></span>

<span data-ttu-id="27bff-120">Si el peso de la página supera 500KB, puede mejorar el tiempo total de carga de la página si reduce el número de elementos web y limita el contenido de la página hasta un grado adecuado.</span><span class="sxs-lookup"><span data-stu-id="27bff-120">If page weight exceeds 500KB, you can improve overall page load time by reducing the number of web parts and limiting page content to an appropriate degree.</span></span>

<span data-ttu-id="27bff-121">Las instrucciones generales para reducir el peso de la página incluyen:</span><span class="sxs-lookup"><span data-stu-id="27bff-121">General guidance for reducing page weight includes:</span></span>

- <span data-ttu-id="27bff-122">Limite el contenido de la página a una cantidad razonable y use varias páginas para el contenido relacionado.</span><span class="sxs-lookup"><span data-stu-id="27bff-122">Limit the page content to a reasonable amount and use multiple pages for related content.</span></span>
- <span data-ttu-id="27bff-123">Minimice el uso de elementos web que tengan contenedores de propiedades grandes.</span><span class="sxs-lookup"><span data-stu-id="27bff-123">Minimize the use of web parts that have large property bags.</span></span>
- <span data-ttu-id="27bff-124">Use vistas resumidas no interactivas siempre que sea posible.</span><span class="sxs-lookup"><span data-stu-id="27bff-124">Use non-interactive rollup views when possible.</span></span>
- <span data-ttu-id="27bff-125">Optimice los tamaños de imagen cambiando el tamaño de las imágenes de forma adecuada, con formatos de imagen comprimidos y asegurándose de que se descargan de una red CDN.</span><span class="sxs-lookup"><span data-stu-id="27bff-125">Optimize image sizes by sizing images appropriately, using compressed image formats and ensuring that they are downloaded from a CDN.</span></span>

<span data-ttu-id="27bff-126">Puede encontrar más información para limitar el peso de la página en el artículo siguiente:</span><span class="sxs-lookup"><span data-stu-id="27bff-126">You can find additional guidance for limiting page weight in the following article:</span></span>

- [<span data-ttu-id="27bff-127">Optimizar el rendimiento de la página en SharePoint</span><span class="sxs-lookup"><span data-stu-id="27bff-127">Optimize page performance in SharePoint</span></span>](https://docs.microsoft.com/sharepoint/dev/general-development/optimize-page-performance-in-sharepoint)

<span data-ttu-id="27bff-128">Antes de realizar revisiones de página para corregir problemas de rendimiento, anote el tiempo de carga de la página en los resultados del análisis.</span><span class="sxs-lookup"><span data-stu-id="27bff-128">Before you make page revisions to remediate performance issues, make a note of the page load time in the analysis results.</span></span> <span data-ttu-id="27bff-129">Ejecute la herramienta de nuevo después de la revisión y compruebe si los nuevos resultados están en línea con su valor de referencia. Luego, compruebe el nuevo tiempo de carga de la página para ver si se ha producido alguna mejora.</span><span class="sxs-lookup"><span data-stu-id="27bff-129">Run the tool again after your revision to see if the new result is within the baseline standard, and check the new page load time to see if there was an improvement.</span></span>

![Resultados de tiempo de carga de la página](media/modern-portal-optimization/pagediag-page-load-time.png)

>[!NOTE]
><span data-ttu-id="27bff-131">El tiempo de carga de la página puede variar en función de varios factores, como la carga de la red, la hora del día y otras condiciones transitorias.</span><span class="sxs-lookup"><span data-stu-id="27bff-131">Page load time can vary based on a variety of factors such as network load, time of day, and other transient conditions.</span></span> <span data-ttu-id="27bff-132">Debe probar el tiempo de carga de la página varias veces, antes y después de realizar cambios, para obtener un promedio.</span><span class="sxs-lookup"><span data-stu-id="27bff-132">You should test page load time a few times before and after making changes to help you average the results.</span></span>

## <a name="related-topics"></a><span data-ttu-id="27bff-133">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="27bff-133">Related topics</span></span>

[<span data-ttu-id="27bff-134">Ajustar el rendimiento de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="27bff-134">Tune SharePoint Online performance</span></span>](tune-sharepoint-online-performance.md)

[<span data-ttu-id="27bff-135">Ajustar el rendimiento de Office 365</span><span class="sxs-lookup"><span data-stu-id="27bff-135">Tune Office 365 performance</span></span>](tune-office-365-performance.md)

[<span data-ttu-id="27bff-136">Rendimiento en la experiencia moderna de SharePoint</span><span class="sxs-lookup"><span data-stu-id="27bff-136">Performance in the modern SharePoint experience</span></span>](https://docs.microsoft.com/sharepoint/modern-experience-performance)

[<span data-ttu-id="27bff-137">Redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="27bff-137">Content delivery networks</span></span>](content-delivery-networks.md)

[<span data-ttu-id="27bff-138">Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="27bff-138">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)
