---
title: Integración de Microsoft 365 con entornos locales
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.date: 10/08/2019
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
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
description: Obtenga información sobre cómo integrar Microsoft 365 con los servicios de directorio existentes.
ms.openlocfilehash: 456e3e73451a07750d707e2fca52df9214c2dfaa
ms.sourcegitcommit: c112869b3ecc0f574b7054ee1edc8c57132f8237
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/15/2020
ms.locfileid: "44736038"
---
# <a name="microsoft-365-integration-with-on-premises-environments"></a>Integración de Microsoft 365 con entornos locales

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Puede integrar Microsoft 365 con los servicios de directorio existentes y con una instalación local de Exchange Server, Skype empresarial Server 2015 o SharePoint Server.
  
 - Cuando se integra con los servicios de directorio, puede sincronizar y administrar cuentas de usuario para ambos entornos. También puede Agregar la sincronización de hash de contraseña o el inicio de sesión único (SSO) para que los usuarios puedan iniciar sesión en ambos entornos con sus credenciales locales.
 - Cuando se integra con productos de servidor local, se crea un entorno híbrido. Un entorno híbrido puede ayudarle a migrar usuarios o información a Microsoft 365, o puede seguir teniendo algunos usuarios o información local y algunos en la nube. Para obtener más información acerca de los entornos híbridos, consulte [información general sobre la nube híbrida](https://docs.microsoft.com/Office365/Enterprise/hybrid-cloud-overview).

También puede usar los asesores de Azure Active Directory (Azure AD) para obtener instrucciones de configuración personalizadas (debe haber iniciado sesión en Microsoft 365):

- [Sincronizar usuarios del directorio de su organización](https://aka.ms/aadconnectpwsync)
- [Asesor de implementación de AD FS](https://aka.ms/adfsguidance)
- [Guía de configuración de Azure AD](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Antes de empezar

Antes de integrar Microsoft 365 y un entorno local, también debe asistir a la [planeación de red y el ajuste del rendimiento](network-planning-and-performance.md). También le interesará conocer los modelos de [identidad](about-office-365-identity.md)disponibles. 

Vea [dónde administrar las cuentas de microsoft 365](manage-office-365-accounts.md) para obtener una lista de las herramientas que puede usar para administrar usuarios y cuentas de Microsoft 365. 
  
## <a name="integrate-microsoft-365-with-directory-services"></a>Integración de Microsoft 365 con los servicios de directorio
Si tiene cuentas de usuario existentes en un directorio local, no desea volver a crear todas esas cuentas en Microsoft 365 y arriesgar la introducción de diferencias o errores entre los entornos. La sincronización de directorios le ayuda a reflejar esas cuentas entre su entorno local y en línea. Con la sincronización de directorios, los usuarios no tienen que recordar nueva información para cada entorno y no es necesario crear o actualizar cuentas dos veces. Tendrá que [preparar el directorio local para la](prepare-for-directory-synchronization.md) sincronización de directorios, puede hacerlo manualmente o usar la [herramienta idfix](install-and-run-idfix.md) (la herramienta Idfix solo funciona con servicios de dominio de Active Directory [AD DS]). 
  
![Usar la sincronización de directorios para mantener sincronizada la información de cuenta de usuario local y en línea](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Si desea que los usuarios puedan iniciar sesión en Microsoft 365 con sus credenciales locales, también puede configurar el SSO. Con SSO, Microsoft 365 está configurado para confiar en el entorno local para la autenticación de usuarios.
  
![Con el inicio de sesión único, la misma cuenta está disponible tanto en el entorno local como en el en línea.](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Las distintas técnicas de administración de cuentas de usuario proporcionan distintas experiencias para los usuarios, como se muestra en la siguiente tabla.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>Sincronización de directorios con o sin sincronización de hash de contraseña o autenticación de paso a través

Un usuario inicia sesión en su entorno local con su cuenta de usuario (dominio\nombre de usuario). Cuando vayan a Microsoft 365, deben volver a iniciar sesión con su cuenta profesional o educativa (user@domain.com). El nombre de usuario es el mismo en ambos entornos. Al agregar la sincronización de hash de contraseña o la autenticación de paso a través, el usuario tiene la misma contraseña para ambos entornos, pero tendrá que volver a proporcionar las credenciales al iniciar sesión en Microsoft 365. La sincronización de directorios con sincronización de hash de contraseña es el escenario de sincronización de directorios que se usa con más frecuencia.

Para configurar la sincronización de directorios, use Azure Active Directory Connect. Para obtener instrucciones, consulte [configurar la sincronización de directorios para Microsoft 365](set-up-directory-synchronization.md)y [Azure ad Connect con la configuración rápida](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Obtenga más información sobre la [preparación para la sincronización de directorios en Microsoft 365](prepare-for-directory-synchronization.md) e [integración de los identificadores locales con Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>Sincronización de directorios con SSO

Un usuario inicia sesión en su entorno local con su cuenta de usuario. Cuando van a Microsoft 365, inician sesión automáticamente o inician sesión con las mismas credenciales que usan para su entorno local (dominio\nombre de usuario).

Para configurar el SSO, también puede usar Azure AD Connect. Para obtener instrucciones, consulte read [Custom Installation of Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Obtenga más información sobre [el inicio de sesión único en aplicaciones en Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect

Azure AD Connect reemplaza versiones antiguas de herramientas de integración de identidades, como DirSync y sincronización de Azure AD. Para obtener más información, vea [¿Qué es la identidad híbrida con Azure Active Directory?](https://go.microsoft.com/fwlink/p/?LinkId=527969). Si quiere actualizar desde Azure Active Directory Sync a Azure AD Connect, consulte [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240). 

Consulte también [implementar la sincronización de directorios de microsoft 365 en Microsoft Azure](https://go.microsoft.com/fwlink/?LinkId=517887).

## <a name="see-also"></a>Vea también

[Información general de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
