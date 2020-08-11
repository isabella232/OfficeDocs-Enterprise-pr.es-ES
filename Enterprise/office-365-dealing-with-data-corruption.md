---
title: Microsoft 365 tratar los daños en los datos
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
ms.custom: seo-marvel-apr2020
description: En este artículo se explican los datos dañados en Microsoft 365 y los esfuerzos realizados por Microsoft para evitar y recuperar datos.
ms.openlocfilehash: dc8e865a69e110fa0a68e6cd9d9f4d6b45d43d71
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606636"
---
# <a name="dealing-with-data-corruption-in-microsoft-365"></a>Información relacionada con los datos dañados en Microsoft 365

Uno de los aspectos desafiantes de la ejecución de un servicio en la nube a gran escala es cómo controlar los daños en los datos, dado el gran volumen de datos y sistemas independientes. Los daños en los datos pueden deberse a:

- Errores de aplicaciones o de infraestructura, que dañan parte o todo el estado de la aplicación
- Problemas de hardware que producen datos perdidos o la incapacidad de leer datos
- Errores operativos humanos
- Hackers malintencionados y empleados descontentos
- Incidentes en servicios externos que resultan en alguna pérdida de datos

Debido a que una mayor resistencia en la integridad de los datos significa menos incidentes de daños en los datos, Microsoft ha integrado los mecanismos de protección 365 de Microsoft para evitar que se produzcan daños, así como sistemas y procesos que nos permiten recuperar datos si es así. Las comprobaciones y procesos existen en las distintas fases del proceso de lanzamiento de ingeniería para aumentar la resistencia contra daños en los datos, entre los que se incluyen:

- Diseño del sistema
- Estructura y organización del código
- Revisión de código
- Pruebas unitarias, pruebas de integración y pruebas del sistema
- Pruebas/puertas de cables de viaje

Dentro de los entornos de producción de Microsoft 365, la replicación del mismo nivel entre centros de datos garantiza que siempre habrá varias copias activas de todos los datos. Las imágenes y los scripts estándar se usan para recuperar los servidores perdidos y los datos replicados se usan para restaurar los datos del cliente. Debido a las comprobaciones y procesos integrados de resistencia de datos, Microsoft solo mantiene copias de seguridad de la documentación del sistema de información de Microsoft 365 (incluida la documentación relacionada con la seguridad), mediante la replicación integrada en SharePoint Online y nuestra herramienta de repositorio de código interno, Source Depot. La documentación del sistema se almacena en SharePoint Online y Source Depot contiene imágenes del sistema y de la aplicación. SharePoint Online y Source Depot usan el control de versiones y se replican casi en tiempo real.
