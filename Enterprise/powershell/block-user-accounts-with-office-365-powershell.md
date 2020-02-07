---
title: Bloquear cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Explica cómo usar Office 365 PowerShell para bloquear y desbloquear el acceso a cuentas de Office 365.
ms.openlocfilehash: 18c7cea2df2514d7402dfcfd894acc03ed69b1c9
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841697"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloquear cuentas de usuario con PowerShell de Office 365

Al bloquear el acceso a una cuenta de Office 365, cualquier usuario que no pueda usar la cuenta puede iniciar sesión y acceder a los servicios y datos de su organización de Office 365. Puede usar Office 365 PowerShell para bloquear el acceso a cuentas de usuario individuales y múltiples.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
 
### <a name="block-access-to-individual-user-accounts"></a>Bloquear el acceso a cuentas de usuario individuales

Use la siguiente sintaxis para bloquear una cuenta de usuario individual:
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> El parámetro-ObjectID en el cmdlet Set-AzureAD acepta el nombre de inicio de sesión de la cuenta, también conocido como nombre principal de usuario, o el identificador de objeto de la cuenta. 
  
Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

Para desbloquear esta cuenta de usuario, ejecute el siguiente comando:
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

Para mostrar el UPN de la cuenta de usuario en función del nombre para mostrar del usuario, use los comandos siguientes:
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

En este ejemplo se muestra el UPN de la cuenta de usuario para el usuario denominado Caleb alféizares.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Para bloquear una cuenta según el nombre para mostrar del usuario, use los comandos siguientes:
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquear el acceso a varias cuentas de usuario

Para bloquear el acceso a varias cuentas de usuario, cree un archivo de texto que contenga un nombre de inicio de sesión de la cuenta en cada línea de la siguiente manera:
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

En los siguientes comandos, el archivo de texto de ejemplo es C:\Mis Documentos\cuentas.txt. Reemplácelo por la ruta de acceso y el nombre de archivo del archivo de texto.
  
Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
### <a name="block-access-to-individual-user-accounts"></a>Bloquear el acceso a cuentas de usuario individuales

Utilice la sintaxis siguiente para bloquear el acceso a una cuenta de usuario individual:
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Para desbloquear la cuenta de usuario, ejecute el siguiente comando:
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a>Bloquear el acceso a varias cuentas de usuario

En primer lugar, cree un archivo de texto que contenga una cuenta en cada línea como esta:
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

En los siguientes comandos, el archivo de texto de ejemplo es C:\Mis Documentos\cuentas.txt. Reemplácelo por la ruta de acceso y el nombre de archivo del archivo de texto.
    
Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a>Consulte también

[Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
