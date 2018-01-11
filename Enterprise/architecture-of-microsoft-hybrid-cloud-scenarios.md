---
title: "Arquitectura de escenarios de nube híbrida de Microsoft"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: "Resumen: Comprenda la arquitectura de las ofertas de nube híbrida de Microsoft."
ms.openlocfilehash: 6c61d7467177b0dbf70e5540e32b059b348a062c
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a><span data-ttu-id="a5dbe-103">Arquitectura de escenarios de nube híbrida de Microsoft</span><span class="sxs-lookup"><span data-stu-id="a5dbe-103">Architecture of Microsoft hybrid cloud scenarios</span></span>

 <span data-ttu-id="a5dbe-104">**Resumen:** Comprenda la arquitectura de las ofertas de nube híbrida de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-104">**Summary:** Understand the architecture of Microsoft's hybrid cloud offerings.</span></span>
  
<span data-ttu-id="a5dbe-105">Use un enfoque de arquitectura para planear e implementar escenarios de nube híbrida con plataformas y servicios en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-105">Use an architectural approach to plan and implement hybrid cloud scenarios with Microsoft cloud services and platforms.</span></span>
  
<span data-ttu-id="a5dbe-106">**Figura 1: La pila de nube híbrida de Microsoft**</span><span class="sxs-lookup"><span data-stu-id="a5dbe-106">**Figure 1: The Microsoft hybrid cloud stack**</span></span>

![La pila de nube híbrida de Microsoft](images/Hybrid_Poster/Hybrid_Cloud_Stack.png)
  
<span data-ttu-id="a5dbe-108">En la figura 1, se muestra la pila de nube híbrida de Microsoft y su capa, que puede ser Local, Red, Identidad, aplicaciones y escenarios, y la categoría de servicio en la nube (SaaS de Microsoft y PaaS de Azure).</span><span class="sxs-lookup"><span data-stu-id="a5dbe-108">Figure 1 shows the Microsoft hybrid cloud stack and its layer, which include on-premises, network, Identity, apps and scenarios, and the category of cloud service (Microsoft SaaS, Azure PaaS, and Azure PaaS).</span></span>
  
<span data-ttu-id="a5dbe-p101">La capa de aplicaciones y escenarios contiene los escenarios de nube híbrida específicos que se detallan en los artículos adicionales de este modelo. Las capas Identidad, Red y Local pueden ser comunes a las categorías de servicio en la nube (SaaS o PaaS).</span><span class="sxs-lookup"><span data-stu-id="a5dbe-p101">The Apps and scenarios layer contains the specific hybrid cloud scenarios that are detailed in the additional articles of this model. The Identity, Network, and On-premises layers can be common to the categories of cloud service (SaaS, PaaS, or PaaS).</span></span>
  
- <span data-ttu-id="a5dbe-111">Local</span><span class="sxs-lookup"><span data-stu-id="a5dbe-111">On-premises</span></span>
    
    <span data-ttu-id="a5dbe-p102">La infraestructura local para escenarios híbridos puede incluir servidores de SharePoint, Exchange, Skype Empresarial y aplicaciones de línea de negocio. También puede incluir almacenes de datos (bases de datos, listas, archivos). Sin conexiones de ExpressRoute, se debe permitir el acceso a los almacenes de datos locales a través de un proxy inverso o al hacer que el servidor o los datos sean accesibles en su red perimetral o extranet.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-p102">On-premises infrastructure for hybrid scenarios can include servers for SharePoint, Exchange, Skype for Business, and line of business applications. It can also include data stores (databases, lists, files). Without ExpressRoute connections, access to the on-premises data stores must be allowed through a reverse proxy or by making the server or data accessible on your DMZ or extranet.</span></span>
    
- <span data-ttu-id="a5dbe-115">Red</span><span class="sxs-lookup"><span data-stu-id="a5dbe-115">Network</span></span>
    
    <span data-ttu-id="a5dbe-p103">Hay dos opciones de conectividad con plataformas y servicios de nube de Microsoft: la canalización de Internet existente y ExpressRoute. Use una conexión de ExpressRoute si es importante el rendimiento predecible. Puede usar una conexión de ExpressRoute para conectarse directamente con los servicios de SaaS de Microsoft (Office 365 y Dynamics 365) y los servicios de PaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-p103">There are two choices for connectivity to Microsoft cloud platforms and services: your existing Internet pipe and ExpressRoute. Use an ExpressRoute connection if predictable performance is important. You can use one ExpressRoute connection to connect directly to Microsoft SaaS services (Office 365 and Dynamics 365), Azure PaaS services, and Azure PaaS services.</span></span>
    
