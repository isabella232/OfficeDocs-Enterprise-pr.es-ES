---
title: Agregar o quitar un administrador de geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtenga información sobre cómo agregar o quitar un administrador ubican en OneDrive para profesionales Multi-ubican.
ms.openlocfilehash: 7630597654df9ad78619b94fedc9e18d5b0b721e
ms.sourcegitcommit: 886b23f590f6187f7a98c1083a3b49359ec2a5c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2018
---
# <a name="add-or-remove-a-geo-administrator-in-onedrive-for-busniess-multi-geo"></a><span data-ttu-id="e8015-103">Agregar o quitar un administrador ubican en OneDrive para Busniess Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="e8015-103">Add or remove a geo administrator in OneDrive for Busniess Multi-Geo</span></span>

<span data-ttu-id="e8015-p101">Puede configurar administradores independientes para cada ubicación geográfica que tienen en el inquilino de. Estos administradores tendrán acceso a la configuración de SharePoint Online y OneDrive que son específicos de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="e8015-p101">You can configure separate administrators for each geo location that you have in your tenant. These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo-location.</span></span>

<span data-ttu-id="e8015-p102">Algunos servicios - como el almacén de términos - se administran desde la ubicación central y se replican en ubicaciones de satélite. El Administrador de geo para la ubicación central tiene acceso a estas, mientras que los administradores geo para las ubicaciones de satélite no.</span><span class="sxs-lookup"><span data-stu-id="e8015-p102">Some services - such as the term store - are administered from the central location and replicated to satellite locations. The geo admin for the central location has access to these, whereas geo admins for satellite locations don’t.</span></span>

<span data-ttu-id="e8015-108">Los administradores globales y los administradores de SharePoint Online sigan teniendo acceso a la configuración en todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="e8015-108">Global administrators and SharePoint Online administrators continue to have access to settings in all geo locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="e8015-109">Configuración de los administradores de geo</span><span class="sxs-lookup"><span data-stu-id="e8015-109">Configuring geo administrators</span></span>

<span data-ttu-id="e8015-110">Configurar administradores ubican requiere el módulo de PowerShell en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="e8015-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="e8015-111">Utilizar [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectar con el centro de administración de la ubicación geográfica donde desea agregar el administrador ubican. (Por ejemplo, Connect-SPOServicehttps://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="e8015-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="e8015-112">Para ver los administradores ubican existente de una ubicación, ejecute`Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="e8015-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="e8015-113">Adición de un usuario como un administrador de geo</span><span class="sxs-lookup"><span data-stu-id="e8015-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="e8015-114">Para agregar un usuario como un administrador de geo, ejecute`Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="e8015-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="e8015-115">Para quitar un usuario como un administrador de Geo de una ubicación, ejecute`Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="e8015-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="e8015-116">Adición de un grupo como un administrador de geo</span><span class="sxs-lookup"><span data-stu-id="e8015-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="e8015-117">Puede agregar un grupo de seguridad o un grupo de seguridad habilitados para correo como un administrador ubican. (No se admiten grupos de distribución y grupos de Office 365.)</span><span class="sxs-lookup"><span data-stu-id="e8015-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="e8015-118">Para agregar un grupo como un administrador de geo, ejecute`Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="e8015-118">To add a group as a geo admin, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="e8015-119">Para quitar un grupo como un administrador de geo, ejecute`Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="e8015-119">To remove a group as a geo admin, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="e8015-p103">Tenga en cuenta que no todos los grupos de seguridad tienen un alias de grupo. Si desea agregar un grupo de seguridad que no tiene un alias, ejecute [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) para recuperar una lista de grupos, busque ObjectID de su grupo de seguridad y, a continuación, ejecute:</span><span class="sxs-lookup"><span data-stu-id="e8015-p103">Note that not all security groups have a group alias. If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/en-us/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="e8015-122">Para quitar un grupo mediante el uso de ObjectID, ejecute`Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="e8015-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="e8015-123">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e8015-123">See Also</span></span>

[<span data-ttu-id="e8015-124">SPOGeoAdministrator agregar</span><span class="sxs-lookup"><span data-stu-id="e8015-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="e8015-125">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="e8015-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="e8015-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="e8015-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="e8015-127">Establecer un alias (MailNickName) para un grupo de seguridad</span><span class="sxs-lookup"><span data-stu-id="e8015-127">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/en-us/powershell/module/azuread/set-azureadgroup)