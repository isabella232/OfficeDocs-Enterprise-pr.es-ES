---
title: Diseño del almacenamiento para la nube de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 7e511118-1b75-413a-b959-ad0d3ffc9516
description: 'Resumen: Comprender por qué necesita almacenamiento en la nube y revise la lista de opciones de almacenamiento en la nube de Microsoft y los escenarios de almacenamiento de claves.'
ms.openlocfilehash: d96992d63115095dd6a1b7277886d0a4bb2bc02f
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915235"
---
# <a name="designing-storage-for-the-microsoft-cloud"></a><span data-ttu-id="9bbc6-103">Diseño del almacenamiento para la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9bbc6-103">Designing storage for the Microsoft cloud</span></span>

 <span data-ttu-id="9bbc6-104">**Resumen:** Comprender por qué necesita almacenamiento en la nube y revise la lista de opciones de almacenamiento en la nube de Microsoft y los escenarios de almacenamiento de claves.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-104">**Summary:** Understand why you need cloud storage and review the list of Microsoft's cloud storage options and the key storage scenarios.</span></span>
  
<span data-ttu-id="9bbc6-105">Integración de su almacenamiento de información con los servicios de nube de Microsoft le proporciona acceso a una amplia gama de opciones de plataforma de servicios y en la nube.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-105">Integrating your storage with Microsoft cloud services gives you access to a broad range of services and cloud platform options.</span></span>
  
## <a name="why-cloud-storage"></a><span data-ttu-id="9bbc6-106">¿Por qué almacenamiento en nube?</span><span class="sxs-lookup"><span data-stu-id="9bbc6-106">Why cloud storage?</span></span>

<span data-ttu-id="9bbc6-107">Hay dos motivos principales para usar el almacenamiento en la nube.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-107">There are two key reasons to use cloud storage.</span></span>
  
1. <span data-ttu-id="9bbc6-108">Velocidad de mercado:</span><span class="sxs-lookup"><span data-stu-id="9bbc6-108">Speed to market:</span></span>
    
  - <span data-ttu-id="9bbc6-109">Configuración más rápido para alta disponibilidad y recuperación ante desastres</span><span class="sxs-lookup"><span data-stu-id="9bbc6-109">Faster configuration for high availability and disaster recovery</span></span>
    
  - <span data-ttu-id="9bbc6-110">No hay hardware de almacenamiento para comprar</span><span class="sxs-lookup"><span data-stu-id="9bbc6-110">No storage hardware to purchase</span></span>
    
  - <span data-ttu-id="9bbc6-111">Instalaciones sanitarias integrados proporcionados por las ofertas de nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9bbc6-111">Built-in plumbing provided by Microsoft's cloud offerings</span></span>
    
  - <span data-ttu-id="9bbc6-112">Disponible en cualquier lugar del mundo</span><span class="sxs-lookup"><span data-stu-id="9bbc6-112">Available from anywhere in the world</span></span>
    
2. <span data-ttu-id="9bbc6-113">Disminuir los costos para mantener:</span><span class="sxs-lookup"><span data-stu-id="9bbc6-113">Lower costs to maintain:</span></span>
    
  - <span data-ttu-id="9bbc6-114">Elasticidad para escalar hacia arriba y abajo sus exigencias de almacenamiento de información</span><span class="sxs-lookup"><span data-stu-id="9bbc6-114">Elasticity to scale up and down your storage demands</span></span>
    
  - <span data-ttu-id="9bbc6-115">No hay hardware de almacenamiento de información para mantener o migrar</span><span class="sxs-lookup"><span data-stu-id="9bbc6-115">No storage hardware to maintain or migrate</span></span>
    
  - <span data-ttu-id="9bbc6-116">Microsoft es su fontanero integrada para mantener y mejorar la infraestructura</span><span class="sxs-lookup"><span data-stu-id="9bbc6-116">Microsoft is your built-in plumber to maintain and improve infrastructure</span></span>
    
  - <span data-ttu-id="9bbc6-117">Mejor seguridad de almacenamiento de información en el mercado con mejoras continuas</span><span class="sxs-lookup"><span data-stu-id="9bbc6-117">Best storage security in the marketplace with ongoing improvements</span></span>
    
