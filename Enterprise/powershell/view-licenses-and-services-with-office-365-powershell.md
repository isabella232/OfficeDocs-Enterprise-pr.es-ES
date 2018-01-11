---
title: Ver las licencias y los servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: "Explica cómo usar PowerShell de Office 365 para ver información sobre los planes de licencias, los servicios y las licencias disponibles en su organización de Office 365."
ms.openlocfilehash: f43a1c20be157d26ec9cd1d98df2f5e17517b1d6
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Ver licencias y servicios con PowerShell de Office 365

**Resumen:** se explica cómo usar PowerShell de Office 365 para ver información sobre los planes de licencias, los servicios y las licencias disponibles en su organización de Office 365.
  
Todas las suscripciones de Office 365 se componen de estos elementos:
- **Planes de licencias** También se conocen comoplanes de licencia o planes de Office 365. Los planes de licencias determinan los servicios de Office 365 que están disponibles para los usuarios. Su suscripción a Office 365 puede contener varios planes de licencias. Un plan de licencias de ejemplo sería Office 365 Enterprise E3.
    
- **Servicios** También se conocen comoplanes de servicio. Los servicios son los productos, las características y las capacidades de Office 365 disponibles en cada plan de licencias, por ejemplo, Exchange Online y Office Professional Plus. Los usuarios pueden tener varias licencias asignadas que provengan de diferentes planes de licencias, y les permitan obtener acceso a diferentes servicios.
    
- **Licencias** Los planes de licencias contienen el número de licencias que haya adquirido. Puede asignar licencias a los usuarios para que estos puedan usar los servicios de Office 365 definidos por el plan de licencias. Cada cuenta de usuario necesita como mínimo una licencia del plan de licencias para que el usuario correspondiente pueda iniciar sesión en Office 365 y usar los servicios.
    
Puede usar PowerShell de Office 365 para ver información detallada sobre los planes de licencias, las licencias y los servicios disponibles en su organización de Office 365. Para obtener más información sobre los productos, las características y los servicios disponibles en las diferentes suscripciones de Office 365, consulte [Opciones de planes de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).
## <a name="before-you-begin"></a>Antes de empezar
<a name="RTT"> </a>

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Hay un script de PowerShell que automatiza los procedimientos descritos en este tema. En concreto, el script le permite ver y deshabilitar servicios de la organización de Office 365, incluido Sway. Para obtener más información, consulte [Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
## <a name="view-information-about-licensing-plans-and-the-available-licenses"></a>Ver información sobre los planes de licencias y las licencias disponibles
<a name="ShortVersion"> </a>

Para obtener información resumida sobre los planes de licencias actuales y las licencias disponibles en cada plan, ejecute el siguiente comando en PowerShell de Office 365:
  
```
Get-MsolAccountSku
```

Los resultados contienen la siguiente información:
  
- **AccountSkuId:** se muestran los planes de licencias disponibles para su organización con la sintaxis `<CompanyName>:<LicensingPlan>`. _<CompanyName>_ es el valor que proporcionó al inscribirse en Office 365; se trata de un valor único para su organización. El valor _<LicensingPlan>_ es el mismo para todos los usuarios. Por ejemplo, en el valor `litwareinc:ENTERPRISEPACK`, el nombre de la compañía es `litwareinc` y el nombre del plan de licencias es `ENTERPRISEPACK` (que es el nombre del sistema para Office 365 Enterprise E3).
    
- **ActiveUnits**: número de licencias que compró para un plan de licencias en concreto.
    
- **WarningUnits**: número de licencias de un plan de licencias que no renovó y que expirarán al finalizar los 30 días del período de gracia.
    
- **ConsumedUnits**: es el número de licencias asignadas a los usuarios de un plan de licencias específico.
    
Para ver información detallada sobre los servicios de Office 365 disponibles en todos sus planes de licencia, ejecute el comando siguiente:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

En la tabla siguiente, se muestran los planes de servicio de Office 365, junto con sus nombres descriptivos, para los servicios más comunes. Su lista de planes de servicio puede ser diferente. Para obtener una lista completa de los planes de servicio y sus nombres descriptivos, póngase en contacto con el [soporte técnico de Office ]((https://support.office.com/home/contact)).
  
|****Plan de servicio****|****Descripción****|
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
   
Para obtener información detallada sobre los servicios de Office 365 disponibles en un plan de licencias en concreto, use la sintaxis siguiente.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq " <AccountSkuId>"}).ServiceStatus
```

En este ejemplo, se muestran los servicios de Office 365 disponibles en el plan de licencias de litwareinc:ENTERPRISEPACK (Office 365 Enterprise E3).
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?
<a name="ShortVersion"> </a>

||
|:-----|
|![El icono reducido de LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **¿Es la primera vez que usa Office 365?**         LinkedIn Learning pone a su disposición vídeos gratuitos de cursos de [Office 365 admins and IT pros]((https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5)). |
   
## <a name="see-also"></a>Consulte también
<a name="ShortVersion"> </a>

#### 

[Ver los usuarios con licencia y sin licencia con PowerShell de Office 365](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
  
[Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365](view-account-license-and-service-details-with-office-365-powershell.md)
#### 

[Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)

