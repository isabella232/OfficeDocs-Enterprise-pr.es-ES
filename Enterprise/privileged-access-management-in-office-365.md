---
title: Con privilegios de acceso a la administración de Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 7/13/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Strat_O365_IP
ms.custom: Ent_Solutions
ms.assetid: ''
description: Utilice este tema para obtener más información acerca de la característica de administración de acceso con privilegios en Office 365
ms.openlocfilehash: 22286d4f91ffa0bd3c49f028681d20e36d14283d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915395"
---
# <a name="privileged-access-management-in-office-365"></a><span data-ttu-id="405de-103">Con privilegios de acceso a la administración de Office 365</span><span class="sxs-lookup"><span data-stu-id="405de-103">Privileged access management in Office 365</span></span>

> [!IMPORTANT]
> <span data-ttu-id="405de-104">En este tema se tratan instrucciones de implementación y configuración de características de la versión beta pública sólo está disponibles actualmente en Office 365 E5 y avanzada SKU de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="405de-104">This topic covers deployment and configuration guidance for public beta features only currently available in Office 365 E5 and Advanced Compliance SKUs.</span></span>

<span data-ttu-id="405de-p101">Con privilegios de acceso permite la administración de control de acceso granular a través de las tareas de administración con privilegios en Office 365.  Puede ayudar a proteger la organización de las infracciones que pueden usar cuentas con privilegios de administración existentes con acceso permanente a los datos confidenciales o acceso a la configuración de configuración crítica. Después de habilitar la administración con privilegios de acceso, los usuarios deberán solicitar acceso just-in-time para completar las tareas con privilegios elevados y con privilegios a través de un flujo de trabajo de aprobación que es altamente con ámbito y límite de tiempo. Esto proporciona a los usuarios just-suficientemente-acceso para realizar la tarea en curso, sin riesgo de exposición de datos confidenciales u opciones de configuración críticos. Habilitación de la administración de acceso con privilegios en Office 365 habilitará la organización operar con cero privilegios permanente y proporcionar un nivel de defensa contra las vulnerabilidades de seguridad que surjan debido a tales acceso administrativo permanente.</span><span class="sxs-lookup"><span data-stu-id="405de-p101">Privileged access management allows granular access control over privileged admin tasks in Office 365.  It can help protect your organization from breaches that may use existing privileged admin accounts with standing access to sensitive data or access to critical configuration settings. After enabling privileged access management, users will need to request just-in-time access to complete elevated and privileged tasks through an approval workflow that is highly scoped and time-bound. This gives users just-enough-access to perform the task at hand, without risking exposure of sensitive data or critical configuration settings. Enabling privileged access management in Office 365 will enable your organization to operate with zero standing privileges and provide a layer of defense against vulnerabilities arising because of such standing administrative access.</span></span> 

<span data-ttu-id="405de-110">En este tema se le guiarán a través de habilitar y configurar la administración del acceso con privilegios en su organización de Office 365 y servir como una guía de referencia de solicitud, aprobación y administración de la característica.</span><span class="sxs-lookup"><span data-stu-id="405de-110">This topic will guide you through enabling and configuring privileged access management in your Office 365 organization and serve as a reference guide for requesting, approving, and managing the feature.</span></span> 

## <a name="before-you-begin"></a><span data-ttu-id="405de-111">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="405de-111">Before you begin</span></span>

### <a name="limited-functionality"></a><span data-ttu-id="405de-112">Funcionalidad limitada</span><span class="sxs-lookup"><span data-stu-id="405de-112">Limited functionality</span></span>
<span data-ttu-id="405de-p102">Durante la versión beta pública, con privilegios de acceso a las características de administración sólo están disponibles a través de [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) en Office 365. Con privilegios de acceso a administración trata las definiciones de tarea en el nivel de los cmdlets de administración de Exchange. En futuras Office 365 versiones acceso con privilegios estarán disponible a través del portal de administración de características y cubren los otros servicios de cargas de trabajo de Office 365.</span><span class="sxs-lookup"><span data-stu-id="405de-p102">During the public beta, privileged access management features are only available through [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/exchange-online-powershell?view=exchange-ps) in Office 365. Privileged access management covers the task definitions at the level of Exchange management cmdlets. In future Office 365 releases, privileged access features will be available through the admin portal and will cover other Office 365 workloads services.</span></span>

