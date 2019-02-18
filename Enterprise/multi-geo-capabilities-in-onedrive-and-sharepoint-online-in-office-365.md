---
title: Capacidades multigeográficas de OneDrive en Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expanda la presencia de Office 365 a varias regiones geográficas con las capacidades multigeográficas de OneDrive Online.
ms.openlocfilehash: f89bfe7cb9a287200591746dc6d22430cd6eed1b
ms.sourcegitcommit: a8aedcfe0d6a6047a622fb3f68278c81c1e413bb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/15/2019
ms.locfileid: "30052994"
---
# <a name="multi-geo-capabilities-in-onedrive-in-office-365"></a><span data-ttu-id="d06f0-103">Capacidades multigeográficas de OneDrive en Office 365</span><span class="sxs-lookup"><span data-stu-id="d06f0-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="d06f0-p101">Con las capacidades multigeográficas de OneDrive Online, su organización puede expandir su presencia en Office 365 a varias regiones geográficas o países dentro de su espacio empresarial existente. Póngase en contacto con su equipo de cuentas de Microsoft para inscribir su empresa multinacional en OneDrive para la Empresa multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="d06f0-p101">With Multi-Geo capabilities in OneDrive and SharePoint Online, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant. Reach out to your Microsoft Account Team to sign up your Multi-National Company for OneDrive for Business Multi-Geo.</span></span>
  
<span data-ttu-id="d06f0-106">Con OneDrive multigeográfico, puede aprovisionar y almacenar los datos en reposo en las ubicaciones geográficas que haya elegido para cumplir los requisitos de residencia de datos y al mismo tiempo permitir la implementación global de experiencias de productividad modernas para sus empleados.</span><span class="sxs-lookup"><span data-stu-id="d06f0-106">With OneDrive Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>
  
<span data-ttu-id="d06f0-107">Esta es la forma en que las características multigeográficas pueden beneficiar a su organización:</span><span class="sxs-lookup"><span data-stu-id="d06f0-107">Here's how multi-geo features can benefit your organization:</span></span>
  
- <span data-ttu-id="d06f0-108">Funcione como una organización conectada global con un único espacio empresarial de Office 365 que abarca varias ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="d06f0-108">Operate as one global connected organization with a single Office 365 tenant spanning multiple geo locations.</span></span>
    
- <span data-ttu-id="d06f0-109">Cumpla los requisitos de residencia de datos al crear y hospeda los datos en reposo en una ubicación geográfica determinada.</span><span class="sxs-lookup"><span data-stu-id="d06f0-109">Meet data residency requirements by creating and hosting data-at-rest within a specified geo location.</span></span>
    
- <span data-ttu-id="d06f0-110">Confiera a los usuarios satélite la misma experiencia moderna de productividad de la que disfrutan los usuarios de la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="d06f0-110">Empower your satellite users with the same modern productivity experiences enjoyed by your central location users.</span></span>
    
- <span data-ttu-id="d06f0-111">Permita que los usuarios se muevan de una ubicación geográfica a otra cuando sus roles cambian, mientras que el acceso a su contenido se mantiene intacto.</span><span class="sxs-lookup"><span data-stu-id="d06f0-111">Enable your users to move across geo locations as their role changes, while access to their content is kept intact.</span></span>
    
- <span data-ttu-id="d06f0-112">Ajuste las directivas de uso compartido por ubicación geográfica y las directivas de prevención de pérdida de datos por sitio.</span><span class="sxs-lookup"><span data-stu-id="d06f0-112">Tailor your sharing policies per geo location and data loss prevention policies per site.</span></span>
    
- <span data-ttu-id="d06f0-113">Designe supervisores de eDiscovery por ubicación geográfica y permita que los casos regulatorios se adapten a su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="d06f0-113">Designate eDiscovery managers per geo location and allow governing cases tailored to your geo location.</span></span>
    
- <span data-ttu-id="d06f0-114">Elija espacios de nombres de dirección URL únicos (por ejemplo, ContosoEUR.sharepoint.com) para las ubicaciones geográficas adicionales.</span><span class="sxs-lookup"><span data-stu-id="d06f0-114">Choose unique URL namespaces (for example, ContosoEUR.sharepoint.com) for your additional geo locations.</span></span>
    
- <span data-ttu-id="d06f0-115">Consolide los datos locales regionales en su inquilino multigeográfico de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d06f0-115">Consolidate your regional on-premises data into your Office 365 multi-geo tenant.</span></span>
    
<span data-ttu-id="d06f0-p102">En una configuración multigeográfica, el espacio empresarial de Office 365 se compone de una ubicación central (en la que su suscripción de Office 365 fue aprovisionada originalmente) y una o varias ubicaciones geográficas por satélite. El concepto clave de la ubicación multigeográfica es que un solo espacio empresarial abarcará de una a varias ubicaciones geográficas. En un espacio empresarial multigeográfico, la información sobre las ubicaciones geográficas, los grupos y los usuarios se controla en Azure Active Directory (AAD). Dado que la información del espacio empresarial se controla centralizadamente y se sincroniza en cada ubicación geográfica, el uso compartido y las experiencias en las que interviene alguien de su compañía contienen conocimiento global.</span><span class="sxs-lookup"><span data-stu-id="d06f0-p102">In a multi-geo configuration, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite geo locations. The key concept of multi-geo is that a single tenancy will span across one multiple geo locations. In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD). Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

