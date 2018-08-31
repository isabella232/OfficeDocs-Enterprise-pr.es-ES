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
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="d9989-104">Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange</span><span class="sxs-lookup"><span data-stu-id="d9989-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="d9989-p102">Si ha habilitado híbrida moderno autenticación (HMA) sólo para buscar es adecuada para su entorno actual, puede deshabilitar HMA. En este artículo se explica cómo.</span><span class="sxs-lookup"><span data-stu-id="d9989-p102">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA. This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="d9989-107">¿Quién está destinado este artículo?</span><span class="sxs-lookup"><span data-stu-id="d9989-107">Who is this article for?</span></span>

<span data-ttu-id="d9989-108">Si ha habilitado la autenticación moderno en Skype para profesionales en línea o local, o Exchange Online o local y se encuentra que debe deshabilitar HMA, estos pasos son para usted.</span><span class="sxs-lookup"><span data-stu-id="d9989-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>
  
 <span data-ttu-id="d9989-109">**Importante** Vea el artículo ' [Skype para topologías empresariales compatibles con autenticación moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)' si se encuentra en Skype para profesionales en línea o local, tienen una topología mixta HMA y necesita buscar en las topologías admitidas antes de empezar.</span><span class="sxs-lookup"><span data-stu-id="d9989-109">**Important** See the ' [Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="d9989-110">Procedimiento para deshabilitar la autenticación de moderno híbrida (Exchange)</span><span class="sxs-lookup"><span data-stu-id="d9989-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="d9989-111">**Exchange local**: abra el Shell de administración de Exchange y ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="d9989-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following command.</span></span> 
    
1. <span data-ttu-id="d9989-112">Set-OrganizationConfig-OAuth2ClientProfileEnabled $false</span><span class="sxs-lookup"><span data-stu-id="d9989-112">Set-OrganizationConfig -OAuth2ClientProfileEnabled $false</span></span>
    
2. <span data-ttu-id="d9989-113">Set-AuthServer-evoSTS Identity - IsDefaultAuthorizationEndpoint $false</span><span class="sxs-lookup"><span data-stu-id="d9989-113">Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false</span></span>
    
2. <span data-ttu-id="d9989-p103">**Exchange Online**: conectarse a Exchange Online con PowerShell remoto. Ejecute el siguiente comando para activar la marca de *OAuth2ClientProfileEnabled* 'false'.</span><span class="sxs-lookup"><span data-stu-id="d9989-p103">**Exchange Online**: Connect to Exchange Online with Remote PowerShell. Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false'.</span></span> 
    
1. <span data-ttu-id="d9989-116">Set-OrganizationConfig-OAuth2ClientProfileEnabled: $false</span><span class="sxs-lookup"><span data-stu-id="d9989-116">Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false</span></span>
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="d9989-117">Procedimiento para deshabilitar la autenticación de moderno híbrida (Skype para la empresa)</span><span class="sxs-lookup"><span data-stu-id="d9989-117">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="d9989-118">**Skype para empresarial local**: ejecute los siguientes comandos en Skype para Shell de administración de negocio.</span><span class="sxs-lookup"><span data-stu-id="d9989-118">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell.</span></span>
    
1. <span data-ttu-id="d9989-119">Set-CsOAuthConfiguration - ClientAuthorizationOAuthServerIdentity ""</span><span class="sxs-lookup"><span data-stu-id="d9989-119">Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""</span></span>
    
2. <span data-ttu-id="d9989-p104">**Skype para la empresa en línea**: conectarse a Skype para la empresa en línea con PowerShell remoto. Ejecute el siguiente comando para deshabilitar la autenticación moderno.</span><span class="sxs-lookup"><span data-stu-id="d9989-p104">**Skype for Business Online**: Connect to Skype for Business Online with Remote PowerShell. Run the following command to disable Modern Authentication.</span></span> 
    
1. <span data-ttu-id="d9989-122">Set-CsOAuthConfiguration - ClientAdalAuthOverride no permitido</span><span class="sxs-lookup"><span data-stu-id="d9989-122">Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed</span></span>
    
<span data-ttu-id="d9989-123">[Vínculo hacia atrás a la introducción a la autenticación moderno](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="d9989-123">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

