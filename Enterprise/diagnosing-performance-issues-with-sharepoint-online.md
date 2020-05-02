---
title: Diagnosticar problemas de rendimiento con SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 7/9/2019
audience: Admin
ms.topic: troubleshooting
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
ms.assetid: 3c364f9e-b9f6-4da4-a792-c8e8c8cd2e86
description: En este artículo se muestra cómo diagnosticar problemas comunes relacionados con el sitio de SharePoint Online mediante las herramientas de desarrollo de Internet Explorer.
ms.openlocfilehash: 06b9958953b55c70fe52981cd55d24c00faa490e
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004593"
---
# <a name="diagnosing-performance-issues-with-sharepoint-online"></a><span data-ttu-id="5e1db-103">Diagnosticar problemas de rendimiento con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5e1db-103">Diagnosing performance issues with SharePoint Online</span></span>

<span data-ttu-id="5e1db-104">En este artículo se muestra cómo diagnosticar problemas comunes relacionados con el sitio de SharePoint Online mediante las herramientas de desarrollo de Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="5e1db-104">This article shows you how you can diagnose common issues with your SharePoint Online site using Internet Explorer developer tools.</span></span>
  
<span data-ttu-id="5e1db-105">Hay tres formas diferentes de identificar que una página de un sitio de SharePoint Online tiene un problema de rendimiento con las personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="5e1db-105">There are three different ways that you can identify that a page on a SharePoint Online site has a performance problem with the customizations.</span></span>
  
- <span data-ttu-id="5e1db-106">El monitor de red de la barra de herramientas F12</span><span class="sxs-lookup"><span data-stu-id="5e1db-106">The F12 tool bar network monitor</span></span>

- <span data-ttu-id="5e1db-107">Comparación con una línea base no personalizada</span><span class="sxs-lookup"><span data-stu-id="5e1db-107">Comparison to a non-customized baseline</span></span>

- <span data-ttu-id="5e1db-108">Métricas del encabezado de respuesta de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5e1db-108">SharePoint Online response header metrics</span></span>

<span data-ttu-id="5e1db-109">En este tema se describe cómo usar cada uno de estos métodos para diagnosticar problemas de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="5e1db-109">This topic describes how to use each of these methods to diagnose performance issues.</span></span> <span data-ttu-id="5e1db-110">Una vez que haya averiguado la causa del problema, puede trabajar en una solución con los artículos sobre cómo mejorar el rendimiento de SharePoint que puede encontrar https://aka.ms/tuneen.</span><span class="sxs-lookup"><span data-stu-id="5e1db-110">Once you've figured out the cause of the problem, you can work toward a solution using the articles about improving SharePoint performance that you can find on https://aka.ms/tune.</span></span>
  
## <a name="using-the-f12-tool-bar-to-diagnose-performance-in-sharepoint-online"></a><span data-ttu-id="5e1db-111">Usar la barra de herramientas F12 para diagnosticar el rendimiento en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5e1db-111">Using the F12 tool bar to diagnose performance in SharePoint Online</span></span>
<span data-ttu-id="5e1db-112"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="5e1db-112"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="5e1db-113">En este artículo se usa Internet Explorer 11.</span><span class="sxs-lookup"><span data-stu-id="5e1db-113">In this article we use Internet Explorer 11.</span></span> <span data-ttu-id="5e1db-114">Las versiones de las herramientas de desarrollo F12 en otros exploradores tienen características parecidas, aunque pueden tener un aspecto ligeramente diferente.</span><span class="sxs-lookup"><span data-stu-id="5e1db-114">Versions of the F12 developer tools on other browsers have similar features though they may look slightly different.</span></span> <span data-ttu-id="5e1db-115">Para obtener información sobre las herramientas de desarrollo F12, consulte:</span><span class="sxs-lookup"><span data-stu-id="5e1db-115">For information on the F12 developer tools, see:</span></span>
  
