---
title: Desactivar la sincronización de directorios para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Obtenga información sobre cómo usar PowerShell para desactivar la sincronización de directorios para Microsoft 365
ms.openlocfilehash: 1e3e26a262c112c05fe22cda2dbe3f14efb61f87
ms.sourcegitcommit: c1a1b028195342affe0f3367db4e79c42429582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "45387713"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a><span data-ttu-id="230a4-103">Desactivar la sincronización de directorios para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="230a4-103">Turn off directory synchronization for Microsoft 365</span></span>
<span data-ttu-id="230a4-104">Puede usar PowerShell para desactivar la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="230a4-104">You can use PowerShell to turn off directory synchronization.</span></span> <span data-ttu-id="230a4-105">Sin embargo, no se recomienda desactivar la sincronización de directorios como un paso de solución de problemas.</span><span class="sxs-lookup"><span data-stu-id="230a4-105">However, it is not recommended that you turn off directory synchronization as a troubleshooting step.</span></span> <span data-ttu-id="230a4-106">Si necesita ayuda para solucionar problemas de la sincronización de directorios, consulte el artículo [solución de problemas con la sincronización de directorios para Microsoft 365](fix-problems-with-directory-synchronization.md) .</span><span class="sxs-lookup"><span data-stu-id="230a4-106">If you need assistance with troubleshooting directory synchronization, see the [Fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) article.</span></span> 
  
<span data-ttu-id="230a4-107">[Póngase en contacto con el soporte técnico](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para productos empresariales si es necesario.</span><span class="sxs-lookup"><span data-stu-id="230a4-107">[Contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products if needed.</span></span>
  
## <a name="turn-off-directory-synchronization"></a><span data-ttu-id="230a4-108">Desactivar la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="230a4-108">Turn off directory synchronization</span></span>  
<span data-ttu-id="230a4-109">Para desactivar la sincronización de directorios:</span><span class="sxs-lookup"><span data-stu-id="230a4-109">To turn off Directory synchronization:</span></span>
  
1. <span data-ttu-id="230a4-110">En primer lugar, instale el software necesario y conéctese a su suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="230a4-110">First, install the required software and connect to your Microsoft 365 subscription.</span></span> <span data-ttu-id="230a4-111">Para obtener instrucciones, vea [conectarse con el módulo Microsoft Azure Active Directory para Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="230a4-111">For instructions, see [Connect with the Microsoft Azure Active Directory Module for Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
2. <span data-ttu-id="230a4-112">Use [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para deshabilitar la sincronización de directorios:</span><span class="sxs-lookup"><span data-stu-id="230a4-112">Use [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) to disable directory synchronization:</span></span> 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
><span data-ttu-id="230a4-113">Si usa este comando, debe esperar 72 horas para poder volver a activar la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="230a4-113">If you use this command, you must wait 72 hours before you can turn directory synchronization back on.</span></span>
>
 
