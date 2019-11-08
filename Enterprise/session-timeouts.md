---
title: Tiempos de espera de sesión para Office 365
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 37a5c116-5b07-4f70-8333-5b86fd2c3c40
ms.collection:
- M365-security-compliance
description: Los tiempos de espera de sesión se usan para equilibrar la seguridad y la facilidad de acceso en aplicaciones cliente de Office 365.
ms.openlocfilehash: e39d578f0a5f193691724e3b3a0c42db0ad1011b
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38030925"
---
# <a name="session-timeouts-for-office-365"></a>Tiempos de espera de sesión para Office 365

La duración de las sesiones es una parte importante de la autenticación de Office 365 y es un componente importante para equilibrar la seguridad y el número de veces que se solicitan sus credenciales a los usuarios.
  
## <a name="session-times-for-office-365-services"></a>Tiempos de sesión para servicios de Office 365

Cuando los usuarios se autentican en cualquiera de las aplicaciones móviles o aplicaciones Web de Office 365, se establece una sesión. Mientras dure la sesión, los usuarios no tendrán que volver a autenticarse. Las sesiones pueden expirar cuando los usuarios están inactivos, cuando cierran el explorador o la pestaña, o cuando el token de autenticación expira por otros motivos, como cuando se restableció su contraseña. Los servicios de Office 365 tienen tiempos de espera de sesión diferentes para coincidir con el uso típico de cada servicio.
  
En la siguiente tabla se enumeran las duraciones de sesión para los servicios de Office 365:
  
|**Servicio de Office 365**|**Tiempo de espera de sesión**|
|:-----|:-----|
|Centro de administración de 365 de Microsoft  <br/> |Se le pedirá que proporcione las credenciales del centro de administración cada 8 horas.  <br/> |
|SharePoint Online  <br/> |5 días de inactividad siempre que los usuarios elijan **mantener la sesión iniciada**. Si el usuario obtiene acceso a SharePoint Online una vez transcurridas 24 o más horas desde el inicio de sesión anterior, el valor de tiempo de espera se restablece en 5 días.  <br/> |
|Outlook Web App  <br/> |6 horas.  <br/> Puede cambiar este valor usando el parámetro _ActivityBasedAuthenticationTimeoutInterval_ en el cmdlet [set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) .  <br/> |
|Azure Active Directory  <br/> (Lo usan los clientes de Office 2013 con la autenticación moderna habilitada)  <br/> | La autenticación moderna usa tokens de acceso y tokens de actualización para conceder acceso de usuario a los recursos de Office 365 mediante Azure Active Directory. Un token de acceso es un token web JSON que se proporciona después de una autenticación correcta y es válido durante 1 hora. También se proporciona un token de actualización con una duración más larga. Cuando los tokens de acceso expiran, los clientes de Office usan un token de actualización válido para obtener un nuevo token de acceso. Este intercambio es correcto si la autenticación inicial del usuario sigue siendo válida.  <br/>  Los tokens de actualización son válidos durante 90 días y con uso continuo, pueden ser válidos hasta que se revocan.  <br/>  Los tokens de actualización se pueden invalidar con varios eventos como:  <br/>  La contraseña del usuario ha cambiado desde que se emitió el token de actualización.  <br/>  Un administrador puede aplicar directivas de acceso condicional que restringen el acceso al recurso al que el usuario intenta obtener acceso.  <br/> |
|Aplicaciones móviles de SharePoint y OneDrive para Android, iOS y Windows 10  <br/> |La duración predeterminada para el token de acceso es 1 hora. El tiempo de inactividad máximo predeterminado del token de actualización es de 90 días.  <br/> [Obtenga más información sobre tokens y cómo configurar las duraciones de tokens](https://docs.microsoft.com/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Para revocar el token de actualización, puede restablecer la contraseña de Office 365 del usuario.  <br/> |
|Yammer con el inicio de sesión de Office 365  <br/> |Duración del explorador. Si los usuarios cierran el explorador y tienen acceso a Yammer en un nuevo explorador, Yammer los volverá a autenticar con Office 365. Si los usuarios usan exploradores de terceros que almacenan en la memoria caché cookies, es posible que no tengan que volver a autenticarse al volver a abrir el explorador.  <br/> > [!NOTE]> esto solo es válido para redes que usen el inicio de sesión de Office 365 para Yammer.           |
   

