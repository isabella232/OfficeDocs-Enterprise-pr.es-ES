---
title: Redes para Contoso Corporation
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
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: "Resumen: Comprenda la definición y los elementos de la nube híbrida de Microsoft."
ms.openlocfilehash: 0943864c8a9982eba00a139617ebe17d39cdde4e
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="networking-for-the-contoso-corporation"></a><span data-ttu-id="183ca-103">Redes para Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="183ca-103">Networking for the Contoso Corporation</span></span>

 <span data-ttu-id="183ca-104">**Resumen:** Comprenda la definición y los elementos de la nube híbrida de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="183ca-104">**Summary:** Understand the definition and elements of Microsoft hybrid cloud.</span></span>
  
<span data-ttu-id="183ca-p101">Para adoptar una infraestructura cloud inclusive, ingenieros de red de Contoso se dio cuenta el cambio fundamental en el modo en que el tráfico de red a los recorridos de servicios basados en cloud. En lugar de sólo optimiza el tráfico a servidores locales y los centros de datos, debe prestarse atención igual a optimizar el tráfico en el perímetro de Internet y a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="183ca-p101">To adopt a cloud-inclusive infrastructure, Contoso's network engineers realized the fundamental shift in the way that network traffic to cloud-based services travels. Instead of only optimizing traffic to on-premises servers and datacenters, equal attention must be paid to optimizing traffic to the Internet edge and across the Internet.</span></span>
  
## <a name="contosos-networking-infrastructure"></a><span data-ttu-id="183ca-107">Infraestructura de red de Contoso</span><span class="sxs-lookup"><span data-stu-id="183ca-107">Contoso's networking infrastructure</span></span>

<span data-ttu-id="183ca-108">Contoso tiene la infraestructura de red que se muestra en la figura 1.</span><span class="sxs-lookup"><span data-stu-id="183ca-108">Contoso has the networking infrastructure shown in Figure 1.</span></span>
  
<span data-ttu-id="183ca-109">**Figura 1: Infraestructura WAN de Contoso**</span><span class="sxs-lookup"><span data-stu-id="183ca-109">**Figure 1: Contoso's WAN infrastructure**</span></span>

![Infraestructura WAN de Contoso que vincula la sede central, los centros regionales y las oficinas satélite](images/Contoso_Poster/Contoso_WW_Net.png)
  
<span data-ttu-id="183ca-111">La figura 1 muestra las oficinas de Contoso en todo el mundo y el conjunto de vínculos WAN de oficinas regionales y satélite entre ellos.</span><span class="sxs-lookup"><span data-stu-id="183ca-111">Figure 1 shows the Contoso's offices across the globe and the set of regional and satellite office WAN links between them.</span></span>
  
<span data-ttu-id="183ca-112">Los elementos adicionales de la red son los siguientes:</span><span class="sxs-lookup"><span data-stu-id="183ca-112">Additional elements of their network are the following:</span></span>
  
- <span data-ttu-id="183ca-113">Red local</span><span class="sxs-lookup"><span data-stu-id="183ca-113">On-premises network</span></span>
    
    <span data-ttu-id="183ca-p102">Vínculos WAN conectan la sede de París para oficinas regionales y las oficinas regionales a oficinas satélite en una configuración de concentrador y radios. Dentro de cada oficina, enrutadores entregar tráfico a los hosts o los puntos de acceso inalámbrico en subredes, que utilizan el espacio de direcciones IP privado.</span><span class="sxs-lookup"><span data-stu-id="183ca-p102">WAN links connect the Paris headquarters to regional offices and regional offices to satellite offices in a spoke and hub configuration. Within each office, routers deliver traffic to hosts or wireless access points on subnets, which use the private IP address space.</span></span>
    
- <span data-ttu-id="183ca-116">Conectividad a Internet</span><span class="sxs-lookup"><span data-stu-id="183ca-116">Internet connectivity</span></span>
    
    <span data-ttu-id="183ca-p103">Cada oficina tiene su propia conexión a Internet mediante un servidor proxy. Esto normalmente se implementa como una WAN enlace a un ISP local que también proporciona direcciones IP públicas del servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="183ca-p103">Each office has its own Internet connectivity via a proxy server. This is typically implemented as a WAN link to a local ISP that also provides public IP addresses for the proxy server.</span></span>
    
