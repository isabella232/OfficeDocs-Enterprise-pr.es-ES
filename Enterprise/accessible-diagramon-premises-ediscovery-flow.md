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
# <a name="accessible-diagram---on-premises-ediscovery-flow"></a><span data-ttu-id="19a7f-103">Diagrama accesible: Flujo de exhibición de documentos electrónicos local</span><span class="sxs-lookup"><span data-stu-id="19a7f-103">Accessible diagram - On-premises eDiscovery Flow</span></span>

<span data-ttu-id="19a7f-104">**Resumen:** Este artículo es una versión de texto accesible del diagrama denominada flujo de exhibición de documentos electrónicos local.</span><span class="sxs-lookup"><span data-stu-id="19a7f-104">**Summary:** This article is an accessible text version of the diagram named On-premises eDiscovery Flow.</span></span>
  
<span data-ttu-id="19a7f-105">En este póster se explica de manera detallada la arquitectura y el flujo de datos entre productos de servidor.</span><span class="sxs-lookup"><span data-stu-id="19a7f-105">This poster provides details about the architecture and flow of data across server products.</span></span> 
  
## <a name="across-sharepoint-exchange-lync-and-file-shares"></a><span data-ttu-id="19a7f-106">En SharePoint, Exchange, Lync y recursos compartidos de archivos</span><span class="sxs-lookup"><span data-stu-id="19a7f-106">Across SharePoint, Exchange, Lync, and file shares</span></span>

<span data-ttu-id="19a7f-107">El diagrama muestra un usuario que envía una consulta que tiene acceso a dos granjas de servidores, una granja de aplicaciones de SharePoint 2013 Enterprise y una granja de servicios de SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="19a7f-107">The diagram shows a user sending a query that accesses two server farms, a SharePoint 2013 Enterprise App Farm, and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="19a7f-108">La granja de servicios de SharePoint 2013 se comunica con una granja de contenido de SharePoint 2013, Exchange Server 2013 (que se comunica con Lync 2013) y recursos compartidos de archivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="19a7f-108">The SharePoint 2013 Services Farm communicates with a SharePoint 2013 Content Farm, Exchange Server 2013 (which communicates with Lync 2013), and Windows File Shares.</span></span> 
  
<span data-ttu-id="19a7f-109">La lista de flujo de exhibición de documentos electrónicos describe el flujo de datos y el orden en que las acciones de consulta de exhibición de documentos electrónicos se producen en SharePoint, Exchange, Lync y los recursos compartidos de archivos. </span><span class="sxs-lookup"><span data-stu-id="19a7f-109">The eDiscovery Flow List describes the flow of data and the order in which eDisovery query actions occur across SharePoint, Exchange, Lync, and file shares.</span></span> 
  
<span data-ttu-id="19a7f-110">Primero de describe detalladamente la lista de flujo de exhibición de documentos electrónicos y después se describen detalladamente las características representadas en el diagrama. </span><span class="sxs-lookup"><span data-stu-id="19a7f-110">The eDiscovery flow list is described in detail first, followed by a detailed description of the features depicted in the diagram.</span></span> 
  
### <a name="ediscovery-flow-list"></a><span data-ttu-id="19a7f-111">Lista de flujo de exhibición de documentos electrónicos</span><span class="sxs-lookup"><span data-stu-id="19a7f-111">eDiscovery Flow List</span></span>

<span data-ttu-id="19a7f-p102">Los números de cada uno de los pasos descritos en esta lista corresponden a los pasos que se muestran en el diagrama. El diagrama se describe con mayor detalle más adelante en este documento </span><span class="sxs-lookup"><span data-stu-id="19a7f-p102">The numbers for each of the steps described in this list pertain to a step depicted in the diagram. The diagram is described in detail later in this document.</span></span> 
  
1. <span data-ttu-id="19a7f-114">Los casos de exhibición de documentos electrónicos se crean, gestionan y usan en el centro de exhibición de documentos electrónicos (EDC).</span><span class="sxs-lookup"><span data-stu-id="19a7f-114">eDiscovery cases are created, managed, and used in the eDiscovery center (EDC).</span></span> <span data-ttu-id="19a7f-115">EDC es una colección de sitios de SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="19a7f-115">The EDC is a SharePoint 2013 site collection.</span></span> <span data-ttu-id="19a7f-116">Aquí es donde se definen los casos, se identifican los orígenes que se deben seguir, se emiten las consultas, se revisan los resultados de las consultas y se establecen o eliminan las operaciones de conservación de contenido.</span><span class="sxs-lookup"><span data-stu-id="19a7f-116">This is where cases are defined, sources to be tracked are identified, queries are issued, query results are reviewed, and holds on content are placed or removed.</span></span> 
    
