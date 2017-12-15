---
title: "Diagrama accesible Integración de redes de productos de servidores de Microsoft Office"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 89f564eb-95c3-4077-bb92-75bf71b51270
description: "Este artículo es una versión de texto accesible del diagrama con el nombre Integración de red de los productos de servidor de Microsoft Office."
ms.openlocfilehash: 2ced3ae648d07ae00c66b8ede8562df66826e4a9
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---network-integration-of-microsoft-office-server-products"></a><span data-ttu-id="fe0a9-103">Diagrama accesible: Integración de redes de productos de servidores de Microsoft Office</span><span class="sxs-lookup"><span data-stu-id="fe0a9-103">Accessible diagram - Network Integration of Microsoft Office Server Products</span></span>

<span data-ttu-id="fe0a9-104">**Resumen:** Este artículo es una versión de texto accesible del diagrama con el nombre de red de Microsoft Office Server productos de integración.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-104">**Summary:** This article is an accessible text version of the diagram named Network Integration of Microsoft Office Server Products.</span></span>
  
<span data-ttu-id="fe0a9-p101">En este póster se describe de manera general un entorno de red que incluye Lync Server 2013, SharePoint 2013 y Exchange Server 2013. También se muestran los siguientes elementos de red comunes a dichos productos: acceso remoto e interno, autenticación, tráfico de cliente y enrutamiento de tráfico a través de dispositivos compartidos.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p101">This poster provides a general illustration of a network environment that includes Lync Server 2013, SharePoint 2013, and Exchange Server 2013. It also illustrates the following networking elements that are common across these products: remote and internal access, authentication, client traffic, and routing traffic through shared devices.</span></span> 
  
## <a name="high-level-concepts-for-lync-exchange-sharepoint-server-and-office-web-apps"></a><span data-ttu-id="fe0a9-107">Conceptos de alto nivel para Lync, Exchange, SharePoint Server y Office Web Apps</span><span class="sxs-lookup"><span data-stu-id="fe0a9-107">High-level concepts for Lync, Exchange, SharePoint Server, and Office Web Apps</span></span>

### <a name="about-the-design"></a><span data-ttu-id="fe0a9-108">Acerca del diseño</span><span class="sxs-lookup"><span data-stu-id="fe0a9-108">About the design</span></span>

#### <a name="streamlined-network-design"></a><span data-ttu-id="fe0a9-109">Diseño de red simplificado</span><span class="sxs-lookup"><span data-stu-id="fe0a9-109">Streamlined network design</span></span>

<span data-ttu-id="fe0a9-p102">Esta topología ilustra una implementación de la red local de SharePoint 2013, Exchange Server 2013 y Lync Server 2013. También muestra el uso del servicio basado en la nube de Microsoft, Exchange Online Protection, que proporciona protección contra correo no deseado y malware para el tráfico entrante del Protocolo simple de transferencia de correo (SMTP) de Internet.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p102">This topology illustrates an on-premises network deployment of SharePoint 2013, Exchange Server 2013, and Lync Server 2013. It also shows the use of the Microsoft cloud-based service, Exchange Online Protection, which provides spam and malware protection for inbound Simple Mail Transfer Protocol (SMTP) traffic from the Internet.</span></span> 
  
<span data-ttu-id="fe0a9-p103">El diseño de esta red se simplificó a un conjunto mínimo de características de red y no incluye características adicionales de seguridad o infraestructura que algunas organizaciones podrían requerir.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p103">This network design is streamlined to a minimum set of network features. The design does not take into account additional security or infrastructure features that some organizations might require.</span></span> 
  
<span data-ttu-id="fe0a9-114">Este diagrama:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-114">This diagram:</span></span> 
  
- <span data-ttu-id="fe0a9-115">Proporciona un ejemplo de topología de red que ilustra el tráfico entrante y saliente a través de un enrutador de puerta de enlace y el equilibrio de carga del tráfico (externo e interno) de sesiones de cliente a los niveles de servidor de SharePoint, Exchange y Lync adecuados.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-115">Provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers.</span></span> 
    
- <span data-ttu-id="fe0a9-116">Muestra el uso de servidores de acceso remoto opcionales, como una puerta de enlace VPN de terceros o un servidor de DirectAccess, para proporcionar comunicación segura para los empleados con movilidad o remotos.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-116">Shows the use of optional remote access servers, such as a third-party VPN gateway or DirectAccess server, to provide secure communication for roaming or remote employees.</span></span> 
    
- <span data-ttu-id="fe0a9-117">Describe el flujo de tráfico de Lync, Exchange y SharePoint desde el cliente a cada nivel de servidor de plataforma.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-117">Details the SharePoint, Exchange, and Lync traffic flow from the client to each platform server tier.</span></span> 
    
- <span data-ttu-id="fe0a9-118">Identifica el tipo de conexión de acceso remoto o interno basado en el cliente (asociado o empleado, por ejemplo) y el método de autenticación usado.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-118">Identifies the type of remote or internal access connection based on client (such as partner or employee), and the authentication method used.</span></span> 
    
- <span data-ttu-id="fe0a9-119">Divide las plataformas SharePoint, Exchange y Lync según los roles de servidor necesarios, identificando el front-end, la aplicación, la base de datos y otros niveles.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-119">Breaks down the SharePoint, Exchange, and Lync platforms by required server roles, identifying the front end, application, database, and other levels.</span></span> 
    
<span data-ttu-id="fe0a9-p104">La arquitectura que se usa aquí para Lync, SharePoint y Exchange no sugiere una forma de implementación preferente de estas plataformas. Únicamente es un ejemplo, dado que las topologías varían en función de consideraciones de seguridad y requisitos de red específicos.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p104">The architecture used here for SharePoint, Lync, and Exchange does not suggest a preferred way of implementing these platforms. It merely provides an example as topologies differ based on unique network requirements and security considerations.</span></span> 
  
#### <a name="gateway-router"></a><span data-ttu-id="fe0a9-122">Enrutador de puerta de enlace</span><span class="sxs-lookup"><span data-stu-id="fe0a9-122">Gateway router</span></span>

