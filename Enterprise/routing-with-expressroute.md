---
title: Enrutamiento con ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/7/2017
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
ms.assetid: e1da26c6-2d39-4379-af6f-4da213218408
description: Para conocer adecuadamente enrutar el tráfico a Office 365 con Azure ExpressRoute, necesitará una idea clara de los requisitos de enrutamiento de ExpressRoute núcleo y circuitos ExpressRoute y dominios de enrutamiento. Estos disponer los aspectos básicos para el uso de ExpressRoute que se dependen de los clientes de Office 365.
ms.openlocfilehash: e80ce78c0b229881349a4d02c7708fb9509748a9
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542748"
---
# <a name="routing-with-expressroute-for-office-365"></a>Enrutamiento con ExpressRoute para Office 365

Para conocer adecuadamente enrutar el tráfico a Office 365 con Azure ExpressRoute, necesitará una idea clara de los principales [requisitos de enrutamiento ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-routing/) y [ExpressRoute circuitos y dominios de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-circuit-peerings/). Estos disponer los aspectos básicos para el uso de ExpressRoute que se dependen de los clientes de Office 365.
  
Algunos de los elementos claves en los artículos anteriores que necesita comprender son:
  
- Circuitos ExpressRoute no se asignan a la infraestructura física específica, pero son una conexión lógica realizada en una sola ubicación interconexión por Microsoft y un proveedor de interconexión en su nombre.

- Hay una asignación de 1:1 entre un circuito ExpressRoute y una tecla s de atención al cliente.

- Cada circuito puede admitir hasta 3 relaciones de interconexión independientes (interconexión pública de Azure, interconexión privada de Azure y Microsoft interconexión); Office 365 requiere Microsoft interconexión.

- Cada circuito tiene un ancho de banda fijo que se comparte entre todas las relaciones de interconexión.

- Direcciones IPv4 de cualquier público y pública como números que se va a usar para el ExpressRoute circuito debe validarse como usted propietario, o le han asignado exclusivamente por el propietario del intervalo de direcciones.

- Los circuitos ExpressRoute virtuales son redundantes globalmente y seguirán las prácticas estándar de enrutamiento BGP. Esto es la razón por la que se recomienda dos circuitos físicos por salida a su proveedor en una configuración activa/activa.

