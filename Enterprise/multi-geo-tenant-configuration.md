---
title: Configuración de espacios empresariales en OneDrive para la Empresa multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Aprenda a configurar OneDrive para la Empresa multigeográfico.
ms.openlocfilehash: 6c4a1012f3f26265ef88d82c55bb3ac11cc82da4
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849876"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="e1de1-103">Configuración de espacios empresariales en OneDrive para la Empresa multigeográfico</span><span class="sxs-lookup"><span data-stu-id="e1de1-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="e1de1-p101">Antes de configurar el espacio empresarial de OneDrive para la Empresa multigeográfico, asegúrese de haber leído [Planear OneDrive para la Empresa multigeográfico](plan-for-multi-geo.md). Para seguir los pasos de este artículo, necesitará una lista de las ubicaciones geográficas que quiera habilitar como ubicaciones satélite y los usuarios de la prueba que quiera aprovisionar en esas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="e1de1-106">Agregar las capacidades multigeográficas del plan de Office 365 al espacio empresarial</span><span class="sxs-lookup"><span data-stu-id="e1de1-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="e1de1-p102">Para usar OneDrive para la Empresa multigeográfico, necesita el plan _Multi-Geo Capabilities in Office 365_ (Capacidades multigeográficas de Office 365). Trabaje con el equipo de cuenta para agregar este plan a su espacio empresarial. Su equipo de cuenta le pondrá en contacto con el especialista en licencias adecuado y le configurará el espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="e1de1-p103">Tenga en cuenta que el plan _Multi-Geo Capabilities in Office 365_ (Capacidades multigeográficas de Office 365) es un plan de servicio de nivel de usuario. Necesita una licencia para cada usuario que quiera hospedar en una ubicación por satélite. Puede agregar más licencias a medida que agregue usuarios en las ubicaciones por satélite.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="e1de1-113">Cuando haya aprovisionado el espacio empresarial con el plan _Capacidades multigeográficas en Office 365_, la pestaña **Geo locations** (Ubicaciones geográficas) estará disponible en el [Centro de administración de OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="e1de1-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="add-satellite-locations-to-your-tenant"></a><span data-ttu-id="e1de1-114">Agregar ubicaciones satélite a su espacio empresarial</span><span class="sxs-lookup"><span data-stu-id="e1de1-114">Add satellite locations to your tenant</span></span>

<span data-ttu-id="e1de1-p104">Debe añadir una ubicación satélite para cada ubicación geográfica donde quiere usar OneDrive para la Empresa. Las ubicaciones geográficas disponibles se muestran en la tabla siguiente:</span><span class="sxs-lookup"><span data-stu-id="e1de1-p104">You must add a satellite location for each geo location where you want to use OneDrive for Business. Available geo locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="e1de1-117"><strong>Ubicación</strong></span><span class="sxs-lookup"><span data-stu-id="e1de1-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="e1de1-118"><strong>Código</strong></span><span class="sxs-lookup"><span data-stu-id="e1de1-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="e1de1-119">Asia-Pacífico</span><span class="sxs-lookup"><span data-stu-id="e1de1-119">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="e1de1-120">APC</span><span class="sxs-lookup"><span data-stu-id="e1de1-120">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e1de1-121">Australia</span><span class="sxs-lookup"><span data-stu-id="e1de1-121">Australia</span></span></td>
<td align="left"><span data-ttu-id="e1de1-122">AUS</span><span class="sxs-lookup"><span data-stu-id="e1de1-122">AUS</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e1de1-123">Canadá</span><span class="sxs-lookup"><span data-stu-id="e1de1-123">Canada</span></span></td>
<td align="left"><span data-ttu-id="e1de1-124">CAN</span><span class="sxs-lookup"><span data-stu-id="e1de1-124">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e1de1-125">Europa, Oriente medio y África</span><span class="sxs-lookup"><span data-stu-id="e1de1-125">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="e1de1-126">EUR</span><span class="sxs-lookup"><span data-stu-id="e1de1-126">EUR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e1de1-127">Francia</span><span class="sxs-lookup"><span data-stu-id="e1de1-127">France</span></span></td>
<td align="left"><span data-ttu-id="e1de1-128">FRA</span><span class="sxs-lookup"><span data-stu-id="e1de1-128">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e1de1-129">Japón</span><span class="sxs-lookup"><span data-stu-id="e1de1-129">Japan</span></span></td>
<td align="left"><span data-ttu-id="e1de1-130">JPN</span><span class="sxs-lookup"><span data-stu-id="e1de1-130">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="e1de1-131">Corea</span><span class="sxs-lookup"><span data-stu-id="e1de1-131">Korea</span></span></td>
<td align="left"><span data-ttu-id="e1de1-132">KOR</span><span class="sxs-lookup"><span data-stu-id="e1de1-132">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e1de1-133">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="e1de1-133">North America</span></span></td>
<td align="left"><span data-ttu-id="e1de1-134">NAM</span><span class="sxs-lookup"><span data-stu-id="e1de1-134">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="e1de1-135">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="e1de1-135">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="e1de1-136">GBR</span><span class="sxs-lookup"><span data-stu-id="e1de1-136">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="e1de1-137">Para agregar una ubicación de satélite</span><span class="sxs-lookup"><span data-stu-id="e1de1-137">To add a satellite geo location</span></span>

