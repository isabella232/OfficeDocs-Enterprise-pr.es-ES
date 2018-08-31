---
title: Use popouts lean para reducir la memoria usada al leer los mensajes de correo
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/8/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
description: Este artículo contiene información para mejorar el rendimiento de descarga de mensaje en Outlook en el web.
ms.openlocfilehash: 07c427793c1cd60d25020a1ab49855ed1bc77cf6
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542777"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="e75a5-103">Use popouts lean para reducir la memoria usada al leer los mensajes de correo</span><span class="sxs-lookup"><span data-stu-id="e75a5-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="e75a5-p101">Este artículo contiene información para mejorar el rendimiento de descarga de mensaje en Outlook en el web. En este artículo es parte del proyecto de [Diseño de la red y ajuste del rendimiento de Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="e75a5-p101">This article contains information for improving message download performance in Outlook on the web. This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
   
<span data-ttu-id="e75a5-p102">Como administrador global de Office 365, puede configurar Outlook en la web para ofrecer *popouts lean* , más pequeña y menos versión con uso intensivo de memoria de determinados mensajes de correo electrónico en Microsoft Edge o Internet Explorer. Cuando se configuran popouts lean para Outlook en la web, se cargan representan componentes del servidor que optimizar el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="e75a5-p102">As an Office 365 global administrator, you can configure Outlook on the web to deliver  *lean popouts*  , a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer. When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="e75a5-108">A partir de marzo de 2018, lean popouts actualmente no están disponibles para los mensajes que especifican restricciones de derechos de uso, como Information Rights Management (IRM).</span><span class="sxs-lookup"><span data-stu-id="e75a5-108">As of March 2018, lean popouts are currently not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span> 
  
<span data-ttu-id="e75a5-109">Estas características seguirán funcionando en la ventana principal, pero no están disponibles en popouts lean:</span><span class="sxs-lookup"><span data-stu-id="e75a5-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="e75a5-110">Complementos de Outlook</span><span class="sxs-lookup"><span data-stu-id="e75a5-110">Outlook add-ins</span></span>
    
- <span data-ttu-id="e75a5-111">Skype para la presencia de negocio</span><span class="sxs-lookup"><span data-stu-id="e75a5-111">Skype for Business presence</span></span>
    
 <span data-ttu-id="e75a5-112">**Para configurar lean popouts para todos los usuarios dentro de la organización de Office 365**</span><span class="sxs-lookup"><span data-stu-id="e75a5-112">**To configure lean popouts for all users within your Office 365 organization**</span></span>
  
1. <span data-ttu-id="e75a5-113">[Conectarse a Exchange Online mediante PowerShell remoto](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="e75a5-113">[Connect to Exchange Online Using Remote PowerShell](http://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
    
2. <span data-ttu-id="e75a5-114">Ejecute el cmdlet [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) con el parámetro LeanPopoutEnabled como sigue:</span><span class="sxs-lookup"><span data-stu-id="e75a5-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span> 
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

    <span data-ttu-id="e75a5-115">Por ejemplo, para habilitar lean popouts para todos los usuarios de su organización:</span><span class="sxs-lookup"><span data-stu-id="e75a5-115">For example, to enable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

    <span data-ttu-id="e75a5-116">Para deshabilitar lean popouts para todos los usuarios de su organización:</span><span class="sxs-lookup"><span data-stu-id="e75a5-116">To disable lean popouts for all users in your organization:</span></span>
    
  ```
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```


