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
description: En este artículo se muestra cómo diagnosticar problemas comunes relacionados con el sitio de SharePoint Online mediante las herramientas de desarrollo de Internet Explorer.
ms.openlocfilehash: 89d4544bfabf6424b5f401bad7d63bd7fa41b5ca
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33492296"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a>Diagnosticar problemas de rendimiento con SharePoint Online

En este artículo se muestra cómo diagnosticar problemas comunes relacionados con el sitio de SharePoint Online mediante las herramientas de desarrollo de Internet Explorer.
  
Hay tres formas diferentes de identificar que una página de un sitio de SharePoint Online tiene un problema de rendimiento con las personalizaciones.
  
- El monitor de red de la barra de herramientas F12
    
- Comparación con una línea base no personalizada
    
- Métricas del encabezado de respuesta de SharePoint Online
    
En este tema se describe cómo usar cada uno de estos métodos para diagnosticar problemas de rendimiento. Una vez que haya averiguado la causa del problema, puede trabajar en una solución con los artículos sobre cómo mejorar el rendimiento de SharePoint que puede encontrar http://aka.ms/tuneen.
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a>Usar la barra de herramientas F12 para diagnosticar el rendimiento en SharePoint Online
<a name="F12ToolInfo"> </a>

En este artículo se usa Internet Explorer 11. Las versiones de las herramientas de desarrollo F12 en otros exploradores tienen características parecidas, aunque pueden tener un aspecto ligeramente diferente. Para obtener información sobre las herramientas de desarrollo F12, consulte:
  
- [Novedades de las herramientas F12](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [Usar las herramientas de desarrollo F12](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
Para que aparezcan las herramientas de desarrollo, presione **F12** y, a continuación, haga clic en el icono Wi-Fi: 
  
![Captura de pantalla del icono wifi de herramientas de desarrollo F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
En la pestaña **red** , presione el botón verde de reproducción para cargar una página. La herramienta devuelve todos los archivos que el explorador solicita para obtener la página que solicitó. En la siguiente captura de pantalla se muestra una lista de este tipo. 
  
![Captura de pantalla de la lista de archivos que se devuelve con una solicitud de página.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
También puede ver los tiempos de descarga de los archivos en el lado derecho, tal y como se muestra en esta captura de pantalla.
  
![Diagrama que muestra el tiempo empleado en cargar las páginas solicitadas desde SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
Esto le proporciona una representación visual del tiempo que tardó en cargarse el archivo. La línea verde representa cuando la página está preparada para que el explorador la represente. Esto puede proporcionarle una vista rápida de los distintos archivos que podrían estar causando una carga lenta de páginas en el sitio.
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a>Configurar una línea base no personalizada para SharePoint Online
<a name="F12ToolInfo"> </a>

La mejor manera de determinar el rendimiento de su sitio puntos débiles es configurar una colección de sitios predefinida completamente en SharePoint Online. De esta forma, podrá comparar todos los diversos aspectos de su sitio con lo que obtendría sin personalización en la página. La Página principal de OneDrive para la empresa es un buen ejemplo de una colección de sitios independiente que es improbable que tenga personalizaciones.
  
## <a name="viewing-sharepoint-response-header-information"></a>Visualización de la información del encabezado de respuesta de SharePoint
<a name="F12ToolInfo"> </a>

En SharePoint Online y SharePoint Server 2013, puede tener acceso a la información que se envía de vuelta al explorador en el encabezado de respuesta para cada archivo. Los dos valores más útiles para diagnosticar problemas de rendimiento son SPRequestDuration y X-SharePointHealthScore:
  
- **SPRequestDuration**
    
    Esta es la cantidad de tiempo que la solicitud tardó en procesar el servidor. Esto puede ayudar a determinar si la solicitud es muy pesada y utiliza muchos recursos. Este es el mejor conocimiento que tiene sobre la cantidad de trabajo que el servidor está haciendo para atender la página.
    
- **X-SharePointHealthScore**
    
    Esto indica la utilización del servidor, o CPU, en el que se ejecuta la instancia de SharePoint. Este número oscila entre 0 y 10, donde 0 indica que el servidor está inactivo y 10 indica que el servidor está muy ocupado. Un HealthScore que es siempre 9 o 10, puede indicar un problema de rendimiento continuado con el servidor. Cualquier otro número indica que el servidor está funcionando dentro del intervalo esperado.
    
 **Para ver la información del encabezado de respuesta de SharePoint**
  
1. Asegúrese de que tiene instaladas las herramientas F12. Para obtener más información sobre cómo descargar e instalar estas herramientas, consulte [what's New in F12 Tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).
    
2. En las herramientas F12, en la pestaña **red** , haga clic en el botón verde reproducir para cargar una página. 
    
3. Haga clic en uno de los archivos. aspx devueltos por la herramienta y, a continuación, haga clic en **detalles**. 
    
    ![Muestra los detalles del encabezado de respuesta](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. Haga clic en **encabezados de respuesta**. 
    
    ![Diagrama que muestra la dirección URL del encabezado de respuesta](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a>¿Qué está causando problemas de rendimiento en SharePoint Online?
<a name="F12ToolInfo"> </a>

El artículo [Opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md) muestra un ejemplo de cómo usar el valor SPRequestDuration para determinar que la complicada navegación estructural hacía que la página tardara mucho tiempo en procesarse en el servidor. Al tomar un valor para un sitio de línea base (sin personalización), es posible determinar si un archivo determinado tarda mucho tiempo en cargarse. El ejemplo que se usa en [las opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md) es el archivo. aspx principal. Ese archivo contiene la mayor parte del código de ASP.NET que se ejecuta para la carga de la página. En función de la plantilla de sitio que use, podría ser Start. aspx, Home. aspx, default. aspx u otro nombre si Personaliza la Página principal. Si este número es considerablemente superior al sitio de línea de base, es una buena indicación de que hay algo complejo en la página que está causando problemas de rendimiento. 
  
Una vez que haya identificado que hay un problema específico de su sitio, la forma recomendada para averiguar qué causa el bajo rendimiento es eliminar todas las causas posibles, como las personalizaciones de páginas y, a continuación, volver a agregarlas al sitio de una en una. Una vez que haya quitado las personalizaciones suficientes que la página está funcionando correctamente, puede Agregar personalizaciones específicas de una en una.
  
Por ejemplo, si tiene una navegación muy compleja, intente cambiar la navegación para que no se muestren los subsitios y, después, revise las herramientas de desarrollo para ver si esto supone una diferencia. O bien, si tiene una gran cantidad de contenido acumulado, pruebe a quitarlos de la página y ver si esto mejora las cosas. Si elimina todas las causas posibles y las agrega de nuevo de una en una, puede identificar fácilmente qué características son el mayor problema y, a continuación, trabajar hacia una solución.
  

