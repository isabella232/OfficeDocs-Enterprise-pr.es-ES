---
title: Configurar búsqueda de OneDrive de negocios Multi-Geo
ms.author: tlarsen
author: tklarsen
manager: arnek
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Obtenga información acerca de cómo configurar la búsqueda en un entorno multi-geo.
ms.openlocfilehash: 5cf155c2c5bd2e27a54d84c4d5411e5b1afce568
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="configure-search-for-onedrive-for-business-multi-geo"></a>Configurar búsqueda de OneDrive de negocios Multi-Geo

En un entorno Multi-Geo SharePoint Online (SPO), una organización puede tener un arrendatario de Office 365, pero almacenar su contenido de SharePoint en varias ubicaciones geográficas - una ubicación central y una o más ubicaciones geo de satélite.

Cada ubicación geográfica tiene su propio centro de búsqueda e índices de búsqueda. Cuando un usuario realiza una búsqueda, la consulta se colocadas en abanico para todos los índices y se combinan los resultados devueltos.

Por ejemplo, puede buscar un usuario en una ubicación geográfica para el contenido almacenado en otra ubicación geográfica, o contenido en un sitio de SharePoint que está restringido a una ubicación geográfica diferente. Si el usuario tiene acceso a este contenido, la búsqueda mostrará el resultado.

## <a name="which-search-clients-work-in-a-multi-geo-environment"></a>¿En un entorno Multi-Geo que buscar trabajo de los clientes?

Estos clientes pueden devolver resultados desde todas las ubicaciones de geo:

-   OneDrive for Business

-   Delve

-   La página principal de SharePoint

-   El centro de búsqueda

-   Aplicaciones de búsqueda personalizadas que utilizan la API de búsqueda de SharePoint

### <a name="onedrive-for-business"></a>OneDrive for Business

Tan pronto como se ha configurado el entorno Multi-Geo, los usuarios que busque en OneDrive Obtén resultados de todas las ubicaciones de geo.

### <a name="delve"></a>Delve

Tan pronto como se ha configurado el entorno Multi-Geo, los usuarios que buscar en Delve Obtén resultados de todas las ubicaciones de geo.

La fuente de Delve y la tarjeta de perfil sólo mostrar vistas previas de archivos que se almacenan en la ubicación **central** . Para los archivos que se almacenan en ubicaciones de satélite geo, el icono del tipo de archivo se muestra en su lugar.

### <a name="the-sharepoint-home-page"></a>La página principal de SharePoint

Tan pronto como se ha configurado el entorno Multi-Geo, los usuarios verán noticias, sitios recientes y seguidos desde varias ubicaciones geo en su página de inicio de SharePoint. Si utiliza el cuadro de búsqueda en la página principal de SharePoint, obtendrán resultados combinados desde varias ubicaciones geo.

### <a name="the-search-center"></a>El centro de búsqueda

