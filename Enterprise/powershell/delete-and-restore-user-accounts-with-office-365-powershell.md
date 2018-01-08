---
title: Eliminar y restaurar cuentas de usuario con PowerShell de Office 365
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
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: "Obtenga información sobre cómo usar PowerShell de Office 365 para eliminar y restaurar cuentas de usuario de Office 365."
ms.openlocfilehash: 8404395ea9594cea1a2e772cecbeb011756b7754
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="delete-and-restore-user-accounts-with-office-365-powershell"></a>Eliminar y restaurar cuentas de usuario con PowerShell de Office 365

**Resumen:** obtenga información sobre cómo usar PowerShell de Office 365 para eliminar y restaurar cuentas de usuario de Office 365.
  
Al utilizar PowerShell de Office 365 para eliminar una cuenta de usuario, esta no se elimina de forma permanente. Puede restaurar la cuenta de usuario eliminada durante los siguientes 30 días.
  
## <a name="before-you-begin"></a>Antes de empezar

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.
    
## <a name="use-office-365-powershell-to-block-access-to-individual-user-accounts"></a>Usar PowerShell de Office 365 para bloquear el acceso a cuentas de usuario individuales
<a name="ShortVersion"> </a>

Para eliminar una cuenta de usuario, utilice la siguiente sintaxis:
  
```
Remove-MsolUser -UserPrincipalName <Account>
```

Este ejemplo elimina la cuenta de usuario BelindaN@litwareinc.com.
  
```
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

Para restaurar una cuenta de usuario eliminada dentro del periodo de gracia de 30 días, utilice la sintaxis siguiente:
  
```
Restore-MsolUser -UserPrincipalName <Account>
```

Este ejemplo restaura la cuenta eliminada BelindaN@litwareinc.com.
  
```
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 **Notas**:
  
- Para ver la lista de usuarios eliminados que pueden restaurarse, ejecute el siguiente comando:
    
  ```
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- Si otra cuenta usa el nombre principal de usuario original de la cuenta de usuario, use el parámetro  _NewUserPrincipalName_ en vez de _UserPrincipalName_ para especificar un nombre principal de usuario al restaurar la cuenta de usuario.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-remove-a-user-account"></a>Usar el módulo de PowerShell Azure Active Directory V2 para eliminar una cuenta de usuario.
<a name="ShortVersion"> </a>

Para usar el cmdlet **Remove-AzureADUser** desde el módulo de PowerShell Azure Active Directory V2, primero tiene que conectarse a la suscripción. Para obtener instrucciones, vea [Conectarse con el módulo de PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Después de haberse conectado, use la sintaxis siguiente para eliminar una cuenta de usuario individual:
  
```
Remove-AzureADUser -ObjectID <Account>
```

Este ejemplo elimina la cuenta de usuario fabricec@litwareinc.com.
  
```
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> El parámetro **ObjectID** en el cmdlet **Remove-AzureAD** acepta tanto el nombre de cuenta, también conocido como nombre principal de usuario, o la ID de objeto de la cuenta.
  
Para mostrar el nombre de cuenta según el nombre de usuario, use los comandos siguientes:
  
```
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Este ejemplo muestra el nombre de cuenta para el usuario llamado Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Para eliminar una cuenta según el nombre de usuario, use los comandos siguientes:
  
```
$userName="<User name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="see-also"></a>Consulte también
<a name="SeeAlso"> </a>

Vea estos temas adicionales sobre cómo administrar usuarios con PowerShell de Office 365:
  
- [Crear cuentas de usuario con PowerShell de Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Bloquear cuentas de usuario con PowerShell de Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Asignar licencias a cuentas de usuario con PowerShell de Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Eliminar licencias de cuentas de usuario con PowerShell de Office 365](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Remove-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691636)
    
- [Restore-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691637)
    
- [New-AzureADUsuario](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

