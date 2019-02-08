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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="64d63-104">Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange</span><span class="sxs-lookup"><span data-stu-id="64d63-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="64d63-p102">Si ha habilitado híbrida moderno autenticación (HMA) sólo para buscar es adecuada para su entorno actual, puede deshabilitar HMA. En este artículo se explica cómo.</span><span class="sxs-lookup"><span data-stu-id="64d63-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="64d63-107">¿Quién está destinado este artículo?</span><span class="sxs-lookup"><span data-stu-id="64d63-107">Who is this article for?</span></span>

<span data-ttu-id="64d63-108">Si ha habilitado la autenticación moderno en Skype para profesionales en línea o local, o Exchange Online o local y se encuentra que debe deshabilitar HMA, estos pasos son para usted.</span><span class="sxs-lookup"><span data-stu-id="64d63-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="64d63-109">Vea el artículo '[Skype para topologías empresariales compatibles con autenticación moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)' si se encuentra en Skype para profesionales en línea o local, tienen una topología mixta HMA y necesita buscar en las topologías admitidas antes de empezar.</span><span class="sxs-lookup"><span data-stu-id="64d63-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="64d63-110">Procedimiento para deshabilitar la autenticación de moderno híbrida (Exchange)</span><span class="sxs-lookup"><span data-stu-id="64d63-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="64d63-111">**Exchange local**: abra el Shell de administración de Exchange y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="64d63-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="64d63-p103">**Exchange Online**: [conectarse a Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) con PowerShell remoto. Ejecute el siguiente comando para activar la marca de *OAuth2ClientProfileEnabled* 'false':</span><span class="sxs-lookup"><span data-stu-id="64d63-p103">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="64d63-114">Procedimiento para deshabilitar la autenticación de moderno híbrida (Skype para la empresa)</span><span class="sxs-lookup"><span data-stu-id="64d63-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="64d63-115">**Skype para empresarial local**: ejecute los siguientes comandos en Skype para Shell de administración de negocio:</span><span class="sxs-lookup"><span data-stu-id="64d63-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="64d63-p104">**Skype para la empresa en línea**: [conectarse a Skype para la empresa en línea](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) con PowerShell remoto. Ejecute el siguiente comando para deshabilitar la autenticación moderno:</span><span class="sxs-lookup"><span data-stu-id="64d63-p104">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell. Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="64d63-118">[Vínculo hacia atrás a la introducción a la autenticación moderno](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="64d63-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

