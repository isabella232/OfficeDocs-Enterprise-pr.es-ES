---
title: Planeamiento de red con ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 2/14/2018
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
ms.assetid: 103208f1-e788-4601-aa45-504f896511cd
description: ExpressRoute para Office 365 proporciona conectividad de capa 3 entre los centros de datos de Microsoft y de la red. Los circuitos usar anuncios de ruta de protocolo de puerta de enlace de borde (BGP) de los servidores front-end de Office 365. Desde la perspectiva de sus dispositivos locales, cuando sea necesario seleccionar la ruta de acceso correcta de TCP/IP a Office 365, ExpressRoute de Azure se ve como una alternativa a Internet.
ms.openlocfilehash: 7a2c9cb8ee562c0527416aa83184de90cd204476
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897233"
---
# <a name="network-planning-with-expressroute-for-office-365"></a>Planeamiento de red con ExpressRoute para Office 365

ExpressRoute para Office 365 proporciona conectividad de capa 3 entre los centros de datos de Microsoft y de la red. Los circuitos usar anuncios de ruta de protocolo de puerta de enlace de borde (BGP) de los servidores front-end de Office 365. Desde la perspectiva de sus dispositivos locales, cuando sea necesario seleccionar la ruta de acceso correcta de TCP/IP a Office 365, ExpressRoute de Azure se ve como una alternativa a Internet.
  
Azure ExpressRoute agrega una ruta de acceso directo a un conjunto específico de características compatibles y los servicios que se ofrecen por los servidores de Office 365 dentro de centros de datos de Microsoft. ExpressRoute Azure no reemplaza la conectividad a Internet para centros de datos de Microsoft o servicios de Internet básicos, como la resolución de nombres de dominio. Deben ser ExpressRoute de Azure y los circuitos de Internet protegido y redundantes.
  
En la siguiente tabla se destaca algunas diferencias entre las conexiones de ExpressRoute de Azure en el contexto de Office 365 e internet.

