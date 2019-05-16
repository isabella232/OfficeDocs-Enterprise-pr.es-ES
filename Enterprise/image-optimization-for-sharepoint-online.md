---
title: Optimización de imágenes para SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Obtenga información sobre cómo usar representaciones y sprites para mejorar el rendimiento de la imagen en los sitios web de SharePoint Online.
ms.openlocfilehash: b1210146aa3efb042937abeece4df0e62a579b94
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34067376"
---
# <a name="image-optimization-for-sharepoint-online"></a>Optimización de imágenes para SharePoint Online

La velocidad de carga de una página web depende del tamaño combinado de todos los componentes necesarios para representar la página, incluidas las imágenes, HTML, JavaScript y CSS. Las imágenes son una buena forma de hacer que el sitio sea más atractivo, pero su tamaño puede afectar al rendimiento. Mediante la optimización de las imágenes con compresión y cambio de tamaño, y el uso de sprites, puede desplazar los efectos de imágenes muy grandes. Con las representaciones de imágenes de SharePoint, puede cargar una sola imagen grande y mostrar secciones de la imagen, lo que permite volver a usarla en lugar de volver a cargarla.
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a>Usar sprites para acelerar la carga de imágenes en SharePoint Online

|||
|:-----|:-----|
| Un sprite de imagen contiene muchas imágenes más pequeñas. Mediante el uso de CSS, puede seleccionar una parte de la imagen compuesta para mostrar en una parte determinada de la página con posición absoluta. Básicamente, se mueve una sola imagen por la página en lugar de cargar varias imágenes y se hace que una pequeña parte de la imagen esté visible a través de una ventana pequeña en la que la parte necesaria de la imagen de Sprite se muestra al usuario final. SharePoint Online usa sprites para mostrar sus distintos iconos en el Sprite spcommon. png.  <br/>  Qué se trata aquí:  <br/>  Compresión de imágenes  <br/>  Optimización de imágenes  <br/>  Representaciones de imágenes de SharePoint  <br/> |![Captura de pantalla de spcommon](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
Esto puede aumentar el rendimiento porque solo se descarga una imagen en lugar de varias, y luego se almacena en caché y se reutiliza dicha imagen. Incluso si la imagen no permanece en caché, al tener una sola imagen en lugar de varias imágenes, este método reduce el número total de solicitudes HTTP al servidor, lo que reducirá los tiempos de carga de la página. Esta es realmente una forma de agrupación de imágenes. Esta es una técnica muy útil si las imágenes no cambian muy a menudo, por ejemplo, iconos, tal como se muestra en el ejemplo de SharePoint proporcionado anteriormente. Puede usar [Web Essentials](http://vswebessentials.com/), un proyecto de terceros, basado en la comunidad de código abierto, para conseguir esto fácilmente en Microsoft Visual Studio. Para obtener más información, vea [minificación y la agrupación en SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a>Uso de la compresión y optimización de imágenes para acelerar la carga de páginas en SharePoint

La compresión y la optimización de imágenes consiste en reducir el tamaño de archivo de las imágenes que se usan en el sitio. A menudo, la mejor técnica para reducir el tamaño de una imagen es cambiar el tamaño de la imagen a las dimensiones máximas que se van a ver en el sitio. No tiene sentido tener una imagen más grande que nunca se verá. Asegurarse de que las imágenes son de las dimensiones correctas con un editor de imágenes es una forma rápida y sencilla de reducir el tamaño de la página.
  
Una vez que las imágenes tienen el tamaño correcto, el siguiente paso es optimizar la compresión de estas imágenes. Hay varias herramientas que se pueden usar para la compresión y optimización, incluidas las herramientas de la galería de fotografías y de otros fabricantes. La clave para la compresión es reducir el tamaño de archivo tanto como sea posible sin perder calidad de calidad para los usuarios finales. Asegúrese de probar los archivos comprimidos en una pantalla de alta definición para asegurarse de que siguen siendo correctos.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Acelerar las descargas de páginas con representaciones de imágenes de SharePoint

Las representaciones de imágenes son una característica de SharePoint Online que permite dar servicio a diferentes versiones de imágenes en función de las dimensiones de imagen predefinidas. Esto es especialmente importante cuando hay contenido de imagen generado por el usuario o las dimensiones de la imagen, como el ancho y el alto, se corrigen mediante la CSS en el sitio. Incluso si una imagen se ha corregido mediante CSS, la imagen de resolución completa sigue cargada. En este caso, el tamaño de archivo se puede reducir mediante representaciones de imágenes.
  
> [!NOTE]
> Las representaciones solo están disponibles para SharePoint cuando la publicación está habilitada. Puede habilitar la publicación en configuración \> del sitio \> de administración de \> características de sitio de SharePoint Server Publishing. De lo contrario, la opción no aparecerá. 
  
El cambio de tamaño de la representación de imágenes funciona tomando la dimensión más pequeña que defina, ya sea de ancho o de alto y, a continuación, cambia el tamaño de la imagen para que el resto de la dimensión se ajuste automáticamente según la relación de aspecto bloqueada. De forma predeterminada, se recortará la imagen del centro con las dimensiones restantes. Por ejemplo, si define una representación de 100px de ancho y 50px de alto y la imagen original es 1000px de ancho y 800px de alta, se cambiará de tamaño para que la dimensión 800px ahora sea 50px y la dimensión 1000px (ahora 62,5 px) se recorta desde el centro de la imagen.
  
Los pasos son relativamente sencillos, pero para que las imágenes usen las representaciones, las representaciones deben estar en el sitio de SharePoint antes de agregar las imágenes. Además, también debe tener activadas las características de infraestructura de publicación de SharePoint Server (en el nivel de colección de sitios) y de publicación de SharePoint Server (nivel de sitio).
  
 **Agregar una representación de imágenes para acelerar la carga de páginas**
  
1. Compruebe que la cuenta de usuario que está realizando este procedimiento tiene, como mínimo, permisos de diseño en el sitio de nivel superior de la colección de sitios y que el sitio se está publicando en una página web.
    
2. En un explorador Web, vaya al sitio de nivel superior de la colección de sitios de publicación.
    
3. Elija el icono **Configuración**. 
    
4. En la página **configuración del sitio** , en la sección **aspecto** , verá las representaciones de imágenes integradas. 
    
    Puede usar las representaciones desde el cuadro o elegir **representaciones de imágenes** para crear una nueva. 
    
    ![Captura de pantalla de representación de imágenes](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. En la página **Representaciones de imágenes**, elija **Agregar nuevo elemento**.
    
    ![Captura de pantalla de Agregar nuevo elemento](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. En la página **Nueva representación de imagen**, en el cuadro **Nombre**, escriba un nombre para la representación. 
    
7. En los cuadros de texto **Ancho** y **Alto**, escriba el ancho y alto, en píxeles, de la representación y luego elija **Guardar**.
    
    ![Captura de pantalla del nombre de la representación de imagen](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a>Recorte personalizado con representaciones de imágenes en SharePoint

De forma predeterminada, se genera una representación de imágenes desde el centro de la imagen. Puede ajustar la representación de imagen para imágenes individuales al recortar la parte de la imagen que desea usar. Puede recortar las imágenes de manera individual, por representación. Recortar las imágenes acelera la carga de páginas mediante la caché BLOB de SharePoint para crear una versión de la imagen para cada representación. De este modo, se reduce la carga del servidor, ya que sólo se cambia el tamaño de la imagen una vez y, a continuación, está lista para servir a los usuarios finales varias veces. Para obtener más información sobre Cómo recortar una representación de imágenes, vea recortar [una representación de imágenes](https://go.microsoft.com/fwlink/p/?LinkId=525626).
  

