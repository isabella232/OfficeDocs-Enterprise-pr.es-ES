---
title: Uso de las Comunidades BGP en ExpressRoute para escenarios de Office 365
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
description: 'Conectarse a Office 365 utilizando ExpressRoute de Azure se basa en anuncios BGP de subredes IP específicas que representan las redes donde se implementan los extremos de Office 365. Debido a la naturaleza global de Office 365 y el número de servicios que constituyen Office 365, los clientes a menudo tienen una necesidad para administrar los anuncios que se aceptan en su red. Reducir el número de subredes IP; conoce como prefijos IP en el resto de este artículo, que se alinea con la terminología de administración de red BGP, sirve los siguientes objetivos-end para los clientes:'
ms.openlocfilehash: c6e40dc29df55aa87e8d40c6203100fa1e7ad38f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542724"
---
# <a name="using-bgp-communities-in-expressroute-for-office-365-scenarios"></a>Uso de las Comunidades BGP en ExpressRoute para escenarios de Office 365

Conectarse a Office 365 utilizando ExpressRoute de Azure se basa en anuncios BGP de subredes IP específicas que representan las redes donde se implementan los extremos de Office 365. Debido a la naturaleza global de Office 365 y el número de servicios que constituyen Office 365, los clientes a menudo tienen una necesidad para administrar los anuncios que se aceptan en su red. Reducir el número de subredes IP; conoce como prefijos IP en el resto de este artículo, que se alinea con la terminología de administración de red BGP, sirve los siguientes objetivos-end para los clientes:
  
- **Administrar los prefijos numéricos de IP anunciados aceptados** - los clientes que tienen una infraestructura de red interna o de operador de la red que sólo admite un número limitado de prefijos IP y los clientes que tienen un operador de la red que los cargos de aceptación de prefijos por encima de un número limitado se va a evaluar el número total de prefijos ya ha anunciado a su red y seleccione qué aplicaciones de Office 365 son más adecuadas para ExpressRoute.

- **Administrar la cantidad de ancho de banda necesario en el circuito de Azure ExpressRoute** - es posible que los clientes desean controlar la envolvente de ancho de banda de los servicios de Office 365 a través de la ruta de acceso de ExpressRoute frente a la ruta de acceso de Internet. Esto permite a los clientes reservar ancho de banda de ExpressRoute de determinadas aplicaciones como Skype para la empresa y enrutar las aplicaciones de Office 365 restantes a través de la ruta de acceso de Internet.

Para ayudar a los clientes con estos objetivos, los prefijos de Office 365 IP que se anuncian a través de ExpressRoute se etiquetan con valores de la Comunidad BGP específicos de servicio como se muestra en el ejemplo siguiente.
  
> [!NOTE]
> Puede esperar cierto tráfico de red asociado con otras aplicaciones que se deben incluir en el valor de la Comunidad. Este es el comportamiento previsto para un Software global como un servicio que ofrece con centros de datos y los servicios compartidos. Esto se ha minimizado siempre que sea posible con los objetivos de dos anteriores, administración de recuento de prefijo o ancho de banda en mente.

