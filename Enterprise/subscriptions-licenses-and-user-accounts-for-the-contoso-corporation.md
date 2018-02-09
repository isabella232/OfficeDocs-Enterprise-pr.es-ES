---
title: Suscripciones, licencias y cuentas de usuario para Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 'Resumen: Comprender la estructura de los inquilinos, cuentas de usuario, licencias y suscripciones de nube de Contoso.'
ms.openlocfilehash: 6e62fbbc0f52019e5d233fc73992b000952344f5
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a><span data-ttu-id="d4c1c-103">Suscripciones, licencias y cuentas de usuario para Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="d4c1c-103">Subscriptions, licenses, and user accounts for the Contoso Corporation</span></span>

 <span data-ttu-id="d4c1c-104">**Resumen:** Comprender la estructura de los inquilinos, cuentas de usuario, licencias y suscripciones de nube de Contoso.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-104">**Summary:** Understand the structure of Contoso's cloud subscriptions, licenses, user accounts, and tenants.</span></span>
  
<span data-ttu-id="d4c1c-105">Para proporcionar un uso coherente de las identidades y la facturación para todas las ofertas de nube, Microsoft ofrece una jerarquía de cuentas de organización, suscripciones, licencias y usuario.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-105">To provide a consistent use of identities and billing for all cloud offerings, Microsoft provides an organization/subscriptions/licenses/user accounts hierarchy:</span></span>
  
- <span data-ttu-id="d4c1c-106">Organización</span><span class="sxs-lookup"><span data-stu-id="d4c1c-106">Organization</span></span>
    
    <span data-ttu-id="d4c1c-107">La entidad empresarial que usa las ofertas de nube de Microsoft, normalmente identificadas por un nombre de dominio DNS público, como contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-107">The business entity that is using Microsoft cloud offerings, typically identified by a public DNS domain name, such as contoso.com.</span></span>
    
- <span data-ttu-id="d4c1c-108">Suscripciones</span><span class="sxs-lookup"><span data-stu-id="d4c1c-108">Subscriptions</span></span>
    
    <span data-ttu-id="d4c1c-p101">Para Microsoft SaaS (Office 365, Intune/EMS y Dynamics 365) de las ofertas de nube, una suscripción es un producto específico y un conjunto de licencias de usuario comprado. Para Azure, una suscripción permite la facturación de los servicios de nube consumido a la organización.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-p101">For Microsoft SaaS cloud offerings (Office 365, Intune/EMS, and Dynamics 365), a subscription is a specific product and a purchased set of user licenses. For Azure, a subscription allows for billing of consumed cloud services to the organization.</span></span>
    
- <span data-ttu-id="d4c1c-111">Licencias</span><span class="sxs-lookup"><span data-stu-id="d4c1c-111">Licenses</span></span>
    
    <span data-ttu-id="d4c1c-p102">Para las ofertas de nube de Microsoft SaaS, una licencia permite una cuenta de usuario específica utilizar los servicios de nube. Para Azure, licencias de software se crean en tarifas de servicio, pero en algunos casos que necesitará adquirir licencias de software adicionales.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-p102">For Microsoft SaaS cloud offerings, a license allows a specific user account to use cloud services. For Azure, software licenses are built into service pricing, but in some cases you will need to purchase additional software licenses.</span></span>
    
- <span data-ttu-id="d4c1c-114">Cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d4c1c-114">User accounts</span></span>
    
    <span data-ttu-id="d4c1c-115">Las cuentas de usuario se almacenan en un inquilino de Azure AD y pueden sincronizarse desde un proveedor de identidades local como Windows Server AD.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-115">User accounts are stored in an Azure AD tenant and can be synchronized from an on-premises identity provider such as Windows Server AD.</span></span>
    
## <a name="contosos-structure"></a><span data-ttu-id="d4c1c-116">Estructura de Contoso</span><span class="sxs-lookup"><span data-stu-id="d4c1c-116">Contoso's structure</span></span>

