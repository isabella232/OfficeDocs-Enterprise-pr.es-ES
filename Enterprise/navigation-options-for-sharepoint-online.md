---
title: Opciones de navegación para SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: En este artículo se describe cómo mejorar los tiempos de carga de páginas de SharePoint Online mediante navegación administrada o navegación controlada por la búsqueda en la publicación de clásico.
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542968"
---
# <a name="navigation-options-for-sharepoint-online"></a><span data-ttu-id="39c3e-103">Opciones de navegación para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="39c3e-103">Navigation options for SharePoint Online</span></span>

<span data-ttu-id="39c3e-104">En este artículo se describe cómo mejorar los tiempos de carga de páginas de SharePoint Online mediante navegación administrada o navegación controlada por la búsqueda en la publicación de clásico.</span><span class="sxs-lookup"><span data-stu-id="39c3e-104">This article describes how to improve page load times for SharePoint Online by using managed navigation or search-driven navigation in Classic publishing.</span></span>
  
<span data-ttu-id="39c3e-105">SharePoint Online con publicación clásica habilitada tiene dos áreas de navegación; Navegación global y navegación actual.</span><span class="sxs-lookup"><span data-stu-id="39c3e-105">SharePoint Online with classic publishing enabled has two navigation areas; Global Navigation and Current Navigation.</span></span>
  
<span data-ttu-id="39c3e-106">Navegación global es el menú de navegación superior mientras la navegación actual es el lado o en contexto a izquierda/derecha navegación dependen de la configuración de idioma y la página maestra utilizados.</span><span class="sxs-lookup"><span data-stu-id="39c3e-106">Global navigation is the top navigation menu while Current Navigation is the side or in-context left/right navigation dependent on the language configuration and master page utilized.</span></span>
  
<span data-ttu-id="39c3e-107">Navegación puede afectar negativamente al rendimiento para el Portal completo como a menudo está configurado para su uso de todo el portal y como tal, es un elemento importante de cualquier sitio de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="39c3e-107">Navigation can negatively impact performance for the entire Portal as it is often configured for portal-wide use and as such is an important element of any SharePoint site.</span></span>
  
<span data-ttu-id="39c3e-108">Navegación estructural no es la opción recomendada de navegación en SharePoint Online, tal y como se diseñó para una topología local con el recorte de seguridad y este diseño hace que las llamadas excesiva en el servidor y afecta al rendimiento cuando se usa.</span><span class="sxs-lookup"><span data-stu-id="39c3e-108">Structural navigation is not the recommended navigation option in SharePoint Online as it was designed for an On-premise topology with security trimming and this design causes excessive server calls and impacts performance when it is used.</span></span>
  
<span data-ttu-id="39c3e-p101">Que el diseño ha cambiado con la introducción de los sitios de SharePoint moderno donde moderno tiene una jerarquía de sitios plana simplificado. Esto ha simplificado la navegación con una jerarquía simplificada que ha eliminado los problemas de rendimiento relacionados con la navegación.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p101">That design has changed with the introduction of Modern SharePoint sites where Modern has a simplified flattened site hierarchy. This has simplified navigation with a simplified hierarchy that has eliminated performance issues related to navigation.</span></span>
  
<span data-ttu-id="39c3e-p102">Hay dos opciones de navegación del cuadro principal en SharePoint, así como una tercera, enfoque personalizado basado en búsquedas. Como alternativa, un cuarto y opción bastante popular es crear un proveedor personalizado de navegación. Revise [las soluciones de navegación para portales de SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) para obtener orientación sobre un proveedor de navegación personalizada.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p102">There are two main out-of-the-box navigation options in SharePoint as well as a third, custom, search-driven approach. Alternatively, a fourth and fairly popular option is to build a Custom Navigation Provider. Please review [Navigation solutions for SharePoint Online portals](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) for guidance on a Custom navigation provider.</span></span> 
  
<span data-ttu-id="39c3e-114">Cada opción tiene ventajas e inconvenientes, tal como se describe en la siguiente tabla.</span><span class="sxs-lookup"><span data-stu-id="39c3e-114">Each option has pros and cons as outlined in the following table.</span></span>
  
