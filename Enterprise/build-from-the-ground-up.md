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
ms.openlocfilehash: be7ea3e7526115f1a983ec89f2afeb5d130daee1
ms.sourcegitcommit: d1a1480982c773f2241cb17f85072be8724ea841
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/09/2018
---
# <a name="build-from-the-ground-up"></a>Crear desde el principio

 **Resumen:** Obtenga los detalles en el conjunto de la nube de bloques de creación de almacenamiento de información que puede utilizar para crear su propio servicio de almacenamiento o la solución.
  
"Generarlo desde el principio" soluciones de almacenamiento de información:
  
- Le permiten crear su propia solución de almacenamiento de información desde el principio. 
    
- Requiere una programación mediante las API del resto.
    
- Proporcionar lo último en flexibilidad y personalización.
    
Las secciones siguientes describen los detalles de cada opción de almacenamiento "Crear desde cero".
  
## <a name="azure-storage-files"></a>Almacenamiento de Azure (archivos)

### <a name="features"></a>Características

- Resulta más fácil mover aplicaciones heredadas a la nube
    
- Almacenamiento de blobs preferido para nuevas aplicaciones
    
- Puede montar desde una máquina virtual Azure
    
- Puede montar locales con SMB 3.0
    
- Funciona con Linux y Windows
    
- No admite autenticación AD Azure o ACL (claves de almacenamiento de Azure cuenta proporcionan autenticación y autorización para obtener acceso al recurso compartido de archivo)
    
### <a name="common-uses"></a>Usos comunes

- Migrar aplicaciones heredadas a la nube que se basan en recursos compartidos de archivos
    
- Compartir herramientas de desarrollo y pruebas
    
- Aplicaciones distribuidas pueden almacenar registros de datos de diagnóstico y volcados de sucesos
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Archivos de copia de seguridad
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dn166972.aspx).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-blobs"></a>Almacenamiento de Azure (BLOB)

### <a name="features"></a>Características

- Cada cuenta de almacenamiento puede contener hasta 500 TB (una suscripción puede tener varias cuentas de almacenamiento)
    
- Cuentas de almacenamiento se organizan en contenedores, que pueden tener la seguridad aplicada a ellos y pueden contener objetos binarios
    
- BLOB de bloque está optimizado para la transmisión y almacenamiento de nube objetos hasta 200 GB de tamaño
    
- Blobs de página están optimizados para que representan discos PaaS y escribe apoyando aleatorio, tamaño de hasta 1 TB
    
- Anexar objetos binarios están optimizados para anexar las operaciones, 195 GB
    
- Almacenamiento de Premium proporciona más rápidos IOPS a través del almacenamiento SSD
    
### <a name="common-uses"></a>Usos comunes

- Copias de seguridad de archivos, equipos, bases de datos y dispositivos de imágenes y texto para aplicaciones web
    
- Datos de configuración de aplicaciones de nube
    
- Datos grandes, como los registros y otros conjuntos de datos grandes
    
- Blob de Azure utiliza almacenamiento de información para sus propios servicios, como los discos de máquinas virtuales y HDInsight
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179376.aspx).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-queues"></a>Almacenamiento de Azure (colas)

### <a name="features"></a>Características

- Cuenta de almacenamiento puede contener cualquier número de colas
    
- Cola puede contener cualquier número de mensajes (hasta que la cuenta de almacenamiento está lleno)
    
- La cola de mensajes automáticamente se eliminan transcurridos siete días si no recuperada y eliminada por una aplicación
    
- Mensajes pueden ser de hasta 64 KB de tamaño
    
- Protegidos a nivel de cuenta de almacenamiento
    
- Las colas se van a pasar mensajes de control, los datos sin procesar no
    
### <a name="common-uses"></a>Usos comunes

- Crear un registro de trabajo para procesar de forma asincrónica
    
- Procesamiento de mensajes de registro
    
- Desacoplar aplicaciones
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Distribuir eventos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179353.aspx).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="azure-storage-tables"></a>Almacenamiento de Azure (tablas)

### <a name="features"></a>Características

- Mejor los conjuntos de datos semiestructurados
    
- Normalmente un coste menor que SQL tradicional
    
- Muy rápida si la consulta de clave, lento si la consulta de valor
    
- Escalable masivamente; cualquier cantidad de tablas hasta los límites de la cuenta de almacenamiento
    
- Accesible a través de la API de REST, protocolo oData limitado, .NET
    
- Los valores deben serializarse.
    
### <a name="common-uses"></a>Usos comunes

- Datos de usuario para aplicaciones web
    
- Libretas de direcciones
    
- Información del dispositivo
    
### <a name="key-storage-scenarios"></a>Escenarios de almacenamiento de claves

- Administrar datos
    
### <a name="resources"></a>Recursos

Para obtener información adicional, haga clic en [aquí](https://msdn.microsoft.com/library/azure/dd179463.aspx).
  
Para obtener información de costo, haga clic en [aquí](http://azure.microsoft.com/pricing/details/storage/).
  
## <a name="microsoft-azure-storage-recommendations"></a>Recomendaciones de almacenamiento de Azure de Microsoft

Al diseñar su solución de almacenamiento de información personalizada con el almacenamiento de Azure, tenga en cuenta lo siguiente:
  
- Aproveche varias cuentas de almacenamiento de información para una mayor escalabilidad, para el aumento de tamaño (> 100 TB) o para un mayor rendimiento (> 5.000 operaciones por segundo).
    
- Diseño de la capacidad para agregar cuentas de almacenamiento adicionales como un cambio de configuración, no como un cambio de código.
    
- Elija cuidadosamente las funciones de partición para el almacenamiento de la tabla habilitar la escala deseada en términos de rendimiento de inserción y consulta.
    
- Elija nombres de columna cortos para propiedades como los metadatos (nombres de propiedad) de la tabla están almacenado dentro de banda (los nombres de columna también cuentan para el tamaño máximo de fila de 1 MB).
    
- Cuando sea posible, las operaciones en el almacenamiento de información de lote.
    
- Agresivamente caché la información de la base de datos de configuración en una memoria caché distribuida.
    
- Si depende de tener un cierto segmento de datos disponibles en la caché de aplicación rendimiento o la confiabilidad, la aplicación debe rechazar las solicitudes entrantes hasta que la memoria caché ha sido rellenada.
    
- Dividir los datos en vertical (por tabla) u horizontalmente (tabla de segmentos en varios fragmentos) para repartir la carga entre varias bases de datos.
    
## <a name="see-also"></a>Consulte también

[Almacenamiento de Microsoft Cloud para arquitectos empresariales](microsoft-cloud-storage-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)



