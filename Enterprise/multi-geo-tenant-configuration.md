---
title: Configuración de inquilino Multi-Geo de Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
ms.custom: ''
localization_priority: Priority
description: Obtenga información sobre cómo configurar Office 365 Multi-Geo.
ms.openlocfilehash: 8e845a7d1c3a8d83189a77c5fc7a6e8d3358a425
ms.sourcegitcommit: 5fe1c9be652222d6956c7dad5949ddcf0bd27041
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2019
ms.locfileid: "38076394"
---
# <a name="office-365-multi-geo-tenant-configuration"></a><span data-ttu-id="5a343-103">Configuración de inquilino Multi-Geo de Office 365</span><span class="sxs-lookup"><span data-stu-id="5a343-103">Office 365 Multi-Geo tenant configuration</span></span>

<span data-ttu-id="5a343-104">Antes de configurar su inquilino de Office 365 Multi-Geo, asegúrese de haber leído [Plan para Office 365 Multi-Geo](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="5a343-104">Before you configure your tenant for Office 365 Multi-Geo, be sure you have read [Plan for Office 365 Multi-Geo](plan-for-multi-geo.md).</span></span> <span data-ttu-id="5a343-105">Para seguir los pasos de este artículo, necesitará una lista de las ubicaciones geográficas que quiera habilitar como ubicaciones satélite y los usuarios de la prueba que quiera aprovisionar en esas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="5a343-105">To follow the steps in this article, you'll need a list of the geo locations that you want to enable as satellite locations, and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="5a343-106">Agregar las capacidades multigeográficas del plan de Office 365 al espacio empresarial</span><span class="sxs-lookup"><span data-stu-id="5a343-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="5a343-107">Para usar Office 365 Multi-Geo, necesita el plan _Capacidades multigeográficas en Office 365_.</span><span class="sxs-lookup"><span data-stu-id="5a343-107">To use Office 365 Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan.</span></span> <span data-ttu-id="5a343-108">Trabaje con el equipo de cuentas para agregar este plan a su espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="5a343-108">Work with your account team to add this plan to your tenant.</span></span> <span data-ttu-id="5a343-109">Su equipo de cuentas le pondrá en contacto con el especialista en licencias adecuado y configurará el espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="5a343-109">Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="5a343-p103">Tenga en cuenta que el plan _Multi-Geo Capabilities in Office 365_ (Capacidades multigeográficas de Office 365) es un plan de servicio de nivel de usuario. Necesita una licencia para cada usuario que quiera hospedar en una ubicación por satélite. Puede agregar más licencias a medida que agregue usuarios en las ubicaciones por satélite.</span><span class="sxs-lookup"><span data-stu-id="5a343-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="5a343-113">Cuando haya aprovisionado el espacio empresarial con el plan _Capacidades multigeográficas en Office 365_, la pestaña **Ubicaciones geográficas** estará disponible en los centros de administración de OneDrive y SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5a343-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the OneDrive and SharePoint admin centers.</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="5a343-114">Agregar ubicaciones satélite a su espacio empresarial</span><span class="sxs-lookup"><span data-stu-id="5a343-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="5a343-115">Debe añadir una ubicación satélite para cada ubicación geográfica donde quiere almacenar datos.</span><span class="sxs-lookup"><span data-stu-id="5a343-115">You must add a satellite location for each geo location where you want to store data.</span></span> <span data-ttu-id="5a343-116">En la tabla siguiente se muestran las ubicaciones geográficas disponibles:</span><span class="sxs-lookup"><span data-stu-id="5a343-116">Available geo locations are shown in the following table:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Captura de pantalla de la página de ubicaciones geográficas en el Centro de administración de SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="5a343-118">Para agregar una ubicación de satélite</span><span class="sxs-lookup"><span data-stu-id="5a343-118">To add a satellite location</span></span>

1. <span data-ttu-id="5a343-119">Abra el Centro de administración de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="5a343-119">Open the SharePoint admin center.</span></span>

2. <span data-ttu-id="5a343-120">Navegue a la pestaña **Geo locations** (Ubicaciones geográficas).</span><span class="sxs-lookup"><span data-stu-id="5a343-120">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="5a343-121">Haga clic en **Agregar ubicación**.</span><span class="sxs-lookup"><span data-stu-id="5a343-121">Click **Add location**.</span></span>

4. <span data-ttu-id="5a343-122">Seleccione la ubicación que quiere agregar y haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="5a343-122">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="5a343-123">Escriba el dominio que quiere usar con la ubicación geográfica y haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="5a343-123">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="5a343-124">Haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="5a343-124">Click **Close**.</span></span>

<span data-ttu-id="5a343-p105">El aprovisionamiento puede tardar desde unas horas hasta 72 horas, dependiendo del tamaño del espacio empresarial. Una vez completado el aprovisionamiento de una ubicación por satélite, recibirá un correo electrónico de confirmación. Cuando la nueva ubicación geográfica aparezca en azul en el mapa de la pestaña **Ubicaciones geográficas** del Centro de administración de OneDrive, podrá proceder a establecer la ubicación de datos preferida de los usuarios a esa ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="5a343-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="5a343-p106">La nueva ubicación por satélite se configurará con la configuración predeterminada. Esto le permitirá configurar esa ubicación por satélite según sus necesidades de cumplimiento local.</span><span class="sxs-lookup"><span data-stu-id="5a343-p106">Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="5a343-130">Establecimiento de la ubicación de datos preferida de los usuarios</span><span class="sxs-lookup"><span data-stu-id="5a343-130">Setting users' preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="5a343-p107">Cuando haya habilitado las ubicaciones de satélite necesarias, puede actualizar su cuenta de usuario para que use la ubicación de datos adecuada. Se recomienda establecer una ubicación de datos preferida para cada uno de los usuarios, aunque el usuario permanezca en la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="5a343-p107">Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a343-133">Si se establece la ubicación de datos preferida de un usuario a una ubicación que no se ha configurado como una ubicación satélite o la ubicación central, el sistema usará de forma predeterminada la ubicación central para el aprovisionamiento de sitios de SharePoint, de OneDrive y de buzones de grupo.</span><span class="sxs-lookup"><span data-stu-id="5a343-133">If a user's preferred data location is set to a location that has not been configured as a satellite location or the central location, the system will default to the central location when provisioning OneDrive and SharePoint sites and Group mailboxes.</span></span>

> [!TIP]
> <span data-ttu-id="5a343-134">Se recomienda iniciar las validaciones con un usuario de prueba o un grupo pequeño de usuarios antes de implementar la versión multigeográfica en la organización completa.</span><span class="sxs-lookup"><span data-stu-id="5a343-134">We recommend that you begin validations with a test user or small group of users before rolling out multi-geo to your broader organization.</span></span>

<span data-ttu-id="5a343-135">En Azure Active Directory hay dos tipos de objetos de usuario: usuarios solo de nube y usuarios sincronizados.</span><span class="sxs-lookup"><span data-stu-id="5a343-135">In Azure Active Directory there are two types of user objects: cloud only users and synchronized users.</span></span> <span data-ttu-id="5a343-136">Siga las instrucciones adecuadas para el tipo de usuario.</span><span class="sxs-lookup"><span data-stu-id="5a343-136">Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a><span data-ttu-id="5a343-137">Sincronizar la ubicación de datos preferida del usuario con Azure Active Directory Connect</span><span class="sxs-lookup"><span data-stu-id="5a343-137">Synchronize user's Preferred Data Location using Azure Active Directory Connect</span></span> 

<span data-ttu-id="5a343-p109">Si los usuarios de la compañía se sincronizan en un sistema de Active Directory local con Azure Active Directory, el elemento PreferredDataLocation tiene que rellenarse en AD y sincronizarse con AAD. Siga el proceso de [Sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferida de recursos de Office 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) para configurar la sincronización de la ubicación de datos preferida del entorno local de Active Directory en Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="5a343-p109">If your company’s users are synchronized from an on-premises Active Directory system to Azure Active Directory, their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) to configure Preferred Data Location sync from on-premises Active Directory to Azure Active Directory.</span></span>