### <a name="connecting-to-exchange-online-powershell"></a><span data-ttu-id="405de-116">Conectarse a Exchange Online PowerShell</span><span class="sxs-lookup"><span data-stu-id="405de-116">Connecting to Exchange Online PowerShell</span></span>
<span data-ttu-id="405de-117">Los pasos de configuración en este tema le guiará a través de habilitación y uso de access con privilegios en Office 365 con Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="405de-117">The configuration steps in this topic will walk you through enabling and using privileged access in Office 365 using Exchange Online PowerShell.</span></span> 

<span data-ttu-id="405de-118">Siga los pasos descritos en [conectarse a Exchange Online PowerShell mediante autenticación multifactor](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) para conectarse a Exchange Online PowerShell con sus credenciales de Office 365 para habilitar y configurar el acceso con privilegios para su organización.</span><span class="sxs-lookup"><span data-stu-id="405de-118">Follow the steps in [Connect to Exchange Online PowerShell using Multi-Factor authentication](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/mfa-connect-to-exchange-online-powershell?view=exchange-ps) to connect to Exchange Online PowerShell with your Office 365 credentials to enable and configure privileged access for your organization.</span></span>

> [!NOTE]
> <span data-ttu-id="405de-p103">No es necesario habilitar la autenticación multifactor para su organización de Office 365 usar los pasos para habilitar el acceso con privilegios mientras se conecta a Exchange Online PowerShell. Conectar con la autenticación multifactor crea un token de OAuth que se usa en el acceso con privilegios para las solicitudes de firma.</span><span class="sxs-lookup"><span data-stu-id="405de-p103">You do not need to enable multi-factor authentication for your Office 365 organization to use the steps to enable privileged access while connecting to Exchange Online PowerShell. Connecting with multi-factor authentication creates an OAuth token that is used by privileged access for signing your requests.</span></span>

## <a name="enable-and-configure-privileged-access-management"></a><span data-ttu-id="405de-121">Habilitar y configurar la administración con privilegios de acceso</span><span class="sxs-lookup"><span data-stu-id="405de-121">Enable and configure privileged access management</span></span>

### <a name="step-1---create-an-approvers-group"></a><span data-ttu-id="405de-122">Paso 1: crear el grupo del aprobador</span><span class="sxs-lookup"><span data-stu-id="405de-122">Step 1 - Create an approver's group</span></span>
<span data-ttu-id="405de-p104">En el Portal de administración de Office 365, seleccione **grupos** > **Agregar un grupo**, a continuación, cree un grupo de seguridad habilitado para correo para los aprobadores de acceso predeterminada con privilegios. Cuando haya terminado, seleccione **Agregar** para crear y guardar el grupo de aprobadores.</span><span class="sxs-lookup"><span data-stu-id="405de-p104">From Office 365 Admin Portal, select **Groups** > **Add a group**, then create a mail enabled security group for the default privileged access approvers. When complete, select **Add** to create and save the approver group.</span></span>

![Pantalla de aprobadores con privilegios de acceso en el portal de administración de Office 365](media/privileged-access-approvers-ui.png)

> [!NOTE] 
> <span data-ttu-id="405de-p105">En este momento, sólo los usuarios con acceso administrativo pueden aprobar las solicitudes de acceso de Office 365 privilegiada. En el futuro, cualquier usuario que forma parte del grupo de los aprobadores podrán aprobar las solicitudes de acceso.</span><span class="sxs-lookup"><span data-stu-id="405de-p105">At this time, only users with administrative access are allowed to approve requests from Office 365 priviledged access. In future any user who is part of the Approvers’ group will be able to approve access requests.</span></span>

### <a name="step-2---enable-privileged-access-in-office-365"></a><span data-ttu-id="405de-128">Paso 2: habilitar el acceso con privilegios en Office 365</span><span class="sxs-lookup"><span data-stu-id="405de-128">Step 2 - Enable privileged access in Office 365</span></span>
<span data-ttu-id="405de-129">Acceso con privilegios debe habilitarse explícitamente con el grupo de aprobador predeterminado y un conjunto de cuentas del sistema que desea que se deben excluir desde el control de acceso de administración con privilegios de acceso, inclusive.</span><span class="sxs-lookup"><span data-stu-id="405de-129">Privileged access needs to be explicitly turned on with the default approver group and including a set of system accounts that you’d want to be excluded from the privileged access management access control.</span></span> 

