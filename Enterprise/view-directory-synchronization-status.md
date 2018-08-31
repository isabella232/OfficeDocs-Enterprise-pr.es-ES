---
title: Ver el estado de sincronización de directorios en Office 365
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
ms.assetid: 18be3b98-34ae-47be-9337-ab6c3fb372ac
description: Obtenga información sobre cómo desactivar la sincronización de Active directory. También puede ver su estado.
ms.openlocfilehash: c843fa4d71976cbdd0d6d3d10720e2845b26796c
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22543009"
---
# <a name="view-directory-synchronization-status-in-office-365"></a>Ver el estado de sincronización de directorios en Office 365
Si ha integrado su Active Directory local con Azure AD mediante la sincronización de su entorno local con Office 365, también puede comprobar el estado de la sincronización.
  
## <a name="view-directory-synchronization-status"></a>Ver el estado de sincronización de Active directory
- Inicie sesión en el centro de administración de Office 365 y elegir el **Estado de sincronización de directorios** en la página principal. 
- Como alternativa, puede ir a **los usuarios** \> **usuarios activos**y en la página **usuarios activos** , elija **más** \> **sincronización de Active Directory**. En el panel de la **Sincronización de directorios** , elija **Ir a la administración de sincronización de directorios**.
    
## <a name="information-on-the-manage-directory-synchronization-page"></a>Obtener información acerca de la página de sincronización de directorios de administrar

En la siguiente tabla se enumera las características que se puede obtener información acerca de la página.
  
Si hay un problema con la sincronización de directorios, los errores se enumeran en esta página también. Para obtener más información acerca de los diferentes errores que puedan surgir, consulte [identificar errores de sincronización de Active directory en Office 365](identify-directory-synchronization-errors.md).
  
|**Elemento**|**¿Qué es**|
|:-----|:-----|
|**Dominios comprobados** | Número de dominios en el inquilino de Office 365 que haya comprobado posee. |
|**Dominios no comprobados** | Dominios ha agregado, pero no se ha comprobado. |
|**Sincronización de Active Directory habilitado** |True o False. Especifica si ha habilitado la sincronización de Active directory. |
|**Última sincronización de Active directory** | Última vez que se ejecutó la sincronización de Active directory. Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización se ha hace más de tres días. |
|**Habilitado para la sincronización de contraseñas** | True o False. Especifica si tienen sincronización de hash de contraseña entre nuestra local y su inquilino de Office 365. |
|**Última sincronización de contraseñas** | Última vez que se ejecutó la sincronización de contraseñas hash. Se mostrará una advertencia y un vínculo a una herramienta de solución de problemas si la última sincronización se ha hace más de tres días. |
|**Versión de cliente de sincronización de Active Directory** | Contiene un vínculo de descarga si se ha publicado una nueva versión de Azure Connect de AD. |
|**Herramienta IDFix** | Vínculo de descarga para [IDFix](install-and-run-idfix.md), una herramienta que puede utilizar para proteger Active Directory local. |
|**Cuenta de servicio de sincronización de Active Directory** | Muestra el nombre de la que cuenta de servicio de sincronización de directorios de Office 365. |