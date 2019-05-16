---
title: Mover un sitio de SharePoint a otra ubicación geográfica (versión preliminar)
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Aprenda a mover un sitio de OneDrive a otra ubicación geográfica
ms.openlocfilehash: 74a1ccf7dcfa60d74135211d7b74a2e7096d09b0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070116"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location-preview"></a><span data-ttu-id="07275-103">Mover un sitio de SharePoint a otra ubicación geográfica (versión preliminar)</span><span class="sxs-lookup"><span data-stu-id="07275-103">Move a SharePoint site to a different geo location (Preview)</span></span>

<span data-ttu-id="07275-104">Con el movimiento geográfico de sitios de SharePoint, puede mover dichos sitios a otras ubicaciones geográficas dentro de su entorno multigeográfico. </span><span class="sxs-lookup"><span data-stu-id="07275-104">With SharePoint site geo move, you can move SharePoint sites to other geo locations within your multi-geo environment.</span></span> <span data-ttu-id="07275-105">Esta característica está disponible actualmente en versión preliminar.</span><span class="sxs-lookup"><span data-stu-id="07275-105">This feature is currently in preview.</span></span>

<span data-ttu-id="07275-106">Los siguientes tipos de sitios pueden moverse entre ubicaciones geográficas:</span><span class="sxs-lookup"><span data-stu-id="07275-106">The following types of site can be moved between geo locations:</span></span>

- <span data-ttu-id="07275-107">Sitios conectados a Grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="07275-107">Office 365 Group-connected sites</span></span>
- <span data-ttu-id="07275-108">Sitios modernos sin ninguna asociación con los Grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="07275-108">Modern sites without an Office 365 Group association</span></span>
- <span data-ttu-id="07275-109">Sitios clásicos de SharePoint</span><span class="sxs-lookup"><span data-stu-id="07275-109">Classic SharePoint sites</span></span>
- <span data-ttu-id="07275-110">Sitios de comunicación</span><span class="sxs-lookup"><span data-stu-id="07275-110">Communication sites</span></span>

<span data-ttu-id="07275-111">Debe ser un administrador global o un administrador de SharePoint para mover un sitio entre ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="07275-111">You must be a Global Administrator or SharePoint Administrator to move a site between geo locations.</span></span>

<span data-ttu-id="07275-112">Hay una ventana de solo lectura durante el movimiento geográfico de sitios de SharePoint de aproximadamente 4 a 6 horas, según el contenido del sitio.</span><span class="sxs-lookup"><span data-stu-id="07275-112">There is a read-only window during the SharePoint site geo move of approximately 4-6 hours, depending on site contents.</span></span>
 
## <a name="best-practices"></a><span data-ttu-id="07275-113">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="07275-113">Best practices</span></span>

- <span data-ttu-id="07275-114">Pruebe un movimiento del sitio de SharePoint en un sitio de prueba para familiarizarse con el procedimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-114">Try a SharePoint site move on a test site to get familiar with the procedure.</span></span> 
- <span data-ttu-id="07275-115">Compruebe si el sitio se puede mover antes de programar o realizar el cambio.</span><span class="sxs-lookup"><span data-stu-id="07275-115">Validate whether the site can be moved prior to scheduling or performing the move.</span></span> 
- <span data-ttu-id="07275-116">Cuando sea posible, programe movimientos de sitios entre ubicaciones geográficas fuera del horario laboral para reducir el impacto con el usuario.</span><span class="sxs-lookup"><span data-stu-id="07275-116">When possible schedule cross-geo sites moves for outside business hours to reduce user impact.</span></span>
- <span data-ttu-id="07275-117">Comuníquese con los usuarios afectados antes del movimiento de sitios.</span><span class="sxs-lookup"><span data-stu-id="07275-117">Communicate with impacted users prior to the sites move.</span></span> 

## <a name="communicating-to-your-users"></a><span data-ttu-id="07275-118">Comunicación con los usuarios</span><span class="sxs-lookup"><span data-stu-id="07275-118">Communicating to your users</span></span>

