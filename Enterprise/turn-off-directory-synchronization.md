---
title: Desactivar la sincronización de directorios para Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
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
ms.openlocfilehash: 4fbfb6b9e3fcb1512fc4aa9c3d8ee6c37682e58a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085079"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="6bcc0-103">Desactivar la sincronización de directorios para Office 365</span><span class="sxs-lookup"><span data-stu-id="6bcc0-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="6bcc0-p101">Puede usar PowerShell para desactivar la sincronización de directorios. Sin embargo, no se recomienda desactivar la sincronización de directorios como un paso de solución de problemas. Si necesita ayuda para solucionar problemas de la sincronización de directorios, consulte el artículo [solución de problemas con la sincronización de directorios para Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="6bcc0-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="6bcc0-107">[Póngase en contacto con el soporte técnico](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para productos empresariales si es necesario.</span><span class="sxs-lookup"><span data-stu-id="6bcc0-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="6bcc0-108">Desactivar la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="6bcc0-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="6bcc0-109">Para desactivar la sincronización de directorios:</span><span class="sxs-lookup"><span data-stu-id="6bcc0-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="6bcc0-p102">En primer lugar, instale el software necesario y conéctese a su suscripción de Office 365. Para obtener instrucciones para ambos, vea [conectarse a PowerShell de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="6bcc0-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="6bcc0-112">Use [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para deshabilitar la sincronización de directorios:</span><span class="sxs-lookup"><span data-stu-id="6bcc0-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```