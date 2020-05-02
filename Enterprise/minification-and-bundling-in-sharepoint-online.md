---
title: Minificación y agrupación en SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 3/1/2017
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
ms.assetid: 87a52468-994e-43a2-b155-7229ed659291
description: En este artículo se describe cómo usar minificación y las técnicas de agrupación con Web Essentials para reducir el número de solicitudes HTTP y reducir el tiempo que se tarda en cargar páginas en SharePoint Online.
ms.openlocfilehash: 44f9e6151c22c3715b56a164bd0c9cacedcf2580
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004775"
---
# <a name="minification-and-bundling-in-sharepoint-online"></a>Minificación y agrupación en SharePoint Online

En este artículo se describe cómo usar minificación y las técnicas de agrupación con Web Essentials para reducir el número de solicitudes HTTP y reducir el tiempo que se tarda en cargar páginas en SharePoint Online.
  
Al personalizar el sitio web, puede acabar agregando un gran número de archivos adicionales al servidor para admitir la personalización. La adición de JavaScript, CSS e imágenes adicionales aumenta el número de solicitudes HTTP que se realizan en el servidor, lo que, a su vez, aumenta el tiempo que se tarda en mostrar una página web. Si tiene varios archivos del mismo tipo, puede agrupar estos archivos para hacer que la descarga de estos archivos sea más rápida.
  
Para los archivos JavaScript y CSS, también puede usar un enfoque denominado minificación, donde reduce el tamaño total de los archivos quitando el espacio en blanco y otros caracteres que no son necesarios.
  
## <a name="minification-and-bundling-javascript-and-css-files-with-web-essentials"></a>Minificación y agrupar archivos JavaScript y CSS con Web Essentials

Puede usar software de terceros, como Web Essentials, para agrupar archivos CSS y JavaScript.
  
> [!IMPORTANT]
> Web Essentials es un proyecto de terceros, basado en la comunidad de código abierto. El software es una extensión de Visual Studio 2012 y Visual Studio 2013 y no es compatible con Microsoft. Para descargar Web Essentials, visite el sitio web en [https://vswebessentials.com/download](https://go.microsoft.com/fwlink/p/?LinkId=525629). 
  
Web Essentials ofrece dos formas de agrupación:
  
- . bundle: para archivos CSS y JavaScript
    
- . Sprite: para imágenes (solo disponible en Visual Studio 2013)
    
Puede usar Web Essentials si tiene una característica existente con algunos elementos de personalización de marca a los que se hace referencia en una página maestra personalizada, como:
  
![Captura de pantalla de un elemento que identifica la marca en la página maestra personalizada](media/3a6eba36-973d-482b-8556-a9394b8ba19f.png)
  
 **Para crear una agrupación de TE000127218 y CSS en Web Essentials**
  
1. En Visual Studio, en el explorador de soluciones, seleccione los archivos que desea incluir en la agrupación.
    
2. Haga clic con el botón derecho en los archivos seleccionados y seleccione **Web Essentials** \> **crear archivo de agrupación de JavaScript** en el menú contextual. Por ejemplo: 
    
    ![Captura de pantalla que muestra las opciones de menú de Web Essentials](media/41aac84c-4538-4f78-b454-46e651f868a3.png)
  
## <a name="viewing-the-results-of-bundling-javascript-and-css-files"></a>Visualización de los resultados de la agrupación de archivos JavaScript y CSS

Al crear una agrupación de JavaScript y CSS, Web Essentials crea un archivo XML denominado archivo de receta que identifica los archivos JavaScript y CSS, así como otra información de configuración: 
  
![Captura de pantalla del archivo receta de JavaScript y CSS](media/7ba891f8-52d8-467b-a0f6-b062dd1137a4.png)
  
Además, si la marca reducir archivos se establece en true en la receta de la agrupación, los archivos se reducen en tamaño y se agrupan. Esto significa que se crearon versiones reducidos de los archivos de JavaScript a los que se puede hacer referencia en la página maestra.
  
![Captura de pantalla de la marca de minify establecida en verdadero](media/50523af2-6412-4117-ac3d-5bd26f6d562e.png)
  
Al cargar una página desde el sitio web, puede usar las herramientas de desarrollo de su explorador Web, como Internet Explorer 11, para ver el número de solicitudes enviadas al servidor y el tiempo que tardó cada archivo en cargarse.
  
La siguiente figura es el resultado de cargar los archivos JavaScript y CSS antes de minificación.
  
![Captura de pantalla que muestra los 80 artículos descargándose](media/e2df3912-1923-46e6-8cf2-3015a31554e1.png)
  
Después de agrupar los archivos CSS y JavaScript, el número de solicitudes se ha quitado a 74 y cada archivo tardó ligeramente más tiempo que los archivos originales para descargarlos individualmente:
  
![Captura de pantalla que muestra los 74 artículos descargándose](media/686c4387-70e8-4a74-9d45-059f33a91184.png)
  
Después de la agrupación, el archivo de agrupación de JavaScript se ha reducido significativamente de 815KB a 365KB:
  
![Captura de pantalla que muestra el tamaño de la descarga reducido](media/5e7dbd98-faff-4f68-b320-108fb252e395.png)
  
## <a name="bundling-images-by-creating-an-image-sprite"></a>Agrupación de imágenes mediante la creación de un sprite de imagen

De forma similar a la agrupación de archivos JavaScript y CSS, puede combinar muchos iconos pequeños y otras imágenes comunes en una hoja de sprites más grande y, a continuación, usar CSS para mostrar las imágenes individuales. En lugar de descargar cada imagen individual, el explorador Web del usuario descarga una hoja de Sprite una vez y, a continuación, la almacena en caché en el equipo local. Esto mejora el rendimiento de la carga de la página al reducir el número de descargas y viajes de ida y vuelta al servidor Web.
  
 **Para crear un sprite de imagen en Web Essentials**
  
1. En Visual Studio, en el explorador de soluciones, seleccione los archivos que desea incluir en la agrupación.
    
2. Haga clic con el botón secundario en los archivos seleccionados y, a continuación, seleccione **Web Essentials** \> **crear Sprite de imagen** en el menú contextual. Por ejemplo: 
    
    ![Captura de pantalla que muestra cómo crear un objeto sprite de imagen](media/de0fe741-4ef7-4e3b-bafa-ef9f4822dac6.png)
  
3. Elija una ubicación para guardar el archivo de Sprite. El archivo. Sprite es un archivo XML que describe la configuración y los archivos del Sprite. En las figuras siguientes se muestra un ejemplo de un archivo de Sprite PNG y su archivo XML correspondiente. Sprite.
    
    ![Captura de pantalla de un archivo de sprite](media/0876bb2a-d1b9-4169-8e95-9c290d628d90.png)
  
    ![Captura de pantalla de archivo XML de sprite](media/d1f94776-280d-4d56-abb5-384f145d9989.png)
  

