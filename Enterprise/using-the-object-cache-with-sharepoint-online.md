---
title: Usar la memoria caché de objetos con SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 38bc9c14-3826-449c-beb6-b1003bcbeaaf
description: En este artículo se explica la diferencia entre el uso de la memoria caché de objetos en SharePoint Server 2013 local y SharePoint Online.
ms.openlocfilehash: 8ae2e2675444c023b69030f3f46f170b450fb390
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616843"
---
# <a name="using-the-object-cache-with-sharepoint-online"></a>Usar la memoria caché de objetos con SharePoint Online

En este artículo se explica la diferencia entre el uso de la memoria caché de objetos en SharePoint Server 2013 local y SharePoint Online.
  
Hay un impacto negativo significativo de confiar en la memoria caché de objetos en la implementación de SharePoint Online. Cualquier dependencia de la memoria caché de objetos en SharePoint Online reducirá la confiabilidad de la página. 
  
## <a name="how-the-sharepoint-online-and-sharepoint-server-2013-object-cache-works"></a>Cómo funciona la caché de objetos de SharePoint Online y SharePoint Server 2013

Cuando SharePoint Server 2013 está hospedado en local, el cliente tiene servidores front-end web privados que hospedan la memoria caché de objetos. Esto significa que la memoria caché está dedicada a un cliente y solo está limitada por la cantidad de memoria disponible y asignada a la memoria caché de objetos. Dado que solo se atiende a un cliente en el escenario local, los servidores front-end web suelen hacer que los usuarios realicen solicitudes a los mismos sitios una y otra vez. Esto significa que la memoria caché se llena rápidamente y permanece llena de los resultados de la consulta de la lista y los objetos de SharePoint que los usuarios solicitan de manera regular.
  
![Muestra el tráfico y la carga a los servidores locales front-end web](media/a0d38b36-4909-4abb-8d4e-4930814bb3de.png)
  
Como resultado, la segunda vez que un usuario visita una página, el tiempo de carga de la página mejora. Después de un mínimo de cuatro cargas de la misma página, la página se almacena en caché en todos los servidores web Front-end.
  
Por el contrario, en SharePoint Online hay muchos más servidores, pero también muchos más sitios. Cada usuario puede conectarse a un servidor web Front-end diferente que no tiene la caché rellenada. O bien, es posible que la memoria caché se llene para un servidor, pero el siguiente usuario a ese servidor web Front-end solicita una página de un sitio diferente. O, incluso si el siguiente usuario solicita la misma página que en la visita anterior, se equilibra la carga con un servidor cliente web diferente que no tiene esa página en la caché. En este último caso, el almacenamiento en caché no ayuda a los usuarios.
  
En la siguiente ilustración, cada punto representa una página que un usuario solicita y donde se almacena en caché. Diferentes colores representan a diferentes clientes que realizan el uso compartido de la infraestructura SaaS.
  
![Muestra los resultados de almacenamiento en memoria caché de objetos en SharePoint Online](media/25d04011-ef83-4cb7-9e04-a6ed490f63c3.png)
  
Como puede ver en el diagrama, las probabilidades de que un usuario determinado que visita un servidor con la versión almacenada en caché de la página sean delgadas. Además, debido al gran rendimiento y al hecho de que los servidores se comparten entre muchos sitios, la caché no dura mucho tiempo, ya que sólo hay un espacio para el almacenamiento en caché disponible.
  
Por todos estos motivos, depender de que los usuarios obtengan objetos almacenados en la caché no es una forma eficaz de garantizar una experiencia del usuario de calidad y tiempos de carga de página en SharePoint Online.
  
## <a name="if-we-cant-rely-on-the-object-cache-to-improve-performance-in-sharepoint-online-what-do-we-use-instead"></a>Si no podemos confiar en la memoria caché de objetos para mejorar el rendimiento en SharePoint Online, ¿qué usamos en su lugar?

Como no se debe basar en el almacenamiento en caché en SharePoint Online, debe evaluar métodos de diseño alternativos para las personalizaciones de SharePoint que usan la memoria caché de objetos. Esto significa usar enfoques para problemas de rendimiento que no se basan en el almacenamiento en caché de objetos para obtener buenos resultados para los usuarios. Esto se describe en algunos de los otros artículos de esta serie e incluyen:
  
- [Opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md)
    
- [Minificación y agrupación en SharePoint Online](minification-and-bundling-in-sharepoint-online.md)
    
- [Usar redes de entrega de contenido](using-content-delivery-networks-with-sharepoint-online.md)
    
- [Retrasar la carga de imágenes y JavaScript en SharePoint Online](delay-loading-images-and-javascript-in-sharepoint-online.md)
    

