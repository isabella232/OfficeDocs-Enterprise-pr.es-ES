---
title: Configurar eDiscovery para Microsoft 365 Multi-Geo
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
localization_priority: Normal
ms.collection: Strat_SP_gtc
description: Obtenga información sobre cómo configurar eDiscovery de Microsoft 365 Multi-Geo.
ms.openlocfilehash: 7257e5e9a5a7154d574743e3e515e49e9dc714b2
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433831"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a><span data-ttu-id="c64b4-103">Configuración de eDiscovery de Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="c64b4-103">Microsoft 365 Multi-Geo eDiscovery configuration</span></span>

<span data-ttu-id="c64b4-p101">De forma predeterminada, un administrador o un supervisor de eDiscovery de un inquilino multigeográfico solo podrán ejecutar eDiscovery en la ubicación central de ese espacio empresarial. Para que se pueda ejecutar eDiscovery en ubicaciones por satélite, hay un nuevo parámetro de filtro de seguridad de cumplimiento llamado "Región" disponible mediante PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c64b4-p101">By default, an eDiscovery Manager or Administrator of a multi-geo tenant will be able to conduct eDiscovery only in the central location of that tenant. To support the ability to conduct eDiscovery for satellite locations, a new Compliance Security Filter parameter called "Region" is available via PowerShell.</span></span>

<span data-ttu-id="c64b4-106">El administrador global de Microsoft 365 debe asignar permisos de supervisor de eDiscovery para que otros usuarios puedan ejecutar eDiscovery y asignar un parámetro "Región" en el filtro de seguridad de cumplimiento correspondiente para especificar la región donde se ejecutará eDiscovery como ubicación por satélite; en caso contrario, no se ejecutará eDiscovery en la ubicación por satélite.</span><span class="sxs-lookup"><span data-stu-id="c64b4-106">The Microsoft 365 global administrator must assign eDiscovery Manager permissions to allow others to perform eDiscovery and assign a "Region" parameter in their applicable Compliance Security Filter to specify the region for conducting eDiscovery as satellite location, otherwise no eDiscovery will be carried out for the satellite location.</span></span>

<span data-ttu-id="c64b4-p102">Cuando se establece el rol Administrador o Supervisor de eDiscovery para una ubicación satélite concreta, el administrador o supervisor de eDiscovery solo podrán realizar acciones de búsqueda de eDiscovery en sitios de SharePoint y OneDrive situados en esa ubicación satélite. Si un administrador o supervisor de eDiscovery intenta realizar búsquedas en sitios de SharePoint o OneDrive fuera de la ubicación satélite especificada, no se devolverá ningún resultado. Además, cuando el administrador o supervisor de eDiscovery de una ubicación satélite desencadena una exportación, los datos se exportan a la instancia de Azure de esa región. Esto ayuda a las organizaciones a mantener el cumplimiento al no permitir que el contenido se exporte a través de fronteras controladas.</span><span class="sxs-lookup"><span data-stu-id="c64b4-p102">When the eDiscovery Manager or Administrator role is set for a particular satellite location, the eDiscovery Manager or Administrator will only be able to perform eDiscovery search actions against the SharePoint sites and OneDrive sites located in that satellite location. If an eDiscovery Manager or Administrator attempts to search SharePoint or OneDrive sites outside the specified satellite location, no results will be returned. Also, when the eDiscovery Manager or Administrator for a satellite location triggers an export, data is exported to the Azure instance of that region. This helps organizations stay in compliance by not allowing content to be exported across controlled borders.</span></span>

> [!NOTE]
> <span data-ttu-id="c64b4-111">Si es necesario que un supervisor de eDiscovery realice búsquedas en varias ubicaciones satélite de SharePoint, habrá que crear otra cuenta para el supervisor de eDiscovery que especifique la ubicación satélite alternativa donde se encuentran los sitios de OneDrive o SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c64b4-111">If it's necessary for an eDiscovery Manager to search across multiple SharePoint satellite locations, another user account will need to be created for the eDiscovery Manager which specifies the alternate satellite location where the OneDrive or SharePoint sites are located.</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

<span data-ttu-id="c64b4-112">Para establecer el filtro de seguridad de cumplimiento para una región:</span><span class="sxs-lookup"><span data-stu-id="c64b4-112">To set the Compliance Security Filter for a Region:</span></span>

1. <span data-ttu-id="c64b4-113">[Conéctese a PowerShell del Centro de seguridad y cumplimiento de Microsoft 365](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).</span><span class="sxs-lookup"><span data-stu-id="c64b4-113">[Connect to Microsoft 365 Security & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell)</span></span>

2. <span data-ttu-id="c64b4-114">Use la sintaxis que se muestre a continuación:</span><span class="sxs-lookup"><span data-stu-id="c64b4-114">Use the following syntax:</span></span>

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   <span data-ttu-id="c64b4-115">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c64b4-115">For example:</span></span>

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

<span data-ttu-id="c64b4-116">Vea el articulo [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/new-compliancesecurityfilter) para obtener más parámetros y sintaxis.</span><span class="sxs-lookup"><span data-stu-id="c64b4-116">See the [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/new-compliancesecurityfilter) article for additional parameters and syntax.</span></span>
