---
title: "Diagrama accesible: Flujo de exhibición de documentos electrónicos local"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b9dcd692-0485-4eec-870d-87ab6b89d97b
description: "Este artículo es una versión de texto accesible del diagrama Flujo de exhibición de documentos electrónicos local."
ms.openlocfilehash: e137a75fb80c9198a332144d82fe405c6884aa52
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="fd530-103">Diagrama accesible: Flujo de exhibición de documentos electrónicos local</span><span class="sxs-lookup"><span data-stu-id="fd530-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="fd530-104">**Resumen:** Este artículo es una versión de texto accesible del diagrama denominado local eDiscovery flujo.</span><span class="sxs-lookup"><span data-stu-id="fd530-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="fd530-105">En este póster se explica de manera detallada la arquitectura y el flujo de datos entre productos de servidor.</span><span class="sxs-lookup"><span data-stu-id="fd530-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="fd530-106">En SharePoint, Exchange, Lync y recursos compartidos de archivos</span><span class="sxs-lookup"><span data-stu-id="fd530-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="fd530-p101">El diagrama muestra un usuario que envíe una consulta que tiene acceso a dos conjuntos de servidores, un entorno de aplicación de SharePoint 2013 Enterprise y un conjunto de servicios de SharePoint de 2013. La granja de servidores de SharePoint 2013 Services se comunica con un conjunto de contenido de SharePoint 2013, 2013 de Exchange Server (que se comunica con Lync 2013) y archivos compartidos de Windows.</span><span class="sxs-lookup"><span data-stu-id="fd530-p101">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm. The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="fd530-109">La lista de flujo de exhibición de documentos electrónicos describe el flujo de datos y el orden en que las acciones de consulta de exhibición de documentos electrónicos se producen en SharePoint, Exchange, Lync y los recursos compartidos de archivos. </span><span class="sxs-lookup"><span data-stu-id="fd530-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="fd530-110">Primero de describe detalladamente la lista de flujo de exhibición de documentos electrónicos y después se describen detalladamente las características representadas en el diagrama. </span><span class="sxs-lookup"><span data-stu-id="fd530-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="fd530-111">Lista de flujo de exhibición de documentos electrónicos</span><span class="sxs-lookup"><span data-stu-id="fd530-111">eDiscovery Flow List</span></span>

