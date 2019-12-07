---
title: Colaborar con invitados en un equipo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Obtenga información sobre cómo colaborar con invitados en Microsoft Teams.
ms.openlocfilehash: 9920bb57f31a36dcc4f903e2f26eccbf41a522db
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886529"
---
# <a name="collaborate-with-guests-in-a-team"></a><span data-ttu-id="8713f-103">Colaborar con invitados en un equipo</span><span class="sxs-lookup"><span data-stu-id="8713f-103">Collaborate with guests in a team</span></span>

<span data-ttu-id="8713f-104">Si necesita colaborar con invitados en documentos, tareas y conversaciones, le recomendamos que use Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8713f-104">If you need to collaborate with guests across documents, tasks, and conversations, we recommend using Microsoft Teams.</span></span> <span data-ttu-id="8713f-105">Teams ofrece todas las características de colaboración disponibles en Office y SharePoint con chat persistente y un conjunto de herramientas de colaboración personalizable y extensible en una experiencia de usuario unificada.</span><span class="sxs-lookup"><span data-stu-id="8713f-105">Teams provides all of the collaboration features available in Office and SharePoint with persistent chat and a customizable and extensible set of collaboration tools in a unified user experience.</span></span>

<span data-ttu-id="8713f-106">En este artículo, analizaremos los pasos de configuración de Microsoft 365 necesarios para configurar un equipo para la colaboración con los invitados.</span><span class="sxs-lookup"><span data-stu-id="8713f-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a team for collaboration with guests.</span></span>

## <a name="video-demonstration"></a><span data-ttu-id="8713f-107">Vídeo de demostración</span><span class="sxs-lookup"><span data-stu-id="8713f-107">Video demonstration</span></span>

<span data-ttu-id="8713f-108">En este vídeo se muestran los pasos de configuración que se describen en este documento.</span><span class="sxs-lookup"><span data-stu-id="8713f-108">This video shows the configuration steps described in this document.</span></span></br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE44NTr?autoplay=false]

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="8713f-109">Configuración de las relaciones de organización de Azure</span><span class="sxs-lookup"><span data-stu-id="8713f-109">Azure Organizational relationships settings</span></span>

<span data-ttu-id="8713f-110">El uso compartido en Microsoft 365 se rige en su nivel más alto por la configuración de relaciones organizativas en Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="8713f-110">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="8713f-111">Si el uso compartido de invitado está deshabilitado o restringido en Azure AD, se invalidará cualquier configuración de uso compartido que configure en Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="8713f-111">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="8713f-112">Compruebe la configuración de relaciones de organización para asegurarse de que no se bloquee el uso compartido con invitados.</span><span class="sxs-lookup"><span data-stu-id="8713f-112">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Captura de pantalla de la página de configuración de relaciones de organización de Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="8713f-114">Para establecer la configuración de relación organizativa</span><span class="sxs-lookup"><span data-stu-id="8713f-114">To set organizational relationship settings</span></span>

