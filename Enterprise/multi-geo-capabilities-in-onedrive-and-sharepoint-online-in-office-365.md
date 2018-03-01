---
title: Capacidades de Multi-Geo en OneDrive y SharePoint Online en Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 1/24/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: "Con multi-geo las capacidades de OneDrive y SharePoint Online, su organización puede expandir su presencia en Office 365 a múltiples regiones geográficas o países en su arrendatario existente."
ms.openlocfilehash: d53da13d5a6a6d5add9da69a3bca9fcdfa39bbd0
ms.sourcegitcommit: 38d43444cf5e03527aa75f670efb2de0f48f847d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/28/2018
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365"></a><span data-ttu-id="5bd78-103">Capacidades de Multi-Geo en OneDrive y SharePoint Online en Office 365</span><span class="sxs-lookup"><span data-stu-id="5bd78-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="5bd78-p101">Con multi-geo las capacidades de OneDrive y SharePoint Online, su organización puede expandir su presencia en Office 365 a múltiples regiones geográficas o países en su arrendatario existente. Esta característica está actualmente en la vista previa. Llegar a su equipo de cuentas de Microsoft para suscribirse a su empresa multinacional para la previsualización de OneDrive Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="5bd78-p101">With multi-geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. This feature is currently in preview. Reach out to your Microsoft Account Team to sign up your Multi-National Company for the OneDrive Multi-Geo preview.</span></span>
  