2. <span data-ttu-id="19a7f-117">La consulta o la acción de exhibición de documentos electrónicos, como las operaciones Hold, ReleaseHold o GetStatus, se transmiten desde el EDC al proxy de la aplicación de servicio de búsqueda (SSA) en la granja de SharePoint Enterprise.</span><span class="sxs-lookup"><span data-stu-id="19a7f-117">The eDiscovery query or action, such as place a Hold, ReleaseHold, or GetStatus, is relayed from the EDC to the Search Service Application (SSA) proxy in the Enterprise App Farm.</span></span> <span data-ttu-id="19a7f-118">Después, el proxy de SSA transmite el tráfico a la SSA en la granja de SharePoint Services.</span><span class="sxs-lookup"><span data-stu-id="19a7f-118">The SSA proxy then relays the traffic to the SSA in the Services App Farm.</span></span> <span data-ttu-id="19a7f-119">En este ejemplo, la solicitud es ubicar cualquier cosa en la granja de contenido de SharePoint con "CONTOSO" en el nombre de archivo en retención.</span><span class="sxs-lookup"><span data-stu-id="19a7f-119">In this example, the request is to place anything in the SharePoint Content Farm with "CONTOSO" in the file name on hold.</span></span> 
    
3. <span data-ttu-id="19a7f-p105">Si la solicitud consiste en consultar un caso, la SSA consulta el índice de búsqueda. Después, el conjunto de resultados de consulta de exhibición de documentos electrónicos se devuelve al usuario a través del EDC. </span><span class="sxs-lookup"><span data-stu-id="19a7f-p105">If the request is to query a case, the SSA consults the search index. Then, the eDiscovery query result set returns to the user through the EDC.</span></span> 
    
4. <span data-ttu-id="19a7f-122">Si la solicitud es una acción, como ejecutar una operación Hold o ReleaseHold, esa acción se escribe en la tabla Actions_Table en la base de datos administrativa de la SSA.</span><span class="sxs-lookup"><span data-stu-id="19a7f-122">If the request is an action, such as place a Hold or ReleaseHold, that action is written to the Actions_Table in the SSA Administrative database.</span></span> <span data-ttu-id="19a7f-123">En este ejemplo, se escribe una solicitud de retención para cualquier cosa de la granja de contenido de SharePoint con "CONTOSO" en Actions_Table.</span><span class="sxs-lookup"><span data-stu-id="19a7f-123">In this example, a hold request for anything in the SharePoint Content Farm with "CONTOSO" is written to the Actions_Table.</span></span> 
    
5. <span data-ttu-id="19a7f-124">A intervalos regulares, se activa el trabajo del temporizador con la operación de conservación local de exhibición de documentos electrónicos en la granja de contenido, el cual genera una solicitud de acciones pendientes y envía actualizaciones de estado mediante el proxy de SSA a la SSA.</span><span class="sxs-lookup"><span data-stu-id="19a7f-124">At regular intervals the Content Farm eDiscovery in-place hold timer job wakes up and generates a request for pending actions and sends status updates through the SSA proxy to the SSA.</span></span> 
    
6. <span data-ttu-id="19a7f-125">La consulta de acciones pendientes se transmite a la SSA central, que a su vez consulta en Actions_Table si hay alguna acción pendiente para la granja de contenido.</span><span class="sxs-lookup"><span data-stu-id="19a7f-125">The query for pending actions is relayed to the central SSA, which consults the Action_Table for any pending actions for the Content Farm.</span></span> <span data-ttu-id="19a7f-126">El trabajo del temporizador de conservación local en la granja de contenido también envía actualizaciones de estado para objetos y acciones que ha recibido, y estas se escriben en Action_Table.</span><span class="sxs-lookup"><span data-stu-id="19a7f-126">The Content Farm in-place hold timer job also sends status updates for objects and actions it has received, which are written to the ActionsTable.</span></span> 
    
