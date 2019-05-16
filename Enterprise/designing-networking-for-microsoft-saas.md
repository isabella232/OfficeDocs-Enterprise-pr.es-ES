---
title: Diseño de redes para SaaS de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Resumen: Aprenda a optimizar la red para tener acceso a los servicios de SaaS de Microsoft, como Office 365, Microsoft Intune y Dynamics 365.'
ms.openlocfilehash: 695e3255bf1afcb5314985caccb15ead410d93f6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067776"
---
# <a name="designing-networking-for-microsoft-saas"></a><span data-ttu-id="12973-103">Diseño de redes para SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="12973-103">Designing networking for Microsoft SaaS</span></span>

 <span data-ttu-id="12973-104">**Resumen:** Aprenda a optimizar la red para tener acceso a los servicios de SaaS de Microsoft, como Office 365, Microsoft Intune y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="12973-104">**Summary:** Understand how to optimize your network for access to Microsoft's SaaS services, including Office 365, Microsoft Intune, and Dynamics 365.</span></span>
  
<span data-ttu-id="12973-105">La optimización de la red para los servicios SaaS de Microsoft requiere la configuración de dispositivos perimetrales e internos para dirigir las diferentes categorías de tráfico a los servicios SaaS de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="12973-105">Optimizing your network for Microsoft SaaS services requires the configuration of internal and edge devices to route the different categories of traffic to Microsoft SaaS services.</span></span>
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a><span data-ttu-id="12973-106">Pasos para preparar la red para los servicios SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="12973-106">Steps to prepare your network for Microsoft SaaS services</span></span>

<span data-ttu-id="12973-107">Siga estos pasos para optimizar la red para los servicios SaaS de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="12973-107">Follow these steps to optimize your network for Microsoft SaaS services:</span></span>
  
1. <span data-ttu-id="12973-108">Vea la sección **Pasos para preparar la red para Servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="12973-108">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="12973-109">Agregue una conexión a Internet a cada una de las oficinas.</span><span class="sxs-lookup"><span data-stu-id="12973-109">Add an Internet connection to each of your offices.</span></span>
    
3. <span data-ttu-id="12973-110">Asegúrese de que los ISP de todas las conexiones a Internet usen un servidor DNS con una dirección IP local.</span><span class="sxs-lookup"><span data-stu-id="12973-110">Ensure that the ISPs for all Internet connections use a DNS server with a local IP address.</span></span>
    
4. <span data-ttu-id="12973-111">Examine el las redirecciones de red, los destinos intermedios como los servicios de seguridad basados en la nube y elimínelos si es posible.</span><span class="sxs-lookup"><span data-stu-id="12973-111">Examine your network hairpins, intermediate destinations such as cloud-based security services, and eliminate them if possible.</span></span>
    
5. <span data-ttu-id="12973-112">Configure los dispositivos perimetrales para omitir el procesamiento de las categorías optimizar y permitir del tráfico SaaS de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="12973-112">Configure your edge devices to bypass processing for the Optimize and Allow categories of Microsoft SaaS traffic.</span></span>

## <a name="optimizing-traffic-to-microsofts-saas-services"></a><span data-ttu-id="12973-113">Optimización del tráfico a los servicios SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="12973-113">Optimizing traffic to Microsoft’s SaaS services</span></span>    

<span data-ttu-id="12973-114">Hay tres categorías de tráfico SaaS de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="12973-114">There are three categories of Microsoft SaaS traffic:</span></span>

- <span data-ttu-id="12973-115">Optimizar</span><span class="sxs-lookup"><span data-stu-id="12973-115">Optimize</span></span>

  <span data-ttu-id="12973-116">Necesario para la conectividad con todos los servicios SaaS de Microsoft y representan el 75% del ancho de banda, las conexiones y el volumen de datos de SaaS de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="12973-116">Required for connectivity to every Microsoft SaaS service and represent over 75% of Microsoft SaaS bandwidth, connections, and volume of data.</span></span>

- <span data-ttu-id="12973-117">Permitir</span><span class="sxs-lookup"><span data-stu-id="12973-117">Allow</span></span>

  <span data-ttu-id="12973-118">Necesario para la conectividad a características y servicios específicos de SaaS de Microsoft, pero no tan sensibles al rendimiento y la latencia de la red como los de la categoría optimizar.</span><span class="sxs-lookup"><span data-stu-id="12973-118">Required for connectivity to specific Microsoft SaaS services and features but are not as sensitive to network performance and latency as those in the Optimize category.</span></span>