## <a name="microsoft-cloud-storage-options"></a><span data-ttu-id="9bbc6-118">Opciones de almacenamiento en la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9bbc6-118">Microsoft cloud storage options</span></span>

<span data-ttu-id="9bbc6-119">Para ayudarle a comprender la amplia variedad de opciones de almacenamiento en la nube, usamos una analogía de construcción.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-119">To help you understand the wide variety of cloud storage options, we use a construction analogy.</span></span>
  
### <a name="move-in-ready"></a><span data-ttu-id="9bbc6-120">Listo para la instalación</span><span class="sxs-lookup"><span data-stu-id="9bbc6-120">Move-in ready</span></span>

<span data-ttu-id="9bbc6-p101">Use estas soluciones ya preparadas que se empaquetan con servicios existentes. Utilizar inmediatamente y con la configuración mínima.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-p101">Use these prepackaged solutions that are bundled with existing services. Use immediately and with minimal configuration.</span></span>
  
- <span data-ttu-id="9bbc6-123">Creación de inquilino</span><span class="sxs-lookup"><span data-stu-id="9bbc6-123">Office 365</span></span>
    
- <span data-ttu-id="9bbc6-124">Microsoft Intune</span><span class="sxs-lookup"><span data-stu-id="9bbc6-124">Microsoft Intune</span></span>
    
- <span data-ttu-id="9bbc6-125">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="9bbc6-125">OneDrive for Business</span></span>
    
- <span data-ttu-id="9bbc6-126">Dynamics 365</span><span class="sxs-lookup"><span data-stu-id="9bbc6-126">Dynamics 365</span></span>
    
- <span data-ttu-id="9bbc6-127">Visual Studio Team Services</span><span class="sxs-lookup"><span data-stu-id="9bbc6-127">Visual Studio Team Services</span></span>
    
- <span data-ttu-id="9bbc6-128">Azure Site Recovery</span><span class="sxs-lookup"><span data-stu-id="9bbc6-128">Azure Site Recovery</span></span>
    
- <span data-ttu-id="9bbc6-129">Sitio de uso compartido de yammer</span><span class="sxs-lookup"><span data-stu-id="9bbc6-129">Yammer Site Sharing</span></span>
    
- <span data-ttu-id="9bbc6-130">Copia de seguridad de Azure</span><span class="sxs-lookup"><span data-stu-id="9bbc6-130">Azure Backup</span></span>
    
