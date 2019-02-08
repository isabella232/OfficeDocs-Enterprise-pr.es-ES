---
title: Implementación de ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/5/2017
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
ms.assetid: 77735c9d-8b80-4d2f-890e-a8598547dea6
description: ExpressRoute para Office 365 proporciona una ruta de acceso de enrutamiento alternativa a muchos internet conexión a servicios de Office 365. La arquitectura de ExpressRoute para Office 365 se basa en publicidad prefijos IP públicos de servicios de Office 365 que ya puede tener acceso a través de Internet en sus circuitos ExpressRoute aprovisionados para su posterior redistribución de dichos prefijos IP en la red. Con ExpressRoute se permiten eficazmente varias diferentes rutas de acceso, a través de internet y a través de ExpressRoute, para muchos servicios de Office 365. Este estado de enrutamiento de su red puede representar un cambio significativo en el diseño de la topología de la red interna.
ms.openlocfilehash: e535135557f7f2f64077c1d926f120fff78dbd42
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25715876"
---
# <a name="implementing-expressroute-for-office-365"></a>Implementación de ExpressRoute para Office 365

ExpressRoute para Office 365 proporciona una ruta de acceso de enrutamiento alternativa a muchos internet conexión a servicios de Office 365. La arquitectura de ExpressRoute para Office 365 se basa en publicidad prefijos IP públicos de servicios de Office 365 que ya puede tener acceso a través de Internet en sus circuitos ExpressRoute aprovisionados para su posterior redistribución de dichos prefijos IP en la red. Con ExpressRoute se permiten eficazmente varias diferentes rutas de acceso, a través de internet y a través de ExpressRoute, para muchos servicios de Office 365. Este estado de enrutamiento de su red puede representar un cambio significativo en el diseño de la topología de la red interna.
  
 **Estado:** Guía completa v2
  
Debe planear cuidadosamente su ExpressRoute para la implementación de Office 365 para dar cabida a para la complejidad de la red de la necesidad de enrutamiento disponibles a través de ambos un circuito dedicado con rutas insertadas en su red principal e internet. Si usted y su equipo no realizan la planificación detallada y las pruebas de esta guía, hay un alto riesgo que podrá disfrutar intermitente o una pérdida total de conectividad a Office 365 con servicios cuando está habilitado el circuito ExpressRoute.
  
Para que una implementación correcta, debe analizar los requisitos de infraestructura, vaya a través de la evaluación de la red detallada y diseño, planeación de la implantación de una manera controlada y por fases detenidamente y crear un plan de prueba y validación detallada. Para un entorno distribuido grande no es poco frecuente para ver las implementaciones abarcan varios meses. Esta guía está diseñada para ayudarle a planear con antelación.
  
Grandes implementaciones correctas pueden tardar seis meses en la planeación y a menudo incluyen a los miembros del equipo de muchas áreas de la organización incluidos redes, los administradores del servidor Proxy y servidor de seguridad, los administradores de Office 365, seguridad, soporte técnico para el usuario final, project administración y patrocinadores ejecutivos. La inversión en el proceso de planeación permite reducir la probabilidad de que podrá disfrutar resultante en el tiempo de inactividad o compleja y costosa solución de problemas de errores de implementación.
  
Esperamos que los siguientes requisitos previos deben completarse antes de inicia esta guía de implementación.
  
1. Se ha completado una evaluación de red para determinar si ExpressRoute está recomendado y aprobado.

