---
title: Integración de Office 365 con entornos local
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- LYN150
- SPS150
- MOE150
- MED150
ms.assetid: 263faf8d-aa21-428b-aed3-2021837a4b65
description: Obtenga información sobre cómo integrar Office 365 con los servicios de directorio existentes.
ms.openlocfilehash: b660dda74303a3bf0fa92bc8e3146cd2c9add662
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542862"
---
# <a name="office-365-integration-with-on-premises-environments"></a>Integración de Office 365 con entornos local

También puede integrar Office 365 con los servicios de directorio existentes y con una instalación local de Exchange Server, Skype para Business Server 2015 o SharePoint Server 2013.
  
 - Al integrar con servicios de Active directory, puede sincronizar y administrar cuentas de usuario para ambos entornos. También puede agregar la sincronización de hash de contraseña o inicio de sesión único (SSO) por lo que los usuarios pueden iniciar sesión en ambos entornos con sus credenciales locales.
 - Al integrar con productos de servidor local, cree un entorno híbrido. Un entorno híbrido puede ayudar a migrar los usuarios o información a Office 365 o puede seguir tienen algunos usuarios o algunos información local y algunos en la nube. Para obtener más información sobre entornos híbridos, vea [Introducción a las soluciones de Office 365 híbrida en la nube](https://support.office.com/article/59616fab-acdb-40e9-b414-cf0c965c80b7).

También puede usar los asesores de Azure AD para obtener instrucciones de instalación personalizada:
- [Asesor de Azure Connect de AD](https://aka.ms/aadconnectpwsync)
- [Asesor de implementación de AD FS](https://aka.ms/adfsguidance)
- [Asistente para la implementación de RMS de Azure](https://aka.ms/azuremsguidance)
- [Guía de instalación de Azure AD Premium](https://aka.ms/aadpguidance)
   
## <a name="before-you-begin"></a>Antes de empezar
Antes de integrar un entorno local y Office 365, debe asistir a la [planeación de la red y ajuste del rendimiento de Office 365](network-planning-and-performance.md). También deseará comprender los [modelos de identidad](about-office-365-identity.md) disponibles en Office 365. 

Vea [donde para administrar usuarios de Office 365 cuentas](manage-office-365-accounts.md) para obtener una lista de herramientas que puede utilizar para administrar las cuentas y los usuarios de Office 365. 
  
## <a name="integrate-office-365-with-directory-services"></a>Integrar Office 365 con servicios de Active directory
Si tiene cuentas de usuario existentes en un directorio local, no desea volver a crear todas las cuentas en Office 365 y presentación de diferencias o errores entre los entornos de riesgo. Sincronización de Active Directory le ayuda a reflejar esas cuentas entre su en línea y local de entornos. Con la sincronización de directorios, los usuarios no tienen que recordar información nueva para cada entorno y no tiene que crear o actualizar las cuentas de dos veces. Será necesario para la [preparación de su directorio local](prepare-for-directory-synchronization.md) para la sincronización de Active directory, puede hacerlo manualmente o usar la [herramienta IdFix](install-and-run-idfix.md) (IdFix herramienta sólo funciona con Active Directory). 
  
![Usar sincronización de Active directory para mantener local y la información de la cuenta de usuario en pantalla sincronizado](media/a64af0d0-9be6-46b1-8727-277e683abf5e.png)
  
Si desea que los usuarios puedan iniciar sesión en Office 365 con sus credenciales locales, también puede configurar SSO. Con SSO, Office 365 está configurado para confiar en el entorno local para la autenticación de usuario.
  
![Con el inicio de sesión único, la misma cuenta está disponible en entornos en línea y local](media/d76235f2-8a53-405e-b8ef-dfa4cfc208b8.png)
  
Las técnicas de administración de cuenta de usuario diferente proporcionan experiencias de diferentes para los usuarios, tal como se muestra en la siguiente tabla.
 
### <a name="directory-synchronization-with-or-without-password-hash-synchronization-or-pass-through-authentication"></a>**Sincronización de directorios con o sin autenticación de paso a través o de sincronización de hash de contraseña**
Un usuario inicia sesión en su entorno local con su cuenta de usuario (DOMINIO\nombre de usuario). Cuando vayan a Office 365, debe vuelva a iniciarla con su cuenta de trabajo o escuela (user@domain.com). El nombre de usuario es el mismo en ambos entornos. Cuando se agrega la sincronización de contraseñas hash o autenticación de paso a través, el usuario tiene la misma contraseña para ambos entornos, pero tendrá esas credenciales que volver a proporcionar al iniciar sesión en Office 365. Sincronización de directorios con la sincronización de contraseñas hash es el escenario de sincronización de directorios usadas con más frecuencia.

Para configurar la sincronización de directorios, use Azure Active Directory Connect. Para obtener instrucciones, lea [: configurar la sincronización de Active directory para Office 365](set-up-directory-synchronization.md)y [Azure usar AD conectar con la configuración de express](https://go.microsoft.com/fwlink/p/?LinkId=698537).

Obtener más información acerca de la [Preparación para abastecer a los usuarios a través de sincronización de directorios para Office 365](prepare-for-directory-synchronization.md) e [integración de su local que se identifica con Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=518101).

### <a name="directory-synchronization-with-sso"></a>**Sincronización de directorios con SSO**
Un usuario inicia sesión en su entorno local con su cuenta de usuario. Cuando vayan a Office 365, ya sea han iniciado sesión automáticamente, o inicien sesión con las mismas credenciales que se utilizan para su entorno local (DOMINIO\nombre de usuario).

Para configurar SSO también usar Azure Connect de AD. Para obtener instrucciones, lea [uso Azure AD conectar con una configuración personalizada](https://go.microsoft.com/fwlink/p/?LinkID=698430).

Obtenga más información acerca de [acceso de la aplicación y un inicio de sesión único con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698604).

## <a name="azure-ad-connect"></a>Azure AD Connect
Conectar de Azure AD reemplaza las versiones anteriores de herramientas de integración de identidad, como la sincronización de directorios y sincronización de AD de Azure. Para obtener más información, vea [integración de sus identidades local con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969). Si desea actualizar de sincronización de Azure Active Directory a Azure Connect de AD, vea [las instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240). Vea una arquitectura de solución generada [Office 365 sincronización](https://go.microsoft.com/fwlink/?LinkId=517887)de directorios (DirSync) en Microsoft Azure.