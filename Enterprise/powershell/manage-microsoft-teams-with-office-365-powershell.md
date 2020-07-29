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
ms.sourcegitcommit: 132c97bd5e0dbe469da64356ace5084b71419cea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "45429215"
---
# <a name="manage-microsoft-teams-with-powershell"></a>Administrar Microsoft Teams con PowerShell

*Este artículo afecta tanto a Office 365 Enterprise como a Microsoft 365 Enterprise*

Puede administrar Microsoft Teams con PowerShell.
  
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


## <a name="see-also"></a>Recursos adicionales

[Información general sobre PowerShell de Teams](https://docs.microsoft.com/microsoftteams/teams-powershell-overview)
  
[Administrar Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)

