---
title: Crear desde el principio
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: "Resumen: Obtenga los detalles en el conjunto de la nube de bloques de creación de almacenamiento de información que puede utilizar para crear su propio servicio de almacenamiento o la solución."
ms.openlocfilehash: eabf38e0ccef3335b2d198a33f5622d0d449589a
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="e4f82-103">Crear desde el principio</span><span class="sxs-lookup"><span data-stu-id="e4f82-103">Build from the ground up</span></span>

 <span data-ttu-id="e4f82-104">**Resumen:** Obtenga los detalles en el conjunto de la nube de bloques de creación de almacenamiento de información que puede utilizar para crear su propio servicio de almacenamiento o la solución.</span><span class="sxs-lookup"><span data-stu-id="e4f82-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="e4f82-105">"Generarlo desde el principio" soluciones de almacenamiento de información:</span><span class="sxs-lookup"><span data-stu-id="e4f82-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="e4f82-106">Le permiten crear su propia solución de almacenamiento de información desde el principio.</span><span class="sxs-lookup"><span data-stu-id="e4f82-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="e4f82-107">Requiere una programación mediante las API del resto.</span><span class="sxs-lookup"><span data-stu-id="e4f82-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="e4f82-108">Proporcionar lo último en flexibilidad y personalización.</span><span class="sxs-lookup"><span data-stu-id="e4f82-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="e4f82-109">Las secciones siguientes describen los detalles de cada opción de almacenamiento "Crear desde cero".</span><span class="sxs-lookup"><span data-stu-id="e4f82-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="e4f82-110">Almacenamiento de Azure (archivos)</span><span class="sxs-lookup"><span data-stu-id="e4f82-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="e4f82-111">Características</span><span class="sxs-lookup"><span data-stu-id="e4f82-111">Features</span></span>

- <span data-ttu-id="e4f82-112">Resulta más fácil mover aplicaciones heredadas a la nube</span><span class="sxs-lookup"><span data-stu-id="e4f82-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="e4f82-113">Almacenamiento de blobs preferido para nuevas aplicaciones</span><span class="sxs-lookup"><span data-stu-id="e4f82-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="e4f82-114">Puede montar desde una máquina virtual Azure</span><span class="sxs-lookup"><span data-stu-id="e4f82-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="e4f82-115">Puede montar locales con SMB 3.0</span><span class="sxs-lookup"><span data-stu-id="e4f82-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="e4f82-116">Funciona con Linux y Windows</span><span class="sxs-lookup"><span data-stu-id="e4f82-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="e4f82-117">No admite autenticación AD Azure o ACL (claves de almacenamiento de Azure cuenta proporcionan autenticación y autorización para obtener acceso al recurso compartido de archivo)</span><span class="sxs-lookup"><span data-stu-id="e4f82-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="e4f82-118">Usos comunes</span><span class="sxs-lookup"><span data-stu-id="e4f82-118">Common uses</span></span>

- <span data-ttu-id="e4f82-119">Migrar aplicaciones heredadas a la nube que se basan en recursos compartidos de archivos</span><span class="sxs-lookup"><span data-stu-id="e4f82-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="e4f82-120">Compartir herramientas de desarrollo y pruebas</span><span class="sxs-lookup"><span data-stu-id="e4f82-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="e4f82-121">Aplicaciones distribuidas pueden almacenar registros de datos de diagnóstico y volcados de sucesos</span><span class="sxs-lookup"><span data-stu-id="e4f82-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="e4f82-122">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="e4f82-122">Key storage scenarios</span></span>

- <span data-ttu-id="e4f82-123">Archivos de copia de seguridad</span><span class="sxs-lookup"><span data-stu-id="e4f82-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="e4f82-124">Recursos</span><span class="sxs-lookup"><span data-stu-id="e4f82-124">Resources</span></span>

<span data-ttu-id="e4f82-125">Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4f82-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="e4f82-126">Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="e4f82-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="e4f82-127">Almacenamiento de Azure (BLOB)</span><span class="sxs-lookup"><span data-stu-id="e4f82-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="e4f82-128">Características</span><span class="sxs-lookup"><span data-stu-id="e4f82-128">Features</span></span>

