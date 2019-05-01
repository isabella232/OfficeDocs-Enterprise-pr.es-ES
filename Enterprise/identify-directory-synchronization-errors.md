---
title: Ver errores de sincronización de directorios en Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Obtenga información sobre cómo ver los errores de sincronización de directorios en el centro de administración de Microsoft 365.
ms.openlocfilehash: 8450c2e26c9c9ae194be46d81018a20c91e35f29
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491276"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="f6c62-103">Ver errores de sincronización de directorios en Office 365</span><span class="sxs-lookup"><span data-stu-id="f6c62-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="f6c62-104">Puede ver los errores de sincronización de directorios en el [centro de administración de Microsoft 365](https://admin.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="f6c62-104">You can view directory synchronization errors in the [Microsoft 365 admin center](https://admin.microsoft.com).</span></span> <span data-ttu-id="f6c62-105">Solo se muestran los errores del objeto de usuario.</span><span class="sxs-lookup"><span data-stu-id="f6c62-105">Only the User object errors are displayed.</span></span> <span data-ttu-id="f6c62-106">Para ver los errores con PowerShell, consulte [identificar objetos con DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span><span class="sxs-lookup"><span data-stu-id="f6c62-106">To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).</span></span>

<span data-ttu-id="f6c62-107">Después de ver, vea [solucionar problemas con la sincronización de directorios para Office 365](fix-problems-with-directory-synchronization.md) para corregir los problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="f6c62-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="f6c62-108">Ver los errores de sincronización de directorios en el centro de administración</span><span class="sxs-lookup"><span data-stu-id="f6c62-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="f6c62-109">Para ver los errores en el centro de administración:</span><span class="sxs-lookup"><span data-stu-id="f6c62-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="f6c62-110">Inicie sesión en Office 365 con su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="f6c62-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="f6c62-111">Vaya a la [información acerca del centro de administración](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="f6c62-111">Go to the [About the admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="f6c62-112">En la página **principal** , verá el icono de **Estado de sincronización de directorios** .</span><span class="sxs-lookup"><span data-stu-id="f6c62-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![Icono de estado de sincronización de directorios de la versión preliminar del centro de administración](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="f6c62-114">En el mosaico, seleccione **Estado** de sincronización de directorios para ir a la página **Estado de sincronización de directorios** .</span><span class="sxs-lookup"><span data-stu-id="f6c62-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="f6c62-115">En la parte inferior de la página puede ver si hay errores de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="f6c62-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![En la página estado de sincronización de directorios puede ver si hay errores de objetos dirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="f6c62-117">Elija **encontramos errores de objeto** de sincronización de directorios para ir a una vista detallada de los errores de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="f6c62-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="f6c62-118">También puede ir a la página **errores de sincronización de directorios** si elige que **se encuentren errores de objeto de sincronización** de directorios en el icono Estado de sincronización de **directorios** .</span><span class="sxs-lookup"><span data-stu-id="f6c62-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Página de errores de sincronización de directorios](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="f6c62-120">En la página **errores de sincronización de directorios** , elija cualquiera de los errores enumerados para mostrar el panel de detalles con información sobre el error y sugerencias sobre cómo solucionarlo.</span><span class="sxs-lookup"><span data-stu-id="f6c62-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
