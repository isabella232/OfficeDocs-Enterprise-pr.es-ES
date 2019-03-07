---
title: Introducción a la autenticación moderna híbrida y requisitos previos para su uso con servidores locales de Skype empresarial y Exchange
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: ''
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
ms.collection:
- M365-security-compliance
description: La autenticación moderna es un método de administración de identidades que ofrece autenticación y autorización de usuario más seguras. Está disponible para implementaciones híbridas de Skype empresarial Server local y Exchange Server local, así como para entornos híbridos de dominio dividido de Skype empresarial. Este artículo contiene vínculos a documentos relacionados sobre requisitos previos, la configuración/deshabilitación de la autenticación moderna y para algunos de los clientes relacionados (por ejemplo, Outlook y clientes de Skype) información.
ms.openlocfilehash: 26efa77e3c98c0395188e6ca7a2f65cd3b8b939e
ms.sourcegitcommit: 19f0deee26b6cf2eef316c742054572bb9d98b84
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2019
ms.locfileid: "30458350"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Introducción a la autenticación moderna híbrida y requisitos previos para su uso con servidores locales de Skype empresarial y Exchange

La autenticación moderna es un método de administración de identidades que ofrece autenticación y autorización de usuario más seguras. Está disponible para implementaciones híbridas de Office 365 de Skype empresarial Server local y Exchange Server local, así como para entornos híbridos de Skype empresarial de dominio dividido. Este artículo contiene vínculos a documentos relacionados sobre requisitos previos, la configuración/deshabilitación de la autenticación moderna y para algunos de los clientes relacionados (por ejemplo, Outlook y clientes de Skype) información. 
  
