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
ms.collection:
- Ent_O365
- SPO_Content
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c932bd9b-fb9a-47ab-a330-6979d03688c0
description: En este artículo se describe cómo se puede implementar en SharePoint Online sin realizar pruebas de carga tradicionales, ya que no está permitido.
ms.openlocfilehash: 13e71343aa5ec823003791d99e227fc835117b62
ms.sourcegitcommit: 89ecf793443963b4c87cf1033bf0284cbfb83d9a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2019
ms.locfileid: "38077883"
---
# <a name="capacity-planning-and-load-testing-sharepoint-online"></a>Planeamiento de capacidad y pruebas de carga en SharePoint Online
En este artículo se describe cómo implementar en SharePoint Online sin pruebas de carga tradicionales, ya que las pruebas de carga no se permiten en SharePoint Online. SharePoint Online es un servicio en la nube y las capacidades de carga, el estado y el equilibrio general de carga en el servicio son administrados por Microsoft.
  
El mejor enfoque para garantizar el éxito de iniciar el sitio es seguir los principios básicos, los procedimientos y las recomendaciones que se destacan en el plan de lanzamiento de la [implementación del portal](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out).

## <a name="overview-of-how-sharepoint-online-performs-capacity-planning"></a>Información general sobre cómo SharePoint Online realiza la planeación de capacidad 
Una de las principales ventajas de SharePoint Online sobre una implementación local es la elasticidad de la nube, así como las optimizaciones para los usuarios en las regiones distribuidas. Nuestro entorno de gran escala está configurado para atender a millones de usuarios a diario, por lo que es importante que controle la capacidad con eficacia mediante el equilibrio y la expansión de las granjas de servidores.
  
Aunque el crecimiento suele ser impredecible para cualquier inquilino de una granja de servidores, la suma de las solicitudes agregadas es predecible a lo largo del tiempo. Al identificar las tendencias de crecimiento en SharePoint Online, podemos planear la expansión futura.
  
Con el fin de usar la capacidad de manera eficaz y tratar con un crecimiento inesperado, en cualquier granja de servidores, tenemos automatización que realiza un seguimiento y supervisa varios elementos del servicio. Se usan varias métricas, con una de las principales cargas de CPU, que se usa como señal para los servidores front-end de escalado vertical. Además, se recomienda realizar un [enfoque escalonado por fases](https://docs.microsoft.com/office365/enterprise/planportallaunchroll-out), ya que los entornos SQL se escalarán de acuerdo con la carga y el crecimiento a lo largo del tiempo, y siguiendo las fases y las ondas, se permite la distribución correcta de esa carga y crecimiento. 

La capacidad es más que simplemente agregar hardware de forma continua, pero también se refiere a la administración y el control de esa capacidad para garantizar que atiende las solicitudes de carga válidas. Se recomienda que los clientes sigan las instrucciones recomendadas para asegurarse de que tienen la mejor experiencia. También significa que tenemos patrones y controles de limitación de peticiones para garantizar que no se permite el comportamiento "abusivo" en el servicio. Aunque no todo el comportamiento "malo" es intencionado, debemos asegurarnos de que limitamos el efecto de ese comportamiento. Para obtener más información sobre la limitación y cómo evitarlo, consulte el artículo sobre [Cómo evitar limitaciones de uso](https://docs.microsoft.com/sharepoint/dev/general-development/how-to-avoid-getting-throttled-or-blocked-in-sharepoint-online) .

## <a name="why-you-cannot-load-test-sharepoint-online"></a>Por qué no se puede cargar SharePoint Online de prueba
Con los entornos locales, las pruebas de carga se usan para validar la hipótesis de escala y, en última instancia, buscar el punto de ruptura de una granja de servidores; mediante saturarla con la carga. 

Con SharePoint Online, debemos hacer cosas de forma diferente porque la escala es relativamente fluida y se ajusta, limita y controla la carga, según ciertas heurísticas. Como un entorno multiempresa escalable de gran tamaño, debemos proteger todos los inquilinos de la misma granja de servidores, por lo que se limitarán automáticamente las pruebas de carga. Si, por el contrario, intenta la prueba de carga, además de limitarse, recibirá los resultados disimulables y potencialmente engañosos, ya que es probable que la granja de servidores que probó en la actualidad haya tenido cambios de escala durante la ventana de pruebas o en el horario de las pruebas, como la escala y las acciones de equilibrio de la granja de servidores se realizan de manera continua.

En lugar de intentar cargar SharePoint de prueba como un servicio, céntrese en seguir los procedimientos recomendados y siga las instrucciones para [crear, iniciar y mantener una guía del portal saludable](https://go.microsoft.com/fwlink/?linkid=2105838) .
