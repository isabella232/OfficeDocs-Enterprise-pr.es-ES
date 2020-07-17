---
title: Ver los errores de sincronización de directorios en Microsoft 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Obtenga información sobre cómo ver los errores de sincronización de directorios en el centro de administración de Microsoft 365.
ms.openlocfilehash: 57ca9ce125679931adcca93621474cec9ee9b82f
ms.sourcegitcommit: 3349fdaff646f5f7d92c22565402dfc22c12d2ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2020
ms.locfileid: "44842094"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a><span data-ttu-id="50809-103">Ver los errores de sincronización de directorios en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="50809-103">View directory synchronization errors in Microsoft 365</span></span>

<span data-ttu-id="50809-104">Puede ver los errores de sincronización de directorios en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="50809-104">You can view directory synchronization errors in the Microsoft 365 admin center.</span></span> <span data-ttu-id="50809-105">Solo se muestran los errores del objeto de usuario.</span><span class="sxs-lookup"><span data-stu-id="50809-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="50809-106">Para ver errores con PowerShell, consulte [identificar objetos con DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="50809-106">To view errors with PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a><span data-ttu-id="50809-107">Ver los errores de sincronización de directorios en el centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="50809-107">View directory synchronization errors in the Microsoft 365 admin center</span></span>

<span data-ttu-id="50809-108">Para ver los errores en el centro de administración de Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="50809-108">To view any errors in the Microsoft 365 admin center:</span></span>
  
1. <span data-ttu-id="50809-109">Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) con una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="50809-109">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) with a global administrator account.</span></span> 
    
2. <span data-ttu-id="50809-110">En la página **principal** , verá la tarjeta de **Administración de usuarios** .</span><span class="sxs-lookup"><span data-stu-id="50809-110">On the **Home** page, you'll see the **User management** card.</span></span> 
    
    ![La tarjeta de administración de usuarios en el centro de administración de Microsoft 365](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. <span data-ttu-id="50809-112">En la tarjeta, elija **sincronizar errores** en **Azure ad Connect** para ver los errores en la página de **errores de sincronización de directorios** .</span><span class="sxs-lookup"><span data-stu-id="50809-112">On the card, choose **Sync errors** under **Azure AD Connect** to see the errors on the **Directory sync errors** page.</span></span>   
    
    ![Un ejemplo de la página de errores de sincronización de directorios](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. <span data-ttu-id="50809-114">Elija cualquiera de los errores para mostrar el panel de detalles con información sobre el error y sugerencias sobre cómo solucionarlo.</span><span class="sxs-lookup"><span data-stu-id="50809-114">Choose any of the errors to display the details pane with information about the error and tips on how to fix it.</span></span>

   ![Ejemplo de los detalles de un error de sincronización de directorios](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
<span data-ttu-id="50809-116">Después de ver, vea [solucionar problemas con la sincronización de directorios para Microsoft 365](fix-problems-with-directory-synchronization.md) para corregir los problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="50809-116">After viewing, see [fixing problems with directory synchronization for Microsoft 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>

