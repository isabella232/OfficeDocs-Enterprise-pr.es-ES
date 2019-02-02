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
ms.openlocfilehash: 52a7b762b8e86c3e538579f7c1e1611515469389
ms.sourcegitcommit: c7ad181394a8a3ee261dc44e7a1e70f6ebe7cbcf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "29696357"
---
# <a name="how-to-check-office-365-service-health"></a>Cómo comprobar el estado del servicio de Office 365

Puede ver el estado de Office 365, Yammer, Microsoft Dynamics CRM y servicios de nube de Microsoft Intune en la página de **estado del servicio** de Office 365 en el centro de administración. Si experimenta problemas con un servicio de nube, puede comprobar el estado del servicio para determinar si se trata de un problema conocido con una resolución en curso antes de llamar al soporte técnico o dedicada a la solución de problemas de tiempo. 

Si no puede iniciar sesión en el portal de servicio, puede usar la [página de estado de servicio](https://status.office365.com) para buscar problemas conocidos que le impide iniciar sesión en el inquilino.
  
### <a name="how-to-check-service-health"></a>Cómo comprobar el estado del servicio

1. Vaya a [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) e inicie sesión con una cuenta de administrador. 
    
    > [!NOTE]
    > Los usuarios que tienen asignado el rol de administrador de servicios o administrador global pueden ver el estado del servicio. Para que los administradores de Exchange, SharePoint y Skype Empresarial puedan ver el estado del servicio, también se les debe asignar el rol Administrador de servicios.
  
2. Para abrir el estado del servicio, en el centro de administración, vaya a **Mantenimiento** > **estado del servicio**, o haga clic en la **tarjeta de servicio de estado** en el **panel principal**. La tarjeta de panel indica si hay un problema de servicio de active y vínculos a la página de estado de servicio detallados.
    
    ![Dashboard card for service health](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. El estado de mantenimiento de cada servicio en la nube se muestra en formato de tabla con un icono para indicar los posibles estados.
    
> [!TIP]
> También puede usar la [aplicación de administración de Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) en su dispositivo móvil para ver el estado del servicio, que es una buena forma de mantenerse al día con las notificaciones de inserción. 
  
### <a name="view-details-of-posted-service-health"></a>Ver detalles del estado del servicio publicado

En la vista predeterminada, se muestran todos los servicios y su estado de mantenimiento actual. Para filtrar la vista a servicios está experimentando un incidente, seleccione **incidentes** en la barra de sombreado de la izquierda. Selección de **avisos** mostrará únicamente los servicios que actualmente tienen un asesor registrado. Desde la vista de **todos los servicios** , haciendo clic en el estado del servicio que se muestra se abrirá una vista de resumen del documento informativo o incidente. 
  
![View of current issues in service health](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
En el resumen del aviso o del incidente, se proporciona la siguiente información: 
  
![Una captura de pantalla etiquetar los campos en un documento informativo de servicio](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. Identificador y resumen de un problema.
    
2. Estado actual. Consulte las definiciones de este artículo para conocer la explicación de cada posible estado.
    
3. Descripción de cómo este problema puede afectar a los usuarios.
    
4. Hora en la que se inició el problema y hora en la que se actualizó el mensaje del estado del servicio por última vez. Mientras el problema se sigue produciendo, publicamos mensajes frecuentes para informarle de nuestro progreso en la aplicación de una solución.
    
5. Seleccione el vínculo **Mostrar detalles** para ver más detalles sobre el problema, incluido el historial de todos los mensajes publicados mientras trabajamos en encontrar una solución. 
    
### <a name="translate-service-health-details"></a>Detalles del estado del servicio de traducción

Como las explicaciones del estado del servicio se publican en tiempo real, no se traducen automáticamente a su idioma y los detalles de los eventos de servicio se muestran solo en inglés. Para traducir la explicación, siga estos pasos:
  
1. Vaya a [Traductor](https://www.bing.com/translator/).
    
2. En la página **Estado del servicio**, seleccione un incidente o un aviso. En **Mostrar detalles**, copie el texto sobre el problema.
    
3. En el traductor, pegue el texto y elija **Traducir**.
    
### <a name="definitions"></a>Definiciones

La mayoría de las veces, los servicios aparecerán como correctos sin más información. Cuando un servicio experimenta un problema, este se identifica como aviso o incidente y se muestra el estado actual.
  
> [!TIP]
> Los eventos de mantenimiento planeados se muestran en el estado del servicio. Puede realizar un seguimiento de los eventos de mantenimiento planeados manteniéndose al día con el **Centro de mensajes**. Filtre por los mensajes de la categoría Planear el cambio para descubrir cuándo sucederá el cambio, el efecto que tendrá y cómo debe prepararse para afrontarlo. Vea [Centro de mensajes de Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) para obtener más detalles. 
  
### <a name="incidents-and-advisories"></a>Incidentes y avisos

|||
|:-----|:-----|
|![Information icon for advisory](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Si se muestra un aviso en un servicio, significa que somos conscientes de que existe un problema que está afectando a algunos usuarios, pero el servicio todavía está disponible. En los avisos, suele haber una solución alternativa para el problema y es posible que este se produzca de forma intermitente o que esté limitado a unas consecuencias para el usuario y a un ámbito específicos.  <br/> |
|![Exclamation point icon for incident](media/a636db57-6083-44dc-bbd5-556850804f17.png)|Si, en un servicio, se muestra un incidente activo, significa que existe un problema crítico y que el servicio o una de las características principales del servicio no está disponible. Por ejemplo, es posible que los usuarios no puedan enviar ni recibir correo electrónico o que no puedan iniciar sesión. Los incidentes tendrán un impacto notable sobre los usuarios. Cuando haya un incidente en curso, ofreceremos actualizaciones en relación con la investigación, las acciones llevadas a cabo y la confirmación de la resolución en el panel Estado del servicio.  <br/> |
   
### <a name="status-definitions"></a>Definiciones de los estados

|**Estado**|**Definición**|
|:-----|:-----|
|**Bajo investigación** | Somos conscientes de que existe un problema potencial y estamos recopilando más información sobre lo que sucede y el ámbito de impacto. |
|**Degradación del servicio** | Hemos confirmado que existe un problema que puede afectar al uso de un servicio o una característica. Es posible que vea este estado si un servicio está funcionando más lento de lo normal, si hay interrupciones intermitentes o si una característica no funciona, por ejemplo. |
|**Interrupción del servicio** | Verá este estado si se determina que un problema afecta a posibilidad de los usuarios de obtener acceso al servicio. En este caso, el problema es importante y se puede reproducir de forma coherente. |
|**Restaurando el servicio** | Se ha identificado la causa del problema, sabemos qué acción correctiva debemos aplicar y estamos en proceso de restablecer el servicio a un estado correcto. |
|**Recuperación extendida** | Este estado indica que se están llevando a cabo acciones correctivas para restablecer el servicio para la mayoría de los usuarios, pero que llevará algún tiempo llegar a todos los sistemas afectados. También es posible que vea este estado en caso de que hayamos aplicado una solución temporal para reducir el impacto a la espera de aplicar una permanente. |
|**Investigación suspendida** | Si nuestra investigación detallada sobre un problema potencial resulta en una solicitud de información adicional por parte de los clientes para permitirnos investigar de forma más exhaustiva, verá este estado. Si necesitamos su ayuda, le haremos saber qué datos y registros necesitamos. |
|**Servicio restaurado** | Hemos confirmado que una acción correctiva ha resuelto el problema subyacente y el servicio se ha restaurado al estado correcto. Para averiguar qué ha fallado, vea los detalles del problema. |
|**Informe del incidente posteriores a la publicado** | Hemos publicado un informe del incidente Post para un problema específico que incluye información de la causa raíz y pasos siguientes para asegurarse de que no volver a producirse un problema similar. |
   
## <a name="history"></a>Historial

Estado del servicio permite a mirar el estado actual de mantenimiento y ver el historial de los avisos de servicio y los incidentes que han afectado al inquilino en los últimos 30 días. Para ver el estado de todos los servicios anteriores, seleccione **Ver historial de** en la página de **estado del servicio** . 
  
![Show link to health history](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
Se muestra una lista de todos los mensajes del estado del servicio publicados en el período de tiempo seleccionado, como se puede ver a continuación:
  
![View service health history](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
Puede ver el historial de mantenimiento para los últimos 7 días o últimos 30 días. Seleccione cualquier fila para ver más detalles acerca del problema.
  
Para obtener más información acerca de nuestro compromiso de tiempo de actividad, vea [operations transparentes de Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Enviar comentarios

Nuestro objetivo es asegurarnos de que la información que le proporcionamos sobre un problema en curso sea oportuna, precisa y útil. Para indicarnos su opinión sobre nuestra actuación, seleccione una clasificación por estrellas. Una vez que nos haya valorado con una puntuación de 1 a 5 estrellas, podrá enviar comentarios sobre detalles específicos. Usaremos sus comentarios para ajustar nuestro sistema de estado del servicio.
  
![Feedback form for service health issues](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a>Vea también

[Informes de actividades en el Centro de administración de Office 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

