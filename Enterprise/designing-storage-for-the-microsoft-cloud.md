---
title: "Diseño de almacenamiento de información para la nube de Microsoft"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Top
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: "Resumen: Comprender por qué necesita almacenamiento en nube y revise la lista de opciones de almacenamiento de nube de Microsoft y los escenarios de almacenamiento de claves."
ms.openlocfilehash: 3501f6a39498276d02fe4178f701a06dfb6a3e93
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="2c497-103">Diseño de almacenamiento de información para la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="2c497-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="2c497-104">**Resumen:** Comprender por qué necesita almacenamiento en nube y revise la lista de opciones de almacenamiento de nube de Microsoft y los escenarios de almacenamiento de claves.</span><span class="sxs-lookup"><span data-stu-id="2c497-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="2c497-105">Integración de su almacenamiento de información con servicios de nube de Microsoft proporciona acceso a una amplia gama de opciones de plataformas de nube y los servicios.</span><span class="sxs-lookup"><span data-stu-id="2c497-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="2c497-106">¿Por qué almacenamiento en nube?</span><span class="sxs-lookup"><span data-stu-id="2c497-106">Why cloud storage?</span></span>

<span data-ttu-id="2c497-107">Existen dos razones fundamentales para utilizar el almacenamiento en la nube.</span><span class="sxs-lookup"><span data-stu-id="2c497-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="2c497-108">Velocidad de salida al mercado:</span><span class="sxs-lookup"><span data-stu-id="2c497-108">Speed to market:</span></span>
    
  - <span data-ttu-id="2c497-109">Configuración más rápida para alta disponibilidad y recuperación ante desastres</span><span class="sxs-lookup"><span data-stu-id="2c497-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="2c497-110">No hay hardware de almacenamiento para comprar</span><span class="sxs-lookup"><span data-stu-id="2c497-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="2c497-111">Fontanería integrado proporcionado por las ofertas de nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="2c497-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="2c497-112">Disponible desde cualquier lugar del mundo</span><span class="sxs-lookup"><span data-stu-id="2c497-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="2c497-113">Disminuir los costos para mantener:</span><span class="sxs-lookup"><span data-stu-id="2c497-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="2c497-114">Elasticidad para escalar y bajar sus exigencias de almacenamiento de información</span><span class="sxs-lookup"><span data-stu-id="2c497-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="2c497-115">No hay hardware de almacenamiento de información para mantener o migrar</span><span class="sxs-lookup"><span data-stu-id="2c497-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="2c497-116">Microsoft es su fontanero integrado para mantener y mejorar la infraestructura</span><span class="sxs-lookup"><span data-stu-id="2c497-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="2c497-117">Mejor seguridad de almacenamiento de información en el mercado con mejoras continuas</span><span class="sxs-lookup"><span data-stu-id="2c497-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="2c497-118">Opciones de almacenamiento de nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="2c497-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="2c497-119">Para ayudarle a comprender la amplia variedad de opciones de almacenamiento de nube, utilizamos una analogía de construcción.</span><span class="sxs-lookup"><span data-stu-id="2c497-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="2c497-120">Mover en listo</span><span class="sxs-lookup"><span data-stu-id="2c497-120">Move-in ready</span></span>

<span data-ttu-id="2c497-p101">Utilice estas soluciones ya preparadas que se incluyen con servicios existentes. Utilizar inmediatamente y con una configuración mínima.</span><span class="sxs-lookup"><span data-stu-id="2c497-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="2c497-123">Office 365</span><span class="sxs-lookup"><span data-stu-id="2c497-123">Office 365</span></span>
    
- <span data-ttu-id="2c497-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="2c497-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="2c497-125">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="2c497-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="2c497-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="2c497-126">Dynamics 365</span></span>
    
- <span data-ttu-id="2c497-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="2c497-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="2c497-128">Recuperación de sitio de Azure</span><span class="sxs-lookup"><span data-stu-id="2c497-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="2c497-129">Yammer sitio compartir</span><span class="sxs-lookup"><span data-stu-id="2c497-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="2c497-130">Copia de seguridad de Azure</span><span class="sxs-lookup"><span data-stu-id="2c497-130">Azure Backup</span></span>
    
