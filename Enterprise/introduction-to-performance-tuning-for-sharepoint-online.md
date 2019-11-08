---
title: Introducción al ajuste del rendimiento para SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/22/2018
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: En este artículo se explica qué aspectos específicos debe tener en cuenta al diseñar páginas para obtener el mejor rendimiento en SharePoint Online.
ms.openlocfilehash: 3c2c6ccc58659aceaaf831b97eb8c4c05141afce
ms.sourcegitcommit: fa900775790eb369db1983cd3868b628b699f145
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38033406"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Introducción al ajuste del rendimiento para SharePoint Online

En este artículo se explica qué aspectos específicos debe tener en cuenta al diseñar páginas para obtener el mejor rendimiento en SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>Métricas de SharePoint Online

Las siguientes métricas generales para SharePoint Online proporcionan datos del mundo real sobre el rendimiento:
  
- Velocidad de carga de páginas
    
- Número de viajes de ida y vuelta necesarios por página
    
- Problemas con el servicio
    
- Otras cosas que causan una degradación del rendimiento
    
### <a name="conclusions-reached-because-of-the-data"></a>Se han alcanzado conclusiones a causa de los datos

Los datos nos dicen:
  
- La mayoría de las páginas se ejecutan correctamente en SharePoint Online.
    
- Las páginas no personalizadas se cargan muy rápidamente.
    
- OneDrive para la empresa, los sitios de grupo y las páginas del sistema, como _layouts, etc., se cargan rápidamente.
    
- El 1% más lento de las páginas de SharePoint Online tarda más de 5.000 milisegundos en cargarse.
    
Una prueba comparativa sencilla que puede usar sería medir el rendimiento comparando el tiempo de carga de su propio portal con el tiempo de carga de la Página principal de OneDrive para la empresa, ya que usa pocas características personalizadas. Por lo general, este será el primer paso que le pedirá que complete la solución de problemas de rendimiento de la red.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Usar una cuenta de usuario estándar al comprobar el rendimiento

Un administrador de la colección de sitios, el propietario del sitio, el editor o el colaborador pertenecen a grupos de seguridad adicionales, tienen permisos adicionales y, por tanto, tienen elementos adicionales que SharePoint carga en una página.
  
Esto es aplicable a SharePoint local y SharePoint Online, pero en un escenario local las diferencias no se apreciarán tan fácilmente como en SharePoint Online.
  
Para evaluar correctamente la forma en que se realizará una página para los usuarios, debe usar una cuenta de usuario estándar para evitar cargar los controles de creación y el tráfico adicional relacionado con los grupos de seguridad.
  
## <a name="connection-categories-for-performance-tuning"></a>Categorías de conexión para ajustar el rendimiento

Puede clasificar las conexiones entre el servidor y el usuario en tres componentes principales. Tenga en cuenta lo que debe tener en el diseño de páginas de SharePoint Online para obtener información sobre los tiempos de carga.
  
- **Servidor** de Los servidores que hospeda Microsoft en los centros de recursos.
    
- **Red** La red de Microsoft, Internet y su red local entre el centro de recursos y los usuarios.
    
- **Explorador** Dónde se carga la página.
    
Dentro de estas tres conexiones, normalmente hay cinco motivos por los que se produce un 95% de páginas lentas. Cada uno de estos motivos se describe en este artículo:
  
- Problemas de navegación
    
- Resumen de contenido
    
- Archivos grandes
    
- Muchas solicitudes al servidor
    
- Procesamiento de elementos Web
    
### <a name="server-connection"></a>Conexión de servidor

Muchos de los problemas que afectan al rendimiento con SharePoint local también se aplican a SharePoint Online.
  
Como cabría esperar, tiene mucho más control sobre el rendimiento de los servidores con SharePoint local. Con las cosas de SharePoint Online es un poco diferente. Cuanto más trabajo realice un servidor, más tiempo se tardará en representar una página. Con SharePoint, el mayor culpable de este aspecto son las páginas complejas con varios elementos Web.
  