## <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="d06f0-120">Vídeo: Presentación de Office 365 multigeográfico</span><span class="sxs-lookup"><span data-stu-id="d06f0-120">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]
  
## <a name="get-multi-geo-features-in-three-simple-steps"></a><span data-ttu-id="d06f0-121">Obtener características multigeográficas en tres simples pasos</span><span class="sxs-lookup"><span data-stu-id="d06f0-121">Get multi-geo features in three simple steps</span></span>

<span data-ttu-id="d06f0-122">La configuración multigeográfica resulta muy sencilla:</span><span class="sxs-lookup"><span data-stu-id="d06f0-122">Configuring multi-geo is easy:</span></span>
  
1. <span data-ttu-id="d06f0-p103">Trabaje con el equipo de cuenta para agregar el plan de servicio _Multi-Geo Capabilities in Office 365_ (Capacidades multigeográficas de Office 365). Le guiará para que agregue el número de licencias necesarias.</span><span class="sxs-lookup"><span data-stu-id="d06f0-p103">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan. They will guide you to add the number of licenses needed.</span></span>
    
2. <span data-ttu-id="d06f0-125">Agregue las ubicaciones por satélite.</span><span class="sxs-lookup"><span data-stu-id="d06f0-125">Add your satellite locations.</span></span>
    
3. <span data-ttu-id="d06f0-126">Configure las cuentas de usuario para la ubicación apropiada.</span><span class="sxs-lookup"><span data-stu-id="d06f0-126">Configure your user accounts for the appropriate location.</span></span>
    
## <a name="multi-geo-status-and-availability"></a><span data-ttu-id="d06f0-127">Estado multigeográfico y disponibilidad</span><span class="sxs-lookup"><span data-stu-id="d06f0-127">Multi-Geo status and availability</span></span>

<span data-ttu-id="d06f0-128">OneDrive multigeográfico se ofrece actualmente en estos países y regiones:</span><span class="sxs-lookup"><span data-stu-id="d06f0-128">OneDrive Multi-Geo is currently offered in these regions and countries:</span></span>
  
- <span data-ttu-id="d06f0-129">Asia-Pacífico</span><span class="sxs-lookup"><span data-stu-id="d06f0-129">Asia-Pacific</span></span>

- <span data-ttu-id="d06f0-130">Australia</span><span class="sxs-lookup"><span data-stu-id="d06f0-130">Australia</span></span>

- <span data-ttu-id="d06f0-131">Canadá</span><span class="sxs-lookup"><span data-stu-id="d06f0-131">Canada</span></span>

- <span data-ttu-id="d06f0-132">Unión Europea (EMEA)</span><span class="sxs-lookup"><span data-stu-id="d06f0-132">European Union (EMEA)</span></span>

- <span data-ttu-id="d06f0-133">Francia</span><span class="sxs-lookup"><span data-stu-id="d06f0-133">France</span></span>

- <span data-ttu-id="d06f0-134">India</span><span class="sxs-lookup"><span data-stu-id="d06f0-134">India</span></span>

- <span data-ttu-id="d06f0-135">Japón</span><span class="sxs-lookup"><span data-stu-id="d06f0-135">Japan</span></span>

- <span data-ttu-id="d06f0-136">Reino Unido</span><span class="sxs-lookup"><span data-stu-id="d06f0-136">United Kingdom</span></span>

- <span data-ttu-id="d06f0-137">Estados Unidos (Norteamérica)</span><span class="sxs-lookup"><span data-stu-id="d06f0-137">United States (North America)</span></span>

- <span data-ttu-id="d06f0-138">Corea</span><span class="sxs-lookup"><span data-stu-id="d06f0-138">Korea</span></span>

## <a name="getting-started"></a><span data-ttu-id="d06f0-139">Introducción</span><span class="sxs-lookup"><span data-stu-id="d06f0-139">Getting started</span></span>

<span data-ttu-id="d06f0-p104">Para empezar a usar OneDrive para la Empresa multigeográfico, el primer paso es [planear el entorno de OneDrive para la Empresa multigeográfico](plan-for-multi-geo.md). Después, [obtener información sobre cómo administrar un entorno multigeográfico](administering-a-multi-geo-environment.md) y [cómo experimentarán los usuarios un entorno multigeográfico](multi-geo-user-experience.md). Cuando esté listo para configurar OneDrive para la Empresa multigeográfico, [configure el espacio empresarial como multigeográfico](multi-geo-tenant-configuration.md), luego [mueva los sitios de OneDrive existentes a sus nuevas ubicaciones multigeográficas](move-onedrive-between-geo-locations.md) y [configure la búsqueda](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="d06f0-p104">To get started with OneDrive for Business Multi-Geo, the first step is to [plan your OneDrive for Business Multi-Geo environment](plan-for-multi-geo.md). Next, [learn about administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience a multi-geo environment](multi-geo-user-experience.md). When you are ready to set up OneDrive for Business Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md), then [move any existing OneDrive sites to thier new geo-locations](move-onedrive-between-geo-locations.md) and [set up search](configure-search-for-multi-geo.md).</span></span>
