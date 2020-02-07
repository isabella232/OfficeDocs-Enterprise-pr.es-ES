---
title: Usar la memoria caché de objetos con SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: En este artículo se explica la diferencia entre el uso de la memoria caché de objetos en SharePoint Server 2013 local y SharePoint Online.
ms.openlocfilehash: 24d58b692667c897d2f25d41d4216a74382a5390
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841054"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a><span data-ttu-id="cea87-103">Usar la memoria caché de objetos con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cea87-103">Using the object cache with SharePoint Online</span></span>

<span data-ttu-id="cea87-104">En este artículo se explica la diferencia entre el uso de la memoria caché de objetos en SharePoint Server 2013 local y SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="cea87-104">This article explains the difference between using the object cache in SharePoint Server 2013 on-premises and SharePoint Online.</span></span>
  
<span data-ttu-id="cea87-105">Hay un impacto negativo significativo de confiar en la memoria caché de objetos en la implementación de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="cea87-105">There is significant negative impact of relying on the object cache in SharePoint Online deployment.</span></span> <span data-ttu-id="cea87-106">Cualquier dependencia de la memoria caché de objetos en SharePoint Online reducirá la confiabilidad de la página.</span><span class="sxs-lookup"><span data-stu-id="cea87-106">Any dependency on object cache in SharePoint Online will reduce the reliability of your page.</span></span> 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a><span data-ttu-id="cea87-107">Cómo funciona la caché de objetos de SharePoint Online y SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="cea87-107">How the SharePoint Online and SharePoint Server 2013 object cache works</span></span>

<span data-ttu-id="cea87-108">Cuando SharePoint Server 2013 está hospedado en local, el cliente tiene servidores front-end web privados que hospedan la memoria caché de objetos.</span><span class="sxs-lookup"><span data-stu-id="cea87-108">When SharePoint Server 2013 is hosted on-premises, the customer has private front-end web servers that host the object cache.</span></span> <span data-ttu-id="cea87-109">Esto significa que la memoria caché está dedicada a un cliente y solo está limitada por la cantidad de memoria disponible y asignada a la memoria caché de objetos.</span><span class="sxs-lookup"><span data-stu-id="cea87-109">This means the cache is dedicated to one customer and is only limited by how much memory is available and allocated to the object cache.</span></span> <span data-ttu-id="cea87-110">Dado que solo se atiende a un cliente en el escenario local, los servidores front-end web suelen hacer que los usuarios realicen solicitudes a los mismos sitios una y otra vez.</span><span class="sxs-lookup"><span data-stu-id="cea87-110">Because only one customer is served in the on-premises scenario the front-end web servers typically have users making requests to the same sites over and over.</span></span> <span data-ttu-id="cea87-111">Esto significa que la memoria caché se llena rápidamente y permanece llena de los resultados de la consulta de la lista y los objetos de SharePoint que los usuarios solicitan de manera regular.</span><span class="sxs-lookup"><span data-stu-id="cea87-111">This means that the cache gets full quickly and remains full of the list query results and SharePoint objects that your users are requesting on a regular basis.</span></span>
  
