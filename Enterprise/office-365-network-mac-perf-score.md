---
title: Evaluación de la red de Office 365 (versión preliminar)
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
description: Evaluación de la red de Office 365 (versión preliminar)
ms.openlocfilehash: f919eeb2771095502865b4a5079b91eb8d7efe36
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106442"
---
# <a name="office-365-network-assessment-preview"></a>Evaluación de la red de Office 365 (versión preliminar)

La evaluación de red de Office 365 indica el impacto relativo de la experiencia del usuario con respecto a la conectividad de red del cliente. El impacto de cualquier conectividad de red de Microsoft se excluye de esto para permitir a los clientes optimizar los diseños de red de los que son responsables.

Se calcula a partir de las medidas que afectan a la experiencia del usuario en las cargas de trabajo de Office 365 y se muestran como un porcentaje con un intervalo de 0 a 100.

Una puntuación de red muy baja sugiere que los clientes de Office 365 tendrán problemas significativos para conectar o hacer que el usuario responda correctamente. Una puntuación de 80% representa la conectividad de red, en la que no se debe esperar recibir quejas del usuario sobre la experiencia del usuario de Office 365 debido al rendimiento de la red. A medida que se realizan mejoras en la conectividad de red, esta puntuación aumentará junto con la experiencia del usuario.

>[!IMPORTANT]
>Las recomendaciones de rendimiento de red, información y evaluaciones en el centro de administración de Microsoft 365 se encuentra actualmente en estado de versión preliminar y solo está disponible para los inquilinos de Office 365 que se han inscrito en el programa de vista previa de características.

## <a name="exchange-online"></a>Exchange Online

Para Exchange Online se mide la latencia TCP desde el equipo cliente al servidor front-end de Exchange. Esto puede verse afectado por la distancia que la red viaja a través de la LAN y la WAN de los clientes. También puede verse afectado por servicios o dispositivos intermedios de red que retrasn la conectividad o provocan la reenvío de paquetes.

## <a name="sharepoint-online"></a>SharePoint Online

Para SharePoint Online, se mide la velocidad de descarga disponible para que un usuario tenga acceso a un documento. Esto puede verse afectado por el ancho de banda disponible en los circuitos de red entre el equipo cliente y la red de Microsoft. También suele afectar a la congestión de la red que existe en los cuellos de botella en dispositivos de red complejos o en áreas de Wi-Fi de mala cobertura.

## <a name="microsoft-teams"></a>Microsoft Teams

Para Microsoft Teams, la calidad de la red se mide como latencia UDP, vibración UDP y pérdida de paquetes UDP. UDP se usa para la conectividad de medios de audio y vídeo de conferencias y llamadas de Microsoft Teams. Esto se puede ver afectado por los mismos factores que para la latencia y la velocidad de descarga, además de las brechas de conectividad en la compatibilidad con UDP de una red, ya que UDP se configura por separado en el protocolo TCP más común.

## <a name="tenant-network-score-and-office-location-network-score"></a>Puntuación de red de inquilinos y puntuación de red de ubicación de oficina

Una puntuación de red mide el diseño del perímetro de red de una ubicación de la oficina a la red de Microsoft. Las mejoras en el perímetro de la red se realizan mejor en cada ubicación de la oficina o cuando se agrega conectividad de red puede haber mejoras que afectan a varias ubicaciones.
Se muestra una puntuación de red para todo el inquilino de Office 365 en la página información general de rendimiento de red y una puntuación de red específica para cada ubicación de la oficina detectada en la página de Resumen de esa ubicación.

## <a name="network-score-panel"></a>Panel de puntuación de red

Cada puntuación de red, ya sea para el inquilino o para una ubicación específica de la oficina, muestra un panel con detalles sobre la puntuación. Este panel muestra un gráfico de barras con la puntuación como un porcentaje y como los puntos totales para cada carga de trabajo de componente, incluidas solo cargas de trabajo en las que se recibieron datos de medición. Para una puntuación de red de ubicación de oficina, también se muestra un benchmark que es la mediana de todos los clientes de Office 365 que han notificado datos en la misma ciudad que la ubicación de la oficina.

El desglose de la puntuación en el panel muestra la puntuación de cada una de las cargas de trabajo de componente.

El historial de puntuación muestra los últimos 30 días de la puntuación y el Banco de pruebas.

## <a name="related-topics"></a>Temas relacionados

[Recomendaciones de rendimiento de red en el centro de administración de Microsoft 365 (versión preliminar)](office-365-network-mac-perf-overview.md)

[Office 365 Network performance Insight (versión preliminar)](office-365-network-mac-perf-insights.md)

[Herramienta de incorporación de red de Office 365 en el centro de administración de M365 (versión preliminar)](office-365-network-mac-perf-onboarding-tool.md)
