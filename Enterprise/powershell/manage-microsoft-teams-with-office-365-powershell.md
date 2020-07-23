---
title: Administrar Microsoft Teams con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Resumen: Use PowerShell para administrar Microsoft Teams.'
ms.openlocfilehash: 8958c6ec6f0c17c21461cbee4cb1a6441ceed8d6
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230616"
---
# <a name="manage-microsoft-teams-with-powershell"></a><span data-ttu-id="e7666-103">Administrar Microsoft Teams con PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7666-103">Manage Microsoft Teams with PowerShell</span></span>

<span data-ttu-id="e7666-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="e7666-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="e7666-105">Puede administrar Microsoft Teams con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e7666-105">You can manage Microsoft Teams with PowerShell.</span></span>
  
<span data-ttu-id="e7666-106">En primer lugar, instale el [módulo de Microsoft Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="e7666-106">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="e7666-107">Iniciar sesión con un nombre de usuario y una contraseña</span><span class="sxs-lookup"><span data-stu-id="e7666-107">Sign in with a user name and password</span></span>

<span data-ttu-id="e7666-108">Para la nube de Office 365 en todo el mundo (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="e7666-108">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="e7666-109">Para la nube de Office 365 U.S. Government DoD:</span><span class="sxs-lookup"><span data-stu-id="e7666-109">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="e7666-110">Para la oficina 365 para Estados Unidos GCC High Cloud:</span><span class="sxs-lookup"><span data-stu-id="e7666-110">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="e7666-111">Iniciar sesión con multi-factor Authentication (MFA)</span><span class="sxs-lookup"><span data-stu-id="e7666-111">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="e7666-112">Para la nube de Office 365 en todo el mundo (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="e7666-112">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="e7666-113">Para la nube de Office 365 U.S. Government DoD:</span><span class="sxs-lookup"><span data-stu-id="e7666-113">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="e7666-114">Para la oficina 365 para Estados Unidos GCC High Cloud:</span><span class="sxs-lookup"><span data-stu-id="e7666-114">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="e7666-115">Desconexión de Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e7666-115">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="e7666-116">Use este comando:</span><span class="sxs-lookup"><span data-stu-id="e7666-116">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="e7666-117">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e7666-117">See also</span></span>

[<span data-ttu-id="e7666-118">Información general sobre PowerShell de Teams</span><span class="sxs-lookup"><span data-stu-id="e7666-118">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="e7666-119">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7666-119">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e7666-120">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="e7666-120">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

