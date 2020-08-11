---
title: Ver el estado de sincronización de directorios en Microsoft 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: En este artículo, obtenga información acerca de cómo puede comprobar el estado de la sincronización de directorios en Office 365.
ms.openlocfilehash: 9aaad085854326ebb6542f03256ae851b27f0980
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605866"
---
# <a name="view-directory-synchronization-status-in-microsoft-365"></a>Ver el estado de sincronización de directorios en Microsoft 365

Si ha integrado su Active Directory local con Azure AD mediante la sincronización del entorno local con Microsoft 365, también puede comprobar el estado de la sincronización.
  
## <a name="view-directory-synchronization-status"></a>Ver el estado de sincronización de directorios

- Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) y elija **Estado de sincronización de directorios** en la Página principal.
- Como alternativa, puede **ir a usuarios** \> **activos**y, en la página **usuarios activos** , elija **más** \> **sincronización de directorios**. En el panel **sincronización de directorios** , elija **ir a administración de sincronización**de directorios.

## <a name="information-on-the-manage-directory-synchronization-page"></a>Información en la página administrar la sincronización de directorios

En la siguiente tabla se enumeran las características a las que puede obtener información en la página.
  
Si hay un problema con la sincronización de directorios, los errores también se enumeran en esta página. Para obtener más información acerca de los diferentes errores que se pueden encontrar, consulte [identificar errores de sincronización de directorios en Microsoft 365](identify-directory-synchronization-errors.md).
  
|**Elemento**|**Para qué sirve**|
|:-----|:-----|
|**Dominios comprobados** | Número de dominios de su inquilino de Microsoft 365 que ha comprobado que es el propietario. |
|**Dominios no comprobados** | Dominios que ha agregado, pero no comprobado. |
|**Sincronización de directorios habilitada** |True o false. Especifica si ha habilitado la sincronización de directorios. |
|**Sincronización de directorios más reciente** | Última vez que se ejecutó la sincronización de directorios. Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización fue de hace más de tres días. |
|**Sincronización de contraseñas habilitada** | True o false. Especifica si la sincronización de hash de contraseña entre nuestro entorno local y su inquilino de Microsoft 365. |
|**Última sincronización de contraseñas** | Última vez que se ejecutó la sincronización hash de contraseña. Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización fue de hace más de tres días. |
|**Versión del cliente de sincronización de directorios** | Contiene un vínculo de descarga si se ha lanzado una nueva versión de Azure AD Connect. |
|**Cuenta del servicio de sincronización de directorios** | Muestra el nombre de la cuenta del servicio de sincronización de directorios de Microsoft 365. |