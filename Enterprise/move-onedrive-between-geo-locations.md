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
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="0e5b7-103">Moverlo a una ubicación geográfica diferente OneDrive</span><span class="sxs-lookup"><span data-stu-id="0e5b7-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="0e5b7-p101">Con OneDrive geo mover, puede mover el OneDrive de un usuario a una ubicación geográfica diferente. Movimiento de OneDrive geo se realiza por el Administrador de SharePoint Online o el administrador global de Office 365. Antes de iniciar un OneDrive mover geo, asegúrese de notificar al usuario cuyo OneDrive se mueve y se recomienda que cierren todos los archivos para la duración del movimiento. (Si el usuario tiene un documento abierto con el cliente de Office durante el desplazamiento, a continuación, en mover el documento deberá guardarse en la nueva ubicación de finalización). El movimiento puede programarse para un momento futuro, si lo desea.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="0e5b7-p102">El servicio de OneDrive utiliza el almacenamiento de blobs de Azure para almacenar el contenido. El blob de almacenamiento asociado con OneDrive del usuario se moverán desde el origen a la ubicación de destino geográfico dentro de 40 días de OneDrive está disponible para el usuario de destino. Se restaurará el acceso a OneDrive de usuario tan pronto como el destino OneDrive está disponible.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="0e5b7-p103">Durante la ventana Mover de geo OneDrive (aproximadamente 2-6 horas) OneDrive del usuario se establece en sólo lectura. El usuario todavía puede tener acceso a sus archivos a través de su sitio de OneDrive en SharePoint Online o el cliente de sincronización OneDrive. Una vez OneDrive geo mover, el usuario se conectará automáticamente a su OneDrive en la ubicación de destino geográfico cuando navegan a OneDrive en el selector de la aplicación de Office 365. El cliente de sincronización iniciará automáticamente la sincronización desde la nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="0e5b7-115">Los procedimientos descritos en este artículo requieren el [Módulo de PowerShell en línea de Microsoft SharePoint](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="0e5b7-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="0e5b7-116">Mover un sitio de OneDrive</span><span class="sxs-lookup"><span data-stu-id="0e5b7-116">Moving a OneDrive site</span></span>

<span data-ttu-id="0e5b7-p104">Para llevar a cabo un OneDrive mover geo, Administrador de inquilinos primero debe establecer la ubicación de datos preferidos (PDL del usuario) a la ubicación geográfica correspondiente. Una vez establecido el PDL, espere al menos 24 horas sincronizar a través de las ubicaciones geo antes de iniciar el movimiento de geo OneDrive la actualización de PDL.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p104">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="0e5b7-119">Cuando utiliza el geo mueve cmdlets, conectar a servicio de SPO en la ubicación del usuario actual OneDrive geo, utilizando la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-119">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="0e5b7-120">Por ejemplo: para mover OneDrive de usuario 'Matt@contosoenergy.onmicrosoft.com', conectarse al centro de administración de SharePoint euros como OneDrive del usuario se encuentra en la ubicación geográfica de euros:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-120">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="0e5b7-121">Validación del entorno</span><span class="sxs-lookup"><span data-stu-id="0e5b7-121">Validating the environment</span></span>

<span data-ttu-id="0e5b7-122">Antes de empezar a mover un geo OneDrive, le recomendamos que valide el entorno.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-122">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="0e5b7-123">Para garantizar que todas las ubicaciones de geo son compatibles, ejecute:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-123">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="0e5b7-p105">Si es un OneDrive bajo retención legal o contiene un subsitio, no se puede mover. Puede utilizar el cmdlet Start-SPOUserAndContentMove con el parámetro - ValidationOnly para validar si es capaz de mover el OneDrive:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p105">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="0e5b7-p106">Esto devolverá un éxito si la OneDrive está listo para ser movido o producirá un error si existe una retención legal o subsitio que podría impedir el movimiento. Una vez que haya validado que el OneDrive esté listo para moverse, puede iniciar el movimiento.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p106">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="0e5b7-128">Iniciar un movimiento de geo OneDrive</span><span class="sxs-lookup"><span data-stu-id="0e5b7-128">Start a OneDrive geo move</span></span>

<span data-ttu-id="0e5b7-129">Para iniciar el movimiento, ejecute:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-129">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="0e5b7-130">Con estos parámetros:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-130">Using these parameters:</span></span>

