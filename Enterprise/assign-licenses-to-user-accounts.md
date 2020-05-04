---
title: Asignar licencias de Office 365 a cuentas de usuario
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2019
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
description: Describe cómo asignar licencias de Office 365 a cuentas de usuario, ya sea de forma individual o en función de la pertenencia a grupos.
ms.openlocfilehash: 77e6f6c20e9eeff11487a31cb2d616abbed42601
ms.sourcegitcommit: 11751463c952f57f397b886eebfbd37790d461af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2020
ms.locfileid: "44009385"
---
# <a name="assign-office-365-licenses-to-user-accounts"></a><span data-ttu-id="eec96-103">Asignar licencias de Office 365 a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="eec96-103">Assign Office 365 licenses to user accounts</span></span>

<span data-ttu-id="eec96-104">*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="eec96-104">*This article applies to both Office 365 Enterprise and Microsoft 365 Enterprise.*</span></span>

<span data-ttu-id="eec96-105">Para el modelo de identidad solo de nube, puede asignar licencias de Office 365 a las cuentas de usuario a medida que se crean, en función de cómo las cree.</span><span class="sxs-lookup"><span data-stu-id="eec96-105">For the cloud-only identity model, you can assign Office 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="eec96-106">Para el modelo de identidad híbrida, cuando las cuentas de usuario de servicios de dominio de Active Directory (AD DS) se sincronizan por primera vez, no se les asigna automáticamente una licencia de Office 365.</span><span class="sxs-lookup"><span data-stu-id="eec96-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned an Office 365 license.</span></span>

<span data-ttu-id="eec96-107">En cualquier caso, debe asignar una licencia a las cuentas de usuario para que los usuarios puedan acceder a los servicios de Office 365, como el correo electrónico y Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="eec96-107">In either case, you must assign a license to user accounts so your users can access Office 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="eec96-108">Puede asignar licencias a cuentas de usuario, ya sea de forma individual o automática, a través de la pertenencia a grupos.</span><span class="sxs-lookup"><span data-stu-id="eec96-108">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="eec96-109">Para asignar licencias de Office 365 a cuentas de usuario individuales, puede usar:</span><span class="sxs-lookup"><span data-stu-id="eec96-109">To assign Office 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="eec96-110">Centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="eec96-110">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/office365/admin/subscriptions-and-billing/assign-licenses-to-users)
- [<span data-ttu-id="eec96-111">PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="eec96-111">Office 365 PowerShell</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="eec96-112">Para la asignación automática de licencias, consulte [licencias basadas en grupos en Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="eec96-112">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="eec96-113">Siguientes pasos</span><span class="sxs-lookup"><span data-stu-id="eec96-113">Next steps</span></span>

<span data-ttu-id="eec96-114">Con el conjunto completo de cuentas de usuario a las que se han asignado licencias, ya está listo para:</span><span class="sxs-lookup"><span data-stu-id="eec96-114">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="eec96-115">Implementar seguridad</span><span class="sxs-lookup"><span data-stu-id="eec96-115">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="eec96-116">Implementación de software cliente, como aplicaciones de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="eec96-116">Deploy client software, such as Microsoft 365 Apps</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [<span data-ttu-id="eec96-117">Configurar la administración de dispositivos móviles en Office 365</span><span class="sxs-lookup"><span data-stu-id="eec96-117">Set up Mobile Device Management in Office 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="eec96-118">Configuración de servicios y aplicaciones</span><span class="sxs-lookup"><span data-stu-id="eec96-118">Configure services and applications</span></span>](configure-services-and-applications.md)
