---
title: Información de la red de 365 de Microsoft (versión preliminar)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Información de la red de 365 de Microsoft (versión preliminar)
ms.openlocfilehash: 0146019d1424cda696104d68eeda32ce28a26391
ms.sourcegitcommit: 07ab7d300c8df8b1665cfe569efc506b00915d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "43612910"
---
# <a name="microsoft-365-network-insights-preview"></a><span data-ttu-id="3619a-103">Información de la red de 365 de Microsoft (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3619a-103">Microsoft 365 Network Insights (preview)</span></span>

<span data-ttu-id="3619a-104">**Network Insights** son métricas de rendimiento de Live que recopila el inquilino de Microsoft 365 y que solo pueden ver los usuarios administrativos de su espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="3619a-104">**Network insights** are live performance metrics collected from your Microsoft 365 tenant, and available to view only by administrative users in your tenant.</span></span> <span data-ttu-id="3619a-105">La información se muestra en el centro de administración de Microsoft 365 <https://portal.microsoft.com/adminportal/home#/networkperformance>en.</span><span class="sxs-lookup"><span data-stu-id="3619a-105">Insights are displayed in the Microsoft 365 Admin Center at <https://portal.microsoft.com/adminportal/home#/networkperformance>.</span></span>

<span data-ttu-id="3619a-106">La información está destinada a ayudar en el diseño de perímetros de red para sus ubicaciones de oficina.</span><span class="sxs-lookup"><span data-stu-id="3619a-106">Insights are intended to help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="3619a-107">Cada conocimiento proporciona detalles sobre las características de rendimiento de un problema común específico para cada ubicación geográfica en la que los usuarios obtienen acceso a su inquilino.</span><span class="sxs-lookup"><span data-stu-id="3619a-107">Each insight provides live details about the performance characteristics for a specific common issue for each geographic location where users are accessing your tenant.</span></span>

<span data-ttu-id="3619a-108">Hay cinco información de red específica que se puede mostrar para cada ubicación de la oficina:</span><span class="sxs-lookup"><span data-stu-id="3619a-108">There are five specific network insights that may be shown for each office location:</span></span>

