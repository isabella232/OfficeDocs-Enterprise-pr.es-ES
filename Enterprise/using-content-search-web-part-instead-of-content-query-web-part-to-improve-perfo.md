---
title: Uso de elemento de Web de búsqueda de contenido en lugar de elemento Web consulta de contenido para mejorar el rendimiento en SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 4/20/2015
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: En este artículo se describe cómo aumentar el rendimiento mediante el reemplazo del elemento Web consulta de contenido con el elemento Web de búsqueda de contenido en SharePoint Server 2013 y SharePoint Online.
ms.openlocfilehash: f86a4b75c4bf75ebaa99924411d017c7eb7b6760
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22543019"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="62a47-103">Uso de elemento de Web de búsqueda de contenido en lugar de elemento Web consulta de contenido para mejorar el rendimiento en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="62a47-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="62a47-104">En este artículo se describe cómo aumentar el rendimiento mediante el reemplazo del elemento Web consulta de contenido con el elemento Web de búsqueda de contenido en SharePoint Server 2013 y SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="62a47-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="62a47-p101">Una de las nuevas características más eficaces de SharePoint Server 2013 y SharePoint Online es la parte de Web de búsqueda de contenido (CSWP). Este elemento Web utiliza el índice de búsqueda para recuperar rápidamente los resultados que se muestran al usuario. Use el elemento Web de búsqueda de contenido en lugar del contenido consulta de elemento Web (CQWP) en las páginas para mejorar el rendimiento para los usuarios.</span><span class="sxs-lookup"><span data-stu-id="62a47-p101">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP). This Web Part uses the search index to quickly retrieve results which are shown to the user. Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="62a47-p102">Uso de un elemento Web de búsqueda de contenido a través de un elemento Web consulta de contenido, se producirá casi siempre mucho mejor rendimiento de carga de página en SharePoint Online. Hay una poco una configuración adicional para obtener la consulta derecha, pero las recompensas son usuarios más satisfechos y mejorar el rendimiento.</span><span class="sxs-lookup"><span data-stu-id="62a47-p102">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online. There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="62a47-110">Comparación de la mejora del rendimiento que obtiene al utilizar el elemento Web de búsqueda de contenido en lugar de elemento Web consulta de contenido</span><span class="sxs-lookup"><span data-stu-id="62a47-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="62a47-p103">Los siguientes ejemplos muestran las mejoras de rendimiento relativa que puede recibir al usar un elemento Web de búsqueda de contenido en lugar de un elemento Web consulta de contenido. Los efectos son más obvios con una estructura compleja de sitios y las consultas de contenido muy amplias.</span><span class="sxs-lookup"><span data-stu-id="62a47-p103">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part. The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="62a47-113">Este sitio de ejemplo tiene las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="62a47-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="62a47-114">8 niveles de subsitios.</span><span class="sxs-lookup"><span data-stu-id="62a47-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="62a47-115">Se enumeran con un tipo de contenido personalizado "fruta".</span><span class="sxs-lookup"><span data-stu-id="62a47-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="62a47-116">En el elemento Web, la consulta de contenido es amplia, devolución de todos los elementos con el tipo de contenido de "fruta".</span><span class="sxs-lookup"><span data-stu-id="62a47-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="62a47-p104">En el ejemplo se utiliza sólo 50 artículos en todos los sitios de 8. Los efectos se pronuncia aún más para los sitios con más contenido.</span><span class="sxs-lookup"><span data-stu-id="62a47-p104">The example only uses 50 items across the 8 sites. The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="62a47-119">Aquí es una captura de pantalla de los resultados del elemento Web consulta de contenido.</span><span class="sxs-lookup"><span data-stu-id="62a47-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Gráfico que muestra la consulta de contenido del elemento web](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="62a47-p105">En el Explorador de Internet, utilice la ficha de **red** de las herramientas de desarrollo F12 para ver los detalles del encabezado de respuesta. En la siguiente captura de pantalla, el valor de la **SPRequestDuration** para esta carga de página es 924 milisegundos.</span><span class="sxs-lookup"><span data-stu-id="62a47-p105">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header. In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![Captura de pantalla que muestra la duración de la solicitud de 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="62a47-p106">**SPRequestDuration** indica la cantidad de trabajo que se realiza en el servidor para preparar la página. Elementos Web de consulta de contenido con elementos Web de búsqueda de contenido de conmutación considerablemente reduce el tiempo necesario para representar la página. Sin embargo, una página con un elemento de Web de búsqueda de contenido equivalente, devolver el mismo número de resultados tiene un valor de **SPRequestDuration** de 106 milisegundos, como se muestra en esta captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="62a47-p106">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page. Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page. By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![Captura de pantalla que muestra la duración de la solicitud de 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="62a47-128">Adición de un elemento Web de búsqueda de contenido en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="62a47-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="62a47-p107">Adición de un elemento Web de búsqueda de contenido es muy similar a un elemento de Web de consulta de contenido normal. Vea la sección *"Agregar un elemento Web de búsqueda"* en [configurar un elemento Web de búsqueda de contenido en SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="62a47-p107">Adding a Content Search Web Part is very similar to a regular Content Query Web Part. See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="62a47-131">Creación de la consulta de búsqueda adecuada para su elemento Web búsqueda de contenido</span><span class="sxs-lookup"><span data-stu-id="62a47-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="62a47-p108">Una vez que haya agregado un elemento Web de búsqueda de contenido, puede refinar la búsqueda y devolver los elementos que desee. Para obtener instrucciones detalladas acerca de cómo hacer esto, vea la sección, *"Mostrar contenido mediante la configuración de una consulta avanzada en un elemento Web búsqueda de contenido"* en [configurar un elemento Web de búsqueda de contenido en SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="62a47-p108">Once you have added a Content Search Web Part, you can refine the search and return the items you want. For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="62a47-134">Crear y probar la herramienta de consulta</span><span class="sxs-lookup"><span data-stu-id="62a47-134">Query building and testing tool</span></span>

<span data-ttu-id="62a47-135">Para que una herramienta crear y probar las consultas complejas, consulte la [Herramienta de consulta de búsqueda](https://sp2013searchtool.codeplex.com/) en Codeplex.</span><span class="sxs-lookup"><span data-stu-id="62a47-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

