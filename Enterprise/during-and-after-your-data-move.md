---
title: Durante y después del movimiento de datos
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
search.appverid:
- MET150
localization_priority: Normal
ms.assetid: f47e3e09-b1dc-4b80-b6ea-fd6e0933407f
description: Movimientos de datos son una operación de back-end con una repercusión mínima para los usuarios finales. Se requiere ninguna acción mientras Microsoft mueve cada servicio y los datos asociados para el inquilino a un nuevo ubican de centro de datos. Transferencia de datos y la validación se producen en segundo plano de antemano con un impacto mínimo en los usuarios.
ms.openlocfilehash: 0c715e80acbac126626c73a75fac1bbc809367e2
ms.sourcegitcommit: 82219b5f8038ae066405dfb7933c40bd1f598bd0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/14/2018
ms.locfileid: "23975178"
---
# <a name="during-and-after-your-data-move"></a>Durante y después del movimiento de datos

Movimientos de datos son una operación de back-end con una repercusión mínima para los usuarios finales. Se requiere ninguna acción mientras Microsoft mueve cada servicio y los datos asociados para el inquilino a un nuevo ubican de centro de datos. Transferencia de datos y la validación se producen en segundo plano de antemano con un impacto mínimo en los usuarios.
  
> [!NOTE]
> Los movimientos se produzcan en momentos diferentes para cada servicio. Como resultado, verá la funcionalidad reducida descrita para cada servicio a una hora diferente. 
  
Una vez completados los movimientos para cada uno de Exchange Online, SharePoint Online y Skype para la empresa, vea el centro de Office 365 mensaje de confirmación. Tal como se muestra en la tabla siguiente, puede demorar hasta 24 meses después del final del período de inscripción, para completar todos los datos solicitados se mueve para todos los clientes en un ubican específico. Si ve los problemas con el inquilino de tras el traslado, póngase en contacto con el [Soporte técnico de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) para obtener asistencia. 
  

|**Clientes con dirección en de facturación**|**Todos los movimientos completados**|
|:-----|:-----|
|Australia, Nueva Zelanda, Fiyi  <br/> |31 de octubre de 2017  <br/> |
|Japón  <br/> |31 de octubre de 2018  <br/> |
|India  <br/> |31 de octubre de 2018  <br/> |
|Canadá  <br/> |31 de octubre de 2018  <br/> |
|Corea del sur  <br/> |31 de octubre de 2018  <br/> |
|Reino Unido  <br/> |15 de septiembre de 2019  <br/> |
|Francia  <br/> |15 de septiembre de 2020  <br/> |
   
## <a name="moves-that-involve-a-third-party-audio-conferencing-provider"></a>Movimientos que implican a un proveedor de conferencia de Audio de terceros

- Servicios de complemento de proveedor de conferencia de Audio de terceros para Skype para la empresa no están disponibles para los usuarios alojados en los centros de datos específicos de geo nuevo. 
    
- Los clientes existentes con un servicio de proveedor de conferencia de Audio de terceros no deberían solicitar un movimiento a un nuevo centro de datos ubican específicos. 
    
- Nuevos clientes implementados en los centros de datos específicos de geo nuevo, debe solicitar un movimiento a un centro de datos regional para usar un proveedor de conferencia de Audio de terceros. 
    
## <a name="exchange-online"></a>Exchange Online

Debido a que tarda en mover cada usuario a la nueva ubican de centro de datos para un único inquilino, algunos usuarios aún estará en el antiguo ubican de centro de datos durante el traslado, mientras que otros usuarios estará en el nuevo ubican de centro de datos. Esto significa que algunas características que implican el acceso a varios buzones totalmente no funcionarán durante un período del proceso de mover, que puede últimas semanas. Estas características se describen en las secciones siguientes.
  
### <a name="mailbox-move"></a>Movimiento del buzón

Cuando un zonas de centro de datos de buzones de correo individuales movimientos crosses, el contenido de los buzones en primer lugar se traslada previamente para que los datos existentes se copien en el destino ubican sin que ello afecte a los buzones de correo. En el momento de transferencia para el destino ubican, el buzón de correo en el origen ubican está bloqueado para unos minutos. Durante este tiempo, los clientes de correo electrónico no se pueden conectar temporalmente. Los cambios adicionales se copian en el destino geográfico, y, a continuación, el buzón de correo completa el movimiento a la ubican de destino. Se ha producido sin interrupción durante el traslado de flujo de correo.
  
