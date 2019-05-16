---
title: Información acerca de la identidad de Office 365 y Azure Active Directory
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
- M365-security-compliance
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 06a189e7-5ec6-4af2-94bf-a22ea225a7a9
description: Obtenga información sobre cómo se administra la identidad del usuario en Office 365.
ms.openlocfilehash: 85cfce4b08236bfcee74b6fe6d9c29766e7211c6
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068766"
---
# <a name="understanding-office-365-identity-and-azure-active-directory"></a>Información acerca de la identidad de Office 365 y Azure Active Directory

Office 365 usa el servicio de autenticación y la identidad de usuario basada en la nube de Azure Active Directory (Azure AD) para administrar usuarios. Si se configura la administración de identidades entre la organización local y Office 365 es una decisión temprana que es una de las bases de la infraestructura de la nube. Dado que cambiar esta configuración más adelante puede ser difícil, tenga en cuenta las opciones para determinar qué funciona mejor para las necesidades de su organización. Puede elegir entre dos modelos de autenticación principales en Office 365 para configurar y administrar cuentas de usuario; **autenticación de nube** y **autenticación federada**.
  
Es importante considerar detenidamente cuál de estos modelos de identidad y autenticación debe usar para empezar a trabajar. Piense en el tiempo, la complejidad existente y el costo de implementar y mantener cada una de las opciones de autenticación e identidad. Estos factores son distintos para cada organización; Además, debe comprender los conceptos clave de las opciones de identidad para ayudarle a elegir el modelo de autenticación e identidad que desea usar para la implementación.
  
## <a name="cloud-authentication"></a>Autenticación en la nube

En función de si tiene o no tiene un entorno de Active Directory existente, tiene varias opciones para administrar los servicios de autenticación e identidad para sus usuarios con Office 365.
  
### <a name="cloud-only"></a>Solo de nube

