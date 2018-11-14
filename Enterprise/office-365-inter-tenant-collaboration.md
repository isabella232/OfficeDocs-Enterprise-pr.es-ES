---
title: Colaboración entre espacios empresariales de Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 11/08/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- MOE150
ms.assetid: eb45fd8b-1d5d-4b0c-9c5a-479dbb176e7d
description: Obtenga información sobre cómo funciona la colaboración de Office 365 a través de los inquilinos y las organizaciones.
ms.openlocfilehash: ec844f78a0ae31469c2ca92c5cb97d965bdb3508
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219890"
---
# <a name="office-365-inter-tenant-collaboration"></a>Colaboración entre espacios empresariales de Office 365

En este artículo se describe varias formas de colaborar entre dos de los inquilinos de Office 365. Está destinado a los administradores de Office 365.
  
Suponga que dos organizaciones, Fabrikam y Contoso, cada uno de ellos tienen un Office 365 para el inquilino de negocio y que desean trabajar juntos en varios proyectos; algunas de las cuales se ejecutan durante un tiempo limitado y algunos de los cuales son continuas. ¿Cómo pueden Fabrikam y Contoso habilitar sus personas y los equipos a colaborar más eficazmente entre los diferentes inquilinos de Office 365 de forma segura? Office 365, junto con la colaboración de Azure Active Directory B2B, proporciona varias opciones. En este artículo se describe varios escenarios claves que pueden tener en cuenta Fabrikam y Contoso.
  
Opciones de colaboración entre inquilinos de Office 365 incluyen el uso de una ubicación central para los archivos y las conversaciones, uso compartido de calendarios, uso de mensajería instantánea, las llamadas de audio y vídeo para la comunicación y proteger el acceso a los recursos y las aplicaciones. Utilice las siguientes tablas para seleccionar las soluciones y obtener más información.
  
## <a name="exchange-online-collaboration-options"></a>Opciones de colaboración en línea de Exchange

