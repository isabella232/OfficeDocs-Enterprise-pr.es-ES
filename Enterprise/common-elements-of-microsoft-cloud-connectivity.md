---
title: Elementos comunes de la conectividad de la nube de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 061d4507-7360-4029-8f4b-3d4bc6b4ade0
description: 'Resumen: Descubra los elementos comunes de la infraestructura de red y aprenda a preparar la red.'
ms.openlocfilehash: 27a83217e94d6a0f882825c57346b58ea1834443
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="common-elements-of-microsoft-cloud-connectivity"></a><span data-ttu-id="02ad4-103">Elementos comunes de la conectividad de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="02ad4-103">Common elements of Microsoft cloud connectivity</span></span>

 <span data-ttu-id="02ad4-104">**Resumen:** Descubra los elementos comunes de la infraestructura de red y aprenda a preparar la red.</span><span class="sxs-lookup"><span data-stu-id="02ad4-104">**Summary:** Understand the common elements of networking infrastructure and how to prepare your network.</span></span>
  
<span data-ttu-id="02ad4-105">La integración de las redes en la nube de Microsoft proporciona un acceso óptimo a una amplia gama de servicios.</span><span class="sxs-lookup"><span data-stu-id="02ad4-105">Integrating your networking with the Microsoft cloud provides optimal access to a broad range of services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-cloud-services"></a><span data-ttu-id="02ad4-106">Pasos para preparar la red para los servicios en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="02ad4-106">Steps to prepare your network for Microsoft cloud services</span></span>
<span data-ttu-id="02ad4-107"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="02ad4-107"><a name="steps"> </a></span></span>

<span data-ttu-id="02ad4-108">En la red local:</span><span class="sxs-lookup"><span data-stu-id="02ad4-108">For your on-premises network:</span></span>
  
1. <span data-ttu-id="02ad4-109">Analizar los equipos cliente y optimizar el hardware de red, los controladores de software, la configuración de protocolo y los exploradores de Internet.</span><span class="sxs-lookup"><span data-stu-id="02ad4-109">Analyze your client computers and optimize for network hardware, software drivers, protocol settings, and Internet browsers.</span></span>
    
2. <span data-ttu-id="02ad4-110">Analizar la red local para determinar la latencia del tráfico y el enrutamiento óptimo del dispositivo perimetral de Internet.</span><span class="sxs-lookup"><span data-stu-id="02ad4-110">Analyze your on-premises network for traffic latency and optimal routing to the Internet edge device.</span></span>
    
3. <span data-ttu-id="02ad4-111">Analizar la capacidad y el rendimiento del dispositivo perimetral de Internet y optimizar para lograr los niveles más altos de tráfico.</span><span class="sxs-lookup"><span data-stu-id="02ad4-111">Analyze the capacity and performance of your Internet edge device and optimize for higher levels of traffic.</span></span>
    
<span data-ttu-id="02ad4-112">Para la conexión a Internet:</span><span class="sxs-lookup"><span data-stu-id="02ad4-112">For your Internet connection:</span></span>
  
1. <span data-ttu-id="02ad4-113">Analizar la latencia entre el dispositivo perimetral de Internet (como el firewall externo) y las ubicaciones regionales del servicio en la nube de Microsoft al que se conecta.</span><span class="sxs-lookup"><span data-stu-id="02ad4-113">Analyze the latency between your Internet edge device (such as your external firewall) and the regional locations of the Microsoft cloud service to which you are connecting.</span></span>
    
2. <span data-ttu-id="02ad4-p101">Analizar la capacidad y la utilización de la conexión actual a Internet y agregar capacidad si es necesario. Otra opción es agregar una conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="02ad4-p101">Analyze the capacity and utilization of your current Internet connection and add capacity if needed. Alternately, add an ExpressRoute connection.</span></span>
    
## <a name="microsoft-cloud-connectivity-options"></a><span data-ttu-id="02ad4-116">Opciones de conectividad en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="02ad4-116">Microsoft cloud connectivity options</span></span>
<span data-ttu-id="02ad4-117"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="02ad4-117"><a name="steps"> </a></span></span>

<span data-ttu-id="02ad4-118">Use la canalización de Internet existente o una conexión de ExpressRoute para Office 365, Azure y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="02ad4-118">Use your existing Internet pipe or an ExpressRoute connection to Office 365, Azure, and Dynamics 365.</span></span>
  
<span data-ttu-id="02ad4-119">**Figura 1: Opciones para la conectividad en la nube de Microsoft**</span><span class="sxs-lookup"><span data-stu-id="02ad4-119">**Figure 1: Options for Microsoft cloud connectivity**</span></span>

![Figura 1:  Opciones para la conectividad en la nube de Microsoft](images/Network_Poster/CommonElements.png)

  
<span data-ttu-id="02ad4-p102">La figura 1 muestra cómo se puede conectar una red local con las ofertas en la nube de Microsoft usando la canalización de Internet existente o ExpressRoute. La canalización de Internet representa una red perimetral y puede tener los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="02ad4-p102">Figure 1 shows how an on-premises network can be connected to Microsoft cloud offerings using their existing Internet pipe or ExpressRoute. The Internet pipe represents a DMZ and can have the following components:</span></span>
  
