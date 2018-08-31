---
title: Planeación de la migración y red para Office 365
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/29/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- BCS160
ms.assetid: f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132
description: Contiene vínculos a información sobre la planeación de la red y las pruebas y migración a Office 365.
ms.openlocfilehash: e2434a65b48c12f38d7371a569ba8e0bc282ae06
ms.sourcegitcommit: ad5bdc53ca67ee6a663c27648511c1ad768a76d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "23223062"
---
# <a name="network-and-migration-planning-for-office-365"></a><span data-ttu-id="0f6a9-103">Planeación de la migración y red para Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-103">Network and migration planning for Office 365</span></span>

<span data-ttu-id="0f6a9-104">Este artículo contiene vínculos a información acerca de la planeación y pruebas de red y migración a Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-104">This article contains links to information about network planning and testing, and migration to Office 365.</span></span>
  
<span data-ttu-id="0f6a9-105">Antes de implementar por primera vez o migrar a Office 365, puede usar la información de estos temas para calcular el ancho de banda que necesita y, a continuación, probar y verificar que tiene suficiente ancho de banda para implementar o migrar a Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-105">Before you deploy for the first time or migrate to Office 365, you can use the information in these topics to estimate the bandwidth you need and then to test and verify that you have enough bandwidth to deploy or migrate to Office 365.</span></span>

