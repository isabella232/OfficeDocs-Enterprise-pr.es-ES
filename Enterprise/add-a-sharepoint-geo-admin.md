---
title: Agregar o quitar un administrador de geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Aprenda a agregar o quitar un administrador geo en OneDrive para el negocio Multi-Geo.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a>Agregar o quitar un administrador geo en OneDrive de Busniess Multi-Geo

Puede configurar administradores independientes para cada ubicación geográfica que tiene en su arrendatario. Estos administradores tendrán acceso a la configuración de SharePoint Online y OneDrive son específicos de su ubicación geográfica.

Algunos servicios - como el almacén de términos - se administran desde la ubicación central y se replican en ubicaciones de satélite. El admin geo para la ubicación central tiene acceso a estos, mientras que los no administradores geo para ubicaciones de satélite.

Los administradores globales y los administradores de SharePoint Online sigan teniendo acceso a la configuración en todas las ubicaciones de geo.

## <a name="configuring-geo-administrators"></a>Configurar administradores de geo

Configurar administradores de geo requiere el módulo de PowerShell de SharePoint Online.

Utilizar [SPOService de conectar](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectarse al centro de administración de la ubicación geográfica donde desee agregar el administrador geo. (Por ejemplo, conectar SPOServicehttps://ContosoEUR-admin.sharepoint.com.)

Para agregar un usuario como un administrador de geo, ejecutar`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`

Para ver los administradores geo existente de una ubicación, ejecutar`Get-SPOGeoAdministrators`

Para quitar un usuario como administradores de una ubicación geográfica, ejecute`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`

## <a name="see-also"></a>Consulte también

[SPOGeoAdministrator agregar](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[Get-SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[Quitar SPOGeoAdministrator](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)