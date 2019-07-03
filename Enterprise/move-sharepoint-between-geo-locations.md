---
title: 'Mover un sitio SharePoint a otra ubicación geográfica '
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Aprenda a mover un sitio de OneDrive a otra ubicación geográfica
ms.openlocfilehash: f1837942a72881578930f94ad8c4b57dbdb0c649
ms.sourcegitcommit: 59c250b5f62e72fb51fd0b80d2be636ee8078f6b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2019
ms.locfileid: "35422379"
---
# <a name="move-a-sharepoint-site-to-a-different-geo-location"></a><span data-ttu-id="18a16-103">Mover un sitio SharePoint a otra ubicación geográfica </span><span class="sxs-lookup"><span data-stu-id="18a16-103">Move a SharePoint site to a different geo location (Preview)</span></span>

<span data-ttu-id="18a16-104">Con el movimiento geográfico de sitios de SharePoint, puede mover dichos sitios a otras ubicaciones geográficas dentro de su entorno multigeográfico. </span><span class="sxs-lookup"><span data-stu-id="18a16-104">With SharePoint site geo move, you can move SharePoint sites to other geo locations within your multi-geo environment.</span></span>

<span data-ttu-id="18a16-105">Los siguientes tipos de sitios pueden moverse entre ubicaciones geográficas:</span><span class="sxs-lookup"><span data-stu-id="18a16-105">The following types of site can be moved between geo locations:</span></span>

- <span data-ttu-id="18a16-106">Sitios conectados a Grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="18a16-106">Office 365 Group-connected sites</span></span>
- <span data-ttu-id="18a16-107">Sitios modernos sin ninguna asociación con los Grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="18a16-107">Modern sites without an Office 365 Group association</span></span>
- <span data-ttu-id="18a16-108">Sitios clásicos de SharePoint</span><span class="sxs-lookup"><span data-stu-id="18a16-108">Classic SharePoint sites</span></span>
- <span data-ttu-id="18a16-109">Sitios de comunicación</span><span class="sxs-lookup"><span data-stu-id="18a16-109">Communication sites</span></span>

<span data-ttu-id="18a16-110">Debe ser un administrador global o un administrador de SharePoint para mover un sitio entre ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="18a16-110">You must be a Global Administrator or SharePoint Administrator to move a site between geo locations.</span></span>

<span data-ttu-id="18a16-111">Hay una ventana de solo lectura durante el movimiento geográfico de sitios de SharePoint de aproximadamente 4 a 6 horas, según el contenido del sitio.</span><span class="sxs-lookup"><span data-stu-id="18a16-111">There is a read-only window during the SharePoint site geo move of approximately 4-6 hours, depending on site contents.</span></span>
 
## <a name="best-practices"></a><span data-ttu-id="18a16-112">Procedimientos recomendados</span><span class="sxs-lookup"><span data-stu-id="18a16-112">Best practices</span></span>

- <span data-ttu-id="18a16-113">Pruebe un movimiento del sitio de SharePoint en un sitio de prueba para familiarizarse con el procedimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-113">Try a SharePoint site move on a test site to get familiar with the procedure.</span></span> 
- <span data-ttu-id="18a16-114">Compruebe si el sitio se puede mover antes de programar o realizar el cambio.</span><span class="sxs-lookup"><span data-stu-id="18a16-114">Validate whether the site can be moved prior to scheduling or performing the move.</span></span> 
- <span data-ttu-id="18a16-115">Cuando sea posible, programe movimientos de sitios entre ubicaciones geográficas fuera del horario laboral para reducir el impacto con el usuario.</span><span class="sxs-lookup"><span data-stu-id="18a16-115">When possible schedule cross-geo sites moves for outside business hours to reduce user impact.</span></span>
- <span data-ttu-id="18a16-116">Comuníquese con los usuarios afectados antes del movimiento de sitios.</span><span class="sxs-lookup"><span data-stu-id="18a16-116">Communicate with impacted users prior to the sites move.</span></span> 

## <a name="communicating-to-your-users"></a><span data-ttu-id="18a16-117">Comunicación con los usuarios</span><span class="sxs-lookup"><span data-stu-id="18a16-117">Communicating to your users</span></span>

