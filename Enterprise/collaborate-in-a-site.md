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
ms.openlocfilehash: 23f55e22d4c85dcd168c403f50b35f574be9ac07
ms.sourcegitcommit: 3bba97053caf5f9cff0ef3205afb7869535f38bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/16/2019
ms.locfileid: "36992389"
---
# <a name="collaborate-with-guests-in-a-site"></a><span data-ttu-id="b3e36-103">Colaborar con invitados en un sitio</span><span class="sxs-lookup"><span data-stu-id="b3e36-103">Collaborate with guests in a site</span></span>

<span data-ttu-id="b3e36-104">Si necesita colaborar con invitados en documentos, datos y listas, puede usar un sitio de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b3e36-104">If you need to collaborate with guests across documents, data, and lists, you can use a SharePoint site.</span></span> <span data-ttu-id="b3e36-105">Los sitios modernos de SharePoint están conectados a Office 365 grupos que pueden administrar la pertenencia al sitio y proporcionar herramientas de colaboración adicionales, como un buzón compartido y un calendario.</span><span class="sxs-lookup"><span data-stu-id="b3e36-105">Modern SharePoint sites are connected to Office 365 Groups which can manage the site membership and provide additional collaboration tools such as a shared mailbox and calendar.</span></span>

<span data-ttu-id="b3e36-106">En este artículo, analizaremos los pasos de configuración de Microsoft 365 necesarios para configurar un sitio de SharePoint para la colaboración con los invitados.</span><span class="sxs-lookup"><span data-stu-id="b3e36-106">In this article, we'll walk through the Microsoft 365 configuration steps necessary to set up a SharePoint site for collaboration with guests.</span></span>

## <a name="azure-organizational-relationships-settings"></a><span data-ttu-id="b3e36-107">Configuración de las relaciones de organización de Azure</span><span class="sxs-lookup"><span data-stu-id="b3e36-107">Azure Organizational relationships settings</span></span>

<span data-ttu-id="b3e36-108">El uso compartido en Microsoft 365 se rige en su nivel más alto por la configuración de relaciones organizativas en Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="b3e36-108">Sharing in Microsoft 365 is governed at its highest level by the organizational relationships settings in Azure Active Directory.</span></span> <span data-ttu-id="b3e36-109">Si el uso compartido de invitado está deshabilitado o restringido en Azure AD, se invalidará cualquier configuración de uso compartido que configure en Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="b3e36-109">If guest sharing is disabled or restricted in Azure AD, this will override any sharing settings that you configure in Microsoft 365.</span></span>

<span data-ttu-id="b3e36-110">Compruebe la configuración de relaciones de organización para asegurarse de que no se bloquee el uso compartido con invitados.</span><span class="sxs-lookup"><span data-stu-id="b3e36-110">Check the organizational relationships settings to ensure that sharing with guests is not blocked.</span></span>

![Captura de pantalla de la página de configuración de relaciones empresariales de Azure Active Directory](media/azure-ad-organizational-relationships-settings.png)

<span data-ttu-id="b3e36-112">Para establecer la configuración de relación organizativa</span><span class="sxs-lookup"><span data-stu-id="b3e36-112">To set organizational relationship settings</span></span>

