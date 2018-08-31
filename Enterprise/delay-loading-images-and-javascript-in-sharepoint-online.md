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
description: En este artículo se describe cómo puede disminuir el tiempo de carga para las páginas de SharePoint Online mediante el uso de JavaScript para retrasar la carga de imágenes y también esperando cargar JavaScript que no sean esenciales hasta después de la carga de las páginas.
ms.openlocfilehash: b8b052d85c99e51dff4b0fc747b3b52c17de8d8b
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542937"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a><span data-ttu-id="c883c-103">Retrasar la carga de imágenes y JavaScript en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="c883c-103">Delay loading images and JavaScript in SharePoint Online</span></span>

<span data-ttu-id="c883c-104">En este artículo se describe cómo puede disminuir el tiempo de carga para las páginas de SharePoint Online mediante el uso de JavaScript para retrasar la carga de imágenes y también esperando cargar JavaScript que no sean esenciales hasta después de la carga de las páginas.</span><span class="sxs-lookup"><span data-stu-id="c883c-104">This article describes how you can decrease the load time for SharePoint Online pages by using JavaScript to delay loading images and also by waiting to load non-essential JavaScript until after the page loads.</span></span> 
  
<span data-ttu-id="c883c-p101">Las imágenes pueden afectar negativamente las velocidades de carga de página en SharePoint Online. De forma predeterminada, la mayoría de exploradores de Internet modernos buscan previamente las imágenes al cargar una página HTML. Esto puede provocar que la página esté innecesariamente lenta si las imágenes no están visibles en la pantalla hasta que el usuario se desplaza hacia abajo. Las imágenes pueden bloquear el explorador y este no podrá cargar la parte visible de la página. Para solucionar este problema, puede usar JavaScript para omitir cargar las imágenes en primer lugar. Además, cargar JavaScript no esencial puede ralentizar demasiado los tiempos de carga de las páginas de SharePoint. En este tema se describen algunos métodos que puede utilizar para mejorar los tiempos de carga de página con JavaScript en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="c883c-p101">Images can negatively affect page load speeds on SharePoint Online. By default, most modern Internet browsers pre-fetch images when loading an HTML page. This can cause the page to be unnecessarily slow to load if the images are not visible on the screen until the user scrolls down. The images can block the browser from loading the visible part of the page. To work around this problem, you can use JavaScript to skip loading the images first. Also, loading non-essential JavaScript can slow down load times on your SharePoint pages too. This topic describes some methods you can use to improve page load times with JavaScript in SharePoint Online.</span></span> 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a><span data-ttu-id="c883c-112">Mejorar los tiempos de carga de página al retrasar la carga de imágenes en páginas de SharePoint Online con JavaScript</span><span class="sxs-lookup"><span data-stu-id="c883c-112">Improve page load times by delaying image loading in SharePoint Online pages by using JavaScript</span></span>

<span data-ttu-id="c883c-p102">Puede usar JavaScript para evitar que un explorador web de la búsqueda anticipada de las imágenes. Esto acelera la representación global del documento. Para hacer esto quita el valor del atributo src de la \<img\> etiquetar y reemplácelo por la ruta de acceso a un archivo en un atributo de datos tales como: datos-src. Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="c883c-p102">You can use JavaScript to prevent a web browser from pre-fetching images. This speeds up overall document rendering. To do this you remove the value of the src attribute from the \<img\> tag and replace it with the path to a file in a data attribute such as: data-src. For example:</span></span>
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

<span data-ttu-id="c883c-p103">Mediante el uso de este método, el explorador no descargue las imágenes inmediatamente. Si la imagen se encuentra en el área de visualización, JavaScript indica al explorador para recuperar la dirección URL de los atributos de datos e Insertar como el valor para el atributo src. La imagen se carga sólo como el usuario se desplaza y lo que respecta a la vista.</span><span class="sxs-lookup"><span data-stu-id="c883c-p103">By using this method, the browser doesn't download the images immediately. If the image is already in the viewport, JavaScript tells the browser to retrieve the URL from the data attribute and insert it as the value for the src attribute. The image only loads as the user scrolls and it comes into view.</span></span>
  
