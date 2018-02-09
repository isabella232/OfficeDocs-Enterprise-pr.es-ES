---
title: "Diagrama accesible: Recuperación ante desastres de SharePoint para Microsoft Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: "Este artículo es una versión de texto accesible del diagrama con el nombre Recuperación ante desastres de SharePoint en Microsoft Azure."
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a><span data-ttu-id="d536e-103">Diagrama accesible: Recuperación ante desastres de SharePoint para Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="d536e-103">Accessible diagram - SharePoint Disaster Recovery to Microsoft Azure</span></span>

<span data-ttu-id="d536e-104">**Resumen:** Este artículo es una versión de texto accesible del diagrama denominado recuperación de desastres de SharePoint de Microsoft Azure.</span><span class="sxs-lookup"><span data-stu-id="d536e-104">**Summary:** This article is an accessible text version of the diagram named SharePoint Disaster Recovery to Microsoft Azure.</span></span>
  
<span data-ttu-id="d536e-105">En este póster se proporcionan ejemplos de arquitecturas para la creación de un entorno de recuperación de Azure. </span><span class="sxs-lookup"><span data-stu-id="d536e-105">This poster provides examples of architectures for building a recovery environment in Azure.</span></span> 
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a><span data-ttu-id="d536e-106">Entorno local con un entorno de recuperación de Azure</span><span class="sxs-lookup"><span data-stu-id="d536e-106">On-premises environment with an Azure recovery environment</span></span>

<span data-ttu-id="d536e-107">El diagrama muestra un ejemplo de arquitectura para el entorno de producción de un entorno local que usa Azure para la recuperación. </span><span class="sxs-lookup"><span data-stu-id="d536e-107">The diagram shows an example of architecture used for the production environment of an on-premises environment that uses Azure for recovery.</span></span> 
  
### <a name="on-premises-production-environment"></a><span data-ttu-id="d536e-108">Entorno de producción local</span><span class="sxs-lookup"><span data-stu-id="d536e-108">On-premises production environment</span></span>

<span data-ttu-id="d536e-109">El diagrama adjunto muestra un entorno de producción activo con cuatro niveles de servidores en una granja de servidores. </span><span class="sxs-lookup"><span data-stu-id="d536e-109">The accompanying diagram shows a live production environment with four tiers of servers in a server farm.</span></span> 
  
#### <a name="tier-1"></a><span data-ttu-id="d536e-110">Nivel 1</span><span class="sxs-lookup"><span data-stu-id="d536e-110">Tier 1</span></span>

<span data-ttu-id="d536e-p101">Hay dos servidores para servicios de front-end y procesamiento de consultas. Hay una partición de índice que proporciona una réplica de ambos servidores. </span><span class="sxs-lookup"><span data-stu-id="d536e-p101">There are two servers for front-end services and query processing. There is an index partition that provides a replica of both servers.</span></span> 
  
#### <a name="tier-2"></a><span data-ttu-id="d536e-113">Nivel 2</span><span class="sxs-lookup"><span data-stu-id="d536e-113">Tier 2</span></span>

<span data-ttu-id="d536e-114">En este nivel hay dos servidores para la caché distribuida. </span><span class="sxs-lookup"><span data-stu-id="d536e-114">There are two servers for distributed cache in this tier.</span></span> 
  
#### <a name="tier-3"></a><span data-ttu-id="d536e-115">Nivel 3</span><span class="sxs-lookup"><span data-stu-id="d536e-115">Tier 3</span></span>

<span data-ttu-id="d536e-p102">En este nivel hay tres servidores. Cada servidor proporciona los siguientes servicios: </span><span class="sxs-lookup"><span data-stu-id="d536e-p102">There are three servers in this tier. Each server provides the following services:</span></span> 
  
- <span data-ttu-id="d536e-118">Servicios de back-end </span><span class="sxs-lookup"><span data-stu-id="d536e-118">Backend services</span></span> 
    
- <span data-ttu-id="d536e-119">Administración</span><span class="sxs-lookup"><span data-stu-id="d536e-119">Admin</span></span> 
    
