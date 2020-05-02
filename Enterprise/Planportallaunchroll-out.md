---
title: Planeación del lanzamiento del portal del plan de implementación en SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- SPO160
- MET150
description: En este artículo se describe cómo planear el lanzamiento del portal en SharePoint Online y los pasos que se deben seguir para un inicio correcto
ms.openlocfilehash: c6f1ef0817534fe2e643492e882fe8f61c3a01dc
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004113"
---
# <a name="planning-your-portal-launch-roll-out-plan-in-sharepoint-online"></a>Planeación del lanzamiento del portal del plan de implementación en SharePoint Online

Un portal es un sitio de SharePoint en la intranet que tiene un gran número de visores de sitio que emplean el contenido en el sitio. En las organizaciones de gran tamaño podría haber varios de estos, por ejemplo, un portal de empresa y un portal de RRHH. Por lo general, los portales tienen relativamente pocas personas que aportan y crean el sitio y su contenido. La mayoría de los visitantes del portal únicamente leen y usan el contenido.

En este artículo se describe cómo planear la implementación y el plan de implementación en SharePoint Online. También proporciona métodos para seguir, ya que las pruebas de carga tradicionales no están permitidas en SharePoint Online. SharePoint Online es un servicio en la nube y las capacidades de carga, el estado y el equilibrio general de carga en el servicio son administrados por Microsoft.

