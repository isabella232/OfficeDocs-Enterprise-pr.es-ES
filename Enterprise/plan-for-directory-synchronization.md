---
title: Identidad híbrida y sincronización de directorios para Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.date: 06/09/2020
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MOE150
- MET150
ms.assetid: d3577c90-dda5-45ca-afb0-370d2889b10f
description: Describe la sincronización de directorios con Microsoft 365, la limpieza de los servicios de dominio de Active Directory y la herramienta Azure Active Directory Connect.
ms.openlocfilehash: ef7af68a65e4799e7bffbe6edba4f2b237a4d8b4
ms.sourcegitcommit: ff1d21fe5eb8eba7a65d250aa37aadc8f503a10a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2020
ms.locfileid: "44698967"
---
# <a name="hybrid-identity-and-directory-synchronization-for-microsoft-365"></a>Identidad híbrida y sincronización de directorios para Microsoft 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

En función de las necesidades de negocio y los requisitos técnicos, el modelo de identidad híbrida y la sincronización de directorios son las opciones más comunes para los clientes empresariales que están adoptando Microsoft 365. La sincronización de directorios permite administrar las identidades de los servicios de dominio de Active Directory (AD DS) y todas las actualizaciones de las cuentas de usuario, los grupos y los contactos se sincronizan con el inquilino de Azure Active Directory (Azure AD) de la suscripción a Microsoft 365.

>[!Note]
>Cuando las cuentas de usuario de AD DS se sincronizan por primera vez, no se les asigna automáticamente una licencia de Microsoft 365 y no pueden acceder a los servicios de Microsoft 365, como el correo electrónico. Primero debe asignarles una ubicación de uso. A continuación, asigne una licencia a estas cuentas de usuario, ya sea de forma individual o dinámica a través de la pertenencia a grupos.
>

## <a name="authentication-for-hybrid-identity"></a>Autenticación para la identidad híbrida

Hay dos tipos de autenticación cuando se usa el modelo de identidad híbrida:

- Autenticación administrada

  Azure AD administra el proceso de autenticación mediante el uso de una versión hash de la contraseña almacenada de forma local o envía las credenciales a un agente de software local para que lo autentique el AD DS local.

- Autenticación federada

  Azure AD redirige al equipo cliente que solicita la autenticación a otro proveedor de identidad.

### <a name="managed-authentication"></a>Autenticación administrada

Hay dos tipos de autenticación administrada:

- Sincronización de hash de contraseña (PHS)

  Azure AD realiza la autenticación en sí.

- Autenticación de paso a través (PTA)

  Azure AD tiene AD DS realizar la autenticación.


#### <a name="password-hash-synchronization-phs"></a>Sincronización de hash de contraseña (PHS)

Con PHS, se sincronizan las cuentas de usuario de AD DS con Microsoft 365 y se administran los usuarios de forma local. Los valores hash de las contraseñas de usuario se sincronizan de AD DS con Azure AD para que los usuarios tengan la misma contraseña local y en la nube. Esta es la forma más sencilla de habilitar la autenticación para las identidades de AD DS en Azure AD. 

![Sincronización de hash de contraseña (PHS)](./media/plan-for-directory-synchronization/phs-authentication.png)

Cuando se cambian o se restablecen las contraseñas locales, los nuevos hash de contraseña se sincronizan con Azure AD para que los usuarios siempre puedan usar la misma contraseña para los recursos de la nube y los recursos locales. Las contraseñas de usuario nunca se envían a Azure AD o se almacenan en Azure AD en texto no cifrado. Algunas características Premium de Azure AD, como la protección de identidad, requieren PHS independientemente del método de autenticación que se seleccione.
  
Vea [elegir el método de autenticación correcto](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) para obtener más información.
  
#### <a name="pass-through-authentication-pta"></a>Autenticación de paso a través (PTA)

PTA proporciona una validación de contraseña simple para los servicios de autenticación de Azure AD mediante un agente de software que se ejecuta en uno o varios servidores locales para validar a los usuarios directamente con AD DS. Con PTA, se sincronizan las cuentas de usuario de AD DS con Microsoft 365 y se administran los usuarios de forma local. 

![Autenticación de paso a través (PTA)](./media/plan-for-directory-synchronization/pta-authentication.png)

PTA permite que los usuarios inicien sesión en las aplicaciones y los recursos locales y de Microsoft 365 usando su cuenta local y su contraseña. Esta configuración valida las contraseñas de los usuarios directamente en AD DS local sin almacenar los hash de contraseña en Azure AD. 

PTA también es para las organizaciones con requisitos de seguridad para aplicar inmediatamente Estados de cuentas de usuario locales, directivas de contraseñas y horas de inicio de sesión. 
  
Vea [elegir el método de autenticación correcto](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) para obtener más información.
  
### <a name="federated-authentication"></a>Autenticación federada

La autenticación federada es principalmente para grandes empresas con requisitos de autenticación más complejos. Las identidades de AD DS se sincronizan con Microsoft 365 y las cuentas de usuario se administran de forma local. Con la autenticación federada, los usuarios tienen la misma contraseña local y en la nube, y no tienen que iniciar sesión de nuevo para usar Microsoft 365. 