1. <span data-ttu-id="8713f-115">Inicie sesión en Microsoft Azure en [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="8713f-115">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="8713f-116">En el panel de navegación izquierdo, haga clic en **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="8713f-116">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="8713f-117">En el panel de **información general** , haga clic en **relaciones organizativas**.</span><span class="sxs-lookup"><span data-stu-id="8713f-117">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="8713f-118">En el panel relaciones de la **organización** , haga clic en **configuración**.</span><span class="sxs-lookup"><span data-stu-id="8713f-118">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="8713f-119">Asegúrese de que los **administradores y los usuarios de la función invitador invitado puedan** invitar y que **los miembros puedan invitar** están establecidos en **sí**.</span><span class="sxs-lookup"><span data-stu-id="8713f-119">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="8713f-120">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="8713f-120">If you made changes, click **Save**.</span></span>

<span data-ttu-id="8713f-121">Anote la configuración de la sección **restricciones de colaboración** .</span><span class="sxs-lookup"><span data-stu-id="8713f-121">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="8713f-122">Asegúrese de que los dominios de los invitados con los que desea colaborar no están bloqueados.</span><span class="sxs-lookup"><span data-stu-id="8713f-122">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="teams-guest-access-settings"></a><span data-ttu-id="8713f-123">Configuración de acceso de invitado de Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8713f-123">Teams guest access settings</span></span>

<span data-ttu-id="8713f-124">Los equipos tienen un conmutador de encendido y apagado principal para el acceso de invitado y una variedad de opciones de configuración disponibles para controlar lo que pueden hacer los invitados en un equipo.</span><span class="sxs-lookup"><span data-stu-id="8713f-124">Teams has a master on/off switch for guest access and a variety of settings available to control what guests can do in a team.</span></span> <span data-ttu-id="8713f-125">El conmutador maestro, **permitir el acceso de invitado en Microsoft Teams** , debe estar **activado** para que el acceso de invitado trabaje en Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8713f-125">The master switch, **Allow guest access in Teams** must be **On** for guest access to work in Teams.</span></span>

<span data-ttu-id="8713f-126">Asegúrese de que el acceso de invitado esté habilitado en Microsoft Teams y realice cualquier ajuste en la configuración de invitado en función de las necesidades de su empresa.</span><span class="sxs-lookup"><span data-stu-id="8713f-126">Check to ensure that guest access is enabled in Teams and make any adjustment to the guest settings based on your business needs.</span></span> <span data-ttu-id="8713f-127">Tenga en cuenta que esta configuración afecta a todos los equipos.</span><span class="sxs-lookup"><span data-stu-id="8713f-127">Keep in mind that these settings affect all teams.</span></span>

![Captura de pantalla de la opción de acceso de invitado de Teams](media/teams-guest-access-toggle-on.png)

<span data-ttu-id="8713f-129">Para establecer la configuración de acceso de invitado de Teams</span><span class="sxs-lookup"><span data-stu-id="8713f-129">To set Teams guest access settings</span></span>

1. <span data-ttu-id="8713f-130">Inicie sesión en el centro de administración de Microsoft [https://admin.microsoft.com](https://admin.microsoft.com)365 en.</span><span class="sxs-lookup"><span data-stu-id="8713f-130">Log in to the Microsoft 365 admin center at [https://admin.microsoft.com](https://admin.microsoft.com).</span></span>
2. <span data-ttu-id="8713f-131">En el panel de navegación izquierdo, haga clic en **Mostrar todo**.</span><span class="sxs-lookup"><span data-stu-id="8713f-131">In the left navigation, click **Show all**.</span></span>
3. <span data-ttu-id="8713f-132">En **centros de administración**, haga clic en **Teams**.</span><span class="sxs-lookup"><span data-stu-id="8713f-132">Under **Admin centers**, click **Teams**.</span></span>
4. <span data-ttu-id="8713f-133">En el centro de administración de Teams, en el panel de navegación de la izquierda, expanda **configuración de toda la organización** y haga clic en **acceso de invitado**.</span><span class="sxs-lookup"><span data-stu-id="8713f-133">In the Teams admin center, in the left navigation, expand **Org-wide settings** and click **Guest access**.</span></span>
5. <span data-ttu-id="8713f-134">Asegúrese de que la **opción permitir el acceso de invitado en Microsoft Teams** está **activada**.</span><span class="sxs-lookup"><span data-stu-id="8713f-134">Ensure that **Allow guest access in Teams** is set to **On**.</span></span>
6. <span data-ttu-id="8713f-135">Realice los cambios que desee en la configuración de invitado adicional y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="8713f-135">Make any desired changes to the additional guest settings, and then click **Save**.</span></span>

> [!NOTE]
> <span data-ttu-id="8713f-136">La configuración del invitado de Teams puede tardar hasta 24 horas en activa una vez que la activa.</span><span class="sxs-lookup"><span data-stu-id="8713f-136">It may take up to twenty-four hours for the Teams guest setting to become active after you turn it on.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="8713f-137">Configuración de invitado de Office 365 Groups</span><span class="sxs-lookup"><span data-stu-id="8713f-137">Office 365 Groups guest settings</span></span>

<span data-ttu-id="8713f-138">Microsoft Teams usa los grupos de Office 365 para la pertenencia al equipo.</span><span class="sxs-lookup"><span data-stu-id="8713f-138">Teams uses Office 365 Groups for team membership.</span></span> <span data-ttu-id="8713f-139">La configuración de invitado de los grupos de Office 365 debe estar activada para que el acceso de invitado en Microsoft Teams funcione.</span><span class="sxs-lookup"><span data-stu-id="8713f-139">The Office 365 Groups guest settings must be turned on in order for guest access in Teams to work.</span></span>

![Captura de pantalla de la configuración de invitados de Grupos de Office 365 en el Centro de administración de Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="8713f-141">Para establecer la configuración de invitado de Office 365 Groups</span><span class="sxs-lookup"><span data-stu-id="8713f-141">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="8713f-142">En el centro de administración de Microsoft 365, en el panel de navegación de la izquierda, expanda **configuración**.</span><span class="sxs-lookup"><span data-stu-id="8713f-142">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="8713f-143">Haga clic en **servicios & complementos**.</span><span class="sxs-lookup"><span data-stu-id="8713f-143">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="8713f-144">En la lista, haga clic en **grupos de Office 365**.</span><span class="sxs-lookup"><span data-stu-id="8713f-144">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="8713f-145">Asegúrese de que la casilla **permitir a los miembros del grupo fuera de la organización el acceso al contenido del grupo** y **que los propietarios del grupo agreguen personas fuera de la organización a las** casillas de verificación están activadas.</span><span class="sxs-lookup"><span data-stu-id="8713f-145">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="8713f-146">Si ha realizado cambios, haga clic en **Guardar cambios**.</span><span class="sxs-lookup"><span data-stu-id="8713f-146">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="8713f-147">Configuración de uso compartido en el nivel de organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="8713f-147">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="8713f-148">El contenido de Microsoft Teams, como archivos, carpetas y listas, se almacena en SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8713f-148">Teams content such as files, folders, and lists are all stored in SharePoint.</span></span> <span data-ttu-id="8713f-149">Para que los invitados tengan acceso a estos elementos en Microsoft Teams, la configuración de uso compartido en el nivel de la organización de SharePoint debe permitir el uso compartido con invitados.</span><span class="sxs-lookup"><span data-stu-id="8713f-149">In order for guests to have access to these items in Teams, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="8713f-150">La configuración en el nivel de la organización determina qué opciones de configuración están disponibles para cada uno de los sitios, incluidos los sitios asociados a teams.</span><span class="sxs-lookup"><span data-stu-id="8713f-150">The organization-level settings determine what settings are available for individual sites, including sites associated with teams.</span></span> <span data-ttu-id="8713f-151">La configuración del sitio no puede ser más permisiva que la configuración de nivel de organización.</span><span class="sxs-lookup"><span data-stu-id="8713f-151">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="8713f-152">Si desea permitir el uso compartido de archivos y carpetas con personas sin autenticar, elija **cualquiera**.</span><span class="sxs-lookup"><span data-stu-id="8713f-152">If you want to allow file and folder sharing with unauthenticated people, choose **Anyone**.</span></span> <span data-ttu-id="8713f-153">Si desea asegurarse de que todos los invitados tienen que autenticarse, elija los **invitados nuevos y existentes**.</span><span class="sxs-lookup"><span data-stu-id="8713f-153">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="8713f-154">Elija la configuración más permisiva que necesitará cualquier sitio de la organización.</span><span class="sxs-lookup"><span data-stu-id="8713f-154">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Captura de pantalla de la configuración de uso compartido en el nivel de organización de SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="8713f-156">Para establecer la configuración de uso compartido en el nivel de la organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="8713f-156">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="8713f-157">En el centro de administración de Microsoft 365, en el panel de navegación izquierdo, en **centros de administración**, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="8713f-157">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="8713f-158">En el Centro de administración de SharePoint, en el panel de navegación izquierdo, haga clic en **Uso compartido**.</span><span class="sxs-lookup"><span data-stu-id="8713f-158">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="8713f-159">Asegúrese de que el uso compartido externo para SharePoint está establecido en **todos** o en **invitados nuevos o existentes**.</span><span class="sxs-lookup"><span data-stu-id="8713f-159">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="8713f-160">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="8713f-160">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="8713f-161">Configuración de vínculos predeterminados de nivel de organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="8713f-161">SharePoint organization level default link settings</span></span>

<span data-ttu-id="8713f-162">La configuración predeterminada de los vínculos de archivos y carpetas determina qué opción de vínculo se muestra al usuario de forma predeterminada cuando comparte un archivo o una carpeta.</span><span class="sxs-lookup"><span data-stu-id="8713f-162">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="8713f-163">Los usuarios pueden cambiar el tipo de vínculo a una de las otras opciones antes de compartirlo, si lo desea.</span><span class="sxs-lookup"><span data-stu-id="8713f-163">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="8713f-164">Tenga en cuenta que esta configuración afecta a todos los equipos y sitios de SharePoint de la organización.</span><span class="sxs-lookup"><span data-stu-id="8713f-164">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="8713f-165">Elija el tipo de vínculo que está seleccionado de forma predeterminada cuando los usuarios comparten archivos y carpetas:</span><span class="sxs-lookup"><span data-stu-id="8713f-165">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="8713f-166">**Cualquiera que tenga el vínculo** : elija esta opción si prevé compartir una gran cantidad de archivos y carpetas con personas no autenticadas.</span><span class="sxs-lookup"><span data-stu-id="8713f-166">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with unauthenticated people.</span></span> <span data-ttu-id="8713f-167">Si desea permitir que *todos* los vínculos, pero le preocupa el uso compartido no autenticado accidentalmente, considere una de las otras opciones como predeterminada.</span><span class="sxs-lookup"><span data-stu-id="8713f-167">If you want to allow *Anyone* links but are concerned about accidental unauthenticated sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="8713f-168">Este tipo de vínculo solo está disponible si ha habilitado a **todos los usuarios** que comparten el mismo.</span><span class="sxs-lookup"><span data-stu-id="8713f-168">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="8713f-169">**Solo las personas de su organización** : elija esta opción si prevé que la mayoría del uso compartido de archivos y carpetas sea para personas dentro de la organización.</span><span class="sxs-lookup"><span data-stu-id="8713f-169">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="8713f-170">**Personas específicas** : considere esta opción si espera compartir muchos archivos y carpetas con los invitados.</span><span class="sxs-lookup"><span data-stu-id="8713f-170">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="8713f-171">Este tipo de vínculo funciona con los invitados y requiere que se autentiquen.</span><span class="sxs-lookup"><span data-stu-id="8713f-171">This type of link works with guests and requires them to authenticate.</span></span>
 
![Captura de pantalla de la configuración de uso compartido de los archivos y carpetas de nivel de organización de SharePoint ](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="8713f-173">Para establecer la configuración de vínculos predeterminados de nivel de organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="8713f-173">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="8713f-174">Vaya a la página de uso compartido en el centro de administración de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8713f-174">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="8713f-175">En **vínculos de archivos y carpetas**, seleccione el vínculo de uso compartido predeterminado que desee usar.</span><span class="sxs-lookup"><span data-stu-id="8713f-175">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="8713f-176">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="8713f-176">If you made changes, click **Save**.</span></span>

## <a name="create-a-team"></a><span data-ttu-id="8713f-177">Crear un equipo</span><span class="sxs-lookup"><span data-stu-id="8713f-177">Create a team</span></span>

<span data-ttu-id="8713f-178">El siguiente paso es crear el equipo que planea usar para colaborar con invitados.</span><span class="sxs-lookup"><span data-stu-id="8713f-178">The next step is to create the team that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="8713f-179">Para crear un equipo</span><span class="sxs-lookup"><span data-stu-id="8713f-179">To create a team</span></span>
1. <span data-ttu-id="8713f-180">En Microsoft Teams, en **la pestaña Microsoft Teams** , haga clic en **unirse o en crear un equipo** en la parte inferior del panel izquierdo.</span><span class="sxs-lookup"><span data-stu-id="8713f-180">In Teams, on the **Teams** tab, click **Join or create a team** at the bottom of the left pane.</span></span>
2. <span data-ttu-id="8713f-181">Haga clic en **crear un equipo**.</span><span class="sxs-lookup"><span data-stu-id="8713f-181">Click **Create a team**.</span></span>
3. <span data-ttu-id="8713f-182">Haga clic en **crear un equipo desde cero**.</span><span class="sxs-lookup"><span data-stu-id="8713f-182">Click **Build a team from scratch**.</span></span>
4. <span data-ttu-id="8713f-183">Elija **privado** o **público**.</span><span class="sxs-lookup"><span data-stu-id="8713f-183">Choose **Private** or **Public**.</span></span>
5. <span data-ttu-id="8713f-184">Escriba un nombre y una descripción para el equipo y, a continuación, haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="8713f-184">Type a name and description for the team, and then click **Create**.</span></span>
6. <span data-ttu-id="8713f-185">Haga clic en **omitir**.</span><span class="sxs-lookup"><span data-stu-id="8713f-185">Click **Skip**.</span></span>

<span data-ttu-id="8713f-186">Invitaremos a los usuarios más adelante.</span><span class="sxs-lookup"><span data-stu-id="8713f-186">We'll invite users later.</span></span> <span data-ttu-id="8713f-187">A continuación, es importante comprobar la configuración de uso compartido de nivel de sitio para el sitio de SharePoint asociado al equipo.</span><span class="sxs-lookup"><span data-stu-id="8713f-187">Next, it's important to check the site-level sharing settings for the SharePoint site that is associated with the team.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="8713f-188">Configuración de uso compartido del nivel de sitio de SharePoint</span><span class="sxs-lookup"><span data-stu-id="8713f-188">SharePoint site level sharing settings</span></span>

<span data-ttu-id="8713f-189">Compruebe la configuración de uso compartido de nivel de sitio para asegurarse de que permite el tipo de acceso que desea para este equipo.</span><span class="sxs-lookup"><span data-stu-id="8713f-189">Check the site-level sharing settings to make sure that they allow the type of access that you want for this team.</span></span> <span data-ttu-id="8713f-190">Por ejemplo, si establece la configuración en el nivel de la organización en **cualquiera**, pero desea que todos los invitados se autentiquen para este equipo, asegúrese de que la configuración de uso compartido de nivel de sitio esté establecida en **invitados nuevos y existentes**.</span><span class="sxs-lookup"><span data-stu-id="8713f-190">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this team, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

![Captura de pantalla de la configuración de uso compartido externo del sitio de SharePoint](media/sharepoint-site-external-sharing-settings.png)


<span data-ttu-id="8713f-192">Para establecer la configuración de uso compartido de nivel de sitio</span><span class="sxs-lookup"><span data-stu-id="8713f-192">To set site-level sharing settings</span></span>
1. <span data-ttu-id="8713f-193">En el Centro de administración de SharePoint, en el panel de navegación izquierdo, expanda **Sitios** y haga clic en **Sitios activos**.</span><span class="sxs-lookup"><span data-stu-id="8713f-193">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="8713f-194">Seleccione el sitio para el equipo recién creado.</span><span class="sxs-lookup"><span data-stu-id="8713f-194">Select the site for the team that you just created.</span></span>
3. <span data-ttu-id="8713f-195">En la cinta de opciones, haga clic en **Uso compartido**.</span><span class="sxs-lookup"><span data-stu-id="8713f-195">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="8713f-196">Asegúrese de que el uso compartido está establecido en **todos** o en **invitados nuevos o existentes**.</span><span class="sxs-lookup"><span data-stu-id="8713f-196">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="8713f-197">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="8713f-197">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="8713f-198">Invitar a usuarios</span><span class="sxs-lookup"><span data-stu-id="8713f-198">Invite users</span></span>

<span data-ttu-id="8713f-199">La configuración de uso compartido de invitados ya está configurada, por lo que puede empezar a agregar invitados y usuarios internos a su equipo.</span><span class="sxs-lookup"><span data-stu-id="8713f-199">Guest sharing settings are now configured, so you can start adding internal users and guests to your team.</span></span> 

<span data-ttu-id="8713f-200">Para invitar a usuarios internos a un equipo</span><span class="sxs-lookup"><span data-stu-id="8713f-200">To invite internal users to a team</span></span>
1. <span data-ttu-id="8713f-201">En el equipo, haga clic en **más opciones** (**\*\***) y, a continuación, haga clic en **Agregar miembro**.</span><span class="sxs-lookup"><span data-stu-id="8713f-201">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="8713f-202">Escriba el nombre de la persona a la que desea invitar.</span><span class="sxs-lookup"><span data-stu-id="8713f-202">Type the name of the person who you want to invite.</span></span>
3. <span data-ttu-id="8713f-203">Haga clic en **Agregar** y, después, en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="8713f-203">Click **Add**, and then click **Close**.</span></span>

<span data-ttu-id="8713f-204">Para invitar a invitados a un equipo</span><span class="sxs-lookup"><span data-stu-id="8713f-204">To invite guests to a team</span></span>
1. <span data-ttu-id="8713f-205">En el equipo, haga clic en **más opciones** (**\*\***) y, a continuación, haga clic en **Agregar miembro**.</span><span class="sxs-lookup"><span data-stu-id="8713f-205">In the team, click **More options** (**\*\*\***), and then click **Add member**.</span></span>
2. <span data-ttu-id="8713f-206">Escriba la dirección de correo electrónico del invitado al que desea invitar.</span><span class="sxs-lookup"><span data-stu-id="8713f-206">Type the email address of the guest who you want to invite.</span></span>
3. <span data-ttu-id="8713f-207">Haga clic en **editar información de invitado**.</span><span class="sxs-lookup"><span data-stu-id="8713f-207">Click **Edit guest information**.</span></span>
4. <span data-ttu-id="8713f-208">Escriba el nombre completo del invitado y haga clic en la marca de verificación.</span><span class="sxs-lookup"><span data-stu-id="8713f-208">Type the guest's full name and click the check mark.</span></span>
5. <span data-ttu-id="8713f-209">Haga clic en **Agregar** y, después, en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="8713f-209">Click **Add**, and then click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="8713f-210">Vea también</span><span class="sxs-lookup"><span data-stu-id="8713f-210">See Also</span></span>

[<span data-ttu-id="8713f-211">Procedimientos recomendados para compartir archivos y carpetas con usuarios no autenticados</span><span class="sxs-lookup"><span data-stu-id="8713f-211">Best practices for sharing files and folders with unauthenticated users</span></span>](best-practices-anonymous-sharing.md)

[<span data-ttu-id="8713f-212">Reducir la exposición accidental de archivos al compartirlos con invitados</span><span class="sxs-lookup"><span data-stu-id="8713f-212">Limit accidental exposure to files when sharing with guests</span></span>](sharing-limit-accidental-exposure.md)

<span data-ttu-id="8713f-213">[Crear un entorno de uso compartido de invitado seguro](create-a-secure-guest-sharing-environment.md))</span><span class="sxs-lookup"><span data-stu-id="8713f-213">[Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md))</span></span>


