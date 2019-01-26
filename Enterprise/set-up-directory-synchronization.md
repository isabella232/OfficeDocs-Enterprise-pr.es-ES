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
search.appverid:
- MET150
- MOE150
- MED15
- MBS150
- BCS160
ms.assetid: 1b3b5318-6977-42ed-b5c7-96fa74b08846
description: Obtenga información sobre cómo configurar la sincronización de directorios entre su Active Directory local y de Office 365.
ms.openlocfilehash: f2cd29e7a81854bb64f6317aa2b41e674ae22df4
ms.sourcegitcommit: a4546e1f3fe9e8e25a56ed350400d51eb7dd7f83
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "29555446"
---
# <a name="set-up-directory-synchronization-for-office-365"></a>Configuración de la sincronización del directorio para Office 365

Office 365 usa el servicio de administración de identidades de usuario basada en la nube Azure Active Directory para administrar usuarios. También puede integrar su Active Directory local con Azure AD mediante la sincronización de su entorno local con Office 365. Una vez establecida la sincronización puede decidir tener su autenticación de usuario que tienen lugar dentro de Azure AD o dentro de su directorio local.
  
## <a name="office-365-directory-synchronization"></a>Sincronización de directorios de Office 365

Puede utilizar la identidad sincronizada o identidad federada entre la organización local y Office 365. Con identidad sincronizada, administrar los usuarios locales y que se autentiquen mediante Azure AD cuando utilizan la misma contraseña en la nube como local. Este es el escenario más común de sincronización de Active directory. Autenticación de paso a través o identidad federada, le permite administrar los usuarios locales y que se autentiquen mediante su directorio local. Identidad federada requiere una configuración adicional y permite que los usuarios sólo iniciar sesión una vez. Para obtener más información, lea la [identidad de descripción Office 365 y Azure Active Directory](about-office-365-identity.md).
  
## <a name="want-to-upgrade-from-windows-azure-active-directory-sync-dirsync-to-azure-active-directory-connect"></a>¿Desea actualizar de sincronización de Windows Azure Active Directory (DirSync) para conectarse de Azure Active Directory?

Si está utilizando actualmente la sincronización de directorios y desea actualizar, head a través de a [azure.com](https://azure.com) para [obtener instrucciones de actualización](https://go.microsoft.com/fwlink/p/?LinkId=733240).
  
## <a name="prerequisites-for-azure-ad-connect"></a>Conectan los requisitos previos para Azure AD

Obtener una suscripción gratuita a Azure AD con su suscripción de Office 365. Al configurar la sincronización de Active directory, instalará Azure Active Directory Connect en uno de los servidores locales.
  
Para Office 365 necesitará:
  
- Compruebe su dominio local (el procedimiento le guiará a través de esto).
- Tiene permisos de [asignación de roles de administrador en Office 365 para profesionales](https://support.office.com/article/EAC4D046-1AFD-4F1A-85FC-8219C79E1504) para el inquilino de Office 365 y local de Active Directory.

Para el servidor local en el que instala Azure Connect AD necesita el siguiente software:
  
|**Sistema operativo de servidor**|**Otros programas de software**|
|:-----|:-----|
|**Windows Server 2012 R2** | -PowerShell se instala de forma predeterminada, no se requiere ninguna acción.  <br> -Net 4.5.1 y versiones posteriores se ofrecen a través de Windows Update. Asegúrese de que ha instalado las actualizaciones más recientes de Windows Server en el Panel de Control. |
|**Windows Server 2008 R2 con Service Pack 1 (SP1)** o **Windows Server 2012** | -La versión más reciente de PowerShell está disponible en Windows Management Framework 4.0. Busque en el [Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).<br> -.net 4.5.1 y versiones posteriores están disponibles en el [Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |
|**Windows Server 2008** | -La última versión admitida de PowerShell está disponible en Windows Management Framework 3.0, disponible en el [Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996).  <br> -.net 4.5.1 y versiones posteriores están disponibles en el [Centro de descarga de Microsoft](https://go.microsoft.com/fwlink/p/?LinkId=717996). |

> [!NOTE]
> Si se usa la sincronización de directorios de Azure Active Directory, el número máximo de miembros del grupo de distribución que se pueden sincronizar desde su Active Directory local a Active Directory de Azure es 15.000. Para conectar de Azure AD, ese número es de 50.000. 
  
Para revisar más detenidamente el hardware, software, cuenta y requisitos de permisos, requisitos de certificado SSL y límites de objeto para Azure Connect de AD, lea [los requisitos previos para conectarse de Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=716896).
  
También puede revisar el Azure Connect AD [historial de versiones de la versión](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-version-history) para ver qué se incluye y corregido en cada versión.

## <a name="to-set-up-directory-synchronization"></a>Para configurar la sincronización de Active directory

1. Inicie sesión en el centro de administración de Office 365 y elija **usuarios** \> **Usuarios activos** en la navegación de la izquierda.
2. En el centro de administración de Office 365, en la página **usuarios activos** , elija **más** \> **sincronización de Active Directory**.

    ![En el menú más, elija la sincronización de directorios](media/dc6669e5-c01b-471e-9cdf-04f5d44e1c4b.png)
  
3. En la página **preparación de Active Directory** , seleccione el vínculo **Descargar Microsoft Azure Active Directory Connect herramienta** para empezar. Para obtener más información acerca del proceso de instalación de Azure Active Directory Connect, vea [Azure AD conectar y estado de conexión de Azure AD guía básica de instalación](https://docs.microsoft.com/azure/active-directory/hybrid/how-to-connect-install-roadmap).

## <a name="assign-licenses-to-synchronized-users"></a>Asignar licencias a los usuarios sincronizados

Una vez que haya sincronizado a los usuarios de Office 365, que se crean, pero necesita asignar licencias a ellos de forma que puedan utilizar las características de Office 365, como correo. Para obtener instrucciones, vea [asignar licencias a los usuarios de Office 365 para la empresa](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).

## <a name="finish-setting-up-domains"></a>Finalizar la configuración de dominios

Siga los pasos descritos en [crear registros DNS para Office 365 al administrar sus registros DNS](https://support.office.com/article/b0f3fdca-8a80-4e8e-9ef3-61e8a2a9ab23) que se va a finalizar la configuración de los dominios.