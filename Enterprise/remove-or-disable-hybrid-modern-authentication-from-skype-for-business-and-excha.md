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
ms.openlocfilehash: fff9599641630386183ab9e1a0b8f597f0ba6e5b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542943"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a>Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange

Si ha habilitado híbrida moderno autenticación (HMA) sólo para buscar es adecuada para su entorno actual, puede deshabilitar HMA. En este artículo se explica cómo.
  
## <a name="who-is-this-article-for"></a>¿Quién está destinado este artículo?

Si ha habilitado la autenticación moderno en Skype para profesionales en línea o local, o Exchange Online o local y se encuentra que debe deshabilitar HMA, estos pasos son para usted.
  
 **Importante** Vea el artículo ' [Skype para topologías empresariales compatibles con autenticación moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)' si se encuentra en Skype para profesionales en línea o local, tienen una topología mixta HMA y necesita buscar en las topologías admitidas antes de empezar.
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a>Procedimiento para deshabilitar la autenticación de moderno híbrida (Exchange)

1. **Exchange local**: abra el Shell de administración de Exchange y ejecute el siguiente comando. 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled $false
    
2. Set-AuthServer-evoSTS Identity - IsDefaultAuthorizationEndpoint $false
    
2. **Exchange Online**: conectarse a Exchange Online con PowerShell remoto. Ejecute el siguiente comando para activar la marca de *OAuth2ClientProfileEnabled* 'false'. 
    
1. Set-OrganizationConfig-OAuth2ClientProfileEnabled: $false
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a>Procedimiento para deshabilitar la autenticación de moderno híbrida (Skype para la empresa)

1. **Skype para empresarial local**: ejecute los siguientes comandos en Skype para Shell de administración de negocio.
    
1. Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity ""
    
2. **Skype para la empresa en línea**: conectarse a Skype para la empresa en línea con PowerShell remoto. Ejecute el siguiente comando para deshabilitar la autenticación moderno. 
    
1. Set-CsOAuthConfiguration - ClientAdalAuthOverride no permitido
    
[Vínculo hacia atrás a la introducción a la autenticación moderno](hybrid-modern-auth-overview.md) . 
  

