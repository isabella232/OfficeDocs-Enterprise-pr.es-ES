---
title: Introducción al ajuste del rendimiento para SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: En este artículo se explica qué aspectos específicos que debe tener en cuenta cuando se diseñan las páginas para obtener el mejor rendimiento en SharePoint Online.
ms.openlocfilehash: 96aeec19a6b582d0dc8701cd2e99329ec8ce156b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542709"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a><span data-ttu-id="615cc-103">Introducción al ajuste del rendimiento para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-103">Introduction to performance tuning for SharePoint Online</span></span>

<span data-ttu-id="615cc-104">En este artículo se explica qué aspectos específicos que debe tener en cuenta cuando se diseñan las páginas para obtener el mejor rendimiento en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="615cc-104">This article explains what specific aspects you need to consider when designing pages for best performance in SharePoint Online.</span></span>
  
## <a name="in-this-article"></a><span data-ttu-id="615cc-105">En este artículo</span><span class="sxs-lookup"><span data-stu-id="615cc-105">In this article</span></span>

- <span data-ttu-id="615cc-106">[Métricas de SharePoint Online](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) y [conclusiones alcanza debido a los datos](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span><span class="sxs-lookup"><span data-stu-id="615cc-106">[SharePoint Online metrics](introduction-to-performance-tuning-for-sharepoint-online.md#spometrics) and [Conclusions reached because of the data](introduction-to-performance-tuning-for-sharepoint-online.md#data)</span></span>
    
- [<span data-ttu-id="615cc-107">Use una cuenta de usuario estándar al rendimiento</span><span class="sxs-lookup"><span data-stu-id="615cc-107">Use a standard user account when checking performance</span></span>](introduction-to-performance-tuning-for-sharepoint-online.md#standuser)
    
- <span data-ttu-id="615cc-108">[Categorías de conexión para el ajuste del rendimiento](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [conexión de servidor](introduction-to-performance-tuning-for-sharepoint-online.md#server), [conexión de red](introduction-to-performance-tuning-for-sharepoint-online.md#network)y [la conexión de explorador](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span><span class="sxs-lookup"><span data-stu-id="615cc-108">[Connection categories for performance tuning](introduction-to-performance-tuning-for-sharepoint-online.md#connect): [Server connection](introduction-to-performance-tuning-for-sharepoint-online.md#server), [Network connection](introduction-to-performance-tuning-for-sharepoint-online.md#network), and [Browser connection](introduction-to-performance-tuning-for-sharepoint-online.md#browser)</span></span>
    
## <a name="sharepoint-online-metrics"></a><span data-ttu-id="615cc-109">Métricas de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-109">SharePoint Online metrics</span></span>
<span data-ttu-id="615cc-110"><a name="spometrics"> </a></span><span class="sxs-lookup"><span data-stu-id="615cc-110"></span></span>

<span data-ttu-id="615cc-111">Las siguientes métricas amplias para SharePoint Online proporcionan datos reales sobre el rendimiento:</span><span class="sxs-lookup"><span data-stu-id="615cc-111">The following broad metrics for SharePoint Online provide real world data about performance:</span></span>
  
- <span data-ttu-id="615cc-112">La velocidad de carga de páginas</span><span class="sxs-lookup"><span data-stu-id="615cc-112">How fast pages load</span></span>
    
- <span data-ttu-id="615cc-113">Cuántos recorridos de idas y vuelta se requieren por página</span><span class="sxs-lookup"><span data-stu-id="615cc-113">How many round trips required per page</span></span>
    
- <span data-ttu-id="615cc-114">Problemas con el servicio</span><span class="sxs-lookup"><span data-stu-id="615cc-114">Issues with the service</span></span>
    
- <span data-ttu-id="615cc-115">Otras cuestiones que provocan una degradación del rendimiento</span><span class="sxs-lookup"><span data-stu-id="615cc-115">Other things that cause performance degradation</span></span>
    
### <a name="conclusions-reached-because-of-the-data"></a><span data-ttu-id="615cc-116">Conclusiones debido a los datos</span><span class="sxs-lookup"><span data-stu-id="615cc-116">Conclusions reached because of the data</span></span>
<span data-ttu-id="615cc-117"><a name="data"> </a></span><span class="sxs-lookup"><span data-stu-id="615cc-117"></span></span>

<span data-ttu-id="615cc-118">Los datos indican lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="615cc-118">The data tells us:</span></span>
  
- <span data-ttu-id="615cc-119">La mayoría de las páginas tienen un buen rendimiento en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="615cc-119">Most of the pages perform well on SharePoint Online.</span></span>
    
- <span data-ttu-id="615cc-120">Las páginas que no han sido personalizadas se cargan muy rápidamente.</span><span class="sxs-lookup"><span data-stu-id="615cc-120">Non-customized pages load very quickly.</span></span>
    
- <span data-ttu-id="615cc-121">OneDrive para la Empresa, sitios de grupo y páginas del sistema, como _layouts, etc., se cargan rápidamente.</span><span class="sxs-lookup"><span data-stu-id="615cc-121">OneDrive for Business, team sites and system pages, such as _layouts, etc., are all quick to load.</span></span>
    
- <span data-ttu-id="615cc-122">El 1 % más lento de las páginas de SharePoint Online tardan más de 5.000 milisegundos en cargarse.</span><span class="sxs-lookup"><span data-stu-id="615cc-122">The slowest 1% of SharePoint Online pages take more than 5,000 milliseconds to load.</span></span>
    
<span data-ttu-id="615cc-p101">Una prueba comparativa simple que puede usar sería medir el rendimiento comparando el tiempo de carga de su propio portal con el tiempo de carga de la página de inicio de OneDrive para la Empresa ya que usa pocas características personalizadas. Este suele ser el primer paso que el Soporte técnico le pedirá que complete al solucionar problemas de rendimiento de red.</span><span class="sxs-lookup"><span data-stu-id="615cc-p101">One simple benchmark test you can use would be to measure performance by comparing the load time of your own portal against the load time of the OneDrive for Business home page as it uses few customized features. This will often be the first step Support will ask you to complete when troubleshooting network performance issues.</span></span>
  
## <a name="use-a-standard-user-account-when-checking-performance"></a><span data-ttu-id="615cc-125">Use una cuenta de usuario estándar al rendimiento</span><span class="sxs-lookup"><span data-stu-id="615cc-125">Use a standard user account when checking performance</span></span>
<span data-ttu-id="615cc-126"><a name="standuser"> </a></span><span class="sxs-lookup"><span data-stu-id="615cc-126"></span></span>

<span data-ttu-id="615cc-127">Un administrador de colección de sitios, el propietario del sitio, el Editor o el colaborador pertenecen a grupos de seguridad adicionales, disponer de permisos adicionales y, por lo tanto, tienen elementos adicionales que se carga de SharePoint en una página.</span><span class="sxs-lookup"><span data-stu-id="615cc-127">A Site Collection Administrator, Site Owner, Editor, or Contributor belong to additional security groups, have additional permissions, and therefore have additional elements that SharePoint loads on a page.</span></span>
  
<span data-ttu-id="615cc-128">Esto es aplicable a SharePoint local y SharePoint Online, pero en un escenario local las diferencias no se con la misma facilidad notará como en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="615cc-128">This is applicable to SharePoint on-premises and SharePoint Online but in an on-premises scenario the differences will not be as easily noticed as in SharePoint Online.</span></span>
  
<span data-ttu-id="615cc-129">Para evaluar correctamente cómo llevará a cabo una página para los usuarios, debe usar una cuenta de usuario estándar para evitar la carga de la creación de controles y el tráfico adicional relacionados con los grupos de seguridad.</span><span class="sxs-lookup"><span data-stu-id="615cc-129">In order to correctly evaluate how a page will perform for users, you should use a standard user account to avoid loading the authoring controls and additional traffic related to security groups.</span></span>
  
## <a name="connection-categories-for-performance-tuning"></a><span data-ttu-id="615cc-130">Categorías de conexión para ajustar el rendimiento</span><span class="sxs-lookup"><span data-stu-id="615cc-130">Connection categories for performance tuning</span></span>
<span data-ttu-id="615cc-131"><a name="connect"> </a></span><span class="sxs-lookup"><span data-stu-id="615cc-131"></span></span>

<span data-ttu-id="615cc-p102">Puede clasificar las conexiones entre el servidor y el usuario en tres componentes principales. Tenga en cuenta esto al diseñar páginas de SharePoint Online para obtener más información sobre tiempos de carga.</span><span class="sxs-lookup"><span data-stu-id="615cc-p102">You can categorize the connections between the server and the user into three main components. Consider these when designing SharePoint Online pages for insight into load times.</span></span>
  
- <span data-ttu-id="615cc-134">**Server.** Los servidores que hospeda Microsoft en centros de datos.</span><span class="sxs-lookup"><span data-stu-id="615cc-134">**Server.** The servers that Microsoft hosts in datacenters.</span></span>
    
- <span data-ttu-id="615cc-135">**Red.** La red de Microsoft, Internet y la red local entre el centro de datos y los usuarios.</span><span class="sxs-lookup"><span data-stu-id="615cc-135">**Network.** The Microsoft network, the Internet, and your on-premises network between the datacenter and your users.</span></span>
    
- <span data-ttu-id="615cc-136">**Explorador.** Donde se carga la página.</span><span class="sxs-lookup"><span data-stu-id="615cc-136">**Browser.** Where the page is loaded.</span></span>
    
<span data-ttu-id="615cc-p103">Dentro de estas tres conexiones, normalmente hay cinco motivos que causan el 95 % de páginas lentas. En este artículo se describe cado uno de los motivos:</span><span class="sxs-lookup"><span data-stu-id="615cc-p103">Within these three connections there are typically five reasons that cause 95% of slow pages. Each of these reasons is discussed in this article:</span></span>
  
- <span data-ttu-id="615cc-139">Problemas de navegación</span><span class="sxs-lookup"><span data-stu-id="615cc-139">Navigation issues</span></span>
    
- <span data-ttu-id="615cc-140">Acumulación de contenido</span><span class="sxs-lookup"><span data-stu-id="615cc-140">Content roll up</span></span>
    
- <span data-ttu-id="615cc-141">Archivos de gran tamaño</span><span class="sxs-lookup"><span data-stu-id="615cc-141">Large files</span></span>
    
- <span data-ttu-id="615cc-142">Muchas solicitudes al servidor</span><span class="sxs-lookup"><span data-stu-id="615cc-142">Many requests to the server</span></span>
    
- <span data-ttu-id="615cc-143">Procesamiento de elementos web</span><span class="sxs-lookup"><span data-stu-id="615cc-143">Web Part processing</span></span>
    
### <a name="server-connection"></a><span data-ttu-id="615cc-144">Conexión de servidor</span><span class="sxs-lookup"><span data-stu-id="615cc-144">Server connection</span></span>
<span data-ttu-id="615cc-145"><a name="server"> </a></span><span class="sxs-lookup"><span data-stu-id="615cc-145"></span></span>

<span data-ttu-id="615cc-146">Muchos de los problemas que afectan al rendimiento con SharePoint local también se aplican a SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="615cc-146">Many of the issues that affect performance with SharePoint on-premises also apply to SharePoint Online.</span></span>
  
<span data-ttu-id="615cc-p104">Como cabría esperar, tiene mucho más control sobre el rendimiento de los servidores con SharePoint local. Con SharePoint Online las cosas son un poco diferentes. Cuanto más trabajo requiera al servidor, más tarda en procesar una página. Con SharePoint, la causa más grande en este sentido son páginas complejas con varios elementos web.</span><span class="sxs-lookup"><span data-stu-id="615cc-p104">As you would expect, you have far more control over how servers perform with on-premises SharePoint. With SharePoint Online things are a little different. The more work you make a server do, the longer it takes to render a page. With SharePoint, the biggest culprit in this respect are complex pages with multiple web parts.</span></span>
  
<span data-ttu-id="615cc-151">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-151">SharePoint Online</span></span>
  
![Captura de pantalla del servidor en línea](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
<span data-ttu-id="615cc-153">SharePoint</span><span class="sxs-lookup"><span data-stu-id="615cc-153">SharePoint</span></span>
  
![Captura de pantalla del servidor local](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
<span data-ttu-id="615cc-p105">Con SharePoint Online, realmente pueden suceder que determinadas solicitudes de página terminen llamando a varios servidores. Podría acabar con una matriz de solicitudes entre los servidores para una solicitud individual. Estas interacciones son costosas desde una perspectiva de carga de página y harán que todo sea lento.</span><span class="sxs-lookup"><span data-stu-id="615cc-p105">With SharePoint Online, certain page requests may actually end up calling multiple servers. You could end up with a matrix of requests between servers for an individual request. These interactions are expensive from a page load perspective and will make things slow.</span></span>
  
<span data-ttu-id="615cc-158">Algunos ejemplos de estas interacciones de servidor a servidor son:</span><span class="sxs-lookup"><span data-stu-id="615cc-158">Examples of these server to server interactions are:</span></span>
  
- <span data-ttu-id="615cc-159">Servidores web a SQL</span><span class="sxs-lookup"><span data-stu-id="615cc-159">Web to SQL Servers</span></span>
    
- <span data-ttu-id="615cc-160">Servidores web a servidores de aplicaciones</span><span class="sxs-lookup"><span data-stu-id="615cc-160">Web to application servers</span></span>
    
<span data-ttu-id="615cc-p106">Lo otro que puede ralentizar las interacciones del servidor son los faltantes en la memoria caché. A diferencia de SharePoint local, hay muy poca probabilidad de que llegará al mismo servidor para una página que ha visitado previamente. Esto hace que el almacenamiento en caché de los objetos quede obsoleto.</span><span class="sxs-lookup"><span data-stu-id="615cc-p106">The other thing that can slow down server interactions is cache misses. Unlike on-premises SharePoint, there is a very slim chance that you will hit the same server for a page that you have visited previously; this makes object caching obsolete.</span></span>
  
### <a name="network-connection"></a><span data-ttu-id="615cc-163">Conexión de red</span><span class="sxs-lookup"><span data-stu-id="615cc-163">Network connection</span></span>
<span data-ttu-id="615cc-164"><a name="network"> </a></span><span class="sxs-lookup"><span data-stu-id="615cc-164"></span></span>

<span data-ttu-id="615cc-p107">Con SharePoint local que no tiene el uso de una red WAN, es posible que utilice una conexión de alta velocidad entre centros de datos y los usuarios finales. Por lo general, las cosas son fáciles de administrar desde una perspectiva de la red.</span><span class="sxs-lookup"><span data-stu-id="615cc-p107">With on-premises SharePoint that doesn't make use of a WAN, you may use a high-speed connection between datacenter and end-users. Generally, things are easy to manage from a network perspective.</span></span>
  
<span data-ttu-id="615cc-167">Con SharePoint Online, hay algunos factores más que se deben tener en cuenta. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="615cc-167">With SharePoint Online, there are a few more factors to consider; for example:</span></span>
  
- <span data-ttu-id="615cc-168">La red de Microsoft</span><span class="sxs-lookup"><span data-stu-id="615cc-168">The Microsoft network</span></span>
    
- <span data-ttu-id="615cc-169">Internet</span><span class="sxs-lookup"><span data-stu-id="615cc-169">The Internet</span></span>
    
- <span data-ttu-id="615cc-170">El ISP</span><span class="sxs-lookup"><span data-stu-id="615cc-170">The ISP</span></span>
    
<span data-ttu-id="615cc-171">Independientemente de qué versión de SharePoint (y qué red) se utiliza, lo que dará lugar normalmente a la red ocupada es:</span><span class="sxs-lookup"><span data-stu-id="615cc-171">Regardless of which version of SharePoint (and which network) you are using, things that will typically cause the network to be busy include:</span></span>
  
- <span data-ttu-id="615cc-172">Carga de gran tamaño</span><span class="sxs-lookup"><span data-stu-id="615cc-172">Large payload</span></span>
    
- <span data-ttu-id="615cc-173">Muchos archivos</span><span class="sxs-lookup"><span data-stu-id="615cc-173">Many files</span></span>
    
- <span data-ttu-id="615cc-174">Gran distancia física con el servidor</span><span class="sxs-lookup"><span data-stu-id="615cc-174">Large physical distance to the server</span></span>
    
<span data-ttu-id="615cc-p108">Una característica que puede aprovechar en SharePoint Online es la CDN de Microsoft (Content Delivery Network). Una CDN es, básicamente, una colección de servidores implementada en varios centros de datos distribuida. Con una CDN, contenido en las páginas se puede hospedar en un servidor hacia el cliente incluso si el cliente se encuentra lejos desde el servidor de SharePoint original. Microsoft va a utilizar más en el futuro para almacenar las instancias locales de las páginas que no se puede personalizar, por ejemplo la página de principal del administrador SharePoint Online. Para obtener más información acerca de las CDN, vea [redes de entrega de contenido](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span><span class="sxs-lookup"><span data-stu-id="615cc-p108">One feature that you can leverage in SharePoint Online is the Microsoft CDN (Content Delivery Network). A CDN is basically a distributed collection of servers deployed across multiple datacenters. With a CDN, content on pages can be hosted on a server close to the client even if the client is far away from the originating SharePoint Server. Microsoft will be using this more in the future to store local instances of pages which cannot be customized, for example the SharePoint Online admin home page. For more information about CDNs, see [Content delivery networks](https://support.office.com/article/Content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f).</span></span>
  
<span data-ttu-id="615cc-p109">Algo que debe tener en cuenta, pero que tal vez no pueda hacer mucho al respecto, es la velocidad de conexión de su ISP. Una simple herramienta de prueba de velocidad indica la velocidad de conexión.</span><span class="sxs-lookup"><span data-stu-id="615cc-p109">Something that you need to be aware of but may not be able to do much about is the connection speed of your ISP. A simple speed test tool will tell you the connection speed.</span></span>
  
### <a name="browser-connection"></a><span data-ttu-id="615cc-182">Conexión de explorador</span><span class="sxs-lookup"><span data-stu-id="615cc-182">Browser connection</span></span>
<span data-ttu-id="615cc-183"><a name="browser"> </a></span><span class="sxs-lookup"><span data-stu-id="615cc-183"></span></span>

<span data-ttu-id="615cc-184">Existen algunos factores que debe considerar con exploradores web desde una perspectiva de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="615cc-184">There are a few factors to consider with web browsers from a performance perspective.</span></span>
  
<span data-ttu-id="615cc-p110">Visitar páginas complejas afectará al rendimiento. Mayoría de los exploradores sólo tiene una pequeña memoria caché (alrededor de 90MB), mientras el promedio página web suele ser alrededor de 1,6 MB. Esto no tardará mucho tiempo para acostumbrarse copia de seguridad.</span><span class="sxs-lookup"><span data-stu-id="615cc-p110">Visiting complex pages will affect performance. Most browsers only have a small cache (around 90MB), while the average web page is typically around 1.6MB. This doesn't take long to get used up.</span></span>
  
<span data-ttu-id="615cc-p111">Ancho de banda también puede ser un problema. Por ejemplo, si un usuario es ver vídeos en otra sesión, esto afectará al rendimiento de la página de SharePoint. Mientras no se puede evitar que los usuarios multimedia de transmisión por secuencias, puede controlar la forma en que se carga una página para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="615cc-p111">Bandwidth may also be an issue. For example, if a user is watching videos in another session, this will affect the performance of your SharePoint page. While you can't prevent users from streaming media, you can control the way a page will load for users.</span></span>
  
<span data-ttu-id="615cc-191">Consulte los siguientes artículos para diferentes técnicas de personalización de página SharePoint Online y otras prácticas recomendadas que le ayudarán a lograr un rendimiento óptimo.</span><span class="sxs-lookup"><span data-stu-id="615cc-191">Check out the following articles for different SharePoint Online page customization techniques and other best practices to help you achieve optimal performance.</span></span>
  
- [<span data-ttu-id="615cc-192">Opciones de navegación para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-192">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="615cc-193">Use la herramienta de diagnóstico de la página de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-193">Use the Page Diagnostics tool for SharePoint Online</span></span>](page-diagnostics-for-spo.md)
    
- [<span data-ttu-id="615cc-194">Optimización de imágenes para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-194">Image optimization for SharePoint Online</span></span>](image-optimization-for-sharepoint-online.md)
    
- [<span data-ttu-id="615cc-195">Retrasar la carga de imágenes y JavaScript en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-195">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [<span data-ttu-id="615cc-196">Minificación y agrupación en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-196">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="615cc-197">Usar redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="615cc-197">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="615cc-198">Uso de elemento de Web de búsqueda de contenido en lugar de elemento Web consulta de contenido para mejorar el rendimiento en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-198">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [<span data-ttu-id="615cc-199">Planeación de capacidad y la carga de prueba de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-199">Capacity planning and load testing SharePoint Online</span></span>](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [<span data-ttu-id="615cc-200">Diagnosticar problemas de rendimiento con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-200">Diagnosing performance issues with SharePoint Online</span></span>](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [<span data-ttu-id="615cc-201">Usar la memoria caché de objetos con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-201">Using the object cache with SharePoint Online</span></span>](using-the-object-cache-with-sharepoint-online.md)
    
- [<span data-ttu-id="615cc-202">Cómo: Evitar estar limitado o bloqueado en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="615cc-202">How to: Avoid getting throttled or blocked in SharePoint Online</span></span>](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

