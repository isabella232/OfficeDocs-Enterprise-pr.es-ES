---
title: Planificación de la sincronización del directorio para Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Describe la sincronización de directorios con Office 365, la limpieza de Active Directory y la herramienta de Azure Active Directory Connect.
ms.openlocfilehash: cc2a2ca050facaf53f0a235898c31ae7aaeff4ae
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542858"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Planificación de la sincronización del directorio para Office 365
Según las necesidades del negocio y requisitos técnicos, sincronización de directorios es la opción de aprovisionamiento más comunes para los clientes de empresa que se mueven a Office 365. Sincronización de Active Directory permite que las identidades que va a administrar en el Active Directory local y todas las actualizaciones a esa identidad se sincronizan en Office 365.
  
Hay un par de cosas que hay que tener en cuenta al planear una implementación de la sincronización de Active directory, incluida la preparación de Active directory y los requisitos y la funcionalidad de Azure Active Directory. Preparación de Active Directory trata algunas áreas. Se incluyen las actualizaciones de atributos, auditoría y planear la ubicación del controlador de dominio. Planificación de requisitos y la funcionalidad incluye la determinación de los permisos que se requieren, planeación de escenarios de multiforest o directorio, la planeación de la capacidad y sincronización bidireccional.
  
## <a name="office-365-identity-models"></a>Modelos de identidad de Office 365
Office 365 usa dos modelos de autenticación e identidad principales: autenticación y autenticación federada de nube.
  
### <a name="cloud-authentication"></a>Autenticación en la nube
[Identidad de nube](about-office-365-identity.md) : crear y administrar los usuarios en el centro de administración de Office 365, también puede usar Windows PowerShell o Azure Active Directory para administrar los usuarios. 
  
[Sincronizar de hash de contraseña con un inicio de sesión único perfecta](about-office-365-identity.md) - la manera más sencilla de habilitar la autenticación para los objetos de Active directory local en Azure AD. Con la sincronización de hash de contraseña (PBS), sincronizar los objetos de cuenta de usuario de Active Directory local con Office 365 y administrar los usuarios locales. 
  
[Autenticación de paso a través con un inicio de sesión único transparente](about-office-365-identity.md) : proporciona una validación de contraseña simple para servicios de autenticación de Azure AD mediante un agente de software que se ejecuta en uno o más servidores locales para validar a los usuarios directamente con su Active Directory local. 
  
### <a name="federated-authentication"></a>Autenticación federada
[Identidad federada con los servicios de federación de Active Directory AD FS](about-office-365-identity.md) - principalmente para grandes organizaciones con requisitos de autenticación más complejas, local se sincronizan los objetos de Active directory con Office 365 y son las cuentas de usuarios administrada local. 
  
[Proveedores de autenticación e identidad de terceros](about-office-365-identity.md) - Active directory objetos es posible que se sincronizan en Office 365 y acceso a los recursos de nube de local se administra principalmente por un proveedor de identidad de terceros (IdP). 
  
## <a name="active-directory-cleanup"></a>Limpieza de Active Directory
Para ayudar a garantizar una transición sin problemas a Office 365 mediante la sincronización, se recomienda preparar el bosque de Active Directory antes de empezar la implementación de sincronización de directorios de Office 365.
  
Al [Configurar la sincronización de Active directory en Office 365](set-up-directory-synchronization.md), es uno de los pasos para [descargar y ejecuta la herramienta IdFix](install-and-run-idfix.md). Puede usar la herramienta IdFix para ayudar con la [limpieza de directorios](prepare-directory-attributes-for-synch-with-idfix.md).
  
La limpieza del directorio debería centrarse en las siguientes tareas:

- Quite los atributos **proxyAddress** y **userPrincipalName** duplicados.
- Actualice los atributos **userPrincipalName** no válidos o en blanco con atributos **userPrincipalName** válidos.
- Quitar caracteres no válidos y dudosos en **givenName**, apellido ( **sn** ), **sAMAccountName**, **displayName**, **correo**, **proxyAddresses**, **mailNickname**y **userPrincipalName** atributos. Para obtener información detallada sobre la preparación de atributos, vea la [lista de atributos que se sincronizan mediante la herramienta de sincronización de Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).
    
    > [!NOTE]
    > Estos son los mismos atributos que se sincroniza Azure Connect de AD. 
  
## <a name="multiforest-deployment-considerations"></a>Consideraciones de implementación de bosques múltiples
Para varios bosques y las opciones de SSO, use [Conectar de AD de instalación personalizada de Azure](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Si su organización tiene varios bosques para la autenticación (bosques de inicio de sesión), se recomienda lo siguiente:
  
- **Evaluación de la consolidación de los bosques.** En general, hay más sobrecarga necesaria para mantener varios bosques. A menos que su organización tiene restricciones de seguridad que determinan la necesidad de bosques separados, considere la posibilidad de simplificar el entorno local.
- **Uso únicamente en su bosque de inicio de sesión principal.** Considere la posibilidad de implementar Office 365 sólo en su bosque de inicio de sesión principal para la implementación inicial de Office 365. 
    
Si no se pueden consolidar la implementación de Active Directory de varios bosques o está utilizando otros servicios de directorio para administrar identidades, es posible que pueda sincronizar estos con la Ayuda de Microsoft o de un socio.
  
Para obtener más información, consulte [Sincronización de Active Directory de varios bosques con escenario de inicio de sesión único](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Herramientas de integración de Active Directory
Sincronización de directorios es la sincronización de objetos de Active directory (usuarios, grupos y contactos) desde el entorno de Active Directory local a la infraestructura de Active directory de Office 365. Vea las [Herramientas de integración de Active directory](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obtener una lista de las herramientas disponibles y su funcionalidad. La herramienta recomendada para usar es [Conectar de Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Cuando las cuentas de usuario se sincronizan con el directorio de Office 365 por primera vez, se marcan como no activada. No pueden enviar ni recibir correo electrónico, y no consumen licencias de suscripción. Cuando esté listo para asignar suscripciones a Office 365 a usuarios específicos, debe seleccionar y activarlos mediante la asignación de una licencia válida.
  
Sincronización de directorios es necesaria para las características y funciones siguientes:
  
- SSO
    
- Coexistencia de Lync
    
- Exchange implementación híbrida, incluidos:
    
  - Totalmente compartida lista global de direcciones (GAL) entre su entorno de Exchange local y Office 365.
  - Sincronización de información de GAL desde varios sistemas de correo.
  - La capacidad para agregar a los usuarios y quitar usuarios de las ofertas de servicios de Office 365. Esto requiere lo siguiente:
  - Sincronización bidireccional de directorios se debe configurar durante la instalación de la sincronización de Active directory. De forma predeterminada, las herramientas de sincronización de Active directory escriben información de Active directory sólo a la nube. Al configurar la sincronización bidireccional, habilita la funcionalidad de escritura diferida para que un número limitado de atributos de objeto se copian de la nube y, a continuación, les vuelven a escribir su Active Directory local. Reescritura también se conoce como modo de híbrida de Exchange. 
  - Implementación híbrida de Exchange local
  - La capacidad para mover algunos buzones de usuario a Office 365 manteniendo otros usuario buzones locales.
  - Remitentes seguros y remitentes bloqueados locales se replican en Office 365.
  - Función de delegación básica y envío en nombre de otra persona.
  - Tiene una solución de autenticación de tarjetas inteligentes o multifactor integrado local.
    
- Sincronización de fotos, miniaturas, salas de conferencias y grupos de seguridad