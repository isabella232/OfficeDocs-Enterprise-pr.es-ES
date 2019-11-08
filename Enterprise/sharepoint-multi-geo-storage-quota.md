---
title: Cuotas de almacenamiento de SharePoint en entornos multigeográficos
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Obtenga información sobre las cuotas de almacenamiento de SharePoint en entornos multigeográficos.
ms.openlocfilehash: d4049312a2da64f16d2637ffd37adf98f2282287
ms.sourcegitcommit: fa900775790eb369db1983cd3868b628b699f145
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033386"
---
# <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a><span data-ttu-id="e140f-103">Cuotas de almacenamiento de SharePoint en entornos multigeográficos</span><span class="sxs-lookup"><span data-stu-id="e140f-103">SharePoint storage quotas in multi-geo environments</span></span>

<span data-ttu-id="e140f-104">De forma predeterminada, todas las ubicaciones geográficas de un entorno multigeográfico comparten la cuota de almacenamiento del espacio empresarial disponible.</span><span class="sxs-lookup"><span data-stu-id="e140f-104">By default, all geo locations of a multi-geo environment share the available tenant storage quota.</span></span>

<span data-ttu-id="e140f-105">Con la configuración de cuota de almacenamiento de SharePoint geográfica, puede administrar la cuota de almacenamiento para cada ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="e140f-105">With the SharePoint geo storage quota setting, you can manage the storage quota for each geo location.</span></span> <span data-ttu-id="e140f-106">Al asignar una cuota de almacenamiento de una ubicación geográfica, esta se convierte en la cantidad máxima de almacenamiento disponible para esa ubicación geográfica y se resta de la cuota de almacenamiento disponible por espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="e140f-106">When you allocate a storage quota for a geo location, it becomes the maximum amount of storage available for that geo location, and is deducted from the available tenant storage quota.</span></span> <span data-ttu-id="e140f-107">Luego, la cuota de almacenamiento disponible por espacio empresarial restante se comparte entre las ubicaciones geográficas configuradas a las que no se ha asignado una cuota de almacenamiento.</span><span class="sxs-lookup"><span data-stu-id="e140f-107">The remaining available tenant storage quota is then shared across the configured geo locations for which a specific storage quota has not been allocated.</span></span>

<span data-ttu-id="e140f-108">La cuota de almacenamiento de SharePoint para cualquier ubicación geográfica puede asignarse por el administrador de SharePoint Online mediante la conexión a la ubicación central.</span><span class="sxs-lookup"><span data-stu-id="e140f-108">The SharePoint storage quota for any geo location can be allocated by the SharePoint Online administrator by connecting to the central location.</span></span> <span data-ttu-id="e140f-109">Los administradores geográficos de ubicaciones satélites pueden ver la cuota de almacenamiento, pero no pueden asignarlas.</span><span class="sxs-lookup"><span data-stu-id="e140f-109">Geo administrators for satellite locations can view the storage quota but cannot allocate it.</span></span>

## <a name="configure-a-storage-quota-for-a-geo-location"></a><span data-ttu-id="e140f-110">Configurar una cuota de almacenamiento de una ubicación geográfica</span><span class="sxs-lookup"><span data-stu-id="e140f-110">Configure a storage quota for a geo location</span></span>

<span data-ttu-id="e140f-111">Use el [módulo de Microsoft Office SharePoint Online](https://www.microsoft.com/download/details.aspx?id=35588 ) y conéctese a la ubicación central para asignar la cuota de almacenamiento de una ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="e140f-111">Use the [Microsoft SharePoint Online Module](https://www.microsoft.com/download/details.aspx?id=35588 ) and connect to the central location to allocate the storage quota for a geo location.</span></span> 

<span data-ttu-id="e140f-112">Para asignar la cuota de almacenamiento de una ubicación, ejecute el cmdlet:</span><span class="sxs-lookup"><span data-stu-id="e140f-112">To allocate Storage Quota for a location, run cmdlet:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>`

<span data-ttu-id="e140f-113">Para ver la cuota de almacenamiento de la ubicación geográfica actual, ejecute:</span><span class="sxs-lookup"><span data-stu-id="e140f-113">To view Storage Quota for the current geo location, run:</span></span>

`Get-SPOGeoStorageQuota`

![Ventana de captura de pantalla de PowerShell que muestra el cmdlet Get-SPOGeoStorageQuota](media/multi-geo-storage-quota.png)

<span data-ttu-id="e140f-115">Para ver la cuota de almacenamiento de todas las ubicaciones geográficas, ejecute:</span><span class="sxs-lookup"><span data-stu-id="e140f-115">To view Storage Quota for all geo locations, run:</span></span>

`Get-SPOGeoStorageQuota -AllLocations`

<span data-ttu-id="e140f-116">Para quitar la cuota de almacenamiento asignada a una ubicación geográfica, establezca `StorageQuota value = 0`:</span><span class="sxs-lookup"><span data-stu-id="e140f-116">To remove the allocated storage quota for a geo location, set `StorageQuota value = 0`:</span></span>

`Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0`