<span data-ttu-id="07275-119">Es importante comunicar el resultado esperado a los usuarios de los sitios (generalmente los que pueden editarlos), al migrar los sitios de SharePoint entre ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="07275-119">When moving SharePoint sites between geo locations, it's important to communicate to the sites' users (generally anyone with the ability to edit the site) what to expect.</span></span> <span data-ttu-id="07275-120">Esto puede ayudar a reducir la confusión de los usuarios y las llamadas a su departamento de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="07275-120">This can help reduce user confusion and calls to your help desk.</span></span> <span data-ttu-id="07275-121">Envíe un correo a los usuarios antes de mover los sitios e infórmeles de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="07275-121">Email your sites' users before the move and let them know the following information:</span></span>

- <span data-ttu-id="07275-122">Cuándo se espera que inicie el movimiento y cuánto tiempo se espera que tarde en completarse.</span><span class="sxs-lookup"><span data-stu-id="07275-122">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="07275-123">La ubicación geográfica de destino para el sitio y la dirección URL para obtener acceso a la nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="07275-123">What geo location their site is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="07275-124">Necesitan cerrar sus archivos sin realizar ediciones durante el desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="07275-124">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="07275-125">Los permisos de archivo y el uso compartido no cambiará como resultado del movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-125">File permissions and sharing will not change because of the move.</span></span>
- <span data-ttu-id="07275-126">Acciones previstas de la experiencia del usuario en un entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="07275-126">What to expect from the user experience in a multi-geo environment</span></span>

<span data-ttu-id="07275-127">Asegúrese de enviar a los usuarios un correo electrónico cuando se complete correctamente el movimiento para informarles de que pueden reanudar su trabajo en los sitios.</span><span class="sxs-lookup"><span data-stu-id="07275-127">Be sure to send your sites' users an email when the move has successfully completed informing them that they can resume working on their sites.</span></span>

## <a name="scheduling-sharepoint-site-moves"></a><span data-ttu-id="07275-128">Programación de movimientos de sitios de SharePoint </span><span class="sxs-lookup"><span data-stu-id="07275-128">Scheduling SharePoint site moves</span></span>

<span data-ttu-id="07275-129">Puede programar los movimientos de sitios de SharePoint por adelantado (como se describe más adelante en este artículo).</span><span class="sxs-lookup"><span data-stu-id="07275-129">You can schedule SharePoint site moves in advance (described later in this article).</span></span> <span data-ttu-id="07275-130">Puede programar los movimientos como sigue:</span><span class="sxs-lookup"><span data-stu-id="07275-130">You can schedule moves as follows:</span></span>

- <span data-ttu-id="07275-131">Puede programar un máximo de 4000 movimientos cada vez.</span><span class="sxs-lookup"><span data-stu-id="07275-131">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="07275-132">Al empezar el movimiento, puede programar más, con un máximo de 4000 movimientos pendientes en la cola y en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="07275-132">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
 
<span data-ttu-id="07275-133">Para programar un movimiento geográfico de sitio de SharePoint para un momento posterior, incluya uno de los parámetros siguiente al iniciar:</span><span class="sxs-lookup"><span data-stu-id="07275-133">To schedule a SharePoint site geo move for a later time, include one of the following parameters when you start the move:</span></span>
- <span data-ttu-id="07275-134">`PreferredMoveBeginDate`: Es probable que se inicie el cambio en este momento especificado.</span><span class="sxs-lookup"><span data-stu-id="07275-134">`PreferredMoveBeginDate` – The move will likely begin at this specified time.</span></span>
- <span data-ttu-id="07275-135">`PreferredMoveEndDate`: Es probable que se complete el movimiento dentro de este tiempo especificado, en el mejor de los casos.</span><span class="sxs-lookup"><span data-stu-id="07275-135">`PreferredMoveEndDate` – The move will likely be completed by this specified time, on a best effort basis.</span></span> 

<span data-ttu-id="07275-136">La hora para ambos parámetros debe especificarse según el Tiempo universal coordinado (UTC).</span><span class="sxs-lookup"><span data-stu-id="07275-136">Time must be specified in Coordinated Universal Time (UTC) for both parameters.</span></span>

## <a name="moving-the-site"></a><span data-ttu-id="07275-137">Mover el sitio</span><span class="sxs-lookup"><span data-stu-id="07275-137">Moving the site</span></span>

