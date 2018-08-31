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
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Retrasar la carga de imágenes y JavaScript en SharePoint Online

En este artículo se describe cómo puede disminuir el tiempo de carga para las páginas de SharePoint Online mediante el uso de JavaScript para retrasar la carga de imágenes y también esperando cargar JavaScript que no sean esenciales hasta después de la carga de las páginas. 
  
Las imágenes pueden afectar negativamente las velocidades de carga de página en SharePoint Online. De forma predeterminada, la mayoría de exploradores de Internet modernos buscan previamente las imágenes al cargar una página HTML. Esto puede provocar que la página esté innecesariamente lenta si las imágenes no están visibles en la pantalla hasta que el usuario se desplaza hacia abajo. Las imágenes pueden bloquear el explorador y este no podrá cargar la parte visible de la página. Para solucionar este problema, puede usar JavaScript para omitir cargar las imágenes en primer lugar. Además, cargar JavaScript no esencial puede ralentizar demasiado los tiempos de carga de las páginas de SharePoint. En este tema se describen algunos métodos que puede utilizar para mejorar los tiempos de carga de página con JavaScript en SharePoint Online. 
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Mejorar los tiempos de carga de página al retrasar la carga de imágenes en páginas de SharePoint Online con JavaScript

Puede usar JavaScript para evitar que un explorador web de la búsqueda anticipada de las imágenes. Esto acelera la representación global del documento. Para hacer esto quita el valor del atributo src de la \<img\> etiquetar y reemplácelo por la ruta de acceso a un archivo en un atributo de datos tales como: datos-src. Por ejemplo:
  
```
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Mediante el uso de este método, el explorador no descargue las imágenes inmediatamente. Si la imagen se encuentra en el área de visualización, JavaScript indica al explorador para recuperar la dirección URL de los atributos de datos e Insertar como el valor para el atributo src. La imagen se carga sólo como el usuario se desplaza y lo que respecta a la vista.
  
Para hacer que todo esto ocurra, necesitará usar JavaScript.
  
En un archivo de texto, defina la función **isElementInViewport()** para comprobar si un elemento está en la parte del explorador que es visible para el usuario. 
  
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

A continuación, utilice **isElementInViewport()** en la función **loadItemsInView()**. La función **loadItemsInView()** cargará todas las imágenes que tienen un valor para el atributo data-src si se encuentran en la parte del explorador que es visible para el usuario. Agregue la siguiente función en el archivo de texto: 
  
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

Por último, llame a **loadItemsInView()** desde **window.onscroll()** tal como se muestra en el ejemplo siguiente. Esto garantiza que las imágenes que se encuentran en la ventanilla se cargan cuando el usuario necesita, pero no antes. Agregue lo siguiente en el archivo de texto: 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

Para SharePoint Online, deberá asociar la siguiente función al evento de desplazamiento en el área de s4 # \<div\> etiqueta. Esto es debido a que los eventos de ventana se reemplazan a fin de garantizar que la cinta de opciones permanece conectado a la parte superior de la página.
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Guarde el archivo de texto como archivo de JavaScript con la extensión .js. Por ejemplo: delayLoadImages.js.
  
Una vez que haya terminado de escribir delayLoadImages.js, puede agregar el contenido del archivo a una página maestra en SharePoint Online. Para ello, mediante la adición de un vínculo de la secuencia de comandos al encabezado de la página maestra. Una vez que se encuentra en una página maestra, el código JavaScript se aplicarán a todas las páginas en su sitio de SharePoint Online que usan ese diseño de página maestra. Como alternativa, si se va a usar sólo esto en una página de su sitio, use el elemento Web editor de secuencias de comandos para incrustar el código JavaScript en la página. Consulte estos temas para obtener más información:
  
- [Cómo: aplicar una página maestra a un sitio de SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [Cómo: crear un diseño de página en SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **Ejemplo: Hacer referencia al archivo delayLoadImages.js de JavaScript desde una página maestra en SharePoint Online**
  
Para que funcione, también deberá hacer referencia a jQuery en la página maestra. En el ejemplo siguiente, puede ver en la carga inicial de páginas que hay solo una imagen cargada pero hay varias más en la página.
  
![Captura de pantalla que muestra una imagen cargada en la página](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
La captura de pantalla siguiente muestra el resto de las imágenes que se descargan cuando se desplazan a la vista activa.
  
![Captura de pantalla que muestra varias imágenes cargadas en la página](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Retrasar la carga de la imagen con JavaScript puede ser una técnica eficaz para aumentar el rendimiento; Sin embargo, si se aplica la técnica en un sitio web público, los motores de búsqueda no pueden rastrear las imágenes tal como rastrearían una imagen formada de manera habitual. Esto puede afectar a las clasificaciones de motores de búsqueda porque los metadatos en la imagen en sí no están realmente allí hasta que se cargue la página. Los rastreadores de los motores de búsqueda solo leen el código HTML y, por lo tanto, no verán las imágenes como contenido de la página. Las imágenes son uno de los factores que se usan para clasificar páginas en los resultados de búsqueda. Una forma de solucionar este problema es usar texto de introducción para las imágenes.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>Ejemplo de código de GitHub: Inserción de JavaScript para mejorar el rendimiento

No se pierda el artículo y ejemplo de código en [JavaScript inyección](https://go.microsoft.com/fwlink/p/?LinkId=524759) proporcionado en depósito. 
  
## <a name="see-also"></a>Vea también

[Exploradores compatibles de Office 2013 y Office 365 ProPlus](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Cómo: aplicar una página maestra a un sitio de SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[Cómo: crear un diseño de página en SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)