|<span data-ttu-id="39c3e-115">**Navegación estructural**</span><span class="sxs-lookup"><span data-stu-id="39c3e-115">**Structural navigation**</span></span>|<span data-ttu-id="39c3e-116">**Navegación administrada**</span><span class="sxs-lookup"><span data-stu-id="39c3e-116">**Managed navigation**</span></span>|<span data-ttu-id="39c3e-117">**Navegación controlada por la búsqueda**</span><span class="sxs-lookup"><span data-stu-id="39c3e-117">**Search-driven navigation**</span></span>||<span data-ttu-id="39c3e-118">**Proveedor de navegación personalizada**</span><span class="sxs-lookup"><span data-stu-id="39c3e-118">**Custom Navigation Provider**</span></span>|
|:-----|:-----|:-----|:-----|:-----|
| <span data-ttu-id="39c3e-119">Ventajas:</span><span class="sxs-lookup"><span data-stu-id="39c3e-119">Pros:</span></span>  <br/>  <span data-ttu-id="39c3e-120">Fácil de configurar</span><span class="sxs-lookup"><span data-stu-id="39c3e-120">Easy to configure</span></span>  <br/>  <span data-ttu-id="39c3e-121">Seguridad garantizada</span><span class="sxs-lookup"><span data-stu-id="39c3e-121">Security-trimmed</span></span>  <br/>  <span data-ttu-id="39c3e-122">Se actualiza automáticamente cuando se agregan sitios</span><span class="sxs-lookup"><span data-stu-id="39c3e-122">Automatically updates as sites are added</span></span>  <br/> | <span data-ttu-id="39c3e-123">Ventajas:</span><span class="sxs-lookup"><span data-stu-id="39c3e-123">Pros:</span></span>  <br/>  <span data-ttu-id="39c3e-124">Fácil de mantener</span><span class="sxs-lookup"><span data-stu-id="39c3e-124">Easy to maintain</span></span>  <br/>  <span data-ttu-id="39c3e-125">Opción recomendada</span><span class="sxs-lookup"><span data-stu-id="39c3e-125">Recommended option</span></span>  <br/> | <span data-ttu-id="39c3e-126">Ventajas:</span><span class="sxs-lookup"><span data-stu-id="39c3e-126">Pros:</span></span>  <br/>  <span data-ttu-id="39c3e-127">Seguridad garantizada</span><span class="sxs-lookup"><span data-stu-id="39c3e-127">Security-trimmed</span></span>  <br/>  <span data-ttu-id="39c3e-128">Se actualiza automáticamente cuando se agregan sitios</span><span class="sxs-lookup"><span data-stu-id="39c3e-128">Automatically updates as sites are added</span></span>  <br/>  <span data-ttu-id="39c3e-129">Rápido tiempo de carga y estructura de navegación en caché local</span><span class="sxs-lookup"><span data-stu-id="39c3e-129">Fast loading time and locally cached navigation structure</span></span>  <br/> || <span data-ttu-id="39c3e-130">Ventajas:</span><span class="sxs-lookup"><span data-stu-id="39c3e-130">Pros:</span></span>  <br/>    <br/>  <span data-ttu-id="39c3e-131">Mayor número de opciones / opciones disponibles</span><span class="sxs-lookup"><span data-stu-id="39c3e-131">Wider choice / options available</span></span>  <br/>  <span data-ttu-id="39c3e-132">Cargar Fast al almacenamiento en caché se usa correctamente</span><span class="sxs-lookup"><span data-stu-id="39c3e-132">Fast loading when caching is used correctly</span></span>  <br/> |
| <span data-ttu-id="39c3e-133">Desventajas:</span><span class="sxs-lookup"><span data-stu-id="39c3e-133">Cons:</span></span>  <br/> <span data-ttu-id="39c3e-134">**No se recomienda**</span><span class="sxs-lookup"><span data-stu-id="39c3e-134">**Not recommended**</span></span> <br/> <span data-ttu-id="39c3e-135">**Afecta al rendimiento**</span><span class="sxs-lookup"><span data-stu-id="39c3e-135">**Impacts performance**</span></span> <br/> | <span data-ttu-id="39c3e-136">Desventajas:</span><span class="sxs-lookup"><span data-stu-id="39c3e-136">Cons:</span></span>  <br/>  <span data-ttu-id="39c3e-137">No se actualiza automáticamente para reflejar la estructura del sitio</span><span class="sxs-lookup"><span data-stu-id="39c3e-137">Not automatically updated to reflect site structure</span></span>  <br/>  <span data-ttu-id="39c3e-138">Afecta al rendimiento si está habilitado el recorte de seguridad</span><span class="sxs-lookup"><span data-stu-id="39c3e-138">Impacts performance if security trimming is enabled</span></span>  <br/> | <span data-ttu-id="39c3e-139">Desventajas:</span><span class="sxs-lookup"><span data-stu-id="39c3e-139">Cons:</span></span>  <br/>  <span data-ttu-id="39c3e-140">No se pueden ordenar sitios de forma sencilla</span><span class="sxs-lookup"><span data-stu-id="39c3e-140">No ability to easily order sites</span></span>  <br/>  <span data-ttu-id="39c3e-141">Requiere la personalización de la página maestra (se requieren conocimientos técnicos)</span><span class="sxs-lookup"><span data-stu-id="39c3e-141">Requires customization of the master page (technical skills required)</span></span>  <br/> || <span data-ttu-id="39c3e-142">Desventajas:</span><span class="sxs-lookup"><span data-stu-id="39c3e-142">Cons:</span></span>  <br/>  <span data-ttu-id="39c3e-143">Se requiere desarrollo personalizado</span><span class="sxs-lookup"><span data-stu-id="39c3e-143">Custom development is required</span></span>  <br/>  <span data-ttu-id="39c3e-144">Origen de datos externo / caché almacena es necesario, por ejemplo, Azure</span><span class="sxs-lookup"><span data-stu-id="39c3e-144">External data source / cache stored is needed e.g. Azure</span></span>  <br/> |
   