<span data-ttu-id="d4c1c-117">Contoso determinó la siguiente estructura para la organización y sus suscripciones, licencias, cuentas e inquilinos:</span><span class="sxs-lookup"><span data-stu-id="d4c1c-117">Contoso determined the following structure for the organization and its subscriptions, licenses, accounts, and tenants:</span></span>
  
<span data-ttu-id="d4c1c-118">**Figura 1: Contoso organización, suscripciones, licencias, cuentas de usuario y los inquilinos**</span><span class="sxs-lookup"><span data-stu-id="d4c1c-118">**Figure 1: Contoso's organization, subscriptions, licenses, user accounts and tenants**</span></span>

![Organización, suscripciones, licencias, cuentas de usuario e inquilinos de Contoso](images/Contoso_Poster/Subscriptions.png)
  
<span data-ttu-id="d4c1c-120">La figura 1 muestra cómo la organización Contoso incluye varias suscripciones y está vinculada a un inquilino común de Azure AD que contiene las cuentas de usuario que se sincronizan desde el bosque de Windows Server AD de contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-120">Figure 1 shows how the Contoso organization includes multiple subscriptions and is tied to a common Azure AD tenant that contains the user accounts synchronized from the contoso.com Windows Server AD forest.</span></span>
  
- <span data-ttu-id="d4c1c-121">**Organización** Contoso Corporation se identifica mediante su nombre de dominio público contoso.com.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-121">**Organization** The Contoso Corporation is identified by its public domain name contoso.com.</span></span>
    
  - <span data-ttu-id="d4c1c-122">**Suscripciones y licencias** La empresa Contoso utiliza lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d4c1c-122">**Subscriptions and licenses** The Contoso Corporation is using the following:</span></span>
    
  - <span data-ttu-id="d4c1c-123">El producto de Office 365 Enterprise E3 con 5.000 licencias</span><span class="sxs-lookup"><span data-stu-id="d4c1c-123">The Office 365 Enterprise E3 product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="d4c1c-124">Producto Office 365 Enterprise E5 con 200 licencias</span><span class="sxs-lookup"><span data-stu-id="d4c1c-124">The Office 365 Enterprise E5 product with 200 licenses</span></span>
    
  - <span data-ttu-id="d4c1c-125">El producto EMS con 5.000 licencias</span><span class="sxs-lookup"><span data-stu-id="d4c1c-125">The EMS product with 5,000 licenses</span></span>
    
  - <span data-ttu-id="d4c1c-126">El producto Dynamics 365 con 100 licencias</span><span class="sxs-lookup"><span data-stu-id="d4c1c-126">The Dynamics 365 product with 100 licenses</span></span>
    
  - <span data-ttu-id="d4c1c-127">Varias suscripciones de Azure según las regiones</span><span class="sxs-lookup"><span data-stu-id="d4c1c-127">Multiple Azure subscriptions based on regions</span></span>
    
  - <span data-ttu-id="d4c1c-128">**Cuentas de usuario** Un arrendatario común de Azure AD contiene la lista de cuentas de usuario y grupos utilizan todas las suscripciones de Contoso, a excepción de pruebas y desarrollo Azure suscripciones.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-128">**User accounts** A common Azure AD tenant contains the list of user accounts and groups used by all of Contoso's subscriptions, with the exception of dev/test Azure subscriptions.</span></span>
    
<span data-ttu-id="d4c1c-129">Para los inquilinos de Contoso:</span><span class="sxs-lookup"><span data-stu-id="d4c1c-129">For Contoso's tenants:</span></span>
  
- <span data-ttu-id="d4c1c-p103">Para las ofertas de nube de SaaS, el arrendatario es la ubicación regional que aloja a los servidores que proporcionan servicios de nube. Contoso ha elegido la región europea para alojar a sus arrendatarios de Office 365, EMS y Dynamics 365.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-p103">For SaaS cloud offerings, the tenant is the regional location that houses the servers providing cloud services. Contoso chose the European region to host its Office 365, EMS, and Dynamics 365 tenants.</span></span> 
    
