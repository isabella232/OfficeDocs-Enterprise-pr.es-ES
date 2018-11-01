---
title: Mover un sitio de OneDrive a otra ubicación geográfica
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Aprenda a mover un sitio de OneDrive a otra ubicación geográfica
ms.openlocfilehash: 258c562343875ff4ad115b81dba5338c79641dfc
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849856"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a>Mover un sitio de OneDrive a otra ubicación geográfica 

Con la transferencia geográfica de OneDrive, puede mover la instancia de OneDrive del usuario a otra ubicación geográfica. La transferencia geográfica de OneDrive la realiza el administrador de SharePoint Online o el administrador global de Office 365. Antes de iniciar una transferencia geográfica de OneDrive, asegúrese de notificar al usuario cuya instancia de OneDrive se mueve y recomendarle que cierre todos los archivos durante el movimiento. (Si el usuario tiene un documento abierto con el cliente Office durante el movimiento, es necesario guardar el documento en la nueva ubicación al finalizar el movimiento). El movimiento puede programarse para un momento futuro.

El servicio de OneDrive usa Azure Blob Storage para almacenar contenido. El blob de almacenamiento asociado a la instancia de OneDrive del usuario se moverá de la ubicación geográfica de origen a la de destino. La ubicación de destino de OneDrive estará disponible para el usuario en los 40 días siguientes. El acceso a la instancia de OneDrive del usuario se restablecerá en cuanto la ubicación de destino de OneDrive esté disponible.

Durante el período de transferencia geográfica de OneDrive (de 2 a 6 horas), el usuario de OneDrive se establece en solo lectura. Todavía tiene acceso a sus archivos mediante el cliente de sincronización de OneDrive o en su sitio de OneDrive en SharePoint Online. Al finalizar la transferencia geográfica de OneDrive, el usuario se conectará automáticamente a su OneDrive en la ubicación geográfica de destino cuando navegue a OneDrive en el iniciador de aplicaciones de Office 365. El cliente de sincronización iniciará automáticamente la sincronización desde la nueva ubicación.

Los procedimientos descritos en este artículo necesitan el [Módulo de PowerShell de Microsoft SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588).

## <a name="communicating-to-your-users"></a>Comunicación con los usuarios

Al mover sitios de OneDrive entre ubicaciones geográficas, es importante comunicar a los usuarios lo que pueden esperar que ocurra. Esto permitirá reducir la confusión de los usuarios y las llamadas al departamento de soporte técnico. Envíe un correo electrónico a los usuarios antes de la migración y proporcióneles la información siguiente:

- Cuándo se espera que se inicie la migración y cuánto tiempo se espera que tarde en completarse.
- La ubicación geográfica de destino para su cuenta de OneDrive y la dirección URL para obtener acceso a la nueva ubicación.
- Necesitan cerrar sus archivos y no realizar ediciones durante la migración.
- El uso compartido de los permisos de archivos no cambiará como resultado de la migración.
- Acciones previstas de la [experiencia del usuario en un entorno multigeográfico](multi-geo-user-experience.md)

Asegúrese de enviar a los usuarios un correo electrónico cuando se complete correctamente la migración para informarles de que pueden reanudar su trabajo en OneDrive.

## <a name="scheduling-onedrive-site-moves"></a>Programar movimientos de un sitio de OneDrive

Puede programar de antemano los movimientos del sitio de OneDrive (tal como se describe más adelante en este artículo). Le recomendamos que empiece por un número pequeño de usuarios para validar los flujos de trabajo y las estrategias de comunicación. Una vez que esté familiarizado con el proceso, puede programar movimientos de la siguiente manera:

- Puede programar un máximo de 4000 movimientos cada vez.
- Al empezar el movimiento, puede programar más, con un máximo de 4000 movimientos pendientes en la cola y en cualquier momento.
- Recomendamos no programar más de 4000 movimientos al mes.

## <a name="moving-a-onedrive-site"></a>Mover un sitio de OneDrive

