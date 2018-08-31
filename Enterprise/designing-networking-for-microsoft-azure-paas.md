---
title: Diseño de redes para PaaS de Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 'Resumen: aprenda a optimizar la red para obtener acceso a PaaS de Microsoft Azure.'
ms.openlocfilehash: d20bb5adb46592363926a2926752ed345823c26e
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915115"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a><span data-ttu-id="f9ab1-103">Diseño de redes para PaaS de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="f9ab1-103">Designing networking for Microsoft Azure PaaS</span></span>

 <span data-ttu-id="f9ab1-104">**Resumen:** aprenda a optimizar la red para obtener acceso a PaaS de Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-104">**Summary:** Understand how to optimize your network for access to Microsoft Azure PaaS.</span></span>
  
<span data-ttu-id="f9ab1-105">La optimización de las redes para aplicaciones PaaS de Azure requiere un ancho de banda de Internet adecuado y puede exigir la distribución del tráfico de red por varios sitios o aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-105">Optimizing networking for Azure PaaS apps requires adequate Internet bandwidth and can require the distribution of network traffic across multiple sites or apps.</span></span>
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a><span data-ttu-id="f9ab1-106">Pasos de planeamiento para hospedar aplicaciones PaaS de una organización en Azure</span><span class="sxs-lookup"><span data-stu-id="f9ab1-106">Planning steps for hosting organization PaaS applications in Azure</span></span>

1. <span data-ttu-id="f9ab1-107">Vea la sección **Pasos para preparar la red para los servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).</span><span class="sxs-lookup"><span data-stu-id="f9ab1-107">Go through the **Steps to prepare your network for Microsoft cloud services** section in [Common elements of Microsoft cloud connectivity](common-elements-of-microsoft-cloud-connectivity.md).</span></span>
    
2. <span data-ttu-id="f9ab1-108">Para optimizar el ancho de banda de Internet, siga los pasos 2 a 4 de la sección **Pasos para preparar la red para los servicios SaaS de Microsoft** del artículo [Diseño de redes para SaaS de Microsoft](designing-networking-for-microsoft-saas.md).</span><span class="sxs-lookup"><span data-stu-id="f9ab1-108">Optimize your Internet bandwidth using steps 2 - 4 of the **Steps to prepare your network for Microsoft SaaS services** section in [Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md).</span></span>
    
3. <span data-ttu-id="f9ab1-109">Determine si necesita una conexión de ExpressRoute a Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-109">Determine whether you need an ExpressRoute connection to Azure.</span></span>
    
4. <span data-ttu-id="f9ab1-110">En el caso de las cargas de trabajo basadas en web, determinar si necesita la Puerta de enlace de aplicaciones de Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-110">For web-based workloads, determine whether you need the Azure Application Gateway.</span></span>
    
5. <span data-ttu-id="f9ab1-111">En el caso de la distribución de tráfico a distintos puntos de conexión en diferentes centros de datos, decidir si necesita Administrador de tráfico de Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-111">For distribution of traffic to different endpoints in different data centers, determine whether you need Azure Traffic Manager.</span></span>
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a><span data-ttu-id="f9ab1-112">Ancho de banda de Internet para las aplicaciones PaaS de la organización</span><span class="sxs-lookup"><span data-stu-id="f9ab1-112">Internet bandwidth for organization PaaS applications</span></span>

<span data-ttu-id="f9ab1-p101">Las aplicaciones de la organización hospedadas en PaaS de Azure requieren ancho de banda de Internet para los usuarios de la intranet. Hay dos opciones:</span><span class="sxs-lookup"><span data-stu-id="f9ab1-p101">Organization applications hosted in Azure PaaS require Internet bandwidth for intranet users. There are two options:</span></span>
  
- <span data-ttu-id="f9ab1-p102">**Opción 1:** Use la canalización existente optimizada para el tráfico de Internet con la capacidad para controlar las cargas máximas. Consulte[Diseño de redes para SaaS de Microsoft](designing-networking-for-microsoft-saas.md) para informarse sobre el perímetro de Internet, el uso de clientes y las consideraciones sobre las operaciones de TI.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-p102">**Option 1:** Use your existing pipe, optimized for Internet traffic with the capacity to handle peak loads. See[Designing networking for Microsoft SaaS](designing-networking-for-microsoft-saas.md) for Internet edge, client usage, and IT operations considerations.</span></span>
    
