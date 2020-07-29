---
title: Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Normal
description: Expanda la presencia de Microsoft 365 a varias regiones geográficas con Microsoft 365 Multi-Geo.
ms.openlocfilehash: 01683caa3dfebc8331bb0b4b6ba239be2e0d9aaa
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433811"
---
# <a name="microsoft-365-multi-geo"></a><span data-ttu-id="32255-103">Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="32255-103">Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="32255-104">Con Microsoft 365 Multi-Geo, su organización puede expandir su presencia en Microsoft 365 a varias regiones geográficas y países dentro de su espacio empresarial existente.</span><span class="sxs-lookup"><span data-stu-id="32255-104">With Microsoft 365 Multi-Geo, your organization can expand its Microsoft 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="32255-105">Póngase en contacto con su equipo de cuentas de Microsoft para registrar su compañía multinacional a Microsoft 365 Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="32255-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for Microsoft 365 Multi-Geo.</span></span>
  
<span data-ttu-id="32255-106">Con Microsoft 365 Multi-Geo, puede aprovisionar y almacenar los datos en reposo en las ubicaciones geográficas que haya elegido para cumplir los requisitos de residencia de datos y, al mismo tiempo, puede permitir la implementación global de experiencias de productividad modernas para sus empleados.</span><span class="sxs-lookup"><span data-stu-id="32255-106">With Microsoft 365 Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-microsoft-365-multi-geo"></a><span data-ttu-id="32255-107">Vídeo: Presentación de Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="32255-107">Video: Introducing Microsoft 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="32255-108">En un entorno multigeográfico, su espacio empresarial de Microsoft 365 cuenta con una ubicación central (donde se aprovisionó originalmente la suscripción a Microsoft 365) y una o varias ubicaciones satélites.</span><span class="sxs-lookup"><span data-stu-id="32255-108">In a Multi-Geo environment, your Microsoft 365 tenant consists of a central location (where your Microsoft 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="32255-109">En un espacio empresarial multigeográfico, la información sobre las ubicaciones geográficas, grupos y la información de usuario, se controla en Azure Active Directory (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="32255-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (Azure AD).</span></span> <span data-ttu-id="32255-110">Como la información del espacio empresarial se controla de forma centralizada y se sincroniza en cada ubicación geográfica, el uso compartido y las experiencias que involucran a todos los empleados de su compañía comparten una conciencia global.</span><span class="sxs-lookup"><span data-stu-id="32255-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![Captura de pantalla del mapa multigeográfico desde el Centro de administración de SharePoint Online](media/multi-geo-world-map.png)

