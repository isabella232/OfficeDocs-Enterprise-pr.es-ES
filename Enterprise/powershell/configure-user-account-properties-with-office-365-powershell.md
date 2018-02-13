---
title: Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: O365ITProTrain, Ent_Office_Other, PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumen: Uso Office 365 PowerShell para configurar las propiedades de la persona o a varias cuentas de usuario en los inquilinos de Office 365.'
ms.openlocfilehash: 65857511886534e18ba3e67b79ab4d74a0119568
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell

 **Resumen:** Utilice Office 365 PowerShell para configurar las propiedades de la persona o a varias cuentas de usuario en los inquilinos de Office 365.
  
Aunque puede utilizar el centro de administración de Office 365 para configurar las propiedades de las cuentas de usuario de los inquilinos de Office 365, también puede utilizar Office 365 PowerShell y hacer algunas cosas que no puede el centro de administración de Office 365.
  
## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
  
## <a name="change-properties-for-a-specific-user-account"></a>Cambiar las propiedades de una cuenta de usuario específica

Para configurar las propiedades de una cuenta de usuario específica, use el cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) y especificar las propiedades para establecer o cambiar. Este comando de ejemplo cambia la ubicación de uso de Belinda Newman en Francia:
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Identificar la cuenta con el parámetro **- UserPrincipalName** y establece o cambia las propiedades específicas con parámetros adicionales. Presentamos una lista de los parámetros más comunes.
  
- -Ciudad "\<nombre de la ciudad >"
    
- -País "\<nombre de país >"
    
- -Departamento "\<nombre de departamento >"
    
- DisplayName: "\<nombre completo del usuario >"
    
- -Fax "\<número de fax >"
    
- -FirstName "\<nombre usuario >"
    
- -Apellido "\<último nombre de usuario >"
    
- -Teléfono móvil "\<número de teléfono móvil >"
    
- -Office "\<ubicación de la oficina >"
    
- -El número de teléfono "\<número de teléfono de oficina >"
    
- -PostalCode "\<código postal >"
    
- -PreferredLanguage "\<idioma >"
    
- -Estado "\<nombre de estado >"
    
- -StreetAddress "\<dirección >"
    
- -Título "\<nombre del título >"
    
- -UsageLocation "\<código de país o región de 2 caracteres >"
    
    Esto es el país de dos letras ISO 3166-1 alpha-2 (A2) o el código de región.
    
