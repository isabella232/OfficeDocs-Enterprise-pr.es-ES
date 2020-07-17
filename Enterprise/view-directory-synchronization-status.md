---
title: Ver el estado de sincronización de directorios en Microsoft 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Obtenga información sobre cómo desactivar la sincronización de directorios. También puede ver su estado.
ms.openlocfilehash: d6f3a9f1f4e069716501f58e188daedacbf7e597
ms.sourcegitcommit: 0f7607b5e88b78ae250900ce7ce1b019cd245aa1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2020
ms.locfileid: "44906203"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="c69c7-104">Ver el estado de sincronización de directorios en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="c69c7-104">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="c69c7-105">Si ha integrado su Active Directory local con Azure AD mediante la sincronización del entorno local con Microsoft 365, también puede comprobar el estado de la sincronización.</span><span class="sxs-lookup"><span data-stu-id="c69c7-105">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="c69c7-106">Ver el estado de sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="c69c7-106">View directory synchronization status</span></span>

- <span data-ttu-id="c69c7-107">Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) y elija **Estado de sincronización de directorios** en la Página principal.</span><span class="sxs-lookup"><span data-stu-id="c69c7-107">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="c69c7-108">Como alternativa, puede **ir a usuarios** \> **activos**y, en la página **usuarios activos** , elija **más** \> **sincronización de directorios**.</span><span class="sxs-lookup"><span data-stu-id="c69c7-108">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="c69c7-109">En el panel **sincronización de directorios** , elija **ir a administración de sincronización**de directorios.</span><span class="sxs-lookup"><span data-stu-id="c69c7-109">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="c69c7-110">Información en la página administrar la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="c69c7-110">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="c69c7-111">En la siguiente tabla se enumeran las características a las que puede obtener información en la página.</span><span class="sxs-lookup"><span data-stu-id="c69c7-111">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="c69c7-112">Si hay un problema con la sincronización de directorios, los errores también se enumeran en esta página.</span><span class="sxs-lookup"><span data-stu-id="c69c7-112">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="c69c7-113">Para obtener más información acerca de los diferentes errores que se pueden encontrar, consulte [identificar errores de sincronización de directorios en Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="c69c7-113">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="c69c7-114">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="c69c7-114">**Item**</span></span>|<span data-ttu-id="c69c7-115">**Para qué sirve**</span><span class="sxs-lookup"><span data-stu-id="c69c7-115">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="c69c7-116">**Dominios comprobados**</span><span class="sxs-lookup"><span data-stu-id="c69c7-116">**Domains verified**</span></span> | <span data-ttu-id="c69c7-117">Número de dominios de su inquilino de Microsoft 365 que ha comprobado que es el propietario.</span><span class="sxs-lookup"><span data-stu-id="c69c7-117">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="c69c7-118">**Dominios no comprobados**</span><span class="sxs-lookup"><span data-stu-id="c69c7-118">**Domains not verified**</span></span> | <span data-ttu-id="c69c7-119">Dominios que ha agregado, pero no comprobado.</span><span class="sxs-lookup"><span data-stu-id="c69c7-119">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="c69c7-120">**Sincronización de directorios habilitada**</span><span class="sxs-lookup"><span data-stu-id="c69c7-120">**Directory sync enabled**</span></span> |<span data-ttu-id="c69c7-121">True o false.</span><span class="sxs-lookup"><span data-stu-id="c69c7-121">True or False.</span></span> <span data-ttu-id="c69c7-122">Especifica si ha habilitado la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="c69c7-122">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="c69c7-123">**Sincronización de directorios más reciente**</span><span class="sxs-lookup"><span data-stu-id="c69c7-123">**Latest directory sync**</span></span> | <span data-ttu-id="c69c7-124">Última vez que se ejecutó la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="c69c7-124">Last time directory sync ran.</span></span> <span data-ttu-id="c69c7-125">Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización fue de hace más de tres días.</span><span class="sxs-lookup"><span data-stu-id="c69c7-125">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="c69c7-126">**Sincronización de contraseñas habilitada**</span><span class="sxs-lookup"><span data-stu-id="c69c7-126">**Password sync enabled**</span></span> | <span data-ttu-id="c69c7-127">True o false.</span><span class="sxs-lookup"><span data-stu-id="c69c7-127">True or False.</span></span> <span data-ttu-id="c69c7-128">Especifica si la sincronización de hash de contraseña entre nuestro entorno local y su inquilino de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c69c7-128">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="c69c7-129">**Última sincronización de contraseñas**</span><span class="sxs-lookup"><span data-stu-id="c69c7-129">**Last Password Sync**</span></span> | <span data-ttu-id="c69c7-130">Última vez que se ejecutó la sincronización hash de contraseña.</span><span class="sxs-lookup"><span data-stu-id="c69c7-130">Last time password hash sync ran.</span></span> <span data-ttu-id="c69c7-131">Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización fue de hace más de tres días.</span><span class="sxs-lookup"><span data-stu-id="c69c7-131">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="c69c7-132">**Versión del cliente de sincronización de directorios**</span><span class="sxs-lookup"><span data-stu-id="c69c7-132">**Directory sync client version**</span></span> | <span data-ttu-id="c69c7-133">Contiene un vínculo de descarga si se ha lanzado una nueva versión de Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="c69c7-133">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="c69c7-134">**Herramienta IDFix**</span><span class="sxs-lookup"><span data-stu-id="c69c7-134">**IDFix Tool**</span></span> | <span data-ttu-id="c69c7-135">Vínculo de descarga a [IDFix](install-and-run-idfix.md), una herramienta que puede usar para comprobar Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="c69c7-135">Download link to [IDFix](install-and-run-idfix.md), a tool you can use to check you local Active Directory.</span></span> |
|<span data-ttu-id="c69c7-136">**Cuenta del servicio de sincronización de directorios**</span><span class="sxs-lookup"><span data-stu-id="c69c7-136">**Directory sync service account**</span></span> | <span data-ttu-id="c69c7-137">Muestra el nombre de la cuenta del servicio de sincronización de directorios de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c69c7-137">Displays the name of your Microsoft 365 directory sync service account.</span></span> |