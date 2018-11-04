---
title: Planificación de dispositivos de red que se conecten a servicios de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 073433ca-3511-4db9-b173-7a2edca57691
description: 'Resumen: describe las consideraciones sobre la capacidad de la red, los aceleradores de WAN y los dispositivos que equilibran la carga y que se utilizan para conectarse a Office 365.'
ms.openlocfilehash: 023eb3f5ed4d81d1d49d18c69ef8c81032fd5851
ms.sourcegitcommit: 317c2753be2aedb60698e94606ba59b63c962328
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/02/2018
ms.locfileid: "25933127"
---
# <a name="plan-for-network-devices-that-connect-to-office-365-services"></a><span data-ttu-id="bc80b-103">Planificación de dispositivos de red que se conecten a servicios de Office 365</span><span class="sxs-lookup"><span data-stu-id="bc80b-103">Plan for network devices that connect to Office 365 services</span></span>

 <span data-ttu-id="bc80b-104">**Resumen**: describe las consideraciones sobre la capacidad de la red, los aceleradores de WAN y los dispositivos que equilibran la carga y que se utilizan para conectarse a Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc80b-104">**Summary**: Describes considerations for network capacity, WAN accelerators, and load balancing devices that are used to connect to Office 365.</span></span>
  
<span data-ttu-id="bc80b-p101">Algunos hardware de red puede tener limitaciones en el número de sesiones simultáneas que se admiten. Para organizaciones que tengan más de 2.000 usuarios, se recomienda que sus dispositivos de red para asegurarse de que son capaces de administrar el tráfico del servicio Office 365 adicional que van a supervisar. Red administración Protocolo simple (SNMP) software de supervisión pueden ayudarle a hacerlo.</span><span class="sxs-lookup"><span data-stu-id="bc80b-p101">Some network hardware may have limitations on the number of concurrent sessions that are supported. For organizations having more than 2,000 users, we recommend that they monitor their network devices to ensure they are capable of handling the additional Office 365 service traffic. Simple Network Management Protocol (SNMP) monitoring software can help you do this.</span></span>

||
|:-----|
| <span data-ttu-id="bc80b-108">En este artículo forma parte de la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="bc80b-108">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

