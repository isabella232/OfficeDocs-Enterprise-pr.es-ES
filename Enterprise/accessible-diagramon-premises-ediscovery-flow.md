---
title: "Diagrama accesible: Flujo de exhibición de documentos electrónicos local"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "Este artículo es una versión de texto accesible del diagrama Flujo de exhibición de documentos electrónicos local."
ms.openlocfilehash: de94fc2af94df47a83f4a7847a84cd18131f637e
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a>Diagrama accesible: Flujo de exhibición de documentos electrónicos local

**Resumen:** Este artículo es una versión de texto accesible del diagrama denominado local eDiscovery flujo.
  
En este póster se explica de manera detallada la arquitectura y el flujo de datos entre productos de servidor. 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a>En SharePoint, Exchange, Lync y recursos compartidos de archivos

El diagrama muestra un usuario que envíe una consulta que tiene acceso a dos conjuntos de servidores, un entorno de aplicación de SharePoint 2013 Enterprise y un conjunto de servicios de SharePoint de 2013. La granja de servidores de SharePoint 2013 Services se comunica con un conjunto de contenido de SharePoint 2013, 2013 de Exchange Server (que se comunica con Lync 2013) y archivos compartidos de Windows. 
  
La lista de flujo de exhibición de documentos electrónicos describe el flujo de datos y el orden en que las acciones de consulta de exhibición de documentos electrónicos se producen en SharePoint, Exchange, Lync y los recursos compartidos de archivos.  
  
Primero de describe detalladamente la lista de flujo de exhibición de documentos electrónicos y después se describen detalladamente las características representadas en el diagrama.  
  
### <a name="ediscovery-flow-list"></a>Lista de flujo de exhibición de documentos electrónicos

Los números de cada uno de los pasos descritos en esta lista corresponden a los pasos que se muestran en el diagrama. El diagrama se describe con mayor detalle más adelante en este documento  
  
1. casos de eDiscovery son creados, gestionados y utilizados en el centro de eDiscovery (EDC). La EDC es una colección de sitios de SharePoint de 2013. Esto es donde se definen los casos, se identifican los orígenes de seguimiento, se emiten consultas, se revisan los resultados de la consulta y suspensiones en el contenido se coloca o se quitan. 
    
2. La consulta de eDiscovery o acción, por ejemplo, colocar una suspensión, ReleaseHold o GetStatus, se retransmite desde la EDC para el proxy de aplicación de servicio de búsqueda (SSA) en el conjunto de servidores de empresa de la aplicación. El proxy de SSA, a continuación, retransmite el tráfico de lo SSA en el conjunto de servidores de servicios de la aplicación. En este ejemplo, la solicitud es colocar nada en el conjunto de contenido de SharePoint con "CONTOSO" en el nombre del archivo en espera. 
    
3. Si la solicitud consiste en consultar un caso, la SSA consulta el índice de búsqueda. Después, el conjunto de resultados de consulta de exhibición de documentos electrónicos se devuelve al usuario a través del EDC.  
    
4. Si la solicitud es una acción, como colocar una suspensión o ReleaseHold, dicha acción se escribe en el Actions_Table en la base de datos administrativa de SSA. En este ejemplo, se escribe una solicitud de suspensión para nada en el conjunto de contenido de SharePoint con "CONTOSO" en la Actions_Table. 
    
5. A intervalos regulares, se activa el trabajo del temporizador con la operación de conservación local de exhibición de documentos electrónicos en la granja de contenido, el cual genera una solicitud de acciones pendientes y envía actualizaciones de estado mediante el proxy de SSA a la SSA.  
    
6. La consulta de acciones pendientes se retransmite a la central SSA, que consulta el Action_Table de acciones para el conjunto de contenido pendientes. El trabajo del temporizador de suspensión en lugar de granja de servidores de contenido también envía actualizaciones de estado de los objetos y las acciones que ha recibido, que se escriben en el ActionsTable. 
    
7. El SSA envía la solicitud de suspensión de cualquier contenido con "CONTOSO" en el nombre del conjunto de servidores de contenido de SharePoint 2013 para el trabajo del temporizador de suspensión en lugar de eDiscovery en la granja de servidores de contenido. 
    
8. El eDiscovery lugar mantenga temporizador lugares de trabajo mantienen el "Sitio de CONTOSO" y "Contenido CONTOSO" en. 
    
9. El trabajo del temporizador de conservación local de exhibición de documentos electrónicos se ejecuta periódicamente en la granja de SharePoint Enterprise para comprobar el estado de las acciones de detección y actualizarlo.  
    
10. La consulta de estado se transmite a través del proxy de SSA de la granja de SharePoint Enterprise hacia la SSA de la granja SharePoint Services.  
    
11. La SSA recupera el estado de Action_Table y lo devuelve al trabajo del temporizador en la granja de SharePoint Enterprise, la cual inserta las actualizaciones de estado en el EDC.  
    
12. Cuando el usuario de eDiscovery está buscando (o realizar una acción) para los orígenes de Exchange, como un buzón o el contenido archivado de Lync, el SSA central utiliza proxy de Exchange Web Services (EWS) para consultar los servicios Web Exchange. Exchange tiene su propia infraestructura de eDiscovery y de búsqueda y administra todas las llamadas de eDiscovery internamente. 
    
13. Los EWS responden a la SSA con resultados de búsqueda de exhibición de documentos electrónicos o con una respuesta a una solicitud de estado para una conservación basada en una consulta que, a su vez, se transmite al EDC.  
    
#### <a name="prerequisites"></a>Requisitos previos

