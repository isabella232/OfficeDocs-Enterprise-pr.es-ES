---
title: Evaluación de red de Microsoft 365 (versión preliminar)
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/21/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
description: Evaluación de red de Microsoft 365 (versión preliminar)
ms.openlocfilehash: 3554c86b94e6b24cf82231da640b7e010fe07c11
ms.sourcegitcommit: 07ab7d300c8df8b1665cfe569efc506b00915d23
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "43612900"
---
# <a name="microsoft-365-network-assessment-preview"></a>Evaluación de red de Microsoft 365 (versión preliminar)

En la página Microsoft 365 del centro de administración de Microsoft para Microsoft 365, **evaluación** de la red divide una amplia variedad de métricas de rendimiento de red en una instantánea del estado de la red de la empresa, representada por un valor Points de 1-100. Las evaluaciones de red están en el ámbito de todo el inquilino y en cada ubicación geográfica desde la que los usuarios se conectan a su espacio empresarial, lo que proporciona a los administradores de Microsoft 365 una manera fácil de captar de forma instantánea un Gestalt del estado de la red de la empresa y profundizar rápidamente en un informe detallado de cualquier ubicación global de la oficina.

El valor de puntos de evaluación de red es una medición promedio de las métricas de latencia, ancho de banda, velocidad de descarga y calidad de la conexión que se compila en directo en el momento en que se ven. Las métricas de rendimiento para las redes que son propiedad de Microsoft se excluyen de estas medidas para garantizar que los resultados de la evaluación sean inequívocos y específicos de la red corporativa.

![Valor de evaluación de la red](Media/m365-mac-perf/m365-mac-perf-overview-score-top.png)

Un valor muy bajo de evaluación de la red sugiere que los clientes de Microsoft 365 tendrán problemas importantes para conectarse al inquilino o mantener una experiencia de usuario con capacidad de respuesta, mientras que un valor alto indica una red configurada correctamente con pocos problemas de rendimiento continuos. Un valor de 80% representa una línea de base sana en la que no debería esperar recibir quejas de los usuarios habituales sobre la conectividad de Microsoft 365 o la capacidad de respuesta debido al rendimiento de la red. A medida que se realizan mejoras de conectividad de red reiterativas, este valor aumentará junto con la experiencia del usuario.

>[!IMPORTANT]
>Información sobre la red, recomendaciones de rendimiento y evaluaciones en el centro de administración de Microsoft 365 se encuentra actualmente en estado de versión preliminar y solo está disponible para los inquilinos de Microsoft 365 que se han inscrito en el programa de vista previa de características.

## <a name="network-assessment-panel"></a>Panel evaluación de red

Cada evaluación de la red, ya sea en el ámbito del inquilino o en una ubicación específica de la oficina, muestra un panel con detalles sobre la evaluación. Este panel muestra un gráfico de barras de la evaluación como un porcentaje y como los puntos totales para cada carga de trabajo de componente, incluidas solo cargas de trabajo en las que se recibieron datos de medición. Para una evaluación de red de ubicación de oficina, también se muestra un benchmark que es la mediana de todos los clientes de Microsoft 365 que han notificado datos en la misma ciudad que la ubicación de la oficina.

![Valor de evaluación de red de ejemplo](Media/m365-mac-perf/m365-mac-perf-overview-score.png)

El **desglose** de la evaluación en el panel muestra la evaluación de cada una de las cargas de trabajo de componentes.

El **historial** de la evaluación muestra los últimos 30 días de la evaluación y el Banco de pruebas.

## <a name="tenant-network-assessments-and-office-location-network-assessments"></a>Evaluaciones de red de inquilinos y evaluaciones de red de ubicación de oficina

Una evaluación de la red mide el diseño del perímetro de la red de una ubicación de la oficina a la red de Microsoft. Las mejoras en el perímetro de la red se realizan mejor en cada ubicación de la oficina o cuando se agrega conectividad de red puede haber mejoras que afectan a varias ubicaciones.

Se muestra un valor de evaluación de red para todo el espacio empresarial de Microsoft 365 en la página información general de rendimiento de red y un valor específico para cada ubicación de la oficina detectada en la página de Resumen de esa ubicación.

## <a name="exchange-online"></a>Exchange Online

Para Exchange Online se mide la latencia TCP desde el equipo cliente al servidor front-end de Exchange. Esto puede verse afectado por la distancia que la red viaja a través de la LAN y la WAN de los clientes. También puede verse afectado por servicios o dispositivos intermedios de red que retrasn la conectividad o provocan la reenvío de paquetes.

## <a name="sharepoint-online"></a>SharePoint Online

Para SharePoint Online, se mide la velocidad de descarga disponible para que un usuario tenga acceso a un documento. Esto puede verse afectado por el ancho de banda disponible en los circuitos de red entre el equipo cliente y la red de Microsoft. También suele afectar a la congestión de la red que existe en los cuellos de botella en dispositivos de red complejos o en áreas de Wi-Fi de mala cobertura.

## <a name="microsoft-teams"></a>Microsoft Teams

Para Microsoft Teams, la calidad de la red se mide como latencia UDP, vibración UDP y pérdida de paquetes UDP. UDP se usa para la conectividad de medios de audio y vídeo de conferencias y llamadas de Microsoft Teams. Esto se puede ver afectado por los mismos factores que para la latencia y la velocidad de descarga, además de las brechas de conectividad en la compatibilidad con UDP de una red, ya que UDP se configura por separado en el protocolo TCP más común.

## <a name="related-topics"></a>Temas relacionados

[Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)](office-365-network-mac-perf-overview.md)

[Microsoft 365 Network performance Insight (versión preliminar)](office-365-network-mac-perf-insights.md)

[Prueba de conectividad de Microsoft 365 en el centro de administración de M365 (versión preliminar)](office-365-network-mac-perf-onboarding-tool.md)

[Servicios de ubicación de conectividad de red 365 de Microsoft (versión preliminar)](office-365-network-mac-location-services.md)
