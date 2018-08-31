---
title: Preguntas más frecuentes sobre el movimiento de datos
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 9/14/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: Aquí encontrará respuestas a preguntas generales sobre cómo mover datos principales a un nuevo ubican de centro de datos.
ms.openlocfilehash: 40f83ee94aaa7c919f08d91d888ff131da02df67
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542868"
---
# <a name="data-move-general-faq"></a>Preguntas más frecuentes sobre el movimiento de datos

Aquí encontrará respuestas a preguntas generales sobre cómo mover datos principales a un nuevo ubican de centro de datos.
  
 **Pregunta: ¿cómo se puede hacer que mis datos de cliente están seguro durante el traslado y que no tengo tiempo de inactividad?**
  
Movimientos de datos r. son una operación de servicio back-end con una repercusión mínima para los usuarios finales. Se enumeran las características que pueden verse afectadas en [durante y después de la migración de datos](during-and-after-your-data-move.md). Se cumplir el [Microsoft Online Services nivel contrato servicio (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) para disponibilidad por lo que no hay nada que necesitan los clientes para preparar o para supervisar durante el traslado. 
  
Todos los servicios de Office 365 ejecutan las mismas versiones en los centros de datos, por lo que puede estar seguro de funcionalidad coherente. El servicio es totalmente compatible en todo el proceso.
  
 **P. ¿Cuál es el impacto de contar con los distintos servicios que se encuentra en diferentes zonas?**
  
R. para algunos clientes existentes y clientes en medio del proceso de movimiento, algunos de los servicios de Office 365 pueden encontrarse en distintas zonas. Nuestros servicios se ejecutan independientemente entre sí y no tiene ningún impacto de usuario si éste es el caso.
  
 **P. ¿nuevos clientes de Office 365 se aprovisionan automáticamente en las zonas de centro de datos nueva?**
  
R. Sí. Una vez que un nuevo ubican de centro de datos está disponible, nuevo Office 365 para clientes empresariales que seleccione un país apto para la nueva ubican como su país durante la suscripción tendrá sus datos principales hospedados en el nuevo ubican de centro de datos.
  
 **P. ¿dónde están mis datos se encuentra?**
  
Se publicar la ubicación de zonas del centro de datos, centros de datos y la ubicación de los datos de cliente en el [Centro de datos interactiva de Office 365 se asigna ](https://o365datacentermap.azurewebsites.net). A partir del 1 de agosto, podrá comprobar la ubicación de los datos de clientes en reposo a través de la sección ubicación de datos en su perfil de organización en el centro de administración de Office 365.
  
 **P. ¿los clientes existentes de Office 365 se moverán a la nueva zonas de centro de datos?**
  
Los clientes A. optan Office 365 pueden solicitar que sus datos principales que se mueve a la nueva zonas. Los clientes necesitarán enviar una solicitud antes de la fecha límite para su geo para poder participar. 
  
 **P. ¿qué clientes son aptos para solicitar un movimiento?**
  
A. existente Office 365 clientes comerciales que seleccionó un país apto para la nueva ubican datacenter podrán solicitar un movimiento. 
  
 **P. ¿cuándo podrá solicitar un movimiento?**
  
R. el período de solicitud se anunciará en la página [cómo solicitar el movimiento de datos](request-your-data-move.md) . 
  
 **Pregunta: ¿Cómo puedo solicitar va a mover?**
  
R. los clientes cualificados verá una página en su [Portal de administración de Office 365](https://portal.office.com/). Para obtener instrucciones acerca de cómo solicitar un movimiento, consulte [cómo solicitar el movimiento de datos](request-your-data-move.md) . 
  
 **P. ¿puedo cambiar mi selección después de solicitar un movimiento?**
  
R. no es posible que nos quitar el proceso después de enviar la solicitud.
  
 **P. ¿Qué sucede si no solicitar un movimiento antes de la fecha límite?**
  
R. estamos no pueda aceptar solicitudes va a mover después de la fecha límite en cada ubican.
  
 **P. ¿Qué ocurre si deseo mover Mis datos con el fin de obtener un mejor rendimiento de la red?**
  
No es una garantía para un mejor rendimiento de red que se va a cerca de un centro de datos de Office 365. Existen muchos factores y componentes que afectan al rendimiento de la red entre el usuario final y el servicio de Office 365. Para obtener más información sobre este y ajuste del rendimiento, vea [Diseño de la red y ajuste del rendimiento de Office 365](network-planning-and-performance.md).
  
 **P. ¿todos los servicios de mover sus datos en el mismo día?**
  
R. los servicios no mueven los datos al mismo tiempo. Cada servicio se moverá de forma independiente y es probable que moverá los datos en momentos diferentes.
  
 **P. ¿puedo elegir cuando deseo que mis datos va a mover?**
  
R. los clientes no pueden seleccionar una fecha específica, no se puede retrasar la su traspaso, y no podemos compartir una fecha específica o período de tiempo para que los movimientos.
  
 **P. ¿pueden compartir cuando los datos se se moverán?**
  
Movimientos de datos r. son una operación de back-end con una repercusión mínima para los usuarios finales. La complejidad, precisión y una escala a la que necesitamos para llevar a cabo los movimientos de datos dentro de un entorno globalmente mando y automatizado prohíben nos uso compartido cuando se espera un movimiento de datos para llevar a cabo para el inquilino o cualquier otro inquilino único. Los clientes recibirán una confirmación en el centro de mensajes por servicio colaborador cuando haya finalizado el movimiento de datos. 
  
 **P. ¿Qué ocurre si los usuarios tener acceso a servicios mientras se va a mover los datos?**
  
R. vea [durante y después de la migración de datos](during-and-after-your-data-move.md) para obtener una lista completa de las características que podría estar limitada durante partes del movimiento de datos para cada servicio. 
  
 **Pregunta: ¿Cómo sé que el movimiento es completado?**
  
R. vea el centro de mensajes de Office 365 para confirmación de que ha finalizado el movimiento de datos de cada servicio. Cuando se mueven los datos de cada servicio, publicaremos un aviso de finalización, por lo que se obtienen tres avisos de finalización: uno para Exchange Online, SharePoint Online y Skype para profesionales en línea.
  
Si ve los problemas tras el traslado, póngase en contacto con el [Soporte técnico de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) para obtener asistencia. 
  
 **P. ¿qué datos para Office 365 se almacenan en el nuevo zonas de centro de datos?**
  
R. Si un disposiciones cliente su inquilino de una de las zonas de centro de datos nueva, Microsoft almacena los siguientes datos del cliente en reposo dentro de la geo:
  
- Contenido del buzón Exchange Online (cuerpo del correo electrónico, las entradas de calendario y el contenido de los datos adjuntos de correo electrónico)
    
- Contenido del sitio de SharePoint Online y los archivos almacenados dentro de ese sitio, incluido el contenido de Project Online y acceso en línea.
    
Además, estos datos no se replican fuera de la ubican.
  
 **P. estoy un cliente de Office 365 en una de las nuevas zonas de centro de datos, pero cuando suscribió, selecciona un país distinto. ¿Cómo puedo pueden moverse a la nueva ubican de centro de datos?**
  
R. Desafortunadamente, no es posible cambiar el país asociado con el inquilino. En su lugar, debe crear a un nuevo inquilino de Office 365 con una nueva suscripción y mover manualmente los usuarios y los datos en el inquilino de nuevo.
  
 **P. ¿habrá cambios en mi factura?**
  
R. en la mayoría de los casos, no hay ningún cambio en la que los clientes en verán en su extracto de facturación.
  
Microsoft cargará a todos los clientes australianos de Office 365 una cantidad adicional igual a la australiana GST para servicios de Office 365 y emitirá facturas de impuestos. Se producirá este cambio porque GST de Australia de sujetos entregas de bienes y servicios proporcionados y ofrecidas en Australia.
  
 **P. ¿Qué ocurre si estamos en proceso de migración de datos de correo electrónico a Office 365 durante el traslado de Exchange Online?**
  
R. Si las migraciones de correo electrónico están en curso, se cancelará cualquier buzones individuales que se van a migrar actualmente mientras finaliza el inquilino de movimiento y migración de los buzones de correo se reiniciará automáticamente una vez que se encuentra el inquilino en los centros de datos de destino.
  
 **¿P. después de que los datos se mueven fuera de la anterior ubican del centro de datos, se lo quita de esos centros de datos?**
  
R. Sí, los datos anteriores se purgarán después de un período de tiempo.
  
 **P. ¿puedo realizar pruebas piloto de algunos usuarios?**
  
R. cuando el inquilino de Office 365 se mueve a un nuevo ubican de centro de datos, todos los usuarios se mueven a la vez. Puede crear un inquilino de prueba independiente para probar la conectividad, pero no se puede combinar el inquilino de prueba en modo alguno con el inquilino de existente.
  
 **P. ¿cómo recibirá una notificación sobre el movimiento y el usuario en mi compañía recibirá una notificación?**
  
R. utilizaremos el centro de mensajes de Office 365, que es visible para los usuarios que tengan los permisos de administrador en Office 365.
  
 **P. ¿no es necesario esperar a que Microsoft mover los datos. ¿Puedo simplemente crear a un nuevo inquilino y mover yo mismo?**
  
R. Sí, sin embargo, el proceso no será tan transparente como si fuera de Microsoft realizar el movimiento de datos.
  
Si crea a un nuevo inquilino después de la nueva ubican de centro de datos está disponible, se hospedará el inquilino nuevo en el nuevo ubican. Este nuevo inquilino es completamente independiente de su inquilino anterior y es responsable de mover todos los buzones de usuario, contenido del sitio, nombres de dominio y otros datos. Tenga en cuenta que no se puede mover el nombre del inquilino de inquilino de uno a otro. Se recomienda que espere a que el programa de movimiento proporcionado por Microsoft, tal y como se aquí se ocupe de mover todas las configuraciones, datos y suscripciones para los usuarios.
  
 **P. no estoy listo para moverse, ¿puedo escoger una fecha de movimiento específico?**
  
R. no es posible cambiar cuando se moverán los datos de cliente de cada servicio. Movimientos de datos son una operación de back-end con una repercusión mínima para los usuarios finales.
  
 **P. Mis datos cliente ya se ha movido a una nueva ubican de centro de datos. ¿Puedo mover vuelta?**
  
R. Esto no es posible. No se puede retroceder los clientes que se han movido al nuevo ubican los centros de datos. Como un cliente en cualquier ubican, experimentará la misma calidad de servicio, el rendimiento y controles de seguridad tal como hizo antes.
  
 **P. ¿la nueva zonas de centro de datos use las mismas versiones de servicios de Office 365 como las zonas de centro de datos actual?**
  
R. Sí.
  
 **¿Los inquilinos de va a Office 365 p. hospedados en los centros de datos nuevo esté disponible para los usuarios fuera del país?**
  
R. Sí. Microsoft mantiene una red global de gran tamaño con conexiones a Internet públicas en más de 50 ubicaciones en 23 países todo el mundo con acuerdos de interconexión con más de 1.500 proveedores de servicios de Internet (ISP). Los usuarios podrán tener acceso a los centros de datos desde cualquier lugar y en Internet.
  

