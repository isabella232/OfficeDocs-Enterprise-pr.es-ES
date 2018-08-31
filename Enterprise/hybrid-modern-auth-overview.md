---
title: Introducción a la autenticación moderno híbrida y requisitos previos para usar con Skype local para los servidores empresariales y de Exchange
ms.author: tracyp
ms.reviewer: smithre4
author: MSFTTracyP
manager: laurawi
ms.date: 8/27/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.assetid: ef753b32-7251-4c9e-b442-1a5aec14e58d
description: Autenticación moderna es un método de administración de identidades que ofrece más seguro autorización y autenticación de usuario. Está disponible para las implementaciones híbridas de Skype para Business server local y Exchange server local, así como dominio dividido Skype para híbridos de negocio. Este artículo contiene vínculos a relacionados con documentos sobre los requisitos previos, el programa de instalación o deshabilitar la autenticación moderno y a la parte de la información de cliente relacionados (ej Outlook y Skype clientes).
ms.openlocfilehash: 3d510c6d3e9f8ff885279dc008eeefb5d1014639
ms.sourcegitcommit: 2ffe998e58ce1466366d697d99f0dd3e85b0605c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/28/2018
ms.locfileid: "23240595"
---
# <a name="hybrid-modern-authentication-overview-and-prerequisites-for-using-it-with-on-premises-skype-for-business-and-exchange-servers"></a>Introducción a la autenticación moderno híbrida y requisitos previos para usar con Skype local para los servidores empresariales y de Exchange

Autenticación moderna es un método de administración de identidades que ofrece más seguro autorización y autenticación de usuario. Está disponible para las implementaciones híbridas de Office 365 de Skype para Business server local y Exchange server local, así como, dominio dividido Skype para híbridos de negocio. Este artículo contiene vínculos a relacionados con documentos sobre los requisitos previos, el programa de instalación o deshabilitar la autenticación moderno y a la parte de la información de cliente relacionados (ej Outlook y Skype clientes). 
  
