---
title: Configurar la red de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Resumen: Vea estos artículos para comprender las redes de Office 365.'
ms.openlocfilehash: 725c2470644206045a40816fad3643b83d6c8ea6
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "38747419"
---
# <a name="set-up-your-network-for-office-365"></a><span data-ttu-id="73607-103">Configurar la red de Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-103">Set up your network for Office 365</span></span>

<span data-ttu-id="73607-104">*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="73607-104">*This applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="73607-p101">Una parte importante de la integración de Office 365 es asegurarse de que la red y las conexiones a Internet están configuradas para el acceso optimizado. Configurar la red local para obtener acceso a una nube distribuida globalmente de software como servicio (SaaS) es diferente de una red tradicional que está optimizada para el tráfico a los centros de datos locales.</span><span class="sxs-lookup"><span data-stu-id="73607-p101">An important part of your Office 365 onboarding is to first ensure that your network and Internet connections are set up for optimized access. Configuring your on-premises network to access a globally distributed Software-as-a-Service (SaaS) cloud is different from a traditional network that is optimized for traffic to on-premises datacenters.</span></span> 

<span data-ttu-id="73607-107">Use estos artículos para comprender las principales diferencias, así como para modificar los dispositivos perimetrales, los equipos cliente y la red local a fin de obtener el mejor rendimiento para sus usuarios locales.</span><span class="sxs-lookup"><span data-stu-id="73607-107">Use these articles to understand the key differences and to modify your  edge devices, client computers, and on-premises network to get the best user performance.</span></span>

## <a name="how-office-365-networking-works"></a><span data-ttu-id="73607-108">Funcionamiento de las redes de Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-108">How Office 365 networking works</span></span>

<span data-ttu-id="73607-109">Vea estos artículos para obtener información general sobre la conectividad de Office 365:</span><span class="sxs-lookup"><span data-stu-id="73607-109">See these articles for an overview of connectivity for Office 365:</span></span>