<span data-ttu-id="405de-130">En Exchange Online PowerShell para habilitar el acceso con privilegios y para asignar el grupo de aprobadores, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="405de-130">Run the following command in Exchange Online PowerShell to enable privileged access and to assign the approver's group:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```
<span data-ttu-id="405de-131">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="405de-131">Example:</span></span>
```
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

> [!NOTE]
> <span data-ttu-id="405de-132">Cuentas del sistema característica está disponible para asegurarse de determinados automations dentro de las organizaciones pueden trabajar sin dependencia en acceso con privilegios, sin embargo, se recomienda que estas exclusiones se excepcionales y los autorizados deben aprobados y auditar con regularidad.</span><span class="sxs-lookup"><span data-stu-id="405de-132">System accounts feature is made available to ensure certain automations within your organizations can work without dependency on privileged access, however it is recommended that such exclusions be exceptional and those allowed should be approved and audited regularly.</span></span>

### <a name="step-3---create-an-approval-policy"></a><span data-ttu-id="405de-133">Paso 3: crear una directiva de aprobación</span><span class="sxs-lookup"><span data-stu-id="405de-133">Step 3 - Create an approval policy</span></span>
<span data-ttu-id="405de-p106">Una directiva de aprobación le permite definir los requisitos de aprobación específico con ámbito en tareas individuales. Las opciones de tipo de aprobación son **automático** o **Manual**.</span><span class="sxs-lookup"><span data-stu-id="405de-p106">An approval policy allows you to define the specific approval requirements scoped at individual tasks. The approval type options are **Auto** or **Manual**.</span></span> 

<span data-ttu-id="405de-136">Ejecute el siguiente comando en Exchange Online PowerShell para definir una directiva de aprobación:</span><span class="sxs-lookup"><span data-stu-id="405de-136">Run the following command in Exchange Online PowerShell to define an approval policy:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```
<span data-ttu-id="405de-137">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="405de-137">Example:</span></span>
```
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

## <a name="using-privileged-access-in-your-office-365-organization"></a><span data-ttu-id="405de-138">Uso de acceso con privilegios en su organización de Office 365</span><span class="sxs-lookup"><span data-stu-id="405de-138">Using privileged access in your Office 365 organization</span></span>

### <a name="requesting-elevation-authorization-to-execute-tasks"></a><span data-ttu-id="405de-139">Solicitud de autorización de elevación para ejecutar tareas</span><span class="sxs-lookup"><span data-stu-id="405de-139">Requesting elevation authorization to execute tasks</span></span>
<span data-ttu-id="405de-p107">Una vez habilitado, con privilegios de acceso requiere aprobaciones para ejecutar cualquier tarea que tiene una directiva de aprobación asociada definida. Los usuarios que necesiten ejecutar tareas incluidas en la una directiva de aprobación debe solicitar y recibir aprobación de acceso con el fin de tener los permisos necesarios para ejecutar la tarea.</span><span class="sxs-lookup"><span data-stu-id="405de-p107">Once enabled, privileged access requires approvals for executing any task that has an associated approval policy defined. Users needing to execute tasks included in the an approval policy must request and be granted access approval in order to have permissions necessary to execute the task.</span></span>

<span data-ttu-id="405de-142">Ejecute el siguiente comando en Exchange Online PowerShell para crear y enviar una solicitud de aprobación al grupo del aprobador:</span><span class="sxs-lookup"><span data-stu-id="405de-142">Run the following command in Exchange Online PowerShell to create and submit an approval request to the approver's group:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```
<span data-ttu-id="405de-143">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="405de-143">Example:</span></span>
```
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```
### <a name="view-status-of-elevation-requests"></a><span data-ttu-id="405de-144">Ver el estado de las solicitudes de elevación</span><span class="sxs-lookup"><span data-stu-id="405de-144">View status of elevation requests</span></span>
<span data-ttu-id="405de-145">Una vez creada una solicitud de aprobación, estado de la solicitud de elevación puede revisarse con el asociado con el identificador de solicitud.</span><span class="sxs-lookup"><span data-stu-id="405de-145">After an approval request is created, elevation request status can be reviewed using the associated with request ID.</span></span>