Después el Multi-Geo entorno se ha configurado, cada centro de búsqueda continúa para mostrar únicamente los resultados de su propia ubicación geográfica. Administradores deben [cambiar la configuración de cada centro de búsqueda](#_Set_up_a_1) para obtener resultados de todas las ubicaciones de geo. Posteriormente, los usuarios que en el centro de búsqueda de búsqueda Obtén resultados desde todas las ubicaciones de geo.

### <a name="custom-search-applications"></a>Aplicaciones de búsqueda personalizadas

Como de costumbre, aplicaciones de búsqueda personalizadas interactúan con los índices de búsqueda utilizando las API existentes de resto de búsqueda de SharePoint. Para obtener resultados de todas o algunas ubicaciones geo, la aplicación debe [llamar a la API e incluir los nuevos parámetros de consulta de Multi-Geo](#_Get_custom_search) en la solicitud. Esto desencadena un ventilador fuera de la consulta a todas las ubicaciones de geo.

## <a name="whats-different-about-search-in-a-multi-geo-environment"></a>¿Qué es diferente acerca de búsqueda en un entorno Multi-Geo?

Algunas características de búsqueda, es posible que esté familiarizado con, funcionan de forma diferente en un entorno Multi-Geo.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Característica</strong></th>
<th align="left"><strong>¿Cómo funciona</strong></th>
<th align="left"><strong>Solución alternativa</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Resultados de la promoción</td>
<td align="left">Puede crear reglas de consulta con resultados promocionadas en distintos niveles: para el inquilino todo, para una colección de sitios o para un sitio. En un entorno Multi-Geo, definir resultados promovidos en el nivel de <strong>inquilinos</strong> si desea promover los resultados a los centros de búsqueda en <strong>todas las</strong> ubicaciones de geo. Si usted <strong>sólo</strong> desea promover los resultados en el centro de búsqueda que está en la ubicación geográfica de la colección de sitios o el sitio, definir los resultados en el nivel de <strong>colección de sitios</strong> o <strong>sitio</strong> .</td>
<td align="left">Si no necesita diferentes resultados promovidos por ubicación geográfica, por ejemplo diferentes reglas para viajar, recomendamos definir promover los resultados en el nivel de inquilinos.</td>
</tr>
<tr class="even">
<td align="left">Refinadores de búsqueda</td>
<td align="left">La búsqueda devuelve los refinadores de todas las ubicaciones geo de un arrendatario y luego los agrega. La agregación es un mayor esfuerzo, lo que significa que los recuentos de refinador podrían no ser exactos al 100%. Para la mayoría de los escenarios controlados por la búsqueda de esta precisión es suficiente.</td>
<td align="left">Para aplicaciones orientadas a la búsqueda que dependen de su integridad refinador, consultar cada ubicación geográfica independientemente sin necesidad de utilizar múltiples Geo fan-out.</td>
</tr>
<tr class="odd">
<td align="left"></td>
<td align="left">Multi-Geo búsqueda no es compatible con la creación de depósitos dinámico para los refinadores numéricos.</td>
<td align="left">Utilice el <a href="https://docs.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint">parámetro "Discretize"</a> para los refinadores numéricos.</td>
</tr>
<tr class="even">
<td align="left">Identificadores de documento</td>
<td align="left">Si está desarrollando una aplicación controlada por búsqueda que depende de ID documento, observe que identificadores de documento en un entorno Multi-Geo no son únicos en todas las ubicaciones de geo, son únicas para cada ubicación geográfica.</td>
<td align="left">Hemos agregado una columna que identifica la ubicación geográfica. Utilice esta columna para lograr la unicidad. Esta columna se denomina "GeoLocationSource".</td>
</tr>
<tr class="odd">
<td align="left">Número de resultados</td>
<td align="left">La página de resultados de búsqueda muestra resultados combinados de las ubicaciones de geo, pero no es posible más allá de 500 resultados de página.</td>
<td align="left"></td>
</tr>
</tbody>
</table>

## <a name="whats-not-supported-for-search-in-a-multi-geo-environment"></a>¿Qué no se admite para la búsqueda en un entorno Multi-Geo?

Algunas de las características de búsqueda, es posible que esté familiarizado con, no se admiten en un entorno Multi-Geo.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Función de búsqueda</strong></th>
<th align="left"><strong>Nota</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Autenticación sólo de la aplicación</td>
<td align="left">La autenticación sólo de la aplicación (acceso privilegiado de servicios) no es compatible con Multi-Geo búsqueda.</td>
</tr>
<tr class="even">
<td align="left">Usuarios invitados</td>
<td align="left">Sólo los usuarios invitados Obtén resultados desde la ubicación geográfica que está buscando desde.</td>
</tr>
</tbody>
</table>

## <a name="how-does-search-work-in-a-multi-geo-environment"></a>¿Cómo funciona la búsqueda de hace en un entorno Multi-Geo?

**Todos** los clientes de búsqueda utilizan las API existentes de resto de búsqueda de SharePoint para interactuar con los índices de búsqueda.
<img src="media/configure-search-for-multi-geo_image1-1.png" />

1. Un cliente de búsqueda llama el extremo del resto de búsqueda con la propiedad de consulta EnableMultiGeoSearch = true.
2. La consulta se envía a todas las ubicaciones de geo de los inquilinos.
3. Resultados de la búsqueda de cada ubicación geográfica se combinan y clasificados.
4. El cliente obtiene los resultados de la búsqueda unificada.



<span id="_Set_up_a" class="anchor"><span id="_Ref501388384" class="anchor"></span></span>Observe que no combinar los resultados de búsqueda hasta que hemos recibido resultados de todas las ubicaciones de geo. Esto significa que las búsquedas Multi-Geo tienen latencia adicional en comparación con las búsquedas en un entorno con geo sólo una ubicación.

<span id="_Set_up_a_1" class="anchor"><span id="_Ref505252370" class="anchor"></span></span>
## <a name="get-a-search-center-to-show-results-from-all-geo-locations"></a>Obtener un centro de búsqueda para mostrar los resultados de todas las ubicaciones de geo

Cada centro de búsqueda tiene varias líneas verticales y tendrá que configurar individualmente cada vertical.

1.  Asegúrese de que realiza estos pasos con una cuenta que tenga permiso para editar la página de resultados de la búsqueda y el elemento Web de resultados de búsqueda.

2.  Desplácese a la página de resultados de la búsqueda (consulte las páginas de resultados de la [lista](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) de búsqueda)

3.  Seleccione vertical para configurar, haga clic en el icono de engranaje de **configuración** en la esquina superior derecha y, a continuación, haga clic en **Editar página**. La página de resultados de búsqueda se abre en modo de edición.

     ![](media/configure-search-for-multi-geo_image2.png)
1.  En el elemento Web de resultados de búsqueda, mueva el puntero a la parte superior, la esquina derecha del elemento Web, haga clic en la flecha y, a continuación, haga clic en **Modificar elemento Web** en el menú. Se abre el panel de herramientas elemento Web resultados de la búsqueda en la cinta de opciones en la parte superior derecha de la página.![](media/configure-search-for-multi-geo_image3.png)

1.  En el panel de herramientas elemento Web, en la sección de **configuración** , en **configuración de control de resultados**, seleccione **Multi-Geo mostrar resultados** para obtener el elemento de Web de resultados de búsqueda para mostrar los resultados de todas las ubicaciones de geo.

2.  Haga clic en **Aceptar** para guardar los cambios y cerrar el panel de herramientas elemento Web.

3.  Compruebe los cambios realizados en el elemento Web de resultados de la búsqueda haciendo clic **En verificación** en la ficha de página del menú principal.

4.  Publicar los cambios mediante el vínculo proporcionado en la nota en la parte superior de la página.

<span id="_Get_custom_search" class="anchor"><span id="_Ref501388387" class="anchor"></span></span>
## <a name="get-custom-search-applications-to-show-results-from-all-or-some-geo-locations"></a>Obtener aplicaciones de búsqueda personalizadas para mostrar los resultados de todas o algunas ubicaciones geo

Aplicaciones de búsqueda personalizadas Obtén resultados de ubicaciones geo todas o algunas, especificando parámetros de consulta con la solicitud de la API de REST de búsqueda de SharePoint. Dependiendo de los parámetros de la consulta, la consulta se abanico a todas las ubicaciones de geo o en algunas ubicaciones geo. Por ejemplo, si sólo necesita un subconjunto de ubicaciones geo para buscar la información pertinente de la consulta, puede controlar el fan-out a éstas. Si la solicitud es correcta, la API de REST de SharePoint Search devuelve datos de respuesta.

### <a name="query-parameters"></a>Parámetros de consulta

EnableMultiGeoSearch - esto es un valor booleano que especifica si la consulta será abanico a los índices de otras ubicaciones geo del inquilino Multi-Geo. Se establece en **true** para fan-out de la consulta; **false** para no fan-out de la consulta. El valor predeterminado es **false**. Si no incluye este parámetro, la consulta es **no** abanico a otras ubicaciones geo. Si utiliza el parámetro en un entorno que no sea Multi-Geo, se omite el parámetro.

TipoCliente - se trata de una cadena. Escriba un nombre de cliente única para cada aplicación de búsqueda. Si no incluye este parámetro, la consulta es **no** abanico a otras ubicaciones geo.

MultiGeoSearchConfiguration: ésta es una lista opcional de qué geo ubicaciones en el Multi-Geo inquilinos para la consulta abanico para cuando **EnableMultiGeoSearch** es **true**. Si no incluye este parámetro, o déjelo en blanco, la consulta se abanico a todas las ubicaciones de geo. Para cada ubicación geográfica, escriba lo siguiente en formato JSON:

<table>
<thead>
<tr class="header">
<th align="left">Elemento</th>
<th align="left">Descripción</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Ubicación_datos</td>
<td align="left">La ubicación geográfica, por ejemplo NAM.</td>
</tr>
<tr class="even">
<td align="left">Extremo</td>
<td align="left">El extremo al que conectarse, por ejemplohttps://contoso.sharepoint.com</td>
</tr>
<tr class="odd">
<td align="left">SourceId</td>
<td align="left">El GUID del origen del resultado, por ejemplo B81EAB55-3140-4312-B0F4-9459D1B4FFEE.</td>
</tr>
</tbody>
</table>

Si se omite Ubicación_datos o extremo o un Ubicación_datos está duplicado, se produce un error en la solicitud. [Puede obtener información acerca del extremo de ubicaciones de geo de los inquilinos mediante Microsoft Graph](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).

### <a name="response-data"></a>Datos de respuesta

MultiGeoSearchStatus: se trata de una propiedad que devuelve la API de búsqueda de SharePoint en respuesta a una solicitud. El valor de la propiedad es una cadena y proporciona la siguiente información acerca de los resultados que devuelve la API de búsqueda de SharePoint:

<table>
<thead>
<tr class="header">
<th align="left">Valor</th>
<th align="left">Descripción</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Total</td>
<td align="left">Resultados completos de <strong>todas</strong> las ubicaciones de geo.</td>
</tr>
<tr class="even">
<td align="left">Parcial</td>
<td align="left">Resultados parciales de una o más ubicaciones de geo. Los resultados son incompletos debido a un error transitorio.</td>
</tr>

</tbody>
</table>

### <a name="query-using-the-rest-service"></a>Consulta con el servicio REST

Una solicitud GET, especifica los parámetros de consulta en la dirección URL. Con una solicitud POST, pase los parámetros de consulta en el cuerpo en formato JavaScript Object Notation (JSON).

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
<td align="left">Tipo de contenido</td>
<td align="left">Application/json; odata = verbose</td>
</tr>
</tbody>
</table>

#### <a name="sample-get-request-thats-fanned-out-to-all-geo-locations"></a>Ejemplo de solicitud GET que es abanico a **todas las** ubicaciones de geo

https:// \<inquilinos\>/\_api, búsqueda/query?querytext = 'sharepoint' & Propiedades = 'EnableMultiGeoSearch:true' & TipoCliente =' Mi\_cliente\_id'

#### <a name="sample-get-request-to-fan-out-to-some-geo-locations"></a>Ejemplo de solicitud GET para fan-out en **algunas** ubicaciones geo

https:// <tenant>/_api/search/query?querytext = 'sitio' & TipoCliente = & Propiedades de 'my_client_id' ='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration: [{Ubicación_datos\:"NAM"\,extremo\:"https\: contosoNAM.sharepoint.com"\,SourceId\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\,{Ubicación_datos\:"Puede"\,extremo\:" https\://contosoCAN.sharepoint-df.com "}]'

#### <a name="sample-post-request-thats-fanned-out-to-all-geo-locations"></a>Ejemplo de solicitud POST que es abanico a **todas las** ubicaciones de geo

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


#### <a name="sample-post-request-thats-fanned-out-to-some-geo-locations"></a>Ejemplo de solicitud POST que es abanico a **algunas** ubicaciones de geo


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

### <a name="query-using-csom"></a>Consulta con OMSC

Ésta es una consulta de OMSC de muestra es abanico a **todas las** ubicaciones de geo:

    var keywordQuery = new KeywordQuery(ctx);
    keywordQuery.QueryText = query.SearchQueryText;
    keywordQuery.ClientType = <enter a string here>;
    keywordQuery["EnableMultiGeoSearch"] = true;

