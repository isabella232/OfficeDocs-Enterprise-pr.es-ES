---
title: Retrasar la carga de imágenes y JavaScript en SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 12/29/2016
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: 74d327e5-755f-4135-b9a5-7b79578c1bf9
description: En este artículo se describe cómo reducir el tiempo de carga de las páginas de SharePoint Online con JavaScript para retrasar la carga de imágenes y también al esperar a cargar JavaScript no esencial hasta que se cargue la página.
ms.openlocfilehash: 9069fb395465cd9d087c018cc2ae782759ddcb0d
ms.sourcegitcommit: 6b4c3a11ef7000480463d43a7a4bc2ced063efce
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "35616793"
---
# <a name="delay-loading-images-and-javascript-in-sharepoint-online"></a>Retrasar la carga de imágenes y JavaScript en SharePoint Online

En este artículo se describe cómo reducir el tiempo de carga de las páginas de SharePoint Online con JavaScript para retrasar la carga de imágenes y también al esperar a cargar JavaScript no esencial hasta que se cargue la página.
  
Las imágenes pueden afectar negativamente a la velocidad de carga de página en SharePoint Online. De forma predeterminada, la mayoría de los exploradores de Internet modernos capturan imágenes antes de cargar una página HTML. Esto puede hacer que la página sea innecesariamente lenta para cargarse si las imágenes no se ven en la pantalla hasta que el usuario se desplaza hacia abajo. Las imágenes pueden impedir que el explorador cargue la parte visible de la página. Para solucionar este problema, puede usar JavaScript para omitir primero la carga de las imágenes. Además, la carga de JavaScript que no es esencial puede ralentizar la carga de los tiempos de las páginas de SharePoint. En este tema se describen algunos métodos que puede usar para mejorar los tiempos de carga de página con JavaScript en SharePoint Online.
  
## <a name="improve-page-load-times-by-delaying-image-loading-in-sharepoint-online-pages-by-using-javascript"></a>Mejorar los tiempos de carga de página retrasando la carga de imágenes en las páginas de SharePoint Online con JavaScript

Puede usar JavaScript para evitar que un explorador Web Busque imágenes previamente. Esto acelera la representación general de los documentos. Para ello, quite el valor del atributo src de la \<etiqueta IMG\> y reemplácelo por la ruta de acceso a un archivo en un atributo de datos como: Data-src. Por ejemplo:
  
```txt
<img src="" data-src="/sites/NavigationBySearch/_catalogs/masterpage/media/microsoft-white-8.jpg" />
```

Mediante este método, el explorador no descarga las imágenes de forma inmediata. Si la imagen ya está en la ventanilla, JavaScript le indica al explorador que recupere la dirección URL del atributo Data e insértela como el valor para el atributo src. La imagen solo se carga cuando el usuario se desplaza y se muestra.
  
Para que todo esto suceda, deberá usar JavaScript.
  
En un archivo de texto, defina la función **isElementInViewport ()** para comprobar si un elemento se encuentra o no en la parte del explorador que es visible para el usuario. 
  
```txt
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

A continuación, use **isElementInViewport ()** en la función **loadItemsInView ()** . La función **loadItemsInView ()** cargará todas las imágenes que tienen un valor para el atributo Data-src si se encuentran en la parte del explorador que es visible para el usuario. Agregue la siguiente función al archivo de texto: 
  
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

Por último, llame a **loadItemsInView ()** desde dentro de **window. OnScroll ()** , como se muestra en el ejemplo siguiente. Esto garantiza que las imágenes que están en la ventanilla se cargan a medida que las necesita el usuario, pero no antes. Agregue lo siguiente al archivo de texto: 
  
```
//Example of calling loadItemsInView() from within window.onscroll()
$(window).on("scroll", function () {
    loadItemsInView();
});

```

Para SharePoint Online, debe adjuntar la siguiente función al evento scroll en la etiqueta div \<\> #s4-Workspace. Esto se debe a que los eventos de ventana se invalidan para garantizar que la cinta permanece adjunta a la parte superior de la página.
  
```
//Keep the ribbon at the top of the page
$('#s4-workspace').on("scroll", function () {
    loadItemsInView();
});
```

Guarde el archivo de texto como archivo JavaScript con la extensión. js, por ejemplo, delayLoadImages. js.
  
Una vez que haya terminado de escribir delayLoadImages. js, puede Agregar el contenido del archivo a una página maestra en SharePoint Online. Para ello, agregue un vínculo de script al encabezado en la página maestra. Una vez que está en una página maestra, el JavaScript se aplicará a todas las páginas de su sitio de SharePoint Online que usen ese diseño de página maestra. Como alternativa, si solo va a usar esto en una página del sitio, use el elemento Web script editor para incrustar el código JavaScript en la página. Vea estos temas para obtener más información:
  
- [Aplicar una página maestra a un sitio de SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
    
- [Cómo crear un diseño de página en SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)
    
 **Ejemplo: hacer referencia al archivo delayLoadImages. js de JavaScript desde una página maestra en SharePoint Online**
  
Para que esto funcione, también tiene que hacer referencia a jQuery en la página maestra. En el siguiente ejemplo, puede ver en la carga de página inicial que solo hay una imagen cargada, pero hay varias más en la página.
  
![Captura de pantalla que muestra una imagen cargada en la página](media/3d177ddb-67e5-43a7-b327-c9f9566ca937.png)
  
En la siguiente captura de pantalla se muestra el resto de las imágenes que se descargan cuando se desplazan a la vista.
  
![Captura de pantalla que muestra varias imágenes cargadas en la página](media/95eb2b14-f6a1-4eac-a5cb-96097e49514c.png)
  
Retrasar la carga de imágenes mediante JavaScript puede ser una técnica eficaz para aumentar el rendimiento; sin embargo, si la técnica se aplica a un sitio web público, los motores de búsqueda no podrán rastrear las imágenes de la misma forma que lo harían con una imagen de formato frecuente. Esto puede afectar a las clasificaciones en los motores de búsqueda porque los metadatos de la imagen en sí no están realmente ahí hasta que se carga la página. Los rastreadores del motor de búsqueda solo leen el HTML y, por lo tanto, no verán las imágenes como contenido en la página. Las imágenes son uno de los factores que se usan para clasificar las páginas en los resultados de búsqueda. Una manera de solucionar esto es usar texto de introducción para sus imágenes.
  
## <a name="github-code-sample-injecting-javascript-to-improve-performance"></a>Ejemplo de código de GitHub: inyectar JavaScript para mejorar el rendimiento

No pierdas el artículo y el ejemplo de código de la [inyección de JavaScript](https://go.microsoft.com/fwlink/p/?LinkId=524759) que se proporciona en github. 
  
## <a name="see-also"></a>Vea también

[Exploradores compatibles en Office 2013 y Office 365 ProPlus](https://support.office.com/article/57342811-0dc4-4316-b773-20082ced8a82)
  
[Aplicar una página maestra a un sitio de SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525627)
  
[Cómo crear un diseño de página en SharePoint 2013](https://go.microsoft.com/fwlink/p/?LinkId=525628)

