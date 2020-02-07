---
title: Planeamiento de redes con ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
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
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: ExpressRoute para Office 365 ofrece conectividad de nivel 3 entre la red y los centros de recursos de Microsoft. Los circuitos usan anuncios de ruta de protocolo de puerta de enlace de borde (BGP) de los servidores front-end de Office 365. Desde la perspectiva de los dispositivos locales, cuando es necesario seleccionar la ruta TCP/IP correcta a Office 365, Azure ExpressRoute se ve como una alternativa a Internet.
ms.openlocfilehash: 2f38b88b5d940d1a8aa171c777e82a4a308be0cf
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844561"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Planeamiento de redes con ExpressRoute para Office 365

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

ExpressRoute para Office 365 ofrece conectividad de nivel 3 entre la red y los centros de recursos de Microsoft. Los circuitos usan anuncios de ruta de protocolo de puerta de enlace de borde (BGP) de los servidores front-end de Office 365. Desde la perspectiva de los dispositivos locales, cuando es necesario seleccionar la ruta TCP/IP correcta a Office 365, Azure ExpressRoute se ve como una alternativa a Internet.
  
Azure ExpressRoute agrega una ruta de acceso directa a un conjunto específico de características y servicios compatibles ofrecidos por los servidores de Office 365 dentro de los centros de recursos de Microsoft. Azure ExpressRoute no sustituye la conectividad de Internet a los centros de servicios de Microsoft o los servicios de Internet básicos, como la resolución de nombres de dominio. Azure ExpressRoute y los circuitos de Internet deben estar protegidos y ser redundantes.
  
En la tabla siguiente se resaltan algunas diferencias entre las conexiones de Internet y Azure ExpressRoute en el contexto de Office 365.