<span data-ttu-id="32255-112">Tenga en cuenta que Microsoft 365 Multi-Geo no está diseñado principalmente para optimizar el rendimiento, sino para cumplir con los requisitos de residencia de datos.</span><span class="sxs-lookup"><span data-stu-id="32255-112">Note that Microsoft 365 Multi-Geo is not designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="32255-113">Para obtener información sobre la optimización del rendimiento de Microsoft 365, vea [Network planning and performance tuning for Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) (Planeamiento de red y ajuste de rendimiento para Microsoft 365) o póngase en contacto con su grupo de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="32255-113">For information about performance optimization for Microsoft 365, see [Network planning and performance tuning for Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="32255-114">Terminología</span><span class="sxs-lookup"><span data-stu-id="32255-114">Terminology</span></span>

<span data-ttu-id="32255-115">Estos son los términos clave utilizados para describir Microsoft 365 Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="32255-115">Here are the key terms used in describing Microsoft 365 Multi-Geo:</span></span>

- <span data-ttu-id="32255-116">**Ubicación central**: la ubicación geográfica en la que se ha aprovisionado originalmente el espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="32255-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="32255-117">**Administrador geográfico**: un administrador que puede administrar una o varias ubicaciones satélites especificadas.</span><span class="sxs-lookup"><span data-stu-id="32255-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="32255-118">**Código geográfico**: un código de tres letras de una ubicación geográfica determinada.</span><span class="sxs-lookup"><span data-stu-id="32255-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="32255-119">**Ubicación geográfica**: una ubicación geográfica que puede usarse en un espacio empresarial multigeográfico para alojar datos, como los buzones de Exchange y los sitios de SharePoint y OneDrive.</span><span class="sxs-lookup"><span data-stu-id="32255-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="32255-120">**Ubicación de datos preferida (PDL)**: una propiedad de usuario que establece el administrador e indica la ubicación geográfica donde se deben aprovisionar los buzones de Exchange de usuarios y OneDrive.</span><span class="sxs-lookup"><span data-stu-id="32255-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="32255-121">La PDL también determina dónde aprovisionar sitios de SharePoint creados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="32255-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="32255-122">**Ubicación satélite**: las ubicaciones geográficas donde están habilitadas las cargas de trabajo compatibles geográficamente de Microsoft 365 (Exchange, OneDrive y SharePoint) en un espacio empresarial multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="32255-122">**Satellite location** – The geo locations where the geo-aware Microsoft 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="32255-123">**Cuenta empresarial**: la representación de una organización de Microsoft 365, que suele tener uno o más dominios asociados (por ejemplo, contoso.com).</span><span class="sxs-lookup"><span data-stu-id="32255-123">**Tenant** – An organization's representation in Microsoft 365 which typically has one or more domains associated with it (for example, contoso.com).</span></span>

## <a name="licensing"></a><span data-ttu-id="32255-124">Licencias</span><span class="sxs-lookup"><span data-stu-id="32255-124">Licensing</span></span>

<span data-ttu-id="32255-125">Microsoft 365 Multi-Geo está disponible como complemento en los siguientes planes de suscripción de Microsoft 365 para los clientes de EA con un mínimo de 250 puestos de Microsoft 365 en su espacio empresarial y un mínimo del 5% de estos puestos con un entorno multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="32255-125">Microsoft 365 Multi-Geo is available as an add-on to the following Microsoft 365 subscription plans for EA customers with a minimum of 250 Microsoft 365 seats in their tenant, and a minimum of 5% of those seats using multi-geo.</span></span> <span data-ttu-id="32255-126">Póngase en contacto con el equipo de su cuenta de Microsoft para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="32255-126">Please contact your Microsoft account team for details.</span></span>

- <span data-ttu-id="32255-127">Microsoft 365 F1, E1, E3 o E5</span><span class="sxs-lookup"><span data-stu-id="32255-127">Microsoft 365 F1, E1, E3, or E5</span></span>
- <span data-ttu-id="32255-128">Exchange Online (plan 1 o plan 2)</span><span class="sxs-lookup"><span data-stu-id="32255-128">Exchange Online Plan 1 or Plan 2</span></span>
- <span data-ttu-id="32255-129">OneDrive para la Empresa (plan 1 o plan 2)</span><span class="sxs-lookup"><span data-stu-id="32255-129">OneDrive for Business Plan 1 or Plan 2</span></span>
- <span data-ttu-id="32255-130">SharePoint Online (plan 1 o plan 2)</span><span class="sxs-lookup"><span data-stu-id="32255-130">SharePoint Online Plan 1 or Plan 2</span></span>

## <a name="microsoft-365-multi-geo-availability"></a><span data-ttu-id="32255-131">Disponibilidad de Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="32255-131">Microsoft 365 Multi-Geo availability</span></span>

<span data-ttu-id="32255-132">Actualmente, se ofrece Microsoft 365 Multi-Geo en estos países y regiones:</span><span class="sxs-lookup"><span data-stu-id="32255-132">Microsoft 365 Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="32255-133">Introducción</span><span class="sxs-lookup"><span data-stu-id="32255-133">Getting started</span></span>

<span data-ttu-id="32255-134">Siga estos pasos para empezar a usar Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="32255-134">Follow these steps to get started with multi-geo:</span></span>

1. <span data-ttu-id="32255-135">Trabaje con el equipo de cuentas para agregar el plan de servicio _Funciones multigeográficas en Microsoft 365_.</span><span class="sxs-lookup"><span data-stu-id="32255-135">Work with your account team to add the _Multi-Geo Capabilities in Microsoft 365_ service plan.</span></span> <span data-ttu-id="32255-136">Le guiará para agregar el número de licencias necesarias.</span><span class="sxs-lookup"><span data-stu-id="32255-136">They will guide you to add the number of licenses needed.</span></span> <span data-ttu-id="32255-137">La característica multigeográfica está disponible actualmente para los clientes EA con un mínimo de 250 suscripciones a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="32255-137">Multi-Geo feature is available to EA customers with a minimum of 250 Microsoft 365 subscriptions.</span></span>

   <span data-ttu-id="32255-138">Antes de empezar a usar Microsoft 365 Multi-Geo, Microsoft necesita configurar el espacio empresarial de Exchange Online para la compatibilidad con Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="32255-138">Before you can start using Microsoft 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="32255-139">Este proceso de configuración única se activa después de pedir el plan de servicio de las *Capacidades multigeográficas de Microsoft 365* y después de que las licencias se muestren en el espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="32255-139">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Microsoft 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="32255-140">Recibirá notificaciones en el [centro de mensajes de Microsoft 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) cuando se apliquen las licencias Multi-Geo y, después, puede empezar a configurar y usar las capacidades de Microsoft 365 Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="32255-140">You'll receive notifications in the [Microsoft 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Microsoft 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="32255-141">Lea [Planificar el entorno multigeográfico](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="32255-141">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="32255-142">Obtenga información sobre cómo [administrar un entorno multigeográfico](administering-a-multi-geo-environment.md) y [cómo los usuarios experimentarán el entorno](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="32255-142">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="32255-143">Cuando esté listo para configurar Microsoft 365 Multi-Geo, [configure su espacio empresarial multigeográfico](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="32255-143">When you are ready to set up Microsoft 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="32255-144">[Configure la búsqueda](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="32255-144">[Set up search](configure-search-for-multi-geo.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="32255-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="32255-145">See also</span></span>

[<span data-ttu-id="32255-146">Capacidades multigeográficas en Exchange Online y OneDrive</span><span class="sxs-lookup"><span data-stu-id="32255-146">Multi-Geo in Exchange Online and OneDrive</span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="32255-147">Capacidades multigeográficas de OneDrive y SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="32255-147">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[<span data-ttu-id="32255-148">Capacidades multigeográficas de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="32255-148">Multi-Geo Capabilities in Exchange Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)

[<span data-ttu-id="32255-149">Experiencia de equipos en un entorno multigeo</span><span class="sxs-lookup"><span data-stu-id="32255-149">Teams experience in a multi-geo environment</span></span>](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo)
