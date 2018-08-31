---
title: Optimización de imágenes para SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/19/2018
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: c7edb02a-fdab-4f91-9a20-cba01dad28ef
description: Obtenga información sobre cómo usar las representaciones y sprites para mejorar el rendimiento de la imagen en los sitios Web de SharePoint Online.
ms.openlocfilehash: 313046dec885a38062635254699301bcf556d698
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542722"
---
# <a name="image-optimization-for-sharepoint-online"></a>Optimización de imágenes para SharePoint Online

El tamaño combinado de todos los componentes requeridos para representar la página incluidos imágenes, HTML, JavaScript y CSS depende de la velocidad de carga de una página Web. Las imágenes son una buena forma para que su sitio más atractivo, pero su tamaño puede afectar al rendimiento. Mediante la optimización de las imágenes con compresión y el cambio de tamaño y uso de sprites, puede compensar los efectos de imágenes muy grandes. Uso de representaciones de imágenes de SharePoint, puede cargar una sola imagen grande y mostrar las secciones de la imagen para que puedan ser volver a usar en lugar de volver a cargar.
  
## <a name="using-sprites-to-speed-up-image-loading-in-sharepoint-online"></a>Utilizar sprites para acelerar la carga de imágenes en SharePoint Online

|||
|:-----|:-----|
| Un sprite imagen contiene muchas imágenes más pequeñas. Uso de CSS seleccione una parte de la imagen compuesta para mostrar en un elemento concreto de la página con una posición absoluta. Básicamente, mover una sola imagen alrededor de la página en lugar de cargar varias imágenes y hacer que una pequeña parte de la imagen visible a través de una pequeña ventana donde se muestra la parte de la imagen de sprite necesaria para el usuario final. SharePoint Online usa sprites para mostrar sus varios iconos en el spcommon.png sprite.  <br/>  ¿Qué se incluye aquí:  <br/>  Compresión de imagen  <br/>  Optimización de la imagen  <br/>  Representaciones de imágenes de SharePoint  <br/> |![Captura de pantalla de spcommon](media/cc5cdee1-8e54-4537-9a8a-8854f4ee849f.png)|
   
