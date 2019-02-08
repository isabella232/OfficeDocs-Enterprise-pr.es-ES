---
title: Información general de conectividad de red de Office 365
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
description: Explica por qué es importante para los servicios de SaaS, el objetivo de las redes de Office 365, optimización de la red y cómo SaaS requiere diferentes redes de otras cargas de trabajo.
ms.openlocfilehash: 4acaee86136c88e5ac5b3c795f594fb056d15204
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897213"
---
# <a name="office-365-network-connectivity-overview"></a>Información general de conectividad de red de Office 365

Office 365 es una nube de Software-as-a-Service (SaaS) distribuida que proporciona escenarios de productividad y colaboración a través de un conjunto diverso de micro servicios y aplicaciones. Componentes de cliente de Office 365, como Outlook, Word y PowerPoint se ejecuten en los equipos de los usuarios y conectan a otros componentes de Office 365 que se ejecutan en centros de datos de Microsoft. El factor más importante que determina la calidad de la experiencia del usuario final de Office 365 es la confiabilidad de la red y una latencia baja entre los clientes de Office 365 y las puertas de frente de servicio de Office 365.

En este artículo, obtendrá información sobre los objetivos de la red de Office 365 y por qué Office 365 redes requiere un enfoque diferente a la optimización de tráfico de Internet genérico.

## <a name="office-365-networking-goals"></a>Objetivos de las redes de Office 365

El objetivo de las redes de Office 365 es optimizar la experiencia del usuario final al habilitar el acceso menos restrictivo entre los clientes y los extremos de Office 365 más cercanos. La calidad de la experiencia del usuario final está directamente relacionada con el rendimiento y la capacidad de respuesta de la aplicación que está utilizando el usuario. Por ejemplo, Microsoft Teams se basa en baja latencia para que las llamadas de teléfono del usuario, las conferencias y colaboraciones pantalla compartidos son sin problemas y Outlook se basa en la conectividad de redes excelente para las características de búsqueda instantánea que aprovechan la indización del lado del servidor y AI capacidades de.