Con el modelo de solo nube, solo se administran las cuentas de usuario en Office 365. No es necesario ningún servidor local; Azure AD los ha administrado en la nube. Puede crear y administrar usuarios en el [centro de administración de Microsoft 365](https://admin.microsoft.com) o mediante cmdlets de [PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell) de Windows PowerShell, y la identidad y la autenticación se administran completamente en la nube de Azure ad. El modelo de solo nube suele ser una buena opción si: 
  
- No tiene ningún otro directorio de usuarios local.
    
- Tiene un directorio local muy complejo y simplemente desea evitar el trabajo de integración con él.
    
- Tiene un directorio local existente, pero desea ejecutar una prueba o un piloto de Office 365. Más adelante, puede hacer coincidir los usuarios de la nube con los usuarios locales cuando esté listo para conectarse con el directorio local.
    
Para empezar a trabajar con la identidad de nube, consulte [configurar Office 365 para empresas](https://support.office.com/article/6a3a29a0-e616-4713-99d1-15eda62d04fa).
  
### <a name="password-hash-sync-with-seamless-single-sign-on"></a>Sincronización de hash de contraseña con inicio de sesión único sin problemas

La forma más sencilla de habilitar la autenticación para los objetos de directorio local en Azure AD. Con la sincronización de hash de contraseña (PHS), se sincronizan los objetos de cuenta de usuario de Active Directory local con Office 365 y se administran los usuarios de forma local. Los valores hash de las contraseñas de usuario se sincronizan desde Active Directory local a Azure AD para que los usuarios tengan la misma contraseña local y en la nube. Cuando se cambian o se restablecen las contraseñas locales, los nuevos hash de contraseña se sincronizan con Azure AD para que los usuarios siempre puedan usar la misma contraseña para los recursos de la nube y los recursos locales. Las contraseñas nunca se envían a Azure AD o se almacenan en Azure AD en texto no cifrado. Algunas características Premium de Azure AD, como la protección de identidad, requieren PHS independientemente del método de autenticación que se seleccione. Con el inicio de sesión único sin problemas, los usuarios inician sesión automáticamente en Azure AD cuando están en sus dispositivos corporativos y se conectan a la red corporativa.
  
Obtenga más información sobre cómo [elegir la sincronización de hash de contraseña](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) y [el inicio de sesión único sin interrupciones](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
### <a name="pass-through-authentication-with-seamless-single-sign-on"></a>Autenticación de paso a través con inicio de sesión único sin interrupciones

Proporciona una validación de contraseña sencilla para los servicios de autenticación de Azure AD mediante un agente de software que se ejecuta en uno o varios servidores locales para validar a los usuarios directamente con Active Directory local. Con la autenticación de paso a través (PTA), se sincronizan los objetos de cuenta de usuario de Active Directory local con Office 365 y se administran los usuarios de forma local. Permite a los usuarios iniciar sesión en recursos y aplicaciones locales y de Office 365 usando su cuenta local y su contraseña. Esta configuración valida las contraseñas de los usuarios directamente en su Active Directory local sin enviar valores de hash de contraseña a Office 365. Las empresas con requisitos de seguridad para aplicar inmediatamente Estados de cuentas de usuario locales, directivas de contraseñas y horas de inicio de sesión usarían este método de autenticación. Con el inicio de sesión único sin problemas, los usuarios inician sesión automáticamente en Azure AD cuando están en sus dispositivos corporativos y se conectan a la red corporativa.
  
Obtenga más información sobre cómo [elegir la autenticación de paso a través](https://docs.microsoft.com/azure/security/azure-ad-choose-authn) y [el inicio de sesión único sin interrupciones](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-sso).
  
## <a name="federated-authentication-options"></a>Opciones de autenticación federada

Si tiene un entorno de Active Directory existente en local, puede integrar Office 365 con su directorio mediante la autenticación federada para administrar los servicios de autenticación e identidad para los usuarios en Office 365.
  
### <a name="federated-identity-with-active-directory-federation-services-ad-fs"></a>Identidad federada con los servicios de Federación de Active Directory (AD FS)

Principalmente para grandes empresas con requisitos de autenticación más complejos, los objetos de directorio local se sincronizan con Office 365 y las cuentas de usuario se administran de forma local. Con AD FS, los usuarios tienen la misma contraseña local y en la nube, y no tienen que iniciar sesión de nuevo para usar Office 365. Este modelo de autenticación federada puede proporcionar requisitos de autenticación adicionales, como la autenticación basada en tarjeta inteligente o una autenticación multifactor de terceros y suele ser necesario cuando las organizaciones tienen un requisito de autenticación no es compatible de forma nativa con Azure AD.
  
Obtenga más información sobre cómo [elegir la identidad federada con AD FS](https://docs.microsoft.com/azure/security/azure-ad-choose-authn).
  
### <a name="third-party-authentication-and-identity-providers"></a>Proveedores de autenticación e identidad de terceros

Los objetos de directorio local se pueden sincronizar con Office 365 y el acceso a recursos de la nube es administrado principalmente por un proveedor de identidades de terceros (IdP). Si su organización usa una solución de Federación de terceros, puede configurar el inicio de sesión con esa solución para Office 365, siempre que la solución de Federación de terceros sea compatible con Azure AD.
  
Obtenga más información sobre la [compatibilidad de Federación de Azure ad](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect-federation-compatibility).
  
## <a name="configuring-identity-and-authentication-with-office-365"></a>Configuración de la identidad y la autenticación con Office 365

La integración de los directorios locales con Office 365 y Azure AD se ha simplificado con [Azure ad Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect). Azure AD Connect es la mejor forma de conectar los directorios y es la recomendación de Microsoft para que las organizaciones sincronicen sus usuarios a la nube.
  
También puede usar los asesores de Azure AD: [Azure ad Connect Advisor](https://aka.ms/aadconnectpwsync), el asesor de [implementación de AD FS](https://aka.ms/adfsguidance)y la [Guía de configuración de Azure ad Premium](https://aka.ms/aadpguidance).
  
## <a name="video-training"></a>Vídeo de aprendizaje

Para obtener más información, consulte el curso de vídeo [Office 365: administrar identidades con Azure ad Connect](https://support.office.com/article/90991a1d-c0ab-479a-b413-35c9706f6fed.aspx)y ofrecido por LinkedIn Learning.
