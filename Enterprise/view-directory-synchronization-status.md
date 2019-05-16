---
title: Ver el estado de sincronización de directorios en Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Obtenga información sobre cómo desactivar la sincronización de directorios. También puede ver su estado.
ms.openlocfilehash: 4204d72719e928982b2b6222fb971d62c0f1f8d6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070416"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Ver el estado de sincronización de directorios en Office 365

Si ha integrado su Active Directory local con Azure AD mediante la sincronización del entorno local con Office 365, también puede comprobar el estado de la sincronización.
  
## <a name="view-directory-synchronization-status"></a>Ver el estado de sincronización de directorios

- Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) y elija **Estado de sincronización de directorios** en la Página principal.
- **** \> Como alternativa, puede ir a usuarios **activos**y, en la página **usuarios activos** , elija **más** \> **sincronización de directorios**. En el panel **sincronización de directorios** , elija **ir a administración de sincronización**de directorios.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Información en la página administrar la sincronización de directorios

En la siguiente tabla se enumeran las características a las que puede obtener información en la página.
  
Si hay un problema con la sincronización de directorios, los errores también se enumeran en esta página. Para obtener más información acerca de los diferentes errores que se pueden producir, consulte [identificar errores de sincronización de directorios en Office 365](identify-directory-synchronization-errors.md).
  
|**Item**|**Para qué sirve**|
|:-----|:-----|
|**Dominios comprobados** | Número de dominios de su inquilino de Office 365 que ha comprobado que es el propietario. |
|**Dominios no comprobados** | Dominios que ha agregado, pero no comprobado. |
|**Sincronización de directorios habilitada** |True o false. Especifica si ha habilitado la sincronización de directorios. |
|**Sincronización de directorios más reciente** | Última vez que se ejecutó la sincronización de directorios. Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización fue de hace más de tres días. |
|**Sincronización de contraseñas habilitada** | True o false. Especifica si tiene sincronización de hash de contraseña entre nuestro entorno local y su inquilino de Office 365. |
|**Última sincronización de contraseñas** | Última vez que se ejecutó la sincronización hash de contraseña. Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización fue de hace más de tres días. |
|**Versión del cliente de sincronización de directorios** | Contiene un vínculo de descarga si se ha lanzado una nueva versión de Azure AD Connect. |
|**Herramienta IDFix** | Vínculo de descarga a [IDFix](install-and-run-idfix.md), una herramienta que puede usar para comprobar Active Directory local. |
|**Cuenta del servicio de sincronización de directorios** | Muestra el nombre de la cuenta del servicio de sincronización de directorios de Office 365. |