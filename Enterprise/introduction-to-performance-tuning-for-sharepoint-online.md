---
title: Introducción al ajuste del rendimiento para SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/22/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 81c4be5f-327e-435d-a568-526d68cffef0
description: En este artículo se explica qué aspectos específicos que debe tener en cuenta cuando se diseñan las páginas para obtener el mejor rendimiento en SharePoint Online.
ms.openlocfilehash: 07938770d711477126f78fc583e8d2533ba5c1d1
ms.sourcegitcommit: ba91a1d2d785c1df425617b309fec2edc093793a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "26219880"
---
# <a name="introduction-to-performance-tuning-for-sharepoint-online"></a>Introducción al ajuste del rendimiento para SharePoint Online

En este artículo se explica qué aspectos específicos que debe tener en cuenta cuando se diseñan las páginas para obtener el mejor rendimiento en SharePoint Online.
     
## <a name="sharepoint-online-metrics"></a>Métricas de SharePoint Online

Las siguientes métricas amplias para SharePoint Online proporcionan datos reales sobre el rendimiento:
  
- La velocidad de carga de páginas
    
- Cuántos recorridos de idas y vuelta se requieren por página
    
- Problemas con el servicio
    
- Otras cuestiones que provocan una degradación del rendimiento
    
### <a name="conclusions-reached-because-of-the-data"></a>Conclusiones debido a los datos

Los datos indican lo siguiente:
  
- La mayoría de las páginas tienen un buen rendimiento en SharePoint Online.
    
- Las páginas que no han sido personalizadas se cargan muy rápidamente.
    
- OneDrive para la Empresa, sitios de grupo y páginas del sistema, como _layouts, etc., se cargan rápidamente.
    
- El 1 % más lento de las páginas de SharePoint Online tardan más de 5.000 milisegundos en cargarse.
    
Una prueba comparativa simple que puede usar sería medir el rendimiento comparando el tiempo de carga de su propio portal con el tiempo de carga de la página de inicio de OneDrive para la Empresa ya que usa pocas características personalizadas. Este suele ser el primer paso que el Soporte técnico le pedirá que complete al solucionar problemas de rendimiento de red.
  
## <a name="use-a-standard-user-account-when-checking-performance"></a>Use una cuenta de usuario estándar al rendimiento

Un administrador de colección de sitios, el propietario del sitio, el Editor o el colaborador pertenecen a grupos de seguridad adicionales, disponer de permisos adicionales y, por lo tanto, tienen elementos adicionales que se carga de SharePoint en una página.
  
Esto es aplicable a SharePoint local y SharePoint Online, pero en un escenario local las diferencias no se con la misma facilidad notará como en SharePoint Online.
  
Para evaluar correctamente cómo llevará a cabo una página para los usuarios, debe usar una cuenta de usuario estándar para evitar la carga de la creación de controles y el tráfico adicional relacionados con los grupos de seguridad.
  
## <a name="connection-categories-for-performance-tuning"></a>Categorías de conexión para ajustar el rendimiento

Puede clasificar las conexiones entre el servidor y el usuario en tres componentes principales. Tenga en cuenta esto al diseñar páginas de SharePoint Online para obtener más información sobre tiempos de carga.
  
- **Servidor** Los servidores que hospeda Microsoft en centros de datos.
    
- **Red** La red de Microsoft, Internet y la red local entre el centro de datos y los usuarios.
    
- **Explorador** Donde se carga la página.
    
Dentro de estas tres conexiones, normalmente hay cinco motivos que causan el 95 % de páginas lentas. En este artículo se describe cado uno de los motivos:
  
- Problemas de navegación
    
- Acumulación de contenido
    
- Archivos de gran tamaño
    
- Muchas solicitudes al servidor
    
- Procesamiento de elementos web
    
### <a name="server-connection"></a>Conexión de servidor

Muchos de los problemas que afectan al rendimiento con SharePoint local también se aplican a SharePoint Online.
  
Como cabría esperar, tiene mucho más control sobre el rendimiento de los servidores con SharePoint local. Con SharePoint Online las cosas son un poco diferentes. Cuanto más trabajo requiera al servidor, más tarda en procesar una página. Con SharePoint, la causa más grande en este sentido son páginas complejas con varios elementos web.
  
Servidor de SharePoint local
  
![Captura de pantalla del servidor local](media/a8e9b646-cdff-4131-976a-b5f891da44ac.png)
  
SharePoint Online
  
