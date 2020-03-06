---
title: 'Mover un sitio SharePoint a otra ubicación geográfica '
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
f1.keywords:
- NOCSH
description: Aprenda a mover un sitio de OneDrive a otra ubicación geográfica
ms.openlocfilehash: 8bcd76959cdddd5bb6fadf390e5b71df8decf0a0
ms.sourcegitcommit: 160a2564c90a4d64d19f072e0de9fe1b3cd0c917
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2020
ms.locfileid: "42417045"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a>Mover un sitio SharePoint a otra ubicación geográfica 

Con el movimiento geográfico de sitios de SharePoint, puede mover dichos sitios a otras ubicaciones geográficas dentro de su entorno multigeográfico. 

Los siguientes tipos de sitios pueden moverse entre ubicaciones geográficas:

- Sitios conectados a Grupos de Office 365
- Sitios modernos sin ninguna asociación con los Grupos de Office 365
- Sitios clásicos de SharePoint
- Sitios de comunicación

Debe ser un administrador global o un administrador de SharePoint para mover un sitio entre ubicaciones geográficas.

Hay una ventana de solo lectura durante el movimiento geográfico de sitios de SharePoint de aproximadamente 4 a 6 horas, según el contenido del sitio.
 
## <a name="best-practices"></a>Procedimientos recomendados

- Pruebe un movimiento del sitio de SharePoint en un sitio de prueba para familiarizarse con el procedimiento. 
- Compruebe si el sitio se puede mover antes de programar o realizar el cambio. 
- Cuando sea posible, programe movimientos de sitios entre ubicaciones geográficas fuera del horario laboral para reducir el impacto con el usuario.
- Comuníquese con los usuarios afectados antes del movimiento de sitios. 

## <a name="communicating-to-your-users"></a>Comunicación con los usuarios

Es importante comunicar el resultado esperado a los usuarios de los sitios (generalmente los que pueden editarlos), al migrar los sitios de SharePoint entre ubicaciones geográficas. Esto puede ayudar a reducir la confusión de los usuarios y las llamadas a su departamento de soporte técnico. Envíe un correo a los usuarios antes de mover los sitios e infórmeles de lo siguiente:

- Cuándo se espera que inicie el movimiento y cuánto tiempo se espera que tarde en completarse.
- La ubicación geográfica de destino para el sitio y la dirección URL para obtener acceso a la nueva ubicación.
- Necesitan cerrar sus archivos sin realizar ediciones durante el desplazamiento.
- Los permisos de archivo y el uso compartido no cambiará como resultado del movimiento.
- Acciones previstas de la experiencia del usuario en un entorno multigeográfico

Asegúrese de enviar a los usuarios un correo electrónico cuando se complete correctamente el movimiento para informarles de que pueden reanudar su trabajo en los sitios.

## <a name="scheduling-sharepoint-site-moves"></a>Programación de movimientos de sitios de SharePoint 

Puede programar los movimientos de sitios de SharePoint por adelantado (como se describe más adelante en este artículo). Puede programar los movimientos como sigue:

- Puede programar un máximo de 4000 movimientos cada vez.
- Al empezar el movimiento, puede programar más, con un máximo de 4000 movimientos pendientes en la cola y en cualquier momento.
 
Para programar un movimiento geográfico de sitio de SharePoint para un momento posterior, incluya uno de los parámetros siguiente al iniciar:
- `PreferredMoveBeginDate`: Es probable que se inicie el cambio en este momento especificado.
- `PreferredMoveEndDate`: Es probable que se complete el movimiento dentro de este tiempo especificado, en el mejor de los casos. 

La hora para ambos parámetros debe especificarse según el Tiempo universal coordinado (UTC).

## <a name="moving-the-site"></a>Mover el sitio

El movimiento geográfico del sitio de SharePoint requiere que se conecte y se realice desde la URL del administrador de SharePoint en la ubicación geográfica donde se encuentra el sitio.

Por ejemplo, si la URL del sitio es https://contosohealthcare.sharepoint.com/sites/Turbines, conéctese a la URL del administrador de SharePoint en https://contosohealthcare-admin.sharepoint.com:

