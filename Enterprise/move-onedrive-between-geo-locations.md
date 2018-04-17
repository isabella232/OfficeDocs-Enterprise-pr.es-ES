---
title: Moverlo a una ubicación geográfica diferente OneDrive
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Obtenga información sobre cómo mover un sitio de OneDrive a una ubicación geográfica diferente.
ms.openlocfilehash: 7ce9106fa7d8d144f0f8935713b4df926a73fb6b
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Moverlo a una ubicación geográfica diferente OneDrive 

Con OneDrive geo mover, puede mover el OneDrive de un usuario a una ubicación geográfica diferente. Movimiento de OneDrive geo se realiza por el Administrador de SharePoint Online o el administrador global de Office 365. Antes de iniciar un OneDrive mover geo, asegúrese de notificar al usuario cuyo OneDrive se mueve y se recomienda que cierren todos los archivos para la duración del movimiento. (Si el usuario tiene un documento abierto con el cliente de Office durante el desplazamiento, a continuación, en mover el documento deberá guardarse en la nueva ubicación de finalización). El movimiento puede programarse para un momento futuro, si lo desea.

El servicio de OneDrive utiliza el almacenamiento de blobs de Azure para almacenar el contenido. El blob de almacenamiento asociado con OneDrive del usuario se moverán desde el origen a la ubicación de destino geográfico dentro de 40 días de OneDrive está disponible para el usuario de destino. Se restaurará el acceso a OneDrive de usuario tan pronto como el destino OneDrive está disponible.

Durante la ventana Mover de geo OneDrive (aproximadamente 2-6 horas) OneDrive del usuario se establece en sólo lectura. El usuario todavía puede tener acceso a sus archivos a través de su sitio de OneDrive en SharePoint Online o el cliente de sincronización OneDrive. Una vez OneDrive geo mover, el usuario se conectará automáticamente a su OneDrive en la ubicación de destino geográfico cuando navegan a OneDrive en el selector de la aplicación de Office 365. El cliente de sincronización iniciará automáticamente la sincronización desde la nueva ubicación.

