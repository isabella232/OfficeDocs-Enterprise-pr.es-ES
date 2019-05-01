---
title: Administración de la conectividad de ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/13/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365_Setup
search.appverid:
- MET150
- BCS160
ms.assetid: e4468915-15e1-4530-9361-cd18ce82e231
description: ExpressRoute para Office 365 ofrece una ruta de acceso alternativa para llegar a varios servicios de Office 365 sin necesidad de que todo el tráfico llegue a Internet. Aunque la conexión a Internet con Office 365 todavía es necesaria, las rutas específicas que Microsoft anuncia a través de BGP a la red hacen que se prefiera el circuito de ExpressRoute directo a menos que haya otras configuraciones en la red. Las tres áreas comunes que puede configurar para administrar este enrutamiento incluyen el filtrado de prefijos, la seguridad y el cumplimiento.
ms.openlocfilehash: 5345c4067f4ecf9b1b1bc1a0ad20d6e1f5273f65
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487736"
---
# <a name="managing-expressroute-for-office-365-connectivity"></a>Administración de la conectividad de ExpressRoute para Office 365

ExpressRoute para Office 365 ofrece una ruta de acceso alternativa para llegar a varios servicios de Office 365 sin necesidad de que todo el tráfico llegue a Internet. Aunque la conexión a Internet con Office 365 todavía es necesaria, las rutas específicas que Microsoft anuncia a través de BGP a la red hacen que se prefiera el circuito de ExpressRoute directo a menos que haya otras configuraciones en la red. Las tres áreas comunes que puede configurar para administrar este enrutamiento incluyen el filtrado de prefijos, la seguridad y el cumplimiento.
  
