---
title: Opciones de navegación para SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: Este artículo describen los sitios de las opciones de navegación con publicación de SharePoint habilitado en SharePoint Online. La elección y la configuración de navegación afectará de forma significativa el rendimiento y la escalabilidad de sitios de SharePoint Online.
ms.openlocfilehash: 08790dcee343e9e69bbaab149cce8a390470e7d6
ms.sourcegitcommit: 5731dce2440e5a7a261f6360e8e2e9639d339d4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2018
ms.locfileid: "23957455"
---
# <a name="navigation-options-for-sharepoint-online"></a>Opciones de navegación para SharePoint Online

Este artículo describen los sitios de las opciones de navegación con publicación de SharePoint habilitado en SharePoint Online. La elección y la configuración de navegación afectará de forma significativa el rendimiento y la escalabilidad de sitios de SharePoint Online.

## <a name="overview"></a>Información general

Configuración del proveedor de navegación puede afectar significativamente al rendimiento de todo el sitio, y deben tener en cuenta consideraciones cuidado para seleccionar un proveedor de navegación y la configuración que escala de forma eficaz los requisitos de un sitio de SharePoint. Hay dos proveedores de navegación del cuadro, así como las implementaciones de navegación personalizada.

La primera opción, [**navegación Managed (metadatos)**](#using-managed-navigation-and-metadata-in-sharepoint-online), se recomienda y es una de las opciones predeterminadas en SharePoint Online; Sin embargo, se recomienda deshabilitar el recorte de seguridad a menos que requiera. Recorte de seguridad está habilitado como una configuración de seguro de forma predeterminada para este proveedor de navegación; Sin embargo, muchos sitios no requieren la sobrecarga de la restricción de seguridad ya que los elementos de navegación a menudo son coherentes para todos los usuarios del sitio. Con la configuración recomendada para deshabilitar el recorte de seguridad, este proveedor de navegación no requiere enumerar la estructura del sitio y es altamente escalable con el impacto de rendimiento aceptable.

La segunda opción, [**navegación estructural**](#using-structural-navigation-in-sharepoint-online), **es no una opción recomendada de navegación en SharePoint Online**. Este proveedor de navegación se diseñó para una topología local está limitado soporte en SharePoint Online. Mientras proporciona algunas conjunto adicional de capacidades en comparación con otras opciones de navegación, estas características, incluidos el recorte de seguridad y enumeración de estructura del sitio, tiene un costo de las llamadas de excesiva en el servidor y el rendimiento y escalabilidad de impactos cuando se usa. Sitios mediante navegación structed que consuman demasiados recursos pueden ser sujetas a limitación.

Además de los proveedores de navegación del cuadro, muchos clientes han implementado correctamente las implementaciones de navegación personalizada alternativo. Una clase común de las implementaciones de navegación personalizada adopta patrones de diseño representado por el cliente que almacenan una memoria caché local de los nodos de navegación. (Vea **[secuencias de comandos de cliente basado en búsquedas](#using-search-driven-client-side-scripting)** en este artículo).

Estos proveedores de navegación tienen un par de ventajas claves: 
- Por lo general funcionan bien con los diseños de página con capacidad de respuesta.
- Son extremadamente escalables y eficaz porque puede presentarse sin costo del recurso (y la actualización en segundo plano después de un tiempo de espera). 
- Estos proveedores de navegación pueden recuperar datos de navegación mediante diversas estrategias, comprendido entre las configuraciones estáticas simples para varios proveedores de datos dinámicos. 

Un ejemplo de un proveedor de datos es usar una **navegación controlada por la búsqueda**, que permite flexibilidad para enumerar los nodos de navegación y controlar el recorte de forma eficaz de seguridad. 

Hay otras opciones más populares para crear **proveedores de navegación personalizada**. Revise [las soluciones de navegación para portales de SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) para obtener más información sobre la creación de un proveedor personalizado de navegación.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Opciones de navegación pros y contras de SharePoint Online

En la siguiente tabla se resume las ventajas y desventajas de cada opción. 


|Navegación administrada  |Navegación estructural  |Navegación por búsqueda  |Proveedor de navegación personalizada  |
|---------|---------|---------|---------|
|Ventajas:<br/><br/>Fácil de mantener<br/>Opción recomendada<br/>     |Ventajas:<br/><br/>Fácil de configurar<br/>Restricciones de seguridad<br/>Se actualiza automáticamente cuando se agrega contenido<br/>|Ventajas:<br/><br/>Restricciones de seguridad<br/>Se actualiza automáticamente cuando se agregan sitios<br/>Rápido tiempo de carga y estructura de navegación en caché local<br/>|Ventajas:<br/><br/>Más amplia gama de opciones disponibles<br/>Cargar Fast al almacenamiento en caché se usa correctamente<br/>Muchas opciones funcionan bien con diseño de página con capacidad de respuesta<br/>|
|Desventajas:<br/><br/>No se actualiza automáticamente para reflejar la estructura del sitio<br/>Afecta al rendimiento si está habilitado el recorte de seguridad<br/>|Desventajas:<br/><br/>**No se recomienda**<br/>**Afecta al rendimiento y escalabilidad**<br/>**Sujeto a limitación**<br/>|Desventajas:<br/><br/>No se pueden ordenar sitios de forma sencilla<br/>Requiere la personalización de la página maestra (se requieren conocimientos técnicos)<br/>|Desventajas:<br/><br/>Se requiere desarrollo personalizado<br/>Origen de datos externo / caché almacena es necesario, por ejemplo, Azure<br/>|

La opción más adecuada para su sitio dependerá de las necesidades del sitio y en su capacidad técnica. Si desea que un proveedor de navegación de cuadro escalable, navegación administrada con el recorte de seguridad deshabilitado es una opción muy buena. 

Se puede mantener la opción de navegación administrada a través de configuración, no a los archivos de personalización de código y es mucho más rápido que la navegación estructural. Si requieren el recorte de seguridad y está familiarizado con el uso de una página maestra personalizada y tienen capacidad de algunos en la organización para mantener los cambios que pueden producirse en la página maestra predeterminada para SharePoint Online, la opción de búsqueda puede producir una mejor experiencia del usuario. Si tiene requisitos más complejos, un proveedor de navegación personalizada puede ser la opción más adecuada. NO se recomienda navegación estructural.

Por último, es importante tener en cuenta que SharePoint va a agregar proveedores de navegación adicionales y funciones para arquitecturas modernas de sitio de SharePoint aprovechamiento de una jerarquía de sitios más plana y un modelo de concentrador y radio con los sitios de concentradores de SharePoint. Esto permite muchos escenarios lograr que no requieren el uso de la característica de publicación de SharePoint, y estas configuraciones de navegación están optimizadas para la escalabilidad y la latencia dentro de SharePoint Online. Tenga en cuenta que a menudo el mismo principio - simplificación de la estructura general de su sitio de publicación de SharePoint a una estructura más plana, la aplicación ayuda a con el rendimiento general y escalar así como. Esto significa que en lugar de tener una única colección de sitios con cientos de sitios (subwebs), un mejor enfoque es tiene muchas colecciones de sitios con subsitios muy pocos (subwebs).


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Uso de metadatos y navegación administrada en SharePoint Online

Navegación administrada es otra opción del cuadro que puede usar para volver a crear la mayor parte de la misma funcionalidad que la navegación estructural. Metadatos administrados pueden configurarse para que el recorte de seguridad está habilitada o deshabilitada. Cuando se configura con el recorte de seguridad deshabilitado, navegación administrada es bastante eficaz como que carga todos los vínculos de navegación con un número constante de llamadas de servidor. Habilitación de la restricción de seguridad, sin embargo, niega algunas de las ventajas de la navegación administrada y los clientes pueden elegir explorar una de las soluciones de navegación personalizada para un rendimiento óptimo y la escalabilidad.

Muchos sitios no requieren el recorte de seguridad, como la estructura de navegación a menudo es coherente para todos los usuarios del sitio. Si está deshabilitado el recorte de seguridad y se agrega un vínculo a la navegación que no todos los usuarios tienen acceso a, el vínculo seguirá mostrando pero dará lugar a un mensaje de acceso denegado. No hay ningún riesgo de accidental acceso al contenido.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Cómo implementar la navegación administrada y los resultados

Hay varios artículos en Docs.Microsoft.com acerca de los detalles de la navegación administrada, por ejemplo, vea [información general de la navegación administrada en SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Para implementar la navegación administrada, configure las condiciones con las direcciones URL correspondiente a la estructura de navegación del sitio. Navegación administrada incluso puede ser manualmente curated que va a reemplazar navegación estructural en muchos casos. Por ejemplo:

![Estructura del sitio de SharePoint Online](media/SPONavOptionsListOfSites.png)

En el ejemplo siguiente se muestra el rendimiento de la navegación compleja mediante navegación administrada.

![Rendimiento de navegación complejas con navegación administrada](media/SPONavOptionsComplexNavPerf.png)

Usar la navegación administrada coherentemente mejora el rendimiento en comparación con el enfoque de navegación estructural.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Usar la navegación estructural en SharePoint Online

Esto es el panel de navegación del cuadro usado de forma predeterminada y es la solución más sencilla pero como tal, tiene un equilibrio rendimiento costosos. No requiere ninguna personalización y un usuario no técnico también fácilmente puede agregar elementos, ocultar los elementos y administrar la navegación desde la página de configuración. Esto es sin embargo también true para la navegación administrados por lo que se recomienda utilizar la navegación administrados como que también se puede fácilmente administrada y controla así como con mejor performance.

![Navegación estructural con Mostrar subsitios seleccionado](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Activar la navegación estructural en SharePoint Online

Para ilustrar cómo el rendimiento en una solución de SharePoint Online estándar con navegación estructural y el Mostrar subsitios opción activado. A continuación se presenta una captura de pantalla de configuración que se encuentra en la página **Configuración del sitio** \> **navegación**.
  
![Captura de pantalla que muestra subsitios](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analizar el rendimiento de la navegación estructural en SharePoint Online

Para analizar el rendimiento de una página de SharePoint, use la ficha de **red** de las herramientas de desarrollo F12 en Internet Explorer. 
  
![Captura de pantalla que muestra la pestaña Red de herramientas de desarrollo F12](media/SPONavOptionsNetworks.png)
  
1. En la ficha **Red**, haga clic en la página .aspx que se está cargando y, a continuación, haga clic en la ficha **Detalles**.<br/> ![Captura de pantalla que muestra la pestaña Detalles](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. Haga clic en **Encabezados de respuesta**. <br/>![Captura de pantalla de la pestaña Detalles](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint devuelve la información de diagnóstico útil en sus encabezados de respuesta. 
3. Uno de los elementos más útiles de información es **SPRequestDuration** , que es el valor, en milisegundos, de una solicitud de cuánto tardó en procesarse en el servidor. En la siguiente captura de pantalla está desactivada para la navegación estructural **Mostrar subsitios** . Esto significa que hay sólo el vínculo de la colección de sitios en la navegación global:<br/>![Captura de pantalla que muestra los tiempos de carga como duración de solicitud](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. La clave de **SPRequestDuration** tiene un valor de 245 milisegundos. Esto representa el tiempo que se tardó en devolver la solicitud. Dado que hay un solo elemento de navegación en el sitio, se trata de un buen rendimiento para cómo SharePoint Online realiza sin navegación gruesa. La captura de pantalla siguiente muestra cómo agregar en los subsitios que afecta a esta clave.<br/>![Captura de pantalla que muestra una duración de solicitud de 2 502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
Adición de los subsitios ha aumentado considerablemente el tiempo necesario para devolver la solicitud de página para este sitio de ejemplo es relativamente simple. Jerarquías de sitios complejos, incluidas las páginas de navegación y otras opciones de topología y configuración pueden aumentar considerablemente este impacto aún más.

## <a name="using-search-driven-client-side-scripting"></a>Usar scripting de cliente por búsqueda

Uso de búsqueda puede aprovechar los índices que se crean en segundo plano mediante el rastreo continuo. Los resultados de búsqueda se extraen del índice de búsqueda y los resultados son restricciones de seguridad. Esto es generalmente más rápido que los proveedores de navegación del cuadro cuando se necesita la reducción de seguridad. Uso de búsqueda para la navegación estructural, especialmente si tiene una estructura de sitio complejo, va a acelerar considerablemente en tiempo de carga de página. La principal ventaja de esta a través de navegación administrada es que se benefician de recorte de seguridad.

Este enfoque implica la creación de una página maestra personalizada y reemplazar el código de navegación del cuadro con código HTML personalizado. Siga este procedimiento descrito en el siguiente ejemplo para reemplazar el código de navegación en el archivo `seattle.html`. En este ejemplo, se abrirá la `seattle.html` de archivos y reemplace todo el elemento `id=”DeltaTopNavigation”` con el código HTML personalizado.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Ejemplo: Reemplace el código de navegación del cuadro en una página maestra

1.  Vaya a la página Configuración del sitio.
2.  Haga clic en **Páginas maestras** para abrir la galería de páginas maestras.
3.  Desde aquí puede navegar por la biblioteca y descargue el archivo `seattle.master`.
4.  Edite el código con un editor de texto y elimine el bloque de código en la siguiente captura de pantalla.<br/>![Eliminar el bloque de código que se muestra](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Quitar el código entre la `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` y `<\SharePoint:AjaxDelta>` de etiquetas y reemplácelo con el siguiente fragmento de código:<br/>

```
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
6. Reemplace la dirección URL en la carga de la imagen etiqueta delimitadora al principio, con un vínculo a una imagen de carga en la colección de sitios. Una vez realizados los cambios, cambie el nombre del archivo y, a continuación, cárguela en la Galería de páginas maestras. Esto genera un nuevo archivo. master.<br/>
7. Este código HTML es el marcado básicos que se va a rellenar con los resultados de búsqueda devueltos desde el código JavaScript. Tendrá que modificar el código para cambiar el valor de raíz de var = "dirección URL de la colección de sitios" como se muestra en el siguiente fragmento de código:<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. Los resultados se asignan a la matriz de self.nodes y se crea una jerarquía de fuera de los objetos con linq.js asignar el resultado a una matriz self.heirarchy. Esta matriz es el objeto que está enlazado el código HTML. Esto se realiza en la función toggleView(), pasando el objeto automático a la función ko.applyBinding().<br/>Esto hace que la matriz de jerarquía enlazar el código HTML siguiente:<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

Los controladores de eventos para `mouseenter` y `mouseexit` se agregan a la navegación de nivel superior para controlar los menús de lista desplegable del subsitio que se realiza en el `addEventsToElements()` (función).

En nuestro ejemplo de navegación complejas, una página en blanco se carga sin tener que el almacenamiento en caché local se muestra el tiempo empleado en el servidor ha cortado hacia abajo en la barra de navegación estructural del banco de pruebas para obtener un resultado similar como el enfoque de navegación administrada.

### <a name="about-the-javascript-file"></a>Acerca del archivo JavaScript...

Todo el archivo JavaScript es de esta manera:

```
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

    // ByHierarchy method breaks the sorting in chrome and firefix 
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

Para resumir el código mostrado anteriormente en el `jQuery $(document).ready` función hay un `viewModel object` creado y, a continuación, el `loadNavigationNodes()` se llama a la función en ese objeto. Esta función carga ya sea la jerarquía de navegación generado anteriormente almacenada en el almacenamiento local de HTML5 del explorador del cliente o llama a la función `queryRemoteInterface()`.

`QueryRemoteInterface()`genera una solicitud utilizando la `getRequest()` función con el parámetro de consulta definida anteriormente en la secuencia de comandos y, a continuación, devuelve datos desde el servidor. Estos datos están esencialmente una matriz de todos los sitios de la colección de sitios que se representan como objetos de transferencia de datos con varias propiedades. 

A continuación, se analizan estos datos en el que se han definido previamente `SPO.Models.NavigationNode` objetos que utilizan `Knockout.js` para crear propiedades perceptible para su uso por datos de enlace de los valores en el código HTML que se ha definido anteriormente. 

Los objetos, a continuación, se colocan en una matriz de resultados. Esta matriz se analiza en JSON con cobertura y se almacena en el almacenamiento de explorador local para mejorar el rendimiento en cargas de página futuras.

### <a name="benefits-of-this-approach"></a>Ventajas de este enfoque

Una de las principal ventajas de [este enfoque](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) es que mediante el uso de almacenamiento local de HTML5, el panel de navegación se almacena localmente para el usuario la próxima vez que carga la página. Se obtienen las mejoras de rendimiento principales de uso de la API de búsqueda para la navegación estructural; Sin embargo, se tarda algunos capacidad técnica para ejecutar y personalizar esta funcionalidad. 

En la [implementación de ejemplo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), los sitios se ordenan en la misma manera que la navegación estructural del cuadro; orden alfabético. Si desea que se desvían de este orden, sería más complicado desarrollar y mantener. Además, este enfoque requiere que se desvían de las páginas maestras compatibles. Si no se mantiene la página principal personalizada, el sitio se no participar en las actualizaciones y mejoras que Microsoft pone a las páginas maestras.

[Por encima del código](#about-the-javascript-file) presenta las siguientes dependencias:

- jQuery-http://jquery.com/
- KnockoutJS-http://knockoutjs.com/
- LINQ.js - http://linqjs.codeplex.com/, o github.com/neuecc/linq.js

La versión actual de LinqJS no contiene el método ByHierarchy que se usa en el código anterior y, interrumpirá el código de navegación. Para solucionar este problema, agregue el método siguiente al archivo Linq.js antes de la línea `Flatten: function ()`.

```
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

