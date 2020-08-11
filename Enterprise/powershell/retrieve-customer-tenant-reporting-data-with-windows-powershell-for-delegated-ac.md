---
title: Recuperar datos de informes de inquilinos de clientes con Windows PowerShell para asociados de DAP
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
ms.custom: seo-marvel-apr2020
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Resumen: use el modo remoto de Windows PowerShell para Microsoft Exchange Online para recuperar informes de espacios empresariales de clientes individuales.'
ms.openlocfilehash: 69c441f1e241f964ec3ef24a915331a8980a4794
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606246"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="4ebc1-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span><span class="sxs-lookup"><span data-stu-id="4ebc1-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="4ebc1-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="4ebc1-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="4ebc1-105">Use Windows PowerShell remoto para Microsoft Exchange Online para recuperar informes de inquilinos de cliente individuales.</span><span class="sxs-lookup"><span data-stu-id="4ebc1-105">Use remote Windows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="4ebc1-106">Los partners de sindicación y proveedor de soluciones en la nube (CSP) pueden tener acceso a los datos que forman los informes de inquilinos de clientes directamente a través de Windows PowerShell remoto para Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4ebc1-106">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remote Windows PowerShell for Exchange Online PowerShell.</span></span> <span data-ttu-id="4ebc1-107">Esto permite a los asociados recopilar y guardar los datos de los informes para luego realizar otras operaciones con ellos.</span><span class="sxs-lookup"><span data-stu-id="4ebc1-107">This lets partners collect and save the reporting data and then perform other operations on it.</span></span> <span data-ttu-id="4ebc1-108">Después de abrir una conexión remota, recuperar datos de informes sobre un arrendamiento de cliente es igual que ejecutar cualquier cmdlet en un arrendamiento de cliente..</span><span class="sxs-lookup"><span data-stu-id="4ebc1-108">After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="4ebc1-109">En este artículo, se usa Windows PowerShell remoto para Exchange Online para conectarse a un único arrendamiento de clientes y recuperar un informe.</span><span class="sxs-lookup"><span data-stu-id="4ebc1-109">In this article, you use remote Windows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report.</span></span> <span data-ttu-id="4ebc1-110">De forma predeterminada, Windows PowerShell no admite agregar datos de informes de varios arrendamientos de cliente.</span><span class="sxs-lookup"><span data-stu-id="4ebc1-110">By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies.</span></span> <span data-ttu-id="4ebc1-111">Los informes que recupera con este procedimiento son solo para el  _DelegatedOrg_ al que se conecta.</span><span class="sxs-lookup"><span data-stu-id="4ebc1-111">The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
 
## <a name="before-you-begin"></a><span data-ttu-id="4ebc1-112">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="4ebc1-112">Before you begin</span></span>

- <span data-ttu-id="4ebc1-p103">Debe conectarse a su inquilino de Exchange Online mediante el modo remoto de Windows PowerShell. Para obtener instrucciones, consulte [Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="4ebc1-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="4ebc1-115">Ejecutar Get-StaleMailboxReport a modo de ejemplo</span><span class="sxs-lookup"><span data-stu-id="4ebc1-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="4ebc1-116">Después de abrir una sesión remota en Exchange Online, ejecute este comando para recuperar el elemento **Get-StaleMailboxReport** del intervalo de fechas entre el 25/03/2015 y el 31/03/2015.</span><span class="sxs-lookup"><span data-stu-id="4ebc1-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="4ebc1-p104">Existen muchos otros cmdlets de informes disponibles para Exchange Online, Lync Online y SharePoint Online, así como otros para el seguimiento de mensajes. Para obtener más información sobre los cmdlets de informes disponibles y el servicio web de informes de Office 365, consulte los temas en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="4ebc1-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="4ebc1-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="4ebc1-119">See also</span></span>

#### 

[<span data-ttu-id="4ebc1-120">Servicio web de informes de Office 365</span><span class="sxs-lookup"><span data-stu-id="4ebc1-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="4ebc1-121">Cmdlets de informes en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="4ebc1-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="4ebc1-122">Ayuda para socios</span><span class="sxs-lookup"><span data-stu-id="4ebc1-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