`Connect-SPOService -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a>Validación del entorno

Se recomienda realizar una comprobación para asegurarse de que se puede mover el sitio, antes de programar su movimiento.

No se admite mover sitios con:
-   Servicios de conectividad empresarial
-   Formularios de InfoPath 
- Se aplicaron las plantillas de Information Rights Management (IRM)

Para asegurarse de que todas las ubicaciones geográficas son compatibles, ejecute `Get-SPOGeoMoveCrossCompatibilityStatus`. Esto mostrará todas las ubicaciones geográficas y si el entorno es compatible con la ubicación geográfica de destino.

Para realizar una comprobación de validación en el sitio, use `Start-SPOSiteContentMove` con el parámetro `-ValidationOnly` para comprobar si el sitio se puede mover. Por ejemplo:

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

Esto devolverá *Success* si el sitio está listo para moverse o *Fail* si hay algunas condiciones bloqueadas.

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a>Iniciar un movimiento geográfico de sitios de SharePoint con sitios sin ninguna asociación con los Grupos de Office 365

De forma predeterminada, se cambiará la dirección URL inicial del sitio a la dirección URL de la ubicación geográfica de destino. Por ejemplo:

https://Contoso.sharepoint.com/sites/projectx a https://ContosoEUR.sharepoint.com/sites/projectx

Los sitios sin ninguna asociación con los Grupos de Office 365, también pueden cambiar el nombre mediante el parámetro `-DestinationUrl`. Por ejemplo:

https://Contoso.sharepoint.com/sites/projectx a https://ContosoEUR.sharepoint.com/sites/projecty

Para iniciar el movimiento del sitio, ejecute:

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Captura de pantalla de la ventana de PowerShell que muestra el cmdlet Start-SPOSiteContentMove](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a>Iniciar el movimiento geográfico de sitios de SharePoint con sitios conectados a Grupos de Office 365

Para mover un sitio conectado a grupos de Office 365, primero el administrador global debe cambiar el atributo de ubicación de datos preferida (PDL) del Grupo de Office 365.

Para establecer la PDL de un Grupo de Office 365:

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
Una vez que haya actualizado la PDL, puede iniciar el movimiento del sitio: 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a>Cancelar un movimiento geográfico de sitios de SharePoint

Puede detener un movimiento geográfico de sitios de SharePoint, siempre que el movimiento no esté en curso ni se haya finalizado, mediante el cmdlet `Stop-SPOSiteContentMove`.

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a>Determinar el estado de un movimiento geográfico de sitios de SharePoint

Puede determinar el estado de un movimiento de sitios dentro y fuera de la ubicación geográfica a la que está conectado mediante los siguientes cmdlet:

- [Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (sitios no conectados al grupo)
- Get-SPOUnifiedGroupMoveState (sitios conectados al grupo)

Use el parámetro `-SourceSiteUrl` para especificar el sitio del que quiere ver el estado del movimiento.

Los estados del movimiento se describen en la tabla siguiente.

|Estado|Descripción|
|:-----|:----------|
|Ready to Trigger|No se ha iniciado el movimiento.|
|Scheduled|El movimiento está en cola, pero todavía no se ha iniciado.|
|InProgress (n/4)|El movimiento está en curso en uno de los siguientes estados: validación (1/4), copia de seguridad (2/4), restauración (3/4), limpieza (4/4).|
|Success|El movimiento se completó correctamente.|
|Failed|No se pudo realizar el movimiento.|

También puede aplicar la opción `-Verbose` para ver información adicional sobre el movimiento.

## <a name="user-experience"></a>Experiencia del usuario

Los usuarios del sitio deben notar una interrupción mínima al mover su sitio a otra ubicación geográfica. Excepto un estado breve de solo lectura durante el movimiento, los permisos y los vínculos existentes seguirán funcionando como se espera una vez completado el proceso.

### <a name="site"></a>Sitio

Mientras se realiza el movimiento, el sitio está configurado como de solo lectura. Una vez completado el movimiento, se dirige al usuario al sitio nuevo en la nueva ubicación geográfica al hacer clic en los marcadores u en otros vínculos del sitio.

### <a name="permissions"></a>Permisos

Los usuarios con permisos al sitio seguirán teniendo acceso durante el movimiento y después de su finalización.

### <a name="sync-client"></a>Cliente de sincronización

El cliente de sincronización detectará automáticamente y transferirá fácilmente la sincronización con la nueva ubicación de sitio, una vez completado el movimiento. El usuario no necesitará volver a iniciar sesión ni realizar ninguna otra acción. (Se requiere la versión 17.3.6943.0625 o posterior del cliente de sincronización).

Si un usuario actualiza un archivo mientras el movimiento está en curso, el cliente de sincronización le notificará que hay cargas de archivos pendientes mientras el movimiento está en curso.

### <a name="sharing-links"></a>Vínculos de uso compartido

Tras la finalización del movimiento geográfico de sitios de SharePoint, los vínculos compartidos existentes de los archivos que se movieron se redirigirán automáticamente a la nueva ubicación geográfica.

### <a name="most-recently-used-files-in-office-mru"></a>Los archivos usados recientemente de Office (MRU)

El servicio MRU se actualiza con la dirección URL del sitio y sus direcciones URL de contenido cuando se complete el movimiento. Eso se aplica a Word, Excel y PowerPoint

### <a name="onenote-experience"></a>Experiencia de OneNote

El cliente de win32 de OneNote y la aplicación UWP (Universal) detectarán automáticamente y sincronizarán perfectamente blocs de notas con la nueva ubicación del sitio cuando se complete el movimiento. El usuario no necesitará volver a iniciar sesión ni realizar ninguna otra acción. El único indicador visible para el usuario es que la sincronización de la notebook fallaría cuando el movimiento del sitio esté en curso. Esta experiencia está disponible en las siguientes versiones de cliente de OneNote:

- OneNote win32. versión 16.0.8326.2096 (y versiones posteriores)
- OneNote UWP: versión 16.0.8431.1006 (y versiones posteriores)
- Aplicación móvil de OneNote (versión 16.0.8431.1011 y versiones posteriores)

### <a name="teams-applicable-to-office-365-group-connected-sites"></a>Teams (se aplica a los sitios conectados al Grupo de Office 365)

Cuando se complete el movimiento geográfico de sitios de SharePoint, los usuarios tendrán acceso a sus archivos de sitio de Grupo de Office 365 en la aplicación de Teams. Además, los archivos compartidos mediante chat de Teams desde el sitio, antes del movimiento geográfico, seguirán funcionando tras completar el mismo.

### <a name="sharepoint-mobile-app-iosandroid"></a>Aplicación móvil de SharePoint para Android y iOS

Se admite la aplicación móvil de SharePoint entre las zonas geográficas y podrá detectar la nueva ubicación geográfica del sitio.

### <a name="sharepoint-workflows"></a>Flujos de trabajo de SharePoint

Los flujos de trabajo de SharePoint 2013 deben volver a publicarse después de mover el sitio. Los flujos de trabajo de SharePoint 2010 deberían seguir funcionando con normalidad.

### <a name="apps"></a>Aplicaciones

Si se mueve un sitio con aplicaciones, debe volver a crear instancias de aplicación en la nueva ubicación geográfica del sitio, ya que es posible que la aplicación y sus conexiones no estén disponibles en la ubicación geográfica de destino.

### <a name="flow"></a>Flow

En la mayoría de los casos los flujos seguirán funcionando después de mover geográficamente el sitio de SharePoint. Se recomienda probarlos una vez completado el movimiento.

### <a name="powerapps"></a>PowerApps

PowerApps debe volver a crearse en la ubicación de destino.

### <a name="data-movement-between-geo-locations"></a>Mover datos entre ubicaciones geográficas

SharePoint usa el Azure Blob Storage para su contenido, mientras los metadatos asociados con los sitios y los archivos se almacenan dentro de SharePoint. Cuando el sitio se mueve de su ubicación geográfica de origen a la de destino, el servicio también moverá el Blob Storage asociado.  El movimiento de Blob Storage se completa en aproximadamente 40 días. 
