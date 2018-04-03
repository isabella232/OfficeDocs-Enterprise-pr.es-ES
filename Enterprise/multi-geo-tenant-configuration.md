---
title: OneDrive para configuración de inquilinos de negocios Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Aprenda a configurar OneDrive para negocios Multi-Geo.
ms.openlocfilehash: 4ef31df802eeaedf2eecbdd295d2e359816e4909
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a><span data-ttu-id="1bf22-103">OneDrive para configuración de inquilinos de negocios Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="1bf22-103">OneDrive for Business Multi-Geo tenant configuration</span></span>

<span data-ttu-id="1bf22-p101">Antes de configurar a su arrendatario para OneDrive de negocios Multi-Geo, asegúrese de que ha leído el [Plan de OneDrive de negocios Multi-Geo](plan-for-multi-geo.md). Para seguir los pasos de este artículo, necesitará una lista de las ubicaciones que desea habilitar y los usuarios de prueba que desee aprovisionar para dichas ubicaciones.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p101">Before you configure your tenant for OneDrive for Business Multi-Geo, be sure you have read [Plan for OneDrive for Business Multi-Geo](plan-for-multi-geo.md). To follow the steps in this article, you’ll need a list of the locations that you want to enable and the test users that you want to provision for those locations.</span></span>

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a><span data-ttu-id="1bf22-106">Agregar las capacidades Multi-Geo en el plan de Office 365 a los inquilinos</span><span class="sxs-lookup"><span data-stu-id="1bf22-106">Add the Multi-Geo Capabilities in Office 365 plan to your tenant</span></span>

<span data-ttu-id="1bf22-p102">Para utilizar OneDrive para negocios Multi-Geo, necesita el plan _Multi-Geo capacidades de Office 365_ . Trabaje con su equipo de cuenta para agregar este plan a los inquilinos. Su equipo de cuentas se conectará con el especialista de licencia apropiado y obtener al inquilino configurado.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p102">To use OneDrive for Business Multi-Geo, you need the _Multi-Geo Capabilities in Office 365_ plan. Work with your account team to add this plan to your tenant. Your account team will connect you with the appropriate licensing specialist and get your tenant configured.</span></span>

<span data-ttu-id="1bf22-p103">Tenga en cuenta que el plan de _Capacidades de Multi-Geo en Office 365_ es un servicio de nivel de usuario. Necesita una licencia para cada usuario que desee alojar en una ubicación de setellite. Puede agregar más licencias con el tiempo a medida que agrega los usuarios en ubicaciones de satélite.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p103">Note that the _Multi-Geo Capabilities in Office 365_ plan is a user-level service plan. You need a license for each user that you want to host in a setellite location. You can add more licenses over time as you add users in satellite locations.</span></span>

