---
title: Agregar o quitar un administrador geográfico
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords:
- NOCSH
description: Obtenga más información sobre cómo agregar o quitar un administrador geográfico de Microsoft 365 Multi-Geo.
ms.openlocfilehash: 13b730de6b318ddb3a4cf3a084d4b59e56a82dbf
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433611"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a>Agregar o quitar un administrador geográfico de Microsoft 365 Multi-Geo

Puede configurar administradores independientes para cada ubicación geográfica de su espacio empresarial. Estos administradores tendrán acceso a la configuración de SharePoint Online y OneDrive específica de su ubicación geográfica.

Algunos servicios, como el almacén de términos, se administran desde la ubicación central y se replican en ubicaciones satélites. El administrador geográfico de la ubicación central tiene acceso a dichos servicios, pero los administradores geográficos de ubicaciones satélites no.

Los administradores globales y administradores de SharePoint Online seguirán teniendo acceso a la configuración de la ubicación central y todas las ubicaciones satélites.

## <a name="configuring-geo-administrators"></a>Configurar los administradores geográficos

Para configurar los administradores geográficos se requiere el módulo de PowerShell de SharePoint Online.

Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectarse al centro de administración de la ubicación geográfica donde quiera agregar el administrador geográfico. (Por ejemplo, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)

Para ver los administradores geográficos existentes de una ubicación, ejecute `Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Agregar un usuario como administrador geográfico

Para agregar un usuario como administrador geográfico, ejecute `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Para quitar un usuario como administrador geográfico de una ubicación, ejecute  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Agregar un grupo como administrador geográfico

Puede agregar un grupo de seguridad o un grupo de seguridad habilitado para correo como administrador geográfico. (No se admiten los grupos de distribución y Grupos de Microsoft 365).

Para agregar un grupo como administrador geográfico, ejecute `Add-SPOGeoAdministrator -GroupAlias <alias>`

Para quitar un grupo como administrador geográfico, ejecute `Remove-SPOGeoAdministrator -GroupAlias <alias>`

Tenga en cuenta que no todos los grupos de seguridad tienen un alias de grupo. Si quiere agregar un grupo de seguridad que no tiene un alias, ejecute [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) para recuperar una lista de grupos, busque el ObjectID del grupo seguridad y ejecute lo siguiente:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Para quitar un grupo mediante ObjectID, ejecute `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>Vea también

[Add-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Establecer un alias (MailNickName) de un grupo de seguridad](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)