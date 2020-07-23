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
description: 'Resumen: use el modo remoto de Windows PowerShell para Microsoft Exchange Online para recuperar informes de espacios empresariales de clientes individuales.'
ms.openlocfilehash: 4e18eb2e2ed5f801106535b31577d3186e87c58c
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230286"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Use Windows PowerShell remoto para Microsoft Exchange Online para recuperar informes de inquilinos de cliente individuales.
  
Los partners de sindicación y proveedor de soluciones en la nube (CSP) pueden tener acceso a los datos que forman los informes de inquilinos de clientes directamente a través de Windows PowerShell remoto para Exchange Online PowerShell. Esto permite a los asociados recopilar y guardar los datos de los informes para luego realizar otras operaciones con ellos. Después de abrir una conexión remota, recuperar datos de informes sobre un arrendamiento de cliente es igual que ejecutar cualquier cmdlet en un arrendamiento de cliente..
  
En este artículo, se usa Windows PowerShell remoto para Exchange Online para conectarse a un único arrendamiento de clientes y recuperar un informe. De forma predeterminada, Windows PowerShell no admite agregar datos de informes de varios arrendamientos de cliente. Los informes que recupera con este procedimiento son solo para el  _DelegatedOrg_ al que se conecta.
  
 
## <a name="before-you-begin"></a>Antes de empezar

- Debe conectarse a su inquilino de Exchange Online mediante el modo remoto de Windows PowerShell. Para obtener instrucciones, consulte [Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="run-the-get-stalemailboxreport-sample"></a>Ejecutar Get-StaleMailboxReport a modo de ejemplo

Después de abrir una sesión remota en Exchange Online, ejecute este comando para recuperar el elemento **Get-StaleMailboxReport** del intervalo de fechas entre el 25/03/2015 y el 31/03/2015.
  
```
Get-StaleMailboxReport -StartDate 03/25/2015 -EndDate 03/31/2015
```

Existen muchos otros cmdlets de informes disponibles para Exchange Online, Lync Online y SharePoint Online, así como otros para el seguimiento de mensajes. Para obtener más información sobre los cmdlets de informes disponibles y el servicio web de informes de Office 365, consulte los temas en la sección siguiente.
  
## <a name="see-also"></a>Consulte también

#### 

[Servicio web de informes de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlets de informes en Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)
  
[Ayuda para socios](https://go.microsoft.com/fwlink/p/?LinkID=533477)

