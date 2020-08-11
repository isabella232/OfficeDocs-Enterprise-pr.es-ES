---
title: Agregar o quitar un administrador geográfico
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: SPO_Content
localization_priority: Normal
f1.keywords:
- NOCSH
description: ¿Necesita configurar administradores independientes para cada ubicación geográfica? Obtenga más información sobre cómo agregar o quitar un administrador geográfico de Microsoft 365 Multi-Geo.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: b69ff352ae0e5ceb55200e0ed034e278808cdc9f
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605826"
---
# <a name="add-or-remove-a-geo-administrator-in-microsoft-365-multi-geo"></a><span data-ttu-id="47102-104">Agregar o quitar un administrador geográfico de Microsoft 365 Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="47102-104">Add or remove a geo administrator in Microsoft 365 Multi-Geo</span></span>

<span data-ttu-id="47102-105">Puede configurar administradores independientes para cada ubicación geográfica de su espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="47102-105">You can configure separate administrators for each geo location that you have in your tenant.</span></span> <span data-ttu-id="47102-106">Estos administradores tendrán acceso a la configuración de SharePoint Online y OneDrive específica de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="47102-106">These administrators will have access to the SharePoint Online and OneDrive settings that are specific to their geo location.</span></span>

<span data-ttu-id="47102-107">Algunos servicios, como el almacén de términos, se administran desde la ubicación central y se replican en ubicaciones satélites.</span><span class="sxs-lookup"><span data-stu-id="47102-107">Some services - such as the term store - are administered from the central location and replicated to satellite locations.</span></span> <span data-ttu-id="47102-108">El administrador geográfico de la ubicación central tiene acceso a dichos servicios, pero los administradores geográficos de ubicaciones satélites no.</span><span class="sxs-lookup"><span data-stu-id="47102-108">The geo admin for the central location has access to these, whereas geo admins for satellite locations don't.</span></span>

<span data-ttu-id="47102-109">Los administradores globales y administradores de SharePoint Online seguirán teniendo acceso a la configuración de la ubicación central y todas las ubicaciones satélites.</span><span class="sxs-lookup"><span data-stu-id="47102-109">Global administrators and SharePoint Online administrators continue to have access to settings in the central location and all satellite locations.</span></span>

## <a name="configuring-geo-administrators"></a><span data-ttu-id="47102-110">Configurar los administradores geográficos</span><span class="sxs-lookup"><span data-stu-id="47102-110">Configuring geo administrators</span></span>

<span data-ttu-id="47102-111">Para configurar los administradores geográficos se requiere el módulo de PowerShell de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="47102-111">Configuring geo admins requires SharePoint Online PowerShell module.</span></span>

<span data-ttu-id="47102-112">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) para conectarse al centro de administración de la ubicación geográfica donde quiera agregar el administrador geográfico. (Por ejemplo, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span><span class="sxs-lookup"><span data-stu-id="47102-112">Use [Connect-SPOService](https://docs.microsoft.com/powershell/module/sharepoint-online/Connect-SPOService) to connect to the admin center of the geo location where you want to add the geo admin. (For example, Connect-SPOService  https://ContosoEUR-admin.sharepoint.com.)</span></span>

<span data-ttu-id="47102-113">Para ver los administradores geográficos existentes de una ubicación, ejecute `Get-SPOGeoAdministrator`</span><span class="sxs-lookup"><span data-stu-id="47102-113">To view the existing geo admins of a location, run `Get-SPOGeoAdministrator`</span></span>

### <a name="adding-a-user-as-a-geo-admin"></a><span data-ttu-id="47102-114">Agregar un usuario como administrador geográfico</span><span class="sxs-lookup"><span data-stu-id="47102-114">Adding a user as a geo admin</span></span>

<span data-ttu-id="47102-115">Para agregar un usuario como administrador geográfico, ejecute `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="47102-115">To add a user as a geo admin, run `Add-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

<span data-ttu-id="47102-116">Para quitar un usuario como administrador geográfico de una ubicación, ejecute  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span><span class="sxs-lookup"><span data-stu-id="47102-116">To remove a user as a Geo Admin of a location, run  `Remove-SPOGeoAdministrator -UserPrincipalName <UPN>`</span></span>

### <a name="adding-a-group-as-a-geo-admin"></a><span data-ttu-id="47102-117">Agregar un grupo como administrador geográfico</span><span class="sxs-lookup"><span data-stu-id="47102-117">Adding a group as a geo admin</span></span>

<span data-ttu-id="47102-118">Puede agregar un grupo de seguridad o un grupo de seguridad habilitado para correo como administrador geográfico. (No se admiten los grupos de distribución y Grupos de Microsoft 365).</span><span class="sxs-lookup"><span data-stu-id="47102-118">You can add a security group or a mail-enabled security group as a geo admin. (Distribution groups and Microsoft 365 Groups are not supported.)</span></span>

<span data-ttu-id="47102-119">Para agregar un grupo como administrador geográfico, ejecute `Add-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="47102-119">To add a group as a geo administrator, run `Add-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="47102-120">Para quitar un grupo como administrador geográfico, ejecute `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span><span class="sxs-lookup"><span data-stu-id="47102-120">To remove a group as a geo administrator, run `Remove-SPOGeoAdministrator -GroupAlias <alias>`</span></span>

<span data-ttu-id="47102-121">Tenga en cuenta que no todos los grupos de seguridad tienen un alias de grupo.</span><span class="sxs-lookup"><span data-stu-id="47102-121">Note that not all security groups have a group alias.</span></span> <span data-ttu-id="47102-122">Si quiere agregar un grupo de seguridad que no tiene un alias, ejecute [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) para recuperar una lista de grupos, busque el ObjectID del grupo seguridad y ejecute lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="47102-122">If you want to add a security group that does not have an alias, run [Get-MsolGroup](https://docs.microsoft.com/powershell/module/msonline/get-msolgroup) to retrieve a list of groups, find your security group's ObjectID, and then run:</span></span>

`Add-SPOGeoAdministrator -ObjectID <ObjectID>`

<span data-ttu-id="47102-123">Para quitar un grupo mediante ObjectID, ejecute `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span><span class="sxs-lookup"><span data-stu-id="47102-123">To remove a group by using the ObjectID, run `Remove-SPOGeoAdministrator -ObjectID <ObjectID>`</span></span>

## <a name="related-topics"></a><span data-ttu-id="47102-124">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="47102-124">Related topics</span></span>

[<span data-ttu-id="47102-125">Add-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="47102-125">Add-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/add-spogeoadministrator)

[<span data-ttu-id="47102-126">Get-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="47102-126">Get-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spogeoadministrator)

[<span data-ttu-id="47102-127">Remove-SPOGeoAdministrator</span><span class="sxs-lookup"><span data-stu-id="47102-127">Remove-SPOGeoAdministrator</span></span>](https://docs.microsoft.com/powershell/module/sharepoint-online/remove-spogeoadministrator)

[<span data-ttu-id="47102-128">Establecer un alias (MailNickName) de un grupo de seguridad</span><span class="sxs-lookup"><span data-stu-id="47102-128">Set an alias (MailNickName) for a security group</span></span>](https://docs.microsoft.com/powershell/module/azuread/set-azureadgroup)