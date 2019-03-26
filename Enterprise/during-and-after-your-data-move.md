---
title: Durante y después de mover los datos
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 03/15/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: Los movimientos de datos son una operación back-end con un impacto mínimo en los usuarios finales. No es necesario realizar ninguna acción mientras Microsoft mueve todos los servicios y datos asociados del inquilino a un nuevo centro de datos geográfico. La transferencia y validación de datos se producen en segundo plano de antemano con un impacto mínimo para los usuarios.
ms.openlocfilehash: 7635de71e207ff01b24b8b8df8664e3f57f395cf
ms.sourcegitcommit: 4ef8e113fa20b539de1087422455fc26ff123d55
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "30647998"
---
# <a name="during-and-after-your-data-move"></a>Durante y después de mover los datos

Los movimientos de datos son una operación back-end con un impacto mínimo en los usuarios finales. No es necesario realizar ninguna acción mientras Microsoft mueve todos los servicios y datos asociados del inquilino a un nuevo centro de datos geográfico. La transferencia y validación de datos se producen en segundo plano de antemano con un impacto mínimo para los usuarios.
  
> [!NOTE]
> Los movimientos se producen en diferentes momentos para cada servicio. Como resultado, verá la funcionalidad reducida descrita para cada servicio a una hora distinta. 
  
Vea el centro de mensajes de Office 365 para confirmar que se han completado los movimientos de Exchange Online, SharePoint Online y Skype empresarial. Como se muestra en la tabla siguiente, puede tardar hasta 24 meses, después del final del período de inscripción, completar todos los movimientos de datos solicitados para todos los clientes de una geo específica. Si ve algún problema con el espacio empresarial después de la transferencia, póngase en contacto con el [soporte técnico de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) para obtener ayuda. 
  

|**Clientes con dirección de facturación en**|**Todos los movimientos completados por**|
|:-----|:-----|
|Australia, Nueva Zelanda, Fiji  <br/> |31 de octubre de 2017  <br/> |
|Japón  <br/> |31 de octubre de 2018  <br/> |
|India  <br/> |31 de octubre de 2018  <br/> |
|Canadá  <br/> |30 de junio de 2019  <br/> |
|Corea del sur  <br/> |31 de octubre de 2018  <br/> |
|United Kingdom  <br/> |15 de septiembre de 2019  <br/> |
|Francia  <br/> |15 de septiembre de 2020  <br/> |
|Emiratos Árabes Unidos  <br/> |Anunció  <br/> |
|Sudáfrica  <br/> |Anunció  <br/> |
   
## <a name="exchange-online"></a>Exchange Online

Dado que el tiempo de traslado de cada usuario a la nueva geo de centro de recursos es necesario, algunos usuarios seguirán estando en la geografía del centro de recursos antiguo durante la transferencia, mientras que otros se encontrarán en la nueva geografía del centro de recursos. Esto significa que algunas características que implican el acceso a varios buzones de correo pueden no funcionar completamente durante un período del proceso de traslado, que puede durar semanas. Estas características se describen en las secciones siguientes.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Abrir "carpeta compartida" en Outlook Web Access

Algunos usuarios abren una carpeta de correo compartido desde otro buzón (que el usuario tiene permisos de lectura o escritura) en Outlook Web Access mediante la característica "carpeta compartida". En la tabla siguiente se describe cómo funciona el acceso a las carpetas compartidas durante el movimiento de un buzón. Tenga en cuenta que los usuarios con permisos completos para un buzón de correo compartido pueden abrir el buzón de correo mediante Outlook Web Access durante el traslado. 
  
