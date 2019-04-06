---
title: Deshabilitar el acceso a servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Use Office 365 PowerShell para deshabilitar el acceso a los servicios de Office 365 para los usuarios.
ms.openlocfilehash: 0f2c603edd624c9d53a28b37c1c9795bad05ec0f
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001823"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Deshabilitar el acceso a servicios con PowerShell de Office 365

**Resumen:** Explica cómo usar Office 365 PowerShell para deshabilitar el acceso a los servicios de Office 365 para los usuarios de la organización.
  
Cuando se asigna una licencia a una cuenta de Office 365 a un plan de licencias, los servicios de Office 365 se ponen a disposición del usuario a partir de dicha licencia. Sin embargo, puede controlar los servicios de Office 365 a los que el usuario puede tener acceso. Por ejemplo, aunque la licencia permita el acceso al servicio de SharePoint Online, puede deshabilitar el acceso a ella. Puede usar PowerShell para deshabilitar el acceso a cualquier número de servicios para un plan de licencias específico para:

- Una cuenta individual.
    
- Un grupo de cuentas.
    
- Todas las cuentas de su organización.

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

A continuación, use este comando para ver los planes de licencias disponibles, también conocidos como Accountskuid:

```
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

Para obtener más información, vea [ver licencias y servicios con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Para ver los resultados antes y después de los procedimientos de este tema, vea [View Account License and Service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
Hay un script de PowerShell que automatiza los procedimientos descritos en este tema. En concreto, el script permite ver y deshabilitar servicios en la organización de Office 365, incluido Sway. Para obtener más información, consulte [Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a>DesHabilitar los servicios específicos de Office 365 para usuarios específicos para un plan de licencias específico
  
Para deshabilitar un conjunto específico de servicios de Office 365 para los usuarios de un plan de licencias específico, siga estos pasos:
  
1. Identifique los servicios no deseados en el plan de licencias mediante la siguiente sintaxis:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  En el ejemplo siguiente se crea un objeto **LicenseOptions** que deshabilita los servicios de Office Online y SharePoint Online en el plan `litwareinc:ENTERPRISEPACK` de licencias denominado (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Use el objeto **LicenseOptions** del paso 1 en uno o más usuarios.
    
  - Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  En el ejemplo siguiente se crea una nueva cuenta para Naiara Padilla que asigna la licencia y deshabilita los servicios descritos en el paso 1.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  Para obtener más información acerca de la creación de cuentas de usuario en Office 365 PowerShell, consulte [Create User accounts with office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Para deshabilitar los servicios para un usuario con licencia existente, use la siguiente sintaxis:
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  En este ejemplo se deshabilitan los servicios para el usuario BelindaN@litwareinc.com.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Para deshabilitar los servicios descritos en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre de su plan de Office 365 en la pantalla del cmdlet **Get-MsolAccountSku** (por ejemplo, **litwareinc: ENTERPRISEPACK**) y, a continuación, ejecute los comandos siguientes:
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_ , solo se devuelven las primeras 500 cuentas de usuario.


  - Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:
    
  - **Filtrar las cuentas basándose en un atributo de cuenta existente** Para ello, use la sintaxis siguiente:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  En el siguiente ejemplo se deshabilitan los servicios para usuarios del Departamento de ventas de Estados Unidos.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Usar una lista de cuentas específicas** Para ello, siga estos pasos:
    
1. Cree un archivo de texto que contenga una cuenta en cada línea como en el ejemplo:
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  En este ejemplo, el archivo de texto es C\\: mis\\documentos accounts. txt.
    
2. Ejecute el siguiente comando:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Si desea deshabilitar el acceso a los servicios para varios planes de licencias, repita las instrucciones anteriores para cada plan de licencias y asegúrese de que:

- Las cuentas de usuario se han asignado al plan de licencias.
- Los servicios que se deshabilitan están disponibles en el plan de licencias.

Para deshabilitar los servicios de Office 365 para los usuarios mientras los está asignando a un plan de licencias, vea desHabilitar el [acceso a los servicios mientras se asignan licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).


## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Vea también
<a name="SeeAlso"> </a>

Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:
  
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear cuentas de usuario con PowerShell de Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Asignar licencias a cuentas de usuario con PowerShell de Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Crear cuentas de usuario con PowerShell de Office 365](create-user-accounts-with-office-365-powershell.md)
    