- <span data-ttu-id="f9ab1-117">**Opción 2:** Para las necesidades de ancho de banda de alto o de baja latencia, use una conexión de ExpressRoute a Azure.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-117">**Option 2:** For high-bandwidth or low latency needs, use an ExpressRoute connection to Azure.</span></span>
    
<span data-ttu-id="f9ab1-118">**Figura 1: Opciones de conexión para conectarse a los servicios PaaS de Azure**</span><span class="sxs-lookup"><span data-stu-id="f9ab1-118">**Figure 1: Connection options for connecting the Azure PaaS services**</span></span>

![Figura 1: Opciones de conexión de los servicios PaaS de Azure](media/Network-Poster/PaaS1.png)
  
<span data-ttu-id="f9ab1-120">La figura 1 muestra una red local que se conecta a los servicios PaaS de Azure a través de una canalización de Internet o ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-120">Figure 1 shows an on-premises network connecting to Azure PaaS services over an Internet pipe or ExpressRoute.</span></span>
  
## <a name="azure-application-gateway"></a><span data-ttu-id="f9ab1-121">Puerta de enlace de aplicación de Azure</span><span class="sxs-lookup"><span data-stu-id="f9ab1-121">Azure Application Gateway</span></span>

<span data-ttu-id="f9ab1-122">Enrutamiento de nivel de aplicación y servicios de equilibrio de carga que permiten compilar un front-end web escalable y altamente disponible en Azure para las aplicaciones web, los servicios en la nube y las máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-122">Application-level routing and load balancing services that let you build a scalable and highly-available web front end in Azure for web apps, cloud services, and virtual machines.</span></span> 
  
<span data-ttu-id="f9ab1-123">**Figura 2: Puerta de enlace de aplicaciones de Azure**</span><span class="sxs-lookup"><span data-stu-id="f9ab1-123">**Figure 2: Azure Application Gateway**</span></span>

![Figura 2: Servicio de puerta de enlace de aplicaciones de Azure](media/Network-Poster/PaaS2.png)
  
<span data-ttu-id="f9ab1-125">La figura 2 muestra la Puerta de enlace de aplicaciones de Azure y cómo las solicitudes de usuario que proceden de Internet pueden enrutarse hacia las aplicaciones web de Azure, los servicios en la nube o las máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-125">Figure 2 shows the Azure Application Gateway and how user requests from the Internet can be routed to Azure web apps, cloud services, or virtual machines.</span></span>
  
<span data-ttu-id="f9ab1-126">Actualmente, la Puerta de enlace de aplicaciones admite la entrega de aplicaciones de capa 7 para lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="f9ab1-126">Application Gateway currently supports layer 7 application delivery for the following:</span></span>
  
- <span data-ttu-id="f9ab1-127">Equilibrio de carga HTTP</span><span class="sxs-lookup"><span data-stu-id="f9ab1-127">HTTP load balancing</span></span>
    
- <span data-ttu-id="f9ab1-128">Afinidad de sesión basada en cookies</span><span class="sxs-lookup"><span data-stu-id="f9ab1-128">Cookie-based session affinity</span></span>
    
- <span data-ttu-id="f9ab1-129">Descarga SSL</span><span class="sxs-lookup"><span data-stu-id="f9ab1-129">SSL offload</span></span>
    