-   <span data-ttu-id="0e5b7-131">_UserPrincipalName_ : UPN del usuario cuyo OneDrive se va a mover.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-131">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="0e5b7-p107">_DestinationDataLocation_ : ubicación geográfica donde es necesario mover el OneDrive. Debe ser igual que la ubicación de datos preferido del usuario.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p107">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="0e5b7-134">Se recomienda ejecutar `Get-SPOGeoMoveStateCompatibility` con `ValidationOnly` antes de iniciar la OneDrive mover geo.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-134">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="0e5b7-135">Por ejemplo, para mover el OneDrive de matt@contosoenergy.onmicrosoft.com de euros a Australia, ejecute:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-135">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="0e5b7-136">Para programar un traslado geográfico para un momento posterior, utilice uno de los siguientes parámetros:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-136">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="0e5b7-p108">_PreferredMoveBeginDate_ : el movimiento lo probable es que empiece a esa hora especificada. Tiempo debe especificarse en la hora Universal coordinada (UTC).</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p108">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="0e5b7-p109">_PreferredMoveEndDate_ – el probable desplazamiento completarse hasta el momento especificado, en función del mejor esfuerzo. Tiempo debe especificarse en la hora Universal coordinada (UTC).</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p109">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="0e5b7-141">Cancelar un desplazamiento de geo OneDrive</span><span class="sxs-lookup"><span data-stu-id="0e5b7-141">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="0e5b7-142">Puede detener el movimiento geográfico de OneDrive de un usuario, siempre que el movimiento no está en curso o completado mediante el cmdlet:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-142">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="0e5b7-143">Donde _UserPrincipalName_ es el UPN del usuario cuyo OneDrive mover que desea detener.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-143">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="0e5b7-144">Determinar el estado actual</span><span class="sxs-lookup"><span data-stu-id="0e5b7-144">Determining current status</span></span>