<span data-ttu-id="c883c-119">Para hacer que todo esto ocurra, necesitará usar JavaScript.</span><span class="sxs-lookup"><span data-stu-id="c883c-119">To make all of this happen, you'll need to use JavaScript.</span></span>
  
<span data-ttu-id="c883c-120">En un archivo de texto, defina la función **isElementInViewport()** para comprobar si un elemento está en la parte del explorador que es visible para el usuario.</span><span class="sxs-lookup"><span data-stu-id="c883c-120">In a text file, define the **isElementInViewport()** function to check whether or not an element is in the part of the browser that is visible to the user.</span></span> 
  
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

<span data-ttu-id="c883c-p104">A continuación, utilice **isElementInViewport()** en la función **loadItemsInView()**. La función **loadItemsInView()** cargará todas las imágenes que tienen un valor para el atributo data-src si se encuentran en la parte del explorador que es visible para el usuario. Agregue la siguiente función en el archivo de texto:</span><span class="sxs-lookup"><span data-stu-id="c883c-p104">Next, use **isElementInViewport()** in the **loadItemsInView()** function. The **loadItemsInView()** function will load all images that have a value for the data-src attribute if they are in the part of the browser that is visible to the user. Add the following function to the text file:</span></span> 
  
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

<span data-ttu-id="c883c-p105">Por último, llame a **loadItemsInView()** desde **window.onscroll()** tal como se muestra en el ejemplo siguiente. Esto garantiza que las imágenes que se encuentran en la ventanilla se cargan cuando el usuario necesita, pero no antes. Agregue lo siguiente en el archivo de texto:</span><span class="sxs-lookup"><span data-stu-id="c883c-p105">Finally, call **loadItemsInView()** from within **window.onscroll()** as shown in the following example. This ensures that any images that are in the viewport are loaded as the user needs them, but not before. Add the following to the text file:</span></span> 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

<span data-ttu-id="c883c-p106">Para SharePoint Online, deberá asociar la siguiente función al evento de desplazamiento en el área de s4 # \<div\> etiqueta. Esto es debido a que los eventos de ventana se reemplazan a fin de garantizar que la cinta de opciones permanece conectado a la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="c883c-p106">For SharePoint Online, you need to attach the following function to the scroll event on the #s4-workspace \<div\> tag. This is because the window events are overridden in order to ensure the ribbon remains attached to the top of the page.</span></span>
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

<span data-ttu-id="c883c-129">Guarde el archivo de texto como archivo de JavaScript con la extensión .js. Por ejemplo: delayLoadImages.js.</span><span class="sxs-lookup"><span data-stu-id="c883c-129">Save the text file as a JavaScript file with the extension .js, for example delayLoadImages.js.</span></span>
  
<span data-ttu-id="c883c-p107">Una vez que haya terminado de escribir delayLoadImages.js, puede agregar el contenido del archivo a una página maestra en SharePoint Online. Para ello, mediante la adición de un vínculo de la secuencia de comandos al encabezado de la página maestra. Una vez que se encuentra en una página maestra, el código JavaScript se aplicarán a todas las páginas en su sitio de SharePoint Online que usan ese diseño de página maestra. Como alternativa, si se va a usar sólo esto en una página de su sitio, use el elemento Web editor de secuencias de comandos para incrustar el código JavaScript en la página. Consulte estos temas para obtener más información:</span><span class="sxs-lookup"><span data-stu-id="c883c-p107">Once you've finished writing delayLoadImages.js, you can add the contents of the file to a master page in SharePoint Online. You do this by adding a script link to the header in the master page. Once it's in a master page, the JavaScript will be applied to all pages in your SharePoint Online site that use that master page layout. Alternatively, if you intend to only use this on one page of your site, use the script editor Web Part to embed the JavaScript into the page. See these topics for more information:</span></span>
  
