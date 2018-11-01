---
title: Planear OneDrive para la Empresa con capacidades multigeográficas
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información sobre OneDrive para la Empresa con capacidades multigeográficas, cómo funcionan las Capacidades multigeográficas y qué ubicaciones geográficas están disponibles para el almacenamiento de datos.
ms.openlocfilehash: d40f84ea3636b4eca2711a48bd9d70c73a242cfd
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849866"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="5e4db-103">Planear OneDrive para la Empresa con capacidades multigeográficas</span><span class="sxs-lookup"><span data-stu-id="5e4db-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="5e4db-104">Esta guía está diseñada para administradores de compañías multinacionales (MNC) que estén preparando el espacio empresarial de SharePoint Online para expandirlo a otras geografías según la presencia de la compañía para cumplir con los requisitos de residencia de datos.</span><span class="sxs-lookup"><span data-stu-id="5e4db-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="5e4db-p101">En una configuración de OneDrive con capacidades multigeográficas, el espacio empresarial de Office 365 está compuesto por una ubicación central y una o más ubicaciones geográficas satelitales. Es un único espacio empresarial que abarca varias ubicaciones geográficas. En OneDrive con capacidades multigeográficas, la información del espacio empresarial, incluidas las ubicaciones geográficas, se dominan en Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="5e4db-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="5e4db-108">Aquí encontrará algunos términos clave de Capacidades multigeográficas para ayudarle a comprender los conceptos básicos de la configuración:</span><span class="sxs-lookup"><span data-stu-id="5e4db-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="5e4db-109">**Espacio empresarial:** la representación de una organización en la nube de Office 365, que suele tener uno o más dominios asociados (por ejemplo, http://contoso.sharepoint.com)).</span><span class="sxs-lookup"><span data-stu-id="5e4db-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="5e4db-110">**Ubicación geográfica**: las ubicaciones geográficas disponibles para hospedar datos en un espacio empresarial de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5e4db-110">**Geo locations** – The geographic locations available to host data in an Office 365 tenant.</span></span>