|**Finalidad del uso compartido**|**Acción administrativa**|**Información sobre procedimientos**|
|:-----|:-----|:-----|
|Compartir calendarios con otra organización de Office 365  <br/> |Los administradores pueden configurar distintos niveles de acceso al calendario de Exchange Online para permitir que las empresas colaborar con otras empresas y permitir a los usuarios compartir las programaciones (información de libre/ocupado) con otros usuarios  <br/> |[Uso compartido en Exchange Online](https://technet.microsoft.com/en-us/library/jj916670%28v=exchg.150%29.aspx) <br/> [Relaciones de organización de Exchange Online](https://technet.microsoft.com/en-us/library/jj916658%28v=exchg.150%29.aspx) <br/> [Crear una relación de organización en Exchange Online](https://technet.microsoft.com/en-us/library/jj916671%28v=exchg.150%29.aspx) <br/> [Modificar y relación de la organización en Exchange Online](https://technet.microsoft.com/en-us/library/jj916659%28v=exchg.150%29.aspx) <br/> [Quitar una relación de organización de Exchange Online](https://technet.microsoft.com/en-us/library/jj916657%28v=exchg.150%29.aspx) <br/> [Compartir calendarios con usuarios externos](https://support.office.com/article/fb00dd4e-2d5f-4e8d-8ff4-94b2cf002bdd) <br/> |
|Controlar cómo los usuarios compartir sus calendarios con las personas de fuera de la organización  <br/> |Los administradores aplicar las directivas de uso compartidas a los buzones de los usuarios para controlar quién puede compartirse con y el nivel de acceso concedido  <br/> |[Uso compartido de las directivas de Exchange Online](https://technet.microsoft.com/en-us/library/jj916673%28v=exchg.150%29.aspx) <br/> [Crear una directiva de uso compartido en Exchange Online](https://technet.microsoft.com/en-us/library/jj916676%28v=exchg.150%29.aspx) <br/> [Aplicar una directiva de uso compartido a buzones de correo en Exchange Online](https://technet.microsoft.com/en-us/library/jj916672%28v=exchg.150%29.aspx) <br/> [Modificar, deshabilitar o quitar una directiva de uso compartido en Exchange Online](https://technet.microsoft.com/en-us/library/jj916674%28v=exchg.150%29.aspx) <br/> |
|Configurar el correo electrónico seguro canales y controlar el flujo de correo con organizaciones asociadas  <br/> |Los administradores crear conectores para aplicar seguridad a los intercambios de correo con una organización asociada o el proveedor de servicios. Los conectores de exigir el cifrado a través de seguridad de la capa de transporte (TLS), así como permitir las restricciones en los nombres de dominio o el correo electrónico de envío de socios de intervalos de direcciones IP.  <br/> |[Empleo de TLS por parte de Exchange Online para proteger las conexiones de correo electrónico en Office 365](https://technet.microsoft.com/en-us/library/mt163898.aspx) <br/> [Configure mail flow using connectors in Office 365](https://technet.microsoft.com/en-us/library/ms.exch.eac.connectorselection%28v=exchg.150%29.aspx) <br/> [Dominios remotos en Exchange Online](https://technet.microsoft.com/en-us/library/jj966211%28v=exchg.150%29.aspx) <br/> [Configure el conector para el flujo de correo seguro con una organización asociada](https://technet.microsoft.com/en-us/library/dn751021%28v=exchg.150%29.aspx) <br/> [Procedimientos recomendados de flujo de correo para Exchange Online y Office 365 (descripción general)](https://technet.microsoft.com/en-us/library/0e6cd9d5-ad3e-418a-8ea9-3bf33332c491%28v=exchg.150%29) <br/> |
   
## <a name="sharepoint-online-and-onedrive-for-business-collaboration-options"></a>SharePoint Online y OneDrive para las opciones de colaboración empresarial

|**Los objetivos de uso compartido**|**Acción administrativa**|**Información sobre procedimientos**|
|:-----|:-----|:-----|
|Compartir documentos y sitios con usuarios externos  <br/> |Los administradores configuran el uso compartido en el inquilino o nivel de colección de sitios para la cuenta de Microsoft autenticados, trabajo o escuela cuenta cuentas autenticadas o de invitado  <br/> |[Administrar el uso compartido externo en su entorno de SharePoint Online](https://support.office.com/en-US/article/Manage-external-sharing-for-your-SharePoint-Online-environment-C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> [Dominios restringidos el uso compartido en Office 365 SharePoint Online y OneDrive para la empresa](https://support.office.com/en-US/article/Restricted-Domains-Sharing-in-Office-365-SharePoint-Online-and-OneDrive-for-Business-5d7589cd-0997-4a00-a2ba-2320ec49c4e9) <br/> [Use SharePoint Online como una solución de extranet de business-to-business (B2B)](https://support.office.com/article/7b087413-165a-4e94-8871-4393e0b9c037) <br/> |
|Seguimiento y controlar el uso compartido externo para los usuarios finales  <br/> |OneDrive para los propietarios de archivos de negocio y SharePoint Online de los usuarios finales configurar sitios y el uso compartido de documentos y establecer notificaciones para realizar un seguimiento de uso compartido  <br/> |[Configurar notificaciones para uso compartido externo para OneDrive para la empresa](https://support.office.com/en-US/article/Configure-notifications-for-external-sharing-for-OneDrive-for-Business-b640c693-f170-4227-b8c1-b0a7e0fa876b) <br/> [Compartir archivos o carpetas de SharePoint en Office 365](https://support.office.com/article/1fe37332-0f9a-4719-970e-d2578da4941c) <br/> |
   
## <a name="skype-for-business-collaboration-options"></a>Skype para las opciones de colaboración empresarial

|**Finalidad del uso compartido**|**Acción administrativa**|**Información sobre procedimientos**|
|:-----|:-----|:-----|
|Skype para profesionales Online - mensajería instantánea, llamadas y la presencia con otro Skype para usuarios profesionales  <br/> |Los administradores pueden habilitar su Skype para los usuarios en línea de negocio para mensajería instantánea, realizar llamadas de audio y vídeo y ver estado de presencia con los usuarios de otra inquilino de Office 365.  <br/> |[Permitir a los usuarios contactar con usuarios externos de Skype Empresarial](https://support.office.com/article/b414873a-0059-4cd5-aea1-e5d0857dbc94) <br/> |
|Skype para profesionales Online - mensajería instantánea, llamadas y la presencia con los usuarios de Skype (consumidor)  <br/> |Los administradores pueden habilitar su Skype para los usuarios en línea de negocio para mensajería instantánea, realizar llamadas y ver estado de presencia con los usuarios de Skype (consumidor).  <br/> |[Permitir Skype para usuarios profesionales agregar contactos de Skype](https://support.office.com/article/08666236-1894-42ae-8846-e49232bbc460) <br/> |
   
## <a name="azure-ad-b2b-collaboration-options"></a>Opciones de colaboración B2B de AD de Azure

|**Finalidad del uso compartido**|**Acción administrativa**|**Información sobre procedimientos**|
|:-----|:-----|:-----|
|Colaboración de Azure AD B2B - uso compartido mediante la adición de usuarios externos a un grupo en el directorio de la organización del contenido  <br/> |Un administrador global para un inquilino de Office 365 puede invitar a personas en otro inquilino de Office 365 para unirse a su directorio, agregar los usuarios externos a un grupo y conceder acceso al contenido, como sitios de SharePoint y bibliotecas para el grupo.  <br/> |[¿Qué es la vista previa de colaboración de Azure AD B2B?](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-what-is-azure-ad-b2b) <br/> [B2B de Azure AD: Nuevas actualizaciones facilitan la colaboración entre empresarial](https://blogs.technet.microsoft.com/enterprisemobility/2017/02/01/azure-ad-b2b-new-updates-make-cross-business-collab-easy/) <br/> [Uso compartido externo de Office 365 y colaboración de Azure Active Directory B2B](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-o365-external-user) <br/> [Colaboración de Azure B2B de Active Directory API y personalización](https://docs.microsoft.com/en-us/azure/active-directory/active-directory-b2b-api) <br/> [Azure AD y mostrar identidad: colaboración de Azure de AD de B2B (Business to Business](https://channel9.msdn.com/Series/Azure-AD-Identity/AzureADB2B) <br/> |
   
## <a name="office-365-collaboration-options"></a>Opciones de colaboración de Office 365

|**Finalidad del uso compartido**|**Acción administrativa**|**Información sobre procedimientos**|
|:-----|:-----|:-----|
|Grupos de Office 365 - correo electrónico, calendario, OneNote y los archivos compartidos en un lugar central  <br/> |Se admiten grupos en Essentials Business, Business Premium, educación y los planes de Enterprise E1, E3 y E5. Las personas de un inquilino de Office 365 pueden crear un grupo e invitar a personas en otro inquilino de Office 365 como usuarios invitados. También se aplica a Dynamics CRM.  <br/> |[Obtenga información acerca de los grupos de Office 365](https://support.office.com/article/b565caa1-5c40-40ef-9915-60fdb2d97fa2) <br/> [Acceso como invitado en grupos de Office 365](https://support.office.com/article/bfc7a840-868f-4fd6-a390-f347bf51aff6) <br/> [Implementar grupos de Office 365](https://technet.microsoft.com/en-us/library/dn896591.aspx) <br/> |
   
## <a name="yammer-collaboration-options"></a>Opciones de colaboración de yammer

|**Finalidad del uso compartido**|**Acción administrativa**|**Información sobre procedimientos**|
|:-----|:-----|:-----|
|Yammer: colaboración a través de un medio sociales de empresa  <br/> |A menos que la capacidad de crear grupos externos está deshabilitada por un administrador de Yammer, los usuarios pueden crear grupos externos para colaborar en Yammer a través de conversaciones, la capacidad de like y siga entradas, compartir archivos y conversaciones en línea.  <br/> |[Crear y administrar grupos externos en Yammer](https://support.office.com/article/9ccd15ce-0efc-4dc1-81bc-4a424ab6f92a) <br/> |
   
## <a name="teams-collaboration-options"></a>Opciones de colaboración de equipos

|**Finalidad del uso compartido**|**Acción administrativa**|**Información sobre procedimientos**|
|:-----|:-----|:-----|
|Colaborar en los equipos con usuarios externos a la organización  <br/> |Un administrador global para el inquilino de Office 365 invitar a necesita habilitar la colaboración externa en los equipos. Los propietarios de los administradores y del equipo global ahora podrán invitar a alguien con una dirección de correo electrónico para colaborar en los equipos.  <br/> Los administradores también pueden administrar y editar a invitados ya están presentes en su inquilino.  <br/> |[Autorizar el acceso de invitado](https://docs.microsoft.com/en-us/microsoftteams/teams-dependencies) <br/> [Activar o desactivar el acceso como invitado en los equipos](https://docs.microsoft.com/en-us/microsoftteams/set-up-guests) <br/> [Uso de PowerShell para controlar el acceso de invitado](https://docs.microsoft.com/en-us/microsoftteams/guest-access-powershell) <br/> [Lista de comprobación de acceso de invitado](https://docs.microsoft.com/en-us/microsoftteams/guest-access-checklist) <br/> [Ver los usuarios de invitado](https://docs.microsoft.com/en-us/microsoftteams/view-guests) <br/> [Editar información de usuario de invitado](https://docs.microsoft.com/en-us/microsoftteams/edit-guests-information) <br/> |
|Los propietarios de equipo pueden invitar a y administrar cómo colaboran invitados dentro de sus equipos.  <br/> |Los propietarios de equipo tienen controles adicionales sobre lo que los invitados pueden hacer dentro de sus equipos.  <br/> |[Agregar invitados](https://support.office.com/en-us/article/teams-and-channels-df38ae23-8f85-46d3-b071-cb11b9de5499?ui=en-US&amp;rs=en-US&amp;ad=US#bkmk_addingguests&amp;ID0EAABAAA=Add_guests) <br/> [Agregar a un invitado a un equipo](https://docs.microsoft.com/en-us/microsoftteams/add-guests) <br/> [Administrar el acceso de invitado en los equipos](https://docs.microsoft.com/en-us/microsoftteams/manage-guests) <br/> [Ver quién está en un equipo o en un canal](https://support.office.com/en-us/article/see-who-s-on-a-team-or-in-a-channel-5c6be9be-9c45-4a0f-a1a0-f332b23cb6b7?ui=en-US&amp;rs=en-US&amp;ad=US) <br/> |
|Pueden ver contenido en los equipos y colaborar con otros miembros invitados de otros inquilinos  <br/> |Ninguno.  <br/> |[La experiencia de acceso de invitado](https://docs.microsoft.com/en-us/microsoftteams/guest-experience) <br/> |

## <a name="power-bi-collaboration-options"></a>Opciones de colaboración de Power BI

|**Finalidad del uso compartido**|**Acción administrativa**|**Información sobre procedimientos**|
|:-----|:-----|:-----|
|Power BI permite a los usuarios externos invitado consumir contenido compartido a ellos a través de vínculos. Esto permite a los usuarios de la organización distribuir contenido de forma segura entre las organizaciones.<br/> | El Administrador de Power BI puede controlar si los usuarios pueden invitar a los usuarios externos para ver contenido dentro de la organización. <br/> |[Distribuir contenido de Power BI para los usuarios externos invitado con Azure AD B2B](https://docs.microsoft.com/en-us/power-bi/service-admin-azure-ad-b2b) <br/> |
 
## <a name="points-to-be-aware-of-about-office-365-inter-tenant-collaboration"></a>Puntos que se deben tener en cuenta acerca de la colaboración entre inquilino de Office 365

### <a name="sharing-of-user-accounts-licenses-subscriptions-and-storage"></a>Uso compartido de almacenamiento, las licencias, las suscripciones y las cuentas de usuario

Cada organización mantiene su propio cuentas de usuario, las identidades, grupos de seguridad, suscripciones, licencias y almacenamiento de información. Personas usan las características de colaboración en Office 365 junto con uso compartido de las directivas y configuración de seguridad para proporcionar acceso a la información necesaria que se mantiene el control de activos de la empresa.
  
- **Cuentas de usuario:** No se pueden compartir las cuentas y las cuentas no se dupliquen en los inquilinos o las particiones en los servicios de directorio de Active Directory local. 
    
- **Licencias &amp; suscripciones:** En Office 365, licencias de planes de licencias (también llamadas SKU o Office 365 planes) ofrecer a los usuarios acceso a los servicios de Office 365 que se definen para esos planes. 
    
- **Almacenamiento:** En los planes de Office 365 de los límites de software para SharePoint Online se administran por separado desde los límites de almacenamiento de buzones de correo. Límites de almacenamiento de buzones de correo se configuran y administran mediante Exchange Online. En ambos escenarios de almacenamiento de información no se puede compartir entre los inquilinos. 
    
### <a name="can-we-share-domain-namespaces-across-office-365-tenants"></a>¿Podemos compartir espacios de nombres de dominio en Office 365 inquilinos?

No. Dominios de personal, por ejemplo, fabrikam.com o tailspintoys.com, sólo pueden ser asociados y se utiliza con un inquilino en el momento. Cada inquilino debe tener su propio espacio de nombres; Espacios de nombres de UPN, SMTP y SIP no se puede compartir en inquilinos.
  
### <a name="what-about-hybrid-components-and-office-365-inter-tenant-collaboration"></a>¿Qué componentes híbrida y la colaboración entre inquilino de Office 365?

Los componentes de híbridos locales, como una organización de Exchange y conectar de Azure AD, no se puede dividir en varios inquilinos.
  