<span data-ttu-id="5bd78-107">Con OneDrive Multi-Geo, puede aprovisionar y almacenar los datos en reposo en las ubicaciones de geo que ha elegido para satisfacer los requisitos de residencia de los datos y al mismo tiempo desbloquear su implementación global de experiencias de productividad moderna a los empleados.</span><span class="sxs-lookup"><span data-stu-id="5bd78-107">With OneDrive Multi-Geo, you can provision and store data-at-rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="5bd78-108">Le mostramos cómo características multi-geo pueden beneficiar a su organización:</span><span class="sxs-lookup"><span data-stu-id="5bd78-108">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="5bd78-109">Funcionar como una organización conectada global con un único inquilino de Office 365 que abarcan varias ubicaciones geo.</span><span class="sxs-lookup"><span data-stu-id="5bd78-109">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="5bd78-110">Cumplir los requisitos de residencia de datos mediante la creación y alojamiento de datos en reposo dentro de una ubicación geográfica especificada.</span><span class="sxs-lookup"><span data-stu-id="5bd78-110">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="5bd78-111">Equipe a sus usuarios de satélite con las mismas experiencias de productividad moderna disfrutadas los usuarios de una ubicación central.</span><span class="sxs-lookup"><span data-stu-id="5bd78-111">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="5bd78-112">Permitir a los usuarios mover entre geo ubicaciones como sus cambios de funciones, mientras que el acceso a su contenido se mantiene intacto.</span><span class="sxs-lookup"><span data-stu-id="5bd78-112">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="5bd78-113">Adaptar las directivas de uso compartidas por ubicación geográfica y las políticas de prevención de pérdida de datos por cada sitio.</span><span class="sxs-lookup"><span data-stu-id="5bd78-113">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="5bd78-114">Designar administradores por ubicación geográfica de eDiscovery y permitir que regulan casos adaptados a su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="5bd78-114">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="5bd78-115">Elegir espacios de nombres únicos de dirección URL (por ejemplo, ContosoEUR.sharepoint.com) para las ubicaciones geo adicionales.</span><span class="sxs-lookup"><span data-stu-id="5bd78-115">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="5bd78-116">Consolidar los datos de instalaciones regionales a los inquilinos de multi-geo Office 365.</span><span class="sxs-lookup"><span data-stu-id="5bd78-116">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="5bd78-117">Para obtener más información y para ver una demostración, vea [Introducción a Multi-Geo capacidades en Office 365 y cómo configurarlos](https://youtu.be/3d9-Vt2fArk) y el[póster de introducción de Multi-Geo](https://technet.microsoft.com/library/dn782272.aspx).</span><span class="sxs-lookup"><span data-stu-id="5bd78-117">For more information, and to see a demonstration, see [Introducing Multi-Geo capabilities in Office 365 and how to configure them](https://youtu.be/3d9-Vt2fArk) and the[Multi-Geo overview poster](https://technet.microsoft.com/library/dn782272.aspx).</span></span>
  
<span data-ttu-id="5bd78-p102">En una configuración multi-geo, el arrendatario Office 365 consiste en una ubicación central (también conocido como una ubicación predeterminada) y una o más ubicaciones de geo de satélite. El concepto clave de multi-geo es que un único contrato de arrendamiento abarcar uno varias ubicaciones geo. En un arrendatario multi-geo, la información acerca de la información de usuario, grupos y ubicaciones geo se domina en Azure Active Directory (DAA). Porque la información del arrendatario es domina centralmente y sincronizado en cada ubicación geográfica, compartir y experiencias que implican cualquier persona de la compañía contienen conocimiento global.</span><span class="sxs-lookup"><span data-stu-id="5bd78-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (also known as a default location) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>
  
## <a name="sample-multi-geo-tenant-configuration"></a><span data-ttu-id="5bd78-122">Ejemplo de configuración de inquilinos multi-geo</span><span class="sxs-lookup"><span data-stu-id="5bd78-122">Sample multi-geo tenant configuration</span></span>

<span data-ttu-id="5bd78-123">Utilizando un arrendatario multi-geo, Contoso, con una ubicación central de América del Norte, puede expandir a satélite geo ubicaciones en Europa y Australia bajo el paraguas de organización único de Contoso.com. Los usuarios con su ubicación preferida de datos establecido en Europa tendrán su OneDrive en Europa mientras que los usuarios con su ubicación de datos preferido en América del Norte tendrá su OneDrive en los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="5bd78-123">By using a multi-geo tenant, Contoso, with a central location of North America, can expand to satellite geo locations in Europe, and Australia under the single organization umbrella of Contoso.com. Users with their preferred data location set to Europe will have their OneDrive in Europe while users with their preferred data location in North America will have their OneDrive in the US.</span></span>
  
![Mapa del mundo, mostrando geo ubicaciones de Contoso y otras ubicaciones disponibles geo](images/df317ccc-2e53-411d-9211-a5aee63ca1e5.png)
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="5bd78-125">Obtener características de multi-geo en tres sencillos pasos</span><span class="sxs-lookup"><span data-stu-id="5bd78-125">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="5bd78-126">Es fácil configurar multi-geo:</span><span class="sxs-lookup"><span data-stu-id="5bd78-126">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="5bd78-127">Habilitar al arrendatario Office 365 para multi-geo.</span><span class="sxs-lookup"><span data-stu-id="5bd78-127">Enable your Office 365 tenant for multi-geo.</span></span>
    
2. <span data-ttu-id="5bd78-128">Agregar las ubicaciones de satélite.</span><span class="sxs-lookup"><span data-stu-id="5bd78-128">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="5bd78-129">Configurar las cuentas de usuario para la ubicación adecuada.</span><span class="sxs-lookup"><span data-stu-id="5bd78-129">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="5bd78-130">Disponibilidad y estado de Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="5bd78-130">Multi-Geo status and availability</span></span>

<span data-ttu-id="5bd78-131">OneDrive Multi-Geo se ofrece actualmente en estos países y regiones:</span><span class="sxs-lookup"><span data-stu-id="5bd78-131">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="5bd78-132">Asia y Pacífico</span><span class="sxs-lookup"><span data-stu-id="5bd78-132">Asia-Pacific</span></span>
    
- <span data-ttu-id="5bd78-133">Australia</span><span class="sxs-lookup"><span data-stu-id="5bd78-133">Australia</span></span>
    
- <span data-ttu-id="5bd78-134">Canadá</span><span class="sxs-lookup"><span data-stu-id="5bd78-134">Canada</span></span>
    
- <span data-ttu-id="5bd78-135">Unión Europea (EMEA)</span><span class="sxs-lookup"><span data-stu-id="5bd78-135">European Union (EMEA)</span></span>
    
- <span data-ttu-id="5bd78-136">India</span><span class="sxs-lookup"><span data-stu-id="5bd78-136">India</span></span>
    
- <span data-ttu-id="5bd78-137">Japón</span><span class="sxs-lookup"><span data-stu-id="5bd78-137">Japan</span></span>
    
- <span data-ttu-id="5bd78-138">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="5bd78-138">United Kingdom</span></span>
    
- <span data-ttu-id="5bd78-139">Estados Unidos (Norteamérica)</span><span class="sxs-lookup"><span data-stu-id="5bd78-139">United States (North America)</span></span>
    
- <span data-ttu-id="5bd78-140">Corea del sur</span><span class="sxs-lookup"><span data-stu-id="5bd78-140">South Korea</span></span>
    
> [!NOTE]
> <span data-ttu-id="5bd78-141">India y Corea del sur actualmente sólo están disponibles para clientes con licencias y direcciones de facturación en esas ubicaciones geo.</span><span class="sxs-lookup"><span data-stu-id="5bd78-141">India and South Korea are currently only available for customers with licenses and billing addresses in those geo locations.</span></span> 
  
<span data-ttu-id="5bd78-142">Ubicaciones próximas geo:</span><span class="sxs-lookup"><span data-stu-id="5bd78-142">Upcoming geo locations:</span></span>
  
- <span data-ttu-id="5bd78-143">Francia</span><span class="sxs-lookup"><span data-stu-id="5bd78-143">France</span></span>
    
<span data-ttu-id="5bd78-144">Servicios disponibles:</span><span class="sxs-lookup"><span data-stu-id="5bd78-144">Available services:</span></span>
  
- <span data-ttu-id="5bd78-145">Exchange Online: en la vista previa</span><span class="sxs-lookup"><span data-stu-id="5bd78-145">Exchange Online - in preview</span></span>
    
- <span data-ttu-id="5bd78-146">OneDrive para empresas, en vista preliminar</span><span class="sxs-lookup"><span data-stu-id="5bd78-146">OneDrive for Business - in preview</span></span>
    
- <span data-ttu-id="5bd78-147">SharePoint Online - en desarrollo</span><span class="sxs-lookup"><span data-stu-id="5bd78-147">SharePoint Online - in development</span></span>
    

