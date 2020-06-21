---
title: Controles de acceso de supervisión y auditoría de Microsoft 365
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
description: 'Resumen: Resumen de los diversos controles de acceso de supervisión y auditoría disponibles en Microsoft 365.'
ms.openlocfilehash: aba1a9966cf50735ba3348fe126d7b4c9233b4b2
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774875"
---
# <a name="monitoring-and-auditing-access-controls-in-microsoft-365"></a>Supervisión y auditoría de controles de acceso en Microsoft 365

Microsoft realiza una supervisión y auditoría exhaustiva de toda la delegación, los privilegios y las operaciones que se producen en Microsoft 365. El control de acceso de Microsoft 365 es un proceso automatizado que se basa en el principio de privilegios mínimos y que incorpora controles y auditorías de acceso a los datos:

- Todo el acceso permitido se puede trazar a un usuario único. Los administradores son responsables de su control del contenido del cliente.
- Se capturan las solicitudes de control de acceso, las aprobaciones y los registros de operaciones administrativas para analizar la seguridad y los eventos malintencionados.
- Los niveles de acceso se revisan casi en tiempo real en función de la pertenencia a grupos de seguridad para garantizar que solo los usuarios que tengan justificaciones empresariales autorizadas y cumplan los requisitos de elegibilidad tienen acceso a los sistemas.
- Microsoft 365, sus controles de acceso y los servicios de soporte, incluidos Azure Active Directory y centros de recursos físicos, son periódicamente auditados por terceros independientes para el cumplimiento de las normas [ISO/iec 27001](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27001), [iso/IEC 27018](https://www.microsoft.com/TrustCenter/Compliance/iso-iec-27018), [SOC](https://www.microsoft.com/TrustCenter/Compliance/SOC), [FedRAMP](https://www.microsoft.com/TrustCenter/Compliance/FedRAMP)y otros [estándares](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons).
- Los ingenieros de 365 de Microsoft deben realizar un aprendizaje de seguridad anual, revisar los procedimientos de acceso elevado y confirmar las directivas de seguridad y privacidad de Microsoft para mantener los derechos del servicio.

Las alertas automatizadas se desencadenan cuando se detecta actividad sospechosa, como varios inicios de sesión erróneos en un período corto. El equipo de respuesta de seguridad 365 de Microsoft usa el aprendizaje automático y el análisis de datos extensos para revisar y analizar la actividad, buscar patrones de acceso irregulares y responder de forma proactiva a actividades anómalas y ilícitas. Microsoft también emplea un equipo dedicado de evaluadores de penetración y participa en el equipo en rojo periódico y en los ejercicios de equipo azul para encontrar los problemas de seguridad y control de acceso en el servicio. Los clientes pueden comprobar la eficacia de los sistemas de control de acceso mediante el uso de informes de auditoría y la API de actividad de administración proporcionada por Microsoft 365.

Para obtener más información, consulte referencia de la [API de actividad de administración de Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference) y [Auditoría e informes en Microsoft 365](office-365-auditing-and-reporting-overview.md).
