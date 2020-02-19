---
title: Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 02/04/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Información general sobre las recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)
ms.openlocfilehash: d944814effc62956d5047bad1f3088d0919793ee
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106443"
---
# <a name="network-performance-recommendations-in-the-microsoft-365-admin-center-preview"></a>Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)

La página rendimiento de red del centro de administración de Microsoft 365 muestra Network Insights y una puntuación de red para clientes empresariales. Network Insights son cambios específicos en el diseño de la arquitectura de red recomendadas para mejorar la experiencia del usuario con la conectividad de red a Office 365 y la puntuación de red muestra cómo la conectividad de red afecta a la experiencia del usuario, lo que permite comparar distintas conexiones de red de ubicación de usuario. Las empresas que usan Office 365 con varias ubicaciones de oficina y arquitecturas de perímetro de red no triviales pueden beneficiarse de esto durante la incorporación inicial a Office 365 o para corregir los problemas de rendimiento de la red detectados con el uso. expansión. Por lo general, esto no es necesario en el caso de pequeñas empresas que usen Office 365 o cualquier empresa que ya tenga conectividad de red sencilla y directa. Se espera que las empresas con más de 500 usuarios y varias ubicaciones de oficina disfruten de lo máximo.

>[!IMPORTANT]
>Las recomendaciones de rendimiento de red, información y evaluaciones en el centro de administración de Microsoft 365 se encuentra actualmente en estado de versión preliminar y solo está disponible para los inquilinos de Office 365 que se han inscrito en el programa de vista previa de características.

## <a name="enterprise-network-connectivity-challenges"></a>Desafíos de conectividad de red empresarial

![Red del cliente a la nube](Media/m365-mac-perf/m365-mac-perf-first-last-mile.png)

