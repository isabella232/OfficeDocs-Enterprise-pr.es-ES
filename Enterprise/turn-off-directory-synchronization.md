---
title: Desactivar la sincronización de directorios para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED150
ms.assetid: ee5f861e-bd48-4267-83d1-a4ead4b4a00d
description: En este artículo, encontrará información sobre cómo usar PowerShell para desactivar la sincronización de directorios para Microsoft 365.
ms.openlocfilehash: 815d20ff6a0697f1533e44305e20e61a9282312b
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46603652"
---
# <a name="turn-off-directory-synchronization-for-microsoft-365"></a>Desactivar la sincronización de directorios para Microsoft 365
Puede usar PowerShell para desactivar la sincronización de directorios. Sin embargo, no se recomienda desactivar la sincronización de directorios como un paso de solución de problemas. Si necesita ayuda para solucionar problemas de la sincronización de directorios, consulte el artículo [solución de problemas con la sincronización de directorios para Microsoft 365](fix-problems-with-directory-synchronization.md) . 
  
[Póngase en contacto con el soporte técnico](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para productos empresariales si es necesario.
  
## <a name="turn-off-directory-synchronization"></a>Desactivar la sincronización de directorios  
Para desactivar la sincronización de directorios:
  
1. En primer lugar, instale el software necesario y conéctese a su suscripción a Microsoft 365. Para obtener instrucciones, vea [conectarse con el módulo Microsoft Azure Active Directory para Windows PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
    
2. Use [set-MsolDirSyncEnabled](https://go.microsoft.com/fwlink/p/?LinkId=821939) para deshabilitar la sincronización de directorios: 
    
  ```powershell
  Set-MsolDirSyncEnabled -EnableDirSync $false
  ```

>[!Note]
>Si usa este comando, debe esperar 72 horas para poder volver a activar la sincronización de directorios.
>
 
