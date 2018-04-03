---
title: Administrar un entorno multi-geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtenga información acerca de cómo configurar la búsqueda en un entorno multi-geo.
ms.openlocfilehash: 0c5c8eaa981c31151c70507da54587a7269f98f5
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="dfe92-103">Configurar búsqueda de OneDrive de negocios Multi-Geo</span><span class="sxs-lookup"><span data-stu-id="dfe92-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="dfe92-104">En un entorno Multi-Geo SharePoint Online (SPO), una organización puede tener un arrendatario de Office 365, pero almacenar su contenido de SharePoint en varias ubicaciones geográficas - una ubicación central y una o más ubicaciones geo de satélite.</span><span class="sxs-lookup"><span data-stu-id="dfe92-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="dfe92-p101">Cada ubicación geográfica tiene su propio centro de búsqueda e índices de búsqueda. Cuando un usuario realiza una búsqueda, la consulta se colocadas en abanico para todos los índices y se combinan los resultados devueltos.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="dfe92-p102">Por ejemplo, puede buscar un usuario en una ubicación geográfica para el contenido almacenado en otra ubicación geográfica, o contenido en un sitio de SharePoint que está restringido a una ubicación geográfica diferente. Si el usuario tiene acceso a este contenido, la búsqueda mostrará el resultado.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="dfe92-109">¿En un entorno Multi-Geo que buscar trabajo de los clientes?</span><span class="sxs-lookup"><span data-stu-id="dfe92-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="dfe92-110">Estos clientes pueden devolver resultados desde todas las ubicaciones de geo:</span><span class="sxs-lookup"><span data-stu-id="dfe92-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="dfe92-111">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="dfe92-111">OneDrive for Business</span></span>

-   <span data-ttu-id="dfe92-112">Delve</span><span class="sxs-lookup"><span data-stu-id="dfe92-112">Delve</span></span>

-   <span data-ttu-id="dfe92-113">La página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="dfe92-113">The SharePoint home page</span></span>

-   <span data-ttu-id="dfe92-114">El centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="dfe92-114">The Search Center</span></span>

-   <span data-ttu-id="dfe92-115">Aplicaciones de búsqueda personalizadas que utilizan la API de búsqueda de SharePoint</span><span class="sxs-lookup"><span data-stu-id="dfe92-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="dfe92-116">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="dfe92-116">OneDrive for Business</span></span>

<span data-ttu-id="dfe92-117">Tan pronto como se ha configurado el entorno Multi-Geo, los usuarios que busque en OneDrive Obtén resultados de todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="dfe92-118">Delve</span><span class="sxs-lookup"><span data-stu-id="dfe92-118">Delve</span></span>

<span data-ttu-id="dfe92-119">Tan pronto como se ha configurado el entorno Multi-Geo, los usuarios que buscar en Delve Obtén resultados de todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="dfe92-p103">La fuente de Delve y la tarjeta de perfil sólo mostrar vistas previas de archivos que se almacenan en la ubicación **central** . Para los archivos que se almacenan en ubicaciones de satélite geo, el icono del tipo de archivo se muestra en su lugar.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="dfe92-122">La página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="dfe92-122">The SharePoint home page</span></span>

<span data-ttu-id="dfe92-p104">Tan pronto como se ha configurado el entorno Multi-Geo, los usuarios verán noticias, sitios recientes y seguidos desde varias ubicaciones geo en su página de inicio de SharePoint. Si utilizan el cuadro de búsqueda en la página principal de SharePoint, sólo obtener resultados desde la ubicación geográfica SPHome índice de búsqueda se encuentra en.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use search box on the SharePoint home page, they only get results from the geo location SPHome search index is located in.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="dfe92-125">El centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="dfe92-125">The Search Center</span></span>

