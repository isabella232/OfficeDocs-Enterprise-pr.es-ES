---
title: Bloquear cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/10/2018
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
ms.openlocfilehash: 748d24f95f9dca651158dae2fe15e9c655eb021e
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915415"
---
# <a name="block-user-accounts-with-office-365-powershell"></a>Bloquear cuentas de usuario con PowerShell de Office 365

**Resumen:**  Se explica cómo usar PowerShell de Office 365 para bloquear y desbloquear el acceso a cuentas de Office 365.
  
Bloquear el acceso a una cuenta de Office 365 impide que alguien pueda usar la cuenta para iniciar sesión y tener acceso a los servicios y los datos de la organización de Office 365. Cuando se bloquea el acceso a la cuenta, el usuario recibe el siguiente mensaje de error cuando intenten iniciar sesión en:
  
![Cuenta de Office 365 bloqueada.](media/o365-powershell-account-blocked.png)
  
Puede usar PowerShell de Office 365 para bloquear el acceso a una persona y varias cuentas de usuario.
  
## <a name="before-you-begin"></a>Antes de empezar

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Cuando se bloquea una cuenta de usuario, puede tardar hasta 24 horas para que surtan efecto en los clientes y dispositivos de todos los usuarios.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Usar PowerShell de Office 365 para bloquear el acceso a cuentas de usuario individuales

Utilice la sintaxis siguiente para bloquear el acceso a una cuenta de usuario individual:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $true
```

Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

Para desbloquear la cuenta de usuario, ejecute el siguiente comando:
  
```
Set-MsolUser -UserPrincipalName <UPN of user account>  -BlockCredential $false
```

En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="use-office-365-powershell-to-block-access-to-multiple-user-accounts"></a>Usar PowerShell de Office 365 para bloquear el acceso a varias cuentas de usuario

En primer lugar, cree un archivo de texto que contiene una cuenta en cada línea como la siguiente:
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
En los siguientes comandos, el archivo de texto de ejemplo es C:\My Documents\Accounts.txt. Reemplazar por la ruta de acceso y el nombre de su archivo de texto.
    
Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:
    
  ```
  Get-Content Accounts.txt | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-block-access-to-user-accounts"></a>Usar el módulo de PowerShell Azure Active Directory V2 para bloquear el acceso a cuentas de usuario

Para usar el cmdlet **New-AzureADUser** desde el módulo de PowerShell Azure Active Directory V2 debe conectarse primero a la suscripción. Para las instrucciones, consulte[Conectarse con el módulo de PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Después de haberse conectado, use la sintaxis siguiente para bloquear una cuenta de usuario individual:
  
```
Set-AzureADUser -ObjectID <UPN of user account> -AccountEnabled $false
```

> [!NOTE]
> El parámetro ObjectID en el cmdlet Set-AzureAD acepta tanto el nombre de cuenta, también conocido como nombre principal de usuario, o la ID de objeto de la cuenta. 
  
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
$userName="<user account display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

En este ejemplo se muestra la cuenta de usuario UPN para el usuario llamado Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Para bloquear una cuenta según el nombre de usuario, use los comandos siguientes:
  
```
$userName="<user account display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

Para bloquear el acceso a varias cuentas de usuario, cree un archivo de texto que contiene un nombre de cuenta en cada línea como la siguiente:
    
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

## <a name="see-also"></a>Consulte también

Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:
  
- [Crear cuentas de usuario con PowerShell de Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Asignar licencias a cuentas de usuario con PowerShell de Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Eliminar licencias de cuentas de usuario con PowerShell de Office 365](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=113310)
    
- [Set-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691644)
    
- [New-AzureADUsuario](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

