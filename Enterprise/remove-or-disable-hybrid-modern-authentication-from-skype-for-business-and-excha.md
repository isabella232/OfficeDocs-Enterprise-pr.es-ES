---
title: Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange
ms.author: tracyp
author: MSFTTracyP
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
ms.openlocfilehash: 011e24c546fede11177e49ce8b36599d7d81d121
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070986"
---
# <a name="removing-or-disabling-hybrid-modern-authentication-from-skype-for-business-and-exchange"></a><span data-ttu-id="c8439-104">Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange</span><span class="sxs-lookup"><span data-stu-id="c8439-104">Removing or disabling Hybrid Modern Authentication from Skype for Business and Exchange</span></span>

<span data-ttu-id="c8439-105">Si ha habilitado la autenticación moderna híbrida (HMA) solo para encontrar que no es adecuada para su entorno actual, puede deshabilitar la HMA.</span><span class="sxs-lookup"><span data-stu-id="c8439-105">If you've enabled Hybrid Modern Authentication (HMA) only to find it's unsuitable for your current environment, you can disable HMA.</span></span> <span data-ttu-id="c8439-106">En este artículo se explica cómo hacerlo.</span><span class="sxs-lookup"><span data-stu-id="c8439-106">This article explains how.</span></span>
  
## <a name="who-is-this-article-for"></a><span data-ttu-id="c8439-107">¿A quién está destinado este artículo?</span><span class="sxs-lookup"><span data-stu-id="c8439-107">Who is this article for?</span></span>

<span data-ttu-id="c8439-108">Si ha habilitado la autenticación moderna en Skype empresarial online o local, y en Exchange online o local, y encuentra que necesita deshabilitar la HMA, estos pasos son para usted.</span><span class="sxs-lookup"><span data-stu-id="c8439-108">If you've enabled Modern Authentication in Skype for Business Online or On-premises, and/or Exchange Online or On-premises and found you need to disable HMA, these steps are for you.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c8439-109">Consulte el artículo "[topologías de Skype empresarial compatibles con la autenticación moderna](https://technet.microsoft.com/en-us/library/mt803262.aspx)" si está en Skype empresarial online o local, tiene un HMA de topología mixta y necesita mirar las topologías admitidas antes de empezar.</span><span class="sxs-lookup"><span data-stu-id="c8439-109">See the '[Skype for Business topologies supported with Modern Authentication](https://technet.microsoft.com/en-us/library/mt803262.aspx)' article if you're in Skype for Business Online or On-premises, have a mixed-topology HMA, and need to look at supported topologies before you begin.</span></span>
  
## <a name="how-to-disable-hybrid-modern-authentication-exchange"></a><span data-ttu-id="c8439-110">Cómo deshabilitar la autenticación moderna híbrida (Exchange)</span><span class="sxs-lookup"><span data-stu-id="c8439-110">How to disable Hybrid Modern Authentication (Exchange)</span></span>

1. <span data-ttu-id="c8439-111">**Exchange local**: Abra el shell de administración de Exchange y ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="c8439-111">**Exchange On-premises**: Open the Exchange Management Shell and run the following commands:</span></span> 

```powershell
Set-OrganizationConfig -OAuth2ClientProfileEnabled $false
Set-AuthServer -Identity evoSTS -IsDefaultAuthorizationEndpoint $false
```

2. <span data-ttu-id="c8439-112">**Exchange Online**: [conectarse a Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) con PowerShell remoto.</span><span class="sxs-lookup"><span data-stu-id="c8439-112">**Exchange Online**: [Connect to Exchange Online](https://docs.microsoft.com/en-us/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="c8439-113">Ejecute el siguiente comando para convertir la marca *OAuth2ClientProfileEnabled* en "false":</span><span class="sxs-lookup"><span data-stu-id="c8439-113">Run the following command to turn your  *OAuth2ClientProfileEnabled*  flag to 'false':</span></span>

```powershell    
Set-OrganizationConfig -OAuth2ClientProfileEnabled:$false
```
    
## <a name="how-to-disable-hybrid-modern-authentication-skype-for-business"></a><span data-ttu-id="c8439-114">Cómo deshabilitar la autenticación moderna híbrida (Skype empresarial)</span><span class="sxs-lookup"><span data-stu-id="c8439-114">How to disable Hybrid Modern Authentication (Skype for Business)</span></span>

1. <span data-ttu-id="c8439-115">**Skype empresarial local**: ejecute los siguientes comandos en el shell de administración de Skype empresarial:</span><span class="sxs-lookup"><span data-stu-id="c8439-115">**Skype for Business On-premises**: Run the following commands in Skype for Business Management Shell:</span></span>

```powershell
Set-CsOAuthConfiguration -ClientAuthorizationOAuthServerIdentity ""
```

2. <span data-ttu-id="c8439-116">**Skype empresarial online**: [conectarse a Skype empresarial online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) con PowerShell remoto.</span><span class="sxs-lookup"><span data-stu-id="c8439-116">**Skype for Business Online**: [Connect to Skype for Business Online](https://docs.microsoft.com/en-us/office365/enterprise/powershell/manage-skype-for-business-online-with-office-365-powershell) with Remote PowerShell.</span></span> <span data-ttu-id="c8439-117">Ejecute el siguiente comando para deshabilitar la autenticación moderna:</span><span class="sxs-lookup"><span data-stu-id="c8439-117">Run the following command to disable Modern Authentication:</span></span>

```powershell    
Set-CsOAuthConfiguration -ClientAdalAuthOverride Disallowed
```

<span data-ttu-id="c8439-118">[Vínculo volver a la introducción a la autenticación moderna](hybrid-modern-auth-overview.md) .</span><span class="sxs-lookup"><span data-stu-id="c8439-118">[Link back to the Modern Authentication overview](hybrid-modern-auth-overview.md) .</span></span> 
  

