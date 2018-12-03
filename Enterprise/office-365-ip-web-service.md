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
ms.openlocfilehash: 8a9b3981f833705b0d77e87a6f0588730b9fb170
ms.sourcegitcommit: 7db45f3c81f38908ac2d6f64ceb79a4f334ec3cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2018
ms.locfileid: "26985775"
---
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="a46b0-104">**Dirección IP de Office 365 y servicio web de URL**</span><span class="sxs-lookup"><span data-stu-id="a46b0-104">**Office 365 IP Address and URL Web service**</span></span>

<span data-ttu-id="a46b0-p102">Para ayudarle a identificar y diferenciar el tráfico de red de Office 365, un nuevo servicio web publica puntos de conexión de Office 365, con lo cual le resultará más fácil evaluar, configurar y mantenerse al día con los cambios. Este nuevo servicio web reemplaza los archivos XML descargables que están disponibles actualmente. Se prevé la eliminación gradual del formato XML para el 2 de octubre de 2018.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p102">To help you better identify and differentiate Office 365 network traffic, a new web service publishes Office 365 endpoints, making it easier for you to evaluate, configure, and stay up to date with changes. This new web service replaces the XML downloadable files that are currently available. The XML format is planned to be phased out on October 2, 2018.</span></span>

<span data-ttu-id="a46b0-p103">Como cliente o proveedor de dispositivos de red perimetral, usted puede crear el nuevo servicio web basado en REST para las entradas FQDN y la dirección IP de Office 365. Puede obtener acceso a los datos directamente en un explorador web con estas direcciones URL.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p103">As a customer or a network perimeter device vendor, you can build against the new REST-based web service for the Office 365 IP address and FQDN entries. You can access the data directly in a web browser using these URLs.</span></span>

- <span data-ttu-id="a46b0-110">Para obtener la versión más reciente de los intervalos de direcciones IP y URL de Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="a46b0-110">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="a46b0-111">Si desea ver los datos de la página de intervalos de direcciones IP y URL de Office 365 para los firewalls y servidores proxy, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="a46b0-111">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="a46b0-112">Para obtener los últimos cambios desde finales de julio de 2018 cuando se publicó el servicio web, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="a46b0-112">To get all the latest changes since the end of July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="a46b0-113">Como cliente, puede usar este servicio web para:</span><span class="sxs-lookup"><span data-stu-id="a46b0-113">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="a46b0-114">Actualizar los scripts de PowerShell para obtener datos de puntos de conexión de Office 365 y modificar el formato de los dispositivos de redes.</span><span class="sxs-lookup"><span data-stu-id="a46b0-114">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="a46b0-115">Usar esta información para actualizar los archivos PAC implementados en los equipos cliente.</span><span class="sxs-lookup"><span data-stu-id="a46b0-115">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="a46b0-116">Como proveedor de dispositivos de red perimetral, puede usar este servicio web para:</span><span class="sxs-lookup"><span data-stu-id="a46b0-116">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="a46b0-117">Crear y probar software de dispositivos para descargar la lista de configuración automatizada.</span><span class="sxs-lookup"><span data-stu-id="a46b0-117">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="a46b0-118">Comprobar la versión actual.</span><span class="sxs-lookup"><span data-stu-id="a46b0-118">Check for the current version.</span></span>
- <span data-ttu-id="a46b0-119">Obtener los cambios actuales.</span><span class="sxs-lookup"><span data-stu-id="a46b0-119">Get the current changes.</span></span>

<span data-ttu-id="a46b0-120">Para obtener más información, consulte:</span><span class="sxs-lookup"><span data-stu-id="a46b0-120">For additional information, see:</span></span>

