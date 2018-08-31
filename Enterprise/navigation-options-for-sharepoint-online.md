---
title: Opciones de navegación para SharePoint Online
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 6/27/2018
ms.audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid: SPO160
ms.assetid: adb92b80-b342-4ecb-99a1-da2a2b4782eb
description: En este artículo se describe cómo mejorar los tiempos de carga de páginas de SharePoint Online mediante navegación administrada o navegación controlada por la búsqueda en la publicación de clásico.
ms.openlocfilehash: 6b2ee613d0cc6a6df92eb9b53374087a0ac2e5b7
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542968"
---
# <a name="navigation-options-for-sharepoint-online"></a>Opciones de navegación para SharePoint Online

En este artículo se describe cómo mejorar los tiempos de carga de páginas de SharePoint Online mediante navegación administrada o navegación controlada por la búsqueda en la publicación de clásico.
  
SharePoint Online con publicación clásica habilitada tiene dos áreas de navegación; Navegación global y navegación actual.
  
Navegación global es el menú de navegación superior mientras la navegación actual es el lado o en contexto a izquierda/derecha navegación dependen de la configuración de idioma y la página maestra utilizados.
  
Navegación puede afectar negativamente al rendimiento para el Portal completo como a menudo está configurado para su uso de todo el portal y como tal, es un elemento importante de cualquier sitio de SharePoint.
  
Navegación estructural no es la opción recomendada de navegación en SharePoint Online, tal y como se diseñó para una topología local con el recorte de seguridad y este diseño hace que las llamadas excesiva en el servidor y afecta al rendimiento cuando se usa.
  
Que el diseño ha cambiado con la introducción de los sitios de SharePoint moderno donde moderno tiene una jerarquía de sitios plana simplificado. Esto ha simplificado la navegación con una jerarquía simplificada que ha eliminado los problemas de rendimiento relacionados con la navegación.
  