- [<span data-ttu-id="73607-110">Información general de conectividad de red de Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-110">Office 365 networking connectivity overview</span></span>](office-365-networking-overview.md)
- [<span data-ttu-id="73607-111">Principios de conectividad de red de Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-111">Office 365 network connectivity principles</span></span>](office-365-network-connectivity-principles.md)
- [<span data-ttu-id="73607-112">Evaluar la conexión de red de Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-112">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)

<span data-ttu-id="73607-113">Para obtener información sobre cómo mejorar el rendimiento, vea [Planear la red y ajustar el rendimiento de Office 365](network-planning-and-performance.md).</span><span class="sxs-lookup"><span data-stu-id="73607-113">For advice on enhancing performance, see [Network planning and performance tuning for Office 365](network-planning-and-performance.md).</span></span>

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a><span data-ttu-id="73607-114">Admitir las redes de Office 365 como un proveedor de equipos de red</span><span class="sxs-lookup"><span data-stu-id="73607-114">Support Office 365 networking as a network equipment vendor</span></span>

<span data-ttu-id="73607-p102">Si es un proveedor de equipos de red, únase al [Programa para partners de redes de Office 365](office-365-networking-partner-program.md). Inscríbase en el programa para compilar principios de conectividad de red de Office 365 en sus productos y soluciones.</span><span class="sxs-lookup"><span data-stu-id="73607-p102">If you are a network equipment vendor, join the [Office 365 Networking Partner Program](office-365-networking-partner-program.md). Enroll in the program to build Office 365 network connectivity principles into your products and solutions.</span></span> 

## <a name="office-365-endpoints"></a><span data-ttu-id="73607-117">Puntos de conexión de Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-117">Office 365 endpoints</span></span>

<span data-ttu-id="73607-118">Los puntos de conexión son el conjunto de direcciones IP de destino, nombres de dominio DNS y URL para el tráfico de Office 365 en Internet.</span><span class="sxs-lookup"><span data-stu-id="73607-118">Endpoints are the set of destination IP addresses, DNS domain names, and URLs for Office 365 traffic on the Internet.</span></span> 

<span data-ttu-id="73607-p103">Para optimizar el rendimiento de los servicios basados en la nube de Office 365, algunos puntos de conexión necesitan un tratamiento especial por parte de los exploradores cliente y los dispositivos de la red perimetral. Estos dispositivos incluyen firewalls, inspección e interrupción SSL, dispositivos de inspección de paquetes y sistemas de prevención de pérdida de datos.</span><span class="sxs-lookup"><span data-stu-id="73607-p103">To optimize performance to Office 365 cloud-based services, these endpoints need special handling by your client browsers and the devices in your edge network. These devices include firewalls, SSL Break and Inspect and packet inspection devices, and data loss prevention systems.</span></span>

<span data-ttu-id="73607-121">Vea [Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md) para obtener detalles.</span><span class="sxs-lookup"><span data-stu-id="73607-121">See [Managing Office 365 endpoints](managing-office-365-endpoints.md) for the details.</span></span>

<span data-ttu-id="73607-p104">Actualmente, hay cinco nubes diferentes de Office 365. En esta tabla se le indicará la lista de puntos de conexión de cada una.</span><span class="sxs-lookup"><span data-stu-id="73607-p104">There are currently five different Office 365 clouds. This table takes you to the list of endpoints for each one.</span></span>

|||
|:-------|:-----|
| [<span data-ttu-id="73607-124">Puntos de conexión mundiales</span><span class="sxs-lookup"><span data-stu-id="73607-124">Worldwide endpoints</span></span>](urls-and-ip-address-ranges.md) | <span data-ttu-id="73607-125">Puntos de conexión para suscripciones a Office 365 de todo el mundo, que incluyen Government Community Cloud (GCC) de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="73607-125">The endpoints for worldwide Office 365 subscriptions, which include the United States Government Community Cloud (GCC).</span></span> |
| [<span data-ttu-id="73607-126">Puntos de conexión de DoD de Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="73607-126">U.S. Government DoD endpoints</span></span>](office-365-u-s-government-dod-endpoints.md) | <span data-ttu-id="73607-127">Puntos de conexión para las suscripciones del Department of Defense (DoD) de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="73607-127">The endpoints for United States Department of Defense (DoD) subscriptions.</span></span> |
| [<span data-ttu-id="73607-128">Puntos de conexión de GCC High de Estados Unidos</span><span class="sxs-lookup"><span data-stu-id="73607-128">U.S. Government GCC High endpoints</span></span>](office-365-u-s-government-gcc-high-endpoints.md) | <span data-ttu-id="73607-129">Puntos de conexión para suscripciones a Government Community Cloud High (GCC High) de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="73607-129">The endpoints for United States Government Community Cloud High (GCC High) subscriptions.</span></span> |
| [<span data-ttu-id="73607-130">Puntos de conexión de Office 365 operado por 21Vianet</span><span class="sxs-lookup"><span data-stu-id="73607-130">Office 365 operated by 21Vianet endpoints</span></span>](urls-and-ip-address-ranges-21vianet.md) | <span data-ttu-id="73607-131">Puntos de conexión de Office 365 operado por 21Vianet, que está diseñado para satisfacer las necesidades de Office 365 en China.</span><span class="sxs-lookup"><span data-stu-id="73607-131">The endpoints for Office 365 operated by 21Vianet, which is designed to meet the needs for Office 365 in China.</span></span> |
| [<span data-ttu-id="73607-132">Puntos de conexión de Office 365 Germany</span><span class="sxs-lookup"><span data-stu-id="73607-132">Office 365 Germany endpoints</span></span>](office-365-germany-endpoints.md) | <span data-ttu-id="73607-133">Puntos de conexión de una nube independiente en Europa para los clientes con más regulaciones en Alemania, la Unión Europea (UE) y la Asociación Europea de Libre Comercio (AELC).</span><span class="sxs-lookup"><span data-stu-id="73607-133">The endpoints for a separate cloud in Europe for the most regulated customers in Germany, the European Union (EU), and the European Free Trade Association (EFTA).</span></span> |
|||

<span data-ttu-id="73607-134">Para automatizar la obtención de la lista más reciente de puntos de conexión para su nube de Office 365, vea [Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="73607-134">To automate getting the latest list of endpoints for your Office 365 cloud, see the [Office 365 IP Address and URL Web service](office-365-ip-web-service.md).</span></span>

<span data-ttu-id="73607-135">Para consultar puntos de conexión adicionales, vea estos artículos:</span><span class="sxs-lookup"><span data-stu-id="73607-135">For additional endpoints, see these articles:</span></span>

- [<span data-ttu-id="73607-136">Puntos de conexión adicionales no incluidos en el servicio web</span><span class="sxs-lookup"><span data-stu-id="73607-136">Additional endpoints not included in the Web service</span></span>](additional-office365-ip-addresses-and-urls.md)
- [<span data-ttu-id="73607-137">Solicitudes de red en Office 2016 para Mac</span><span class="sxs-lookup"><span data-stu-id="73607-137">Network requests in Office 2016 for Mac</span></span>](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a><span data-ttu-id="73607-138">Otros temas sobre las redes de Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-138">Additional topics for Office 365 networking</span></span>

<span data-ttu-id="73607-139">Vea estos artículos para consultar temas especializados sobre las redes de Office 365:</span><span class="sxs-lookup"><span data-stu-id="73607-139">See these articles for specialized topics in Office 365 networking:</span></span>

- [<span data-ttu-id="73607-140">Redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="73607-140">Content delivery networks</span></span>](content-delivery-networks.md)
- [<span data-ttu-id="73607-141">Compatibilidad con IPv6 en servicios de Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-141">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
- [<span data-ttu-id="73607-142">Compatibilidad de NAT con Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-142">NAT support with Office 365</span></span>](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a><span data-ttu-id="73607-143">ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-143">ExpressRoute for Office 365</span></span>

<span data-ttu-id="73607-144">Vea estos artículos para obtener información sobre el uso de ExpressRoute para el tráfico de Office 365:</span><span class="sxs-lookup"><span data-stu-id="73607-144">See these articles for information on the use of ExpressRoute for Office 365 traffic:</span></span>

- [<span data-ttu-id="73607-145">Azure ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-145">Azure ExpressRoute for Office 365</span></span>](azure-expressroute.md)
- [<span data-ttu-id="73607-146">Implementación de ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-146">Implementing ExpressRoute for Office 365</span></span>](implementing-expressroute.md)
- [<span data-ttu-id="73607-147">Planeamiento de red con ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-147">Network planning with ExpressRoute for Office 365</span></span>](network-planning-with-expressroute.md)
- [<span data-ttu-id="73607-148">Enrutamiento con ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="73607-148">Routing with ExpressRoute for Office 365</span></span>](routing-with-expressroute.md)
