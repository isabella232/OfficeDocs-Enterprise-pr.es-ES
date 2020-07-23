---
title: Identidad solo de nube de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/09/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Describe cómo crear usuarios y grupos cuando la suscripción de Microsoft 365 usa identidad solo de nube.
ms.openlocfilehash: 0c2568d7be3f7a7b476d4cf918f00baf238da5ad
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230026"
---
# <a name="microsoft-365-cloud-only-identity"></a><span data-ttu-id="69863-103">Identidad solo de nube de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="69863-103">Microsoft 365 cloud-only identity</span></span>

<span data-ttu-id="69863-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="69863-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="69863-105">Con la identidad solo de nube, todos los usuarios, grupos y contactos se almacenan en el inquilino de Azure Active Directory (Azure AD) de la suscripción a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="69863-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Microsoft 365 subscription.</span></span> <span data-ttu-id="69863-106">Estos son los componentes básicos de la identidad solo de la nube.</span><span class="sxs-lookup"><span data-stu-id="69863-106">Here are the basic components of cloud-only identity.</span></span>
 
![Los componentes básicos de la identidad solo de nube](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="69863-108">Los usuarios y sus cuentas de usuario en las organizaciones se pueden clasificar de varias formas.</span><span class="sxs-lookup"><span data-stu-id="69863-108">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="69863-109">Por ejemplo, algunos son empleados y tienen un estado permanente.</span><span class="sxs-lookup"><span data-stu-id="69863-109">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="69863-110">Algunos son proveedores, contratistas o asociados que tienen un estado temporal.</span><span class="sxs-lookup"><span data-stu-id="69863-110">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="69863-111">Algunos son usuarios externos que no tienen cuentas de usuario, pero tienen que seguir concedido el acceso a servicios y recursos específicos para admitir la interacción y la colaboración.</span><span class="sxs-lookup"><span data-stu-id="69863-111">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="69863-112">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="69863-112">For example:</span></span>

- <span data-ttu-id="69863-113">Cuentas de espacio empresarial que representan a usuarios de su organización a los que asigna una licencia para servicios en la nube</span><span class="sxs-lookup"><span data-stu-id="69863-113">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="69863-114">Cuentas entre empresas (B2B) que representan a usuarios externos a la organización a los que invita a participar en colaboración</span><span class="sxs-lookup"><span data-stu-id="69863-114">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration</span></span>

<span data-ttu-id="69863-115">Tomar en existencias los tipos de usuarios de la organización.</span><span class="sxs-lookup"><span data-stu-id="69863-115">Take stock of the types of users in your organization.</span></span> <span data-ttu-id="69863-116">¿Cuáles son las agrupaciones?</span><span class="sxs-lookup"><span data-stu-id="69863-116">What are the groupings?</span></span> <span data-ttu-id="69863-117">Por ejemplo, puede agrupar a los usuarios por una función o un propósito de alto nivel para su organización.</span><span class="sxs-lookup"><span data-stu-id="69863-117">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="69863-p104">Además, algunos servicios en la nube se pueden compartir con usuarios externos a la organización sin cuentas de usuario. También necesitará identificar estos grupos de usuarios.</span><span class="sxs-lookup"><span data-stu-id="69863-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="69863-120">Puede usar grupos en Azure AD para varios fines que simplifican la administración del entorno de la nube.</span><span class="sxs-lookup"><span data-stu-id="69863-120">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="69863-121">Por ejemplo, con los grupos de Azure AD, puede:</span><span class="sxs-lookup"><span data-stu-id="69863-121">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="69863-122">Use licencias basadas en grupos para asignar licencias para Microsoft 365 a sus cuentas de usuario automáticamente en cuanto se agreguen como miembros.</span><span class="sxs-lookup"><span data-stu-id="69863-122">Use group-based licensing to assign licenses for Microsoft 365 to your user accounts automatically as soon as they are added as members.</span></span>
- <span data-ttu-id="69863-123">Agregue cuentas de usuario a grupos específicos de forma dinámica según los atributos de la cuenta de usuario, como el nombre del Departamento.</span><span class="sxs-lookup"><span data-stu-id="69863-123">Add user accounts to specific groups dynamically based on user account attributes, such as department name.</span></span>
- <span data-ttu-id="69863-124">Aprovisionar automáticamente a los usuarios para aplicaciones de software como servicio (SaaS) y para proteger el acceso a esas aplicaciones con multi-factor Authentication (MFA) y otras reglas de acceso condicional.</span><span class="sxs-lookup"><span data-stu-id="69863-124">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication (MFA) and other Conditional Access rules.</span></span>
- <span data-ttu-id="69863-125">Aprovisionar permisos y niveles de acceso para los sitios de grupo de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="69863-125">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="69863-126">***Los usuarios*** nuevos se crean con:</span><span class="sxs-lookup"><span data-stu-id="69863-126">You create new ***users*** with:</span></span>

- [<span data-ttu-id="69863-127">Centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="69863-127">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="69863-128">PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="69863-128">PowerShell for Microsoft 365</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="69863-129">Los nuevos ***grupos*** se crean con:</span><span class="sxs-lookup"><span data-stu-id="69863-129">You create new ***groups*** with:</span></span>

- [<span data-ttu-id="69863-130">Centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="69863-130">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="69863-131">PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="69863-131">PowerShell for Microsoft 365</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identity"></a><span data-ttu-id="69863-132">Paso siguiente para identidad solo de nube</span><span class="sxs-lookup"><span data-stu-id="69863-132">Next step for cloud-only identity</span></span>

[<span data-ttu-id="69863-133">Asignar licencias a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="69863-133">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
