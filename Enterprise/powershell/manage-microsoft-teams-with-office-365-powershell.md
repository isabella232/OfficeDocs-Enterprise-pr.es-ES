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
# <a name="manage-microsoft-teams-with-office-365-powershell"></a>Administrar Microsoft Teams con Office 365 PowerShell

Puede administrar Microsoft Teams con Office 365 PowerShell.
  
En primer lugar, instale el [módulo de Microsoft Teams](https://www.powershellgallery.com/packages/MicrosoftTeams/).
    
## <a name="sign-in-with-a-user-name-and-password"></a>Iniciar sesión con un nombre de usuario y una contraseña

Para la nube de Office 365 en todo el mundo (+ GCC):

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred
```

Para la nube de Office 365 U.S. Government DoD: 

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsDOD
```

Para la oficina 365 para Estados Unidos GCC High Cloud:

```powershell
$cred=Get-Credential
Connect-MicrosoftTeams -Credential $cred -TeamsEnvironmentName TeamsGCCH
```

## <a name="sign-in-with-multi-factor-authentication-mfa"></a>Iniciar sesión con multi-factor Authentication (MFA)

Para la nube de Office 365 en todo el mundo (+ GCC):

```powershell
Connect-MicrosoftTeams
```

Para la nube de Office 365 U.S. Government DoD: 

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsDOD
```

Para la oficina 365 para Estados Unidos GCC High Cloud:

```powershell
Connect-MicrosoftTeams -TeamsEnvironmentName TeamsGCCH
```

## <a name="disconnect-from-microsoft-teams"></a>Desconexión de Microsoft Teams

Use este comando:

```powershell
Disconnect-MicrosoftTeams
```


## <a name="see-also"></a>Vea también

[Información general sobre PowerShell de Teams](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

