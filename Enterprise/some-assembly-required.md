---
title: Se necesitan algunos ensamblados
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
ms.assetid: ccf1b8b3-0d50-4c66-b314-f480245fad5e
description: 'Resumen: Obtenga los detalles en el conjunto de opciones de almacenamiento en la nube que puede usar para crear la solución de almacenamiento de información personalizada.'
ms.openlocfilehash: 2c80b0cdf0829e80a7916133ee51a45c91b96efa
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915525"
---
# <a name="some-assembly-required"></a>Se necesitan algunos ensamblados

 **Resumen:** Para obtener información sobre el conjunto de nube opciones de almacenamiento que puede usar para crear la solución de almacenamiento de información personalizada.
  
Soluciones de almacenamiento de "Algunos ensamblado requerido":
  
- Usar los servicios existentes como punto de partida para su solución de almacenamiento.
    
- Codificación o que requieren una configuración.
    
- Se pueden personalizar para satisfacer sus necesidades.
    
En las secciones siguientes se describen los detalles de cada solución de almacenamiento "Algunos ensamblado necesario".
  
## <a name="azure-content-delivery-network"></a>Red de entrega de contenido de Azure

### <a name="features"></a>Características

- Análisis avanzados y en tiempo real
    
- Seguridad sólida frente a DDoS
    
- Obtiene contenido automáticamente desde un sitio Web de Azure o servicio de nube de Azure una vez configurada la integración
    
- Nueva asociación con Akamai
    
- Puede controlar los picos de tráfico repentino y cargas elevadas
    
### <a name="common-uses"></a>Usos comunes

- Distribuir audio, vídeo, aplicaciones, imágenes y otros archivos más rápido y más confiable a los clientes mediante el uso de los servidores que son más cercanos a ellos
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
- Administración de vídeos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://azure.microsoft.com/services/cdn/).
  
