---
title: Durante y después del movimiento de datos
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
ms.collection: SPO_Content
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: Los movimientos de datos son una operación back-end con un impacto mínimo en los usuarios finales. No es necesario realizar ninguna acción mientras Microsoft mueve todos los servicios y datos asociados del inquilino a un nuevo centro de datos geográfico. La transferencia y validación de datos se producen en segundo plano de antemano con un impacto mínimo para los usuarios.
ms.openlocfilehash: f98d3a9aaef1197b1f424ce8cbd23b3d18b7ef2b
ms.sourcegitcommit: 761dd21a6b7a2650ef26fd8d6b303c04fa2546f2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/01/2020
ms.locfileid: "40923862"
---
# <a name="during-and-after-your-data-move"></a>Durante y después del movimiento de datos

Los movimientos de datos son una operación back-end con un impacto mínimo en los usuarios finales. No es necesario realizar ninguna acción mientras Microsoft mueve todos los servicios y datos asociados del inquilino a un nuevo centro de datos geográfico. La transferencia y validación de datos se producen en segundo plano de antemano con un impacto mínimo para los usuarios.
  
> [!NOTE]
> Los movimientos se producen en diferentes momentos para cada servicio. Como resultado, verá la funcionalidad reducida descrita para cada servicio a una hora distinta. 
  
Vea el centro de mensajes de Office 365 para confirmar que se han completado los movimientos de Exchange Online, SharePoint Online y Skype empresarial. Como se muestra en la tabla siguiente, puede tardar hasta 24 meses, después del final del período de inscripción, completar todos los movimientos de datos solicitados para todos los clientes de una geo específica. Si ve algún problema con el espacio empresarial después de la transferencia, póngase en contacto con el [soporte técnico de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) para obtener ayuda. 
  

|**Clientes con país de suscripción en**|**Todos los movimientos completados por**|
|:-----|:-----|
|Australia, Nueva Zelanda, Fiji  <br/> |1 de julio de 2022  <br/> |
|Japón  <br/> |1 de julio de 2022  <br/> |
|India  <br/> |1 de julio de 2022  <br/> |
|Canadá  <br/> |1 de julio de 2022  <br/> |
|Corea del sur  <br/> |1 de julio de 2022  <br/> |
|Reino Unido  <br/> |1 de julio de 2022  <br/> |
|Francia  <br/> |1 de julio de 2022  <br/> |
|Emiratos Árabes Unidos  <br/> |1 de julio de 2022  <br/> |
|Sudáfrica  <br/> |1 de julio de 2022  <br/> |
|Suiza, Liechtenstein  <br/> |1 de julio de 2022  <br/> |
|Alemania  <br/> |Plane  <br/> |

> [!NOTE]
> Los clientes de los países de Office 365 elegibles pueden optar por la migración de datos del servicio de chat de Microsoft Teams desde el 1 de enero de 2020 hasta el 30 de junio de 2020, que también indicarán la migración de todas las cargas de trabajo elegibles.  Los clientes que hayan optado por la migración anterior a 2020 pueden esperar que Exchange Online y SharePoint Online/OneDrive para la empresa puedan completarse hasta que se complete la fecha límite original, mientras que Microsoft Teams completará el 1 de julio de 2022 para todos los clientes. 

## <a name="exchange-online"></a>Exchange Online

Dado que el tiempo de traslado de cada usuario a la nueva geo de centro de recursos es necesario, algunos usuarios seguirán estando en la geografía del centro de recursos antiguo durante la transferencia, mientras que otros se encontrarán en la nueva geografía del centro de recursos. Esto significa que algunas características que implican el acceso a varios buzones de correo pueden no funcionar completamente durante un período del proceso de traslado, que puede durar semanas. Estas características se describen en las secciones siguientes.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Abrir "carpeta compartida" en Outlook Web Access

Algunos usuarios abren una carpeta de correo compartido desde otro buzón (que el usuario tiene permisos de lectura o escritura) en Outlook Web Access mediante la característica "carpeta compartida". En la tabla siguiente se describe cómo funciona el acceso a las carpetas compartidas durante el movimiento de un buzón. Tenga en cuenta que los usuarios con permisos completos para un buzón de correo compartido pueden abrir el buzón de correo mediante Outlook Web Access durante el traslado. 
  
|**Configuración**|**Descripción**|
|:-----|:-----|
|El usuario tiene permiso de carpeta de buzón de correo en otro buzón  <br/> |Posiblemente limitado.  <br/> Si el usuario A y el buzón B no se encuentran en el mismo área geográfica durante el movimiento de inquilino, el usuario A no puede abrir la carpeta del buzón B en Outlook Web Access si el usuario A solo tiene permiso para una carpeta específica del buzón B.  <br/> Para agregar una carpeta compartida, haga clic con el botón derecho en el nombre de usuario en el panel de navegación izquierdo y seleccione **Agregar carpeta compartida**.  <br/> |
|Usuario con permiso de buzón de correo completo a otro buzón  <br/> |Totalmente compatible.  <br/> Si el usuario A tiene permiso de "acceso total" en el buzón B, el usuario A puede hacer clic en la carpeta compartida en el panel de navegación izquierdo de Outlook Web Access para abrir una ventana que muestre el buzón B.  Un usuario puede abrir un buzón compartido mediante Outlook Web Access durante la transferencia sin ningún impacto negativo. La limitación solo se aplica al uso compartido en el nivel de carpeta en un buzón.           |
  
