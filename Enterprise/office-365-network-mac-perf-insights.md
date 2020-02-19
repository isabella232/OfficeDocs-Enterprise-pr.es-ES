---
title: Office 365 Network performance Insight (versión preliminar)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Office 365 Network performance Insight (versión preliminar)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106449"
---
# <a name="office-365-network-performance-insights-preview"></a><span data-ttu-id="51a0f-103">Office 365 Network performance Insight (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="51a0f-103">Office 365 network performance insights (preview)</span></span>

<span data-ttu-id="51a0f-104">Las páginas de rendimiento de la red del centro de administración de 365 de Microsoft muestran Office 365 Network Insights, que puede ayudarle a diseñar perímetros de red para sus ubicaciones de oficina.</span><span class="sxs-lookup"><span data-stu-id="51a0f-104">The Microsoft 365 Admin Center network performance pages show Office 365 network insights which can help in designing network perimeters for your office locations.</span></span> <span data-ttu-id="51a0f-105">Hay cinco información de red específica que se puede mostrar para cada ubicación de la oficina.</span><span class="sxs-lookup"><span data-stu-id="51a0f-105">There are five specific network insights that may be shown for each office location.</span></span>

>[!IMPORTANT]
><span data-ttu-id="51a0f-106">Las recomendaciones de rendimiento de red, información y evaluaciones en el centro de administración de Microsoft 365 se encuentra actualmente en estado de versión preliminar y solo está disponible para los inquilinos de Office 365 que se han inscrito en el programa de vista previa de características.</span><span class="sxs-lookup"><span data-stu-id="51a0f-106">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="backhauled-network-egress"></a><span data-ttu-id="51a0f-107">Salida de red en recorrido</span><span class="sxs-lookup"><span data-stu-id="51a0f-107">Backhauled network egress</span></span>

<span data-ttu-id="51a0f-108">La distancia desde la ubicación del usuario hasta la red de salida es superior a 500 millas (800 kilómetros) y se espera que esto afecte al rendimiento.</span><span class="sxs-lookup"><span data-stu-id="51a0f-108">The distance from the user location to the network egress is greater than 500 miles (800 kilometers) and this is expected to be impacting performance.</span></span> <span data-ttu-id="51a0f-109">Se recomienda la salida local más cercana al usuario.</span><span class="sxs-lookup"><span data-stu-id="51a0f-109">Local egress closer to the user is recommended.</span></span>

<span data-ttu-id="51a0f-110">Esto identifica que la distancia entre la ubicación de la oficina y la red de salida es de más de 500 millas.</span><span class="sxs-lookup"><span data-stu-id="51a0f-110">This identifies that the distance between the office location and the network egress is more than 500 miles.</span></span> <span data-ttu-id="51a0f-111">La ubicación de la oficina se identifica con una ubicación de equipo cliente confusa y la ubicación de salida de red se identifica con las bases de datos dirección IP inversa para la ubicación.</span><span class="sxs-lookup"><span data-stu-id="51a0f-111">The office location is identified by an obfuscated client machine location and the network egress location is identified by using reverse IP Address to location databases.</span></span> <span data-ttu-id="51a0f-112">La ubicación de la oficina puede no ser exacta si servicios de ubicación de Windows está deshabilitado en los equipos.</span><span class="sxs-lookup"><span data-stu-id="51a0f-112">The office location may be inaccurate if Windows Location Services is disabled on machines.</span></span> <span data-ttu-id="51a0f-113">La ubicación de salida de red puede ser inexacta si la información de la base de datos de direcciones IP inversas no es exacta.</span><span class="sxs-lookup"><span data-stu-id="51a0f-113">The network egress location may be inaccurate if the reverse IP Address database information is inaccurate.</span></span>

<span data-ttu-id="51a0f-114">Los detalles de esta visión incluyen la ubicación de la oficina, la ubicación de salida de red y la distancia entre ellas.</span><span class="sxs-lookup"><span data-stu-id="51a0f-114">Details for this insight include the office location, the network egress location, and the distance between them.</span></span>

<span data-ttu-id="51a0f-115">Para esta visión, recomendamos que se acerque la salida de red a la ubicación de la oficina para que la conectividad pueda enrutarse de forma óptima a la red de Microsoft en Internet y a las puertas frontales del servicio 365 de Office.</span><span class="sxs-lookup"><span data-stu-id="51a0f-115">For this insight we would recommend network egress closer to the office location so that connectivity can route optimally to Microsoft's network on the Internet and onto Office 365 service front doors.</span></span> <span data-ttu-id="51a0f-116">Dejar la red cercana a los usuarios las ubicaciones de la oficina también permiten un mejor rendimiento en el futuro, ya que Microsoft expande los puntos de la red de presencia y las puertas frontales del servicio de Office 365 en el futuro.</span><span class="sxs-lookup"><span data-stu-id="51a0f-116">Having close network egress to users office locations also allows for improved performance in the future as Microsoft expands both network points of presence and Office 365 service front doors in the future.</span></span>

