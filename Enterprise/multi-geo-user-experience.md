---
title: Experiencia del usuario en un entorno multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información sobre la experiencia del usuario de SharePoint y OneDrive en un entorno multigeográfico.
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="b6efb-103">Experiencia del usuario en un entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="b6efb-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="b6efb-104">Esto es lo que verán los usuarios en una configuración de OneDrive multigeográfico:</span><span class="sxs-lookup"><span data-stu-id="b6efb-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="b6efb-105">Ubicación de la instancia de OneDrive para la Empresa del usuario</span><span class="sxs-lookup"><span data-stu-id="b6efb-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="b6efb-p101">Los usuarios habrán aprovisionado su instancia de OneDrive para la Empresa en la ubicación de datos que prefieran. Si un usuario navega a una dirección URL de OneDrive que contiene una ubicación geográfica incorrecta (por ejemplo, un marcador de una ubicación geográfica anterior), se les redirige automáticamente a la instancia de OneDrive en la ubicación geográfica correspondiente.</span><span class="sxs-lookup"><span data-stu-id="b6efb-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="b6efb-108">Uso compartido</span><span class="sxs-lookup"><span data-stu-id="b6efb-108">Sharing</span></span>

<span data-ttu-id="b6efb-p102">La experiencia del selector de personas muestra a todos los usuarios independientemente de su ubicación geográfica. Esto permite a un usuario compartir con otro usuario en la misma geoárea común o en otra de las ubicaciones geográficas del espacio empresarial. El contenido procedente de distintas ubicaciones geográficas se mostrará en la vista **Compartidos conmigo** en la instancia de OneDrive para la Empresa del usuario y se tiene acceso a él con la experiencia de inicio de sesión único independientemente de la ubicación geográfica en que se hospede.</span><span class="sxs-lookup"><span data-stu-id="b6efb-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="b6efb-112">Aplicaciones de Office</span><span class="sxs-lookup"><span data-stu-id="b6efb-112">Office applications</span></span>

<span data-ttu-id="b6efb-p103">Las aplicaciones de Office tales como Word, Excel y PowerPoint detectarán automáticamente la ubicación geográfica correcta de OneDrive para la Empresa de cada usuario cuando inicien sesión. Los usuarios no tienen que escribir la dirección URL específica de geoárea de su instancia de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="b6efb-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="b6efb-115">Cliente de sincronización de OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="b6efb-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="b6efb-116">El cliente de sincronización de OneDrive para la Empresa (versión 17.3.6943.0625 y versiones posteriores) detectará automáticamente la ubicación geográfica correcta de OneDrive para la Empresa del usuario.</span><span class="sxs-lookup"><span data-stu-id="b6efb-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="b6efb-117">Iniciador de aplicaciones de Office 365</span><span class="sxs-lookup"><span data-stu-id="b6efb-117">Office 365 app launcher</span></span>

<span data-ttu-id="b6efb-p104">El iniciador de aplicaciones es de reconocimiento multigeográfico y dirigirá cada icono a la ubicación geográfica correspondiente de la carga de trabajo. El icono de OneDrive apunta a la ubicación geográfica correcta en la que se hospeda la biblioteca de OneDrive del usuario, mientras que el icono de SharePoint apuntará a todos los usuarios de la ubicación central, ya que los sitios de grupo siguen hospedados allí.</span><span class="sxs-lookup"><span data-stu-id="b6efb-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="b6efb-120">Perfiles de usuarios de Delve</span><span class="sxs-lookup"><span data-stu-id="b6efb-120">Delve User profiles</span></span>

<span data-ttu-id="b6efb-p105">La información de perfiles de usuario se controla en la ubicación geográfica del usuario. Al seleccionar un usuario, se le dirigirá a la ubicación geográfica correcta del usuario, donde verá los detalles completos de su perfil.</span><span class="sxs-lookup"><span data-stu-id="b6efb-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="b6efb-123">Si Delve está desactivada, verá la experiencia de perfil clásica de SharePoint, que no es de reconocimiento multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="b6efb-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="b6efb-124">Delve</span><span class="sxs-lookup"><span data-stu-id="b6efb-124">Delve</span></span>

<span data-ttu-id="b6efb-125">En el caso de usuarios de Office 365 que se encuentran en instancias por satélite, se admite Delve multigeográfico, con la limitación de que Delve no se vincula a entradas de blog de SharePoint escritas por usuarios de otras regiones, solo a sus sitios de blog de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b6efb-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="b6efb-126">Búsqueda</span><span class="sxs-lookup"><span data-stu-id="b6efb-126">Search</span></span>

<span data-ttu-id="b6efb-p106">Cada ubicación geográfica tiene su propio índice de búsqueda y Centro de búsqueda. Cuando un usuario realiza una búsqueda, la consulta se envía a todas las ubicaciones geográficas y los resultados devueltos se combinan y luego se clasifican para que el usuario obtenga resultados unificados. Los usuarios obtienen resultados de todas las ubicaciones geográficas independientemente de su propia ubicación geográfica. Vea [Configurar la búsqueda en OneDrive para la Empresa multigeográfico](configure-search-for-multi-geo.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="b6efb-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="b6efb-131">Se admiten los siguientes clientes de búsqueda:</span><span class="sxs-lookup"><span data-stu-id="b6efb-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="b6efb-132">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="b6efb-132">OneDrive for Business</span></span>

-   <span data-ttu-id="b6efb-133">Delve</span><span class="sxs-lookup"><span data-stu-id="b6efb-133">Delve</span></span>

-   <span data-ttu-id="b6efb-134">Página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="b6efb-134">SharePoint Home</span></span>

-   <span data-ttu-id="b6efb-135">Centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="b6efb-135">The Search Center</span></span>

-   <span data-ttu-id="b6efb-136">Aplicaciones de búsqueda personalizada que usan la API de SharePoint Search</span><span class="sxs-lookup"><span data-stu-id="b6efb-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="b6efb-137">OneDrive para iOS y Android</span><span class="sxs-lookup"><span data-stu-id="b6efb-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="b6efb-p107">Las aplicaciones móviles de OneDrive para iOS y Android mostrarán los archivos de OneDrive y los archivos compartidos con usted, independientemente de su ubicación geográfica. La búsqueda en las aplicaciones móviles de OneDrive mostrará resultados relevantes de todas las ubicaciones geográficas. Descargue la última versión de estas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="b6efb-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="b6efb-141">Vea [Usar OneDrive en iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) y [usar OneDrive para Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="b6efb-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="b6efb-142">Experiencia de Teams</span><span class="sxs-lookup"><span data-stu-id="b6efb-142">Teams Experience</span></span>

<span data-ttu-id="b6efb-p108">Teams es de reconocimiento multigeográfico. Independientemente de la ubicación geográfica del usuario se muestran los archivos de OneDrive y los archivos vistos recientemente. Las menciones con @ funcionan con usuarios de todas las ubicaciones multigeográficas.</span><span class="sxs-lookup"><span data-stu-id="b6efb-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
