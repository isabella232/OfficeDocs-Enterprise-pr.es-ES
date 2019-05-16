---
title: Introducción al ajuste del rendimiento para SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: En este artículo se explica qué aspectos específicos debe tener en cuenta al diseñar páginas para obtener el mejor rendimiento en SharePoint Online.
ms.openlocfilehash: 4743364f6e8a1e84800085d0875abad84491780b
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067216"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="b6dcc-103">Introducción al ajuste del rendimiento para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="b6dcc-104">En este artículo se explica qué aspectos específicos debe tener en cuenta al diseñar páginas para obtener el mejor rendimiento en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
     
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="b6dcc-105">Métricas de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-105">SharePoint Online metrics</span></span>

<span data-ttu-id="b6dcc-106">Las siguientes métricas generales para SharePoint Online proporcionan datos del mundo real sobre el rendimiento:</span><span class="sxs-lookup"><span data-stu-id="b6dcc-106">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="b6dcc-107">Velocidad de carga de páginas</span><span class="sxs-lookup"><span data-stu-id="b6dcc-107">How fast pages load</span></span>
    
- <span data-ttu-id="b6dcc-108">Número de viajes de ida y vuelta necesarios por página</span><span class="sxs-lookup"><span data-stu-id="b6dcc-108">How many round trips required per page</span></span>
    
- <span data-ttu-id="b6dcc-109">Problemas con el servicio</span><span class="sxs-lookup"><span data-stu-id="b6dcc-109">Issues with the service</span></span>
    
- <span data-ttu-id="b6dcc-110">Otras cosas que causan una degradación del rendimiento</span><span class="sxs-lookup"><span data-stu-id="b6dcc-110">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="b6dcc-111">Se han alcanzado conclusiones a causa de los datos</span><span class="sxs-lookup"><span data-stu-id="b6dcc-111">Conclusions reached because of the data</span></span>

<span data-ttu-id="b6dcc-112">Los datos nos dicen:</span><span class="sxs-lookup"><span data-stu-id="b6dcc-112">The data tells us:</span></span>
  
- <span data-ttu-id="b6dcc-113">La mayoría de las páginas se ejecutan correctamente en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-113">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="b6dcc-114">Las páginas no personalizadas se cargan muy rápidamente.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-114">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="b6dcc-115">OneDrive para la empresa, los sitios de grupo y las páginas del sistema, como _ layouts, etc., se cargan rápidamente.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-115">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="b6dcc-116">El 1% más lento de las páginas de SharePoint Online tarda más de 5.000 milisegundos en cargarse.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-116">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="b6dcc-117">Una prueba comparativa sencilla que puede usar sería medir el rendimiento comparando el tiempo de carga de su propio portal con el tiempo de carga de la Página principal de OneDrive para la empresa, ya que usa pocas características personalizadas.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-117">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features.</span></span> <span data-ttu-id="b6dcc-118">Por lo general, este será el primer paso que le pedirá que complete la solución de problemas de rendimiento de la red.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-118">This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="b6dcc-119">Usar una cuenta de usuario estándar al comprobar el rendimiento</span><span class="sxs-lookup"><span data-stu-id="b6dcc-119">Use a standard user account when checking performance</span></span>

<span data-ttu-id="b6dcc-120">Un administrador de la colección de sitios, el propietario del sitio, el editor o el colaborador pertenecen a grupos de seguridad adicionales, tienen permisos adicionales y, por tanto, tienen elementos adicionales que SharePoint carga en una página.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-120">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="b6dcc-121">Esto es aplicable a SharePoint local y SharePoint Online, pero en un escenario local las diferencias no se apreciarán tan fácilmente como en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-121">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="b6dcc-122">Para evaluar correctamente la forma en que se realizará una página para los usuarios, debe usar una cuenta de usuario estándar para evitar cargar los controles de creación y el tráfico adicional relacionado con los grupos de seguridad.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-122">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="b6dcc-123">Categorías de conexión para ajustar el rendimiento</span><span class="sxs-lookup"><span data-stu-id="b6dcc-123">Connection categories for performance tuning</span></span>

<span data-ttu-id="b6dcc-124">Puede clasificar las conexiones entre el servidor y el usuario en tres componentes principales.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-124">You can categorize the connections between the server and the user into three main components.</span></span> <span data-ttu-id="b6dcc-125">Tenga en cuenta lo que debe tener en el diseño de páginas de SharePoint Online para obtener información sobre los tiempos de carga.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-125">Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="b6dcc-126">**Servidor** de Los servidores que hospeda Microsoft en los centros de recursos.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-126">**Server** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="b6dcc-127">**Red** La red de Microsoft, Internet y su red local entre el centro de recursos y los usuarios.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-127">**Network** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="b6dcc-128">**Explorador** Dónde se carga la página.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-128">**Browser** Where the page is loaded.</span></span>
    
