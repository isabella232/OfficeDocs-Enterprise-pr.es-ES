---
title: Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumen: Use PowerShell de Office 365 para configurar las propiedades de individuales o de varias cuentas de usuario en el inquilino de Office 365.'
ms.openlocfilehash: 4db63482fdcc1d6cb186e663fd55c13186b33813
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546491"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell

 **Resumen:** Usar Office 365 PowerShell para configurar las propiedades de individuales o de varias cuentas de usuario en el inquilino de Office 365.
  
Aunque puede usar el centro de administración de Office 365 para configurar las propiedades de las cuentas de usuario de su inquilino de Office 365, también puede usar PowerShell de Office 365 y hacer cosas que no se puede el centro de administración de Office 365.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Usar Azure Active Directory PowerShell para el módulo de gráfico

Para configurar las propiedades de cuentas de usuario con Azure Active Directory PowerShell para el módulo de gráfico, use el cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) y especificar las propiedades para establecer o cambiar. 

Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
   
### <a name="change-properties-for-a-specific-user-account"></a>Cambiar las propiedades de una cuenta de usuario específica

Identificar la cuenta con el parámetro **- ObjectID** y establecer o cambiar las propiedades específicas con parámetros adicionales. Aquí tiene una lista de los parámetros más comunes.
  
- -Departamento "\<nombre de departamento >"
    
- -DisplayName "\<nombre completo del usuario >"
    
- -FacsimilieTelephoneNumber "\<número de fax >"
    
- -GivenName "\<nombre de usuario >"
    
- -Apellido "\<apellidos del usuario >"
    
- -Móvil "\<número de teléfono móvil >"
    
- -JobTitle "\<puesto >"
    
- -PreferredLanguage "\<idioma >"
    
- -StreetAddress "\<dirección postal >"
    
- -Ciudad "\<nombre de la ciudad >"
    
- -Estado "\<nombre de estado >"
    
- -PostalCode "\<código postal >"
    
- -País "\<nombre del país >"
    
- -TelephoneNumber "\<número de teléfono de office >"
    
- Propiedad - UsageLocation "\<código de país o región 2 caracteres >"
    
    Este es el código de región o país de dos letras ISO 3166-1 alfa-2 (A2).
    
