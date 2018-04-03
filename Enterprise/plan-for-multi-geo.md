---
title: Plan de OneDrive para el negocio Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Conozca OneDrive para Multi-Geo del negocio, cómo funciona multi-geo y qué ubicaciones de geo están disponibles para el almacenamiento de datos.
ms.openlocfilehash: 22ba0f4ebc3fb3c4e11bc0386a1479fa6a889ad8
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="f2c95-103">Plan de OneDrive para el negocio Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="f2c95-103">Plan for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="f2c95-104">Esta guía está diseñada para administradores de empresas multinacionales (MNCs) que se están preparando su inquilino de SharePoint Online para expandirse a zonas geográficas adicionales con arreglo a la presencia de la empresa para satisfacer los requisitos de residencia de los datos.</span><span class="sxs-lookup"><span data-stu-id="f2c95-104">This guidance is designed for administrators of multi-national companies (MNCs) who are preparing their SharePoint Online tenant to be expanded to additional geographies in accordance with the company’s presence to meet data residency requirements.</span></span>

<span data-ttu-id="f2c95-p101">En una configuración OneDrive Multi-Geo, el arrendatario Office 365 consiste en una ubicación central (también conocida como la ubicación predeterminada) y una o más ubicaciones de geo de satélite. Se trata de un solo usuario que abarca varias ubicaciones geo. En OneDrive Multi-Geo, su información de inquilinos, incluyendo geo ubicaciones, es usado en Azure Active Directory (DAA).</span><span class="sxs-lookup"><span data-stu-id="f2c95-p101">In a OneDrive Multi-Geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. This is a single tenant that spans across multiple geo locations. In OneDrive Multi-Geo, your tenant information, including geo locations, is mastered in Azure Active Directory (AAD).</span></span> 

<span data-ttu-id="f2c95-108">Éstos son algunos de los términos clave multi-geo para ayudarle a comprender los conceptos básicos de la configuración:</span><span class="sxs-lookup"><span data-stu-id="f2c95-108">Here are some key multi-geo terms to help you understand the basic concepts of the configuration:</span></span>

