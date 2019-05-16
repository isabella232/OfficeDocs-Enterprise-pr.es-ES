---
title: Preguntas más frecuentes sobre el movimiento de datos
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 09/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 1f01bc6f-5d37-4d14-bdd3-9d94a1e23e14
description: A continuación, se incluyen respuestas a preguntas generales sobre cómo mover datos principales a un nuevo centro de datos geográfico.
ms.openlocfilehash: 29706f49ee0faf8c535b50843f224b7b1b2a372e
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067906"
---
# <a name="data-move-general-faq"></a>Preguntas más frecuentes sobre el movimiento de datos

A continuación, se incluyen respuestas a preguntas generales sobre cómo mover datos principales a un nuevo centro de datos geográfico.
  
## <a name="what-customers-are-eligible-to-request-a-move"></a>¿Qué clientes pueden optar a solicitar un movimiento?
  
Los clientes de Office 365 Commercial existentes que seleccionaron un país apto para la nueva área geográfica del centro de recursos podrán solicitar un movimiento.  El programa solo existe para los inquilinos con un código de país elegible asignado al inquilino de Office 365 para migrar datos de cliente principales en reposo para cargas de trabajo elegibles en el área geográfica de Office 365 Datacenter correspondiente.  Consulte la página [Cómo solicitar el movimiento de datos](request-your-data-move.md) para confirmar la elegibilidad del país.   

## <a name="how-do-we-define-core-customer-data"></a>¿Cómo se definen los principales datos de clientes?
 
Los datos de clientes principales son un término que hace referencia a un subconjunto de los datos de clientes definidos en los [términos de Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkID=249048): 
- Contenido del buzón de correo de Exchange Online (cuerpo del correo electrónico, entradas del calendario y contenido de los datos adjuntos del correo electrónico)
- Contenido del sitio de SharePoint Online y los archivos almacenados en ese sitio
- Archivos cargados en OneDrive para la empresa 

## <a name="at-what-point-is-my-migration-complete-so-that-my-tenants-core-customer-data-is-being-stored-at-rest-in-my-new-geo"></a>¿En qué punto se ha completado mi migración para que los datos principales del cliente del inquilino se almacenen en reposo en mi nuevo área geográfica?

Debido a las dependencias compartidas entre Exchange Online y SharePoint Online/OneDrive para la empresa, cualquier migración no se puede considerar completa hasta que se migren ambos servicios.  Exchange Online y SharePoint Online/OneDrive para la empresa suelen migrar a horas independientes e independientemente entre ellos.  Los administradores de inquilinos reciben confirmación en el centro de mensajes cuando se completa cada migración de servicio y pueden ver la tarjeta de ubicación de datos en el centro de administración en cualquier momento para confirmar los datos principales del cliente en la ubicación de REST para cada servicio.

## <a name="will-my-tenant-automatically-be-moved-to-the-new-datacenter-geo"></a>¿Se moverá mi inquilino automáticamente a la nueva geo de centro de recursos?
 
Hay dos acciones que puede llevar a cabo como administrador de inquilinos.

- Suscripción.Inscríbase en el programa de migración de Office 365 y recibirá una fecha límite asignada para que los servicios migren los datos principales del cliente en reposo a la nueva área geográfica del centro de datos.Consulte la página [Cómo solicitar el movimiento de datos](request-your-data-move.md) para obtener instrucciones sobre cómo participar en el programa.
- No ejecutar ninguna acción.No emprender ninguna acción, lo que hace que Microsoft pueda mover los datos principales de clientes en reposo a su nuevo centro de datos geográfico en el transcurso del tiempo como parte de la administración y optimización del servicio.Los datos solo pueden moverse a su nuevo área geográfica del centro de datos, no a cualquier otra geografía.Se notifica a través del centro de mensajes cuando se ha completado este movimiento de administración del servicio.

## <a name="how-do-you-make-sure-my-customer-data-is-safe-during-the-move-and-that-i-wont-experience-downtime"></a>¿Cómo se asegura de que mis datos de clientes sean seguros durante el traslado y que no me informará de que se produzca un tiempo de inactividad?
  
