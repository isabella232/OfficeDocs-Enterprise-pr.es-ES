---
title: El servicio web de URL y dirección IP de Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 8/6/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
ms.reviewer: pandrew
search.appverid:
- MET150
- MOE150
- BCS160
description: El servicio web de URL y dirección IP de Office 365 le ayuda a identificar y a diferenciar mejor el tráfico de red de Office 365, lo que facilita la evaluación, la configuración y la actualización de los cambios.
ms.openlocfilehash: 2dd725c39446d7e9cdad6b7e870bf7353ff1f8e3
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38031215"
---
# <a name="office-365-ip-address-and-url-web-service"></a>El servicio web de URL y dirección IP de Office 365

El servicio web de URL y dirección IP de Office 365 le ayuda a identificar y a diferenciar mejor el tráfico de red de Office 365, lo que facilita la evaluación, la configuración y la actualización de los cambios. Este servicio web basado en REST reemplaza los archivos XML anteriores descargables, que se han retirado el 2 de octubre de 2018.

Como cliente o proveedor de dispositivo de red perimetral, puede crear el servicio web para las entradas de direcciones IP y FQDN de Office 365. Puede obtener acceso a los datos directamente en un explorador web con estas direcciones URL:

- Para obtener la versión más reciente de los intervalos de direcciones IP y URL de Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Si desea ver los datos de la página de intervalos de direcciones IP y URL de Office 365 para los firewalls y servidores proxy, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Para obtener los últimos cambios desde finales de julio de 2018 cuando se publicó por primera vez el servicio web, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Como cliente, puede usar este servicio web para:

- Actualizar los scripts de PowerShell para obtener datos de puntos de conexión de Office 365 y modificar el formato de los dispositivos de redes.
- Usar esta información para actualizar los archivos PAC implementados en los equipos cliente.

Como proveedor de dispositivos de red perimetral, puede usar este servicio web para:

- Crear y probar software de dispositivos para descargar la lista de configuración automatizada.
- Comprobar la versión actual.
- Obtener los cambios actuales.

> [!NOTE]
> Si usa Azure ExpressRoute para conectarse a Office 365, consulte [Azure ExpressRoute para Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) para familiarizarse con los servicios de Office 365 compatibles con Azure ExpressRoute. Revise también el artículo [Direcciones URL e intervalos de direcciones IP de Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) para conocer las solicitudes de red para las aplicaciones de Office 365 que requieren conectividad a Internet. Esto le ayudará a configurar mejor los dispositivos de seguridad de perimetral.

Para obtener más información, vea:

- [Entrada de blog con el anuncio en el foro de la Comunidad de profesionales de Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Foro de la Comunidad de profesionales de Office 365 para dudas sobre el uso de los servicios web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>Parámetros comunes

Estos parámetros son comunes a todos los métodos de servicio web:

- **format=<JSON | CSV>**: de forma predeterminada, el formato de datos devueltos es JSON. Use este parámetro opcional para devolver los datos en formato de valores separados por comas (CSV).
- **ClientRequestId=\<guid>**: un GUID obligatorio que se genera para la asociación del cliente. Genere un GUID único para cada equipo que llama al servicio web (los scripts que se incluyen en esta página generan un GUID por usted). No use los GUID que se muestran en los ejemplos siguientes, puesto que el servicio web puede bloquearlos en el futuro. El formato GUID es _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, donde x representa un número hexadecimal.

  Para generar un GUID, puede usar el comando de PowerShell [New-GUID](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) o usar un servicio en línea como el [Generador GUID en línea](https://www.guidgenerator.com/).

## <a name="version-web-method"></a>Método web de versión

Microsoft actualiza las entradas de direcciones IP y FQDN de Office 365 al final de cada mes. En ocasiones, las actualizaciones fuera de banda se publican debido a incidencias de soporte técnico, actualizaciones de seguridad u otros requisitos operativos.

Los datos de cada instancia publicada se asignan a un número de versión y el método web de versión le permite buscar la versión más reciente de cada una de las instancias del servicio de Office 365. Le recomendamos que compruebe la versión no más de una vez cada hora.

Los parámetros del método web de versión son:

- **AllVersions=<true | false>**: de forma predeterminada, la versión devuelta es la más reciente. Incluya este parámetro opcional para solicitar todas las versiones publicadas desde la primera publicación del servicio web.
- **Format=<JSON | CSV | RSS>**: además de los formatos JSON y CSV, el método web de versión también es compatible con RSS. Puede usar este parámetro opcional con el parámetro _AllVersions=true_ para solicitar una fuente RSS que pueda usarse con Outlook u otros lectores de RSS.
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**: este parámetro opcional especifica la instancia para la que se devolverá la versión. Si se omite, se devuelven todas las instancias. Instancias válidas son: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.

El método web de versión no está limitado y nunca devuelve códigos de respuesta HTTP 429. La respuesta al método web de versión incluye un encabezado Cache-Control que recomienda almacenar los datos durante 1 hora. El resultado del método web de versión puede ser un registro único o una matriz de registros. Los elementos de cada registro son:

- instance: el nombre corto de la instancia de servicio de Office 365.
- latest: la versión más reciente de los puntos de conexión de la instancia especificada.
- versions: una lista de todas las versiones anteriores de la instancia especificada. Este elemento solo se incluye si el parámetro _AllVersions_ es verdadero.

### <a name="examples"></a>Ejemplos:

Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este URI devuelve la versión más reciente de cada instancia de servicio de Office 365. Resultado de ejemplo:

```json
[
 {
  "instance": "Worldwide",
  "latest": "2018063000"
 },
 {
  "instance": "USGovDoD",
  "latest": "2018063000"
 },
 {
  "instance": "USGovGCCHigh",
  "latest": "2018063000"
 },
 {
  "instance": "China",
  "latest": "2018063000"
 },
 {
  "instance": "Germany",
  "latest": "2018063000"
 }
]
```

> [!IMPORTANT]
> El GUID para el parámetro ClientRequestID en estos URI es solo un ejemplo. Para probar los URI de servicio web, genere su propio GUID. El servicio web podría bloquear en el futuro los GUID que se muestran en estos ejemplos.

Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este URI devuelve la versión más reciente de la instancia de servicio especificada de Office 365. Resultado de ejemplo:

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

Ejemplo 3 de URI de solicitud: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este URI muestra los resultados en formato CSV. Resultado de ejemplo:

```csv
instance,latest
Worldwide,2018063000
```

Ejemplo 4 de URI de solicitud: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este URI muestra todas las versiones anteriores que se han publicado para la instancia de servicio de Office 365 en todo el mundo. Resultado de ejemplo:

```json
{
  "instance": "Worldwide",
  "latest": "2018063000",
  "versions": [
    "2018063000",
    "2018062000"
  ]
}
```

Ejemplo 5 de URI de fuente RSS: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)

Este URI muestra una fuente RSS de las versiones publicadas que incluyen vínculos a la lista de cambios de cada versión. Resultado de ejemplo:

```xml
<?xml version="1.0" encoding="ISO-8859-1"?>
<rss version="2.0" xmlns:a10="https://www.w3.org/2005/Atom">
<channel>
<link>https://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
```

## <a name="endpoints-web-method"></a>Método web de puntos de conexión

El método web de puntos de conexión devuelve todos los registros de intervalos de direcciones IP y URL que conforman el servicio de Office 365. Los datos más recientes del método web de los puntos de conexión se deben usar siempre para la configuración del dispositivo de red. Microsoft avisa con 30 días de antelación de publicar nuevas adiciones, para darle tiempo de actualizar las listas de control de acceso y las listas de omisión del servidor proxy. Recomendamos llamar de nuevo al método web de puntos de conexión solo cuando la versión del método web indica que hay disponible una nueva versión de los datos.

Los parámetros del método web de puntos de conexión son:

- **ServiceAreas=<Common | Exchange | SharePoint | Skype>**: una lista separada por comas de las áreas de servicio. Los elementos válidos son _Common_, _Exchange_, _SharePoint_ y _Skype_. Como los elementos del área de servicio _Common_ son un requisito previo de todas las demás áreas de servicio, el servicio web siempre los incluye. Si no incluye este parámetro, se devolverán todas las áreas de servicio.
- **TenantName=<tenant_name>**: su nombre de inquilino de Office 365. El servicio web toma el nombre que usted proporciona y lo inserta en las partes de URL que incluyen el nombre de inquilino. Si no proporciona un nombre de inquilino, los elementos de las direcciones URL tendrán el carácter comodín (\*).
- **NoIPv6=<true | false>**: establezca el valor en _true_ para excluir las direcciones IPv6 del resultado, si no usa IPv6 en la red.
- **Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**: este parámetro obligatorio especifica la instancia desde la que se devolverán los puntos de conexión. Instancias válidas son: _Worldwide_, _China_, _Germany_, _USGovDoD_ y _USGovGCCHigh_.

Si llama al método web de puntos de conexión demasiadas veces desde la misma dirección IP de cliente, es posible que reciba el código de respuesta HTTP _429 (Demasiadas solicitudes)_. Si recibe este código de respuesta, espere 1 hora antes de repetir la solicitud o genere un nuevo GUID. Como recomendación general, solo debe llamar al método web de puntos de conexión cuando el método web de versión indica que hay una nueva versión disponible.

El resultado del método web de puntos de conexión es una matriz de registros en la que cada registro representa un conjunto específico de puntos de conexión. Los elementos de cada registro son:

- id: el número de identificador inmutable del conjunto de puntos de conexión.
- serviceArea: el área de servicio que forma parte de: _Common_, _Exchange_, _SharePoint_ o _Skype_.
- urls: las URL del conjunto de puntos de conexión. Una matriz JSON de registros DNS. Se omite si está en blanco.
- tcpPorts: puertos TCP del conjunto de puntos de conexión. El formato de todos los elementos de los puertos es una lista separada por coma de puertos o intervalos de puertos separados por un carácter de guión (-). Los puertos se aplican a todas las direcciones IP y URL en el conjunto de puntos de conexión de una categoría determinada. Se omite si está en blanco.
- udpPorts: los puertos UDP de los intervalos de direcciones IP en este conjunto de puntos de conexión. Se omite si está en blanco.
- ips: los intervalos de direcciones IP asociados a este punto de conexión asociado a los puertos TCP o UDP indicados. Una matriz JSON de intervalos de direcciones IP. Se omite si está en blanco.
- category: la categoría de conectividad del conjunto de puntos de conexión. Los valores válidos son _Optimize_, _Allow_ y _Default_. Si busca el resultado del método web de puntos de conexión para la categoría de una dirección IP o dirección URL específica, es posible que la consulta devuelva varias categorías. En ese caso, siga la recomendación de la categoría de prioridad más alta. Por ejemplo, si el punto de conexión se muestra tanto en _Optimize_ como en _Allow_, debe seguir los requisitos de _Optimize_. Obligatorio.
- expressRoute: _True_ si este conjunto de puntos de conexión se enruta a través de ExpressRoute; _False_ en caso contrario.
- required: _True_ si se requiere que el conjunto de puntos de conexión tenga conectividad para que sea compatible Office 365. _False_ si este conjunto de puntos de conexión es opcional.
- notes: para puntos de conexión opcionales, este texto describe la funcionalidad de Office 365 que no será disponible si no se puede tener acceso a las direcciones IP o las direcciones URL en este conjunto de puntos de conexión en el nivel de red. Se omite si está en blanco.

### <a name="examples"></a>Ejemplos:

Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este URI obtiene todos los puntos de conexión de la instancia Worldwide de Office 365 para todas las cargas de trabajo. Ejemplo de resultado en el que se muestra un extracto del resultado:

```json
[
 {
  "id": 1,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.protection.outlook.com"
   ],
  "ips":
   [
    "2a01:111:f403::/48", "23.103.132.0/22", "23.103.136.0/21", "23.103.198.0/23", "23.103.212.0/22", "40.92.0.0/14", "40.107.0.0/17", "40.107.128.0/18", "52.100.0.0/14", "213.199.154.0/24", "213.199.180.128/26", "94.245.120.64/26", "207.46.163.0/24", "65.55.88.0/24", "216.32.180.0/23", "23.103.144.0/20", "65.55.169.0/24", "207.46.100.0/24", "2a01:111:f400:7c00::/54", "157.56.110.0/23", "23.103.200.0/22", "104.47.0.0/17", "2a01:111:f400:fc00::/54", "157.55.234.0/24", "157.56.112.0/24", "52.238.78.88/32"
   ],
  "tcpPorts": "443",
  "expressRoute": true,
  "category": "Allow"
 },
 {
  "id": 2,
  "serviceArea": "Exchange",
  "serviceAreaDisplayName": "Exchange Online",
  "urls":
   [
    "*.mail.protection.outlook.com"
   ],
```

Tenga en cuenta que el resultado completo de la solicitud en este ejemplo contiene otros conjuntos de puntos de conexión.

Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este ejemplo obtiene extremos de la instancia Worldwide de Office 365 para Exchange Online y solo dependencias.

El resultado para el ejemplo 2 es similar al del ejemplo 1, excepto que los resultados no incluirán puntos de conexión para SharePoint Online o Skype Empresarial Online.

## <a name="changes-web-method"></a>Método web de cambios

El método web de cambios devuelve las actualizaciones más recientes que se han publicado y, por lo general, los cambios en los intervalos de direcciones IP y URL del mes anterior.

Los cambios a datos de los puntos de conexión más críticos son las direcciones IP y URL nuevas. Si no se agrega una dirección IP a la lista de control de acceso de un firewall o una dirección URL a la lista de omisiones del servidor proxy, los usuarios de Office 365 de ese dispositivo de red pueden experimentar una interrupción. Independientemente de los requisitos operativos, los nuevos puntos de conexión se publican en el servicio web 30 días antes de la fecha en la que se aprovisionan los puntos de conexión, para darle tiempo de actualizar las listas de control de acceso y las listas de omisión del servidor proxy.

El parámetro obligatorio del método web de cambios es:

- **Version=\<YYYYMMDDNN>**: parámetro obligatorio de ruta de URL. Este valor es la versión que ha implementado actualmente. El servicio web devolverá los cambios desde esa versión. El formato es _AAAAMMDDNN_, donde _NN_ es un número natural incrementado si hay varias versiones que deben publicarse en un solo día, con _00_ representando la primera actualización para un día determinado. El servicio web requiere que el parámetro _versión_ contenga exactamente 10 dígitos.

El método de web de cambios tiene una tasa limitada al igual que el método web de puntos de conexión.  Si recibe un código de respuesta HTTP 429, espere 1 hora antes de repetir la solicitud o genere un nuevo GUID.

El resultado del método web de cambios es una matriz de registros en la que cada uno representa un cambio de una versión específica de los puntos de conexión. Los elementos de cada registro son:

- id: el identificador inmutable del registro de cambios.
- endpointSetId: el identificador del registro del conjunto de puntos de conexión que se ha modificado.
- disposition: describe el resultado del cambio en el registro de conjuntos de puntos de conexión. Los valores _change_, _add_ o_remove_.
- impact: no todos los cambios serán igualmente importantes para todos los entornos. Este elemento describe el impacto previsto en un entorno perimetral de red de empresa como resultado de este cambio. Este elemento solo se incluye en los registros de cambio de la versión **2018112800** y posteriores. Las opciones para el impacto son: AddedIp, una dirección IP se ha agregado a Office 365 y pronto estará disponible en el servicio. Este es un cambio que debe realizar en un firewall u otro dispositivo de red perimetral de nivel 3. Si no agrega esto antes de empezar a usarlo, puede experimentar una interrupción.
  AddedUrl: se ha agregado una URL a Office 365 y pronto estará disponible en el servicio. Esto representa un cambio que debe realizar en un servidor proxy u otro dispositivo de red perimetral de análisis de URL. Si no agrega esta URL antes de empezar a usarlo, puede experimentar una interrupción.
  AddedIpAndUrl: se han agregado una dirección IP y una URL. Este es un cambio que necesita llevar a cabo en un dispositivo de nivel 3 de firewall, en un servidor proxy o un dispositivo de análisis de URL. Si no agrega este par IP/URL antes de empezar a usarlo, puede experimentar una interrupción.
  RemovedIpOrUrl: se ha eliminado al menos una dirección IP o una dirección URL de Office 365. Elimine los puntos de conexión de red de sus dispositivos perimetrales, pero no hay una fecha límite para hacerlo.
  ChangedIsExpressRoute: se ha cambiado el atributo de compatibilidad ExpressRoute. Si usa ExpressRoute, es posible que deba realizar una acción en función de la configuración.
  MovedIpOrUrl: se ha pasado una dirección IP o una dirección URL entre este conjunto de puntos de conexión y otro. Por lo general, no es necesario realizar ninguna acción.
  RemovedDuplicateIpOrUrl: se ha eliminado una dirección IP o URL duplicada, pero aún está publicada para Office 365. Por lo general, no es necesario realizar ninguna acción.
  OtherNonPriorityChanges: se ha cambiado algo menos importante que todas las demás opciones, como el contenido de un campo de nota.
- version: la versión del conjunto de puntos de conexión publicado en la que se ha introducido el cambio. Los números de versión tienen el formato _YYYYMMDDNN_, donde _NN_ es un número natural incrementado si hay varias versiones que deben publicarse en un solo día.
- previous: una subestructura en la que se detallan los valores anteriores de los elementos modificados en el conjunto de puntos de conexión. Esto no se incluye para los conjuntos de extremos recién añadidos.  Incluye _ExpressRoute_, _serviceArea_, _category,_, _required_, _tcpPorts_, _udpPorts_ y _notes_.
- current: una subestructura en la que se detallan los valores actualizados de los elementos de los cambios en el conjunto de puntos de conexión. Incluye _ExpressRoute_, _serviceArea_, _category,_, _required_, _tcpPorts_, _udpPorts_ y _notes_.
- add: una subestructura en la que se detallan los elementos que se agregarán a colecciones de conjuntos de puntos de conexión. Se omite si no hay adiciones.
  effectiveDate: define los datos cuando las adiciones estarán disponibles en el servicio.
  ips: los elementos que se agregarán a la matriz _ips_.
  urls: los elementos que se agregarán a la matriz _urls_.
- remove: una subestructura en la que se detallan los elementos que se eliminarán del conjunto de puntos de conexión. Se omite si no hay eliminaciones.
  ips: los elementos que se eliminarán de la matriz _ips_.
  urls: los elementos que se eliminarán de la matriz _urls_.

### <a name="examples"></a>Ejemplos:

Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Se solicitan todos los cambios anteriores a la instancia de servicio worldwide de Office 365. Resultado de ejemplo:

```json
[
 {
  "id": 424,
  "endpointSetId": 32,
  "disposition": "Change",
  "version": "2018062700",
  "remove":
   {
    "urls":
     [
      "*.api.skype.com", "skypegraph.skype.com"
     ]
   }
 },
 {
  "id": 426,
  "endpointSetId": 31,
  "disposition": "Change",
  "version": "2018062700",
  "add":
   {
    "effectiveDate": "20180609",
    "ips":
     [
      "51.140.203.190/32"
     ]
   },
  "remove":
   {
    "ips":
     [
```

Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Se solicitan los cambios desde la versión especificada a la instancia Worldwide de Office 365. En este caso, la versión especificada es la más reciente. Resultado de ejemplo:

```json
[
  {
    "id":3,
    "endpointSetId":33,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["65.55.127.0/24","66.119.157.192/26","66.119.158.0/25",
      "111.221.76.128/25","111.221.77.0/26","207.46.5.0/24"]
    }
  },
  {
    "id":4,
    "endpointSetId":45,
    "changeDescription":"Removing old IP prefixes",
    "disposition":"Change",
    "version":"2018031301",
    "remove":{
      "ips":["13.78.93.8/32","40.113.87.220/32","40.114.149.220/32",
      "40.117.100.83/32","40.118.214.164/32","104.208.31.113/32"]
    }
  }
]
```

## <a name="example-powershell-script"></a>Ejemplo de script de PowerShell

Este es un script de PowerShell que puede ejecutar para ver si hay acciones que debe realizar para los datos actualizados. Puede ejecutar este script como tarea programada para comprobar si hay una actualización de la versión. Para evitar una carga excesiva en el servicio web, intente no ejecutar el script más de una vez cada hora.

Este script hace lo siguiente:

- Comprueba el número de versión de los puntos de conexión de las instancias Worldwide de Office 365 actuales llamando a la API de REST del servicio web.
- Comprueba si hay un archivo de versión actual en _$env:TEMP\O365_endpoints_latestversion.txt_. La ruta de acceso de la variable global **$env:Temp** es, por lo general, _C:\Users\\ <nombre_usuario\>\AppData\Local\Temp_.
- Si esta es la primera vez que se ejecuta el script, este devuelve la versión actual y todas las direcciones IP y URL actuales, escribe la versión de los puntos de conexión en el archivo _$env:TEMP\O365_endpoints_latestversion.txt_ y el resultado de los datos de los puntos de conexión en el archivo _$env:TEMP\O365_endpoints_data.txt_. Puede modificar la ruta de acceso y/o el nombre del archivo de salida editando las líneas siguientes:

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- En cada ejecución subsiguiente del script, si la versión más reciente del servicio web es la misma que la versión del archivo _O365_endpoints_latestversion.txt_, el script saldrá sin realizar cambios.
- Si la versión más reciente del servicio web es más reciente que la versión del archivo _O365_endpoints_latestversion.txt_, el script devuelve los puntos de conexión y los filtros de los puntos de conexión de las categorías **Allow** y **Optimize**, actualiza la versión en el archivo _O365_endpoints_latestversion.txt_ y escribe los datos actualizados en el archivo _O365_endpoints_data.txt_.

El script genera un _ClientRequestId_ único para el equipo en el que se ejecuta y reutiliza este identificador en varias llamadas. Este ID se almacena en el archivo _O365_endpoints_latestversion.txt_.

### <a name="to-run-the-powershell-script"></a>Ejecución del script de PowerShell

1. Copie el script y guárdelo en su unidad de disco duro local o en la ubicación de scripts como _Get-O365WebServiceUpdates.ps1_.
1. Ejecute el script en el editor de scripts que prefiera, como PowerShell ISE o VS Code, o desde una consola de PowerShell con el comando siguiente:

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    No hay ningún parámetro para pasar al script.

```powershell
<# Get-O365WebServiceUpdates.ps1
From https://aka.ms/ipurlws
v1.1 8/6/2019

DESCRIPTION
This script calls the REST API of the Office 365 IP and URL Web Service (Worldwide instance)
and checks to see if there has been a new update since the version stored in an existing
$Env:TEMP\O365_endpoints_latestversion.txt file in your user directory's temp folder
(usually C:\Users\<username>\AppData\Local\Temp).
If the file doesn't exist, or the latest version is newer than the current version in the
file, the script returns IPs and/or URLs that have been changed, added or removed in the latest
update and writes the new version and data to the output file $Env:TEMP\O365_endpoints_data.txt.

USAGE
Run as a scheduled task every 60 minutes.

PARAMETERS
n/a

PREREQUISITES
PS script execution policy: Bypass
PowerShell 3.0 or later
Does not require elevation
#>

#Requires -Version 3.0

# web service root URL
$ws = "https://endpoints.office.com"
# path where output files will be stored
$versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
$datapath = $Env:TEMP + "\O365_endpoints_data.txt"

# fetch client ID and version if version file exists; otherwise create new file and client ID
if (Test-Path $versionpath) {
    $content = Get-Content $versionpath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
    Write-Output ("Version file exists! Current version: " + $lastVersion)
}
else {
    Write-Output ("First run! Creating version file at " + $versionpath + ".")
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $versionpath
}

# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"
    # write the new version number to the version file
    @($clientRequestId, $version.latest) | Out-File $versionpath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
    # URL results
    $flatUrls = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $urls = $(if ($endpointSet.urls.Count -gt 0) { $endpointSet.urls } else { @() })
        $urlCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $urlCustomObjects = $urls | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    url      = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $urlCustomObjects
    }
    # IPv4 results
    $flatIp4s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings contain dots
        $ip4s = $ips | Where-Object { $_ -like '*.*' }
        $ip4CustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ip4CustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip4CustomObjects
    }
    # IPv6 results
    $flatIp6s = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv6 strings contain colons
        $ip6s = $ips | Where-Object { $_ -like '*:*' }
        $ip6CustomObjects = @()
        if ($endpointSet.category -in ("Optimize")) {
            $ip6CustomObjects = $ip6s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ip6CustomObjects
    }

    # write output to screen
    Write-Output ("Client Request ID: " + $clientRequestId)
    Write-Output ("Last Version: " + $lastVersion)
    Write-Output ("New Version: " + $version.latest)
    Write-Output ""
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "IPv6 Firewall IP Address Ranges"
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    Write-Output ("IP and URL data written to " + $datapath)

    # write output to data file
    Write-Output "Office 365 IP and UL Web Service data" | Out-File $datapath
    Write-Output "Worldwide instance" | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output ("Version: " + $version.latest) | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv4 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp4s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "IPv6 Firewall IP Address Ranges" | Out-File $datapath -Append
    ($flatIp6s.ip | Sort-Object -Unique) -join "," | Out-File $datapath -Append
    Write-Output "" | Out-File $datapath -Append
    Write-Output "URLs for Proxy Server" | Out-File $datapath -Append
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-File $datapath -Append
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date."
}
```

## <a name="example-python-script"></a>Ejemplo de script de Python

Este es un script de Python, probado con Python 3.6.3 en Windows 10, que puede ejecutar para ver si hay acciones que debe seguir para los datos actualizados. Este script comprueba el número de versión de los extremos de la instancia Worldwide de Office 365. Cuando se produce un cambio, se descargan los extremos y filtros de los extremos de categoría _Allow_ y _Optimize_. También se usa un único ClientRequestId en varias llamadas y se guarda la versión más reciente que se encuentra en un archivo temporal. Debe llamar a este script una vez cada hora para comprobar si hay una actualización de versión.

```python
import json
import os
import urllib.request
import uuid
# helper to call the webservice and parse the response
def webApiGet(methodName, instanceName, clientRequestId):
    ws = "https://endpoints.office.com"
    requestPath = ws + '/' + methodName + '/' + instanceName + '?clientRequestId=' + clientRequestId
    request = urllib.request.Request(requestPath)
    with urllib.request.urlopen(request) as response:
        return json.loads(response.read().decode())
# path where client ID and latest version number will be stored
datapath = os.environ['TEMP'] + '\endpoints_clientid_latestversion.txt'
# fetch client ID and version if data exists; otherwise create new file
if os.path.exists(datapath):
    with open(datapath, 'r') as fin:
        clientRequestId = fin.readline().strip()
        latestVersion = fin.readline().strip()
else:
    clientRequestId = str(uuid.uuid4())
    latestVersion = '0000000000'
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + latestVersion)
# call version method to check the latest version, and pull new data if version number is different
version = webApiGet('version', 'Worldwide', clientRequestId)
if version['latest'] > latestVersion:
    print('New version of Office 365 worldwide commercial service instance endpoints detected')
    # write the new version number to the data file
    with open(datapath, 'w') as fout:
        fout.write(clientRequestId + '\n' + version['latest'])
    # invoke endpoints method to get the new data
    endpointSets = webApiGet('endpoints', 'Worldwide', clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into tuples with port and category
    flatUrls = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            category = endpointSet['category']
            urls = endpointSet['urls'] if 'urls' in endpointSet else []
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatUrls.extend([(category, url, tcpPorts, udpPorts) for url in urls])
    flatIps = []
    for endpointSet in endpointSets:
        if endpointSet['category'] in ('Optimize', 'Allow'):
            ips = endpointSet['ips'] if 'ips' in endpointSet else []
            category = endpointSet['category']
            # IPv4 strings have dots while IPv6 strings have colons
            ip4s = [ip for ip in ips if '.' in ip]
            tcpPorts = endpointSet['tcpPorts'] if 'tcpPorts' in endpointSet else ''
            udpPorts = endpointSet['udpPorts'] if 'udpPorts' in endpointSet else ''
            flatIps.extend([(category, ip, tcpPorts, udpPorts) for ip in ip4s])
    print('IPv4 Firewall IP Address Ranges')
    print(','.join(sorted(set([ip for (category, ip, tcpPorts, udpPorts) in flatIps]))))
    print('URLs for Proxy Server')
    print(','.join(sorted(set([url for (category, url, tcpPorts, udpPorts) in flatUrls]))))

    # TODO send mail (e.g. with smtplib/email modules) with new endpoints data
else:
    print('Office 365 worldwide commercial service instance endpoints are up-to-date')
```

## <a name="web-service-interface-versioning"></a>Control de versiones de la interfaz de servicio web

En el futuro, es posible que se necesiten actualizaciones de los parámetros o resultados de estos métodos de servicio web. Después de que se publique la versión de disponibilidad general de estos servicios web, Microsoft hará lo posible para avisar con antelación sobre actualizaciones de material en el servicio web. Cuando Microsoft cree que una actualización necesitará realizar cambios en los clientes que usan el servicio web, mantendrá la versión previa (una versión anterior) del servicio web disponible durante al menos 12 meses después de la publicación de la nueva versión. Es posible que los clientes que no se actualicen durante ese tiempo no puedan tener acceso al servicio web y a sus métodos. Los clientes deben asegurarse de que los clientes del servicio web sigan funcionando sin errores si se llevan a cabo los siguientes cambios en la firma de la interfaz de servicio web:

- Agregar un nuevo parámetro opcional a un método web existente que no tenga que facilitarse mediante clientes antiguos y que no afecte al resultado que recibe un cliente anterior.
- Agregar un nuevo atributo con nombre en uno de los elementos REST de respuesta o una de las columnas adicionales a la respuesta CSV.
- Agregar un nuevo método web con otro nombre al que no llamen los clientes anteriores.

## <a name="update-notifications"></a>Notificaciones de actualización

Puede usar algunos métodos diferentes para recibir notificaciones de correo electrónico cuando se publiquen cambios en las direcciones IP y URL en el servicio web.

- Para usar una solución de Microsoft Flow, vea [Usar Microsoft Flow para recibir un correo electrónico de cambios en las direcciones IP y URL de Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).
- Para implementar una aplicación lógica de Azure con una plantilla de ARM, vea [Notificación de actualización de Office 365 (v1.1)](https://aka.ms/ipurlws-updates-template).
- Para escribir su propio script de notificación con PowerShell, vea [Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage).

## <a name="exporting-a-proxy-pac-file"></a>Exportar un archivo proxy PAC

[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) es un script de PowerShell que lee los puntos de conexión de red más recientes desde el servicio web URL y la dirección IP de Office 365, y crea un archivo PAC de ejemplo. Para obtener más información sobre cómo usar Get-PacFile, vea [Usar un archivo PAC para el enrutamiento directo del tráfico fundamental de Office 365](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).

## <a name="related-topics"></a>Temas relacionados
  
[Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)

[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)

[Evaluar la conectividad de red de Office 365](assessing-network-connectivity.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimización de la red para Skype Empresarial Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)
