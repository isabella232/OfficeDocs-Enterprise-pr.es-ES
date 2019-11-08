---
title: Opciones de navegación para SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: En este artículo se describen las opciones de navegación sitios con la publicación de SharePoint habilitada en SharePoint Online. La elección y configuración de la navegación afectan significativamente al rendimiento y la escalabilidad de los sitios de SharePoint Online. Este artículo no se aplica a los sitios de grupo clásicos.
ms.openlocfilehash: fa180e1904ef57f28e512c6d6ff163f2f4a483ad
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031265"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="53eec-105">Opciones de navegación para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53eec-105">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="53eec-106">En este artículo se describen las opciones de navegación sitios con la publicación de SharePoint habilitada en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="53eec-106">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online.</span></span> <span data-ttu-id="53eec-107">La elección y configuración de la navegación afectan significativamente al rendimiento y la escalabilidad de los sitios de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="53eec-107">The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="53eec-108">Información general</span><span class="sxs-lookup"><span data-stu-id="53eec-108">Overview</span></span>

<span data-ttu-id="53eec-109">La configuración del proveedor de navegación puede afectar significativamente al rendimiento de todo el sitio, y se debe tener en cuenta para elegir un proveedor de navegación y una configuración que se escale con eficacia para los requisitos de un sitio de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="53eec-109">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site.</span></span> <span data-ttu-id="53eec-110">Hay dos proveedores de navegación preparados, así como implementaciones de navegación personalizadas.</span><span class="sxs-lookup"><span data-stu-id="53eec-110">There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="53eec-111">Se recomienda la primera opción, la [**navegación administrada (metadatos)**](#using-managed-navigation-and-metadata-in-sharepoint-online), y es una de las opciones predeterminadas de SharePoint Online; sin embargo, se recomienda deshabilitar el recorte de seguridad a menos que sea necesario.</span><span class="sxs-lookup"><span data-stu-id="53eec-111">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required.</span></span> <span data-ttu-id="53eec-112">El recorte de seguridad está habilitado como configuración segura de forma predeterminada para este proveedor de navegación; sin embargo, muchos sitios no requieren la sobrecarga de recorte de seguridad, ya que los elementos de navegación suelen ser coherentes para todos los usuarios del sitio.</span><span class="sxs-lookup"><span data-stu-id="53eec-112">Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site.</span></span> <span data-ttu-id="53eec-113">Con la configuración recomendada para deshabilitar el recorte de seguridad, este proveedor de navegación no necesita la enumeración de la estructura del sitio y es altamente escalable con un impacto aceptable en el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="53eec-113">With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="53eec-114">La segunda opción, [**navegación estructural**](#using-structural-navigation-in-sharepoint-online), **no es una opción de navegación recomendada en SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="53eec-114">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**.</span></span> <span data-ttu-id="53eec-115">Este proveedor de navegación se diseñó para una topología local con compatibilidad limitada en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="53eec-115">This navigation provider was designed for an on-premises topology has limited support in SharePoint Online.</span></span> <span data-ttu-id="53eec-116">Aunque proporciona un conjunto adicional de funcionalidades en lugar de otras opciones de navegación, estas características, incluidos el recorte de seguridad y la enumeración de la estructura del sitio, tienen un costo de llamadas de servidor excesivas y afectan a la escalabilidad y al rendimiento cuando se usan.</span><span class="sxs-lookup"><span data-stu-id="53eec-116">While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used.</span></span> <span data-ttu-id="53eec-117">Los sitios que usan la navegación estructurada que consumen demasiados recursos pueden estar sujetos a limitación.</span><span class="sxs-lookup"><span data-stu-id="53eec-117">Sites using structured navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="53eec-118">Además de los proveedores de navegación preinstalados, muchos clientes han implementado correctamente implementaciones de navegación personalizadas alternativas.</span><span class="sxs-lookup"><span data-stu-id="53eec-118">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations.</span></span> <span data-ttu-id="53eec-119">Una clase común de implementaciones de navegación personalizadas adopta patrones de diseño representados por el cliente que almacenan una memoria caché local de nodos de navegación.</span><span class="sxs-lookup"><span data-stu-id="53eec-119">One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes.</span></span> <span data-ttu-id="53eec-120">(Vea **[scripting del lado cliente basado en búsquedas](#using-search-driven-client-side-scripting)** en este artículo).</span><span class="sxs-lookup"><span data-stu-id="53eec-120">(See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="53eec-121">Estos proveedores de navegación tienen un par de ventajas clave:</span><span class="sxs-lookup"><span data-stu-id="53eec-121">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="53eec-122">Por lo general, funcionan bien con diseños de página dinámicos.</span><span class="sxs-lookup"><span data-stu-id="53eec-122">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="53eec-123">Son extremadamente escalables y funcionan porque pueden representarse sin costo de recursos (y actualizar en segundo plano después de un tiempo de espera).</span><span class="sxs-lookup"><span data-stu-id="53eec-123">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="53eec-124">Estos proveedores de navegación pueden recuperar datos de navegación mediante varias estrategias, desde configuraciones estáticas simples a varios proveedores de datos dinámicos.</span><span class="sxs-lookup"><span data-stu-id="53eec-124">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="53eec-125">Un ejemplo de un proveedor de datos es usar una **navegación**basada en búsquedas, que permite la flexibilidad para enumerar los nodos de navegación y controlar de forma eficaz el recorte de seguridad.</span><span class="sxs-lookup"><span data-stu-id="53eec-125">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="53eec-126">Hay otras opciones populares para crear **proveedores de navegación personalizados**.</span><span class="sxs-lookup"><span data-stu-id="53eec-126">There are other popular options to build **Custom navigation providers**.</span></span> <span data-ttu-id="53eec-127">Revise [soluciones de navegación para portales de SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) para obtener más información sobre la creación de un proveedor de navegación personalizado.</span><span class="sxs-lookup"><span data-stu-id="53eec-127">Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="53eec-128">Ventajas y desventajas de las opciones de navegación de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53eec-128">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="53eec-129">En la tabla siguiente se resumen las ventajas y los inconvenientes de cada opción.</span><span class="sxs-lookup"><span data-stu-id="53eec-129">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="53eec-130">Navegación administrada</span><span class="sxs-lookup"><span data-stu-id="53eec-130">Managed navigation</span></span>  |<span data-ttu-id="53eec-131">Navegación estructural</span><span class="sxs-lookup"><span data-stu-id="53eec-131">Structural navigation</span></span>  |<span data-ttu-id="53eec-132">Navegación basada en búsquedas</span><span class="sxs-lookup"><span data-stu-id="53eec-132">Search-driven navigation</span></span>  |<span data-ttu-id="53eec-133">Proveedor de navegación personalizada</span><span class="sxs-lookup"><span data-stu-id="53eec-133">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="53eec-134">Ti</span><span class="sxs-lookup"><span data-stu-id="53eec-134">Pros:</span></span><br/><br/><span data-ttu-id="53eec-135">Fácil de mantener</span><span class="sxs-lookup"><span data-stu-id="53eec-135">Easy to maintain</span></span><br/><span data-ttu-id="53eec-136">Opción recomendada</span><span class="sxs-lookup"><span data-stu-id="53eec-136">Recommended option</span></span><br/>     |<span data-ttu-id="53eec-137">Ti</span><span class="sxs-lookup"><span data-stu-id="53eec-137">Pros:</span></span><br/><br/><span data-ttu-id="53eec-138">Fácil de configurar</span><span class="sxs-lookup"><span data-stu-id="53eec-138">Easy to configure</span></span><br/><span data-ttu-id="53eec-139">Seguridad recortada</span><span class="sxs-lookup"><span data-stu-id="53eec-139">Security trimmed</span></span><br/><span data-ttu-id="53eec-140">Se actualiza automáticamente cuando se agrega contenido</span><span class="sxs-lookup"><span data-stu-id="53eec-140">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="53eec-141">Ti</span><span class="sxs-lookup"><span data-stu-id="53eec-141">Pros:</span></span><br/><br/><span data-ttu-id="53eec-142">Seguridad recortada</span><span class="sxs-lookup"><span data-stu-id="53eec-142">Security trimmed</span></span><br/><span data-ttu-id="53eec-143">Se actualiza automáticamente cuando se agregan sitios</span><span class="sxs-lookup"><span data-stu-id="53eec-143">Automatically updates as sites are added</span></span><br/><span data-ttu-id="53eec-144">Tiempo de carga rápida y estructura de navegación en caché local</span><span class="sxs-lookup"><span data-stu-id="53eec-144">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="53eec-145">Ti</span><span class="sxs-lookup"><span data-stu-id="53eec-145">Pros:</span></span><br/><br/><span data-ttu-id="53eec-146">Opción más amplia de opciones disponibles</span><span class="sxs-lookup"><span data-stu-id="53eec-146">Wider choice of options available</span></span><br/><span data-ttu-id="53eec-147">Carga rápida cuando se utiliza correctamente el almacenamiento en caché</span><span class="sxs-lookup"><span data-stu-id="53eec-147">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="53eec-148">Muchas opciones funcionan bien con un diseño de página dinámico</span><span class="sxs-lookup"><span data-stu-id="53eec-148">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="53eec-149">Conos</span><span class="sxs-lookup"><span data-stu-id="53eec-149">Cons:</span></span><br/><br/><span data-ttu-id="53eec-150">No se actualiza automáticamente para reflejar la estructura del sitio</span><span class="sxs-lookup"><span data-stu-id="53eec-150">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="53eec-151">Afecta al rendimiento si se habilita el recorte de seguridad</span><span class="sxs-lookup"><span data-stu-id="53eec-151">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="53eec-152">Conos</span><span class="sxs-lookup"><span data-stu-id="53eec-152">Cons:</span></span><br/><br/><span data-ttu-id="53eec-153">**No recomendado**</span><span class="sxs-lookup"><span data-stu-id="53eec-153">**Not recommended**</span></span><br/><span data-ttu-id="53eec-154">**Impacto en el rendimiento y la escalabilidad**</span><span class="sxs-lookup"><span data-stu-id="53eec-154">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="53eec-155">**Sujeto a la limitación**</span><span class="sxs-lookup"><span data-stu-id="53eec-155">**Subject to throttling**</span></span><br/>|<span data-ttu-id="53eec-156">Conos</span><span class="sxs-lookup"><span data-stu-id="53eec-156">Cons:</span></span><br/><br/><span data-ttu-id="53eec-157">No se pueden ordenar sitios fácilmente</span><span class="sxs-lookup"><span data-stu-id="53eec-157">No ability to easily order sites</span></span><br/><span data-ttu-id="53eec-158">Requiere la personalización de la página maestra (habilidades técnicas necesarias)</span><span class="sxs-lookup"><span data-stu-id="53eec-158">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="53eec-159">Conos</span><span class="sxs-lookup"><span data-stu-id="53eec-159">Cons:</span></span><br/><br/><span data-ttu-id="53eec-160">Se requiere desarrollo personalizado</span><span class="sxs-lookup"><span data-stu-id="53eec-160">Custom development is required</span></span><br/><span data-ttu-id="53eec-161">Se necesita un origen de datos externo o almacenamiento en caché, por ejemplo Azure</span><span class="sxs-lookup"><span data-stu-id="53eec-161">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="53eec-162">La opción más adecuada para su sitio dependerá de los requisitos de su sitio y de su capacidad técnica.</span><span class="sxs-lookup"><span data-stu-id="53eec-162">The most appropriate option for your site will depend on your site requirements and on your technical capability.</span></span> <span data-ttu-id="53eec-163">Si desea un proveedor de navegación listo para usar que sea escalable, la navegación administrada con el recorte de seguridad deshabilitado es una buena opción.</span><span class="sxs-lookup"><span data-stu-id="53eec-163">If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span>

<span data-ttu-id="53eec-164">La opción de navegación administrada se puede mantener mediante la configuración, no implica archivos de personalización de código y es significativamente más rápida que la navegación estructural.</span><span class="sxs-lookup"><span data-stu-id="53eec-164">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation.</span></span> <span data-ttu-id="53eec-165">Si requiere el recorte de seguridad y se siente cómodo con una página maestra personalizada y tiene alguna función en la organización para mantener los cambios que se pueden producir en la página maestra predeterminada para SharePoint Online, la opción basada en búsquedas puede producir una mejor experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="53eec-165">If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience.</span></span> <span data-ttu-id="53eec-166">Si tiene requisitos más complejos, un proveedor de navegación personalizado puede ser la opción correcta.</span><span class="sxs-lookup"><span data-stu-id="53eec-166">If you have more complex requirements, then a custom navigation provider may be the right choice.</span></span> <span data-ttu-id="53eec-167">NO se recomienda la navegación estructural.</span><span class="sxs-lookup"><span data-stu-id="53eec-167">Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="53eec-168">Por último, es importante tener en cuenta que SharePoint está agregando proveedores de navegación adicionales y funcionalidad para arquitecturas de sitio de SharePoint modernas que aprovechan una jerarquía de sitios más acoplada y un modelo de concentrador y radio con sitios concentradores de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="53eec-168">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites.</span></span> <span data-ttu-id="53eec-169">Esto permite lograr muchos escenarios que no requieren el uso de la característica de publicación de SharePoint y estas configuraciones de navegación están optimizadas para la escalabilidad y la latencia en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="53eec-169">This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online.</span></span> <span data-ttu-id="53eec-170">Tenga en cuenta que al aplicar el mismo principio, simplificando la estructura general del sitio de publicación de SharePoint a una estructura más plana, a menudo también mejora el rendimiento y la escala general.</span><span class="sxs-lookup"><span data-stu-id="53eec-170">Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well.</span></span> <span data-ttu-id="53eec-171">Esto significa que en lugar de tener una sola colección de sitios con cientos de sitios (subwebs), un mejor enfoque es disponer de muchas colecciones de sitios con muy pocos subsitios (subwebs).</span><span class="sxs-lookup"><span data-stu-id="53eec-171">What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="53eec-172">Usar la navegación administrada y los metadatos en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53eec-172">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="53eec-173">La navegación administrada es otra opción precreada que puede usar para volver a crear la mayor parte de la funcionalidad como navegación estructural.</span><span class="sxs-lookup"><span data-stu-id="53eec-173">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation.</span></span> <span data-ttu-id="53eec-174">Los metadatos administrados se pueden configurar para que el recorte de seguridad esté habilitado o deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="53eec-174">Managed metadata can be configured to have security trimming enabled or disabled.</span></span> <span data-ttu-id="53eec-175">Cuando se configura con el recorte de seguridad deshabilitado, la navegación administrada es bastante eficiente ya que carga todos los vínculos de navegación con un número constante de llamadas del servidor.</span><span class="sxs-lookup"><span data-stu-id="53eec-175">When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls.</span></span> <span data-ttu-id="53eec-176">La habilitación de la reducción de seguridad, anula algunas de las ventajas de la navegación administrada y los clientes pueden elegir explorar una de las soluciones de navegación personalizadas para obtener una escalabilidad y un rendimiento óptimos.</span><span class="sxs-lookup"><span data-stu-id="53eec-176">Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="53eec-177">Muchos sitios no requieren el recorte de seguridad, ya que la estructura de navegación suele ser coherente para todos los usuarios del sitio.</span><span class="sxs-lookup"><span data-stu-id="53eec-177">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site.</span></span> <span data-ttu-id="53eec-178">Si se deshabilita el recorte de seguridad y se agrega un vínculo a la navegación que no tienen acceso a todos los usuarios, el vínculo seguirá mostrando pero conducirá a un mensaje de acceso denegado.</span><span class="sxs-lookup"><span data-stu-id="53eec-178">If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message.</span></span> <span data-ttu-id="53eec-179">No existe ningún riesgo de acceso involuntario al contenido.</span><span class="sxs-lookup"><span data-stu-id="53eec-179">There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="53eec-180">Cómo implementar la navegación administrada y los resultados</span><span class="sxs-lookup"><span data-stu-id="53eec-180">How to implement managed navigation and the results</span></span>

<span data-ttu-id="53eec-181">Hay varios artículos sobre Docs.Microsoft.com acerca de los detalles de la navegación administrada, por ejemplo, vea [información general sobre la navegación administrada en SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="53eec-181">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="53eec-182">Para implementar la navegación administrada, se configuran los términos con direcciones URL correspondientes a la estructura de navegación del sitio.</span><span class="sxs-lookup"><span data-stu-id="53eec-182">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site.</span></span> <span data-ttu-id="53eec-183">La navegación administrada puede incluso creadosrse manualmente para reemplazar la navegación estructural en muchos casos.</span><span class="sxs-lookup"><span data-stu-id="53eec-183">Managed navigation can even be manually curated to replace structural navigation in many cases.</span></span> <span data-ttu-id="53eec-184">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="53eec-184">For example:</span></span>

![Estructura de sitio de SharePoint Online](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="53eec-186">En el ejemplo siguiente se muestra el rendimiento de la navegación compleja mediante la navegación administrada.</span><span class="sxs-lookup"><span data-stu-id="53eec-186">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Rendimiento de navegación compleja con navegación administrada](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="53eec-188">Usar la navegación administrada de forma coherente mejora el rendimiento comparado con el enfoque de navegación estructural.</span><span class="sxs-lookup"><span data-stu-id="53eec-188">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="53eec-189">Uso de la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53eec-189">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="53eec-190">Esta es la navegación predefinida que se usa de forma predeterminada y es la solución más sencilla, pero, como tal, tiene un equilibrio entre rendimiento caro.</span><span class="sxs-lookup"><span data-stu-id="53eec-190">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off.</span></span> <span data-ttu-id="53eec-191">No requiere personalización y un usuario no técnico también puede agregar elementos, ocultar elementos y administrar la navegación desde la página de configuración fácilmente.</span><span class="sxs-lookup"><span data-stu-id="53eec-191">It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page.</span></span> <span data-ttu-id="53eec-192">Sin embargo, esto también se aplica a la navegación administrada, por lo que se recomienda usar la navegación administrada, ya que también se puede administrar y controlar fácilmente, así como mejorar el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="53eec-192">This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Navegación estructural con la muestra de subsitios seleccionada](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="53eec-194">Activar la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53eec-194">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="53eec-195">Ilustrar cómo se activa el rendimiento de una solución estándar de SharePoint Online con navegación estructural y la opción Mostrar subsitios.</span><span class="sxs-lookup"><span data-stu-id="53eec-195">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on.</span></span> <span data-ttu-id="53eec-196">A continuación se muestra una captura de pantalla de la configuración que se encuentra en la **navegación**de **configuración** \> del sitio de página.</span><span class="sxs-lookup"><span data-stu-id="53eec-196">Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Captura de pantalla que muestra subsitios](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="53eec-198">Analizar el rendimiento de la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="53eec-198">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="53eec-199">Para analizar el rendimiento de una página de SharePoint, use la ficha **red** de las herramientas de desarrollo F12 de Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="53eec-199">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Captura de pantalla que muestra la pestaña Red de herramientas de desarrollo F12](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="53eec-201">En la ficha **red** , haga clic en la página. aspx que se va a cargar y, a continuación, haga clic en la pestaña **detalles** .</span><span class="sxs-lookup"><span data-stu-id="53eec-201">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="53eec-202">![Captura de pantalla que muestra la pestaña Detalles](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="53eec-202">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="53eec-203">Haga clic en **encabezados de respuesta**.</span><span class="sxs-lookup"><span data-stu-id="53eec-203">Click **Response headers**.</span></span> <br/><span data-ttu-id="53eec-204">![Captura de pantalla de la pestaña Detalles](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="53eec-204">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="53eec-205">SharePoint devuelve información de diagnóstico útil en sus encabezados de respuesta.</span><span class="sxs-lookup"><span data-stu-id="53eec-205">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="53eec-206">Uno de los elementos de información más útiles es **SPRequestDuration** , que es el valor, en milisegundos, del tiempo que tardó una solicitud en procesarse en el servidor.</span><span class="sxs-lookup"><span data-stu-id="53eec-206">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> <span data-ttu-id="53eec-207">En la siguiente captura de pantalla, **Mostrar subsitios** está desactivada para la navegación estructural.</span><span class="sxs-lookup"><span data-stu-id="53eec-207">In the following screenshot **show subsites** is unchecked for the structural navigation.</span></span> <span data-ttu-id="53eec-208">Esto significa que solo hay un vínculo a la colección de sitios en la navegación global:</span><span class="sxs-lookup"><span data-stu-id="53eec-208">This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="53eec-209">![Captura de pantalla que muestra los tiempos de carga como duración de solicitud](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="53eec-209">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="53eec-210">La clave **SPRequestDuration** tiene un valor de 245 milisegundos.</span><span class="sxs-lookup"><span data-stu-id="53eec-210">The **SPRequestDuration** key has a value of 245 milliseconds.</span></span> <span data-ttu-id="53eec-211">Esto representa el tiempo que tardó en devolver la solicitud.</span><span class="sxs-lookup"><span data-stu-id="53eec-211">This represents the time it took to return the request.</span></span> <span data-ttu-id="53eec-212">Como solo hay un elemento de navegación en el sitio, esta es una buena prueba de la forma en que SharePoint Online realiza sin una navegación intensiva.</span><span class="sxs-lookup"><span data-stu-id="53eec-212">Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation.</span></span> <span data-ttu-id="53eec-213">En la siguiente captura de pantalla se muestra cómo la adición en los subsitios afecta a esta clave.</span><span class="sxs-lookup"><span data-stu-id="53eec-213">The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="53eec-214">![Captura de pantalla que muestra una duración de solicitud de 2 502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="53eec-214">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="53eec-215">La adición de los subsitios ha aumentado significativamente el tiempo que se tarda en devolver la solicitud de página para este sitio de ejemplo relativamente sencillo.</span><span class="sxs-lookup"><span data-stu-id="53eec-215">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site.</span></span> <span data-ttu-id="53eec-216">Las jerarquías de sitio complejas, incluidas las páginas de navegación, y otras opciones de configuración y topología pueden aumentar drásticamente este impacto aún más.</span><span class="sxs-lookup"><span data-stu-id="53eec-216">Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="53eec-217">Uso de scripting de cliente basado en búsquedas</span><span class="sxs-lookup"><span data-stu-id="53eec-217">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="53eec-218">Mediante la búsqueda, puede aprovechar los índices que se han integrado en el fondo con el rastreo continuo.</span><span class="sxs-lookup"><span data-stu-id="53eec-218">Using search you can leverage the indexes that are built up in the background using continuous crawl.</span></span> <span data-ttu-id="53eec-219">Los resultados de la búsqueda se extraen del índice de búsqueda y los resultados se reducen por seguridad.</span><span class="sxs-lookup"><span data-stu-id="53eec-219">The search results are pulled from the search index and the results are security-trimmed.</span></span> <span data-ttu-id="53eec-220">Esto suele ser más rápido que los proveedores de navegación preparados cuando se requiere el recorte de seguridad.</span><span class="sxs-lookup"><span data-stu-id="53eec-220">This is generally faster than out-of-the-box navigation providers when security trimming is required.</span></span> <span data-ttu-id="53eec-221">Usar la búsqueda para la navegación estructural, sobre todo si tiene una estructura de sitio compleja, reducirá considerablemente el tiempo de carga de la página.</span><span class="sxs-lookup"><span data-stu-id="53eec-221">Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably.</span></span> <span data-ttu-id="53eec-222">La principal ventaja de esto sobre la navegación administrada es que se beneficia de la reducción de seguridad.</span><span class="sxs-lookup"><span data-stu-id="53eec-222">The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="53eec-223">Este enfoque implica la creación de una página maestra personalizada y la sustitución del código de navegación precreado con HTML personalizado.</span><span class="sxs-lookup"><span data-stu-id="53eec-223">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML.</span></span> <span data-ttu-id="53eec-224">Siga este procedimiento descrito en el siguiente ejemplo para reemplazar el código de navegación en el archivo `seattle.html`.</span><span class="sxs-lookup"><span data-stu-id="53eec-224">Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`.</span></span> <span data-ttu-id="53eec-225">En este ejemplo, se abrirá el `seattle.html` archivo y se reemplazará todo el `id=”DeltaTopNavigation”` elemento con código HTML personalizado.</span><span class="sxs-lookup"><span data-stu-id="53eec-225">In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="53eec-226">Ejemplo: reemplazar el código de navegación de precodificación en una página maestra</span><span class="sxs-lookup"><span data-stu-id="53eec-226">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="53eec-227">Navegue a la página Configuración del sitio.</span><span class="sxs-lookup"><span data-stu-id="53eec-227">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="53eec-228">Abra la galería de páginas maestras; para ello, haga clic en **páginas maestras**.</span><span class="sxs-lookup"><span data-stu-id="53eec-228">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="53eec-229">Desde aquí puede navegar por la biblioteca y descargar el archivo `seattle.master`.</span><span class="sxs-lookup"><span data-stu-id="53eec-229">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="53eec-230">Edite el código con un editor de texto y elimine el bloque de código en la siguiente captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="53eec-230">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Eliminar el bloque de código que se muestra](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="53eec-232">Quite el código entre las `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` etiquetas `<\SharePoint:AjaxDelta>` y y reemplácela por el siguiente fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="53eec-232">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

```
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
6. <span data-ttu-id="53eec-233">Reemplace la dirección URL de la etiqueta de anclaje de la imagen de carga al principio, por un vínculo a una imagen de carga en la colección de sitios.</span><span class="sxs-lookup"><span data-stu-id="53eec-233">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection.</span></span> <span data-ttu-id="53eec-234">Después de realizar los cambios, cambie el nombre del archivo y, a continuación, cárguelo en la galería de páginas maestras.</span><span class="sxs-lookup"><span data-stu-id="53eec-234">After you have made the changes, rename the file and then upload it to the master page gallery.</span></span> <span data-ttu-id="53eec-235">Esto genera un nuevo archivo. Master.</span><span class="sxs-lookup"><span data-stu-id="53eec-235">This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="53eec-236">Este HTML es el marcado básico que rellenará los resultados de la búsqueda devueltos desde el código JavaScript.</span><span class="sxs-lookup"><span data-stu-id="53eec-236">This HTML is the basic markup that will be populated by the search results returned from JavaScript code.</span></span> <span data-ttu-id="53eec-237">Tendrá que editar el código para cambiar el valor de var root = "site Collection URL" como se muestra en el siguiente fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="53eec-237">You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="53eec-238">Los resultados se asignan a self. Nodes y una jerarquía se crea a partir de los objetos mediante Linq. js, que asigna el resultado a una matriz self. hierarchy.</span><span class="sxs-lookup"><span data-stu-id="53eec-238">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy.</span></span> <span data-ttu-id="53eec-239">Esta matriz es el objeto que está enlazado al HTML.</span><span class="sxs-lookup"><span data-stu-id="53eec-239">This array is the object that is bound to the HTML.</span></span> <span data-ttu-id="53eec-240">Esto se realiza en la función toggleView () pasando el objeto Self a la función ko. applyBinding ().</span><span class="sxs-lookup"><span data-stu-id="53eec-240">This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="53eec-241">Esto hace que la matriz de jerarquías se enlace al siguiente HTML:</span><span class="sxs-lookup"><span data-stu-id="53eec-241">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="53eec-242">Los controladores de eventos para `mouseenter` y `mouseexit` se agregan a la navegación de nivel superior para controlar los menús desplegables de subsitio que se realizan `addEventsToElements()` en la función.</span><span class="sxs-lookup"><span data-stu-id="53eec-242">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="53eec-243">En nuestro ejemplo de navegación compleja, una carga de página nueva sin el almacenamiento en caché local muestra el tiempo empleado en el servidor se ha reducido de la navegación estructural de Benchmark para obtener un resultado similar al del enfoque de navegación administrada.</span><span class="sxs-lookup"><span data-stu-id="53eec-243">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="53eec-244">Acerca del archivo JavaScript...</span><span class="sxs-lookup"><span data-stu-id="53eec-244">About the JavaScript file...</span></span>

<span data-ttu-id="53eec-245">El archivo JavaScript completo es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="53eec-245">The entire JavaScript file is as follows:</span></span>

```
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

    // ByHierarchy method breaks the sorting in chrome and firefix 
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

<span data-ttu-id="53eec-246">Para resumir el código que se ha mostrado `jQuery $(document).ready` anteriormente en la función `viewModel object` , se ha creado `loadNavigationNodes()` una y, a continuación, se llama a la función en ese objeto.</span><span class="sxs-lookup"><span data-stu-id="53eec-246">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called.</span></span> <span data-ttu-id="53eec-247">Esta función carga la jerarquía de navegación previamente creada almacenada en el almacenamiento local de HTML5 del explorador del cliente o llama a `queryRemoteInterface()`la función.</span><span class="sxs-lookup"><span data-stu-id="53eec-247">This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="53eec-248">`QueryRemoteInterface()`compila una solicitud mediante la `getRequest()` función con el parámetro de consulta definido anteriormente en el script y, a continuación, devuelve datos del servidor.</span><span class="sxs-lookup"><span data-stu-id="53eec-248">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server.</span></span> <span data-ttu-id="53eec-249">Estos datos son esencialmente una matriz de todos los sitios de la colección de sitios que se representan como objetos de transferencia de datos con diversas propiedades.</span><span class="sxs-lookup"><span data-stu-id="53eec-249">This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="53eec-250">A continuación, estos datos se analizan en los `SPO.Models.NavigationNode` objetos definidos anteriormente `Knockout.js` que usan para crear propiedades observables para su uso mediante el enlace de datos de los valores en el código HTML que se ha definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="53eec-250">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="53eec-251">A continuación, los objetos se colocan en una matriz de resultados.</span><span class="sxs-lookup"><span data-stu-id="53eec-251">The objects are then put into a results array.</span></span> <span data-ttu-id="53eec-252">Esta matriz se analiza en JSON usando knockout y se almacena en el almacenamiento local del explorador para mejorar el rendimiento en futuras cargas de páginas.</span><span class="sxs-lookup"><span data-stu-id="53eec-252">This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="53eec-253">Ventajas de este enfoque</span><span class="sxs-lookup"><span data-stu-id="53eec-253">Benefits of this approach</span></span>

<span data-ttu-id="53eec-254">Una de las principales ventajas de [este enfoque](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) es que, al usar el almacenamiento local de HTML5, la navegación se almacena localmente para el usuario la próxima vez que cargue la página.</span><span class="sxs-lookup"><span data-stu-id="53eec-254">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span> <span data-ttu-id="53eec-255">Obtenemos mejoras de rendimiento principales al usar la API de búsqueda para la navegación estructural; sin embargo, se necesita cierta capacidad técnica para ejecutar y personalizar esta funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="53eec-255">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="53eec-256">En la [implementación del ejemplo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), los sitios se ordenan de la misma manera que la navegación estructural de forma integrada; orden alfabético.</span><span class="sxs-lookup"><span data-stu-id="53eec-256">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order.</span></span> <span data-ttu-id="53eec-257">Si desea desviarse de esta orden, sería más complicado su desarrollo y mantenimiento.</span><span class="sxs-lookup"><span data-stu-id="53eec-257">If you wanted to deviate from this order, it would be more complicated to develop and maintain.</span></span> <span data-ttu-id="53eec-258">Además, este enfoque requiere que se desvíe de las páginas maestras admitidas.</span><span class="sxs-lookup"><span data-stu-id="53eec-258">Also, this approach requires you to deviate from the supported master pages.</span></span> <span data-ttu-id="53eec-259">Si no se mantiene la página maestra personalizada, el sitio perderá las actualizaciones y las mejoras que Microsoft realiza en las páginas maestras.</span><span class="sxs-lookup"><span data-stu-id="53eec-259">If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="53eec-260">El [código anterior](#about-the-javascript-file) tiene las siguientes dependencias:</span><span class="sxs-lookup"><span data-stu-id="53eec-260">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="53eec-261">jQueryhttps://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="53eec-261">jQuery - https://jquery.com/</span></span>
- <span data-ttu-id="53eec-262">KnockoutJS -https://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="53eec-262">KnockoutJS - https://knockoutjs.com/</span></span>
- <span data-ttu-id="53eec-263">Linq. js- https://linqjs.codeplex.com/o github.com/neuecc/Linq.js</span><span class="sxs-lookup"><span data-stu-id="53eec-263">Linq.js - https://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="53eec-264">La versión actual de LinqJS no contiene el método ByHierarchy que se usó en el código anterior y romperá el código de navegación.</span><span class="sxs-lookup"><span data-stu-id="53eec-264">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code.</span></span> <span data-ttu-id="53eec-265">Para solucionarlo, agregue el método siguiente al archivo Linq. js antes de la línea `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="53eec-265">To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

```
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
  
## <a name="related-topics"></a><span data-ttu-id="53eec-266">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="53eec-266">Related topics</span></span>

[<span data-ttu-id="53eec-267">Información general sobre la navegación administrada en SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="53eec-267">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

