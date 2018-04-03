---
title: Administrar un entorno multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtenga información acerca de cómo administrar servicios de SharePoint y OneDrive en un entorno multi-geo.
ms.openlocfilehash: f49cf35503ee6495b5982dc7d72f9b1936f564c6
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="administering-a-multi-geo-environment"></a><span data-ttu-id="fbe7b-103">Administrar un entorno multi-geo</span><span class="sxs-lookup"><span data-stu-id="fbe7b-103">Administering a multi-geo environment</span></span>

<span data-ttu-id="fbe7b-104">Aquí es un vistazo a cómo funcionan los servicios de OneDrive y SharePoint en un entorno multi-geo.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-104">Here's a look at how OneDrive and SharePoint services work in a multi-geo environment.</span></span>

#### <a name="onedrive-administrator-experience"></a><span data-ttu-id="fbe7b-105">Experiencia de administrador de OneDrive</span><span class="sxs-lookup"><span data-stu-id="fbe7b-105">OneDrive Administrator Experience</span></span>

<span data-ttu-id="fbe7b-p101">El [Centro de administración de OneDrive](https://admin.onedrive.com) tiene una ficha **ubicaciones Geo** en la izquierda las características que se asignan un geo-ubicaciones donde puede ver y administrar las ubicaciones geo. Utilice esta página para agregar o eliminar ubicaciones de geo para el arrendatario.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-p101">The [OneDrive admin center](https://admin.onedrive.com) has a **Geo locations** tab in the left navigation which features a geo-locations map where you can view and manage your geo locations. Use this page to add or delete geo locations for your tenant.</span></span>

#### <a name="taxonomy"></a><span data-ttu-id="fbe7b-108">Taxonomía</span><span class="sxs-lookup"><span data-stu-id="fbe7b-108">Taxonomy</span></span>

<span data-ttu-id="fbe7b-p102">Apoyamos [taxonomía](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificada para metadatos empresariales administrados entre ubicaciones geo, con el maestro alojado en la ubicación central para su empresa. Se recomienda que administre su taxonomía global desde la ubicación central y sólo agregar términos específicos de la ubicación a la taxonomía de la ubicación geográfica de satélite. Términos de taxonomía global se sincronizarán con las ubicaciones de satélite geo.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-p102">We support a unified [taxonomy](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) for enterprise managed metadata across geo locations, with the master being hosted in the central location for your company. We recommend that you manage your global taxonomy from the central location and only add location-specific terms to the satellite geo location’s Taxonomy. Global taxonomy terms will synchronize to the satellite geo locations.</span></span>

#### <a name="sharing"></a><span data-ttu-id="fbe7b-112">Uso compartido</span><span class="sxs-lookup"><span data-stu-id="fbe7b-112">Sharing</span></span>

<span data-ttu-id="fbe7b-p103">Los administradores pueden establecer y administrar las directivas de uso compartidas para cada una de sus ubicaciones. Los sitios de OneDrive en cada ubicación geográfica respeta sólo la correspondiente geo para compartir valores específicos. Por ejemplo, puede permitir [Compartir externo](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) para su ubicación central, pero no para el satélite ubicación o viceversa. Para OneDrive Multi-Geo, debe administrar la configuración de uso compartido en cada ubicación geográfica como éstos no se sincronizan entre los inquilinos.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-p103">Administrators can set and manage sharing policies for each of their locations. The OneDrive sites in each geo location will honor only the corresponding geo specific sharing settings. For example, you can allow [external sharing](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) for your central location, but not for your satellite location or vice versa. For OneDrive Multi-Geo, you must manage your sharing settings at each geo location as these are not synchronized across the tenant.</span></span>

<span data-ttu-id="fbe7b-p104">Administrar uso compartido visita la página del [Centro de administración de OneDrive configuración de uso compartido](https://admin.onedrive.com/?v=SharingSettings) . De forma predeterminada compartir externo está habilitado con nadie en cada ubicación de satélite.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-p104">To manage sharing visit the [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) page. By default external sharing is enabled with Anyone in each satellite location.</span></span>

#### <a name="user-profile-application"></a><span data-ttu-id="fbe7b-119">Aplicación de perfil de usuario</span><span class="sxs-lookup"><span data-stu-id="fbe7b-119">User Profile Application</span></span>

<span data-ttu-id="fbe7b-p105">Hay una [aplicación de perfil de usuario](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) en cada ubicación geográfica. Información de perfil de cada usuario se aloja en su ubicación geográfica y están disponibles para el Administrador de esa ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-p105">There is a [user profile application](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) in each geo location. Each user’s profile information is hosted in their geo location and available to the administrator for that geo location.</span></span>

<span data-ttu-id="fbe7b-122">Si dispone de propiedades de perfil personalizado, recomendamos que utilice el mismo esquema de perfil en todo el mundo y llenar las propiedades de perfil personalizado en todas las ubicaciones de geo o donde sea necesario.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-122">If you have custom profile properties, then we recommend that you use the same profile schema across geographies and populate your custom profile properties either in all geo locations or where needed.</span></span>

#### <a name="bcs-secure-store-apps"></a><span data-ttu-id="fbe7b-123">Seguro de BCS, almacén, aplicaciones</span><span class="sxs-lookup"><span data-stu-id="fbe7b-123">BCS, Secure Store, Apps</span></span>

<span data-ttu-id="fbe7b-124">BCS, almacenamiento seguro y aplicaciones tienen instancias geo independiente, por lo tanto, el Administrador de SharePoint Online debe administrar y configurar estos servicios de cada instancia de geo dónde desean estar presentes.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-124">BCS, Secure Store, and Apps all have separate geo instances, therefore the SharePoint Online administrator should manage and configure these services from each geo instance where they want them to be present.</span></span>

#### <a name="security-and-compliance-admin-center"></a><span data-ttu-id="fbe7b-125">Centro de administración de cumplimiento de normas y de seguridad</span><span class="sxs-lookup"><span data-stu-id="fbe7b-125">Security and Compliance Admin Center</span></span>

<span data-ttu-id="fbe7b-126">Hay un centro de cumplimiento central para el arrendatario Multi-Geo: [Centro de cumplimiento de normas y seguridad de Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span><span class="sxs-lookup"><span data-stu-id="fbe7b-126">There is one central compliance center for the Multi-Geo tenant: [Office 365 Security & Compliance Center](https://protection.office.com/?rfr=AdminCenter\#/homepage).</span></span>

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a><span data-ttu-id="fbe7b-127">Información protección (IP) Prevention (DLP) Directiva de DLP</span><span class="sxs-lookup"><span data-stu-id="fbe7b-127">Information Protection (IP) Data Loss Prevention (DLP) Policy</span></span>

<span data-ttu-id="fbe7b-p106">Puede establecer su DLP IP directivas para OneDrive para el negocio en el centro de seguridad y cumplimiento de normas, directivas de ámbito según sea necesario a los inquilinos entero o a usuarios aplicables. Por ejemplo: si desea seleccionar una directiva para un usuario OneDrive en una ubicación de satélite, seleccione esta opción para aplicar la directiva a un OneDrive determinado y especifique el usuario la dirección url OneDrive. Ver [Resumen de las políticas de prevención de pérdida de datos](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) para la dirección general de creación de directivas DLP.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-p106">You can set your IP DLP policies for OneDrive for Business in the Security and Compliance center, scoping policies as needed to the whole tenant or to applicable users. For example: If you wish to select a policy for a OneDrive user in a satellite location, select to apply the policy to a specific OneDrive and enter the user’s OneDrive url. See [Overview of data loss prevention policies](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) for general guidance in creating DLP policies.</span></span>

<span data-ttu-id="fbe7b-131">Las directivas DLP se sincronizan automáticamente en función de su aplicabilidad a cada ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-131">The DLP policies are automatically synchronized based on their applicability to each geo location.</span></span>

<span data-ttu-id="fbe7b-132">La implementación de las políticas de prevención de pérdida de datos y protección de la información a todos los usuarios en una ubicación geográfica no es una opción disponible en la interfaz de usuario, en su lugar debe seleccionar las cuentas de OneDrive aplicables de la directiva o la directiva se aplican globalmente a todas las cuentas de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-132">Implementing Information Protection and Data Loss prevention policies to all users in a geo location is not an option available in the UI, instead you must select the applicable OneDrive accounts for the policy or apply the policy globally to all OneDrive accounts.</span></span>

#### <a name="ediscovery"></a><span data-ttu-id="fbe7b-133">eDiscovery</span><span class="sxs-lookup"><span data-stu-id="fbe7b-133">eDiscovery</span></span> 

<span data-ttu-id="fbe7b-p107">De forma predeterminada, un eDiscovery Manager o administrador de un arrendatario multi-geo podrá conducta eDiscovery sólo en la ubicación central de ese arrendatario. Para admitir la posibilidad de realizar eDiscovery para ubicaciones de satélite, un nuevo parámetro de filtro de seguridad de cumplimiento de normas llamado "Región" está disponible a través de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-p107">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called “Region” is available via PowerShell.</span></span>

<span data-ttu-id="fbe7b-136">El administrador global de Office 365 debe asignar permisos de administrador de eDiscovery para permitir que otros usuarios realizan eDiscovery y asignar un parámetro de "Región" en su filtro de seguridad de cumplimiento de normas aplicables para especificar la región para llevar a cabo eDiscovery como satélite ubicación, en caso contrario que no eDiscovery se realizará para la ubicación de satélite.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-136">The Office 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a “Region” parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="fbe7b-p108">Cuando se establece la función de administrador o administrador de eDiscovery para una ubicación particular geo, el eDiscovery Manager o administrador sólo podrá realizar acciones de búsqueda de eDiscovery en los sitios de SharePoint y sitios OneDrive que se encuentran en esa ubicación geográfica. Si un eDiscovery Manager o administrador intenta buscar en sitios de SharePoint o OneDrive fuera de la región determinada, no se devolverá ningún resultado. Además, cuando el eDiscovery Manager o administrador de una región, desencadena una exportación, los datos se exportan a la instancia de Azure de esa región. Esto ayuda a las organizaciones a cumplir las normas al no permitir que contenido exportarse fuera de las fronteras controladas.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-p108">When the eDiscovery Manager or Administrator role is set for a particular-geo location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that geo-location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified region, no results will be returned. Also, when the eDiscovery Manager or Administrator for a region triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="fbe7b-141">Si es necesario que un administrador para buscar en varias regiones de SharePoint de eDiscovery, otra cuenta de usuario deberá crearse para el eDiscovery Manager que especifica la región alternativa donde se encuentran los sitios de SharePoint o de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-141">If it's necessary for an eDiscovery Manager to search across multiple SharePoint regions, another user account will need to be created for the eDiscovery Manager which specifies the alternate region where the OneDrive or SharePoint sites are located.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="fbe7b-142"><strong>Multi-Geo admite Geo ubicaciones</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-142"><strong>Multi-Geo supported Geo Locations</strong></span></span></th>
<th align="left"><span data-ttu-id="fbe7b-143"><strong>eDiscovery para SharePoint se exportan los datos estarán en esta ubicación de datos Blob de Azure...</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-143"><strong>eDiscovery for SharePoint Exported data will be in this Azure Blob data location…</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="fbe7b-144"><strong>NAM</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-144"><strong>NAM</strong></span></span></td>
<td align="left"><span data-ttu-id="fbe7b-145">Centros de datos de EE.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-145">US Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fbe7b-146"><strong>EUROS</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-146"><strong>EUR</strong></span></span></td>
<td align="left"><span data-ttu-id="fbe7b-147">Centros de datos de Europa</span><span class="sxs-lookup"><span data-stu-id="fbe7b-147">Europe Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fbe7b-148"><strong>APC</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-148"><strong>APC</strong></span></span></td>
<td align="left"><span data-ttu-id="fbe7b-149">Sudeste o centros de datos de Asia oriental</span><span class="sxs-lookup"><span data-stu-id="fbe7b-149">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fbe7b-150"><strong>PUEDE</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-150"><strong>CAN</strong></span></span></td>
<td align="left"><span data-ttu-id="fbe7b-151">Centros de datos de EE.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-151">US Data Centers</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fbe7b-152"><strong>AUSTRALIA</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-152"><strong>AUS</strong></span></span></td>
<td align="left"><span data-ttu-id="fbe7b-153">Sudeste o centros de datos de Asia oriental</span><span class="sxs-lookup"><span data-stu-id="fbe7b-153">South East or East Asia Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fbe7b-154"><strong>KOR</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-154"><strong>KOR</strong></span></span></td>
<td align="left"><span data-ttu-id="fbe7b-155">Ubicación de datos predeterminada del inquilino</span><span class="sxs-lookup"><span data-stu-id="fbe7b-155">Tenant's default data location</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="fbe7b-156"><strong>GBR</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-156"><strong>GBR</strong></span></span></td>
<td align="left"><span data-ttu-id="fbe7b-157">Centros de datos de Europa</span><span class="sxs-lookup"><span data-stu-id="fbe7b-157">Europe Data Centers</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="fbe7b-158"><strong>JPN</strong></span><span class="sxs-lookup"><span data-stu-id="fbe7b-158"><strong>JPN </strong></span></span></td>
<td align="left"><span data-ttu-id="fbe7b-159">Sudeste o centros de datos de Asia oriental</span><span class="sxs-lookup"><span data-stu-id="fbe7b-159">South East or East Asia Data Centers</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="fbe7b-160">Para establecer el filtro de seguridad de cumplimiento para una región:</span><span class="sxs-lookup"><span data-stu-id="fbe7b-160">To set the Compliance Security Filter for a Region:</span></span>

1.  <span data-ttu-id="fbe7b-161">Abrir Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fbe7b-161">Open Windows PowerShell</span></span>

2.  <span data-ttu-id="fbe7b-162">Intro</span><span class="sxs-lookup"><span data-stu-id="fbe7b-162">Enter</span></span>  
    <span data-ttu-id="fbe7b-163">$s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -credenciales $cred-autenticación básica - AllowRedirection - SessionOption (New-PSSessionOption - SkipCACheck - SkipCNCheck - SkipRevocationCheck)</span><span class="sxs-lookup"><span data-stu-id="fbe7b-163">$s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)</span></span>

    <span data-ttu-id="fbe7b-164">$un = $s Import-PSSession - AllowClobber</span><span class="sxs-lookup"><span data-stu-id="fbe7b-164">$a = Import-PSSession $s -AllowClobber</span></span>  

3.  <span data-ttu-id="fbe7b-165">**Nueva ComplianceSecurityFilter** **-Acción** Todos los EnterTheNameYouWantToAssign **NombreFiltro -** **-región** EnterTheRegionParameter **-usuarios** EnterTheUserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="fbe7b-165">**New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName</span></span>

    <span data-ttu-id="fbe7b-166">Por ejemplo: **nuevo ComplianceSecurityFilter-acción** todos los NAMEDISCOVERYMANAGERS **NombreFiltro -** **-región** NAM **-usuarios** adwood@contosodemosx.onmicrosoft.com</span><span class="sxs-lookup"><span data-stu-id="fbe7b-166">For Example: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com</span></span>

<span data-ttu-id="fbe7b-167">Consulte el artículo [ComplianceSecurityFilter de nuevo](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) para la sintaxis y los parámetros adicionales</span><span class="sxs-lookup"><span data-stu-id="fbe7b-167">See the [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) article for additional parameters and syntax</span></span>

#### <a name="audit-log-search"></a><span data-ttu-id="fbe7b-168">Búsqueda de registros de auditoría</span><span class="sxs-lookup"><span data-stu-id="fbe7b-168">Audit log search</span></span>

<span data-ttu-id="fbe7b-p109">Un unificado de [registro de auditoría](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) para todas las ubicaciones de geo está disponible desde la página de búsqueda de registro de auditoría de Office 365. Puede ver todas las entradas de registro de auditoría por zonas, por ejemplo, NOMBR & euros geo actividad de los usuarios se mostrará en una vista de la organización y, a continuación, puede aplicar los filtros existentes para ver las actividades del usuario específico.</span><span class="sxs-lookup"><span data-stu-id="fbe7b-p109">A unified [Audit log](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) for all your geo locations is available from the Office 365 audit log search page. You can see all the audit log entries from across geos, for example, NAM & EUR geo users’ activities will show up in one org view and then you can apply existing filters to see specific user’s activities.</span></span>
