---
title: Crear un grupo de Microsoft 365 con un PDL específico
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
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información sobre cómo crear un grupo de Microsoft 365 con una ubicación de datos preferida especificada en un entorno multigeográfico.
ms.openlocfilehash: 5b2294ff8821e84cb0158fa989b97134353969b2
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057990"
---
# <a name="create-an-microsoft-365-group-with-a-specific-pdl"></a><span data-ttu-id="df99e-103">Crear un grupo de Microsoft 365 con un PDL específico</span><span class="sxs-lookup"><span data-stu-id="df99e-103">Create an Microsoft 365 Group with a specific PDL</span></span>

<span data-ttu-id="df99e-104">Cuando los usuarios en un entorno multigeográfico crean un grupo de Microsoft 365, la ubicación de datos preferida del grupo se establece automáticamente según la del usuario.</span><span class="sxs-lookup"><span data-stu-id="df99e-104">When users in a multi-geo environment create an Microsoft 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="df99e-105">Los administradores globales, de SharePoint y de Exchange pueden crear grupos en cualquier región que seleccionen.</span><span class="sxs-lookup"><span data-stu-id="df99e-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="df99e-106">Si necesita crear un grupo con un PDL específico, puede hacerlo desde el Centro de administración de SharePoint o a través del cmdlet New-UnifiedGroup de Exchange Online de Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df99e-106">If you need to create a group with a specific PDL, you can do that using from the SharePoint admin center or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="df99e-107">Al hacerlo, tanto el buzón del grupo como el sitio de SharePoint asociado con el grupo se aprovisionarán en el PDL especificado.</span><span class="sxs-lookup"><span data-stu-id="df99e-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="df99e-108">Para crear un grupo de Microsoft 365 con la PDL que designe, vaya al Centro de administración de SharePoint en la ubicación geográfica donde desea crear el sitio del grupo.</span><span class="sxs-lookup"><span data-stu-id="df99e-108">To create an Microsoft 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="df99e-109">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="df99e-109">For example:</span></span>

<span data-ttu-id="df99e-110">Si desea crear un sitio de grupo en su ubicación de Australia, puede ir a https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span><span class="sxs-lookup"><span data-stu-id="df99e-110">If you want to create a group site in your Australia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="df99e-111">Seleccione **+ Crear**.</span><span class="sxs-lookup"><span data-stu-id="df99e-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="df99e-112">Siga el proceso para crear un sitio de grupo.</span><span class="sxs-lookup"><span data-stu-id="df99e-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="df99e-113">El sitio de grupo se aprovisionará en la ubicación geográfica correspondiente al Centro de administración de SharePoint desde el que haya iniciado la solicitud de creación de sitios.</span><span class="sxs-lookup"><span data-stu-id="df99e-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="df99e-114">Usar Exchange PowerShell</span><span class="sxs-lookup"><span data-stu-id="df99e-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="df99e-115">Conéctese a Exchange Online PowerShell y pase el parámetro *-MailBoxRegion* con el código de ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="df99e-115">Connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="df99e-116">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="df99e-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Captura de pantalla del cmdlet de PowerShell New-UnifiedGroup con la sintaxis](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="df99e-118">Tenga en cuenta que el aprovisionamiento de sitios de grupo de SharePoint se realiza a petición.</span><span class="sxs-lookup"><span data-stu-id="df99e-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="df99e-119">El sitio se aprovisionará la primera vez que un propietario o miembro del grupo intente acceder a él.</span><span class="sxs-lookup"><span data-stu-id="df99e-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="df99e-120">Códigos de ubicación geográfica</span><span class="sxs-lookup"><span data-stu-id="df99e-120">Geo location codes</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="df99e-121">Vea también</span><span class="sxs-lookup"><span data-stu-id="df99e-121">See also</span></span>

[<span data-ttu-id="df99e-122">Conectarse a Exchange Online mediante PowerShell</span><span class="sxs-lookup"><span data-stu-id="df99e-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
