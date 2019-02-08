---
title: Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 11/3/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5a91b9e3-1508-475b-93e0-710fa5d5cd2d
description: Si ha habilitado híbrida moderno autenticación (HMA) sólo para buscar es adecuada para su entorno actual, puede deshabilitar HMA. En este artículo se explica cómo.
ms.openlocfilehash: 802add6295edffe3ec80e70e9bd70663479ec61a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25359032"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange

Si ha habilitado híbrida moderno autenticación (HMA) sólo para buscar es adecuada para su entorno actual, puede deshabilitar HMA. En este artículo se explica cómo.
  
## <a name="who-is-this-article-for"></a>¿Quién está destinado este artículo?

Si ha habilitado la autenticación moderno en Skype para profesionales en línea o local, o Exchange Online o local y se encuentra que debe deshabilitar HMA, estos pasos son para usted.

> [!IMPORTANT]
> Vea el artículo '[Skype para topologías empresariales compatibles con autenticación moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)' si se encuentra en Skype para profesionales en línea o local, tienen una topología mixta HMA y necesita buscar en las topologías admitidas antes de empezar.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Procedimiento para deshabilitar la autenticación de moderno híbrida (Exchange)

1. **Exchange local**: abra el Shell de administración de Exchange y ejecute los siguientes comandos: 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. **Exchange Online**: [conectarse a Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) con PowerShell remoto. Ejecute el siguiente comando para activar la marca de *OAuth2ClientProfileEnabled* 'false':

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Procedimiento para deshabilitar la autenticación de moderno híbrida (Skype para la empresa)

1. **Skype para empresarial local**: ejecute los siguientes comandos en Skype para Shell de administración de negocio:

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. **Skype para la empresa en línea**: [conectarse a Skype para la empresa en línea](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) con PowerShell remoto. Ejecute el siguiente comando para deshabilitar la autenticación moderno:

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

[Vínculo hacia atrás a la introducción a la autenticación moderno](hybrid-modern-auth-overview.md) . 
  

