---
title: Agregar o quitar un administrador de geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Aprenda a agregar o quitar un administrador geo en OneDrive para el negocio Multi-Geo.
ms.openlocfilehash: 0007f1ac3c73fa7a2ada562f8da65215f80744ca
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="64179-103">Agregar o quitar un administrador geo en OneDrive de Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="64179-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="64179-p101">Puede configurar administradores independientes para cada ubicación geográfica que tiene en su arrendatario. Estos administradores tendrán acceso a la configuración de SharePoint Online y OneDrive son específicos de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="64179-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="64179-p102">Algunos servicios - como el almacén de términos - se administran desde la ubicación central y se replican en ubicaciones de satélite. El admin geo para la ubicación central tiene acceso a estos, mientras que los no administradores geo para ubicaciones de satélite.</span><span class="sxs-lookup"><span data-stu-id="64179-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="64179-108">Los administradores globales y los administradores de SharePoint Online sigan teniendo acceso a la configuración en todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="64179-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="64179-109">Configurar administradores de geo</span><span class="sxs-lookup"><span data-stu-id="64179-109">Configuring geo administrators</span></span>

<span data-ttu-id="64179-110">Configurar administradores de geo requiere el módulo de PowerShell de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="64179-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="64179-111">Utilizar [SPOService de conectar](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectarse al centro de administración de la ubicación geográfica donde desee agregar el administrador geo. (Por ejemplo, conectar SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="64179-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="64179-112">Para agregar un usuario como un administrador de geo, ejecutar`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="64179-112">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="64179-113">Para ver los administradores geo existente de una ubicación, ejecutar`Get-SPOGeoAdministrators`</span><span class="sxs-lookup"><span data-stu-id="64179-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrators`</span></span>

<span data-ttu-id="64179-114">Para quitar un usuario como administradores de una ubicación geográfica, ejecute`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="64179-114">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

## <a name="see-also"></a><span data-ttu-id="64179-115">Consulte también</span><span class="sxs-lookup"><span data-stu-id="64179-115">See Also</span></span>

[<span data-ttu-id="64179-116">SPOGeoAdministrator agregar</span><span class="sxs-lookup"><span data-stu-id="64179-116">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="64179-117">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="64179-117">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="64179-118">Quitar SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="64179-118">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)