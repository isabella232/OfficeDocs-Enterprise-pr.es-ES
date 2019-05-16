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
ms.openlocfilehash: 0c6f2dd64cb406681c0a98099b2a42887ee79c25
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067266"
---
# <a name="office-365-idfix-transaction-log"></a><span data-ttu-id="2584c-103">Registro de transacciones de IdFix de Office 365</span><span class="sxs-lookup"><span data-stu-id="2584c-103">Office 365 IdFix transaction log</span></span>

<span data-ttu-id="2584c-104">Proporciona un ejemplo y describe la Convención de nomenclatura y el nivel de registro predeterminado del registro de transacciones de IdFix de Office 365.</span><span class="sxs-lookup"><span data-stu-id="2584c-104">Provides an example and describes the naming convention and default log level of the Office 365 IdFix transaction log.</span></span>
  
## <a name="idfix-transaction-log-location"></a><span data-ttu-id="2584c-105">Ubicación del registro de transacciones de IdFix</span><span class="sxs-lookup"><span data-stu-id="2584c-105">IdFix transaction log location</span></span>

<span data-ttu-id="2584c-106">La herramienta IdFix de Office 365 crea un nuevo registro de transacciones cada vez que hace clic en **aplicar** en IdFix y se aplican los cambios en el bosque de Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2584c-106">The Office 365 IdFix tool creates a new transaction log each time you click **Apply** in IdFix and apply changes to the Active Directory forest.</span></span> <span data-ttu-id="2584c-107">El registro de transacciones se guarda en la misma carpeta en la que ha instalado IdFix.</span><span class="sxs-lookup"><span data-stu-id="2584c-107">The transaction log is saved in the same folder where you installed IdFix.</span></span> <span data-ttu-id="2584c-108">De forma predeterminada, esta carpeta es C:\Deployment Tools\IDFix.</span><span class="sxs-lookup"><span data-stu-id="2584c-108">By default, this folder is C:\Deployment Tools\IDFix.</span></span> <span data-ttu-id="2584c-109">El nombre del archivo de registro de transacciones usa un formato de marca de fecha y hora, por ejemplo, verbose 6-1-2018 6-17-22 PM indica un archivo que se generó el 1 de junio de 2018 a 6:17:22 PM.</span><span class="sxs-lookup"><span data-stu-id="2584c-109">The transaction log file name uses a date and time stamp format, for example, Verbose 6-1-2018 6-17-22 PM indicates a file that was generated at June 1, 2018 at 6:17:22 PM.</span></span> <span data-ttu-id="2584c-110">Verbose indica el nivel de registro.</span><span class="sxs-lookup"><span data-stu-id="2584c-110">Verbose indicates the logging level.</span></span> 
  
## <a name="idfix-transaction-log-logging-level"></a><span data-ttu-id="2584c-111">Nivel de registro de transacciones de IdFix</span><span class="sxs-lookup"><span data-stu-id="2584c-111">IdFix transaction log logging level</span></span>

<span data-ttu-id="2584c-112">La palabra verbose en el nombre del archivo de registro de transacciones indica el nivel de registro en el archivo.</span><span class="sxs-lookup"><span data-stu-id="2584c-112">The word verbose in the transaction log file name indicates the level of logging in the file.</span></span> <span data-ttu-id="2584c-113">Detallado significa que se captura la cantidad máxima de información en el registro.</span><span class="sxs-lookup"><span data-stu-id="2584c-113">Verbose means that the maximum amount of information is captured in the log.</span></span> <span data-ttu-id="2584c-114">Este es el nivel de registro predeterminado.</span><span class="sxs-lookup"><span data-stu-id="2584c-114">This is the default logging level.</span></span> <span data-ttu-id="2584c-115">En este momento, no puede cambiar el nivel de registro.</span><span class="sxs-lookup"><span data-stu-id="2584c-115">At this time, you cannot change the logging level.</span></span>
  
## <a name="idfix-transaction-log-format"></a><span data-ttu-id="2584c-116">Formato de registro de transacciones de IdFix</span><span class="sxs-lookup"><span data-stu-id="2584c-116">IdFix transaction log format</span></span>

<span data-ttu-id="2584c-117">IdFix escribe los resultados de cada acción de **actualización** en un registro de transacciones, como se muestra en el ejemplo siguiente:</span><span class="sxs-lookup"><span data-stu-id="2584c-117">IdFix writes the results of each **UPDATE** action to a transaction log as shown in the following example:</span></span>
  
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