![Captura de pantalla del servidor en línea](media/46b27ded-d8a4-4287-b3e0-2603a764b8f8.png)
  
Con SharePoint Online, realmente pueden suceder que determinadas solicitudes de página terminen llamando a varios servidores. Podría acabar con una matriz de solicitudes entre los servidores para una solicitud individual. Estas interacciones son costosas desde una perspectiva de carga de página y harán que todo sea lento.
  
Algunos ejemplos de estas interacciones de servidor a servidor son:
  
- Servidores web a SQL
    
- Servidores web a servidores de aplicaciones
    
Lo otro que puede ralentizar las interacciones del servidor son los faltantes en la memoria caché. A diferencia de SharePoint local, hay muy poca probabilidad de que llegará al mismo servidor para una página que ha visitado previamente. Esto hace que el almacenamiento en caché de los objetos quede obsoleto.
  
### <a name="network-connection"></a>Conexión de red

Con SharePoint local que no tiene el uso de una red WAN, es posible que utilice una conexión de alta velocidad entre centros de datos y los usuarios finales. Por lo general, las cosas son fáciles de administrar desde una perspectiva de la red.
  
Con SharePoint Online, hay algunos factores más que se deben tener en cuenta. Por ejemplo:
  
- La red de Microsoft
    
- Internet
    
- El ISP
    
Independientemente de qué versión de SharePoint (y qué red) se utiliza, lo que dará lugar normalmente a la red ocupada es:
  
- Carga de gran tamaño
    
- Muchos archivos
    
- Gran distancia física con el servidor
    
Una característica que puede aprovechar en SharePoint Online es la CDN de Microsoft (Content Delivery Network). Una CDN es, básicamente, una colección de servidores implementada en varios centros de datos distribuida. Con una CDN, contenido en las páginas se puede hospedar en un servidor hacia el cliente incluso si el cliente se encuentra lejos desde el servidor de SharePoint original. Microsoft va a utilizar más en el futuro para almacenar las instancias locales de las páginas que no se puede personalizar, por ejemplo la página de principal del administrador SharePoint Online. Para obtener más información acerca de las CDN, vea [redes de entrega de contenido](https://docs.microsoft.com/en-us/office365/enterprise/content-delivery-networks).
  
Algo que debe tener en cuenta, pero que tal vez no pueda hacer mucho al respecto, es la velocidad de conexión de su ISP. Una simple herramienta de prueba de velocidad indica la velocidad de conexión.
  
### <a name="browser-connection"></a>Conexión de explorador

Existen algunos factores que debe considerar con exploradores web desde una perspectiva de rendimiento.
  
Visitar páginas complejas afectará al rendimiento. Mayoría de los exploradores sólo tiene una pequeña memoria caché (alrededor de 90MB), mientras el promedio página web suele ser alrededor de 1,6 MB. Esto no tardará mucho tiempo para acostumbrarse copia de seguridad.
  
Ancho de banda también puede ser un problema. Por ejemplo, si un usuario es ver vídeos en otra sesión, esto afectará al rendimiento de la página de SharePoint. Mientras no se puede evitar que los usuarios multimedia de transmisión por secuencias, puede controlar la forma en que se carga una página para los usuarios.
  
Consulte los siguientes artículos para diferentes técnicas de personalización de página SharePoint Online y otras prácticas recomendadas que le ayudarán a lograr un rendimiento óptimo.
  
- [Opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Use la herramienta de diagnóstico de la página de SharePoint Online](page-diagnostics-for-spo.md)
    
- [Optimización de imágenes para SharePoint Online](image-optimization-for-sharepoint-online.md)
    
- [Retrasar la carga de imágenes y JavaScript en SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    
- [Minificación y agrupación en SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Usar redes de entrega de contenido](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Uso de elemento de Web de búsqueda de contenido en lugar de elemento Web consulta de contenido para mejorar el rendimiento en SharePoint Online](using-content-search-web-part-instead-of-content-query-web-part-to-improve-perfo.md)
    
- [Planeación de capacidad y la carga de prueba de SharePoint Online](capacity-planning-and-load-testing-sharepoint-online.md)
    
- [Diagnosticar problemas de rendimiento con SharePoint Online](diagnosing-performance-issues-with-sharepoint-online.md)
    
- [Usar la memoria caché de objetos con SharePoint Online](using-the-object-cache-with-sharepoint-online.md)
    
- [Cómo: Evitar estar limitado o bloqueado en SharePoint Online](https://msdn.microsoft.com/en-us/library/office/dn889829.aspx)
    