<span data-ttu-id="0e5b7-145">Puede comprobar el estado de un OneDrive geo mover dentro o fuera del geo que está conectado mediante el cmdlet Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-145">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="0e5b7-146">Los Estados de movimiento se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-146">The move statuses are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="0e5b7-147"><strong>Estado</strong></span><span class="sxs-lookup"><span data-stu-id="0e5b7-147"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="0e5b7-148"><strong>Descripción</strong></span><span class="sxs-lookup"><span data-stu-id="0e5b7-148"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="0e5b7-149">No iniciado</span><span class="sxs-lookup"><span data-stu-id="0e5b7-149">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="0e5b7-150">El movimiento no se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-150">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0e5b7-151">En curso (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="0e5b7-151">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="0e5b7-152">El movimiento está en progreso en uno de los siguientes estados: validación (1/4), (2/4) de la copia de seguridad, restaurar (3/4), limpieza (4/4).</span><span class="sxs-lookup"><span data-stu-id="0e5b7-152">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="0e5b7-153">Correcto</span><span class="sxs-lookup"><span data-stu-id="0e5b7-153">Success</span></span></td>
<td align="left"><span data-ttu-id="0e5b7-154">El movimiento se ha completado correctamente.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-154">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="0e5b7-155">Failed</span><span class="sxs-lookup"><span data-stu-id="0e5b7-155">Failed</span></span></td>
<td align="left"><span data-ttu-id="0e5b7-156">Error en el movimiento.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-156">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="0e5b7-157">Para encontrar el estado de movimiento de un usuario específico, utilice el parámetro UserPrincipalName:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-157">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="0e5b7-158">Para encontrar el estado de todos los movimientos dentro o fuera de la ubicación geográfica que está conectado a, utilice el parámetro MoveState con uno de los siguientes valores: no iniciado, en curso, éxito, error, todos.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-158">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="0e5b7-159">También puede agregar el `-Verbose` parámetro para obtener una descripción más detallada del estado de movimiento.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-159">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="0e5b7-160">Experiencia del usuario</span><span class="sxs-lookup"><span data-stu-id="0e5b7-160">User Experience</span></span>

<span data-ttu-id="0e5b7-p110">Los usuarios de OneDrive deben observar una interrupción mínima si su OneDrive se mueve a una ubicación geográfica diferente. Aparte de un estado de sólo lectura breve durante el traslado, permisos y vínculos existentes seguirán funcionando como se esperaba una vez completado el movimiento.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p110">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="0e5b7-163">OneDrive for Business</span><span class="sxs-lookup"><span data-stu-id="0e5b7-163">OneDrive for Business</span></span>

<span data-ttu-id="0e5b7-p111">Mientras se realiza el traslado OneDrive del usuario se establece en sólo lectura. Una vez completado el movimiento, el usuario se dirige a su OneDrive en la nueva ubicación geográfica cuando navegan a OneDrive el iniciador de la aplicación de Office 365 o un explorador web.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p111">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="0e5b7-166">Permisos de OneDrive contenido</span><span class="sxs-lookup"><span data-stu-id="0e5b7-166">Permissions on OneDrive content</span></span>

<span data-ttu-id="0e5b7-167">Los usuarios con permisos para el contenido de OneDrive continuarán teniendo acceso al contenido durante el movimiento y, una vez terminado.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-167">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="0e5b7-168">Cliente de sincronización de OneDrive</span><span class="sxs-lookup"><span data-stu-id="0e5b7-168">OneDrive Sync Client</span></span> 

<span data-ttu-id="0e5b7-p112">El cliente de sincronización OneDrive detectará automáticamente y transferir fácilmente la sincronización a la nueva ubicación de OneDrive una vez finalizado el movimiento de geo OneDrive. El usuario no necesitará iniciar sesión nuevamente o realizar cualquier otra acción.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p112">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.</span></span>

<span data-ttu-id="0e5b7-171">Si un usuario actualiza un archivo mientras se realiza el traslado de geo OneDrive, el cliente de sincronización notificará a ellos que están pendientes cargas de archivos mientras el movimiento está en curso.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-171">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="0e5b7-172">Vínculos para compartir</span><span class="sxs-lookup"><span data-stu-id="0e5b7-172">Sharing links</span></span> 

<span data-ttu-id="0e5b7-173">Tras OneDrive geo mover finalización, redirigirán automáticamente los vínculos compartidos existentes para los archivos que se movieron a la nueva ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-173">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="0e5b7-174">Experiencia de OneNote</span><span class="sxs-lookup"><span data-stu-id="0e5b7-174">OneNote Experience</span></span> 

<span data-ttu-id="0e5b7-p113">Cliente win32 de OneNote y UWP (Universal) de la aplicación detectará automáticamente y perfectamente sincronizar blocs de notas en la nueva ubicación de OneDrive una vez completada la OneDrive geo mover. El usuario no necesitará iniciar sesión nuevamente o realizar cualquier otra acción. El indicador sólo está visible para el usuario es la sincronización de Bloc de notas se produciría un error cuando OneDrive geo movimiento está en progreso. Esta experiencia está disponible en las siguientes versiones de cliente de OneNote:</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p113">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="0e5b7-179">OneNote win32: versión 16.0.8326.2096 (o posterior)</span><span class="sxs-lookup"><span data-stu-id="0e5b7-179">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="0e5b7-180">OneNote UWP – versión 16.0.8431.1006 (o posterior)</span><span class="sxs-lookup"><span data-stu-id="0e5b7-180">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="0e5b7-181">OneNote Mobile App – versión 16.0.8431.1011 (o posterior)</span><span class="sxs-lookup"><span data-stu-id="0e5b7-181">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="0e5b7-182">Aplicación de los equipos</span><span class="sxs-lookup"><span data-stu-id="0e5b7-182">Teams app</span></span>

<span data-ttu-id="0e5b7-p114">Tras OneDrive geo mover finalización, los usuarios tendrán acceso a sus archivos de OneDrive en el App de equipos Además, archivos compartidos a través de chat de los equipos de su OneDrive antes de mover geo seguirán funcionando después de completar el movimiento.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p114">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="0e5b7-185">OneDrive para el negocio de la aplicación móvil (iOS)</span><span class="sxs-lookup"><span data-stu-id="0e5b7-185">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="0e5b7-186">Tras OneDrive geo mover terminación, el usuario tendría que cerrar la sesión e iniciarla de nuevo en el iOS App Mobile para sincronizar con la nueva ubicación de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-186">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="0e5b7-187">Existente seguido de grupos y sitios</span><span class="sxs-lookup"><span data-stu-id="0e5b7-187">Existing followed groups and sites</span></span>

<span data-ttu-id="0e5b7-p115">Grupos y sitios visitados se mostrarán en el OneDrive del usuario para la empresa independientemente de su ubicación geográfica. Sitios y grupos alojados en otra ubicación geográfica se abren en una pestaña distinta.</span><span class="sxs-lookup"><span data-stu-id="0e5b7-p115">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