<span data-ttu-id="fd530-p102">Los números de cada uno de los pasos descritos en esta lista corresponden a los pasos que se muestran en el diagrama. El diagrama se describe con mayor detalle más adelante en este documento </span><span class="sxs-lookup"><span data-stu-id="fd530-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="fd530-p103">casos de eDiscovery son creados, gestionados y utilizados en el centro de eDiscovery (EDC). La EDC es una colección de sitios de SharePoint de 2013. Esto es donde se definen los casos, se identifican los orígenes de seguimiento, se emiten consultas, se revisan los resultados de la consulta y suspensiones en el contenido se coloca o se quitan.</span><span class="sxs-lookup"><span data-stu-id="fd530-p103">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC). The EDC is a SharePoint 2013 site collection. This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="fd530-p104">La consulta de eDiscovery o acción, por ejemplo, colocar una suspensión, ReleaseHold o GetStatus, se retransmite desde la EDC para el proxy de aplicación de servicio de búsqueda (SSA) en el conjunto de servidores de empresa de la aplicación. El proxy de SSA, a continuación, retransmite el tráfico de lo SSA en el conjunto de servidores de servicios de la aplicación. En este ejemplo, la solicitud es colocar nada en el conjunto de contenido de SharePoint con "CONTOSO" en el nombre del archivo en espera.</span><span class="sxs-lookup"><span data-stu-id="fd530-p104">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm. The SSA proxy then relays the traffic to the SSA in the Services App Farm. In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="fd530-p105">Si la solicitud consiste en consultar un caso, la SSA consulta el índice de búsqueda. Después, el conjunto de resultados de consulta de exhibición de documentos electrónicos se devuelve al usuario a través del EDC. </span><span class="sxs-lookup"><span data-stu-id="fd530-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="fd530-p106">Si la solicitud es una acción, como colocar una suspensión o ReleaseHold, dicha acción se escribe en el Actions_Table en la base de datos administrativa de SSA. En este ejemplo, se escribe una solicitud de suspensión para nada en el conjunto de contenido de SharePoint con "CONTOSO" en la Actions_Table.</span><span class="sxs-lookup"><span data-stu-id="fd530-p106">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database. In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="fd530-124">A intervalos regulares, se activa el trabajo del temporizador con la operación de conservación local de exhibición de documentos electrónicos en la granja de contenido, el cual genera una solicitud de acciones pendientes y envía actualizaciones de estado mediante el proxy de SSA a la SSA. </span><span class="sxs-lookup"><span data-stu-id="fd530-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="fd530-p107">La consulta de acciones pendientes se retransmite a la central SSA, que consulta el Action_Table de acciones para el conjunto de contenido pendientes. El trabajo del temporizador de suspensión en lugar de granja de servidores de contenido también envía actualizaciones de estado de los objetos y las acciones que ha recibido, que se escriben en el ActionsTable.</span><span class="sxs-lookup"><span data-stu-id="fd530-p107">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm. The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="fd530-127">El SSA envía la solicitud de suspensión de cualquier contenido con "CONTOSO" en el nombre del conjunto de servidores de contenido de SharePoint 2013 para el trabajo del temporizador de suspensión en lugar de eDiscovery en la granja de servidores de contenido.</span><span class="sxs-lookup"><span data-stu-id="fd530-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="fd530-128">El eDiscovery lugar mantenga temporizador lugares de trabajo mantienen el "Sitio de CONTOSO" y "Contenido CONTOSO" en.</span><span class="sxs-lookup"><span data-stu-id="fd530-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="fd530-129">El trabajo del temporizador de conservación local de exhibición de documentos electrónicos se ejecuta periódicamente en la granja de SharePoint Enterprise para comprobar el estado de las acciones de detección y actualizarlo. </span><span class="sxs-lookup"><span data-stu-id="fd530-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="fd530-130">La consulta de estado se transmite a través del proxy de SSA de la granja de SharePoint Enterprise hacia la SSA de la granja SharePoint Services. </span><span class="sxs-lookup"><span data-stu-id="fd530-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="fd530-131">La SSA recupera el estado de Action_Table y lo devuelve al trabajo del temporizador en la granja de SharePoint Enterprise, la cual inserta las actualizaciones de estado en el EDC. </span><span class="sxs-lookup"><span data-stu-id="fd530-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="fd530-p108">Cuando el usuario de eDiscovery está buscando (o realizar una acción) para los orígenes de Exchange, como un buzón o el contenido archivado de Lync, el SSA central utiliza proxy de Exchange Web Services (EWS) para consultar los servicios Web Exchange. Exchange tiene su propia infraestructura de eDiscovery y de búsqueda y administra todas las llamadas de eDiscovery internamente.</span><span class="sxs-lookup"><span data-stu-id="fd530-p108">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services. Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="fd530-134">Los EWS responden a la SSA con resultados de búsqueda de exhibición de documentos electrónicos o con una respuesta a una solicitud de estado para una conservación basada en una consulta que, a su vez, se transmite al EDC. </span><span class="sxs-lookup"><span data-stu-id="fd530-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="fd530-135">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="fd530-135">Prerequisites</span></span>

- <span data-ttu-id="fd530-136">El motor de búsqueda Enterprise Search  debe estar configurado, los rastreos de búsqueda en los orígenes de contenido (SharePoint y los recursos compartidos de archivos de Windows) deben realizarse correctamente y todos los orígenes de contenido deben encontrarse en el índice. </span><span class="sxs-lookup"><span data-stu-id="fd530-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="fd530-137">La autenticación y la confianza de servidor a servidor deben estar configuradas entre la granja de SharePoint Services y Exchange, y también entre Exchange y Lync. </span><span class="sxs-lookup"><span data-stu-id="fd530-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="fd530-138">Descripción de los componentes del diagrama</span><span class="sxs-lookup"><span data-stu-id="fd530-138">Description of components in the diagram</span></span>

<span data-ttu-id="fd530-p109">El diagrama muestra un usuario que envíe una consulta que tiene acceso a dos conjuntos de servidores, un entorno de SharePoint 2013 empresarial de la aplicación y un conjunto de servicios de SharePoint de 2013. El conjunto de servidores de SharePoint Services interactúa con un conjunto de contenido de SharePoint 2013, 2013 de Exchange Server (las interfaces con Lync 2013) y archivos compartidos de Windows.</span><span class="sxs-lookup"><span data-stu-id="fd530-p109">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm. The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="fd530-141">El conjunto de servidores de SharePoint 2013 Enterprise App</span><span class="sxs-lookup"><span data-stu-id="fd530-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="fd530-142">El conjunto de servidores de SharePoint 2013 empresarial de la aplicación contiene los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="fd530-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="fd530-143">EDC</span><span class="sxs-lookup"><span data-stu-id="fd530-143">EDC</span></span>
    
- <span data-ttu-id="fd530-144">Proxy de SSA </span><span class="sxs-lookup"><span data-stu-id="fd530-144">SSA proxy</span></span> 
    
