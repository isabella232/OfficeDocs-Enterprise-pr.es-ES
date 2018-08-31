---
title: Uso de elemento de Web de búsqueda de contenido en lugar de elemento Web consulta de contenido para mejorar el rendimiento en SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: En este artículo se describe cómo aumentar el rendimiento mediante el reemplazo del elemento Web consulta de contenido con el elemento Web de búsqueda de contenido en SharePoint Server 2013 y SharePoint Online.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22543019"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a>Uso de elemento de Web de búsqueda de contenido en lugar de elemento Web consulta de contenido para mejorar el rendimiento en SharePoint Online

En este artículo se describe cómo aumentar el rendimiento mediante el reemplazo del elemento Web consulta de contenido con el elemento Web de búsqueda de contenido en SharePoint Server 2013 y SharePoint Online.
  
Una de las nuevas características más eficaces de SharePoint Server 2013 y SharePoint Online es la parte de Web de búsqueda de contenido (CSWP). Este elemento Web utiliza el índice de búsqueda para recuperar rápidamente los resultados que se muestran al usuario. Use el elemento Web de búsqueda de contenido en lugar del contenido consulta de elemento Web (CQWP) en las páginas para mejorar el rendimiento para los usuarios.
  
Uso de un elemento Web de búsqueda de contenido a través de un elemento Web consulta de contenido, se producirá casi siempre mucho mejor rendimiento de carga de página en SharePoint Online. Hay una poco una configuración adicional para obtener la consulta derecha, pero las recompensas son usuarios más satisfechos y mejorar el rendimiento.
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a>Comparación de la mejora del rendimiento que obtiene al utilizar el elemento Web de búsqueda de contenido en lugar de elemento Web consulta de contenido

Los siguientes ejemplos muestran las mejoras de rendimiento relativa que puede recibir al usar un elemento Web de búsqueda de contenido en lugar de un elemento Web consulta de contenido. Los efectos son más obvios con una estructura compleja de sitios y las consultas de contenido muy amplias.
  
Este sitio de ejemplo tiene las siguientes características:
  
- 8 niveles de subsitios.
    
- Se enumeran con un tipo de contenido personalizado "fruta".
    
- En el elemento Web, la consulta de contenido es amplia, devolución de todos los elementos con el tipo de contenido de "fruta".
    
- En el ejemplo se utiliza sólo 50 artículos en todos los sitios de 8. Los efectos se pronuncia aún más para los sitios con más contenido.
    
Aquí es una captura de pantalla de los resultados del elemento Web consulta de contenido.
  
![Gráfico que muestra la consulta de contenido del elemento web](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
En el Explorador de Internet, utilice la ficha de **red** de las herramientas de desarrollo F12 para ver los detalles del encabezado de respuesta. En la siguiente captura de pantalla, el valor de la **SPRequestDuration** para esta carga de página es 924 milisegundos. 
  
![Captura de pantalla que muestra la duración de la solicitud de 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 **SPRequestDuration** indica la cantidad de trabajo que se realiza en el servidor para preparar la página. Elementos Web de consulta de contenido con elementos Web de búsqueda de contenido de conmutación considerablemente reduce el tiempo necesario para representar la página. Sin embargo, una página con un elemento de Web de búsqueda de contenido equivalente, devolver el mismo número de resultados tiene un valor de **SPRequestDuration** de 106 milisegundos, como se muestra en esta captura de pantalla: 
  
![Captura de pantalla que muestra la duración de la solicitud de 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a>Adición de un elemento Web de búsqueda de contenido en SharePoint Online

Adición de un elemento Web de búsqueda de contenido es muy similar a un elemento de Web de consulta de contenido normal. Vea la sección *"Agregar un elemento Web de búsqueda"* en [configurar un elemento Web de búsqueda de contenido en SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a>Creación de la consulta de búsqueda adecuada para su elemento Web búsqueda de contenido

Una vez que haya agregado un elemento Web de búsqueda de contenido, puede refinar la búsqueda y devolver los elementos que desee. Para obtener instrucciones detalladas acerca de cómo hacer esto, vea la sección, *"Mostrar contenido mediante la configuración de una consulta avanzada en un elemento Web búsqueda de contenido"* en [configurar un elemento Web de búsqueda de contenido en SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).
  
## <a name="query-building-and-testing-tool"></a>Crear y probar la herramienta de consulta

Para que una herramienta crear y probar las consultas complejas, consulte la [Herramienta de consulta de búsqueda](https://sp2013searchtool.codeplex.com/) en Codeplex. 
  

