---
title: 'Diagrama accesible: Integración de características en productos de servidores de Microsoft Office'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: d78983fa-0951-49b8-b890-d76a44c70035
description: 'Este artículo es una versión de texto accesible del diagrama Integración de características en los productos de Microsoft Office Server: SharePoint Server, Exchange Server, Lync Server y Office Online.'
ms.openlocfilehash: 809a9272d7088ac069aad6b64daedfe059188247
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487816"
---
# <a name="accessible-diagram---feature-integration-across-microsoft-office-server-products"></a>Diagrama accesible: Integración de características en productos de servidores de Microsoft Office

**Resumen:** Este artículo es una versión de texto accesible del diagrama con el nombre integración de características en los productos de Microsoft Office Server-SharePoint Server, Exchange Server, Lync Server y Office online.
  
El diagrama consta de varias pestañas, como se indica en los títulos de sección de este documento.
  
## <a name="introduction-tab"></a>Ficha Introducción

### <a name="illustrations-for-cross-server-features"></a>Ilustraciones de características entre servidores

Este archivo de Visio (o archivo PDF de varias páginas) presenta nueve fichas, cada una de ellas con información y un diagrama sobre una característica que funciona en todos los productos de Office Server.
  
Estas son las características y las fichas:  
  
- Introducción
    
- Autenticación de servidor en servidor 
    
- Fotos de usuarios en alta resolución 
    
- Almacén de contactos unificado 
    
- Buzones del sitio 
    
- Sincronización de tareas de Exchange 
    
- Presencia de Lync en Outlook Web App 
    
- Correo de voz
    
- Grabaciones de reuniones 
    
Envíe sus comentarios sobre esta solución o solicite otras soluciones a MODAContent@microsoft.com.  
  
### <a name="tips-for-printing"></a>Consejos para la impresión

El tamaño de página de cada ficha es 22 x 17 pulgadas (aproximadamente un cuarto del tamaño de un diagrama de ingeniería ANSI). Puede imprimir esta página en dos hojas de tamaño tabloide (17 x 11 pulgadas) o cuatro hojas de tamaño carta (11 x 8,5 pulgadas). Si dispone de un trazador, puede imprimir estos pósteres a tamaño completo. Si no tiene un trazador, siga estos pasos para imprimir en un papel de tamaño más reducido.  
  
 **Impresión de pósteres en papel de tamaño reducido**
  
1. Abra el póster en Visio. 
    
2. En el menú **Archivo**, haga clic en **Configurar página**. 
    
3. En la ficha **Configurar impresión**, en la sección **Papel de la impresora**, seleccione el tamaño del papel en el que desee imprimir.
    
4. En la ficha **Configurar impresión**, en la sección **Zoom para imprimir**, haga clic en **Ajustar a** y, a continuación, escriba **1 hoja a lo ancho por 1 hoja a lo largo**. 
    
5. En la ficha **Tamaño de página**, haga clic en **Ajustar al contenido del dibujo** y, a continuación, haga clic en **Aceptar**. 
    
6. En el menú **Archivo**, haga clic en **Imprimir**. 
    
### <a name="microsoft-tags-and-qr-codes"></a>Etiquetas de Microsoft y códigos QR

Use su Windows Phone o descargue un lector de códigos QR para obtener más información sobre cómo implementar estas características.  
  
### <a name="cross-server-features"></a>Características de varios servidores

En una tabla se muestran las características y los productos Office Server que las usan. Estas son las características:  
  
Autenticación de servidor a servidor. Esta característica se aplica a:  
  
- SharePoint 
    
- Exchange
    
- 2015
    
- Office Online (anteriormente conocido como Office Web Apps)  
    
Fotos de usuarios en alta resolución. Esta característica se aplica a:  
  
- SharePoint
    
- Exchange
    
- 2015
    
Almacén de contactos unificado. Esta característica se aplica a:  
  
- Exchange
    
- 2015
    
Buzones de sitio. Esta característica se aplica a:  
  
- SharePoint
    
- Exchange
    
Sincronización de tareas de Exchange. Esta característica se aplica a:  
  
- SharePoint
    
- Exchange
    
Presencia de Lync en Outlook Web App. Esta característica se aplica a:  
  
- 2015
    
Correo de voz. Esta característica se aplica a:  
  
- 2015
    
Grabaciones de reuniones. Esta característica se aplica a:  
  
- SharePoint
    
- 2015
    
### <a name="office-web-apps-server"></a>Servidor Office Web Apps