<span data-ttu-id="fe0a9-p105">Para esta topología, el enrutador de la puerta de enlace se encuentra en el perímetro de la red y enruta todo el tráfico entrante y saliente hacia y desde la intranet. Como alternativa, también puede haber otros componentes que eliminen la brecha entre el enrutador de la puerta de enlace y el equilibrador de carga que se muestra, por ejemplo, varias capas de firewall. Esta topología representa solo una manera entre muchas de implementar la red. En esta configuración, la puerta de enlace se configuró con listas de control de acceso (ACL) para permitir tráfico entrante y saliente muy específico y basado en IP en las interfaces del enrutador. También se puede ejecutar ACL, inspecciones avanzadas o traducción de direcciones de red (NAT) en otros dispositivos, como los firewall, en la red.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p105">For this topology, the gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet. Alternatively, there could also be other components that bridge the gap between the gateway router and the load balancer shown, such as multiple layers of firewalls. This topology represents just one way to deploy your network out of many. In this configuration, the gateway is configured with access control lists (ACLs) to permit very specific incoming and outgoing IP-based traffic on the router interfaces. ACLs, advanced inspection, or Network Address Translation (NAT) can also be performed on other devices, such as firewalls, throughout your network.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-devices"></a><span data-ttu-id="fe0a9-128">Equilibrador de carga y dispositivos de proxy inverso</span><span class="sxs-lookup"><span data-stu-id="fe0a9-128">Load balancer and reverse proxy devices</span></span>

<span data-ttu-id="fe0a9-p106">Puede usar soluciones de equilibrio de carga de hardware o software para redirigir el tráfico de segmentos, incluidos servidores front-end web de SharePoint y servidores de acceso de cliente de Exchange (CAS). En algunos casos, lo ideal es usar un equilibrador de carga basado en hardware de nivel 7 para los requisitos de persistencia ya que puede funcionar mejor gracias a que usa información, como cookies o encabezados, en la solicitud. Sin embargo, factores como el costo y un uso y cargas de trabajo mayores de este tipo de solución podrían no ser convenientes para sus necesidades específicas. Tenga en cuenta los siguientes aspectos sobre el equilibrio de carga entre SharePoint, Exchange y Lync:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p106">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). In some cases it's optimal to use a layer 7 hardware-based load balancer for persistence requirements as it can perform better by using information in the request, such as cookies or headers. However, factors like cost and increased utilization and workload from such a solution might not be desirable for your specific needs. Consider the following points for load balancing across SharePoint, Exchange, and Lync:</span></span> 
  
- <span data-ttu-id="fe0a9-p107">SharePoint: para SharePoint 2013, no es necesario habilitar la afinidad de los servidores front-end web. Normalmente, esta se usa para el mantenimiento de sesiones y para evitar varias solicitudes de autenticación de los clientes a cada servidor web front-end. El nuevo servicio de caché distribuida en SharePoint 2013 almacena y distribuye los tokens de inicio de sesión en los servidores web de la granja de servidores de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p107">SharePoint - For SharePoint 2013, you do not need to enable affinity for your front-end web servers. Normally, this would be used for creating sticky sessions and avoiding multiple authentication requests from clients to each front-end web server. The new Distributed Cache service in SharePoint 2013 stores and distributes logon tokens across the web servers of the SharePoint farm.</span></span> 
    
- <span data-ttu-id="fe0a9-p108">Exchange: en Exchange 2013, la función de CAS está diseñada para usar el equilibrio de carga de nivel 4, que distribuye las solicitudes a la capa de transporte. Esto puede reducir considerablemente el uso del equilibrador de carga y la carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p108">Exchange - In Exchange 2013, the CAS role is designed to use layer 4 load balancing, distributing requests at the transport layer. This can significantly decrease load balancer utilization and workload.</span></span> 
    
- <span data-ttu-id="fe0a9-p109">Lync: se recomienda usar el equilibrio de carga del Sistema de nombres de dominio (DNS) para el tráfico de protocolo de inicio de sesión (SIP) de granjas de servidores de Lync. El equilibrio de carga de hardware (HLB) es necesario para el tráfico de Lync Web (HTTPS).</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p109">Lync - Domain Name System (DNS) load balancing is recommended for Session Initiation Protocol (SIP) traffic for Lync pools. Hardware load balancing (HLB) is required for Lync Web (HTTPS) traffic.</span></span> 
    
### <a name="remote-access-options"></a><span data-ttu-id="fe0a9-140">Opciones de acceso remoto</span><span class="sxs-lookup"><span data-stu-id="fe0a9-140">Remote access options</span></span>

<span data-ttu-id="fe0a9-p110">Hay varias opciones que pueden publicar en Internet los recursos de la intranet para los asociados o proporcionar acceso remoto seguro a los empleados remotos o con movilidad. Estos ejemplos incluyen servidores proxy inversos, DirectAccess y puertas de enlace de VPN de terceros. Las soluciones de acceso remoto que se describen más adelante en esta sección son posibilidades para SharePoint, Lync y Exchange, o para cualquier combinación de estos servidores en una implementación local. Sin embargo, algunas opciones remotas podrían no funcionar con una solución concreta.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p110">There are several options that can publish intranet resources for partners on the Internet or provide secure remote access for remote or roaming employees. Such examples include reverse proxies, DirectAccess, and third-party VPN gateways. The remote access solutions discussed later in this section are possibilities for SharePoint, Lync, and Exchange, or any combination of these servers in an on-premises deployment. However, some remote options might not work with a particular solution.</span></span> 
  
<span data-ttu-id="fe0a9-p111">Proxy inverso: un proxy inverso admite el cifrado de tráfico, como la capa de sockets seguros (SSL), y con este puede publicar en Internet aplicaciones de intranet y recursos web para usuarios autenticados y asociados. Un ejemplo es Microsoft Forefront Unified Access Gateway (UAG). Muchos equilibradores de carga de hardware también admiten la funcionalidad de proxy inverso. Sin embargo, todavía hay escenarios válidos para el uso de una solución independiente con base en sus necesidades y requisitos, tales como optimización del rendimiento, compartimentación de seguridad y aislamiento de tráfico.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p111">Reverse Proxy - A reverse proxy supports traffic encryption, such as Secure Sockets Layer (SSL), and with it you can publish intranet applications and web resources to authenticated users and partners on the Internet. An example is Microsoft Forefront Unified Access Gateway (UAG). Many hardware load balancers also support reverse proxy functionality. However, there are still valid scenarios for using a standalone solution based on your needs and requirements, such as traffic isolation, security compartmentalization, and performance optimization.</span></span> 
  
<span data-ttu-id="fe0a9-149">Ventajas y consideraciones del proxy inverso:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-149">Reverse-proxy benefits and considerations:</span></span> 
  
- <span data-ttu-id="fe0a9-150">Proporciona acceso seguro y autenticado a los socios o usuarios que acceden a recursos de la intranet (usa SSL [TCP 443] entre el cliente y el servidor proxy inverso).</span><span class="sxs-lookup"><span data-stu-id="fe0a9-150">Provides authenticated and secured access for partners or users accessing intranet resources (uses SSL (TCP 443) between the client and reverse proxy server).</span></span> 
    
