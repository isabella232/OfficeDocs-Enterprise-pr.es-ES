---
title: Diseño de redes para SaaS de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Resumen: Aprenda a optimizar la red para tener acceso a los servicios de SaaS de Microsoft, como Office 365, Microsoft Intune y Dynamics 365.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872271"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="ff5a8-103">Diseño de redes para SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ff5a8-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="ff5a8-104">**Resumen:** Aprenda a optimizar la red para tener acceso a los servicios de SaaS de Microsoft, como Office 365, Microsoft Intune y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="ff5a8-105">Optimización de la red para los servicios de Microsoft SaaS requiere la configuración de interno y dispositivos de extremo para enrutar las diferentes categorías de tráfico a los servicios de Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="ff5a8-106">Pasos para preparar la red para los servicios SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ff5a8-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="ff5a8-107">Siga estos pasos para optimizar la red para los servicios SaaS de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="ff5a8-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="ff5a8-108">Vea la sección **Pasos para preparar la red para Servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="ff5a8-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="ff5a8-109">Agregar una conexión a Internet a cada uno de sus oficinas.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="ff5a8-110">Asegúrese de que el ISP para todas las conexiones de Internet utilicen un servidor DNS con una dirección IP local.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="ff5a8-111">Examine su hairpins de red, los destinos intermedios, como los servicios de seguridad basados en la nube y eliminarlos si es posible.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="ff5a8-112">Configurar los dispositivos de borde para el desvío de procesamiento para optimizar y permitir que las categorías de tráfico de Microsoft SaaS.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="ff5a8-113">Optimizar el tráfico de los servicios de Microsoft SaaS</span><span class="sxs-lookup"><span data-stu-id="ff5a8-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="ff5a8-114">Existen tres categorías de Microsoft SaaS tráfico:</span><span class="sxs-lookup"><span data-stu-id="ff5a8-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="ff5a8-115">Optimizar</span><span class="sxs-lookup"><span data-stu-id="ff5a8-115">Optimize</span></span>

  <span data-ttu-id="ff5a8-116">Necesario para la conectividad con cada servicio de Microsoft SaaS y representan más del 75% del ancho de banda de Microsoft SaaS, conexiones y volumen de datos.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="ff5a8-117">Permitir</span><span class="sxs-lookup"><span data-stu-id="ff5a8-117">Allow</span></span>

  <span data-ttu-id="ff5a8-118">Necesarios para la conectividad con específicos Microsoft SaaS de servicios y sobre las características de pero no son tan confidenciales a rendimiento de la red y la latencia como los de la categoría de optimizar.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="ff5a8-119">Predeterminada</span><span class="sxs-lookup"><span data-stu-id="ff5a8-119">Default</span></span>

  <span data-ttu-id="ff5a8-p101">Representan los servicios de Microsoft SaaS y dependencias que no requieren ninguna optimización. Puede tratar el tráfico de categoría predeterminada al igual que el tráfico normal de Internet.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-p101">Represent Microsoft SaaS services and dependencies that do not require any optimization. You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="ff5a8-122">**En la figura 1: Configuración recomendada para el tráfico de Microsoft SaaS para todas las oficinas**</span><span class="sxs-lookup"><span data-stu-id="ff5a8-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![En la figura 1: Configuración recomendada para el tráfico de Microsoft SaaS para todas las oficinas](media/Network-Poster/SaaS1.png)

<span data-ttu-id="ff5a8-124">La figura 1 muestra la configuración recomendada de todas las oficinas, incluidas las sucursales y unos regionales o centrales, en la que:</span><span class="sxs-lookup"><span data-stu-id="ff5a8-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="ff5a8-125">Categoría **predeterminada** y general se enruta el tráfico de Internet para las oficinas que tienen servidores proxy y otros dispositivos de borde para proporcionar protección frente a los riesgos de seguridad basados en Internet.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="ff5a8-126">**Optimizar** y **Permitir** el tráfico de categoría se reenvía directamente hasta el borde de front-end de red de Microsoft de más cercana a la oficina que contiene el usuario que se conecta, pasando por alto los servidores proxy y otros dispositivos de extremo.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="ff5a8-127">Dispositivos de definidas por el software de área extensa (WAN SD) de red en las sucursales separan el tráfico de modo que:</span><span class="sxs-lookup"><span data-stu-id="ff5a8-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="ff5a8-128">Categoría **predeterminada** y general el tráfico de Internet va a una oficina central o regional a través de la red troncal de WAN.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="ff5a8-129">**Optimizar** y **Permitir** el tráfico de categoría que se va al ISP que proporciona la conexión a Internet local.</span><span class="sxs-lookup"><span data-stu-id="ff5a8-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="ff5a8-130">Para obtener más información, vea:</span><span class="sxs-lookup"><span data-stu-id="ff5a8-130">For more information, see:</span></span>
  
- [<span data-ttu-id="ff5a8-131">Principios de conectividad de red</span><span class="sxs-lookup"><span data-stu-id="ff5a8-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="ff5a8-132">Planeación de la migración y red para Office 365</span><span class="sxs-lookup"><span data-stu-id="ff5a8-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="ff5a8-133">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="ff5a8-133">Next step</span></span>

[<span data-ttu-id="ff5a8-134">Diseño de redes para PaaS de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="ff5a8-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="ff5a8-135">Ver también</span><span class="sxs-lookup"><span data-stu-id="ff5a8-135">See also</span></span>

[<span data-ttu-id="ff5a8-136">Microsoft Cloud Networking para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="ff5a8-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="ff5a8-137">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ff5a8-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

