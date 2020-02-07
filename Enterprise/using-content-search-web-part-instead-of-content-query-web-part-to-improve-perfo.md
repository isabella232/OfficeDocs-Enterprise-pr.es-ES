---
title: Usar el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido para mejorar el rendimiento en SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/20/2015
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- SPO160
ms.assetid: e8ce6b72-745b-464a-85c7-cbf6eb53391b
description: En este artículo se describe cómo aumentar el rendimiento al reemplazar el elemento Web de consulta de contenido con el elemento Web de búsqueda de contenido en SharePoint Server 2013 y SharePoint Online.
ms.openlocfilehash: 16d8e976a96487752a78b91a783041448621a275
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843931"
---
# <a name="using-content-search-web-part-instead-of-content-query-web-part-to-improve-performance-in-sharepoint-online"></a><span data-ttu-id="cf734-103">Usar el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido para mejorar el rendimiento en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cf734-103">Using Content Search Web Part instead of Content Query Web Part to improve performance in SharePoint Online</span></span>

<span data-ttu-id="cf734-104">En este artículo se describe cómo aumentar el rendimiento al reemplazar el elemento Web de consulta de contenido con el elemento Web de búsqueda de contenido en SharePoint Server 2013 y SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="cf734-104">This article describes how to increase performance by replacing the Content Query Web Part with the Content Search Web Part in SharePoint Server 2013 and SharePoint Online.</span></span>
  
<span data-ttu-id="cf734-105">Una de las características nuevas más eficaces de SharePoint Server 2013 y SharePoint Online es el elemento Web de búsqueda de contenido (CSWP).</span><span class="sxs-lookup"><span data-stu-id="cf734-105">One of the most powerful new features of SharePoint Server 2013 and SharePoint Online is the Content Search Web Part (CSWP).</span></span> <span data-ttu-id="cf734-106">Este elemento Web usa el índice de búsqueda para recuperar rápidamente los resultados que se muestran al usuario.</span><span class="sxs-lookup"><span data-stu-id="cf734-106">This Web Part uses the search index to quickly retrieve results which are shown to the user.</span></span> <span data-ttu-id="cf734-107">Use el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido (CQWP) en las páginas para mejorar el rendimiento de los usuarios.</span><span class="sxs-lookup"><span data-stu-id="cf734-107">Use the Content Search Web Part instead of the Content Query Web Part (CQWP) in your pages to improve performance for your users.</span></span>
  
<span data-ttu-id="cf734-108">El uso de un elemento Web de búsqueda de contenido en un elemento Web de consulta de contenido casi siempre dará lugar a un rendimiento de carga de páginas significativamente mejor en SharePoint Online.</span><span class="sxs-lookup"><span data-stu-id="cf734-108">Using a Content Search Web Part over a Content Query Web Part will almost always result in significantly better page load performance on SharePoint Online.</span></span> <span data-ttu-id="cf734-109">Hay una configuración adicional para obtener la consulta correcta, pero las recompensas mejoran el rendimiento y los usuarios más contentos.</span><span class="sxs-lookup"><span data-stu-id="cf734-109">There is a little additional configuration to get the right query, but the rewards are improved performance and happier users.</span></span>
  
## <a name="comparing-the-performance-gain-you-get-from-using-content-search-web-part-instead-of-content-query-web-part"></a><span data-ttu-id="cf734-110">Comparación de la mejora de rendimiento que obtiene al usar el elemento Web de búsqueda de contenido en lugar del elemento Web de consulta de contenido</span><span class="sxs-lookup"><span data-stu-id="cf734-110">Comparing the performance gain you get from using Content Search Web Part instead of Content Query Web Part</span></span>

<span data-ttu-id="cf734-111">Los siguientes ejemplos muestran las mejoras de rendimiento relativas que puede recibir cuando usa un elemento Web de búsqueda de contenido en lugar de un elemento Web de consulta de contenido.</span><span class="sxs-lookup"><span data-stu-id="cf734-111">The following examples show the relative performance gains you may receive when you use a Content Search Web Part instead of a Content Query Web Part.</span></span> <span data-ttu-id="cf734-112">Los efectos son más obvios con una compleja estructura del sitio y consultas de contenido muy amplias.</span><span class="sxs-lookup"><span data-stu-id="cf734-112">The effects are more obvious with a complex site structure and very broad content queries.</span></span>
  
<span data-ttu-id="cf734-113">Este sitio de ejemplo tiene las siguientes características:</span><span class="sxs-lookup"><span data-stu-id="cf734-113">This example site has the following characteristics:</span></span>
  
- <span data-ttu-id="cf734-114">8 niveles de subsitios.</span><span class="sxs-lookup"><span data-stu-id="cf734-114">8 levels of subsites.</span></span>
    
- <span data-ttu-id="cf734-115">Listas con un tipo de contenido personalizado "fruta".</span><span class="sxs-lookup"><span data-stu-id="cf734-115">Lists using a custom "fruit" content type.</span></span>
    
- <span data-ttu-id="cf734-116">En el elemento Web, la consulta de contenido es amplia y devuelve todos los elementos con el tipo de contenido "fruta".</span><span class="sxs-lookup"><span data-stu-id="cf734-116">In the Web Part, the content query is broad, returning all items with the content type of "fruit".</span></span>
    
- <span data-ttu-id="cf734-117">En el ejemplo solo se usan 50 elementos en los 8 sitios.</span><span class="sxs-lookup"><span data-stu-id="cf734-117">The example only uses 50 items across the 8 sites.</span></span> <span data-ttu-id="cf734-118">Los efectos serán aún más pronunciados para los sitios con más contenido.</span><span class="sxs-lookup"><span data-stu-id="cf734-118">The effects will be even more pronounced for sites with more content.</span></span>
    
