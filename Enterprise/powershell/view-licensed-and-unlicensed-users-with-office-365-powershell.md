---
title: Ver los usuarios con licencia y sin licencia con PowerShell de Office 365
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Se explica cómo usar PowerShell de Office 365 para ver las cuentas de usuario con licencia y sin licencia.
ms.openlocfilehash: 61f94664a62b6a5cb178579c1a5777b208d0b2ec
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123367"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="e10ca-103">Ver los usuarios con licencia y sin licencia con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="e10ca-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="e10ca-104">**Resumen:** se explica cómo usar PowerShell de Office 365 para ver las cuentas de usuario con licencia y sin licencia.</span><span class="sxs-lookup"><span data-stu-id="e10ca-104">**Summary:** Explains how to use Office 365 PowerShell to view licensed and unlicensed user accounts.</span></span>
  
<span data-ttu-id="e10ca-p101">Las cuentas de usuario de la organización de Office 365 pueden tener algunas, todas o ninguna de las licencias disponibles asignadas a ellas desde los planes de licencias que están disponibles en su organización. Puede usar PowerShell de Office 365 para encontrar rápidamente los usuarios con licencia y sin licencia de la organización.</span><span class="sxs-lookup"><span data-stu-id="e10ca-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="e10ca-107">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="e10ca-107">Before you begin</span></span>

- <span data-ttu-id="e10ca-p102">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e10ca-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="e10ca-110">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="e10ca-110">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="viewing-licensed-and-unlicensed-users"></a><span data-ttu-id="e10ca-111">Visualización de los usuarios con licencia y sin licencia</span><span class="sxs-lookup"><span data-stu-id="e10ca-111">Viewing licensed and unlicensed users</span></span>

<span data-ttu-id="e10ca-112">Para ver la lista de todas las cuentas de usuario y su estado de licencias en la organización, ejecute el comando siguiente en PowerShell de Office 365:</span><span class="sxs-lookup"><span data-stu-id="e10ca-112">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```
Get-MsolUser -All
```

<span data-ttu-id="e10ca-113">Para ver la lista de todas las cuentas de usuario sin licencia de su organización, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="e10ca-113">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="e10ca-114">Para ver la lista de todas las cuentas de usuario con licencia de su organización, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="e10ca-114">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="e10ca-115">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e10ca-115">See also</span></span>

<span data-ttu-id="e10ca-116">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="e10ca-116">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="e10ca-117">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="e10ca-117">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="e10ca-118">Where-Object</span><span class="sxs-lookup"><span data-stu-id="e10ca-118">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

