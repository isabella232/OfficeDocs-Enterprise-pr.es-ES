---
title: Opciones de navegación para SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: En este artículo se describen las opciones de navegación sitios con la publicación de SharePoint habilitada en SharePoint Online.
ms.openlocfilehash: dd11775c35f9eb7d2b6bccc38023b6f8bce8efc4
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606766"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="56ccd-103">Opciones de navegación para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="56ccd-103">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="56ccd-104">En este artículo se describen las opciones de navegación sitios con la publicación de SharePoint habilitada en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="56ccd-104">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="56ccd-105">La elección y configuración de la navegación afectan significativamente al rendimiento y la escalabilidad de los sitios de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="56ccd-105">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span> <span data-ttu-id="56ccd-106">La plantilla de sitio de publicación de SharePoint solo debe usarse si es necesario para un portal centralizado y la característica de publicación solo debe habilitarse en sitios específicos y solo cuando sea absolutamente necesario, ya que puede afectar al rendimiento cuando se usa incorrectamente.</span><span class="sxs-lookup"><span data-stu-id="56ccd-106">The SharePoint Publishing site template should only be used if required for a centralized portal and the publishing feature should only be enabled on specific sites and only when absolutely required as it can impact performance when used incorrectly.</span></span>

>[!NOTE]
><span data-ttu-id="56ccd-107">Si está usando las opciones modernas de navegación de SharePoint, como el menú mega, la navegación en cascada o la navegación de concentradores, este artículo no se aplica a su sitio.</span><span class="sxs-lookup"><span data-stu-id="56ccd-107">If you're using modern SharePoint navigation options like mega menu, cascading navigation, or hub navigation, this article does not apply to your site.</span></span> <span data-ttu-id="56ccd-108">Las arquitecturas de sitio modernas de SharePoint aprovechan una jerarquía de sitios más acoplada y un modelo de concentrador y radio.</span><span class="sxs-lookup"><span data-stu-id="56ccd-108">Modern SharePoint site architectures leverage a more flattened site hierarchy and a hub-and-spoke model.</span></span> <span data-ttu-id="56ccd-109">Esto permite lograr muchos escenarios que no requieran el uso de la característica de publicación de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="56ccd-109">This allows many scenarios to be achieved that do NOT require use of the SharePoint Publishing feature.</span></span>

## <a name="overview-of-navigation-options"></a><span data-ttu-id="56ccd-110">Información general sobre las opciones de navegación</span><span class="sxs-lookup"><span data-stu-id="56ccd-110">Overview of navigation options</span></span>

