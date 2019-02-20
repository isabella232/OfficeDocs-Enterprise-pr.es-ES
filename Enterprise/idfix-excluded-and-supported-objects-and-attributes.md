---
title: Objetos y atributos admitidos y excluidos en IdFix
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2016
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Enumera los atributos que se excluyen y son compatibles con la herramienta IdFix.
ms.openlocfilehash: d6b7aac023e9fe96b8308483322e718937ab1355
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085089"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="8720f-103">Objetos y atributos admitidos y excluidos en IdFix</span><span class="sxs-lookup"><span data-stu-id="8720f-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="8720f-p101">Hay dos conjuntos de reglas que mantiene IdFix: multiempresa y dedicado/ITAR. Por el momento, los dos conjuntos de reglas excluyen los mismos objetos, atributos y valores de atributos de la búsqueda. Esto puede cambiar en las próximas versiones.</span><span class="sxs-lookup"><span data-stu-id="8720f-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="8720f-107">Exclusiones de errores dedicados y multiempresa que usa IdFix</span><span class="sxs-lookup"><span data-stu-id="8720f-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="8720f-p102">En esta sección se enumeran los objetos, los atributos y los valores que se excluyen en IdFix de su búsqueda en el directorio. El asterisco (\*) es un carácter comodín que se puede sustituir por otros caracteres.</span><span class="sxs-lookup"><span data-stu-id="8720f-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="8720f-110">Objetos, atributos y valores excluidos durante una búsqueda de IdFix</span><span class="sxs-lookup"><span data-stu-id="8720f-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="8720f-111">**Exclusión**</span><span class="sxs-lookup"><span data-stu-id="8720f-111">**Exclusion**</span></span>|<span data-ttu-id="8720f-112">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="8720f-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="8720f-113">Elección\*</span><span class="sxs-lookup"><span data-stu-id="8720f-113">Admini\*</span></span> |<span data-ttu-id="8720f-114">Administrador</span><span class="sxs-lookup"><span data-stu-id="8720f-114">Administrator</span></span> |
|<span data-ttu-id="8720f-115">CAS_ {\*</span><span class="sxs-lookup"><span data-stu-id="8720f-115">CAS_{\*</span></span>  |<span data-ttu-id="8720f-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="8720f-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="8720f-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="8720f-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="8720f-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="8720f-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="8720f-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="8720f-119">FederatedEmail\*</span></span> |<span data-ttu-id="8720f-p103">FederatedEmail. *GUID*</span><span class="sxs-lookup"><span data-stu-id="8720f-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="8720f-122">"\*</span><span class="sxs-lookup"><span data-stu-id="8720f-122">Guest\*</span></span> ||
|<span data-ttu-id="8720f-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="8720f-123">HTTPConnector\*</span></span>  |<span data-ttu-id="8720f-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="8720f-124">HTTPConnector</span></span> |
|<span data-ttu-id="8720f-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="8720f-125">krbtgt\*</span></span> |<span data-ttu-id="8720f-126">MS-DS-KrbTgt-Link</span><span class="sxs-lookup"><span data-stu-id="8720f-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="8720f-127">cuenta\*</span><span class="sxs-lookup"><span data-stu-id="8720f-127">iusr_\*</span></span> |<span data-ttu-id="8720f-128">IUSR _ *nombreEquipo*</span><span class="sxs-lookup"><span data-stu-id="8720f-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="8720f-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="8720f-129">iwam\*</span></span>  |<span data-ttu-id="8720f-130">IWAM _ *nombreEquipo*</span><span class="sxs-lookup"><span data-stu-id="8720f-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="8720f-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="8720f-131">msol\*</span></span> |<span data-ttu-id="8720f-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="8720f-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="8720f-133">admisión\*</span><span class="sxs-lookup"><span data-stu-id="8720f-133">support_\*</span></span> ||
|<span data-ttu-id="8720f-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="8720f-134">SystemMailbox\*</span></span> |<span data-ttu-id="8720f-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="8720f-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="8720f-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="8720f-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="8720f-137">distinguishedName contiene "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="8720f-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="8720f-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="8720f-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="8720f-139">Object contains the IsCriticalSystemObject attribute</span><span class="sxs-lookup"><span data-stu-id="8720f-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="8720f-140">Consulte [atributos isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="8720f-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="8720f-141">Objetos y atributos multiempresa y dedicados que comprueba IdFix</span><span class="sxs-lookup"><span data-stu-id="8720f-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="8720f-142">Los atributos que IdFix comprueba para detectar errores se describen en la sección "preparación de objetos y atributos de directorio" en [preparar atributos de directorio para la sincronización con Office 365 mediante la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="8720f-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