Consulte la [página de preguntas más frecuentes](https://azure.microsoft.com/documentation/articles/expressroute-faqs/) para obtener más información sobre los servicios compatibles, los costos y detalles de configuración. En la lista de proveedores de conectividad que ofrece soporte técnico de interconexión de Microsoft, vea el [artículo de ubicaciones de ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-locations/) para obtener información. También que hemos registrado una serie de [ExpressRoute de Azure para Office 365 aprendizaje](https://channel9.msdn.com/series/aer) 10 en Channel 9 para ayudar a explicar los conceptos más detenidamente.
  
## <a name="ensuring-route-symmetry"></a>Asegurar la simetría de ruta

Los servidores front-end de Office 365 son accesibles en Internet y ExpressRoute. Estos servidores se prefieren enrutar a través de circuitos ExpressRoute cuando ambos están disponibles. Por esta razón no hay una posibilidad de asimetría ruta si prefiere el tráfico de la red enrutar a través de los circuitos de Internet. Rutas asimétricas son un problema debido a que los dispositivos que llevar a cabo la inspección de paquetes con seguimiento de estado pueden bloquear el tráfico de retorno que sigue una ruta diferente a los paquetes salientes seguido.
  
Independientemente de si se inicia una conexión a Office 365 a través de Internet o ExpressRoute, el origen debe ser una dirección públicamente enrutable. Con muchos clientes interconexión directamente con Microsoft, tener direcciones privadas donde la duplicación es posible entre los clientes que no es factible.
  
Los siguientes son escenarios donde se iniciará comunicaciones de Office 365 a la red local. Para simplificar el diseño de la red, se recomienda el enrutamiento de estos a través de la ruta de acceso de Internet.
  
- ADFS durante la validación de la contraseña para el inicio de sesión.

- [Las implementaciones híbridas de Exchange Server](https://technet.microsoft.com/library/jj200581%28v=exchg.150%29.aspx).

- Enviar correo electrónico desde un inquilino de Exchange Online a un host local..

- Enviar correo de SharePoint Online desde SharePoint Online para un host local.

- [SharePoint federados búsqueda híbrida](https://technet.microsoft.com/library/dn197174.aspx).

- [Entornos híbridos de SharePoint BCS](https://technet.microsoft.com/library/dn197239.aspx ).

- [Skype para entornos híbridos de negocio](https://technet.microsoft.com/en-us/library/jj205403.aspx) o [Skype para la federación de negocio](https://technet.microsoft.com/library/skype-for-business-online-federation-and-public-im-conectivity.aspx).

- [Skype para la nube de Business Connector](https://technet.microsoft.com/library/mt605227.aspx ).

Para que Microsoft pueda enrutar a la red para estos flujos de tráfico bidireccional, se deben compartir las rutas BGP a sus dispositivos locales con Microsoft.
  
## <a name="deciding-which-applications-and-features-route-over-expressroute"></a>Decidir qué aplicaciones y características enrutan a través de ExpressRoute

Cuando se configura una relación de interconexión con el dominio de enrutamiento interconexión de Microsoft y están aprobadas para el acceso adecuado, podrá ver todos los PaaS y SaaS servicios disponibles a través de ExpressRoute. Los servicios de Office 365 diseñados para ExpressRoute se pueden administrar con [las Comunidades BGP](https://aka.ms/bgpexpressroute365) o [filtros de rutas](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal).
  
Otras aplicaciones, como Office 365 vídeo, es una aplicación de Office 365; Sin embargo, Office 365 vídeo consta de tres componentes diferentes, el portal de, el servicio de transmisión por secuencias y la red de entrega de contenido. El portal se encuentra dentro de SharePoint Online, la transmisión por secuencias vidas de servicio dentro de los servicios de medios de Azure, mientras que la red de entrega de contenido reside dentro de la CDN de Azure. En la siguiente tabla se describe estos componentes.
  
| |
|**Componente**|**Aplicación subyacente**|**¿Se incluyen en la Comunidad de SharePoint Online BGP?**|**Finalidad**|
|:-----|:-----|:-----|:-----|
|Portal de vídeo de Office 365  <br/> |SharePoint Online  <br/> |Sí  <br/> |Configuración, cargar  <br/> |
|Servicio de transmisión por secuencias de vídeo de Office 365  <br/> |Servicios de multimedia de Azure  <br/> |No  <br/> |Servicio de transmisión por secuencias, que se usa en el caso de que el vídeo no está disponible desde la CDN  <br/> |
|Red de entrega de contenido de vídeo de Office 365  <br/> |CDN de Azure  <br/> |No  <br/> |Origen principal de descarga y transmisión de video. [Más información acerca de las redes de vídeo de Office 365](https://support.office.com/article/Office-365-Video-networking-Frequently-Asked-Questions-FAQ-2bed67a1-4052-49ff-a4ce-b7e6530eb98e).<br/> |

Cada una de las características de Office 365 que están disponibles con Microsoft interconexión se muestran en el [artículo de los extremos de Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) por tipo de aplicación y el FQDN. La razón para utilizar el FQDN en las tablas es permitir a los clientes administrar el tráfico de uso de archivos PAC u otras configuraciones de proxy, consulte a nuestra guía de [administración de Office 365 extremos](https://aka.ms/manageo365endpoints) por ejemplo PAC archivos.
  
En algunas situaciones hemos utilizado un dominio comodín donde uno o más sub-FQDN se anuncian diferente del dominio comodín de nivel superior. Esto suele ocurrir cuando el carácter comodín representa una lista de servidores que se todos anuncian a ExpressRoute y a Internet, mientras que un pequeño conjunto de fracciones de destinos sólo se anuncian a Internet o al revés. Hacer referencia a las tablas siguientes para comprender dónde están las diferencias.
  
En esta tabla se muestra el carácter comodín y los FQDN que se anuncian a internet y Azure ExpressRoute junto con el FQDN de sub que se anuncian solo a internet.

|**Dominio de caracteres comodín anuncia a circuitos ExpressRoute e Internet**|**FQDN de Sub anuncia a sólo circuitos de Internet**|
|:-----|:-----|
|\*. microsoftonline.com  <br/> |Click.Email.microsoftonline.com  <br/> Portal.microsoftonline.com  <br/> provisioningapi.microsoftonline.com  <br/> adminwebservice.microsoftonline.com  <br/> |
|\*. officeapps.live.com  <br/> |nexusRules.officeapps.live.com  <br/> Nexus.officeapps.Live.com  <br/> ODC.officeapps.Live.com  <br/> ODC.officeapps.Live.com  <br/> CDN.odc.officeapps.Live.com  <br/> OLS.officeapps.Live.com  <br/> ocsredir.officeapps.Live.com  <br/> ocws.officeapps.Live.com  <br/> ocsa.officeapps.Live.com  <br/> |

Normalmente, los archivos PAC están diseñados para enviar las solicitudes de red a ExpressRoute anuncian extremos directamente al circuito y todas las otras solicitudes de red para el servidor proxy. Si está configurando un archivo PAC similar, redacte el archivo PAC en el orden siguiente:
  
1. Incluir los FQDN sub de la columna dos en la tabla anterior en la parte superior del archivo de PAC, enviar el tráfico hacia el servidor proxy. Hemos creado un archivo de PAC de ejemplo para su uso en nuestro artículo acerca de cómo [administrar los extremos de Office 365](https://aka.ms/manageexpressroute365).

2. Incluir todos los nombres de dominio completos marcados anunciados a ExpressRoute en [este artículo](https://aka.ms/o365endpoints) por debajo de la primera sección, enviar el tráfico directamente a su circuito ExpressRoute.

3. Incluir cualquier otros extremos de la red o las reglas debajo de estas dos entradas, enviar el tráfico hacia el servidor proxy.

Esta tabla muestra los dominios de caracteres comodín que se anuncian a circuitos de Internet sólo junto con el FQDN de sub que se anuncian a ExpressRoute de Azure y circuitos de Internet. Para el archivo PAC anteriormente, los FQDN en dos de las columnas de la por debajo de la tabla se enumeran como que se anuncia a ExpressRoute en el vínculo al que hace referencia, lo que significa que se incluirá en el segundo grupo de entradas en el archivo.

|**Dominio de caracteres comodín anunciada a sólo circuitos de Internet**|**FQDN de Sub anuncia a circuitos ExpressRoute e Internet**|
|:-----|:-----|
|\*. office.com  <br/> |\*. outlook.office.com  <br/> Home.Office.com  <br/> Outlook.Office.com  <br/> Portal.Office.com  <br/> www.Office.com  <br/> |
|\*. office.net  <br/> |Agent.Office.NET  <br/> |
|\*. office365.com  <br/> |Outlook.office365.com  <br/> : SMTP.office365.com  <br/> |
|\*. outlook.com  <br/> |\*. protection.outlook.com  <br/> \*. mail.protection.outlook.com  <br/> detección automática -\<inquilino\>. outlook.com  <br/> |
|\*. windows.net  <br/> |Login.Windows.NET  <br/> |

## <a name="routing-office-365-traffic-over-the-internet-and-expressroute"></a>Enrutar el tráfico a través de Internet y ExpressRoute Office 365

Para enrutar a Office 365 aplicación de su elección necesitará para determinar un número de factores clave.
  
1. ¿Cuánto ancho de banda requerirá la aplicación. Uso existente de muestreo es el método solo confiable para determinar esto en la organización.

2. ¿Qué ubicaciones de salida que desee para el tráfico de red deje de la red. Debe planear a fin de minimizar la latencia de red para la conectividad a Office 365 como esto afecta negativamente al rendimiento. Debido a que Skype para la empresa utiliza vídeo y voz en tiempo real es especialmente susceptible a la latencia de red deficiente.

3. Si desea que todos los datos o un subconjunto de las ubicaciones de red para sacar provecho de ExpressRoute.

4. ¿Qué ubicaciones ExpressRoute desde la ofrece su proveedor de red elegida.

Una vez que determinar las respuestas a estas preguntas, puede aprovisionar un circuito ExpressRoute que satisfaga las necesidades de ancho de banda y la ubicación. Para red más asistencia en el planeamiento, consulte la [Guía para la mejora de red de Office 365](https://aka.ms/tune) y el [caso práctico en cómo planeación del rendimiento de red de controladores de Microsoft](https://aka.ms/tunemsit).
  
### <a name="example-1-single-geographic-location"></a>En el ejemplo 1: Única ubicación geográfica
  
Este ejemplo es un escenario para una compañía ficticia llamada Trey Research que tiene una sola ubicación geográfica.
  
Sólo se permiten a los empleados de Trey Research para conectarse a los servicios y sitios Web en internet que el departamento de seguridad permite explícitamente en el par de servidores proxy de salida que se encuentran entre la red corporativa y su ISP.
  
Trey Research planea usar ExpressRoute de Azure para Office 365 y reconoce que algunos tráfico como el tráfico dirigido a las redes de entrega de contenido no podrá enrutar a través de la ExpressRoute para la conexión de Office 365. Dado que todo el tráfico ya rutas en los dispositivos de proxy de forma predeterminada, estas solicitudes seguirán funcionando como antes. Después de Trey Research determina que cumplen los requisitos de enrutamiento de Azure ExpressRoute, que se producen para crear un circuito, configure el enrutamiento y el nuevo circuito ExpressRoute la vinculación a una red virtual. Una vez que la configuración de ExpressRoute de Azure fundamental esté en su lugar, Trey Research utiliza el [archivo de PAC #2 que se publicar](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) para enrutar el tráfico con datos específicos del cliente a través de la ExpressRoute directa para las conexiones de Office 365.
  
Tal como se muestra en el siguiente diagrama, Trey Research es capaz de satisfacer el requisito para enrutar el tráfico de Office 365 a través de internet y un subconjunto de tráfico a través de ExpressRoute mediante una combinación de los cambios de configuración de proxy de enrutamiento y salientes.
  
1. Uso del [archivo de PAC #2 que se publicar](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies) para enrutar el tráfico a través de un punto de salida de internet independientes para ExpressRoute de Azure para Office 365.

2. Los clientes están configurados con una ruta predeterminada hacia los servidores proxy de Trey Research.

En este escenario de ejemplo, Trey Research está usando un dispositivo de proxy de salida. De forma similar, los clientes que no utilizan ExpressRoute de Azure para Office 365 es posible que desee utilizar esta técnica para enrutar el tráfico según el costo de inspección del tráfico destinado a los extremos de gran volumen Well-known.
  
El mayor volumen FQDN para Exchange Online, SharePoint Online y Skype para profesionales en línea son los siguientes:
  
![Red de borde de ExpressRoute del cliente](media/dab8cc42-b1d6-46d6-b2f6-d70f9e16d5ea.png)
  
- Outlook.office365.com, outlook.office.com

- \<nombre del inquilino\>. sharepoint.com, \<nombre del inquilino\>-my.sharepoint.com, \<nombre del inquilino\>-\<aplicación\>. sharepoint.com

- \*. Lync.com junto con los intervalos IP para el tráfico que no sean TCP

- \*broadcast.officeapps.Live.com, \*excel.officeapps.live.com, \*onenote.officeapps.live.com, \*powerpoint.officeapps.live.com, \*view.officeapps.live.com, \*visio.officeapps.live.com, \* Word-edit.officeapps.live.com, \*view.officeapps.live.com de word, office.live.com

Obtener más información acerca de la [implementación y administración de la configuración de proxy en Windows 8](https://blogs.technet.com/b/deploymentguys/archive/2013/05/08/windows-8-supporting-proxy-services-with-static-configurations-web-hosted-pac-files-and-domain-policy-configured-proxy.aspx) y [asegurarse de Office 365 no se limita a su proxy](https://blogs.technet.com/b/onthewire/archive/2014/03/28/ensuring-your-office-365-network-connection-isn-t-throttled-by-your-proxy.aspx).
  
Con un único circuito ExpressRoute, no hay ningún una alta disponibilidad para Trey Research. En el caso de que se producirá un error en el par de redundantes de Trey de los dispositivos de borde que se servicio de actualización de la conectividad ExpressRoute, no es un circuito ExpressRoute adicional para una conmutación por error. Esto deja Trey Research en un problema como conmutación por error a internet requerirá la reconfiguración manual y en algunos casos direcciones IP nuevo. Si desea que Trey agregar una alta disponibilidad, es la solución más sencilla agregar circuitos de ExpressRoute adicionales para cada ubicación y configurar los circuitos de una manera activo/activo.
  
## <a name="routing-expressroute-for-office-365-with-multiple-locations"></a>Enrutamiento ExpressRoute para Office 365 con varias ubicaciones

El último escenario, el enrutamiento de tráfico de Office 365 a través de ExpressRoute es la base para la arquitectura de enrutamiento de incluso más compleja. Independientemente del número de ubicaciones, número de continentes donde existen esas ubicaciones, número de circuitos ExpressRoute y así sucesivamente, poder enrutar parte del tráfico a Internet y algunos el tráfico a través de ExpressRoute se requerirán.
  
Incluyen las preguntas adicionales que deben responderse para los clientes con varias ubicaciones en varias regiones geográficas:
  
1. ¿Necesita un circuito ExpressRoute en cada ubicación? Si usa Skype para profesionales en línea o se ocupa de la confidencialidad de latencia para SharePoint Online o Exchange Online, se recomienda un par redundante de circuitos ExpressRoute de activo/activo en cada ubicación. Vea el Skype para profesionales calidad y red conectividad Guía de medios para obtener más detalles.

2. Si un circuito ExpressRoute no está disponible en una región determinada, ¿cómo debe Office 365 dirigido a enrutar el tráfico?

3. ¿Qué es el método preferido para consolidar el tráfico en el caso de las redes con muchas ubicaciones pequeñas?

Cada una de estas presenta un desafío único que requiere que se va a evaluar su propia red, así como las opciones disponibles en Microsoft.

|**Consideración**|**Componentes de la red para evaluar**|
|:-----|:-----|
|Circuitos en más de una ubicación  <br/> |Se recomienda un mínimo de dos circuitos configurados en una manera activo/activo.  <br/> Deben ser en comparación con las necesidades de costo, la latencia y ancho de banda.  <br/> Utilizar costo de ruta BGP, archivos PAC y NAT para administrar el enrutamiento con varios circuitos.  <br/> |
|El enrutamiento desde ubicaciones sin un circuito ExpressRoute  <br/> |Se recomienda la salida y la resolución DNS como cerca de la persona que inicia la solicitud para Office 365.  <br/> Reenvío de DNS se puede usar para permitir que las oficinas remotas detectar el extremo adecuado.  <br/> Los clientes en la oficina remota deben tener una ruta disponible que proporciona acceso al circuito ExpressRoute.  <br/> |
|Consolidación de pequeña oficina  <br/> |Uso de ancho de banda y datos disponible debe compararse cuidadosamente.  <br/> |

> [!NOTE]
> Microsoft prefiere ExpressRoute a través de internet si la ruta está disponible independientemente de la ubicación física.
  
Cada una de estas consideraciones debe tenerse en cuenta para cada red único. A continuación se incluye un ejemplo.
  
### <a name="example-2-multi-geographic-locations"></a>Ejemplo 2: Con múltiples zonas geográficas ubicaciones
  
Este ejemplo es un escenario para una compañía ficticia denominada Humongous seguros que tiene varias ubicaciones geográficas.
  
Seguros Humongous está geográficamente dispersa con las oficinas de todo el mundo. Que desean implementar ExpressRoute de Azure para Office 365 mantener la mayor parte de su tráfico de Office 365 en conexiones de red directas. Seguros Humongous también tiene oficinas en dos continentes adicionales. Los empleados de la oficina remota donde ExpressRoute no es factible será necesario enrutar a una o ambas de las instalaciones principales para usar una conexión de ExpressRoute.
  
El principio básico es obtener el tráfico de Office 365 destinadas a un centro de datos de Microsoft tan pronto como sea posible. En este ejemplo, seguros Humongous debe decidir si sus oficinas remotas deben enrutar a través de Internet para llegar a un centro de datos de Microsoft a través de cualquier conexión tan pronto como sea posible o si sus oficinas remotas deben enrutar a través de una red interna para llegar a un Microsoft Centro de datos a través de una conexión de ExpressRoute lo más rápido posible.
  
Centros de datos, redes y arquitectura de la aplicación de Microsoft están diseñados para tomar communications globalmente diferentes y de servicio de ellos en la forma más eficiente posible. Ésta es una de las redes más grandes en el mundo. Las solicitudes de destinados a Office 365 que permanecen en redes de los clientes más tiempo del necesario no puedan aprovechar las ventajas de esta arquitectura.
  
En la situación de Humongous Insurance, deben seguir dependiendo de las aplicaciones que se va a utilizar a través de ExpressRoute. Por ejemplo, si son un Skype para la empresa en línea al cliente, o va a aprovechar la conectividad de ExpressRoute cuando se conecta a Skype externo para las reuniones en línea de negocio, el diseño recomendado en el Skype para calidad de medios en línea de negocio y red Guía de conectividad es aprovisionar un circuito ExpressRoute adicional para la ubicación de terceros. Esto puede resultar más caro desde una perspectiva de red; Sin embargo, el enrutamiento las solicitudes desde uno continente a otro antes de entregar a un centro de datos de Microsoft puede provocar una experiencia deficiente o no se puede usar durante Skype para comunicaciones y reuniones en línea de negocio.
  
Si no está utilizando Humongous seguros o no tiene previsto aprovechar Skype para profesionales en línea en modo alguno, enrutar el tráfico de red de Office 365 dirigido a volver a un continente con un ExpressRoute conexión puede ser viable aunque puede causar latencia innecesario o TCP congestión. En ambos casos, el enrutamiento de Internet, se recomienda el tráfico de destino a Internet en el sitio local para aprovechar las ventajas de las redes de entrega de contenido que Office 365 se basa en.
  
![Multi-geografía ExpressRoute](media/98fdd883-2c5a-4df7-844b-bd28cd0b9f50.png)
  
Cuando seguros Humongous va a planear su estrategia de múltiples geografía, hay un número de cosas que hay que tener en cuenta alrededor de tamaño del circuito, número de circuitos, conmutación por error y así sucesivamente.
  
Con ExpressRoute en una única ubicación con varias regiones si se intenta usar el circuito, seguros Humongous desea asegurarse de que las conexiones a Office 365 desde una oficina remota se envían al centro de datos de Office 365 más cercana sedes centrales y recibidas por el ubicación de la oficina central. Para ello, seguros Humongous implementa reenvío de DNS para reducir el número de viajes de ida y consultas DNS necesarios para establecer la conexión con el entorno de Office 365 más cercano al punto de salida de internet sedes centrales adecuado. Esto impide que al cliente de resolución de un servidor front-end local y se asegura el servidor Front-End, la persona que se conecta a está cerca de la oficina central donde se interconexión Humongous seguro con Microsoft. También puede aprender a [asignar un reenviador condicional para un nombre de dominio](https://technet.microsoft.com/library/Cc794735%28v=WS.10%29.aspx).
  
En este escenario, el tráfico de la oficina remota podría resolver la infraestructura de front-end de Office 365 en Norteamérica y sacar provecho de Office 365 para conectarse a los servidores back-end de acuerdo con la arquitectura de la aplicación de Office 365. Por ejemplo, Exchange Online se terminará la conexión en Norteamérica y esos servidores front-end sería conectarse al servidor de buzón de correo de back-end donde residía el inquilino. Todos los servicios de tengan un servicio de puerta delantera ampliamente distribuido consta de los destinos de unidifusión y difusión por proximidad.
  
Si Humongous tiene oficinas principales en varios continentes, se recomienda un mínimo de dos circuitos activo/activo por región con el fin de reducir la latencia de aplicaciones confidenciales como Skype para profesionales en línea. Si todas las oficinas se encuentran en un único continente o no está usando la colaboración en tiempo real, tener una salida consolidado o distribuido elija es una decisión específica del cliente. Cuando varios circuitos están disponibles, BGP enrutamiento se asegurará de conmutación por error debe cualquier circuito único dejan de estar disponible.
  
Encontrará más información acerca del ejemplo de [configuraciones de enrutamiento](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-routing/) y [https://azure.microsoft.com/en-us/documentation/articles/expressroute-config-samples-nat/](https://azure.microsoft.com/documentation/articles/expressroute-config-samples-nat/).
  
## <a name="selective-routing-with-expressroute"></a>Selectiva de enrutamiento con ExpressRoute

Enrutamiento selectiva con ExpressRoute puedan ser necesarios para una variedad de motivos, por ejemplo, las pruebas, implantar ExpressRoute a un subconjunto de usuarios. Existen diversas herramientas que los clientes pueden usar para enrutar el tráfico de red de Office 365 a través ExpressRoute de forma selectiva:
  
1. **Ruta filtrado/segregación** - de lo que permite las rutas BGP a Office 365 a través de ExpressRoute a un subconjunto de las subredes los enrutadores. Esto distribuye selectivamente por segmento de red de cliente o la ubicación de la oficina física. Esto es común para escalonar implantación de ExpressRoute para Office 365 y está configurado en sus dispositivos BGP.

2. **Archivos y direcciones URL de PAC** - dirigir Office 365 destinado el tráfico de red para específicos FQDN enrutar en una ruta de acceso específica. Esto distribuye selectivamente por equipo cliente identificado por la [implementación del archivo PAC](https://aka.ms/manageo365endpoints#ID0EACAAA=2._Proxies).

3. **Filtrado de rutas** - [filtros de rutas](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) son una forma de usar un subconjunto de los servicios admitidos a través de interconexión de Microsoft.

4. **Las Comunidades BGP** - filtrado basado en [las etiquetas de la Comunidad BGP](https://aka.ms/bgpexpressroute365) permite que un cliente determinar qué aplicaciones de Office 365 atravesará ExpressRoute y que atravesará internet.

Éste es un vínculo corto que puede usar para volver:[https://aka.ms/erorouting](https://aka.ms/erorouting)
  
## <a name="related-topics"></a>Temas relacionados

[Conectividad de red a Office 365](network-connectivity.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Implementación de ExpressRoute para Office 365](implementing-expressroute.md)
  
[Calidad de medios y el rendimiento de conectividad de red en Skype para la empresa en línea](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimización de la red de Skype para profesionales en línea](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute y QoS en Skype para la empresa en línea](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flujo de llamadas de uso ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Uso de las Comunidades BGP en ExpressRoute para escenarios de Office 365](bgp-communities-in-expressroute.md)
  
[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Red de Office 365 y ajuste del rendimiento](network-planning-and-performance.md)
