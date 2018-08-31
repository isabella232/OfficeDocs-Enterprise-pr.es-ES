---
title: Descripción de la identidad de Office 365 y Azure Active Directory
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Obtenga información sobre cómo se administra la identidad del usuario en Office 365.
ms.openlocfilehash: 0fb6e77aef4495b2284256c13cb21320e6292746
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914985"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Descripción de la identidad de Office 365 y Azure Active Directory

Office 365 usa el servicio de autenticación e identidad de usuario basada en la nube Azure Active Directory (AD Azure) para administrar los usuarios. Sobre la selección si está configurada la administración de identidades entre la organización local y Office 365 es una decisión anticipada que es una de las bases de la infraestructura de la nube. Debido a que puede resultar difícil cambiar esta configuración más adelante, considere detenidamente las opciones para determinar qué funciona mejor para las necesidades de su organización. Puede elegir entre dos modelos de autenticación principal en Office 365 para configurar y administrar cuentas de usuario; **la autenticación en la nube** y **autenticación federada**.
  
Es importante considerar detenidamente cuál de estos modelos de autenticación e identidad a usar para obtener la copia de seguridad y que se está ejecutando. Piense en el tiempo, la complejidad existente y el costo para implementar y mantener cada una de las opciones de autenticación e identidad. Estos factores son diferentes para cada organización; y debe comprender los conceptos clave para las opciones de identidad para ayudarle a elegir la autenticación y el modelo de identidad que desea usar para la implementación.
  
## <a name="cloud-authentication"></a>Autenticación en la nube

En función de si tienen o no tienen una existente Active Directory entorno local, dispone de varias opciones para administrar los servicios de autenticación e identidad de los usuarios con Office 365.
  
### <a name="cloud-only"></a>Basada solo en la nube

Con el modelo de nube, administrar sólo las cuentas de usuario en Office 365. No hay servidores locales son necesarios; se administra completamente en la nube por Azure AD. Puede crear y administrar los usuarios en el centro de administración de Office 365, o mediante el uso de Windows PowerShell [cmdlets de PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) y la identidad y la autenticación que se administran completamente en la nube por Azure AD. El modelo de nube suele ser aconsejable si: 
  
- No tener ningún directorio de usuarios de local.
    
- Tiene un directorio local muy compleja y simplemente desea evitar el trabajo para integrar con él.
    
- Tiene un directorio local existente, pero desea ejecutar una versión de prueba o piloto de Office 365. Más adelante, puede hacer coincidir los usuarios en la nube para los usuarios locales cuando esté listo para conectarse a su directorio local.
    
Para empezar con la identidad de nube, consulte [configurar Office 365 para la empresa](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Sincronización de hash de contraseña con un inicio de sesión único perfecta

La forma más sencilla para habilitar la autenticación para los objetos de Active directory local en Azure AD. Con la sincronización de hash de contraseña (PBS), sincronizar los objetos de cuenta de usuario de Active Directory local con Office 365 y administrar los usuarios locales. Los valores hash de las contraseñas de usuario se sincronizan desde su Active Directory local a Azure AD para que los usuarios tengan la misma contraseña local y en la nube. Cuando las contraseñas se cambian o restablecer local, se sincronizan los hashes de contraseña nueva para Azure AD para que los usuarios siempre pueden usar la misma contraseña para los recursos en la nube y locales. Las contraseñas nunca se envían a Azure AD o almacenadas en Azure AD en texto no cifrado. Algunas características de premium de Azure AD, tales como la protección de identidad, requieren PBS independientemente de que está seleccionado el método de autenticación. Con perfecta de sesión único, los usuarios se conectan automáticamente a Azure AD cuando son en sus dispositivos corporativos y conectados a la red corporativa.
  
Obtenga más información sobre cómo [Elegir la sincronización de contraseñas hash](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) y [un inicio de sesión único sin problemas](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Autenticación de paso a través con un inicio de sesión único perfecta

Proporciona una validación de contraseña simple para servicios de autenticación de Azure AD mediante un agente de software que se ejecuta en uno o más servidores locales para validar a los usuarios directamente con su Active Directory local. Con la autenticación de paso a través (PTA), sincronizar objetos de cuenta de usuario de Active Directory local con Office 365 y administrar los usuarios locales. Permite a los usuarios a iniciar sesión en local y recursos de Office 365 y las aplicaciones que usan su cuenta local y la contraseña. Esta configuración valida las contraseñas de los usuarios directamente en su Active Directory local sin enviar los hashes de contraseña a Office 365. Estados de las empresas con un requisito de seguridad para aplicar inmediatamente la cuenta de usuario local, las directivas de contraseña y las horas de inicio de sesión se utilizan este método de autenticación. Con perfecta de sesión único, los usuarios se conectan automáticamente a Azure AD cuando son en sus dispositivos corporativos y conectados a la red corporativa.
  
Obtenga más información acerca de la [elección de autenticación de paso a través](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) y [perfecta single sign-on](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Opciones de autenticación federada

Si tiene una existente Active Directory entorno local, puede integrar Office 365 con su directorio mediante el uso de autenticación federada para administrar los servicios de autenticación e identidad de los usuarios de Office 365.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Identidad federada con los servicios de federación de Active Directory (AD FS)

Principalmente para grandes organizaciones con requisitos de autenticación más complejos, local se sincronizan los objetos de Active directory con Office 365 y las cuentas de los usuarios son administrados local. Con AD FS, los usuarios tienen la misma contraseña local y en la nube y no tienen que iniciar sesión de nuevo usar Office 365. Este modelo de autenticación federada puede proporcionar los requisitos de autenticación adicionales, como la autenticación basada en tarjeta inteligente o una autenticación multifactor de terceros y normalmente no es necesaria cuando las organizaciones tienen un requisito de autenticación no admite de forma nativa Azure AD.
  
Obtener más información acerca de cómo [Elegir una identidad federada con AD FS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).
  
### <a name="third-party-authentication-and-identity-providers"></a>Proveedores de autenticación e identidad de terceros

Local se pueden sincronizar objetos de directorio a Office 365 y acceso a los recursos en la nube se administra principalmente mediante un proveedor de identidad de terceros (IdP). Si su organización utiliza una solución de federación de terceros, puede configurar inicio de sesión con esa solución para Office 365 siempre que la solución de federación de terceros es compatible con Azure AD.
  
Obtenga más información acerca de la [compatibilidad de federación de AD de Azure](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Configuración de autenticación e identidad con Office 365

Integración de los directorios local con Office 365 y Azure AD se ha simplificado con [Azure Connect de AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Conectar de Azure AD es la mejor forma de conectar los directorios y recomendación de Microsoft para las organizaciones a sus usuarios a la nube de sincronización.
  
También puede usar los asesores de Azure AD: el [Asesor de Azure Connect de AD](https://aka.ms/aadconnectpwsync), el [Asesor de implementación de AD FS](https://aka.ms/adfsguidance)y la [Guía de configuración de Azure AD Premium](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Aprendizaje en vídeo

Para obtener más información, vea el curso de vídeo [Office 365: administrar identidades utilizando Azure AD conectar](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx), la mano de aprendizaje de LinkedIn.
