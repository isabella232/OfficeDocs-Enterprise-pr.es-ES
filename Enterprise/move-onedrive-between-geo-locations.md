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
ms.openlocfilehash: 80768d0838d1d5d072d3e221c4c2b4b1af78dae6
ms.sourcegitcommit: aabd369fc8b397f9e738374d42d8afd18b96d469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "19174906"
---
# <a name="move-a-onedrive-site-to-a-different-geo-location"></a><span data-ttu-id="aafa1-103">Mover un sitio de OneDrive a otra ubicación geográfica</span><span class="sxs-lookup"><span data-stu-id="aafa1-103">Move a OneDrive site to a different geo-location</span></span> 

<span data-ttu-id="aafa1-p101">Con la transferencia geográfica de OneDrive, puede mover la instancia de OneDrive del usuario a otra ubicación geográfica. La transferencia geográfica de OneDrive la realiza el administrador de SharePoint Online o el administrador global de Office 365. Antes de iniciar una transferencia geográfica de OneDrive, asegúrese de notificar al usuario cuya instancia de OneDrive se mueve y recomendarle que cierre todos los archivos durante el movimiento. (Si el usuario tiene un documento abierto con el cliente Office durante el movimiento, es necesario guardar el documento en la nueva ubicación al finalizar el movimiento). El movimiento puede programarse para un momento futuro.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p101">With OneDrive geo move, you can move a user’s OneDrive to a different geo location. OneDrive geo move is performed by the SharePoint Online administrator or the Office 365 global administrator. Before you start a OneDrive geo move, be sure to notify the user whose OneDrive is being moved and recommend they close all files for the duration of the move. (If the user has a document open using the Office client during the move, then upon move completion the document will need to be saved to the new location.) The move can be scheduled for a future time, if desired.</span></span>

<span data-ttu-id="aafa1-p102">El servicio de OneDrive usa Azure Blob Storage para almacenar contenido. El blob de almacenamiento asociado a la instancia de OneDrive del usuario se moverá de la ubicación geográfica de origen a la de destino. La ubicación de destino de OneDrive estará disponible para el usuario en los 40 días siguientes. El acceso a la instancia de OneDrive del usuario se restablecerá en cuanto la ubicación de destino de OneDrive esté disponible.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p102">The OneDrive service uses Azure Blob Storage to store content. The Storage blob associated with the user’s OneDrive will be moved from the source to destination geo location within 40 days of destination OneDrive being available to the user. The access to the user’s OneDrive will be restored as soon as the destination OneDrive is available.</span></span>

<span data-ttu-id="aafa1-p103">Durante el período de transferencia geográfica de OneDrive (de 2 a 6 horas), el usuario de OneDrive se establece en solo lectura. Todavía tiene acceso a sus archivos mediante el cliente de sincronización de OneDrive o en su sitio de OneDrive en SharePoint Online. Al finalizar la transferencia geográfica de OneDrive, el usuario se conectará automáticamente a su OneDrive en la ubicación geográfica de destino cuando navegue a OneDrive en el iniciador de aplicaciones de Office 365. El cliente de sincronización iniciará automáticamente la sincronización desde la nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p103">During OneDrive geo move window (about 2-6 hours) the user's OneDrive is set to read-only. The user can still access their files via the OneDrive sync client or their OneDrive site in SharePoint Online. After OneDrive geo move is complete, the user will be automatically connected to their OneDrive at the destination geo location when they navigate to OneDrive in the Office 365 app launcher. The sync client will automatically begin syncing from the new location.</span></span>

