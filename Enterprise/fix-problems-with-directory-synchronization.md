---
title: Solucionar problemas de la sincronización de directorios para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Priority
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
description: Describe las causas comunes de problemas con la sincronización de directorios en Office 365 y ofrece unos cuantos métodos para ayudar a identificarlos y resolverlos.
ms.openlocfilehash: fac0c477f3c68271a2f0f8c4e2a09fc051fe1ce4
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502655"
---
# <a name="fixing-problems-with-directory-synchronization-for-microsoft-365"></a>Solucionar problemas de la sincronización de directorios para Microsoft 365

La sincronización de directorios permite continuar con la administración de usuarios y grupos en una implementación local y sincronizar las adiciones, las eliminaciones y los cambios en la nube. Pero la configuración es algo complicada y en ocasiones puede resultar difícil identificar el origen de los problemas. Contamos con los recursos para ayudarle a identificar posibles problemas y a resolverlos.
  
## <a name="how-do-i-know-if-something-is-wrong"></a>¿Cómo puedo saber si algo va mal?

La primera indicación que algo va mal es cuando el icono del estado de DirSync en el centro de administración de Microsoft 365 indica que hay un problema.
  
También recibirá un correo de Microsoft 365 (al correo electrónico alternativo y al correo electrónico de administrador) que indica que su inquilino ha detectado errores de sincronización de directorios. Para obtener información detallada, vea [Identificar errores de sincronización de directorios en Microsoft 365](identify-directory-synchronization-errors.md).
  
## <a name="how-do-i-get-azure-active-directory-connect-tool"></a>¿Cómo puedo obtener la herramienta Azure Active Directory Connect?

En el [Centro de administración de Microsoft 365](https://admin.microsoft.com), vaya a **Usuarios** \> **Usuarios activos**. Haga clic en el menú **Más** (puntos suspensivos) y seleccione **Sincronización de directorios**. 
  
Siga las [instrucciones del asistente](set-up-directory-synchronization.md) para descargar Azure AD Connect. 
  
Si todavía está usando la sincronización (DirSync) de Azure Active Directory (Azure AD), eche un vistazo a [Cómo solucionar los problemas de instalación de la herramienta de sincronización de Azure Active Directory y de los mensajes de error del asistente de configuración en Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=396717) para obtener información sobre los requisitos del sistema para instalar dirsync, los permisos que necesita y cómo solucionar los errores comunes. 
  
Para actualizar desde la sincronización de Azure AD a Azure AD Connect, vea [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="resolving-common-causes-of-problems-with-directory-synchronization-in-microsoft-365"></a>Resolver causas comunes de los problemas de la sincronización de directorios de Microsoft 365

### <a name="synchronized-objects-arent-appearing-or-updating-online-or-im-getting-synchronization-error-reports-from-the-service"></a>Los objetos sincronizados no aparecen o no se actualizan en línea, o recibo informes de errores de sincronización del servicio.

- [Resistencia de atributo duplicado y sincronización de identidad](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-syncservice-duplicate-attribute-resiliency)

### <a name="i-have-an-alert-in-the-admin-center-or-am-receiving-automated-emails-that-there-hasnt-been-a-recent-synchronization-event"></a>Tengo una alerta en el centro de administración o recibo correos electrónicos automatizados que indican que no ha habido ningún evento de sincronización reciente
- [Solucionar problemas de conectividad con Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/tshoot-connect-connectivity)
- [Cuentas y permisos de Azure AD Connect](https://go.microsoft.com/fwlink/p/?LinkId=820598)
- [Sincronización de Azure AD Connect: Cómo administrar la cuenta de servicio de Azure AD](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-azureadaccount)
- [La sincronización de directorios con Azure Active Directory se detiene o le advierte que la sincronización no se ha registrado en más de un día](https://support.microsoft.com/help/2882421/directory-synchronization-to-azure-active-directory-stops-or-you-re-warned-that-sync-hasn-t-registered-in-more-than-a-day)

### <a name="password-hashes-arent-synchronizing-or-im-seeing-an-alert-in-the-admin-center-that-there-hasnt-been-a-recent-password-hash-synchronization"></a>Los hash de contraseñas no se sincronizan o veo una alerta en el centro de administración que indica que no ha habido ninguna sincronización de los hash de contraseñas reciente
- [Implementar la sincronización de hash de contraseñas con la sincronización de Azure AD Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-password-hash-synchronization)

### <a name="im-seeing-an-alert-that-object-quota-exceeded"></a>Veo una alerta que indica que se ha superado la cuota de objetos
- Se aplica una cuota de objetos integrada para ayudar a proteger el servicio. Si en su directorio hay demasiados objetos deben sincronizarse en Microsoft 365, [Póngase en contacto con soporte técnico para productos para empresas](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) para aumentar la cuota.

### <a name="i-need-to-know-which-attributes-are-synchronized"></a>Necesito saber qué atributos están sincronizados
- Puede ver una lista de todos los atributos sincronizados entre la instalación local y la nube [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396719).

### <a name="i-cant-manage-or-remove-objects-that-were-synchronized-to-the-cloud"></a>No puedo administrar o quitar objetos sincronizados con la nube
- ¿Está listo para administrar objetos en la nube exclusivamente? ¿O un objeto que se eliminó en la implementación local ha quedado atascado en la nube? Eche un vistazo a [Solución de problemas de errores durante la sincronización](https://go.microsoft.com/fwlink/p/?linkid=842044) y [artículo de soporte técnico](https://go.microsoft.com/fwlink/p/?LinkId=396720) para obtener instrucciones sobre cómo resolver estos problemas.

### <a name="i-got-an-error-message-that-my-company-has-exceeded-the-number-of-objects-that-can-be-synchronized"></a>Un mensaje de error indica que mi compañía ha excedido el número de objetos que se pueden sincronizar
- Puede leer más sobre este problema [aquí](https://go.microsoft.com/fwlink/p/?LinkId=396721).
   
## <a name="other-resources"></a>Otros recursos

- [Script para corregir los nombres principales de usuario duplicados](https://go.microsoft.com/fwlink/p/?LinkId=396725)
    
- [Cómo preparar un dominio no enrutable (por ejemplo, el dominio local) para la sincronización de directorios](prepare-a-non-routable-domain-for-directory-synchronization.md)
    
- [Script para contar el total de objetos sincronizados](https://go.microsoft.com/fwlink/p/?LinkId=396726)
    
- [Solución de problemas de AD FS 2.0](https://go.microsoft.com/fwlink/p/?LinkId=396727)
    
- [Usar PowerShell para corregir atributos DisplayName vacíos de grupos habilitados para correo](https://go.microsoft.com/fwlink/p/?LinkId=396728)
    
- [Usar PowerShell para corregir UPN duplicados](https://go.microsoft.com/fwlink/p/?LinkId=396730)
    
- [Usar PowerShell para corregir direcciones de correo duplicadas](https://go.microsoft.com/fwlink/p/?LinkId=396731)
    
## <a name="diagnostic-tools"></a>Herramientas de diagnóstico

[La herramienta IDFix](prepare-directory-attributes-for-synch-with-idfix.md) se usa para realizar detecciones y correcciones de objetos de identidad y de sus atributos en entornos de Active Directory locales en la preparación para la migración a Microsoft 365. IDFix está pensado para los administradores de Active Directory responsables de la sincronización de directorios con el servicio de Microsoft 365. 

[Descargue la herramienta IDFix](https://go.microsoft.com/fwlink/p/?LinkId=396718) desde el centro de descarga de Microsoft.
