---
title: Uso de comunidades BGP en ExpressRoute para Office 365 escenarios
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099
description: 'La conexión a Office 365 mediante Azure ExpressRoute se basa en anuncios BGP de subredes IP específicas que representan redes en las que se implementan los puntos de conexión de 365 de Office. Debido a la naturaleza global de Office 365 y al número de servicios que constituyen Office 365, los clientes suelen tener la necesidad de administrar los anuncios que aceptan en su red. Reducir el número de subredes IP; conocido como prefijos IP en el resto de este artículo, para alinearse con la terminología de administración de red BGP, atiende los siguientes objetivos finales para los clientes:'
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490926"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Uso de comunidades BGP en ExpressRoute para Office 365 escenarios

La conexión a Office 365 mediante Azure ExpressRoute se basa en anuncios BGP de subredes IP específicas que representan redes en las que se implementan los puntos de conexión de 365 de Office. Debido a la naturaleza global de Office 365 y al número de servicios que constituyen Office 365, los clientes suelen tener la necesidad de administrar los anuncios que aceptan en su red. Reducir el número de subredes IP; conocido como prefijos IP en el resto de este artículo, para alinearse con la terminología de administración de red BGP, atiende los siguientes objetivos finales para los clientes:
  
- **Administrar el número** de prefijos IP anunciados admitidos: los clientes que tienen una infraestructura de red interna o un operador de red que solo admiten un número limitado de prefijos IP y clientes que tienen un operador de red que cobra por aceptar prefijos por encima de un número limitado se desea evaluar el número total de prefijos ya anunciados en su red y seleccionar qué aplicaciones de Office 365 son las más adecuadas para ExpressRoute.

- **Administrar la cantidad de ancho de banda necesario en el circuito de Azure ExpressRoute** : es posible que los clientes deseen controlar el sobre de ancho de banda de los servicios de Office 365 a través de la ruta de acceso de ExpressRoute frente a la ruta de Internet. Esto permite a los clientes reservar ancho de banda de ExpressRoute para aplicaciones específicas como Skype empresarial y enrutar las aplicaciones de Office 365s restantes a través de la ruta de Internet.

Para ayudar a los clientes con estos objetivos, los prefijos IP de Office 365 que se anuncian a través de ExpressRoute se etiquetan con valores de comunidad BGP específicos del servicio, como se muestra en el ejemplo siguiente.
  
> [!NOTE]
> Es de esperar que parte del tráfico de red asociado con otras aplicaciones se incluya en el valor de la comunidad. Este es el comportamiento previsto para un software global como una oferta de servicio con servicios compartidos y centros de trabajo. Esto se ha minimizado en el caso de que sea posible, teniendo en cuenta las dos metas anteriores, la administración del número de prefijos y/o el ancho de banda.

