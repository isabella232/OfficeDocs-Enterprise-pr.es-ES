---
title: Diagnosticar problemas de rendimiento con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 2/23/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: En este artículo se muestra cómo puede diagnosticar problemas comunes con su sitio de SharePoint Online con las herramientas para desarrolladores de Internet Explorer.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542856"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnosticar problemas de rendimiento con SharePoint Online

En este artículo se muestra cómo puede diagnosticar problemas comunes con su sitio de SharePoint Online con las herramientas para desarrolladores de Internet Explorer.
  
Existen tres maneras diferentes de identificar que una página en un sitio de SharePoint Online tiene un problema de rendimiento con las personalizaciones.
  
- El monitor de red de la barra de herramientas F12
    
- Comparación con una línea base no personalizada
    
- Métricas de encabezado de respuesta de SharePoint Online
    
En este tema se describe cómo usar cada uno de estos métodos para diagnosticar problemas de rendimiento. Una vez que ha podido averiguar la causa del problema, puede trabajar hacia una solución mediante los artículos sobre cómo mejorar el rendimiento de SharePoint que puede encontrar en http://aka.ms/tune.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Usar la barra de herramientas F12 para diagnosticar el rendimiento en SharePoint Online
<a name="F12ToolInfo"> </a>

En este artículo se utiliza Internet Explorer 11. Las versiones de las herramientas de desarrollo F12 en otros exploradores tienen características similares, aunque pueden tener una apariencia ligeramente distinta. Para obtener más información sobre las herramientas de desarrollo F12, consulte:
  
- [Novedades en las herramientas F12](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [Uso de las herramientas de desarrollo F12](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
Para que aparezcan las herramientas de desarrollo, presione **F12** y, a continuación, haga clic en el icono de Wi-Fi: 
 
  
![Captura de pantalla del icono wifi de herramientas de desarrollo F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
En la ficha **Red**, presione el botón verde de reproducción para cargar una página. La herramienta devuelve todos los archivos que solicita el explorador para obtener la página que usted solicitó. La captura de pantalla siguiente muestra una lista de estas características. 
  
![Captura de pantalla de la lista de archivos que se devuelve con una solicitud de página.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
También puede ver los tiempos de descarga de los archivos en el lado derecho como se muestra en esta captura de pantalla.
  
![Diagrama que muestra el tiempo empleado en cargar las páginas solicitadas desde SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Esto le proporciona una representación visual del tiempo empleado en cargar el archivo. La línea verde representa cuándo está lista la página para que el explorador la presente. De esta manera, usted puede obtener una vista rápida de los diferentes archivos que podrían estar causando cargas de página lentas en su sitio.


  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Configuración de una línea de base no personalizados para SharePoint Online
<a name="F12ToolInfo"> </a>

Es la mejor forma de determinar los puntos débiles del rendimiento de su sitio configurar una colección de sitios de completamente-de-fábrica en SharePoint Online. De este modo puede comparar todos los diversos aspectos de su sitio con lo que se obtiene con sin personalización en la página. La OneDrive para la página principal de negocio es un buen ejemplo de una colección de sitios independiente que es poco probable que tienen las personalizaciones.
  
## <a name="viewing-sharepoint-response-header-information"></a>Ver información de encabezados de respuesta de SharePoint
<a name="F12ToolInfo"> </a>

En SharePoint Online y SharePoint Server 2013 puede tener acceso a la información que se envía al explorador en el encabezado de respuesta para cada archivo. Los dos valores más útiles para diagnosticar problemas de rendimiento son SPRequestDuration y X-SharePointHealthScore:
  
- **SPRequestDuration**
    
    Es la cantidad de tiempo que la solicitud empleó en el servidor para su procesamiento. Puede ayudar a determinar si la solicitud es muy pesada y hace uso intensivo de recursos. Es la mejor información que usted tiene en cuanto a la cantidad de trabajo que el servidor está haciendo para servir la página.
    
- **X-SharePointHealthScore**
    
    Esto indica que el uso del servidor o la CPU, en el que se ejecuta la instancia de SharePoint. Este número va de 0 a 10, donde 0 indica que el servidor está inactivo y 10 indica que el servidor está ocupado. Una puntuación de estado que sea coherente 9 o 10 podría indicar un problema de rendimiento en curso con el servidor. Cualquier otro número indica que ese servidor está funcionando dentro del intervalo esperado.
    
 **Para ver información de encabezados de respuesta de SharePoint**
  
1. Asegúrese de que tiene instaladas las herramientas F12. Para obtener más información sobre cómo descargar e instalar estas herramientas, vea [Novedades de herramientas F12](https://go.microsoft.com/fwlink/p/?LinkId=522545).
    
2. En las herramientas F12, en la ficha **Red**, presione el botón verde de reproducción para cargar una página. 
    
3. Haga clic en uno de los archivos .aspx devueltos por la herramienta y, a continuación, haga clic en **DETALLES**. 
    
    ![Muestra los detalles del encabezado de respuesta](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Haga clic en **Encabezados de respuesta**. 
    
    ![Diagrama que muestra la dirección URL del encabezado de respuesta](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>¿Qué está causando problemas de rendimiento en SharePoint Online?
<a name="F12ToolInfo"> </a>

El artículo [Opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md) , muestra un ejemplo de utilizando el valor de SPRequestDuration para determinar que la navegación estructural complicada fue lo que provoca que la página que se va a tardar mucho tiempo en procesar en el servidor. Siguiendo un valor para un sitio de línea base (sin personalización), es posible determinar si cualquier archivo determinado tarda mucho tiempo en cargar. En el ejemplo se usa en [las opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md) es el archivo .aspx principal. Ese archivo contiene la mayor parte del código ASP.NET que se ejecuta para la carga de página. Dependiendo de la plantilla de sitio que utiliza, podría tratarse start.aspx, home.aspx, default.aspx o cualquier otro nombre si personalizar la página principal. Si este número es considerablemente superior a su sitio de línea de base, es una buena indicación de que hay algo complejo sucede en la página que está causando problemas de rendimiento. 
  
Una vez que haya identificado que se trata de un problema específico de su sitio, el método recomendado para averiguar qué está causando un bajo rendimiento es eliminar todas las causas posibles, como personalizaciones de página y, a continuación, volver a agregarlas en el sitio de una en una. Cuando haya quitado suficientes personalizaciones y la página funcione bien, podrá volver a agregar personalizaciones específicas de una en una.
  
Por ejemplo, si tiene una navegación muy compleja, intente cambiar la navegación para no mostrar los subsitios y luego revise las herramientas de desarrollo para ver si hay una diferencia. O bien, si tiene una gran cantidad de informes de contenido, intente quitarlos de la página y ver si esto mejora la situación. Si elimina todas las causas posibles y vuelve a agregarlas de una en una, puede identificar fácilmente qué características son el principal problema y trabajar en una solución. 

  

