---
title: Principios de conectividad de red de Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
search.appverid: MET150
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
f1.keywords:
- NOCSH
description: Antes de empezar a planear la red para la conectividad de red de Office 365, es importante comprender los principios de conectividad para administrar de forma segura el tráfico de Office 365 y obtener el mejor rendimiento posible. Este artículo le ayudará a comprender las instrucciones más recientes para optimizar de forma segura la conectividad de red de Office 365.
ms.openlocfilehash: 399f00412bfd5c26a5910b9dcaa141a4fababd93
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502705"
---
# <a name="microsoft-365-network-connectivity-principles"></a>Principios de conectividad de red de Microsoft 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Antes de empezar a planear la red para la conectividad de red de Microsoft 365, es importante comprender los principios de conectividad para administrar de forma segura el tráfico de Microsoft 365 y obtener el mejor rendimiento posible. Este artículo le ayudará a comprender las instrucciones más recientes para optimizar de forma segura la conectividad de red de Microsoft 365.
  
Las redes empresariales tradicionales se diseñan principalmente para proporcionar a los usuarios acceso a las aplicaciones y a los datos alojados en centros de datos operados por empresas con una seguridad del perímetro robusta. El modelo tradicional presupone que los usuarios accederán a las aplicaciones y a los datos desde dentro del perímetro de la red corporativa, mediante vínculos WAN de sucursales o de forma remota mediante conexiones VPN.
  
La adopción de aplicaciones SaaS como Microsoft 365 traslada cierta combinación de servicios y de datos fuera del perímetro de la red. Sin la optimización, el tráfico entre los usuarios y las aplicaciones SaaS está sujeto a la latencia causada por la inspección de paquetes, las redirecciones de red, las conexiones involuntarias a puntos de conexión alejados geográficamente y otros factores. Para asegurar el máximo rendimiento y confiabilidad de Microsoft 365, necesita entender e implementar directrices claves para la optimización.
  
En este artículo, obtendrá información sobre:
  
