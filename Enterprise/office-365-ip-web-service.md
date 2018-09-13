---
title: Dirección IP de Office 365 y servicio web de URL
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 9/4/2018
ms.audience: ITPro
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
description: Para ayudarle a identificar y diferenciar el tráfico de red de Office 365, un nuevo servicio web publica puntos de conexión de Office 365, con lo cual le resultará más fácil evaluar, configurar y mantenerse al día con los cambios. Este nuevo servicio web reemplaza los archivos XML descargables que están disponibles actualmente.
ms.openlocfilehash: 3abd6a0692ae4d66c76f8c0d65653b83646c6e23
ms.sourcegitcommit: d07feeba2e886febc6a57a5c33b0df02b3db5631
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "23830898"
---
# <a name="office-365-ip-address-and-url-web-service"></a>**Dirección IP de Office 365 y servicio web de URL**

Para ayudarle a identificar y diferenciar el tráfico de red de Office 365, un nuevo servicio web publica puntos de conexión de Office 365, con lo cual le resultará más fácil evaluar, configurar y mantenerse al día con los cambios. Este nuevo servicio web reemplaza los archivos XML descargables que están disponibles actualmente. Se prevé la eliminación gradual del formato XML para el 2 de octubre de 2018.

Como cliente o proveedor de dispositivos de red perimetral, usted puede crear el nuevo servicio web basado en REST para las entradas FQDN y la dirección IP de Office 365. Puede obtener acceso a los datos directamente en un explorador web con estas direcciones URL.

- Para obtener la versión más reciente de los intervalos de direcciones IP y URL de Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Si desea ver los datos de la página de intervalos de direcciones IP y URL de Office 365 para los firewalls y servidores proxy, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).
- Para obtener los últimos cambios desde finales de julio de 2018 cuando se publicó el servicio web, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).

Como cliente, puede usar este servicio web para:

- Actualizar los scripts de PowerShell para obtener datos de puntos de conexión de Office 365 y modificar el formato de los dispositivos de redes.
- Usar esta información para actualizar los archivos PAC implementados en los equipos cliente.

Como proveedor de dispositivos de red perimetral, puede usar este servicio web para:

- Crear y probar software de dispositivos para descargar la lista de configuración automatizada.
- Comprobar la versión actual.
- Obtener los cambios actuales.

Para obtener más información, consulte:

