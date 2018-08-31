---
title: Conectividad de clientes
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/6/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 4232abcf-4ae5-43aa-bfa1-9a078a99c78b
description: 'Resumen: explica de qué manera los equipos cliente se conectan con los inquilinos de Office 365, según la ubicación del equipo cliente y el centro de datos del inquilino de Office 365.'
ms.openlocfilehash: 9455147e70a391619e1602f2e36d9162ff2c0928
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223042"
---
# <a name="client-connectivity"></a><span data-ttu-id="85a39-103">Conectividad de clientes</span><span class="sxs-lookup"><span data-stu-id="85a39-103">Client connectivity</span></span>

 <span data-ttu-id="85a39-104">**Resumen:** explica de qué manera los equipos cliente se conectan con los inquilinos de Office 365, según la ubicación del equipo cliente y el centro de datos del inquilino de Office 365.</span><span class="sxs-lookup"><span data-stu-id="85a39-104">**Summary:** Explains how client computers connect to Office 365 tenants, depending on the location of the client computer and Office 365 tenant datacenter.</span></span>
  
<span data-ttu-id="85a39-p101">Office 365 reside en centros de datos Microsoft todo el mundo que ayudan a mantener el servicio de copia de seguridad y la ejecución incluso cuando hay un problema importante en una región, como un terremoto o un corte de alimentación. Cuando se conecta a su inquilino de Office 365, la conexión del cliente se dirigirá al centro de datos adecuado donde se hospeda el inquilino. Las reglas que determinan dónde se puede hospedar el inquilino se definen mediante el contrato de Microsoft. Las reglas que determinan cómo el cliente adquiere los datos desde esa ubicación de centro de datos dependen de la arquitectura del servicio que está utilizando.</span><span class="sxs-lookup"><span data-stu-id="85a39-p101">Office 365 resides in Microsoft datacenters around the world which help keep the service up and running even when there's a major problem in one region, such as an earthquake or a power outage. When you connect to your Office 365 tenant, the client connection will be directed to the appropriate datacenter where your tenant is being hosted. The rules that determine where your tenant can be hosted are defined by your agreement with Microsoft. The rules that determine how your client acquires the data from that datacenter location depend on the architecture of the service you're using.</span></span>
  
<span data-ttu-id="85a39-p102">Por ejemplo, cuando se inicia sesión en el portal de Office 365, está suela estar conectado al centro de datos más cercano al cliente y dirigido a continuación, en función del servicio que usar siguiente. Si iniciar el correo electrónico, la conexión inicial para mostrar la interfaz de usuario todavía puede venir desde el centro de datos más cercano, pero es posible que se abre una segunda conexión entre el centro de datos más cercano y el centro de datos donde se encuentra el inquilino de para mostrar lo que aparece en los mensajes de correo electrónico lea. Microsoft administra una de las redes de diez principales en el mundo resultante en conexiones increíblemente fast de centro de datos para datacenter fast.</span><span class="sxs-lookup"><span data-stu-id="85a39-p102">For example, when you log on to the Office 365 portal, you're usually connected to the closest datacenter to the client and then directed depending on the service you use next. If you launch email, the initial connection to display the UI may still come from the nearest datacenter, but a second connection might be opened between the nearest datacenter and the datacenter where your tenant is located to show you what's in the emails you read. Microsoft operates one of the top ten networks in the world resulting in incredibly fast datacenter-to-datacenter connections fast.</span></span>
  
<span data-ttu-id="85a39-112">Después de leer el artículo, es probable que comprenderá ¿por qué no proporcionamos [intervalos de direcciones IP y URL de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) por centro de datos, simplemente son demasiado conectadas entre sí y depende de otra para hacer que sea posible.</span><span class="sxs-lookup"><span data-stu-id="85a39-112">After you read the article, you'll likely understand why we don't provide [Office 365 URLs and IP address ranges](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2) per datacenter, they are simply too interconnected and reliant on each other to make that feasible.</span></span>
  
<span data-ttu-id="85a39-p103">Si está utilizando ExpressRoute de Azure para Office 365, en la mayoría de los casos la conectividad se vaya a través de una conexión privada a Office 365 en lugar de la conexión pública que se describen aquí. Los principios acerca de cómo los clientes se conectan continúan siendo exactos. Obtenga más información acerca de [ExpressRoute de Azure para Office 365](azure-expressroute.md).</span><span class="sxs-lookup"><span data-stu-id="85a39-p103">If you're using Azure ExpressRoute for Office 365, in most cases your connectivity will go over a private connection to Office 365 instead of the public connection described here. The principles about how clients connect are still accurate. Learn more about [Azure ExpressRoute for Office 365](azure-expressroute.md).</span></span>
  
