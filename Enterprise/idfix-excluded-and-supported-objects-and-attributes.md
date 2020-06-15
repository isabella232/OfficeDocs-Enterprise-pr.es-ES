---
title: Objetos y atributos admitidos y excluidos en IdFix
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Enumera los atributos que se excluyen y son compatibles con la herramienta IdFix.
ms.openlocfilehash: da9a59d60b1ae2f1f68803e5a10afba16207fc69
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711580"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="4a73b-103">Objetos y atributos admitidos y excluidos en IdFix</span><span class="sxs-lookup"><span data-stu-id="4a73b-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="4a73b-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="4a73b-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="4a73b-105">Hay dos conjuntos de reglas que se mantienen en IdFix; Multiinquilino y dedicado/ITAR.</span><span class="sxs-lookup"><span data-stu-id="4a73b-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="4a73b-106">En este momento, los dos conjuntos de reglas excluyen los mismos objetos, atributos y valores de atributo de su búsqueda.</span><span class="sxs-lookup"><span data-stu-id="4a73b-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="4a73b-107">Esto puede cambiar en futuras versiones.</span><span class="sxs-lookup"><span data-stu-id="4a73b-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="4a73b-108">Exclusiones de error dedicadas y multiinquilino usadas por IdFix</span><span class="sxs-lookup"><span data-stu-id="4a73b-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="4a73b-109">En esta sección se enumeran los objetos, los atributos y los valores que se excluyen en IdFix de su búsqueda en el directorio.</span><span class="sxs-lookup"><span data-stu-id="4a73b-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="4a73b-110">El asterisco ( \* ) es un carácter comodín que se puede sustituir por otros caracteres.</span><span class="sxs-lookup"><span data-stu-id="4a73b-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="4a73b-111">Objetos, atributos y valores excluidos durante una búsqueda de IdFix</span><span class="sxs-lookup"><span data-stu-id="4a73b-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="4a73b-112">**Exclusión**</span><span class="sxs-lookup"><span data-stu-id="4a73b-112">**Exclusion**</span></span>|<span data-ttu-id="4a73b-113">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="4a73b-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="4a73b-114">Elección\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-114">Admini\*</span></span> |<span data-ttu-id="4a73b-115">Administrador</span><span class="sxs-lookup"><span data-stu-id="4a73b-115">Administrator</span></span> |
|<span data-ttu-id="4a73b-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-116">CAS_{\*</span></span>  |<span data-ttu-id="4a73b-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="4a73b-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="4a73b-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="4a73b-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="4a73b-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="4a73b-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-120">FederatedEmail\*</span></span> |<span data-ttu-id="4a73b-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="4a73b-121">FederatedEmail.</span></span> <span data-ttu-id="4a73b-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="4a73b-122">*GUID*</span></span> |
|<span data-ttu-id="4a73b-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-123">Guest\*</span></span> ||
|<span data-ttu-id="4a73b-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-124">HTTPConnector\*</span></span>  |<span data-ttu-id="4a73b-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="4a73b-125">HTTPConnector</span></span> |
|<span data-ttu-id="4a73b-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-126">krbtgt\*</span></span> |<span data-ttu-id="4a73b-127">MS-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="4a73b-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="4a73b-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-128">iusr_\*</span></span> |<span data-ttu-id="4a73b-129">iusr_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="4a73b-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="4a73b-130">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-130">iwam\*</span></span>  |<span data-ttu-id="4a73b-131">IWAM_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="4a73b-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="4a73b-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-132">msol\*</span></span> |<span data-ttu-id="4a73b-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="4a73b-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="4a73b-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-134">support_\*</span></span> ||
|<span data-ttu-id="4a73b-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-135">SystemMailbox\*</span></span> |<span data-ttu-id="4a73b-136">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="4a73b-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="4a73b-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="4a73b-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="4a73b-138">distinguishedName contiene "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="4a73b-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="4a73b-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="4a73b-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="4a73b-140">El objeto contiene el atributo IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="4a73b-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="4a73b-141">Consulte [atributos isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="4a73b-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="4a73b-142">Atributos y objetos dedicados multiinquilinos y dedicados comprobados por IdFix</span><span class="sxs-lookup"><span data-stu-id="4a73b-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="4a73b-143">Los atributos que se comprueban para detectar errores en IdFix se describen en la sección "preparación de objetos y atributos de directorio" en [preparar atributos de directorio para la sincronización con Microsoft 365 mediante la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="4a73b-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Microsoft 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