|**Diferencias en la planeación de red**|**Conexión de red de Internet**|**Conexión de red de ExpressRoute**|
|:-----|:-----|:-----|
| Acceso a servicios de Internet necesarios, incluidos;  <br/>  Resolución de nombres DNS  <br/>  Comprobación de revocación de certificados  <br/>  Redes de entrega de contenido  <br/> |Sí  <br/> |Las solicitudes a la infraestructura de DNS y/o CDN que posee Microsoft pueden usar la red de ExpressRoute.  <br/> |
| Acceso a servicios de Office 365, incluidos;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype Empresarial Online  <br/>  Office en un explorador  <br/>  Portal y autenticación de Office 365  <br/> |Sí, todas las aplicaciones y características  <br/> |Sí, [aplicaciones y características específicas](https://aka.ms/o365endpoints) <br/> |
|Seguridad local en el perímetro.  <br/> |Sí  <br/> |Sí  <br/> |
|Planeación de alta disponibilidad.  <br/> |Conmutación por error a una conexión de red de Internet alternativa  <br/> |Conmutación por error a una conexión de ExpressRoute alternativa  <br/> |
|Conexión directa con un perfil de red predecible.  <br/> |No  <br/> |Sí  <br/> |
|Conectividad IPv6.  <br/> |Sí  <br/> |Sí  <br/> |

Expanda los títulos a continuación para obtener más información sobre la planeación de redes. También hemos grabado una serie [de formación de Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer) que se adentra más profunda.

## <a name="existing-azure-expressroute-customers"></a>Clientes de Azure ExpressRoute existentes

Si está usando un circuito de Azure ExpressRoute existente y desea agregar conectividad de Office 365 a través de este circuito, debe mirar el número de circuitos, ubicaciones de salida y tamaño de los circuitos para asegurarse de que satisfarán las necesidades del uso de Office 365. La mayoría de los clientes necesitan más ancho de banda y muchos necesitan circuitos adicionales.
  
Para permitir el acceso a Office 365 sobre los circuitos de Azure ExpressRoute existentes, [Configure los filtros de ruta](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) para asegurarse de que los servicios de Office 365 sean accesibles.
  
La suscripción de Azure ExpressRoute está centrada en el cliente, lo que significa que las suscripciones están ligadas a los clientes. Como cliente, puede tener varios circuitos de Azure ExpressRoute y tener acceso a muchos recursos de la nube de Microsoft a través de esos circuitos. Por ejemplo, puede optar por tener acceso a una máquina virtual hospedada de Azure, un inquilino de prueba de Office 365 y un inquilino de producción de Office 365 en un par de circuitos de Azure ExpressRoute redundantes.
  
En esta tabla se describen los dos tipos de relaciones de emparejamiento que puede elegir para implementar a través de los circuitos.

|**Relación de emparejamiento**|**Azure privado**|**Microsoft**|
|:-----|:-----|:-----|
|**Servicios** <br/> |IaaS: máquinas virtuales de Azure  <br/> |PaaS: servicios públicos de Azure  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Inicio de conexión * * * * <br/> |Cliente a Microsoft  <br/> Microsoft a cliente  <br/> |Cliente a Microsoft  <br/> Microsoft a cliente  <br/> |
|**Compatibilidad con QoS** <br/> |Sin QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup> QoS solo admite Skype empresarial en este momento.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Planeación de ancho de banda para Azure ExpressRoute

Cada cliente de Office 365 tiene necesidades de ancho de banda único en función del número de personas en cada ubicación, de la actividad de cada aplicación de Office 365 y de otros factores, como el uso de equipamiento local o híbrido y las configuraciones de seguridad de la red.
  
Tener un ancho de banda muy pequeño tendrá como resultado una congestión, retransmisiones de datos y retrasos impredecibles. Tener demasiado ancho de banda tendrá como resultado un costo innecesario. En una red existente, a menudo se hace referencia al ancho de banda en términos de la cantidad de espacio disponible en el circuito como un porcentaje. Tener un 10% de espacio libre tendrá como resultado una congestión y tener un 80% de espacio en general significa un coste innecesario. Las asignaciones de destino de espacio estándar son de 20% a 50%.
  
Para encontrar el nivel correcto del ancho de banda, el mejor mecanismo es probar el consumo de red existente. Esta es la única forma de obtener una verdadera medida de uso y necesitará como todas las aplicaciones y la configuración de red son únicas en cierto modo. Al medir, querrá prestar especial atención al consumo de ancho de banda, la latencia y la congestión TCP totales para comprender las necesidades de la red.
  
Una vez que tenga una línea de base estimada que incluya todas las aplicaciones de red, pruebe Office 365 con un grupo pequeño que comprenda los distintos perfiles de las personas de su organización para determinar el uso real y use las dos medidas para calcular la cantidad de ancho de banda que necesitará para cada ubicación de la oficina. Si hay problemas de latencia o de congestión TCP en las pruebas, es posible que tenga que mover los salida más cerca a los usuarios mediante Office 365 o quitar la detección intensiva de la red, como el descifrado o la inspección de SSL.
  
Todas las recomendaciones en cuanto al tipo de procesamiento de red se recomiendan en los circuitos de ExpressRoute y de Internet. Lo mismo ocurre con el resto de las instrucciones de nuestro [sitio de ajuste del rendimiento](https://aka.ms/tune).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Aplicar controles de seguridad a Azure ExpressRoute para Office 365 escenarios

La protección de la conectividad de Azure ExpressRoute comienza con los mismos principios que la protección de conectividad de Internet. Muchos clientes eligen implementar los controles de red y perimetral a lo largo de la ruta de acceso de ExpressRoute que conecta su red local a Office 365 y otras nubes de Microsoft. Estos controles pueden incluir firewalls, proxies de aplicaciones, prevención de fugas de datos, detección de intrusiones, sistemas de prevención de intrusiones, etc. En muchos casos, los clientes aplican diferentes niveles de controles al tráfico iniciado desde el entorno local pasando a Microsoft, en comparación con el tráfico Iniciado por Microsoft que va a la red local del cliente, en lugar de que el tráfico iniciado de forma local pase a un general Destino de Internet.
  
Estos son algunos ejemplos de integración de la seguridad con el [modelo de conectividad de ExpressRoute](https://docs.microsoft.com/azure/expressroute/expressroute-connectivity-models) que decida implementar.

|**Opción de integración de ExpressRoute**|**Modelo de perímetro de seguridad de red**|
|:-----|:-----|
|Colocalizado en un intercambio de nube  <br/> |Instalar una nueva o aprovechar la infraestructura de seguridad/perímetro existente en la instalación de coubicación en la que se establece la conexión de ExpressRoute.  <br/> Aproveche la instalación de co-ubicación exclusivamente con fines de enrutamiento/interconexión y conexiones de back-lance desde una instalación de coubicación en la infraestructura de seguridad/perímetro local.  <br/> |
|Ethernet de punto a punto  <br/> |Termine la conexión punto a punto de ExpressRoute en la ubicación de la infraestructura de seguridad/perímetro local existente.  <br/> Instale una nueva infraestructura de seguridad/perímetro específica de la ruta de acceso de ExpressRoute y finalice la conexión punto a punto.  <br/> |
|De cualquier a cualquier IPVPN  <br/> |Aprovechar una infraestructura de seguridad/perímetro local existente en todas las ubicaciones que entran en la IPVPN usada para la conectividad de ExpressRoute para Office 365.  <br/> Horquilla el IPVPN usado para ExpressRoute para Office 365 a ubicaciones locales específicas designadas para servir como seguridad/perímetro.  <br/> |

Algunos proveedores de servicios también ofrecen funcionalidad de seguridad y perímetro administrada como parte de sus soluciones de integración con Azure ExpressRoute.
  
Al considerar la ubicación de la topología de las opciones red/perímetro de seguridad usadas para ExpressRoute para Office 365 conexiones, las siguientes son consideraciones adicionales
  
- La profundidad y el tipo de controles de seguridad o red pueden afectar al rendimiento y la escalabilidad de la experiencia de usuario de Office 365.

- Los flujos de salida (local-\>Microsoft) y de entrada (Microsoft\>en local) [si están habilitados] pueden tener diferentes requisitos. Es probable que sean diferentes de los destinos salientes a los destinos de Internet generales.

- Office 365 requisitos para puertos o protocolos, y las subredes IP necesarias son las mismas si el tráfico se enruta a través de ExpressRoute para Office 365 o Internet.

- La ubicación topológica de los controles de seguridad o de la red del cliente determina la última red de un extremo a otro entre el usuario y el servicio de Office 365 y puede tener un impacto importante en la latencia y la congestión de la red.

- Se recomienda a los clientes que diseñen su topología de seguridad/perímetro para su uso con ExpressRoute para Office 365 de acuerdo con los procedimientos recomendados para redundancia, alta disponibilidad y recuperación ante desastres.

Este es un ejemplo de Woodgrove Bank que compara las diferentes opciones de conectividad de Azure ExpressRoute con los modelos de seguridad perimetral descritos anteriormente.
  
### <a name="example-1-securing-azure-expressroute"></a>Ejemplo 1: protección de Azure ExpressRoute
  
En Woodgrove Bank se está pensando en implementar Azure ExpressRoute y después de planear la arquitectura óptima para el [enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md) y después de usar las instrucciones anteriores para comprender los requisitos de ancho de banda, ya que determinan el mejor método para proteger su perímetro.
  
Para Woodgrove, una organización multinacional con ubicaciones en varios continentes, la seguridad debe abarcar todos los perímetros. La opción de conectividad óptima para Woodgrove es una conexión multipunto con varias ubicaciones de emparejamiento en todo el mundo para atender las necesidades de sus empleados en cada continente. Cada continente incluye circuitos de Azure ExpressRoute redundantes en el continente y la seguridad debe abarcar todos ellos.
  
La infraestructura existente de Woodgrove es fiable y puede controlar el trabajo adicional, como resultado, Woodgrove Bank puede usar la infraestructura para Azure ExpressRoute y la seguridad del perímetro de Internet. Si este no era el caso, Woodgrove podía optar por comprar equipos adicionales para complementar el equipo existente o para controlar un tipo de conexión diferente.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Alta disponibilidad y conmutación por error con Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Le recomendamos que conprovisione al menos dos circuitos activos de cada salida con ExpressRoute a su proveedor de ExpressRoute. Este es el punto más común por el que vemos errores para los clientes y puede evitarlo fácilmente al aprovisionar un par de circuitos de ExpressRoute activos/activos. También se recomienda al menos dos circuitos de Internet activos/activos, ya que muchos servicios de Office 365 solo están disponibles a través de Internet.
  
Dentro del punto de salida de la red hay muchos otros dispositivos y circuitos que desempeñan un papel crítico en la forma en que los usuarios perciben la disponibilidad. Estas partes de los escenarios de conectividad no están cubiertas por ExpressRoute ni por los SLAs de Office 365, pero desempeñan un papel crítico en la disponibilidad del servicio de extremo a extremo según lo percibido por las personas de la organización.
  
Céntrese en las personas que usan y operan Office 365, si un error de un componente afectaría a la experiencia de los pueblos mediante el servicio, busque formas de limitar el porcentaje total de personas afectadas. Si un modo de conmutación por error es complejo desde el momento, tenga en cuenta la experiencia de los pueblos de mucho tiempo para la recuperación y busque los modos de conmutación por error automatizada y simples y de funcionamiento.
  
Fuera de la red, Office 365, ExpressRoute y el proveedor de ExpressRoute tienen distintos niveles de disponibilidad.
  
### <a name="service-availability"></a>Disponibilidad del servicio
  
- Los servicios de Office 365 están cubiertos por [contratos de nivel de servicio](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx)bien definidos, que incluyen métricas de disponibilidad y disponibilidad para servicios individuales. Uno de los motivos por los que Office 365 puede mantener estos niveles elevados de disponibilidad de servicio es la capacidad de los componentes individuales de realizar una conmutación por error de los diversos centros de recursos de Microsoft mediante la red global de Microsoft. Este failover se extiende desde el centro de recursos y la red hasta los distintos puntos de salida de Internet y permite la conmutación por error sin problemas desde la perspectiva de las personas que usan el servicio.

- ExpressRoute [proporciona un SLA de disponibilidad de 99,9%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) en circuitos dedicados individuales entre el perímetro de red de Microsoft y el proveedor de ExpressRoute o la infraestructura de asociados. Estos niveles de servicio se aplican en el nivel de circuito de ExpressRoute, que consta de [dos interconexiones independientes](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) entre el equipo de Microsoft redundante y el equipo de proveedor de red en cada ubicación de emparejamiento.

### <a name="provider-availability"></a>Disponibilidad del proveedor
  
- Las disposiciones de nivel de servicio de Microsoft se detienen en su proveedor o asociado de ExpressRoute. Este es también el primer lugar donde puede elegir las opciones que influirán en el nivel de disponibilidad. Debe evaluar de cerca las características de arquitectura, disponibilidad y resistencia que ofrece su proveedor de ExpressRoute entre el perímetro de la red y la conexión con los proveedores en cada ubicación de emparejamiento de Microsoft. Preste especial atención a los aspectos lógicos y físicos de la redundancia, el equipo de emparejamiento, el operador y los circuitos WAN proporcionados, y cualquier otro servicio de valor agregado, como servicios NAT o firewalls administrados.

### <a name="designing-your-availability-plan"></a>Diseño de su plan de disponibilidad
  
Se recomienda encarecidamente planear y diseñar la alta disponibilidad y la resistencia en los escenarios de conectividad de un extremo a otro para Office 365. Debe incluirse un diseño;
  
- no hay puntos de error únicos, incluidos los circuitos de ExpressRoute y de Internet.

- minimizar el número de personas afectadas y la duración de ese impacto en los modos de error más esperados.

- optimización del proceso de recuperación automática, repetible y simple de los modos de error más esperados.

- dar soporte a todas las demandas del tráfico de red y la funcionalidad a través de rutas redundantes, sin una degradación considerable.

Los escenarios de conectividad deben incluir una topología de red optimizada para varias rutas de red independientes y activas a Office 365. Esto ofrecerá una mejor disponibilidad de un extremo a otro que una topología optimizada solo para la redundancia en el nivel de dispositivo o equipo individual.
  
> [!TIP]
> Si los usuarios se distribuyen en varios continentes o regiones geográficas y cada una de esas ubicaciones se conecta a través de circuitos WAN redundantes en una ubicación local única donde se encuentra un solo circuito ExpressRoute, los usuarios experimentarán menos disponibilidad de servicio de extremo a extremo en lugar de un diseño de topología de red que incluye circuitos de ExpressRoute independientes que conectan las distintas regiones a la ubicación de emparejamiento más cercana.
  
Le recomendamos que conprovisione al menos dos circuitos de ExpressRoute con cada circuito conectado con una ubicación de emparejamiento geográfica distinta. Debe aprovisionar este par de circuitos activos-activos en todas las regiones en las que los usuarios usarán conectividad de ExpressRoute para los servicios de Office 365. Esto permite que cada región permanezca conectada durante un desastre que afecte a una ubicación principal, como un centro de recursos o una ubicación de emparejamiento. La configuración en como activo/activo permite que el tráfico del usuario final se distribuya en varias rutas de red. Esto reduce el ámbito de las personas afectadas durante las interrupciones del equipo o del dispositivo de red.
  
No se recomienda usar un solo circuito ExpressRoute con Internet como copia de seguridad.
  
### <a name="example-2-failover-and-high-availability"></a>Ejemplo 2: conmutación por error y alta disponibilidad
  
El diseño multigeográfico de Woodgrove Bank se ha sometido a una revisión del enrutamiento, el ancho de banda, la seguridad y ahora debe pasar por una revisión de alta disponibilidad. Woodgrove considera que la alta disponibilidad abarca tres categorías; resistencia, confiabilidad y redundancia.
  
La resistencia permite que Woodgrove se recupere rápidamente de los errores. La confiabilidad permite que Woodgrove ofrezca un resultado coherente en el sistema. La redundancia permite que Woodgrove se mueva entre una o más instancias reflejadas de la infraestructura.
  
Dentro de cada configuración perimetral, Woodgrove tiene firewalls, servidores proxy e IDENTIFICADOres redundantes. Para Norteamérica, Woodgrove tiene una configuración perimetral en el centro de recursos de Dallas y otra configuración perimetral en el centro de recursos de Virginia. El equipo redundante de cada ubicación ofrece resistencia a esa ubicación.
  
La configuración de red en Woodgrove Bank se basa en unos cuantos principios clave:
  
- Dentro de cada región geográfica, hay varios circuitos de Azure ExpressRoute.

- Cada circuito dentro de una región puede admitir todo el tráfico de red dentro de esa región.

- El enrutamiento imprimirá con claridad una o la otra ruta de acceso en función de la disponibilidad, la ubicación, etc.

- La conmutación por error entre circuitos de Azure ExpressRoute se produce automáticamente sin que Woodgrove necesite configuración o acción adicional.

- La conmutación por error entre circuitos de Internet se produce automáticamente sin necesidad de configuración o acción adicional que Woodgrove necesita.

En esta configuración, con redundancia en el nivel físico y virtual, Woodgrove Bank es capaz de ofrecer resistencia local, resistencia regional y resistencia global de una manera fiable. Woodgrove decidió esta configuración después de evaluar un solo circuito de Azure ExpressRoute por región, así como la posibilidad de conmutar por error a Internet.
  
Si Woodgrove no ha podido tener varios circuitos de Azure ExpressRoute por región, el tráfico de enrutamiento que se origina en Norteamérica al circuito de Azure ExpressRoute en Asia Pacífico agregaría un nivel inaceptable de latencia y la configuración de reenviador DNS necesaria agrega complejidad.
  
No se recomienda aprovechar Internet como una configuración de copia de seguridad. Esto rompe el principio de confiabilidad de Woodgrove, lo que da como resultado una experiencia incoherente mediante la conexión. Además, la configuración manual sería necesaria para la conmutación por error en la consideración de los anuncios BGP que se configuraron, la configuración de NAT, la configuración de DNS y la configuración del proxy. Esta complejidad de conmutación por error agregada aumenta el tiempo de recuperación y reduce su capacidad para diagnosticar y solucionar los pasos necesarios.
  
¿Sigue teniendo preguntas sobre cómo planear e implementar la administración del tráfico o Azure ExpressRoute? Lea el resto de nuestra [Guía de rendimiento y red](https://aka.ms/tune) o las [preguntas más frecuentes de Azure ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).
  
## <a name="working-with-azure-expressroute-providers"></a>Trabajar con proveedores de Azure ExpressRoute
<a name="BKMK_high-availability"> </a>

Elija las ubicaciones de los circuitos en función del ancho de banda, la latencia, la seguridad y la planeación de alta disponibilidad. Una vez que conozca las ubicaciones óptimas donde desea situar los circuitos, [Revise la lista actual de proveedores por región](https://azure.microsoft.com/documentation/articles/expressroute-locations/).
  
Trabaje con su proveedor o proveedores para seleccionar las opciones de conectividad más adecuadas: punto a punto, de varios puntos o hospedado. Recuerde que puede combinar y hacer coincidir las opciones de conectividad siempre que el ancho de banda y otros componentes redundantes admitan el diseño de alta disponibilidad y enrutamiento.
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>Temas relacionados
<a name="BKMK_high-availability"> </a>

[Evaluar la conectividad de red de Office 365](assessing-network-connectivity.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Implementación de ExpressRoute para Office 365](implementing-expressroute.md)
  
[Uso de las comunidades BGP en ExpressRoute para los escenarios de Office 365 (versión preliminar)](bgp-communities-in-expressroute.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimización de la red para Skype Empresarial Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute y QoS en Skype empresarial online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flujo de llamadas con ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