7. <span data-ttu-id="19a7f-127">El SSA envía la solicitud de retención para cualquier contenido con "CONTOSO" en el nombre de la granja de contenido de SharePoint 2013 al trabajo del temporizador de conservación local de eDiscovery en la granja de servidores de contenido.</span><span class="sxs-lookup"><span data-stu-id="19a7f-127">The hold request for any content with "CONTOSO" in the name in the SharePoint 2013 Content Farm is sent by the SSA to the eDiscovery in-place hold timer job in the Content Farm.</span></span> 
    
8. <span data-ttu-id="19a7f-128">El trabajo del temporizador de conservación local de eDiscovery coloca el "sitio de CONTOSO" y el "contenido de CONTOSO" en espera.</span><span class="sxs-lookup"><span data-stu-id="19a7f-128">The eDiscovery in-place hold timer job places the "CONTOSO Site" and "CONTOSO content" on hold.</span></span> 
    
9. <span data-ttu-id="19a7f-129">El trabajo del temporizador de conservación local de exhibición de documentos electrónicos se ejecuta periódicamente en la granja de SharePoint Enterprise para comprobar el estado de las acciones de detección y actualizarlo. </span><span class="sxs-lookup"><span data-stu-id="19a7f-129">The eDiscovery in-place hold timer job periodically runs in the Enterprise App Farm to check the status of discovery actions and to update the status.</span></span> 
    
10. <span data-ttu-id="19a7f-130">La consulta de estado se transmite a través del proxy de SSA de la granja de SharePoint Enterprise hacia la SSA de la granja SharePoint Services. </span><span class="sxs-lookup"><span data-stu-id="19a7f-130">The status query is relayed through the Enterprise App Farm SSA proxy to the SharePoint Services Farm SSA.</span></span> 
    
11. <span data-ttu-id="19a7f-131">La SSA recupera el estado de Action_Table y lo devuelve al trabajo del temporizador en la granja de SharePoint Enterprise, la cual inserta las actualizaciones de estado en el EDC.</span><span class="sxs-lookup"><span data-stu-id="19a7f-131">The SSA retrieves the status from the Actions table and returns it to the timer job in the Enterprise App Farm, which pushes the status updates to the EDC.</span></span> 
    
12. <span data-ttu-id="19a7f-132">Cuando el usuario de exhibición de documentos electrónicos realiza una búsqueda (o ejecuta una acción) en los orígenes de Exchange, como buscar un buzón de correo o contenido de Lync archivado, la SSA central usa el proxy de los servicios Web Exchange (EWS) para consultar los EWS.</span><span class="sxs-lookup"><span data-stu-id="19a7f-132">When the eDiscovery user is searching (or performing an action) for Exchange sources, such as a mailbox or archived Lync content, the central SSA uses Exchange Web Services (EWS) proxy to query Exchange Web Services.</span></span> <span data-ttu-id="19a7f-133">Exchange tiene su propia infraestructura de búsqueda y exhibición de documentos electrónicos, y gestiona internamente todas las llamadas a exhibición de documentos electrónicos.</span><span class="sxs-lookup"><span data-stu-id="19a7f-133">Exchange has its own search and eDiscovery infrastructure and manages all eDiscovery calls internally.</span></span> 
    
13. <span data-ttu-id="19a7f-134">Los EWS responden a la SSA con resultados de búsqueda de exhibición de documentos electrónicos o con una respuesta a una solicitud de estado para una conservación basada en una consulta que, a su vez, se transmite al EDC. </span><span class="sxs-lookup"><span data-stu-id="19a7f-134">Exchange Web Services responds to SSA with eDiscovery search results or a response to a status request for a query-based hold, which, in turn, gets relayed to the EDC.</span></span> 
    
#### <a name="prerequisites"></a><span data-ttu-id="19a7f-135">Requisitos previos</span><span class="sxs-lookup"><span data-stu-id="19a7f-135">Prerequisites</span></span>

- <span data-ttu-id="19a7f-136">El motor de búsqueda Enterprise Search  debe estar configurado, los rastreos de búsqueda en los orígenes de contenido (SharePoint y los recursos compartidos de archivos de Windows) deben realizarse correctamente y todos los orígenes de contenido deben encontrarse en el índice. </span><span class="sxs-lookup"><span data-stu-id="19a7f-136">SharePoint Enterprise Search must be configured, search crawls on content sources (SharePoint and Windows file shares) are successfully occurring, and all content sources are in the index.</span></span> 
    
