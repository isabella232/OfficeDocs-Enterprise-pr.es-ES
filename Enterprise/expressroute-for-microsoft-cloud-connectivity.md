---
title: ExpressRoute para la conectividad en la nube de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: bf2295c4-d411-49cd-aaa5-116a4a456c5a
description: "Resumen: Descubra cómo ExpressRoute puede ayudarle mediante conexiones más rápidas y fiables a los servicios y las plataformas en la nube de Microsoft."
ms.openlocfilehash: 40cde8753a5e6de6a76a04198fe90d510ee9a315
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a><span data-ttu-id="9a999-103">ExpressRoute para la conectividad en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9a999-103">ExpressRoute for Microsoft cloud connectivity</span></span>

 <span data-ttu-id="9a999-104">**Resumen:** Descubra cómo ExpressRoute puede ayudarle mediante conexiones más rápidas y fiables a los servicios y las plataformas en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-104">**Summary:** Understand how ExpressRoute can help you with faster and more reliable connections to Microsoft's cloud services and platforms.</span></span>
  
<span data-ttu-id="9a999-105">ExpressRoute proporciona una conexión de red privada, dedicada y de alto rendimiento con la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-105">ExpressRoute provides a private, dedicated, high-throughput network connection to Microsoft's cloud.</span></span>
  
## <a name="expressroute-to-the-microsoft-cloud"></a><span data-ttu-id="9a999-106">ExpressRoute a la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9a999-106">ExpressRoute to the Microsoft cloud</span></span>

<span data-ttu-id="9a999-107">Esta es la ruta de acceso de red a la nube de Microsoft sin una conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="9a999-107">Here is the networking path to the Microsoft cloud without an ExpressRoute connection.</span></span>
  
<span data-ttu-id="9a999-108">**Figura 1: La ruta de acceso de red sin ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="9a999-108">**Figure 1: The networking path without ExpressRoute**</span></span>

![Figura 1: La ruta de acceso de red sin ExpressRoute](images/Network_Poster/ExpressRoute.png)
  
<span data-ttu-id="9a999-p101">La figura 1 muestra la ruta de acceso típica entre una red local y la nube de Microsoft. El perímetro de red local se conecta a Internet a través de un vínculo WAN a un ISP. Después el tráfico viaja por Internet hasta el perímetro de la nube de Microsoft. Las ofertas de la nube de Microsoft incluyen Office 365, Microsoft Azure, Microsoft Intune y Dynamics 365. Los usuarios de una organización pueden encontrarse en la red local o en Internet.</span><span class="sxs-lookup"><span data-stu-id="9a999-p101">Figure 1 shows the typical path between an on-premises network and the Microsoft cloud. The on-premises network edge connects to the Internet through a WAN link to an ISP. The traffic then travels across the Internet to the edge of the Microsoft cloud. Cloud offerings within the Microsoft cloud include Office 365, Microsoft Azure, Microsoft Intune, and Dynamics 365. Users of an organization can be located on the on-premises network or on the Internet.</span></span>
  
<span data-ttu-id="9a999-115">Sin una conexión de ExpressRoute, la única parte de la ruta de acceso a la nube de Microsoft que puede controlar (y que puede tener una relación con el proveedor de servicios) es el vínculo entre el perímetro de la red local y el ISP.</span><span class="sxs-lookup"><span data-stu-id="9a999-115">Without an ExpressRoute connection, the only part of the traffic path to the Microsoft cloud that you can control (and have a relationship with the service provider) is the link between your on-premises network edge and your ISP.</span></span> 
  
<span data-ttu-id="9a999-116">La ruta de acceso entre el ISP y el perímetro de la nube de Microsoft es un sistema de entrega de mejor esfuerzo en Internet sujeto a interrupciones, congestión de tráfico y la supervisión de usuarios malintencionados.</span><span class="sxs-lookup"><span data-stu-id="9a999-116">The path between your ISP and the Microsoft cloud edge is a best-effort delivery system on the Internet subject to outages, traffic congestion, and monitoring by malicious users.</span></span>
  
<span data-ttu-id="9a999-117">Los usuarios de Internet, como usuarios móviles o remotos, envían el tráfico a la nube de Microsoft a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="9a999-117">Users on the Internet, such as roaming or remote users, send their traffic to the Microsoft cloud over the Internet.</span></span>
  
<span data-ttu-id="9a999-118">Estas son las rutas de acceso de red a la nube de Microsoft con una conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="9a999-118">Here are the networking paths to the Microsoft cloud with an ExpressRoute connection.</span></span>
  
<span data-ttu-id="9a999-119">**Figura 2: Las rutas de acceso de red con ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="9a999-119">**Figure 2: The networking paths with ExpressRoute**</span></span>

![Figura 2: La ruta de acceso de red con ExpressRoute](images/Network_Poster/ExpressRoute_post.png)
  
<span data-ttu-id="9a999-p102">La figura 2 muestra dos rutas de acceso de red. El tráfico a Microsoft Intune viaja por la misma ruta que el tráfico normal de Internet. El tráfico que va a Office 365, Microsoft Azure y Dynamics 365 viaja a través de la conexión de ExpressRoute, una ruta dedicada que está entre el perímetro de la red local y el perímetro de la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-p102">Figure 2 shows two networking paths. Traffic to Microsoft Intune travels the same path as normal Internet traffic. Traffic to Office 365, Microsoft Azure, and Dynamics 365 travels across the ExpressRoute connection, a dedicated path between the edge of the on-premises network and the edge of the Microsoft cloud.</span></span>
  
