---
title: Introducción a la conectividad de red de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/12/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Se explica por qué es importante la optimización de red para los servicios SaaS, el objetivo de la red de Office 365 y cómo SaaS requiere distintas redes de otras cargas de trabajo.
ms.openlocfilehash: 4acaee86136c88e5ac5b3c795f594fb056d15204
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491916"
---
# <a name="office-365-network-connectivity-overview"></a>Introducción a la conectividad de red de Office 365

Office 365 es una nube de software como servicio (SaaS) distribuida que proporciona escenarios de productividad y colaboración a través de un conjunto diverso de micro-servicios y aplicaciones. Los componentes de cliente de Office 365 como Outlook, Word y PowerPoint se ejecutan en los equipos de los usuarios y se conectan a otros componentes de Office 365 que se ejecutan en centros de usuarios de Microsoft. El factor más importante que determina la calidad de la experiencia del usuario final de Office 365 es la confiabilidad de red y la baja latencia entre los clientes de Office 365 y las puertas frontales del servicio de Office 365.

En este artículo, obtendrá información sobre los objetivos de la red de Office 365 y por qué la red de Office 365 requiere un enfoque diferente de optimización que el tráfico genérico de Internet.

## <a name="office-365-networking-goals"></a>Objetivos de red de Office 365

El objetivo último de la red de Office 365 es optimizar la experiencia del usuario final al habilitar el acceso menos restrictivo entre los clientes y los puntos de conexión de Office 365 más cercanos. La calidad de la experiencia del usuario final está directamente relacionada con el rendimiento y la capacidad de respuesta de la aplicación que está usando el usuario. Por ejemplo, Microsoft Teams depende de baja latencia para que las llamadas telefónicas de los usuarios, las conferencias y las colaboraciones de pantalla compartida se encuentren sin problemas y que Outlook se base en una buena conectividad de red para las características de búsqueda instantánea que aprovechan la indización del lado servidor y los AI sus.