|**Diferencias en la planeación de la red**|**Conexión de red de Internet**|**Conexión de red ExpressRoute**|
|:-----|:-----|:-----|
| Acceso a los servicios de internet necesarios, incluidos;  <br/>  Resolución de nombres DNS  <br/>  Comprobación de revocación de certificados  <br/>  Redes de entrega de contenido  <br/> |Sí  <br/> |Las solicitudes a Microsoft que son propiedad de infraestructura DNS o CDN puede usar la red ExpressRoute.  <br/> |
| Acceso a servicios de Office 365, incluidos;  <br/>  Exchange Online  <br/>  SharePoint Online  <br/>  Skype Empresarial Online  <br/>  Office Online  <br/>  Autenticación y Portal de office 365  <br/> |Sí, todas las aplicaciones y características  <br/> |Sí, [las características y aplicaciones específicas](https://aka.ms/o365endpoints) <br/> |
|Seguridad en perimetral local.  <br/> |Sí  <br/> |Sí  <br/> |
|Planeación de alta disponibilidad.  <br/> |Conmutación por error a una conexión de red de internet alternativas  <br/> |Conmutación por error a una conexión de ExpressRoute alternativo  <br/> |
|Conexión directa con un perfil de red predecible.  <br/> |No  <br/> |Sí  <br/> |
|Conectividad IPv6.  <br/> |Sí  <br/> |Sí  <br/> |

Expanda los siguientes títulos en la red más orientaciones de planeación. También que hemos registrado una serie de [ExpressRoute de Azure para Office 365 aprendizaje](https://channel9.msdn.com/series/aer) 10 partes que se adentra más profundos.

## <a name="existing-azure-expressroute-customers"></a>Clientes existentes de ExpressRoute de Azure

Si está utilizando un circuito de Azure ExpressRoute existente y desea agregar conectividad de Office 365 a través de este circuito, debe mirar el número de circuitos, ubicaciones de salida y el tamaño de los circuitos para asegurarse de que podrán satisfacer las necesidades de su uso de Office 365. La mayoría de los clientes requieren más ancho de banda y muchas requieren circuitos adicionales.
  
Para habilitar el acceso a Office 365 a través de los circuitos ExpressRoute de Azure existentes, [configure los filtros de ruta](https://docs.microsoft.com/azure/expressroute/how-to-routefilter-portal) para asegurarse de los servicios de Office 365 son accesibles.
  
La suscripción de Azure ExpressRoute es cliente centrado en las suscripciones de significado están vinculadas a los clientes. Como un cliente, puede tener varios circuitos ExpressRoute de Azure y puede tener acceso a muchos recursos de la nube de Microsoft a través de los circuitos. Por ejemplo, puede elegir tener acceso a un Azure hospeda la máquina virtual, un inquilino de prueba de Office 365 y un inquilino de producción de Office 365 a través de un par de circuitos ExpressRoute de Azure redundantes.
  
En esta tabla se describe los dos tipos de relaciones que puede optar por implementar a través de los circuitos.

|**Relación de interconexión**|**Privada de Azure**|**Microsoft**|
|:-----|:-----|:-----|
|**Servicios** <br/> |IaaS: Máquinas virtuales de Azure  <br/> |PaaS: Servicios públicos de Azure  <br/> SaaS: Office 365  <br/> SaaS: Dynamics 365  <br/> |
|Conexión inicio *** <br/> |Cliente a Microsoft  <br/> Cliente de Microsoft  <br/> |Cliente a Microsoft  <br/> Cliente de Microsoft  <br/> |
|**Compatibilidad con QoS** <br/> |Sin QoS  <br/> |QoS<sup>1</sup> <br/> |

<sup>1</sup> QoS admite Skype para la empresa sólo en este momento.
  
## <a name="bandwidth-planning-for-azure-expressroute"></a>Ancho de banda de planeación para ExpressRoute de Azure

Todos los clientes de Office 365 tiene necesidades de ancho de banda única según el número de personas en cada ubicación, ¿cómo activo son con cada aplicación de Office 365 y otros factores, como el uso de las configuraciones de seguridad de red o equipamiento híbrida y local.
  
Tener demasiado poco ancho de banda, se producirá una congestión, retransmisiones de datos y los retrasos impredecibles. Tener demasiado ancho de banda, se producirá en costos innecesarios. En una red existente, ancho de banda es a menudo hace referencia a en cuanto a la cantidad de espacio disponible en el circuito como un porcentaje. Tener la capacidad de un 10% de aumento es probable que esto congestión y tener la capacidad de 80% de aumento generalmente significa costos innecesarios. Asignaciones de destino de la capacidad de aumento típica son un 20% y el 50%.
  
Para buscar el nivel adecuado de ancho de banda, el mejor mecanismo es probar el consumo de red existente. Esta es la única forma de obtener una medida del uso de true y necesita que cada configuración de red y las aplicaciones están en algunos aspectos únicos. Es necesario cuando medición querrá prestar especial atención para el consumo de ancho de banda total, la latencia y la congestión de TCP para comprender la red.
  
Una vez que tiene una línea base estimada que incluye todas las aplicaciones de red, piloto Office 365 con un pequeño grupo que comprende los diferentes perfiles de personas de la organización para determinar el uso real, y use las dos mediciones para calcular la cantidad de ancho de banda que se necesita para cada ubicación de la oficina. Si hay cualquier latencia o problemas de congestión de TCP que se encuentran en las pruebas, es posible que necesita mover la salida más cerca a las personas con Office 365 o quitar exploración como descifrado de SSL o inspección intensiva de la red.
  
Todas nuestras recomendaciones acerca de qué tipo de procesamiento de red se recomienda se aplica a circuitos ExpressRoute e Internet. Lo mismo es cierto para el resto de las instrucciones en nuestro [sitio de ajuste de rendimiento](https://aka.ms/tune).
  
## <a name="applying-security-controls-to-azure-expressroute-for-office-365-scenarios"></a>Aplicación de controles de seguridad a ExpressRoute de Azure para escenarios de Office 365

Protección de la conectividad de Azure ExpressRoute comienza con los mismos principios que la protección de la conectividad a Internet. Muchos clientes optar por implementar controles de red y del perímetro a lo largo de la ruta de acceso de ExpressRoute conectar su red local a Office 365 y otros nubes de Microsoft. Estos controles pueden incluir firewalls, servidores proxy de aplicación, prevención de pérdida de datos, la detección de intrusiones, sistemas de prevención de intrusiones y así sucesivamente. En muchos casos los clientes aplicar diferentes niveles de controles para el tráfico iniciado desde local va a Microsoft, en comparación con el tráfico iniciado desde Microsoft va a red local del cliente, en comparación con el tráfico iniciado desde local va a general Destino de Internet.
  
Aquí tiene algunos ejemplos de integración de seguridad con el [modelo de conectividad a ExpressRoute](https://docs.microsoft.com/en-us/azure/expressroute/expressroute-connectivity-models) de optar por implementar.

|**Opción de integración de ExpressRoute**|**Modelo de perímetro de seguridad de red**|
|:-----|:-----|
|Colocalizada en un intercambio en la nube  <br/> |Instalar nuevos o aprovechar la infraestructura de seguridad/perimetral existente en las instalaciones de la ubicación compartida donde se establece la conexión ExpressRoute.  <br/> Aproveche co-ubicación instalaciones puramente para fines de enrutamiento de interconexión y conexiones de lance hacia atrás desde las instalaciones de ubicación compartida en la infraestructura de seguridad/perimetral local.  <br/> |
|Ethernet de punto a punto  <br/> |Finalizar la conexión de punto a punto ExpressRoute en la ubicación de infraestructura de seguridad/perimetral local existente.  <br/> Instalar la nueva infraestructura de seguridad/perimetral específico a la ruta de acceso ExpressRoute y terminar la conexión de punto a punto no existe.  <br/> |
|Cualquier IPVPN  <br/> |Aprovechar una infraestructura de seguridad/perimetral local existente en todas las ubicaciones que egreso en el IPVPN se utiliza para ExpressRoute de conectividad de Office 365.  <br/> Horquilla el IPVPN se utiliza para ExpressRoute Office 365 a ubicaciones específicas local designado para que sirva como el perímetro de seguridad.  <br/> |

Algunos proveedores de servicio también ofrecen una funcionalidad administrada/perímetro de seguridad como parte de sus soluciones de integración con Azure ExpressRoute.
  
Al considerar la colocación de topología de las opciones de perímetro de red o de seguridad que se utiliza para ExpressRoute de conexiones de Office 365, a continuación se muestran consideraciones adicionales
  
- Los controles de profundidad y el tipo de red o de seguridad pueden tener impacto en el rendimiento y la escalabilidad de la experiencia de usuario de Office 365.

- Saliente (en-local -\>Microsoft) y entrante (Microsoft -\>local) [si se habilita] flujos pueden tener requisitos diferentes. Estos son probablemente diferente de salida a general destinos de Internet.

- Requisitos de Office 365 para los puertos y protocolos y subredes IP necesarias son los mismos si se enruta el tráfico a través de ExpressRoute para Office 365 o a través de Internet.

- Colocación topológica de los controles de red o de seguridad del cliente determina la red de extremo a extremo ultimate entre el usuario y el servicio de Office 365 y puede tener un impacto importante en la latencia de red y congestión.

- Se recomienda para diseñar su topología de perímetro de seguridad o para su uso con ExpressRoute para Office 365 con arreglo a los procedimientos recomendados para la recuperación ante desastres, alta disponibilidad y redundancia de los clientes.

Este es un ejemplo de Woodgrove Bank que compara las diferentes opciones de conectividad de Azure ExpressRoute con los modelos de seguridad perimetral que se ha descrito anteriormente.
  
### <a name="example-1-securing-azure-expressroute"></a>En el ejemplo 1: Protección de ExpressRoute de Azure
  
Woodgrove Bank está considerando la implementación ExpressRoute de Azure y después de planear la arquitectura óptima para [enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md) y después de utilizar las instrucciones anteriores para comprender los requisitos de ancho de banda, es determinar el mejor método para proteger el perímetro de su.
  
Para Woodgrove, una organización multinacional con ubicaciones en varios continentes, seguridad debe abarcar todos los perímetros. La opción de conectividad óptima para Woodgrove es una conexión multipunto con varias ubicaciones de interconexión todo el mundo para atender las necesidades de sus empleados en cada continente. Cada continente incluye circuitos redundantes de Azure ExpressRoute dentro de la continente y seguridad debe abarcar todos estos.
  
Infraestructura existente de Woodgrove Bank es confiable y puede controlar el trabajo adicional, como resultado, Woodgrove Bank es capaz de utilizar la infraestructura para su seguridad perimetral Azure ExpressRoute e internet. Si no fuese el caso, podría elegir Woodgrove adquirir equipamiento adicional para complementar sus equipos existentes o para controlar un tipo diferente de conexión.
  
## <a name="high-availability-and-failover-with-azure-expressroute"></a>Alta disponibilidad y conmutación por error con ExpressRoute de Azure
<a name="BKMK_high-availability"> </a>

Se recomienda al menos dos circuitos activos desde cada salida con ExpressRoute a su proveedor de ExpressRoute de aprovisionamiento. Éste es el lugar más comunes se vea errores para los clientes y se puede evitar fácilmente mediante el aprovisionamiento de un par de circuitos ExpressRoute de activo/activo. También se recomienda al menos dos circuitos de Internet de activo/activo debido a que muchos servicios de Office 365 solo están disponibles a través de Internet.
  
Dentro del punto de salida de la red son muchos otros dispositivos y circuitos que desempeñan un papel crítico en cómo personas perciben disponibilidad. Las partes siguientes de los escenarios de conectividad no están cubiertas por ExpressRoute o SLA de Office 365, pero se reproduce un rol crítico en la disponibilidad del servicio de extremo a extremo como detectadas por las personas de su organización.
  
Centrarse en las personas que usan y operativo Office 365, si un error de cualquier uno componente afectaría a personas experiencia con el servicio, busque maneras limitar el porcentaje del total de personas afectadas. Si un modo de conmutación por error es operacional complejo, considere la posibilidad de experiencia de las personas de mucho tiempo para la recuperación y busque los modos de conmutación por error operacional simple y automatizada.
  
Fuera de la red, Office 365, ExpressRoute y su proveedor de ExpressRoute todos tienen distintos niveles de disponibilidad.
  
### <a name="service-availability"></a>Disponibilidad del servicio
  
- Servicios de Office 365 se tratan por bien definido [contratos de nivel de servicio](https://technet.microsoft.com/library/office-365-service-level-agreement.aspx), que incluyen métricas de tiempo de actividad y la disponibilidad de los servicios individuales. Una razón que Office 365 puede mantener dichos niveles de servicio alta disponibilidad es la capacidad de los componentes individuales sin ningún problema una conmutación por error entre los muchos centros de datos Microsoft, uso de la red global de Microsoft. Esta conmutación por error se extiende desde el centro de datos y la red a los varios puntos de salida de Internet y permite la conmutación por error sin ningún problema desde la perspectiva de las personas que usan el servicio.

- ExpressRoute [proporciona un SLA de disponibilidad del 99,9%](https://azure.microsoft.com/support/legal/sla/expressroute/v1_0/) en circuitos dedicados individuales entre el perímetro de red de Microsoft y la infraestructura del proveedor o socio ExpressRoute. Estos niveles de servicio se aplican en el nivel de circuito ExpressRoute, que se compone de [dos independiente interconexiones](https://azure.microsoft.com/documentation/articles/expressroute-introduction/) entre los equipos redundantes de Microsoft y el equipo del proveedor de red en cada ubicación de interconexión.

### <a name="provider-availability"></a>Disponibilidad de proveedor
  
- Detención los acuerdos de nivel de servicios de Microsoft en su proveedor de ExpressRoute o socio. También es el primer lugar, puede elegir opciones que va a influir en su nivel de disponibilidad. Estrechamente debe evaluar la arquitectura, la disponibilidad y las características de resistencia ofrece su proveedor de ExpressRoute entre el perímetro de la red y la conexión de proveedores en cada ubicación de interconexión de Microsoft. Preste especial atención a los aspectos lógicos y físicos de redundancia, equipamiento interconexión, circuitos WAN portadora proporcionado, y cualquier valor adicional agregar servicios como servicios NAT o firewalls administrados.

### <a name="designing-your-availability-plan"></a>Diseñar el plan de disponibilidad
  
Recomendamos encarecidamente que planear y diseñar una alta disponibilidad y resistencia en los escenarios de conectividad de extremo a extremo para Office 365. Debe incluir un diseño;
  
- sin puntos únicos de error, incluidos circuitos ExpressRoute e Internet.

- minimizar el número de personas afectadas y la duración de ese impacto para los modos de error más anticipados.

- optimización del proceso de recuperación simple, repetible y automática de los modos de error más anticipados.

- compatibilidad con las demandas de su tráfico de red y la funcionalidad a través de las rutas de acceso redundantes, sin una degradación sustancial completas.

Los escenarios de conectividad deben incluir una topología de red que está optimizada para varias rutas de acceso de red independiente y activa a Office 365. Esto dará como resultado una mejor disponibilidad to-end de una topología que está optimizada sólo para conseguir redundancia en el nivel de dispositivos o equipos individual.
  
> [!TIP]
> Si los usuarios están distribuidos en varios continentes o regiones geográficas y cada una de esas ubicaciones se conecta a través de circuitos WAN redundantes para una sola ubicación local donde se encuentra un único circuito ExpressRoute, los usuarios experimentarán menor disponibilidad de servicio end-to-end que un diseño de la topología de red que incluye circuitos ExpressRoute independientes que se conectan las diferentes regiones a la interconexión más cercano ubicación.
  
Se recomienda al menos dos circuitos ExpressRoute con cada conexión de circuito a con una ubicación geográfica de interconexión diferente de aprovisionamiento. Debe aprovisionar este par activa de circuitos para cada área donde los usuarios utilizarán ExpressRoute conectividad para servicios de Office 365. Esto permitirá a cada región permanecen conectadas durante un desastre que afecta a una ubicación como un centro de datos principal o interconexión. Configurarlos como activo/activo, permite que el tráfico de usuario final ser distribuidos en varias rutas de acceso de red. Esto reduce el ámbito de personas afectadas durante las interrupciones de equipamiento de red o dispositivo.
  
No se recomienda el uso de un único circuito de ExpressRoute con Internet como una copia de seguridad.
  
### <a name="example-2-failover-and-high-availability"></a>En el ejemplo 2: Alta disponibilidad y conmutación por error
  
Diseño con múltiples zonas geográficas de Woodgrove Bank ha sufrido una revisión de enrutamiento, ancho de banda, seguridad y ahora debe ir a través de una revisión de alta disponibilidad. Woodgrove piensa acerca de la alta disponibilidad como que cubren tres categorías; resistencia, la confiabilidad y la redundancia.
  
Resistencia permite Woodgrove recuperarse rápidamente de errores. Confiabilidad permite Woodgrove ofrecer un resultado coherente dentro del sistema. Redundancia permite Woodgrove para un movimiento entre una o más instancias reflejados de infraestructura.
  
Dentro de cada configuración perimetral, Woodgrove tiene redundantes Firewalls, servidores proxy y los identificadores. América del Norte, Woodgrove tiene una configuración de borde en su centro de datos de Dallas y otra configuración perimetral en su centro de datos de Virginia. Los equipos redundantes en cada ubicación ofrecen resistencia a esa ubicación.
  
La configuración de red de Woodgrove Bank se basa en función en unos principios clave:
  
- Dentro de cada región geográfica, hay varios circuitos ExpressRoute de Azure.

- Cada circuito dentro de una región puede admitir todo el tráfico de red dentro de esa región.

- Enrutamiento claramente prefiere una o la otra ruta de acceso según la disponibilidad, ubicación y así sucesivamente.

- Conmutación por error entre circuitos ExpressRoute de Azure sucede automáticamente sin configuración adicional o acción requeridos por Woodgrove.

- Conmutación por error entre circuitos de Internet que sucede automáticamente sin configuración adicional o acción requeridos por Woodgrove.

En esta configuración, con redundancia en el nivel de físico y virtual, Woodgrove Bank es capaz de ofrecer resistencia local, regional resistencia y resistencia global de forma segura. Woodgrove había elegido esta configuración después de evaluar un único circuito de Azure ExpressRoute por región, así como la posibilidad de conmutación por error a internet.
  
Si no se ha no puede tener varios circuitos ExpressRoute de Azure por región Woodgrove, enrutar el tráfico que se originan en Norteamérica al circuito ExpressRoute de Azure en Asia Pacífico agregaría un nivel inaceptable de latencia y la configuración del reenviador DNS necesaria agrega complejidad.
  
Aprovechamiento de internet como una configuración de copia de seguridad no se recomienda. Esto saltos de principio de confiabilidad de Woodgrove Bank, lo que resulta en una experiencia incoherente con la conexión. Además, la configuración manual sería necesaria para conmutación por error teniendo en cuenta los anuncios de BGP que se han configurado, configuración de NAT, configuración de DNS y la configuración del proxy. Esto agrega complejidad de conmutación por error aumenta el tiempo de recuperación y disminuye su capacidad para diagnosticar y solucionar problemas de los pasos necesarios para.
  
¿Aún tiene preguntas acerca de cómo planear e implementar la administración del tráfico o ExpressRoute de Azure? Lea el resto de nuestra [Guía de rendimiento y de la red](https://aka.ms/tune) o las [Preguntas más frecuentes sobre ExpressRoute de Azure](https://azure.microsoft.com/documentation/articles/expressroute-faqs/).
  
## <a name="working-with-azure-expressroute-providers"></a>Trabajar con proveedores de ExpressRoute de Azure
<a name="BKMK_high-availability"> </a>

Elija las ubicaciones de los circuitos en función de su ancho de banda, latencia, seguridad y planeamiento de alta disponibilidad. Una vez que sepa las ubicaciones óptimas que le gustaría colocar circuitos [Revise la lista actual de proveedores por región](https://azure.microsoft.com/documentation/articles/expressroute-locations/).
  
Trabajar con su proveedor o proveedores para seleccionar las mejores opciones de conectividad, punto a punto, multipunto u hospedado. Recuerde, puede mezclar y coincidir con las opciones de conectividad, siempre y cuando el ancho de banda y otros componentes redundantes son compatibles con el diseño de enrutamiento y la alta disponibilidad.
  
Este es un vínculo breve que se puede usar para volver: [https://aka.ms/planningexpressroute365](https://aka.ms/planningexpressroute365)
  
## <a name="related-topics"></a>Temas relacionados
<a name="BKMK_high-availability"> </a>

[Conectividad de red a Office 365](network-connectivity.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Implementación de ExpressRoute para Office 365](implementing-expressroute.md)
  
[Uso de comunidades BGP en ExpressRoute para escenarios de Office 365 (versión preliminar)](bgp-communities-in-expressroute.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimización de la red para Skype Empresarial Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute y QoS en Skype Empresarial Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flujo de llamadas con ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
