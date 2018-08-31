---
title: Funcionamiento de la autenticación moderna para aplicaciones cliente de Office 2013 y Office 2016
ms.author: sirkkuw
author: Sirkkuw
manager: laurawi
ms.date: 8/1/2017
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- GMA150
- GPA150
- GEA150
- BCS160
ms.assetid: e4c45989-4b1a-462e-a81b-2a13191cf517
description: Obtenga información sobre cómo funciona la autenticación moderna de Office 365 diferente para las aplicaciones de cliente de 2016 y Office 2013.
ms.openlocfilehash: a9b6e2dabec9fb59f5fd7f60508dcbc6fe840cfb
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542866"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Funcionamiento de la autenticación moderna para aplicaciones cliente de Office 2013 y Office 2016

Lea este artículo para saber cómo utilizan las características de autenticación moderno Office 2013 y aplicaciones cliente de Office 2016 basándose en la configuración de autenticación en el inquilino de Office 365 para Exchange Online, SharePoint Online y Skype para profesionales en línea.
  
## <a name="availability-of-modern-authentication-for-office-365-services"></a>Disponibilidad de autenticación moderna para servicios de Office 365

Para los servicios de Office 365, el estado predeterminado de autenticación moderno es:
  
- **Activado para Exchange Online de forma predeterminada.** Vea [Habilitar o deshabilitar la autenticación moderna en Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) para activarla o desactivar. 
    
- **Activado para SharePoint Online de forma predeterminada.** 
    
- **Activado para Skype para profesionales en línea de forma predeterminada.** Vea [Habilitar Skype para empresarial en línea para la autenticación moderna ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)para activarla o desactivar.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportamiento de inicio de sesión de las aplicaciones cliente de Office

Aplicaciones de cliente de Office 2013 admiten la autenticación heredada de forma predeterminada. Heredado significa que admiten la autenticación en el inicio de sesión de Microsoft Online, Ayudante o básica. En orden para estos clientes a usar las características de autenticación moderno, las ventanas de cliente tiene establecer las claves del registro. Para obtener instrucciones, vea [Habilitar moderno Authentication for Office 2013 en dispositivos de Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).
  
Lea [cómo usar autenticación moderno (ADAL) con Skype para la empresa](https://go.microsoft.com/fwlink/p/?LinkId=785431) para obtener más información acerca de cómo funciona con Skype para la empresa. 
  
Los clientes de Office 2016 admiten autenticación moderna de forma predeterminada, y es necesario realizar ninguna acción para que el cliente usar estos flujos de nuevo. Sin embargo, es necesario una acción explícita para usar la autenticación heredada.
  
Haga clic en los vínculos siguientes para ver cómo funciona la autenticación de cliente de Office 2013 y Office 2016 con los servicios de Office 365 dependiendo de si está activada autenticación moderna.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype Empresarial Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
### <a name="exchange-online"></a>Exchange Online

En la siguiente tabla se describe el comportamiento de la autenticación para las aplicaciones cliente de Office 2013 o 2016 de Office cuando se conecten a Exchange Online con o sin autenticación moderna.
  
|Aplicación de cliente de Office versión ***|Clave del registro está presente? ***|La autenticación en moderno? ***|Comportamiento de la autenticación con autenticación moderno activado para el inquilino (valor predeterminado) o ***|Comportamiento de la autenticación con autenticación moderno desactivarse para el inquilino ***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sí  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, a continuación, se usa la autenticación básica. Servidor rechaza la autenticación moderna cuando no está habilitado el inquilino.  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, a continuación, se usa la autenticación básica. Servidor rechaza la autenticación moderna cuando no está habilitado el inquilino.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, a continuación, se usa la autenticación básica. Servidor rechaza la autenticación moderna cuando no está habilitado el inquilino.  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, a continuación, se usa la autenticación básica. Servidor rechaza la autenticación moderna cuando no está habilitado el inquilino.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 0  <br/> |No  <br/> |Autenticación básica  <br/> |Autenticación básica  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Autenticación básica  <br/> |Autenticación básica  <br/> |
|Office 2013  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, a continuación, se usa la autenticación básica. Servidor rechaza la autenticación moderna cuando no está habilitado el inquilino.  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, a continuación, se usa la autenticación básica. Servidor rechaza la autenticación moderna cuando no está habilitado el inquilino.  <br/> |
   
### <a name="sharepoint-online"></a>SharePoint Online
<a name="BK_SharePointOnline"> </a>

En la siguiente tabla se describe el comportamiento de la autenticación para las aplicaciones cliente de Office 2013 o 2016 de Office cuando intenten conectarse a SharePoint Online con o sin autenticación moderna.
  
|Aplicación de cliente de Office versión ***|Clave del registro está presente? ***|La autenticación en moderno? ***|Comportamiento de la autenticación con autenticación moderno activado para el inquilino (valor predeterminado) o ***|Comportamiento de la autenticación con autenticación moderno desactivarse para el inquilino ***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sí  <br/> |Autenticación moderna.  <br/> |No se puede conectar.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Autenticación moderna.  <br/> |No se puede conectar.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 0  <br/> |No  <br/> |Microsoft Online-Asistente de sesión solo.  <br/> |Microsoft Online-Asistente de sesión solo.  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Microsoft Online-Asistente de sesión solo.  <br/> |Microsoft Online-Asistente de sesión solo.  <br/> |
|Office 2013  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Autenticación moderna.  <br/> |No se puede conectar.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype Empresarial Online
<a name="BK_SFBO"> </a>

En la siguiente tabla se describe el comportamiento de la autenticación para aplicaciones de cliente de Office 2016 o Office 2013 cuando se conectan a Skype para profesionales en línea con o sin autenticación moderna.
  
|Aplicación de cliente de Office versión ***|Clave del registro está presente? ***|La autenticación en moderno? ***|Comportamiento de la autenticación con autenticación moderno activado para el inquilino ***|Comportamiento de la autenticación con autenticación moderno desactivado para el inquilino (valor predeterminado) o ***|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No, o EnableADAL = 1  <br/> |Sí  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, se usa el Ayudante para el inicio de sesión de Microsoft Online. Servidor rechaza la autenticación moderna cuando Skype para los inquilinos empresarial en línea no están habilitados.  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, se usa el Ayudante para el inicio de sesión de Microsoft Online. Servidor rechaza la autenticación moderna cuando Skype para los inquilinos empresarial en línea no están habilitados.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, se usa el Ayudante para el inicio de sesión de Microsoft Online. Servidor rechaza la autenticación moderna cuando Skype para los inquilinos empresarial en línea no están habilitados.  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, se usa el Ayudante para el inicio de sesión de Microsoft Online. Servidor rechaza la autenticación moderna cuando Skype para los inquilinos empresarial en línea no están habilitados.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 0  <br/> |No  <br/> |Microsoft Online-Asistente de sesión solo.  <br/> |Microsoft Online-Asistente de sesión solo.  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Microsoft Online-Asistente de sesión solo.  <br/> |Microsoft Online-Asistente de sesión solo.  <br/> |
|Office 2013  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Primero se intenta la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderno, se usa el Ayudante para el inicio de sesión de Microsoft Online. Servidor rechaza la autenticación moderna cuando Skype para los inquilinos empresarial en línea no están habilitados.  <br/> |Microsoft Online-Asistente de sesión solo.  <br/> |
   
## <a name="see-also"></a>Vea también

[Usar la autenticación moderna Office 365 con los clientes de Office](https://support.office.com/article/776c0036-66fd-41cb-8928-5495c0f9168a)

