---
title: Experiencia del usuario en un entorno multigeográfico
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Obtenga información sobre la experiencia del usuario de SharePoint, OneDrive y Exchange en un entorno multigeográfico.
ms.openlocfilehash: 21858989f853b2a8c87808e38763068631173f7f
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057756"
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="13fab-103">Experiencia del usuario en un entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="13fab-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="13fab-104">Esto es lo que verán los usuarios en una configuración de OneDrive multigeográfico:</span><span class="sxs-lookup"><span data-stu-id="13fab-104">Here's what your users will see in a OneDrive Multi-Geo configuration:</span></span>

## <a name="exchange-mailbox"></a><span data-ttu-id="13fab-105">Buzón de Exchange</span><span class="sxs-lookup"><span data-stu-id="13fab-105">Exchange mailbox</span></span>

<span data-ttu-id="13fab-106">El buzón de Exchange de un usuario se aprovisiona en su ubicación de datos preferida y si esta cambia el buzón se reubica automáticamente.</span><span class="sxs-lookup"><span data-stu-id="13fab-106">A user's Exchange mailbox is provisioned to their preferred data location, and is automatically relocated if their PDL changes.</span></span> <span data-ttu-id="13fab-107">Los usuarios pueden usar Outlook y Outlook en la Web normalmente sin cambios en la experiencia del usuario en un entorno de multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="13fab-107">Users can use Outlook and Outlook on the web normally with no change in user experience in a multi-geo environment.</span></span>

## <a name="hub-sites"></a><span data-ttu-id="13fab-108">Sitios centrales</span><span class="sxs-lookup"><span data-stu-id="13fab-108">Hub sites</span></span>

<span data-ttu-id="13fab-109">Los sitios centrales de SharePoint mejoran la detección y la participación con contenido para los empleados, al crear una representación completa y coherente de proyectos, departamentos o regiones.</span><span class="sxs-lookup"><span data-stu-id="13fab-109">SharePoint Hub sites enhances the discovery and engagement with content for employees, while creating a complete and consistent representation of projects, departments or regions.</span></span> <span data-ttu-id="13fab-110">En un entorno multigeográfico, los sitios de ubicaciones satélite pueden asociarse fácilmente con un sitio central independientemente de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="13fab-110">In a multi-geo environment, sites from satellite locations can easily be associated with a hub site regardless the hub site's geo location.</span></span> <span data-ttu-id="13fab-111">Los usuarios pueden buscar y obtener resultados en la central mediante una experiencia de búsqueda única, independientemente de la ubicación geográfica de los sitios.</span><span class="sxs-lookup"><span data-stu-id="13fab-111">Users can search and get results across the hub through a single search experience, regardless of the geo location of the sites.</span></span>

## <a name="microsoft-365-app-launcher"></a><span data-ttu-id="13fab-112">Iniciador de aplicaciones de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="13fab-112">Microsoft 365 app launcher</span></span>

<span data-ttu-id="13fab-113">El iniciador de aplicaciones es compatible con múltiples ubicaciones geográficas y dirigirá cada icono a la ubicación geográfica correspondiente de la carga de trabajo.</span><span class="sxs-lookup"><span data-stu-id="13fab-113">The app launcher is multi-geo aware and will direct each tile to the appropriate geo location of the workload.</span></span> <span data-ttu-id="13fab-114">Los iconos de SharePoint y OneDrive apuntarán al usuario a la ubicación correspondiente a la ubicación geográfica aprovisionada del usuario.</span><span class="sxs-lookup"><span data-stu-id="13fab-114">The SharePoint and OneDrive tiles will point the user to the location corresponding to the user's provisioned geo location.</span></span> <span data-ttu-id="13fab-115">Esto significa que si el usuario tiene un OneDrive en la ubicación central, el icono de SharePoint apuntarán a la página principal de SharePoint en la ubicación central, pero se aprovisionará su sitio de grupo en la ubicación correspondiente a su ubicación de datos preferida.</span><span class="sxs-lookup"><span data-stu-id="13fab-115">This means that is the user has a OneDrive in the central location, their SharePoint tile will point them to SP Home in the central location but their group site will be provisioned in the location corresponding to their PDL.</span></span> 