-   <span data-ttu-id="f2c95-109">**Inquilinos** : representación de una organización en la nube de Office 365, que normalmente tiene uno o más dominios asociados (por ejemplo, http://contoso.sharepoint.com).</span><span class="sxs-lookup"><span data-stu-id="f2c95-109">**Tenant** – An organization’s representation in the Office 365 cloud which typically has one or more domains associated with it (for example, http://contoso.sharepoint.com).</span></span> 

-   <span data-ttu-id="f2c95-p102">**Geo ubicaciones** , las ubicaciones geográficas donde se hospedan los datos de su arrendatario. Multi-geo arrendatarios abarcan más de una ubicación geográfica, por ejemplo, Norteamérica y Europa.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p102">**Geo locations** – The geographic locations where your tenant’s data is hosted. Multi-geo tenants span more than one geo location, for example, North America and Europe.</span></span>

-   <span data-ttu-id="f2c95-112">**Ubicaciones de datos permitido (ADL)** : las ubicaciones de geo para el cual el arrendatario se ha configurado para alojar los datos de OneDrive y SharePoint.</span><span class="sxs-lookup"><span data-stu-id="f2c95-112">**Allowed Data Locations (ADL)** – The geo locations for which your tenant has been configured to host OneDrive and SharePoint data.</span></span>

-   <span data-ttu-id="f2c95-p103">**Ubicación de datos preferidos (PDL)** : la ubicación geográfica donde se almacenan datos de OneDrive de un usuario individual. Esta propiedad puede establecerse por el administrador a cualquiera de las ubicaciones de datos permitidos que se han configurado para el arrendatario. Tenga en cuenta que si cambia el PDL para un usuario que ya tiene un sitio de OneDrive, sus datos OneDrive no se mueven a la nueva ubicación geográfica automáticamente. Para obtener más información, vea [mover una biblioteca de OneDrive a una ubicación geográfica diferente](move-onedrive-between-geo-locations.md) .</span><span class="sxs-lookup"><span data-stu-id="f2c95-p103">**Preferred Data Location (PDL)** – The geo location where an individual user’s OneDrive data is stored. This can be set by the administrator to any of the Allowed Data Locations that have been configured for the tenant. Note that if you change the PDL for a user who already has a OneDrive site, their OneDrive data is not moved to the new geo location automatically. See [Move a OneDrive library to a different geo-location](move-onedrive-between-geo-locations.md) for more information.</span></span>

<span data-ttu-id="f2c95-117">Habilitar Multi-Geo requiere cuatro pasos clave:</span><span class="sxs-lookup"><span data-stu-id="f2c95-117">Enabling Multi-Geo requires four key steps:</span></span>

1.  <span data-ttu-id="f2c95-118">Trabaje con su equipo de cuenta para agregar el plan de servicio _Multi-Geo capacidades de Office 365_ .</span><span class="sxs-lookup"><span data-stu-id="f2c95-118">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span>

2.  <span data-ttu-id="f2c95-119">Elija su deseado geo ubicaciones de satélite y agregarlos a los inquilinos.</span><span class="sxs-lookup"><span data-stu-id="f2c95-119">Choose your desired satellite geo location(s) and add them to your tenant.</span></span>

3.  <span data-ttu-id="f2c95-p104">Establecer ubicación de datos preferido de los usuarios a la ubicación de geo satélite deseado. Cuando se aprovisiona un sitio nuevo de OneDrive para un usuario, se aprovisiona a su PDL.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p104">Set your users’ preferred data location to the desired satellite geo location. When a new OneDrive site is provisioned for a user, it is provisioned to their PDL.</span></span>

4.  <span data-ttu-id="f2c95-122">Migrar los sitios existentes de OneDrive de los usuarios desde el domicilio a su ubicación de datos preferido según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="f2c95-122">Migrate your users’ existing OneDrive sites from the home location to their preferred data location as needed.</span></span>

<span data-ttu-id="f2c95-123">Para obtener información detallada sobre cada uno de estos pasos, consulte [Configurar OneDrive para negocios Multi-Geo](multi-geo-tenant-configuration.md) .</span><span class="sxs-lookup"><span data-stu-id="f2c95-123">See [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md) for details on each of these steps.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f2c95-p105">Tenga en cuenta que las características de Multi-Geo de Office 365 no están diseñadas para los casos de optimización de rendimiento, están diseñados para satisfacer los requisitos de residencia de los datos. Para obtener información acerca de la optimización de rendimiento para Office 365, consulte [planificación de la red y ajuste del rendimiento para Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o póngase en contacto con su grupo de soporte.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p105">Note that the Multi-Geo features of Office 365 are not designed for performance optimization cases, they are designed to meet data residency requirements. For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

<span data-ttu-id="f2c95-p106">Puede configurar cualquiera de las siguientes ubicaciones para ser satélite geo ubicaciones donde puede alojar archivos de OneDrive. Mientras planea para multi-geo, haga una lista de las ubicaciones que desea agregar a su inquilino de Office 365. Recomendamos a partir de una o dos ubicaciones de satélite y expandiendo gradualmente en más ubicaciones geo, si es necesario.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p106">You can configure any of the following locations to be satellite geo locations where you can host OneDrive files. As you plan for multi-geo, make a list of the locations that you want to add to your Office 365 tenant. We recommend starting with one or two satellite locations and then gradually expanding to more geo locations, if needed.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f2c95-129"><strong>Ubicación</strong></span><span class="sxs-lookup"><span data-stu-id="f2c95-129"><strong>Location</strong></span></span></th>
<th align="left"><span data-ttu-id="f2c95-130"><strong>Código</strong></span><span class="sxs-lookup"><span data-stu-id="f2c95-130"><strong>Code</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f2c95-131">Asia y Pacífico</span><span class="sxs-lookup"><span data-stu-id="f2c95-131">Asia-Pacific</span></span></td>
<td align="left"><span data-ttu-id="f2c95-132">APC</span><span class="sxs-lookup"><span data-stu-id="f2c95-132">APC</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f2c95-133">Europa / Medio Oriente / África</span><span class="sxs-lookup"><span data-stu-id="f2c95-133">Europe / Middle East / Africa</span></span></td>
<td align="left"><span data-ttu-id="f2c95-134">EUROS</span><span class="sxs-lookup"><span data-stu-id="f2c95-134">EUR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f2c95-135">Norteamérica</span><span class="sxs-lookup"><span data-stu-id="f2c95-135">North America</span></span></td>
<td align="left"><span data-ttu-id="f2c95-136">NAM</span><span class="sxs-lookup"><span data-stu-id="f2c95-136">NAM</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f2c95-137">Australia</span><span class="sxs-lookup"><span data-stu-id="f2c95-137">Australia</span></span></td>
<td align="left"><span data-ttu-id="f2c95-138">AUSTRALIA</span><span class="sxs-lookup"><span data-stu-id="f2c95-138">AUS</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f2c95-139">Canadá</span><span class="sxs-lookup"><span data-stu-id="f2c95-139">Canada</span></span></td>
<td align="left"><span data-ttu-id="f2c95-140">PUEDE</span><span class="sxs-lookup"><span data-stu-id="f2c95-140">CAN</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f2c95-141">Japón</span><span class="sxs-lookup"><span data-stu-id="f2c95-141">Japan</span></span></td>
<td align="left"><span data-ttu-id="f2c95-142">JPN</span><span class="sxs-lookup"><span data-stu-id="f2c95-142">JPN</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f2c95-143">Corea</span><span class="sxs-lookup"><span data-stu-id="f2c95-143">Korea</span></span></td>
<td align="left"><span data-ttu-id="f2c95-144">KOR</span><span class="sxs-lookup"><span data-stu-id="f2c95-144">KOR</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f2c95-145">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="f2c95-145">United Kingdom</span></span></td>
<td align="left"><span data-ttu-id="f2c95-146">GBR</span><span class="sxs-lookup"><span data-stu-id="f2c95-146">GBR</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f2c95-147">Ubicaciones próximas geo:</span><span class="sxs-lookup"><span data-stu-id="f2c95-147">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="f2c95-148">Francia</span><span class="sxs-lookup"><span data-stu-id="f2c95-148">France</span></span>
- <span data-ttu-id="f2c95-149">India</span><span class="sxs-lookup"><span data-stu-id="f2c95-149">India</span></span>

<span data-ttu-id="f2c95-p107">Al configurar multi-geo, considere la posibilidad de tomar esta oportunidad para consolidar su infraestructura local mientras la migración a Office 365. Por ejemplo, si tiene conjuntos de servidores locales en Singapur y Malasia, a continuación, puede consolidarlos a la ubicación de satélite APC, siempre que los requisitos de residencia de datos le permiten hacerlo.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p107">When you configure multi-geo, consider taking the opportunity to consolidate your on-premises infrastructure while migrating to Office 365. For example, if you have on-premises farms in Singapore and Malaysia, then you can consolidate them to the APC satellite location, provided data residency requirements allow you to do so.</span></span>

## <a name="best-practices"></a><span data-ttu-id="f2c95-152">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="f2c95-152">Best practices</span></span>

<span data-ttu-id="f2c95-p108">Recomendamos que cree un usuario de prueba Office 365 realizar algunas pruebas iniciales. Le mostraremos algunos pasos de pruebas y comprobación con este usuario antes de continuar con los usuarios de producción integrada en la función OneDrive Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p108">We recommend that you create a test user in Office 365 to do some initial testing. We’ll walk through some testing and verification steps with this user before you proceed to onboard production users into the OneDrive Multi-Geo feature.</span></span>

<span data-ttu-id="f2c95-p109">Una vez que haya realizado la comprobación con el usuario de prueba, seleccione un grupo piloto: quizás en su departamento de TI: ser el primero en utilizar OneDrive en una nueva ubicación geográfica. Para este primer grupo, seleccione los usuarios que no tienen aún un OneDrive. Se recomiendan no más de cinco personas en este grupo inicial y expanda gradualmente siguiendo un enfoque de implementación por lotes.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p109">Once you’ve completed testing with the test user, select a pilot group – perhaps from your IT department – to be the first to use OneDrive in a new geo-location. For this first group, select users who do not yet have a OneDrive. We recommend no more than five people in this initial group and gradually expand following a batched rollout approach.</span></span>

<span data-ttu-id="f2c95-p110">Cada usuario debe tener una *ubicación de datos preferidos* (PDL) para que Office 365 puede determinar en qué ubicación geográfica aprovisionar su OneDrive. Ubicación de datos preferido del usuario debe coincidir con una de las ubicaciones de satélite elegido o su ubicación central. Aunque el campo PDL no es obligatorio, se recomienda que se establezca una PDL para todos los usuarios. Cargas de trabajo de un usuario sin una PDL se suministrará en la ubicación central basada en la lógica de Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p110">Each user should have a *preferred data location* (PDL) set so that Office 365 can determine in which geo location to provision their OneDrive. The user’s preferred data location must match one of your chosen satellite locations or your central location. While the PDL field is not mandatory, we recommend that a PDL be set for all users. Workloads of a user without a PDL will be provisioned in the central location based on the Multi-Geo logic.</span></span>   

<span data-ttu-id="f2c95-p111">Crear una lista de los usuarios e incluyen su nombre principal de usuario (UPN) y el código de almacén para la ubicación apropiada de datos preferido. Incluir para empezar con su usuario de prueba y el grupo piloto inicial. Necesitará esta lista para los procedimientos de configuración.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p111">Create a list of your users, and include their user principal name (UPN) and the location code for the appropriate preferred data location. Include your test user and your initial pilot group to start with. You’ll need this list for the configuration procedures.</span></span>

<span data-ttu-id="f2c95-p112">Si los usuarios se sincronizan desde un sistema de Active Directory (AD) local a Azure Active Directory (DAA), debe establecer la ubicación de datos preferido de usuarios sincronizados mediante el uso de directorio activo de Azure Connect. No se puede configurar directamente la ubicación de datos preferido de usuarios sincronizados mediante AD PowerShell de Azure. Se tratan los pasos para configurar PDL en AD y sincronizarla en [sincronización de directorio activo Azure Connect: configurar ubicación de datos preferido de recursos de Office 365](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span><span class="sxs-lookup"><span data-stu-id="f2c95-p112">If your users are synchronized from an on-premises Active Directory (AD) system to Azure Active Directory (AAD), you must set the preferred data location for synchronized users by using Azure Active Directory Connect. You cannot directly configure the preferred data location for synchronized users using Azure AD PowerShell. The steps to set up PDL in AD and Synchronize it are covered in [Azure Active Directory Connect sync: Configure preferred data location for Office 365 resources](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).</span></span>

<span data-ttu-id="f2c95-p113">La administración de un arrendatario multi-geo puede diferir del inquilino-multi-geo, como muchas de las opciones de SharePoint y OneDrive y servicios son multi-geo. Recomendamos que revise [la administración de un entorno multi-geo](administering-a-multi-geo-environment.md) antes de continuar con la configuración.</span><span class="sxs-lookup"><span data-stu-id="f2c95-p113">The administration of a multi-geo tenant can differ from a non-multi-geo tenant, as many of the SharePoint and OneDrive settings and services are multi-geo aware. We recommend that you review [Administering a multi-geo environment](administering-a-multi-geo-environment.md) before you proceed with your configuration.</span></span>

<span data-ttu-id="f2c95-170">Lea la [experiencia de usuario en un entorno de multgeo](multi-geo-user-experience.md) para obtener más información acerca de la experiencia de los usuarios finales en un entorno multi-geo.</span><span class="sxs-lookup"><span data-stu-id="f2c95-170">Read [User experience in a multgeo environment](multi-geo-user-experience.md) for details about your end users' experience in a multi-geo environment.</span></span>

<span data-ttu-id="f2c95-171">Para empezar a configurar OneDrive para negocios Multi-Geo, vea [Configurar OneDrive para negocios Multi-Geo](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="f2c95-171">To get started configuring OneDrive for Business Multi-Geo, see [Configure OneDrive for Business Multi-Geo](multi-geo-tenant-configuration.md).</span></span>

<span data-ttu-id="f2c95-172">Una vez que haya completado la configuración, no olvide [migrar bibliotecas de OneDrive de los usuarios](move-onedrive-between-geo-locations.md) según sea necesario para permitir que los usuarios que trabajan desde sus ubicaciones de datos preferido.</span><span class="sxs-lookup"><span data-stu-id="f2c95-172">Once you’ve completed the configuration, remember to [migrate your users' OneDrive libraries](move-onedrive-between-geo-locations.md) as needed to get your users working from their preferred data locations.</span></span>