Para realizar una transferencia geográfica de OneDrive, el administrador de espacios empresariales debe establecer primero la ubicación de datos preferida (PDL) del usuario en la ubicación geográfica adecuada. Cuando se haya establecido la PDL, espere como mínimo 24 para que la actualización de PDL se sincronice en todas las ubicaciones geográficas antes de iniciar la transferencia geográfica de OneDrive.

Al usar los cmdlets de transferencia geográfica, conéctese al servicio de SPO en la ubicación geográfica actual de OneDrive del usuario, con la sintaxis siguiente:

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

Por ejemplo, para mover la instancia de OneDrive del usuario "Matt@contosoenergy.onmicrosoft.com", conéctese al Centro de administración de SharePoint EUR, ya que la instancia de OneDrive del usuario se encuentra en la ubicación geográfica EUR:

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)

## <a name="validating-the-environment"></a>Validación del entorno

Antes de iniciar la transferencia geográfica de OneDrive, se recomienda validar el entorno.

Para asegurarse de que todas las ubicaciones geográficas son compatibles, ejecute:

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

Si una instancia de OneDrive se encuentra en suspensión legal o contiene un subsitio no puede moverse. Puede usar el cmdlet Start-SPOUserAndContentMove cmdlet con el parámetro -ValidationOnly para validar si la instancia de OneDrive puede moverse:

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

Se devolverá Success si OneDrive está listo para moverse o Fail si hay una suspensión legal o un subsitio que impida el movimiento. Cuando haya validado que OneDrive está listo para moverse, puede iniciar el movimiento.

## <a name="start-a-onedrive-geo-move"></a>Iniciar una transferencia geográfica de OneDrive

Para iniciar el movimiento, ejecute:  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

Con estos parámetros:

-   _UserPrincipalName_: UPN del usuario cuya instancia de OneDrive se va a mover.

-   _DestinationDataLocation_: ubicación geográfica a la que hay que mover OneDrive. Debe ser la ubicación de datos preferida del usuario.

> [!NOTE]
> Se recomienda ejecutar `Get-SPOGeoMoveStateCompatibility` con `ValidationOnly` antes de iniciar la transferencia geográfica de OneDrive.

Por ejemplo, para mover la instancia de OneDrive de matt@contosoenergy.onmicrosoft.com de EUR a AUS, ejecute:

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations-image2.png)

Para programar una transferencia geográfica para más adelante, use uno de los parámetros siguientes:

-   _PreferredMoveBeginDate_: es probable que el movimiento se inicie a la hora especificada. La hora debe especificarse en la hora universal coordinada (UTC).

-   _PreferredMoveEndDate_: es probable que el movimiento finalice antes de la hora especificada, sin garantía. La hora debe especificarse en la hora universal coordinada (UTC). 

## <a name="cancel-a-onedrive-geo-move"></a>Cancelar una transferencia geográfica de OneDrive 

Para detener la transferencia geográfica de una instancia de OneDrive del usuario, siempre que el movimiento no esté en curso ni finalizado, use el cmdlet:

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

Donde _UserPrincipalName_ es el UPN del usuario cuyo movimiento de OneDrive se quiere detener.

## <a name="determining-current-status"></a>Determinación del estado actual

Puede comprobar el estado de una transferencia geográfica de OneDrive desde o hasta la geoárea a la que esté conectado con el cmdlet Get-SPOUserAndContentMoveState.

Los estados del movimiento se describen en la tabla siguiente.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Estado</strong></th>
<th align="left"><strong>Descripción</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">NotStarted</td>
<td align="left">No se ha iniciado el movimiento.</td>
</tr>
<tr class="even">
<td align="left">InProgress (<em>n</em>/4)</td>
<td align="left">El movimiento está en curso en uno de los siguientes estados: validación (1/4), copia de seguridad (2/4), restauración (3/4), limpieza (4/4).</td>
</tr>
<tr class="odd">
<td align="left">Success</td>
<td align="left">El movimiento se completó correctamente.</td>
</tr>
<tr class="even">
<td align="left">Failed</td>
<td align="left">No se pudo realizar el movimiento.</td>
</tr>
</tbody>
</table>

Para ver el estado del movimiento de un usuario específico, use el parámetro UserPrincipalName:

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