- [La arquitectura 365 de Microsoft](office-365-network-connectivity-principles.md#BKMK_Architecture) cuando se aplica a la conectividad del cliente con la nube
- La actualización de [principios de conectividad de Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Principles) y estrategias para optimizar el tráfico de red y la experiencia del usuario final
- El [servicio web de puntos de conexión de Office 365](office-365-network-connectivity-principles.md#BKMK_WebSvc), que permite a los administradores de red emplear una lista estructurada de puntos de conexión para su uso en la optimización de la red
- Guía sobre las [nuevas categorías de puntos de conexión de Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) y la optimización
- [Comparación de la seguridad del perímetro de la red con la seguridad del punto de conexión](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Opciones de [optimización incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt) del tráfico de Microsoft 365
- La [prueba de conectividad de Microsoft 365](https://aka.ms/netonboard), una nueva herramienta para probar la conectividad básica a Microsoft 365

## <a name="microsoft-365-architecture"></a>Arquitectura de Microsoft 365
<a name="BKMK_Architecture"> </a>

Microsoft 365 es una nube distribuida de software como servicio (SaaS) que proporciona escenarios de productividad y colaboración a través de un conjunto diverso de microservicios y aplicaciones, como Exchange Online, SharePoint Online, Skype Empresarial Online, Microsoft Teams, Exchange Online Protection, Office en un explorador y muchos más. Si bien las aplicaciones específicas de Microsoft 365 pueden tener sus características únicas cuando se aplican a la red del cliente y a la conectividad con la nube, todas comparten algunas entidades de seguridad, metas y patrones de arquitectura claves. Estos patrones de arquitectura y principios para la conectividad son habituales en muchas otras nubes de SaaS y, al mismo tiempo, son distintos de los modelos de implementación habituales de las nubes de plataforma como servicio y de infraestructura como servicio, como Microsoft Azure.
  
Una de las características de la arquitectura de Microsoft 365 más importantes (y que suelen pasarse por alto o son malinterpretadas por arquitectos de red) es que es verdaderamente un servicio distribuido global, teniendo en cuenta cómo se conectan los usuarios a dicho servicio. La ubicación del inquilino de destino de Microsoft 365 resulta importante para entender dónde se sitúan los datos de los clientes que se almacenan en la nube, pero la experiencia de usuario de Microsoft 365 no implica una conexión directa con los discos que contienen los datos. La experiencia de usuario de Microsoft 365 (incluidos el rendimiento, la confiabilidad y otras características de calidad importantes) implica conectividad a través de puertas frontales de servicio enormemente distribuido que se escalan horizontalmente en centenares de ubicaciones de Microsoft en todo el mundo. En la mayoría de los casos, la mejor experiencia de usuario se logra al permitir que la red del cliente redirija las solicitudes del usuario al punto de entrada de servicio de Microsoft 365, en lugar de conectarse a Microsoft 365 a través de un punto de salida en una ubicación central o una región.
  
Para la mayoría de los clientes, los usuarios de Microsoft 365 se distribuyen en muchas ubicaciones. Para obtener los mejores resultados, debe tener en cuenta los principios descritos en este documento desde el punto de vista de escalado horizontal (en vez de vertical), para centrarse en optimizar la conectividad con el punto de presencia más cercano en la Red Global de Microsoft, y no con la ubicación geográfica del inquilino de Microsoft 365. Esto último significa que, aunque los datos del inquilino de Microsoft 365 se almacenen en una ubicación geográfica específica, la experiencia de Microsoft 365 para ese inquilino permanecerá distribuida y podrá encontrarse en la proximidad (de red) de la ubicación de cada usuario final que el inquilino tenga.
  
## <a name="microsoft-365-connectivity-principles"></a>Principios de conectividad de Microsoft 365
<a name="BKMK_Principles"> </a>

Microsoft recomienda los siguientes principios para lograr una conectividad y un rendimiento óptimos de Microsoft 365. Utilice estos principios de conectividad de Microsoft 365 para administrar el tráfico y obtener el máximo rendimiento al conectarse a Microsoft 365.
  
El objetivo principal del diseño de la red debe ser minimizar la latencia mediante la reducción del tiempo de ida y vuelta (RTT) desde su red a la Red Global de Microsoft, la red troncal de conexión pública de Microsoft que interconecta todos los centros de datos de Microsoft con la baja latencia y los puntos de entrada de aplicaciones en la nube distribuidos por todo el mundo. Puede obtener más información sobre la Red Global de Microsoft en [Cómo construye Microsoft su red global rápida y confiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-microsoft-365-traffic"></a>Identificar y diferenciar el tráfico de Microsoft 365

![Identificar el tráfico de Microsoft 365](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Identificar el tráfico de red 365 de Microsoft es el primer paso para poder diferenciar dicho tráfico del tráfico de red genérico de Internet. La conectividad de Microsoft 365 puede optimizarse mediante la implementación de una combinación de enfoques como la optimización de rutas de red, reglas de firewall, la configuración de proxy del explorador y la omisión de dispositivos de inspección de red en determinados puntos de conexión.
  
Las instrucciones anteriores de optimización de Microsoft 365 dividían los puntos de conexión de Microsoft 365 en dos categorías: **Necesarios** y **Opcionales**. Debido a que se han agregado puntos de conexión para admitir los nuevos servicios y características de Microsoft 365, hemos reorganizado los puntos de conexión de Microsoft 365 en tres categorías: **Optimizar**, **Permitir** y **Predeterminado**. Las instrucciones para cada categoría se aplican a todos los puntos de conexión de dicha categoría, para facilitar la comprensión y la implementación de las optimizaciones.
  
Para más información sobre las categorías de puntos de conexión de Microsoft 365 y los métodos de optimización, consulte la sección [Nuevas categorías de puntos de conexión de Office 365](office-365-network-connectivity-principles.md#BKMK_Categories).
  
Microsoft publica ahora todos los puntos de conexión de Microsoft 365 como un servicio web y proporciona instrucciones sobre cómo dar a estos datos el mejor uso posible. Para más información sobre cómo recuperar puntos de conexión de Microsoft 365 y trabajar con ellos, consulte el artículo [Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Conexiones de red de salida de forma local

![Conexiones de red de salida de forma local](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
La salida local de DNS y de Internet resulta fundamental para reducir la latencia de la conexión y garantizar que las conexiones del usuario se realicen al punto más cercano de entrada a los servicios de Microsoft 365. Dado que se trata de una topología de la red compleja, es importante implementar juntas la salida local de DNS y la salida local de Internet. Para más información sobre cómo Microsoft 365 redirige conexiones de cliente al punto de entrada más cercano, consulte el artículo [Conectividad de cliente](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Antes de los servicios en la nube como Microsoft 365, la conectividad de Internet del usuario final como factor de diseño en la arquitectura de red era relativamente sencilla. Cuando se distribuyen los servicios de Internet y los sitios web por todo el mundo, la latencia entre los puntos de salida corporativos y un determinado punto de conexión de destino depende en gran medida de la distancia geográfica.
  
En una arquitectura de red tradicional, todas las conexiones de Internet salientes atraviesan la red corporativa y salen de una ubicación central. A medida que las ofertas de la nube de Microsoft han madurado, ha aumentado la importancia de contar con una arquitectura de red distribuida accesible desde Internet para poder admitir los servicios en la nube sensibles a la latencia. La Red Global de Microsoft se ha diseñado para dar cabida a los requisitos de latencia con la infraestructura de puerta frontal de servicio distribuido, un tejido dinámico de puntos de entrada global que redirige las conexiones entrantes de servicios en la nube al punto de entrada más cercano. El objetivo es reducir la longitud de la "última milla" para los clientes de la nube de Microsoft al acortar de forma eficaz la ruta entre el cliente y la nube.
  
Las redes WAN empresariales suelen diseñarse para transmitir en la red de retorno (backhaul) el tráfico de red a una oficina central de la empresa para su inspección antes de su salida a Internet, normalmente mediante uno o varios servidores proxy. El siguiente diagrama ilustra una topología de red de este tipo.
  
![Modelo de red empresarial tradicional](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Dado que Microsoft 365 se ejecuta en la Red Global de Microsoft, que incluye servidores front-end distribuidos por todo el mundo, con frecuencia se podrá encontrar servidor front-end cerca de la ubicación del usuario. Si se proporciona la salida local de Internet y se configuran los servidores internos DNS para ofrecer resolución de nombres locales para los puntos de conexión de Microsoft 365, el tráfico de red destinado a Microsoft 365 puede conectarse a los servidores front-end de Microsoft 365 más cercanos al usuario. El siguiente diagrama muestra un ejemplo de una topología de red que permite a usuarios —que se conectan desde la oficina principal, desde la sucursal y desde ubicaciones remotas— seguir la ruta más corta al punto de entrada de Microsoft 365 más cercano.
  
![Modelo de red WAN con puntos de salida regionales](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Acortar de esta forma la ruta de red a los puntos de entrada de Microsoft 365 puede mejorar el rendimiento de la conectividad y la experiencia del usuario final en Microsoft 365. Asimismo, puede contribuir a reducir el impacto que los cambios futuros en la arquitectura de la red puedan tener en el rendimiento y la confiabilidad de Microsoft 365.
  
Además, las solicitudes DNS pueden introducir latencia si el servidor DNS de respuesta está lejos o ocupado. Puede minimizar la latencia de la resolución de nombres al aprovisionar servidores DNS locales en las ubicaciones de las sucursales y al configurarlos para que almacenen en caché los registros DNS de manera adecuada.
  
Aunque las salidas regionales pueden funcionar bien con Microsoft 365, el modelo de conectividad óptimo consiste en ofrecer siempre la salida de red en la ubicación del usuario, independientemente de si se encuentra en la red corporativa o en ubicaciones remotas como hogares, hoteles, cafeterías y aeropuertos. El siguiente diagrama representa este modelo de salida directa local.
  
![Arquitectura de red de salida local](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Para aprovechar la arquitectura de puerta frontal de servicio distribuido de la Red Global de Microsoft, las empresas que han adoptado Microsoft 365 deben asegurarse de que las conexiones de los usuarios a Microsoft 365 empleen la ruta más corta posible al punto de entrada más cercano de la Red Global de Microsoft. La arquitectura de la red de salida local realiza esto al permitir redirigir el tráfico de Microsoft 365 a la salida más cercana, sea cual sea la ubicación del usuario.
  
La arquitectura de salida local presenta las siguientes ventajas respecto al modelo tradicional:
  
- Ofrece rendimiento óptimo de Microsoft 365 al optimizar la longitud de la ruta. las conexiones de los usuarios finales se redirigen dinámicamente al punto de entrada más cercano de Microsoft 365 mediante la infraestructura de puerta frontal de servicio distribuido.
- Reduce la carga en la infraestructura de la red corporativa, ya que permite la salida local.
- Protege las conexiones en ambos extremos aprovechando la seguridad del punto de conexión del cliente y las características de seguridad de la nube.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Evitar las redirecciones de red

![Evite las redirecciones](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Como regla general, la ruta más corta y directa entre el usuario y el punto de conexión más cercano de Microsoft 365 le ofrecerá el mejor rendimiento. Las redirecciones de red tienen lugar cuando el tráfico WAN o VPN con un destino en particular se dirige por primera vez a otra ubicación intermedia (como una pila de seguridad, un agente de acceso a la nube o una puerta de enlace web basada en la nube), lo que introduce latencia y un posible redireccionamiento a un extremo lejano geográficamente. Las redirecciones de red también pueden deberse a las ineficiencias de enrutamiento/emparejamiento o a búsquedas DNS no ideales (remotas).
  
Para garantizar que la conectividad de Microsoft 365 no esté sujeta a la redirecciones de red, incluso en el caso de salida local, compruebe si el ISP que se usa para proporcionar salida de Internet en la ubicación del usuario tiene una relación de emparejamiento directa con la Red Global de Microsoft cercana a esa ubicación. También es una buena idea configurar el enrutamiento de salida para que envíe directamente el tráfico de confianza de Microsoft 365, en lugar de enviarlo a través de un proxy o túnel mediante una nube de terceros o un proveedor de seguridad de red basada en la nube que procese el tráfico de Internet. La resolución de nombres DNS locales de los puntos de conexión de Microsoft 365 le ayuda a garantizar que, además de usar el enrutamiento directo, se utilicen los puntos de entrada de Microsoft 365 más cercanos para las conexiones de los usuarios.
  
Si usa servicios de red o seguridad basados en la nube para el tráfico de Microsoft 365, asegúrese de que se evalúen los resultados de la redirección y de que se comprenda su impacto en el rendimiento de Microsoft 365. Para ello, puede examinar el número y la ubicación de las ubicaciones de los proveedores de servicios a través de los que se reenvía el tráfico en relación con el número de sucursales y de puntos de emparejamiento de la Red Global de Microsoft, la calidad de la relación de emparejamiento de red del proveedor de servicio con su ISP y Microsoft, y el impacto que tiene la transmisión en la red de retorno (backhaul) en el rendimiento de la infraestructura del proveedor de servicios.
  
Debido a la gran cantidad de ubicaciones distribuidas con puntos de entrada de Microsoft 365 y su proximidad a los usuarios finales, el enrutamiento del tráfico de Microsoft 365 a cualquier red o proveedor de seguridad de terceros puede tener un impacto adverso en las conexiones de Microsoft 365 si la red del proveedor no está configurada para un emparejamiento óptimo de Microsoft 365.
  
<a name="BKMK_P4"> </a>
### <a name="assess-bypassing-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Evaluar la omisión de servidores proxy, dispositivos de inspección del tráfico y tecnologías de seguridad duplicadas

![Omitir servidores proxy, dispositivos de inspección del tráfico y tecnologías de seguridad duplicadas](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Los clientes empresariales deberían revisar sus métodos de seguridad y de reducción de riesgos de la red específicamente para el tráfico vinculado de Microsoft 365, así como usar las características de seguridad de Microsoft 365 para reducir su dependencia de tecnologías de seguridad de red para el tráfico de red de Microsoft 365 que son invasivas y costosas y tienen un impacto en el rendimiento.
  
La mayoría de las redes empresariales exigen seguridad de red para el tráfico de Internet mediante tecnologías como servidores proxy, inspección SSL, inspección de paquetes y sistemas de prevención de pérdida de datos. Estas tecnologías proporcionan una importante mitigación de riesgos para las solicitudes de Internet genéricas, pero pueden reducir drásticamente el rendimiento, la escalabilidad y la calidad de la experiencia del usuario final cuando se aplican a los puntos de conexión de Microsoft 365.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Servicio web de Puntos de conexión de Office 365

Los administradores de Microsoft 365 pueden usar un script o una llamada REST para consumir una lista estructurada de puntos de conexión desde el servicio web de Puntos de conexión de Office 365 y actualizar la configuración de los firewalls perimetrales y otros dispositivos de red. Esto garantizará que el tráfico vinculado a Microsoft 365 se identifique, se trate de forma adecuada y se administre de una manera diferente del tráfico de red vinculado a sitios web de Internet genéricos y a menudo desconocidos. Para más información sobre cómo utilizar el servicio web de Puntos de conexión de Office 365, consulte el artículo [Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Scripts de configuración automática de proxy (PAC)
<a name="BKMK_WebSvc"> </a>

Los administradores de Microsoft 365 pueden crear scripts PAC (configuración automática del proxy) que se pueden enviar a los equipos de los usuarios a través de WPAD o GPO. Se pueden usar scripts PAC para omitir los servidores proxy para las solicitudes de Microsoft 365 de usuarios WAN o VPN, lo que permite al tráfico de Microsoft 365 usar conexiones directas de Internet en lugar de atravesar la red corporativa.
  
#### <a name="microsoft-365-security-features"></a>Características de seguridad de Microsoft 365
<a name="BKMK_WebSvc"> </a>

Microsoft es transparente en relación con la seguridad de centros de datos, la seguridad operacional y la reducción de riesgos relacionados con los servidores de Microsoft 365 y con los puntos de conexión de red que representan. Las características de seguridad integradas de Microsoft 365 están disponibles para reducir los riesgos de seguridad de la red. Dichas características incluyen la prevención de la pérdida de datos, antivirus, autenticación multifactor, Caja de seguridad del cliente, Protección contra amenazas avanzada, Inteligencia sobre amenazas de Microsoft 365, Puntuación segura de Microsoft 365, Exchange Online Protection y seguridad de la red contra DDoS.
  
Para más información sobre el centro de datos de Microsoft y la seguridad de la Red Global, consulte el [Centro de confianza de Microsoft](https://www.microsoft.com/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Nuevas categorías de puntos de conexión de Office 365
<a name="BKMK_Categories"> </a>

Los puntos de conexión de Office 365 representan un conjunto variado de direcciones y subredes de red. Los puntos de conexión pueden ser direcciones URL, direcciones IP o intervalos IP, y algunos puntos de conexión se muestran con puertos TCP/UDP específicos. Las direcciones URL pueden ser un FQDN como *account.office.net* o una dirección URL con carácter comodín como *\*. office365.com*.
  
> [!NOTE]
> Las ubicaciones de los puntos de conexión de Office 365 en la red no están directamente relacionadas con la ubicación de los datos de inquilino de Microsoft 365. Por este motivo, los clientes deberían considerar Microsoft 365 como un servicio distribuido y global, y no deben intentar bloquear las conexiones de red a los puntos de conexión de Office 365 en función de criterios geográficos.
  
En nuestras instrucciones anteriores para administrar el tráfico de Microsoft 365, los puntos de conexión se organizaban en dos categorías: **Necesarios** y **Opcionales**. Los puntos de conexión en cada categoría requerían diferentes optimizaciones en función de la importancia del servicio, y muchos clientes se enfrentaban a dificultades para justificar la aplicación de las mismas optimizaciones de red a la lista completa de direcciones IP y URL de Office 365.
  
En el nuevo modelo, los puntos de conexión se dividen en tres categorías: **Optimizar**, **Permitir** y **Predeterminado**, lo que proporciona un eje basado en las prioridades en el que se pueden centrar los esfuerzos de optimización de la red para lograr todas las mejoras posibles de rendimiento y el retorno de la inversión. Los puntos de conexión se consolidan en las categorías anteriores según la sensibilidad de la experiencia efectiva del usuario en relación con el volumen y la calidad de la red, el campo de rendimiento de los escenarios y la facilidad de implementación. Se pueden aplicar las optimizaciones recomendadas de la misma forma a todos los puntos de conexión de una categoría determinada.
  
- Los puntos de conexión de la categoría **Optimizar** son obligatorios para la conectividad a todos los servicios de Office 365 y representan más del 75 % del ancho de banda, las conexiones y el volumen de datos de Office 365. Estos puntos de conexión representan los escenarios de Office 365 que son más sensibles al rendimiento, la latencia y la disponibilidad de la red. Todos los puntos de conexión se hospedan en centros de datos de Microsoft. Se espera que la tasa de cambio para los puntos de conexión de esta categoría sea mucho menor que para los puntos de conexión de las otras dos categorías. Esta categoría contiene un conjunto reducido (en el orden de ~ 10) de direcciones URL y un conjunto definido de subredes IP dedicadas a cargas centrales de trabajo de Office 365, como Exchange Online, SharePoint Online, Skype Empresarial online y Microsoft Teams.

    Una lista resumida de puntos de conexión críticos bien definidos le ayudará a planear e implementar optimizaciones de red de alto valor para estos destinos de forma más rápida y sencilla.

    Algunos ejemplos de puntos de conexión de *Optimizar* son *https://outlook.office365.com* *https://\<tenant\>.sharepoint.com* y *https://\<tenant\>-my.sharepoint.com*.

    Entre los métodos de optimización se incluyen:

  - Omitir los puntos de conexión de *Optimizar* en dispositivos y servicios de red que realicen interceptación de tráfico, descifrado SSL, inspección profunda de paquetes y filtrado de contenidos.
  - Omitir los dispositivos de proxy locales y servicios de proxy basados en la nube que se suelen usar para la exploración genérica de Internet.
  - Priorizar la evaluación de estos puntos de conexión como puntos de plena confianza para sus sistemas perimetrales y de infraestructura de red.
  - Priorizar la reducción o eliminación de la transmisión en la red de retorno (backhaul) de WAN y facilitar la salida directa distribuida basada en Internet para estos puntos de conexión lo más cerca posible de la ubicación del usuario o de la sucursal.
  - Facilitar la conectividad directa a estos puntos de conexión de la nube para los usuarios VPN mediante la implementación de tunelización dividida.
  - Asegúrese de que las direcciones IP que devuelve la resolución de nombres DNS coincidan con la ruta de salida de enrutamiento para estos puntos de conexión.
  - Dé prioridad a estos puntos de conexión para la integración SD-WAN para el enrutamiento de latencia directa y mínima al punto más cercano de emparejamiento de Internet de la Red Global de Microsoft.

- Los puntos de conexión de **Permitir** son obligatorios para la conectividad a características y servicios específicos de Office 365, pero no son tan sensibles al rendimiento y la latencia de la red como los de la categoría *Optimizar*. La huella de la red general de estos puntos de conexión, desde el punto de vista del ancho de banda y del recuento de conexiones, es también menor. Estos puntos de conexión se dedican a Office 365 y se hospedan en centros de datos de Microsoft. Representan un amplio conjunto de microservicios de Office 365 y de sus dependencias (en el orden de ~ 100 direcciones URL) y se espera que cambien a una tasa mayor que los puntos de conexión de la categoría *Optimizar*. No todos los puntos de conexión de esta categoría están asociados a subredes IP definidas y dedicadas.

    Las optimizaciones de red para los puntos de conexión de *Permitir* pueden mejorar la experiencia de usuario de Office 365, pero puede que algunos clientes opten por definir las optimizaciones de manera más restringida, para minimizar los cambios en la red.

    Algunos ejemplos de puntos de conexión de *Permitir* incluyen *https://\*.protection.outlook.com* y *https://accounts.accesscontrol.windows.net*.

    Entre los métodos de optimización se incluyen:

  - Omitir los puntos de conexión de *Permitir* en dispositivos y servicios de red que realicen interceptación de tráfico, descifrado SSL, inspección profunda de paquetes y filtrado de contenidos.
  - Priorizar la evaluación de estos puntos de conexión como puntos de plena confianza para sus sistemas perimetrales y de infraestructura de red.
  - Priorizar la reducción o eliminación de la transmisión en la red de retorno (backhaul) de WAN y facilitar la salida directa distribuida basada en Internet para estos puntos de conexión lo más cerca posible de la ubicación del usuario o de la sucursal.
  - Asegúrese de que las direcciones IP que devuelve la resolución de nombres DNS coincidan con la ruta de salida de enrutamiento para estos puntos de conexión.
  - Dé prioridad a estos puntos de conexión para la integración SD-WAN para el enrutamiento de latencia directa y mínima al punto más cercano de emparejamiento de Internet de la Red Global de Microsoft.

- Los puntos de conexión **Predeterminados** representan los servicios de Office 365 y las dependencias que no necesitan optimización, y las redes de clientes los pueden tratar como tráfico normal vinculado a Internet. Es posible que algunos puntos de conexión de esta categoría no estén alojados en centros de datos de Microsoft. Algunos ejemplos son  *https://odc.officeapps.live.com*  y  *https://appexsin.stb.s-msn.com*.

Para más información sobre las técnicas de optimización de red de Office 365, consulte el artículo [Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Comparación de la seguridad del perímetro de la red con la seguridad del punto de conexión
<a name="BKMK_SecurityComparison"> </a>

El objetivo de la seguridad de red tradicional es fortalecer el perímetro de la red corporativa frente a vulnerabilidades de seguridad malintencionadas e intrusiones. A medida que las organizaciones adoptan Microsoft 365, algunos servicios de red y datos se van migrando de manera total o parcial a la nube. En cuanto a los cambios fundamentales en la arquitectura de red, este proceso requiere una nueva evaluación de la seguridad de la red que tenga en cuenta factores emergentes:
  
- A medida que se adoptan servicios en la nube, los datos y servicios de red se distribuyen entre los centros de datos locales y la nube, y la seguridad perimetral por sí sola deja de bastar.
- Los usuarios remotos se conectan a recursos corporativos tanto en centros de datos locales como en la nube desde ubicaciones no controladas como hogares, hoteles y cafeterías.
- Las características de seguridad desarrolladas de propósito específico se integran cada vez más en los servicios en la nube y también pueden complementar o reemplazar los sistemas de seguridad existentes.

Microsoft ofrece una amplia gama de características de seguridad de Microsoft 365 y proporciona una guía prescriptiva para emplear las mejores prácticas de seguridad que pueden ayudarle a garantizar la seguridad de los datos y de la red para Microsoft 365. Las prácticas recomendadas incluyen las siguientes:
  
- **Usar la autenticación multifactor (MFA)** MFA agrega una capa adicional de protección a una estrategia de contraseña segura al obligar a los usuarios a confirmar una llamada telefónica, un mensaje de texto o una notificación de aplicación en el smartphone después de escribir la contraseña correcta.

- **Usar Microsoft Cloud App Security** Configure directivas para realizar un seguimiento de actividad anómala y actuar sobre la misma. Configurar alertas con Microsoft Cloud App Security para que los administradores puedan revisar las actividades de riesgo o poco habituales de los usuarios, como descargar grandes cantidades de datos, varios intentos fallidos de inicio de sesión o conexiones desde direcciones IP desconocidas o peligrosas.

- **Configurar la prevención de la pérdida de datos (DLP)** DLP le permite identificar datos confidenciales y crear directivas que contribuyen a evitar que los usuarios compartan los datos por error o de forma deliberada. DLP funciona en Microsoft 365, incluido en Exchange Online, SharePoint Online y OneDrive, de modo que los usuarios puedan cumplir las normativas sin interrumpir el flujo de trabajo.

- **Usar la Caja de seguridad del cliente** Como administrador de Microsoft 365, puede usar la Caja de seguridad del cliente para controlar el acceso de un ingeniero de soporte técnico de Microsoft a sus datos durante una sesión de ayuda. En casos donde el ingeniero requiere acceso a los datos para solucionar un problema, la Caja de seguridad del cliente le permite aprobar o rechazar la solicitud de acceso.

- **Usar la Puntuación segura de Office 365** Se trata de una herramienta de análisis de seguridad que proporciona recomendaciones para reducir aún más los riesgos. La Puntuación segura analiza las actividades y la configuración de Microsoft 365 y las compara con una línea de base establecida por Microsoft. Obtendrá una puntuación en función de su alineación con las mejores prácticas de seguridad.

Para lograr un enfoque holístico de seguridad mejorada, se debería tener en cuenta lo siguiente:
  
- Trasladar el énfasis de la seguridad perimetral a la seguridad de los puntos de conexión mediante la aplicación de características de seguridad de cliente de Office y basadas en la nube.
  - Restringir el perímetro de seguridad al centro de datos
  - Habilitar la confianza equivalente para dispositivos de usuario dentro la oficina o en ubicaciones remotas
  - Centrarse en proteger la ubicación de los datos y la ubicación del usuario
  - Los equipos de usuarios administrados tienen un nivel de confianza superior con la seguridad de los puntos de conexión
- Administrar toda la seguridad de la información de forma holística, en lugar de centrarse únicamente en el perímetro
  - Redefinir WAN y crear una seguridad de red perimetral permitiendo al tráfico de confianza omitir los dispositivos de seguridad y trasladando los dispositivos no administrados a las redes Wi-Fi de invitado
  - Reducir los requisitos de seguridad de red del perímetro WAN corporativo
  - Algunos dispositivos de seguridad de perímetro de red, como firewalls, siguen siendo necesarios, pero la carga disminuye
  - Garantiza la salida local para el tráfico de Microsoft 365
- Las mejoras se pueden realizar de manera progresiva, tal y como se describe en la sección [Optimización incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt). Algunas técnicas de optimización pueden ofrecer una mejor relación coste-beneficio según su arquitectura de red, de modo que debería elegir aquellas optimizaciones que sean más adecuadas para su organización.

Para más información sobre la seguridad y el cumplimiento de Microsoft 365, consulte el artículo [Seguridad de Microsoft 365](https://docs.microsoft.com/microsoft-365/security) y [Seguridad de Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance).
  
## <a name="incremental-optimization"></a>Optimización incremental
<a name="BKMK_IncOpt"> </a>

Anteriormente en este artículo, hemos representado el modelo ideal de conectividad de red para SaaS. Sin embargo, para muchas organizaciones grandes con arquitecturas de red tradicionalmente complejas, no resultará práctico realizar todos estos cambios directamente. En esta sección, se trata una serie de cambios incrementales que pueden ayudar a mejorar el rendimiento y la confiabilidad de Microsoft 365.
  
Los métodos que usted use para optimizar el tráfico de Microsoft 365 variarán en función de la topología de su red y de los dispositivos de red que haya implementado. Las grandes empresas con numerosas ubicaciones y prácticas complejas de seguridad de red tendrán que desarrollar una estrategia que incluya todos o la mayoría de los principios que aparecen en la sección [Principios de conectividad de Microsoft 365](office-365-network-connectivity-principles.md#BKMK_Principles), mientras que puede que las organizaciones pequeñas solo necesiten considerar uno o dos principios.
  
Puede abordar la optimización como un proceso gradual y aplicar cada método de manera sucesiva. En la tabla siguiente se muestra una lista de los métodos clave de optimización ordenados por impacto en la latencia y en la confiabilidad para el mayor número posible de usuarios.
  
|**Método de optimización**|**Descripción**|**Impacto**|
|:-----|:-----|:-----|
|Resolución de DNS y salida de Internet locales  <br/> |Aprovisionar los servidores DNS locales en cada ubicación y asegurarse de que la salida a Internet de las conexiones de Microsoft 365 esté lo más cerca posible de la ubicación del usuario.  <br/> | Minimizar la latencia  <br/>  Mejorar la confiabilidad de la conectividad con el punto de entrada de Microsoft 365 más cercano  <br/> |
|Agregar puntos de salida regionales  <br/> |Si la red corporativa tiene varias ubicaciones pero un solo punto de salida, agregue puntos de salida regionales para permitir a los usuarios conectarse al punto de entrada de Microsoft 365 más cercano.  <br/> | Minimizar la latencia  <br/>  Mejorar la confiabilidad de la conectividad con el punto de entrada de Microsoft 365 más cercano  <br/> |
|Omitir servidores proxy y dispositivos de inspección  <br/> |Configurar los exploradores con archivos PAC que envíen solicitudes de Microsoft 365 directamente a los puntos de salida.  <br/> Configurar los enrutadores perimetrales y firewalls para permitir el tráfico de Microsoft 365 sin inspección.  <br/> | Minimizar la latencia  <br/>  Reducir la carga en los dispositivos de red  <br/> |
|Habilitar la conexión directa para usuarios VPN  <br/> |En el caso de los usuarios VPN, habilite las conexiones de Microsoft 365 para que puedan conectarse directamente desde la red del usuario, en lugar de usar el túnel VPN mediante la implementación de tunelización dividida.  <br/> | Minimizar la latencia  <br/>  Mejorar la confiabilidad de la conectividad con el punto de entrada de Microsoft 365 más cercano  <br/> |
|Migrar de WAN tradicional a SD-WAN  <br/> |Las redes de área extensa definidas por software (SD-WAN) simplifican la administración de WAN y mejoran el rendimiento al reemplazar los enrutadores WAN tradicionales por aplicaciones virtuales, de forma similar a la virtualización de los recursos de proceso mediante máquinas virtuales (VM).  <br/> | Mejorar el rendimiento y la manejabilidad del tráfico WAN  <br/>  Reducir la carga en los dispositivos de red  <br/> |

## <a name="related-topics"></a>Temas relacionados

[Información general de conectividad de red de Microsoft 365](office-365-networking-overview.md)

[Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md)

[Direcciones URL e intervalos de direcciones IP de Office 365](urls-and-ip-address-ranges.md)

[Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md)

[Evaluar la conectividad de red de Microsoft 365](assessing-network-connectivity.md)

[Planeamiento de red y ajuste del rendimiento para Microsoft 365](network-planning-and-performance.md)

[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)

[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)

[Redes de entrega de contenido](content-delivery-networks.md)

[Prueba de conectividad de Microsoft 365](https://aka.ms/netonboard)

[Cómo construye Microsoft su red global rápida y confiable](https://azure.microsoft.com/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)

[Blog de redes de Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)
