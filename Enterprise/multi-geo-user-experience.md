---
title: Experiencia del usuario en un entorno de multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtener información sobre la experiencia de usuario de SharePoint y OneDrive en un entorno multi-geo.
ms.openlocfilehash: 91837883ef7c970674a500afa4fda9adfafc6d5b
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a><span data-ttu-id="bbed3-103">Experiencia del usuario en un entorno multi-geo</span><span class="sxs-lookup"><span data-stu-id="bbed3-103">User experience in a multi-geo environment</span></span>

<span data-ttu-id="bbed3-104">Aquí es lo que verán los usuarios en una configuración OneDrive Multi-Geo:</span><span class="sxs-lookup"><span data-stu-id="bbed3-104">Here’s what your users will see in a OneDrive Multi-Geo configuration:</span></span>

#### <a name="users-onedrive-for-business-location"></a><span data-ttu-id="bbed3-105">OneDrive de usuario para la ubicación de la empresa</span><span class="sxs-lookup"><span data-stu-id="bbed3-105">User’s OneDrive for Business location</span></span>

<span data-ttu-id="bbed3-p101">Los usuarios tendrán su OneDrive para el negocio aprovisionado en su ubicación de datos preferido. Si un usuario se desplaza a una dirección URL de OneDrive que contiene una ubicación geográfica incorrecta (por ejemplo, un marcador de una ubicación geográfica anterior), se le dirigirá automáticamente a la OneDrive en la ubicación geográfica correspondiente.</span><span class="sxs-lookup"><span data-stu-id="bbed3-p101">Users will have their OneDrive for Business provisioned in their preferred data location. If a user navigates to a OneDrive URL that contains an incorrect geo-location (such as a bookmark from a previous geo-location), they are automatically redirected to the OneDrive in the appropriate geo-location.</span></span>

#### <a name="sharing"></a><span data-ttu-id="bbed3-108">Uso compartido</span><span class="sxs-lookup"><span data-stu-id="bbed3-108">Sharing</span></span>

<span data-ttu-id="bbed3-p102">La experiencia de selector de personas muestra todos los usuarios independientemente de su ubicación geográfica. Esto permite que un usuario comparta con otro usuario en su mismo geográfico o de cualquier otra de ubicaciones de geo de su arrendatario. Geo diferentes ubicaciones se mostrarán en la vista **compartida conmigo** en OneDrive del usuario para el negocio y se pueden acceder con Single Sign On experiencia independientemente de qué ubicación geográfica se aloja en contenido.</span><span class="sxs-lookup"><span data-stu-id="bbed3-p102">The People Picker experience shows all users regardless of their geo location. This allows a user to share with another user in their same geo or in any other of your tenant’s geo locations. Content from different geo locations will show up in the **Shared with Me** view in the user's OneDrive for Business and can be accessed with Single-Sign-On experience regardless of which geo-location it is hosted in.</span></span>

#### <a name="office-applications"></a><span data-ttu-id="bbed3-112">Aplicaciones de Office</span><span class="sxs-lookup"><span data-stu-id="bbed3-112">Office applications</span></span>

<span data-ttu-id="bbed3-p103">Aplicaciones de Office como Word, Excel y PowerPoint detectará automáticamente el OneDrive correcto para la ubicación geográfica de negocios para cada usuario cuando inician sesión. Los usuarios no necesitan especificar la URL específica de geo para su OneDrive.</span><span class="sxs-lookup"><span data-stu-id="bbed3-p103">Office applications such as Word, Excel, and PowerPoint will automatically detect the correct OneDrive for Business geo-location for each user when they log in. Users do not need to enter the geo-specific URL for their OneDrive.</span></span>

#### <a name="onedrive-for-business-sync-client"></a><span data-ttu-id="bbed3-115">OneDrive para el cliente de sincronización del negocio</span><span class="sxs-lookup"><span data-stu-id="bbed3-115">OneDrive for Business Sync Client</span></span>

<span data-ttu-id="bbed3-116">La OneDrive para el cliente de sincronización Business (versión 17.3.6943.0625 y posteriores) detectará automáticamente el OneDrive correcto para la ubicación geográfica de negocio para el usuario.</span><span class="sxs-lookup"><span data-stu-id="bbed3-116">The OneDrive for Business Sync Client (version 17.3.6943.0625 and later) will automatically detect the correct OneDrive for Business geo location for the user.</span></span>

#### <a name="office-365-app-launcher"></a><span data-ttu-id="bbed3-117">Iniciador de aplicaciones de Office 365</span><span class="sxs-lookup"><span data-stu-id="bbed3-117">Office 365 app launcher</span></span>

<span data-ttu-id="bbed3-p104">El iniciador de la aplicación es Multi-Geo y dirigirá cada mosaico a la ubicación geográfica correspondiente de la carga de trabajo. El OneDrive mosaico apunta a la ubicación correcta geo donde se aloja la biblioteca del usuario OneDrive, mientras que el mosaico de SharePoint seleccione todos los usuarios en la ubicación central, como sitios de grupo siguen alojados allí.</span><span class="sxs-lookup"><span data-stu-id="bbed3-p104">The app launcher is Multi-Geo aware and will direct each tile to the appropriate geo location of the workload. The OneDrive tile points to the correct geo location where the user’s OneDrive library is hosted, while the SharePoint tile will point all users to the central location, as team sites are still hosted there.</span></span>

#### <a name="delve-user-profiles"></a><span data-ttu-id="bbed3-120">Profundizar los perfiles de usuario</span><span class="sxs-lookup"><span data-stu-id="bbed3-120">Delve User profiles</span></span>