- <span data-ttu-id="d536e-120">Administrador de flujos de trabajo</span><span class="sxs-lookup"><span data-stu-id="d536e-120">Workflow manager</span></span> 
    
- <span data-ttu-id="d536e-121">Rastreo</span><span class="sxs-lookup"><span data-stu-id="d536e-121">Crawl</span></span> 
    
- <span data-ttu-id="d536e-122">Procesamiento de contenido</span><span class="sxs-lookup"><span data-stu-id="d536e-122">Content processing</span></span> 
    
- <span data-ttu-id="d536e-123">Análisis</span><span class="sxs-lookup"><span data-stu-id="d536e-123">Analytics</span></span> 
    
#### <a name="tier-4"></a><span data-ttu-id="d536e-124">Nivel 4</span><span class="sxs-lookup"><span data-stu-id="d536e-124">Tier 4</span></span>

<span data-ttu-id="d536e-p103">En este nivel hay dos servidores. Ambos servidores tienen tres grupos de disponibilidad, como se describe a continuación: </span><span class="sxs-lookup"><span data-stu-id="d536e-p103">There are two servers in this tier. Both servers have three availability groups, as follows:</span></span> 
  
- <span data-ttu-id="d536e-127">El grupo de disponibilidad 1 proporciona capacidades de búsqueda. </span><span class="sxs-lookup"><span data-stu-id="d536e-127">Availability group #1 provides search capabilities.</span></span> 
    
- <span data-ttu-id="d536e-128">El grupo de disponibilidad 2 proporciona contenido, configuración y aplicaciones de servicio. </span><span class="sxs-lookup"><span data-stu-id="d536e-128">Availability group #2 provides content, configuration, and service applications.</span></span> 
    
- <span data-ttu-id="d536e-129">El grupo de disponibilidad 3 proporciona contenido. </span><span class="sxs-lookup"><span data-stu-id="d536e-129">Availability group #3 provides content.</span></span> 
    
<span data-ttu-id="d536e-p104">También hay un servidor de uso compartido de archivos en este nivel. Los servidores del nivel 4 usan el trasvase de registros para comunicarse con este servidor. Este servidor, a su vez, se comunica mediante el servicio Replicación del sistema de archivos distribuido (DFSR) con un servidor del recurso compartido de archivos en el entorno de recuperación de espera semiactiva de Azure, tal como se describe en la sección siguiente. </span><span class="sxs-lookup"><span data-stu-id="d536e-p104">There is also a file sharing server in this tier. The tier 4 servers use log shipping to communicate with this server. This server, in turn, communicates over Distributed File System Replication (DFSR) to a file share server in the Azure warm standby recovery environment, as described in the following section.</span></span> 
  
### <a name="azure-recovery-environment"></a><span data-ttu-id="d536e-133">Entorno de recuperación de Azure</span><span class="sxs-lookup"><span data-stu-id="d536e-133">Azure recovery environment</span></span>

#### <a name="warm-standby-environment-running-virtual-machines"></a><span data-ttu-id="d536e-134">Entorno de espera semiactiva que ejecuta máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="d536e-134">Warm standby environment running virtual machines</span></span>

<span data-ttu-id="d536e-p105">El diagrama adjunto muestra el entorno local replicado exactamente en el entorno de recuperación de Azure. El servidor del recurso compartido de archivos en este entorno se vincula al entorno local a través de DFSR. DFSR transfiere los registros del entorno de producción al entorno de recuperación a través del servidor del recurso compartido de archivos. </span><span class="sxs-lookup"><span data-stu-id="d536e-p105">The accompanying diagram shows the on-premises environment replicated exactly in the Azure recovery environment. The file share server in this environment is linked to the on-premises environment through DFSR. DFSR transfers logs from the production environment to the recovery environment through the file share server.</span></span> 
  
### <a name="overview"></a><span data-ttu-id="d536e-138">Información general</span><span class="sxs-lookup"><span data-stu-id="d536e-138">Overview</span></span>

