---
title: API de Actividad de administración de Office 365
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
- M365-analytics
f1.keywords:
- NOCSH
description: En este artículo, puede encontrar un breve resumen sobre la API de actividad de administración de Office 365 y la información que proporciona desde los registros de actividades.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 05b47be60816b09a24df3dd0076a4d0cbcdabe84
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605552"
---
# <a name="office-365-management-activity-api"></a>API de Actividad de administración de Office 365

Microsoft proporciona Reporting Services que puede usar para obtener información de transacciones agregada sobre su inquilino de Office 365. La [API de actividad de administración 365 de Office](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview#office-365-management-activity-api) usa un diseño RESTful estándar del sector y OAuth v2 para la autenticación. Esto hace que sea fácil empezar a experimentar con la recuperación de datos y a su recopilación en herramientas y aplicaciones de visualización. La API proporciona una fuente de datos con información sobre el usuario, el administrador, las operaciones y la actividad de seguridad en Office 365. Los datos pueden conservarse con fines regulatorios o combinarse con datos de registros que se retienen de una infraestructura local u otros orígenes. Esto ayuda a crear una solución de supervisión para operaciones, seguridad y cumplimiento de normas en toda la empresa.

La API de actividad de administración de Office 365 proporciona información sobre diversas acciones y eventos de usuario, administrador, sistema y directiva de los registros de actividad de Office 365 y Azure Active Directory. La API proporciona un esquema de auditoría coherente con más de 10 campos comunes en todos los servicios. La API permite que las organizaciones realicen conexiones entre eventos fácilmente y habilita nuevas formas de razonamiento sobre los datos.

Docenas de proveedores de software independientes (ISV) asociados con Microsoft y han creado soluciones basadas en la API. Algunas soluciones se centran únicamente en los datos de Office 365 y en otros datos de origen de varios proveedores de nube y sistemas locales para crear una vista unificada de las operaciones, la seguridad y la actividad relacionada con el cumplimiento. 

Para obtener más información, vea la referencia de la [API de actividad de administración de Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference).
