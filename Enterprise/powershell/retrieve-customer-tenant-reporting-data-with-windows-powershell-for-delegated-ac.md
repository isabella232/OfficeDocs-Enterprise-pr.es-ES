---
title: Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Resumen: Use el modo remoto de Windows PowerShell para Microsoft Exchange Online para recuperar informes de inquilinos de cliente individuales.'
ms.openlocfilehash: d4b8d931b6b8ea8c7b8467dd70326e1b0fbfc3d5
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998629"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="9a996-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span><span class="sxs-lookup"><span data-stu-id="9a996-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="9a996-104">Use Windows PowerShell remoto para Microsoft Exchange Online para recuperar informes de inquilinos de cliente individuales.</span><span class="sxs-lookup"><span data-stu-id="9a996-104">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="9a996-105">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a996-105">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell.</span></span> <span data-ttu-id="9a996-106">This lets partners collect and save the reporting data and then perform other operations on it.</span><span class="sxs-lookup"><span data-stu-id="9a996-106">This lets partners collect and save the reporting data and then perform other operations on it.</span></span> <span data-ttu-id="9a996-107">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span><span class="sxs-lookup"><span data-stu-id="9a996-107">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="9a996-108">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span><span class="sxs-lookup"><span data-stu-id="9a996-108">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span></span> <span data-ttu-id="9a996-109">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span><span class="sxs-lookup"><span data-stu-id="9a996-109">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span></span> <span data-ttu-id="9a996-110">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span><span class="sxs-lookup"><span data-stu-id="9a996-110">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="9a996-111">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="9a996-111">Before you begin</span></span>

- <span data-ttu-id="9a996-112">You need to connect to your Exchange Online tenant by using remote Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a996-112">You need to connect to your Exchange Online tenant by using remote Windows PowerShell.</span></span> <span data-ttu-id="9a996-113">For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="9a996-113">For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="9a996-114">Ejecutar Get-StaleMailboxReport a modo de ejemplo</span><span class="sxs-lookup"><span data-stu-id="9a996-114">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="9a996-115">Después de abrir una sesión remota en Exchange Online, ejecute este comando para recuperar el elemento **Get-StaleMailboxReport** del intervalo de fechas entre el 25/03/2015 y el 31/03/2015.</span><span class="sxs-lookup"><span data-stu-id="9a996-115">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="9a996-116">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use.</span><span class="sxs-lookup"><span data-stu-id="9a996-116">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use.</span></span> <span data-ttu-id="9a996-117">To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span><span class="sxs-lookup"><span data-stu-id="9a996-117">To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9a996-118">Consulte también</span><span class="sxs-lookup"><span data-stu-id="9a996-118">See also</span></span>

#### 

[<span data-ttu-id="9a996-119">Servicio web de informes de Office 365</span><span class="sxs-lookup"><span data-stu-id="9a996-119">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="9a996-120">Cmdlets de informes en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="9a996-120">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="9a996-121">Ayuda para socios</span><span class="sxs-lookup"><span data-stu-id="9a996-121">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

