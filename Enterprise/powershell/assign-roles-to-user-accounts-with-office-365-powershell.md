---
title: Asignar roles a cuentas de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/30/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Resumen: Use Office 365 PowerShell para asignar roles a cuentas de usuario.'
ms.openlocfilehash: d06b305c348d014ce526448d7f8401c26f4d1c47
ms.sourcegitcommit: 3100813cd7dff8b27b1a30a6d6ed5a7c4765c60f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "34586986"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Asignar roles a cuentas de usuario con Office 365 PowerShell

Puede asignar roles a cuentas de usuario de forma rápida y sencilla mediante Office 365 PowerShell.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

En primer lugar, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) con una cuenta de administrador global.
  
A continuación, determine el nombre de inicio de sesión de la cuenta de usuario que desea agregar a un rol (ejemplo: fredsm@contoso.com). Esto también se conoce como el nombre principal de usuario (UPN).

A continuación, determine el nombre de la función. Use esta [lista de permisos de roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).

>[!Note]
>Preste atención a las notas de este artículo. Algunos nombres de rol son diferentes para Azure AD PowerShell. Por ejemplo, el rol "Administrador de SharePoint" en el centro de administración de Microsoft 365 se denomina "administrador del servicio de SharePoint" para Azure AD PowerShell.
>

A continuación, rellene los nombres de rol y de inicio de sesión y ejecute estos comandos.
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

A continuación, se muestra un ejemplo de un conjunto de comandos completado:
  
```
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Para mostrar la lista de nombres de usuario para una función específica, use estos comandos.

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

En primer lugar, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con una cuenta de administrador global.
  
### <a name="for-a-single-role-change"></a>Para un cambio de función único

Las formas más comunes de tener una cuenta de usuario específica son con su nombre para mostrar o su nombre de correo electrónico, también conocido como nombre principal de usuario (UPN) de nombre de inicio de sesión.

#### <a name="display-names-of-user-accounts"></a>Mostrar los nombres de las cuentas de usuario

Si se usa para trabajar con los nombres para mostrar de las cuentas de usuario, determine lo siguiente:
  
- La cuenta de usuario que desea configurar.
    
    Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista completa de cuentas, use este comando:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenados por nombre para mostrar, de una en una pantalla cada vez. Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** . Aquí le mostramos un ejemplo:
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".
    
- El rol que desea asignar.
    
    Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Una vez que haya determinado el nombre para mostrar de la cuenta y el nombre de la función, use estos comandos para asignar el rol a la cuenta:
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Copie los comandos y péguelos en el Bloc de notas. Para las variables **$dispName** y **$roleName** , reemplace el texto de la descripción con sus valores, \< Quite los caracteres y > y deje las comillas. Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas. Como alternativa, puede usar el entorno de script integrado (ISE) de Windows PowerShell.
  
A continuación, se muestra un ejemplo de un conjunto de comandos completado:
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Nombres de inicio de sesión de cuentas de usuario

Si se usa para trabajar con los nombres de inicio de sesión o UPN de las cuentas de usuario, determine lo siguiente:
  
- El UPN de la cuenta de usuario.
    
    Si aún no conoce el UPN, use este comando:
    
  ```
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Este comando enumera el UPN de las cuentas de usuario, ordenados por el UPN, de una en una pantalla a la vez. Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** . Aquí le mostramos un ejemplo:
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".
    
- El rol que desea asignar.
    
    Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Una vez que tenga el UPN de la cuenta y el nombre del rol, use estos comandos para asignar el rol a la cuenta:
  
```
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Copie los comandos y péguelos en el Bloc de notas. Para las variables **$upnName** y **$roleName** , reemplace el texto de la descripción con sus valores, \< Quite los caracteres y > y deje las comillas. Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas. Como alternativa, puede usar Windows PowerShell ISE.
  
A continuación, se muestra un ejemplo de un conjunto de comandos completado:
  
```
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a>Para varios cambios de funciones

Determine lo siguiente:
  
- Qué cuentas de usuario desea configurar. Puede usar los métodos de la sección anterior para recopilar el conjunto de nombres para mostrar o UPN.
    
- Qué roles desea asignar a cada cuenta de usuario.
    
    Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

A continuación, cree un archivo de texto de valores separados por comas (CSV) que tenga los campos nombre para mostrar o nombre de rol y UPN. Puede hacerlo fácilmente con Microsoft Excel.

Este es un ejemplo de nombres para mostrar:
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

Este es un ejemplo para los UPN:
  
```
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```


## <a name="see-also"></a>Vea también

- [Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
- [Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