<span data-ttu-id="39c3e-p103">La opción más adecuada para su sitio dependerá de las necesidades del sitio y en su capacidad técnica. Si está familiarizado con el uso de una página maestra personalizada y tienen la capacidad de algunos en la organización para mantener los cambios que pueden producirse en la página maestra predeterminada para SharePoint Online, la opción controlados por búsqueda generarán la mejor experiencia de usuario. Si desea que un simple término medio entre la navegación estructural de fábrica y búsqueda, a continuación, la navegación administrada es una opción muy buena. Se puede mantener la opción de navegación administrada a través de configuración, no a los archivos de personalización de código y es mucho más rápido que la navegación estructural de cuadro.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p103">The most appropriate option for your site will depend on your site requirements and on your technical capability. If you are comfortable using a custom master page and have some capability in the organization to maintain the changes that may occur in the default master page for SharePoint Online, then the search-driven option will produce the best user experience. If you want a simple middle ground between the out-of-the-box structural navigation and search, then the managed navigation is a very good option. The managed navigation option can be maintained through configuration, does not involve code customization files, and it is significantly faster than the out-of-the-box structural navigation.</span></span>
  
<span data-ttu-id="39c3e-p104">Simplificación de la estructura general de su Portal clásico muy similar a moderno, ayuda a con el rendimiento y escala así como generales. Esto significa que en lugar de tener una única colección de sitios con cientos o miles de sitios (subwebs), un mejor enfoque consiste en tener muchas colecciones de sitios con subsitios muy pocos (subwebs).</span><span class="sxs-lookup"><span data-stu-id="39c3e-p104">Simplifying the overall structure of your Classic Portal much like Modern, helps with overall performance and scale as well. What this means is that instead of having a single Site Collection with hundreds / thousands of sites (subwebs), a better approach is to have many site collections with very few subsites (subwebs).</span></span>
  
<span data-ttu-id="39c3e-151">Proporciona opciones adicionales de escala en el servicio, evita poner todo el contenido en una base de datos grande y en última instancia permite mayor flexibilidad para navegación y lo más importante es que la seguridad.</span><span class="sxs-lookup"><span data-stu-id="39c3e-151">This provides additional scaling options in the service, avoids putting all content into one big database and ultimately allows greater flexibility for navigation and more importantly security.</span></span>
  
## <a name="using-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="39c3e-152">Usar la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="39c3e-152">Using structural navigation in SharePoint Online</span></span>

