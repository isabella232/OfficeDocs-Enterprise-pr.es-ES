---
title: Tiempos de espera de sesión para Office 365
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
ms.date: 6/29/2018
ms.audience: Admin
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
description: Tiempos de espera de sesión se utilizan para equilibrar la seguridad y la facilidad de acceso en las aplicaciones cliente de Office 365.
ms.openlocfilehash: dda13f280149c969354ae1f0eac336f1d8ed23e7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542825"
---
# <a name="session-timeouts-for-office-365"></a>Tiempos de espera de sesión para Office 365

Duración de sesión es una parte importante de la autenticación para Office 365 y un componente importante en el equilibrio de seguridad y el número de veces que se le pide a los usuarios sus credenciales.
  
## <a name="session-times-for-office-365-services"></a>Tiempos de sesión de servicios de Office 365

Cuando los usuarios se autentican en cualquiera de las aplicaciones web de Office 365 o aplicaciones móviles, se establece una sesión. Para la duración de la sesión, los usuarios no necesitan volver a autenticar. Las sesiones pueden caducar cuando los usuarios están inactivos, cuando cierre el explorador o ficha, o cuando expire su token de autenticación por otras razones, como cuando se ha restablecido su contraseña. Los servicios de Office 365 tengan tiempos de espera de sesión diferente para que se correspondan con el uso normal de cada servicio.
  
En la siguiente tabla se enumera la vigencia de sesión para los servicios de Office 365:
  
|**Servicio de Office 365**|**Tiempo de espera de sesión**|
|:-----|:-----|
|Centro de administración de Office 365  <br/> |Le pedirá que proporcione las credenciales para el centro de administración de cada 8 horas.  <br/> |
|SharePoint Online  <br/> |5 días de inactividad mientras los usuarios elige **mantener la sesión iniciada**. Si el usuario obtiene acceso a SharePoint Online nuevamente después de 24 o más horas han transcurrido desde el inicio de sesión de anterior, el valor de tiempo de espera se restablece en 5 días.<br/> |
|Outlook Web App  <br/> |6 horas.  <br/> Puede cambiar este valor mediante el parámetro _ActivityBasedAuthenticationTimeoutInterval_ en el cmdlet [Set-OrganizationConfig](https://go.microsoft.com/fwlink/p/?LinkId=615378) .  <br/> |
|Azure Active Directory  <br/> (Usado por los clientes de Office 2013 Windows con autenticación moderna habilitada)  <br/> | Autenticación moderna usa tokens de acceso y tokens de actualización para conceder acceso de usuario a los recursos de Office 365 con Azure Active Directory. Un token de acceso es un Token de Web de JSON proporcionado después de una autenticación correcta y es válido para 1 hora. También se proporciona un token de actualización con una vigencia más larga. Cuando expiren tokens de acceso, los clientes de Office utilizan un token de actualización válida para obtener un nuevo token de acceso. Este intercambio se realiza correctamente si la autenticación inicial del usuario todavía es válida.  <br/>  Tokens de actualización son válidos durante 90 días, y con uso continuo, puede ser válidos hasta que se ha revocado.  <br/>  Actualizar los tokens se pueden invalidar por varios eventos tales como:  <br/>  Contraseña del usuario ha cambiado desde que se emitió el token de actualización.  <br/>  Un administrador puede aplicar las directivas de acceso condicional que restricción el acceso a los recursos que el usuario está intentando obtener acceso a.  <br/> |
|Aplicaciones móviles de SharePoint y OneDrive para Android, iOS y 10 de Windows  <br/> |La duración predeterminada para el token de acceso es 1 hora. El tiempo de inactividad máximo predeterminado de token de actualización es de 90 días.<br/> [Encontrará más información sobre los tokens y cómo configurar duraciones de símbolo (token)](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-configurable-token-lifetimes) <br/> Para revocar la actualización de símbolo (token), puede restablecer la contraseña del usuario Office 365  <br/> |
|Yammer con inicio de sesión en Office 365  <br/> |Duración del explorador. Si los usuarios cierre el explorador y tener acceso a Yammer en una nueva ventana del explorador, Yammer autenticará volver a con Office 365. Si los usuarios utilizan exploradores de terceros que las cookies de la memoria caché, es posible que no deben volver a autenticar cuando vuelva a abrir el explorador.<br/> > [!NOTE]> Esto sólo es válido para las redes con inicio de sesión en Office 365 para Yammer.           |
   