<span data-ttu-id="9bbc6-131">Para los detalles de cada una de estas opciones de almacenamiento en nube, consulte [Move en listo](move-in-ready.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc6-131">For the details of each of these cloud storage options, see [Move-in ready](move-in-ready.md).</span></span>
  
### <a name="some-assembly-required"></a><span data-ttu-id="9bbc6-132">Se necesitan algunos ensamblados</span><span class="sxs-lookup"><span data-stu-id="9bbc6-132">Some assembly required</span></span>

<span data-ttu-id="9bbc6-133">Utilice estos servicios existentes como un punto de partida para su solución de almacenamiento con una configuración adicional o codificación para que se ajusten personalizado.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-133">Use these existing services as a starting point for your storage solution with additional configuration or coding for a custom fit.</span></span>
  
- <span data-ttu-id="9bbc6-134">Red de entrega de contenido de Azure</span><span class="sxs-lookup"><span data-stu-id="9bbc6-134">Azure Content Delivery Network</span></span>
    
- <span data-ttu-id="9bbc6-135">Servicios de multimedia de Azure</span><span class="sxs-lookup"><span data-stu-id="9bbc6-135">Azure Media Services</span></span>
    
- <span data-ttu-id="9bbc6-136">HdInsight</span><span class="sxs-lookup"><span data-stu-id="9bbc6-136">HdInsight</span></span>
    
- <span data-ttu-id="9bbc6-137">Memoria caché Redis Azure</span><span class="sxs-lookup"><span data-stu-id="9bbc6-137">Azure Redis Cache</span></span>
    
- <span data-ttu-id="9bbc6-138">Base de datos SQL de Azure</span><span class="sxs-lookup"><span data-stu-id="9bbc6-138">Azure SQL Database</span></span>
    
- <span data-ttu-id="9bbc6-139">SQL Server en una máquina virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="9bbc6-139">SQL Server on an Azure VM</span></span>
    
- <span data-ttu-id="9bbc6-140">DB Cosmos Azure</span><span class="sxs-lookup"><span data-stu-id="9bbc6-140">Azure Cosmos DB</span></span>
    
- <span data-ttu-id="9bbc6-141">StorSimple</span><span class="sxs-lookup"><span data-stu-id="9bbc6-141">StorSimple</span></span>
    
- <span data-ttu-id="9bbc6-142">Almacén de datos SQL Azure</span><span class="sxs-lookup"><span data-stu-id="9bbc6-142">Azure SQL Data Warehouse</span></span>
    
- <span data-ttu-id="9bbc6-143">Almacén de lago de datos de Azure</span><span class="sxs-lookup"><span data-stu-id="9bbc6-143">Azure Data Lake Store</span></span>
    
<span data-ttu-id="9bbc6-144">Para obtener detalles de cada una de estas opciones de almacenamiento en la nube, vea [algunos ensamblado necesarios](some-assembly-required.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc6-144">For the details of each of these cloud storage options, see [Some assembly required](some-assembly-required.md).</span></span>
  
### <a name="build-from-the-ground-up"></a><span data-ttu-id="9bbc6-145">Crear desde cero</span><span class="sxs-lookup"><span data-stu-id="9bbc6-145">Build from the ground up</span></span>

<span data-ttu-id="9bbc6-146">Use estos bloques de creación de almacenamiento, junto con codificación, para crear su propia solución de almacenamiento o aplicaciones desde el principio.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-146">Use these storage building blocks, along with coding, to create your own storage solution or apps from scratch.</span></span>
  
- <span data-ttu-id="9bbc6-147">Almacenamiento de Azure (archivos)</span><span class="sxs-lookup"><span data-stu-id="9bbc6-147">Azure Storage (files)</span></span>
    
- <span data-ttu-id="9bbc6-148">Almacenamiento de Azure (BLOB)</span><span class="sxs-lookup"><span data-stu-id="9bbc6-148">Azure Storage (blobs)</span></span>
    
- <span data-ttu-id="9bbc6-149">Almacenamiento de Azure (colas)</span><span class="sxs-lookup"><span data-stu-id="9bbc6-149">Azure Storage (queues)</span></span>
    
- <span data-ttu-id="9bbc6-150">Almacenamiento de Azure (tablas)</span><span class="sxs-lookup"><span data-stu-id="9bbc6-150">Azure Storage (tables)</span></span>
    
<span data-ttu-id="9bbc6-151">Para obtener detalles de cada una de estas opciones de almacenamiento en la nube, vea [crear desde cero](build-from-the-ground-up.md).</span><span class="sxs-lookup"><span data-stu-id="9bbc6-151">For the details of each of these cloud storage options, see [Build from the ground up](build-from-the-ground-up.md).</span></span>
  
## <a name="key-storage-scenarios"></a><span data-ttu-id="9bbc6-152">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="9bbc6-152">Key storage scenarios</span></span>

<span data-ttu-id="9bbc6-153">Estos son los principales escenarios que requieren almacenamiento de información basada en la nube:</span><span class="sxs-lookup"><span data-stu-id="9bbc6-153">Here are the key scenarios that require cloud-based storage:</span></span>
  
- <span data-ttu-id="9bbc6-154">Datos de la memoria caché</span><span class="sxs-lookup"><span data-stu-id="9bbc6-154">Cache data</span></span>
    
    <span data-ttu-id="9bbc6-155">Acelerar el acceso a los datos usados con más frecuencia mediante el almacenamiento en una memoria caché de alta velocidad.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-155">Accelerate access to commonly used data by storing it in a high-speed cache.</span></span>
    
- <span data-ttu-id="9bbc6-156">Colaborar con los miembros del equipo</span><span class="sxs-lookup"><span data-stu-id="9bbc6-156">Collaborate with team members</span></span>
    
    <span data-ttu-id="9bbc6-157">Conceder permisos a varios usuarios para permitir el acceso a datos en el almacenamiento en la nube.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-157">Grant permission to multiple users to allow access to data in cloud storage.</span></span>
    
- <span data-ttu-id="9bbc6-158">Administrar datos</span><span class="sxs-lookup"><span data-stu-id="9bbc6-158">Manage data</span></span>
    
    <span data-ttu-id="9bbc6-159">Almacenar, mover o eliminar datos de forma masiva interno o externo.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-159">Store, move, or delete internal or external bulk data.</span></span>
    
- <span data-ttu-id="9bbc6-160">Administrar el código fuente</span><span class="sxs-lookup"><span data-stu-id="9bbc6-160">Manage source code</span></span>
    
    <span data-ttu-id="9bbc6-161">Cargar, colaborar y archivos de código de aplicaciones se ejecutan en la nube.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-161">Upload, collaborate, and run application code files in the cloud.</span></span>
    
- <span data-ttu-id="9bbc6-162">Archivos de copia de seguridad</span><span class="sxs-lookup"><span data-stu-id="9bbc6-162">Backup files</span></span>
    
    <span data-ttu-id="9bbc6-163">Almacenar copias de los datos internos o externos fuera del sitio en varias ubicaciones en la nube.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-163">Store copies of internal or external data offsite in multiple cloud locations.</span></span>
    
- <span data-ttu-id="9bbc6-164">Publicación de comunicaciones de la empresa</span><span class="sxs-lookup"><span data-stu-id="9bbc6-164">Publish company communications</span></span>
    
    <span data-ttu-id="9bbc6-165">Crear un único punto de publicación para los mensajes internos o externos.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-165">Create a single point of publication for internal or external messages.</span></span>
    
- <span data-ttu-id="9bbc6-166">Distribuir millones de eventos</span><span class="sxs-lookup"><span data-stu-id="9bbc6-166">Distribute millions of events</span></span>
    
    <span data-ttu-id="9bbc6-167">Crear almacenamiento para ingesta de telemetría de sitios Web, aplicaciones y dispositivos.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-167">Create storage for telemetry ingestion from websites, apps, and devices.</span></span>
    
- <span data-ttu-id="9bbc6-168">Administrar/serve vídeos</span><span class="sxs-lookup"><span data-stu-id="9bbc6-168">Manage/serve videos</span></span>
    
    <span data-ttu-id="9bbc6-169">Almacenar y atender a contenido de vídeo a los clientes o usuarios de la organización.</span><span class="sxs-lookup"><span data-stu-id="9bbc6-169">Store and serve video content to customers or organization users.</span></span>
    
## <a name="next-step"></a><span data-ttu-id="9bbc6-170">Paso siguiente</span><span class="sxs-lookup"><span data-stu-id="9bbc6-170">Next step</span></span>

<span data-ttu-id="9bbc6-171">Revise las opciones de almacenamiento en la nube de [movimiento en listo](move-in-ready.md) .</span><span class="sxs-lookup"><span data-stu-id="9bbc6-171">Review the [Move-in ready](move-in-ready.md) cloud storage options.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9bbc6-172">Vea también</span><span class="sxs-lookup"><span data-stu-id="9bbc6-172">See Also</span></span>

[<span data-ttu-id="9bbc6-173">Almacenamiento de Microsoft Cloud para arquitectos empresariales</span><span class="sxs-lookup"><span data-stu-id="9bbc6-173">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="9bbc6-174">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="9bbc6-174">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="9bbc6-175">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="9bbc6-175">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)


