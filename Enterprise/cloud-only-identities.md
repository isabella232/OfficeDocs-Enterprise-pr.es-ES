---
title: Identidades de solo nube de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Describe cómo crear usuarios y grupos cuando la suscripción de Office 365 usa identidades de solo nube.
ms.openlocfilehash: 7a2aaf7705378da3cbd91b415f07d10b6e039293
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164615"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="d8190-103">Identidades de solo nube de Office 365</span><span class="sxs-lookup"><span data-stu-id="d8190-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="d8190-104">Con la identidad solo de nube, todos los usuarios, grupos y contactos se almacenan en el inquilino de Azure Active Directory (Azure AD) de la suscripción a Office 365.</span><span class="sxs-lookup"><span data-stu-id="d8190-104">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="d8190-105">Estos son los componentes básicos de la identidad solo de la nube.</span><span class="sxs-lookup"><span data-stu-id="d8190-105">Here are the basic components of cloud-only identity.</span></span>
 
![](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="d8190-106">Los usuarios y sus cuentas de usuario en las organizaciones se pueden clasificar de varias formas.</span><span class="sxs-lookup"><span data-stu-id="d8190-106">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="d8190-107">Por ejemplo, algunos son empleados y tienen un estado permanente.</span><span class="sxs-lookup"><span data-stu-id="d8190-107">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="d8190-108">Algunos son proveedores, contratistas o asociados que tienen un estado temporal.</span><span class="sxs-lookup"><span data-stu-id="d8190-108">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="d8190-109">Algunos son usuarios externos que no tienen cuentas de usuario, pero tienen que seguir concedido el acceso a servicios y recursos específicos para admitir la interacción y la colaboración.</span><span class="sxs-lookup"><span data-stu-id="d8190-109">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="d8190-110">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d8190-110">For example:</span></span>

- <span data-ttu-id="d8190-111">Cuentas de espacio empresarial que representan a usuarios de su organización a los que asigna una licencia para servicios en la nube</span><span class="sxs-lookup"><span data-stu-id="d8190-111">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="d8190-112">Las cuentas de empresa a empresa (B2B) representan a los usuarios externos a la organización que invita a participar en la colaboración a los tipos de usuarios de la organización.</span><span class="sxs-lookup"><span data-stu-id="d8190-112">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="d8190-113">¿Cuáles son las agrupaciones?</span><span class="sxs-lookup"><span data-stu-id="d8190-113">What are the groupings?</span></span> <span data-ttu-id="d8190-114">Por ejemplo, puede agrupar a los usuarios por una función o un propósito de alto nivel para su organización.</span><span class="sxs-lookup"><span data-stu-id="d8190-114">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="d8190-p104">Además, algunos servicios en la nube se pueden compartir con usuarios externos a la organización sin cuentas de usuario. También necesitará identificar estos grupos de usuarios.</span><span class="sxs-lookup"><span data-stu-id="d8190-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="d8190-117">Puede usar grupos en Azure AD para varios fines que simplifican la administración del entorno de la nube.</span><span class="sxs-lookup"><span data-stu-id="d8190-117">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="d8190-118">Por ejemplo, con los grupos de Azure AD, puede:</span><span class="sxs-lookup"><span data-stu-id="d8190-118">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="d8190-119">Use licencias basadas en grupos para asignar licencias de Office 365 a sus cuentas de usuario automáticamente en cuanto se agreguen.</span><span class="sxs-lookup"><span data-stu-id="d8190-119">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="d8190-120">Agregar cuentas de usuario a grupos específicos dinámicamente basándose en los atributos de cuenta de usuario, como el departamento.</span><span class="sxs-lookup"><span data-stu-id="d8190-120">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="d8190-121">Aprovisionar automáticamente usuarios para aplicaciones de software como servicio (SaaS) y proteger el acceso a esas aplicaciones con autenticación multifactor y otras reglas de acceso condicional.</span><span class="sxs-lookup"><span data-stu-id="d8190-121">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="d8190-122">Aprovisionar permisos y niveles de acceso para los sitios de grupo de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="d8190-122">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="d8190-123">Puede crear nuevos ***usuarios*** con:</span><span class="sxs-lookup"><span data-stu-id="d8190-123">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="d8190-124">Centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d8190-124">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="d8190-125">PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d8190-125">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="d8190-126">Puede crear ***grupos*** nuevos con:</span><span class="sxs-lookup"><span data-stu-id="d8190-126">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="d8190-127">Centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d8190-127">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="d8190-128">PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d8190-128">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="d8190-129">Paso siguiente para identidades solo en la nube</span><span class="sxs-lookup"><span data-stu-id="d8190-129">Next step for cloud-only identities</span></span>

[<span data-ttu-id="d8190-130">Asignar licencias a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d8190-130">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
