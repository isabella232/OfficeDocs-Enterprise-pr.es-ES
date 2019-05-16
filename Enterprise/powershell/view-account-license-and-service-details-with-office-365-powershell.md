---
title: Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explica cómo usar Office 365 PowerShell para determinar los servicios de Office 365 que se han asignado a los usuarios.
ms.openlocfilehash: 608d26dfc4aa1be782f94aa3b1ba5f66a0378f1e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071126"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365

**Resumen:** Explica cómo usar Office 365 PowerShell para determinar los servicios de Office 365 que se han asignado a los usuarios.
  
En Office 365, las licencias de los planes de licencias (también denominados SKU o los planes de Office 365) proporcionan a los usuarios acceso a los servicios de Office 365 definidos para esos planes. Sin embargo, un usuario podría no tener acceso a todos los servicios disponibles en una licencia que está actualmente asignada a ellos. Puede usar Office 365 PowerShell para ver el estado de los servicios de las cuentas de usuario. 

Para obtener más información acerca de los planes de licencias, la licencia y los servicios, consulte [ver licencias y servicios con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
A continuación, enumere los planes de licencia para el inquilino con este comando.

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

Use estos comandos para enumerar los servicios que están disponibles en cada plan de licencias.

```
$allSKUs=Get-AzureADSubscribedSku
$licArray = @()
for($i = 0; $i -lt $allSKUs.Count; $i++)
{
$licArray += "Service Plan: " + $allSKUs[$i].SkuPartNumber
$licArray +=  Get-AzureADSubscribedSku -ObjectID $allSKUs[$i].ObjectID | Select -ExpandProperty ServicePlans
$licArray +=  ""
}
$licArray
````

Use estos comandos para enumerar las licencias que se asignan a una cuenta de usuario.

````
$userUPN="<user account UPN, such as belindan@contoso.com>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
````

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

A continuación, ejecute este comando para enumerar los planes de licencias disponibles en su organización. 

```
Get-MsolAccountSku
```

A continuación, ejecute este comando para enumerar los servicios que están disponibles en cada plan de licencias y el orden en que aparecen (el número de índice).

````
(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus
````
  
Use este comando para enumerar las licencias que se asignan a un usuario y el orden en que aparecen (el número de índice).

````
Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses
````

>[!Note]
>Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.
>
   

### <a name="to-view-services-for-a-user-account"></a>Para ver los servicios de una cuenta de usuario

Para ver todos los servicios de Office 365 a los que tiene acceso un usuario, use la siguiente sintaxis:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

En este ejemplo se muestran los servicios a los que el usuario BelindaN@litwareinc.com tiene acceso. Se muestran los servicios que están asociados a todas las licencias asignadas a su cuenta.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

En este ejemplo se muestran los servicios a los que tiene acceso la usuaria BelindaN@litwareinc.com a partir de la primera licencia asignada a su cuenta (el número de índice es 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Para ver todos los servicios de un usuario que tiene asignadas *varias licencias*, use la siguiente sintaxis:

```
$userAccountUPN="<user account UPN>"
$AllLicenses=(Get-MsolUser -UserPrincipalName $userAccountUPN).Licenses
$licArray = @()
for($i = 0; $i -lt $AllLicenses.Count; $i++)
{
$licArray += "License: " + $AllLicenses[$i].AccountSkuId
$licArray +=  $AllLicenses[$i].ServiceStatus
$licArray +=  ""
}
$licArray
```

  
## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Consulte también

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
