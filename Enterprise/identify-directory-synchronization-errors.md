---
title: Ver errores de sincronización de directorios en Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
description: Obtenga información sobre cómo ver los errores de sincronización de directorios en el centro de administración de Office 365.
ms.openlocfilehash: 8b7bb16aeddbf1765426c3725cd1f670524ef6d1
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085039"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Ver errores de sincronización de directorios en Office 365

Puede ver los errores de sincronización de directorios en el centro de administración de Office 365. Solo se muestran los errores del objeto de usuario. Para ver los errores con PowerShell, consulte [identificar objetos con DirSyncProvisioningErrors](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency).

Después de ver, vea [solucionar problemas con la sincronización de directorios para Office 365](fix-problems-with-directory-synchronization.md) para corregir los problemas identificados.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Ver los errores de sincronización de directorios en el centro de administración

Para ver los errores en el centro de administración:
  
1. Inicie sesión en Office 365 con su cuenta profesional o educativa. 
    
2. Vaya a la [información acerca del centro de administración de Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. En la página **principal** , verá el icono de **Estado de sincronización de directorios** . 
    
    ![Icono de estado de sincronización de directorios de la versión preliminar del centro de administración](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. En el mosaico, seleccione **Estado** de sincronización de directorios para ir a la página **Estado de sincronización de directorios** . 
    
    En la parte inferior de la página puede ver si hay errores de sincronización de directorios.
    
    ![En la página estado de sincronización de directorios puede ver si hay errores de objetos dirSync](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Elija **encontramos errores de objeto** de sincronización de directorios para ir a una vista detallada de los errores de sincronización de directorios. 
    
    > [!NOTE]
    > También puede ir a la página **errores de sincronización de directorios** si elige que **se encuentren errores de objeto de sincronización** de directorios en el icono Estado de sincronización de **directorios** . 
  
![Página de errores de sincronización de directorios](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. En la página **errores de sincronización de directorios** , elija cualquiera de los errores enumerados para mostrar el panel de detalles con información sobre el error y sugerencias sobre cómo solucionarlo. 
