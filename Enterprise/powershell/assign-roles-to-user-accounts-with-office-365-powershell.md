---
title: Asignar roles a cuentas de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- DecEntMigration
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Resumen: Utilice Office 365 PowerShell y el cmdlet Add-MsolRoleMember para asignar roles a cuentas de usuario.'
ms.openlocfilehash: 673a71fb2f85515276e94767ed3f9dd40655dfea
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a>Asignar roles a cuentas de usuario con Office 365 PowerShell

 **Resumen:** Utilice Office 365 PowerShell y el cmdlet **Add-MsolRoleMember** para asignar roles a cuentas de usuario.
  
Puede asignar la funciones de forma rápida y sencilla a cuentas de usuario mediante Office 365 PowerShell identificando el nombre para mostrar de la cuenta de usuario y el nombre del rol.
  
## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos de este tema requieren conectarse a Office 365 PowerShell utilizando una cuenta de administrador global. Para obtener instrucciones, vea [conectarse a Office 365 PowerShell](connect-to-office-365-powershell.md).
  
## <a name="for-a-single-role-change"></a>Para un cambio de función única

Determine lo siguiente:
  
- La cuenta de usuario que desea configurar.
    
    Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista completa de cuentas, use este comando:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenadas por el nombre para mostrar, una pantalla a la vez. Mediante el cmdlet **donde** puede filtrar la lista a un conjunto más pequeño. Éste es un ejemplo:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra sólo las cuentas de usuario para el que el nombre para mostrar empieza con "Juan".
    
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

Los comandos de copiar y pegarlos en el Bloc de notas. Para las variables **$dispName** y **$roleName** , reemplace el texto de la descripción con sus valores, quite el \< y > caracteres y dejar las comillas. Copie las líneas modificadas y pegarlos en la ventana de Windows Azure Active Directory módulo para Windows PowerShell para ejecutarlas. Como alternativa, puede utilizar el entorno integrado de secuencias de comandos de Windows PowerShell (ISE).
  
Aquí es un ejemplo de un conjunto de comandos completa:
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a>Varios cambios de función

Determine lo siguiente:
  
- Qué cuentas de usuario que desea configurar.
    
    Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista de cuentas, use este comando:
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra el nombre para mostrar de todas las cuentas de usuario, ordenadas por el nombre para mostrar, una pantalla a la vez. Mediante el cmdlet **donde** puede filtrar la lista a un conjunto más pequeño. Éste es un ejemplo:
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    Este comando muestra sólo las cuentas de usuario para el que el nombre para mostrar empieza con "Juan".
    
- Los roles que desea asignar a cada cuenta de usuario.
    
    Para mostrar la lista de roles disponibles que se pueden asignar a cuentas de usuario, use este comando:
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

A continuación, cree un archivo de texto de valores separados por comas (CSV) que contiene el DisplayName y la función de nombres de los campos. Éste es un ejemplo:
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

A continuación, especifique la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a>See also

#### 

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
#### 

[MsolRoleMember agregar](https://msdn.microsoft.com/library/dn194120.aspx)

