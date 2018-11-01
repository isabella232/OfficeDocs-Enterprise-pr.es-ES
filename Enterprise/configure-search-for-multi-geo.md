---
title: Configurar la búsqueda en OneDrive para la Empresa multigeográfico
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información sobre cómo configurar la búsqueda en un entorno multigeográfico.
ms.openlocfilehash: 5ca2a35385ab2c246b78dc8811e8435bbdec25c7
ms.sourcegitcommit: a3e2b2e58c328238c15d3f9daf042ea3de9d66be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2018
ms.locfileid: "25849916"
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a><span data-ttu-id="f737b-103">Configurar la búsqueda en OneDrive para la Empresa multigeográfico</span><span class="sxs-lookup"><span data-stu-id="f737b-103">Configure Search for OneDrive for Business Multi-Geo</span></span>

<span data-ttu-id="f737b-104">En un entorno de OneDrive para la Empresa multigeográfico, una organización puede tener un espacio empresarial de Office 365, pero almacenar el contenido de OneDrive en varias ubicaciones geográficas: una ubicación central y una o varias ubicaciones por satélite.</span><span class="sxs-lookup"><span data-stu-id="f737b-104">In a Multi-Geo SharePoint Online (SPO) environment, an organization can have one Office 365 tenant, but store their SharePoint content in multiple geographical locations - one central location and one or more satellite geo locations.</span></span>

<span data-ttu-id="f737b-p101">Cada ubicación geográfica tiene su propio índice de búsqueda y Centro de búsqueda. Cuando un usuario realiza una búsqueda, se efectúa una distribución ramificada de la consulta a todos los índices y los resultados devueltos se combinan.</span><span class="sxs-lookup"><span data-stu-id="f737b-p101">Each geographical location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.</span></span>

<span data-ttu-id="f737b-p102">Por ejemplo, un usuario de una ubicación geográfica puede realizar búsquedas de contenido almacenado en otra ubicación geográfica o contenido de un sitio de SharePoint que está restringido a otra ubicación geográfica. Si el usuario tiene acceso a este contenido, la búsqueda mostrará el resultado.</span><span class="sxs-lookup"><span data-stu-id="f737b-p102">For example, a user in one geo location can search for content stored in another geo location, or for content on a SharePoint site that’s restricted to a different geo location. If the user has access to this content, search will show the result.</span></span>

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a><span data-ttu-id="f737b-109">¿Qué clientes de búsqueda trabajan en un entorno multigeográfico?</span><span class="sxs-lookup"><span data-stu-id="f737b-109">Which search clients work in a Multi-Geo environment?</span></span>

<span data-ttu-id="f737b-110">Estos clientes pueden devolver resultados de todas las ubicaciones geográficas:</span><span class="sxs-lookup"><span data-stu-id="f737b-110">These clients can return results from all geo locations:</span></span>

-   <span data-ttu-id="f737b-111">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="f737b-111">OneDrive for Business</span></span>

-   <span data-ttu-id="f737b-112">Delve</span><span class="sxs-lookup"><span data-stu-id="f737b-112">Delve</span></span>

-   <span data-ttu-id="f737b-113">Página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="f737b-113">The SharePoint home page</span></span>

-   <span data-ttu-id="f737b-114">Centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="f737b-114">The Search Center</span></span>

-   <span data-ttu-id="f737b-115">Aplicaciones de búsqueda personalizada que usan la API de SharePoint Search</span><span class="sxs-lookup"><span data-stu-id="f737b-115">Custom search applications that use the SharePoint Search API</span></span>

### <a name="onedrive-for-business"></a><span data-ttu-id="f737b-116">OneDrive para la Empresa</span><span class="sxs-lookup"><span data-stu-id="f737b-116">OneDrive for Business</span></span>

<span data-ttu-id="f737b-117">En cuanto se haya configurado el entorno multigeográfico, los usuarios que busquen en OneDrive obtendrán resultados de todas las ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="f737b-117">As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all geo locations.</span></span>

