---
title: Ver los usuarios con licencia y sin licencia con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Se explica cómo usar PowerShell de Office 365 para ver las cuentas de usuario con licencia y sin licencia.
ms.openlocfilehash: 0648fae89a45b080bd48561bb079184f0e97dd36
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546511"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Ver los usuarios con licencia y sin licencia con PowerShell de Office 365

**Resumen:** se explica cómo usar PowerShell de Office 365 para ver las cuentas de usuario con licencia y sin licencia.
  
Las cuentas de usuario de la organización de Office 365 pueden tener algunas, todas o ninguna de las licencias disponibles asignadas a ellas desde los planes de licencias que están disponibles en su organización. Puede usar PowerShell de Office 365 para encontrar rápidamente los usuarios con licencia y sin licencia de la organización.


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usar Azure Active Directory PowerShell para el módulo de gráfico

Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
Para ver la lista de todas las cuentas de usuario de la organización que no se han asignado cualquiera de los planes de licencias (usuarios sin licencia), ejecute el siguiente comando:
  
```
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

Para ver la lista de todas las cuentas de usuario de la organización que han sido asignados cualquiera de los planes de licencias (usuarios con licencia), ejecute el siguiente comando:
  
```
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $user.AssignedLicenses[$i].disabledplans ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} } }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usar el módulo de Microsoft Azure Active Directory para Windows PowerShell

Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Para ver la lista de todas las cuentas de usuario y su estado de licencias en la organización, ejecute el comando siguiente en PowerShell de Office 365:
  
```
Get-MsolUser -All
```

Para ver la lista de todas las cuentas de usuario sin licencia de su organización, ejecute el comando siguiente:
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Para ver la lista de todas las cuentas de usuario con licencia de su organización, ejecute el comando siguiente:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a>Vea también

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