1. <span data-ttu-id="b3e36-113">Inicie sesión en Microsoft Azure en [https://portal.azure.com](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="b3e36-113">Log in to Microsoft Azure at [https://portal.azure.com](https://portal.azure.com).</span></span>
2. <span data-ttu-id="b3e36-114">En el panel de navegación izquierdo, haga clic en **Azure Active Directory**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-114">In the left navigation, click **Azure Active Directory**.</span></span>
3. <span data-ttu-id="b3e36-115">En el panel de **información general** , haga clic en **relaciones organizativas**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-115">In the **Overview** pane, click **Organizational relationships**.</span></span>
4. <span data-ttu-id="b3e36-116">En el panel relaciones de la **organización** , haga clic en **configuración**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-116">In the **Organizational relationships** pane, click **Settings**.</span></span>
5. <span data-ttu-id="b3e36-117">Asegúrese de que los **administradores y los usuarios de la función invitador invitado puedan** invitar y que **los miembros puedan invitar** están establecidos en **sí**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-117">Ensure that **Admins and users in the guest inviter role can invite** and **Members can invite** are both set to **Yes**.</span></span>
6. <span data-ttu-id="b3e36-118">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-118">If you made changes, click **Save**.</span></span>

<span data-ttu-id="b3e36-119">Anote la configuración de la sección **restricciones de colaboración** .</span><span class="sxs-lookup"><span data-stu-id="b3e36-119">Note the settings in the **Collaboration restrictions** section.</span></span> <span data-ttu-id="b3e36-120">Asegúrese de que los dominios de los invitados con los que desea colaborar no están bloqueados.</span><span class="sxs-lookup"><span data-stu-id="b3e36-120">Make sure that the domains of the guests that you want to collaborate with aren't blocked.</span></span>

## <a name="office-365-groups-guest-settings"></a><span data-ttu-id="b3e36-121">Configuración de invitado de Office 365 Groups</span><span class="sxs-lookup"><span data-stu-id="b3e36-121">Office 365 Groups guest settings</span></span>

<span data-ttu-id="b3e36-122">Los sitios modernos de SharePoint usan grupos de Office 365 para controlar el acceso al sitio.</span><span class="sxs-lookup"><span data-stu-id="b3e36-122">Modern SharePoint sites use Office 365 Groups to control site access.</span></span> <span data-ttu-id="b3e36-123">La configuración de invitado de los grupos de Office 365 debe estar activada para que el acceso de invitado en los sitios de SharePoint funcione.</span><span class="sxs-lookup"><span data-stu-id="b3e36-123">The Office 365 Groups guest settings must be turned on in order for guest access in SharePoint sites to work.</span></span>

![Captura de pantalla de la configuración de invitado de Office 365 Groups en el centro de administración de Microsoft 365](media/office-365-groups-guest-settings.png)

<span data-ttu-id="b3e36-125">Para establecer la configuración de invitado de Office 365 Groups</span><span class="sxs-lookup"><span data-stu-id="b3e36-125">To set Office 365 Groups guest settings</span></span>

1. <span data-ttu-id="b3e36-126">En el centro de administración de Microsoft 365, en el panel de navegación de la izquierda, expanda **configuración**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-126">In the Microsoft 365 admin center, in the left navigation, expand **Settings**.</span></span>
2. <span data-ttu-id="b3e36-127">Haga clic en **servicios & complementos**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-127">Click **Services & add-ins**.</span></span>
3. <span data-ttu-id="b3e36-128">En la lista, haga clic en **grupos de Office 365**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-128">In the list, click **Office 365 Groups**.</span></span>
4. <span data-ttu-id="b3e36-129">Asegúrese de que la casilla **permitir a los miembros del grupo fuera de la organización el acceso al contenido del grupo** y **que los propietarios del grupo agreguen personas fuera de la organización a las** casillas de verificación están activadas.</span><span class="sxs-lookup"><span data-stu-id="b3e36-129">Ensure that the **Let group members outside your organization access group content** and **Let group owners add people outside your organization to groups** check boxes are both checked.</span></span>
5. <span data-ttu-id="b3e36-130">Si ha realizado cambios, haga clic en **Guardar cambios**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-130">If you made changes, click **Save changes**.</span></span>


## <a name="sharepoint-organization-level-sharing-settings"></a><span data-ttu-id="b3e36-131">Configuración de uso compartido en el nivel de organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="b3e36-131">SharePoint organization level sharing settings</span></span>

<span data-ttu-id="b3e36-132">Para que los invitados tengan acceso a los sitios de SharePoint, la configuración de uso compartido en el nivel de la organización de SharePoint debe permitir el uso compartido con invitados.</span><span class="sxs-lookup"><span data-stu-id="b3e36-132">In order for guests to have access to SharePoint sites, the SharePoint organization-level sharing settings must allow for sharing with guests.</span></span>

<span data-ttu-id="b3e36-133">La configuración en el nivel de la organización determina qué opciones de configuración están disponibles para cada sitio.</span><span class="sxs-lookup"><span data-stu-id="b3e36-133">The organization-level settings determine what settings are available for individual sites.</span></span> <span data-ttu-id="b3e36-134">La configuración del sitio no puede ser más permisiva que la configuración de nivel de organización.</span><span class="sxs-lookup"><span data-stu-id="b3e36-134">Site settings cannot be more permissive than the organization-level settings.</span></span>

<span data-ttu-id="b3e36-135">Si desea permitir el uso compartido de archivos y carpetas con usuarios anónimos, elija **cualquier persona**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-135">If you want to allow file and folder sharing with anonymous users, choose **Anyone**.</span></span> <span data-ttu-id="b3e36-136">Si desea asegurarse de que todos los invitados tienen que autenticarse, elija los **invitados nuevos y existentes**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-136">If you want to ensure that all guests have to authenticate, choose **New and existing guests**.</span></span> <span data-ttu-id="b3e36-137">Elija la configuración más permisiva que necesitará cualquier sitio de la organización.</span><span class="sxs-lookup"><span data-stu-id="b3e36-137">Choose the most permissive setting that will be needed by any site in your organization.</span></span>

![Captura de pantalla de la configuración de uso compartido en el nivel de organización de SharePoint](media/sharepoint-organization-external-sharing-controls.png)


<span data-ttu-id="b3e36-139">Para establecer la configuración de uso compartido en el nivel de la organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="b3e36-139">To set SharePoint organization level sharing settings</span></span>

1. <span data-ttu-id="b3e36-140">En el centro de administración de Microsoft 365, en el panel de navegación izquierdo, en **centros de administración**, haga clic en **SharePoint**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-140">In the Microsoft 365 admin center, in the left navigation, under **Admin centers**, click **SharePoint**.</span></span>
2. <span data-ttu-id="b3e36-141">En el centro de administración de SharePoint, en el panel de navegación izquierdo, haga clic en **compartir**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-141">In the SharePoint admin center, in the left navigation, click **Sharing**.</span></span>
3. <span data-ttu-id="b3e36-142">Asegúrese de que el uso compartido externo para SharePoint está establecido en **todos** o en **invitados nuevos o existentes**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-142">Ensure that external sharing for SharePoint is set to **Anyone** or **New and existing guests**.</span></span>
4. <span data-ttu-id="b3e36-143">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-143">If you made changes, click **Save**.</span></span>


## <a name="sharepoint-organization-level-default-link-settings"></a><span data-ttu-id="b3e36-144">Configuración de vínculos predeterminados de nivel de organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="b3e36-144">SharePoint organization level default link settings</span></span>

<span data-ttu-id="b3e36-145">La configuración predeterminada de los vínculos de archivos y carpetas determina qué opción de vínculo se muestra al usuario de forma predeterminada cuando comparte un archivo o una carpeta.</span><span class="sxs-lookup"><span data-stu-id="b3e36-145">The default file and folder link settings determine which link option is shown to the user by default when they share a file or folder.</span></span> <span data-ttu-id="b3e36-146">Los usuarios pueden cambiar el tipo de vínculo a una de las otras opciones antes de compartirlo, si lo desea.</span><span class="sxs-lookup"><span data-stu-id="b3e36-146">Users can change the link type to one of the other options before sharing if desired.</span></span>

<span data-ttu-id="b3e36-147">Tenga en cuenta que esta configuración afecta a todos los equipos y sitios de SharePoint de la organización.</span><span class="sxs-lookup"><span data-stu-id="b3e36-147">Keep in mind that this setting affects all teams and SharePoint sites in your organization.</span></span>

<span data-ttu-id="b3e36-148">Elija el tipo de vínculo que está seleccionado de forma predeterminada cuando los usuarios comparten archivos y carpetas:</span><span class="sxs-lookup"><span data-stu-id="b3e36-148">Choose the type of link that's selected by default when users share files and folders:</span></span>

- <span data-ttu-id="b3e36-149">**Cualquiera que tenga el vínculo** : elija esta opción si prevé compartir una gran cantidad de archivos y carpetas con usuarios anónimos.</span><span class="sxs-lookup"><span data-stu-id="b3e36-149">**Anyone with the link** - Choose this option if you expect to share a lot of files and folders with anonymous users.</span></span> <span data-ttu-id="b3e36-150">Si desea permitir que *todos* los vínculos, pero le preocupa el uso compartido de anónimos accidentales, tenga en cuenta una de las otras opciones predeterminadas.</span><span class="sxs-lookup"><span data-stu-id="b3e36-150">If you want to allow *Anyone* links but are concerned about accidental anonymous sharing, consider one of the other options as the default.</span></span> <span data-ttu-id="b3e36-151">Este tipo de vínculo solo está disponible si ha habilitado a **todos los usuarios** que comparten el mismo.</span><span class="sxs-lookup"><span data-stu-id="b3e36-151">This link type is only available if you've enabled **Anyone** sharing.</span></span>
- <span data-ttu-id="b3e36-152">**Solo las personas de su organización** : elija esta opción si prevé que la mayoría del uso compartido de archivos y carpetas sea para personas dentro de la organización.</span><span class="sxs-lookup"><span data-stu-id="b3e36-152">**Only people in your organization** - Choose this option if you expect most file and folder sharing to be with people inside your organization.</span></span>
- <span data-ttu-id="b3e36-153">**Personas específicas** : considere esta opción si espera compartir muchos archivos y carpetas con los invitados.</span><span class="sxs-lookup"><span data-stu-id="b3e36-153">**Specific people** - Consider this option if you expect to do a lot of file and folder sharing with guests.</span></span> <span data-ttu-id="b3e36-154">Este tipo de vínculo funciona con los invitados y requiere que se autentiquen.</span><span class="sxs-lookup"><span data-stu-id="b3e36-154">This type of link works with guests and requires them to authenticate.</span></span>
 
![Captura de pantalla de la configuración de uso compartido de archivos y carpetas en el nivel de organización de SharePoint](media/sharepoint-organization-files-folders-sharing-settings.png)


<span data-ttu-id="b3e36-156">Para establecer la configuración de vínculos predeterminados de nivel de organización de SharePoint</span><span class="sxs-lookup"><span data-stu-id="b3e36-156">To set the SharePoint organization level default link settings</span></span>

1. <span data-ttu-id="b3e36-157">Vaya a la página de uso compartido en el centro de administración de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b3e36-157">Navigate to the Sharing page in the SharePoint admin center.</span></span>
2. <span data-ttu-id="b3e36-158">En **vínculos de archivos y carpetas**, seleccione el vínculo de uso compartido predeterminado que desee usar.</span><span class="sxs-lookup"><span data-stu-id="b3e36-158">Under **File and folder links**, select the default sharing link that you want to use.</span></span>
3. <span data-ttu-id="b3e36-159">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-159">If you made changes, click **Save**.</span></span>

## <a name="create-a-site"></a><span data-ttu-id="b3e36-160">Crear un sitio</span><span class="sxs-lookup"><span data-stu-id="b3e36-160">Create a site</span></span>

<span data-ttu-id="b3e36-161">El siguiente paso es crear el sitio que va a usar para colaborar con los invitados.</span><span class="sxs-lookup"><span data-stu-id="b3e36-161">The next step is to create the site that you plan to use for collaborating with guests.</span></span>

<span data-ttu-id="b3e36-162">Para crear un sitio</span><span class="sxs-lookup"><span data-stu-id="b3e36-162">To create a site</span></span>
1. <span data-ttu-id="b3e36-163">En el centro de administración de SharePoint, en **sitios**, haga clic en **sitios activos**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-163">In the SharePoint admin center, under **Sites**, click **Active sites**.</span></span>
2. <span data-ttu-id="b3e36-164">Haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-164">Click **Create**.</span></span>
3. <span data-ttu-id="b3e36-165">Haga clic en **sitio de grupo**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-165">Click **Team site**.</span></span>
4. <span data-ttu-id="b3e36-166">Escriba un nombre de sitio y escriba un nombre para el propietario del grupo (propietario del sitio).</span><span class="sxs-lookup"><span data-stu-id="b3e36-166">Type a site name and enter a name for the Group owner (site owner).</span></span>
5. <span data-ttu-id="b3e36-167">En **Configuración avanzada**, elija si desea que sea un sitio público o privado.</span><span class="sxs-lookup"><span data-stu-id="b3e36-167">Under **Advanced settings**, choose if you want this to be a public or private site.</span></span>
6. <span data-ttu-id="b3e36-168">Haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-168">Click **Next**.</span></span>
7. <span data-ttu-id="b3e36-169">Haga clic en **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-169">Click **Finish**.</span></span>

<span data-ttu-id="b3e36-170">Invitaremos a los usuarios más adelante.</span><span class="sxs-lookup"><span data-stu-id="b3e36-170">We'll invite users later.</span></span> <span data-ttu-id="b3e36-171">A continuación, es importante comprobar la configuración de uso compartido de nivel de sitio para este sitio.</span><span class="sxs-lookup"><span data-stu-id="b3e36-171">Next, it's important to check the site-level sharing settings for this site.</span></span>

## <a name="sharepoint-site-level-sharing-settings"></a><span data-ttu-id="b3e36-172">Configuración de uso compartido del nivel de sitio de SharePoint</span><span class="sxs-lookup"><span data-stu-id="b3e36-172">SharePoint site level sharing settings</span></span>

<span data-ttu-id="b3e36-173">Compruebe la configuración de uso compartido de nivel de sitio para asegurarse de que permite el tipo de acceso que desea para este sitio.</span><span class="sxs-lookup"><span data-stu-id="b3e36-173">Check the site-level sharing settings to make sure that they allow the type of access that you want for this site.</span></span> <span data-ttu-id="b3e36-174">Por ejemplo, si establece la configuración de nivel de organización en **cualquiera**, pero desea que todos los invitados se autentiquen en este sitio, asegúrese de que la configuración de uso compartido de nivel de sitio esté establecida en **invitados nuevos y existentes**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-174">For example, if you set the organization-level settings to **Anyone**, but you want all guests to authenticate for this site, then make sure the site-level sharing settings are set to **New and existing guests**.</span></span>

<span data-ttu-id="b3e36-175">Tenga en cuenta que el sitio no se puede compartir con usuarios anónimos (configuración de**cualquier persona** ), pero sí puede archivos y carpetas individuales.</span><span class="sxs-lookup"><span data-stu-id="b3e36-175">Note that the site cannot be shared with anonymous users (**Anyone** setting), but individual files and folders can.</span></span>

![Captura de pantalla de la configuración de uso compartido externo del sitio de SharePoint](media/sharepoint-site-external-sharing-settings.png)

<span data-ttu-id="b3e36-177">Para establecer la configuración de uso compartido de nivel de sitio</span><span class="sxs-lookup"><span data-stu-id="b3e36-177">To set site-level sharing settings</span></span>
1. <span data-ttu-id="b3e36-178">En el centro de administración de SharePoint, en el panel de navegación de la izquierda, expanda **sitios** y haga clic en **sitios activos**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-178">In the SharePoint admin center, in the left navigation, expand **Sites** and click **Active sites**.</span></span>
2. <span data-ttu-id="b3e36-179">Seleccione el sitio que acaba de crear.</span><span class="sxs-lookup"><span data-stu-id="b3e36-179">Select the site that you just created.</span></span>
3. <span data-ttu-id="b3e36-180">En la cinta, haga clic en **uso compartido**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-180">In the ribbon, click **Sharing**.</span></span>
4. <span data-ttu-id="b3e36-181">Asegúrese de que el uso compartido está establecido en **todos** o en **invitados nuevos o existentes**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-181">Ensure that sharing is set to **Anyone** or **New and existing guests**.</span></span>
5. <span data-ttu-id="b3e36-182">Si ha realizado cambios, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-182">If you made changes, click **Save**.</span></span>

## <a name="invite-users"></a><span data-ttu-id="b3e36-183">Invitar a usuarios</span><span class="sxs-lookup"><span data-stu-id="b3e36-183">Invite users</span></span>

<span data-ttu-id="b3e36-184">La configuración de uso compartido de invitados ya está configurada, por lo que puede empezar a agregar invitados y usuarios internos a su sitio.</span><span class="sxs-lookup"><span data-stu-id="b3e36-184">Guest sharing settings are now configured, so you can start adding internal users and guests to your site.</span></span> <span data-ttu-id="b3e36-185">El acceso al sitio se controla mediante el grupo de Office 365 asociado, por lo que vamos a agregar a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="b3e36-185">Site access is controlled through the associated Office 365 Group, so we'll be adding users there.</span></span>

<span data-ttu-id="b3e36-186">Para invitar a usuarios internos a un grupo</span><span class="sxs-lookup"><span data-stu-id="b3e36-186">To invite internal users to a group</span></span>
1. <span data-ttu-id="b3e36-187">Navegue hasta el sitio en el que desea agregar usuarios.</span><span class="sxs-lookup"><span data-stu-id="b3e36-187">Navigate to the site where you want to add users.</span></span>
2. <span data-ttu-id="b3e36-188">Haga clic en **miembros** en la esquina superior derecha.</span><span class="sxs-lookup"><span data-stu-id="b3e36-188">Click **Members** in the upper right.</span></span>
3. <span data-ttu-id="b3e36-189">Haga clic en **Agregar miembros**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-189">Click **Add members**.</span></span>
4. <span data-ttu-id="b3e36-190">Escriba los nombres o las direcciones de correo electrónico de los usuarios que desea invitar al sitio y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-190">Type the names or email addresses of the users that you want to invite to the site, and then click **Save**.</span></span>

<span data-ttu-id="b3e36-191">No se pueden agregar usuarios invitados desde el sitio.</span><span class="sxs-lookup"><span data-stu-id="b3e36-191">Guest users can't be added from the site.</span></span> <span data-ttu-id="b3e36-192">Debe agregarlos mediante Outlook en la Web.</span><span class="sxs-lookup"><span data-stu-id="b3e36-192">You need to add them using Outlook on the web.</span></span>

<span data-ttu-id="b3e36-193">Para invitar a invitados a un sitio</span><span class="sxs-lookup"><span data-stu-id="b3e36-193">To invite guests to a site</span></span>
1. <span data-ttu-id="b3e36-194">En Outlook en la web, en **grupos**, haga clic en el grupo al que desea agregar miembros.</span><span class="sxs-lookup"><span data-stu-id="b3e36-194">In Outlook on the web, under **Groups**, click the group where you want to add members.</span></span>
2. <span data-ttu-id="b3e36-195">Abra la tarjeta de contacto del grupo y, a continuación, en **más opciones** (...), haga clic en **Agregar miembros**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-195">Open the group contact card, and then, under **More options** (...), click **Add members**.</span></span>
3. <span data-ttu-id="b3e36-196">Escriba las direcciones de correo electrónico de los invitados que desea invitar y, a continuación, haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-196">Type the email addresses of the guests that you want to invite, and then click **Add**.</span></span>
4. <span data-ttu-id="b3e36-197">Haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="b3e36-197">Click **Close**.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3e36-198">Vea también</span><span class="sxs-lookup"><span data-stu-id="b3e36-198">See Also</span></span>
