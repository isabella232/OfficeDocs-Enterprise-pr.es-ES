---
title: "Mover datos de transacción históricos a la nube"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 3e9c405a-415b-4584-aa7e-f2489299c457
description: "Resumen: Cómo Contoso ha implementado SQL Server Stretch Database para reducir sus necesidades de almacenamiento de datos locales y los costos de ejecución diarios."
ms.openlocfilehash: ef21b00f54fcc6efda2e83cb5952a99c7b8c8f28
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="moving-historical-transaction-data-to-the-cloud"></a><span data-ttu-id="ff513-103">Mover datos de transacción históricos a la nube</span><span class="sxs-lookup"><span data-stu-id="ff513-103">Moving historical transaction data to the cloud</span></span>

 <span data-ttu-id="ff513-104">**Resumen:** Cómo Contoso ha implementado SQL Server Stretch Database para reducir sus necesidades de almacenamiento de datos locales y los costos de ejecución diarios.</span><span class="sxs-lookup"><span data-stu-id="ff513-104">**Summary:** How Contoso implemented SQL Server stretch database to reduce its on-premises data storage needs and daily running costs.</span></span>
  
<span data-ttu-id="ff513-p101">El sistema de almacenamiento empresarial de Contoso almacena una gran cantidad de datos de transacción históricos para adaptarse a los requisitos reglamentarios y para las investigaciones de marketing y análisis de BI de tendencias de gasto. Contoso también necesita restaurar los datos archivados de una cinta magnética; un proceso muy largo. El hardware en el sistema de almacenamiento empresarial de Contoso estaba llegando al final de su ciclo de vida y reemplazarlo resultaría muy costoso.</span><span class="sxs-lookup"><span data-stu-id="ff513-p101">Contoso's enterprise storage system stores a large amount of historical transaction data for adherence with regulatory requirements and for marketing research and BI analysis of spending trends. Contoso also needs to restore archived data from magnetic tape, a time-intensive process. The hardware in Contoso's enterprise storage system was nearing its end of life and replacing it would be very expensive.</span></span> 
  
<span data-ttu-id="ff513-p102">Como parte de su necesidad empresarial de reducir verticalmente sus centros de datos locales, Contoso ha decidido actualizar a SQL Server 2016 por la característica híbrida de Stretch Database y su perfecta integración con Azure. Stretch Database permite que Contoso mueva los datos inactivos en sus tablas desde el entorno local al almacenamiento en la nube, lo que libera espacio en el disco local y reduce el mantenimiento. Los datos inactivos y activos se encuentran en las mismas tablas y siempre están disponibles para las aplicaciones, los usuarios y el mantenimiento, como copias de seguridad y restauraciones. En la figura 1 se muestra Stretch Database.</span><span class="sxs-lookup"><span data-stu-id="ff513-p102">As part of its business need to scale down its on-premises datacenters, Contoso chose to upgrade to SQL Server 2016 because of the Stretch Database hybrid feature and its seamless integration with Azure. Stretch Database allows Contoso to move the cold data in its tables from on-premises to cloud storage, freeing up local disk space and reducing maintenance. Both hot and cold data are in the same tables and are always available to applications and their users and for maintenance, such as backups and restores. Figure 1 shows Stretch Database.</span></span>
  
<span data-ttu-id="ff513-112">**Figura 1: SQL Server Stretch Database**</span><span class="sxs-lookup"><span data-stu-id="ff513-112">**Figure 1: SQL Server Stretch Database**</span></span>

![SQL Server Stretch Database como solución de datos híbrido](images/Contoso_Poster/StretchDB01.png)
  
