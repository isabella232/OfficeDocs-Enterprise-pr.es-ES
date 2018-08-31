---
title: Uso de redes de entrega de contenido con SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 5/8/2017
ms.audience: Admin
ms.topic: troubleshooting
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: 9a64268c-0b74-4eaa-b971-fb6380b1b165
description: 'Resumen: En este artículo se describe redes de distribución de contenido (CDN) y cómo puede usarlos para aumentar el rendimiento de SharePoint Online.'
ms.openlocfilehash: 63062c08d0c22518eb36ea0a6faa97106fd394b4
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542812"
---
# <a name="using-content-delivery-networks-with-sharepoint-online"></a>Uso de redes de entrega de contenido con SharePoint Online

 **Resumen:** En este artículo se describe redes de distribución de contenido (CDN) y cómo puede usarlos para aumentar el rendimiento de SharePoint Online. 
  
En las Comunidades de desarrollo de web de hoy, hay muchas bibliotecas comunes (por ejemplo, archivos CSS y JavaScript) que se pueden incluir en la solución de SharePoint. Muchos de estos están hospedados por Microsoft en sus CDN de ASP. Esto significa que puede hacer referencia a estas bibliotecas de estos servidores distribuidos y permitir integrados sistemas enrutamiento de DNS de internet buscar el servidor más cercano al usuario. Los ejemplos de este artículo demuestran cómo es un proceso bastante significativa la diferencia de tiempo entre la descarga de jQuery biblioteca populares desde el servidor de SharePoint Online frente a la CDN de ASP. El usuario también tengan ya la versión CDN almacena en caché en el equipo local para que no tienen que descargar el archivo. Esto puede ser importante si tiene usuarios que se distribuyen de todo el mundo y lejos desde el centro de datos que hospeda su sitio de SharePoint Online.
  
Al crear páginas de SharePoint Online, la latencia puede verse afectada por la distancia física entre los usuarios y la ubicación de la instancia de SharePoint Online. Esto es especialmente importante para las organizaciones que tienen una presencia global donde un sitio puede estar hospedado en un continente mientras los usuarios del otro lado del mundo tienen acceso a su contenido. Las CDN ayudan a mitigar esta situación al hospedar ciertos activos web populares en diferentes ubicaciones más cerca de los usuarios finales.
  
Como una CDN es una red mundial de servidores que hospedan a los mismos archivos, las direcciones URL de Internet para los archivos almacenados en las CDN se interpretan en el equipo cliente de modo que el servidor que está más cerca del usuario proporciona el archivo. Esto reduce significativamente los retrasos causados por los ciclos de ida y vuelta.
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a>El desafío de hospedar sitios de SharePoint Online para un público global

Los sitios de SharePoint Online se hospedan en centros de datos asociados a la ubicación (especificada por el usuario) seleccionada al suscribirse a Office 365. Por ejemplo, si el sitio está en servidores en los Estados Unidos y tiene usuarios que acceden al sitio desde Asia oriental, pueden surgir problemas de latencia debido a la distancia que los datos tienen que recorrer por el cable de fibra óptica.
  
Muchos archivos estáticos usados por la interfaz de usuario de SharePoint predeterminado ya se hospedan en red en todo el mundo de Microsoft de las CDN. Esto mejorará el rendimiento a través del tiempo. Sin embargo, si utiliza cualquier activos populares de CSS y JavaScript (por ejemplo; JQuery, Modernizr, inicio o ASP.NET Ajax) puede mejorar los tiempos de carga de estos archivos mediante el uso de las CDN disponibles de forma gratuita.
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a>Ventajas de utilizar las CDN para mejorar la velocidad de descarga

Uso de las CDN, puede mejorar tiempos de carga de página para una variedad de motivos. Una razón es que la distancia entre la CDN y el usuario puede ser más corta que la distancia a la instancia de SharePoint Online. Estas redes se distribuyen altamente y también están diseñadas para tener muy altas disponibilidad y tiempos de respuesta. Otra razón es si está utilizando una biblioteca de popular de archivos CSS, junto con una CDN, es posible que el usuario ya tenga la biblioteca de caché y que no necesitan incluso descargarlo en absoluto.
  
Las capturas de pantalla siguientes ilustran las ventajas de usar las CDN. Son estas capturas de pantalla de la ficha de **red** en las herramientas de desarrollo de Internet Explorer 11. Estas capturas de pantalla muestran la latencia en la biblioteca populares jQuery. Para que aparezca esta pantalla, en el Explorador de Internet, presione la **tecla F12** y seleccione la ficha de **red** que se representa con un icono de Wi-Fi. 
  
![Captura de pantalla de red F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
Esta captura de pantalla muestra la biblioteca que se cargan en la Galería de páginas maestras en el propio sitio de SharePoint Online. El tiempo que se tardó en cargar la biblioteca es 1.51 segundos.
  
![Captura de pantalla de tiempo de carga de 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
La segunda captura de pantalla muestra el mismo archivo de entrega de Microsoft CDN. En este momento la latencia es alrededor 496 milisegundos. Esto es una mejora de gran tamaño y muestra que se eliminó un segundo todo desactiva el tiempo total para descargar el contenido de la página.
  
![Captura de pantalla de los tiempos de carga de 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a>Usar las CDN con SharePoint Server 2013

Utilizando las CDN sólo tiene sentido en un contexto de SharePoint Online y debería evitarse con SharePoint Server 2013. Esto es debido a que no todas las ventajas alrededor de ubicación geográfica de suspensión es true si el servidor se encuentra local o geográficamente cerrar de todos modos. Además, si hay una conexión de red a los servidores donde está hospedado, el sitio se puede utilizar sin una conexión a Internet y, por tanto, no puede recuperar los archivos CDN. De lo contrario, debe usar una CDN si hay uno disponible y estables para la biblioteca y los archivos que necesita para su sitio.
  
## <a name="popular-cdns-and-how-to-use-them"></a>CDN populares y cómo usarlas

Ajax CDN de Microsoft ofrece la mayoría de las bibliotecas populares incluidas jQuery (y todos sus otras bibliotecas), ASP.NET Ajax, programa previo, Knockout.js y muchos más.
  
Para incluir estos scripts en su proyecto, simplemente reemplace las referencias a estas bibliotecas disponibles públicamente con referencias a la dirección CDN en lugar de incluirlas en su propio proyecto. Por ejemplo, use el siguiente código para vincular a jQuery:
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

Para obtener más información acerca de las CDN, vea [redes de entrega de contenido](content-delivery-networks.md).
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a>Más temas acerca del uso de las CDN con SharePoint

[Elemento web de cliente de Office 365 CDN de hospedaje](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