2. Ha seleccionado un proveedor de servicios de red de ExpressRoute. Encuentre información detallada sobre [los socios de ExpressRoute y ubicaciones de interconexión](https://azure.microsoft.com/documentation/articles/expressroute-locations/).

3. Ya ha leído y comprender la [documentación de ExpressRoute](https://azure.microsoft.com/documentation/services/expressroute/) y la red interna es capaz de satisfacer los requisitos previos de ExpressRoute de un extremo a otro.

4. Su equipo tiene lectura todas las guías públicas y documentación en [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365), [https://aka.ms/ert](https://aka.ms/ert)y la serie de [ExpressRoute de Azure para Office 365 aprendizaje](https://channel9.msdn.com/series/aer) en Channel 9 para obtener una descripción de críticos detalles técnicos incluidos en seguimiento:

      - Dependencias de internet de servicios de SaaS.

      - Cómo evitar rutas asimétricas y administran el enrutamiento complejas.

      - Procedimiento para incorporar la seguridad del perímetro, disponibilidad y controles de nivel de aplicación.

## <a name="begin-by-gathering-requirements"></a>Comience con la recopilación de requisitos
<a name="requirements"> </a>

Para iniciar, determinar qué características y servicios que desea adoptar dentro de la organización. Debe determinar qué características de los distintos servicios de Office 365 se va a usar y las ubicaciones en la red que se va a hospedar personas con esas características. Con el catálogo de escenarios, debe agregar los atributos de la red que cada una de esas situaciones requieren; Por ejemplo, los flujos de tráfico de red entrante y saliente y si los extremos de Office 365 están disponibles a través de ExpressRoute o no.
  
Para recopilar los requisitos de su organización:
  
- El tráfico de red entrantes y salientes para los servicios de Office 365 que está usando la organización del catálogo. Consulte la página de intervalos de direcciones IP y URL de Office 365 para la descripción de los flujos que requieren diferentes escenarios de Office 365.

- Recopilar documentación de topología de red existente que muestra detalles de la red troncal WAN interna y la topología, la conectividad de los sitios de satélite, conectividad de usuario milla última, enrutar a puntos de salida de red perimetral y los servicios de proxy.

  - Identificar los extremos de servicio entrantes en los diagramas de red que Office 365 y otros servicios de Microsoft se conectan a, que muestra internet y las rutas de acceso de conexión propuestos de ExpressRoute.

  - Identifique todas las ubicaciones de usuario geográfica y la conectividad de WAN entre las ubicaciones junto con las ubicaciones que actualmente tienen una salida a internet y las ubicaciones que se propondrán para tener una salida en una ubicación de interconexión de ExpressRoute.

  - Identificar todos los dispositivos de borde, como los servidores proxy, servidores de seguridad y así sucesivamente y su relación con los flujos de iba a través de Internet y ExpressRoute del catálogo.

  - Si los usuarios finales tendrá acceso a servicios de Office 365 a través de enrutamiento directo o proxy de aplicación indirecta para flujos de Internet y ExpressRoute del documento.

- Agregar la ubicación de su inquilino y cumplir-me ubicaciones a su diagrama de red.

- Estimación de la esperada y observado rendimiento y latencia de características de la red desde ubicaciones principales de usuario a Office 365. Tenga en cuenta que Office 365 es un conjunto de servicios global y distribuido y los usuarios se conectarán a ubicaciones que pueden ser diferentes de la ubicación de su inquilino. Por este motivo, se recomienda para medir y optimizar el rendimiento de latencia entre el usuario y el borde más cercano de la red global de Microsoft a través de conexiones de ExpressRoute e Internet. Puede usar los resultados de la evaluación de la red para ayudar con esta tarea.

- Seguridad de red de empresa de lista y los requisitos de alta disponibilidad que deben cumplir con la nueva conexión de ExpressRoute. Por ejemplo, cómo los usuarios sigan obtener acceso a Office 365 en caso de fallo del circuito ExpressRoute o salida de Internet.

- Documento fluye qué Office 365 de red entrante y saliente utilizará la ruta de acceso de Internet y que va a usar ExpressRoute. Las características específicas de las ubicaciones geográficas de los usuarios y los detalles de la topología de red local pueden requerir el plan para ser diferente de la ubicación de un usuario a otro.

### <a name="catalog-your-outbound-and-inbound-network-traffic"></a>El tráfico de red entrante y saliente de catálogo
<a name="trafficCatalog"> </a>

Para minimizar la complejidad de red de enrutamiento y otros, se recomienda que sólo utilice ExpressRoute para Office 365 para los flujos de tráfico de red que se requieren para ir a través de una conexión dedicada debido a los requisitos legales o como resultado de la evaluación de la red. Además, se recomienda almacenar provisionalmente del ámbito de los flujos de tráfico de red entrante y saliente de enrutamiento y enfoque ExpressRoute como diferentes fases de implementación del proyecto. Implementar ExpressRoute para Office 365 para flujos de tráfico de red saliente y deje flujos de tráfico de red entrante a través de Internet pueden ayudar a controlar el aumento de complejidad de topología y los riesgos de presentación adicionales iniciadas por el usuario sólo asimétrica posibilidades de enrutamiento.
  
El catálogo de tráfico de red debe contener los listados de todas las conexiones de red entrantes y salientes que tendrá entre su red local y Microsoft.
  
- Flujos de tráfico de red saliente son los escenarios donde se inicia una conexión desde el entorno local, como de los clientes internos o servidores, con un destino de los servicios de Microsoft. Estas conexiones pueden ser directa a Office 365 o indirecta, por ejemplo, cuando la conexión va a través de servidores proxy, firewalls u otros dispositivos de red en la ruta de acceso a Office 365.

- Flujos de tráfico de red entrante son los escenarios donde se inicia una conexión de la nube de Microsoft a un host local. Estas conexiones normalmente, es necesaria ir a través de firewall y otra infraestructura de seguridad que requiere la directiva de seguridad del cliente para los flujos de externamente originados.

Lea la sección **asegurar simetría de ruta** del artículo [enrutamiento con ExpressRoute para Office 365](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) para determinar los servicios que va a enviar el tráfico entrante y busque la columna marcada **ExpressRoute para Office 365** en la [Office 365 los extremos](https://support.office.com/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) artículo de referencia para determinar el resto de la información de conectividad.
  
Para cada servicio que requiere una conexión saliente, querrá describir la conectividad planeada para el servicio que incluye el enrutamiento de red, la configuración de proxy, la inspección de paquetes y las necesidades de ancho de banda.
  
Para cada servicio que requiere una conexión entrante, necesitará alguna información adicional. Los servidores en la nube de Microsoft va a establecer conexiones a su red local. para asegurarse de que las conexiones se realizan correctamente, querrá describir todos los aspectos de esta conectividad, incluidos; las entradas DNS públicas para los servicios que aceptarán las conexiones entrantes, la CIDR con formato de direcciones IP de IPv4, qué equipamiento ISP está implicado, y cómo entrante NAT o NAT de origen se controla para estas conexiones.
  
Se deben revisar las conexiones entrantes, independientemente de si va a conectar a través de internet o no se ha incorporado ExpressRoute para garantizar el enrutamiento asimétrica. En algunos casos, local extremos que Servicios de Office 365 inician conexiones entrantes a mayo también deben tener acceso por otros servicios de que no es de Microsoft y Microsoft. Es un requisito imprescindible que habilitar el enrutamiento ExpressRoute a estos servicios para fines de Office 365 no interrumpa otros escenarios. En muchos casos, los clientes es posible que necesitan implementar los cambios específicos en su red interna, como origen basados NAT, para asegurarse de que los flujos de entrada de Microsoft permanecen simétricos después de que ExpressRoute está habilitado.
  
Éste es un ejemplo del nivel de detalle necesario. En este caso híbrida de Exchange enrutará al sistema local a través de ExpressRoute.

|**Propiedad Connection**|**Value**|
|:-----|:-----|
|**Dirección del tráfico de red** <br/> |Entrada  <br/> |
|**Servicio** <br/> |Exchange Hybrid  <br/> |
|**Extremo de Office 365 pública (origen)** <br/> |Exchange Online (direcciones IP)  <br/> |
|**Extremo de local pública (destino)** <br/> |5.5.5.5  <br/> |
|**Entrada (Internet) DNS pública** <br/> |Autodiscover.contoso.com  <br/> |
|**Este extremo local utilizará para otros servicios de Microsoft (que no sean Office 365)** <br/> |No  <br/> |
|**Se usará este extremo local por los usuarios y los sistemas de Internet** <br/> |Sí  <br/> |
|**Sistemas internos publican a través de extremos públicos** <br/> |Función de acceso de cliente de Exchange Server (local) 192.168.101, 192.168.102, 192.168.103  <br/> |
|**Anuncio de IP público del extremo de la** <br/> |**En Internet**: 5.5.0.0/16  <br/> **Para ExpressRoute**: 5.5.5.0/24  <br/> |
|**Controles de seguridad/perimetral** <br/> |**Ruta de acceso de Internet**: DeviceID_002  <br/> **Ruta de acceso de ExpressRoute**: DeviceID_003  <br/> |
|**Alta disponibilidad** <br/> |Activo/activo a través de 2 ubican redundantes  <br/> Circuitos ExpressRoute - Chicago y Dallas  <br/> |
|**Control de la simetría de ruta de acceso** <br/> |**Método**: NAT de origen  <br/> **Ruta de acceso de Internet**: NAT de origen de las conexiones entrantes a 192.168.5.5  <br/> |**Ruta de acceso de ExpressRoute**: las conexiones NAT de origen (Chicago) 192.168.1.0 y 192.168.2.0 (Dallas)  <br/> |

Éste es un ejemplo de un servicio que sólo es de salida:

|**Propiedad Connection**|**Value**|
|:-----|:-----|
|**Dirección del tráfico de red** <br/> |Salida  <br/> |
|**Servicio** <br/> |SharePoint Online  <br/> |
|**Extremo local (origen)** <br/> |Estación de trabajo de usuario  <br/> |
|**Extremo de Office 365 pública (destino)** <br/> |SharePoint Online (direcciones IP)  <br/> |
|**Entrada (Internet) DNS pública** <br/> |\*. sharepoint.com (y FQDN adicionales)  <br/> |
|**Referencias a CDN** <br/> |CDN.sharepointonline.com (y FQDN adicionales) - direcciones IP que mantienen los proveedores de CDN)  <br/> |
|**Anuncio de IP y NAT en uso** <br/> |**Ruta de acceso de Internet/NAT de origen**: 1.1.1.0/24  <br/> **Ruta de acceso de ExpressRoute/NAT de origen**: 1.1.2.0/24 (Chicago) y 1.1.3.0/24 (Dallas)  <br/> |
|**Método de conectividad** <br/> |**Internet**: a través de proxy de capa 7 (archivo .pac)  <br/> **ExpressRoute**: directo enrutamiento (no hay proxy)  <br/> |
|**Controles de seguridad/perimetral** <br/> |**Ruta de acceso de Internet**: DeviceID_002  <br/> **Ruta de acceso de ExpressRoute**: DeviceID_003  <br/> |
|**Alta disponibilidad** <br/> |**Ruta de acceso de Internet**: salida de internet redundantes  <br/> **Ruta de acceso de ExpressRoute**: activo/activo 'patata caliente' enrutamiento entre 2 circuitos ExpressRoute ubican redundantes - Chicago y Dallas  <br/> |
|**Control de la simetría de ruta de acceso** <br/> |**Método**: NAT para todas las conexiones de origen  <br/> |

### <a name="your-network-topology-design-with-regional-connectivity"></a>Diseño de topología de red con conectividad regional
<a name="topology"> </a>

Una vez que comprenda los servicios y sus flujos de tráfico de red asociado, puede crear un diagrama de red que incorpora estos nuevos requisitos de conectividad y se ilustra los cambios que use ExpressRoute para Office 365. El diagrama debe incluir:
  
1. Todas las ubicaciones de usuario donde se acceso desde Office 365 y otros servicios.

2. Todos los internet y ExpressRoute puntos de salida.

3. Todos los entrantes y salientes dispositivos que administración la conectividad dentro y fuera de la red, incluidos los enrutadores, los firewalls, servidores proxy de aplicación y prevención y detección de intrusiones.

4. Destinos internos para todo el tráfico entrante, como los servidores internos de ADFS que aceptar conexiones de los servidores de proxy de aplicación de web ADFS.

5. Catálogo de todas las subredes IP que aparecerá en el anuncio

6. Identificar cada ubicación donde usuarios tendrán acceso a Office 365 desde y lista el cumplen-me ubicaciones que se usará para ExpressRoute.

7. Ubicaciones y partes de la topología de red interna, donde se aceptarán prefijos de IP de Microsoft y aprendidas ExpressRoute, filtran y se propagan a.

8. La topología de red debe ilustran la ubicación geográfica de cada segmento de red y cómo se conecta a la red de Microsoft a través de ExpressRoute o a Internet.

El diagrama siguiente muestra cada ubicación donde las personas van a usar Office 365 desde junto con los anuncios de enrutamiento entrantes y salientes a Office 365.
  
![Reunirse geográfica regional de ExpressRoute-me](media/d866b36b-49bf-416b-af1b-d054e24989d2.png)
  
Para el tráfico saliente, las personas acceso a Office 365 en uno de tres maneras:
  
1. A través de un reunirse-me ubicación en Norteamérica para las personas de California.

2. A través de un reunirse-me ubicación en Hong Kong para las personas de Hong Kong.

3. A través de internet de Bangladesh donde hay menos personas y no aprovisionado ningún circuito ExpressRoute.

![Conexiones salientes de diagrama regional](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
De forma similar, el tráfico de red entrante desde Office 365 devuelve en uno de tres maneras:
  
1. A través de un reunirse-me ubicación en Norteamérica para las personas de California.

2. A través de un reunirse-me ubicación en Hong Kong para las personas de Hong Kong.

3. A través de internet de Bangladesh donde hay menos personas y no aprovisionado ningún circuito ExpressRoute.

![Conexiones entrantes para diagrama regional](media/d6d6160d-bf28-4de3-a787-186c7432b306.png)
  
### <a name="determine-the-appropriate-meet-me-location"></a>Determinar el correspondiente cumplen-me ubicación

La selección de reunirse-me ubicaciones, que son la ubicación física donde su circuito ExpressRoute conecta la red a la red de Microsoft, está influenciado por las ubicaciones donde las personas tendrán acceso a Office 365 desde. Como una oferta de SaaS, Office 365 no funciona en el modelo IaaS o PaaS regional de la misma forma que hace de Azure. En su lugar, Office 365 es un conjunto distribuido de servicios de colaboración, donde los usuarios pueden necesitar para conectarse a los extremos en varios centros de datos y regiones, que no pueden estar necesariamente en la misma ubicación o región donde se hospeda el inquilino del usuario.
  
Esto significa que la consideración más importante que debe tomar al seleccionar reunirse-me ubicaciones para ExpressRoute para Office 365 es donde las personas de la organización van a conectar desde. La recomendación general para conectividad óptima de Office 365 es implementar enrutamiento, de modo que las solicitudes de usuario para servicios de Office 365 se entregan en la red de Microsoft a través de la ruta de acceso de red más corta, esto se también a menudo se conoce como enrutamiento 'patata caliente'. Por ejemplo, si la mayoría de los usuarios de Office 365 están en uno o dos ubicaciones, selección de reunirse-me ubicaciones que se encuentran en la proximidad más cercana a la ubicación de los usuarios va a crear el diseño óptimo. Si su compañía tiene grandes grupos de usuarios en muchas áreas diferentes, es posible que desea que considere la posibilidad de tener varios circuitos ExpressRoute y cumplir-me ubicaciones. Para algunas de las ubicaciones de usuario, no puede ser la ruta de acceso más corta/más óptima en Office 365 y redes de Microsoft a través de su reunirse interno de WAN y ExpressRoute-me points, pero a través de Internet.
  
En ocasiones, hay varios reunirse-me ubicaciones que podrían ser seleccionadas dentro de un área de proximidad relativa a los usuarios. Rellene la siguiente tabla para tomar las decisiones.

|**Planeada reunirse ExpressRoute-me ubicaciones en California y Nueva York**||
|:-----|:-----|
|Ubicación  <br/> |Número de personas  <br/> |Se esperaba la latencia de red de Microsoft a través de la salida de Internet  <br/> |Latencia esperada a la red de Microsoft a través de ExpressRoute  <br/> |
|Los Ángeles  <br/> |10,000  <br/> |~ 15 ms  <br/> |~ 10 ms (a través de Silicon Valley)  <br/> |
|Washington DC  <br/> |15.000  <br/> |~ 20 ms.  <br/> |~ 10 ms (a través de Nueva York)  <br/> |
|Dallas  <br/> |5,000  <br/> |~ 15 ms  <br/> |~ 40ms (a través de Nueva York)  <br/> |

Una vez que el proveedor de servicios de red de ExpressRoute de la arquitectura de la red global que muestra el área de Office 365, cumplir-me ha desarrollado las ubicaciones y la cantidad de personas por ubicación, puede utilizarse para identificar si se pueden establecer cualquier optimizaciones. También puede mostrar horquilla global conexiones de red donde se enruta el tráfico a una ubicación lejana con el fin de obtener el cumplen-me ubicación. Si se detecta una horquilla en la red global que debe se corrigió antes de continuar. Cualquiera encontrar otra reunirse-me ubicación o use selectivas puntos de salida de Internet descanso para evitar la horquilla.
  
El primer diagrama, se muestra un ejemplo de un cliente con dos ubicaciones físicas en Norteamérica. Puede ver la información acerca de las ubicaciones de office, las ubicaciones del inquilino de Office 365, y cumplen con varias opciones para ExpressRoute-me ubicaciones. En este ejemplo, el cliente ha seleccionado el cumplen-me ubicación basado en dos principios, en orden:
  
1. Proximidad más cercano a las personas de su organización.

2. Más cercano cerca de un centro de datos de Microsoft donde se hospeda Office 365.

![Reunirse geográfica ExpressRoute US-me](media/5ec38274-b317-4ec1-91c8-90c2a7fd32ca.png)
  
Expandir este concepto ligeramente más, segundo diagrama se muestra en el que se enfrenta un cliente multinacional de ejemplo con información similar y toma de decisiones. Este cliente tiene una pequeña oficina en Bangladesh con solo un equipo pequeño de diez personas centrada en el crecimiento de su huella en la región. Hay un reunirse-me ubicación en Chennai y un centro de datos de Microsoft con Office 365 hospedados en Chennai por lo que un reunirse-me ubicación tendría sentido; Sin embargo, para diez personas, el gasto del circuito adicional es pesado. En lo que respecta a la red, debe determinar si la latencia necesarios para enviar el tráfico de red a través de la red es más eficaz que el capital para adquirir otro circuito ExpressRoute de gastos.
  
Como alternativa, las diez personas en Bangladesh pueden experimentar un mejor rendimiento con su tráfico de red enviado a través de internet a la red de Microsoft de que tendría el enrutamiento en su red interna tal y como se mostró en los diagramas de introducción y reproducido a continuación.
  
![Conexiones salientes de diagrama regional](media/8319943d-08f0-4781-9ef3-d23de2ad4671.png)
  
## <a name="create-your-expressroute-for-office-365-implementation-plan"></a>Crear su ExpressRoute para el plan de implementación de Office 365
<a name="implementation"> </a>

El plan de implementación debe abarcar tanto los detalles técnicos de la configuración de ExpressRoute, así como los detalles de configuración de toda la infraestructura de la red, como las siguientes.
  
- Planeación de los servicios que se dividen en ExpressRoute e Internet.

- Planeación de ancho de banda, seguridad, alta disponibilidad y de conmutación por error.

- Diseño de enrutamiento entrante y saliente, incluidas las optimizaciones de ruta de acceso de enrutamiento adecuados de distintas ubicaciones

- Decidir hasta qué punto se ha anunciado en la red ExpressRoute rutas y cuál es el mecanismo para que los clientes seleccionar la ruta de acceso de Internet o ExpressRoute; Por ejemplo, dirigir a proxy de enrutamiento o de la aplicación.

- Planeación de los cambios de registros DNS, incluidas las entradas de [Marco de directivas de remitente](https://technet.microsoft.com/library/dn789058%28v=exchg.150%29.aspx) .

- Planeación de la estrategia NAT incluidos saliente y entrante origen NAT.

### <a name="plan-your-routing-with-both-internet-and-expressroute-network-paths"></a>Planear el enrutamiento con internet y rutas de acceso de red ExpressRoute
<a name="paths"> </a>

- Para la implementación inicial, todos los servicios de entrada, como el correo electrónico entrante o conectividad híbrida, se recomiendan que use internet.

- Planeación de usuario final cliente enrutamiento LAN, tales como la [configuración de un archivo PAC/WPAD](https://aka.ms/manageo365endpoints), ruta predeterminada, los servidores proxy y los anuncios de rutas BGP.

- Planeación de enrutamiento perimetral, incluidos los servidores proxy, firewalls y servidores proxy de la nube.

### <a name="plan-your-bandwidth-security-high-availability-and-failover"></a>Planeación de su ancho de banda, seguridad, alta disponibilidad y conmutación por error
<a name="availability"> </a>

Crear un plan para el ancho de banda necesario para cada carga de trabajo de Office 365 principal. Estimación por separado de Exchange Online, SharePoint Online y Skype para los requisitos de ancho de banda en línea de negocio. Puede usar las calculadoras de estimación que Adjuntamos para Exchange Online y Skype para la empresa como punto de partida; Sin embargo, una prueba piloto con un ejemplo representativo de los perfiles de usuario y las ubicaciones es necesaria comprender las necesidades de ancho de banda de la organización.
  
Agregar cómo se controla la seguridad en cada ubicación de salida de ExpressRoute a su plan e internet, recuerde todas las conexiones ExpressRoute a Office 365 usar interconexión pública y aún deben estar protegidas con arreglo a las directivas de seguridad de la compañía de que se conectan a externo redes.
  
Agregar detalles al plan sobre qué personas se verán afectadas por qué tipo de interrupción y cómo las personas podrán realizar su trabajo con plena capacidad de la manera más sencilla.
  
#### <a name="plan-bandwidth-requirements-including-skype-for-business-requirements-on-jitter-latency-congestion-and-headroom"></a>Planear los requisitos de ancho de banda, incluidos Skype para los requisitos de negocio en vibración, la latencia, congestión y capacidad de aumento
  
Skype para profesionales Online también tiene requisitos específicos de red adicionales que se detallan en el artículo de [calidad de los medios y el rendimiento de la conectividad de red en Skype para profesionales en línea](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917).
  
Lea la sección de **planeación de ancho de banda para ExpressRoute de Azure** en la [planeación de red con ExpressRoute para Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
Al realizar una evaluación de ancho de banda con los usuarios pilotos, puede usar a nuestra guía; [Optimizar el rendimiento de office 365 con las líneas de base y el historial de rendimiento](https://support.office.com/article/Office-365-performance-tuning-using-baselines-and-performance-history-1492cb94-bd62-43e6-b8d0-2a61ed88ebae).
  
#### <a name="plan-for-high-availability-requirements"></a>Planeación de requisitos de alta disponibilidad
  
Crear un plan para alta disponibilidad para satisfacer sus necesidades e incorporar esto en el diagrama de topología de red actualizada. Lea la sección de **alta disponibilidad y conmutación por error con ExpressRoute de Azure** en la [planeación de red con ExpressRoute para Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
#### <a name="plan-for-network-security-requirements"></a>Planeación de requisitos de seguridad de red
  
Crear un plan para satisfacer los requisitos de seguridad de red e incorporar esto en el diagrama de topología de red actualizada. Lea la sección de **controles de seguridad de aplicar a ExpressRoute de Azure para escenarios de Office 365** en la [planeación de red con ExpressRoute para Office 365](https://support.office.com/article/Network-planning-with-ExpressRoute-for-Office-365-103208f1-e788-4601-aa45-504f896511cd).
  
### <a name="design-outbound-service-connectivity"></a>Diseño de la conectividad de los servicios de salida
<a name="outbound"> </a>

ExpressRoute para Office 365 tiene requisitos de red *salientes* que no estén familiarizados. En concreto, las direcciones IP que representan las redes y los usuarios a Office 365 y actúan como los extremos de origen para las conexiones de red saliente a Microsoft deben seguir requisitos específicos que se describen a continuación.
  
1. Los extremos deben ser direcciones IP públicas, que se registran a su compañía o al operador de proporcionar conectividad ExpressRoute a usted.

2. Los extremos deben ser anunciado a Microsoft y validado de aceptado por ExpressRoute.

3. Los extremos no deben ser anuncia a Internet con la métrica de enrutamiento misma o más preferida.

4. Los extremos no deben usarse para la conectividad con servicios de Microsoft que no están configurados a través de ExpressRoute.

Si el diseño de la red no cumple estos requisitos, hay un alto riesgo para que los usuarios experimentarán errores de conectividad a Office 365 y otros servicios de Microsoft debido a la ruta holing negro o enrutamiento asimétrica. Esto se produce cuando las solicitudes a los servicios de Microsoft se enrutan a través de ExpressRoute, pero las respuestas se enrutan a través de internet, o viceversa y las respuestas desciende por dispositivos de red con seguimiento de estado como los servidores de seguridad.
  
El método más comunes que puede usar para cumplir los requisitos anteriores es usar NAT, ya sea implementado como parte de la red o proporcionado por su operador de ExpressRoute el origen. NAT de origen permite abstraer los detalles y el direccionamiento IP privado de la red en internet desde ExpressRoute y; junto con los anuncios de ruta IP correctos, proporcionan un mecanismo sencillo para garantizar la simetría de la ruta de acceso. Si está utilizando dispositivos de red con seguimiento de estado que son específicos de las ubicaciones de interconexión ExpressRoute, debe implementar grupos de servidores NAT independientes para cada ExpressRoute interconexión para garantizar la simetría de la ruta de acceso.
  
Obtenga más información acerca de los [requisitos de NAT ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-nat/).
  
Agregue los cambios para la conectividad de salida para el diagrama de topología de red.
  
### <a name="design-inbound-service-connectivity"></a>Diseño de la conectividad de los servicios de entrada
<a name="inbound"> </a>

La mayoría de las implementaciones empresariales de Office 365 asumir algún tipo de conectividad entrante desde Office 365 a los servicios locales, como por ejemplo, para Exchange, SharePoint y Skype para escenarios híbridos empresarial, las migraciones de buzones de correo y la autenticación mediante ADFS infraestructura. Cuando ExpressRoute habilitar una ruta de enrutamiento adicional entre su red local y Microsoft para la conectividad de salida, estas conexiones entrantes sin darse cuenta pueden verse afectadas por el enrutamiento asimétrica, incluso si desea que tengan esos flujos seguirán uso de Internet. Se recomiendan algunas precauciones que se describe a continuación para asegurarse de que no hay que ningún impacto a Internet en función de flujos de entrada de Office 365 para sistemas locales.
  
Para reducir los riesgos de enrutamiento asimétrica para flujos de tráfico de red entrante, todas las conexiones entrantes de deben utilizar NAT de origen antes de que se enrutan en segmentos de la red que tienen visibilidad enrutamiento en ExpressRoute. Si se permiten las conexiones entrantes en un segmento de red con enrutamiento visibilidad en ExpressRoute sin NAT de origen, las solicitudes que se originan desde Office 365 introduce de internet, pero la respuesta regrese a Office 365 prefiere la ExpressRoute ruta de acceso de red a la red de Microsoft, lo que provoca que el enrutamiento de asimétrica.
  
Es posible que tenga en cuenta uno de los siguientes modelos de implementación para satisfacer este requisito:
  
1. Llevar a cabo NAT de origen antes de que las solicitudes se enrutan a la red interna mediante equipamiento de red como servidores de seguridad o equilibradores en la ruta de acceso de carga desde Internet a sus sistemas local.

2. Asegúrese de que las rutas de ExpressRoute no se propagan a los segmentos de red donde servicios entrantes, como frente finalización servidores o inverso sistemas de proxy, controlar residen las conexiones de Internet.

Explícitamente teniendo en cuenta estos escenarios en la red y mantener todo el tráfico de red entrante fluyen a través de la Ayuda de Internet a minimizar la implementación y riesgos operacionales de enrutamiento asimétrica.
  
Puede haber casos donde es posible que elija para dirigir algunos flujos entrantes a través de conexiones de ExpressRoute. Para estos escenarios, tomar en cuenta las siguientes consideraciones adicionales.
  
1. Office 365 puede solo destino local los extremos que use IP pública. Esto significa, incluso si el local extremo entrante sólo se expone a Office 365 a través de ExpressRoute, aún necesita tener IP públicas asociado con ella.

2. Resolución de nombres DNS que realizan servicios de Office 365 para resolver extremos local ocurrir cuando se utiliza DNS público. Esto significa que debe registrar el FQDN de los extremos de servicio entrantes a las asignaciones de IP en Internet.

3. Para recibir conexiones de red entrantes a través de ExpressRoute, las subredes IP públicas de estos extremos deben para ser anunciado a Microsoft a través de ExpressRoute.

4. Evalúe detenidamente estos flujos de tráfico de red entrante para asegurarse de que la seguridad adecuada y controles de red se aplican a ellos con arreglo a la seguridad de la compañía y las directivas de red.

5. Una vez su local extremos entrantes se anuncian a Microsoft a través de ExpressRoute, ExpressRoute se convertirá en la ruta de acceso de enrutamiento preferido a esos extremos para todos los servicios de Microsoft, incluidos Office 365. Esto significa que las subredes de extremo sólo se deben usar para la comunicación con los servicios de Office 365 y no hay otros servicios en la red de Microsoft. De lo contrario, el diseño de la hará que el enrutamiento asimétrica donde conexiones entrantes de otros servicios que se prefieren para enrutar de Microsoft de entrada a través de ExpressRoute, mientras que la ruta de acceso devuelto utiliza Internet.

6. En el evento un ExpressRoute de circuito o cumplir-me ubicación es hacia abajo, que necesitará para garantizar la local extremos entrantes siguen estando disponibles para aceptar las solicitudes a través de una ruta de acceso de red independiente. Esto puede significar una subred de anuncios para esos extremos a través de varios circuitos ExpressRoute.

7. Se recomienda aplicar NAT de origen para todos los flujos de tráfico de red entrante entra en la red a través de ExpressRoute, especialmente cuando estos flujos entre dispositivos de red con seguimiento de estado como los servidores de seguridad.

8. Algunos servicios locales, como proxy de AD FS o detección automática de Exchange, pueden recibir las solicitudes entrantes de servicios de Office 365 y los usuarios desde Internet. Para estas solicitudes Office 365 se dirigirán al mismo FQDN como solicitudes de usuario a través de Internet. Lo que permite conexiones de usuario entrantes desde internet a esos extremos locales, al intentar forzar conexiones de Office 365 para usar ExpressRoute, representa la complejidad de enrutamiento importante. Para la mayoría de los clientes no se recomienda la implementación de escenarios de este tipo complejos a través de ExpressRoute debido a las consideraciones operativas. Esta sobrecarga adicional incluye, administrar los riesgos de enrutamiento asimétrica y requerirá detenidamente administrar anuncios y directivas de enrutamiento a través de varias dimensiones.

### <a name="update-your-network-topology-plan-to-show-how-you-would-avoid-asymmetric-routes"></a>Actualizar el plan de topología de red para mostrar cómo podría evitar rutas asimétricas
<a name="asymmetric"> </a>

Desea evitar el enrutamiento asimétrica para asegurarse de que las personas de su organización sin ningún problema pueden usar Office 365, así como otros servicios importantes en internet. Existen dos configuraciones comunes los clientes tienen que causan enrutamiento asimétrica. Ahora es un buen momento para revisar la configuración de red que se va a usar y compruebe si alguno de estos escenarios de enrutamiento asimétricos podría existir.
  
Para comenzar, examinaremos algunas situaciones diferentes asociadas con el siguiente diagrama de red. En este diagrama, todos los servidores que reciben las solicitudes entrantes, como híbrida ADFS local o en los servidores se encuentran en el centro de datos de Nueva Jersey y se anuncian a internet.
  
1. Mientras la red perimetral es segura, no existe ninguna NAT de origen está disponible para las solicitudes entrantes.

2. Los servidores en el centro de datos nueva Jersey son vean internet y rutas de ExpressRoute.

![Información general de la conectividad de ExpressRoute](media/8f074af6-ef38-44e8-bc5a-8b4d981fbb20.png)
  
También le ofrecemos sugerencias acerca de cómo solucionarlos.
  
#### <a name="problem-1-cloud-to-on-premises-connection-over-the-internet"></a>Problema 1: En la nube para la conexión local a través de Internet
  
El siguiente diagrama ilustra la ruta de acceso de red asimétrica tomada cuando la configuración de red no proporciona NAT para las solicitudes entrantes de la nube de Microsoft a través de internet.
  
1. La solicitud entrante desde Office 365 recupera la dirección IP del extremo local de DNS público y envía la solicitud a la red perimetral.

2. En esta configuración con errores, no hay ninguna NAT de origen configurado o disponible en la red perimetral, donde es el tráfico enviado resultante en la dirección IP de origen real de direcciones que se utiliza como el destino devuelto.

  - El servidor en la red enruta el tráfico devuelto a Office 365 a través de cualquier conexión de red de ExpressRoute disponible.

  - El resultado es una ruta de acceso asimétrica para ese flujo a Office 365, lo que resulta en una conexión interrumpida.

![Problema de enrutamiento ExpressRoute Asymetric 1](media/9c210c2a-e0ea-4180-8ede-1bf41746ce7a.png)
  
##### <a name="solution-1a-source-nat"></a>Solución 1a: NAT de origen
  
Simplemente agregando una NAT de origen a la solicitud de entrada resuelve esta red mal configurada. En este diagrama:
  
1. La solicitud entrante continúa escribir a través de la red perimetral de dicho centro de datos nueva Jersey. Este tiempo NAT de origen está disponible.

2. Realizar una copia de la respuesta desde el servidor distribuye hacia la dirección IP asociada con la NAT de origen en lugar de la dirección IP original, lo que resulta en la respuesta a la devolución a lo largo de la misma ruta de acceso de red.

![Solución de enrutamiento ExpressRoute Asymetric 1](media/0e87a155-f8de-48ed-92ac-27367b727a82.png)
  
##### <a name="solution-1b-route-scoping"></a>Solución 1b: ruta de ámbito
  
Como alternativa, puede elegir para que no permita la BGP ExpressRoute prefijos van a anunciar, para quitar la ruta de acceso de red alternativa para aquellos equipos. En este diagrama:
  
1. La solicitud entrante continúa escribir a través de la red perimetral de dicho centro de datos nueva Jersey. En este momento los prefijos anunciados de Microsoft a través del circuito ExpressRoute no están disponibles para el centro de datos nueva Jersey.

2. Realizar una copia de la respuesta desde el servidor distribuye hacia la dirección IP asociada con la dirección IP original a través de la única ruta disponible, lo que resulta en la respuesta a la devolución a lo largo de la misma ruta de acceso de red.

![Solución de enrutamiento ExpressRoute Asymetric 2](media/9cb4b2bf-7aa6-487a-bc02-e02af8a979f6.png)
  
#### <a name="problem-2-cloud-to-on-premises-connection-over-expressroute"></a>Problema 2: En la nube para la conexión local a través de ExpressRoute
  
El siguiente diagrama ilustra la ruta de acceso de red asimétrica tomada cuando la configuración de red no proporciona NAT para las solicitudes entrantes de la nube de Microsoft a través de ExpressRoute.
  
1. La solicitud entrante desde Office 365 recupera la dirección IP de DNS y envía la solicitud a la red perimetral.

2. En esta configuración con errores, no hay ninguna NAT de origen configurado o disponible en la red perimetral, donde es el tráfico enviado resultante en la dirección IP de origen real de direcciones que se utiliza como el destino devuelto.

  - El equipo en la red distribuye el tráfico devuelto a Office 365 a través de cualquier conexión de red de ExpressRoute disponible.

  - El resultado es una conexión a Office 365 asimétrica.

![Problema de enrutamiento ExpressRoute Asymetric 2](media/f6fd155b-bbb7-472a-846e-039a99f09913.png)
  
##### <a name="solution-2-source-nat"></a>Solución 2: Origen NAT
  
Simplemente agregando una NAT de origen a la solicitud de entrada resuelve esta red mal configurada. En este diagrama:
  
1. La solicitud entrante continúa escribir a través de la red perimetral de dicho centro de datos de Nueva York. Este tiempo NAT de origen está disponible.

2. Realizar una copia de la respuesta desde el servidor distribuye hacia la dirección IP asociada con la NAT de origen en lugar de la dirección IP original, lo que resulta en la respuesta a la devolución a lo largo de la misma ruta de acceso de red.

![Solución de enrutamiento ExpressRoute Asymetric 3](media/a5d2b90d-a3ec-4047-afbf-6e6e99f376a7.png)
  
### <a name="paper-verify-that-the-network-design-has-path-symmetry"></a>Papel Compruebe que el diseño de la red tiene simetría de la ruta de acceso

En este momento, debe comprobar en papel que el plan de implementación ofrece la simetría de ruta para los distintos escenarios en los que se usará con Office 365. Identificación de la ruta de red específica que se espera que se llevará a cabo cuando una persona usa diferentes características del servicio. Desde la red local y el enrutamiento de WAN, para los dispositivos perimetrales, para la ruta de acceso de conectividad; ExpressRoute o internet y sesión en la conexión con el extremo en línea.
  
Debe hacer esto para todos los servicios de red de Office 365 que se identificaron anteriormente como servicios que se adopte la organización.
  
Ayuda a realizar este recorrido de producto a través de rutas con una segunda persona. Explíqueles donde se espera cada salto de red para obtener su ruta de siguiente y asegúrese de que está familiarizado con las rutas de acceso. Recuerde que ExpressRoute siempre proporcionará una ruta más específica a direcciones IP del servidor Microsoft darle menor costo de ruta que una ruta predeterminada de Internet.
  
### <a name="design-client-connectivity-configuration"></a>Configuración de conectividad de cliente de diseño
<a name="asymmetric"> </a>

![Uso de archivos PAC con ExpressRoute](media/7cfa6482-dbae-416a-ae6f-a45e5f4de23b.png)
  
Si está utilizando un servidor proxy para internet enlazado el tráfico, a continuación, necesita ajustar cualquier PAC o los archivos de configuración de cliente para asegurarse de los equipos cliente en la red están configurados correctamente para enviar el tráfico de ExpressRoute que desee a Office 365 sin a en tránsito el servidor proxy y el tráfico restante, incluidos algunos tráfico de Office 365, se envía al proxy relevante. Lea a nuestra guía sobre la [administración de Office 365 extremos](https://aka.ms/manageo365endpoints) por ejemplo archivos PAC.
  
> [!NOTE]
> Los extremos cambiarán con frecuencia, con la frecuencia semanal. Sólo debe realizar cambios en función de los servicios y características de que la organización ha adoptado para reducir el número de cambios que debe realizar para mantenerse al día. Preste especial atención a la **Fecha efectiva** de la fuente RSS donde se anuncian los cambios y se mantiene un registro de todos los más allá de los cambios, IP las direcciones que se anuncian no se ha anunciado o quitarse del anuncio, hasta que se alcanza la fecha efectiva.
  
## <a name="build-your-deployment-and-testing-procedures"></a>Crear su implementación y procedimientos de prueba
<a name="testing"> </a>

El plan de implementación debe incluir reversión de planificación y comprobación. Si su implementación no está funcionando según lo previsto, el plan de debe diseñarse para afectar el menor número de personas antes de que se descubren problemas. Los siguientes son algunos principios de alto niveles que debe tener en cuenta el plan.
  
1. Provisionalmente la incorporación de servicio del segmento y el usuario de red para minimizar la interrupción.

2. Planificación para probar las rutas con traceroute y TCP se conectan desde un host conectado independiente de internet.

3. Preferiblemente, se deben realizar las pruebas de servicios entrantes y salientes en una red de prueba aislado con un inquilino de prueba de Office 365.

      - Como alternativa, las pruebas se pueden realizar en una red de producción si el cliente aún no utiliza Office 365 o se encuentra en la prueba piloto.

      - Como alternativa, las pruebas sólo pueden ser se realizan durante una interrupción de producción que está reservado para la prueba y de supervisión.

      - Como alternativa, las pruebas pueden realizarse mediante la comprobación de rutas para cada servicio en cada nodo de enrutador de capa 3. Este otoño copia sólo debe usarse si no hay otras pruebas es posible porque falta de prueba físico presenta riesgos.

### <a name="build-your-deployment-procedures"></a>Crear los procedimientos de implementación

Los procedimientos de implementación deben desplegar a pequeños grupos de personas en fases para permitir las pruebas antes de implementar a grupos de personas mayores. Los siguientes son varias formas de organizar la implementación de ExpressRoute.
  
1. Configurar ExpressRoute con interconexión de Microsoft y han los anuncios de rutas que se reenvíen a un único host sólo para almacenar provisionalmente con fines de pruebas.

2. Anunciar rutas a la red de ExpressRoute para un único segmento de red al principio y expanda anuncios de ruta por segmento de red o la región.

3. Si la implementación de Office 365 por primera vez, use la implementación de la red ExpressRoute como una prueba piloto para un número reducido de personas.

4. Si usa servidores proxy, o bien puede configurar un archivo PAC de prueba para dirigir a un número reducido de personas para ExpressRoute con las pruebas y los comentarios antes de agregar más información.

El plan de implementación debe incluir cada uno de los procedimientos de implementación que se deben realizar o comandos que deben usarse para implementar la configuración de red. Cuando el tiempo de interrupción de red llega todos los cambios que se realicen debe ser desde el mismo nivel y plan de implementación escrito que se ha escrito de antemano revisado. Vea la nuestra orientación de la configuración técnica del ExpressRoute.
  
- Actualización de sus registros de SPF TXT si ha cambiado las direcciones IP para los servidores locales que seguirán para enviar correo electrónico.

- Actualizar las entradas DNS para los servidores locales si ha cambiado las direcciones IP para dar cabida a una nueva configuración de NAT.

- Asegúrese de que se ha suscrito a la fuente RSS para que las notificaciones de extremo de Office 365 mantener las configuraciones de enrutamiento o proxy.

Una vez finalizada la implementación de ExpressRoute se deben ejecutar los procedimientos descritos en el plan de pruebas. Los resultados para cada procedimiento deben haber iniciado. Debe incluir procedimientos para revertir al entorno de producción original en el caso de los resultados del plan de pruebas indican que la implementación no se realizó correctamente.
  
### <a name="build-your-test-procedures"></a>Crear los procedimientos de prueba

Los procedimientos de pruebas deben incluir las pruebas para cada servicio de red entrantes y salientes para Office 365 que van a usar ExpressRoute y otros que no. Deben incluir los procedimientos de las pruebas de cada ubicación de red único, incluidos los usuarios que no son locales en la LAN corporativa.
  
Algunos ejemplos de las actividades de prueba incluyen lo siguiente.
  
1. Haga ping a desde el enrutador local para el enrutador de operador de red.

2. Validar el 500 + Office 365 y CRM Online la dirección IP se reciben anuncios por el enrutador local.

3. Validar la entrada y salida NAT está en funcionamiento entre ExpressRoute y la red interna.

4. Validar que el dispositivo NAT que las rutas se anuncian desde el enrutador.

5. Validar que ExpressRoute ha aceptado sus prefijos anunciados.

      - Use el siguiente cmdlet para comprobar interconexión anuncios:

      ```PowerShell
      Get-AzureRmExpressRouteCircuitRouteTable -DevicePath Primary -ExpressRouteCircuitName TestER -ResourceGroupName RG -PeeringType MicrosoftPeering
      ```

6. Validar la IP de NAT pública del intervalo no se anuncia a Microsoft a través de cualquier otro ExpressRoute o circuito de red de Internet pública a menos que sea un subconjunto específico de un intervalo mayor como se muestra en el ejemplo anterior.

7. ExpressRoute circuitos están emparejados, validar que se están ejecutando sesiones BGP.

8. Configurar un único host en el interior del dispositivo NAT y usar ping, tracert y tcpping para probar la conectividad entre el nuevo circuito a la outlook.office365.com de host. Como alternativa, podría utilizar una herramienta como Wireshark o 3.4 de Monitor de red de Microsoft en un puerto reflejado a la MSEE para validar está poder conectarse a la dirección IP asociada con outlook.office365.com.

9. Probar la funcionalidad de nivel de aplicación para Exchange Online.

  - Probar Outlook es capaz de conectarse a Exchange Online y enviar y recibir correo electrónico.

  - Probar Outlook es capaz de utilizar el modo en línea.

  - Probar la capacidad de conectividad y el envío o recepción de smartphone.

10. Probar la funcionalidad de nivel de aplicación para SharePoint Online

  - OneDrive de prueba para el cliente de sincronización.

  - Probar el acceso de SharePoint Online web.

11. Probar la funcionalidad de nivel de aplicación de Skype para escenarios llamados empresariales:

  - Unirse a llamada de conferencia como usuario autenticado [invitar iniciadas por el usuario final].

  - Invitar a un usuario a la llamada de conferencia [invitar enviado desde MCU].

  - Unirse a conferencia como usuario anónimo mediante la Skype para la aplicación web empresarial.

  - Unirse a llamada desde su conexión por cable de PC, el teléfono IP y el dispositivo móvil.

  - Llamar a los usuarios federados o llamada de validación de RTC: llamada finalizada, calidad de la llamada es aceptable, el tiempo de conexión es aceptable.

  - Compruebe el estado de presencia de los contactos se ha actualizado para ambos miembros del inquilino y los usuarios federados.

### <a name="common-problems"></a>Problemas más comunes

Enrutamiento asimétrica es el problema de implementación más comunes. A continuación presentamos algunos orígenes comunes para buscar:
  
- Uso de una topología de enrutamiento de red abierto o plano sin NAT en lugar de origen.

- No se utiliza SNAT para enrutar a entrantes conexiones de servicios a través de internet y ExpressRoute.

- No probar servicios entrantes en ExpressRoute en una red de prueba antes de implementar a grandes rasgos.

## <a name="deploying-expressroute-connectivity-through-your-network"></a>Implementación de la conectividad de ExpressRoute a través de la red
<a name="testing"> </a>

Fase de la implementación de un segmento de la red a la vez, progresivamente implantar la conectividad para distintas partes de la red con un plan para revertir para cada nuevo segmento de red. Si la implementación se alinea con una implementación de Office 365, implementar primero a los usuarios pilotos de Office 365 y ampliar desde allí.
  
En primer lugar para la prueba y, a continuación, para la producción:
  
- Ejecute los pasos de implementación para habilitar ExpressRoute.

- Probar su vean que las rutas de red son como se esperaba.

- Realizar pruebas en cada servicio entrante y saliente.

- Reversión si se detectan los problemas.

### <a name="set-up-a-test-connection-to-expressroute-with-a-test-network-segment"></a>Configurar una conexión de prueba a ExpressRoute con un segmento de red de prueba

Ahora que ya tiene el plan completo en papel es el momento de probar en una pequeña escala. En esta prueba establecerá una sola conexión ExpressRoute con Microsoft Peering a una subred de prueba en su red local. Se pueden configurar una [prueba inquilino de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=403802) con conectividad a y desde la subred de prueba e incluir todos los servicios de entrada y salidos que se va a usar en producción en la subred de prueba. Configurar DNS para el segmento de red de prueba y establecer todos los servicios de entrada y salidos. Ejecutar su plan de pruebas y asegúrese de que está familiarizado con el enrutamiento para cada servicio y la propagación de la ruta.
  
### <a name="execute-the-deployment-and-test-plans"></a>Ejecutar los planes de implementación y prueba

Al completar los elementos descritos anteriormente, compruebe desactiva las áreas completada y asegúrese de y haber revisado el equipo de ellos antes de ejecutar la implementación y pruebas de los planes.
  
- Lista de servicios entrantes y salientes que participan en el cambio de la red.

- Diagrama de arquitectura de red global que muestra la salida de internet y reunirse ExpressRoute-me ubicaciones.

- Diagrama de enrutamiento de red que muestra las rutas de acceso de red distinta que usa para cada servicio de implementada.

- Un plan de implementación con los pasos para implementar los cambios y rollback si es necesario.

- Un plan de pruebas para las pruebas de cada servicio de red y de Office 365.

- Completado validación de papel de las rutas de producción para servicios entrantes y salientes.

- Una prueba completada a través de un segmento de red de prueba incluidas las pruebas de disponibilidad.

Elija una ventana de interrupción que es suficiente para ejecutar el plan de implementación completa y el plan de pruebas, tiene algunos tiempo disponible para la solución de problemas y la hora para sucesivas copia si es necesario.
  
> [!CAUTION]
> Debido a la naturaleza compleja de enrutamiento a través de internet y ExpressRoute, se recomienda que el tiempo de búfer adicional se agrega a esta ventana para tratar de solucionar problemas de enrutamiento complejas.
  
### <a name="configure-qos-for-skype-for-business-online"></a>Configuración de QoS para Skype para la empresa en línea

QoS es necesario para obtener los beneficios de voz y reuniones de Skype para profesionales en línea. Puede configurar QoS después de comprobar que la conexión de red ExpressRoute no bloquean cualquiera de los otro acceso del servicio de Office 365. Configuración de QoS se describe en el artículo [ExpressRoute y QoS en Skype para profesionales en línea](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) .
  
## <a name="troubleshooting-your-implementation"></a>Solución de problemas de la implementación
<a name="troubleshooting"> </a>

¿El primer lugar para buscar es en los pasos descritos en esta guía de implementación, se han cualquiera perdidas en el plan de implementación? Volver atrás y ejecutar aún más pequeña red prueba si es posible para replicar el error y depurar no existe.
  
Identificar qué entrante o saliente servicios no se pudo durante las pruebas. Obtener específicamente las direcciones IP y subredes para cada uno de los servicios que no se pudo. Seguir adelante y facilitarán el diagrama de topología de red en papel y validar el enrutamiento. Validar específicamente donde el enrutamiento de ExpressRoute se anuncia a, ese enrutamiento durante la interrupción del servicio si es posible con los seguimientos de prueba.
  
Ejecute PSPing con un seguimiento de red a cada extremo de cliente y evaluar las direcciones IP de origen y destino para validar que se hayan definido como se esperaba. Ejecute telnet en cualquier host de correo que se exponen en el puerto 25 y compruebe que SNAT es ocultar la dirección IP de origen original si se espera.
  
Tenga en cuenta que, durante la implementación de Office 365 con una conexión de ExpressRoute que necesitará para garantizar la configuración de red para ExpressRoute, se ha diseñado de forma óptima y también ha optimizado los demás componentes de la red, como los equipos cliente. Además de usar a esta guía de planeación para solucionar problemas de los pasos que se haya perdido, que también hemos escrito un [plan para Office 365 de solución de problemas de rendimiento](https://support.office.com/article/Performance-troubleshooting-plan-for-Office-365-e241e5d9-b1d8-4f1d-a5c8-4106b7325f8c) .
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/implementexpressroute365](https://aka.ms/implementexpressroute365)
  
## <a name="related-topics"></a>Temas relacionados

[Conectividad de red a Office 365](network-connectivity.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Uso de comunidades BGP en ExpressRoute para escenarios de Office 365 (versión preliminar)](bgp-communities-in-expressroute.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimización de la red para Skype Empresarial Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute y QoS en Skype Empresarial Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flujo de llamadas con ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)
