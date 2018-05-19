---
title: Administración de un entorno de multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información cómo administrar los servicios de SharePoint y OneDrive en un entorno multigeográfico.
ms.openlocfilehash: 596db0e2cffedc74a4840ae4427a3350ba1e27d8
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="52c9c-103">Administración de un entorno de multigeográfico</span><span class="sxs-lookup"><span data-stu-id="52c9c-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="52c9c-104">Vea cómo funcionan los servicios de OneDrive y SharePoint en un entorno de multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="52c9c-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="52c9c-105">Experiencia del administrador de OneDrive</span><span class="sxs-lookup"><span data-stu-id="52c9c-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="52c9c-p101">El [Centro de administración de OneDrive](https://admin.onedrive.com) tiene una pestaña **Geo locations** (Ubicaciones geográficas) en la navegación izquierda que cuenta con un mapa de ubicaciones geográficas en el que puede ver y administrar sus ubicaciones geográficas. Utilice esta página para agregar o eliminar ubicaciones geográficas en el espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="52c9c-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="52c9c-108">Taxonomía</span><span class="sxs-lookup"><span data-stu-id="52c9c-108">Taxonomy</span></span>

<span data-ttu-id="52c9c-p102">Se admite una [taxonomía](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificada para metadatos administrados empresariales en todas las ubicaciones geográficas, con el patrón hospedado en la ubicación central de la compañía. Se recomienda administrar la taxonomía global desde la ubicación central y agregar solo términos específicos de la ubicación a la taxonomía de la ubicación geográfica por satélite. Los términos de la taxonomía global se sincronizarán con las ubicaciones geográficas por satélite.</span><span class="sxs-lookup"><span data-stu-id="52c9c-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="52c9c-112">Uso compartido</span><span class="sxs-lookup"><span data-stu-id="52c9c-112">Sharing</span></span>

<span data-ttu-id="52c9c-p103">Los administradores pueden establecer y administrar directivas de uso compartido en cada una de sus ubicaciones. Los sitios de OneDrive de cada ubicación geográfica solo cumplirán la configuración de uso específica de la correspondiente geoárea. (Por ejemplo, puede permitir [uso compartido externo](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) en la ubicación central, pero no en la ubicación por satélite y viceversa). Tenga en cuenta que la configuración de uso compartido no permite configurar limitaciones de uso compartido entre ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="52c9c-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. (For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa.) Note that the sharing settings do not allow configuring sharing limitations between geo-locations.</span></span>

<span data-ttu-id="52c9c-p104">En OneDrive multigeográfico, ha de administrar la configuración de uso compartido en cada ubicación geográfica, ya que no se sincroniza en todo el espacio empresarial. Para administrar el uso compartido, visite la página [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) (Configuración de uso compartido en el Centro de administración de OneDrive). El uso compartido externo con cualquier persona de cada ubicación por satélite está habilitado de forma predeterminada.</span><span class="sxs-lookup"><span data-stu-id="52c9c-p104">For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant. To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="52c9c-119">Aplicación de perfil de usuario</span><span class="sxs-lookup"><span data-stu-id="52c9c-119">User Profile Application</span></span>

<span data-ttu-id="52c9c-p105">Existe una [aplicación de perfil de usuario](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) en cada ubicación geográfica. La información de perfil de cada usuario se hospeda en su ubicación geográfica y está disponible para el administrador de esa ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="52c9c-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="52c9c-p106">Si tiene propiedades de perfil personalizadas, se recomienda usar el mismo esquema de perfil en todo el mundo y rellenar las propiedades de perfil personalizadas en todas las ubicaciones geográficas o donde sea necesario. Para obtener instrucciones sobre cómo rellenar los datos de perfil de usuario mediante programación, consulte el artículo sobre la [API de actualización masiva de los perfiles de usuario](https://docs.microsoft.com/es-ES/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span><span class="sxs-lookup"><span data-stu-id="52c9c-p106">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed. For guidance regarding how to populate user profile data programmatically, please refer to the [Bulk User Profile Update API](https://docs.microsoft.com/es-ES/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="52c9c-124">BCS, Secure Store, Apps</span><span class="sxs-lookup"><span data-stu-id="52c9c-124">BCS: Secure Store Service</span></span>

<span data-ttu-id="52c9c-125">Los servicios BCS, Secure Store y Apps tienen todos instancias geográficas independientes, por lo que el Administrador de SharePoint Online debe administrarlos y configurarlos en cada instancia geográfica en la que quieren que estén presentes.</span><span class="sxs-lookup"><span data-stu-id="52c9c-125">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="52c9c-126">Centro de seguridad y cumplimiento</span><span class="sxs-lookup"><span data-stu-id="52c9c-126">Security and Compliance Admin Center</span></span>

<span data-ttu-id="52c9c-127">Existe un centro de cumplimiento centralizado para el inquilino multigeográfico: [Centro de seguridad y cumplimiento de Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="52c9c-127">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="52c9c-128">Directiva de prevención de pérdida de datos (DLP) e Information Protection (IP)</span><span class="sxs-lookup"><span data-stu-id="52c9c-128">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="52c9c-p107">Puede establecer directivas DLP IP para OneDrive para la Empresa en el centro de seguridad y cumplimiento, además de aplicar ámbito a las directivas según sea necesario para todo el espacio empresarial o a los usuarios que corresponda. Por ejemplo: si desea seleccionar una directiva para un usuario de OneDrive en una ubicación por satélite, seleccione esta opción para aplicar la directiva en un determinado OneDrive y escriba la dirección url de OneDrive del usuario. Vea [Información general sobre las directivas de prevención de pérdida de datos](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) para obtener instrucciones generales para crear directivas DLP.</span><span class="sxs-lookup"><span data-stu-id="52c9c-p107">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="52c9c-132">Las directivas DLP se sincronizan automáticamente en función de su aplicabilidad a cada ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="52c9c-132">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="52c9c-133">La implementación de directivas de prevención de pérdida de datos e Information Protection a todos los usuarios de una ubicación geográfica no es una opción disponible en la interfaz de usuario, en lugar de ello, debe seleccionar las cuentas de OneDrive a las que quiere aplicar la directiva o aplicar la directiva globalmente a todas las cuentas de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="52c9c-133">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="52c9c-134">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="52c9c-134">eDiscovery</span></span> 

<span data-ttu-id="52c9c-p108">De forma predeterminada, un administrador o un supervisor de eDiscovery de un inquilino multigeográfico solo podrán ejecutar eDiscovery en la ubicación central de ese espacio empresarial. Para que se pueda ejecutar eDiscovery en ubicaciones por satélite, hay un nuevo parámetro de filtro de seguridad de cumplimiento llamado "Región" disponible mediante PowerShell.</span><span class="sxs-lookup"><span data-stu-id="52c9c-p108">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="52c9c-137">El administrador global de Office 365 debe asignar permisos de supervisor de eDiscovery para que otros usuarios puedan ejecutar eDiscovery y asignar un parámetro "Región" en el filtro de seguridad de cumplimiento correspondiente para especificar la región donde se ejecutará eDiscovery como ubicación por satélite; en caso contrario, no se ejecutará eDiscovery en la ubicación por satélite.</span><span class="sxs-lookup"><span data-stu-id="52c9c-137">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="52c9c-p109">Cuando se establece el rol Administrador o Supervisor de eDiscovery para una ubicación geográfica concreta, el administrador o supervisor de eDiscovery solo podrán realizar acciones de búsqueda de eDiscovery en sitios de SharePoint y OneDrive situados en esa ubicación geográfica. Si un administrador o supervisor de eDiscovery intenta realizar búsquedas en sitios de SharePoint o OneDrive fuera de la región especificada, no se devolverá ningún resultado. Además, cuando el administrador o supervisor de eDiscovery de una región desencadena una exportación, los datos se exportan a la instancia de Azure de esa región. Esto ayuda a las organizaciones a mantener el cumplimiento al no permitir que el contenido se exporte a través de fronteras controladas.</span><span class="sxs-lookup"><span data-stu-id="52c9c-p109">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="52c9c-142">Si es necesario que un supervisor de eDiscovery realice búsquedas en varias regiones de SharePoint, habrá que crear otra cuenta para el supervisor de eDiscovery que especifique la región alternativa en donde se encuentran los sitios de OneDrive o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="52c9c-142">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="52c9c-143"><strong>Ubicaciones geográficas compatibles con capacidades multigeográficas</strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-143"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="52c9c-144"><strong>Los datos exportados de eDiscovery para SharePoint estarán en esta ubicación de datos de Azure Blob…</strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-144"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="52c9c-145"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-145"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="52c9c-146">Centros de datos de EE. UU.</span><span class="sxs-lookup"><span data-stu-id="52c9c-146">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52c9c-147"><strong>EUR</strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-147"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="52c9c-148">Centros de datos de Europa</span><span class="sxs-lookup"><span data-stu-id="52c9c-148">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="52c9c-149"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-149"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="52c9c-150">Centros de datos de Asia oriental o Asia Suroriental</span><span class="sxs-lookup"><span data-stu-id="52c9c-150">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52c9c-151"><strong>CAN</strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-151"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="52c9c-152">Centros de datos de EE. UU.</span><span class="sxs-lookup"><span data-stu-id="52c9c-152">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="52c9c-153"><strong>AUS</strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-153"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="52c9c-154">Centros de datos de Asia oriental o Asia Suroriental</span><span class="sxs-lookup"><span data-stu-id="52c9c-154">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52c9c-155"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-155"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="52c9c-156">Ubicación de datos predeterminada del espacio empresarial</span><span class="sxs-lookup"><span data-stu-id="52c9c-156">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="52c9c-157"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-157"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="52c9c-158">Centros de datos de Europa</span><span class="sxs-lookup"><span data-stu-id="52c9c-158">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="52c9c-159"><strong>JPN </strong></span><span class="sxs-lookup"><span data-stu-id="52c9c-159"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="52c9c-160">Centros de datos de Asia oriental o Asia Suroriental</span><span class="sxs-lookup"><span data-stu-id="52c9c-160">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="52c9c-161">Para establecer el filtro de seguridad de cumplimiento para una región:</span><span class="sxs-lookup"><span data-stu-id="52c9c-161">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="52c9c-162">Abra Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="52c9c-162">Open Windows PowerShell.</span></span>

2.  <span data-ttu-id="52c9c-163">Escriba</span><span class="sxs-lookup"><span data-stu-id="52c9c-163">Enter</span></span>  
    <span data-ttu-id="52c9c-164">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="52c9c-164">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="52c9c-165">$a = Import-PSSession $s -AllowClobber</span><span class="sxs-lookup"><span data-stu-id="52c9c-165">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="52c9c-166">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="52c9c-166">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="52c9c-167">Por ejemplo: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="52c9c-167">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="52c9c-168">Vea el articulo [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) para obtener más parámetros y sintaxis</span><span class="sxs-lookup"><span data-stu-id="52c9c-168">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="52c9c-169">Búsqueda de registros de auditoría</span><span class="sxs-lookup"><span data-stu-id="52c9c-169">Audit log search</span></span>

<span data-ttu-id="52c9c-p110">Hay un [registro de auditoría](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unificado de todas las ubicaciones geográficas disponible en la página de búsqueda de registros de auditoría de Office 365. Puede ver todas las entradas de registro de auditoría en todas las geoáreas, por ejemplo, las actividades de los usuarios de las geoáreas NAM y EUR se mostrarán en una vista de la organización y luego puede aplicar los filtros existentes para ver actividades específicas del usuario.</span><span class="sxs-lookup"><span data-stu-id="52c9c-p110">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