- [<span data-ttu-id="c883c-135">Cómo: aplicar una página maestra a un sitio de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c883c-135">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [<span data-ttu-id="c883c-136">Cómo: crear un diseño de página en SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c883c-136">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 <span data-ttu-id="c883c-137">**Ejemplo: Hacer referencia al archivo delayLoadImages.js de JavaScript desde una página maestra en SharePoint Online**</span><span class="sxs-lookup"><span data-stu-id="c883c-137">**Example: Referencing the JavaScript delayLoadImages.js file from a master page in SharePoint Online**</span></span>
  
<span data-ttu-id="c883c-p108">Para que funcione, también deberá hacer referencia a jQuery en la página maestra. En el ejemplo siguiente, puede ver en la carga inicial de páginas que hay solo una imagen cargada pero hay varias más en la página.</span><span class="sxs-lookup"><span data-stu-id="c883c-p108">In order for this to work, you also need to reference jQuery in the master page. In the following example, you can see in the initial page load that there is only one image loaded but there are several more on the page.</span></span>
  
![Captura de pantalla que muestra una imagen cargada en la página](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
<span data-ttu-id="c883c-141">La captura de pantalla siguiente muestra el resto de las imágenes que se descargan cuando se desplazan a la vista activa.</span><span class="sxs-lookup"><span data-stu-id="c883c-141">The following screen shot shows the rest of the images that are downloaded after they scroll into view.</span></span>
  
![Captura de pantalla que muestra varias imágenes cargadas en la página](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
<span data-ttu-id="c883c-p109">Retrasar la carga de la imagen con JavaScript puede ser una técnica eficaz para aumentar el rendimiento; Sin embargo, si se aplica la técnica en un sitio web público, los motores de búsqueda no pueden rastrear las imágenes tal como rastrearían una imagen formada de manera habitual. Esto puede afectar a las clasificaciones de motores de búsqueda porque los metadatos en la imagen en sí no están realmente allí hasta que se cargue la página. Los rastreadores de los motores de búsqueda solo leen el código HTML y, por lo tanto, no verán las imágenes como contenido de la página. Las imágenes son uno de los factores que se usan para clasificar páginas en los resultados de búsqueda. Una forma de solucionar este problema es usar texto de introducción para las imágenes.</span><span class="sxs-lookup"><span data-stu-id="c883c-p109">Delaying image loading by using JavaScript can be an effective technique in increasing performance; however, if the technique is applied on a public website then search engines are not able to crawl the images in the same way they would crawl a regularly formed image. This can affect rankings on search engines because metadata on the image itself is not really there until the page loads. Search engine crawlers only read the HTML and therefore will not see the images as content on the page. Images are one of the factors used to rank pages in search results. One way to work around this is to use introductory text for your images.</span></span>
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a><span data-ttu-id="c883c-148">Ejemplo de código de GitHub: Inserción de JavaScript para mejorar el rendimiento</span><span class="sxs-lookup"><span data-stu-id="c883c-148">GitHub code sample: Injecting JavaScript to improve performance</span></span>

<span data-ttu-id="c883c-149">No se pierda el artículo y ejemplo de código en [JavaScript inyección](https://go.microsoft.com/fwlink/p/?LinkId=524759) proporcionado en depósito.</span><span class="sxs-lookup"><span data-stu-id="c883c-149">Don't miss the article and code sample on [JavaScript injection](https://go.microsoft.com/fwlink/p/?LinkId=524759) provided on GitHub.</span></span> 
  
## <a name="see-also"></a><span data-ttu-id="c883c-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="c883c-150">See also</span></span>

[<span data-ttu-id="c883c-151">Exploradores compatibles de Office 2013 y Office 365 ProPlus</span><span class="sxs-lookup"><span data-stu-id="c883c-151">Supported browsers in Office 2013 and Office 365 ProPlus</span></span>](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[<span data-ttu-id="c883c-152">Cómo: aplicar una página maestra a un sitio de SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c883c-152">How to: Apply a master page to a site in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[<span data-ttu-id="c883c-153">Cómo: crear un diseño de página en SharePoint 2013</span><span class="sxs-lookup"><span data-stu-id="c883c-153">How to: Create a page layout in SharePoint 2013</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=525628)

