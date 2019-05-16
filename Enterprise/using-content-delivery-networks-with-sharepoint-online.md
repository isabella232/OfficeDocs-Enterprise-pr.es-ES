---
title: Using content delivery networks with SharePoint Online (Usar redes de entrega de contenido con SharePoint Online)
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Resumen: en este artículo se describen las redes de entrega de contenido (CDN) y cómo se pueden usar para aumentar el rendimiento de SharePoint Online.'
ms.openlocfilehash: 24b12ae60a8c089d8e32d2609957e8b0e3420510
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34070586"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Using content delivery networks with SharePoint Online (Usar redes de entrega de contenido con SharePoint Online)

 **Resumen:** En este artículo se describen las redes de entrega de contenido (CDN) y cómo se pueden usar para aumentar el rendimiento de SharePoint Online. 
  
En las comunidades de desarrollo web de hoy en día, hay muchas bibliotecas comunes (como archivos JavaScript y CSS) que puede incluir en la solución de SharePoint. Muchas de ellas están hospedadas por Microsoft en su red CDN de ASP. Esto significa que puede hacer referencia a estas bibliotecas desde estos servidores distribuidos y permitir que los sistemas de enrutamiento DNS integrados en Internet encuentren el servidor más cercano al usuario. Los ejemplos de este artículo muestran cómo la diferencia de tiempo entre la descarga de jQuery Library popular desde el servidor de SharePoint Online en comparación con la red CDN de ASP es bastante significativa. El usuario también puede tener la versión de la red CDN almacenada en caché en el equipo local para que no tenga que descargar el archivo. Esto puede ser importante si tiene usuarios distribuidos en todo el mundo y lejos del centro de recursos que hospeda el sitio de SharePoint Online.
  
Al crear páginas para SharePoint Online, la latencia puede verse afectada por la distancia física entre los usuarios y la ubicación de la instancia de SharePoint Online. Esto es especialmente importante para las organizaciones que tienen una presencia global en la que un sitio puede alojarse en un continente mientras que los usuarios del otro lado del mundo tienen acceso a su contenido. Las CDN ayudan a mitigar esta situación al hospedar determinados activos web populares en diferentes ubicaciones más cerca de los usuarios finales.
  
Dado que una red CDN es una red mundial de servidores que hospedan los mismos archivos, las direcciones URL de Internet para los archivos almacenados en los CDN se interpretan en el equipo cliente, de modo que el servidor más cercano al usuario tenga el archivo. Esto reduce considerablemente los retrasos causados por los viajes de ida y vuelta de la red.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>El desafío de hospedar sitios de SharePoint Online para una audiencia global

Los sitios de SharePoint Online se hospedan en centros de recursos relacionados con la ubicación (especificada por el usuario) seleccionada al registrarse con Office 365. Por ejemplo, si su sitio está en servidores de Estados Unidos y tiene usuarios que obtienen acceso al sitio desde Asia oriental, podrían surgir problemas de latencia debido a la distancia que tienen los datos para viajar por cable de fibra óptica.
  
Muchos archivos estáticos usados por la interfaz de usuario de SharePoint predeterminada ya están hospedados en la red mundial de CDN de Microsoft. Esto mejorará el rendimiento a lo largo del tiempo. Sin embargo, si usa los recursos de JavaScript y CSS populares (por ejemplo, JQuery, Modernizr, bootstrap o ASP.NET AJAX) puede mejorar las horas de carga de estos archivos con CDN disponibles de forma gratuita.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Ventajas de usar CDN para mejorar la velocidad de descarga

El uso de CDN puede mejorar los tiempos de carga de página por diversos motivos. Una razón es que la distancia entre la red CDN y el usuario puede ser menor que la distancia a la instancia de SharePoint Online. Estas redes están muy distribuidas y también están diseñadas para tener una disponibilidad muy alta y tiempos de respuesta. Otra razón es que si usa una biblioteca de archivos CSS conocida, junto con una red CDN, es posible que el usuario ya tenga la biblioteca almacenada en caché y que ni siquiera necesiten descargarla.
  
En las siguientes capturas de pantalla se muestran las ventajas de usar CDN. Estas capturas de pantalla se encuentran en la pestaña **red** de las herramientas de desarrollo de Internet Explorer 11. En estas capturas de pantalla se muestra la latencia de la biblioteca de jQuery de la popular. Para que aparezca esta pantalla, en Internet Explorer, presione **F12** y seleccione la pestaña **red** , que se simbólica con un icono de Wi-Fi. 
  
![Captura de pantalla de red F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
En esta captura de pantalla se muestra la biblioteca cargada en la galería de páginas maestras en el propio sitio de SharePoint Online. El tiempo que tardó en cargar la biblioteca es de 1,51 segundos.
  
![Captura de pantalla de tiempo de carga de 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
La segunda captura de pantalla muestra el mismo archivo que proporciona la red CDN de Microsoft. Esta vez la latencia es de alrededor de 496 milisegundos. Esto es una gran mejora y muestra que se ha recortado un segundo en todo el tiempo total para descargar el contenido de la página.
  
![Captura de pantalla de los tiempos de carga de 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Uso de redes CDN con SharePoint Server 2013

El uso de los CDN solo tiene sentido en un contexto de SharePoint Online y debe evitarse con SharePoint Server 2013. Esto se debe a que todas las ventajas sobre la ubicación geográfica no tienen el valor true si el servidor se encuentra local o geográficamente cerrado de todos modos. Además, si hay una conexión de red a los servidores en los que está hospedada, el sitio puede usarse sin una conexión a Internet y, por lo tanto, no puede recuperar los archivos de la red CDN. De lo contrario, debe usar una red CDN si hay una disponible y estable para la biblioteca y los archivos que necesita para su sitio.
  
## <a name="popular-cdns-and-how-to-use-them"></a>Redes CDN populares y cómo usarlas

La red CDN de AJAX de Microsoft ofrece la mayoría de las bibliotecas populares, incluidas jQuery (y todas sus otras bibliotecas), ASP.NET AJAX, Bootstrap, Knockout. js y muchos más.
  
Para incluir estos scripts en su proyecto, simplemente reemplace todas las referencias a estas bibliotecas disponibles públicamente por referencias a la dirección de la red CDN en lugar de incluirla en el propio proyecto. Por ejemplo, use el siguiente código para vincular a jQuery:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Para obtener más información acerca de las CDN, vea [redes de entrega de contenido](content-delivery-networks.md).
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Más temas sobre el uso de redes CDN con SharePoint

[Hospedar un elemento Web del lado cliente desde la red CDN de Office 365](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

