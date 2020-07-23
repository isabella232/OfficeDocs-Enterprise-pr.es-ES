---
title: Asignar licencias de 365 de Microsoft a cuentas de usuario
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
description: Describe cómo asignar licencias de 365 de Microsoft a cuentas de usuario, ya sea de forma individual o en función de la pertenencia a grupos.
ms.openlocfilehash: 3a51f4966cdcfede57ad8a69546face160ae1750
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230006"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts"></a><span data-ttu-id="d9774-103">Asignar licencias de 365 de Microsoft a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d9774-103">Assign Microsoft 365 licenses to user accounts</span></span>

<span data-ttu-id="d9774-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="d9774-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="d9774-105">Para el modelo de identidad solo de nube, puede asignar licencias de Microsoft 365 a las cuentas de usuario a medida que se crean, en función de cómo las cree.</span><span class="sxs-lookup"><span data-stu-id="d9774-105">For the cloud-only identity model, you can assign Microsoft 365 licenses to user accounts as they are created, depending on how you create them.</span></span>

<span data-ttu-id="d9774-106">Para el modelo de identidad híbrida, cuando las cuentas de usuario de servicios de dominio de Active Directory (AD DS) se sincronizan por primera vez, no se les asigna una licencia de Microsoft 365 automáticamente.</span><span class="sxs-lookup"><span data-stu-id="d9774-106">For the hybrid identity model, when Active Directory Domain Services (AD DS) user accounts are synchronized for the first time, they are not automatically assigned a Microsoft 365 license.</span></span> <span data-ttu-id="d9774-107">Primero debe configurar cada cuenta de usuario con una ubicación de usuario.</span><span class="sxs-lookup"><span data-stu-id="d9774-107">You must first configure each user account with a user location.</span></span>

<span data-ttu-id="d9774-108">En cualquier caso, debe asignar una licencia a las cuentas de usuario para que los usuarios puedan acceder a los servicios de Microsoft 365, como el correo electrónico y Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="d9774-108">In either case, you must assign a license to user accounts so your users can access Microsoft 365 services, such as email and Microsoft Teams.</span></span>

<span data-ttu-id="d9774-109">Puede asignar licencias a cuentas de usuario, ya sea de forma individual o automática, a través de la pertenencia a grupos.</span><span class="sxs-lookup"><span data-stu-id="d9774-109">You can assign licenses to user accounts either individually or automatically through group membership.</span></span>

<span data-ttu-id="d9774-110">Para asignar licencias de 365 de Microsoft a cuentas de usuario individuales, puede usar:</span><span class="sxs-lookup"><span data-stu-id="d9774-110">To assign Microsoft 365 licenses to individual user accounts, you can use:</span></span>

- [<span data-ttu-id="d9774-111">Centro de administración de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d9774-111">The Microsoft 365 admin center</span></span>](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users)
- [<span data-ttu-id="d9774-112">PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d9774-112">PowerShell for Microsoft 365</span></span>](https://docs.microsoft.com/office365/enterprise/powershell/assign-licenses-to-user-accounts-with-office-365-powershell)

<span data-ttu-id="d9774-113">Para la asignación automática de licencias, consulte [licencias basadas en grupos en Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span><span class="sxs-lookup"><span data-stu-id="d9774-113">For automatic license assignment, see [group-based licensing in Azure AD](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d9774-114">Pasos siguientes</span><span class="sxs-lookup"><span data-stu-id="d9774-114">Next steps</span></span>

<span data-ttu-id="d9774-115">Con el conjunto completo de cuentas de usuario a las que se han asignado licencias, ya está listo para:</span><span class="sxs-lookup"><span data-stu-id="d9774-115">With the full set of user accounts that have been assigned licenses, you are now ready to:</span></span>

- [<span data-ttu-id="d9774-116">Implementar seguridad</span><span class="sxs-lookup"><span data-stu-id="d9774-116">Implement security</span></span>](https://docs.microsoft.com/microsoft-365/security/office-365-security/security-roadmap)
- [<span data-ttu-id="d9774-117">Implementación de software cliente, como aplicaciones de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d9774-117">Deploy client software, such as Microsoft 365 Apps</span></span>](https://docs.microsoft.com/DeployOffice/deployment-guide-microsoft-365-apps)
- [<span data-ttu-id="d9774-118">Configurar la administración de dispositivos móviles en Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="d9774-118">Set up Mobile Device Management in Microsoft 365</span></span>](https://support.office.com/article/set-up-mobile-device-management-mdm-in-office-365-dd892318-bc44-4eb1-af00-9db5430be3cd)
- [<span data-ttu-id="d9774-119">Configuración de servicios y aplicaciones</span><span class="sxs-lookup"><span data-stu-id="d9774-119">Configure services and applications</span></span>](configure-services-and-applications.md)