|**Servicio**|**Valor de la Comunidad BGP**|**Notas**|
|:-----|:-----|:-----|
|Exchange\*  <br/> |12076:5010  <br/> |Incluye los servicios de Exchange y elevación de privilegios\*  <br/> |
|SharePoint\*  <br/> |12076:5020  <br/> |SharePoint Online  <br/> |
|Skype para la empresa\*  <br/> |12076:5030  <br/> |Skype Empresarial Online  <br/> |
|otros servicios de Office 365\*  <br/> |12076:5100  <br/> |Incluye Azure Active Directory (escenarios de autenticación y la sincronización de Active Directory), así como servicios de Portal de Office 365  <br/> |
|\*El ámbito de los escenarios de servicio incluidos en ExpressRoute se documenta en el artículo de [los extremos de Office 365](https://aka.ms/o365endpoints) .  <br/> \*\*Servicios adicionales y los valores de la Comunidad BGP se pueden agregar en el futuro. [Vea la lista actual de las Comunidades BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/).<br/> |

## <a name="what-are-the-most-common-scenarios-for-using-bgp-communities"></a>¿Cuáles son los escenarios más comunes para el uso de las Comunidades BGP?

Los clientes pueden usar Comunidades BGP regular grupos de prefijos IP que se aceptan por su red a través de ExpressRoute de Azure, así que influyen en el recuento total de prefijo IP y sobre ancho de banda esperado de determinados servicios de Office 365. Es importante comprender que todos los Office 365 requerirá que el tráfico, independientemente de la utilización de Azure ExpressRoute o comunidades de BGP enlazados a internet. Los siguientes tres escenarios son los usos más comunes de esta funcionalidad.
  
### <a name="scenario-1-minimizing-the-number-of-office-365-ip-prefixes"></a>Escenario 1: Minimizar el número de prefijos de IP de Office 365

Contoso Corporation es una empresa de 50.000 persona que actualmente usa Office 365 para Exchange Online y SharePoint Online. En la revisión de ExpressRoute requisitos de que Contoso determina sus dispositivos de red en muchas ubicaciones regionales no pueden controlar los tamaños de tabla enrutamiento por encima de 100 entradas de ruta adicionales. Contoso había revisado el número total de prefijos IP que ExpressRoute sería anunciar para el conjunto completo de servicios de Office 365 y concluye que supere los 100. Para mantenerse por debajo del 100 entradas de ruta adicionales, el uso de ExpressRoute para Office 365 al acaba SharePoint Online BGP Comunidad valor, 12076:5020, recibido a través de Microsoft ExpressRoute interconexión los ámbitos de Contoso.

|**Etiqueta de la Comunidad BGP utilizada**|**Funcionalidad se pueden enrutar a través de ExpressRoute de Azure**|**Rutas de Internet necesarias**|
|:-----|:-----|:-----|
|SharePoint  <br/> (12076:5020)  <br/> |SharePoint Online &amp; OneDrive para la empresa  <br/> | DNS, CRL, &amp; CDN solicitudes  <br/>  Todos los demás servicios de Office 365 específicamente no se admite a través de ExpressRoute de Azure  <br/>  Todos los demás servicios de nube de Microsoft  <br/>  Portal de Office 365, autenticación de Office 365, &amp; Office Online  <br/>  Exchange Online, Exchange Online Protection y Skype para la empresa en línea  <br/> |

> [!NOTE]
> Para lograr menores recuentos de prefijo para cada servicio, se aplicarán durante una cantidad mínima de superposición entre los servicios. Este es el comportamiento esperado.
  
### <a name="scenario-2-scoping-expressroute-and-internal-bandwidth-use-to-some-office-365-services"></a>Escenario 2: ExpressRoute de alcance y ancho de banda interno se usan para algunos servicios de Office 365

Fabrikam Inc., una empresa multinacional grande con una red heterogénea distribuida, es un suscriptor de muchos servicios de Office 365, incluidos; Exchange Online, SharePoint Online y Skype para la empresa en línea. Infraestructura de enrutamiento interno de Fabrikam puede administrar miles de prefijos IP en sus tablas de enrutamiento; Sin embargo, Fabrikam sólo desea aprovisionar ExpressRoute y ancho de banda interno para las aplicaciones de Office 365 más sensible al rendimiento de la red y usar su ancho de banda de Internet existente para todas las demás aplicaciones de Office 365.
  
Por ese motivo, los ámbitos de Fabrikam su ancho de banda de Azure ExpressRoute acaba Skype para valor de comunidad BGP en línea de negocio, 12076:5030, recibido a través de Microsoft ExpressRoute interconexión. El tráfico de red restante asociado a Office 365 continuará utilizando los puntos de salida de internet.

|**Etiqueta de la Comunidad BGP utilizada**|**Funcionalidad se pueden enrutar a través de ExpressRoute de Azure**|**Rutas de Internet necesarias**|
|:-----|:-----|:-----|
|Skype Empresarial  <br/> (12076:5030)  <br/> |Skype SIP señalización, descargas, uso compartido de voz, vídeo y escritorio  <br/> | DNS, CRL, &amp; CDN solicitudes  <br/>  Todos los demás servicios de Office 365 específicamente no se admite a través de ExpressRoute de Azure  <br/>  Todos los demás servicios de nube de Microsoft  <br/>  Portal de Office 365, autenticación de Office 365, &amp; Office Online  <br/>  Skype para telemetría empresarial, sugerencias rápidas de Skype cliente, la conectividad de mensajería instantánea pública  <br/>  Exchange Online, Exchange Online Protection y SharePoint Online  <br/> |

### <a name="scenario-3-scoping-azure-expressroute-for-office-365-services-only"></a>Escenario 3: Ámbito de Azure ExpressRoute para sólo los servicios de Office 365

Woodgrove Bank es un cliente de varios servicios de nube de Microsoft, incluidos Office 365. Después de evaluar su red capacidad y el consumo de Woodgrove Bank decide implementar Azure ExpressRoute como la ruta de acceso preferida para los servicios compatibles de Office 365. Las tablas de enrutamiento pueden admitir el conjunto completo de prefijos de IP de Office 365 y los circuitos de Azure ExpressRoute que ha aprovisionado admiten todas las necesidades de ancho de banda y latencia proyectadas.
  
Para asegurar el tráfico de red asociado con los servicios de nube de Microsoft distinta de la utilización de ExpressRoute para Office 365 a todos los prefijos IP de los ámbitos de Office 365, Woodgrove Bank cuente con valores de la Comunidad BGP específicos de Office 365, 12076:5010, 12076:5020, 12076:5030, 12076:5100.

|**Etiqueta de la Comunidad BGP utilizada**|**Funcionalidad se pueden enrutar a través de ExpressRoute de Azure**|**Rutas de Internet necesarias**|
|:-----|:-----|:-----|
|Exchange, Skype para la empresa, SharePoint, &amp; otros servicios  <br/> (12076:5010, 12076:5020, 12076:5030, 12076:5100)  <br/> |Exchange Online &amp; Exchange Online Protection  <br/> SharePoint Online &amp; OneDrive para la empresa  <br/> Skype SIP señalización, descargas, uso compartido de voz, vídeo y escritorio  <br/> Portal de Office 365, autenticación de Office 365, &amp; Office Online  <br/> | DNS, CRL, &amp; CDN solicitudes  <br/>  Todos los demás servicios de Office 365 específicamente no se admite a través de ExpressRoute de Azure  <br/>  Todos los demás servicios de nube de Microsoft  <br/> |

## <a name="key-planning-considerations-to-using-bgp-communities"></a>Clave de planeación de consideraciones para usar BGP Comunidades

Los clientes que elija para aprovechar las ventajas de las Comunidades BGP para influir en cómo ExpressRoute se ha anunciado y propagarse a través de la red del cliente deben tener en cuenta las siguientes consideraciones:
  
- Al usar las Comunidades BGP en el diseño de la red es importante garantizar la simetría de la ruta se mantiene. En algunos casos, la adición o eliminación de las Comunidades BGP puede crear una situación donde enrutamiento simétrico se interrumpe y se debe actualizar la configuración de enrutamiento para volver a establecer el enrutamiento simétrico.

- Ámbito de Azure ExpressRoute con los valores de la Comunidad BGP es una acción del cliente. Microsoft anuncia todos los prefijos IP asociadas con la relación de interconexión independientemente de cualquier ámbito configurado por el cliente.

- ExpressRoute Azure no admite todas las acciones de red de Microsoft en función del cliente asignado a las Comunidades BGP.

- Los prefijos IP utilizados por Office 365are sólo marcan con valores de la Comunidad BGP específicos de servicio, no se admiten determinadas Comunidades BGP de ubicación. Servicios de Office 365 son globales en naturaleza, filtrado basados en la ubicación del inquilino de prefijos o no es compatible con datos dentro de la nube de Office 365. El enfoque recomendado consiste en configurar la red para coordinar la más corta o la ruta de acceso de red preferida de ubicación de red del usuario en la red global de Microsoft, independientemente de la ubicación física de la dirección IP del servicio de Office 365 solicitada.

- Los prefijos IP incluidos en cada valor de la Comunidad BGP representan una subred que contiene las direcciones IP para la aplicación de Office 365 asociada con el valor. En algunos casos, más de una aplicación de Office 365 tiene las direcciones IP en una subred resultante en un prefijo de IP existentes en más de un valor de la Comunidad. Esto es, aunque poco, comportamiento esperado debido a la fragmentación de asignación y no afecta a los objetivos de administración de recuento o ancho de banda de prefijo. Se recomienda usar el "permitir lo que necesita" los clientes enfocar en lugar de "Denegar lo que no se necesita" cuando aprovechando las Comunidades BGP para Office 365 minimizar el efecto.

- Uso de las Comunidades BGP no cambia la configuración necesaria para usar Office 365 o los requisitos de conectividad de red subyacente. Los clientes que desean tener acceso a Office 365 siguen siendo necesarios para poder tener acceso a Internet.

- Ámbito ExpressRoute de Azure con las Comunidades BGP sólo afecta a las rutas de que la red interna puede ver a través de la relación de interconexión de Microsoft. Es posible que necesite realizar configuraciones de nivel de aplicaciones adicionales, como el uso de una configuración de PAC o WPAD junto con el enrutamiento de ámbito.

- Además de usar Microsoft asignado a Comunidades BGP, los clientes pueden elegir asignar a sus propias comunidades BGP a prefijos de Office 365 IP aprendidos a través de ExpressRoute de Azure para influir en el enrutamiento interno. Un caso de uso más populares es asignar una comunidad BGP ubicación basada en todas las rutas aprendidas a través de cada ExpressRoute determinado interconexión ubicación y, a continuación, usar esa información en dirección descendente en la red del cliente para coordinar la más corta o preferida en ruta de acceso de red en Red de Microsoft. El uso del cliente asignado a Comunidades BGP con ExpressRoute para escenarios de Office 365 está fuera del ámbito de control de Microsoft o la visibilidad.

Éste es un vínculo corto que puede usar para volver: [https://aka.ms/bgpexpressroute365](https://aka.ms/bgpexpressroute365).
  
## <a name="related-topics"></a>Temas relacionados

[Conectividad de red a Office 365](network-connectivity.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Calidad de medios y el rendimiento de conectividad de red en Skype para la empresa en línea](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[ExpressRoute y QoS en Skype para la empresa en línea](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flujo de llamadas de uso ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Implementación de ExpressRoute para Office 365](implementing-expressroute.md)
  
[Soporte técnico para Comunidades BGP](https://azure.microsoft.com/documentation/articles/expressroute-routing/)
  
[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)
  
[Aprendizaje de Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer)
