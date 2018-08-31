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
ms.assetid: cc453ae5-fa9b-4836-b0ce-c7e824b1e36d
description: Se enumeran los atributos que son compatibles con la herramienta IdFix y excluidos.
ms.openlocfilehash: de8d57bb8ad9a3097ec9da3ff2a485095a140a42
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542850"
---
# <a name="idfix-excluded-and-supported-objects-and-attributes"></a><span data-ttu-id="b1b61-103">Objetos y atributos admitidos y excluidos en IdFix</span><span class="sxs-lookup"><span data-stu-id="b1b61-103">IdFix excluded and supported objects and attributes</span></span>
<span data-ttu-id="b1b61-p101">Hay dos conjuntos de reglas que mantiene IdFix: multiempresa y dedicado/ITAR. Por el momento, los dos conjuntos de reglas excluyen los mismos objetos, atributos y valores de atributos de la búsqueda. Esto puede cambiar en las próximas versiones.</span><span class="sxs-lookup"><span data-stu-id="b1b61-p101">There are two sets of rules maintained by IdFix; Multi-tenant and Dedicated/ITAR. At this time, the two rule sets exclude the same objects, attributes, and attribute values from its search. This may change in future releases.</span></span>
  
## <a name="multi-tenant-and-dedicated-error-exclusions-used-by-idfix"></a><span data-ttu-id="b1b61-107">Exclusiones de errores dedicados y multiempresa que usa IdFix</span><span class="sxs-lookup"><span data-stu-id="b1b61-107">Multi-tenant and Dedicated error exclusions used by IdFix</span></span>
<span data-ttu-id="b1b61-p102">En esta sección se enumera los objetos, atributos y valores que IdFix se excluye de la búsqueda del directorio. El asterisco (\*) es un carácter comodín que se puede sustituir por otros caracteres.</span><span class="sxs-lookup"><span data-stu-id="b1b61-p102">This section lists the objects, attributes, and values that IdFix excludes from its search of the directory. The asterisk (\*) is a wildcard that can be substituted for other characters.</span></span>
  
### <a name="objects-attributes-and-values-excluded-during-an-idfix-search"></a><span data-ttu-id="b1b61-110">Objetos, atributos y valores excluidos durante una búsqueda de IdFix</span><span class="sxs-lookup"><span data-stu-id="b1b61-110">Objects, attributes, and values excluded during an IdFix search</span></span>

