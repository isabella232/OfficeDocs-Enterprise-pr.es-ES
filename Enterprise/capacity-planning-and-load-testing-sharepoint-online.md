---
title: Planeación de capacidad y la carga de prueba de SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/18/2016
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: En este artículo se describe cómo se puede implementar en SharePoint Online sin tener que realizar las pruebas de carga tradicional como no está permitido.
ms.openlocfilehash: 6a22ee089adc0817f5c52bbfee5f2b41d7e5d80c
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181031"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planeación de capacidad y la carga de prueba de SharePoint Online

En este artículo se describe cómo se puede implementar en SharePoint Online sin pruebas de carga tradicional, ya que las pruebas de carga no son recomendable.
  
Aunque no es recomendable, existen otras maneras, puede asegurarse de que carga activo pruebas en SharePoint Online un sitio no producirá una experiencia de usuario deficiente cuando el sitio se ha iniciado. 
  
Con SharePoint Online no es necesario que realizar la planeación de la capacidad, como esto se realiza automáticamente como parte de la oferta de servicio. Con los entornos local, las pruebas de carga se usan para validar la suposición de escala y, finalmente, busque el punto de interrupción de una granja de servidores; al saturar con carga. Con SharePoint Online, necesitamos hacer cosas de manera diferente. Que se va a un entorno de varios inquilino, tenemos que proteger a todos los inquilinos en la misma granja de servidores, por lo que se va a limitar automáticamente cualquier las pruebas de carga. Esto significa que se recibirá decepcionantes y potencialmente engañoso son resultados si se intenta cargar el entorno de prueba.
  
Uno de los principales beneficios de SharePoint Online a través de una implementación local es la elasticidad de la nube. Nuestro entorno de gran escala está configurado para el servicio millones de usuarios de manera diaria por lo que es importante que se controlan capacidad eficazmente mediante la expansión automática de las granjas de servidores, tal y como y cuando sea necesario. En este artículo se explica la planificación para el crecimiento de la capacidad y la escala horizontal en su lugar. El artículo también trata los enfoques para usar que no requieren pruebas de carga.
  
## <a name="how-office-365-predicts-load-and-expands-capacity"></a>Cómo Office 365 prevé carga y expande la capacidad

Trabajo de administración de capacidad de SharePoint Online server se realiza a través de dos métodos:
  
- Previsión de la capacidad
    
- Equilibrio de carga en granjas de servidores de un solo servidor
    
A diferencia de planeación para un entorno local, para la previsión de capacidad en SharePoint Online, estamos capacitados para compilar las estadísticas y los posibles requisitos en cualquier grupo de servidor determinado de gráfico. La demanda agregada puede parecerse a las solicitudes en la zona (donde una zona es un grupo de granjas de servidores de SharePoint) línea de crecimiento en la imagen siguiente:
  
![Gráfico que muestra la capacidad de predicción: previsión](media/ca800cb6-cc59-451f-98bd-55e035489af3.png)
  
Mientras el crecimiento es impredecible en cualquier una granja de servidores, la suma de las solicitudes en una zona agregada es predecible. Mediante la identificación de las tendencias de crecimiento en SharePoint Online, podemos hacer planes de expansión en el futuro.
  
Para poder utilizar la capacidad de forma eficaz y abordar los problemas con el crecimiento inesperado, en cualquier conjunto de servidores, tenemos automatización que realiza un seguimiento de carga front-end y cambia la escala de copia de seguridad en su lugar, cuando sea necesario. La métrica principal que se usa como una señal para escalar front-termina es la carga de CPU. Nuestro objetivo consiste en mantener los momentos de mayor carga de CPU en un 40%. Esto es con el fin de tener suficiente búfer absorber los picos inesperados. Como carga enfoques 40% en estado estable, se agregue servidores front-end para granjas de servidores.
  
![Gráfico que muestra la capacidad de predicción: administrar granjas de servidores](media/6b2a8c63-24c1-4504-b7a3-3d3b3be2583a.png)
  
Servidores adicionales se pueden agregar rápidamente a una granja de servidores, los que anteriormente se han agregado a la zona mediante el uso de la previsión con. 
  
## <a name="how-do-i-plan-for-a-site-launch"></a>¿Cómo planeado para el lanzamiento de un sitio?

Puede esperar a que la granja de servidores en el que se inicia el nuevo sitio automáticamente se supervisarán para que se agreguen nuevos servidores front-end, como se describió anteriormente. Por este motivo, no es necesario ninguna notificación para su lanzamiento del sitio nuevo.
  
Después de otras prácticas recomendadas para una sola página en SharePoint Online es poco probable que el lanzamiento de un nuevo sitio a incluso 100.000 usuarios tendrán ningún impacto en la granja de servidores.
  
Hay algunas estrategias para planear una versión de un nuevo sitio de SharePoint Online. Tal como se muestra en la siguiente imagen, a menudo es considerablemente superior a los que realmente se usa el sitio que la cantidad de usuarios que están invitados. Esta imagen muestra una estrategia de acerca de cómo implantar una versión. Este método no sólo contribuye a la carga de rendimiento, sino que también puede ayudar a identificar maneras de mejorar el sitio de SharePoint antes de la gran mayoría de los usuarios para verlo.
  
![Gráfico que muestra los usuarios invitados y activos](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
En la fase piloto, es buena obtener comentarios de los usuarios que la organización confía y sabe realizarán ser ocupado. En este modo, es posible evaluar cómo se utiliza el sistema, así como cómo va a realizar.
  
Una vez hecho esto, comienza un roll out a todos los usuarios de ondas; obtener comentarios y revisar el rendimiento con regularidad. Esto tiene la ventaja de lentamente Introducción al sistema y realizar mejoras como el sistema obtiene usar más. Esto también nos permite reaccionar ante el aumento de la carga como el sitio se ha implantado a más usuarios.
  
Por último, mientras que las pruebas de carga están prohibidas, los clientes desean configurar ping periódicos para el servicio de disponibilidad de medida y la latencia. Esto permitirá identificar una línea de base para su sitio. Sin embargo, estos deben mantenerse a baja frecuencia para evitar la limitación de los problemas descritos anteriormente.
  