Office Web Apps Server es un producto de Office Server que proporciona servicios de visualización y edición de archivos basados en el explorador para archivos de Office. Office Web Apps Server funciona con productos y servicios que admiten el protocolo de la Interfaz de plataforma abierta de aplicaciones web (WOPI). Estos productos, conocidos como hosts, incluyen SharePoint 2013, Lync Server 2013 y Exchange Server 2013.   
  
Para obtener más información sobre Office Web Apps Server, descargue el póster simplificado de la implementación http://aka.ms/OfficeWebAppsPosterde Office Web Apps en. 
  
## <a name="server-to-server-authentication-tab"></a>Ficha Autenticación de servidor a servidor

### <a name="servicing-resource-requests-between-servers"></a>Atender solicitudes de recursos entre servidores

La autenticación de servidor a servidor es una característica nueva de Exchange Server 2013, Lync Server 2013 y SharePoint Server 2013 que permite a un servidor solicitar los recursos de otro servidor en nombre de un usuario. Esta característica usa el protocolo Open Authorization (OAuth) 2.0 estándar del sector. La autenticación de servidor a servidor permite muchos escenarios nuevos, como la exhibición de documentos electrónicos, las fotos de usuarios en alta resolución y los buzones de correo del sitio.  
  
 **Productos de servidor** 
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="server-to-server-trust-relationships"></a>Relaciones de confianza de servidor a servidor

Para que un servidor atienda una solicitud de recursos entrante, debe confiar en el servidor que realiza la solicitud. Para establecer esta confianza, debe configurar las relaciones de confianza de servidor a servidor.   
  
Una relación de confianza de servidor a servidor es unidireccional. Al configurar un servidor que ejecuta SharePoint 2013 para que confíe en un servidor con Exchange Server 2013, el servidor SharePoint confía en las solicitudes de recursos del servidor Exchange, pero el servidor Exchange no confía en las solicitudes de recursos del servidor SharePoint. Para una integración óptima, debe establecer confianzas bidireccionales.  
  
El diagrama adjunto muestra las relaciones de confianza de servidor a servidor que se establecen como relaciones de confianza bidireccionales. Muestra las relaciones de confianza bidireccionales entre un servidor Exchange, un servidor SharePoint y un servidor Lync. Cada tipo de servidor tiene una relación de confianza bidireccional con los otros dos servidores.  
  
### <a name="configuration"></a>Configuración

Para configurar una confianza de autenticación de servidor a servidor, debe agregar un nuevo emisor de tokens de seguridad de confianza para cada uno de los servidores envíe solicitudes de recursos en nombre de los usuarios. Cada tipo de servidor tiene un extremo de metadatos de notación de objetos JavaScript (JSON) que contiene información de configuración y una parte pública del certificado de firma de token de acceso. Parte de la configuración de una confianza de autenticación de servidor a servidor consiste en especificar el extremo de metadatos JSON del otro servidor.  
  
La tabla siguiente enumera el extremo de metadatos JSON para cada servidor. La tabla muestra:  
  
- Un servidor Exchange con un extremo de metadatos JSON<server name>de https:///Autodiscover/Metadata/JSON/1 
    
- Un servidor Lync con un extremo de metadatos JSON<server name>de https:///Metadata/JSON/1 
    
- Un servidor de SharePoint con un extremo de metadatos<web app name>JSON de https:///_layouts/15/Metadata/JSON/1 
    
### <a name="example-how-server-to-server-authentication-works-for-ediscovery-between-sharepoint-and-exchange"></a>Ejemplo: Funcionamiento de la autenticación de servidor a servidor para la exhibición de documentos electrónicos entre SharePoint y Exchange

En este ejemplo, el servidor de Exchange 2013 se ha configurado para confiar en el servidor que ejecuta SharePoint Server con una confianza de servidor a servidor. Se ha configurado un centro de exhibición de documentos electrónicos en el servidor que ejecuta SharePoint Server para incluir los datos de buzones de correo en el servidor Exchange.  
  
Las solicitudes de recursos en otro servidor adoptan la forma de tokens de acceso que se envían al servicio de servidor web en el servidor de destino.  
  
En el diagrama adjunto se muestra cómo se desplazan las consultas y los tokens de acceso entre los dos servidores.  
  
1. Un administrador de exhibición de documentos electrónicos envía una consulta al servidor que ejecuta SharePoint Server, que incluye recursos de un servidor Exchange.  
    
2. El servidor que ejecuta SharePoint Server genera un token de acceso, que identifica el usuario y el recurso solicitado.  
    
3. El servidor que ejecuta SharePoint Server envía el token de acceso al servidor Exchange.  
    