<span data-ttu-id="bbed3-p105">Información de perfil de usuario es usado en la ubicación del usuario geo. Al seleccionar un usuario, se le dirigirá a la ubicación geográfica apropiada para el usuario, donde podrá ver sus detalles de perfil completo.</span><span class="sxs-lookup"><span data-stu-id="bbed3-p105">User profile information is mastered in the user's geo location. When selecting a user, you will be directed to the appropriate geo location for the user, where you will see their full profile details.</span></span>

<span data-ttu-id="bbed3-123">Si Delve está desactivado, se verá el perfil clásico de experiencia en SharePoint, lo que no es multi-geo.</span><span class="sxs-lookup"><span data-stu-id="bbed3-123">If Delve is turned off, you will see the classic profile experience in SharePoint, which is not multi-geo aware.</span></span>

#### <a name="delve"></a><span data-ttu-id="bbed3-124">Delve</span><span class="sxs-lookup"><span data-stu-id="bbed3-124">Delve</span></span>

<span data-ttu-id="bbed3-125">Para los usuarios de Office 365 que se encuentran en las instancias de satélite, Multi-Geo profundizar es compatible con la limitación de Delve no se vincula a entradas de blog de SharePoint escritos por usuarios de otras regiones, sólo a los sitios de blogs de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="bbed3-125">For Office 365 users who are in the satellite instances, Delve Multi-Geo is supported, with the limitation that Delve doesn’t link to SharePoint blog posts written by users in other regions, only to their SharePoint blog sites.</span></span>

#### <a name="search"></a><span data-ttu-id="bbed3-126">Búsqueda</span><span class="sxs-lookup"><span data-stu-id="bbed3-126">Search</span></span>

<span data-ttu-id="bbed3-p106">Cada ubicación geográfica tiene su propio centro de búsqueda e índices de búsqueda. Cuando un usuario realiza una búsqueda, la consulta se envía a todas las ubicaciones de geo y los resultados devueltos se combinan y se clasificarán por lo que el usuario obtiene resultados unificadas. Los usuarios Obtén resultados de todas las ubicaciones geo independientemente su propia ubicación geográfica. Para obtener información específica, vea [Configurar búsqueda de OneDrive de negocios Multi-Geo](configure-search-for-multi-geo.md) .</span><span class="sxs-lookup"><span data-stu-id="bbed3-p106">Each geo location has its own search index and Search Center. When a user searches, the query is sent to all the geo locations, and the returned results are merged and then ranked so the user gets unified results. Users get results from all geo locations regardless of their own geo location. See [Configure Search for OneDrive for Business Multi-Geo](configure-search-for-multi-geo.md) for specifics.</span></span>

<span data-ttu-id="bbed3-131">Se admiten los siguientes clientes de búsqueda:</span><span class="sxs-lookup"><span data-stu-id="bbed3-131">The following search clients are supported:</span></span>

-   <span data-ttu-id="bbed3-132">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="bbed3-132">OneDrive for Business</span></span>

-   <span data-ttu-id="bbed3-133">Delve</span><span class="sxs-lookup"><span data-stu-id="bbed3-133">Delve</span></span>

-   <span data-ttu-id="bbed3-134">Inicio de SharePoint</span><span class="sxs-lookup"><span data-stu-id="bbed3-134">SharePoint Home</span></span>

-   <span data-ttu-id="bbed3-135">El centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="bbed3-135">The Search Center</span></span>

-   <span data-ttu-id="bbed3-136">Aplicaciones de búsqueda personalizadas que utilizan la API de búsqueda de SharePoint</span><span class="sxs-lookup"><span data-stu-id="bbed3-136">Custom search applications that use the SharePoint Search API</span></span>

#### <a name="onedrive-ios-and-android"></a><span data-ttu-id="bbed3-137">OneDrive iOS y Android</span><span class="sxs-lookup"><span data-stu-id="bbed3-137">OneDrive iOS and Android</span></span> 

<span data-ttu-id="bbed3-p107">El OneDrive iOS y Android aplicaciones móviles le mostrará los archivos OneDrive y compartido con usted, independientemente de su ubicación geográfica. Búsqueda de las aplicaciones móviles OneDrive mostrará resultados relevantes de todas las ubicaciones de geo. Descargue la versión más reciente de estas aplicaciones.</span><span class="sxs-lookup"><span data-stu-id="bbed3-p107">The OneDrive iOS and Android mobile apps will show you your OneDrive files and files shared with you regardless of their geo location. Search from the OneDrive mobile apps will show relevant results from all geo locations. Please download the latest version of these apps.</span></span>

<span data-ttu-id="bbed3-141">Para obtener más información, vea utilizar [OneDrive en iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) y [OneDrive de uso para Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .</span><span class="sxs-lookup"><span data-stu-id="bbed3-141">See Use [OneDrive on iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) and [Use OneDrive for Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) for more information.</span></span>

#### <a name="teams-experience"></a><span data-ttu-id="bbed3-142">Experiencia de los equipos</span><span class="sxs-lookup"><span data-stu-id="bbed3-142">Teams Experience</span></span>

<span data-ttu-id="bbed3-p108">Equipos es multi-geo. Independientemente de la ubicación del usuario geo se muestran archivos de OneDrive y vistos recientemente. @ menciona el trabajo con usuarios de todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="bbed3-p108">Teams is multi-geo aware. OneDrive files and recently viewed files are shown regardless of the user’s geo location. @ mentions work with users from all geo-locations.</span></span>