Esto puede aumentar el rendimiento debido a que se descargue sólo una imagen en lugar de varios y, a continuación, la memoria caché y volver a usar esa imagen. Incluso si la imagen no se mantiene en caché, por tener una única imagen en lugar de varias imágenes, este método reduce el número total de solicitudes HTTP para el servidor que va a reducir los tiempos de carga de página. Esto realmente es una forma de agrupación de imagen. Esto es una técnica muy útil si las imágenes no cambian muy a menudo, por ejemplo, los iconos, tal como se muestra en el ejemplo de SharePoint proporcionado anteriormente. Puede que el uso de [Web Essentials](http://vswebessentials.com/), un proyecto de otro fabricante, Abrir origen, en función de la Comunidad para realizar esta acción fácilmente en Microsoft Visual Studio. Para obtener más información, vea [reducción y agrupación en SharePoint Online](https://go.microsoft.com/fwlink/?LinkId=708698).
  
## <a name="using-image-compression-and-optimization-to-speed-up-page-loading-in-sharepoint"></a>Usar compresión y optimización de imágenes para acelerar la carga de páginas en SharePoint

La compresión y optimización de imágenes consiste en reducir el tamaño de archivo de las imágenes utilizadas en el sitio. A menudo, la mejor técnica para reducir el tamaño de una imagen es cambiar el tamaño de la imagen a las dimensiones máximas que se verán en el sitio. No es recomendable tener una imagen con un tamaño mayor al que se verá. Una forma rápida y fácil de reducir el tamaño de la página es usar un editor de imágenes para asegurarse de que las imágenes tengan las dimensiones correctas.
  
Una vez las imágenes están el tamaño correcto, el siguiente paso es optimizar la compresión de estas imágenes. Existen diversas herramientas disponibles que se usará para la compresión y optimización, incluida la Galería de fotografías y herramientas de otros fabricantes. Es la clave de compresión reducir el tamaño de archivo máximo posible sin perder calidad distinguir a los usuarios finales. Asegúrese de que probar los archivos comprimidos en una pantalla de alta definición para asegurarse de que aún buscará buena.
  
## <a name="speed-up-page-downloads-by-using-sharepoint-image-renditions"></a>Acelerar descargas de página mediante representaciones de imágenes de SharePoint

Representaciones de imágenes son una característica de SharePoint Online que permite atender a las diferentes versiones de imágenes en función de las dimensiones de la imagen predefinidos. Esto es especialmente importante cuando hay contenido de imagen generados por el usuario o las dimensiones de la imagen como el ancho y alto se corrigen por el CSS en el sitio. Incluso si una imagen es fija por CSS, la imagen a resolución completa se carga todavía. En este caso se puede reducir el tamaño del archivo mediante el uso de representaciones de imágenes.
  
> [!NOTE]
> Las representaciones solo están disponibles para SharePoint cuando se habilite la publicación. Puede habilitar la publicación en configuración de \> configuración del sitio \> administrar características del sitio \> publicación de SharePoint Server. La opción no aparecerá en caso contrario. 
  
La modificación de tamaño para representación de imágenes funciona tomando la dimensión más pequeña que define, ancho o alto y, luego cambiando el tamaño de la imagen para que la otra dimensión cambie de tamaño automáticamente en función de la relación de aspecto bloqueada. De forma predeterminada, se recorta la imagen desde el centro por las dimensiones restantes. Por ejemplo, si define una representación de 100px de ancho y 50px de alto, y la imagen original tiene 1000px de ancho y 800px de alto, se modificará el tamaño de modo que la dimensión de 800px ahora tenga 50px y la dimensión de 1000px (ahora 62,5px) se recorte desde el centro de la imagen.
  
Los pasos son relativamente sencillos pero, para que las imágenes usen estas representaciones, las representaciones deben estar en el sitio de SharePoint antes de agregar las imágenes. Además, también debe tener activadas las características Infraestructura de publicación de SharePoint Server (nivel de colección de sitios) y Publicación de SharePoint Server (nivel de sitio).
  
 **Agregar una representación de una imagen para acelerar la carga de la página**
  
1. Compruebe que la cuenta de usuario que está realizando este procedimiento tiene, como mínimo, permisos de diseño en el sitio de nivel superior de la colección de sitios, y que se publica el sitio a una página Web.
    
2. En un explorador web, vaya al sitio de nivel superior de la colección de sitios de publicación.
    
3. Elija el icono **Configuración**. 
    
4. En la página **Configuración del sitio**, en la sección **Apariencia**, verá las representaciones de imágenes integradas. 
    
    Puede usar las representaciones de fábrica o elegir **Representaciones de imágenes** para crear una nueva. 
    
    ![Captura de pantalla de representación de una imagen](media/eaae0d53-657d-47ef-b687-65c5167eae4d.PNG)
  
5. En la página **Representaciones de imágenes**, elija **Agregar nuevo elemento**.
    
    ![Captura de pantalla de Agregar nuevo elemento](media/8cede22e-52bf-4d9d-99cb-162f2f6ce92b.PNG)
  
6. En la página **Nueva representación de imagen**, en el cuadro **Nombre**, escriba un nombre para la representación. 
    
7. En los cuadros de texto **Ancho** y **Alto**, escriba el ancho y alto, en píxeles, de la representación y luego elija **Guardar**.
    
    ![Captura de pantalla del nombre de la representación de imagen](media/5a6119ed-c163-40df-a4db-ec629d15607d.PNG)
  
## <a name="custom-cropping-with-image-renditions-in-sharepoint"></a>Recorte personalizado con representaciones de imágenes en SharePoint

De forma predeterminada, se genera una representación de una imagen desde el centro de la imagen. Puede ajustar la representación de una imagen para imágenes individuales al recortar la parte de la imagen que desea usar. Puede recortar las imágenes de forma individual, por copia. Recortar las imágenes acelera la carga mediante el uso de memoria caché de blob de SharePoint para crear una versión de la imagen para cada copia de la página. De este modo, la carga del servidor se reduce debido a que la imagen es sólo cambia el tamaño de una sola vez y, a continuación, está lista para servir a los usuarios finales varias veces. Para obtener más información sobre cómo recortar una representación de una imagen, vea [recortar una representación de una imagen](https://go.microsoft.com/fwlink/p/?LinkId=525626).
  