- <span data-ttu-id="e4f82-129">Cada cuenta de almacenamiento puede contener hasta 500 TB (una suscripción puede tener varias cuentas de almacenamiento)</span><span class="sxs-lookup"><span data-stu-id="e4f82-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="e4f82-130">Cuentas de almacenamiento se organizan en contenedores, que pueden tener la seguridad aplicada a ellos y pueden contener objetos binarios</span><span class="sxs-lookup"><span data-stu-id="e4f82-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="e4f82-131">BLOB de bloque está optimizado para la transmisión y almacenamiento de nube objetos hasta 200 GB de tamaño</span><span class="sxs-lookup"><span data-stu-id="e4f82-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="e4f82-132">Blobs de página están optimizados para que representan discos PaaS y escribe apoyando aleatorio, tamaño de hasta 1 TB</span><span class="sxs-lookup"><span data-stu-id="e4f82-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="e4f82-133">Anexar objetos binarios están optimizados para anexar las operaciones, 195 GB</span><span class="sxs-lookup"><span data-stu-id="e4f82-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="e4f82-134">Almacenamiento de Premium proporciona más rápidos IOPS a través del almacenamiento SSD</span><span class="sxs-lookup"><span data-stu-id="e4f82-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="e4f82-135">Usos comunes</span><span class="sxs-lookup"><span data-stu-id="e4f82-135">Common uses</span></span>

- <span data-ttu-id="e4f82-136">Copias de seguridad de archivos, equipos, bases de datos y dispositivos de imágenes y texto para aplicaciones web</span><span class="sxs-lookup"><span data-stu-id="e4f82-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="e4f82-137">Datos de configuración de aplicaciones de nube</span><span class="sxs-lookup"><span data-stu-id="e4f82-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="e4f82-138">Datos grandes, como los registros y otros conjuntos de datos grandes</span><span class="sxs-lookup"><span data-stu-id="e4f82-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="e4f82-139">Blob de Azure utiliza almacenamiento de información para sus propios servicios, como los discos de máquinas virtuales y HDInsight</span><span class="sxs-lookup"><span data-stu-id="e4f82-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="e4f82-140">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="e4f82-140">Key storage scenarios</span></span>

- <span data-ttu-id="e4f82-141">Administrar datos</span><span class="sxs-lookup"><span data-stu-id="e4f82-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="e4f82-142">Recursos</span><span class="sxs-lookup"><span data-stu-id="e4f82-142">Resources</span></span>

<span data-ttu-id="e4f82-143">Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4f82-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="e4f82-144">Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="e4f82-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="e4f82-145">Almacenamiento de Azure (colas)</span><span class="sxs-lookup"><span data-stu-id="e4f82-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="e4f82-146">Características</span><span class="sxs-lookup"><span data-stu-id="e4f82-146">Features</span></span>

- <span data-ttu-id="e4f82-147">Cuenta de almacenamiento puede contener cualquier número de colas</span><span class="sxs-lookup"><span data-stu-id="e4f82-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="e4f82-148">Cola puede contener cualquier número de mensajes (hasta que la cuenta de almacenamiento está lleno)</span><span class="sxs-lookup"><span data-stu-id="e4f82-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="e4f82-149">La cola de mensajes automáticamente se eliminan transcurridos siete días si no recuperada y eliminada por una aplicación</span><span class="sxs-lookup"><span data-stu-id="e4f82-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="e4f82-150">Mensajes pueden ser de hasta 64 KB de tamaño</span><span class="sxs-lookup"><span data-stu-id="e4f82-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="e4f82-151">Protegidos a nivel de cuenta de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="e4f82-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="e4f82-152">Las colas se van a pasar mensajes de control, los datos sin procesar no</span><span class="sxs-lookup"><span data-stu-id="e4f82-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="e4f82-153">Usos comunes</span><span class="sxs-lookup"><span data-stu-id="e4f82-153">Common uses</span></span>

- <span data-ttu-id="e4f82-154">Crear un registro de trabajo para procesar de forma asincrónica</span><span class="sxs-lookup"><span data-stu-id="e4f82-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="e4f82-155">Procesamiento de mensajes de registro</span><span class="sxs-lookup"><span data-stu-id="e4f82-155">Processing log messages</span></span>
    
- <span data-ttu-id="e4f82-156">Desacoplar aplicaciones</span><span class="sxs-lookup"><span data-stu-id="e4f82-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="e4f82-157">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="e4f82-157">Key storage scenarios</span></span>

- <span data-ttu-id="e4f82-158">Distribuir eventos</span><span class="sxs-lookup"><span data-stu-id="e4f82-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="e4f82-159">Recursos</span><span class="sxs-lookup"><span data-stu-id="e4f82-159">Resources</span></span>

<span data-ttu-id="e4f82-160">Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4f82-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="e4f82-161">Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="e4f82-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="e4f82-162">Almacenamiento de Azure (tablas)</span><span class="sxs-lookup"><span data-stu-id="e4f82-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="e4f82-163">Características</span><span class="sxs-lookup"><span data-stu-id="e4f82-163">Features</span></span>

