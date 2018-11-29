---
title: ExpressRoute para la conectividad en la nube de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
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
ms.openlocfilehash: 3ac8d52f50ff6df612de68ea51136fc16d5c9169
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872331"
---
# <a name="expressroute-for-microsoft-cloud-connectivity"></a>ExpressRoute para la conectividad en la nube de Microsoft

 **Resumen:** Descubra cómo ExpressRoute puede ayudarle mediante conexiones más rápidas y fiables a los servicios y las plataformas en la nube de Microsoft.
  
ExpressRoute proporciona una conexión de red privada, dedicada y de alto rendimiento con la nube de Microsoft.
  
## <a name="expressroute-to-the-microsoft-cloud"></a>ExpressRoute a la nube de Microsoft

Esta es la ruta de acceso de red a la nube de Microsoft sin una conexión de ExpressRoute.
  
**Figura 1: La ruta de acceso de red sin ExpressRoute**

![Figura 1: La ruta de acceso de red sin ExpressRoute](media/Network-Poster/ExpressRoute.png)
  
La figura 1 muestra la ruta de acceso típica entre una red local y la nube de Microsoft. El perímetro de red local se conecta a Internet a través de un vínculo WAN a un ISP. Después el tráfico viaja por Internet hasta el perímetro de la nube de Microsoft. Las ofertas de la nube de Microsoft incluyen Office 365, Microsoft Azure, Microsoft Intune y Dynamics 365. Los usuarios de una organización pueden encontrarse en la red local o en Internet.
  
Sin una conexión de ExpressRoute, la única parte de la ruta de acceso a la nube de Microsoft que puede controlar (y que puede tener una relación con el proveedor de servicios) es el vínculo entre el perímetro de la red local y el ISP. 
  
La ruta de acceso entre el ISP y el perímetro de la nube de Microsoft es un sistema de entrega de mejor esfuerzo en Internet sujeto a interrupciones, congestión de tráfico y la supervisión de usuarios malintencionados.
  
Los usuarios de Internet, como usuarios móviles o remotos, envían el tráfico a la nube de Microsoft a través de Internet.
  
Estas son las rutas de acceso de red a la nube de Microsoft con una conexión de ExpressRoute.
  
**Figura 2: Las rutas de acceso de red con ExpressRoute**

![Figura 2: La ruta de acceso de red con ExpressRoute](media/Network-Poster/ExpressRoute-post.png)
  
La figura 2 muestra dos rutas de acceso de red. El tráfico a Microsoft Intune viaja por la misma ruta que el tráfico normal de Internet. El tráfico que va a Office 365, Microsoft Azure y Dynamics 365 viaja a través de la conexión de ExpressRoute, una ruta dedicada que está entre el perímetro de la red local y el perímetro de la nube de Microsoft.
  
