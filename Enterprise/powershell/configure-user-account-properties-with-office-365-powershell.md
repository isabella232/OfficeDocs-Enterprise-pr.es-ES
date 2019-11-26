---
title: Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumen: Use Office 365 PowerShell para configurar las propiedades de una o varias cuentas de usuario en el inquilino de Office 365.'
ms.openlocfilehash: 67ce7d3c57f286f0b2365aa2503fdf1c8bc13429
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257661"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a>Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell

 **Resumen:** Use Office 365 PowerShell para configurar las propiedades de una o varias cuentas de usuario en el inquilino de Office 365.
  
Aunque puede usar el centro de administración de Microsoft 365 para configurar las propiedades de las cuentas de usuario de su inquilino de Office 365, también puede usar PowerShell de Office 365 y realizar algunas acciones que el centro de administración no puede.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Para configurar las propiedades de las cuentas de usuario con el módulo Azure Active Directory PowerShell para Graph, use el cmdlet [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) y especifique las propiedades que se deben establecer o cambiar. 

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
   
### <a name="change-properties-for-a-specific-user-account"></a>Cambiar las propiedades de una cuenta de usuario específica

La cuenta se identifica con el parámetro **-objectId** y se establecen o cambian las propiedades específicas con parámetros adicionales. A continuación se muestra una lista de los parámetros más comunes.
  
- -Department "\<nombre del Departamento>"
    
- -DisplayName "\<nombre de usuario completo>"
    
- -FacsimilieTelephoneNumber "\<número de fax>"
    
- -GivenName "\<nombre de usuario>"
    
- -Apellidos\<"apellidos del usuario>"
    
- -Mobile "\<número de teléfono móvil>"
    
- -Cargo "\<nombre de trabajo>"
    
- -PreferredLanguage "\<> de idioma"
    
- -Dirección "\<calle>"
    
- -City "\<nombre de la ciudad>"
    
- -Estado "\<nombre de estado>"
    
- -CódigoPostal "\<> de código postal"
    
- -Country "\<nombre de país>"
    
- -TelephoneNumber "\<número de teléfono de la oficina>"
    
- -UsageLocation "\<código de país o región de 2 caracteres>"
    
    Este es el código de país o región de dos letras ISO 3166-1 (a2).
    
Consulte [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para obtener más parámetros.


Para mostrar el nombre principal de usuario de las cuentas de usuario, ejecute el siguiente comando.
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).
    
- Ordenar la lista de nombres principales de usuario alfabéticamente ( **Sort-Object UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar solo la propiedad de nombre principal de usuario para cada cuenta ( **Select-Object UserPrincipalName** ).
- Mostrar una pantalla a la vez ( **más** ).
    
En este comando se enumeran todas las cuentas. Si desea mostrar el nombre principal de usuario de una cuenta en función de su nombre para mostrar (nombre y apellido), rellene la variable **$username** a continuación (quite \< los caracteres y >) y, a continuación, ejecute los siguientes comandos:
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En este ejemplo se muestra el nombre principal de usuario de la cuenta de usuario con el nombre para mostrar de los alféizares de Caleb.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Mediante el uso de una variable **$UPN** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar. Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificando su nombre para mostrar en lugar de su nombre principal de usuario:
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Cambiar las propiedades de todas las cuentas de usuario

Para cambiar las propiedades de todos los usuarios, puede usar la combinación de los cmdlets **Get-AzureADUser** y **set-AzureADUser** . En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios:
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).
    
- Establezca la ubicación del usuario en Francia ( **set-AzureADUser-UsageLocation "fr"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Cambiar las propiedades de un conjunto específico de cuentas de usuario

Para cambiar las propiedades de un conjunto específico de cuentas de usuario, puede usar la combinación de los cmdlets **Get-AzureADUser**, **Where**y **set-AzureADUser** . En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios del departamento de contabilidad:
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).
    