- <span data-ttu-id="19a7f-137">La autenticación y la confianza de servidor a servidor deben estar configuradas entre la granja de SharePoint Services y Exchange, y también entre Exchange y Lync. </span><span class="sxs-lookup"><span data-stu-id="19a7f-137">Server-to-server trust and authentication must be configured between the SharePoint Services Farm and Exchange and also between Exchange and Lync.</span></span> 
    
### <a name="description-of-components-in-the-diagram"></a><span data-ttu-id="19a7f-138">Descripción de los componentes del diagrama</span><span class="sxs-lookup"><span data-stu-id="19a7f-138">Description of components in the diagram</span></span>

<span data-ttu-id="19a7f-139">El diagrama muestra un usuario que envía una consulta, que tiene acceso a dos granjas de servidores, una granja de aplicaciones de SharePoint 2013 Enterprise y una granja de servicios de SharePoint 2013.</span><span class="sxs-lookup"><span data-stu-id="19a7f-139">The diagram shows a user sending a query, which accesses two server farms, a SharePoint 2013 Enterprise App Farm and a SharePoint 2013 Services Farm.</span></span> <span data-ttu-id="19a7f-140">La granja de SharePoint Services interactúa con una granja de contenido de SharePoint 2013, Exchange Server 2013 (que interactúa con Lync 2013) y recursos compartidos de archivos de Windows.</span><span class="sxs-lookup"><span data-stu-id="19a7f-140">The SharePoint Services Farm interfaces with a SharePoint 2013 Content Farm, Exchange Server 2013 (which interfaces with Lync 2013), and Windows File Shares.</span></span> 
  
#### <a name="sharepoint-2013-enterprise-app-farm"></a><span data-ttu-id="19a7f-141">Granja de servidores de aplicaciones empresariales de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="19a7f-141">SharePoint 2013 Enterprise App Farm</span></span>

<span data-ttu-id="19a7f-142">La granja de aplicaciones de SharePoint 2013 Enterprise contiene los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="19a7f-142">The SharePoint 2013 Enterprise App Farm contains the following components:</span></span> 
  
- <span data-ttu-id="19a7f-143">EDC</span><span class="sxs-lookup"><span data-stu-id="19a7f-143">EDC</span></span>
    
- <span data-ttu-id="19a7f-144">Proxy de SSA </span><span class="sxs-lookup"><span data-stu-id="19a7f-144">SSA proxy</span></span> 
    
- <span data-ttu-id="19a7f-145">Trabajo del temporizador</span><span class="sxs-lookup"><span data-stu-id="19a7f-145">Timer job</span></span> 
    
<span data-ttu-id="19a7f-p110">Cuando el usuario envía una consulta o una acción, esta se envía al EDC de la granja de SharePoint Enterprise. Se producen estas acciones: </span><span class="sxs-lookup"><span data-stu-id="19a7f-p110">A query or action sent by the user is sent to the EDC in the Enterprise App Farm. The following actions occur:</span></span> 
  
- <span data-ttu-id="19a7f-148">La acción o la consulta se envía al proxy de SSA. </span><span class="sxs-lookup"><span data-stu-id="19a7f-148">The query or action goes to the SSA proxy.</span></span> 
    
- <span data-ttu-id="19a7f-p111">El proxy de SSA envía una consulta de estado o una respuesta para el trabajo del temporizador de la granja de SharePoint Enterprise, y también envía una consulta de estado o una respuesta al servicio de SSA en la granja de SharePoint Services. Las acciones que se derivan de ello se describen en la sección sobre la granja de SharePoint Services. </span><span class="sxs-lookup"><span data-stu-id="19a7f-p111">The SSA proxy sends a status query or response to the Timer job in the Enterprise App Farm, and it also sends a status query or response to the SSA service in the SharePoint Services Farm. The actions that result from this are described in the section about the SharePoint Services Farm.</span></span> 
    
- <span data-ttu-id="19a7f-151">Cuando recibe una respuesta, el trabajo del temporizador la envía al proxy de SSA y al EDC. </span><span class="sxs-lookup"><span data-stu-id="19a7f-151">When it receives a response, the Timer job sends the response to the SSA proxy and to the EDC.</span></span> 
    
