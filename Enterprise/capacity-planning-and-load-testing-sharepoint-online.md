---
title: Planeación de capacidad y la carga de prueba de SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: En este artículo se describe cómo se puede implementar en SharePoint Online sin tener que realizar las pruebas de carga tradicional como no está permitido.
ms.openlocfilehash: 06649942f20dc18abfcae0e56df7e3ea56ed9165
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542973"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a><span data-ttu-id="d08f4-103">Planeación de capacidad y la carga de prueba de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="d08f4-103">Capacity planning and load testing SharePoint Online</span></span>

<span data-ttu-id="d08f4-104">En este artículo se describe cómo se puede implementar en SharePoint Online sin tener que realizar las pruebas de carga tradicional como no está permitido.</span><span class="sxs-lookup"><span data-stu-id="d08f4-104">This article describes how you can deploy to SharePoint Online without performing traditional load testing since it is not permitted.</span></span>
  
<span data-ttu-id="d08f4-105">Aunque no es recomendable, existen otras maneras, puede asegurarse de que carga activo pruebas en SharePoint Online un sitio no producirá una experiencia de usuario deficiente cuando el sitio se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="d08f4-105">Although active load testing on SharePoint Online is strongly discouraged, there are other ways you can make sure that a site will not produce a poor user experience when you launch the site.</span></span> 
  
<span data-ttu-id="d08f4-p101">Con SharePoint Online no es necesario que realizar la planeación de la capacidad, como esto se realiza automáticamente como parte de la oferta de servicio. Con los entornos local, las pruebas de carga se usan para validar la suposición de escala y, finalmente, busque el punto de interrupción de una granja de servidores; al saturar con carga. Con SharePoint Online, necesitamos hacer cosas de manera diferente. Que se va a un entorno de varios inquilino, tenemos que proteger a todos los inquilinos en la misma granja de servidores, por lo que se va a limitar automáticamente cualquier las pruebas de carga. Esto significa que se recibirá decepcionantes y potencialmente engañoso son resultados si se intenta cargar el entorno de prueba.</span><span class="sxs-lookup"><span data-stu-id="d08f4-p101">With SharePoint Online you don't have to do capacity planning, as this is done for you as part of our service offering. With on-premises environments, load testing is used to validate scale assumption and ultimately find the breaking point of a farm; by saturating it with load. With SharePoint Online we need to do things differently. Being a multi-tenant environment, we have to protect all tenants in the same farm, so we will automatically throttle any load tests. This means you will receive disappointing and potentially misleading results if you attempt to load test your environment.</span></span>
  
<span data-ttu-id="d08f4-p102">Uno de los principales beneficios de SharePoint Online a través de una implementación local es la elasticidad de la nube. Nuestro entorno de gran escala está configurado para el servicio millones de usuarios de manera diaria por lo que es importante que se controlan capacidad eficazmente mediante la expansión automática de las granjas de servidores, tal y como y cuando sea necesario. En este artículo se explica la planificación para el crecimiento de la capacidad y la escala horizontal en su lugar. El artículo también trata los enfoques para usar que no requieren pruebas de carga.</span><span class="sxs-lookup"><span data-stu-id="d08f4-p102">One of the main benefits of SharePoint Online over an on-premises deployment is the elasticity of the cloud. Our large scale environment is set up to service millions of users on a daily basis so it is important that we handle capacity effectively by automatically expanding farms, as and when needed. This article explains how we plan for capacity growth and scale out in place. The article also covers approaches for you to use that don't involve load testing.</span></span>
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a><span data-ttu-id="d08f4-115">Cómo Office 365 prevé carga y expande la capacidad</span><span class="sxs-lookup"><span data-stu-id="d08f4-115">How Office 365 predicts load and expands capacity</span></span>

<span data-ttu-id="d08f4-116">Trabajo de administración de capacidad de SharePoint Online server se realiza a través de dos métodos:</span><span class="sxs-lookup"><span data-stu-id="d08f4-116">SharePoint Online server capacity management work is done through two methods:</span></span>
  
- <span data-ttu-id="d08f4-117">Previsión de la capacidad</span><span class="sxs-lookup"><span data-stu-id="d08f4-117">Capacity forecasting</span></span>
    
- <span data-ttu-id="d08f4-118">Equilibrio de carga en granjas de servidores de un solo servidor</span><span class="sxs-lookup"><span data-stu-id="d08f4-118">Load-balancing on single server farms</span></span>
    
<span data-ttu-id="d08f4-p103">A diferencia de planeación para un entorno local, para la previsión de capacidad en SharePoint Online, estamos capacitados para compilar las estadísticas y los posibles requisitos en cualquier grupo de servidor determinado de gráfico. La demanda agregada puede parecerse a las solicitudes en la zona (donde una zona es un grupo de granjas de servidores de SharePoint) línea de crecimiento en la imagen siguiente:</span><span class="sxs-lookup"><span data-stu-id="d08f4-p103">Unlike planning for an on-premises environment, for capacity forecasting in SharePoint Online, we are able to compile statistics and graph potential requirements in any given server group. The aggregate demand might look something like the Requests in zone (where a zone is a group of SharePoint farms) growth line in the image below:</span></span>
  