<span data-ttu-id="2c497-131">Para los detalles de cada una de estas opciones de almacenamiento en nube, consulte [mover en listo](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="2c497-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="2c497-132">Algunos ensamblados necesarios</span><span class="sxs-lookup"><span data-stu-id="2c497-132">Some assembly required</span></span>

<span data-ttu-id="2c497-133">Utilice estos servicios existentes como punto de partida para la solución de almacenamiento con una configuración adicional o de codificación para un ajuste personalizado.</span><span class="sxs-lookup"><span data-stu-id="2c497-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="2c497-134">Red de entrega de contenido de Azure</span><span class="sxs-lookup"><span data-stu-id="2c497-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="2c497-135">Servicios de Azure Media</span><span class="sxs-lookup"><span data-stu-id="2c497-135">Azure Media Services</span></span>
    
- <span data-ttu-id="2c497-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="2c497-136">HdInsight</span></span>
    
- <span data-ttu-id="2c497-137">Caché de Azure Redis</span><span class="sxs-lookup"><span data-stu-id="2c497-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="2c497-138">Base de datos SQL de Azure</span><span class="sxs-lookup"><span data-stu-id="2c497-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="2c497-139">SQL Server en una máquina virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="2c497-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="2c497-140">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="2c497-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="2c497-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="2c497-141">StorSimple</span></span>
    
- <span data-ttu-id="2c497-142">Almacén de datos SQL Azure</span><span class="sxs-lookup"><span data-stu-id="2c497-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="2c497-143">Lago de Azure Data Store</span><span class="sxs-lookup"><span data-stu-id="2c497-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="2c497-144">Para los detalles de cada una de estas opciones de almacenamiento de nube, vea [necesario algún ensamblado](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="2c497-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="2c497-145">Crear desde el principio</span><span class="sxs-lookup"><span data-stu-id="2c497-145">Build from the ground up</span></span>

<span data-ttu-id="2c497-146">Utilice estos pilares de almacenamiento de información, junto con la codificación, para crear su propia solución de almacenamiento de información o aplicaciones desde cero.</span><span class="sxs-lookup"><span data-stu-id="2c497-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="2c497-147">Almacenamiento de Azure (archivos)</span><span class="sxs-lookup"><span data-stu-id="2c497-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="2c497-148">Almacenamiento de Azure (BLOB)</span><span class="sxs-lookup"><span data-stu-id="2c497-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="2c497-149">Almacenamiento de Azure (colas)</span><span class="sxs-lookup"><span data-stu-id="2c497-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="2c497-150">Almacenamiento de Azure (tablas)</span><span class="sxs-lookup"><span data-stu-id="2c497-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="2c497-151">Para los detalles de cada una de estas opciones de almacenamiento de nube, vea [Generar desde la base](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="2c497-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="2c497-152">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="2c497-152">Key storage scenarios</span></span>

<span data-ttu-id="2c497-153">Aquí están los escenarios clave que requieren almacenamiento de información basados en cloud:</span><span class="sxs-lookup"><span data-stu-id="2c497-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="2c497-154">Datos de la caché</span><span class="sxs-lookup"><span data-stu-id="2c497-154">Cache data</span></span>
    
    <span data-ttu-id="2c497-155">Acelerar el acceso a datos utilizados habitualmente almacenándola en una memoria caché de alta velocidad.</span><span class="sxs-lookup"><span data-stu-id="2c497-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="2c497-156">Colaborar con los miembros del equipo</span><span class="sxs-lookup"><span data-stu-id="2c497-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="2c497-157">Conceder permiso a varios usuarios para permitir el acceso a los datos en el almacenamiento en la nube.</span><span class="sxs-lookup"><span data-stu-id="2c497-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="2c497-158">Administrar datos</span><span class="sxs-lookup"><span data-stu-id="2c497-158">Manage data</span></span>
    
    <span data-ttu-id="2c497-159">Almacenar, mover o eliminar datos de forma masiva interna o externa.</span><span class="sxs-lookup"><span data-stu-id="2c497-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="2c497-160">Administrar el código fuente</span><span class="sxs-lookup"><span data-stu-id="2c497-160">Manage source code</span></span>
    
    <span data-ttu-id="2c497-161">Cargar, colaborar y ejecutar archivos de código de la aplicación en la nube.</span><span class="sxs-lookup"><span data-stu-id="2c497-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="2c497-162">Archivos de copia de seguridad</span><span class="sxs-lookup"><span data-stu-id="2c497-162">Backup files</span></span>
    
    <span data-ttu-id="2c497-163">Almacenar copias de los datos internos o externos fuera del sitio en varias ubicaciones de la nube.</span><span class="sxs-lookup"><span data-stu-id="2c497-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="2c497-164">Publicar las comunicaciones de la empresa</span><span class="sxs-lookup"><span data-stu-id="2c497-164">Publish company communications</span></span>
    
    <span data-ttu-id="2c497-165">Crear un único punto de publicación de mensajes internos o externos.</span><span class="sxs-lookup"><span data-stu-id="2c497-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="2c497-166">Distribuir millones de eventos</span><span class="sxs-lookup"><span data-stu-id="2c497-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="2c497-167">Crear almacenamiento para la ingestión de telemetría de sitios Web, aplicaciones y dispositivos.</span><span class="sxs-lookup"><span data-stu-id="2c497-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="2c497-168">Administrar y servir vídeos</span><span class="sxs-lookup"><span data-stu-id="2c497-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="2c497-169">Almacenar y servir contenido de vídeo a los clientes o usuarios de la organización.</span><span class="sxs-lookup"><span data-stu-id="2c497-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="2c497-170">Siguiente paso</span><span class="sxs-lookup"><span data-stu-id="2c497-170">Next step</span></span>

<span data-ttu-id="2c497-171">Revise las opciones de almacenamiento de nube [mover en listo](move-in-ready.md) .</span><span class="sxs-lookup"><span data-stu-id="2c497-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2c497-172">See Also</span><span class="sxs-lookup"><span data-stu-id="2c497-172">See Also</span></span>

[<span data-ttu-id="2c497-173">Almacenamiento en la nube de Microsoft para Enterprise Architects</span><span class="sxs-lookup"><span data-stu-id="2c497-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="2c497-174">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="2c497-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="2c497-175">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="2c497-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)