- <span data-ttu-id="183ca-119">Presencia en Internet</span><span class="sxs-lookup"><span data-stu-id="183ca-119">Internet presence</span></span>
    
    <span data-ttu-id="183ca-p104">Contoso posee el nombre de dominio público de contoso.com. El sitio web público de Contoso para pedir productos es un conjunto de servidores en un centro de datos conectados a Internet en el campus de París. Contoso utiliza un /24 intervalo de direcciones IP pública en Internet.</span><span class="sxs-lookup"><span data-stu-id="183ca-p104">Contoso owns the contoso.com public domain name. The Contoso public web site for ordering products is a set of servers in an Internet-connected datacenter in the Paris campus. Contoso uses a /24 public IP address range on the Internet.</span></span>
    
## <a name="contosos-app-infrastructure"></a><span data-ttu-id="183ca-123">Infraestructura de app de Contoso</span><span class="sxs-lookup"><span data-stu-id="183ca-123">Contoso's app infrastructure</span></span>

<span data-ttu-id="183ca-124">Contoso ha diseñado su infraestructura de servidores y aplicaciones para lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="183ca-124">Contoso has architected its application and server infrastructure for the following:</span></span>
  
<span data-ttu-id="183ca-125">**Figura 2: Infraestructura de Contoso para aplicaciones internas**</span><span class="sxs-lookup"><span data-stu-id="183ca-125">**Figure 2: Contoso's infrastructure for internal applications**</span></span>

![Infraestructura de Contoso para aplicaciones internas](images/Contoso_Poster/App_Infra.png)
  
- <span data-ttu-id="183ca-127">Las oficinas satélite usan servidores de almacenamiento en caché locales para almacenar documentos y sitios web internos a los que se accede frecuentemente.</span><span class="sxs-lookup"><span data-stu-id="183ca-127">Satellite offices use local caching servers to store frequently-accessed documents and internal web sites.</span></span>
    
- <span data-ttu-id="183ca-p105">Concentradores regionales utilizar servidores de aplicación regional para la configuración regional y oficinas satélite. Estos servidores se sincronización con los servidores en las sedes de París.</span><span class="sxs-lookup"><span data-stu-id="183ca-p105">Regional hubs use regional application servers for the regional and satellite offices. These servers synchronize with servers in the Paris headquarters.</span></span>
    
- <span data-ttu-id="183ca-130">Las instalaciones de París tienen los centros de datos que contienen los servidores de aplicaciones centralizados que sirven a toda la organización.</span><span class="sxs-lookup"><span data-stu-id="183ca-130">The Paris campus has the datacenters that contain the centralized application servers that serve the entire organization.</span></span>
    
<span data-ttu-id="183ca-p106">Para los usuarios de oficinas de centros regionales o satélite, el 60 % de los recursos que necesitan los empleados pueden obtenerse de los servidores de oficinas de concentradores regionales o satélite. El 40 % adicional de solicitudes de recursos debe realizarse a través del vínculo WAN a las instalaciones de París.</span><span class="sxs-lookup"><span data-stu-id="183ca-p106">For users in satellite or regional hub offices, 60% of the resources needed by employees can be served by satellite and regional hub office servers. The additional 40% of resource requests must go over the WAN link to the Paris campus.</span></span>
  
## <a name="contosos-network-analysis"></a><span data-ttu-id="183ca-133">Análisis de red de Contoso</span><span class="sxs-lookup"><span data-stu-id="183ca-133">Contoso's network analysis</span></span>

<span data-ttu-id="183ca-134">Éstos son los resultados de los análisis de Contoso de los cambios necesarios en su red para adaptarse a las diferentes categorías de ofertas de nube de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="183ca-134">Here are the results of Contoso's analysis of the changes needed on their network to accommodate the different categories of Microsoft's cloud offerings:</span></span>
  