- [<span data-ttu-id="5e1db-116">Novedades de las herramientas F12</span><span class="sxs-lookup"><span data-stu-id="5e1db-116">What's new in F12 Tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522545)

- [<span data-ttu-id="5e1db-117">Usar las herramientas de desarrollo F12</span><span class="sxs-lookup"><span data-stu-id="5e1db-117">Using the F12 developer tools</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=522546)

<span data-ttu-id="5e1db-118">Para que aparezcan las herramientas de desarrollo, presione **F12** y, a continuación, haga clic en el icono Wi-Fi:</span><span class="sxs-lookup"><span data-stu-id="5e1db-118">To bring up the developer tools press **F12** and then click the Wi-Fi icon:</span></span>
  
![Captura de pantalla del icono wifi de herramientas de desarrollo F12](media/27acacbb-5688-459a-aa2f-5c8c5f17b76e.png)
  
<span data-ttu-id="5e1db-120">En la pestaña **red** , presione el botón verde de reproducción para cargar una página.</span><span class="sxs-lookup"><span data-stu-id="5e1db-120">On the **Network** tab, press the green play button to load a page.</span></span> <span data-ttu-id="5e1db-121">La herramienta devuelve todos los archivos que el explorador solicita para obtener la página que solicitó.</span><span class="sxs-lookup"><span data-stu-id="5e1db-121">The tool returns all of the files that the browser requests in order to get the page you asked for.</span></span> <span data-ttu-id="5e1db-122">En la siguiente captura de pantalla se muestra una lista de este tipo.</span><span class="sxs-lookup"><span data-stu-id="5e1db-122">The following screen shot shows one such list.</span></span>
  
![Captura de pantalla de la lista de archivos que se devuelve con una solicitud de página.](media/247a9422-76da-4b0c-bed3-ce77b05e4560.png)
  
<span data-ttu-id="5e1db-124">También puede ver los tiempos de descarga de los archivos en el lado derecho, tal y como se muestra en esta captura de pantalla.</span><span class="sxs-lookup"><span data-stu-id="5e1db-124">You can also see the download times of the files on the right side as shown in this screen shot.</span></span>
  
![Diagrama que muestra el tiempo empleado en cargar las páginas solicitadas desde SharePoint](media/d71ad1fa-9018-4fae-82eb-c1838e7db0ff.png)
  
<span data-ttu-id="5e1db-126">Esto le proporciona una representación visual del tiempo que tardó en cargarse el archivo.</span><span class="sxs-lookup"><span data-stu-id="5e1db-126">This gives you a visual representation of how long the file took to load.</span></span> <span data-ttu-id="5e1db-127">La línea verde representa cuando la página está preparada para que el explorador la represente.</span><span class="sxs-lookup"><span data-stu-id="5e1db-127">The green line represents when the page is ready to be rendered by the browser.</span></span> <span data-ttu-id="5e1db-128">Esto puede proporcionarle una vista rápida de los distintos archivos que podrían estar causando una carga lenta de páginas en el sitio.</span><span class="sxs-lookup"><span data-stu-id="5e1db-128">This can give you a quick view of the different files that might be causing slow page loads on your site.</span></span>
  
## <a name="setting-up-a-non-customized-baseline-for-sharepoint-online"></a><span data-ttu-id="5e1db-129">Configurar una línea base no personalizada para SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5e1db-129">Setting up a non-customized baseline for SharePoint Online</span></span>
<span data-ttu-id="5e1db-130"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="5e1db-130"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="5e1db-131">La mejor manera de determinar el rendimiento de su sitio puntos débiles es configurar una colección de sitios predefinida completamente en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="5e1db-131">The best way to determine your site's performance weak points is to set up a completely out-of-the-box site collection in SharePoint Online.</span></span> <span data-ttu-id="5e1db-132">De esta forma, podrá comparar todos los diversos aspectos de su sitio con lo que obtendría sin personalización en la página.</span><span class="sxs-lookup"><span data-stu-id="5e1db-132">This way you can compare all the various aspects of your site with what you would get with no customization on the page.</span></span> <span data-ttu-id="5e1db-133">La Página principal de OneDrive para la empresa es un buen ejemplo de una colección de sitios independiente que es improbable que tenga personalizaciones.</span><span class="sxs-lookup"><span data-stu-id="5e1db-133">The OneDrive for Business home page is a good example of a separate site collection that is unlikely to have any customizations.</span></span>
  
## <a name="viewing-sharepoint-response-header-information"></a><span data-ttu-id="5e1db-134">Visualización de la información del encabezado de respuesta de SharePoint</span><span class="sxs-lookup"><span data-stu-id="5e1db-134">Viewing SharePoint response header information</span></span>
<span data-ttu-id="5e1db-135"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="5e1db-135"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="5e1db-136">En SharePoint Online, puede tener acceso a la información que se envía de vuelta al explorador en el encabezado de respuesta para cada archivo.</span><span class="sxs-lookup"><span data-stu-id="5e1db-136">In SharePoint Online, you can access the information that is sent back to the browser in the response header for each file.</span></span> <span data-ttu-id="5e1db-137">El valor más útil para diagnosticar problemas de rendimiento es **SPRequestDuration**, que muestra la cantidad de tiempo que la solicitud tardó en procesar el servidor.</span><span class="sxs-lookup"><span data-stu-id="5e1db-137">The most useful value for diagnosing performance issues is **SPRequestDuration**, which displays the amount of time that the request took on the server to be processed.</span></span> <span data-ttu-id="5e1db-138">Esto puede ayudar a determinar si la solicitud es muy pesada y utiliza muchos recursos.</span><span class="sxs-lookup"><span data-stu-id="5e1db-138">This can help determine if the request is very heavy and resource intensive.</span></span> <span data-ttu-id="5e1db-139">Este es el mejor conocimiento que tiene sobre la cantidad de trabajo que el servidor está haciendo para atender la página.</span><span class="sxs-lookup"><span data-stu-id="5e1db-139">This is the best insight you have into how much work the server is doing to serve the page.</span></span>

### <a name="to-view-sharepoint-response-header-information"></a><span data-ttu-id="5e1db-140">Para ver la información del encabezado de respuesta de SharePoint</span><span class="sxs-lookup"><span data-stu-id="5e1db-140">To view SharePoint response header information</span></span>
  
1. <span data-ttu-id="5e1db-141">Asegúrese de que tiene instaladas las herramientas F12.</span><span class="sxs-lookup"><span data-stu-id="5e1db-141">Ensure that you have the F12 tools installed.</span></span> <span data-ttu-id="5e1db-142">Para obtener más información sobre cómo descargar e instalar estas herramientas, consulte [what's New in F12 Tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span><span class="sxs-lookup"><span data-stu-id="5e1db-142">For more information on downloading and installing these tools, see [What's new in F12 tools](https://go.microsoft.com/fwlink/p/?LinkId=522545).</span></span>

2. <span data-ttu-id="5e1db-143">En las herramientas F12, en la pestaña **red** , haga clic en el botón verde reproducir para cargar una página.</span><span class="sxs-lookup"><span data-stu-id="5e1db-143">In the F12 tools, on the **Network** tab, press the green play button to load a page.</span></span>

3. <span data-ttu-id="5e1db-144">Haga clic en uno de los archivos. aspx devueltos por la herramienta y, a continuación, haga clic en **detalles**.</span><span class="sxs-lookup"><span data-stu-id="5e1db-144">Click one of the .aspx files returned by the tool and then click **DETAILS**.</span></span>

    ![Muestra los detalles del encabezado de respuesta](media/1f8a044a-caf8-4613-be2b-7e064141ac8a.png)
  
4. <span data-ttu-id="5e1db-146">Haga clic en **encabezados de respuesta**.</span><span class="sxs-lookup"><span data-stu-id="5e1db-146">Click **Response headers**.</span></span>

    ![Diagrama que muestra la dirección URL del encabezado de respuesta](media/efc7076e-447e-447e-882a-ae3aa721e2c3.png)
  
## <a name="whats-causing-performance-issues-in-sharepoint-online"></a><span data-ttu-id="5e1db-148">¿Qué está causando problemas de rendimiento en SharePoint Online?</span><span class="sxs-lookup"><span data-stu-id="5e1db-148">What's causing performance issues in SharePoint Online?</span></span>
<span data-ttu-id="5e1db-149"><a name="F12ToolInfo"> </a></span><span class="sxs-lookup"><span data-stu-id="5e1db-149"><a name="F12ToolInfo"> </a></span></span>

<span data-ttu-id="5e1db-150">El artículo [Opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md) muestra un ejemplo de cómo usar el valor SPRequestDuration para determinar que la complicada navegación estructural hacía que la página tardara mucho tiempo en procesarse en el servidor.</span><span class="sxs-lookup"><span data-stu-id="5e1db-150">The article [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) shows an example of using the SPRequestDuration value to determine that the complicated structural navigation was causing the page to take a long time to process on the server.</span></span> <span data-ttu-id="5e1db-151">Al tomar un valor para un sitio de línea base (sin personalización), es posible determinar si un archivo determinado tarda mucho tiempo en cargarse.</span><span class="sxs-lookup"><span data-stu-id="5e1db-151">By taking a value for a baseline site (without customization), it is possible to determine if any given file is taking a long time to load.</span></span> <span data-ttu-id="5e1db-152">El ejemplo que se usa en [las opciones de navegación para SharePoint Online](navigation-options-for-sharepoint-online.md) es el archivo. aspx principal.</span><span class="sxs-lookup"><span data-stu-id="5e1db-152">The example used in [Navigation options for SharePoint Online](navigation-options-for-sharepoint-online.md) is the main .aspx file.</span></span> <span data-ttu-id="5e1db-153">Ese archivo contiene la mayor parte del código de ASP.NET que se ejecuta para la carga de la página.</span><span class="sxs-lookup"><span data-stu-id="5e1db-153">That file contains most of the ASP.NET code that runs for your page load.</span></span> <span data-ttu-id="5e1db-154">En función de la plantilla de sitio que use, podría ser Start. aspx, Home. aspx, default. aspx u otro nombre si Personaliza la Página principal.</span><span class="sxs-lookup"><span data-stu-id="5e1db-154">Depending on the site template you use, this could be start.aspx, home.aspx, default.aspx, or another name if you customize the home page.</span></span> <span data-ttu-id="5e1db-155">Si este número es considerablemente superior al sitio de línea de base, es una buena indicación de que hay algo complejo en la página que está causando problemas de rendimiento.</span><span class="sxs-lookup"><span data-stu-id="5e1db-155">If this number is considerably higher than your baseline site, then it's a good indication that there is something complex going on in your page that is causing performance issues.</span></span>
  
<span data-ttu-id="5e1db-156">Una vez que haya identificado que hay un problema específico de su sitio, la forma recomendada para averiguar qué causa el bajo rendimiento es eliminar todas las causas posibles, como las personalizaciones de páginas y, a continuación, volver a agregarlas al sitio de una en una.</span><span class="sxs-lookup"><span data-stu-id="5e1db-156">Once you have identified that an issue specific to your site, the recommended way to figure out what is causing poor performance is to eliminate all of the possible causes, like page customizations, and then add them back to the site one by one.</span></span> <span data-ttu-id="5e1db-157">Una vez que haya quitado las personalizaciones suficientes que la página está funcionando correctamente, puede Agregar personalizaciones específicas de una en una.</span><span class="sxs-lookup"><span data-stu-id="5e1db-157">Once you have removed enough customizations that the page is performing well, you can then add back specific customizations one by one.</span></span>
  
<span data-ttu-id="5e1db-158">Por ejemplo, si tiene una navegación muy compleja, intente cambiar la navegación para que no se muestren los subsitios y, después, revise las herramientas de desarrollo para ver si esto supone una diferencia.</span><span class="sxs-lookup"><span data-stu-id="5e1db-158">For example, if you have a very complex navigation try changing the navigation to not show sub-sites then check the developer tools to see if this makes a difference.</span></span> <span data-ttu-id="5e1db-159">O bien, si tiene una gran cantidad de contenido acumulado, pruebe a quitarlos de la página y ver si esto mejora las cosas.</span><span class="sxs-lookup"><span data-stu-id="5e1db-159">Or if you have a large amount of content roll-ups try removing them from your page and see if this improves things.</span></span> <span data-ttu-id="5e1db-160">Si elimina todas las causas posibles y las agrega de nuevo de una en una, puede identificar fácilmente qué características son el mayor problema y, a continuación, trabajar hacia una solución.</span><span class="sxs-lookup"><span data-stu-id="5e1db-160">If you eliminate all of the possible causes and add them back in one at a time, you can easily identify which features are the biggest problem and then work towards a solution.</span></span>
