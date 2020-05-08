---
title: Capacidades multigeográficas de OneDrive y SharePoint Online
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
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expanda la presencia de Microsoft 365 a varias regiones geográficas con las capacidades multigeográficas de OneDrive Online.
ms.openlocfilehash: dd65be117a57868e16794f64690e788e575112f5
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057970"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="67332-103">Capacidades multigeográficas de OneDrive y SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="67332-103">Multi-Geo Capabilities in OneDrive and SharePoint Online</span></span>

<span data-ttu-id="67332-104">Las capacidades multigeográficas de OneDrive y SharePoint Online permiten controlar el país o región donde se almacenan los recursos compartidos, como sitios de grupo de SharePoint y buzones de grupo de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="67332-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of the country or region where shared resources like SharePoint team sites and Microsoft 365 Group mailboxes are stored at rest.</span></span>

<span data-ttu-id="67332-105">Todos los usuarios, buzones de grupo y sitios de SharePoint tienen una Ubicación de datos preferida (PDL) que indica la ubicación geográfica donde están almacenados los datos relacionados.</span><span class="sxs-lookup"><span data-stu-id="67332-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="67332-106">Los datos personales de los usuarios (buzón de Exchange y OneDrive), junto con los Grupos de Microsoft 365 o los sitios de SharePoint que creen, pueden almacenarse en la ubicación geográfica especificada para cumplir los requisitos de residencia de datos.</span><span class="sxs-lookup"><span data-stu-id="67332-106">Users' personal data (Exchange mailbox and OneDrive) along with any Microsoft 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="67332-107">También puede [especificar administradores diferentes para cada ubicación geográfica](add-a-sharepoint-geo-admin.md).</span><span class="sxs-lookup"><span data-stu-id="67332-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="67332-108">Los usuarios obtienen una experiencia fluida al usar los servicios de Microsoft 365, incluidas las aplicaciones de Office, OneDrive y Search.</span><span class="sxs-lookup"><span data-stu-id="67332-108">Users get a seamless experience when using Microsoft 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="67332-109">Vea [Experiencia de usuario en un entorno multi-geográfico](multi-geo-user-experience.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="67332-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="67332-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="67332-110">OneDrive</span></span>

<span data-ttu-id="67332-111">El OneDrive de cada usuario lo puede aprovisionar o [mover un administrador](move-onedrive-between-geo-locations.md) a una ubicación de satélite conforme con la PDL del usuario.</span><span class="sxs-lookup"><span data-stu-id="67332-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="67332-112">Los archivos personales se conservan en esa ubicación geográfica, aunque se pueden compartir con usuarios en otra ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="67332-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sharepoint-sites-and-groups"></a><span data-ttu-id="67332-113">Sitios y grupos de SharePoint</span><span class="sxs-lookup"><span data-stu-id="67332-113">SharePoint Sites and Groups</span></span>

<span data-ttu-id="67332-114">La administración de la característica multigeográfica está disponible en el Centro de administración de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="67332-114">Management of the Multi-Geo feature is available through the SharePoint admin center.</span></span> <span data-ttu-id="67332-115">Encontrará información detallada en la [correspondiente entrada de blog](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).</span><span class="sxs-lookup"><span data-stu-id="67332-115">Detailed information can be found in the [corresponding blog post](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302).</span></span>

<span data-ttu-id="67332-116">Cuando un usuario crea un sitio de SharePoint conectado al grupo en un entorno multigeográfico, su PDL se utiliza para determinar la ubicación geográfica donde se crean el sitio y su buzón de grupo asociado.</span><span class="sxs-lookup"><span data-stu-id="67332-116">When a user creates a SharePoint group-connected site in a multi-geo environment, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="67332-117">(Si el valor de la PDL del usuario no se ha configurado o se ha establecido en una ubicación geográfica que no se ha configurado como una ubicación de satélite, el sitio y el buzón se crean en la ubicación central).</span><span class="sxs-lookup"><span data-stu-id="67332-117">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="67332-118">Otros servicios de Microsoft 365 aparte de Exchange, OneDrive y SharePoint no son multigeográficos.</span><span class="sxs-lookup"><span data-stu-id="67332-118">Microsoft 365 services other than Exchange, OneDrive, and SharePoint are not Multi-Geo.</span></span> <span data-ttu-id="67332-119">Sin embargo, los Grupos de Microsoft 365 creados por estos servicios estarán marcados con la PDL del creador, y su buzón de grupo de Exchange y el sitio de grupo de Office 365 SharePoint estarán aprovisionados con la ubicación geográfica correspondiente.</span><span class="sxs-lookup"><span data-stu-id="67332-119">However, Microsoft 365 Groups that are created by these services will be stamped with the PDL of the creator and their Exchange Group mailbox and SharePoint O365 Group Site provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="67332-120">Administrar el entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="67332-120">Managing the multi-geo environment</span></span>

<span data-ttu-id="67332-121">Puede configurar y administrar su entorno multigeográfico mediante el Centro de administración de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="67332-121">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![Captura de pantalla de la página de ubicaciones geográficas en el Centro de administración de SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="67332-123">(Algunas acciones, como cambiar un sitio de SharePoint o un sitio de OneDrive, requieren Microsoft PowerShell).</span><span class="sxs-lookup"><span data-stu-id="67332-123">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="67332-124">Consulte también</span><span class="sxs-lookup"><span data-stu-id="67332-124">See also</span></span>

[<span data-ttu-id="67332-125">Capacidades multigeográficas en grupos de SharePoint y Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="67332-125">Multi-Geo in SharePoint and Microsoft 365 Groups</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Now-available-Multi-Geo-in-SharePoint-and-Office-365-Groups/ba-p/263302)

[<span data-ttu-id="67332-126">Administración de un entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="67332-126">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="67332-127">Cuotas de almacenamiento de SharePoint en entornos multigeográficos</span><span class="sxs-lookup"><span data-stu-id="67332-127">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="67332-128">Administración de buzones de correo de Exchange Online en un entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="67332-128">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