<span data-ttu-id="d536e-139">El entorno de recuperación ante desastres para una granja de SharePoint 2013 local puede alojarse en Azure.</span><span class="sxs-lookup"><span data-stu-id="d536e-139">The disaster recovery environment for an on-premises SharePoint 2013 farm can be hosted in Azure.</span></span> 
  
-  <span data-ttu-id="d536e-140"> Servicios de infraestructura de Azure proporciona un centro de datos secundario. </span><span class="sxs-lookup"><span data-stu-id="d536e-140">Azure Infrastructure Services provides a secondary datacenter.</span></span>
    
- <span data-ttu-id="d536e-141">Únicamente se pagan los recursos que se usan.</span><span class="sxs-lookup"><span data-stu-id="d536e-141">Pay only for the resources you use.</span></span> 
    
- <span data-ttu-id="d536e-142">Permite escalar horizontalmente granjas de servidores de recuperación de tamaño pequeño después de un desastre para cumplir con los objetivos de escala y capacidad. </span><span class="sxs-lookup"><span data-stu-id="d536e-142">Small recovery farms can be scaled out after a disaster to meet scale and capacity targets.</span></span> 
    
<span data-ttu-id="d536e-143">La granja de servidores de recuperación en Azure se configura de forma tan idéntica como sea posible a la granja de servidores de producción local. </span><span class="sxs-lookup"><span data-stu-id="d536e-143">The recovery farm in Azure is configured as identically as possible to the production on-premises farm.</span></span> 
  
- <span data-ttu-id="d536e-144">Misma representación de roles de servidor.</span><span class="sxs-lookup"><span data-stu-id="d536e-144">Same representation of server roles.</span></span> 
    
- <span data-ttu-id="d536e-145">Misma configuración de personalizaciones. </span><span class="sxs-lookup"><span data-stu-id="d536e-145">Same configuration of customizations.</span></span> 
    
- <span data-ttu-id="d536e-146">Misma configuración de las características de búsqueda (pueden ser en una versión más pequeña de la granja de servidores de producción). </span><span class="sxs-lookup"><span data-stu-id="d536e-146">Same configuration of search features (these can be on a smaller version of the production farm).</span></span> 
    
<span data-ttu-id="d536e-147">El trasvase de registros y el servicio DFSR se usan para copiar las copias de seguridad de la base de datos y los registros de transacciones en la granja de servidores de Azure. </span><span class="sxs-lookup"><span data-stu-id="d536e-147">Log shipping and DFSR are used to copy database backups and transaction logs to the Azure farm.</span></span> 
  
- <span data-ttu-id="d536e-p106">DFSR se usa para transferir los registros del entorno de producción al entorno de recuperación. En un escenario WAN, resulta más eficaz usar DFSR que trasvasar los registros directamente al servidor secundario en Azure.</span><span class="sxs-lookup"><span data-stu-id="d536e-p106">DFSR is used to transfer logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.</span></span> 
    
- <span data-ttu-id="d536e-150">Los registros se reproducen en los equipos con SQL Server basados en Azure. </span><span class="sxs-lookup"><span data-stu-id="d536e-150">Logs are replayed to the Azure-based SQL Server computers.</span></span> 
    
- <span data-ttu-id="d536e-151">Las bases de datos de registros trasvasados se asocian a la granja de servidores únicamente después de realizar un ejercicio de recuperación.</span><span class="sxs-lookup"><span data-stu-id="d536e-151">Log-shipped databases are not attached to the farm until a recovery exercise is performed.</span></span> 
    
<span data-ttu-id="d536e-152">Procedimientos de conmutación por error: </span><span class="sxs-lookup"><span data-stu-id="d536e-152">Failover procedures:</span></span> 
  
1. <span data-ttu-id="d536e-153">Detenga el trasvase de registros.</span><span class="sxs-lookup"><span data-stu-id="d536e-153">Stop log shipping.</span></span> 
    
2. <span data-ttu-id="d536e-154">Deje de aceptar tráfico a la granja de servidores principal.</span><span class="sxs-lookup"><span data-stu-id="d536e-154">Stop accepting traffic to the primary farm.</span></span> 
    