Para obtener información de costo, haga clic en [aquí](https://azure.microsoft.com/pricing/details/cdn/).
  
## <a name="hdinsight"></a>HdInsight

### <a name="features"></a>Características

- Distribución de Apache Hadoop con tecnología de la nube servicio A datos lago
    
- Incrementar la escalabilidad a petabytes a petición
    
- Procesar datos no estructurados y semiestructurados desarrollar en Java, .NET y mucho más
    
- Omitir la compra y el mantenimiento de hardware
    
- Conectar los clústeres de Hadoop local con la nube
    
- Flexibilidad para implementar proyectos de Hadoop arbitrarios a través de secuencias de comandos personalizadas (por ejemplo, R, Giraph, Solr)
    
### <a name="common-uses"></a>Usos comunes

- Cargas de trabajo de análisis de datos
    
- Marco de procesamiento de datos en memoria de datos grandes (Spark)
    
- Procesamiento de la secuencia en tiempo real (tormenta)
    
- Procesamiento de transacciones grandes (OLTP) de datos no relacionales (HBase)
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://azure.microsoft.com/services/hdinsight/).
  
Para obtener información de costo, haga clic en [aquí](https://azure.microsoft.com/pricing/details/hdinsight/).
  
## <a name="azure-sql-database"></a>Base de datos SQL de Azure

### <a name="features"></a>Características

- Optimizado para reducir los costos y administración
    
- Automática alta disponibilidad, recuperación ante desastres y actualización
    
- Se recomienda para las organizaciones administrar cientos o miles de bases de datos de hasta 1 TB en tamaño
    
- Técnicas de sharding pueden dividir datos entre bases de datos de almacenamiento mayor
    
- Expandir base de datos con SQL Server 2016
    
### <a name="common-uses"></a>Usos comunes

- Nuevas aplicaciones diseñadas en la nube con datos relacionales
    
- Procesamiento de datos a través de conjuntos de datos muy estructurados, esquemáticos con relaciones
    
- Datos espaciales o tipos de datos enriquecidos
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="elastic-database"></a>Base de datos de escalabilidad

Uso de los recursos de SQL Azure prácticamente ilimitados de base de datos cuando:
  
- La cantidad total de datos es demasiado grande para ajustarse a las restricciones de una sola base de datos.
    
- El rendimiento de las transacciones de la carga de trabajo general supera las capacidades de una sola base de datos.
    
- Los inquilinos requieren el aislamiento físico entre sí, por lo que se necesitan bases de datos independientes para cada inquilino.
    
- Las distintas secciones de una base de datos deben residir en diferentes geografías para cumplimiento de normas, el rendimiento o geopolíticos motivos.
    
Con la escala vertical, puede cambiar la edición por rendimiento de nivel de base de datos de Azure o mediante el uso de grupos de servidores de base de datos elástico.
  
![Escalado vertical proporcionado por Azure SQL Database.](media/Storage-Poster/CloudStor-VertScale.png)
  
Ajuste de escala horizontal, puede agregar nuevas bases de datos según sea necesario.
  
![Escalado horizontal proporcionado por Azure SQL Database.](media/Storage-Poster/CloudStor-HorizScale.png)
  
Haga clic [aquí](https://docs.microsoft.com/azure/sql-database/sql-database-elastic-scale-introduction) para obtener más información.
  
### <a name="stretch-database-with-sql-server-2016"></a>Stretch Database con SQL Server 2016

Expandir base de datos es una característica de SQL Server 2016 que le permite transparente y segura mover datos pasiva, como datos de negocio cerrado en una tabla de gran tamaño que contiene la información de pedidos, a una base de datos de SQL estiramiento en Azure. Cuando se estira, el contenido de una instancia de SQL Server, una base de datos o incluso una sola tabla es la combinación de datos locales en el servidor de SQL Server 2016 y datos remotos en Azure. Datos que se pasa a ser candidato para extender automáticamente se mueven a Azure por 2016 de SQL Server.
  
![Stretch Database con SQL Server 2016.](media/Storage-Poster/CloudStor-Stretch.png)
  
Las consultas del usuario que incluyen los datos históricos se reenvían de manera transparente a Azure SQL Stretch Database. No es necesario que las consultas se vuelvan a escribir, aunque se extienda la tabla.
  
Stretch Database proporciona una opción rentable para el almacenamiento a largo plazo y el acceso transparente a los datos históricos. También soluciona problemas de rendimiento y disponibilidad que surgen cuando las tablas son muy grandes.
  
Haga clic [aquí](https://msdn.microsoft.com/library/dn935011.aspx) para obtener más información.
  
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](http://azure.microsoft.com/services/sql-database/).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/sql-database/).
  
## <a name="azure-cosmos-db"></a>DB Cosmos Azure

### <a name="features"></a>Características

- Garantiza una latencia baja, SLA de disponibilidad del 99,99% con escala ilimitada, escalabilidad de almacenamiento y el rendimiento
    
- Todos los datos se replican globalmente en cualquier número de regiones con conmutación por error transparente y cuatro niveles de coherencia bien definido
    
- Indiza automáticamente todos los datos sin necesidad de esquemas o índices secundarios
    
- Consultas SQL Rich y JavaScript y las transacciones de varios artículos
    
### <a name="common-uses"></a>Usos comunes

- IoT, Mobile y Social
    
- Para juegos
    
- Comercial
    
- Administración de contenido
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="cosmos-db-vs-azure-tables-vs-azure-sql-database"></a>Base de datos SQL de COSMOS DB en comparación con Azure tablas en comparación con Azure

Atributos comunes de Cosmos DB, almacenamiento de tablas de Azure y base de datos de SQL Azure:
  
- SLA de disponibilidad 99,99
    
- Servicios de base de datos totalmente administrados
    
- Certificación ISO 27001, HIPAA y modelo de la UE cláusulas compatibles con
    
En la siguiente tabla se muestra los atributos poco frecuentes de base de datos de SQL Azure, almacenamiento de tablas de Azure y Azure Cosmos DB.
  
![Atributos infrecuentes de Cosmos DB frente a tablas de Azure frente a Azure SQL Database](media/Storage-Poster/CloudStor-Table.png)
  
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](http://azure.microsoft.com/services/documentdb/).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/documentdb/).
  
## <a name="azure-media-services"></a>Servicios de multimedia de Azure

### <a name="features"></a>Características

- Vídeo en la entrega de propuestas (VOD) con escala y en vivo
    
- Codificación de alta disponibilidad y transmisión por secuencias
    
- Es compatible con Flash, iOS, Android, HTML5 y Xbox
    
- Soporte DRM certificado Studio
    
- Monetización de contenido enriquecido
    
- Amplio ecosistema de socios previamente integrados
    
### <a name="common-uses"></a>Usos comunes

- Codificar, almacenar y en secuencia de audio y vídeo en escala
    
- Transmisión por secuencias en tiempo real y VOD
    
- Administración de contenido de vídeo optimizada
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administración de vídeos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://azure.microsoft.com/services/media-services/).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/media-services/).
  
## <a name="azure-redis-cache"></a>Memoria caché Redis Azure

### <a name="features"></a>Características

- Servidor seguro y dedicado Redis con alta disponibilidad con la replicación de datos y conmutación por error administrado por Microsoft
    
- Se recomienda para cualquier aplicación necesidad de alto rendimiento
    
- Está disponible en tamaños de hasta 530 GB y más allá (con Premium y sharding automática)
    
- Persistencia Redis persiste en memoria caché de datos para el almacenamiento de Azure
    
- Redis Clustering permite conseguir el rendimiento y la escala máxima
    
- Aislamiento de seguridad y red mejorado con soporte de red Virtual de Azure
    
### <a name="common-uses"></a>Usos comunes

- Búsqueda inversa de los datos en cualquier servicio de almacenamiento en Azure, como DB Cosmos y base de datos de SQL Azure
    
- Contenido sincronizado desde otros almacenes de datos
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Datos de la memoria caché
    
- Agente de mensaje para las aplicaciones de alto rendimiento
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](http://azure.microsoft.com/services/cache/).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/cache/).
  
## <a name="sql-server-on-an-azure-vm"></a>SQL Server en una máquina virtual de Azure

### <a name="features"></a>Características

- SQL Server que se ejecuta como una aplicación instalada en una máquina virtual de Azure
    
- Uso de una imagen de la galería con SQL Server instalado o Traer su propia licencia de SQL Server
    
### <a name="common-uses"></a>Usos comunes

- Administrar los datos de aplicaciones
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](http://azure.microsoft.com/services/virtual-machines/).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/virtual-machines/).
  
## <a name="storsimple"></a>StorSimple

### <a name="features"></a>Características

- Híbrido de empresa escalable, almacenamiento SAN con SSD y la unidad de disco duro de la matriz de almacenamiento local híbrido, con el almacenamiento en la nube como una extensión integrada de la solución
    
- Desduplicación en línea, compresión, interconexión automática y cifrado no estructurado y punto y los datos estructurados
    
- Protección de datos automatizada fuera del sitio mediante instantáneas de la nube
    
- Recuperación ante desastres altamente eficiente, independiente de la ubicación
    
- Movilidad de datos para los datos de la empresa con StorSimple dispositivo Virtual en Azure
    
### <a name="common-uses"></a>Usos comunes

- Administrar el crecimiento de los datos relacionados con recursos compartidos de archivos, archivos y otros repositorios de datos
    
- Fuera del sitio datos protección y recuperación ante desastres para recursos compartidos de archivos, las máquinas virtuales, SQL y SharePoint (mediante el almacenamiento remoto de blobs)
    
- Utilizar las instantáneas de la nube para clonar datos en Azure y aumentar la agilidad del negocio.
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
- Colaborar
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](http://azure.microsoft.com/services/storsimple/).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storsimple/).
  
## <a name="azure-sql-data-warehouse"></a>Almacén de datos SQL Azure

### <a name="features"></a>Características

- Almacén de datos de escalabilidad que escala hasta petabytes hasta 32 consultas simultáneas
    
- Administrar grandes volúmenes de datos estructurados con fast analytics dinámicamente aumentar y hundir compute en segundos
    
- Admite el cifrado de datos transparente
    
- Copia de seguridad cada 8 horas durante 7 días
    
### <a name="common-uses"></a>Usos comunes

- Informes de ventas
    
- Informes de uso
    
- Gran cantidad de datos
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://azure.microsoft.com/services/sql-data-warehouse/).
  
Para obtener información de costo, haga clic en [aquí](https://azure.microsoft.com/pricing/details/sql-data-warehouse/).
  
## <a name="azure-data-lake-store"></a>Almacén de lago de datos de Azure

### <a name="features"></a>Características

- Un repositorio de gran escala para cargas de trabajo de análisis de datos grande
    
- Un sistema de archivos distribuido en Hadoop para la nube
    
- Sin límites en el tamaño de archivo fijos
    
- Ningún límite fijo en tamaño de la cuenta
    
- Datos estructurados y sin estructurar en su formato nativo.
    
- Rendimiento masivo para incrementar el rendimiento analítico
    
- Duración alta, disponibilidad y confiabilidad (SLA 99,9% empresariales y soporte técnico las 24 horas 7)
    
- Control de acceso de Azure Active Directory
    
### <a name="common-uses"></a>Usos comunes

- Repositorio de toda la empresa para almacenar cada tipo de datos recopilados en un solo lugar
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://azure.microsoft.com/services/data-lake-store/).
  
Para obtener información de costo, haga clic en [aquí](https://azure.microsoft.com/pricing/details/data-lake-store/).
  
## <a name="next-step"></a>Paso siguiente

Revise las opciones de almacenamiento en la nube [generarlo desde el principio de la copia de seguridad](build-from-the-ground-up.md) .
  
## <a name="see-also"></a>Vea también

[Almacenamiento de Microsoft Cloud para arquitectos empresariales](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)



