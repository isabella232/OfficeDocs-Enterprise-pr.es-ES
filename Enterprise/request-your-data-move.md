---
title: Cómo solicitar el movimiento de datos
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/10/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 5bb64310-36fc-473d-b791-a0176f21707f
f1.keywords:
- NOCSH
description: Los clientes de Office 365 existentes deberán enviar una solicitud antes de la fecha límite de su país para que los datos del cliente de los servicios de Office 365 participantes se muevan a su nueva geografía.
ms.openlocfilehash: 506943ce802adbd8d443cfb69212834b9c552f61
ms.sourcegitcommit: e2f7bb4ccd4c74902235f680104ca6b56c051587
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2020
ms.locfileid: "42106231"
---
# <a name="how-to-request-your-data-move"></a>Cómo solicitar el movimiento de datos

> [!NOTE]
> La información de esta página solo se aplica a los clientes que tienen inquilinos de Office 365 existentes antes de los nuevos centros de datos en su área geográfica lanzada. 
  
Los clientes de Office 365 existentes pueden solicitar una migración temprana de los datos principales de los clientes de su organización en reposo.  
  
## <a name="when-can-i-request-a-move"></a>¿Cuándo puedo solicitar un movimiento?

|**Clientes con país de suscripción en**|**Inicio del período de la solicitud**|**Fecha límite de solicitud**|
|:-----|:-----|:-----|
|Japón  <br/> |1 de enero de 2020  <br/> |30 de junio de 2020  <br/> |
|Australia, Nueva Zelanda, Fiji  <br/> |1 de enero de 2020  <br/> |30 de junio de 2020  <br/> |
|India  <br/> |1 de enero de 2020  <br/> |30 de junio de 2020  <br/> |
|Canada  <br/> |1 de enero de 2020  <br/> |30 de junio de 2020  <br/> |
|Reino Unido  <br/> |1 de enero de 2020  <br/> |30 de junio de 2020  <br/> |
|Corea del Sur  <br/> |1 de enero de 2020  <br/> |30 de junio de 2020  <br/> |
|Francia  <br/> |1 de enero de 2020  <br/> |30 de junio de 2020  <br/> |
|Emiratos Árabes Unidos  <br/> |15 de julio de 2019  <br/> |30 de junio de 2020  <br/> |
|Sudáfrica  <br/> |25 de julio de 2019  <br/> |30 de junio de 2020  <br/> |
|Suiza, Liechtenstein  <br/> |10 de diciembre de 2019  <br/> |30 de junio de 2020  <br/> |
|Alemania  <br/> |Plane  <br/> |Plane  <br/> |
   
## <a name="how-to-request-a-move"></a>Cómo solicitar un movimiento

