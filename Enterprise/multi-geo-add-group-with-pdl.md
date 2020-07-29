---
title: Crear un grupo de 365 de Microsoft con un PDL específico
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
localization_priority: Normal
description: Obtenga información sobre cómo crear un grupo de Microsoft 365 con una ubicación de datos preferida especificada en un entorno multigeográfico.
ms.openlocfilehash: bcababe39035550be445f2eee4d8121a2983132f
ms.sourcegitcommit: aac21bb1a7c1dfc3ba76a2db883e0457037c5667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "45433861"
---
# <a name="create-a-microsoft-365-group-with-a-specific-pdl"></a><span data-ttu-id="2e869-103">Crear un grupo de 365 de Microsoft con un PDL específico</span><span class="sxs-lookup"><span data-stu-id="2e869-103">Create a Microsoft 365 Group with a specific PDL</span></span>

<span data-ttu-id="2e869-104">Cuando los usuarios de un entorno multigeográfico crean un grupo de Microsoft 365, la ubicación de datos preferida del grupo se establece automáticamente en la del usuario.</span><span class="sxs-lookup"><span data-stu-id="2e869-104">When users in a multi-geo environment create a Microsoft 365 Group, the group preferred data location is automatically set to that of the user.</span></span> <span data-ttu-id="2e869-105">Los administradores globales, de SharePoint y de Exchange pueden crear grupos en cualquier región que seleccionen.</span><span class="sxs-lookup"><span data-stu-id="2e869-105">Global, SharePoint, and Exchange Administrators can create groups in any region they select.</span></span> 

<span data-ttu-id="2e869-106">Si necesita crear un grupo con un PDL específico, puede hacerlo desde el Centro de administración de SharePoint o a través del cmdlet New-UnifiedGroup de Exchange Online de Microsoft PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2e869-106">If you need to create a group with a specific PDL, you can do that using from the SharePoint admin center or through the Exchange Online New-UnifiedGroup Microsoft PowerShell cmdlet.</span></span> <span data-ttu-id="2e869-107">Al hacerlo, tanto el buzón del grupo como el sitio de SharePoint asociado con el grupo se aprovisionarán en el PDL especificado.</span><span class="sxs-lookup"><span data-stu-id="2e869-107">When you do this, both the group mailbox and SharePoint site associated with the group will be provisioned in the specified PDL.</span></span>

<span data-ttu-id="2e869-108">Para crear un grupo de 365 de Microsoft con el PDL que especifique, vaya al centro de administración de SharePoint en la ubicación geográfica en la que desea crear el sitio de grupo.</span><span class="sxs-lookup"><span data-stu-id="2e869-108">To create a Microsoft 365 Group with the PDL that you specify, go to the SharePoint admin center in the geo location where you want to create the group site.</span></span>

<span data-ttu-id="2e869-109">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="2e869-109">For example:</span></span>

<span data-ttu-id="2e869-110">Si desea crear un sitio de grupo en su ubicación de Australia, puede ir a https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span><span class="sxs-lookup"><span data-stu-id="2e869-110">If you want to create a group site in your Australia location, you can go to https://ContosoAUS-admin.sharepoint.com/_layouts/15/online/AdminHome.aspx#/siteManagement</span></span>

1. <span data-ttu-id="2e869-111">Seleccione **+ Crear**.</span><span class="sxs-lookup"><span data-stu-id="2e869-111">Select **+ Create**.</span></span>
2. <span data-ttu-id="2e869-112">Siga el proceso para crear un sitio de grupo.</span><span class="sxs-lookup"><span data-stu-id="2e869-112">Follow the process to create a group site.</span></span>

<span data-ttu-id="2e869-113">El sitio de grupo se aprovisionará en la ubicación geográfica correspondiente al Centro de administración de SharePoint desde el que haya iniciado la solicitud de creación de sitios.</span><span class="sxs-lookup"><span data-stu-id="2e869-113">Your group site will be provisioned in the geo location corresponding to the SharePoint admin center from which you initiated the site creation request.</span></span> 

<span data-ttu-id="2e869-114">Usar Exchange PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e869-114">Using Exchange PowerShell</span></span> 

<span data-ttu-id="2e869-115">Conéctese a Exchange Online PowerShell y pase el parámetro *-MailBoxRegion* con el código de ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="2e869-115">Connect to Exchange Online PowerShell and pass the parameter *-MailBoxRegion* with the geo location code.</span></span>

<span data-ttu-id="2e869-116">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="2e869-116">For example:</span></span> 

```PowerShell
New-UnifiedGroup -DisplayName MultiGeoEUR -Alias "MultiGeoEUR" -AccessType Public -MailboxRegion EUR 
```

![Captura de pantalla del cmdlet de PowerShell New-UnifiedGroup con la sintaxis](media/multi-geo-new-group-with-pdl-powershell.png)

<span data-ttu-id="2e869-118">Tenga en cuenta que el aprovisionamiento de sitios de grupo de SharePoint se realiza a petición.</span><span class="sxs-lookup"><span data-stu-id="2e869-118">Note that SharePoint group site provisioning is on-demand.</span></span> <span data-ttu-id="2e869-119">El sitio se aprovisionará la primera vez que un propietario o miembro del grupo intente acceder a él.</span><span class="sxs-lookup"><span data-stu-id="2e869-119">The site will be provisioned the first time a group owner or member attempts to access it.</span></span>

## <a name="geo-location-codes"></a><span data-ttu-id="2e869-120">Códigos de ubicación geográfica</span><span class="sxs-lookup"><span data-stu-id="2e869-120">Geo location codes</span></span>

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

## <a name="see-also"></a><span data-ttu-id="2e869-121">Vea también</span><span class="sxs-lookup"><span data-stu-id="2e869-121">See also</span></span>

[<span data-ttu-id="2e869-122">Conectarse a Exchange Online mediante PowerShell</span><span class="sxs-lookup"><span data-stu-id="2e869-122">Connect to Exchange Online PowerShell</span></span>](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell)