> [!NOTE]
> Microsoft cambió el modo en que se revisó el dominio de enrutamiento de emparejamiento de Microsoft para Azure ExpressRoute. A partir del 31 de julio de 2017, todos los clientes de Azure ExpressRoute pueden habilitar el emparejamiento de Microsoft directamente desde la consola de administración de Azure o a través de PowerShell. Después de habilitar el emparejamiento de Microsoft, cualquier cliente puede crear filtros de ruta para recibir anuncios de ruta BGP para las aplicaciones de participación del cliente de Dynamics 365 (anteriormente conocidas como CRM Online). Los clientes que necesiten Azure ExpressRoute para Office 365 deben obtener una revisión de Microsoft antes de que puedan crear filtros de ruta para Office 365. Póngase en contacto con su equipo de cuentas de Microsoft para obtener información sobre cómo solicitar una revisión para habilitar Office 365 ExpressRoute. Las suscripciones no autorizadas que intenten crear filtros de ruta para Office 365 recibirán un [mensaje de error](https://support.microsoft.com/kb/3181709)
  
## <a name="prefix-filtering"></a>Filtrado de preFijos

Microsoft recomienda que los clientes acepten todas las rutas BGP, tal y como se anuncian en Microsoft, las rutas que se han sometido a un proceso de revisión y validación rigurosos eliminando los beneficios de los controles. ExpressRoute ofrece de forma nativa los controles recomendados, como la propiedad del prefijo de IP, la integridad y la escala, sin filtrado de ruta entrante en el lado del cliente.
  
Si requiere validación adicional de la propiedad de ruta a través del emparejamiento público de ExpressRoute, puede comprobar las rutas anunciadas en la lista de todos los prefijos IP IPv4 e IPv6 que representan los [intervalos IP públicos de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602). Estos intervalos cubren el espacio de direcciones completo de Microsoft y no cambian con frecuencia, lo que proporciona un conjunto de intervalos fiable para filtrar que también proporciona protección adicional a los clientes que preocupan que las rutas que no pertenecen a Microsoft se pierdan en su entorno. En caso de que se produzca un cambio, se realizará el día 1 del mes y el número de versión en la sección **detalles** de la página cambiará cada vez que se actualice el archivo.
  
Hay varios motivos para evitar el uso de las [direcciones URL de Office 365 e intervalos de direcciones IP](https://aka.ms/o365endpoints) para la generación de listas de filtros de prefijos. Incluidos los siguientes:
  
- Los prefijos de Office 365 IP experimentan una gran cantidad de cambios con frecuencia.

- Los intervalos de direcciones IP y URL de Office 365 están diseñados para administrar las listas de permitidos de firewall y la infraestructura de proxy, no el enrutamiento.

- Las direcciones URL y los intervalos de direcciones IP de Office 365 no cubren otros servicios de Microsoft que puedan estar en el ámbito de las conexiones de ExpressRoute.

| |
|**Opción**|**Complejidad**|**Control de cambios**|
|:-----|:-----|:-----|
|Aceptar todas las rutas de Microsoft  <br/> |**Bajo:** El cliente se basa en los controles de Microsoft para asegurarse de que todas las rutas son propiedad de forma adecuada.  <br/> |Ninguno  <br/> |
|Filtrar superredes de Microsoft propiedad  <br/> |**Medio:** El cliente implementa listas resumidas de filtros de prefijo para permitir solo las rutas de propiedad de Microsoft.  <br/> |Los clientes deben asegurarse de que las actualizaciones poco frecuentes se reflejan en los filtros de ruta.  <br/> |
|Filtrar intervalos IP de Office 365  <br/> [!CAUTION] No recomendado
|**Alto:** El cliente filtra las rutas basándose en prefijos IP 365 de Office definidos.  <br/> |Los clientes deben implementar un proceso de administración de cambios sólido para las actualizaciones mensuales.  <br/> [!CAUTION] Esta solución requiere cambios significativos en el curso. Es probable que los cambios no implementados en tiempo se produzcan en una interrupción del servicio.   |

La conexión a Office 365 mediante Azure ExpressRoute se basa en anuncios BGP de subredes IP específicas que representan redes en las que se implementan los puntos de conexión de 365 de Office. Debido a la naturaleza global de Office 365 y al número de servicios que componen Office 365, los clientes suelen tener la necesidad de administrar los anuncios que aceptan en su red. Si le preocupa el número de prefijos anunciados en el entorno, la característica de [comunidad BGP](https://support.office.com/article/Using-BGP-communities-in-ExpressRoute-for-Office-365-scenarios-preview-9ac4d7d4-d9f8-40a8-8c78-2a6d7fe96099) le permitirá filtrar los anuncios a un conjunto específico de servicios de Office 365. Esta característica ahora está en versión preliminar.
  
Independientemente de cómo administre los anuncios de rutas BGP procedentes de Microsoft, no obtendrá ninguna exposición especial a los servicios de Office 365 en comparación con la conexión a Office 365 a través de un solo circuito de Internet. Microsoft mantiene los mismos niveles de seguridad, cumplimiento y rendimiento independientemente del tipo de circuito que use un cliente para conectarse a Office 365.
  
### <a name="security"></a>Seguridad

Microsoft recomienda que mantenga sus propios controles de perímetro de seguridad y red para las conexiones que vayan a y desde ExpressRoute y el emparejamiento de Microsoft, que incluye conexiones a y desde servicios de Office 365. Los controles de seguridad deben estar en su ubicación para las solicitudes de red que viajan desde la red a la red de Microsoft, así como a la red de Microsoft entrante en la red.
  
#### <a name="outbound-from-customer-to-microsoft"></a>Saliente de cliente a Microsoft
  
Cuando los equipos se conectan a Office 365, se conectan al mismo conjunto de extremos independientemente de si la conexión se realiza a través de un circuito de Internet o ExpressRoute. Independientemente del circuito que se use, Microsoft recomienda tratar los servicios de Office 365 como más confiables que los destinos de Internet genéricos. Los controles de seguridad salientes deben centrarse en los puertos y protocolos para reducir la exposición y minimizar el mantenimiento continuo. La información necesaria del puerto está disponible en el artículo de referencia de los [puntos de conexión de Office 365](https://aka.ms/o365endpoints) .
  
Para los controles agregados, puede usar el filtrado de nivel de FQDN dentro de la infraestructura de proxy para restringir o inspeccionar algunas o todas las solicitudes de red dirigidas a Internet u Office 365. El mantenimiento de la lista de FQDN a medida que se publican las características y el desarrollo de las ofertas de Office 365 requiere una administración de cambios y un seguimiento de cambios más sólidos en los [puntos de conexión de office 365](https://aka.ms/o365endpoints)publicados.
  
> [!CAUTION]
> Microsoft recomienda no confiar exclusivamente en prefijos IP para administrar la seguridad saliente a Office 365.

|**Opción**|**Complejidad**|**Control de cambios**|
|:-----|:-----|:-----|
|Sin restricciones  <br/> |**Bajo:** El cliente permite el acceso saliente sin restricciones a Microsoft.  <br/> |Ninguno  <br/> |
|Restricciones de puertos  <br/> |**Bajo:** El cliente restringe el acceso saliente a Microsoft por los puertos esperados.  <br/> |Poco frecuentes.  <br/> |
|Restricciones de FQDN  <br/> |**Alto:** El cliente restringe el acceso saliente a Office 365 en función de los FQDN publicados.  <br/> |Cambios mensuales.  <br/> |

#### <a name="inbound-from-microsoft-to-customer"></a>Entrante de Microsoft al cliente
  
Hay varios escenarios opcionales que requieren que Microsoft inicie conexiones a la red.
  
- ADFS durante la validación de contraseñas para el inicio de sesión.

- [ImplementaCiones híbridas de Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- Correo de un inquilino de Exchange Online a un host local.

- Envío de correo de SharePoint Online desde SharePoint Online a un host local.

- [Búsqueda híbrida federada de SharePoint](https://technet.microsoft.com/library/dn197174.aspx).

- [BCS híbrido de SharePoint](https://technet.microsoft.com/library/dn197239.aspx ).

- Federación [de Skype empresarial híbrido](https://technet.microsoft.com/en-us/library/jj205403.aspx) o [Skype empresarial](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype empresarial Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Microsoft recomienda que acepte estas conexiones a través del circuito de Internet en lugar de su circuito ExpressRoute para reducir la complejidad. Si su cumplimiento o necesidades de rendimiento dictan estas conexiones entrantes deben aceptarse a través de un circuito de ExpressRoute, se recomienda usar un firewall o un proxy inverso para el ámbito de las conexiones aceptadas. Puede usar los [puntos de conexión de Office 365](https://aka.ms/o365endpoints) para calcular los FQDN y prefijos IP correctos.
  
### <a name="compliance"></a>Cumplimiento

No confiamos en la ruta de enrutamiento que usa para ninguno de nuestros controles de cumplimiento. Independientemente de si se conecta a los servicios de Office 365 a través de un circuito de ExpressRoute o de Internet, los controles de cumplimiento no cambiarán. Debe revisar los diferentes niveles de certificación de seguridad y cumplimiento para Office 365 para averiguar la mejor opción para satisfacer las necesidades de su organización.
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/manageexpressroute365](https://aka.ms/manageexpressroute365)
  
## <a name="related-topics"></a>Temas relacionados

[Redes de entrega de contenido](content-delivery-networks.md)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Aprendizaje de Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer)
