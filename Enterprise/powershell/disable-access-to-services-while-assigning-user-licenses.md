---
title: Deshabilitar el acceso a los servicios al asignar licencias de usuario
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom: PowerShell, Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específico al mismo tiempo el uso de PowerShell de Office 365."
ms.openlocfilehash: 5b39a7e92217f5f7039ae1d8980f0c271ea29bfb
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a>Deshabilitar el acceso a los servicios al asignar licencias de usuario

**Resumen:**  Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específico al mismo tiempo el uso de PowerShell de Office 365.
  
Suscripciones a Office 365 cuentan con planes de servicio para los servicios individuales. A menudo, los administradores de Office 365 necesitan deshabilitar ciertos planes al asignar licencias a los usuarios. Con las instrucciones de este artículo, puede asignar una licencia de Office 365 al deshabilitar el uso de PowerShell para un usuario individual o varias cuentas de usuario de planes de servicio específico.
  
> [!NOTE]
> En este artículo se basa en el trabajo de Siddhartha Parmar, un ingeniero de escalamiento de soporte de Microsoft. 
  
## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a>Recopilar información sobre suscripciones y planes de servicio

Ejecute este comando para ver sus suscripciones actuales:
  
```
Get-MsolAccountSku
```

En la presentación de la `Get-MsolAccountSku` comando:
  
- **AccountSkuId** es una suscripción para su organización en \<NombreDeOrganización >:\<suscripción > formato. El \<NombreDeOrganización > es el valor que proporciona cuando se inscribe en Office 365 y es exclusivo para su organización. El \<suscripción > es el valor de una suscripción específica. Por ejemplo, para litwareinc:ENTERPRISEPACK, el nombre de la organización es litwareinc y el nombre de la suscripción es ENTERPRISEPACK (Office 365 Enterprise E3).
    
- **ActiveUnits** es el número de licencias que ha adquirido para la suscripción.
    
- **WarningUnits** es el número de licencias en una suscripción que usted no ha renovado y que caducará después del período de gracia de 30 días.
    
- **ConsumedUnits** es el número de licencias que haya asignado a los usuarios para la suscripción.
    
Tenga en cuenta el AccountSkuId de la suscripción de Office 365 que contiene los usuarios que desea licencia. Además, asegúrese de que hay suficientes licencias para asignar (restar **ConsumedUnits** de **ActiveUnits** ).
  
A continuación, ejecute este comando para ver los detalles acerca de los planes de servicio de Office 365 que están disponibles en todas las suscripciones:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

En la pantalla de este comando, determinar qué planes de servicio que le gustaría deshabilitar al asignar licencias a los usuarios.
  
Aquí es una lista parcial de los planes de servicio y sus correspondientes servicios de Office 365.
  
|**Plan de servicio**|**Descripción**|
|:-----|:-----|
|BALANCEO  <br/> |Sway  <br/> |
|INTUNE_O365  <br/> |Administración de dispositivos móviles para Office 365  <br/> |
|YAMMER_ENTERPRISE  <br/> |Yammer  <br/> |
|RMS_S_ENTERPRISE  <br/> |Azure Rights Management (RMS)  <br/> |
|OFFICESUBSCRIPTION  <br/> |Office Professional Plus  <br/> |
|MCOSTANDARD  <br/> |Skype Empresarial Online  <br/> |
|SHAREPOINTWAC  <br/> |Office Online  <br/> |
|SHAREPOINTENTERPRISE  <br/> |SharePoint Online  <br/> |
|EXCHANGE_S_ENTERPRISE  <br/> |Plan 2 de Exchange Online  <br/> |
   
Ahora que tiene el AccountSkuId y los planes de servicio para deshabilitar, puede asignar licencias para un usuario individual o para varios usuarios.
  
## <a name="for-a-single-user"></a>Para un único usuario

Para un solo usuario, rellene el nombre principal de usuario de la cuenta de usuario, la AccountSkuId y la lista de planes de servicio para deshabilitar y quitar el texto explicativo y los \< y > caracteres. A continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
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

Aquí es un bloque de comandos de ejemplo para la cuenta denominada belindan@contoso.com, para la licencia de contoso:ENTERPRISEPACK, y los planes de servicio para deshabilitar son RMS_S_ENTERPRISE, SWAY, INTUNE_O365 y YAMMER_ENTERPRISE:
  
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

## <a name="for-multiple-users"></a>Para varios usuarios

Para realizar esta tarea de administración de varios usuarios, cree un archivo de texto de valores separados por comas (CSV) que contiene los campos UserPrincipalName y UsageLocation. Éste es un ejemplo:
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

A continuación, especifique la ubicación de la entrada y salida CSV archivos, la cuenta ID de SKU y la lista de planes de servicio para deshabilitar y, a continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

Este bloque de comandos de PowerShell:
  
- Muestra el nombre principal de usuario de cada usuario.
    
- Asigna personalizar licencias para cada usuario.
    
- Crea un archivo CSV con todos los usuarios que se han procesado y muestra su estado de licencia.
    
## <a name="see-also"></a>Consulte también

#### 

[Deshabilitar el acceso a servicios con PowerShell de Office 365](disable-access-to-services-with-office-365-powershell.md)
  
[Deshabilitar el acceso al dominio con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md)
  
[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)

