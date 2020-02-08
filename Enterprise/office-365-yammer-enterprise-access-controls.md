---
title: Controles de acceso empresarial de Office 365 Yammer
ms.author: robmazz
author: robmazz
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
description: 'Resumen: un breve resumen sobre los controles de acceso empresarial de Yammer en el entorno de producción.'
ms.openlocfilehash: 9b88ff0f8c480dd3726246e47714d9468509ef08
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841797"
---
# <a name="yammer-enterprise-access-controls"></a>Controles de acceso de Yammer Enterprise 

El acceso físico y lógico al entorno de producción de Yammer está restringido a un pequeño conjunto de personas (infraestructura y operaciones). Como con otros ingenieros de Office 365, los ingenieros de Yammer tienen un acceso sin igual a los datos de los clientes. El acceso debe solicitarse mediante un sistema de control de acceso Just-in-Time basado en aprobaciones similar a Lockbox con un número limitado de aprobadores. Los aprobadores comprueban la solicitud (por ejemplo, comprueban si la solicitud es legítima según la necesidad, el caso de negocio, la hora, etc.) y, a continuación, aprueba o deniega la solicitud. Si se aprueba la solicitud, se concede el acceso JIT durante un tiempo definido y limitado. Una vez que se ha superado el tiempo de acceso, el acceso expira automáticamente.

Como con otros servicios de Office 365, todos los accesos al entorno de producción de Yammer usan la autenticación multifactor. Todo el historial de acceso y comandos se atribuye a un usuario y ha sido registrado y revisado con regularidad por el equipo de seguridad de Yammer.

Para obtener más información acerca de la administración y administración de Yammer, consulte [ayuda del administrador de Yammer](https://support.office.com/article/yammer-–-admin-help-e1464355-1f97-49ac-b2aa-dd320b179dbe?ui=en-US&rs=en-US&ad=US).