Hay dos opciones de navegación del cuadro principal en SharePoint, así como una tercera, enfoque personalizado basado en búsquedas. Como alternativa, un cuarto y opción bastante popular es crear un proveedor personalizado de navegación. Revise [las soluciones de navegación para portales de SharePoint Online](https://docs.microsoft.com/en-us/sharepoint/dev/solution-guidance/portal-navigation) para obtener orientación sobre un proveedor de navegación personalizada. 
  
Cada opción tiene ventajas e inconvenientes, tal como se describe en la siguiente tabla.
  
|**Navegación estructural**|**Navegación administrada**|**Navegación controlada por la búsqueda**||**Proveedor de navegación personalizada**|
|:-----|:-----|:-----|:-----|:-----|
| Ventajas:  <br/>  Fácil de configurar  <br/>  Seguridad garantizada  <br/>  Se actualiza automáticamente cuando se agregan sitios  <br/> | Ventajas:  <br/>  Fácil de mantener  <br/>  Opción recomendada  <br/> | Ventajas:  <br/>  Seguridad garantizada  <br/>  Se actualiza automáticamente cuando se agregan sitios  <br/>  Rápido tiempo de carga y estructura de navegación en caché local  <br/> || Ventajas:  <br/>    <br/>  Mayor número de opciones / opciones disponibles  <br/>  Cargar Fast al almacenamiento en caché se usa correctamente  <br/> |
| Desventajas:  <br/> **No se recomienda** <br/> **Afecta al rendimiento** <br/> | Desventajas:  <br/>  No se actualiza automáticamente para reflejar la estructura del sitio  <br/>  Afecta al rendimiento si está habilitado el recorte de seguridad  <br/> | Desventajas:  <br/>  No se pueden ordenar sitios de forma sencilla  <br/>  Requiere la personalización de la página maestra (se requieren conocimientos técnicos)  <br/> || Desventajas:  <br/>  Se requiere desarrollo personalizado  <br/>  Origen de datos externo / caché almacena es necesario, por ejemplo, Azure  <br/> |
   
La opción más adecuada para su sitio dependerá de las necesidades del sitio y en su capacidad técnica. Si está familiarizado con el uso de una página maestra personalizada y tienen la capacidad de algunos en la organización para mantener los cambios que pueden producirse en la página maestra predeterminada para SharePoint Online, la opción controlados por búsqueda generarán la mejor experiencia de usuario. Si desea que un simple término medio entre la navegación estructural de fábrica y búsqueda, a continuación, la navegación administrada es una opción muy buena. Se puede mantener la opción de navegación administrada a través de configuración, no a los archivos de personalización de código y es mucho más rápido que la navegación estructural de cuadro.
  
Simplificación de la estructura general de su Portal clásico muy similar a moderno, ayuda a con el rendimiento y escala así como generales. Esto significa que en lugar de tener una única colección de sitios con cientos o miles de sitios (subwebs), un mejor enfoque consiste en tener muchas colecciones de sitios con subsitios muy pocos (subwebs).
  
Proporciona opciones adicionales de escala en el servicio, evita poner todo el contenido en una base de datos grande y en última instancia permite mayor flexibilidad para navegación y lo más importante es que la seguridad.
  
## <a name="using-structural-navigation-in-sharepoint-online"></a>Usar la navegación estructural en SharePoint Online

Esto es el panel de navegación del cuadro usado de forma predeterminada y es la solución más sencilla pero como tal, tiene un equilibrio rendimiento costosos. No requiere ninguna personalización y un usuario no técnico también fácilmente puede agregar elementos, ocultar los elementos y administrar la navegación desde la página de configuración. Esto es sin embargo también true para la navegación administrados por lo que se recomienda utilizar también navegación administrados como que pueden ser fácilmente administrada y controla así como.
  
### <a name="turning-on-structural-navigation-in-sharepoint-online"></a>Activar la navegación estructural en SharePoint Online

Para ilustrar cómo el rendimiento en una solución de SharePoint Online estándar con navegación estructural y el Mostrar subsitios opción activado. A continuación se captura una pantalla de configuración que se encuentra en la página **Configuración del sitio** \> **navegación**.
  
![Captura de pantalla que muestra subsitios](media/5b6a8841-34ed-4f61-b6d3-9d3e78d393e7.png)
  
### <a name="analyzing-structural-navigation-performance-in-sharepoint-online"></a>Analizar el rendimiento de la navegación estructural en SharePoint Online

Para analizar el rendimiento de una página de SharePoint, utilice la ficha **Red** de las herramientas de desarrollo F12 en Internet Explorer. 
  
![Captura de pantalla que muestra la pestaña Red de herramientas de desarrollo F12](media/e2aed8af-0843-487a-8b68-4f5260a2685e.png)
  
En la ficha **Red**, haga clic en la página .aspx que se está cargando y, a continuación, haga clic en la ficha **Detalles**. 
  
![Captura de pantalla que muestra la pestaña Detalles](media/ad85cefb-7bc5-4932-b29c-25f61b4ceeb2.png)
  
Haga clic en **Encabezados de respuesta**.
  
![Captura de pantalla de la pestaña Detalles](media/c47770ac-5b2b-4941-9830-c57565dec4cc.png)
  
SharePoint devuelve la información de diagnóstico útil en sus encabezados de respuesta. Uno de los más útiles es **SPRequestDuration**, que es el valor en milisegundos del tiempo que tardó en procesarse una solicitud en el servidor. 
  
En la pantalla siguiente **Mostrar subsitios** está desactivada para la navegación estructural. Esto significa que hay sólo el vínculo de la colección de sitios en la navegación global: 
  
![Captura de pantalla que muestra los tiempos de carga como duración de solicitud](media/3422b2e8-15ec-4bb9-ba86-0965b6b49b01.png)
  
La clave de **SPRequestDuration** tiene un valor de 245 milisegundos. Esto representa el tiempo que se tardó en devolver la solicitud. Dado que hay un solo elemento de navegación en el sitio, se trata de un buen rendimiento para cómo SharePoint Online realiza sin navegación gruesa. La captura de pantalla siguiente muestra cómo agregar en los subsitios que afecta a esta clave. 
  
![Captura de pantalla que muestra una duración de solicitud de 2 502 ms](media/618ee4e9-2ffa-4a22-b638-fa77b72292b8.png)
  
Agregar los subsitios ha aumentado significativamente el tiempo empleado en devolver la solicitud de página.
  
Las ventajas de usar la navegación estructurada regular es que fácilmente puede organizar el orden, ocultar sitios, agregar páginas, los resultados son restricciones de seguridad, y no se desvían de las páginas maestras compatibles que se usa en SharePoint Online.
  
## <a name="using-managed-navigation-and-managed-metadata-in-sharepoint-online"></a>Usar navegación administrada y metadatos administrados en SharePoint Online

La navegación administrada es otra opción de fábrica que puede utilizar para volver a crear al mismo tipo de funcionalidad que la navegación estructural.
  
La ventaja de usar metadatos administrados es que resulta mucho más rápido para recuperar los datos que el uso de contenido por consulta para crear la navegación del sitio. Aunque es que mucho más rápido no hay ninguna forma de recorte de seguridad los resultados por lo que si un usuario no tiene acceso a un sitio determinado, el vínculo seguirá mostrando pero dará lugar a un mensaje de error.
  
 **Cómo implementar la navegación administrada y los resultados**
  
Hay varios artículos de TechNet acerca de los detalles de la navegación administrada, por ejemplo, vea [información general de la navegación administrada en SharePoint Server 2013](https://go.microsoft.com/fwlink/?LinkId=708689).
  
Para implementar la navegación administrada, deberá tener permisos de administrador para el almacén de términos. Al configurar términos con direcciones URL que coinciden con la estructura de una colección de sitios, se puede usar la navegación administrada para reemplazar la navegación estructural. Por ejemplo:
  
![Captura de pantalla del ejemplo Subsite1](media/4155b4da-ccff-4e2a-92de-7803ac62982b.png)
  
En el ejemplo siguiente se muestra el rendimiento de la navegación compleja mediante navegación administrada.
  
![Captura de pantalla del ejemplo de SPRequestDuration](media/72257528-0ec6-48b0-85a5-efeb7432db5b.png)
  
El uso consistente de navegación administrada mejora el rendimiento en comparación con el contenido por enfoque de navegación estructural de consulta.
  
## <a name="using-search-driven-client-side-scripting"></a>Usar scripting de cliente por búsqueda

Mediante la búsqueda, se pueden aprovechar los índices que se compilan en segundo plano mediante el rastreo continuo. Esto significa que no existen consultas de contenido intensas. Los resultados de búsqueda se extraen del índice de búsqueda, y los resultados tiene seguridad garantizada. Esto es más rápido que usar consultas de contenido normales. Con la búsqueda de navegación estructural, especialmente si tiene una estructura de sitios compleja, acelerará considerablemente el tiempo de carga de páginas. La principal ventaja de esto con respecto a la navegación administrada es que usted se beneficia con la seguridad garantizada.
  
Este enfoque consiste en crear una página maestra personalizada y reemplazar el código de navegación de fábrica con HTML personalizado. Siga este procedimiento para reemplazar el código de navegación en el archivo seattle.html.
  
En este ejemplo, se abra el archivo seattle.html y reemplace todo el elemento **id = "DeltaTopNavigation"** con el código HTML personalizado. 
  
 **Ejemplo: Para reemplazar el código de navegación de fábrica en una página maestra**
  
1. Vaya a la página **Configuración del sitio**. 
    
2. Haga clic en **Páginas maestras** para abrir la galería de páginas maestras.
    
3. Desde aquí puede navegar por la biblioteca y descargar el archivo **seattle.master**.
    
4. Edite el código con un editor de texto y elimine el bloque de código en la siguiente captura de pantalla.
    
    ![Captura de pantalla del código de DeltaTopNavigation para eliminar](media/70db2cd2-660d-4e0d-9d5c-a5df331c73b4.png)
  
5. Quitar el código entre la \<SharePoint:AjaxDelta id = "DeltaTopNavigation"\> y \<\SharePoint:AjaxDelta\> de etiquetas y reemplácelo con el siguiente fragmento de código:
    
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

6. Reemplace la dirección URL en la carga de la imagen etiqueta delimitadora al principio, con un vínculo a una imagen de carga en la colección de sitios. Una vez realizados los cambios, cambie el nombre del archivo y, a continuación, cárguela en la Galería de páginas maestras. Esto genera un nuevo archivo. master.
    
7. Este código HTML es el marcado básicos que se va a rellenar con los resultados de búsqueda devueltos desde el código JavaScript. Tendrá que modificar el código siguiente para cambiar el valor para el `var root = "site collection URL"` como se muestra en el siguiente fragmento de código: 
    
  ```
  var root = "https://spperformance.sharepoint.com/sites/NavigationBySearch";
  ```

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
  var query = baseUrl + "'contentClass=\"STS_Web\"+path:" + root + "'&amp;trimduplicates=false&amp;rowlimit=300";
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
              if (cachedNodes &amp;&amp; timeStamp) {
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
              if (elem.children &amp;&amp; elem.children.length > 0) {
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
  
  ```

     $("li.level1").mouseover (función () { 
  
posición de var = $(this).position();
  
.find("ul.level2").css $(this) ({ancho: 100, izquierda: position.left + 10, top: 50});
    
     }) 
  
.MouseOut (función () {
  
.find("ul.level2").css $(this) ({izquierdo:-99999, superior: 0});
  
});
  
$("li.level2").mouseover (función () {
  
posición de var = $(this).position();
  
Console.log(JSON.stringify(Position));
  
.find("ul.level3").css $(this) ({ancho: 100, izquierda: position.left + 95, top: position.top});
    
     }) 
  
.MouseOut (función () {
  
.find("ul.level3").css $(this) ({izquierdo:-99999, superior: 0});
  
});
    
    } _spBodyOnLoadFunctionNames.push("InitCustomNav");
    
    To summarize the code shown above in the jQuery **[$(document).ready]** function there is a **[viewModel]** object created and then the **[loadNavigationNodes()]** function on that object is called. This function either loads the previously built navigation hierarchy stored in the HTML5 local storage of the client browser or it calls the function **[queryRemoteInterface()]**. 
    
    **[QueryRemoteInterface()]** builds a request using the **[getRequest()]** function with the query parameter defined earlier in the script and then returns data from the server. This data is essentially an array of all the sites in the site collection represented as data transfer objects with various properties. This data is then parsed into the previously defined **[SPO.Models.NavigationNode]** objects which use Knockout.js to create observable properties for use by data binding the values into the HTML that we defined earlier. The objects are then put into a results array. This array is parsed into JSON using Knockout and stored in the local browser storage for improved performance on future page loads. 
    
8. A continuación, se asignan los resultados a la matriz **[self.nodes]** y se crea una jerarquía de fuera de los objetos con linq.js asignar el resultado a una matriz **[self.heirarchy]**. Esta matriz es el objeto que está enlazado el código HTML. Esto se realiza en la función **[toggleView()]** , se pasa el objeto automático a la función **[ko.applyBinding()]** . Esto hace que la matriz de jerarquía enlazar el código HTML siguiente: 
    
  ```
  <div data-bind="foreach: hierarchy" class="noindex ms-core-listMenu-horizontalBox">
  ```

    Por último, se agregan los controladores de eventos para **[mouseenter]** y **[mouseexit]** para la navegación de nivel superior para controlar los menús de lista desplegable del subsitio que se realiza en la función **[addEventsToElements()]** . 
    
    Los resultados de la navegación pueden verse en la captura de pantalla siguiente:
    
    ![Captura de pantalla de los resultados de la navegación](media/020d34d2-942a-431b-9b26-6d2c8a6fde30.png)
  
    En nuestro ejemplo de navegación compleja, una carga de página nueva sin el almacenamiento en memoria caché local muestra que el tiempo empleado en el servidor se ha reducido con respecto a la navegación estructural de pruebas comparativas para obtener un resultado similar al enfoque de navegación administrada.
    
    ![Captura de pantalla de SPRequestDuration 301](media/307d7caf-e83a-40d9-a551-91d842521d03.png)
  
    Una de las principales ventajas de este enfoque es que mediante el almacenamiento local de HTML5, la navegación se almacena localmente para el usuario la próxima vez que cargue la página.
    
Obtenemos mejoras de rendimiento muy importantes del uso de la API de búsqueda para la navegación estructural. Sin embargo, esto requiere capacidad técnica para ejecutar y personalizar esta funcionalidad. En la implementación de ejemplo, los sitios se ordenan de la misma forma que la navegación estructural de fábrica (por orden alfabético). Si deseara usar otro orden, sería más complicado desarrollar y mantener. Además, este enfoque requiere que se desvíe de las páginas maestras compatibles. Si no se mantiene la página maestra personalizada, el sitio perderá las actualizaciones y mejoras que Microsoft realice en las páginas maestras.
  
El código anterior tiene las siguientes dependencias:
  
- jQuery-[http://jquery.com/](http://jquery.com/)
    
- KnockoutJS-[http://knockoutjs.com/](http://knockoutjs.com/)
    
- LINQ.js - [http://linqjs.codeplex.com/](http://linqjs.codeplex.com/), o [github.com/neuecc/linq.js](https://github.com/neuecc/linq.js/)
    
La versión actual de LinqJS no contiene el método ByHierarchy que se usa en el código anterior y, interrumpirá el código de navegación. Para solucionar este problema, agregue el método siguiente al archivo Linq.js antes de la línea "Flatten: función ()".
  
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


