---
title: Inicio rápido de la red de entrega de contenido (CDN) de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 06/04/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
description: Inicio rápido de la red de entrega de contenido (CDN) de Office 365
ms.openlocfilehash: 4abaaa5545bc807c4da297c66fd9ad1fb188adc7
ms.sourcegitcommit: 576c3dbdef535f952a861197dea5348908da9504
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "44561930"
---
# <a name="office-365-content-delivery-network-cdn-quickstart"></a><span data-ttu-id="e66a3-103">Inicio rápido de la red de entrega de contenido (CDN) de Office 365</span><span class="sxs-lookup"><span data-stu-id="e66a3-103">Office 365 Content Delivery Network (CDN) Quickstart</span></span>

<span data-ttu-id="e66a3-104">Puede usar la red de entrega de **contenido (CDN) de Office 365** integrada para hospedar activos estáticos (imágenes, JavaScript, hojas de estilos, archivos WOFF) para proporcionar un mejor rendimiento en las páginas de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e66a3-104">You can use the built-in **Office 365 Content Delivery Network (CDN)** to host static assets (images, JavaScript, Stylesheets, WOFF files) to provide better performance for your SharePoint Online pages.</span></span> <span data-ttu-id="e66a3-105">La CDN de Office 365 mejora el rendimiento al almacenamiento en caché los archivos estáticos más cerca de los exploradores que los solicitan, lo que ayuda a acelerar descargas y reducir la latencia.</span><span class="sxs-lookup"><span data-stu-id="e66a3-105">The Office 365 CDN improves performance by caching static assets closer to the browsers requesting them, which helps to speed up downloads and reduce latency.</span></span> <span data-ttu-id="e66a3-106">Además, la red CDN de Office 365 usa el protocolo HTTP/2 para mejorar la compresión y la canalización HTTP.</span><span class="sxs-lookup"><span data-stu-id="e66a3-106">Also, the Office 365 CDN uses the HTTP/2 protocol for improved compression and HTTP pipelining.</span></span> <span data-ttu-id="e66a3-107">La red CDN de Office 365 se incluye como parte de la suscripción a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e66a3-107">The Office 365 CDN service is included as part of your SharePoint Online subscription.</span></span>

<span data-ttu-id="e66a3-108">Para obtener una guía de información más detallada [, vea usar la red de entrega de contenido (CDN) de Office 365 con SharePoint Online](use-office-365-cdn-with-spo.md).</span><span class="sxs-lookup"><span data-stu-id="e66a3-108">For more detailed information guidance see [Use the Office 365 Content Delivery Network (CDN) with SharePoint Online](use-office-365-cdn-with-spo.md).</span></span>

>[!NOTE]
><span data-ttu-id="e66a3-109">La red CDN de Office 365 solo está disponible para los inquilinos en la nube de producción (en todo el mundo).</span><span class="sxs-lookup"><span data-stu-id="e66a3-109">The Office 365 CDN is only available to tenants in the production (worldwide) cloud.</span></span> <span data-ttu-id="e66a3-110">Actualmente, los inquilinos de las nubes del gobierno de Estados Unidos, China y Alemania no admiten la red CDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="e66a3-110">Tenants in the US Government, China and Germany clouds do not currently support the Office 365 CDN.</span></span>

## <a name="use-the-page-diagnostics-for-sharepoint-tool-to-identify-items-not-in-cdn"></a><span data-ttu-id="e66a3-111">Usar la herramienta diagnósticos de página para SharePoint para identificar elementos que no se encuentran en la red CDN</span><span class="sxs-lookup"><span data-stu-id="e66a3-111">Use the Page Diagnostics for SharePoint tool to identify items not in CDN</span></span>

<span data-ttu-id="e66a3-112">Puede usar la extensión **diagnóstico de página para el explorador de herramientas de SharePoint** para enumerar fácilmente activos en las páginas de SharePoint Online que se pueden agregar a un origen de la red CDN.</span><span class="sxs-lookup"><span data-stu-id="e66a3-112">You can use the **Page Diagnostics for SharePoint tool** browser extension to easily list assets in your SharePoint Online pages that can be added to a CDN origin.</span></span>

