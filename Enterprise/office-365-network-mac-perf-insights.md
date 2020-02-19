---
title: Office 365 Network performance Insight (versión preliminar)
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
description: Office 365 Network performance Insight (versión preliminar)
ms.openlocfilehash: 2e57ffabec5b2172cb36f10135406ddda95bc1c5
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106449"
---
# <a name="office-365-network-performance-insights-preview"></a>Office 365 Network performance Insight (versión preliminar)

Las páginas de rendimiento de la red del centro de administración de 365 de Microsoft muestran Office 365 Network Insights, que puede ayudarle a diseñar perímetros de red para sus ubicaciones de oficina. Hay cinco información de red específica que se puede mostrar para cada ubicación de la oficina.

>[!IMPORTANT]
>Las recomendaciones de rendimiento de red, información y evaluaciones en el centro de administración de Microsoft 365 se encuentra actualmente en estado de versión preliminar y solo está disponible para los inquilinos de Office 365 que se han inscrito en el programa de vista previa de características.

## <a name="backhauled-network-egress"></a>Salida de red en recorrido

La distancia desde la ubicación del usuario hasta la red de salida es superior a 500 millas (800 kilómetros) y se espera que esto afecte al rendimiento. Se recomienda la salida local más cercana al usuario.

Esto identifica que la distancia entre la ubicación de la oficina y la red de salida es de más de 500 millas. La ubicación de la oficina se identifica con una ubicación de equipo cliente confusa y la ubicación de salida de red se identifica con las bases de datos dirección IP inversa para la ubicación. La ubicación de la oficina puede no ser exacta si servicios de ubicación de Windows está deshabilitado en los equipos. La ubicación de salida de red puede ser inexacta si la información de la base de datos de direcciones IP inversas no es exacta.

Los detalles de esta visión incluyen la ubicación de la oficina, la ubicación de salida de red y la distancia entre ellas.

Para esta visión, recomendamos que se acerque la salida de red a la ubicación de la oficina para que la conectividad pueda enrutarse de forma óptima a la red de Microsoft en Internet y a las puertas frontales del servicio 365 de Office. Dejar la red cercana a los usuarios las ubicaciones de la oficina también permiten un mejor rendimiento en el futuro, ya que Microsoft expande los puntos de la red de presencia y las puertas frontales del servicio de Office 365 en el futuro.

Esta información se abrevia como "salida" en algunas vistas de resumen.

## <a name="better-performance-detected-for-customers-near-you"></a>Se ha detectado un mejor rendimiento para los clientes cercanos

Dado que un número significativo de clientes en el área metropolitana tiene mejor rendimiento que los usuarios de la organización en esta ubicación de la oficina.

Esto se centra en el rendimiento agregado de los clientes de Office 365 en la misma ciudad que esta ubicación de la oficina.

![Rendimiento de red relativo](Media/m365-mac-perf/m365-mac-perf-relative-perf.png)

Se calcula el porcentaje de clientes de Office 365 en la misma ciudad en los mejores depósitos de rendimiento. Si este número es el 10% de más, muestra el conocimiento de la red.

Esta información se abrevia como "homólogos" en algunas vistas de resumen.

## <a name="use-of-a-non-optimal-exchange-online-service-front-door"></a>Uso de una puerta principal no óptima del servicio de Exchange Online

El usuario no se conecta a una puerta de enlace de servicio 365 de Office óptima y se espera que se vea afectado el rendimiento.

Enumeramos las puertas frontales del servicio de Exchange online que son adecuadas para su uso desde la ciudad de la ubicación de la oficina con buen rendimiento. Si la prueba actual muestra el uso de una puerta de servicio de Exchange online que no está en esta lista, se indica esta recomendación.

El uso de un servicio de Exchange online no óptimo puede deberse a una backhaul? n de red antes de que la red corporativa se deshaga, en cuyo caso se recomienda la salida local y directa de la red. También podría deberse al uso de un servidor remoto de resolución de recursiva de DNS, en cuyo caso se recomienda alinear el servidor de resolución de DNS recursivo con la salida de red.

Esta información se abrevia como "enrutamiento" en algunas vistas de resumen.

## <a name="use-of-non-optimal-sharepoint-online-service-front-door"></a>Uso de puerta frontal no óptima del servicio de SharePoint Online

El usuario no se conecta al servicio de puerta de enlace frontal de SharePoint Online más cercano. Se espera que se vea afectado el rendimiento.

Identificamos la puerta frontal del servicio de SharePoint Online a la que se conecta el cliente de prueba. A continuación, para la ciudad de la ubicación de la oficina, la encontrarás en la puerta frontal esperada del servicio de SharePoint Online para esa ciudad. Si no coincide, realizamos esta recomendación.

Esta información se abrevia como "AFD" en algunas vistas de resumen.

## <a name="low-download-speed-from-sharepoint-front-door"></a>Velocidad de descarga baja desde la puerta frontal de SharePoint

La velocidad de descarga de red sub óptima detecta el tiempo que se tarda en cargar documentos de OneDrive para la empresa.

La velocidad de descarga que un usuario puede obtener del servicio de SharePoint Online y OneDrive para la empresa las puertas del anverso se mide en megabytes por segundo (MBps). Si este valor es inferior a 1 MBps, proporcionaremos esta visión.

Para mejorar la velocidad de descarga, es posible que sea necesario aumentar el ancho de banda que puede tener un usuario. Como alternativa, puede que exista una congestión de red entre los equipos de los usuarios en la ubicación de la oficina y la puerta de servicio de SharePoint Online. A veces se denomina pérdida de Congestive y restringe la velocidad de descarga disponible para los usuarios, incluso si hay suficiente ancho de banda disponible.

Esta información se abrevia como "rendimiento" en algunas vistas de resumen.

## <a name="related-topics"></a>Temas relacionados

[Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)](office-365-network-mac-perf-overview.md)

[Evaluación de la red de Office 365 (versión preliminar)](office-365-network-mac-perf-score.md)

[Herramienta de incorporación de red de Office 365 en el centro de administración de M365 (versión preliminar)](office-365-network-mac-perf-onboarding-tool.md)