<span data-ttu-id="39c3e-p105">Esto es el panel de navegación del cuadro usado de forma predeterminada y es la solución más sencilla pero como tal, tiene un equilibrio rendimiento costosos. No requiere ninguna personalización y un usuario no técnico también fácilmente puede agregar elementos, ocultar los elementos y administrar la navegación desde la página de configuración. Esto es sin embargo también true para la navegación administrados por lo que se recomienda utilizar también navegación administrados como que pueden ser fácilmente administrada y controla así como.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p105">This is the out-of-the-box navigation used by default and is the most straightforward solution but as such has an expensive performance trade-off. It does not require any customization and a non-technical user can also easily add items, hide items, and manage the navigation from the settings page. This is however also true for Managed Navigation so it is recommended to use Managed Navigation as that can also be easily managed and controlled as well.</span></span>
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a><span data-ttu-id="39c3e-156">Activar la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="39c3e-156">Turning on structural navigation in SharePoint Online</span></span>

<span data-ttu-id="39c3e-p106">Para ilustrar cómo el rendimiento en una solución de SharePoint Online estándar con navegación estructural y el Mostrar subsitios opción activado. A continuación se captura una pantalla de configuración que se encuentra en la página **Configuración del sitio** \> **navegación**.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p106">To illustrate how the performance in a standard SharePoint Online solution with structural navigation and the show subsites option turned on. Below is a screen shot settings found on the page **Site Settings** \> **Navigation**.</span></span>
  
