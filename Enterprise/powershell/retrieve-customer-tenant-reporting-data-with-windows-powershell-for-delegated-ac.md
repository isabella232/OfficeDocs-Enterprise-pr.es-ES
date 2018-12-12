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
ms.custom: ''
ms.assetid: 893e5275-30b3-433f-8ecd-644f78f513e2
description: 'Resumen: Use el modo remoto de Windows PowerShell para Microsoft Exchange Online para recuperar informes de inquilinos de cliente individuales.'
ms.openlocfilehash: d764f34b89ee55fd7015f01c0c48446fc73a6ac0
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
ms.locfileid: "17114669"
---
# <a name="retrieve-customer-tenant-reporting-data-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a>Retrieve customer tenant reporting data with Windows PowerShell for Delegated Access Permissions (DAP) partners

 **Resumen:** use el modo remoto de Windows PowerShell para Microsoft Exchange Online para recuperar informes de espacios empresariales de clientes individuales.
  
Socios de sindicación y proveedor de soluciones en la nube (CSP) puede acceder a los datos que conforman los informes de inquilino de cliente directamente a través del modo remoto de Windows PowerShell para Exchange Online PowerShell. Esto permite a los asociados recopilar y guardar los datos de los informes para luego realizar otras operaciones con ellos. Después de abrir una conexión remota, recuperar datos de informes sobre un arrendamiento de cliente es igual que ejecutar cualquier cmdlet en un arrendamiento de cliente..
  
En este artículo, debe usar el modo remoto de Windows PowerShell para Exchange Online para conectarse a un solo arrendamiento de cliente y recuperar un informe. De forma predeterminada, Windows PowerShell no admite agregar datos de informes de varios arrendamientos de cliente. Los informes que recupera con este procedimiento son solo para el  _DelegatedOrg_ al que se conecta.
  
Si desea recuperar un único informe para todos los arrendamientos de cliente, encontrará un script de ejemplo para ello en [Agregar datos de informes de clientes a través de Windows PowerShell para asociados con permiso de acceso delegado (DAP)](aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-pe.md) .
  
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

