---
title: Eliminar cuentas de usuario de Microsoft 365 con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
- seo-marvel-apr2020
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: En este artículo, obtenga información sobre cómo usar diferentes módulos en PowerShell para eliminar cuentas de usuario de Microsoft 365.
ms.openlocfilehash: d34201e2ef467ab4250ccde46a3d082b1b927d61
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605986"
---
# <a name="delete-microsoft-365-user-accounts-with-powershell"></a>Eliminar cuentas de usuario de Microsoft 365 con PowerShell

Puede usar PowerShell para Microsoft 365 para eliminar una cuenta de usuario.
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Después de haberse conectado, use la sintaxis siguiente para eliminar una cuenta de usuario individual:
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

Este ejemplo elimina la cuenta de usuario fabricec@litwareinc.com.
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> El parámetro **-objectId** en el cmdlet **Remove-AzureADUser** acepta tanto el nombre de inicio de sesión de la cuenta, también conocido como el nombre principal de usuario, o el identificador de objeto de la cuenta.
  
Para mostrar el nombre de cuenta según el nombre de usuario, use los comandos siguientes:
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Este ejemplo muestra el nombre de cuenta para el usuario llamado Caleb Sills.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Para eliminar una cuenta según el nombre para mostrar del usuario, use los comandos siguientes:
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Al eliminar una cuenta de usuario con el Módulo Microsoft Azure Active Directory para Windows PowerShell, esta no se elimina de forma permanente. Puede restaurar la cuenta de usuario eliminada durante los siguientes 30 días.

En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Para eliminar una cuenta de usuario, utilice la siguiente sintaxis:
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

Este ejemplo elimina la cuenta de usuario BelindaN@litwareinc.com.
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Para restaurar una cuenta de usuario eliminada dentro del periodo de gracia de 30 días, utilice la sintaxis siguiente:
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

Este ejemplo restaura la cuenta eliminada BelindaN@litwareinc.com.
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Notas:**
  
- Para ver la lista de usuarios eliminados que pueden restaurarse, ejecute el siguiente comando:
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Si otra cuenta usa el nombre principal de usuario original de la cuenta de usuario, use el parámetro _NewUserPrincipalName_ en vez de _UserPrincipalName_ para especificar un nombre principal de usuario al restaurar la cuenta de usuario.


## <a name="see-also"></a>Vea también

[Administrar cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)