|**Configuración**|**Descripción**|
|:-----|:-----|
|El usuario tiene permiso de carpeta de buzón de correo en otro buzón  <br/> |Posiblemente limitado.  <br/> Si el usuario A y el buzón B no se encuentran en el mismo área geográfica durante el movimiento de inquilino, el usuario A no puede abrir la carpeta del buzón B en Outlook Web Access si el usuario A solo tiene permiso para una carpeta específica del buzón B.  <br/> Para agregar una carpeta compartida, haga clic con el botón derecho en el nombre de usuario en el panel de navegación izquierdo y seleccione **Agregar carpeta compartida**.  <br/> |
|Usuario con permiso de buzón de correo completo a otro buzón  <br/> |Totalmente compatible.  <br/> Si el usuario A tiene permiso de "acceso total" en el buzón B, el usuario A puede hacer clic en la carpeta compartida en el panel de navegación izquierdo de Outlook Web Access para abrir una ventana que muestre el buzón B.  Un usuario puede abrir un buzón compartido mediante Outlook Web Access durante la transferencia sin ningún impacto negativo. La limitación solo se aplica al uso compartido en el nivel de carpeta en un buzón.           |
   
### <a name="public-folders"></a>Carpetas públicas

Si el buzón de carpeta pública se encuentra temporalmente en un centro de recursos geográfico diferente del usuario que intenta tener acceso a él, es posible que el usuario no pueda obtener acceso al buzón de carpetas públicas. 
  
### <a name="online-archives"></a>Archivos en línea

Mientras el movimiento está en curso, es posible que los usuarios que se conectan a través de Outlook para Mac no puedan conectarse a su buzón de archivo en línea. Se admite el acceso al buzón de archivo para los usuarios que se conectan con Outlook y Outlook Web Access.
  
## <a name="sharepoint-online"></a>SharePoint Online

Cuando se mueve SharePoint Online, también se mueven los datos de los siguientes servicios:
  
- OneDrive para la Empresa
    
- Project Online
    
- Project para Office 365
    
- Servicios de vídeo de Office 365
    
- Office Online
    
- Office 365 ProPlus
    
- Visio Pro para Office 365
    
Una vez que haya terminado de mover los datos de SharePoint Online, es posible que vea algunos de los siguientes efectos.
  
### <a name="office-365-video-services"></a>Servicios de vídeo de Office 365

- El movimiento de datos para el vídeo tarda más tiempo que los movimientos en el resto del contenido de SharePoint Online.
    
- Una vez movido el contenido de SharePoint Online, habrá un período de tiempo en el que no se pueden reproducir los vídeos.
    
- Estamos quitando las copias transcodificadas del centro de recursos anterior y transformarlas de nuevo en el nuevo centro de recursos.
    
### <a name="search"></a>Buscar

En el transcurso del traslado de los datos de SharePoint Online, migramos el índice de búsqueda y la configuración de búsqueda a una nueva ubicación. Hasta que haya **completado** el traslado de los datos de SharePoint Online, seguiremos atendiendo a los usuarios del índice en la ubicación original. En la nueva ubicación, la búsqueda comienza automáticamente el rastreo del contenido después de haber terminado de mover los datos de SharePoint Online. A partir de este punto, traponemos a sus usuarios del índice migrado. Los cambios en el contenido que se produjeron después de la migración no se incluyen en el índice migrado hasta que el rastreo los seleccione. La mayoría de los clientes no aprecian que los resultados sean menos actualizados después de haber terminado de mover los datos de SharePoint Online, pero algunos clientes podrían experimentar una actualización reducida en las primeras 24-48 horas. 
  
Se ven afectadas las siguientes características de búsqueda:
  
- Resultados de la búsqueda y elementos Web de búsqueda: los resultados no incluyen los cambios que se produjeron después de la migración hasta que el rastreo los seleccione. 
    
- Delve: Delve no incluye los cambios que se produjeron después de la migración hasta que los rastreo los seleccione.
    
- Informes de popularidad y búsqueda para el sitio: los reCuentos de informes de Excel en la nueva ubicación solo incluyen recuentos y recuentos de informes de uso que se ejecutaron después de completar el traslado de los datos de SharePoint Online. Los recuentos del período provisional se pierden y no se pueden recuperar. Este período suele ser un par de días. Algunos clientes podrían experimentar pérdidas más cortas o más largas.
    
