---
title: Asignar licencias de 365 de Microsoft a cuentas de usuario
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Describe cómo asignar licencias de 365 de Microsoft a cuentas de usuario, ya sea de forma individual o en función de la pertenencia a grupos.
ms.openlocfilehash: f28b9a6367cec2f67b664db2d43ba55b9cf19638
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2020
ms.locfileid: "44735938"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a>Asignar licencias de 365 de Microsoft a cuentas de usuario

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Para el modelo de identidad solo de nube, puede asignar licencias de Microsoft 365 a las cuentas de usuario a medida que se crean, en función de cómo las cree.

Para el modelo de identidad híbrida, cuando las cuentas de usuario de servicios de dominio de Active Directory (AD DS) se sincronizan por primera vez, no se les asigna una licencia de Microsoft 365 automáticamente. Primero debe configurar cada cuenta de usuario con una ubicación de usuario.

En cualquier caso, debe asignar una licencia a las cuentas de usuario para que los usuarios puedan acceder a los servicios de Microsoft 365, como el correo electrónico y Microsoft Teams.

Puede asignar licencias a cuentas de usuario, ya sea de forma individual o automática, a través de la pertenencia a grupos.

Para asignar licencias de 365 de Microsoft a cuentas de usuario individuales, puede usar:

- [Centro de administración de Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
- [PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

Para la asignación automática de licencias, consulte [licencias basadas en grupos en Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Siguientes pasos

Con el conjunto completo de cuentas de usuario a las que se han asignado licencias, ya está listo para:

- [Implementar seguridad](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [Implementación de software cliente, como aplicaciones de Microsoft 365](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [Configurar la administración de dispositivos móviles en Microsoft 365](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [Configuración de servicios y aplicaciones](configure-services-and-applications.md)