- <span data-ttu-id="fe0a9-p112">Para Exchange, una ventaja de usar un proxy inverso como Forefront UAG es la autenticación previa antes de acceder al servidor acceso de cliente de Exchange. Los usuarios de acceso remoto que usan aplicaciones publicadas como Outlook Web Access (OWA), pueden autenticar con los métodos básico, NTLM o Kerberos antes de acceder a la red interna.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p112">For Exchange, a benefit of using a reverse proxy such as Forefront UAG is pre-authentication before accessing the Exchange Client access server. Remote access users using published applications such as Outlook Web Access (OWA) can authenticate with the basic, NTLM, or Kerberos methods before they reach the internal network.</span></span> 
    
- <span data-ttu-id="fe0a9-153">Para Exchange y SharePoint, soluciones como Forefront UAG pueden terminar las conexiones SSL y disminuir la carga del servidor de recursos de la intranet y al mismo tiempo proporcionar un punto de administración único para los certificados.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-153">For Exchange and SharePoint, solutions like Forefront UAG can terminate SSL connections and decrease the load of the intranet resources server while providing a single point of management for certificates.</span></span> 
    
- <span data-ttu-id="fe0a9-p113">Para Lync, el tráfico de Web (HTTPS) atraviesa el proxy inverso (TCP 443) para la comunicación con el cliente. El proxy inverso retransmite la conexión HTTPS a los servicios de Lync Web, los CAS de Exchange y Office Web Apps. Lync Server 2013 no es compatible con UAG.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p113">For Lync, Web (HTTPS) traffic goes through the reverse proxy (TCP 443) for client communication. The reverse proxy proxies the HTTPS connection to Lync Web Services, Exchange CAS, and Office Web Apps. Lync Server 2013 does not support UAG.</span></span> 
    
<span data-ttu-id="fe0a9-p114">DirectAccess: tecnología de acceso remoto que se basa en el protocolo de seguridad de Internet (IPsec) para la autenticación y el cifrado de tráfico entre el servidor y el cliente de DirectAccess. DirectAccess proporciona acceso simultáneo a los recursos de Internet e intranet para los empleados remotos y con movilidad sin necesidad de iniciar una conexión.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p114">DirectAccess - A remote access technology that relies on Internet Protocol security (IPsec) for authentication and for encrypting traffic between the DirectAccess client and server. DirectAccess provides simultaneous access to both Internet and intranet resources for roaming and remote employees without having to initiate a connection.</span></span> 
  
<span data-ttu-id="fe0a9-159">Aspectos a considerar sobre DirectAccess:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-159">DirectAccess points to consider:</span></span> 
  
- <span data-ttu-id="fe0a9-160">DirectAccess usa tráfico protegido por IPsec (protocolo 50 y 51 y UDP 500) entre el servidor y el cliente de DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-160">DirectAccess uses IPsec protected traffic (protocol 50 and 51 and UDP 500) between the DirectAccess client and server.</span></span> 
    
- <span data-ttu-id="fe0a9-161">DirectAccess para Windows Server 2012 y Windows 8 no necesita una implementación de infraestructura de clave pública (PKI) para la autenticación de cliente y servidor.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-161">DirectAccess for Windows Server 2012 and Windows 8 does not need a public key infrastructure (PKI) deployment for server and client authentication.</span></span> 
    
- <span data-ttu-id="fe0a9-162">Se recomienda no usar DirectAccess con Lync Server 2013 debido a problemas de latencia de audio y vídeo asociados con el cifrado y descifrado de IPsec.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-162">We recommend against using DirectAccess with Lync Server 2013 because of audio and video latency issues associated with IPsec encryption and decryption.</span></span> 
    
    <span data-ttu-id="fe0a9-p115">Puerta de enlace de VPN: las puertas de enlace de VPN típicas proporcionan una conexión de acceso remoto en la que el equipo de un cliente de acceso remoto se proyecta de forma lógica a la intranet a través de una conexión de túnel iniciada por el usuario. Puede usar el acceso remoto unificado de Windows Server 2012 o varias soluciones de terceros para proporcionar acceso seguro a la intranet para los empleados con movilidad o remotos. La opción de VPN no se recomienda para Lync. El tráfico remoto de Lync debe usar servidores perimetrales y el túnel dividido.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p115">VPN Gateway - Typical VPN gateways provide a remote access connection in which a remote access client computer is logically projected onto the intranet through a tunneled and user-initiated connection. You can use Unified Remote Access in Windows Server 2012 or several third-party solutions to provide secured access to the intranet for roaming or remote employees. VPN is not recommended for Lync. Remote Lync traffic should use the Edge Servers and split tunneling.</span></span> 
    
### <a name="domain-name-system-dns-considerations"></a><span data-ttu-id="fe0a9-167">Consideraciones sobre el Sistema de nombres de dominio (DNS)</span><span class="sxs-lookup"><span data-stu-id="fe0a9-167">Domain Name System (DNS) considerations</span></span>

<span data-ttu-id="fe0a9-168">Necesitará elaborar un plan para el conjunto de registros DNS que permiten a los usuarios de Internet e intranet resolver nombres DNS para las direcciones IP adecuadas.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-168">You need to plan for the set of DNS records that allow both Internet and intranet users to resolve DNS names to the appropriate IP addresses.</span></span> 
  
- <span data-ttu-id="fe0a9-169">Para los asociados basados en Internet y los empleados con movilidad o remotos, los registros DNS registrados con servidores DNS de Internet proporcionan una resolución para el conjunto de direcciones IP públicas correspondientes al enrutador de la puerta de enlace, el servidor perimetral de Lync, el conjunto de direcciones IP virtuales (VIP) en el equilibrador de carga, y la puerta de enlace VPN o DirectAccess según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-169">For Internet-based partners and roaming or remote employees, DNS records registered with Internet DNS servers provide resolution to the set of public IP addresses corresponding to the gateway router, the Lync Edge Server, the set of virtual IP addresses (VIPs) on the load balancer, and the DirectAccess or VPN gateway as needed.</span></span> 
    
- <span data-ttu-id="fe0a9-170">Para los usuarios de la intranet, los registros DNS registrados con servidores DNS de la intranet proporcionan una resolución para el conjunto de direcciones IP virtuales (VIP) en el equilibrador de carga para el acceso a los recursos de Exchange, SharePoint y Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-170">For intranet-based users, DNS records registered with intranet DNS servers provide resolution to the set of virtual IP addresses (VIPs) on the load balancer for access to SharePoint, Lync, and Exchange resources.</span></span> 
    
