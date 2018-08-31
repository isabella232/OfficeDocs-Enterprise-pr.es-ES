---
title: Cómo comprobar el estado del servicio Office 365
ms.author: kfollis
author: kfollis
manager: scotv
ms.date: 6/15/2018
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
ms.openlocfilehash: d01fe8e269ace922ab92cca779d6f8fea8b6802e
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542763"
---
# <a name="how-to-check-office-365-service-health"></a><span data-ttu-id="a9a31-103">Cómo comprobar el estado del servicio Office 365</span><span class="sxs-lookup"><span data-stu-id="a9a31-103">How to check Office 365 service health</span></span>

<span data-ttu-id="a9a31-p101">Puede ver el estado de Office 365, Yammer, Microsoft Dynamics CRM y servicios de nube de Microsoft Intune en Office 365 ** de servicio de estado ** página en el centro de administración. Si experimenta problemas con un servicio de nube, puede comprobar el estado del servicio para determinar si se trata de un problema conocido con una resolución en curso antes de llamar al soporte técnico o dedicada a la solución de problemas de tiempo.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p101">You can view the health of Office 365, Yammer, Microsoft Dynamics CRM, and Microsoft Intune cloud services on the Office 365 ** Service health ** page in the admin center. If you are experiencing problems with a cloud service, you can check the service health to determine whether this is a known issue with a resolution in progress before you call support or spend time troubleshooting.</span></span> 
  
### <a name="how-to-check-service-health"></a><span data-ttu-id="a9a31-106">Cómo comprobar el estado del servicio</span><span class="sxs-lookup"><span data-stu-id="a9a31-106">How to check service health</span></span>

1. <span data-ttu-id="a9a31-107">Vaya a [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) y el inicio de sesión con una cuenta de administrador.</span><span class="sxs-lookup"><span data-stu-id="a9a31-107">Go to [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) and sign in with an admin account.</span></span> 
    
    > [!NOTE]
    > <span data-ttu-id="a9a31-p102">Las personas que tengan asignadas el administrador global o el rol de administrador de servicio pueden ver el estado del servicio. Para permitir que Exchange, SharePoint y Skype para los administradores de negocio ver el estado del servicio, se debe también asignar el rol de administrador de servicio.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p102">People who are assigned the global admin or service administrator role can view service health. To allow Exchange, SharePoint, and Skype for Business admins to view service health, they must also be assigned the Service admin role.</span></span> 
  
