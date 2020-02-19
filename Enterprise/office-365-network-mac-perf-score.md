---
title: Evaluación de la red de Office 365 (versión preliminar)
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
description: Evaluación de la red de Office 365 (versión preliminar)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106442"
---
# <a name="office-365-network-assessment-preview"></a><span data-ttu-id="3d56b-103">Evaluación de la red de Office 365 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3d56b-103">Office 365 network assessment (preview)</span></span>

<span data-ttu-id="3d56b-104">La evaluación de red de Office 365 indica el impacto relativo de la experiencia del usuario con respecto a la conectividad de red del cliente.</span><span class="sxs-lookup"><span data-stu-id="3d56b-104">The Office 365 network assessment indicates the relative user experience impact from customer network connectivity.</span></span> <span data-ttu-id="3d56b-105">El impacto de cualquier conectividad de red de Microsoft se excluye de esto para permitir a los clientes optimizar los diseños de red de los que son responsables.</span><span class="sxs-lookup"><span data-stu-id="3d56b-105">The impact of any Microsoft owned network connectivity is excluded from this to enable customers to optimize network designs for which they are responsible.</span></span>

<span data-ttu-id="3d56b-106">Se calcula a partir de las medidas que afectan a la experiencia del usuario en las cargas de trabajo de Office 365 y se muestran como un porcentaje con un intervalo de 0 a 100.</span><span class="sxs-lookup"><span data-stu-id="3d56b-106">It is calculated from measurements that impact user experience in key Office 365 workloads and shown as a percentage with a range of 0 to 100.</span></span>

<span data-ttu-id="3d56b-107">Una puntuación de red muy baja sugiere que los clientes de Office 365 tendrán problemas significativos para conectar o hacer que el usuario responda correctamente.</span><span class="sxs-lookup"><span data-stu-id="3d56b-107">A very low network score suggests that Office 365 clients will have significant problems connecting or remaining user responsive.</span></span> <span data-ttu-id="3d56b-108">Una puntuación de 80% representa la conectividad de red, en la que no se debe esperar recibir quejas del usuario sobre la experiencia del usuario de Office 365 debido al rendimiento de la red.</span><span class="sxs-lookup"><span data-stu-id="3d56b-108">A score of 80% represents network connectivity where you should not expect to receive user complaints about your Office 365 user experience due to your network performance.</span></span> <span data-ttu-id="3d56b-109">A medida que se realizan mejoras en la conectividad de red, esta puntuación aumentará junto con la experiencia del usuario.</span><span class="sxs-lookup"><span data-stu-id="3d56b-109">As network connectivity improvements are made, this score will increase along with user experience.</span></span>

>[!IMPORTANT]
><span data-ttu-id="3d56b-110">Las recomendaciones de rendimiento de red, información y evaluaciones en el centro de administración de Microsoft 365 se encuentra actualmente en estado de versión preliminar y solo está disponible para los inquilinos de Office 365 que se han inscrito en el programa de vista previa de características.</span><span class="sxs-lookup"><span data-stu-id="3d56b-110">Network performance recommendations, insights and assessments in the Microsoft 365 Admin Center is currently in preview status, and is only available for Office 365 tenants that have been enrolled in the feature preview program.</span></span>

## <a name="exchange-online"></a><span data-ttu-id="3d56b-111">Exchange Online</span><span class="sxs-lookup"><span data-stu-id="3d56b-111">Exchange Online</span></span>

<span data-ttu-id="3d56b-112">Para Exchange Online se mide la latencia TCP desde el equipo cliente al servidor front-end de Exchange.</span><span class="sxs-lookup"><span data-stu-id="3d56b-112">For Exchange Online the TCP latency from the client machine to the Exchange front end server is measured.</span></span> <span data-ttu-id="3d56b-113">Esto puede verse afectado por la distancia que la red viaja a través de la LAN y la WAN de los clientes.</span><span class="sxs-lookup"><span data-stu-id="3d56b-113">This can be impacted by the distance the network travels over the customers LAN and WAN.</span></span> <span data-ttu-id="3d56b-114">También puede verse afectado por servicios o dispositivos intermedios de red que retrasn la conectividad o provocan la reenvío de paquetes.</span><span class="sxs-lookup"><span data-stu-id="3d56b-114">It can also be impacted by network intermediary devices or services which delay the connectivity or cause packets to be resent.</span></span>

## <a name="sharepoint-online"></a><span data-ttu-id="3d56b-115">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="3d56b-115">SharePoint Online</span></span>

<span data-ttu-id="3d56b-116">Para SharePoint Online, se mide la velocidad de descarga disponible para que un usuario tenga acceso a un documento.</span><span class="sxs-lookup"><span data-stu-id="3d56b-116">For SharePoint Online the download speed available for a user to access a document is measured.</span></span> <span data-ttu-id="3d56b-117">Esto puede verse afectado por el ancho de banda disponible en los circuitos de red entre el equipo cliente y la red de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3d56b-117">This can be impacted by the bandwidth available on network circuits between the client machine and Microsoft’s network.</span></span> <span data-ttu-id="3d56b-118">También suele afectar a la congestión de la red que existe en los cuellos de botella en dispositivos de red complejos o en áreas de Wi-Fi de mala cobertura.</span><span class="sxs-lookup"><span data-stu-id="3d56b-118">It is also often impacted by network congestion that exists in bottlenecks in complex network devices or in poor coverage Wi-Fi areas.</span></span>

