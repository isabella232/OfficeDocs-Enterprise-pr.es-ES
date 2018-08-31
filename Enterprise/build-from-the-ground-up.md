---
title: Crear desde cero
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
ms.assetid: 84348d0c-d9d1-4a98-9b99-8433f9b70e45
description: 'Resumen: Para obtener información sobre el conjunto de nube de bloques de creación de almacenamiento que puede usar para crear su propio servicio de almacenamiento o la solución.'
ms.openlocfilehash: 8ef5d7a99c4e82d9a4fc3eb281a4af505887b792
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915685"
---
# <a name="build-from-the-ground-up"></a><span data-ttu-id="8eebf-103">Crear desde cero</span><span class="sxs-lookup"><span data-stu-id="8eebf-103">Build from the ground up</span></span>

 <span data-ttu-id="8eebf-104">**Resumen:** Para obtener información sobre el conjunto de nube de bloques de creación de almacenamiento que puede usar para crear su propio servicio de almacenamiento o la solución.</span><span class="sxs-lookup"><span data-stu-id="8eebf-104">**Summary:** Get the details on the set of cloud storage building blocks that you can use to create your own storage service or solution.</span></span>
  
<span data-ttu-id="8eebf-105">"Generarlo desde el principio" soluciones de almacenamiento de información:</span><span class="sxs-lookup"><span data-stu-id="8eebf-105">"Build from the ground up" storage solutions:</span></span>
  
- <span data-ttu-id="8eebf-106">Permiten crear su propia solución de almacenamiento de información desde el principio.</span><span class="sxs-lookup"><span data-stu-id="8eebf-106">Allow you to create your own storage solution from scratch.</span></span> 
    
- <span data-ttu-id="8eebf-107">Requiere que la programación con las API de REST.</span><span class="sxs-lookup"><span data-stu-id="8eebf-107">Requires programming using the REST APIs.</span></span>
    
- <span data-ttu-id="8eebf-108">Proporcionar lo último en flexibilidad y personalización.</span><span class="sxs-lookup"><span data-stu-id="8eebf-108">Provide the ultimate in customization and flexibility.</span></span>
    
<span data-ttu-id="8eebf-109">En las secciones siguientes se describen los detalles de cada opción de almacenamiento "Generarlo desde el principio".</span><span class="sxs-lookup"><span data-stu-id="8eebf-109">The following sections describe the details of each "Build from the ground up" storage option.</span></span>
  
## <a name="azure-storage-files"></a><span data-ttu-id="8eebf-110">Almacenamiento de Azure (archivos)</span><span class="sxs-lookup"><span data-stu-id="8eebf-110">Azure Storage (files)</span></span>

### <a name="features"></a><span data-ttu-id="8eebf-111">Características</span><span class="sxs-lookup"><span data-stu-id="8eebf-111">Features</span></span>

- <span data-ttu-id="8eebf-112">Resulta más sencillo mover aplicaciones heredadas a la nube</span><span class="sxs-lookup"><span data-stu-id="8eebf-112">Makes it easier to move legacy applications to the cloud</span></span>
    
- <span data-ttu-id="8eebf-113">Almacenamiento de blobs preferido para nuevas aplicaciones</span><span class="sxs-lookup"><span data-stu-id="8eebf-113">Blob storage preferred for new applications</span></span>
    
- <span data-ttu-id="8eebf-114">Puede montar desde una máquina virtual de Azure</span><span class="sxs-lookup"><span data-stu-id="8eebf-114">Can mount from an Azure virtual machine</span></span>
    
- <span data-ttu-id="8eebf-115">Puede montar local con SMB 3.0</span><span class="sxs-lookup"><span data-stu-id="8eebf-115">Can mount on-premises with SMB 3.0</span></span>
    
- <span data-ttu-id="8eebf-116">Funciona con Windows y Linux</span><span class="sxs-lookup"><span data-stu-id="8eebf-116">Works with Linux and Windows</span></span>
    
- <span data-ttu-id="8eebf-117">No es compatible con la autenticación basada en AD Azure o ACL (claves de la cuenta de almacenamiento de Azure proporcionan autenticación y autorización para obtener acceso al recurso compartido de archivo)</span><span class="sxs-lookup"><span data-stu-id="8eebf-117">Doesn't support Azure AD-based authentication or ACLs (Azure Storage account keys provide authentication and authorized access to the file share)</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="8eebf-118">Usos comunes</span><span class="sxs-lookup"><span data-stu-id="8eebf-118">Common uses</span></span>

