---
title: Opciones de navegación para SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Este artículo describen los sitios de las opciones de navegación con publicación de SharePoint habilitado en SharePoint Online. La elección y la configuración de navegación afectará de forma significativa el rendimiento y la escalabilidad de sitios de SharePoint Online.
ms.openlocfilehash: 5a190ca643c20b6644ca1eecdac2a4a2e281a09e
ms.sourcegitcommit: 45633b7034ee98d0cd833db9743f283b638237f4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "26547182"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="233e9-104">Opciones de navegación para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="233e9-104">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="233e9-p102">Este artículo describen los sitios de las opciones de navegación con publicación de SharePoint habilitado en SharePoint Online. La elección y la configuración de navegación afectará de forma significativa el rendimiento y la escalabilidad de sitios de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="233e9-p102">This article describes navigation options sites with SharePoint Publishing enabled in SharePoint Online. The choice and configuration of navigation significantly impacts the performance and scalability of sites in SharePoint Online.</span></span>

## <a name="overview"></a><span data-ttu-id="233e9-107">Información general</span><span class="sxs-lookup"><span data-stu-id="233e9-107">Overview</span></span>

<span data-ttu-id="233e9-p103">Configuración del proveedor de navegación puede afectar significativamente al rendimiento de todo el sitio, y deben tener en cuenta consideraciones cuidado para seleccionar un proveedor de navegación y la configuración que escala de forma eficaz los requisitos de un sitio de SharePoint. Hay dos proveedores de navegación del cuadro, así como las implementaciones de navegación personalizada.</span><span class="sxs-lookup"><span data-stu-id="233e9-p103">Navigation provider configuration can significantly impact performance for the entire site, and careful consideration must be taken to pick a navigation provider and configuration that scales effectively for the requirements of a SharePoint site. There are two out-of-the-box navigation providers, as well as custom navigation implementations.</span></span>