<span data-ttu-id="18a16-118">Es importante comunicar el resultado esperado a los usuarios de los sitios (generalmente los que pueden editarlos), al migrar los sitios de SharePoint entre ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="18a16-118">When moving SharePoint sites between geo locations, it's important to communicate to the sites' users (generally anyone with the ability to edit the site) what to expect.</span></span> <span data-ttu-id="18a16-119">Esto puede ayudar a reducir la confusión de los usuarios y las llamadas a su departamento de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="18a16-119">This can help reduce user confusion and calls to your help desk.</span></span> <span data-ttu-id="18a16-120">Envíe un correo a los usuarios antes de mover los sitios e infórmeles de lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="18a16-120">Email your sites' users before the move and let them know the following information:</span></span>

- <span data-ttu-id="18a16-121">Cuándo se espera que inicie el movimiento y cuánto tiempo se espera que tarde en completarse.</span><span class="sxs-lookup"><span data-stu-id="18a16-121">When the move is expected to start and how long it is expected to take</span></span>
- <span data-ttu-id="18a16-122">La ubicación geográfica de destino para el sitio y la dirección URL para obtener acceso a la nueva ubicación.</span><span class="sxs-lookup"><span data-stu-id="18a16-122">What geo location their site is moving to, and the URL to access the new location</span></span>
- <span data-ttu-id="18a16-123">Necesitan cerrar sus archivos sin realizar ediciones durante el desplazamiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-123">They should close their files and not make edits during the move.</span></span>
- <span data-ttu-id="18a16-124">Los permisos de archivo y el uso compartido no cambiará como resultado del movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-124">File permissions and sharing will not change because of the move.</span></span>
- <span data-ttu-id="18a16-125">Acciones previstas de la experiencia del usuario en un entorno multigeográfico</span><span class="sxs-lookup"><span data-stu-id="18a16-125">What to expect from the user experience in a multi-geo environment</span></span>

<span data-ttu-id="18a16-126">Asegúrese de enviar a los usuarios un correo electrónico cuando se complete correctamente el movimiento para informarles de que pueden reanudar su trabajo en los sitios.</span><span class="sxs-lookup"><span data-stu-id="18a16-126">Be sure to send your sites' users an email when the move has successfully completed informing them that they can resume working on their sites.</span></span>

## <a name="scheduling-sharepoint-site-moves"></a><span data-ttu-id="18a16-127">Programación de movimientos de sitios de SharePoint </span><span class="sxs-lookup"><span data-stu-id="18a16-127">Scheduling SharePoint site moves</span></span>

<span data-ttu-id="18a16-128">Puede programar los movimientos de sitios de SharePoint por adelantado (como se describe más adelante en este artículo).</span><span class="sxs-lookup"><span data-stu-id="18a16-128">You can schedule SharePoint site moves in advance (described later in this article).</span></span> <span data-ttu-id="18a16-129">Puede programar los movimientos como sigue:</span><span class="sxs-lookup"><span data-stu-id="18a16-129">You can schedule moves as follows:</span></span>

- <span data-ttu-id="18a16-130">Puede programar un máximo de 4000 movimientos cada vez.</span><span class="sxs-lookup"><span data-stu-id="18a16-130">You can schedule up to 4,000 moves at a time.</span></span>
- <span data-ttu-id="18a16-131">Al empezar el movimiento, puede programar más, con un máximo de 4000 movimientos pendientes en la cola y en cualquier momento.</span><span class="sxs-lookup"><span data-stu-id="18a16-131">As the moves begin, you can schedule more, with a maximum of 4,000 pending moves in the queue and any given time.</span></span>
 
<span data-ttu-id="18a16-132">Para programar un movimiento geográfico de sitio de SharePoint para un momento posterior, incluya uno de los parámetros siguiente al iniciar:</span><span class="sxs-lookup"><span data-stu-id="18a16-132">To schedule a SharePoint site geo move for a later time, include one of the following parameters when you start the move:</span></span>
- <span data-ttu-id="18a16-133">`PreferredMoveBeginDate`: Es probable que se inicie el cambio en este momento especificado.</span><span class="sxs-lookup"><span data-stu-id="18a16-133">`PreferredMoveBeginDate` – The move will likely begin at this specified time.</span></span>
- <span data-ttu-id="18a16-134">`PreferredMoveEndDate`: Es probable que se complete el movimiento dentro de este tiempo especificado, en el mejor de los casos.</span><span class="sxs-lookup"><span data-stu-id="18a16-134">`PreferredMoveEndDate` – The move will likely be completed by this specified time, on a best effort basis.</span></span> 

