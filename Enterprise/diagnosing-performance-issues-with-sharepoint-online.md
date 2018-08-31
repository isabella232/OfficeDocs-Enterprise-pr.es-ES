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
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="da4e2-103">Diagnosticar problemas de rendimiento con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="da4e2-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="da4e2-104">En este artículo se muestra cómo puede diagnosticar problemas comunes con su sitio de SharePoint Online con las herramientas para desarrolladores de Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="da4e2-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="da4e2-105">Existen tres maneras diferentes de identificar que una página en un sitio de SharePoint Online tiene un problema de rendimiento con las personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="da4e2-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="da4e2-106">El monitor de red de la barra de herramientas F12</span><span class="sxs-lookup"><span data-stu-id="da4e2-106">The F12 tool bar network monitor</span></span>
    
- <span data-ttu-id="da4e2-107">Comparación con una línea base no personalizada</span><span class="sxs-lookup"><span data-stu-id="da4e2-107">Comparison to a non-customized baseline</span></span>
    
- <span data-ttu-id="da4e2-108">Métricas de encabezado de respuesta de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="da4e2-108">SharePoint Online response header metrics</span></span>
    
<span data-ttu-id="da4e2-p101">En este tema se describe cómo usar cada uno de estos métodos para diagnosticar problemas de rendimiento. Una vez que ha podido averiguar la causa del problema, puede trabajar hacia una solución mediante los artículos sobre cómo mejorar el rendimiento de SharePoint que puede encontrar en http://aka.ms/tune.</span><span class="sxs-lookup"><span data-stu-id="da4e2-p101">This topic describes how to use each of these methods to diagnose performance issues. Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on http://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="da4e2-111">Usar la barra de herramientas F12 para diagnosticar el rendimiento en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="da4e2-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="da4e2-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="da4e2-112"></span></span>

<span data-ttu-id="da4e2-p102">En este artículo se utiliza Internet Explorer 11. Las versiones de las herramientas de desarrollo F12 en otros exploradores tienen características similares, aunque pueden tener una apariencia ligeramente distinta. Para obtener más información sobre las herramientas de desarrollo F12, consulte:</span><span class="sxs-lookup"><span data-stu-id="da4e2-p102">In this article we use Internet Explorer 11. Versions of the F12 developer tools on other browsers have similar features though they may look slightly different. For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="da4e2-116">Novedades en las herramientas F12</span><span class="sxs-lookup"><span data-stu-id="da4e2-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)
    