3. <span data-ttu-id="d536e-155">Reproduzca los registros de transacciones finales.</span><span class="sxs-lookup"><span data-stu-id="d536e-155">Replay the final transaction logs.</span></span> 
    
4. <span data-ttu-id="d536e-156">Adjunte las bases de datos de contenido a la granja de servidores.</span><span class="sxs-lookup"><span data-stu-id="d536e-156">Attach the content databases to the farm.</span></span> 
    
5. <span data-ttu-id="d536e-157">Inicie un rastreo completo.</span><span class="sxs-lookup"><span data-stu-id="d536e-157">Start a full crawl.</span></span> 
    
6. <span data-ttu-id="d536e-158">Restaure las aplicaciones de servicio a partir de las bases de datos de servicios que se han replicado.</span><span class="sxs-lookup"><span data-stu-id="d536e-158">Restore service applications from the replicated services databases.</span></span> 
    
<span data-ttu-id="d536e-159">Los objetivos de recuperación que ofrece esta solución incluyen: </span><span class="sxs-lookup"><span data-stu-id="d536e-159">Recovery objectives provided by this solution include:</span></span> 
  
- <span data-ttu-id="d536e-160">Sitios y contenido</span><span class="sxs-lookup"><span data-stu-id="d536e-160">Sites and content</span></span> 
    
- <span data-ttu-id="d536e-161">Búsqueda (rastreos repetidos, falta de historial de búsqueda) </span><span class="sxs-lookup"><span data-stu-id="d536e-161">Search (re-crawled, no search history)</span></span> 
    
- <span data-ttu-id="d536e-162">Servicios</span><span class="sxs-lookup"><span data-stu-id="d536e-162">Services</span></span>
    
<span data-ttu-id="d536e-163">Otros elementos que es posible resolver a través de los Servicios de Consultoría de Microsoft o de un asociado: </span><span class="sxs-lookup"><span data-stu-id="d536e-163">Additional items that can be addressed by Microsoft Consulting Services or a partner:</span></span> 
  
- <span data-ttu-id="d536e-164">Sincronización de soluciones de granja personalizadas</span><span class="sxs-lookup"><span data-stu-id="d536e-164">Synchronizing custom farm solutions</span></span> 
    
- <span data-ttu-id="d536e-165">Conexiones a orígenes de datos locales (conectividad a datos empresariales [BDC] y búsqueda de orígenes de contenido) </span><span class="sxs-lookup"><span data-stu-id="d536e-165">Connections to data sources on premises (Business Data Connectivity (BDC) and search content sources)</span></span> 
    
- <span data-ttu-id="d536e-166">Escenarios de restauración de búsqueda</span><span class="sxs-lookup"><span data-stu-id="d536e-166">Search restore scenarios</span></span> 
    
- <span data-ttu-id="d536e-167">Objetivos de tiempo de recuperación (RTO) y objetivos de punto de recuperación (RPO)</span><span class="sxs-lookup"><span data-stu-id="d536e-167">Recovery Time Objectives (RTO) and Recovery Point Objectives (RPO)</span></span> 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a><span data-ttu-id="d536e-168">Entorno de espera pasiva que ejecuta máquinas virtuales</span><span class="sxs-lookup"><span data-stu-id="d536e-168">Cold standby environment running virtual machines</span></span>

<span data-ttu-id="d536e-169">Los entornos de espera pasiva tardan más en iniciarse pero son más económicos. </span><span class="sxs-lookup"><span data-stu-id="d536e-169">Cold standby environments take longer to start but are less expensive.</span></span> 
  
- <span data-ttu-id="d536e-p107">La granja de servidores se crearon por completo, pero las máquinas virtuales se detuvieron después de crear la granja. Únicamente se pagan costos de procesamiento cuando las máquinas virtuales están en ejecución, pero sí se aplican costos de transferencia de datos de red y de almacenamiento. </span><span class="sxs-lookup"><span data-stu-id="d536e-p107">The farm is fully built, but the virtual machines are stopped after the farm is created. You pay only processing costs when the virtual machines are running, but storage and network data transfer costs apply.</span></span> 
    