<span data-ttu-id="ff513-114">En la figura 1 se muestra cómo un cliente de SQL envía consultas de T-SQL a un servidor que ejecuta SQL Server 2016, que las reenvía a Azure SQL Stretch Database en PaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="ff513-114">Figure 1 shows how a SQL client sends T-SQL queries to a server running SQL Server 2016, which forwards them to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="ff513-115">Para obtener más información, consulte [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span><span class="sxs-lookup"><span data-stu-id="ff513-115">For more information, see [Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx).</span></span>
  
<span data-ttu-id="ff513-116">Contoso ha usado estos pasos para mover sus datos históricos a la nube:</span><span class="sxs-lookup"><span data-stu-id="ff513-116">Contoso used these steps to move their historical data to the cloud:</span></span>
  
1. <span data-ttu-id="ff513-117">Analizar bases de datos</span><span class="sxs-lookup"><span data-stu-id="ff513-117">Analyze databases</span></span>
    
    <span data-ttu-id="ff513-p103">Se ha realizado un análisis de las tablas de las bases de datos que pretenden moverse a la nube y se han solucionado los problemas. El nuevo Stretch Database Advisor les proporciona información general completa de lo que pueden esperar de todas las características de SQL Server 2016, incluidas las tablas que tienen datos inactivos que podrían extenderse.</span><span class="sxs-lookup"><span data-stu-id="ff513-p103">Performed an analysis of the tables in the databases that they intended to move to the cloud and fixed any issues. The new Stretch Database Advisor gave them a full overview of what they can expect from all features in SQL Server 2016, including which tables have cold data that could be stretched.</span></span>
    
2. <span data-ttu-id="ff513-120">Actualización</span><span class="sxs-lookup"><span data-stu-id="ff513-120">Upgrade</span></span>
    
    <span data-ttu-id="ff513-121">Se han actualizado los servidores SQL Server existentes en el centro de datos de la sede central de París a SQL Server 2016.</span><span class="sxs-lookup"><span data-stu-id="ff513-121">Updated existing SQL servers in the Paris headquarters datacenter to SQL Server 2016.</span></span>
    
3. <span data-ttu-id="ff513-122">Migrar datos inactivos a la nube</span><span class="sxs-lookup"><span data-stu-id="ff513-122">Migrate cold data to the cloud</span></span>
    
    <span data-ttu-id="ff513-p104">Con SQL Management Studio han identificado las bases de datos que se van a extender y las tablas que se van a migrar a instancias de Stretch Database en Azure. Con el paso del tiempo y en segundo plano, SQL Server 2016 ha movido los datos históricos a las bases de datos de Stretch Database en Azure.</span><span class="sxs-lookup"><span data-stu-id="ff513-p104">Using SQL Management Studio, they identified the databases to stretch and the tables to migrate to instances of Stretch Database in Azure. Over time and in the background, SQL Server 2016 moved the historical data to stretch databases in Azure.</span></span>
    
<span data-ttu-id="ff513-125">Aquí se muestra la configuración resultante para un servidor que ejecuta SQL Server 2016 en la sede central de París.</span><span class="sxs-lookup"><span data-stu-id="ff513-125">Here is the resulting configuration for one server running SQL Server 2016 in the Paris headquarters.</span></span>
  
<span data-ttu-id="ff513-126">**Figura 2: Usar Stretch Database en un servidor del centro de datos de Contoso**</span><span class="sxs-lookup"><span data-stu-id="ff513-126">**Figure 2: Using Stretch Database for a server in Contoso's datacenter**</span></span>

![SQL Server Stretch Database de configuración de Contoso para un solo equipo que ejecuta SQL Server](images/Contoso_Poster/StretchDB02.png)

  
<span data-ttu-id="ff513-128">En la figura 2 se muestra cómo las consultas de usuario en un servidor de aplicaciones del centro de datos de Contoso se convierten en consultas SQL que se pasan a Azure SQL Stretch Database en PaaS de Azure.</span><span class="sxs-lookup"><span data-stu-id="ff513-128">Figure 2 shows how user queries to an application server in Contoso's datacenter become SQL queries that are passed to an Azure SQL Stretch Database in Azure PaaS.</span></span>
  
<span data-ttu-id="ff513-p105">Los usuarios tienen acceso a los datos mediante consultas y aplicaciones existentes. Las directivas de acceso siguen siendo las mismas. Además, no se necesitan copias de seguridad en cinta. El mantenimiento consiste en realizar copias de seguridad y restaurar datos activos.</span><span class="sxs-lookup"><span data-stu-id="ff513-p105">Users access the data through existing apps and queries. Access policies remain the same. Moving forward, there is no need for tape backups. Maintenance consists of backing up and restoring hot data.</span></span>
  
<span data-ttu-id="ff513-133">Después de implementar Stretch Database, Contoso:</span><span class="sxs-lookup"><span data-stu-id="ff513-133">After implementing Stretch Database, Contoso:</span></span>
  
- <span data-ttu-id="ff513-134">Ha reducido sus necesidades de almacenamiento de datos locales en un 85 %.</span><span class="sxs-lookup"><span data-stu-id="ff513-134">Reduced its on-premises data storage needs by 85%.</span></span>
    
- <span data-ttu-id="ff513-135">Ha realizado la actualización del sistema de almacenamiento empresarial y la dependencia de archivos de cinta magnética innecesarios.</span><span class="sxs-lookup"><span data-stu-id="ff513-135">Made the update of the enterprise storage system and reliance on magnetic tape archives unnecessary.</span></span>
    
- <span data-ttu-id="ff513-136">Ha reducido sus costos de ejecución diarios de manera significativa.</span><span class="sxs-lookup"><span data-stu-id="ff513-136">Reduced its daily running costs significantly.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="ff513-137">Vea también</span><span class="sxs-lookup"><span data-stu-id="ff513-137">See Also</span></span>

[<span data-ttu-id="ff513-138">Escenarios empresariales para Contoso Corporation</span><span class="sxs-lookup"><span data-stu-id="ff513-138">Enterprise scenarios for the Contoso Corporation</span></span>](enterprise-scenarios-for-the-contoso-corporation.md)
  
[<span data-ttu-id="ff513-139">Contoso en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ff513-139">Contoso in the Microsoft Cloud</span></span>](contoso-in-the-microsoft-cloud.md)
  
[<span data-ttu-id="ff513-140">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="ff513-140">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

<span data-ttu-id="ff513-141">[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)</span><span class="sxs-lookup"><span data-stu-id="ff513-141">[Stretch Database](https://msdn.microsoft.com/library/dn935011.aspx)</span></span>
  
<span data-ttu-id="ff513-142">[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de la toma de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)</span><span class="sxs-lookup"><span data-stu-id="ff513-142">[Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers](https://sway.com/FJ2xsyWtkJc2taRD)</span></span>




