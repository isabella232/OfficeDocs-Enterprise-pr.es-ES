---
title: Usar la memoria caché de objetos con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: En este artículo se explica la diferencia entre el uso de la memoria caché de objetos en SharePoint Server 2013 local y SharePoint Online.
ms.openlocfilehash: 8aa505645bb5f39c65684412ddebbd2b02baa13f
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542854"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Usar la memoria caché de objetos con SharePoint Online

En este artículo se explica la diferencia entre el uso de la memoria caché de objetos en SharePoint Server 2013 local y SharePoint Online.
  
Si se depende de la caché de objetos en una implementación de SharePoint Online, se produce un impacto negativo relevante. Cualquier dependencia de memoria caché de objetos en SharePoint Online reducirá la confiabilidad de la página. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Cómo SharePoint Online y SharePoint Server 2013 funcionamiento de la memoria caché de objetos

Cuando SharePoint Server 2013 está hospedado local, el cliente tiene servidores front-end web privada que hospedan la caché de objetos. Esto significa que la memoria caché está dedicada a un cliente y sólo está limitada por la cantidad de memoria es disponibles y asignados a la memoria caché de objetos. Dado que solo un cliente se sirve en el escenario local los servidores front-end web normalmente tienen los usuarios que realizan solicitudes a los mismos sitios, una y otra vez. Esto significa que la memoria caché obtiene completa rápidamente y permanece completa de los resultados de la consulta de lista y los objetos de SharePoint que los usuarios solicitan de forma regular.
  
![Muestra el tráfico y la carga a los servidores locales front-end web](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
En consecuencia, la segunda vez que un usuario visita una página, el tiempo de carga de la página mejora. Después de un mínimo de cuatro cargas de la misma página, la página se almacena en la memoria caché en todos los servidores front-end web.
  
Por el contrario, en SharePoint Online hay muchos más servidores pero también muchos más sitios. Cada usuario puede conectarse a un servidor web front-end diferente que no tiene la memoria caché que se rellena. O bien, es posible obtener rellena la memoria caché para un servidor, pero el siguiente usuario que ese servidor front-end web solicita una página de un sitio diferente. O bien, incluso si el usuario siguiente solicita la misma página que en su visita anterior, son con equilibrio de carga en un servidor web front-end diferente que no tiene esa página en su memoria caché. En este último caso, el almacenamiento en caché no ayuda a los usuarios en absoluto.
  
En la figura siguiente, cada punto representa una página que un usuario solicita y donde se almacenó en la memoria caché. Los distintos colores representan a diferentes clientes que usan de modo compartido la infraestructura de SaaS.
  
![Muestra los resultados de almacenamiento en memoria caché de objetos en SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Como puede ver en el diagrama, las posibilidades de que cualquier usuario determinado alcanzando a un servidor con la versión en caché de la página son delgadas. Además, debido a la gran rendimiento y el hecho de que los servidores se comparten entre muchos sitios, la memoria caché no por última vez durante cuánto tiempo puesto que sólo hay mucho espacio para almacenar en caché disponible.
  
Por todos estos motivos, depender de que los usuarios obtengan objetos almacenados en la memoria caché no es una forma eficaz de garantizar una experiencia de usuario de calidad y tiempos de carga páginas en SharePoint Online.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Si no podemos depender de la memoria caché de objetos para mejorar el rendimiento en SharePoint Online, ¿qué usamos en su lugar?

Puesto que no debe depender del almacenamiento en memoria caché en SharePoint Online, debe evaluar enfoques de diseño alternativos para las personalizaciones de SharePoint que usan la memoria caché de objetos. Esto significa que se deben usar enfoques para problemas de rendimiento que no dependan de la memoria caché de objetos para obtener buenos resultados para los usuarios. Se describe en algunos de los otros artículos de esta serie e incluyen:
  
- [Opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minificación y agrupación en SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Usar redes de entrega de contenido](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Retrasar la carga de imágenes y JavaScript en SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