- <span data-ttu-id="d536e-172">En caso de desastre, todas las máquinas virtuales en la granja de servidores se inician y se revisan. </span><span class="sxs-lookup"><span data-stu-id="d536e-172">In the event of a disaster, all the virtual machines in the farm are started and patched.</span></span> 
    
- <span data-ttu-id="d536e-173">Las copias de seguridad y los registros de transacciones se aplican a las bases de datos de la granja de servidores. </span><span class="sxs-lookup"><span data-stu-id="d536e-173">Backups and transaction logs are applied to the farm databases.</span></span> 
    
<span data-ttu-id="d536e-174">En la siguiente lista se describen procedimientos adicionales para los entornos de espera pasiva: </span><span class="sxs-lookup"><span data-stu-id="d536e-174">The following list describes additional procedures for cold standby environments:</span></span> 
  
- <span data-ttu-id="d536e-175">Active las máquinas virtuales con regularidad para revisar, actualizar y comprobar el entorno. </span><span class="sxs-lookup"><span data-stu-id="d536e-175">Turn on virtual machines regularly to patch, update, and verify the environment.</span></span> 
    
- <span data-ttu-id="d536e-176">Ejecute procedimientos para actualizar las direcciones IP y DNS. </span><span class="sxs-lookup"><span data-stu-id="d536e-176">Run procedures to refresh DNS and IP addresses.</span></span> 
    
- <span data-ttu-id="d536e-177">Configure SQL AlwaysOn después de una conmutación por error. </span><span class="sxs-lookup"><span data-stu-id="d536e-177">Set up SQL AlwaysOn after a failover.</span></span> 
    
<span data-ttu-id="d536e-p108">El diagrama adjunto muestra un entorno de recuperación replicado en máquinas virtuales. Después de una conmutación por error a un entorno de espera pasiva, todas las máquinas virtuales se inician y los grupos de disponibilidad se configuran usando la reproducción de registros para que los servidores de base de datos queden disponibles. </span><span class="sxs-lookup"><span data-stu-id="d536e-p108">The accompanying diagram shows a replicated recovery environment on virtual machines. After failover to a cold standby environment, all virtual machines are started, and the availability groups are configured using replay logs to make the database servers available.</span></span> 
  
## <a name="sharepoint-recovery-environment-in-azure"></a><span data-ttu-id="d536e-180">Entorno de recuperación de SharePoint en Azure</span><span class="sxs-lookup"><span data-stu-id="d536e-180">SharePoint recovery environment in Azure</span></span>

<span data-ttu-id="d536e-181">Diseñe y cree el entorno de conmutación por error en Azure. </span><span class="sxs-lookup"><span data-stu-id="d536e-181">Design and build the failover environment in Azure.</span></span> 
  
- <span data-ttu-id="d536e-182">Cree una red virtual en Azure.</span><span class="sxs-lookup"><span data-stu-id="d536e-182">Create a virtual network in Azure.</span></span> 
    
- <span data-ttu-id="d536e-p109">Conecte la red local a la red virtual en Azure con una conexión VPN sitio a sitio. Esta conexión usa una puerta de enlace dinámica en Azure. </span><span class="sxs-lookup"><span data-stu-id="d536e-p109">Connect the on-premises network with the virtual network in Azure with a site-to-site VPN connection. This connection uses a dynamic gateway in Azure.</span></span> 
    
- <span data-ttu-id="d536e-p110">Implemente uno o más controladores de dominio en la red virtual de Azure y configúrelos para que funcionen con el dominio local. Estos controladores de dominio son servidores de catálogo. </span><span class="sxs-lookup"><span data-stu-id="d536e-p110">Deploy one or more domain controllers to the Azure virtual network, and configure these to work with your on-premises domain. These domain controllers are catalog servers.</span></span> 
    
