---
title: ExpressRoute para la conectividad en la nube de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/12/2019
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: 'Resumen: Descubra cómo ExpressRoute puede ayudarle mediante conexiones más rápidas y fiables a los servicios y las plataformas en la nube de Microsoft.'
ms.openlocfilehash: a3b36e98c946bc3ae7281bd38cd4b98820ee8afb
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33488196"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="ebe38-103">ExpressRoute para la conectividad en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ebe38-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="ebe38-104">**Resumen:** Descubra cómo ExpressRoute puede ayudarle mediante conexiones más rápidas y fiables a los servicios y las plataformas en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="ebe38-105">ExpressRoute proporciona una conexión de red privada, dedicada y de alto rendimiento con la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="ebe38-106">ExpressRoute a la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ebe38-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="ebe38-107">Esta es la ruta de acceso de red a la nube de Microsoft sin una conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ebe38-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="ebe38-108">**Figura 1: La ruta de acceso de red sin ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="ebe38-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![Figura 1: La ruta de acceso de red sin ExpressRoute](media/Network-Poster/ExpressRoute.png)
  
<span data-ttu-id="ebe38-p101">La figura 1 muestra la ruta de acceso típica entre una red local y la nube de Microsoft. El perímetro de red local se conecta a Internet a través de un vínculo WAN a un ISP. Después el tráfico viaja por Internet hasta el perímetro de la nube de Microsoft. Las ofertas de la nube de Microsoft incluyen Office 365, Microsoft Azure, Microsoft Intune y Dynamics 365. Los usuarios de una organización pueden encontrarse en la red local o en Internet.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="ebe38-115">Sin una conexión de ExpressRoute, la única parte de la ruta de acceso a la nube de Microsoft que puede controlar (y que puede tener una relación con el proveedor de servicios) es el vínculo entre el perímetro de la red local y el ISP.</span><span class="sxs-lookup"><span data-stu-id="ebe38-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="ebe38-116">La ruta de acceso entre el ISP y el perímetro de la nube de Microsoft es un sistema de entrega de mejor esfuerzo en Internet sujeto a interrupciones, congestión de tráfico y la supervisión de usuarios malintencionados.</span><span class="sxs-lookup"><span data-stu-id="ebe38-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="ebe38-117">Los usuarios de Internet, como usuarios móviles o remotos, envían el tráfico a la nube de Microsoft a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="ebe38-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="ebe38-118">Estas son las rutas de acceso de red a la nube de Microsoft con una conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ebe38-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="ebe38-119">**Figura 2: Las rutas de acceso de red con ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="ebe38-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![Figura 2: La ruta de acceso de red con ExpressRoute](media/Network-Poster/ExpressRoute-post.png)
  
<span data-ttu-id="ebe38-p102">La figura 2 muestra dos rutas de acceso de red. El tráfico a Microsoft Intune viaja por la misma ruta que el tráfico normal de Internet. El tráfico que va a Office 365, Microsoft Azure y Dynamics 365 viaja a través de la conexión de ExpressRoute, una ruta dedicada que está entre el perímetro de la red local y el perímetro de la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="ebe38-124">Ahora, con una conexión de ExpressRoute, puede tener control, a través de una relación con su proveedor de servicios, sobre toda la ruta de tráfico desde su perímetro hasta el perímetro de la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-124">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge.</span></span> <span data-ttu-id="ebe38-125">Esta conexión puede ofrecer un rendimiento predecible y un [SLA de tiempo de actividad de 99,95%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span><span class="sxs-lookup"><span data-stu-id="ebe38-125">This connection can offer predictable performance and a [99.95% uptime SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).</span></span>
  
