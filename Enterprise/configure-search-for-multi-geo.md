---
title: Configurar búsqueda de OneDrive de negocios Multi-Geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtenga información acerca de cómo configurar la búsqueda en un entorno multi-geo.
ms.openlocfilehash: 5aa1e9eb189e00dbed8f575e88046b661341bf52
ms.sourcegitcommit: 21cc62118b78b76d16ef12e2c3eff2c0c789e3d0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="5ac39-103">Configurar búsqueda de OneDrive de negocios Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="5ac39-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="5ac39-104">En un entorno Multi-Geo SharePoint Online (SPO), una organización puede tener un arrendatario de Office 365, pero almacenar su contenido de SharePoint en varias ubicaciones geográficas - una ubicación central y una o más ubicaciones geo de satélite.</span><span class="sxs-lookup"><span data-stu-id="5ac39-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="5ac39-p101">Cada ubicación geográfica tiene su propio centro de búsqueda e índices de búsqueda. Cuando un usuario realiza una búsqueda, la consulta se colocadas en abanico para todos los índices y se combinan los resultados devueltos.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="5ac39-p102">Por ejemplo, puede buscar un usuario en una ubicación geográfica para el contenido almacenado en otra ubicación geográfica, o contenido en un sitio de SharePoint que está restringido a una ubicación geográfica diferente. Si el usuario tiene acceso a este contenido, la búsqueda mostrará el resultado.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="5ac39-109">¿En un entorno Multi-Geo que buscar trabajo de los clientes?</span><span class="sxs-lookup"><span data-stu-id="5ac39-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="5ac39-110">Estos clientes pueden devolver resultados desde todas las ubicaciones de geo:</span><span class="sxs-lookup"><span data-stu-id="5ac39-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="5ac39-111">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="5ac39-111">OneDrive for Business</span></span>

-   <span data-ttu-id="5ac39-112">Delve</span><span class="sxs-lookup"><span data-stu-id="5ac39-112">Delve</span></span>

-   <span data-ttu-id="5ac39-113">La página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="5ac39-113">The SharePoint home page</span></span>

-   <span data-ttu-id="5ac39-114">El centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="5ac39-114">The Search Center</span></span>

-   <span data-ttu-id="5ac39-115">Aplicaciones de búsqueda personalizadas que utilizan la API de búsqueda de SharePoint</span><span class="sxs-lookup"><span data-stu-id="5ac39-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="5ac39-116">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="5ac39-116">OneDrive for Business</span></span>

<span data-ttu-id="5ac39-117">Tan pronto como se ha configurado el entorno Multi-Geo, los usuarios que busque en OneDrive Obtén resultados de todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="5ac39-118">Delve</span><span class="sxs-lookup"><span data-stu-id="5ac39-118">Delve</span></span>

<span data-ttu-id="5ac39-119">Tan pronto como se ha configurado el entorno Multi-Geo, los usuarios que buscar en Delve Obtén resultados de todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="5ac39-p103">La fuente de Delve y la tarjeta de perfil sólo mostrar vistas previas de archivos que se almacenan en la ubicación **central** . Para los archivos que se almacenan en ubicaciones de satélite geo, el icono del tipo de archivo se muestra en su lugar.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="5ac39-122">La página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="5ac39-122">The SharePoint home page</span></span>

<span data-ttu-id="5ac39-p104">Tan pronto como se ha configurado el entorno Multi-Geo, los usuarios verán noticias, sitios recientes y seguidos desde varias ubicaciones geo en su página de inicio de SharePoint. Si utiliza el cuadro de búsqueda en la página principal de SharePoint, obtendrán resultados combinados desde varias ubicaciones geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="5ac39-125">El centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="5ac39-125">The Search Center</span></span>

