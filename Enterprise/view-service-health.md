---
title: Cómo comprobar el estado del servicio de Office 365
ms.author: robmazz
author: robmazz
manager: laurawi
ms.audience: Admin
ms.topic: article
f1_keywords:
- O365P_ServiceHealthModern
- O365M_ServiceHealthModern
- O365E_ViewStatusServices
- O365E_ServiceHealthModern
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
- IWA160
ms.assetid: 932ad3ad-533c-418a-b938-6e44e8bc33b0
description: Ver el estado de mantenimiento de servicios de Office 365 antes de llamar a soporte técnico para ver si hay una interrupción del servicio de active
ms.openlocfilehash: 7e04e1309c990ccced67663576285f7276603ccc
ms.sourcegitcommit: 6826e0ea4a777f7d98500209a9d3bc75e89f8d15
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/30/2019
ms.locfileid: "29651194"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="fc87d-103">Cómo comprobar el estado del servicio de Office 365</span><span class="sxs-lookup"><span data-stu-id="fc87d-103">How to check Office 365 service health</span></span>

<span data-ttu-id="fc87d-p101">Puede ver el estado de Office 365, Yammer, Microsoft Dynamics CRM y servicios de nube de Microsoft Intune en la página de **estado del servicio** de Office 365 en el centro de administración. Si experimenta problemas con un servicio de nube, puede comprobar el estado del servicio para determinar si se trata de un problema conocido con una resolución en curso antes de llamar al soporte técnico o dedicada a la solución de problemas de tiempo.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 **Service health** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 

