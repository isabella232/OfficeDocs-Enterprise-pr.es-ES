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
ms.collection:
- Ent_O365
- M365-subscription-management
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: 98ca5b3f-f720-4d8e-91be-fe656548a25a
description: 'Obtenga información sobre qué herramientas usar para administrar los usuarios de Office 365 y cómo lo que puede usar depende de cómo administre las identidades de usuario. '
ms.openlocfilehash: fb98c7103aaadb16ac6f7d459a2595022110bb94
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487076"
---
# <a name="tools-to-manage-office-365-accounts"></a>Herramientas para administrar cuentas de Office 365

Puede administrar usuarios de Office 365 de varias maneras diferentes, según su configuración. Puede administrar los usuarios en el [centro de administración de Microsoft 365](https://admin.microsoft.com), en Windows PowerShell, en el directorio local o en el portal de administración de Azure Active Directory. En cuanto compre Office 365, podrá usar el centro de administración y Windows PowerShell para administrar cuentas. Al administrar las identidades de nube, todas las personas de la organización tienen un identificador de usuario y una contraseña independientes para Office 365. Si desea integrar con la infraestructura local y tener cuentas de usuario sincronizadas con Office 365, puede usar Azure Active Directory Connect para proporcionar sincronización de identidades y, opcionalmente, proporcionar sincronización de contraseña o completa funcionalidad de inicio de sesión único.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planeación de dónde y cómo se va a administrar las cuentas de usuario

Dónde y cómo puede administrar las cuentas de usuario depende del modelo de identidad que desee usar para el Office 365. Los dos modelos generales son la autenticación en la nube y la autenticación federada.
  
### <a name="cloud-authentication"></a>Autenticación en la nube

- [Autenticación](about-office-365-identity.md#cloud-authentication) en la nube: cree y administre usuarios en el centro de administración, también puede usar Windows PowerShell o Azure Active Directory para administrar los usuarios. 
    
- [Sincronización de hash de contraseña con inicio de sesión único sin interrupciones](about-office-365-identity.md) : la forma más sencilla de habilitar la autenticación para los objetos de directorio local en Azure ad. Con la sincronización de hash de contraseña (PHS), se sincronizan los objetos de cuenta de usuario de Active Directory local con Office 365 y se administran los usuarios de forma local. 
    
- [Autenticación de paso a través con el inicio de sesión único sin problemas](about-office-365-identity.md) : proporciona una validación de contraseña sencilla para los servicios de autenticación de Azure ad mediante un agente de software que se ejecuta en uno o varios servidores locales para validar a los usuarios directamente con su Active Directory local. 
    
### <a name="federated-authentication"></a>Autenticación federada

- [Opciones de autenticación federada](about-office-365-identity.md#federated-authentication-options) : principalmente para grandes empresas con requisitos de autenticación más complejos, los objetos de directorio local se sincronizan con Office 365 y las cuentas de usuario se administran de forma local. 
    
- Los objetos del directorio local de [autenticación e identidad de terceros](about-office-365-identity.md) se pueden sincronizar con Office 365 y el acceso a recursos de la nube es administrado principalmente por un proveedor de identidades de terceros (IDP). 
    
## <a name="managing-accounts"></a>Administración de cuentas

A la hora de decidir la forma en que su organización va a crear y administrar cuentas, tenga en cuenta lo siguiente:
  
- El software de sincronización de directorios debe instalarse en los servidores del entorno local para conectar las identidades entre Office 365 y el directorio local.
    
- Cualquier opción de sincronización de directorios, incluidas las opciones SSO, requiere que los atributos de directorio local cumplan los estándares. Los detalles de los atributos que se usan en el directorio y la forma en que se necesita la limpieza (si los hay) se describen en [preparación para aprovisionar a los usuarios a través de la sincronización de directorios a Office 365](prepare-for-directory-synchronization.md). Consulte [instalar y ejecutar la herramienta idfix de Office 365](install-and-run-idfix.md) para obtener instrucciones sobre cómo usar IdFix para automatizar la limpieza de directorios. 
    
- Planee cómo va a crear cuentas de Office 365.
    
    En la siguiente tabla se enumeran las diferentes herramientas de administración de cuentas.
    
|**Opción**|**Notas**|
|:-----|:-----|
|Centro de administración  <br/> |[Agregar usuarios individualmente o de forma masiva a Office 365-ayuda para administradores](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/>  Proporciona una interfaz web sencilla para agregar y cambiar cuentas de usuario.  <br/>  No se puede usar para cambiar usuarios si la sincronización de directorios está habilitada (se puede establecer la asignación de ubicación y licencia).  <br/>  No se puede usar con las opciones de SSO.  <br/> |
|Windows PowerShell  <br/> |[Administración de Office 365 con Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Permite agregar usuarios a usuarios en masa mediante un script de Windows PowerShell.  <br/>  Se puede usar para asignar una ubicación y licencias a las cuentas, independientemente de cómo se creen las cuentas.  <br/> |
|Importación masiva  <br/> |[Agregar varios usuarios al mismo tiempo a Office 365: ayuda para administradores](add-several-users-at-the-same-time.md) <br/>  Permite importar un archivo CSV para agregar un grupo de usuarios a Office 365.  <br/>  No se puede usar con las opciones de SSO.  <br/> |
|Azure Active Directory  <br/> |Obtendrá una edición gratuita de Azure Active Directory con su suscripción a Office 365. Puede realizar funciones como el restablecimiento de contraseña de autoservicio para los usuarios de la nube y la personalización de las páginas de inicio de sesión y panel de acceso con la edición gratuita. Para obtener una funcionalidad mejorada, puede actualizar a la edición básica o a la edición Premium. Vea las [ediciones de Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=698465) para obtener la lista de características admitidas.  <br/> |
|Sincronización de directorios  <br/> |[Integración de las identidades locales con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Para la sincronización de directorios con o sin sincronización de contraseñas, use [Azure ad Connect con configuración rápida](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br/>  Para varios bosques y opciones de SSO, use la [instalación personalizada de Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).  <br/>  Proporciona la infraestructura necesaria para habilitar el SSO.  <br/>  Necesario para muchos escenarios híbridos:  <br/>  Migración preconfigurada  <br/>  Exchange híbrido  <br/>  Sincroniza los grupos habilitados para correo y la seguridad desde el directorio local.  <br/> |
   
- Independientemente de cómo pretenda agregar las cuentas de usuario a Office 365, debe administrar varias características de cuenta, como la asignación de licencias, la especificación de la ubicación, etc. Estas características se pueden administrar a largo plazo desde el centro de administración o también se pueden [crear cuentas de usuario con PowerShell de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
    Si opta por agregar y administrar a todos los usuarios a través del centro de administración, deberá especificar la ubicación y asignar licencias al mismo tiempo que se crea la cuenta de Office 365. Como resultado, no es necesario realizar mucha planeación.
    
    > [!IMPORTANT]
    > La creación de cuentas en Office 365 sin asignar una licencia (en SharePoint Online, por ejemplo) significa que el propietario de la cuenta puede ver el portal de Office 365, pero no puede tener acceso a ninguno de los servicios de la suscripción de la compañía. Después de asignar una ubicación y la licencia, la cuenta se replica en el servicio o los servicios que asignó. El usuario puede iniciar sesión en su cuenta y usar los servicios que se le asignaron. 
  
## <a name="next-steps"></a>Pasos siguientes

[Integración de Office 365 con entornos locales](office-365-integration.md)
  
## <a name="see-also"></a>Vea también

[Administrar cuentas de usuario en Office 365](https://support.office.com/article/3204162b-0b6c-4838-8a11-394b9bfd31de.aspx)
  

