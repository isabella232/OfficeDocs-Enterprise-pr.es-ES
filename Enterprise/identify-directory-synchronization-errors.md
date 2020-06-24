---
title: Ver los errores de sincronización de directorios en Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Obtenga información sobre cómo ver los errores de sincronización de directorios en el centro de administración de Microsoft 365.
ms.openlocfilehash: 57ca9ce125679931adcca93621474cec9ee9b82f
ms.sourcegitcommit: 3349fdaff646f5f7d92c22565402dfc22c12d2ed
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/22/2020
ms.locfileid: "44842094"
---
# <a name="view-directory-synchronization-errors-in-microsoft-365"></a>Ver los errores de sincronización de directorios en Microsoft 365

Puede ver los errores de sincronización de directorios en el centro de administración de Microsoft 365. Solo se muestran los errores del objeto de usuario. Para ver errores con PowerShell, consulte [identificar objetos con DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

## <a name="view-directory-synchronization-errors-in-the-microsoft-365-admin-center"></a>Ver los errores de sincronización de directorios en el centro de administración de Microsoft 365

Para ver los errores en el centro de administración de Microsoft 365:
  
1. Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) con una cuenta de administrador global. 
    
2. En la página **principal** , verá la tarjeta de **Administración de usuarios** . 
    
    ![La tarjeta de administración de usuarios en el centro de administración de Microsoft 365](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
3. En la tarjeta, elija **sincronizar errores** en **Azure ad Connect** para ver los errores en la página de **errores de sincronización de directorios** .   
    
    ![Un ejemplo de la página de errores de sincronización de directorios](media/882094a3-80d3-4aae-b90b-78b27047974c.png)

4. Elija cualquiera de los errores para mostrar el panel de detalles con información sobre el error y sugerencias sobre cómo solucionarlo.

   ![Ejemplo de los detalles de un error de sincronización de directorios](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
Después de ver, vea [solucionar problemas con la sincronización de directorios para Microsoft 365](fix-problems-with-directory-synchronization.md) para corregir los problemas identificados.