- <span data-ttu-id="fe0a9-p116">Los clientes de DirectAccess usan servidores DNS de la intranet para los nombres que corresponden al espacio de nombres DNS de intranet y los servidores DNS de Internet para los demás nombres. Para simplificar la operación de DirectAccess, considere el uso de una implementación dividida de DNS que use distintos espacios de nombres DNS para los nombres basados en Internet y de intranet. Por ejemplo, use contoso.com para el espacio de nombres de Internet y corp.contoso.com para el espacio de nombres de intranet.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p116">DirectAccess clients use intranet DNS servers for names corresponding to the intranet DNS name space and Internet DNS servers for names that do not. To simplify the operation of DirectAccess, consider the use of a split DNS implementation that uses different DNS namespaces for intranet and Internet-based names. For example, use contoso.com for Internet namespace and corp.contoso.com for the intranet namespace.</span></span> 
    
- <span data-ttu-id="fe0a9-p117">Exchange usa un modelo de DNS dividido donde el host de resolución de direcciones IP es diferente para el tráfico enrutado públicamente y para el tráfico de la red corporativa. Como mínimo, necesitará tener registros DNS para OWA, el servicio de detección automática, las direcciones URL de ActiveSync para el tráfico del cliente y un registro MX para el correo entrante.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p117">Exchange uses a split DNS model where host to IP resolution differs on publicly routed traffic from that on the corporate network. At a minimum, you need to have DNS records for OWA, Autodiscover, ActiveSync URLs for client traffic, and an MX record for inbound mail.</span></span> 
    
- <span data-ttu-id="fe0a9-176">Si está utilizando Exchange Online Protection (EOP), el registro MX señala a ese servicio en lugar de la granja de servidores de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-176">If you are using Exchange Online Protection (EOP), your MX record points to that service instead of your Exchange farm.</span></span> 
    
- <span data-ttu-id="fe0a9-177">Para Exchange, necesitará un registro TXT de prueba de propiedad en el DNS público y un identificador de la organización de federación para configurar el uso compartido federado.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-177">For Exchange, you need a proof of ownership TXT record in your public DNS, and a Federation Org ID to set up federated sharing.</span></span> 
    
- <span data-ttu-id="fe0a9-178">Los clientes de VPN de acceso remoto se pueden configurar para usar únicamente servidores DNS de la intranet cuando la conexión VPN de acceso remoto esté activa.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-178">Remote access VPN clients can be configured to use only intranet DNS servers when the remote access VPN connection is active.</span></span> 
    
### <a name="diagram-description"></a><span data-ttu-id="fe0a9-179">Descripción del diagrama</span><span class="sxs-lookup"><span data-stu-id="fe0a9-179">Diagram Description</span></span>

<span data-ttu-id="fe0a9-p118">Este diagrama proporciona un ejemplo de topología de red que ilustra el tráfico entrante y saliente a través de un enrutador de puerta de enlace y el equilibrio de carga del tráfico (externo e interno) de sesiones de cliente a los niveles de servidor de SharePoint, Exchange y Lync adecuados. La descripción de este diagrama se divide en dos partes:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p118">This diagram provides an example network topology illustrating inbound and outbound traffic through a gateway router and load balancing of client session traffic (external and internal) to the appropriate SharePoint, Exchange, and Lync server tiers. The description of this diagram is divided into two parts:</span></span> 
  
- <span data-ttu-id="fe0a9-182">Descripción de componentes mostrados en el diagrama</span><span class="sxs-lookup"><span data-stu-id="fe0a9-182">Description of components shown in the diagram</span></span> 
    
- <span data-ttu-id="fe0a9-183">Descripción de cómo se mueve el tráfico a través de los componentes a los niveles de servidor de SharePoint, Exchange, Lync y Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-183">Description of how traffic moves through the components to the SharePoint, Exchange, Lync, and Office Web Apps server tiers.</span></span> 
    
#### <a name="description-of-components-shown-in-the-diagram"></a><span data-ttu-id="fe0a9-184">Descripción de componentes mostrados en el diagrama</span><span class="sxs-lookup"><span data-stu-id="fe0a9-184">Description of components shown in the diagram</span></span>

#### <a name="user-types"></a><span data-ttu-id="fe0a9-185">Tipos de usuario</span><span class="sxs-lookup"><span data-stu-id="fe0a9-185">User types</span></span>

<span data-ttu-id="fe0a9-186">Hay cuatro tipos de usuario diferentes, tres fuera de los servicios de red y de nube y uno interno, que incluyen:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-186">There are four different types of users, three outside the network and cloud services and one internal, which include:</span></span> 
  
- <span data-ttu-id="fe0a9-187">Empresas asociadas (negocio a negocio): externo</span><span class="sxs-lookup"><span data-stu-id="fe0a9-187">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="fe0a9-188">Asociados particulares (SharePoint y anónimo [Lync]): externo</span><span class="sxs-lookup"><span data-stu-id="fe0a9-188">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="fe0a9-189">Empleados remotos y con movilidad: externo</span><span class="sxs-lookup"><span data-stu-id="fe0a9-189">Roaming and remote employees-external</span></span> 
    
- <span data-ttu-id="fe0a9-190">Empleados internos</span><span class="sxs-lookup"><span data-stu-id="fe0a9-190">Internal employees</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="fe0a9-191">Tráfico de correo electrónico basado en la nube</span><span class="sxs-lookup"><span data-stu-id="fe0a9-191">Cloud-based email traffic</span></span>

<span data-ttu-id="fe0a9-192">Hay un componente basado en la nube para el tráfico de correo electrónico basado en SMTP: hosts de correo de Internet o Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-192">There is a cloud-based component for SMTP-based email traffic, either Internet Mail Hosts or Exchange Online Protection.</span></span> 
  
#### <a name="authentication-for-external-access"></a><span data-ttu-id="fe0a9-193">Autenticación para acceso externo</span><span class="sxs-lookup"><span data-stu-id="fe0a9-193">Authentication for external access</span></span>

<span data-ttu-id="fe0a9-p119">Hay un conjunto específico de procedimientos de autenticación para cada uno de los tipos de usuario de Exchange, SharePoint y Lync. Estos se describen con mayor detalle más adelante en este documento.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p119">There is a specific set of authentication procedures for Lync, SharePoint, and Exchange for each of the user types. They are described in more detail later in this document.</span></span> 
  
#### <a name="gateway-router-with-acls"></a><span data-ttu-id="fe0a9-196">Enrutador de puerta de enlace con ACL</span><span class="sxs-lookup"><span data-stu-id="fe0a9-196">Gateway router with ACLs</span></span>

