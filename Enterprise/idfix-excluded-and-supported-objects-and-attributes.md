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
ms.openlocfilehash: 0203f47864dc4222cd2f95a4e67b2f10bec44f71
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41840147"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="89cd5-103">Objetos y atributos admitidos y excluidos en IdFix</span><span class="sxs-lookup"><span data-stu-id="89cd5-103">IdFix excluded and supported objects and attributes</span></span>

<span data-ttu-id="89cd5-104">*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="89cd5-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="89cd5-105">Hay dos conjuntos de reglas que se mantienen en IdFix; Multiinquilino y dedicado/ITAR.</span><span class="sxs-lookup"><span data-stu-id="89cd5-105">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR.</span></span> <span data-ttu-id="89cd5-106">En este momento, los dos conjuntos de reglas excluyen los mismos objetos, atributos y valores de atributo de su búsqueda.</span><span class="sxs-lookup"><span data-stu-id="89cd5-106">At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search.</span></span> <span data-ttu-id="89cd5-107">Esto puede cambiar en futuras versiones.</span><span class="sxs-lookup"><span data-stu-id="89cd5-107">This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="89cd5-108">Exclusiones de error dedicadas y multiinquilino usadas por IdFix</span><span class="sxs-lookup"><span data-stu-id="89cd5-108">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="89cd5-109">En esta sección se enumeran los objetos, los atributos y los valores que se excluyen en IdFix de su búsqueda en el directorio.</span><span class="sxs-lookup"><span data-stu-id="89cd5-109">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory.</span></span> <span data-ttu-id="89cd5-110">El asterisco (\*) es un carácter comodín que se puede sustituir por otros caracteres.</span><span class="sxs-lookup"><span data-stu-id="89cd5-110">The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="89cd5-111">Objetos, atributos y valores excluidos durante una búsqueda de IdFix</span><span class="sxs-lookup"><span data-stu-id="89cd5-111">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="89cd5-112">**Exclusión**</span><span class="sxs-lookup"><span data-stu-id="89cd5-112">**Exclusion**</span></span>|<span data-ttu-id="89cd5-113">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="89cd5-113">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="89cd5-114">Elección\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-114">Admini\*</span></span> |<span data-ttu-id="89cd5-115">Administrador</span><span class="sxs-lookup"><span data-stu-id="89cd5-115">Administrator</span></span> |
|<span data-ttu-id="89cd5-116">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-116">CAS_{\*</span></span>  |<span data-ttu-id="89cd5-117">CAS_ {fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="89cd5-117">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="89cd5-118">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-118">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="89cd5-119">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="89cd5-119">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="89cd5-120">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-120">FederatedEmail\*</span></span> |<span data-ttu-id="89cd5-121">FederatedEmail.</span><span class="sxs-lookup"><span data-stu-id="89cd5-121">FederatedEmail.</span></span> <span data-ttu-id="89cd5-122">*GUID*</span><span class="sxs-lookup"><span data-stu-id="89cd5-122">*GUID*</span></span> |
|<span data-ttu-id="89cd5-123">Guest\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-123">Guest\*</span></span> ||
|<span data-ttu-id="89cd5-124">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-124">HTTPConnector\*</span></span>  |<span data-ttu-id="89cd5-125">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="89cd5-125">HTTPConnector</span></span> |
|<span data-ttu-id="89cd5-126">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-126">krbtgt\*</span></span> |<span data-ttu-id="89cd5-127">MS-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="89cd5-127">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="89cd5-128">iusr_\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-128">iusr_\*</span></span> |<span data-ttu-id="89cd5-129">iusr_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="89cd5-129">iusr_ *machinename*</span></span> |
|<span data-ttu-id="89cd5-130">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-130">iwam\*</span></span>  |<span data-ttu-id="89cd5-131">IWAM_ *MachineName*</span><span class="sxs-lookup"><span data-stu-id="89cd5-131">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="89cd5-132">msol\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-132">msol\*</span></span> |<span data-ttu-id="89cd5-133">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="89cd5-133">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="89cd5-134">support_\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-134">support_\*</span></span> ||
|<span data-ttu-id="89cd5-135">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-135">SystemMailbox\*</span></span> |<span data-ttu-id="89cd5-136">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="89cd5-136">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="89cd5-137">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="89cd5-137">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="89cd5-138">distinguishedName contiene "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="89cd5-138">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="89cd5-139">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="89cd5-139">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="89cd5-140">El objeto contiene el atributo IsCriticalSystemObject</span><span class="sxs-lookup"><span data-stu-id="89cd5-140">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="89cd5-141">Consulte [atributos isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="89cd5-141">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="89cd5-142">Atributos y objetos dedicados multiinquilinos y dedicados comprobados por IdFix</span><span class="sxs-lookup"><span data-stu-id="89cd5-142">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="89cd5-143">Los atributos que IdFix comprueba para detectar errores se describen en la sección "preparación de objetos y atributos de directorio" en [preparar atributos de directorio para la sincronización con Office 365 mediante la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="89cd5-143">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

