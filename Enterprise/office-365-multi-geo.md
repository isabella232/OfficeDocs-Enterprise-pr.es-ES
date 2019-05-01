---
title: Office 365 Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Expandir la presencia de Office 365 a varias regiones geográficas con Office 365 Multi-Geo.
ms.openlocfilehash: eb5c28131b7ac629d9acc607c777756b8825549c
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491956"
---
# <a name="office-365-multi-geo"></a><span data-ttu-id="2b37d-103">Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="2b37d-103">Office 365 Multi-Geo</span></span>

<span data-ttu-id="2b37d-104">Con Office 365 Multi-Geo, su organización puede expandir su presencia en Office 365 a varias regiones geográficas y países dentro de su espacio empresarial existente.</span><span class="sxs-lookup"><span data-stu-id="2b37d-104">With Office 365 Multi-Geo, your organization can expand its Office 365 presence to multiple geographic regions and/or countries within your existing tenant.</span></span> <span data-ttu-id="2b37d-105">Póngase en contacto con su equipo de cuentas de Microsoft para registrar su compañía multinacional a Office 365 Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="2b37d-105">Reach out to your Microsoft Account Team to sign up your Multi-National Company for Office 365 Multi-Geo.</span></span>
  
<span data-ttu-id="2b37d-106">Con Office 365 Multi-Geo, puede aprovisionar y almacenar los datos en reposo en las ubicaciones geográficas que haya elegido para cumplir los requisitos de residencia de datos y, al mismo tiempo, puede permitir la implementación global de experiencias de productividad modernas para sus empleados.</span><span class="sxs-lookup"><span data-stu-id="2b37d-106">With Office 365 Multi-Geo, you can provision and store data at rest in the geo locations that you've chosen to meet data residency requirements, and at the same time unlock your global roll out of modern productivity experiences to your workforce.</span></span>

#### <a name="video-introducing-office-365-multi-geo"></a><span data-ttu-id="2b37d-107">Vídeo: Introducción a Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="2b37d-107">Video: Introducing Office 365 Multi-Geo</span></span>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE1Yk6B?autoplay=false]

<span data-ttu-id="2b37d-108">En un entorno multigeográfico, su espacio empresarial de Office 365 cuenta con una ubicación central (donde se aprovisionó originalmente la suscripción a Office 365) y una o varias ubicaciones satélites.</span><span class="sxs-lookup"><span data-stu-id="2b37d-108">In a Multi-Geo environment, your Office 365 tenant consists of a central location (where your Office 365 subscription was originally provisioned) and one or more satellite locations.</span></span> <span data-ttu-id="2b37d-109">En un espacio empresarial multigeográfico, la información sobre las ubicaciones geográficas, grupos y la información de usuario, se controla en Azure Active Directory (AAD).</span><span class="sxs-lookup"><span data-stu-id="2b37d-109">In a multi-geo tenant, the information about geo locations, groups, and user information, is mastered in Azure Active Directory (AAD).</span></span> <span data-ttu-id="2b37d-110">Como la información del espacio empresarial se controla de forma centralizada y se sincroniza en cada ubicación geográfica, el uso compartido y las experiencias que involucran a todos los empleados de su compañía comparten una conciencia global.</span><span class="sxs-lookup"><span data-stu-id="2b37d-110">Because your tenant information is mastered centrally and synchronized into each geo location, sharing and experiences involving anyone from your company contain global awareness.</span></span>

![Captura de pantalla del mapa multigeográfico desde el Centro de administración de SharePoint Online](media/multi-geo-world-map.png)