Muchas empresas tienen configuraciones de perímetro de red que han crecido con el tiempo y están diseñadas principalmente para acomodar el acceso al sitio web de Internet de los empleados, donde la mayoría de los sitios web no se conocen de antemano y no son de confianza. El enfoque predominante y necesario evita los ataques de malware y de pesca de estos sitios web desconocidos. Esta estrategia de configuración de red, a la vez que resulta útil por motivos de seguridad, puede llevar a una degradación del rendimiento del usuario y de la experiencia del usuario de Office 365. Las empresas pueden mejorar la experiencia del usuario, pero también seguir protegendo su entorno siguiendo los [principios de conectividad de Office 365](https://aka.ms/pnc) y pronto usando la nueva característica de rendimiento de la red del centro de administración de Microsoft 365. Esta característica ayuda con el diseño de la arquitectura de red que se alinea con los principios de conectividad de Office 365 y debe llevar a un rendimiento de red optimizado para la conectividad con Office 365.

## <a name="how-we-can-solve-these-challenges"></a>Cómo podemos resolver estos desafíos

A veces, Microsoft se le pide que investigue los problemas de rendimiento de la red con Office 365 para grandes clientes empresariales, y estos suelen tener una causa raíz relacionada con la infraestructura de salida de red de los clientes. Cuando se encuentra una causa de raíz común de un problema con el perímetro de la red del cliente, buscamos la identificación de medidas de prueba simples que la identifiquen. Una prueba con un umbral de medida que identifica un problema específico es valiosa porque podemos probar la misma medida en cualquier ubicación, saber si esta causa es la que está presente allí y compartirla como un conocimiento de red con el administrador. En algunos detalles de red, simplemente se indica un problema que necesita una investigación más. Un conocimiento de la red donde se tienen suficientes pruebas para mostrar una acción de corrección específica para corregir la causa raíz aparece como una acción recomendada. Estas indicaciones de red basadas en mediciones que superan un umbral predeterminado son mucho más valiosas que los consejos de prácticas recomendadas generales, ya que no es necesario preguntar si se aplican ciertas prácticas recomendadas y dará como resultado una importante mejora de la experiencia del usuario o no. .

## <a name="network-performance-overview-in-the-microsoft-365-admin-center"></a>Introducción al rendimiento de red en el centro de administración de Microsoft 365

Microsoft tiene medidas de red existentes entre las que se incluyen varios clientes Web y de escritorio de Office que admiten el funcionamiento de Office 365. Estas mediciones ahora se usan para proporcionar información de diseño de arquitectura de red y una puntuación de rendimiento de red que se muestran en la página rendimiento de red en el centro de administración de Microsoft 365.

La información de ubicación aproximada asociada con las medidas de red puede identificar la ciudad en la que se encuentran los dispositivos cliente. Se usa para mostrar los clientes las ubicaciones de la oficina y las medidas de red se agrupan para proporcionar información sobre la red para esa ubicación de la oficina. La puntuación de red en cada ubicación se muestra con color y el número relativo de usuarios en cada ubicación se representa mediante el tamaño del círculo. La página de información general también muestra la puntuación de red para el cliente como media ponderada en todas las ubicaciones de la oficina.

## <a name="specific-office-location-network-performance-summary-and-insights"></a>Información específica sobre el rendimiento y el resumen del rendimiento de red de una ubicación de Office

Al seleccionar una ubicación de la oficina se abre una página de Resumen específica de la ubicación. Se muestran los detalles de salida de red que se han identificado a partir de las medidas de esa ubicación de la oficina.

La página de Resumen de ubicación de oficinas muestra además la puntuación de red de las ubicaciones, el historial de puntuación de red, una comparación de esta clasificación de ubicaciones para otros clientes en la misma ciudad y una lista de información específica y recomendaciones que el cliente puede emprender para mejorar su conectividad de red. Las comparaciones entre clientes en la misma ciudad se basan en la expectativa de que todos los clientes tengan el mismo acceso a los proveedores de servicios de red, la infraestructura de telecomunicaciones y los puntos cercanos de presencia de la red de Microsoft.

La pestaña detalles de la página ubicación de la oficina muestra los resultados de medidas específicos que se usaron para provenir de información, recomendaciones y la puntuación de red. Esto se proporciona para que los ingenieros de red puedan validar las recomendaciones y el factor de las restricciones o los detalles de su entorno.
Para los clientes que quieran mejorar la precisión de las ubicaciones y las recomendaciones de la oficina, siempre que permitan especificar información más específica. Esto se realiza editando la información de ubicación descubierta y puede reducir las aproximaciones inherentes a la información de ubicación disponible para las mediciones de red.

## <a name="faq"></a>Preguntas frecuentes

### <a name="what-is-office-365-service-front-door"></a>¿Qué es el servicio de Office 365 puerta frontal?

La puerta frontal del servicio de Office 365 es un punto de entrada en la red global de Microsoft donde los clientes y servicios de Office terminan su conexión de red. Para obtener una conexión de red óptima a Office 365, se recomienda que la conexión de red se termine en la puerta frontal de Office 365 más cercana en su ciudad o metro.
Nota: la puerta delantera del servicio 365 de Office no tiene ninguna relación directa con el producto "Azure Front Door Service" disponible en Azure Marketplace.

### <a name="what-is-an-optimal-office-365-service-front-door"></a>¿Qué es una puerta frontal de servicio de Office 365 óptima?

Una puerta frontal del servicio Office 365 óptima es la que más se aproxime a la salida de la red, generalmente en su ciudad o área metropolitana. Use la herramienta de rendimiento de red de Office 365 para determinar la ubicación del servicio de Office 365 en uso en la puerta frontal y del servicio de la puerta de servicio óptima. Si la herramienta determina que la puerta frontal en uso es óptima, se está conectando de forma óptima a la red global de Microsoft.

### <a name="what-is-an-internet-egress-location"></a>¿Qué es una ubicación de salida de Internet?

La ubicación de salida de Internet es la ubicación en la que el tráfico de red sale de la red de la empresa y se conecta a Internet. También se identifica como la ubicación en la que tiene un dispositivo de traducción de direcciones de red (NAT) y normalmente donde se conecta con un proveedor de servicios de Internet (ISP). Si ve una larga distancia entre su ubicación y la ubicación de salida de Internet, puede identificar un backhaul de WAN importante.

## <a name="related-topics"></a>Temas relacionados

[Office 365 Network performance Insight (versión preliminar)](office-365-network-mac-perf-insights.md)

[Evaluación de la red de Office 365 (versión preliminar)](office-365-network-mac-perf-score.md)

[Herramienta de incorporación de red de Office 365 en el centro de administración de M365 (versión preliminar)](office-365-network-mac-perf-onboarding-tool.md)
