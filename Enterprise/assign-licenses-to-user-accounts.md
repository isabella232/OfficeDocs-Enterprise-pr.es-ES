---
title: Asignar licencias de Office 365 a cuentas de usuario
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Describe cómo asignar licencias de Office 365 a cuentas de usuario, ya sea de forma individual o en función de la pertenencia a grupos.
ms.openlocfilehash: bc736236f9371ee1372fd36af4a707aca2ee1408
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745713"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a>Asignar licencias de Office 365 a cuentas de usuario

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Para el modelo de identidad solo de nube, puede asignar licencias de Office 365 a las cuentas de usuario a medida que se crean, en función de cómo las cree.

Para el modelo de identidad híbrida, cuando las cuentas de usuario de servicios de dominio de Active Directory (AD DS) se sincronizan por primera vez, no se les asigna automáticamente una licencia de Office 365.

En cualquier caso, debe asignar una licencia a las cuentas de usuario para que los usuarios puedan acceder a los servicios de Office 365, como el correo electrónico y Microsoft Teams.

Puede asignar licencias a cuentas de usuario, ya sea de forma individual o automática, a través de la pertenencia a grupos.

Para asignar licencias de Office 365 a cuentas de usuario individuales, puede usar:

- [Centro de administración de Microsoft 365](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

Para la asignación automática de licencias, consulte [licencias basadas en grupos en Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).

## <a name="next-steps"></a>Siguientes pasos

Con el conjunto completo de cuentas de usuario a las que se han asignado licencias, ya está listo para:

- [Implementar seguridad](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [Implementación de software de cliente, como Office 365 ProPlus](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [Configuración de la administración de dispositivos móviles](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [Configuración de servicios y aplicaciones](configure-services-and-applications.md)
