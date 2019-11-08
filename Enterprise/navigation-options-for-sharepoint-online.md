---
title: Opciones de navegación para SharePoint Online
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: En este artículo se describen las opciones de navegación sitios con la publicación de SharePoint habilitada en SharePoint Online. La elección y configuración de la navegación afectan significativamente al rendimiento y la escalabilidad de los sitios de SharePoint Online. Este artículo no se aplica a los sitios de grupo clásicos.
ms.openlocfilehash: fa180e1904ef57f28e512c6d6ff163f2f4a483ad
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031265"
---
# <a name="navigation-options-for-sharepoint-online"></a>Opciones de navegación para SharePoint Online

En este artículo se describen las opciones de navegación sitios con la publicación de SharePoint habilitada en SharePoint Online. La elección y configuración de la navegación afectan significativamente al rendimiento y la escalabilidad de los sitios de SharePoint Online.

## <a name="overview"></a>Información general

La configuración del proveedor de navegación puede afectar significativamente al rendimiento de todo el sitio, y se debe tener en cuenta para elegir un proveedor de navegación y una configuración que se escale con eficacia para los requisitos de un sitio de SharePoint. Hay dos proveedores de navegación preparados, así como implementaciones de navegación personalizadas.

Se recomienda la primera opción, la [**navegación administrada (metadatos)**](#using-managed-navigation-and-metadata-in-sharepoint-online), y es una de las opciones predeterminadas de SharePoint Online; sin embargo, se recomienda deshabilitar el recorte de seguridad a menos que sea necesario. El recorte de seguridad está habilitado como configuración segura de forma predeterminada para este proveedor de navegación; sin embargo, muchos sitios no requieren la sobrecarga de recorte de seguridad, ya que los elementos de navegación suelen ser coherentes para todos los usuarios del sitio. Con la configuración recomendada para deshabilitar el recorte de seguridad, este proveedor de navegación no necesita la enumeración de la estructura del sitio y es altamente escalable con un impacto aceptable en el rendimiento.

La segunda opción, [**navegación estructural**](#using-structural-navigation-in-sharepoint-online), **no es una opción de navegación recomendada en SharePoint Online**. Este proveedor de navegación se diseñó para una topología local con compatibilidad limitada en SharePoint Online. Aunque proporciona un conjunto adicional de funcionalidades en lugar de otras opciones de navegación, estas características, incluidos el recorte de seguridad y la enumeración de la estructura del sitio, tienen un costo de llamadas de servidor excesivas y afectan a la escalabilidad y al rendimiento cuando se usan. Los sitios que usan la navegación estructurada que consumen demasiados recursos pueden estar sujetos a limitación.

Además de los proveedores de navegación preinstalados, muchos clientes han implementado correctamente implementaciones de navegación personalizadas alternativas. Una clase común de implementaciones de navegación personalizadas adopta patrones de diseño representados por el cliente que almacenan una memoria caché local de nodos de navegación. (Vea **[scripting del lado cliente basado en búsquedas](#using-search-driven-client-side-scripting)** en este artículo).

Estos proveedores de navegación tienen un par de ventajas clave: 
- Por lo general, funcionan bien con diseños de página dinámicos.
- Son extremadamente escalables y funcionan porque pueden representarse sin costo de recursos (y actualizar en segundo plano después de un tiempo de espera). 
- Estos proveedores de navegación pueden recuperar datos de navegación mediante varias estrategias, desde configuraciones estáticas simples a varios proveedores de datos dinámicos. 

Un ejemplo de un proveedor de datos es usar una **navegación**basada en búsquedas, que permite la flexibilidad para enumerar los nodos de navegación y controlar de forma eficaz el recorte de seguridad. 

Hay otras opciones populares para crear **proveedores de navegación personalizados**. Revise [soluciones de navegación para portales de SharePoint Online](https://docs.microsoft.com/sharepoint/dev/solution-guidance/portal-navigation) para obtener más información sobre la creación de un proveedor de navegación personalizado.
  
## <a name="pros-and-cons-of-sharepoint-online-navigation-options"></a>Ventajas y desventajas de las opciones de navegación de SharePoint Online

En la tabla siguiente se resumen las ventajas y los inconvenientes de cada opción. 


|Navegación administrada  |Navegación estructural  |Navegación basada en búsquedas  |Proveedor de navegación personalizada  |
|---------|---------|---------|---------|
|Ti<br/><br/>Fácil de mantener<br/>Opción recomendada<br/>     |Ti<br/><br/>Fácil de configurar<br/>Seguridad recortada<br/>Se actualiza automáticamente cuando se agrega contenido<br/>|Ti<br/><br/>Seguridad recortada<br/>Se actualiza automáticamente cuando se agregan sitios<br/>Tiempo de carga rápida y estructura de navegación en caché local<br/>|Ti<br/><br/>Opción más amplia de opciones disponibles<br/>Carga rápida cuando se utiliza correctamente el almacenamiento en caché<br/>Muchas opciones funcionan bien con un diseño de página dinámico<br/>|
|Conos<br/><br/>No se actualiza automáticamente para reflejar la estructura del sitio<br/>Afecta al rendimiento si se habilita el recorte de seguridad<br/>|Conos<br/><br/>**No recomendado**<br/>**Impacto en el rendimiento y la escalabilidad**<br/>**Sujeto a la limitación**<br/>|Conos<br/><br/>No se pueden ordenar sitios fácilmente<br/>Requiere la personalización de la página maestra (habilidades técnicas necesarias)<br/>|Conos<br/><br/>Se requiere desarrollo personalizado<br/>Se necesita un origen de datos externo o almacenamiento en caché, por ejemplo Azure<br/>|

La opción más adecuada para su sitio dependerá de los requisitos de su sitio y de su capacidad técnica. Si desea un proveedor de navegación listo para usar que sea escalable, la navegación administrada con el recorte de seguridad deshabilitado es una buena opción.

La opción de navegación administrada se puede mantener mediante la configuración, no implica archivos de personalización de código y es significativamente más rápida que la navegación estructural. Si requiere el recorte de seguridad y se siente cómodo con una página maestra personalizada y tiene alguna función en la organización para mantener los cambios que se pueden producir en la página maestra predeterminada para SharePoint Online, la opción basada en búsquedas puede producir una mejor experiencia del usuario. Si tiene requisitos más complejos, un proveedor de navegación personalizado puede ser la opción correcta. NO se recomienda la navegación estructural.

Por último, es importante tener en cuenta que SharePoint está agregando proveedores de navegación adicionales y funcionalidad para arquitecturas de sitio de SharePoint modernas que aprovechan una jerarquía de sitios más acoplada y un modelo de concentrador y radio con sitios concentradores de SharePoint. Esto permite lograr muchos escenarios que no requieren el uso de la característica de publicación de SharePoint y estas configuraciones de navegación están optimizadas para la escalabilidad y la latencia en SharePoint Online. Tenga en cuenta que al aplicar el mismo principio, simplificando la estructura general del sitio de publicación de SharePoint a una estructura más plana, a menudo también mejora el rendimiento y la escala general. Esto significa que en lugar de tener una sola colección de sitios con cientos de sitios (subwebs), un mejor enfoque es disponer de muchas colecciones de sitios con muy pocos subsitios (subwebs).


## <a name="using-managed-navigation-and-metadata-in-sharepoint-online"></a>Usar la navegación administrada y los metadatos en SharePoint Online

La navegación administrada es otra opción precreada que puede usar para volver a crear la mayor parte de la funcionalidad como navegación estructural. Los metadatos administrados se pueden configurar para que el recorte de seguridad esté habilitado o deshabilitado. Cuando se configura con el recorte de seguridad deshabilitado, la navegación administrada es bastante eficiente ya que carga todos los vínculos de navegación con un número constante de llamadas del servidor. La habilitación de la reducción de seguridad, anula algunas de las ventajas de la navegación administrada y los clientes pueden elegir explorar una de las soluciones de navegación personalizadas para obtener una escalabilidad y un rendimiento óptimos.

Muchos sitios no requieren el recorte de seguridad, ya que la estructura de navegación suele ser coherente para todos los usuarios del sitio. Si se deshabilita el recorte de seguridad y se agrega un vínculo a la navegación que no tienen acceso a todos los usuarios, el vínculo seguirá mostrando pero conducirá a un mensaje de acceso denegado. No existe ningún riesgo de acceso involuntario al contenido.

### <a name="how-to-implement-managed-navigation-and-the-results"></a>Cómo implementar la navegación administrada y los resultados

Hay varios artículos sobre Docs.Microsoft.com acerca de los detalles de la navegación administrada, por ejemplo, vea [información general sobre la navegación administrada en SharePoint Server](https://docs.microsoft.com/sharepoint/administration/overview-of-managed-navigation).

Para implementar la navegación administrada, se configuran los términos con direcciones URL correspondientes a la estructura de navegación del sitio. La navegación administrada puede incluso creadosrse manualmente para reemplazar la navegación estructural en muchos casos. Por ejemplo:

![Estructura de sitio de SharePoint Online](media/SPONavOptionsListOfSites.png)

En el ejemplo siguiente se muestra el rendimiento de la navegación compleja mediante la navegación administrada.

![Rendimiento de navegación compleja con navegación administrada](media/SPONavOptionsComplexNavPerf.png)

Usar la navegación administrada de forma coherente mejora el rendimiento comparado con el enfoque de navegación estructural.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Uso de la navegación estructural en SharePoint Online

Esta es la navegación predefinida que se usa de forma predeterminada y es la solución más sencilla, pero, como tal, tiene un equilibrio entre rendimiento caro. No requiere personalización y un usuario no técnico también puede agregar elementos, ocultar elementos y administrar la navegación desde la página de configuración fácilmente. Sin embargo, esto también se aplica a la navegación administrada, por lo que se recomienda usar la navegación administrada, ya que también se puede administrar y controlar fácilmente, así como mejorar el rendimiento.

![Navegación estructural con la muestra de subsitios seleccionada](media/SPONavOptionsStructuredShowSubsites.png)
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Activar la navegación estructural en SharePoint Online

Ilustrar cómo se activa el rendimiento de una solución estándar de SharePoint Online con navegación estructural y la opción Mostrar subsitios. A continuación se muestra una captura de pantalla de la configuración que se encuentra en la **navegación**de **configuración** \> del sitio de página.
  
![Captura de pantalla que muestra subsitios](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analizar el rendimiento de la navegación estructural en SharePoint Online

Para analizar el rendimiento de una página de SharePoint, use la ficha **red** de las herramientas de desarrollo F12 de Internet Explorer. 
  
![Captura de pantalla que muestra la pestaña Red de herramientas de desarrollo F12](media/SPONavOptionsNetworks.png)
  
1. En la ficha **red** , haga clic en la página. aspx que se va a cargar y, a continuación, haga clic en la pestaña **detalles** .<br/> ![Captura de pantalla que muestra la pestaña Detalles](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)<br/>
2. Haga clic en **encabezados de respuesta**. <br/>![Captura de pantalla de la pestaña Detalles](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)<br/>SharePoint devuelve información de diagnóstico útil en sus encabezados de respuesta. 
3. Uno de los elementos de información más útiles es **SPRequestDuration** , que es el valor, en milisegundos, del tiempo que tardó una solicitud en procesarse en el servidor. En la siguiente captura de pantalla, **Mostrar subsitios** está desactivada para la navegación estructural. Esto significa que solo hay un vínculo a la colección de sitios en la navegación global:<br/>![Captura de pantalla que muestra los tiempos de carga como duración de solicitud](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)<br/>
4. La clave **SPRequestDuration** tiene un valor de 245 milisegundos. Esto representa el tiempo que tardó en devolver la solicitud. Como solo hay un elemento de navegación en el sitio, esta es una buena prueba de la forma en que SharePoint Online realiza sin una navegación intensiva. En la siguiente captura de pantalla se muestra cómo la adición en los subsitios afecta a esta clave.<br/>![Captura de pantalla que muestra una duración de solicitud de 2 502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)<br/>
  
La adición de los subsitios ha aumentado significativamente el tiempo que se tarda en devolver la solicitud de página para este sitio de ejemplo relativamente sencillo. Las jerarquías de sitio complejas, incluidas las páginas de navegación, y otras opciones de configuración y topología pueden aumentar drásticamente este impacto aún más.

## <a name="using-search-driven-client-side-scripting"></a>Uso de scripting de cliente basado en búsquedas

Mediante la búsqueda, puede aprovechar los índices que se han integrado en el fondo con el rastreo continuo. Los resultados de la búsqueda se extraen del índice de búsqueda y los resultados se reducen por seguridad. Esto suele ser más rápido que los proveedores de navegación preparados cuando se requiere el recorte de seguridad. Usar la búsqueda para la navegación estructural, sobre todo si tiene una estructura de sitio compleja, reducirá considerablemente el tiempo de carga de la página. La principal ventaja de esto sobre la navegación administrada es que se beneficia de la reducción de seguridad.

Este enfoque implica la creación de una página maestra personalizada y la sustitución del código de navegación precreado con HTML personalizado. Siga este procedimiento descrito en el siguiente ejemplo para reemplazar el código de navegación en el archivo `seattle.html`. En este ejemplo, se abrirá el `seattle.html` archivo y se reemplazará todo el `id=”DeltaTopNavigation”` elemento con código HTML personalizado.

### <a name="example-replace-the-out-of-the-box-navigation-code-in-a-master-page"></a>Ejemplo: reemplazar el código de navegación de precodificación en una página maestra

1.  Navegue a la página Configuración del sitio.
2.  Abra la galería de páginas maestras; para ello, haga clic en **páginas maestras**.
3.  Desde aquí puede navegar por la biblioteca y descargar el archivo `seattle.master`.
4.  Edite el código con un editor de texto y elimine el bloque de código en la siguiente captura de pantalla.<br/>![Eliminar el bloque de código que se muestra](media/SPONavOptionsDeleteCodeBlock.png)<br/>
5. Quite el código entre las `<SharePoint:AjaxDelta id=”DeltaTopNavigation”>` etiquetas `<\SharePoint:AjaxDelta>` y y reemplácela por el siguiente fragmento de código:<br/>

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
6. Reemplace la dirección URL de la etiqueta de anclaje de la imagen de carga al principio, por un vínculo a una imagen de carga en la colección de sitios. Después de realizar los cambios, cambie el nombre del archivo y, a continuación, cárguelo en la galería de páginas maestras. Esto genera un nuevo archivo. Master.<br/>
7. Este HTML es el marcado básico que rellenará los resultados de la búsqueda devueltos desde el código JavaScript. Tendrá que editar el código para cambiar el valor de var root = "site Collection URL" como se muestra en el siguiente fragmento de código:<br/>

```
var root = “https://spperformance.sharepoint.com/sites/NavigationBySearch”;
```
<br/>
8. Los resultados se asignan a self. Nodes y una jerarquía se crea a partir de los objetos mediante Linq. js, que asigna el resultado a una matriz self. hierarchy. Esta matriz es el objeto que está enlazado al HTML. Esto se realiza en la función toggleView () pasando el objeto Self a la función ko. applyBinding ().<br/>Esto hace que la matriz de jerarquías se enlace al siguiente HTML:<br/>

```
<div data-bind=”foreach: hierarchy” class=”noindex ms-core-listMenu-horizontalBox”>
```

Los controladores de eventos para `mouseenter` y `mouseexit` se agregan a la navegación de nivel superior para controlar los menús desplegables de subsitio que se realizan `addEventsToElements()` en la función.

En nuestro ejemplo de navegación compleja, una carga de página nueva sin el almacenamiento en caché local muestra el tiempo empleado en el servidor se ha reducido de la navegación estructural de Benchmark para obtener un resultado similar al del enfoque de navegación administrada.

### <a name="about-the-javascript-file"></a>Acerca del archivo JavaScript...

El archivo JavaScript completo es el siguiente:

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

Para resumir el código que se ha mostrado `jQuery $(document).ready` anteriormente en la función `viewModel object` , se ha creado `loadNavigationNodes()` una y, a continuación, se llama a la función en ese objeto. Esta función carga la jerarquía de navegación previamente creada almacenada en el almacenamiento local de HTML5 del explorador del cliente o llama a `queryRemoteInterface()`la función.

`QueryRemoteInterface()`compila una solicitud mediante la `getRequest()` función con el parámetro de consulta definido anteriormente en el script y, a continuación, devuelve datos del servidor. Estos datos son esencialmente una matriz de todos los sitios de la colección de sitios que se representan como objetos de transferencia de datos con diversas propiedades. 

A continuación, estos datos se analizan en los `SPO.Models.NavigationNode` objetos definidos anteriormente `Knockout.js` que usan para crear propiedades observables para su uso mediante el enlace de datos de los valores en el código HTML que se ha definido anteriormente. 

A continuación, los objetos se colocan en una matriz de resultados. Esta matriz se analiza en JSON usando knockout y se almacena en el almacenamiento local del explorador para mejorar el rendimiento en futuras cargas de páginas.

### <a name="benefits-of-this-approach"></a>Ventajas de este enfoque

Una de las principales ventajas de [este enfoque](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page) es que, al usar el almacenamiento local de HTML5, la navegación se almacena localmente para el usuario la próxima vez que cargue la página. Obtenemos mejoras de rendimiento principales al usar la API de búsqueda para la navegación estructural; sin embargo, se necesita cierta capacidad técnica para ejecutar y personalizar esta funcionalidad. 

En la [implementación del ejemplo](#example-replace-the-out-of-the-box-navigation-code-in-a-master-page), los sitios se ordenan de la misma manera que la navegación estructural de forma integrada; orden alfabético. Si desea desviarse de esta orden, sería más complicado su desarrollo y mantenimiento. Además, este enfoque requiere que se desvíe de las páginas maestras admitidas. Si no se mantiene la página maestra personalizada, el sitio perderá las actualizaciones y las mejoras que Microsoft realiza en las páginas maestras.

El [código anterior](#about-the-javascript-file) tiene las siguientes dependencias:

- jQueryhttps://jquery.com/
- KnockoutJS -https://knockoutjs.com/
- Linq. js- https://linqjs.codeplex.com/o github.com/neuecc/Linq.js

La versión actual de LinqJS no contiene el método ByHierarchy que se usó en el código anterior y romperá el código de navegación. Para solucionarlo, agregue el método siguiente al archivo Linq. js antes de la línea `Flatten: function ()`.

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

