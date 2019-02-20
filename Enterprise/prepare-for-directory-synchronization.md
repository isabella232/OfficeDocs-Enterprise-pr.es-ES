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
ms.collection:
- Ent_O365
- M365-identity-device-management
search.appverid:
- MET150
- MOP150
- MOE150
- MBS150
ms.assetid: 01920974-9e6f-4331-a370-13aea4e82b3e
description: Describe cómo preparar el aprovisionamiento de usuarios a Office 365 mediante la sincronización de directorios y las ventajas a largo plazo del uso de este método.
ms.openlocfilehash: af402950b3681285898d0d87b897d363a693bf98
ms.sourcegitcommit: 1b6ba4043497c27b3a89689766b975f2405e0ec8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2019
ms.locfileid: "30085109"
---
# <a name="prepare-to-provision-users-through-directory-synchronization-to-office-365"></a>Preparación para aprovisionar a los usuarios a través de la sincronización del directorio a Office 365

El aprovisionamiento de usuarios con la sincronización de directorios requiere más planeación y preparación que simplemente administrar la cuenta profesional o educativa directamente en Office 365. Las tareas adicionales de planeación y preparación son necesarias para asegurarse de que la implementación local de Active Directory se sincroniza correctamente con Azure Active Directory. Entre las ventajas agregadas a su organización se incluyen:
  
- Reducción de los programas de administración de la organización
- Habilitar opcionalmente escenario de inicio de sesión único
- Automatizar cambios de cuenta en Office 365
    