### <a name="delve"></a><span data-ttu-id="f737b-118">Delve</span><span class="sxs-lookup"><span data-stu-id="f737b-118">Delve</span></span>

<span data-ttu-id="f737b-119">En cuanto se haya configurado el entorno multigeográfico, los usuarios que busquen en Delve obtendrán resultados de todas las ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="f737b-119">As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all geo locations.</span></span>

<span data-ttu-id="f737b-p103">La fuente de Delve y la tarjeta de perfil solo muestran vistas previas de los archivos almacenados en la ubicación **central**. Para los archivos que se almacenan en ubicaciones por satélite, se muestra el icono del tipo de archivo en su lugar.</span><span class="sxs-lookup"><span data-stu-id="f737b-p103">The Delve feed and the profile card only show previews of files that are stored in the **central** location. For files that are stored in satellite geo locations, the icon for the file type is shown instead.</span></span>

### <a name="the-sharepoint-home-page"></a><span data-ttu-id="f737b-122">Página principal de SharePoint</span><span class="sxs-lookup"><span data-stu-id="f737b-122">The SharePoint home page</span></span>

<span data-ttu-id="f737b-p104">En cuanto se haya configurado el entorno multigeográfico, los usuarios verán noticias, sitios seguidos y recientes desde varias ubicaciones geográficas en su página principal de SharePoint. Si usan el cuadro de búsqueda en la página principal de SharePoint, obtendrán resultados combinados desde varias ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="f737b-p104">As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple geo locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple geo locations.</span></span>

### <a name="the-search-center"></a><span data-ttu-id="f737b-125">Centro de búsqueda</span><span class="sxs-lookup"><span data-stu-id="f737b-125">The Search Center</span></span>