<span data-ttu-id="fc87d-106">Si no puede iniciar sesión en el portal de servicio, puede usar la [página de estado de servicio](https://status.office365.com) para buscar problemas conocidos que le impide iniciar sesión en el inquilino.</span><span class="sxs-lookup"><span data-stu-id="fc87d-106">If you are unable to sign in to the service portal, you can use the [service status page](https://status.office365.com) to check for known issues preventing you from logging into your tenant.</span></span>
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="fc87d-107">Cómo comprobar el estado del servicio</span><span class="sxs-lookup"><span data-stu-id="fc87d-107">How to check service health</span></span>

1. <span data-ttu-id="fc87d-108">Vaya a [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e inicie sesión con una cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="fc87d-108">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="fc87d-p102">Los usuarios que tienen asignado el rol de administrador de servicios o administrador global pueden ver el estado del servicio. Para que los administradores de Exchange, SharePoint y Skype Empresarial puedan ver el estado del servicio, también se les debe asignar el rol Administrador de servicios.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span>
  
2. <span data-ttu-id="fc87d-p103">Para abrir el estado del servicio, en el centro de administración, vaya a **Mantenimiento** > **estado del servicio**, o haga clic en la **tarjeta de servicio de estado** en el **panel principal**. La tarjeta de panel indica si hay un problema de servicio de active y vínculos a la página de estado de servicio detallados.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p103">To open service health, in the admin center, go to **Health** > **Service health**, or click the **Service health card** on the **Home dashboard**. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="fc87d-114">El estado de mantenimiento de cada servicio en la nube se muestra en formato de tabla con un icono para indicar los posibles estados.</span><span class="sxs-lookup"><span data-stu-id="fc87d-114">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="fc87d-115">También puede usar la [aplicación de administración de Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) en su dispositivo móvil para ver el estado del servicio, que es una buena forma de mantenerse al día con las notificaciones de inserción.</span><span class="sxs-lookup"><span data-stu-id="fc87d-115">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="fc87d-116">Ver detalles del estado del servicio publicado</span><span class="sxs-lookup"><span data-stu-id="fc87d-116">View details of posted service health</span></span>

<span data-ttu-id="fc87d-p104">En la vista predeterminada, se muestran todos los servicios y su estado de mantenimiento actual. Para filtrar la vista a servicios está experimentando un incidente, seleccione **incidentes** en la barra de sombreado de la izquierda. Selección de **avisos** mostrará únicamente los servicios que actualmente tienen un asesor registrado. Desde la vista de **todos los servicios** , haciendo clic en el estado del servicio que se muestra se abrirá una vista de resumen del documento informativo o incidente.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="fc87d-122">En el resumen del aviso o del incidente, se proporciona la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="fc87d-122">The advisory or incident summary provides the following information:</span></span> 
  
![Una captura de pantalla etiquetar los campos en un documento informativo de servicio](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="fc87d-124">Identificador y resumen de un problema.</span><span class="sxs-lookup"><span data-stu-id="fc87d-124">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="fc87d-p105">Estado actual. Consulte las definiciones de este artículo para conocer la explicación de cada posible estado.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="fc87d-127">Descripción de cómo este problema puede afectar a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="fc87d-127">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="fc87d-p106">Hora en la que se inició el problema y hora en la que se actualizó el mensaje del estado del servicio por última vez. Mientras el problema se sigue produciendo, publicamos mensajes frecuentes para informarle de nuestro progreso en la aplicación de una solución.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="fc87d-130">Seleccione el vínculo **Mostrar detalles** para ver más detalles sobre el problema, incluido el historial de todos los mensajes publicados mientras trabajamos en encontrar una solución.</span><span class="sxs-lookup"><span data-stu-id="fc87d-130">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="fc87d-131">Detalles del estado del servicio de traducción</span><span class="sxs-lookup"><span data-stu-id="fc87d-131">Translate service health details</span></span>

<span data-ttu-id="fc87d-p107">Como las explicaciones del estado del servicio se publican en tiempo real, no se traducen automáticamente a su idioma y los detalles de los eventos de servicio se muestran solo en inglés. Para traducir la explicación, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="fc87d-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="fc87d-134">Vaya a [Traductor](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="fc87d-134">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="fc87d-p108">En la página **Estado del servicio**, seleccione un incidente o un aviso. En **Mostrar detalles**, copie el texto sobre el problema.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="fc87d-137">En el traductor, pegue el texto y elija **Traducir**.</span><span class="sxs-lookup"><span data-stu-id="fc87d-137">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="fc87d-138">Definiciones</span><span class="sxs-lookup"><span data-stu-id="fc87d-138">Definitions</span></span>

<span data-ttu-id="fc87d-p109">La mayoría de las veces, los servicios aparecerán como correctos sin más información. Cuando un servicio experimenta un problema, este se identifica como aviso o incidente y se muestra el estado actual.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="fc87d-p110">Los eventos de mantenimiento planeados se muestran en el estado del servicio. Puede realizar un seguimiento de los eventos de mantenimiento planeados manteniéndose al día con el **Centro de mensajes**. Filtre por los mensajes de la categoría Planear el cambio para descubrir cuándo sucederá el cambio, el efecto que tendrá y cómo debe prepararse para afrontarlo. Vea [Centro de mensajes de Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) para obtener más detalles.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="fc87d-145">Incidentes y avisos</span><span class="sxs-lookup"><span data-stu-id="fc87d-145">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="fc87d-p111">Si se muestra un aviso en un servicio, significa que somos conscientes de que existe un problema que está afectando a algunos usuarios, pero el servicio todavía está disponible. En los avisos, suele haber una solución alternativa para el problema y es posible que este se produzca de forma intermitente o que esté limitado a unas consecuencias para el usuario y a un ámbito específicos.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="fc87d-p112">Si, en un servicio, se muestra un incidente activo, significa que existe un problema crítico y que el servicio o una de las características principales del servicio no está disponible. Por ejemplo, es posible que los usuarios no puedan enviar ni recibir correo electrónico o que no puedan iniciar sesión. Los incidentes tendrán un impacto notable sobre los usuarios. Cuando haya un incidente en curso, ofreceremos actualizaciones en relación con la investigación, las acciones llevadas a cabo y la confirmación de la resolución en el panel Estado del servicio.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="fc87d-154">Definiciones de los estados</span><span class="sxs-lookup"><span data-stu-id="fc87d-154">Status definitions</span></span>

|<span data-ttu-id="fc87d-155">**Estado**</span><span class="sxs-lookup"><span data-stu-id="fc87d-155">**Status**</span></span>|<span data-ttu-id="fc87d-156">**Definición**</span><span class="sxs-lookup"><span data-stu-id="fc87d-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="fc87d-157">**Bajo investigación**</span><span class="sxs-lookup"><span data-stu-id="fc87d-157">**Investigating**</span></span> | <span data-ttu-id="fc87d-158">Somos conscientes de que existe un problema potencial y estamos recopilando más información sobre lo que sucede y el ámbito de impacto.</span><span class="sxs-lookup"><span data-stu-id="fc87d-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span> |
|<span data-ttu-id="fc87d-159">**Degradación del servicio**</span><span class="sxs-lookup"><span data-stu-id="fc87d-159">**Service degradation**</span></span> | <span data-ttu-id="fc87d-p113">Hemos confirmado que existe un problema que puede afectar al uso de un servicio o una característica. Es posible que vea este estado si un servicio está funcionando más lento de lo normal, si hay interrupciones intermitentes o si una característica no funciona, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span> |
|<span data-ttu-id="fc87d-162">**Interrupción del servicio**</span><span class="sxs-lookup"><span data-stu-id="fc87d-162">**Service interruption**</span></span> | <span data-ttu-id="fc87d-p114">Verá este estado si se determina que un problema afecta a posibilidad de los usuarios de obtener acceso al servicio. En este caso, el problema es importante y se puede reproducir de forma coherente.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span> |
|<span data-ttu-id="fc87d-165">**Restaurando el servicio**</span><span class="sxs-lookup"><span data-stu-id="fc87d-165">**Restoring service**</span></span> | <span data-ttu-id="fc87d-166">Se ha identificado la causa del problema, sabemos qué acción correctiva debemos aplicar y estamos en proceso de restablecer el servicio a un estado correcto.</span><span class="sxs-lookup"><span data-stu-id="fc87d-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span> |
|<span data-ttu-id="fc87d-167">**Recuperación extendida**</span><span class="sxs-lookup"><span data-stu-id="fc87d-167">**Extended recovery**</span></span> | <span data-ttu-id="fc87d-p115">Este estado indica que se están llevando a cabo acciones correctivas para restablecer el servicio para la mayoría de los usuarios, pero que llevará algún tiempo llegar a todos los sistemas afectados. También es posible que vea este estado en caso de que hayamos aplicado una solución temporal para reducir el impacto a la espera de aplicar una permanente.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span> |
|<span data-ttu-id="fc87d-170">**Investigación suspendida**</span><span class="sxs-lookup"><span data-stu-id="fc87d-170">**Investigation suspended**</span></span> | <span data-ttu-id="fc87d-p116">Si nuestra investigación detallada sobre un problema potencial resulta en una solicitud de información adicional por parte de los clientes para permitirnos investigar de forma más exhaustiva, verá este estado. Si necesitamos su ayuda, le haremos saber qué datos y registros necesitamos.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span> |
|<span data-ttu-id="fc87d-173">**Servicio restaurado**</span><span class="sxs-lookup"><span data-stu-id="fc87d-173">**Service restored**</span></span> | <span data-ttu-id="fc87d-p117">Hemos confirmado que una acción correctiva ha resuelto el problema subyacente y el servicio se ha restaurado al estado correcto. Para averiguar qué ha fallado, vea los detalles del problema.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span> |
|<span data-ttu-id="fc87d-176">**Informe del incidente posteriores a la publicado**</span><span class="sxs-lookup"><span data-stu-id="fc87d-176">**Post-incident report published**</span></span> | <span data-ttu-id="fc87d-177">Hemos publicado un informe del incidente Post para un problema específico que incluye información de la causa raíz y pasos siguientes para asegurarse de que no volver a producirse un problema similar.</span><span class="sxs-lookup"><span data-stu-id="fc87d-177">We’ve published a Post Incident Report for a specific issue that includes root cause information and next steps to ensure a similar issue doesn’t reoccur.</span></span> |
   
## <a name="history"></a><span data-ttu-id="fc87d-178">Historial</span><span class="sxs-lookup"><span data-stu-id="fc87d-178">History</span></span>

<span data-ttu-id="fc87d-p118">El estado del servicio le permite ver el estado actual y el historial de los incidentes y avisos del servicio que se hayan producido durante los últimos 30 días. Para ver el estado anterior de todos los servicios, seleccione **Ver historial** en la página **Estado del servicio**.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="fc87d-182">Se muestra una lista de todos los mensajes del estado del servicio publicados en el período de tiempo seleccionado, como se puede ver a continuación:</span><span class="sxs-lookup"><span data-stu-id="fc87d-182">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="fc87d-p119">Puede ver el historial de mantenimiento para los últimos 7 días o últimos 30 días. Seleccione cualquier fila para ver más detalles acerca del problema.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="fc87d-186">Para obtener más información acerca de nuestro compromiso de tiempo de actividad, vea [operations transparentes de Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="fc87d-186">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="fc87d-187">Enviar comentarios</span><span class="sxs-lookup"><span data-stu-id="fc87d-187">Leave feedback</span></span>

<span data-ttu-id="fc87d-p120">Nuestro objetivo es asegurarnos de que la información que le proporcionamos sobre un problema en curso sea oportuna, precisa y útil. Para indicarnos su opinión sobre nuestra actuación, seleccione una clasificación por estrellas. Una vez que nos haya valorado con una puntuación de 1 a 5 estrellas, podrá enviar comentarios sobre detalles específicos. Usaremos sus comentarios para ajustar nuestro sistema de estado del servicio.</span><span class="sxs-lookup"><span data-stu-id="fc87d-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="fc87d-193">Vea también</span><span class="sxs-lookup"><span data-stu-id="fc87d-193">See also</span></span>

[<span data-ttu-id="fc87d-194">Informes de actividades en el Centro de administración de Office 365</span><span class="sxs-lookup"><span data-stu-id="fc87d-194">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

