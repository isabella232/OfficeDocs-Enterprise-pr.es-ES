---
title: Desactivar la sincronización de directorios para Office 365
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
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Obtenga información sobre cómo usar PowerShell para desactivar la sincronización de Active directory para Office 365
ms.openlocfilehash: f47209dd8b6be47b7ae7a4b63a9fae38c5cb498f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542935"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Desactivar la sincronización de directorios para Office 365
Puede usar PowerShell para desactivar la sincronización de Active directory. Sin embargo, no se recomienda desactivar la sincronización de Active directory como un paso de solución de problemas. Si necesita ayuda con la solución de problemas de sincronización de directorios, vea el artículo de [fijación de problemas con la sincronización de Active directory para Office 365](fix-problems-with-directory-synchronization.md) . 
  
[Contactar con el servicio](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para productos de negocio si es necesario.
  
## <a name="turn-off-directory-synchronization"></a>Desactivar la sincronización de directorios  
Para desactivar la sincronización de directorios:
  
1. En primer lugar, instale el software necesario y conectarse a su suscripción de Office 365. Para obtener instrucciones para ambos, vea [conectarse a Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=821938).
    
2. Usar [Set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para deshabilitar la sincronización de directorios: 
    
  ```
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```