## <a name="office-applications"></a><span data-ttu-id="13fab-116">Aplicaciones de Office</span><span class="sxs-lookup"><span data-stu-id="13fab-116">Office applications</span></span>

<span data-ttu-id="13fab-117">Las aplicaciones de Office tales como Word, Excel y PowerPoint detectarán automáticamente la ubicación geográfica correcta de OneDrive para la Empresa de cada usuario cuando inicien sesión.</span><span class="sxs-lookup"><span data-stu-id="13fab-117">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in.</span></span> <span data-ttu-id="13fab-118">Los usuarios no tienen que escribir la dirección URL específica de geoárea de su instancia de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="13fab-118">Users do not need to enter the geo-specific URL for their OneDrive or SharePoint sites.</span></span>

## <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="13fab-119">Cliente de sincronización de OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="13fab-119">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="13fab-120">El cliente de sincronización de OneDrive para la Empresa (versión 17.3.6943.0625 y versiones posteriores) detectará automáticamente la ubicación geográfica correcta de OneDrive para la Empresa del usuario.</span><span class="sxs-lookup"><span data-stu-id="13fab-120">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span> <span data-ttu-id="13fab-121">La compatibilidad con clientes de sincronización incluye la posibilidad de sincronizar sitios basados en grupos independientemente de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="13fab-121">Synch client support includes the ability to sync groups-based sites regardless of their geo location.</span></span> <span data-ttu-id="13fab-122">Tenga en cuenta que el cliente de sincronización de Groove no es compatible con las capacidades multigeográficas.</span><span class="sxs-lookup"><span data-stu-id="13fab-122">Note that the Groove sync client is not supported for multi-geo.</span></span> 

## <a name="onedrive-for-business-location"></a><span data-ttu-id="13fab-123">Ubicación de la instancia de OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="13fab-123">OneDrive for Business location</span></span>

<span data-ttu-id="13fab-p106">Los usuarios habrán aprovisionado su instancia de OneDrive para la Empresa en la ubicación de datos que prefieran. Si un usuario navega a una dirección URL de OneDrive que contiene una ubicación geográfica incorrecta (por ejemplo, un marcador de una ubicación geográfica anterior), se les redirige automáticamente a la instancia de OneDrive en la ubicación geográfica correspondiente.</span><span class="sxs-lookup"><span data-stu-id="13fab-p106">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo location (such as a bookmark from a previous geo location), they are automatically redirected to the OneDrive in the appropriate geo location.</span></span>

## <a name="onedrive-ios-and-android"></a><span data-ttu-id="13fab-126">OneDrive para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="13fab-126">OneDrive iOS and Android</span></span> 

<span data-ttu-id="13fab-p107">Las aplicaciones móviles de OneDrive para iOS y Android mostrarán los archivos de OneDrive y los archivos compartidos con usted, independientemente de su ubicación geográfica. La búsqueda en las aplicaciones móviles de OneDrive mostrará resultados relevantes de todas las ubicaciones geográficas. Descargue la última versión de estas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="13fab-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="13fab-130">Vea [Usar OneDrive en iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) y [usar OneDrive para Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="13fab-130">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

## <a name="onedrive-mobile-client"></a><span data-ttu-id="13fab-131">Cliente móvil de OneDrive</span><span class="sxs-lookup"><span data-stu-id="13fab-131">OneDrive Mobile Client</span></span> 

<span data-ttu-id="13fab-132">El cliente móvil de OneDrive es compatible con las capacidades multigeográficas y mostrará el contenido y los resultados relevantes de todas las ubicaciones geográfica.</span><span class="sxs-lookup"><span data-stu-id="13fab-132">The OneDrive Mobile Client is multi-geo aware and will display pertinent content and results from all geo locations.</span></span>