<span data-ttu-id="fe0a9-197">El enrutador de la puerta de enlace se encuentra en el perímetro de la red y enruta todo el tráfico entrante y saliente hacia y desde la intranet.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-197">The gateway router sits at the edge of the network and routes all incoming and outgoing traffic to and from the intranet.</span></span> 
  
#### <a name="remote-access-servers-for-lync-and-sharepoint"></a><span data-ttu-id="fe0a9-198">Servidores de acceso remoto para Lync y SharePoint</span><span class="sxs-lookup"><span data-stu-id="fe0a9-198">Remote access servers for Lync and SharePoint</span></span>

<span data-ttu-id="fe0a9-199">Esta topología incluye un servidor perimetral de Lync y una puerta de enlace de VPN de SharePoint o un servidor de DirectAccess.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-199">This topology includes a Lync Edge server, and a SharePoint VPN gateway or DirectAccess server.</span></span> 
  
#### <a name="load-balancer-and-reverse-proxy-device"></a><span data-ttu-id="fe0a9-200">Equilibrador de carga y dispositivo de proxy inverso</span><span class="sxs-lookup"><span data-stu-id="fe0a9-200">Load balancer and reverse proxy device</span></span>

<span data-ttu-id="fe0a9-p120">Puede usar soluciones de equilibrio de carga de hardware o software para redirigir el tráfico de segmentos, incluidos servidores front-end web de SharePoint y servidores de acceso de cliente de Exchange (CAS). Esta topología muestra los componentes de direcciones IP virtuales de Lync, SharePoint y Exchange en el equilibrador de carga.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p120">You can use hardware or software load balancing solutions to redirect traffic for segments including SharePoint front-end web servers and Exchange Client Access Servers (CASs). This topology shows Lync VIP, SharePoint VIP, and Exchange VIP components in the load balancer.</span></span> 
  
#### <a name="servers"></a><span data-ttu-id="fe0a9-203">Servidores</span><span class="sxs-lookup"><span data-stu-id="fe0a9-203">Servers</span></span>

<span data-ttu-id="fe0a9-p121">Hay cuatro servidores: Lync, Exchange, SharePoint y Office Web Apps Server. Cada servidor puede tener tres niveles: un front-end, un nivel de acceso de cliente, una capa de aplicación y un nivel de base de datos o almacenamiento de información.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p121">There are four servers: Lync, SharePoint, Exchange, and Office Web Apps Server. Each server can have three tiers: a front-end, client-access tier, an application tier, and a database/storage tier.</span></span>
  
#### <a name="front-end-client-access-tier"></a><span data-ttu-id="fe0a9-206">Nivel de acceso de cliente front-end</span><span class="sxs-lookup"><span data-stu-id="fe0a9-206">Front-end, client-access tier</span></span>

<span data-ttu-id="fe0a9-207">Este nivel tiene componentes en los cuatro servidores:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-207">This tier has components on all four servers:</span></span> 
  
- <span data-ttu-id="fe0a9-p122">Granja de servidores de Lync (front-end). El diagrama muestra dos bases de datos de Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p122">Lync pool (front end). The diagram shows two Lync databases.</span></span> 
    
- <span data-ttu-id="fe0a9-p123">El servidor front-end de SharePoint y la caché distribuida. El diagrama muestra tres bases de datos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p123">SharePoint front end and distributed cache. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="fe0a9-p124">CAS de Exchange. El diagrama muestra dos bases de datos de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p124">Exchange CAS. The diagram shows two Exchange databases.</span></span> 
    
- <span data-ttu-id="fe0a9-p125">Office Web Apps Server. El diagrama muestra dos bases de datos de Office Web Apps.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p125">Office Web Apps Server. The diagram shows two Office Web Apps databases.</span></span> 
    
#### <a name="application-tier"></a><span data-ttu-id="fe0a9-216">Capa de aplicación</span><span class="sxs-lookup"><span data-stu-id="fe0a9-216">Application tier</span></span>

<span data-ttu-id="fe0a9-217">Esta capa tiene componentes únicamente en el servidor de SharePoint:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-217">This tier has components only on the SharePoint server:</span></span> 
  
- <span data-ttu-id="fe0a9-p126">Búsqueda (consulta, índice, administración). El diagrama muestra tres bases de datos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p126">Search (query, index, admin). The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="fe0a9-p127">Procesamiento por lotes. El diagrama muestra tres bases de datos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p127">Batch processing. The diagram shows three SharePoint databases.</span></span> 
    
#### <a name="databasestorage-tier"></a><span data-ttu-id="fe0a9-222">Nivel de base de datos y almacenamiento de información</span><span class="sxs-lookup"><span data-stu-id="fe0a9-222">Database/storage tier</span></span>

<span data-ttu-id="fe0a9-223">Este nivel tiene componentes en los servidores de Exchange, SharePoint y Lync:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-223">This tier has components on the Lync, SharePoint, and Exchange servers:</span></span> 
  
- <span data-ttu-id="fe0a9-p128">Base de datos de Lync (back-end). El diagrama muestra tres bases de datos de Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p128">Lync Database (backend). The diagram shows three Lync databases.</span></span> 
    
- <span data-ttu-id="fe0a9-p129">Base de datos de SharePoint El diagrama muestra tres bases de datos de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p129">SharePoint Database. The diagram shows three SharePoint databases.</span></span> 
    
- <span data-ttu-id="fe0a9-p130">Servidor de buzones de Exchange. El diagrama muestra dos servidores de buzones de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p130">Exchange Mailbox server. The diagram shows two Exchange Mailbox servers.</span></span> 
    
