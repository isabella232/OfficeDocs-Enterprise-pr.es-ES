---
title: Registro de transacciones de IdFix de Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Proporciona un ejemplo y describe la convención de nomenclatura y el nivel de registro predeterminado del registro de transacciones de IdFix de Office 365.
ms.openlocfilehash: 016318c7e771ec6c5f90336e11c5dd011144d12e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542852"
---
# <a name="office-365-idfix-transaction-log"></a>Registro de transacciones de IdFix de Office 365

Proporciona un ejemplo y describe la convención de nomenclatura y el nivel de registro predeterminado del registro de transacciones de IdFix de Office 365.
  
## <a name="idfix-transaction-log-location"></a>Ubicación del registro de transacciones de IdFix

La herramienta IdFix de Office 365 crea un nuevo registro de transacciones cada vez que haga clic en **Aplicar** en IdFix y aplica cambios en el bosque de Active Directory. El registro de transacciones se guarda en la misma carpeta donde ha instalado IdFix. De forma predeterminada, esta carpeta es C:\Deployment Tools\IDFix. El nombre de archivo de registro de transacciones usa un formato de marca de fecha y hora, por ejemplo, detallado 6-1-2018 6-17-22 P.M. indica un archivo que se generó en 1 de junio de 2018 en 6:17:22 P.M. detallado indica el nivel de registro. 
  
## <a name="idfix-transaction-log-logging-level"></a>Nivel de registro de transacciones en IdFix

La palabra "detallado" en el nombre del archivo de registro de transacciones indica el nivel de registro en el archivo. Detallado significa que se captura la mayor cantidad de información posible en el registro. Es el nivel predeterminado de registro. En este momento, no puede cambiar el nivel de registro.
  
## <a name="idfix-transaction-log-format"></a>Formato del registro de transacciones de IdFix

IdFix escribe los resultados de cada acción de **actualización** en un registro de transacciones, como se muestra en el ejemplo siguiente:
  
```
5/22/2018 6:36:44 AM Initialized - IdFix version 1.07 - Multi-Tenant
5/22/2018 6:36:47 AM Query AD
5/22/2018 6:36:47 AM FOREST:e2k10.com SERVER:dc1.e2k10.com FILTER:(|(objectCategory=Person)(objectCategory=Group))
5/22/2018 6:36:47 AM Please wait while the LDAP Connection is established.
5/22/2018 6:36:49 AM Query Count: 140  Error Count: 29  Duplicate Check Count: 191
5/22/2018 6:36:49 AM Elapsed Time: AD Query - 00:00:02.3890432
5/22/2018 6:36:49 AM Write split files
5/22/2018 6:36:49 AM Merge split files
5/22/2018 6:36:49 AM Count duplicates
5/22/2018 6:36:49 AM Write filtered duplicate objects
5/22/2018 6:36:49 AM Read filtered duplicate objects
5/22/2018 6:36:49 AM Read error file
5/22/2018 6:36:49 AM Elapsed Time: Duplicate Checks - 00:00:00.0780785
5/22/2018 6:36:49 AM Populating DataGrid
5/22/2018 6:36:50 AM Elapsed Time: Populate DataGridView - 00:00:00.0780785
5/22/2018 6:36:50 AM Query Count: 140  Error Count: 53
5/22/2018 6:37:34 AM Apply Pending
5/22/2018 6:37:34 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][EDIT]
5/22/2018 6:37:34 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][REMOVE]
5/22/2018 6:37:34 AM COMPLETE
5/22/2018 6:37:40 AM Loading Updates
5/22/2018 6:37:40 AM Action Selection
5/22/2018 6:37:57 AM Apply Pending
5/22/2018 6:37:57 AM Update: [CN=user000001,OU=e2k10OU1,DC=e2k10,DC=com][user][mailnickname][character][user?^|000001][user000001][UNDO]
5/22/2018 6:37:57 AM Update: [CN=user000008,OU=e2k10OU1,DC=e2k10,DC=com][user][targetAddress][duplicate][smtp:user000008@customer.com][][UNDO]
5/22/2018 6:37:57 AM COMPLETE

```