<span data-ttu-id="51a0f-117">Esta información se abrevia como "salida" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="51a0f-117">This insight is abbreviated as "Egress" in some summary views.</span></span>

## <a name="better-performance-detected-for-customers-near-you"></a><span data-ttu-id="51a0f-118">Se ha detectado un mejor rendimiento para los clientes cercanos</span><span class="sxs-lookup"><span data-stu-id="51a0f-118">Better performance detected for customers near you</span></span>

<span data-ttu-id="51a0f-119">Dado que un número significativo de clientes en el área metropolitana tiene mejor rendimiento que los usuarios de la organización en esta ubicación de la oficina.</span><span class="sxs-lookup"><span data-stu-id="51a0f-119">Since a significant number of customers in your metro area have better performance than users in your organization at this office location.</span></span>

<span data-ttu-id="51a0f-120">Esto se centra en el rendimiento agregado de los clientes de Office 365 en la misma ciudad que esta ubicación de la oficina.</span><span class="sxs-lookup"><span data-stu-id="51a0f-120">This looks at the aggregate performance of Office 365 customers in the same city as this office location.</span></span>

![Rendimiento de red relativo](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

<span data-ttu-id="51a0f-122">Se calcula el porcentaje de clientes de Office 365 en la misma ciudad en los mejores depósitos de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="51a0f-122">We calculate the percentage of Office 365 customers in the same city in better performance buckets.</span></span> <span data-ttu-id="51a0f-123">Si este número es el 10% de más, muestra el conocimiento de la red.</span><span class="sxs-lookup"><span data-stu-id="51a0f-123">If this number if 10% of more then we show the network insight.</span></span>

<span data-ttu-id="51a0f-124">Esta información se abrevia como "homólogos" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="51a0f-124">This insight is abbreviated as "Peers" in some summary views.</span></span>

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a><span data-ttu-id="51a0f-125">Uso de una puerta principal no óptima del servicio de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="51a0f-125">Use of a non-optimal Exchange Online service front door</span></span>

<span data-ttu-id="51a0f-126">El usuario no se conecta a una puerta de enlace de servicio 365 de Office óptima y se espera que se vea afectado el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="51a0f-126">The user is not connecting to an optimal Office 365 service front door and this is expected to be impacting performance.</span></span>

<span data-ttu-id="51a0f-127">Enumeramos las puertas frontales del servicio de Exchange online que son adecuadas para su uso desde la ciudad de la ubicación de la oficina con buen rendimiento.</span><span class="sxs-lookup"><span data-stu-id="51a0f-127">We list Exchange Online service front doors which are suitable for use from the office location city with good performance.</span></span> <span data-ttu-id="51a0f-128">Si la prueba actual muestra el uso de una puerta de servicio de Exchange online que no está en esta lista, se indica esta recomendación.</span><span class="sxs-lookup"><span data-stu-id="51a0f-128">If the current test shows use of an Exchange Online service front door not on this list, then we call out this recommendation.</span></span>

<span data-ttu-id="51a0f-129">El uso de un servicio de Exchange online no óptimo puede deberse a una backhaul? n de red antes de que la red corporativa se deshaga, en cuyo caso se recomienda la salida local y directa de la red.</span><span class="sxs-lookup"><span data-stu-id="51a0f-129">Use of a non-optimal Exchange Online service front door could be caused by network backhaul before the corporate network egress in which case we recommend local and direct network egress.</span></span> <span data-ttu-id="51a0f-130">También podría deberse al uso de un servidor remoto de resolución de recursiva de DNS, en cuyo caso se recomienda alinear el servidor de resolución de DNS recursivo con la salida de red.</span><span class="sxs-lookup"><span data-stu-id="51a0f-130">It could also be caused by use of a remote DNS Recursive Resolver server in which case we recommend aligning the DNS Recursive Resolver server with the network egress.</span></span>

<span data-ttu-id="51a0f-131">Esta información se abrevia como "enrutamiento" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="51a0f-131">This insight is abbreviated as "Routing" in some summary views.</span></span>

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a><span data-ttu-id="51a0f-132">Uso de puerta frontal no óptima del servicio de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="51a0f-132">Use of non-optimal SharePoint Online service front door</span></span>

<span data-ttu-id="51a0f-133">El usuario no se conecta al servicio de puerta de enlace frontal de SharePoint Online más cercano.</span><span class="sxs-lookup"><span data-stu-id="51a0f-133">The user is not connecting to the closest SharePoint Online service front door.</span></span> <span data-ttu-id="51a0f-134">Se espera que se vea afectado el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="51a0f-134">This is expected to be impacting performance.</span></span>

<span data-ttu-id="51a0f-135">Identificamos la puerta frontal del servicio de SharePoint Online a la que se conecta el cliente de prueba.</span><span class="sxs-lookup"><span data-stu-id="51a0f-135">We identify the SharePoint Online service front door that the test client is connecting to.</span></span> <span data-ttu-id="51a0f-136">A continuación, para la ciudad de la ubicación de la oficina, la encontrarás en la puerta frontal esperada del servicio de SharePoint Online para esa ciudad.</span><span class="sxs-lookup"><span data-stu-id="51a0f-136">Then for the office location city we compare that to the expected SharePoint Online service front door for that city.</span></span> <span data-ttu-id="51a0f-137">Si no coincide, realizamos esta recomendación.</span><span class="sxs-lookup"><span data-stu-id="51a0f-137">If it doesn't match, then we make this recommendation.</span></span>

<span data-ttu-id="51a0f-138">Esta información se abrevia como "AFD" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="51a0f-138">This insight is abbreviated as "Afd" in some summary views.</span></span>

## <a name="low-download-speed-from-sharepoint-front-door"></a><span data-ttu-id="51a0f-139">Velocidad de descarga baja desde la puerta frontal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="51a0f-139">Low download speed from SharePoint front door</span></span>

<span data-ttu-id="51a0f-140">La velocidad de descarga de red sub óptima detecta el tiempo que se tarda en cargar documentos de OneDrive para la empresa.</span><span class="sxs-lookup"><span data-stu-id="51a0f-140">Sub optimal network download speed detected which impacts how long it takes to load documents from OneDrive for Business.</span></span>

<span data-ttu-id="51a0f-141">La velocidad de descarga que un usuario puede obtener del servicio de SharePoint Online y OneDrive para la empresa las puertas del anverso se mide en megabytes por segundo (MBps).</span><span class="sxs-lookup"><span data-stu-id="51a0f-141">The download speed that a user can get from SharePoint Online and OneDrive for Business service front doors is measured in megabytes per second (MBps).</span></span> <span data-ttu-id="51a0f-142">Si este valor es inferior a 1 MBps, proporcionaremos esta visión.</span><span class="sxs-lookup"><span data-stu-id="51a0f-142">If this value is less than 1 MBps then we provide this insight.</span></span>

<span data-ttu-id="51a0f-143">Para mejorar la velocidad de descarga, es posible que sea necesario aumentar el ancho de banda que puede tener un usuario.</span><span class="sxs-lookup"><span data-stu-id="51a0f-143">To improve download speed that a user can get bandwidth may need to be increased.</span></span> <span data-ttu-id="51a0f-144">Como alternativa, puede que exista una congestión de red entre los equipos de los usuarios en la ubicación de la oficina y la puerta de servicio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="51a0f-144">Alternatively, there may be network congestion between user machines at the office location and the SharePoint Online service front door.</span></span> <span data-ttu-id="51a0f-145">A veces se denomina pérdida de Congestive y restringe la velocidad de descarga disponible para los usuarios, incluso si hay suficiente ancho de banda disponible.</span><span class="sxs-lookup"><span data-stu-id="51a0f-145">This is sometimes called congestive loss and it restricts the download speed available to users even if sufficient bandwidth is available.</span></span>

<span data-ttu-id="51a0f-146">Esta información se abrevia como "rendimiento" en algunas vistas de resumen.</span><span class="sxs-lookup"><span data-stu-id="51a0f-146">This insight is abbreviated as "Throughput" in some summary views.</span></span>

## <a name="related-topics"></a><span data-ttu-id="51a0f-147">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="51a0f-147">Related topics</span></span>

[<span data-ttu-id="51a0f-148">Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="51a0f-148">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="51a0f-149">Evaluación de la red de Office 365 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="51a0f-149">Office 365 network assessment (preview)</span></span>](office-365-network-mac-perf-score.md)

[<span data-ttu-id="51a0f-150">Herramienta de incorporación de red de Office 365 en el centro de administración de M365 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="51a0f-150">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
