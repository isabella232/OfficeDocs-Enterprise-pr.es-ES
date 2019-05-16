---
title: 'Diagrama accesible: Flujo de exhibición de documentos electrónicos local'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: Este artículo es una versión de texto accesible del diagrama Flujo de exhibición de documentos electrónicos local.
ms.openlocfilehash: bdaf46c552b346d0e6966cd3589f239146ddadc5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068536"
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Diagrama accesible: Flujo de exhibición de documentos electrónicos local

**Resumen:** Este artículo es una versión de texto accesible del diagrama denominada flujo de exhibición de documentos electrónicos local.
  
En este póster se explica de manera detallada la arquitectura y el flujo de datos entre productos de servidor. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>En SharePoint, Exchange, Lync y recursos compartidos de archivos

El diagrama muestra un usuario que envía una consulta que tiene acceso a dos granjas de servidores, una granja de aplicaciones de SharePoint 2013 Enterprise y una granja de servicios de SharePoint 2013. La granja de servicios de SharePoint 2013 se comunica con una granja de contenido de SharePoint 2013, Exchange Server 2013 (que se comunica con Lync 2013) y recursos compartidos de archivos de Windows. 
  
La lista de flujo de exhibición de documentos electrónicos describe el flujo de datos y el orden en que las acciones de consulta de exhibición de documentos electrónicos se producen en SharePoint, Exchange, Lync y los recursos compartidos de archivos.  
  
Primero de describe detalladamente la lista de flujo de exhibición de documentos electrónicos y después se describen detalladamente las características representadas en el diagrama.  
  
### <a name="ediscovery-flow-list"></a>Lista de flujo de exhibición de documentos electrónicos

Los números de cada uno de los pasos descritos en esta lista corresponden a los pasos que se muestran en el diagrama. El diagrama se describe con mayor detalle más adelante en este documento  
  
1. Los casos de exhibición de documentos electrónicos se crean, gestionan y usan en el centro de exhibición de documentos electrónicos (EDC). EDC es una colección de sitios de SharePoint 2013. Aquí es donde se definen los casos, se identifican los orígenes que se deben seguir, se emiten las consultas, se revisan los resultados de las consultas y se establecen o eliminan las operaciones de conservación de contenido. 
    
2. La consulta o la acción de exhibición de documentos electrónicos, como las operaciones Hold, ReleaseHold o GetStatus, se transmiten desde el EDC al proxy de la aplicación de servicio de búsqueda (SSA) en la granja de SharePoint Enterprise. Después, el proxy de SSA transmite el tráfico a la SSA en la granja de SharePoint Services. En este ejemplo, la solicitud es ubicar cualquier cosa en la granja de contenido de SharePoint con "CONTOSO" en el nombre de archivo en retención. 
    
3. Si la solicitud consiste en consultar un caso, la SSA consulta el índice de búsqueda. Después, el conjunto de resultados de consulta de exhibición de documentos electrónicos se devuelve al usuario a través del EDC.  
    
4. Si la solicitud es una acción, como ejecutar una operación Hold o ReleaseHold, esa acción se escribe en la tabla Actions_Table en la base de datos administrativa de la SSA. En este ejemplo, se escribe una solicitud de retención para cualquier cosa de la granja de contenido de SharePoint con "CONTOSO" en Actions_Table. 
    
5. A intervalos regulares, se activa el trabajo del temporizador con la operación de conservación local de exhibición de documentos electrónicos en la granja de contenido, el cual genera una solicitud de acciones pendientes y envía actualizaciones de estado mediante el proxy de SSA a la SSA. 
    
6. La consulta de acciones pendientes se transmite a la SSA central, que a su vez consulta en Actions_Table si hay alguna acción pendiente para la granja de contenido. El trabajo del temporizador de conservación local en la granja de contenido también envía actualizaciones de estado para objetos y acciones que ha recibido, y estas se escriben en Action_Table. 
    
7. El SSA envía la solicitud de retención para cualquier contenido con "CONTOSO" en el nombre de la granja de contenido de SharePoint 2013 al trabajo del temporizador de conservación local de eDiscovery en la granja de servidores de contenido. 
    
