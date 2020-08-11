---
title: Configurar la red para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: ''
description: Encuentre vínculos a artículos con información que le ayudará a configurar la red para Microsoft 365, incluida una descripción general de la conectividad de red y una lista de puntos de conexión.
ms.openlocfilehash: 2c5966dc169a189a4f5040d4b5673859a38e6640
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605212"
---
# <a name="set-up-your-network-for-microsoft-365"></a><span data-ttu-id="17d8d-103">Configurar la red para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-103">Set up your network for Microsoft 365</span></span>

<span data-ttu-id="17d8d-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="17d8d-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="17d8d-p101">Una parte importante de la incorporación de Microsoft 365 es asegurarse de que la red y las conexiones de Internet están configuradas para un acceso optimizado. La configuración de la red local para tener acceso a una nube de software como servicio (SaaS) distribuida globalmente es diferente de una red tradicional optimizada para el tráfico a los centros de recursos locales y una conexión a Internet central.</span><span class="sxs-lookup"><span data-stu-id="17d8d-p101">An important part of your Microsoft 365 onboarding is to ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters and a central Internet connection.</span></span> 

<span data-ttu-id="17d8d-107">Use estos artículos para comprender las principales diferencias, así como para modificar los dispositivos perimetrales, los equipos cliente y la red local a fin de obtener el mejor rendimiento para sus usuarios locales.</span><span class="sxs-lookup"><span data-stu-id="17d8d-107">Use these articles to understand the key differences and to modify your edge devices, client computers, and on-premises network to get the best performance for your on-premises users.</span></span>

## <a name="how-microsoft-365-networking-works"></a><span data-ttu-id="17d8d-108">Cómo funciona la red de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-108">How Microsoft 365 networking works</span></span>

<span data-ttu-id="17d8d-109">Consulte estos artículos para obtener información general sobre la conectividad de Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="17d8d-109">See these articles for an overview of connectivity for Microsoft 365:</span></span>

- [<span data-ttu-id="17d8d-110">Información general de conectividad de red de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-110">Microsoft 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="17d8d-111">Principios de conectividad de red de 365 de Microsoft</span><span class="sxs-lookup"><span data-stu-id="17d8d-111">Microsoft 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="17d8d-112">Evaluar la conectividad de red de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-112">Assessing Microsoft 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="17d8d-113">Para obtener consejos sobre cómo mejorar el rendimiento, consulte [planeación de red y ajuste del rendimiento para Microsoft 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="17d8d-113">For advice on enhancing performance, see [Network planning and performance tuning for Microsoft 365](network-planning-and-performance.md).</span></span>

## <a name="support-microsoft-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="17d8d-114">Compatibilidad con redes de Microsoft 365 como proveedor de equipo de red</span><span class="sxs-lookup"><span data-stu-id="17d8d-114">Support Microsoft 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="17d8d-p102">Si es un proveedor de equipos de red, únase al [Programa para partners de redes de Office 365](office-365-networking-partner-program.md). Inscríbase en el programa para compilar principios de conectividad de red de Office 365 en sus productos y soluciones.</span><span class="sxs-lookup"><span data-stu-id="17d8d-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="17d8d-117">Puntos de conexión de Office 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-117">Office 365 endpoints</span></span>

<span data-ttu-id="17d8d-118">Los puntos de conexión son el conjunto de direcciones IP de destino, nombres de dominio DNS y URL para el tráfico de Office 365 en Internet.</span><span class="sxs-lookup"><span data-stu-id="17d8d-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="17d8d-p103">Para optimizar el rendimiento de los servicios basados en la nube de Office 365, algunos puntos de conexión necesitan un tratamiento especial por parte de los exploradores cliente y los dispositivos de la red perimetral. Estos dispositivos incluyen firewalls, inspección e interrupción SSL, dispositivos de inspección de paquetes y sistemas de prevención de pérdida de datos.</span><span class="sxs-lookup"><span data-stu-id="17d8d-p103">To optimize performance to Office 365 cloud-based services, some endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="17d8d-121">Vea [Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md) para obtener detalles.</span><span class="sxs-lookup"><span data-stu-id="17d8d-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="17d8d-p104">Actualmente, hay cinco nubes diferentes de Office 365. En esta tabla se le indicará la lista de puntos de conexión de cada una.</span><span class="sxs-lookup"><span data-stu-id="17d8d-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="17d8d-124">Puntos de conexión mundiales</span><span class="sxs-lookup"><span data-stu-id="17d8d-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="17d8d-125">Puntos de conexión para suscripciones a Office 365 de todo el mundo, que incluyen Government Community Cloud (GCC) de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="17d8d-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="17d8d-126">Puntos de conexión de DoD de Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="17d8d-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="17d8d-127">Puntos de conexión para las suscripciones del Department of Defense (DoD) de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="17d8d-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="17d8d-128">Puntos de conexión de GCC High de Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="17d8d-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="17d8d-129">Puntos de conexión para suscripciones a Government Community Cloud High (GCC High) de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="17d8d-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="17d8d-130">Puntos de conexión de Office 365 operado por 21Vianet</span><span class="sxs-lookup"><span data-stu-id="17d8d-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="17d8d-131">Puntos de conexión de Office 365 operado por 21Vianet, que está diseñado para satisfacer las necesidades de Office 365 en China.</span><span class="sxs-lookup"><span data-stu-id="17d8d-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="17d8d-132">Puntos de conexión de Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="17d8d-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="17d8d-133">Puntos de conexión de una nube independiente en Europa para los clientes con más regulaciones en Alemania, la Unión Europea (UE) y la Asociación Europea de Libre Comercio (AELC).</span><span class="sxs-lookup"><span data-stu-id="17d8d-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="17d8d-134">Para automatizar la obtención de la lista más reciente de puntos de conexión para su nube de Office 365, vea [Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="17d8d-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="17d8d-135">Para consultar puntos de conexión adicionales, vea estos artículos:</span><span class="sxs-lookup"><span data-stu-id="17d8d-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="17d8d-136">Puntos de conexión adicionales no incluidos en el servicio web</span><span class="sxs-lookup"><span data-stu-id="17d8d-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="17d8d-137">Solicitudes de red en Office 2016 para Mac</span><span class="sxs-lookup"><span data-stu-id="17d8d-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-microsoft-365-networking"></a><span data-ttu-id="17d8d-138">Temas adicionales para redes de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-138">Additional topics for Microsoft 365 networking</span></span>

<span data-ttu-id="17d8d-139">Consulte estos artículos para ver temas especializados en redes de Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="17d8d-139">See these articles for specialized topics in Microsoft 365 networking:</span></span>

- [<span data-ttu-id="17d8d-140">Redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="17d8d-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="17d8d-141">Compatibilidad con IPv6 en servicios de Office 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="17d8d-142">Compatibilidad de NAT con Office 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-microsoft-365"></a><span data-ttu-id="17d8d-143">ExpressRoute para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-143">ExpressRoute for Microsoft 365</span></span>

<span data-ttu-id="17d8d-144">Vea estos artículos para obtener información sobre el uso de ExpressRoute para el tráfico de Office 365:</span><span class="sxs-lookup"><span data-stu-id="17d8d-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="17d8d-145">Azure ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="17d8d-146">Implementación de ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="17d8d-147">Planeamiento de red con ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="17d8d-148">Enrutamiento con ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="17d8d-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