![Muestra el tráfico y la carga a los servidores locales front-end web](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
<span data-ttu-id="cea87-113">Como resultado, la segunda vez que un usuario visita una página, el tiempo de carga de la página mejora.</span><span class="sxs-lookup"><span data-stu-id="cea87-113">As a result, the second time a user visits a page, the page load time improves.</span></span> <span data-ttu-id="cea87-114">Después de un mínimo de cuatro cargas de la misma página, la página se almacena en caché en todos los servidores web Front-end.</span><span class="sxs-lookup"><span data-stu-id="cea87-114">After a minimum of four loads of the same page, the page is cached on all of the front-end web servers.</span></span>
  
<span data-ttu-id="cea87-115">Por el contrario, en SharePoint Online hay muchos más servidores, pero también muchos más sitios.</span><span class="sxs-lookup"><span data-stu-id="cea87-115">In contrast, in SharePoint Online there are many more servers but also many more sites.</span></span> <span data-ttu-id="cea87-116">Cada usuario puede conectarse a un servidor web Front-end diferente que no tiene la caché rellenada.</span><span class="sxs-lookup"><span data-stu-id="cea87-116">Each user may connect to a different front-end web server that doesn't have the cache populated.</span></span> <span data-ttu-id="cea87-117">O bien, es posible que la memoria caché se llene para un servidor, pero el siguiente usuario a ese servidor web Front-end solicita una página de un sitio diferente.</span><span class="sxs-lookup"><span data-stu-id="cea87-117">Or, perhaps the cache does get populated for a server, but the next user to that front-end web server requests a page from a different site.</span></span> <span data-ttu-id="cea87-118">O, incluso si el siguiente usuario solicita la misma página que en la visita anterior, se equilibra la carga con un servidor cliente web diferente que no tiene esa página en la caché.</span><span class="sxs-lookup"><span data-stu-id="cea87-118">Or, even if the next user requests the same page as on their previous visit, they are load-balanced to a different front-end web server that doesn't have that page in its cache.</span></span> <span data-ttu-id="cea87-119">En este último caso, el almacenamiento en caché no ayuda a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="cea87-119">In this last case, caching doesn't help the users at all.</span></span>
  
<span data-ttu-id="cea87-120">En la siguiente ilustración, cada punto representa una página que un usuario solicita y donde se almacena en caché.</span><span class="sxs-lookup"><span data-stu-id="cea87-120">In the following figure, each dot represents a page that a user is requesting and where it cached.</span></span> <span data-ttu-id="cea87-121">Diferentes colores representan a diferentes clientes que realizan el uso compartido de la infraestructura SaaS.</span><span class="sxs-lookup"><span data-stu-id="cea87-121">Different colors represent different customers making shared use of the SaaS infrastructure.</span></span>
  
![Muestra los resultados de almacenamiento en memoria caché de objetos en SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
<span data-ttu-id="cea87-123">Como puede ver en el diagrama, las probabilidades de que un usuario determinado que visita un servidor con la versión almacenada en caché de la página sean delgadas.</span><span class="sxs-lookup"><span data-stu-id="cea87-123">As you can see from the diagram, the chances of any given user hitting a server with the cached version of their page are slim.</span></span> <span data-ttu-id="cea87-124">Además, debido al gran rendimiento y al hecho de que los servidores se comparten entre muchos sitios, la caché no dura mucho tiempo, ya que sólo hay un espacio para el almacenamiento en caché disponible.</span><span class="sxs-lookup"><span data-stu-id="cea87-124">Also, due to the large throughput and fact that the servers are shared between many sites, the cache doesn't last long since there is only so much space for caching available.</span></span>
  
<span data-ttu-id="cea87-125">Por todos estos motivos, depender de que los usuarios obtengan objetos almacenados en la caché no es una forma eficaz de garantizar una experiencia del usuario de calidad y tiempos de carga de página en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="cea87-125">For all of these reasons, relying on users getting cached objects is not an effective way to ensure a quality user experience and page load times in SharePoint Online.</span></span>
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a><span data-ttu-id="cea87-126">Si no podemos confiar en la memoria caché de objetos para mejorar el rendimiento en SharePoint Online, ¿qué usamos en su lugar?</span><span class="sxs-lookup"><span data-stu-id="cea87-126">If we can't rely on the object cache to improve performance in SharePoint Online, what do we use instead?</span></span>

<span data-ttu-id="cea87-127">Como no se debe basar en el almacenamiento en caché en SharePoint Online, debe evaluar métodos de diseño alternativos para las personalizaciones de SharePoint que usan la memoria caché de objetos.</span><span class="sxs-lookup"><span data-stu-id="cea87-127">Since you shouldn't rely on caching in SharePoint Online, you should evaluate alternative design approaches for SharePoint customizations that use the object cache.</span></span> <span data-ttu-id="cea87-128">Esto significa usar enfoques para problemas de rendimiento que no se basan en el almacenamiento en caché de objetos para obtener buenos resultados para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="cea87-128">This means using approaches for performance issues which do not rely on the object caching in order to produce good results for users.</span></span> <span data-ttu-id="cea87-129">Esto se describe en algunos de los otros artículos de esta serie e incluyen:</span><span class="sxs-lookup"><span data-stu-id="cea87-129">This is described in some of the other articles in this series and include:</span></span>
  
- [<span data-ttu-id="cea87-130">Opciones de navegación para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cea87-130">Navigation options for SharePoint Online</span></span>](navigation-options-for-sharepoint-online.md)
    
- [<span data-ttu-id="cea87-131">Minificación y agrupación en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cea87-131">Minification and bundling in SharePoint Online</span></span>](minification-and-bundling-in-sharepoint-online.md)
    
- [<span data-ttu-id="cea87-132">Usar redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="cea87-132">Using content delivery networks</span></span>](using-content-delivery-networks-with-sharepoint-online.md)
    
- [<span data-ttu-id="cea87-133">Retrasar la carga de imágenes y JavaScript en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cea87-133">Delay loading images and JavaScript in SharePoint Online</span></span>](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