- <span data-ttu-id="8eebf-119">Migración de aplicaciones heredadas a la nube que se basan en recursos compartidos de archivos</span><span class="sxs-lookup"><span data-stu-id="8eebf-119">Migrating legacy applications to the cloud that rely on file shares</span></span>
    
- <span data-ttu-id="8eebf-120">Compartir herramientas de desarrollo y pruebas</span><span class="sxs-lookup"><span data-stu-id="8eebf-120">Share development and testing tools</span></span>
    
- <span data-ttu-id="8eebf-121">Pueden almacenar los registros de datos de diagnóstico y volcados de sucesos aplicaciones distribuidas</span><span class="sxs-lookup"><span data-stu-id="8eebf-121">Distributed apps can store logs, diagnostic data, and crash dumps</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="8eebf-122">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="8eebf-122">Key storage scenarios</span></span>

- <span data-ttu-id="8eebf-123">Archivos de copia de seguridad</span><span class="sxs-lookup"><span data-stu-id="8eebf-123">Backup files</span></span>
    
### <a name="resources"></a><span data-ttu-id="8eebf-124">Recursos</span><span class="sxs-lookup"><span data-stu-id="8eebf-124">Resources</span></span>

<span data-ttu-id="8eebf-125">Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span><span class="sxs-lookup"><span data-stu-id="8eebf-125">For additional information, click [here](https://msdn.microsoft.com/library/azure/dn166972.aspx).</span></span>
  
<span data-ttu-id="8eebf-126">Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="8eebf-126">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-blobs"></a><span data-ttu-id="8eebf-127">Almacenamiento de Azure (BLOB)</span><span class="sxs-lookup"><span data-stu-id="8eebf-127">Azure Storage (blobs)</span></span>

### <a name="features"></a><span data-ttu-id="8eebf-128">Características</span><span class="sxs-lookup"><span data-stu-id="8eebf-128">Features</span></span>

- <span data-ttu-id="8eebf-129">Cada cuenta de almacenamiento puede contener hasta 500 TB (una sola suscripción puede tener varias cuentas de almacenamiento)</span><span class="sxs-lookup"><span data-stu-id="8eebf-129">Each storage account can hold up to 500 TB (one subscription can have multiple storage accounts)</span></span>
    
- <span data-ttu-id="8eebf-130">Cuentas de almacenamiento se organizan en contenedores, que pueden tener la seguridad que se aplican a ellos y pueden contener BLOB</span><span class="sxs-lookup"><span data-stu-id="8eebf-130">Storage accounts are organized into containers, which can have security applied to them and can contain blobs</span></span>
    
- <span data-ttu-id="8eebf-131">BLOB de bloque está optimizado para la transmisión por secuencias y objetos de almacenar en la nube, hasta 200 GB de tamaño</span><span class="sxs-lookup"><span data-stu-id="8eebf-131">Block blobs are optimized for streaming and storing cloud objects, up to 200 GB in size</span></span>
    
- <span data-ttu-id="8eebf-132">BLOB de página está optimizado para representar PaaS discos y admitir aleatorio escribe un tamaño de hasta 1 TB</span><span class="sxs-lookup"><span data-stu-id="8eebf-132">Page blobs are optimized for representing PaaS disks and supporting random writes, up to 1 TB in size</span></span>
    
- <span data-ttu-id="8eebf-133">Anexar BLOB está optimizado para anexar las operaciones, 195 GB</span><span class="sxs-lookup"><span data-stu-id="8eebf-133">Append blobs are optimized for append operations, up to 195 GB</span></span>
    
- <span data-ttu-id="8eebf-134">Almacenamiento de Premium proporciona más rápidas IOPS a través de almacenamiento SSD</span><span class="sxs-lookup"><span data-stu-id="8eebf-134">Premium Storage provides faster IOPS through SSD storage</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="8eebf-135">Usos comunes</span><span class="sxs-lookup"><span data-stu-id="8eebf-135">Common uses</span></span>

- <span data-ttu-id="8eebf-136">Copias de seguridad de los archivos, equipos, las bases de datos y dispositivos de imágenes y texto para las aplicaciones web</span><span class="sxs-lookup"><span data-stu-id="8eebf-136">Backups of files, computers, databases, and devices Images and text for web applications</span></span>
    
- <span data-ttu-id="8eebf-137">Datos de configuración de aplicaciones de nube</span><span class="sxs-lookup"><span data-stu-id="8eebf-137">Configuration data for cloud applications</span></span>
    
- <span data-ttu-id="8eebf-138">Datos grandes, como los registros y otros grandes conjuntos de datos</span><span class="sxs-lookup"><span data-stu-id="8eebf-138">Big data, such as logs and other large datasets</span></span>
    
- <span data-ttu-id="8eebf-139">Usos de Azure blob almacenamiento para sus propios servicios, como los discos HDInsight y una máquina virtual</span><span class="sxs-lookup"><span data-stu-id="8eebf-139">Azure uses blob storage for its own services, such as HDInsight and virtual machine disks</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="8eebf-140">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="8eebf-140">Key storage scenarios</span></span>

- <span data-ttu-id="8eebf-141">Administrar datos</span><span class="sxs-lookup"><span data-stu-id="8eebf-141">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="8eebf-142">Recursos</span><span class="sxs-lookup"><span data-stu-id="8eebf-142">Resources</span></span>

<span data-ttu-id="8eebf-143">Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span><span class="sxs-lookup"><span data-stu-id="8eebf-143">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179376.aspx).</span></span>
  