SharePoint Server local
  
![Captura de pantalla del servidor local](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Captura de pantalla del servidor en línea](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Con SharePoint Online, algunas solicitudes de página pueden acabar, en realidad, en llamar a varios servidores. Podría acabar con una matriz de solicitudes entre servidores para una solicitud individual. Estas interacciones son costosas desde el punto de vista de carga de páginas y harán que sean más lentas.
  
Algunos ejemplos de estas interacciones de servidor a servidor son:
  
- Servidores web a SQL Server
    
- Web a servidores de aplicaciones
    
Lo otro que puede ralentizar las interacciones del servidor son las faltas de caché. A diferencia de SharePoint local, hay muy poca probabilidad de que llegue al mismo servidor para una página que ha visitado anteriormente; Esto hace que el almacenamiento en caché de objetos sea obsoleto.
  
### <a name="network-connection"></a>Conexión de red 

Con SharePoint local que no hace uso de una WAN, puede usar una conexión de alta velocidad entre el centro de recursos y los usuarios finales. Por lo general, las cosas son fáciles de administrar desde el punto de vista de la red.
  
Con SharePoint Online, hay algunos factores más que hay que tener en cuenta; por ejemplo:
  
- The Microsoft Network
    
- Internet
    
- El ISP
    
Independientemente de la versión de SharePoint (y la red) que use, lo que normalmente hará que la red esté ocupada incluye:
  
- Gran carga
    
- Muchos archivos
    
- Gran distancia física con el servidor
    
Una característica que puede aprovechar en SharePoint Online es la red de entrega de contenido (CDN) de Microsoft. Una CDN es básicamente una colección distribuida de servidores implementados en varios centros de recursos. Con una red CDN, el contenido de las páginas puede alojarse en un servidor cercano al cliente incluso si el cliente se encuentra alejado del servidor de SharePoint de origen. Microsoft lo utilizará más en el futuro para almacenar instancias locales de páginas que no se pueden personalizar, por ejemplo, la Página principal de administración de SharePoint Online. Para obtener más información acerca de las CDN, vea [redes de entrega de contenido](https://docs.microsoft.com/office365/enterprise/content-delivery-networks).
  
Algo que necesita tener en cuenta pero que no puede hacer mucho por es la velocidad de conexión de su ISP. Una herramienta de prueba de velocidad simple le dirá la velocidad de conexión.
  
### <a name="browser-connection"></a>Conexión con el explorador

Hay algunos factores que se deben tener en cuenta con los exploradores Web desde el punto de vista del rendimiento.
  
La visita de páginas complejas afectará al rendimiento. La mayoría de los exploradores solo tienen una caché pequeña (alrededor de 90MB), mientras que la página web promedio suele encontrase a 1,6 MB. Esto no tarda mucho en llegar a usarse.
  
El ancho de banda también puede ser un problema. Por ejemplo, si un usuario ve vídeos en otra sesión, el rendimiento de la página de SharePoint se verá afectado. Aunque no se puede impedir que los usuarios transmitan contenido multimedia, puede controlar la forma en que se cargará una página para los usuarios.
  
Consulte los siguientes artículos para conocer las distintas técnicas de personalización de páginas de SharePoint Online y otros procedimientos recomendados para ayudarle a conseguir un rendimiento óptimo.
  
- [Opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Usar la herramienta de diagnóstico de página para SharePoint Online](page-diagnostics-for-spo.md)
    
- [Optimización de imágenes para SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Retrasar la carga de imágenes y JavaScript en SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minificación y agrupación en SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Usar redes de entrega de contenido](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Usar el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido para mejorar el rendimiento en SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Planeamiento de capacidad y pruebas de carga en SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnosticar problemas de rendimiento con SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Usar la memoria caché de objetos con SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Cómo: Evitar estar limitado o bloqueado en SharePoint Online](https://msdn.microsoft.com/library/office/dn889829.aspx)
    