- <span data-ttu-id="e4f82-164">Mejor los conjuntos de datos semiestructurados</span><span class="sxs-lookup"><span data-stu-id="e4f82-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="e4f82-165">Normalmente un coste menor que SQL tradicional</span><span class="sxs-lookup"><span data-stu-id="e4f82-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="e4f82-166">Muy rápida si la consulta de clave, lento si la consulta de valor</span><span class="sxs-lookup"><span data-stu-id="e4f82-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="e4f82-167">Escalable masivamente; cualquier cantidad de tablas hasta los límites de la cuenta de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="e4f82-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="e4f82-168">Accesible a través de la API de REST, protocolo oData limitado, .NET</span><span class="sxs-lookup"><span data-stu-id="e4f82-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="e4f82-169">Los valores deben serializarse.</span><span class="sxs-lookup"><span data-stu-id="e4f82-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="e4f82-170">Usos comunes</span><span class="sxs-lookup"><span data-stu-id="e4f82-170">Common uses</span></span>

- <span data-ttu-id="e4f82-171">Datos de usuario para aplicaciones web</span><span class="sxs-lookup"><span data-stu-id="e4f82-171">User data for web applications</span></span>
    
- <span data-ttu-id="e4f82-172">Libretas de direcciones</span><span class="sxs-lookup"><span data-stu-id="e4f82-172">Address books</span></span>
    
- <span data-ttu-id="e4f82-173">Información del dispositivo</span><span class="sxs-lookup"><span data-stu-id="e4f82-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="e4f82-174">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="e4f82-174">Key storage scenarios</span></span>

- <span data-ttu-id="e4f82-175">Administrar datos</span><span class="sxs-lookup"><span data-stu-id="e4f82-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="e4f82-176">Recursos</span><span class="sxs-lookup"><span data-stu-id="e4f82-176">Resources</span></span>

<span data-ttu-id="e4f82-177">Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span><span class="sxs-lookup"><span data-stu-id="e4f82-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="e4f82-178">Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="e4f82-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="e4f82-179">Recomendaciones de almacenamiento de Azure de Microsoft</span><span class="sxs-lookup"><span data-stu-id="e4f82-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="e4f82-180">Al diseñar su solución de almacenamiento de información personalizada con el almacenamiento de Azure, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="e4f82-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="e4f82-181">Aproveche varias cuentas de almacenamiento de información para una mayor escalabilidad, para el aumento de tamaño (> 100 TB) o para un mayor rendimiento (> 5.000 operaciones por segundo).</span><span class="sxs-lookup"><span data-stu-id="e4f82-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="e4f82-182">Diseño de la capacidad para agregar cuentas de almacenamiento adicionales como un cambio de configuración, no como un cambio de código.</span><span class="sxs-lookup"><span data-stu-id="e4f82-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="e4f82-183">Elija cuidadosamente las funciones de partición para el almacenamiento de la tabla habilitar la escala deseada en términos de rendimiento de inserción y consulta.</span><span class="sxs-lookup"><span data-stu-id="e4f82-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="e4f82-184">Elija nombres de columna cortos para propiedades como los metadatos (nombres de propiedad) de la tabla están almacenado dentro de banda (los nombres de columna también cuentan para el tamaño máximo de fila de 1 MB).</span><span class="sxs-lookup"><span data-stu-id="e4f82-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="e4f82-185">Cuando sea posible, las operaciones en el almacenamiento de información de lote.</span><span class="sxs-lookup"><span data-stu-id="e4f82-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="e4f82-186">Agresivamente caché la información de la base de datos de configuración en una memoria caché distribuida.</span><span class="sxs-lookup"><span data-stu-id="e4f82-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="e4f82-187">Si depende de tener un cierto segmento de datos disponibles en la caché de aplicación rendimiento o la confiabilidad, la aplicación debe rechazar las solicitudes entrantes hasta que la memoria caché ha sido rellenada.</span><span class="sxs-lookup"><span data-stu-id="e4f82-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="e4f82-188">Dividir los datos en vertical (por tabla) u horizontalmente (tabla de segmentos en varios fragmentos) para repartir la carga entre varias bases de datos.</span><span class="sxs-lookup"><span data-stu-id="e4f82-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="e4f82-189">Consulte también</span><span class="sxs-lookup"><span data-stu-id="e4f82-189">See Also</span></span>

[<span data-ttu-id="e4f82-190">Almacenamiento de Microsoft Cloud para arquitectos empresariales</span><span class="sxs-lookup"><span data-stu-id="e4f82-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="e4f82-191">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="e4f82-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="e4f82-192">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="e4f82-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



