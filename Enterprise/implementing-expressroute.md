---
title: Implementar ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: ExpressRoute para Office 365 proporciona una ruta de acceso de enrutamiento alternativa a muchos servicios de Office 365 de conexión a Internet. La arquitectura de ExpressRoute para Office 365 se basa en los prefijos IP públicos de publicidad de los servicios de Office 365 a los que ya se puede tener acceso a través de Internet en los circuitos de ExpressRoute aprovisionados para la redistribución posterior de dichos prefijos IP en la red. Con ExpressRoute, se habilitan de manera eficaz varias rutas de acceso de enrutamiento diferentes, a través de Internet y de ExpressRoute, para muchos servicios de Office 365. Este estado de enrutamiento en la red puede representar un cambio importante en la forma en que se diseña la topología de la red interna.
ms.openlocfilehash: ab40a346ca1b19fcd100f17b934b766b21741010
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998132"
---
# <a name="implementing-expressroute-for-office-365"></a>Implementar ExpressRoute para Office 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

ExpressRoute para Office 365 proporciona una ruta de acceso de enrutamiento alternativa a muchos servicios de Office 365 de conexión a Internet. La arquitectura de ExpressRoute para Office 365 se basa en los prefijos IP públicos de publicidad de los servicios de Office 365 a los que ya se puede tener acceso a través de Internet en los circuitos de ExpressRoute aprovisionados para la redistribución posterior de dichos prefijos IP en la red. Con ExpressRoute, se habilitan de manera eficaz varias rutas de acceso de enrutamiento diferentes, a través de Internet y de ExpressRoute, para muchos servicios de Office 365. Este estado de enrutamiento en la red puede representar un cambio importante en la forma en que se diseña la topología de la red interna.
  
 **Estado:** Guía completa V2
  
Debe planear cuidadosamente su implementación de ExpressRoute para Office 365 para adaptarse a las complejidades de la red de tener el enrutamiento disponible a través de un circuito dedicado con rutas inyectadas en la red principal y en Internet. Si usted y su equipo no realizan la planeación y las pruebas detalladas en esta guía, existe un alto riesgo de que experimente una pérdida intermitente o total de conectividad con los servicios de Office 365 cuando el circuito de ExpressRoute esté habilitado.
  
Para tener una implementación correcta, deberá analizar los requisitos de la infraestructura, realizar una evaluación detallada de la red y diseñar, planear cuidadosamente la implementación de una manera preconfigurada y controlada y crear un plan de pruebas y validación detallado. Para un entorno distribuido de gran tamaño, no es raro ver las implementaciones en un intervalo de varios meses. Esta guía está diseñada para ayudarle a planificar con antelación.
  
Las implementaciones correctas de gran tamaño pueden tardar seis meses en planeación y, a menudo, incluir a los miembros del equipo de muchas áreas de la organización, incluidos los administradores de redes, Firewall y servidores proxy, los administradores de Office 365, la seguridad, el soporte técnico para el usuario final, la administración de proyectos y el patrocinio ejecutivo. Su inversión en el proceso de planeación reducirá la probabilidad de que experimente errores de implementación, lo que provoca un tiempo de inactividad o una solución de problemas compleja y costosa.
  
Esperamos que se completen los siguientes requisitos previos antes de que se inicie esta guía de implementación.
  
1. Ha completado una evaluación de la red para determinar si ExpressRoute es el recomendado y aprobado.

