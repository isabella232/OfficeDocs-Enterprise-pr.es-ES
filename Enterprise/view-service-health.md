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
# <a name="how-to-check-office-365-service-health"></a>Cómo comprobar el estado del servicio Office 365

Puede ver el estado de Office 365, Yammer, Microsoft Dynamics CRM y servicios de nube de Microsoft Intune en Office 365 ** de servicio de estado ** página en el centro de administración. Si experimenta problemas con un servicio de nube, puede comprobar el estado del servicio para determinar si se trata de un problema conocido con una resolución en curso antes de llamar al soporte técnico o dedicada a la solución de problemas de tiempo. 
  
### <a name="how-to-check-service-health"></a>Cómo comprobar el estado del servicio

1. Vaya a [https://portal.office.com/adminportal/home](https://portal.office.com/adminportal/home#/homepage) y el inicio de sesión con una cuenta de administrador. 
    
    > [!NOTE]
    > Las personas que tengan asignadas el administrador global o el rol de administrador de servicio pueden ver el estado del servicio. Para permitir que Exchange, SharePoint y Skype para los administradores de negocio ver el estado del servicio, se debe también asignar el rol de administrador de servicio. 
  
2. Para abrir el estado del servicio, en el centro de administración, vaya a **Mantenimiento** \> **estado del servicio**, o haga clic en el estado del servicio de tarjetas en el panel principal. La tarjeta de panel indica si hay un problema de servicio de active y vínculos a la página de estado de servicio detallados.
    
    ![Tarjeta de panel de estado del servicio](media/8ae3de43-7bd5-4ee9-90ed-8b5ba5f9b474.png)
  
3. El estado de mantenimiento de cada servicio de nube se muestra en un formato de tabla con un icono para indicar estados posibles.
    
> [!TIP]
> También puede usar la [aplicación de administración de Office 365](https://go.microsoft.com/fwlink/p/?linkid=627216) en su dispositivo móvil para ver el estado del servicio, que es una excelente manera de mantenerse al día con las notificaciones de inserción. 
  
### <a name="view-details-of-posted-service-health"></a>Visualización de detalles de mantenimiento de servicio registrado

En la vista predeterminada, se muestran todos los servicios y su estado de mantenimiento actual. Para filtrar la vista a servicios está experimentando un incidente, seleccione **incidentes** en la barra de sombreado de la izquierda. Selección de **avisos** mostrará únicamente los servicios que actualmente tienen un asesor registrado. Desde la vista de **todos los servicios** , haciendo clic en el estado del servicio que se muestra se abrirá una vista de resumen del documento informativo o incidente. 
  
![Vista de problemas actuales en el estado del servicio](media/f829a3af-1aca-4dc2-97eb-15d805349b24.png)
  
El documento informativo o incidente resumen proporciona la siguiente información: 
  
![Una captura de pantalla etiquetar los campos en un documento informativo de servicio](media/0dd6065c-1381-4a5c-8ca0-854c3e043a5c.png)
  
1. Un problema resumen y el identificador de instrucción del problema.
    
2. El estado actual. Consulte las definiciones de estado en este artículo para obtener una explicación de cada estado posible.
    
3. Una descripción de cómo este problema puede afectar a los usuarios.
    
4. La hora en que se inició el problema y la última vez que se actualizó el mensaje de estado de servicio. A lo largo de la duración de un problema se publicar mensajes frecuentes para darle a conocer el progreso que estamos haciendo que en la aplicación de una solución.
    
5. Seleccione el vínculo **Mostrar detalles** para ver más detalles sobre el problema, incluido el historial de todos los mensajes expuestos mientras se trabaja en una solución. 
    
### <a name="translate-service-health-details"></a>Traducir detalles de mantenimiento de servicio

Debido a que se publican explicaciones de mantenimiento de servicio en tiempo real, no se convierten automáticamente a su idioma y los detalles de un evento de servicio sólo están disponibles en inglés. Para traducir la explicación, siga estos pasos:
  
1. Vaya al [traductor](https://www.bing.com/translator/).
    
2. En la página de **estado del servicio** , seleccione un incidente o documento informativo. En **Mostrar detalles**, copie el texto sobre el problema.
    
3. En traductor, pegue el texto y elegir **traducir**.
    
### <a name="definitions"></a>Definiciones

La mayoría de los servicios de tiempo se mostrará como correcto sin más información. Cuando un servicio tiene un problema, el problema se identifica como un documento informativo o un incidente y muestra el estado actual.
  
> [!TIP]
> Planeado mantenimiento no se muestran en estado del servicio de eventos. Para realizar un seguimiento de eventos de mantenimiento planeado por mantenerse actualizado con el **Centro de mensajes**. Filtrar de modo que los mensajes que se pueden clasificados como Plan for cambio para averiguar cuando va a que se produzca el cambio, su efecto y a prepararse para el mismo. Para obtener más información, vea [Centro de mensajes en Office 365](https://support.office.com/article/38fb3333-bfcc-4340-a37b-deda509c2093) . 
  
### <a name="incidents-and-advisories"></a>Incidentes y avisos

|||
|:-----|:-----|
|![Icono de información de documento informativo](media/a7f5fd21-c760-4948-9bc1-50f7c8070e28.png)|Si un servicio tiene un aviso que se muestra, sabemos de un problema que afecta a algunos usuarios, pero el servicio sigue estando disponible. En un documento informativo, a menudo es una solución al problema y el problema puede ser intermitente o está limitado en el impacto de ámbito y usuario.  <br/> |
|![Icono de signo de exclamación de incidente](media/a636db57-6083-44dc-bbd5-556850804f17.png)|Si un servicio tiene un incidente activo que se muestra, es un problema crítico y el servicio o una función principal del servicio no está disponible. Por ejemplo, es posible que pueda a los usuarios enviar y recibir correo electrónico o no se ha podido inicio de sesión. incidentes tendrá notable impacto en los usuarios. Cuando hay un incidente en curso, proporcionamos actualizaciones de la investigación, los esfuerzos de mitigación y confirmación de resolución en el panel de estado de servicio.  <br/> |
   
### <a name="status-definitions"></a>Definiciones de estado

| |
|**Estado**|**Definición**|
|:-----|:-----|
|Investigar  <br/> |Se está al tanto de un posible problema y se recopilar más información sobre lo que está ocurriendo y el ámbito de impacto.  <br/> |
|Degradación del servicio  <br/> |Hemos confirmado que hay un problema que puede afectar al uso de un servicio o característica. Es posible que vea este estado si un servicio está llevando a cabo más lentamente de lo habitual, hay interrupciones intermitentes, o si una característica no funciona, por ejemplo.  <br/> |
|Interrupción del servicio  <br/> |Verá este estado si se determina que un problema afecta a la capacidad de los usuarios tener acceso al servicio. En este caso, el problema es significativo y puede reproducir de forma coherente.  <br/> |
|Restauración del servicio  <br/> |Se ha identificado la causa del problema, sabemos qué que llevar a cabo una acción correctiva y están en el proceso de mejorar el servicio de estado correcto.  <br/> |
|Recuperación extendida  <br/> |Este estado indica que una acción correctiva está en curso para restaurar el servicio a la mayoría de los usuarios, pero tardará algún tiempo en llegar a todos los sistemas afectados. También es posible que vea este estado si hemos hecho temporal corregir para reducir el impacto mientras se espera que se debe aplicar una solución permanente.  <br/> |
|Investigación suspendida  <br/> |Si se produce una solicitud para obtener información adicional de los clientes para permitir que nos investigar aún más nuestra investigación detallada de un posible problema, verá este estado. Si necesitamos actuar, le dejaremos saber qué datos o los registros que necesitamos.  <br/> |
|Servicio restaurado  <br/> |Hemos confirmado que una acción correctiva ha resuelto el problema subyacente y el servicio se ha restaurado a un estado correcto. Para averiguar lo que salió mal, ver los detalles del problema.  <br/> |
   
## <a name="history"></a>Historial

Estado del servicio permite mirar el estado actual de mantenimiento y ver el historial de los avisos de servicio y los incidentes en los últimos 30 días. Para ver el estado de todos los servicios anteriores, seleccione **Ver historial de** en la página de **estado del servicio** . 
  
![Mostrar vínculo a historial de mantenimiento](media/12a3e484-1eb4-497f-8cab-8064bccc2ef5.png)
  
Se muestra una lista de todos los mensajes de estado de servicio registrado en el período de tiempo seleccionado, tal y como se muestra a continuación:
  
![Ver historial de mantenimiento de servicio](media/5ed20247-121c-4abe-9fe7-9025e26a2d0e.png)
  
Puede ver el historial de mantenimiento para los últimos 7 días o últimos 30 días. Seleccione cualquier fila para ver más detalles acerca del problema.
  
Para obtener más información acerca de nuestro compromiso de tiempo de actividad, vea [operations transparentes de Office 365](https://go.microsoft.com/fwlink/?linkid=848695).
  
## <a name="leave-feedback"></a>Votar

Nuestro objetivo es asegurarse de que la información que proporcionamos a usted sobre un problema de curso es oportuna, precisa y útil. Para Díganos cómo lo estamos haciendo, seleccione una clasificación por estrellas. Una vez que háganos una puntuación de 1 a 5 estrellas, puede proporcionar comentarios en cualquier detalles específicos. Vamos a utilizar los comentarios para ajustar con precisión nuestro sistema de mantenimiento de servicio.
  
![Formulario de comentarios para problemas de mantenimiento de servicio](media/fd083fdb-fde8-47b4-9136-b90d1d003864.png)
  
## <a name="see-also"></a>Vea también

[Informes de actividad en el centro de administración de Office 365](https://support.office.com/article/0d6dfb17-8582-4172-a9a9-aed798150263)

