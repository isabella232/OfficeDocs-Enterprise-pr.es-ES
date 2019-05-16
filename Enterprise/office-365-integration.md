---
title: Integración de Office 365 con entornos locales
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Obtenga información sobre cómo integrar Office 365 con los servicios de directorio existentes.
ms.openlocfilehash: 1fa044a0a9db0d8422239cf301fea21a2c3d47e9
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069746"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Integración de Office 365 con entornos locales

Puede integrar Office 365 con los servicios de directorio existentes y con una instalación local de Exchange Server, Skype empresarial Server 2015 o SharePoint Server 2013.
  
 - Cuando se integra con los servicios de directorio, puede sincronizar y administrar cuentas de usuario para ambos entornos. También puede Agregar la sincronización de hash de contraseña o el inicio de sesión único (SSO) para que los usuarios puedan iniciar sesión en ambos entornos con sus credenciales locales.
 - Cuando se integra con productos de servidor local, se crea un entorno híbrido. Un entorno híbrido puede ayudarle a migrar usuarios o información a Office 365, o puede seguir teniendo algunos usuarios o información local y algunos en la nube. Para obtener más información acerca de los entornos híbridos, consulte [Office 365 Hybrid Cloud Solutions Overview](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).

También puede usar los asesores de Azure AD para obtener instrucciones de instalación personalizadas:
- [Azure AD Connect Advisor](https://aka.ms/aadconnectpwsync)
- [Asesor de implementación de AD FS](https://aka.ms/adfsguidance)
- [Asistente para la implementación de Azure RMS](https://aka.ms/azuremsguidance)
- [Guía de instalación de Azure AD Premium](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Antes de empezar
Antes de integrar Office 365 y un entorno local, también debe asistir a la planeación de [red y el ajuste del rendimiento de Office 365](network-planning-and-performance.md). También le interesará conocer los modelos de [identidad](about-office-365-identity.md) disponibles en Office 365. 

Vea [dónde administrar las cuentas de usuario de office 365](manage-office-365-accounts.md) para obtener una lista de las herramientas que puede usar para administrar usuarios y cuentas de Office 365. 
  
## <a name="integrate-office-365-with-directory-services"></a>Integración de Office 365 con los servicios de directorio
Si tiene cuentas de usuario existentes en un directorio local, no desea volver a crear todas esas cuentas en Office 365 y arriesgar la introducción de diferencias o errores entre los entornos. La sincronización de directorios le ayuda a reflejar esas cuentas entre su entorno local y en línea. Con la sincronización de directorios, los usuarios no tienen que recordar nueva información para cada entorno y no es necesario crear o actualizar cuentas dos veces. Tendrá que [preparar el directorio local para la](prepare-for-directory-synchronization.md) sincronización de directorios, puede hacerlo manualmente o usar la [herramienta idfix](install-and-run-idfix.md) (la herramienta Idfix solo funciona con Active Directory). 
  
![Usar la sincronización de directorios para mantener sincronizada la información de cuenta de usuario local y en línea](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Si desea que los usuarios puedan iniciar sesión en Office 365 con sus credenciales locales, también puede configurar el SSO. Con SSO, Office 365 está configurado para confiar en el entorno local para la autenticación de usuarios.
  
![Con el inicio de sesión único, la misma cuenta está disponible tanto en el entorno local como en el en línea.](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Las distintas técnicas de administración de cuentas de usuario proporcionan distintas experiencias para los usuarios, como se muestra en la siguiente tabla.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**Sincronización de directorios con o sin sincronización de hash de contraseña o autenticación de paso a través**
Un usuario inicia sesión en su entorno local con su cuenta de usuario (dominio\nombre de usuario). Cuando vayan a Office 365, deben volver a iniciar sesión con su cuenta profesional o educativa (user@domain.com). El nombre de usuario es el mismo en ambos entornos. Al agregar la sincronización de hash de contraseña o la autenticación de paso a través, el usuario tiene la misma contraseña para ambos entornos, pero tendrá que volver a proporcionar las credenciales al iniciar sesión en Office 365. La sincronización de directorios con sincronización de hash de contraseña es el escenario de sincronización de directorios que se usa con más frecuencia.

Para configurar la sincronización de directorios, use Azure Active Directory Connect. Para obtener instrucciones, consulte [configurar la sincronización de directorios para Office 365](set-up-directory-synchronization.md)y [usar Azure ad Connect con la configuración rápida](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Obtenga más información sobre cómo [prepararse para aprovisionar a los usuarios a través de la sincronización de directorios a Office 365](prepare-for-directory-synchronization.md) e [integrar sus identificadores locales con Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>**Sincronización de directorios con SSO**
Un usuario inicia sesión en su entorno local con su cuenta de usuario. Cuando van a Office 365, inician sesión automáticamente o inician sesión con las mismas credenciales que usan para su entorno local (dominio\nombre de usuario).

Para configurar el SSO, también puede usar Azure AD Connect. Para obtener instrucciones, lea [usar Azure ad Connect con configuración personalizada](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Obtenga más información sobre [el acceso a aplicaciones y el inicio de sesión único con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect
Azure AD Connect reemplaza versiones antiguas de herramientas de integración de identidades, como dirSync y sincronización de Azure AD. Para obtener más información, consulte [integración de las identidades locales con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). Si quiere actualizar desde Azure Active Directory Sync a Azure AD Connect, consulte [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240). Vea una arquitectura de solución creada para la [sincronización de directorios (DirSync) de Office 365 en Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).