2. Ha seleccionado un proveedor de servicios de red de ExpressRoute. Buscar detalles sobre los [socios de ExpressRoute y las ubicaciones de emparejamiento](https://azure.microsoft.com/documentation/articles/expressroute-locations/).

3. Ya ha leído y entendido la [documentación de expressroute](https://azure.microsoft.com/documentation/services/expressroute/) y su red interna puede cumplir los requisitos previos de expressroute de principio a fin.

4. Su equipo ha leído todas las instrucciones y la documentación pública en [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365) , [https://aka.ms/ert](https://aka.ms/ert) y ha visto la serie de [aprendizaje de Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer) en Channel 9 para obtener conocimientos técnicos críticos, entre los que se incluyen:

      - Las dependencias de Internet de los servicios SaaS.

      - Cómo evitar rutas asimétricas y controlar el enrutamiento complejo.

      - Cómo incorporar los controles de seguridad del perímetro, disponibilidad y nivel de aplicación.

## <a name="begin-by-gathering-requirements"></a>Comenzar por la recopilación de requisitos
<a name="requirements"> </a>

Empiece por determinar qué características y servicios va a adoptar dentro de su organización. Debe determinar qué características de los distintos servicios de Office 365 se usarán y qué ubicaciones de la red hospedarán a los usuarios que usan estas características. Con el catálogo de escenarios, necesita agregar los atributos de red que requieren cada uno de estos escenarios; como flujos de tráfico de red entrante y saliente y si los puntos de conexión de Office 365 están disponibles a través de ExpressRoute o no.
  
Para recopilar los requisitos de la organización:
  
- Catalogue el tráfico de red entrante y saliente para los servicios de Office 365 que usa la organización. Consulte la página direcciones URL e intervalos de direcciones IP de Office 365 para obtener la descripción de los flujos que requieren distintos escenarios de Office 365.

- Recopilar documentación de la topología de red existente que muestre los detalles de la red troncal y la topología de la WAN interna, la conectividad de los sitios satélite, la conectividad de usuario de última millas, el enrutamiento a los puntos de salida del perímetro de red y los servicios proxy.

  - Identifique los puntos de conexión de servicio de entrada en los diagramas de red a los que se conectará Office 365 y otros servicios de Microsoft, mostrando las rutas de conexión de ExpressRoute propuestas y de Internet.

  - Identifique todas las ubicaciones de usuario geográficas y la conectividad WAN entre las ubicaciones, junto con las cuales las ubicaciones actualmente tienen salida a Internet y qué ubicaciones se propone tener como salida a una ubicación de emparejamiento de ExpressRoute.

  - Identifique todos los dispositivos perimetrales, como servidores proxy, firewalls, etc., y Catalogue su relación con los flujos que pasan por Internet y ExpressRoute.

  - Documente si los usuarios finales tendrán acceso a los servicios de Office 365 mediante enrutamiento directo o proxy de aplicaciones indirectas para los flujos de Internet y de ExpressRoute.

- Agregue la ubicación del espacio empresarial y las ubicaciones de Meet-me a su diagrama de red.

- Estimar las características de latencia y rendimiento de red esperadas y observadas desde las ubicaciones de usuario principales a Office 365. Tenga en cuenta que Office 365 es un conjunto de servicios globales y distribuidos que se conectará a ubicaciones que pueden ser diferentes de la ubicación de su inquilino. Por este motivo, se recomienda medir y optimizar la latencia entre el usuario y el borde más cercano de red global de Microsoft sobre ExpressRoute y conexiones de Internet. Puede usar los resultados de la evaluación de red como ayuda para esta tarea.

- Enumerar los requisitos de alta disponibilidad y seguridad de red de la empresa que deben cumplirse con la nueva conexión de ExpressRoute. Por ejemplo, ¿cómo siguen los usuarios para obtener acceso a Office 365 en caso de que se produzca un error de circuito de salida de Internet o de ExpressRoute.

- Documente qué flujos de red de entrada y salida de Office 365 usarán la ruta de Internet y que usarán ExpressRoute. Las características específicas de las ubicaciones geográficas de los usuarios y los detalles de la topología de red local pueden requerir que el plan sea diferente de una ubicación de usuario a otra.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>Catalogar el tráfico de red saliente y entrante
<a name="trafficCatalog"> </a>

Para minimizar el enrutamiento y otras complejidades de la red, se recomienda usar solo ExpressRoute para Office 365 para los flujos de tráfico de red que se necesitan para pasar por una conexión dedicada debido a los requisitos normativos o como resultado de la evaluación de la red. Además, se recomienda que almacene el ámbito del enrutamiento de ExpressRoute y los flujos de tráfico de red de entrada y salida como fases diferentes y distintas del proyecto de implementación. Implementar ExpressRoute para Office 365 solo para los flujos de tráfico de red de salida iniciados por el usuario y dejar el flujo de tráfico de red entrante a través de Internet puede ayudar a controlar el aumento de la complejidad topológica y los riesgos de la introducción de posibilidades de enrutamiento asimétrico adicionales.
  
El catálogo de tráfico de red debe contener listas de todas las conexiones de red entrantes y salientes que tendrá entre la red local y Microsoft.
  
- Los flujos de tráfico de red saliente son todos los escenarios en los que se inicia una conexión desde el entorno local, por ejemplo, de clientes o servidores internos, con un destino de los servicios de Microsoft. Estas conexiones pueden ser directas a Office 365 o indirectas, como cuando la conexión pasa a través de servidores proxy, firewalls u otros dispositivos de red en la ruta de acceso a Office 365.

- Los flujos de tráfico de red de entrada son todos los escenarios en los que se inicia una conexión desde la nube de Microsoft a un host local. Por lo general, estas conexiones deben pasar por firewall y otras infraestructuras de seguridad que la Directiva de seguridad de cliente necesita para flujos externos originados.

Lea la **sección garantizar la simetría de rutas** del artículo [enrutamiento con expressroute para Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) para determinar qué servicios enviarán tráfico entrante y busque la columna marcada como **expressroute para Office 365** en el artículo de referencia de los puntos de conexión de [Office 365](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) para determinar el resto de la información de conectividad.
  
Para cada servicio que requiera una conexión saliente, querrá describir la conectividad planeada para el servicio, incluidos el enrutamiento de red, la configuración de proxy, la inspección de paquetes y las necesidades de ancho de banda.
  
Para cada servicio que requiera una conexión entrante, necesitará información adicional. Los servidores de la nube de Microsoft establecerán conexiones a la red local. para asegurarse de que las conexiones se realizan correctamente, es conveniente describir todos los aspectos de esta conectividad, entre ellos: las entradas DNS públicas para los servicios que aceptarán estas conexiones entrantes, las direcciones IP IPv4 con formato CIDR, que participan en el equipo de ISP y cómo se administra NAT de entrada o NAT de origen para estas conexiones.
  
Las conexiones entrantes deben revisarse independientemente de si se conectan a través de Internet o ExpressRoute para asegurarse de que no se ha incluido el enrutamiento asimétrico. En algunos casos, es posible que los puntos de conexión locales que los servicios de Office 365 inicien conexiones entrantes también necesiten que otros servicios de Microsoft y que no sean de Microsoft obtengan acceso a ellos. Es fundamental que la habilitación del enrutamiento de ExpressRoute a estos servicios para los propósitos de Office 365 no interrumpa otros escenarios. En muchos casos, es posible que los clientes necesiten implementar cambios específicos en su red interna, como NAT basada en origen, para garantizar que los flujos de entrada de Microsoft sigan siendo simétricos después de habilitar ExpressRoute.
  
A continuación, se muestra un ejemplo del nivel de detalle necesario. En este caso, Exchange Hybrid se enrutaría al sistema local a través de ExpressRoute.

|**Connection (propiedad)**|**Valor**|
|:-----|:-----|
|**Dirección del tráfico de red** <br/> |Entrada  <br/> |
|**Servicio** <br/> |Exchange Hybrid  <br/> |
|**Punto de conexión público de Office 365 (origen)** <br/> |Exchange Online (direcciones IP)  <br/> |
|**Punto de conexión público local (destino)** <br/> |5.5.5.5  <br/> |
|**Entrada DNS pública (Internet)** <br/> |Autodiscover.contoso.com  <br/> |
|**Se usará este punto de conexión local para otros servicios de Microsoft (no para Office 365)** <br/> |No  <br/> |
|**Los usuarios o sistemas de Internet usarán este punto de conexión local** <br/> |Sí  <br/> |
|**Sistemas internos publicados a través de puntos de conexión públicos** <br/> |Rol de acceso de cliente de Exchange Server (local) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Anuncio de IP del extremo público** <br/> |**A Internet**: 5.5.0.0/16  <br/> **Para ExpressRoute**: 5.5.5.0/24  <br/> |
|**Controles de seguridad/perímetro** <br/> |**Ruta de acceso a Internet**: DeviceID_002  <br/> **Ruta de acceso de ExpressRoute**: DeviceID_003  <br/> |
|**Alta disponibilidad** <br/> |Activo/activo entre 2 redundancias geográficas  <br/> Circuitos de ExpressRoute: Chicago y Dallas  <br/> |
|**Control de simetría de ruta de acceso** <br/> |**Método**: NAT de origen  <br/> **Ruta de acceso a Internet**: conexiones de entrada NAT de origen a 192.168.5.5  <br/> |**Ruta de acceso de ExpressRoute**: conexiones NAT de origen a 192.168.1.0 (Chicago) y 192.168.2.0 (Dallas)  <br/> |

Este es un ejemplo de un servicio que solo es saliente:

|**Connection (propiedad)**|**Valor**|
|:-----|:-----|
|**Dirección del tráfico de red** <br/> |Salida  <br/> |
|**Servicio** <br/> |SharePoint Online  <br/> |
|**Punto de conexión local (origen)** <br/> |Estación de trabajo de usuario  <br/> |
|**El punto de conexión público de Office 365 (destino)** <br/> |SharePoint Online (direcciones IP)  <br/> |
|**Entrada DNS pública (Internet)** <br/> |\*. sharepoint.com (y FQDN adicionales)  <br/> |
|**Referencias CDN** <br/> |cdn.sharepointonline.com (y FQDN adicionales): direcciones IP mantenidas por los proveedores de CDN  <br/> |
|**Anuncios IP y NAT en uso** <br/> |**Ruta de acceso de Internet/NAT de origen**: 1.1.1.0/24  <br/> **Ruta de acceso de ExpressRoute/NAT de origen**: 1.1.2.0/24 (Chicago) y 1.1.3.0/24 (Dallas)  <br/> |
|**Método de conectividad** <br/> |**Internet**: mediante proxy de capa 7 (archivo. PAC)  <br/> **ExpressRoute**: enrutamiento directo (sin proxy)  <br/> |
|**Controles de seguridad/perímetro** <br/> |**Ruta de acceso a Internet**: DeviceID_002  <br/> **Ruta de acceso de ExpressRoute**: DeviceID_003  <br/> |
|**Alta disponibilidad** <br/> |**Ruta de acceso a Internet**: salida de Internet redundante  <br/> **Ruta de acceso de expressroute**: enrutamiento de "patata caliente" activo/activo entre 2 circuitos ExpressRoute con redundancia geográfica (Chicago y Dallas)  <br/> |
|**Control de simetría de ruta de acceso** <br/> |**Método**: NAT de origen para todas las conexiones  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>El diseño de la topología de red con conectividad regional
<a name="topology"> </a>

Una vez que comprenda los servicios y los flujos de tráfico de red asociados, puede crear un diagrama de red que incorpore estos nuevos requisitos de conectividad e ilustre los cambios que hará para usar ExpressRoute para Office 365. El diagrama debe incluir:
  
1. Todas las ubicaciones de usuario desde las que se tendrá acceso a Office 365 y otros servicios.

2. Todos los puntos de salida de Internet y ExpressRoute.

3. Todos los dispositivos salientes y entrantes que administran la conectividad dentro y fuera de la red, incluidos los enrutadores, los firewalls, los servidores proxy de aplicación y la detección y prevención de intrusiones.

4. Destinos internos para todo el tráfico entrante, como los servidores ADFS internos que aceptan conexiones de los servidores proxy de aplicación Web de ADFS.

5. Catálogo de todas las subredes IP que se anunciarán

6. Identifique cada ubicación en la que los usuarios tendrán acceso a Office 365 y enumere las ubicaciones de Meet-me que se usarán para ExpressRoute.

7. Las ubicaciones y las partes de la topología de red interna, donde se aceptarán, filtrarán y propagarán los prefijos de IP de Microsoft que haya aprendido de ExpressRoute.

8. La topología de red debe ilustrar la ubicación geográfica de cada segmento de red y cómo se conecta a la red de Microsoft sobre ExpressRoute o Internet.

El siguiente diagrama muestra cada ubicación en la que los usuarios usarán Office 365, junto con los anuncios de enrutamiento de entrada y de salida hasta Office 365.
  
![Reunión geográfica regional de ExpressRoute](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Para el tráfico saliente, los usuarios tienen acceso a Office 365 de una de estas tres maneras:
  
1. A través de una ubicación de Meet-me en Norteamérica para los usuarios de California.

2. A través de una ubicación de Meet-me en Hong Kong para los usuarios de Hong Kong.

3. A través de Internet en Bangladesh, donde hay menos personas y ningún circuito aprovisionado de ExpressRoute.

![Conexiones salientes para diagrama regional](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
De forma similar, el tráfico de red entrante de Office 365 devuelve una de estas tres maneras:
  
1. A través de una ubicación de Meet-me en Norteamérica para los usuarios de California.

2. A través de una ubicación de Meet-me en Hong Kong para los usuarios de Hong Kong.

3. A través de Internet en Bangladesh, donde hay menos personas y ningún circuito aprovisionado de ExpressRoute.

![Conexiones entrantes para diagrama regional](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Determinación de la ubicación adecuada para reunirse

La selección de las ubicaciones Meet-me, que son la ubicación física donde el circuito de ExpressRoute conecta la red a la red de Microsoft, se ve influenciada por las ubicaciones desde las que los usuarios tendrán acceso a Office 365. Como una oferta de SaaS, Office 365 no funciona en el modelo regional IaaS o PaaS de la misma manera que lo hace Azure. En su lugar, Office 365 es un conjunto distribuido de servicios de colaboración donde es posible que los usuarios necesiten conectarse a extremos en varios centros de recursos y regiones, que no necesariamente se encuentran en la misma ubicación o región donde se hospeda el inquilino del usuario.
  
Esto significa que la consideración más importante que debe tomar al seleccionar ubicaciones de Meet-me para ExpressRoute para Office 365 es donde se conectará a las personas de su organización. La recomendación general para la conectividad de Office 365 óptima es implementar el enrutamiento, de modo que las solicitudes de usuario a los servicios de Office 365 se entreguen a la red de Microsoft a través de la ruta de acceso de red más corta, esto también se conoce como el enrutamiento de "patata caliente". Por ejemplo, si la mayoría de los usuarios de Office 365 se encuentran en una o dos ubicaciones, al seleccionar las ubicaciones Meet-me más cercanas a la ubicación de dichos usuarios se creará un diseño óptimo. Si su compañía tiene grandes poblaciones de usuarios en muchas regiones diferentes, es posible que desee considerar la posibilidad de tener varios circuitos de ExpressRoute y ubicaciones de Meet-me. Para algunas de sus ubicaciones de usuario, la ruta más corta o óptima a Microsoft Network y Office 365, puede que no sea a través de los puntos de reunirse-conmigo internos de WAN y ExpressRoute, sino a través de Internet.
  
A menudo, hay varias ubicaciones Meet-me que se pueden seleccionar en una región con proximidad relativa a los usuarios. Rellene la tabla siguiente para obtener una guía de las decisiones.

|**Ubicaciones planeadas para reunirse con conmigo de ExpressRoute en California y Nueva York**||
|:-----|:-----|
|Location  <br/> |Número de personas  <br/> |Latencia esperada para la red de Microsoft en la salida de Internet  <br/> |Latencia esperada para Microsoft Network sobre ExpressRoute  <br/> |
|Los Ángeles  <br/> |10 000  <br/> |~ 15ms  <br/> |~ 10 ms (a través de Silicon Valley)  <br/> |
|DC de Washington  <br/> |15.000  <br/> |~ 20 MS  <br/> |~ 10 ms (a través de Nueva York)  <br/> |
|Dallas  <br/> |5.000  <br/> |~ 15ms  <br/> |~ 40ms (a través de Nueva York)  <br/> |

Una vez que la arquitectura de red global que muestra la región de Office 365, las ubicaciones del proveedor de servicios de red de ExpressRoute y la cantidad de personas por ubicación se ha desarrollado, se puede usar para identificar si se pueden realizar optimizaciones. También puede mostrar conexiones de red horquilla globales en las que el tráfico se enruta hacia una ubicación lejana para obtener la ubicación de Meet-me. Si se detecta un horquilla en la red global, debe corregirse antes de continuar. Busque otra ubicación para reunirse o use puntos de salida de un punto de conexión de Internet selectivo para evitar el horquilla.
  
El primer diagrama muestra un ejemplo de un cliente con dos ubicaciones físicas en Norteamérica. Puede ver la información sobre las ubicaciones de Office, las ubicaciones de inquilinos de Office 365 y varias opciones para las ubicaciones de reunirse con mí de ExpressRoute. En este ejemplo, el cliente ha seleccionado la ubicación reunirse para mí en función de dos principios, en orden:
  
1. La proximidad más cercana a las personas de su organización.

2. Más cerca de cerca de un centro de recursos de Microsoft en el que se hospeda Office 365.

![Reunión geográfica estadounidense de ExpressRoute](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Si se amplía este concepto ligeramente más, el segundo diagrama muestra un ejemplo de cliente multinacional que se enfrenta a información y toma de decisiones similares. Este cliente tiene una pequeña oficina en Bangladesh con un pequeño equipo de diez personas centrada en aumentar su tamaño en la región. Hay una ubicación de Meet-me en Chennai y un centro de información de Microsoft con Office 365 hospedado en Chennai para que una ubicación de Meet-me tenga sentido; sin embargo, para diez personas, el gasto del circuito adicional es agobiante. A medida que mira en la red, necesitará determinar si la latencia que implica enviar el tráfico de red a través de la red es más eficaz que gastar el capital para adquirir otro circuito de ExpressRoute.
  
Como alternativa, las diez personas de Bangladesh pueden experimentar un mejor rendimiento con el tráfico de red que se envía a través de Internet a la red de Microsoft, que enrutaría en su red interna tal como mostramos en los diagramas introductorios y se reproducían a continuación.
  
![Conexiones salientes para diagrama regional](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Crear el plan de implementación de ExpressRoute para Office 365
<a name="implementation"> </a>

El plan de implementación debe abarcar los detalles técnicos de la configuración de ExpressRoute, así como los detalles de la configuración de todas las demás infraestructuras de la red, como las siguientes.
  
- Planeación de los servicios que se dividen entre ExpressRoute e Internet.

- Planeación de ancho de banda, seguridad, alta disponibilidad y conmutación por error.

- Diseño de enrutamiento de entrada y de salida, incluidas las optimizaciones de ruta de acceso de enrutamiento adecuadas para diferentes ubicaciones

- Decida hasta dónde se anunciarán las rutas de ExpressRoute en su red y cuál es el mecanismo para que los clientes seleccionen la ruta de acceso de ExpressRoute o Internet; por ejemplo, enrutamiento directo o proxy de aplicación.

- Planee los cambios en los registros DNS, incluidas las entradas del [marco de directivas de remitente](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) .

- Planear la estrategia de NAT, incluidos NAT de origen de entrada y salida.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planeación del enrutamiento con rutas de red de Internet y ExpressRoute
<a name="paths"> </a>

- Para la implementación inicial, se recomienda usar Internet para todos los servicios de entrada, como el correo electrónico entrante o la conectividad híbrida.

- Planee el enrutamiento de LAN de cliente del usuario final, como [la configuración de un archivo PAC/WPAD, la](https://aka.ms/manageo365endpoints)ruta predeterminada, los servidores proxy y los anuncios de rutas BGP.

- Planee el enrutamiento perimetral, incluidos los servidores proxy, los firewalls y los proxy en la nube.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planeación del ancho de banda, seguridad, alta disponibilidad y conmutación por error
<a name="availability"> </a>

Cree un plan para el ancho de banda necesario para cada carga de trabajo de Office 365 principal. Estime por separado los requisitos de ancho de banda de Exchange Online, SharePoint Online y Skype empresarial online. Puede usar las calculadoras de estimación que hemos proporcionado para Exchange Online y Skype empresarial como punto de partida; sin embargo, es necesario realizar una prueba piloto con una muestra representativa de los perfiles de usuario y las ubicaciones para comprender completamente las necesidades de ancho de banda de la organización.
  
Agregue la forma en que se controla la seguridad en cada ubicación de salida de ExpressRoute y de Internet al plan, recuerde que todas las conexiones de ExpressRoute a Office 365 usan emparejamiento público y deben protegerse de acuerdo con las directivas de seguridad de la empresa de conexión a redes externas.
  
Agregue detalles al plan sobre las personas a las que se les aplicará el tipo de interrupción y la forma en que los usuarios podrán realizar su trabajo a toda su capacidad de la manera más sencilla.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planeación de los requisitos de ancho de banda, incluidos los requisitos de Skype empresarial para vibración, latencia, congestión y espacio
  
Skype empresarial online también tiene requisitos de red adicionales específicos, que se detallan en el artículo [calidad de medios y rendimiento de conectividad de red en Skype empresarial online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Lea la sección **planeación de ancho de banda para Azure ExpressRoute** en [planificación de red con ExpressRoute para Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Al realizar una evaluación del ancho de banda con los usuarios piloto, puede usar nuestra guía; [Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planeación de requisitos de alta disponibilidad
  
Cree un plan de alta disponibilidad para satisfacer sus necesidades e incorpore esto en el diagrama de la topología de red actualizada. Lea la sección **alta disponibilidad y conmutación por error con Azure ExpressRoute** en [planeación de red con ExpressRoute para Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planeación de los requisitos de seguridad de red
  
Cree un plan para cumplir con los requisitos de seguridad de la red e incorpórelo a su diagrama de topología de red actualizada. Lea la sección **aplicar controles de seguridad a Azure ExpressRoute para office 365 escenarios** de [planeación de red con ExpressRoute para Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Diseño de la Conectividad del servicio de salida
<a name="outbound"> </a>

ExpressRoute para Office 365 tiene requisitos de red de *salida* que podrían no estar familiarizados. Concretamente, las direcciones IP que representan a los usuarios y las redes en Office 365 y actúan como los extremos de origen para las conexiones de red de salida a Microsoft deben seguir requisitos específicos que se describen a continuación.
  
1. Los puntos de conexión deben ser direcciones IP públicas, que están registradas en su compañía o que el operador le proporciona conectividad de ExpressRoute.

2. Los puntos de conexión deben anunciarse a Microsoft y validarse o aceptarse mediante ExpressRoute.

3. Los puntos de conexión no se deben anunciar a Internet con la misma métrica de enrutamiento preferida.

4. Los puntos de conexión no deben usarse para la conectividad con servicios de Microsoft que no se configuran sobre ExpressRoute.

Si su diseño de red no cumple estos requisitos, hay un alto riesgo de que los usuarios experimenten errores de conectividad con Office 365 y otros servicios de Microsoft debido a la ruta de negro Holing o al enrutamiento asimétrico. Esto ocurre cuando las solicitudes a los servicios de Microsoft se enrutan a través de ExpressRoute, pero las respuestas se redirigen a través de Internet, o viceversa, y las respuestas se pierden mediante dispositivos de red con estado como firewalls.
  
El método más común que puede usar para cumplir los requisitos anteriores es usar la NAT de origen, ya sea implementada como parte de la red o proporcionada por el operador de ExpressRoute. NAT de origen le permite abstraer los detalles y el direccionamiento IP privado de la red de Internet de ExpressRoute y; junto con los anuncios de ruta IP adecuados, proporcionan un mecanismo sencillo para garantizar la simetría de la ruta de acceso. Si está usando dispositivos de red con estado específicos de las ubicaciones de emparejamiento de ExpressRoute, debe implementar grupos de NAT independientes para cada emparejamiento de ExpressRoute para garantizar la simetría de la ruta de acceso.
  
Obtenga más información sobre los [requisitos de NAT de ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-nat/).
  
Agregue los cambios para la conectividad saliente al diagrama de topología de red.
  
### <a name="design-inbound-service-connectivity"></a>Diseño de la Conectividad del servicio de entrada
<a name="inbound"> </a>

La mayoría de las implementaciones empresariales de Office 365 suponen alguna forma de conectividad entrante desde Office 365 a servicios locales, como Exchange, SharePoint y Skype empresarial híbrido, migraciones de buzones de correo y autenticación con la infraestructura de ADFS. Cuando ExpressRoute habilita una ruta de enrutamiento adicional entre la red local y Microsoft para la conectividad saliente, es posible que las conexiones entrantes se vean afectadas involuntariamente por un enrutamiento asimétrico, incluso si desea que esos flujos sigan usando Internet. Se recomiendan algunas precauciones que se describen a continuación para asegurarse de que no haya impacto en los flujos entrantes basados en Internet desde Office 365 a sistemas locales.
  
Para minimizar los riesgos de enrutamiento asimétrico para los flujos de tráfico de red de entrada, todas las conexiones entrantes deben usar la NAT de origen antes de enrutarse en segmentos de la red que tienen visibilidad de enrutamiento en ExpressRoute. Si las conexiones entrantes están permitidas en un segmento de red con visibilidad de enrutamiento en ExpressRoute sin NAT de origen, las solicitudes que se originan en Office 365 entrarán en Internet, pero la respuesta que se redirigirá a Office 365 preferirá la ruta de acceso de red de ExpressRoute a la red de Microsoft, lo que provocará un enrutamiento asimétrico.
  
Puede considerar uno de los siguientes patrones de implementación para satisfacer este requisito:
  
1. Realizar NAT de origen antes de que las solicitudes se enruten a la red interna mediante el equipamiento de red, como firewalls o equilibradores de carga, en la ruta de acceso de Internet a los sistemas locales.

2. Asegúrese de que las rutas de ExpressRoute no se propagan a los segmentos de red donde residen los servicios de entrada, como los servidores front-end o los sistemas de proxy inverso, que controlan las conexiones de Internet.

La administración explícita de estos escenarios en la red y la conservación de todos los flujos de tráfico de red de entrada a través de Internet ayuda a minimizar la implementación y el riesgo operativo del enrutamiento asimétrico.
  
Puede haber casos en los que tenga que elegir dirigir algunos flujos de entrada a través de conexiones de ExpressRoute. Para estos escenarios, tenga en cuenta las siguientes consideraciones adicionales.
  
1. Office 365 solo puede dirigirse a extremos locales que usen IP públicas. Esto significa que incluso si el punto de conexión de entrada local solo se expone a Office 365 sobre ExpressRoute, debe tener asociada una dirección IP pública.

2. Toda la resolución de nombres DNS que realizan los servicios de Office 365 para resolver los extremos locales a través de DNS público. Esto significa que debe registrar el FQDN de los puntos de conexión del servicio de entrada en las asignaciones IP en Internet.

3. Para recibir conexiones de red de entrada a través de ExpressRoute, las subredes IP públicas para estos extremos deben anunciarse a Microsoft sobre ExpressRoute.

4. Evalúe cuidadosamente estos flujos de tráfico de red entrante para asegurarse de que se les apliquen los controles de seguridad y de red adecuados de acuerdo con las directivas de red y seguridad de la empresa.

5. Una vez que los extremos de entrada locales se anuncian a Microsoft sobre ExpressRoute, ExpressRoute se convertirá en la ruta de acceso de enrutamiento preferida a dichos extremos para todos los servicios de Microsoft, incluido Office 365. Esto significa que esas subredes de extremos solo deben usarse para las comunicaciones con los servicios de Office 365 y ningún otro servicio en la red de Microsoft. De lo contrario, el diseño provocará un enrutamiento asimétrico en el que las conexiones entrantes de otros servicios de Microsoft prefieren enrutar el tráfico entrante sobre ExpressRoute, mientras que la ruta de regreso usará Internet.

6. En caso de que un circuito de ExpressRoute o la ubicación de Meet-me esté inactivo, deberá asegurarse de que los extremos de entrada locales sigan estando disponibles para aceptar solicitudes a través de una ruta de acceso de red independiente. Esto puede significar subredes de publicidad para los extremos a través de varios circuitos de ExpressRoute.

7. Se recomienda aplicar NAT de origen para todos los flujos de tráfico de red de entrada que entran en la red a través de ExpressRoute, especialmente cuando estos flujos cruzan dispositivos de red con estado, como firewalls.

8. Algunos servicios locales, como proxy de ADFS o detección automática de Exchange, pueden recibir solicitudes entrantes de los servicios de Office 365 y de los usuarios de Internet. Para estas solicitudes, Office 365 tendrá como destino el mismo FQDN que las solicitudes de usuario a través de Internet. Permitir conexiones de usuario entrante desde Internet a los puntos de conexión locales, al forzar a las conexiones de Office 365 a usar ExpressRoute, representa una complejidad de enrutamiento importante. Para la gran mayoría de los clientes que implementan escenarios complejos sobre ExpressRoute no se recomiendan por consideraciones operativas. Esta sobrecarga adicional incluye la administración de riesgos de enrutamiento asimétrico y requerirá la administración minuciosa de las directivas y los anuncios de enrutamiento en varias dimensiones.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Actualizar el plan de topología de red para mostrar cómo evitar rutas asimétricas
<a name="asymmetric"> </a>

Desea evitar el enrutamiento asimétrico para asegurarse de que las personas de su organización puedan usar sin problemas Office 365, así como otros servicios importantes en Internet. Hay dos configuraciones comunes que los clientes tienen y causan el enrutamiento asimétrico. Ahora es un buen momento para revisar la configuración de red que tiene previsto usar y comprobar si uno de estos escenarios de enrutamiento asimétrico puede existir.
  
Para empezar, analizaremos algunas situaciones distintas asociadas con el siguiente diagrama de red. En este diagrama, todos los servidores que reciben solicitudes entrantes, como ADFS o servidores híbridos locales, se encuentran en el nuevo centro de datos de Jersey y se anuncian en Internet.
  
1. Aunque la red perimetral es segura, no hay ninguna NAT de origen disponible para las solicitudes entrantes.

2. Los servidores del nuevo centro de datos de Jersey pueden ver tanto las rutas de ExpressRoute como las de Internet.

![Información general de conectividad de ExpressRoute](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
También tenemos sugerencias sobre cómo corregirlos.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problema 1: conexión local de nube a través de Internet
  
El siguiente diagrama ilustra la ruta de acceso de red asimétrica tomada cuando la configuración de red no proporciona NAT para las solicitudes entrantes desde la nube de Microsoft a través de Internet.
  
1. La solicitud entrante de Office 365 recupera la dirección IP del punto de conexión local desde el DNS público y envía la solicitud a la red perimetral.

2. En esta configuración defectuosa, no hay ninguna NAT de origen configurada o disponible en la red perimetral en la que se envía el tráfico, lo que da como resultado la dirección IP de origen real que se usa como destino de la devolución.

  - El servidor de la red distribuye el tráfico de devolución a Office 365 a través de cualquier conexión de red de ExpressRoute disponible.

  - El resultado es una ruta de acceso asimétrica para ese flujo a Office 365, lo que da como resultado una conexión interrumpida.

![Problema 1 de enrutamiento de ExpressRoute Asymetric](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Solución 1A: NAT de origen
  
La simple adición de una NAT de origen a la solicitud de entrada resuelve esta red mal configurada. En este diagrama:
  
1. La solicitud entrante sigue entrando a través de la red perimetral del centro de datos de la Nueva Jersey. Esta vez la NAT de origen está disponible.

2. La respuesta del servidor se redirige hacia la IP asociada con la NAT de origen en lugar de la dirección IP original, lo que da como resultado la respuesta que se devuelve en la misma ruta de red.

![Solución 1 de enrutamiento de ExpressRoute Asymetric](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Solución 1B: ámbito de enrutamiento
  
Como alternativa, puede optar por no permitir que se anuncien los prefijos BGP de ExpressRoute, ya que se quita la ruta de red alternativa para esos equipos. En este diagrama:
  
1. La solicitud entrante sigue entrando a través de la red perimetral del centro de datos de la Nueva Jersey. Esta vez los prefijos anunciados de Microsoft a través del circuito de ExpressRoute no están disponibles para el nuevo centro de datos de Jersey.

2. La respuesta del servidor se redirige hacia la IP asociada con la dirección IP original a través de la única ruta disponible, lo que da como resultado la respuesta que se devuelve en la misma ruta de red.

![Solución 2 de enrutamiento de ExpressRoute Asymetric](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problema 2: conexión local de nube a través de ExpressRoute
  
El siguiente diagrama ilustra la ruta de acceso de red asimétrica tomada cuando la configuración de red no proporciona NAT para las solicitudes entrantes desde la nube de Microsoft a través de ExpressRoute.
  
1. La solicitud entrante de Office 365 recupera la dirección IP de DNS y envía la solicitud a la red perimetral.

2. En esta configuración defectuosa, no hay ninguna NAT de origen configurada o disponible en la red perimetral en la que se envía el tráfico, lo que da como resultado la dirección IP de origen real que se usa como destino de la devolución.

  - El equipo de la red enruta el tráfico de devolución a Office 365 a través de cualquier conexión de red de ExpressRoute disponible.

  - El resultado es una conexión asimétrica a Office 365.

![Problema 2 de enrutamiento de ExpressRoute Asymetric](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Solución 2: NAT de origen
  
La simple adición de una NAT de origen a la solicitud de entrada resuelve esta red mal configurada. En este diagrama:
  
1. La solicitud entrante sigue entrando a través de la red perimetral del centro de datos de Nueva York. Esta vez la NAT de origen está disponible.

2. La respuesta del servidor se redirige hacia la IP asociada con la NAT de origen en lugar de la dirección IP original, lo que da como resultado la respuesta que se devuelve en la misma ruta de red.

![Solución 3 de enrutamiento de ExpressRoute Asymetric](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Papel Compruebe que el diseño de red tiene simetría de ruta de acceso

En este punto, debe comprobar en papel que su plan de implementación ofrece simetría de ruta para los distintos escenarios en los que se va a usar Office 365. Identificará la ruta de red específica que se espera que se tome cuando una persona use características diferentes del servicio. Desde la red local y el enrutamiento WAN, hacia los dispositivos perimetrales, a la ruta de conectividad; ExpressRoute o Internet y en la conexión con el extremo en línea.
  
Necesitará hacerlo para todos los servicios de red de Office 365 que se identificaron anteriormente como servicios que adoptará su organización.
  
Este documento le ayudará a recorrer las rutas con una segunda persona. Explíqueles dónde se espera que cada salto de red obtenga su siguiente ruta y asegúrese de que está familiarizado con las rutas de enrutamiento. Recuerde que ExpressRoute siempre proporcionará una ruta más Scope a las direcciones IP de servidor de Microsoft, lo que le proporcionará un costo de ruta menor que una ruta predeterminada de Internet.
  
### <a name="design-client-connectivity-configuration"></a>Diseñar la configuración de conectividad de cliente
<a name="asymmetric"> </a>

![Uso de archivos PAC con ExpressRoute](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Si usa un servidor proxy para el tráfico de enlace a Internet, debe ajustar los archivos PAC o de configuración del cliente para asegurarse de que los equipos cliente de la red estén configurados correctamente para enviar el tráfico de ExpressRoute que desee a Office 365 sin tener que usar el servidor proxy y el tráfico restante, incluido el tráfico de Office 365, se enviará al proxy correspondiente. Lea nuestra guía sobre la [Administración de puntos de conexión de Office 365](https://aka.ms/manageo365endpoints) , por ejemplo archivos PAC.
  
> [!NOTE]
> Los puntos de conexión cambian con frecuencia, tan a menudo como semanalmente. Solo debe realizar cambios en función de los servicios y las características que su organización haya adoptado para reducir el número de cambios que tendrá que hacer para estar al día. Preste especial atención a la **fecha efectiva** de la fuente RSS en la que se anuncian los cambios y se conserva un registro de todos los cambios anteriores, las direcciones IP anunciadas no se pueden anunciar o quitar del anuncio hasta que se alcance la fecha efectiva.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Crear los procedimientos de implementación y prueba
<a name="testing"> </a>

El plan de implementación debe incluir la planeación de pruebas y de reversión. Si la implementación no funciona como se esperaba, el plan debe diseñarse para que afecte al menor número de personas antes de que se detecten los problemas. A continuación se muestran algunos principios de alto nivel que debe tener en cuenta el plan.
  
1. Ensaye el segmento de red y la incorporación de servicios de usuario para minimizar las interrupciones.

2. Planee la prueba de rutas con traceroute y TCP Connect desde un host independiente conectado a Internet.

3. Preferiblemente, las pruebas de servicios entrantes y salientes deben realizarse en una red de prueba aislada con un inquilino de Office 365 de prueba.

      - Como alternativa, puede realizar pruebas en una red de producción si el cliente todavía no usa Office 365 o está en fase piloto.

      - Como alternativa, se pueden realizar pruebas durante una interrupción de producción que se reserva únicamente para pruebas y supervisión.

      - Como alternativa, puede realizar pruebas comprobando las rutas de cada servicio en cada nodo de enrutador de nivel 3. Este retroceso solo debe usarse si no se pueden realizar otras pruebas, dado que la falta de pruebas físicas presenta un riesgo.

### <a name="build-your-deployment-procedures"></a>Crear los procedimientos de implementación

Los procedimientos de implementación deben distribuirse a pequeños grupos de personas en etapas para permitir las pruebas antes de implementar a grupos más grandes de personas. Las siguientes son varias formas de ensayar la implementación de ExpressRoute.
  
1. Configure ExpressRoute con emparejamiento de Microsoft y reenvíe los anuncios de ruta a un solo host para fines de pruebas preconfiguradas.

2. Anuncie las rutas a la red de ExpressRoute a un solo segmento de red en primer lugar y expanda los anuncios de ruta por segmento o región de red.

3. Si es la primera vez que implementa Office 365, use la implementación de red de ExpressRoute como piloto para un pequeño número de personas.

4. Si usa servidores proxy, también puede configurar un archivo PAC de prueba para dirigir un pequeño número de personas a ExpressRoute con pruebas y comentarios antes de agregar más.

El plan de implementación debe enumerar cada uno de los procedimientos de implementación que se deben realizar o los comandos que deben usarse para implementar la configuración de red. Cuando llegue el momento de la interrupción de la red, todos los cambios que se realicen deben prometerse del plan escrito de implementación, que se ha escrito previamente y del mismo nivel. Vea nuestra guía sobre la configuración técnica de ExpressRoute.
  
- Actualizar los registros TXT de SPF si ha cambiado direcciones IP para los servidores locales que seguirán enviando correo electrónico.

- Actualizar las entradas DNS para los servidores locales si ha cambiado las direcciones IP para acomodar una nueva configuración de NAT.

- Asegúrese de que se ha suscrito a la fuente RSS de las notificaciones de punto de conexión de Office 365 para mantener las configuraciones de proxy o enrutamiento.

Una vez completada la implementación de ExpressRoute, los procedimientos del plan de pruebas deben ejecutarse. Se deben registrar los resultados de cada procedimiento. Debe incluir procedimientos para revertir al entorno de producción original en el caso de que los resultados del plan de pruebas indiquen que la implementación no se realizó correctamente.
  
### <a name="build-your-test-procedures"></a>Crear los procedimientos de prueba

Los procedimientos de prueba deben incluir pruebas para cada servicio de red de entrada y salida de Office 365 que usen ExpressRoute y otros que no lo hagan. Los procedimientos deben incluir pruebas de cada ubicación de red única, incluidos los usuarios que no son locales en la LAN corporativa.
  
Algunos ejemplos de actividades de prueba son los siguientes.
  
1. Haga ping desde el enrutador local al enrutador del operador de red.

2. Validan los más de 500 anuncios de direcciones IP de Office 365 y CRM Online que se reciben en el enrutador local.

3. Validar que la NAT de entrada y de salida funciona entre ExpressRoute y la red interna.

4. Valida que las rutas a su NAT se anuncien desde el enrutador.

5. Validar que ExpressRoute ha aceptado los prefijos anunciados.

      - Use el siguiente cmdlet para comprobar los anuncios de emparejamiento:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Valide el intervalo IP público de NAT no se anuncia a Microsoft a través de ningún otro circuito de red de Internet de ExpressRoute a menos que sea un subconjunto específico de un intervalo mayor como en el ejemplo anterior.

7. Los circuitos de ExpressRoute están emparejados, compruebe que ambas sesiones BGP se estén ejecutando.

8. Configure un único host en el interior del NAT y use ping, tracert y tcpping para probar la conectividad en el nuevo circuito con el host outlook.office365.com. Como alternativa, puede usar una herramienta como Wireshark o monitor de red de Microsoft 3,4 en un puerto reflejado para la MSEE para validar que pueda conectarse a la dirección IP asociada con outlook.office365.com.

9. Pruebe la funcionalidad de nivel de aplicación para Exchange Online.

  - Pruebe Outlook puede conectarse a Exchange Online y enviar y recibir correo electrónico.

  - Pruebe si Outlook puede usar el modo en línea.

  - Pruebe la conectividad de smartphone y la capacidad de envío y recepción.

10. Probar la funcionalidad de nivel de aplicación para SharePoint Online

  - Pruebe el cliente de sincronización de OneDrive para la empresa.

  - Pruebe el acceso web de SharePoint Online.

11. Pruebe la funcionalidad de nivel de aplicación para los escenarios de llamadas de Skype empresarial:

  - Unirse a la llamada de conferencia como usuario autenticado [invitación iniciada por el usuario final].

  - Invitar al usuario a la llamada de conferencia [invitación enviada desde MCU].

  - Unirse a la Conferencia como usuario anónimo mediante la aplicación Web de Skype empresarial.

  - Únete a la llamada desde la conexión de tu equipo de red, el teléfono IP y el dispositivo móvil.

  - Llamada a usuario federado o llamada a validación RTC: se ha completado la llamada, la calidad de la llamada es aceptable, el tiempo de conexión es aceptable.

  - Compruebe que el estado de presencia de los contactos se ha actualizado para los miembros del inquilino y los usuarios federados.

### <a name="common-problems"></a>Problemas comunes

El enrutamiento asimétrico es el problema más común de implementación. Estos son algunos de los orígenes comunes que hay que buscar:
  
- Uso de una topología de enrutamiento de red abierta o plana sin NAT de origen en su ubicación.

- No usar SNAT para redirigir a los servicios de entrada a través de las conexiones de Internet y de ExpressRoute.

- No se prueban los servicios de entrada en ExpressRoute en una red de prueba antes de la implementación general.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Implementación de la conectividad de ExpressRoute a través de la red
<a name="testing"> </a>

Ensaye la implementación en un segmento de la red al mismo tiempo, que distribuye progresivamente la conectividad a distintas partes de la red con un plan para revertir para cada nuevo segmento de red. Si su implementación está alineada con una implementación de Office 365, implemente primero en los usuarios piloto de Office 365 y amplíe desde allí.
  
Primero para la prueba y, a continuación, para producción:
  
- Ejecute los pasos de implementación para habilitar ExpressRoute.

- Compruebe que ve las rutas de red como se esperaba.

- Realice pruebas en cada servicio de entrada y de salida.

- Revertir si detecta algún problema.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Configurar una conexión de prueba para ExpressRoute con un segmento de red de prueba

Ahora que ha completado el plan en papel, es el tiempo para probar a pequeña escala. En esta prueba, establecerá una sola conexión de ExpressRoute con emparejamiento de Microsoft en una subred de prueba en su red local. Puede configurar un [inquilino de Office 365 de prueba](https://go.microsoft.com/fwlink/p/?LinkID=403802) con conectividad a la subred de prueba y desde esta, e incluir todos los servicios salientes y entrantes que va a usar en producción en la subred de prueba. Configure DNS para el segmento de red de prueba y establezca todos los servicios entrantes y salientes. Ejecute el plan de pruebas y asegúrese de que está familiarizado con el enrutamiento de cada servicio y la propagación de la ruta.
  
### <a name="execute-the-deployment-and-test-plans"></a>Ejecutar los planes de implementación y pruebas

Cuando complete los elementos descritos anteriormente, marque las áreas que ha completado y asegúrese de que usted y su equipo las han revisado antes de ejecutar los planes de implementación y pruebas.
  
- Lista de los servicios entrantes y salientes que participan en el cambio de red.

- Diagrama de arquitectura de red global que muestra la salida de Internet y las ubicaciones de reunirse conmigo de ExpressRoute.

- Diagrama de enrutamiento de red que muestra las distintas rutas de red usadas para cada servicio implementado.

- Un plan de implementación con los pasos para implementar los cambios y revertir si es necesario.

- Un plan de pruebas para probar cada servicio de red y 365 de Office.

- Se completó la validación del papel de las rutas de producción para los servicios entrantes y salientes.

- Una prueba completada en un segmento de red de prueba, incluidas las pruebas de disponibilidad.

Elija una ventana de interrupción que sea lo suficientemente prolongada como para ejecutar todo el plan de implementación y el plan de pruebas, tenga tiempo disponible para la solución de problemas y tiempo para revertir si es necesario.
  
> [!CAUTION]
> Debido a la naturaleza compleja del enrutamiento a través de Internet y de ExpressRoute, se recomienda agregar más tiempo de búfer a esta ventana para controlar la solución de problemas de enrutamiento complejo.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Configurar QoS para Skype empresarial online

La QoS es necesaria para obtener las ventajas de voz y reuniones de Skype empresarial online. Puede configurar QoS una vez que haya asegurado de que la conexión de red de ExpressRoute no bloquee ninguna de sus otros servicios de Office 365. La configuración de QoS se describe en el artículo [ExpressRoute and QoS in Skype for Business online](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .
  
## <a name="troubleshooting-your-implementation"></a>Solución de problemas de la implementación
<a name="troubleshooting"> </a>

El primer lugar donde buscar se encuentra en los pasos de esta guía de implementación, ¿se ha perdido algún tiempo en el plan de implementación? Vuelva atrás y ejecute pruebas de pequeña red pequeños, si es posible, para replicar el error y depurarlo.
  
Identifique los servicios de entrada o salida que no se pudieron realizar durante las pruebas. Obtenga específicamente las direcciones IP y las subredes para cada uno de los servicios en los que se produjo un error. Siga adelante y recorra el diagrama de la topología de red en papel y valide el enrutamiento. Valide en concreto dónde se anuncia el enrutamiento de ExpressRoute, pruebe ese enrutamiento durante la interrupción si es posible con seguimientos.
  
Ejecutar PSPing con un seguimiento de red para cada extremo de cliente y evaluar las direcciones IP de origen y de destino para validar que son como se espera. Ejecute Telnet en cualquier host de correo que exponga en el puerto 25 y compruebe que SNAT oculta la dirección IP de origen original si esto se espera.
  
Tenga en cuenta que, al implementar Office 365 con una conexión de ExpressRoute, tendrá que asegurarse de que la configuración de red para ExpressRoute esté diseñada de forma óptima y que también ha optimizado los demás componentes de la red, como los equipos cliente. Además de usar esta guía de planeación para solucionar los pasos que puede haber perdido, también hemos escrito un [plan de solución de problemas de rendimiento para Office 365](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>Temas relacionados

[Evaluar la red de Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Uso de las comunidades BGP en ExpressRoute para los escenarios de Office 365 (versión preliminar)](bgp-communities-in-expressroute.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimización de la red para Skype Empresarial Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute y calidad del servicio en Skype Empresarial Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flujo de llamadas con ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)
