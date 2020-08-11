---
title: Opciones de navegación para SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 4/7/2020
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- SPO_Content
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- SPO160
- MET150
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: En este artículo se describen las opciones de navegación sitios con la publicación de SharePoint habilitada en SharePoint Online.
ms.openlocfilehash: dd11775c35f9eb7d2b6bccc38023b6f8bce8efc4
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606766"
---
# <a name="navigation-options-for-sharepoint-online"></a>Opciones de navegación para SharePoint Online

En este artículo se describen las opciones de navegación sitios con la publicación de SharePoint habilitada en SharePoint Online. La elección y configuración de la navegación afectan significativamente al rendimiento y la escalabilidad de los sitios de SharePoint Online. La plantilla de sitio de publicación de SharePoint solo debe usarse si es necesario para un portal centralizado y la característica de publicación solo debe habilitarse en sitios específicos y solo cuando sea absolutamente necesario, ya que puede afectar al rendimiento cuando se usa incorrectamente.

>[!NOTE]
>Si está usando las opciones modernas de navegación de SharePoint, como el menú mega, la navegación en cascada o la navegación de concentradores, este artículo no se aplica a su sitio. Las arquitecturas de sitio modernas de SharePoint aprovechan una jerarquía de sitios más acoplada y un modelo de concentrador y radio. Esto permite lograr muchos escenarios que no requieran el uso de la característica de publicación de SharePoint.

## <a name="overview-of-navigation-options"></a>Información general sobre las opciones de navegación

La configuración del proveedor de navegación puede afectar significativamente al rendimiento de todo el sitio, y se debe tener en cuenta para elegir un proveedor de navegación y una configuración que se escale con eficacia para los requisitos de un sitio de SharePoint. Hay dos proveedores de navegación preparados, así como implementaciones de navegación personalizadas.

