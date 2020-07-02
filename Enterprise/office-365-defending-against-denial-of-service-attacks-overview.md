---
title: Defenderse contra ataques por denegación de servicio en Microsoft 365
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
description: Información general sobre los ataques de denegación de servicio (DoS).
ms.openlocfilehash: 2cbe5eb86402fd7b7888f39440a58935604c90eb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998424"
---
# <a name="defend-against-denial-of-service-attacks-in-microsoft-365"></a>Defenderse contra ataques por denegación de servicio en Microsoft 365

## <a name="introduction"></a>Introducción

Microsoft ofrece una infraestructura de confianza para más de 200 servicios en la nube hospedados en una infraestructura de nube global de más de 100 centros de recursos. Entre ellos se incluyen:

- Microsoft Azure
- Microsoft Bing
- Microsoft Dynamics 365
- Microsoft 365 y Office 365
- Microsoft OneDrive
- Skype
- Xbox Live

Como organización global con una presencia importante en Internet y muchas propiedades de Internet destacadas que proporcionan servicios en la nube, Microsoft es un objetivo común y amplio para los hackers y otras personas malintencionadas. La capa de comunicación de red entre los clientes y la nube de Microsoft es uno de los principales objetivos de ataques malintencionados. De hecho, Microsoft es de manera continua y persistente bajo alguna forma de ciberataque basada en la red. En línea con esto, Microsoft usa principios de seguridad de defensa en profundidad para proteger sus redes y servicios en la nube. Sin sistemas de mitigación confiable y persistente que defienden contra estos ataques, los servicios en la nube de Microsoft estarán sin conexión y no estarán disponibles para los clientes.

## <a name="definition-and-symptoms-of-denial-of-service-attacks"></a>Definición y síntomas de ataques por denegación de servicio

Una forma de atacar los servicios de red es crear muchas solicitudes a los hosts de servicio para saturar la red y los servidores para denegar el servicio a los usuarios legítimos. Esto se conoce como un ataque de denegación de servicio (DoS). Cuando varios actores, extremos o vectores realizan el ataque, se hace referencia a él como un ataque de denegación de servicio (DDoS) distribuido. Aunque los medios, motivos y objetivos varían, los ataques entre DoS y DDoS suelen estar formados por los esfuerzos para evitar que un sitio o servicio de Internet funcione correctamente o en su totalidad, ya sea de forma temporal o indefinida.

El equipo de [preparación de emergencia para equipos de Estados Unidos](https://www.us-cert.gov/) (US-CERT) define los síntomas de ataques dos para incluir:

- Rendimiento de red inusualmente lento (al abrir archivos o acceder a sitios de Internet)
- No disponibilidad de un sitio web
- Incapacidad para obtener acceso a un sitio web
- Aumento espectacular en el correo no deseado recibido
- Desconexión de una conexión a Internet inalámbrica o cableada
- Pérdida a largo plazo de acceso a la web o a cualquier servicio de Internet

## <a name="related-topics"></a>Temas relacionados

- [Principios básicos de la defensa contra ataques por denegación de servicio](office-365-core-principles-of-defense-against-dos-attacks.md)
- [Estrategia de la defensa de denegación de servicio de Microsoft](office-365-microsoft-dos-defense-strategy.md)
- [Defensa de los servicios en la nube de Microsoft contra ataques por denegación de servicio](office-365-defending-cloud-services-against-dos-attacks.md)
