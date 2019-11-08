---
title: Colaborar con invitados en un documento
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Obtenga información sobre cómo colaborar con invitados en un documento en SharePoint y OneDrive.
ms.openlocfilehash: 9ddbae276252c89ecae31a7f2bf5f1a3bf59af0f
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38029154"
---
# <a name="collaborate-with-guests-on-a-document"></a><span data-ttu-id="9c871-103">Colaborar con invitados en un documento</span><span class="sxs-lookup"><span data-stu-id="9c871-103">Collaborate with guests on a document</span></span>

<span data-ttu-id="9c871-104">Si necesita colaborar con los invitados en documentos de SharePoint o OneDrive, puede enviarles un vínculo para compartir al documento.</span><span class="sxs-lookup"><span data-stu-id="9c871-104">If you need to collaborate with guests on documents in SharePoint or OneDrive, you can send them a sharing link to the document.</span></span> <span data-ttu-id="9c871-105">En este artículo, analizaremos los pasos de configuración de Microsoft 365 necesarios para configurar los vínculos de uso compartido de SharePoint y OneDrive según las necesidades de su organización.</span><span class="sxs-lookup"><span data-stu-id="9c871-105">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up sharing links for SharePoint and OneDrive for the needs of your organization.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="9c871-106">Vídeo de demostración</span><span class="sxs-lookup"><span data-stu-id="9c871-106">Video demonstration</span></span>

<span data-ttu-id="9c871-107">En este vídeo se muestran los pasos de configuración que se describen en este documento.</span><span class="sxs-lookup"><span data-stu-id="9c871-107">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE450Vt?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="9c871-108">Configuración de las relaciones de organización de Azure</span><span class="sxs-lookup"><span data-stu-id="9c871-108">Azure Organizational relationships settings</span></span>

<span data-ttu-id="9c871-109">El uso compartido en Microsoft 365 se rige en su nivel más alto por la configuración de relaciones organizativas en Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9c871-109">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="9c871-110">Si el uso compartido de invitado está deshabilitado o restringido en Azure AD, se invalidará cualquier configuración de uso compartido que configure en Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="9c871-110">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="9c871-111">Compruebe la configuración de relaciones de organización para asegurarse de que no se bloquee el uso compartido con invitados.</span><span class="sxs-lookup"><span data-stu-id="9c871-111">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Captura de pantalla de la página de configuración de relaciones empresariales de Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="9c871-113">Para establecer la configuración de relación organizativa</span><span class="sxs-lookup"><span data-stu-id="9c871-113">To set organizational relationship settings</span></span>