|<span data-ttu-id="183ca-135">**Las ofertas de nube de SaaS: Office 365, EMS y Dynamics 365**</span><span class="sxs-lookup"><span data-stu-id="183ca-135">**SaaS cloud offerings: Office 365, EMS, and Dynamics 365**</span></span>|<span data-ttu-id="183ca-136">**PaaS Azure: Aplicaciones móviles**</span><span class="sxs-lookup"><span data-stu-id="183ca-136">**Azure PaaS: Mobile applications**</span></span>|<span data-ttu-id="183ca-137">**Azure IaaS: Las cargas de trabajo basado en servidor**</span><span class="sxs-lookup"><span data-stu-id="183ca-137">**Azure IaaS: Server-based workloads**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="183ca-138">Una adopción satisfactoria de servicios SaaS por parte de los usuarios depende de alta disponibilidad y rendimiento conectividad a Internet, o directamente a los servicios de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="183ca-138">Successful adoption of SaaS services by users depends on highly-available and performant connectivity to the Internet, or directly to Microsoft cloud services.</span></span>  <br/> <span data-ttu-id="183ca-139">Para usuarios móviles, se supone que su acceso a la Internet actual sea adecuada.</span><span class="sxs-lookup"><span data-stu-id="183ca-139">For mobile users, their current Internet access is assumed to be adequate.</span></span>  <br/> <span data-ttu-id="183ca-140">Para los usuarios de la intranet de Contoso, cada oficina debe ser analizada y optimizada para el rendimiento de Internet y tiempos de ida y vuelta al centro de datos de Microsoft Europa aloja a los inquilinos de Office 365, EMS y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="183ca-140">For users on the Contoso intranet, each office must be analyzed and optimized for throughput to the Internet and round-trip times to Microsoft's Europe datacenter hosting the Office 365, EMS, and Dynamics 365 tenants.</span></span>  <br/> |<span data-ttu-id="183ca-p107">Para ofrecer mejor soporte a los empleados móviles, las aplicaciones heredadas y algunos sitios de uso compartido de archivos se están remodelando e implementando como aplicaciones PaaS de Azure. Para un rendimiento óptimo, Contoso planea implementar las nuevas aplicaciones desde varios centros de datos de Azure en todo el mundo. Azure Traffic Manager para enviar solicitudes de aplicaciones cliente, provengan de un usuario móvil o de en un equipo en la oficina, al centro de datos de Azure más cercano que hospede la aplicación.</span><span class="sxs-lookup"><span data-stu-id="183ca-p107">To better support mobile workers, legacy apps and some file sharing sites are being reworked and deployed as Azure PaaS apps. For optimum performance, Contoso plans to deploy the new apps from multiple Azure datacenters across the world. Azure Traffic Manager to send client app requests, whether they originate from a mobile user or a computer in the office, to the nearest Azure datacenter hosting the app.</span></span>  <br/>  <span data-ttu-id="183ca-144">El departamento de TI deberá agregar PaaS performance de las aplicaciones y la distribución de tráfico a su solución de supervisión de estado de red.</span><span class="sxs-lookup"><span data-stu-id="183ca-144">The IT department will need to add PaaS application performance and traffic distribution to their network health monitoring solution.</span></span> <br/> |<span data-ttu-id="183ca-145">Para mover algunos servidores heredados y archiving fuera de los centros de datos del campus de París y agregar servidores según sea necesario para el procesamiento de fin de trimestre, Contoso planea utilizar máquinas virtuales que se ejecutan en servicios de infraestructura de Azure.</span><span class="sxs-lookup"><span data-stu-id="183ca-145">To move some legacy and archival servers out of the Paris campus datacenters and add servers as needed for quarter-end processing, Contoso plans to use virtual machines running in Azure infrastructure services.</span></span>  <br/> <span data-ttu-id="183ca-146">Las redes virtuales de Azure que contienen estos servidores deben diseñarse para los espacios de direcciones no se superponen, DNS enrutamiento e integrado.</span><span class="sxs-lookup"><span data-stu-id="183ca-146">The Azure virtual networks that contain these servers must be designed for non-overlapping address spaces, routing, and integrated DNS.</span></span>  <br/> <span data-ttu-id="183ca-147">El departamento de TI debe incluir estos nuevos servidores en su sistema de administración y supervisión de la red.</span><span class="sxs-lookup"><span data-stu-id="183ca-147">The IT department must include these new servers in their network management and monitoring system.</span></span>  <br/> |
   
## <a name="contosos-use-of-expressroute"></a><span data-ttu-id="183ca-148">Uso de Contoso de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="183ca-148">Contoso's use of ExpressRoute</span></span>

<span data-ttu-id="183ca-p108">ExpressRoute es una conexión WAN dedicada desde su ubicación en una ubicación de interconexión de Microsoft que se conecta a la red a la red de la nube de Microsoft. Las conexiones de ExpressRoute proporcionan performance predecible y un tiempo de actividad del 99,9% SLA. .</span><span class="sxs-lookup"><span data-stu-id="183ca-p108">ExpressRoute is a dedicated WAN connection from your location to a Microsoft peering location that connects your network to the Microsoft cloud network. ExpressRoute connections provide predictable performance and a 99.9% uptime SLA. .</span></span>
  