<span data-ttu-id="8eebf-144">Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="8eebf-144">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-queues"></a><span data-ttu-id="8eebf-145">Almacenamiento de Azure (colas)</span><span class="sxs-lookup"><span data-stu-id="8eebf-145">Azure Storage (queues)</span></span>

### <a name="features"></a><span data-ttu-id="8eebf-146">Características</span><span class="sxs-lookup"><span data-stu-id="8eebf-146">Features</span></span>

- <span data-ttu-id="8eebf-147">Cuenta de almacenamiento puede contener cualquier número de colas</span><span class="sxs-lookup"><span data-stu-id="8eebf-147">Storage account can contain any number of queues</span></span>
    
- <span data-ttu-id="8eebf-148">Cola puede contener cualquier número de mensajes (hasta que la cuenta de almacenamiento está lleno)</span><span class="sxs-lookup"><span data-stu-id="8eebf-148">Queue can contain any number of messages (until the storage account is full)</span></span>
    
- <span data-ttu-id="8eebf-149">La cola de mensajes automáticamente se eliminan después de siete días si no se recuperan o elimina una aplicación</span><span class="sxs-lookup"><span data-stu-id="8eebf-149">Queue messages are automatically deleted after seven days if not retrieved and deleted by an application</span></span>
    
- <span data-ttu-id="8eebf-150">Los mensajes pueden tener hasta 64 KB de tamaño</span><span class="sxs-lookup"><span data-stu-id="8eebf-150">Messages may be up to 64 KB in size</span></span>
    
- <span data-ttu-id="8eebf-151">Proteger a nivel de la cuenta de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="8eebf-151">Secured at storage account level</span></span>
    
- <span data-ttu-id="8eebf-152">Las colas están diseñadas para pasar mensajes de control, los datos sin procesar no</span><span class="sxs-lookup"><span data-stu-id="8eebf-152">Queues are intended to pass control messages, not raw data</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="8eebf-153">Usos comunes</span><span class="sxs-lookup"><span data-stu-id="8eebf-153">Common uses</span></span>

- <span data-ttu-id="8eebf-154">Crear un trabajo pendiente para procesar de forma asincrónica</span><span class="sxs-lookup"><span data-stu-id="8eebf-154">Create a backlog of work to process asynchronously</span></span>
    
- <span data-ttu-id="8eebf-155">Procesamiento de los mensajes de registro</span><span class="sxs-lookup"><span data-stu-id="8eebf-155">Processing log messages</span></span>
    
- <span data-ttu-id="8eebf-156">Desacoplar aplicaciones</span><span class="sxs-lookup"><span data-stu-id="8eebf-156">Decouple applications</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="8eebf-157">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="8eebf-157">Key storage scenarios</span></span>

- <span data-ttu-id="8eebf-158">Distribuir eventos</span><span class="sxs-lookup"><span data-stu-id="8eebf-158">Distribute events</span></span>
    