- <span data-ttu-id="19a7f-152">Los resultados de la consulta o la acción se envían al usuario desde el EDC. </span><span class="sxs-lookup"><span data-stu-id="19a7f-152">Any results from the query or action are sent to the user from the EDC.</span></span> 
    
#### <a name="sharepoint-2013-services-farm"></a><span data-ttu-id="19a7f-153">Granja de servicios de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="19a7f-153">SharePoint 2013 Services Farm</span></span>

<span data-ttu-id="19a7f-154">La granja de servicios de SharePoint 2013 contiene los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="19a7f-154">The SharePoint 2013 Services Farm contains the following components:</span></span> 
  
- <span data-ttu-id="19a7f-155">Servicio de SSA </span><span class="sxs-lookup"><span data-stu-id="19a7f-155">SSA Service</span></span> 
    
- <span data-ttu-id="19a7f-156">Base de datos del índice de búsqueda</span><span class="sxs-lookup"><span data-stu-id="19a7f-156">Search index database</span></span> 
    
- <span data-ttu-id="19a7f-157">Base de datos de admin_db de SSA.</span><span class="sxs-lookup"><span data-stu-id="19a7f-157">SSA admin_db database.</span></span> <span data-ttu-id="19a7f-158">La tabla de acciones de esta base de datos contiene: retener retenciones de suspensión</span><span class="sxs-lookup"><span data-stu-id="19a7f-158">The Actions Table in this database contains: Hold Release Hold GetStatus</span></span> 
    
- <span data-ttu-id="19a7f-159">Proxy de EWS </span><span class="sxs-lookup"><span data-stu-id="19a7f-159">EWS proxy</span></span> 
    
<span data-ttu-id="19a7f-160">Cuando el proxy de SSA en la granja de SharePoint Enterprise envía una consulta de estado a la SSA en la granja de SharePoint Services, se producen estas acciones: </span><span class="sxs-lookup"><span data-stu-id="19a7f-160">When the SSA proxy in the SharePoint Enterprise App Farm sends a status query to the SSA in the SharePoint Services Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="19a7f-p113">Si la solicitud es una consulta, la SSA consulta el índice de búsqueda. Se envía una respuesta de detección a la SSA y después al usuario a través del EDC. </span><span class="sxs-lookup"><span data-stu-id="19a7f-p113">If the request is a query, the SSA consults the search index. The discovery response is returned to the SSA and then to the user through the EDC.</span></span> 
    
- <span data-ttu-id="19a7f-163">Si la solicitud es una acción de escritura, el servicio de SSA envía la acción de escritura a admin_db de SSA. </span><span class="sxs-lookup"><span data-stu-id="19a7f-163">If the request is a write action, the SSA service sends the write action to the SSA admin_db.</span></span> 
    
- <span data-ttu-id="19a7f-164">Se envía una solicitud de resultados de rastreo y respuesta desde el SSA a la granja de servidores de contenido de SharePoint 2013 y se devuelve una respuesta a la SSA.</span><span class="sxs-lookup"><span data-stu-id="19a7f-164">A crawl and responding results request is sent from the SSA to the SharePoint 2013 Content Farm and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="19a7f-165">Se envía una consulta de rastreo y de resultados de respuesta desde la SSA a los recursos de archivos compartidos de Windows, y se devuelve una respuesta a la SSA. </span><span class="sxs-lookup"><span data-stu-id="19a7f-165">A crawl and responding results request is sent from the SSA to the Windows File Shares, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="19a7f-166">Se envía una consulta de acciones, respuestas o actualizaciones de estado pendientes desde la SSA al proxy de SSA en la granja de contenido de SharePoint y se devuelve una respuesta a la SSA. </span><span class="sxs-lookup"><span data-stu-id="19a7f-166">A query for pending action(s), responses, or status updates is sent from the SSA to the SSA proxy in the SharePoint Content Farm, and a response is returned to the SSA.</span></span> 
    
- <span data-ttu-id="19a7f-167">Se envía una solicitud de acción/estado de Exchange desde la SSA al proxy de EWS, que envía una solicitud de acción/ estado de consulta de Exchange al servicio Web Exchange en el servidor Exchange 2013.  </span><span class="sxs-lookup"><span data-stu-id="19a7f-167">An Exchange action/status request is sent from the SSA to the EWS proxy, which sends an Exchange Query action/status request to the Exchange Web Service on the Exchange 2013 server.</span></span> 
    