<span data-ttu-id="bc80b-p102">Configuración de proxy de Internet saliente también afecta a la conectividad a los servicios de Office 365 para las aplicaciones cliente en local. También debe configurar los dispositivos de proxy de la red para permitir conexiones para las aplicaciones y direcciones URL de servicios de nube de Microsoft. Cada organización es diferente. Para obtener una idea de cómo Microsoft administra este proceso y la cantidad de ancho de banda se aprovisione, [Lea el caso práctico](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span><span class="sxs-lookup"><span data-stu-id="bc80b-p102">On-premises outgoing Internet proxy settings also affect connectivity to Office 365 services for your client applications. You must also configure your network proxy devices to allow connections for Microsoft cloud services URLs and applications. Every organization is different. To get an idea for how Microsoft manages this process and the amount of bandwidth we provision, [read the case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365).</span></span>
  
<span data-ttu-id="bc80b-113">El siguiente Skype para artículos de Ayuda de negocio tienen más información acerca de Skype para la configuración de negocio:</span><span class="sxs-lookup"><span data-stu-id="bc80b-113">The following Skype for Business Help articles have more information about Skype for Business settings:</span></span>
  
- [<span data-ttu-id="bc80b-114">Solución de problemas de Skype para errores de inicio de sesión empresarial en línea para los administradores</span><span class="sxs-lookup"><span data-stu-id="bc80b-114">Troubleshooting Skype for Business Online sign-in errors for administrators</span></span>](https://docs.microsoft.com/skypeforbusiness/set-up-skype-for-business-online/troubleshooting-sign-in-errors-for-admins)

- [<span data-ttu-id="bc80b-115">No se puede conectar a Skype para la empresa o determinadas características no funcionan, porque un firewall local bloquea la conexión</span><span class="sxs-lookup"><span data-stu-id="bc80b-115">You cannot connect to Skype for Business, or certain features do not work, because an on-premises firewall blocks the connection</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=243625)

> [!NOTE]
> <span data-ttu-id="bc80b-116">Si bien muchas de estas opciones son Skype para específicas de la empresa, las instrucciones generales sobre la configuración de red son útil para todos los servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="bc80b-116">While many of these settings are Skype for Business-specific, the general guidance on network configuration is useful for all Office 365 services.</span></span>
  
## <a name="determining-network-capacity"></a><span data-ttu-id="bc80b-117">Determinar la capacidad de la red</span><span class="sxs-lookup"><span data-stu-id="bc80b-117">Determining Network Capacity</span></span>

<span data-ttu-id="bc80b-p103">Cada dispositivo de red que existe en una conexión tiene un límite de capacidad. Entre estos dispositivos se incluyen los adaptadores, enrutadores y  conmutadores de la red de cliente y servidor, así como los concentradores  que los interconectan. Una capacidad de red adecuada significa que ninguno de ellos está saturado. Supervisar la actividad de la red es fundamental para contribuir a garantizar que las cargas reales en todos los dispositivos de red estén por debajo de su capacidad máxima. La capacidad de la red afecta el rendimiento del dispositivo proxy.</span><span class="sxs-lookup"><span data-stu-id="bc80b-p103">Every network device that exists on a connection has its capacity limit. These devices include the client and server network adapters, routers, switches, and hubs that interconnect them. Adequate network capacity means that none of them are saturated. Monitoring network activity is essential to help ensure that the actual loads on all network devices are less than their maximum capacity. Network capacity affects proxy device performance.</span></span>
  
<span data-ttu-id="bc80b-p104">En la mayoría de las situaciones, el ancho de banda de conexión de Internet establece el límite para la cantidad de tráfico. Un rendimiento bajo durante horas punta de tráfico probablemente está causado por un uso excesivo del vínculo de Internet. Esta situación también se aplica a un escenario de sucursal, donde están conectados los equipos de servidor proxy sucursales para el dispositivo de proxy en sedes centrales de la sucursal a través de un vínculo lento de red de área extensa (WAN).</span><span class="sxs-lookup"><span data-stu-id="bc80b-p104">In most situations, the Internet connection bandwidth sets the limit for the amount of traffic. Weak performance during peak traffic hours is probably caused by excessive use of the Internet link. This situation also applies to a branch office scenario, where branch office proxy server computers are connected to the proxy device at the branch's headquarters over a slow Wide Area Network (WAN) link.</span></span>
  
<span data-ttu-id="bc80b-p105">Para probar la capacidad de red, supervisar la actividad de red en la interfaz de red del proxy. Si es más del 75 por ciento del ancho de banda máximo de cualquier interfaz de red, considere la posibilidad de aumentar el ancho de banda de la infraestructura de red que no es la adecuada. O bien, considere el uso de características avanzadas, como la compresión HTTP.</span><span class="sxs-lookup"><span data-stu-id="bc80b-p105">To test network capacity, monitor the network activity on the proxy network interface. If it's more than 75 percent of the maximum bandwidth of any network interface, consider increasing the bandwidth of the network infrastructure that's inadequate. Or, consider using advanced features, such as HTTP compression.</span></span>
  
## <a name="wan-accelerators"></a><span data-ttu-id="bc80b-129">Aceleradores WAN</span><span class="sxs-lookup"><span data-stu-id="bc80b-129">WAN Accelerators</span></span>

<span data-ttu-id="bc80b-p106">Si su organización usa dispositivos de proxy de aceleración de área extensa (WAN) de red, es posible que tiene problemas al tener acceso a los servicios de Office 365. Es posible que necesite optimizar su dispositivo de red o dispositivos para asegurarse de que los usuarios tengan una experiencia coherente al obtener acceso a Office 365. Por ejemplo, servicios de Office 365 cifran algún contenido de Office 365 y el encabezado TCP. El dispositivo no es posible que sea capaz de controlar este tipo de tráfico.</span><span class="sxs-lookup"><span data-stu-id="bc80b-p106">If your organization uses wide area network (WAN) acceleration proxy appliances, you may encounter issues when you access the Office 365 services. You may need to optimize your network device or devices to ensure that your users have a consistent experience when accessing Office 365. For example, Office 365 services encrypt some Office 365 content and the TCP header. Your device may not be able to handle this kind of traffic.</span></span>
  
<span data-ttu-id="bc80b-134">Lea nuestra declaración de soporte técnico sobre el [uso de controlador de optimización de la WAN o dispositivos de inspección del tráfico con Office 365](https://support.microsoft.com/kb/2690045).</span><span class="sxs-lookup"><span data-stu-id="bc80b-134">Read our support statement about [Using WAN Optimization Controller or Traffic/Inspection devices with Office 365](https://support.microsoft.com/kb/2690045).</span></span>
  
## <a name="hardware-and-software-load-balancing-devices"></a><span data-ttu-id="bc80b-135">Dispositivos de equilibrio de carga de hardware y software</span><span class="sxs-lookup"><span data-stu-id="bc80b-135">Hardware and Software Load-balancing Devices</span></span>

<span data-ttu-id="bc80b-p107">Su organización necesita usar un equilibrador de carga de red basado en hardware (HLB) o una solución de equilibrio de carga de red (NLB) para distribuir solicitudes a sus servidores de servicios de federación de Active Directory (AD FS) o servidores híbridos Exchange. Los equilibradores de carga controlan el tráfico de red de los servidores locales. Estos servidores son muy importantes para contribuir a garantizar la disponibilidad de una implementación híbrida de Exchange y de inicio de sesión único.</span><span class="sxs-lookup"><span data-stu-id="bc80b-p107">Your organization needs to use a hardware load balancer (HLB) or a Network Load Balancing (NLB) solution to distribute requests to your Active Directory Federation Services (AD FS) servers and/or your Exchange hybrid servers. Load-balancing devices control the network traffic to the on-premises servers. These servers are crucial in helping to ensure the availability of single sign-on and Exchange hybrid deployment.</span></span>
  
<span data-ttu-id="bc80b-p108">Se proporciona una solución NLB basada en software integrada en Windows Server. Office 365 es compatible con esta solución para lograr el equilibrio de carga.</span><span class="sxs-lookup"><span data-stu-id="bc80b-p108">We provide a software-based NLB solution built into Windows Server. Office 365 supports this solution to achieve load balancing.</span></span>
  
## <a name="firewalls-and-proxies"></a><span data-ttu-id="bc80b-141">Los firewalls y servidores proxy</span><span class="sxs-lookup"><span data-stu-id="bc80b-141">Firewalls and proxies</span></span>

<span data-ttu-id="bc80b-142">Para obtener más información acerca de cómo configurar los firewall y servidores proxy para conectarse a Office 365, lea [los extremos de administración de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [conectividad de red a Office 365](network-connectivity.md)y [Office 365 extremos preguntas más frecuentes](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) para obtener más información acerca de la selección de circuitos y dispositivos.</span><span class="sxs-lookup"><span data-stu-id="bc80b-142">For more details on configuring firewalls and proxies to connect to Office 365, read [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a), [Network connectivity to Office 365](network-connectivity.md), and [Office 365 endpoints FAQ](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d) to learn more about devices and circuit selection.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="bc80b-143">Vea también</span><span class="sxs-lookup"><span data-stu-id="bc80b-143">See also</span></span>

[<span data-ttu-id="bc80b-144">Asesores de implementación para servicios de Office 365</span><span class="sxs-lookup"><span data-stu-id="bc80b-144">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
