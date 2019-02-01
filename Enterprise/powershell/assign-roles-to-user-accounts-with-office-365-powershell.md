---
title: Asignar roles a cuentas de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Resumen: Use PowerShell de Office 365 para asignar roles a cuentas de usuario.'
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690441"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Asignar roles a cuentas de usuario con Office 365 PowerShell

Puede asignar rápida y fácilmente la roles a cuentas de usuario con PowerShell de Office 365.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Primero, [conectarse a su inquilino Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) utilizando una cuenta de administrador global.
  
A continuación, determine el nombre de inicio de sesión de la cuenta de usuario que desea agregar a una función (ejemplo: fredsm@contoso.com). Esto es también conocido como el nombre principal de usuario (UPN).

A continuación, determine el nombre de la función. Use este comando para obtener una lista de las funciones que se pueden asignar con PowerShell.

````
Get-AzureADDirectoryRole
````

A continuación, rellene los nombres de inicio de sesión y la función y ejecute estos comandos.
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Este es un ejemplo de un conjunto de comandos completado:
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

Para mostrar la lista de nombres de usuario para un rol específico, use estos comandos.

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conectarse a su inquilino Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) utilizando una cuenta de administrador global.
  
### <a name="for-a-single-role-change"></a>Para un cambio de función única

Determine lo siguiente:
  
- La cuenta de usuario que desea configurar.
    
    Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista completa de las cuentas, use este comando:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenadas por el nombre para mostrar, una pantalla a la vez. Puede filtrar la lista a un conjunto más pequeño mediante el cmdlet **donde** . Este es un ejemplo:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Este comando enumera sólo las cuentas de usuario para el que el nombre para mostrar comienza por "John".
    
- La función que desea asignar.
    
    Para mostrar la lista de roles disponibles que se pueden asignar a cuentas de usuario, use este comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

Una vez que haya determinado el nombre para mostrar de la cuenta y el nombre de la función, utilice estos comandos para asignar el rol a la cuenta:
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

Copie los comandos y péguelos en el Bloc de notas. Para las variables **$dispName** y **$roleName** , reemplace el texto de descripción con sus valores, quite el \< y > caracteres y deje las comillas. Copie las líneas modificadas y péguelas en la ventana de Windows Azure Active Directory módulo para Windows PowerShell para ejecutarlas. Como alternativa, puede utilizar el entorno integrado de secuencia de comandos de Windows PowerShell (ISE).
  
Este es un ejemplo de un conjunto de comandos completado:
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a>Para varios cambios de rol

Determine lo siguiente:
  
- Qué cuentas de usuario que desea configurar.
    
    Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista de cuentas, use este comando:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra el nombre para mostrar de todas las cuentas de usuario, ordenadas por el nombre para mostrar, una pantalla a la vez. Puede filtrar la lista a un conjunto más pequeño mediante el cmdlet **donde** . Este es un ejemplo:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Este comando enumera sólo las cuentas de usuario para el que el nombre para mostrar comienza por "John".
    
- Los roles que desea asignar a cada cuenta de usuario.
    
    Para mostrar la lista de roles disponibles que se pueden asignar a cuentas de usuario, use este comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

A continuación, cree un archivo de texto de valores separados por comas (CSV) que tiene el DisplayName y la función de nombres de los campos. Este es un ejemplo:
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>Vea también

- [Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
- [Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