<span data-ttu-id="e66a3-113">La **herramienta diagnósticos de página para SharePoint** es una extensión de explorador para los nuevos exploradores de Microsoft Edge ( https://www.microsoft.com/edge) y Chrome que analizan las páginas del portal moderno de SharePoint Online y del sitio de publicación clásico.</span><span class="sxs-lookup"><span data-stu-id="e66a3-113">The **Page Diagnostics for SharePoint tool** is a browser extension for the new Microsoft Edge (https://www.microsoft.com/edge) and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="e66a3-114">La herramienta le ofrece un informe para cada página analizada en el que se muestra el rendimiento de la página respecto a un conjunto definido de criterios de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="e66a3-114">The tool provides a report for each analyzed page showing how the page performs against a defined set of performance criteria.</span></span> <span data-ttu-id="e66a3-115">Para instalar e informarse de la herramienta Diagnóstico de página de SharePoint, visite [Usar la herramienta Diagnóstico de página para SharePoint Online](https://aka.ms/perftool).</span><span class="sxs-lookup"><span data-stu-id="e66a3-115">To install and learn about the Page Diagnostics for SharePoint tool, visit [Use the Page Diagnostics tool for SharePoint Online](https://aka.ms/perftool).</span></span>

<span data-ttu-id="e66a3-116">Cuando ejecuta la herramienta diagnósticos de página para SharePoint en una página de SharePoint Online, puede hacer clic en la pestaña **pruebas de diagnóstico** para ver una lista de los activos que no se hospedan en la red CDN.</span><span class="sxs-lookup"><span data-stu-id="e66a3-116">When you run the Page Diagnostics for SharePoint tool on a SharePoint Online page, you can click the **Diagnostic Tests** tab to see a list of assets not being hosted by the CDN.</span></span> <span data-ttu-id="e66a3-117">Estos activos se enumerarán en la comprobación de la **red de entrega de contenido (CDN)** , tal como se muestra en la captura de pantalla siguiente.</span><span class="sxs-lookup"><span data-stu-id="e66a3-117">These assets will be listed under the heading **Content Delivery Network (CDN) check** as shown in the screenshot below.</span></span>

![Diagnósticos de página](media/page-diagnostics-for-spo/pagediag-results-general.PNG)

>[!NOTE]
><span data-ttu-id="e66a3-119">La herramienta de Diagnóstico de páginas solo funciona para SharePoint Online y no se puede usar en una página del sistema de SharePoint. </span><span class="sxs-lookup"><span data-stu-id="e66a3-119">The Page Diagnostics tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

## <a name="cdn-overview"></a><span data-ttu-id="e66a3-120">Información general de CDN</span><span class="sxs-lookup"><span data-stu-id="e66a3-120">CDN Overview</span></span>

<span data-ttu-id="e66a3-121">La red CDN de Office 365 está diseñada para optimizar el rendimiento de los usuarios mediante la distribución de objetos de acceso frecuente como imágenes y archivos JavaScript a través de una red global de alta velocidad, lo que reduce el tiempo de carga de la página y proporciona acceso a los objetos hospedados lo más cerca posible al usuario.</span><span class="sxs-lookup"><span data-stu-id="e66a3-121">The Office 365 CDN is designed to optimize performance for users by distributing frequently accessed objects like images and javascript files over a high-speed global network, reducing page load time and providing access to hosted objects as close as possible to the user.</span></span> <span data-ttu-id="e66a3-122">La red CDN recopila los activos de una ubicación denominada _origen_.</span><span class="sxs-lookup"><span data-stu-id="e66a3-122">The CDN fetches your assets from a location called an _origin_.</span></span> <span data-ttu-id="e66a3-123">Un origen puede ser un sitio de SharePoint, una biblioteca de documentos o una carpeta a la que se pueda tener acceso mediante una dirección URL.</span><span class="sxs-lookup"><span data-stu-id="e66a3-123">An origin can be a SharePoint site, document library or folder that is accessible by a URL.</span></span>

<span data-ttu-id="e66a3-124">La red CDN de Office 365 se divide en dos tipos básicos:</span><span class="sxs-lookup"><span data-stu-id="e66a3-124">The Office 365 CDN is separated into two basic types:</span></span>

- <span data-ttu-id="e66a3-125">La **red CDN pública** está diseñada para usarse para JS (JavaScript), CSS (StyleSheets), archivo de fuentes web (Woff, WOFF2) y imágenes no registradas como logotipos de la compañía.</span><span class="sxs-lookup"><span data-stu-id="e66a3-125">**Public CDN** is designed to be used for JS (JavaScript), CSS (StyleSheets), Web Font File (WOFF, WOFF2) and non-proprietary images like company logos.</span></span>
- <span data-ttu-id="e66a3-126">La **red CDN privada** está diseñada para usarse para imágenes (PNG, JPG, JPEG, etc.).</span><span class="sxs-lookup"><span data-stu-id="e66a3-126">**Private CDN** is designed to be used for images (PNG, JPG, JPEG, etc.).</span></span>

<span data-ttu-id="e66a3-127">Puede elegir entre los orígenes públicos o privados de su organización.</span><span class="sxs-lookup"><span data-stu-id="e66a3-127">You can choose to have both public or private origins for your organization.</span></span> <span data-ttu-id="e66a3-128">La mayoría de las organizaciones optarán por implementar una combinación de ambos.</span><span class="sxs-lookup"><span data-stu-id="e66a3-128">Most organizations will choose to implement a combination of the two.</span></span> <span data-ttu-id="e66a3-129">Tanto las opciones públicas como las privadas proporcionan mejoras de rendimiento similares, pero cada una tiene atributos y ventajas únicos.</span><span class="sxs-lookup"><span data-stu-id="e66a3-129">Both public and private options provide similar performance gains, but each has unique attributes and advantages.</span></span> <span data-ttu-id="e66a3-130">Para obtener más información acerca de los orígenes de CDN públicos y privados, vea [elegir si cada origen debe ser público o privado](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span><span class="sxs-lookup"><span data-stu-id="e66a3-130">For more information about public and private CDN origins, see [Choose whether each origin should be public or private](use-office-365-cdn-with-spo.md#CDNOriginChoosePublicPrivate).</span></span>

## <a name="how-to-enable-public-and-private-cdn-with-the-default-configuration"></a><span data-ttu-id="e66a3-131">Cómo habilitar la red CDN pública y privada con la configuración predeterminada</span><span class="sxs-lookup"><span data-stu-id="e66a3-131">How to enable Public and Private CDN with the default configuration</span></span>
<span data-ttu-id="e66a3-132">Antes de realizar cambios en la configuración de la red CDN del inquilino, debe comprobar que cumple con las directivas de cumplimiento, seguridad y privacidad de la organización.</span><span class="sxs-lookup"><span data-stu-id="e66a3-132">Before you make changes to the tenant CDN settings, you should verify that it meets compliance, security and privacy policies of your organization.</span></span>

<span data-ttu-id="e66a3-133">Para obtener opciones de configuración más detalladas, o si ya ha habilitado la red CDN y desea agregar ubicaciones (orígenes) adicionales, consulte la sección [set up and configure The Office 365 CDN by Using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell) .</span><span class="sxs-lookup"><span data-stu-id="e66a3-133">For more detailed configuration settings, or if you have already enabled CDN and want to add additional locations (origins), please see the section [Set up and configure the Office 365 CDN by using the SharePoint Online Management Shell](use-office-365-cdn-with-spo.md#set-up-and-configure-the-office-365-cdn-by-using-the-sharepoint-online-management-shell)</span></span>

<span data-ttu-id="e66a3-134">Conéctese a su inquilino mediante el shell de administración de SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="e66a3-134">Connect to your tenant using the SharePoint Online Management Shell:</span></span>

```PowerShell
Connect-SPOService -Url https://<YourTenantName>-admin.sharepoint.com
```

<span data-ttu-id="e66a3-135">Para permitir que su organización use los orígenes públicos y privados con la configuración predeterminada, escriba el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="e66a3-135">To enable your organization to use both public and private origins with the default configuration, type the following command:</span></span>

```PowerShell
Set-SPOTenantCdnEnabled -CdnType Both -Enable $true
```

<span data-ttu-id="e66a3-136">El resultado de estos cmdlets debería ser similar al siguiente:</span><span class="sxs-lookup"><span data-stu-id="e66a3-136">Output of these cmdlets should look like the following:</span></span>

![Resultado de set-SPOTenantCdnEnabled](media/O365-CDN/o365-cdn-enable-output.png)

## <a name="see-also"></a><span data-ttu-id="e66a3-138">Vea también</span><span class="sxs-lookup"><span data-stu-id="e66a3-138">See also</span></span>

[<span data-ttu-id="e66a3-139">Usar la herramienta de diagnóstico de página para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e66a3-139">Use the Page Diagnostics tool for SharePoint Online</span></span>](https://aka.ms/perftool)

[<span data-ttu-id="e66a3-140">Uso de la red de entrega de contenido (CDN) de Office 365 con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="e66a3-140">Use the Office 365 Content Delivery Network (CDN) with SharePoint Online</span></span>](use-office-365-cdn-with-spo.md)

[<span data-ttu-id="e66a3-141">Redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="e66a3-141">Content Delivery Networks</span></span>](https://aka.ms/o365cdns)

[<span data-ttu-id="e66a3-142">Planeamiento de red y ajuste del rendimiento para Office 365</span><span class="sxs-lookup"><span data-stu-id="e66a3-142">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)

[<span data-ttu-id="e66a3-143">Series de rendimiento de SharePoint: serie de vídeos de red CDN de Office 365</span><span class="sxs-lookup"><span data-stu-id="e66a3-143">SharePoint Performance Series - Office 365 CDN video series</span></span>](https://www.youtube.com/playlist?list=PLR9nK3mnD-OWMfr1BA9mr5oCw2aJXw4WA)
