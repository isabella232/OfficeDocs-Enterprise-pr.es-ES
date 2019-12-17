---
title: Desactivar la sincronización de directorios en Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Obtenga información sobre cómo usar PowerShell para desactivar la sincronización de directorios para Office 365
ms.openlocfilehash: de7cfcbc11ed281e412c68674b808613b3421041
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072402"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="c8f9b-103">Desactivar la sincronización de directorios en Office 365</span><span class="sxs-lookup"><span data-stu-id="c8f9b-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="c8f9b-104">Puede usar PowerShell para desactivar la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="c8f9b-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="c8f9b-105">Sin embargo, no se recomienda desactivar la sincronización de directorios como un paso de solución de problemas.</span><span class="sxs-lookup"><span data-stu-id="c8f9b-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="c8f9b-106">Si necesita ayuda para solucionar problemas de la sincronización de directorios, consulte el artículo [solución de problemas con la sincronización de directorios para Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="c8f9b-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="c8f9b-107">[Póngase en contacto con el soporte técnico](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para productos empresariales si es necesario.</span><span class="sxs-lookup"><span data-stu-id="c8f9b-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="c8f9b-108">Desactivar la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="c8f9b-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="c8f9b-109">Para desactivar la sincronización de directorios:</span><span class="sxs-lookup"><span data-stu-id="c8f9b-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="c8f9b-110">En primer lugar, instale el software necesario y conéctese a su suscripción de Office 365.</span><span class="sxs-lookup"><span data-stu-id="c8f9b-110">First, install the required software and connect to your Office 365 subscription.</span></span> <span data-ttu-id="c8f9b-111">Para obtener instrucciones para ambos, vea [conectarse a PowerShell de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="c8f9b-111">For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="c8f9b-112">Use [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para deshabilitar la sincronización de directorios:</span><span class="sxs-lookup"><span data-stu-id="c8f9b-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```