Los clientes elegibles verán una página en el [centro de administración de 365 de Microsoft](https://aka.ms/365admin), que les permitirá solicitar que sus datos principales de clientes se muevan a su nueva región de centro de datos.  
  
Para obtener acceso a la página en el centro de administración de Microsoft 365, en el panel de navegación de la izquierda, expanda **configuración**y, a continuación, haga clic en **configuración**.
Seleccione el **Perfil de organización**de la ficha y, a continuación, seleccione la **residencia de datos**de opción.
  
**Es posible que no vea esta sección si se aplica una de las siguientes opciones**:
- El inquilino no es apto para el programa de Office 365 Move.  La idoneidad la determina el país de suscripción del inquilino.
- Todos los datos principales de clientes en reposo ya se encuentran en la nueva área geográfica (consulte la sección Ubicación de datos de la página). 
  
Si su organización tiene requisitos de residencia de datos y necesita solicitar una migración temprana, haga clic en **participar** en la parte superior derecha de la sección. En el lado derecho de la pantalla aparecerá una nueva sección en la que se explican los detalles del programa de Office 365 Move. Seleccione el botón de alternancia junto al texto en el que **se indica que es necesario migrar los datos principales de clientes de la organización en reposo**. A continuación, haga clic en **Guardar**.
  
![Pantalla de opción de suscripción de Datacenter](media/dataresidencyflyoutae.jpg)
  
Debe ver el texto en la sección **residencia de datos** para indicar que **su organización ha solicitado mover sus datos principales de clientes.** También tendrá un mensaje de confirmación en el centro de mensajes. Esto confirma que ha solicitado un movimiento correctamente. 


  
## <a name="what-happens-after-requesting-a-move"></a>¿Qué sucede después de solicitar un movimiento?

Una vez solicitada la transferencia, le haremos avanzar tan pronto como nuestras restricciones operativas lo permitan. Debido a la naturaleza impredecible de muchas de las restricciones, no se puede compartir una fecha o un período de tiempo específicos para los movimientos. Verá una notificación cuando se haya completado el movimiento.
  
Los movimientos pueden tardar hasta 24 meses desde la fecha límite de la solicitud para que se complete el país.
  
## <a name="microsoft-teams"></a>Microsoft Teams

A partir del 2020 de enero, los clientes de los países de Office 365 elegibles pueden optar a la migración de los datos del servicio de chat de Microsoft Teams.  Las escalas de tiempo de participación se han reabierto o ampliado para todos los países elegibles para ofrecer a los clientes la oportunidad de considerar el programa de migración anticipada con Microsoft Teams en el ámbito.   

## <a name="optional-actions-before-you-request-a-move"></a>Acciones opcionales antes de solicitar un movimiento

Realice los siguientes pasos según corresponda.
  
### <a name="if-you-use-an-ip-based-firewall-add-allow-rules-for-the-new-ip-addresses"></a>Si usa un firewall basado en IP, agregue reglas de permiso para las nuevas direcciones IP

Se recomienda usar el filtrado DNS para los firewalls en lugar de las direcciones IP. No se requieren nuevas entradas DNS.
  
Si usa un firewall basado en IP para la conectividad a Internet, debe agregar reglas de permiso para las nuevas direcciones IP para el centro de recursos de destino geográficamente. Las direcciones IP de la nueva GEOS de centro de recursos además de los nuevos servidores se agregan de forma continua a los [intervalos de direcciones IP y URL de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=229631).
  
Consulte la documentación del firewall para obtener información sobre cómo agregar reglas de permiso (también conocidas como listas de blanca).
  
Después de agregar las direcciones IP, es posible que desee probar la conectividad con el nuevo centro de recursos geográfico. Para ello, se recomienda crear un nuevo inquilino de [prueba gratuita de 30 días](https://go.microsoft.com/fwlink/?LinkId=522463) tan pronto como el nuevo área geográfica del centro de información esté disponible. 
  
### <a name="test-using-a-new-tenant"></a>Realizar pruebas con un nuevo espacio empresarial

Si quiere probar la conectividad antes de mover, puede configurar un [nuevo inquilino gratuito de prueba de 30 días](https://go.microsoft.com/fwlink/?LinkId=522463) después de que el nuevo área geográfica del centro de información esté disponible y usarlo para obtener experiencia de Office 365 hospedada en el nuevo área geográfica del centro de recursos. 
  
El inquilino de prueba no se puede combinar con el espacio empresarial existente:
  
- Los usuarios deben usar una cuenta de prueba independiente para sus pruebas.
    
- No hay ninguna forma de mover datos entre los inquilinos.
    
### <a name="notify-users-to-update-out-of-date-exchange-settings-on-mobile-devices"></a>Notificar a los usuarios que actualicen la configuración de Exchange no actualizada en los dispositivos móviles

Si los usuarios tienen un dispositivo móvil con el servidor de Exchange configurado en **m.Outlook.com** o **podxxxxx.Outlook.com**, se recomienda cambiar a **Outlook.Office365.com**, siguiendo las instrucciones de [configurar un dispositivo móvil para sincronizar con la cuenta](https://support.office.com/article/c9139caf-01ab-41a0-827c-3c06ee569ed3).

## <a name="related-topics"></a>Temas relacionados

[Mover datos básicos a un nuevo Office 365 Datacenter GEOS](moving-data-to-new-datacenter-geos.md)

[Preguntas más frecuentes sobre el movimiento de datos](data-move-faq.md)

[Nueva GEOS de centro de recursos para Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Servicios de Azure por región](https://azure.microsoft.com/regions/)
  