4. El servidor Exchange valida el token de acceso y envía los resultados de la consulta.  
    
5. El servidor que ejecuta SharePoint Server envía los resultados de la consulta de eDiscovery al equipo del administrador de eDiscovery. 
    
## <a name="high-resolution-user-photos-tab"></a>Ficha Fotos de usuarios en alta resolución

### <a name="larger-profile-picture-used-across-all-office-applications"></a>Imagen de perfil más grande usada en todas las aplicaciones de Office

Use la información de la ficha **Fotos de usuarios en alta resolución** para almacenar fotos de hasta 648 x 648 píxeles en Exchange 2013. Otras aplicaciones cliente tendrán acceso a estas fotos, como Outlook, Outlook Web App, SharePoint 2013, Lync 2013 y clientes de correo electrónico móvil. También se almacena una fotografía de baja resolución en Active Directory.
  
 **Productos de servidor** 
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Lync Server 2013 
    
### <a name="configuration"></a>Configuración

Configurar la autenticación de servidor a servidor: 
  
- Entre Exchange 2013 y SharePoint 2013.  
    
- Entre Exchange 2013 y Lync 2013.  
    
 **En Exchange Server 2013**
  
- Inicie y configure el servicio Detección automática de Exchange de 2013.  
    
- Configure las URL externas para SharePoint. Estas son las URL que SharePoint usa cuando accede a fotos en Exchange.  
    
 **En SharePoint Server 2013**
  
- Instale la API administrada de servicios Web Exchange. Use GacUtil para cargar Microsoft.Exchange.WebServices.dll en la caché global de ensamblados (GAC).   
    
- Use Windows PowerShell para configurar la sincronización de fotos con Exchange.  
    
 **Funcionamiento**
  
- Los usuarios cargan una foto a través de la página Mi cuenta en Outlook Web App (OWA) o mediante la configuración de la cuenta en Outlook 2013.  
    
- Exchange cambia automáticamente el tamaño de la imagen para usarla en AD DS (48 x 48 píxeles) o en otras aplicaciones de Office, incluido OWA y el cliente de Outlook 2013 (96 x 96 píxeles).   
    
Los usuarios pueden cargar imágenes que abarquen entre 48 × 48 y 648 × 648 píxeles. Se cambia el tamaño de las fotos:  
  
- Se usa 64 x 64 para la miniatura de AD.  
    
- Se usa 96 × 96 para Outlook Web Access, Outlook, Lync Web Access y Lync 2013.  
    
- Se usa 648 × 648 para Lync Web Access y Lync 2013.  
    
Para obtener ejemplos de scripts de configuración, vea los artículos del blog de Jens Trier Rasmussen: 
  
