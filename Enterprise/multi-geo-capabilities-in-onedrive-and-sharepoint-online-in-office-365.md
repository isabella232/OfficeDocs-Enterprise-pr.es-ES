---
title: Capacidades de Multi-Geo en OneDrive y SharePoint Online en Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/16/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expandir su presencia en Office 365 para varias regiones geográficas con capacidades de multi-geo en OneDrive y SharePoint Online.
ms.openlocfilehash: 3f72158fe05aadfe8a08a5520bf65cd2d0aaa1c6
ms.sourcegitcommit: a81d08c7e8771cb2c232435971e3169d4f7428dc
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="253fe-103">Capacidades de Multi-Geo en OneDrive y SharePoint Online en Office 365</span><span class="sxs-lookup"><span data-stu-id="253fe-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="253fe-p101">Con multi-geo las capacidades de OneDrive y SharePoint Online, su organización puede expandir su presencia en Office 365 a múltiples regiones geográficas o países en su arrendatario existente. Llegar a su equipo de cuentas de Microsoft suscribirse a su empresa multinacional OneDrive de negocios Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="253fe-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="253fe-106">Con OneDrive Multi-Geo, puede aprovisionar y almacenar los datos en reposo en las ubicaciones geo que ha elegido para satisfacer los requisitos de residencia de los datos y al mismo tiempo desbloquear su implementación global de experiencias de productividad moderna a los empleados.</span><span class="sxs-lookup"><span data-stu-id="253fe-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="253fe-107">Le mostramos cómo características multi-geo pueden beneficiar a su organización:</span><span class="sxs-lookup"><span data-stu-id="253fe-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="253fe-108">Funcionar como una organización conectada global con un único inquilino de Office 365 que abarcan varias ubicaciones geo.</span><span class="sxs-lookup"><span data-stu-id="253fe-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="253fe-109">Cumplir los requisitos de residencia de datos mediante la creación y alojamiento de datos en reposo dentro de una ubicación geográfica especificada.</span><span class="sxs-lookup"><span data-stu-id="253fe-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="253fe-110">Equipe a sus usuarios de satélite con las mismas experiencias de productividad moderna disfrutadas los usuarios de una ubicación central.</span><span class="sxs-lookup"><span data-stu-id="253fe-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="253fe-111">Permitir a los usuarios mover entre geo ubicaciones como sus cambios de funciones, mientras que el acceso a su contenido se mantiene intacto.</span><span class="sxs-lookup"><span data-stu-id="253fe-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="253fe-112">Adaptar las directivas de uso compartidas por ubicación geográfica y las políticas de prevención de pérdida de datos por cada sitio.</span><span class="sxs-lookup"><span data-stu-id="253fe-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="253fe-113">Designar administradores por ubicación geográfica de eDiscovery y permitir que regulan casos adaptados a su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="253fe-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="253fe-114">Elegir espacios de nombres únicos de dirección URL (por ejemplo, ContosoEUR.sharepoint.com) para las ubicaciones geo adicionales.</span><span class="sxs-lookup"><span data-stu-id="253fe-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="253fe-115">Consolidar los datos de instalaciones regionales a los inquilinos de multi-geo Office 365.</span><span class="sxs-lookup"><span data-stu-id="253fe-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="253fe-p102">En una configuración multi-geo, el arrendatario Office 365 consiste en una ubicación central (también conocida como la ubicación predeterminada) y una o más ubicaciones de geo de satélite. El concepto clave de multi-geo es que un único contrato de arrendamiento abarcar uno varias ubicaciones geo. En un arrendatario multi-geo, la información acerca de la información de usuario, grupos y ubicaciones geo se domina en Azure Active Directory (DAA). Porque la información del arrendatario es domina centralmente y sincronizado en cada ubicación geográfica, compartir y experiencias que implican cualquier persona de la compañía contienen conocimiento global.</span><span class="sxs-lookup"><span data-stu-id="253fe-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as the default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="253fe-120">Ejemplo de configuración de inquilinos multi-geo</span><span class="sxs-lookup"><span data-stu-id="253fe-120">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="253fe-121">Utilizando un arrendatario multi-geo, Contoso, con una ubicación central de América del Norte, puede expandir a satélite geo ubicaciones en Europa y Australia bajo el paraguas de organización único de Contoso.com. Los usuarios con su ubicación preferida de datos establecido en Europa tendrán su OneDrive en Europa mientras que los usuarios con su ubicación de datos preferido en América del Norte tendrá su OneDrive en los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="253fe-121">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Mapa del mundo, mostrando geo ubicaciones de Contoso y otras ubicaciones disponibles geo](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="253fe-123">Obtener características de multi-geo en tres sencillos pasos</span><span class="sxs-lookup"><span data-stu-id="253fe-123">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="253fe-124">Es fácil configurar multi-geo:</span><span class="sxs-lookup"><span data-stu-id="253fe-124">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="253fe-p103">Trabaje con su equipo de cuenta para agregar el plan de servicio _Multi-Geo capacidades de Office 365_ . Servirán de guía para agregar el número de licencias necesarias.</span><span class="sxs-lookup"><span data-stu-id="253fe-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="253fe-127">Agregar las ubicaciones de satélite.</span><span class="sxs-lookup"><span data-stu-id="253fe-127">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="253fe-128">Configurar las cuentas de usuario para la ubicación adecuada.</span><span class="sxs-lookup"><span data-stu-id="253fe-128">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="253fe-129">Disponibilidad y estado de Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="253fe-129">Multi-Geo status and availability</span></span>

