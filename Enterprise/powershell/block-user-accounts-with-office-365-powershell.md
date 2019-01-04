---
title: Bloquear cuentas de usuario con PowerShell de Office 365
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Se explica cómo usar PowerShell de Office 365 para bloquear y desbloquear el acceso a cuentas de Office 365.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546481"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloquear cuentas de usuario con PowerShell de Office 365

**Resumen:**  Se explica cómo usar PowerShell de Office 365 para bloquear y desbloquear el acceso a cuentas de Office 365.
  
Bloquear el acceso a una cuenta de Office 365 impide que alguien pueda usar la cuenta para iniciar sesión y tener acceso a los servicios y los datos de la organización de Office 365. Puede usar PowerShell de Office 365 para bloquear el acceso a una persona y varias cuentas de usuario.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usar Azure Active Directory PowerShell para el módulo de gráfico

Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Bloquear el acceso a las cuentas de usuario individuales

Para bloquear una cuenta de usuario individual, use la siguiente sintaxis:
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> El parámetro - ObjectID en el cmdlet Set-AzureAD acepta puede ser el inicio de sesión de nombre de cuenta, también conocida como el nombre Principal de usuario o identificador de objeto. de la cuenta 
  
Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Para desbloquear esta cuenta de usuario, ejecute el siguiente comando:
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Para mostrar la cuenta de usuario que UPN basado en nombre para mostrar del usuario, use los siguientes comandos:
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

En este ejemplo se muestra la cuenta de usuario UPN para el usuario llamado Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Para bloquear una cuenta basada en el nombre para mostrar del usuario, use los siguientes comandos:
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquear el acceso a varias cuentas de usuario

Para bloquear el acceso a varias cuentas de usuario, cree un archivo de texto que contiene un inicio de sesión de nombre de cuenta en cada línea como la siguiente:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

En los siguientes comandos, el archivo de texto de ejemplo es C:\My Documents\Accounts.txt. Reemplazar por la ruta de acceso y el nombre de su archivo de texto.
  
Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usar el módulo de Microsoft Azure Active Directory para Windows PowerShell

Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

    
### <a name="block-access-to-individual-user-accounts"></a>Bloquear el acceso a las cuentas de usuario individuales

Utilice la sintaxis siguiente para bloquear el acceso a una cuenta de usuario individual:
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Para desbloquear la cuenta de usuario, ejecute el siguiente comando:
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquear el acceso a varias cuentas de usuario

En primer lugar, cree un archivo de texto que contiene una cuenta en cada línea como la siguiente:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
En los siguientes comandos, el archivo de texto de ejemplo es C:\My Documents\Accounts.txt. Reemplazar por la ruta de acceso y el nombre de su archivo de texto.
    
Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Consulte también

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
