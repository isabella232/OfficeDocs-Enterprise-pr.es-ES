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
# <a name="using-content-delivery-networks-with-sharepoint-online"></a><span data-ttu-id="1a8c5-103">Uso de redes de entrega de contenido con SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1a8c5-103">Using content delivery networks with SharePoint Online</span></span>

 <span data-ttu-id="1a8c5-104">**Resumen:** En este artículo se describe redes de distribución de contenido (CDN) y cómo puede usarlos para aumentar el rendimiento de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-104">**Summary:** This article describes Content Delivery Networks (CDNs) and how you can use them to increase SharePoint Online performance.</span></span> 
  
<span data-ttu-id="1a8c5-p101">En las Comunidades de desarrollo de web de hoy, hay muchas bibliotecas comunes (por ejemplo, archivos CSS y JavaScript) que se pueden incluir en la solución de SharePoint. Muchos de estos están hospedados por Microsoft en sus CDN de ASP. Esto significa que puede hacer referencia a estas bibliotecas de estos servidores distribuidos y permitir integrados sistemas enrutamiento de DNS de internet buscar el servidor más cercano al usuario. Los ejemplos de este artículo demuestran cómo es un proceso bastante significativa la diferencia de tiempo entre la descarga de jQuery biblioteca populares desde el servidor de SharePoint Online frente a la CDN de ASP. El usuario también tengan ya la versión CDN almacena en caché en el equipo local para que no tienen que descargar el archivo. Esto puede ser importante si tiene usuarios que se distribuyen de todo el mundo y lejos desde el centro de datos que hospeda su sitio de SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p101">In today's web development communities, there are many common libraries (such as JavaScript and CSS files) that you may include in your SharePoint solution. Many of these are hosted by Microsoft on their ASP CDN. This means you can reference these libraries from these distributed servers and allow the internet's built-in DNS routing systems to find the closest server to your user. The examples in this article demonstrate how the time difference between downloading the popular library jQuery from the SharePoint Online server versus the ASP CDN is quite significant. The user also may already have the CDN version cached on the local computer so that they do not have to download the file. This can be important if you have users distributed all over the world and far away from the datacenter that hosts your SharePoint Online site.</span></span>
  
<span data-ttu-id="1a8c5-p102">Al crear páginas de SharePoint Online, la latencia puede verse afectada por la distancia física entre los usuarios y la ubicación de la instancia de SharePoint Online. Esto es especialmente importante para las organizaciones que tienen una presencia global donde un sitio puede estar hospedado en un continente mientras los usuarios del otro lado del mundo tienen acceso a su contenido. Las CDN ayudan a mitigar esta situación al hospedar ciertos activos web populares en diferentes ubicaciones más cerca de los usuarios finales.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p102">When creating pages for SharePoint Online, latency can be affected by the physical distance between your users and the location of the SharePoint Online instance. This is particularly important for organizations that have a global presence where a site may be hosted on one continent while users on the other side of the world are accessing its content. CDNs help mitigate this situation by hosting certain popular web assets in different locations closer to the end users.</span></span>
  
<span data-ttu-id="1a8c5-p103">Como una CDN es una red mundial de servidores que hospedan a los mismos archivos, las direcciones URL de Internet para los archivos almacenados en las CDN se interpretan en el equipo cliente de modo que el servidor que está más cerca del usuario proporciona el archivo. Esto reduce significativamente los retrasos causados por los ciclos de ida y vuelta.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p103">Since a CDN is a worldwide network of servers that host the same files, Internet URLs for files stored on the CDNs are interpreted by the client machine so that the server that is closest to the user serves the file. Doing this significantly reduces delays caused by network round trips.</span></span>
  
## <a name="the-challenge-of-hosting-sharepoint-online-sites-for-a-global-audience"></a><span data-ttu-id="1a8c5-116">El desafío de hospedar sitios de SharePoint Online para un público global</span><span class="sxs-lookup"><span data-stu-id="1a8c5-116">The challenge of hosting SharePoint Online sites for a global audience</span></span>