<span data-ttu-id="405de-146">Ejecute el siguiente comando en Exchange Online PowerShell para ver el estado de la solicitud de aprobación para un identificador de solicitud específico:</span><span class="sxs-lookup"><span data-stu-id="405de-146">Run the following command in Exchange Online PowerShell to view a approval request status for a specific request ID:</span></span>
```
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```
<span data-ttu-id="405de-147">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="405de-147">Example:</span></span>
```
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a><span data-ttu-id="405de-148">Aprobación de una solicitud de autorización de elevación</span><span class="sxs-lookup"><span data-stu-id="405de-148">Approving an elevation authorization request</span></span>
<span data-ttu-id="405de-149">Cuando se crea una solicitud de aprobación, los miembros del grupo de aprobadores relevantes recibirán una notificación de correo electrónico y pueden aprobar la solicitud asociada con el identificador de solicitud.</span><span class="sxs-lookup"><span data-stu-id="405de-149">When an approval request is created, members of the relevant approver group will receive an email notification and can approve the request associated with the request ID.</span></span> 

<span data-ttu-id="405de-150">Ejecute el siguiente comando en Exchange Online PowerShell para aprobar una solicitud de autorización de elevación:</span><span class="sxs-lookup"><span data-stu-id="405de-150">Run the following command in Exchange Online PowerShell to approve an elevation authorization request:</span></span>
```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="405de-151">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="405de-151">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```
### <a name="denying-an-elevation-authorization-request"></a><span data-ttu-id="405de-152">La denegación de una solicitud de autorización de elevación</span><span class="sxs-lookup"><span data-stu-id="405de-152">Denying an elevation authorization request</span></span>
<span data-ttu-id="405de-153">Cuando se crea una solicitud de aprobación, los miembros del grupo de aprobadores relevantes pueden denegar la solicitud asociada con el identificador de solicitud.</span><span class="sxs-lookup"><span data-stu-id="405de-153">When an approval request is created, members of the relevant approver group can deny the request associated with the request ID.</span></span> 

<span data-ttu-id="405de-154">Ejecute el siguiente comando en Exchange Online PowerShell para denegar una solicitud de autorización de elevación:</span><span class="sxs-lookup"><span data-stu-id="405de-154">Run the following command in Exchange Online PowerShell to deny an elevation authorization request:</span></span>
```
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```
<span data-ttu-id="405de-155">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="405de-155">Example:</span></span>
```
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

### <a name="running-the-task"></a><span data-ttu-id="405de-156">Ejecución de la tarea</span><span class="sxs-lookup"><span data-stu-id="405de-156">Running the task</span></span>
<span data-ttu-id="405de-p108">Una vez se concede la aprobación, el usuario solicitante puede ejecutar la tarea prevista y va a autorizar y ejecutar la tarea en nombre de los usuarios con privilegios de acceso. La aprobación sigue siendo válida para el solicitado duración (duración predeterminada es de 4 horas), durante el cual el solicitante puede ejecutar la tarea prevista varias veces. Todas esas ejecuciones se registran y a disposición de cumplimiento de normas de auditoría y seguridad.</span><span class="sxs-lookup"><span data-stu-id="405de-p108">After approval is granted, the requesting user can execute the intended task and privileged access will authorize and execute the task on users’ behalf. The approval remains valid for the requested duration (default duration is 4 hours), during which the requester can execute the intended task multiple times. All such executions are logged and made available for security and compliance auditing.</span></span> 

### <a name="disable-privileged-access-in-office-365"></a><span data-ttu-id="405de-160">Deshabilitar el acceso con privilegios en Office 365</span><span class="sxs-lookup"><span data-stu-id="405de-160">Disable privileged access in Office 365</span></span>
<span data-ttu-id="405de-p109">Si es necesario, puede deshabilitar la administración de acceso con privilegios en Office 365. Deshabilitar con privilegios de acceso no eliminar cualquier las directivas de aprobación asociada o grupos de aprobador.</span><span class="sxs-lookup"><span data-stu-id="405de-p109">If needed, you can disable privileged access management in Office 365. Disabling privileged access does not delete any associated approval policies or approver groups.</span></span>