<span data-ttu-id="56ccd-111">La configuración del proveedor de navegación puede afectar significativamente al rendimiento de todo el sitio, y se debe tener en cuenta para elegir un proveedor de navegación y una configuración que se escale con eficacia para los requisitos de un sitio de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="56ccd-111">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="56ccd-112">Hay dos proveedores de navegación preparados, así como implementaciones de navegación personalizadas.</span><span class="sxs-lookup"><span data-stu-id="56ccd-112">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="56ccd-113">La primera opción, [**navegación estructural**](#using-structural-navigation-in-sharepoint-online), es la opción de navegación recomendada en SharePoint Online para los sitios clásicos de SharePoint, **si activa el almacenamiento en caché de navegación estructural para su sitio**.</span><span class="sxs-lookup"><span data-stu-id="56ccd-113">The first option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), is the recommended navigation option in SharePoint Online for classic Sharepoint sites, **if you turn on structural navigation caching for your site**.</span></span> <span data-ttu-id="56ccd-114">Este proveedor de navegación muestra los elementos de navegación bajo el sitio actual y, de forma opcional, el sitio actual y sus elementos relacionados.</span><span class="sxs-lookup"><span data-stu-id="56ccd-114">This navigation provider displays the navigation items below the current site, and optionally the current site and its siblings.</span></span> <span data-ttu-id="56ccd-115">Proporciona funciones adicionales, como el recorte de seguridad y la enumeración de la estructura del sitio.</span><span class="sxs-lookup"><span data-stu-id="56ccd-115">It provides additional capabilities such as security trimming and site structure enumeration.</span></span> <span data-ttu-id="56ccd-116">Si el almacenamiento en caché está deshabilitado, esto afectará negativamente al rendimiento y la escalabilidad, y puede estar sujeto a la limitación.</span><span class="sxs-lookup"><span data-stu-id="56ccd-116">If caching is disabled, this will negatively impact performance and scalability, and may be subject to throttling.</span></span>

<span data-ttu-id="56ccd-117">La segunda opción, la [**navegación administrada (metadatos)**](#using-managed-navigation-and-metadata-in-sharepoint-online), representa los elementos de navegación con un conjunto de términos de metadatos administrados.</span><span class="sxs-lookup"><span data-stu-id="56ccd-117">The second option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), represents navigation items using a Managed Metadata term set.</span></span> <span data-ttu-id="56ccd-118">Se recomienda deshabilitar el recorte de seguridad a menos que sea necesario.</span><span class="sxs-lookup"><span data-stu-id="56ccd-118">We recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="56ccd-119">El recorte de seguridad está habilitado como configuración segura de forma predeterminada para este proveedor de navegación; sin embargo, muchos sitios no requieren la sobrecarga de recorte de seguridad, ya que los elementos de navegación suelen ser coherentes para todos los usuarios del sitio.</span><span class="sxs-lookup"><span data-stu-id="56ccd-119">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="56ccd-120">Con la configuración recomendada para deshabilitar el recorte de seguridad, este proveedor de navegación no necesita la enumeración de la estructura del sitio y es altamente escalable con un impacto aceptable en el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="56ccd-120">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="56ccd-121">Además de los proveedores de navegación preinstalados, muchos clientes han implementado correctamente implementaciones de navegación personalizadas alternativas.</span><span class="sxs-lookup"><span data-stu-id="56ccd-121">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="56ccd-122">Consulte [scripting del lado cliente](#using-search-driven-client-side-scripting) basado en búsquedas en este artículo.</span><span class="sxs-lookup"><span data-stu-id="56ccd-122">See [Search-driven client-side scripting](#using-search-driven-client-side-scripting) in this article.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="56ccd-123">Ventajas y desventajas de las opciones de navegación de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="56ccd-123">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="56ccd-124">En la tabla siguiente se resumen las ventajas y los inconvenientes de cada opción.</span><span class="sxs-lookup"><span data-stu-id="56ccd-124">The following table summarizes the pros and cons of each option.</span></span>

|<span data-ttu-id="56ccd-125">Navegación estructural</span><span class="sxs-lookup"><span data-stu-id="56ccd-125">Structural navigation</span></span>  |<span data-ttu-id="56ccd-126">Navegación administrada</span><span class="sxs-lookup"><span data-stu-id="56ccd-126">Managed navigation</span></span>  |<span data-ttu-id="56ccd-127">Navegación basada en búsquedas</span><span class="sxs-lookup"><span data-stu-id="56ccd-127">Search-driven navigation</span></span>  |<span data-ttu-id="56ccd-128">Proveedor de navegación personalizada</span><span class="sxs-lookup"><span data-stu-id="56ccd-128">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="56ccd-129">Ti</span><span class="sxs-lookup"><span data-stu-id="56ccd-129">Pros:</span></span><br/><br/><span data-ttu-id="56ccd-130">Fácil de mantener</span><span class="sxs-lookup"><span data-stu-id="56ccd-130">Easy to maintain</span></span><br/><span data-ttu-id="56ccd-131">Seguridad recortada</span><span class="sxs-lookup"><span data-stu-id="56ccd-131">Security trimmed</span></span><br/><span data-ttu-id="56ccd-132">Actualizaciones automáticas en un plazo de 24 horas al cambiar el contenido</span><span class="sxs-lookup"><span data-stu-id="56ccd-132">Automatically updates within 24 hours when content is changed</span></span><br/>     |<span data-ttu-id="56ccd-133">Ti</span><span class="sxs-lookup"><span data-stu-id="56ccd-133">Pros:</span></span><br/><br/><span data-ttu-id="56ccd-134">Fácil de mantener</span><span class="sxs-lookup"><span data-stu-id="56ccd-134">Easy to maintain</span></span><br/>|<span data-ttu-id="56ccd-135">Ti</span><span class="sxs-lookup"><span data-stu-id="56ccd-135">Pros:</span></span><br/><br/><span data-ttu-id="56ccd-136">Seguridad recortada</span><span class="sxs-lookup"><span data-stu-id="56ccd-136">Security trimmed</span></span><br/><span data-ttu-id="56ccd-137">Se actualiza automáticamente cuando se agregan sitios</span><span class="sxs-lookup"><span data-stu-id="56ccd-137">Automatically updates as sites are added</span></span><br/><span data-ttu-id="56ccd-138">Tiempo de carga rápida y estructura de navegación en caché local</span><span class="sxs-lookup"><span data-stu-id="56ccd-138">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="56ccd-139">Ti</span><span class="sxs-lookup"><span data-stu-id="56ccd-139">Pros:</span></span><br/><br/><span data-ttu-id="56ccd-140">Opción más amplia de opciones disponibles</span><span class="sxs-lookup"><span data-stu-id="56ccd-140">Wider choice of options available</span></span><br/><span data-ttu-id="56ccd-141">Carga rápida cuando se utiliza correctamente el almacenamiento en caché</span><span class="sxs-lookup"><span data-stu-id="56ccd-141">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="56ccd-142">Muchas opciones funcionan bien con un diseño de página dinámico</span><span class="sxs-lookup"><span data-stu-id="56ccd-142">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="56ccd-143">Conos</span><span class="sxs-lookup"><span data-stu-id="56ccd-143">Cons:</span></span><br/><br/><span data-ttu-id="56ccd-144">**Afecta al rendimiento si el almacenamiento en caché está deshabilitado**</span><span class="sxs-lookup"><span data-stu-id="56ccd-144">**Impacts performance if caching is disabled**</span></span><br/><span data-ttu-id="56ccd-145">Sujeto a la limitación</span><span class="sxs-lookup"><span data-stu-id="56ccd-145">Subject to throttling</span></span><br/>|<span data-ttu-id="56ccd-146">Conos</span><span class="sxs-lookup"><span data-stu-id="56ccd-146">Cons:</span></span><br/><br/><span data-ttu-id="56ccd-147">No se actualiza automáticamente para reflejar la estructura del sitio</span><span class="sxs-lookup"><span data-stu-id="56ccd-147">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="56ccd-148">**Afecta al rendimiento si se habilita el recorte de seguridad** o si la estructura de navegación es compleja</span><span class="sxs-lookup"><span data-stu-id="56ccd-148">**Impacts performance if security trimming is enabled** or when navigation structure is complex</span></span><br/>|<span data-ttu-id="56ccd-149">Conos</span><span class="sxs-lookup"><span data-stu-id="56ccd-149">Cons:</span></span><br/><br/><span data-ttu-id="56ccd-150">No se pueden ordenar sitios fácilmente</span><span class="sxs-lookup"><span data-stu-id="56ccd-150">No ability to easily order sites</span></span><br/><span data-ttu-id="56ccd-151">Requiere la personalización de la página maestra (habilidades técnicas necesarias)</span><span class="sxs-lookup"><span data-stu-id="56ccd-151">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="56ccd-152">Conos</span><span class="sxs-lookup"><span data-stu-id="56ccd-152">Cons:</span></span><br/><br/><span data-ttu-id="56ccd-153">Se requiere desarrollo personalizado</span><span class="sxs-lookup"><span data-stu-id="56ccd-153">Custom development is required</span></span><br/><span data-ttu-id="56ccd-154">Se necesita un origen de datos externo o almacenamiento en caché, por ejemplo Azure</span><span class="sxs-lookup"><span data-stu-id="56ccd-154">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="56ccd-155">La opción más adecuada para su sitio dependerá de los requisitos de su sitio y de su capacidad técnica.</span><span class="sxs-lookup"><span data-stu-id="56ccd-155">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="56ccd-156">Si quiere un proveedor de navegación fácil de configurar que se actualice automáticamente cuando cambie el contenido, la navegación estructural [con el almacenamiento en caché habilitado](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) es una buena opción.</span><span class="sxs-lookup"><span data-stu-id="56ccd-156">If you want an easy-to-configure navigation provider that automatically updates when content is changed, then structural navigation [with caching enabled](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) is a good option.</span></span>

>[!NOTE]
><span data-ttu-id="56ccd-157">Aplicar el mismo principio que los sitios modernos de SharePoint simplificando la estructura general del sitio a una estructura más plana y no jerárquica mejora el rendimiento y simplifica el paso a los sitios modernos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="56ccd-157">Applying the same principle as modern SharePoint sites by simplifying the overall site structure to a flatter, non-hierarchical structure improves performance and simplifies moving to modern SharePoint sites.</span></span> <span data-ttu-id="56ccd-158">Esto significa que en lugar de tener una sola colección de sitios con cientos de sitios (subwebs), un mejor enfoque es disponer de muchas colecciones de sitios con muy pocos subsitios (subwebs).</span><span class="sxs-lookup"><span data-stu-id="56ccd-158">What this means is that instead of having a single site collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="56ccd-159">Analizar el rendimiento de navegación en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="56ccd-159">Analyzing navigation performance in SharePoint Online</span></span>

<span data-ttu-id="56ccd-160">La [herramienta diagnósticos de página para SharePoint](https://aka.ms/perftool) es una extensión de explorador para los exploradores Microsoft Edge y Chrome que analizan las páginas del portal moderno de SharePoint Online y del sitio de publicación clásico.</span><span class="sxs-lookup"><span data-stu-id="56ccd-160">The [Page Diagnostics for SharePoint tool](https://aka.ms/perftool) is a browser extension for Microsoft Edge and Chrome browsers that analyzes both SharePoint Online modern portal and classic publishing site pages.</span></span> <span data-ttu-id="56ccd-161">Esta herramienta solo funciona para SharePoint Online y no se puede usar en una página del sistema de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="56ccd-161">This tool only works for SharePoint Online, and cannot be used on a SharePoint system page.</span></span>

<span data-ttu-id="56ccd-162">La herramienta genera un informe para cada página analizada que muestra cómo se ejecuta la página en un conjunto predefinido de reglas y muestra información detallada cuando los resultados de una prueba se encuentran fuera del valor de línea base.</span><span class="sxs-lookup"><span data-stu-id="56ccd-162">The tool generates a report for each analyzed page showing how the page performs against a pre-defined set of rules and displays detailed information when results for a test fall outside the baseline value.</span></span> <span data-ttu-id="56ccd-163">Los diseñadores y administradores de SharePoint Online pueden usar la herramienta para solucionar problemas de rendimiento y garantizar que las nuevas páginas se optimizan antes de la publicación.</span><span class="sxs-lookup"><span data-stu-id="56ccd-163">SharePoint Online administrators and designers can use the tool to troubleshoot performance issues to ensure that new pages are optimized prior to publishing.</span></span>

<span data-ttu-id="56ccd-164">En particular, **SPRequestDuration** es el tiempo que tarda SharePoint en procesar la página.</span><span class="sxs-lookup"><span data-stu-id="56ccd-164">**SPRequestDuration** in particular is the time it takes for SharePoint to process the page.</span></span> <span data-ttu-id="56ccd-165">La navegación intensa (como, por ejemplo, las páginas en navegación), las jerarquías de sitios complejas y otras opciones de configuración y topología pueden contribuir drásticamente a las duraciones más largas.</span><span class="sxs-lookup"><span data-stu-id="56ccd-165">Heavy navigation (like including pages in navigation), complex site hierarchies, and other configuration and topology options can all dramatically contribute to longer durations.</span></span>

## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="56ccd-166">Uso de la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="56ccd-166">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="56ccd-167">Esta es la navegación predefinida que se usa de forma predeterminada y es la solución más sencilla.</span><span class="sxs-lookup"><span data-stu-id="56ccd-167">This is the out-of-the-box navigation used by default and is the most straightforward solution.</span></span> <span data-ttu-id="56ccd-168">No requiere personalización y un usuario no técnico también puede agregar elementos, ocultar elementos y administrar la navegación desde la página de configuración fácilmente.</span><span class="sxs-lookup"><span data-stu-id="56ccd-168">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="56ccd-169">Se recomienda [Habilitar el almacenamiento en caché](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43); de lo contrario, existe un equilibrio entre rendimiento caro.</span><span class="sxs-lookup"><span data-stu-id="56ccd-169">We recommend [enabling caching](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43), otherwise there is an expensive performance trade-off.</span></span>

### <a name="how-to-implement-structural-navigation-caching"></a><span data-ttu-id="56ccd-170">Cómo implementar el almacenamiento en caché de navegación estructural</span><span class="sxs-lookup"><span data-stu-id="56ccd-170">How to implement structural navigation caching</span></span>

<span data-ttu-id="56ccd-171">En la apariencia de la **configuración del sitio**  >  **y**la  >  **navegación**, puede validar si la navegación estructural está seleccionada para la navegación global o la navegación actual.</span><span class="sxs-lookup"><span data-stu-id="56ccd-171">Under **Site Settings** > **Look and Feel** > **Navigation**, you can validate if structural navigation is selected for either global navigation or current navigation.</span></span> <span data-ttu-id="56ccd-172">La selección de **Mostrar páginas** tendrá un impacto negativo en el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="56ccd-172">Selecting **Show pages** will have negative impact on performance.</span></span>

![Navegación estructural con la muestra de subsitios seleccionada](media/SPONavOptionsStructuredShowSubsites.png)

<span data-ttu-id="56ccd-174">El almacenamiento en caché se puede habilitar o deshabilitar en el nivel de la colección de sitios y en el nivel del sitio, y se habilita de forma predeterminada para ambos.</span><span class="sxs-lookup"><span data-stu-id="56ccd-174">Caching can be enabled or disabled at the site collection level and at the site level, and is enabled for both by default.</span></span> <span data-ttu-id="56ccd-175">Para habilitar en el nivel de la colección de sitios, en **configuración del sitio**navegación de la colección de sitios de administración de sitios  >  **Site Collection Administration**  >  **Site Collection Navigation**, active la casilla **Habilitar almacenamiento en caché**.</span><span class="sxs-lookup"><span data-stu-id="56ccd-175">To enable at the site collection level, under **Site Settings** > **Site Collection Administration** > **Site Collection Navigation**, check the box for **Enable caching**.</span></span>

![Habilitar el almacenamiento en caché en el nivel de sitio](media/structural-nav/structural-nav-caching-site-coll.png)

<span data-ttu-id="56ccd-177">Para habilitar en el nivel de sitio, **Site Settings**en  >  **navegación**por la configuración del sitio, active la casilla **Habilitar almacenamiento en caché**.</span><span class="sxs-lookup"><span data-stu-id="56ccd-177">To enable at the site level, under **Site Settings** > **Navigation**, check the box for **Enable caching**.</span></span>

![Habilitar el almacenamiento en caché en el nivel de sitio](media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="56ccd-179">Usar la navegación administrada y los metadatos en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="56ccd-179">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="56ccd-180">La navegación administrada es otra opción precreada que puede usar para volver a crear la mayor parte de la funcionalidad como navegación estructural.</span><span class="sxs-lookup"><span data-stu-id="56ccd-180">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="56ccd-181">Los metadatos administrados se pueden configurar para que el recorte de seguridad esté habilitado o deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="56ccd-181">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="56ccd-182">Cuando se configura con el recorte de seguridad deshabilitado, la navegación administrada es bastante eficiente ya que carga todos los vínculos de navegación con un número constante de llamadas del servidor.</span><span class="sxs-lookup"><span data-stu-id="56ccd-182">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="56ccd-183">No obstante, la habilitación de la reducción de seguridad anula algunas de las ventajas de rendimiento de la navegación administrada.</span><span class="sxs-lookup"><span data-stu-id="56ccd-183">Enabling security trimming, however, negates some of the performance advantages of managed navigation.</span></span>

<span data-ttu-id="56ccd-184">Si necesita habilitar el recorte de seguridad, le recomendamos que:</span><span class="sxs-lookup"><span data-stu-id="56ccd-184">If you need to enable security trimming, we recommend that you:</span></span>

- <span data-ttu-id="56ccd-185">Actualizar todos los vínculos a direcciones URL descriptivas a vínculos simples</span><span class="sxs-lookup"><span data-stu-id="56ccd-185">Update all friendly URL links to simple links</span></span>
- <span data-ttu-id="56ccd-186">Agregar los nodos de recorte de seguridad necesarios como direcciones URL descriptivas</span><span class="sxs-lookup"><span data-stu-id="56ccd-186">Add required security trimming nodes as friendly URLs</span></span>
- <span data-ttu-id="56ccd-187">Limitar el número de elementos de navegación a un máximo de 100 y no tener más de 3 niveles de profundidad</span><span class="sxs-lookup"><span data-stu-id="56ccd-187">Limit the number of navigation items to no more than 100 and no more than 3 levels deep</span></span>

<span data-ttu-id="56ccd-188">Muchos sitios no requieren el recorte de seguridad, ya que la estructura de navegación suele ser coherente para todos los usuarios del sitio.</span><span class="sxs-lookup"><span data-stu-id="56ccd-188">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="56ccd-189">Si se deshabilita el recorte de seguridad y se agrega un vínculo a la navegación que no tienen acceso a todos los usuarios, el vínculo seguirá mostrando pero conducirá a un mensaje de acceso denegado.</span><span class="sxs-lookup"><span data-stu-id="56ccd-189">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="56ccd-190">No existe ningún riesgo de acceso involuntario al contenido.</span><span class="sxs-lookup"><span data-stu-id="56ccd-190">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="56ccd-191">Cómo implementar la navegación administrada y los resultados</span><span class="sxs-lookup"><span data-stu-id="56ccd-191">How to implement managed navigation and the results</span></span>

<span data-ttu-id="56ccd-192">Hay varios artículos sobre docs.microsoft.com acerca de los detalles de la navegación administrada.</span><span class="sxs-lookup"><span data-stu-id="56ccd-192">There are several articles on docs.microsoft.com about the details of managed navigation.</span></span> <span data-ttu-id="56ccd-193">Por ejemplo, vea [información general sobre la navegación administrada en SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="56ccd-193">For example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="56ccd-194">Para implementar la navegación administrada, se configuran los términos con direcciones URL correspondientes a la estructura de navegación del sitio.</span><span class="sxs-lookup"><span data-stu-id="56ccd-194">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of the site.</span></span> <span data-ttu-id="56ccd-195">La navegación administrada puede incluso creadosrse manualmente para reemplazar la navegación estructural en muchos casos.</span><span class="sxs-lookup"><span data-stu-id="56ccd-195">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="56ccd-196">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="56ccd-196">For example:</span></span>

![Estructura de sitio de SharePoint Online](media/SPONavOptionsListOfSites.png)<span data-ttu-id="56ccd-198">)</span><span class="sxs-lookup"><span data-stu-id="56ccd-198">)</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="56ccd-199">Uso de scripting de cliente basado en búsquedas</span><span class="sxs-lookup"><span data-stu-id="56ccd-199">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="56ccd-200">Una clase común de implementaciones de navegación personalizadas adopta patrones de diseño representados por el cliente que almacenan una memoria caché local de nodos de navegación.</span><span class="sxs-lookup"><span data-stu-id="56ccd-200">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span>

<span data-ttu-id="56ccd-201">Estos proveedores de navegación tienen un par de ventajas clave:</span><span class="sxs-lookup"><span data-stu-id="56ccd-201">These navigation providers have a couple of key advantages:</span></span>

- <span data-ttu-id="56ccd-202">Por lo general, funcionan bien con diseños de página dinámicos.</span><span class="sxs-lookup"><span data-stu-id="56ccd-202">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="56ccd-203">Son extremadamente escalables y funcionan porque pueden representarse sin costo de recursos (y actualizar en segundo plano después de un tiempo de espera).</span><span class="sxs-lookup"><span data-stu-id="56ccd-203">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span>
- <span data-ttu-id="56ccd-204">Estos proveedores de navegación pueden recuperar datos de navegación mediante varias estrategias, desde configuraciones estáticas simples a varios proveedores de datos dinámicos.</span><span class="sxs-lookup"><span data-stu-id="56ccd-204">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span>

<span data-ttu-id="56ccd-205">Un ejemplo de un proveedor de datos es usar una **navegación**basada en búsquedas, que permite la flexibilidad para enumerar los nodos de navegación y controlar de forma eficaz el recorte de seguridad.</span><span class="sxs-lookup"><span data-stu-id="56ccd-205">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span>

<span data-ttu-id="56ccd-206">Hay otras opciones populares para crear **proveedores de navegación personalizados**.</span><span class="sxs-lookup"><span data-stu-id="56ccd-206">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="56ccd-207">Revise [soluciones de navegación para portales de SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) para obtener más información sobre la creación de un proveedor de navegación personalizado.</span><span class="sxs-lookup"><span data-stu-id="56ccd-207">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>

<span data-ttu-id="56ccd-208">Mediante la búsqueda, puede aprovechar los índices que se han integrado en el fondo con el rastreo continuo.</span><span class="sxs-lookup"><span data-stu-id="56ccd-208">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="56ccd-209">Los resultados de la búsqueda se extraen del índice de búsqueda y los resultados se reducen por seguridad.</span><span class="sxs-lookup"><span data-stu-id="56ccd-209">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="56ccd-210">Esto suele ser más rápido que los proveedores de navegación preparados cuando se requiere el recorte de seguridad.</span><span class="sxs-lookup"><span data-stu-id="56ccd-210">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="56ccd-211">Usar la búsqueda para la navegación estructural, sobre todo si tiene una estructura de sitio compleja, reducirá considerablemente el tiempo de carga de la página.</span><span class="sxs-lookup"><span data-stu-id="56ccd-211">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="56ccd-212">La principal ventaja de esto sobre la navegación administrada es que se beneficia de la reducción de seguridad.</span><span class="sxs-lookup"><span data-stu-id="56ccd-212">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="56ccd-213">Este enfoque implica la creación de una página maestra personalizada y la sustitución del código de navegación precreado con HTML personalizado.</span><span class="sxs-lookup"><span data-stu-id="56ccd-213">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="56ccd-214">Siga este procedimiento descrito en el siguiente ejemplo para reemplazar el código de navegación en el archivo `seattle.html` .</span><span class="sxs-lookup"><span data-stu-id="56ccd-214">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="56ccd-215">En este ejemplo, se abrirá el `seattle.html` archivo y se reemplazará todo el elemento `id="DeltaTopNavigation"` con código HTML personalizado.</span><span class="sxs-lookup"><span data-stu-id="56ccd-215">In this example, you will open the `seattle.html` file and replace the whole element `id="DeltaTopNavigation"` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="56ccd-216">Ejemplo: reemplazar el código de navegación de precodificación en una página maestra</span><span class="sxs-lookup"><span data-stu-id="56ccd-216">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1. <span data-ttu-id="56ccd-217">Navegue a la página Configuración del sitio.</span><span class="sxs-lookup"><span data-stu-id="56ccd-217">Navigate to the Site Settings page.</span></span>
2. <span data-ttu-id="56ccd-218">Abra la galería de páginas maestras; para ello, haga clic en **páginas maestras**.</span><span class="sxs-lookup"><span data-stu-id="56ccd-218">Open the master page gallery by clicking **Master Pages**.</span></span>
3. <span data-ttu-id="56ccd-219">Desde aquí puede navegar por la biblioteca y descargar el archivo `seattle.master` .</span><span class="sxs-lookup"><span data-stu-id="56ccd-219">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4. <span data-ttu-id="56ccd-220">Edite el código con un editor de texto y elimine el bloque de código en la siguiente captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="56ccd-220">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Eliminar el bloque de código que se muestra](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="56ccd-222">Quite el código entre las `<SharePoint:AjaxDelta id="DeltaTopNavigation">` `<\SharePoint:AjaxDelta>` etiquetas y y reemplácela por el siguiente fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="56ccd-222">Remove the code between the `<SharePoint:AjaxDelta id="DeltaTopNavigation">` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```javascript
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                </a>

                <!-- ko if: children.length > 0-->
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
          <!-- /ko -->
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```

<br/>
6. <span data-ttu-id="56ccd-223">Reemplace la dirección URL de la etiqueta de anclaje de la imagen de carga al principio, por un vínculo a una imagen de carga en la colección de sitios.</span><span class="sxs-lookup"><span data-stu-id="56ccd-223">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="56ccd-224">Después de realizar los cambios, cambie el nombre del archivo y, a continuación, cárguelo en la galería de páginas maestras.</span><span class="sxs-lookup"><span data-stu-id="56ccd-224">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="56ccd-225">Esto genera un nuevo archivo. Master.</span><span class="sxs-lookup"><span data-stu-id="56ccd-225">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="56ccd-226">Este HTML es el marcado básico que rellenará los resultados de la búsqueda devueltos desde el código JavaScript.</span><span class="sxs-lookup"><span data-stu-id="56ccd-226">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="56ccd-227">Tendrá que editar el código para cambiar el valor de var root = "site Collection URL" como se muestra en el siguiente fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="56ccd-227">You will need to edit the code to change the value for var root = "site collection URL" as demonstrated in the following snippet:</span></span><br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. <span data-ttu-id="56ccd-228">Los resultados se asignan a self. Nodes y una jerarquía se crea a partir de los objetos mediante la linq.js asignar el resultado a una matriz self. hierarchy.</span><span class="sxs-lookup"><span data-stu-id="56ccd-228">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="56ccd-229">Esta matriz es el objeto que está enlazado al HTML.</span><span class="sxs-lookup"><span data-stu-id="56ccd-229">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="56ccd-230">Esto se realiza en la función toggleView () pasando el objeto Self a la función ko. applyBinding ().</span><span class="sxs-lookup"><span data-stu-id="56ccd-230">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="56ccd-231">Esto hace que la matriz de jerarquías se enlace al siguiente HTML:</span><span class="sxs-lookup"><span data-stu-id="56ccd-231">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

<span data-ttu-id="56ccd-232">Los controladores de eventos para `mouseenter` y `mouseexit` se agregan a la navegación de nivel superior para controlar los menús desplegables de subsitio que se realizan en la `addEventsToElements()` función.</span><span class="sxs-lookup"><span data-stu-id="56ccd-232">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="56ccd-233">En nuestro ejemplo de navegación compleja, una carga de página nueva sin el almacenamiento en caché local muestra el tiempo empleado en el servidor se ha reducido de la navegación estructural de Benchmark para obtener un resultado similar al del enfoque de navegación administrada.</span><span class="sxs-lookup"><span data-stu-id="56ccd-233">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="56ccd-234">Acerca del archivo JavaScript...</span><span class="sxs-lookup"><span data-stu-id="56ccd-234">About the JavaScript file...</span></span>

>[!NOTE]
><span data-ttu-id="56ccd-235">Si usa JavaScript personalizado, asegúrese de que la red CDN pública esté habilitada y que el archivo esté en una ubicación de red CDN.</span><span class="sxs-lookup"><span data-stu-id="56ccd-235">If using custom JavaScript, ensure that public CDN is enabled and the file is in a CDN location.</span></span>

<span data-ttu-id="56ccd-236">El archivo JavaScript completo es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="56ccd-236">The entire JavaScript file is as follows:</span></span>

```javascript
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefox
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

```

<span data-ttu-id="56ccd-237">Para resumir el código que se ha mostrado anteriormente en la `jQuery $(document).ready` función `viewModel object` , se ha creado una y, a continuación, `loadNavigationNodes()` se llama a la función en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="56ccd-237">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="56ccd-238">Esta función carga la jerarquía de navegación previamente creada almacenada en el almacenamiento local de HTML5 del explorador del cliente o llama a la función `queryRemoteInterface()` .</span><span class="sxs-lookup"><span data-stu-id="56ccd-238">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="56ccd-239">`QueryRemoteInterface()`compila una solicitud mediante la `getRequest()` función con el parámetro de consulta definido anteriormente en el script y, a continuación, devuelve datos del servidor.</span><span class="sxs-lookup"><span data-stu-id="56ccd-239">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="56ccd-240">Estos datos son esencialmente una matriz de todos los sitios de la colección de sitios que se representan como objetos de transferencia de datos con diversas propiedades.</span><span class="sxs-lookup"><span data-stu-id="56ccd-240">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span>

<span data-ttu-id="56ccd-241">A continuación, estos datos se analizan en los `SPO.Models.NavigationNode` objetos definidos anteriormente que usan `Knockout.js` para crear propiedades observables para su uso mediante el enlace de datos de los valores en el código HTML que se ha definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="56ccd-241">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span>

<span data-ttu-id="56ccd-242">A continuación, los objetos se colocan en una matriz de resultados.</span><span class="sxs-lookup"><span data-stu-id="56ccd-242">The objects are then put into a results array.</span></span> <span data-ttu-id="56ccd-243">Esta matriz se analiza en JSON usando knockout y se almacena en el almacenamiento local del explorador para mejorar el rendimiento en futuras cargas de páginas.</span><span class="sxs-lookup"><span data-stu-id="56ccd-243">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="56ccd-244">Ventajas de este enfoque</span><span class="sxs-lookup"><span data-stu-id="56ccd-244">Benefits of this approach</span></span>

<span data-ttu-id="56ccd-245">Una de las principales ventajas de [este enfoque](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) es que, al usar el almacenamiento local de HTML5, la navegación se almacena localmente para el usuario la próxima vez que cargue la página.</span><span class="sxs-lookup"><span data-stu-id="56ccd-245">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="56ccd-246">Obtenemos mejoras de rendimiento principales al usar la API de búsqueda para la navegación estructural; sin embargo, se necesita cierta capacidad técnica para ejecutar y personalizar esta funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="56ccd-246">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span>

<span data-ttu-id="56ccd-247">En la [implementación del ejemplo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), los sitios se ordenan de la misma manera que la navegación estructural de forma integrada; orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="56ccd-247">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="56ccd-248">Si desea desviarse de esta orden, sería más complicado su desarrollo y mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="56ccd-248">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="56ccd-249">Además, este enfoque requiere que se desvíe de las páginas maestras admitidas.</span><span class="sxs-lookup"><span data-stu-id="56ccd-249">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="56ccd-250">Si no se mantiene la página maestra personalizada, el sitio perderá las actualizaciones y las mejoras que Microsoft realiza en las páginas maestras.</span><span class="sxs-lookup"><span data-stu-id="56ccd-250">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="56ccd-251">El [código anterior](#about-the-javascript-file) tiene las siguientes dependencias:</span><span class="sxs-lookup"><span data-stu-id="56ccd-251">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="56ccd-252">jQueryhttps://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="56ccd-252">jQuery - https://jquery.com/</span></span>
- <span data-ttu-id="56ccd-253">KnockoutJS -https://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="56ccd-253">KnockoutJS - https://knockoutjs.com/</span></span>
- <span data-ttu-id="56ccd-254">Linq.js https://linqjs.codeplex.com/ o github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="56ccd-254">Linq.js - https://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="56ccd-255">La versión actual de LinqJS no contiene el método ByHierarchy que se usó en el código anterior y romperá el código de navegación.</span><span class="sxs-lookup"><span data-stu-id="56ccd-255">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="56ccd-256">Para solucionarlo, agregue el método siguiente al archivo de Linq.js antes de la línea `Flatten: function ()` .</span><span class="sxs-lookup"><span data-stu-id="56ccd-256">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```javascript
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);

     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a><span data-ttu-id="56ccd-257">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="56ccd-257">Related topics</span></span>

[<span data-ttu-id="56ccd-258">Información general sobre la navegación administrada en SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="56ccd-258">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

[<span data-ttu-id="56ccd-259">Rendimiento y almacenamiento en caché de navegación estructural</span><span class="sxs-lookup"><span data-stu-id="56ccd-259">Structural navigation caching and performance</span></span>](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)
