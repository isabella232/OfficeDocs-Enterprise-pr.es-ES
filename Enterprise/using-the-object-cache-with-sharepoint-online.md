---
title: Usar la memoria caché de objetos con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: En este artículo se explica la diferencia entre el uso de la memoria caché de objetos en SharePoint Server 2013 local y SharePoint Online.
ms.openlocfilehash: 59f3a69199893cb367d4d28c0c545ebd9dfd1236
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25769859"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="5d3b5-103">Usar la memoria caché de objetos con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5d3b5-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="5d3b5-104">En este artículo se explica la diferencia entre el uso de la memoria caché de objetos en SharePoint Server 2013 local y SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5d3b5-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="5d3b5-p101">Si se depende de la caché de objetos en una implementación de SharePoint Online, se produce un impacto negativo relevante. Cualquier dependencia de memoria caché de objetos en SharePoint Online reducirá la confiabilidad de la página.</span><span class="sxs-lookup"><span data-stu-id="5d3b5-p101">There is significant negative impact of relying on the object cache in SharePoint Online deployment. Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="5d3b5-107">Cómo SharePoint Online y SharePoint Server 2013 funcionamiento de la memoria caché de objetos</span><span class="sxs-lookup"><span data-stu-id="5d3b5-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="5d3b5-p102">Cuando SharePoint Server 2013 está hospedado local, el cliente tiene servidores front-end web privada que hospedan la caché de objetos. Esto significa que la memoria caché está dedicada a un cliente y sólo está limitada por la cantidad de memoria es disponibles y asignados a la memoria caché de objetos. Dado que solo un cliente se sirve en el escenario local los servidores front-end web normalmente tienen los usuarios que realizan solicitudes a los mismos sitios, una y otra vez. Esto significa que la memoria caché obtiene completa rápidamente y permanece completa de los resultados de la consulta de lista y los objetos de SharePoint que los usuarios solicitan de forma regular.</span><span class="sxs-lookup"><span data-stu-id="5d3b5-p102">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache. This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache. Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over. This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![Muestra el tráfico y la carga a los servidores locales front-end web](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="5d3b5-p103">En consecuencia, la segunda vez que un usuario visita una página, el tiempo de carga de la página mejora. Después de un mínimo de cuatro cargas de la misma página, la página se almacena en la memoria caché en todos los servidores front-end web.</span><span class="sxs-lookup"><span data-stu-id="5d3b5-p103">As a result, the second time a user visits a page, the page load time improves. After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="5d3b5-p104">Por el contrario, en SharePoint Online hay muchos más servidores pero también muchos más sitios. Cada usuario puede conectarse a un servidor web front-end diferente que no tiene la memoria caché que se rellena. O bien, quizás obtener rellena la memoria caché para un servidor, pero el usuario siguiente a que las solicitudes de servidor front-end web una página de un sitio diferente. O bien, incluso si el usuario siguiente solicita la misma página que en su visita anterior, son con equilibrio de carga en un servidor web front-end diferente que no tiene esa página en su memoria caché. En este último caso, el almacenamiento en caché no ayuda a los usuarios en absoluto.</span><span class="sxs-lookup"><span data-stu-id="5d3b5-p104">In contrast, in SharePoint Online there are many more servers but also many more sites. Each user may connect to a different front-end web server that doesn't have the cache populated. Or, perhaps the cache does get populated for a server, but the next user to that front-end web server requests a page from a different site. Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache. In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="5d3b5-p105">En la figura siguiente, cada punto representa una página que un usuario solicita y donde se almacenó en la memoria caché. Los distintos colores representan a diferentes clientes que usan de modo compartido la infraestructura de SaaS.</span><span class="sxs-lookup"><span data-stu-id="5d3b5-p105">In the following figure, each dot represents a page that a user is requesting and where it cached. Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![Muestra los resultados de almacenamiento en memoria caché de objetos en SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="5d3b5-p106">Como puede ver en el diagrama, las posibilidades de que cualquier usuario determinado alcanzando a un servidor con la versión en caché de la página son delgadas. Además, debido a la gran rendimiento y el hecho de que los servidores se comparten entre muchos sitios, la memoria caché no por última vez durante cuánto tiempo puesto que sólo hay mucho espacio para almacenar en caché disponible.</span><span class="sxs-lookup"><span data-stu-id="5d3b5-p106">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim. Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="5d3b5-125">Por todos estos motivos, depender de que los usuarios obtengan objetos almacenados en la memoria caché no es una forma eficaz de garantizar una experiencia de usuario de calidad y tiempos de carga páginas en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5d3b5-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="5d3b5-126">Si no podemos depender de la memoria caché de objetos para mejorar el rendimiento en SharePoint Online, ¿qué usamos en su lugar?</span><span class="sxs-lookup"><span data-stu-id="5d3b5-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="5d3b5-p107">Puesto que no debe depender del almacenamiento en memoria caché en SharePoint Online, debe evaluar enfoques de diseño alternativos para las personalizaciones de SharePoint que usan la memoria caché de objetos. Esto significa que se deben usar enfoques para problemas de rendimiento que no dependan de la memoria caché de objetos para obtener buenos resultados para los usuarios. Se describe en algunos de los otros artículos de esta serie e incluyen:</span><span class="sxs-lookup"><span data-stu-id="5d3b5-p107">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache. This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users. This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="5d3b5-130">Opciones de navegación para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5d3b5-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="5d3b5-131">Minificación y agrupación en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5d3b5-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="5d3b5-132">Usar redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="5d3b5-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="5d3b5-133">Retrasar la carga de imágenes y JavaScript en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5d3b5-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

