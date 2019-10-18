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
# <a name="create-an-office-365-group-with-a-specific-pdl"></a><span data-ttu-id="3a8d7-103">Crear un grupo de Office 365 con un PDL específico</span><span class="sxs-lookup"><span data-stu-id="3a8d7-103">Create an Office 365 Group with a specific PDL</span></span>

<span data-ttu-id="3a8d7-104">Cuando los usuarios en un entorno multigeográfico crean un grupo de Office 365, la ubicación de datos preferida del grupo se establece automáticamente según la del usuario.</span><span class="sxs-lookup"><span data-stu-id="3a8d7-104">When users in a multi-geo environment create an Office 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="3a8d7-105">Si necesita crear un grupo con un PDL específico, puede hacerlo mediante el cmdlet de Microsoft PowerShell New-UnifiedGroup de Exchange Online.</span><span class="sxs-lookup"><span data-stu-id="3a8d7-105">If you need to create a group with a specific PDL, you can do that using the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="3a8d7-106">Al hacerlo, tanto el buzón del grupo como el sitio de SharePoint asociado con el grupo se aprovisionarán en el PDL especificado.</span><span class="sxs-lookup"><span data-stu-id="3a8d7-106">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="3a8d7-107">Debe ser un administrador global o un administrador de SharePoint Online o de Exchange Online para realizar estas acciones.</span><span class="sxs-lookup"><span data-stu-id="3a8d7-107">You must be a global administrator or a SharePoint Online or Exchange Online administrator to do this.</span></span>

<span data-ttu-id="3a8d7-108">Para crear un grupo de Office 365 con el PDL que especifique, conéctese al PowerShell de Exchange Online y pase el parámetro *-MailBoxRegion* con el código de ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="3a8d7-108">To create an Office 365 Group with the PDL that you specify, connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="3a8d7-109">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="3a8d7-109">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Captura de pantalla del cmdlet de PowerShell New-UnifiedGroup con la sintaxis](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="3a8d7-111">Tenga en cuenta que el aprovisionamiento de sitios de grupo de SharePoint se realiza a petición.</span><span class="sxs-lookup"><span data-stu-id="3a8d7-111">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="3a8d7-112">El sitio se aprovisionará la primera vez que un propietario o miembro del grupo intente acceder a él.</span><span class="sxs-lookup"><span data-stu-id="3a8d7-112">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="3a8d7-113">Códigos de ubicación geográfica</span><span class="sxs-lookup"><span data-stu-id="3a8d7-113">Geo location codes</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="3a8d7-114">Vea también</span><span class="sxs-lookup"><span data-stu-id="3a8d7-114">See also</span></span>

[<span data-ttu-id="3a8d7-115">Conectarse a Exchange Online mediante PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a8d7-115">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)