- [¿Qué es la autenticación moderno?](hybrid-modern-auth-overview.md#BKMK_WhatisModAuth)
    
- [¿Qué cambia cuando usa la autenticación moderno?](hybrid-modern-auth-overview.md#BKMK_WhatChanges)
    
- [Comprobar el estado de autenticación moderno del entorno local](hybrid-modern-auth-overview.md#BKMK_CheckStatus)
    
- [¿Cumplen los requisitos previos de autenticación moderno?](hybrid-modern-auth-overview.md#BKMK_MeetPrereq)
    
- [¿Qué más necesito saber antes de comenzar?](hybrid-modern-auth-overview.md#BKMK_Whatelse)
    
- [Lista de direcciones URL de autenticación moderno](hybrid-modern-auth-overview.md#BKMK_URLListforMA)
    
## <a name="what-is-modern-authentication"></a>¿Qué es la autenticación moderno?
<a name="BKMK_WhatisModAuth"> </a>

Al hablar de comunicación entre un cliente (por ejemplo, el equipo portátil o el teléfono) y un servidor, Microsoft utiliza la frase 'Moderna autenticación'.
  
Autenticación moderna es un término genérico para una combinación de métodos de autorización y autenticación, así como algunas medidas de seguridad que se basan en directivas de acceso que puede que ya esté familiarizado con. Incluye:
  
- **Métodos de autenticación**: autenticación multifactor; Autenticación basada en certificados de cliente; y la biblioteca de autenticación de Active Directory ( [ADAL](https://technet.microsoft.com/en-us/library/mt710548.aspx)).
    
- **Métodos de autorización**: implementación de Microsoft de Open Authorization (OAuth). 
    
- **Las directivas de acceso condicional**: administración de aplicación de Mobile (MAM) y acceso condicional con Azure Active Directory. 
    
Administración de identidades de usuario con autenticación moderno ofrece a los administradores muchas herramientas diferentes para usar cuando se trata de proteger los recursos y ofrece métodos más seguros de administración de identidades para ambos local (Exchange y Skype para la empresa), híbrida de Exchange y Skype para escenarios de división/híbrida-dominio empresarial.
  
Tenga en cuenta que dado Skype para la empresa funciona estrechamente con Exchange, el comportamiento de inicio de sesión Skype para los usuarios verán el cliente de negocio se verán afectado por el estado de autenticación moderno de Exchange. Esto también se aplicará si tiene un Skype para entornos híbridos de dominio dividido de negocio. Además, el tipo de Skype para entornos híbridos de negocio que admite el uso de autenticación moderno se llama a menudo un '-dominio dividido' (en un dominio dividido, tiene Skype para profesionales en línea y Skype para profesionales en prem, y los usuarios están hospedados en ambas ubicaciones).
  
 **Importante** ¿Sabía que, a partir de agosto de 2017, todos los inquilinos de Office 365 nuevo que incluyan Skype para la empresa en línea y en línea de Exchange tendrán habilitada de forma predeterminada la autenticación moderno? Los inquilinos ya existentes no tengan un cambio en su estado de MA predeterminado, pero todos los inquilinos nuevo soportan automáticamente el conjunto ampliado de características de identidad que vea enumerados anteriormente. Para comprobar el estado de MA Skype para la empresa en línea, puede usar Skype para profesionales online PowerShell con credenciales de administrador Global. Ejecute 'Get-CsOAuthConfiguration' para comprobar el resultado de - ClientADALAuthOverride. Si - ClientADALAuthOverride tiene su autenticación moderno está activada. 
  
## <a name="what-changes-when-i-use-modern-authentication"></a>¿Qué cambia cuando usa la autenticación moderno?
<a name="BKMK_WhatChanges"> </a>

Cuando se usa la autenticación moderno con Skype local para empresariales o Exchange server, todavía esté *autenticar* a los usuarios locales, pero la historia de *autorizar* su acceso a los cambios de recursos (como archivos o mensajes de correo electrónico). Esto es por este motivo, aunque autenticación moderno es acerca de la comunicación de cliente y servidor, los pasos que se tomaron en configuración de resultado MA en evoSTS (un símbolo (token) servicio de seguridad usado por Azure AD) que se establece como servidor de autenticación de Skype para profesionales y Exchange server local. 
  
El cambio a evoSTS permite que los servidores aprovechar las ventajas de OAuth (emisión de token) para autorizar a los clientes en sus instalaciones y también permite a los métodos de seguridad uso local comunes en la nube (similar a la autenticación multifactor). Además, la evoSTS emite tokens que permiten a los usuarios solicitar acceso a los recursos sin proporcionar su contraseña como parte de la solicitud. Independientemente de donde se hospeda a los usuarios (de online o local), e independientemente de qué ubicación hospeda el recurso necesario, EvoSTS se convertirá en el núcleo de autorizar a los usuarios y los clientes una vez que se configura la autenticación moderno.
  
Este es un ejemplo de lo que quiero decir. Si Skype para cliente empresarial necesita tener acceso a Exchange server para obtener información de calendario en nombre de un usuario, utiliza la biblioteca de autenticación de Active Directory (ADAL) para ello. ADAL una biblioteca de código diseñada para recursos protegidos en el directorio disponible para las aplicaciones de cliente con los tokens de seguridad de OAuth. ADAL funciona con OAuth para comprobar las notificaciones y los tokens de (en lugar de las contraseñas), para conceder el acceso de un usuario a un recurso de exchange. En el pasado, la entidad de certificación en una transacción como ésta: el servidor que sabe cómo validar las notificaciones de usuario y emitir los tokens necesarios--es posible que han sido un servicio de Token de seguridad local, o incluso servicios de federación de Active Directory. Sin embargo, la autenticación moderno centraliza dicha autoridad con Azure Active Directory (AD Azure) en la nube.
  
Esto también significa que, aunque el servidor Exchange y Skype para los entornos de negocios pueden ser totalmente local, el servidor de autorización estará en línea, y su entorno local debe tener la capacidad de crear y mantener una conexión a su oficina suscripción 365 en la nube (y la instancia de Azure Active Directory que la suscripción se usa como su directorio).
  
¿Qué no cambiar? Si se encuentra en un dominio dividido híbrido o uso de Skype para profesionales y Exchange server local, todos los usuarios deben autenticarse primero *local* . En una implementación híbrida de autenticación moderno, Lyncdiscovery y Autodiscovery señalen al servidor local. 
  
 **Importante** Si necesita saber el Skype específico para topologías empresariales compatibles con MA, está [documentado derecha aquí](https://technet.microsoft.com/en-us/library/mt803262.aspx).
  
## <a name="check-the-modern-authentication-status-of-your-on-premises-environment"></a>Comprobar el estado de autenticación moderno del entorno local
<a name="BKMK_CheckStatus"> </a>

Debido a que autenticación moderno cambia el servidor de autorización usado cuando Servicios de sacar provecho de OAuth/S2S, necesita saber si moderno autenticación está habilitada o deshabilitada para su Skype para el entorno empresarial y de Exchange. Puede comprobar el estado de su Exchange o Skype para servidores empresariales, de forma local, ejecutando el comando Get-CSOAuthConfiguration en PowerShell. Si el comando devuelve una propiedad de 'OAuthServers' vacía, se deshabilita la autenticación moderno.
  
## <a name="do-you-meet-modern-authentication-prerequisites"></a>¿Cumplen los requisitos previos de autenticación moderno?

Comprobar y comprobar estos elementos de la lista antes de continuar:
  
- **Skype para específicos de su negocio**
    
  - Todos los servidores deben tener SFB Server 2015 CU5 o posterior
    
  - **Excepción** : dispositivo de sucursal de supervivencia (SBA) puede estar en la versión actual (basada en Lync 2013) 
    
  - Su dominio SIP se agrega como un dominio federado en Office 365
    
  - Todos los SFB servidores front-end debe tener conexiones salientes a internet, las direcciones URL la autenticación de Office 365 (TCP 443) y raíz conocido certificado CRL (TCP 80) que aparecen en las filas 1 y 2 de la sección 'autenticación de Office 365 e identidad' de IP y URL de [Office 365 intervalos de direcciones](https://www.bing.com/search?q=%22Office+365+URLs+and+IP+address+ranges%22&amp;src=IE-SearchBox&amp;FORM=IESR3N&amp;redir=5&amp;itrid=96B6C7422F9F4019B37C1B7FDAF8831E).
    
 **Nota** Si su Skype para los servidores front-end de negocio usa un servidor proxy para el acceso a Internet, se debe especificar el número IP y puerto de servidor proxy utilizado en la sección Configuración del archivo web.config para cada front-end. 
  
- c:\Program files\Skype para Business Server 2015\Web Components\Web ticket\int\web.config
    
- c:\Program files\Skype para Business Server 2015\Web Components\Web ticket\ext\web.config
    
- \</System.identityModel.Services\>
    
     \<System.NET\> 
    
     \<defaultProxy\> 
    
     \<proxy 
    
     proxyAddress = "http://192.168.100.60:8080" 
    
     BypassOnLocal = "true" 
    
     /\> 
    
     \</defaultProxy\> 
    
     \</ System.NET\> 
    
    \</Configuration\>
    
 **Importante** No olvide suscribirse a la fuente RSS para que [las direcciones URL de Office 365 y los intervalos de direcciones IP](https://support.office.com/en-us/article/Office-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) para mantenerse al día con los listados más recientes de las direcciones URL necesarias. 
  
- **Servidor de Exchange específico**
    
  - Está usando Exchange server 2013 CU19 y de seguridad, o Exchange server 2016 CU8 y arriba.
    
  - No hay ningún servidor de Exchange 2010 en el entorno.
    
  - Descarga de SSL no está configurada. Se admite la terminación SSL y volver a cifrar.
    
  - En el caso de que su entorno utiliza una infraestructura de servidor proxy para permitir que los servidores para conectarse a Internet, asegúrese de que todos los servidores de Exchange tienen el servidor proxy definido en la propiedad [InternetWebProxy](https://technet.microsoft.com/en-us/library/bb123716%28v=exchg.160%29.aspx) .
    
- **Requisitos de protocolo y el cliente de Exchange**
  
  - Los siguientes clientes admiten la autenticación moderna:

  |**Clientes**|**Protocolo principal**|**Notas**|
  |:-----|:-----|:-----|
  |Outlook 2013 y Outlook 2016  <br/> |MAPI sobre HTTP  <br/> |Debe estar habilitado MAPI sobre HTTP en Exchange con el fin de utilizar autenticación moderna con estos clientes (normalmente habilitado o True para las nuevas instalaciones de Exchange 2013 Service Pack 1 y posterior); Para obtener más información, vea [moderno cómo funciona la autenticación para aplicaciones de cliente de Office 2013 y Office 2016](https://docs.microsoft.com/en-us/office365/enterprise/modern-auth-for-office-2013-and-2016).  <br/> Asegúrese de que está ejecutando la compilación mínima necesaria de Outlook; consulte [las actualizaciones más recientes para las versiones de Outlook que usan Windows Installer (MSI)](https://docs.microsoft.com/en-us/officeupdates/outlook-updates-msi).  <br/> |
  |Outlook 2016 para Mac  <br/> |Servicios web de Exchange  <br/> |  <br/> |
  |Outlook for iOS and Android  <br/> |  <br/> |Para obtener más información, vea [Using híbrida autenticación moderno con Outlook para iOS y Android](https://docs.microsoft.com/en-us/Exchange/clients/outlook-for-ios-and-android/use-hybrid-modern-auth) .  <br/> |
  |Clientes de Exchange ActiveSync (por ejemplo, iOS11 correo)  <br/> |Exchange ActiveSync  <br/> |Para los clientes de Exchange ActiveSync que admiten la autenticación moderna, debe volver a crear el perfil con el fin de cambiar de la autenticación básica a la autenticación moderna.  <br/> |

- **Requisitos previos**
    
  - Si usa ADFS, debe tener Windows 2012 R2 ADFS 3.0 y superior para la federación
    
  - Las configuraciones de identidad son cualquiera de los tipos admitidos por conectar AAD (como la sincronización de hash de contraseña, autenticación de paso a través, local STS compatibles con Office 365, etc.)
    
  - Debe AAD conectar configurada y funciona para la sincronización y replicación de usuarios.
    
  - Haya comprobado que híbrida funciona entre su local y Office 365:
    
  - Declaración de soporte oficial para entornos híbridos de Exchange indica que debe tener CU actual o CU actual - 1.
    
  - Asegúrese de que ambos un usuario de prueba local, así como un usuario de prueba híbrida hospedados en Office 365, puede iniciar la sesión en el Skype para el cliente de escritorio empresarial (si desea usar la autenticación moderno con Skype) y Microsoft Outlook (si lo desea por lo que usa la autenticación moderno con Exchange).
    
## <a name="what-else-do-i-need-to-know-before-i-begin"></a>¿Qué más necesito saber antes de comenzar?
<a name="BKMK_Whatelse"> </a>

1. Todos los escenarios en los servidores locales implican configurando moderno autenticación local (de hecho, para Skype para la empresa tiene una lista de topologías admitidas) para que sea el servidor responsable de la autenticación y autorización en el (Microsoft Cloud Seguridad servicio de token de AAD, llamado 'evoSTS') y la actualización de Azure Active Directory (AAD) acerca de las direcciones URL o espacios de nombres utilizados por la instalación local de cualquiera Skype para empresariales o de Exchange. Por lo tanto, los servidores locales tomar una dependencia de Microsoft Cloud. Esta acción podría considerarse configuración 'híbrida auth'.
    
2. Este artículo contiene vínculos a otras personas que le ayudarán a elegir admite topologías de autenticación moderno (es necesarias solamente para Skype para la empresa) y procedimientos de artículos ese esquema de los pasos de configuración o los pasos para deshabilitar la autenticación moderno, para Exchange local y Skype para la empresa local. Favorito esta página en el explorador si va a necesitar una base de inicio para usar la autenticación moderno en su entorno de servidor.
    
## <a name="list-of-modern-authentication-urls"></a>Lista de direcciones URL de autenticación moderno
<a name="BKMK_URLListforMA"> </a>

- [Cómo configurar el servidor de Exchange local para usar la autenticación moderno](configure-exchange-server-for-hybrid-modern-authentication.md)
    
- [Skype para topologías empresariales compatibles con autenticación moderno](https://technet.microsoft.com/en-us/library/mt803262.aspx)
    
- [Cómo configurar Skype para la empresa local para usar la autenticación moderno](configure-skype-for-business-for-hybrid-modern-authentication.md)
    
- [Quitar o deshabilitar la autenticación moderna híbrida de Skype Empresarial y Exchange](remove-or-disable-hybrid-modern-authentication-from-skype-for-business-and-excha.md)
    

