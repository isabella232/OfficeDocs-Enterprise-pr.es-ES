---
title: Use la herramienta de diagnóstico de la página de SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/26/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
search.appverid:
- MET150
- SPO160
- MOE150
- BSA160
ms.assetid: dbab2593-dc6a-40f7-adfe-031b9baa620f
description: Use los diagnósticos de página para la herramienta de SharePoint para analizar sus páginas clásicas con las mejores prácticas recomendadas para SharePoint Online.
ms.openlocfilehash: 6bfe26900426b30b9f0ad0746b0c1840e122dc82
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542942"
---
# <a name="use-the-page-diagnostics-tool-for-sharepoint-online"></a><span data-ttu-id="6eb73-103">Use la herramienta de diagnóstico de la página de SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="6eb73-103">Use the Page Diagnostics tool for SharePoint Online</span></span>

<span data-ttu-id="6eb73-104">En este artículo se describe cómo puede usar la herramienta de diagnóstico de página para analizar sus páginas de publicación clásicas y las páginas de sitios de equipo clásico, frente a un subconjunto de las prácticas recomendadas en **SharePoint Online**.</span><span class="sxs-lookup"><span data-stu-id="6eb73-104">This article describes how you can use the Page Diagnostic tool to analyze your classic publishing pages and pages on classic team sites, against a subset of recommended practices in **SharePoint Online**.</span></span> 
  
<span data-ttu-id="6eb73-p101">Los sitios de grupo que no tengan habilitada la publicación no se pueden hacer uso de las CDN pero todas las reglas restantes son aplicables. Publicación agrega sobrecarga adicional, por lo que no activa la publicación sólo para obtener la funcionalidad CDN tal y como lo quedará afectado negativamente tiempos de carga de página.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p101">Team sites that don't have Publishing enabled cannot make use of CDNs but all of the remaining rules are applicable. Publishing adds additional overhead so do not turn on Publishing just to get the CDN functionality as it will negatively impact page load times.</span></span>
  
> [!IMPORTANT]
> <span data-ttu-id="6eb73-p102">La herramienta de diagnóstico de la página no se ejecutará con las bibliotecas de documentos o páginas del sistema, como la herramienta está diseñada para revisar las páginas del sitio de SharePoint. Una página *allitems.aspx* es un sistema. Si intenta ejecutar la herramienta en una página del sistema, recibirá un mensaje que lee, "sólo se debe ejecutar esta aplicación en las páginas de SharePoint." > ![debe ejecutar en una página de SharePoint](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)</span><span class="sxs-lookup"><span data-stu-id="6eb73-p102">The Page Diagnostics tool will not run against document libraries or system pages, as the tool is designed to review SharePoint site pages. An  *allitems.aspx*  page is a system page. If you attempt to run the tool on a system page, you will get a message that reads, "This application should only be run on SharePoint pages." > ![Must run on a  SharePoint page](media/34aadfff-1009-496b-9c87-4fc2780e017c.png)</span></span>
  