- <span data-ttu-id="02ad4-p103">**Firewall interno:** una barrera entre su red de confianza y otra que no sea confiable. Lleva a cabo el filtrado del tráfico (basado en reglas) y la supervisión.</span><span class="sxs-lookup"><span data-stu-id="02ad4-p103">**Internal firewall:** A barrier between your trusted network and an untrusted one. Performs traffic filtering (based on rules) and monitoring.</span></span>
    
- <span data-ttu-id="02ad4-125">**Carga de trabajo externa:** sitios web u otras cargas de trabajo a disposición de los usuarios externos de Internet.</span><span class="sxs-lookup"><span data-stu-id="02ad4-125">**External workload:** Web sites or other workloads made available to external users on the Internet.</span></span>
    
- <span data-ttu-id="02ad4-p104">**Servidor proxy:** atiende las solicitudes de contenido web en nombre de los usuarios de la intranet. Un proxy inverso permite las solicitudes entrantes no solicitadas.</span><span class="sxs-lookup"><span data-stu-id="02ad4-p104">**Proxy server:** Services requests for web content on behalf of intranet users. A reverse proxy allows unsolicited inbound requests.</span></span>
    
- <span data-ttu-id="02ad4-p105">**Firewall externo:** permite el tráfico saliente y el tráfico entrante especificado. Puede traducir direcciones.</span><span class="sxs-lookup"><span data-stu-id="02ad4-p105">**External firewall:** Allows outbound traffic and specified inbound traffic. Can perform address translation.</span></span>
    
- <span data-ttu-id="02ad4-130">**Conexión WAN a ISP:** conexión a un ISP (basada en proveedor) que se comunica con Internet para conseguir la conectividad y el enrutamiento.</span><span class="sxs-lookup"><span data-stu-id="02ad4-130">**WAN connection to ISP:** A carrier-based connection to an ISP, who peers with the Internet for connectivity and routing.</span></span>
    
## <a name="areas-of-networking-common-to-all-microsoft-cloud-services"></a><span data-ttu-id="02ad4-131">Áreas de redes comunes a todos los servicios en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="02ad4-131">Areas of networking common to all Microsoft cloud services</span></span>
<span data-ttu-id="02ad4-132"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="02ad4-132"><a name="steps"> </a></span></span>

<span data-ttu-id="02ad4-133">Al adoptar cualquiera de los servicios en la nube de Microsoft, debe tener en cuenta estas áreas de redes.</span><span class="sxs-lookup"><span data-stu-id="02ad4-133">You need to consider these areas of networking when adopting any of Microsoft's cloud services.</span></span>
  
- <span data-ttu-id="02ad4-134">**Rendimiento de la intranet:** el rendimiento de los recursos de Internet se verá mermado si la intranet, incluidos los equipos cliente, no se optimiza.</span><span class="sxs-lookup"><span data-stu-id="02ad4-134">**Intranet performance:** Performance to Internet-based resources will suffer if your intranet, including client computers, is not optimized.</span></span>
    
- <span data-ttu-id="02ad4-135">**Dispositivos perimetrales:** dispositivos situados en el perímetro de la red son puntos de salida y pueden incluir traductores de direcciones de red (NAT), servidores proxy (incluidos los inversos), firewalls, dispositivos de detección de intrusiones o una combinación.</span><span class="sxs-lookup"><span data-stu-id="02ad4-135">**Edge devices:** Devices at the edge of your network are egress points and can include Network Address Translators (NATs), proxy servers (including reverse proxies), firewalls, intrusion detection devices, or a combination.</span></span>
    
- <span data-ttu-id="02ad4-p106">**Conexión a Internet:** la conexión WAN a Internet y al ISP debe tener suficiente capacidad para albergar las cargas máximas. También puede usar una conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="02ad4-p106">**Internet connection:** Your WAN connection to your ISP and the Internet should have enough capacity to handle peak loads. You can also use an ExpressRoute connection.</span></span>
    
- <span data-ttu-id="02ad4-p107">**DNS de Internet:** A, AAAA, CNAME, MX, PTR y otros registros para buscar la nube de Microsoft o los servicios hospedados en la nube. Por ejemplo, puede que necesite un registro CNAME para la aplicación hospedada en PaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="02ad4-p107">**Internet DNS:** A, AAAA, CNAME, MX, PTR and other records to locate Microsoft cloud or your services hosted in the cloud. For example, you might need a CNAME record for your app hosted in Azure PaaS.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="02ad4-140">See Also</span><span class="sxs-lookup"><span data-stu-id="02ad4-140">See Also</span></span>

<span data-ttu-id="02ad4-141"><a name="steps"> </a></span><span class="sxs-lookup"><span data-stu-id="02ad4-141"><a name="steps"> </a></span></span>

[<span data-ttu-id="02ad4-142">Microsoft Cloud Networking para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="02ad4-142">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="02ad4-143">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="02ad4-143">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="02ad4-144">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="02ad4-144">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)