- Uso de fotos de alta resolución de Exchange 2013 desde SharePoint Server 2013 (http://aka.ms/Bhr4d2) 
    
- Integración de Exchange 2013 y Lync Server 2013 (http://aka.ms/Pn08dw) 
    
El póster también contiene códigos QR para estos dos artículos del blog.  
  
En el diagrama de acompañamiento se muestra a los usuarios cómo cargar una foto para usarla en todas las aplicaciones de Office.  
  
1. El usuario actualiza la foto en Outlook, SharePoint o Lync. Después, usa la foto actualizada en todas las aplicaciones de Office.   
    
2. El usuario puede actualizar una foto de varias maneras:  
    
3. 
  - Desde un cliente de Outlook u Outlook Web App (OWA) a través del puerto HTTP 443 hacia un servidor de acceso de cliente de Exchange.  
    
  - Desde Mi sitio a través de HTTP o HTTPS hacia un servidor SharePoint. SharePoint almacena en caché el usuario en la base de datos de Mi sitio (Https:443). El servidor SharePoint interactúa con el servidor de acceso de cliente de Exchange mediante las URL externas configuradas en Exchange.  
    
  - Lync 2013 Client, que mantiene una GetConnection con el servidor de Exchange para obtener actualizaciones de fotos (HTTPS Get request-443). 
    
4. El servidor de acceso de cliente de Exchange se conecta al servidor de buzones de Exchange mediante la comunicación interna de Exchange.   
    
5. El servidor de buzones de Exchange usa Exchange 2013 para insertar la fotografía de alta resolución del usuario en AD DS (LDAP:389).  
    
6. La foto se sincroniza desde los Servicios de dominio de Active Directory (AD DS) para el servicio de libreta de direcciones (ABS) de Lync en el servidor de Lync, de modo que los clientes heredados puedan obtener la misma foto (LDAP:389).  
    
7. El cliente heredado de Lync ahora tiene acceso a la foto.  
    
## <a name="unified-contact-store-tab"></a>Ficha Almacén de contactos unificado

### <a name="exchange-2013-is-the-contact-store-for-all-office-applications"></a>Exchange 2013 es el almacén de contactos de todas las aplicaciones de Office

El Almacén de contactos unificado (UCS) es una característica que proporciona una experiencia de contactos uniforme para todos los productos de Microsoft Office. Los usuarios almacenan toda la información de contacto en su buzón de Exchange 2013. Esta información de contacto está disponible de manera global en Lync, Exchange, Outlook y Outlook Web App.   
  
 **Productos de servidor** 
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
 **Configuración**
  
- Configure la autenticación de servidor a servidor entre Exchange Server 2013 y Lync Server 2013. 
    
- En Lync 2013, habilite la directiva del almacén de contactos unificado (está habilitada de manera predeterminada).  
    
Para obtener ejemplos de scripts de configuración, vea el artículo del blog de Jens Trier Rasmussen: 
  
- Integración de Exchange 2013 y Lync Server 2013 (http://aka.ms/Oyg7fh) 
    
 **Cómo funciona** 
  
- Los contactos de Lync para un usuario se migran automáticamente a Exchange 2013 cuando el usuario inicia sesión con Lync de 2013.  
    
- Los usuarios pueden acceder a sus contactos de Lync y administrarlos desde Lync 2013, Outlook 2013 u Outlook Web Access.   
    
Los contactos de un usuario se migran automáticamente al servidor Exchange 2013 cuando el usuario: 
  
1. Tiene asignada una directiva de servicios de usuario que tiene UcsAllowed configurado en **True**. 
    
2. Tiene aprovisionado un buzón de Exchange 2013 y ha iniciado sesión en el buzón al menos una vez. 
    
3. Inicia una sesión en Lync a través de un cliente enriquecido de Lync 2013. 
    
Inicia una sesión en Lync a través de un cliente enriquecido de Lync 2013.  
  
1. Inicia una sesión en su buzón de Exchange 2013 en el servidor de acceso de cliente de Exchange, mediante un cliente de Outlook u Outlook Web App (OWA) a través de HTTPS/443. El servidor de buzones de Exchange usa la comunicación interna de Exchange para comunicarse con el servidor de acceso de cliente de Exchange.  
    
2. Inicia sesión en Lync 2013. El cliente de Lync contacta con el servidor Lync a través de SIP/5061 HTTPS/443.  
    
3. El cliente de Lync indica al servidor Lync que el usuario está habilitado para el almacén de contactos unificado a través de SIP/5061.  
    
4. Lync Server usa el servicio de almacenamiento de Lync para migrar los contactos del usuario a Exchange 2013 en el servidor de acceso de cliente de Exchange. 
    
5. El usuario debe cerrar la sesión e iniciar sesión en Lync 2013 para que se muestren los cambios (no se muestra en el diagrama).  
    
6. Después de la migración, el cliente de Lync usa los servicios Web Exchange (EWS) para leer y mantener los contactos de Lync.  
    
## <a name="site-mailboxes-tab"></a>Ficha Buzones del sitio

### <a name="a-central-filing-cabinet-for-emails-and-documents"></a>Un archivador central para correos electrónicos y documentos

Los buzones del sitio mejoran la colaboración y la productividad de los usuarios, ya que permiten el acceso a documentos almacenados en SharePoint y a mensajes de correo almacenados en Exchange, todo ello a través de la misma interfaz de cliente. 
  
 **Productos de servidor** 
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
 **Configuración**
  
Configuración de SharePoint: 
  
- Configure la sincronización de perfiles de usuario en la granja de SharePoint.  
    
- Configure la aplicación del servicio de administración de aplicaciones en la granja de SharePoint.  
    
- Configure SSL para que la zona predeterminada admita la autenticación de servidor a servidor.  
    
- Instale la API de EWS en los servidores que ejecuten SharePoint 2013.  
    
- Establezca la confianza OAuth y los permisos del servicio en los servidores que ejecuten SharePoint 2013.  
    
Configuración de Exchange:  
  
- Establezca la confianza OAuth y los permisos del servicio en los servidores Exchange.  
    
- Cree una directiva de aprovisionamiento del buzón del sitio. 
    
- Configure un prefijo de nombre del buzón del sitio. 
    
 **Funcionamiento**
  
Un buzón del sitio está compuesto funcionalmente por la pertenencia al sitio de SharePoint 2013 (propietarios y miembros), el almacenamiento compartido mediante un buzón de Exchange 2013 para los mensajes de correo y un sitio de SharePoint 2013 para los documentos, y una interfaz de administración que atiende las necesidades del ciclo de vida y el aprovisionamiento. 
  
En el diagrama adjunto se muestran los usuarios que usan buzones de sitio para acceder a mensajes de correo en Outlook y a documentos almacenados en SharePoint.  
  
1. Los usuarios pueden acceder a documentos del sitio de grupo de SharePoint a través de los buzones de sitio en Outlook 2013 Pro Plus.  
    
2. Los usuarios también pueden leer mensajes de correo en la Bandeja de entrada del buzón de sitio del sitio de grupo de SharePoint.  
    
3. Los mensajes de correo se almacenan en buzones de sitio en servidores Exchange.  
    
4. Los documentos se almacenan en buzones de sitio en servidores SharePoint.  
    
5. Los metadatos del contenido del sitio de SharePoint se sincronizan con Exchange mediante la API de transferencia de estado de representación (REST) a través de HTTPS.  
    
### <a name="provisioning-and-management"></a>Aprovisionamiento y administración

Los buzones de sitio se aprovisionan y se administran a través de SharePoint 2013. Tanto SharePoint como Exchange disponen de características para aprovisionar y administrar.  
  
#### <a name="sharepoint"></a>SharePoint

Un diagrama muestra los componentes de SharePoint que se requieren para aprovisionar el buzón de sitio, incluidos:  
  
- Aplicación de buzón del sitio  
    
- Miembros y propietarios del sitio de grupo  
    
- Directiva de ciclo de vida del sitio de grupo  
    
Para aprovisionar un nuevo buzón del sitio, instale la aplicación de buzón del sitio en su sitio de grupo y acceda a la aplicación al menos una vez.  
  
La pertenencia al sitio de SharePoint determina quién tiene acceso al buzón del sitio.   
  
La retención del buzón del sitio sigue la misma directiva de ciclo de vida que se ha configurado para el sitio de SharePoint al que está asociado.  
  
#### <a name="exchange"></a>Exchange

En el diagrama se muestra la directiva de aprovisionamiento del buzón del sitio. Se trata del componente de Exchange necesario para aprovisionar el buzón del sitio.
  
En el servidor Exchange, puede definir las directivas de aprovisionamiento del buzón del sitio. Estas directivas rigen las características de correo electrónico que se envían al buzón del sitio y que se reciben de él, así como el tamaño del buzón del sitio en el servidor Exchange. También permiten definir un prefijo para las direcciones de correo del buzón del sitio.   
  
Para las implementaciones locales de Exchange, también tendrá que buscar y eliminar buzones del sitio que se hayan marcado para su eliminación a través de la directiva del ciclo de vida de SharePoint.  
  
## <a name="exchange-task-synchronization-tab"></a>Ficha Sincronización de tareas de Exchange

### <a name="synchronizing-tasks-among-sharepoint-server-2013-project-server-2013-and-exchange-server-2013"></a>Sincronizar tareas entre SharePoint Server 2013, Project Server 2013 y Exchange Server 2013

Use la información de la ficha Sincronización de tareas de Exchange para sincronizar tareas en SharePoint Server 2013 y Project Server 2013 con Exchange Server 2013. Los usuarios pueden ver y administrar sus tareas en Outlook 2013 o en Mi sitio.  
  
 **Productos de servidor** 
  
- Exchange Server 2013 
    
- SharePoint Server 2013 
    
- Project Server 2013 (opcional)  
    
 **Requisitos previos**
  
En Exchange 2013:  
  
- Configure la confianza OAuth y el permiso del servicio.  
    
En SharePoint Server 2013:  
  
- Aplicación de servicio de perfiles de usuario. 
    
- Aplicación Servicio de administración del trabajo. 
    
- Búsqueda (necesario para las tareas en SharePoint Server 2013). Configure con rastreos continuos y rastreos incrementales.  
    
- Capa de sockets seguros (SSL) 
    
- Los usuarios ya disponen de Mis sitios.  
    
- Aplicación de servicio de Project (para agregar tareas de Project Server).  
    
- API de servicios Web Exchange en cada servidor front-end web (es un archivo .exe que se descarga por separado y debe instalarse).  
    
En Project Server 2013:  
  
- Cree sitios de Project Web App.  
    
 **Cómo funciona**
  
Cuando se abre o se actualiza la vista Mis tareas en Mis sitios:  
  
- La aplicación Servicio de administración del trabajo se sincroniza entre SharePoint Server y Project Server.   
    
- El trabajo del temporizador de sincronización de Exchange llama a la aplicación Servicio de administración del trabajo para sincronizar las tareas con Exchange Server 2013.  
    
- Se actualiza la página Mis tareas en Mis sitios.  
    
Cuando se ejecuta el trabajo del temporizador de sincronización de Exchange:  
  
- La aplicación Servicio de administración del trabajo se sincroniza entre SharePoint Server, Project Server y Exchange Server.  
    
En el diagrama adjunto se muestra la interacción entre SharePoint Server 2013, Exchange Server 2013, Outlook 2013 y Project Server 2013.  
  
SharePoint Server 2013 ejecuta estos trabajos y aplicaciones:  
  
- Aplicación de servicio de perfiles de usuario. 
    
- Aplicación de servicio de búsqueda. 
    
- Aplicación Servicio de administración del trabajo, que se describe continuación.  
    
- Trabajo del temporizador de sincronización de Exchange, que se describen a continuación.  
    
- SharePoint Server 2013 contiene el usuario mi sitio y otros sitios, y ejecuta varias tareas de usuario. 
    
- SharePoint Server 2013 contiene un índice de búsqueda.  
    
Exchange Server 2013 contiene lo siguiente:  
  
- Base de datos de Exchange con la información de correo electrónico del usuario  
    
- Tareas de sincronización  
    
Outlook 2013 muestra lo siguiente:  
  
- Los usuarios pueden participar para sincronizar sus tareas (este proceso se describe más adelante).  
    
- Los usuarios pueden ver y editar tareas de Outlook.  
    
Project Server 2013 muestra lo siguiente:  
  
- Base de datos de proyecto  
    
- Sitios de Project Web Access con tareas  
    
Aplicación Servicio de administración del trabajo:  
  
- Agrega tareas de las listas de SharePoint y las listas de tareas de Project (no sincroniza tareas con Exchange Server).  
    
- Se sincroniza cuando los usuarios ven Mi sitio.  
    
- Mantiene la lista de usuarios que participan.   
    
- Sincroniza el siguiente lote de usuarios.  
    
El trabajo del temporizador de sincronización de Exchange:  
  
- Determina el siguiente lote de usuarios.  
    
- Garantiza que todos los usuarios están sincronizados constantemente.  
    
- Inicia la llamada a la aplicación Servicio de administración del trabajo para sincronizar las tareas con Exchange Server solo para los usuarios que participan.  
    
Participación 
  
- Los usuarios deben participar para sincronizar sus tareas de Exchange con Mi sitio, o sus tareas de SharePoint Server 2013 y Project Server 2013 con Exchange Server 2013.  
    
## <a name="lync-presence-in-office-2013-outlook-web-app-and-sharepoint-server-tab"></a>Ficha Presencia de Lync en Office 2013, Outlook Web App y SharePoint Server

### <a name="lync-server-as-the-authoritative-source-of-presence-information"></a>Lync Server como fuente relevante de información de presencia

Al usar la información de presencia de Lync, tendrá una vista uniforme de la información de presencia en Lync, Outlook y SharePoint. Outlook consulte la información de presencia directamente a Lync, que está instalado localmente en el mismo equipo que Outlook. Cuando los usuarios visualizan la información de presencia en SharePoint Server, Lync consulta la información de presencia en el equipo local.
  
Productos de cliente:  
  
- Outlook 2013 
    
- Lync 2013 
    
Productos de servidor:  
  
- Exchange Server 2013 
    
- Lync Server 2013 
    
- SharePoint Server 2013 
    
 **Cómo funciona** 
  
Mientras Lync 2013 esté instalado en el equipo local del usuario, Outlook y SharePoint Server mostrarán automáticamente la información de presencia de los usuarios.  
  
Para los usuarios de Outlook Web App, el servidor de acceso cliente (CAS) de Exchange consulta la presencia en nombre del usuario.  
  
 **Hay dos diagramas adjuntos**
  
El primero muestra el procedimiento por el que un usuario inicia sesión en Outlook Web App y, después, Exchange solicita Lync Server la información de presencia.  
  
1. El usuario inicia sesión en Outlook Web App. El equipo cliente accede al servidor de acceso de cliente de Exchange a través de HTTPS/443 y también llama al servidor de buzones de Exchange con una comunicación interna de Exchange.  
    
2. El usuario inicia sesión en su buzón de Exchange 2013 y el servidor de acceso de cliente de Exchange consulta a Lync Server para obtener información de presencia a través de SIP/MTLS:5061.  
    
Para obtener más información, consulte [integración de Microsoft Lync Server 2013 y Microsoft Outlook Web App 2013](https://go.microsoft.com/fwlink/?LinkId=313522).
  
En el segundo diagrama se muestra cómo Outlook y SharePoint Server usan Lync 2013 para mostrar información de presencia de los usuarios.  
  
1. El usuario inicia sesión en Lync 2013 a través de SIP/TLS:5061, que llama al servidor Lync.   
    
2. A. El usuario inicia sesión en su buzón de Exchange 2013 a través de Outlook en Office 2013. El equipo cliente accede al servidor de acceso de cliente de Exchange a través de HTTPS/443 y también llama al servidor de buzones de Exchange con una comunicación interna de Exchange.  
    
3. A. Outlook llama a Lync instalado en el mismo equipo que Outlook para recuperar la información de presencia.  
    
4. B. El usuario se conecta a Mi sitio de SharePoint a través de HTTP o HTTPS, y este llama al servidor SharePoint.  
    
5. B. Internet Explorer llama a Lync, que está instalado en el mismo equipo que el explorador, para recuperar la información de presencia.  
    
## <a name="voicemail-tab"></a>Ficha Correo de voz

### <a name="exchange-um-is-the-voicemail-system-for-lync-server"></a>Mensajería unificada de Exchange: el sistema de correo de voz para Lync Server

El correo de voz permite a una persona que realiza una llamada dejar un mensaje de voz para cualquier usuario de Lync mediante Mensajería unificada de Exchange.   
  
Productos de cliente: 
  
- Lync 2013 
    
- Dispositivo PSTN (PBX, móvil, POTS)  
    
Productos de servidor: 
  
- Exchange Server 2013 
    
- Exchange Server 2013 
    
 **Cómo funciona** 
  
Cuando el destinatario de la llamada no responde a una llamada en ninguno de los puntos de conexión activos del destinatario de la llamada, Lync Server enruta la llamada al correo de voz en la mensajería UNIFICAda de Exchange (por ejemplo, el servidor de buzones de Exchange). 
  
En el diagrama adjunto se muestra el enrutamiento de llamadas en dos escenarios:  
  
- El autor de la llamada inicia una llamada mediante Lync 2013.  
    
- El autor de la llamada inicia una llamada mediante el dispositivo PSTN (PBX, móvil, POTS).  
    
El autor de la llamada inicia una llamada mediante Lync 2013:  
  
1. El autor de la llamada inicia una llamada al destinatario de la llamada mediante Lync 2013. Se inicia la llamada y se envía al servidor Lync.  
    
2. La llamada se enruta al servidor principal de Lync del destinatario de la llamada. 
    
3. Lync Server suena los puntos de conexión activos del destinatario de la llamada en Lync 2013. 
    
4. Cuando no se contesta la llamada, esta se enruta al buzón de voz (Mensajería unificada de Exchange) en el servidor de acceso cliente de Exchange (enrutador de llamada).  
    
El autor de la llamada inicia una llamada mediante Lync 2013:  
  
1. El autor de la llamada B marca el número de teléfono del destinatario de la llamada con RTC. 
    
2. La llamada de PSTN se enruta desde la puerta de enlace IP hacia el servidor de mediación, que es un servidor Lync.  
    
3. El servidor de mediación enrutar la llamada al servidor principal de Lync del destinatario de la llamada. 
    
4. Lync Server suena los puntos de conexión activos del destinatario de la llamada en Lync 2013. 
    
5. Cuando no se contesta la llamada, esta se enruta al buzón de voz (Mensajería unificada de Exchange) en el servidor de acceso cliente de Exchange (enrutador de llamada).  
    
## <a name="meeting-recordings-tab"></a>Ficha Grabaciones de reuniones

### <a name="publish-your-meeting-recordings-on-your-sharepoint-team-site"></a>Publicar las grabaciones de reuniones en el sitio de grupo de SharePoint

Las grabaciones de reuniones son un componente esencial de las comunicaciones unificadas. Una buena manera de compartir las grabaciones de reuniones consiste en usar bibliotecas de activos de SharePoint en los sitios de grupo para almacenar las grabaciones de reuniones.  
  
Productos de cliente:  
  
- Lync 2013 
    
Productos de servidor:  
  
- Productos de servidor:  
    
- SharePoint 2013 
    
Requisitos previos 
  
- Lync 2013: la grabación de reuniones es una característica del lado cliente en Lync 2013.   
    
- SharePoint 2013: dispone del sitio de grupo, donde puede almacenar las grabaciones de reuniones que ya hay en marcha.  
    
 **¿Qué se graba?**
  
Durante la reunión, se graba lo siguiente en un archivo MP4 (cada punto de la lista va precedido de un icono que representa el tipo de grabación):  
  
- Todo el audio  
    
- Vídeo del orador activo (si se usa) 
    
- Vídeo de panorámica (si se usa)  
    
- Todo el contenido que se presenta  
    
- Mensajería instantánea*   
    
*Solo se incluyen los mensajes instantáneos enviados durante la reunión. No se registran los mensajes de igual a igual enviados entre los participantes de la reunión que no formen parte de la reunión.  
  
El póster incluye dos diagramas para dos escenarios distintos:  
  
- Preparación para la publicación de grabaciones de reuniones  
    
- Grabación y publicación de una reunión con el cliente de Lync  
    
### <a name="preparing-for-publishing-meeting-recordings"></a>Preparación para la publicación de grabaciones de reuniones

En el diagrama se muestra SharePoint Server 2013 con un sitio de grupo, el centro de Administración Central y el servidor de Internet Information Services (IIS).  
  
El sitio de grupo contiene:  
  
- La aplicación Biblioteca de activos.  
    
- Biblioteca de activos de reuniones, a la que los miembros del grupo envían las grabaciones de reuniones.  
    
El centro de Administración Central contiene la configuración general de la aplicación web.  
  
El servidor de IIS contiene la configuración de IIS.  
  
Preparación para publicar grabaciones de reuniones: 
  
1. En el sitio de grupo de SharePoint, agregue la aplicación Biblioteca de activos. Si no puede cargar las grabaciones de las reuniones debido a restricciones de tamaño o tiempos de espera de la conexión, otra posibilidad es que realice los pasos adicionales 2 y 3. 
    
2. En Administración Central de SharePoint, cambie el valor del tamaño máximo de carga para la aplicación web que contiene la colección de sitios de grupo.  
    
3. En la configuración del servidor de IIS, aumente el tiempo de espera de la conexión de IIS para el sitio web que contiene la colección de sitios de grupo.  
    
 **Bibliotecas de activos digitales**
  
Las bibliotecas de activos digitales son bibliotecas de activos que contienen vídeos y, además, tienen ciertas implicaciones de capacidad y rendimiento. Para obtener más información, vea planear bibliotecas de activos digitales en SharePoint Server 2013 http://aka.ms/O1vq5w, que se encuentra en. El póster también incluye un código QR para acceder a esta información. 
  
### <a name="recording-and-publishing-a-meeting-using-the-lync-client"></a>Grabación y publicación de una reunión con el cliente de Lync

En el diagrama se muestra un usuario que usa Lync para unirse a una reunión. La reunión se graba mediante el cliente de Lync, que crea un archivo MP4 con el contenido de la reunión. La grabación en MP4 se guarda en la carpeta de grabaciones de Lync del equipo. Puede mover la grabación MP4 a la biblioteca de activos de reuniones; desde allí podrá insertar la grabación en una página wiki, una página SharePoint o un blog.  
  
 **Para grabar y publicar una reunión mediante el cliente de Lync** 
  
1. Empiece a grabar la reunión con el cliente de Lync.  
    
2. El contenido de la reunión se graba en un archivo MP4 mientras dura la reunión.  
    
3. Una vez finalizada la reunión, la grabación de MP4 aparece en la carpeta Recording de su equipo\\(\\<username>\\C\\: users videos, grabaciones de Lync). Si lo desea, puede personalizar la grabación de la reunión mediante la aplicación Administrador de grabaciones de Lync que se instala con el cliente de Lync. 
    
4. Arrastre y coloque la grabación de la reunión en la biblioteca de activos de SharePoint. 
    
5. Opcional: Una vez que la grabación está en la biblioteca de activos, puede insertarla en cualquier página de SharePoint. Para obtener más información acerca de este paso, vea la entrada del blog de Office 365, crear y publicar vídeos de aprendizaje con SharePoint y http://aka.ms/R61q35Lync Online, que se encuentran en. 
    
 **Miniaturas de vídeo**
  
Las miniaturas de vídeo mejoran el aspecto de la biblioteca de activos. Para obtener más información acerca de la creación de miniaturas para sus grabaciones de reuniones, consulte capturar o cambiar una http://aka.ms/Kupj85miniatura de vídeo, que se encuentra en. El póster también incluye un código QR para acceder a esta información. 
  

