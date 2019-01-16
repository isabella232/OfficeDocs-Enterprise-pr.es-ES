---
title: Principios de conectividad de red de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/14/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid: MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.assetid: 76e7f232-917a-4b13-8fe2-4f8dbccfe041
description: Antes de empezar a planear la red para la conectividad de red de Office 365, es importante comprender los principios de conectividad para administrar de forma segura el tráfico de Office 365 y obtener el mejor rendimiento posible. En este artículo le ayudará a comprender las instrucciones más reciente para optimizar de forma segura conectividad de red de Office 365.
ms.openlocfilehash: d319d99cdd413fe1df9e8f88d18742ad464bbb3b
ms.sourcegitcommit: f0ba0d8c62f802447bc9d07f5d877067156fbed5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/15/2019
ms.locfileid: "28021811"
---
# <a name="office-365-network-connectivity-principles"></a>Principios de conectividad de red de Office 365

Antes de empezar a planear la red para la conectividad de red de Office 365, es importante comprender los principios de conectividad para administrar de forma segura el tráfico de Office 365 y obtener el mejor rendimiento posible. En este artículo le ayudará a comprender las instrucciones más reciente para optimizar de forma segura conectividad de red de Office 365.
  
Las redes empresariales tradicionales están diseñadas principalmente para proporcionar a los usuarios acceso a aplicaciones y datos hospedados en centros de datos de compañía que se emplean con la seguridad del perímetro seguro. El modelo tradicional se supone que los usuarios tendrán acceso a las aplicaciones y los datos desde dentro del perímetro de la red corporativa, a través de vínculos WAN de sucursales o de forma remota a través de conexiones VPN. 
  
La adopción de aplicaciones de SaaS como Office 365 mueve una combinación de servicios y datos fuera de la red perimetral. Sin la optimización, el tráfico entre los usuarios y aplicaciones SaaS está sujeto a latencia introducida por la inspección de paquetes, hairpins de red, conexiones accidentales a extremos alejadas geográficamente y otros factores. Puede garantizar el mejor rendimiento de Office 365 y la confiabilidad mediante descripción e implementación de las instrucciones de optimización de la clave.
  
En este artículo, obtendrá información sobre:
  