<span data-ttu-id="9a999-p103">Ahora, con una conexión de ExpressRoute, puede tener control, a través de una relación con su proveedor de servicios, sobre toda la ruta de tráfico desde su perímetro hasta el perímetro de la nube de Microsoft. Esta conexión puede ofrecer un rendimiento predecible y un contrato de nivel de servicio con un tiempo de actividad del 99,9%.</span><span class="sxs-lookup"><span data-stu-id="9a999-p103">With an ExpressRoute connection, you now have control, through a relationship with your service provider, over the entire traffic path from your edge to the Microsoft cloud edge. This connection can offer predictable performance and a 99.9% uptime SLA.</span></span>
  
<span data-ttu-id="9a999-p104">Ahora podrá disfrutar de un rendimiento y una latencia predecibles, según la conexión de su proveedor de servicios, en los servicios de Office 365, Azure y Dynamics 365. En este momento no se admiten las Conexiones de ExpressRoute a Microsoft Intune.</span><span class="sxs-lookup"><span data-stu-id="9a999-p104">You can now count on predictable throughput and latency, based on your service provider's connection, to Office 365, Azure, and Dynamics 365 services. ExpressRoute connections to Microsoft Intune are not supported at this time.</span></span>
  
<span data-ttu-id="9a999-128">El tráfico enviado a través de la conexión de ExpressRoute ya no está sujeto a las interrupciones de Internet, la congestión del tráfico ni la supervisión.</span><span class="sxs-lookup"><span data-stu-id="9a999-128">Traffic sent over the ExpressRoute connection is no longer subject to Internet outages, traffic congestion, and monitoring.</span></span>
  
<span data-ttu-id="9a999-p105">Los usuarios de Internet, como usuarios móviles o remotos, siguen enviando el tráfico a la nube de Microsoft a través de Internet. Una excepción es el tráfico a una línea intranet de una aplicación empresarial hospedada en IaaS de Azure, que se envía por la conexión de ExpressRoute a través de una conexión de acceso remoto a la red local.</span><span class="sxs-lookup"><span data-stu-id="9a999-p105">Users on the Internet, such as roaming or remote users, still send their traffic to the Microsoft cloud over the Internet. One exception is traffic to an intranet line of business application hosted in Azure IaaS, which is sent over the ExpressRoute connection via a remote access connection to the on-premises network.</span></span>
  
<span data-ttu-id="9a999-131">Incluso con una conexión de ExpressRoute, una parte del tráfico se sigue enviando a través de Internet, como las consultas de DNS, la comprobación de la lista de revocación de certificados y las solicitudes de red de entrega de contenido (CDN).</span><span class="sxs-lookup"><span data-stu-id="9a999-131">Even with an ExpressRoute connection, some traffic is still sent over the Internet, such as DNS queries, certificate revocation list checking, and content delivery network (CDN) requests.</span></span>
  
<span data-ttu-id="9a999-132">Consulte estos recursos adicionales para obtener más información:</span><span class="sxs-lookup"><span data-stu-id="9a999-132">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="9a999-133">ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="9a999-133">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="9a999-134">ExpressRoute para Azure</span><span class="sxs-lookup"><span data-stu-id="9a999-134">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a><span data-ttu-id="9a999-135">Ventajas de ExpressRoute para Azure</span><span class="sxs-lookup"><span data-stu-id="9a999-135">Advantages of ExpressRoute for Azure</span></span>

<span data-ttu-id="9a999-136">Estas son algunas de las ventajas de usar ExpressRoute para los servicios en la nube basados en Azure:</span><span class="sxs-lookup"><span data-stu-id="9a999-136">Here are some advantages of using ExpressRoute for Azure-based cloud services:</span></span>
  
- <span data-ttu-id="9a999-p106">**Rendimiento predecible:** con una ruta dedicada al perímetro de la nube de Microsoft, el rendimiento no está sujeto a las interrupciones del proveedor de Internet y tiene un pico en el tráfico de Internet. Puede determinar a los proveedores y responsabilizarlos con un acuerdo de nivel de servicio de rendimiento y latencia en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-p106">**Predictable performance:** With a dedicated path to the edge of the Microsoft cloud, your performance is not subject to Internet provider outages and spikes in Internet traffic. You can determine and hold your providers accountable to a throughput and latency SLA to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="9a999-p107">**Privacidad de los datos para el tráfico:** los usuarios malintencionados no podrán supervisar ni capturar o analizar paquetes del tráfico enviado a través de la conexión dedicada de ExpressRoute. Es tan seguro como usar vínculos WAN basados en Multiprotocol Label Switching (MPLS).</span><span class="sxs-lookup"><span data-stu-id="9a999-p107">**Data privacy for your traffic:** Traffic sent over your dedicated ExpressRoute connection is not subject to Internet monitoring or packet capture and analysis by malicious users. It is as secure as using Multiprotocol Label Switching (MPLS)-based WAN links.</span></span>
    
- <span data-ttu-id="9a999-141">**Conexiones de alto rendimiento:** gracias a la amplia compatibilidad con las conexiones de ExpressRoute, los proveedores de Exchange y los proveedores de servicios de red, podemos obtener un vínculo de hasta 10 Gbps a la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-141">**High throughput connections:** With wide support for ExpressRoute connections by exchange providers and network service providers, you can obtain up to a 10 Gbps link to the Microsoft cloud.</span></span>
    