Para buscar el estado de todos los movimientos desde o hasta la ubicación geográfica a la que está conectado, use el parámetro MoveState con uno de los siguientes valores: NotStarted, InProgress, Success, Failed, All.

`Get-SPOUserAndContentMoveState -MoveState <value>`

También puede agregar el parámetro `-Verbose` para obtener una descripción más detallada del estado del movimiento.

## <a name="user-experience"></a>Experiencia del usuario

Los usuarios de OneDrive no deberían advertir ninguna interrupción si su instancia de OneDrive se mueve a otra ubicación geográfica. Excepto un breve estado de solo lectura durante el cambio, los vínculos y permisos existentes seguirán funcionando como se espera una vez completado el movimiento.

### <a name="onedrive-for-business"></a>OneDrive para la Empresa

Mientras se realiza el movimiento, el estado de OneDrive del usuario se establece en solo lectura. Una vez completado el movimiento, el usuario se dirigirá a su OneDrive en la nueva ubicación geográfica cuando navegue a OneDrive, el iniciador de aplicaciones de Office 365 o un explorador web.

### <a name="permissions-on-onedrive-content"></a>Permisos en contenido de OneDrive

Los usuarios con permisos de contenido de OneDrive seguirán teniendo acceso al contenido durante el movimiento y después de su finalización.

### <a name="onedrive-sync-client"></a>Cliente de sincronización de OneDrive 

El cliente de sincronización de OneDrive detectará automáticamente la sincronización y la transferirá de forma fluida a la nueva ubicación de OneDrive cuando se haya completado el movimiento geográfico de OneDrive. El usuario no tiene que volver a iniciar la sesión ni realizar ninguna otra acción. (Se necesita la versión 17.3.6943.0625 o posteriores del cliente de sincronización).

Si un usuario actualiza un archivo mientras el movimiento geográfico de OneDrive está en curso, el cliente de sincronización le notificará que hay cargas de archivos pendientes mientras el movimiento está en curso.

### <a name="sharing-links"></a>Vínculos de uso compartido 

Tras la finalización de la transferencia geográfica de OneDrive, los vínculos compartidos existentes a los archivos que se movieron se redirigirán automáticamente a la nueva ubicación geográfica.

### <a name="onenote-experience"></a>Experiencia de OneNote 

El cliente OneNote win32 y la aplicación UWP (Universal) detectarán automáticamente los blocs de notas y los sincronizarán perfectamente con la nueva ubicación de OneDrive cuando se haya completado la transferencia geográfica de OneDrive. El usuario no tiene que volver a iniciar sesión ni realizar ninguna otra acción. El único indicador visible para el usuario sería un error de sincronización de blocs de notas cuando la transferencia geográfica de OneDrive está en curso. Esta experiencia está disponible en las siguientes versiones de cliente OneNote:

-   OneNote win32. versión 16.0.8326.2096 (y versiones posteriores)

-   OneNote UWP: versión 16.0.8431.1006 (y versiones posteriores)

-   Aplicación móvil de OneNote (versión 16.0.8431.1011 y versiones posteriores)

### <a name="teams-app"></a>Aplicación de Teams

Tras la finalización de la transferencia geográfica de OneDrive, los usuarios tendrán acceso a sus archivos de OneDrive en la aplicación de Teams. Además, los archivos compartidos a través de chats de Teams desde su instancia de OneDrive anteriores a la transferencia geográfica seguirán funcionando tras completar el movimiento.

### <a name="onedrive-for-business-mobile-app-ios"></a>Aplicación móvil de OneDrive para la Empresa (iOS) 

Tras la finalización de la transferencia geográfica de OneDrive, el usuario tendría que cerrar sesión e iniciarla de nuevo en la aplicación para dispositivos móviles iOS a fin de sincronizarla con la nueva ubicación de OneDrive.

### <a name="existing-followed-groups-and-sites"></a>Sitios y grupos seguidos existentes

Los sitios y grupos seguidos se mostrarán en la instancia de OneDrive del usuario independientemente de su ubicación geográfica. Los sitios y grupos hospedados en otra ubicación geográfica se abrirán en una pestaña aparte.