<span data-ttu-id="fe0a9-230">Para obtener más información sobre los componentes instalados en cada uno de los roles de servidor de SharePoint, consulte [Topologías simplificadas para SharePoint 2013](https://aka.ms/Ma5cgk).</span><span class="sxs-lookup"><span data-stu-id="fe0a9-230">For more information about components installed on each of the SharePoint server roles, see [Streamlined Topologies for SharePoint 2013](https://aka.ms/Ma5cgk).</span></span> 
  
#### <a name="description-of-how-traffic-moves-through-the-components-to-the-different-server-tiers"></a><span data-ttu-id="fe0a9-231">Descripción de cómo se mueve el tráfico a través de los componentes a los distintos niveles de servidor</span><span class="sxs-lookup"><span data-stu-id="fe0a9-231">Description of how traffic moves through the components to the different server tiers</span></span>

<span data-ttu-id="fe0a9-232">Esta sección describe cómo se mueven las solicitudes del usuario a través de la topología de red.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-232">This section describes how user requests move through the network topology.</span></span> 
  
#### <a name="authentication-and-routing-for-external-access"></a><span data-ttu-id="fe0a9-233">Autenticación y enrutamiento para acceso externo</span><span class="sxs-lookup"><span data-stu-id="fe0a9-233">Authentication and routing for external access</span></span>

<span data-ttu-id="fe0a9-234">Hay tres tipos de usuario diferentes fuera de los servicios de red y de nube, que incluyen:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-234">There are three different types of clients outside the network and cloud services, which include:</span></span> 
  
- <span data-ttu-id="fe0a9-235">Empresas asociadas (negocio a negocio): externo</span><span class="sxs-lookup"><span data-stu-id="fe0a9-235">Partner companies (business-to-business)-external</span></span> 
    
- <span data-ttu-id="fe0a9-236">Asociados particulares (SharePoint y anónimo [Lync]): externo</span><span class="sxs-lookup"><span data-stu-id="fe0a9-236">Individual partners (SharePoint and anonymous (Lync))-external</span></span> 
    
- <span data-ttu-id="fe0a9-237">Empleados remotos y con movilidad: externo</span><span class="sxs-lookup"><span data-stu-id="fe0a9-237">Roaming and remote employees-external</span></span> 
    
<span data-ttu-id="fe0a9-238">El proceso de autenticación y enrutamiento para cada tipo de usuario externo se describe de manera individual.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-238">The authentication and routing process for each external user type is described individually.</span></span> 
  
#### <a name="partner-companies-business-to-business-httpspartnerwebcontosocom"></a><span data-ttu-id="fe0a9-239">Empresas asociadas (negocio a negocio) (https://partnerweb.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="fe0a9-239">Partner companies (business-to-business) (https://partnerweb.contoso.com)</span></span>

- <span data-ttu-id="fe0a9-p131">Lync: confianza de federación con otras organizaciones, Skype y conectividad de mensajería instantánea pública (PIC) con AOL. El tráfico de federación de Lync pasa a través del enrutador de puerta de enlace al servidor perimetral de Lync, a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso) y después al servidor de Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p131">Lync: federation trust with other organizations, Skype and Public IM Connectivity (PIC) with AOL. The Lync federation traffic goes through the gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="fe0a9-p132">SharePoint: Proveedor de identidad de asociados de confianza con autenticación SAML. El tráfico de cliente de SharePoint pasa a través del enrutador de puerta de enlace a la dirección VIP de SharePoint (equilibrador de carga/servidor proxy inverso) y después al servidor de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p132">SharePoint: Trusted partner identity provider with SAML authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="fe0a9-p133">Exchange: Autenticación TLS mutua para el tráfico de correo, autenticación SAML para el uso compartido federado. El tráfico de cliente de Exchange pasa a través del enrutador de puerta de enlace a la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) y después al servidor de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p133">Exchange: Mutual Auth TLS for mail traffic, SAML authentication for Federated Sharing. The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="fe0a9-246">El tráfico de SMTP pasa a través del enrutador de puerta de enlace y de la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) al servidor de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-246">SMTP traffic goes through the Gateway router and through the Exchange VIP (load balancer/reverse proxy server) to the Exchange server.</span></span> 
    
#### <a name="individual-partners-sharepoint-and-anonymous-lync-httpspartnerwebcontosocom-and-httpsmeetcontosocom"></a><span data-ttu-id="fe0a9-247">Asociados particulares (SharePoint) y anónimos (Lync) (https://partnerweb.contoso.com y https://meet.contoso.com)</span><span class="sxs-lookup"><span data-stu-id="fe0a9-247">Individual partners (SharePoint) and anonymous (Lync) (https://partnerweb.contoso.com and https://meet.contoso.com)</span></span>

- <span data-ttu-id="fe0a9-p134">Lync: los usuarios anónimos solo pueden unirse a reuniones de Lync organizadas por los empleados. El tráfico de federación de Lync pasa a través del enrutador de puerta de enlace al servidor perimetral de Lync, a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso) y después al servidor de Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p134">Lync: anonymous users can only join Lync meetings organized by employees. The Lync federation traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="fe0a9-p135">SharePoint: Proveedor de identidad de asociados de confianza con autenticación SAML o autenticación basada en formularios. El tráfico de cliente de SharePoint pasa a través del enrutador de puerta de enlace a la dirección VIP de SharePoint (equilibrador de carga/servidor proxy inverso) y después al servidor de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p135">SharePoint: Trusted partner identity provider with SAML authentication or forms-based authentication. The SharePoint client traffic goes through the Gateway router to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="fe0a9-252">Exchange: no aplica.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-252">Exchange: Does not apply.</span></span> 
    
- <span data-ttu-id="fe0a9-253">El tráfico de Lync Web pasa a través del enrutador de puerta de enlace al servidor perimetral de Lync, a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso), a un equilibrador de carga de hardware, que se requiere para el tráfico HTTPS, y después al servidor de Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-253">Lync Web traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="roaming-and-remote-employees"></a><span data-ttu-id="fe0a9-254">Empleados remotos y con movilidad</span><span class="sxs-lookup"><span data-stu-id="fe0a9-254">Roaming and remote employees</span></span>

1. <span data-ttu-id="fe0a9-255">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-255">https://intranet.contoso.com</span></span> 
    
2. <span data-ttu-id="fe0a9-256">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-256">https://teams.contoso.com</span></span> 
    
3. <span data-ttu-id="fe0a9-257">https://my.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-257">https://my.contoso.com</span></span>
    
4. <span data-ttu-id="fe0a9-258">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-258">https://partnerweb.contoso.com</span></span> 
    
5. <span data-ttu-id="fe0a9-259">https://mail.contoso.com*</span><span class="sxs-lookup"><span data-stu-id="fe0a9-259">https://mail.contoso.com*</span></span> 
    
6. <span data-ttu-id="fe0a9-260">https://dial.contoso.com*</span><span class="sxs-lookup"><span data-stu-id="fe0a9-260">https://dial.contoso.com*</span></span>
    
7. <span data-ttu-id="fe0a9-261">https://meet.contoso.com*</span><span class="sxs-lookup"><span data-stu-id="fe0a9-261">https://meet.contoso.com*</span></span>
    
* <span data-ttu-id="fe0a9-262">La dirección URL de Exchange consta de los siguientes directorios virtuales: Detección automática, ECP, EWS, Microsoft-Server-ActiveSync, OAB, OWA y PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-262">The Exchange URL has the following virtual directories: Autodiscover, ecp, EWS, Microsoft-Server-ActiveSync, OAB, owa, PowerShell</span></span> 
  