<span data-ttu-id="b6dcc-129">Dentro de estas tres conexiones, normalmente hay cinco motivos por los que se produce un 95% de páginas lentas.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-129">Within these three connections there are typically five reasons that cause 95% of slow pages.</span></span> <span data-ttu-id="b6dcc-130">Cada uno de estos motivos se describe en este artículo:</span><span class="sxs-lookup"><span data-stu-id="b6dcc-130">Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="b6dcc-131">Problemas de navegación</span><span class="sxs-lookup"><span data-stu-id="b6dcc-131">Navigation issues</span></span>
    
- <span data-ttu-id="b6dcc-132">Resumen de contenido</span><span class="sxs-lookup"><span data-stu-id="b6dcc-132">Content roll up</span></span>
    
- <span data-ttu-id="b6dcc-133">Archivos grandes</span><span class="sxs-lookup"><span data-stu-id="b6dcc-133">Large files</span></span>
    
- <span data-ttu-id="b6dcc-134">Muchas solicitudes al servidor</span><span class="sxs-lookup"><span data-stu-id="b6dcc-134">Many requests to the server</span></span>
    
- <span data-ttu-id="b6dcc-135">Procesamiento de elementos Web</span><span class="sxs-lookup"><span data-stu-id="b6dcc-135">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="b6dcc-136">Conexión de servidor</span><span class="sxs-lookup"><span data-stu-id="b6dcc-136">Server connection</span></span>

<span data-ttu-id="b6dcc-137">Muchos de los problemas que afectan al rendimiento con SharePoint local también se aplican a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-137">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="b6dcc-138">Como cabría esperar, tiene mucho más control sobre el rendimiento de los servidores con SharePoint local.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-138">As you would expect, you have far more control over how servers perform with on-premises SharePoint.</span></span> <span data-ttu-id="b6dcc-139">Con las cosas de SharePoint Online es un poco diferente.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-139">With SharePoint Online things are a little different.</span></span> <span data-ttu-id="b6dcc-140">Cuanto más trabajo realice un servidor, más tiempo se tardará en representar una página.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-140">The more work you make a server do, the longer it takes to render a page.</span></span> <span data-ttu-id="b6dcc-141">Con SharePoint, el mayor culpable de este aspecto son las páginas complejas con varios elementos Web.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-141">With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="b6dcc-142">SharePoint Server local</span><span class="sxs-lookup"><span data-stu-id="b6dcc-142">SharePoint Server on-premises</span></span>
  
