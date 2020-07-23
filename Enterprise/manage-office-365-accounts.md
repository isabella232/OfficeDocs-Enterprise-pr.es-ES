---
title: Herramientas para administrar cuentas de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: overview
ms.prod: office-online-server
localization_priority: Normal
f1.keywords:
- CSH
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
description: 'Obtenga información sobre qué herramientas usar para administrar los usuarios de Microsoft 365. '
ms.openlocfilehash: 324a95e111812180cefffe98f2d7ec3c64e956b1
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230236"
---
# <a name="tools-to-manage-microsoft-365-accounts"></a>Herramientas para administrar cuentas de Microsoft 365

Puede administrar los usuarios de Microsoft 365 de varias maneras diferentes, según su configuración. Puede administrar usuarios en el [centro de administración de Microsoft 365](https://admin.microsoft.com), Windows PowerShell, en servicios de dominio de Active Directory (AD DS) o en el portal de administración de Azure Active Directory (Azure ad). 

En cuanto compre Microsoft 365, puede usar el centro de administración y Windows PowerShell para administrar cuentas. Al administrar las identidades de nube, todas las personas de la organización tienen un identificador de usuario y una contraseña independientes para Microsoft 365. Si desea integrar con la infraestructura local y tener cuentas de usuario sincronizadas con Microsoft 365, puede usar Azure AD Connect para proporcionar la sincronización de identidades y contraseñas para la funcionalidad de inicio de sesión único.
  
## <a name="plan-for-where-and-how-you-will-manage-your-user-accounts"></a>Planeación de dónde y cómo se va a administrar las cuentas de usuario

Dónde y cómo puede administrar las cuentas de usuario depende del modelo de identidad que desee usar para el 365 de Microsoft. Los dos modelos generales son la autenticación en la nube y la autenticación federada.
  
### <a name="cloud-authentication"></a>Autenticación en la nube

- Autenticación en la nube: cree y administre usuarios en el centro de administración de Microsoft 365. También puede usar Windows PowerShell o Azure AD. 
    
- Sincronización de hash de contraseña (PHS) con inicio de sesión único sin interrupciones: la forma más sencilla de habilitar la autenticación para los objetos de AD DS en Azure AD. Con PHS, se sincronizan los objetos de cuenta de usuario de AD DS con Microsoft 365 y se administran los usuarios de forma local. 
    
- Autenticación de paso a través (PTA) con inicio de sesión único sin problemas: proporciona una validación de contraseña sencilla para los servicios de autenticación de Azure AD mediante un agente de software que se ejecuta en uno o varios servidores locales para validar a los usuarios directamente con AD DS. 
    
### <a name="federated-authentication"></a>Autenticación federada

- Opciones de autenticación federada: principalmente para grandes empresas con requisitos de autenticación más complejos, los objetos de AD DS se sincronizan con Microsoft 365 y las cuentas de usuario se administran de forma local. 
    
- [Proveedores de identidad y autenticación de terceros](about-office-365-identity.md) : los objetos de AD DS se pueden sincronizar con Microsoft 365 y el acceso a recursos de la nube es administrado principalmente por un proveedor de identidades de terceros (IDP). 
    
## <a name="managing-accounts"></a>Administración de cuentas

A la hora de decidir la forma en que su organización va a crear y administrar cuentas, tenga en cuenta los siguientes requisitos:
  
- El software de sincronización de directorios debe instalarse en los servidores del entorno local para conectar las identidades entre Microsoft 365 y AD DS.
    
- Cualquier opción de sincronización de directorios, incluidas las opciones SSO, requiere que los atributos de AD DS cumplan los estándares. Los detalles de los atributos que se usan en el directorio y la forma en que se necesita la limpieza (si los hay) se describen en [preparación para aprovisionar a los usuarios a través de la sincronización de directorios a Microsoft 365](prepare-for-directory-synchronization.md). Consulte [Descargar y ejecutar la herramienta Microsoft 365 ID Fix](install-and-run-idfix.md) para obtener instrucciones sobre cómo usar la corrección del identificador para automatizar la limpieza del directorio. 
    
- Planee cómo va a crear cuentas de Microsoft 365.
    
    En la siguiente tabla se enumeran las diferentes herramientas de administración de cuentas.
    
|**Opción**|**Notas**|
|:-----|:-----|
|Centro de administración  <br/> |[Agregar usuarios individualmente o de forma masiva](https://docs.microsoft.com/microsoft-365/admin/add-users/add-users) <br/>  Proporciona una interfaz web sencilla para agregar y cambiar cuentas de usuario.  <br/>  No se puede usar para cambiar usuarios si la sincronización de directorios está habilitada (se puede establecer la asignación de ubicación y licencia).  <br/>  No se puede usar con las opciones de SSO.  <br/> |
|Windows PowerShell  <br/> |[Administración de Microsoft 365 con Windows PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=698471) <br/>  Permite agregar usuarios a usuarios en masa mediante un script de Windows PowerShell.  <br/>  Se puede usar para asignar una ubicación y licencias a las cuentas, independientemente de cómo se creen las cuentas.  <br/> |
|Importación masiva  <br/> |[Agregar varios usuarios al mismo tiempo](add-several-users-at-the-same-time.md) <br/>  Permite importar un archivo CSV para agregar un grupo de usuarios a Microsoft 365.  <br/>  No se puede usar con las opciones de SSO.  <br/> |
|Azure AD  <br/> |Obtendrá una edición gratuita de Azure AD con su suscripción a Microsoft 365. Puede realizar funciones como el restablecimiento de contraseña de autoservicio para los usuarios de la nube y la personalización de las páginas de inicio de sesión y panel de acceso con la edición gratuita. Para obtener funciones mejoradas, puede actualizar a la edición básica, a Azure AD Premium P1 o a Azure AD Premium P2. Consulte [Azure ad Editions](https://go.microsoft.com/fwlink/p/?LinkId=698465) para obtener la lista de características admitidas.  <br/> |
|Sincronización de directorios  <br/> |[Integración de las identidades locales con Azure AD](https://go.microsoft.com/fwlink/p/?LinkID=624168) <br/>  Para la sincronización de directorios con o sin sincronización de contraseñas, use [Azure ad Connect con configuración rápida](https://go.microsoft.com/fwlink/p/?LinkID=698537).  <br/>  Para varios bosques y opciones de SSO, use la [instalación personalizada de Azure ad Connect](https://go.microsoft.com/fwlink/p/?LinkId=698430).  <br/>  Proporciona la infraestructura necesaria para habilitar el SSO.  <br/>  Necesario para muchos escenarios híbridos:  <br/>  Migración preconfigurada  <br/>  Exchange híbrido  <br/>  Sincroniza los grupos habilitados para correo y la seguridad de AD DS.  <br/> |
   
- Independientemente de cómo pretenda agregar las cuentas de usuario a Microsoft 365, debe administrar varias características de cuenta, como la asignación de licencias, la especificación de la ubicación, etc. Estas características se pueden administrar a largo plazo desde el centro de administración o también se pueden [crear cuentas de usuario con PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=717083).
    
    Si elige agregar y administrar a todos los usuarios a través del centro de administración, deberá especificar la ubicación y asignar licencias al mismo tiempo que crea la cuenta de Microsoft 365. Como resultado, no es necesario realizar mucha planeación.
    
    > [!IMPORTANT]
    > La creación de cuentas en Microsoft 365 sin asignar una licencia (en SharePoint Online, por ejemplo) significa que el propietario de la cuenta puede ver el centro de administración de Microsoft 365, pero no puede tener acceso a ninguno de los servicios de la suscripción de la compañía. Después de asignar una ubicación y la licencia, la cuenta se replica en el servicio o los servicios que asignó. El usuario puede iniciar sesión en su cuenta y usar los servicios que se le asignaron. 
  
## <a name="next-steps"></a>Pasos siguientes

[Integración de Microsoft 365 con entornos locales](office-365-integration.md)
  
## <a name="see-also"></a>Consulta también

[Administrar usuarios y grupos en Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users)
  