<span data-ttu-id="07275-138">El movimiento geográfico del sitio de SharePoint requiere que se conecte y se realice desde la URL del administrador de SharePoint en la ubicación geográfica donde se encuentra el sitio.</span><span class="sxs-lookup"><span data-stu-id="07275-138">SharePoint site geo move requires that you connect and perform the move from the SharePoint Admin URL in the geo location where the site is.</span></span>

<span data-ttu-id="07275-139">Por ejemplo, si la URL del sitio es https://contosohealthcare.sharepoint.com/sites/Turbines, conéctese a la URL del administrador de SharePoint en https://contosohealthcare-admin.sharepoint.com:</span><span class="sxs-lookup"><span data-stu-id="07275-139">For example, if the site URL is https://contosohealthcare.sharepoint.com/sites/Turbines, connect to the SharePoint Admin URL at https://contosohealthcare-admin.sharepoint.com:</span></span>

`connect-sposervice -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a><span data-ttu-id="07275-140">Validación del entorno</span><span class="sxs-lookup"><span data-stu-id="07275-140">Validating the environment</span></span>

<span data-ttu-id="07275-141">Se recomienda realizar una comprobación para asegurarse de que se puede mover el sitio, antes de programar su movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-141">We recommend that before scheduling any site move, you perform a validation to ensure that the site can be moved.</span></span>

<span data-ttu-id="07275-142">No se admite mover sitios con:</span><span class="sxs-lookup"><span data-stu-id="07275-142">We do not support moving sites with:</span></span>
-   <span data-ttu-id="07275-143">Servicios de conectividad empresarial</span><span class="sxs-lookup"><span data-stu-id="07275-143">Business Connectivity Services</span></span>
-   <span data-ttu-id="07275-144">Formularios de InfoPath</span><span class="sxs-lookup"><span data-stu-id="07275-144">InfoPath forms</span></span> 

<span data-ttu-id="07275-145">Para asegurarse de que todas las ubicaciones geográficas son compatibles, ejecute `Get-SPOGeoMoveCrossCompatibilityStatus`.</span><span class="sxs-lookup"><span data-stu-id="07275-145">To ensure all geo locations are compatible, run `Get-SPOGeoMoveCrossCompatibilityStatus`.</span></span> <span data-ttu-id="07275-146">Esto mostrará todas las ubicaciones geográficas y si el entorno es compatible con la ubicación geográfica de destino.</span><span class="sxs-lookup"><span data-stu-id="07275-146">This will display all your geo locations and whether the environment is compatible with the destination geo location.</span></span>

<span data-ttu-id="07275-147">Para realizar una comprobación de validación en el sitio, use `Start-SPOSiteContentMove` con el parámetro `-ValidationOnly` para comprobar si el sitio se puede mover.</span><span class="sxs-lookup"><span data-stu-id="07275-147">To perform a validation-only check on your site, use `Start-SPOSiteContentMove` with the `-ValidationOnly` parameter to validate if the site is able to be moved.</span></span> <span data-ttu-id="07275-148">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="07275-148">For example:</span></span>

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

<span data-ttu-id="07275-149">Esto devolverá *Success* si el sitio está listo para moverse o *Fail* si hay algunas condiciones bloqueadas.</span><span class="sxs-lookup"><span data-stu-id="07275-149">This will return *Success* if the site is ready to be moved or *Fail* if any of blocked conditions are present.</span></span>

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a><span data-ttu-id="07275-150">Iniciar un movimiento geográfico de sitios de SharePoint con sitios sin ninguna asociación con los Grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="07275-150">Start a SharePoint site geo move for a site with no associated Office 365 Group</span></span>

<span data-ttu-id="07275-151">De forma predeterminada, se cambiará la dirección URL inicial del sitio a la dirección URL de la ubicación geográfica de destino.</span><span class="sxs-lookup"><span data-stu-id="07275-151">By default, initial URL for the site will change to the URL of the destination geo location.</span></span> <span data-ttu-id="07275-152">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="07275-152">For example:</span></span>

<span data-ttu-id="07275-153">https://Contoso.sharepoint.com/sites/projectx a https://Contoso.sharepointEUR.com/sites/projectx</span><span class="sxs-lookup"><span data-stu-id="07275-153">https://Contoso.sharepoint.com/sites/projectx to https://Contoso.sharepointEUR.com/sites/projectx</span></span>

<span data-ttu-id="07275-154">Los sitios sin ninguna asociación con los Grupos de Office 365, también pueden cambiar el nombre mediante el parámetro `-DestinationUrl`.</span><span class="sxs-lookup"><span data-stu-id="07275-154">For sites with no Office 365 Group association, you can also rename the site by using the `-DestinationUrl` parameter.</span></span> <span data-ttu-id="07275-155">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="07275-155">For example:</span></span>

<span data-ttu-id="07275-156">https://Contoso.sharepoint.com/sites/projectx a https://Contoso.sharepointEUR.com/sites/projecty</span><span class="sxs-lookup"><span data-stu-id="07275-156">https://Contoso.sharepoint.com/sites/projectx to https://Contoso.sharepointEUR.com/sites/projecty</span></span>

<span data-ttu-id="07275-157">Para iniciar el movimiento del sitio, ejecute:</span><span class="sxs-lookup"><span data-stu-id="07275-157">To start the site move, run:</span></span>

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Captura de pantalla de la ventana de PowerShell que muestra el cmdlet Start-SPOSiteContentMove](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a><span data-ttu-id="07275-159">Iniciar el movimiento geográfico de sitios de SharePoint con sitios conectados a Grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="07275-159">Start a SharePoint site geo move for an Office 365 Group-connected site</span></span>

<span data-ttu-id="07275-160">Para mover un sitio conectado a grupos de Office 365, primero el administrador global debe cambiar el atributo de ubicación de datos preferida (PDL) del Grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="07275-160">To move an Office 365 Group-connected site, the global administrator must first change the Preferred Data Location (PDL) attribute for the Office 365 Group.</span></span>

<span data-ttu-id="07275-161">Para establecer la PDL de un Grupo de Office 365:</span><span class="sxs-lookup"><span data-stu-id="07275-161">To set the PDL for an Office 365 Group:</span></span>

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
<span data-ttu-id="07275-162">Una vez que haya actualizado la PDL, puede iniciar el movimiento del sitio:</span><span class="sxs-lookup"><span data-stu-id="07275-162">Once you have updated the PDL, you can start the site move:</span></span> 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a><span data-ttu-id="07275-163">Cancelar un movimiento geográfico de sitios de SharePoint</span><span class="sxs-lookup"><span data-stu-id="07275-163">Cancel a SharePoint site geo move</span></span>

<span data-ttu-id="07275-164">Puede detener un movimiento geográfico de sitios de SharePoint, siempre que el movimiento no esté en curso ni se haya finalizado, mediante el cmdlet `Stop-SPOSiteContentMove`.</span><span class="sxs-lookup"><span data-stu-id="07275-164">You can stop a SharePoint site geo move, provided the move is not in progress or completed by using the `Stop-SPOSiteContentMove` cmdlet.</span></span>

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a><span data-ttu-id="07275-165">Determinar el estado de un movimiento geográfico de sitios de SharePoint</span><span class="sxs-lookup"><span data-stu-id="07275-165">Determining the status of a SharePoint site geo move</span></span>

<span data-ttu-id="07275-166">Puede determinar el estado de un movimiento de sitios dentro y fuera de la ubicación geográfica a la que está conectado mediante los siguientes cmdlet:</span><span class="sxs-lookup"><span data-stu-id="07275-166">You can determine the status of a site move in our out of the geo that you are connected to by using the following cmdlets:</span></span>

- <span data-ttu-id="07275-167">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (sitios no conectados al grupo)</span><span class="sxs-lookup"><span data-stu-id="07275-167">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (non-Group-connected sites)</span></span>
- <span data-ttu-id="07275-168">Get-SPOUnifiedGroupMoveState (sitios conectados al grupo)</span><span class="sxs-lookup"><span data-stu-id="07275-168">Get-SPOUnifiedGroupMoveState (Group-connected sites)</span></span>

<span data-ttu-id="07275-169">Use el parámetro `-SourceSiteUrl` para especificar el sitio del que quiere ver el estado del movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-169">Use the `-SourceSiteUrl` parameter to specify the site for which you want to see move status.</span></span>

<span data-ttu-id="07275-170">Los estados del movimiento se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="07275-170">The move statuses are described in the following table.</span></span>

|<span data-ttu-id="07275-171">Estado</span><span class="sxs-lookup"><span data-stu-id="07275-171">Status</span></span>|<span data-ttu-id="07275-172">Descripción</span><span class="sxs-lookup"><span data-stu-id="07275-172">Description</span></span>|
|:-----|:----------|
|<span data-ttu-id="07275-173">Ready to Trigger</span><span class="sxs-lookup"><span data-stu-id="07275-173">Ready to Trigger</span></span>|<span data-ttu-id="07275-174">No se ha iniciado el movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-174">The move has not started.</span></span>|
|<span data-ttu-id="07275-175">Scheduled</span><span class="sxs-lookup"><span data-stu-id="07275-175">Scheduled</span></span>|<span data-ttu-id="07275-176">El movimiento está en cola, pero todavía no se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="07275-176">The move is in queue but has not yet started.</span></span>|
|<span data-ttu-id="07275-177">InProgress (n/4)</span><span class="sxs-lookup"><span data-stu-id="07275-177">InProgress (n/4)</span></span>|<span data-ttu-id="07275-178">El movimiento está en curso en uno de los siguientes estados: validación (1/4), copia de seguridad (2/4), restauración (3/4), limpieza (4/4).</span><span class="sxs-lookup"><span data-stu-id="07275-178">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span>|
|<span data-ttu-id="07275-179">Success</span><span class="sxs-lookup"><span data-stu-id="07275-179">Success</span></span>|<span data-ttu-id="07275-180">El movimiento se completó correctamente.</span><span class="sxs-lookup"><span data-stu-id="07275-180">The move has completed successfully.</span></span>|
|<span data-ttu-id="07275-181">Failed</span><span class="sxs-lookup"><span data-stu-id="07275-181">Failed</span></span>|<span data-ttu-id="07275-182">No se pudo realizar el movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-182">The move failed.</span></span>|

<span data-ttu-id="07275-183">También puede aplicar la opción `-Verbose` para ver información adicional sobre el movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-183">You can also apply the `-Verbose` option to see additional information about the move.</span></span>

## <a name="user-experience"></a><span data-ttu-id="07275-184">Experiencia del usuario</span><span class="sxs-lookup"><span data-stu-id="07275-184">User experience</span></span>

<span data-ttu-id="07275-185">Los usuarios del sitio deben notar una interrupción mínima al mover su sitio a otra ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="07275-185">Site users should notice minimal disruption when their site is moved to a different geo location.</span></span> <span data-ttu-id="07275-186">Excepto un estado breve de solo lectura durante el movimiento, los permisos y los vínculos existentes seguirán funcionando como se espera una vez completado el proceso.</span><span class="sxs-lookup"><span data-stu-id="07275-186">Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="site"></a><span data-ttu-id="07275-187">Sitio</span><span class="sxs-lookup"><span data-stu-id="07275-187">Site</span></span>

<span data-ttu-id="07275-188">Mientras se realiza el movimiento, el sitio está configurado como de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="07275-188">While the move is in progress the site is set to read-only.</span></span> <span data-ttu-id="07275-189">Una vez completado el movimiento, se dirige al usuario al sitio nuevo en la nueva ubicación geográfica al hacer clic en los marcadores u en otros vínculos del sitio.</span><span class="sxs-lookup"><span data-stu-id="07275-189">Once the move is completed, the user is directed to the new site in the new geo location when they click on bookmarks or other links to the site.</span></span>

### <a name="permissions"></a><span data-ttu-id="07275-190">Permisos</span><span class="sxs-lookup"><span data-stu-id="07275-190">Permissions</span></span>

<span data-ttu-id="07275-191">Los usuarios con permisos al sitio seguirán teniendo acceso durante el movimiento y después de su finalización.</span><span class="sxs-lookup"><span data-stu-id="07275-191">Users with permissions to site will continue to have access to the site during the move and after it's complete.</span></span>

### <a name="sync-client"></a><span data-ttu-id="07275-192">Cliente de sincronización</span><span class="sxs-lookup"><span data-stu-id="07275-192">Sync Client</span></span>

<span data-ttu-id="07275-193">El cliente de sincronización detectará automáticamente y transferirá fácilmente la sincronización con la nueva ubicación de sitio, una vez completado el movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-193">The sync client will automatically detect and seamlessly transfer syncing to the new site location once the site move is complete.</span></span> <span data-ttu-id="07275-194">El usuario no necesitará volver a iniciar sesión ni realizar ninguna otra acción.</span><span class="sxs-lookup"><span data-stu-id="07275-194">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="07275-195">(Se requiere la versión 17.3.6943.0625 o posterior del cliente de sincronización).</span><span class="sxs-lookup"><span data-stu-id="07275-195">(Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="07275-196">Si un usuario actualiza un archivo mientras el movimiento está en curso, el cliente de sincronización le notificará que hay cargas de archivos pendientes mientras el movimiento está en curso.</span><span class="sxs-lookup"><span data-stu-id="07275-196">If a user updates a file while the move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="07275-197">Vínculos de uso compartido</span><span class="sxs-lookup"><span data-stu-id="07275-197">Sharing links</span></span>

<span data-ttu-id="07275-198">Tras la finalización del movimiento geográfico de sitios de SharePoint, los vínculos compartidos existentes de los archivos que se movieron se redirigirán automáticamente a la nueva ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="07275-198">When the SharePoint site geo move completes, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="most-recently-used-files-in-office-mru"></a><span data-ttu-id="07275-199">Los archivos usados recientemente de Office (MRU)</span><span class="sxs-lookup"><span data-stu-id="07275-199">Most Recently Used files in Office (MRU)</span></span>

<span data-ttu-id="07275-200">El servicio MRU se actualiza con la dirección URL del sitio y sus direcciones URL de contenido cuando se complete el movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-200">The MRU service is updated with the site url and its content URLs once the move completes.</span></span> <span data-ttu-id="07275-201">Eso se aplica a Word, Excel y PowerPoint</span><span class="sxs-lookup"><span data-stu-id="07275-201">This applies to Word, Excel, and PowerPoint.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="07275-202">Experiencia de OneNote</span><span class="sxs-lookup"><span data-stu-id="07275-202">OneNote experience</span></span>

<span data-ttu-id="07275-203">El cliente de win32 de OneNote y la aplicación UWP (Universal) detectarán automáticamente y sincronizarán perfectamente blocs de notas con la nueva ubicación del sitio cuando se complete el movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-203">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new site location once site move is complete.</span></span> <span data-ttu-id="07275-204">El usuario no necesitará volver a iniciar sesión ni realizar ninguna otra acción.</span><span class="sxs-lookup"><span data-stu-id="07275-204">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="07275-205">El único indicador visible para el usuario es que la sincronización de la notebook fallaría cuando el movimiento del sitio esté en curso.</span><span class="sxs-lookup"><span data-stu-id="07275-205">The only visible indicator to the user is notebook sync would fail when site move is in progress.</span></span> <span data-ttu-id="07275-206">Esta experiencia está disponible en las siguientes versiones de cliente de OneNote:</span><span class="sxs-lookup"><span data-stu-id="07275-206">This experience is available on the following OneNote client versions:</span></span>

- <span data-ttu-id="07275-207">OneNote win32. versión 16.0.8326.2096 (y versiones posteriores)</span><span class="sxs-lookup"><span data-stu-id="07275-207">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>
- <span data-ttu-id="07275-208">OneNote UWP: versión 16.0.8431.1006 (y versiones posteriores)</span><span class="sxs-lookup"><span data-stu-id="07275-208">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>
- <span data-ttu-id="07275-209">Aplicación móvil de OneNote (versión 16.0.8431.1011 y versiones posteriores)</span><span class="sxs-lookup"><span data-stu-id="07275-209">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-applicable-to-office-365-group-connected-sites"></a><span data-ttu-id="07275-210">Teams (se aplica a los sitios conectados al Grupo de Office 365)</span><span class="sxs-lookup"><span data-stu-id="07275-210">Teams (applicable to Office 365 Group connected sites)</span></span>

<span data-ttu-id="07275-211">Cuando se complete el movimiento geográfico de sitios de SharePoint, los usuarios tendrán acceso a sus archivos de sitio de Grupo de Office 365 en la aplicación de Teams.</span><span class="sxs-lookup"><span data-stu-id="07275-211">When the SharePoint site geo move completes, users will have access to their Office 365 Group site files on the Teams app.</span></span> <span data-ttu-id="07275-212">Además, los archivos compartidos mediante chat de Teams desde el sitio, antes del movimiento geográfico, seguirán funcionando tras completar el mismo.</span><span class="sxs-lookup"><span data-stu-id="07275-212">Additionally, files shared via Teams chat from their site prior to geo move will continue to work after move is complete.</span></span>

### <a name="sharepoint-mobile-app-iosandroid"></a><span data-ttu-id="07275-213">Aplicación móvil de SharePoint para Android y iOS</span><span class="sxs-lookup"><span data-stu-id="07275-213">SharePoint Mobile App (iOS/Android)</span></span>

<span data-ttu-id="07275-214">Se admite la aplicación móvil de SharePoint entre las zonas geográficas y podrá detectar la nueva ubicación geográfica del sitio.</span><span class="sxs-lookup"><span data-stu-id="07275-214">The SharePoint Mobile App is cross geo compatible and able to detect the site's new geo location.</span></span>

### <a name="sharepoint-workflows"></a><span data-ttu-id="07275-215">Flujos de trabajo de SharePoint</span><span class="sxs-lookup"><span data-stu-id="07275-215">SharePoint workflows</span></span>

<span data-ttu-id="07275-216">Los flujos de trabajo de SharePoint 2013 deben volver a publicarse después de mover el sitio.</span><span class="sxs-lookup"><span data-stu-id="07275-216">SharePoint 2013 workflows need to be republished after the site move.</span></span> <span data-ttu-id="07275-217">Los flujos de trabajo de SharePoint 2010 deberían seguir funcionando con normalidad.</span><span class="sxs-lookup"><span data-stu-id="07275-217">SharePoint 2010 workflows should continue to function normally.</span></span>

### <a name="apps"></a><span data-ttu-id="07275-218">Aplicaciones</span><span class="sxs-lookup"><span data-stu-id="07275-218">Apps</span></span>

<span data-ttu-id="07275-219">Si se mueve un sitio con aplicaciones, debe volver a crear instancias de aplicación en la nueva ubicación geográfica del sitio, ya que es posible que la aplicación y sus conexiones no estén disponibles en la ubicación geográfica de destino.</span><span class="sxs-lookup"><span data-stu-id="07275-219">If you are moving a site with apps, you must re-instantiate the app in the site's new geo location as the app and its connections may not be available in the destination geo location.</span></span>

### <a name="flow"></a><span data-ttu-id="07275-220">Flow</span><span class="sxs-lookup"><span data-stu-id="07275-220">Flow</span></span>

<span data-ttu-id="07275-221">En la mayoría de los casos los flujos seguirán funcionando después de mover geográficamente el sitio de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="07275-221">In most cases Flows will continue to work after a SharePoint site geo move.</span></span> <span data-ttu-id="07275-222">Se recomienda probarlos una vez completado el movimiento.</span><span class="sxs-lookup"><span data-stu-id="07275-222">We recommend that you test them once the move has completed.</span></span>

### <a name="powerapps"></a><span data-ttu-id="07275-223">PowerApps</span><span class="sxs-lookup"><span data-stu-id="07275-223">PowerApps</span></span>

<span data-ttu-id="07275-224">PowerApps debe volver a crearse en la ubicación de destino.</span><span class="sxs-lookup"><span data-stu-id="07275-224">PowerApps need to be recreated in the destination location.</span></span>

### <a name="data-movement-between-geo-locations"></a><span data-ttu-id="07275-225">Mover datos entre ubicaciones geográficas</span><span class="sxs-lookup"><span data-stu-id="07275-225">Data movement between geo locations</span></span>

<span data-ttu-id="07275-226">SharePoint usa el Azure Blob Storage para su contenido, mientras los metadatos asociados con los sitios y los archivos se almacenan dentro de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="07275-226">SharePoint uses Azure Blob storage for its content, while the metadata associated with sites and its files is stored within SharePoint.</span></span> <span data-ttu-id="07275-227">Cuando el sitio se mueve de su ubicación geográfica de origen a la de destino, el servicio también moverá el Blob Storage asociado. </span><span class="sxs-lookup"><span data-stu-id="07275-227">After the site is moved from its source geo location to its destination geo location, the service will also move its associated Blob Storage.</span></span> <span data-ttu-id="07275-228">El movimiento de Blob Storage se completa en aproximadamente 40 días.</span><span class="sxs-lookup"><span data-stu-id="07275-228">Blob Storage moves complete in approximately 40 days.</span></span> 