![Captura de pantalla del servidor local](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="b6dcc-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-144">SharePoint Online</span></span>
  
![Captura de pantalla del servidor en línea](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="b6dcc-146">Con SharePoint Online, algunas solicitudes de página pueden acabar, en realidad, en llamar a varios servidores.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-146">With SharePoint Online, certain page requests may actually end up calling multiple servers.</span></span> <span data-ttu-id="b6dcc-147">Podría acabar con una matriz de solicitudes entre servidores para una solicitud individual.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-147">You could end up with a matrix of requests between servers for an individual request.</span></span> <span data-ttu-id="b6dcc-148">Estas interacciones son costosas desde el punto de vista de carga de páginas y harán que sean más lentas.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-148">These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="b6dcc-149">Algunos ejemplos de estas interacciones de servidor a servidor son:</span><span class="sxs-lookup"><span data-stu-id="b6dcc-149">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="b6dcc-150">Servidores web a SQL Server</span><span class="sxs-lookup"><span data-stu-id="b6dcc-150">Web to SQL Servers</span></span>
    
- <span data-ttu-id="b6dcc-151">Web a servidores de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="b6dcc-151">Web to application servers</span></span>
    
<span data-ttu-id="b6dcc-152">Lo otro que puede ralentizar las interacciones del servidor son las faltas de caché.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-152">The other thing that can slow down server interactions is cache misses.</span></span> <span data-ttu-id="b6dcc-153">A diferencia de SharePoint local, hay muy poca probabilidad de que llegue al mismo servidor para una página que ha visitado anteriormente; Esto hace que el almacenamiento en caché de objetos sea obsoleto.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-153">Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="b6dcc-154">Conexión de red </span><span class="sxs-lookup"><span data-stu-id="b6dcc-154">Network connection</span></span>

<span data-ttu-id="b6dcc-155">Con SharePoint local que no hace uso de una WAN, puede usar una conexión de alta velocidad entre el centro de recursos y los usuarios finales.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-155">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users.</span></span> <span data-ttu-id="b6dcc-156">Por lo general, las cosas son fáciles de administrar desde el punto de vista de la red.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-156">Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="b6dcc-157">Con SharePoint Online, hay algunos factores más que hay que tener en cuenta; por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="b6dcc-157">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="b6dcc-158">The Microsoft Network</span><span class="sxs-lookup"><span data-stu-id="b6dcc-158">The Microsoft network</span></span>
    
- <span data-ttu-id="b6dcc-159">Internet</span><span class="sxs-lookup"><span data-stu-id="b6dcc-159">The Internet</span></span>
    
- <span data-ttu-id="b6dcc-160">El ISP</span><span class="sxs-lookup"><span data-stu-id="b6dcc-160">The ISP</span></span>
    
<span data-ttu-id="b6dcc-161">Independientemente de la versión de SharePoint (y la red) que use, lo que normalmente hará que la red esté ocupada incluye:</span><span class="sxs-lookup"><span data-stu-id="b6dcc-161">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="b6dcc-162">Gran carga</span><span class="sxs-lookup"><span data-stu-id="b6dcc-162">Large payload</span></span>
    
- <span data-ttu-id="b6dcc-163">Muchos archivos</span><span class="sxs-lookup"><span data-stu-id="b6dcc-163">Many files</span></span>
    
- <span data-ttu-id="b6dcc-164">Gran distancia física con el servidor</span><span class="sxs-lookup"><span data-stu-id="b6dcc-164">Large physical distance to the server</span></span>
    
<span data-ttu-id="b6dcc-165">Una característica que puede aprovechar en SharePoint Online es la red de entrega de contenido (CDN) de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-165">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network).</span></span> <span data-ttu-id="b6dcc-166">Una CDN es básicamente una colección distribuida de servidores implementados en varios centros de recursos.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-166">A CDN is basically a distributed collection of servers deployed across multiple datacenters.</span></span> <span data-ttu-id="b6dcc-167">Con una red CDN, el contenido de las páginas puede alojarse en un servidor cercano al cliente incluso si el cliente se encuentra alejado del servidor de SharePoint de origen.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-167">With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server.</span></span> <span data-ttu-id="b6dcc-168">Microsoft lo utilizará más en el futuro para almacenar instancias locales de páginas que no se pueden personalizar, por ejemplo, la Página principal de administración de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-168">Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page.</span></span> <span data-ttu-id="b6dcc-169">Para obtener más información acerca de las CDN, vea [redes de entrega de contenido](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span><span class="sxs-lookup"><span data-stu-id="b6dcc-169">For more information about CDNs, see [Content delivery networks](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).</span></span>
  
<span data-ttu-id="b6dcc-170">Algo que necesita tener en cuenta pero que no puede hacer mucho por es la velocidad de conexión de su ISP.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-170">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP.</span></span> <span data-ttu-id="b6dcc-171">Una herramienta de prueba de velocidad simple le dirá la velocidad de conexión.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-171">A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="b6dcc-172">Conexión con el explorador</span><span class="sxs-lookup"><span data-stu-id="b6dcc-172">Browser connection</span></span>

<span data-ttu-id="b6dcc-173">Hay algunos factores que se deben tener en cuenta con los exploradores Web desde el punto de vista del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-173">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="b6dcc-174">La visita de páginas complejas afectará al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-174">Visiting complex pages will affect performance.</span></span> <span data-ttu-id="b6dcc-175">La mayoría de los exploradores solo tienen una caché pequeña (alrededor de 90MB), mientras que la página web promedio suele encontrase a 1,6 MB.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-175">Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB.</span></span> <span data-ttu-id="b6dcc-176">Esto no tarda mucho en llegar a usarse.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-176">This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="b6dcc-177">El ancho de banda también puede ser un problema.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-177">Bandwidth may also be an issue.</span></span> <span data-ttu-id="b6dcc-178">Por ejemplo, si un usuario ve vídeos en otra sesión, el rendimiento de la página de SharePoint se verá afectado.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-178">For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page.</span></span> <span data-ttu-id="b6dcc-179">Aunque no se puede impedir que los usuarios transmitan contenido multimedia, puede controlar la forma en que se cargará una página para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-179">While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="b6dcc-180">Consulte los siguientes artículos para conocer las distintas técnicas de personalización de páginas de SharePoint Online y otros procedimientos recomendados para ayudarle a conseguir un rendimiento óptimo.</span><span class="sxs-lookup"><span data-stu-id="b6dcc-180">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="b6dcc-181">Opciones de navegación para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-181">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="b6dcc-182">Usar la herramienta de diagnóstico de página para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-182">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="b6dcc-183">Optimización de imágenes para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-183">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="b6dcc-184">Retrasar la carga de imágenes y JavaScript en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-184">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="b6dcc-185">Minificación y agrupación en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-185">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="b6dcc-186">Usar redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="b6dcc-186">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="b6dcc-187">Usar el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido para mejorar el rendimiento en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-187">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="b6dcc-188">Planeamiento de capacidad y pruebas de carga en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-188">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="b6dcc-189">Diagnosticar problemas de rendimiento con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-189">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="b6dcc-190">Usar la memoria caché de objetos con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-190">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="b6dcc-191">Cómo: Evitar estar limitado o bloqueado en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="b6dcc-191">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