|<span data-ttu-id="b1b61-111">**Exclusión**</span><span class="sxs-lookup"><span data-stu-id="b1b61-111">**Exclusion**</span></span>|<span data-ttu-id="b1b61-112">**Ejemplo**</span><span class="sxs-lookup"><span data-stu-id="b1b61-112">**Example**</span></span>|
|:-----|:-----|
|<span data-ttu-id="b1b61-113">Derechos\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-113">Admini\*</span></span> |<span data-ttu-id="b1b61-114">Administrador</span><span class="sxs-lookup"><span data-stu-id="b1b61-114">Administrator</span></span> |
|<span data-ttu-id="b1b61-115">{CAS_\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-115">CAS_{\*</span></span>  |<span data-ttu-id="b1b61-116">CAS_{fe35fc98e69e4d08}</span><span class="sxs-lookup"><span data-stu-id="b1b61-116">CAS_{fe35fc98e69e4d08}</span></span> |
|<span data-ttu-id="b1b61-117">DiscoverySearchMailbox\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-117">DiscoverySearchMailbox\*</span></span>  |<span data-ttu-id="b1b61-118">DiscoverySearchMailbox</span><span class="sxs-lookup"><span data-stu-id="b1b61-118">DiscoverySearchMailbox</span></span>  |
|<span data-ttu-id="b1b61-119">FederatedEmail\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-119">FederatedEmail\*</span></span> |<span data-ttu-id="b1b61-p103">FederatedEmail. *GUID*</span><span class="sxs-lookup"><span data-stu-id="b1b61-p103">FederatedEmail. *GUID*</span></span> |
|<span data-ttu-id="b1b61-122">Invitado\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-122">Guest\*</span></span> ||
|<span data-ttu-id="b1b61-123">HTTPConnector\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-123">HTTPConnector\*</span></span>  |<span data-ttu-id="b1b61-124">HTTPConnector</span><span class="sxs-lookup"><span data-stu-id="b1b61-124">HTTPConnector</span></span> |
|<span data-ttu-id="b1b61-125">krbtgt\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-125">krbtgt\*</span></span> |<span data-ttu-id="b1b61-126">MS-DS-KrbTgt-vínculo</span><span class="sxs-lookup"><span data-stu-id="b1b61-126">ms-DS-KrbTgt-Link</span></span> |
|<span data-ttu-id="b1b61-127">IUSR_\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-127">iusr_\*</span></span> |<span data-ttu-id="b1b61-128">IUSR_ *nombreEquipo*</span><span class="sxs-lookup"><span data-stu-id="b1b61-128">iusr_ *machinename*</span></span> |
|<span data-ttu-id="b1b61-129">IWAM\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-129">iwam\*</span></span>  |<span data-ttu-id="b1b61-130">IWAM_ *nombreEquipo*</span><span class="sxs-lookup"><span data-stu-id="b1b61-130">IWAM_ *machinename*</span></span> |
|<span data-ttu-id="b1b61-131">msol\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-131">msol\*</span></span> |<span data-ttu-id="b1b61-132">MSOL_AD_SYNC</span><span class="sxs-lookup"><span data-stu-id="b1b61-132">MSOL_AD_SYNC</span></span> |
|<span data-ttu-id="b1b61-133">Support_\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-133">support_\*</span></span> ||
|<span data-ttu-id="b1b61-134">SystemMailbox\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-134">SystemMailbox\*</span></span> |<span data-ttu-id="b1b61-135">SystemMailbox { *GUID* }</span><span class="sxs-lookup"><span data-stu-id="b1b61-135">Systemmailbox{ *GUID*  }</span></span>|
|<span data-ttu-id="b1b61-136">WWIOadmini\*</span><span class="sxs-lookup"><span data-stu-id="b1b61-136">WWIOadmini\*</span></span>  ||
|\*$ ||
|<span data-ttu-id="b1b61-137">distinguishedName contiene "\0ACNF:"</span><span class="sxs-lookup"><span data-stu-id="b1b61-137">distinguishedName contains "\0ACNF:"</span></span>|<span data-ttu-id="b1b61-138">"\0ACNF: *GUID* "</span><span class="sxs-lookup"><span data-stu-id="b1b61-138">"\0ACNF: *GUID*  "</span></span> |
|<span data-ttu-id="b1b61-139">Object contains the IsCriticalSystemObject attribute</span><span class="sxs-lookup"><span data-stu-id="b1b61-139">Object contains the IsCriticalSystemObject attribute</span></span> |<span data-ttu-id="b1b61-140">Vea el [atributo isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span><span class="sxs-lookup"><span data-stu-id="b1b61-140">See [Attribute isCriticalSystemObject](https://go.microsoft.com/fwlink/p/?LinkId=401169).</span></span> |
   
## <a name="multi-tenant-and-dedicated-objects-and-attributes-checked-by-idfix"></a><span data-ttu-id="b1b61-141">Objetos y atributos multiempresa y dedicados que comprueba IdFix</span><span class="sxs-lookup"><span data-stu-id="b1b61-141">Multi-Tenant and Dedicated objects and attributes checked by IdFix</span></span>
<span data-ttu-id="b1b61-142">Se describen los atributos que se comprueban los errores de idfix en la sección "Objeto y atributo preparación de Active Directory" en [la preparación atributos de Active directory para la sincronización con Office 365 mediante el uso de la herramienta IdFix](prepare-directory-attributes-for-synch-with-idfix.md).</span><span class="sxs-lookup"><span data-stu-id="b1b61-142">The attributes that are checked for errors by IdFix are described in the section "Directory object and attribute preparation" in [Prepare directory attributes for synchronization with Office 365 by using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md).</span></span>
  