<span data-ttu-id="5ac39-p105">Después el Multi-Geo entorno se ha configurado, cada centro de búsqueda continúa para mostrar únicamente los resultados de su propia ubicación geográfica. Administradores deben [cambiar la configuración de cada centro de búsqueda](#_Set_up_a_1) para obtener resultados de todas las ubicaciones de geo. Posteriormente, los usuarios que en el centro de búsqueda de búsqueda Obtén resultados desde todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="5ac39-129">Aplicaciones de búsqueda personalizadas</span><span class="sxs-lookup"><span data-stu-id="5ac39-129">Custom search applications</span></span>

<span data-ttu-id="5ac39-p106">Como de costumbre, aplicaciones de búsqueda personalizadas interactúan con los índices de búsqueda utilizando las API existentes de resto de búsqueda de SharePoint. Para obtener resultados de todas o algunas ubicaciones geo, la aplicación debe [llamar a la API e incluir los nuevos parámetros de consulta de Multi-Geo](#_Get_custom_search) en la solicitud. Esto desencadena un ventilador fuera de la consulta a todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="5ac39-133">¿Qué es diferente acerca de búsqueda en un entorno Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="5ac39-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="5ac39-134">Algunas características de búsqueda, es posible que esté familiarizado con, funcionan de forma diferente en un entorno Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5ac39-135"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="5ac39-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="5ac39-136"><strong>¿Cómo funciona</strong></span><span class="sxs-lookup"><span data-stu-id="5ac39-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="5ac39-137"><strong>Solución alternativa</strong></span><span class="sxs-lookup"><span data-stu-id="5ac39-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="5ac39-138">Resultados de la promoción</span><span class="sxs-lookup"><span data-stu-id="5ac39-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="5ac39-p107">Puede crear reglas de consulta con resultados promocionadas en distintos niveles: para el inquilino todo, para una colección de sitios o para un sitio. En un entorno Multi-Geo, definir resultados promovidos en el nivel de <strong>inquilinos</strong> si desea promover los resultados a los centros de búsqueda en <strong>todas las</strong> ubicaciones de geo. Si usted <strong>sólo</strong> desea promover los resultados en el centro de búsqueda que está en la ubicación geográfica de la colección de sitios o el sitio, definir los resultados en el nivel de <strong>colección de sitios</strong> o <strong>sitio</strong> .</span><span class="sxs-lookup"><span data-stu-id="5ac39-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="5ac39-142">Si no necesita diferentes resultados promovidos por ubicación geográfica, por ejemplo diferentes reglas para viajar, recomendamos definir promover los resultados en el nivel de inquilinos.</span><span class="sxs-lookup"><span data-stu-id="5ac39-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5ac39-143">Refinadores de búsqueda</span><span class="sxs-lookup"><span data-stu-id="5ac39-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="5ac39-p108">La búsqueda devuelve los refinadores de todas las ubicaciones geo de un arrendatario y luego los agrega. La agregación es un mayor esfuerzo, lo que significa que los recuentos de refinador podrían no ser exactos al 100%. Para la mayoría de los escenarios controlados por la búsqueda de esta precisión es suficiente.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="5ac39-147">Para aplicaciones orientadas a la búsqueda que dependen de su integridad refinador, consultar cada ubicación geográfica independientemente sin necesidad de utilizar múltiples Geo fan-out.</span><span class="sxs-lookup"><span data-stu-id="5ac39-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="5ac39-148">Multi-Geo búsqueda no es compatible con la creación de depósitos dinámico para los refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="5ac39-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="5ac39-149">Utilice el <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">parámetro "Discretize"</a> para los refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="5ac39-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5ac39-150">Identificadores de documento</span><span class="sxs-lookup"><span data-stu-id="5ac39-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="5ac39-151">Si está desarrollando una aplicación controlada por búsqueda que depende de ID documento, observe que identificadores de documento en un entorno Multi-Geo no son únicos en todas las ubicaciones de geo, son únicas para cada ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="5ac39-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="5ac39-p109">Hemos agregado una columna que identifica la ubicación geográfica. Utilice esta columna para lograr la unicidad. Esta columna se denomina "GeoLocationSource".</span><span class="sxs-lookup"><span data-stu-id="5ac39-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5ac39-155">Número de resultados</span><span class="sxs-lookup"><span data-stu-id="5ac39-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="5ac39-156">La página de resultados de búsqueda muestra resultados combinados de las ubicaciones de geo, pero no es posible más allá de 500 resultados de página.</span><span class="sxs-lookup"><span data-stu-id="5ac39-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="5ac39-157">¿Qué no se admite para la búsqueda en un entorno Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="5ac39-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="5ac39-158">Algunas de las características de búsqueda, es posible que esté familiarizado con, no se admiten en un entorno Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5ac39-159"><strong>Función de búsqueda</strong></span><span class="sxs-lookup"><span data-stu-id="5ac39-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="5ac39-160"><strong>Nota</strong></span><span class="sxs-lookup"><span data-stu-id="5ac39-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="5ac39-161">Autenticación sólo de la aplicación</span><span class="sxs-lookup"><span data-stu-id="5ac39-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="5ac39-162">La autenticación sólo de la aplicación (acceso privilegiado de servicios) no es compatible con Multi-Geo búsqueda.</span><span class="sxs-lookup"><span data-stu-id="5ac39-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5ac39-163">Usuarios invitados</span><span class="sxs-lookup"><span data-stu-id="5ac39-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="5ac39-164">Sólo los usuarios invitados Obtén resultados desde la ubicación geográfica que está buscando desde.</span><span class="sxs-lookup"><span data-stu-id="5ac39-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="5ac39-165">¿Cómo funciona la búsqueda de hace en un entorno Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="5ac39-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="5ac39-166">**Todos** los clientes de búsqueda utilizan las API existentes de resto de búsqueda de SharePoint para interactuar con los índices de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="5ac39-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. <span data-ttu-id="5ac39-167">Un cliente de búsqueda llama el extremo del resto de búsqueda con la propiedad de consulta EnableMultiGeoSearch = true.</span><span class="sxs-lookup"><span data-stu-id="5ac39-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="5ac39-168">La consulta se envía a todas las ubicaciones de geo de los inquilinos.</span><span class="sxs-lookup"><span data-stu-id="5ac39-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="5ac39-169">Resultados de la búsqueda de cada ubicación geográfica se combinan y clasificados.</span><span class="sxs-lookup"><span data-stu-id="5ac39-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="5ac39-170">El cliente obtiene los resultados de la búsqueda unificada.</span><span class="sxs-lookup"><span data-stu-id="5ac39-170">The client gets unified search results.</span></span>



<span data-ttu-id="5ac39-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Observe que no combinar los resultados de búsqueda hasta que hemos recibido resultados de todas las ubicaciones de geo. Esto significa que las búsquedas Multi-Geo tienen latencia adicional en comparación con las búsquedas en un entorno con geo sólo una ubicación.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="5ac39-173">Obtener un centro de búsqueda para mostrar los resultados de todas las ubicaciones de geo</span><span class="sxs-lookup"><span data-stu-id="5ac39-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="5ac39-174">Cada centro de búsqueda tiene varias líneas verticales y tendrá que configurar individualmente cada vertical.</span><span class="sxs-lookup"><span data-stu-id="5ac39-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="5ac39-175">Asegúrese de que realiza estos pasos con una cuenta que tenga permiso para editar la página de resultados de la búsqueda y el elemento Web de resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="5ac39-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="5ac39-176">Desplácese a la página de resultados de la búsqueda (consulte las páginas de resultados de la [lista](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de búsqueda)</span><span class="sxs-lookup"><span data-stu-id="5ac39-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="5ac39-p111">Seleccione vertical para configurar, haga clic en el icono de engranaje de **configuración** en la esquina superior derecha y, a continuación, haga clic en **Editar página**. La página de resultados de búsqueda se abre en modo de edición.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo_image2.png)
1.  <span data-ttu-id="5ac39-p112">En el elemento Web de resultados de búsqueda, mueva el puntero a la parte superior, la esquina derecha del elemento Web, haga clic en la flecha y, a continuación, haga clic en **Modificar elemento Web** en el menú. Se abre el panel de herramientas elemento Web resultados de la búsqueda en la cinta de opciones en la parte superior derecha de la página.![](media/configure-search-for-multi-geo_image3.png)</span><span class="sxs-lookup"><span data-stu-id="5ac39-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo_image3.png)</span></span>

1.  <span data-ttu-id="5ac39-181">En el panel de herramientas elemento Web, en la sección de **configuración** , en **configuración de control de resultados**, seleccione **Multi-Geo mostrar resultados** para obtener el elemento de Web de resultados de búsqueda para mostrar los resultados de todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="5ac39-182">Haga clic en **Aceptar** para guardar los cambios y cerrar el panel de herramientas elemento Web.</span><span class="sxs-lookup"><span data-stu-id="5ac39-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="5ac39-183">Compruebe los cambios realizados en el elemento Web de resultados de la búsqueda haciendo clic **En verificación** en la ficha de página del menú principal.</span><span class="sxs-lookup"><span data-stu-id="5ac39-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="5ac39-184">Publicar los cambios mediante el vínculo proporcionado en la nota en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="5ac39-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="5ac39-185">Obtener aplicaciones de búsqueda personalizadas para mostrar los resultados de todas o algunas ubicaciones geo</span><span class="sxs-lookup"><span data-stu-id="5ac39-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="5ac39-p113">Aplicaciones de búsqueda personalizadas Obtén resultados de ubicaciones geo todas o algunas, especificando parámetros de consulta con la solicitud de la API de REST de búsqueda de SharePoint. Dependiendo de los parámetros de la consulta, la consulta se abanico a todas las ubicaciones de geo o en algunas ubicaciones geo. Por ejemplo, si sólo necesita un subconjunto de ubicaciones geo para buscar la información pertinente de la consulta, puede controlar el fan-out a éstas. Si la solicitud es correcta, la API de REST de SharePoint Search devuelve datos de respuesta.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="5ac39-190">Parámetros de consulta</span><span class="sxs-lookup"><span data-stu-id="5ac39-190">Query parameters</span></span>

<span data-ttu-id="5ac39-p114">EnableMultiGeoSearch - esto es un valor booleano que especifica si la consulta será abanico a los índices de otras ubicaciones geo del inquilino Multi-Geo. Se establece en **true** para fan-out de la consulta; **false** para no fan-out de la consulta. El valor predeterminado es **false**. Si no incluye este parámetro, la consulta es **no** abanico a otras ubicaciones geo. Si utiliza el parámetro en un entorno que no sea Multi-Geo, se omite el parámetro.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="5ac39-p115">TipoCliente - se trata de una cadena. Escriba un nombre de cliente única para cada aplicación de búsqueda. Si no incluye este parámetro, la consulta es **no** abanico a otras ubicaciones geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="5ac39-p116">MultiGeoSearchConfiguration: ésta es una lista opcional de qué geo ubicaciones en el Multi-Geo inquilinos para la consulta abanico para cuando **EnableMultiGeoSearch** es **true**. Si no incluye este parámetro, o déjelo en blanco, la consulta se abanico a todas las ubicaciones de geo. Para cada ubicación geográfica, escriba lo siguiente en formato JSON:</span><span class="sxs-lookup"><span data-stu-id="5ac39-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5ac39-202">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ac39-202">Item</span></span></th>
<th align="left"><span data-ttu-id="5ac39-203">Descripción</span><span class="sxs-lookup"><span data-stu-id="5ac39-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="5ac39-204">Ubicación_datos</span><span class="sxs-lookup"><span data-stu-id="5ac39-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="5ac39-205">La ubicación geográfica, por ejemplo NAM.</span><span class="sxs-lookup"><span data-stu-id="5ac39-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5ac39-206">Extremo</span><span class="sxs-lookup"><span data-stu-id="5ac39-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="5ac39-207">El extremo al que conectarse, por ejemplohttps://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="5ac39-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="5ac39-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="5ac39-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="5ac39-209">El GUID del origen del resultado, por ejemplo B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="5ac39-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="5ac39-p117">Si se omite Ubicación_datos o extremo o un Ubicación_datos está duplicado, se produce un error en la solicitud. [Puede obtener información acerca del extremo de ubicaciones de geo de los inquilinos mediante Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="5ac39-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="5ac39-212">Datos de respuesta</span><span class="sxs-lookup"><span data-stu-id="5ac39-212">Response data</span></span>

<span data-ttu-id="5ac39-p118">MultiGeoSearchStatus: se trata de una propiedad que devuelve la API de búsqueda de SharePoint en respuesta a una solicitud. El valor de la propiedad es una cadena y proporciona la siguiente información acerca de los resultados que devuelve la API de búsqueda de SharePoint:</span><span class="sxs-lookup"><span data-stu-id="5ac39-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5ac39-215">Valor</span><span class="sxs-lookup"><span data-stu-id="5ac39-215">Value</span></span></th>
<th align="left"><span data-ttu-id="5ac39-216">Descripción</span><span class="sxs-lookup"><span data-stu-id="5ac39-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="5ac39-217">Total</span><span class="sxs-lookup"><span data-stu-id="5ac39-217">Full</span></span></td>
<td align="left"><span data-ttu-id="5ac39-218">Resultados completos de <strong>todas</strong> las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="5ac39-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="5ac39-219">Parcial</span><span class="sxs-lookup"><span data-stu-id="5ac39-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="5ac39-p119">Resultados parciales de una o más ubicaciones de geo. Los resultados son incompletos debido a un error transitorio.</span><span class="sxs-lookup"><span data-stu-id="5ac39-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="5ac39-222">Consulta con el servicio REST</span><span class="sxs-lookup"><span data-stu-id="5ac39-222">Query using the REST service</span></span>

<span data-ttu-id="5ac39-p120">Una solicitud GET, especifica los parámetros de consulta en la dirección URL. Con una solicitud POST, pase los parámetros de consulta en el cuerpo en formato JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="5ac39-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="5ac39-225">Encabezados de solicitud</span><span class="sxs-lookup"><span data-stu-id="5ac39-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="5ac39-226">Nombre</span><span class="sxs-lookup"><span data-stu-id="5ac39-226">Name</span></span></th>
<th align="left"><span data-ttu-id="5ac39-227">Valor</span><span class="sxs-lookup"><span data-stu-id="5ac39-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="5ac39-228">Tipo de contenido</span><span class="sxs-lookup"><span data-stu-id="5ac39-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="5ac39-229">Application/json; odata = verbose</span><span class="sxs-lookup"><span data-stu-id="5ac39-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="5ac39-230">Ejemplo de solicitud GET que es abanico a **todas las** ubicaciones de geo</span><span class="sxs-lookup"><span data-stu-id="5ac39-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="5ac39-231">https:// \<inquilinos\>/\_api, búsqueda/query?querytext = 'sharepoint' & Propiedades = 'EnableMultiGeoSearch:true' & TipoCliente =' Mi\_cliente\_id'</span><span class="sxs-lookup"><span data-stu-id="5ac39-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="5ac39-232">Ejemplo de solicitud GET para fan-out en **algunas** ubicaciones geo</span><span class="sxs-lookup"><span data-stu-id="5ac39-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="5ac39-233">https:// <tenant>/_api/search/query?querytext = 'sitio' & TipoCliente = & Propiedades de 'my_client_id' ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{Ubicación_datos\:"NAM"\,extremo\:"https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{Ubicación_datos\:"Puede"\,extremo\:" https\://contosoCAN.sharepoint-df.com "}]'</span><span class="sxs-lookup"><span data-stu-id="5ac39-233">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="5ac39-234">Ejemplo de solicitud POST que es abanico a **todas las** ubicaciones de geo</span><span class="sxs-lookup"><span data-stu-id="5ac39-234">Sample POST request that’s fanned out to **all** geo locations</span></span>

    {
        "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="5ac39-235">Ejemplo de solicitud POST que es abanico a **algunas** ubicaciones de geo</span><span class="sxs-lookup"><span data-stu-id="5ac39-235">Sample POST request that’s fanned out to **some** geo locations</span></span>


    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }

### <a name="query-using-csom"></a><span data-ttu-id="5ac39-236">Consulta con OMSC</span><span class="sxs-lookup"><span data-stu-id="5ac39-236">Query using CSOM</span></span>

<span data-ttu-id="5ac39-237">Ésta es una consulta de OMSC de muestra es abanico a **todas las** ubicaciones de geo:</span><span class="sxs-lookup"><span data-stu-id="5ac39-237">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

