---
title: Deshabilitar el acceso a los servicios al asignar licencias de usuario
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específicos al mismo tiempo mediante Office 365 PowerShell.
ms.openlocfilehash: c93f54fcd5716a0ea53290c24a2594b8bc63cecf
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491316"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>Deshabilitar el acceso a los servicios al asignar licencias de usuario

**Resumen:**  Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específicos al mismo tiempo mediante Office 365 PowerShell.
  
Las suscripciones de Office 365 incluyen planes de servicio para servicios individuales. Office 365 los administradores a menudo necesitan deshabilitar determinados planes al asignar licencias a los usuarios. Con las instrucciones de este artículo, puede asignar una licencia de Office 365 y deshabilitar los planes de servicio específicos con PowerShell para una cuenta de usuario individual o varias cuentas de usuario.


## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

A continuación, ejecute este comando para ver sus suscripciones actuales:
  
```
Get-MsolAccountSku
```

En la pantalla del `Get-MsolAccountSku` comando:
  
- **AccountSkuId** es una suscripción para su organización en \<el formato\<OrganizationName>: Subscription>. \<OrganizationName> es el valor que proporcionó cuando se inscribió en Office 365 y es único para su organización. El \<valor Subscription> es para una suscripción específica. Por ejemplo, para litwareinc: ENTERPRISEPACK, el nombre de la organización es litwareinc y el nombre de la suscripción es ENTERPRISEPACK (Office 365 Enterprise E3).
    
- **ActiveUnits** es el número de licencias que ha comprado para la suscripción.
    
- **WarningUnits** es el número de licencias de una suscripción que no se renovaron y que expirarán después del período de gracia de 30 días.
    
- **ConsumedUnits** es el número de licencias que ha asignado a los usuarios para la suscripción.
    
Tenga en cuenta el AccountSkuId de su suscripción de Office 365 que contiene los usuarios a los que desea conceder una licencia. Además, asegúrese de que hay suficientes licencias para asignar (reste **ConsumedUnits** a **ActiveUnits** ).
  
A continuación, ejecute este comando para ver los detalles sobre los planes de servicio de Office 365 que están disponibles en todas las suscripciones:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

En la pantalla de este comando, determine qué planes de servicio desea deshabilitar al asignar licencias a los usuarios.
  
A continuación se muestra una lista parcial de los planes de servicio y los servicios de Office 365 correspondientes.

En la tabla siguiente, se muestran los planes de servicio de Office 365, junto con sus nombres descriptivos, para los servicios más comunes. Su lista de planes de servicio puede ser diferente. 
  
|**Plan de servicio**|**Descripción**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Empresarial Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plan 2 de Exchange Online  <br/> |
   
Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).
   
Ahora que tiene los planes de AccountSkuId y servicio para deshabilitar, puede asignar licencias para un usuario individual o para varios usuarios.
  
### <a name="for-a-single-user"></a>Para un solo usuario

Para un solo usuario, escriba el nombre principal de usuario de la cuenta de usuario, el AccountSkuId y la lista de planes de servicio para deshabilitar y quitar el texto explicativo y los \< caracteres y >. A continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

Este es un ejemplo de bloque de comandos para la cuenta denominada belindan@contoso.com, para la licencia de Contoso: ENTERPRISEPACK, y los planes de servicio que se van a deshabilitar son RMS_S_ENTERPRISE, SWAY, INTUNE_O365 y YAMMER_ENTERPRISE:
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

### <a name="for-multiple-users"></a>Para varios usuarios

Para realizar esta tarea de administración para varios usuarios, cree un archivo de texto de valores separados por comas (CSV) que contenga los campos UserPrincipalName y UsageLocation. Aquí le mostramos un ejemplo:
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

A continuación, rellene la ubicación de los archivos CSV de entrada y salida, el identificador de SKU de cuenta y la lista de planes de servicio que se van a deshabilitar y, a continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Este bloque de comandos de PowerShell:
  
- Muestra el nombre principal de usuario de cada usuario.
    
- Asigna licencias personalizadas a cada usuario.
    
- Crea un archivo CSV con todos los usuarios que se procesaron y muestra su estado de licencia.
    
## <a name="see-also"></a>Vea también

[Deshabilitar el acceso a servicios con PowerShell de Office 365](disable-access-to-services-with-office-365-powershell.md)
  
[Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)
  
[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)