- [Entrada de blog con el anuncio en el foro de la Comunidad de profesionales de Office 365](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [Foro de la Comunidad de profesionales de Office 365 para dudas sobre el uso de los servicios web](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a>**Parámetros comunes**

Estos parámetros son comunes a todos los métodos de servicio web:

- **format=CSV | JSON**: parámetro de cadena de consulta. De forma predeterminada, el formato de los datos devueltos es JSON. Incluya este parámetro opcional para devolver los datos en formato de valores separados por comas (CSV).
- **ClientRequestId**: parámetro de cadena de consulta. Un GUID necesario que se genera para la asociación de clientes. Debe generar un GUID para cada equipo que llama al servicio web. No use los GUID que se muestran en los ejemplos siguientes, porque el servicio web podría bloquearlos en el futuro. El formato de GUID es _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, donde x representa un número hexadecimal. Para generar un GUID, use el comando de PowerShell [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6).

## <a name="version-web-method"></a>**Método web de versión**

Microsoft actualiza la dirección IP de Office 365 y las entradas FQDN al final de cada mes y en ocasiones fuera de ciclo por motivos operativos o de soporte técnico. Los datos de cada instancia publicada se asignan a un número de versión. El método web de versión permite obtener la versión más reciente de cada instancia de servicio de Office 365. Le recomendamos que compruebe la versión de cada día o, a lo sumo, cada hora. Se espera que las nuevas versiones salgan al inicio de cada mes. A veces, debido a algún incidente de soporte técnico o algún requisito de seguridad o de otro tipo, saldrán nuevas versiones durante el mes.

Hay un parámetro para el método web de versión:

- **AllVersions=true**: parámetro de cadena de consulta. De forma predeterminada, la versión devuelta es la más reciente. Incluya este parámetro opcional para solicitar todas las versiones publicadas.
- **Format=JSON** | **CSV** | **RSS**. Además de los formatos JSON y CSV, el método web de versión también es compatible con RSS. Puede usarlo junto con el parámetro allVersions=true para solicitar una fuente RSS, que se puede usar con Outlook y otros lectores RSS.
- **Instance**: parámetro de ruta. Este parámetro opcional especifica la instancia para la que se devolverá la versión. Si se omite, se devolverán todas las instancias. Las instancias válidas son: Worldwide, China, Germany, USGovDoD, USGovGCCHigh

El resultado del método web de versión puede ser un registro único o una matriz de registros. Los elementos de cada registro son:

- instance: el nombre corto de la instancia de servicio de Office 365.
- latest: la versión más reciente de los extremos de la instancia especificada.
- versions: una lista de todas las versiones anteriores de la instancia especificada. Este elemento solo se incluye si el parámetro AllVersions es true.

### <a name="examples"></a>**Ejemplos:**

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

[!IMPORTANT]
El GUID para el parámetro ClientRequestID en estos URI es solo un ejemplo. Para probar los URI de servicio web, genere su propio GUID. El servicio web podría bloquear en el futuro los GUID que se muestran en estos ejemplos.

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
<rss version="2.0" xmlns:a10="http://www.w3.org/2005/Atom">
<channel>
<link>http://aka.ms/o365ip</link>
<description/>
<language>en-us</language>
<lastBuildDate>Thu, 02 Aug 2018 00:00:00 Z</lastBuildDate>
<item>
<guid isPermaLink="false">2018080200</guid>
<link>https://endpoints.office.com/changes/Worldwide/2018080200?singleVersion&clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7</link> <description>Version 2018080200 includes 2 changes. IPs: 2 added and 0 removed.</description>
<pubDate>Thu, 02 Aug 2018 00:00:00 Z</pubDate>
</item>
...
```

## <a name="endpoints-web-method"></a>**Método web de puntos de conexión**

El método web de puntos de conexión devuelve todos los registros para los intervalos de direcciones IP y URL que conforman el servicio de Office 365. Aunque los datos más recientes del método web de puntos de conexión deben usarse para la configuración de dispositivos de red, los datos se pueden almacenar en caché por un máximo de 30 días tras su publicación debido a la antelación prevista para adiciones. Los parámetros del método web de puntos de conexión son:

- **ServiceAreas**: parámetro de cadena de consulta. Una lista de valores separados por comas de áreas de servicio. Los elementos válidos son Common, Exchange, SharePoint y Skype. Como los elementos del área de servicio Common son un requisito previo para todas las demás áreas de servicio, el servicio web siempre los incluirá. Si no incluye este parámetro, se devolverán todas las áreas de servicio.
- **TenantName**: parámetro de cadena de consulta. El nombre de la cuenta empresarial de Office 365. El servicio web tiene el nombre especificado y lo inserta en partes de las direcciones URL que incluyen el nombre del inquilino. Si no proporciona un nombre de cuenta empresarial, esas partes de las direcciones URL tienen el carácter comodín (\*).
- **NoIPv6**: parámetro de cadena de consulta. Establezca esto en true para excluir las direcciones IPv6 del resultado. Por ejemplo, si no usa IPv6 en la red.
- **Instance**: parámetro de ruta. Este parámetro obligatorio especifica la instancia para la que se devolverán los extremos. Las instancias válidas son: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.

El resultado del método web de extremos es una matriz de registros en la que cada registro representa un conjunto de extremos. Los elementos de cada registro son:

- id: el número de identificador inmutable del conjunto de extremos.
- serviceArea: el área de servicio que forma parte de: Common, Exchange, SharePoint o Skype
- urls: las direcciones URL del conjunto de extremos. Una matriz de JSON de registros DNS. Se omite si está en blanco.
- tcpPorts: los puertos TCP del conjunto de extremos. Todos los elementos de los puertos tienen formato de lista de valores separados por comas de puertos o intervalos de puertos separados por un carácter de guión (-). Los puertos se aplican a todas las direcciones IP y todas las direcciones URL en ese conjunto de extremos para esa categoría. Se omite si está en blanco.
- udpPorts: los puertos UDP para los intervalos de direcciones IP en ese conjunto de extremos. Se omite si está en blanco.
- ips: los intervalos de direcciones IP asociados a este conjunto de extremos punto de conexión que se establece como asociado a los puertos TCP o UDP mencionados. Una matriz de JSON de intervalos de direcciones IP. Se omite si está en blanco.
- category: la categoría de conectividad del conjunto de extremos. Los valores válidos son Optimize, Allow y Default. Obligatorio.
- expressRoute: verdadero o falso si este conjunto de extremos se enruta a través de ExpressRoute.
- required: verdadero si se requiere que el conjunto de extremos tenga conectividad para Office 365 para ser compatible. Falso si el conjunto de extremos es opcional.
- notes: para puntos de conexión opcionales, este texto describe la funcionalidad de Office 365 que faltará si las direcciones IP o las direcciones URL en este conjunto de extremos no se pueden consultar en el nivel de red. Se omite si está en blanco.

### <a name="examples"></a>Ejemplos:

Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este URI obtiene todos los extremos de la instancia worldwide de Office 365 para todas las cargas de trabajo. El resultado de ejemplo que muestra un fragmento de salida:

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
...
```

No se incluyen los conjuntos de extremos adicionales en este ejemplo.

Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)

Este ejemplo obtiene extremos de la instancia Worldwide de Office 365 para Exchange Online y solo dependencias.

El resultado para el ejemplo 2 es similar al del ejemplo 1, excepto que los resultados no incluirán extremos para SharePoint Online o Skype Empresarial Online.

## <a name="changes-web-method"></a>Método web de cambios

El método web de cambios devuelve las actualizaciones más recientes que se han publicado. Normalmente se trata de los cambios del mes anterior en los intervalos de direcciones IP y URL. Los cambios más importantes que se procesarán son cuando se agregan nuevas direcciones URL o direcciones IP porque la imposibilidad de agregar una dirección IP a una lista de control de acceso de firewall o una dirección URL a un servidor proxy omitir lista puede provocar una interrupción para los usuarios de Office 365 detrás de dicho dispositivo de red. Pese a los requisitos operativos, las operaciones _Add_ se agregan con un aviso de 30 días antes de que se produzca dicha interrupción.

El parámetro para el método web de cambios es:

- **Version**. Parámetro de ruta de URL necesario. La versión que está implementada actualmente y después de la cual desea ver los cambios realizados. El formato es _YYYYMMDDNN_.

El resultado del método web de cambios es una matriz de registros en la que cada registro representa un cambio en una versión específica de los extremos. Los elementos de cada registro son:

- id: el identificador inmutable del registro de cambios.
- endpointSetId: el identificador del registro del conjunto de extremos que se modificó. Obligatorio.
- disposition: puede ser de cambio, adición o eliminación y describe lo que hizo el cambio al registro del conjunto de extremos. Obligatorio.
- version: la versión del conjunto de extremos publicados en la que se presentó el cambio. Los números de versión están en el formato _YYYYMMDDNN_, donde NN es un número natural incrementado si hay varias versiones que deben publicarse en un solo día.
- anterior: una subestructura en la que se detallan los valores anteriores de los elementos modificados en el conjunto de extremos. Esto no se incluye para los conjuntos de extremos recién añadidos. Incluye tcpPorts, udpPorts, ExpressRoute, category, required y notes.
- current: una subestructura en la que se detallan los valores actualizados de los elementos de cambios en el conjunto de extremos. Incluye tcpPorts, udpPorts, ExpressRoute, category, required y notes.
- add: una subestructura en la que se detallan los elementos que se agregarán a las colecciones de conjuntos de extremos. Se omite si no hay ninguna adición.
  - effectiveDate: define los datos cuando las adiciones se activarán en el servicio.
  - ips: los elementos que se agregarán a la matriz de direcciones IP.
  - urls: los elementos que se agregarán a la matriz de direcciones URL.
- remove: una subestructura en la que se detallan los elementos que se eliminarán del conjunto de extremos. Se omite si no hay ninguna eliminación.
  - ips: los elementos que se eliminarán de la matriz de direcciones IP.
  - urls: los elementos que se eliminarán de la matriz de direcciones URL.

### <a name="examples"></a>**Ejemplos:**

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
...
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

## <a name="example-powershell-script"></a>**Ejemplo de script de PowerShell**

Este es un script de PowerShell que puede ejecutar para ver si hay acciones que debe seguir para los datos actualizados. Este script comprueba el número de versión de los extremos de la instancia Worldwide de Office 365. Cuando se produce un cambio, se descargan los extremos y filtros de los extremos de categoría &quot;Allow&quot; y &quot;Optimize&quot;. También se usa un único ClientRequestId en varias llamadas y se guarda la versión más reciente que se encuentra en un archivo temporal. Debe llamar a este script una vez cada hora para comprobar si hay una actualización de versión.

```powershell
# webservice root URL
$ws = "https://endpoints.office.com"
# path where client ID and latest version number will be stored
$datapath = $Env:TEMP + "\endpoints_clientid_latestversion.txt"
# fetch client ID and version if data file exists; otherwise create new file
if (Test-Path $datapath) {
    $content = Get-Content $datapath
    $clientRequestId = $content[0]
    $lastVersion = $content[1]
}
else {
    $clientRequestId = [GUID]::NewGuid().Guid
    $lastVersion = "0000000000"
    @($clientRequestId, $lastVersion) | Out-File $datapath
}
# call version method to check the latest version, and pull new data if version number is different
$version = Invoke-RestMethod -Uri ($ws + "/version/Worldwide?clientRequestId=" + $clientRequestId)
if ($version.latest -gt $lastVersion) {
    Write-Host "New version of Office 365 worldwide commercial service instance endpoints detected"

    # write the new version number to the data file
    @($clientRequestId, $version.latest) | Out-File $datapath
    # invoke endpoints method to get the new data
    $endpointSets = Invoke-RestMethod -Uri ($ws + "/endpoints/Worldwide?clientRequestId=" + $clientRequestId)
    # filter results for Allow and Optimize endpoints, and transform these into custom objects with port and category
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
    $flatIps = $endpointSets | ForEach-Object {
        $endpointSet = $_
        $ips = $(if ($endpointSet.ips.Count -gt 0) { $endpointSet.ips } else { @() })
        # IPv4 strings have dots while IPv6 strings have colons
        $ip4s = $ips | Where-Object { $_ -like '*.*' }

        $ipCustomObjects = @()
        if ($endpointSet.category -in ("Allow", "Optimize")) {
            $ipCustomObjects = $ip4s | ForEach-Object {
                [PSCustomObject]@{
                    category = $endpointSet.category;
                    ip = $_;
                    tcpPorts = $endpointSet.tcpPorts;
                    udpPorts = $endpointSet.udpPorts;
                }
            }
        }
        $ipCustomObjects
    }
    Write-Output "IPv4 Firewall IP Address Ranges"
    ($flatIps.ip | Sort-Object -Unique) -join "," | Out-String
    Write-Output "URLs for Proxy Server"
    ($flatUrls.url | Sort-Object -Unique) -join "," | Out-String
    # TODO Call Send-MailMessage with new endpoints data
}
else {
    Write-Host "Office 365 worldwide commercial service instance endpoints are up-to-date"
}
```

## <a name="example-python-script"></a>**Ejemplo de script de Python**

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

## <a name="web-service-interface-versioning"></a>**Control de versiones de la interfaz de servicio web**

Las actualizaciones de los parámetros o los resultados de estos métodos de servicio web pueden ser necesarias en el futuro. Después de que se publica la versión de disponibilidad general de estos servicios web, Microsoft realizará esfuerzos razonables para proporcionar un aviso por adelantado de las actualizaciones materiales al servicio web. Cuando Microsoft considere que una actualización requerirá cambios en los clientes con el servicio web, Microsoft conservará la versión anterior (versión inmediatamente anterior) del servicio de web disponible durante al menos doce (12) meses después del lanzamiento de la nueva versión. Es posible que los clientes que no actualicen durante ese tiempo no puedan consultar el servicio web y sus métodos. Los clientes deben asegurarse de que los clientes del servicio web continuarán trabajando sin errores si se realizan los cambios siguientes en la firma de interfaz del servicio web:

- Agregar un nuevo parámetro opcional a un método web existente que no tenga que facilitarse mediante clientes antiguos y que no afecte al resultado que recibe un cliente anterior.
- Agregar un nuevo atributo con nombre en uno de los elementos REST de respuesta o una de las columnas adicionales a la respuesta CSV.
- Agregar un nuevo método web con otro nombre al que no llamen los clientes anteriores.

## <a name="related-topics"></a>Temas relacionados
  
[Intervalos de direcciones IP y URL de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)

[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)

[Conectividad de red a Office 365](network-connectivity.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)
  
[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Implementación de ExpressRoute para Office 365](implementing-expressroute.md)
  
[Uso de comunidades BGP en ExpressRoute para escenarios de Office 365 (versión preliminar)](bgp-communities-in-expressroute.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Optimización de la red para Skype Empresarial Online](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)
  
[ExpressRoute y QoS en Skype Empresarial Online](https://support.office.com/article/20c654da-30ee-4e4f-a764-8b7d8844431d)
  
[Flujo de llamadas con ExpressRoute](https://support.office.com/article/413acb29-ad83-4393-9402-51d88e7561ab)
  
[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)
  
[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)