### <a name="resources"></a><span data-ttu-id="8eebf-159">Recursos</span><span class="sxs-lookup"><span data-stu-id="8eebf-159">Resources</span></span>

<span data-ttu-id="8eebf-160">Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span><span class="sxs-lookup"><span data-stu-id="8eebf-160">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179353.aspx).</span></span>
  
<span data-ttu-id="8eebf-161">Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="8eebf-161">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="azure-storage-tables"></a><span data-ttu-id="8eebf-162">Almacenamiento de Azure (tablas)</span><span class="sxs-lookup"><span data-stu-id="8eebf-162">Azure Storage (tables)</span></span>

### <a name="features"></a><span data-ttu-id="8eebf-163">Características</span><span class="sxs-lookup"><span data-stu-id="8eebf-163">Features</span></span>

- <span data-ttu-id="8eebf-164">Mejor para conjuntos de datos semiestructurados</span><span class="sxs-lookup"><span data-stu-id="8eebf-164">Best for semi-structured datasets</span></span>
    
- <span data-ttu-id="8eebf-165">Normalmente, un costo menor que SQL tradicional</span><span class="sxs-lookup"><span data-stu-id="8eebf-165">Typically lower cost than traditional SQL</span></span>
    
- <span data-ttu-id="8eebf-166">Es muy rápida si la consulta de clave, lento si la consulta de valor</span><span class="sxs-lookup"><span data-stu-id="8eebf-166">Very fast if querying for key, slow if querying for value</span></span>
    
- <span data-ttu-id="8eebf-167">Escalable masivamente; cualquier cantidad de tablas hasta los límites de la cuenta de almacenamiento</span><span class="sxs-lookup"><span data-stu-id="8eebf-167">Massively scalable; any amount of tables up to the limits of the storage account</span></span>
    
- <span data-ttu-id="8eebf-168">Accesible a través de la API de REST, protocolo oData limitado, .NET</span><span class="sxs-lookup"><span data-stu-id="8eebf-168">Accessible through REST API, limited oData protocol, .NET</span></span>
    
- <span data-ttu-id="8eebf-169">Deben ser serializados valores</span><span class="sxs-lookup"><span data-stu-id="8eebf-169">Values must be serialized</span></span>
    
### <a name="common-uses"></a><span data-ttu-id="8eebf-170">Usos comunes</span><span class="sxs-lookup"><span data-stu-id="8eebf-170">Common uses</span></span>

- <span data-ttu-id="8eebf-171">Datos de usuario para aplicaciones web</span><span class="sxs-lookup"><span data-stu-id="8eebf-171">User data for web applications</span></span>
    
- <span data-ttu-id="8eebf-172">Libretas de direcciones</span><span class="sxs-lookup"><span data-stu-id="8eebf-172">Address books</span></span>
    
- <span data-ttu-id="8eebf-173">Información del dispositivo</span><span class="sxs-lookup"><span data-stu-id="8eebf-173">Device information</span></span>
    
### <a name="key-storage-scenarios"></a><span data-ttu-id="8eebf-174">Escenarios de almacenamiento de claves</span><span class="sxs-lookup"><span data-stu-id="8eebf-174">Key storage scenarios</span></span>

- <span data-ttu-id="8eebf-175">Administrar datos</span><span class="sxs-lookup"><span data-stu-id="8eebf-175">Manage data</span></span>
    
### <a name="resources"></a><span data-ttu-id="8eebf-176">Recursos</span><span class="sxs-lookup"><span data-stu-id="8eebf-176">Resources</span></span>