<span data-ttu-id="18a16-135">La hora para ambos parámetros debe especificarse según el Tiempo universal coordinado (UTC).</span><span class="sxs-lookup"><span data-stu-id="18a16-135">Time must be specified in Coordinated Universal Time (UTC) for both parameters.</span></span>

## <a name="moving-the-site"></a><span data-ttu-id="18a16-136">Mover el sitio</span><span class="sxs-lookup"><span data-stu-id="18a16-136">Moving the site</span></span>

<span data-ttu-id="18a16-137">El movimiento geográfico del sitio de SharePoint requiere que se conecte y se realice desde la URL del administrador de SharePoint en la ubicación geográfica donde se encuentra el sitio.</span><span class="sxs-lookup"><span data-stu-id="18a16-137">SharePoint site geo move requires that you connect and perform the move from the SharePoint Admin URL in the geo location where the site is.</span></span>

<span data-ttu-id="18a16-138">Por ejemplo, si la URL del sitio es https://contosohealthcare.sharepoint.com/sites/Turbines, conéctese a la URL del administrador de SharePoint en https://contosohealthcare-admin.sharepoint.com:</span><span class="sxs-lookup"><span data-stu-id="18a16-138">For example, if the site URL is https://contosohealthcare.sharepoint.com/sites/Turbines, connect to the SharePoint Admin URL at https://contosohealthcare-admin.sharepoint.com:</span></span>

`connect-sposervice -url https://contosohealthcare-admin.sharepoint.com`

![](media/move-onedrive-between-geo-locations-image1.png)
 
### <a name="validating-the-environment"></a><span data-ttu-id="18a16-139">Validación del entorno</span><span class="sxs-lookup"><span data-stu-id="18a16-139">Validating the environment</span></span>

<span data-ttu-id="18a16-140">Se recomienda realizar una comprobación para asegurarse de que se puede mover el sitio, antes de programar su movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-140">We recommend that before scheduling any site move, you perform a validation to ensure that the site can be moved.</span></span>

<span data-ttu-id="18a16-141">No se admite mover sitios con:</span><span class="sxs-lookup"><span data-stu-id="18a16-141">We do not support moving sites with:</span></span>
-   <span data-ttu-id="18a16-142">Servicios de conectividad empresarial</span><span class="sxs-lookup"><span data-stu-id="18a16-142">Business Connectivity Services</span></span>
-   <span data-ttu-id="18a16-143">Formularios de InfoPath</span><span class="sxs-lookup"><span data-stu-id="18a16-143">InfoPath forms</span></span> 

<span data-ttu-id="18a16-144">Para asegurarse de que todas las ubicaciones geográficas son compatibles, ejecute `Get-SPOGeoMoveCrossCompatibilityStatus`.</span><span class="sxs-lookup"><span data-stu-id="18a16-144">To ensure all geo locations are compatible, run `Get-SPOGeoMoveCrossCompatibilityStatus`.</span></span> <span data-ttu-id="18a16-145">Esto mostrará todas las ubicaciones geográficas y si el entorno es compatible con la ubicación geográfica de destino.</span><span class="sxs-lookup"><span data-stu-id="18a16-145">This will display all your geo locations and whether the environment is compatible with the destination geo location.</span></span>

<span data-ttu-id="18a16-146">Para realizar una comprobación de validación en el sitio, use `Start-SPOSiteContentMove` con el parámetro `-ValidationOnly` para comprobar si el sitio se puede mover.</span><span class="sxs-lookup"><span data-stu-id="18a16-146">To perform a validation-only check on your site, use `Start-SPOSiteContentMove` with the `-ValidationOnly` parameter to validate if the site is able to be moved.</span></span> <span data-ttu-id="18a16-147">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="18a16-147">For example:</span></span>

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