Los procedimientos descritos en este artículo requieren el [Módulo de PowerShell en línea de Microsoft SharePoint](https://www.microsoft.com/en-us/download/details.aspx?id=35588).

## <a name="moving-a-onedrive-site"></a>Mover un sitio de OneDrive

Para llevar a cabo un OneDrive mover geo, Administrador de inquilinos primero debe establecer la ubicación de datos preferidos (PDL del usuario) a la ubicación geográfica correspondiente. Una vez establecido el PDL, espere al menos 24 horas sincronizar a través de las ubicaciones geo antes de iniciar el movimiento de geo OneDrive la actualización de PDL.

Cuando utiliza el geo mueve cmdlets, conectar a servicio de SPO en la ubicación del usuario actual OneDrive geo, utilizando la sintaxis siguiente:

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

Por ejemplo: para mover OneDrive de usuario 'Matt@contosoenergy.onmicrosoft.com', conectarse al centro de administración de SharePoint euros como OneDrive del usuario se encuentra en la ubicación geográfica de euros:

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a>Validación del entorno

Antes de empezar a mover un geo OneDrive, le recomendamos que valide el entorno.

Para garantizar que todas las ubicaciones de geo son compatibles, ejecute:

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

Si es un OneDrive bajo retención legal o contiene un subsitio, no se puede mover. Puede utilizar el cmdlet Start-SPOUserAndContentMove con el parámetro - ValidationOnly para validar si es capaz de mover el OneDrive:

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Esto devolverá un éxito si la OneDrive está listo para ser movido o producirá un error si existe una retención legal o subsitio que podría impedir el movimiento. Una vez que haya validado que el OneDrive esté listo para moverse, puede iniciar el movimiento.

## <a name="start-a-onedrive-geo-move"></a>Iniciar un movimiento de geo OneDrive

Para iniciar el movimiento, ejecute:  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

Con estos parámetros:

-   _UserPrincipalName_ : UPN del usuario cuyo OneDrive se va a mover.

-   _DestinationDataLocation_ : ubicación geográfica donde es necesario mover el OneDrive. Debe ser igual que la ubicación de datos preferido del usuario.

> [!NOTE]
> Se recomienda ejecutar `Get-SPOGeoMoveStateCompatibility` con `ValidationOnly` antes de iniciar la OneDrive mover geo.

Por ejemplo, para mover el OneDrive de matt@contosoenergy.onmicrosoft.com de euros a Australia, ejecute:

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

Para programar un traslado geográfico para un momento posterior, utilice uno de los siguientes parámetros:

-   _PreferredMoveBeginDate_ : el movimiento lo probable es que empiece a esa hora especificada. Tiempo debe especificarse en la hora Universal coordinada (UTC).

-   _PreferredMoveEndDate_ – el probable desplazamiento completarse hasta el momento especificado, en función del mejor esfuerzo. Tiempo debe especificarse en la hora Universal coordinada (UTC). 

## <a name="cancel-a-onedrive-geo-move"></a>Cancelar un desplazamiento de geo OneDrive 

Puede detener el movimiento geográfico de OneDrive de un usuario, siempre que el movimiento no está en curso o completado mediante el cmdlet:

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

Donde _UserPrincipalName_ es el UPN del usuario cuyo OneDrive mover que desea detener.

## <a name="determining-current-status"></a>Determinar el estado actual

Puede comprobar el estado de un OneDrive geo mover dentro o fuera del geo que está conectado mediante el cmdlet Get-SPOUserAndContentMoveState.

Los Estados de movimiento se describen en la tabla siguiente.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Estado</strong></th>
<th align="left"><strong>Descripción</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">No iniciado</td>
<td align="left">El movimiento no se ha iniciado.</td>
</tr>
<tr class="even">
<td align="left">En curso (<em>n</em>/4)</td>
<td align="left">El movimiento está en progreso en uno de los siguientes estados: validación (1/4), (2/4) de la copia de seguridad, restaurar (3/4), limpieza (4/4).</td>
</tr>
<tr class="odd">
<td align="left">Correcto</td>
<td align="left">El movimiento se ha completado correctamente.</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">Error en el movimiento.</td>
</tr>
</tbody>
</table>

Para encontrar el estado de movimiento de un usuario específico, utilice el parámetro UserPrincipalName:

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Para encontrar el estado de todos los movimientos dentro o fuera de la ubicación geográfica que está conectado a, utilice el parámetro MoveState con uno de los siguientes valores: no iniciado, en curso, éxito, error, todos.

`Get-SPOUserAndContentMoveState -MoveState <value>`

También puede agregar el `-Verbose` parámetro para obtener una descripción más detallada del estado de movimiento.

## <a name="user-experience"></a>Experiencia del usuario

Los usuarios de OneDrive deben observar una interrupción mínima si su OneDrive se mueve a una ubicación geográfica diferente. Aparte de un estado de sólo lectura breve durante el traslado, permisos y vínculos existentes seguirán funcionando como se esperaba una vez completado el movimiento.

### <a name="onedrive-for-business"></a>OneDrive for Business

Mientras se realiza el traslado OneDrive del usuario se establece en sólo lectura. Una vez completado el movimiento, el usuario se dirige a su OneDrive en la nueva ubicación geográfica cuando navegan a OneDrive el iniciador de la aplicación de Office 365 o un explorador web.

### <a name="permissions-on-onedrive-content"></a>Permisos de OneDrive contenido

Los usuarios con permisos para el contenido de OneDrive continuarán teniendo acceso al contenido durante el movimiento y, una vez terminado.

### <a name="onedrive-sync-client"></a>Cliente de sincronización de OneDrive 

El cliente de sincronización OneDrive detectará automáticamente y transferir fácilmente la sincronización a la nueva ubicación de OneDrive una vez finalizado el movimiento de geo OneDrive. El usuario no necesitará iniciar sesión nuevamente o realizar cualquier otra acción.

Si un usuario actualiza un archivo mientras se realiza el traslado de geo OneDrive, el cliente de sincronización notificará a ellos que están pendientes cargas de archivos mientras el movimiento está en curso.

### <a name="sharing-links"></a>Vínculos para compartir 

Tras OneDrive geo mover finalización, redirigirán automáticamente los vínculos compartidos existentes para los archivos que se movieron a la nueva ubicación geográfica.

### <a name="onenote-experience"></a>Experiencia de OneNote 

Cliente win32 de OneNote y UWP (Universal) de la aplicación detectará automáticamente y perfectamente sincronizar blocs de notas en la nueva ubicación de OneDrive una vez completada la OneDrive geo mover. El usuario no necesitará iniciar sesión nuevamente o realizar cualquier otra acción. El indicador sólo está visible para el usuario es la sincronización de Bloc de notas se produciría un error cuando OneDrive geo movimiento está en progreso. Esta experiencia está disponible en las siguientes versiones de cliente de OneNote:

-   OneNote win32: versión 16.0.8326.2096 (o posterior)

-   OneNote UWP – versión 16.0.8431.1006 (o posterior)

-   OneNote Mobile App – versión 16.0.8431.1011 (o posterior)

### <a name="teams-app"></a>Aplicación de los equipos

Tras OneDrive geo mover finalización, los usuarios tendrán acceso a sus archivos de OneDrive en el App de equipos Además, archivos compartidos a través de chat de los equipos de su OneDrive antes de mover geo seguirán funcionando después de completar el movimiento.

### <a name="onedrive-for-business-mobile-app-ios"></a>OneDrive para el negocio de la aplicación móvil (iOS) 

Tras OneDrive geo mover terminación, el usuario tendría que cerrar la sesión e iniciarla de nuevo en el iOS App Mobile para sincronizar con la nueva ubicación de OneDrive.

### <a name="existing-followed-groups-and-sites"></a>Existente seguido de grupos y sitios

Grupos y sitios visitados se mostrarán en el OneDrive del usuario para la empresa independientemente de su ubicación geográfica. Sitios y grupos alojados en otra ubicación geográfica se abren en una pestaña distinta.