1. <span data-ttu-id="9c871-114">Inicie sesión en Microsoft Azure en [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="9c871-114">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="9c871-115">En el panel de navegación izquierdo, haga clic en **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="9c871-115">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="9c871-116">En el panel de **información general** , haga clic en **relaciones organizativas**.</span><span class="sxs-lookup"><span data-stu-id="9c871-116">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="9c871-117">En el panel relaciones de la **organización** , haga clic en **configuración**.</span><span class="sxs-lookup"><span data-stu-id="9c871-117">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="9c871-118">Asegúrese de que los **administradores y los usuarios de la función invitador invitado puedan** invitar y que **los miembros puedan invitar** están establecidos en **sí**.</span><span class="sxs-lookup"><span data-stu-id="9c871-118">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="9c871-119">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="9c871-119">If you made changes, click **Save**.</span></span>

<span data-ttu-id="9c871-120">Anote la configuración de la sección **restricciones de colaboración** .</span><span class="sxs-lookup"><span data-stu-id="9c871-120">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="9c871-121">Asegúrese de que los dominios de los invitados con los que desea colaborar no están bloqueados.</span><span class="sxs-lookup"><span data-stu-id="9c871-121">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="9c871-122">Configuración de uso compartido en el nivel de organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="9c871-122">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="9c871-123">Para que los invitados tengan acceso a un documento en SharePoint o OneDrive, la configuración de uso compartido en el nivel de la organización de SharePoint y OneDrive debe permitir el uso compartido con invitados.</span><span class="sxs-lookup"><span data-stu-id="9c871-123">In order for guests to have access to a document in SharePoint or OneDrive, the SharePoint and OneDrive organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="9c871-124">La configuración a nivel de organización para SharePoint determina qué opciones de configuración están disponibles para los sitios de SharePoint individuales.</span><span class="sxs-lookup"><span data-stu-id="9c871-124">The organization-level settings for SharePoint determine what settings are available for individual SharePoint sites.</span></span> <span data-ttu-id="9c871-125">La configuración del sitio no puede ser más permisiva que la configuración de nivel de organización.</span><span class="sxs-lookup"><span data-stu-id="9c871-125">Site settings cannot be more permissive than the organization-level settings.</span></span> <span data-ttu-id="9c871-126">La configuración en el nivel de la organización para OneDrive determina el nivel de uso compartido que está disponible en las bibliotecas de OneDrive de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="9c871-126">The organization-level setting for OneDrive determines what level of sharing is available in users' OneDrive libraries.</span></span>

<span data-ttu-id="9c871-127">Para SharePoint y OneDrive, si quiere permitir el uso compartido de archivos y carpetas con usuarios anónimos, elija **cualquier persona**.</span><span class="sxs-lookup"><span data-stu-id="9c871-127">For SharePoint and OneDrive, if you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="9c871-128">Si desea asegurarse de que todos los invitados tienen que autenticarse, elija los **invitados nuevos y existentes**.</span><span class="sxs-lookup"><span data-stu-id="9c871-128">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="9c871-129">Los vínculos para *Cualquiera* son la manera más fácil de compartir: los invitados pueden abrir el vínculo sin autenticación y tienen la libertad de compartirlo con otros usuarios.</span><span class="sxs-lookup"><span data-stu-id="9c871-129">*Anyone* links are the easiest way to share: guests can open the link without authentication and are free to pass it on to others.</span></span>

<span data-ttu-id="9c871-130">Para SharePoint, elija la configuración más permisiva que necesitará cualquier sitio de la organización.</span><span class="sxs-lookup"><span data-stu-id="9c871-130">For SharePoint, choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Captura de pantalla de la configuración de uso compartido en el nivel de organización de SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="9c871-132">Para establecer la configuración de uso compartido en el nivel de la organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="9c871-132">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="9c871-133">En el centro de administración de Microsoft 365, en el panel de navegación izquierdo, en **centros de administración**, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="9c871-133">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="9c871-134">En el Centro de administración de SharePoint, en el panel de navegación izquierdo, haga clic en **Uso compartido**.</span><span class="sxs-lookup"><span data-stu-id="9c871-134">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="9c871-135">Asegúrese de que el uso compartido externo para SharePoint o OneDrive está establecido en **cualquiera** o **invitados nuevos o existentes**.</span><span class="sxs-lookup"><span data-stu-id="9c871-135">Ensure that external sharing for SharePoint or OneDrive is set to **Anyone** or **New and existing guests**.</span></span> <span data-ttu-id="9c871-136">(Tenga en cuenta que la configuración de OneDrive no puede ser más permisiva que la configuración de SharePoint).</span><span class="sxs-lookup"><span data-stu-id="9c871-136">(Note that the OneDrive setting cannot be more permissive than the SharePoint setting.)</span></span>
4. <span data-ttu-id="9c871-137">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="9c871-137">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="9c871-138">Configuración de vínculos predeterminados de nivel de organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="9c871-138">SharePoint organization level default link settings</span></span>

<span data-ttu-id="9c871-139">La configuración predeterminada de los vínculos de archivos y carpetas determina qué opción de vínculo se muestra al usuario de forma predeterminada cuando comparte un archivo o una carpeta.</span><span class="sxs-lookup"><span data-stu-id="9c871-139">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="9c871-140">Los usuarios pueden cambiar el tipo de vínculo a una de las otras opciones antes de compartirlo, si lo desea.</span><span class="sxs-lookup"><span data-stu-id="9c871-140">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="9c871-141">Tenga en cuenta que esta configuración afecta a los sitios de SharePoint de su organización, así como a OneDrive.</span><span class="sxs-lookup"><span data-stu-id="9c871-141">Keep in mind that this setting affects SharePoint sites in your organization, as well as OneDrive.</span></span>

<span data-ttu-id="9c871-142">Elija el tipo de vínculo que está seleccionado de forma predeterminada cuando los usuarios comparten archivos y carpetas:</span><span class="sxs-lookup"><span data-stu-id="9c871-142">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="9c871-143">**Cualquiera que tenga el vínculo** : elija esta opción si prevé compartir una gran cantidad de archivos y carpetas con usuarios anónimos.</span><span class="sxs-lookup"><span data-stu-id="9c871-143">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="9c871-144">Si desea permitir que *todos* los vínculos, pero le preocupa el uso compartido de anónimos accidentales, tenga en cuenta una de las otras opciones predeterminadas.</span><span class="sxs-lookup"><span data-stu-id="9c871-144">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="9c871-145">Este tipo de vínculo solo está disponible si ha habilitado a **todos los usuarios** que comparten el mismo.</span><span class="sxs-lookup"><span data-stu-id="9c871-145">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="9c871-146">**Solo las personas de su organización** : elija esta opción si prevé que la mayoría del uso compartido de archivos y carpetas sea para personas dentro de la organización.</span><span class="sxs-lookup"><span data-stu-id="9c871-146">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="9c871-147">**Personas específicas** : considere esta opción si espera compartir muchos archivos y carpetas con los invitados.</span><span class="sxs-lookup"><span data-stu-id="9c871-147">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="9c871-148">Este tipo de vínculo funciona con los invitados y requiere que se autentiquen.</span><span class="sxs-lookup"><span data-stu-id="9c871-148">This type of link works with guests and requires them to authenticate.</span></span>
 
![Captura de pantalla de la configuración de uso compartido de archivos y carpetas en el nivel de organización de SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="9c871-150">Para establecer la configuración de vínculo predeterminado de SharePoint y OneDrive de la organización</span><span class="sxs-lookup"><span data-stu-id="9c871-150">To set the SharePoint and OneDrive organization level default link settings</span></span>

1. <span data-ttu-id="9c871-151">Vaya a la página de uso compartido en el centro de administración de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9c871-151">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="9c871-152">En **vínculos de archivos y carpetas**, seleccione el vínculo de uso compartido predeterminado que desee usar.</span><span class="sxs-lookup"><span data-stu-id="9c871-152">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="9c871-153">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="9c871-153">If you made changes, click **Save**.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="9c871-154">Configuración de uso compartido del nivel de sitio de SharePoint</span><span class="sxs-lookup"><span data-stu-id="9c871-154">SharePoint site level sharing settings</span></span>

<span data-ttu-id="9c871-155">Si está compartiendo archivos y fodlers que están en un sitio de SharePoint, también debe comprobar la configuración de uso compartido de nivel de sitio para ese sitio.</span><span class="sxs-lookup"><span data-stu-id="9c871-155">If you're sharing files and fodlers that are in a SharePoint site, you also need to check the site-level sharing settings for that site.</span></span>

![Captura de pantalla de la configuración de uso compartido externo del sitio de SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="9c871-157">Para establecer la configuración de uso compartido de nivel de sitio</span><span class="sxs-lookup"><span data-stu-id="9c871-157">To set site-level sharing settings</span></span>
1. <span data-ttu-id="9c871-158">En el Centro de administración de SharePoint, en el panel de navegación izquierdo, expanda **Sitios** y haga clic en **Sitios activos**.</span><span class="sxs-lookup"><span data-stu-id="9c871-158">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="9c871-159">Seleccione el sitio que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="9c871-159">Select the site that you just created.</span></span>
3. <span data-ttu-id="9c871-160">En la cinta de opciones, haga clic en **Uso compartido**.</span><span class="sxs-lookup"><span data-stu-id="9c871-160">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="9c871-161">Asegúrese de que el uso compartido está establecido en **todos** o en **invitados nuevos o existentes**.</span><span class="sxs-lookup"><span data-stu-id="9c871-161">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="9c871-162">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="9c871-162">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="9c871-163">Invitar a usuarios</span><span class="sxs-lookup"><span data-stu-id="9c871-163">Invite users</span></span>

<span data-ttu-id="9c871-164">La configuración de uso compartido de invitados ya está configurada, por lo que los usuarios ahora pueden compartir archivos y carpetas con los invitados.</span><span class="sxs-lookup"><span data-stu-id="9c871-164">Guest sharing settings are now configured, so users can now share files and folders with guests.</span></span> <span data-ttu-id="9c871-165">Consulte [compartir archivos y carpetas de OneDrive](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) y [compartir archivos o carpetas de SharePoint](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="9c871-165">See [Share OneDrive files and folders](https://support.office.com/article/9fcc2f7d-de0c-4cec-93b0-a82024800c07) and [Share SharePoint files or folders](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c871-166">Vea también</span><span class="sxs-lookup"><span data-stu-id="9c871-166">See Also</span></span>

[<span data-ttu-id="9c871-167">Procedimientos recomendados para compartir archivos y carpetas con usuarios anónimos</span><span class="sxs-lookup"><span data-stu-id="9c871-167">Best practices for sharing files and folders with anonymous users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="9c871-168">Reducir la exposición accidental de archivos al compartirlos con invitados</span><span class="sxs-lookup"><span data-stu-id="9c871-168">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)