La primera opción, [**navegación estructural**](#using-structural-navigation-in-sharepoint-online), es la opción de navegación recomendada en SharePoint Online para los sitios clásicos de SharePoint, **si activa el almacenamiento en caché de navegación estructural para su sitio**. Este proveedor de navegación muestra los elementos de navegación bajo el sitio actual y, de forma opcional, el sitio actual y sus elementos relacionados. Proporciona funciones adicionales, como el recorte de seguridad y la enumeración de la estructura del sitio. Si el almacenamiento en caché está deshabilitado, esto afectará negativamente al rendimiento y la escalabilidad, y puede estar sujeto a la limitación.

La segunda opción, la [**navegación administrada (metadatos)**](#using-managed-navigation-and-metadata-in-sharepoint-online), representa los elementos de navegación con un conjunto de términos de metadatos administrados. Se recomienda deshabilitar el recorte de seguridad a menos que sea necesario. El recorte de seguridad está habilitado como configuración segura de forma predeterminada para este proveedor de navegación; sin embargo, muchos sitios no requieren la sobrecarga de recorte de seguridad, ya que los elementos de navegación suelen ser coherentes para todos los usuarios del sitio. Con la configuración recomendada para deshabilitar el recorte de seguridad, este proveedor de navegación no necesita la enumeración de la estructura del sitio y es altamente escalable con un impacto aceptable en el rendimiento.

Además de los proveedores de navegación preinstalados, muchos clientes han implementado correctamente implementaciones de navegación personalizadas alternativas. Consulte [scripting del lado cliente](#using-search-driven-client-side-scripting) basado en búsquedas en este artículo.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Ventajas y desventajas de las opciones de navegación de SharePoint Online

En la tabla siguiente se resumen las ventajas y los inconvenientes de cada opción.

|Navegación estructural  |Navegación administrada  |Navegación basada en búsquedas  |Proveedor de navegación personalizada  |
|---------|---------|---------|---------|
|Ti<br/><br/>Fácil de mantener<br/>Seguridad recortada<br/>Actualizaciones automáticas en un plazo de 24 horas al cambiar el contenido<br/>     |Ti<br/><br/>Fácil de mantener<br/>|Ti<br/><br/>Seguridad recortada<br/>Se actualiza automáticamente cuando se agregan sitios<br/>Tiempo de carga rápida y estructura de navegación en caché local<br/>|Ti<br/><br/>Opción más amplia de opciones disponibles<br/>Carga rápida cuando se utiliza correctamente el almacenamiento en caché<br/>Muchas opciones funcionan bien con un diseño de página dinámico<br/>|
|Conos<br/><br/>**Afecta al rendimiento si el almacenamiento en caché está deshabilitado**<br/>Sujeto a la limitación<br/>|Conos<br/><br/>No se actualiza automáticamente para reflejar la estructura del sitio<br/>**Afecta al rendimiento si se habilita el recorte de seguridad** o si la estructura de navegación es compleja<br/>|Conos<br/><br/>No se pueden ordenar sitios fácilmente<br/>Requiere la personalización de la página maestra (habilidades técnicas necesarias)<br/>|Conos<br/><br/>Se requiere desarrollo personalizado<br/>Se necesita un origen de datos externo o almacenamiento en caché, por ejemplo Azure<br/>|

La opción más adecuada para su sitio dependerá de los requisitos de su sitio y de su capacidad técnica. Si quiere un proveedor de navegación fácil de configurar que se actualice automáticamente cuando cambie el contenido, la navegación estructural [con el almacenamiento en caché habilitado](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43) es una buena opción.

>[!NOTE]
>Aplicar el mismo principio que los sitios modernos de SharePoint simplificando la estructura general del sitio a una estructura más plana y no jerárquica mejora el rendimiento y simplifica el paso a los sitios modernos de SharePoint. Esto significa que en lugar de tener una sola colección de sitios con cientos de sitios (subwebs), un mejor enfoque es disponer de muchas colecciones de sitios con muy pocos subsitios (subwebs).

## <a name="analyzing-navigation-performance-in-sharepoint-online"></a>Analizar el rendimiento de navegación en SharePoint Online

La [herramienta diagnósticos de página para SharePoint](https://aka.ms/perftool) es una extensión de explorador para los exploradores Microsoft Edge y Chrome que analizan las páginas del portal moderno de SharePoint Online y del sitio de publicación clásico. Esta herramienta solo funciona para SharePoint Online y no se puede usar en una página del sistema de SharePoint.

La herramienta genera un informe para cada página analizada que muestra cómo se ejecuta la página en un conjunto predefinido de reglas y muestra información detallada cuando los resultados de una prueba se encuentran fuera del valor de línea base. Los diseñadores y administradores de SharePoint Online pueden usar la herramienta para solucionar problemas de rendimiento y garantizar que las nuevas páginas se optimizan antes de la publicación.

En particular, **SPRequestDuration** es el tiempo que tarda SharePoint en procesar la página. La navegación intensa (como, por ejemplo, las páginas en navegación), las jerarquías de sitios complejas y otras opciones de configuración y topología pueden contribuir drásticamente a las duraciones más largas.

## <a name="using-structural-navigation-in-sharepoint-online"></a>Uso de la navegación estructural en SharePoint Online

Esta es la navegación predefinida que se usa de forma predeterminada y es la solución más sencilla. No requiere personalización y un usuario no técnico también puede agregar elementos, ocultar elementos y administrar la navegación desde la página de configuración fácilmente. Se recomienda [Habilitar el almacenamiento en caché](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43); de lo contrario, existe un equilibrio entre rendimiento caro.

### <a name="how-to-implement-structural-navigation-caching"></a>Cómo implementar el almacenamiento en caché de navegación estructural

En la apariencia de la **configuración del sitio**  >  **y**la  >  **navegación**, puede validar si la navegación estructural está seleccionada para la navegación global o la navegación actual. La selección de **Mostrar páginas** tendrá un impacto negativo en el rendimiento.

![Navegación estructural con la muestra de subsitios seleccionada](media/SPONavOptionsStructuredShowSubsites.png)

El almacenamiento en caché se puede habilitar o deshabilitar en el nivel de la colección de sitios y en el nivel del sitio, y se habilita de forma predeterminada para ambos. Para habilitar en el nivel de la colección de sitios, en **configuración del sitio**navegación de la colección de sitios de administración de sitios  >  **Site Collection Administration**  >  **Site Collection Navigation**, active la casilla **Habilitar almacenamiento en caché**.

![Habilitar el almacenamiento en caché en el nivel de sitio](media/structural-nav/structural-nav-caching-site-coll.png)

Para habilitar en el nivel de sitio, **Site Settings**en  >  **navegación**por la configuración del sitio, active la casilla **Habilitar almacenamiento en caché**.

![Habilitar el almacenamiento en caché en el nivel de sitio](media/structural-nav/structural-nav-caching-site.png)

## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Usar la navegación administrada y los metadatos en SharePoint Online

La navegación administrada es otra opción precreada que puede usar para volver a crear la mayor parte de la funcionalidad como navegación estructural. Los metadatos administrados se pueden configurar para que el recorte de seguridad esté habilitado o deshabilitado. Cuando se configura con el recorte de seguridad deshabilitado, la navegación administrada es bastante eficiente ya que carga todos los vínculos de navegación con un número constante de llamadas del servidor. No obstante, la habilitación de la reducción de seguridad anula algunas de las ventajas de rendimiento de la navegación administrada.

Si necesita habilitar el recorte de seguridad, le recomendamos que:

- Actualizar todos los vínculos a direcciones URL descriptivas a vínculos simples
- Agregar los nodos de recorte de seguridad necesarios como direcciones URL descriptivas
- Limitar el número de elementos de navegación a un máximo de 100 y no tener más de 3 niveles de profundidad

Muchos sitios no requieren el recorte de seguridad, ya que la estructura de navegación suele ser coherente para todos los usuarios del sitio. Si se deshabilita el recorte de seguridad y se agrega un vínculo a la navegación que no tienen acceso a todos los usuarios, el vínculo seguirá mostrando pero conducirá a un mensaje de acceso denegado. No existe ningún riesgo de acceso involuntario al contenido.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Cómo implementar la navegación administrada y los resultados

Hay varios artículos sobre docs.microsoft.com acerca de los detalles de la navegación administrada. Por ejemplo, vea [información general sobre la navegación administrada en SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Para implementar la navegación administrada, se configuran los términos con direcciones URL correspondientes a la estructura de navegación del sitio. La navegación administrada puede incluso creadosrse manualmente para reemplazar la navegación estructural en muchos casos. Por ejemplo:

![Estructura de sitio de SharePoint Online](media/SPONavOptionsListOfSites.png))

## <a name="using-search-driven-client-side-scripting"></a>Uso de scripting de cliente basado en búsquedas

Una clase común de implementaciones de navegación personalizadas adopta patrones de diseño representados por el cliente que almacenan una memoria caché local de nodos de navegación.

Estos proveedores de navegación tienen un par de ventajas clave:

- Por lo general, funcionan bien con diseños de página dinámicos.
- Son extremadamente escalables y funcionan porque pueden representarse sin costo de recursos (y actualizar en segundo plano después de un tiempo de espera).
- Estos proveedores de navegación pueden recuperar datos de navegación mediante varias estrategias, desde configuraciones estáticas simples a varios proveedores de datos dinámicos.

Un ejemplo de un proveedor de datos es usar una **navegación**basada en búsquedas, que permite la flexibilidad para enumerar los nodos de navegación y controlar de forma eficaz el recorte de seguridad.

Hay otras opciones populares para crear **proveedores de navegación personalizados**. Revise [soluciones de navegación para portales de SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) para obtener más información sobre la creación de un proveedor de navegación personalizado.

Mediante la búsqueda, puede aprovechar los índices que se han integrado en el fondo con el rastreo continuo. Los resultados de la búsqueda se extraen del índice de búsqueda y los resultados se reducen por seguridad. Esto suele ser más rápido que los proveedores de navegación preparados cuando se requiere el recorte de seguridad. Usar la búsqueda para la navegación estructural, sobre todo si tiene una estructura de sitio compleja, reducirá considerablemente el tiempo de carga de la página. La principal ventaja de esto sobre la navegación administrada es que se beneficia de la reducción de seguridad.

Este enfoque implica la creación de una página maestra personalizada y la sustitución del código de navegación precreado con HTML personalizado. Siga este procedimiento descrito en el siguiente ejemplo para reemplazar el código de navegación en el archivo `seattle.html` . En este ejemplo, se abrirá el `seattle.html` archivo y se reemplazará todo el elemento `id="DeltaTopNavigation"` con código HTML personalizado.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Ejemplo: reemplazar el código de navegación de precodificación en una página maestra

1. Navegue a la página Configuración del sitio.
2. Abra la galería de páginas maestras; para ello, haga clic en **páginas maestras**.
3. Desde aquí puede navegar por la biblioteca y descargar el archivo `seattle.master` .
4. Edite el código con un editor de texto y elimine el bloque de código en la siguiente captura de pantalla.<br/>![Eliminar el bloque de código que se muestra](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Quite el código entre las `<SharePoint:AjaxDelta id="DeltaTopNavigation">` `<\SharePoint:AjaxDelta>` etiquetas y y reemplácela por el siguiente fragmento de código:<br/>

```javascript
<div id="loading">
  <!--Replace with path to loading image.-->
  <div style="background-image: url(''); height: 22px; width: 22px; ">
  </div>
</div>
<!-- Main Content-->
<div id="navContainer" style="display:none">
    <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
        </a>
        <ul id="menu" data-bind="foreach: $data.children" style="padding-left:20px">
            <li class="static dynamic-children level1">
                <a class="static dynamic-children menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

                 <!-- ko if: children.length > 0-->
                    <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                <!-- ko if: children.length == 0-->
                    <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
                        <span class="menu-item-text" data-bind="text: item.Title">
                        </span>
                    </span>
                <!-- /ko -->
                </a>

                <!-- ko if: children.length > 0-->
                <ul id="menu"  data-bind="foreach: children;" class="dynamic  level2" >
                    <li class="dynamic level2">
                        <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline  ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">

          <!-- ko if: children.length > 0-->
          <span aria-haspopup="true" class="additional-background ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
           <!-- /ko -->
          <!-- ko if: children.length == 0-->
          <span aria-haspopup="true" class="ms-navedit-flyoutArrow dynamic-children">
           <span class="menu-item-text" data-bind="text: item.Title">
           </span>
          </span>
          <!-- /ko -->
                        </a>
          <!-- ko if: children.length > 0-->
         <ul id="menu" data-bind="foreach: children;" class="dynamic level3" >
          <li class="dynamic level3">
           <a class="dynamic menu-item ms-core-listMenu-item ms-displayInline ms-navedit-linkNode" data-bind="attr: { href: item.Url, title: item.Title }">
            <span class="menu-item-text" data-bind="text: item.Title">
            </span>
           </a>
          </li>
         </ul>
           <!-- /ko -->
                    </li>
                </ul>
                <!-- /ko -->
            </li>
        </ul>
    </div>
</div>
```

<br/>
6. Reemplace la dirección URL de la etiqueta de anclaje de la imagen de carga al principio, por un vínculo a una imagen de carga en la colección de sitios. Después de realizar los cambios, cambie el nombre del archivo y, a continuación, cárguelo en la galería de páginas maestras. Esto genera un nuevo archivo. Master.<br/>
7. Este HTML es el marcado básico que rellenará los resultados de la búsqueda devueltos desde el código JavaScript. Tendrá que editar el código para cambiar el valor de var root = "site Collection URL" como se muestra en el siguiente fragmento de código:<br/>

```javascript
var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
```

<br/>
8. Los resultados se asignan a self. Nodes y una jerarquía se crea a partir de los objetos mediante la linq.js asignar el resultado a una matriz self. hierarchy. Esta matriz es el objeto que está enlazado al HTML. Esto se realiza en la función toggleView () pasando el objeto Self a la función ko. applyBinding ().<br/>Esto hace que la matriz de jerarquías se enlace al siguiente HTML:<br/>

```javascript
<div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
```

Los controladores de eventos para `mouseenter` y `mouseexit` se agregan a la navegación de nivel superior para controlar los menús desplegables de subsitio que se realizan en la `addEventsToElements()` función.

En nuestro ejemplo de navegación compleja, una carga de página nueva sin el almacenamiento en caché local muestra el tiempo empleado en el servidor se ha reducido de la navegación estructural de Benchmark para obtener un resultado similar al del enfoque de navegación administrada.

### <a name="about-the-javascript-file"></a>Acerca del archivo JavaScript...

>[!NOTE]
>Si usa JavaScript personalizado, asegúrese de que la red CDN pública esté habilitada y que el archivo esté en una ubicación de red CDN.

El archivo JavaScript completo es el siguiente:

```javascript
//Models and Namespaces
var SPOCustom = SPOCustom || {};
SPOCustom.Models = SPOCustom.Models || {}
SPOCustom.Models.NavigationNode = function () {

    this.Url = ko.observable("");
    this.Title = ko.observable("");
    this.Parent = ko.observable("");

};

var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
var baseUrl = root + "/_api/search/query?querytext=";
var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&trimduplicates=false&rowlimit=300";

var baseRequest = {
    url: "",
    type: ""
};


//Parses a local object from JSON search result.
function getNavigationFromDto(dto) {
    var item = new SPOCustom.Models.NavigationNode();
    if (dto != undefined) {

        var webTemplate = getSearchResultsValue(dto.Cells.results, 'WebTemplate');

        if (webTemplate != "APP") {
            item.Title(getSearchResultsValue(dto.Cells.results, 'Title')); //Key = Title
            item.Url(getSearchResultsValue(dto.Cells.results, 'Path')); //Key = Path
            item.Parent(getSearchResultsValue(dto.Cells.results, 'ParentLink')); //Key = ParentLink
        }

    }
    return item;
}

function getSearchResultsValue(results, key) {

    for (i = 0; i < results.length; i++) {
        if (results[i].Key == key) {
            return results[i].Value;
        }
    }
    return null;
}

//Parse a local object from the serialized cache.
function getNavigationFromCache(dto) {
    var item = new SPOCustom.Models.NavigationNode();

    if (dto != undefined) {

        item.Title(dto.Title);
        item.Url(dto.Url);
        item.Parent(dto.Parent);
    }

    return item;
}

/* create a new OData request for JSON response */
function getRequest(endpoint) {
    var request = baseRequest;
    request.type = "GET";
    request.url = endpoint;
    request.headers = { ACCEPT: "application/json;odata=verbose" };
    return request;
};

/* Navigation Module*/
function NavigationViewModel() {
    "use strict";
    var self = this;
    self.nodes = ko.observableArray([]);
    self.hierarchy = ko.observableArray([]);;
    self.loadNavigatioNodes = function () {
        //Check local storage for cached navigation datasource.
        var fromStorage = localStorage["nodesCache"];
        if (false) {
            var cachedNodes = JSON.parse(localStorage["nodesCache"]);

            if (cachedNodes && timeStamp) {
                //Check for cache expiration. Currently set to 3 hrs.
                var now = new Date();
                var diff = now.getTime() - timeStamp;
                if (Math.round(diff / (1000 * 60 * 60)) < 3) {

                    //return from cache.
                    var cacheResults = [];
                    $.each(cachedNodes, function (i, item) {
                        var nodeitem = getNavigationFromCache(item, true);
                        cacheResults.push(nodeitem);
                    });

                    self.buildHierarchy(cacheResults);
                    self.toggleView();
                    addEventsToElements();
                    return;
                }
            }
        }
        //No cache hit, REST call required.
        self.queryRemoteInterface();
    };

    //Executes a REST call and builds the navigation hierarchy.
    self.queryRemoteInterface = function () {
        var oDataRequest = getRequest(query);
        $.ajax(oDataRequest).done(function (data) {
            var results = [];
            $.each(data.d.query.PrimaryQueryResult.RelevantResults.Table.Rows.results, function (i, item) {

                if (i == 0) {
                    //Add root element.
                    var rootItem = new SPOCustom.Models.NavigationNode();
                    rootItem.Title("Root");
                    rootItem.Url(root);
                    rootItem.Parent(null);
                    results.push(rootItem);
                }
                var navItem = getNavigationFromDto(item);
                results.push(navItem);
            });
            //Add to local cache
            localStorage["nodesCache"] = ko.toJSON(results);

            localStorage["nodesCachedAt"] = new Date().getTime();
            self.nodes(results);
            if (self.nodes().length > 0) {
                var unsortedArray = self.nodes();
                var sortedArray = unsortedArray.sort(self.sortObjectsInArray);

                self.buildHierarchy(sortedArray);
                self.toggleView();
                addEventsToElements();
            }
        }).fail(function () {
            //Handle error here!!
            $("#loading").hide();
            $("#error").show();
        });
    };
    self.toggleView = function () {
        var navContainer = document.getElementById("navContainer");
        ko.applyBindings(self, navContainer);
        $("#loading").hide();
        $("#navContainer").show();

    };
    //Uses linq.js to build the navigation tree.
    self.buildHierarchy = function (enumerable) {
        self.hierarchy(Enumerable.From(enumerable).ByHierarchy(function (d) {
            return d.Parent() == null;
        }, function (parent, child) {
            if (parent.Url() == null || child.Parent() == null)
                return false;
            return parent.Url().toUpperCase() == child.Parent().toUpperCase();
        }).ToArray());

        self.sortChildren(self.hierarchy()[0]);
    };


    self.sortChildren = function (parent) {

        // sjip processing if no children
        if (!parent || !parent.children || parent.children.length === 0) {
            return;
        }

        parent.children = parent.children.sort(self.sortObjectsInArray2);

        for (var i = 0; i < parent.children.length; i++) {
            var elem = parent.children[i];

            if (elem.children && elem.children.length > 0) {
                self.sortChildren(elem);
            }
        }
    };

    // ByHierarchy method breaks the sorting in chrome and firefox
    // we need to resort  as ascending
    self.sortObjectsInArray2 = function (a, b) {
        if (a.item.Title() > b.item.Title())
            return 1;
        if (a.item.Title() < b.item.Title())
            return -1;
        return 0;
    };


    self.sortObjectsInArray = function (a, b) {
        if (a.Title() > b.Title())
            return -1;
        if (a.Title() < b.Title())
            return 1;
        return 0;
    }
}

//Loads the navigation on load and binds the event handlers for mouse interaction.
function InitCustomNav() {
    var viewModel = new NavigationViewModel();
    viewModel.loadNavigatioNodes();
}

function addEventsToElements() {
    //events.
      $("li.level1").mouseover(function () {
          var position = $(this).position();
          $(this).find("ul.level2").css({ width: 100, left: position.left + 10, top: 50 });
      })
   .mouseout(function () {
     $(this).find("ul.level2").css({  left: -99999, top: 0 });
   
    });
   
     $("li.level2").mouseover(function () {
          var position = $(this).position();
          console.log(JSON.stringify(position));
          $(this).find("ul.level3").css({ width: 100, left: position.left + 95, top:  position.top});
      })
   .mouseout(function () {
     $(this).find("ul.level3").css({  left: -99999, top: 0 });
    });
} _spBodyOnLoadFunctionNames.push("InitCustomNav");

```

Para resumir el código que se ha mostrado anteriormente en la `jQuery $(document).ready` función `viewModel object` , se ha creado una y, a continuación, `loadNavigationNodes()` se llama a la función en ese objeto. Esta función carga la jerarquía de navegación previamente creada almacenada en el almacenamiento local de HTML5 del explorador del cliente o llama a la función `queryRemoteInterface()` .

`QueryRemoteInterface()`compila una solicitud mediante la `getRequest()` función con el parámetro de consulta definido anteriormente en el script y, a continuación, devuelve datos del servidor. Estos datos son esencialmente una matriz de todos los sitios de la colección de sitios que se representan como objetos de transferencia de datos con diversas propiedades.

A continuación, estos datos se analizan en los `SPO.Models.NavigationNode` objetos definidos anteriormente que usan `Knockout.js` para crear propiedades observables para su uso mediante el enlace de datos de los valores en el código HTML que se ha definido anteriormente.

A continuación, los objetos se colocan en una matriz de resultados. Esta matriz se analiza en JSON usando knockout y se almacena en el almacenamiento local del explorador para mejorar el rendimiento en futuras cargas de páginas.

### <a name="benefits-of-this-approach"></a>Ventajas de este enfoque

Una de las principales ventajas de [este enfoque](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) es que, al usar el almacenamiento local de HTML5, la navegación se almacena localmente para el usuario la próxima vez que cargue la página. Obtenemos mejoras de rendimiento principales al usar la API de búsqueda para la navegación estructural; sin embargo, se necesita cierta capacidad técnica para ejecutar y personalizar esta funcionalidad.

En la [implementación del ejemplo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), los sitios se ordenan de la misma manera que la navegación estructural de forma integrada; orden alfabético. Si desea desviarse de esta orden, sería más complicado su desarrollo y mantenimiento. Además, este enfoque requiere que se desvíe de las páginas maestras admitidas. Si no se mantiene la página maestra personalizada, el sitio perderá las actualizaciones y las mejoras que Microsoft realiza en las páginas maestras.

El [código anterior](#about-the-javascript-file) tiene las siguientes dependencias:

- jQueryhttps://jquery.com/
- KnockoutJS -https://knockoutjs.com/
- Linq.js https://linqjs.codeplex.com/ o github.com/neuecc/linq.js

La versión actual de LinqJS no contiene el método ByHierarchy que se usó en el código anterior y romperá el código de navegación. Para solucionarlo, agregue el método siguiente al archivo de Linq.js antes de la línea `Flatten: function ()` .

```javascript
ByHierarchy: function(firstLevel, connectBy, orderBy, ascending, parent) {
     ascending = ascending == undefined ? true : ascending;
     var orderMethod = ascending == true ? 'OrderBy' : 'OrderByDescending';
     var source = this;
     firstLevel = Utils.CreateLambda(firstLevel);
     connectBy = Utils.CreateLambda(connectBy);
     orderBy = Utils.CreateLambda(orderBy);

     //Initiate or increase level
     var level = parent === undefined ? 1 : parent.level + 1;

    return new Enumerable(function() {
         var enumerator;
         var index = 0;

        var createLevel = function() {
                 var obj = {
                     item: enumerator.Current(),
                     level : level
                 };
                 obj.children = Enumerable.From(source).ByHierarchy(firstLevel, connectBy, orderBy, ascending, obj);
                 if (orderBy !== undefined) {
                     obj.children = obj.children[orderMethod](function(d) {
                         return orderBy(d.item); //unwrap the actual item for sort to work
                     });
                 }
                 obj.children = obj.children.ToArray();
                 Enumerable.From(obj.children).ForEach(function(child) {
                     child.getParent = function() {
                         return obj;
                     };
                 });
                 return obj;
             };

        return new IEnumerator(

        function() {
             enumerator = source.GetEnumerator();
         }, function() {
             while (enumerator.MoveNext()) {
                 var returnArr;
                 if (!parent) {
                     if (firstLevel(enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }

                } else {
                     if (connectBy(parent.item, enumerator.Current(), index++)) {
                         return this.Yield(createLevel());
                     }
                 }
             }
             return false;
         }, function() {
             Utils.Dispose(enumerator);
         })
     });
 },

```
  
## <a name="related-topics"></a>Temas relacionados

[Información general sobre la navegación administrada en SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation)

[Rendimiento y almacenamiento en caché de navegación estructural](https://support.office.com/article/structural-navigation-and-performance-f163053f-8eca-4b9c-b973-36b395093b43)