- <span data-ttu-id="fe0a9-p136">Lync: Autenticación TLS-DSK o NTLM. El tráfico de cliente de Lync pasa a través del enrutador de puerta de enlace al servidor perimetral de Lync, a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso) y después al servidor de Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p136">Lync: TLS-DSK or NTLM authentication. The Lync client traffic goes through the Gateway router to the Lync Edge Server, to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="fe0a9-p137">SharePoint: Servicios de dominio de Active Directory (AD DS), autenticación basada en formularios o autenticación SAML. El tráfico de cliente de SharePoint pasa a través de la puerta de enlace VPN o el servidor de DirectAccess a la dirección VIP de SharePoint (equilibrador de carga/servidor proxy inverso) y después al servidor de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p137">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes through the VPN gateway or the DirectAccess server to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint server.</span></span> 
    
- <span data-ttu-id="fe0a9-p138">Exchange: Autenticación básica mediante SSL (ActiveSync, detección automática) y autenticación basada en formularios (OWA). El tráfico de cliente de Exchange pasa a través del enrutador de puerta de enlace a la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) y después al servidor de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p138">Exchange: Basic authentication over SSL (ActiveSync, Autodiscover), forms-based authentication (OWA). The Exchange client traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="fe0a9-269">El tráfico de cliente de Lync pasa a través del enrutador de puerta de enlace a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso), a un equilibrador de carga de hardware, que se requiere para el tráfico HTTPS, y después al servidor de Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-269">Lync client traffic goes through the Gateway router to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="authentication-for-internal-access"></a><span data-ttu-id="fe0a9-270">Autenticación para acceso interno</span><span class="sxs-lookup"><span data-stu-id="fe0a9-270">Authentication for internal access</span></span>

#### <a name="internal-employees"></a><span data-ttu-id="fe0a9-271">Empleados internos</span><span class="sxs-lookup"><span data-stu-id="fe0a9-271">Internal employees</span></span>

> <span data-ttu-id="fe0a9-272">https://intranet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-272">https://intranet.contoso.com</span></span> 
    
> <span data-ttu-id="fe0a9-273">https://teams.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-273">https://teams.contoso.com</span></span> 
    
> <span data-ttu-id="fe0a9-274">https://my.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-274">https://my.contoso.com</span></span>
    
> <span data-ttu-id="fe0a9-275">https://partnerweb.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-275">https://partnerweb.contoso.com</span></span>
    
> <span data-ttu-id="fe0a9-276">https://mail.contoso.com*</span><span class="sxs-lookup"><span data-stu-id="fe0a9-276">https://mail.contoso.com*</span></span> 
    
> <span data-ttu-id="fe0a9-277">https://dial.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-277">https://dial.contoso.com</span></span> 
    
> <span data-ttu-id="fe0a9-278">https://meet.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-278">https://meet.contoso.com</span></span>
    
> <span data-ttu-id="fe0a9-279">https://admin.contoso.com</span><span class="sxs-lookup"><span data-stu-id="fe0a9-279">https://admin.contoso.com</span></span>
    
- <span data-ttu-id="fe0a9-p139">Lync: Autenticación mediante Kerberos, TLS-DSK o NTLM. El tráfico de cliente de Lync pasa a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso) y después al servidor de Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p139">Lync: Kerberos, TLS-DSK, or NTLM authentication. The Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server), and then to the Lync Server.</span></span> 
    
- <span data-ttu-id="fe0a9-p140">SharePoint: Servicios de dominio de Active Directory (AD DS), autenticación basada en formularios o autenticación SAML. El tráfico de cliente de SharePoint pasa a la dirección VIP de SharePoint (equilibrador de carga/servidor proxy inverso) y después al servidor de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p140">SharePoint: Active Directory Domain Services (AD DS), forms-based authentication, or SAML authentication. The SharePoint client traffic goes to the SharePoint VIP (load balancer/reverse proxy server), and then to the SharePoint Server.</span></span> 
    
- <span data-ttu-id="fe0a9-p141">Exchange: AD DS y autenticación basada en formularios. El tráfico de cliente de Exchange pasa a la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) y después al servidor de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p141">Exchange: AD DS, forms-based authentication. The Exchange client traffic goes to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
    
- <span data-ttu-id="fe0a9-286">El tráfico de cliente de Lync pasa a la dirección VIP de Lync (equilibrador de carga/servidor proxy inverso), a un equilibrador de carga de hardware, que se requiere para el tráfico HTTPS, y después al servidor de Lync.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-286">Lync client traffic goes to the Lync VIP (load balancer/reverse proxy server) to a hardware load balancer, which is required for HTTPS traffic, and then to the Lync Server.</span></span> 
    
#### <a name="cloud-based-email-traffic"></a><span data-ttu-id="fe0a9-287">Tráfico de correo electrónico basado en la nube</span><span class="sxs-lookup"><span data-stu-id="fe0a9-287">Cloud-based email traffic</span></span>

<span data-ttu-id="fe0a9-288">El componente basado en la nube para el tráfico de correo electrónico basado en SMTP consiste en hosts de correo de Internet o Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-288">The cloud-based component for SMTP-based email traffic consists of either Internet Mail Hosts or Exchange Online Protection.</span></span>
  
<span data-ttu-id="fe0a9-p142">Estos componentes mueven el tráfico de correo electrónico a través de la red mediante SMTP. El tráfico pasa a través del enrutador de puerta de enlace a la dirección VIP de Exchange (equilibrador de carga/servidor proxy inverso) y después al servidor de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p142">These components move email traffic over the network using SMTP. The traffic goes through the Gateway router to the Exchange VIP (load balancer/reverse proxy server), and then to the Exchange Server.</span></span> 
  
### <a name="network-traffic-legend"></a><span data-ttu-id="fe0a9-291">Leyenda de tráfico de red</span><span class="sxs-lookup"><span data-stu-id="fe0a9-291">Network traffic legend</span></span>

<span data-ttu-id="fe0a9-292">El cuadro de la leyenda muestra de forma gráfica (con líneas de diferentes colores) los distintos tipos de tráfico representados en el gráfico, de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-292">The legend box graphically shows the different types of traffic depicted on the graph in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="fe0a9-293">Línea verde: tráfico SIP de Lync</span><span class="sxs-lookup"><span data-stu-id="fe0a9-293">Green line: Lync SIP traffic</span></span> 
    
- <span data-ttu-id="fe0a9-294">Línea azul: tráfico de Lync Web</span><span class="sxs-lookup"><span data-stu-id="fe0a9-294">Blue line: Lync Web traffic</span></span> 
    
