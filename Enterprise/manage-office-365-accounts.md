---
title: Herramientas para administrar cuentas de Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 5/3/2018
ms.audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Obtenga información sobre qué herramientas se pueden usar para administrar los usuarios de Office 365, y cómo puede usar depende de cómo administrar las identidades de usuario. '
ms.openlocfilehash: 24a7dd72603b881ea0810d0712900bc78dc34a81
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542711"
---
# <a name="tools-to-manage-office-365-accounts"></a>Herramientas para administrar cuentas de Office 365

Puede administrar los usuarios de Office 365 de varias maneras diferentes, dependiendo de la configuración. Puede administrar los usuarios en el centro de administración de Office 365, Windows PowerShell, el directorio local, o en el portal de administración de Azure Active Directory. Tan pronto como comprar Office 365, el centro de administración y Windows PowerShell pueden usarse para administrar cuentas. Cuando la administración de identidades de nube cada persona en su organización tiene un identificador de usuario independiente y una contraseña para Office 365. Si desea integrar con la infraestructura local y tener las cuentas de usuario sincronizadas con Office 365, puede usar Azure Active Directory Connect para proporcionar una sincronización de identidades y, opcionalmente, proporcionar la sincronización de contraseña o completa funcionalidad de inicio de sesión único.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planeación de dónde y cómo va a administrar las cuentas de usuario

Depende de dónde y cómo puede administrar las cuentas de usuario en el modelo de identidad que desea usar para Office 365. Los dos modelos generales son la autenticación de la nube y autenticación federada.
  
### <a name="cloud-authentication"></a>Autenticación en la nube

- [La autenticación en la nube](about-office-365-identity.md#cloud-authentication) : crear y administrar los usuarios en el centro de administración de Office 365, también puede usar Windows PowerShell o Azure Active Directory para administrar los usuarios. 
    
- [Sincronizar de hash de contraseña con un inicio de sesión único perfecta](about-office-365-identity.md) - la manera más sencilla de habilitar la autenticación para los objetos de Active directory local en Azure AD. Con la sincronización de hash de contraseña (PBS), sincronizar los objetos de cuenta de usuario de Active Directory local con Office 365 y administrar los usuarios locales. 
    
- [Autenticación de paso a través con un inicio de sesión único transparente](about-office-365-identity.md) : proporciona una validación de contraseña simple para servicios de autenticación de Azure AD mediante un agente de software que se ejecuta en uno o más servidores locales para validar a los usuarios directamente con su Active Directory local. 
    
### <a name="federated-authentication"></a>Autenticación federada

- [Opciones de autenticación federada](about-office-365-identity.md#federated-authentication-options) - principalmente para grandes organizaciones con requisitos de autenticación más complejas, local se sincronizan los objetos de Active directory con Office 365 y las cuentas de los usuarios son administrados local. 
    
- [Proveedores de autenticación e identidad de terceros](about-office-365-identity.md) - Active directory objetos es posible que se sincronizan en Office 365 y acceso a los recursos de nube de local se administra principalmente por un proveedor de identidad de terceros (IdP). 
    
## <a name="managing-accounts"></a>Administración de cuentas

Al decidir qué modo va a crear y administrar cuentas de su organización, tenga en cuenta lo siguiente:
  
- El software de sincronización de Active directory debe estar instalado en los servidores dentro de su entorno local para conectar las identidades entre Office 365 y el directorio local.
    
- Cualquier opción de sincronización de Active directory, incluidas las opciones de SSO, requiere los atributos de Active directory local cumple con los estándares. Se describen las características específicas de los atributos que se usan en su directorio y qué limpieza (si hay alguno) es necesario en [Prepare to provision a los usuarios a través de sincronización de directorios para Office 365](prepare-for-directory-synchronization.md). Para obtener instrucciones sobre cómo usar IdFix para automatizar la limpieza de directorios, vea [instalar y ejecutar la herramienta IdFix de Office 365](install-and-run-idfix.md) . 
    
- Planear cómo se van a crear cuentas de Office 365.
    
    En la siguiente tabla se enumera las herramientas de administración de cuenta diferente.
    
|**Opción**|**Notas**|
|:-----|:-----|
|Centro de administración de Office 365  <br/> |[Agregar los usuarios individualmente o de forma masiva a Office 365 - ayuda de administración](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  Proporciona una interfaz web simple para agregar y modificar cuentas de usuario.  <br/>  No se puede usar para cambiar los usuarios si se habilita la sincronización de Active directory (se puede establecer asignación de ubicaciones y licencias).  <br/>  No se puede usar con las opciones de SSO.  <br/> |
|Windows PowerShell  <br/> |[Administrar Office 365 con Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Le permite agregar usuarios en los usuarios de forma masiva mediante una secuencia de comandos de Windows PowerShell.  <br/>  Puede usarse para asignar ubicación ni licencias para las cuentas, independientemente de cómo se crean las cuentas.  <br/> |
|Importación en bloque  <br/> |[Agregar varios usuarios al mismo tiempo a Office 365: ayuda para administradores](add-several-users-at-the-same-time.md) <br/>  Permite importar un archivo CSV para agregar un grupo de usuarios a Office 365.  <br/>  No se puede usar con las opciones de SSO.  <br/> |
|Azure Active Directory  <br/> |Obtenga una edición gratuita de Azure Active Directory con su suscripción de Office 365. Puede realizar funciones como restablecer para los usuarios en la nube y la personalización de las páginas de inicio de sesión y Panel de acceso mediante el uso de la edición gratuita de contraseña self-service. Para obtener funcionalidad mejorada, puede actualizar a la edición básica o la edición premium. Vea [las ediciones de Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698465) para la lista de características compatibles.<br/> |
|Sincronización de directorios  <br/> |[Integración de sus identidades local con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Sincronización de directorios con o sin la sincronización de contraseña, use [Azure conectar de AD con la configuración de express](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br/>  Para varios bosques y las opciones de SSO, use [Conectar de AD de instalación personalizada de Azure](https://go.microsoft.com/fwlink/p/?LinkId=698430).  <br/>  Proporciona la infraestructura necesaria habilitar SSO.  <br/>  Necesario para muchos escenarios híbridos:  <br/>  Migración preconfigurada  <br/>  Exchange híbrido  <br/>  Sincroniza los grupos de seguridad y los habilitados para correo desde el directorio local.  <br/> |
   
- Independientemente de cómo piensa agregar las cuentas de usuario a Office 365, debe administrar varias características de cuenta, como la asignación de licencias, que especifica la ubicación y así sucesivamente. Estas características se pueden administrar a largo plazo desde el centro de administración de Office 365 o también puede [crear cuentas de usuario con PowerShell de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
    Si elige agregar y administrar todos los usuarios a través del centro de administración de Office 365, se especifique la ubicación y asignar licencias al mismo tiempo que la creación de la cuenta de Office 365. Como resultado, es necesario no mucho de planeación.
    
    > [!IMPORTANT]
    > Creación de cuentas en Office 365 sin asignar una licencia (a SharePoint Online, por ejemplo) significa que el propietario de la cuenta, puede ver el pero del portal de Office 365 no puede tener acceso a cualquiera de los servicios dentro de la suscripción de su empresa. Después de asignar una ubicación y la licencia, la cuenta se ha replicado en el servicio o servicios que asignó. El usuario puede iniciar sesión en su cuenta y usar los servicios que les haya asignado. 
  
## <a name="next-steps"></a>Pasos siguientes

[Integración de Office 365 con entornos local](office-365-integration.md)
  
## <a name="see-also"></a>Vea también

[Administrar cuentas de usuario en Office 365](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