- [<span data-ttu-id="da4e2-117">Uso de las herramientas de desarrollo F12</span><span class="sxs-lookup"><span data-stu-id="da4e2-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)
    
<span data-ttu-id="da4e2-118">Para que aparezcan las herramientas de desarrollo, presione **F12** y, a continuación, haga clic en el icono de Wi-Fi: 
</span><span class="sxs-lookup"><span data-stu-id="da4e2-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span> 
  
![Captura de pantalla del icono wifi de herramientas de desarrollo F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="da4e2-p103">En la ficha **Red**, presione el botón verde de reproducción para cargar una página. La herramienta devuelve todos los archivos que solicita el explorador para obtener la página que usted solicitó. La captura de pantalla siguiente muestra una lista de estas características.</span><span class="sxs-lookup"><span data-stu-id="da4e2-p103">On the **Network** tab, press the green play button to load a page. The tool returns all of the files that the browser requests in order to get the page you asked for. The following screen shot shows one such list.</span></span> 
  
![Captura de pantalla de la lista de archivos que se devuelve con una solicitud de página.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="da4e2-124">También puede ver los tiempos de descarga de los archivos en el lado derecho como se muestra en esta captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="da4e2-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![Diagrama que muestra el tiempo empleado en cargar las páginas solicitadas desde SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="da4e2-p104">Esto le proporciona una representación visual del tiempo empleado en cargar el archivo. La línea verde representa cuándo está lista la página para que el explorador la presente. De esta manera, usted puede obtener una vista rápida de los diferentes archivos que podrían estar causando cargas de página lentas en su sitio.

</span><span class="sxs-lookup"><span data-stu-id="da4e2-p104">This gives you a visual representation of how long the file took to load. The green line represents when the page is ready to be rendered by the browser. This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="da4e2-129">Configuración de una línea de base no personalizados para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="da4e2-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="da4e2-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="da4e2-130"></span></span>

<span data-ttu-id="da4e2-p105">Es la mejor forma de determinar los puntos débiles del rendimiento de su sitio configurar una colección de sitios de completamente-de-fábrica en SharePoint Online. De este modo puede comparar todos los diversos aspectos de su sitio con lo que se obtiene con sin personalización en la página. La OneDrive para la página principal de negocio es un buen ejemplo de una colección de sitios independiente que es poco probable que tienen las personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="da4e2-p105">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online. This way you can compare all the various aspects of your site with what you would get with no customization on the page. The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="da4e2-134">Ver información de encabezados de respuesta de SharePoint</span><span class="sxs-lookup"><span data-stu-id="da4e2-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="da4e2-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="da4e2-135"></span></span>

<span data-ttu-id="da4e2-p106">En SharePoint Online y SharePoint Server 2013 puede tener acceso a la información que se envía al explorador en el encabezado de respuesta para cada archivo. Los dos valores más útiles para diagnosticar problemas de rendimiento son SPRequestDuration y X-SharePointHealthScore:</span><span class="sxs-lookup"><span data-stu-id="da4e2-p106">In SharePoint Online and SharePoint Server 2013 you can access the information that is sent back to the browser in the response header for each file. The two most useful values for diagnosing performance issues are SPRequestDuration and X-SharePointHealthScore:</span></span>
  
- <span data-ttu-id="da4e2-138">**SPRequestDuration**</span><span class="sxs-lookup"><span data-stu-id="da4e2-138">**SPRequestDuration**</span></span>
    
    <span data-ttu-id="da4e2-p107">Es la cantidad de tiempo que la solicitud empleó en el servidor para su procesamiento. Puede ayudar a determinar si la solicitud es muy pesada y hace uso intensivo de recursos. Es la mejor información que usted tiene en cuanto a la cantidad de trabajo que el servidor está haciendo para servir la página.</span><span class="sxs-lookup"><span data-stu-id="da4e2-p107">This is the amount of time that the request took on the server to be processed. This can help determine if the request is very heavy and resource intensive. This is the best insight you have into how much work the server is doing to serve the page.</span></span>
    
- <span data-ttu-id="da4e2-142">**X-SharePointHealthScore**</span><span class="sxs-lookup"><span data-stu-id="da4e2-142">**X-SharePointHealthScore**</span></span>
    
    <span data-ttu-id="da4e2-p108">Esto indica que el uso del servidor o la CPU, en el que se ejecuta la instancia de SharePoint. Este número va de 0 a 10, donde 0 indica que el servidor está inactivo y 10 indica que el servidor está ocupado. Una puntuación de estado que sea coherente 9 o 10 podría indicar un problema de rendimiento en curso con el servidor. Cualquier otro número indica que ese servidor está funcionando dentro del intervalo esperado.</span><span class="sxs-lookup"><span data-stu-id="da4e2-p108">This indicates the utilization of the server, or CPU, on which your SharePoint instance runs. This number ranges from 0 to 10 where 0 indicates the server is idle and 10 indicates the server is very busy. A HealthScore that is consistently 9 or 10 might indicate an ongoing performance issue with the server. Any other number indicates that server is operating within the expected range.</span></span>
    
 <span data-ttu-id="da4e2-147">**Para ver información de encabezados de respuesta de SharePoint**</span><span class="sxs-lookup"><span data-stu-id="da4e2-147">**To view SharePoint response header information**</span></span>
  
1. <span data-ttu-id="da4e2-p109">Asegúrese de que tiene instaladas las herramientas F12. Para obtener más información sobre cómo descargar e instalar estas herramientas, vea [Novedades de herramientas F12](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span><span class="sxs-lookup"><span data-stu-id="da4e2-p109">Ensure that you have the F12 tools installed. For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>
    
2. <span data-ttu-id="da4e2-150">En las herramientas F12, en la ficha **Red**, presione el botón verde de reproducción para cargar una página.</span><span class="sxs-lookup"><span data-stu-id="da4e2-150">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span> 
    
3. <span data-ttu-id="da4e2-151">Haga clic en uno de los archivos .aspx devueltos por la herramienta y, a continuación, haga clic en **DETALLES**.</span><span class="sxs-lookup"><span data-stu-id="da4e2-151">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span> 
    
    ![Muestra los detalles del encabezado de respuesta](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="da4e2-153">Haga clic en **Encabezados de respuesta**.</span><span class="sxs-lookup"><span data-stu-id="da4e2-153">Click **Response headers**.</span></span> 
    
    ![Diagrama que muestra la dirección URL del encabezado de respuesta](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="da4e2-155">¿Qué está causando problemas de rendimiento en SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="da4e2-155">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="da4e2-156"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="da4e2-156"></span></span>

<span data-ttu-id="da4e2-p110">El artículo [Opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md) , muestra un ejemplo de utilizando el valor de SPRequestDuration para determinar que la navegación estructural complicada fue lo que provoca que la página que se va a tardar mucho tiempo en procesar en el servidor. Siguiendo un valor para un sitio de línea base (sin personalización), es posible determinar si cualquier archivo determinado tarda mucho tiempo en cargar. En el ejemplo se usa en [las opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md) es el archivo .aspx principal. Ese archivo contiene la mayor parte del código ASP.NET que se ejecuta para la carga de página. Dependiendo de la plantilla de sitio que utiliza, podría tratarse start.aspx, home.aspx, default.aspx o cualquier otro nombre si personalizar la página principal. Si este número es considerablemente superior a su sitio de línea de base, es una buena indicación de que hay algo complejo sucede en la página que está causando problemas de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="da4e2-p110">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server. By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load. The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file. That file contains most of the ASP.NET code that runs for your page load. Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page. If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span> 
  
<span data-ttu-id="da4e2-p111">Una vez que haya identificado que se trata de un problema específico de su sitio, el método recomendado para averiguar qué está causando un bajo rendimiento es eliminar todas las causas posibles, como personalizaciones de página y, a continuación, volver a agregarlas en el sitio de una en una. Cuando haya quitado suficientes personalizaciones y la página funcione bien, podrá volver a agregar personalizaciones específicas de una en una.</span><span class="sxs-lookup"><span data-stu-id="da4e2-p111">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one. Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="da4e2-p112">Por ejemplo, si tiene una navegación muy compleja, intente cambiar la navegación para no mostrar los subsitios y luego revise las herramientas de desarrollo para ver si hay una diferencia. O bien, si tiene una gran cantidad de informes de contenido, intente quitarlos de la página y ver si esto mejora la situación. Si elimina todas las causas posibles y vuelve a agregarlas de una en una, puede identificar fácilmente qué características son el principal problema y trabajar en una solución. 
</span><span class="sxs-lookup"><span data-stu-id="da4e2-p112">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference. Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things. If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
  