## <a name="search"></a><span data-ttu-id="13fab-133">Búsqueda</span><span class="sxs-lookup"><span data-stu-id="13fab-133">Search</span></span>

<span data-ttu-id="13fab-p108">Cada ubicación geográfica tiene su propio índice de búsqueda y Centro de búsqueda. Cuando un usuario realiza una búsqueda, la consulta se envía a todas las ubicaciones geográficas y los resultados devueltos se combinan y luego se clasifican para que el usuario obtenga resultados unificados. Los usuarios obtienen resultados de todas las ubicaciones geográficas independientemente de su propia ubicación geográfica. Vea [Configurar la búsqueda en OneDrive para la Empresa multigeográfico](configure-search-for-multi-geo.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="13fab-p108">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="13fab-138">Se admiten los siguientes clientes de búsqueda:</span><span class="sxs-lookup"><span data-stu-id="13fab-138">The following search clients are supported:</span></span>

-   <span data-ttu-id="13fab-139">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="13fab-139">OneDrive for Business</span></span>

-   <span data-ttu-id="13fab-140">Delve</span><span class="sxs-lookup"><span data-stu-id="13fab-140">Delve</span></span>

-   <span data-ttu-id="13fab-141">Página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="13fab-141">SharePoint Home</span></span>

-   <span data-ttu-id="13fab-142">Centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="13fab-142">The Search Center</span></span>

-   <span data-ttu-id="13fab-143">Aplicaciones de búsqueda personalizada que usan la API de SharePoint Search</span><span class="sxs-lookup"><span data-stu-id="13fab-143">Custom search applications that use the SharePoint Search API</span></span>

## <a name="sharepoint-home"></a><span data-ttu-id="13fab-144">Página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="13fab-144">SharePoint Home</span></span> 

<span data-ttu-id="13fab-145">En SharePoint Multi-Geo su página principal de SharePoint se hospeda en la ubicación donde se encuentra el usuario según su ubicación de OneDrive para la Empresa.</span><span class="sxs-lookup"><span data-stu-id="13fab-145">In SharePoint Multi-Geo your SharePoint home is hosted in the location where the user resides as determined by their OneDrive for business location.</span></span> <span data-ttu-id="13fab-146">Por ejemplo: si el usuario tiene hospedado OneDrive en una ubicación satélite de Europa, la página principal de SharePoint se representará desde Europa.</span><span class="sxs-lookup"><span data-stu-id="13fab-146">For example: if the user has their OneDrive hosted in an European satellite location, their SharePoint Home will be rendered from Europe.</span></span> <span data-ttu-id="13fab-147">La página principal de SharePoint incluye todo el contenido relevante para el usuario independientemente de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="13fab-147">SharePoint home includes all content relevant to the user regardless of its geo location.</span></span> 

<span data-ttu-id="13fab-148">**Sitios seguidos, noticias de sitios, sitios recientes, sitios frecuentes y sitios sugeridos**</span><span class="sxs-lookup"><span data-stu-id="13fab-148">**Followed Sites, News from Sites, Recent Sites, Frequent Sites, and Suggested sites**</span></span>

<span data-ttu-id="13fab-149">Todos estos componentes se mostrarán con independencia de la ubicación geográfica donde se hospeda el contenido, siempre y cuando el usuario tenga permisos para dicho contenido.</span><span class="sxs-lookup"><span data-stu-id="13fab-149">All of these components will show up for the user regardless of the geo location where the content is hosted, so long as the user has permissions to said content.</span></span> 

<span data-ttu-id="13fab-150">**Vínculos destacados**</span><span class="sxs-lookup"><span data-stu-id="13fab-150">**Features Links**</span></span>

<span data-ttu-id="13fab-151">Los administradores pueden configurar vínculos destacados en la página principal de SharePoint según sea adecuado para cada ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="13fab-151">Admins may configure Featured links in SharePoint home as appropriate to each geo location.</span></span> <span data-ttu-id="13fab-152">Esto permite que el administrador destaque en la página principal de SharePoint de cada región los vínculos que sean apropiados para los usuarios de la región.</span><span class="sxs-lookup"><span data-stu-id="13fab-152">This allows the admin to feature in the SP Home for each region the links that are appropriate for users in the region.</span></span> 

## <a name="sharepoint-mobile-client"></a><span data-ttu-id="13fab-153">Cliente móvil de SharePoint</span><span class="sxs-lookup"><span data-stu-id="13fab-153">SharePoint Mobile Client</span></span> 

<span data-ttu-id="13fab-154">El cliente móvil de SharePoint es compatible con las capacidades multigeográficas y mostrará el contenido y los resultados relevantes de todas las ubicaciones geográfica.</span><span class="sxs-lookup"><span data-stu-id="13fab-154">The SharePoint Mobile Client is multi-geo aware and will display pertinent content and results from all geo locations.</span></span>

## <a name="sharing"></a><span data-ttu-id="13fab-155">Uso compartido</span><span class="sxs-lookup"><span data-stu-id="13fab-155">Sharing</span></span>

<span data-ttu-id="13fab-156">La experiencia de selector de personas muestra todos los usuarios, independientemente de su ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="13fab-156">The People Picker experience shows all users regardless of their geo location.</span></span> <span data-ttu-id="13fab-157">Esto permite que un usuario pueda compartir con otro de su misma ubicación geográfica o en cualquier otra ubicación geográfica de su inquilino.</span><span class="sxs-lookup"><span data-stu-id="13fab-157">This allows a user to share with another user in their same geo or in any other of your tenant's geo locations.</span></span> <span data-ttu-id="13fab-158">El contenido de diferentes ubicaciones geográficas se mostrará en la vista **Compartido conmigo** OneDrive para la Empresa del usuario y puede accederse a el con la experiencia inicio de sesión único independientemente de la ubicación geográfica en la que se hospeda.</span><span class="sxs-lookup"><span data-stu-id="13fab-158">Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single Sign-On experience regardless of which geo location it is hosted in.</span></span>

## <a name="teams-experience"></a><span data-ttu-id="13fab-159">Experiencia de Teams</span><span class="sxs-lookup"><span data-stu-id="13fab-159">Teams Experience</span></span>

<span data-ttu-id="13fab-160">Teams es compatible con las capacidades multigeográficas.</span><span class="sxs-lookup"><span data-stu-id="13fab-160">Teams is multi-geo aware.</span></span> <span data-ttu-id="13fab-161">Los archivos de OneDrive y los archivos vistos recientemente se muestran independientemente de la ubicación geográfica del usuario.</span><span class="sxs-lookup"><span data-stu-id="13fab-161">OneDrive files and recently viewed files are shown regardless of the user's geo location.</span></span> <span data-ttu-id="13fab-162">Las @menciones funcionan con los usuarios de todas las ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="13fab-162">@ mentions work with users from all geo-locations.</span></span>

## <a name="user-profiles"></a><span data-ttu-id="13fab-163">Perfiles de usuario</span><span class="sxs-lookup"><span data-stu-id="13fab-163">User profiles</span></span>

<span data-ttu-id="13fab-p113">La información de perfiles de usuario se controla en la ubicación geográfica del usuario. Al seleccionar un usuario, se le dirigirá a la ubicación geográfica correcta del usuario, donde verá los detalles completos de su perfil.</span><span class="sxs-lookup"><span data-stu-id="13fab-p113">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="13fab-166">Si Delve está desactivada, verá la experiencia de perfil clásica de SharePoint, que no es de reconocimiento multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="13fab-166">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>


