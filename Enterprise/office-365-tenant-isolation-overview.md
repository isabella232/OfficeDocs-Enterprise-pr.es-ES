---
title: Aislamiento de inquilinos en Microsoft 365
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
description: Este artículo contiene un resumen de cómo Microsoft aplica el aislamiento de inquilino en servicios en la nube, como Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 531b5023af49c776cccfef06dee5bff4b303beff
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606546"
---
# <a name="tenant-isolation-in-microsoft-365"></a>Aislamiento de inquilinos en Microsoft 365

Una de las principales ventajas de la informática en la nube es el concepto de una infraestructura compartida común en numerosos clientes a la vez, lo que lleva a economías de escala. Este concepto se denomina *multiempresa*. Microsoft funciona continuamente para garantizar que las arquitecturas multiinquilinos de nuestros servicios en la nube admitan la seguridad de ámbito empresarial, la confidencialidad, la privacidad, la integridad y los estándares de disponibilidad.

De acuerdo con las importantes inversiones y la experiencia obtenida de la [informática de confianza](https://www.microsoft.com/trust-center) y el ciclo de vida de [desarrollo de seguridad](https://www.microsoft.com/securityengineering/sdl/), los servicios en la nube de Microsoft se diseñaron con la hipótesis de que todos los inquilinos son potencialmente hostiles a todos los demás inquilinos, y hemos implementado medidas de seguridad para evitar que las acciones de un inquilino afecten a la seguridad o el servicio de

Los dos objetivos principales de mantener el aislamiento de inquilino en un entorno multiempresa son:

1.    Evitar la fuga o el acceso no autorizado a contenido de clientes entre inquilinos; y
2.    Evitar que las acciones de un inquilino afecten negativamente al servicio para otro espacio empresarial

Se han implementado varias formas de protección en Microsoft 365 para evitar que los clientes pongan en peligro los servicios o las aplicaciones de Microsoft 365 o que obtengan acceso no autorizado a la información de otros inquilinos o del propio sistema de Microsoft 365, incluidos:

- El aislamiento lógico del contenido del cliente dentro de cada inquilino para los servicios de Microsoft 365 se consigue a través de la autorización y el control de acceso basado en roles de Azure Active Directory.
- SharePoint Online proporciona mecanismos de aislamiento de datos en el nivel de almacenamiento.
- Microsoft usa una rigurosa seguridad física, detección en segundo plano y una estrategia de cifrado de varias capas para proteger la confidencialidad y la integridad del contenido del cliente. Todos los centros de recursos de Microsoft 365 tienen controles de acceso biométricos, con la mayoría de los que requieren impresiones de Palm para obtener acceso físico. Además, todos los empleados de Microsoft en Estados Unidos deben realizar correctamente una comprobación de antecedentes estándar como parte del proceso de contratación. Para obtener más información acerca de los controles usados para el acceso administrativo en Microsoft 365, consulte [microsoft 365 Administrative Access Controls](office-365-administrative-access-controls-overview.md).
- Microsoft 365 usa tecnologías de servicio que cifran el contenido del cliente en reposo y en tránsito, incluidos BitLocker, el cifrado por archivo, la seguridad de la capa de transporte (TLS) y el protocolo de seguridad de Internet (IPsec). Para obtener información específica sobre el cifrado en Microsoft 365, consulte [tecnologías de cifrado de datos en microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/office-365-encryption-in-the-microsoft-cloud-overview).

Juntas, las protecciones de la lista anterior proporcionan controles sólidos de aislamiento lógico que proporcionan protección contra amenazas y mitigación equivalente a la que proporciona el aislamiento físico por sí solo.

## <a name="related-links"></a>Vínculos relacionados

- [Aislamiento y Control de acceso en Azure Active Directory](office-365-isolation-in-azure-active-directory.md)
- [Aislamiento del inquilino en Office Graph y Delve](office-365-isolation-in-graph-and-delve.md)
- [Aislamiento de inquilino en Búsqueda de Microsoft 365](office-365-isolation-in-office-365-search.md)
- [Aislamiento del inquilino en Office 365 Video](office-365-isolation-in-office-365-video.md)
- [Límites de recursos](office-365-resource-limits.md)
- [Supervisar y probar los límites de inquilinos](office-365-monitoring-and-testing.md)
- [Aislamiento y control de acceso en Microsoft 365](office-365-isolation-in-office-365.md)
