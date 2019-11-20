---
title: Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/3/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
ms.collection:
- M365-security-compliance
description: Si ha habilitado la autenticación moderna híbrida (HMA) solo para encontrar que no es adecuada para su entorno actual, puede deshabilitar la HMA. En este artículo se explica cómo hacerlo.
ms.openlocfilehash: 72b902db04fd7c56d573d9df079f353a3f6cdc4f
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748398"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Si ha habilitado la autenticación moderna híbrida (HMA) solo para encontrar que no es adecuada para su entorno actual, puede deshabilitar la HMA. En este artículo se explica cómo hacerlo.
  
## <a name="who-is-this-article-for"></a>¿A quién está destinado este artículo?

Si ha habilitado la autenticación moderna en Skype empresarial online o local, y en Exchange online o local, y encuentra que necesita deshabilitar la HMA, estos pasos son para usted.

> [!IMPORTANT]
> Consulte el artículo "[topologías de Skype empresarial compatibles con la autenticación moderna](https://technet.microsoft.com/library/mt803262.aspx)" si está en Skype empresarial online o local, tiene un HMA de topología mixta y necesita mirar las topologías admitidas antes de empezar.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Cómo deshabilitar la autenticación moderna híbrida (Exchange)

1. **Exchange local**: Abra el shell de administración de Exchange y ejecute los siguientes comandos: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [conectarse a Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) con PowerShell remoto. Ejecute el siguiente comando para convertir la marca *OAuth2ClientProfileEnabled* en "false":

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Cómo deshabilitar la autenticación moderna híbrida (Skype empresarial)

1. **Skype empresarial local**: ejecute los siguientes comandos en el shell de administración de Skype empresarial:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype empresarial online**: [conectarse a Skype empresarial online](https://docs.microsoft.com/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) con PowerShell remoto. Ejecute el siguiente comando para deshabilitar la autenticación moderna:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Vínculo volver a la introducción a la autenticación moderna](hybrid-modern-auth-overview.md) . 
  