<span data-ttu-id="5a343-140">Se recomienda incluir el establecimiento de la ubicación de datos preferida del usuario como parte del flujo de trabajo de creación de usuarios estándar.</span><span class="sxs-lookup"><span data-stu-id="5a343-140">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a343-141">Para los nuevos usuarios que no tengan aprovisionado OneDrive, espere como mínimo 24 horas tras sincronizar la ubicación de datos preferida (PDL) de un usuario con Azure Active Directory para que los cambios se propaguen antes de que el usuario inicie sesión en OneDrive para la Empresa.</span><span class="sxs-lookup"><span data-stu-id="5a343-141">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to Azure Active Directory for the changes to propagate before the user logs in to OneDrive for Business.</span></span> <span data-ttu-id="5a343-142">(El establecimiento de la PDL antes de que el usuario inicie sesión para aprovisionar OneDrive para la Empresa garantiza que la nueva instancia de OneDrive del usuario se aprovisionará en la ubicación correcta).</span><span class="sxs-lookup"><span data-stu-id="5a343-142">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="5a343-143">Establecimiento de la ubicación de datos preferida de usuarios solo de nube</span><span class="sxs-lookup"><span data-stu-id="5a343-143">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="5a343-144">Si los usuarios de la compañía no se sincronizan en un sistema de Active Directory local con Azure Active Directory, lo que indica que se crearon en Office 365 o Azure Active Directory, la PDL debe establecerse con Azure Active Directory PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a343-144">If your company's users are not synchronized from an on-premises Active Directory system to Azure Active Directory, meaning they are created in Office 365 or Azure Active Directory, then the PDL must be set using Azure Active Directory PowerShell.</span></span>

