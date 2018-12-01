---
title: Asignar licencias a cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/29/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: Se explica cómo usar PowerShell de Office 365 para asignar una licencia de Office 365 a los usuarios sin licencia.
ms.openlocfilehash: 4c91c9f2441d0e537f2fa23fd1f021fe0bfe03b6
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123297"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Asignar licencias a cuentas de usuario con PowerShell de Office 365

**Resumen:** se explica cómo usar PowerShell de Office 365 para asignar una licencia de Office 365 a los usuarios sin licencia.
  
Es importante asignar licencias a las cuentas de usuario de Office 365, ya que los usuarios no pueden usar ningún servicio de Office 365 hasta que su cuenta tenga una licencia. Puede usar PowerShell de Office 365 para asignar de forma eficiente licencias a cuentas sin licencia, especialmente a varias cuentas. 

## <a name="before-you-begin"></a>Antes de empezar
<a name="RTT"> </a>

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Use el cmdlet **Get-MsolAccountSku** para ver los planes de licencias disponibles y el número de licencias disponibles en cada plan de la organización. El número de licencias disponibles en cada plan es **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para obtener más información sobre los planes de licencias, las licencias y los servicios, vea[Ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).
    
- Para buscar las cuentas sin licencia de la organización, ejecute el comando  `Get-MsolUser -All -UnlicensedUsersOnly`
    
- Solo puede asignar licencias a cuentas de usuario que tengan la propiedad **UsageLocation** establecida en un código de país ISO 3166-1 alpha-2 válido (por ejemplo, “US” para Estados Unidos y “FR” para Francia). Algunos servicios de Office 365 no están disponibles en determinados países. Para obtener más información, vea [Información sobre restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Para buscar cuentas que no tengan un valor **UsageLocation**, ejecute el comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Para establecer el valor **UsageLocation** en una cuenta, utilice la sintaxis `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Por ejemplo,  `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- Si usa el cmdlet **Get-MsolUser** sin el parámetro `-All`, solo se devuelven las 500 primeras cuentas.

## <a name="assigning-licenses-to-user-accounts"></a>Asignación de licencias para las cuentas de usuario
    
Para asignar una licencia a un usuario, use la sintaxis siguiente en PowerShell de Office 365:
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

En este ejemplo, se asigna una licencia desde el plan de licencias `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) al usuario sin licencia `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Para asignar una licencia a varios usuarios sin licencia, use la sintaxis siguiente:
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Notas**
  
- No se pueden asignar varias licencias a un usuario desde el mismo plan de licencias.
    
- Si no dispone de licencias suficientes, las licencias se asignan a los usuarios en el orden en que los devuelve el cmdlet **Get-MsolUser** hasta que se agoten las licencias disponibles.
    
En este ejemplo, se asignan licencias desde el plan de licencias `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) a todos los usuarios sin licencia.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

En este ejemplo se asignan esas mismas licencias a los usuarios sin licencia del departamento de ventas de los Estados Unidos.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```
  
## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Consulte también
<a name="SeeAlso"> </a>

Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:
  
- [Crear cuentas de usuario](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminación y restauración de las cuentas de usuario](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Cuentas de usuario de bloque](block-user-accounts-with-office-365-powershell.md)
    
- [Quitar las licencias de las cuentas de usuario](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

