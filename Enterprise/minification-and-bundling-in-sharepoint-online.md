---
title: Minificación y agrupación en SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 3/1/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: En este artículo se describe cómo utilizar la reducción y agrupación técnicas con Web Essentials para reducir el número de solicitudes HTTP y para reducir el tiempo que se tarda en cargar páginas en SharePoint Online.
ms.openlocfilehash: edc959e881b0f22b72fba64969e5984f30bce696
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542687"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a><span data-ttu-id="bf445-103">Minificación y agrupación en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="bf445-103">Minification and bundling in SharePoint Online</span></span>

<span data-ttu-id="bf445-104">En este artículo se describe cómo utilizar la reducción y agrupación técnicas con Web Essentials para reducir el número de solicitudes HTTP y para reducir el tiempo que se tarda en cargar páginas en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="bf445-104">This article describes how to use minification and bundling techniques with Web Essentials to reduce the number of HTTP requests and to reduce the time it takes to load pages in SharePoint Online.</span></span>
  
<span data-ttu-id="bf445-p101">Al personalizar su sitio web puede terminar agregando un gran número de archivos adicionales en el servidor para admitir la personalización. Agregar más imágenes, CSS y JavaScript aumenta el número de solicitudes HTTP al servidor, lo que a su vez aumenta el tiempo empleado en mostrar una página web. Si tiene varios archivos del mismo tipo, puede agrupar estos archivos para acelerar la descarga de los archivos.</span><span class="sxs-lookup"><span data-stu-id="bf445-p101">When you customize your website you can end up adding a large number of extra files to the server to support the customization. Adding extra JavaScript, CSS, and images increases the number of HTTP requests to the server which in turn increases the time it takes to display a web page. If you have multiple files of the same type, you can bundle these files to make downloading these files faster.</span></span>
  
<span data-ttu-id="bf445-108">Para los archivos CSS y JavaScript, también puede utilizar un enfoque llamado reducción, donde se reduce el tamaño total de archivos mediante la eliminación de espacio en blanco y otros caracteres que no son necesarios.</span><span class="sxs-lookup"><span data-stu-id="bf445-108">For JavaScript and CSS files, you can also use an approach called minification, where you reduce the total size of files by removing whitespace and other characters that aren't necessary.</span></span>
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a><span data-ttu-id="bf445-109">Minificación y agrupación de archivos JavaScript y CSS con Web Essentials</span><span class="sxs-lookup"><span data-stu-id="bf445-109">Minification and bundling JavaScript and CSS files with Web Essentials</span></span>