8. El trabajo del temporizador de conservación local de eDiscovery coloca el "sitio de CONTOSO" y el "contenido de CONTOSO" en espera. 
    
9. El trabajo del temporizador de conservación local de exhibición de documentos electrónicos se ejecuta periódicamente en la granja de SharePoint Enterprise para comprobar el estado de las acciones de detección y actualizarlo.  
    
10. La consulta de estado se transmite a través del proxy de SSA de la granja de SharePoint Enterprise hacia la SSA de la granja SharePoint Services.  
    
11. La SSA recupera el estado de Action_Table y lo devuelve al trabajo del temporizador en la granja de SharePoint Enterprise, la cual inserta las actualizaciones de estado en el EDC. 
    
12. Cuando el usuario de exhibición de documentos electrónicos realiza una búsqueda (o ejecuta una acción) en los orígenes de Exchange, como buscar un buzón de correo o contenido de Lync archivado, la SSA central usa el proxy de los servicios Web Exchange (EWS) para consultar los EWS. Exchange tiene su propia infraestructura de búsqueda y exhibición de documentos electrónicos, y gestiona internamente todas las llamadas a exhibición de documentos electrónicos. 
    
13. Los EWS responden a la SSA con resultados de búsqueda de exhibición de documentos electrónicos o con una respuesta a una solicitud de estado para una conservación basada en una consulta que, a su vez, se transmite al EDC.  
    
#### <a name="prerequisites"></a>Requisitos previos

- El motor de búsqueda Enterprise Search  debe estar configurado, los rastreos de búsqueda en los orígenes de contenido (SharePoint y los recursos compartidos de archivos de Windows) deben realizarse correctamente y todos los orígenes de contenido deben encontrarse en el índice.  
    
- La autenticación y la confianza de servidor a servidor deben estar configuradas entre la granja de SharePoint Services y Exchange, y también entre Exchange y Lync.  
    
### <a name="description-of-components-in-the-diagram"></a>Descripción de los componentes del diagrama

El diagrama muestra un usuario que envía una consulta, que tiene acceso a dos granjas de servidores, una granja de aplicaciones de SharePoint 2013 Enterprise y una granja de servicios de SharePoint 2013. La granja de SharePoint Services interactúa con una granja de contenido de SharePoint 2013, Exchange Server 2013 (que interactúa con Lync 2013) y recursos compartidos de archivos de Windows. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>Granja de servidores de aplicaciones empresariales de SharePoint 2013

La granja de aplicaciones de SharePoint 2013 Enterprise contiene los siguientes componentes: 
  
- EDC
    
- Proxy de SSA  
    
- Trabajo del temporizador 
    
Cuando el usuario envía una consulta o una acción, esta se envía al EDC de la granja de SharePoint Enterprise. Se producen estas acciones:  
  
- La acción o la consulta se envía al proxy de SSA.  
    
- El proxy de SSA envía una consulta de estado o una respuesta para el trabajo del temporizador de la granja de SharePoint Enterprise, y también envía una consulta de estado o una respuesta al servicio de SSA en la granja de SharePoint Services. Las acciones que se derivan de ello se describen en la sección sobre la granja de SharePoint Services.  
    
- Cuando recibe una respuesta, el trabajo del temporizador la envía al proxy de SSA y al EDC.  
    
- Los resultados de la consulta o la acción se envían al usuario desde el EDC.  
    
#### <a name="sharepoint-2013-services-farm"></a>Granja de servicios de SharePoint 2013

La granja de servicios de SharePoint 2013 contiene los siguientes componentes: 
  
- Servicio de SSA  
    
- Base de datos del índice de búsqueda 
    
- Base de datos de admin_db de SSA. La tabla de acciones de esta base de datos contiene: retener retenciones de suspensión 
    
- Proxy de EWS  
    
Cuando el proxy de SSA en la granja de SharePoint Enterprise envía una consulta de estado a la SSA en la granja de SharePoint Services, se producen estas acciones:  
  