<span data-ttu-id="ebe38-p104">Ahora podrá disfrutar de un rendimiento y una latencia predecibles, según la conexión de su proveedor de servicios, en los servicios de Office 365, Azure y Dynamics 365. En este momento no se admiten las Conexiones de ExpressRoute a Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="ebe38-128">El tráfico enviado a través de la conexión de ExpressRoute ya no está sujeto a las interrupciones de Internet, la congestión del tráfico ni la supervisión.</span><span class="sxs-lookup"><span data-stu-id="ebe38-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="ebe38-p105">Los usuarios de Internet, como usuarios móviles o remotos, siguen enviando el tráfico a la nube de Microsoft a través de Internet. Una excepción es el tráfico a una línea intranet de una aplicación empresarial hospedada en IaaS de Azure, que se envía por la conexión de ExpressRoute a través de una conexión de acceso remoto a la red local.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="ebe38-131">Incluso con una conexión de ExpressRoute, una parte del tráfico se sigue enviando a través de Internet, como las consultas de DNS, la comprobación de la lista de revocación de certificados y las solicitudes de red de entrega de contenido (CDN).</span><span class="sxs-lookup"><span data-stu-id="ebe38-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="ebe38-132">Consulte estos recursos adicionales para obtener más información:</span><span class="sxs-lookup"><span data-stu-id="ebe38-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="ebe38-133">ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="ebe38-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="ebe38-134">ExpressRoute para Azure</span><span class="sxs-lookup"><span data-stu-id="ebe38-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="ebe38-135">Ventajas de ExpressRoute para Azure</span><span class="sxs-lookup"><span data-stu-id="ebe38-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="ebe38-136">Estas son algunas de las ventajas de usar ExpressRoute para los servicios en la nube basados en Azure:</span><span class="sxs-lookup"><span data-stu-id="ebe38-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="ebe38-p106">**Rendimiento predecible:** con una ruta dedicada al perímetro de la nube de Microsoft, el rendimiento no está sujeto a las interrupciones del proveedor de Internet y tiene un pico en el tráfico de Internet. Puede determinar a los proveedores y responsabilizarlos con un acuerdo de nivel de servicio de rendimiento y latencia en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="ebe38-p107">**Privacidad de los datos para el tráfico:** los usuarios malintencionados no podrán supervisar ni capturar o analizar paquetes del tráfico enviado a través de la conexión dedicada de ExpressRoute. Es tan seguro como usar vínculos WAN basados en Multiprotocol Label Switching (MPLS).</span><span class="sxs-lookup"><span data-stu-id="ebe38-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="ebe38-141">**Conexiones de alto rendimiento:** gracias a la amplia compatibilidad con las conexiones de ExpressRoute, los proveedores de Exchange y los proveedores de servicios de red, podemos obtener un vínculo de hasta 10 Gbps a la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="ebe38-142">**Menor coste en algunas configuraciones:** aunque las conexiones de ExpressRoute suponen un coste adicional, en algunos casos una sola conexión de ExpressRoute puede costar menos que aumentar la capacidad de Internet en varias ubicaciones de la organización para proporcionar un rendimiento adecuado en los servicios en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="ebe38-p108">Una conexión de ExpressRoute no garantiza un mayor rendimiento en todas las configuraciones. Se puede obtener un rendimiento menor a través de una conexión de ExpressRoute de ancho de banda bajo que a través de una conexión a Internet de ancho de banda alto que esté a unos pocos saltos de un centro de datos regional de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="ebe38-145">Para conocer las recomendaciones más recientes para el uso de ExpressRoute con Office 365, consulte [Azure ExpressRoute para Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="ebe38-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="ebe38-146">Modelos de conectividad de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="ebe38-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="ebe38-147">La tabla 1 muestra los tres modelos de conectividad principales para las conexiones de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ebe38-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="ebe38-148">**Colocalizado en un intercambio de nube**</span><span class="sxs-lookup"><span data-stu-id="ebe38-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="ebe38-149">**Ethernet de punto a punto**</span><span class="sxs-lookup"><span data-stu-id="ebe38-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="ebe38-150">**Conexión (IP VPN) universal**</span><span class="sxs-lookup"><span data-stu-id="ebe38-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![Modelo de conectividad de ExpressRoute: Colocalizado en un intercambio de nube](media/Network-Poster/ER-Conn1.png)|![Modelo de conectividad de ExpressRoute: Ethernet de punto a punto](media/Network-Poster/ER-Conn2.png)|![Modelo de conectividad de ExpressRoute: Conexión (IP VPN) universal](media/Network-Poster/ER-Conn3.png)|
|<span data-ttu-id="ebe38-154">Si el centro de datos se encuentra colocalizado en instalaciones con un intercambio de nube, puede solicitar una conexión cruzada virtual a la nube de Microsoft a través del intercambio de Ethernet del proveedor de colocalización.</span><span class="sxs-lookup"><span data-stu-id="ebe38-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="ebe38-155">Si el centro de datos se encuentra en sus instalaciones, puede usar un vínculo punto a punto de Ethernet para conectarse a la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="ebe38-156">Si ya usa un proveedor de IP VPN (MPLS) para conectar los sitios de la organización, una conexión de ExpressRoute a la nube de Microsoft actúa como otra ubicación en su WAN privada.</span><span class="sxs-lookup"><span data-stu-id="ebe38-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="ebe38-157">**Tabla 1: Modelos de conectividad de ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="ebe38-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="ebe38-158">Relaciones de emparejamiento de ExpressRoute a los servicios en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ebe38-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="ebe38-159">Una sola conexión de ExpressRoute admite hasta dos relaciones de emparejamiento del Protocolo de puerta de enlace de borde (BGP) diferentes a distintas partes de la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-159">A single ExpressRoute connection supports up to two different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud.</span></span> <span data-ttu-id="ebe38-160">BPG usa relaciones de emparejamiento para establecer la confianza e intercambiar información de enrutamiento.</span><span class="sxs-lookup"><span data-stu-id="ebe38-160">BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="ebe38-161">**Figura 3: las dos relaciones BGP diferentes en una sola conexión de ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="ebe38-161">**Figure 3: The two different BGP relationships in a single ExpressRoute connection**</span></span>

![Figura 3: las dos relaciones BGP diferentes en una sola conexión de ExpressRoute](media/Network-Poster/ERPeering.png)
  
<span data-ttu-id="ebe38-163">La figura 3 muestra una conexión de ExpressRoute desde una red local.</span><span class="sxs-lookup"><span data-stu-id="ebe38-163">Figure 3 shows an ExpressRoute connection from an on-premises network.</span></span> <span data-ttu-id="ebe38-164">La conexión de ExpressRoute tiene dos relaciones de emparejamiento lógicas.</span><span class="sxs-lookup"><span data-stu-id="ebe38-164">The ExpressRoute connection has two logical peering relationships.</span></span> <span data-ttu-id="ebe38-165">Una relación de emparejamiento de Microsoft va a los servicios SaaS de Microsoft, incluidos Office 365, Dynamcs 365 y los servicios PaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="ebe38-165">A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365, Dynamcs 365, and Azure PaaS services.</span></span> <span data-ttu-id="ebe38-166">Una relación de emparejamiento privada va a IaaS de Azure y a una puerta de enlace de red virtual que hospeda máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="ebe38-166">A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="ebe38-167">La relación de emparejamiento de BGP de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="ebe38-167">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="ebe38-168">Va de un enrutador de la DMZ a las direcciones públicas de los servicios de Office 365, Dynamics 365 y Azure.</span><span class="sxs-lookup"><span data-stu-id="ebe38-168">Is from a router in your DMZ to the public addresses of Office 365, Dynamics 365, and Azure services.</span></span> 
    
- <span data-ttu-id="ebe38-169">Admite la comunicación iniciada bidireccionalmente.</span><span class="sxs-lookup"><span data-stu-id="ebe38-169">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="ebe38-170">La relación de emparejamiento privada de BGP:</span><span class="sxs-lookup"><span data-stu-id="ebe38-170">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="ebe38-171">Va de un enrutador del perímetro de la red de su organización a las direcciones IP privadas asignadas a sus redes virtuales de Azure.</span><span class="sxs-lookup"><span data-stu-id="ebe38-171">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="ebe38-172">Admite la comunicación iniciada bidireccionalmente.</span><span class="sxs-lookup"><span data-stu-id="ebe38-172">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="ebe38-173">Es una extensión de la red de su organización a la nube de Microsoft que incluye el direccionamiento y el enrutamiento internamente coherentes.</span><span class="sxs-lookup"><span data-stu-id="ebe38-173">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>

>[!Note]
><span data-ttu-id="ebe38-174">La relación BGP de emparejamiento pública descrita en las versiones anteriores de este artículo está en desuso.</span><span class="sxs-lookup"><span data-stu-id="ebe38-174">The public peering BGP relationship described in previous versions of this article has been deprecated.</span></span>
>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="ebe38-175">Ejemplo de la implementación de una aplicación y el flujo de tráfico con ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="ebe38-175">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="ebe38-p111">El modo en que el tráfico viaja a través de las conexiones de ExpressRoute y dentro de la nube de Microsoft es una función de las rutas en los saltos de la ruta de acceso entre el origen, el destino y el comportamiento de la aplicación. En este ejemplo vemos una aplicación que se ejecuta en una máquina virtual de Azure que tiene acceso a una granja de SharePoint local a través de una conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p111">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="ebe38-178">**Figura 4: Una aplicación de una máquina virtual de Azure que obtiene acceso a una granja de SharePoint local**</span><span class="sxs-lookup"><span data-stu-id="ebe38-178">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![Figura 4: Una aplicación de una máquina virtual de Azure que obtiene acceso a una granja de SharePoint local](media/Network-Poster/ER-App-Flow1.png)

  
<span data-ttu-id="ebe38-180">La figura 4 muestra una granja de SharePoint local, una conexión VPN de sitio a sitio entre la red local y una red virtual en IaaS de Azure, un servidor de aplicaciones que se ejecuta como una máquina virtual de IaaS de Azure y el flujo de tráfico entre el servidor de aplicaciones y la granja de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ebe38-180">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="ebe38-181">La aplicación busca la dirección IP de la granja de SharePoint usando el DNS local y todo el tráfico atraviesa la conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="ebe38-181">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="ebe38-182">Esta organización migró su granja de SharePoint local a SharePoint Online en Office 365 e implementó una conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ebe38-182">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="ebe38-183">**Figura 5: Traslado de la granja de SharePoint local a SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="ebe38-183">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![Figura 5: Traslado de la granja de SharePoint local a SharePoint Online](media/Network-Poster/Hairpin1.png)
  
<span data-ttu-id="ebe38-p112">La figura 5 muestra la adición de una conexión de ExpressRoute con relaciones de emparejamiento a los servicios SaaS de Microsoft, a Office 365 y a los servicios IaaS de Azure que contienen el servidor de aplicaciones en una red virtual. La granja local de SharePoint se migró a Office 365.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p112">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="ebe38-187">Con las relaciones de emparejamiento privadas y de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="ebe38-187">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="ebe38-188">Desde la puerta de enlace de red virtual de Azure, hay disponibles ubicaciones locales en la conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ebe38-188">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="ebe38-189">Desde la suscripción a Office 365, las direcciones IP públicas de dispositivos perimetrales, como servidores proxy, están disponibles en la conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ebe38-189">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="ebe38-190">Desde el perímetro de la red local, las direcciones IP privadas de la red virtual de Azure y las direcciones IP públicas de Office 365 están disponibles en la conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ebe38-190">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="ebe38-191">Cuando la aplicación tiene acceso a las direcciones URL de SharePoint Online, reenvía el tráfico a través de la conexión de ExpressRoute a un servidor proxy del perímetro.</span><span class="sxs-lookup"><span data-stu-id="ebe38-191">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="ebe38-p113">Cuando el servidor proxy busca la dirección IP de SharePoint Online, reenvía el tráfico de vuelta a través de la conexión de ExpressRoute. El tráfico de respuesta recorre la ruta inversa.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p113">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="ebe38-194">**Figura 6: Flujo de tráfico cuando se migra la granja de SharePoint a SharePoint Online en Office 365**</span><span class="sxs-lookup"><span data-stu-id="ebe38-194">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![Figura 6: Flujo de tráfico cuando se migra la granja de SharePoint a SharePoint Online en Office 365](media/Network-Poster/Hairpin2.png)

  
<span data-ttu-id="ebe38-196">La figura 6 muestra cómo fluye el tráfico entre el servidor de aplicaciones y SharePoint Online en Office 365 a través de la relación de emparejamiento privada del servidor de aplicaciones al perímetro de la red local y después del perímetro a Office 365 a través de la relación de emparejamiento de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-196">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="ebe38-197">El resultado es una redirección al origen, consecuencia del comportamiento de la aplicación y el enrutamiento.</span><span class="sxs-lookup"><span data-stu-id="ebe38-197">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="ebe38-198">Red de nube de Microsoft y de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="ebe38-198">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="ebe38-199">Las conexiones de ExpressRoute están disponibles en dos versiones: ExpressRoute y ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="ebe38-199">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="ebe38-200">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="ebe38-200">ExpressRoute</span></span>

<span data-ttu-id="ebe38-201">El modo en que el tráfico fluye entre la red de su organización y un centro de datos de Microsoft es una combinación de:</span><span class="sxs-lookup"><span data-stu-id="ebe38-201">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="ebe38-202">Sus ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="ebe38-202">Your locations.</span></span>
    
- <span data-ttu-id="ebe38-203">Las ubicaciones de emparejamiento en la nube de Microsoft (las ubicaciones físicas para conectarse al perímetro de Microsoft).</span><span class="sxs-lookup"><span data-stu-id="ebe38-203">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="ebe38-204">Las ubicaciones de los centros de datos de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-204">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="ebe38-205">Las ubicaciones de los centros de datos de Microsoft y las de emparejamiento en la nube están conectadas a la red en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-205">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="ebe38-p114">Cuando se crea una conexión de ExpressRoute a una ubicación de emparejamiento en la nube de Microsoft, nos conectamos a la red en la nube de Microsoft y a todas las ubicaciones de centros de datos de Microsoft que hay en el mismo continente. El tráfico entre la ubicación de emparejamiento en la nube y el centro de datos de Microsoft de destino se realiza a través de la red en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p114">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="ebe38-208">Esto puede hacer que la entrega en los centros de datos locales de Microsoft no sea óptima para el modelo de conectividad universal.</span><span class="sxs-lookup"><span data-stu-id="ebe38-208">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="ebe38-209">**Figura 7: ejemplo de una organización distribuida geográficamente que usa una sola conexión de ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="ebe38-209">**Figure 7: Example of a geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![Figura 7: ejemplo de una organización distribuida geográficamente que usa una sola conexión de ExpressRoute](media/Network-Poster/MSNet1.png)
  
<span data-ttu-id="ebe38-p115">La figura 7 muestra una organización con dos ubicaciones, la ubicación 1 en el noroeste de Estados Unidos y la ubicación 2 en el noreste. Están conectados por un proveedor WAN universal. Esta organización tiene también una conexión de ExpressRoute a una ubicación de emparejamiento de Microsoft de la costa oeste. El tráfico de la ubicación 2 en el noreste destinado a un centro de datos de la costa este debe atravesar toda la red WAN de la organización hasta llegar a la costa oeste, a la ubicación de emparejamiento de Microsoft, y luego volver a recorrer todo el país por la red en la nube de Microsoft hasta llegar al centro de datos de la costa este.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p115">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="ebe38-215">Para lograr una entrega óptima, use varias conexiones de ExpressRoute a ubicaciones regionales de emparejamiento en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-215">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="ebe38-216">**Figura 8: El uso de varias conexiones de ExpressRoute para la entrega óptima en centros de datos regionales**</span><span class="sxs-lookup"><span data-stu-id="ebe38-216">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![Figura 8: El uso de varias conexiones de ExpressRoute para la entrega óptima en centros de datos regionales](media/Network-Poster/MSNet2.png)
  
<span data-ttu-id="ebe38-p116">La figura 8 muestra la misma organización con dos conexiones de ExpressRoute, una para cada ubicación, a ubicaciones de emparejamiento de Microsoft locales de una región. En esta configuración, el tráfico de la ubicación 2 en el noreste destinado a un centro de datos de la costa este va directamente a una ubicación de emparejamiento de la costa este, a la red en la nube de Microsoft, y luego al centro de datos de la costa este.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p116">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="ebe38-220">Varias conexiones de ExpressRoute pueden proporcionar:</span><span class="sxs-lookup"><span data-stu-id="ebe38-220">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="ebe38-221">Mejor rendimiento a ubicaciones de centros de datos de Microsoft locales de una región.</span><span class="sxs-lookup"><span data-stu-id="ebe38-221">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="ebe38-222">Mayor disponibilidad en la nube de Microsoft cuando una conexión local de ExpressRoute deje de estar disponible.</span><span class="sxs-lookup"><span data-stu-id="ebe38-222">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="ebe38-p117">Esto funciona bien con las organizaciones que están en el mismo continente. Sin embargo, el tráfico a los centros de datos de Microsoft que están fuera del continente de la organización viaja a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p117">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="ebe38-225">En el caso del tráfico intercontinental que va por la red en la nube de Microsoft, debe usar conexiones de ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="ebe38-225">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="ebe38-226">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="ebe38-226">ExpressRoute Premium</span></span>

<span data-ttu-id="ebe38-227">En el caso de las organizaciones que se distribuyen globalmente en varios continentes, puede usar ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="ebe38-227">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="ebe38-p118">Con ExpressRoute Premium, puede llegar a cualquier centro de datos de Microsoft de cualquier continente y desde cualquier ubicación de emparejamiento de Microsoft de cualquier continente. El tráfico entre continentes se transmite a través de la red en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p118">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="ebe38-230">Con varias conexiones de ExpressRoute Premium, podemos conseguir:</span><span class="sxs-lookup"><span data-stu-id="ebe38-230">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="ebe38-231">Mejor rendimiento en centros de datos de Microsoft locales de un continente.</span><span class="sxs-lookup"><span data-stu-id="ebe38-231">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="ebe38-232">Mayor disponibilidad en la nube de Microsoft global cuando una conexión local de ExpressRoute deje de estar disponible.</span><span class="sxs-lookup"><span data-stu-id="ebe38-232">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="ebe38-233">ExpressRoute Premium es necesario para las conexiones de ExpressRoute basadas en Office 365.</span><span class="sxs-lookup"><span data-stu-id="ebe38-233">ExpressRoute Premium is required for Office 365-based ExpressRoute connections.</span></span>
  
<span data-ttu-id="ebe38-234">**Figura 9: La red mundial en la nube de Microsoft**</span><span class="sxs-lookup"><span data-stu-id="ebe38-234">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![Figura 9: La red mundial en la nube de Microsoft](media/Network-Poster/MSNet3.png)
  
<span data-ttu-id="ebe38-p119">La figura 9 muestra un diagrama lógico de la red mundial en la nube de Microsoft, con redes que abarcan los continentes y las regiones del mundo y sus interconexiones. Cuando cada parte de la red en la nube de Microsoft está en un continente, una empresa global crea conexiones de ExpressRoute Premium desde sus oficinas concentradoras regionales a ubicaciones de emparejamiento de Microsoft locales.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p119">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="ebe38-238">En el caso de una oficina regional, el tráfico adecuado de Office 365 que va a:</span><span class="sxs-lookup"><span data-stu-id="ebe38-238">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="ebe38-239">Centros de datos de Office 365 continentales viaja a través de la red en la nube de Microsoft dentro del continente.</span><span class="sxs-lookup"><span data-stu-id="ebe38-239">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="ebe38-240">Centros de datos de Office 365 en otro continente viaja a través de la red intercontinental en nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-240">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="ebe38-241">Para más información, visite:</span><span class="sxs-lookup"><span data-stu-id="ebe38-241">For more information, see:</span></span>
  
- [<span data-ttu-id="ebe38-242">Aprendizaje de Azure ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="ebe38-242">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="ebe38-243">Planear la red y ajustar el rendimiento de Office 365</span><span class="sxs-lookup"><span data-stu-id="ebe38-243">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
## <a name="expressroute-options"></a><span data-ttu-id="ebe38-244">Opciones de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="ebe38-244">ExpressRoute options</span></span>

<span data-ttu-id="ebe38-245">También puede incorporar las opciones siguientes a la implementación de ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="ebe38-245">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="ebe38-246">**Seguridad en el perímetro:** para proporcionar seguridad avanzada en el tráfico enviado y recibido a través de la conexión de ExpressRoute, como la inspección del tráfico o la detección de intrusiones y malware, coloque las aplicaciones de seguridad en la ruta de acceso del tráfico dentro de la red perimetral o en el perímetro de la intranet.</span><span class="sxs-lookup"><span data-stu-id="ebe38-246">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
- <span data-ttu-id="ebe38-247">**Tráfico de Internet para máquinas virtuales:** Para evitar que las máquinas virtuales de Azure inicien el tráfico directamente con ubicaciones de Internet, anuncie la ruta predeterminada a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ebe38-247">**Internet traffic for VMs:** To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft.</span></span> <span data-ttu-id="ebe38-248">El tráfico de Internet se enruta a través de la conexión de ExpressRoute y a través de los servidores proxy locales.</span><span class="sxs-lookup"><span data-stu-id="ebe38-248">Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers.</span></span> <span data-ttu-id="ebe38-249">El tráfico de las máquinas virtuales de Azure a los servicios PaaS de Azure o a Office 365 se vuelve a enrutar a través de la conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="ebe38-249">Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="ebe38-p121">**Optimizadores de WAN:** puede implementar optimizadores de WAN a ambos lados de una conexión de emparejamiento privada para una red virtual de Azure entre locales (VNet). Dentro de la VNet de Azure, use una aplicación de red del optimizador de WAN de Azure Marketplace y el enrutamiento definido por el usuario para enrutar el tráfico a través de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p121">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="ebe38-p122">**Calidad de servicio:** use valores de Punto de código de servicios diferenciados (DSCP) en el encabezado IPv4 del tráfico para marcarlo para voz, vídeo/interactivo o entrega de mejor esfuerzo. Esto es especialmente importante en la relación de emparejamiento de Microsoft y en el tráfico de Skype Empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="ebe38-p122">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="ebe38-254">Consulte estos recursos adicionales para obtener más información:</span><span class="sxs-lookup"><span data-stu-id="ebe38-254">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="ebe38-255">ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="ebe38-255">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="ebe38-256">Aprendizaje de Azure ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="ebe38-256">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="ebe38-257">ExpressRoute para Azure</span><span class="sxs-lookup"><span data-stu-id="ebe38-257">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="ebe38-258">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="ebe38-258">Next step</span></span>

[<span data-ttu-id="ebe38-259">Diseño de redes para SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ebe38-259">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="ebe38-260">Ver también</span><span class="sxs-lookup"><span data-stu-id="ebe38-260">See also</span></span>

[<span data-ttu-id="ebe38-261">Microsoft Cloud Networking para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="ebe38-261">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="ebe38-262">Recursos de arquitectura de TI de Microsoft Cloud</span><span class="sxs-lookup"><span data-stu-id="ebe38-262">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