![Gráfico que muestra la capacidad de predicción: previsión](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
<span data-ttu-id="d08f4-p104">Mientras el crecimiento es impredecible en cualquier una granja de servidores, la suma de las solicitudes en una zona agregada es predecible. Mediante la identificación de las tendencias de crecimiento en SharePoint Online, podemos hacer planes de expansión en el futuro.</span><span class="sxs-lookup"><span data-stu-id="d08f4-p104">While the growth is unpredictable in any one farm, the aggregated sum of requests in a zone is predictable. By identifying the growth trends in SharePoint Online, we can plan for future expansion.</span></span>
  
<span data-ttu-id="d08f4-p105">Para poder utilizar la capacidad de forma eficaz y abordar los problemas con el crecimiento inesperado, en cualquier conjunto de servidores, tenemos automatización que realiza un seguimiento de carga front-end y cambia la escala de copia de seguridad en su lugar, cuando sea necesario. La métrica principal que se usa como una señal para escalar front-termina es la carga de CPU. Nuestro objetivo consiste en mantener los momentos de mayor carga de CPU en un 40%. Esto es con el fin de tener suficiente búfer absorber los picos inesperados. Como carga enfoques 40% en estado estable, se agregue servidores front-end para granjas de servidores.</span><span class="sxs-lookup"><span data-stu-id="d08f4-p105">In order to efficiently use capacity and deal with unexpected growth, in any farm, we have automation that tracks front-end load and scales up in place, when needed. The main metric we use as a signal to scale up front ends is CPU load. Our goal is to keep peak CPU load under 40%. This is in order to have enough buffer to absorb unexpected spikes. As load approaches 40% in steady state, we add front ends to farms.</span></span>
  
![Gráfico que muestra la capacidad de predicción: administrar granjas de servidores](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
<span data-ttu-id="d08f4-130">Servidores adicionales se pueden agregar rápidamente a una granja de servidores, los que anteriormente se han agregado a la zona mediante el uso de la previsión con.</span><span class="sxs-lookup"><span data-stu-id="d08f4-130">Additional servers can be quickly added to a farm, using those which have been previously added to the zone through the usage forecast.</span></span> 
  
## <a name="how-do-i-plan-for-a-site-launch"></a><span data-ttu-id="d08f4-131">¿Cómo planeado para el lanzamiento de un sitio?</span><span class="sxs-lookup"><span data-stu-id="d08f4-131">How do I plan for a site launch?</span></span>

<span data-ttu-id="d08f4-p106">Puede esperar a que la granja de servidores en el que se inicia el nuevo sitio automáticamente se supervisarán para que se agreguen nuevos servidores front-end, como se describió anteriormente. Por este motivo, no es necesario ninguna notificación para su lanzamiento del sitio nuevo.</span><span class="sxs-lookup"><span data-stu-id="d08f4-p106">You should expect that the farm on which your new site launches will automatically be monitored so that new front-end servers are added, as described above. For this reason, we don't need any notification for your new site launch.</span></span>
  
<span data-ttu-id="d08f4-134">Después de otras prácticas recomendadas para una sola página en SharePoint Online es poco probable que el lanzamiento de un nuevo sitio a incluso 100.000 usuarios tendrán ningún impacto en la granja de servidores.</span><span class="sxs-lookup"><span data-stu-id="d08f4-134">Following other best practices for a single page on SharePoint Online it is unlikely that a new site launch to even 100,000 users will have any impact to the farm.</span></span>
  
<span data-ttu-id="d08f4-p107">Hay algunas estrategias para planear una versión de un nuevo sitio de SharePoint Online. Tal como se muestra en la siguiente imagen, a menudo es considerablemente superior a los que realmente se usa el sitio que la cantidad de usuarios que están invitados. Esta imagen muestra una estrategia de acerca de cómo implantar una versión. Este método no sólo contribuye a la carga de rendimiento, sino que también puede ayudar a identificar maneras de mejorar el sitio de SharePoint antes de la gran mayoría de los usuarios para verlo.</span><span class="sxs-lookup"><span data-stu-id="d08f4-p107">There are a few strategies to plan for a release of a new SharePoint Online site. As shown in the following image, often the amount of users that are invited is significantly higher than those that actually use the site. This image shows a strategy about how to roll out a release. This method not only helps with performance loading but also can help identify ways to improve the SharePoint site before the large majority of the users see it.</span></span>
  
![Gráfico que muestra los usuarios invitados y activos](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
<span data-ttu-id="d08f4-p108">En la fase piloto, es buena obtener comentarios de los usuarios que la organización confía y sabe realizarán ser ocupado. En este modo, es posible evaluar cómo se utiliza el sistema, así como cómo va a realizar.</span><span class="sxs-lookup"><span data-stu-id="d08f4-p108">In the pilot phase, it is good to get feedback from users that the organization trusts and knows will be engaged. This way it is possible to gauge how the system is being used, as well as how it is performing.</span></span>
  
<span data-ttu-id="d08f4-p109">Una vez hecho esto, comienza un roll out a todos los usuarios de ondas; obtener comentarios y revisar el rendimiento con regularidad. Esto tiene la ventaja de lentamente Introducción al sistema y realizar mejoras como el sistema obtiene usar más. Esto también nos permite reaccionar ante el aumento de la carga como el sitio se ha implantado a más usuarios.</span><span class="sxs-lookup"><span data-stu-id="d08f4-p109">After this, begins a roll out to all users in waves; getting feedback and reviewing the performance regularly. This has the advantage of slowly introducing the system and making improvements as the system gets more use. This also allows us to react to the increased load as the site is rolled out to more and more users.</span></span>
  
<span data-ttu-id="d08f4-p110">Por último, mientras que las pruebas de carga están prohibidas, los clientes desean configurar ping periódicos para el servicio de disponibilidad de medida y la latencia. Esto permitirá identificar una línea de base para su sitio. Sin embargo, estos deben mantenerse a baja frecuencia para evitar la limitación de los problemas descritos anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d08f4-p110">Finally, while load tests are prohibited, customers may want to set up periodical pings to the service to measure availability and latency. This will identify a baseline for their site. However, these must be kept to low frequency to avoid throttling issues previously described.</span></span>
  