Vea [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parámetros adicionales.
  
Para mostrar el nombre Principal de usuario para las cuentas de usuario, ejecute el siguiente comando.
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Ordenar alfabéticamente la lista de nombres principales de usuario ( **Objeto Sort UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar sólo la propiedad de nombre Principal de usuario para cada cuenta ( **UserPrincipalName Select-Object** ).
- Mostrarlos una pantalla a la vez ( **más** ).
    
Este comando obtendrá una lista con todas las cuentas. Si desea mostrar el nombre Principal de usuario de una cuenta en función de su presentación name (nombre y el apellido), rellene la variable **$userName** más abajo (eliminación de la \< y > caracteres), y, a continuación, ejecute los siguientes comandos:
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En este ejemplo se muestra el nombre Principal de usuario para la cuenta de usuario con el nombre para mostrar de Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Mediante el uso de una variable de **$upn** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar. Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificar su nombre para mostrar en lugar de su nombre Principal de usuario:
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Cambiar las propiedades de todas las cuentas de usuario

Para cambiar las propiedades de todos los usuarios, puede usar la combinación de los cmdlets **Get-AzureADUser** y **Set-AzureADUser** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios a Francia:
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Establezca la ubicación del usuario en Francia ( **Set-AzureADUser-propiedad UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Cambiar las propiedades de un conjunto específico de cuentas de usuario

Para cambiar las propiedades de un conjunto específico de la cuenta de usuario, puede usar la combinación de los cmdlets **Get-AzureADUser**, **donde**y **Set-AzureADUser** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios del departamento de contabilidad a Francia:
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen su propiedad departamento establecida en "Contabilidad" ( **donde {$_. Departamento - eq "Contabilidad"}** ) y enviar la información resultante con el siguiente comando ( **|** ).
    
- Establezca la ubicación del usuario en Francia ( **Set-AzureADUser-propiedad UsageLocation "FR"** ).
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Usar el módulo de Microsoft Azure Active Directory para Windows PowerShell

Para configurar las propiedades de cuentas de usuario con el Microsoft Azure Active Directory módulo para Windows PowerShell, use el cmdlet Set-MsolUser y especificar las propiedades para establecer o cambiar. 

Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
### <a name="change-properties-for-a-specific-user-account"></a>Cambiar las propiedades de una cuenta de usuario específica

Para configurar las propiedades de una cuenta de usuario específica, use el cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) y especificar las propiedades para establecer o cambiar. 

Identificar la cuenta con el parámetro **- UserPrincipalName** y establecer o cambiar las propiedades específicas con parámetros adicionales. Aquí tiene una lista de los parámetros más comunes.
  
- -Ciudad "\<nombre de la ciudad >"
    
- -País "\<nombre del país >"
    
- -Departamento "\<nombre de departamento >"
    
- -DisplayName "\<nombre completo del usuario >"
    
- -Fax "\<número de fax >"
    
- -FirstName "\<nombre de usuario >"
    
- -LastName "\<apellidos del usuario >"
    
- -MobilePhone "\<número de teléfono móvil >"
    
- -Office "\<ubicación de la oficina >"
    
- -PhoneNumber "\<número de teléfono de office >"
    
- -PostalCode "\<código postal >"
    
- -PreferredLanguage "\<idioma >"
    
- -Estado "\<nombre de estado >"
    
- -StreetAddress "\<dirección postal >"
    
- -Title "\<nombre título >"
    
- Propiedad - UsageLocation "\<código de país o región 2 caracteres >"
    
    Este es el código de región o país de dos letras ISO 3166-1 alfa-2 (A2).
    
Vea [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para parámetros adicionales.
  
Para ver los nombres de entidad de seguridad de usuario de todos los usuarios, ejecute el siguiente comando.
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Ordenar alfabéticamente la lista de nombres principales de usuario ( **Objeto Sort UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar sólo la propiedad de nombre Principal de usuario para cada cuenta ( **UserPrincipalName Select-Object** ).
    
- Mostrarlos una pantalla a la vez ( **más** ).
    
Este comando obtendrá una lista con todas las cuentas. Si desea mostrar el nombre Principal de usuario de una cuenta en función de su presentación name (nombre y el apellido), rellene la variable **$userName** más abajo (eliminación de la \< y > caracteres), y, a continuación, ejecute los siguientes comandos:
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En este ejemplo se muestra el nombre de entidad de seguridad de usuario para el usuario llamado Caleb Sills.
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Mediante el uso de una variable de **$upn** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar. Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificar su nombre para mostrar en lugar de su nombre Principal de usuario:
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Cambiar las propiedades de todas las cuentas de usuario

Para cambiar las propiedades de todos los usuarios, puede combinar los cmdlets **Get-MsolUser** y **Set-MsolUser**. En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios:
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Establezca la ubicación del usuario en Francia ( **Set-MsolUser-propiedad UsageLocation "FR"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Cambiar las propiedades de un conjunto específico de cuentas de usuario

Para cambiar las propiedades de un conjunto específico de la cuenta de usuario, puede usar la combinación de los cmdlets **Get-MsolUser**, **Where-Object**y **Set-MsolUser** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios del departamento de contabilidad a Francia:
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen su propiedad departamento establecido en "Contabilidad" ( **Where-Object {$_. Departamento - eq "Contabilidad"}** ) y enviar la información resultante con el siguiente comando ( **|** ).
    
- Establezca la ubicación del usuario en Francia ( **Set-MsolUser-propiedad UsageLocation "FR"** ).
    

## <a name="see-also"></a>Vea también

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