- <span data-ttu-id="19a7f-168">Se envía una consulta/respuesta de estado desde la SSA hacia admin_db de la SSA y se devuelve a la SSA. </span><span class="sxs-lookup"><span data-stu-id="19a7f-168">A status query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
- <span data-ttu-id="19a7f-169">Se envía una consulta/respuesta de acción pendiente desde la SSA hacia admin_db de la SSA y se devuelve a la SSA. </span><span class="sxs-lookup"><span data-stu-id="19a7f-169">A pending action query/response is sent from the SSA to the SSA admin_db and is returned to the SSA.</span></span> 
    
#### <a name="sharepoint-2013-content-farm"></a><span data-ttu-id="19a7f-170">Granja de contenido de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="19a7f-170">SharePoint 2013 Content Farm</span></span>

<span data-ttu-id="19a7f-171">La granja de contenido de SharePoint 2013 contiene los siguientes componentes:</span><span class="sxs-lookup"><span data-stu-id="19a7f-171">The SharePoint 2013 Content Farm contains the following components:</span></span> 
  
- <span data-ttu-id="19a7f-172">Proxy de SSA </span><span class="sxs-lookup"><span data-stu-id="19a7f-172">SSA proxy</span></span> 
    
- <span data-ttu-id="19a7f-173">Trabajo del temporizador</span><span class="sxs-lookup"><span data-stu-id="19a7f-173">Timer job</span></span> 
    
- <span data-ttu-id="19a7f-174">Sitio de SharePoint de Contoso </span><span class="sxs-lookup"><span data-stu-id="19a7f-174">Contoso SharePoint site</span></span> 
    
- <span data-ttu-id="19a7f-175">Contenido de SharePoint de Contoso </span><span class="sxs-lookup"><span data-stu-id="19a7f-175">Contoso SharePoint content</span></span> 
    
<span data-ttu-id="19a7f-176">Cuando la SSA en la granja de SharePoint Services envía una consulta de estado al proxy de SSA en la granja de contenido de SharePoint, se producen estas acciones: </span><span class="sxs-lookup"><span data-stu-id="19a7f-176">When the SSA in the SharePoint Services Farm sends a status query to the SSA Proxy in the SharePoint Content Farm, the following actions occur:</span></span> 
  
- <span data-ttu-id="19a7f-177">El proxy de SSA en la granja de contenido de SharePoint envía una consulta de respuesta de estado/acciones pendientes al trabajo del temporizador. </span><span class="sxs-lookup"><span data-stu-id="19a7f-177">The SSA proxy in the SharePoint Content Farm sends a query for pending actions/status response to the Timer job.</span></span> 
    
- <span data-ttu-id="19a7f-178">El trabajo del temporizador envía una solicitud al sitio de SharePoint de Contoso, que revisa el contenido de SharePoint de Contoso. </span><span class="sxs-lookup"><span data-stu-id="19a7f-178">The Timer job sends a request to the Contoso SharePoint site, which reviews the Contoso SharePoint content.</span></span> 
    
- <span data-ttu-id="19a7f-179">La respuesta a la consulta de estado/acciones pendientes se envía desde el trabajo del temporizador hacia el proxy de SSA en la granja de contenido de SharePoint y, después, se envía al servicio de SSA en la granja de SharePoint Services. </span><span class="sxs-lookup"><span data-stu-id="19a7f-179">The response to the pending actions/status query is sent from the Timer job to the SSA proxy in the SharePoint Content Farm, and then it is sent to the SSA service in the SharePoint Services Farm</span></span> 
    
#### <a name="exchange-2013"></a><span data-ttu-id="19a7f-180">Exchange 2013</span><span class="sxs-lookup"><span data-stu-id="19a7f-180">Exchange 2013</span></span>

<span data-ttu-id="19a7f-181">El componente de servidor de Exchange 2013 contiene el servicio Web Exchange y proporciona lo siguiente: </span><span class="sxs-lookup"><span data-stu-id="19a7f-181">The Exchange 2013 server component contains the Exchange Web Service and provides the following:</span></span> 
  