Algunos usuarios es posible que necesite reiniciar el escritorio de Outlook después de mover el buzón de correo, tal como se describe en [el artículo de Knowledge Base 2591913](https://support.microsoft.com/kb/2591913).
  
### <a name="shared-mailbox"></a>Buzón compartido

Un usuario con permiso de "Acceso total" a los buzones compartidos no se ve afectado durante el traslado.
  
### <a name="resource-mailbox"></a>Buzón de recursos

Un usuario que necesita para administrar las configuraciones de buzón de recursos a través de la página de opciones en Outlook Web Access puede seguir hacerlo durante el traslado.
  
Si los buzones de recursos se administran directamente a través de los cmdlets de Exchange, los cmdlets Set-MailboxRegionalConfiguration y Set-MailboxCalendarConfiguration no funcionan si el usuario está ejecutando y el buzón de recursos se encuentran en diferentes zonas.
  
### <a name="calendar-delegation"></a>Delegación de calendario

Información de disponibilidad y uso compartido de calendarios no se ven afectados durante el movimiento del inquilino. El usuario A con permiso de escritura a la carpeta Calendario del buzón de correo B aún puede administrar la carpeta del calendario del buzón de correo B con escritorio de Outlook. Sin embargo, durante el traslado, si el usuario A y B de buzón de correo no están disponibles en el mismo ubican, el usuario A no puede editar calendario del buzón de correo B en Outlook Web Access hasta que ambos se mueven a la ubican de destino.
  
### <a name="open-shared-folder-in-outlook-web-access"></a>Abra "Carpeta compartida" en Outlook Web Access

Algunos usuarios abran una carpeta de correo compartido desde otro buzón (que el usuario tiene de lectura o escritura permisos para) en Outlook Web Access mediante la característica de "Carpeta compartida". En la siguiente tabla se describe cómo mover el acceso a las carpetas compartidas funciona durante un buzón de correo. Tenga en cuenta que los usuarios con permisos completos para un buzón compartido pueden abrir el buzón de correo mediante Outlook Web Access durante el traslado. 
  
|**Configuración**|**Descripción**|
|:-----|:-----|
|El usuario tiene permiso de la carpeta de buzón de correo para otro buzón  <br/> |Potencialmente limitado.  <br/> Si el usuario A y B de buzón de correo no están disponibles en el mismo ubican durante el movimiento del inquilino, el usuario A no puede abrir carpeta de buzón de correo B en Outlook Web Access si un usuario sólo tiene permiso para una carpeta específica en el buzón de correo B.  <br/> Para agregar una carpeta compartida, haga clic en el nombre de usuario en el panel de navegación izquierdo y seleccione **Agregar una carpeta compartida**.  <br/> |
|Usuario con permiso de buzón de correo completo a otro buzón  <br/> |Totalmente compatible.  <br/> Si un usuario tiene permiso de "Acceso total" b de buzón de correo, a continuación, el usuario A puede haga clic en la carpeta compartida en el panel de navegación izquierdo en Outlook Web Access para abrir una ventana que muestra los buzones de correo B.  <br/> > [!NOTE]> Un usuario puede abrir un buzón compartido con Outlook Web Access durante el traslado sin ningún impacto negativo. La limitación solo se aplica a nivel de carpeta compartida en un buzón de correo.           |
   
### <a name="public-folders"></a>Carpetas públicas

Si el buzón de correo de carpetas públicas está temporalmente en un ubican diferente del centro de datos desde el usuario intenta tener acceso a él, el usuario no puede acceder a él. 
  
### <a name="online-archives"></a>Archivos en línea

Mientras el movimiento está en curso, los usuarios se conecta a través de Outlook Web Access no podrán conectarse a su buzón de archivo en línea. Se admite el acceso al buzón de archivo para los usuarios se conecta con Outlook.
  
### <a name="ediscovery-amp-auditing"></a>exhibición de documentos electrónicos &amp; auditoría

La exhibición de documentos electrónicos y auditoría de las características de la seguridad de Office 365 &amp; mueve el inquilino de entre ubican de soporte técnico de centro de cumplimiento. a diferencia del centro de administración de Exchange (EAC), que no es compatible con consultas de los usuarios que aún no se mueven una vez que el inquilino mover se ha iniciado. Para obtener más información acerca de la seguridad &amp; centro de cumplimiento, consulte [Office 365 seguridad &amp; centro de cumplimiento](https://go.microsoft.com/fwlink/p/?linkid=841313). 
  
En la tabla siguiente se muestra cómo obtener acceso a la exhibición de documentos electrónicos y auditoría a través de la seguridad y el CEF &amp; centro de cumplimiento.
  
||**Centro de administración de Exchange**|**Seguridad &amp; centro de cumplimiento**|
|:-----|:-----|:-----|
|eDiscovery  <br/> | Vaya a https://portal.office.comy, a continuación, haga clic en el icono de **administración** . <br/> Haga clic en **centros de administración** \> **Exchange**. <br/> Seleccione **administración de cumplimiento de normas** \> **exhibición de documentos electrónicos en contexto &amp; suspensión**. | Vaya a https://portal.office.comy, a continuación, haga clic en el icono de administración. <br/> Haga clic en **centros de administración** \> **seguridad &amp; cumplimiento**. <br/> Seleccione **búsqueda &amp; investigación** \> **exhibición de documentos electrónicos**.|
|Auditoría  <br/> | Vaya a https://portal.office.comy, a continuación, haga clic en el icono de **administración** . <br/> Haga clic en **centros de administración** \> **Exchange**. Seleccione **administración de cumplimiento de normas** \> **auditoría**. | Vaya a https://portal.office.comy, a continuación, haga clic en el icono de administración. <br/> Haga clic en **centros de administración** \> **seguridad &amp; cumplimiento**. <br/> Seleccione **búsqueda &amp; investigación** \> **búsqueda de registro de auditoría**. |
   
### <a name="mailbox-migration"></a>Migración de correo

Cuando se mueve un inquilino entre zonas, un lote de migración puede informar de errores en algunos usuarios en el lote de migración que se dejan en el origen geográfico. En este caso, elimine el lote de migración existente para quitar la solicitud de sincronización subyacente. Después de que el lote se limpia totalmente, crear el lote de nuevo, que se iniciará la creación de solicitudes de sincronización en el ubican de destino.
  
## <a name="sharepoint-online"></a>SharePoint Online

Cuando se mueve SharePoint Online, también se mueven datos para los siguientes servicios:
  
- OneDrive para la Empresa
    
- Project Online
    
- Project para Office 365
    
- Servicios de vídeo de Office 365
    
- Office Online
    
- Office 365 ProPlus
    
- Visio Pro para Office 365
    
Una vez que hemos completado mover los datos de SharePoint Online, es posible que vea algunos de los siguientes efectos.
  
### <a name="office-365-video-services"></a>Servicios de vídeo de Office 365

- Mover los datos de vídeo requiere más tiempo que los movimientos para el resto del contenido en SharePoint Online.
    
- Después de SharePoint Online se mueve contenido, habrá un intervalo de tiempo cuando no pueden reproducir vídeos.
    
- Nos estamos quitando la transacción de forma rígida copia desde el centro de datos anterior y transcodificación nuevamente en el nuevo centro de datos.
    
### <a name="search"></a>Búsqueda

Durante el traslado de los datos de SharePoint Online, nos migrar la configuración de búsqueda e índices de búsqueda a una nueva ubicación. Hasta que se ha **completado** el movimiento de los datos de SharePoint Online, se seguirán atender los usuarios desde el índice en la ubicación original. En la nueva ubicación, búsqueda inicia automáticamente el rastreo de su contenido una vez que hemos completado mover los datos de SharePoint Online. De este punto y en adelante somos los usuarios desde el índice migrado. Los cambios realizados en el contenido que se ha producido después de la migración no se incluyen en el índice migrado hasta que el rastreo toma ellos. La mayoría de los clientes no tenga en cuenta que los resultados son menos derecha actualizado después de que se ha completado el movimiento de sus datos de SharePoint Online, pero algunos clientes podrían experimentar actualización reducción en las primeras horas de 24-48 
  
Se ven afectadas las siguientes características de búsqueda:
  
- Resultados de búsqueda y elementos Web de búsqueda: los resultados no incluyen los cambios que se ha producido después de la migración hasta que el rastreo toma ellos. 
    
- Profundizar: Profundizar no incluye los cambios que se ha producido después de la migración hasta que el rastreo toma ellos.
    
- Popularidad e informes de búsqueda para el sitio: incluyen solamente los recuentos de los informes de Excel en la nueva ubicación recuentos migrados y recuentos de informes de uso que se han ejecutado después de que se complete mover los datos de SharePoint Online. Los recuentos de desde el período provisional se pierden y no se puede recuperar. Este período normalmente es un par de días. Algunos clientes podrían experimentar pérdidas cortas o más largos.
    
- Portal de vídeo: Vista recuentos y estadísticas para el Portal de vídeo dependen de las estadísticas para los informes de Excel, por lo que los recuentos de vista y las estadísticas para el Portal de vídeo se pierden durante el mismo período de tiempo en cuanto a los informes de Excel.
    
- exhibición de documentos electrónicos: no se muestran hasta que el rastreo recoge los cambios de elementos que han cambiado durante la migración.
    
- Protección ante la pérdida de datos (DLP): No se aplican las directivas en los elementos que cambiar hasta que el rastreo recoge los cambios.
    
## <a name="skype-for-business"></a>Skype Empresarial

Todos los usuarios se cerrará desde el Skype para software de cliente de negocio durante la transferencia. En el inicio de sesión automático se volverán a conectar los usuarios dentro de dos minutos.
  
|**Características que funcionan durante todo traslado**|**Características que podrán estar limitadas durante una parte del movimiento**|
|:-----|:-----|
| Llamadas de voz y mensajería instantáneas  <br/>  Los usuarios pueden agregar contactos, agregar grupos de contactos, agregue las reuniones, establecer su ubicación y cambie "¿Qué ocurre hoy".  <br/>  Configuración de audio del proveedor de conferencia (ACP) se copia en el ubican del centro de datos de destino. Si el proveedor ACP está presente en el centro de datos de destino, funcionará. De lo contrario, no será posible.  <br/> | Inquilino Admin TRPS (PowerShell remoto inquilino) no estará disponible para los administradores crear sesiones.  <br/>  Administrador de inquilinos LAC no estará disponible para los administradores iniciar sesión y cambiar la configuración del usuario.  <br/> |
   
|**Tras el traslado**|
|:-----|
| Datos de la reunión (presentaciones que se cargan, etc.) no se moverán y tienen que volver a que se cargan.  <br/>  Clientes de Lync más antiguos, como el cliente de Lync 2010 y Lync para Mac 2011 cliente, se conocen en memoria caché de información de DNS para el servicio causando problemas de inicio de sesión. Puede ser necesario borrar la memoria caché de DNS si el usuario no está en el último Skype para cliente de Windows de negocio. Pida a los usuarios para ejecutar el [Asistente de solución de problemas](https://support.microsoft.com/en-us/kb/2541980) y siga las instrucciones acerca de cómo borrar la memoria caché del cliente. Lync para los usuarios de Mac cliente debe seguir [estas instrucciones](https://support.microsoft.com/en-us/kb/2629861).<br/> |
   
## <a name="data-for-other-services-including-yammer-and-power-bi"></a>Datos para otros servicios, incluidos Yammer y Power BI

Sólo se mover los datos de cliente de Exchange Online, SharePoint Online y Skype para la empresa. No se mover datos para otros servicios. No hay ningún cambio o impacto a usted como un cliente o un usuario de estos otros servicios. No influyen en el proceso de mover, y la ubicación de sus datos de clientes permanece inalterada.
  
## <a name="related-topics"></a>Temas relacionados 
 
[Cómo solicitar el movimiento de datos](request-your-data-move.md)
    
[Preguntas más frecuentes sobre el movimiento de datos](data-move-faq.md)
  
[Nuevas zonas de centro de datos de Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Servicios de Azure por región](https://azure.microsoft.com/en-us/regions/)