Para obtener más información acerca de las ventajas del uso de la sincronización de directorios, vea el [mapa de ruta de sincronización de directorios]( https://go.microsoft.com/fwlink/p/?LinkId=525398) y la identidad de [Office 365 y Azure Active Directory](about-office-365-identity.md).
  
Para determinar qué escenario es el mejor para su organización, revise la [comparación](https://go.microsoft.com/fwlink/p/?LinkId=525320)de las herramientas de integración de directorios.
  
## <a name="directory-cleanup-tasks"></a>Tareas de limpieza de directorios

Antes de empezar a sincronizar el directorio, deberá limpiar su directorio.
  
Revise también los [atributos que Azure ad Connect ha sincronizado con Azure Active Directory](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-sync-attributes-synchronized).
  
> [!IMPORTANT]
> Si no realiza la limpieza del directorio antes de sincronizar, puede haber un efecto negativo significativo en el proceso de implementación. Puede tardar días, o incluso semanas, en pasar por el ciclo de sincronización de directorios, identificar errores y volver a sincronizar. 
  
En el directorio local, complete las siguientes tareas de limpieza:
  
1. Asegúrese de que cada usuario al que se le asignen ofertas de servicio de Office 365 tenga una dirección de correo electrónico válida y única en el atributo **proxyAddresses**. 
    
2. Quite los valores duplicados en el atributo **proxyAddresses**. 
    
3.  Si es posible, asegúrese de que cada uno de los usuarios a los que se asignarán ofertas de servicio de Office 365 tenga un valor único y válido para el atributo **userPrincipalName** en el objeto de **usuario** del usuario. Para una mejor experiencia de sincronización, asegúrese de que el UPN de Active Directory local coincida con el UPN de nube. Si un usuario no tiene un valor para el atributo **userPrincipalName** , el objeto de **usuario** debe contener un valor válido y único para el atributo **samAccountName** . Quite los valores duplicados en el atributo **userPrincipalName** . 
    
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

La correcta sincronización de directorios entre el directorio local y Office 365 requiere que los atributos del directorio local estén preparados correctamente. Por ejemplo, debe asegurarse de que los caracteres específicos no se usan en determinados atributos que se sincronizan con el entorno de Office 365. Los caracteres inEsperados no causan un error en la sincronización de directorios, pero podrían devolver una advertencia. Caracteres no válidos, se producirá un error en la sincronización de directorios.
  
También se producirá un error en la sincronización de directorios si algunos de los usuarios de Active Directory tienen uno o más atributos duplicados. Cada usuario debe tener atributos únicos.
  
A continuación se enumeran los atributos que debe preparar:
  
 **Nota:** También puede usar la [herramienta IdFix](install-and-run-idfix.md) para que este proceso sea mucho más fácil. 
  
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
    > Si hay valores duplicados, se sincroniza el primer usuario con el valor. Los usuarios posteriores no aparecerán en Office 365. Debe modificar el valor de Office 365, o bien modificar ambos valores en el directorio local para que ambos usuarios aparezcan en Office 365. 
  
- **mailNickname** (alias de Exchange) 
    
  - El valor del atributo no puede comenzar con un punto (.).
  - El valor del atributo debe ser único dentro del directorio.
    
- **proxyAddresses **
    
  - Atributo de varios valores
  - Número máximo de caracteres por valor: 256
  - El valor del atributo no debe contener un espacio.
  - El valor del atributo debe ser único dentro del directorio.
  - Caracteres no válidos: \< \> (); , [ ] "
    
    Tenga en cuenta que los caracteres no válidos se aplican a los caracteres que siguen al delimitador de tipo y ":", de modo que SMTP:User@contso.com está permitido, pero SMTP:user:M@contoso.com no lo es.
    
    > [!IMPORTANT]
    > Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir con los estándares de mensajería de correo electrónico. Si hay direcciones duplicadas o no deseadas, consulte el tema [de la ayuda quitar direcciones proxy duplicadas y no deseadas en Exchange](https://go.microsoft.com/fwlink/?LinkId=293860). 
  
- **sAMAccountName**
    
  - Número máximo de caracteres: 20
  - El valor del atributo debe ser único dentro del directorio.
  - Caracteres no válidos: [\ "|, \< \> /: + =;? \* ]
  - Si un usuario tiene un atributo **sAMAccountName** no válido, pero tiene un atributo **userPrincipalName** válido, se crea la cuenta del usuario en Office 365. 
  - Si **samAccountName** y **userPrincipalName** no son válidos, se debe actualizar el atributo **userPrincipalName** local de Active Directory. 
    
- **sn** (apellido) 
    
  - Si el atributo existe en el objeto de usuario, se sincronizará con Office 365, pero Office 365 no lo necesita ni lo usa.
    
- **targetAddress**
    
    Es necesario que el atributo **targetAddress** (por ejemplo, SMTP:Tom@contoso.com) que se rellene para el usuario deba aparecer en la GAL de Office 365. En los escenarios de migración de mensajería de terceros, sería necesaria la extensión de esquema de Office 365 para el directorio local. La extensión de esquema de Office 365 también agregará otros atributos útiles para administrar objetos de Office 365 que se rellenan con una herramienta de sincronización de directorios desde un directorio local. Por ejemplo, se agregaría el atributo **msExchHideFromAddressLists** para administrar los buzones ocultos o los grupos de distribución. 
   
  - Número máximo de caracteres: 256
  - El valor del atributo no debe contener un espacio.
  - El valor del atributo debe ser único dentro del directorio.
  - Caracteres no válidos \< \> : \ (); , [ ] "
  - Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir las normas de mensajería de correo.
    
- **userPrincipalName**
    
  - El atributo **userPrincipalName** debe estar en el formato de inicio de sesión de estilo Internet, donde el nombre de usuario está seguido del signo de arroba (@) y de un nombre de dominio: por ejemplo, user@contoso.com. Todas las direcciones de Protocolo simple de transferencia de correo (SMTP) deben cumplir con los estándares de mensajería de correo electrónico.
  - El número máximo de caracteres para el atributo **userPrincipalName** es 113. Se permite un número de caracteres específico antes y después del signo arroba (@), como se muestra aquí: 
  - Número máximo de caracteres del nombre de usuario situado delante del signo (@): 64
  - Número máximo de caracteres para el nombre de dominio después de la arroba (@): 48
  - Caracteres no válidos: &amp; \* \% +/=? { } | \< \> ( ) ; : , [ ] "
  - Una umlaut también es un carácter no válido.
  - El carácter @ es necesario en cada valor **userPrincipalName** . 
  - El carácter @ no puede ser el primer carácter de cada valor **userPrincipalName**. 
  - El nombre de usuario no puede terminar con un punto (.), un&amp;signo de y comercial (), un espacio o un signo de arroba (@).
  - El nombre de usuario no puede tener espacios.
  - Deben usarse dominios enRutables; por ejemplo, no se pueden usar dominios locales o internos.
  - Unicode se convierte a guiones bajos.
  - **userPrincipalName** no puede contener valores duplicados en el directorio. 
    
## <a name="prepare-the-userprincipalname-attribute"></a>Preparar el atributo userPrincipalName

Active Directory está diseñado para permitir que los usuarios finales de la organización inicien sesión en su directorio mediante **samAccountName** o **userPrincipalName**. De forma similar, los usuarios finales pueden iniciar sesión en Office 365 mediante el nombre principal de usuario (UPN) de su cuenta profesional o educativa. La sincronización de directorios intenta crear nuevos usuarios en Azure Active Directory con el mismo UPN que se encuentra en el directorio local. El UPN tiene el mismo formato que una dirección de correo electrónico. 

En Office 365, el UPN es el atributo predeterminado que se usa para generar la dirección de correo electrónico. Es fácil obtener **userPrincipalName** (local y en Azure Active Directory) y la dirección de correo electrónico principal de **proxyAddresses** establecida en valores diferentes. Cuando se establecen en valores diferentes, puede haber confusión para los administradores y los usuarios finales. 
  
Es mejor alinear estos atributos para reducir la confusión. Para cumplir los requisitos de inicio de sesión único con los servicios de Federación de Active Directory (AD FS) 2,0, debe asegurarse de que los UPN de Azure Active Directory y su implementación local de Active Directory coincidan con un espacio de nombres de dominio válido.
  
## <a name="add-an-alternative-upn-suffix-to-ad-ds"></a>Adición de un sufijo UPN alternativo a AD DS

Es posible que deba agregar un sufijo UPN alternativo para asociar las credenciales corporativas del usuario con el entorno de Office 365. Un sufijo UPN es la parte de un UPN a la derecha del carácter @. Los UPN que se usan para el inicio de sesión único pueden contener letras, números, puntos, guiones y caracteres de subrayado, pero ningún otro tipo de caracteres.
  
Para obtener más información acerca de cómo agregar un sufijo UPN alternativo a Active Directory, consulte [preparar la sincronización de directorios]( https://go.microsoft.com/fwlink/p/?LinkId=525430).
  
## <a name="match-the-on-premises-upn-with-the-office-365-upn"></a>Hacer coincidir el UPN local con el UPN de Office 365

Si ya ha configurado la sincronización de directorios, es posible que el UPN del usuario para Office 365 no concuerda con el UPN local del usuario que se define en el servicio de directorio local. Esto puede ocurrir cuando a un usuario se le asignó una licencia antes de que se comprobó el dominio. Para solucionar esto, use [PowerShell para corregir](https://go.microsoft.com/fwlink/p/?LinkId=396730) el UPN duplicado y actualizar el UPN del usuario para asegurarse de que el UPN de Office 365 coincide con el nombre de usuario corporativo y el dominio. Si actualiza el UPN en el servicio de directorio local y desea que se sincronice con la identidad de Azure Active Directory, debe quitar la licencia del usuario en Office 365 antes de realizar los cambios de forma local. 
  
Consulte también [Cómo preparar un dominio no enrutable (como un dominio. local) para la sincronización de directorios](prepare-a-non-routable-domain-for-directory-synchronization.md).
  
## <a name="directory-integration-tools"></a>Herramientas de integración de directorios

La sincronización de directorios es la sincronización de objetos de directorio (usuarios, grupos y contactos) desde el entorno local de Active Directory a la infraestructura de directorios de Office 365, Azure Active Directory. Consulte [herramientas de integración de directorios](https://go.microsoft.com/fwlink/p/?LinkID=510956) para obtener una lista de las herramientas disponibles y su funcionalidad. La herramienta recomendada es [Microsoft Azure Active Directory Connect](https://go.microsoft.com/fwlink/p/?LinkID=510956). Para obtener más información acerca de Azure Active Directory Connect, consulte [integración de las identidades locales con Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkId=527969).
  
Cuando las cuentas de usuario se sincronizan con el directorio de Office 365 por primera vez, se marcan como no activadas. No pueden enviar ni recibir correo electrónico y no consumen licencias de suscripción. Cuando esté listo para asignar suscripciones de Office 365 a usuarios específicos, debe seleccionarlas y activarlas [asignando licencias a los usuarios de Office 365 para empresas](https://support.office.com/article/997596b5-4173-4627-b915-36abac6786dc).
  
También puede usar [PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=613097) para asignar licencias. Consulte [Cómo usar PowerShell para asignar licencias automáticamente a los usuarios de Office 365](https://go.microsoft.com/fwlink/p?LinkID=329805) para una solución automatizada.