- <span data-ttu-id="a5dbe-119">Identidad</span><span class="sxs-lookup"><span data-stu-id="a5dbe-119">Identity</span></span>
    
    <span data-ttu-id="a5dbe-p104">Para la infraestructura de identidad de la nube, hay dos formas de proceder, según la plataforma de nube de Microsoft. Para SaaS y PaaS de Azure, integre la infraestructura de identidad local con Azure AD o fedérese con los proveedores de identidad de terceros o de infraestructura de identidad local. Para máquinas virtuales que se ejecutan en Azure, puede ampliar su infraestructura de identidad local, como Windows Server AD, a las redes virtuales (VNets) en que se encuentran las máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-p104">For cloud identity infrastructure, there are two ways to go, depending on the Microsoft cloud platform. For SaaS and Azure PaaS, integrate your on-premises identity infrastructure with Azure AD or federate with your on-premises identity infrastructure or third-party identity providers. For VMs running in Azure, you can extend your on-premises identity infrastructure, such as Windows Server AD, to the virtual networks (VNets) where your VMs reside.</span></span>
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a><span data-ttu-id="a5dbe-123">Escenarios de nube híbrida para el proceso de adopción de la nube de tres fases</span><span class="sxs-lookup"><span data-stu-id="a5dbe-123">Hybrid cloud scenarios for the three-phase cloud adoption process</span></span>

<span data-ttu-id="a5dbe-p105">Muchas empresas, incluida Microsoft, usan un enfoque de tres fases para la adopción de la nube. Los escenarios de nube híbrida pueden desempeñar un papel en cada fase.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-p105">Many enterprises, including Microsoft's, use a three-phase approach to adopting the cloud. Hybrid cloud scenarios can play a role in each phase.</span></span>
  
1. <span data-ttu-id="a5dbe-126">Mover las cargas de trabajo de productividad a SaaS</span><span class="sxs-lookup"><span data-stu-id="a5dbe-126">Move productivity workloads to SaaS</span></span>
    
    <span data-ttu-id="a5dbe-127">Para las cargas de trabajo de productividad locales o que deben permanecer locales, los escenarios híbridos permiten que se integren con sus equivalentes en la nube.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-127">For productivity workloads that currently are or must stay on-premises, hybrid scenarios allow them to be integrated with their cloud counterparts.</span></span>
    
2. <span data-ttu-id="a5dbe-128">Desarrollar aplicaciones nuevas y modernas en PaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="a5dbe-128">Develop new and modern applications in Azure PaaS</span></span>
    
    <span data-ttu-id="a5dbe-129">Las aplicaciones PaaS híbridas de Azure pueden aprovechar con seguridad los recursos de almacenamiento o del servidor local.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-129">Azure PaaS hybrid applications can securely leverage on-premises server or storage resources.</span></span>
    
3. <span data-ttu-id="a5dbe-130">Mover aplicaciones existentes a IaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="a5dbe-130">Move existing applications to Azure IaaS</span></span>
    
    <span data-ttu-id="a5dbe-131">Para los escenarios de elevar y desplazar y compilar en la nube, las aplicaciones basadas en servidor que se ejecutan en máquinas virtuales de Azure ofrecen aprovisionamiento y escalado sencillos.</span><span class="sxs-lookup"><span data-stu-id="a5dbe-131">For lift-and-shift and build-in-the-cloud scenarios, server-based applications running on Azure VMs provide easy provisioning and scaling.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="a5dbe-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="a5dbe-132">See Also</span></span>

[<span data-ttu-id="a5dbe-133">Microsoft Hybrid Cloud para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="a5dbe-133">Microsoft Hybrid Cloud for Enterprise Architects</span></span>](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[<span data-ttu-id="a5dbe-134">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="a5dbe-134">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="a5dbe-135">[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="a5dbe-135">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>



