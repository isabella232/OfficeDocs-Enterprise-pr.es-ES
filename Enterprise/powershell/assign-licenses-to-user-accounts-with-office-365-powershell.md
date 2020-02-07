---
title: Asignar licencias a cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Cómo usar Office 365 PowerShell para asignar una licencia de Office 365 a los usuarios sin licencia.
ms.openlocfilehash: 9fbf81db3b942dab90ef214169f197a8fea3f7ed
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841687"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Asignar licencias a cuentas de usuario con PowerShell de Office 365

Los usuarios no pueden usar ningún servicio de Office 365 hasta que su cuenta tenga asignada una licencia de un plan de licencias. Puede usar Office 365 PowerShell para asignar licencias rápidamente a cuentas sin licencia. 

>[!Note]
>Las cuentas de usuario deben tener asignada una ubicación. Puede hacerlo desde las propiedades de una cuenta de usuario en el centro de administración de Microsoft 365 o desde PowerShell.
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

A continuación, enumere los planes de licencia para el inquilino con este comando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

A continuación, obtenga el nombre de inicio de sesión de la cuenta a la que desea agregar una licencia, también conocida como nombre principal de usuario (UPN).

A continuación, asegúrese de que la cuenta de usuario tiene asignada una ubicación de uso.

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

Si no hay ninguna ubicación de uso asignada, puede asignar una con estos comandos:

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

Por último, especifique el nombre de inicio de sesión del usuario y el nombre del plan de licencia y ejecute estos comandos.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

Ejecute el `Get-MsolAccountSku` comando para ver los planes de licencias disponibles y el número de licencias disponibles en cada plan de la organización. El número de licencias disponibles en cada plan es **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para obtener más información acerca de los planes de licencias, las licencias y los servicios, consulte [ver licencias y servicios con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

Para buscar las cuentas sin licencia de la organización, ejecute este comando.

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

Solo se pueden asignar licencias a cuentas de usuario que tengan la propiedad **UsageLocation** establecida en un código de país ISO 3166-1 alpha-2 válido. Por ejemplo, US para Estados Unidos y FR para Francia. Algunos servicios de Office 365 no están disponibles en determinados países. Para obtener más información, consulte [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
Para buscar las cuentas que no tienen un valor **UsageLocation** , ejecute este comando.

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

Para establecer el valor **UsageLocation** en una cuenta, ejecute este comando.

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

Por ejemplo:

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
Si usa el cmdlet **Get-MsolUser** sin usar el parámetro **All**, solo se devuelven las 500 primeras cuentas.

### <a name="assigning-licenses-to-user-accounts"></a>Asignar licencias a cuentas de usuario
    
Para asignar una licencia a un usuario, use el siguiente comando en Office 365 PowerShell.
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

En este ejemplo se asigna una licencia desde el plan de licencias **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) al usuario sin licencia **\@litwareinc.com**:
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Para asignar una licencia a todos los usuarios sin licencia, ejecute este comando.
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
>No se pueden asignar varias licencias a un usuario desde el mismo plan de licencias. Si no dispone de licencias suficientes, las licencias se asignan a los usuarios en el orden en que los devuelve el cmdlet **Get-MsolUser** hasta que se agoten las licencias disponibles.
>

En este ejemplo se asignan licencias desde el plan de licencias **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a todos los usuarios sin licencia:
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

En este ejemplo se asignan las mismas licencias a los usuarios sin licencia del Departamento de ventas de Estados Unidos:
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a>Mover un usuario a una suscripción diferente (plan de licencia) con el módulo Azure Active Directory PowerShell para Graph

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
A continuación, obtenga el nombre de inicio de sesión de la cuenta de usuario para la que desea cambiar las suscripciones, también conocido como nombre principal de usuario (UPN).

A continuación, enumere las suscripciones (planes de licencia) para el inquilino con este comando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

A continuación, enumere las suscripciones que la cuenta de usuario tiene actualmente con estos comandos.

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

Identifique la suscripción que el usuario tiene actualmente (la suscripción de) y la suscripción a la que está moviendo el usuario (la suscripción a).

Por último, especifique los nombres de suscripción para y de (números de parte de SKU) y ejecute estos comandos.

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

Puede comprobar el cambio de suscripción de la cuenta de usuario con estos comandos.

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a>Vea también

[Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
