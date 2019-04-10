---
title: Agregar o quitar un administrador geográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
description: Aprenda a agregar o quitar un administrador geográfico de Office 365 Multi-Geo.
ms.openlocfilehash: 28af776f3afe4e3cc666817eb2d5faff846aa1af
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931669"
---
# <a name="add-or-remove-a-geo-administrator-in-office-365-multi-geo"></a><span data-ttu-id="67958-103">Agregar o quitar un administrador geográfico de Office 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="67958-103">Add or remove a geo administrator in Office 365 Multi-Geo</span></span>

<span data-ttu-id="67958-104">Puede configurar administradores independientes para cada ubicación geográfica de su espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="67958-104">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="67958-105">Estos administradores tendrán acceso a la configuración de SharePoint Online y OneDrive específica de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="67958-105">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="67958-106">Algunos servicios, como el almacén de términos, se administran desde la ubicación central y se replican en ubicaciones satélites.</span><span class="sxs-lookup"><span data-stu-id="67958-106">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="67958-107">El administrador geográfico de la ubicación central tiene acceso a dichos servicios, pero los administradores geográficos de ubicaciones satélites no.</span><span class="sxs-lookup"><span data-stu-id="67958-107">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="67958-108">Los administradores globales y administradores de SharePoint Online seguirán teniendo acceso a la configuración de la ubicación central y todas las ubicaciones satélites.</span><span class="sxs-lookup"><span data-stu-id="67958-108">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="67958-109">Configurar los administradores geográficos</span><span class="sxs-lookup"><span data-stu-id="67958-109">Configuring geo administrators</span></span>

<span data-ttu-id="67958-110">Para configurar los administradores geográficos se requiere el módulo de PowerShell de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="67958-110">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="67958-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectarse al centro de administración de la ubicación geográfica donde quiera agregar el administrador geográfico. (Por ejemplo, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="67958-111">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="67958-112">Para ver los administradores geográficos existentes de una ubicación, ejecute `Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="67958-112">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="67958-113">Agregar un usuario como administrador geográfico</span><span class="sxs-lookup"><span data-stu-id="67958-113">Adding a user as a geo admin</span></span>

<span data-ttu-id="67958-114">Para agregar un usuario como administrador geográfico, ejecute `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="67958-114">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="67958-115">Para quitar un usuario como administrador geográfico de una ubicación, ejecute  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="67958-115">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="67958-116">Agregar un grupo como administrador geográfico</span><span class="sxs-lookup"><span data-stu-id="67958-116">Adding a group as a geo admin</span></span>

<span data-ttu-id="67958-117">Puede agregar un grupo de seguridad o un grupo de seguridad habilitado para correo como administrador geográfico. (Los grupos de distribución y Grupos de Office 365 no son compatibles).</span><span class="sxs-lookup"><span data-stu-id="67958-117">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Office 365 Groups are not supported.)</span></span>

<span data-ttu-id="67958-118">Para agregar un grupo como administrador geográfico, ejecute `Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="67958-118">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="67958-119">Para quitar un grupo como administrador geográfico, ejecute `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="67958-119">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="67958-120">Tenga en cuenta que no todos los grupos de seguridad tienen un alias de grupo.</span><span class="sxs-lookup"><span data-stu-id="67958-120">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="67958-121">Si quiere agregar un grupo de seguridad que no tiene un alias, ejecute [Get-MsolGroup](https://docs.microsoft.com/es-ES/powershell/module/msonline/get-msolgroup) para recuperar una lista de grupos, busque el ObjectID del grupo seguridad y ejecute lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="67958-121">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/es-ES/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="67958-122">Para quitar un grupo mediante ObjectID, ejecute `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="67958-122">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="see-also"></a><span data-ttu-id="67958-123">Vea también</span><span class="sxs-lookup"><span data-stu-id="67958-123">See Also</span></span>

[<span data-ttu-id="67958-124">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="67958-124">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="67958-125">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="67958-125">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="67958-126">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="67958-126">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="67958-127">Establecer un alias (MailNickName) de un grupo de seguridad</span><span class="sxs-lookup"><span data-stu-id="67958-127">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/es-ES/powershell/module/azuread/set-azureadgroup)