<span data-ttu-id="1a8c5-p104">Los sitios de SharePoint Online se hospedan en centros de datos asociados a la ubicación (especificada por el usuario) seleccionada al suscribirse a Office 365. Por ejemplo, si el sitio está en servidores en los Estados Unidos y tiene usuarios que acceden al sitio desde Asia oriental, pueden surgir problemas de latencia debido a la distancia que los datos tienen que recorrer por el cable de fibra óptica.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p104">SharePoint Online sites are hosted at datacenters relative to the location (specified by the user) selected when you signed up with Office 365. For example, if your site is on servers in the United States and you have users accessing the site from East Asia, latency issues might arise due to the distance the data has to travel over fiber optic cable.</span></span>
  
<span data-ttu-id="1a8c5-p105">Muchos archivos estáticos usados por la interfaz de usuario de SharePoint predeterminado ya se hospedan en red en todo el mundo de Microsoft de las CDN. Esto mejorará el rendimiento a través del tiempo. Sin embargo, si utiliza cualquier activos populares de CSS y JavaScript (por ejemplo; JQuery, Modernizr, inicio o ASP.NET Ajax) puede mejorar los tiempos de carga de estos archivos mediante el uso de las CDN disponibles de forma gratuita.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p105">Many static files used by the default SharePoint user interface are already hosted on Microsoft's worldwide network of CDNs. This will improve performance over time. However, if you use any popular JavaScript and CSS assets (for example; JQuery, Modernizr, Bootstrap, or ASP.NET Ajax) you can improve the loading times of these files by using freely available CDNs.</span></span>
  
## <a name="advantages-of-using-cdns-to-improve-download-speed"></a><span data-ttu-id="1a8c5-122">Ventajas de utilizar las CDN para mejorar la velocidad de descarga</span><span class="sxs-lookup"><span data-stu-id="1a8c5-122">Advantages of using CDNs to improve download speed</span></span>

<span data-ttu-id="1a8c5-p106">Uso de las CDN, puede mejorar tiempos de carga de página para una variedad de motivos. Una razón es que la distancia entre la CDN y el usuario puede ser más corta que la distancia a la instancia de SharePoint Online. Estas redes se distribuyen altamente y también están diseñadas para tener muy altas disponibilidad y tiempos de respuesta. Otra razón es si está utilizando una biblioteca de popular de archivos CSS, junto con una CDN, es posible que el usuario ya tenga la biblioteca de caché y que no necesitan incluso descargarlo en absoluto.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p106">Using CDNs can improve page load times for a variety of reasons. One reason is that the distance between the CDN and the user may be shorter than the distance to the SharePoint Online instance. These networks are highly distributed and are also designed to have very high availability and response times. Another reason is that if you are using a popular library of CSS files, in conjunction with a CDN, the user may already have the library cached and they won't even need to download it at all.</span></span>
  
<span data-ttu-id="1a8c5-p107">Las capturas de pantalla siguientes ilustran las ventajas de usar las CDN. Son estas capturas de pantalla de la ficha de **red** en las herramientas de desarrollo de Internet Explorer 11. Estas capturas de pantalla muestran la latencia en la biblioteca populares jQuery. Para que aparezca esta pantalla, en el Explorador de Internet, presione la **tecla F12** y seleccione la ficha de **red** que se representa con un icono de Wi-Fi.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p107">The following screen shots illustrate the advantages of using CDNs. These screen shots are from the **Network** tab in the Internet Explorer 11 developer tools. These screen shots show the latency on the popular library jQuery. To bring up this screen, in Internet Explorer, press **F12** and select the **Network** tab which is symbolized with a Wi-Fi icon.</span></span> 
  
![Captura de pantalla de red F12](media/930541fd-af9b-434a-ae18-7bda867be128.png)
  
<span data-ttu-id="1a8c5-p108">Esta captura de pantalla muestra la biblioteca que se cargan en la Galería de páginas maestras en el propio sitio de SharePoint Online. El tiempo que se tardó en cargar la biblioteca es 1.51 segundos.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p108">This screen shot shows the library uploaded to the master page gallery on the SharePoint Online site itself. The time it took to upload the library is 1.51 seconds.</span></span>
  
![Captura de pantalla de tiempo de carga de 1,51 s](media/64225c79-fa53-480f-81cd-0d351674320e.png)
  