- <span data-ttu-id="d4c1c-p104">Los servicios de Azure PaaS y aplicaciones y cargas de trabajo de TI de IaaS pueden tener tenencia en cualquier centro de datos de Azure en todo el mundo. Un arrendatario AD Azure es una instancia específica de Azure AD que contiene las cuentas y grupos.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-p104">Azure PaaS services and apps and IaaS IT workloads can have tenancy in any Azure datacenter across the world. An Azure AD tenant is a specific instance of Azure AD containing accounts and groups.</span></span>
    
- <span data-ttu-id="d4c1c-134">El inquilino AD Azure comun que contiene las cuentas sincronizadas para el bosque de Windows Server de Contoso AD proporciona IDaaS en las ofertas de nube de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-134">The common Azure AD tenant that contains the synchronized accounts for the Contoso Windows Server AD forest provides IDaaS across Microsoft's cloud offerings.</span></span>
    
<span data-ttu-id="d4c1c-135">Para obtener más información, consulte [suscripciones, licencias, cuentas y los inquilinos para las ofertas de nube de Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span><span class="sxs-lookup"><span data-stu-id="d4c1c-135">For more information, see [Subscriptions, licenses, accounts, and tenants for Microsoft's cloud offerings](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).</span></span>
  
## <a name="contosos-azure-subscriptions"></a><span data-ttu-id="d4c1c-136">Suscripciones de Azure de Contoso</span><span class="sxs-lookup"><span data-stu-id="d4c1c-136">Contoso's Azure subscriptions</span></span>

<span data-ttu-id="d4c1c-137">La figura 2 muestra el diseño jerárquico de suscripciones de Azure de Contoso:</span><span class="sxs-lookup"><span data-stu-id="d4c1c-137">Figure 2 shows the hierarchical design of Contoso's Azure subscriptions:</span></span>
  
<span data-ttu-id="d4c1c-138">**Figura 2: Estructura de Contoso para suscripciones de Azure**</span><span class="sxs-lookup"><span data-stu-id="d4c1c-138">**Figure 2: Contoso's structure for Azure subscriptions**</span></span>

![Estructura de Contoso para las suscripciones a Azure](images/Contoso_Poster/Subscriptions_Nested.png)
  
- <span data-ttu-id="d4c1c-140">Contoso está en la parte superior, de acuerdo con su Contrato Enterprise con Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-140">Contoso is at the top, based on its Enterprise Agreement with Microsoft.</span></span>
    
- <span data-ttu-id="d4c1c-141">Hay un conjunto de cuentas correspondiente a las diferentes regiones de Contoso Corporation todo el mundo, basado en los dominios del bosque de Windows Server AD de Contoso.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-141">There are a set of accounts corresponding to the different regions of the Contoso Corporation around the world, based on the domains of Contoso's Windows Server AD forest.</span></span>
    
- <span data-ttu-id="d4c1c-142">Dentro de cada región, hay una o más suscripciones basadas en necesidades de implementación de desarrollo, pruebas y producción de la región.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-142">Within each region, there are one or more subscriptions based on the region's development, testing, and production deployment needs.</span></span>
    
<span data-ttu-id="d4c1c-p105">Cada suscripción de Azure puede asociarse a un solo inquilino de Azure AD que contenga cuentas de usuario y grupos para la autenticación y la autorización para los servicios de Azure. Las suscripciones de producción usan el inquilino de Azure AD común de Contoso.</span><span class="sxs-lookup"><span data-stu-id="d4c1c-p105">Each Azure subscription can be associated with a single Azure AD tenant that contains user accounts and groups for authentication and authorization to Azure services. Production subscriptions use the common Contoso Azure AD tenant.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d4c1c-145">See Also</span><span class="sxs-lookup"><span data-stu-id="d4c1c-145">See Also</span></span>

[<span data-ttu-id="d4c1c-146">Contoso en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4c1c-146">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="d4c1c-147">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="d4c1c-147">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="d4c1c-148">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="d4c1c-148">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)




