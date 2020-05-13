---
title: Administrar Microsoft Teams con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Resumen: Use Office 365 PowerShell para administrar Microsoft Teams.'
ms.openlocfilehash: 0f15d71558ddb5166090b067da06e0a6321a2b99
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2020
ms.locfileid: "44209130"
---
# <a name="manage-microsoft-teams-with-office-365-powershell"></a><span data-ttu-id="94adc-103">Administrar Microsoft Teams con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="94adc-103">Manage Microsoft Teams with Office 365 PowerShell</span></span>

<span data-ttu-id="94adc-104">Puede administrar Microsoft Teams con Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="94adc-104">You can manage Microsoft Teams with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="94adc-105">En primer lugar, instale el [módulo de Microsoft Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span><span class="sxs-lookup"><span data-stu-id="94adc-105">First, install the [Microsoft Teams module](https://www.powershellgallery.com/packages/MicrosoftTeams/).</span></span>
    
## <a name="sign-in-with-a-user-name-and-password"></a><span data-ttu-id="94adc-106">Iniciar sesión con un nombre de usuario y una contraseña</span><span class="sxs-lookup"><span data-stu-id="94adc-106">Sign in with a user name and password</span></span>

<span data-ttu-id="94adc-107">Para la nube de Office 365 en todo el mundo (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="94adc-107">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

<span data-ttu-id="94adc-108">Para la nube de Office 365 U.S. Government DoD:</span><span class="sxs-lookup"><span data-stu-id="94adc-108">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="94adc-109">Para la oficina 365 para Estados Unidos GCC High Cloud:</span><span class="sxs-lookup"><span data-stu-id="94adc-109">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a><span data-ttu-id="94adc-110">Iniciar sesión con multi-factor Authentication (MFA)</span><span class="sxs-lookup"><span data-stu-id="94adc-110">Sign in with multi-factor authentication (MFA)</span></span>

<span data-ttu-id="94adc-111">Para la nube de Office 365 en todo el mundo (+ GCC):</span><span class="sxs-lookup"><span data-stu-id="94adc-111">For the Office 365 Worldwide (+GCC) cloud:</span></span>

```powershell
Connect-MicrosoftTeams
```

<span data-ttu-id="94adc-112">Para la nube de Office 365 U.S. Government DoD:</span><span class="sxs-lookup"><span data-stu-id="94adc-112">For the Office 365 U.S. Government DoD cloud:</span></span> 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

<span data-ttu-id="94adc-113">Para la oficina 365 para Estados Unidos GCC High Cloud:</span><span class="sxs-lookup"><span data-stu-id="94adc-113">For the Office 365 U.S. Government GCC High cloud:</span></span>

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a><span data-ttu-id="94adc-114">Desconexión de Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="94adc-114">Disconnect from Microsoft Teams</span></span>

<span data-ttu-id="94adc-115">Use este comando:</span><span class="sxs-lookup"><span data-stu-id="94adc-115">Use this command:</span></span>

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a><span data-ttu-id="94adc-116">Vea también</span><span class="sxs-lookup"><span data-stu-id="94adc-116">See also</span></span>

[<span data-ttu-id="94adc-117">Información general sobre PowerShell de Teams</span><span class="sxs-lookup"><span data-stu-id="94adc-117">Teams PowerShell Overview</span></span>](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[<span data-ttu-id="94adc-118">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="94adc-118">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="94adc-119">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="94adc-119">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

