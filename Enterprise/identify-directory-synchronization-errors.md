---
title: Ver errores de sincronización de Active directory en Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- GPA150
ms.assetid: b4fc07a5-97ea-4ca6-9692-108acab74067
description: Obtenga información sobre cómo ver los errores de sincronización de Active directory en el centro de administración de Office 365.
ms.openlocfilehash: 62f1135568261eccf0e7e66b78c5aaff966c7281
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542851"
---
# <a name="view-directory-synchronization-errors-in-office-365"></a>Ver errores de sincronización de Active directory en Office 365

Puede ver los errores de sincronización de Active directory en el centro de administración de Office 365. Se muestran sólo los errores del objeto de usuario. Para ver los errores mediante el uso de PowerShell, vea [identificar objetos con DirSyncProvisioningErrors](https://go.microsoft.com/fwlink/p/?LinkId=798300).

Después de visualización, vea [solución de problemas con la sincronización de Active directory para Office 365](fix-problems-with-directory-synchronization.md) para corregir los problemas identificados.
  
## <a name="view-directory-synchronization-errors-in-the-admin-center"></a>Ver errores de sincronización de Active directory en el centro de administración

Para ver los errores en el centro de administración:
  
1. Inicie sesión en Office 365 con su cuenta profesional o educativa. 
    
2. Vaya al [Centro de administración de acerca de Office 365](https://support.office.com/article/758befc4-0888-4009-9f14-0d147402fd23).
    
3. En la página **principal** , verá el icono de **Estado de sincronización de directorios** . 
    
    ![El estado de sincronización de directorios en mosaico en la vista previa del centro de administración](media/060006e9-de61-49d5-8979-e77cda198e71.png)
  
4. En el icono, elija el **Estado de sincronización de directorios** para ir a la página de **Estado de la sincronización de Active Directory** . 
    
    En la parte inferior de la página puede ver si hay errores de sincronización de directorios.
    
    ![En la página de estado de la sincronización de Active Directory puede ver si hay errores de objeto de sincronización de directorios](media/882094a3-80d3-4aae-b90b-78b27047974c.png)
  
    Elija **se encuentra errores de objeto de sincronización de directorios** para ir a una vista detallada de los errores de sincronización de Active directory. 
    
    > [!NOTE]
    > También puede ir a la página de **errores de sincronización de directorios** si elige **se encuentra errores de objeto de sincronización de directorios** en el icono de **estado de sincronización de directorios** . 
  
![Página de errores de sincronización de directorios](media/a6e302d4-6be7-4e3a-b4b5-81c5a2c02952.png)
  
5. En la página de **errores de sincronización de directorios** , elija cualquiera de los errores que se enumeran para mostrar el panel de detalles con información sobre los errores y sugerencias sobre cómo corregirlo. 