Los movimientos de datos son una operación del servicio back-end con un impacto mínimo en los usuarios finales. Las características que se pueden influir se muestran en [durante y después de que se muevan los datos](during-and-after-your-data-move.md). Adhiere al [contrato de nivel de servicio de Microsoft Online Services (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) por disponibilidad para que no haya nada que los clientes necesiten para preparar o para supervisar durante el movimiento. 
  
Todos los servicios de Office 365 ejecutan las mismas versiones en los centros de recursos, por lo que puede garantizar la coherencia de la funcionalidad. El servicio es totalmente compatible durante todo el proceso.
  
## <a name="what-is-the-impact-of-having-different-services-located-in-different-geos"></a>¿Cuál es el impacto de tener diferentes servicios ubicados en diferentes GEOS?

Algunos de los servicios de Office 365 pueden estar ubicados en diferentes GEOS para los clientes existentes y para los clientes que se encuentran en la mitad del proceso de movimiento.  Nuestros servicios se ejecutan de forma independiente entre sí y, si es así, no se produce ningún impacto en la experiencia del usuario.Sin embargo, para fines de residencia de datos, no se puede considerar completar una migración de inquilino hasta que se migren Exchange Online y SharePoint Online/OneDrive para la empresa a la misma geografía del centro de datos.
  
## <a name="will-new-office-365-customers-be-automatically-provisioned-in-the-new-datacenter-geos"></a>¿Los nuevos clientes de Office 365 se aprovisionarán automáticamente en el nuevo centro de GEOS?
  
Sí. Una vez que haya una nueva geografía del centro de datos disponible, los clientes de Office 365 para empresas que seleccionan un país que cumplan los requisitos para la nueva geografía se almacenarán en el área geográfica del nuevo centro de datos.
  
 ## <a name="where-is-my-core-customer-data-is-located"></a>¿Dónde se encuentran los datos principales de los clientes?

Los administradores de espacios empresariales pueden ver la tarjeta de ubicación de datos en el centro de administración en cualquier momento para confirmar los datos principales del cliente en la ubicación de REST para cada servicio, específicamente para su inquilino.También publicamos la ubicación del centro de datos GEOS, los centros de datos y la ubicación de los datos de cliente de Office 365 en el centro de datos [ interactivo de office 365](https://office.com/datamaps) como referencia para los datos de cliente principales predeterminados en las ubicaciones de REST para los nuevos inquilinos.  Puede comprobar la ubicación de los datos de cliente en reposo a través de la sección Ubicación de datos del perfil de la organización en el centro de administración de Office 365.  
 
## <a name="when-will-i-be-able-to-request-a-move"></a>¿Cuándo podré solicitar un movimiento?
  
Consulte la página [Cómo solicitar el movimiento de datos](request-your-data-move.md) para obtener información sobre los intervalos de tiempo admitidos para su centro de datos geográfico.
  
## <a name="how-can-i-request-to-be-moved"></a>¿Cómo puedo solicitar que se mueva?
  
Los clientes elegibles verán una página en el [portal de administración de Office 365](https://portal.office.com/). Consulte [Cómo solicitar](request-your-data-move.md) un movimiento de datos para obtener instrucciones sobre cómo solicitar un movimiento. 
  
## <a name="can-i-change-my-selection-after-requesting-a-move"></a>¿Puedo cambiar mi selección después de solicitar un movimiento?
  
No es posible quitarlo del proceso después de enviar la solicitud.
  
## <a name="what-happens-if-i-do-not-request-a-move-before-the-deadline"></a>¿Qué sucede si no solicito un movimiento antes de la fecha límite?
  
 Es posible que podamos aceptar la solicitud en función de una excepción para conceder a su inquilino una fecha límite asignada para completar el traslado.  Póngase en contacto con el [soporte técnico de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459) para realizar la solicitud.  Recuerde que algunas cargas de trabajo se pueden mover a su nueva geo incluso sin una solicitud de participación si no se produce ninguna acción, Microsoft puede mover los datos principales de clientes en reposo a su nuevo centro de datos geográfico a lo largo del tiempo como parte de la administración y optimización del servicio.Los datos solo pueden moverse a su nuevo área geográfica del centro de datos, no a cualquier otra geografía.  Se notifica a través del centro de mensajes cuando se ha completado este movimiento de administración del servicio.
  
 ## <a name="what-if-i-want-to-move-my-data-in-order-to-get-better-network-performance"></a>¿Qué hago si quiero mover mis datos para obtener un mejor rendimiento de la red?
  
Estar cerca de un centro de información de Office 365 no es una garantía para mejorar el rendimiento de la red. Hay muchos factores y componentes que afectan al rendimiento de la red entre el usuario final y el servicio de Office 365. Para obtener más información acerca de este y ajustar el rendimiento, consulte [planificación de la red y ajuste del rendimiento para Office 365](network-planning-and-performance.md).
  
 ## <a name="do-all-the-services-move-their-data-on-the-same-day"></a>¿Todos los servicios mueven sus datos en el mismo día?
 
Cada servicio se mueve de forma independiente y es probable que mueva sus datos en diferentes momentos.
  
 ## <a name="can-i-choose-when-i-want-my-data-to-be-moved"></a>¿Puedo elegir cuándo quiero mover mis datos?
 
 Los clientes no pueden seleccionar una fecha específica, no pueden retrasar su movimiento y no podemos compartir una fecha o un período de tiempo específicos para los movimientos.
  
 ## <a name="can-you-share-when-my-data-will-be-be-moved"></a>¿Puede compartir cuando mis datos se van a mover?
  
Los movimientos de datos son una operación back-end con un impacto mínimo en los usuarios finales. La complejidad, la precisión y la escala a la que necesitamos realizar movimientos de datos dentro de un entorno operado globalmente y automatizado nos impedían compartir el contenido cuando se espera que se lleve a cabo un movimiento de datos para el inquilino o cualquier otro inquilino único. Los clientes recibirán una confirmación en el centro de mensajes por servicio colaborador cuando se haya completado el movimiento de datos. 
  
 ## <a name="what-happens-if-users-access-services-while-the-data-is-being-moved"></a>¿Qué sucede si los usuarios obtienen acceso a los servicios mientras se mueven los datos?

Vea [durante y después de la transferencia de datos](during-and-after-your-data-move.md) para obtener una lista completa de las características que pueden ser limitadas durante el movimiento de datos para cada servicio. 
  
 ## <a name="how-do-i-know-the-move-is-complete"></a>¿Cómo sé que se ha completado el traslado?
  
Vea el centro de mensajes de Office 365 para confirmar que se ha completado el movimiento de los datos de cada servicio. Cuando se mueven los datos de cada servicio, publicaremos un aviso de finalización para que reciba tres avisos de finalización: uno para cada uno de ellos para Exchange Online, SharePoint Online y Skype empresarial online.  También puede comprobar la ubicación de los datos de cliente en reposo mediante la sección Ubicación de datos del perfil de la organización en el centro de administración de Office 365.  
  
## <a name="i-am-an-office-365-customer-in-one-of-the-new-datacenter-geos-but-when-i-signed-up-i-selected-a-different-country-how-can-i-be-moved-to-the-new-datacenter-geo"></a>Soy un cliente de Office 365 en una de las nuevas GEOS de centro de recursos, pero cuando me he registrado, seleccioné un país diferente. ¿Cómo se puede mover a la nueva geografía del centro de recursos?

No se puede cambiar el país de suscripción asociado a su espacio empresarial. En su lugar, debe crear un nuevo inquilino de Office 365 con una nueva suscripción y mover manualmente los usuarios y los datos al nuevo inquilino.
  
## <a name="what-happens-if-we-are-in-process-of-email-data-migration-to-office-365-during-the-exchange-online-move"></a>¿Qué sucede si estamos en proceso de migración de datos de correo electrónico a Office 365 durante el movimiento de Exchange Online?

Este es un escenario muy común y es totalmente compatible.  La migración en la nube entre el centro de administración de GEOS no interfiere con ninguna migración en premisis a buzones de correo en la nube.
  
 ## <a name="can-i-pilot-some-users"></a>¿Puedo realizar un ensayo piloto de algunos usuarios?
  
Puede crear un inquilino de prueba independiente para probar la conectividad, pero el inquilino de prueba no se puede combinar de ninguna manera con el inquilino existente.

## <a name="i-dont-want-to-wait-for-microsoft-to-move-my-data-can-i-just-create-a-new-tenant-and-move-myself"></a>No quiero esperar a que Microsoft mueva mis datos. ¿Puedo crear un nuevo inquilino y desplazarme yo mismo?
  
Sí, pero el proceso no será tan transparente como si Microsoft tuviera que realizar el movimiento de datos.
  
Si crea un nuevo inquilino después de que el nuevo área geográfica disponible, el nuevo inquilino se hospedará en la nueva geo. Este nuevo espacio empresarial es completamente independiente del inquilino anterior y es responsable de mover todos los buzones de usuario, el contenido del sitio, los nombres de dominio y otros datos. Tenga en cuenta que no se puede mover el nombre del espacio empresarial de un inquilino a otro. Le recomendamos que espere al programa de movimiento proporcionado por Microsoft, ya que se ocupará de mover la configuración, los datos y las suscripciones de los usuarios.
  
 ## <a name="im-not-ready-to-be-moved-can-i-pick-a-specific-move-date"></a>No estoy listo para mover, ¿puedo elegir una fecha de movimiento específica?
  
No, no es posible cambiar Cuándo se moverán los datos principales de los clientes de cada servicio.
  
 ## <a name="my-customer-data-has-already-been-moved-to-a-new-datacenter-geo-can-i-move-back"></a>Los datos de mis clientes ya se han movido a un nuevo centro de datos geográficamente. ¿Puedo desplazarse hacia atrás?
 
No, no es posible. Los clientes que se movieron a nuevos centros de usuarios geográficamente no se pueden volver a mover. Como cliente en cualquier geográfico, tendrá la misma calidad de los controles de servicio, rendimiento y seguridad que antes.  [Office 365 multigeográfico](https://aka.ms/multi-geo) está disponible para algunos clientes como un complemento y permite que un solo inquilino cree varios GEOS de satélite y mueva los datos de usuario a esos GEOS con compromisos de residencia de datos.
  
 ## <a name="do-the-new-datacenter-geos-use-the-same-versions-of-office-365-services-as-the-current-datacenter-geos"></a>¿El nuevo centro de GEOS usa las mismas versiones de los servicios de Office 365 como el centro de GEOS de centros de recursos actual?

Sí.
  
## <a name="will-office-365-tenants-hosted-in-the-new-datacenters-be-available-to-users-outside-of-the-country"></a>¿Los inquilinos de Office 365 hospedados en los nuevos centros de recursos estarán disponibles para los usuarios fuera del país?
  
R. Sí. Microsoft mantiene una red global de gran tamaño con conexiones a Internet públicas en más de 130 ubicaciones en 35 países de todo el mundo con acuerdos de emparejamiento con más de 2.700 proveedores de servicios de Internet (ISP). Los usuarios podrán tener acceso a los centros de recursos desde cualquier lugar en Internet.

## <a name="my-tenant-is-configured-for-office-365-multi-geohttpsakamsmulti-geo--can-i-still-enroll-in-my-tenant-in-the-office-365-move-program-to-change-my-default-geo-and-move-any-user-not-in-a-satellite-region-to-the-new-default-geo"></a>Mi espacio empresarial está configurado para [Office 365 multigeográfico](https://aka.ms/multi-geo).  ¿Puedo inscribirse en mi inquilino en el programa de Office 365 mover para cambiar mi área geográfica predeterminada y mover a un usuario que no está en una región de satélite al nuevo área geográfica predeterminada?

Sí, el espacio empresarial es apto para inscribirse.  Se moverán todos los buzones EXO de su área geográfica predeterminada actual a la nueva geo del centro de recursos local.  No se moverán los buzones EXO configurados en regiones multilingües multilingües para seguir respetando la residencia de datos de la región satélite como se ha previsto.  SharePoint Online y OneDrive para la empresa no pueden migrar al nuevo centro de proceso de correo geográfico como parte del programa mover, aunque puede configurar los recursos compartidos de OneDrive para la empresa para que se muevan a cualquier región que quiera mediante el programa multigeográfico.
  
## <a name="related-topics"></a>Temas relacionados

[Mover datos básicos a un nuevo Office 365 Datacenter GEOS](moving-data-to-new-datacenter-geos.md)

[Cómo solicitar el movimiento de datos](request-your-data-move.md)

[Office 365 multigeográfico](https://aka.ms/multi-geo)

[Mapa de centros de recursos interactivos de Office 365](https://office.com/datamaps)

[Soporte técnico de Office 365](https://go.microsoft.com/fwlink/p/?LinkID=522459)

[Nueva GEOS de centro de recursos para Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Servicios de Azure por región](https://azure.microsoft.com/en-us/regions/)
