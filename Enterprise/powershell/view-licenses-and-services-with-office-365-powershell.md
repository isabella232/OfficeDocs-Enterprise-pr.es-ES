---
title: Ver las licencias y los servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
description: Explica cómo usar PowerShell de Office 365 para ver información sobre los planes de licencias, los servicios y las licencias disponibles en su organización de Office 365.
ms.openlocfilehash: f673ac984e504a740dfac474821366d34de5ccbc
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730335"
---
# <a name="view-licenses-and-services-with-office-365-powershell"></a>Ver licencias y servicios con PowerShell de Office 365

**Resumen:** se explica cómo usar PowerShell de Office 365 para ver información sobre los planes de licencias, los servicios y las licencias disponibles en su organización de Office 365.
  
Todas las suscripciones de Office 365 se componen de estos elementos:

- **Planes de licencias** Estos son también conocido como planes de licencias o planes de Office 365. Planes de licencias definición los servicios de Office 365 que están disponibles para los usuarios. Su suscripción de Office 365 puede contener varios planes de licencias. Un plan de licencias de ejemplo sería E3 Enterprise de Office 365.
    
- **Servicios de** Estos son también conocido como planes de servicio. Servicios son los productos de Office 365, características y capacidades que están disponibles en cada plan de licencias, por ejemplo, Exchange Online y Office Professional Plus. Los usuarios pueden tener varias licencias asignadas a ellos desde distintos planes de licencias que concesión acceso a diferentes servicios.
    
- **Licencias** Los planes de licencias contienen el número de licencias que haya adquirido. Puede asignar licencias a los usuarios para que estos puedan usar los servicios de Office 365 definidos por el plan de licencias. Cada cuenta de usuario necesita como mínimo una licencia del plan de licencias para que el usuario correspondiente pueda iniciar sesión en Office 365 y usar los servicios.
    
Puede usar PowerShell de Office 365 para ver información detallada sobre los planes de licencias, las licencias y los servicios disponibles en su organización de Office 365. Para obtener más información sobre los productos, las características y los servicios disponibles en las diferentes suscripciones de Office 365, consulte [Opciones de planes de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=691147).


## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
Para ver información resumida acerca de los planes actuales de licencias y las licencias disponibles para cada plan, ejecute el siguiente comando:
  
```
Get-AzureADSubscribedSku | Select -Property Sku*,ConsumedUnits -ExpandProperty PrepaidUnits
```

Los resultados contienen la siguiente información:
  
- **SkuPartNumber:** Muestra los planes de licencias disponibles para su organización. Por ejemplo, `ENTERPRISEPACK` es el nombre del sistema para Office 365 Enterprise E3.
    
- **Habilitado:** Número de licencias que ha adquirido para un plan de licencias específico.
    
- **ConsumedUnits**: es el número de licencias asignadas a los usuarios de un plan de licencias específico.
    
Para ver detalles acerca de los que están disponibles en todos los planes de licencias de servicios de Office 365, mostrar en primer lugar una lista de los planes de licencia.

````
Get-AzureADSubscribedSku | Select SkuPartNumber
````

A continuación, almacene la información de licencia de planes en una variable.

````
$licenses = Get-AzureADSubscribedSku
````

A continuación, se muestran los servicios en un plan de licencias específicos.

````
$licenses[<index>].ServicePlan
````

\<Índice > es un número entero que especifica el número de fila del plan de licencia de la presentación de la `Get-AzureADSubscribedSku | Select SkuPartNumber` command, menos 1.

Por ejemplo, si la presentación de la `Get-AzureADSubscribedSku | Select SkuPartNumber` comando es esto:

````
SkuPartNumber
-------------
WIN10_VDA_E5
EMSPREMIUM
ENTERPRISEPREMIUM
FLOW_FREE
````

A continuación, el comando para mostrar los servicios para el plan de licencia ENTERPRISEPREMIUM es la siguiente:

````
$licenses[2].ServicePlan
````

ENTERPRISEPREMIUM es la tercera fila. Por lo tanto, es el valor de índice (3 - 1), o 2.

Para obtener una lista completa de los planes de licencia (también conocido como nombres de producto), sus planes de servicio incluido y sus correspondientes nombres descriptivos, vea [nombres de producto y los identificadores de plan de servicio para las licencias](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

>[!Note]
>Un script de PowerShell está disponible que automatiza los procedimientos descritos en este tema. En concreto, la secuencia de comandos le permite ver y deshabilitar los servicios de la organización de Office 365, incluidos balanceo. Para obtener más información, vea [Deshabilitar el acceso a balanceo con PowerShell de Office 365](disable-access-to-sway-with-office-365-powershell.md).
>
    
Para ver información resumida acerca de los planes actuales de licencias y las licencias disponibles para cada plan, ejecute el siguiente comando:
  
```
Get-MsolAccountSku
```

Los resultados contienen la siguiente información:
  
- **AccountSkuId:** se muestran los planes de licencias disponibles para su organización con la sintaxis `<CompanyName>:<LicensingPlan>`. _<CompanyName>_ es el valor que proporcionó al inscribirse en Office 365; se trata de un valor único para su organización. El valor _<LicensingPlan>_ es el mismo para todos los usuarios. Por ejemplo, en el valor `litwareinc:ENTERPRISEPACK`, el nombre de la compañía es `litwareinc` y el nombre del plan de licencias es `ENTERPRISEPACK` (que es el nombre del sistema para Office 365 Enterprise E3).
    
- **ActiveUnits:** Número de licencias que ha adquirido para un plan de licencias específico.
    
- **WarningUnits**: número de licencias de un plan de licencias que no renovó y que expirarán al finalizar los 30 días del período de gracia.
    
- **ConsumedUnits**: es el número de licencias asignadas a los usuarios de un plan de licencias específico.
    
Para ver información detallada sobre los servicios de Office 365 disponibles en todos sus planes de licencia, ejecute el comando siguiente:
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

La siguiente tabla muestran los planes de servicio de Office 365 y sus nombres descriptivos para los servicios más comunes. La lista de planes de servicio puede ser diferente. 
  
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
   
Para obtener una lista completa de los planes de licencia (también conocido como nombres de producto), sus planes de servicio incluido y sus correspondientes nombres descriptivos, vea [nombres de producto y los identificadores de plan de servicio para las licencias](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).

Para obtener información detallada sobre los servicios de Office 365 disponibles en un plan de licencias en concreto, use la sintaxis siguiente.
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "<AccountSkuId>"}).ServiceStatus
```

En este ejemplo se muestra los servicios de Office 365 que están disponibles en el plan de licencias litwareinc: enterprisepack (Office 365 Enterprise E3).
  
```
(Get-MsolAccountSku | where {$_.AccountSkuId -eq "litwareinc:ENTERPRISEPACK"}).ServiceStatus
```


## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Vea también


[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