- <span data-ttu-id="19a7f-182">La confianza/OAuth de servidor a servidor se controla entre la granja de servidores de contenido de SharePoint 2013 y la de Exchange 2013.</span><span class="sxs-lookup"><span data-stu-id="19a7f-182">Server-to-server Trust/OAuth is handled between the SharePoint 2013 Content Farm and Exchange 2013.</span></span> 
    
- <span data-ttu-id="19a7f-183">La confianza/OAuth de servidor a servidor se controla entre Exchange 2013 y Lync 2013. </span><span class="sxs-lookup"><span data-stu-id="19a7f-183">Server-to-server Trust/OAuth is handled between Exchange 2013 and Lync 2013.</span></span> 
    
#### <a name="lync-2013"></a><span data-ttu-id="19a7f-184">Lync 2013</span><span class="sxs-lookup"><span data-stu-id="19a7f-184">Lync 2013</span></span>

<span data-ttu-id="19a7f-185">El componente Lync 2013 archiva contenido de Lync en Exchange 2013. </span><span class="sxs-lookup"><span data-stu-id="19a7f-185">The Lync 2013 component archives Lync content in Exchange 2013.</span></span> 
  
#### <a name="windows-file-shares"></a><span data-ttu-id="19a7f-186">Recursos compartidos de archivos de Windows</span><span class="sxs-lookup"><span data-stu-id="19a7f-186">Windows File Shares</span></span>

<span data-ttu-id="19a7f-187">El componente de recursos compartidos de archivos de Windows proporciona resultados de rastreo para la SSA en la granja de SharePoint Services. </span><span class="sxs-lookup"><span data-stu-id="19a7f-187">The Windows File Shares component provides crawl results to the SSA in the SharePoint Services Farm.</span></span> 
  
### <a name="legend"></a><span data-ttu-id="19a7f-188">Legend</span><span class="sxs-lookup"><span data-stu-id="19a7f-188">Legend</span></span>

<span data-ttu-id="19a7f-189">La leyenda de este diagrama muestra de forma gráfica los distintos tipos de tráfico representados entre los componentes con líneas de colores distintos: </span><span class="sxs-lookup"><span data-stu-id="19a7f-189">The legend for this diagram graphically shows the different types of traffic depicted among the components in different colored lines as follows:</span></span> 
  
- <span data-ttu-id="19a7f-190">Línea azul claro: consulta/acción-datos de la consulta o de la acción de eDiscovery</span><span class="sxs-lookup"><span data-stu-id="19a7f-190">Light blue line: Query/action - eDiscovery query or action data</span></span> 
    
- <span data-ttu-id="19a7f-191">Línea naranja: datos de respuesta de consulta de las-eDiscovery Query Response</span><span class="sxs-lookup"><span data-stu-id="19a7f-191">Orange line: eDisovery response - eDiscovery query response data</span></span> 
    
- <span data-ttu-id="19a7f-192">Línea verde: estado de consulta/respuesta-estado de exhibición de documentos electrónicos datos de consulta/respuesta</span><span class="sxs-lookup"><span data-stu-id="19a7f-192">Green line: Status query/response - eDiscovery status query/response data</span></span> 
    
- <span data-ttu-id="19a7f-193">Línea púrpura: solicitud de acción/estado de Exchange-solicitud de exhibición de documentos electrónicos para el estado de acción del tráfico de Exchange.</span><span class="sxs-lookup"><span data-stu-id="19a7f-193">Purple line: Exchange action/status request - eDiscovery request for action status for Exchange traffic.</span></span> 
    
- <span data-ttu-id="19a7f-194">Línea roja: respuesta de estado/datos de Exchange-respuesta de consulta o estado de exhibición de documentos electrónicos de Exchange.</span><span class="sxs-lookup"><span data-stu-id="19a7f-194">Red line: Exchange data/status response - eDiscovery query or status response from Exchange.</span></span> 
    
- <span data-ttu-id="19a7f-195">Línea negra discontinua: OAuth/Confianza de servidor a servidor </span><span class="sxs-lookup"><span data-stu-id="19a7f-195">Dotted black line: Server-to-Server Trust/Oauth</span></span> 
    
- <span data-ttu-id="19a7f-196">Línea negra fija: Rastreo/resultados </span><span class="sxs-lookup"><span data-stu-id="19a7f-196">Solid black line: Crawl/results</span></span> 
    

