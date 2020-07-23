---
title: Ver licencias y servicios de Microsoft 365 con PowerShell
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
- O365ITProTrain
- LIL_Placement
- PowerShell
ms.assetid: bb5260a9-a6a3-4f34-b19a-06c6699f6723
description: Explica cómo usar PowerShell para ver información sobre los planes de licencias, los servicios y las licencias disponibles en su organización de Microsoft 365.
ms.openlocfilehash: f0b7d6cd5981bec09e7773d10d82ff81c0f34d4e
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230216"
---
# <a name="view-microsoft-365-licenses-and-services-with-powershell"></a>Ver licencias y servicios de Microsoft 365 con PowerShell

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Todas las suscripciones de Microsoft 365 constan de los siguientes elementos:

- **Planes de licencias** También se conocen como planes de licencia o planes de 365 de Microsoft. Los planes de licencias definen los servicios de Microsoft 365 que están disponibles para los usuarios. Su suscripción a Microsoft 365 puede contener varios planes de licencias. Un plan de licencias de ejemplo sería Microsoft 365 E3.
    
- **Servicios** de También se conocen como planes de servicio. Los servicios son los productos, las características y las capacidades de Microsoft 365 que están disponibles en cada plan de licencias, por ejemplo, Exchange Online y Microsoft 365 apps for Enterprise (anteriormente denominado Office 365 ProPlus). Los usuarios pueden tener varias licencias asignadas que provengan de diferentes planes de licencias, y les permitan obtener acceso a diferentes servicios.
    
- **Licencias** Los planes de licencias contienen el número de licencias que haya adquirido. Las licencias se asignan a los usuarios para que puedan usar los servicios de Microsoft 365 definidos por el plan de licencias. Todas las cuentas de usuario requieren al menos una licencia de un plan de licencias para que puedan iniciar sesión en Microsoft 365 y usar los servicios.
    
Puede usar PowerShell para Microsoft 365 para ver detalles sobre los planes de licencias, las licencias y los servicios disponibles en su organización de Microsoft 365. Para obtener más información sobre los productos, las características y los servicios disponibles en las diferentes suscripciones de Office 365, consulte [Opciones de planes de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Para ver información resumida sobre los planes de licencias actuales y las licencias disponibles para cada plan, ejecute este comando:
  
```powershell
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Los resultados contienen:
  
- **SkuPartNumber:** Muestra los planes de licencias disponibles para su organización. Por ejemplo, `ENTERPRISEPACK` es el nombre del plan de licencias de Office 365 Enterprise E3.
    
- **Habilitado:** Número de licencias que ha comprado para un plan de licencias específico.
    
- **ConsumedUnits**: es el número de licencias asignadas a los usuarios de un plan de licencias específico.
    
Para ver información detallada sobre los servicios de Microsoft 365 que están disponibles en todos los planes de licencias, primero muestre una lista de los planes de licencia.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

A continuación, almacene la información de los planes de licencia en una variable.

```powershell
$licenses = Get-AzureADSubscribedSku
```

A continuación, muestre los servicios en un plan de licencias específico.

```powershell
$licenses[<index>].ServicePlans
```

\<index>es un entero que especifica el número de fila del plan de licencia desde la presentación del `Get-AzureADSubscribedSku | Select SkuPartNumber` comando, menos 1.

Por ejemplo, si la presentación del `Get-AzureADSubscribedSku | Select SkuPartNumber` comando es la siguiente:

```powershell
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
```

A continuación, el comando para mostrar los servicios del plan de licencias ENTERPRISEPREMIUM es el siguiente:

```powershell
$licenses[2].ServicePlans
```

ENTERPRISEPREMIUM es la tercera fila. Por lo tanto, el valor de índice es (3-1) o 2.

Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Hay un script de PowerShell que automatiza los procedimientos descritos en este tema. En concreto, el script permite ver y deshabilitar servicios en la organización de Microsoft 365, incluido Sway. Para obtener más información, vea [deshabilitar el acceso a Sway con PowerShell](disable-access-to-sway-with-office-365-powershell.md).
>
    
Para ver información resumida sobre los planes de licencias actuales y las licencias disponibles para cada plan, ejecute el siguiente comando:
  
```powershell
Get-MsolAccountSku
```

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

Los resultados contienen la siguiente información:
  
- **AccountSkuId:** Mostrar los planes de licencias disponibles para la organización mediante la sintaxis `<CompanyName>:<LicensingPlan>` .  _\<CompanyName>_ es el valor que proporcionó cuando se inscribió en Microsoft 365 y es único para su organización. El valor _\<LicensingPlan>_ es el mismo para todos los usuarios. Por ejemplo, en el valor `litwareinc:ENTERPRISEPACK`, el nombre de la empresa es  `litwareinc` y el nombre del plan de licencias, `ENTERPRISEPACK`, que es el nombre de sistema para Office 365 Enterprise E3.
    
- **ActiveUnits:** Número de licencias que ha comprado para un plan de licencias específico.
    
- **WarningUnits**: número de licencias de un plan de licencias que no renovó y que expirarán al finalizar los 30 días del período de gracia.
    
- **ConsumedUnits**: es el número de licencias asignadas a los usuarios de un plan de licencias específico.
    
Para ver información detallada sobre los servicios de Microsoft 365 que están disponibles en todos los planes de licencia, ejecute el siguiente comando:
  
```powershell
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

En la siguiente tabla se muestran los planes de servicio de Microsoft 365 y sus nombres descriptivos para los servicios más comunes. Su lista de planes de servicio puede ser diferente. 
  
|**Plan de servicio**|**Descripción**|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Microsoft 365 apps for Enterprise *(anteriormente denominado Office 365 ProPlus)*  <br/> |
| `MCOSTANDARD` <br/> |Skype Empresarial Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plan 2 de Exchange Online  <br/> |
   
Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Para ver información detallada sobre los servicios de Microsoft 365 que están disponibles en un plan de licencias específico, use la siguiente sintaxis.
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

En este ejemplo se muestran los servicios que están disponibles en el plan de licencias litwareinc: ENTERPRISEPACK (Office 365 Enterprise E3).
  
```powershell
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```

## <a name="see-also"></a>Consulte también

[Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)
