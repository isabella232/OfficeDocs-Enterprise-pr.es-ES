---
title: Introducción a la autenticación moderna híbrida y requisitos previos para el uso con servidores locales de Skype Empresarial y Exchange
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 04/15/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
f1.keywords:
- NOCSH
description: La autenticación moderna es un método de administración de identidades que ofrece autenticación y autorización de usuarios más seguras. Está disponible para implementaciones híbridas de servidores de Skype Empresarial y Exchange, así como para entornos híbridos de dominio dividido de Skype Empresarial. Este artículo contiene vínculos a los documentos relacionados sobre los requisitos previos, la configuración o desactivación de la autenticación moderna e información para algunos de los clientes relacionados (como  los clientes de Skype y Outlook).
ms.openlocfilehash: df755c8af161609c1c18dbe066662aaf1d410429
ms.sourcegitcommit: a9021ba0800ffc0da21cf2c4da67ab1da2d97099
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2020
ms.locfileid: "46571053"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Introducción a la autenticación moderna híbrida y requisitos previos para el uso en Skype Empresarial y los servidores de Exchange locales

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

La _autenticación moderna_ es un método de administración de identidades que ofrece autenticación y autorización de usuarios más seguras. Está disponible para implementaciones híbridas de Office 365 de servidores de Skype Empresarial y Exchange, así como para entornos híbridos de dominio dividido de Skype Empresarial. Este artículo contiene vínculos a los documentos relacionados sobre los requisitos previos, la configuración o desactivación de la autenticación moderna e información para algunos de los clientes relacionados (como  los clientes de Skype y Outlook).
  