<span data-ttu-id="85a39-116">Para obtener más profundidad en Skype para las solicitudes de red empresarial, lea el artículo de [calidad de los medios y el rendimiento de la conectividad de red en Skype para profesionales en línea](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span><span class="sxs-lookup"><span data-stu-id="85a39-116">For more depth on Skype for Business network requests, read the article [Media Quality and Network Connectivity Performance in Skype for Business Online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).</span></span>

||
|:-----|
| <span data-ttu-id="85a39-117">En este artículo forma parte de la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="85a39-117">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

> [!NOTE]
> <span data-ttu-id="85a39-p104">Echamos mucho cuidado para administrar los datos de cliente, por lo que es segura y privada en nuestros centros de datos. Se incluye información acerca de los pasos que se tomen para administrar la privacidad en el [Centro de confianza](https://go.microsoft.com/fwlink/?LinkID=397383).</span><span class="sxs-lookup"><span data-stu-id="85a39-p104">We take great care to manage customer data so it's secure and private in our datacenters. Details about the steps we take to manage privacy are included in the [Trust Center](https://go.microsoft.com/fwlink/?LinkID=397383).</span></span>
  
## <a name="connecting-to-the-nearest-datacenter"></a><span data-ttu-id="85a39-120">Conectar con el centro de datos más cercano</span><span class="sxs-lookup"><span data-stu-id="85a39-120">Connecting to the nearest datacenter</span></span>

<span data-ttu-id="85a39-p105">Éste es el tipo de conexión más comunes y se usa mediante el portal de Office 365 y Exchange Online. En esta situación, cuando los clientes intentan conectarse a Office 365, consulta DNS de su equipo determina la región del mundo que procede de su equipo y Office 365 redirige la solicitud al centro de datos más cercano.</span><span class="sxs-lookup"><span data-stu-id="85a39-p105">This is the most common type of connection, and it's used by both the Office 365 portal and Exchange Online. In this situation, when clients attempt to connect to Office 365, their computer's DNS query determines the region of the world their computer is coming from, and Office 365 redirects the request to the nearest datacenter.</span></span>
  
<span data-ttu-id="85a39-123">Las conexiones en el portal de detención en el centro de datos más cercano y el equipo cliente se presenta con información sobre el inquilino del cliente desde esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="85a39-123">Connections to the portal stop at the nearest datacenter, and the client computer is presented with information about the client's tenant from that location.</span></span>
  
<span data-ttu-id="85a39-p106">Exchange Online va un paso más allá. Una vez que el equipo cliente está conectado al centro de datos más cercano, un servidor de Exchange en ese centro de datos se conecta al centro de datos donde el inquilino es realmente encuentra tal como se ilustra en el *¿cómo esto trabajar sección* por debajo. Los servidores de Exchange Online en el centro de datos más cercano, a continuación, proxy de las solicitudes desde el equipo cliente en el servidor de buzón de correo. Esto acelera la experiencia para el equipo cliente desplazando el trabajo de recuperación de mensajes de correo electrónico y elementos de calendario a la red de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="85a39-p106">Exchange Online goes a step further. Once the client computer is connected to the nearest datacenter, an Exchange server in that datacenter connects to the datacenter where the tenant is actually located as illustrated in the  *How does this work section*  below. The Exchange Online servers in the nearest datacenter then proxy the requests from the client computer to the mailbox server. This speeds up the experience for the client computer by moving the heavy lifting of retrieving emails and calendar items to the Microsoft network.</span></span>
  
## <a name="how-does-this-work-for-standard-cloud-offerings"></a><span data-ttu-id="85a39-128">¿Cómo funciona esto para las ofertas de nube estándar?</span><span class="sxs-lookup"><span data-stu-id="85a39-128">How does this work for standard cloud offerings?</span></span>

<span data-ttu-id="85a39-p107">Este proceso de conexión es estándar para tráfico alto, las aplicaciones web de alto valor, como Office 365. En esta sección, se de esquema y se ilustran los pasos en el proceso. Cuando el equipo cliente no está en la misma región como el inquilino, busca mucho varían en función del servicio que el cliente se conecta a la conexión.</span><span class="sxs-lookup"><span data-stu-id="85a39-p107">This connection process is standard for high traffic, high value web applications like Office 365. In this section, we outline and illustrate the steps in the process. When the client computer is not in the same region as the tenant, the connection looks much different depending on the service the client is connecting to.</span></span>
  
 <span data-ttu-id="85a39-p108">Este diagrama ilustra a un cliente con una oferta estándar de Office 365 con un inquilino en Norteamérica. En este escenario, la persona que realiza la solicitud se haya desplazado a Europa y está usando Office 365 desde esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="85a39-p108">This diagram depicts a customer using a standard Office 365 offering with a tenant in North America. In this scenario, the person making the request has traveled to Europe and is using Office 365 from that location.</span></span>
  
1. <span data-ttu-id="85a39-134">El equipo cliente solicita a los servidores DNS locales para la dirección IP asociada con Office 365.</span><span class="sxs-lookup"><span data-stu-id="85a39-134">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="85a39-135">Los servidores DNS locales del equipo cliente solicitan a los servidores de DNS de Microsoft para la dirección IP asociada con Office 365.</span><span class="sxs-lookup"><span data-stu-id="85a39-135">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="85a39-136">Los servidores DNS de Microsoft devolución el nombre del servidor regional (basado en la ubicación de los servidores del cliente DNS) y el equipo cliente repite los pasos 1 y 2 para obtener la dirección IP del centro de datos de Office 365 regional.</span><span class="sxs-lookup"><span data-stu-id="85a39-136">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="85a39-137">El equipo cliente se conecta a la dirección IP del centro de datos regional.</span><span class="sxs-lookup"><span data-stu-id="85a39-137">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="85a39-138">Los servidores de Exchange Online establecen una conexión con el centro de datos activo donde reside el inquilino del cliente.</span><span class="sxs-lookup"><span data-stu-id="85a39-138">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Centro de datos regional más próximo](media/4ea108e9-a299-4e3d-b0d3-469b434ff899.png)
  
## <a name="how-does-this-work-for-sovereign-cloud-offerings"></a><span data-ttu-id="85a39-140">¿Cómo la nube este trabajo para soberanos a las ofertas?</span><span class="sxs-lookup"><span data-stu-id="85a39-140">How does this work for sovereign cloud offerings?</span></span>

<span data-ttu-id="85a39-p109">Esta conexión es ligeramente diferente para las ofertas de nube soberanos, como Office 365 operado por Vianet 21. Con el inquilino en una instancia soberano de Office 365, los servidores de Office 365 más cercanos que aceptarán conexiones del portal son los servidores dentro de la región soberano donde reside el inquilino. De forma similar, los clientes de acceso a SharePoint Online en nuestro soberanos en la nube o las ofertas estándares se dirigirán a los servidores front-end donde reside el inquilino. Vea conectar con el centro de datos activo que aparece a continuación.</span><span class="sxs-lookup"><span data-stu-id="85a39-p109">This connection is slightly different for sovereign cloud offerings such as Office 365 operated by 21 Vianet. With the tenant in a sovereign instance of Office 365, the nearest Office 365 servers that will accept portal connections are the servers within the sovereign region where the tenant resides. Similarly, customers accessing SharePoint Online in our sovereign cloud or standard offerings will be directed to front end servers where the tenant resides. See connecting to the active datacenter below.</span></span>
  
1. <span data-ttu-id="85a39-145">El equipo cliente solicita a los servidores DNS locales para la dirección IP asociada con Office 365.</span><span class="sxs-lookup"><span data-stu-id="85a39-145">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="85a39-146">Los servidores DNS locales del equipo cliente solicitan a los servidores de DNS de Microsoft para la dirección IP asociada con Office 365.</span><span class="sxs-lookup"><span data-stu-id="85a39-146">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="85a39-147">Los servidores DNS de Microsoft devolución el nombre del servidor regional (basado en la ubicación de los servidores del cliente DNS) y el equipo cliente repite los pasos 1 y 2 para obtener la dirección IP del centro de datos de Office 365 regional.</span><span class="sxs-lookup"><span data-stu-id="85a39-147">Microsoft's DNS servers return the regional server name (based on the location of the client's DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="85a39-148">El equipo cliente se conecta a la dirección IP del centro de datos regional.</span><span class="sxs-lookup"><span data-stu-id="85a39-148">The client computer connects to the regional datacenter IP address.</span></span>

5. <span data-ttu-id="85a39-149">Los servidores de Exchange Online establecen una conexión con el centro de datos activo donde reside el inquilino del cliente.</span><span class="sxs-lookup"><span data-stu-id="85a39-149">The Exchange Online servers establish a connection to the active datacenter where the customer's tenant resides.</span></span>

![Centro de datos regional más próximo de EE. UU.](media/c0628c54-0059-48c5-8a0f-41bf392ee182.png)
  
## <a name="connecting-to-the-active-datacenter"></a><span data-ttu-id="85a39-151">Conexión con el centro de datos activo</span><span class="sxs-lookup"><span data-stu-id="85a39-151">Connecting to the active datacenter</span></span>

<span data-ttu-id="85a39-p110">Conectar con el centro de datos activo está diseñado para más pesadas cargas de trabajo de transferencia de datos y se usa actualmente en SharePoint Online. En esta situación, cuando los clientes intentan conectarse a Office 365, su explorador se redirige al centro de datos activo para su inquilino de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="85a39-p110">Connecting to the active datacenter is designed for heavier data transfer workloads and is currently used by SharePoint Online. In this situation, when clients attempt to connect to Office 365, their browser is redirected to the active datacenter for their SharePoint Online tenant.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="85a39-154">¿Cómo funciona esto?</span><span class="sxs-lookup"><span data-stu-id="85a39-154">How does this work?</span></span>

<span data-ttu-id="85a39-p111">Cuando el equipo cliente se conecta a SharePoint Online desde una región diferente, la conexión se redirige al centro de datos de SharePoint Online activo. En este escenario, el cliente está utilizando un estándar que ofrece, lo que en las conexiones del portal restante local y las conexiones de SharePoint Online que se dirige al centro de datos activa.</span><span class="sxs-lookup"><span data-stu-id="85a39-p111">When the client computer is connecting to SharePoint Online from a different region, the connection is redirected to the active SharePoint Online datacenter. In this scenario, the customer is using a standard offering, resulting in the portal connections remaining local and the SharePoint Online connections being directed to the active datacenter.</span></span>
  
1. <span data-ttu-id="85a39-157">El equipo cliente solicita a los servidores DNS locales para la dirección IP asociada con Office 365.</span><span class="sxs-lookup"><span data-stu-id="85a39-157">The client computer asks the local DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="85a39-158">Los servidores DNS locales del equipo cliente solicitan a los servidores de DNS de Microsoft para la dirección IP asociada con Office 365.</span><span class="sxs-lookup"><span data-stu-id="85a39-158">The client computer's local DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="85a39-159">Los servidores DNS de Microsoft devolución el nombre del servidor del centro de datos SharePoint Online activo (basado en la ubicación del inquilino de Office 365 del cliente), y el equipo cliente repite los pasos 1 y 2 para obtener la dirección IP del centro de datos de Office 365 activo.</span><span class="sxs-lookup"><span data-stu-id="85a39-159">Microsoft's DNS servers return the server name of the active SharePoint Online datacenter (based on the location of the client's Office 365 tenant), and the client computer repeats steps 1 and 2 to obtain the IP address of the active Office 365 datacenter.</span></span>

4. <span data-ttu-id="85a39-160">El equipo cliente se conecta a la dirección IP del centro de datos activo.</span><span class="sxs-lookup"><span data-stu-id="85a39-160">The client computer connects to the active datacenter IP address.</span></span>

![Centro de datos activo de EE. UU.](media/c6d2933f-49cb-4536-bea7-c868707755ae.png)
  
## <a name="connecting-over-virtual-private-networks-vpns"></a><span data-ttu-id="85a39-162">Conexión a través de redes privadas virtuales (VPN)</span><span class="sxs-lookup"><span data-stu-id="85a39-162">Connecting over Virtual Private Networks (VPNs)</span></span>

<span data-ttu-id="85a39-p112">Este tipo de conexión aplica sólo cuando se usa una red privada virtual (VPN) en los equipos cliente. En realidad, el comportamiento de Office 365 no cambia simplemente porque se usa una red privada virtual, pero las redes privadas virtuales con frecuencia se usan para controlar cómo los equipos cliente establecen conexiones a Office 365 y, normalmente, los resultados en una experiencia degradada, por lo que es importante cubrir.</span><span class="sxs-lookup"><span data-stu-id="85a39-p112">This type of connection applies only when a virtual private network (VPN) is used by client computers. In reality, Office 365 behavior isn't changed simply because a VPN is used, but VPNs are commonly used to control how client computers establish connections to Office 365 and usually results in a degraded experience, so it's important to cover.</span></span>
  
## <a name="how-does-this-work"></a><span data-ttu-id="85a39-165">¿Cómo funciona esto?</span><span class="sxs-lookup"><span data-stu-id="85a39-165">How does this work?</span></span>

<span data-ttu-id="85a39-p113">Cuando el equipo cliente establece una conexión VPN a una oficina corporativa en una región diferente, los servidores DNS en los que office se usan en lugar de los servidores DNS en la ubicación del equipo cliente. En la mayoría de los casos, esta conexión adicional a través de la VPN, degradará la experiencia de Office 365. Los servicios de Office 365 están optimizados para conexiones de cliente de servicio como más cercano al usuario final como sea posible. Muchos servicios sacar provecho de la red perimetral Azure, redes de distribución de contenido y la capacidad de red confiable en la red de Microsoft para ofrecer la mejor experiencia de usuario posible cuando se realizan las solicitudes de red para servicios de Office 365 lo más cerca del equipo cliente como sea posible.</span><span class="sxs-lookup"><span data-stu-id="85a39-p113">When the client computer establishes a VPN connection to a corporate office in a different region, the DNS servers at that office are used instead of the DNS servers at the client computer's location. In most cases, this extra connection over the VPN will degrade the Office 365 experience. The Office 365 services are optimized to service customer connections as close to the end user as possible. Many services leverage the Azure edge network, Content Delivery Networks, and the reliable network capacity on the Microsoft network to deliver the best possible user experience when network requests for Office 365 services are made as close to the client computer as possible.</span></span>
  
1. <span data-ttu-id="85a39-170">El equipo cliente solicita el DNS VPN servidores para la dirección IP asociada con Office 365.</span><span class="sxs-lookup"><span data-stu-id="85a39-170">The client computer asks the VPN DNS servers for the IP address associated with Office 365.</span></span>

2. <span data-ttu-id="85a39-171">Los servidores DNS de la VPN del equipo cliente solicitan a los servidores de DNS de Microsoft para la dirección IP asociada con Office 365.</span><span class="sxs-lookup"><span data-stu-id="85a39-171">The client computer's VPN DNS servers ask the Microsoft DNS servers for the IP address associated with Office 365.</span></span>

3. <span data-ttu-id="85a39-172">Los servidores DNS de Microsoft devolución el nombre del servidor regional (basado en la ubicación de los servidores DNS de la VPN), y el equipo cliente repite los pasos 1 y 2 para obtener la información de dirección IP del centro de datos de Office 365 regional.</span><span class="sxs-lookup"><span data-stu-id="85a39-172">Microsoft's DNS servers return the regional server name (based on the location of the VPN DNS servers), and the client computer repeats steps 1 and 2 to obtain the IP address information of the regional Office 365 datacenter.</span></span>

4. <span data-ttu-id="85a39-173">El equipo cliente conecta al centro de datos dirección IP que se encuentra más cercano a la oficina corporativa con que se estableció una conexión VPN.</span><span class="sxs-lookup"><span data-stu-id="85a39-173">The client computer connects to the datacenter IP address that's closest to the corporate office they established a VPN connection with.</span></span>

![Conectividad VPN de centro de datos](media/b5f4c06c-65a3-462d-aae8-9a4602dd8d9e.png)
  
<span data-ttu-id="85a39-175">Éste es un vínculo corto que puede usar para volver:[https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span><span class="sxs-lookup"><span data-stu-id="85a39-175">Here's a short link you can use to come back: [https://aka.ms/o365clientconnectivity](https://aka.ms/o365clientconnectivity)</span></span>
  
## <a name="see-also"></a><span data-ttu-id="85a39-176">Vea también</span><span class="sxs-lookup"><span data-stu-id="85a39-176">See also</span></span>

[<span data-ttu-id="85a39-177">Administración de extremos de Office 365</span><span class="sxs-lookup"><span data-stu-id="85a39-177">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[<span data-ttu-id="85a39-178">Conectividad de red a Office 365</span><span class="sxs-lookup"><span data-stu-id="85a39-178">Network connectivity to Office 365</span></span>](network-connectivity.md)