<span data-ttu-id="183ca-p109">Con una conexión ExpressRoute, está conectado a la red de la nube de Microsoft y todas las ubicaciones de centros de datos de Microsoft en el mismo continente. El tráfico entre la ubicación de interconexión de la nube y el centro de datos de Microsoft de destino se realiza a través de la red de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="183ca-p109">With an ExpressRoute connection, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network</span></span>
  
<span data-ttu-id="183ca-154">**Figura 3: La nube red de Microsoft en todo el mundo**</span><span class="sxs-lookup"><span data-stu-id="183ca-154">**Figure 3: The Microsoft cloud network worldwide**</span></span>

![La red mundial en la nube de Microsoft](images/Contoso_Poster/MS_WW_Cloud.png)
  
<span data-ttu-id="183ca-156">La figura 3 muestra la red en la nube de Microsoft interconectada para las distintas regiones del mundo.</span><span class="sxs-lookup"><span data-stu-id="183ca-156">Figure 3 shows the interconnected Microsoft cloud network for the various regions of the world.</span></span>
  
<span data-ttu-id="183ca-p110">Con ExpressRoute Premium, puede llegar a cualquier centro de datos de Microsoft de cualquier continente y desde cualquier ubicación de emparejamiento de Microsoft de cualquier continente. El tráfico entre continentes se transmite a través de la red en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="183ca-p110">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="183ca-159">Basándose en el análisis de tráfico actual y futuro a las ofertas de nube de Microsoft, Contoso ha realizado una evaluación de la red e implementado una a cualquier conexión ExpressRoute (basadas en MPLS) para obtener acceso a recursos de Azure, con interconexión privada y pública relaciones de la sede de París para la ubicación de interconexión de Microsoft en Europa.</span><span class="sxs-lookup"><span data-stu-id="183ca-159">Based on the analysis of current and future traffic to Microsoft's cloud offerings, Contoso has performed a network assessment and implemented an any-to-any (MPLS-based) ExpressRoute connection for access to Azure resources, with private and public peering relationships, from the Paris headquarters to the Microsoft peering location in Europe.</span></span>
  
<span data-ttu-id="183ca-160">Esta conexión le dará de al departamento de TI de Contoso:</span><span class="sxs-lookup"><span data-stu-id="183ca-160">This connection will give Contoso's IT department:</span></span>
  
- <span data-ttu-id="183ca-161">Rendimiento coherente para la administración de aplicaciones PaaS de Azure distribuidas</span><span class="sxs-lookup"><span data-stu-id="183ca-161">Consistent performance for administration of distributed Azure PaaS apps</span></span>
    
    <span data-ttu-id="183ca-p111">Todos de los desarrolladores de aplicaciones y de infraestructura central de Contoso administradores están en el campus de París. Con aplicaciones de Azure PaaS distribuidas a centros de datos distintos de Azure todo el mundo, Contoso necesita performance consistente en el campus de París para administrar las aplicaciones y sus recursos de almacenamiento de información, que consisten en TB de documentos.</span><span class="sxs-lookup"><span data-stu-id="183ca-p111">All of Contoso's application developers and core infrastructure IT administrators are in the Paris campus. With Azure PaaS apps distributed to different Azure datacenters around the world, Contoso needs consistent performance from the Paris campus to administer the apps and their storage resources, which consist of TB of documents.</span></span>
    
- <span data-ttu-id="183ca-164">Rendimiento constante para la administración de servidores en IaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="183ca-164">Consistent performance for administration of servers in Azure IaaS</span></span>
    
    <span data-ttu-id="183ca-p112">Los administradores de centros de datos de Contoso están en el campus de París y los servidores que se desplegarán en Azure son una extensión del centro de datos de París. Contoso necesita performance consistente a estos nuevos servidores para tener acceso a aplicaciones heredadas y almacenamiento para archiving y procesamiento de fin de trimestre.</span><span class="sxs-lookup"><span data-stu-id="183ca-p112">Contoso's datacenter administrators are in the Paris campus and the servers to be deployed in Azure are an extension of the Paris datacenter. Contoso needs consistent performance to these new servers for access to legacy apps and archival storage and for end-of-quarter processing.</span></span>
    
## <a name="contosos-path-to-cloud-networking-readiness"></a><span data-ttu-id="183ca-167">Ruta de acceso de Contoso en la preparación de redes de nube</span><span class="sxs-lookup"><span data-stu-id="183ca-167">Contoso's path to cloud networking readiness</span></span>