Con una conexión ExpressRoute, ahora dispone de control a través de una relación con su proveedor de servicios, a través de la ruta de acceso completa del tráfico desde el borde de Microsoft en la nube perimetral. Esta conexión puede ofrecer performance predecible y un [tiempo de actividad de 99,95% SLA](https://azure.microsoft.com/support/legal/sla/expressroute/v1_3/).
  
Ahora podrá disfrutar de un rendimiento y una latencia predecibles, según la conexión de su proveedor de servicios, en los servicios de Office 365, Azure y Dynamics 365. En este momento no se admiten las Conexiones de ExpressRoute a Microsoft Intune.
  
El tráfico enviado a través de la conexión de ExpressRoute ya no está sujeto a las interrupciones de Internet, la congestión del tráfico ni la supervisión.
  
Los usuarios de Internet, como usuarios móviles o remotos, siguen enviando el tráfico a la nube de Microsoft a través de Internet. Una excepción es el tráfico a una línea intranet de una aplicación empresarial hospedada en IaaS de Azure, que se envía por la conexión de ExpressRoute a través de una conexión de acceso remoto a la red local.
  
Incluso con una conexión de ExpressRoute, una parte del tráfico se sigue enviando a través de Internet, como las consultas de DNS, la comprobación de la lista de revocación de certificados y las solicitudes de red de entrega de contenido (CDN).
  
Consulte estos recursos adicionales para obtener más información:
  
- [ExpressRoute para Office 365](https://aka.ms/expressrouteoffice365)
    
- [ExpressRoute para Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="advantages-of-expressroute-for-azure"></a>Ventajas de ExpressRoute para Azure

Estas son algunas de las ventajas de usar ExpressRoute para los servicios en la nube basados en Azure:
  
- **Rendimiento predecible:** con una ruta dedicada al perímetro de la nube de Microsoft, el rendimiento no está sujeto a las interrupciones del proveedor de Internet y tiene un pico en el tráfico de Internet. Puede determinar a los proveedores y responsabilizarlos con un acuerdo de nivel de servicio de rendimiento y latencia en la nube de Microsoft.
    
- **Privacidad de los datos para el tráfico:** los usuarios malintencionados no podrán supervisar ni capturar o analizar paquetes del tráfico enviado a través de la conexión dedicada de ExpressRoute. Es tan seguro como usar vínculos WAN basados en Multiprotocol Label Switching (MPLS).
    
- **Conexiones de alto rendimiento:** gracias a la amplia compatibilidad con las conexiones de ExpressRoute, los proveedores de Exchange y los proveedores de servicios de red, podemos obtener un vínculo de hasta 10 Gbps a la nube de Microsoft.
    
- **Menor coste en algunas configuraciones:** aunque las conexiones de ExpressRoute suponen un coste adicional, en algunos casos una sola conexión de ExpressRoute puede costar menos que aumentar la capacidad de Internet en varias ubicaciones de la organización para proporcionar un rendimiento adecuado en los servicios en la nube de Microsoft.
    
Una conexión de ExpressRoute no garantiza un mayor rendimiento en todas las configuraciones. Se puede obtener un rendimiento menor a través de una conexión de ExpressRoute de ancho de banda bajo que a través de una conexión a Internet de ancho de banda alto que esté a unos pocos saltos de un centro de datos regional de Microsoft.
  
Para conocer las recomendaciones más recientes para el uso de ExpressRoute con Office 365, consulte [Azure ExpressRoute para Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd).
  
## <a name="expressroute-connectivity-models"></a>Modelos de conectividad de ExpressRoute

La tabla 1 muestra los tres modelos de conectividad principales para las conexiones de ExpressRoute.
  
|**Colocalizado en un intercambio de nube**|**Ethernet de punto a punto**|**Conexión (IP VPN) universal**|
|:-----|:-----|:-----|
|![Modelo de conectividad de ExpressRoute: Colocalizado en un intercambio de nube](media/Network-Poster/ER-Conn1.png)|![Modelo de conectividad de ExpressRoute: Ethernet de punto a punto](media/Network-Poster/ER-Conn2.png)|![Modelo de conectividad de ExpressRoute: Conexión (IP VPN) universal](media/Network-Poster/ER-Conn3.png)|
|Si el centro de datos se encuentra colocalizado en instalaciones con un intercambio de nube, puede solicitar una conexión cruzada virtual a la nube de Microsoft a través del intercambio de Ethernet del proveedor de colocalización.  <br/> |Si el centro de datos se encuentra en sus instalaciones, puede usar un vínculo punto a punto de Ethernet para conectarse a la nube de Microsoft.  <br/> |Si ya usa un proveedor de IP VPN (MPLS) para conectar los sitios de la organización, una conexión de ExpressRoute a la nube de Microsoft actúa como otra ubicación en su WAN privada.  <br/> |
   
 **Tabla 1: Modelos de conectividad de ExpressRoute**
  
## <a name="expressroute-peering-relationships-to-microsoft-cloud-services"></a>Relaciones de emparejamiento de ExpressRoute a los servicios en la nube de Microsoft

Una única conexión de ExpressRoute admite hasta tres relaciones diferentes de emparejamiento de Border Gateway Protocol (BGP) a distintas partes de la nube de Microsoft. BPG usa relaciones de emparejamiento para establecer la confianza e intercambiar información de enrutamiento.
  
**Figura 3: Las tres relaciones BGP en una sola conexión de ExpressRoute**

![Figura 3: Las tres relaciones BGP en una sola conexión de ExpressRoute](media/Network-Poster/ERPeering.png)
  
La figura 3 muestra una conexión ExpressRoute desde una red local. La conexión de ExpressRoute tiene tres relaciones lógicas de interconexión. Una relación de interconexión Microsoft va a servicios de Microsoft SaaS, incluyendo Dynamcs CRM Online y Office 365. Una relación de interconexión pública que se va a los servicios de Azure PaaS. Una relación de interconexión privada va a Azure IaaS y a una puerta de enlace de red virtual que hospeda máquinas virtuales.
  
La relación de emparejamiento de BGP de Microsoft: 
  
- Va de un enrutador de la red perimetral a las direcciones públicas de los servicios de Office 365 y Dynamics 365. 
    
- Admite la comunicación iniciada bidireccionalmente.
    
La relación de emparejamiento pública de BGP:
  
- Va de un enrutador de la red perimetral a las direcciones IP públicas de los servicios de Azure.
    
- Admite la comunicación iniciada unidireccionalmente solo desde sistemas locales. La relación de emparejamiento no admite comunicaciones iniciadas desde los servicios PaaS de Azure.
    
La relación de emparejamiento privada de BGP:
  
- Va de un enrutador del perímetro de la red de su organización a las direcciones IP privadas asignadas a sus redes virtuales de Azure.
    
- Admite la comunicación iniciada bidireccionalmente.
    
- Es una extensión de la red de su organización a la nube de Microsoft que incluye el direccionamiento y el enrutamiento internamente coherentes.
    
## <a name="example-of-application-deployment-and-traffic-flow-with-expressroute"></a>Ejemplo de la implementación de una aplicación y el flujo de tráfico con ExpressRoute

El modo en que el tráfico viaja a través de las conexiones de ExpressRoute y dentro de la nube de Microsoft es una función de las rutas en los saltos de la ruta de acceso entre el origen, el destino y el comportamiento de la aplicación. En este ejemplo vemos una aplicación que se ejecuta en una máquina virtual de Azure que tiene acceso a una granja de SharePoint local a través de una conexión VPN de sitio a sitio.
  
**Figura 4: Una aplicación de una máquina virtual de Azure que obtiene acceso a una granja de SharePoint local**

![Figura 4: Una aplicación de una máquina virtual de Azure que obtiene acceso a una granja de SharePoint local](media/Network-Poster/ER-App-Flow1.png)

  
La figura 4 muestra una granja de SharePoint local, una conexión VPN de sitio a sitio entre la red local y una red virtual en IaaS de Azure, un servidor de aplicaciones que se ejecuta como una máquina virtual de IaaS de Azure y el flujo de tráfico entre el servidor de aplicaciones y la granja de SharePoint.
  
La aplicación busca la dirección IP de la granja de SharePoint usando el DNS local y todo el tráfico atraviesa la conexión VPN de sitio a sitio.
  
Esta organización migró su granja de SharePoint local a SharePoint Online en Office 365 e implementó una conexión de ExpressRoute.
  
**Figura 5: Traslado de la granja de SharePoint local a SharePoint Online**

![Figura 5: Traslado de la granja de SharePoint local a SharePoint Online](media/Network-Poster/Hairpin1.png)
  
La figura 5 muestra la adición de una conexión de ExpressRoute con relaciones de emparejamiento a los servicios SaaS de Microsoft, a Office 365 y a los servicios IaaS de Azure que contienen el servidor de aplicaciones en una red virtual. La granja local de SharePoint se migró a Office 365.
  
Con las relaciones de emparejamiento privadas y de Microsoft:
  
- Desde la puerta de enlace de red virtual de Azure, hay disponibles ubicaciones locales en la conexión de ExpressRoute.
    
- Desde la suscripción a Office 365, las direcciones IP públicas de dispositivos perimetrales, como servidores proxy, están disponibles en la conexión de ExpressRoute.
    
- Desde el perímetro de la red local, las direcciones IP privadas de la red virtual de Azure y las direcciones IP públicas de Office 365 están disponibles en la conexión de ExpressRoute.
    
Cuando la aplicación tiene acceso a las direcciones URL de SharePoint Online, reenvía el tráfico a través de la conexión de ExpressRoute a un servidor proxy del perímetro. 
  
Cuando el servidor proxy busca la dirección IP de SharePoint Online, reenvía el tráfico de vuelta a través de la conexión de ExpressRoute. El tráfico de respuesta recorre la ruta inversa.
  
**Figura 6: Flujo de tráfico cuando se migra la granja de SharePoint a SharePoint Online en Office 365**

![Figura 6: Flujo de tráfico cuando se migra la granja de SharePoint a SharePoint Online en Office 365](media/Network-Poster/Hairpin2.png)

  
La figura 6 muestra cómo fluye el tráfico entre el servidor de aplicaciones y SharePoint Online en Office 365 a través de la relación de emparejamiento privada del servidor de aplicaciones al perímetro de la red local y después del perímetro a Office 365 a través de la relación de emparejamiento de Microsoft.
  
El resultado es una redirección al origen, consecuencia del comportamiento de la aplicación y el enrutamiento.
  
## <a name="expressroute-and-microsofts-cloud-network"></a>Red de nube de Microsoft y de ExpressRoute

Las conexiones de ExpressRoute están disponibles en dos versiones: ExpressRoute y ExpressRoute Premium.
  
### <a name="expressroute"></a>ExpressRoute

El modo en que el tráfico fluye entre la red de su organización y un centro de datos de Microsoft es una combinación de:
  
- Sus ubicaciones.
    
- Las ubicaciones de emparejamiento en la nube de Microsoft (las ubicaciones físicas para conectarse al perímetro de Microsoft).
    
- Las ubicaciones de los centros de datos de Microsoft.
    
Las ubicaciones de los centros de datos de Microsoft y las de emparejamiento en la nube están conectadas a la red en la nube de Microsoft.
  
Cuando se crea una conexión de ExpressRoute a una ubicación de emparejamiento en la nube de Microsoft, nos conectamos a la red en la nube de Microsoft y a todas las ubicaciones de centros de datos de Microsoft que hay en el mismo continente. El tráfico entre la ubicación de emparejamiento en la nube y el centro de datos de Microsoft de destino se realiza a través de la red en la nube de Microsoft.
  
Esto puede hacer que la entrega en los centros de datos locales de Microsoft no sea óptima para el modelo de conectividad universal.
  
**Figura 7: Ejemplo de una organización distribuidos geográficamente que usa una sola conexión ExpressRoute**

![Figura 7: Ejemplo de una organización distribuidos geográficamente que usa una sola conexión ExpressRoute](media/Network-Poster/MSNet1.png)
  
La figura 7 muestra una organización con dos ubicaciones, la ubicación 1 en el noroeste de Estados Unidos y la ubicación 2 en el noreste. Están conectados por un proveedor WAN universal. Esta organización tiene también una conexión de ExpressRoute a una ubicación de emparejamiento de Microsoft de la costa oeste. El tráfico de la ubicación 2 en el noreste destinado a un centro de datos de la costa este debe atravesar toda la red WAN de la organización hasta llegar a la costa oeste, a la ubicación de emparejamiento de Microsoft, y luego volver a recorrer todo el país por la red en la nube de Microsoft hasta llegar al centro de datos de la costa este.
  
Para lograr una entrega óptima, use varias conexiones de ExpressRoute a ubicaciones regionales de emparejamiento en la nube de Microsoft. 
  
**Figura 8: El uso de varias conexiones de ExpressRoute para la entrega óptima en centros de datos regionales**

![Figura 8: El uso de varias conexiones de ExpressRoute para la entrega óptima en centros de datos regionales](media/Network-Poster/MSNet2.png)
  
La figura 8 muestra la misma organización con dos conexiones de ExpressRoute, una para cada ubicación, a ubicaciones de emparejamiento de Microsoft locales de una región. En esta configuración, el tráfico de la ubicación 2 en el noreste destinado a un centro de datos de la costa este va directamente a una ubicación de emparejamiento de la costa este, a la red en la nube de Microsoft, y luego al centro de datos de la costa este.
  
Varias conexiones de ExpressRoute pueden proporcionar:
  
- Mejor rendimiento a ubicaciones de centros de datos de Microsoft locales de una región.
    
- Mayor disponibilidad en la nube de Microsoft cuando una conexión local de ExpressRoute deje de estar disponible.
    
Esto funciona bien con las organizaciones que están en el mismo continente. Sin embargo, el tráfico a los centros de datos de Microsoft que están fuera del continente de la organización viaja a través de Internet.
  
En el caso del tráfico intercontinental que va por la red en la nube de Microsoft, debe usar conexiones de ExpressRoute Premium.
  
### <a name="expressroute-premium"></a>ExpressRoute Premium

En el caso de las organizaciones que se distribuyen globalmente en varios continentes, puede usar ExpressRoute Premium. 
  
Con ExpressRoute Premium, puede llegar a cualquier centro de datos de Microsoft de cualquier continente y desde cualquier ubicación de emparejamiento de Microsoft de cualquier continente. El tráfico entre continentes se transmite a través de la red en la nube de Microsoft.
  
Con varias conexiones de ExpressRoute Premium, podemos conseguir:
  
- Mejor rendimiento en centros de datos de Microsoft locales de un continente.
    
- Mayor disponibilidad en la nube de Microsoft global cuando una conexión local de ExpressRoute deje de estar disponible.
    
ExpressRoute Premium es necesario para las conexiones de ExpressRoute basadas en Office 365. Pero no supone un coste adicional para las empresas que tienen 500 usuarios con licencia o más.
  
**Figura 9: La red mundial en la nube de Microsoft**

![Figura 9: La red mundial en la nube de Microsoft](media/Network-Poster/MSNet3.png)
  
La figura 9 muestra un diagrama lógico de la red mundial en la nube de Microsoft, con redes que abarcan los continentes y las regiones del mundo y sus interconexiones. Cuando cada parte de la red en la nube de Microsoft está en un continente, una empresa global crea conexiones de ExpressRoute Premium desde sus oficinas concentradoras regionales a ubicaciones de emparejamiento de Microsoft locales.
  
En el caso de una oficina regional, el tráfico adecuado de Office 365 que va a:
  
- Centros de datos de Office 365 continentales viaja a través de la red en la nube de Microsoft dentro del continente.
    
- Centros de datos de Office 365 en otro continente viaja a través de la red intercontinental en nube de Microsoft.
    
Para más información, visite:
  
- [Aprendizaje de Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer/)
    
- [Planear la red y ajustar el rendimiento de Office 365](https://aka.ms/tune)
    
- [Administración del rendimiento de Office 365](https://mva.microsoft.com/en-US/training-courses/office-365-performance-management-8416)
    
## <a name="expressroute-options"></a>Opciones de ExpressRoute

También puede incorporar las opciones siguientes a la implementación de ExpressRoute:
  
- **Seguridad en el perímetro:** para proporcionar seguridad avanzada en el tráfico enviado y recibido a través de la conexión de ExpressRoute, como la inspección del tráfico o la detección de intrusiones y malware, coloque las aplicaciones de seguridad en la ruta de acceso del tráfico dentro de la red perimetral o en el perímetro de la intranet.
    
    Tráfico de Internet para máquinas virtuales: para impedir que las máquinas virtuales de Azure inicien el tráfico directamente con ubicaciones de Internet, anuncie la ruta predeterminada a Microsoft. El tráfico de Internet se enruta a través de la conexión de ExpressRoute y a través de los servidores proxy locales. El tráfico de las máquinas virtuales de Azure a los servicios PaaS de Azure o a Office 365 se vuelve a enrutar a través de la conexión de ExpressRoute.
    
- **Optimizadores de WAN:** puede implementar optimizadores de WAN a ambos lados de una conexión de emparejamiento privada para una red virtual de Azure entre locales (VNet). Dentro de la VNet de Azure, use una aplicación de red del optimizador de WAN de Azure Marketplace y el enrutamiento definido por el usuario para enrutar el tráfico a través de la aplicación.
    
- **Calidad de servicio:** use valores de Punto de código de servicios diferenciados (DSCP) en el encabezado IPv4 del tráfico para marcarlo para voz, vídeo/interactivo o entrega de mejor esfuerzo. Esto es especialmente importante en la relación de emparejamiento de Microsoft y en el tráfico de Skype Empresarial Online.
    
Consulte estos recursos adicionales para obtener más información:
  
- [ExpressRoute para Office 365](https://aka.ms/expressrouteoffice365)
    
- [Aprendizaje de Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer/)
    
- [ExpressRoute para Azure](https://azure.microsoft.com/services/expressroute/)
    
## <a name="next-step"></a>Paso siguiente

[Diseño de redes para SaaS de Microsoft](designing-networking-for-microsoft-saas.md)

## <a name="see-also"></a>Ver también

[Microsoft Cloud Networking para arquitectos profesionales](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

