---
title: Retrasar la carga de imágenes y JavaScript en SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/29/2016
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: En este artículo se describe cómo reducir el tiempo de carga de las páginas de SharePoint Online con JavaScript para retrasar la carga de imágenes y también al esperar a cargar JavaScript no esencial hasta que se cargue la página.
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33490306"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="41377-103">Retrasar la carga de imágenes y JavaScript en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="41377-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="41377-104">En este artículo se describe cómo reducir el tiempo de carga de las páginas de SharePoint Online con JavaScript para retrasar la carga de imágenes y también al esperar a cargar JavaScript no esencial hasta que se cargue la página.</span><span class="sxs-lookup"><span data-stu-id="41377-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="41377-105">Las imágenes pueden afectar negativamente a la velocidad de carga de página en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="41377-105">Images can negatively affect page load speeds on SharePoint Online.</span></span> <span data-ttu-id="41377-106">De forma predeterminada, la mayoría de los exploradores de Internet modernos capturan imágenes antes de cargar una página HTML.</span><span class="sxs-lookup"><span data-stu-id="41377-106">By default, most modern Internet browsers pre-fetch images when loading an HTML page.</span></span> <span data-ttu-id="41377-107">Esto puede hacer que la página sea innecesariamente lenta para cargarse si las imágenes no se ven en la pantalla hasta que el usuario se desplaza hacia abajo.</span><span class="sxs-lookup"><span data-stu-id="41377-107">This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down.</span></span> <span data-ttu-id="41377-108">Las imágenes pueden impedir que el explorador cargue la parte visible de la página.</span><span class="sxs-lookup"><span data-stu-id="41377-108">The images can block the browser from loading the visible part of the page.</span></span> <span data-ttu-id="41377-109">Para solucionar este problema, puede usar JavaScript para omitir primero la carga de las imágenes.</span><span class="sxs-lookup"><span data-stu-id="41377-109">To work around this problem, you can use JavaScript to skip loading the images first.</span></span> <span data-ttu-id="41377-110">Además, la carga de JavaScript que no es esencial puede ralentizar la carga de los tiempos de las páginas de SharePoint.</span><span class="sxs-lookup"><span data-stu-id="41377-110">Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too.</span></span> <span data-ttu-id="41377-111">En este tema se describen algunos métodos que puede usar para mejorar los tiempos de carga de página con JavaScript en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="41377-111">This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="41377-112">Mejorar los tiempos de carga de página retrasando la carga de imágenes en las páginas de SharePoint Online con JavaScript</span><span class="sxs-lookup"><span data-stu-id="41377-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="41377-113">Puede usar JavaScript para evitar que un explorador Web Busque imágenes previamente.</span><span class="sxs-lookup"><span data-stu-id="41377-113">You can use JavaScript to prevent a web browser from pre-fetching images.</span></span> <span data-ttu-id="41377-114">Esto acelera la representación general de los documentos.</span><span class="sxs-lookup"><span data-stu-id="41377-114">This speeds up overall document rendering.</span></span> <span data-ttu-id="41377-115">Para ello, quite el valor del atributo src de la \<etiqueta IMG\> y reemplácelo por la ruta de acceso a un archivo en un atributo de datos como: Data-src. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="41377-115">To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="41377-116">Mediante este método, el explorador no descarga las imágenes de forma inmediata.</span><span class="sxs-lookup"><span data-stu-id="41377-116">By using this method, the browser doesn't download the images immediately.</span></span> <span data-ttu-id="41377-117">Si la imagen ya está en la ventanilla, JavaScript le indica al explorador que recupere la dirección URL del atributo Data e insértela como el valor para el atributo src.</span><span class="sxs-lookup"><span data-stu-id="41377-117">If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute.</span></span> <span data-ttu-id="41377-118">La imagen solo se carga cuando el usuario se desplaza y se muestra.</span><span class="sxs-lookup"><span data-stu-id="41377-118">The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="41377-119">Para que todo esto suceda, deberá usar JavaScript.</span><span class="sxs-lookup"><span data-stu-id="41377-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="41377-120">En un archivo de texto, defina la función **isElementInViewport ()** para comprobar si un elemento se encuentra o no en la parte del explorador que es visible para el usuario.</span><span class="sxs-lookup"><span data-stu-id="41377-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
```
function isElementInViewport(el) {
  if (!el)
    return false;
  var rect = el.getBoundingClientRect();
  return (
    rect.top >= 0 &amp;&amp;
    rect.left >= 0 &amp;&amp;
    rect.bottom <= (window.innerHeight || document.documentElement.clientHeight) &amp;&amp;
    rect.right <= (window.innerWidth || document.documentElement.clientWidth) 
  );
}

```

<span data-ttu-id="41377-121">A continuación, use **isElementInViewport ()** en la función **loadItemsInView ()** .</span><span class="sxs-lookup"><span data-stu-id="41377-121">Next, use **isElementInViewport()** in the **loadItemsInView()** function.</span></span> <span data-ttu-id="41377-122">La función **loadItemsInView ()** cargará todas las imágenes que tienen un valor para el atributo Data-src si se encuentran en la parte del explorador que es visible para el usuario.</span><span class="sxs-lookup"><span data-stu-id="41377-122">The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user.</span></span> <span data-ttu-id="41377-123">Agregue la siguiente función al archivo de texto:</span><span class="sxs-lookup"><span data-stu-id="41377-123">Add the following function to the text file:</span></span> 
  
```
function loadItemsInView() {
  //Select elements by the row id.
  $("#row [data-src]").each(function () {
      var isVisible = isElementInViewport(this);
      if (isVisible) {
          if ($(this).attr("src") == undefined) {
              $(this).attr("src", $(this).data("src"));
          }
      }
  });
}
```

