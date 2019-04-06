---
title: Planeación de la sincronización de directorios para Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Describe la sincronización de directorios con Office 365, limpieza de Active Directory y la herramienta de Azure Active Directory Connect.
ms.openlocfilehash: 1a7c63f699c51c829aaab5b70cb6a1a203bca3be
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001833"
---
# <a name="plan-for-directory-synchronization-for-office-365"></a>Planeación de la sincronización de directorios para Office 365

Según las necesidades empresariales y los requisitos técnicos, la sincronización de directorios es la opción de aprovisionamiento más común para los clientes empresariales que se mueven a Office 365. La sincronización de directorios permite que las identidades se administren en Active Directory local y todas las actualizaciones de dicha identidad se sincronizan con Office 365.
  
Hay un par de cosas que se deben tener en cuenta al planear una implementación de la sincronización de directorios, incluida la preparación del directorio, y los requisitos y la funcionalidad de Azure Active Directory. La preparación de directorios abarca un número muy reducido de áreas. Incluyen actualizaciones de atributos, auditoría y planeación de la ubicación de los controladores de dominio. Los requisitos y la funcionalidad de planeación incluyen la determinación de los permisos necesarios, la planeación de escenarios de varios bosques y directorios, la planeación de la capacidad y la sincronización bidireccional.
  
## <a name="office-365-identity-models"></a>Modelos de identidad de Office 365

Office 365 usa dos modelos de autenticación e identidad principales: la autenticación en la nube y la autenticación federada.
  
### <a name="cloud-authentication"></a>Autenticación en la nube

[Identidad de nube](about-office-365-identity.md) : cree y administre usuarios en el [centro de administración de Microsoft 365](https://admin.microsoft.com), también puede usar Windows PowerShell o Azure Active Directory para administrar los usuarios.
  
[Sincronización de hash de contraseña con inicio de sesión único sin interrupciones](about-office-365-identity.md) : la forma más sencilla de habilitar la autenticación para los objetos de directorio local en Azure ad. Con la sincronización de hash de contraseña (PHS), se sincronizan los objetos de cuenta de usuario de Active Directory local con Office 365 y se administran los usuarios de forma local.
  
[Autenticación de paso a través con el inicio de sesión único sin problemas](about-office-365-identity.md) : proporciona una validación de contraseña sencilla para los servicios de autenticación de Azure ad mediante un agente de software que se ejecuta en uno o varios servidores locales para validar a los usuarios directamente con su Active Directory local.
  
### <a name="federated-authentication"></a>Autenticación federada

[Identidad federada con los servicios de Federación de Active Directory AD FS](about-office-365-identity.md) : principalmente para grandes organizaciones empresariales con requisitos de autenticación más complejos, los objetos del directorio local se sincronizan con Office 365 y las cuentas de los usuarios se administrada de forma local.
  
Los objetos del directorio local de [autenticación e identidad de terceros](about-office-365-identity.md) se pueden sincronizar con Office 365 y el acceso a recursos de la nube es administrado principalmente por un proveedor de identidades de terceros (IDP).
  
## <a name="active-directory-cleanup"></a>Limpieza de Active Directory

Para ayudar a garantizar una transición sin problemas a Office 365 mediante la sincronización, se recomienda encarecidamente preparar el bosque de Active Directory antes de comenzar la implementación de sincronización de directorios de Office 365.
  
Al [configurar la sincronización de directorios en Office 365](set-up-directory-synchronization.md), uno de los pasos es [Descargar y ejecutar la herramienta IdFix](install-and-run-idfix.md). Puede usar la herramienta IdFix para ayudarle con la [limpieza de directorios](prepare-directory-attributes-for-synch-with-idfix.md).
  
La limpieza de directorios debe centrarse en las siguientes tareas:

- Quitar los atributos **proxyAddress** y **userPrincipalName** duplicados.
- Actualice los atributos **userPrincipalName** no válidos o en blanco con atributos **userPrincipalName** válidos.
- Quitar los caracteres dudosos y no válidos de **givenName**, apellidos ( **SN** ), **samAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**y **userPrincipalName** sus. Para obtener información detallada sobre la preparación de atributos, consulte [lista de atributos que se sincronizan mediante la herramienta de sincronización de Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Estos son los mismos atributos que Azure AD Connect sincroniza. 
  
## <a name="multi-forest-deployment-considerations"></a>Consideraciones sobre la implementación de varios bosques

Para varios bosques y opciones de SSO, use la [instalación personalizada de Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Si su organización tiene varios bosques para la autenticación (bosques de inicio de sesión), recomendamos encarecidamente lo siguiente:
  
- **Evaluar la consolidación de los bosques.** En general, es necesario más carga para mantener varios bosques. A menos que la organización tenga restricciones de seguridad que determinen la necesidad de bosques independientes, considere la posibilidad de simplificar el entorno local.
- **Use solamente en el bosque de inicio de sesión principal.** Considere la posibilidad de implementar Office 365 solo en el bosque de inicio de sesión principal para su lanzamiento inicial de Office 365. 

Si no puede consolidar su implementación de Active Directory de varios bosques o está usando otros servicios de directorio para administrar las identidades, es posible que pueda sincronizarlas con la ayuda de Microsoft o de un asociado.
  
Para obtener más información, vea [sincronización de directorios de varios bosques con escenario de inicio de sesión único](https://go.microsoft.com/fwlink/p/?LinkId=525321).
  
## <a name="directory-integration-tools"></a>Herramientas de integración de directorios

La sincronización de directorios es la sincronización de objetos de directorio (usuarios, grupos y contactos) desde el entorno local de Active Directory a la infraestructura de directorios de Office 365. Consulte [herramientas de integración de directorios](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obtener una lista de las herramientas disponibles y su funcionalidad. La herramienta que se recomienda usar es [Azure Active Directory Connect](https://go.microsoft.com/fwlink/?LinkId=525323).
  
Cuando las cuentas de usuario se sincronizan con el directorio de Office 365 por primera vez, se marcan como no activadas. No pueden enviar ni recibir correo electrónico y no consumen licencias de suscripción. Cuando esté listo para asignar suscripciones de Office 365 a usuarios específicos, debe seleccionarlas y activarlas asignando una licencia válida.
  
La sincronización de directorios es necesaria para las siguientes características y funciones:
  
- SSO
- Coexistencia de Skype
- Implementación híbrida de Exchange, que incluye:
  - Lista global de direcciones (GAL) totalmente compartida entre el entorno de Exchange local y Office 365.
  - Sincronización de información de GAL desde varios sistemas de correo.
  - La capacidad de agregar usuarios y quitar usuarios de las ofertas de servicio de Office 365. Esto requiere lo siguiente:
  - La sincronización bidireccional debe configurarse durante la configuración de la sincronización de directorios. De forma predeterminada, las herramientas de sincronización de directorios escriben información de directorio solo en la nube. Cuando se configura la sincronización bidireccional, se habilita la funcionalidad de reescritura de modo que se copie un número limitado de atributos de objeto de la nube y, a continuación, se escriban de nuevo en el Active Directory local. La escritura diferida también se conoce como modo híbrido de Exchange. 
  - Una implementación híbrida de Exchange local
  - La capacidad de mover algunos buzones de usuario a Office 365 al mismo tiempo que se conservan otros buzones de usuario locales.
  - Los remitentes seguros y los remitentes bloqueados locales se replican en Office 365.
  - Función de delegación básica y envío en nombre de otra persona.
  - Tiene una solución de autenticación multifactor o de tarjeta inteligente local integrada.
- Sincronización de fotos, miniaturas, salas de conferencias y grupos de seguridad