> <span data-ttu-id="6eb73-p103">No es un error en la herramienta como no hay ningún valor en la evaluación de bibliotecas o páginas del sistema. Navegue a una página de SharePoint que no sea de sistema para usar la herramienta. ¿Si desea enviar comentarios acerca de la herramienta por favor, haga clic en la ficha acerca y siga el [ceder el vínculo de comentarios](https://go.microsoft.com/fwlink/?linkid=874109).</span><span class="sxs-lookup"><span data-stu-id="6eb73-p103">This is not an error in the tool as there is no value in assessing libraries or system pages. Please navigate to a non-system SharePoint page to use the tool. Should you wish to give feedback about the tool please click the About tab and follow the [give feedback link](https://go.microsoft.com/fwlink/?linkid=874109).</span></span> 
  
## <a name="how-to-use-the-page-diagnostic-tool"></a><span data-ttu-id="6eb73-114">Cómo usar la herramienta de diagnóstico de página</span><span class="sxs-lookup"><span data-stu-id="6eb73-114">How to use the Page Diagnostic tool</span></span>
<span data-ttu-id="6eb73-115"><a name="useit"> </a></span><span class="sxs-lookup"><span data-stu-id="6eb73-115"></span></span>

1. <span data-ttu-id="6eb73-116">Mediante un explorador de Chrome, abra directamente el [vínculo a la herramienta](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) o abra la búsqueda en el [Almacén Web del explorador de Chrome](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) e instale la extensión de explorador.</span><span class="sxs-lookup"><span data-stu-id="6eb73-116">Using a Chrome browser, open the [link to the tool](https://chrome.google.com/webstore/detail/inahogkhlkbkjkkaleonemeijihmfagi) directly or open the Search in the [Chrome Browser WebStore](https://chrome.google.com/webstore/search/page%20diagnostics%20for%20sharepoint) and install the browser extension.</span></span> 
    
    <span data-ttu-id="6eb73-117">Revise la directiva de privacidad del usuario proporcionada en la página de descripción en el almacén.</span><span class="sxs-lookup"><span data-stu-id="6eb73-117">Please review the User Privacy Policy provided on the description page in the store.</span></span>
    
    <span data-ttu-id="6eb73-118">Al agregar la herramienta para el explorador, verá lo siguiente tenga en cuenta los permisos.</span><span class="sxs-lookup"><span data-stu-id="6eb73-118">When adding the tool to your browser, you will see the following permissions notice.</span></span>
    
    ![Permisos del almacén de cromo](media/e9fbcef0-1171-43ac-8ea8-c2b5be1b7925.png)
  
    <span data-ttu-id="6eb73-p104">Este aviso está en su lugar debido a que una página puede contener contenido desde ubicaciones fuera de SharePoint según los elementos Web y las personalizaciones en la página. Esto significa que la herramienta leerá las solicitudes y respuestas cuando se hace clic en el botón Inicio y sólo de la ficha activa de SharePoint donde se ejecuta la herramienta. Esta información se captura localmente por el explorador web y está disponible a través de la exportación al vínculo de JSON en la herramienta. **La información no se envía o capturada por Microsoft.**</span><span class="sxs-lookup"><span data-stu-id="6eb73-p104">This notice is in place because a page may contain content from locations outside of SharePoint depending on the webparts and customizations on the page. This means that the tool will read the requests and responses when the start button is clicked and only for the active SharePoint tab where the tool is running. That information is captured locally by the web browser and is available to you via the Export to JSON link in the tool. **The information is not sent to or captured by Microsoft.**</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="6eb73-p105">Microsoft no lee los datos o sitios Web que visite y no se captura cualquier información personal, la información de sitio Web o descargar con esta herramienta. La única información registrada por la herramienta es el nombre del inquilino, count y si se ha usado la opción de compatibilidad con el registro cuando se ejecuta la herramienta de la regla. Esta información es de Microsoft para analizar cuáles son los desafíos que se está produciendo por nuestros clientes y para garantizar que la capacidad de registro de soporte técnico no es un mal uso.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p105">Microsoft does not read the data or websites you visit, and we do not capture any personal information, website or download information with this tool. The only information logged by the tool is the Tenant name, Rule count and whether the support logging option has been utilized when the tool is run. This information is for Microsoft to analyze what challenges are being experienced by our Customers and to ensure the Support logging capability is not being misused.</span></span>
  
<span data-ttu-id="6eb73-127">La herramienta respeta el Microsoft Privacy directiva accesible [aquí](https://go.microsoft.com/fwlink/p/?linkid=857875).</span><span class="sxs-lookup"><span data-stu-id="6eb73-127">The tool respects the Microsoft Privacy policy accessible [here](https://go.microsoft.com/fwlink/p/?linkid=857875).</span></span> 
  
    The "Export to JSON" functionality in the tool is also why the "Manage your downloads" permission is needed. Please follow your Company's own Privacy guidelines before sharing the JSON file outside of your Company as it contains the URL's and they fall within PII (Personally Identifiable Information).
    
2. <span data-ttu-id="6eb73-128">(Opcional) Si desea usar la herramienta en modo de incognito de cromo, navegue a la extensión y haga clic en "permitir en incognito".</span><span class="sxs-lookup"><span data-stu-id="6eb73-128">(Optional) If you want to use the tool in Chrome incognito mode, navigate to the extension and click "allow in incognito".</span></span>
    
3. <span data-ttu-id="6eb73-129">Navegue a la página de publicación de SharePoint clásica en SharePoint Online que le gustaría usar para revisar.</span><span class="sxs-lookup"><span data-stu-id="6eb73-129">Navigate to the SharePoint classic publishing page on SharePoint Online that you would like to review.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="6eb73-p106">Nos hemos permitido para "carga retrasada" de elementos en las páginas; por lo tanto, la **herramienta no se detiene automáticamente**. Si desea detener la colección, puede hacer clic en **Detener**. (Esto es por diseño que abarquen para todos los escenarios de carga de página)</span><span class="sxs-lookup"><span data-stu-id="6eb73-p106">We have allowed for "delay loading" of items on pages; therefore, the **tool will not stop automatically**. Should you wish to stop collection, you can click **Stop**. (This is by design to cater for all page load scenarios)</span></span> 
  
<span data-ttu-id="6eb73-p107">Antes de hacer clic en **Detener**, asegúrese de que los datos de seguimiento de red están completas. En caso contrario, tendrá un seguimiento parcial.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p107">Before you click **Stop**, make sure that the network trace data is complete. Otherwise, you will have a partial trace.</span></span> 
  
<span data-ttu-id="6eb73-p108">Además, la herramienta es una extensión de explorador y apertura de varias fichas o windows solo permitirá una instancia activa de la herramienta para ejecutarse a la vez. Se trata de una limitación de extensiones en el explorador.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p108">Additionally, the tool is a Browser Extension, and opening multiple tabs or windows will only allow one active instance of the tool to be run at one time. This is a limitation of extensions in the browser.</span></span> 
  
4. <span data-ttu-id="6eb73-137">Haga clic en el logotipo de extensión</span><span class="sxs-lookup"><span data-stu-id="6eb73-137">Click on the Extension logo</span></span> ![Diagnósticos de página para el logotipo de SharePoint](media/60a3e44d-1b59-483f-b50f-d580044d921a.png) <span data-ttu-id="6eb73-139">para cargar la herramienta y se presentarán con la siguiente ventana emergente de extensión:</span><span class="sxs-lookup"><span data-stu-id="6eb73-139">to load the tool and you will be presented with the following extension popup window:</span></span> 
    
    ![Herramienta de diagnóstico de página de elemento emergente](media/b01fa00e-c5f3-4c37-91f2-6edd096cf87e.png)
  
    <span data-ttu-id="6eb73-141">Iniciar y detener follow operaciones comenzará el concepto básico de cuando haga clic en Inicio que volverá a cargar la página y la colección.</span><span class="sxs-lookup"><span data-stu-id="6eb73-141">Start and stop operations follow the basic concept of when you click start the page will reload and collection will begin.</span></span>
    
5. <span data-ttu-id="6eb73-p109">El primer vínculo es el vínculo **acerca de** y proporciona instrucciones generales y obtener información detallada acerca de la herramienta que incluye un vínculo a este artículo. También incluye un vínculo directo a las recomendaciones de rendimiento de SharePoint, un aviso de terceros y una opción para proporcionar comentarios sobre la herramienta.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p109">The first link is the **About** link and will provide general guidance and details regarding the tool including a link back to this article. It also includes a direct link to SharePoint Performance recommendations, a Third Party notice and an option to provide feedback about the tool.</span></span> 
    
6. <span data-ttu-id="6eb73-p110">Revise la información **identificador de correlación, SPRequestDuration, SPIISLatency** **, hora y dirección URL de carga de página** . (Esta sección es informativa y puede usarse para fines unos).</span><span class="sxs-lookup"><span data-stu-id="6eb73-p110">Review the **Correlation ID, SPRequestDuration, SPIISLatency** **, Page load time and URL** information. (This section is informational and can be used for a few purposes.)</span></span> 
    
  - <span data-ttu-id="6eb73-146">**CorrelationID** es un elemento importante cuando se trabaja con los equipos de soporte técnico de Microsoft, tal como les permite extraer datos de diagnóstico adicionales.</span><span class="sxs-lookup"><span data-stu-id="6eb73-146">**CorrelationID** is an important element when working with the Microsoft Support Teams as it allows them to pull additional diagnostic data.</span></span> 
    
  - <span data-ttu-id="6eb73-p111">**SPRequestDuration** es la hora del servidor necesario para procesar la página. Si este tiempo es larga, no necesariamente significa que el servidor estaba realizando mal, pero también puede reflejar el número de llamadas y cargar inserta por la página en el servidor, por ejemplo, navegación estructural, imágenes de gran tamaño, una gran cantidad de llamadas a la API podría contribuir a más tiempo del servidor .</span><span class="sxs-lookup"><span data-stu-id="6eb73-p111">**SPRequestDuration** is the server time taken to process the page. If this time is long, it does not necessarily mean that the server was performing badly but can also reflect the number of calls and load pushed by the page to the server e.g. Structural Navigation, large images, lots of API calls could all contribute to longer server time.</span></span> 
    
  - <span data-ttu-id="6eb73-p112">**SPIISLatency** es el tiempo en milisegundos que se llevan a cabo en el servidor Web Front-End cuando se recibe la solicitud para cargar la página. Este es un indicador de latencia para iniciar el procesamiento de la página y no incluye el tiempo necesario para que la aplicación web responder.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p112">**SPIISLatency** is the time in milliseconds taken on the Web Front End Server when it receives the request to load the page. This is an indicator of latency to start processing the page and does not include the time taken for the web application to respond.</span></span> 
    
  - <span data-ttu-id="6eb73-p113">**Tiempo de carga de página** es el tiempo registrado por la página desde el momento de la solicitud a la hora de la respuesta se ha recibido y leídos por el explorador. Tiempo adicional se ve afectada por el rendimiento del equipo y el tiempo que tarda el explorador cargar.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p113">**Page load time** is the time recorded by the page from the time of the request to the time the response was received and read by the browser. Any additional time is affected by the performance of the computer and the time it takes for the browser to load.</span></span> 
    
  - <span data-ttu-id="6eb73-153">La **dirección URL** (localizador uniforme de recursos) es la dirección web de la página actual.</span><span class="sxs-lookup"><span data-stu-id="6eb73-153">The **URL** (Uniform Resource Locator) is the web address of the current page.</span></span> 
    
7. <span data-ttu-id="6eb73-154">La **ficha diagnóstico** mostrará una lista de las reglas y si cualquiera de ellos están marcados con un color rojo ![entre](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), a continuación, hay problemas identificados en la página.</span><span class="sxs-lookup"><span data-stu-id="6eb73-154">The **Diagnostic tab** will list the rules and if any of them are marked with a red ![Cross](media/9859ac84-be43-4eae-984c-e0e827f5a228.png), then there are issues identified on the page.</span></span>
    
    <span data-ttu-id="6eb73-p114">Cada regla tiene su propio vínculo "más información" Si hace clic en él cuando es de color rojo. Que le llevará a los detalles detrás de esa regla y cómo corregir el problema.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p114">Each rule has its own "more info" link if you click on it when it is red. That will take you to the details behind that rule and how to remediate the issue.</span></span>
    
    ![Diagnósticos rojo - regla open](media/1598f0f7-3103-4613-8787-dfec6fffd40a.png)
  
1. <span data-ttu-id="6eb73-158">Comprobar el usuario que ejecute como estándar</span><span class="sxs-lookup"><span data-stu-id="6eb73-158">Check Running as Standard User</span></span>
  
<span data-ttu-id="6eb73-p115">Comprobar el rendimiento de la página no se debe realizar cuando inicia sesión como una cuenta de servicio, el administrador o el Administrador de colección de sitios, es decir, una cuenta con privilegios elevados. Funcionalidad y secuencias de comandos adicionales se carga específicamente para esos tipos de cuentas y no proporcionará una representación verdadera del rendimiento de la página.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p115">Checking page performance should not be performed when logged in as a Service Account, Administrator or Site Collection Administrator i.e. an account with elevated privileges. Additional scripts and functionality is loaded specifically for those types of accounts and will not provide a true representation of the page performance.</span></span>
    
2. <span data-ttu-id="6eb73-161">Solicitudes de verificación para SharePoint</span><span class="sxs-lookup"><span data-stu-id="6eb73-161">Check Requests to SharePoint</span></span>
  
<span data-ttu-id="6eb73-p116">Se debe limitar la cantidad de datos y las solicitudes realizadas al servidor como una página sobrecargada experimentará un rendimiento deficiente. Esta comprobación comprueba el número de solicitudes que se realizan en SharePoint y le aconseje cuando las solicitudes de superar los 6 solicitudes. La mayoría de las solicitudes deben se almacena en caché y, por tanto, no se llama para cada carga de página. Memoria caché debe ser el programa de instalación y utilizada durante al menos 15 minutos para reducir la cantidad de llamadas a una página por cada usuario. Éste es un problema común y en la mayoría de los casos sólo cambian los datos diariamente pero la página comprueba y recupera los datos cada vez para cada página para cada usuario que a menudo no es necesario.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p116">The amount of data and requests made to the server should be limited as an overloaded page will experience poor performance. This check verifies the number of requests being made to SharePoint and will advise when the requests exceed 6 requests. Most requests should be cached and therefore not called for every page load. Cache should be setup and utilized for at least 15 minutes to reduce the amount of calls to a page by each and every User. This is a common problem and in most cases data only changes daily but the page checks and fetches data each time for each page for each user which is often unnecessary.</span></span>
    
3. <span data-ttu-id="6eb73-167">Comprobar el uso de las CDN</span><span class="sxs-lookup"><span data-stu-id="6eb73-167">Check using CDNs</span></span>
  
<span data-ttu-id="6eb73-p117">Redes de distribución de contenido se han proporcionado por Microsoft y a los que hace referencia a que estos son las redes de entrega de contenido en línea SharePoint. Hay varios tipos de, así como los distintos servicios CDN al igual que las CDN de SharePoint y, a continuación, las CDN en Azure. [Use las siguientes instrucciones](https://go.microsoft.com/fwlink/?linkid=873250).</span><span class="sxs-lookup"><span data-stu-id="6eb73-p117">Content Delivery networks have been provided by Microsoft and the ones referred to here are the SharePoint Online Content Delivery Networks. There are multiple types available as well as different CDN services like SharePoint CDNs and then CDNs in Azure. [Use the following guidance](https://go.microsoft.com/fwlink/?linkid=873250).</span></span>
    
4. <span data-ttu-id="6eb73-171">Verificación de tamaños de imagen grande</span><span class="sxs-lookup"><span data-stu-id="6eb73-171">Check for Large Image Sizes</span></span>
  
<span data-ttu-id="6eb73-p118">Imágenes deben ser optimizadas para web mediante el uso de tipos de web mejor como PNG. Representaciones de imágenes también debe utilizarse y está disponibles en SharePoint directamente. Imágenes / representaciones de imágenes mayores que 100kb se marcará como no optimizada para web. [Use las siguientes instrucciones para optimizar el imágenes](https://go.microsoft.com/fwlink/?linkid=873251).</span><span class="sxs-lookup"><span data-stu-id="6eb73-p118">Images should be optimized for web by utilizing better web types like PNG. Image renditions should also be utilized and is available in SharePoint directly. Images / image renditions larger than 100kb will be highlighted as not optimized for web. [Use the following guidance for optimizing images](https://go.microsoft.com/fwlink/?linkid=873251).</span></span>
    
5. <span data-ttu-id="6eb73-176">Protección para la navegación estructural</span><span class="sxs-lookup"><span data-stu-id="6eb73-176">Check for Structural Navigation</span></span>
  
<span data-ttu-id="6eb73-p119">Navegación estructural se diseñó originalmente para su uso en SharePoint local donde se podría utilizar la memoria caché de objetos. Navegación estructural no se recomienda para su uso en SharePoint Online y se debe cambiar a navegación administrada o un proveedor personalizado. [Usar las siguientes instrucciones para optimizar la navegación.](https://go.microsoft.com/fwlink/?linkid=873247)</span><span class="sxs-lookup"><span data-stu-id="6eb73-p119">Structural Navigation was originally designed for use in SharePoint on-Premises where object cache could be utilized. Structural Navigation is not recommended for use in SharePoint Online and should be changed to Managed Navigation or a Custom Provider. [Use the following guidance for optimizing navigation.](https://go.microsoft.com/fwlink/?linkid=873247)</span></span>
    
6. <span data-ttu-id="6eb73-180">Verificación de WebPart CBQ (CBQ - elemento Web consulta de contenido)</span><span class="sxs-lookup"><span data-stu-id="6eb73-180">Check for CBQ WebPart (CBQ - Content by Query WebPart)</span></span>
  
<span data-ttu-id="6eb73-p120">El elemento Web consulta de contenido genera una alta carga SQL medida que pasa por todos los elementos de la consulta para cada carga de página, para cada usuario. A diferencia de una instalación local, no hay ninguna caché disponible para limitar el número de consultas que sea necesario para rellenar este elemento Web. Como tal, CBQ se ejecuta lentamente y afecta al rendimiento general de la página que es la razón por la que no se debe utilizar. Utilice el elemento Web de búsqueda de contenido (CSWP) como un reemplazo para el elemento Web consulta de contenido. [Use las directrices siguientes relacionadas con el elemento Web de búsqueda de contenido](https://go.microsoft.com/fwlink/?linkid=873245).</span><span class="sxs-lookup"><span data-stu-id="6eb73-p120">The Content by Query WebPart generates a high SQL load as it traverses all items in the query for each and every page load, for each User. Unlike an on-Premises installation, there is no cache available to limit the number of queries needed to populate this WebPart. As such CBQ performs slowly and impacts overall page performance which is why it should not be utilized. Please use the Content Search WebPart (CSWP) as the replacement for the Content Query WebPart. [Use the following guidance related to the Content Search WebPart](https://go.microsoft.com/fwlink/?linkid=873245).</span></span>
    
8. <span data-ttu-id="6eb73-p121">La **ficha seguimiento de red** proporciona \*\*\* información detallada acerca de las solicitudes para crear la página, así como las respuestas recibidas. El rendimiento de cada solicitud y respuesta son codificación por colores en función de su impacto en el rendimiento general de la página, es decir, verde \< 500 ms, amarilla 500 ms-1.000 ms y rojo \> 1000ms.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p121">The **Network Trace tab** provides **** detailed information about the requests to build the page as well as the responses received. The performance of each request and response are color coded based on their impact on the overall page performance i.e. Green \< 500ms, Yellow 500-1000ms and Red \> 1000ms.</span></span> 
    
    <span data-ttu-id="6eb73-188">En esta ficha hay una exportación a opción de JSON si desea descargar y compartir los detalles de solicitud y respuesta.</span><span class="sxs-lookup"><span data-stu-id="6eb73-188">On this tab there is an Export to JSON option should you wish to download and share the request and response details.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="6eb73-189">Mantenga el mouse sobre la dirección URL abreviada para ver la dirección URL completa.</span><span class="sxs-lookup"><span data-stu-id="6eb73-189">Hover over the shortened URL to view the complete URL.</span></span> 
  
    ![Seguimiento de red](media/3cfede99-7d31-4041-888d-7bbc275cadc2.png)
  
    <span data-ttu-id="6eb73-191">En esta imagen el color rojo es la propia página y que se muestra siempre rojo a menos que la página se carga en \< 1000ms (es decir, de 1 segundo).</span><span class="sxs-lookup"><span data-stu-id="6eb73-191">In this image the Red is the page itself and that will always show red unless the page loads in \< 1000ms (i.e. 1 second).</span></span>
    
    <span data-ttu-id="6eb73-p122">En algunos casos, *no habrá ningún indicador de color o de tiempo debido a que los elementos estén ya en caché por el explorador* . Para probar correctamente, abra la página, desactive la memoria caché del explorador y, a continuación, haga clic en **Iniciar** como que va a forzar la carga de una página "pasiva" y ser un reflejo de la carga de página inicial es true. Esto debe, a continuación, compararse a la carga de página "caliente" también le ayudará a determinar qué elementos se que se almacenan en caché en la página.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p122">In some cases  *there will be no time or color indicator because the items have already been cached by the browser*  . To test this correctly, open the page, clear browser cache, and then click **Start** as that will force a "cold" page load and be a true reflection of the initial page load. This should then be compared to the "warm" page load as that will also help determine what items are being cached on the page.</span></span> 
    
9. <span data-ttu-id="6eb73-p123">Si desea compartir estos detalles o información con sus desarrolladores o una persona de soporte técnico, a continuación, puede hacer clic en "Exportar a JSON" según la imagen anterior y que descargará los resultados. Tenga en cuenta que el archivo, a continuación, se puede abrir con un visor de archivos JSON.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p123">If you wish to share these details or information with your developers or a Support person then you can click "Export to JSON" as per the above image and that will download the results. Please note that the file can then be opened using a JSON file viewer.</span></span>
    
    > [!IMPORTANT]
    > <span data-ttu-id="6eb73-197">Estos resultados contendrá la dirección de URL y, por tanto, contiene PII (información de identificación personal) y debe seguir las directrices de la compañía antes de distribuir dicha información.</span><span class="sxs-lookup"><span data-stu-id="6eb73-197">These results will contain the URL's and therefore contains PII (Personally Identifiable Information) and you should follow your Company guidelines before distributing that information.</span></span> 
  
10. <span data-ttu-id="6eb73-p124">Hemos incluido una **característica de nivel de soporte técnico de Microsoft** que sólo se utiliza cuando se trabaja directamente en un caso de soporte técnico para obtener un rendimiento. Uso de esta característica no le proporcionará ninguna ventaja cuando se usa sin nuestro equipo de soporte técnico. De hecho hará que la página realizar mucho más lentamente y puede considerarse uso continuado de la característica de uso "incorrecto" del servicio. No hay ninguna información adicional cuando se utiliza esta característica en la herramienta tal y como se agrega la información adicional para el registro en el servicio.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p124">We have included a **Microsoft Support level feature** that should only be utilized when working directly on a Support Case for performance. Utilizing this feature will provide no benefit to you when used without our Support team. It will in fact make the page perform significantly slower and continued use of the feature may be considered "misuse" of the service. There is no additional information when using this feature in the tool as the additional information is added to the logging in the service.</span></span> 
    
    <span data-ttu-id="6eb73-p125">Ningún cambio es visible, excepto en que se le notificará que se ha habilitado y se degradará significativamente el rendimiento de la página por 2 - 3 veces un rendimiento más lento mientras que está habilitado. Sólo será relevante para la página determinada y esa sesión activa. Por este motivo, debe usarse con moderación y sólo cuando activamente ocupado con nuestro equipo de soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p125">No change is visible except that you will be notified that you have enabled it and your page performance will be significantly degraded by 2-3 times slower performance whilst that is enabled. It will only be relevant for the particular page and that active session. For this reason, this should be used sparingly and only when actively engaged with our Support Team.</span></span>
    
    <span data-ttu-id="6eb73-p126">Para habilitar la característica por favor, abra la herramienta y use ALT-MAYÚS-L que, a continuación, se mostrará "Habilitar el registro de nivel de soporte técnico". Haga clic en que la casilla de verificación y, a continuación, haga clic en inician para volver a cargar la página y generar el registro detallado para soporte técnico analizar.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p126">To enable the feature please open the tool and use ALT-Shift-L which will then display "Enable support level logging". Click the checkbox and then click start to reload the page and generate verbose logging for Support to analyze.</span></span>
    
    ![Habilitada la opción de soporte técnico](media/ddef47de-8593-4b28-9346-eb48ebf6cdab.png)
  
    <span data-ttu-id="6eb73-p127">Un elemento importante para esto es el CorrelationID como el equipo de soporte técnico, a continuación, utilizará ese número para extraer la información necesaria. Por favor, copie el CorrelationID y proporcione a soporte técnico al no pueden llevar a cabo el trabajo necesario sin el identificador completo.</span><span class="sxs-lookup"><span data-stu-id="6eb73-p127">An important element for this is the CorrelationID as the Support team will then utilize that number to extract the information needed. Please copy the CorrelationID and provide that to Support as they cannot perform the required work without the complete ID.</span></span>
    
