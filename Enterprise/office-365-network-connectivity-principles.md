---
title: Principios de conectividad de red de Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
f1.keywords:
- NOCSH
description: Antes de empezar a planear la red para la conectividad de red de Office 365, es importante comprender los principios de conectividad para administrar de forma segura el tráfico de Office 365 y obtener el mejor rendimiento posible. Este artículo le ayudará a comprender las instrucciones más recientes para optimizar de manera segura la conectividad de red de Office 365.
ms.openlocfilehash: 83743bfcb7a2bd3ba137947b7eb65d159d039b25
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230296"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Principios de conectividad de red de Microsoft 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Antes de empezar a planear la red para la conectividad de red de Microsoft 365, es importante comprender los principios de conectividad para administrar de forma segura el tráfico de Microsoft 365 y obtener el mejor rendimiento posible. Este artículo le ayudará a comprender las instrucciones más recientes para optimizar de forma segura la conectividad de red de Microsoft 365.
  
Las redes empresariales tradicionales están diseñadas principalmente para proporcionar a los usuarios acceso a las aplicaciones y los datos hospedados en centros de datos de empresa con una seguridad de perímetro sólida. El modelo tradicional presupone que los usuarios accederán a las aplicaciones y los datos desde dentro del perímetro de la red corporativa, a través de vínculos WAN desde sucursales o de forma remota a través de conexiones VPN.
  
La adopción de aplicaciones SaaS como Microsoft 365 mueve una combinación de servicios y datos fuera del perímetro de la red. Sin la optimización, el tráfico entre los usuarios y las aplicaciones SaaS está sujeto a la latencia que presenta la inspección de paquetes, el las redirecciones de red, las conexiones involuntarias a extremos geográficamente alejados y otros factores. Puede garantizar el mejor rendimiento y la confiabilidad de Microsoft 365 mediante la comprensión e implementación de las directrices de optimización de claves.
  
En este artículo, obtendrá información sobre:
  
