---
title: Capacidades multigeográficas de OneDrive y SharePoint Online
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
ms.assetid: 094e86f2-9ff0-40ac-af31-28fcaba00c1d
description: Expanda la presencia de Office 365 a varias regiones geográficas con las capacidades multigeográficas de OneDrive Online.
ms.openlocfilehash: 15dcb44943fa1bf331ef6260946f7c3a632d3c4a
ms.sourcegitcommit: dffbcfb1cbc9776a29229a787c1eab4192e55cff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "30948591"
---
# <a name="multi-geo-capabilities-in-onedrive-and-sharepoint-online"></a><span data-ttu-id="12b68-103">Capacidades multigeográficas de OneDrive y SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="12b68-103">Multi-Geo Capabilities in OneDrive and SharePoint Online in Office 365</span></span>

<span data-ttu-id="12b68-104">Las capacidades multigeográficas de OneDrive y SharePoint Online permiten controlar el país o región donde se almacenan los recursos compartidos, como sitios de grupo de SharePoint y buzones de grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="12b68-104">Multi-Geo capabilities in OneDrive and SharePoint Online enables control of the country or region where shared resources like SharePoint team sites and Office 365 Group mailboxes are stored at rest.</span></span>

<span data-ttu-id="12b68-105">Todos los usuarios, buzones de grupo y sitios de SharePoint tienen una Ubicación de datos preferida (PDL) que indica la ubicación geográfica donde están almacenados los datos relacionados.</span><span class="sxs-lookup"><span data-stu-id="12b68-105">Each user, Group mailbox, and SharePoint site has a Preferred Data Location (PDL) which denotes the geo location where related data is to be stored.</span></span> <span data-ttu-id="12b68-106">Los datos personales de los usuarios (buzón de Exchange y OneDrive), junto con los Grupos de Office 365 o los sitios de SharePoint que creen, pueden almacenarse en la ubicación geográfica especificada para cumplir los requisitos de residencia de datos.</span><span class="sxs-lookup"><span data-stu-id="12b68-106">Users' personal data (Exchange mailbox and OneDrive) along with any Office 365 Groups or SharePoint sites that they create can be stored in the specified geo location to meet data residency requirements.</span></span> <span data-ttu-id="12b68-107">También puede [especificar administradores diferentes para cada ubicación geográfica](add-a-sharepoint-geo-admin.md).</span><span class="sxs-lookup"><span data-stu-id="12b68-107">You can [specify different administrators for each geo location](add-a-sharepoint-geo-admin.md).</span></span>

<span data-ttu-id="12b68-108">Los usuarios obtienen una experiencia fluida al usar los servicios de Office 365, incluidas las aplicaciones de Office, OneDrive y Search.</span><span class="sxs-lookup"><span data-stu-id="12b68-108">Users get a seamless experience when using Office 365 services, including Office applications, OneDrive, and Search.</span></span> <span data-ttu-id="12b68-109">Vea [Experiencia de usuario en un entorno multi-geográfico](multi-geo-user-experience.md) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="12b68-109">See [User experience in a multi-geo environment](multi-geo-user-experience.md) for details.</span></span>

## <a name="onedrive"></a><span data-ttu-id="12b68-110">OneDrive</span><span class="sxs-lookup"><span data-stu-id="12b68-110">OneDrive</span></span>

<span data-ttu-id="12b68-111">El OneDrive de cada usuario lo puede aprovisionar o [mover un administrador](move-onedrive-between-geo-locations.md) a una ubicación de satélite conforme con la PDL del usuario.</span><span class="sxs-lookup"><span data-stu-id="12b68-111">Each user's OneDrive can be provisioned in or [moved by an administrator](move-onedrive-between-geo-locations.md) to a satellite location in accordance with the user's PDL.</span></span> <span data-ttu-id="12b68-112">Los archivos personales se conservan en esa ubicación geográfica, aunque se pueden compartir con usuarios en otra ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="12b68-112">Personal files are then kept in that geo location, though they can be shared with users in other geo locations.</span></span>

