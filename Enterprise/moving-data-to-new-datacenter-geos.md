---
title: Mover datos básicos a un nuevo Office 365 Datacenter GEOS
ms.author: deniseb
author: denisebmsft
manager: laurawi
ms.date: 07/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 0a35176a-e585-4dec-a90b-36be8314667f
description: 'El nuevo centro de GEOS agrega capacidad y calcula recursos para apoyar el crecimiento constante del uso y la demanda de los clientes. Además, el nuevo centro de datos GEOS ofrece una residencia de datos geográfica para los principales datos de clientes. Los datos principales de los clientes son un término que hace referencia a un subconjunto de los datos de clientes definidos en los términos de Microsoft Online Services: contenido del buzón de correo de Exchange Online (cuerpo del correo electrónico, entradas del calendario y contenido de los datos adjuntos del correo electrónico) y contenido del sitio de SharePoint Online y los archivos se almacenan en ese sitio y los archivos cargados en OneDrive para la empresa.'
ms.openlocfilehash: df52b50f6e291a80aeb7b8d783937d225bfb6e29
ms.sourcegitcommit: 842ac51577317dfc8d2adc46d09b4d735f29bc4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/25/2019
ms.locfileid: "35907643"
---
# <a name="moving-core-data-to-new-office-365-datacenter-geos"></a>Mover datos básicos a un nuevo Office 365 Datacenter GEOS

Seguimos abrimos New Datacenter GEOS for Office 365 for Business Services. Estos nuevos GEOS de centro de recursos agregan capacidad y computan recursos para admitir el crecimiento constante del uso y la demanda de los clientes. Además, el nuevo centro de datos GEOS ofrece una residencia de datos geográfica para los principales datos de clientes. 

Los datos de clientes principales son un término que hace referencia a un subconjunto de los datos de clientes definidos en los [términos de Microsoft Online Services](https://go.microsoft.com/fwlink/p/?LinkID=249048): 
- Contenido del buzón de correo de Exchange Online (cuerpo del correo electrónico, entradas del calendario y contenido de los datos adjuntos del correo electrónico)
- Contenido del sitio de SharePoint Online y los archivos almacenados en ese sitio
- Archivos cargados en OneDrive para la empresa 
  
Los clientes existentes que tienen sus datos de clientes principales almacenados en un centro de datos ya existente no se ven afectados por el inicio de una nueva geografía del centro de datos. No presentamos ninguna funcionalidad, características o certificaciones de cumplimiento únicos con el nuevo centro de recursos geográfico. Como cliente en cualquiera de estas dos GEOS, obtendrá los mismos controles de calidad de servicio, rendimiento y seguridad que antes. Ofrecemos a los clientes existentes que aparecen en la tabla que se muestra a continuación una opción para solicitar la migración temprana de los datos principales de clientes de la organización en el resto a su nuevo área geográfica del centro de datos.
  
|Clientes con dirección de facturación en * * * *|Geo de centro de recursos anterior * * * *|Nueva geo del centro de recursos * * * *|Geográfico disponible desde * * * *|
|:-----|:-----|:-----|:-----|
|Japón * * * *| Asia/Pacífico | Japón | Diciembre de 2014 |
|Australia, Nueva Zelanda, Fiji * * * *| Asia/Pacífico | Australia | Marzo de 2015 |
|India * * * *| Asia/Pacífico | India | Octubre de 2015 |
|Canadá * * * *| Norteamérica | Canadá | Mayo de 2016 |
|Reino Unido * * * *| Europa | Reino Unido | Septiembre de 2016 |
|Corea del sur * * * *| Asia/Pacífico | Corea del sur | Abril de 2017 |
|Francia * * * *| Europa | Francia | Marzo de 2018 |
|Emiratos Árabes Unidos * * * *| Europa | Emiratos Árabes Unidos | Junio de 2019 |
|Sudáfrica * * * *| Europa | Sudáfrica | 2019 de julio |
  
Los clientes nuevos o los inquilinos de Office 365 creados después de la disponibilidad del nuevo área geográfica del centro de datos tendrán automáticamente almacenados sus datos de clientes principales en el nuevo centro de datos.
  
Una lista completa de todos los GEOS de centro de datos, los centros de datos y la ubicación de los datos de clientes en reposo están disponibles como parte de los [mapas de centros](https://office.com/datamaps)de datos interactivos. 
  
## <a name="data-residency-option"></a>Opción de residencia de datos

Proporcionamos una opción de residencia de datos para los clientes de Office 365 existentes que están cubiertos por la GEOS del centro de datos que se enumeran en la tabla anterior. Con esta opción, los clientes con requisitos de residencia de datos pueden solicitar la migración temprana de los datos principales de los clientes de su organización en reposo a su nuevo área geográfica del centro de datos.  Microsoft ofrecerá una fecha límite asignada a todos los clientes elegibles que soliciten la migración temprana durante la ventana de inscripción.  Revise la página [Cómo solicitar el movimiento de datos](request-your-data-move.md) para obtener más información sobre la ventana de inscripción para la geografía y los pasos para inscribirse en el programa.  Los movimientos de datos pueden tardar hasta 24 meses después del período de solicitud para completarse.

No realizar ninguna acción da como resultado que Microsoft pueda mover los datos principales de clientes en reposo a su nuevo centro de datos geográfico en el transcurso del tiempo como parte de la administración y optimización del servicio.Los datos principales de los clientes solo pueden desplazarse a su nuevo área geográfica del centro de datos, no a cualquier otra geografía.Notificaremos a los administradores de inquilinos a través del centro de mensajes cuando se haya completado este movimiento de administración de servicios y actualice la ubicación de los datos en el centro de administración.
   
No presentamos ninguna funcionalidad, características o certificaciones de cumplimiento únicos con el nuevo centro de recursos geográfico.
    
La complejidad, la precisión y la escala a la que necesitamos realizar movimientos de datos dentro de un entorno operado globalmente y automatizado nos impedían compartir el contenido cuando se espera que se lleve a cabo un movimiento de datos para el inquilino o cualquier otro inquilino único. Los clientes recibirán una confirmación en el centro de mensajes por servicio colaborador cuando se haya completado el movimiento de datos. 
    
Los movimientos de datos son una operación del servicio back-end con un impacto mínimo en los usuarios finales. Las características que se pueden influir se enumeran en la página [durante y después de mover datos](during-and-after-your-data-move.md) . Adhiere al [contrato de nivel de servicio de Microsoft Online Services (SLA)](https://go.microsoft.com/fwlink/p/?LinkId=523897) por disponibilidad para que no haya nada que los clientes necesiten para preparar o para supervisar durante el movimiento. La notificación de todo el mantenimiento del servicio se realiza si es necesario. 

Los datos que se mueven a la nueva geo de centro de datos se completan sin costo adicional para el cliente.
    
## <a name="related-topics"></a>Temas relacionados 
 
[Cómo solicitar el movimiento de datos](request-your-data-move.md)
    
[Preguntas más frecuentes sobre el movimiento de datos](data-move-faq.md)
  
[Nueva GEOS de centro de recursos para Microsoft Dynamics CRM Online](https://go.microsoft.com/fwlink/p/?Linkid=615924)
  
[Servicios de Azure por región](https://azure.microsoft.com/en-us/regions/)