<span data-ttu-id="18a16-148">Esto devolverá *Success* si el sitio está listo para moverse o *Fail* si hay algunas condiciones bloqueadas.</span><span class="sxs-lookup"><span data-stu-id="18a16-148">This will return *Success* if the site is ready to be moved or *Fail* if any of blocked conditions are present.</span></span>

### <a name="start-a-sharepoint-site-geo-move-for-a-site-with-no-associated-office-365-group"></a><span data-ttu-id="18a16-149">Iniciar un movimiento geográfico de sitios de SharePoint con sitios sin ninguna asociación con los Grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="18a16-149">Start a SharePoint site geo move for a site with no associated Office 365 Group</span></span>

<span data-ttu-id="18a16-150">De forma predeterminada, se cambiará la dirección URL inicial del sitio a la dirección URL de la ubicación geográfica de destino.</span><span class="sxs-lookup"><span data-stu-id="18a16-150">By default, initial URL for the site will change to the URL of the destination geo location.</span></span> <span data-ttu-id="18a16-151">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="18a16-151">For example:</span></span>

<span data-ttu-id="18a16-152">https://Contoso.sharepoint.com/sites/projectx a https://ContosoEUR.sharepoint.com/sites/projectx</span><span class="sxs-lookup"><span data-stu-id="18a16-152">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projectx</span></span>

<span data-ttu-id="18a16-153">Los sitios sin ninguna asociación con los Grupos de Office 365, también pueden cambiar el nombre mediante el parámetro `-DestinationUrl`.</span><span class="sxs-lookup"><span data-stu-id="18a16-153">For sites with no Office 365 Group association, you can also rename the site by using the `-DestinationUrl` parameter.</span></span> <span data-ttu-id="18a16-154">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="18a16-154">For example:</span></span>

<span data-ttu-id="18a16-155">https://Contoso.sharepoint.com/sites/projectx a https://ContosoEUR.sharepoint.com/sites/projecty</span><span class="sxs-lookup"><span data-stu-id="18a16-155">https://Contoso.sharepoint.com/sites/projectx to https://ContosoEUR.sharepoint.com/sites/projecty</span></span>

<span data-ttu-id="18a16-156">Para iniciar el movimiento del sitio, ejecute:</span><span class="sxs-lookup"><span data-stu-id="18a16-156">To start the site move, run:</span></span>

`Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>`

![Captura de pantalla de la ventana de PowerShell que muestra el cmdlet Start-SPOSiteContentMove](media/multi-geo-sharepoint-site-move-powershell.png)

### <a name="start-a-sharepoint-site-geo-move-for-an-office-365-group-connected-site"></a><span data-ttu-id="18a16-158">Iniciar el movimiento geográfico de sitios de SharePoint con sitios conectados a Grupos de Office 365</span><span class="sxs-lookup"><span data-stu-id="18a16-158">Start a SharePoint site geo move for an Office 365 Group-connected site</span></span>

<span data-ttu-id="18a16-159">Para mover un sitio conectado a grupos de Office 365, primero el administrador global debe cambiar el atributo de ubicación de datos preferida (PDL) del Grupo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="18a16-159">To move an Office 365 Group-connected site, the global administrator must first change the Preferred Data Location (PDL) attribute for the Office 365 Group.</span></span>

