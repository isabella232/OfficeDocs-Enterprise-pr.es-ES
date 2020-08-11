---
title: Estrategia de defensa DoS de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: None
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: En este artículo, puede encontrar información general sobre la estrategia de defensa de Microsoft para ataques por denegación de servicio (DoS).
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 242ec7a6fed574a0e5aa767ab31c28fc33b28e88
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605542"
---
# <a name="microsoft-365-denial-of-service-defense-strategy"></a>Estrategia de defensa de denegación de servicio de Microsoft 365

La estrategia de Microsoft para defenderse contra los ataques de denegación de servicio (DoS) basados en red es única debido a nuestra escala y a la superficie global. Esta escala permite a Microsoft usar estrategias y técnicas para que puedan coincidir algunas organizaciones, proveedores o organizaciones de clientes. La piedra angular de la estrategia DoS es nuestra presencia global. Microsoft se compromete con los proveedores de Internet, los proveedores de emparejamiento (públicos y privados) y las corporaciones privadas de todo el mundo. Esto proporciona a Microsoft una presencia importante en Internet y permite a Microsoft absorber ataques en un área de gran superficie.

Teniendo en cuentan esta naturaleza única, Microsoft usa procesos de detección y mitigación que difieren de los usados por grandes empresas. La estrategia se basa en una separación de detección y mitigación global distribuida a través de muchos perímetros de red. Muchas empresas usan soluciones de terceros para detectar y mitigar los ataques en el perímetro. A medida que aumentaba la capacidad de la periferia de Microsoft, se denominó la importancia de cualquier ataque contra contornos individuales o específicos. Debido a esta configuración única, Microsoft separó los componentes de detección y mitigación. Microsoft implementa sistemas de detección de varios niveles para detectar ataques más cercanos a sus puntos de saturación, a la vez que mantiene una mitigación global en el perímetro. Esta estrategia garantiza que se puedan controlar varios ataques simultáneos.

Una de las defensas más eficaces y de bajo costo utilizadas por Microsoft contra ataques DoS es reducir las superficies de ataque al servicio. El tráfico no deseado se descarta en el perímetro de la red en lugar de analizar, procesar y limpiar los datos en línea.

En la interfaz con la red pública, Microsoft usa dispositivos de seguridad de propósito especial para el firewall, la traducción de direcciones de red y las funciones de filtrado IP. Microsoft también usa el enrutamiento global de igualdad de costos (ECMP). El enrutamiento de ECMP global es un marco de red para garantizar que hay varias rutas globales para llegar a un servicio. Con estas varias rutas, los ataques contra los servicios se limitan a la región desde la que se origina el ataque. Otras regiones no deberían verse afectadas por este ataque, ya que los usuarios finales usarían otras rutas para llegar al servicio en esas regiones. Microsoft también ha desarrollado sistemas de correlación y detección de DoS internos que usan datos de flujo, métricas de rendimiento y otra información. Se trata de un servicio en la nube de hiperescala en Microsoft Azure, que analiza los datos recopilados de varios puntos de los servicios y las redes de Microsoft. Un equipo de respuesta ante incidentes entre cargas de trabajo en DoS identifica los roles y las responsabilidades en Teams, los criterios de escalabilidad y los protocolos para la contratación de varios equipos y el tratamiento de incidentes. Estas soluciones proporcionan protección basada en red contra ataques DoS.

Por último, las cargas de trabajo basadas en la nube se configuran con umbrales optimizados basados en su Protocolo y el uso de ancho de banda debe proteger la carga de trabajo de manera exclusiva.