- [Arquitectura de office 365](office-365-network-connectivity-principles.md#BKMK_Architecture) , tal como se aplica a la conectividad de cliente a la nube
- Actualizado [principios de conectividad de Office 365](office-365-network-connectivity-principles.md#BKMK_Principles) y estrategias para optimizar el tráfico de red y la experiencia del usuario final
- El [servicio web de Office 365 extremos](office-365-network-connectivity-principles.md#BKMK_WebSvc), lo que permite a los administradores de red consumir una lista estructurada de extremos para su uso en la optimización de la red
- Instrucciones de [categorías de extremo de nuevo Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) y optimización
- [Comparación de la seguridad de perímetro de red con la seguridad de extremo](office-365-network-connectivity-principles.md#BKMK_SecurityComparison)
- Opciones de [optimización incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt) para el tráfico de Office 365

## <a name="office-365-architecture"></a>Arquitectura de Office 365
<a name="BKMK_Architecture"> </a>

Office 365 es una nube de Software-as-a-Service (SaaS) distribuida que proporciona escenarios de productividad y colaboración a través de un conjunto diverso de micro-servicios y aplicaciones, como Exchange Online, SharePoint Online, Skype para Online de negocio de Microsoft Los equipos, Exchange Online Protection, Office Online y muchos otros. Mientras que determinadas aplicaciones de Office 365 pueden tener sus características exclusivas tal como se aplica a la red del cliente y la conectividad a la nube, todos ellos comparten algunas entidades de seguridad claves, los objetivos y patrones de arquitectura. Estas entidades de seguridad y los patrones de arquitectura para la conectividad de son típicos para muchos otros nubes SaaS y al mismo tiempo que se va a un proceso bastante diferentes de los modelos de implementación típica de plataforma como servicio y nubes de infraestructura como servicio, como Microsoft Azure.
  
Una de las características más importantes de arquitectura de Office 365 (que es a menudo perdidas o interpretado por diseñadores de red) es que es un servicio distribuido realmente global, en el contexto de cómo los usuarios se conectan a él. La ubicación del inquilino de destino Office 365 es importante comprender la localidad de donde se almacenan los datos de los clientes dentro de la nube, pero la experiencia del usuario con Office 365 no implica que se conectan directamente a los discos que contiene los datos. La experiencia del usuario con Office 365 (incluido el rendimiento, confiabilidad y otras características de calidad importante) implica la conectividad a través de un servicio altamente distribuido las puertas de frontal que se incrementó la escalabilidad horizontal a través de cientos de ubicaciones de Microsoft de todo el mundo. En la mayoría de los casos, la mejor experiencia de usuario se logra por lo que permite la red del cliente para enrutar las solicitudes de usuario para el punto de entrada de servicio de Office 365 más cercano, en lugar de conectarse a Office 365 a través de un punto de salida en una ubicación central o la región.
  
Para la mayoría de los clientes, los usuarios de Office 365 están distribuidos en muchas ubicaciones. Para lograr los mejores resultados, los principios descritos en este documento deben ser explicaba desde el escalado horizontal (no incremento) punto de vista, centrándose en optimizar la conectividad en el punto más cercano de presencia en la red Global de Microsoft, no a la información geográfica ubicación del inquilino de Office 365. En esencia, esto significa que, aunque los datos del inquilino de Office 365 pueden almacenarse en una ubicación geográfica específica, experiencia de Office 365 para ese inquilino permanece distribuida y puede estar presente en muy cerrar proximidad (red) para cada ubicación de usuario final que tiene el inquilino .
  
## <a name="office-365-connectivity-principles"></a>Principios de conectividad de Office 365
<a name="BKMK_Principles"> </a>

Microsoft recomienda los siguientes principios para lograr un rendimiento y conectividad óptima de Office 365. Use estos principios de conectividad de Office 365 para administrar el tráfico y obtener el mejor rendimiento al conectarse a Office 365.
  
El objetivo principal en el diseño de red debe ser a fin de Minimizar latencia mediante la reducción del tiempo de ida y vuelta (RTT) desde la red en la red Global de Microsoft, red troncal de red pública de Microsoft que interconecta todos los centros de datos de Microsoft con una latencia baja y en la nube de puntos de entrada de aplicación dispersos por todo el mundo. Encontrará más información acerca de la red Global de Microsoft en [cómo Microsoft crea su red global rápida y confiable](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).
  
<a name="BKMK_P1"> </a>
### <a name="identify-and-differentiate-office-365-traffic"></a>Identificar y diferenciar el tráfico de Office 365

![Identificar el tráfico de Office 365](media/621aaec9-971d-4f19-907a-1ae2ef6d72fc.png)
  
Que identifica el tráfico de red de Office 365 es el primer paso para poder diferenciar los que el tráfico de genérico del tráfico de red enlazado a Internet. Conectividad de Office 365 se puede optimizar mediante la implementación de una combinación de enfoques como optimización de la ruta de red, las reglas de firewall, configuración de proxy del explorador y el desvío de inspección de dispositivos de red para determinados extremos.
  
Guía de optimización de Office 365 anterior divide los extremos de Office 365 en dos categorías, **requerido** y **opcional**. Tal y como se han agregado para admitir los nuevos servicios de Office 365 y las características de los extremos, nos hemos reorganizado extremos de Office 365 en tres categorías: **optimizar**, **Permitir** y **establecer como predeterminado**. Instrucciones para cada categoría se aplica a todos los extremos en la categoría, realizar optimizaciones más fácil de comprender e implementar. 
  
Para obtener más detalles sobre las categorías de extremo de Office 365 y métodos de optimización, vea la sección [categorías de extremo de nuevo Office 365](office-365-network-connectivity-principles.md#BKMK_Categories) .
  
Ahora, Microsoft publica todos los extremos de Office 365 como un servicio web y proporciona orientación sobre cómo utilizar estos datos mejor. Para obtener más información acerca de cómo recuperar y trabajar con los extremos de Office 365, vea el artículo de [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
<a name="BKMK_P2"> </a>
### <a name="egress-network-connections-locally"></a>Conexiones de red de salida de forma local

![Conexiones de red de salida de forma local](media/b42a45be-1ab4-4073-a7dc-fbdfb4aedd24.png)
  
Salida DNS local e Internet es de importancia crítica para reducir la latencia de las conexiones y asegurarse de que las conexiones de usuario se realizan en el punto más cercano de entrada a los servicios de Office 365. En una topología de red compleja, es importante implementar DNS local y salida de Internet local juntos. Para obtener más información acerca de cómo Office 365 enruta las conexiones de cliente hasta el punto más cercano de entrada, vea el artículo de [Conectividad de cliente](https://support.office.com/en-us/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b).
  
Antes de la llegada de los servicios de nube, como Office 365, el usuario final la conectividad a Internet como un factor de diseño de arquitectura de red era relativamente simple. Cuando se distribuyen de servicios de Internet y sitios web de todo el mundo, latencia entre puntos de salida corporativo y cualquier extremo de destino determinado es en gran medida una función de la distancia geográfica.
  
En una arquitectura de red tradicional, todas las conexiones salientes de Internet atraviesan la red corporativa y egreso desde una ubicación central. Han madurado ofertas de nube de Microsoft, una arquitectura distribuida de red a través de Internet se ha convertido en crítica para la compatibilidad con servicios de nube sensibles a la latencia. La red Global de Microsoft se diseñó para dar cabida a los requisitos de latencia con la infraestructura distribuida puerta de servicio delantera, un fabric dinámico de puntos de entrada global que redirige las conexiones de servicio de nube entrantes para el punto de entrada más cercano. Esto está pensado para reducir la longitud de la "último paso" para los clientes de Microsoft en la nube acortar la ruta entre el cliente y la nube de forma eficaz.
  
WAN de empresa a menudo están diseñadas para el tráfico de red de backhaul a una oficina central de la empresa central para la inspección antes de salida a Internet, normalmente a través de uno o varios servidores proxy de. El diagrama siguiente muestra una topología de red de este tipo.
  
![Modelo de red de empresa tradicional](media/fc87b8fd-a191-47a7-9704-1e445599813a.png)
  
Dado que Office 365 se ejecuta en la red Global de Microsoft, que incluye los servidores front-end todo el mundo, suele haber un servidor front-end cerca de la ubicación del usuario. Proporcionando local salida de Internet y mediante la configuración de los servidores DNS internos para proporcionar la resolución de nombres local para los extremos de Office 365, el tráfico de red destinado a Office 365 puede conectarse a los servidores front-end de Office 365 más cerca posible al usuario. El diagrama siguiente muestra un ejemplo de una topología de red que permite a los usuarios que se conectan desde la oficina central, sucursales y ubicaciones remotas que se deben seguir la ruta más corta para el punto de entrada de Office 365 más cercano.
  
![Modelo de red WAN con puntos de salida regional](media/4d4c07cc-a928-42b8-9a54-6c3741380a33.png)
  
Acortar la ruta de acceso de red a Office 365 puntos de entrada de esta forma pueden mejorar el rendimiento de conectividad y el usuario final experiencia de Office 365 y puede también ayuda a reducir el impacto de los cambios posteriores a la arquitectura de red en el rendimiento de Office 365 y confiabilidad.
  
Además, las solicitudes DNS pueden introducir latencia si el servidor DNS de respuesta está lejano u ocupado. Puede reducir al mínimo la latencia de resolución de nombre aprovisionamiento servidores DNS locales en ubicaciones de sucursales y asegurándose de que están configurados correctamente para los registros DNS de la memoria caché.
  
Aunque salida regional puede funcionar bien para Office 365, el modelo de conectividad óptima sería proporcionar siempre salida de red en la ubicación del usuario, independientemente de si se trata de la red corporativa o ubicaciones remotas, como principal, hoteles, cafeterías y aeropuertos. Este modelo de salida directa local está representado en el diagrama siguiente.
  
![Arquitectura de la red local de salida](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)
  
Las empresas que han adoptado Office 365 pueden aprovechar la arquitectura de la puerta de servicio delantera distribuida de la red Global de Microsoft al garantizar que las conexiones de usuario a Office 365 toman la ruta más corta posible a la entrada de la red Global de Microsoft más cercana punto. Para ello, la arquitectura de red de salida local permitir que el tráfico de Office 365 se enrutan a través de la salida más cercano, independientemente de la ubicación del usuario.
  
La arquitectura de salida local tiene las siguientes ventajas sobre el modelo tradicional:
  
- Proporciona un rendimiento óptimo Office 365 mediante la optimización de longitud de ruta. Conexiones de usuario final se enrutan dinámicamente en el punto de entrada de Office 365 más cercano por la infraestructura de la puerta de servicio delantera distribuida.
- Reduce la carga en la infraestructura de red corporativa permitiendo la salida local.
- Protege las conexiones en ambos extremos aprovechando la seguridad de extremo de cliente y las características de seguridad de la nube.

<a name="BKMK_P3"> </a>
### <a name="avoid-network-hairpins"></a>Evitar las redirecciones de red

![Evitar hairpins](media/ee53e8af-f57b-4292-a256-4f36733b263a.png)
  
Como regla general, la ruta más corta, más directa entre el usuario y el extremo más cercano de Office 365 ofrecerá el mejor rendimiento. Una horquilla de red que sucede cuando el tráfico de WAN o VPN enlazado para un destino concreto en primer lugar se dirige a otra ubicación intermedia (por ejemplo, la pila de seguridad, broker de acceso en la nube, de puerta de enlace de web en función de la nube), presentación de latencia y redirección posible a un extremo alejado geográficamente. Hairpins de red también pueden deberse a ineficacias enrutamiento de interconexión o inferiores a los óptimos consultas DNS (remotos).
  
Para asegurarse de que la conectividad de Office 365 no está sujeto a hairpins de red incluso en el caso de salida local, compruebe si el ISP que se usa para proporcionar la salida de Internet para la ubicación de usuario tiene una relación de interconexión directa con la red Global de Microsoft en Cerrar proximidad a esa ubicación. Es posible que también desea configurar para enviar el tráfico de confianza de Office 365 directamente el enrutamiento de salida, en lugar de conexiones proxy o túnel a través de una nube de otro fabricante o proveedor de seguridad de red basada en la nube procesa el tráfico enlazado a Internet. Resolución de nombres DNS local de los extremos de Office 365 ayuda a garantizar que el enrutamiento directo, además de los puntos de entrada de Office 365 más cercanos se utilizan para las conexiones de usuario.
  
Si usa red basada en la nube o servicios de seguridad para el tráfico de Office 365, asegúrese de que se evalúa el efecto de hairpinning y se entiende su impacto en el rendimiento de Office 365. Esto puede realizarse mediante el examen del número y las ubicaciones de las ubicaciones de proveedor de servicio a través del cual se reenvía el tráfico en relación con el número de sus sucursales y puntos de interconexión de red Global de Microsoft, la calidad de la relación de interconexión de red de el proveedor de servicios con su ISP y Microsoft y el impacto de rendimiento de backhauling en la infraestructura del proveedor de servicio.
  
Debido al gran número de ubicaciones distribuidas con puntos de entrada de Office 365 y su proximidad a los usuarios finales, enrutar el tráfico de Office 365 para cualquier proveedor de red o de seguridad de terceros puede tener un impacto negativo en las conexiones de Office 365 si no es de la red del proveedor configurado para interconexión óptima de Office 365.
  
<a name="BKMK_P4"> </a>
### <a name="bypass-proxies-traffic-inspection-devices-and-duplicate-security-technologies"></a>Evitar los servidores proxy, los dispositivos de inspección de tráfico y las tecnologías de seguridad duplicados

![Evitar los servidores proxy, los dispositivos de inspección de tráfico y las tecnologías de seguridad duplicados](media/0131930d-c6cb-4ae1-bbff-fe4cf6939a23.png)
  
Los clientes de empresa deben revisar la seguridad de su red y métodos para reducir el riesgo específicamente para Office 365 enlazado el tráfico y usar las características de seguridad de Office 365 para reducir su dependencia en intrusiva, el rendimiento afecta a y la seguridad de red costosa tecnologías para el tráfico de red de Office 365.
  
La mayoría de las redes empresariales exigir la aplicación de seguridad de red para el tráfico de Internet mediante tecnologías como los servidores proxy, inspección de SSL, la inspección de paquetes y sistemas de prevención de pérdida de datos. Estas tecnologías proporcionan mitigación de riesgos importantes para las solicitudes de Internet genéricas, pero pueden reducir considerablemente el rendimiento, escalabilidad y la calidad de la experiencia del usuario final cuando se aplica a los extremos de Office 365.
  
<a name="BKMK_WebSvc"> </a>
#### <a name="office-365-endpoints-web-service"></a>Servicio web de extremos de Office 365

Los administradores de Office 365 pueden usar una secuencia de comandos o llamada REST al consumir una lista estructurada de extremos de los extremos de Office 365 de servicio web y actualizar las configuraciones de servidores de seguridad perimetrales y otros dispositivos de red. Esto le permitirá garantizar que el tráfico enlazado para Office 365 es identificado, tratamiento apropiado y administran de forma diferente desde el tráfico de red enlazado para los sitios web de Internet genérico y a menudo desconocido. Para obtener más información sobre cómo usar los extremos de Office 365 servicio web, vea el artículo [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://support.office.com/en-us/article/office-365-urls-and-ip-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
#### <a name="pac-proxy-automatic-configuration-scripts"></a>Secuencias de comandos de PAC (configuración automática de Proxy)
<a name="BKMK_WebSvc"> </a>

Los administradores de Office 365 pueden crear scripts de PAC (configuración automática de Proxy) que se pueden entregar a equipos de los usuarios a través de WPAD o GPO. Secuencias de comandos de PAC pueden usarse para omitir a los servidores proxy para Office 365 las solicitudes de los usuarios WAN o VPN, lo que permite el tráfico de Office 365 usar conexiones directas a Internet, en lugar de recorrido de la red corporativa.
  
#### <a name="office-365-security-features"></a>Características de seguridad de Office 365
<a name="BKMK_WebSvc"> </a>

Microsoft es transparente acerca de la seguridad del centro de datos, seguridad operativa y reducción de los riesgos alrededor de los servidores de Office 365 y los extremos de red que representan. Características de Office 365 seguridad integrada están disponibles para reducir el riesgo de seguridad de red, como la prevención de pérdida de datos, el antivirus, autenticación multifactor, cuadro de bloqueo de cliente, avanzada de protección contra amenazas, información sobre amenazas de Office 365, seguro de Office 365 Puntuación, Exchange Online Protection y seguridad de red DDOS.
  
Para obtener más información sobre el centro de datos de Microsoft y la seguridad de red Global, consulte el [Centro de confianza de Microsoft](https://www.microsoft.com/en-us/trustcenter/security).
  
## <a name="new-office-365-endpoint-categories"></a>Nuevas categorías de extremo de Office 365
<a name="BKMK_Categories"> </a>

Los extremos de Office 365 representan un conjunto variado de direcciones de red y subredes. Las direcciones URL, es posible extremos de intervalos de direcciones IP o IP, y se enumeran algunos extremos con determinados puertos TCP/UDP. Las direcciones URL pueden ser un FQDN como *account.office.net* o una dirección URL de caracteres comodín, como * \*. office365.com*.
  
> [!NOTE]
> Las ubicaciones de los extremos de Office 365 dentro de la red no están directamente relacionados con la ubicación de los datos del inquilino de Office 365. Por este motivo, los clientes deben tener un aspecto en Office 365 como un servicio distribuido y global y no deben intentar bloquear las conexiones de red a los extremos de Office 365 según criterios geográficos.
  
En nuestra orientación anterior para administrar el tráfico de Office 365, extremos se organizan en dos categorías, **requerido** y **opcional**. Extremos dentro de cada categoría necesarios optimizaciones diferentes según la importancia del servicio y muchos clientes que enfrentan desafíos en justificar la aplicación de las mismas optimizaciones de red a la lista completa de direcciones IP y URL de Office 365. 
  
En el nuevo modelo, los extremos son separar en tres categorías, **optimizar**, **Permitir** y **predeterminado**, que proporciona una tabla dinámica basada en prioridad sobre dónde centrar los esfuerzos de optimización de red para obtener el mejor mejoras de rendimiento y devolver de la inversión. Los extremos se consolidan en las categorías anteriores en función de la confidencialidad de la experiencia de usuario eficaz para sobres de calidad, capacidad y rendimiento de red de escenarios y facilidad de implementación. Optimizaciones de recomendado, se pueden aplicar la misma forma a todos los extremos de una categoría determinada.
  
- **Optimizar** extremos son necesarios para la conectividad con cada servicio de Office 365 y representan más del 75% del ancho de banda, las conexiones y volumen de datos de Office 365. Estos extremos representan los escenarios de Office 365 que son más sensibles a rendimiento, latencia y la disponibilidad de la red. Todos los extremos se hospedan en centros de datos de Microsoft. La tasa de cambio de los extremos de esta categoría se espera que sea mucho más bajo que para los extremos en las dos categorías. Esta categoría incluye un conjunto muy pequeño (en el orden ~ 10) de la clave de las direcciones URL y un conjunto definido de subredes IP dedicadas a las cargas de trabajo de núcleo de Office 365, como Exchange Online, SharePoint Online, Skype para profesionales en línea y Microsoft Teams.

    Una lista de extremos críticos bien definidos condensada debería ayudarle a planear e implementar las optimizaciones de red de alto valor para estos destinos más rápidos y fácil.

    Ejemplos de extremos de *optimizar* *https://outlook.office365.com* , *https://\<inquilino\>. sharepoint.com* y *https://\<inquilino\>-my.sharepoint.com* .

    Métodos de optimización se incluyen:

  - El desvío de lista blanca *optimizar* los extremos o en dispositivos de red y servicios que llevar a cabo el tráfico interceptación, SSL descifrado, inspección profunda del paquete y filtrado de contenido.
  - El desvío de los dispositivos de proxy local y servicios basados en la nube proxy usados con frecuencia para la exploración de Internet genérico.
  - Establecer la prioridad de la evaluación de estos extremos como de plena confianza por los sistemas de infraestructura y el perímetro de red.
  - Establecer prioridades de reducción o eliminación de WAN backhauling y facilitar directa salida basado en Internet distribuido para estos extremos lo más cercano a las ubicaciones de los usuarios y sucursales como sea posible.
  - Facilitar la conectividad directa a estos extremos en la nube para los usuarios VPN mediante la implementación de túnel dividido.
  - Asegúrese de que las direcciones IP devueltas por la resolución de nombres DNS coinciden con la ruta de acceso de salida enrutamiento para estos extremos.
  - Establecer prioridades de estos extremos para la integración de WAN SD para el enrutamiento de latencia mínima, directa en el punto más cercano de interconexión de Internet de la red global de Microsoft.

- **Permitir** extremos son necesarios para la conectividad con las características y servicios específicos de Office 365, pero no son tan confidenciales a rendimiento de la red y la latencia como los de la categoría de *optimizar* . El espacio de red general de estos extremos desde el punto de vista de recuento de ancho de banda y conexión también es considerablemente menor. Estos extremos dedicados a Office 365 y se hospedan en centros de datos de Microsoft. Que representan un amplio conjunto de servicios de micro de Office 365 y sus dependencias (del orden de las direcciones URL de ~ 100) y se espera que cambie a una velocidad superior a los de la categoría de *optimizar* . No todos los extremos de esta categoría se asocian con definido subredes IP dedicadas.

    Optimizaciones de red para *Permitir* extremos pueden mejorar la experiencia de usuario de Office 365, pero es posible que algunos clientes prefieren de ámbito de esas optimizaciones más estrictamente para minimizar los cambios realizados en su red.

    Ejemplos de extremos de *Permitir* *https://\*. protection.outlook.com* y *https://accounts.accesscontrol.windows.net*.

    Métodos de optimización se incluyen:

  - El desvío de lista blanca *Permitir* los extremos o en dispositivos de red y servicios que llevar a cabo el tráfico interceptación, SSL descifrado, inspección profunda del paquete y filtrado de contenido.
  - Establecer la prioridad de la evaluación de estos extremos como de plena confianza por los sistemas de infraestructura y el perímetro de red.
  - Establecer prioridades de reducción o eliminación de WAN backhauling y facilitar directa salida basado en Internet distribuido para estos extremos lo más cercano a las ubicaciones de los usuarios y sucursales como sea posible.
  - Asegúrese de que las direcciones IP devueltas por la resolución de nombres DNS coinciden con la ruta de acceso de salida enrutamiento para estos extremos.
  - Establecer prioridades de estos extremos para la integración de WAN SD para el enrutamiento de latencia mínima, directa en el punto más cercano de interconexión de Internet de la red global de Microsoft.

- **Valor predeterminado** extremos representan servicios de Office 365 y dependencias que no requieren ninguna optimización y redes de los clientes pueden tratar como Internet normal había enlazado el tráfico. Tenga en cuenta que algunos extremos de esta categoría no pueden hospedarse en centros de datos de Microsoft. Algunos ejemplos son *https://odc.officeapps.live.com* y *https://appexsin.stb.s-msn.com*.

Para obtener más información acerca de las técnicas de optimización de red de Office 365, vea el artículo [extremos de administración de Office 365](https://support.office.com/en-us/article/managing-office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EAEAAA=0._Overview).
  
## <a name="comparing-network-perimeter-security-with-endpoint-security"></a>Comparación de la seguridad de perímetro de red con la seguridad de extremo
<a name="BKMK_SecurityComparison"> </a>

El objetivo de la seguridad de red tradicional es reforzar el perímetro de la red corporativa frente a intrusiones y ataques malintencionados. Cuando las organizaciones adoptan Office 365, algunos servicios de red y los datos se total o parcialmente migran a la nube. Al igual que cualquier cambio fundamental en la arquitectura de la red, este proceso requiere una reevaluación de seguridad de red que tiene en cuenta los factores emergentes:
  
- Tal y como se adoptan servicios de nube, datos y servicios de red se distribuyen entre centros de datos local y la nube y seguridad perimetral ya no es la adecuada en su propio.
- Los usuarios remotos conectarse a recursos corporativos en centros de datos locales y en la nube desde ubicaciones no controladas como hogares, hoteles y cafeterías.
- Características de seguridad creado especialmente para cada vez más están integradas en los servicios de nube y potencialmente pueden complementar o reemplazar sistemas de seguridad existentes.

Microsoft ofrece una amplia intervalo de Office 365 características de seguridad y proporciona instrucciones para emplear prácticas recomendadas de seguridad que pueden ayudar a garantizar la seguridad de datos y de red para Office 365. Procedimientos recomendados son los siguientes:
  
- **Autenticación multifactor de uso (MFA)** MFA agrega una capa adicional de protección a una estrategia de contraseña segura por requerir que los usuarios a una llamada de teléfono, mensaje de texto o una notificación de la aplicación en su teléfono inteligente después de escribir correctamente su contraseña.

- **Seguridad de la aplicación de uso Office 365 en la nube** Establecer directivas para realizar un seguimiento de la actividad anómala y actuar en él. Configurar las alertas de seguridad de la aplicación de Office 365 en la nube para que los administradores puedan consultar la actividad de usuario inusual o arriesgado, como una descarga grandes cantidades de datos, varios intentos erróneos de inicio de sesión o direcciones conexiones desde una dirección IP desconocida o peligrosa.

- **Configuración de prevención de pérdida de datos (DLP)** DLP permite identificar datos confidenciales y crear directivas que ayudan a impedir que los usuarios los datos de uso compartido de forma accidental o intencionada. DLP funciona a través de Office 365 incluido Exchange Online, SharePoint Online y OneDrive para que sus usuarios puedan permanecer compatible con sin interrumpir su flujo de trabajo.

- **Caja de seguridad de uso del cliente** Como un administrador de Office 365, puede usar la caja de seguridad de cliente para controlar cómo un ingeniero de soporte técnico de Microsoft tiene acceso a los datos durante una sesión de ayuda. En los casos donde el ingeniero requiere acceso a los datos para solucionar problemas y corregir un problema, caja de seguridad de cliente permite aprobar o rechazar la solicitud de acceso.

- **Usar puntuación segura de Office 365** Puntuación seguro es una herramienta de análisis de seguridad que se recomienda lo que puede hacer para reducir el riesgo. Puntuación de seguro se busca en la configuración de Office 365 y las actividades y los compara con una línea de base establecida por Microsoft. Obtendrá una puntuación de cómo alineadas que se basan en con procedimientos recomendados de seguridad.

Un enfoque integral para mejorar la seguridad debe incluir la consideración de las siguientes opciones:
  
- Desplazar el énfasis de la seguridad del perímetro hacia la seguridad de extremo mediante la aplicación basada en la nube y las características de seguridad de cliente de Office.
  - Reducir el perímetro de seguridad para el centro de datos
  - Habilitar la confianza equivalente para los dispositivos de usuario dentro de la oficina o en ubicaciones remotas
  - Centrarse en la protección de la ubicación de datos y la ubicación del usuario
  - Usuario administrado máquinas tengan confianza superior con seguridad de extremo
- Administrar toda la seguridad de información de forma global, no centrarse únicamente en el perímetro de la
  - Redefinición de WAN y creación de seguridad de la red perimetral por lo que permite el tráfico de confianza para el desvío de dispositivos de seguridad y separación de los dispositivos no administrados para redes Wi-Fi de invitado.
  - Reduce los requisitos de seguridad de red del borde WAN corporativo
  - Algunos dispositivos de seguridad de perímetro de red, como firewalls aún son necesarios, pero de carga se reduce
  - Se asegura de salida local para el tráfico de Office 365
- Mejoras pueden tratarse incrementalmente tal como se describe en la sección [optimización Incremental](office-365-network-connectivity-principles.md#BKMK_IncOpt) . Algunas técnicas de optimización pueden ofrecer mejores relaciones de costos y beneficios dependiendo de la arquitectura de la red, y debe elegir las optimizaciones que hacen más adecuado para su organización.

Para obtener más información sobre el cumplimiento de normas y seguridad de Office 365, vea el artículo [información general de seguridad y cumplimiento de normas en Office 365](https://support.office.com/en-us/article/overview-of-security-and-compliance-in-office-365-dcb83b2c-ac66-4ced-925d-50eb9698a0b2?ui=en-US&amp;rs=en-US&amp;ad=US).
  
## <a name="incremental-optimization"></a>Optimización incremental
<a name="BKMK_IncOpt"> </a>

Nos hemos representado el modelo de conectividad a red ideal para SaaS anteriormente en este artículo, pero para muchas organizaciones grandes con arquitecturas de red históricamente compleja, no será práctico directamente realizar todos estos cambios. En esta sección, se describe un número de cambios incrementales que puede ayudar a mejorar la confiabilidad y rendimiento de Office 365.
  
Los métodos que se va a utilizar para optimizar el tráfico de Office 365 variará en función de la topología de red y los dispositivos de red que ha implementado. Las grandes empresas con muchas ubicaciones y procedimientos de seguridad de red complejas necesitará para desarrollar una estrategia que incluye la mayor parte o la totalidad de los principios enumerados en la sección [principios de conectividad de Office 365](office-365-network-connectivity-principles.md#BKMK_Principles) , mientras que las organizaciones más pequeñas, es posible que sólo deben tener en cuenta uno o dos.
  
Puede enfocar la optimización como un proceso incremental, aplicar sucesivamente cada método. En la siguiente tabla se enumera los métodos de optimización de la clave en el orden de su impacto en la latencia y la confiabilidad para el mayor número de usuarios.
  
|**Método de optimización**|**Description**|**Impacto**|
|:-----|:-----|:-----|
|Resolución DNS local de entrada y salida de Internet  <br/> |Aprovisionar servidores DNS locales en cada ubicación y asegúrese de que salida de Office 365 conexiones a Internet más cerca posible a la ubicación del usuario.  <br/> | Minimizar latencia  <br/>  Mejorar la conectividad confiable al punto de entrada más cercano de Office 365  <br/> |
|Agregar puntos de salida regional  <br/> |Si la red corporativa tiene varias ubicaciones, pero el punto de salida sólo uno, agregar puntos de salida regional para habilitar a los usuarios conectarse al punto de entrada de Office 365 más cercano.  <br/> | Minimizar latencia  <br/>  Mejorar la conectividad confiable al punto de entrada más cercano de Office 365  <br/> |
|Evitar los servidores proxy y los dispositivos de inspección  <br/> |Configuración de los exploradores con archivos PAC que envían solicitudes de Office 365 directamente a los puntos de salida.  <br/> Configure los enrutadores de borde y firewalls para permitir el tráfico de Office 365 sin inspección.  <br/> | Minimizar latencia  <br/>  Reducir la carga en los dispositivos de red  <br/> |
|Habilitar conexión directa para los usuarios VPN  <br/> |Para los usuarios VPN, habilite las conexiones de Office 365 para conectarse directamente desde la red del usuario, en lugar de a través del túnel VPN mediante la implementación de túnel dividido.  <br/> | Minimizar latencia  <br/>  Mejorar la conectividad confiable al punto de entrada más cercano de Office 365  <br/> |
|Migración de WAN tradicional a SD WAN  <br/> |SD-redes de área extensa (Software definido redes de área extensa) simplifican la administración de WAN y mejoran el rendimiento mediante el reemplazo de enrutadores WAN tradicionales con dispositivos virtuales, similares a la virtualización de recursos de cálculo con máquinas virtuales (VM).  <br/> | Mejorar el rendimiento y la capacidad de administración de tráfico de WAN  <br/>  Reducir la carga en los dispositivos de red  <br/> |