- Portal de vídeo: los recuentos y las estadísticas del portal de vídeo dependen de las estadísticas de los informes de Excel, por lo que los recuentos y las estadísticas del portal de vídeo se pierden durante el mismo período de tiempo que para los informes de Excel.
    
- eDiscovery: los elementos que se cambiaron durante la migración no se muestran hasta que el rastreo toma los cambios.
    
- Prevención de pérdida de datos (DLP): las directivas no se aplican a los elementos que cambian hasta que el rastreo toma los cambios.
    
## <a name="skype-for-business"></a>Skype Empresarial

Todos los usuarios se cerrarán desde el software de cliente de Skype empresarial durante la recorte. El inicio de sesión automático volverá a conectar a los usuarios en dos minutos.
  
|**Características que funcionan durante la transferencia completa**|**Características que pueden estar limitadas durante una parte del movimiento**|
|:-----|:-----|
| Mensajería instantánea y llamadas de voz  <br/>  Los usuarios pueden agregar contactos, agregar grupos de contactos, agregar reuniones, definir su ubicación y cambiar "¿Qué está ocurriendo hoy".  <br/>  La configuración del proveedor de servicios de audioconferencia (ACP) se copia en el área geográfica del centro de servicios de destino. Si el proveedor ACP está presente en el centro de centros de recursos de destino, funcionará. De lo contrario, no lo hará.  <br/> | El administrador de inquilinos TRPS (PowerShell remoto del inquilino) no estará disponible para que los administradores puedan crear sesiones.  <br/>  El CONCENTRADOr de administración de inquilinos no estará disponible para que los administradores inicien sesión y cambie la configuración del usuario.  <br/> |
   
|**Después del movimiento**|
|:-----|
| Los datos de la reunión (presentaciones cargadas, etc.) no se moverán y deberán volver a cargarse.  <br/>  Los clientes más antiguos de Lync, como el cliente de Lync 2010 y el cliente de Lync para Mac 2011, se sabe que almacenan en caché la información de DNS para el servicio que causa problemas de inicio de sesión. Es posible que sea necesario borrar la memoria caché de DNS si el usuario no se encuentra en el último cliente Windows de Skype empresarial. Pida a los usuarios que ejecuten el Asistente para la [solución de problemas](https://support.microsoft.com/en-us/kb/2541980) y siga las instrucciones sobre cómo borrar la memoria caché del cliente. Los usuarios del cliente de Lync para Mac deben seguir [estas instrucciones](https://support.microsoft.com/en-us/kb/2629861).  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a>Movimientos de Skype empresarial que implican a un proveedor de servicios de audioconferencia de terceros
Los servicios complementarios de proveedores de servicios de audioconferencia de terceros para Skype empresarial no están disponibles para los usuarios hospedados en nuevos centros de datos geográficamente específicos.  Los clientes existentes que usen un servicio de proveedor de servicios de audioconferencia de terceros no deben solicitar el traslado a un nuevo centro de datos específico de forma geográfica.  Los clientes nuevos que se implementen en los nuevos centros de datos geográficamente específicos deberán solicitar un traslado a un centro de datos regional para usar un proveedor de servicios de audioconferencia de terceros.

## <a name="data-for-other-services-including-teams-yammer-and-power-bi"></a>Datos para otros servicios, incluidos Teams, Yammer y Power BI

Solo se mueven los datos de clientes para Exchange Online, SharePoint Online y Skype empresarial. No se mueven datos para otros servicios. No hay ningún cambio ni impacto para usted como cliente o usuario de estos otros servicios. El proceso de traslado no influye en ellos y la ubicación de los datos de sus clientes no sufre cambios.
  
## <a name="related-topics"></a>Temas relacionados 
 
[Cómo solicitar el movimiento de datos](request-your-data-move.md)
    
[Preguntas frecuentes generales sobre movimiento de datos](data-move-faq.md)
  
[Nueva GEOS de centro de recursos para Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Servicios de Azure por región](https://azure.microsoft.com/en-us/regions/)