|**Servicio**|**Valor de comunidad BGP**|**Notas**|
|:-----|:-----|:-----|
|bolsa\*  <br/> |12076:5010  <br/> |Incluye servicios de Exchange y EOP\*  <br/> |
|SharePoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype empresarial\*  <br/> |12076:5030  <br/> |Skype Empresarial Online  <br/> |
|otros servicios de Office 365\*  <br/> |12076:5100  <br/> |Incluye Azure Active Directory (escenarios de autenticación y sincronización de directorios) y Office 365 Portal Services  <br/> |
|\*El ámbito de los escenarios de servicio incluidos en ExpressRoute está documentado en el artículo [puntos de conexión de Office 365](https://aka.ms/o365endpoints) .  <br/> \*\*Los servicios adicionales y los valores de comunidad BGP se pueden agregar en el futuro. [Vea la lista actual de comunidades BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/).  <br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>¿Cuáles son los escenarios más comunes para usar comunidades BGP?

Los clientes pueden usar las comunidades BGP para regular los grupos de prefijos IP aceptados por su red a través de Azure ExpressRoute, lo que influye en el número total de prefijos IP y en el envolvente de ancho de banda esperado de determinados servicios de Office 365. Es importante comprender que todo Office 365 necesitará tráfico de enlace a Internet independientemente del uso de Azure ExpressRoute o de las comunidades BGP. Los tres escenarios siguientes son los usos más comunes de esta funcionalidad.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Escenario 1: minimizar el número de prefijos IP de Office 365

Contoso Corporation es una compañía 50.000 persona que actualmente usa Office 365 para Exchange Online y SharePoint Online. Al revisar los requisitos de ExpressRoute, contoso determina los dispositivos de red en muchas ubicaciones regionales no se pueden controlar los tamaños de las tablas de enrutamiento por encima de 100 entradas de ruta adicionales. Contoso revisó el número total de prefijos IP que ExpressRoute anunciaría en el conjunto completo de servicios de Office 365 y llegó a la conclusión de que supera 100. Para permanecer en las entradas de ruta adicionales de 100, Contoso tiene como objetivo el uso de ExpressRoute para Office 365 solo para el valor de la comunidad BGP de SharePoint Online, 12076:5020, recibido a través de emparejamiento de Microsoft ExpressRoute.

|**Etiqueta de comunidad BGP usada**|**Funcionalidad enrutable a través de Azure ExpressRoute**|**Rutas de Internet requeridas**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive para la empresa  <br/> | Solicitudes de DNS, &amp; CRL o CDN  <br/>  Todos los demás servicios de Office 365 no son compatibles específicamente con Azure ExpressRoute  <br/>  Todos los demás servicios en la nube de Microsoft  <br/>  Office 365 portal, Office 365 Authentication, &amp; Office Online  <br/>  Exchange Online, Exchange Online Protection y Skype empresarial online  <br/> |

> [!NOTE]
> Para obtener recuentos de prefijos inferiores para cada servicio, se mantendrá una cantidad mínima de superposición entre los servicios. Este es el comportamiento previsto.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Escenario 2: ámbito de ExpressRoute y uso de ancho de banda interno para algunos servicios de Office 365

Fabrikam Inc, una gran empresa multinacional con una red heterogénea distribuida, es un suscriptor de varios servicios de Office 365, incluido el; Exchange Online, SharePoint Online y Skype empresarial online. La infraestructura de enrutamiento interno de Fabrikam puede administrar miles de prefijos IP en sus tablas de enrutamiento; sin embargo, Fabrikam solo quiere aprovisionar ExpressRoute y el ancho de banda interno para las aplicaciones de Office 365 que son más sensibles al rendimiento de red y usan el ancho de banda de Internet existente para todas las demás aplicaciones de Office 365.
  
Por ese motivo, Fabrikam asigna su ancho de banda de Azure ExpressRoute solo al valor de comunidad BGP de Skype empresarial online, 12076:5030, que se recibió a través del emparejamiento de Microsoft en ExpressRoute. El tráfico de red restante asociado con Office 365 sigue usando los puntos de salida de Internet.

|**Etiqueta de comunidad BGP usada**|**Funcionalidad enrutable a través de Azure ExpressRoute**|**Rutas de Internet requeridas**|
|:-----|:-----|:-----|
|Skype Empresarial  <br/> (12076:5030)  <br/> |Señalización SIP de Skype, descargas, voz, vídeo y uso compartido de escritorio  <br/> | Solicitudes de DNS, &amp; CRL o CDN  <br/>  Todos los demás servicios de Office 365 no son compatibles específicamente con Azure ExpressRoute  <br/>  Todos los demás servicios en la nube de Microsoft  <br/>  Office 365 portal, Office 365 Authentication, &amp; Office Online  <br/>  Telemetría de Skype empresarial, sugerencias rápidas del cliente de Skype, conectividad de mensajería instantánea pública  <br/>  Exchange Online, Exchange Online Protection y SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Escenario 3: ámbito de Azure ExpressRoute para Office 365 solo servicios

Woodgrove Bank es un cliente de varios servicios en la nube de Microsoft, incluido Office 365. Después de evaluar la capacidad de red y el consumo, Woodgrove Bank decide implementar Azure ExpressRoute como la ruta de acceso preferida para los servicios de Office 365 compatibles. Las tablas de enrutamiento pueden admitir el conjunto completo de prefijos IP de Office 365 y los circuitos de Azure ExpressRoute que han aprovisionado admiten todas las necesidades de ancho de banda y latencia proyectadas.
  
Para garantizar el tráfico de red asociado a los servicios en la nube de Microsoft que no sean Office 365, Woodgrove Bank tiene en cuenta el uso de ExpressRoute para Office 365 a todos los prefijos IP etiquetados con los valores de la comunidad BGP específicos de Office 365, 12076:5010, 12076:5020, 12076:5030 12076:5100.

|**Etiqueta de comunidad BGP usada**|**Funcionalidad enrutable a través de Azure ExpressRoute**|**Rutas de Internet requeridas**|
|:-----|:-----|:-----|
|Exchange, Skype empresarial, SharePoint, &amp; otros servicios  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive para la empresa  <br/> Señalización SIP de Skype, descargas, voz, vídeo y uso compartido de escritorio  <br/> Office 365 portal, Office 365 Authentication, &amp; Office Online  <br/> | Solicitudes de DNS, &amp; CRL o CDN  <br/>  Todos los demás servicios de Office 365 no son compatibles específicamente con Azure ExpressRoute  <br/>  Todos los demás servicios en la nube de Microsoft  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Consideraciones clave para la planeación del uso de comunidades BGP

Los clientes que optan por aprovechar las comunidades BGP para influir en la forma en que ExpressRoute se anuncia y se propagan a través de la red del cliente deben tener en cuenta las siguientes consideraciones:
  
- Al usar las comunidades BGP en el diseño de red, es importante asegurarse de que aún se mantenga la simetría de ruta. En algunos casos, la adición o eliminación de comunidades BGP puede crear una situación en la que el enrutamiento simétrico se rompe y la configuración de enrutamiento debe actualizarse para restablecer el enrutamiento simétrico.

- El ámbito de Azure ExpressRoute con valores de comunidad BGP es una acción del cliente. Microsoft publicará todos los prefijos IP asociados con la relación de emparejamiento independientemente de los ámbitos configurados por el cliente.

- Azure ExpressRoute no admite ninguna acción en la red de Microsoft basada en las comunidades BGP asignadas por el cliente.

- Los prefijos IP usados por Office 365are solo marcados con valores de comunidad BGP específicos de servicio, no se admiten las comunidades BGP específicas de la ubicación. Los servicios de Office 365 son de naturaleza global, los prefijos de filtrado basados en la ubicación del inquilino o los datos dentro de la nube de Office 365 no son compatibles. El enfoque recomendado es configurar la red para coordinar la ruta de red más corta o preferida desde la ubicación de red del usuario a la red global de Microsoft, independientemente de la ubicación física de la dirección IP del servicio de Office 365 están solicitando.

- Los prefijos IP incluidos en cada valor de comunidad BGP representan una subred que contiene las direcciones IP de la aplicación Office 365 asociada con el valor. En algunos casos, más de una aplicación de Office 365 tiene direcciones IP dentro de una subred, lo que da como resultado un prefijo IP en más de un valor de comunidad. Esto es normal, aunque rara, comportamiento debido a la fragmentación de asignación y no afecta al número de prefijos ni a los objetivos de administración de ancho de banda. Se recomienda a los clientes que usen el método "permitir los requisitos", en lugar de "denegar lo que no se necesita" cuando aprovechen las ventajas de las comunidades BGP para Office 365 para minimizar el efecto.

- El uso de comunidades BGP no cambia los requisitos de conectividad de red subyacentes ni la configuración necesaria para usar Office 365. Los clientes que quieran tener acceso a Office 365 siguen siendo necesarios para poder acceder a Internet.

- El ámbito de Azure ExpressRoute con comunidades BGP solo afecta a las rutas que la red interna puede ver a través de la relación de emparejamiento de Microsoft. Es posible que necesite realizar configuraciones de nivel de aplicación adicionales, como el uso de una PAC o una configuración de WPAD junto con el enrutamiento con ámbito.

- Además de usar las comunidades BGP asignadas por Microsoft, los clientes pueden elegir asignar sus propias comunidades BGP a los prefijos IP de Office 365 aprendidos a través de Azure ExpressRoute para influir en el enrutamiento interno. Un caso de uso popular es la asignación de una ubicación basada en la comunidad BGP a todas las rutas aprendidas a través de cada ubicación de emparejamiento ExpressRoute determinada y la posterior utilización de esa información en la red del cliente para coordinar la ruta de acceso de red más corta o preferida en Red de Microsoft. El uso de comunidades BGP asignadas por el cliente con ExpressRoute para Office 365 escenarios está fuera del ámbito del control o la visibilidad de Microsoft.

Este es un vínculo breve que puede usar para volver: [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365).
  
## <a name="related-topics"></a>Temas relacionados

[Conectividad de red a Office 365](network-connectivity.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute y QoS en Skype empresarial online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flujo de llamadas con ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implementación de ExpressRoute para Office 365](implementing-expressroute.md)
  
[Compatibilidad con comunidades BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)
  
[Aprendizaje de Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer)