El objetivo principal del diseño de red debe ser minimizar la latencia reduciendo el tiempo de ida y vuelta (RTT) de los equipos cliente a la red global de Microsoft, la red troncal de la red pública de Microsoft que conecta todos los centros de recursos de Microsoft con baja latencia , los puntos de entrada de la aplicación en la nube de alta disponibilidad se propagan por todo el mundo. Puede obtener más información sobre Microsoft Global Network en la [forma en que Microsoft crea su red global de confianza y rápida](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

La optimización del rendimiento de la red de Office 365 no necesita ser complicada. Puede obtener el mejor rendimiento posible si sigue unos cuantos principios clave:

- Identificación del tráfico de red de Office 365
- Permitir la salida de bifurcaciones locales de tráfico de red de Office 365 a Internet desde cada ubicación en la que los usuarios se conecten a Office 365
- Permitir el tráfico de Office 365 para omitir servidores proxy y dispositivos de inspección de paquetes

Para obtener más información sobre los principios de conectividad de red de Office 365, consulte [office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Arquitecturas de red tradicionales y SaaS

Los principios de arquitectura de red tradicional para las cargas de trabajo cliente-servidor se diseñan en torno al supuesto de que el tráfico entre los clientes y los extremos no se extienda fuera del perímetro de la red corporativa. Además, en muchas redes empresariales, todas las conexiones de Internet salientes atraviesan la red corporativa y se salida de una ubicación central.

En las arquitecturas de red tradicionales, la mayor latencia para el tráfico de Internet genérico es un equilibrio necesario para mantener la seguridad del perímetro de la red, y la optimización del rendimiento para el tráfico de Internet suele implicar la actualización o el escalado horizontal del equipo en los puntos de salida de red. Sin embargo, este enfoque no se redirecciona a los requisitos para un rendimiento óptimo de la red de los servicios SaaS como Office 365.

## <a name="identifying-office-365-network-traffic"></a>Identificación del tráfico de red de Office 365

Estamos haciendo que sea más fácil identificar el tráfico de red de Office 365 y simplificar la administración de la identificación de red.

- Nuevas categorías de puntos de conexión de red para diferenciar el tráfico de red de alta importancia del tráfico de red que no se ve afectado por las latencias de Internet. Hay solo un puñado de direcciones URL y admite direcciones IP en la categoría "optimizar" más importante.
- Servicios web para el uso de scripts o la configuración directa de dispositivos y la administración de cambios de la identificación de red de Office 365. Los cambios están disponibles en el servicio Web, en el formato RSS o en el correo electrónico mediante una plantilla de Microsoft Flow.
- [Programa para socios de red de office 365](http://aka.ms/Office365NPP) con asociados de Microsoft que proporcionan dispositivos o servicios que siguen los principios de conectividad de red de Office 365 y tienen una configuración sencilla.

## <a name="securing-office-365-connections"></a>Proteger las conexiones de Office 365

El objetivo de la seguridad de red tradicional es proteger el perímetro de la red corporativa contra intrusiones y ataques malintencionados. La mayoría de las redes empresariales exigen la seguridad de red para el tráfico de Internet mediante tecnologías como servidores proxy, firewalls, interrupción e inspección de SSL, inspección profunda de paquetes y sistemas de prevención de pérdida de datos. Estas tecnologías proporcionan una importante mitigación de riesgos para las solicitudes de Internet genéricas, pero pueden reducir drásticamente el rendimiento, la escalabilidad y la calidad de la experiencia del usuario final cuando se aplican a los puntos de conexión 365 de Office.

Office 365 ayuda a satisfacer las necesidades de su organización para la seguridad del contenido y el uso de datos con características de gobierno y seguridad integradas diseñadas específicamente para las cargas de trabajo y características de Office 365. Para obtener más información acerca de la seguridad y el cumplimiento de Office 365, consulte la [Guía de seguridad de office 365](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap). Para obtener más información acerca de las recomendaciones de Microsoft y la posición de soporte en soluciones avanzadas de red que realizan un procesamiento de nivel avanzado en el tráfico de Office 365, consulte [uso de dispositivos de red de terceros o soluciones en el tráfico de office 365](https://support.microsoft.com/en-us/help/2690045).

## <a name="why-is-office-365-networking-different"></a>¿Por qué es diferente la red de Office 365?

Office 365 está diseñado para obtener un rendimiento óptimo mediante el uso de la seguridad de extremos y conexiones de red cifradas, lo que reduce la necesidad de aplicar la seguridad perimetral. Office 365 Datacenters se encuentran en todo el mundo y el servicio está diseñado para usar varios métodos para conectar clientes a los mejores puntos de conexión de servicio disponibles. Como los datos de usuario y el procesamiento se distribuyen entre muchos centros de datos de Microsoft, no hay un único extremo de red al que se puedan conectar los equipos cliente. De hecho, Microsoft Global Network optimiza dinámicamente los datos y servicios de su inquilino de Office 365 para adaptarlos a las ubicaciones geográficas de las que tienen acceso los usuarios finales.

Algunos problemas comunes de rendimiento se crean cuando el tráfico de Office 365 está sujeto a la inspección de paquetes y salida centralizada:

- La alta latencia puede provocar un rendimiento extremadamente deficiente de las secuencias de audio y vídeo, y la respuesta lenta de la recuperación de datos, las búsquedas, la colaboración en tiempo real, la información de disponibilidad de calendario, el contenido del producto y otros servicios.
- La salida de conexiones desde una ubicación central derrota las capacidades de enrutamiento dinámico de la red global de Office 365, lo que agrega latencia y tiempo de ida y vuelta
- El descifrado de un tráfico de red de Office 365 protegido con SSL y su nuevo cifrado puede provocar errores de protocolo y tener riesgo de seguridad

La reducción de la ruta de acceso de red a los puntos de entrada de Office 365 al permitir que el tráfico de clientes salga lo más cerca posible de su ubicación geográfica puede mejorar el rendimiento de conectividad y la experiencia del usuario final en Office 365. También puede ayudar a reducir el impacto de los cambios futuros a la arquitectura de red en el rendimiento y la confiabilidad de Office 365. El modelo de conectividad óptimo es proporcionar siempre salida de red en la ubicación del usuario, independientemente de si se encuentra en la red corporativa o en las ubicaciones remotas, como los hogares, los hoteles, las cafeterías y los aeropuertos. El tráfico de Internet genérico y el tráfico de red corporativa basado en WAN se enrutarán por separado y no usarán el modelo de salida directo local. Este modelo de salida directo local se representa en el siguiente diagrama.

![Arquitectura de red de salida local](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

La arquitectura de salida local tiene las siguientes ventajas para el tráfico de red de Office 365 en el modelo tradicional:
  
- Proporciona el rendimiento óptimo de Office 365 mediante la optimización de la longitud de la ruta. Las conexiones de usuario final se enrutan dinámicamente al punto de entrada de Office 365 más cercano por parte de la infraestructura de _puerta de servicio distribuida_ de la red global de Microsoft y el tráfico se enruta internamente a los puntos de conexión de datos y servicios a través de la interfaz de usuario de Microsoft fibra oscura de alta disponibilidad de latencia ultra baja.
- Reduce la carga de la infraestructura de red corporativa al permitir la salida local para el tráfico de Office 365, al omitir los proxies y los dispositivos de inspección de tráfico.
- Protege las conexiones en ambos extremos aprovechando la seguridad de los extremos de cliente y las características de seguridad en la nube, evitando la aplicación de tecnologías de seguridad de red redundantes.

> [!NOTE]
> La infraestructura de _puerta frontal de servicio distribuido_ es el perímetro de red de alta disponibilidad y escalabilidad de Microsoft Global Network con ubicaciones geográficamente distribuidas. Termina las conexiones de usuario final y las enruta de manera eficaz dentro de la red global de Microsoft. Puede obtener más información sobre Microsoft Global Network en la [forma en que Microsoft crea su red global de confianza y rápida](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Para obtener más información sobre cómo comprender y aplicar los principios de conectividad de red de Office 365, consulte [office 365 Network Connectivity Principles](office-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Conclusión

La optimización del rendimiento de la red de Office 365 realmente se reduce a la eliminación de obstáculos innecesarios. Al tratar las conexiones de Office 365 como tráfico de confianza, puede evitar que la latencia se agregue mediante la inspección de paquetes y la competencia para el ancho de banda de proxy. Permitir conexiones locales entre los equipos cliente y los puntos de conexión de Office 365 permite enrutar dinámicamente el tráfico a través de la red global de Microsoft.

## <a name="related-topics"></a>Temas relacionados

[Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)

[Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md)

[Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md)

[Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md)

[Conectividad de red a Office 365](network-connectivity.md)

[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)

[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)

[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)

[Cómo Microsoft crea su red global rápida y fiable](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