<span data-ttu-id="cf734-119">Esta es una captura de pantalla de los resultados del elemento Web consulta de contenido.</span><span class="sxs-lookup"><span data-stu-id="cf734-119">Here is a screen shot of the results of the Content Query Web Part.</span></span>
  
![Gráfico que muestra la consulta de contenido del elemento web](media/b3d41f20-dfe5-46ed-9c0a-31057e82de33.png)
  
<span data-ttu-id="cf734-121">En Internet Explorer, use la pestaña **red** de las herramientas de desarrollo F12 para ver los detalles del encabezado de respuesta.</span><span class="sxs-lookup"><span data-stu-id="cf734-121">In Internet Explorer, use the **Network** tab of the F12 developer tools to look at the details for the response header.</span></span> <span data-ttu-id="cf734-122">En la siguiente captura de pantalla, el valor de **SPRequestDuration** para esta carga de página es de 924 milisegundos.</span><span class="sxs-lookup"><span data-stu-id="cf734-122">In the following screen shot, the value for the **SPRequestDuration** for this page load is 924 milliseconds.</span></span> 
  
![Captura de pantalla que muestra la duración de la solicitud de 924](media/343571f2-a249-4de2-bc11-2cee93498aea.png)
  
 <span data-ttu-id="cf734-124">**SPRequestDuration** indica la cantidad de trabajo que se realiza en el servidor para preparar la página.</span><span class="sxs-lookup"><span data-stu-id="cf734-124">**SPRequestDuration** indicates the amount of work that is done on the server to prepare the page.</span></span> <span data-ttu-id="cf734-125">El cambio de contenido por elementos Web de consulta con contenido por elementos Web de búsqueda reduce considerablemente el tiempo que se tarda en representar la página.</span><span class="sxs-lookup"><span data-stu-id="cf734-125">Switching Content by Query Web Parts with Content by Search Web Parts dramatically reduces the time it takes to render the page.</span></span> <span data-ttu-id="cf734-126">Por el contrario, una página con un elemento Web de búsqueda de contenido equivalente que devuelve el mismo número de resultados tiene un valor **SPRequestDuration** de 106 milisegundos, tal como se muestra en esta captura de pantalla:</span><span class="sxs-lookup"><span data-stu-id="cf734-126">By contrast, a page with an equivalent Content Search Web Part, returning the same number of results has an **SPRequestDuration** value of 106 milliseconds as shown in this screen shot:</span></span> 
  
![Captura de pantalla que muestra la duración de la solicitud de 106](media/b46387ac-660d-4e5e-a11c-cc430e912962.png)
  
## <a name="adding-a-content-search-web-part-in-sharepoint-online"></a><span data-ttu-id="cf734-128">Adición de un elemento Web de búsqueda de contenido en SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="cf734-128">Adding a Content Search Web Part in SharePoint Online</span></span>

<span data-ttu-id="cf734-129">Agregar un elemento Web de búsqueda de contenido es muy similar a un elemento Web de consulta de contenido normal.</span><span class="sxs-lookup"><span data-stu-id="cf734-129">Adding a Content Search Web Part is very similar to a regular Content Query Web Part.</span></span> <span data-ttu-id="cf734-130">Vea la sección *sobre cómo agregar un elemento Web de búsqueda de contenido* en [configurar un elemento Web de búsqueda de contenido en SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="cf734-130">See the section  *"Add a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="creating-the-right-search-query-for-your-content-search-web-part"></a><span data-ttu-id="cf734-131">Crear la consulta de búsqueda correcta para el elemento Web de búsqueda de contenido</span><span class="sxs-lookup"><span data-stu-id="cf734-131">Creating the right search query for your Content Search Web Part</span></span>

<span data-ttu-id="cf734-132">Una vez que haya agregado un elemento Web de búsqueda de contenido, puede refinar la búsqueda y devolver los elementos que desee.</span><span class="sxs-lookup"><span data-stu-id="cf734-132">Once you have added a Content Search Web Part, you can refine the search and return the items you want.</span></span> <span data-ttu-id="cf734-133">Para obtener instrucciones detalladas sobre cómo hacerlo, vea la sección *"Mostrar contenido mediante la configuración de una consulta avanzada en un elemento Web de búsqueda de contenido"* en [configurar un elemento Web de búsqueda de contenido en SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span><span class="sxs-lookup"><span data-stu-id="cf734-133">For detailed instructions on how to do this, see the section,  *"Display content by configuring an advanced query in a Content Search Web Part"*  in [Configure a Content Search Web Part in SharePoint](https://support.office.com/article/Configure-a-Content-Search-Web-Part-in-SharePoint-0dc16de1-dbe4-462b-babb-bf8338c36c9a).</span></span>
  
## <a name="query-building-and-testing-tool"></a><span data-ttu-id="cf734-134">Herramienta de creación de consultas y pruebas</span><span class="sxs-lookup"><span data-stu-id="cf734-134">Query building and testing tool</span></span>

<span data-ttu-id="cf734-135">Para obtener una herramienta para compilar y probar consultas complejas, vea la [herramienta de consulta de búsqueda](https://sp2013searchtool.codeplex.com/) en Codeplex.</span><span class="sxs-lookup"><span data-stu-id="cf734-135">For a tool to build and test complex queries, see the [Search Query Tool](https://sp2013searchtool.codeplex.com/) on Codeplex.</span></span> 
  

