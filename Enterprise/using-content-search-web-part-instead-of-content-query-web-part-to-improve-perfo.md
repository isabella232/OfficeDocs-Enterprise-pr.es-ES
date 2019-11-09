---
title: Usar el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido para mejorar el rendimiento en SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: En este artículo se describe cómo aumentar el rendimiento al reemplazar el elemento Web de consulta de contenido con el elemento Web de búsqueda de contenido en SharePoint Server 2013 y SharePoint Online.
ms.openlocfilehash: e2a3a1dd5a0010fcf1bbf61a039ca1d23292f70d
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077949"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Usar el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido para mejorar el rendimiento en SharePoint Online

En este artículo se describe cómo aumentar el rendimiento al reemplazar el elemento Web de consulta de contenido con el elemento Web de búsqueda de contenido en SharePoint Server 2013 y SharePoint Online.
  
Una de las características nuevas más eficaces de SharePoint Server 2013 y SharePoint Online es el elemento Web de búsqueda de contenido (CSWP). Este elemento Web usa el índice de búsqueda para recuperar rápidamente los resultados que se muestran al usuario. Use el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido (CQWP) en las páginas para mejorar el rendimiento de los usuarios.
  
El uso de un elemento Web de búsqueda de contenido en un elemento Web de consulta de contenido casi siempre dará lugar a un rendimiento de carga de páginas significativamente mejor en SharePoint Online. Hay una configuración adicional para obtener la consulta correcta, pero las recompensas mejoran el rendimiento y los usuarios más contentos.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Comparación de la mejora de rendimiento que obtiene al usar el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido

Los siguientes ejemplos muestran las mejoras de rendimiento relativas que puede recibir cuando usa un elemento Web de búsqueda de contenido en lugar de un elemento Web de consulta de contenido. Los efectos son más obvios con una compleja estructura del sitio y consultas de contenido muy amplias.
  
Este sitio de ejemplo tiene las siguientes características:
  
- 8 niveles de subsitios.
    
- Listas con un tipo de contenido personalizado "fruta".
    
- En el elemento Web, la consulta de contenido es amplia y devuelve todos los elementos con el tipo de contenido "fruta".
    
- En el ejemplo solo se usan 50 elementos en los 8 sitios. Los efectos serán aún más pronunciados para los sitios con más contenido.
    
Esta es una captura de pantalla de los resultados del elemento Web consulta de contenido.
  
![Gráfico que muestra la consulta de contenido del elemento web](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
En Internet Explorer, use la pestaña **red** de las herramientas de desarrollo F12 para ver los detalles del encabezado de respuesta. En la siguiente captura de pantalla, el valor de **SPRequestDuration** para esta carga de página es de 924 milisegundos. 
  
![Captura de pantalla que muestra la duración de la solicitud de 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** indica la cantidad de trabajo que se realiza en el servidor para preparar la página. El cambio de contenido por elementos Web de consulta con contenido por elementos Web de búsqueda reduce considerablemente el tiempo que se tarda en representar la página. Por el contrario, una página con un elemento Web de búsqueda de contenido equivalente que devuelve el mismo número de resultados tiene un valor **SPRequestDuration** de 106 milisegundos, tal como se muestra en esta captura de pantalla: 
  
![Captura de pantalla que muestra la duración de la solicitud de 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Adición de un elemento Web de búsqueda de contenido en SharePoint Online

Agregar un elemento Web de búsqueda de contenido es muy similar a un elemento Web de consulta de contenido normal. Vea la sección *sobre cómo agregar un elemento Web de búsqueda de contenido* en [configurar un elemento Web de búsqueda de contenido en SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Crear la consulta de búsqueda correcta para el elemento Web de búsqueda de contenido

Una vez que haya agregado un elemento Web de búsqueda de contenido, puede refinar la búsqueda y devolver los elementos que desee. Para obtener instrucciones detalladas sobre cómo hacerlo, vea la sección *"Mostrar contenido mediante la configuración de una consulta avanzada en un elemento Web de búsqueda de contenido"* en [configurar un elemento Web de búsqueda de contenido en SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Herramienta de creación de consultas y pruebas

Para obtener una herramienta para compilar y probar consultas complejas, vea la [herramienta de consulta de búsqueda](https://sp2013searchtool.codeplex.com/) en Codeplex. 
  

