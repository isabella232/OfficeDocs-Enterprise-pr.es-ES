---
title: Introducción a la autenticación moderna híbrida y requisitos previos para su uso con Skype empresarial local y los servidores de Exchange
ms.author: kvice
ms.reviewer: smithre4
author: kelleyvice-msft
manager: laurawi
ms.date: 12/17/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: La autenticación moderna es un método de administración de identidades que ofrece autenticación y autorización de usuario más seguras. Está disponible para implementaciones híbridas de Skype empresarial Server local y Exchange Server local, así como para entornos híbridos de dominio dividido de Skype empresarial. Este artículo contiene vínculos a documentos relacionados sobre requisitos previos, la configuración/deshabilitación de la autenticación moderna y para algunos de los clientes relacionados (por ejemplo, Outlook y clientes de Skype) información.
ms.openlocfilehash: 87a2cc49594b0b71d1288e27ab1323f1850fd7eb
ms.sourcegitcommit: 9dfaeff7a1625a7325bb94f3eb322fc161ce066b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2019
ms.locfileid: "40261403"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Introducción a la autenticación moderna híbrida y requisitos previos para su uso con servidores locales de Skype empresarial y Exchange

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

La _autenticación moderna_ es un método de administración de identidades que ofrece autenticación y autorización de usuario más seguras. Está disponible para implementaciones híbridas de Office 365 de Skype empresarial Server local y Exchange Server local, así como para entornos híbridos de Skype empresarial de dominio dividido. Este artículo contiene vínculos a documentos relacionados sobre requisitos previos, la configuración/deshabilitación de la autenticación moderna y para algunos de los clientes relacionados (por ejemplo, Outlook y clientes de Skype) información.
  
