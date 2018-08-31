---
title: Preparación para aprovisionar a los usuarios a través de la sincronización del directorio a Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 8/21/2018
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365p_AddUsersWithDirSync
- O365M_AddUsersWithDirSync
- O365E_HRCSetupAADConnectAboutLM617031
- O365E_AddUsersWithDirSync
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Describe cómo prepararse para abastecer a los usuarios a Office 365 mediante el uso de la sincronización de directorios y los beneficios a largo plazo de utilizar este método.
ms.openlocfilehash: 78636fd3ec7aaaac8fa06ba8a0f2c37d76d1b045
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542966"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Preparación para aprovisionar a los usuarios a través de la sincronización del directorio a Office 365

Aprovisionamiento de los usuarios con la sincronización de Active directory requiere más planeación y preparación que simplemente administrar la cuenta de trabajo o escuela directamente en Office 365. Las tareas de planeación y preparación adicionales necesarios para asegurarse de que su Active Directory local se sincroniza correctamente a Active Directory de Azure. Las ventajas se ha agregado a su organización se incluyen:
  
- Reducción de los programas de administración de la organización
- Opcionalmente, habilitar el escenario de inicio de sesión único
- Automatizar cambios de cuenta en Office 365
    
Para obtener más información acerca de las ventajas del uso de sincronización de directorios, vea la [Guía de sincronización de Active Directory]( https://go.microsoft.com/fwlink/p/?LinkId=525398) y la [identidad de descripción Office 365 y Azure Active Directory](about-office-365-identity.md).
  
Para determinar qué escenario es el mejor para su organización, revise la [comparación de herramientas de integración de Active directory](https://go.microsoft.com/fwlink/p/?LinkId=525320).
  
## <a name="directory-cleanup-tasks"></a>Tareas de limpieza de Active Directory

Antes de empezar a sincronizar el directorio, debe limpiar el directorio.
  
Revise también los [atributos que se sincronizan con Azure Active Directory por Azure Connect de AD](https://go.microsoft.com/fwlink/p/?LinkId=746480).
  
> [!IMPORTANT]
> Si no realiza la limpieza de Active directory antes de sincronizar, puede ser un efecto negativo significativo en el proceso de implementación. Podría tardar días o incluso semanas, vaya a través del ciclo de sincronización de directorios, que identifica los errores y volver a realizar la sincronización. 
  
En el directorio local, complete las siguientes tareas de limpieza:
  
1. Asegúrese de que cada usuario al que se le asignen ofertas de servicio de Office 365 tenga una dirección de correo electrónico válida y única en el atributo **proxyAddresses**. 
    
2. Quite los valores duplicados en el atributo **proxyAddresses**. 
    
3.  Si es posible, asegúrese de que cada usuario que se le asignen las ofertas de servicios de Office 365 tiene un valor válido y único para el atributo **userPrincipalName** en el objeto de **usuario** del usuario. Mejor experiencia de sincronización, asegúrese de que el UPN de directorio activo local coincide con el UPN de la nube. Si un usuario no tiene un valor para el atributo **userPrincipalName** , a continuación, el objeto de **usuario** debe contener un valor único y válido para el atributo **sAMAccountName** . Quitar valores duplicados en el atributo **userPrincipalName** . 
    
4. Para el uso óptimo de la lista global de direcciones (LGD), asegúrese de que la información de los siguientes atributos es correcta:
    
  - givenName 
  - apellido
  - displayName
  - Puesto
  - Departamento
  - Oficina
  - Teléfono de la oficina
  - Teléfono móvil
  - Número de fax
  - Dirección
  - Ciudad
  - Estado o provincia
  - Código postal
  - País o región
    
## <a name="directory-object-and-attribute-preparation"></a>Preparación de atributos y objetos de directorio

Sincronización de directorios es correcta entre su Active directory local y Office 365 requiere que se haya preparado correctamente los atributos de Active directory local. Por ejemplo, debe asegurarse de que no se utilizan caracteres específicos en ciertos atributos que se sincronizan con el entorno de Office 365. Caracteres inesperados después no causan un error de sincronización de Active directory pero podrían devolver una advertencia. Caracteres no válidos provocará un error de sincronización de Active directory.
  
También se producirá un error de sincronización de directorios si algunos de los usuarios de Active Directory tienen uno o más atributos duplicados. Cada usuario debe tener atributos únicos.
  
Aquí se enumeran los atributos que necesita para preparar:
  
 **Nota:** También puede usar la [herramienta IdFix](install-and-run-idfix.md) para realizar este proceso mucho más sencillo. 
  
- **displayName**
    
  - Si el atributo existe en el objeto de usuario, se sincronizará con Office 365.
  - Si este atributo existe en el objeto de usuario, debe haber un valor para él. Es decir, el atributo no debe estar en blanco.
  - Número máximo de caracteres: 256
    
- **givenName **
    
  - Si el atributo existe en el objeto de usuario, se sincronizará con Office 365, pero Office 365 no lo necesita ni lo usa.
  - Número máximo de caracteres: 64
    
- **correo**
    
  - El valor del atributo debe ser único dentro del directorio.
    
    > [!NOTE]
    > Si hay valores duplicados, se sincronizará el primer usuario con el valor. Los usuarios siguientes no aparecerán en Office 365. Debe modificar el valor en Office 365, o modificar de los dos valores en el directorio local en el orden de los dos usuarios que aparezca en Office 365. 
  
- **mailNickname** (alias de Exchange) 
    
  - El valor del atributo no puede comenzar con un punto (.).
  - El valor del atributo debe ser único dentro del directorio.
    
- **proxyAddresses **
    
  - Atributo de varios valores
  - Número máximo de caracteres por valor: 256
  - El valor del atributo no debe contener un espacio.
  - El valor del atributo debe ser único dentro del directorio.
  - Caracteres no válidos: \< \> (); , [ ] "
    
    Tenga en cuenta que los caracteres no válidos se aplican a los caracteres que siguen el delimitador de tipo y ":", por ejemplo, que se permite SMTP:User@contso.com, pero SMTP:user:M@contoso.com no lo es.
    
    > [!IMPORTANT]
    > Todas las direcciones de Protocolo Simple de transferencia de correo (SMTP) deben cumplir las normas de mensajería de correo electrónico. Si existen direcciones duplicadas o no deseadas, vea el tema de ayuda para [Quitar duplicado y no deseado proxy direcciones en Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Número máximo de caracteres: 20
  - El valor del atributo debe ser único dentro del directorio.
  - ¿Caracteres no válidos: [\ "|, /: \< \> + =;? \* ]
  - Si un usuario tiene un atributo **sAMAccountName** no válido, pero tiene un atributo **userPrincipalName** válido, se crea la cuenta del usuario en Office 365. 
  - Si los **atributos sAMAccountName** y **userPrincipalName** no son válidos, se debe actualizar el atributo **userPrincipalName** de Active Directory de local. 
    
- **sn** (apellido) 
    
  - Si el atributo existe en el objeto de usuario, se sincronizará con Office 365, pero Office 365 no lo necesita ni lo usa.
    
- **targetAddress**
    
    Es necesario que el atributo **targetAddress** (por ejemplo, SMTP:tom@contoso.com) que se rellena para el usuario debe aparecer en la lista global de direcciones de Office 365. En escenarios de migración de mensajería de terceros, esto requeriría la ampliación del esquema de Office 365 para el directorio local. La extensión de esquema de Office 365 puede agregar también otros atributos útiles para administrar los objetos de Office 365 que se rellenan mediante una herramienta de sincronización de Active directory desde el directorio local. Por ejemplo, se debe agregar el atributo **msExchHideFromAddressLists** para administrar buzones ocultos o grupos de distribución. 
   
  - Número máximo de caracteres: 256
  - El valor del atributo no debe contener un espacio.
  - El valor del atributo debe ser único dentro del directorio.
  - Caracteres no válidos: \ \< \> (); , [ ] "
  - Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir las normas de mensajería de correo.
    
- **userPrincipalName**
    
  - El atributo **userPrincipalName** debe estar en el inicio de sesión de formato de estilo Internet donde el nombre de usuario está seguido del signo de arroba (@) y un nombre de dominio: por ejemplo, user@contoso.com. Todas las direcciones de Protocolo Simple de transferencia de correo (SMTP) deben cumplir las normas de mensajería de correo electrónico.
  - El número máximo de caracteres para el atributo **userPrincipalName** es 113. Se permite un número de caracteres específico antes y después del signo arroba (@), como se muestra aquí: 
  - Número máximo de caracteres del nombre de usuario situado delante del signo (@): 64
  - Número máximo de caracteres para el nombre de dominio después de la arroba (@): 48
  - ¿Caracteres no válidos: \ % &amp; \* + / =? { } | \< \> ( ) ; : , [ ] "
  - Diéresis también es un carácter no válido.
  - El carácter @ es necesario en cada valor **userPrincipalName** . 
  - El carácter @ no puede ser el primer carácter de cada valor **userPrincipalName**. 
  - El nombre de usuario no puede terminar con un punto (.), un signo de y comercial (&amp;), un espacio o un signo de arroba (@).
  - El nombre de usuario no puede tener espacios.
  - Deben usarse dominios enrutables; Por ejemplo, no pueden usarse dominios locales o internos.
  - Unicode se convierte a guiones bajos.
  - **userPrincipalName** no puede contener valores duplicados en el directorio. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Preparar el atributo userPrincipalName

Active Directory está diseñado para permitir que los usuarios finales de la organización para iniciar sesión en su directorio mediante **userPrincipalName**o **sAMAccountName** . De forma similar, los usuarios finales pueden iniciar sesión Office 365 con el nombre principal de usuario (UPN) de su trabajo o escuela cuenta. Sincronización de Active Directory intenta crear nuevos usuarios en Azure Active Directory mediante el uso de la misma UPN que se encuentra en el directorio local. El UPN es con formato como una dirección de correo electrónico. 

En Office 365, el UPN es el atributo predeterminado que se usa para generar la dirección de correo electrónico. Es fácil obtener **userPrincipalName** (local y en Azure Active Directory) y la dirección de correo electrónico principal en **proxyAddresses** establecida en valores diferentes. Cuando se establecen en valores diferentes, puede haber confusión para los administradores y los usuarios finales. 
  
Es mejor alinear estos atributos para reducir la confusión. Para satisfacer los requisitos de inicio de sesión único con los servicios de federación de Active Directory (AD FS) 2.0, debe asegurarse de que el UPN en Azure Active Directory y su Active Directory local match y usa un espacio de nombres de dominio válido.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Agregar un sufijo UPN alternativo en AD DS

Debe agregar un sufijo UPN alternativo para asociar las credenciales del usuario corporativo con el entorno de Office 365. Un sufijo UPN es la parte de un UPN a la derecha del carácter @. UPN que se usan para el inicio de sesión único pueden contener letras, números, períodos, guiones y caracteres de subrayado, pero no hay otros tipos de caracteres.
  
Para obtener más información sobre cómo agregar un sufijo UPN alternativo a Active Directory, consulte [Prepare para la sincronización de Active directory]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Coincide con el UPN local con Office 365 UPN

Si ya ha configurado la sincronización de directorios, es posible que el UPN del usuario para Office 365 no coincide con el UPN del usuario local que se define en el servicio de directorio local. Esto puede ocurrir cuando un usuario se ha asignado una licencia antes de que el dominio se ha comprobado. Para solucionar este problema, use [PowerShell para corregir UPN duplicado](https://go.microsoft.com/fwlink/p/?LinkId=396730) para actualizar el UPN del usuario para asegurarse de que el UPN de Office 365 coincide con el nombre de usuario corporativo y el dominio. Si está actualizando el UPN en el servicio de directorio local y desea sincronizar con la identidad de Azure Active Directory, debe quitar la licencia del usuario en Office 365 antes de hacer los cambios locales. 
  
Consulte también [cómo preparar un dominio no se puede enrutar (por ejemplo, el dominio local) para la sincronización de Active directory](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Herramientas de integración de Active Directory

Sincronización de directorios es la sincronización de objetos de Active directory (usuarios, grupos y contactos) desde el entorno de Active Directory local a la infraestructura de Active directory de Office 365, Azure Active Directory. Vea [Las herramientas de integración de Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obtener una lista de las herramientas disponibles y su funcionalidad. La herramienta recomendada es [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Para obtener más información acerca de Azure Active Directory Connect, vea [integración de sus identidades local con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).
  
Cuando las cuentas de usuario se sincronizan con el directorio de Office 365 por primera vez, se marcan como no activada. No pueden enviar ni recibir correo electrónico, y no consumen licencias de suscripción. Cuando esté listo para asignar suscripciones a Office 365 a usuarios específicos, debe seleccionar y activar [asignar licencias a los usuarios de Office 365 para la empresa](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
  
También puede usar [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) para asignar licencias. Consulte [How to Use PowerShell para asignar automáticamente licencias a los usuarios de Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) para una solución automatizada.