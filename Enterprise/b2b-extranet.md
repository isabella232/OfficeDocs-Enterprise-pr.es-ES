---
title: Para obtener más información, consulte Crear una extranet de B2B con invitados administrados.
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
localization_priority: Normal
f1.keywords: NOCSH
description: Obtenga información sobre cómo crear un sitio o un equipo de extranet B2B con usuarios invitados administrados desde una organización asociada.
ms.openlocfilehash: cdf4470920a307d569fcfd650f40c77f4a5423a4
ms.sourcegitcommit: 4e50f43857f93f42b71650354d1aec9ed4cc7fe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "42549069"
---
# <a name="create-a-b2b-extranet-with-managed-guests"></a><span data-ttu-id="9b751-103">Para obtener más información, consulte Crear una extranet de B2B con invitados administrados.</span><span class="sxs-lookup"><span data-stu-id="9b751-103">Create a B2B extranet with managed guests</span></span>

<span data-ttu-id="9b751-104">Puede usar la [Administración de derechos de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) para crear una extranet B2B para colaborar con una organización asociada que use Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9b751-104">You can use [Azure Active Directory Entitlement Management](https://docs.microsoft.com/azure/active-directory/governance/entitlement-management-overview) to create a B2B extranet to collaborate with a partner organization that uses Azure Active Directory.</span></span> <span data-ttu-id="9b751-105">Esto permite a los usuarios inscribirse por sí mismos en el sitio o equipo de extranet y recibir acceso a través de un flujo de trabajo de aprobación.</span><span class="sxs-lookup"><span data-stu-id="9b751-105">This allows users to self-enroll in the extranet site or team and receive access via an approval workflow.</span></span>

<span data-ttu-id="9b751-106">Con este método de compartir recursos para colaboración, la organización asociada puede ayudarle a mantener y aprobar a los usuarios invitados en su extremo, lo que reduce la carga en el Departamento de ti y permite que los usuarios más familiarizados con el acuerdo de colaboración administren al usuario. al.</span><span class="sxs-lookup"><span data-stu-id="9b751-106">With this method of sharing resources for collaboration, the partner organization can help maintain and approve the guest users on their end, reducing the burden on your IT department and allowing those most familiar with the collaboration agreement to manage user access.</span></span>

<span data-ttu-id="9b751-107">En este artículo se describen los pasos para crear un paquete de recursos (en este caso, un sitio o un equipo) que puede compartir con una organización asociada a través de un modelo de registro de acceso sin ayuda de autoservicio.</span><span class="sxs-lookup"><span data-stu-id="9b751-107">This article walks through the steps to create a package of resources (in this case, a site or team) that you can share with a partner organization through a self-service access registration model.</span></span> 

