---
title: Recuperación ante desastres de SharePoint Server 2013 en Microsoft Azure
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 04/17/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Deployment
ms.assetid: e9d14cb2-ff28-4a18-a444-cebf891880ea
description: 'Summary: Using Azure, you can create a disaster-recovery environment for your on-premises SharePoint farm. This article describes how to design and implement this solution.'
ms.openlocfilehash: 101d87b1a25d2b3ac8a7ae29832e52c805ecdc4c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998172"
---
# <a name="sharepoint-server-2013-disaster-recovery-in-microsoft-azure"></a>Recuperación ante desastres de SharePoint Server 2013 en Microsoft Azure

 Con Azure, puede crear un entorno de recuperación ante desastres para su granja de servidores local de SharePoint. En este artículo se describe cómo diseñar e implementar esta solución.

 **Ver el vídeo de información general sobre la recuperación ante desastres de SharePoint Server 2013**
> [!VIDEO https://www.microsoft.com/videoplayer/embed/1b73ec8f-29bd-44eb-aa3a-f7932784bfd9?autoplay=false]
  
 When disaster strikes your SharePoint on-premises environment, your top priority is to get the system running again quickly. Disaster recovery with SharePoint is quicker and easier when you have a backup environment already running in Microsoft Azure. This video explains the main concepts of a SharePoint warm failover environment and complements the full details available in this article.
  
Use este artículo con el modelo de solución: **recuperación ante desastres de SharePoint en Microsoft Azure**.
  
[![Proceso de recuperación ante desastres de SharePoint a Azure](media/SP-DR-Azure.png)](https://go.microsoft.com/fwlink/p/?LinkId=392555)
  
 [PDF](https://go.microsoft.com/fwlink/p/?LinkId=392555) |  [Visio](https://go.microsoft.com/fwlink/p/?LinkId=392554)
  
## <a name="use-azure-infrastructure-services-for-disaster-recovery"></a>Usar Servicios de infraestructura de Azure para recuperación ante desastres

Many organizations do not have a disaster recovery environment for SharePoint, which can be expensive to build and maintain on-premises. Azure Infrastructure Services provides compelling options for disaster recovery environments that are more flexible and less expensive than the on-premises alternatives.
  
Entre las ventajas de usar Servicios de infraestructura de Azure se incluyen:
  
- **Fewer costly resources** Maintain and pay for fewer resources than on-premises disaster recovery environments. The number of resources depends on which disaster-recovery environment you choose: cold standby, warm standby, or hot standby.
    
- **Better resource flexibility** In the event of a disaster, easily scale out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources.
    
- **Reducir el compromiso de los centros de datos** Use Servicios de infraestructura de Azure en lugar de invertir en un segundo centro de datos en una región distinta.
    
There are less-complex options for organizations just getting started with disaster recovery and advanced options for organizations with high-resilience requirements. The definitions for cold, warm, and hot standby environments are a little different when the environment is hosted on a cloud platform. The following table describes these environments for building a SharePoint recovery farm in Azure.
  
**Tabla: Entornos de recuperación**

|**Tipo de entorno de recuperación**|**Descripción**|
|:-----|:-----|
|Activa  <br/> |Se aprovisiona, actualiza y ejecuta una granja completa en modo de espera.  <br/> |
|Semiactiva  <br/> |Se crea la granja de servidores y se ponen en marcha y actualizan las máquinas virtuales.  <br/> La recuperación incluye adjuntar bases de datos de contenido, aprovisionar aplicaciones de servicio y rastrear contenido.  <br/> La granja de servidores puede ser una versión reducida de la granja de servidores de producción y más adelante se puede escalar horizontalmente para atender a la base completa de usuarios.  <br/> |
|Pasiva  <br/> |La granja de servidores se ha creado por completo, pero las máquinas virtuales están detenidas.  <br/> Para realizar el mantenimiento del entorno, hay que iniciar las máquinas virtuales de vez en cuando, revisar, actualizar y comprobar el entorno.  <br/> En caso de desastre, inicie el entorno completo.  <br/> |
   
It's important to evaluate your organization's Recovery Time Objectives (RTOs) and Recovery Point Objectives (RPOs). These requirements determine which environment is the most appropriate investment for your organization.
  
The guidance in this article describes how to implement a warm standby environment. You can also adapt it to a cold standby environment, although you need to follow additional procedures to support this kind of environment. This article does not describe how to implement a hot standby environment.
  
Para obtener más información sobre las soluciones de recuperación ante desastres, consulte [High availability and disaster recovery concepts in SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkID=393114) y [Choose a disaster recovery strategy for SharePoint 2013](https://go.microsoft.com/fwlink/p/?linkid=203228).
  
## <a name="solution-description"></a>Descripción de la solución

Para la solución de recuperación ante desastres de espera semiactiva se requiere este entorno:
  
- Una granja de servidores de producción de SharePoint local
    
- Una granja de servidores de recuperación de SharePoint en Azure
    
- Una conexión VPN de sitio a sitio entre los dos entornos
    
En esta ilustración se muestran estos tres elementos.
  
**Ilustración: Elementos de una solución en estado de espera semiactiva en Azure**

![Elementos de una solución de espera semiactiva de SharePoint en Azure](media/AZarch-AZWarmStndby.png)
  
El trasvase de registros de SQL Server con la Replicación del sistema de archivos distribuido (DFSR) se usa para copiar las copias de seguridad de bases de datos y los registros de transacciones en la granja de servidores de recuperación en Azure: 
  
- DFSR transfers logs from the production environment to the recovery environment. In a WAN scenario, DFSR is more efficient than shipping the logs directly to the secondary server in Azure.
    
- Los registros se reproducen para SQL Server en el entorno de recuperación de Azure.
    
- No adjunte bases de datos de contenido de SharePoint cuyos registros se han trasvasado en el entorno de recuperación, hasta que se realice un ejercicio de recuperación.
    
Siga estos pasos para recuperar la granja de servidores:
  
1. Detenga el trasvase de registros.
    
2. Deje de aceptar tráfico a la granja de servidores principal.
    
3. Reproduzca los registros de transacciones finales.
    
4. Adjunte las bases de datos de contenido a la granja de servidores.
    
5. Restaure las aplicaciones de servicio a partir de las bases de datos de servicios que se han replicado.
    
6. Actualice los registros del sistema de nombres de dominio (DNS) para que apunten a la granja de servidores de recuperación.
    
7. Inicie un rastreo completo.
    
We recommend that you rehearse these steps regularly and document them to help ensure that your live recovery runs smoothly. Attaching content databases and restoring service applications can take some time and typically involves some manual configuration.
  
Después de realizar una recuperación, esta solución proporciona los elementos que aparecen en la tabla siguiente.
  
**Tabla: Objetivos de recuperación de solución**

|**Elemento**|**Descripción**|
|:-----|:-----|
|Sitios y contenido  <br/> |Los sitios y el contenido están disponibles en el entorno de recuperación.  <br/> |
|Una nueva instancia de búsqueda  <br/> |In this warm standby solution, search is not restored from search databases. Search components in the recovery farm are configured as similarly as possible to the production farm. After the sites and content are restored, a full crawl is started to rebuild the search index. You do not need to wait for the crawl to complete to make the sites and content available.  <br/> |
|Servicios  <br/> | Services that store data in databases are restored from the log-shipped databases. Services that do not store data in databases are simply started. <br/>  Not all services with databases need to be restored. The following services do not need to be restored from databases and can simply be started after failover: <br/>  Recolección de datos de uso y estado <br/>  Servicio de estado <br/>  Automatización de Word <br/>  Cualquier otro servicio que no usa una base de datos <br/> |
   
You can work with Microsoft Consulting Services (MCS) or a partner to address more-complex recovery objectives. These are summarized in the following table.
  
**Tabla: Otros elementos que MCS o un socio pueden tratar**

|**Elemento**|**Descripción**|
|:-----|:-----|
|Sincronización de soluciones de granja personalizadas  <br/> |Ideally, the recovery farm configuration is identical to the production farm. You can work with a consultant or partner to evaluate whether custom farm solutions are replicated and whether the process is in place for keeping the two environments synchronized.  <br/> |
|Conexiones a orígenes de datos de locales  <br/> |No sería práctico replicar las conexiones en sistemas de datos back-end, como conexiones de controlador de dominio de reserva (BDC) y orígenes de contenido de búsqueda.  <br/> |
|Escenarios de restauración de búsqueda  <br/> |Because enterprise search deployments tend to be fairly unique and complex, restoring search from databases requires a greater investment. You can work with a consultant or partner to identify and implement search restore scenarios that your organization might require.  <br/> |
   
En las instrucciones proporcionadas en este artículo se supone que la granja de servidores ya está diseñada e implementada.
  
## <a name="detailed-architecture"></a>Arquitectura detallada

Lo ideal es que la configuración de la granja de servidores de recuperación en Azure sea idéntica a la granja de servidores de producción local, incluido lo siguiente:
  
- La misma representación de roles de servidor
    
- La misma configuración de personalizaciones
    
- La misma configuración de componentes de búsqueda
    
The environment in Azure can be a smaller version of the production farm. If you plan to scale out the recovery farm after failover, it's important that each type of server role be initially represented.
  
Some configurations might not be practical to replicate in the failover environment. Be sure to test the failover procedures and environment to help ensure that the failover farm provides the expected service level.
  
This solution doesn't prescribe a specific topology for a SharePoint farm. The focus of this solution is to use Azure for the failover farm and to implement log shipping and DFSR between the two environments.
  
### <a name="warm-standby-environments"></a>Entorno de espera semiactiva

In a warm standby environment, all virtual machines in the Azure environment are running. The environment is ready for a failover exercise or event.
  
En la siguiente ilustración se muestra una solución de recuperación ante desastres procedente de una granja de SharePoint local hacia una granja de SharePoint basada en Azure, que está configurada como un entorno de espera semiactiva.
  
**Ilustración: Topología y elementos clave de una granja de producción y una granja de servidores de recuperación en espera semiactiva.**

![Topología de una granja de servidores de SharePoint y una granja de servidores de recuperación con espera semiactiva](media/AZarch-AZWarmStndby.png)
  
En este diagrama:
  
- Se ilustran dos entornos en paralelo: la granja de SharePoint local y la granja de espera semiactiva en Azure.
    
- Cada entorno incluye un recurso compartido de archivos.
    
- Each farm includes four tiers. To achieve high availability, each tier includes two servers or virtual machines that are configured identically for a specific role, such as front-end services, distributed cache, back-end services, and databases. It isn't important in this illustration to call out specific components. The two farms are configured identically.
    
- The fourth tier is the database tier. Log shipping is used to copy logs from the secondary database server in the on-premises environment to the file share in the same environment.
    
- DFSR copia archivos desde el recurso compartido de archivos del entorno local hacia el recurso compartido de archivos en el entorno de Azure.
    
- El trasvase de registros reproduce los registros desde el recurso compartido de archivos en el entorno de Azure hasta la réplica principal en el grupo disponibilidad AlwaysOn de SQL Server en el entorno de recuperación.
    
### <a name="cold-standby-environments"></a>Entornos de espera pasiva

In a cold standby environment, most of the SharePoint farm virtual machines can be shut down. (We recommend occasionally starting the virtual machines, such as every two weeks or once a month, so that each virtual machine can sync with the domain.) The following virtual machines in the Azure recovery environment must remain running to help ensure continuous operations of log shipping and DFSR:
  
- El recurso compartido de archivos
    
- El servidor de bases de datos principal
    
- Al menos una máquina virtual que ejecute Servicios de dominio de Windows Server Active Directory y DNS
    
The following figure shows an Azure failover environment in which the file share virtual machine and the primary SharePoint database virtual machine are running. All other SharePoint virtual machines are stopped. The virtual machine that is running Windows Server Active Directory and DNS is not shown.
  
**Ilustración: Granja de servidores de recuperación de espera pasiva con máquinas virtuales en funcionamiento**

![Elementos de una solución de espera pasiva de SharePoint en Azure](media/AZarch-AZColdStndby.png)
  
Después de la conmutación por error a un entorno de espera pasiva, se inician todas las máquinas virtuales y debe configurarse el método para lograr una alta disponibilidad de los servidores de bases de datos, como los grupos de disponibilidad AlwaysOn de SQL Server.
  
Si se implementan varios grupos de almacenamiento (las bases de datos están dispersas en más de un conjunto de alta disponibilidad de SQL Server), la base de datos principal para cada grupo de almacenamiento debe estar ejecutándose para aceptar los registros asociados a su grupo de almacenamiento.
  
### <a name="skills-and-experience"></a>Conocimientos y experiencia

Multiple technologies are used in this disaster recovery solution. To help ensure that these technologies interact as expected, each component in the on-premises and Azure environment must be installed and configured correctly. We recommend that the person or team who sets up this solution have a strong working knowledge of and hands-on skills with the technologies described in the following articles:
  
- [Servicios de replicación del Sistema de archivos distribuido (DFS)](https://go.microsoft.com/fwlink/p/?LinkId=392698)
    
- [Clústeres de conmutación por error de Windows Server (WSFC) con SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392701)
    
- [Grupos de disponibilidad AlwaysOn (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392725)
    
- [Realizar copias de seguridad y restaurar bases de datos de SQL Server](https://go.microsoft.com/fwlink/p/?LinkId=392728)
    
- [Instalación e implementación de la granja de servidores de SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=393119)
    
- [Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=392729)
    
Finally, we recommend scripting skills that you can use to automate tasks associated with these technologies. It's possible to use the available user interfaces to complete all the tasks described in this solution. However, a manual approach can be time consuming and error prone and delivers inconsistent results.
  
In addition to Windows PowerShell, there are also Windows PowerShell libraries for SQL Server, SharePoint Server, and Azure. Don't forget T-SQL, which can also help reduce the time to configure and maintain your disaster-recovery environment.
  
## <a name="disaster-recovery-roadmap"></a>Plan de recuperación ante desastres

![Representación visual del mapa de ruta de la recuperación ante desastres de SharePoint.](media/Azure-DRroadmap.png)
  
En esta guía básica se da por supuesto que ya tiene una granja de servidores de SharePoint Server 2013 implementada en producción.
  
**Tabla: Guía básica de recuperación ante desastres**

|**Fase**|**Descripción**|
|:-----|:-----|
|Fase 1  <br/> |Diseñar el entorno de recuperación ante desastres  <br/> |
|Fase 2  <br/> |Crear la red virtual de Azure y la conexión VPN.  <br/> |
|Fase 3  <br/> |Implementar Windows Active Directory y servicios de nombres de dominio en la red virtual de Azure  <br/> |
|Fase 4  <br/> |Implementar la granja de servidores de recuperación de SharePoint en Azure.  <br/> |
|Fase 5  <br/> |Configurar DFSR entre granjas.  <br/> |
|Fase 6  <br/> |Configurar el trasvase de registros a la granja de servidores de recuperación.  <br/> |
|Fase 7  <br/> | Validate failover and recovery solutions. This includes the following procedures and technologies: <br/>  Detener el trasvase de registros <br/>  Restaurar las copias de seguridad <br/>  Rastrear el contenido <br/>  Recuperar servicios <br/>  Administrar los registros DNS <br/> |
   
## <a name="phase-1-design-the-disaster-recovery-environment"></a>Fase 1: Diseñar el entorno de recuperación ante desastres

Siga las instrucciones de [Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) para diseñar el entorno de recuperación ante desastres, incluida la granja de servidores de recuperación de SharePoint. Puede usar los gráficos de la [solución de recuperación ante desastres de SharePoint en un archivo de Azure](https://go.microsoft.com/fwlink/p/?LinkId=392554) Visio para iniciar el proceso de diseño. Le recomendamos que diseñe el entorno completo antes comenzar a trabajar en el entorno de Azure.
  
Además de las instrucciones proporcionadas en [Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) para el diseño de la red virtual, la conexión VPN, Active Directory y la granja de servidores de SharePoint, asegúrese de agregar un rol de recurso compartido de archivos al entorno de Azure.
  
To support log shipping in a disaster-recovery solution, a file share virtual machine is added to the subnet where the database roles reside. The file share also serves as the third node of a Node Majority for the SQL Server AlwaysOn availability group. This is the recommended configuration for a standard SharePoint farm that uses SQL Server AlwaysOn availability groups. 
  
> [!NOTE]
> It is important to review the prerequisites for a database to participate in a SQL Server AlwaysOn availability group. For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups](https://go.microsoft.com/fwlink/p/?LinkId=510870). 
  
**Ilustración: Ubicación de un servidor de archivos utilizado para una solución de recuperación ante desastres**

![Muestra una máquina virtual de recurso compartido de archivos que se agrega al mismo servicio en la nube que contiene los roles de servidor de bases de datos de SharePoint.](media/AZenv-FSforDFSRandWSFC.png)
  
In this diagram, a file share virtual machine is added to the same subnet in Azure that contains the database server roles. Do not add the file share virtual machine to an availability set with other server roles, such as the SQL Server roles.
  
If you are concerned about the high availability of the logs, consider taking a different approach by using [SQL Server backup and restore with Azure Blob Storage Service](https://go.microsoft.com/fwlink/p/?LinkId=393113). This is a new feature in Azure that saves logs directly to a blob storage URL. This solution does not include guidance about using this feature.
  
When you design the recovery farm, keep in mind that a successful disaster recovery environment accurately reflects the production farm that you want to recover. The size of the recovery farm is not the most important thing in the recovery farm's design, deployment, and testing. Farm scale varies from organization to organization based on business requirements. It might be possible to use a scaled-down farm for a short outage or until performance and capacity demands require you to scale the farm.
  
Configure the recovery farm as identically as possible to the production farm so that it meets your service level agreement (SLA) requirements and provides the functionality that you need to support your business. When you design the disaster recovery environment, also look at your change management process for your production environment. We recommend that you extend the change management process to the recovery environment by updating the recovery environment at the same interval as the production environment. As part of the change management process, we recommend maintaining a detailed inventory of your farm configuration, applications, and users. 
  
## <a name="phase-2-create-the-azure-virtual-network-and-vpn-connection"></a>Fase 2: Crear la red virtual de Azure y la conexión VPN

[Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md) shows you how to plan and deploy the virtual network in Azure and how to create the VPN connection. Follow the guidance in the topic to complete the following procedures:
  
- Planear el espacio de direcciones IP privado de la Red virtual.
    
- Planear los cambios de infraestructura de enrutamiento para la Red virtual.
    
- Planear las reglas de firewall para el tráfico hacia y desde el dispositivo VPN local.
    
- Crear la red virtual entre entornos locales en Azure.
    
- Configurar el enrutamiento entre la red local y la Red virtual.
    
## <a name="phase-3-deploy-active-directory-and-domain-name-services-to-the-azure-virtual-network"></a>Fase 3: Implementar Active Directory y servicios de nombres de dominio en la red virtual de Azure

Esta fase abarca la implementación de Windows Server Active Directory y DNS en la Red virtual en un escenario híbrido, como se describe en [Arquitecturas de Microsoft Azure para SharePoint 2013](microsoft-azure-architectures-for-sharepoint-2013.md) y se muestra en esta imagen.
  
**Ilustración: Configuración de dominio híbrido de Active Directory**

![Dos máquinas virtuales implementadas en la red virtual de Azure y la subred de la granja de servidores de SharePoint son controladores de dominio de réplica y servidores DNS.](media/AZarch-HyADdomainConfig.png)
  
In the illustration, two virtual machines are deployed to the same subnet. These virtual machines are each hosting two roles: Active Directory and DNS.
  
Before deploying Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These guidelines help you determine whether you need a different architecture or different configuration settings for your solution.
  
Para obtener instrucciones detalladas sobre cómo configurar un controlador de dominio en Azure, consulte [Instalación de un controlador de dominio réplica de Active Directory en Redes virtuales de Azure](https://go.microsoft.com/fwlink/p/?LinkId=392687).
  
Before this phase, you didn't deploy virtual machines to the Virtual Network. The virtual machines for hosting Active Directory and DNS are likely not the largest virtual machines you need for the solution. Before you deploy these virtual machines, first create the largest virtual machine that you plan to use in your Virtual Network. This helps ensure that your solution lands on a tag in Azure that allows the largest size you need. You do not need to configure this virtual machine at this time. Simply create it, and set it aside. If you do not do this, you might run into a limitation when you try to create larger virtual machines later, which was an issue at the time this article was written. 
  
## <a name="phase-4-deploy-the-sharepoint-recovery-farm-in-azure"></a>Fase 4: Implementar la granja de servidores de recuperación de SharePoint en Azure

Deploy the SharePoint farm in your Virtual Network according to your design plans. It might be helpful to review [Planning for SharePoint 2013 on Azure Infrastructure Services](https://go.microsoft.com/fwlink/p/?LinkId=400984) before you deploy SharePoint roles in Azure.
  
Tenga en cuenta estas prácticas que hemos aprendido al crear nuestro entorno de prueba de concepto:
  
- Cree las máquinas virtuales mediante el portal de Azure o PowerShell.
    
- Azure and Hyper-V do not support dynamic memory. Be sure this is factored into your performance and capacity plans.
    
- Restart virtual machines through the Azure interface, not from the virtual machine logon itself. Using the Azure interface works better and is more predictable.
    
- If you want to shut down a virtual machine to save costs, use the Azure interface. If you shut down from the virtual machine logon, charges continue to accrue.
    
- Use una convención de nomenclatura para las máquinas virtuales.
    
- Preste atención a la ubicación del centro de datos en la que se van a implementar las máquinas virtuales.
    
- No se admite la característica de ajuste a escala automático de Azure para los roles de SharePoint.
    
- No configure los elementos de la granja de servidores que se vayan a restaurar, como las colecciones de sitios. 
    
## <a name="phase-5-set-up-dfsr-between-the-farms"></a>Fase 5: Configurar DFSR entre las granjas de servidores

To set up file replication by using DFSR, use the DNS Management snap-in. However, before the DFSR setup, log on to your on-premises file server and Azure file server and enable the service in Windows.
  
En el panel del administrador de servidores, siga estos pasos:
  
- Configure el servidor local.
    
- Inicie el **Asistente para agregar roles y características**.
    
- Abra el nodo **Servicios de archivos y almacenamiento**.
    
- Seleccione **Espacios de nombres DFS** y **Replicación DFS**.
    
- Haga clic en **Siguiente** para finalizar los pasos del asistente.
    
En esta tabla se proporcionan vínculos a entradas de blog y artículos de referencia de DFSR.
  
**Tabla: Artículos de referencia de DFSR**

|**Title**|**Descripción**|
|:-----|:-----|
|[Replicación](https://go.microsoft.com/fwlink/p/?LinkId=392732) <br/> |Tema de TechNet sobre administración de DFS con vínculos para la replicación  <br/> |
|[Replicación DFS: Guía de supervivencia](https://go.microsoft.com/fwlink/p/?LinkId=392737) <br/> |Sitio wiki con vínculos a información sobre DFS  <br/> |
|[Replicación DFS: Preguntas más frecuentes](https://go.microsoft.com/fwlink/p/?LinkId=392738) <br/> |Tema de TechNet sobre replicación DFS  <br/> |
|[Blog de Jose Barreto](https://go.microsoft.com/fwlink/p/?LinkId=392739) <br/> |Blog escrito por un administrador del programa principal del equipo de Servidor de archivos de Microsoft  <br/> |
|[Blog del equipo de Almacenamiento de Microsoft: File Cabinet](https://go.microsoft.com/fwlink/p/?LinkId=392740) <br/> |Blog sobre los servicios de archivo y las características de almacenamiento en Windows Server  <br/> |
   
## <a name="phase-6-set-up-log-shipping-to-the-recovery-farm"></a>Fase 6: Configurar el trasvase de registros a la granja de servidores de recuperación

Log shipping is the critical component for setting up disaster recovery in this environment. You can use log shipping to automatically send transaction log files for databases from a primary database server instance to a secondary database server instance. To set up log shipping, see [Configure log shipping in SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-log-shipping). 
  
> [!IMPORTANT]
> Log shipping support in SharePoint Server is limited to certain databases. For more information, see [Supported high availability and disaster recovery options for SharePoint databases (SharePoint 2013)](https://go.microsoft.com/fwlink/p/?LinkId=393121). 
  
## <a name="phase-7-validate-failover-and-recovery"></a>Fase 7: Validar la conmutación por error y la recuperación

The goal of this final phase is to verify that the disaster recovery solution works as planned. To do this, create a failover event that shuts down the production farm and starts up the recovery farm as a replacement. You can start a failover scenario manually or by using scripts.
  
The first step is to stop incoming user requests for farm services or content. You can do this by disabling DNS entries or by shutting down the front-end web servers. After the farm is "down," you can fail over to the recovery farm.
  
### <a name="stop-log-shipping"></a>Detener el trasvase de registros

You must stop log shipping before farm recovery. Stop log shipping on the secondary server in Azure first, and then stop it on the primary server on-premises. Use the following script to stop log shipping on the secondary server first and then on the primary server. The database names in the script might be different, depending on your environment.
  
```
-- This script removes log shipping from the server.
-- Commands must be executed on the secondary server first and then on the primary server.

SET NOCOUNT ON
DECLARE  @PriDB nvarchar(max)
,@SecDB nvarchar(250)
,@PriSrv nvarchar(250)
,@SecSrv nvarchar(250)

Set @PriDB= ''
SET @PriDB = UPPER(@PriDB)
SET @PriDB = REPLACE(@PriDB, ' ', '')
SET @PriDB = '''' + REPLACE(@PriDB, ',', ''', ''') + ''''

Set @SecDB = @PriDB

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_secondary '' + '''''''' + prm.Primary_Database + '''''', '''''' + sec.Secondary_Server + '''''', '''''' + sec.Secondary_database + ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_primary_database '' + '''''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

Exec ( 'Select  ''exec master..sp_delete_log_shipping_secondary_primary '' + '''''''' + prm.primary_server + '''''', '''''' + prm.primary_database +  ''''''''   
from msdb.dbo.log_shipping_monitor_primary prm INNER JOIN msdb.dbo.log_shipping_primary_secondaries sec  ON  prm.primary_database=sec.secondary_database
where prm.primary_database in ( ' + @PriDB + ' )')

```

### <a name="restore-the-backups"></a>Restaurar las copias de seguridad

Backups must be restored in the order in which they were created. Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions (that is, by using  `WITH NORECOVERY`):
  
- The full database backup and the last differential backup - Restore these backups, if any exist, taken before the particular transaction log backup. Before the most recent full or differential database backup was created, the database was using the full recovery model or bulk-logged recovery model.
    
- All transaction log backups - Restore any transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup. Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.
    
To recover the content database on the secondary server so that the sites render, remove all database connections before recovery. To restore the database, run the following SQL statement.
  
```
restore database WSS_Content with recovery

```

> [!IMPORTANT]
> When you use T-SQL explicitly, specify either **WITH NORECOVERY** or **WITH RECOVERY** in every RESTORE statement to eliminate ambiguity—this is very important when writing scripts. After the full and differential backups are restored, the transaction logs can be restored in SQL Server Management Studio. Also, because log shipping is already stopped, the content database is in a standby state, so you must change the state to full access.
  
In SQL Server Management Studio, right-click the **WSS_Content** database, point to **Tasks** > **Restore**, and then click **Transaction Log** (if you have not restored the full backup, this is not available). For more information, see[Restore a Transaction Log Backup (SQL Server)](https://go.microsoft.com/fwlink/p/?LinkId=392778).
  
### <a name="crawl-the-content-source"></a>Rastrear el origen de contenido

You must start a full crawl for each content source to restore the Search Service. Note that you lose some analytics information from the on-premises farm, such as search recommendations. Before you start the full crawls, use the Windows PowerShell cmdlet **Restore-SPEnterpriseSearchServiceApplication** and specify the log-shipped and replicated Search Administration database, **Search_Service__DB_<GUID>**. This cmdlet gives the search configuration, schema, managed properties, rules, and sources and creates a default set of the other components.
  
Para iniciar un rastreo completo, siga estos pasos:
  
1. En Administración central de SharePoint 2013, vaya a **Administración de aplicaciones** > **Aplicaciones de servicio** > **Administrar aplicaciones de servicio** y, a continuación, haga clic en la aplicación de servicio Búsqueda que quiera rastrear.
    
2. En la página **Administración de búsquedas**, haga clic en **Orígenes de contenido**, señale el origen de contenido que quiera, haga clic en la flecha y después en **Iniciar rastreo completo**.
    
### <a name="recover-farm-services"></a>Recuperar servicios de la granja de servidores

En esta tabla se muestra cómo recuperar servicios que tienen bases de datos con trasvase de registros, servicios que tienen bases de datos pero no se recomienda que se restauren con el trasvase de registros y servicios que no tienen bases de datos.
  
> [!IMPORTANT]
> Si restaura una base de datos de SharePoint local en el entorno de Azure no recuperará los servicios de SharePoint que no haya instalado manualmente en Azure. 
  
**Tabla: Referencia de la base de datos de aplicación de servicio**

|**Restaurar estos servicios desde bases de datos con trasvase de registros:**|**Estos servicios tienen bases de datos, pero le recomendamos que inicie estos servicios sin restaurar las bases de datos:**|**Estos servicios no almacenan datos en bases de datos; inicie estos servicios después de la conmutación por error:**|
|:-----|:-----|:-----|
| Servicio de traducción automática <br/>  Servicio de metadatos administrados <br/>  Servicio de almacenamiento seguro <br/>  User Profile. (Only the Profile and Social Tagging databases are supported. The Synchronization database is not supported.) <br/>  Servicio de configuración de suscripción de Microsoft SharePoint Foundation <br/> | Recolección de datos de uso y estado <br/>  Servicio de estado <br/>  Automatización de Word <br/> | Servicios de Excel <br/>  PerformancePoint Services <br/>  Conversión de PowerPoint <br/>  Servicio de gráficos de Visio <br/>  Administración del trabajo <br/> |
   
En este ejemplo se muestra cómo restaurar el servicio de metadatos administrados desde una base de datos.
  
This uses the existing Managed_Metadata_DB database. This database is log shipped, but there is no active service application on the secondary farm, so it needs to be connected after the service application is in place.
  
En primer lugar, use  `New-SPMetadataServiceApplication` y especifique el modificador `DatabaseName` con el nombre de la base de datos restaurada.
  
Después, configure la nueva aplicación de servicio de metadatos administrados en el servidor secundario, como se muestra aquí:
  
- Nombre: Servicio de metadatos administrados
    
- Servidor de bases de datos: el nombre de la base de datos del registro de transacciones que se ha trasvasado
    
- Nombre de la base de datosManaged_Metadata_DB
    
- Grupo de aplicaciones: aplicaciones de servicio de SharePoint 
    
### <a name="manage-dns-records"></a>Administrar los registros DNS

Debe crear manualmente los registros DNS para que apunten a la granja de servidores de SharePoint.
  
In most cases where you have multiple front-end web servers, it makes sense to take advantage of the Network Load Balancing feature in Windows Server 2012 or a hardware load balancer to distribute requests among the web-front-end servers in your farm. Network load balancing can also help reduce risk by distributing requests to the other servers if one of your web-front-end servers fails. 
  
Typically, when you set up network load balancing, your cluster is assigned a single IP address. You then create a DNS host record in the DNS provider for your network that points to the cluster. (For this project, we put a DNS server in Azure for resiliency in case of an on-premises datacenter failure.) For instance, you can create a DNS record, in DNS Manager in Active Directory, for example, called  `https://sharepoint.contoso.com`, that points to the IP address for your load-balanced cluster.
  
Para el acceso externo a la granja de servidores de SharePoint, puede crear un registro de host en un servidor DNS externo con la misma dirección URL que usan los clientes en la intranet (por ejemplo, `https://sharepoint.contoso.com` ) que apunta a una dirección IP externa en el firewall. (Un procedimiento recomendado es configurar un DNS dividido para que el servidor DNS interno tenga autoridad para `contoso.com` y enrute las solicitudes directamente al clúster de la granja de servidores de SharePoint, en lugar de enrutar las solicitudes DNS al servidor DNS externo). A continuación, puede asignar la dirección IP externa a la dirección IP interna del clúster local para que los clientes encuentren los recursos que buscan.
  
A partir de aquí, puede que se encuentre con un par de escenarios de recuperación ante desastres diferentes:
  
 **Example scenario: The on-premises SharePoint farm is unavailable because of hardware failure in the on-premises SharePoint farm.** In this case, after you have completed the steps for failover to the Azure SharePoint farm, you can configure network load balancing on the recovery SharePoint farm's web-front-end servers, the same way you did with the on-premises farm. You can then redirect the host record in your internal DNS provider to point to the recovery farm's cluster IP address. Note that it can take some time before cached DNS records on clients are refreshed and point to the recovery farm.
  
 **Example scenario: The on-premises datacenter is lost completely.** This scenario might occur due to a natural disaster, such as a fire or flood. In this case, for an enterprise, you would likely have a secondary datacenter hosted in another region as well as your Azure subnet that has its own directory services and DNS. As in the previous disaster scenario, you can redirect your internal and external DNS records to point to the Azure SharePoint farm. Again, take note that DNS-record propagation can take some time.
  
Si usa colecciones de sitios con nombre de host, como se recomienda en [arquitectura e implementación de colecciones de sitios con nombre de host (SharePoint 2013)](https://docs.microsoft.com/SharePoint/administration/host-named-site-collection-architecture-and-deployment), puede tener varias colecciones de sitios hospedadas por la misma aplicación web en su granja de servidores de SharePoint, con nombres DNS únicos (por ejemplo, `https://sales.contoso.com` y `https://marketing.contoso.com` ). En este caso, puede crear registros DNS para cada colección de sitios que señalen la dirección IP del clúster. En cuanto una solicitud llega a los servidores front-end web de SharePoint, estos se encargan de enrutar cada solicitud a la colección de sitios adecuada.
  
## <a name="microsoft-proof-of-concept-environment"></a>Entorno de prueba de concepto de Microsoft

We designed and tested a proof-of-concept environment for this solution. The design goal for our test environment was to deploy and recover a SharePoint farm that we might find in a customer environment. We made several assumptions, but we knew that the farm needed to provide all of the out-of-the-box functionality without any customizations. The topology was designed for high availability by using best practice guidance from the field and product group.
  
En esta tabla se describen las máquinas virtuales de Hyper-V que hemos creado y configurado para el entorno de prueba local.
  
**Tabla: máquinas virtuales para prueba local**

|**Nombre del servidor**|**Rol**|**Configuración**|
|:-----|:-----|:-----|
|DC1  <br/> |Controlador de dominio con Active Directory.  <br/> |Dos procesadores  <br/> De 512 MB a 4 GB de RAM  <br/> 1 disco duro de 127 GB  <br/> |
|RRAS  <br/> |Servidor configurado con el rol servicio de enrutamiento y acceso remoto (RRAS).  <br/> |Dos procesadores  <br/> De 2 a 8 GB de RAM  <br/> 1 disco duro de 127 GB  <br/> |
|FS1  <br/> |Servidor de archivos con recursos compartidos para copias de seguridad y un extremo para DFSR.  <br/> |Cuatro procesadores  <br/> De 2 a 12 GB de RAM  <br/> 1 disco duro de 127 GB  <br/> Disco duro (SAN) 1 x 1 TB  <br/> Disco duro 1 x 750 GB  <br/> |
|SP-WFE1, SP-WFE2  <br/> |Servidor front-end web  <br/> |Cuatro procesadores  <br/> 16 GB de RAM  <br/> |
|SP-APP1, SP-APP2, SP-APP3  <br/> |Servidores de aplicaciones.  <br/> |Cuatro procesadores  <br/> De 2 a 16 GB de RAM  <br/> |
|SP-SQL-HA1, SP-SQL-HA2  <br/> |Database servers, configured with SQL Server 2012 AlwaysOn availability groups to provide high availability. This configuration uses SP-SQL-HA1 and SP-SQL-HA2 as the primary and secondary replicas.  <br/> |Cuatro procesadores  <br/> De 2 a 16 GB de RAM  <br/> |
   
En la siguiente tabla se describe la configuración de las unidades de las máquinas virtuales de Hyper-V que hemos creado y configurado para el servidor front-end web y el servidor de aplicaciones, en el entorno de prueba local.
  
**Tabla: Requisitos de las unidades de las máquinas virtuales para el servidor front-end web y el servidor de aplicaciones en la prueba local**

|**Letra de unidad**|**Tamaño**|**Nombre de directorio**|**Ruta de acceso**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Unidad del sistema  <br/> |<DriveLetter>:\\Archivos de programa\\Microsoft SQL Server\\  <br/> |
|E  <br/> |80  <br/> |Unidad de registro (40 GB)  <br/> |<DriveLetter>:\\Archivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |80  <br/> |Página (36 GB)  <br/> |<DriveLetter>:\\Archivos de programa\\Microsoft SQL Server\\MSSQL\\DATA  <br/> |
   
The following table describes drive configurations for the Hyper-V virtual machines created and configured to serve as the on-premises database servers. On the **Database Engine Configuration** page, access the **Data Directories** tab to set and confirm the settings shown in the following table.
  
**Tabla: Requisitos de las unidades de las máquinas virtuales para el servidor de bases de datos en la prueba local**

|**Letra de unidad**|**Tamaño**|**Nombre de directorio**|**Ruta de acceso**|
|:-----|:-----|:-----|:-----|
|C  <br/> |80  <br/> |Directorio raíz de datos  <br/> |<DriveLetter>:\\Archivos de programa\\Microsoft SQL Server\\  <br/> |
|E  <br/> |500  <br/> |Directorio de base de datos de usuario  <br/> |<DriveLetter>:\\Archivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|F  <br/> |500  <br/> |Directorio de registro de base de datos de usuario  <br/> |<DriveLetter>:\\Archivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|G  <br/> |500  <br/> |Directorio de base de datos temporal  <br/> |<DriveLetter>:\\Archivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
|H  <br/> |500  <br/> |Directorio de registro de base de datos temporal  <br/> |<DriveLetter>:\\Archivos de programa\\Microsoft SQL Server\\MSSQL10_50.MSSQLSERVER\\MSSQL\\DATA  <br/> |
   
### <a name="setting-up-the-test-environment"></a>Configuración del entorno de prueba

During the different deployment phases, the test team typically worked on the on-premises architecture first and then on the corresponding Azure environment. This reflects the general real-world cases where in-house production farms are already running. What is even more important is that you should know the current production workload, capacity, and typical performance. In addition to building a disaster recovery model that can meet business requirements, you should size the recovery farm servers to deliver a minimum level of service. In a cold or warm standby environment, a recovery farm is typically smaller than a production farm. After the recovery farm is stable and in production, the farm can be scaled up and out to meet workload requirements.
  
Implementamos nuestro entorno de prueba en tres fases:
  
- Configurar la infraestructura híbrida
    
- Aprovisionar los servidores
    
- Implementar las granjas de servidores de SharePoint
    
#### <a name="set-up-the-hybrid-infrastructure"></a>Configurar la infraestructura híbrida

This phase involved setting up a domain environment for the on-premises farm and for the recovery farm in Azure. In addition to the normal tasks associated with configuring Active Directory, the test team implemented a routing solution and a VPN connection between the two environments.
  
#### <a name="provision-the-servers"></a>Aprovisionar los servidores

In addition to the farm servers, it was necessary to provision servers for the domain controllers and configure a server to handle RRAS as well as the site-to-site VPN. Two file servers were provisioned for the DFSR service, and several client computers were provisioned for testers.
  
#### <a name="deploy-the-sharepoint-farms"></a>Implementar las granjas de servidores de SharePoint

The SharePoint farms were deployed in two stages in order to simplify environment stabilization and troubleshooting, if required. During the first stage, each farm was deployed on the minimum number of servers for each tier of the topology to support the required functionality.
  
We created the database servers with SQL Server installed before creating the SharePoint 2013 servers. Because this was a new deployment, we created the availability groups before deploying SharePoint. We created three groups based on MCS best practice guidance. 
  
> [!NOTE]
> Create placeholder databases so that you can create availability groups before the SharePoint installation. For more information, see [Configure SQL Server 2012 AlwaysOn Availability Groups for SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=517626)
  
Creamos la granja de servidores y unimos servidores adicionales en este orden:
  
- Aprovisionar SP-SQL-HA1 y SP-SQL-HA2.
    
- Configurar AlwaysOn y crear los tres grupos de disponibilidad para la granja de servidores. 
    
- Aprovisionar SP-APP1 para hospedar Administración central.
    
- Aprovisionar WFE1 SP y WFE2 SP para hospedar la caché distribuida. 
    
Usamos el parámetro  _skipRegisterAsDistributedCachehost_ cuando ejecutamos **psconfig.exe** en la línea de comandos. Para más información, vea [Planear las fuentes y el servicio de caché distribuida en SharePoint Server 2013](https://docs.microsoft.com/sharepoint/administration/plan-for-feeds-and-the-distributed-cache-service). 
  
Repetimos estos pasos en el entorno de recuperación:
  
- Aprovisionar AZ-SQL-HA1 y AZ-SQL-HA2.
    
- Configurar AlwaysOn y crear los tres grupos de disponibilidad para la granja de servidores.
    
- Aprovisionar AZ-APP1 para hospedar Administración central.
    
- Aprovisionar WFE1 AZ y AZ-WFE2 para hospedar la caché distribuida.
    
After we configured the distributed cache and added test users and test content, we started stage two of the deployment. This required scaling out the tiers and configuring the farm servers to support the high-availability topology described in the farm architecture.
  
En esta tabla se describen las máquinas virtuales, las subredes y los conjuntos de disponibilidad que configuramos para nuestra granja de servidores de recuperación.
  
**Tabla: Infraestructura de la granja de servidores de recuperación**

|**Nombre del servidor**|**Rol**|**Configuración**|**Subred**|**Conjunto de disponibilidad**|
|:-----|:-----|:-----|:-----|:-----|
|spDRAD  <br/> |Controlador de dominio con Active Directory  <br/> |Dos procesadores  <br/> De 512 MB a 4 GB de RAM  <br/> 1 disco duro de 127 GB  <br/> |sp-ADservers  <br/> ||
|AZ-SP-FS  <br/> |Servidor de archivos con recursos compartidos para copias de seguridad y un extremo para DFSR  <br/> | Configuración de A5: <br/>  Dos procesadores <br/>  14 GB de RAM <br/>  1 disco duro de 127 GB <br/>  1 disco duro de 135 GB <br/>  1 disco duro de 127 GB <br/>  1 disco duro de 150 GB <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
|AZ-WFE1, AZ -WFE2  <br/> |Servidores front-end web  <br/> | Configuración de A5: <br/>  Dos procesadores <br/>  14 GB de RAM <br/>  1 disco duro de 127 GB <br/> |sp-webservers  <br/> |WFE_SET  <br/> |
|AZ -APP1, AZ -APP2, AZ -APP3  <br/> |Servidores de aplicaciones  <br/> | Configuración de A5: <br/>  Dos procesadores <br/>  14 GB de RAM <br/>  1 disco duro de 127 GB <br/> |sp-applicationservers  <br/> |APP_SET  <br/> |
|AZ -SQL-HA1, AZ -SQL-HA2  <br/> |Servidores de base de datos y réplicas principales y secundarias para los grupos de disponibilidad AlwaysOn  <br/> | Configuración de A5: <br/>  Dos procesadores <br/>  14 GB de RAM <br/> |sp-databaseservers  <br/> |DATA_SET  <br/> |
   
### <a name="operations"></a>Operaciones

En cuanto el equipo de pruebas estabilizó los entornos de la granja de servidores y finalizó las pruebas funcionales, empezó a realizar estas tareas de operaciones, necesarias para configurar el entorno de recuperación local:
  
- Configurar copias de seguridad completas y diferenciales
    
- Configurar DFSR en los servidores de archivos que transfieren los registros de transacciones entre el entorno local y el entorno de Azure.
    
- Configurar el trasvase de registros en el servidor de bases de datos principal.
    
- Stabilize, validate, and troubleshoot log shipping, as required. This included identifying and documenting any behavior that might cause issues, such as network latency, which would cause log shipping or DFSR file synchronization failures.
    
### <a name="databases"></a>Bases de datos

Nuestras pruebas de conmutación por error incluyeron estas bases de datos: 
  
- WSS_Content
    
- ManagedMetadata
    
- Base de datos de perfil
    
- Base de datos de sincronización
    
- Base de datos social
    
- Concentrador de tipo de contenido (una base de datos para un concentrador de sindicación de tipo de contenido dedicado)
    
## <a name="troubleshooting-tips"></a>Sugerencias para solucionar problemas

En esta sección se explican los problemas producidos durante las pruebas y sus soluciones. 
  
### <a name="using-the-term-store-management-tool-caused-the-error-the-managed-metadata-store-or-connection-is-currently-not-available"></a>Al usar la Herramienta de administración del almacén de términos se produce un error que indica que la conexión o el almacén de metadatos administrado no están disponibles"

Asegúrese de que la cuenta del grupo de aplicaciones usada por la aplicación web tiene acceso de lectura al permiso del almacén de términos.
  
### <a name="custom-term-sets-are-not-available-in-the-site-collection"></a>Los conjuntos de términos personalizados no están disponibles en la colección de sitios

Check for a missing service application association between your content site collection and your content type hub. In addition, under the **Managed Metadata - <site collection name> Connection** properties screen, make sure this option is enabled: **This service application is the default storage location for column specific term sets.**
  
### <a name="the-get-adforest-windows-powershell-command-generates-the-error-the-term-get-adforest-is-not-recognized-as-the-name-of-a-cmdlet-function-script-file-or-operable-program"></a>El comando Get-ADForest de Windows PowerShell genera el error: "El término 'Get-ADForest' no se reconoce como nombre de un cmdlet, función, archivo de script o programa ejecutable"

When setting up user profiles, you need the Active Directory forest name. In the Add Roles and Features Wizard, ensure that you have enabled the Active Directory Module for Windows PowerShell (under the **Remote Server Administration Tools>Role Administration Tools>AD DS and AD LDS Tools** section). In addition, run the following commands before using **Get-ADForest** to help ensure that your software dependencies are loaded.
  
```
Import-module servermanager
Import-module activedirectory

```

### <a name="availability-group-creation-fails-at-starting-the-alwayson_health-xevent-session-on-server-name"></a>Se produce un error en la creación del grupo de disponibilidad al iniciar la sesión de XEvent 'AlwaysOn_health' en '<server name>'

Asegúrese de que los dos nodos del clúster de conmutación por error tienen el estado "Arriba" y no "En pausa" o "Detenido". 
  
### <a name="sql-server-log-shipping-job-fails-with-access-denied-error-trying-to-connect-to-the-file-share"></a>El trabajo de trasvase de registros de SQL Server genera un error de acceso denegado al intentar conectar con el recurso compartido de archivos

Asegúrese de que el Agente SQL Server se ejecuta con credenciales de red, en lugar de las credenciales predeterminadas.
  
### <a name="sql-server-log-shipping-job-indicates-success-but-no-files-are-copied"></a>El trabajo de trasvase de registros de SQL Server indica que se ha realizado correctamente, pero no se ha copiado ningún archivo

This happens because the default backup preference for an availability group is **Prefer Secondary**. Ensure that you run the log shipping job from the secondary server for the availability group instead of the primary; otherwise, the job will fail silently. 
  
### <a name="managed-metadata-service-or-other-sharepoint-service-fails-to-start-automatically-after-installation"></a>El servicio de metadatos administrados (u otro servicio de SharePoint) no se puede iniciar automáticamente después de la instalación

Los servicios pueden tardar varios minutos en iniciarse, en función del rendimiento y la carga actual del servidor de SharePoint. Haga clic manualmente en **iniciar** para el servicio y proporcione la hora adecuada para el inicio mientras que, de vez en cuando, actualice la pantalla de servicios en el servidor para supervisar su estado. En caso de que el servicio permanezca detenido, habilite el registro de diagnóstico de SharePoint, intente volver a iniciar el servicio y compruebe si hay errores en el registro. Para obtener más información, vea [configurar el registro de diagnóstico en SharePoint 2013](https://docs.microsoft.com/sharepoint/administration/configure-diagnostic-logging)
  
### <a name="after-changing-dns-to-the-azure-failover-environment-client-browsers-continue-to-use-the-old-ip-address-for-the-sharepoint-site"></a>Después de cambiar DNS al entorno de conmutación por error de Azure, los exploradores de los clientes siguen usando la antigua dirección IP para el sitio de SharePoint

Your DNS change might not be visible to all clients immediately. On a test client, perform the following command from an elevated command prompt and attempt to access the site again.
  
```
Ipconfig /flushdns
```

## <a name="additional-resources"></a>Recursos adicionales

[Compatibilidad de alta disponibilidad y opciones de recuperación ante desastres para bases de datos de SharePoint](https://docs.microsoft.com/sharepoint/administration/supported-high-availability-and-disaster-recovery-options-for-sharepoint-databas)
  
[Configuración de grupos de disponibilidad AlwaysOn de SQL Server 2012 para SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=393122)
  
## <a name="see-also"></a>Consulta también

[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.yml)