- <span data-ttu-id="fe0a9-295">Línea púrpura: Tráfico de cliente de SharePoint</span><span class="sxs-lookup"><span data-stu-id="fe0a9-295">Purple line: SharePoint client traffic</span></span> 
    
- <span data-ttu-id="fe0a9-296">Línea naranja: Tráfico de cliente de Exchange</span><span class="sxs-lookup"><span data-stu-id="fe0a9-296">Orange line: Exchange client traffic</span></span> 
    
- <span data-ttu-id="fe0a9-297">Línea gris: Tráfico del servidor de correo de Exchange entre Exchange locales y Exchange Online Protection.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-297">Gray line: Exchange Mail Server traffic between Exchange on-premises and Exchange Online Protection.</span></span> 
    
<span data-ttu-id="fe0a9-298">En el cuadro de la leyenda también se describen los distintos tipos de tráfico y los puertos usados.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-298">The different types of traffic and the ports that they use are also described in the legend box.</span></span> 
  
#### <a name="lync-sip-traffic-and-lync-web-traffic"></a><span data-ttu-id="fe0a9-299">Tráfico SIP de Lync y tráfico de Lync Web</span><span class="sxs-lookup"><span data-stu-id="fe0a9-299">Lync SIP traffic and Lync web traffic</span></span>

<span data-ttu-id="fe0a9-300">El servidor perimetral de Lync usa los siguientes puertos para la comunicación del usuario externo:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-300">The Lync Edge Server uses the following ports for external user communication:</span></span> 
  
- <span data-ttu-id="fe0a9-301">Tráfico de señalización/IM (SIP o SIMPLE): Puerto TCP 443 (abierto para el tráfico entrante)</span><span class="sxs-lookup"><span data-stu-id="fe0a9-301">Signaling/IM traffic (SIP/SIMPLE): TCP port 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="fe0a9-302">Tráfico de conferencias Web (PSOM): TCP 443 (abierto para el tráfico entrante)</span><span class="sxs-lookup"><span data-stu-id="fe0a9-302">Web conferencing traffic (PSOM): TCP 443 (open for inbound traffic)</span></span> 
    
- <span data-ttu-id="fe0a9-303">Tráfico de A/V (SRTP): TCP 443, UDP 3478 y TCP 50000-59999 (opcional) (abiertos para el tráfico entrante y saliente)</span><span class="sxs-lookup"><span data-stu-id="fe0a9-303">A/V traffic (SRTP): TCP 443, UDP 3478 and TCP 50000-59999 (optional) (open for inbound and outbound traffic)</span></span> 
    
<span data-ttu-id="fe0a9-304">El servidor perimetral de Lync usa los siguientes puertos para la comunicación con servicios de federación:</span><span class="sxs-lookup"><span data-stu-id="fe0a9-304">Lync Edge Server uses the following ports for federation communication:</span></span> 
  
- <span data-ttu-id="fe0a9-305">Puertos TCP 5061 (SIP), 5269 (XMPP) y 443 y puerto UDP 3478 (SRTP) (abiertos para el tráfico entrante y saliente)</span><span class="sxs-lookup"><span data-stu-id="fe0a9-305">TCP ports 5061 (SIP), 5269 (XMPP), 443 and UDP 3478 (SRTP) (open for inbound and outbound traffic)</span></span> 
    
#### <a name="sharepoint-client-traffic"></a><span data-ttu-id="fe0a9-306">Tráfico de cliente de SharePoint</span><span class="sxs-lookup"><span data-stu-id="fe0a9-306">SharePoint client traffic</span></span>

<span data-ttu-id="fe0a9-p143">SharePoint puede usar el puerto TCP 443 (SSL) para comunicaciones cifradas entre el cliente y el equilibrador de carga. Para el acceso externo desde Internet, este puerto debe abrirse para el tráfico entrante y saliente en el enrutador de la puerta de enlace (o firewall externo).</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p143">SharePoint can use TCP port 443 (SSL) for encrypted communication between the client and the load balancer. For external access from the Internet, this port needs to be opened for inbound and outbound traffic on the gateway router (or external firewall).</span></span> 
  
#### <a name="exchange-client-traffic-and-exchange-mail-server-traffic"></a><span data-ttu-id="fe0a9-309">Tráfico de cliente de Exchange y tráfico del servidor de correo de Exchange</span><span class="sxs-lookup"><span data-stu-id="fe0a9-309">Exchange client traffic and Exchange mail server traffic</span></span>

<span data-ttu-id="fe0a9-p144">Exchange usa el puerto TCP 25 (SMTP) para las comunicaciones de servidor a servidor. La mayor parte del tráfico de cliente (OWA, ActiveSync, detección automática, Outlook en cualquier lugar) se controla a través del puerto 443 (HTTPS). Si tiene clientes POP o IMAP, los puertos 110 (POP3), 995 (cifrado POP3), 143 (IMAP4), 993 (IMAP4 cifrados) y 587 (SMTP) también se usan para ofrecer compatibilidad a estos clientes.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p144">Exchange uses TCP port 25 (SMTP) for server-to-server communications. Most client traffic (OWA, ActiveSync, Autodiscover, Outlook Anywhere) is handled over port 443 (HTTPS). If you have POP or IMAP clients, ports 110 (POP3), 995 (encrypted POP3), 143 (IMAP4), 993 (encrypted IMAP4), and 587 (SMTP) are also used to support these clients.</span></span> 
  
#### <a name="more-on-lync-network-traffic"></a><span data-ttu-id="fe0a9-313">¿Desea conocer más sobre el tráfico de red de Lync?</span><span class="sxs-lookup"><span data-stu-id="fe0a9-313">More on Lync network traffic?</span></span>

<span data-ttu-id="fe0a9-p145">Infórmese de cómo Lync Server puede ayudar a su organización a proporcionar mensajería instantánea, conferencias web, uso compartido de aplicaciones y comunicación de voz. Para obtener más información, consulte el [Póster de cargas de trabajo de protocolos de Microsoft Lync Server 2013 ](https://aka.ms/G5jzjo).</span><span class="sxs-lookup"><span data-stu-id="fe0a9-p145">Learn how Lync Server can help your organization provide instant messaging, web conferencing, application sharing, and voice communication. For more information, see [Microsoft Lync Server 2013 Protocol Workloads Poster](https://aka.ms/G5jzjo).</span></span> 
  
<span data-ttu-id="fe0a9-316">El póster también incluye un código QR para tener acceso a esta información.</span><span class="sxs-lookup"><span data-stu-id="fe0a9-316">The poster also includes a QR code to access this information.</span></span> 
  

