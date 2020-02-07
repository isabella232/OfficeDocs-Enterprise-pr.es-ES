---
title: Desactivar la sincronización de directorios en Office 365
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
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: Obtenga información sobre cómo usar PowerShell para desactivar la sincronización de directorios para Office 365
ms.openlocfilehash: eab736241372b2d1b6023dc803dff540dded64ae
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841017"
---
# <a name="turn-off-directory-synchronization-for-office-365"></a>Desactivar la sincronización de directorios en Office 365
Puede usar PowerShell para desactivar la sincronización de directorios. Sin embargo, no se recomienda desactivar la sincronización de directorios como un paso de solución de problemas. Si necesita ayuda para solucionar problemas de la sincronización de directorios, consulte el artículo [solución de problemas con la sincronización de directorios para Office 365](fix-problems-with-directory-synchronization.md) . 
  
[Póngase en contacto con el soporte técnico](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para productos empresariales si es necesario.
  
## <a name="turn-off-directory-synchronization"></a>Desactivar la sincronización de directorios  
Para desactivar la sincronización de directorios:
  
1. En primer lugar, instale el software necesario y conéctese a su suscripción de Office 365. Para obtener instrucciones, vea [conectarse con el módulo Microsoft Azure Active Directory para Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Use [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para deshabilitar la sincronización de directorios: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```
