---
title: Deshabilitar el acceso a los servicios de Microsoft 365 con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Use PowerShell para deshabilitar el acceso a los servicios de Microsoft 365 para los usuarios.
ms.openlocfilehash: 4e7c59447dae027dffa7fd5ea24d1818d5d64a9a
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230686"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a>Deshabilitar el acceso a los servicios de Microsoft 365 con PowerShell

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Cuando a una cuenta de Microsoft 365 se le asigna una licencia de un plan de licencias, los servicios de Microsoft 365 se ponen a disposición del usuario a partir de dicha licencia. Sin embargo, puede controlar los servicios de Microsoft 365 a los que el usuario puede tener acceso. Por ejemplo, aunque la licencia permita el acceso al servicio de SharePoint Online, puede deshabilitar el acceso a ella. Puede usar PowerShell para deshabilitar el acceso a cualquier número de servicios para un plan de licencias específico para:

- Una cuenta individual.
- Un grupo de cuentas.
- Todas las cuentas de su organización.

>[!Note]
>Hay dependencias de servicio de Microsoft 365 que pueden impedir que se deshabilite un servicio especificado cuando otros servicios dependen de él.
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

A continuación, use este comando para ver los planes de licencias disponibles, también conocidos como Accountskuid:

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

Para obtener más información, vea [ver licencias y servicios con PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
Para ver los resultados antes y después de los procedimientos de este tema, vea [View Account License and Service details with PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
Hay un script de PowerShell que automatiza los procedimientos descritos en este tema. En concreto, el script permite ver y deshabilitar servicios en la organización de Microsoft 365, incluido Sway. Para obtener más información, vea [deshabilitar el acceso a Sway con PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a>Deshabilitar los servicios específicos de Microsoft 365 para usuarios específicos para un plan de licencias específico
  
Para deshabilitar un conjunto específico de servicios de Microsoft 365 para los usuarios de un plan de licencias específico, siga estos pasos:
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a>Paso 1: identificar los servicios no deseados en el plan de licencias mediante la siguiente sintaxis:
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

En el ejemplo siguiente se crea un objeto **LicenseOptions** que deshabilita los servicios de Office y SharePoint Online en el plan de licencias denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a>Paso 2: Use el objeto **LicenseOptions** del paso 1 en uno o más usuarios.
    
Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

En el ejemplo siguiente se crea una nueva cuenta para Naiara Padilla que asigna la licencia y deshabilita los servicios descritos en el paso 1.
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

Para obtener más información acerca de la creación de cuentas de usuario en PowerShell para Microsoft 365, consulte [Create User accounts with PowerShell](create-user-accounts-with-office-365-powershell.md).
    
Para deshabilitar los servicios para un usuario con licencia existente, use la siguiente sintaxis:
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

En este ejemplo se deshabilitan los servicios para el usuario BelindaN@litwareinc.com.
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

Para deshabilitar los servicios descritos en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre del plan 365 de Microsoft en la pantalla del cmdlet **Get-MsolAccountSku** (por ejemplo, **litwareinc: ENTERPRISEPACK**) y, a continuación, ejecute los comandos siguientes:
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_ , solo se devuelven las primeras 500 cuentas de usuario.

Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:
    
**Método 1. Filtrar las cuentas basándose en un atributo de cuenta existente** 

Para ello, utilice la siguiente sintaxis:
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

En el siguiente ejemplo se deshabilitan los servicios para usuarios del Departamento de ventas de Estados Unidos.
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

**Método 2: usar una lista de cuentas específicas** 

Para ello, siga estos pasos:
    
1. Cree un archivo de texto que contenga una cuenta en cada línea como en el ejemplo:
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  En este ejemplo, el archivo de texto es C: \\ Mis documentos \\Accounts.txt.
    
2. Ejecute el siguiente comando:
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Si desea deshabilitar el acceso a los servicios para varios planes de licencias, repita las instrucciones anteriores para cada plan de licencias y asegúrese de que:

- Las cuentas de usuario se han asignado al plan de licencias.
- Los servicios que se deshabilitan están disponibles en el plan de licencias.

Para deshabilitar los servicios de Microsoft 365 para los usuarios mientras los está asignando a un plan de licencias, vea [deshabilitar el acceso a los servicios mientras se asignan licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).


## <a name="see-also"></a>Consulte también

[Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)