- <span data-ttu-id="d536e-187">Adapte la granja de servidores de SharePoint para los servicios en la nube y conjuntos de disponibilidad.  </span><span class="sxs-lookup"><span data-stu-id="d536e-187">Adapt the SharePoint farm for cloud services and availability sets.</span></span> 
    
- <span data-ttu-id="d536e-188">Implemente la granja de servidores de SharePoint y un servidor de archivos para hospedar recursos compartidos de archivos. </span><span class="sxs-lookup"><span data-stu-id="d536e-188">Deploy the SharePoint farm plus a file server to host file shares.</span></span> 
    
- <span data-ttu-id="d536e-189">Configure el trasvase de registros y DFSR entre el entorno local y el entorno de recuperación basado en Azure. </span><span class="sxs-lookup"><span data-stu-id="d536e-189">Set up log shipping and DFSR between the on-premises environment and the Azure-based recovery environment.</span></span> 
    
<span data-ttu-id="d536e-190">El diagrama adjunto muestra el entorno local y la red virtual de Azure con las siguientes características: </span><span class="sxs-lookup"><span data-stu-id="d536e-190">The accompanying diagram shows the on-premises environment and the Azure virtual network with the following features:</span></span> 
  
### <a name="on-premises-environment"></a><span data-ttu-id="d536e-191">Entorno local</span><span class="sxs-lookup"><span data-stu-id="d536e-191">On-premises environment</span></span>

- <span data-ttu-id="d536e-192">RRAS de Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d536e-192">Windows Server 2012 RRAS</span></span> 
    
- <span data-ttu-id="d536e-193">Servidor de Active Directory</span><span class="sxs-lookup"><span data-stu-id="d536e-193">Active Directory server</span></span> 
    
<span data-ttu-id="d536e-194">La red local interactúa con la red virtual Azure a través de una puerta de enlace de red privada virtual (VPN). </span><span class="sxs-lookup"><span data-stu-id="d536e-194">The on-premises network interfaces with the Azure virtual network over a virtual private network (VPN) gateway.</span></span> 
  
### <a name="azure-virtual-network"></a><span data-ttu-id="d536e-195">Red virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="d536e-195">Azure virtual network</span></span>

<span data-ttu-id="d536e-196">La puerta de enlace de VPN interactúa con una subred de puerta de enlace de VPN activa. </span><span class="sxs-lookup"><span data-stu-id="d536e-196">The VPN gateway interfaces with an active VPN gateway subnet.</span></span> 
  
<span data-ttu-id="d536e-197">Hay tres servicios en la nube en el entorno de red virtual de Azure:</span><span class="sxs-lookup"><span data-stu-id="d536e-197">There are three cloud services in the Azure virtual network:</span></span> 
  
- <span data-ttu-id="d536e-198">El primer servicio en la nube tiene dos servidores de Active Directory y DNS con un conjunto de disponibilidad. </span><span class="sxs-lookup"><span data-stu-id="d536e-198">The first cloud service has two Active Directory and DNS servers with an availability set.</span></span> 
    
- <span data-ttu-id="d536e-p111">El segundo servicio de nube tiene tres conjuntos de servidores: dos distribuyen servidores de caché con un conjunto de disponibilidad. Dos servidores front-end con un conjunto de disponibilidad. Tres servidores de back-end con un conjunto de disponibilidad.</span><span class="sxs-lookup"><span data-stu-id="d536e-p111">The second cloud service has three sets of servers: Two distributed cache servers with an availability set. Two front-end servers with an availability set. Three backend servers with an availability set.</span></span>
    
- <span data-ttu-id="d536e-p112">El tercer servicio en la nube tiene tres servidores de bases de datos con un conjunto de disponibilidad. Uno de estos servidores de bases de datos es un recurso compartido de archivos para el trasvase de registros y un tercer nodo de una mayoría de nodos para SQL Server AlwaysOn </span><span class="sxs-lookup"><span data-stu-id="d536e-p112">The third cloud service has three database servers with an availability set. One of these database servers is a file share for log shipping and a third node of a node majority for SQL Server AlwaysOn.</span></span> 
    