<span data-ttu-id="9b751-108">Antes de empezar, cree el sitio o equipo que desea compartir con la organización asociada y habilítelo para compartir el invitado.</span><span class="sxs-lookup"><span data-stu-id="9b751-108">Before you begin, create the site or team that you want to share with the partner organization and enable it for guest sharing.</span></span> <span data-ttu-id="9b751-109">Consulte [colaborar con invitados en un sitio](collaborate-in-a-site.md) o [colaborar con los invitados en un equipo](collaborate-as-a-team.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="9b751-109">See [Collaborate with guests in a site](collaborate-in-a-site.md) or [Collaborate with guests in a team](collaborate-as-a-team.md) for more information.</span></span> <span data-ttu-id="9b751-110">También le recomendamos que revise [crear un entorno seguro de uso compartido de invitados](create-a-secure-guest-sharing-environment.md) para obtener información sobre las características de seguridad y cumplimiento que puede usar para ayudar a mantener sus directivas de gobierno al colaborar con invitados.</span><span class="sxs-lookup"><span data-stu-id="9b751-110">We also recommend that you review [Create a secure guest sharing environment](create-a-secure-guest-sharing-environment.md) for information about security and compliance features that you can use to help maintain your governance policies when collaborating with guests.</span></span>

## <a name="connect-the-partner-organization"></a><span data-ttu-id="9b751-111">Conexión de la organización asociada</span><span class="sxs-lookup"><span data-stu-id="9b751-111">Connect the partner organization</span></span>

<span data-ttu-id="9b751-112">Para invitar a invitados de una organización asociada, debe agregar el dominio del asociado como una organización conectada en Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="9b751-112">In order to invite guests from a partner organization, you need to add the the partner's domain as a connected organization in Azure Active Directory.</span></span>

<span data-ttu-id="9b751-113">Para agregar una organización conectada</span><span class="sxs-lookup"><span data-stu-id="9b751-113">To add a connected organization</span></span>
1. <span data-ttu-id="9b751-114">En [Azure Active Directory](https://aad.portal.azure.com), haga clic en **gobierno de identidades**.</span><span class="sxs-lookup"><span data-stu-id="9b751-114">In [Azure Active Directory](https://aad.portal.azure.com), click **Identity Governance**.</span></span>
2. <span data-ttu-id="9b751-115">Haga clic en **organizaciones conectadas**.</span><span class="sxs-lookup"><span data-stu-id="9b751-115">Click **Connected organizations**.</span></span>
4. <span data-ttu-id="9b751-116">Haga clic en **Agregar organización conectada**.</span><span class="sxs-lookup"><span data-stu-id="9b751-116">Click **Add connected organization**.</span></span>
5. <span data-ttu-id="9b751-117">Escriba un nombre y una descripción para la organización y, a continuación, haga clic en **siguiente: Directory + Domain**.</span><span class="sxs-lookup"><span data-stu-id="9b751-117">Type a name and description for the organization, and then click **Next: Directory + domain**.</span></span>
6. <span data-ttu-id="9b751-118">Haga clic en **Agregar directorio + dominio**.</span><span class="sxs-lookup"><span data-stu-id="9b751-118">Click **Add directory + domain**.</span></span>
7. <span data-ttu-id="9b751-119">Escriba el dominio de la organización a la que desea conectarse y, a continuación, haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="9b751-119">Type the domain for the organization that you want to connect, and then click **Add**.</span></span>
8. <span data-ttu-id="9b751-120">Haga clic en **conectar**y, a continuación, haga clic en **siguiente: patrocinadores**.</span><span class="sxs-lookup"><span data-stu-id="9b751-120">Click **Connect**, and then click **Next: Sponsors**.</span></span>
9. <span data-ttu-id="9b751-121">Agregue personas de su organización o de la organización a la que se va a conectar a quién desea aprobar el acceso para los usuarios invitados.</span><span class="sxs-lookup"><span data-stu-id="9b751-121">Add people from your organization or the organization that you're connecting to who you want to approve access for guest users.</span></span>
10. <span data-ttu-id="9b751-122">Haga clic en **siguiente: revisión + crear**.</span><span class="sxs-lookup"><span data-stu-id="9b751-122">Click **Next: Review + Create**.</span></span>
11. <span data-ttu-id="9b751-123">Revise la configuración que eligió y, a continuación, haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="9b751-123">Review the settings that you've chosen and then click **Create**.</span></span>

    ![Captura de pantalla de la página organizaciones conectadas en Azure Active Directory](media/identity-governance-connected-organizations.png)

## <a name="choose-the-resources-to-share"></a><span data-ttu-id="9b751-125">Elegir los recursos que se van a compartir</span><span class="sxs-lookup"><span data-stu-id="9b751-125">Choose the resources to share</span></span>

<span data-ttu-id="9b751-126">El primer paso para seleccionar recursos para compartir con una organización asociada es crear un catálogo que los contenga.</span><span class="sxs-lookup"><span data-stu-id="9b751-126">The first step in selecting resources to share with a partner organization is to create a catalog to contain them.</span></span>

<span data-ttu-id="9b751-127">Para crear un catálogo</span><span class="sxs-lookup"><span data-stu-id="9b751-127">To create a catalog</span></span>
1. <span data-ttu-id="9b751-128">En [Azure Active Directory](https://aad.portal.azure.com), haga clic en **gobierno de identidades**.</span><span class="sxs-lookup"><span data-stu-id="9b751-128">In [Azure Active Directory](https://aad.portal.azure.com), click **Identity Governance**.</span></span>
2. <span data-ttu-id="9b751-129">Haga clic en **catálogos**.</span><span class="sxs-lookup"><span data-stu-id="9b751-129">Click **Catalogs**.</span></span>
3. <span data-ttu-id="9b751-130">Haga clic en **nuevo catálogo**.</span><span class="sxs-lookup"><span data-stu-id="9b751-130">Click **New catalog**.</span></span>
4. <span data-ttu-id="9b751-131">Escriba un nombre y una descripción para el catálogo y asegúrese de que estén **habilitados** y habilitados **para los usuarios externos** establecidos en **sí**.</span><span class="sxs-lookup"><span data-stu-id="9b751-131">Type a name and description for the catalog and ensure that **Enabled** and **Enabled for external users** are both set to **Yes**.</span></span>
5. <span data-ttu-id="9b751-132">Haga clic en **Crear**.</span><span class="sxs-lookup"><span data-stu-id="9b751-132">Click **Create**.</span></span>

   ![Captura de pantalla de la página de catálogos en el gobierno de identidad de Azure Active Directory](media/identity-governance-catalogs.png)

<span data-ttu-id="9b751-134">Una vez creado el catálogo, agregue el sitio o equipo de SharePoint que desea compartir con la organización asociada.</span><span class="sxs-lookup"><span data-stu-id="9b751-134">Once the catalog has been created, you add the SharePoint site or team that you want to share with the partner organization.</span></span>

<span data-ttu-id="9b751-135">Para agregar recursos a un catálogo</span><span class="sxs-lookup"><span data-stu-id="9b751-135">To add resources to a catalog</span></span>
1. <span data-ttu-id="9b751-136">En el gobierno de identidad de Azure AD, haga clic en **catálogos**y, a continuación, haga clic en el catálogo en el que desea agregar recursos.</span><span class="sxs-lookup"><span data-stu-id="9b751-136">In Azure AD Identity Governance, click **Catalogs**, and then click the catalog where you want to add resources.</span></span>
2. <span data-ttu-id="9b751-137">Haga clic en **recursos** y, a continuación, en **Agregar recursos**.</span><span class="sxs-lookup"><span data-stu-id="9b751-137">Click **Resources** and then click **Add resources**.</span></span>
3. <span data-ttu-id="9b751-138">Seleccione los equipos o sitios de SharePoint que desea incluir en la extranet y, a continuación, haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="9b751-138">Select the teams or SharePoint sites that you want to include in your extranet, and then click **Add**.</span></span>

   ![Captura de pantalla de la página de recursos del catálogo en el gobierno de identidad de Azure Active Directory](media/identity-governance-catalog-resource.png)

<span data-ttu-id="9b751-140">Una vez que haya definido los recursos que desea compartir, el siguiente paso consiste en crear un paquete de acceso, que define el tipo de acceso que se concede a los usuarios asociados y el proceso de aprobación para los nuevos usuarios asociados que solicitan acceso.</span><span class="sxs-lookup"><span data-stu-id="9b751-140">Once you've defined the resources that you want to share, the next step is to create an access package, which defines the type of access that partner users are granted and the approval process for new partner users requesting access.</span></span>

<span data-ttu-id="9b751-141">Para crear un paquete de Access</span><span class="sxs-lookup"><span data-stu-id="9b751-141">To create an access package</span></span>
1. <span data-ttu-id="9b751-142">En el gobierno de identidad de Azure AD, haga clic en **catálogos**y, a continuación, haga clic en el catálogo en el que desea crear un paquete de acceso.</span><span class="sxs-lookup"><span data-stu-id="9b751-142">In Azure AD Identity Governance, click **Catalogs**, and then click the catalog where you want to create an access package.</span></span>
2. <span data-ttu-id="9b751-143">Haga clic en **paquetes de Access**y, a continuación, en **nuevo paquete de acceso**.</span><span class="sxs-lookup"><span data-stu-id="9b751-143">Click **Access packages**, and then click **New access package**.</span></span>
3. <span data-ttu-id="9b751-144">Escriba un nombre y una descripción para el paquete de Access y, a continuación, haga clic en **siguiente: roles de recursos**.</span><span class="sxs-lookup"><span data-stu-id="9b751-144">Type a name and description for the access package, and then click **Next: Resource roles**.</span></span>
4. <span data-ttu-id="9b751-145">Elija los recursos del catálogo que desea usar para la extranet.</span><span class="sxs-lookup"><span data-stu-id="9b751-145">Choose the resources from the catalog that you want to use for your extranet.</span></span>
5. <span data-ttu-id="9b751-146">Para cada recurso, en la columna **rol** , elija el rol de usuario que desea conceder a los usuarios invitados que usan la extranet.</span><span class="sxs-lookup"><span data-stu-id="9b751-146">For each resource, in the **Role** column, choose the user role you want to grant to the guest users who use the extranet.</span></span>
6. <span data-ttu-id="9b751-147">Haga clic en **siguiente: solicitudes**.</span><span class="sxs-lookup"><span data-stu-id="9b751-147">Click **Next: Requests**.</span></span>
7. <span data-ttu-id="9b751-148">En **usuarios que pueden solicitar acceso**, elija **para los usuarios que no están en el directorio**.</span><span class="sxs-lookup"><span data-stu-id="9b751-148">Under **Users who can request access**, choose **For users not in your directory**.</span></span>
8. <span data-ttu-id="9b751-149">Asegúrese de que la opción **organizaciones conectadas específicas** está seleccionada y, a continuación, haga clic en **Agregar directorios**.</span><span class="sxs-lookup"><span data-stu-id="9b751-149">Ensure that the **Specific connected organizations** option is selected, and then click **Add directories**.</span></span>
9. <span data-ttu-id="9b751-150">Elige la organización conectada que agregaste anteriormente y, a continuación, haz clic en **seleccionar**</span><span class="sxs-lookup"><span data-stu-id="9b751-150">Choose the connected organization that you add earlier, and then click **Select**</span></span>
10. <span data-ttu-id="9b751-151">En **aprobación**, elija **sí** para **requerir aprobación**.</span><span class="sxs-lookup"><span data-stu-id="9b751-151">Under **Approval**, choose **Yes** for **Require approval**.</span></span>
11. <span data-ttu-id="9b751-152">En **primer aprobador**, elija uno de los patrocinadores que agregó anteriormente o elija un usuario específico.</span><span class="sxs-lookup"><span data-stu-id="9b751-152">Under **First approver**, choose one of the sponsors that you added earlier or choose a specific user.</span></span>
12. <span data-ttu-id="9b751-153">Haga clic en **Agregar suplencia** y seleccione un aprobador de reserva.</span><span class="sxs-lookup"><span data-stu-id="9b751-153">Click **Add fallback** and select a fallback approver.</span></span>
13. <span data-ttu-id="9b751-154">En **Habilitar**, elija **sí**.</span><span class="sxs-lookup"><span data-stu-id="9b751-154">Under **Enable**, choose **Yes**.</span></span>
14. <span data-ttu-id="9b751-155">Haga clic en **siguiente: ciclo de vida**.</span><span class="sxs-lookup"><span data-stu-id="9b751-155">Click **Next: Lifecycle**.</span></span>
15. <span data-ttu-id="9b751-156">Elija la configuración de caducidad y revisión de Access que desea usar y, a continuación, haga clic en **siguiente: revisión + crear**.</span><span class="sxs-lookup"><span data-stu-id="9b751-156">Choose the expiration and access review settings that you want to use, and then click **Next: Review + Create**.</span></span>
16. <span data-ttu-id="9b751-157">Revise la configuración y, a continuación, haga clic en **crear**.</span><span class="sxs-lookup"><span data-stu-id="9b751-157">Review your settings, and then click **Create**.</span></span>

    ![Captura de pantalla de la pantalla de paquetes de acceso en el gobierno de identidad de Azure Active Directory](media/identity-governance-access-packages.png)

<span data-ttu-id="9b751-159">Si está asociando con una organización de gran tamaño, es posible que quiera ocultar el paquete de Access.</span><span class="sxs-lookup"><span data-stu-id="9b751-159">If you're partnering with a large organization, you may want to hide the access package.</span></span> <span data-ttu-id="9b751-160">Si el paquete está oculto, los usuarios de la organización asociada no podrán ver el paquete en su portal de *acceso* .</span><span class="sxs-lookup"><span data-stu-id="9b751-160">If the package is hidden, then users in the partner organization will not see the package on their *My Access* portal.</span></span> <span data-ttu-id="9b751-161">En su lugar, se deben enviar a un vínculo directo para registrarse en el paquete.</span><span class="sxs-lookup"><span data-stu-id="9b751-161">Instead, they must be sent a direct link to sign up for the package.</span></span> <span data-ttu-id="9b751-162">Ocultar el paquete de acceso puede reducir el número de solicitudes de acceso inadecuadas y también puede ayudar a mantener los paquetes de acceso disponibles en el portal de la organización asociada.</span><span class="sxs-lookup"><span data-stu-id="9b751-162">Hiding the access package can reduce the number of inappropriate access requests and can also help keep available access packages organized in the partner organization's portal.</span></span>

<span data-ttu-id="9b751-163">Para establecer un paquete de Access en oculto</span><span class="sxs-lookup"><span data-stu-id="9b751-163">To set an access package to hidden</span></span>
1. <span data-ttu-id="9b751-164">En Azure AD control de identidad, haga clic en **paquetes de acceso**y, después, haga clic en el paquete de acceso.</span><span class="sxs-lookup"><span data-stu-id="9b751-164">In Azure AD Identity Governance, click **Access packages**, and then click your access package.</span></span>
2. <span data-ttu-id="9b751-165">En la página **información general** , haga clic en **Editar**.</span><span class="sxs-lookup"><span data-stu-id="9b751-165">On the **Overview** page, click **Edit**.</span></span>
3. <span data-ttu-id="9b751-166">En **propiedades**, elija **sí** para **ocultar**y, a continuación, haga clic en **Guardar**.</span><span class="sxs-lookup"><span data-stu-id="9b751-166">Under **Properties**, choose **Yes** for **Hidden**, and then click **Save**.</span></span>

   ![Captura de pantalla de una pantalla Editar propiedades del paquete de Access](media/identity-governance-access-package-hidden.png)

## <a name="invite-partner-users"></a><span data-ttu-id="9b751-168">Invitar a usuarios asociados</span><span class="sxs-lookup"><span data-stu-id="9b751-168">Invite partner users</span></span>

<span data-ttu-id="9b751-169">Si establece el paquete de Access en oculto, deberá enviar un vínculo directo a la organización asociada para que pueda solicitar acceso a su sitio o equipo.</span><span class="sxs-lookup"><span data-stu-id="9b751-169">If you set the access package to hidden, you need to send a direct link to the partner organization so that they can request access to your site or team.</span></span>

<span data-ttu-id="9b751-170">Para buscar el vínculo del portal de Access</span><span class="sxs-lookup"><span data-stu-id="9b751-170">To find the access portal link</span></span>
1. <span data-ttu-id="9b751-171">En Azure AD control de identidad, haga clic en **paquetes de acceso**y, después, haga clic en el paquete de acceso.</span><span class="sxs-lookup"><span data-stu-id="9b751-171">In Azure AD Identity Governance, click **Access packages**, and then click your access package.</span></span>
2. <span data-ttu-id="9b751-172">En la página **información general** , haga clic en el vínculo **copiar al portapapeles** del **vínculo del portal de acceso**.</span><span class="sxs-lookup"><span data-stu-id="9b751-172">On the **Overview** page, click **Copy to clipboard** link for the **My Access portal link**.</span></span>

   ![Captura de pantalla de las propiedades del paquete de Access con el vínculo del portal de Access](media/identity-governance-access-portal-link.png)

<span data-ttu-id="9b751-174">Una vez que haya copiado el vínculo, puede compartirlo con su contacto en la organización asociada y puede enviarlo a los usuarios de su equipo de colaboración.</span><span class="sxs-lookup"><span data-stu-id="9b751-174">Once you have copied the link, you can share it with your contact at the partner organization and they can send it to the users on their collaboration team.</span></span>

## <a name="see-also"></a><span data-ttu-id="9b751-175">Vea también</span><span class="sxs-lookup"><span data-stu-id="9b751-175">See Also</span></span>

[<span data-ttu-id="9b751-176">Crear un entorno seguro de uso compartido para invitados</span><span class="sxs-lookup"><span data-stu-id="9b751-176">Create a secure guest sharing environment</span></span>](create-a-secure-guest-sharing-environment.md)

