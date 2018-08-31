---
title: Ver el estado de sincronización de directorios en Office 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Obtenga información sobre cómo desactivar la sincronización de Active directory. También puede ver su estado.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22543009"
---
# <a name="view-directory-synchronization-status-in-office-365"></a><span data-ttu-id="e7976-104">Ver el estado de sincronización de directorios en Office 365</span><span class="sxs-lookup"><span data-stu-id="e7976-104">View directory synchronization status in Office 365</span></span>
<span data-ttu-id="e7976-105">Si ha integrado su Active Directory local con Azure AD mediante la sincronización de su entorno local con Office 365, también puede comprobar el estado de la sincronización.</span><span class="sxs-lookup"><span data-stu-id="e7976-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Office 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="e7976-106">Ver el estado de sincronización de Active directory</span><span class="sxs-lookup"><span data-stu-id="e7976-106">View directory synchronization status</span></span>
- <span data-ttu-id="e7976-107">Inicie sesión en el centro de administración de Office 365 y elegir el **Estado de sincronización de directorios** en la página principal.</span><span class="sxs-lookup"><span data-stu-id="e7976-107">Sign in to the Office 365 admin center and choose **DirSync Status** on the home page.</span></span> 
- <span data-ttu-id="e7976-p102">Como alternativa, puede ir a **los usuarios** \> **usuarios activos**y en la página **usuarios activos** , elija **más** \> **sincronización de Active Directory**. En el panel de la **Sincronización de directorios** , elija **Ir a la administración de sincronización de directorios**.</span><span class="sxs-lookup"><span data-stu-id="e7976-p102">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**. On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>
    
## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="e7976-110">Obtener información acerca de la página de sincronización de directorios de administrar</span><span class="sxs-lookup"><span data-stu-id="e7976-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="e7976-111">En la siguiente tabla se enumera las características que se puede obtener información acerca de la página.</span><span class="sxs-lookup"><span data-stu-id="e7976-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="e7976-p103">Si hay un problema con la sincronización de directorios, los errores se enumeran en esta página también. Para obtener más información acerca de los diferentes errores que puedan surgir, consulte [identificar errores de sincronización de Active directory en Office 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="e7976-p103">If there is a problem with your directory synchronization, the errors are listed on this page as well. For more information about different errors you might encounter, see [Identify directory synchronization errors in Office 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="e7976-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="e7976-114">**Item**</span></span>|<span data-ttu-id="e7976-115">**¿Qué es**</span><span class="sxs-lookup"><span data-stu-id="e7976-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="e7976-116">**Dominios comprobados**</span><span class="sxs-lookup"><span data-stu-id="e7976-116">**Domains verified**</span></span> | <span data-ttu-id="e7976-117">Número de dominios en el inquilino de Office 365 que haya comprobado posee.</span><span class="sxs-lookup"><span data-stu-id="e7976-117">Number of domains in your Office 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="e7976-118">**Dominios no comprobados**</span><span class="sxs-lookup"><span data-stu-id="e7976-118">**Domains not verified**</span></span> | <span data-ttu-id="e7976-119">Dominios ha agregado, pero no se ha comprobado.</span><span class="sxs-lookup"><span data-stu-id="e7976-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="e7976-120">**Sincronización de Active Directory habilitado**</span><span class="sxs-lookup"><span data-stu-id="e7976-120">**Directory sync enabled**</span></span> |<span data-ttu-id="e7976-p104">True o False. Especifica si ha habilitado la sincronización de Active directory.</span><span class="sxs-lookup"><span data-stu-id="e7976-p104">True or False. Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="e7976-123">**Última sincronización de Active directory**</span><span class="sxs-lookup"><span data-stu-id="e7976-123">**Latest directory sync**</span></span> | <span data-ttu-id="e7976-p105">Última vez que se ejecutó la sincronización de Active directory. Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización se ha hace más de tres días.</span><span class="sxs-lookup"><span data-stu-id="e7976-p105">Last time directory sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="e7976-126">**Habilitado para la sincronización de contraseñas**</span><span class="sxs-lookup"><span data-stu-id="e7976-126">**Password sync enabled**</span></span> | <span data-ttu-id="e7976-p106">True o False. Especifica si tienen sincronización de hash de contraseña entre nuestra local y su inquilino de Office 365.</span><span class="sxs-lookup"><span data-stu-id="e7976-p106">True or False. Specifies whether you have password hash sync between our on-premises and your Office 365 tenant.</span></span> |
|<span data-ttu-id="e7976-129">**Última sincronización de contraseñas**</span><span class="sxs-lookup"><span data-stu-id="e7976-129">**Last Password Sync**</span></span> | <span data-ttu-id="e7976-p107">Última vez que se ejecutó la sincronización de contraseñas hash. Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización se ha hace más de tres días.</span><span class="sxs-lookup"><span data-stu-id="e7976-p107">Last time password hash sync ran. Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="e7976-132">**Versión de cliente de sincronización de Active Directory**</span><span class="sxs-lookup"><span data-stu-id="e7976-132">**Directory sync client version**</span></span> | <span data-ttu-id="e7976-133">Contiene un vínculo de descarga si se ha publicado una nueva versión de Azure Connect de AD.</span><span class="sxs-lookup"><span data-stu-id="e7976-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="e7976-134">**Herramienta IDFix**</span><span class="sxs-lookup"><span data-stu-id="e7976-134">**IDFix Tool**</span></span> | <span data-ttu-id="e7976-135">Vínculo de descarga para [IDFix](install-and-run-idfix.md), una herramienta que puede utilizar para proteger Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="e7976-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="e7976-136">**Cuenta de servicio de sincronización de Active Directory**</span><span class="sxs-lookup"><span data-stu-id="e7976-136">**Directory sync service account**</span></span> | <span data-ttu-id="e7976-137">Muestra el nombre de la que cuenta de servicio de sincronización de directorios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="e7976-137">Displays the name of you Office 365 directory sync service account.</span></span> |