<span data-ttu-id="aafa1-115">Los procedimientos descritos en este artículo necesitan el [Módulo de PowerShell de Microsoft SharePoint Online](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span><span class="sxs-lookup"><span data-stu-id="aafa1-115">The procedures in this article require the [Microsoft SharePoint Online PowerShell Module](https://www.microsoft.com/en-us/download/details.aspx?id=35588).</span></span>

## <a name="communicating-to-your-users"></a><span data-ttu-id="aafa1-116">Comunicación con los usuarios</span><span class="sxs-lookup"><span data-stu-id="aafa1-116">Communicating to your users</span></span>

<span data-ttu-id="aafa1-p104">Al mover sitios de OneDrive entre ubicaciones geográficas, es importante comunicar a los usuarios lo que pueden esperar que ocurra. Esto permitirá reducir la confusión de los usuarios y las llamadas al departamento de soporte técnico. Envíe un correo electrónico a los usuarios antes de la migración y proporcióneles la información siguiente:</span><span class="sxs-lookup"><span data-stu-id="aafa1-p104">When moving OneDrive sites between geo-locations, it's important to communicate to your users what to expect. This can help reduce user confusion and calls to your help desk. Email your users before the move and let them know the following information:</span></span>

- <span data-ttu-id="aafa1-120">Cuándo se espera que se inicie la migración y cuánto tiempo se espera que tarde en completarse.</span><span class="sxs-lookup"><span data-stu-id="aafa1-120">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="aafa1-121">La ubicación geográfica de destino para su cuenta de OneDrive y la dirección URL para obtener acceso a la nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="aafa1-121">What geo location their OneDrive is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="aafa1-122">Necesitan cerrar sus archivos y no realizar ediciones durante la migración.</span><span class="sxs-lookup"><span data-stu-id="aafa1-122">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="aafa1-123">El uso compartido de los permisos de archivos no cambiará como resultado de la migración.</span><span class="sxs-lookup"><span data-stu-id="aafa1-123">File permissions and sharing will not change as a result of the move.</span></span>
- <span data-ttu-id="aafa1-124">Acciones previstas de la [experiencia del usuario en un entorno multigeográfico](multi-geo-user-experience.md)</span><span class="sxs-lookup"><span data-stu-id="aafa1-124">What to expect from the [user experience in a multi-geo environment](multi-geo-user-experience.md)</span></span>

<span data-ttu-id="aafa1-125">Asegúrese de enviar a los usuarios un correo electrónico cuando se complete correctamente la migración para informarles de que pueden reanudar su trabajo en OneDrive.</span><span class="sxs-lookup"><span data-stu-id="aafa1-125">Be sure to send your users an email when the move has successfully completed informing them that they can resume working in OneDrive.</span></span>

## <a name="moving-a-onedrive-site"></a><span data-ttu-id="aafa1-126">Mover un sitio de OneDrive</span><span class="sxs-lookup"><span data-stu-id="aafa1-126">Moving a OneDrive site</span></span>

<span data-ttu-id="aafa1-p105">Para realizar una transferencia geográfica de OneDrive, el administrador de espacios empresariales debe establecer primero la ubicación de datos preferida (PDL) del usuario en la ubicación geográfica adecuada. Cuando se haya establecido la PDL, espere como mínimo 24 para que la actualización de PDL se sincronice en todas las ubicaciones geográficas antes de iniciar la transferencia geográfica de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p105">To perform a OneDrive geo move, the tenant administrator must first set the user’s Preferred Data Location (PDL) to the appropriate geo location. Once the PDL is set, wait for at least 24 hours for the PDL update to sync across the geo locations before starting the OneDrive geo move.</span></span>

<span data-ttu-id="aafa1-129">Al usar los cmdlets de transferencia geográfica, conéctese al servicio de SPO en la ubicación geográfica actual de OneDrive del usuario, con la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="aafa1-129">When using the geo move cmdlets, connect to SPO Service at the user’s current OneDrive geo location, using the following syntax:</span></span>

`connect-sposervice -url https://<tenantName>-admin.sharepoint.com`

<span data-ttu-id="aafa1-130">Por ejemplo, para mover la instancia de OneDrive del usuario "Matt@contosoenergy.onmicrosoft.com", conéctese al Centro de administración de SharePoint EUR, ya que la instancia de OneDrive del usuario se encuentra en la ubicación geográfica EUR:</span><span class="sxs-lookup"><span data-stu-id="aafa1-130">For example: To move OneDrive of user ‘Matt@contosoenergy.onmicrosoft.com’, connect to EUR SharePoint Admin center as the user’s OneDrive is in EUR geo location:</span></span>

`connect-sposervice -url https://contosoenergyeur-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations_image1.png)

## <a name="validating-the-environment"></a><span data-ttu-id="aafa1-131">Validación del entorno</span><span class="sxs-lookup"><span data-stu-id="aafa1-131">Validating the environment</span></span>

<span data-ttu-id="aafa1-132">Antes de iniciar la transferencia geográfica de OneDrive, se recomienda validar el entorno.</span><span class="sxs-lookup"><span data-stu-id="aafa1-132">Before you start a OneDrive geo move, we recommend that you validate the environment.</span></span>

<span data-ttu-id="aafa1-133">Para asegurarse de que todas las ubicaciones geográficas son compatibles, ejecute:</span><span class="sxs-lookup"><span data-stu-id="aafa1-133">To ensure that all geo locations are compatible, run:</span></span>

`Get-SPOGeoMoveCompatibilityStatus -AllLocations 1`

<span data-ttu-id="aafa1-p106">Si una instancia de OneDrive se encuentra en suspensión legal o contiene un subsitio no puede moverse. Puede usar el cmdlet Start-SPOUserAndContentMove cmdlet con el parámetro -ValidationOnly para validar si la instancia de OneDrive puede moverse:</span><span class="sxs-lookup"><span data-stu-id="aafa1-p106">If a OneDrive is under legal hold or if it contains a subsite, it cannot be moved. You can use the Start-SPOUserAndContentMove cmdlet with the -ValidationOnly parameter to validate if the OneDrive is able to be moved:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly`

<span data-ttu-id="aafa1-p107">Se devolverá Success si OneDrive está listo para moverse o Fail si hay una suspensión legal o un subsitio que impida el movimiento. Cuando haya validado que OneDrive está listo para moverse, puede iniciar el movimiento.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p107">This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.</span></span>

## <a name="start-a-onedrive-geo-move"></a><span data-ttu-id="aafa1-138">Iniciar una transferencia geográfica de OneDrive</span><span class="sxs-lookup"><span data-stu-id="aafa1-138">Start a OneDrive geo move</span></span>

<span data-ttu-id="aafa1-139">Para iniciar el movimiento, ejecute:</span><span class="sxs-lookup"><span data-stu-id="aafa1-139">To start the move, run:</span></span>  

`Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>`

<span data-ttu-id="aafa1-140">Con estos parámetros:</span><span class="sxs-lookup"><span data-stu-id="aafa1-140">Using these parameters:</span></span>

-   <span data-ttu-id="aafa1-141">_UserPrincipalName_: UPN del usuario cuya instancia de OneDrive se va a mover.</span><span class="sxs-lookup"><span data-stu-id="aafa1-141">_UserPrincipalName_ – UPN of the user whose OneDrive is being moved.</span></span>

-   <span data-ttu-id="aafa1-p108">_DestinationDataLocation_: ubicación geográfica a la que hay que mover OneDrive. Debe ser la ubicación de datos preferida del usuario.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p108">_DestinationDataLocation_ – Geo-Location where the OneDrive needs to be moved. This should be same as the user’s preferred data location.</span></span>

> [!NOTE]
> <span data-ttu-id="aafa1-144">Se recomienda ejecutar `Get-SPOGeoMoveStateCompatibility` con `ValidationOnly` antes de iniciar la transferencia geográfica de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="aafa1-144">We recommend running `Get-SPOGeoMoveStateCompatibility` with `ValidationOnly` prior to initiating OneDrive geo move.</span></span>

<span data-ttu-id="aafa1-145">Por ejemplo, para mover la instancia de OneDrive de matt@contosoenergy.onmicrosoft.com de EUR a AUS, ejecute:</span><span class="sxs-lookup"><span data-stu-id="aafa1-145">For example, to move the OneDrive of matt@contosoenergy.onmicrosoft.com from EUR to AUS, run:</span></span>

`Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS`

![](media/move-onedrive-between-geo-locations_image2.png)

<span data-ttu-id="aafa1-146">Para programar una transferencia geográfica para más adelante, use uno de los parámetros siguientes:</span><span class="sxs-lookup"><span data-stu-id="aafa1-146">To schedule a geo move for a later time, use one of the following parameters:</span></span>

-   <span data-ttu-id="aafa1-p109">_PreferredMoveBeginDate_: es probable que el movimiento se inicie a la hora especificada. La hora debe especificarse en la hora universal coordinada (UTC).</span><span class="sxs-lookup"><span data-stu-id="aafa1-p109">_PreferredMoveBeginDate_ – The move will likely begin at this specified time. Time must be specified in Coordinated Universal Time (UTC).</span></span>

-   <span data-ttu-id="aafa1-p110">_PreferredMoveEndDate_: es probable que el movimiento finalice antes de la hora especificada, sin garantía. La hora debe especificarse en la hora universal coordinada (UTC).</span><span class="sxs-lookup"><span data-stu-id="aafa1-p110">_PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).</span></span> 

## <a name="cancel-a-onedrive-geo-move"></a><span data-ttu-id="aafa1-151">Cancelar una transferencia geográfica de OneDrive</span><span class="sxs-lookup"><span data-stu-id="aafa1-151">Cancel a OneDrive geo move</span></span> 

<span data-ttu-id="aafa1-152">Para detener la transferencia geográfica de una instancia de OneDrive del usuario, siempre que el movimiento no esté en curso ni finalizado, use el cmdlet:</span><span class="sxs-lookup"><span data-stu-id="aafa1-152">You can stop the geo move of a user’s OneDrive, provided the move is not in progress or completed by using the cmdlet:</span></span>

`Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>`

<span data-ttu-id="aafa1-153">Donde _UserPrincipalName_ es el UPN del usuario cuyo movimiento de OneDrive se quiere detener.</span><span class="sxs-lookup"><span data-stu-id="aafa1-153">Where _UserPrincipalName_ is the UPN of the user whose OneDrive move you want to stop.</span></span>

## <a name="determining-current-status"></a><span data-ttu-id="aafa1-154">Determinación del estado actual</span><span class="sxs-lookup"><span data-stu-id="aafa1-154">Determining current status</span></span>

<span data-ttu-id="aafa1-155">Puede comprobar el estado de una transferencia geográfica de OneDrive desde o hasta la geoárea a la que esté conectado con el cmdlet Get-SPOUserAndContentMoveState.</span><span class="sxs-lookup"><span data-stu-id="aafa1-155">You can check the status of a OneDrive geo move in or out of the geo that you’re connected to by using the Get-SPOUserAndContentMoveState cmdlet.</span></span>

<span data-ttu-id="aafa1-156">Los estados del movimiento se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="aafa1-156">The fields in alerts are described in the following table.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="aafa1-157"><strong>Estado</strong></span><span class="sxs-lookup"><span data-stu-id="aafa1-157"><strong>Status</strong></span></span></th>
<th align="left"><span data-ttu-id="aafa1-158"><strong>Descripción</strong></span><span class="sxs-lookup"><span data-stu-id="aafa1-158"><strong>Description</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="aafa1-159">NotStarted</span><span class="sxs-lookup"><span data-stu-id="aafa1-159">NotStarted</span></span></td>
<td align="left"><span data-ttu-id="aafa1-160">No se ha iniciado el movimiento.</span><span class="sxs-lookup"><span data-stu-id="aafa1-160">The move has not started.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="aafa1-161">InProgress (<em>n</em>/4)</span><span class="sxs-lookup"><span data-stu-id="aafa1-161">InProgress (<em>n</em>/4)</span></span></td>
<td align="left"><span data-ttu-id="aafa1-162">El movimiento está en curso en uno de los siguientes estados: validación (1/4), copia de seguridad (2/4), restauración (3/4), limpieza (4/4).</span><span class="sxs-lookup"><span data-stu-id="aafa1-162">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="aafa1-163">Success</span><span class="sxs-lookup"><span data-stu-id="aafa1-163">Success</span></span></td>
<td align="left"><span data-ttu-id="aafa1-164">El movimiento se completó correctamente.</span><span class="sxs-lookup"><span data-stu-id="aafa1-164">The move has completed successfully.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="aafa1-165">Failed</span><span class="sxs-lookup"><span data-stu-id="aafa1-165">Failed</span></span></td>
<td align="left"><span data-ttu-id="aafa1-166">No se pudo realizar el movimiento.</span><span class="sxs-lookup"><span data-stu-id="aafa1-166">The move failed.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="aafa1-167">Para ver el estado del movimiento de un usuario específico, use el parámetro UserPrincipalName:</span><span class="sxs-lookup"><span data-stu-id="aafa1-167">To find the status of a specific user’s move, use the UserPrincipalName parameter:</span></span>

`Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>`

<span data-ttu-id="aafa1-168">Para buscar el estado de todos los movimientos desde o hasta la ubicación geográfica a la que está conectado, use el parámetro MoveState con uno de los siguientes valores: NotStarted, InProgress, Success, Failed, All.</span><span class="sxs-lookup"><span data-stu-id="aafa1-168">To find the status of all of the moves in or out of the geo location that you’re connected to, use the MoveState parameter with one of the following values: NotStarted, InProgress, Success, Failed, All.</span></span>

`Get-SPOUserAndContentMoveState -MoveState <value>`

<span data-ttu-id="aafa1-169">También puede agregar el parámetro `-Verbose` para obtener una descripción más detallada del estado del movimiento.</span><span class="sxs-lookup"><span data-stu-id="aafa1-169">You can also add the `-Verbose` parameter for more verbose descriptions of the move state.</span></span>

## <a name="user-experience"></a><span data-ttu-id="aafa1-170">Experiencia del usuario</span><span class="sxs-lookup"><span data-stu-id="aafa1-170">User Experience</span></span>

<span data-ttu-id="aafa1-p111">Los usuarios de OneDrive no deberían advertir ninguna interrupción si su instancia de OneDrive se mueve a otra ubicación geográfica. Excepto un breve estado de solo lectura durante el cambio, los vínculos y permisos existentes seguirán funcionando como se espera una vez completado el movimiento.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p111">Users of OneDrive should notice minimal disruption if their OneDrive is moved to a different geo location. Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="aafa1-173">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="aafa1-173">OneDrive for Business</span></span>

<span data-ttu-id="aafa1-p112">Mientras se realiza el movimiento, el estado de OneDrive del usuario se establece en solo lectura. Una vez completado el movimiento, el usuario se dirigirá a su OneDrive en la nueva ubicación geográfica cuando navegue a OneDrive, el iniciador de aplicaciones de Office 365 o un explorador web.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p112">While the move is in progress the user’s OneDrive is set to read-only. Once the move is completed, the user is directed to their OneDrive in the new geo location when they navigate to OneDrive the Office 365 app launcher or a web browser.</span></span>

### <a name="permissions-on-onedrive-content"></a><span data-ttu-id="aafa1-176">Permisos en contenido de OneDrive</span><span class="sxs-lookup"><span data-stu-id="aafa1-176">Permissions on OneDrive content</span></span>

<span data-ttu-id="aafa1-177">Los usuarios con permisos de contenido de OneDrive seguirán teniendo acceso al contenido durante el movimiento y después de su finalización.</span><span class="sxs-lookup"><span data-stu-id="aafa1-177">Users with permissions to OneDrive content will continue to have access to the content during the move and after it’s complete.</span></span>

### <a name="onedrive-sync-client"></a><span data-ttu-id="aafa1-178">Cliente de sincronización de OneDrive</span><span class="sxs-lookup"><span data-stu-id="aafa1-178">OneDrive Sync Client</span></span> 

<span data-ttu-id="aafa1-p113">El cliente de sincronización de OneDrive detectará automáticamente la sincronización y la transferirá de forma fluida a la nueva ubicación de OneDrive cuando se haya completado el movimiento geográfico de OneDrive. El usuario no tiene que volver a iniciar la sesión ni realizar ninguna otra acción. (Se necesita la versión 17.3.6943.0625 o posteriores del cliente de sincronización).</span><span class="sxs-lookup"><span data-stu-id="aafa1-p113">The OneDrive sync client will automatically detect and seamlessly transfer syncing to the new OneDrive location once the OneDrive geo move is complete. The user does not need to sign-in again or take any other action.  (Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="aafa1-182">Si un usuario actualiza un archivo mientras el movimiento geográfico de OneDrive está en curso, el cliente de sincronización le notificará que hay cargas de archivos pendientes mientras el movimiento está en curso.</span><span class="sxs-lookup"><span data-stu-id="aafa1-182">If a user updates a file while the OneDrive geo move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="aafa1-183">Vínculos de uso compartido</span><span class="sxs-lookup"><span data-stu-id="aafa1-183">Sharing links</span></span> 

<span data-ttu-id="aafa1-184">Tras la finalización de la transferencia geográfica de OneDrive, los vínculos compartidos existentes a los archivos que se movieron se redirigirán automáticamente a la nueva ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="aafa1-184">Upon OneDrive geo move completion, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="aafa1-185">Experiencia de OneNote</span><span class="sxs-lookup"><span data-stu-id="aafa1-185">OneNote Experience</span></span> 

<span data-ttu-id="aafa1-p114">El cliente OneNote win32 y la aplicación UWP (Universal) detectarán automáticamente los blocs de notas y los sincronizarán perfectamente con la nueva ubicación de OneDrive cuando se haya completado la transferencia geográfica de OneDrive. El usuario no tiene que volver a iniciar sesión ni realizar ninguna otra acción. El único indicador visible para el usuario sería un error de sincronización de blocs de notas cuando la transferencia geográfica de OneDrive está en curso. Esta experiencia está disponible en las siguientes versiones de cliente OneNote:</span><span class="sxs-lookup"><span data-stu-id="aafa1-p114">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new OneDrive location once OneDrive geo move is complete. The user does not need to sign-in again or take any other action. The only visible indicator to the user is notebook sync would fail when OneDrive geo move is in progress. This experience is available on the following OneNote client versions:</span></span>

-   <span data-ttu-id="aafa1-190">OneNote win32. versión 16.0.8326.2096 (y versiones posteriores)</span><span class="sxs-lookup"><span data-stu-id="aafa1-190">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>

-   <span data-ttu-id="aafa1-191">OneNote UWP: versión 16.0.8431.1006 (y versiones posteriores)</span><span class="sxs-lookup"><span data-stu-id="aafa1-191">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>

-   <span data-ttu-id="aafa1-192">Aplicación móvil de OneNote (versión 16.0.8431.1011 y versiones posteriores)</span><span class="sxs-lookup"><span data-stu-id="aafa1-192">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-app"></a><span data-ttu-id="aafa1-193">Aplicación de Teams</span><span class="sxs-lookup"><span data-stu-id="aafa1-193">Teams app</span></span>

<span data-ttu-id="aafa1-p115">Tras la finalización de la transferencia geográfica de OneDrive, los usuarios tendrán acceso a sus archivos de OneDrive en la aplicación de Teams. Además, los archivos compartidos a través de chats de Teams desde su instancia de OneDrive anteriores a la transferencia geográfica seguirán funcionando tras completar el movimiento.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p115">Upon OneDrive geo move completion, users will have access to their OneDrive files on the Teams app. Additionally, files shared via Teams chat from their OneDrive prior to geo move will continue to work after move is complete.</span></span>

### <a name="onedrive-for-business-mobile-app-ios"></a><span data-ttu-id="aafa1-196">Aplicación móvil de OneDrive para la Empresa (iOS)</span><span class="sxs-lookup"><span data-stu-id="aafa1-196">OneDrive for Business Mobile App (iOS)</span></span> 

<span data-ttu-id="aafa1-197">Tras la finalización de la transferencia geográfica de OneDrive, el usuario tendría que cerrar sesión e iniciarla de nuevo en la aplicación para dispositivos móviles iOS a fin de sincronizarla con la nueva ubicación de OneDrive.</span><span class="sxs-lookup"><span data-stu-id="aafa1-197">Upon OneDrive geo move completion, the user would need to sign out and sign in again on the iOS Mobile App to sync to the new OneDrive location.</span></span>

### <a name="existing-followed-groups-and-sites"></a><span data-ttu-id="aafa1-198">Sitios y grupos seguidos existentes</span><span class="sxs-lookup"><span data-stu-id="aafa1-198">Existing followed groups and sites</span></span>

<span data-ttu-id="aafa1-p116">Los sitios y grupos seguidos se mostrarán en la instancia de OneDrive del usuario independientemente de su ubicación geográfica. Los sitios y grupos hospedados en otra ubicación geográfica se abrirán en una pestaña aparte.</span><span class="sxs-lookup"><span data-stu-id="aafa1-p116">Followed sites and groups will show up in the user's OneDrive for business regardless of their geo location. Sites and Groups hosted in another geo location will open in a separate tab.</span></span>
