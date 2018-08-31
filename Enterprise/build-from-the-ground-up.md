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
# <a name="build-from-the-ground-up"></a>Crear desde cero

 **Resumen:** Para obtener información sobre el conjunto de nube de bloques de creación de almacenamiento que puede usar para crear su propio servicio de almacenamiento o la solución.
  
"Generarlo desde el principio" soluciones de almacenamiento de información:
  
- Permiten crear su propia solución de almacenamiento de información desde el principio. 
    
- Requiere que la programación con las API de REST.
    
- Proporcionar lo último en flexibilidad y personalización.
    
En las secciones siguientes se describen los detalles de cada opción de almacenamiento "Generarlo desde el principio".
  
## <a name="azure-storage-files"></a>Almacenamiento de Azure (archivos)

### <a name="features"></a>Características

- Resulta más sencillo mover aplicaciones heredadas a la nube
    
- Almacenamiento de blobs preferido para nuevas aplicaciones
    
- Puede montar desde una máquina virtual de Azure
    
- Puede montar local con SMB 3.0
    
- Funciona con Windows y Linux
    
- No es compatible con la autenticación basada en AD Azure o ACL (claves de la cuenta de almacenamiento de Azure proporcionan autenticación y autorización para obtener acceso al recurso compartido de archivo)
    
### <a name="common-uses"></a>Usos comunes

- Migración de aplicaciones heredadas a la nube que se basan en recursos compartidos de archivos
    
- Compartir herramientas de desarrollo y pruebas
    
- Pueden almacenar los registros de datos de diagnóstico y volcados de sucesos aplicaciones distribuidas
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Archivos de copia de seguridad
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dn166972.aspx).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-blobs"></a>Almacenamiento de Azure (BLOB)

### <a name="features"></a>Características

- Cada cuenta de almacenamiento puede contener hasta 500 TB (una sola suscripción puede tener varias cuentas de almacenamiento)
    
- Cuentas de almacenamiento se organizan en contenedores, que pueden tener la seguridad que se aplican a ellos y pueden contener BLOB
    
- BLOB de bloque está optimizado para la transmisión por secuencias y objetos de almacenar en la nube, hasta 200 GB de tamaño
    
- BLOB de página está optimizado para representar PaaS discos y admitir aleatorio escribe un tamaño de hasta 1 TB
    
- Anexar BLOB está optimizado para anexar las operaciones, 195 GB
    
- Almacenamiento de Premium proporciona más rápidas IOPS a través de almacenamiento SSD
    
### <a name="common-uses"></a>Usos comunes

- Copias de seguridad de los archivos, equipos, las bases de datos y dispositivos de imágenes y texto para las aplicaciones web
    
- Datos de configuración de aplicaciones de nube
    
- Datos grandes, como los registros y otros grandes conjuntos de datos
    
- Usos de Azure blob almacenamiento para sus propios servicios, como los discos HDInsight y una máquina virtual
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179376.aspx).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-queues"></a>Almacenamiento de Azure (colas)

### <a name="features"></a>Características

- Cuenta de almacenamiento puede contener cualquier número de colas
    
- Cola puede contener cualquier número de mensajes (hasta que la cuenta de almacenamiento está lleno)
    
- La cola de mensajes automáticamente se eliminan después de siete días si no se recuperan o elimina una aplicación
    
- Los mensajes pueden tener hasta 64 KB de tamaño
    
- Proteger a nivel de la cuenta de almacenamiento
    
- Las colas están diseñadas para pasar mensajes de control, los datos sin procesar no
    
### <a name="common-uses"></a>Usos comunes

- Crear un trabajo pendiente para procesar de forma asincrónica
    
- Procesamiento de los mensajes de registro
    
- Desacoplar aplicaciones
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Distribuir eventos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179353.aspx).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-tables"></a>Almacenamiento de Azure (tablas)

### <a name="features"></a>Características

- Mejor para conjuntos de datos semiestructurados
    
- Normalmente, un costo menor que SQL tradicional
    
- Es muy rápida si la consulta de clave, lento si la consulta de valor
    
- Escalable masivamente; cualquier cantidad de tablas hasta los límites de la cuenta de almacenamiento
    
- Accesible a través de la API de REST, protocolo oData limitado, .NET
    
- Deben ser serializados valores
    
### <a name="common-uses"></a>Usos comunes

- Datos de usuario para aplicaciones web
    
- Libretas de direcciones
    
- Información del dispositivo
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179463.aspx).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="microsoft-azure-storage-recommendations"></a>Recomendaciones de almacenamiento de información de Microsoft Azure

Al diseñar la solución de almacenamiento de información personalizada con el almacenamiento de Azure, tenga en cuenta lo siguiente:
  
- Sacar provecho de varias cuentas de almacenamiento para una mayor escalabilidad, ya sea de mayor tamaño (> 100 TB) o para un mayor rendimiento (5.000 > operaciones por segundo).
    
- Diseño de la capacidad para agregar cuentas de almacenamiento adicionales como un cambio de configuración, no como un cambio de código.
    
- Seleccione detenidamente partición funciones para el almacenamiento de la tabla habilitar la escala deseada en términos de rendimiento de insertar y consulta.
    
- Elija los nombres de columna corto para las propiedades de la tabla como los metadatos (los nombres de propiedades) son almacenado dentro de banda (los nombres de columna también cuentan para el tamaño máximo de fila de 1 MB).
    
- Cuando sea posible, las operaciones en almacenamiento de información de lote.
    
- Forma agresiva información de caché en la base de datos de configuración en una memoria caché distribuida.
    
- Si depende de tener un segmento de algunos de los datos disponibles en la memoria caché de rendimiento de la aplicación o la confiabilidad, la aplicación debe rechazar las solicitudes entrantes hasta que se rellenan previamente la memoria caché.
    
- Particiones de los datos en verticalmente (por tabla) u horizontalmente (tabla de segmento a través de varios shards) para repartir la carga entre varias bases de datos.
    
## <a name="see-also"></a>Vea también

[Almacenamiento de Microsoft Cloud para arquitectos empresariales](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)