<span data-ttu-id="2b37d-112">Tenga en cuenta que Office 365 Multi-Geo no está diseñado principalmente para optimizar el rendimiento, sino que para cumplir con los requisitos de residencia de datos.</span><span class="sxs-lookup"><span data-stu-id="2b37d-112">Note that Office 365 Multi-Geo is not primarily designed for performance optimization, it is designed to meet data residency requirements.</span></span> <span data-ttu-id="2b37d-113">Para obtener información sobre la optimización del rendimiento de Office 365, vea [Ajuste de rendimiento y planes de red para Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o póngase en contacto con su grupo de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="2b37d-113">For information about performance optimization for Office 365, see [Network planning and performance tuning for Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) or contact your support group.</span></span>

## <a name="terminology"></a><span data-ttu-id="2b37d-114">Terminología</span><span class="sxs-lookup"><span data-stu-id="2b37d-114">Terminology</span></span>

<span data-ttu-id="2b37d-115">Estos son los términos clave utilizados para describir Office 365 Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="2b37d-115">Here are the key terms used in describing Office 365 Multi-Geo:</span></span>

- <span data-ttu-id="2b37d-116">**Ubicación central**: la ubicación geográfica en la que se ha aprovisionado originalmente el espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="2b37d-116">**Central location** - the geo location where your tenant was originally provisioned.</span></span>
- <span data-ttu-id="2b37d-117">**Administrador geográfico**: un administrador que puede administrar una o varias ubicaciones satélites especificadas.</span><span class="sxs-lookup"><span data-stu-id="2b37d-117">**Geo administrator** - An administrator who can administer one or more specified satellite locations.</span></span>
- <span data-ttu-id="2b37d-118">**Código geográfico**: un código de tres letras de una ubicación geográfica determinada.</span><span class="sxs-lookup"><span data-stu-id="2b37d-118">**Geo code** - a three-letter code for a given geo location.</span></span>
- <span data-ttu-id="2b37d-119">**Ubicación geográfica**: una ubicación geográfica que puede usarse en un espacio empresarial multigeográfico para alojar datos, como los buzones de Exchange y los sitios de SharePoint y OneDrive.</span><span class="sxs-lookup"><span data-stu-id="2b37d-119">**Geo location** – A geographic location that can be used in a multi-geo tenant to host data, including Exchange mailboxes and OneDrive and SharePoint sites.</span></span>
- <span data-ttu-id="2b37d-120">**Ubicación de datos preferida (PDL)**: una propiedad de usuario que establece el administrador e indica la ubicación geográfica donde se deben aprovisionar los buzones de Exchange de usuarios y OneDrive.</span><span class="sxs-lookup"><span data-stu-id="2b37d-120">**Preferred Data Location (PDL)** – A user property set by the administrator that indicates where the geo location where the users Exchange mailbox and OneDrive should be provisioned.</span></span> <span data-ttu-id="2b37d-121">La PDL también determina dónde aprovisionar sitios de SharePoint creados por el usuario.</span><span class="sxs-lookup"><span data-stu-id="2b37d-121">The PDL also determines where SharePoint sites that are created by the user are provisioned.</span></span>
- <span data-ttu-id="2b37d-122">**Ubicación de satélite**: las ubicaciones geográficas donde están habilitadas las cargas de trabajo compatibles geográficamente de Office 365 (Exchange, OneDrive y SharePoint) en un espacio empresarial multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="2b37d-122">**Satellite location** – The geo locations where the geo-aware Office 365 workloads (SharePoint, OneDrive, and Exchange) are enabled in a multi-geo tenant.</span></span>
- <span data-ttu-id="2b37d-123">**Espacio empresarial**: la representación de una organización de Office 365, que suele tener uno o más dominios asociados (por ejemplo, contoso.com).</span><span class="sxs-lookup"><span data-stu-id="2b37d-123">**Tenant** – An organization's representation in Office 365 which typically has one or more domains associated with it (for example, contoso.com).</span></span>

## <a name="office-365-multi-geo-availability"></a><span data-ttu-id="2b37d-124">Disponibilidad de Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="2b37d-124">Office 365 Multi-Geo availability</span></span>

<span data-ttu-id="2b37d-125">Actualmente, se ofrece Office 365 Multi-Geo en estos países y regiones:</span><span class="sxs-lookup"><span data-stu-id="2b37d-125">Office 365 Multi-Geo is currently offered in these regions and countries:</span></span>

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="getting-started"></a><span data-ttu-id="2b37d-126">Introducción</span><span class="sxs-lookup"><span data-stu-id="2b37d-126">Getting started</span></span>

<span data-ttu-id="2b37d-127">Siga estos pasos para empezar a usar Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="2b37d-127">Follow these steps to get started with multi-geo:</span></span>

1. <span data-ttu-id="2b37d-128">Trabaje con el equipo de cuentas para agregar el plan de servicio _Funciones multigeográficas en Office 365_.</span><span class="sxs-lookup"><span data-stu-id="2b37d-128">Work with your account team to add the _Multi-Geo Capabilities in Office 365_ service plan.</span></span> <span data-ttu-id="2b37d-129">Le guiará para agregar el número de licencias necesarias.</span><span class="sxs-lookup"><span data-stu-id="2b37d-129">They will guide you to add the number of licenses needed.</span></span> <span data-ttu-id="2b37d-130">La característica multigeográfica está disponible actualmente para los clientes con un mínimo de 2 500 suscripciones a Office 365.</span><span class="sxs-lookup"><span data-stu-id="2b37d-130">Multi-Geo feature is available to customers with a minimum of 2,500 Office 365 subscriptions.</span></span>

   <span data-ttu-id="2b37d-131">Antes de empezar a usar Office 365 Multi-Geo, Microsoft necesita configurar el espacio empresarial de Exchange Online para la compatibilidad con Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="2b37d-131">Before you can start using Office 365 Multi-Geo, Microsoft needs to configure your Exchange Online tenant for multi-geo support.</span></span> <span data-ttu-id="2b37d-132">Este proceso de configuración única se activa después de pedir el plan de servicio de las *Capacidades multigeográficas de Office 365* y después de que las licencias se muestren en el espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="2b37d-132">This one-time configuration process is triggered after you order the *Multi-Geo Capabilities in Office 365* service plan and the licenses show up in your tenant.</span></span> <span data-ttu-id="2b37d-133">Recibirá notificaciones en el [centro de mensajes de Office 365](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) cuando se apliquen las licencias Multi-Geo y, después, puede empezar a configurar y usar las capacidades de Office 365 Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="2b37d-133">You'll receive notifications in the [Office 365 message center](https://support.office.com/article/38FB3333-BFCC-4340-A37B-DEDA509C2093) once your Multi-Geo licenses are applied and you then may begin configuring and using your Office 365 Multi-Geo capabilities.</span></span>

2. <span data-ttu-id="2b37d-134">Lea [Planificar el entorno multigeográfico](plan-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="2b37d-134">Read [Plan your multi-geo environment](plan-for-multi-geo.md).</span></span>

3. <span data-ttu-id="2b37d-135">Obtenga información sobre cómo [administrar un entorno multigeográfico](administering-a-multi-geo-environment.md) y [cómo los usuarios experimentarán el entorno](multi-geo-user-experience.md).</span><span class="sxs-lookup"><span data-stu-id="2b37d-135">Learn about [administering a multi-geo environment](administering-a-multi-geo-environment.md) and [how your users will experience the environment](multi-geo-user-experience.md).</span></span>

4. <span data-ttu-id="2b37d-136">Cuando esté listo para configurar Office 365 Multi-Geo, [configure su espacio empresarial multigeográfico](multi-geo-tenant-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="2b37d-136">When you are ready to set up Office 365 Multi-Geo, [configure your tenant for multi-geo](multi-geo-tenant-configuration.md).</span></span>

5. <span data-ttu-id="2b37d-137">[Configure la búsqueda](configure-search-for-multi-geo.md).</span><span class="sxs-lookup"><span data-stu-id="2b37d-137">[Set up search](configure-search-for-multi-geo.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2b37d-138">Vea también</span><span class="sxs-lookup"><span data-stu-id="2b37d-138">See also</span></span>

[<span data-ttu-id="2b37d-139">Capacidades multigeográficas en Exchange Online y OneDrive</span><span class="sxs-lookup"><span data-stu-id="2b37d-139">Multi-Geo in Exchange Online and OneDrive</span></span>](https://Aka.ms/GoMultiGeo)

[<span data-ttu-id="2b37d-140">Capacidades multigeográficas de OneDrive y SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2b37d-140">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)

[<span data-ttu-id="2b37d-141">Capacidades multigeográficas de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="2b37d-141">Multi-Geo Capabilities in Exchange Online</span></span>](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-exchange-online)