<span data-ttu-id="1a8c5-p109">La segunda captura de pantalla muestra el mismo archivo de entrega de Microsoft CDN. En este momento la latencia es alrededor 496 milisegundos. Esto es una mejora de gran tamaño y muestra que se eliminó un segundo todo desactiva el tiempo total para descargar el contenido de la página.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p109">The second screen shot shows the same file delivered by Microsoft's CDN. This time the latency is around 496 milliseconds. This is a large improvement and shows that a whole second is shaved off the total time to download the page content.</span></span>
  
![Captura de pantalla de los tiempos de carga de 469 ms](media/6a553cc3-25a0-42c1-aae7-4aebbc2eb4c3.png)
  
## <a name="using-cdns-with-sharepoint-server-2013"></a><span data-ttu-id="1a8c5-139">Usar las CDN con SharePoint Server 2013</span><span class="sxs-lookup"><span data-stu-id="1a8c5-139">Using CDNs with SharePoint Server 2013</span></span>

<span data-ttu-id="1a8c5-p110">Utilizando las CDN sólo tiene sentido en un contexto de SharePoint Online y debería evitarse con SharePoint Server 2013. Esto es debido a que no todas las ventajas alrededor de ubicación geográfica de suspensión es true si el servidor se encuentra local o geográficamente cerrar de todos modos. Además, si hay una conexión de red a los servidores donde está hospedado, el sitio se puede utilizar sin una conexión a Internet y, por tanto, no puede recuperar los archivos CDN. De lo contrario, debe usar una CDN si hay uno disponible y estables para la biblioteca y los archivos que necesita para su sitio.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p110">Using CDNs only makes sense in a SharePoint Online context and should be avoided with SharePoint Server 2013. This is because all of the advantages around geographic location do not hold true if the server is located on-premises or geographically close anyway. Additionally, if there is a network connection to the servers where it's hosted, then the site may be used without an Internet connection and therefore cannot retrieve the CDN files. Otherwise, you should use a CDN if there is one available and stable for the library and files you need for your site.</span></span>
  
## <a name="popular-cdns-and-how-to-use-them"></a><span data-ttu-id="1a8c5-144">CDN populares y cómo usarlas</span><span class="sxs-lookup"><span data-stu-id="1a8c5-144">Popular CDNs and how to use them</span></span>

<span data-ttu-id="1a8c5-145">Ajax CDN de Microsoft ofrece la mayoría de las bibliotecas populares incluidas jQuery (y todos sus otras bibliotecas), ASP.NET Ajax, programa previo, Knockout.js y muchos más.</span><span class="sxs-lookup"><span data-stu-id="1a8c5-145">Microsoft's Ajax CDN offers most of the popular libraries including jQuery (and all of its other libraries), ASP.NET Ajax, Bootstrap, Knockout.js, and many more.</span></span>
  
<span data-ttu-id="1a8c5-p111">Para incluir estos scripts en su proyecto, simplemente reemplace las referencias a estas bibliotecas disponibles públicamente con referencias a la dirección CDN en lugar de incluirlas en su propio proyecto. Por ejemplo, use el siguiente código para vincular a jQuery:</span><span class="sxs-lookup"><span data-stu-id="1a8c5-p111">To include these scripts in your project, simply replace any references to these publicly available libraries with references to the CDN address instead of including it in your project itself. For example, use the following code to link to jQuery:</span></span>
  
```
<script src=http://ajax.aspnetcdn.com/ajax/jquery-2.1.1.js> </script>
```

<span data-ttu-id="1a8c5-148">Para obtener más información acerca de las CDN, vea [redes de entrega de contenido](content-delivery-networks.md).</span><span class="sxs-lookup"><span data-stu-id="1a8c5-148">For more information about CDNs, see [Content delivery networks](content-delivery-networks.md).</span></span>
  
## <a name="more-topics-about-using-cdns-with-sharepoint"></a><span data-ttu-id="1a8c5-149">Más temas acerca del uso de las CDN con SharePoint</span><span class="sxs-lookup"><span data-stu-id="1a8c5-149">More topics about using CDNs with SharePoint</span></span>

[<span data-ttu-id="1a8c5-150">Elemento web de cliente de Office 365 CDN de hospedaje</span><span class="sxs-lookup"><span data-stu-id="1a8c5-150">Hosting client-side web part from Office 365 CDN</span></span>](https://dev.office.com/sharepoint/docs/spfx/web-parts/get-started/hosting-webpart-from-office-365-cdn)
  

