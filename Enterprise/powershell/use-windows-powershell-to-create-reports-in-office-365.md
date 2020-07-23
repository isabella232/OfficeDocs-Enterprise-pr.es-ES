---
title: Usar PowerShell para crear informes para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: ''
ms.assetid: 1ea4d4ec-af89-496f-9678-701867f5a6fc
description: 'Resumen: Use PowerShell para Microsoft 365 para crear informes que no puede producir en el centro de administración de Microsoft 365.'
ms.openlocfilehash: 855f6529445b95dd949fb672f978a82f1afd6149
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229806"
---
# <a name="use-powershell-to-create-reports-for-microsoft-365"></a><span data-ttu-id="243c8-103">Usar PowerShell para crear informes para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="243c8-103">Use PowerShell to create reports for Microsoft 365</span></span>

<span data-ttu-id="243c8-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="243c8-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="243c8-105">Existen muchos informes diferentes disponibles en el Centro de administración de Microsoft Office 365.</span><span class="sxs-lookup"><span data-stu-id="243c8-105">There are many different reports available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="243c8-106">Sin embargo, estos informes solo proporcionan demasiada información y a veces necesita más.</span><span class="sxs-lookup"><span data-stu-id="243c8-106">However, these reports only provide so much information and sometimes you need more.</span></span> <span data-ttu-id="243c8-107">Es cuando necesita PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="243c8-107">That's when you need PowerShell for Microsoft 365</span></span>
  
<span data-ttu-id="243c8-108">En estos artículos se describe cómo usar PowerShell para Microsoft 365 para obtener información de su inquilino de Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="243c8-108">These articles that describe how to use PowerShell for Microsoft 365 to obtain information from your Microsoft 365 tenant:</span></span>
  
- <span data-ttu-id="243c8-109">Introducción a los informes con PowerShell para Microsoft 365:</span><span class="sxs-lookup"><span data-stu-id="243c8-109">Getting started with reporting using PowerShell for Microsoft 365:</span></span>
    
  - [<span data-ttu-id="243c8-110">PowerShell para Microsoft 365 puede revelar información adicional que no puede ver con el centro de administración</span><span class="sxs-lookup"><span data-stu-id="243c8-110">PowerShell for Microsoft 365 can reveal additional information that you cannot see with the Admin center</span></span>](https://technet.microsoft.com/library/dn568034.aspx#reveal)
    
  - [<span data-ttu-id="243c8-111">PowerShell para Microsoft 365 es excelente en el filtrado de datos</span><span class="sxs-lookup"><span data-stu-id="243c8-111">PowerShell for Microsoft 365 is great at filtering data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#filter)
    
  - [<span data-ttu-id="243c8-112">PowerShell para Microsoft 365 simplifica la tarea de imprimir o guardar datos</span><span class="sxs-lookup"><span data-stu-id="243c8-112">PowerShell for Microsoft 365 makes it easy to print or save data</span></span>](https://technet.microsoft.com/library/dn568034.aspx#printsave)
    
- <span data-ttu-id="243c8-113">Informes para licencias y cuentas de usuario:</span><span class="sxs-lookup"><span data-stu-id="243c8-113">Reports for user accounts and licenses:</span></span>
    
  - [<span data-ttu-id="243c8-114">Ver licencias y servicios de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-114">View Microsoft 365 licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="243c8-115">Ver los usuarios con licencia y sin licencia de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-115">View Microsoft 365 licensed and unlicensed users with PowerShell</span></span>](view-licensed-and-unlicensed-users-with-office-365-powershell.md)
    
  - [<span data-ttu-id="243c8-116">Ver los detalles del servicio y la licencia de la cuenta 365 de Microsoft con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-116">View Microsoft 365 account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
  - [<span data-ttu-id="243c8-117">Ver cuentas de usuario 365 de Microsoft con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-117">View Microsoft 365 user accounts with PowerShell</span></span>](view-user-accounts-with-office-365-powershell.md)
    
- <span data-ttu-id="243c8-118">Informes de SharePoint Online:</span><span class="sxs-lookup"><span data-stu-id="243c8-118">Reports for SharePoint Online:</span></span>
    
  - [<span data-ttu-id="243c8-119">Introducción al Shell de administración de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="243c8-119">Get started with SharePoint Online Management Shell</span></span>](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online)
    
  - [<span data-ttu-id="243c8-120">Administrar grupos de sitio de SharePoint Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-120">Manage SharePoint Online site groups with PowerShell</span></span>](https://technet.microsoft.com/library/122f4099-c78d-4cce-bab0-4343b04596ae.aspx)
    
- <span data-ttu-id="243c8-121">Informes de Exchange Online:</span><span class="sxs-lookup"><span data-stu-id="243c8-121">Reports for Exchange Online:</span></span>
    
  - [<span data-ttu-id="243c8-122">Mostrar información del buzón de Exchange Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-122">Display Exchange Online mailbox information with PowerShell</span></span>](https://technet.microsoft.com/library/13843002-56ca-4b75-81c5-84386522b01b.aspx)
    
  - [<span data-ttu-id="243c8-123">Mostrar informes de Exchange Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-123">Display Exchange Online reports with PowerShell</span></span>](https://technet.microsoft.com/library/4873a063-9fc4-4ed9-826a-6e935fef61d4.aspx)
    
## <a name="see-also"></a><span data-ttu-id="243c8-124">Consulte también</span><span class="sxs-lookup"><span data-stu-id="243c8-124">See also</span></span>

[<span data-ttu-id="243c8-125">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-125">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="243c8-126">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="243c8-126">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
  
[<span data-ttu-id="243c8-127">Administrar SharePoint Online con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-127">Manage SharePoint Online with PowerShell</span></span>](manage-sharepoint-online-with-office-365-powershell.md)
  
[<span data-ttu-id="243c8-128">Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="243c8-128">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