<span data-ttu-id="41377-124">Por último, llame a **loadItemsInView ()** desde dentro de **window. OnScroll ()** , como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="41377-124">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example.</span></span> <span data-ttu-id="41377-125">Esto garantiza que las imágenes que están en la ventanilla se cargan a medida que las necesita el usuario, pero no antes.</span><span class="sxs-lookup"><span data-stu-id="41377-125">This ensures that any images that are in the viewport are loaded as the user needs them, but not before.</span></span> <span data-ttu-id="41377-126">Agregue lo siguiente al archivo de texto:</span><span class="sxs-lookup"><span data-stu-id="41377-126">Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="41377-127">Para SharePoint Online, debe adjuntar la siguiente función al evento scroll en la etiqueta div \<\> #s4-Workspace.</span><span class="sxs-lookup"><span data-stu-id="41377-127">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag.</span></span> <span data-ttu-id="41377-128">Esto se debe a que los eventos de ventana se invalidan para garantizar que la cinta permanece adjunta a la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="41377-128">This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="41377-129">Guarde el archivo de texto como archivo JavaScript con la extensión. js, por ejemplo, delayLoadImages. js.</span><span class="sxs-lookup"><span data-stu-id="41377-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="41377-130">Una vez que haya terminado de escribir delayLoadImages. js, puede Agregar el contenido del archivo a una página maestra en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="41377-130">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online.</span></span> <span data-ttu-id="41377-131">Para ello, agregue un vínculo de script al encabezado en la página maestra.</span><span class="sxs-lookup"><span data-stu-id="41377-131">You do this by adding a script link to the header in the master page.</span></span> <span data-ttu-id="41377-132">Una vez que está en una página maestra, el JavaScript se aplicará a todas las páginas de su sitio de SharePoint Online que usen ese diseño de página maestra.</span><span class="sxs-lookup"><span data-stu-id="41377-132">Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout.</span></span> <span data-ttu-id="41377-133">Como alternativa, si solo va a usar esto en una página del sitio, use el elemento Web script editor para incrustar el código JavaScript en la página.</span><span class="sxs-lookup"><span data-stu-id="41377-133">Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page.</span></span> <span data-ttu-id="41377-134">Vea estos temas para obtener más información:</span><span class="sxs-lookup"><span data-stu-id="41377-134">See these topics for more information:</span></span>
  
- [<span data-ttu-id="41377-135">Aplicar una página maestra a un sitio de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="41377-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="41377-136">Cómo crear un diseño de página en SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="41377-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="41377-137">**Ejemplo: hacer referencia al archivo delayLoadImages. js de JavaScript desde una página maestra en SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="41377-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="41377-138">Para que esto funcione, también tiene que hacer referencia a jQuery en la página maestra.</span><span class="sxs-lookup"><span data-stu-id="41377-138">In order for this to work, you also need to reference jQuery in the master page.</span></span> <span data-ttu-id="41377-139">En el siguiente ejemplo, puede ver en la carga de página inicial que solo hay una imagen cargada, pero hay varias más en la página.</span><span class="sxs-lookup"><span data-stu-id="41377-139">In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![Captura de pantalla que muestra una imagen cargada en la página](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="41377-141">En la siguiente captura de pantalla se muestra el resto de las imágenes que se descargan cuando se desplazan a la vista.</span><span class="sxs-lookup"><span data-stu-id="41377-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![Captura de pantalla que muestra varias imágenes cargadas en la página](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="41377-143">ReTrasar la carga de imágenes mediante JavaScript puede ser una técnica eficaz para aumentar el rendimiento; sin embargo, si la técnica se aplica a un sitio web público, los motores de búsqueda no podrán rastrear las imágenes de la misma forma que lo harían con una imagen de formato frecuente.</span><span class="sxs-lookup"><span data-stu-id="41377-143">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image.</span></span> <span data-ttu-id="41377-144">Esto puede afectar a las clasificaciones en los motores de búsqueda porque los metadatos de la imagen en sí no están realmente ahí hasta que se carga la página.</span><span class="sxs-lookup"><span data-stu-id="41377-144">This can affect rankings on search engines because metadata on the image itself is not really there until the page loads.</span></span> <span data-ttu-id="41377-145">Los rastreadores del motor de búsqueda solo leen el HTML y, por lo tanto, no verán las imágenes como contenido en la página.</span><span class="sxs-lookup"><span data-stu-id="41377-145">Search engine crawlers only read the HTML and therefore will not see the images as content on the page.</span></span> <span data-ttu-id="41377-146">Las imágenes son uno de los factores que se usan para clasificar las páginas en los resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="41377-146">Images are one of the factors used to rank pages in search results.</span></span> <span data-ttu-id="41377-147">Una manera de solucionar esto es usar texto de introducción para sus imágenes.</span><span class="sxs-lookup"><span data-stu-id="41377-147">One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="41377-148">Ejemplo de código de GitHub: inyectar JavaScript para mejorar el rendimiento</span><span class="sxs-lookup"><span data-stu-id="41377-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="41377-149">No pierdas el artículo y el ejemplo de código de la [inyección de JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=524759) que se proporciona en github.</span><span class="sxs-lookup"><span data-stu-id="41377-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="41377-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="41377-150">See also</span></span>

[<span data-ttu-id="41377-151">Exploradores compatibles en Office 2013 y Office 365 proPlus</span><span class="sxs-lookup"><span data-stu-id="41377-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="41377-152">Aplicar una página maestra a un sitio de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="41377-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="41377-153">Cómo crear un diseño de página en SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="41377-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

