---
title: Enrutamiento con ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: En este artículo, obtenga información sobre los requisitos de enrutamiento, los circuitos y los dominios de enrutamiento de Azure ExpressRoute para su uso con Office 365.
ms.openlocfilehash: c8063d570744b3a5fd42328ed3940fe7477c25c9
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605232"
---
# <a name="routing-with-expressroute-for-office-365"></a>Enrutamiento con ExpressRoute para Office 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Para comprender correctamente el tráfico de enrutamiento a Office 365 mediante Azure ExpressRoute, necesitará una sólida visión de los [requisitos de enrutamiento de expressroute](https://azure.microsoft.com/documentation/articles/expressroute-routing/) principales y los [circuitos y dominios de enrutamiento de expressroute](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/). Estos diseñan los conceptos básicos para usar ExpressRoute en los que se basarán los clientes de Office 365.
  
Algunos de los elementos más importantes de los artículos anteriores que debe comprender son:
  
- Los circuitos de ExpressRoute no se asignan a una infraestructura física específica, sino que son una conexión lógica que Microsoft y un proveedor de emparejamiento realizan en su nombre en una única ubicación de emparejamiento.

- Hay una asignación 1:1 entre un circuito ExpressRoute y una clave s del cliente.

- Cada circuito puede admitir 2 relaciones de emparejamiento independientes (emparejamiento privado de Azure y emparejamiento de Microsoft); Office 365 requiere emparejamiento de Microsoft.

- Cada circuito tiene un ancho de banda fijo que se comparte entre todas las relaciones de emparejamiento.

- Las direcciones IPv4 públicas y públicas como números que se usarán para el circuito de ExpressRoute deben validarse como pertenecientes a usted o asignados exclusivamente por el propietario del intervalo de direcciones.

- Los circuitos virtuales de ExpressRoute son redundantes de forma global y siguen las prácticas estándar de enrutamiento BGP. Esta es la razón por la que recomendamos dos circuitos físicos por salida a su proveedor en una configuración activo/activo.