<span data-ttu-id="bf445-110">Puede usar software de terceros como Web Essentials para agrupar los archivos CSS y JavaScript.</span><span class="sxs-lookup"><span data-stu-id="bf445-110">You can use third-party software such as Web Essentials to bundle CSS and JavaScript files.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="bf445-p102">Web Essentials es un proyecto de otro fabricante, Abrir origen, en función de la Comunidad. El software es una extensión de Visual Studio 2012 y Visual Studio 2013 y no es compatible con Microsoft. Para descargar Web Essentials, visite el sitio Web en [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span><span class="sxs-lookup"><span data-stu-id="bf445-p102">Web Essentials is a third-party, open-source, community-based project. The software is an extension to Visual Studio 2012 and Visual Studio 2013 and is not supported by Microsoft. To download Web Essentials, visit the website at [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629).</span></span> 
  
<span data-ttu-id="bf445-114">Web Essentials ofrece dos formas de agrupación:</span><span class="sxs-lookup"><span data-stu-id="bf445-114">Web Essentials offers two forms of bundling:</span></span>
  
- <span data-ttu-id="bf445-115">.bundle: para archivos CSS y JavaScript</span><span class="sxs-lookup"><span data-stu-id="bf445-115">.bundle: for CSS and JavaScript files</span></span>
    
- <span data-ttu-id="bf445-116">.sprite: para imágenes (disponible solo en Visual Studio 2013)</span><span class="sxs-lookup"><span data-stu-id="bf445-116">.sprite: for images (only available in Visual Studio 2013)</span></span>
    
<span data-ttu-id="bf445-117">Puede usar Web Essentials si tiene una característica existente con algunos elementos de personalización de marca a los que se hace referencia dentro de una página maestra personalizada, como:</span><span class="sxs-lookup"><span data-stu-id="bf445-117">You can use Web Essentials if you have an existing feature with some branding elements that are referenced inside a custom master page, such as:</span></span>
  
![Captura de pantalla de un elemento que identifica la marca en la página maestra personalizada](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 <span data-ttu-id="bf445-119">**Para crear un paquete de TE000127218 y CSS en Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="bf445-119">**To create a TE000127218 and CSS bundle in Web Essentials**</span></span>
  
1. <span data-ttu-id="bf445-120">En Visual Studio, en el Explorador de soluciones, seleccione los archivos que desea incluir en la agrupación.</span><span class="sxs-lookup"><span data-stu-id="bf445-120">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="bf445-p103">Haga clic en los archivos seleccionados y, a continuación, seleccione **Web Essentials** \> **archivo de paquete de creación de JavaScript** en el menú contextual. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="bf445-p103">Right-click the selected files and then select **Web Essentials** \> **Create JavaScript bundle file** from the context menu. For example:</span></span> 
    
    ![Captura de pantalla que muestra las opciones de menú de Web Essentials](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a><span data-ttu-id="bf445-124">Ver los resultados de agrupar archivos JavaScript y CSS</span><span class="sxs-lookup"><span data-stu-id="bf445-124">Viewing the results of bundling JavaScript and CSS files</span></span>

<span data-ttu-id="bf445-125">Cuando se crea una agrupación de JavaScript y CSS, Web Essentials crea un archivo XML llamado archivo de receta que identifica a los archivos JavaScript y CSS y también a información de configuración:</span><span class="sxs-lookup"><span data-stu-id="bf445-125">When you create a JavaScript and CSS bundle, Web Essentials creates an XML file called a recipe file that identifies the JavaScript and CSS files as well as some other configuration information:</span></span> 
  
![Captura de pantalla del archivo receta de JavaScript y CSS](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
<span data-ttu-id="bf445-p104">Además, si la marca de minificación se establece como true en la receta de agrupación, los archivos pasan a tener menos tamaño y a estar agrupados. Esto significa que se crearon nuevas versiones minificadas de los archivos JavaScript y que usted puede hacer referencia a estas versiones en la página maestra.</span><span class="sxs-lookup"><span data-stu-id="bf445-p104">In addition, if the minify flag is set to true in the bundling recipe the files are reduced in size as well as bundled together. This means that new, minified versions of the JavaScript files were created that you can reference in your master page.</span></span>
  
![Captura de pantalla de la marca de minify establecida en verdadero](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
<span data-ttu-id="bf445-130">Cuando carga una página de su sitio web, puede usar las herramientas de desarrollo desde el explorador web, como Internet Explorer 11, para ver el número de solicitudes enviadas al servidor y cuánto tiempo tardó cada archivo en cargarse.</span><span class="sxs-lookup"><span data-stu-id="bf445-130">When you load a page from your web site, you can use the developer tools from your web browser, such as Internet Explorer 11, to see the number of requests sent to the server and how long each file took to load.</span></span>
  
<span data-ttu-id="bf445-131">La figura siguiente es el resultado de cargar los archivos JavaScript y CSS antes de la minificación.</span><span class="sxs-lookup"><span data-stu-id="bf445-131">The following figure is the result of loading the JavaScript and CSS files before minification.</span></span>
  
![Captura de pantalla que muestra los 80 artículos descargándose](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
<span data-ttu-id="bf445-133">Después de agrupar los archivos CSS y JavaScript, el número de solicitudes bajó a 74 y la descarga individual de cada archivo solo fue ligeramente más lenta que con los archivos originales:</span><span class="sxs-lookup"><span data-stu-id="bf445-133">After bundling the CSS and JavaScript files together, the number of requests dropped to 74 and each file took only slightly longer than the original files to download individually:</span></span>
  
![Captura de pantalla que muestra los 74 artículos descargándose](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
<span data-ttu-id="bf445-135">Después de la agrupación, el archivo de agrupación JavaScript se reduce significativamente de 815 KB a 365 KB:</span><span class="sxs-lookup"><span data-stu-id="bf445-135">After bundling, the JavaScript bundle file is reduced significantly from 815KB to 365KB:</span></span>
  
![Captura de pantalla que muestra el tamaño de la descarga reducido](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a><span data-ttu-id="bf445-137">Agrupar imágenes mediante la creación de un sprite de imagen</span><span class="sxs-lookup"><span data-stu-id="bf445-137">Bundling images by creating an image sprite</span></span>

<span data-ttu-id="bf445-p105">De forma similar a cómo se agrupan los archivos CSS y JavaScript, puede combinar muchos iconos pequeños y otras imágenes comunes en una hoja de sprite más grande y, a continuación, usar CSS para revelar las imágenes individuales. En lugar de descargar cada imagen individual, el explorador del usuario web de descargas de la hoja de sprite una vez y, a continuación, se almacena en caché en el equipo local. Esto mejora el rendimiento de carga de página mediante un corte hacia abajo en el número de descargas y versiones de ida y vuelta al servidor web.</span><span class="sxs-lookup"><span data-stu-id="bf445-p105">Similar to how you bundle JavaScript and CSS files, you can combine many small icons and other common images into a larger sprite sheet and then use CSS to reveal the individual images. Instead of downloading each individual image, the user's web browser downloads the sprite sheet once and then caches it on the local computer. This improves page load performance by cutting down on the number of downloads and round trips to the web server.</span></span>
  
 <span data-ttu-id="bf445-141">**Para crear un sprite de imagen en Web Essentials**</span><span class="sxs-lookup"><span data-stu-id="bf445-141">**To create an image sprite in Web Essentials**</span></span>
  
1. <span data-ttu-id="bf445-142">En Visual Studio, en el Explorador de soluciones, seleccione los archivos que desea incluir en la agrupación.</span><span class="sxs-lookup"><span data-stu-id="bf445-142">In Visual Studio, in Solution Explorer, select the files that you want to include in the bundle.</span></span>
    
2. <span data-ttu-id="bf445-p106">Haga clic en los archivos seleccionados y, a continuación, seleccione **Web Essentials** \> **crear sprite de imagen** en el menú contextual. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="bf445-p106">Right-click the selected files and then select **Web Essentials** \> **Create image sprite** from the context menu. For example:</span></span> 
    
    ![Captura de pantalla que muestra cómo crear un objeto sprite de imagen](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. <span data-ttu-id="bf445-p107">Elija una ubicación para guardar el archivo de sprite. El archivo .sprite es un archivo XML que describe la configuración y los archivos del sprite. Las siguientes figuras muestran un ejemplo de un archivo PNG de sprite y el archivo XML de .sprite correspondiente.</span><span class="sxs-lookup"><span data-stu-id="bf445-p107">Choose a location to save the sprite file. The .sprite file is an XML file that describes the settings and files in the sprite. The following figures show an example of a sprite PNG file and its corresponding .sprite XML file.</span></span>
    
    ![Captura de pantalla de un archivo de sprite](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Captura de pantalla de archivo XML de sprite](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

