---
title: Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Se explica cómo usar PowerShell de Office 365 para determinar los servicios de Office 365 que se han asignado a los usuarios.
ms.openlocfilehash: 5d575ea9e0b45ddc453b3b1c73bd53bf73adab2e
ms.sourcegitcommit: 16806849f373196797d65e63ced825d547aef956
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2018
ms.locfileid: "27213957"
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365

**Resumen:** Se explica cómo usar PowerShell de Office 365 para determinar los servicios de Office 365 que se han asignado a los usuarios.
  
En Office 365, licencias de planes de licencias (también llamadas SKU o Office 365 planes) ofrecer a los usuarios acceso a los servicios de Office 365 que se definen para esos planes. Sin embargo, un usuario no puede tener acceso a todos los servicios que están disponibles en una licencia que está asignada actualmente a ellos. Puede usar PowerShell de Office 365 para ver el estado de los servicios en las cuentas de usuario. 

## <a name="before-you-begin"></a>Antes de empezar

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Use los comandos de `Get-MsolAccountSku` y `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` para buscar la siguiente información:
    
  - Los planes de licencias que están disponibles en su organización.
    
  - Los servicios que están disponibles en cada plan de licencias y el orden en que muestran (el número de índice).
    
     Para obtener más información acerca de las licencias de los planes, la licencia y servicios, vea [ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).
    
- Use el comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` para buscar las licencias que se asignan a un usuario y el orden en que están enumerados (el número de índice).
    
- Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.
    

## <a name="to-view-services-for-a-user-account"></a>Para ver los servicios para una cuenta de usuario

Para ver todos los servicios de Office 365 que un usuario tiene acceso a, use la siguiente sintaxis:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

En este ejemplo se muestran los servicios a la que el usuario BelindaN@litwareinc.com tiene acceso. Esto muestra los servicios que están asociados con todas las licencias que se asignan a su cuenta.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

En este ejemplo se muestran los servicios a los que tiene acceso la usuaria BelindaN@litwareinc.com a partir de la primera licencia asignada a su cuenta (el número de índice es 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Para ver todos los servicios para un usuario que se ha asignado *varias licencias*, use la siguiente sintaxis:

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

  
## <a name="see-also"></a>Consulte también

Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:
  
- [Crear cuentas de usuario con PowerShell de Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear cuentas de usuario con PowerShell de Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Asignar licencias a cuentas de usuario con PowerShell de Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Eliminar licencias de cuentas de usuario con PowerShell de Office 365](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]