- [<span data-ttu-id="3619a-109">Salida de red en recorrido</span><span class="sxs-lookup"><span data-stu-id="3619a-109">Backhauled network egress</span></span>](#backhauled-network-egress)
- [<span data-ttu-id="3619a-110">Se ha detectado un mejor rendimiento para los clientes cercanos</span><span class="sxs-lookup"><span data-stu-id="3619a-110">Better performance detected for customers near you</span></span>](#better-performance-detected-for-customers-near-you)
- [<span data-ttu-id="3619a-111">Uso de una puerta principal no óptima del servicio de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3619a-111">Use of a non-optimal Exchange Online service front door</span></span>](#use-of-a-non-optimal-exchange-online-service-front-door)
- [<span data-ttu-id="3619a-112">Uso de puerta frontal del servicio de SharePoint Online no óptimo</span><span class="sxs-lookup"><span data-stu-id="3619a-112">Use of a non-optimal SharePoint Online service front door</span></span>](#use-of-a-non-optimal-sharepoint-online-service-front-door)
- [<span data-ttu-id="3619a-113">Velocidad de descarga baja desde la puerta frontal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="3619a-113">Low download speed from SharePoint front door</span></span>](#low-download-speed-from-sharepoint-front-door)

>[!IMPORTANT]
><span data-ttu-id="3619a-114">Información sobre la red, recomendaciones de rendimiento y evaluaciones en el centro de administración de Microsoft 365 se encuentra actualmente en estado de versión preliminar y solo está disponible para los inquilinos de Microsoft 365 que se han inscrito en el programa de vista previa de características.</span><span class="sxs-lookup"><span data-stu-id="3619a-114">Network insights, performance recommendations and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Microsoft 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="3619a-115">Salida de red en recorrido</span><span class="sxs-lookup"><span data-stu-id="3619a-115">Backhauled network egress</span></span>

<span data-ttu-id="3619a-116">Esta información se mostrará si el servicio de Network Insights detecta que la distancia desde una ubicación de usuario determinada a la red de salida es superior a 500 millas (800 kilómetros), lo que indica que el tráfico de Microsoft 365 se está reteniendo en un dispositivo perimetral de Internet o proxy común.</span><span class="sxs-lookup"><span data-stu-id="3619a-116">This insight will be displayed if the network insights service detects that the distance from a given user location to the network egress is greater than 500 miles (800 kilometers), indicating that Microsoft 365 traffic is being backhauled to a common Internet edge device or proxy.</span></span>

<span data-ttu-id="3619a-117">Esta información se abrevia como "salida" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="3619a-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

![Salida de red en recorrido](Media/m365-mac-perf/m365-mac-perf-insights-detail-backhauled.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="3619a-119">Escenario</span><span class="sxs-lookup"><span data-stu-id="3619a-119">What does this mean?</span></span>

<span data-ttu-id="3619a-120">Esto identifica que la distancia entre la ubicación de la oficina y la red de salida es de más de 500 millas (800 kilómetros).</span><span class="sxs-lookup"><span data-stu-id="3619a-120">This identifies that the distance between the office location and the network egress is more than 500 miles (800 kilometers).</span></span> <span data-ttu-id="3619a-121">La ubicación de la oficina se identifica con una ubicación de equipo cliente confusa y la ubicación de salida de red se identifica con las bases de datos dirección IP inversa para la ubicación.</span><span class="sxs-lookup"><span data-stu-id="3619a-121">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="3619a-122">La ubicación de la oficina puede no ser exacta si servicios de ubicación de Windows está deshabilitado en los equipos.</span><span class="sxs-lookup"><span data-stu-id="3619a-122">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="3619a-123">La ubicación de salida de red puede ser inexacta si la información de la base de datos de direcciones IP inversas no es exacta.</span><span class="sxs-lookup"><span data-stu-id="3619a-123">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="3619a-124">Los detalles de esta visión incluyen la ubicación de la oficina, el porcentaje estimado del usuario total del inquilino en la ubicación, la ubicación de salida actual de la red, la relevancia de la ubicación de salida, la distancia entre la ubicación y el punto de salida actual, la fecha en que se detectó la condición por primera vez y la fecha en que se resolvió la condición.</span><span class="sxs-lookup"><span data-stu-id="3619a-124">Details for this insight include the office location, estimated percentage of total tenant user at the location, the current network egress location, relevance of the egress location, the distance between the location and the current egress point, the date the condition was first detected, and the date the condition was resolved.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="3619a-125">¿Qué tengo que hacer?</span><span class="sxs-lookup"><span data-stu-id="3619a-125">What should I do?</span></span>

<span data-ttu-id="3619a-126">Para esta idea, recomendamos que se acerque la salida de red a la ubicación de la oficina para que la conectividad pueda enrutarse de forma óptima a la red global de Microsoft y a la puerta frontal del servicio Microsoft 365 más cercana.</span><span class="sxs-lookup"><span data-stu-id="3619a-126">For this insight, we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's global network and to the nearest Microsoft 365 service front door.</span></span> <span data-ttu-id="3619a-127">Dejar la red cercana a los usuarios las ubicaciones de Office también permiten un mejor rendimiento en el futuro, ya que Microsoft expande tanto los puntos de presencia de red como las puertas frontales del servicio 365 de Microsoft en el futuro.</span><span class="sxs-lookup"><span data-stu-id="3619a-127">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Microsoft 365 service front doors in the future.</span></span>

<span data-ttu-id="3619a-128">Para obtener más información acerca de cómo resolver este problema, vea [conexiones de red de salida de forma local](office-365-network-connectivity-principles.md#egress-network-connections-locally) en los principios de conectividad de red de [Office 365](office-365-network-connectivity-principles.md).</span><span class="sxs-lookup"><span data-stu-id="3619a-128">For more information about how to resolve this issue, see [Egress network connections locally](office-365-network-connectivity-principles.md#egress-network-connections-locally) in [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="3619a-129">Se ha detectado un mejor rendimiento para los clientes cercanos</span><span class="sxs-lookup"><span data-stu-id="3619a-129">Better performance detected for customers near you</span></span>

<span data-ttu-id="3619a-130">Esta información se mostrará si el servicio de Network Insights detecta que un número importante de clientes en el área metropolitana tiene mejor rendimiento que los usuarios de la organización en esta ubicación de la oficina.</span><span class="sxs-lookup"><span data-stu-id="3619a-130">This insight will be displayed if the network insights service detects that a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="3619a-131">Esta información se abrevia como "homólogos" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="3619a-131">This insight is abbreviated as "Peers" in some summary views.</span></span>

![Rendimiento de red relativo](Media/m365-mac-perf/m365-mac-perf-insights-detail-cust-near-you.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="3619a-133">Escenario</span><span class="sxs-lookup"><span data-stu-id="3619a-133">What does this mean?</span></span>

<span data-ttu-id="3619a-134">Esta visión examina el rendimiento agregado de los clientes de Microsoft 365 en la misma ciudad que esta ubicación de la oficina.</span><span class="sxs-lookup"><span data-stu-id="3619a-134">This insight examines the aggregate performance of Microsoft 365 customers in the same city as this office location.</span></span> <span data-ttu-id="3619a-135">Esta información se muestra si el promedio de latencia de los usuarios es un 10% mayor que la latencia media de los inquilinos vecinos.</span><span class="sxs-lookup"><span data-stu-id="3619a-135">This insight is displayed if the average latency of your users is 10% greater than the average latency of neighboring tenants.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="3619a-136">¿Qué tengo que hacer?</span><span class="sxs-lookup"><span data-stu-id="3619a-136">What should I do?</span></span>

<span data-ttu-id="3619a-137">Puede haber muchas razones para esta condición, como la latencia en la red corporativa o los problemas de diseño de la arquitectura o del ISP, o los cuellos de botella.</span><span class="sxs-lookup"><span data-stu-id="3619a-137">There could be many reasons for this condition, including latency in your corporate network or ISP, bottlenecks, or architecture design issues.</span></span> <span data-ttu-id="3619a-138">Examine la latencia entre cada salto en la ruta entre la red de la oficina y la puerta de frontal de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3619a-138">Examine the latency between each hop in the route between your office network and the current Microsoft 365 front door.</span></span> <span data-ttu-id="3619a-139">Para obtener más información, consulte [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span><span class="sxs-lookup"><span data-stu-id="3619a-139">For more information, see [Office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="3619a-140">Uso de una puerta principal no óptima del servicio de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3619a-140">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="3619a-141">Esta información se mostrará si el servicio de Network Insights detecta que los usuarios de una ubicación específica no se conectan a una puerta de enlace de servicio de Exchange Online óptima.</span><span class="sxs-lookup"><span data-stu-id="3619a-141">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to an optimal Exchange Online service front door.</span></span>

<span data-ttu-id="3619a-142">Esta información se abrevia como "enrutamiento" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="3619a-142">This insight is abbreviated as "Routing" in some summary views.</span></span>

![Puerta delantera no óptima](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-exo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="3619a-144">Escenario</span><span class="sxs-lookup"><span data-stu-id="3619a-144">What does this mean?</span></span>

<span data-ttu-id="3619a-145">Enumeramos las puertas frontales del servicio de Exchange online que son adecuadas para su uso desde la ciudad de la ubicación de la oficina con buen rendimiento.</span><span class="sxs-lookup"><span data-stu-id="3619a-145">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="3619a-146">Si la prueba actual muestra el uso de una puerta de servicio de Exchange online que no está en esta lista, se indica esta recomendación.</span><span class="sxs-lookup"><span data-stu-id="3619a-146">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="3619a-147">¿Qué tengo que hacer?</span><span class="sxs-lookup"><span data-stu-id="3619a-147">What should I do?</span></span>

<span data-ttu-id="3619a-148">El uso de un servicio de Exchange online no óptimo puede deberse a una backhaul? n de red antes de que la red corporativa se deshaga, en cuyo caso se recomienda la salida local y directa de la red.</span><span class="sxs-lookup"><span data-stu-id="3619a-148">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="3619a-149">También podría deberse al uso de un servidor remoto de resolución de recursiva de DNS, en cuyo caso se recomienda alinear el servidor de resolución de DNS recursivo con la salida de red.</span><span class="sxs-lookup"><span data-stu-id="3619a-149">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="use-of-a-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="3619a-150">Uso de puerta frontal del servicio de SharePoint Online no óptimo</span><span class="sxs-lookup"><span data-stu-id="3619a-150">Use of a non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="3619a-151">Esta información se mostrará si el servicio de Network Insights detecta que los usuarios de una ubicación específica no se conectan a la puerta frontal del servicio de SharePoint Online más cercana.</span><span class="sxs-lookup"><span data-stu-id="3619a-151">This insight will be displayed if the network insights service detects that users in a specific location are not connecting to the closest SharePoint Online service front door.</span></span>

<span data-ttu-id="3619a-152">Esta información se abrevia como "AFD" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="3619a-152">This insight is abbreviated as "Afd" in some summary views.</span></span>

![Puerta delantera no óptima](Media/m365-mac-perf/m365-mac-perf-insights-detail-front-door-spo.png)

### <a name="what-does-this-mean"></a><span data-ttu-id="3619a-154">Escenario</span><span class="sxs-lookup"><span data-stu-id="3619a-154">What does this mean?</span></span>

<span data-ttu-id="3619a-155">Identificamos la puerta frontal del servicio de SharePoint Online a la que se conecta el cliente de prueba.</span><span class="sxs-lookup"><span data-stu-id="3619a-155">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="3619a-156">A continuación, para la ciudad de la ubicación de la oficina, la encontrarás en la puerta frontal esperada del servicio de SharePoint Online para esa ciudad.</span><span class="sxs-lookup"><span data-stu-id="3619a-156">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="3619a-157">Si no coincide, realizamos esta recomendación.</span><span class="sxs-lookup"><span data-stu-id="3619a-157">If it doesn't match, then we make this recommendation.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="3619a-158">¿Qué tengo que hacer?</span><span class="sxs-lookup"><span data-stu-id="3619a-158">What should I do?</span></span>

<span data-ttu-id="3619a-159">El uso de un servicio de SharePoint Online no óptimo puede deberse a la backhaul? n de red antes de que la red corporativa se deshaga, en cuyo caso se recomienda la salida local y directa de la red.</span><span class="sxs-lookup"><span data-stu-id="3619a-159">Use of a non-optimal SharePoint Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="3619a-160">También podría deberse al uso de un servidor remoto de resolución de recursiva de DNS, en cuyo caso se recomienda alinear el servidor de resolución de DNS recursivo con la salida de red.</span><span class="sxs-lookup"><span data-stu-id="3619a-160">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="3619a-161">Velocidad de descarga baja desde la puerta frontal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="3619a-161">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="3619a-162">Esta información se mostrará si el servicio de Network Insights detecta que el ancho de banda entre la ubicación específica de la oficina y SharePoint Online es inferior a 1 MBps.</span><span class="sxs-lookup"><span data-stu-id="3619a-162">This insight will be displayed if the network insights service detects that bandwidth between the specific office location and SharePoint Online is less than 1 MBps.</span></span>

<span data-ttu-id="3619a-163">Esta información se abrevia como "rendimiento" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="3619a-163">This insight is abbreviated as "Throughput" in some summary views.</span></span>

### <a name="what-does-this-mean"></a><span data-ttu-id="3619a-164">Escenario</span><span class="sxs-lookup"><span data-stu-id="3619a-164">What does this mean?</span></span>

<span data-ttu-id="3619a-165">La velocidad de descarga que un usuario puede obtener del servicio de SharePoint Online y OneDrive para la empresa las puertas del anverso se mide en megabytes por segundo (MBps).</span><span class="sxs-lookup"><span data-stu-id="3619a-165">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="3619a-166">Si este valor es inferior a 1 MBps, proporcionaremos esta visión.</span><span class="sxs-lookup"><span data-stu-id="3619a-166">If this value is less than 1 MBps then we provide this insight.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="3619a-167">¿Qué tengo que hacer?</span><span class="sxs-lookup"><span data-stu-id="3619a-167">What should I do?</span></span>

<span data-ttu-id="3619a-168">Para mejorar la velocidad de descarga, es posible que sea necesario aumentar el ancho de banda.</span><span class="sxs-lookup"><span data-stu-id="3619a-168">To improve download speeds, bandwidth may need to be increased.</span></span> <span data-ttu-id="3619a-169">Como alternativa, puede que exista una congestión de red entre los equipos de los usuarios en la ubicación de la oficina y la puerta de servicio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="3619a-169">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="3619a-170">A veces se denomina pérdida de Congestive y restringe la velocidad de descarga disponible para los usuarios, incluso si hay suficiente ancho de banda disponible.</span><span class="sxs-lookup"><span data-stu-id="3619a-170">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

## <a name="china-user-optimal-network-egress"></a><span data-ttu-id="3619a-171">Salida de red óptima de usuario de China</span><span class="sxs-lookup"><span data-stu-id="3619a-171">China user optimal network egress</span></span>

<span data-ttu-id="3619a-172">Esta información se mostrará si su organización tiene usuarios en China que se conectan a su inquilino de Microsoft 365 en otras ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="3619a-172">This insight will be displayed if your organization has users in China connecting to your Microsoft 365 tenant in other geographic locations.</span></span> 

### <a name="what-does-this-mean"></a><span data-ttu-id="3619a-173">Escenario</span><span class="sxs-lookup"><span data-stu-id="3619a-173">What does this mean?</span></span>

<span data-ttu-id="3619a-174">Si su organización tiene conectividad WAN privada, le recomendamos configurar un circuito de WAN de red desde sus ubicaciones de oficina en China que tenga red de salida a Internet en cualquiera de las siguientes ubicaciones:</span><span class="sxs-lookup"><span data-stu-id="3619a-174">If your organization has private WAN connectivity, we recommend configuring a network WAN circuit from your office locations in China that has network egress to the Internet in any of the following locations:</span></span>

- <span data-ttu-id="3619a-175">RAE de Hong Kong</span><span class="sxs-lookup"><span data-stu-id="3619a-175">Hong Kong</span></span>
- <span data-ttu-id="3619a-176">Japón</span><span class="sxs-lookup"><span data-stu-id="3619a-176">Japan</span></span>
- <span data-ttu-id="3619a-177">Taiwán</span><span class="sxs-lookup"><span data-stu-id="3619a-177">Taiwan</span></span>
- <span data-ttu-id="3619a-178">Corea del Sur</span><span class="sxs-lookup"><span data-stu-id="3619a-178">South Korea</span></span>
- <span data-ttu-id="3619a-179">Singapur</span><span class="sxs-lookup"><span data-stu-id="3619a-179">Singapore</span></span>
- <span data-ttu-id="3619a-180">Malasia</span><span class="sxs-lookup"><span data-stu-id="3619a-180">Malaysia</span></span>

<span data-ttu-id="3619a-181">Internet sale aún más de los usuarios que estas ubicaciones reducirán el rendimiento y los resultados en China podrían causar problemas de alta latencia y conectividad debido a congestión transfronteriza.</span><span class="sxs-lookup"><span data-stu-id="3619a-181">Internet egress further away from users than these locations will reduce performance, and egress in China may cause high latency and connectivity issues due to cross-border congestion.</span></span>

### <a name="what-should-i-do"></a><span data-ttu-id="3619a-182">¿Qué tengo que hacer?</span><span class="sxs-lookup"><span data-stu-id="3619a-182">What should I do?</span></span>

<span data-ttu-id="3619a-183">Para obtener más información acerca de cómo mitigar problemas de rendimiento relacionados con esta visión, consulte [Office 365 global tenant performance Optimization for China users](https://docs.microsoft.com/office365/enterprise/office-365-networking-china).</span><span class="sxs-lookup"><span data-stu-id="3619a-183">For more information about how to mitigate performance issues related to this insight, see [Office 365 global tenant performance optimization for China users](https://docs.microsoft.com/office365/enterprise/office-365-networking-china).</span></span>

## <a name="related-topics"></a><span data-ttu-id="3619a-184">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="3619a-184">Related topics</span></span>

[<span data-ttu-id="3619a-185">Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3619a-185">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="3619a-186">Evaluación de red de Microsoft 365 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3619a-186">Microsoft 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="3619a-187">Prueba de conectividad de Microsoft 365 en el centro de administración de M365 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3619a-187">Microsoft 365 connectivity test in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)

[<span data-ttu-id="3619a-188">Servicios de ubicación de conectividad de red 365 de Microsoft (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3619a-188">Microsoft 365 Network Connectivity Location Services (preview)</span></span>](office-365-network-mac-location-services.md)