<span data-ttu-id="405de-163">Ejecute el siguiente comando en Exchange Online Powershell para deshabilitar el acceso con privilegios:</span><span class="sxs-lookup"><span data-stu-id="405de-163">Run the following command in Exchange Online Powershell to disable privileged access:</span></span>

```
Disable-ElevatedAccessControl
```
## <a name="managed-access-to-microsoft-graph-in-microsoft-azure"></a><span data-ttu-id="405de-164">Acceso a administrada para Microsoft Graph en Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="405de-164">Managed access to Microsoft Graph in Microsoft Azure</span></span>

> [!IMPORTANT]
> <span data-ttu-id="405de-165">En esta sección se describe cómo obtener información detallada acerca de una característica que sólo está disponible en vista previa.</span><span class="sxs-lookup"><span data-stu-id="405de-165">This section covers details about a feature currently available only in preview.</span></span>

<span data-ttu-id="405de-p110">Acceso administrado para Microsoft Graph en Microsoft Azure es un servicio que ayuda a las organizaciones a ejercer un nivel de control sobre sus datos de Office 365 específico. Este sistema permite que los desarrolladores de aplicaciones seguir entendimiento con los datos.</span><span class="sxs-lookup"><span data-stu-id="405de-p110">Managed access to Microsoft Graph in Microsoft Azure is a service that helps organizations exert a granular level of control over their Office 365 data. This system allows application developers to forge insights with that data.</span></span> 

<span data-ttu-id="405de-p111">Este sistema usa acceso a Office 365 con privilegios para assert control sobre sus datos a través de su flujo de trabajo de aprobación, que permite el acceso de ámbito a los datos de Office 365 con la supervisión de la administración. Las solicitudes de datos se incluyen cuando las aplicaciones se instalan y requieren acceso a datos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="405de-p111">This system uses Office 365 privileged access to assert control over their data through its approval workflow, allowing scoped access to Office 365 data with admin oversight. Requests for data come in when applications are installed and require access to Office 365 data.</span></span>

### <a name="view-request-details"></a><span data-ttu-id="405de-170">Vista Detalles de la solicitud</span><span class="sxs-lookup"><span data-stu-id="405de-170">View request details</span></span>
<span data-ttu-id="405de-171">Ver los detalles de las solicitudes de acceso para los datos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="405de-171">View details of the access requests for Office 365 data.</span></span>

<span data-ttu-id="405de-172">Ejecute el siguiente comando en Exchange Online Powershell para ver las solicitudes de datos:</span><span class="sxs-lookup"><span data-stu-id="405de-172">Run the following command in Exchange Online Powershell to view data requests:</span></span>
```
Get-ElevatedAccessRequest | where {$_.RequestedAccess -like '*Data Access Request*'} | select RequestorUPN, Service, RequestedAccess | fl
```
<span data-ttu-id="405de-173">Salida de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="405de-173">Example output:</span></span>
```
RequestorUPN    : admin@contoso.com
Service         : Office365
RequestedAccess : Data Access Request
```

### <a name="approve-data-access-requests"></a><span data-ttu-id="405de-174">Aprobar solicitudes de acceso a datos</span><span class="sxs-lookup"><span data-stu-id="405de-174">Approve data access requests</span></span>
<span data-ttu-id="405de-175">Todas las solicitudes de acceso de datos se pueden aprobar a través de los cmdlets de aprobación de acceso con privilegios estándar.</span><span class="sxs-lookup"><span data-stu-id="405de-175">All data access requests can be approved through the standard privileged access approval cmdlets.</span></span>

<span data-ttu-id="405de-176">Ejecute el siguiente comando en Exchange Online Powershell para aprobar todas las solicitudes de datos para el solicitante específico:</span><span class="sxs-lookup"><span data-stu-id="405de-176">Run the following command in Exchange Online Powershell to approve all data requests for specific requestor:</span></span>