- [¿Qué es la autenticación moderna?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
- [¿Qué cambios cuando utilizo la autenticación moderna?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
- [Comprobar el estado de autenticación moderna del entorno local](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
- [¿Cumple los requisitos previos de autenticación moderna?](#do-you-meet-modern-authentication-prerequisites)
- [¿Qué más necesito saber antes de empezar?](hybrid-modern-auth-overview.md#BKMK_Whatelse)

## <a name="what-is-modern-authentication"></a>¿Qué es la autenticación moderna?
<a name="BKMK_WhatisModAuth"> </a>

La autenticación moderna es un término genérico para una combinación de métodos de autenticación y autorización entre un cliente (por ejemplo, el portátil o el teléfono) y un servidor, así como algunas medidas de seguridad que se basan en las directivas de acceso que puede que ya esté familiarizado. Incluye:
  
- **Métodos de autenticación**: multi-factor Authentication (MFA); autenticación de tarjetas inteligentes; autenticación basada en certificados de cliente
- **Métodos de autorización**: implementación de Microsoft de Open Authorization (OAuth)
- **Directivas de acceso condicional**: administración de aplicaciones móviles (MAM) y acceso condicional de Azure Active Directory

La administración de identidades de usuario con autenticación moderna proporciona a los administradores muchas herramientas distintas para proteger los recursos y ofrece métodos más seguros de administración de identidades para escenarios locales (Exchange y Skype empresarial), Exchange híbrido y Skype for Business híbridos o de dominios divididos.
  
Tenga en cuenta que, como Skype empresarial funciona estrechamente con Exchange, el comportamiento de inicio de sesión que verán los usuarios del cliente de Skype empresarial se verá afectado por el estado de autenticación moderna de Exchange. Esto también se aplicará si tiene una arquitectura híbrida de _dominio dividido_ de Skype empresarial, en la que tiene Skype empresarial online y Skype empresarial local, con los usuarios hospedados en ambas ubicaciones.

Para obtener más información sobre la autenticación moderna en Office 365, consulte [soporte técnico de aplicaciones de cliente de office 365: autenticación moderna](office-365-client-support-modern-authentication.md).
  
> [!IMPORTANT]
> A partir de agosto de 2017, todos los inquilinos de Office 365 nuevos que incluyen Skype empresarial online y Exchange Online tendrán habilitada la autenticación moderna de forma predeterminada. Los inquilinos preexistentes no tendrán un cambio en el estado de MA predeterminado, pero todos los nuevos inquilinos admitirán automáticamente el conjunto ampliado de características de identidad que se muestran más arriba. Para comprobar el estado del MA, consulte la sección [comprobar el estado de autenticación moderna de su entorno local](hybrid-modern-auth-overview.md#BKMK_CheckStatus) .
  
## <a name="what-changes-when-i-use-modern-authentication"></a>¿Qué cambios cuando utilizo la autenticación moderna?
<a name="BKMK_WhatChanges"> </a>

Al usar la autenticación moderna con Skype empresarial local o Exchange Server, sigue *autenticando* a los usuarios de forma local, pero el caso de *autorizar* el acceso a los recursos (como archivos o mensajes de correo electrónico) cambia. Por este motivo, aunque la autenticación moderna se refiere a la comunicación de cliente y servidor, los pasos que se llevan a cabo durante la configuración del MA dan como resultado evoSTS (un servicio de token de seguridad usado por Azure AD) que se establece como servidor de autenticación para Skype empresarial y Exchange Server local.
  
El cambio a evoSTS permite a los servidores locales aprovechar OAuth (emisión de token) para autorizar a los clientes y también permite que los métodos de seguridad de uso local sean comunes en la nube (como la autenticación multifactor). Además, evoSTS emite tokens que permiten a los usuarios solicitar acceso a los recursos sin proporcionar su contraseña como parte de la solicitud. Independientemente de la ubicación de los usuarios (de conexión o local), y independientemente de la ubicación que hospede el recurso necesario, EvoSTS se convertirá en la base de autorizaciones de usuarios y clientes una vez configurada la autenticación moderna.
  
Por ejemplo, si un cliente de Skype empresarial necesita acceder a Exchange Server para obtener información del calendario en nombre de un usuario, usa la biblioteca de autenticación de Active Directory (ADAL) para hacerlo. ADAL es una biblioteca de código diseñada para que los recursos protegidos en el directorio estén disponibles para las aplicaciones cliente mediante tokens de seguridad de OAuth. ADAL funciona con OAuth para comprobar notificaciones e intercambiar tokens (en lugar de contraseñas), para conceder a un usuario acceso a un recurso. En el pasado, la autoridad de una transacción como esta, el servidor que sabe cómo validar las notificaciones de usuario y emitir los tokens necesarios, puede haber sido un servicio de token de seguridad local o incluso servicios de Federación de Active Directory. Sin embargo, la autenticación moderna centraliza esa autoridad mediante Azure Active Directory (AAD).
  
Esto también significa que aunque sus entornos de Exchange Server y Skype empresarial puedan estar completamente locales, el servidor de autorización estará en línea y el entorno local debe tener la capacidad de crear y mantener una conexión con su oficina. 365 suscripción en la nube (y la instancia de Azure Active Directory que su suscripción usa como su directorio).
  
¿Qué no cambia? Tanto si está en un híbrido de dominio dividido como si usa Skype empresarial y Exchange Server local, todos los usuarios deben autenticarse primero *en el entorno local*. En una implementación híbrida de la autenticación moderna, _Lyncdiscovery_ y _AutoDiscovery_ apuntan a su servidor local.
  
> [!IMPORTANT]
> Si necesita conocer las topologías de Skype empresarial específicas compatibles con MA, se [documenta aquí](https://technet.microsoft.com/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Comprobar el estado de autenticación moderna del entorno local
<a name="BKMK_CheckStatus"> </a>

Debido a que la autenticación moderna cambia el servidor de autorización usado cuando los servicios aprovechan OAuth o S2S, necesita saber si la autenticación moderna está habilitada o deshabilitada para sus entornos locales de Skype empresarial y Exchange. Puede comprobar el estado de los servidores de Exchange mediante la ejecución del siguiente comando de PowerShell:

```powershell
Get-OrganizationConfig | ft OAuth*
```

Si el valor de la propiedad _OAuth2ClientProfileEnabled_ es **false**, la autenticación moderna está deshabilitada.

Para obtener más información acerca del cmdlet Get-OrganizationConfig, consulte [Get-organizationconfig](https://docs.microsoft.com/powershell/module/exchange/organization/get-organizationconfig).

Para comprobar los servidores de Skype empresarial, ejecute el siguiente comando de PowerShell:

```powershell
Get-CSOAuthConfiguration
```

Si el comando devuelve una propiedad _OAuthServers_ vacía o si no se **permite**el valor de la propiedad _ClientADALAuthOverride_ , la autenticación moderna está deshabilitada.

Para obtener más información sobre el cmdlet Get-CsOAuthConfiguration, consulte [Get-CsOAuthConfiguration](https://docs.microsoft.com/powershell/module/skype/get-csoauthconfiguration).
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>¿Cumple los requisitos previos de autenticación moderna?

Compruebe y compruebe estos elementos de la lista antes de continuar:
  
- **Específico de Skype empresarial**
  - Todos los servidores deben tener la actualización acumulativa de mayo de 2017 (CU5) para Skype empresarial Server 2015 o posterior
    - **Excepción** : el dispositivo de sucursal de supervivencia (SBA) puede estar en la versión actual (en función de la versión de Lync 2013)
  - El dominio SIP se agrega como un dominio federado en Office 365
  - Todos los front-ends de SFB deben tener conexiones salientes a Internet, a direcciones URL de autenticación de Office 365 (TCP 443) y CRL de certificado raíz conocidas (TCP 80) enumeradas en las filas 56 y 125 de la sección ' Microsoft 365 Common y Office ' de los [intervalos de direcciones IP y URL de office 365](urls-and-ip-address-ranges.md).
  
- **Skype empresarial local en un entorno híbrido de Office 365**
  - Una implementación de Skype empresarial Server 2019 con todos los servidores que ejecutan Skype empresarial Server 2019.
  - Una implementación de Skype empresarial Server 2015 con todos los servidores que ejecutan Skype empresarial Server 2015.
  - Una implementación con un máximo de dos versiones de servidor distintas, como se muestra a continuación:
    - Skype Empresarial Server 2015
    - Skype empresarial Server 2019
  - Todos los servidores de Skype empresarial deben tener instaladas las últimas actualizaciones acumulativas, consulte [actualizaciones de Skype empresarial Server](https://docs.microsoft.com/skypeforbusiness/sfb-server-updates) para buscar y administrar todas las actualizaciones disponibles.
  - No hay Lync Server 2010 o 2013 en el entorno híbrido.

>[!NOTE]
>Si los servidores front-end de Skype empresarial usan un servidor proxy para el acceso a Internet, se debe especificar el número de puerto y la IP del servidor proxy que se usan en la sección de configuración del archivo Web. config para cada front-end.
  
- C:\Archivos de Files\Skype para Business Server 2015 \ Web Components\Web ticket\int\web.config
- C:\Archivos de Files\Skype para Business Server 2015 \ Web Components\Web ticket\ext\web.config

```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="https://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```

> [!IMPORTANT]
> No olvide suscribirse a la fuente RSS para los [intervalos de direcciones IP y URL de Office 365](urls-and-ip-address-ranges.md) para estar al día de los últimos listados de direcciones URL necesarias.
  
- **Específico de Exchange Server**
  - Está usando tanto Exchange Server 2013 CU19 como up, Exchange Server 2016 CU8 y up, o Exchange Server 2019 CU1 y up.
  - No hay ningún servidor de Exchange 2010 en el entorno.
  - La descarga de SSL no está configurada. Se admite la terminación SSL y el nuevo cifrado.
  - En el caso de que el entorno use una infraestructura de servidor proxy para permitir que los servidores se conecten a Internet, asegúrese de que todos los servidores de Exchange tengan el servidor proxy definido en la propiedad [InternetWebProxy](https://technet.microsoft.com/library/bb123716%28v=exchg.160%29.aspx) .
  
- **Exchange Server local en un entorno híbrido de Office 365**

  - Si usa Exchange Server 2013, al menos un servidor debe tener instalados los roles de servidor buzón de correo y acceso de cliente. Aunque es posible instalar los roles de acceso de cliente y buzón de correo en servidores independientes, se recomienda instalar ambos roles en el mismo servidor para proporcionar confiabilidad adicional y mejorar el rendimiento.
  - Si usa Exchange Server 2016 o una versión posterior, al menos un servidor debe tener instalado el rol de servidor buzón de correo.
  - No existe el servidor de Exchange 2007 o 2010 en el entorno híbrido.
  - Todos los servidores de Exchange deben tener instaladas las últimas actualizaciones de Cummulative, consulte [Actualizar Exchange a las actualizaciones acumulativas más recientes](https://docs.microsoft.com/exchange/plan-and-deploy/install-cumulative-updates?view=exchserver-2019) para buscar y administrar todas las actualizaciones disponibles.

- **Requisitos del protocolo y del cliente de Exchange**
  
  - Los siguientes clientes admiten la autenticación moderna:

  |**Clientes**|**Protocolo principal**|**Notas**|
  |:-----|:-----|:-----|
  |Outlook 2013 y Outlook 2016  <br/> |MAPI sobre HTTP  <br/> |MAPI sobre HTTP debe estar habilitado en Exchange para poder aprovechar la autenticación moderna con estos clientes (normalmente habilitado o verdadero para instalaciones nuevas de Exchange 2013 Service Pack 1 y versiones posteriores); para obtener más información, vea [Cómo funciona la autenticación moderna para las aplicaciones cliente de office 2013 y office 2016](https://docs.microsoft.com/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Asegúrese de que está ejecutando la compilación mínima necesaria de Outlook; consulte [las actualizaciones más recientes de las versiones de Outlook que usan Windows Installer (MSI)](https://docs.microsoft.com/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 para Mac  <br/> |Servicios web de Exchange  <br/> |  <br/> |
  |Outlook para iOS y Android  <br/> |  <br/> |Vea [usar la autenticación moderna híbrida con Outlook para iOS y Android](https://docs.microsoft.com/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) para obtener más información.  <br/> |
  |Clientes de Exchange ActiveSync (por ejemplo, iOS11 de correo)  <br/> |Exchange ActiveSync  <br/> |Para los clientes de Exchange ActiveSync que admiten la autenticación moderna, debe volver a crear el perfil para cambiar de la autenticación básica a la autenticación moderna.  <br/> |

- **Requisitos previos generales**
  - Si usa ADFS, debe tener Windows 2012 R2 ADFS 3,0 y posterior para la Federación.
  - Las configuraciones de identidad son cualquiera de los tipos compatibles con AAD Connect (como la sincronización de hash de contraseña, la autenticación de paso a través, el STS local admitido por Office 365, et cetera).
  - Tiene la conexión de AAD configurada y en funcionamiento para la replicación y sincronización de usuarios.
  - Ha comprobado que la configuración híbrida se ha configurado con el modo de topología híbrida híbrida de Exchange entre el entorno local y el de Office 365. Declaración oficial de soporte para Exchange Hybrid indica que debe tener CU actual o CU actual-1.
    > [!NOTE]
    > La autenticación moderna híbrida no es compatible con el [agente híbrido](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).

  - Asegúrese de que tanto un usuario de prueba local como un usuario de prueba híbrida hospedado en Office 365, puedan iniciar sesión en el cliente de escritorio de Skype empresarial (si desea usar la autenticación moderna con Skype) y Microsoft Outlook (si desea usar la autenticación moderna con Exchange).

## <a name="what-else-do-i-need-to-know-before-i-begin"></a>¿Qué más necesito saber antes de empezar?
<a name="BKMK_Whatelse"> </a>

- Todos los escenarios de los servidores locales implican la configuración de la autenticación moderna local (de hecho, en Skype empresarial hay una lista de topologías admitidas) para que el servidor responsable de la autenticación y la autorización esté en la nube de Microsoft ( Servicio de token de seguridad de AAD, denominado "evoSTS", y actualización de Azure Active Directory (AAD) acerca de las direcciones URL o los espacios de nombres usados por la instalación local de Skype empresarial o Exchange. Por lo tanto, los servidores locales toman una dependencia de la nube de Microsoft. Realizar esta acción puede considerarse la configuración de la "autenticación híbrida".
- En este artículo se establecen vínculos a otros usuarios que le ayudarán a elegir topologías de autenticación moderna admitidas (solo necesarias para Skype empresarial) y artículos de procedimientos que describen los pasos de configuración o los pasos para deshabilitar la autenticación moderna para Exchange local. y Skype empresarial local. Si va a necesitar una base de datos de inicio para usar la autenticación moderna en su entorno de servidor, es preferible esta página en el explorador.

## <a name="related-topics"></a>Temas relacionados
<a name="BKMK_URLListforMA"> </a>

- [Cómo configurar Exchange Server local para usar la autenticación moderna](configure-exchange-server-for-hybrid-modern-authentication.md)
- [Topologías de Skype empresarial compatibles con la autenticación moderna](https://technet.microsoft.com/library/mt803262.aspx)
- [Cómo configurar Skype empresarial local para usar la autenticación moderna](configure-skype-for-business-for-hybrid-modern-authentication.md)
- [Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