El objetivo principal en el diseño de red debe ser a fin de Minimizar latencia mediante la reducción del tiempo de ida y vuelta (RTT) desde los equipos cliente a la red Global de Microsoft, red troncal de red pública de Microsoft que interconecta todos los centros de datos de Microsoft con una latencia baja , puntos de entrada de aplicación de alta disponibilidad en la nube dispersos por todo el mundo. Encontrará más información acerca de la red Global de Microsoft en [cómo Microsoft crea su red global rápida y confiable](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Optimizar el rendimiento de red de Office 365 no necesita ser complicada. Puede obtener el mejor rendimiento posible siguiendo unos principios claves:

- Identificar el tráfico de red de Office 365
- Permitir la salida de la sucursal local del tráfico de red de Office 365 a internet desde cada ubicación donde los usuarios se conectan a Office 365
- Permitir el tráfico de Office 365 se omiten los servidores proxy y los dispositivos de inspección de paquetes

Para obtener más información sobre los principios de conectividad de red de Office 365, vea [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md).

## <a name="traditional-network-architectures-and-saas"></a>Arquitecturas de red tradicional y SaaS

Principios de arquitectura de red tradicional de las cargas de trabajo de cliente/servidor están diseñados alrededor de la suposición de que el tráfico entre los clientes y los extremos no se extiende fuera del perímetro de la red corporativa. Además, en muchas de las redes empresariales, todas las conexiones salientes de Internet atraviesan la red corporativa y egreso desde una ubicación central.

En las arquitecturas de red tradicional, latencia superior para el tráfico de Internet genérico es un mal necesario para mantener la seguridad de red perimetral y optimización del rendimiento para el tráfico de Internet normalmente implica actualizar o escalar la equipos en los puntos de salida de red. Sin embargo, este enfoque no tiene en cuenta los requisitos para obtener un rendimiento óptimo de red de servicios de SaaS, como Office 365.

## <a name="identifying-office-365-network-traffic"></a>Que identifica el tráfico de red de Office 365

Estamos haciendo que sea más fácil identificar el tráfico de red de Office 365 y hacerla más sencilla administrar la identificación de la red.

- Nuevas categorías de extremos de la red para diferenciar el tráfico de red de importancia crítica de tráfico de red que no se ve afectado por las latencias de Internet. Hay sólo algunos de las direcciones URL y auxiliares direcciones IP en la categoría "Optimizar" más importante.
- Servicios Web para el uso de la secuencia de comandos o administración de cambios y configuración de dispositivos directa de identificación de red de Office 365. Los cambios están disponibles desde el servicio web, o en formato RSS o en correo electrónico mediante una plantilla de Microsoft Flow.
- [Programa para socios de red de office 365](http://aka.ms/Office365NPP) con los socios de Microsoft que proporcionan dispositivos o servicios que siguen los principios de conectividad de red de Office 365 y tienen configuración sencilla.

## <a name="securing-office-365-connections"></a>Proteger las conexiones de Office 365

El objetivo de la seguridad de red tradicional es reforzar el perímetro de la red corporativa frente a intrusiones y ataques malintencionados. La mayoría de las redes empresariales reforzar la seguridad de red para el tráfico de Internet mediante tecnologías como los servidores proxy, servidores de seguridad, salto de SSL e inspeccionan, inspección profunda del paquete y sistemas de prevención de pérdida de datos. Estas tecnologías proporcionan mitigación de riesgos importantes para las solicitudes de Internet genéricas, pero pueden reducir considerablemente el rendimiento, la escalabilidad y la calidad de la experiencia del usuario final cuando se aplica a los extremos de Office 365.

Office 365 ayuda a satisfacer las necesidades de su organización para el cumplimiento de uso de la seguridad y los datos de contenido con las características integradas de seguridad y gobierno diseñados específicamente para cargas de trabajo y las características de Office 365. Para obtener más información acerca de cumplimiento y seguridad de Office 365, vea la [Guía de seguridad de Office 365](https://docs.microsoft.com/en-us/office365/securitycompliance/security-roadmap). Para obtener más información acerca de las recomendaciones y la posición de soporte técnico de Microsoft en soluciones de red avanzadas que realizar el procesamiento de nivel avanzado en el tráfico de Office 365, vea [uso de dispositivos de red de terceros o soluciones en el tráfico de Office 365](https://support.microsoft.com/en-us/help/2690045).

## <a name="why-is-office-365-networking-different"></a>¿Por qué es Office 365 redes diferentes?

Office 365 está diseñado para un rendimiento óptimo con la seguridad de extremo y conexiones de red cifradas, reducir la necesidad de cumplimiento de seguridad de perímetro. Centros de datos de Office 365 se encuentran en todo el mundo y el servicio está diseñado para utilizar varios métodos para conectar los clientes a procedimientos extremos de servicio disponibles. Dado que el procesamiento y datos de usuario se distribuye entre muchos centros de datos de Microsoft, no hay ningún extremo de red único al cliente que se pueden conectar máquinas. De hecho, datos y servicios en el inquilino de Office 365 dinámicamente están optimizados por la red Global de Microsoft para adaptarse a las ubicaciones geográficas desde la que se tiene acceso a los usuarios finales.

Algunos problemas comunes de rendimiento se crean cuando el tráfico de Office 365 está sujeto a inspección de paquetes y centralizado salida:

- Latencia alta puede provocar que extremadamente bajo rendimiento de secuencias de audio y vídeo y la respuesta lenta de recuperación de datos, las búsquedas, colaboración en tiempo real, información de disponibilidad de calendario, contenido en productos y otros servicios
- Egressing conexiones desde una derrota ubicación central las capacidades de enrutamiento dinámicas de la red global de Office 365, adición de latencia y el tiempo de ida y vuelta
- Descifrado de SSL protegido el tráfico de red de Office 365 y volver a cifrar puede provocar errores de protocolo y tiene riesgos de seguridad

Acortar la ruta de acceso de red a puntos de entrada de Office 365 permitiendo el tráfico de cliente a egreso lo más cerca posible a su ubicación geográfica puede mejorar la conectividad de rendimiento y el usuario final de experiencia en Office 365. También puede ayudar a reducir el impacto de los cambios en el futuro a la arquitectura de red en el rendimiento de Office 365 y la confiabilidad. El modelo de conectividad óptima es proporcionar siempre salida de red en la ubicación del usuario, independientemente de si se trata de la red corporativa o ubicaciones remotas como principal, hoteles, cafeterías y aeropuertos. Genérico el tráfico de Internet y de WAN en función del tráfico de red corporativa se enrutan por separado y no usan el modelo de salida directa local. Este modelo de salida directa local está representado en el diagrama siguiente.

![Arquitectura de la red local de salida](media/6bc636b0-1234-4ceb-a45a-aadd1044b39c.png)

La arquitectura de salida local tiene las siguientes ventajas para el tráfico de red de Office 365 a través del modelo tradicional:
  
- Proporciona un rendimiento óptimo Office 365 mediante la optimización de longitud de ruta. Conexiones de usuario final se enrutan dinámicamente en el punto de entrada de Office 365 más cercano mediante la infraestructura de _distribuida puerta de entrada de servicio_ de la red Global de Microsoft, y se enruta el tráfico a continuación, internamente a los extremos de los datos y servicios a través de Microsoft fibra oscura de Ultra baja latencia alta disponibilidad.
- Reduce la carga en la infraestructura de red corporativa permitiendo la salida local para el tráfico de Office 365, pasando por alto los servidores proxy y los dispositivos de inspección de tráfico.
- Protege las conexiones en ambos extremos aprovechando extremo seguridad y en la nube seguridad características de cliente, evitar la aplicación de las tecnologías de seguridad de red redundantes.

> [!NOTE]
> La infraestructura de _puerta de entrada de servicio distribuido_ es perimetral de red de alta disponibilidad y escalabilidad de la red Global de Microsoft con ubicaciones distribuidas geográficamente. Finaliza las conexiones de usuario final y eficazmente los enruta dentro de la red Global de Microsoft. Encontrará más información acerca de la red Global de Microsoft en [cómo Microsoft crea su red global rápida y confiable](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/).

Para obtener más información en Descripción y aplicar los principios de conectividad de red de Office 365, vea [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md).

## <a name="conclusion"></a>Conclusión

Optimizar el rendimiento de red de Office 365 realidad, hay que quitar impedimentos innecesarios. Al tratar las conexiones de Office 365 como el tráfico de confianza, puede impedir que latencia van a introducirse por la inspección de paquetes y de la competencia de ancho de banda de proxy. Permitir que las conexiones locales entre equipos cliente y los extremos de Office 365 permite el tráfico dinámicamente enrutarse a través de la red Global de Microsoft.

## <a name="related-topics"></a>Temas relacionados

[Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)

[Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md)

[Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md)

[Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md)

[Conectividad de red a Office 365](network-connectivity.md)

[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)

[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)

[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)

[Cómo Microsoft crea su red global rápida y confiable](https://azure.microsoft.com/en-us/blog/how-microsoft-builds-its-fast-and-reliable-global-network/)