- [<span data-ttu-id="a46b0-121">Entrada de blog con el anuncio en el foro de la Comunidad de profesionales de Office 365</span><span class="sxs-lookup"><span data-stu-id="a46b0-121">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="a46b0-122">Foro de la Comunidad de profesionales de Office 365 para dudas sobre el uso de los servicios web</span><span class="sxs-lookup"><span data-stu-id="a46b0-122">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="a46b0-123">**Parámetros comunes**</span><span class="sxs-lookup"><span data-stu-id="a46b0-123">**Common parameters**</span></span>

<span data-ttu-id="a46b0-124">Estos parámetros son comunes a todos los métodos de servicio web:</span><span class="sxs-lookup"><span data-stu-id="a46b0-124">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="a46b0-p104">**format=CSV | JSON**: parámetro de cadena de consulta. De forma predeterminada, el formato de los datos devueltos es JSON. Incluya este parámetro opcional para devolver los datos en formato de valores separados por comas (CSV).</span><span class="sxs-lookup"><span data-stu-id="a46b0-p104">**format=CSV | JSON** - Query string parameter. By default, the returned data format is JSON. Include this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="a46b0-p105">**ClientRequestId**: parámetro de cadena de consulta. Un GUID necesario que se genera para la asociación de clientes. Debe generar un GUID para cada equipo que llama al servicio web. No use los GUID que se muestran en los ejemplos siguientes, porque el servicio web podría bloquearlos en el futuro. El formato de GUID es _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, donde x representa un número hexadecimal. Para generar un GUID, use el comando de PowerShell [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="a46b0-p105">**ClientRequestId** - Query string parameter. A required GUID that you generate for client association. You should generate a GUID for each machine that calls the web service. Do not use the GUIDs shown in the following examples because they may be blocked by the web service in the future. GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number. To generate a GUID, use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command.</span></span>

## <a name="version-web-method"></a><span data-ttu-id="a46b0-134">**Método web de versión**</span><span class="sxs-lookup"><span data-stu-id="a46b0-134">**Version web method**</span></span>

<span data-ttu-id="a46b0-p106">Microsoft actualiza la dirección IP de Office 365 y las entradas FQDN al final de cada mes y en ocasiones fuera de ciclo por motivos operativos o de soporte técnico. Los datos de cada instancia publicada se asignan a un número de versión. El método web de versión permite obtener la versión más reciente de cada instancia de servicio de Office 365. Le recomendamos que compruebe la versión de cada día o, a lo sumo, cada hora. Se espera que las nuevas versiones salgan al inicio de cada mes. A veces, debido a algún incidente de soporte técnico o algún requisito de seguridad o de otro tipo, saldrán nuevas versiones durante el mes.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p106">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month and occasionally out of cycle for operational or support requirements. The data for each published instance is assigned a version number. The version web method lets you poll for the latest version for each Office 365 service instance. We recommend you check the version daily, or at the most, hourly. New versions should be expected at the start of each month. Sometimes due to support incident, security, or other operational requirements there will be new versions during the month.</span></span>

<span data-ttu-id="a46b0-141">Hay un parámetro para el método web de versión:</span><span class="sxs-lookup"><span data-stu-id="a46b0-141">There is one parameter for the version web method:</span></span>

- <span data-ttu-id="a46b0-p107">**AllVersions=true**: parámetro de cadena de consulta. De forma predeterminada, la versión devuelta es la más reciente. Incluya este parámetro opcional para solicitar todas las versiones publicadas.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p107">**AllVersions=true** - Query string parameter. By default, the version returned is the latest. Include this optional parameter to request all published versions.</span></span>
- <span data-ttu-id="a46b0-p108">**Format=JSON** | **CSV** | **RSS**. Además de los formatos JSON y CSV, el método web de versión también es compatible con RSS. Puede usarlo junto con el parámetro allVersions=true para solicitar una fuente RSS, que se puede usar con Outlook y otros lectores RSS.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p108">**Format=JSON** | **CSV** | **RSS** – In addition to the JSON and CSV formats, the version web method also supports RSS. You can use this along with the allVersions=true parameter to request an RSS feed which can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="a46b0-p109">**Instance**: parámetro de ruta. Este parámetro opcional especifica la instancia para la que se devolverá la versión. Si se omite, se devolverán todas las instancias. Las instancias válidas son: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p109">**Instance** - Route parameter. This optional parameter specifies the instance to return the version for. If omitted, all instances are returned. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="a46b0-p110">El método web de versión no tiene una tasa limitada y no devuelve nunca códigos de respuesta HTTP 429. La respuesta al método web de versión incluye un encabezado de control de caché que recomienda el almacenamiento en caché de los datos durante una hora. El resultado del método web de versión puede ser un registro único o una matriz de registros. Los elementos de cada registro son:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p110">The version web method is not rate limited and does not ever return 429 HTTP Response Codes. The response to the version web method does include a cache-control header recommending caching of the data for 1 hour. The result from the version web method may be a single record or an array of records. The elements of each record are:</span></span>

- <span data-ttu-id="a46b0-155">instance: el nombre corto de la instancia de servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a46b0-155">instance - The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="a46b0-156">latest: la versión más reciente de los extremos de la instancia especificada.</span><span class="sxs-lookup"><span data-stu-id="a46b0-156">latest - The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="a46b0-p111">versions: una lista de todas las versiones anteriores de la instancia especificada. Este elemento solo se incluye si el parámetro AllVersions es true.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p111">versions - A list of all previous versions for the specified instance. This element is only included if the AllVersions parameter is true.</span></span>

<span data-ttu-id="a46b0-p112">Puede usar Microsoft Flow para recibir notificaciones de correo electrónico sobre los cambios realizados en las direcciones IP y URL. Consulte [Usar Microsoft Flow para recibir un correo electrónico de los cambios en las direcciones IP y URL de Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="a46b0-p112">You can use Microsoft Flow to get email notifications of changes to the IP Addresses and URLs. See [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>

### <a name="examples"></a><span data-ttu-id="a46b0-161">**Ejemplos:**</span><span class="sxs-lookup"><span data-stu-id="a46b0-161">**Examples:**</span></span>

<span data-ttu-id="a46b0-162">Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a46b0-162">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a46b0-p113">Este URI devuelve la versión más reciente de cada instancia de servicio de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="a46b0-p114">El GUID para el parámetro ClientRequestID en estos URI es solo un ejemplo. Para probar los URI de servicio web, genere su propio GUID. El servicio web podría bloquear en el futuro los GUID que se muestran en estos ejemplos.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="a46b0-168">Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a46b0-168">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a46b0-p115">Este URI devuelve la versión más reciente de la instancia de servicio especificada de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}

```

<span data-ttu-id="a46b0-171">Ejemplo 3 de URI de solicitud: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a46b0-171">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a46b0-p116">Este URI muestra los resultados en formato CSV. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="a46b0-174">Ejemplo 4 de URI de solicitud: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a46b0-174">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a46b0-p117">Este URI muestra todas las versiones anteriores que se han publicado para la instancia de servicio de Office 365 en todo el mundo. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="a46b0-177">Ejemplo 5 de URI de fuente RSS: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="a46b0-177">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="a46b0-p118">Este URI muestra una fuente RSS de las versiones publicadas que incluyen vínculos a la lista de cambios de cada versión. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="a46b0-180">**Método web de puntos de conexión**</span><span class="sxs-lookup"><span data-stu-id="a46b0-180">**Endpoints web method**</span></span>

<span data-ttu-id="a46b0-p119">El método web de puntos de conexión devuelve todos los registros para los intervalos de direcciones IP y URL que conforman el servicio de Office 365. Aunque los datos más recientes del método web de puntos de conexión deben usarse para la configuración de dispositivos de red, los datos se pueden almacenar en caché por un máximo de 30 días tras su publicación debido a la antelación prevista para adiciones. Solo se recomienda llamar al método web de puntos de conexión de nuevo cuando el método web de versión indica que hay una nueva versión de los datos disponible. Los parámetros del método web de puntos de conexión son:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p119">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service. While the latest data from the endpoints web method should be used for network device configuration, the data can be cached for up to 30 days after it is published due to the advance notice provided for additions. Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="a46b0-p120">**ServiceAreas**: parámetro de cadena de consulta. Una lista de valores separados por comas de áreas de servicio. Los elementos válidos son Common, Exchange, SharePoint y Skype. Como los elementos del área de servicio Common son un requisito previo para todas las demás áreas de servicio, el servicio web siempre los incluirá. Si no incluye este parámetro, se devolverán todas las áreas de servicio.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p120">**ServiceAreas** - Query string parameter. A comma-separated list of service areas. Valid items are Common,Exchange,SharePoint,Skype. Because Common service area items are a prerequisite for all other service areas, the web service will always include them. If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="a46b0-p121">**TenantName**: parámetro de cadena de consulta. El nombre de la cuenta empresarial de Office 365. El servicio web tiene el nombre especificado y lo inserta en partes de las direcciones URL que incluyen el nombre del inquilino. Si no proporciona un nombre de cuenta empresarial, esas partes de las direcciones URL tienen el carácter comodín (\*).</span><span class="sxs-lookup"><span data-stu-id="a46b0-p121">**TenantName** - Query string parameter. Your Office 365 tenant name. The web service takes your provided name and inserts it in parts of URLs that include the tenant name. If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="a46b0-p122">**NoIPv6**: parámetro de cadena de consulta. Establezca esto en true para excluir las direcciones IPv6 del resultado. Por ejemplo, si no usa IPv6 en la red.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p122">**NoIPv6** - Query string parameter. Set this to true to exclude IPv6 addresses from the output, for example, if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="a46b0-p123">**Instance**: parámetro de ruta. Este parámetro obligatorio especifica la instancia para la que se devolverán los extremos. Las instancias válidas son: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p123">**Instance** - Route parameter. This required parameter specifies the instance to return the endpoints for. Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="a46b0-p124">Si llama al método web de puntos de conexión una cantidad excesiva de veces desde la misma dirección IP de cliente es posible que reciba el código de respuesta HTTP 429 Demasiadas solicitudes. La mayoría de los usuarios nunca verá dicho código. Si recibe este código de respuesta, debe esperar 1 hora antes de llamar de nuevo al método. Planee llamar al método web de puntos de conexión solo cuando el método web indique que hay disponible una nueva versión.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p124">If you call the endpoints web method an unreasonable number of times from the same client IP Address you may receive HTTP Response Code 429 Too Many Requests. Most people will never see this. If you get this response code, you should wait 1 hour before calling the method again. Plan to only call the endpoints web method when the version web method indicates there is a new version available.</span></span> 

<span data-ttu-id="a46b0-p125">El resultado del método web de extremos es una matriz de registros en la que cada registro representa un conjunto de extremos. Los elementos de cada registro son:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p125">The result from the endpoints web method is an array of records with each record representing an endpoint set. The elements for each record are:</span></span>

- <span data-ttu-id="a46b0-205">id: el número de identificador inmutable del conjunto de extremos.</span><span class="sxs-lookup"><span data-stu-id="a46b0-205">id - The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="a46b0-206">serviceArea: el área de servicio que forma parte de: Common, Exchange, SharePoint o Skype</span><span class="sxs-lookup"><span data-stu-id="a46b0-206">serviceArea - The service area that this is part of: Common, Exchange, SharePoint, or Skype.</span></span>
- <span data-ttu-id="a46b0-p126">urls: las direcciones URL del conjunto de extremos. Una matriz de JSON de registros DNS. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p126">urls - URLs for the endpoint set. A JSON array of DNS records. Omitted if blank.</span></span>
- <span data-ttu-id="a46b0-p127">tcpPorts: los puertos TCP del conjunto de extremos. Todos los elementos de los puertos tienen formato de lista de valores separados por comas de puertos o intervalos de puertos separados por un carácter de guión (-). Los puertos se aplican a todas las direcciones IP y todas las direcciones URL en ese conjunto de extremos para esa categoría. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p127">tcpPorts - TCP ports for the endpoint set. All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-). Ports apply to all IP addresses and all URLs in that endpoint set for that category. Omitted if blank.</span></span>
- <span data-ttu-id="a46b0-p128">udpPorts: los puertos UDP para los intervalos de direcciones IP en ese conjunto de extremos. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p128">udpPorts - UDP ports for the IP address ranges in this endpoint set. Omitted if blank.</span></span>
- <span data-ttu-id="a46b0-p129">ips: los intervalos de direcciones IP asociados a este conjunto de puntos de conexión que se establece como asociado a los puertos TCP o UDP mencionados. Una matriz de JSON de intervalos de direcciones IP. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p129">ips - The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports. A JSON array of IP Address ranges. Omitted if blank.</span></span>
- <span data-ttu-id="a46b0-p130">categoría: la categoría de conectividad para el conjunto de puntos de conexión. Los valores válidos son Optimizar, Permitir y Predeterminado. Si usa los datos de punto de conexión para buscar la categoría de una dirección URL o una dirección IP, es posible que la consulta devuelva varias categorías. Esto se puede deber a múltiples motivos. En estos casos, debe seguir las recomendaciones para la categoría de prioridad más alta. Por ejemplo, si se muestra el punto de conexión en Optimizar y Permitir, debe seguir los requisitos para Optimizar. Obligatorio.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p130">category - The connectivity category for the endpoint set. Valid values are Optimize, Allow, and Default. If using the endpoint data to search for the category of an IP Address or URL, it is possible that your query may return multiple categories. There are a few reasons why that may happen. In these cases you should follow the recommendations for the highest priority category. For example, if the endpoint appears in both Optimize and Allow, you should follow the requirements for Optimize. Required.</span></span> 
- <span data-ttu-id="a46b0-226">expressRoute: verdadero o falso si este conjunto de puntos de conexión se enruta a través de ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="a46b0-226">expressRoute - True or False if this endpoint set is routed over ExpressRoute.</span></span>
- <span data-ttu-id="a46b0-p131">required: verdadero si se requiere que el conjunto de extremos tenga conectividad para Office 365 para ser compatible. Falso si el conjunto de extremos es opcional.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p131">required - True if this endpoint set is required to have connectivity for Office 365 to be supported. False if this endpoint set is optional.</span></span>
- <span data-ttu-id="a46b0-p132">notes: para puntos de conexión opcionales, este texto describe la funcionalidad de Office 365 que faltará si las direcciones IP o las direcciones URL en este conjunto de extremos no se pueden consultar en el nivel de red. Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p132">notes - For optional endpoints, this text describes Office 365 functionality that will be missing if IP addresses or URLs in this endpoint set cannot be accessed at the network layer. Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="a46b0-231">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="a46b0-231">Examples:</span></span>

<span data-ttu-id="a46b0-232">Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a46b0-232">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a46b0-p133">Este URI obtiene todos los extremos de la instancia worldwide de Office 365 para todas las cargas de trabajo. El resultado de ejemplo que muestra un fragmento de salida:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p133">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads. Example result showing an excerpt of the output:</span></span>

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

<span data-ttu-id="a46b0-235">No se incluyen los conjuntos de extremos adicionales en este ejemplo.</span><span class="sxs-lookup"><span data-stu-id="a46b0-235">Additional endpoint sets are not included in this example.</span></span>

<span data-ttu-id="a46b0-236">Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a46b0-236">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a46b0-237">Este ejemplo obtiene extremos de la instancia Worldwide de Office 365 para Exchange Online y solo dependencias.</span><span class="sxs-lookup"><span data-stu-id="a46b0-237">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="a46b0-238">El resultado para el ejemplo 2 es similar al del ejemplo 1, excepto que los resultados no incluirán extremos para SharePoint Online o Skype Empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="a46b0-238">The output for example 2 is similar to example 1 except that the results will not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="a46b0-239">Método web de cambios</span><span class="sxs-lookup"><span data-stu-id="a46b0-239">Changes web method</span></span>

<span data-ttu-id="a46b0-p134">El método web de cambios devuelve las actualizaciones más recientes que se han publicado. Normalmente se trata de los cambios del mes anterior en los intervalos de direcciones IP y URL. Los cambios más importantes que se procesarán son cuando se agregan nuevas direcciones URL o direcciones IP porque la imposibilidad de agregar una dirección IP a una lista de control de acceso de firewall o una dirección URL a un servidor proxy omitir lista puede provocar una interrupción para los usuarios de Office 365 detrás de dicho dispositivo de red. Pese a los requisitos operativos, las operaciones _Add_ se agregan con un aviso de 30 días antes de que se produzca dicha interrupción.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p134">The changes web method returns the most recent updates that have been published. This is typically the previous month's changes to IP address ranges and URLs. The most critical changes to be processed are when new URLs or IP Addresses are added since failing to add an IP Address to a firewall access control list, or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device. Notwithstanding operational requirements, _Add_ operations are added with 30 days' notice before such an outage would occur.</span></span>

<span data-ttu-id="a46b0-244">El parámetro para el método web de cambios es:</span><span class="sxs-lookup"><span data-stu-id="a46b0-244">The parameter for the changes web method is:</span></span>

- <span data-ttu-id="a46b0-p135">**Version**. Parámetro de ruta de URL necesario. La versión que está implementada actualmente y después de la cual desea ver los cambios realizados. El formato es _YYYYMMDDNN_.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p135">**Version** - Required URL route parameter. The version that you have currently implemented, and you want to see the changes since that version. The format is _YYYYMMDDNN_.</span></span>

<span data-ttu-id="a46b0-p136">El método de web de cambios tiene una tasa limitada al igual que el método web de puntos de conexión. Si recibe un código de respuesta HTTP 429 debería esperar 1 hora antes de llamar de nuevo.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p136">The changes web method is rate limited in the same way as the endpoints web method. If you receive a 429 HTTP Response Code then you should wait 1 hour before calling again.</span></span> 

<span data-ttu-id="a46b0-p137">El resultado del método web de cambios es una matriz de registros en la que cada registro representa un cambio en una versión específica de los extremos. Los elementos de cada registro son:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p137">The result from the changes web method is an array of records with each record representing a change in a specific version of the endpoints. The elements for each record are:</span></span>

- <span data-ttu-id="a46b0-252">id: el identificador inmutable del registro de cambios.</span><span class="sxs-lookup"><span data-stu-id="a46b0-252">id - The immutable id of the change record.</span></span>
- <span data-ttu-id="a46b0-p138">endpointSetId: el identificador del registro del conjunto de extremos que se modificó. Obligatorio.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p138">endpointSetId - The ID of the endpoint set record that is changed. Required.</span></span>
- <span data-ttu-id="a46b0-p139">disposition: puede ser de cambio, adición o eliminación y describe lo que hizo el cambio al registro del conjunto de extremos. Obligatorio.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p139">disposition - This can be either of change, add, or remove and describes what the change did to the endpoint set record. Required.</span></span>
- <span data-ttu-id="a46b0-p140">impact: no todos los cambios serán igualmente importantes para cada entorno. Describe el impacto esperado en un entorno de perímetro de red empresarial como resultado de este cambio. Este atributo sólo se incluye en los registros de cambio de la versión 2018112800 y versiones posteriores. Las opciones para el impacto son:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p140">impact - Not all changes will be equally important to every environment. This describes the expected impact to an enterprise network perimeter environment as a result of this change. This attribute is included only in change records of version 2018112800 and later. Options for the impact are:</span></span>
  - <span data-ttu-id="a46b0-p141">AddedIp: se agregó una dirección IP a Office 365 y estará en el servicio pronto. Esto representa un cambio que debe hacer en un firewall u otro dispositivo de perímetro de red de capa 3. Si no agrega esto antes de empezar a usarlo, puede experimentar una interrupción.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p141">AddedIp – An IP Address was added to Office 365 and will be live on the service soon. This represents a change you need to take on a firewall or other layer 3 network perimeter device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="a46b0-p142">AdedUrl: se agregó una URL a Office 365 y estará en el servicio pronto. Esto representa un cambio que debe hacer en un servidor proxy u otro dispositivo de perímetro de red de análisis de URL. Si no agrega esto antes de empezar a usarlo, puede experimentar una interrupción.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p142">AdedUrl – A URL was added to Office 365 and will be live on the service soon. This represents a change you need to take on a proxy server or URL parsing network perimeter device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="a46b0-p143">AddedIpAndUrl: se han agregado una dirección IP y una dirección URL. Esto representa un cambio que debe seguir en un dispositivo de capa 3 de firewall o un servidor proxy o un dispositivo de análisis de URL. Si no agrega esto antes de empezar a usarlo, puede experimentar una interrupción.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p143">AddedIpAndUrl - Both an IP Address and a URL were added. This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device. If you don’t add this before we start using it, you may experience an outage.</span></span>
  - <span data-ttu-id="a46b0-p144">RemovedIpOrUrl: se ha eliminado al menos una dirección IP o una dirección URL de Office 365. Debería quitar los puntos de conexión de red de los dispositivos de perímetro, pero no hay ningún límite de tiempo para hacer esto.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p144">RemovedIpOrUrl – At least one IP Address or URL was removed from Office 365. You should remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  - <span data-ttu-id="a46b0-p145">ChangedIsExpressRoute: se ha cambiado el atributo de soporte ExpressRoute. Si usa ExpressRoute puede que tenga que realizar alguna acción dependiendo de su configuración.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p145">ChangedIsExpressRoute – The ExpressRoute support attribute was changed. If you use ExpressRoute then you may need to take action depending on your configuration.</span></span>
  - <span data-ttu-id="a46b0-p146">MovedIpOrUrl: se ha pasado una dirección Url o una dirección IP entre este conjunto de puntos de conexión y otro. Por lo general, no es necesaria ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p146">MovedIpOrUrl – We moved an IP Address or Url between this endpoint set and another one. Generally no action is required.</span></span>
  - <span data-ttu-id="a46b0-p147">RemovedDuplicateIpOrUrl: se ha eliminado una dirección IP o Url duplicada, pero aún está publicada para Office 365. Por lo general, no es necesaria ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p147">RemovedDuplicateIpOrUrl – We removed a duplicate IP Address or Url but it’s still published for Office 365. Generally no action is required.</span></span>
  - <span data-ttu-id="a46b0-278">OtherNonPriorityChanges: se ha cambiado algo menos importante que todas las otras opciones, como un campo de nota</span><span class="sxs-lookup"><span data-stu-id="a46b0-278">OtherNonPriorityChanges – We changed something less critical than all of the other options like a note field</span></span>
- <span data-ttu-id="a46b0-p148">version: la versión del conjunto de extremos publicados en la que se presentó el cambio. Los números de versión están en el formato _YYYYMMDDNN_, donde NN es un número natural incrementado si hay varias versiones que deben publicarse en un solo día.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p148">version - The version of the published endpoint set in which the change was introduced. Version numbers are of the format _YYYYMMDDNN_, where NN is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="a46b0-p149">anterior: una subestructura en la que se detallan los valores anteriores de los elementos modificados en el conjunto de extremos. Esto no se incluye para los conjuntos de extremos recién añadidos. Incluye tcpPorts, udpPorts, ExpressRoute, category, required y notes.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p149">previous - A substructure detailing previous values of changed elements on the endpoint set. This will not be included for newly added endpoint sets. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="a46b0-p150">current: una subestructura en la que se detallan los valores actualizados de los elementos de cambios en el conjunto de extremos. Incluye tcpPorts, udpPorts, ExpressRoute, category, required y notes.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p150">current - A substructure detailing updated values of changes elements on the endpoint set. Includes tcpPorts, udpPorts, ExpressRoute, category, required, notes.</span></span>
- <span data-ttu-id="a46b0-p151">add: una subestructura en la que se detallan los elementos que se agregarán a las colecciones de conjuntos de extremos. Se omite si no hay ninguna adición.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p151">add - A substructure detailing items to be added to endpoint set collections. Omitted if there are no additions.</span></span>
  - <span data-ttu-id="a46b0-288">effectiveDate: define los datos cuando las adiciones se activarán en el servicio.</span><span class="sxs-lookup"><span data-stu-id="a46b0-288">effectiveDate - Defines the data when the additions will be live in the service.</span></span>
  - <span data-ttu-id="a46b0-289">ips: los elementos que se agregarán a la matriz de direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="a46b0-289">ips - Items to be added to the ips array.</span></span>
  - <span data-ttu-id="a46b0-290">urls: los elementos que se agregarán a la matriz de direcciones URL.</span><span class="sxs-lookup"><span data-stu-id="a46b0-290">urls- Items to be added to the urls array.</span></span>
- <span data-ttu-id="a46b0-p152">remove: una subestructura en la que se detallan los elementos que se eliminarán del conjunto de extremos. Se omite si no hay ninguna eliminación.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p152">remove - A substructure detailing items to be removed from the endpoint set. Omitted if there are no removals.</span></span>
  - <span data-ttu-id="a46b0-293">ips: los elementos que se eliminarán de la matriz de direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="a46b0-293">ips - Items to be removed from the ips array.</span></span>
  - <span data-ttu-id="a46b0-294">urls: los elementos que se eliminarán de la matriz de direcciones URL.</span><span class="sxs-lookup"><span data-stu-id="a46b0-294">urls- Items to be removed from the urls array.</span></span>

### <a name="examples"></a><span data-ttu-id="a46b0-295">**Ejemplos:**</span><span class="sxs-lookup"><span data-stu-id="a46b0-295">**Examples:**</span></span>

<span data-ttu-id="a46b0-296">Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a46b0-296">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a46b0-p153">Se solicitan todos los cambios anteriores a la instancia de servicio worldwide de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p153">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="a46b0-299">Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="a46b0-299">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="a46b0-p154">Se solicitan los cambios desde la versión especificada a la instancia Worldwide de Office 365. En este caso, la versión especificada es la más reciente. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p154">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="a46b0-303">**Ejemplo de script de PowerShell**</span><span class="sxs-lookup"><span data-stu-id="a46b0-303">**Example PowerShell Script**</span></span>

<span data-ttu-id="a46b0-p155">Este es un script de PowerShell que puede ejecutar para ver si hay acciones que debe seguir para los datos actualizados. Este script comprueba el número de versión de los extremos de la instancia Worldwide de Office 365. Cuando se produce un cambio, se descargan los extremos y filtros de los extremos de categoría &quot;Allow&quot; y &quot;Optimize&quot;. También se usa un único ClientRequestId en varias llamadas y se guarda la versión más reciente que se encuentra en un archivo temporal. Debe llamar a este script una vez cada hora para comprobar si hay una actualización de versión.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p155">Here is a PowerShell script that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the &quot;Allow&quot; and &quot;Optimize&quot; category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="a46b0-309">**Ejemplo de script de Python**</span><span class="sxs-lookup"><span data-stu-id="a46b0-309">**Example Python Script**</span></span>

<span data-ttu-id="a46b0-p156">Este es un script de Python, probado con Python 3.6.3 en Windows 10, que puede ejecutar para ver si hay acciones que debe seguir para los datos actualizados. Este script comprueba el número de versión de los extremos de la instancia Worldwide de Office 365. Cuando se produce un cambio, se descargan los extremos y filtros de los extremos de categoría _Allow_ y _Optimize_. También se usa un único ClientRequestId en varias llamadas y se guarda la versión más reciente que se encuentra en un archivo temporal. Debe llamar a este script una vez cada hora para comprobar si hay una actualización de versión.</span><span class="sxs-lookup"><span data-stu-id="a46b0-p156">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="a46b0-315">**Control de versiones de la interfaz de servicio web**</span><span class="sxs-lookup"><span data-stu-id="a46b0-315">**Web Service interface versioning**</span></span>

<span data-ttu-id="a46b0-p157">Las actualizaciones de los parámetros o los resultados de estos métodos de servicio web pueden ser necesarias en el futuro. Después de que se publica la versión de disponibilidad general de estos servicios web, Microsoft realizará esfuerzos razonables para proporcionar un aviso por adelantado de las actualizaciones materiales al servicio web. Cuando Microsoft considere que una actualización requerirá cambios en los clientes con el servicio web, Microsoft conservará la versión anterior (versión inmediatamente anterior) del servicio de web disponible durante al menos doce (12) meses después del lanzamiento de la nueva versión. Es posible que los clientes que no actualicen durante ese tiempo no puedan consultar el servicio web y sus métodos. Los clientes deben asegurarse de que los clientes del servicio web continuarán trabajando sin errores si se realizan los cambios siguientes en la firma de interfaz del servicio web:</span><span class="sxs-lookup"><span data-stu-id="a46b0-p157">Updates to the parameters or results for these web service methods may be required in the future. After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service. When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least twelve (12) months after the release of the new version. Customers who do not upgrade during that time may be unable to access the web service and its methods. Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="a46b0-321">Agregar un nuevo parámetro opcional a un método web existente que no tenga que facilitarse mediante clientes antiguos y que no afecte al resultado que recibe un cliente anterior.</span><span class="sxs-lookup"><span data-stu-id="a46b0-321">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="a46b0-322">Agregar un nuevo atributo con nombre en uno de los elementos REST de respuesta o una de las columnas adicionales a la respuesta CSV.</span><span class="sxs-lookup"><span data-stu-id="a46b0-322">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="a46b0-323">Agregar un nuevo método web con otro nombre al que no llamen los clientes anteriores.</span><span class="sxs-lookup"><span data-stu-id="a46b0-323">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="related-topics"></a><span data-ttu-id="a46b0-324">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="a46b0-324">Related Topics</span></span>
  
[<span data-ttu-id="a46b0-325">Intervalos de direcciones IP y URL de Office 365</span><span class="sxs-lookup"><span data-stu-id="a46b0-325">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[<span data-ttu-id="a46b0-326">Preguntas frecuentes sobre extremos de Office 365</span><span class="sxs-lookup"><span data-stu-id="a46b0-326">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="a46b0-327">Principios de conectividad de red de Office 365</span><span class="sxs-lookup"><span data-stu-id="a46b0-327">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="a46b0-328">Red de Office 365 y ajuste de rendimiento</span><span class="sxs-lookup"><span data-stu-id="a46b0-328">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="a46b0-329">Conectividad de red a Office 365</span><span class="sxs-lookup"><span data-stu-id="a46b0-329">Network connectivity to Office 365</span></span>](network-connectivity.md)
  
[<span data-ttu-id="a46b0-330">Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="a46b0-330">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="a46b0-331">Optimización de la red para Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="a46b0-331">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="a46b0-332">Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento</span><span class="sxs-lookup"><span data-stu-id="a46b0-332">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="a46b0-333">Plan de solución de problemas de rendimiento para Office 365</span><span class="sxs-lookup"><span data-stu-id="a46b0-333">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