- [¿Qué es la autenticación moderna?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [¿Qué cambia cuando uso la autenticación moderna?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Comprobar el estado de la autenticación moderna de su entorno local](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [¿Cumple los requisitos previos de la autenticación moderna?](#do-you-meet-modern-authentication-prerequisites)
- [¿Qué más necesito saber antes de comenzar?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>¿Qué es la autenticación moderna?
<a name="BKMK_WhatisModAuth"> </a>

La autenticación moderna es un término genérico para una combinación d métodos de autenticación y autorización entre un cliente (por ejemplo, el equipo portátil o el teléfono) y un servidor, así como algunas medidas de seguridad que dependen de las directivas de acceso que puede que ya conozca. Incluye:
  
- **Métodos de autenticación**: autenticación multifactor (MFA), autenticación por tarjeta inteligente, autenticación basada en certificado del cliente
- **Métodos de autorización**: la implementación de Microsoft de Open Authorization (OAuth).
- **Directivas de acceso condicional**: acceso condicional de Azure Active Directory (Azure AD) y administración de aplicaciones móviles (MAM)

La administración de identidades de usuario con la autenticación moderna ofrece a los administradores distintas herramientas para la protección de los recursos y ofrece métodos más seguros de administración de identidades para escenarios locales (Exchange y Skype Empresarial), implementaciones híbridas de Exchange y dominios divididos o híbridos de Skype Empresarial.
  
Tenga en cuenta que, como Skype Empresarial trabaja estrechamente con Exchange, el comportamiento de inicio de sesión que verán los usuarios de los clientes de Skype Empresarial se verán afectados por el estado de la autenticación moderna de Exchange. Esto también se aplicará si tiene una arquitectura híbrida de _dominio dividido_ de Skype Empresarial, en la que tiene tanto Skype Empresarial online como Skype Empresarial local, con usuarios alojados en ambas ubicaciones.

Para más información sobre la autenticación moderna en Office 365, vea [Soporte para aplicaciones cliente de Office 365: autenticación moderna](office-365-client-support-modern-authentication.md).
  
> [!IMPORTANT]
> A partir de agosto de 2017, todos los nuevos espacios empresariales de Office 365 que incluyen Skype Empresarial online y Exchange online tienen la autenticación moderna habilitada de manera predeterminada. Los espacios empresariales preexistentes no tendrán un cambio en el estado de su MA predeterminado, pero todos los nuevos espacios empresariales admiten automáticamente el conjunto ampliado de características de identidad que aparecen anteriormente. Para comprobar el estado de su MA, vea la sección [Comprobar el estado de la autenticación moderna de su entorno local](hybrid-modern-auth-overview.md#BKMK_CheckStatus).
  
## <a name="what-changes-when-i-use-modern-authentication"></a>¿Qué cambia cuando uso la autenticación moderna?
<a name="BKMK_WhatChanges"> </a>

Cuando se usa la autenticación moderna con un servidor de Exchange o Skype Empresarial local, la *autenticación* de los usuarios sigue siendo local, pero la forma de *autorizar* su acceso a los recursos (como archivos o correos electrónicos) cambia. Por este motivo, aunque la autenticación moderna consiste en la comunicación entre el cliente y el servidor, los pasos que se toman durante la configuración de MA hacen que evoSTS (un servicio de token de seguridad usado por Azure AD) se establezca como servidor de autenticación para Skype Empresarial y el servidor de Exchange local.
  
El cambio a evoSTS permite que los servidores locales usen OAuth (emisión de tokens) para autorizar a los clientes, y también el uso de métodos de seguridad comunes en la nube (igual que la autenticación multifactor). Además, el evoSTS emite tokens que permiten que los usuarios soliciten el acceso a los recursos sin proporcionar su contraseña como parte de la solicitud. Independientemente de la ubicación de los usuarios (en línea o en el entorno local) y de la ubicación donde se encuentre el recurso necesario, EvoSTS se convertirá en el centro de autorización de usuarios y clientes cuando se configure la autenticación moderna.
  
Por ejemplo, si un cliente de Skype Empresarial necesita tener acceso al servidor de Exchange para obtener la información de calendario en nombre de un usuario, usará la Biblioteca de autenticación de Active Directory (ADAL) para hacerlo. ADAL es una biblioteca de código diseñada para que los recursos protegidos en el directorio estén disponibles para las aplicaciones de cliente que utilicen tokens de seguridad de OAuth. ADAL funciona con OAuth para comprobar las notificaciones y el intercambio de tokens (en lugar de contraseñas) para conceder a un usuario acceso a un recurso. En el pasado, la autoridad en una transacción como esta (el servidor que sabe cómo validar las notificaciones de usuario y emitir los tokens necesarios) podría haber sido un servicio de token de seguridad local o incluso de Servicios de federación de Active Directory (AD FS). Sin embargo, la autenticación moderna centraliza dicha autoridad al usar Azure AD.
  
Esto también significa que, aunque el servidor de Exchange y los entornos de Skype Empresarial puedan ser totalmente locales, el servidor de autorización estará en línea, y el entorno local debe tener la capacidad de crear y mantener una conexión con la suscripción de Office 365 en la nube (y la instancia de Azure AD que la suscripción usa como directorio).
  
¿Qué no cambia? Tanto si está en un entorno híbrido de dominio dividido como si usa Skype Empresarial y el servidor de Exchange local, todos los usuarios deben autenticarse en primer lugar *localmente*. En una implementación híbrida de la autenticación moderna, _Lyncdiscovery_ y _Autodiscovery_ apuntan al servidor local.
  
> [!IMPORTANT]
> Si necesita averiguar las topologías específicas de Skype Empresarial compatibles con MA, están [documentadas aquí](https://technet.microsoft.com/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Comprobar el estado de la autenticación moderna de su entorno local
<a name="BKMK_CheckStatus"> </a>

Dado que la autenticación moderna cambia el servidor de autorización usado cuando los servicios usan OAuth/S2S, debe averiguar si la autenticación moderna está habilitada o deshabilitada para sus entornos locales de Skype Empresarial y Exchange. Para comprobar el estado de los servidores de Exchange, ejecute el siguiente comando de PowerShell:

```powershell
Get-OrganizationConfig | ft OAuth*
```

Si el valor de la propiedad _OAuth2ClientProfileEnabled_ es **False**, la autenticación moderna está deshabilitada.

Para más información sobre el cmdlet Get-OrganizationConfig, consulte [Get-OrganizationConfig](https://docs.microsoft.com/powershell/module/exchange/organization/get-organizationconfig).

Para comprobar los servidores de Skype Empresarial, ejecute el siguiente comando de PowerShell:

```powershell
Get-CSOAuthConfiguration
```

Si el comando devuelve una propiedad _OAuthServers_ vacía, o si el valor de la propiedad _ClientADALAuthOverride_ no es **Allowed**, la autenticación moderna está deshabilitada.

Para más información sobre el cmdlet Get-CsOAuthConfiguration, vea [Get-CsOAuthConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csoauthconfiguration).
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>¿Cumple los requisitos previos de la autenticación moderna?

Verifique y compruebe estos elementos antes de continuar:
  
- **Específico de Skype Empresarial**
  - Todos los servidores deben tener la actualización acumulativa de mayo de 2017 (CU5) para Skype Empresarial Server 2015 o posterior
    - **Excepción:** Aplicación de sucursal con funciones de supervivencia (SBA) puede estar en la versión actual (basada en Lync 2013)
  - El dominio SIP se ha agregado como un dominio federado en Office 365
  - Todos los front-ends de Skype Empresarial deben tener conexiones salientes a Internet, a las direcciones URL de autenticación de Office 365 (TCP 443) y CRL de raíz de certificado conocidas (TCP 80) enumeradas en las filas 56 y 125 de la sección "Común para Microsoft 365 y Office" de [Intervalos de direcciones IP y URL de Office 365](urls-and-ip-address-ranges.md).
  
- **Skype Empresarial en un entorno híbrido de Office 365**
  - Una implementación de Skype Empresarial Server 2019 con todos los servidores que ejecuten Skype Empresarial Server 2019.
  - Una implementación de Skype Empresarial Server 2015 con todos los servidores que ejecuten Skype Empresarial Server 2015.
  - Una implementación con un máximo de dos versiones de servidor distintas, como se muestra a continuación:
    - Skype Empresarial Server 2015
    - Skype Empresarial Server 2019
  - Todos los servidores de Skype Empresarial deben tener instaladas las últimas actualizaciones acumulativas, consulte [Actualizaciones de Skype Empresarial Server](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) para buscar y administrar todas las actualizaciones disponibles.
  - No hay ningún Lync Server 2010 o 2013 en el entorno híbrido.

>[!NOTE]
>Si los servidores front-end de Skype Empresarial usan un servidor proxy para el acceso a Internet, el número de puerto y la IP del servidor proxy deben especificarse en la sección de configuración del archivo web.config para cada front-end.
  
- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\int\web.config
- C:\Program Files\Skype for Business Server 2015\Web Components\Web ticket\ext\web.config

```xml
<configuration>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</configuration>
```

> [!IMPORTANT]
> Asegúrese de suscribirse a la fuente RSS de [Intervalos de direcciones IP y URL de Office 365](urls-and-ip-address-ranges.md) para mantenerse al día con las listas más recientes de direcciones URL necesarias.
  
- **Específico de Exchange Server**
  - Usa Exchange Server 2013 CU19 o posterior, Exchange Server 2016 CU8 o posterior, o Exchange Server 2019 CU1 o posterior.
  - No hay ningún servidor de Exchange 2010 en el entorno.
  - No se ha configurado la descarga de SSL. Se admite la terminación SSL y el recifrado.
  - En caso de que su entorno use una infraestructura de servidor proxy para permitir que los servidores se conecten a Internet, asegúrese de que todos los servidores de Exchange tengan el servidor proxy definido en la propiedad [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx).
  
- **Implementación local de Exchange Server en un entorno híbrido de Office 365**

  - Si usa Exchange Server 2013, al menos un servidor debe tener instalados los roles de servidor de Acceso de cliente y Buzón de correo. Aunque es posible instalar los roles de Buzón de correo y Acceso de cliente en servidores independientes, le recomendamos que instale los dos en el mismo servidor para proporcionar mayor confiabilidad y mejor rendimiento.
  - Si usa Exchange Server 2016 o una versión posterior, al menos un servidor debe tener instalado el rol de servidor de Buzón de correo.
  - No hay ningún servidor de Exchange 2007 o 2010 en el entorno híbrido.
  - Todos los servidores de Exchange deben tener instaladas las últimas actualizaciones acumulativas, consulte [Actualizar Exchange a las últimas actualizaciones acumulativas](https://docs.microsoft.com/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) para buscar y administrar todas las actualizaciones disponibles.

- **Requisitos de protocolo y el cliente de Exchange**
  
  - Los siguientes clientes son compatibles con la autenticación moderna:

  |**Clientes**|**Protocolo principal**|**Notas**|
  |:-----|:-----|:-----|
  |Outlook 2013 y Outlook 2016  <br/> |MAPI sobre HTTP  <br/> |Se debe habilitar MAPI sobre HTTP en Exchange para poder aprovechar la autenticación moderna con estos clientes (por lo general, se habilitan o son True para las nuevas instalaciones de Exchange 2013 Service Pack 1 y versiones posteriores); para más información, consulte [Cómo funciona la autenticación moderna para las aplicaciones de cliente de Office 2013 y Office 2016](https://docs.microsoft.com/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Asegúrese de que está ejecutando la compilación mínima necesaria de Outlook. Consulte [Últimas actualizaciones para las versiones de Outlook que usan Windows Installer (MSI)](https://docs.microsoft.com/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 para Mac  <br/> |Servicios Web de Exchange  <br/> |  <br/> |
  |Outlook para iOS y Android  <br/> |  <br/> |Consulte [Usar la autenticación moderna híbrida con Outlook para iOS y Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) para más información.  <br/> |
  |Clientes de Exchange ActiveSync (p.ej., correo de iOS11)  <br/> |Exchange ActiveSync  <br/> |Para los clientes de Exchange ActiveSync que son compatibles con la autenticación moderna, debe volver a crear el perfil para cambiar de la autenticación básica a la autenticación moderna.  <br/> |

- **Requisitos previos generales**
  - Si usa AD FS, debe tener Windows 2012 R2 AD FS 3.0 y superior para la federación.
  - Las configuraciones de identidad son cualquiera de los tipos compatibles con Azure AD Connect, como la sincronización de hash de contraseña, la autenticación de paso y el STS local compatibles con Office 365.
  - Tiene Azure AD Connect configurado y funcionando para la replicación y sincronización de usuarios.
  - Ha comprobado que la configuración híbrida está configurada con el modo de Topología híbrida de Exchange clásico entre el entorno local y el de Office 365. La declaración oficial del soporte para la implementación híbrida de Exchange indica que debe tener la CU actual o la CU actual -1.
    > [!NOTE]
    > La autenticación moderna híbrida no es compatible con el [Agente híbrido](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).

  - Asegúrese de que, tanto un usuario de prueba local como un usuario de prueba híbrida alojado en Office 365, puedan iniciar sesión en el cliente de escritorio de Skype Empresarial (si desea usar la autenticación moderna con Skype) y Microsoft Outlook (si desea usar la autenticación moderna con Exchange).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>¿Qué más necesito saber antes de comenzar?
<a name="BKMK_Whatelse"> </a>

- Todos los escenarios para servidores locales implican la configuración de la autenticación moderna local (de hecho, para Skype Empresarial, hay una lista de las topologías compatibles), de modo que el servidor responsable de la autenticación y la autorización se encuentra en la nube de Microsoft (servicio de token de seguridad de Azure AD, denominado "evoSTS") y la actualización de Azure AD sobre las direcciones URL o espacios de nombres que se usan en la instalación local de Skype Empresarial o Exchange. Por lo tanto, los servidores locales ocupan una dependencia en la nube de Microsoft. Llevar a cabo esta acción podría considerarse una configuración de la "autenticación híbrida".
- Este artículo contiene vínculos a otros artículos que le ayudarán a elegir las topologías de autenticación modernas compatibles (necesarias solo para Skype Empresarial) y artículos de instrucciones que muestran los pasos de configuración o los pasos para deshabilitar la autenticación moderna, en Exchange local y en Skype Empresarial local. Marque esta página como favorita en el explorador si va a necesitar una base de inicio para usar la autenticación moderna en el entorno de servidor.

## <a name="related-topics"></a>Temas relacionados
<a name="BKMK_URLListforMA"> </a>

- [Cómo configurar Exchange Server local para usar la autenticación moderna](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Topologías de Skype Empresarial compatibles con la autenticación moderna](https://technet.microsoft.com/library/mt803262.aspx)
- [Cómo configurar Skype Empresarial local para usar la autenticación moderna](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