- El motor de búsqueda Enterprise Search  debe estar configurado, los rastreos de búsqueda en los orígenes de contenido (SharePoint y los recursos compartidos de archivos de Windows) deben realizarse correctamente y todos los orígenes de contenido deben encontrarse en el índice.  
    
- La autenticación y la confianza de servidor a servidor deben estar configuradas entre la granja de SharePoint Services y Exchange, y también entre Exchange y Lync.  
    
### <a name="description-of-components-in-the-diagram"></a>Descripción de los componentes del diagrama

El diagrama muestra un usuario que envíe una consulta que tiene acceso a dos conjuntos de servidores, un entorno de SharePoint 2013 empresarial de la aplicación y un conjunto de servicios de SharePoint de 2013. El conjunto de servidores de SharePoint Services interactúa con un conjunto de contenido de SharePoint 2013, 2013 de Exchange Server (las interfaces con Lync 2013) y archivos compartidos de Windows. 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a>El conjunto de servidores de SharePoint 2013 Enterprise App

El conjunto de servidores de SharePoint 2013 empresarial de la aplicación contiene los siguientes componentes: 
  
- EDC
    
- Proxy de SSA  
    
- Trabajo del temporizador 
    
Cuando el usuario envía una consulta o una acción, esta se envía al EDC de la granja de SharePoint Enterprise. Se producen estas acciones:  
  
- La acción o la consulta se envía al proxy de SSA.  
    
- El proxy de SSA envía una consulta de estado o una respuesta para el trabajo del temporizador de la granja de SharePoint Enterprise, y también envía una consulta de estado o una respuesta al servicio de SSA en la granja de SharePoint Services. Las acciones que se derivan de ello se describen en la sección sobre la granja de SharePoint Services.  
    
- Cuando recibe una respuesta, el trabajo del temporizador la envía al proxy de SSA y al EDC.  
    
- Los resultados de la consulta o la acción se envían al usuario desde el EDC.  
    
#### <a name="sharepoint-2013-services-farm"></a>Conjunto de servicios de SharePoint de 2013

La granja de servidores de SharePoint 2013 Services contiene los siguientes componentes: 
  
- Servicio de SSA  
    
- Base de datos del índice de búsqueda  
    
- Base de datos de admin_db de SSA. Contiene la tabla de acciones en esta base de datos: mantenga versión mantenga GetStatus 
    
- Proxy de EWS  
    
Cuando el proxy de SSA en la granja de SharePoint Enterprise envía una consulta de estado a la SSA en la granja de SharePoint Services, se producen estas acciones:  
  
- Si la solicitud es una consulta, la SSA consulta el índice de búsqueda. Se envía una respuesta de detección a la SSA y después al usuario a través del EDC.  
    
- Si la solicitud es una acción de escritura, el servicio de SSA envía la acción de escritura a admin_db de SSA.  
    
- Un rastreo y responder los resultados de la solicitud se envía desde el SSA para el conjunto de servidores de contenido de SharePoint 2013 y se devuelve una respuesta para el SSA. 
    
- Se envía una consulta de rastreo y de resultados de respuesta desde la SSA a los recursos de archivos compartidos de Windows, y se devuelve una respuesta a la SSA.  
    
- Se envía una consulta de acciones, respuestas o actualizaciones de estado pendientes desde la SSA al proxy de SSA en la granja de contenido de SharePoint y se devuelve una respuesta a la SSA.  
    
- Se envía una solicitud de acción/estado de Exchange desde la SSA al proxy de EWS, que envía una solicitud de acción/ estado de consulta de Exchange al servicio Web Exchange en el servidor Exchange 2013.   
    
- Se envía una consulta/respuesta de estado desde la SSA hacia admin_db de la SSA y se devuelve a la SSA.  
    
- Se envía una consulta/respuesta de acción pendiente desde la SSA hacia admin_db de la SSA y se devuelve a la SSA.  
    
#### <a name="sharepoint-2013-content-farm"></a>Conjunto de contenido de SharePoint de 2013

El conjunto de servidores de SharePoint 2013 contenido contiene los siguientes componentes: 
  
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
  
- Confianza/OAuth de servidor a servidor se controla entre el conjunto de contenido de SharePoint 2013 y 2013 de Exchange. 
    
- La confianza/OAuth de servidor a servidor se controla entre Exchange 2013 y Lync 2013.  
    
#### <a name="lync-2013"></a>Lync 2013

El componente Lync 2013 archiva contenido de Lync en Exchange 2013.  
  
#### <a name="windows-file-shares"></a>Recursos compartidos de archivos de Windows

El componente de recursos compartidos de archivos de Windows proporciona resultados de rastreo para la SSA en la granja de SharePoint Services.  
  
### <a name="legend"></a>Leyenda

La leyenda de este diagrama muestra de forma gráfica los distintos tipos de tráfico representados entre los componentes con líneas de colores distintos:  
  
- Línea azul claro: consulta/acción - datos de consulta o acción de eDiscovery 
    
- Línea naranja: respuesta de eDiscovery - datos de respuesta de consulta de eDiscovery 
    
- Línea verde: consultas y respuestas de estado - datos de consultas y respuestas de estado de eDiscovery 
    
- Púrpura línea: solicitud de acción o estado de Exchange - solicitud de eDiscovery para el estado de la acción para el tráfico de Exchange. 
    
- Línea roja: intercambiar respuesta datos/estado - respuesta de consulta o estado de eDiscovery desde Exchange. 
    
- Línea negra discontinua: OAuth/Confianza de servidor a servidor  
    
- Línea negra fija: Rastreo/resultados  
    

