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
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Obtenga información sobre cómo usar PowerShell para desactivar la sincronización de Active directory para Office 365
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542935"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a><span data-ttu-id="a6d3d-103">Desactivar la sincronización de directorios para Office 365</span><span class="sxs-lookup"><span data-stu-id="a6d3d-103">Turn off directory synchronization for Office 365</span></span>
<span data-ttu-id="a6d3d-p101">Puede usar PowerShell para desactivar la sincronización de Active directory. Sin embargo, no se recomienda desactivar la sincronización de Active directory como un paso de solución de problemas. Si necesita ayuda con la solución de problemas de sincronización de directorios, vea el artículo de [fijación de problemas con la sincronización de Active directory para Office 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="a6d3d-p101">You can use PowerShell to turn off directory synchronization. However, it is not recommended that you turn off directory synchronization as a troubleshooting step. If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="a6d3d-107">[Contactar con el servicio](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para productos de negocio si es necesario.</span><span class="sxs-lookup"><span data-stu-id="a6d3d-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="a6d3d-108">Desactivar la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="a6d3d-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="a6d3d-109">Para desactivar la sincronización de directorios:</span><span class="sxs-lookup"><span data-stu-id="a6d3d-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="a6d3d-p102">En primer lugar, instale el software necesario y conectarse a su suscripción de Office 365. Para obtener instrucciones para ambos, vea [conectarse a Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span><span class="sxs-lookup"><span data-stu-id="a6d3d-p102">First, install the required software and connect to your Office 365 subscription. For instructions for both, see [connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).</span></span>
    
2. <span data-ttu-id="a6d3d-112">Usar [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para deshabilitar la sincronización de directorios:</span><span class="sxs-lookup"><span data-stu-id="a6d3d-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```