La autenticación federada puede admitir requisitos de autenticación adicionales, como la autenticación basada en tarjeta inteligente o una autenticación multifactor de terceros y suele ser necesario cuando las organizaciones tienen un requisito de autenticación que Azure AD no admite de forma nativa.
 
Vea [elegir el método de autenticación correcto](https://docs.microsoft.com/azure/active-directory/hybrid/choose-ad-authn) para obtener más información.
  
#### <a name="third-party-authentication-and-identity-providers"></a>Proveedores de autenticación e identidad de terceros

Los objetos de directorio local se pueden sincronizar con Microsoft 365 y el acceso a recursos de la nube es administrado principalmente por un proveedor de identidades de terceros (IdP). Si su organización usa una solución de Federación de terceros, puede configurar el inicio de sesión con esa solución para Microsoft 365, siempre que la solución de Federación de terceros sea compatible con Azure AD.
  
Consulte la [lista de compatibilidad de Federación de Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility) para obtener más información.
  
## <a name="ad-ds-cleanup"></a>Limpieza de AD DS

Para ayudar a garantizar una transición sin problemas a Microsoft 365 mediante la sincronización, debe preparar el bosque de AD DS antes de comenzar con la implementación de sincronización de directorios de Microsoft 365.
  
Al [configurar la sincronización de directorios](set-up-directory-synchronization.md), uno de los pasos es [Descargar y ejecutar la herramienta IdFix](install-and-run-idfix.md). Puede usar la herramienta IdFix para ayudar con la [limpieza de directorios](prepare-directory-attributes-for-synch-with-idfix.md).
  
La limpieza de directorios debe centrarse en las siguientes tareas:

- Quitar los atributos **proxyAddress** y **userPrincipalName** duplicados.
- Actualice los atributos **userPrincipalName** no válidos o en blanco con atributos **userPrincipalName** válidos.
- Quite los caracteres dudosos y no válidos de los atributos **givenName**, apellidos ( **SN** ), **samAccountName**, **displayName**, **mail**, **proxyAddresses**, **mailNickname**y **userPrincipalName** . Para obtener información detallada sobre la preparación de atributos, consulte [lista de atributos que se sincronizan mediante la herramienta de sincronización de Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=396719).

    > [!NOTE]
    > Estos son los mismos atributos que Azure AD Connect sincroniza. 
  
## <a name="multi-forest-deployment-considerations"></a>Consideraciones sobre la implementación de varios bosques

Para varios bosques y opciones de SSO, use una [instalación personalizada de Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).
  
Si su organización tiene varios bosques para la autenticación (bosques de inicio de sesión), recomendamos encarecidamente lo siguiente:
  
- **Considere la posibilidad de consolidar los bosques.** En general, es necesario más carga para mantener varios bosques. A menos que la organización tenga restricciones de seguridad que determinen la necesidad de bosques independientes, considere la posibilidad de simplificar el entorno local.
- **Use solamente en el bosque de inicio de sesión principal.** Considere la posibilidad de implementar Microsoft 365 solo en el bosque de inicio de sesión principal para la implementación inicial de Microsoft 365. 

Si no puede consolidar su implementación de AD DS de varios bosques o está usando otros servicios de directorio para administrar las identidades, es posible que pueda sincronizarlas con la ayuda de Microsoft o de un asociado.
  
Consulte [topologías para Azure ad Connect](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-topologies) para obtener más información.
  
## <a name="features-that-are-dependent-on-directory-synchronization"></a>Características que dependen de la sincronización de directorios
  
La sincronización de directorios es necesaria para las siguientes características y funciones:
  
- Inicio de sesión único de línea directa de Azure AD (SSO)
- Coexistencia de Skype
- Implementación híbrida de Exchange, que incluye:
  - Lista global de direcciones (GAL) totalmente compartida entre el entorno de Exchange local y Microsoft 365.
  - Sincronización de información de GAL desde varios sistemas de correo.
  - La capacidad de agregar usuarios y quitar usuarios de las ofertas de servicio de Microsoft 365. Esto requiere lo siguiente:
  - La sincronización bidireccional debe configurarse durante la configuración de la sincronización de directorios. De forma predeterminada, las herramientas de sincronización de directorios escriben información de directorio solo en la nube. Cuando se configura la sincronización bidireccional, se habilita la funcionalidad de reescritura de modo que se copie un número limitado de atributos de objeto de la nube y, a continuación, se escriban de nuevo en el AD DS local. La escritura diferida también se conoce como modo híbrido de Exchange. 
  - Una implementación híbrida de Exchange local
  - La capacidad de mover algunos buzones de usuario a Microsoft 365 mientras se mantienen otros buzones de usuario locales.
  - Los remitentes seguros y los remitentes bloqueados locales se replican en Microsoft 365.
  - Función de delegación básica y envío en nombre de otra persona.
  - Tiene una solución de autenticación multifactor o de tarjeta inteligente local integrada.
- Sincronización de fotos, miniaturas, salas de conferencias y grupos de seguridad

## <a name="next-step"></a>Paso siguiente

Cuando esté listo para implementar la identidad híbrida, vea [preparar el aprovisionamiento de usuarios](prepare-for-directory-synchronization.md).
  
## <a name="see-also"></a>Vea también

[Información general de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)