Consulte [MsolUser del conjunto](https://msdn.microsoft.com/library/azure/dn194136.aspx) de parámetros adicionales.
  
Para ver los nombres principales de usuario de todos los usuarios, ejecute el siguiente comando.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Ordenar alfabéticamente la lista de nombres principales de usuario ( **UserPrincipalName de Sort-Object** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar sólo la propiedad de nombre Principal de usuario para cada cuenta ( **UserPrincipalName de Select-Object** ).
    
- Muestra una pantalla a la vez ( **más** ).
    
Este comando mostrará todas las cuentas. Si desea mostrar el nombre Principal de usuario de una cuenta basada en su presentación name (nombre y apellido), rellene la siguiente variable de **$userName** (quitando el \< y > caracteres), y, a continuación, ejecute los comandos siguientes:
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Este ejemplo muestra el nombre Principal de usuario para el usuario llamado Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Mediante el uso de una variable de **$upn** , puede realizar cambios en cuentas individuales basadas en su nombre para mostrar. Aquí es un ejemplo de establecer ubicación de uso de Belinda Newman en Francia, pero especifica su nombre para mostrar en lugar de su nombre Principal de usuario:
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a>Cambiar las propiedades de todas las cuentas de usuario

Para cambiar las propiedades de todos los usuarios, puede utilizar la combinación de los cmdlets **Get-MsolUser** y **MsolUser del conjunto** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios a Francia:
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Establecer la ubicación del usuario en Francia ( **"FR" Set-MsolUser-UsageLocation** ).
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Cambiar las propiedades de un conjunto específico de cuentas de usuario

Para cambiar las propiedades de un conjunto específico de la cuenta de usuario, puede utilizar la combinación de los cmdlets **Get-MsolUser**, **Where-Object**y **MsolUser del conjunto** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios del departamento de contabilidad a Francia:
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tengan su propiedad departamento sea "Contabilidad" ( **Where-Object {$_. Departamento - eq "Contabilidad"}** ) y enviar la información resultante con el siguiente comando ( **|** ).
    
- Establecer la ubicación del usuario en Francia ( **"FR" Set-MsolUser-UsageLocation** ).
    
- Muestra una pantalla a la vez ( **más** ).
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a>Utilice el módulo de Active Directory V2 PowerShell de Azure para configurar las propiedades de la cuenta de usuario

Para configurar las propiedades de cuentas de usuario con el módulo de Active Directory V2 PowerShell de Azure, use el cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) y especificar las propiedades para establecer o cambiar. Pero en primer lugar, debe conectarse a su suscripción. Para las instrucciones, vea [Conectar con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="change-properties-for-a-specific-user-account"></a>Cambiar las propiedades de una cuenta de usuario específica

Este comando de ejemplo cambia la ubicación de uso de Belinda Newman en Francia:
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

Identificar la cuenta con el parámetro **- ObjectID** y establece o cambia las propiedades específicas con parámetros adicionales. Presentamos una lista de los parámetros más comunes.
  
- -Departamento "\<nombre de departamento >"
    
- DisplayName: "\<nombre completo del usuario >"
    
- -FacsimilieTelephoneNumber "\<número de fax >"
    
- -GivenName "\<nombre usuario >"
    
- -El apellido "\<último nombre de usuario >"
    
- -Móvil "\<número de teléfono móvil >"
    
- -JobTitle "\<puesto >"
    
- -PreferredLanguage "\<idioma >"
    
- -StreetAddress "\<dirección >"
    
- -Ciudad "\<nombre de la ciudad >"
    
- -Estado "\<nombre de estado >"
    
- -PostalCode "\<código postal >"
    
- -País "\<nombre de país >"
    
- -TelephoneNumber "\<número de teléfono de oficina >"
    
- -UsageLocation "\<código de país o región de 2 caracteres >"
    
    Esto es el país de dos letras ISO 3166-1 alpha-2 (A2) o el código de región.
    
Consulte [AzureADUser del conjunto](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) de parámetros adicionales.
  
Para mostrar el nombre Principal de usuario para las cuentas de usuario, ejecute el siguiente comando.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Ordenar alfabéticamente la lista de nombres principales de usuario ( **UserPrincipalName de Sort-Object** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar sólo la propiedad de nombre Principal de usuario para cada cuenta ( **UserPrincipalName de Select-Object** ).
- Muestra una pantalla a la vez ( **más** ).
    
Este comando mostrará todas las cuentas. Si desea mostrar el nombre Principal de usuario de una cuenta basada en su presentación name (nombre y apellido), rellene la siguiente variable de **$userName** (quitando el \< y > caracteres), y, a continuación, ejecute los comandos siguientes:
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Este ejemplo muestra el nombre Principal de usuario para el usuario llamado Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Mediante el uso de una variable de **$upn** , puede realizar cambios en cuentas individuales basadas en su nombre para mostrar. Aquí es un ejemplo de establecer ubicación de uso de Belinda Newman en Francia, pero especifica su nombre para mostrar en lugar de su nombre Principal de usuario:
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Cambiar las propiedades de todas las cuentas de usuario

Para cambiar las propiedades de todos los usuarios, puede utilizar la combinación de los cmdlets **Get-AzureADUser** y **AzureADUser del conjunto** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios a Francia:
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Establecer la ubicación del usuario en Francia ( **"FR" Set-AzureADUser-UsageLocation** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Cambiar las propiedades de un conjunto específico de cuentas de usuario

Para cambiar las propiedades de un conjunto específico de la cuenta de usuario, puede utilizar la combinación de los cmdlets **Get-AzureADUser**, **donde**y **AzureADUser del conjunto** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios del departamento de contabilidad a Francia:
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen su propiedad departamento a "Accounting" ( **donde {$_. Departamento - eq "Contabilidad"}** ) y enviar la información resultante con el siguiente comando ( **|** ).
    
- Establecer la ubicación del usuario en Francia ( **"FR" Set-AzureADUser-UsageLocation** ).
    
## <a name="see-also"></a>Consulte también

#### 

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

