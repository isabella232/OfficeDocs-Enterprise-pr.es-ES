---
title: Controles de aislamiento de Microsoft 365
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
description: 'Resumen: una explicación de los controles de aislamiento en Microsoft 365.'
ms.openlocfilehash: da26bb6a41c97a16865bfdd5bdf6aada2069f7fe
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774915"
---
# <a name="microsoft-365-isolation-controls"></a>Controles de aislamiento de Microsoft 365 

Microsoft funciona continuamente para garantizar que la arquitectura multiempresa de Microsoft 365 admita [estándares](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons)de seguridad, confidencialidad, privacidad, integridad, locales, internacionales y disponibilidad de nivel empresarial. La escala y el alcance de los servicios proporcionados por Microsoft hacen que sea difícil y no rentable administrar Microsoft 365 con una interacción humana importante. Los servicios de Microsoft 365 se proporcionan a través de varios centros de datos distribuidos globalmente, cada uno de ellos muy automatizado, con pocas operaciones que requieran un toque humano o cualquier acceso al contenido del cliente. Nuestro personal es compatible con estos servicios y centros de datos mediante herramientas automatizadas y acceso remoto extremadamente seguro. 

Microsoft 365 está formado por varios servicios que proporcionan una funcionalidad empresarial importante y contribuyen a la experiencia de Microsoft 365 completa. Cada uno de estos servicios es independiente y está diseñado para integrarse entre sí.

Microsoft 365 se ha diseñado con los siguientes principios:

 - ** [Arquitectura orientada a servicios](https://docs.microsoft.com/previous-versions/aa480021(v=msdn.10)):** diseño y desarrollo de software en forma de servicios interoperables que proporcionan una funcionalidad empresarial bien definida.
 - **[Garantía de seguridad operativa](https://www.microsoft.com/download/details.aspx?id=40872):** un marco que incorpora los conocimientos adquiridos a través de diversas capacidades que son exclusivas de Microsoft, incluido el [ciclo de vida de desarrollo de seguridad](https://www.microsoft.com/sdl/default.aspx)de Microsoft, [Microsoft Security Response Center](https://technet.microsoft.com/library/dn440717.aspx)y un conocimiento profundo del panorama de las amenazas de Cybersecurity.

Los servicios de Microsoft 365 interoperan entre sí, pero están diseñados e implementados para que se puedan implementar y operar como servicios autónomos, independientes entre sí. Microsoft segrega tareas y áreas de responsabilidad para Microsoft 365 para reducir las oportunidades de modificación no autorizada o accidental o uso incorrecto de los activos de la organización. Microsoft 365 Teams tienen roles definidos como parte de un mecanismo completo de control de acceso basado en roles.

## <a name="customer-content-isolation"></a>Aislamiento de contenido de cliente

Todo el contenido de los clientes de un espacio empresarial se aísla de los otros inquilinos y de los datos de operaciones y sistemas usados en la administración de Microsoft 365. En Microsoft 365 se implementan varias formas de protección para minimizar el riesgo de que se comprometa la amenaza de cualquier servicio o aplicación de Microsoft 365. Varias formas de protección también evitan el acceso no autorizado a la información de los inquilinos o el propio sistema de Microsoft 365.

Para obtener información sobre cómo Microsoft implementa el aislamiento lógico de los datos de inquilino dentro de Microsoft 365, vea [aislamiento de inquilinos en microsoft 365](office-365-tenant-isolation-overview.md).
