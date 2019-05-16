---
title: Planeamiento de capacidad y pruebas de carga en SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 04/10/2019
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: En este artículo se describe cómo se puede implementar en SharePoint Online sin realizar pruebas de carga tradicionales, ya que no está permitido.
ms.openlocfilehash: f8de9ee2eb28b4cafef469a078a3700b1ffbbbb5
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068166"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planeación de la capacidad y pruebas de carga de SharePoint Online.

En este artículo se describe cómo implementar en SharePoint Online sin pruebas de carga tradicionales, ya que las pruebas de carga no se permiten en SharePoint Online. SharePoint Online es un servicio en la nube las capacidades de carga, el estado y el equilibrio general de carga en el servicio son administrados por Microsoft.
  
El mejor enfoque para garantizar el éxito de iniciar el sitio es seguir los principios básicos, prácticas y recomendaciones que se resaltan a continuación.
  
Con los entornos locales, las pruebas de carga se usan para validar la hipótesis de escala y, en última instancia, buscar el punto de ruptura de una granja de servidores; mediante saturarla con la carga. Con SharePoint Online, debemos hacer cosas de manera diferente. Como un entorno multiempresa, debemos proteger todos los inquilinos de la misma granja de servidores, por lo que se limitarán automáticamente las pruebas de carga. Esto significa que recibirá los resultados que pueden ser disimulables y potencialmente engañosos si intenta cargar el entorno de prueba.
  
Una de las principales ventajas de SharePoint Online sobre una implementación local es la elasticidad de la nube. Nuestro entorno de gran escala está configurado para atender a millones de usuarios a diario, por lo que es importante que controle la capacidad con eficacia mediante el equilibrio y la expansión de las granjas de servidores. En el artículo también se describen los métodos para usar que no implican pruebas de carga, pero que implican las siguientes directrices que le ayudarán a que se inicie correctamente. 
  
Aunque el crecimiento es impredecible para cualquier inquilino de una granja de servidores, la suma de las solicitudes agregadas es predecible a lo largo del tiempo. Al identificar las tendencias de crecimiento en SharePoint Online, podemos planear la expansión futura.
  
Para usar la capacidad de manera eficaz y hacer frente a un crecimiento inesperado, en cualquier granja de servidores, tenemos automatización que realiza un seguimiento de la carga front-end y la escalabilidad hacia arriba, cuando sea necesario. Hay varias métricas que se usan con una de las principales cargas de CPU que se usa como señal para escalar verticalmente los servidores front-end. Además de esto y de lo que notará en el artículo, recomendamos un enfoque escalonado/Wave a medida que se escalan los entornos SQL de acuerdo con la carga y la demanda, y según las fases y las ondas, se permite la distribución correcta de la carga y el crecimiento. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>¿Cómo planeo el inicio de un sitio?

### <a name="optimize-pages-by-following-recommended-guidelines"></a>Optimizar las páginas siguiendo las recomendaciones recomendadas
Las páginas de una implementación local no deben tomarse tan solo como están en SharePoint Online sin revisarlas con las instrucciones recomendadas para SharePoint Online.

Se deben tener en cuenta algunos factores clave:
- Las implementaciones locales pueden aprovechar las memorias caché del lado servidor tradicionales como la memoria caché de objetos, pero con las diferencias de topología en la nube, estas opciones no están disponibles.
- Las páginas/características/personalizaciones usadas para el consumo de nube deben optimizarse para varias ubicaciones, de modo que los usuarios de diferentes áreas o regiones tengan una experiencia coherente. La nube ofrece optimizaciones como redes de entrega de contenido (CDN) para optimizar para una base de usuarios distribuidos.

En el caso de las páginas de publicación clásicas de SharePoint Online, puede usar la extensión Chrome de la [herramienta de diagnóstico de páginas](https://aka.ms/perftool) que le ayudarán a analizar las principales páginas de aterrizaje usadas por los usuarios.
Las herramientas de desarrollo F12 en el explorador o [Fiddler](https://www.telerik.com/download/fiddler) se pueden usar para revisar el peso de la página y se debe revisar y optimizar el número de llamadas y elementos que afectan a la carga de páginas general. Puede consultar una lista de recomendaciones, como el uso de redes de entrega de contenido y otras optimizaciones, en el artículo [Tune SharePoint Online performance](https://aka.ms/tuneSPO) .

### <a name="wave--phase-approach"></a>Enfoque de onda/fase
El enfoque de enorme exclamación tradicional para los lanzamientos de sitios no permite la comprobación de que las personalizaciones, los orígenes externos, los servicios o los procesos se hayan probado a la escala adecuada. SharePoint como servicio también escala su capacidad en función del uso y el uso previsto y, aunque no es necesario que notifique el inicio del sitio, debe seguir las instrucciones siguientes para garantizar el éxito.
  
Como se muestra en la siguiente imagen, a menudo el número de usuarios invitados es significativamente más alto que los que realmente usan el sitio. Esta imagen muestra una estrategia sobre cómo implementar una versión. Este método ayuda a identificar formas de mejorar el sitio de SharePoint antes de que lo vea la mayoría de los usuarios. También permite que se ponga en pausa una implementación si se encuentra con problemas en cualquiera de las fases/ondas, con lo que se limita el número potencial de usuarios que se ven afectados.
  
![Gráfico que muestra los usuarios invitados y activos](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
En la fase piloto, es bueno obtener comentarios de los usuarios para los que la organización confía y que sabe que se va a usar. De este modo, es posible evaluar el modo en que se usa el sistema, así como el modo en que se realiza.
  
Durante cada una de las ondas, recopile los comentarios de los usuarios sobre las características, así como el rendimiento durante cada una de las ondas de implementación. Esto tiene la ventaja de que presenta lentamente el sistema y mejora a medida que el sistema obtiene más uso. Esto también nos permite reaccionar a la carga aumentada, ya que el sitio se implementa para más y más usuarios.