<span data-ttu-id="f737b-p105">Cuando se haya configurado el entorno multigeográfico, cada Centro de búsqueda sigue mostrando solo los resultados de su propia ubicación geográfica. Los administradores deben [cambiar la configuración de cada Centro de búsqueda](#_Set_up_a_1) para obtener resultados de todas las ubicaciones geográficas. Después, los usuarios que realicen búsquedas en el Centro de búsqueda obtendrán resultados de todas las ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="f737b-p105">After the Multi-Geo environment has been set up, each Search Center continues to only show results from their own geo location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all geo locations. Afterwards, users that search in the Search Center get results from all geo locations.</span></span>

### <a name="custom-search-applications"></a><span data-ttu-id="f737b-129">Aplicaciones de búsqueda personalizada</span><span class="sxs-lookup"><span data-stu-id="f737b-129">Custom search applications</span></span>

<span data-ttu-id="f737b-p106">Como de costumbre, las aplicaciones de búsqueda personalizada interactúan con los índices de búsqueda mediante las API REST de SharePoint Search existentes. Para obtener resultados de todas o algunas de las ubicaciones geográficas, la aplicación tiene que [llamar a la API e incluir los nuevos parámetros de consulta multigeográfica](#_Get_custom_search) en la solicitud. Esto desencadena la distribución ramificada de la consulta a todas las ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="f737b-p106">As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some geo locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all geo locations.</span></span>

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a><span data-ttu-id="f737b-133">¿En qué se diferencia la búsqueda en un entorno multigeográfico?</span><span class="sxs-lookup"><span data-stu-id="f737b-133">What’s different about search in a Multi-Geo environment?</span></span>

<span data-ttu-id="f737b-134">Algunas características de búsqueda con las que tal vez esté familiarizado, funcionan de forma distinta en un entorno multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="f737b-134">Some search features you might be familiar with, work differently in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f737b-135"><strong>Característica</strong></span><span class="sxs-lookup"><span data-stu-id="f737b-135"><strong>Feature</strong></span></span></th>
<th align="left"><span data-ttu-id="f737b-136"><strong>¿Cómo funciona?</strong></span><span class="sxs-lookup"><span data-stu-id="f737b-136"><strong>How does it work</strong></span></span></th>
<th align="left"><span data-ttu-id="f737b-137"><strong>Solución alternativa</strong></span><span class="sxs-lookup"><span data-stu-id="f737b-137"><strong>Workaround</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f737b-138">Resultados promocionados</span><span class="sxs-lookup"><span data-stu-id="f737b-138">Promoted results</span></span></td>
<td align="left"><span data-ttu-id="f737b-p107">Puede crear reglas de consulta con los resultados promocionados en distintos niveles: para todo el espacio empresarial, para una colección de sitios o para un sitio. En un entorno multigeográfico, defina los resultados promocionados en el nivel de <strong>espacio empresarial</strong> si quiere promover los resultados a los centros de búsqueda de <strong>todas</strong> las ubicaciones geográficas. Si <strong>solo</strong> quiere promover los resultados del Centro de búsqueda que se encuentra en la ubicación geográfica del sitio o la colección de sitios, defina los resultados en el nivel de <strong>colección de sitios</strong> o de <strong>sitio</strong>.</span><span class="sxs-lookup"><span data-stu-id="f737b-p107">You can create query rules with promoted results at different levels: for the whole tenant, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the <strong>tenant</strong> level if you want to promote the results to the Search Centers in <strong>all</strong> geo locations. If you <strong>only</strong> want to promote results in the Search Center that’s in the geo location of the site collection or site, define the results at the <strong>site collection</strong> or <strong>site</strong> level.</span></span></td>
<td align="left"><span data-ttu-id="f737b-142">Si no necesita resultados promocionados distintos por ubicación geográfica, por ejemplo, diferentes reglas de viaje, se recomienda definir los resultados promocionados en el nivel de espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="f737b-142">If you don’t need different promoted results per geo location, for example different rules for traveling, we recommend defining promoted results at the tenant level.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f737b-143">Refinadores de búsquedas</span><span class="sxs-lookup"><span data-stu-id="f737b-143">Search refiners</span></span></td>
<td align="left"><span data-ttu-id="f737b-p108">La búsqueda devuelve refinadores de todas las ubicaciones geográficas de un espacio empresarial y luego los agrega. La agregación es la mejor posible, lo que significa que puede que los recuentos de refinadores no sean exactos al 100%. Para la mayoría de los escenarios basado en búsquedas esta precisión es suficiente. </span><span class="sxs-lookup"><span data-stu-id="f737b-p108">Search returns refiners from all the geo locations of a tenant and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. </span></span></td>
<td align="left"><span data-ttu-id="f737b-147">En aplicaciones basadas en búsquedas que dependen de la exhaustividad del refinador, consulte cada ubicación geográfica por separado sin usar la distribución ramificada multigeográfica.</span><span class="sxs-lookup"><span data-stu-id="f737b-147">For search-driven applications that depend on refiner completeness, query each geo location independently without using Multi-Geo fan-out.</span></span></td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left"><span data-ttu-id="f737b-148">La búsqueda multigeográfica no admite la creación dinámica de cubos para refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="f737b-148">Multi-Geo search doesn’t support dynamic bucketing for numerical refiners.</span></span></td>
<td align="left"><span data-ttu-id="f737b-149">Use el parámetro <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize”</a> para refinadores numéricos.</span><span class="sxs-lookup"><span data-stu-id="f737b-149">Use the <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize” parameter</a> for numerical refiners.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f737b-150">Identificadores de documento</span><span class="sxs-lookup"><span data-stu-id="f737b-150">Document IDs</span></span></td>
<td align="left"><span data-ttu-id="f737b-151">Si está desarrollando una aplicación basada en búsquedas que depende de los identificadores de documento, tenga en cuenta que los identificadores de documento en un entorno multigeográfico no son únicos en todas las ubicaciones geográficas, son únicos por ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="f737b-151">If you’re developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren’t unique across geo locations, they are unique per geo location.</span></span></td>
<td align="left"><span data-ttu-id="f737b-p109">Hemos agregado una columna que identifica la ubicación geográfica. Utilice esta columna para lograr unicidad. Esta columna se denomina "GeoLocationSource".</span><span class="sxs-lookup"><span data-stu-id="f737b-p109">We’ve added a column that identifies the geo location. Use this column to achieve uniqueness. This column is named “GeoLocationSource”.</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f737b-155">Número de resultados</span><span class="sxs-lookup"><span data-stu-id="f737b-155">Number of results</span></span></td>
<td align="left"><span data-ttu-id="f737b-156">La página de resultados de búsqueda muestra los resultados combinados de las ubicaciones geográficas, pero no es posible ver más allá de 500 resultados.</span><span class="sxs-lookup"><span data-stu-id="f737b-156">The search results page shows combined results from the geo locations, but it’s not possible to page beyond 500 results.</span></span></td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a><span data-ttu-id="f737b-157">¿Qué no es compatible con la búsqueda en un entorno multigeográfico?</span><span class="sxs-lookup"><span data-stu-id="f737b-157">What’s not supported for search in a Multi-Geo environment?</span></span>

<span data-ttu-id="f737b-158">Algunas características de búsqueda con las que tal vez esté familiarizado, no se admiten en un entorno multigeográfico.</span><span class="sxs-lookup"><span data-stu-id="f737b-158">Some of the search features you might be familiar with, aren’t supported in a Multi-Geo environment.</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f737b-159"><strong>Característica de búsqueda</strong></span><span class="sxs-lookup"><span data-stu-id="f737b-159"><strong>Search feature</strong></span></span></th>
<th align="left"><span data-ttu-id="f737b-160"><strong>Nota</strong></span><span class="sxs-lookup"><span data-stu-id="f737b-160"><strong>Note</strong></span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f737b-161">Autenticación solo de aplicación</span><span class="sxs-lookup"><span data-stu-id="f737b-161">App-only authentication</span></span></td>
<td align="left"><span data-ttu-id="f737b-162">La autenticación solo de aplicación (acceso con privilegios desde servicios) no se admite en la búsqueda multigeográfica.</span><span class="sxs-lookup"><span data-stu-id="f737b-162">App-only authentication (privileged access from services) isn’t supported in Multi-Geo search.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f737b-163">Usuarios invitados</span><span class="sxs-lookup"><span data-stu-id="f737b-163">Guest users</span></span></td>
<td align="left"><span data-ttu-id="f737b-164">Los usuarios invitados solo obtienen resultados de la ubicación geográfica desde la que buscan.</span><span class="sxs-lookup"><span data-stu-id="f737b-164">Guest users only get results from the geo location that they’re searching from.</span></span></td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a><span data-ttu-id="f737b-165">¿Cómo funciona la búsqueda en un entorno multigeográfico?</span><span class="sxs-lookup"><span data-stu-id="f737b-165">How does search work in a Multi-Geo environment?</span></span>

<span data-ttu-id="f737b-166">**Todos** los clientes de búsqueda usan la API REST de SharePoint Search existente para interactuar con los índices de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="f737b-166">**All** the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.</span></span>

<img src="media/configure-search-for-multi-geo-image1-1.png" />

1. <span data-ttu-id="f737b-167">Un cliente de búsqueda llama al punto de conexión de REST de búsqueda con la propiedad EnableMultiGeoSearch= true.</span><span class="sxs-lookup"><span data-stu-id="f737b-167">A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.</span></span>
2. <span data-ttu-id="f737b-168">La consulta se envía a todas las ubicaciones geográficas del espacio empresarial.</span><span class="sxs-lookup"><span data-stu-id="f737b-168">The query is sent to all geo locations in the tenant.</span></span>
3. <span data-ttu-id="f737b-169">Los resultados de búsqueda de cada ubicación geográfica se combinan y clasifican.</span><span class="sxs-lookup"><span data-stu-id="f737b-169">Search results from each geo location are merged and ranked.</span></span>
4. <span data-ttu-id="f737b-170">El cliente obtiene resultados unificados.</span><span class="sxs-lookup"><span data-stu-id="f737b-170">The client gets unified search results.</span></span>



<span data-ttu-id="f737b-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Observe que no combinamos los resultados de búsqueda hasta que hemos recibido los resultados de todas las ubicaciones geográficas. Esto significa que las búsquedas multigeográficas tienen latencia adicional con respecto a las búsquedas en un entorno de una sola ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="f737b-p110"><span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Notice that we don’t merge the search results until we’ve received results from all the geo locations. This means that Multi-Geo searches have additional latency compared to searches in an environment with only one geo location.</span></span>

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a><span data-ttu-id="f737b-173">Obtener un Centro de búsqueda que muestre los resultados de todas las ubicaciones geográficas</span><span class="sxs-lookup"><span data-stu-id="f737b-173">Get a Search Center to show results from all geo locations</span></span>

<span data-ttu-id="f737b-174">Cada Centro de búsqueda tiene varios sectores verticales y hay que configurar individualmente cada sector vertical.</span><span class="sxs-lookup"><span data-stu-id="f737b-174">Each Search Center has several verticals and you have to set up each vertical individually.</span></span>

1.  <span data-ttu-id="f737b-175">Asegúrese de realizar estos pasos con una cuenta que tenga permiso para editar la página de resultados de búsqueda y el elemento web de resultados de búsqueda.</span><span class="sxs-lookup"><span data-stu-id="f737b-175">Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.</span></span>

2.  <span data-ttu-id="f737b-176">Navegue a la página de resultados de búsqueda (vea la [lista](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de páginas de resultados de búsqueda).</span><span class="sxs-lookup"><span data-stu-id="f737b-176">Navigate to the search results page (see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages)</span></span>

3.  <span data-ttu-id="f737b-p111">Seleccione el sector vertical que quiere configurar, haga clic en el icono de engranaje **Configuración** de la esquina superior derecha y luego en **Editar página**. La página de resultados de búsqueda se abre en modo de edición.</span><span class="sxs-lookup"><span data-stu-id="f737b-p111">Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.</span></span>

     ![](media/configure-search-for-multi-geo-image2.png)
1.  <span data-ttu-id="f737b-p112">En el elemento web de resultados de búsqueda, mueva el puntero a la esquina superior derecha del elemento web, haga clic en la flecha y luego en **Editar elemento Web** en el menú. El panel de herramientas del elemento web de resultados de búsqueda se abrirá en la cinta de la parte superior derecha de la página. ![](media/configure-search-for-multi-geo-image3.png)</span><span class="sxs-lookup"><span data-stu-id="f737b-p112">In the Search Results Web Part, move the pointer to the upper, right corner of the Web Part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page. ![](media/configure-search-for-multi-geo-image3.png)</span></span>

1.  <span data-ttu-id="f737b-181">En la sección **Configuración** del panel de herramientas del elemento web de resultados de búsqueda, en **Configuración de control de resultados**, seleccione **Show Multi-Geo results** (Mostrar resultados multigeográficos) para que el elemento web de resultados de la búsqueda muestre los resultados de todas las ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="f737b-181">In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.</span></span>

2.  <span data-ttu-id="f737b-182">Haga clic en **Aceptar** para guardar los cambios y cierre el panel de herramientas del elemento web.</span><span class="sxs-lookup"><span data-stu-id="f737b-182">Click **OK** to save your change and close the Web Part tool pane.</span></span>

3.  <span data-ttu-id="f737b-183">Para comprobar los cambios realizados en el elemento web de resultados de búsqueda, haga clic en **Proteger** en la pestaña de página del menú principal.</span><span class="sxs-lookup"><span data-stu-id="f737b-183">Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.</span></span>

4.  <span data-ttu-id="f737b-184">Publique los cambios mediante el vínculo incluido en la nota de la parte superior de la página.</span><span class="sxs-lookup"><span data-stu-id="f737b-184">Publish the changes by using the link provided in the note at the top of the page.</span></span>

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a><span data-ttu-id="f737b-185">Obtener aplicaciones de búsqueda personalizada que muestren los resultados de todas o algunas de las ubicaciones geográficas</span><span class="sxs-lookup"><span data-stu-id="f737b-185">Get custom search applications to show results from all or some geo locations</span></span>

<span data-ttu-id="f737b-p113">Las aplicaciones de búsqueda personalizada obtienen resultados de todas o algunas de las ubicaciones geográficas especificando parámetros de consulta con la solicitud a la API REST de SharePoint Search. En función de los parámetros de consulta, se efectúa una distribución ramificada de la consulta a todas o a algunas de las ubicaciones geográficas. Por ejemplo, si solo tiene que consultar un subconjunto de las ubicaciones geográficas para encontrar información relevante, puede controlar la distribución ramificada a solo estas. Si la solicitud se realiza correctamente, la API REST de SharePoint Search devuelve datos de respuesta.</span><span class="sxs-lookup"><span data-stu-id="f737b-p113">Custom search applications get results from all, or some, geo locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all geo locations, or to some geo locations. For example, if you only need to query a subset of geo locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.</span></span>

### <a name="query-parameters"></a><span data-ttu-id="f737b-190">Parámetros de consulta</span><span class="sxs-lookup"><span data-stu-id="f737b-190">Query parameters</span></span>

<span data-ttu-id="f737b-p114">EnableMultiGeoSearch: valor booleano que especifica si se efectuará una distribución ramificada de la consulta a los índices de otras ubicaciones geográficas del inquilino multigeográfico. Establézcalo en **true** para efectuar una distribución ramificada de la consulta; en **false** para no efectuar una distribución ramificada de la consulta. El valor predeterminado es **false**. Si no incluye este parámetro, **no** se efectúa una distribución ramificada de la consulta a otras ubicaciones geográficas. Si usa el parámetro en un entorno que no es multigeográfico, se ignorará el parámetro.</span><span class="sxs-lookup"><span data-stu-id="f737b-p114">EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the Multi-Geo tenant. Set it to **true** to fan out the query; **false** to not fan out the query. The default value is **false**. If you don’t include this parameter, the query is **not** fanned out to other geo locations. If you use the parameter in an environment that isn’t Multi-Geo, the parameter is ignored.</span></span>

<span data-ttu-id="f737b-p115">ClientType: se trata de una cadena. Escriba un nombre de cliente único para cada aplicación de búsqueda. Si no incluye este parámetro, **no** se efectúa una distribución ramificada de la consulta a otra ubicación geográfica.</span><span class="sxs-lookup"><span data-stu-id="f737b-p115">ClientType - This is a string. Enter a unique client name for each search application. If you don’t include this parameter, the query is **not** fanned out to other geo locations.</span></span>

<span data-ttu-id="f737b-p116">MultiGeoSearchConfiguration: lista opcional de las ubicaciones geográficas del inquilino multigeográfico que se distribuyen cuando **EnableMultiGeoSearch** es **true**. Si no incluye este parámetro o lo deja en blanco, se efectúa una distribución ramificada de la consulta a todas las ubicaciones geográficas. Para cada ubicación geográfica, escriba los elementos siguientes, con formato JSON:</span><span class="sxs-lookup"><span data-stu-id="f737b-p116">MultiGeoSearchConfiguration - This is an optional list of which geo locations in the Multi-Geo tenant to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don’t include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f737b-202">Item</span><span class="sxs-lookup"><span data-stu-id="f737b-202">Item</span></span></th>
<th align="left"><span data-ttu-id="f737b-203">Descripción</span><span class="sxs-lookup"><span data-stu-id="f737b-203">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f737b-204">DataLocation</span><span class="sxs-lookup"><span data-stu-id="f737b-204">DataLocation</span></span></td>
<td align="left"><span data-ttu-id="f737b-205">Ubicación geográfica, por ejemplo, NAM.</span><span class="sxs-lookup"><span data-stu-id="f737b-205">The geo location, for example NAM.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f737b-206">EndPoint</span><span class="sxs-lookup"><span data-stu-id="f737b-206">EndPoint</span></span></td>
<td align="left"><span data-ttu-id="f737b-207">Punto de conexión al que conectarse; por ejemplo, https://contoso.sharepoint.com</span><span class="sxs-lookup"><span data-stu-id="f737b-207">The endpoint to connect to, for example https://contoso.sharepoint.com</span></span></td>
</tr>
<tr class="odd">
<td align="left"><span data-ttu-id="f737b-208">SourceId</span><span class="sxs-lookup"><span data-stu-id="f737b-208">SourceId</span></span></td>
<td align="left"><span data-ttu-id="f737b-209">GUID del origen de resultados, por ejemplo, B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span><span class="sxs-lookup"><span data-stu-id="f737b-209">The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</span></span></td>
</tr>
</tbody>
</table>

<span data-ttu-id="f737b-p117">Si omite DataLocation o EndPoint, o si una DataLocation se duplica, la solicitud no se realiza. [Puede obtener información sobre el punto de conexión de las ubicaciones geográficas de un espacio empresarial con Microsoft Graph](https://docs.microsoft.com/es-ES/sharepoint/dev/solution-guidance/multigeo-discovery).</span><span class="sxs-lookup"><span data-stu-id="f737b-p117">If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://docs.microsoft.com/es-ES/sharepoint/dev/solution-guidance/multigeo-discovery).</span></span>

### <a name="response-data"></a><span data-ttu-id="f737b-212">Datos de respuesta</span><span class="sxs-lookup"><span data-stu-id="f737b-212">Response data</span></span>

<span data-ttu-id="f737b-p118">MultiGeoSearchStatus: se trata de una propiedad que devuelve la API de SharePoint Search en respuesta a una solicitud. El valor de la propiedad es una cadena y proporciona la información siguiente sobre los resultados que devuelve la API de SharePoint Search:</span><span class="sxs-lookup"><span data-stu-id="f737b-p118">MultiGeoSearchStatus – This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f737b-215">Valor</span><span class="sxs-lookup"><span data-stu-id="f737b-215">Value</span></span></th>
<th align="left"><span data-ttu-id="f737b-216">Descripción</span><span class="sxs-lookup"><span data-stu-id="f737b-216">Description</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f737b-217">Full</span><span class="sxs-lookup"><span data-stu-id="f737b-217">Full</span></span></td>
<td align="left"><span data-ttu-id="f737b-218">Resultados completos de <strong>todas</strong> ubicaciones geográficas.</span><span class="sxs-lookup"><span data-stu-id="f737b-218">Full results from <strong>all</strong> the geo locations.</span></span></td>
</tr>
<tr class="even">
<td align="left"><span data-ttu-id="f737b-219">Partial</span><span class="sxs-lookup"><span data-stu-id="f737b-219">Partial</span></span></td>
<td align="left"><span data-ttu-id="f737b-p119">Resultados parciales de una o varias ubicaciones geográficas. Los resultados están incompletos debido a un error transitorio.</span><span class="sxs-lookup"><span data-stu-id="f737b-p119">Partial results from one or more geo locations. The results are incomplete due to a transient error.</span></span></td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a><span data-ttu-id="f737b-222">Consultar con el servicio REST</span><span class="sxs-lookup"><span data-stu-id="f737b-222">Query using the REST service</span></span>

<span data-ttu-id="f737b-p120">Con una solicitud GET, especifica los parámetros de consulta en la dirección URL. Con una solicitud de POST, pasa los parámetros de consulta del cuerpo en el formato de notación de objetos JavaScript (JSON).</span><span class="sxs-lookup"><span data-stu-id="f737b-p120">With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation (JSON) format.</span></span>


#### <a name="request-headers"></a><span data-ttu-id="f737b-225">Encabezados de solicitud</span><span class="sxs-lookup"><span data-stu-id="f737b-225">Request headers</span></span>

<table>
<thead>
<tr class="header">
<th align="left"><span data-ttu-id="f737b-226">Nombre</span><span class="sxs-lookup"><span data-stu-id="f737b-226">Name</span></span></th>
<th align="left"><span data-ttu-id="f737b-227">Valor</span><span class="sxs-lookup"><span data-stu-id="f737b-227">Value</span></span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><span data-ttu-id="f737b-228">Content-Type</span><span class="sxs-lookup"><span data-stu-id="f737b-228">Content-Type</span></span></td>
<td align="left"><span data-ttu-id="f737b-229">application/json;odata=verbose</span><span class="sxs-lookup"><span data-stu-id="f737b-229">application/json;odata=verbose</span></span></td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="f737b-230">Ejemplo de distribución ramificada de una solicitud GET a **todas** las ubicaciones geográficas</span><span class="sxs-lookup"><span data-stu-id="f737b-230">Sample GET request that’s fanned out to **all** geo locations</span></span>

<span data-ttu-id="f737b-231">https:// \<espacio empresarial\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span><span class="sxs-lookup"><span data-stu-id="f737b-231">https:// \<tenant\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'</span></span>

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a><span data-ttu-id="f737b-232">Ejemplo de solicitud GET para efectuar una distribución ramificada en **algunas** ubicaciones geográficas</span><span class="sxs-lookup"><span data-stu-id="f737b-232">Sample GET request to fan out to **some** geo locations</span></span>

<span data-ttu-id="f737b-233">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span><span class="sxs-lookup"><span data-stu-id="f737b-233">https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'</span></span>

> [!NOTE]
> <span data-ttu-id="f737b-p121">Las comas y los dos puntos de la lista de ubicaciones geográficas de la propiedad MultiGeoSearchConfiguration van precedidas por el carácter **barra diagonal inversa**. Esto es debido a que las solicitudes GET usan dos puntos para separar las propiedades, y comas para separar los argumentos de las propiedades. Sin la barra diagonal inversa como carácter de escape, la propiedad MultiGeoSearchConfiguration se interpreta de forma errónea.</span><span class="sxs-lookup"><span data-stu-id="f737b-p121">Commas and colons in the list of geo-locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character. This is because GET requests use colons to separate properties and commas to separate arguments of properties. Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.</span></span>

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a><span data-ttu-id="f737b-237">Ejemplo de distribución ramificada de una solicitud POST a **todas** las ubicaciones geográficas</span><span class="sxs-lookup"><span data-stu-id="f737b-237">Sample POST request that’s fanned out to **all** geo locations</span></span>

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a><span data-ttu-id="f737b-238">Ejemplo de distribución ramificada de una solicitud POST a **algunas** ubicaciones geográficas</span><span class="sxs-lookup"><span data-stu-id="f737b-238">Sample POST request that’s fanned out to **some** geo locations</span></span>


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

### <a name="query-using-csom"></a><span data-ttu-id="f737b-239">Consultar con CSOM</span><span class="sxs-lookup"><span data-stu-id="f737b-239">Query using CSOM</span></span>

<span data-ttu-id="f737b-240">Ejemplo de distribución ramificada de una consulta CSOM a **todas** las ubicaciones geográficas</span><span class="sxs-lookup"><span data-stu-id="f737b-240">Here’s a sample CSOM query that’s fanned out to **all** geo locations:</span></span>

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