- <span data-ttu-id="fd530-145">Trabajo del temporizador</span><span class="sxs-lookup"><span data-stu-id="fd530-145">Timer job</span></span> 
    
<span data-ttu-id="fd530-p110">Cuando el usuario envía una consulta o una acción, esta se envía al EDC de la granja de SharePoint Enterprise. Se producen estas acciones: </span><span class="sxs-lookup"><span data-stu-id="fd530-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="fd530-148">La acción o la consulta se envía al proxy de SSA. </span><span class="sxs-lookup"><span data-stu-id="fd530-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="fd530-p111">El proxy de SSA envía una consulta de estado o una respuesta para el trabajo del temporizador de la granja de SharePoint Enterprise, y también envía una consulta de estado o una respuesta al servicio de SSA en la granja de SharePoint Services. Las acciones que se derivan de ello se describen en la sección sobre la granja de SharePoint Services. </span><span class="sxs-lookup"><span data-stu-id="fd530-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="fd530-151">Cuando recibe una respuesta, el trabajo del temporizador la envía al proxy de SSA y al EDC. </span><span class="sxs-lookup"><span data-stu-id="fd530-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="fd530-152">Los resultados de la consulta o la acción se envían al usuario desde el EDC. </span><span class="sxs-lookup"><span data-stu-id="fd530-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="fd530-153">Conjunto de servicios de SharePoint de 2013</span><span class="sxs-lookup"><span data-stu-id="fd530-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="fd530-154">La granja de servidores de SharePoint 2013 Services contiene los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="fd530-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="fd530-155">Servicio de SSA </span><span class="sxs-lookup"><span data-stu-id="fd530-155">SSA Service</span></span> 
    
- <span data-ttu-id="fd530-156">Base de datos del índice de búsqueda </span><span class="sxs-lookup"><span data-stu-id="fd530-156">Search index database</span></span> 
    
- <span data-ttu-id="fd530-p112">Base de datos de admin_db de SSA. Contiene la tabla de acciones en esta base de datos: mantenga versión mantenga GetStatus</span><span class="sxs-lookup"><span data-stu-id="fd530-p112">SSA admin_db database. The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="fd530-159">Proxy de EWS </span><span class="sxs-lookup"><span data-stu-id="fd530-159">EWS proxy</span></span> 
    
<span data-ttu-id="fd530-160">Cuando el proxy de SSA en la granja de SharePoint Enterprise envía una consulta de estado a la SSA en la granja de SharePoint Services, se producen estas acciones: </span><span class="sxs-lookup"><span data-stu-id="fd530-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="fd530-p113">Si la solicitud es una consulta, la SSA consulta el índice de búsqueda. Se envía una respuesta de detección a la SSA y después al usuario a través del EDC. </span><span class="sxs-lookup"><span data-stu-id="fd530-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="fd530-163">Si la solicitud es una acción de escritura, el servicio de SSA envía la acción de escritura a admin_db de SSA. </span><span class="sxs-lookup"><span data-stu-id="fd530-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="fd530-164">Un rastreo y responder los resultados de la solicitud se envía desde el SSA para el conjunto de servidores de contenido de SharePoint 2013 y se devuelve una respuesta para el SSA.</span><span class="sxs-lookup"><span data-stu-id="fd530-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="fd530-165">Se envía una consulta de rastreo y de resultados de respuesta desde la SSA a los recursos de archivos compartidos de Windows, y se devuelve una respuesta a la SSA. </span><span class="sxs-lookup"><span data-stu-id="fd530-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="fd530-166">Se envía una consulta de acciones, respuestas o actualizaciones de estado pendientes desde la SSA al proxy de SSA en la granja de contenido de SharePoint y se devuelve una respuesta a la SSA. </span><span class="sxs-lookup"><span data-stu-id="fd530-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="fd530-167">Se envía una solicitud de acción/estado de Exchange desde la SSA al proxy de EWS, que envía una solicitud de acción/ estado de consulta de Exchange al servicio Web Exchange en el servidor Exchange 2013.  </span><span class="sxs-lookup"><span data-stu-id="fd530-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="fd530-168">Se envía una consulta/respuesta de estado desde la SSA hacia admin_db de la SSA y se devuelve a la SSA. </span><span class="sxs-lookup"><span data-stu-id="fd530-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="fd530-169">Se envía una consulta/respuesta de acción pendiente desde la SSA hacia admin_db de la SSA y se devuelve a la SSA. </span><span class="sxs-lookup"><span data-stu-id="fd530-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="fd530-170">Conjunto de contenido de SharePoint de 2013</span><span class="sxs-lookup"><span data-stu-id="fd530-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="fd530-171">El conjunto de servidores de SharePoint 2013 contenido contiene los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="fd530-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="fd530-172">Proxy de SSA </span><span class="sxs-lookup"><span data-stu-id="fd530-172">SSA proxy</span></span> 
    