<span data-ttu-id="253fe-130">OneDrive Multi-Geo se ofrece actualmente en estos países y regiones:</span><span class="sxs-lookup"><span data-stu-id="253fe-130">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="253fe-131">Asia y Pacífico</span><span class="sxs-lookup"><span data-stu-id="253fe-131">Asia-Pacific</span></span>
    
- <span data-ttu-id="253fe-132">Australia</span><span class="sxs-lookup"><span data-stu-id="253fe-132">Australia</span></span>
    
- <span data-ttu-id="253fe-133">Canadá</span><span class="sxs-lookup"><span data-stu-id="253fe-133">Canada</span></span>
    
- <span data-ttu-id="253fe-134">Unión Europea (EMEA)</span><span class="sxs-lookup"><span data-stu-id="253fe-134">European Union (EMEA)</span></span>
    
- <span data-ttu-id="253fe-135">Japón</span><span class="sxs-lookup"><span data-stu-id="253fe-135">Japan</span></span>
    
- <span data-ttu-id="253fe-136">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="253fe-136">United Kingdom</span></span>
    
- <span data-ttu-id="253fe-137">Estados Unidos (Norteamérica)</span><span class="sxs-lookup"><span data-stu-id="253fe-137">United States (North America)</span></span>
    
- <span data-ttu-id="253fe-138">Corea</span><span class="sxs-lookup"><span data-stu-id="253fe-138">Korea</span></span>
      
<span data-ttu-id="253fe-139">Ubicaciones próximas geo:</span><span class="sxs-lookup"><span data-stu-id="253fe-139">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="253fe-140">Francia</span><span class="sxs-lookup"><span data-stu-id="253fe-140">France</span></span>
- <span data-ttu-id="253fe-141">India</span><span class="sxs-lookup"><span data-stu-id="253fe-141">India</span></span>
    
## <a name="getting-started"></a><span data-ttu-id="253fe-142">Introducción</span><span class="sxs-lookup"><span data-stu-id="253fe-142">Getting started</span></span>

<span data-ttu-id="253fe-p104">Para comenzar con la OneDrive de negocios Multi-Geo, el primer paso es planificar [la OneDrive para el entorno de negocios Multi-Geo](plan-for-multi-geo.md). Siguiente, [Obtenga información acerca de cómo administrar un entorno multi-geo](administering-a-multi-geo-environment.md) y [cómo los usuarios experimentarán un entorno multi-geo](multi-geo-user-experience.md). Cuando esté listo para configurar OneDrive para negocios Multi-Geo, [Configurar el arrendatario para multi-geo](multi-geo-tenant-configuration.md), a continuación, [mover los sitios OneDrive a sus nuevas ubicaciones de geo](move-onedrive-between-geo-locations.md) y [Configurar la búsqueda](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="253fe-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