- [Arquitectura 365 de Microsoft](office-365-network-connectivity-principles.md#BKMK_Architecture) tal y como se aplica a la Conectividad del cliente con la nube
- Se actualizaron los principios y estrategias de [conectividad de Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Principles) para optimizar el tráfico de red y la experiencia del usuario final
- El [servicio Web Office 365 endpoints](office-365-network-connectivity-principles.md#BKMK_WebSvc), que permite a los administradores de red consumir una lista estructurada de puntos de conexión para su uso en la optimización de red.
- [Nuevas categorías de extremos de Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) y guía de optimización
- [Comparación de la seguridad del perímetro de la red con la seguridad de extremos](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Opciones de [optimización incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt) para el tráfico de Microsoft 365
- La [prueba de conectividad de microsoft 365](https://aka.ms/netonboard), una nueva herramienta para probar la conectividad básica con Microsoft 365

## <a name="microsoft-365-architecture"></a>Arquitectura Microsoft 365
<a name="BKMK_Architecture"> </a>

Microsoft 365 es una nube de software como servicio (SaaS) distribuida que proporciona escenarios de productividad y colaboración a través de un conjunto diverso de microservicios y aplicaciones, como Exchange Online, SharePoint Online, Skype empresarial online, Microsoft Teams, Exchange Online Protection, Office en un explorador y muchos otros. Aunque las aplicaciones específicas de Microsoft 365 pueden tener características únicas tal y como se aplican a la red del cliente y conectividad a la nube, todas comparten algunas principales, metas y patrones de arquitectura principales. Estos principios y patrones de arquitectura para la conectividad son típicos para muchas otras nubes de SaaS y al mismo tiempo son diferentes de los modelos típicos de implementación de la plataforma como servicio y las nubes de infraestructura como servicio, como Microsoft Azure.
  
Una de las características arquitectónicas más importantes de Microsoft 365 (que a menudo se pierde o es mal interpretado por arquitectos de red) es que se trata de un servicio distribuido verdaderamente global, en el contexto de cómo se conectan los usuarios a él. La ubicación del inquilino de Microsoft 365 de destino es importante para comprender la localidad de dónde se almacenan los datos de clientes en la nube, pero la experiencia del usuario con Microsoft 365 no implica la conexión directa a los discos que contienen los datos. La experiencia del usuario con Microsoft 365 (incluido el rendimiento, la confiabilidad y otras características de calidad importantes) implica la conectividad a través de puertas frontales de servicio altamente distribuidas que se alejan en cientos de ubicaciones de Microsoft en todo el mundo. En la mayoría de los casos, la mejor experiencia del usuario se consigue al permitir a la red del cliente enrutar las solicitudes de usuario al punto de entrada del servicio Microsoft 365 más cercano, en lugar de conectarse a Microsoft 365 a través de un punto de salida en una ubicación central o región.
  
Para la mayoría de los clientes, los usuarios de Microsoft 365 se distribuyen en varias ubicaciones. Para obtener los mejores resultados, debe tener en cuenta los principios descritos en este documento desde el punto de vista de escalado horizontal (no se amplía), centrándose en la optimización de la conectividad con el punto de presencia más cercano de la red global de Microsoft, no en la ubicación geográfica del espacio empresarial de Microsoft 365. Básicamente, esto significa que, aunque los datos del espacio empresarial de 365 de Microsoft se pueden almacenar en una ubicación geográfica específica, la experiencia de Microsoft 365 para ese inquilino permanece distribuida y puede estar presente en proximidad (de red) en cada ubicación de usuario final que tenga el inquilino.
  
## <a name="microsoft-365-connectivity-principles"></a>Principios de conectividad de Microsoft 365
<a name="BKMK_Principles"> </a>

Microsoft recomienda los siguientes principios para lograr una conectividad y un rendimiento óptimos de Microsoft 365. Use estos principios de conectividad de Microsoft 365 para administrar el tráfico y obtener el mejor rendimiento al conectar con Microsoft 365.
  
El objetivo principal del diseño de red debería ser minimizar la latencia reduciendo el tiempo de ida y vuelta (RTT) de la red a Microsoft Global Network, la red troncal de red pública de Microsoft que interconectan todos los centros de recursos de Microsoft con baja latencia y puntos de entrada de aplicación en la nube que se propagan por todo el mundo. Puede obtener más información sobre Microsoft Global Network en la [forma en que Microsoft crea su red global de confianza y rápida](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Identificar y diferenciar el tráfico de Microsoft 365

![Identificar el tráfico de Microsoft 365](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
La identificación del tráfico de red de Microsoft 365 es el primer paso para poder diferenciar ese tráfico del tráfico de red genérico enlazado a Internet. La conectividad de Microsoft 365 puede optimizarse mediante la implementación de una combinación de enfoques como la optimización de rutas de red, las reglas de firewall, la configuración de proxy del explorador y el desvío de dispositivos de inspección de red para determinados puntos de conexión.
  
La guía de optimización anterior de Microsoft 365 dividió los puntos de conexión de Microsoft 365 en dos categorías, **obligatorias** y **opcionales**. A medida que se han agregado puntos de conexión para admitir nuevos servicios y características de Microsoft 365, hemos reorganizado los puntos de conexión de 365 de Microsoft en tres categorías: **optimizar**, **permitir**y **predeterminado**. Las directrices para cada categoría se aplican a todos los extremos de la categoría, lo que facilita la comprensión y la implementación de las optimizaciones.
  
Para obtener más información sobre las categorías de extremos de Microsoft 365 y los métodos de optimización, consulte la nueva sección de [categorías de puntos de conexión de Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Microsoft publica ahora todos los puntos de conexión de Microsoft 365 como un servicio Web y proporciona orientación sobre la mejor manera de usar estos datos. Para obtener más información sobre cómo recuperar y trabajar con puntos de conexión de 365 de Microsoft, vea el artículo [Office 365 URL e intervalos de direcciones IP](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Conexiones de red de salida de forma local

![Conexiones de red de salida de forma local](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
La salida de DNS y de Internet local es de importancia crítica para reducir la latencia de conexión y garantizar que se realizan conexiones de usuario con el punto de entrada más cercano a los servicios de Microsoft 365. En una topología de red compleja, es importante implementar el DNS local y el salida de Internet local juntos. Para obtener más información acerca de cómo Microsoft 365 enruta las conexiones de cliente al punto de entrada más cercano, vea el artículo [conectividad de clientes](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Antes de la llegada de los servicios en la nube como Microsoft 365, la conectividad de Internet del usuario final como factor de diseño en la arquitectura de red era relativamente sencilla. Cuando los servicios Internet y los sitios web se distribuyen por todo el mundo, la latencia entre los puntos de salida corporativos y un extremo de destino determinado es en gran parte una función de distancia geográfica.
  
En una arquitectura de red tradicional, todas las conexiones de Internet salientes atraviesan la red corporativa y se salida de una ubicación central. A medida que las ofertas de nube de Microsoft han madurado, una arquitectura de red distribuida con conexión a Internet se ha convertido en crítica para admitir servicios en la nube sensibles a la latencia. Microsoft Global Network se diseñó para acomodar los requisitos de latencia con la infraestructura de puertas de servicio distribuido, un fabric dinámico de puntos de entrada globales que enruta las conexiones entrantes de servicios en la nube al punto de entrada más cercano. Esto tiene como objetivo reducir la duración del "último kilómetro" para los clientes de la nube de Microsoft al acortar la ruta entre el cliente y la nube de manera eficaz.
  
Las WANs empresariales suelen estar diseñadas para backhaulr el tráfico de red a una oficina central de la compañía para la inspección antes de la salida a Internet, normalmente a través de uno o más servidores proxy. En el diagrama siguiente se muestra una topología de red de este tipo.
  
![Modelo de red empresarial tradicional](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Debido a que Microsoft 365 se ejecuta en Microsoft Global Network, que incluye servidores front-end en todo el mundo, a menudo habrá un servidor front-end que se aproximará a la ubicación del usuario. Al proporcionar la salida de Internet local y configurar los servidores DNS internos para proporcionar una resolución local de nombres para los extremos de Microsoft 365, el tráfico de red destinado a Microsoft 365 puede conectarse a los servidores front-end de Microsoft 365 lo más cerca posible al usuario. En el diagrama siguiente se muestra un ejemplo de una topología de red que permite a los usuarios que se conectan desde la oficina principal, la sucursal y las ubicaciones remotas seguir la ruta más corta hasta el punto de entrada de Microsoft 365 más cercano.
  
![Modelo de red WAN con puntos de salida regionales](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
La reducción de la ruta de acceso de red a los puntos de entrada de Microsoft 365 puede mejorar el rendimiento de conectividad y la experiencia del usuario final en Microsoft 365, y también puede ayudar a reducir el impacto de los cambios futuros a la arquitectura de red en el rendimiento y la confiabilidad de Microsoft 365.
  
Además, las solicitudes DNS pueden introducir latencia si el servidor DNS de respuesta está lejos o ocupado. Puede minimizar la latencia de la resolución de nombres al aprovisionar servidores DNS locales en ubicaciones de sucursal y asegurarse de que están configurados para almacenar en caché los registros DNS de forma adecuada.
  
Mientras que las salidas regionales pueden funcionar correctamente para Microsoft 365, el modelo de conectividad óptimo sería proporcionar siempre la salida de red en la ubicación del usuario, independientemente de si se encuentra en la red corporativa o en ubicaciones remotas como hogares, hoteles, cafeterías y aeropuertos. Este modelo de salida directo local se representa en el siguiente diagrama.
  
![Arquitectura de red de salida local](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Las empresas que han adoptado Microsoft 365 pueden aprovechar la arquitectura de puertas de servicio distribuidas de Microsoft Global Network, ya que garantizan que las conexiones de usuario a Microsoft 365 tomen la ruta más corta posible al punto de entrada de la red global de Microsoft más cercano. La arquitectura de red de salida local hace esto al permitir que el tráfico de 365 de Microsoft se enrute a través de las salidas más cercanas, independientemente de la ubicación del usuario.
  
La arquitectura de salida local tiene las siguientes ventajas sobre el modelo tradicional:
  
- Proporciona un rendimiento óptimo de Microsoft 365 mediante la optimización de la longitud de la ruta. las conexiones de usuario final se enrutan dinámicamente al punto de entrada de Microsoft 365 más cercano por parte de la infraestructura de puertas de servicio distribuido.
- Reduce la carga de la infraestructura de red corporativa al permitir la salida local.
- Protege las conexiones en ambos extremos aprovechando la seguridad de los extremos de cliente y las características de seguridad en la nube.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Evitar las redirecciones de red

![Evitar las redirecciones](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Como regla general, la ruta más corta, más directa entre el usuario y el extremo más cercano de Microsoft 365, le ofrecerá el mejor rendimiento. Un horquilla de red ocurre cuando el tráfico WAN o VPN enlazado para un determinado destino se dirige primero a otra ubicación intermedia (como pila de seguridad, agente de acceso en la nube, de puerta de enlace Web basada en la nube), lo que introduce la latencia y el redireccionamiento potencial a un extremo alejado geográficamente. Los las redirecciones de red también pueden deberse a ineficiencias de enrutamiento/emparejamiento o a búsquedas de DNS (remotas) no óptimas.
  
Para asegurarse de que la conectividad de Microsoft 365 no está sujeta a la las redirecciones de red incluso en el caso de salida local, compruebe si el ISP que se usa para proporcionar la salida a Internet de la ubicación del usuario tiene una relación de emparejamiento directo con la red global de Microsoft en una proximidad cercana a esa ubicación. Es posible que también desee configurar el enrutamiento de salida para que envíe tráfico de Microsoft 365 de confianza directamente, en lugar de proxy o tunelización a través de una nube de terceros o proveedor de seguridad de red basada en la nube que procese el tráfico enlazado a Internet. La resolución de nombres DNS local de los puntos de conexión de 365 de Microsoft ayuda a garantizar que, además del enrutamiento directo, los puntos de entrada de Microsoft 365 más cercanos se usan para las conexiones de usuario.
  
Si usa la red basada en la nube o los servicios de seguridad para su tráfico de Microsoft 365, asegúrese de que el resultado de la horquilla se evalúa y que se entiende su impacto en el rendimiento de Microsoft 365. Para ello, puede examinar el número y las ubicaciones de las ubicaciones del proveedor de servicios a través de las cuales se reenvía el tráfico en relación con el número de sucursales y los puntos de emparejamiento de la red global de Microsoft, la calidad de la relación de emparejamiento de la red del proveedor de servicios con el ISP y Microsoft, y el impacto en el rendimiento de la infraestructura del proveedor de servicios
  
Debido al gran número de ubicaciones distribuidas con puntos de entrada de Microsoft 365 y su proximidad a los usuarios finales, enrutar el tráfico de Microsoft 365 a cualquier red o proveedor de seguridad de terceros puede tener un impacto negativo en las conexiones de Microsoft 365 si la red del proveedor no está configurada para un emparejamiento de Microsoft 365 óptimo.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Evaluar los servidores proxy que se omiten, los dispositivos de inspección de tráfico y las tecnologías de seguridad duplicadas

![Servidores proxy de derivación, dispositivos de inspección de tráfico y tecnologías de seguridad duplicadas](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Los clientes empresariales deben revisar los métodos de seguridad y reducción de riesgos de red específicamente para el tráfico enlazado de Microsoft 365 y usar las características de seguridad de Microsoft 365 para reducir su dependencia de intrusión, impacto en el rendimiento y costosas tecnologías de seguridad de red para el tráfico de red de Microsoft 365.
  
La mayoría de las redes empresariales exigen la seguridad de red para el tráfico de Internet mediante tecnologías como servidores proxy, inspección de SSL, inspección de paquetes y prevención de pérdida de datos. Estas tecnologías proporcionan una importante mitigación de riesgos para las solicitudes de Internet genéricas, pero pueden reducir drásticamente el rendimiento, la escalabilidad y la calidad de la experiencia del usuario final cuando se aplican a los puntos de conexión 365 de Microsoft.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Servicio Web de extremos de Office 365

Los administradores de Microsoft 365 pueden usar una llamada de script o REST para consumir una lista estructurada de puntos de conexión del servicio Web de extremos de Office 365 y actualizar la configuración de los firewalls perimetrales y otros dispositivos de red. Esto garantizará que el tráfico enlazado para Microsoft 365 se identifica, se trata de manera adecuada y se administra de manera diferente a la del tráfico de red enlazado a sitios web genéricos y con frecuencia desconocidos. Para obtener más información sobre cómo usar el servicio Web de puntos de conexión de Office 365, vea el artículo [office 365 URL e intervalos de direcciones IP](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Scripts de PAC (configuración automática de proxy)
<a name="BKMK_WebSvc"> </a>

Los administradores de Microsoft 365 pueden crear scripts PAC (configuración automática de proxy) que se pueden entregar a los equipos de los usuarios a través de WPAD o GPO. Los scripts PAC se pueden usar para omitir los proxies para solicitudes de Microsoft 365 desde usuarios de WAN o VPN, lo que permite que el tráfico 365 de Microsoft Use conexiones directas a Internet en lugar de atravesar la red corporativa.
  
#### <a name="microsoft-365-security-features"></a>Características de seguridad de Microsoft 365
<a name="BKMK_WebSvc"> </a>

Microsoft es transparente sobre la seguridad del centro de información, la seguridad operativa y la reducción de riesgos alrededor de los servidores 365 de Microsoft y los puntos de conexión de red que representan. Las características de seguridad integradas de 365 de Microsoft están disponibles para reducir los riesgos de seguridad de la red, como prevención de pérdida de datos, anti-virus, autenticación multifactor, casilla de bloqueo de cliente, protección contra amenazas avanzada, Microsoft 365 Threat Intelligence, Microsoft 365 Secure Score, Exchange Online Protection y seguridad DDOS para red.
  
Para obtener más información sobre el centro de datos de Microsoft y la seguridad global de la red, consulte el [centro de confianza de Microsoft](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Nuevas categorías de puntos de conexión de Office 365
<a name="BKMK_Categories"> </a>

Los puntos de conexión de Office 365 representan un conjunto variado de direcciones y subredes de red. Los puntos de conexión pueden ser direcciones URL, direcciones IP o intervalos IP, y algunos puntos de conexión se muestran con puertos TCP/UDP específicos. Las direcciones URL pueden ser un FQDN como *account.Office.net*o una dirección URL de comodín como * \* . Office365.com*.
  
> [!NOTE]
> Las ubicaciones de los puntos de conexión de Office 365 dentro de la red no están directamente relacionadas con la ubicación de los datos del espacio empresarial de Microsoft 365. Por esta razón, los clientes deben mirar a Microsoft 365 como un servicio distribuido y global, y no deben intentar bloquear las conexiones de red a los puntos de conexión de Office 365 según criterios geográficos.
  
En nuestras instrucciones anteriores para administrar el tráfico de 365 de Microsoft, los puntos de conexión se han organizado en dos categorías: **obligatorios** y **opcionales**. Los puntos de conexión dentro de cada categoría requerían diferentes optimizaciones en función de la criticidad del servicio y muchos clientes se enfrentaron a desafíos para justificar la aplicación de las mismas optimizaciones de red a la lista completa de direcciones IP y URL de Office 365.
  
En el nuevo modelo, los puntos de conexión se segregan en tres categorías: **optimizar**, **permitir**y **predeterminado**, lo que proporciona una tabla dinámica basada en la prioridad en la que se centran los esfuerzos de optimización de la red para obtener las mejores mejoras de rendimiento y retorno de la inversión. Los puntos de conexión se consolidan en las categorías anteriores en función de la sensibilidad de la experiencia de usuario efectiva al sobre de la calidad, el volumen y el rendimiento de la red de los escenarios y la facilidad de implementación. Se pueden aplicar optimizaciones recomendadas de la misma forma a todos los extremos de una categoría determinada.
  
- Los extremos de **optimización** son necesarios para la conectividad a todos los servicios de Office 365 y representan un 75% de ancho de banda, conexiones y volumen de datos de Office 365. Estos extremos representan escenarios de Office 365 que son los más sensibles al rendimiento, la latencia y la disponibilidad de la red. Todos los puntos de conexión se hospedan en centros de recursos de Microsoft. Se espera que la tasa de cambio a los puntos de conexión de esta categoría sea mucho menor que para los extremos de las otras dos categorías. Esta categoría incluye un conjunto pequeño (en el orden de ~ 10) de direcciones URL clave y un conjunto definido de subredes IP dedicadas a cargas de trabajo de Office 365 principales como Exchange Online, SharePoint Online, Skype empresarial online y Microsoft Teams.

    Una lista condensada de puntos de conexión críticos bien definidos debe ayudarle a planear e implementar optimizaciones de red de gran valor para estos destinos de manera más rápida y sencilla.

    Ejemplos de *optimización* de extremos: *https://outlook.office365.com* *https:// \<tenant\> . SharePoint.com*y *https:// \<tenant\> -My.SharePoint.com*.

    Los métodos de optimización incluyen:

  - Omitir *optimización* de extremos en dispositivos de red y servicios que realizan la interceptación del tráfico, el descifrado de SSL, la inspección profunda de paquetes y el filtrado de contenido.
  - Omita los dispositivos proxy locales y los servicios proxy basados en la nube que se usan normalmente para la exploración de Internet genérica.
  - Priorizar la evaluación de estos puntos de conexión de la misma forma en que la infraestructura y los sistemas perimetrales de red son de plena confianza.
  - Priorizar la reducción o eliminación de la retransmisión WAN y facilitar la salida basada en Internet distribuida directa para estos puntos de conexión tan cerca de los usuarios y las ubicaciones de las sucursales sea lo más posible.
  - Facilite la conectividad directa con estos puntos de conexión de la nube para usuarios de VPN mediante la implementación de túneles divididos.
  - Asegúrese de que las direcciones IP devueltas por la resolución de nombres DNS coinciden con la ruta de salida de enrutamiento de estos extremos.
  - Establezca la prioridad de estos puntos de conexión para la integración de SD-WAN para una enrutamiento de latencia directa y mínima en el punto de emparejamiento de Internet más cercano de la red global de Microsoft.

- Los extremos **permitidos** son necesarios para la conectividad a características y servicios específicos de Office 365, pero no son tan sensibles al rendimiento y la latencia de la red como los de la categoría *optimizar* . El espacio de red global de estos puntos de conexión desde el punto de vista del ancho de banda y la cuenta de conexión es también más pequeño. Estos puntos de conexión están dedicados a Office 365 y se hospedan en centros de recursos de Microsoft. Representan un amplio conjunto de microservicios de Office 365 y sus dependencias (en el orden de ~ 100 direcciones URL) y se espera que cambien a una velocidad superior a las de la categoría *optimizar* . No todos los puntos de conexión de esta categoría están asociados a subredes IP dedicadas definidas.

    Las optimizaciones de red para *permitir* extremos pueden mejorar la experiencia de usuario de Office 365, pero algunos clientes pueden elegir el ámbito de esas optimizaciones de una mejor reducción para minimizar los cambios en la red.

    Algunos ejemplos de los extremos de *permiso* incluyen *https:// \* . Protection.Outlook.com* y *https://accounts.accesscontrol.windows.net* .

    Los métodos de optimización incluyen:

  - Omitir *permite* extremos en dispositivos de red y servicios que realizan la interceptación del tráfico, el descifrado de SSL, la inspección profunda de paquetes y el filtrado de contenido.
  - Priorizar la evaluación de estos puntos de conexión de la misma forma en que la infraestructura y los sistemas perimetrales de red son de plena confianza.
  - Priorizar la reducción o eliminación de la retransmisión WAN y facilitar la salida basada en Internet distribuida directa para estos puntos de conexión tan cerca de los usuarios y las ubicaciones de las sucursales sea lo más posible.
  - Asegúrese de que las direcciones IP devueltas por la resolución de nombres DNS coinciden con la ruta de salida de enrutamiento de estos extremos.
  - Establezca la prioridad de estos puntos de conexión para la integración de SD-WAN para una enrutamiento de latencia directa y mínima en el punto de emparejamiento de Internet más cercano de la red global de Microsoft.

- Los extremos **predeterminados** representan los servicios y dependencias de Office 365 que no requieren optimización y pueden tratarse mediante redes del cliente como tráfico normal de enlace a Internet. Es posible que algunos puntos de conexión de esta categoría no se hospeden en centros de recursos de Microsoft. Algunos ejemplos son *https://odc.officeapps.live.com* y *https://appexsin.stb.s-msn.com* .

Para obtener más información acerca de las técnicas de optimización de red de Office 365, vea el artículo [Administración de puntos de conexión de 365 de Office](managing-office-365-endpoints.md).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Comparación de la seguridad del perímetro de la red con la seguridad de extremos
<a name="BKMK_SecurityComparison"> </a>

El objetivo de la seguridad de red tradicional es proteger el perímetro de la red corporativa contra intrusiones y ataques malintencionados. A medida que las organizaciones adoptan Microsoft 365, algunos servicios de red y datos se migran en parte o completamente a la nube. En cuanto a los cambios fundamentales en la arquitectura de red, este proceso requiere una nueva evaluación de la seguridad de red que tenga en cuenta los factores emergentes:
  
- A medida que se adoptan los servicios en la nube, los datos y servicios de red se distribuyen entre los centros de datos locales y la nube, y la seguridad del perímetro ya no es adecuada por sí mismo.
- Los usuarios remotos se conectan a recursos corporativos tanto en centros de recursos locales como en la nube desde ubicaciones no controladas como hogares, hoteles y cafeterías.
- Las características de seguridad especialmente diseñadas se integran cada vez más en los servicios en la nube y pueden potencialmente complementar o reemplazar los sistemas de seguridad existentes.

Microsoft ofrece una amplia gama de características de seguridad de Microsoft 365 y proporciona una guía preceptiva para la utilización de los procedimientos recomendados de seguridad que pueden ayudarle a garantizar la seguridad de los datos y de la red para Microsoft 365. Entre los procedimientos recomendados se incluyen los siguientes:
  
- **Usar multi-factor Authentication (MFA)** La MFA agrega una capa de protección adicional a una estrategia de contraseña segura, ya que obliga a los usuarios a confirmar una llamada telefónica, un mensaje de texto o una notificación de la aplicación en el smartphone después de escribir correctamente su contraseña.

- **Usar Microsoft Cloud App Security** Configure las directivas para realizar un seguimiento de la actividad anómala y actuar sobre ella. Configurar alertas con Microsoft Cloud App Security para que los administradores puedan revisar la actividad de los usuarios inusual o arriesgada, como descargar grandes cantidades de datos, varios intentos de inicio de sesión incorrectos o conexiones de direcciones IP desconocidas o peligrosas.

- **Configurar prevención de pérdida de datos (DLP)** DLP le permite identificar datos confidenciales y crear directivas que ayuden a impedir que los usuarios compartan los datos por accidente o de forma intencionada. DLP funciona en Microsoft 365, incluidos Exchange Online, SharePoint Online y OneDrive para que los usuarios puedan cumplir sin interrumpir el flujo de trabajo.

- **Usar caja de caja del cliente** Como administrador de Microsoft 365, puede usar la caja de control del cliente para controlar cómo un ingeniero de soporte técnico de Microsoft obtiene acceso a los datos durante una sesión de ayuda. En casos donde el ingeniero requiere acceso a los datos para solucionar un problema, la Caja de seguridad del cliente le permite aprobar o rechazar la solicitud de acceso.

- **Usar la puntuación segura de Office 365** Una herramienta de análisis de seguridad que recomienda lo que se puede hacer para reducir aún más el riesgo. Puntuación segura busca la configuración y las actividades de Microsoft 365 y las compara con una línea base establecida por Microsoft. Obtendrá una puntuación en función de la alineación que tenga con los procedimientos recomendados de seguridad.

Un enfoque holístico de la seguridad mejorada debe incluir la consideración de lo siguiente:
  
- Destaque el énfasis de la seguridad perimetral hacia la seguridad de los extremos mediante la aplicación de características de seguridad de clientes de Office y basadas en la nube.
  - Reducción del perímetro de seguridad en el centro de seguridad
  - Habilitar la confianza equivalente para los dispositivos de usuario dentro de la oficina o en ubicaciones remotas
  - Centrarse en proteger la ubicación de los datos y la ubicación del usuario
  - Los equipos de usuarios administrados tienen mayor confianza con la seguridad de extremos
- Administrar toda la seguridad de la información de forma holística, no centrarse exclusivamente en el perímetro
  - Redefinir WAN y crear seguridad de red perimetral al permitir que el tráfico de confianza eluda los dispositivos de seguridad y separe los dispositivos no administrados en las redes Wi-Fi de invitado
  - Reducir los requisitos de seguridad de red del perímetro WAN corporativo
  - Algunos dispositivos de seguridad del perímetro de red, como firewalls, aún son necesarios, pero la carga disminuye
  - Garantiza la salida local para el tráfico de Microsoft 365
- Las mejoras se pueden dirigir incrementalmente como se describe en la sección [optimización incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt) . Algunas técnicas de optimización pueden ofrecer mejores proporciones de costos y beneficios en función de la arquitectura de la red y debe elegir optimizaciones que sean más adecuadas para su organización.

Para obtener más información acerca de la seguridad y el cumplimiento de Microsoft 365, vea el artículo [microsoft 365 Security](https://docs.microsoft.com/microsoft-365/security) y [Microsoft 365 Security](https://docs.microsoft.com/microsoft-365/compliance).
  
## <a name="incremental-optimization"></a>Optimización incremental
<a name="BKMK_IncOpt"> </a>

Hemos representado el modelo de conectividad de red ideal para SaaS anteriormente en este artículo, pero para muchas organizaciones grandes con arquitecturas de red históricamente complejas, no será práctico realizar todos estos cambios directamente. En esta sección, analizaremos una serie de cambios incrementales que pueden ayudar a mejorar el rendimiento y la confiabilidad de Microsoft 365.
  
Los métodos que usará para optimizar el tráfico de 365 de Microsoft variarán según la topología de red y los dispositivos de red que haya implementado. Las grandes empresas con muchas ubicaciones y prácticas complejas de seguridad de red deberán desarrollar una estrategia que incluya la mayoría o todos los principios que se enumeran en la sección [principios de conectividad de 365 de Microsoft](office-365-network-connectivity-principles.md#BKMK_Principles) , mientras que las organizaciones más pequeñas podrían tener que considerar solo uno o dos.
  
Puede enfocar la optimización como proceso incremental, aplicando cada método sucesivamente. En la tabla siguiente se enumeran los métodos de optimización de claves por orden de impacto en la latencia y la confiabilidad para el mayor número de usuarios.
  
|**Método de optimización**|**Descripción**|**Impacto**|
|:-----|:-----|:-----|
|Resolución de DNS y salida de Internet locales  <br/> |Aprovisione servidores DNS locales en cada ubicación y asegúrese de que las conexiones de Microsoft 365 se salgan de Internet lo más cercanas posible a la ubicación del usuario.  <br/> | Minimizar la latencia  <br/>  Mejorar la conectividad fiable con el punto de entrada de Microsoft 365 más cercano  <br/> |
|Agregar puntos de salida regionales  <br/> |Si la red corporativa tiene varias ubicaciones pero solo un punto de salida, agregue puntos de salida regionales para permitir que los usuarios se conecten al punto de entrada de Microsoft 365 más cercano.  <br/> | Minimizar la latencia  <br/>  Mejorar la conectividad fiable con el punto de entrada de Microsoft 365 más cercano  <br/> |
|Omitir servidores proxy y dispositivos de inspección  <br/> |Configure los exploradores con archivos PAC que envíen solicitudes de Microsoft 365 directamente a puntos de salida.  <br/> Configure los enrutadores y los firewalls perimetrales para permitir el tráfico de Microsoft 365 sin inspección.  <br/> | Minimizar la latencia  <br/>  Reducir la carga de los dispositivos de red  <br/> |
|Habilitar conexión directa para usuarios de VPN  <br/> |Para los usuarios de VPN, habilite conexiones de 365 Microsoft para conectarse directamente desde la red del usuario, en lugar de hacerlo a través del túnel VPN mediante la implementación de túneles divididos.  <br/> | Minimizar la latencia  <br/>  Mejorar la conectividad fiable con el punto de entrada de Microsoft 365 más cercano  <br/> |
|Migrar de WAN tradicional a SD-WAN  <br/> |Las redes de área extensa de SD-WAN (software definido por software) simplifican la administración de WAN y mejoran el rendimiento al reemplazar los enrutadores WAN tradicionales por dispositivos virtuales, de manera similar a la virtualización de los recursos de proceso mediante máquinas virtuales (VM).  <br/> | Mejorar el rendimiento y la facilidad de administración del tráfico de WAN  <br/>  Reducir la carga de los dispositivos de red  <br/> |

## <a name="related-topics"></a>Temas relacionados

[Introducción a la conectividad de red 365 de Microsoft](office-365-networking-overview.md)

[Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md)

[Direcciones URL e intervalos de direcciones IP de Office 365](urls-and-ip-address-ranges.md)

[Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md)

[Evaluar la conectividad de red de Microsoft 365](assessing-network-connectivity.md)

[Planeamiento de red y ajuste del rendimiento para Microsoft 365](network-planning-and-performance.md)

[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)

[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)

[Redes de entrega de contenido](content-delivery-networks.md)

[Prueba de conectividad de Microsoft 365](https://aka.ms/netonboard)

[Cómo Microsoft crea su red global rápida y fiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog de redes de Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
