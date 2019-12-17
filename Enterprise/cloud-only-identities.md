---
title: Identidades de solo nube de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
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
ms.openlocfilehash: 5991ec838321187b58f913e1707efb2ede9912fb
ms.sourcegitcommit: 3539ec707f984de6f3b874744ff8b6832fbd665e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/17/2019
ms.locfileid: "40072282"
---
# <a name="office-365-cloud-only-identities"></a><span data-ttu-id="df63b-103">Identidades de solo nube de Office 365</span><span class="sxs-lookup"><span data-stu-id="df63b-103">Office 365 cloud-only identities</span></span>

<span data-ttu-id="df63b-104">*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="df63b-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="df63b-105">Con la identidad solo de nube, todos los usuarios, grupos y contactos se almacenan en el inquilino de Azure Active Directory (Azure AD) de la suscripción a Office 365.</span><span class="sxs-lookup"><span data-stu-id="df63b-105">With cloud-only identity, all your users, groups, and contacts are stored in the Azure Active Directory (Azure AD) tenant of your Office 365 subscription.</span></span> <span data-ttu-id="df63b-106">Estos son los componentes básicos de la identidad solo de la nube.</span><span class="sxs-lookup"><span data-stu-id="df63b-106">Here are the basic components of cloud-only identity.</span></span>
 
![Los componentes básicos de la identidad solo de nube](./media/about-office-365-identity/cloud-only-identity.png)

<span data-ttu-id="df63b-108">Los usuarios y sus cuentas de usuario en las organizaciones se pueden clasificar de varias formas.</span><span class="sxs-lookup"><span data-stu-id="df63b-108">Users and their user accounts in organizations can be categorized in a number of ways.</span></span> <span data-ttu-id="df63b-109">Por ejemplo, algunos son empleados y tienen un estado permanente.</span><span class="sxs-lookup"><span data-stu-id="df63b-109">For example, some are employees and have a permanent status.</span></span> <span data-ttu-id="df63b-110">Algunos son proveedores, contratistas o asociados que tienen un estado temporal.</span><span class="sxs-lookup"><span data-stu-id="df63b-110">Some are vendors, contractors, or partners that have a temporary status.</span></span> <span data-ttu-id="df63b-111">Algunos son usuarios externos que no tienen cuentas de usuario, pero tienen que seguir concedido el acceso a servicios y recursos específicos para admitir la interacción y la colaboración.</span><span class="sxs-lookup"><span data-stu-id="df63b-111">Some are external users that have no user accounts but must still be granted access to specific services and resources to support interaction and collaboration.</span></span> <span data-ttu-id="df63b-112">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="df63b-112">For example:</span></span>

- <span data-ttu-id="df63b-113">Cuentas de espacio empresarial que representan a usuarios de su organización a los que asigna una licencia para servicios en la nube</span><span class="sxs-lookup"><span data-stu-id="df63b-113">Tenant accounts represent users within your organization that you license for cloud services</span></span>

- <span data-ttu-id="df63b-114">Las cuentas de empresa a empresa (B2B) representan a los usuarios externos a la organización que invita a participar en la colaboración a los tipos de usuarios de la organización.</span><span class="sxs-lookup"><span data-stu-id="df63b-114">Business to Business (B2B) accounts represent users outside your organization that you invite to participate in collaboration Take stock of the types of users to your organization.</span></span> <span data-ttu-id="df63b-115">¿Cuáles son las agrupaciones?</span><span class="sxs-lookup"><span data-stu-id="df63b-115">What are the groupings?</span></span> <span data-ttu-id="df63b-116">Por ejemplo, puede agrupar a los usuarios por una función o un propósito de alto nivel para su organización.</span><span class="sxs-lookup"><span data-stu-id="df63b-116">For example, you can group users by high-level function or purpose to your organization.</span></span>

<span data-ttu-id="df63b-p104">Además, algunos servicios en la nube se pueden compartir con usuarios externos a la organización sin cuentas de usuario. También necesitará identificar estos grupos de usuarios.</span><span class="sxs-lookup"><span data-stu-id="df63b-p104">Additionally, some cloud services can be shared with users outside your organization without any user accounts. You'll need to identify these groups of users as well.</span></span>

<span data-ttu-id="df63b-119">Puede usar grupos en Azure AD para varios fines que simplifican la administración del entorno de la nube.</span><span class="sxs-lookup"><span data-stu-id="df63b-119">You can use groups in Azure AD for several purposes that simplify management of your cloud environment.</span></span> <span data-ttu-id="df63b-120">Por ejemplo, con los grupos de Azure AD, puede:</span><span class="sxs-lookup"><span data-stu-id="df63b-120">For example, with Azure AD groups, you can:</span></span>

- <span data-ttu-id="df63b-121">Use licencias basadas en grupos para asignar licencias de Office 365 a sus cuentas de usuario automáticamente en cuanto se agreguen.</span><span class="sxs-lookup"><span data-stu-id="df63b-121">Use group-based licensing to assign licenses for Office 365 to your user accounts automatically as soon as they are added.</span></span>
- <span data-ttu-id="df63b-122">Agregar cuentas de usuario a grupos específicos dinámicamente basándose en los atributos de cuenta de usuario, como el departamento.</span><span class="sxs-lookup"><span data-stu-id="df63b-122">Add user accounts to specific groups dynamically based on user account attributes, such as department.</span></span>
- <span data-ttu-id="df63b-123">Aprovisionar automáticamente usuarios para aplicaciones de software como servicio (SaaS) y proteger el acceso a esas aplicaciones con autenticación multifactor y otras reglas de acceso condicional.</span><span class="sxs-lookup"><span data-stu-id="df63b-123">Automatically provision users for Software as a Service (SaaS) applications and to protect access to those applications with multi-factor authentication and other conditional access rules.</span></span>
- <span data-ttu-id="df63b-124">Aprovisionar permisos y niveles de acceso para los sitios de grupo de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="df63b-124">Provision permissions and levels of access for SharePoint Online team sites.</span></span>

<span data-ttu-id="df63b-125">Puede crear nuevos ***usuarios*** con:</span><span class="sxs-lookup"><span data-stu-id="df63b-125">You can create new ***users*** with:</span></span>

- [<span data-ttu-id="df63b-126">Centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="df63b-126">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/add-users/add-users)
- [<span data-ttu-id="df63b-127">PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="df63b-127">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell)

<span data-ttu-id="df63b-128">Puede crear ***grupos*** nuevos con:</span><span class="sxs-lookup"><span data-stu-id="df63b-128">You can create new ***groups*** with:</span></span>

- [<span data-ttu-id="df63b-129">Centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="df63b-129">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/create-groups/create-groups)
- [<span data-ttu-id="df63b-130">PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="df63b-130">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-groups-with-powershell)


## <a name="next-step-for-cloud-only-identities"></a><span data-ttu-id="df63b-131">Paso siguiente para identidades solo en la nube</span><span class="sxs-lookup"><span data-stu-id="df63b-131">Next step for cloud-only identities</span></span>

[<span data-ttu-id="df63b-132">Asignar licencias a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="df63b-132">Assign licenses to user accounts</span></span>](assign-licenses-to-user-accounts.md)
