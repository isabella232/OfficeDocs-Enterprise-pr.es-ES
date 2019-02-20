---
title: Configuración de la sincronización del directorio para Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
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
ms.openlocfilehash: 5f6e5be2a2137ee183a7d592d9a3e6b086e5be9a
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085269"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configuración de la sincronización del directorio para Office 365

Office 365 usa el servicio de administración de identidades de usuario basado en la nube de Azure Active Directory para administrar usuarios. También puede integrar su Active Directory local con Azure AD mediante la sincronización del entorno local con Office 365. Una vez que haya configurado la sincronización, puede decidir que su autenticación de usuario tenga lugar dentro de Azure AD o en el directorio local.
  
## <a name="office-365-directory-synchronization"></a>Sincronización de directorios de Office 365

Puede usar una identidad sincronizada o una identidad federada entre la organización local y Office 365. Con la identidad sincronizada, los usuarios se administran de forma local y Azure AD los autentica cuando usan la misma contraseña en la nube local. Este es el escenario de sincronización de directorios más común. La autenticación de paso a través o la identidad federada permiten administrar los usuarios de forma local y se autentican mediante el directorio local. La identidad federada requiere una configuración adicional y permite que los usuarios solo inicien sesión una vez. Para obtener más información, lea [understandIng Office 365 Identity y Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>¿Quiere actualizar desde la sincronización (dirSync) de Windows Azure Active Directory a Azure Active Directory Connect?

Si actualmente usa dirSync y desea actualizar, vaya a [Azure.com](https://azure.com) para obtener [instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Requisitos previos para Azure AD Connect

Obtendrá una suscripción gratuita a Azure AD con su suscripción de Office 365. Al configurar la sincronización de directorios, se instalará Azure Active Directory Connect en uno de los servidores locales.
  
Para Office 365 tendrá que:
  
- Compruebe el dominio local (el procedimiento le guiará por el proceso).
- [Asigne roles de administrador en Office 365 para](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) los permisos empresariales para su inquilino de Office 365 y Active Directory local.

Para el servidor local en el que instale Azure AD Connect, necesitará el siguiente software:
  
|**SISTEMA operativo del servidor**|**Otros programas de software**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell está instalado de forma predeterminada, no se requiere ninguna acción.  <br> -Net 4.5.1 y versiones posteriores se ofrecen a través de Windows Update. Asegúrese de que tiene instaladas las últimas actualizaciones de Windows Server en el panel de control. |
|**Windows server 2008 R2 con Service Pack 1 (SP1)** o **Windows Server 2012** | -La versión más reciente de PowerShell está disponible en Windows Management Framework 4,0. Buscarlo en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br> -.Net 4.5.1 y versiones posteriores están disponibles en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | -La versión más reciente compatible de PowerShell está disponible en Windows Management Framework 3,0, disponible en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.Net 4.5.1 y versiones posteriores están disponibles en el [centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

> [!NOTE]
> Si usa la sincronización de directorios de Active Directory de Azure, el número máximo de miembros del grupo de distribución que puede sincronizar desde su implementación local de Active Directory a Azure Active Directory es 15.000. Para Azure AD Connect, ese número es 50.000. 
  
Para revisar más atentamente los requisitos de hardware, software, cuentas y permisos, los requisitos de certificados SSL y los límites de objetos de Azure AD Connect, vea [requisitos previos para Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkId=716896).
  
También puede revisar el [historial de versiones](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) de Azure ad Connect para ver lo que se incluye y corregir en cada versión.

## <a name="to-set-up-directory-synchronization"></a>Para configurar la sincronización de directorios

1. inicie sesión en el centro de administración de Office 365 y elija usuarios **activos** de **usuarios** \> en el panel de navegación izquierdo.
2. en la página **usuarios activos** del centro de administración de Office 365, elija **más** \> **sincronización de directorios**.

    ![En el menú más, elija sincronización de directorios.](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. En la página de **preparación de Active** Directory, seleccione el vínculo Descargar la **herramienta de Microsoft Azure Active Directory Connect** para empezar. Para obtener más información acerca del proceso de instalación de Azure Active Directory Connect, consulte [Azure ad Connect y Azure ad Connect Health Installation Roadmap](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Asignar licencias a usuarios sincronizados

Una vez que haya sincronizado los usuarios con Office 365, se crearán, pero tendrá que asignarles licencias para poder usar las características de Office 365, como el correo. Para obtener instrucciones, consulte [asignar licencias a usuarios en Office 365 para empresas](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Finalizar la configuración de dominios

Siga los pasos descritos en [crear registros DNS para Office 365 cuando administre sus registros DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) para finalizar la configuración de sus dominios.