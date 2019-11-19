---
title: Configurar la sincronización de directorios en Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Obtenga información sobre cómo configurar la sincronización de directorios entre Office 365 y su Active Directory local.
ms.openlocfilehash: a51abf7dcca0a9edc4ecf233ea67fdeb80070a70
ms.sourcegitcommit: 23c8781d1a2b0472612c3a2cb6e5d13edb03e236
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "38702251"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configurar la sincronización de directorios en Office 365

Office 365 usa un inquilino de Azure Active Directory (Azure AD) para almacenar y administrar identidades de autenticación y permisos para obtener acceso a los recursos basados en la nube. 

Si tiene un servicio de dominio de Active Directory (AD DS) local, puede sincronizar las cuentas de usuario, los grupos y los contactos de AD DS con el inquilino de Azure AD de su suscripción a Office 365. Se trata de una identidad híbrida para Office 365. A continuación se muestran sus componentes.

![](./media/about-office-365-identity/hybrid-identity.png)

Azure AD Connect se ejecuta en un servidor local y sincroniza AD DS con el inquilino de Azure AD. Además de la sincronización de directorios, puede especificar estas opciones de autenticación:

- Sincronización de hash de contraseña (PHS)

  Azure AD realiza la autenticación en sí.

- Autenticación de paso a través (PTA)

  Azure AD tiene AD DS realizar la autenticación.

- Autenticación federada

  Azure AD redirige al equipo cliente que solicita la autenticación para ponerse en contacto con otro proveedor de identidades.

Consulte [identidades híbridas](plan-for-directory-synchronization.md) para obtener más información.
  
## <a name="1-review-prerequisites-for-azure-ad-connect"></a>1. Revise los requisitos previos de Azure AD Connect

Obtendrá una suscripción gratuita a Azure AD con su suscripción de Office 365. Al configurar la sincronización de directorios, se instalará Azure AD Connect en uno de los servidores locales.
  
Para Office 365, necesitará:
  
- Compruebe el dominio local. El Asistente de Azure AD Connect le guía a través de esto.
- Obtenga los nombres de usuario y las contraseñas de las cuentas de administrador del inquilino de Office 365 y AD DS.

Para el servidor local en el que instale Azure AD Connect, necesitará:
  
|**Sistema operativo del servidor**|**Otros programas de software**|
|:-----|:-----|
|Windows Server 2012 R2 y posterior | -PowerShell está instalado de forma predeterminada, no se requiere ninguna acción.  <br> -Net 4.5.1 y versiones posteriores se ofrecen a través de Windows Update. Asegúrese de que tiene instaladas las últimas actualizaciones de Windows Server en el panel de control. |
|Windows Server 2008 R2 con Service Pack 1 (SP1) * * o Windows Server 2012 | -La versión más reciente de PowerShell está disponible en Windows Management Framework 4,0. Buscarlo en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.Net 4.5.1 y versiones posteriores están disponibles en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|Windows Server 2008 | -La versión más reciente compatible de PowerShell está disponible en Windows Management Framework 3,0, disponible en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.Net 4.5.1 y versiones posteriores están disponibles en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

Consulte requisitos [previos de Azure Active Directory Connect](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-prerequisites) para obtener información detallada sobre los requisitos de hardware, software, cuentas y permisos, los requisitos de certificados SSL y los límites de objetos para Azure ad Connect.
  
También puede revisar el [historial de versiones](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) de Azure ad Connect para ver lo que se incluye y corregir en cada versión.

## <a name="2-install-azure-ad-connect-and-configure-directory-synchronization"></a>2. instalar Azure AD Connect y configurar la sincronización de directorios

Antes de empezar, asegúrese de que tiene:

- El nombre de usuario y la contraseña de un administrador global de Office 365
- El nombre de usuario y la contraseña de un administrador de dominio de AD DS
- Qué método de autenticación (PHS, PTA, federado)
- Si desea usar [el inicio de sesión único de línea directa (SSO) de Azure ad](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-sso)

Siga estos pasos:

1. Inicie sesión en el [centro de administración de Microsoft 365](https://admin.microsoft.com) https://admin.microsoft.com) ( **y seleccione** \> usuarios **activos** usuarios en el panel de navegación de la izquierda.
2. En la **Página usuarios activos** , elija una **sincronización de directorios** **más** (tres puntos) \> .
  
3. En la página **preparación de Azure Active Directory** , seleccione el vínculo **ir al centro de descargas para obtener la herramienta de Azure ad Connect** para empezar. 
4. Siga los pasos del [mapa de ruta de la instalación de Azure ad Connect y Azure ad Connect Health](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="3-finish-setting-up-domains"></a>3. finalizar la configuración de dominios

Siga los pasos descritos en [crear registros DNS para Office 365 cuando administre sus registros DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) para finalizar la configuración de sus dominios.

## <a name="next-step"></a>Paso siguiente

[Asignar licencias a cuentas de usuario](assign-licenses-to-user-accounts.md).
