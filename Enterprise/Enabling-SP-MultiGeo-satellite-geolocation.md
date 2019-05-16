---
title: Habilitar SharePoint Multi-Geo en su ubicación geográfica de satélite
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Habilitar SharePoint Multi-Geo en su ubicación geográfica de satélite.
ms.openlocfilehash: d1f18c22410ec98e6c27cf3d10cdaf05a5095036
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070766"
---
# <a name="enabling-sharepoint-multi-geo-in-your-satellite-geo-location"></a><span data-ttu-id="a9023-103">Habilitar SharePoint Multi-Geo en su ubicación geográfica de satélite</span><span class="sxs-lookup"><span data-stu-id="a9023-103">Enabling SharePoint Multi-Geo in your satellite geo location</span></span>

<span data-ttu-id="a9023-104">Este artículo es para los administradores globales o de SharePoint que crearon una ubicación de satélite multigeográfica **antes** de que las funcionalidades multigeográficas de SharePoint estuvieran disponibles el 27 de marzo de 2019 y que no hayan habilitado SharePoint Multi-Geo en sus ubicaciones geográficas de satélite.</span><span class="sxs-lookup"><span data-stu-id="a9023-104">This article is for Global or SharePoint administrators who have created a Multi-Geo satellite location **before** SharePoint Multi-Geo capabilities became generally available on March 27, 2019, and who have not enabled SharePoint Multi-Geo in their satellite geo location(s).</span></span> 

>[!Note]
><span data-ttu-id="a9023-105">Si ha agregado una nueva ubicación geográfica **después el 27 de marzo**, no es necesario realizar estas acciones, ya que la nueva ubicación geográfica ya estará habilitada para OneDrive y SharePoint Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="a9023-105">If you have added a new geo location **after March 27th**, you do not need to perform these instructions, as your new geo location will already be enabled for OneDrive and SharePoint Multi-Geo.</span></span>

<span data-ttu-id="a9023-106">Estas instrucciones le permitirán habilitar SharePoint en la ubicación de satélite, por lo que los usuarios del satélite multigeográfico pueden aprovechar las funcionalidades de OneDrive y SharePoint Multi-Geo en Office 365.</span><span class="sxs-lookup"><span data-stu-id="a9023-106">These instructions will allow you to enable SharePoint in your satellite location, so your Multi-Geo satellite users can take advantage of both OneDrive and SharePoint Multi-Geo capabilities in O365.</span></span> 

>[!IMPORTANT]
><span data-ttu-id="a9023-107">Tenga en cuenta que esta es una activación unidireccional.</span><span class="sxs-lookup"><span data-stu-id="a9023-107">Please note that this is a one way enablement.</span></span> <span data-ttu-id="a9023-108">Una vez que establezca el modo SPO, no podrá revertir el inquilino al modo de solo OneDrive Multi-Geo sin consultar con el soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="a9023-108">Once you set SPO mode, you will not be able to revert your tenant to OneDrive only Multi-Geo mode without an escalation with support.</span></span> 

## <a name="to-set-a-geo-location-into-spo-mode"></a><span data-ttu-id="a9023-109">Establecer una ubicación geográfica en modo SPO</span><span class="sxs-lookup"><span data-stu-id="a9023-109">To set a geo location into SPO Mode</span></span>

<span data-ttu-id="a9023-110">Para establecer una ubicación geográfica en modo SPO, conéctese a la ubicación geográfica que desea establecer en modo de SPO:</span><span class="sxs-lookup"><span data-stu-id="a9023-110">To set a geo location into SPO mode, connect to the geo location you want to set in SPO Mode:</span></span>

1.  <span data-ttu-id="a9023-111">Abra el Shell de administración de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="a9023-111">Open your SharePoint Online Management Shell</span></span> 
2.  <span data-ttu-id="a9023-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span><span class="sxs-lookup"><span data-stu-id="a9023-112">Connect-SPOService -URL "https://$tenantGeo-admin.sharepoint.com" -Credential $credential</span></span>
3.  <span data-ttu-id="a9023-113">Set-SPOMultiGeoExperience</span><span class="sxs-lookup"><span data-stu-id="a9023-113">Set-SPOMultiGeoExperience</span></span></br></br>
<span data-ttu-id="a9023-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="a9023-114">![Set-SPOMultiGeoExperience](media/Set-SPO-MultiGeo.jpg)</span></span>
4.  <span data-ttu-id="a9023-115">Esta operación suele tardar aproximadamente una hora mientras se realizan varias acciones en el servicio y se vuelve a marcar el inquilino.</span><span class="sxs-lookup"><span data-stu-id="a9023-115">This operation usually takes about an hour while we perform various publish backs in the service and re-stamp your tenant.</span></span> <span data-ttu-id="a9023-116">Después de al menos una hora, lleve a cabo un Get-SPOMultiGeoExperience.</span><span class="sxs-lookup"><span data-stu-id="a9023-116">After at least 1 hour, please perform a Get-SPOMultiGeoExperience.</span></span>  <span data-ttu-id="a9023-117">Esto le mostrará si esta ubicación geográfica está en modo SPO.</span><span class="sxs-lookup"><span data-stu-id="a9023-117">This will show you whether this geo location is in SPO mode.</span></span></br></br>
<span data-ttu-id="a9023-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span><span class="sxs-lookup"><span data-stu-id="a9023-118">![Set-SPOMultiGeoExperience](media/Get-SPO-MultiGeo.jpg)</span></span>

 
 
 
>[!Note]
><span data-ttu-id="a9023-119">Algunas memorias caché del servicio se actualizan cada 24 horas, por lo que es posible que, durante un período de hasta 24 horas, la ubicación geográfica de su satélite se comporte de manera intermitente, como si estuviese todavía en modo ODB.</span><span class="sxs-lookup"><span data-stu-id="a9023-119">Certain caches in the service update every 24 hours, so it is possible that for a period of up to 24 hours, your satellite geo may intermittently behave as if it was still in ODB mode.</span></span> <span data-ttu-id="a9023-120">Esto no causa problemas técnicos.</span><span class="sxs-lookup"><span data-stu-id="a9023-120">This does not cause any technical issues.</span></span> 
 
<span data-ttu-id="a9023-121">Para obtener más información sobre SharePoint Multi-Geo, consulte [aka.ms/sharepointmultigeo](https://docs.microsoft.com/es-ES/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span><span class="sxs-lookup"><span data-stu-id="a9023-121">For additional information regarding SharePoint Multi-Geo, please refer to [aka.ms/sharepointmultigeo](https://docs.microsoft.com/en-us/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)</span></span>