- Busque todas las cuentas de usuario que tengan su propiedad Department establecida en "Accounting" ( **donde {$ _. Department-EQ "Accounting"}** ) y enviar la información resultante al siguiente comando ( **|** ).
    
- Establezca la ubicación del usuario en Francia ( **set-AzureADUser-UsageLocation "fr"** ).
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Para configurar las propiedades de las cuentas de usuario con el módulo Microsoft Azure Active Directory para Windows PowerShell, use el cmdlet Set-MsolUser y especifique las propiedades que se van a establecer o cambiar. 

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
>[!Note]
>PowerShell Core no es compatible con el módulo Microsoft Azure Active Directory para el módulo y los cmdlets de Windows PowerShell con **msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

### <a name="change-properties-for-a-specific-user-account"></a>Cambiar las propiedades de una cuenta de usuario específica

Para configurar las propiedades de una cuenta de usuario específica, use el cmdlet [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) y especifique las propiedades que se van a establecer o cambiar. 

La cuenta se identifica con el parámetro **-UserPrincipalName** y se establecen o cambian las propiedades específicas con parámetros adicionales. A continuación se muestra una lista con los parámetros más comunes.
  
- -City "\<nombre de la ciudad>"
    
- -Country "\<nombre de país>"
    
- -Department "\<nombre del Departamento>"
    
- -DisplayName "\<nombre de usuario completo>"
    
- -Fax "\<número de fax>"
    
- -FirstName "\<nombre de usuario>"
    
- -LastName "\<apellidos del usuario>"
    
- -MobilePhone "\<número de teléfono móvil>"
    
- -Office "\<ubicación de oficina>"
    
- -PhoneNumber "\<número de teléfono de la oficina>"
    
- -CódigoPostal "\<> de código postal"
    
- -PreferredLanguage "\<> de idioma"
    
- -Estado "\<nombre de estado>"
    
- -Dirección "\<calle>"
    
- -Title "\<nombre del título>"
    
- -UsageLocation "\<código de país o región de 2 caracteres>"
    
    Este es el código de país o región de dos letras ISO 3166-1 (a2).
    
Consulte [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para obtener más parámetros.

Para ver los nombres principales de usuario de todos los usuarios, ejecute el siguiente comando.
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).
    
- Ordenar la lista de nombres principales de usuario alfabéticamente ( **Sort-Object UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar solo la propiedad de nombre principal de usuario para cada cuenta ( **Select-Object UserPrincipalName** ).
    
- Mostrar una pantalla a la vez ( **más** ).
    
En este comando se enumeran todas las cuentas. Si desea mostrar el nombre principal de usuario de una cuenta en función de su nombre para mostrar (nombre y apellido), rellene la variable **$username** a continuación (quite \< los caracteres y >) y, a continuación, ejecute los siguientes comandos:
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

En este ejemplo se muestra el nombre principal de usuario del usuario denominado Caleb alféizares.
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

Mediante el uso de una variable **$UPN** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar. Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificando su nombre para mostrar en lugar de su nombre principal de usuario:
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a>Cambiar las propiedades de todas las cuentas de usuario

Para cambiar las propiedades de todos los usuarios, puede combinar los cmdlets **Get-MsolUser** y **Set-MsolUser**. En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios:
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).
    
- Establezca la ubicación del usuario en Francia ( **set-MsolUser-UsageLocation "fr"** ).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Cambiar las propiedades de un conjunto específico de cuentas de usuario

Para cambiar las propiedades de un conjunto específico de cuentas de usuario, puede usar la combinación de los cmdlets **Get-msoluser**, **Where-Object**y **set-MsolUser** . En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios del departamento de contabilidad:
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).
    
- Busque todas las cuentas de usuario que tengan su propiedad Department establecida en "Accounting" ( **Where-Object {$ _. Department-EQ "Accounting"}** ) y enviar la información resultante al siguiente comando ( **|** ).
    
- Establezca la ubicación del usuario en Francia ( **set-MsolUser-UsageLocation "fr"** ).
    

## <a name="see-also"></a>Vea también

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