||
|:-----|
| <span data-ttu-id="0f6a9-106">En este artículo forma parte de la [planeación de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune).</span><span class="sxs-lookup"><span data-stu-id="0f6a9-106">This article is part of [Network planning and performance tuning for Office 365](https://aka.ms/tune).</span></span>|

|||
|:-----|:-----|
|![Consulte red de nube de Microsoft para póster arquitectos de empresa](media/3094be9f-2407-4fa5-896d-aa66ef7b9bb9.png)|<span data-ttu-id="0f6a9-108">Para que los pasos para optimizar el rendimiento de la red Office 365 y otras plataformas de nube de Microsoft y los servicios, vea el póster de [Microsoft en la nube de la red para arquitectos de la empresa](https://aka.ms/cloudarchnetworking) .</span><span class="sxs-lookup"><span data-stu-id="0f6a9-108">For the steps to optimize your network for Office 365 and other Microsoft cloud platforms and services, see the [Microsoft Cloud Networking for Enterprise Architects](https://aka.ms/cloudarchnetworking) poster.</span></span> |
   
## <a name="estimate-network-bandwidth-requirements"></a><span data-ttu-id="0f6a9-109">Estimar los requisitos de ancho de banda de la red</span><span class="sxs-lookup"><span data-stu-id="0f6a9-109">Estimate network bandwidth requirements</span></span>
<span data-ttu-id="0f6a9-110"><a name="EstimateBandwidthRequirements"> </a></span><span class="sxs-lookup"><span data-stu-id="0f6a9-110"></span></span>

<span data-ttu-id="0f6a9-p101">Con Office 365 puede aumentar la utilización del circuito de internet de su organización. Es importante determinar si la cantidad de ancho de banda disponible actualmente es suficiente para controlar el aumento estimado una vez que Office 365 es totalmente implementado dejando al menos el 20% capacidad para tratar los más ocupados de días.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p101">Using Office 365 may increase the utilization of your organization's internet circuit. It's important to determine if the amount of bandwidth currently available is enough to handle the estimated increase once Office 365 is fully deployed while leaving at least 20% capacity to handle the busiest of days.</span></span>
  
<span data-ttu-id="0f6a9-113">Para calcular el ancho de banda, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="0f6a9-113">To estimate the bandwidth, use the following steps:</span></span>
  
1. <span data-ttu-id="0f6a9-p102">Evaluar el número de clientes que utilizará cada salida de Internet. Dejar que nuestra red multi-terabit controle tanta información de la conexión como sea posible.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p102">Assess the number of clients that will use each Internet egress. Let our multi-terabit network handle as much of the connection as possible.</span></span> 
    
2. <span data-ttu-id="0f6a9-p103">Determinar qué servicios de Office 365 y características estarán disponibles para los clientes puedan usar. Probablemente tendrá grupos de personas con distintos servicios o perfiles de uso.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p103">Determine which Office 365 services and features will be available for clients to use. You will likely have groups of people with different services or usage profiles.</span></span>
    
3. <span data-ttu-id="0f6a9-p104">Medir el uso de red para un grupo piloto de los clientes. Asegúrese de que los clientes pilotos son representante de los diferentes perfiles de personas de la organización, así como las distintas ubicaciones geográficas. Puede comprobar los resultados obtenidos con nuestros antiguo calculadoras de forma entre para [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)y [Skype para la empresa](https://go.microsoft.com/fwlink/p/?LinkId=321551) o el [caso práctico](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) que se realizaron en nuestra propia red.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p104">Measure the network use for a pilot group of clients. Ensure the pilot clients are representative of the different profiles of people in the organization as well as the different geographic locations. You can cross-check your results against our old calculators for [Exchange ](https://go.microsoft.com/fwlink/p/?LinkId=321550)and [Skype for Business](https://go.microsoft.com/fwlink/p/?LinkId=321551) or the [case study](https://www.microsoft.com/itshowcase/Article/Content/631/Optimizing-network-performance-for-Microsoft-Office-365) we performed on our own network.</span></span> 
    
4. <span data-ttu-id="0f6a9-121">Utilice las medidas del grupo piloto para extrapolar las necesidades de toda la organización y volver a probar para validar las estimaciones antes de realizar cualquier cambio en la red.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-121">Use the measurements from the pilot group to extrapolate the entire organization's needs and re-test to validate the estimations before making any changes to your network.</span></span>
    
## <a name="test-your-existing-network"></a><span data-ttu-id="0f6a9-122">Probar la red existente</span><span class="sxs-lookup"><span data-stu-id="0f6a9-122">Test your existing network</span></span>
<span data-ttu-id="0f6a9-123"><a name="calculators"> </a></span><span class="sxs-lookup"><span data-stu-id="0f6a9-123"></span></span>

 <span data-ttu-id="0f6a9-p105">**Herramientas de red.** Probar y validar el ancho de banda de Internet para determinar las restricciones de descarga, carga y latencia. Estas herramientas le ayudará a determinar las capacidades de la red para la migración, así como una vez que está totalmente implementado.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p105">**Network tools.** Test and validate your Internet bandwidth to determine download, upload, and latency constraints. These tools will help you determine the capabilities of your network for migration as well as after you're fully deployed.</span></span> 
  
- <span data-ttu-id="0f6a9-p106">[Analizador de mensaje de Microsoft](https://technet.microsoft.com/library/jj649776.aspx): mensaje Analyzer es una herramienta eficaz para solucionar los problemas de red. Analizador de mensaje captura, muestra y analiza el tráfico de mensajería basada en el protocolo y los mensajes del sistema. Analizador de mensaje también permite importar, agregadas y analizar datos de archivos de registro y seguimiento.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p106">[Microsoft Message Analyzer](https://technet.microsoft.com/library/jj649776.aspx): Message Analyzer is an effective tool for troubleshooting network issues. Message Analyzer captures, displays, and analyzes protocol-based messaging traffic and system messages. Message Analyzer also lets you import, aggregate, and analyze data from log and trace files.</span></span>
    
- <span data-ttu-id="0f6a9-130">[Analizador de conectividad remota de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=517243): comprueba la conectividad en el entorno de Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-130">[Microsoft Remote Connectivity Analyzer](https://go.microsoft.com/fwlink/p/?LinkId=517243): Tests connectivity in your Exchange Online environment.</span></span>
    
- <span data-ttu-id="0f6a9-131">Use [el Asistente de recuperación para Office 365 y de soporte técnico de Microsoft](https://diagnostics.office.com/#/Download?env=SOC) para solucionar problemas de Outlook y Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-131">Use the [Microsoft Support and Recovery Assistant for Office 365](https://diagnostics.office.com/#/Download?env=SOC) to fix Outlook and Office 365 problems.</span></span> 
    
## <a name="best-practices-for-network-planning-and-improving-migration-performance-for-office-365"></a><span data-ttu-id="0f6a9-132">Best practices for network planning and improving migration performance for Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-132">Best practices for network planning and improving migration performance for Office 365</span></span>
<span data-ttu-id="0f6a9-133"><a name="BestPractices"> </a></span><span class="sxs-lookup"><span data-stu-id="0f6a9-133"></span></span>

<span data-ttu-id="0f6a9-134">Profundizar un poco más en estos procedimientos recomendados para obtener más información acerca de cómo mejorar la experiencia de Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-134">Dig a little deeper into these best practices for more information about improving your Office 365 experience.</span></span>
  
1. <span data-ttu-id="0f6a9-p107">¿Desea empezar a ayudar a los usuarios inmediatamente? Para obtener sugerencias sobre el uso de Office 365, incluidos SharePoint Online, Exchange Online y Lync Online, cuando la red no está cooperación acaba, vea [procedimientos recomendados para usar Office 365 en una red lenta](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) . Este artículo contiene vínculos a las cargas de contenido de TechNet y Support.office.com para optimizar su experiencia de Office 365 e incluye información en formas sencillas para personalizar las páginas web y cómo establecer la configuración de Internet Explorer para la mejor experiencia de Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p107">Want to get started helping your users right away? See [Best practices for using Office 365 on a slow network](https://support.office.com/article/fd16c8d2-4799-4c39-8fd7-045f06640166) for tips on using Office 365, including SharePoint Online, Exchange Online, and Lync Online, when your network just isn't cooperating. This article links out to loads of content on TechNet and Support.office.com for optimizing your Office 365 experience and includes information on easy ways to customize your web pages and how to set your Internet Explorer settings for the best Office 365 experience.</span></span> 
    
2. <span data-ttu-id="0f6a9-p108">Lea los [Principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples) para comprender los principios de conectividad para administrar el tráfico de Office 365 y obtener el mejor rendimiento posible de forma segura. En este artículo le ayudará a comprender las instrucciones más reciente para optimizar de forma segura conectividad de red de Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p108">Read [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance. This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity.</span></span> 
    
3. <span data-ttu-id="0f6a9-p109">Mejorar el rendimiento de la migración de correo mediante la administración de cuidadosamente la programación de actualizaciones de Windows. Puede actualizar los equipos cliente en lotes y asegúrese de que todos los equipos cliente se actualicen antes de migrar a Office 365 para regular el uso de ancho de banda de red. Para obtener más información, vea [actualizar de forma manual y configurar escritorios de Office 365 para obtener las actualizaciones más recientes](https://support.microsoft.com/gp/office-2013-365-update).</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p109">Improve mail migration performance by carefully managing the schedule for Windows Updates. You can update your client computers in batches and ensure that all client computers are updated before migrating to Office 365 to regulate the use of network bandwidth. For more information, see [Manually update and configure desktops for Office 365 for the latest updates](https://support.microsoft.com/gp/office-2013-365-update).</span></span>
    
4. <span data-ttu-id="0f6a9-p110">El tráfico de red de Office 365 funciona mejor cuando se trata como un servicio de Internet de confianza y permitidos para el desvío de gran parte de la digitalización que algunas organizaciones se coloque en el tráfico de red a los servicios de Internet no son de confianza y filtrado tradicional. Normalmente, esto incluye quitar saliente de procesamiento como la autenticación de usuario de proxy y la inspección de paquetes, así como asegurarse de salida local a Internet con la traducción de direcciones de red (NAT) adecuada y suficiente capacidad de ancho de banda para controlar el mayor solicitudes de red. Hacer referencia a [los extremos de administración de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)para obtener instrucciones adicionales sobre la configuración de la red para administrar Office 365 como un servicio de Internet de confianza en la red.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p110">Office 365 network traffic performs best when it's treated as a trusted Internet service and allowed to bypass much of the traditional filtering and scanning that some organizations place on network traffic to untrusted Internet services. This typically includes removing outbound processing such as proxy user authentication and packet inspection, as well as ensuring local egress to the Internet with the proper Network Address Translation (NAT) and enough bandwidth capacity to handle the increased network requests. Refer to [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)for additional guidance on configuring your network to handle Office 365 as a trusted Internet service on your network.</span></span>
    
1. <span data-ttu-id="0f6a9-p111">Asegúrese de que [los extremos de administración de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). El tráfico adicional que se va a Office 365 da como resultado un aumento de conexiones de proxy de salida, así como un aumento del tráfico seguro a través de TLS/SSL.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p111">Ensure [Managing Office 365 endpoints](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a). The additional traffic going to Office 365 results in an increase of outbound proxy connections as well as an increase in secure traffic over TLS/SSL.</span></span>
    
2. <span data-ttu-id="0f6a9-p112">Si los servidores proxy de salida requieren autenticación de usuario puede experimentar una conexión lenta o una pérdida de funcionalidad. Omitir el requisito de autenticación para los dominios de Office 365 puede reducir esta sobrecarga.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p112">If your outbound proxies require user authentication you may experience slow connectivity or a loss of functionality. Bypassing the authentication requirement for the Office 365 domains can reduce this overhead.</span></span>
    
3. <span data-ttu-id="0f6a9-p113">Si tiene gran cantidad de calendarios y buzones compartidos, puede ver un incremento en la cantidad de conexiones desde Outlook a Exchange. Por ejemplo, el cliente de Outlook puede abrir hasta un máximo de dos conexiones adicionales para cada calendario compartido en uso. En este caso, asegúrese de que el proxy de salida pueda manejar las conexiones o esquive el proxy para las conexiones a Office 365 para Outlook.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p113">If you have a large number of shared calendars and mailboxes, you may see an increase in the number of connections from Outlook to Exchange. For instance, the Outlook client may open up to two additional connections for each shared calendar in use. In this situation, ensure that the egress proxy can handle the connections, or bypass the proxy for connections to Office 365 for Outlook.</span></span>
    
4. <span data-ttu-id="0f6a9-p114">Determinar el número máximo de dispositivos admitidos para una dirección IP pública y cómo equilibrar la carga entre varias direcciones IP. Para obtener más información, vea [admitir NAT con Office 365](nat-support-with-office-365.md).</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p114">Determine the maximum number of supported devices for a public IP address and how to load balance across multiple IP addresses. For more information, see [NAT support with Office 365](nat-support-with-office-365.md).</span></span>
    
5. <span data-ttu-id="0f6a9-p115">Si se está inspeccionando las conexiones salientes desde los equipos de la red, omitiendo este filtrado a los dominios de Office 365 mejorará conectividad y rendimiento. Además, omitir la inspección de salida a menudo elimina la necesidad de una sola salida de Internet y permite la salida de Internet local para Office 365 dirigido a las solicitudes de red.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p115">If you're inspecting outbound connections from computers on your network, bypassing this filtering to the Office 365 domains will improve connectivity and performance. Additionally, bypassing outbound inspection often removes the need for a single Internet egress and enables local Internet egress for Office 365 destined network requests.</span></span>
    
6. <span data-ttu-id="0f6a9-p116">Algunos clientes encontrarán la configuración de la red interna puede afectar al rendimiento. Negociación automática o la detección automática de red de configuración como el tamaño de transmisión máxima (MTU) de la unidad, y las rutas debajo del nivel óptimas a Internet son sitios comunes para buscar.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-p116">Some customers find internal network settings may affect performance. Settings such as maximum transmission unit (MTU) size, network auto-negotiation or auto-detection, and sub-optimal routes to the Internet are common places to look.</span></span>
    
## <a name="network-planning-reference-for-office-365"></a><span data-ttu-id="0f6a9-159">Referencia de planeación de red para Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-159">Network planning reference for Office 365</span></span>
<span data-ttu-id="0f6a9-160"><a name="NetReference"> </a></span><span class="sxs-lookup"><span data-stu-id="0f6a9-160"></span></span>

<span data-ttu-id="0f6a9-161">Estos temas contienen información detallada de referencia de red de Office 365.</span><span class="sxs-lookup"><span data-stu-id="0f6a9-161">These topics contain detailed Office 365 network reference information.</span></span>
  
- [<span data-ttu-id="0f6a9-162">Administración de extremos de Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-162">Managing Office 365 endpoints</span></span>](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
    
- [<span data-ttu-id="0f6a9-163">Conectividad de clientes</span><span class="sxs-lookup"><span data-stu-id="0f6a9-163">Client connectivity</span></span>](client-connectivity.md)
    
- [<span data-ttu-id="0f6a9-164">Redes de entrega de contenido</span><span class="sxs-lookup"><span data-stu-id="0f6a9-164">Content delivery networks</span></span>](content-delivery-networks.md)
    
- [<span data-ttu-id="0f6a9-165">Registros de sistema de nombres de dominio externos para Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-165">External Domain Name System records for Office 365</span></span>](external-domain-name-system-records.md)
    
- [<span data-ttu-id="0f6a9-166">Compatibilidad con IPv6 en servicios de Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-166">IPv6 support in Office 365 services</span></span>](ipv6-support.md)
    
- [<span data-ttu-id="0f6a9-167">Principios de conectividad de red de Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-167">Office 365 Network Connectivity Principles</span></span>](https://aka.ms/o365networkingprinciples)
    
- [<span data-ttu-id="0f6a9-168">Microsoft Virtual Academy: Administración de rendimiento Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-168">Microsoft Virtual Academy: Office 365 Performance Management</span></span>](https://mva.microsoft.com/en-us/training-courses/office-365-performance-management-8416)
    
- [<span data-ttu-id="0f6a9-169">Redes de vídeo de Office 365 preguntas más frecuentes (P+F)</span><span class="sxs-lookup"><span data-stu-id="0f6a9-169">Office 365 video networking Frequently Asked Questions (FAQ)</span></span>](office-365-video-networking-faq.md)
    
- [<span data-ttu-id="0f6a9-170">Planificación de dispositivos de red que se conecten a servicios de Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-170">Plan for network devices that connect to Office 365 services</span></span>](plan-for-network-devices.md)
    
- [<span data-ttu-id="0f6a9-171">Asesores de implementación para servicios de Office 365</span><span class="sxs-lookup"><span data-stu-id="0f6a9-171">Deployment advisors for Office 365 services</span></span>](deployment-advisors-for-office-365.md)
    

