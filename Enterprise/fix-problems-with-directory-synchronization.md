---
title: Solución de problemas con la sincronización de directorios para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
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
- MBS150
ms.assetid: 79c43023-5a47-45ae-8068-d8a26eee6bc2
description: Describe las causas comunes de los problemas con la sincronización de directorios en Office 365 y proporciona algunos métodos para ayudar a solucionar problemas y resolverlos.
ms.openlocfilehash: cb2ec57331d227f0965095ee0782f13af935d569
ms.sourcegitcommit: d2a3d6eeeaa07510ee94c2bc675284d893221a95
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/12/2020
ms.locfileid: "44711913"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Solución de problemas con la sincronización de directorios para Microsoft 365

Con la sincronización de directorios, puede seguir Administrando usuarios y grupos locales y sincronizar adiciones, eliminaciones y cambios en la nube. Pero la configuración es un poco complicada y a veces puede ser difícil identificar el origen de los problemas. Tenemos recursos para ayudarle a identificar posibles problemas y solucionarlos.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>¿Cómo sé si algo es incorrecto?

La primera indicación de que algo es incorrecto es cuando el icono Estado de sincronización de directorios del centro de administración de Microsoft 365 indica que hay un problema.
  
También recibirá un correo (para el correo electrónico alternativo y el correo electrónico de administrador) de Microsoft 365 que indica que el inquilino ha encontrado errores de sincronización de directorios. Para obtener información detallada, vea [identificar errores de sincronización de directorios en Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>¿Cómo obtengo la herramienta Azure Active Directory Connect?

En el [centro de administración de Microsoft 365](https://admin.microsoft.com), vaya a **usuarios** \> **activos**. Haga clic en el menú **más** (tres puntos) y seleccione **sincronización de directorios**. 
  
Siga las [instrucciones del asistente](set-up-directory-synchronization.md) para descargar Azure ad Connect. 
  
Si sigue usando Azure Active Directory Sync (DirSync), eche un vistazo a la [solución de problemas de los mensajes de error del Asistente para la instalación y configuración de la herramienta de sincronización de Azure Active Directory en Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) para obtener información sobre los requisitos del sistema para instalar DirSync, los permisos necesarios y cómo solucionar errores comunes. 
  
Para actualizar desde Azure Active Directory Sync a Azure AD Connect, consulte [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Resolución de causas comunes de problemas con la sincronización de directorios en Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>**Los objetos sincronizados no aparecen o no se actualizan en línea, o bien se obtienen informes de errores de sincronización del servicio.**

- [Resistencia de atributo duplicado y sincronización de identidad](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>**Tengo una alerta en el centro de administración o estoy recibiendo correos electrónicos automatizados que no han habido un evento de sincronización reciente**
- [Solucionar problemas de conectividad con Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Cuentas y permisos de Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Sincronización de Azure AD Connect: Cómo administrar la cuenta de servicio de Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [La sincronización de directorios con Azure Active Directory se detiene o le advierte que la sincronización no se ha registrado en más de un día](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>**Los hash de contraseña no se sincronizan o veo una alerta en el centro de administración que indica que no había una sincronización de hash de contraseña reciente.**
- [Implementar la sincronización de hash de contraseñas con la sincronización de Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>**Veo una alerta que indica que se ha superado la cuota de objetos**
- Tenemos una cuota de objeto integrada para ayudar a proteger el servicio. Si tiene demasiados objetos en el directorio que deben sincronizarse con Microsoft 365, deberá [ponerse en contacto con el soporte técnico para productos empresariales](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar la cuota.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>**Necesito saber qué atributos se sincronizan**
- Puede encontrar una lista de todos los atributos que se sincronizan entre el entorno local y la nube [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>**No puedo administrar o quitar objetos que se sincronizaron en la nube**
- ¿Está preparado para administrar objetos solo en la nube? ¿O hay un objeto que se eliminó localmente pero está bloqueado en la nube? Eche un vistazo a este artículo sobre los [errores de solución de problemas durante la sincronización](https://go.microsoft.com/fwlink/p/?linkid=842044) y el artículo de [soporte técnico](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obtener instrucciones sobre cómo resolver estos problemas.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>**He recibido un mensaje de error que indica que mi compañía ha superado el número de objetos que se pueden sincronizar**
- Para obtener más información sobre este problema, vea [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Otros recursos

- [Script para corregir los nombres principales de usuario duplicados](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Cómo preparar un dominio no enrutable (como un dominio. local) para la sincronización de directorios](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Secuencia de comandos para contar objetos sincronizados totales](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Solución de problemas de AD FS 2,0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Usar PowerShell para corregir atributos DisplayName vacíos para grupos habilitados para correo](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Usar PowerShell para corregir un UPN duplicado](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Usar PowerShell para corregir direcciones de correo electrónico duplicadas](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Herramientas de diagnóstico

La [herramienta IDFix](prepare-directory-attributes-for-synch-with-idfix.md) se usa para realizar la detección y la corrección de objetos de identidad y sus atributos en un entorno local de Active Directory, como preparación para la migración a Microsoft 365. IDFix está destinado a los administradores de Active Directory responsables de la sincronización de directorios con el servicio de Microsoft 365. 

[Descargue la herramienta IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) desde el centro de descarga de Microsoft.