### <a name="build-the-ad-ds-hybrid-environment"></a><span data-ttu-id="d536e-204">Crear el entorno híbrido de AD DS</span><span class="sxs-lookup"><span data-stu-id="d536e-204">Build the AD DS hybrid environment</span></span>

<span data-ttu-id="d536e-205">La configuración de AD DS para esta solución consiste en un escenario de implementación híbrida en el que AD DS se implementa parcialmente en las instalaciones locales y parcialmente en máquinas virtuales de Azure. </span><span class="sxs-lookup"><span data-stu-id="d536e-205">The configuration of AD DS for this solution constitutes a hybrid deployment scenario in which AD DS is partly deployed on-premises and partly deployed on Azure virtual machines.</span></span> 
  
<span data-ttu-id="d536e-206">Importante: antes de implementar AD DS en Azure, lea las Directrices para implementar Windows Server Active Directory en máquinas virtuales de Azure (http://msdn.microsoft.com/es-es/library/windowsazure/jj156090.aspx). </span><span class="sxs-lookup"><span data-stu-id="d536e-206">Important — Before you deploy AD DS in Azure, read Guidelines for Deploying Windows Server Active Directory on Microsoft Azure Virtual Machines (http://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx).</span></span> 
  
<span data-ttu-id="d536e-207">Para obtener instrucciones completas sobre el diseño y la implementación de entornos de Active Directory, consulte http://TechNet.microsoft.com. </span><span class="sxs-lookup"><span data-stu-id="d536e-207">For complete guidance on designing and deploying Active Directory environments, see http://TechNet.microsoft.com.</span></span> 
  
<span data-ttu-id="d536e-p113">Esta arquitectura de referencia incluye dos máquinas virtuales configuradas como controladores de dominio. Cada una está configurada del modo siguiente:· </span><span class="sxs-lookup"><span data-stu-id="d536e-p113">This reference architecture includes two virtual machines configured as domain controllers. Each is configured as follows:</span></span> 
  
- <span data-ttu-id="d536e-210">Tamaño: pequeño. </span><span class="sxs-lookup"><span data-stu-id="d536e-210">Size — Small.</span></span> 
    
- <span data-ttu-id="d536e-211">Sistema operativo: Windows Server 2012.  </span><span class="sxs-lookup"><span data-stu-id="d536e-211">Operating system — Windows Server 2012.</span></span> 
    
- <span data-ttu-id="d536e-p114">Rol: controlador de dominio de AD DS designado como servidor de catálogo global. Esta configuración reduce el tráfico de salida a través de la conexión VPN. En un entorno de varios dominios con altas tasas de cambio, configure los controladores de dominio localmente para que no se sincronicen con los servidores de catálogo global en Azure.  </span><span class="sxs-lookup"><span data-stu-id="d536e-p114">Role — AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the VPN connection. In a multi-domain environment with high rates of change, configure domain controllers on-premises to not sync with the global catalog servers in Azure.</span></span> 
    
- <span data-ttu-id="d536e-p115">Discos de datos: es importante que coloque la base de datos, los registros y SYSVOL de AD DS en discos de datos de Azure. No los coloque en el disco del sistema operativo ni en los discos temporales proporcionados por Azure.</span><span class="sxs-lookup"><span data-stu-id="d536e-p115">Data disks — Place the AD DS database, logs, and SYSVOL on Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure. This is important.</span></span> 
    
- <span data-ttu-id="d536e-218">Rol: instale y configure el DNS de Windows en los controladores de dominio.</span><span class="sxs-lookup"><span data-stu-id="d536e-218">Role — Install and configure Windows DNS on the domain controllers.</span></span> 
    
- <span data-ttu-id="d536e-p116">Direcciones IP: use direcciones IP dinámicas. Esto requiere la creación de una red virtual de Azure. </span><span class="sxs-lookup"><span data-stu-id="d536e-p116">IP addresses — Use dynamic IP addresses. This requires you to create an Azure Virtual Network.</span></span> 
    

