---
title: Configurar la búsqueda para Office 365 Multi-Geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información sobre cómo configurar la búsqueda en un entorno multigeográfico.
ms.openlocfilehash: 5a06b30e7850a23ff6443eb8b5b2e9e14850a7db
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931839"
---
# <a name="configure-search-for-office-365-multi-geo"></a>Configurar la búsqueda para Office 365 Multi-Geo

En un entorno multigeográfico, cada ubicación geográfica tiene su propio índice de búsqueda y centro de búsqueda. Cuando un usuario realiza una búsqueda, se efectúa una distribución ramificada de la consulta a todos los índices y los resultados devueltos se combinan.

Por ejemplo, un usuario de una ubicación geográfica puede realizar búsquedas de contenido almacenado en otra ubicación geográfica o contenido de un sitio de SharePoint que está restringido a otra ubicación geográfica. Si el usuario tiene acceso a este contenido, la búsqueda mostrará el resultado.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>¿Qué clientes de búsqueda trabajan en un entorno multigeográfico?

Estos clientes pueden devolver resultados de todas las ubicaciones geográficas:

-   OneDrive para la Empresa

-   Delve

-   Página principal de SharePoint

-   Centro de búsqueda

-   Aplicaciones de búsqueda personalizada que usan la API de SharePoint Search

### <a name="onedrive-for-business"></a>OneDrive para la Empresa

En cuanto se haya configurado el entorno multigeográfico, los usuarios que busquen en OneDrive obtendrán resultados de todas las ubicaciones geográficas.

### <a name="delve"></a>Delve

En cuanto se haya configurado el entorno multigeográfico, los usuarios que busquen en Delve obtendrán resultados de todas las ubicaciones geográficas.

La fuente de Delve y la tarjeta de perfil solo muestran vistas previas de los archivos almacenados en la ubicación central. Para los archivos que se almacenan en ubicaciones satélite, se muestra el icono del tipo de archivo en su lugar.

### <a name="the-sharepoint-home-page"></a>Página principal de SharePoint

En cuanto se haya configurado el entorno multigeográfico, los usuarios verán noticias, sitios seguidos y recientes desde varias ubicaciones geográficas en su página principal de SharePoint. Si usan el cuadro de búsqueda en la página principal de SharePoint, obtendrán resultados combinados desde varias ubicaciones geográficas.

### <a name="the-search-center"></a>Centro de búsqueda