1. <span data-ttu-id="e1de1-138">Abra el [Centro de administración de OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="e1de1-138">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="e1de1-139">Navegue a la pestaña **Geo locations** (Ubicaciones geográficas).</span><span class="sxs-lookup"><span data-stu-id="e1de1-139">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="e1de1-140">Haga clic en **Agregar ubicación**.</span><span class="sxs-lookup"><span data-stu-id="e1de1-140">Click **Add location**.</span></span>

4. <span data-ttu-id="e1de1-141">Seleccione la ubicación que quiere agregar y haga clic en **Siguiente**.</span><span class="sxs-lookup"><span data-stu-id="e1de1-141">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="e1de1-142">Escriba el dominio que quiere usar con la ubicación geográfica y haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="e1de1-142">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="e1de1-143">Haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="e1de1-143">Click **Close**.</span></span>

<span data-ttu-id="e1de1-p105">El aprovisionamiento puede tardar desde unas horas hasta 72 horas, dependiendo del tamaño del espacio empresarial. Una vez completado el aprovisionamiento de una ubicación por satélite, recibirá un correo electrónico de confirmación. Cuando la nueva ubicación geográfica aparezca en azul en el mapa de la pestaña **Ubicaciones geográficas** del Centro de administración de OneDrive, podrá proceder a establecer la ubicación de datos preferida de los usuarios a esa ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p105">Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="e1de1-p106">La nueva ubicación por satélite se configurará con la configuración predeterminada. Esto le permitirá configurar esa ubicación por satélite según sus necesidades de cumplimiento local.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="e1de1-149">Establecimiento de la ubicación de datos preferida de los usuarios</span><span class="sxs-lookup"><span data-stu-id="e1de1-149">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="e1de1-p107">Cuando haya habilitado las ubicaciones de satélite necesarias, puede actualizar su cuenta de usuario para que use la ubicación de datos adecuada. Se recomienda establecer una ubicación de datos preferida para cada uno de los usuarios, aunque el usuario permanezca en la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="e1de1-152">Se recomienda iniciar las validaciones con un usuario de prueba o un grupo pequeño de usuarios antes de implementar la versión multigeográfica en la organización completa.</span><span class="sxs-lookup"><span data-stu-id="e1de1-152">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="e1de1-p108">En AAD hay dos tipos de objetos de usuario: usuarios solo de nube y usuarios sincronizados. Siga las instrucciones adecuadas para el tipo de usuario.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="e1de1-155">Sincronizar la ubicación de datos preferida del usuario con AD Connect</span><span class="sxs-lookup"><span data-stu-id="e1de1-155">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="e1de1-p109">Si los usuarios de la compañía se sincronizan en un sistema de Active Directory local con Azure Active Directory, su PreferredDataLocation debe rellenarse en AD y sincronizarse con AAD. Siga el proceso de [Sincronización de Azure AD Connect: cambiar a la configuración predeterminada](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) para configurar la sincronización de la ubicación de datos preferida en Active Directory local con Azure Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="e1de1-158">Se recomienda incluir el establecimiento de la ubicación de datos preferida del usuario como parte del flujo de trabajo de creación de usuarios estándar.</span><span class="sxs-lookup"><span data-stu-id="e1de1-158">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1de1-p110">Para los nuevos usuarios que no tengan aprovisionado OneDrive, espere como mínimo 24 horas tras sincronizar la ubicación de datos preferida (PDL) de un usuario con Azure Active Directory para que los cambios se propaguen antes de que el usuario inicie sesión en OneDrive para la Empresa. (El establecimiento de la PDL antes de que el usuario inicie sesión para aprovisionar OneDrive para la Empresa garantiza que la nueva instancia de OneDrive del usuario se aprovisionará en la ubicación correcta).</span><span class="sxs-lookup"><span data-stu-id="e1de1-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="e1de1-161">Establecimiento de la ubicación de datos preferida de usuarios solo de nube</span><span class="sxs-lookup"><span data-stu-id="e1de1-161">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="e1de1-162">Si los usuarios de la compañía no se sincronizan en un sistema de Active Directory local con Azure Active Directory, lo que indica que se crearon en Office 365 o Azure Active Directory, la PDL debe establecerse con Azure Active Directory PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1de1-162">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="e1de1-p111">Los procedimientos de esta sección requieren el [Módulo Microsoft Azure Active Directory para Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si ya tiene instalado Azure Active Directory PowerShell, asegúrese de actualizarlo a la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="e1de1-165">Abra el Módulo Microsoft Azure Active Directory para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e1de1-165">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="e1de1-166">Ejecute `Connect-MsolService` y escriba las credenciales del administrador global del espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="e1de1-166">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="e1de1-p112">Use el cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) para establecer la ubicación de datos preferida de cada uno de los usuarios. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e1de1-p112">Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="e1de1-p113">Puede comprobar que la ubicación de datos preferida se actualizó correctamente mediante el cmdlet Get-MsolUser. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e1de1-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

<span data-ttu-id="e1de1-171">Se recomienda incluir el establecimiento de la ubicación de datos preferida del usuario como parte del flujo de trabajo de creación de usuarios estándar.</span><span class="sxs-lookup"><span data-stu-id="e1de1-171">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e1de1-p114">Para los nuevos usuarios que no tengan aprovisionado OneDrive, espere como mínimo 24 horas tras establecer la PDL de un usuario para que los cambios se propaguen antes de que el usuario inicie sesión en OneDrive. (El establecimiento de la PDL antes de que el usuario inicie sesión para aprovisionar OneDrive para la Empresa garantiza que la nueva instancia de OneDrive del usuario se aprovisionará en la ubicación correcta).</span><span class="sxs-lookup"><span data-stu-id="e1de1-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="e1de1-174">Aprovisionamiento de OneDrive y efecto de la PDL</span><span class="sxs-lookup"><span data-stu-id="e1de1-174">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="e1de1-p115">Si el usuario ya ha creado un sitio de OneDrive en el espacio empresarial, el establecimiento de su PDL no trasladará automáticamente su instancia de OneDrive existente. Para mover la instancia de OneDrive de un usuario, vea [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) (Transferencia geográfica de OneDrive para la Empresa) y siga las instrucciones para mover OneDrive de una ubicación geográfica a otra.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="e1de1-177">Si el usuario no tiene un sitio de OneDrive en el espacio empresarial, se le aprovisionará OneDrive de acuerdo con el valor de PDL, suponiendo que la PDL del usuario coincida con una de las ubicaciones satélite de la empresa.</span><span class="sxs-lookup"><span data-stu-id="e1de1-177">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="e1de1-178">Configuración de la búsqueda multigeográfica</span><span class="sxs-lookup"><span data-stu-id="e1de1-178">Configuring Multi-Geo search</span></span>

<span data-ttu-id="e1de1-179">El espacio empresarial multigeográfico tendrá funcionalidades de búsqueda agregada, lo que permite devolver resultados desde cualquier lugar en el espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="e1de1-179">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="e1de1-180">De forma predeterminada, las búsquedas en estos puntos de entrada devolverán resultados agregados, aunque cada índice de búsqueda se encuentre en la ubicación geográfica correspondiente:</span><span class="sxs-lookup"><span data-stu-id="e1de1-180">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="e1de1-181">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="e1de1-181">OneDrive for business</span></span>

- <span data-ttu-id="e1de1-182">Delve</span><span class="sxs-lookup"><span data-stu-id="e1de1-182">Delve</span></span>

- <span data-ttu-id="e1de1-183">Página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="e1de1-183">SharePoint Home</span></span>

- <span data-ttu-id="e1de1-184">Centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="e1de1-184">Search Center</span></span>

<span data-ttu-id="e1de1-185">Además, pueden configurarse funcionalidades de búsqueda multigeográficas para las aplicaciones de búsqueda personalizada que usan la API de SharePoint Search.</span><span class="sxs-lookup"><span data-stu-id="e1de1-185">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="e1de1-186">Revise [Configurar la búsqueda en OneDrive para la Empresa multigeográfico](configure-search-for-multi-geo.md) para obtener instrucciones, incluidas las limitaciones y diferencias.</span><span class="sxs-lookup"><span data-stu-id="e1de1-186">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="e1de1-187">Validación de la configuración de OneDrive para la Empresa multigeográfico</span><span class="sxs-lookup"><span data-stu-id="e1de1-187">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="e1de1-p116">A continuación se muestran algunos casos de uso básicos que tal vez quiera incluir en el plan de validación antes implementar OneDrive para la Empresa multigeográfico de manera general en la compañía. Después de completar estas pruebas y los casos de uso adicionales que sean relevantes para su compañía, puede continuar y agregar los usuarios al grupo piloto inicial.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="e1de1-190">**OneDrive para la Empresa**</span><span class="sxs-lookup"><span data-stu-id="e1de1-190">**OneDrive for Business**</span></span>

<span data-ttu-id="e1de1-p117">Seleccione OneDrive desde el iniciador de aplicaciones de Office 365 y confirme que le dirige automáticamente a la ubicación geográfica apropiada del usuario, en función de la PDL del usuario. OneDrive para la Empresa debería ahora comenzar el aprovisionamiento en esa ubicación. Una vez aprovisionado, pruebe a cargar y descargar algunos documentos.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="e1de1-194">**Aplicación móvil de OneDrive**</span><span class="sxs-lookup"><span data-stu-id="e1de1-194">**OneDrive Mobile App**</span></span>

<span data-ttu-id="e1de1-p118">Inicie sesión en la aplicación móvil de OneDrive con sus credenciales de cuenta de evaluación. Confirme que puede ver sus archivos de OneDrive para la Empresa y puede interactuar con ellos desde su dispositivo móvil.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="e1de1-197">**Cliente de sincronización de OneDrive**</span><span class="sxs-lookup"><span data-stu-id="e1de1-197">**OneDrive sync client**</span></span>

<span data-ttu-id="e1de1-p119">Confirme que el cliente de sincronización de OneDrive detecta automáticamente la ubicación geográfica de OneDrive para la Empresa al iniciar sesión. Si quiere descargar el cliente de sincronización, puede hacer clic en **Sincronización** en la biblioteca de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="e1de1-200">**Aplicaciones de Office**</span><span class="sxs-lookup"><span data-stu-id="e1de1-200">**Office applications**</span></span>

<span data-ttu-id="e1de1-p120">Para confirmar que tiene acceso a OneDrive para la Empresa, inicie sesión desde una aplicación de Office como Word. Abra la aplicación de Office y seleccione "OneDrive – <TenantName>". Office detectará la ubicación de OneDrive y mostrará los archivos que se pueden abrir.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="e1de1-204">**Uso compartido**</span><span class="sxs-lookup"><span data-stu-id="e1de1-204">**Sharing**</span></span>

<span data-ttu-id="e1de1-p121">Pruebe el uso compartido de archivos de OneDrive. Confirme que el selector de personas muestra todos los usuarios de SharePoint Online independientemente de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="e1de1-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