![Captura de pantalla que muestra subsitios](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a><span data-ttu-id="39c3e-160">Analizar el rendimiento de la navegación estructural en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="39c3e-160">Analyzing structural navigation performance in SharePoint Online</span></span>

<span data-ttu-id="39c3e-161">Para analizar el rendimiento de una página de SharePoint, utilice la ficha **Red** de las herramientas de desarrollo F12 en Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="39c3e-161">To analyze the performance of a SharePoint page use the **Network** tab of the F12 developer tools in Internet Explorer.</span></span> 
  
![Captura de pantalla que muestra la pestaña Red de herramientas de desarrollo F12](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
<span data-ttu-id="39c3e-163">En la ficha **Red**, haga clic en la página .aspx que se está cargando y, a continuación, haga clic en la ficha **Detalles**.</span><span class="sxs-lookup"><span data-stu-id="39c3e-163">On the **Network** tab, click on the .aspx page that is being loaded and then click on the **Details** tab.</span></span> 
  
![Captura de pantalla que muestra la pestaña Detalles](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
<span data-ttu-id="39c3e-165">Haga clic en **Encabezados de respuesta**.</span><span class="sxs-lookup"><span data-stu-id="39c3e-165">Click **Response headers**.</span></span>
  
![Captura de pantalla de la pestaña Detalles](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
<span data-ttu-id="39c3e-p107">SharePoint devuelve la información de diagnóstico útil en sus encabezados de respuesta. Uno de los más útiles es **SPRequestDuration**, que es el valor en milisegundos del tiempo que tardó en procesarse una solicitud en el servidor.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p107">SharePoint returns some useful diagnostic information in its response headers. One of the most useful is **SPRequestDuration** which is the value, in milliseconds, of how long a request took to process on the server.</span></span> 
  
<span data-ttu-id="39c3e-p108">En la pantalla siguiente **Mostrar subsitios** está desactivada para la navegación estructural. Esto significa que hay sólo el vínculo de la colección de sitios en la navegación global:</span><span class="sxs-lookup"><span data-stu-id="39c3e-p108">In the following screen shot **show subsites** is unchecked for the structural navigation. This means that there is only the site collection link in the global navigation:</span></span> 
  
![Captura de pantalla que muestra los tiempos de carga como duración de solicitud](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
<span data-ttu-id="39c3e-p109">La clave de **SPRequestDuration** tiene un valor de 245 milisegundos. Esto representa el tiempo que se tardó en devolver la solicitud. Dado que hay un solo elemento de navegación en el sitio, se trata de un buen rendimiento para cómo SharePoint Online realiza sin navegación gruesa. La captura de pantalla siguiente muestra cómo agregar en los subsitios que afecta a esta clave.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p109">The **SPRequestDuration** key has a value of 245 milliseconds. This represents the time it took to return the request. Since there is only one navigation item on the site, this is a good benchmark for how SharePoint Online performs without heavy navigation. The next screen shot shows how adding in the subsites affects this key.</span></span> 
  
![Captura de pantalla que muestra una duración de solicitud de 2 502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
<span data-ttu-id="39c3e-177">Agregar los subsitios ha aumentado significativamente el tiempo empleado en devolver la solicitud de página.</span><span class="sxs-lookup"><span data-stu-id="39c3e-177">Adding the subsites has significantly increased the time it takes to return the page request.</span></span>
  
<span data-ttu-id="39c3e-178">Las ventajas de usar la navegación estructurada regular es que fácilmente puede organizar el orden, ocultar sitios, agregar páginas, los resultados son restricciones de seguridad, y no se desvían de las páginas maestras compatibles que se usa en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="39c3e-178">The advantages of using the regular structured navigation is that you can easily organize the order, hide sites, add pages, the results are security-trimmed, and you are not deviating from the supported master pages used in SharePoint Online.</span></span>
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a><span data-ttu-id="39c3e-179">Usar navegación administrada y metadatos administrados en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="39c3e-179">Using managed navigation and managed metadata in SharePoint Online</span></span>

<span data-ttu-id="39c3e-180">La navegación administrada es otra opción de fábrica que puede utilizar para volver a crear al mismo tipo de funcionalidad que la navegación estructural.</span><span class="sxs-lookup"><span data-stu-id="39c3e-180">Managed navigation is another out-of-the-box option that you can use to recreate the same sort of functionality as structural navigation.</span></span>
  
<span data-ttu-id="39c3e-p110">La ventaja de usar metadatos administrados es que resulta mucho más rápido para recuperar los datos que el uso de contenido por consulta para crear la navegación del sitio. Aunque es que mucho más rápido no hay ninguna forma de recorte de seguridad los resultados por lo que si un usuario no tiene acceso a un sitio determinado, el vínculo seguirá mostrando pero dará lugar a un mensaje de error.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p110">The advantage of using managed metadata is that it is much faster to retrieve the data than using content by query to build the site navigation. Although it is much faster there is no way to security trim the results so if a user doesn't have access to a given site, the link will still show but will lead to an error message.</span></span>
  
 <span data-ttu-id="39c3e-183">**Cómo implementar la navegación administrada y los resultados**</span><span class="sxs-lookup"><span data-stu-id="39c3e-183">**How to implement managed navigation and the results**</span></span>
  
<span data-ttu-id="39c3e-184">Hay varios artículos de TechNet acerca de los detalles de la navegación administrada, por ejemplo, vea [información general de la navegación administrada en SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span><span class="sxs-lookup"><span data-stu-id="39c3e-184">There are several articles on TechNet about the details of managed navigation, for example, see [Overview of managed navigation in SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).</span></span>
  
<span data-ttu-id="39c3e-p111">Para implementar la navegación administrada, deberá tener permisos de administrador para el almacén de términos. Al configurar términos con direcciones URL que coinciden con la estructura de una colección de sitios, se puede usar la navegación administrada para reemplazar la navegación estructural. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="39c3e-p111">In order to implement managed navigation, you need to have term store administrator permissions. By setting up terms with URLs that match the structure of a site collection, managed navigation can be used to replace structural navigation. For example:</span></span>
  
![Captura de pantalla del ejemplo Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
<span data-ttu-id="39c3e-189">En el ejemplo siguiente se muestra el rendimiento de la navegación compleja mediante navegación administrada.</span><span class="sxs-lookup"><span data-stu-id="39c3e-189">The following example shows the performance of the complex navigation using managed navigation.</span></span>
  
![Captura de pantalla del ejemplo de SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
<span data-ttu-id="39c3e-191">El uso consistente de navegación administrada mejora el rendimiento en comparación con el contenido por enfoque de navegación estructural de consulta.</span><span class="sxs-lookup"><span data-stu-id="39c3e-191">Using managed navigation consistently improves performance compared to the content by query structural navigation approach.</span></span>
  
## <a name="using-search-driven-client-side-scripting"></a><span data-ttu-id="39c3e-192">Usar scripting de cliente por búsqueda</span><span class="sxs-lookup"><span data-stu-id="39c3e-192">Using Search-driven client-side scripting</span></span>

<span data-ttu-id="39c3e-p112">Mediante la búsqueda, se pueden aprovechar los índices que se compilan en segundo plano mediante el rastreo continuo. Esto significa que no existen consultas de contenido intensas. Los resultados de búsqueda se extraen del índice de búsqueda, y los resultados tiene seguridad garantizada. Esto es más rápido que usar consultas de contenido normales. Con la búsqueda de navegación estructural, especialmente si tiene una estructura de sitios compleja, acelerará considerablemente el tiempo de carga de páginas. La principal ventaja de esto con respecto a la navegación administrada es que usted se beneficia con la seguridad garantizada.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p112">Using search you can leverage the indexes that are built up in the background using continuous crawl. This means there are no heavy content queries. The search results are pulled from the search index and the results are security-trimmed. This is faster than using regular content queries. Using search for structural navigation, especially if you have a complex site structure, will speed up page loading time considerably. The main advantage of this over managed navigation is that you benefit from security trimming.</span></span>
  
<span data-ttu-id="39c3e-p113">Este enfoque consiste en crear una página maestra personalizada y reemplazar el código de navegación de fábrica con HTML personalizado. Siga este procedimiento para reemplazar el código de navegación en el archivo seattle.html.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p113">This approach involves creating a custom master page and replacing the out-of-the-box navigation code with custom HTML. Follow this procedure to replace the navigation code in the file seattle.html.</span></span>
  
<span data-ttu-id="39c3e-201">En este ejemplo, se abra el archivo seattle.html y reemplace todo el elemento **id = "DeltaTopNavigation"** con el código HTML personalizado.</span><span class="sxs-lookup"><span data-stu-id="39c3e-201">In this example, you will open the seattle.html file and replace the whole element **id="DeltaTopNavigation"** with the custom HTML code.</span></span> 
  
 <span data-ttu-id="39c3e-202">**Ejemplo: Para reemplazar el código de navegación de fábrica en una página maestra**</span><span class="sxs-lookup"><span data-stu-id="39c3e-202">**Example: To replace the out-of-the-box navigation code in a master page**</span></span>
  
1. <span data-ttu-id="39c3e-203">Vaya a la página **Configuración del sitio**.</span><span class="sxs-lookup"><span data-stu-id="39c3e-203">Navigate to the **Site Settings** page.</span></span> 
    
2. <span data-ttu-id="39c3e-204">Haga clic en **Páginas maestras** para abrir la galería de páginas maestras.</span><span class="sxs-lookup"><span data-stu-id="39c3e-204">Open the master page gallery by clicking **Master Pages**.</span></span>
    
3. <span data-ttu-id="39c3e-205">Desde aquí puede navegar por la biblioteca y descargar el archivo **seattle.master**.</span><span class="sxs-lookup"><span data-stu-id="39c3e-205">From here you can navigate through the library and download the file **seattle.master**.</span></span>
    
4. <span data-ttu-id="39c3e-206">Edite el código con un editor de texto y elimine el bloque de código en la siguiente captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="39c3e-206">Edit the code using a text editor and delete the code block in the following screen shot.</span></span>
    
    ![Captura de pantalla del código de DeltaTopNavigation para eliminar](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. <span data-ttu-id="39c3e-208">Quitar el código entre la \<SharePoint:AjaxDelta id = "DeltaTopNavigation"\> y \<\SharePoint:AjaxDelta\> de etiquetas y reemplácelo con el siguiente fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="39c3e-208">Remove the code between the \<SharePoint:AjaxDelta id="DeltaTopNavigation"\> and \<\SharePoint:AjaxDelta\> tags and replace it with the following snippet:</span></span>
    
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

6. <span data-ttu-id="39c3e-p114">Reemplace la dirección URL en la carga de la imagen etiqueta delimitadora al principio, con un vínculo a una imagen de carga en la colección de sitios. Una vez realizados los cambios, cambie el nombre del archivo y, a continuación, cárguela en la Galería de páginas maestras. Esto genera un nuevo archivo. master.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p114">Replace the URL in the loading image anchor tag at the beginning, with a link to a loading image in your site collection. After you have made the changes, rename the file and then upload it to the master page gallery. This generates a new .master file.</span></span>
    
7. <span data-ttu-id="39c3e-p115">Este código HTML es el marcado básicos que se va a rellenar con los resultados de búsqueda devueltos desde el código JavaScript. Tendrá que modificar el código siguiente para cambiar el valor para el `var root = "site collection URL"` como se muestra en el siguiente fragmento de código:</span><span class="sxs-lookup"><span data-stu-id="39c3e-p115">This HTML is the basic markup that will be populated by the search results returned from JavaScript code. You will need to edit the following code to change the value for the  `var root = "site collection URL"` as demonstrated in the following snippet:</span></span> 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

    <span data-ttu-id="39c3e-214">Todo el archivo JavaScript es de esta manera:</span><span class="sxs-lookup"><span data-stu-id="39c3e-214">The entire JavaScript file is as follows:</span></span>
    
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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     <span data-ttu-id="39c3e-215">$("li.level1").mouseover (función () {</span><span class="sxs-lookup"><span data-stu-id="39c3e-215">$("li.level1").mouseover(function () {</span></span> 
  
<span data-ttu-id="39c3e-216">posición de var = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="39c3e-216">var position = $(this).position();</span></span>
  
<span data-ttu-id="39c3e-217">.find("ul.level2").css $(this) ({ancho: 100, izquierda: position.left + 10, top: 50});</span><span class="sxs-lookup"><span data-stu-id="39c3e-217">$(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });</span></span>
    
     }) 
  
<span data-ttu-id="39c3e-218">.MouseOut (función () {</span><span class="sxs-lookup"><span data-stu-id="39c3e-218">.mouseout(function () {</span></span>
  
<span data-ttu-id="39c3e-219">.find("ul.level2").css $(this) ({izquierdo:-99999, superior: 0});</span><span class="sxs-lookup"><span data-stu-id="39c3e-219">$(this).find("ul.level2").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="39c3e-220">});</span><span class="sxs-lookup"><span data-stu-id="39c3e-220"></span></span>
  
<span data-ttu-id="39c3e-221">$("li.level2").mouseover (función () {</span><span class="sxs-lookup"><span data-stu-id="39c3e-221">$("li.level2").mouseover(function () {</span></span>
  
<span data-ttu-id="39c3e-222">posición de var = $(this).position();</span><span class="sxs-lookup"><span data-stu-id="39c3e-222">var position = $(this).position();</span></span>
  
<span data-ttu-id="39c3e-223">Console.log(JSON.stringify(Position));</span><span class="sxs-lookup"><span data-stu-id="39c3e-223">console.log(JSON.stringify(position));</span></span>
  
<span data-ttu-id="39c3e-224">.find("ul.level3").css $(this) ({ancho: 100, izquierda: position.left + 95, top: position.top});</span><span class="sxs-lookup"><span data-stu-id="39c3e-224">$(this).find("ul.level3").css({ width: 100, left: position.left + 95, top: position.top});</span></span>
    
     }) 
  
<span data-ttu-id="39c3e-225">.MouseOut (función () {</span><span class="sxs-lookup"><span data-stu-id="39c3e-225">.mouseout(function () {</span></span>
  
<span data-ttu-id="39c3e-226">.find("ul.level3").css $(this) ({izquierdo:-99999, superior: 0});</span><span class="sxs-lookup"><span data-stu-id="39c3e-226">$(this).find("ul.level3").css({ left: -99999, top: 0 });</span></span>
  
<span data-ttu-id="39c3e-227">});</span><span class="sxs-lookup"><span data-stu-id="39c3e-227"></span></span>
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. <span data-ttu-id="39c3e-p116">A continuación, se asignan los resultados a la matriz **[self.nodes]** y se crea una jerarquía de fuera de los objetos con linq.js asignar el resultado a una matriz **[self.heirarchy]**. Esta matriz es el objeto que está enlazado el código HTML. Esto se realiza en la función **[toggleView()]** , se pasa el objeto automático a la función **[ko.applyBinding()]** . Esto hace que la matriz de jerarquía enlazar el código HTML siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c3e-p116">Next, the results are assigned to the **[self.nodes]** array and a hierarchy is built out of the objects using linq.js assigning the output to an array **[self.heirarchy]**. This array is the object that is bound to the HTML. This is done in the **[toggleView()]** function by passing the self object to the **[ko.applyBinding()]** function. This then causes the hierarchy array to be bound to the following HTML:</span></span> 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    <span data-ttu-id="39c3e-232">Por último, se agregan los controladores de eventos para **[mouseenter]** y **[mouseexit]** para la navegación de nivel superior para controlar los menús de lista desplegable del subsitio que se realiza en la función **[addEventsToElements()]** .</span><span class="sxs-lookup"><span data-stu-id="39c3e-232">Finally, the event handlers for **[mouseenter]** and **[mouseexit]** are added to the top-level navigation to handle the subsite drop-down menus which is done in the **[addEventsToElements()]** function.</span></span> 
    
    <span data-ttu-id="39c3e-233">Los resultados de la navegación pueden verse en la captura de pantalla siguiente:</span><span class="sxs-lookup"><span data-stu-id="39c3e-233">The results of the navigation can be seen in the screen shot below:</span></span>
    
    ![Captura de pantalla de los resultados de la navegación](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    <span data-ttu-id="39c3e-235">En nuestro ejemplo de navegación compleja, una carga de página nueva sin el almacenamiento en memoria caché local muestra que el tiempo empleado en el servidor se ha reducido con respecto a la navegación estructural de pruebas comparativas para obtener un resultado similar al enfoque de navegación administrada.</span><span class="sxs-lookup"><span data-stu-id="39c3e-235">In our complex navigation example a fresh page load without the local caching shows the time spent on the server has been cut down from the benchmark structural navigation to get a similar result as the managed navigation approach.</span></span>
    
    ![Captura de pantalla de SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    <span data-ttu-id="39c3e-237">Una de las principales ventajas de este enfoque es que mediante el almacenamiento local de HTML5, la navegación se almacena localmente para el usuario la próxima vez que cargue la página.</span><span class="sxs-lookup"><span data-stu-id="39c3e-237">One major benefit of this approach is that by using HTML5 local storage, the navigation is stored locally for the user the next time they load the page.</span></span>
    
<span data-ttu-id="39c3e-p117">Obtenemos mejoras de rendimiento muy importantes del uso de la API de búsqueda para la navegación estructural. Sin embargo, esto requiere capacidad técnica para ejecutar y personalizar esta funcionalidad. En la implementación de ejemplo, los sitios se ordenan de la misma forma que la navegación estructural de fábrica (por orden alfabético). Si deseara usar otro orden, sería más complicado desarrollar y mantener. Además, este enfoque requiere que se desvíe de las páginas maestras compatibles. Si no se mantiene la página maestra personalizada, el sitio perderá las actualizaciones y mejoras que Microsoft realice en las páginas maestras.</span><span class="sxs-lookup"><span data-stu-id="39c3e-p117">We get major performance improvements from using the search API for structural navigation; however, it takes some technical capability to execute and customize this functionality. In the example implementation, the sites are ordered in the same way as the out-of-the-box structural navigation; alphabetical order. If you wanted to deviate from this order, it would be more complicated to develop and maintain. Also, this approach requires you to deviate from the supported master pages. If the custom master page is not maintained, your site will miss out on updates and improvements that Microsoft makes to the master pages.</span></span>
  
<span data-ttu-id="39c3e-243">El código anterior tiene las siguientes dependencias:</span><span class="sxs-lookup"><span data-stu-id="39c3e-243">The above code has the following dependencies:</span></span>
  
- <span data-ttu-id="39c3e-244">jQuery-[http://jquery.com/](http://jquery.com/)</span><span class="sxs-lookup"><span data-stu-id="39c3e-244">jQuery - [http://jquery.com/](http://jquery.com/)</span></span>
    
- <span data-ttu-id="39c3e-245">KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)</span><span class="sxs-lookup"><span data-stu-id="39c3e-245">KnockoutJS - [http://knockoutjs.com/](http://knockoutjs.com/)</span></span>
    
- <span data-ttu-id="39c3e-246">LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), o [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span><span class="sxs-lookup"><span data-stu-id="39c3e-246">Linq.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), or [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)</span></span>
    
<span data-ttu-id="39c3e-p118">La versión actual de LinqJS no contiene el método ByHierarchy que se usa en el código anterior y, interrumpirá el código de navegación. Para solucionar este problema, agregue el método siguiente al archivo Linq.js antes de la línea "Flatten: función ()".</span><span class="sxs-lookup"><span data-stu-id="39c3e-p118">The current version of LinqJS does not contain the ByHierarchy method used in the above code and will break the navigation code. To fix this, add the following method to the Linq.js file before the line "Flatten: function ()".</span></span>
  
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