Consulte la [Página de preguntas más frecuentes](https://azure.microsoft.com/documentation/articles/expressroute-faqs/) para obtener más información sobre los servicios admitidos, los costos y los detalles de configuración. Consulte el [artículo ubicaciones de ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-locations/) para obtener información sobre la lista de proveedores de conectividad que ofrecen soporte de emparejamiento de Microsoft. También hemos grabado una serie de aprendizaje de [Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer) en Channel 9 para ayudarle a explicar los conceptos con mayor detalle.
  
## <a name="ensuring-route-symmetry"></a>Garantizar la simetría de rutas

Los servidores front-end de Office 365 son accesibles en Internet y ExpressRoute. Estos servidores prefieren volver a enrutar a los circuitos locales sobre ExpressRoute cuando ambos están disponibles. Debido a esto, existe la posibilidad de que se enrute la asimetría si el tráfico de la red prefiere enrutar los circuitos de Internet. Las rutas asimétricas son un problema porque los dispositivos que realizan una inspección de paquetes con seguimiento de estado pueden bloquear el tráfico de retorno que sigue a una ruta de acceso diferente a la de los paquetes de salida seguidos.
  
Independientemente de si inicia una conexión con Office 365 a través de Internet o ExpressRoute, el origen debe ser una dirección enrutable públicamente. Con muchos clientes que van directamente a Microsoft, tener direcciones privadas donde la duplicación es posible entre los clientes no es factible.
  
A continuación se muestran escenarios en los que se iniciarán las comunicaciones de Office 365 a la red local. Para simplificar el diseño de red, se recomienda enrutarlos a través de la ruta de Internet.
  
- Servicios SMTP, como correo de un inquilino de Exchange Online a un host local o el correo de SharePoint Online enviado desde SharePoint Online a un host local. El protocolo SMTP se usa de forma más amplia en la red de Microsoft que los prefijos de ruta compartidos en circuitos ExpressRoute y publicitarios los servidores SMTP locales sobre ExpressRoute provocarán errores con estos otros servicios.

- ADFS durante la validación de contraseñas para el inicio de sesión.

- [Implementaciones híbridas de Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- [Búsqueda híbrida federada de SharePoint](https://technet.microsoft.com/library/dn197174.aspx).

- [BCS híbrido de SharePoint](https://technet.microsoft.com/library/dn197239.aspx ).

- Federación [de Skype empresarial híbrido](https://technet.microsoft.com/library/jj205403.aspx) o [Skype empresarial](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype empresarial Cloud Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Para que Microsoft vuelva a enrutarse a la red para estos flujos de tráfico bidireccional, las rutas BGP a los dispositivos locales deben compartirse con Microsoft. Al anunciar prefijos de ruta a Microsoft a través de ExpressRoute, debe seguir estos procedimientos recomendados:

1) No anuncie el mismo prefijo de ruta de dirección IP pública a la Internet pública y a través de ExpressRoute. Se recomienda encarecidamente que los anuncios de prefijo de ruta BGP IP para Microsoft sobre ExpressRoute provienen de un intervalo que no se anuncia a Internet en absoluto. Si no es posible lograr esto debido al espacio de direcciones IP disponible, es esencial que anuncie un intervalo más específico sobre ExpressRoute que los circuitos de Internet.

2) Use grupos de direcciones IP NAT independientes por circuito de ExpressRoute y sepárelos con los de los circuitos de Internet.

3) Tenga en cuenta que cualquier ruta anunciada a Microsoft atraerá el tráfico de red de cualquier servidor de la red de Microsoft, no solo aquellos para los que las rutas se anuncian en la red a través de ExpressRoute. Solo anuncie las rutas a los servidores en los que los escenarios de enrutamiento estén definidos y comprensibles correctamente por el equipo. Anuncie prefijos de ruta de direcciones IP independientes en cada uno de los varios circuitos de ExpressRoute de la red.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Decidir qué aplicaciones y características se enrutan a través de ExpressRoute

Cuando configure una relación de emparejamiento con el dominio de enrutamiento de emparejamiento de Microsoft y esté aprobado para el acceso adecuado, podrá ver todos los servicios de PaaS y SaaS disponibles en ExpressRoute. Los servicios de Office 365 diseñados para ExpressRoute se pueden administrar con [comunidades BGP](https://aka.ms/bgpexpressroute365) o [filtros de ruta](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal).
  
Otras aplicaciones, como Office 365 video, es una aplicación de Office 365; sin embargo, Office 365 video consta de tres componentes diferentes, el portal, el servicio de streaming y la red de entrega de contenido. El portal se encuentra dentro de SharePoint Online, el servicio de streaming de Azure Media Services y la red de entrega de contenido reside en la red CDN de Azure. En la tabla siguiente se describen estos componentes.

|**Componente**|**Aplicación subyacente**|**¿Se incluye en la comunidad BGP de SharePoint Online?**|**Usar**|
|:-----|:-----|:-----|:-----|
|Portal de vídeo de Office 365  <br/> |SharePoint Online  <br/> |Sí  <br/> |Configuración, cargar  <br/> |
|Servicio de streaming de vídeo de Office 365  <br/> |Servicios multimedia de Azure  <br/> |No  <br/> |Servicio de streaming, usado en el caso de que el vídeo no esté disponible en la red CDN  <br/> |
|Red de entrega de contenido de vídeo de Office 365  <br/> |RED CDN de Azure  <br/> |No  <br/> |Origen principal de descarga/transmisión de vídeo. [Obtenga más información sobre la red de vídeo de Office 365](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e).  <br/> |

Cada una de las características de Office 365 que están disponibles con emparejamiento de Microsoft se enumeran en el [artículo de puntos de conexión de office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) por tipo de aplicación y FQDN. La razón para usar el FQDN en las tablas es permitir que los clientes administren el tráfico mediante archivos PAC u otras configuraciones de proxy, consulte nuestra guía para [administrar puntos de conexión de Office 365](https://aka.ms/manageo365endpoints) por ejemplo archivos PAC.
  
En algunas situaciones, hemos usado un dominio comodín donde uno o más subnombres secundarios se anuncian de forma diferente que el dominio comodín de nivel superior. Esto suele ocurrir cuando el carácter comodín representa una lista larga de servidores que se anuncian en ExpressRoute e Internet, mientras que un pequeño subconjunto de destinos solo se anuncia a Internet o al revés. Consulte las tablas siguientes para conocer dónde se encuentran las diferencias.
  
En esta tabla se muestran los FQDN comodín que se anuncian tanto a Internet como a Azure ExpressRoute junto con los sub-FQDN que se anuncian solo en Internet.

|**Dominio comodín anunciado para los circuitos de ExpressRoute e Internet**|**Sub-FQDN anunciado solo para circuitos de Internet**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |click.email.microsoftonline.com  <br/> portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> nexus.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> odc.officeapps.live.com  <br/> cdn.odc.officeapps.live.com  <br/> ols.officeapps.live.com  <br/> ocsredir.officeapps.live.com  <br/> ocws.officeapps.live.com  <br/> ocsa.officeapps.live.com  <br/> |

Por lo general, los archivos PAC están diseñados para enviar solicitudes de red a los extremos anunciados de ExpressRoute directamente al circuito y a todas las demás solicitudes de red al proxy. Si está configurando un archivo PAC como este, Redacte el archivo PAC en el siguiente orden:
  
1. Incluya los sub-FQDN de la columna dos de la tabla anterior en la parte superior del archivo PAC, enviando el tráfico hacia su proxy. Hemos creado un ejemplo de archivo PAC que puede usar en nuestro artículo sobre la [Administración de puntos de conexión de Office 365](https://aka.ms/manageexpressroute365).

2. Incluya todos los FQDN marcados como anunciados en ExpressRoute en [este artículo](https://aka.ms/o365endpoints) , debajo de la primera sección, envío del tráfico directamente a su circuito de ExpressRoute.

3. Incluya otros extremos de red o reglas por debajo de estas dos entradas, enviando el tráfico hacia el proxy.

En esta tabla se muestran los dominios comodín que se anuncian a los circuitos de Internet solo junto con los subfqdn que se anuncian a Azure ExpressRoute y a los circuitos de Internet. Para el archivo PAC anterior, los FQDN de la columna dos de la tabla siguiente se muestran como anunciados en ExpressRoute en el vínculo al que se hace referencia, lo que significa que se incluirán en el segundo grupo de entradas del archivo.

|**Dominio comodín anunciado solo para circuitos de Internet**|**Sub-FQDN anunciado para los circuitos de ExpressRoute e Internet**|
|:-----|:-----|
|\*. office.com  <br/> |\*. outlook.office.com  <br/> home.office.com  <br/> outlook.office.com  <br/> portal.office.com  <br/> <div style="display: inline">www.office.com</div>  <br/> |
|\*. office.net  <br/> |agent.office.net  <br/> |
|\*. office365.com  <br/> |outlook.office365.com  <br/> smtp.office365.com  <br/> |
|\*. outlook.com  <br/> |\*. protection.outlook.com  <br/> \*. mail.protection.outlook.com  <br/> detección automática: \<tenant\> . Outlook.com  <br/> |
|\*. windows.net  <br/> |login.windows.net  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Enrutamiento de tráfico de Office 365 a través de Internet y ExpressRoute

Para enrutar a la aplicación de Office 365 de su elección tendrá que determinar una serie de factores clave.
  
1. La cantidad de ancho de banda que necesitará la aplicación. Muestreo el uso existente es el único método confiable para determinar esto en su organización.

2. Qué ubicaciones de salida desea que el tráfico de red abandone la red. Debe planear la reducción de la latencia de red para la conectividad con Office 365, ya que esto afectará al rendimiento. Como Skype empresarial usa voz y vídeo en tiempo real, es particularmente susceptible a una mala latencia de la red.

3. Si desea que todos los o un subconjunto de sus ubicaciones de red aprovechen ExpressRoute.

4. Qué ubicaciones ofrece ExpressRoute su proveedor de red elegido.

Una vez que determine las respuestas a estas preguntas, puede aprovisionar un circuito de ExpressRoute que cumpla las necesidades de ancho de banda y ubicación. Para más información sobre Planeación de red, consulte la guía de ajuste de la red de [Office 365](https://aka.ms/tune) y el [caso práctico sobre cómo Microsoft controla la planeación del rendimiento de la red](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>Ejemplo 1: ubicación geográfica única
  
Este ejemplo es un escenario para una compañía ficticia denominada Trey Research que tiene una única ubicación geográfica.
  
Los empleados de Trey Research solo pueden conectarse a los servicios y sitios web de Internet que el Departamento de seguridad permite explícitamente en el par de servidores proxy salientes que se encuentran entre la red corporativa y su ISP.
  
Trey Research planea usar Azure ExpressRoute para Office 365 y reconoce que parte del tráfico, como el tráfico destinado a las redes de entrega de contenido, no podrá enrutar a través de ExpressRoute para la conexión de Office 365. Dado que todo el tráfico ya se enruta a los dispositivos de proxy de forma predeterminada, estas solicitudes seguirán funcionando como antes. Una vez que Trey Research determina que puede cumplir los requisitos de enrutamiento de Azure ExpressRoute, crea un circuito, configura el enrutamiento y vincula el nuevo circuito de ExpressRoute a una red virtual. Una vez que se ha implementado la configuración fundamental de Azure ExpressRoute, Trey Research usa el [#2 archivo PAC que publicamos](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) para enrutar el tráfico con datos específicos del cliente a través de ExpressRoute de Direct ExpressRoute para Office 365 conexiones.
  
Como se muestra en el siguiente diagrama, Trey Research puede satisfacer los requisitos para enrutar el tráfico de Office 365 a través de Internet y un subconjunto de tráfico a través de ExpressRoute usando una combinación de cambios de configuración de enrutamiento y de proxy saliente.
  
1. Mediante el [#2 archivo PAC que publicamos](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) para enrutar el tráfico a través de un punto de salida de Internet independiente para Azure ExpressRoute para Office 365.

2. Los clientes se configuran con una ruta predeterminada hacia los servidores proxy de Trey Research.

En este escenario de ejemplo, Trey Research usa un dispositivo de proxy de salida. De forma similar, es posible que los clientes que no usan Azure ExpressRoute para Office 365 deseen usar esta técnica para enrutar el tráfico en función del costo de inspeccionar el tráfico destinado a puntos de conexión de volumen muy conocidos.
  
Los FQDN de mayor volumen para Exchange Online, SharePoint Online y Skype empresarial online son los siguientes:
  
![Red perimetral del cliente de ExpressRoute](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- outlook.office365.com, outlook.office.com

- \<tenant-name\>. SharePoint.com, \<tenant-name\> -My.SharePoint.com, \<tenant-name\> - \<app\> . SharePoint.com

- \*. Lync.com junto con los intervalos IP para el tráfico no TCP

- \*broadcast.officeapps.live.com, \* Excel.officeapps.Live.com, \* onenote.officeapps.live.com, \* PowerPoint.officeapps.Live.com, \* view.officeapps.live.com, \* Visio.officeapps.Live.com, \* Word-Edit.officeapps.Live.com, \* Word-View.officeapps.Live.com, Office.Live.com

Obtenga más información sobre la [implementación y la administración de la configuración de proxy en Windows 8](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx) y [Asegúrese de que Office 365 no está limitado por el proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Con un solo circuito ExpressRoute, no hay alta disponibilidad para Trey Research. En el caso de que el par de dispositivos perimetrales redundantes de Trey que atienden la conectividad de ExpressRoute falle, no hay un circuito de ExpressRoute adicional para la conmutación por error. De este modo, Trey Research en un predicament como conmutación por error a Internet requerirá una reconfiguración manual y, en algunos casos, nuevas direcciones IP. Si Trey desea agregar alta disponibilidad, la solución más sencilla es agregar circuitos de ExpressRoute adicionales para cada ubicación y configurar los circuitos de forma activa/activa.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Enrutamiento de ExpressRoute para Office 365 con varias ubicaciones

El último escenario, enrutar el tráfico de Office 365 sobre ExpressRoute es la base para una arquitectura de enrutamiento aún más compleja. Independientemente del número de ubicaciones, el número de continentes en el que existen esas ubicaciones, el número de circuitos de ExpressRoute, etc., que pueden enrutar parte del tráfico a Internet y se requerirá tráfico sobre ExpressRoute.
  
Las preguntas adicionales que deben responderse a los clientes con varias ubicaciones en varias zonas geográficas son las siguientes:
  
1. ¿Necesita un circuito ExpressRoute en todas las ubicaciones? Si está usando Skype empresarial online o está preocupado por la sensibilidad de latencia de SharePoint Online o Exchange Online, se recomienda usar un par redundante de circuitos de ExpressRoute activos/activos en cada ubicación. Consulte la guía de conectividad de red y calidad de medios de Skype empresarial para obtener más información.

2. Si no hay un circuito ExpressRoute disponible en una región determinada, ¿cómo se debe enrutar el tráfico destinado a Office 365?

3. ¿Cuál es el mejor método para consolidar el tráfico en el caso de redes con muchas ubicaciones pequeñas?

Cada uno de estos plantea un desafío único que requiere que evalúe su propia red, así como las opciones disponibles de Microsoft.

|**Motivos**|**Componentes de red para evaluar**|
|:-----|:-----|
|Circuitos en más de una ubicación  <br/> |Se recomienda un mínimo de dos circuitos configurados de forma activa/activa.  <br/> Se deben comparar las necesidades de costo, latencia y ancho de banda.  <br/> Usar costo de ruta BGP, archivos PAC y NAT para administrar el enrutamiento con varios circuitos.  <br/> |
|Enrutamiento desde ubicaciones sin un circuito ExpressRoute  <br/> |Le recomendamos que la persona que inicia la solicitud para Office 365 se haya desformado de salida y resolución de DNS tan cerca de ella.  <br/> El reenvío de DNS se puede usar para permitir que las oficinas remotas detecten el extremo adecuado.  <br/> Los clientes de la oficina remota deben tener una ruta disponible que proporcione acceso al circuito de ExpressRoute.  <br/> |
|Consolidación de oficinas pequeñas  <br/> |El ancho de banda y el uso de datos disponibles deben compararse con precisión.  <br/> |

> [!NOTE]
> Microsoft preferirá ExpressRoute a través de Internet si la ruta está disponible independientemente de la ubicación física.
  
Cada una de estas consideraciones se debe tener en cuenta para cada red única. A continuación, se muestra un ejemplo.
  
### <a name="example-2-multi-geographic-locations"></a>Ejemplo 2: varias ubicaciones geográficas
  
Este ejemplo es un escenario para una compañía ficticia denominada Humongous Insurance que tiene varias ubicaciones geográficas.
  
Humongous Insurance está geográficamente disperso con oficinas en todo el mundo. Quieren implementar Azure ExpressRoute para Office 365 para mantener la mayor parte del tráfico de Office 365 en conexiones de red directas. Humongous Insurance también tiene oficinas en dos continentes adicionales. Los empleados de la oficina remota en los que ExpressRoute no es factible deberán redirigirse a uno o ambos de los medios principales para usar una conexión de ExpressRoute.
  
El principio guía es conseguir que el tráfico de Office 365 destinado a un centro de recursos de Microsoft sea lo más rápido posible. En este ejemplo, Humongous Insurance debe decidir si sus oficinas remotas deben enrutarse a través de Internet para llegar a un centro de información de Microsoft a través de cualquier conexión lo antes posible o si sus oficinas remotas deben enrutar a través de una red interna para obtener un centro de información de Microsoft a través de una conexión de ExpressRoute tan rápido como sea posible.
  
Los centros de proceso de Microsoft, las redes y la arquitectura de aplicaciones están diseñados para tomar comunicaciones en todo el mundo y atender a ellas de la forma más eficaz posible. Esta es una de las redes más grandes del mundo. Las solicitudes destinadas a Office 365 que permanecen en las redes de los clientes más tiempo de lo necesario no podrán aprovechar esta arquitectura.
  
En la situación de Humongous Insurance, deben continuar en función de las aplicaciones que quieran usar a través de ExpressRoute. Por ejemplo, si es un cliente de Skype empresarial online o tiene previsto aprovechar la conectividad de ExpressRoute cuando se conecta a reuniones externas de Skype empresarial online, el diseño recomendado en la guía de conectividad multimedia y calidad de medios de Skype empresarial online es aprovisionar un circuito de ExpressRoute adicional para la tercera ubicación. Esto puede ser más caro desde el punto de vista de la red; sin embargo, el enrutamiento de solicitudes de un continente a otro antes de entregarlas a un centro de recursos de Microsoft puede causar una experiencia deficiente o inutilizable durante las comunicaciones y las reuniones de Skype empresarial online.
  
Si Humongous Insurance no está usando o no tiene previsto aprovechar Skype empresarial online de ninguna manera, es posible que sea factible el enrutamiento del tráfico de red dirigido de Office 365 a un continente con una conexión de ExpressRoute, aunque puede provocar una latencia innecesaria o una congestión TCP. En ambos casos, se recomienda enrutar el tráfico de Internet destinado a Internet en el sitio local para aprovechar las ventajas de las redes de entrega de contenido de las que se basa Office 365.
  
![ExpressRoute, multi-geografía](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Cuando Humongous Insurance planea su estrategia multigeografía, hay varios aspectos que se deben tener en cuenta en cuanto al tamaño del circuito, el número de circuitos, la conmutación por error, etc.
  
Con ExpressRoute en una única ubicación donde varias regiones intentan usar el circuito, Humongous Insurance desea garantizar que las conexiones a Office 365 desde la oficina remota se envían a la oficina central de Office 365 Datacenter y se reciben en la ubicación de la sede central. Para ello, Humongous Insurance implementa el reenvío de DNS para reducir el número de viajes de ida y vuelta y búsquedas DNS necesarias para establecer la conexión adecuada con el entorno de Office 365 más cercano al punto de salida de Internet de la sede central. Esto evita que el cliente resuelva un servidor front-end local y garantiza que el servidor front-end al que se conecta la persona esté cerca de la oficina central donde Humongous Insurance está emparejamiento con Microsoft. También puede aprender a [asignar un reenviador condicional para un nombre de dominio](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx).
  
En este escenario, el tráfico de la oficina remota resolverá la infraestructura front-end de Office 365 en Norteamérica y aprovechará Office 365 para conectarse a los servidores back-end de acuerdo con la arquitectura de la aplicación Office 365. Por ejemplo, Exchange Online finalizaría la conexión en Norteamérica y esos servidores front-end se conectarían al servidor de buzones de correo back-end en cualquier lugar en el que residía el inquilino. Todos los servicios tienen un servicio de puerta frontal ampliamente distribuido compuesto por destinos de unidifusión y difusión por proximidad.
  
Si Humongous tiene oficinas principales en varios continentes, se recomienda un mínimo de dos circuitos activos/activos por región, a fin de reducir la latencia de aplicaciones confidenciales, como Skype empresarial online. Si todas las oficinas están en un solo continente o no usan la colaboración en tiempo real, tener un punto de salida consolidado o distribuido es una decisión específica del cliente. Cuando hay varios circuitos disponibles, el enrutamiento de BGP garantizará la conmutación por error si un único circuito deja de estar disponible.
  
Obtenga más información sobre [configuraciones de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/) de muestra y [https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/) .
  
## <a name="selective-routing-with-expressroute"></a>Enrutamiento selectivo con ExpressRoute

El enrutamiento selectivo con ExpressRoute puede ser necesario por diversos motivos, como la prueba, la propagación de ExpressRoute a un subconjunto de usuarios. Hay varias herramientas que los clientes pueden usar para enrutar selectivamente el tráfico de red de Office 365 sobre ExpressRoute:
  
1. **Filtrado/segregación de rutas** : permitir rutas BGP a Office 365 sobre ExpressRoute a un subconjunto de las subredes o enrutadores. Esto se redirige selectivamente por el segmento de red del cliente o la ubicación física de la oficina. Esto es habitual para escalonar la implementación de ExpressRoute para Office 365 y está configurado en los dispositivos BGP.

2. **Archivos PAC/direcciones URL** : dirigir el tráfico de red destinado a Office 365 para FQDN específicos para enrutar en una ruta de acceso específica. Este es el equipo cliente que se enruta de forma selectiva como identificado por la [implementación de archivos PAC](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies).

3. **Filtrado**  -  de rutas Los [filtros de ruta](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) son una forma de consumir un subconjunto de servicios admitidos a través de emparejamiento de Microsoft.

4. **Comunidades BGP** : el filtrado basado en [etiquetas de comunidad BGP](https://aka.ms/bgpexpressroute365) permite a un cliente determinar qué aplicaciones de Office 365 atravesarán ExpressRoute y cuáles atravesarán Internet.

Este es un vínculo breve que se puede usar para volver: [https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>Temas relacionados

[Evaluar la red de Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Implementación de ExpressRoute para Office 365](implementing-expressroute.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimización de la red para Skype Empresarial Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute y calidad del servicio en Skype Empresarial Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flujo de llamadas con ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Uso de comunidades BGP en ExpressRoute para Office 365 escenarios](bgp-communities-in-expressroute.md)
  
[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)
  
[Intervalos de direcciones IP y URL de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)
