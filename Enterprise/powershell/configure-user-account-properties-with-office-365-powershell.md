---
title: Configurar las propiedades de la cuenta de usuario 365 de Microsoft con PowerShell
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
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumen: Use PowerShell para Microsoft 365 para configurar las propiedades de una o varias cuentas de usuario en su inquilino de Microsoft 365.'
ms.openlocfilehash: ccf9bf9930551ab1ee26ef7a1f69427cdc4871f5
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230856"
---
# <a name="configure-microsoft-365-user-account-properties-with-powershell"></a>Configurar las propiedades de la cuenta de usuario 365 de Microsoft con PowerShell

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Aunque puede usar el centro de administración de Microsoft 365 para configurar las propiedades de las cuentas de usuario de su inquilino de Microsoft 365, también puede usar PowerShell y hacer algunas cosas que el centro de administración de Microsoft 365 no puede.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Para configurar las propiedades de las cuentas de usuario con el módulo Azure Active Directory PowerShell para Graph, use el cmdlet [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) y especifique las propiedades que se deben establecer o cambiar. 

En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
   
### <a name="change-properties-for-a-specific-user-account"></a>Cambiar las propiedades de una cuenta de usuario específica

La cuenta se identifica con el parámetro **-objectId** y se establecen o cambian las propiedades específicas con parámetros adicionales. A continuación se muestra una lista de los parámetros más comunes.
  
- -Departamento " \<department name> "
    
- -DisplayName " \<full user name> "
    
- -FacsimilieTelephoneNumber " \<fax number> "
    
- -GivenName " \<user first name> "
    
- -2º apellido " \<user last name> "
    
- -Mobile " \<mobile phone number> "
    
- -JobTitle " \<job title> "
    
- -PreferredLanguage " \<language> "
    
- -StreetAddress " \<street address> "
    
- -City " \<city name> "
    
- -State " \<state name> "
    
- -CódigoPostal " \<postal code> "
    
- -Country " \<country name> "
    
- -TelephoneNumber " \<office phone number> "
    
- -UsageLocation " \<2-character country or region code> "
    
    Este es el código de país o región de dos letras ISO 3166-1 (a2).
    
Consulte [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para obtener más parámetros.


Para mostrar el nombre principal de usuario de las cuentas de usuario, ejecute el siguiente comando.
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Este comando indica a PowerShell que:
  
- Obtener toda la información de las cuentas de usuario (**Get-AzureADUser**) y enviarla al comando siguiente ( **|** ).
    
- Ordenar la lista de nombres principales de usuario alfabéticamente (**ordenar UserPrincipalName**) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar solo la propiedad de nombre principal de usuario para cada cuenta (**Seleccione UserPrincipalName**).

- Mostrar una pantalla a la vez (**más**).
    
En este comando se enumeran todas las cuentas. Si desea mostrar el nombre principal de usuario de una cuenta en función de su nombre para mostrar (nombre y apellido), rellene la variable **$username** a continuación (quitando los \< and > caracteres) y, a continuación, ejecute los siguientes comandos:
  
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

Este comando indica a PowerShell que:
  
- Obtener toda la información de las cuentas de usuario (**Get-AzureADUser**) y enviarla al comando siguiente ( **|** ).
    
- Establezca la ubicación del usuario en Francia (**set-AzureADUser-UsageLocation "fr"**).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Cambiar las propiedades de un conjunto específico de cuentas de usuario

Para cambiar las propiedades de un conjunto específico de cuentas de usuario, puede usar la combinación de los cmdlets **Get-AzureADUser**, **Where**y **set-AzureADUser** . En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios del departamento de contabilidad:
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

Este comando indica a PowerShell que:
  
- Obtener toda la información de las cuentas de usuario (**Get-AzureADUser**) y enviarla al comando siguiente ( **|** ).
    
- Busque todas las cuentas de usuario que tengan su propiedad Department establecida en "Accounting" (**donde {$ _. Department-EQ "Accounting"}**) y enviar la información resultante al siguiente comando ( **|** ).
    
- Establezca la ubicación del usuario en Francia (**set-AzureADUser-UsageLocation "fr"**).
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Para configurar las propiedades de las cuentas de usuario con el módulo Microsoft Azure Active Directory para Windows PowerShell, use el cmdlet **set-MsolUser** y especifique las propiedades que se van a establecer o cambiar. 

En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
  
>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

### <a name="change-properties-for-a-specific-user-account"></a>Cambiar las propiedades de una cuenta de usuario específica

Para configurar las propiedades de una cuenta de usuario específica, use el cmdlet [set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) y especifique las propiedades que se van a establecer o cambiar. 

La cuenta se identifica con el parámetro **-UserPrincipalName** y se establecen o cambian las propiedades específicas con parámetros adicionales. A continuación se muestra una lista con los parámetros más comunes.
  
- -City " \<city name> "
    
- -Country " \<country name> "
    
- -Departamento " \<department name> "
    
- -DisplayName " \<full user name> "
    
- -Fax " \<fax number> "
    
- -FirstName " \<user first name> "
    
- -LastName " \<user last name> "
    
- -MobilePhone " \<mobile phone number> "
    
- -Office " \<office location> "
    
- -PhoneNumber " \<office phone number> "
    
- -CódigoPostal " \<postal code> "
    
- -PreferredLanguage " \<language> "
    
- -State " \<state name> "
    
- -StreetAddress " \<street address> "
    
- -Title " \<title name> "
    
- -UsageLocation " \<2-character country or region code> "
    
    Este es el código de país o región de dos letras ISO 3166-1 (a2).
    
Consulte [set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) para obtener más parámetros.

Para ver los nombres principales de usuario de todos los usuarios, ejecute el siguiente comando.
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

Este comando indica a PowerShell que:
  
- Obtener toda la información de las cuentas de usuario (**Get-MsolUser**) y enviarla al comando siguiente ( **|** ).
    
- Ordenar la lista de nombres principales de usuario alfabéticamente (**ordenar UserPrincipalName**) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar solo la propiedad de nombre principal de usuario para cada cuenta (**Seleccione UserPrincipalName**).
    
- Mostrar una pantalla a la vez (**más**).
    
En este comando se enumeran todas las cuentas. Si desea mostrar el nombre principal de usuario de una cuenta en función de su nombre para mostrar (nombre y apellido), rellene la variable **$username** a continuación (quitando los \< and > caracteres) y, a continuación, ejecute los siguientes comandos:
  
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

Este comando indica a PowerShell que:
  
- Obtener toda la información de las cuentas de usuario (**Get-MsolUser**) y enviarla al comando siguiente ( **|** ).
    
- Establezca la ubicación del usuario en Francia (**set-MsolUser-UsageLocation "fr"**).
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a>Cambiar las propiedades de un conjunto específico de cuentas de usuario

Para cambiar las propiedades de un conjunto específico de cuentas de usuario, puede usar la combinación de los cmdlets **Get-msoluser**, **Where**y **set-MsolUser** . En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios del departamento de contabilidad:
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

Este comando indica a PowerShell que:
  
- Obtener toda la información de las cuentas de usuario (**Get-MsolUser**) y enviarla al comando siguiente ( **|** ).
    
- Busque todas las cuentas de usuario que tengan su propiedad Department establecida en "Accounting" (**donde {$ _. Department-EQ "Accounting"}**) y enviar la información resultante al siguiente comando ( **|** ).
    
- Establezca la ubicación del usuario en Francia (**set-MsolUser-UsageLocation "fr"**).
    

## <a name="see-also"></a>Consulte también

[Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)