## <a name="microsoft-teams"></a><span data-ttu-id="3d56b-119">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3d56b-119">Microsoft Teams</span></span>

<span data-ttu-id="3d56b-120">Para Microsoft Teams, la calidad de la red se mide como latencia UDP, vibración UDP y pérdida de paquetes UDP.</span><span class="sxs-lookup"><span data-stu-id="3d56b-120">For Microsoft Teams the Network quality is measured as UDP latency, UDP jitter, and UDP packet loss.</span></span> <span data-ttu-id="3d56b-121">UDP se usa para la conectividad de medios de audio y vídeo de conferencias y llamadas de Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3d56b-121">UDP is used for call and conferencing audio and video media connectivity for Microsoft Teams.</span></span> <span data-ttu-id="3d56b-122">Esto se puede ver afectado por los mismos factores que para la latencia y la velocidad de descarga, además de las brechas de conectividad en la compatibilidad con UDP de una red, ya que UDP se configura por separado en el protocolo TCP más común.</span><span class="sxs-lookup"><span data-stu-id="3d56b-122">This can be impacted by the same factors as for latency and download speed in addition to connectivity gaps in a network’s UDP support since UDP is configured separately to the more common TCP protocol.</span></span>

## <a name="tenant-network-score-and-office-location-network-score"></a><span data-ttu-id="3d56b-123">Puntuación de red de inquilinos y puntuación de red de ubicación de oficina</span><span class="sxs-lookup"><span data-stu-id="3d56b-123">Tenant network score and office location network score</span></span>

<span data-ttu-id="3d56b-124">Una puntuación de red mide el diseño del perímetro de red de una ubicación de la oficina a la red de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="3d56b-124">A network score measures the design of the network perimeter of an office location to Microsoft’s network.</span></span> <span data-ttu-id="3d56b-125">Las mejoras en el perímetro de la red se realizan mejor en cada ubicación de la oficina o cuando se agrega conectividad de red puede haber mejoras que afectan a varias ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="3d56b-125">Improvements to the network perimeter is best done at each office location, or where network connectivity is aggregated there may be improvements that impact multiple locations.</span></span>
<span data-ttu-id="3d56b-126">Se muestra una puntuación de red para todo el inquilino de Office 365 en la página información general de rendimiento de red y una puntuación de red específica para cada ubicación de la oficina detectada en la página de Resumen de esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="3d56b-126">We show a network score for the whole Office 365 tenant on the network performance overview page and a specific network score for each detected office location on that location’s summary page.</span></span>

## <a name="network-score-panel"></a><span data-ttu-id="3d56b-127">Panel de puntuación de red</span><span class="sxs-lookup"><span data-stu-id="3d56b-127">Network score panel</span></span>

<span data-ttu-id="3d56b-128">Cada puntuación de red, ya sea para el inquilino o para una ubicación específica de la oficina, muestra un panel con detalles sobre la puntuación.</span><span class="sxs-lookup"><span data-stu-id="3d56b-128">Each network score whether for the tenant or for a specific office location shows a panel with details about the score.</span></span> <span data-ttu-id="3d56b-129">Este panel muestra un gráfico de barras con la puntuación como un porcentaje y como los puntos totales para cada carga de trabajo de componente, incluidas solo cargas de trabajo en las que se recibieron datos de medición.</span><span class="sxs-lookup"><span data-stu-id="3d56b-129">This panel shows a bar chart of the score both as a percentage and as the total points for each component workload including only workloads where measurement data was received.</span></span> <span data-ttu-id="3d56b-130">Para una puntuación de red de ubicación de oficina, también se muestra un benchmark que es la mediana de todos los clientes de Office 365 que han notificado datos en la misma ciudad que la ubicación de la oficina.</span><span class="sxs-lookup"><span data-stu-id="3d56b-130">For an office location network score we also show a benchmark which is the median of all Office 365 clients that reported data in the same City as your office location.</span></span>

<span data-ttu-id="3d56b-131">El desglose de la puntuación en el panel muestra la puntuación de cada una de las cargas de trabajo de componente.</span><span class="sxs-lookup"><span data-stu-id="3d56b-131">The score breakdown in the panel shows the score for each of the component workloads.</span></span>

<span data-ttu-id="3d56b-132">El historial de puntuación muestra los últimos 30 días de la puntuación y el Banco de pruebas.</span><span class="sxs-lookup"><span data-stu-id="3d56b-132">The score history shows the past 30 days of the score and the benchmark.</span></span>

## <a name="related-topics"></a><span data-ttu-id="3d56b-133">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="3d56b-133">Related topics</span></span>

[<span data-ttu-id="3d56b-134">Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3d56b-134">Network performance recommendations in the Microsoft 365 Admin Center (preview)</span></span>](office-365-network-mac-perf-overview.md)

[<span data-ttu-id="3d56b-135">Office 365 Network performance Insight (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3d56b-135">Office 365 network performance insights (preview)</span></span>](office-365-network-mac-perf-insights.md)

[<span data-ttu-id="3d56b-136">Herramienta de incorporación de red de Office 365 en el centro de administración de M365 (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="3d56b-136">Office 365 Network Onboarding Tool in the M365 Admin Center (preview)</span></span>](office-365-network-mac-perf-onboarding-tool.md)
