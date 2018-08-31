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
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minificación y agrupación en SharePoint Online

En este artículo se describe cómo utilizar la reducción y agrupación técnicas con Web Essentials para reducir el número de solicitudes HTTP y para reducir el tiempo que se tarda en cargar páginas en SharePoint Online.
  
Al personalizar su sitio web puede terminar agregando un gran número de archivos adicionales en el servidor para admitir la personalización. Agregar más imágenes, CSS y JavaScript aumenta el número de solicitudes HTTP al servidor, lo que a su vez aumenta el tiempo empleado en mostrar una página web. Si tiene varios archivos del mismo tipo, puede agrupar estos archivos para acelerar la descarga de los archivos.
  
Para los archivos CSS y JavaScript, también puede utilizar un enfoque llamado reducción, donde se reduce el tamaño total de archivos mediante la eliminación de espacio en blanco y otros caracteres que no son necesarios.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minificación y agrupación de archivos JavaScript y CSS con Web Essentials

Puede usar software de terceros como Web Essentials para agrupar los archivos CSS y JavaScript.
  
> [!IMPORTANT]
> Web Essentials es un proyecto de otro fabricante, Abrir origen, en función de la Comunidad. El software es una extensión de Visual Studio 2012 y Visual Studio 2013 y no es compatible con Microsoft. Para descargar Web Essentials, visite el sitio Web en [http://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629). 
  
Web Essentials ofrece dos formas de agrupación:
  
- .bundle: para archivos CSS y JavaScript
    
- .sprite: para imágenes (disponible solo en Visual Studio 2013)
    
Puede usar Web Essentials si tiene una característica existente con algunos elementos de personalización de marca a los que se hace referencia dentro de una página maestra personalizada, como:
  
![Captura de pantalla de un elemento que identifica la marca en la página maestra personalizada](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **Para crear un paquete de TE000127218 y CSS en Web Essentials**
  
1. En Visual Studio, en el Explorador de soluciones, seleccione los archivos que desea incluir en la agrupación.
    
2. Haga clic en los archivos seleccionados y, a continuación, seleccione **Web Essentials** \> **archivo de paquete de creación de JavaScript** en el menú contextual. Por ejemplo: 
    
    ![Captura de pantalla que muestra las opciones de menú de Web Essentials](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Ver los resultados de agrupar archivos JavaScript y CSS

Cuando se crea una agrupación de JavaScript y CSS, Web Essentials crea un archivo XML llamado archivo de receta que identifica a los archivos JavaScript y CSS y también a información de configuración: 
  
![Captura de pantalla del archivo receta de JavaScript y CSS](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Además, si la marca de minificación se establece como true en la receta de agrupación, los archivos pasan a tener menos tamaño y a estar agrupados. Esto significa que se crearon nuevas versiones minificadas de los archivos JavaScript y que usted puede hacer referencia a estas versiones en la página maestra.
  
![Captura de pantalla de la marca de minify establecida en verdadero](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Cuando carga una página de su sitio web, puede usar las herramientas de desarrollo desde el explorador web, como Internet Explorer 11, para ver el número de solicitudes enviadas al servidor y cuánto tiempo tardó cada archivo en cargarse.
  
La figura siguiente es el resultado de cargar los archivos JavaScript y CSS antes de la minificación.
  
![Captura de pantalla que muestra los 80 artículos descargándose](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Después de agrupar los archivos CSS y JavaScript, el número de solicitudes bajó a 74 y la descarga individual de cada archivo solo fue ligeramente más lenta que con los archivos originales:
  
![Captura de pantalla que muestra los 74 artículos descargándose](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Después de la agrupación, el archivo de agrupación JavaScript se reduce significativamente de 815 KB a 365 KB:
  
![Captura de pantalla que muestra el tamaño de la descarga reducido](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Agrupar imágenes mediante la creación de un sprite de imagen

De forma similar a cómo se agrupan los archivos CSS y JavaScript, puede combinar muchos iconos pequeños y otras imágenes comunes en una hoja de sprite más grande y, a continuación, usar CSS para revelar las imágenes individuales. En lugar de descargar cada imagen individual, el explorador del usuario web de descargas de la hoja de sprite una vez y, a continuación, se almacena en caché en el equipo local. Esto mejora el rendimiento de carga de página mediante un corte hacia abajo en el número de descargas y versiones de ida y vuelta al servidor web.
  
 **Para crear un sprite de imagen en Web Essentials**
  
1. En Visual Studio, en el Explorador de soluciones, seleccione los archivos que desea incluir en la agrupación.
    
2. Haga clic en los archivos seleccionados y, a continuación, seleccione **Web Essentials** \> **crear sprite de imagen** en el menú contextual. Por ejemplo: 
    
    ![Captura de pantalla que muestra cómo crear un objeto sprite de imagen](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Elija una ubicación para guardar el archivo de sprite. El archivo .sprite es un archivo XML que describe la configuración y los archivos del sprite. Las siguientes figuras muestran un ejemplo de un archivo PNG de sprite y el archivo XML de .sprite correspondiente.
    
    ![Captura de pantalla de un archivo de sprite](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Captura de pantalla de archivo XML de sprite](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

