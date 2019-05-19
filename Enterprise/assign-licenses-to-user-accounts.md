---
title: Asignar licencias de Office 365 a cuentas de usuario
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
description: Describe cómo asignar licencias de Office 365 a cuentas de usuario, ya sea de forma individual o en función de la pertenencia a grupos.
ms.openlocfilehash: 0f258ef9240239ebdfa695e8c5b214484cfb4db1
ms.sourcegitcommit: 36e760407a1f4b18bc108134628ed9a8d3e35a8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2019
ms.locfileid: "34164605"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="965e5-103">Asignar licencias de Office 365 a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="965e5-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="965e5-104">Para el modelo de identidad solo de nube, puede asignar licencias de Office 365 a las cuentas de usuario a medida que se crean, en función de cómo las cree.</span><span class="sxs-lookup"><span data-stu-id="965e5-104">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="965e5-105">Para el modelo de identidad híbrida, cuando las cuentas de usuario de servicios de dominio de Active Directory (AD DS) se sincronizan por primera vez, no se les asigna automáticamente una licencia de Office 365.</span><span class="sxs-lookup"><span data-stu-id="965e5-105">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="965e5-106">En cualquier caso, debe asignar una licencia a las cuentas de usuario para que los usuarios puedan acceder a los servicios de Office 365, como el correo electrónico y Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="965e5-106">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="965e5-107">Puede asignar licencias a cuentas de usuario, ya sea de forma individual o automática, a través de la pertenencia a grupos.</span><span class="sxs-lookup"><span data-stu-id="965e5-107">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="965e5-108">Para asignar licencias de Office 365 a cuentas de usuario individuales, puede usar:</span><span class="sxs-lookup"><span data-stu-id="965e5-108">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="965e5-109">Centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="965e5-109">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="965e5-110">PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="965e5-110">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="965e5-111">Para la asignación automática de licencias, consulte [licencias basadas en grupos en Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="965e5-111">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="965e5-112">Siguientes pasos</span><span class="sxs-lookup"><span data-stu-id="965e5-112">Next steps</span></span>

<span data-ttu-id="965e5-113">Con el conjunto completo de cuentas de usuario a las que se han asignado licencias, ya está listo para:</span><span class="sxs-lookup"><span data-stu-id="965e5-113">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="965e5-114">Implementación de software de cliente, como Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="965e5-114">Deploy client software, such as Office 365 ProPlus</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-for-office-365-proplus)
- [<span data-ttu-id="965e5-115">Configuración de la administración de dispositivos móviles</span><span class="sxs-lookup"><span data-stu-id="965e5-115">Configure mobile device management</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="965e5-116">Configuración de servicios y aplicaciones</span><span class="sxs-lookup"><span data-stu-id="965e5-116">Configure services and applications</span></span>](configure-services-and-applications.md)
