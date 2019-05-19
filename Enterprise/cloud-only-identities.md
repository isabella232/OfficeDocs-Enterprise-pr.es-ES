---
title: Identidades de solo nube de Office 365
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
description: Describe cómo crear usuarios y grupos cuando la suscripción de Office 365 usa identidades de solo nube.
ms.openlocfilehash: 7a2aaf7705378da3cbd91b415f07d10b6e039293
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164615"
---
# <a name="office-365-cloud-only-identities"></a>Identidades de solo nube de Office 365

Con la identidad solo de nube, todos los usuarios, grupos y contactos se almacenan en el inquilino de Azure Active Directory (Azure AD) de la suscripción a Office 365. Estos son los componentes básicos de la identidad solo de la nube.
 
![](./media/about-office-365-identity/cloud-only-identity.png)

Los usuarios y sus cuentas de usuario en las organizaciones se pueden clasificar de varias formas. Por ejemplo, algunos son empleados y tienen un estado permanente. Algunos son proveedores, contratistas o asociados que tienen un estado temporal. Algunos son usuarios externos que no tienen cuentas de usuario, pero tienen que seguir concedido el acceso a servicios y recursos específicos para admitir la interacción y la colaboración. Por ejemplo:

- Cuentas de espacio empresarial que representan a usuarios de su organización a los que asigna una licencia para servicios en la nube

- Las cuentas de empresa a empresa (B2B) representan a los usuarios externos a la organización que invita a participar en la colaboración a los tipos de usuarios de la organización. ¿Cuáles son las agrupaciones? Por ejemplo, puede agrupar a los usuarios por una función o un propósito de alto nivel para su organización.

Además, algunos servicios en la nube se pueden compartir con usuarios externos a la organización sin cuentas de usuario. También necesitará identificar estos grupos de usuarios.

Puede usar grupos en Azure AD para varios fines que simplifican la administración del entorno de la nube. Por ejemplo, con los grupos de Azure AD, puede:

- Use licencias basadas en grupos para asignar licencias de Office 365 a sus cuentas de usuario automáticamente en cuanto se agreguen.
- Agregar cuentas de usuario a grupos específicos dinámicamente basándose en los atributos de cuenta de usuario, como el departamento.
- Aprovisionar automáticamente usuarios para aplicaciones de software como servicio (SaaS) y proteger el acceso a esas aplicaciones con autenticación multifactor y otras reglas de acceso condicional.
- Aprovisionar permisos y niveles de acceso para los sitios de grupo de SharePoint Online.

Puede crear nuevos ***usuarios*** con:

- [Centro de administración de Microsoft 365](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

Puede crear ***grupos*** nuevos con:

- [Centro de administración de Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a>Paso siguiente para identidades solo en la nube

[Asignar licencias a cuentas de usuario](assign-licenses-to-user-accounts.md)