<span data-ttu-id="233e9-p104">La primera opción, [**navegación Managed (metadatos)**](#using-managed-navigation-and-metadata-in-sharepoint-online), se recomienda y es una de las opciones predeterminadas en SharePoint Online; Sin embargo, se recomienda deshabilitar el recorte de seguridad a menos que requiera. Recorte de seguridad está habilitado como una configuración de seguro de forma predeterminada para este proveedor de navegación; Sin embargo, muchos sitios no requieren la sobrecarga de la restricción de seguridad ya que los elementos de navegación a menudo son coherentes para todos los usuarios del sitio. Con la configuración recomendada para deshabilitar el recorte de seguridad, este proveedor de navegación no requiere enumerar la estructura del sitio y es altamente escalable con el impacto de rendimiento aceptable.</span><span class="sxs-lookup"><span data-stu-id="233e9-p104">The first option, [**Managed (Metadata) navigation**](#using-managed-navigation-and-metadata-in-sharepoint-online), is recommended, and is one of the default options in SharePoint Online; however, we recommend that security trimming be disabled unless required. Security trimming is enabled as a secure-by-default setting for this navigation provider; however, many sites do not require the overhead of security trimming since navigation elements often are consistent for all users of the site. With the recommended configuration to disable security trimming, this navigation provider does not require enumerating site structure and is highly scalable with acceptable performance impact.</span></span>

<span data-ttu-id="233e9-p105">La segunda opción, [**navegación estructural**](#using-structural-navigation-in-sharepoint-online), **es no una opción recomendada de navegación en SharePoint Online**. Este proveedor de navegación se diseñó para una topología local está limitado soporte en SharePoint Online. Mientras proporciona algunas conjunto adicional de capacidades en comparación con otras opciones de navegación, estas características, incluidos el recorte de seguridad y enumeración de estructura del sitio, tiene un costo de las llamadas de excesiva en el servidor y el rendimiento y escalabilidad de impactos cuando se usa. Sitios mediante navegación structed que consuman demasiados recursos pueden ser sujetas a limitación.</span><span class="sxs-lookup"><span data-stu-id="233e9-p105">The second option, [**Structural navigation**](#using-structural-navigation-in-sharepoint-online), **is NOT a recommended navigation option in SharePoint Online**. This navigation provider was designed for an on-premises topology has limited support in SharePoint Online. While it provides some additional set of capabilities versus other navigation options, these features, including security trimming and site structure enumeration, comes at a cost of excessive server calls and impacts scalability and performance when it is used. Sites using structed navigation that consume excessive resources may be subject to throttling.</span></span>

<span data-ttu-id="233e9-p106">Además de los proveedores de navegación del cuadro, muchos clientes han implementado correctamente las implementaciones de navegación personalizada alternativo. Una clase común de las implementaciones de navegación personalizada adopta patrones de diseño representado por el cliente que almacenan una memoria caché local de los nodos de navegación. (Vea **[secuencias de comandos de cliente basado en búsquedas](#using-search-driven-client-side-scripting)** en este artículo).</span><span class="sxs-lookup"><span data-stu-id="233e9-p106">In addition to the out-of-the-box navigation providers, many customers have successfully implemented alternative custom navigation implementations. One common class of custom navigation implementations embraces client-rendered design patterns that store a local cache of navigation nodes. (See **[Search-driven client-side scripting](#using-search-driven-client-side-scripting)** in this article.)</span></span>

<span data-ttu-id="233e9-120">Estos proveedores de navegación tienen un par de ventajas claves:</span><span class="sxs-lookup"><span data-stu-id="233e9-120">These navigation providers have a couple of key advantages:</span></span> 
- <span data-ttu-id="233e9-121">Por lo general funcionan bien con los diseños de página con capacidad de respuesta.</span><span class="sxs-lookup"><span data-stu-id="233e9-121">They generally work well with responsive page designs.</span></span>
- <span data-ttu-id="233e9-122">Son extremadamente escalables y eficaz porque puede presentarse sin costo del recurso (y la actualización en segundo plano después de un tiempo de espera).</span><span class="sxs-lookup"><span data-stu-id="233e9-122">They are extremely scalable and performant because they can render with no resource cost (and refresh in the background after a timeout).</span></span> 
- <span data-ttu-id="233e9-123">Estos proveedores de navegación pueden recuperar datos de navegación mediante diversas estrategias, comprendido entre las configuraciones estáticas simples para varios proveedores de datos dinámicos.</span><span class="sxs-lookup"><span data-stu-id="233e9-123">These navigation providers can retrieve navigation data using various strategies, ranging from simple static configurations to various dynamic data providers.</span></span> 

<span data-ttu-id="233e9-124">Un ejemplo de un proveedor de datos es usar una **navegación controlada por la búsqueda**, que permite flexibilidad para enumerar los nodos de navegación y controlar el recorte de forma eficaz de seguridad.</span><span class="sxs-lookup"><span data-stu-id="233e9-124">An example of a data provider is to use a **Search-driven navigation**, which allows flexibility for enumerating navigation nodes and handling security trimming efficiently.</span></span> 

<span data-ttu-id="233e9-p107">Hay otras opciones más populares para crear **proveedores de navegación personalizada**. Revise [las soluciones de navegación para portales de SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) para obtener más información sobre la creación de un proveedor personalizado de navegación.</span><span class="sxs-lookup"><span data-stu-id="233e9-p107">There are other popular options to build **Custom navigation providers**. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) for further guidance on building a Custom navigation provider.</span></span>
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a><span data-ttu-id="233e9-127">Opciones de navegación pros y contras de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="233e9-127">Pros and Cons of SharePoint Online navigation options</span></span>

<span data-ttu-id="233e9-128">En la siguiente tabla se resume las ventajas y desventajas de cada opción.</span><span class="sxs-lookup"><span data-stu-id="233e9-128">The following table summarizes the pros and cons of each option.</span></span> 


|<span data-ttu-id="233e9-129">Navegación administrada</span><span class="sxs-lookup"><span data-stu-id="233e9-129">Managed navigation</span></span>  |<span data-ttu-id="233e9-130">Navegación estructural</span><span class="sxs-lookup"><span data-stu-id="233e9-130">Structural navigation</span></span>  |<span data-ttu-id="233e9-131">Navegación por búsqueda</span><span class="sxs-lookup"><span data-stu-id="233e9-131">Search-driven navigation</span></span>  |<span data-ttu-id="233e9-132">Proveedor de navegación personalizada</span><span class="sxs-lookup"><span data-stu-id="233e9-132">Custom-navigation provider</span></span>  |
|---------|---------|---------|---------|
|<span data-ttu-id="233e9-133">Ventajas:</span><span class="sxs-lookup"><span data-stu-id="233e9-133">Pros:</span></span><br/><br/><span data-ttu-id="233e9-134">Fácil de mantener</span><span class="sxs-lookup"><span data-stu-id="233e9-134">Easy to maintain</span></span><br/><span data-ttu-id="233e9-135">Opción recomendada</span><span class="sxs-lookup"><span data-stu-id="233e9-135">Recommended option</span></span><br/>     |<span data-ttu-id="233e9-136">Ventajas:</span><span class="sxs-lookup"><span data-stu-id="233e9-136">Pros:</span></span><br/><br/><span data-ttu-id="233e9-137">Fácil de configurar</span><span class="sxs-lookup"><span data-stu-id="233e9-137">Easy to configure</span></span><br/><span data-ttu-id="233e9-138">Restricciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="233e9-138">Security trimmed</span></span><br/><span data-ttu-id="233e9-139">Se actualiza automáticamente cuando se agrega contenido</span><span class="sxs-lookup"><span data-stu-id="233e9-139">Automatically updates as content is added</span></span><br/>|<span data-ttu-id="233e9-140">Ventajas:</span><span class="sxs-lookup"><span data-stu-id="233e9-140">Pros:</span></span><br/><br/><span data-ttu-id="233e9-141">Restricciones de seguridad</span><span class="sxs-lookup"><span data-stu-id="233e9-141">Security trimmed</span></span><br/><span data-ttu-id="233e9-142">Se actualiza automáticamente cuando se agregan sitios</span><span class="sxs-lookup"><span data-stu-id="233e9-142">Automatically updates as sites are added</span></span><br/><span data-ttu-id="233e9-143">Rápido tiempo de carga y estructura de navegación en caché local</span><span class="sxs-lookup"><span data-stu-id="233e9-143">Fast loading time and locally cached navigation structure</span></span><br/>|<span data-ttu-id="233e9-144">Ventajas:</span><span class="sxs-lookup"><span data-stu-id="233e9-144">Pros:</span></span><br/><br/><span data-ttu-id="233e9-145">Más amplia gama de opciones disponibles</span><span class="sxs-lookup"><span data-stu-id="233e9-145">Wider choice of options available</span></span><br/><span data-ttu-id="233e9-146">Cargar Fast al almacenamiento en caché se usa correctamente</span><span class="sxs-lookup"><span data-stu-id="233e9-146">Fast loading when caching is used correctly</span></span><br/><span data-ttu-id="233e9-147">Muchas opciones funcionan bien con diseño de página con capacidad de respuesta</span><span class="sxs-lookup"><span data-stu-id="233e9-147">Many options work well with responsive page design</span></span><br/>|
|<span data-ttu-id="233e9-148">Desventajas:</span><span class="sxs-lookup"><span data-stu-id="233e9-148">Cons:</span></span><br/><br/><span data-ttu-id="233e9-149">No se actualiza automáticamente para reflejar la estructura del sitio</span><span class="sxs-lookup"><span data-stu-id="233e9-149">Not automatically updated to reflect site structure</span></span><br/><span data-ttu-id="233e9-150">Afecta al rendimiento si está habilitado el recorte de seguridad</span><span class="sxs-lookup"><span data-stu-id="233e9-150">Impacts performance if security trimming is enabled</span></span><br/>|<span data-ttu-id="233e9-151">Desventajas:</span><span class="sxs-lookup"><span data-stu-id="233e9-151">Cons:</span></span><br/><br/><span data-ttu-id="233e9-152">**No se recomienda**</span><span class="sxs-lookup"><span data-stu-id="233e9-152">**Not recommended**</span></span><br/><span data-ttu-id="233e9-153">**Afecta al rendimiento y escalabilidad**</span><span class="sxs-lookup"><span data-stu-id="233e9-153">**Impacts performance and scalability**</span></span><br/><span data-ttu-id="233e9-154">**Sujeto a limitación**</span><span class="sxs-lookup"><span data-stu-id="233e9-154">**Subject to throttling**</span></span><br/>|<span data-ttu-id="233e9-155">Desventajas:</span><span class="sxs-lookup"><span data-stu-id="233e9-155">Cons:</span></span><br/><br/><span data-ttu-id="233e9-156">No se pueden ordenar sitios de forma sencilla</span><span class="sxs-lookup"><span data-stu-id="233e9-156">No ability to easily order sites</span></span><br/><span data-ttu-id="233e9-157">Requiere la personalización de la página maestra (se requieren conocimientos técnicos)</span><span class="sxs-lookup"><span data-stu-id="233e9-157">Requires customization of the master page (technical skills required)</span></span><br/>|<span data-ttu-id="233e9-158">Desventajas:</span><span class="sxs-lookup"><span data-stu-id="233e9-158">Cons:</span></span><br/><br/><span data-ttu-id="233e9-159">Se requiere desarrollo personalizado</span><span class="sxs-lookup"><span data-stu-id="233e9-159">Custom development is required</span></span><br/><span data-ttu-id="233e9-160">Origen de datos externo / caché almacena es necesario, por ejemplo, Azure</span><span class="sxs-lookup"><span data-stu-id="233e9-160">External data source / cache stored is needed e.g. Azure</span></span><br/>|

<span data-ttu-id="233e9-p108">La opción más adecuada para su sitio dependerá de las necesidades del sitio y en su capacidad técnica. Si desea que un proveedor de navegación de cuadro escalable, navegación administrada con el recorte de seguridad deshabilitado es una opción muy buena.</span><span class="sxs-lookup"><span data-stu-id="233e9-p108">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you want a scalable out-of-the-box navigation provider, then Managed navigation with security trimming disabled is a very good option.</span></span> 

<span data-ttu-id="233e9-p109">Se puede mantener la opción de navegación administrada a través de configuración, no a los archivos de personalización de código y es mucho más rápido que la navegación estructural. Si requieren el recorte de seguridad y está familiarizado con el uso de una página maestra personalizada y tienen capacidad de algunos en la organización para mantener los cambios que pueden producirse en la página maestra predeterminada para SharePoint Online, la opción de búsqueda puede producir una mejor experiencia del usuario. Si tiene requisitos más complejos, un proveedor de navegación personalizada puede ser la opción más adecuada. NO se recomienda navegación estructural.</span><span class="sxs-lookup"><span data-stu-id="233e9-p109">The Managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than structural navigation. If you require security trimming and are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the Search-driven option may produce a better user experience. If you have more complex requirements, then a custom navigation provider may be the right choice. Structural navigation is NOT recommended.</span></span>

<span data-ttu-id="233e9-p110">Por último, es importante tener en cuenta que SharePoint va a agregar proveedores de navegación adicionales y funciones para arquitecturas modernas de sitio de SharePoint aprovechamiento de una jerarquía de sitios más plana y un modelo de concentrador y radio con los sitios de concentradores de SharePoint. Esto permite muchos escenarios lograr que no requieren el uso de la característica de publicación de SharePoint, y estas configuraciones de navegación están optimizadas para la escalabilidad y la latencia dentro de SharePoint Online. Tenga en cuenta que a menudo el mismo principio - simplificación de la estructura general de su sitio de publicación de SharePoint a una estructura más plana, la aplicación ayuda a con el rendimiento general y escalar así como. Esto significa que en lugar de tener una única colección de sitios con cientos de sitios (subwebs), un mejor enfoque es tiene muchas colecciones de sitios con subsitios muy pocos (subwebs).</span><span class="sxs-lookup"><span data-stu-id="233e9-p110">Finally, it’s important to note that SharePoint is adding additional navigation providers and functionality for modern SharePoint site architectures leveraging a more flattened site hierarchy and a hub-and-spoke model with SharePoint hub sites. This allows many scenarios to be achieved that do NOT require the use of SharePoint Publishing feature, and these navigation configurations are optimized for scalability and latency within SharePoint Online. Note that applying the same principle - simplifying the overall structure of your SharePoint Publishing site to a flatter structure, often helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a><span data-ttu-id="233e9-171">Uso de metadatos y navegación administrada en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="233e9-171">Using managed navigation and metadata in SharePoint Online</span></span>

<span data-ttu-id="233e9-p111">Navegación administrada es otra opción del cuadro que puede usar para volver a crear la mayor parte de la misma funcionalidad que la navegación estructural. Metadatos administrados pueden configurarse para que el recorte de seguridad está habilitada o deshabilitada. Cuando se configura con el recorte de seguridad deshabilitado, navegación administrada es bastante eficaz como que carga todos los vínculos de navegación con un número constante de llamadas de servidor. Habilitación de la restricción de seguridad, sin embargo, niega algunas de las ventajas de la navegación administrada y los clientes pueden elegir explorar una de las soluciones de navegación personalizada para un rendimiento óptimo y la escalabilidad.</span><span class="sxs-lookup"><span data-stu-id="233e9-p111">Managed navigation is another out-of-the-box option that you can use to recreate most of the same functionality as structural navigation. Managed metadata can be configured to have security trimming enabled or disabled. When configured with security trimming disabled, managed navigation is fairly efficient as it loads all the navigation links with a constant number of server calls. Enabling security trimming, however, negates some of the advantages of managed navigation, and customers may choose to explore one of the custom navigation solutions for optimal performance and scalability.</span></span>

<span data-ttu-id="233e9-p112">Muchos sitios no requieren el recorte de seguridad, como la estructura de navegación a menudo es coherente para todos los usuarios del sitio. Si está deshabilitado el recorte de seguridad y se agrega un vínculo a la navegación que no todos los usuarios tienen acceso a, el vínculo seguirá mostrando pero dará lugar a un mensaje de acceso denegado. No hay ningún riesgo de accidental acceso al contenido.</span><span class="sxs-lookup"><span data-stu-id="233e9-p112">Many sites do not require security trimming, as the navigation structure is often consistent for all users of the site. If security trimming is disabled and a link is added to navigation that not all users have access to, the link will still show but will lead to an access denied message. There is no risk of inadvertent access to the content.</span></span>

### <a name="how-to-implement-managed-navigation-and-the-results"></a><span data-ttu-id="233e9-179">Cómo implementar la navegación administrada y los resultados</span><span class="sxs-lookup"><span data-stu-id="233e9-179">How to implement managed navigation and the results</span></span>

<span data-ttu-id="233e9-180">Hay varios artículos en Docs.Microsoft.com acerca de los detalles de la navegación administrada, por ejemplo, vea [información general de la navegación administrada en SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span><span class="sxs-lookup"><span data-stu-id="233e9-180">There are several articles on Docs.Microsoft.com about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).</span></span>

<span data-ttu-id="233e9-p113">Para implementar la navegación administrada, configure las condiciones con las direcciones URL correspondiente a la estructura de navegación del sitio. Navegación administrada incluso puede ser manualmente curated que va a reemplazar navegación estructural en muchos casos. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="233e9-p113">In order to implement managed navigation, you set up terms with URLs corresponding to the navigation structure of  the site. Managed navigation can even be manually curated to replace structural navigation in many cases. For example:</span></span>

![Estructura del sitio de SharePoint Online](media/SPONavOptionsListOfSites.png)

<span data-ttu-id="233e9-185">En el ejemplo siguiente se muestra el rendimiento de la navegación compleja mediante navegación administrada.</span><span class="sxs-lookup"><span data-stu-id="233e9-185">The following example shows the performance of the complex navigation using managed navigation.</span></span>

![Rendimiento de navegación complejas con navegación administrada](media/SPONavOptionsComplexNavPerf.png)

<span data-ttu-id="233e9-187">Usar la navegación administrada coherentemente mejora el rendimiento en comparación con el enfoque de navegación estructural.</span><span class="sxs-lookup"><span data-stu-id="233e9-187">Using managed navigation consistently improves performance compared to the structural navigation approach.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="233e9-188">Usar la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="233e9-188">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="233e9-p114">Esto es el panel de navegación del cuadro usado de forma predeterminada y es la solución más sencilla pero como tal, tiene un equilibrio rendimiento costosos. No requiere ninguna personalización y un usuario no técnico también fácilmente puede agregar elementos, ocultar los elementos y administrar la navegación desde la página de configuración. Esto es sin embargo también true para la navegación administrados por lo que se recomienda utilizar la navegación administrados como que también se puede fácilmente administrada y controla así como con mejor performance.</span><span class="sxs-lookup"><span data-stu-id="233e9-p114">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well with improved performance.</span></span>

![Navegación estructural con Mostrar subsitios seleccionado](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="233e9-193">Activar la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="233e9-193">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="233e9-p115">Para ilustrar cómo el rendimiento en una solución de SharePoint Online estándar con navegación estructural y el Mostrar subsitios opción activado. A continuación se presenta una captura de pantalla de configuración que se encuentra en la página **Configuración del sitio** \> **navegación**.</span><span class="sxs-lookup"><span data-stu-id="233e9-p115">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screenshot of settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Captura de pantalla que muestra subsitios](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="233e9-197">Analizar el rendimiento de la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="233e9-197">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="233e9-198">Para analizar el rendimiento de una página de SharePoint, use la ficha de **red** de las herramientas de desarrollo F12 en Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="233e9-198">To analyze the performance of a SharePoint page, use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Captura de pantalla que muestra la pestaña Red de herramientas de desarrollo F12](media/SPONavOptionsNetworks.png)
  
1. <span data-ttu-id="233e9-200">En la ficha **Red**, haga clic en la página .aspx que se está cargando y, a continuación, haga clic en la ficha **Detalles**.</span><span class="sxs-lookup"><span data-stu-id="233e9-200">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span><br/> <span data-ttu-id="233e9-201">![Captura de pantalla que muestra la pestaña Detalles](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span><span class="sxs-lookup"><span data-stu-id="233e9-201">![Screenshot showing the details tab](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)</span></span><br/>
2. <span data-ttu-id="233e9-202">Haga clic en **Encabezados de respuesta**.</span><span class="sxs-lookup"><span data-stu-id="233e9-202">Click **Response headers**.</span></span> <br/><span data-ttu-id="233e9-203">![Captura de pantalla de la pestaña Detalles](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span><span class="sxs-lookup"><span data-stu-id="233e9-203">![Screenshot of Details tab](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)</span></span><br/><span data-ttu-id="233e9-204">SharePoint devuelve la información de diagnóstico útil en sus encabezados de respuesta.</span><span class="sxs-lookup"><span data-stu-id="233e9-204">SharePoint returns some useful diagnostic information in its response headers.</span></span> 
3. <span data-ttu-id="233e9-p116">Uno de los elementos más útiles de información es **SPRequestDuration** , que es el valor, en milisegundos, de una solicitud de cuánto tardó en procesarse en el servidor. En la siguiente captura de pantalla está desactivada para la navegación estructural **Mostrar subsitios** . Esto significa que hay sólo el vínculo de la colección de sitios en la navegación global:</span><span class="sxs-lookup"><span data-stu-id="233e9-p116">One of the most useful pieces of information is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server. In the following screenshot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span><br/><span data-ttu-id="233e9-208">![Captura de pantalla que muestra los tiempos de carga como duración de solicitud](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span><span class="sxs-lookup"><span data-stu-id="233e9-208">![Screenshot showing load times as request duration](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)</span></span><br/>
4. <span data-ttu-id="233e9-p117">La clave de **SPRequestDuration** tiene un valor de 245 milisegundos. Esto representa el tiempo que se tardó en devolver la solicitud. Dado que hay un solo elemento de navegación en el sitio, se trata de un buen rendimiento para cómo SharePoint Online realiza sin navegación gruesa. La captura de pantalla siguiente muestra cómo agregar en los subsitios que afecta a esta clave.</span><span class="sxs-lookup"><span data-stu-id="233e9-p117">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span><br/><span data-ttu-id="233e9-213">![Captura de pantalla que muestra una duración de solicitud de 2 502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span><span class="sxs-lookup"><span data-stu-id="233e9-213">![Screenshot showing a request duration of 2502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)</span></span><br/>
  
<span data-ttu-id="233e9-p118">Adición de los subsitios ha aumentado considerablemente el tiempo necesario para devolver la solicitud de página para este sitio de ejemplo es relativamente simple. Jerarquías de sitios complejos, incluidas las páginas de navegación y otras opciones de topología y configuración pueden aumentar considerablemente este impacto aún más.</span><span class="sxs-lookup"><span data-stu-id="233e9-p118">Adding the subsites has significantly increased the time it takes to return the page request for this relatively simple sample site. Complex site hierarchies, including pages in navigation, and other configuration and topology options can dramatically increase this impact even further.</span></span>

## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="233e9-216">Usar scripting de cliente por búsqueda</span><span class="sxs-lookup"><span data-stu-id="233e9-216">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="233e9-p119">Uso de búsqueda puede aprovechar los índices que se crean en segundo plano mediante el rastreo continuo. Los resultados de búsqueda se extraen del índice de búsqueda y los resultados son restricciones de seguridad. Esto es generalmente más rápido que los proveedores de navegación del cuadro cuando se necesita la reducción de seguridad. Uso de búsqueda para la navegación estructural, especialmente si tiene una estructura de sitio complejo, va a acelerar considerablemente en tiempo de carga de página. La principal ventaja de esta a través de navegación administrada es que se benefician de recorte de seguridad.</span><span class="sxs-lookup"><span data-stu-id="233e9-p119">Using search you can leverage the indexes that are built up in the background using continuous crawl. The search results are pulled from the search index and the results are security-trimmed. This is generally faster than out-of-the-box navigation providers when security trimming is required. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>

<span data-ttu-id="233e9-p120">Este enfoque implica la creación de una página maestra personalizada y reemplazar el código de navegación del cuadro con código HTML personalizado. Siga este procedimiento descrito en el siguiente ejemplo para reemplazar el código de navegación en el archivo `seattle.html`. En este ejemplo, se abrirá la `seattle.html` de archivos y reemplace todo el elemento `id=”DeltaTopNavigation”` con el código HTML personalizado.</span><span class="sxs-lookup"><span data-stu-id="233e9-p120">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure outlined in the following example to replace the navigation code in the file `seattle.html`. In this example, you will open the `seattle.html` file and replace the whole element `id=”DeltaTopNavigation”` with custom HTML code.</span></span>

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a><span data-ttu-id="233e9-225">Ejemplo: Reemplace el código de navegación del cuadro en una página maestra</span><span class="sxs-lookup"><span data-stu-id="233e9-225">Example: Replace the out-of-the-box navigation code in a master page</span></span>

1.  <span data-ttu-id="233e9-226">Vaya a la página Configuración del sitio.</span><span class="sxs-lookup"><span data-stu-id="233e9-226">Navigate to the Site Settings page.</span></span>
2.  <span data-ttu-id="233e9-227">Haga clic en **Páginas maestras** para abrir la galería de páginas maestras.</span><span class="sxs-lookup"><span data-stu-id="233e9-227">Open the master page gallery by clicking **Master Pages**.</span></span>
3.  <span data-ttu-id="233e9-228">Desde aquí puede navegar por la biblioteca y descargue el archivo `seattle.master`.</span><span class="sxs-lookup"><span data-stu-id="233e9-228">From here you can navigate through the library and download the file `seattle.master`.</span></span>
4.  <span data-ttu-id="233e9-229">Edite el código con un editor de texto y elimine el bloque de código en la siguiente captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="233e9-229">Edit the code using a text editor and delete the code block in the following screen shot.</span></span><br/>![Eliminar el bloque de código que se muestra](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. <span data-ttu-id="233e9-231">Quitar el código entre la `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` y `<\SharePoint:AjaxDelta>` de etiquetas y reemplácelo con el siguiente fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="233e9-231">Remove the code between the `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` and `<\SharePoint:AjaxDelta>` tags and replace it with the following snippet:</span></span><br/>

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
6. <span data-ttu-id="233e9-p121">Reemplace la dirección URL en la carga de la imagen etiqueta delimitadora al principio, con un vínculo a una imagen de carga en la colección de sitios. Una vez realizados los cambios, cambie el nombre del archivo y, a continuación, cárguela en la Galería de páginas maestras. Esto genera un nuevo archivo. master.</span><span class="sxs-lookup"><span data-stu-id="233e9-p121">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span><br/>
7. <span data-ttu-id="233e9-p122">Este código HTML es el marcado básicos que se va a rellenar con los resultados de búsqueda devueltos desde el código JavaScript. Tendrá que modificar el código para cambiar el valor de raíz de var = "dirección URL de la colección de sitios" como se muestra en el siguiente fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="233e9-p122">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the code to change the value for var root = “site collection URL” as demonstrated in the following snippet:</span></span><br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. <span data-ttu-id="233e9-p123">Los resultados se asignan a la matriz de self.nodes y se crea una jerarquía de fuera de los objetos con linq.js asignar el resultado a una matriz self.hierarchy. Esta matriz es el objeto que está enlazado el código HTML. Esto se realiza en la función toggleView(), pasando el objeto automático a la función ko.applyBinding().</span><span class="sxs-lookup"><span data-stu-id="233e9-p123">The results are assigned to the self.nodes array and a hierarchy is built out of the objects using linq.js assigning the output to an array self.hierarchy. This array is the object that is bound to the HTML. This is done in the toggleView() function by passing the self object to the ko.applyBinding() function.</span></span><br/><span data-ttu-id="233e9-240">Esto hace que la matriz de jerarquía enlazar el código HTML siguiente:</span><span class="sxs-lookup"><span data-stu-id="233e9-240">This then causes the hierarchy array to be bound to the following HTML:</span></span><br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

<span data-ttu-id="233e9-241">Los controladores de eventos para `mouseenter` y `mouseexit` se agregan a la navegación de nivel superior para controlar los menús de lista desplegable del subsitio que se realiza en el `addEventsToElements()` (función).</span><span class="sxs-lookup"><span data-stu-id="233e9-241">The event handlers for `mouseenter` and `mouseexit` are added to the top-level navigation to handle the subsite drop-down menus which is done in the `addEventsToElements()` function.</span></span>

<span data-ttu-id="233e9-242">En nuestro ejemplo de navegación complejas, una página en blanco se carga sin tener que el almacenamiento en caché local se muestra el tiempo empleado en el servidor ha cortado hacia abajo en la barra de navegación estructural del banco de pruebas para obtener un resultado similar como el enfoque de navegación administrada.</span><span class="sxs-lookup"><span data-stu-id="233e9-242">In our complex navigation example, a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>

### <a name="about-the-javascript-file"></a><span data-ttu-id="233e9-243">Acerca del archivo JavaScript...</span><span class="sxs-lookup"><span data-stu-id="233e9-243">About the JavaScript file...</span></span>

<span data-ttu-id="233e9-244">Todo el archivo JavaScript es de esta manera:</span><span class="sxs-lookup"><span data-stu-id="233e9-244">The entire JavaScript file is as follows:</span></span>

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

<span data-ttu-id="233e9-p124">Para resumir el código mostrado anteriormente en el `jQuery $(document).ready` función hay un `viewModel object` creado y, a continuación, el `loadNavigationNodes()` se llama a la función en ese objeto. Esta función carga ya sea la jerarquía de navegación generado anteriormente almacenada en el almacenamiento local de HTML5 del explorador del cliente o llama a la función `queryRemoteInterface()`.</span><span class="sxs-lookup"><span data-stu-id="233e9-p124">To summarize the code shown above in the `jQuery $(document).ready` function there is a `viewModel object` created and then the `loadNavigationNodes()` function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function `queryRemoteInterface()`.</span></span>

<span data-ttu-id="233e9-p125">`QueryRemoteInterface()`genera una solicitud utilizando la `getRequest()` función con el parámetro de consulta definida anteriormente en la secuencia de comandos y, a continuación, devuelve datos desde el servidor. Estos datos están esencialmente una matriz de todos los sitios de la colección de sitios que se representan como objetos de transferencia de datos con varias propiedades.</span><span class="sxs-lookup"><span data-stu-id="233e9-p125">`QueryRemoteInterface()` builds a request using the `getRequest()` function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties.</span></span> 

<span data-ttu-id="233e9-249">A continuación, se analizan estos datos en el que se han definido previamente `SPO.Models.NavigationNode` objetos que utilizan `Knockout.js` para crear propiedades perceptible para su uso por datos de enlace de los valores en el código HTML que se ha definido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="233e9-249">This data is then parsed into the previously defined `SPO.Models.NavigationNode` objects which use `Knockout.js` to create observable properties for use by data binding the values into the HTML that we defined earlier.</span></span> 

<span data-ttu-id="233e9-p126">Los objetos, a continuación, se colocan en una matriz de resultados. Esta matriz se analiza en JSON con cobertura y se almacena en el almacenamiento de explorador local para mejorar el rendimiento en cargas de página futuras.</span><span class="sxs-lookup"><span data-stu-id="233e9-p126">The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="233e9-252">Ventajas de este enfoque</span><span class="sxs-lookup"><span data-stu-id="233e9-252">Benefits of this approach</span></span>

<span data-ttu-id="233e9-p127">Una de las principal ventajas de [este enfoque](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) es que mediante el uso de almacenamiento local de HTML5, el panel de navegación se almacena localmente para el usuario la próxima vez que carga la página. Se obtienen las mejoras de rendimiento principales de uso de la API de búsqueda para la navegación estructural; Sin embargo, se tarda algunos capacidad técnica para ejecutar y personalizar esta funcionalidad.</span><span class="sxs-lookup"><span data-stu-id="233e9-p127">One major benefit of [this approach](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page. We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality.</span></span> 

<span data-ttu-id="233e9-p128">En la [implementación de ejemplo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), los sitios se ordenan en la misma manera que la navegación estructural del cuadro; orden alfabético. Si desea que se desvían de este orden, sería más complicado desarrollar y mantener. Además, este enfoque requiere que se desvían de las páginas maestras compatibles. Si no se mantiene la página principal personalizada, el sitio se no participar en las actualizaciones y mejoras que Microsoft pone a las páginas maestras.</span><span class="sxs-lookup"><span data-stu-id="233e9-p128">In the [example implementation](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>

<span data-ttu-id="233e9-259">[Por encima del código](#about-the-javascript-file) presenta las siguientes dependencias:</span><span class="sxs-lookup"><span data-stu-id="233e9-259">The [above code](#about-the-javascript-file) has the following dependencies:</span></span>

- <span data-ttu-id="233e9-260">jQuery-http://jquery.com/</span><span class="sxs-lookup"><span data-stu-id="233e9-260">jQuery - http://jquery.com/</span></span>
- <span data-ttu-id="233e9-261">KnockoutJS-http://knockoutjs.com/</span><span class="sxs-lookup"><span data-stu-id="233e9-261">KnockoutJS - http://knockoutjs.com/</span></span>
- <span data-ttu-id="233e9-262">LINQ.js - http://linqjs.codeplex.com/, o github.com/neuecc/linq.js</span><span class="sxs-lookup"><span data-stu-id="233e9-262">Linq.js - http://linqjs.codeplex.com/, or github.com/neuecc/linq.js</span></span>

<span data-ttu-id="233e9-p129">La versión actual de LinqJS no contiene el método ByHierarchy que se usa en el código anterior y, interrumpirá el código de navegación. Para solucionar este problema, agregue el método siguiente al archivo Linq.js antes de la línea `Flatten: function ()`.</span><span class="sxs-lookup"><span data-stu-id="233e9-p129">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line `Flatten: function ()`.</span></span>

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
  
## <a name="related-topics"></a><span data-ttu-id="233e9-265">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="233e9-265">Related topics</span></span>

[<span data-ttu-id="233e9-266">Información general sobre la navegación administrada en SharePoint Server</span><span class="sxs-lookup"><span data-stu-id="233e9-266">Overview of managed navigation in SharePoint Server</span></span>](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