<span data-ttu-id="dfe92-p105">Después el Multi-Geo entorno se ha configurado, cada centro de búsqueda continúa para mostrar únicamente los resultados de su propia ubicación geográfica. Administradores deben [cambiar la configuración de cada centro de búsqueda](#_Set_up_a_1) para obtener resultados de todas las ubicaciones de geo. Posteriormente, los usuarios que en el centro de búsqueda de búsqueda Obtén resultados desde todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="dfe92-129">Aplicaciones de búsqueda personalizadas</span><span class="sxs-lookup"><span data-stu-id="dfe92-129">Custom search applications</span></span>

<span data-ttu-id="dfe92-p106">Como de costumbre, aplicaciones de búsqueda personalizadas interactúan con los índices de búsqueda utilizando las API existentes de resto de búsqueda de SharePoint. Para obtener resultados de todas o algunas ubicaciones geo, la aplicación debe [llamar a la API e incluir los nuevos parámetros de consulta de Multi-Geo](#_Get_custom_search) en la solicitud. Esto desencadena un ventilador fuera de la consulta a todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

### <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="dfe92-133">¿Qué es diferente acerca de búsqueda en un entorno Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="dfe92-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="dfe92-134">Algunas características de búsqueda, es posible que esté familiarizado con, funcionan de forma diferente en un entorno Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dfe92-135"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="dfe92-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="dfe92-136"><strong>¿Cómo funciona</strong></span><span class="sxs-lookup"><span data-stu-id="dfe92-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="dfe92-137"><strong>Solución alternativa</strong></span><span class="sxs-lookup"><span data-stu-id="dfe92-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="dfe92-138">Resultados de la promoción</span><span class="sxs-lookup"><span data-stu-id="dfe92-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="dfe92-p107">Puede crear reglas de consulta con resultados promocionadas en distintos niveles: para el inquilino todo, para una colección de sitios o para un sitio. En un entorno Multi-Geo, definir resultados promovidos en el nivel de <strong>inquilinos</strong> si desea promover los resultados a los centros de búsqueda en <strong>todas las</strong> ubicaciones de geo. Si usted <strong>sólo</strong> desea promover los resultados en el centro de búsqueda que está en la ubicación geográfica de la colección de sitios o el sitio, definir los resultados en el nivel de <strong>colección de sitios</strong> o <strong>sitio</strong> .</span><span class="sxs-lookup"><span data-stu-id="dfe92-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="dfe92-142">Si no necesita diferentes resultados promovidos por ubicación geográfica, por ejemplo diferentes reglas para viajar, recomendamos definir promover los resultados en el nivel de inquilinos.</span><span class="sxs-lookup"><span data-stu-id="dfe92-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dfe92-143">Refinadores de búsqueda</span><span class="sxs-lookup"><span data-stu-id="dfe92-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="dfe92-p108">La búsqueda devuelve los refinadores de todas las ubicaciones geo de un arrendatario y luego los agrega. La agregación es un mayor esfuerzo, lo que significa que los recuentos de refinador podrían no ser exactos al 100%. Para la mayoría de los escenarios controlados por la búsqueda de esta precisión es suficiente.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient.</span></span></td>
<td align="left"><span data-ttu-id="dfe92-147">Para aplicaciones orientadas a la búsqueda que dependen de su integridad refinador, consultar cada ubicación geográfica independientemente sin necesidad de utilizar múltiples Geo fan-out.</span><span class="sxs-lookup"><span data-stu-id="dfe92-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="dfe92-148">Multi-Geo búsqueda no es compatible con la creación de depósitos dinámico para los refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="dfe92-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="dfe92-149">Utilice el <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">parámetro "Discretize"</a> para los refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="dfe92-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dfe92-150">Identificadores de documento</span><span class="sxs-lookup"><span data-stu-id="dfe92-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="dfe92-151">Si está desarrollando una aplicación controlada por búsqueda que depende de ID documento, observe que identificadores de documento en un entorno Multi-Geo no son únicos en todas las ubicaciones de geo, son únicas para cada ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="dfe92-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="dfe92-p109">Hemos agregado una columna que identifica la ubicación geográfica. Utilice esta columna para lograr la unicidad. Esta columna se denomina "GeoLocationSource".</span><span class="sxs-lookup"><span data-stu-id="dfe92-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="dfe92-155">Número de resultados</span><span class="sxs-lookup"><span data-stu-id="dfe92-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="dfe92-156">La página de resultados de búsqueda muestra resultados combinados de las ubicaciones de geo, pero no es posible más allá de 500 resultados de página.</span><span class="sxs-lookup"><span data-stu-id="dfe92-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

### <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="dfe92-157">¿Qué no se admite para la búsqueda en un entorno Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="dfe92-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="dfe92-158">Algunas de las características de búsqueda, es posible que esté familiarizado con, no se admiten en un entorno Multi-Geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dfe92-159"><strong>Función de búsqueda</strong></span><span class="sxs-lookup"><span data-stu-id="dfe92-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="dfe92-160"><strong>Nota</strong></span><span class="sxs-lookup"><span data-stu-id="dfe92-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="dfe92-161">Autenticación sólo de la aplicación</span><span class="sxs-lookup"><span data-stu-id="dfe92-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="dfe92-162">La autenticación sólo de la aplicación (acceso privilegiado de servicios) no es compatible con Multi-Geo búsqueda.</span><span class="sxs-lookup"><span data-stu-id="dfe92-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dfe92-163">Usuarios invitados</span><span class="sxs-lookup"><span data-stu-id="dfe92-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="dfe92-164">Sólo los usuarios invitados Obtén resultados desde la ubicación geográfica que está buscando desde.</span><span class="sxs-lookup"><span data-stu-id="dfe92-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

### <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="dfe92-165">¿Cómo funciona la búsqueda de hace en un entorno Multi-Geo?</span><span class="sxs-lookup"><span data-stu-id="dfe92-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="dfe92-166">**Todos** los clientes de búsqueda utilizan las API existentes de resto de búsqueda de SharePoint para interactuar con los índices de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="dfe92-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><p><img src="media/configure-search-for-multi-geo_image1.png" /></p>
<p><span data-ttu-id="dfe92-167">Figura 1: Búsqueda en un arrendatario con tres ubicaciones de geo</span><span class="sxs-lookup"><span data-stu-id="dfe92-167">Figure 1: Searching across a tenant with three geo locations</span></span></p></th>
<th align="left"><p><span data-ttu-id="dfe92-168">Cliente de búsqueda llama el extremo del resto de búsqueda con la propiedad de consulta EnableMultiGeoSearch = true.</span><span class="sxs-lookup"><span data-stu-id="dfe92-168">Search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span></p>
<p><span data-ttu-id="dfe92-169">La consulta se envía a todas las ubicaciones de geo de los inquilinos.</span><span class="sxs-lookup"><span data-stu-id="dfe92-169">The query is sent to all geo locations in the tenant.</span></span></p>
<p><span data-ttu-id="dfe92-170">Resultados de la búsqueda de cada ubicación geográfica se combinan y clasificados.</span><span class="sxs-lookup"><span data-stu-id="dfe92-170">Search results from each geo location are merged and ranked.</span></span></p>
<p><span data-ttu-id="dfe92-171">El cliente obtiene los resultados de la búsqueda unificada.</span><span class="sxs-lookup"><span data-stu-id="dfe92-171">Client gets unified search results.</span></span></p></th>
</tr>
</thead>
<tbody>
</tbody>
</table><span data-ttu-id="dfe92-p110">

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Multi-Geo búsqueda funciona llamando a cada extremo de la búsqueda en cada geos. Las solicitudes al producto afectado remoto se realizan en paralelo, pero a combinación ocurra, esperamos que la pierna más lenta responder antes de que podemos hacer la combinación. Esto implica multi-geo agregar latencia adicional a la experiencia de búsqueda.  <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span> 
### Obtener un centro de búsqueda para mostrar los resultados de todas las ubicaciones de geo</span><span class="sxs-lookup"><span data-stu-id="dfe92-p110">

<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Multi-Geo Search works by calling each search endpoint in each geos. The requests to remote goes are performed in parallel, but to merging to happen, we wait for the slowest leg to reply before we can do the merging. This implies multi-geo add additional latency to the search experience.  <span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
### Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="dfe92-176">Cada centro de búsqueda tiene varias líneas verticales y tendrá que configurar individualmente cada vertical.</span><span class="sxs-lookup"><span data-stu-id="dfe92-176">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="dfe92-177">Asegúrese de que realiza estos pasos con una cuenta que tenga permiso para editar la página de resultados de la búsqueda y el elemento Web de resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="dfe92-177">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="dfe92-178">Desplácese a la página de resultados de la búsqueda (consulte las páginas de resultados de la [lista](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de búsqueda)</span><span class="sxs-lookup"><span data-stu-id="dfe92-178">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="dfe92-179">Seleccione vertical para configurar, haga clic en el icono de engranaje de **configuración** en la esquina superior derecha y, a continuación, haga clic en **Editar página**.</span><span class="sxs-lookup"><span data-stu-id="dfe92-179">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**.</span></span>

> ![](media/configure-search-for-multi-geo_image2.png)
>
> <span data-ttu-id="dfe92-180">La página de resultados de búsqueda se abre en modo de edición.</span><span class="sxs-lookup"><span data-stu-id="dfe92-180">The search results page opens in Edit mode.</span></span>

1.  <span data-ttu-id="dfe92-181">En el elemento Web de resultados de búsqueda, mueva el puntero a la parte superior, la esquina derecha del elemento Web, haga clic en la flecha y, a continuación, haga clic en **Modificar elemento Web** en el menú.</span><span class="sxs-lookup"><span data-stu-id="dfe92-181">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu.</span></span> ![](media/configure-search-for-multi-geo_image3.png)

> <span data-ttu-id="dfe92-182">Se abre el panel de herramientas elemento Web resultados de la búsqueda en la cinta de opciones en la parte superior derecha de la página.</span><span class="sxs-lookup"><span data-stu-id="dfe92-182">The Search Results Web Part tool pane opens under the ribbon in the top right of the page.</span></span>

1.  <span data-ttu-id="dfe92-183">En el panel de herramientas elemento Web, en la sección de **configuración** , en **configuración de control de resultados**, seleccione **Multi-Geo mostrar resultados** para obtener el elemento de Web de resultados de búsqueda para mostrar los resultados de todas las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-183">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="dfe92-184">Haga clic en **Aceptar** para guardar los cambios y cerrar el panel de herramientas elemento Web.</span><span class="sxs-lookup"><span data-stu-id="dfe92-184">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="dfe92-185">Compruebe los cambios realizados en el elemento Web de resultados de la búsqueda haciendo clic **En verificación** en la ficha de página del menú principal.</span><span class="sxs-lookup"><span data-stu-id="dfe92-185">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="dfe92-186">Publicar los cambios mediante el vínculo proporcionado en la nota en la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="dfe92-186">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
### <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="dfe92-187">Obtener aplicaciones de búsqueda personalizadas para mostrar los resultados de todas o algunas ubicaciones geo</span><span class="sxs-lookup"><span data-stu-id="dfe92-187">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="dfe92-p111">Aplicaciones de búsqueda personalizadas Obtén resultados de ubicaciones geo todas o algunas, especificando parámetros de consulta con la solicitud de la API de REST de búsqueda de SharePoint. Dependiendo de los parámetros de la consulta, la consulta se abanico a todas las ubicaciones de geo o en algunas ubicaciones geo. Por ejemplo, si sólo necesita un subconjunto de ubicaciones geo para buscar la información pertinente de la consulta, puede controlar el fan-out a éstas. Si la solicitud es correcta, la API de REST de SharePoint Search devuelve datos de respuesta.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p111">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="dfe92-192">Parámetros de consulta</span><span class="sxs-lookup"><span data-stu-id="dfe92-192">Query parameters</span></span>

<span data-ttu-id="dfe92-p112">**EnableMultiGeoSearch** - se trata de un valor booleano que especifica si la consulta será abanico a los índices de otras ubicaciones geo del inquilino Multi-Geo. Se establece en **true** para fan-out de la consulta; **false** para no fan-out de la consulta. El valor predeterminado es **false**. Si no incluye este parámetro, la consulta es **no** abanico a otras ubicaciones geo. Si utiliza el parámetro en un entorno que no sea Multi-Geo, se omite el parámetro.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p112">**EnableMultiGeoSearch** - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="dfe92-p113">**TipoCliente** - se trata de una cadena. Escriba un nombre de cliente única para cada aplicación de búsqueda. Si no incluye este parámetro, la consulta es **no** abanico a otras ubicaciones geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p113">**ClientType** - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="dfe92-p114">**MultiGeoSearchConfiguration** : ésta es una lista opcional de qué geo ubicaciones en el Multi-Geo inquilinos para la consulta abanico para cuando **EnableMultiGeoSearch** es **true**. Si no incluye este parámetro, o déjelo en blanco, la consulta se abanico a todas las ubicaciones de geo. Para cada ubicación geográfica, escriba lo siguiente en formato JSON:</span><span class="sxs-lookup"><span data-stu-id="dfe92-p114">**MultiGeoSearchConfiguration** - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dfe92-204">Elemento</span><span class="sxs-lookup"><span data-stu-id="dfe92-204">Item</span></span></th>
<th align="left"><span data-ttu-id="dfe92-205">Descripción</span><span class="sxs-lookup"><span data-stu-id="dfe92-205">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="dfe92-206">Ubicación_datos</span><span class="sxs-lookup"><span data-stu-id="dfe92-206">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="dfe92-207">La ubicación geográfica, por ejemplo NAM.</span><span class="sxs-lookup"><span data-stu-id="dfe92-207">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dfe92-208">Extremo</span><span class="sxs-lookup"><span data-stu-id="dfe92-208">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="dfe92-209">El extremo al que conectarse, por ejemplohttps://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="dfe92-209">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="dfe92-210">SourceId</span><span class="sxs-lookup"><span data-stu-id="dfe92-210">SourceId</span></span></td>
<td align="left"><span data-ttu-id="dfe92-211">El GUID del origen del resultado, por ejemplo B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="dfe92-211">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="dfe92-p115">Si se omite Ubicación_datos o extremo o un Ubicación_datos está duplicado, se produce un error en la solicitud. [Puede obtener información acerca del extremo de ubicaciones de geo de los inquilinos mediante Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="dfe92-p115">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="dfe92-214">Datos de respuesta</span><span class="sxs-lookup"><span data-stu-id="dfe92-214">Response data</span></span>

<span data-ttu-id="dfe92-p116">**MultiGeoSearchStatus** : ésta es una propiedad que devuelve la API de búsqueda de SharePoint en respuesta a una solicitud. El valor de la propiedad es una cadena y proporciona la siguiente información acerca de los resultados que devuelve la API de búsqueda de SharePoint:</span><span class="sxs-lookup"><span data-stu-id="dfe92-p116">**MultiGeoSearchStatus** – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dfe92-217">Valor</span><span class="sxs-lookup"><span data-stu-id="dfe92-217">Value</span></span></th>
<th align="left"><span data-ttu-id="dfe92-218">Descripción</span><span class="sxs-lookup"><span data-stu-id="dfe92-218">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="dfe92-219">Total</span><span class="sxs-lookup"><span data-stu-id="dfe92-219">Full</span></span></td>
<td align="left"><span data-ttu-id="dfe92-220">Resultados completos de <strong>todas</strong> las ubicaciones de geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-220">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="dfe92-221">Parcial</span><span class="sxs-lookup"><span data-stu-id="dfe92-221">Partial</span></span></td>
<td align="left"><span data-ttu-id="dfe92-p117">Resultados parciales de una o más ubicaciones de geo. Los resultados son incompletos debido a un error transitorio.</span><span class="sxs-lookup"><span data-stu-id="dfe92-p117">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="dfe92-224">Ninguna</span><span class="sxs-lookup"><span data-stu-id="dfe92-224">None</span></span></td>
<td align="left"><span data-ttu-id="dfe92-225">La consulta no era una consulta Multi-Geo y no fue abanico a otras ubicaciones geo.</span><span class="sxs-lookup"><span data-stu-id="dfe92-225">The query was not a Multi-Geo query and was not fanned out to the other geo locations.</span></span></td>
</tr>
</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="dfe92-226">Consulta con el servicio REST</span><span class="sxs-lookup"><span data-stu-id="dfe92-226">Query using the REST service</span></span>

<span data-ttu-id="dfe92-p118">Una solicitud GET, especifica los parámetros de consulta en la dirección URL. Con una solicitud POST, pase los parámetros de consulta en el cuerpo en formato JavaScript Object Notation (JSON).</span><span class="sxs-lookup"><span data-stu-id="dfe92-p118">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>

#### <a name="request-headers"></a><span data-ttu-id="dfe92-229">Encabezados de solicitud</span><span class="sxs-lookup"><span data-stu-id="dfe92-229">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="dfe92-230">Nombre</span><span class="sxs-lookup"><span data-stu-id="dfe92-230">Name</span></span></th>
<th align="left"><span data-ttu-id="dfe92-231">Valor</span><span class="sxs-lookup"><span data-stu-id="dfe92-231">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="dfe92-232">Tipo de contenido</span><span class="sxs-lookup"><span data-stu-id="dfe92-232">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="dfe92-233">Application/json; odata = verbose</span><span class="sxs-lookup"><span data-stu-id="dfe92-233">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="dfe92-234">Ejemplo de solicitud GET que es abanico a **todas las** ubicaciones de geo</span><span class="sxs-lookup"><span data-stu-id="dfe92-234">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="dfe92-235">https:// \<inquilinos\>/\_api, búsqueda/query?querytext = 'sharepoint' & Propiedades = 'EnableMultiGeoSearch:true' & TipoCliente =' Mi\_cliente\_id'</span><span class="sxs-lookup"><span data-stu-id="dfe92-235">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="dfe92-236">Ejemplo de solicitud GET para fan-out en **algunas** ubicaciones geo</span><span class="sxs-lookup"><span data-stu-id="dfe92-236">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="dfe92-237">https:// <tenant>/_api/search/query?querytext = 'sitio' & TipoCliente = & Propiedades de 'my_client_id' ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{Ubicación_datos\:"NAM"\,extremo\:"https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{Ubicación_datos\:"Puede"\,extremo\:" https\://contosoCAN.sharepoint-df.com "}]'</span><span class="sxs-lookup"><span data-stu-id="dfe92-237">https:// <tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\:"NAM"\,Endpoint\:"https\://contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{DataLocation\:"CAN"\,Endpoint\:"https\://contosoCAN.sharepoint-df.com"}]'</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="dfe92-238">Ejemplo de solicitud POST que es abanico a **todas las** ubicaciones de geo</span><span class="sxs-lookup"><span data-stu-id="dfe92-238">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="dfe92-239">Ejemplo de solicitud POST que es abanico a **algunas** ubicaciones de geo</span><span class="sxs-lookup"><span data-stu-id="dfe92-239">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="dfe92-240">Consulta con OMSC</span><span class="sxs-lookup"><span data-stu-id="dfe92-240">Query using CSOM</span></span>

<span data-ttu-id="dfe92-241">Ésta es una consulta de OMSC de muestra es abanico a **todas las** ubicaciones de geo:</span><span class="sxs-lookup"><span data-stu-id="dfe92-241">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;