- <span data-ttu-id="12973-119">Valor predeterminado</span><span class="sxs-lookup"><span data-stu-id="12973-119">Default</span></span>

  <span data-ttu-id="12973-120">Representa los servicios SaaS de Microsoft y las dependencias que no requieren optimización.</span><span class="sxs-lookup"><span data-stu-id="12973-120">Represent Microsoft SaaS services and dependencies that do not require any optimization.</span></span> <span data-ttu-id="12973-121">Puede tratar el tráfico de categorías predeterminado, por ejemplo, el tráfico normal de Internet.</span><span class="sxs-lookup"><span data-stu-id="12973-121">You can treat Default category traffic like normal Internet traffic.</span></span>


<span data-ttu-id="12973-122">**Figura 1: configuración recomendada para el tráfico SaaS de Microsoft para todas las oficinas**</span><span class="sxs-lookup"><span data-stu-id="12973-122">**Figure 1: Recommended configuration for Microsoft SaaS traffic for all offices**</span></span>

![Figura 1: configuración recomendada para el tráfico SaaS de Microsoft para todas las oficinas](media/Network-Poster/SaaS1.png)

<span data-ttu-id="12973-124">En la figura 1 se muestra la configuración recomendada de todas las oficinas, incluidas las sucursales y las regionales o las centrales, en las que:</span><span class="sxs-lookup"><span data-stu-id="12973-124">Figure 1 shows the recommended configuration of all offices, including branch offices and regional or central ones, in which:</span></span>

- <span data-ttu-id="12973-125">La categoría **predeterminada** y el tráfico general de Internet se enrutan a las oficinas que tienen servidores proxy y otros dispositivos perimetrales para proporcionar protección frente a los riesgos de seguridad basados en Internet.</span><span class="sxs-lookup"><span data-stu-id="12973-125">**Default** category and general Internet traffic is routed to offices that have proxy servers and other edge devices to provide protection against Internet-based security risks.</span></span>
- <span data-ttu-id="12973-126">**Optimizar** y **permitir** el tráfico de categorías se reenvía directamente al perímetro del front-end de la red de Microsoft más cercano a la oficina que contiene el usuario que realiza la conexión, omitiendo los servidores proxy y otros dispositivos perimetrales.</span><span class="sxs-lookup"><span data-stu-id="12973-126">**Optimize** and **Allow** category traffic is forwarded directly to the edge of the Microsoft network front end nearest to the office containing the connecting user, bypassing proxy servers and other edge devices.</span></span>

<span data-ttu-id="12973-127">Los dispositivos de red de área extensa (SD-WAN) definidos por software en las sucursales separan el tráfico para que:</span><span class="sxs-lookup"><span data-stu-id="12973-127">Software-defined wide area network (SD-WAN) devices in branch offices separate traffic so that:</span></span> 

- <span data-ttu-id="12973-128">La categoría **predeterminada** y el tráfico general de Internet van a una oficina central o regional a través de la red troncal WAN.</span><span class="sxs-lookup"><span data-stu-id="12973-128">**Default** category and general Internet traffic goes to a central or regional office over the WAN backbone.</span></span> 
- <span data-ttu-id="12973-129">**Optimizar** y **permitir** el tráfico de categoría va al ISP que proporciona la conexión local a Internet.</span><span class="sxs-lookup"><span data-stu-id="12973-129">**Optimize** and **Allow** category traffic goes to the ISP providing the local Internet connection.</span></span>
  
<span data-ttu-id="12973-130">Para obtener más información, vea:</span><span class="sxs-lookup"><span data-stu-id="12973-130">For more information, see:</span></span>
  
- [<span data-ttu-id="12973-131">Principios de conectividad de red</span><span class="sxs-lookup"><span data-stu-id="12973-131">Network connectivity principles</span></span>](https://aka.ms/expressrouteoffice365)

- [<span data-ttu-id="12973-132">Planeación de la migración y red para Office 365</span><span class="sxs-lookup"><span data-stu-id="12973-132">Network and migration planning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="next-step"></a><span data-ttu-id="12973-133">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="12973-133">Next step</span></span>

[<span data-ttu-id="12973-134">Diseño de redes para PaaS de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="12973-134">Designing networking for Microsoft Azure PaaS</span></span>](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a><span data-ttu-id="12973-135">Ver también</span><span class="sxs-lookup"><span data-stu-id="12973-135">See also</span></span>

[<span data-ttu-id="12973-136">Microsoft Cloud Networking para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="12973-136">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="12973-137">Recursos de arquitectura de TI de Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="12973-137">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

