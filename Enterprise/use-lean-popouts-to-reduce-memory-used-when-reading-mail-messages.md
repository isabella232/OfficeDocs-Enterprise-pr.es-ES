---
title: Usar lean ventanas emergentes para reducir la memoria usada al leer mensajes de correo
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/3/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: a6d6ba01-2562-4c3d-a8f1-78748dd506cf
f1.keywords:
- NOCSH
description: Este artículo contiene información para usar lean ventanas emergentes para mejorar el rendimiento de la descarga de mensajes en Outlook en la Web.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e9ca2f90c8798c144f2763106c4c9ca9f57e9df1
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603612"
---
# <a name="use-lean-popouts-to-reduce-memory-used-when-reading-mail-messages"></a><span data-ttu-id="add09-103">Usar lean ventanas emergentes para reducir la memoria usada al leer mensajes de correo</span><span class="sxs-lookup"><span data-stu-id="add09-103">Use lean popouts to reduce memory used when reading mail messages</span></span>

<span data-ttu-id="add09-104">Este artículo contiene información para mejorar el rendimiento de la descarga de mensajes en Outlook en la Web.</span><span class="sxs-lookup"><span data-stu-id="add09-104">This article contains information for improving message download performance in Outlook on the web.</span></span> <span data-ttu-id="add09-105">Este artículo forma parte del proyecto [planeación de red y ajuste del rendimiento para Office 365](https://aka.ms/tune) .</span><span class="sxs-lookup"><span data-stu-id="add09-105">This article is part of the [Network planning and performance tuning for Office 365](https://aka.ms/tune) project.</span></span>
  
<span data-ttu-id="add09-106">Como administrador global de Office 365, puede configurar Outlook en la web para que ofrezca _ventanas emergentes lean_, una versión más pequeña y que consume menos memoria de determinados mensajes de correo electrónico en Microsoft Edge o Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="add09-106">As an Office 365 global administrator, you can configure Outlook on the web to deliver _lean popouts_, a smaller, less memory-intensive version of certain email messages in Microsoft Edge or Internet Explorer.</span></span> <span data-ttu-id="add09-107">Cuando se configuran los ventanas emergentes Lean para Outlook en la web, se cargan los componentes representados del lado servidor que optimizan el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="add09-107">When lean popouts are configured for Outlook on the web, server-side rendered components are loaded that optimize performance.</span></span>
  
> [!NOTE]
> <span data-ttu-id="add09-108">A partir del 2018 de marzo, los ventanas emergentes lean no están disponibles para los mensajes que especifican restricciones de derechos de uso, como Information Rights Management (IRM).</span><span class="sxs-lookup"><span data-stu-id="add09-108">As of March 2018, lean popouts are not available for messages that specify usage rights restrictions, such as Information Rights Management (IRM).</span></span>
  
<span data-ttu-id="add09-109">Estas características seguirán funcionando en la ventana principal, pero no estarán disponibles en Lean ventanas emergentes:</span><span class="sxs-lookup"><span data-stu-id="add09-109">These features will continue to work in the main window but are not available in lean popouts:</span></span>
  
- <span data-ttu-id="add09-110">Complementos de Outlook</span><span class="sxs-lookup"><span data-stu-id="add09-110">Outlook add-ins</span></span>
  
- <span data-ttu-id="add09-111">Presencia de Skype empresarial</span><span class="sxs-lookup"><span data-stu-id="add09-111">Skype for Business presence</span></span>
  
## <a name="to-configure-lean-popouts-for-all-users-within-your-office-365-organization"></a><span data-ttu-id="add09-112">Para configurar ventanas emergentes eficaces para todos los usuarios de la organización de Office 365</span><span class="sxs-lookup"><span data-stu-id="add09-112">To configure lean popouts for all users within your Office 365 organization</span></span>
  
1. <span data-ttu-id="add09-113">[Conéctese a Exchange online mediante PowerShell remoto](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span><span class="sxs-lookup"><span data-stu-id="add09-113">[Connect to Exchange Online Using Remote PowerShell](https://technet.microsoft.com/library/jj984289%28v=exchg.150%29.aspx ).</span></span>
  
2. <span data-ttu-id="add09-114">Ejecute el cmdlet [set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) con el parámetro LeanPopoutEnabled de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="add09-114">Run the [Set-OrganizationConfig](https://technet.microsoft.com/library/aa997443%28v=exchg.160%29.aspx) cmdlet with the LeanPopoutEnabled parameter as follows:</span></span>

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled <$true |$false >
  ```

  <span data-ttu-id="add09-115">Por ejemplo, para habilitar la ventanas emergentes Lean para todos los usuarios de la organización:</span><span class="sxs-lookup"><span data-stu-id="add09-115">For example, to enable lean popouts for all users in your organization:</span></span>
  
  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $true
  ```

  <span data-ttu-id="add09-116">Para deshabilitar la ventanas emergentes eficiente para todos los usuarios de la organización:</span><span class="sxs-lookup"><span data-stu-id="add09-116">To disable lean popouts for all users in your organization:</span></span>

  ```powershell
  Set-OrganizationConfig -LeanPopoutEnabled $false
  ```
