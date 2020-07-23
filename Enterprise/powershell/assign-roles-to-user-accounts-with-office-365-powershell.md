---
title: Asignar roles a cuentas de usuario de Microsoft 365 con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Resumen: Use PowerShell para Microsoft 365 para asignar roles a cuentas de usuario.'
ms.openlocfilehash: 2be491692c23b1f528612cc5c56e041553f80c48
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230876"
---
# <a name="assign-roles-to-microsoft-365-user-accounts-with-powershell"></a>Asignar roles a cuentas de usuario de Microsoft 365 con PowerShell

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Puede asignar roles a cuentas de usuario de forma rápida y sencilla mediante PowerShell para Microsoft 365.

>[!Note]
>Para asignar roles a cuentas de usuario con el centro de administración de Microsoft 365, consulte [estas instrucciones](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles).
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) con una cuenta de administrador global.
  
A continuación, determine el nombre de inicio de sesión de la cuenta de usuario que desea agregar a un rol (ejemplo: fredsm@contoso.com). Esto también se conoce como el nombre principal de usuario (UPN).

A continuación, determine el nombre de la función. Use esta [lista de permisos de roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).

>[!Note]
>Preste atención a las notas de este artículo. Algunos nombres de rol son diferentes para Azure AD PowerShell. Por ejemplo, el rol "Administrador de SharePoint" en el centro de administración de Microsoft 365 se denomina "administrador del servicio de SharePoint" para Azure AD PowerShell.
>

A continuación, rellene los nombres de rol y de inicio de sesión y ejecute estos comandos.
  
```powershell
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

A continuación, se muestra un ejemplo de un conjunto de comandos completado que asigna el rol de administrador de servicios de SharePoint a la cuenta belindan@contoso.com:
  
```powershell
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

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con una cuenta de administrador global.
  
### <a name="for-a-single-role-change"></a>Para un cambio de función único

Las formas más comunes de una cuenta de usuario específica es con su nombre para mostrar o su nombre de correo electrónico, también conocido como nombre de inicio de sesión o nombre principal de usuario (UPN).

#### <a name="display-names-of-user-accounts"></a>Mostrar los nombres de las cuentas de usuario

Si se usa para trabajar con los nombres para mostrar de las cuentas de usuario, determine lo siguiente:
  
- La cuenta de usuario que desea configurar.
    
    Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista completa de cuentas, use este comando:
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenados por nombre para mostrar, de una en una pantalla cada vez. Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** . Aquí le mostramos un ejemplo:

   >[!Note]
   >PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".
    
- El rol que desea asignar.
    
    Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Una vez que haya determinado el nombre para mostrar de la cuenta y el nombre de la función, use estos comandos para asignar el rol a la cuenta:
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Copie los comandos y péguelos en el Bloc de notas. Para las variables **$dispName** y **$roleName** , reemplace el texto de la descripción con sus valores, quite los \< and > caracteres y deje las comillas. Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas. Como alternativa, puede usar el entorno de script integrado (ISE) de Windows PowerShell.
  
A continuación, se muestra un ejemplo de un conjunto de comandos completado:
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a>Nombres de inicio de sesión de cuentas de usuario

Si se usa para trabajar con los nombres de inicio de sesión o UPN de las cuentas de usuario, determine lo siguiente:
  
- El UPN de la cuenta de usuario.
    
    Si aún no conoce el UPN, use este comando:
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Este comando enumera el UPN de las cuentas de usuario, ordenados por el UPN, de una en una pantalla a la vez. Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** . Aquí le mostramos un ejemplo:
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".
    
- El rol que desea asignar.
    
    Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Una vez que tenga el UPN de la cuenta y el nombre del rol, use estos comandos para asignar el rol a la cuenta:
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

Copie los comandos y péguelos en el Bloc de notas. Para las variables **$upnName** y **$roleName** , reemplace el texto de la descripción con sus valores, quite los \< and > caracteres y deje las comillas. Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas. Como alternativa, puede usar Windows PowerShell ISE.
  
A continuación, se muestra un ejemplo de un conjunto de comandos completado:
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a>Varios cambios de funciones

Para varios cambios de funciones, determine lo siguiente:
  
- Qué cuentas de usuario desea configurar. Puede usar los métodos de la sección anterior para recopilar el conjunto de nombres para mostrar o UPN.
    
- Qué roles desea asignar a cada cuenta de usuario.
    
    Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

A continuación, cree un archivo de texto de valores separados por comas (CSV) que tenga los campos nombre para mostrar o nombre de rol y UPN. Puede hacerlo fácilmente con Microsoft Excel.

Este es un ejemplo de nombres para mostrar:
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

Este es un ejemplo para los UPN:
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Consulte también

- [Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Administrar Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
- [Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)
