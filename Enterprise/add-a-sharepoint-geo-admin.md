---
title: Agregar o quitar un administrador de geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtenga información sobre cómo agregar o quitar un administrador ubican en OneDrive para profesionales Multi-ubican.
ms.openlocfilehash: 7630597654df9ad78619b94fedc9e18d5b0b721e
ms.sourcegitcommit: 886b23f590f6187f7a98c1083a3b49359ec2a5c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Agregar o quitar un administrador ubican en OneDrive para Busniess Multi-Geo

Puede configurar administradores independientes para cada ubicación geográfica que tienen en el inquilino de. Estos administradores tendrán acceso a la configuración de SharePoint Online y OneDrive que son específicos de su ubicación geográfica.

Algunos servicios - como el almacén de términos - se administran desde la ubicación central y se replican en ubicaciones de satélite. El Administrador de geo para la ubicación central tiene acceso a estas, mientras que los administradores geo para las ubicaciones de satélite no.

Los administradores globales y los administradores de SharePoint Online sigan teniendo acceso a la configuración en todas las ubicaciones de geo.

## <a name="configuring-geo-administrators"></a>Configuración de los administradores de geo

Configurar administradores ubican requiere el módulo de PowerShell en SharePoint Online.

Utilizar [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectar con el centro de administración de la ubicación geográfica donde desea agregar el administrador ubican. (Por ejemplo, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Para ver los administradores ubican existente de una ubicación, ejecute`Get-SPOGeoAdministrator`

### <a name="adding-a-user-as-a-geo-admin"></a>Adición de un usuario como un administrador de geo

Para agregar un usuario como un administrador de geo, ejecute`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Para quitar un usuario como un administrador de Geo de una ubicación, ejecute`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

### <a name="adding-a-group-as-a-geo-admin"></a>Adición de un grupo como un administrador de geo

Puede agregar un grupo de seguridad o un grupo de seguridad habilitados para correo como un administrador ubican. (No se admiten grupos de distribución y grupos de Office 365.)

Para agregar un grupo como un administrador de geo, ejecute`Add-SPOGeoAdministrator -GroupAlias <alias>`

Para quitar un grupo como un administrador de geo, ejecute`Remove-SPOGeoAdministrator -GroupAlias <alias>`

Tenga en cuenta que no todos los grupos de seguridad tienen un alias de grupo. Si desea agregar un grupo de seguridad que no tiene un alias, ejecute [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) para recuperar una lista de grupos, busque ObjectID de su grupo de seguridad y, a continuación, ejecute:

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

Para quitar un grupo mediante el uso de ObjectID, ejecute`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`

## <a name="see-also"></a>Consulte también

[SPOGeoAdministrator agregar](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Remove-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[Establecer un alias (MailNickName) para un grupo de seguridad](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)