- <span data-ttu-id="9a999-142">**Menor coste en algunas configuraciones:** aunque las conexiones de ExpressRoute suponen un coste adicional, en algunos casos una sola conexión de ExpressRoute puede costar menos que aumentar la capacidad de Internet en varias ubicaciones de la organización para proporcionar un rendimiento adecuado en los servicios en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-142">**Lower cost for some configurations:** Although ExpressRoute connections are an additional cost, in some cases a single ExpressRoute connection can cost less than increasing your Internet capacity at multiple locations of your organization to provide adequate throughput to Microsoft cloud services.</span></span>
    
<span data-ttu-id="9a999-p108">Una conexión de ExpressRoute no garantiza un mayor rendimiento en todas las configuraciones. Se puede obtener un rendimiento menor a través de una conexión de ExpressRoute de ancho de banda bajo que a través de una conexión a Internet de ancho de banda alto que esté a unos pocos saltos de un centro de datos regional de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-p108">An ExpressRoute connection is not a guarantee of higher performance in every configuration. It is possible to have lower performance over a low-bandwidth ExpressRoute connection than a high-bandwidth Internet connection that is only a few hops away from a regional Microsoft datacenter.</span></span>
  
<span data-ttu-id="9a999-145">Para conocer las recomendaciones más recientes para el uso de ExpressRoute con Office 365, consulte [Azure ExpressRoute para Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span><span class="sxs-lookup"><span data-stu-id="9a999-145">For the latest recommendations for using ExpressRoute with Office 365, see [ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).</span></span>
  
## <a name="expressroute-connectivity-models"></a><span data-ttu-id="9a999-146">Modelos de conectividad de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a999-146">ExpressRoute connectivity models</span></span>

<span data-ttu-id="9a999-147">La tabla 1 muestra los tres modelos de conectividad principales para las conexiones de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="9a999-147">Table 1 shows the three primary connectivity models for ExpressRoute connections.</span></span>
  
|<span data-ttu-id="9a999-148">**Colocalizado en un intercambio de nube**</span><span class="sxs-lookup"><span data-stu-id="9a999-148">**Co-located at a cloud exchange**</span></span>|<span data-ttu-id="9a999-149">**Ethernet de punto a punto**</span><span class="sxs-lookup"><span data-stu-id="9a999-149">**Point-to-point Ethernet**</span></span>|<span data-ttu-id="9a999-150">**Conexión (IP VPN) universal**</span><span class="sxs-lookup"><span data-stu-id="9a999-150">**Any-to-any (IP VPN) connection**</span></span>|
|:-----|:-----|:-----|
|![Modelo de conectividad de ExpressRoute: Colocalizado en un intercambio de nube](images/Network_Poster/ER_Conn1.png)|![Modelo de conectividad de ExpressRoute: Ethernet de punto a punto](images/Network_Poster/ER_Conn2.png)|![Modelo de conectividad de ExpressRoute: Conexión (IP VPN) universal](images/Network_Poster/ER_Conn3.png)|
|<span data-ttu-id="9a999-154">Si el centro de datos se encuentra colocalizado en instalaciones con un intercambio de nube, puede solicitar una conexión cruzada virtual a la nube de Microsoft a través del intercambio de Ethernet del proveedor de colocalización.</span><span class="sxs-lookup"><span data-stu-id="9a999-154">If your datacenter is co-located in a facility with a cloud exchange, you can order a virtual cross-connection to the Microsoft cloud through the co-location provider's Ethernet exchange.</span></span>  <br/> |<span data-ttu-id="9a999-155">Si el centro de datos se encuentra en sus instalaciones, puede usar un vínculo punto a punto de Ethernet para conectarse a la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-155">If your datacenter is located on your premises, you can use a point-to-point Ethernet link to connect to the Microsoft cloud.</span></span>  <br/> |<span data-ttu-id="9a999-156">Si ya usa un proveedor de IP VPN (MPLS) para conectar los sitios de la organización, una conexión de ExpressRoute a la nube de Microsoft actúa como otra ubicación en su WAN privada.</span><span class="sxs-lookup"><span data-stu-id="9a999-156">If you are already using an IP VPN (MPLS) provider to connect the sites of your organization, an ExpressRoute connection to the Microsoft cloud acts like another location on your private WAN.</span></span>  <br/> |
   
 <span data-ttu-id="9a999-157">**Tabla 1: Modelos de conectividad de ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="9a999-157">**Table 1: ExpressRoute connectivity models**</span></span>
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a><span data-ttu-id="9a999-158">Relaciones de emparejamiento de ExpressRoute a los servicios en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9a999-158">ExpressRoute peering relationships to Microsoft cloud services</span></span>

<span data-ttu-id="9a999-p109">Una única conexión de ExpressRoute admite hasta tres relaciones diferentes de emparejamiento de Border Gateway Protocol (BGP) a distintas partes de la nube de Microsoft. BPG usa relaciones de emparejamiento para establecer la confianza e intercambiar información de enrutamiento.</span><span class="sxs-lookup"><span data-stu-id="9a999-p109">A single ExpressRoute connection supports up to three different Border Gateway Protocol (BGP) peering relationships to different parts of the Microsoft cloud. BPG uses peering relationships to establish trust and exchange routing information.</span></span>
  
<span data-ttu-id="9a999-161">**Figura 3: Las tres relaciones BGP en una sola conexión de ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="9a999-161">**Figure 3: The three different BGP relationships in a single ExpressRoute connection**</span></span>

![Figura 3: Las tres relaciones BGP en una sola conexión de ExpressRoute](images/Network_Poster/ERPeering.png)
  
<span data-ttu-id="9a999-p110">La figura 3 muestra una conexión de ExpressRoute desde una red local. La conexión de ExpressRoute contiene tres relaciones lógicas de emparejamiento. Una relación de emparejamiento de Microsoft va a los servicios SaaS Microsoft, incluidos Office 365 y Dynamcs CRM Online. Una relación de emparejamiento pública va a los servicios de PaaS de Azure. Una relación de emparejamiento privada va a IaaS de Azure y a una puerta de enlace de red virtual que hospeda máquinas virtuales.</span><span class="sxs-lookup"><span data-stu-id="9a999-p110">Figure 3 shows an ExpressRoute connection from an on-premises network. The ExpressRoute connection contains three logical peering relationships. A Microsoft peering relationship goes to Microsoft SaaS services, including Office 365 and Dynamcs CRM Online. A public peering relationship goes to Azure PaaS services. A private peering relationship goes to Azure IaaS and to a virtual network gateway that hosts virtual machines.</span></span>
  
<span data-ttu-id="9a999-168">La relación de emparejamiento de BGP de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="9a999-168">The Microsoft peering BGP relationship:</span></span> 
  
- <span data-ttu-id="9a999-169">Va de un enrutador de la red perimetral a las direcciones públicas de los servicios de Office 365 y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="9a999-169">Is from a router in your DMZ to the public addresses of Office 365 and Dynamics 365 services.</span></span> 
    
- <span data-ttu-id="9a999-170">Admite la comunicación iniciada bidireccionalmente.</span><span class="sxs-lookup"><span data-stu-id="9a999-170">Supports bidirectional-initiated communication.</span></span>
    
<span data-ttu-id="9a999-171">La relación de emparejamiento pública de BGP:</span><span class="sxs-lookup"><span data-stu-id="9a999-171">The public peering BGP relationship:</span></span>
  
- <span data-ttu-id="9a999-172">Va de un enrutador de la red perimetral a las direcciones IP públicas de los servicios de Azure.</span><span class="sxs-lookup"><span data-stu-id="9a999-172">Is from a router in your DMZ to the public IP addresses of Azure services.</span></span>
    
- <span data-ttu-id="9a999-p111">Admite la comunicación iniciada unidireccionalmente solo desde sistemas locales. La relación de emparejamiento no admite comunicaciones iniciadas desde los servicios PaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="9a999-p111">Supports unidirectional-initiated communication from on-premises systems only. The peering relationship does not support communication initiated from Azure PaaS services.</span></span>
    
<span data-ttu-id="9a999-175">La relación de emparejamiento privada de BGP:</span><span class="sxs-lookup"><span data-stu-id="9a999-175">The private peering BGP relationship:</span></span>
  
- <span data-ttu-id="9a999-176">Va de un enrutador del perímetro de la red de su organización a las direcciones IP privadas asignadas a sus redes virtuales de Azure.</span><span class="sxs-lookup"><span data-stu-id="9a999-176">Is from a router on the edge of your organization network to the private IP addresses assigned to your Azure VNets.</span></span>
    
- <span data-ttu-id="9a999-177">Admite la comunicación iniciada bidireccionalmente.</span><span class="sxs-lookup"><span data-stu-id="9a999-177">Supports bidirectional-initiated communication.</span></span>
    
- <span data-ttu-id="9a999-178">Es una extensión de la red de su organización a la nube de Microsoft que incluye el direccionamiento y el enrutamiento internamente coherentes.</span><span class="sxs-lookup"><span data-stu-id="9a999-178">Is an extension of your organization network to the Microsoft cloud, complete with internally-consistent addressing and routing.</span></span>
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a><span data-ttu-id="9a999-179">Ejemplo de la implementación de una aplicación y el flujo de tráfico con ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a999-179">Example of application deployment and traffic flow with ExpressRoute</span></span>

<span data-ttu-id="9a999-p112">El modo en que el tráfico viaja a través de las conexiones de ExpressRoute y dentro de la nube de Microsoft es una función de las rutas en los saltos de la ruta de acceso entre el origen, el destino y el comportamiento de la aplicación. En este ejemplo vemos una aplicación que se ejecuta en una máquina virtual de Azure que tiene acceso a una granja de SharePoint local a través de una conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="9a999-p112">How traffic travels across ExpressRoute connections and within the Microsoft cloud is a function of the routes at the hops of the path between the source and the destination and application behavior. Here is an example of an application running on an Azure virtual machine that accesses an on-premises SharePoint farm over a site-to-site VPN connection.</span></span>
  
<span data-ttu-id="9a999-182">**Figura 4: Una aplicación de una máquina virtual de Azure que obtiene acceso a una granja de SharePoint local**</span><span class="sxs-lookup"><span data-stu-id="9a999-182">**Figure 4: An application on an Azure virtual machine accessing an on-premises SharePoint farm**</span></span>

![Figura 4: Una aplicación de una máquina virtual de Azure que obtiene acceso a una granja de SharePoint local](images/Network_Poster/ER_App_Flow1.png)

  
<span data-ttu-id="9a999-184">La figura 4 muestra una granja de SharePoint local, una conexión VPN de sitio a sitio entre la red local y una red virtual en IaaS de Azure, un servidor de aplicaciones que se ejecuta como una máquina virtual de IaaS de Azure y el flujo de tráfico entre el servidor de aplicaciones y la granja de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9a999-184">Figure 4 shows an on-premises SharePoint farm, a site-to-site VPN connection between the on-premises network and a virtual network in Azure IaaS, an application server running as an Azure IaaS virtual machine, and the traffic flow between the application server and the SharePoint farm.</span></span>
  
<span data-ttu-id="9a999-185">La aplicación busca la dirección IP de la granja de SharePoint usando el DNS local y todo el tráfico atraviesa la conexión VPN de sitio a sitio.</span><span class="sxs-lookup"><span data-stu-id="9a999-185">The application locates the IP address of the SharePoint farm using the on-premises DNS and all traffic goes over the site-to-site VPN connection.</span></span>
  
<span data-ttu-id="9a999-186">Esta organización migró su granja de SharePoint local a SharePoint Online en Office 365 e implementó una conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="9a999-186">This organization migrated their on-premises SharePoint farm to SharePoint Online in Office 365 and deployed an ExpressRoute connection.</span></span>
  
<span data-ttu-id="9a999-187">**Figura 5: Traslado de la granja de SharePoint local a SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="9a999-187">**Figure 5: Moving the on-premises SharePoint farm to SharePoint Online**</span></span>

![Figura 5: Traslado de la granja de SharePoint local a SharePoint Online](images/Network_Poster/Hairpin1.png)
  
<span data-ttu-id="9a999-p113">La figura 5 muestra la adición de una conexión de ExpressRoute con relaciones de emparejamiento a los servicios SaaS de Microsoft, a Office 365 y a los servicios IaaS de Azure que contienen el servidor de aplicaciones en una red virtual. La granja local de SharePoint se migró a Office 365.</span><span class="sxs-lookup"><span data-stu-id="9a999-p113">Figure 5 shows the addition of an ExpressRoute connection with peering relationships to Microsoft SaaS and Office 365 and to Azure IaaS containing the application server on a virtual network. The SharePoint on-premises farm has been migrated to Office 365.</span></span>
  
<span data-ttu-id="9a999-191">Con las relaciones de emparejamiento privadas y de Microsoft:</span><span class="sxs-lookup"><span data-stu-id="9a999-191">With the Microsoft and private peering relationships:</span></span>
  
- <span data-ttu-id="9a999-192">Desde la puerta de enlace de red virtual de Azure, hay disponibles ubicaciones locales en la conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="9a999-192">From the Azure virtual network gateway, on-premises locations are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="9a999-193">Desde la suscripción a Office 365, las direcciones IP públicas de dispositivos perimetrales, como servidores proxy, están disponibles en la conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="9a999-193">From the Office 365 subscription, public IP addresses of edge devices, such as proxy servers, are available across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="9a999-194">Desde el perímetro de la red local, las direcciones IP privadas de la red virtual de Azure y las direcciones IP públicas de Office 365 están disponibles en la conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="9a999-194">From the on-premises network edge, the private IP addresses of the Azure VNet and the public IP addresses of Office 365 are available across the ExpressRoute connection.</span></span>
    
<span data-ttu-id="9a999-195">Cuando la aplicación tiene acceso a las direcciones URL de SharePoint Online, reenvía el tráfico a través de la conexión de ExpressRoute a un servidor proxy del perímetro.</span><span class="sxs-lookup"><span data-stu-id="9a999-195">When the application accesses the URLs of SharePoint Online, it forwards its traffic across the ExpressRoute connection to a proxy server in the edge.</span></span> 
  
<span data-ttu-id="9a999-p114">Cuando el servidor proxy busca la dirección IP de SharePoint Online, reenvía el tráfico de vuelta a través de la conexión de ExpressRoute. El tráfico de respuesta recorre la ruta inversa.</span><span class="sxs-lookup"><span data-stu-id="9a999-p114">When the proxy server locates the IP address of SharePoint Online, it forwards the traffic back over the ExpressRoute connection. Response traffic travels the reverse path.</span></span>
  
<span data-ttu-id="9a999-198">**Figura 6: Flujo de tráfico cuando se migra la granja de SharePoint a SharePoint Online en Office 365**</span><span class="sxs-lookup"><span data-stu-id="9a999-198">**Figure 6: Traffic flow when the SharePoint farm has been migrated to SharePoint Online in Office 365**</span></span>

![Figura 6: Flujo de tráfico cuando se migra la granja de SharePoint a SharePoint Online en Office 365](images/Network_Poster/Hairpin2.png)

  
<span data-ttu-id="9a999-200">La figura 6 muestra cómo fluye el tráfico entre el servidor de aplicaciones y SharePoint Online en Office 365 a través de la relación de emparejamiento privada del servidor de aplicaciones al perímetro de la red local y después del perímetro a Office 365 a través de la relación de emparejamiento de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-200">Figure 6 shows how the traffic between the application server and SharePoint Online in Office 365 flows over the private peering relationship from the application server to the on-premises network edge, and then from the edge over the Microsoft peering relationship to Office 365.</span></span>
  
<span data-ttu-id="9a999-201">El resultado es una redirección al origen, consecuencia del comportamiento de la aplicación y el enrutamiento.</span><span class="sxs-lookup"><span data-stu-id="9a999-201">The result is hair pinning, a consequence of the routing and application behavior.</span></span>
  
## <a name="expressroute-and-microsofts-cloud-network"></a><span data-ttu-id="9a999-202">Red de nube de Microsoft y de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a999-202">ExpressRoute and Microsoft's cloud network</span></span>

<span data-ttu-id="9a999-203">Las conexiones de ExpressRoute están disponibles en dos versiones: ExpressRoute y ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="9a999-203">ExpressRoute connections are available in two different versions: ExpressRoute and ExpressRoute Premium.</span></span>
  
### <a name="expressroute"></a><span data-ttu-id="9a999-204">ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a999-204">ExpressRoute</span></span>

<span data-ttu-id="9a999-205">El modo en que el tráfico fluye entre la red de su organización y un centro de datos de Microsoft es una combinación de:</span><span class="sxs-lookup"><span data-stu-id="9a999-205">How traffic travels between your organization network and a Microsoft datacenter is a combination of:</span></span>
  
- <span data-ttu-id="9a999-206">Sus ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="9a999-206">Your locations.</span></span>
    
- <span data-ttu-id="9a999-207">Las ubicaciones de emparejamiento en la nube de Microsoft (las ubicaciones físicas para conectarse al perímetro de Microsoft).</span><span class="sxs-lookup"><span data-stu-id="9a999-207">Microsoft cloud peering locations (the physical locations to connect to the Microsoft edge).</span></span>
    
- <span data-ttu-id="9a999-208">Las ubicaciones de los centros de datos de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-208">Microsoft datacenter locations.</span></span>
    
<span data-ttu-id="9a999-209">Las ubicaciones de los centros de datos de Microsoft y las de emparejamiento en la nube están conectadas a la red en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-209">Microsoft datacenter and cloud peering locations are all connected to the Microsoft cloud network.</span></span>
  
<span data-ttu-id="9a999-p115">Cuando se crea una conexión de ExpressRoute a una ubicación de emparejamiento en la nube de Microsoft, nos conectamos a la red en la nube de Microsoft y a todas las ubicaciones de centros de datos de Microsoft que hay en el mismo continente. El tráfico entre la ubicación de emparejamiento en la nube y el centro de datos de Microsoft de destino se realiza a través de la red en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-p115">When you create an ExpressRoute connection to a Microsoft cloud peering location, you are connected to the Microsoft cloud network and all the Microsoft datacenter locations in the same continent. The traffic between the cloud peering location and the destination Microsoft datacenter is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="9a999-212">Esto puede hacer que la entrega en los centros de datos locales de Microsoft no sea óptima para el modelo de conectividad universal.</span><span class="sxs-lookup"><span data-stu-id="9a999-212">This can result in non-optimal delivery to local Microsoft datacenters for the any-to-any connectivity model.</span></span>
  
<span data-ttu-id="9a999-213">**Figura 7: Ejemplo de una organización distribuida geográficamente que usa una sola conexión de ExpressRoute**</span><span class="sxs-lookup"><span data-stu-id="9a999-213">**Figure 7: Example of an geographically-distributed organization that uses a single ExpressRoute connection**</span></span>

![Figura 7: Ejemplo de una organización distribuida geográficamente que usa una sola conexión de ExpressRoute](images/Network_Poster/MSNet1.png)
  
<span data-ttu-id="9a999-p116">La figura 7 muestra una organización con dos ubicaciones, la ubicación 1 en el noroeste de Estados Unidos y la ubicación 2 en el noreste. Están conectados por un proveedor WAN universal. Esta organización tiene también una conexión de ExpressRoute a una ubicación de emparejamiento de Microsoft de la costa oeste. El tráfico de la ubicación 2 en el noreste destinado a un centro de datos de la costa este debe atravesar toda la red WAN de la organización hasta llegar a la costa oeste, a la ubicación de emparejamiento de Microsoft, y luego volver a recorrer todo el país por la red en la nube de Microsoft hasta llegar al centro de datos de la costa este.</span><span class="sxs-lookup"><span data-stu-id="9a999-p116">Figure 7 shows an organization with two locations, Location 1 in the northwest of the United States and Location 2 in the northeast. They are connected by an any-to-any WAN provider. This organization also has an ExpressRoute connection to a Microsoft peering location on the west coast. Traffic from Location 2 in the northeast destined for an east coast datacenter must travel all the way across the organization's WAN to the west coast, to the Microsoft peering location, and then back across the country over the Microsoft cloud network to the east coast datacenter.</span></span>
  
<span data-ttu-id="9a999-219">Para lograr una entrega óptima, use varias conexiones de ExpressRoute a ubicaciones regionales de emparejamiento en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-219">For optimal delivery, use multiple ExpressRoute connections to regional Microsoft cloud peering locations.</span></span> 
  
<span data-ttu-id="9a999-220">**Figura 8: El uso de varias conexiones de ExpressRoute para la entrega óptima en centros de datos regionales**</span><span class="sxs-lookup"><span data-stu-id="9a999-220">**Figure 8: The use of multiple ExpressRoute connections for optimal delivery to regional datacenters**</span></span>

![Figura 8: El uso de varias conexiones de ExpressRoute para la entrega óptima en centros de datos regionales](images/Network_Poster/MSNet2.png)
  
<span data-ttu-id="9a999-p117">La figura 8 muestra la misma organización con dos conexiones de ExpressRoute, una para cada ubicación, a ubicaciones de emparejamiento de Microsoft locales de una región. En esta configuración, el tráfico de la ubicación 2 en el noreste destinado a un centro de datos de la costa este va directamente a una ubicación de emparejamiento de la costa este, a la red en la nube de Microsoft, y luego al centro de datos de la costa este.</span><span class="sxs-lookup"><span data-stu-id="9a999-p117">Figure 8 shows the same organization with two ExpressRoute connections, one for each location, to regionally local Microsoft peering locations. In this configuration, traffic from Location 2 in the northeast destined for an east coast datacenter goes directly to an east coast peering location, to the Microsoft cloud network, and then to the east coast datacenter.</span></span>
  
<span data-ttu-id="9a999-224">Varias conexiones de ExpressRoute pueden proporcionar:</span><span class="sxs-lookup"><span data-stu-id="9a999-224">Multiple ExpressRoute connections can provide:</span></span>
  
- <span data-ttu-id="9a999-225">Mejor rendimiento a ubicaciones de centros de datos de Microsoft locales de una región.</span><span class="sxs-lookup"><span data-stu-id="9a999-225">Better performance to regionally local Microsoft datacenter locations.</span></span>
    
- <span data-ttu-id="9a999-226">Mayor disponibilidad en la nube de Microsoft cuando una conexión local de ExpressRoute deje de estar disponible.</span><span class="sxs-lookup"><span data-stu-id="9a999-226">Higher availability to the Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="9a999-p118">Esto funciona bien con las organizaciones que están en el mismo continente. Sin embargo, el tráfico a los centros de datos de Microsoft que están fuera del continente de la organización viaja a través de Internet.</span><span class="sxs-lookup"><span data-stu-id="9a999-p118">This works well for organizations in the same continent. However, traffic to Microsoft datacenters outside the organization's continent travels over the Internet.</span></span>
  
<span data-ttu-id="9a999-229">En el caso del tráfico intercontinental que va por la red en la nube de Microsoft, debe usar conexiones de ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="9a999-229">For intercontinental traffic over the Microsoft cloud network, you must use ExpressRoute Premium connections.</span></span>
  
### <a name="expressroute-premium"></a><span data-ttu-id="9a999-230">ExpressRoute Premium</span><span class="sxs-lookup"><span data-stu-id="9a999-230">ExpressRoute Premium</span></span>

<span data-ttu-id="9a999-231">En el caso de las organizaciones que se distribuyen globalmente en varios continentes, puede usar ExpressRoute Premium.</span><span class="sxs-lookup"><span data-stu-id="9a999-231">For organizations that are globally distributed across continents, you can use ExpressRoute Premium.</span></span> 
  
<span data-ttu-id="9a999-p119">Con ExpressRoute Premium, puede llegar a cualquier centro de datos de Microsoft de cualquier continente y desde cualquier ubicación de emparejamiento de Microsoft de cualquier continente. El tráfico entre continentes se transmite a través de la red en la nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-p119">With ExpressRoute Premium, you can reach any Microsoft datacenter on any continent from any Microsoft peering location on any continent. The traffic between continents is carried over the Microsoft cloud network.</span></span>
  
<span data-ttu-id="9a999-234">Con varias conexiones de ExpressRoute Premium, podemos conseguir:</span><span class="sxs-lookup"><span data-stu-id="9a999-234">With multiple ExpressRoute Premium connections, you can have:</span></span>
  
- <span data-ttu-id="9a999-235">Mejor rendimiento en centros de datos de Microsoft locales de un continente.</span><span class="sxs-lookup"><span data-stu-id="9a999-235">Better performance to continentally local Microsoft datacenters.</span></span>
    
- <span data-ttu-id="9a999-236">Mayor disponibilidad en la nube de Microsoft global cuando una conexión local de ExpressRoute deje de estar disponible.</span><span class="sxs-lookup"><span data-stu-id="9a999-236">Higher availability to the global Microsoft cloud when a local ExpressRoute connection becomes unavailable.</span></span>
    
<span data-ttu-id="9a999-p120">ExpressRoute Premium es necesario para las conexiones de ExpressRoute basadas en Office 365. Pero no supone un coste adicional para las empresas que tienen 500 usuarios con licencia o más.</span><span class="sxs-lookup"><span data-stu-id="9a999-p120">ExpressRoute Premium is required for Office 365-based ExpressRoute connections. However, there is no additional cost for enterprises with 500 or more licensed users.</span></span>
  
<span data-ttu-id="9a999-239">**Figura 9: La red mundial en la nube de Microsoft**</span><span class="sxs-lookup"><span data-stu-id="9a999-239">**Figure 9: The world-wide Microsoft cloud network**</span></span>

![Figura 9: La red mundial en la nube de Microsoft](images/Network_Poster/MSNet3.png)
  
<span data-ttu-id="9a999-p121">La figura 9 muestra un diagrama lógico de la red mundial en la nube de Microsoft, con redes que abarcan los continentes y las regiones del mundo y sus interconexiones. Cuando cada parte de la red en la nube de Microsoft está en un continente, una empresa global crea conexiones de ExpressRoute Premium desde sus oficinas concentradoras regionales a ubicaciones de emparejamiento de Microsoft locales.</span><span class="sxs-lookup"><span data-stu-id="9a999-p121">Figure 9 shows a logical diagram of the worldwide Microsoft cloud network, with networks that span the continents and regions of the world and their interconnections. With a portion of the Microsoft cloud network in each continent, a global enterprise creates ExpressRoute Premium connections from its regional hub offices to local Microsoft peering locations.</span></span>
  
<span data-ttu-id="9a999-243">En el caso de una oficina regional, el tráfico adecuado de Office 365 que va a:</span><span class="sxs-lookup"><span data-stu-id="9a999-243">For a regional office, appropriate Office 365 traffic to:</span></span>
  
- <span data-ttu-id="9a999-244">Centros de datos de Office 365 continentales viaja a través de la red en la nube de Microsoft dentro del continente.</span><span class="sxs-lookup"><span data-stu-id="9a999-244">Continental Office 365 datacenters travels over the Microsoft cloud network within the continent.</span></span>
    
- <span data-ttu-id="9a999-245">Centros de datos de Office 365 en otro continente viaja a través de la red intercontinental en nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9a999-245">Office 365 datacenters in another continent travels over the intercontinental Microsoft cloud network.</span></span>
    
<span data-ttu-id="9a999-246">Para más información, visite:</span><span class="sxs-lookup"><span data-stu-id="9a999-246">For more information, see:</span></span>
  
- [<span data-ttu-id="9a999-247">Aprendizaje de Azure ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="9a999-247">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="9a999-248">Planear la red y ajustar el rendimiento de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a999-248">Network planning and performance tuning for Office 365</span></span>](https://aka.ms/tune)
    
- [<span data-ttu-id="9a999-249">Administración del rendimiento de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a999-249">Office 365 Performance Management</span></span>](https://mva.microsoft.com/es-ES/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a><span data-ttu-id="9a999-250">Opciones de ExpressRoute</span><span class="sxs-lookup"><span data-stu-id="9a999-250">ExpressRoute options</span></span>

<span data-ttu-id="9a999-251">También puede incorporar las opciones siguientes a la implementación de ExpressRoute:</span><span class="sxs-lookup"><span data-stu-id="9a999-251">You can also incorporate the following options into your ExpressRoute deployment:</span></span>
  
- <span data-ttu-id="9a999-252">**Seguridad en el perímetro:** para proporcionar seguridad avanzada en el tráfico enviado y recibido a través de la conexión de ExpressRoute, como la inspección del tráfico o la detección de intrusiones y malware, coloque las aplicaciones de seguridad en la ruta de acceso del tráfico dentro de la red perimetral o en el perímetro de la intranet.</span><span class="sxs-lookup"><span data-stu-id="9a999-252">**Security at your edge:** To provide advanced security for the traffic sent and received over the ExpressRoute connection, such as traffic inspection or intrusion/malware detection, place your security appliances in the traffic path within your DMZ or at the border of your intranet.</span></span>
    
    <span data-ttu-id="9a999-p122">Tráfico de Internet para máquinas virtuales: para impedir que las máquinas virtuales de Azure inicien el tráfico directamente con ubicaciones de Internet, anuncie la ruta predeterminada a Microsoft. El tráfico de Internet se enruta a través de la conexión de ExpressRoute y a través de los servidores proxy locales. El tráfico de las máquinas virtuales de Azure a los servicios PaaS de Azure o a Office 365 se vuelve a enrutar a través de la conexión de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="9a999-p122">Internet traffic for VMs To prevent Azure VMs from initiating traffic directly with Internet locations, advertise the default route to Microsoft. Traffic to the Internet is routed across the ExpressRoute connection and through your on-premises proxy servers. Traffic from Azure VMs to Azure PaaS services or Office 365 is routed back across the ExpressRoute connection.</span></span>
    
- <span data-ttu-id="9a999-p123">**Optimizadores de WAN:** puede implementar optimizadores de WAN a ambos lados de una conexión de emparejamiento privada para una red virtual de Azure entre locales (VNet). Dentro de la VNet de Azure, use una aplicación de red del optimizador de WAN de Azure Marketplace y el enrutamiento definido por el usuario para enrutar el tráfico a través de la aplicación.</span><span class="sxs-lookup"><span data-stu-id="9a999-p123">**WAN optimizers:** You can deploy WAN optimizers on both sides of a private peering connection for a cross-premises Azure virtual network (VNet). Inside the Azure VNet, use a WAN optimizer network appliance from the Azure marketplace and user-defined routing to route the traffic through the appliance.</span></span>
    
- <span data-ttu-id="9a999-p124">**Calidad de servicio:** use valores de Punto de código de servicios diferenciados (DSCP) en el encabezado IPv4 del tráfico para marcarlo para voz, vídeo/interactivo o entrega de mejor esfuerzo. Esto es especialmente importante en la relación de emparejamiento de Microsoft y en el tráfico de Skype Empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="9a999-p124">**Quality of service:** Use Differentiated Services Code Point (DSCP) values in the IPv4 header of your traffic to mark it for voice, video/interactive, or best-effort delivery. This is especially important for the Microsoft peering relationship and Skype for Business Online traffic.</span></span>
    
<span data-ttu-id="9a999-260">Consulte estos recursos adicionales para obtener más información:</span><span class="sxs-lookup"><span data-stu-id="9a999-260">See these additional resources for more information:</span></span>
  
- [<span data-ttu-id="9a999-261">ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="9a999-261">ExpressRoute for Office 365</span></span>](https://aka.ms/expressrouteoffice365)
    
- [<span data-ttu-id="9a999-262">Aprendizaje de Azure ExpressRoute para Office 365</span><span class="sxs-lookup"><span data-stu-id="9a999-262">Azure ExpressRoute for Office 365 Training</span></span>](https://channel9.msdn.com/series/aer/)
    
- [<span data-ttu-id="9a999-263">ExpressRoute para Azure</span><span class="sxs-lookup"><span data-stu-id="9a999-263">ExpressRoute for Azure</span></span>](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a><span data-ttu-id="9a999-264">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="9a999-264">Next step</span></span>

[<span data-ttu-id="9a999-265">Diseño de redes para SaaS de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9a999-265">Designing networking for Microsoft SaaS</span></span>](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a><span data-ttu-id="9a999-266">Ver también</span><span class="sxs-lookup"><span data-stu-id="9a999-266">See also</span></span>

[<span data-ttu-id="9a999-267">Microsoft Cloud Networking para arquitectos profesionales</span><span class="sxs-lookup"><span data-stu-id="9a999-267">Microsoft Cloud Networking for Enterprise Architects</span></span>](microsoft-cloud-networking-for-enterprise-architects.md)
  
[<span data-ttu-id="9a999-268">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9a999-268">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="9a999-269">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="9a999-269">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



