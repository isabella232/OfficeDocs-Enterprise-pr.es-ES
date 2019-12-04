---
title: Registro de transacciones de IdFix de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
ms.assetid: d58b7d45-7947-4193-9456-82ba76f42d89
description: Proporciona un ejemplo y describe la Convención de nomenclatura y el nivel de registro predeterminado del registro de transacciones de IdFix de Office 365.
ms.openlocfilehash: 22ea5af87b1bbcaa96f88e3746a50f1411a01b9a
ms.sourcegitcommit: a9804062071939b7b7e60da5b69f484ce1d34ff8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/04/2019
ms.locfileid: "39813428"
---
# <a name="office-365-idfix-transaction-log"></a>Registro de transacciones de IdFix de Office 365

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Proporciona un ejemplo y describe la Convención de nomenclatura y el nivel de registro predeterminado del registro de transacciones de IdFix de Office 365.
  
## <a name="idfix-transaction-log-location"></a>Ubicación del registro de transacciones de IdFix

La herramienta IdFix de Office 365 crea un nuevo registro de transacciones cada vez que hace clic en **aplicar** en IdFix y se aplican los cambios en el bosque de Active Directory. El registro de transacciones se guarda en la misma carpeta en la que ha instalado IdFix. De forma predeterminada, esta carpeta es C:\Deployment Tools\IDFix. El nombre del archivo de registro de transacciones usa un formato de marca de fecha y hora, por ejemplo, verbose 6-1-2018 6-17-22 PM indica un archivo que se generó el 1 de junio de 2018 a 6:17:22 PM. Verbose indica el nivel de registro. 
  
## <a name="idfix-transaction-log-logging-level"></a>Nivel de registro de transacciones de IdFix

La palabra verbose en el nombre del archivo de registro de transacciones indica el nivel de registro en el archivo. Detallado significa que se captura la cantidad máxima de información en el registro. Este es el nivel de registro predeterminado. En este momento, no puede cambiar el nivel de registro.
  
## <a name="idfix-transaction-log-format"></a>Formato de registro de transacciones de IdFix

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