- [¿Qué es la autenticación moderna?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [¿Qué cambios cuando utilizo la autenticación moderna?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [Comprobar el estado de autenticación moderna del entorno local](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [¿Cumple los requisitos previos de autenticación moderna?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [¿Qué más necesito saber antes de empezar?](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [Lista de direcciones URL de autenticación moderna](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>¿Qué es la autenticación moderna?
<a name="BKMK_WhatisModAuth"> </a>

Al hablar sobre la comunicación entre un cliente (por ejemplo, el portátil o el teléfono) y un servidor, Microsoft usa la frase "autenticación moderna".
  
La autenticación moderna es un término paraguas para una combinación de métodos de autenticación y autorización, así como algunas medidas de seguridad que dependen de las directivas de acceso con las que tal vez ya esté familiarizado. Incluye:
  
- **Métodos de autenticación**: multi-factor Authentication; Autenticación basada en certificados de cliente; y la biblioteca de autenticación de Active Directory ( [Adal](https://technet.microsoft.com/en-us/library/mt710548.aspx)).
    
- **Métodos de autorización**: implementación de Microsoft de Open Authorization (OAuth). 
    
- **Directivas de acceso condicional**: administración de aplicaciones móviles (MAM) y acceso condicional de Azure Active Directory. 
    
La administración de identidades de usuario con autenticación moderna proporciona a los administradores muchas herramientas distintas para proteger los recursos y ofrece métodos más seguros de administración de identidades en entornos locales (Exchange y Skype empresarial), Exchange híbrido y escenarios de Skype empresarial híbrido/dominio dividido.
  
Tenga en cuenta que, como Skype empresarial funciona estrechamente con Exchange, el comportamiento de inicio de sesión que verán los usuarios del cliente de Skype empresarial se verá afectado por el estado de autenticación moderna de Exchange. Esto también se aplicará si tiene un híbrido de dominio dividido de Skype empresarial. Además, el tipo de entorno híbrido de Skype empresarial que admite el uso de la autenticación moderna se denomina a menudo "dominio dividido" (en un dominio dividido, tiene tanto Skype empresarial online como Skype empresarial local, y los usuarios están hospedados en ambas ubicaciones).
  
> [!IMPORTANT]
> ¿Sabía que, a partir de agosto de 2017, todos los inquilinos nuevos de Office 365 que incluyen Skype empresarial online y Exchange Online tendrán habilitada la autenticación moderna de forma predeterminada? Los inquilinos preexistentes no tendrán un cambio en el estado de MA predeterminado, pero todos los nuevos inquilinos admitirán automáticamente el conjunto ampliado de características de identidad que se muestran más arriba. Para comprobar el estado del MA para Skype empresarial online, puede usar PowerShell de Skype empresarial online con credenciales de administrador global. Ejecutar `Get-CsOAuthConfiguration` para comprobar el resultado de-ClientADALAuthOverride. Si-ClientADALAuthOverride es "permitida", la autenticación moderna está activada. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>¿Qué cambios cuando utilizo la autenticación moderna?
<a name="BKMK_WhatChanges"> </a>

Al usar la autenticación moderna con Skype empresarial local o Exchange Server, sigue autenticando a los ** usuarios de forma local, pero el caso de autorizar ** el acceso a los recursos (como archivos o mensajes de correo electrónico) cambia. Por este motivo, aunque la autenticación moderna se refiere a la comunicación de cliente y servidor, los pasos que se llevan a cabo durante la configuración del MA dan como resultado evoSTS (un servicio de token de seguridad usado por Azure AD) que se establece como servidor de autenticación para Skype empresarial y Exchange Server local. 
  
El cambio a evoSTS permite a los servidores locales aprovechar OAuth (emisión de token) para autorizar a los clientes y también permite que los métodos de seguridad de uso local sean comunes en la nube (como la autenticación multifactor). Además, evoSTS emite tokens que permiten a los usuarios solicitar acceso a los recursos sin proporcionar su contraseña como parte de la solicitud. Independientemente de la ubicación de los usuarios (de conexión o local), y independientemente de la ubicación que hospede el recurso necesario, EvoSTS se convertirá en la base de autorizaciones de usuarios y clientes una vez configurada la autenticación moderna.
  
A continuación, le mostramos un ejemplo de lo que quiero decir. Si el cliente de Skype empresarial necesita acceder a Exchange Server para obtener información del calendario en nombre de un usuario, usa la biblioteca de autenticación de Active Directory (ADAL) para hacerlo. ADAL es una biblioteca de código diseñada para que los recursos protegidos en el directorio estén disponibles para las aplicaciones cliente mediante tokens de seguridad de OAuth. ADAL funciona con OAuth para comprobar notificaciones e intercambiar tokens (en lugar de contraseñas), para conceder a un usuario acceso a un recurso. En el pasado, la autoridad de una transacción como esta, el servidor que sabe cómo validar las notificaciones de usuario y emitir los tokens necesarios, puede haber sido un servicio de token de seguridad local o incluso servicios de Federación de Active Directory. Sin embargo, la autenticación moderna centraliza esa autoridad con Azure Active Directory (Azure AD) en la nube.
  
Esto también significa que aunque sus entornos de Exchange Server y Skype empresarial puedan estar completamente locales, el servidor de autorización estará en línea y el entorno local debe tener la capacidad de crear y mantener una conexión con su oficina. 365 suscripción en la nube (y la instancia de Azure Active Directory que su suscripción usa como su directorio).
  
¿Qué no cambia? Tanto si está en un híbrido de dominio dividido como si usa Skype empresarial y Exchange Server local, todos los usuarios deben autenticarse primero *en el entorno local* . En una implementación híbrida de la autenticación moderna, Lyncdiscovery y AutoDiscovery apuntan a su servidor local. 
  
> [!IMPORTANT]
> Si necesita conocer las topologías de Skype empresarial específicas compatibles con MA, se [documenta aquí](https://technet.microsoft.com/en-us/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Comprobar el estado de autenticación moderna del entorno local
<a name="BKMK_CheckStatus"> </a>

Debido a que la autenticación moderna cambia el servidor de autorización usado cuando los servicios aprovechan OAuth o S2S, necesita saber si la autenticación moderna está habilitada o desActivada para su entorno de Skype empresarial y Exchange. Puede comprobar el estado de los servidores de Exchange o Skype empresarial, local, mediante la ejecución del `Get-CSOAuthConfiguration` comando en PowerShell. Si el comando devuelve una propiedad ' OAuthServers ' vacía, la autenticación moderna está deshabilitada.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>¿Cumple los requisitos previos de autenticación moderna?

Compruebe y compruebe estos elementos de la lista antes de continuar:
  
- **Específico de Skype empresarial**
    
  - Todos los servidores deben tener SFB Server 2015 CU5 o posterior
    
  - **Excepción** : el dispositivo de sucursal de supervivencia (SBA) puede estar en la versión actual (en función de la versión de Lync 2013) 
    
  - El dominio SIP se agrega como un dominio federado en Office 365
    
  - Todos los front-ends de SFB deben tener conexiones salientes a Internet, a las direcciones URL de autenticación de Office 365 (TCP 443) y las CRL de raíz de certificado conocidas (TCP 80) que aparecen en las filas 56 y 125 de la sección "Microsoft 365 Common y Office Online" de las [direcciones URL e IP de office 365 intervalos de direcciones](urls-and-ip-address-ranges.md).
    
 **Nota:** Si los servidores front-end de Skype empresarial usan un servidor proxy para el acceso a Internet, se debe especificar el número de puerto y la IP del servidor proxy que se usan en la sección de configuración del archivo Web. config para cada front-end. 
  
- C:\Archivos de Files\Skype para Business Server 2015 \ Web Components\Web ticket\int\web.config
    
- C:\Archivos de Files\Skype para Business Server 2015 \ Web Components\Web ticket\ext\web.config
    
```xml
<system.identityModel.services>
  <system.net>
    <defaultProxy>
      <proxy
        proxyaddress="http://192.168.100.60:8080"
        bypassonlocal="true" />
    </defaultProxy>
  </system.net>
</system.identityModel.services>
```
    
> [!IMPORTANT]
> No olvide suscribirse a la fuente RSS para los [intervalos de direcciones IP y URL de Office 365](urls-and-ip-address-ranges.md) para estar al día de los últimos listados de direcciones URL necesarias. 
  
- **Específico de Exchange Server**
    
  - Está usando Exchange Server 2013 CU19, o bien Exchange Server 2016 CU8 y up.
    
  - No hay ningún servidor de Exchange 2010 en el entorno.
    
  - La descarga de SSL no está configurada. Se admite la terminación SSL y el nuevo cifrado.
    
  - En el caso de que el entorno use una infraestructura de servidor proxy para permitir que los servidores se conecten a Internet, asegúrese de que todos los servidores de Exchange tengan el servidor proxy definido en la propiedad [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) .
    
- **Requisitos del protocolo y del cliente de Exchange**
  
  - Los siguientes clientes admiten la autenticación moderna:

  |**Clientes**|**Protocolo principal**|**Notas**|
  |:-----|:-----|:-----|
  |Outlook 2013 y Outlook 2016  <br/> |MAPI sobre HTTP  <br/> |MAPI sobre HTTP debe estar habilitado en Exchange para poder aprovechar la autenticación moderna con estos clientes (normalmente habilitado o verdadero para instalaciones nuevas de Exchange 2013 Service Pack 1 y versiones posteriores); para obtener más información, vea [Cómo funciona la autenticación moderna para las aplicaciones cliente de office 2013 y office 2016](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Asegúrese de que está ejecutando la compilación mínima necesaria de Outlook; consulte [las actualizaciones más recientes de las versiones de Outlook que usan Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 para Mac  <br/> |Servicios web de Exchange  <br/> |  <br/> |
  |Outlook para iOS y Android  <br/> |  <br/> |Vea [usar la autenticación moderna híbrida con Outlook para iOS y Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) para obtener más información.  <br/> |
  |Clientes de Exchange ActiveSync (por ejemplo, iOS11 de correo)  <br/> |Exchange ActiveSync  <br/> |Para los clientes de Exchange ActiveSync que admiten la autenticación moderna, debe volver a crear el perfil para cambiar de la autenticación básica a la autenticación moderna.  <br/> |

- **Requisitos previos generales**
    
  - Si usa ADFS, debe tener Windows 2012 R2 ADFS 3,0 y posterior para la Federación.
    
  - Las configuraciones de identidad son cualquiera de los tipos compatibles con AAD Connect (como la sincronización de hash de contraseña, la autenticación de paso a través, el STS local admitido por Office 365, et cetera).
    
  - Tiene la conexión de AAD configurada y en funcionamiento para la replicación y sincronización de usuarios.
    
  - Ha comprobado que la configuración híbrida se ha configurado con el modo de topología híbrida híbrida de Exchange entre el entorno local y el de Office 365. Declaración oficial de soporte para Exchange Hybrid indica que debe tener CU actual o CU actual-1.
    
    > [!Note]
    > La autenticación moderna híbrida no es compatible con el [agente híbrido](https://docs.microsoft.com/exchange/hybrid-deployment/hybrid-agent).
    
  - Asegúrese de que tanto un usuario de prueba local como un usuario de prueba híbrida hospedado en Office 365, puedan iniciar sesión en el cliente de escritorio de Skype empresarial (si desea usar la autenticación moderna con Skype) y Microsoft Outlook (si lo desea, use la autenticación moderna con Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>¿Qué más necesito saber antes de empezar?
<a name="BKMK_Whatelse"> </a>

1. Todos los escenarios de los servidores locales implican la configuración de la autenticación moderna local (de hecho, en Skype empresarial hay una lista de topologías admitidas) para que el servidor responsable de la autenticación y la autorización esté en la nube de Microsoft ( Servicio de token de seguridad de AAD, denominado "evoSTS", y actualización de Azure Active Directory (AAD) acerca de las direcciones URL o los espacios de nombres usados por la instalación local de Skype empresarial o Exchange. Por lo tanto, los servidores locales toman una dependencia de la nube de Microsoft. Realizar esta acción puede considerarse la configuración de la "autenticación híbrida".
    
2. En este artículo se establecen vínculos a otros usuarios que le ayudarán a elegir topologías de autenticación moderna admitidas (solo necesarias para Skype empresarial) y artículos de procedimientos que describen los pasos de configuración o los pasos para deshabilitar la autenticación moderna para Exchange local. y Skype empresarial local. Favoritos esta página en el explorador si va a necesitar una base de datos de inicio para usar la autenticación moderna en el entorno del servidor.
    
## <a name="list-of-modern-authentication-urls"></a>Lista de direcciones URL de autenticación moderna
<a name="BKMK_URLListforMA"> </a>

- [Cómo configurar Exchange Server local para usar la autenticación moderna](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Topologías de Skype empresarial compatibles con la autenticación moderna](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Cómo configurar Skype empresarial local para usar la autenticación moderna](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Eliminación o deshabilitación de la autenticación moderna híbrida de Skype empresarial y Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

