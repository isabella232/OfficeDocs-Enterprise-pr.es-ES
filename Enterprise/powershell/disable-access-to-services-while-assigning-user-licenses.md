---
title: Deshabilitar el acceso a los servicios al asignar licencias de usuario
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 09/27/2019
audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específicos al mismo tiempo mediante Office 365 PowerShell.
ms.openlocfilehash: 019a8c62829c3b8c4bd2e81d573b861b0a09794a
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841566"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>Deshabilitar el acceso a los servicios al asignar licencias de usuario

Las suscripciones de Office 365 incluyen planes de servicio para servicios individuales. Office 365 los administradores a menudo necesitan deshabilitar determinados planes al asignar licencias a los usuarios. Con las instrucciones de este artículo, puede asignar una licencia de Office 365 y deshabilitar los planes de servicio específicos con PowerShell para una cuenta de usuario individual o varias cuentas de usuario.

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  

A continuación, enumere los planes de licencia para el inquilino con este comando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

A continuación, obtenga el nombre de inicio de sesión de la cuenta a la que desea agregar una licencia, también conocida como nombre principal de usuario (UPN).

A continuación, compile una lista de servicios para habilitar. Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Para el bloque de comandos siguiente, rellene el nombre principal de usuario de la cuenta de usuario, el número de parte de SKU y la lista de planes de servicio para habilitar y quitar \< el texto explicativo y los caracteres y >. A continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```powershell
$userUPN="<user account UPN>"
$skuPart="<SKU part number>"
$serviceList=<double-quoted enclosed, comma-separated list of enabled services>
$user = Get-AzureADUser -ObjectID $userUPN
$skuID= (Get-AzureADSubscribedSku  | Where {$_.SkuPartNumber -eq $skuPart}).SkuID
$SkuFeaturesToEnable = @($serviceList)
$StandardLicense = Get-AzureADSubscribedSku | Where {$_.SkuId -eq $skuID}
$SkuFeaturesToDisable = $StandardLicense.ServicePlans | ForEach-Object { $_ | Where {$_.ServicePlanName -notin $SkuFeaturesToEnable }}
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = $StandardLicense.SkuId
$License.DisabledPlans = $SkuFeaturesToDisable.ServicePlanId
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $user.ObjectId -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

A continuación, ejecute este comando para ver sus suscripciones actuales:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

En la pantalla del `Get-MsolAccountSku` comando:
  
- **AccountSkuId** es una suscripción para su organización en \<NombreOrganización>:\<subscription> Format. El \<> NombreDeOrganización es el valor que proporcionó cuando se inscribió en Office 365 y es único para su organización. El \<valor de> de suscripción es para una suscripción específica. Por ejemplo, para litwareinc: ENTERPRISEPACK, el nombre de la organización es litwareinc y el nombre de la suscripción es ENTERPRISEPACK (Office 365 Enterprise E3).
    
- **ActiveUnits** es el número de licencias que ha comprado para la suscripción.
    
- **WarningUnits** es el número de licencias de una suscripción que no se renovaron y que expirarán después del período de gracia de 30 días.
    
- **ConsumedUnits** es el número de licencias que ha asignado a los usuarios para la suscripción.
    
Tenga en cuenta el AccountSkuId de su suscripción de Office 365 que contiene los usuarios a los que desea conceder una licencia. Además, asegúrese de que hay suficientes licencias para asignar (reste **ConsumedUnits** a **ActiveUnits** ).
  
A continuación, ejecute este comando para ver los detalles sobre los planes de servicio de Office 365 que están disponibles en todas las suscripciones:
  
```powershell
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
| `SHAREPOINTWAC` <br/> |Office   <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plan 2 de Exchange Online  <br/> |
   
Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).
   
Ahora que tiene los planes de AccountSkuId y servicio para deshabilitar, puede asignar licencias para un usuario individual o para varios usuarios.
  
### <a name="for-a-single-user"></a>Para un solo usuario

Para un solo usuario, escriba el nombre principal de usuario de la cuenta de usuario, el AccountSkuId y la lista de planes de servicio para deshabilitar y quitar el texto explicativo y los \< caracteres y >. A continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```powershell
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

A continuación se muestra un ejemplo de un bloque de comandos para la cuenta denominada belindan@contoso.com, para la licencia de Contoso: ENTERPRISEPACK, y los planes de servicio que se van a deshabilitar son RMS_S_ENTERPRISE, SWAY, INTUNE_O365 y YAMMER_ENTERPRISE:
  
```powershell
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
  
```powershell
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

A continuación, rellene la ubicación de los archivos CSV de entrada y salida, el identificador de SKU de cuenta y la lista de planes de servicio que se van a deshabilitar y, a continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
```powershell
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
  
[Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)