## <a name="sharepoint-online"></a>SharePoint Online

Cuando se mueve SharePoint Online, también se mueven los datos de los siguientes servicios:
  
- OneDrive para la Empresa
    
- Project Online
    
- Project para Office 365
    
- Servicios de vídeo de Office 365
    
- Explorador de Office en s
    
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
    
- Informes de popularidad y búsqueda para el sitio: los recuentos de informes de Excel en la nueva ubicación solo incluyen recuentos y recuentos de informes de uso que se ejecutaron después de completar el traslado de los datos de SharePoint Online. Los recuentos del período provisional se pierden y no se pueden recuperar. Este período suele ser un par de días. Algunos clientes podrían experimentar pérdidas más cortas o más largas.
    
- Portal de vídeo: los recuentos y las estadísticas del portal de vídeo dependen de las estadísticas de los informes de Excel, por lo que los recuentos y las estadísticas del portal de vídeo se pierden durante el mismo período de tiempo que para los informes de Excel.
    
- eDiscovery: los elementos que se cambiaron durante la migración no se muestran hasta que el rastreo toma los cambios.
    
- Prevención de pérdida de datos (DLP): las directivas no se aplican a los elementos que cambian hasta que el rastreo toma los cambios.

## <a name="microsoft-teams"></a>Microsoft Teams

Los clientes de los países de Office 365 elegibles pueden optar por la migración de datos del servicio de chat de Microsoft Teams a partir del 1 de enero de 2020.  

## <a name="skype-for-business"></a>Skype Empresarial

Todos los usuarios se cerrarán desde el software de cliente de Skype empresarial durante la recorte. El inicio de sesión automático volverá a conectar a los usuarios en dos minutos.
  
|**Características que funcionan durante la transferencia completa**|**Características que pueden estar limitadas durante una parte del movimiento**|
|:-----|:-----|
| Mensajería instantánea y llamadas de voz  <br/>  Los usuarios pueden agregar contactos, agregar grupos de contactos, agregar reuniones, definir su ubicación y cambiar "¿Qué está ocurriendo hoy".  <br/>  La configuración del proveedor de servicios de audioconferencia (ACP) se copia en el área geográfica del centro de servicios de destino. Si el proveedor ACP está presente en el centro de centros de recursos de destino, funcionará. De lo contrario, no lo hará.  <br/> | El administrador de inquilinos TRPS (PowerShell remoto del inquilino) no estará disponible para que los administradores puedan crear sesiones.  <br/>  El CONCENTRADOr de administración de inquilinos no estará disponible para que los administradores inicien sesión y cambie la configuración del usuario.  <br/> |
   
|**Después del movimiento**|
|:-----|
| Los datos de la reunión (presentaciones cargadas, etc.) no se moverán y deberán volver a cargarse.  <br/>  Los clientes más antiguos de Lync, como el cliente de Lync 2010 y el cliente de Lync para Mac 2011, se sabe que almacenan en caché la información de DNS para el servicio que causa problemas de inicio de sesión. Es posible que sea necesario borrar la memoria caché de DNS si el usuario no se encuentra en el último cliente Windows de Skype empresarial. Vea [solución de problemas de configuración de DNS de Skype empresarial online en Office 365](https://docs.microsoft.com/skypeforbusiness/troubleshoot/online-configuration/dns-configuration-issue). Los usuarios del cliente de Lync para Mac deben seguir [estas instrucciones](https://support.microsoft.com/kb/2629861).  <br/> |
   
### <a name="skype-for-business-moves-that-involve-a-third-party-audio-conferencing-provider"></a>Movimientos de Skype empresarial que implican a un proveedor de servicios de audioconferencia de terceros
Los servicios complementarios de proveedores de servicios de audioconferencia de terceros para Skype empresarial no están disponibles para los usuarios hospedados en nuevos centros de datos geográficamente específicos.  Los clientes existentes que usen un servicio de proveedor de servicios de audioconferencia de terceros no deben solicitar el traslado a un nuevo centro de datos específico de forma geográfica.  Los clientes nuevos que se implementen en los nuevos centros de datos geográficamente específicos deberán solicitar un traslado a un centro de datos regional para usar un proveedor de servicios de audioconferencia de terceros.
  
## <a name="related-topics"></a>Temas relacionados 
 
[Cómo solicitar el movimiento de datos](request-your-data-move.md)
    
[Preguntas más frecuentes sobre el movimiento de datos](data-move-faq.md)
  
[Nueva GEOS de centro de recursos para Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Servicios de Azure por región](https://azure.microsoft.com/regions/)