2. <span data-ttu-id="a9a31-p103">Para abrir el estado del servicio, en el centro de administración, vaya a **Mantenimiento** \> **estado del servicio**, o haga clic en el estado del servicio de tarjetas en el panel principal. La tarjeta de panel indica si hay un problema de servicio de active y vínculos a la página de estado de servicio detallados.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p103">To open service health, in the admin center, go to **Health** \> **Service health**, or click the Service health card on the Home dashboard. The dashboard card indicates whether there is an active service issue and links to the detailed service health page.</span></span>
    
    ![Tarjeta de panel de estado del servicio](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. <span data-ttu-id="a9a31-113">El estado de mantenimiento de cada servicio de nube se muestra en un formato de tabla con un icono para indicar estados posibles.</span><span class="sxs-lookup"><span data-stu-id="a9a31-113">The health state of each cloud service is shown in a table format with an icon to indicate possible states.</span></span>
    
> [!TIP]
> <span data-ttu-id="a9a31-114">También puede usar la [aplicación de administración de Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) en su dispositivo móvil para ver el estado del servicio, que es una excelente manera de mantenerse al día con las notificaciones de inserción.</span><span class="sxs-lookup"><span data-stu-id="a9a31-114">You can also use the [Office 365 Admin app](https://go.microsoft.com/fwlink/p/?linkid=627216) on your mobile device to view Service health, which is a great way to stay current with push notifications.</span></span> 
  
### <a name="view-details-of-posted-service-health"></a><span data-ttu-id="a9a31-115">Visualización de detalles de mantenimiento de servicio registrado</span><span class="sxs-lookup"><span data-stu-id="a9a31-115">View details of posted service health</span></span>

<span data-ttu-id="a9a31-p104">En la vista predeterminada, se muestran todos los servicios y su estado de mantenimiento actual. Para filtrar la vista a servicios está experimentando un incidente, seleccione **incidentes** en la barra de sombreado de la izquierda. Selección de **avisos** mostrará únicamente los servicios que actualmente tienen un asesor registrado. Desde la vista de **todos los servicios** , haciendo clic en el estado del servicio que se muestra se abrirá una vista de resumen del documento informativo o incidente.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p104">In the default view, all services and their current health state are displayed. To filter your view to services currently experiencing an incident, select **Incidents** from the shaded bar on the left. Selecting **Advisories** will show only services that currently have an advisory posted. From the **All services** view, clicking the displayed service state will open a summary view of the advisory or incident.</span></span> 
  
![Vista de problemas actuales en el estado del servicio](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
<span data-ttu-id="a9a31-121">El documento informativo o incidente resumen proporciona la siguiente información:</span><span class="sxs-lookup"><span data-stu-id="a9a31-121">The advisory or incident summary provides the following information:</span></span> 
  
![Una captura de pantalla etiquetar los campos en un documento informativo de servicio](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. <span data-ttu-id="a9a31-123">Un problema resumen y el identificador de instrucción del problema.</span><span class="sxs-lookup"><span data-stu-id="a9a31-123">An issue identifier and summary statement of the problem.</span></span>
    
2. <span data-ttu-id="a9a31-p105">El estado actual. Consulte las definiciones de estado en este artículo para obtener una explicación de cada estado posible.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p105">The current status. See status definitions in this article for an explanation of each potential status.</span></span>
    
3. <span data-ttu-id="a9a31-126">Una descripción de cómo este problema puede afectar a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="a9a31-126">A description of how this issue can affect users.</span></span>
    
4. <span data-ttu-id="a9a31-p106">La hora en que se inició el problema y la última vez que se actualizó el mensaje de estado de servicio. A lo largo de la duración de un problema se publicar mensajes frecuentes para darle a conocer el progreso que estamos haciendo que en la aplicación de una solución.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p106">The time that the issue was started and the last time that the service health message was updated. Throughout the duration of an issue we post frequent messages to let you know the progress that we're making in applying a solution.</span></span>
    
5. <span data-ttu-id="a9a31-129">Seleccione el vínculo **Mostrar detalles** para ver más detalles sobre el problema, incluido el historial de todos los mensajes expuestos mientras se trabaja en una solución.</span><span class="sxs-lookup"><span data-stu-id="a9a31-129">Select the **Show details** link to see more details about the issue, including the history of all messages posted while we work on a solution.</span></span> 
    
### <a name="translate-service-health-details"></a><span data-ttu-id="a9a31-130">Traducir detalles de mantenimiento de servicio</span><span class="sxs-lookup"><span data-stu-id="a9a31-130">Translate service health details</span></span>

<span data-ttu-id="a9a31-p107">Debido a que se publican explicaciones de mantenimiento de servicio en tiempo real, no se convierten automáticamente a su idioma y los detalles de un evento de servicio sólo están disponibles en inglés. Para traducir la explicación, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="a9a31-p107">Because service health explanations are posted in real-time, they are not automatically translated to your language and the details of a service event are in English only. To translate the explanation, follow these steps:</span></span>
  
1. <span data-ttu-id="a9a31-133">Vaya al [traductor](https://www.bing.com/translator/).</span><span class="sxs-lookup"><span data-stu-id="a9a31-133">Go to [Translator](https://www.bing.com/translator/).</span></span>
    
2. <span data-ttu-id="a9a31-p108">En la página de **estado del servicio** , seleccione un incidente o documento informativo. En **Mostrar detalles**, copie el texto sobre el problema.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p108">On the **Service health** page, select an incident or advisory. Under **Show details**, copy the text about the issue.</span></span>
    
3. <span data-ttu-id="a9a31-136">En traductor, pegue el texto y elegir **traducir**.</span><span class="sxs-lookup"><span data-stu-id="a9a31-136">In Translator, paste the text and choose **Translate**.</span></span>
    
### <a name="definitions"></a><span data-ttu-id="a9a31-137">Definiciones</span><span class="sxs-lookup"><span data-stu-id="a9a31-137">Definitions</span></span>

<span data-ttu-id="a9a31-p109">La mayoría de los servicios de tiempo se mostrará como correcto sin más información. Cuando un servicio tiene un problema, el problema se identifica como un documento informativo o un incidente y muestra el estado actual.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p109">Most of the time services will appear as healthy with no further information. When a service is having a problem, the issue is identified as either an advisory or an incident and shows a current status.</span></span>
  
> [!TIP]
> <span data-ttu-id="a9a31-p110">Planeado mantenimiento no se muestran en estado del servicio de eventos. Para realizar un seguimiento de eventos de mantenimiento planeado por mantenerse actualizado con el **Centro de mensajes**. Filtrar de modo que los mensajes que se pueden clasificados como Plan for cambio para averiguar cuando va a que se produzca el cambio, su efecto y a prepararse para el mismo. Para obtener más información, vea [Centro de mensajes en Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) .</span><span class="sxs-lookup"><span data-stu-id="a9a31-p110">Planned maintenance events aren't shown in service health. You can track planned maintenance events by staying up to date with the **Message center**. Filter to messages categorized as Plan for change to find out when the change is going to happen, its effect, and how to prepare for it. See [Message center in Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) for more details.</span></span> 
  
### <a name="incidents-and-advisories"></a><span data-ttu-id="a9a31-144">Incidentes y avisos</span><span class="sxs-lookup"><span data-stu-id="a9a31-144">Incidents and advisories</span></span>

|||
|:-----|:-----|
|![Icono de información de documento informativo](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|<span data-ttu-id="a9a31-p111">Si un servicio tiene un aviso que se muestra, sabemos de un problema que afecta a algunos usuarios, pero el servicio sigue estando disponible. En un documento informativo, a menudo es una solución al problema y el problema puede ser intermitente o está limitado en el impacto de ámbito y usuario.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p111">If a service has an advisory shown, we are aware of a problem that is affecting some users, but the service is still available. In an advisory, there is often a workaround to the problem and the problem may be intermittent or is limited in scope and user impact.</span></span>  <br/> |
|![Icono de signo de exclamación de incidente](media/a636db57-6083-44dc-bbd5-556850804f17.png)|<span data-ttu-id="a9a31-p112">Si un servicio tiene un incidente activo que se muestra, es un problema crítico y el servicio o una función principal del servicio no está disponible. Por ejemplo, es posible que pueda a los usuarios enviar y recibir correo electrónico o no se ha podido inicio de sesión. incidentes tendrá notable impacto en los usuarios. Cuando hay un incidente en curso, proporcionamos actualizaciones de la investigación, los esfuerzos de mitigación y confirmación de resolución en el panel de estado de servicio.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p112">If a service has an active incident shown, it's a critical issue and the service or a major function of the service is unavailable. For example, users may be unable to send and receive email or unable to sign-in. Incidents will have noticeable impact to users. When there is an incident in progress, we will provide updates regarding the investigation, mitigation efforts, and confirmation of resolution in the Service health dashboard.</span></span>  <br/> |
   
### <a name="status-definitions"></a><span data-ttu-id="a9a31-153">Definiciones de estado</span><span class="sxs-lookup"><span data-stu-id="a9a31-153">Status definitions</span></span>

<span data-ttu-id="a9a31-154">| |</span><span class="sxs-lookup"><span data-stu-id="a9a31-154"></span></span>
|<span data-ttu-id="a9a31-155">**Estado**</span><span class="sxs-lookup"><span data-stu-id="a9a31-155">**Status**</span></span>|<span data-ttu-id="a9a31-156">**Definición**</span><span class="sxs-lookup"><span data-stu-id="a9a31-156">**Definition**</span></span>|
|:-----|:-----|
|<span data-ttu-id="a9a31-157">Investigar</span><span class="sxs-lookup"><span data-stu-id="a9a31-157">Investigating</span></span>  <br/> |<span data-ttu-id="a9a31-158">Se está al tanto de un posible problema y se recopilar más información sobre lo que está ocurriendo y el ámbito de impacto.</span><span class="sxs-lookup"><span data-stu-id="a9a31-158">We're aware of a potential issue and are gathering more information about what's going on and the scope of impact.</span></span>  <br/> |
|<span data-ttu-id="a9a31-159">Degradación del servicio</span><span class="sxs-lookup"><span data-stu-id="a9a31-159">Service degradation</span></span>  <br/> |<span data-ttu-id="a9a31-p113">Hemos confirmado que hay un problema que puede afectar al uso de un servicio o característica. Es posible que vea este estado si un servicio está llevando a cabo más lentamente de lo habitual, hay interrupciones intermitentes, o si una característica no funciona, por ejemplo.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p113">We've confirmed that there is an issue that may affect use of a service or feature. You might see this status if a service is performing more slowly than usual, there are intermittent interruptions, or if a feature isn't working, for example.</span></span>  <br/> |
|<span data-ttu-id="a9a31-162">Interrupción del servicio</span><span class="sxs-lookup"><span data-stu-id="a9a31-162">Service interruption</span></span>  <br/> |<span data-ttu-id="a9a31-p114">Verá este estado si se determina que un problema afecta a la capacidad de los usuarios tener acceso al servicio. En este caso, el problema es significativo y puede reproducir de forma coherente.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p114">You'll see this status if we determine that an issue affects the ability for users to access the service. In this case, the issue is significant and can be reproduced consistently.</span></span>  <br/> |
|<span data-ttu-id="a9a31-165">Restauración del servicio</span><span class="sxs-lookup"><span data-stu-id="a9a31-165">Restoring service</span></span>  <br/> |<span data-ttu-id="a9a31-166">Se ha identificado la causa del problema, sabemos qué que llevar a cabo una acción correctiva y están en el proceso de mejorar el servicio de estado correcto.</span><span class="sxs-lookup"><span data-stu-id="a9a31-166">The cause of the issue has been identified, we know what corrective action to take, and are in the process of bringing the service back to a healthy state.</span></span>  <br/> |
|<span data-ttu-id="a9a31-167">Recuperación extendida</span><span class="sxs-lookup"><span data-stu-id="a9a31-167">Extended recovery</span></span>  <br/> |<span data-ttu-id="a9a31-p115">Este estado indica que una acción correctiva está en curso para restaurar el servicio a la mayoría de los usuarios, pero tardará algún tiempo en llegar a todos los sistemas afectados. También es posible que vea este estado si hemos hecho temporal corregir para reducir el impacto mientras se espera que se debe aplicar una solución permanente.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p115">This status indicates that corrective action is in progress to restore service to most users but will take some time to reach all the affected systems. You might also see this status if we've made a temporary fix to reduce impact while we wait to apply a permanent fix.</span></span>  <br/> |
|<span data-ttu-id="a9a31-170">Investigación suspendida</span><span class="sxs-lookup"><span data-stu-id="a9a31-170">Investigation suspended</span></span>  <br/> |<span data-ttu-id="a9a31-p116">Si se produce una solicitud para obtener información adicional de los clientes para permitir que nos investigar aún más nuestra investigación detallada de un posible problema, verá este estado. Si necesitamos actuar, le dejaremos saber qué datos o los registros que necesitamos.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p116">If our detailed investigation of a potential issue results in a request for additional information from customers to allow us to investigate further, you'll see this status. If we need you to act, we'll let you know what data or logs we need.</span></span>  <br/> |
|<span data-ttu-id="a9a31-173">Servicio restaurado</span><span class="sxs-lookup"><span data-stu-id="a9a31-173">Service restored</span></span>  <br/> |<span data-ttu-id="a9a31-p117">Hemos confirmado que una acción correctiva ha resuelto el problema subyacente y el servicio se ha restaurado a un estado correcto. Para averiguar lo que salió mal, ver los detalles del problema.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p117">We've confirmed that corrective action has resolved the underlying problem and the service has been restored to a healthy state. To find out what went wrong, view the issue details.</span></span>  <br/> |
   
## <a name="history"></a><span data-ttu-id="a9a31-176">Historial</span><span class="sxs-lookup"><span data-stu-id="a9a31-176">History</span></span>

<span data-ttu-id="a9a31-p118">Estado del servicio permite mirar el estado actual de mantenimiento y ver el historial de los avisos de servicio y los incidentes en los últimos 30 días. Para ver el estado de todos los servicios anteriores, seleccione **Ver historial de** en la página de **estado del servicio** .</span><span class="sxs-lookup"><span data-stu-id="a9a31-p118">Service health lets you look at current health status and view the history of any service advisories and incidents in the past 30 days. To view the past health of all services, select **View history** on the **Service health** page.</span></span> 
  
![Mostrar vínculo a historial de mantenimiento](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
<span data-ttu-id="a9a31-180">Se muestra una lista de todos los mensajes de estado de servicio registrado en el período de tiempo seleccionado, tal y como se muestra a continuación:</span><span class="sxs-lookup"><span data-stu-id="a9a31-180">A list of all service health messages posted in the selected timeframe is displayed, as shown below:</span></span>
  
![Ver historial de mantenimiento de servicio](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
<span data-ttu-id="a9a31-p119">Puede ver el historial de mantenimiento para los últimos 7 días o últimos 30 días. Seleccione cualquier fila para ver más detalles acerca del problema.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p119">You may view the health history for either the last 7 days or last 30 days. Select any row to view more details about that issue.</span></span>
  
<span data-ttu-id="a9a31-184">Para obtener más información acerca de nuestro compromiso de tiempo de actividad, vea [operations transparentes de Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span><span class="sxs-lookup"><span data-stu-id="a9a31-184">For more information about our commitment to uptime, see [Transparent operations from Office 365](https://go.microsoft.com/fwlink/?linkid=848695).</span></span>
  
## <a name="leave-feedback"></a><span data-ttu-id="a9a31-185">Votar</span><span class="sxs-lookup"><span data-stu-id="a9a31-185">Leave feedback</span></span>

<span data-ttu-id="a9a31-p120">Nuestro objetivo es asegurarse de que la información que proporcionamos a usted sobre un problema de curso es oportuna, precisa y útil. Para Díganos cómo lo estamos haciendo, seleccione una clasificación por estrellas. Una vez que háganos una puntuación de 1 a 5 estrellas, puede proporcionar comentarios en cualquier detalles específicos. Vamos a utilizar los comentarios para ajustar con precisión nuestro sistema de mantenimiento de servicio.</span><span class="sxs-lookup"><span data-stu-id="a9a31-p120">Our goal is to make sure that the information we provide to you about an ongoing issue is timely, accurate, and useful. To tell us how we're doing, select a star rating. After you give us a score from 1 to 5 stars, you can give feedback on any specific details. We'll use your feedback to fine-tune our service health system.</span></span>
  
![Formulario de comentarios para problemas de mantenimiento de servicio](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a><span data-ttu-id="a9a31-191">Vea también</span><span class="sxs-lookup"><span data-stu-id="a9a31-191">See also</span></span>

[<span data-ttu-id="a9a31-192">Informes de actividad en el centro de administración de Office 365</span><span class="sxs-lookup"><span data-stu-id="a9a31-192">Activity Reports in the Office 365 admin center</span></span>](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