Cuando se haya configurado el entorno multigeográfico, cada Centro de búsqueda sigue mostrando solo los resultados de su propia ubicación geográfica. Los administradores deben [cambiar la configuración de cada Centro de búsqueda](#_Set_up_a_1) para obtener resultados de todas las ubicaciones geográficas. Después, los usuarios que realicen búsquedas en el Centro de búsqueda obtendrán resultados de todas las ubicaciones geográficas.

### <a name="custom-search-applications"></a>Aplicaciones de búsqueda personalizada

Como de costumbre, las aplicaciones de búsqueda personalizada interactúan con los índices de búsqueda mediante las API REST de SharePoint Search existentes. Para obtener resultados de todas o algunas de las ubicaciones geográficas, la aplicación tiene que [llamar a la API e incluir los nuevos parámetros de consulta multigeográfica](#_Get_custom_search) en la solicitud. Esto desencadena la distribución ramificada de la consulta a todas las ubicaciones geográficas.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>¿En qué se diferencia la búsqueda en un entorno multigeográfico?

Algunas características de búsqueda con las que tal vez esté familiarizado, funcionan de forma distinta en un entorno multigeográfico.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Característica</strong></th>
<th align="left"><strong>Funcionamiento</strong></th>
<th align="left"><strong>Solución alternativa</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Resultados promocionados</td>
<td align="left">Puede crear reglas de consulta con resultados promocionados a diferentes niveles: para todo el inquilino, para una colección de sitios o para un sitio. En un entorno multigeográfico, defina los resultados promocionados a nivel de espacio empresarial para promover los resultados a los centros de búsqueda en todas las ubicaciones geográficas. Si solo quiere promover los resultados del Centro de búsqueda que se encuentra en la ubicación geográfica del sitio o la colección de sitios, defina los resultados en el nivel de colección de sitios o de sitio. Estos resultados no se promueven en otras ubicaciones geográficas.</td>
<td align="left">Si no necesita resultados promocionados distintos por ubicación geográfica, por ejemplo, diferentes reglas de viaje, se recomienda definir los resultados promocionados en el nivel de espacio empresarial.</td>
</tr>
<tr class="even">
<td align="left">Refinadores de búsquedas</td>
<td align="left">La búsqueda devuelve refinadores de todas las ubicaciones geográficas de un espacio empresarial y luego los agrega. La agregación es la mejor posible, lo que significa que puede que los recuentos de refinadores no sean exactos al 100%. Para la mayoría de los escenarios basado en búsquedas esta precisión es suficiente. </td>
<td align="left">En aplicaciones basadas en búsquedas que dependen de la exhaustividad del refinador, consulte cada ubicación geográfica por separado.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">La búsqueda multigeográfica no admite la creación dinámica de cubos para refinadores numéricos.</td>
<td align="left">Use el parámetro <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">“Discretize”</a> para refinadores numéricos.</td>
</tr>
<tr class="even">
<td align="left">Identificadores de documento</td>
<td align="left">Si está desarrollando una aplicación basada en búsquedas que depende de los identificadores de documento, tenga en cuenta que los identificadores de documento en un entorno multigeográfico no son únicos en todas las ubicaciones geográficas, son únicos por ubicación geográfica.</td>
<td align="left">Hemos agregado una columna que identifica la ubicación geográfica. Utilice esta columna para lograr unicidad. Esta columna se denomina "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">Número de resultados</td>
<td align="left">La página de resultados de búsqueda muestra los resultados combinados de las ubicaciones geográficas, pero no es posible ver más allá de 500 resultados.</td>
<td align="left"></td>
</tr>
<tr class="even">
<td align="left">Búsqueda híbrida</td>
<td align="left">En un entorno de SharePoint híbrido con <a href="https://docs.microsoft.com/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint">búsqueda de nube híbrida</a>, el contenido local se agrega al índice de Office 365 de la ubicación central.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>¿Qué no es compatible con la búsqueda en un entorno multigeográfico?

Algunas características de búsqueda con las que tal vez esté familiarizado, no se admiten en un entorno multigeográfico.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Característica de búsqueda</strong></th>
<th align="left"><strong>Nota</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Autenticación solo de aplicación</td>
<td align="left">La autenticación solo de aplicación (acceso con privilegios desde servicios) no se admite en la búsqueda multigeográfica.</td>
</tr>
<tr class="even">
<td align="left">Usuarios invitados</td>
<td align="left">Los usuarios invitados solo obtienen resultados de la ubicación geográfica desde la que buscan.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>¿Cómo funciona la búsqueda en un entorno multigeográfico?

Todos los clientes de búsqueda usan la API REST de SharePoint Search existente para interactuar con los índices de búsqueda.

<img src="media/configure-search-for-multi-geo-image1-1.png" />

1. Un cliente de búsqueda llama al punto de conexión de REST de búsqueda con la propiedad EnableMultiGeoSearch= true.
2. La consulta se envía a todas las ubicaciones geográficas del espacio empresarial.
3. Los resultados de búsqueda de cada ubicación geográfica se combinan y clasifican.
4. El cliente obtiene resultados unificados.



<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Observe que no combinamos los resultados de búsqueda hasta que hemos recibido los resultados de todas las ubicaciones geográficas. Esto significa que las búsquedas multigeográficas tienen latencia adicional con respecto a las búsquedas en un entorno de una sola ubicación geográfica.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Obtener un Centro de búsqueda que muestre los resultados de todas las ubicaciones geográficas

Cada Centro de búsqueda tiene varios sectores verticales y hay que configurar individualmente cada sector vertical.

1.  Asegúrese de realizar estos pasos con una cuenta que tenga permiso para editar la página de resultados de búsqueda y el elemento web de resultados de búsqueda.

2.  Navegue a la página de resultados de búsqueda (vea la [lista](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de páginas de resultados de búsqueda).

3.  Seleccione el sector vertical que quiere configurar, haga clic en el icono de engranaje **Configuración** de la esquina superior derecha y luego en **Editar página**. La página de resultados de búsqueda se abre en modo de edición.

     ![](media/configure-search-for-multi-geo-image2.png)
1.  En el elemento web Resultados de búsqueda, mueva el puntero a la esquina superior derecha del elemento web, haga clic en la flecha y, a continuación, haga clic en **Editar elemento web** en el menú. El panel de herramientas del elemento web de resultados de búsqueda se abrirá debajo de la cinta en la parte superior derecha de la página. ![](media/configure-search-for-multi-geo-image3.png)

1.  En la sección **Configuración** del panel de herramientas del elemento web de resultados de búsqueda, en **Configuración de control de resultados**, seleccione **Show Multi-Geo results** (Mostrar resultados multigeográficos) para que el elemento web de resultados de la búsqueda muestre los resultados de todas las ubicaciones geográficas.

2.  Haga clic en **Aceptar** para guardar los cambios y cierre el panel de herramientas del elemento web.

3.  Para comprobar los cambios realizados en el elemento web de resultados de búsqueda, haga clic en **Proteger** en la pestaña de página del menú principal.

4.  Publique los cambios mediante el vínculo incluido en la nota de la parte superior de la página.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Obtener aplicaciones de búsqueda personalizada que muestren los resultados de todas o algunas de las ubicaciones geográficas

Las aplicaciones de búsqueda personalizada obtienen resultados de todas o algunas de las ubicaciones geográficas especificando parámetros de consulta con la solicitud a la API REST de SharePoint Search. En función de los parámetros de consulta, se efectúa una distribución ramificada de la consulta a todas o a algunas de las ubicaciones geográficas. Por ejemplo, si solo tiene que consultar un subconjunto de las ubicaciones geográficas para encontrar información relevante, puede controlar la distribución ramificada a solo estas. Si la solicitud se realiza correctamente, la API REST de SharePoint Search devuelve datos de respuesta.

**Requisito**

Para cada ubicación geográfica, debe asegurarse de que se ha concedido a todos los usuarios de la organización el nivel de permisos de **lectura** para el sitio web raíz (por ejemplo, contoso**APAC**.sharepoint.com/ y contoso**UE**.sharepoint.com/). [Más información sobre permisos](https://support.office.com/es-ES/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).

### <a name="query-parameters"></a>Parámetros de consulta

EnableMultiGeoSearch: valor booleano que especifica si se efectuará una distribución ramificada de la consulta a los índices de otras ubicaciones geográficas del inquilino multigeográfico. Establézcalo en **true** para efectuar una distribución ramificada de la consulta o en **false** para no hacerlo. El valor predeterminado es **False**. Si no incluye este parámetro, no se efectúa una distribución ramificada de la consulta a otra ubicación geográfica. Si usa el parámetro en un entorno que no es multigeográfico, se ignorará el parámetro.

ClientType: es una cadena. Escriba un nombre de cliente único para cada aplicación de búsqueda. Si no incluye este parámetro, no se efectúa una distribución ramificada de la consulta a otra ubicación geográfica.

MultiGeoSearchConfiguration: lista opcional de las ubicaciones geográficas del inquilino multigeográfico que se distribuyen cuando **EnableMultiGeoSearch** es **true**. Si no incluye este parámetro o lo deja en blanco, se efectúa una distribución ramificada de la consulta a todas las ubicaciones geográficas. Para cada ubicación geográfica, escriba los elementos siguientes, con formato JSON:

<table>
<thead>
<tr class="header">
<th align="left">Elemento</th>
<th align="left">Descripción</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">DataLocation</td>
<td align="left">Ubicación geográfica, por ejemplo, NAM.</td>
</tr>
<tr class="even">
<td align="left">EndPoint</td>
<td align="left">Punto de conexión al que conectarse; por ejemplo, https://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">GUID del origen de resultados, por ejemplo, B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

Si omite DataLocation o EndPoint, o si una DataLocation se duplica, la solicitud no se realiza. [Puede obtener información sobre el punto de conexión de las ubicaciones geográficas de un espacio empresarial con Microsoft Graph](https://docs.microsoft.com/es-ES/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Datos de respuesta

MultiGeoSearchStatus: se trata de una propiedad que devuelve la API de SharePoint Search en respuesta a una solicitud. El valor de la propiedad es una cadena y proporciona la información siguiente sobre los resultados que devuelve la API de SharePoint Search:

<table>
<thead>
<tr class="header">
<th align="left">Valor</th>
<th align="left">Descripción</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Full</td>
<td align="left">Resultados completos de <strong>todas</strong> ubicaciones geográficas.</td>
</tr>
<tr class="even">
<td align="left">Partial</td>
<td align="left">Resultados parciales de una o varias ubicaciones geográficas. Los resultados están incompletos debido a un error transitorio.</td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Consultar con el servicio REST

Con una solicitud GET, especifica los parámetros de consulta en la dirección URL. Con una solicitud de POST, pasa los parámetros de consulta del cuerpo en el formato de notación de objetos JavaScript (JSON).


#### <a name="request-headers"></a>Encabezados de solicitud

<table>
<thead>
<tr class="header">
<th align="left">Nombre</th>
<th align="left">Valor</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Content-Type</td>
<td align="left">application/json;odata=verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Ejemplo de distribución ramificada de una solicitud GET a **todas** las ubicaciones geográficas

https:// \<espacio empresarial\>/\_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my\_client\_id'

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Ejemplo de solicitud GET para efectuar una distribución ramificada en **algunas** ubicaciones geográficas

https:// \<tenant\>/\_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'

> [!NOTE]
> Las comas y los dos puntos de la lista de ubicaciones geográficas de la propiedad MultiGeoSearchConfiguration van precedidas por el carácter **barra diagonal inversa**. Esto se debe a que las solicitudes GET usan dos puntos para separar las propiedades y comas para separar los argumentos de las propiedades. Sin la barra diagonal inversa como carácter de escape, la propiedad MultiGeoSearchConfiguration se interpreta de forma errónea.

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Ejemplo de distribución ramificada de una solicitud POST a **todas** las ubicaciones geográficas

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Ejemplo de distribución ramificada de una solicitud POST a **algunas** ubicaciones geográficas


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

### <a name="query-using-csom"></a>Consultar con CSOM

Ejemplo de distribución ramificada de una consulta CSOM a **todas** las ubicaciones geográficas:

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