Para ayudar a crear un portal exitoso, siga los principios básicos, prácticas y recomendaciones detalladas en el [sitio crear, iniciar y mantener un buen portal](https://go.microsoft.com/fwlink/?linkid=2105838) 

A continuación se resalta el método de implementación.

## <a name="overview-of-capacity-planning-in-sharepoint-online"></a>Información general sobre la planeación de la capacidad en SharePoint Online
Para usar la capacidad de manera eficaz y tratar con un crecimiento inesperado, en cualquier granja de servidores, tenemos automatización que realiza un seguimiento de determinados escenarios de uso. Aunque el crecimiento exacto es impredecible para cualquier inquilino de una granja de servidores, la suma de solicitudes agregada es predecible a lo largo del tiempo. Al identificar las tendencias de crecimiento en SharePoint Online, podemos planear la expansión futura. Para obtener más información sobre la [planeación de capacidad y la prueba de carga de SharePoint Online](https://docs.microsoft.com/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online).

Una parte clave de un lanzamiento correcto es el enfoque "Wave" o "lanzamiento en fases" que se detalla a continuación. 

## <a name="can-i-load-test-sharepoint-online"></a>¿Puedo cargar SharePoint Online de prueba?
SharePoint Online es un entorno multiinquilino compartido que se equilibra entre las granjas de servidores y la escala se ajusta de manera continua. Pruebas de carga de un entorno, como SharePoint Online, cuyo cambio de escala de forma continua no solo le dará resultados inesperados, pero no está permitido. 

Más información: [planeación de la capacidad y pruebas de carga SharePoint Online](https://docs.microsoft.com/office365/enterprise/capacity-planning-and-load-testing-sharepoint-online)

## <a name="optimize-pages-by-following-recommended-guidelines"></a>Optimizar las páginas siguiendo las recomendaciones recomendadas
Las páginas de una implementación local no se deben mover simplemente como están en SharePoint Online sin tener que revisarlas con las instrucciones recomendadas para SharePoint Online. El mejor enfoque es optimizar siempre cualquier página de inicio para cualquier sitio o portal de SharePoint, ya que es donde la mayoría de los usuarios de la organización tendrán acceso como punto de partida para los sitios.

Se deben tener en cuenta algunos factores básicos:
- Las implementaciones locales pueden aprovechar las memorias caché tradicionales del lado servidor, como la caché de objetos, la caché de resultados y la caché BLOB. Con las diferencias de topología en la nube, estas opciones no están necesariamente disponibles, ya que las diferencias de escalado hacen que sean enfoques menos viables.
- Las páginas/características/personalizaciones usadas para el consumo de nube deben optimizarse para una mayor latencia, así como para las ubicaciones distribuidas de los usuarios, de modo que los usuarios de diferentes áreas o regiones tengan una experiencia más coherente. La nube ofrece optimizaciones como las redes de entrega de contenido (CDN) para optimizar una base de usuarios distribuida, así como para SharePoint moderno, la última buena conocida (LKG) se usa en los elementos Web de fuera del cuadro (OOTB).

### <a name="what-to-do"></a>Qué hacer:
 - Para todas las páginas del sitio de SharePoint Online, use la [herramienta de diagnóstico de página](https://aka.ms/perftool), que es una extensión de cromo que le ayudará a analizar y a proporcionar una guía. Los propietarios de sitios, los editores, los administradores y los programadores pueden usarlas a medida que se diseñan como punto de partida para el análisis y la optimización.
 - Los programadores también deben usar herramientas de desarrollo, como la herramienta de desarrollo de explorador F12 y CTRL-F12 en el explorador de páginas modernas. [Fiddler](https://www.telerik.com/download/fiddler) también se puede usar para revisar el peso (el tamaño en megabytes de la página) de la página y el número de llamadas y elementos que afectan a la carga de página general. 

Esta sección fue un breve resumen de la optimización de páginas.  Para obtener más información, consulte: [creación, Inicio y mantenimiento de un portal saludable](https://go.microsoft.com/fwlink/?linkid=2105838).

## <a name="follow-a-wave--phased-roll-out-approach"></a>Seguir un enfoque de lanzamiento en fases o en una onda
El enfoque de enorme exclamación tradicional para los lanzamientos de sitios no permitirá la comprobación de que las personalizaciones, los orígenes externos, los servicios o los procesos se hayan probado a la escala adecuada. Esto no significa que vaya a tardar meses en iniciarse, pero se recomienda que supere al menos varios días en función del tamaño de la organización. Después de un plan de lanzamiento de onda, le da la opción de pausar y resolver problemas antes de continuar con la siguiente fase y, por lo tanto, se reduce el número potencial de usuarios que se ven afectados por los problemas. SharePoint como servicio escala su capacidad según el uso y el uso previsto y, si bien no es necesario que nos notifique el lanzamiento, debe seguir las instrucciones para garantizar el éxito.
  
Como se muestra en la siguiente imagen, a menudo el número de usuarios invitados es significativamente más alto que los que realmente usan el sitio. Esta imagen muestra una estrategia sobre cómo implementar una versión. Este método ayuda a identificar formas de mejorar el sitio de SharePoint antes de que lo vea la mayoría de los usuarios.
  
![Gráfico que muestra los usuarios invitados y activos](media/0bc14a20-9420-4986-b9b9-fbcd2c6e0fb9.png)
  
En la fase piloto, es bueno obtener comentarios de los usuarios para los que la organización confía y que sabe que se va a usar. De este modo, es posible evaluar el modo en que se usa el sistema, así como el modo en que se realiza.
  
Durante cada una de las ondas, recopile los comentarios de los usuarios sobre las características, así como el rendimiento durante cada una de las ondas de implementación. Esto tiene la ventaja de que presenta lentamente el sistema y mejora a medida que el sistema obtiene más uso. Esto también nos permite reaccionar a la carga aumentada, ya que el sitio se aplica a más y más usuarios, y se combina con las directrices para la optimización de páginas, lo que garantiza una experiencia positiva para los usuarios.

### <a name="what-to-do"></a>Qué hacer:
- Decida el momento de cada fase y asegúrese de que tiene una oportunidad de contingencia o de pausa, en caso de que deba realizar ajustes antes de continuar.
- Planee el primer grupo de usuarios que quiera habilitar para asegurarse de que recibe los comentarios que necesita para avanzar. Esto significa que, cuando sea posible, seleccione un grupo activo de usuarios que proporcionarán comentarios de forma oportuna.
- Al planear cada onda, intente comenzar con una base de usuarios pequeña (menos de 5000 usuarios) y, a continuación, aumente los tamaños de grupo a medida que avance con cada onda. Esto ayuda a crear un enfoque escalonado y permite oportunidades de pausa más sencillas que pueden ser necesarias.