<span data-ttu-id="1bf22-113">Una vez que el arrendatario se haya aprovisionado con el plan de _Capacidades de Multi-Geo en Office 365_ , la ficha **ubicaciones Geo** estará disponible en el [Centro de administración de OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="1bf22-113">Once your tenant has been provisioned with the  _Multi-Geo Capabilities in Office 365_ plan, the **Geo locations** tab will become available in the [OneDrive admin center](https://admin.onedrive.com).</span></span>

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a><span data-ttu-id="1bf22-114">Establecer las ubicaciones de datos permitido (ADL) a los inquilinos</span><span class="sxs-lookup"><span data-stu-id="1bf22-114">Set the Allowed Data Locations (ADL) to your tenant</span></span>

<span data-ttu-id="1bf22-p104">Debe establecer una ubicación de datos permitidos para SharePoint para cada ubicación geográfica donde desea utilizar OneDrive para el negocio. Geo-ubicaciones disponibles se muestran en la tabla siguiente:</span><span class="sxs-lookup"><span data-stu-id="1bf22-p104">You must set an Allowed Data Location for SharePoint for each geo-location where you want to use OneDrive for Business. Available geo-locations are shown in the following table:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="1bf22-117"><strong>Ubicación</strong></span><span class="sxs-lookup"><span data-stu-id="1bf22-117"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="1bf22-118"><strong>Código</strong></span><span class="sxs-lookup"><span data-stu-id="1bf22-118"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="1bf22-119">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="1bf22-119">North America</span></span></td>
<td align="left"><span data-ttu-id="1bf22-120">NAM</span><span class="sxs-lookup"><span data-stu-id="1bf22-120">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1bf22-121">Europa / Medio Oriente / África</span><span class="sxs-lookup"><span data-stu-id="1bf22-121">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="1bf22-122">EUROS</span><span class="sxs-lookup"><span data-stu-id="1bf22-122">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="1bf22-123">Asia y Pacífico</span><span class="sxs-lookup"><span data-stu-id="1bf22-123">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="1bf22-124">APC</span><span class="sxs-lookup"><span data-stu-id="1bf22-124">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1bf22-125">Australia</span><span class="sxs-lookup"><span data-stu-id="1bf22-125">Australia</span></span></td>
<td align="left"><span data-ttu-id="1bf22-126">AUSTRALIA</span><span class="sxs-lookup"><span data-stu-id="1bf22-126">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="1bf22-127">Japón</span><span class="sxs-lookup"><span data-stu-id="1bf22-127">Japan</span></span></td>
<td align="left"><span data-ttu-id="1bf22-128">JPN</span><span class="sxs-lookup"><span data-stu-id="1bf22-128">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1bf22-129">Canadá</span><span class="sxs-lookup"><span data-stu-id="1bf22-129">Canada</span></span></td>
<td align="left"><span data-ttu-id="1bf22-130">PUEDE</span><span class="sxs-lookup"><span data-stu-id="1bf22-130">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="1bf22-131">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="1bf22-131">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="1bf22-132">GBR</span><span class="sxs-lookup"><span data-stu-id="1bf22-132">GBR</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="1bf22-133">Corea</span><span class="sxs-lookup"><span data-stu-id="1bf22-133">Korea</span></span></td>
<td align="left"><span data-ttu-id="1bf22-134">KOR</span><span class="sxs-lookup"><span data-stu-id="1bf22-134">KOR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="1bf22-135">Para agregar una ubicación de satélite geo</span><span class="sxs-lookup"><span data-stu-id="1bf22-135">To add a satellite geo location</span></span>

1. <span data-ttu-id="1bf22-136">Abrir el [Centro de administración de OneDrive](https://admin.onedrive.com).</span><span class="sxs-lookup"><span data-stu-id="1bf22-136">Open the [OneDrive admin center](https://admin.onedrive.com).</span></span>

2. <span data-ttu-id="1bf22-137">Vaya a la ficha **ubicación geográfica** .</span><span class="sxs-lookup"><span data-stu-id="1bf22-137">Navigate to the **Geo locations** tab.</span></span>

3. <span data-ttu-id="1bf22-138">Haga clic en **Agregar ubicación**.</span><span class="sxs-lookup"><span data-stu-id="1bf22-138">Click **Add location**.</span></span>

4. <span data-ttu-id="1bf22-139">Seleccione la ubicación que desea agregar y, a continuación, haga clic en **siguiente**.</span><span class="sxs-lookup"><span data-stu-id="1bf22-139">Select the location that you want to add, and then click **Next**.</span></span>

5. <span data-ttu-id="1bf22-140">Escriba el dominio que desea utilizar con la ubicación geográfica y, a continuación, haga clic en **Agregar**.</span><span class="sxs-lookup"><span data-stu-id="1bf22-140">Type the domain that you want to use with the geo location, and then click **Add**.</span></span>

6. <span data-ttu-id="1bf22-141">Haga clic en **Cerrar**.</span><span class="sxs-lookup"><span data-stu-id="1bf22-141">Click **Close**.</span></span>

<span data-ttu-id="1bf22-p105">Una vez que haya completado el aprovisionamiento de una ubicación de satélite, recibirá una confirmación por correo electrónico. Cuando la nueva ubicación geográfica aparece en azul en el mapa en la ficha **ubicaciones de Geo** en el centro de administración de OneDrive, puede continuar para establecer la ubicación de datos preferido de los usuarios a esa ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p105">Once provisioning of a satellite location has completed, you will recieve an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo-location.</span></span> 

> [!IMPORTANT]
> <span data-ttu-id="1bf22-p106">La nueva ubicación del satélite geo se configurará con la configuración predeterminada. Esto le permitirá configurar esa ubicación geográfica según sus necesidades de cumplimiento de normas locales.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p106">Your new satellite geo location will be set up with default settings. This will allow you to configure that geo location as appropriate for your local compliance needs.</span></span>

## <a name="setting-users-preferred-data-location"></a><span data-ttu-id="1bf22-146">Configuración de ubicación de datos preferido de los usuarios</span><span class="sxs-lookup"><span data-stu-id="1bf22-146">Setting users’ preferred data location</span></span>
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

<span data-ttu-id="1bf22-p107">Después de habilitar las ubicaciones de los datos necesarios, puede actualizar las cuentas de usuario para utilizar la ubicación de datos adecuado. Se recomienda establecer una ubicación de datos preferido para todos los usuarios, incluso si ese usuario se encuentre en la ubicación predeterminada de los datos.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p107">Once you enable the needed data locations, you can update your user accounts to use the appropriate data location. We recommend that you set a preferred data location for every user, even if that user is staying in the default data location.</span></span>

> [!TIP]
> <span data-ttu-id="1bf22-149">Se recomienda empezar validaciones con un usuario de prueba o un pequeño grupo de usuarios antes de implementar capacidades de Multi-Geo a su organización más amplia.</span><span class="sxs-lookup"><span data-stu-id="1bf22-149">We recommend that you begin validations with a test user or small group of users before rolling out Multi-Geo capabilities to your broader organization.</span></span>

<span data-ttu-id="1bf22-p108">En DAA hay dos tipos de objetos de usuario: sólo los usuarios y sincronizado de la nube. Siga las instrucciones apropiadas para su tipo de usuario.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p108">In AAD there are two types of user objects: cloud only users and synchronized users. Please follow the appropriate instructions for your type of user.</span></span>

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a><span data-ttu-id="1bf22-152">Sincronizar mediante AD conectar la ubicación de datos preferido del usuario</span><span class="sxs-lookup"><span data-stu-id="1bf22-152">Synchronize user’s Preferred Data Location using AD Connect</span></span> 

<span data-ttu-id="1bf22-p109">Si los usuarios de su empresa se sincronizan desde un sistema de Active Directory (AD) local a Azure Active Directory (DAA), debe ser rellenado en AD y sincroniza con DAA su PreferredDataLocation. Siga el proceso de [sync de Azure Connect AD: realizar un cambio en la configuración predeterminada de](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) preferido de Configurar sincronización de ubicación de los datos de locales AD a DAA.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p109">If your company’s users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), their PreferredDataLocation must be populated in AD and synchronized to AAD. Follow the process in [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) to configure Preferred Data Location sync from on-premises AD to AAD.</span></span>

<span data-ttu-id="1bf22-155">Recomendamos que incluya la configuración de ubicación de datos preferido del usuario como parte de su flujo de trabajo de creación de usuario estándar.</span><span class="sxs-lookup"><span data-stu-id="1bf22-155">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bf22-p110">Para los nuevos usuarios con ningún OneDrive aprovisionado, espere al menos 24 horas después PDL de un usuario se sincroniza con DAA para que los cambios se propaguen antes de que el usuario inicia sesión en OneDrive para el negocio. (Establecer los datos preferidos ubicación antes de que el usuario inicia una sesión en suministrar su OneDrive para el negocio asegura que se aprovisionará en la ubicación correcta nueva OneDrive del usuario.)</span><span class="sxs-lookup"><span data-stu-id="1bf22-p110">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is synchronized to AAD for the changes to propagate before the user logs in to OneDrive for Business. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

### <a name="setting-preferred-data-location-for-cloud-only-users"></a><span data-ttu-id="1bf22-158">Configuración de ubicación de datos preferido para la nube sólo los usuarios</span><span class="sxs-lookup"><span data-stu-id="1bf22-158">Setting Preferred Data Location for cloud only users</span></span> 

<span data-ttu-id="1bf22-159">Si los usuarios de la compañía no se sincronizan desde un sistema de Active Directory (AD) local a Azure Active Directory (DAA), lo que significa que se crean en Office 365 o DAA, entonces PDL debe establecerse mediante PowerShell DAA.</span><span class="sxs-lookup"><span data-stu-id="1bf22-159">If your company’s users are not synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), meaning they are created in Office 365 or AAD, then PDL must be set using AAD PowerShell.</span></span>

<span data-ttu-id="1bf22-p111">Los procedimientos de esta sección requieren [Microsoft Azure Active Directory para Windows PowerShell módulo](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si ya dispone de PowerShell DAA instalado, asegúrese de que actualice a la versión más reciente.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p111">The procedures in this section require the [Microsoft Azure Active Directory Module for Windows PowerShell Module](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). If you already have AAD PowerShell installed, please ensure you update to the latest version.</span></span>

1.  <span data-ttu-id="1bf22-162">Abra el módulo de Active Directory de Microsoft Azure para Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1bf22-162">Open the Microsoft Azure Active Directory Module for Windows PowerShell.</span></span>

2.  <span data-ttu-id="1bf22-163">Ejecutar `Connect-MsolService` y especifique las credenciales de administrador global para el arrendatario.</span><span class="sxs-lookup"><span data-stu-id="1bf22-163">Run `Connect-MsolService` and enter the global administrator credentials for your tenant.</span></span>

3.  <span data-ttu-id="1bf22-p112">Utilice el cmdlet [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) para establecer la ubicación de datos preferido para cada uno de los usuarios. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="1bf22-p112">Use the [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:</span></span>

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    <span data-ttu-id="1bf22-p113">Puede comprobar para confirmar que la ubicación de datos preferido se ha actualizado correctamente con el cmdlet Get-MsolUser. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="1bf22-p113">You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:</span></span>

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

<span data-ttu-id="1bf22-168">Recomendamos que incluya la configuración de ubicación de datos preferido del usuario como parte de su flujo de trabajo de creación de usuario estándar.</span><span class="sxs-lookup"><span data-stu-id="1bf22-168">We recommend that you include setting the user’s Preferred Data Location as a part of your standard user creation workflow.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1bf22-p114">Para los nuevos usuarios con ningún OneDrive aprovisionado, espere al menos 24 horas después de PDL de un usuario se establece para que los cambios se propaguen antes de que el usuario inicie sesión SharePoint OneDrive. (Establecer los datos preferidos ubicación antes de que el usuario inicia una sesión en suministrar su OneDrive para el negocio asegura que se aprovisionará en la ubicación correcta nueva OneDrive del usuario.)</span><span class="sxs-lookup"><span data-stu-id="1bf22-p114">For new users with no OneDrive provisioned, wait at least 24 hours after a user's PDL is set for the changes to propagate before the user logs in to SharePoint OneDrive. (Setting the preferred data location before the user logs in to provision their OneDrive for Business ensures that the user’s new OneDrive will be provisioned in the correct location.)</span></span>

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a><span data-ttu-id="1bf22-171">Aprovisionamiento de OneDrive y el efecto de PDL</span><span class="sxs-lookup"><span data-stu-id="1bf22-171">OneDrive Provisioning and the effect of PDL</span></span>

<span data-ttu-id="1bf22-p115">Si el usuario ya tiene un sitio de OneDrive creado en el inquilino, estableciendo su PDL no se moverá automáticamente su OneDrive existente. Para mover OneDrive un usuario, consulte [OneDrive de negocios Geo mover](move-onedrive-between-geo-locations.md) siga las instrucciones en OneDrive mover entre ubicaciones geo.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p115">If the user already has a OneDrive site created in the tenant, setting their PDL will not automatically move their existing OneDrive. To move a user’s OneDrive, see [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) please follow the instructions in Moving OneDrive between geo locations.</span></span>

<span data-ttu-id="1bf22-174">Si el usuario no tiene un sitio de OneDrive con el inquilino, OneDrive se aprovisionará para ellos de acuerdo con su valor PDL, suponiendo que el PDL del usuario coincide con uno de los almacenes de datos permitidos de la empresa (ADL).</span><span class="sxs-lookup"><span data-stu-id="1bf22-174">If the user does not have a OneDrive site within the tenant, OneDrive will be provisioned for them in accordance to their PDL value, assuming the PDL for the user matches one of the company’s allowed data locations (ADLs).</span></span>

## <a name="configuring-multi-geo-search"></a><span data-ttu-id="1bf22-175">Configurar la búsqueda Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="1bf22-175">Configuring Multi-Geo search</span></span>

<span data-ttu-id="1bf22-176">El arrendatario Multi-Geo tendrán una capacidad de búsqueda agregado permitiendo una consulta de búsqueda para devolver los resultados desde cualquier lugar con el inquilino.</span><span class="sxs-lookup"><span data-stu-id="1bf22-176">Your Multi-Geo tenant will have aggregate search capabilities allowing a search query to return results from anywhere within the tenant.</span></span>

<span data-ttu-id="1bf22-177">De forma predeterminada, las búsquedas de estos puntos de entrada devolverá resultados agregados, aunque cada índice de búsqueda se encuentra en su ubicación geográfica correspondiente:</span><span class="sxs-lookup"><span data-stu-id="1bf22-177">By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant geo location:</span></span>

- <span data-ttu-id="1bf22-178">OneDrive para el negocio</span><span class="sxs-lookup"><span data-stu-id="1bf22-178">OneDrive for business</span></span>

- <span data-ttu-id="1bf22-179">Delve</span><span class="sxs-lookup"><span data-stu-id="1bf22-179">Delve</span></span>

- <span data-ttu-id="1bf22-180">Inicio de SharePoint</span><span class="sxs-lookup"><span data-stu-id="1bf22-180">SharePoint Home</span></span>

- <span data-ttu-id="1bf22-181">Centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="1bf22-181">Search Center</span></span>

<span data-ttu-id="1bf22-182">Además, las capacidades de búsqueda Multi-Geo pueden configurarse para sus aplicaciones de búsqueda personalizada que utilice la API de búsqueda de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="1bf22-182">Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.</span></span>

<span data-ttu-id="1bf22-183">Consulte [Configurar búsqueda de OneDrive de negocios Multi-Geo](configure-search-for-multi-geo.md) para instrucciones incluidas las limitaciones y diferencias.</span><span class="sxs-lookup"><span data-stu-id="1bf22-183">Please review [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for instructions including any limitations and differences.</span></span>

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a><span data-ttu-id="1bf22-184">Validar la OneDrive para la configuración de negocios Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="1bf22-184">Validating the OneDrive for Business Multi-Geo configuration</span></span>

<span data-ttu-id="1bf22-p116">A continuación se presentan algunos casos de uso básico que desea incluir en el plan de validación antes de ampliamente implementar OneDrive para negocios Multi-Geo a su compañía. Una vez que haya completado estas pruebas y los casos de uso adicionales que son relevantes para su empresa, puede pasar a agregar los usuarios en el grupo piloto inicial.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p116">Below are some basic use cases you may wish to include in your validation plan before broadly rolling out OneDrive for Business Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.</span></span>

<span data-ttu-id="1bf22-187">**OneDrive para el negocio**</span><span class="sxs-lookup"><span data-stu-id="1bf22-187">**OneDrive for Business**</span></span>

<span data-ttu-id="1bf22-p117">Seleccione OneDrive desde el selector de la aplicación de Office 365 y confirme que se dirige automáticamente a la ubicación geográfica correspondiente para el usuario, basándose en PDL del usuario. OneDrive para el negocio debe empezar ahora provisioning en esa ubicación. Pruebe una vez aprovisionado, carga y descarga de algunos documentos.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p117">Select OneDrive from the Office 365 app launcher and confirm that you are automatically directed to the appropriate geo-location for the user, based on the user’s PDL. OneDrive for Business should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.</span></span>

<span data-ttu-id="1bf22-191">**Aplicación OneDrive Mobile**</span><span class="sxs-lookup"><span data-stu-id="1bf22-191">**OneDrive Mobile App**</span></span>

<span data-ttu-id="1bf22-p118">Inicie sesión en su aplicación móvil OneDrive con sus credenciales de la cuenta de prueba. Confirme que puede ver la OneDrive de archivos de empresas y puede interactuar con ellos desde tu dispositivo móvil.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p118">Log into your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive for business files and can interact with them from your mobile device.</span></span>

<span data-ttu-id="1bf22-194">**Cliente de sincronización OneDrive**</span><span class="sxs-lookup"><span data-stu-id="1bf22-194">**OneDrive sync client**</span></span>

<span data-ttu-id="1bf22-p119">Confirme que el cliente de sincronización OneDrive detecta automáticamente su OneDrive para la ubicación geográfica de negocio al iniciar sesión. Si necesita descargar al cliente de sincronización, puede hacer clic en **sincronizar** en la biblioteca OneDrive.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p119">Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo-location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.</span></span>

<span data-ttu-id="1bf22-197">**Aplicaciones de Office**</span><span class="sxs-lookup"><span data-stu-id="1bf22-197">**Office applications**</span></span>

<span data-ttu-id="1bf22-p120">Confirme que puede tener acceso a OneDrive para el negocio al iniciar sesión desde una aplicación de Office, como Word. Abra la aplicación y seleccione "OneDrive: <TenantName>". Office detectará su ubicación OneDrive y mostrar los archivos que se pueden abrir.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p120">Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.</span></span>

<span data-ttu-id="1bf22-201">**Sharing**</span><span class="sxs-lookup"><span data-stu-id="1bf22-201">**Sharing**</span></span>

<span data-ttu-id="1bf22-p121">Intenta compartir archivos de OneDrive. Confirme que el selector de personas muestra todos los usuarios en línea de SharePoint independientemente de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="1bf22-p121">Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo-location.</span></span>