-   <span data-ttu-id="5e4db-p102">**Ubicaciones satélite**: las ubicaciones geográficas que ha configurado para que hospeden los datos de su espacio empresarial de Office 365. Los espacios empresariales de capacidades multigeográficas abarcan más de una ubicación geográfica (por ejemplo, Norteamérica y Europa).</span><span class="sxs-lookup"><span data-stu-id="5e4db-p102">**Satellite locations** – The geo locations that you have configured to host data in your Office 365 tenant. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="5e4db-p103">**Ubicación de datos preferida (PDL):** la ubicación geográfica donde se almacenan los datos de OneDrive de un usuario individual. Esta opción puede configurarla el administrador para cualquiera de las ubicaciones de datos permitidas configuradas para el espacio empresarial. Tenga en cuenta que, si cambia la PDL de un usuario que ya tenga un sitio de OneDrive, sus datos de OneDrive no se moverán automáticamente a la nueva ubicación geográfica. Para obtener más información, vea [Mover una biblioteca de OneDrive a otra ubicación geográfica](move-onedrive-between-geo-locations.md).</span><span class="sxs-lookup"><span data-stu-id="5e4db-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="5e4db-117">Para habilitar Capacidades multigeográficas es necesario completar cuatro pasos principales:</span><span class="sxs-lookup"><span data-stu-id="5e4db-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="5e4db-118">Trabaje con el equipo de cuentas para agregar el plan de servicio _Capacidades multigeográficas en Office 365_.</span><span class="sxs-lookup"><span data-stu-id="5e4db-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="5e4db-119">Seleccione las ubicaciones satélite deseadas y agréguelas al espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="5e4db-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="5e4db-p104">Establezca la ubicación de datos preferida de los usuarios en la ubicación satélite que quiera usar. Cuando se aprovisione un sitio de OneDrive para un usuario, se realizará en su PDL.</span><span class="sxs-lookup"><span data-stu-id="5e4db-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="5e4db-122">Migre los sitios de OneDrive existentes de los usuarios desde la ubicación central a la ubicación de datos preferida, según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="5e4db-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="5e4db-123">Para obtener más información sobre estos pasos, vea [Configurar OneDrive para la Empresa con capacidades multigeográficas](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5e4db-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5e4db-p105">Tenga en cuenta que Office 365 multigeográfico no ha sido diseñado para casos de optimización de rendimiento, sino para cumplir con requisitos de residencia de datos. Para obtener información sobre la optimización de rendimiento para Office 365, vea [Planeamiento de la red y optimización del rendimiento para Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848), o bien póngase en contacto con su grupo de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="5e4db-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="5e4db-p106">Puede configurar cualquiera de las ubicaciones siguientes para que sean ubicaciones satelitales donde podrá hospedar archivos de OneDrive. Al planear la implementación de Capacidades multigeográficas, realice una lista de las ubicaciones que quiera agregar a su espacio empresarial de Office 365. Le recomendamos que empiece con una o dos ubicaciones satelitales y que, después, se expanda de forma progresiva a más ubicaciones geográficas, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="5e4db-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5e4db-129"><strong>Ubicación</strong></span><span class="sxs-lookup"><span data-stu-id="5e4db-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="5e4db-130"><strong>Código</strong></span><span class="sxs-lookup"><span data-stu-id="5e4db-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="5e4db-131">Asia-Pacífico</span><span class="sxs-lookup"><span data-stu-id="5e4db-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="5e4db-132">APC</span><span class="sxs-lookup"><span data-stu-id="5e4db-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5e4db-133">Australia</span><span class="sxs-lookup"><span data-stu-id="5e4db-133">Australia</span></span></td>
<td align="left"><span data-ttu-id="5e4db-134">AUS</span><span class="sxs-lookup"><span data-stu-id="5e4db-134">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5e4db-135">Canadá</span><span class="sxs-lookup"><span data-stu-id="5e4db-135">Canada</span></span></td>
<td align="left"><span data-ttu-id="5e4db-136">CAN</span><span class="sxs-lookup"><span data-stu-id="5e4db-136">CAN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5e4db-137">Europa, Oriente medio y África</span><span class="sxs-lookup"><span data-stu-id="5e4db-137">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="5e4db-138">EUR</span><span class="sxs-lookup"><span data-stu-id="5e4db-138">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5e4db-139">Francia</span><span class="sxs-lookup"><span data-stu-id="5e4db-139">France</span></span></td>
<td align="left"><span data-ttu-id="5e4db-140">FRA</span><span class="sxs-lookup"><span data-stu-id="5e4db-140">FRA</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5e4db-141">Japón</span><span class="sxs-lookup"><span data-stu-id="5e4db-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="5e4db-142">JPN</span><span class="sxs-lookup"><span data-stu-id="5e4db-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5e4db-143">Corea</span><span class="sxs-lookup"><span data-stu-id="5e4db-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="5e4db-144">KOR</span><span class="sxs-lookup"><span data-stu-id="5e4db-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5e4db-145">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="5e4db-145">North America</span></span></td>
<td align="left"><span data-ttu-id="5e4db-146">NAM</span><span class="sxs-lookup"><span data-stu-id="5e4db-146">NAM</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5e4db-147">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="5e4db-147">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="5e4db-148">GBR</span><span class="sxs-lookup"><span data-stu-id="5e4db-148">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="5e4db-149">Próximas ubicaciones geográficas:</span><span class="sxs-lookup"><span data-stu-id="5e4db-149">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="5e4db-150">India</span><span class="sxs-lookup"><span data-stu-id="5e4db-150">India</span></span>

<span data-ttu-id="5e4db-p107">Al configurar Capacidades multigeográficas, podrá consolidar su infraestructura local al migrar a Office 365. Por ejemplo, si tiene granjas de servidores locales en Singapur y Malasia, puede consolidarlas en la ubicación satelital de APC, siempre que los requisitos de residencia de datos le permitan hacerlo.</span><span class="sxs-lookup"><span data-stu-id="5e4db-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="5e4db-153">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="5e4db-153">Best practices</span></span>

<span data-ttu-id="5e4db-p108">Le recomendamos que cree un usuario de prueba en Office 365 para realizar pruebas iniciales. Le indicaremos algunos pasos de verificación y pruebas con este usuario antes de continuar con la incorporación de los usuarios de producción a OneDrive multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="5e4db-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="5e4db-p109">Después de completar las pruebas con el usuario de prueba, seleccione un grupo piloto (por ejemplo, del departamento de TI) para que sea el primero en usar OneDrive en una nueva ubicación geográfica. Para este primer grupo, seleccione usuarios que aún no tengan una cuenta de OneDrive. Le recomendamos que no agregue más de cinco usuarios a este grupo inicial y que se expanda de forma progresiva siguiendo un método de implementación por lotes.</span><span class="sxs-lookup"><span data-stu-id="5e4db-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="5e4db-p110">Cada usuario necesita tener una *ubicación de datos preferida* (PDL) para que Office 365 pueda determinar en qué ubicación geográfica necesita aprovisionar la cuenta de OneDrive. La ubicación de datos preferida del usuario tiene que coincidir con una de las ubicaciones satelitales o con la ubicación central. Aunque el campo de PDL no es obligatorio, le recomendamos que establezca una PDL para todos los usuarios. Las cargas de trabajo de un usuario sin una PDL se aprovisionarán en la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="5e4db-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="5e4db-p111">Cree una lista de los usuarios e incluya su nombre principal de usuario (UPN) y el código de ubicación para la ubicación de datos preferida. Incluya el usuario de prueba y el grupo piloto inicial para empezar. Necesitará esta lista en los procedimientos de configuración.</span><span class="sxs-lookup"><span data-stu-id="5e4db-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="5e4db-p112">Si los usuarios se sincronizan desde un sistema local de Active Directory a Azure Active Directory, tendrá que establecer la ubicación de datos preferida para los usuarios sincronizados con Azure Active Directory Connect. No puede configurar directamente la ubicación de datos preferida para los usuarios sincronizados con Azure AD PowerShell. Los pasos para configurar PDL en AD y sincronizarlos se describen en [Sincronización de Azure Active Directory Connect: Configurar la ubicación de datos preferida para los recursos de Office 365](https://docs.microsoft.com/es-ES/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="5e4db-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/es-ES/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="5e4db-p113">La administración de un inquilino multigeográfico puede ser distinta de un espacio empresarial que no sea multigeográfico, ya que muchas de las opciones de configuración y servicios de SharePoint y OneDrive detectan las Capacidades multigeográficas. Le recomendamos que vea [Administrar un entorno multigeográfico](administering-a-multi-geo-environment.md) antes de continuar con la configuración.</span><span class="sxs-lookup"><span data-stu-id="5e4db-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="5e4db-171">Para obtener más información sobre la experiencia de los usuarios finales en un entorno multigeográfico, vea [Experiencia del usuario en un entorno multigeográfico](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="5e4db-171">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="5e4db-172">Para empezar a configurar OneDrive para la Empresa con capacidades multigeográficas, vea [Configurar OneDrive para la Empresa con capacidades multigeográficas](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="5e4db-172">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="5e4db-173">Cuando complete la configuración, recuerde [migrar las bibliotecas de OneDrive de los usuarios](move-onedrive-between-geo-locations.md) según sea necesario para que los usuarios puedan trabajar desde sus ubicaciones de datos preferidas.</span><span class="sxs-lookup"><span data-stu-id="5e4db-173">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
