---
title: Colaborar con invitados en un sitio
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
description: Obtenga información sobre cómo colaborar con invitados en un sitio de SharePoint.
ms.openlocfilehash: 4b68b50fec4322f12c24969bdd71e7d9c0fda245
ms.sourcegitcommit: d388c76d25ca67f240db97f7bfc90f0991b0e7f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2019
ms.locfileid: "37017318"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="c4135-103">Colaborar con invitados en un sitio</span><span class="sxs-lookup"><span data-stu-id="c4135-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="c4135-104">Si necesita colaborar con invitados en documentos, datos y listas, puede usar un sitio de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c4135-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="c4135-105">Los sitios modernos de SharePoint están conectados a Office 365 grupos que pueden administrar la pertenencia al sitio y proporcionar herramientas de colaboración adicionales, como un buzón compartido y un calendario.</span><span class="sxs-lookup"><span data-stu-id="c4135-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="c4135-106">En este artículo, analizaremos los pasos de configuración de Microsoft 365 necesarios para configurar un sitio de SharePoint para la colaboración con los invitados.</span><span class="sxs-lookup"><span data-stu-id="c4135-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="c4135-107">Configuración de las relaciones de organización de Azure</span><span class="sxs-lookup"><span data-stu-id="c4135-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="c4135-108">El uso compartido en Microsoft 365 se rige en su nivel más alto por la configuración de relaciones organizativas en Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="c4135-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="c4135-109">Si el uso compartido de invitado está deshabilitado o restringido en Azure AD, se invalidará cualquier configuración de uso compartido que configure en Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="c4135-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="c4135-110">Compruebe la configuración de relaciones de organización para asegurarse de que no se bloquee el uso compartido con invitados.</span><span class="sxs-lookup"><span data-stu-id="c4135-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Captura de pantalla de la página de configuración de relaciones empresariales de Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="c4135-112">Para establecer la configuración de relación organizativa</span><span class="sxs-lookup"><span data-stu-id="c4135-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="c4135-113">Inicie sesión en Microsoft Azure en [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="c4135-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="c4135-114">En el panel de navegación izquierdo, haga clic en **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="c4135-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="c4135-115">En el panel de **información general** , haga clic en **relaciones organizativas**.</span><span class="sxs-lookup"><span data-stu-id="c4135-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="c4135-116">En el panel relaciones de la **organización** , haga clic en **configuración**.</span><span class="sxs-lookup"><span data-stu-id="c4135-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="c4135-117">Asegúrese de que los **administradores y los usuarios de la función invitador invitado puedan** invitar y que **los miembros puedan invitar** están establecidos en **sí**.</span><span class="sxs-lookup"><span data-stu-id="c4135-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="c4135-118">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c4135-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="c4135-119">Anote la configuración de la sección **restricciones de colaboración** .</span><span class="sxs-lookup"><span data-stu-id="c4135-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="c4135-120">Asegúrese de que los dominios de los invitados con los que desea colaborar no están bloqueados.</span><span class="sxs-lookup"><span data-stu-id="c4135-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="c4135-121">Configuración de invitado de Office 365 Groups</span><span class="sxs-lookup"><span data-stu-id="c4135-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="c4135-122">Los sitios modernos de SharePoint usan grupos de Office 365 para controlar el acceso al sitio.</span><span class="sxs-lookup"><span data-stu-id="c4135-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="c4135-123">La configuración de invitado de los grupos de Office 365 debe estar activada para que el acceso de invitado en los sitios de SharePoint funcione.</span><span class="sxs-lookup"><span data-stu-id="c4135-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Captura de pantalla de la configuración de invitado de Office 365 Groups en el centro de administración de Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="c4135-125">Para establecer la configuración de invitado de Office 365 Groups</span><span class="sxs-lookup"><span data-stu-id="c4135-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="c4135-126">En el centro de administración de Microsoft 365, en el panel de navegación de la izquierda, expanda **configuración**.</span><span class="sxs-lookup"><span data-stu-id="c4135-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="c4135-127">Haga clic en **servicios & complementos**.</span><span class="sxs-lookup"><span data-stu-id="c4135-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="c4135-128">En la lista, haga clic en **grupos de Office 365**.</span><span class="sxs-lookup"><span data-stu-id="c4135-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="c4135-129">Asegúrese de que la casilla **permitir a los miembros del grupo fuera de la organización el acceso al contenido del grupo** y **que los propietarios del grupo agreguen personas fuera de la organización a las** casillas de verificación están activadas.</span><span class="sxs-lookup"><span data-stu-id="c4135-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="c4135-130">Si ha realizado cambios, haga clic en **Guardar cambios**.</span><span class="sxs-lookup"><span data-stu-id="c4135-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="c4135-131">Configuración de uso compartido en el nivel de organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="c4135-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="c4135-132">Para que los invitados tengan acceso a los sitios de SharePoint, la configuración de uso compartido en el nivel de la organización de SharePoint debe permitir el uso compartido con invitados.</span><span class="sxs-lookup"><span data-stu-id="c4135-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="c4135-133">La configuración en el nivel de la organización determina qué opciones de configuración están disponibles para cada sitio.</span><span class="sxs-lookup"><span data-stu-id="c4135-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="c4135-134">La configuración del sitio no puede ser más permisiva que la configuración de nivel de organización.</span><span class="sxs-lookup"><span data-stu-id="c4135-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="c4135-135">Si desea permitir el uso compartido de archivos y carpetas con usuarios anónimos, elija **cualquier persona**.</span><span class="sxs-lookup"><span data-stu-id="c4135-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="c4135-136">Si desea asegurarse de que todos los invitados tienen que autenticarse, elija los **invitados nuevos y existentes**.</span><span class="sxs-lookup"><span data-stu-id="c4135-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="c4135-137">Elija la configuración más permisiva que necesitará cualquier sitio de la organización.</span><span class="sxs-lookup"><span data-stu-id="c4135-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Captura de pantalla de la configuración de uso compartido en el nivel de organización de SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="c4135-139">Para establecer la configuración de uso compartido en el nivel de la organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="c4135-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="c4135-140">En el centro de administración de Microsoft 365, en el panel de navegación izquierdo, en **centros de administración**, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="c4135-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="c4135-141">En el centro de administración de SharePoint, en el panel de navegación izquierdo, haga clic en **compartir**.</span><span class="sxs-lookup"><span data-stu-id="c4135-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="c4135-142">Asegúrese de que el uso compartido externo para SharePoint está establecido en **todos** o en **invitados nuevos o existentes**.</span><span class="sxs-lookup"><span data-stu-id="c4135-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="c4135-143">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c4135-143">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="c4135-144">Crear un sitio</span><span class="sxs-lookup"><span data-stu-id="c4135-144">Create a site</span></span>

<span data-ttu-id="c4135-145">El siguiente paso es crear el sitio que va a usar para colaborar con los invitados.</span><span class="sxs-lookup"><span data-stu-id="c4135-145">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="c4135-146">Para crear un sitio</span><span class="sxs-lookup"><span data-stu-id="c4135-146">To create a site</span></span>
1. <span data-ttu-id="c4135-147">En el centro de administración de SharePoint, en **sitios**, haga clic en **sitios activos**.</span><span class="sxs-lookup"><span data-stu-id="c4135-147">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="c4135-148">Haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="c4135-148">Click **Create**.</span></span>
3. <span data-ttu-id="c4135-149">Haga clic en **sitio de grupo**.</span><span class="sxs-lookup"><span data-stu-id="c4135-149">Click **Team site**.</span></span>
4. <span data-ttu-id="c4135-150">Escriba un nombre de sitio y escriba un nombre para el propietario del grupo (propietario del sitio).</span><span class="sxs-lookup"><span data-stu-id="c4135-150">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="c4135-151">En **Configuración avanzada**, elija si desea que sea un sitio público o privado.</span><span class="sxs-lookup"><span data-stu-id="c4135-151">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="c4135-152">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="c4135-152">Click **Next**.</span></span>
7. <span data-ttu-id="c4135-153">Haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="c4135-153">Click **Finish**.</span></span>

<span data-ttu-id="c4135-154">Invitaremos a los usuarios más adelante.</span><span class="sxs-lookup"><span data-stu-id="c4135-154">We'll invite users later.</span></span> <span data-ttu-id="c4135-155">A continuación, es importante comprobar la configuración de uso compartido de nivel de sitio para este sitio.</span><span class="sxs-lookup"><span data-stu-id="c4135-155">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="c4135-156">Configuración de uso compartido del nivel de sitio de SharePoint</span><span class="sxs-lookup"><span data-stu-id="c4135-156">SharePoint site level sharing settings</span></span>

<span data-ttu-id="c4135-157">Compruebe la configuración de uso compartido de nivel de sitio para asegurarse de que permite el tipo de acceso que desea para este sitio.</span><span class="sxs-lookup"><span data-stu-id="c4135-157">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="c4135-158">Por ejemplo, si establece la configuración de nivel de organización en **cualquiera**, pero desea que todos los invitados se autentiquen en este sitio, asegúrese de que la configuración de uso compartido de nivel de sitio esté establecida en **invitados nuevos y existentes**.</span><span class="sxs-lookup"><span data-stu-id="c4135-158">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="c4135-159">Tenga en cuenta que el sitio no se puede compartir con usuarios anónimos (configuración de**cualquier persona** ), pero sí puede archivos y carpetas individuales.</span><span class="sxs-lookup"><span data-stu-id="c4135-159">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![Captura de pantalla de la configuración de uso compartido externo del sitio de SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="c4135-161">Para establecer la configuración de uso compartido de nivel de sitio</span><span class="sxs-lookup"><span data-stu-id="c4135-161">To set site-level sharing settings</span></span>
1. <span data-ttu-id="c4135-162">En el centro de administración de SharePoint, en el panel de navegación de la izquierda, expanda **sitios** y haga clic en **sitios activos**.</span><span class="sxs-lookup"><span data-stu-id="c4135-162">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="c4135-163">Seleccione el sitio que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="c4135-163">Select the site that you just created.</span></span>
3. <span data-ttu-id="c4135-164">En la cinta, haga clic en **uso compartido**.</span><span class="sxs-lookup"><span data-stu-id="c4135-164">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="c4135-165">Asegúrese de que el uso compartido está establecido en **todos** o en **invitados nuevos o existentes**.</span><span class="sxs-lookup"><span data-stu-id="c4135-165">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="c4135-166">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c4135-166">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="c4135-167">Invitar a usuarios</span><span class="sxs-lookup"><span data-stu-id="c4135-167">Invite users</span></span>

<span data-ttu-id="c4135-168">La configuración de uso compartido de invitados ya está configurada, por lo que puede empezar a agregar invitados y usuarios internos a su sitio.</span><span class="sxs-lookup"><span data-stu-id="c4135-168">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="c4135-169">El acceso al sitio se controla mediante el grupo de Office 365 asociado, por lo que vamos a agregar a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="c4135-169">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="c4135-170">Para invitar a usuarios internos a un grupo</span><span class="sxs-lookup"><span data-stu-id="c4135-170">To invite internal users to a group</span></span>
1. <span data-ttu-id="c4135-171">Navegue hasta el sitio en el que desea agregar usuarios.</span><span class="sxs-lookup"><span data-stu-id="c4135-171">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="c4135-172">Haga clic en **miembros** en la esquina superior derecha.</span><span class="sxs-lookup"><span data-stu-id="c4135-172">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="c4135-173">Haga clic en **Agregar miembros**.</span><span class="sxs-lookup"><span data-stu-id="c4135-173">Click **Add members**.</span></span>
4. <span data-ttu-id="c4135-174">Escriba los nombres o las direcciones de correo electrónico de los usuarios que desea invitar al sitio y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="c4135-174">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="c4135-175">No se pueden agregar usuarios invitados desde el sitio.</span><span class="sxs-lookup"><span data-stu-id="c4135-175">Guest users can't be added from the site.</span></span> <span data-ttu-id="c4135-176">Debe agregarlos mediante Outlook en la Web.</span><span class="sxs-lookup"><span data-stu-id="c4135-176">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="c4135-177">Para invitar a invitados a un sitio</span><span class="sxs-lookup"><span data-stu-id="c4135-177">To invite guests to a site</span></span>
1. <span data-ttu-id="c4135-178">En Outlook en la web, en **grupos**, haga clic en el grupo al que desea agregar miembros.</span><span class="sxs-lookup"><span data-stu-id="c4135-178">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="c4135-179">Abra la tarjeta de contacto del grupo y, a continuación, en **más opciones** (...), haga clic en **Agregar miembros**.</span><span class="sxs-lookup"><span data-stu-id="c4135-179">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="c4135-180">Escriba las direcciones de correo electrónico de los invitados que desea invitar y, a continuación, haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="c4135-180">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="c4135-181">Haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="c4135-181">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4135-182">Vea también</span><span class="sxs-lookup"><span data-stu-id="c4135-182">See Also</span></span>