<span data-ttu-id="18a16-160">Para establecer la PDL de un Grupo de Office 365:</span><span class="sxs-lookup"><span data-stu-id="18a16-160">To set the PDL for an Office 365 Group:</span></span>

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```
<span data-ttu-id="18a16-161">Una vez que haya actualizado la PDL, puede iniciar el movimiento del sitio:</span><span class="sxs-lookup"><span data-stu-id="18a16-161">Once you have updated the PDL, you can start the site move:</span></span> 

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

## <a name="cancel-a-sharepoint-site-geo-move"></a><span data-ttu-id="18a16-162">Cancelar un movimiento geográfico de sitios de SharePoint</span><span class="sxs-lookup"><span data-stu-id="18a16-162">Cancel a SharePoint site geo move</span></span>

<span data-ttu-id="18a16-163">Puede detener un movimiento geográfico de sitios de SharePoint, siempre que el movimiento no esté en curso ni se haya finalizado, mediante el cmdlet `Stop-SPOSiteContentMove`.</span><span class="sxs-lookup"><span data-stu-id="18a16-163">You can stop a SharePoint site geo move, provided the move is not in progress or completed by using the `Stop-SPOSiteContentMove` cmdlet.</span></span>

## <a name="determining-the-status-of-a-sharepoint-site-geo-move"></a><span data-ttu-id="18a16-164">Determinar el estado de un movimiento geográfico de sitios de SharePoint</span><span class="sxs-lookup"><span data-stu-id="18a16-164">Determining the status of a SharePoint site geo move</span></span>

<span data-ttu-id="18a16-165">Puede determinar el estado de un movimiento de sitios dentro y fuera de la ubicación geográfica a la que está conectado mediante los siguientes cmdlet:</span><span class="sxs-lookup"><span data-stu-id="18a16-165">You can determine the status of a site move in our out of the geo that you are connected to by using the following cmdlets:</span></span>

- <span data-ttu-id="18a16-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (sitios no conectados al grupo)</span><span class="sxs-lookup"><span data-stu-id="18a16-166">[Get-SPOSiteContentMoveState](https://docs.microsoft.com/powershell/module/sharepoint-online/get-spositecontentmovestate) (non-Group-connected sites)</span></span>
- <span data-ttu-id="18a16-167">Get-SPOUnifiedGroupMoveState (sitios conectados al grupo)</span><span class="sxs-lookup"><span data-stu-id="18a16-167">Get-SPOUnifiedGroupMoveState (Group-connected sites)</span></span>

<span data-ttu-id="18a16-168">Use el parámetro `-SourceSiteUrl` para especificar el sitio del que quiere ver el estado del movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-168">Use the `-SourceSiteUrl` parameter to specify the site for which you want to see move status.</span></span>

<span data-ttu-id="18a16-169">Los estados del movimiento se describen en la tabla siguiente.</span><span class="sxs-lookup"><span data-stu-id="18a16-169">The move statuses are described in the following table.</span></span>

|<span data-ttu-id="18a16-170">Estado</span><span class="sxs-lookup"><span data-stu-id="18a16-170">Status</span></span>|<span data-ttu-id="18a16-171">Descripción</span><span class="sxs-lookup"><span data-stu-id="18a16-171">Description</span></span>|
|:-----|:----------|
|<span data-ttu-id="18a16-172">Ready to Trigger</span><span class="sxs-lookup"><span data-stu-id="18a16-172">Ready to Trigger</span></span>|<span data-ttu-id="18a16-173">No se ha iniciado el movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-173">The move has not started.</span></span>|
|<span data-ttu-id="18a16-174">Scheduled</span><span class="sxs-lookup"><span data-stu-id="18a16-174">Scheduled</span></span>|<span data-ttu-id="18a16-175">El movimiento está en cola, pero todavía no se ha iniciado.</span><span class="sxs-lookup"><span data-stu-id="18a16-175">The move is in queue but has not yet started.</span></span>|
|<span data-ttu-id="18a16-176">InProgress (n/4)</span><span class="sxs-lookup"><span data-stu-id="18a16-176">InProgress (n/4)</span></span>|<span data-ttu-id="18a16-177">El movimiento está en curso en uno de los siguientes estados: validación (1/4), copia de seguridad (2/4), restauración (3/4), limpieza (4/4).</span><span class="sxs-lookup"><span data-stu-id="18a16-177">The move is in progress in one of the following states: Validation (1/4), Backup (2/4), Restore (3/4), Cleanup (4/4).</span></span>|
|<span data-ttu-id="18a16-178">Success</span><span class="sxs-lookup"><span data-stu-id="18a16-178">Success</span></span>|<span data-ttu-id="18a16-179">El movimiento se completó correctamente.</span><span class="sxs-lookup"><span data-stu-id="18a16-179">The move has completed successfully.</span></span>|
|<span data-ttu-id="18a16-180">Failed</span><span class="sxs-lookup"><span data-stu-id="18a16-180">Failed</span></span>|<span data-ttu-id="18a16-181">No se pudo realizar el movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-181">The move failed.</span></span>|

<span data-ttu-id="18a16-182">También puede aplicar la opción `-Verbose` para ver información adicional sobre el movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-182">You can also apply the `-Verbose` option to see additional information about the move.</span></span>

## <a name="user-experience"></a><span data-ttu-id="18a16-183">Experiencia del usuario</span><span class="sxs-lookup"><span data-stu-id="18a16-183">User experience</span></span>

<span data-ttu-id="18a16-184">Los usuarios del sitio deben notar una interrupción mínima al mover su sitio a otra ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="18a16-184">Site users should notice minimal disruption when their site is moved to a different geo location.</span></span> <span data-ttu-id="18a16-185">Excepto un estado breve de solo lectura durante el movimiento, los permisos y los vínculos existentes seguirán funcionando como se espera una vez completado el proceso.</span><span class="sxs-lookup"><span data-stu-id="18a16-185">Aside from a brief read-only state during the move, existing links and permissions will continue to work as expected once the move is completed.</span></span>

### <a name="site"></a><span data-ttu-id="18a16-186">Sitio</span><span class="sxs-lookup"><span data-stu-id="18a16-186">Site</span></span>

<span data-ttu-id="18a16-187">Mientras se realiza el movimiento, el sitio está configurado como de solo lectura.</span><span class="sxs-lookup"><span data-stu-id="18a16-187">While the move is in progress the site is set to read-only.</span></span> <span data-ttu-id="18a16-188">Una vez completado el movimiento, se dirige al usuario al sitio nuevo en la nueva ubicación geográfica al hacer clic en los marcadores u en otros vínculos del sitio.</span><span class="sxs-lookup"><span data-stu-id="18a16-188">Once the move is completed, the user is directed to the new site in the new geo location when they click on bookmarks or other links to the site.</span></span>

### <a name="permissions"></a><span data-ttu-id="18a16-189">Permisos</span><span class="sxs-lookup"><span data-stu-id="18a16-189">Permissions</span></span>

<span data-ttu-id="18a16-190">Los usuarios con permisos al sitio seguirán teniendo acceso durante el movimiento y después de su finalización.</span><span class="sxs-lookup"><span data-stu-id="18a16-190">Users with permissions to site will continue to have access to the site during the move and after it's complete.</span></span>

### <a name="sync-client"></a><span data-ttu-id="18a16-191">Cliente de sincronización</span><span class="sxs-lookup"><span data-stu-id="18a16-191">Sync Client</span></span>

<span data-ttu-id="18a16-192">El cliente de sincronización detectará automáticamente y transferirá fácilmente la sincronización con la nueva ubicación de sitio, una vez completado el movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-192">The sync client will automatically detect and seamlessly transfer syncing to the new site location once the site move is complete.</span></span> <span data-ttu-id="18a16-193">El usuario no necesitará volver a iniciar sesión ni realizar ninguna otra acción.</span><span class="sxs-lookup"><span data-stu-id="18a16-193">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="18a16-194">(Se requiere la versión 17.3.6943.0625 o posterior del cliente de sincronización).</span><span class="sxs-lookup"><span data-stu-id="18a16-194">(Version 17.3.6943.0625 or later of the sync client required.)</span></span>

<span data-ttu-id="18a16-195">Si un usuario actualiza un archivo mientras el movimiento está en curso, el cliente de sincronización le notificará que hay cargas de archivos pendientes mientras el movimiento está en curso.</span><span class="sxs-lookup"><span data-stu-id="18a16-195">If a user updates a file while the move is in progress, the sync client will notify them that file uploads are pending while the move is underway.</span></span>

### <a name="sharing-links"></a><span data-ttu-id="18a16-196">Vínculos de uso compartido</span><span class="sxs-lookup"><span data-stu-id="18a16-196">Sharing links</span></span>

<span data-ttu-id="18a16-197">Tras la finalización del movimiento geográfico de sitios de SharePoint, los vínculos compartidos existentes de los archivos que se movieron se redirigirán automáticamente a la nueva ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="18a16-197">When the SharePoint site geo move completes, the existing shared links for the files that were moved will automatically redirect to the new geo location.</span></span>

### <a name="most-recently-used-files-in-office-mru"></a><span data-ttu-id="18a16-198">Los archivos usados recientemente de Office (MRU)</span><span class="sxs-lookup"><span data-stu-id="18a16-198">Most Recently Used files in Office (MRU)</span></span>

<span data-ttu-id="18a16-199">El servicio MRU se actualiza con la dirección URL del sitio y sus direcciones URL de contenido cuando se complete el movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-199">The MRU service is updated with the site url and its content URLs once the move completes.</span></span> <span data-ttu-id="18a16-200">Eso se aplica a Word, Excel y PowerPoint</span><span class="sxs-lookup"><span data-stu-id="18a16-200">This applies to Word, Excel, and PowerPoint.</span></span>

### <a name="onenote-experience"></a><span data-ttu-id="18a16-201">Experiencia de OneNote</span><span class="sxs-lookup"><span data-stu-id="18a16-201">OneNote experience</span></span>

<span data-ttu-id="18a16-202">El cliente de win32 de OneNote y la aplicación UWP (Universal) detectarán automáticamente y sincronizarán perfectamente blocs de notas con la nueva ubicación del sitio cuando se complete el movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-202">OneNote win32 client and UWP (Universal) App will automatically detect and seamlessly sync notebooks to the new site location once site move is complete.</span></span> <span data-ttu-id="18a16-203">El usuario no necesitará volver a iniciar sesión ni realizar ninguna otra acción.</span><span class="sxs-lookup"><span data-stu-id="18a16-203">The user does not need to sign in again or take any other action.</span></span> <span data-ttu-id="18a16-204">El único indicador visible para el usuario es que la sincronización de la notebook fallaría cuando el movimiento del sitio esté en curso.</span><span class="sxs-lookup"><span data-stu-id="18a16-204">The only visible indicator to the user is notebook sync would fail when site move is in progress.</span></span> <span data-ttu-id="18a16-205">Esta experiencia está disponible en las siguientes versiones de cliente de OneNote:</span><span class="sxs-lookup"><span data-stu-id="18a16-205">This experience is available on the following OneNote client versions:</span></span>

- <span data-ttu-id="18a16-206">OneNote win32. versión 16.0.8326.2096 (y versiones posteriores)</span><span class="sxs-lookup"><span data-stu-id="18a16-206">OneNote win32 – Version 16.0.8326.2096 (and later)</span></span>
- <span data-ttu-id="18a16-207">OneNote UWP: versión 16.0.8431.1006 (y versiones posteriores)</span><span class="sxs-lookup"><span data-stu-id="18a16-207">OneNote UWP – Version 16.0.8431.1006 (and later)</span></span>
- <span data-ttu-id="18a16-208">Aplicación móvil de OneNote (versión 16.0.8431.1011 y versiones posteriores)</span><span class="sxs-lookup"><span data-stu-id="18a16-208">OneNote Mobile App – Version 16.0.8431.1011 (and later)</span></span>

### <a name="teams-applicable-to-office-365-group-connected-sites"></a><span data-ttu-id="18a16-209">Teams (se aplica a los sitios conectados al Grupo de Office 365)</span><span class="sxs-lookup"><span data-stu-id="18a16-209">Teams (applicable to Office 365 Group connected sites)</span></span>

<span data-ttu-id="18a16-210">Cuando se complete el movimiento geográfico de sitios de SharePoint, los usuarios tendrán acceso a sus archivos de sitio de Grupo de Office 365 en la aplicación de Teams.</span><span class="sxs-lookup"><span data-stu-id="18a16-210">When the SharePoint site geo move completes, users will have access to their Office 365 Group site files on the Teams app.</span></span> <span data-ttu-id="18a16-211">Además, los archivos compartidos mediante chat de Teams desde el sitio, antes del movimiento geográfico, seguirán funcionando tras completar el mismo.</span><span class="sxs-lookup"><span data-stu-id="18a16-211">Additionally, files shared via Teams chat from their site prior to geo move will continue to work after move is complete.</span></span>

### <a name="sharepoint-mobile-app-iosandroid"></a><span data-ttu-id="18a16-212">Aplicación móvil de SharePoint para Android y iOS</span><span class="sxs-lookup"><span data-stu-id="18a16-212">SharePoint Mobile App (iOS/Android)</span></span>

<span data-ttu-id="18a16-213">Se admite la aplicación móvil de SharePoint entre las zonas geográficas y podrá detectar la nueva ubicación geográfica del sitio.</span><span class="sxs-lookup"><span data-stu-id="18a16-213">The SharePoint Mobile App is cross geo compatible and able to detect the site's new geo location.</span></span>

### <a name="sharepoint-workflows"></a><span data-ttu-id="18a16-214">Flujos de trabajo de SharePoint</span><span class="sxs-lookup"><span data-stu-id="18a16-214">SharePoint workflows</span></span>

<span data-ttu-id="18a16-215">Los flujos de trabajo de SharePoint 2013 deben volver a publicarse después de mover el sitio.</span><span class="sxs-lookup"><span data-stu-id="18a16-215">SharePoint 2013 workflows need to be republished after the site move.</span></span> <span data-ttu-id="18a16-216">Los flujos de trabajo de SharePoint 2010 deberían seguir funcionando con normalidad.</span><span class="sxs-lookup"><span data-stu-id="18a16-216">SharePoint 2010 workflows should continue to function normally.</span></span>

### <a name="apps"></a><span data-ttu-id="18a16-217">Aplicaciones</span><span class="sxs-lookup"><span data-stu-id="18a16-217">Apps</span></span>

<span data-ttu-id="18a16-218">Si se mueve un sitio con aplicaciones, debe volver a crear instancias de aplicación en la nueva ubicación geográfica del sitio, ya que es posible que la aplicación y sus conexiones no estén disponibles en la ubicación geográfica de destino.</span><span class="sxs-lookup"><span data-stu-id="18a16-218">If you are moving a site with apps, you must re-instantiate the app in the site's new geo location as the app and its connections may not be available in the destination geo location.</span></span>

### <a name="flow"></a><span data-ttu-id="18a16-219">Flow</span><span class="sxs-lookup"><span data-stu-id="18a16-219">Flow</span></span>

<span data-ttu-id="18a16-220">En la mayoría de los casos los flujos seguirán funcionando después de mover geográficamente el sitio de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="18a16-220">In most cases Flows will continue to work after a SharePoint site geo move.</span></span> <span data-ttu-id="18a16-221">Se recomienda probarlos una vez completado el movimiento.</span><span class="sxs-lookup"><span data-stu-id="18a16-221">We recommend that you test them once the move has completed.</span></span>

### <a name="powerapps"></a><span data-ttu-id="18a16-222">PowerApps</span><span class="sxs-lookup"><span data-stu-id="18a16-222">PowerApps</span></span>

<span data-ttu-id="18a16-223">PowerApps debe volver a crearse en la ubicación de destino.</span><span class="sxs-lookup"><span data-stu-id="18a16-223">PowerApps need to be recreated in the destination location.</span></span>

### <a name="data-movement-between-geo-locations"></a><span data-ttu-id="18a16-224">Mover datos entre ubicaciones geográficas</span><span class="sxs-lookup"><span data-stu-id="18a16-224">Data movement between geo locations</span></span>

<span data-ttu-id="18a16-225">SharePoint usa el Azure Blob Storage para su contenido, mientras los metadatos asociados con los sitios y los archivos se almacenan dentro de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="18a16-225">SharePoint uses Azure Blob storage for its content, while the metadata associated with sites and its files is stored within SharePoint.</span></span> <span data-ttu-id="18a16-226">Cuando el sitio se mueve de su ubicación geográfica de origen a la de destino, el servicio también moverá el Blob Storage asociado. </span><span class="sxs-lookup"><span data-stu-id="18a16-226">After the site is moved from its source geo location to its destination geo location, the service will also move its associated Blob Storage.</span></span> <span data-ttu-id="18a16-227">El movimiento de Blob Storage se completa en aproximadamente 40 días.</span><span class="sxs-lookup"><span data-stu-id="18a16-227">Blob Storage moves complete in approximately 40 days.</span></span> 