<span data-ttu-id="8eebf-177">Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span><span class="sxs-lookup"><span data-stu-id="8eebf-177">For additional information, click [here](https://msdn.microsoft.com/library/azure/dd179463.aspx).</span></span>
  
<span data-ttu-id="8eebf-178">Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).</span><span class="sxs-lookup"><span data-stu-id="8eebf-178">For cost information, click [here](http://azure.microsoft.com/pricing/details/storage/).</span></span>
  
## <a name="microsoft-azure-storage-recommendations"></a><span data-ttu-id="8eebf-179">Recomendaciones de almacenamiento de información de Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="8eebf-179">Microsoft Azure Storage recommendations</span></span>

<span data-ttu-id="8eebf-180">Al diseñar la solución de almacenamiento de información personalizada con el almacenamiento de Azure, tenga en cuenta lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8eebf-180">When designing your custom storage solution with Azure Storage, keep the following in mind:</span></span>
  
- <span data-ttu-id="8eebf-181">Sacar provecho de varias cuentas de almacenamiento para una mayor escalabilidad, ya sea de mayor tamaño (> 100 TB) o para un mayor rendimiento (5.000 > operaciones por segundo).</span><span class="sxs-lookup"><span data-stu-id="8eebf-181">Leverage multiple storage accounts for greater scalability, either for increased size (> 100 TB) or for more throughput (> 5,000 operations per second).</span></span>
    
- <span data-ttu-id="8eebf-182">Diseño de la capacidad para agregar cuentas de almacenamiento adicionales como un cambio de configuración, no como un cambio de código.</span><span class="sxs-lookup"><span data-stu-id="8eebf-182">Design the ability for adding additional storage accounts as a configuration change, not as a code change.</span></span>
    
- <span data-ttu-id="8eebf-183">Seleccione detenidamente partición funciones para el almacenamiento de la tabla habilitar la escala deseada en términos de rendimiento de insertar y consulta.</span><span class="sxs-lookup"><span data-stu-id="8eebf-183">Carefully select partitioning functions for table storage to enable the desired scale in terms of insert and query performance.</span></span>
    
- <span data-ttu-id="8eebf-184">Elija los nombres de columna corto para las propiedades de la tabla como los metadatos (los nombres de propiedades) son almacenado dentro de banda (los nombres de columna también cuentan para el tamaño máximo de fila de 1 MB).</span><span class="sxs-lookup"><span data-stu-id="8eebf-184">Choose short column names for table properties as the metadata (property names) are stored in-band (the column names also count towards the maximum row size of 1 MB).</span></span>
    
- <span data-ttu-id="8eebf-185">Cuando sea posible, las operaciones en almacenamiento de información de lote.</span><span class="sxs-lookup"><span data-stu-id="8eebf-185">When possible, batch operations into storage.</span></span>
    
- <span data-ttu-id="8eebf-186">Forma agresiva información de caché en la base de datos de configuración en una memoria caché distribuida.</span><span class="sxs-lookup"><span data-stu-id="8eebf-186">Aggressively cache information in the configuration database into a distributed cache.</span></span>
    
- <span data-ttu-id="8eebf-187">Si depende de tener un segmento de algunos de los datos disponibles en la memoria caché de rendimiento de la aplicación o la confiabilidad, la aplicación debe rechazar las solicitudes entrantes hasta que se rellenan previamente la memoria caché.</span><span class="sxs-lookup"><span data-stu-id="8eebf-187">If application performance or reliability is dependent on having a certain segment of data available in the cache, your application should refuse incoming requests until the cache has been pre-populated.</span></span>
    
- <span data-ttu-id="8eebf-188">Particiones de los datos en verticalmente (por tabla) u horizontalmente (tabla de segmento a través de varios shards) para repartir la carga entre varias bases de datos.</span><span class="sxs-lookup"><span data-stu-id="8eebf-188">Partition the data in either vertically (by table) or horizontally (segment table across multiple shards) to spread the load across multiple databases.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="8eebf-189">Vea también</span><span class="sxs-lookup"><span data-stu-id="8eebf-189">See Also</span></span>

[<span data-ttu-id="8eebf-190">Almacenamiento de Microsoft Cloud para arquitectos empresariales</span><span class="sxs-lookup"><span data-stu-id="8eebf-190">Microsoft Cloud Storage for Enterprise Architects</span></span>](microsoft-cloud-storage-for-enterprise-architects.md)
  
[<span data-ttu-id="8eebf-191">Recursos de arquitectura de TI de la nube de Microsoft</span><span class="sxs-lookup"><span data-stu-id="8eebf-191">Microsoft Cloud IT architecture resources</span></span>](microsoft-cloud-it-architecture-resources.md)

[<span data-ttu-id="8eebf-192">Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI</span><span class="sxs-lookup"><span data-stu-id="8eebf-192">Microsoft's Enterprise Cloud Roadmap: Resources for IT Decision Makers</span></span>](https://sway.com/FJ2xsyWtkJc2taRD)



