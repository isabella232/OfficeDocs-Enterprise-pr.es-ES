---
title: Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Resumen: Use el modo remoto de Windows PowerShell para Microsoft Exchange Online para recuperar informes de inquilinos de cliente individuales.'
ms.openlocfilehash: 40c1dedd8fb223ea6fa478b3a5c3e716fe07dd93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="38fb0-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span><span class="sxs-lookup"><span data-stu-id="38fb0-103">Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

 <span data-ttu-id="38fb0-104">**Resumen:** use el modo remoto de Windows PowerShell para Microsoft Exchange Online para recuperar informes de espacios empresariales de clientes individuales.</span><span class="sxs-lookup"><span data-stu-id="38fb0-104">Summary: Use remoteWindows PowerShell for Microsoft Exchange Online to retrieve reports from individual customer tenants.</span></span>
  
<span data-ttu-id="38fb0-p101">Socios de sindicación y proveedor de soluciones en la nube (CSP) puede acceder a los datos que conforman los informes de inquilino de cliente directamente a través del modo remoto de Windows PowerShell para Exchange Online PowerShell. Esto permite a los asociados recopilar y guardar los datos de los informes para luego realizar otras operaciones con ellos. Después de abrir una conexión remota, recuperar datos de informes sobre un arrendamiento de cliente es igual que ejecutar cualquier cmdlet en un arrendamiento de cliente..</span><span class="sxs-lookup"><span data-stu-id="38fb0-p101">Syndication and Cloud Solution Provider (CSP) partners can access the data that makes up customer tenant reports directly via remoteWindows PowerShell for Exchange Online PowerShell. This lets partners collect and save the reporting data and then perform other operations on it. After you open a remote connection, retrieving reporting data about a customer tenancy is identical to running any cmdlet against a customer tenancy.</span></span>
  
<span data-ttu-id="38fb0-p102">En este artículo, debe usar el modo remoto de Windows PowerShell para Exchange Online para conectarse a un solo arrendamiento de cliente y recuperar un informe. De forma predeterminada, Windows PowerShell no admite agregar datos de informes de varios arrendamientos de cliente. Los informes que recupera con este procedimiento son solo para el  _DelegatedOrg_ al que se conecta.</span><span class="sxs-lookup"><span data-stu-id="38fb0-p102">In this article, you use remoteWindows PowerShell for Exchange Online to connect to a single customer tenancy and retrieve a report. By default, Windows PowerShell does not support aggregating reporting data from multiple customer tenancies. The reports you retrieve with this procedure are only for the  _DelegatedOrg_ that you connect to.</span></span>
  
<span data-ttu-id="38fb0-111">Si desea recuperar un único informe para todos los arrendamientos de cliente, encontrará un script de ejemplo para ello en [Agregar datos de informes de clientes a través de Windows PowerShell para asociados con permiso de acceso delegado (DAP)](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .</span><span class="sxs-lookup"><span data-stu-id="38fb0-111">If you want to retrieve a single report for all your customer tenancies, a sample script to do this can be found in [Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="38fb0-112">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="38fb0-112">Before you begin</span></span>

- <span data-ttu-id="38fb0-p103">Debe conectarse a su inquilino de Exchange Online mediante el modo remoto de Windows PowerShell. Para obtener instrucciones, consulte [Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="38fb0-p103">You need to connect to your Exchange Online tenant by using remote Windows PowerShell. For instructions, see [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="run-the-get-stalemailboxreport-sample"></a><span data-ttu-id="38fb0-115">Ejecutar Get-StaleMailboxReport a modo de ejemplo</span><span class="sxs-lookup"><span data-stu-id="38fb0-115">Run the Get-StaleMailboxReport sample</span></span>

<span data-ttu-id="38fb0-116">Después de abrir una sesión remota en Exchange Online, ejecute este comando para recuperar el elemento **Get-StaleMailboxReport** del intervalo de fechas entre el 25/03/2015 y el 31/03/2015.</span><span class="sxs-lookup"><span data-stu-id="38fb0-116">After you have opened a remote session to Exchange Online, run this command to retrieve the **Get-StaleMailboxReport** for the date range 03/25/2015 through 03/31/2015.</span></span>
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

<span data-ttu-id="38fb0-p104">Existen muchos otros cmdlets de informes disponibles para Exchange Online, Lync Online y SharePoint Online, así como otros para el seguimiento de mensajes. Para obtener más información sobre los cmdlets de informes disponibles y el servicio web de informes de Office 365, consulte los temas en la sección siguiente.</span><span class="sxs-lookup"><span data-stu-id="38fb0-p104">There are many other reporting cmdlets available for Exchange Online, Lync Online, and SharePoint Online as well as others for message tracing that you can use. To find out more about the available reporting cmdlets and the Office 365 Reporting web service, see the topics in the following section.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="38fb0-119">Consulte también</span><span class="sxs-lookup"><span data-stu-id="38fb0-119">See also</span></span>

#### 

[<span data-ttu-id="38fb0-120">Servicio web de informes de Office 365</span><span class="sxs-lookup"><span data-stu-id="38fb0-120">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="38fb0-121">Cmdlets de informes en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="38fb0-121">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[<span data-ttu-id="38fb0-122">Ayuda para socios</span><span class="sxs-lookup"><span data-stu-id="38fb0-122">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)