## <a name="sites-and-groups"></a><span data-ttu-id="12b68-113">Equipos y grupos</span><span class="sxs-lookup"><span data-stu-id="12b68-113">Active Directory Sites and Routing Groups tab</span></span>

<span data-ttu-id="12b68-114">Cuando un usuario crea un sitio de SharePoint conectado al grupo, su PDL se utiliza para determinar la ubicación geográfica donde se crean el sitio y su buzón de grupo asociado.</span><span class="sxs-lookup"><span data-stu-id="12b68-114">When a user creates a SharePoint group-connected site, their PDL is used to determine the geo location where the site and its associated Group mailbox is created.</span></span> <span data-ttu-id="12b68-115">(Si el valor de la PDL del usuario no se ha configurado o se ha establecido en una ubicación geográfica que no se ha configurado como una ubicación de satélite, el sitio y el buzón se crean en la ubicación central).</span><span class="sxs-lookup"><span data-stu-id="12b68-115">(If the user's PDL value hasn't been set, or has been set to geo location that hasn't been configured as a satellite location, then the site and mailbox are created in the central location.)</span></span>

<span data-ttu-id="12b68-116">Otros servicios de Office 365 aparte de Exchange, OneDrive y SharePoint no son multigeográficos.</span><span class="sxs-lookup"><span data-stu-id="12b68-116">Office 365 services other than Exchange, OneDrive, and SharePoint are not Multi-Geo.</span></span> <span data-ttu-id="12b68-117">Sin embargo, los Grupos de Office 365 creados por estos servicios estarán marcados con la PDL del creador, y su buzón de grupo de Exchange y el sitio de grupo de Office 365 SharePoint estarán aprovisionados con la ubicación geográfica correspondiente.</span><span class="sxs-lookup"><span data-stu-id="12b68-117">However, Office 365 Groups that are created by these services will be stamped with the PDL of the creator and their Exchange Group mailbox and SharePoint O365 Group Site provisioned in the corresponding geo.</span></span> 

## <a name="managing-the-multi-geo-environment"></a><span data-ttu-id="12b68-118">Administrar el entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="12b68-118">Managing the multi-geo environment</span></span>

<span data-ttu-id="12b68-119">Puede configurar y administrar su entorno multigeográfico mediante el Centro de administración de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="12b68-119">Setting up and managing your multi-geo environment is done through the SharePoint admin center.</span></span> 

![Captura de pantalla de la página de ubicaciones geográficas en el Centro de administración de SharePoint](media/sharepoint-multi-geo-admin-center.png)

<span data-ttu-id="12b68-121">(Algunas acciones, como cambiar un sitio de SharePoint o un sitio de OneDrive, requieren Microsoft PowerShell).</span><span class="sxs-lookup"><span data-stu-id="12b68-121">(Some actions, such as moving a SharePoint site or a OneDrive site require Microsoft PowerShell.)</span></span>

## <a name="see-also"></a><span data-ttu-id="12b68-122">Vea también</span><span class="sxs-lookup"><span data-stu-id="12b68-122">See also</span></span>

[<span data-ttu-id="12b68-123">Aka.ms/GetMultiGeo </span><span class="sxs-lookup"><span data-stu-id="12b68-123">Aka.ms/GetMultiGeo </span></span>](https://Aka.ms/GetMultiGeo)

[<span data-ttu-id="12b68-124">Administración de un entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="12b68-124">Administering a multi-geo environment</span></span>](administering-a-multi-geo-environment.md)

[<span data-ttu-id="12b68-125">Cuotas de almacenamiento de SharePoint en entornos multigeográficos</span><span class="sxs-lookup"><span data-stu-id="12b68-125">SharePoint storage quotas in multi-geo environments</span></span>](sharepoint-multi-geo-storage-quota.md)

[<span data-ttu-id="12b68-126">Administración de buzones de correo de Exchange Online en un entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="12b68-126">Administering Exchange Online mailboxes in a multi-geo environment</span></span>](administering-exchange-online-multi-geo.md)
