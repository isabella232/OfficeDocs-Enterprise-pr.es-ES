---
title: Cómo funciona la autenticación moderna para las aplicaciones de cliente de Office 2013 y Office 2016
ms.author: tracyp
author: MSFTTracyP
manager: laurawi
ms.date: 8/1/2017
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
ms.collection:
- M365-security-compliance
description: Obtenga información sobre cómo funciona la autenticación moderna de Office 365 de forma diferente para las aplicaciones cliente de Office 2013 y 2016.
ms.openlocfilehash: 081d8e70e84f816e925ba421d7f740e6063ca371
ms.sourcegitcommit: c5ea5b8d16201551f82b88738d92c58a7a92c74f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/18/2020
ms.locfileid: "44280219"
---
# <a name="how-modern-authentication-works-for-office-2013-and-office-2016-client-apps"></a>Cómo funciona la autenticación moderna para las aplicaciones de cliente de Office 2013 y Office 2016

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Lea este artículo para obtener información sobre cómo las aplicaciones cliente de Office 2013 y Office 2016 usan las características de autenticación moderna basadas en la configuración de autenticación en el inquilino de Office 365 para Exchange Online, SharePoint Online y Skype empresarial online.

> [!NOTE]
> Las aplicaciones cliente heredadas, como Office 2010 y Office para Mac 2011, no admiten la autenticación moderna y solo se pueden usar con la autenticación básica.

## <a name="availability-of-modern-authentication-for-office-365-services"></a>Disponibilidad de la autenticación moderna para los servicios de Office 365

Para los servicios de Office 365, el estado predeterminado de la autenticación moderna es:
  
