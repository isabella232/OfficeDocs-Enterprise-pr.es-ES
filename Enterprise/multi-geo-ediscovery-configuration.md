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
ms.custom: seo-marvel-apr2020
localization_priority: Normal
ms.collection: Strat_SP_gtc
description: Obtenga información sobre cómo usar el parámetro region para configurar eDiscovery para su uso en ubicaciones de satélite en Microsoft 365 multigeográfico.
ms.openlocfilehash: dec73aef93951bd86f2b84c4eba637bac725603a
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606806"
---
# <a name="microsoft-365-multi-geo-ediscovery-configuration"></a>Configuración de eDiscovery de Microsoft 365 Multi-Geo

De forma predeterminada, un administrador o un supervisor de eDiscovery de un inquilino multigeográfico solo podrán ejecutar eDiscovery en la ubicación central de ese espacio empresarial. Para que se pueda ejecutar eDiscovery en ubicaciones por satélite, hay un nuevo parámetro de filtro de seguridad de cumplimiento llamado "Región" disponible mediante PowerShell.

El administrador global de Microsoft 365 debe asignar permisos de supervisor de eDiscovery para que otros usuarios puedan ejecutar eDiscovery y asignar un parámetro "Región" en el filtro de seguridad de cumplimiento correspondiente para especificar la región donde se ejecutará eDiscovery como ubicación por satélite; en caso contrario, no se ejecutará eDiscovery en la ubicación por satélite.

Cuando se establece el rol Administrador o Supervisor de eDiscovery para una ubicación satélite concreta, el administrador o supervisor de eDiscovery solo podrán realizar acciones de búsqueda de eDiscovery en sitios de SharePoint y OneDrive situados en esa ubicación satélite. Si un administrador o supervisor de eDiscovery intenta realizar búsquedas en sitios de SharePoint o OneDrive fuera de la ubicación satélite especificada, no se devolverá ningún resultado. Además, cuando el administrador o supervisor de eDiscovery de una ubicación satélite desencadena una exportación, los datos se exportan a la instancia de Azure de esa región. Esto ayuda a las organizaciones a mantener el cumplimiento al no permitir que el contenido se exporte a través de fronteras controladas.

> [!NOTE]
> Si es necesario que un supervisor de eDiscovery realice búsquedas en varias ubicaciones satélite de SharePoint, habrá que crear otra cuenta para el supervisor de eDiscovery que especifique la ubicación satélite alternativa donde se encuentran los sitios de OneDrive o SharePoint.

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

Para establecer el filtro de seguridad de cumplimiento para una región:

1. [Conéctese a PowerShell del Centro de seguridad y cumplimiento de Microsoft 365](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Use la sintaxis que se muestre a continuación:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName <TheNameYouWantToAssign> -Region <RegionValue> -Users <UserPrincipalName>
   ```

   Por ejemplo:

   ```powershell
   New-ComplianceSecurityFilter -Action All -FilterName "NAM eDiscovery Managers" -Region NAM -Users adwood@contoso.onmicrosoft.com
   ```

Vea el articulo [New-ComplianceSecurityFilter](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-content-search/new-compliancesecurityfilter) para obtener más parámetros y sintaxis.