<span data-ttu-id="f9ab1-130">Para obtener más información, consulte [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span><span class="sxs-lookup"><span data-stu-id="f9ab1-130">For more information, see [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).</span></span>
  
## <a name="azure-traffic-manager"></a><span data-ttu-id="f9ab1-131">Administrador de tráfico de Azure</span><span class="sxs-lookup"><span data-stu-id="f9ab1-131">Azure Traffic Manager</span></span>

<span data-ttu-id="f9ab1-132">Distribución de tráfico a distintos puntos de conexión, que pueden incluir servicios en la nube o aplicaciones web de Azure ubicadas en diferentes centros de datos o puntos de conexión externos.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-132">Distribution of traffic to different endpoints, which can include cloud services or Azure web apps located in different data centers or external endpoints.</span></span>
  
<span data-ttu-id="f9ab1-133">Administrador de tráfico usa los siguientes métodos de enrutamiento:</span><span class="sxs-lookup"><span data-stu-id="f9ab1-133">Traffic Manager uses the following routing methods:</span></span>
  
- <span data-ttu-id="f9ab1-134">**Conmutación por error:** los puntos de conexión están en los mismos centros de datos Azure o en otros distintos y queremos usar un punto de conexión principal para todo el tráfico, pero también proporcionar copias de seguridad en caso de que los puntos de conexión principales o de copia de seguridad no estén disponibles.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-134">**Failover:** The endpoints are in the same or different Azure datacenters and you want to use a primary endpoint for all traffic, but provide backups in case the primary or the backup endpoints are unavailable.</span></span>
    
- <span data-ttu-id="f9ab1-135">**Round robin:** quiere distribuir la carga en un conjunto de puntos de conexión en el mismo centro de datos o en centros de datos distintos.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-135">**Round robin:** You want to distribute load across a set of endpoints in the same datacenter or across different datacenters.</span></span>
    
- <span data-ttu-id="f9ab1-136">**Rendimiento:** tenemos puntos de conexión en distintas ubicaciones geográficas y queremos que los clientes solicitantes usen el punto de conexión "más próximo", es decir, el de menor latencia.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-136">**Performance:** You have endpoints in different geographic locations and you want requesting clients to use the "closest" endpoint in terms of the lowest latency.</span></span>
    
<span data-ttu-id="f9ab1-137">Este es un ejemplo de tres aplicaciones web distribuidas geográficamente.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-137">Here is an example for three geographically-distributed web apps.</span></span>
  
<span data-ttu-id="f9ab1-138">**Figura 3: Administrador de tráfico de Azure**</span><span class="sxs-lookup"><span data-stu-id="f9ab1-138">**Figure 3: Azure Traffic Manager**</span></span>

![Figura 3: Administrador de tráfico de Azure](media/Network-Poster/PaaS3.png)
  
<span data-ttu-id="f9ab1-p103">La figura 3 muestra el proceso básico que el Administrador de tráfico usa para enrutar las solicitudes hacia tres aplicaciones web de Azure diferentes en Estados Unidos, Europa y Asia. En el ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f9ab1-p103">Figure 3 shows the basic process that Traffic Manager uses to route requests to three different Azure web apps in United States, Europe, and Asia. In the example:</span></span>
  
1. <span data-ttu-id="f9ab1-142">Una consulta de DNS de usuario para solicitar la dirección URL de un sitio web se dirige al Administrador de tráfico de Azure, que, a su vez, devuelve el nombre de una aplicación web regional basándose en el método de enrutamiento del rendimiento.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-142">A user DNS query for a web site URL gets directed to Azure Traffic Manager, which returns the name of a regional web app, based on the performance routing method.</span></span>
    
2. <span data-ttu-id="f9ab1-143">El usuario inicia el tráfico con la aplicación web regional en Europa.</span><span class="sxs-lookup"><span data-stu-id="f9ab1-143">The user initiates traffic with the regional web app in Europe.</span></span>
    
<span data-ttu-id="f9ab1-144">Para obtener más información, vea [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span><span class="sxs-lookup"><span data-stu-id="f9ab1-144">For more information, see [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).</span></span>

## <a name="next-step"></a><span data-ttu-id="f9ab1-145">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="f9ab1-145">Next step</span></span>

[<span data-ttu-id="f9ab1-146">Diseño de redes para IaaS de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="f9ab1-146">Designing networking for Microsoft Azure IaaS</span></span>](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a><span data-ttu-id="f9ab1-147">Ver también</span><span class="sxs-lookup"><span data-stu-id="f9ab1-147">See also</span></span>

[<span data-ttu-id="f9ab1-148">Microsoft Cloud Networking para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="f9ab1-148">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="f9ab1-149">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="f9ab1-149">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="f9ab1-150">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="f9ab1-150">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