- Si la solicitud es una consulta, la SSA consulta el índice de búsqueda. Se envía una respuesta de detección a la SSA y después al usuario a través del EDC.  
    
- Si la solicitud es una acción de escritura, el servicio de SSA envía la acción de escritura a admin_db de SSA.  
    
- Se envía una solicitud de resultados de rastreo y respuesta desde el SSA a la granja de servidores de contenido de SharePoint 2013 y se devuelve una respuesta a la SSA. 
    
- Se envía una consulta de rastreo y de resultados de respuesta desde la SSA a los recursos de archivos compartidos de Windows, y se devuelve una respuesta a la SSA.  
    
- Se envía una consulta de acciones, respuestas o actualizaciones de estado pendientes desde la SSA al proxy de SSA en la granja de contenido de SharePoint y se devuelve una respuesta a la SSA.  
    
- Se envía una solicitud de acción/estado de Exchange desde la SSA al proxy de EWS, que envía una solicitud de acción/ estado de consulta de Exchange al servicio Web Exchange en el servidor Exchange 2013.   
    
- Se envía una consulta/respuesta de estado desde la SSA hacia admin_db de la SSA y se devuelve a la SSA.  
    
- Se envía una consulta/respuesta de acción pendiente desde la SSA hacia admin_db de la SSA y se devuelve a la SSA.  
    
#### <a name="sharepoint-2013-content-farm"></a>Granja de contenido de SharePoint 2013

La granja de contenido de SharePoint 2013 contiene los siguientes componentes: 
  
- Proxy de SSA  
    
- Trabajo del temporizador 
    
- Sitio de SharePoint de Contoso  
    
- Contenido de SharePoint de Contoso  
    
Cuando la SSA en la granja de SharePoint Services envía una consulta de estado al proxy de SSA en la granja de contenido de SharePoint, se producen estas acciones:  
  
- El proxy de SSA en la granja de contenido de SharePoint envía una consulta de respuesta de estado/acciones pendientes al trabajo del temporizador.  
    
- El trabajo del temporizador envía una solicitud al sitio de SharePoint de Contoso, que revisa el contenido de SharePoint de Contoso.  
    
- La respuesta a la consulta de estado/acciones pendientes se envía desde el trabajo del temporizador hacia el proxy de SSA en la granja de contenido de SharePoint y, después, se envía al servicio de SSA en la granja de SharePoint Services.  
    
#### <a name="exchange-2013"></a>Exchange 2013

El componente de servidor de Exchange 2013 contiene el servicio Web Exchange y proporciona lo siguiente:  
  
- La confianza/OAuth de servidor a servidor se controla entre la granja de servidores de contenido de SharePoint 2013 y la de Exchange 2013. 
    
- La confianza/OAuth de servidor a servidor se controla entre Exchange 2013 y Lync 2013.  
    
#### <a name="lync-2013"></a>Lync 2013

El componente Lync 2013 archiva contenido de Lync en Exchange 2013.  
  
#### <a name="windows-file-shares"></a>Recursos compartidos de archivos de Windows

El componente de recursos compartidos de archivos de Windows proporciona resultados de rastreo para la SSA en la granja de SharePoint Services.  
  
### <a name="legend"></a>Legend

La leyenda de este diagrama muestra de forma gráfica los distintos tipos de tráfico representados entre los componentes con líneas de colores distintos:  
  
- Línea azul claro: consulta/acción-datos de la consulta o de la acción de eDiscovery 
    
- Línea naranja: datos de respuesta de consulta de las-eDiscovery Query Response 
    
- Línea verde: estado de consulta/respuesta-estado de exhibición de documentos electrónicos datos de consulta/respuesta 
    
- Línea púrpura: solicitud de acción/estado de Exchange-solicitud de exhibición de documentos electrónicos para el estado de acción del tráfico de Exchange. 
    
- Línea roja: respuesta de estado/datos de Exchange-respuesta de consulta o estado de exhibición de documentos electrónicos de Exchange. 
    
- Línea negra discontinua: OAuth/Confianza de servidor a servidor  
    
- Línea negra fija: Rastreo/resultados  
    