- <span data-ttu-id="fd530-173">Trabajo del temporizador</span><span class="sxs-lookup"><span data-stu-id="fd530-173">Timer job</span></span> 
    
- <span data-ttu-id="fd530-174">Sitio de SharePoint de Contoso </span><span class="sxs-lookup"><span data-stu-id="fd530-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="fd530-175">Contenido de SharePoint de Contoso </span><span class="sxs-lookup"><span data-stu-id="fd530-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="fd530-176">Cuando la SSA en la granja de SharePoint Services envía una consulta de estado al proxy de SSA en la granja de contenido de SharePoint, se producen estas acciones: </span><span class="sxs-lookup"><span data-stu-id="fd530-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="fd530-177">El proxy de SSA en la granja de contenido de SharePoint envía una consulta de respuesta de estado/acciones pendientes al trabajo del temporizador. </span><span class="sxs-lookup"><span data-stu-id="fd530-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="fd530-178">El trabajo del temporizador envía una solicitud al sitio de SharePoint de Contoso, que revisa el contenido de SharePoint de Contoso. </span><span class="sxs-lookup"><span data-stu-id="fd530-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="fd530-179">La respuesta a la consulta de estado/acciones pendientes se envía desde el trabajo del temporizador hacia el proxy de SSA en la granja de contenido de SharePoint y, después, se envía al servicio de SSA en la granja de SharePoint Services. </span><span class="sxs-lookup"><span data-stu-id="fd530-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="fd530-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="fd530-180">Exchange 2013</span></span>

<span data-ttu-id="fd530-181">El componente de servidor de Exchange 2013 contiene el servicio Web Exchange y proporciona lo siguiente: </span><span class="sxs-lookup"><span data-stu-id="fd530-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="fd530-182">Confianza/OAuth de servidor a servidor se controla entre el conjunto de contenido de SharePoint 2013 y 2013 de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fd530-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="fd530-183">La confianza/OAuth de servidor a servidor se controla entre Exchange 2013 y Lync 2013. </span><span class="sxs-lookup"><span data-stu-id="fd530-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="fd530-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="fd530-184">Lync 2013</span></span>

<span data-ttu-id="fd530-185">El componente Lync 2013 archiva contenido de Lync en Exchange 2013. </span><span class="sxs-lookup"><span data-stu-id="fd530-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="fd530-186">Recursos compartidos de archivos de Windows</span><span class="sxs-lookup"><span data-stu-id="fd530-186">Windows File Shares</span></span>

<span data-ttu-id="fd530-187">El componente de recursos compartidos de archivos de Windows proporciona resultados de rastreo para la SSA en la granja de SharePoint Services. </span><span class="sxs-lookup"><span data-stu-id="fd530-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="fd530-188">Leyenda</span><span class="sxs-lookup"><span data-stu-id="fd530-188">Legend</span></span>

<span data-ttu-id="fd530-189">La leyenda de este diagrama muestra de forma gráfica los distintos tipos de tráfico representados entre los componentes con líneas de colores distintos: </span><span class="sxs-lookup"><span data-stu-id="fd530-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="fd530-190">Línea azul claro: consulta/acción - datos de consulta o acción de eDiscovery</span><span class="sxs-lookup"><span data-stu-id="fd530-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="fd530-191">Línea naranja: respuesta de eDiscovery - datos de respuesta de consulta de eDiscovery</span><span class="sxs-lookup"><span data-stu-id="fd530-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="fd530-192">Línea verde: consultas y respuestas de estado - datos de consultas y respuestas de estado de eDiscovery</span><span class="sxs-lookup"><span data-stu-id="fd530-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="fd530-193">Púrpura línea: solicitud de acción o estado de Exchange - solicitud de eDiscovery para el estado de la acción para el tráfico de Exchange.</span><span class="sxs-lookup"><span data-stu-id="fd530-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="fd530-194">Línea roja: intercambiar respuesta datos/estado - respuesta de consulta o estado de eDiscovery desde Exchange.</span><span class="sxs-lookup"><span data-stu-id="fd530-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="fd530-195">Línea negra discontinua: OAuth/Confianza de servidor a servidor </span><span class="sxs-lookup"><span data-stu-id="fd530-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="fd530-196">Línea negra fija: Rastreo/resultados </span><span class="sxs-lookup"><span data-stu-id="fd530-196">Solid black line: Crawl/results</span></span> 
    

