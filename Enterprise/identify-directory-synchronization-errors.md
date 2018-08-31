---
title: Ver errores de sincronización de Active directory en Office 365
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
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Obtenga información sobre cómo ver los errores de sincronización de Active directory en el centro de administración de Office 365.
ms.openlocfilehash: 62f1135568261eccf0e7e66b78c5aaff966c7281
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542851"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a><span data-ttu-id="6b8e6-103">Ver errores de sincronización de Active directory en Office 365</span><span class="sxs-lookup"><span data-stu-id="6b8e6-103">View directory synchronization errors in Office 365</span></span>

<span data-ttu-id="6b8e6-p101">Puede ver los errores de sincronización de Active directory en el centro de administración de Office 365. Se muestran sólo los errores del objeto de usuario. Para ver los errores mediante el uso de PowerShell, vea [identificar objetos con DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).</span><span class="sxs-lookup"><span data-stu-id="6b8e6-p101">You can view directory synchronization errors in the Office 365 admin center. Only the User object errors are displayed. To view errors by using PowerShell, see [Identify objects with DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).</span></span>

<span data-ttu-id="6b8e6-107">Después de visualización, vea [solución de problemas con la sincronización de Active directory para Office 365](fix-problems-with-directory-synchronization.md) para corregir los problemas identificados.</span><span class="sxs-lookup"><span data-stu-id="6b8e6-107">After viewing, see [fixing problems with directory synchronization for Office 365](fix-problems-with-directory-synchronization.md) to correct any identified issues.</span></span>
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a><span data-ttu-id="6b8e6-108">Ver errores de sincronización de Active directory en el centro de administración</span><span class="sxs-lookup"><span data-stu-id="6b8e6-108">View directory synchronization errors in the admin center</span></span>

<span data-ttu-id="6b8e6-109">Para ver los errores en el centro de administración:</span><span class="sxs-lookup"><span data-stu-id="6b8e6-109">To view any errors in the admin center:</span></span>
  
1. <span data-ttu-id="6b8e6-110">Inicie sesión en Office 365 con su cuenta profesional o educativa.</span><span class="sxs-lookup"><span data-stu-id="6b8e6-110">Sign in to Office 365 with your work or school account.</span></span> 
    
2. <span data-ttu-id="6b8e6-111">Vaya al [Centro de administración de acerca de Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span><span class="sxs-lookup"><span data-stu-id="6b8e6-111">Go to the [About the Office 365 admin center](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).</span></span>
    
3. <span data-ttu-id="6b8e6-112">En la página **principal** , verá el icono de **Estado de sincronización de directorios** .</span><span class="sxs-lookup"><span data-stu-id="6b8e6-112">On the **Home** page you will see the **DirSync Status** tile.</span></span> 
    
    ![El estado de sincronización de directorios en mosaico en la vista previa del centro de administración](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. <span data-ttu-id="6b8e6-114">En el icono, elija el **Estado de sincronización de directorios** para ir a la página de **Estado de la sincronización de Active Directory** .</span><span class="sxs-lookup"><span data-stu-id="6b8e6-114">On the tile, choose **DirSync Status** to go to the **Directory Sync Status** page.</span></span> 
    
    <span data-ttu-id="6b8e6-115">En la parte inferior de la página puede ver si hay errores de sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="6b8e6-115">On the bottom of the page you can see if there are DirSync errors.</span></span>
    
    ![En la página de estado de la sincronización de Active Directory puede ver si hay errores de objeto de sincronización de directorios](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    <span data-ttu-id="6b8e6-117">Elija **se encuentra errores de objeto de sincronización de directorios** para ir a una vista detallada de los errores de sincronización de Active directory.</span><span class="sxs-lookup"><span data-stu-id="6b8e6-117">Choose **We found DirSync object errors** to go to a detailed view of the directory synchronization errors.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="6b8e6-118">También puede ir a la página de **errores de sincronización de directorios** si elige **se encuentra errores de objeto de sincronización de directorios** en el icono de **estado de sincronización de directorios** .</span><span class="sxs-lookup"><span data-stu-id="6b8e6-118">You can also go to the **DirSync errors** page if you choose **We found DirSync object errors** on the **DirSync status** tile.</span></span> 
  
![Página de errores de sincronización de directorios](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. <span data-ttu-id="6b8e6-120">En la página de **errores de sincronización de directorios** , elija cualquiera de los errores que se enumeran para mostrar el panel de detalles con información sobre los errores y sugerencias sobre cómo corregirlo.</span><span class="sxs-lookup"><span data-stu-id="6b8e6-120">On the **DirSync errors** page, choose any of the errors listed to display the details pane with information about the error and tips on how to fix it.</span></span> 