```
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```
<span data-ttu-id="405de-177">Ejemplo:</span><span class="sxs-lookup"><span data-stu-id="405de-177">Example:</span></span>
```
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

## <a name="getting-help-and-providing-feedback"></a><span data-ttu-id="405de-178">Obtener ayuda y proporcionar comentarios</span><span class="sxs-lookup"><span data-stu-id="405de-178">Getting help and providing feedback</span></span>
<span data-ttu-id="405de-p112">Reconocemos que durante la versión beta pública es posible que encuentre un error ocasional o tiene comentarios y sugerencias sobre cómo podemos mejorar la administración del acceso con privilegios. Se el valor de sus comentarios y anima a los usuarios a compartir con nosotros:</span><span class="sxs-lookup"><span data-stu-id="405de-p112">We recognize that during the public beta you may come across an occasional bug or have feedback and suggestions on how we can improve privileged access management. We value your feedback and encourage you to share it with us:</span></span>
- <span data-ttu-id="405de-181">Envíenos sus comentarios sugerencias de ad en el [Grupo de Yammer de vista previa de Office](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span><span class="sxs-lookup"><span data-stu-id="405de-181">Post your feedback ad suggestions in the [Office Preview Yammer Group](https://www.yammer.com/officeenterprisenda/#/threads/inGroup?type=in_group&feedId=14435206).</span></span>
- <span data-ttu-id="405de-182">Archivo de los informes de errores en la ruta de acceso de área "Office 365 con privilegios administración de acceso" en el [VSO de vista previa de Office](https://office-previews.visualstudio.com/previews).</span><span class="sxs-lookup"><span data-stu-id="405de-182">File your bug reports under area path “Office 365 Privileged Access Management” on the [Office Preview VSO](https://office-previews.visualstudio.com/previews).</span></span>

## <a name="frequently-asked-questions"></a><span data-ttu-id="405de-183">Preguntas más frecuentes</span><span class="sxs-lookup"><span data-stu-id="405de-183">Frequently asked questions</span></span>

### <a name="what-skus-do-i-need-to-use-privileged-access-in-office-365"></a><span data-ttu-id="405de-184">¿Qué SKU es necesario usar access con privilegios en Office 365?</span><span class="sxs-lookup"><span data-stu-id="405de-184">What SKUs do I need to use privileged access in Office 365?</span></span>
<span data-ttu-id="405de-185">Con privilegios de acceso de administración de Office 365 actualmente sólo está disponible para los clientes con E5 y avanzada SKU de cumplimiento.</span><span class="sxs-lookup"><span data-stu-id="405de-185">Privileged access management in Office 365 is currently only available for customers with E5 and Advanced Compliance SKUs.</span></span>

### <a name="when-will-privileged-access-be-available-for-office-365-workloads-beyond-exchange"></a><span data-ttu-id="405de-186">¿Cuándo estará disponible para cargas de trabajo de Office 365 más allá de Exchange con privilegios de acceso?</span><span class="sxs-lookup"><span data-stu-id="405de-186">When will privileged access be available for Office 365 workloads beyond Exchange?</span></span>
<span data-ttu-id="405de-p113">Se planea ofrecer esta característica en otras cargas de trabajo de Office 365 pronto. Cuando estamos listos para compartir una escala de tiempo, estará disponible a través de la guía básica de Office 365.</span><span class="sxs-lookup"><span data-stu-id="405de-p113">We plan to offer this feature in other Office 365 workloads soon. When we’re ready to share a timeline, it will be available through the Office 365 roadmap.</span></span>

### <a name="how-is-this-different-from-azure-active-directorys-privileged-identity-management"></a><span data-ttu-id="405de-189">¿Cómo es diferente de la administración de identidades con privilegios de Active Directory de Azure?</span><span class="sxs-lookup"><span data-stu-id="405de-189">How is this different from Azure Active Directory’s Privileged Identity Management?</span></span>
<span data-ttu-id="405de-p114">Con privilegios de tener acceso a la administración de Office 365 y el complemento de [administración de identidades con privilegios de Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) mutuamente proporcionando acceso controlar con acceso just-in-time en los distintos ámbitos. Juntos, proporcionan un completo conjunto de controles para la protección de los datos.</span><span class="sxs-lookup"><span data-stu-id="405de-p114">Privileged access management in Office 365 and [Azure AD Privileged Identity Management](https://docs.microsoft.com/azure/active-directory/active-directory-privileged-identity-management-configure) complement each other by providing access control with just-in-time access at different scopes. Together they provide a robust set of controls for protecting your data.</span></span>

<span data-ttu-id="405de-p115">Con privilegios de acceso se puede definir y con ámbito en el nivel de tarea, mientras que la administración de identidades AD con privilegios de Azure se aplica en el nivel de función con la capacidad de ejecutar varias tareas de administración de Office 365.  Azure AD de administración de identidades con privilegios principalmente permite administrar accesos para las funciones de AD y grupos de roles mientras con privilegios de administración de acceso en Office 365 se aplica en el nivel de tarea.</span><span class="sxs-lookup"><span data-stu-id="405de-p115">Privileged access management in Office 365 can be defined and scoped at the task level, while Azure AD Privileged Identity Management applies at the role level with the ability to execute multiple tasks.  Azure AD Privileged Identity Management primarily allows managing accesses for AD roles and role groups while privileged access management in Office 365 is applied at the task level.</span></span>

 - <span data-ttu-id="405de-194">**Con privilegios de habilitar acceso a administración de Office 365 mientras ya está usando la administración de identidades de AD con privilegios de Azure:** Adición de administración de acceso con privilegios en Office 365 puede proporcionar una capa pormenorizada de protección y capacidad para el acceso a datos de Office 365 con privilegios de auditoría.</span><span class="sxs-lookup"><span data-stu-id="405de-194">**Enabling privileged access management in Office 365 while already using Azure AD Privileged Identity Management:** Adding privileged access management in Office 365 can provide another granular layer of protection and audit capabilities for privileged access to Office 365 data.</span></span>

- <span data-ttu-id="405de-195">**Mientras ya está usando la administración de identidades AD con privilegios de habilitación de Azure con privilegios de administración de acceso en Office 365:**  Adición de la administración de identidades con Azure AD privilegios a con privilegios de administración de acceso en Office 365 puede ampliar con privilegios de acceso a datos fuera de Office 365 que principalmente se define por función o la identidad de un usuario.</span><span class="sxs-lookup"><span data-stu-id="405de-195">**Enabling Azure AD Privileged Identity Management while already using privileged access management in Office 365:**  Adding Azure AD Privileged Identity Management to privileged access management in Office 365 can extend privileged access to data outside of Office 365 that’s primarily defined by a user’s role or identity.</span></span> 

### <a name="do-i-need-to-be-a-global-admin-to-manage-privileged-access-in-office-365"></a><span data-ttu-id="405de-196">¿Es necesario ser un administrador Global para administrar el acceso con privilegios en Office 365?</span><span class="sxs-lookup"><span data-stu-id="405de-196">Do I need to be a Global Admin to manage privileged access in Office 365?</span></span>
<span data-ttu-id="405de-p116">Durante la vista previa debe tener privilegios de administrador Global para poder administrar el acceso con privilegios en Office 365. Los usuarios que se incluyen en el grupo de los aprobadores no es necesario ser un administrador Global para revisar y aprobar las solicitudes.</span><span class="sxs-lookup"><span data-stu-id="405de-p116">During the preview you need to have Global Admin privilege to be able to manage privileged access in Office 365. Users who are included in an approvers’ group don't need to be a Global Admin to review and approve requests.</span></span> 

### <a name="how-is-privileged-access-management-in-office-365-related-to-customer-lockbox"></a><span data-ttu-id="405de-199">¿Cómo es la administración de acceso con privilegios en Office 365 relacionadas con la caja de seguridad del cliente?</span><span class="sxs-lookup"><span data-stu-id="405de-199">How is privileged access management in Office 365 related to Customer Lockbox?</span></span>
<span data-ttu-id="405de-p117">[Caja de seguridad de cliente](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) permite a un nivel de control de acceso para las organizaciones para el acceso a datos por su proveedor de servicios, es decir, Microsoft. Con privilegios de acceso de control de acceso granular dentro de una organización para todas las tareas de Office 365 con privilegios permite la administración de Office 365.</span><span class="sxs-lookup"><span data-stu-id="405de-p117">[Customer Lockbox](https://support.office.com/article/Office-365-Customer-Lockbox-Requests-36f9cdd1-e64c-421b-a7e4-4a54d16440a2) allows a level of access control for organizations for access to to data by their service provider, i.e. Microsoft. Privileged access management in Office 365 allows granular access control within an organization for all Office 365 privileged tasks.</span></span>