- Activado **para Exchange online de forma** predeterminada. Consulte [habilitar o deshabilitar la autenticación moderna en Exchange Online](https://support.office.com/article/58018196-f918-49cd-8238-56f57f38d662) para activarla o desactivarla. 
    
- Activado **para SharePoint** online de forma predeterminada. 
    
- Activado **para Skype** empresarial online de forma predeterminada. Consulte [Habilitar Skype empresarial online para la autenticación moderna ](https://social.technet.microsoft.com/wiki/contents/articles/34339.skype-for-business-online-enable-your-tenant-for-modern-authentication.aspx)para desactivarla o desactivarla.

> [!NOTE]
> En el caso de los inquilinos creados**antes** del 1 de agosto de 2017, la autenticación moderna está **desactivada**de forma predeterminada para Exchange Online y Skype para empresas Online.
    
## <a name="sign-in-behavior-of-office-client-apps"></a>Comportamiento de inicio de sesión de las aplicaciones cliente de Office

Las aplicaciones cliente de Office 2013 admiten la autenticación heredada de forma predeterminada. Heredado significa que admiten el Asistente para inicio de sesión de Microsoft online o la autenticación básica. Para que estos clientes usen las características de autenticación moderna, el cliente de Windows debe tener establecidas claves del registro. Para obtener instrucciones, consulte [Habilitar la autenticación moderna para Office 2013 en dispositivos Windows](https://support.office.com/article/7dc1c01a-090f-4971-9677-f1b192d6c910).

Para habilitar la autenticación moderna para cualquier dispositivo con Windows (por ejemplo, en portátiles y tabletas), que tienen Microsoft Office 2013 instalado, debe configurar las siguientes claves del registro. Las claves se tienen que establecer en cada dispositivo en el que quiera habilitar la autenticación moderna:
  
|**Clave del registro**|**Type**|**Valor** |
|:-------|:------:|--------:|
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\EnableADAL  |REG_DWORD  |1   |
|HKCU\SOFTWARE\Microsoft\Office\15.0\Common\Identity\Version |REG_DWORD |1  |
  
Descubra [Cómo usar la autenticación moderna (Adal) con Skype](https://go.microsoft.com/fwlink/p/?LinkId=785431) empresarial para obtener información sobre cómo funciona con Skype empresarial. 
  
Los clientes de Office 2016 admiten la autenticación moderna de forma predeterminada y no es necesario realizar ninguna acción para que el cliente use estos nuevos flujos. Sin embargo, se necesita una acción explícita para usar la autenticación heredada.
  
Haga clic en los siguientes vínculos para ver cómo funciona la autenticación de cliente de Office 2013 y Office 2016 con los servicios de Office 365 en función de si la autenticación moderna está activada o no.
  
- [Exchange Online](modern-auth-for-office-2013-and-2016.md#BK_EchangeOnline)
    
- [SharePoint Online](modern-auth-for-office-2013-and-2016.md#BK_SharePointOnline)
    
- [Skype Empresarial Online](modern-auth-for-office-2013-and-2016.md#BK_SFBO)
    
<a name="BK_EchangeOnline"> </a>
### <a name="exchange-online"></a>Exchange Online

En la siguiente tabla se describe el comportamiento de autenticación para las aplicaciones cliente de Office 2013 u Office 2016 cuando se conectan a Exchange Online con o sin autenticación moderna.
  
|Versión de la aplicación cliente de Office * * * *|¿La clave del registro está presente? * * * *|Autenticación moderna en? * * * *|Comportamiento de autenticación con la autenticación moderna activada para el inquilino (predeterminado) * * * *|Comportamiento de autenticación con la autenticación moderna desactivada para el inquilino * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No <br> AlwaysUseMSOAuthForAutoDiscover = 1 <br/> |Sí  <br/> |Fuerza la autenticación moderna en Outlook 2010, 2013 o 2016 <br/> [Más información](https://support.microsoft.com/help/3126599/outlook-prompts-for-password-when-modern-authentication-is-enabled)|Fuerza la autenticación moderna en el cliente de Outlook.<br/> |
|Office 2016  <br/> |No o EnableADAL = 1  <br/> |Sí  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa la autenticación básica. El servidor rechaza la autenticación moderna cuando el inquilino no está habilitado.  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa la autenticación básica. El servidor rechaza la autenticación moderna cuando el inquilino no está habilitado.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa la autenticación básica. El servidor rechaza la autenticación moderna cuando el inquilino no está habilitado.  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa la autenticación básica. El servidor rechaza la autenticación moderna cuando el inquilino no está habilitado.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 0  <br/> |No  <br/> |Autenticación básica  <br/> |Autenticación básica  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Autenticación básica  <br/> |Autenticación básica  <br/> |
|Office 2013  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa la autenticación básica. El servidor rechaza la autenticación moderna cuando el inquilino no está habilitado.  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa la autenticación básica. El servidor rechaza la autenticación moderna cuando el inquilino no está habilitado.  <br/> |
   
<a name="BK_SharePointOnline"> </a>
### <a name="sharepoint-online"></a>SharePoint Online

En la siguiente tabla se describe el comportamiento de autenticación para las aplicaciones cliente de Office 2013 u Office 2016 cuando se conectan a SharePoint Online con o sin autenticación moderna.
  
|Versión de la aplicación cliente de Office * * * *|¿La clave del registro está presente? * * * *|Autenticación moderna en? * * * *|Comportamiento de autenticación con la autenticación moderna activada para el inquilino (predeterminado) * * * *|Comportamiento de autenticación con la autenticación moderna desactivada para el inquilino * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No o EnableADAL = 1  <br/> |Sí  <br/> |Solo la autenticación moderna.  <br/> |Error al conectar.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Solo la autenticación moderna.  <br/> |Error al conectar.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 0  <br/> |No  <br/> |Solo ayudante para el inicio de sesión de Microsoft online.  <br/> |Solo ayudante para el inicio de sesión de Microsoft online.  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Solo ayudante para el inicio de sesión de Microsoft online.  <br/> |Solo ayudante para el inicio de sesión de Microsoft online.  <br/> |
|Office 2013  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Solo la autenticación moderna.  <br/> |Error al conectar.  <br/> |
   
### <a name="skype-for-business-online"></a>Skype Empresarial Online
<a name="BK_SFBO"> </a>

En la tabla siguiente se describe el comportamiento de autenticación para las aplicaciones cliente de Office 2013 u Office 2016 cuando se conectan a Skype empresarial online con o sin autenticación moderna.
  
|Versión de la aplicación cliente de Office * * * *|¿La clave del registro está presente? * * * *|Autenticación moderna en? * * * *|Comportamiento de autenticación con la autenticación moderna activada para el inquilino * * * *|Comportamiento de autenticación con la autenticación moderna desactivada para el inquilino (predeterminado) * * * *|
|:-----|:-----|:-----|:-----|:-----|
|Office 2016  <br/> |No o EnableADAL = 1  <br/> |Sí  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa el Asistente para el inicio de sesión de Microsoft online. El servidor rechaza la autenticación moderna cuando los inquilinos de Skype empresarial online no están habilitados.  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa el Asistente para el inicio de sesión de Microsoft online. El servidor rechaza la autenticación moderna cuando los inquilinos de Skype empresarial online no están habilitados.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa el Asistente para el inicio de sesión de Microsoft online. El servidor rechaza la autenticación moderna cuando los inquilinos de Skype empresarial online no están habilitados.  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa el Asistente para el inicio de sesión de Microsoft online. El servidor rechaza la autenticación moderna cuando los inquilinos de Skype empresarial online no están habilitados.  <br/> |
|Office 2016  <br/> |Sí, EnableADAL = 0  <br/> |No  <br/> |Solo ayudante para el inicio de sesión de Microsoft online.  <br/> |Solo ayudante para el inicio de sesión de Microsoft online.  <br/> |
|Office 2013  <br/> |No  <br/> |No  <br/> |Solo ayudante para el inicio de sesión de Microsoft online.  <br/> |Solo ayudante para el inicio de sesión de Microsoft online.  <br/> |
|Office 2013  <br/> |Sí, EnableADAL = 1  <br/> |Sí  <br/> |Se intenta primero la autenticación moderna. Si el servidor rechaza una conexión de autenticación moderna, se usa el Asistente para el inicio de sesión de Microsoft online. El servidor rechaza la autenticación moderna cuando los inquilinos de Skype empresarial online no están habilitados.  <br/> |Solo ayudante para el inicio de sesión de Microsoft online.  <br/> |
   
## <a name="see-also"></a>Vea también

[Habilitar la autenticación moderna para Office 2013 en dispositivos Windows](https://support.office.com/article/enable-modern-authentication-for-office-2013-on-windows-devices-7dc1c01a-090f-4971-9677-f1b192d6c910)

[Planeación de multi-factor Authentication para implementaciones de Office 365 (para administradores de Office 365)](https://support.office.com/article/plan-for-multi-factor-authentication-for-office-365-deployments-043807b2-21db-4d5c-b430-c8a6dee0e6ba)

[Inicie sesión en Office 365 con verificación en dos pasos (para usuarios finales)](https://support.office.com/article/sign-in-to-office-365-with-2-step-verification-2b856342-170a-438e-9a4f-3c092394d3cb)

[Información general de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