<span data-ttu-id="183ca-168">Contoso usa los pasos siguientes para preparar su red para la nube de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="183ca-168">Contoso uses the following steps to ready their network for the Microsoft cloud:</span></span>
  
1. <span data-ttu-id="183ca-169">Optimizar los equipos de los empleados para el acceso a Internet</span><span class="sxs-lookup"><span data-stu-id="183ca-169">Optimize employee computers for Internet access</span></span>
    
    <span data-ttu-id="183ca-170">Se comprobarán los equipos individuales para garantizar que la pila de TCP/IP más reciente, el explorador, los controladores NIC y las actualizaciones de seguridad y del sistema operativo estén instalados.</span><span class="sxs-lookup"><span data-stu-id="183ca-170">Individual computers will be checked to ensure that the latest TCP/IP stack, browser, NIC drivers, and security and operating system updates are installed.</span></span>
    
2. <span data-ttu-id="183ca-171">Analizar el uso de la conexión a Internet en cada oficina y aumentarlo según sea necesario</span><span class="sxs-lookup"><span data-stu-id="183ca-171">Analyze Internet connection utilization at each office and increase as needed</span></span>
    
    <span data-ttu-id="183ca-172">Se analizará cada oficina para el uso actual de Internet y ancho de banda del vínculo WAN aumentará si funciona el 70% o mayor utilización.</span><span class="sxs-lookup"><span data-stu-id="183ca-172">Each office will be analyzed for the current Internet usage and WAN link bandwidth will be increased if operating at 70% or above utilization.</span></span>
    
3. <span data-ttu-id="183ca-173">Analizar sistemas DMZ en cada oficina para un rendimiento óptimo</span><span class="sxs-lookup"><span data-stu-id="183ca-173">Analyze DMZ systems at each office for optimal performance</span></span>
    
    <span data-ttu-id="183ca-p113">Se analizarán los firewall, los ID y otros sistemas de la ruta de acceso de Internet para conseguir un rendimiento óptimo. Los servidores proxy se actualizarán según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="183ca-p113">Firewalls, IDSs, and other systems in the Internet path will be analyzed for optimal performance. Proxy servers will be updated or upgraded as needed.</span></span>
    
4. <span data-ttu-id="183ca-176">Agregar ExpressRoute para las instalaciones de París</span><span class="sxs-lookup"><span data-stu-id="183ca-176">Add ExpressRoute for the Paris campus</span></span>
    
    <span data-ttu-id="183ca-177">Proporciona acceso coherente a los recursos de Azure para la administración de cargas de trabajo Azure PaaS e IaaS.</span><span class="sxs-lookup"><span data-stu-id="183ca-177">Provides consistent access to Azure resources for administration of Azure PaaS and IaaS workloads.</span></span>
    
5. <span data-ttu-id="183ca-178">Crear y probar un perfil de Azure Traffic Manager para aplicaciones PaaS de Azure</span><span class="sxs-lookup"><span data-stu-id="183ca-178">Create and test an Azure Traffic Manager profile for Azure PaaS apps</span></span>
    
    <span data-ttu-id="183ca-179">Probar un perfil de Azure Traffic Manager que use el método de enrutamiento del rendimiento para obtener experiencia en la distribución de tráfico de Internet a ubicaciones regionales.</span><span class="sxs-lookup"><span data-stu-id="183ca-179">Test an Azure Traffic Manager profile that uses the performance routing method to gain experience in distributing Internet traffic to regional locations.</span></span>
    
6. <span data-ttu-id="183ca-180">Reservar espacio de direcciones privadas para VNets de Azure</span><span class="sxs-lookup"><span data-stu-id="183ca-180">Reserve private address space for Azure VNets</span></span>
    
    <span data-ttu-id="183ca-181">Según el número de servidores proyectados a corto y largo plazo en IaaS de Azure, reserva el espacio de direcciones privadas para las redes virtuales de Azure y sus subredes.</span><span class="sxs-lookup"><span data-stu-id="183ca-181">Based on the numbers of projected short and long-term servers in Azure IaaS, reserve private address space for Azure VNets and their subnets.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="183ca-182">See Also</span><span class="sxs-lookup"><span data-stu-id="183ca-182">See Also</span></span>

[<span data-ttu-id="183ca-183">Contoso en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="183ca-183">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="183ca-184">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="183ca-184">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="183ca-185">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="183ca-185">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



