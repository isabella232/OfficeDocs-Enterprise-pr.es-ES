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
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: En este artículo, obtenga información acerca de cómo puede comprobar el estado de la sincronización de directorios en Office 365.
ms.openlocfilehash: 9aaad085854326ebb6542f03256ae851b27f0980
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605866"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a><span data-ttu-id="d469e-103">Ver el estado de sincronización de directorios en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d469e-103">View directory synchronization status in Microsoft 365</span></span>

<span data-ttu-id="d469e-104">Si ha integrado su Active Directory local con Azure AD mediante la sincronización del entorno local con Microsoft 365, también puede comprobar el estado de la sincronización.</span><span class="sxs-lookup"><span data-stu-id="d469e-104">If you have integrated your on-premises Active Directory with Azure AD by synchronizing your on-premises environment with Microsoft 365, you can also check the status of your synchronization.</span></span>
  
## <a name="view-directory-synchronization-status"></a><span data-ttu-id="d469e-105">Ver el estado de sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="d469e-105">View directory synchronization status</span></span>

- <span data-ttu-id="d469e-106">Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) y elija **Estado de sincronización de directorios** en la Página principal.</span><span class="sxs-lookup"><span data-stu-id="d469e-106">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com) and choose **DirSync Status** on the home page.</span></span>
- <span data-ttu-id="d469e-107">Como alternativa, puede **ir a usuarios** \> **activos**y, en la página **usuarios activos** , elija **más** \> **sincronización de directorios**.</span><span class="sxs-lookup"><span data-stu-id="d469e-107">Alternately, you can go to **Users** \> **Active users**, and on the **Active users** page, choose **More** \> **Directory synchronization**.</span></span> <span data-ttu-id="d469e-108">En el panel **sincronización de directorios** , elija **ir a administración de sincronización**de directorios.</span><span class="sxs-lookup"><span data-stu-id="d469e-108">On the **Directory Synchronization** pane, choose **Go to DirSync management**.</span></span>

## <a name="information-on-the-manage-directory-synchronization-page"></a><span data-ttu-id="d469e-109">Información en la página administrar la sincronización de directorios</span><span class="sxs-lookup"><span data-stu-id="d469e-109">Information on the Manage directory synchronization page</span></span>

<span data-ttu-id="d469e-110">En la siguiente tabla se enumeran las características a las que puede obtener información en la página.</span><span class="sxs-lookup"><span data-stu-id="d469e-110">The following table lists the features you can get information about on the page.</span></span>
  
<span data-ttu-id="d469e-111">Si hay un problema con la sincronización de directorios, los errores también se enumeran en esta página.</span><span class="sxs-lookup"><span data-stu-id="d469e-111">If there is a problem with your directory synchronization, the errors are listed on this page as well.</span></span> <span data-ttu-id="d469e-112">Para obtener más información acerca de los diferentes errores que se pueden encontrar, consulte [identificar errores de sincronización de directorios en Microsoft 365](identify-directory-synchronization-errors.md).</span><span class="sxs-lookup"><span data-stu-id="d469e-112">For more information about different errors you might encounter, see [Identify directory synchronization errors in Microsoft 365](identify-directory-synchronization-errors.md).</span></span>
  
|<span data-ttu-id="d469e-113">**Elemento**</span><span class="sxs-lookup"><span data-stu-id="d469e-113">**Item**</span></span>|<span data-ttu-id="d469e-114">**Para qué sirve**</span><span class="sxs-lookup"><span data-stu-id="d469e-114">**What it's for**</span></span>|
|:-----|:-----|
|<span data-ttu-id="d469e-115">**Dominios comprobados**</span><span class="sxs-lookup"><span data-stu-id="d469e-115">**Domains verified**</span></span> | <span data-ttu-id="d469e-116">Número de dominios de su inquilino de Microsoft 365 que ha comprobado que es el propietario.</span><span class="sxs-lookup"><span data-stu-id="d469e-116">Number of domains in your Microsoft 365 tenant that you have verified you own.</span></span> |
|<span data-ttu-id="d469e-117">**Dominios no comprobados**</span><span class="sxs-lookup"><span data-stu-id="d469e-117">**Domains not verified**</span></span> | <span data-ttu-id="d469e-118">Dominios que ha agregado, pero no comprobado.</span><span class="sxs-lookup"><span data-stu-id="d469e-118">Domains you have added, but not verified.</span></span> |
|<span data-ttu-id="d469e-119">**Sincronización de directorios habilitada**</span><span class="sxs-lookup"><span data-stu-id="d469e-119">**Directory sync enabled**</span></span> |<span data-ttu-id="d469e-120">True o false.</span><span class="sxs-lookup"><span data-stu-id="d469e-120">True or False.</span></span> <span data-ttu-id="d469e-121">Especifica si ha habilitado la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="d469e-121">Specifies whether you have enabled directory sync.</span></span> |
|<span data-ttu-id="d469e-122">**Sincronización de directorios más reciente**</span><span class="sxs-lookup"><span data-stu-id="d469e-122">**Latest directory sync**</span></span> | <span data-ttu-id="d469e-123">Última vez que se ejecutó la sincronización de directorios.</span><span class="sxs-lookup"><span data-stu-id="d469e-123">Last time directory sync ran.</span></span> <span data-ttu-id="d469e-124">Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización fue de hace más de tres días.</span><span class="sxs-lookup"><span data-stu-id="d469e-124">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="d469e-125">**Sincronización de contraseñas habilitada**</span><span class="sxs-lookup"><span data-stu-id="d469e-125">**Password sync enabled**</span></span> | <span data-ttu-id="d469e-126">True o false.</span><span class="sxs-lookup"><span data-stu-id="d469e-126">True or False.</span></span> <span data-ttu-id="d469e-127">Especifica si la sincronización de hash de contraseña entre nuestro entorno local y su inquilino de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d469e-127">Specifies whether you have password hash sync between our on-premises and your Microsoft 365 tenant.</span></span> |
|<span data-ttu-id="d469e-128">**Última sincronización de contraseñas**</span><span class="sxs-lookup"><span data-stu-id="d469e-128">**Last Password Sync**</span></span> | <span data-ttu-id="d469e-129">Última vez que se ejecutó la sincronización hash de contraseña.</span><span class="sxs-lookup"><span data-stu-id="d469e-129">Last time password hash sync ran.</span></span> <span data-ttu-id="d469e-130">Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización fue de hace más de tres días.</span><span class="sxs-lookup"><span data-stu-id="d469e-130">Will display a warning and a link to a troubleshooting tool if the last sync was more than three days ago.</span></span> |
|<span data-ttu-id="d469e-131">**Versión del cliente de sincronización de directorios**</span><span class="sxs-lookup"><span data-stu-id="d469e-131">**Directory sync client version**</span></span> | <span data-ttu-id="d469e-132">Contiene un vínculo de descarga si se ha lanzado una nueva versión de Azure AD Connect.</span><span class="sxs-lookup"><span data-stu-id="d469e-132">Contains a download link if a new version of Azure AD Connect has been released.</span></span> |
|<span data-ttu-id="d469e-133">**Cuenta del servicio de sincronización de directorios**</span><span class="sxs-lookup"><span data-stu-id="d469e-133">**Directory sync service account**</span></span> | <span data-ttu-id="d469e-134">Muestra el nombre de la cuenta del servicio de sincronización de directorios de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="d469e-134">Displays the name of your Microsoft 365 directory sync service account.</span></span> |