<span data-ttu-id="5a343-p111">Los procedimientos de esta sección requieren el [Módulo Microsoft Azure Active Directory para Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si ya tiene instalado Azure Active Directory PowerShell, asegúrese de actualizarlo a la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="5a343-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have Azure Active Directory PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="5a343-147">Abra el Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a343-147">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="5a343-148">Ejecute `Connect-MsolService` y escriba las credenciales del administrador global del espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="5a343-148">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="5a343-p112">Use el cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) para establecer la ubicación de datos preferida de cada uno de los usuarios. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5a343-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="5a343-p113">Puede comprobar que la ubicación de datos preferida se actualizó correctamente mediante el cmdlet Get-MsolUser. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5a343-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Captura de pantalla de la ventana de PowerShell que muestra set-msoluser](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="5a343-154">Se recomienda incluir el establecimiento de la ubicación de datos preferida del usuario como parte del flujo de trabajo de creación de usuarios estándar.</span><span class="sxs-lookup"><span data-stu-id="5a343-154">We recommend that you include setting the user's Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a343-155">Para los nuevos usuarios que no tengan aprovisionado OneDrive, espere como mínimo 24 horas tras establecer la PDL de un usuario para que los cambios se propaguen antes de que el usuario inicie sesión en OneDrive.</span><span class="sxs-lookup"><span data-stu-id="5a343-155">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to OneDrive.</span></span> <span data-ttu-id="5a343-156">(El establecimiento de la PDL antes de que el usuario inicie sesión para aprovisionar OneDrive para la Empresa garantiza que la nueva instancia de OneDrive del usuario se aprovisionará en la ubicación correcta).</span><span class="sxs-lookup"><span data-stu-id="5a343-156">(Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user's new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="5a343-157">Aprovisionamiento de OneDrive y efecto de la PDL</span><span class="sxs-lookup"><span data-stu-id="5a343-157">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="5a343-158">Si el usuario ya ha creado un sitio de OneDrive en el espacio empresarial, el establecimiento de su PDL no trasladará automáticamente su instancia de OneDrive existente.</span><span class="sxs-lookup"><span data-stu-id="5a343-158">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive.</span></span> <span data-ttu-id="5a343-159">Para mover la instancia de OneDrive de un usuario, vea [Transferencia geográfica de OneDrive para la Empresa](move-onedrive-between-geo-locations.md) y siga las instrucciones para mover OneDrive de una ubicación geográfica a otra.</span><span class="sxs-lookup"><span data-stu-id="5a343-159">To move a user's OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span> <span data-ttu-id="5a343-160">(Tenga en cuenta que el buzón de Exchange del usuario se mueve automáticamente al establecer la PDL del usuario)</span><span class="sxs-lookup"><span data-stu-id="5a343-160">(Note that the user's Exchange mailbox does move automatically when you set the user's PDL.)</span></span>

<span data-ttu-id="5a343-161">Si el usuario no tiene un sitio de OneDrive en el espacio empresarial, se le aprovisionará OneDrive de acuerdo con el valor de PDL, suponiendo que la PDL del usuario coincida con una de las ubicaciones satélite de la empresa.</span><span class="sxs-lookup"><span data-stu-id="5a343-161">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company's satellite locations.</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="5a343-162">Configuración de la búsqueda multigeográfica</span><span class="sxs-lookup"><span data-stu-id="5a343-162">Configuring Multi-Geo search</span></span>

<span data-ttu-id="5a343-163">El espacio empresarial multigeográfico tendrá funcionalidades de búsqueda agregada, lo que permite devolver resultados desde cualquier lugar en el espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="5a343-163">Your multi-geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="5a343-164">De forma predeterminada, las búsquedas en estos puntos de entrada devolverán resultados agregados, aunque cada índice de búsqueda se encuentre en la ubicación geográfica correspondiente:</span><span class="sxs-lookup"><span data-stu-id="5a343-164">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="5a343-165">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="5a343-165">OneDrive for business</span></span>

- <span data-ttu-id="5a343-166">Delve</span><span class="sxs-lookup"><span data-stu-id="5a343-166">Delve</span></span>

- <span data-ttu-id="5a343-167">Página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="5a343-167">SharePoint Home</span></span>

- <span data-ttu-id="5a343-168">Centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="5a343-168">Search Center</span></span>

<span data-ttu-id="5a343-169">Además, pueden configurarse funcionalidades de búsqueda multigeográficas para las aplicaciones de búsqueda personalizada que usan la API de SharePoint Search.</span><span class="sxs-lookup"><span data-stu-id="5a343-169">Additionally, multi-geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="5a343-170">Revise [Configurar la búsqueda en OneDrive para la Empresa multigeográfico](configure-search-for-multi-geo.md) para obtener instrucciones, incluidas las limitaciones y diferencias.</span><span class="sxs-lookup"><span data-stu-id="5a343-170">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-office-365-multi-geo-configuration"></a><span data-ttu-id="5a343-171">Validar la configuración de Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="5a343-171">Validating the Office 365 Multi-Geo configuration</span></span>

<span data-ttu-id="5a343-172">A continuación se muestran algunos casos de uso básicos que tal vez quiera incluir en el plan de validación antes implementar Office 365 Multi-Geo de manera general en la compañía.</span><span class="sxs-lookup"><span data-stu-id="5a343-172">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Office 365 Multi-Geo to your company.</span></span> <span data-ttu-id="5a343-173">Después de completar estas pruebas y los casos de uso adicionales que sean relevantes para su compañía, puede continuar y agregar los usuarios al grupo piloto inicial.</span><span class="sxs-lookup"><span data-stu-id="5a343-173">Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="5a343-174">**OneDrive para la Empresa**</span><span class="sxs-lookup"><span data-stu-id="5a343-174">**OneDrive for Business**</span></span>

<span data-ttu-id="5a343-175">Seleccione OneDrive desde el iniciador de aplicaciones de Office 365 y confirme que le dirige automáticamente a la ubicación geográfica apropiada del usuario, en función de la PDL del usuario.</span><span class="sxs-lookup"><span data-stu-id="5a343-175">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo location for the user, based on the user's PDL.</span></span> <span data-ttu-id="5a343-176">OneDrive para la Empresa debería ahora comenzar el aprovisionamiento en esa ubicación.</span><span class="sxs-lookup"><span data-stu-id="5a343-176">OneDrive for Business should now begin provisioning at that location.</span></span> <span data-ttu-id="5a343-177">Una vez aprovisionado, pruebe a cargar y descargar algunos documentos.</span><span class="sxs-lookup"><span data-stu-id="5a343-177">Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="5a343-178">**Aplicación móvil de OneDrive**</span><span class="sxs-lookup"><span data-stu-id="5a343-178">**OneDrive Mobile App**</span></span>

<span data-ttu-id="5a343-p118">Inicie sesión en la aplicación móvil de OneDrive con sus credenciales de cuenta de evaluación. Confirme que puede ver sus archivos de OneDrive para la Empresa y puede interactuar con ellos desde su dispositivo móvil.</span><span class="sxs-lookup"><span data-stu-id="5a343-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="5a343-181">**Cliente de sincronización de OneDrive**</span><span class="sxs-lookup"><span data-stu-id="5a343-181">**OneDrive sync client**</span></span>

<span data-ttu-id="5a343-p119">Confirme que el cliente de sincronización de OneDrive detecta automáticamente la ubicación geográfica de OneDrive para la Empresa al iniciar sesión. Si quiere descargar el cliente de sincronización, puede hacer clic en **Sincronización** en la biblioteca de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="5a343-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="5a343-184">**Aplicaciones de Office**</span><span class="sxs-lookup"><span data-stu-id="5a343-184">**Office applications**</span></span>

<span data-ttu-id="5a343-p120">Para confirmar que tiene acceso a OneDrive para la Empresa, inicie sesión desde una aplicación de Office como Word. Abra la aplicación de Office y seleccione "OneDrive – <TenantName>". Office detectará la ubicación de OneDrive y mostrará los archivos que se pueden abrir.</span><span class="sxs-lookup"><span data-stu-id="5a343-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="5a343-188">**Uso compartido**</span><span class="sxs-lookup"><span data-stu-id="5a343-188">**Sharing**</span></span>

<span data-ttu-id="5a343-p121">Pruebe el uso compartido de archivos de OneDrive. Confirme que el selector de personas muestra todos los usuarios de SharePoint Online independientemente de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="5a343-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.</span></span>
