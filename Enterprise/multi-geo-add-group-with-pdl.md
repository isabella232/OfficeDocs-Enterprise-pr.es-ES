---
title: Crear un grupo de Office 365 con un PDL específico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información sobre cómo crear un grupo de Office 365 con una ubicación de datos preferida especificada en un entorno multigeográfico.
ms.openlocfilehash: fb512478d69502eafd633b552d1db2acbec43ef4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070007"
---
# <a name="create-an-office-365-group-with-a-specific-pdl"></a>Crear un grupo de Office 365 con un PDL específico

Cuando los usuarios en un entorno multigeográfico crean un grupo de Office 365, la ubicación de datos preferida del grupo se establece automáticamente según la del usuario. Si necesita crear un grupo con un PDL específico, puede hacerlo mediante el cmdlet de Microsoft PowerShell New-UnifiedGroup de Exchange Online. Al hacerlo, tanto el buzón del grupo como el sitio de SharePoint asociado con el grupo se aprovisionarán en el PDL especificado.

Debe ser un administrador global o un administrador de SharePoint Online o de Exchange Online para realizar estas acciones.

Para crear un grupo de Office 365 con el PDL que especifique, conéctese al PowerShell de Exchange Online y pase el parámetro *-MailBoxRegion* con el código de ubicación geográfica.

Por ejemplo: 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Captura de pantalla del cmdlet de PowerShell New-UnifiedGroup con la sintaxis](media/multi-geo-new-group-with-pdl-powershell.png)

Tenga en cuenta que el aprovisionamiento de sitios de grupo de SharePoint se realiza a petición. El sitio se aprovisionará la primera vez que un propietario o miembro del grupo intente acceder a él.

## <a name="geo-location-codes"></a>Códigos de ubicación geográfica

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a>Vea también

[Conectarse a Exchange Online mediante PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)