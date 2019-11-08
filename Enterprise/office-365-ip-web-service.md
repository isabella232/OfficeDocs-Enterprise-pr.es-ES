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
# <a name="office-365-ip-address-and-url-web-service"></a><span data-ttu-id="8fc6f-103">El servicio web de URL y dirección IP de Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc6f-103">Office 365 IP Address and URL web service</span></span>

<span data-ttu-id="8fc6f-104">El servicio web de URL y dirección IP de Office 365 le ayuda a identificar y a diferenciar mejor el tráfico de red de Office 365, lo que facilita la evaluación, la configuración y la actualización de los cambios.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-104">The Office 365 IP Address and URL web service helps you better identify and differentiate Office 365 network traffic, making it easier for you to evaluate, configure, and stay up to date with changes.</span></span> <span data-ttu-id="8fc6f-105">Este servicio web basado en REST reemplaza los archivos XML anteriores descargables, que se han retirado el 2 de octubre de 2018.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-105">This REST-based web service replaces the previous XML downloadable files, which were phased out on October 2, 2018.</span></span>

<span data-ttu-id="8fc6f-106">Como cliente o proveedor de dispositivo de red perimetral, puede crear el servicio web para las entradas de direcciones IP y FQDN de Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-106">As a customer or a network perimeter device vendor, you can build against the web service for Office 365 IP address and FQDN entries.</span></span> <span data-ttu-id="8fc6f-107">Puede obtener acceso a los datos directamente en un explorador web con estas direcciones URL:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-107">You can access the data directly in a web browser using these URLs:</span></span>

- <span data-ttu-id="8fc6f-108">Para obtener la versión más reciente de los intervalos de direcciones IP y URL de Office 365, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-108">For the latest version of the Office 365 URLs and IP address ranges, use [https://endpoints.office.com/version](https://endpoints.office.com/version?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="8fc6f-109">Si desea ver los datos de la página de intervalos de direcciones IP y URL de Office 365 para los firewalls y servidores proxy, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-109">For the data on the Office 365 URLs and IP address ranges page for firewalls and proxy servers, use [https://endpoints.office.com/endpoints/worldwide](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>
- <span data-ttu-id="8fc6f-110">Para obtener los últimos cambios desde finales de julio de 2018 cuando se publicó por primera vez el servicio web, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-110">To get all the latest changes since July 2018 when the web service was first available, use [https://endpoints.office.com/changes/worldwide/0000000000](https://endpoints.office.com/changes/worldwide/0000000000?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="8fc6f-111">Como cliente, puede usar este servicio web para:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-111">As a customer, you can use this web service to:</span></span>

- <span data-ttu-id="8fc6f-112">Actualizar los scripts de PowerShell para obtener datos de puntos de conexión de Office 365 y modificar el formato de los dispositivos de redes.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-112">Update your PowerShell scripts to obtain Office 365 endpoint data and modify any formatting for your networking devices.</span></span>
- <span data-ttu-id="8fc6f-113">Usar esta información para actualizar los archivos PAC implementados en los equipos cliente.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-113">Use this information to update PAC files deployed to client computers.</span></span>

<span data-ttu-id="8fc6f-114">Como proveedor de dispositivos de red perimetral, puede usar este servicio web para:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-114">As a network perimeter device vendor, you can use this web service to:</span></span>

- <span data-ttu-id="8fc6f-115">Crear y probar software de dispositivos para descargar la lista de configuración automatizada.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-115">Create and test device software to download the list for automated configuration.</span></span>
- <span data-ttu-id="8fc6f-116">Comprobar la versión actual.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-116">Check for the current version.</span></span>
- <span data-ttu-id="8fc6f-117">Obtener los cambios actuales.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-117">Get the current changes.</span></span>

> [!NOTE]
> <span data-ttu-id="8fc6f-118">Si usa Azure ExpressRoute para conectarse a Office 365, consulte [Azure ExpressRoute para Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) para familiarizarse con los servicios de Office 365 compatibles con Azure ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-118">If you are using Azure ExpressRoute to connect to Office 365, please review [Azure ExpressRoute for Office 365](https://docs.microsoft.com/office365/enterprise/azure-expressroute) to familiarize yourself with the Office 365 services supported over Azure ExpressRoute.</span></span> <span data-ttu-id="8fc6f-119">Revise también el artículo [Direcciones URL e intervalos de direcciones IP de Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) para conocer las solicitudes de red para las aplicaciones de Office 365 que requieren conectividad a Internet.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-119">Also review the article [Office 365 URLs and IP address ranges](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges?redirectSourcePath=%252farticle%252fOffice-365-URLs-and-IP-address-ranges-8548a211-3fe7-47cb-abb1-355ea5aa88a2) to understand which network requests for Office 365 applications require Internet connectivity.</span></span> <span data-ttu-id="8fc6f-120">Esto le ayudará a configurar mejor los dispositivos de seguridad de perimetral.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-120">This will help to better configure your perimeter security devices.</span></span>

<span data-ttu-id="8fc6f-121">Para obtener más información, vea:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-121">For more information, see:</span></span>

- [<span data-ttu-id="8fc6f-122">Entrada de blog con el anuncio en el foro de la Comunidad de profesionales de Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc6f-122">Announcement blog post in the Office 365 Tech Community Forum</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Blog/Announcing-Office-365-endpoint-categories-and-Office-365-IP/ba-p/177638)
- [<span data-ttu-id="8fc6f-123">Foro de la Comunidad de profesionales de Office 365 para dudas sobre el uso de los servicios web</span><span class="sxs-lookup"><span data-stu-id="8fc6f-123">Office 365 Tech Community Forum for questions about use of the web services</span></span>](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking)

## <a name="common-parameters"></a><span data-ttu-id="8fc6f-124">Parámetros comunes</span><span class="sxs-lookup"><span data-stu-id="8fc6f-124">Common parameters</span></span>

<span data-ttu-id="8fc6f-125">Estos parámetros son comunes a todos los métodos de servicio web:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-125">These parameters are common across all the web service methods:</span></span>

- <span data-ttu-id="8fc6f-126">**format=<JSON | CSV>**: de forma predeterminada, el formato de datos devueltos es JSON.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-126">**format=<JSON | CSV>** — By default, the returned data format is JSON.</span></span> <span data-ttu-id="8fc6f-127">Use este parámetro opcional para devolver los datos en formato de valores separados por comas (CSV).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-127">Use this optional parameter to return the data in comma-separated values (CSV) format.</span></span>
- <span data-ttu-id="8fc6f-128">**ClientRequestId=\<guid>**: un GUID obligatorio que se genera para la asociación del cliente.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-128">**ClientRequestId=\<guid>** — A required GUID that you generate for client association.</span></span> <span data-ttu-id="8fc6f-129">Genere un GUID único para cada equipo que llama al servicio web (los scripts que se incluyen en esta página generan un GUID por usted).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-129">Generate a unique GUID for each machine that calls the web service (the scripts included on this page generate a GUID for you).</span></span> <span data-ttu-id="8fc6f-130">No use los GUID que se muestran en los ejemplos siguientes, puesto que el servicio web puede bloquearlos en el futuro.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-130">Do not use the GUIDs shown in the following examples because they might be blocked by the web service in the future.</span></span> <span data-ttu-id="8fc6f-131">El formato GUID es _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, donde x representa un número hexadecimal.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-131">GUID format is _xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx_, where x represents a hexadecimal number.</span></span>

  <span data-ttu-id="8fc6f-132">Para generar un GUID, puede usar el comando de PowerShell [New-GUID](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) o usar un servicio en línea como el [Generador GUID en línea](https://www.guidgenerator.com/).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-132">To generate a GUID, you can use the [New-Guid](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/new-guid?view=powershell-6) PowerShell command, or use an online service such as [Online GUID Generator](https://www.guidgenerator.com/).</span></span>

## <a name="version-web-method"></a><span data-ttu-id="8fc6f-133">Método web de versión</span><span class="sxs-lookup"><span data-stu-id="8fc6f-133">Version web method</span></span>

<span data-ttu-id="8fc6f-134">Microsoft actualiza las entradas de direcciones IP y FQDN de Office 365 al final de cada mes.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-134">Microsoft updates the Office 365 IP address and FQDN entries at the end of each month.</span></span> <span data-ttu-id="8fc6f-135">En ocasiones, las actualizaciones fuera de banda se publican debido a incidencias de soporte técnico, actualizaciones de seguridad u otros requisitos operativos.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-135">Out-of-band updates are sometimes published due to support incidents, security updates or other operational requirements.</span></span>

<span data-ttu-id="8fc6f-136">Los datos de cada instancia publicada se asignan a un número de versión y el método web de versión le permite buscar la versión más reciente de cada una de las instancias del servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-136">The data for each published instance is assigned a version number, and the version web method enables you to check for the latest version of each Office 365 service instance.</span></span> <span data-ttu-id="8fc6f-137">Le recomendamos que compruebe la versión no más de una vez cada hora.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-137">We recommend that you check the version not more than once an hour.</span></span>

<span data-ttu-id="8fc6f-138">Los parámetros del método web de versión son:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-138">Parameters for the version web method are:</span></span>

- <span data-ttu-id="8fc6f-139">**AllVersions=<true | false>**: de forma predeterminada, la versión devuelta es la más reciente.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-139">**AllVersions=<true | false>** — By default, the version returned is the latest.</span></span> <span data-ttu-id="8fc6f-140">Incluya este parámetro opcional para solicitar todas las versiones publicadas desde la primera publicación del servicio web.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-140">Include this optional parameter to request all published versions since the web service was first released.</span></span>
- <span data-ttu-id="8fc6f-141">**Format=<JSON | CSV | RSS>**: además de los formatos JSON y CSV, el método web de versión también es compatible con RSS.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-141">**Format=<JSON | CSV | RSS>** — In addition to the JSON and CSV formats, the version web method also supports RSS.</span></span> <span data-ttu-id="8fc6f-142">Puede usar este parámetro opcional con el parámetro _AllVersions=true_ para solicitar una fuente RSS que pueda usarse con Outlook u otros lectores de RSS.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-142">You can use this optional parameter along with the _AllVersions=true_ parameter to request an RSS feed that can be used with Outlook or other RSS readers.</span></span>
- <span data-ttu-id="8fc6f-143">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**: este parámetro opcional especifica la instancia para la que se devolverá la versión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-143">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — This optional parameter specifies the instance to return the version for.</span></span> <span data-ttu-id="8fc6f-144">Si se omite, se devuelven todas las instancias.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-144">If omitted, all instances are returned.</span></span> <span data-ttu-id="8fc6f-145">Instancias válidas son: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-145">Valid instances are: Worldwide, China, Germany, USGovDoD, USGovGCCHigh.</span></span>

<span data-ttu-id="8fc6f-146">El método web de versión no está limitado y nunca devuelve códigos de respuesta HTTP 429.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-146">The version web method is not rate limited and does not ever return 429 HTTP Response Codes.</span></span> <span data-ttu-id="8fc6f-147">La respuesta al método web de versión incluye un encabezado Cache-Control que recomienda almacenar los datos durante 1 hora.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-147">The response to the version web method does include a cache-control header recommending caching of the data for 1 hour.</span></span> <span data-ttu-id="8fc6f-148">El resultado del método web de versión puede ser un registro único o una matriz de registros.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-148">The result from the version web method can be a single record or an array of records.</span></span> <span data-ttu-id="8fc6f-149">Los elementos de cada registro son:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-149">The elements of each record are:</span></span>

- <span data-ttu-id="8fc6f-150">instance: el nombre corto de la instancia de servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-150">instance — The short name of the Office 365 service instance.</span></span>
- <span data-ttu-id="8fc6f-151">latest: la versión más reciente de los puntos de conexión de la instancia especificada.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-151">latest — The latest version for endpoints of the specified instance.</span></span>
- <span data-ttu-id="8fc6f-152">versions: una lista de todas las versiones anteriores de la instancia especificada.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-152">versions — A list of all previous versions for the specified instance.</span></span> <span data-ttu-id="8fc6f-153">Este elemento solo se incluye si el parámetro _AllVersions_ es verdadero.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-153">This element is only included if the _AllVersions_ parameter is true.</span></span>

### <a name="examples"></a><span data-ttu-id="8fc6f-154">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-154">Examples:</span></span>

<span data-ttu-id="8fc6f-155">Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-155">Example 1 request URI: [https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8fc6f-p113">Este URI devuelve la versión más reciente de cada instancia de servicio de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-p113">This URI returns the latest version of each Office 365 service instance. Example result:</span></span>

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
> <span data-ttu-id="8fc6f-p114">El GUID para el parámetro ClientRequestID en estos URI es solo un ejemplo. Para probar los URI de servicio web, genere su propio GUID. El servicio web podría bloquear en el futuro los GUID que se muestran en estos ejemplos.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-p114">The GUID for the ClientRequestID parameter in these URIs are only an example. To try the web service URIs out, generate your own GUID. The GUIDs shown in these examples may be blocked by the web service in the future.</span></span>

<span data-ttu-id="8fc6f-161">Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-161">Example 2 request URI: [https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8fc6f-p115">Este URI devuelve la versión más reciente de la instancia de servicio especificada de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-p115">This URI returns the latest version of the specified Office 365 service instance. Example result:</span></span>

```json
{
 "instance": "Worldwide",
 "latest": "2018063000"
}
```

<span data-ttu-id="8fc6f-164">Ejemplo 3 de URI de solicitud: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-164">Example 3 request URI: [https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?Format=CSV&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8fc6f-p116">Este URI muestra los resultados en formato CSV. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-p116">This URI shows output in CSV format. Example result:</span></span>

```csv
instance,latest
Worldwide,2018063000
```

<span data-ttu-id="8fc6f-167">Ejemplo 4 de URI de solicitud: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-167">Example 4 request URI: [https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/version/Worldwide?AllVersions=true&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8fc6f-p117">Este URI muestra todas las versiones anteriores que se han publicado para la instancia de servicio de Office 365 en todo el mundo. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-p117">This URI shows all prior versions that have been published for the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="8fc6f-170">Ejemplo 5 de URI de fuente RSS: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-170">Example 5 RSS Feed URI: [https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS](https://endpoints.office.com/version/worldwide?clientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7&allVersions=true&format=RSS)</span></span>

<span data-ttu-id="8fc6f-p118">Este URI muestra una fuente RSS de las versiones publicadas que incluyen vínculos a la lista de cambios de cada versión. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-p118">This URI shows an RSS feed of the published versions that include links to the list of changes for each version. Example result:</span></span>

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

## <a name="endpoints-web-method"></a><span data-ttu-id="8fc6f-173">Método web de puntos de conexión</span><span class="sxs-lookup"><span data-stu-id="8fc6f-173">Endpoints web method</span></span>

<span data-ttu-id="8fc6f-174">El método web de puntos de conexión devuelve todos los registros de intervalos de direcciones IP y URL que conforman el servicio de Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-174">The endpoints web method returns all records for IP address ranges and URLs that make up the Office 365 service.</span></span> <span data-ttu-id="8fc6f-175">Los datos más recientes del método web de los puntos de conexión se deben usar siempre para la configuración del dispositivo de red.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-175">The latest data from the endpoints web method should always be used for network device configuration.</span></span> <span data-ttu-id="8fc6f-176">Microsoft avisa con 30 días de antelación de publicar nuevas adiciones, para darle tiempo de actualizar las listas de control de acceso y las listas de omisión del servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-176">Microsoft provides advance notice 30 days prior to publishing new additions to give you time to update access control lists and proxy server bypass lists.</span></span> <span data-ttu-id="8fc6f-177">Recomendamos llamar de nuevo al método web de puntos de conexión solo cuando la versión del método web indica que hay disponible una nueva versión de los datos.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-177">We recommend that you only call the endpoints web method again when the version web method indicates that a new version of the data is available.</span></span>

<span data-ttu-id="8fc6f-178">Los parámetros del método web de puntos de conexión son:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-178">Parameters for the endpoints web method are:</span></span>

- <span data-ttu-id="8fc6f-179">**ServiceAreas=<Common | Exchange | SharePoint | Skype>**: una lista separada por comas de las áreas de servicio.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-179">**ServiceAreas=<Common | Exchange | SharePoint | Skype>** — A comma-separated list of service areas.</span></span> <span data-ttu-id="8fc6f-180">Los elementos válidos son _Common_, _Exchange_, _SharePoint_ y _Skype_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-180">Valid items are _Common_, _Exchange_, _SharePoint_, and _Skype_.</span></span> <span data-ttu-id="8fc6f-181">Como los elementos del área de servicio _Common_ son un requisito previo de todas las demás áreas de servicio, el servicio web siempre los incluye.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-181">Because _Common_ service area items are a prerequisite for all other service areas, the web service always includes them.</span></span> <span data-ttu-id="8fc6f-182">Si no incluye este parámetro, se devolverán todas las áreas de servicio.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-182">If you do not include this parameter, all service areas are returned.</span></span>
- <span data-ttu-id="8fc6f-183">**TenantName=<tenant_name>**: su nombre de inquilino de Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-183">**TenantName=<tenant_name>** — Your Office 365 tenant name.</span></span> <span data-ttu-id="8fc6f-184">El servicio web toma el nombre que usted proporciona y lo inserta en las partes de URL que incluyen el nombre de inquilino.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-184">The web service takes your provided name and inserts it in parts of URLs that include the tenant name.</span></span> <span data-ttu-id="8fc6f-185">Si no proporciona un nombre de inquilino, los elementos de las direcciones URL tendrán el carácter comodín (\*).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-185">If you don't provide a tenant name, those parts of URLs have the wildcard character (\*).</span></span>
- <span data-ttu-id="8fc6f-186">**NoIPv6=<true | false>**: establezca el valor en _true_ para excluir las direcciones IPv6 del resultado, si no usa IPv6 en la red.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-186">**NoIPv6=<true | false>** — Set the value to _true_ to exclude IPv6 addresses from the output if you don't use IPv6 in your network.</span></span>
- <span data-ttu-id="8fc6f-187">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>**: este parámetro obligatorio especifica la instancia desde la que se devolverán los puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-187">**Instance=<Worldwide | China | Germany | USGovDoD | USGovGCCHigh>** — This required parameter specifies the instance from which to return the endpoints.</span></span> <span data-ttu-id="8fc6f-188">Instancias válidas son: _Worldwide_, _China_, _Germany_, _USGovDoD_ y _USGovGCCHigh_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-188">Valid instances are: _Worldwide_, _China_, _Germany_, _USGovDoD_, and _USGovGCCHigh_.</span></span>

<span data-ttu-id="8fc6f-189">Si llama al método web de puntos de conexión demasiadas veces desde la misma dirección IP de cliente, es posible que reciba el código de respuesta HTTP _429 (Demasiadas solicitudes)_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-189">If you call the endpoints web method too many times from the same client IP address, you might receive HTTP response code _429 (Too Many Requests)_.</span></span> <span data-ttu-id="8fc6f-190">Si recibe este código de respuesta, espere 1 hora antes de repetir la solicitud o genere un nuevo GUID.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-190">If you get this response code, wait 1 hour before repeating your request, or generate a new GUID for the request.</span></span> <span data-ttu-id="8fc6f-191">Como recomendación general, solo debe llamar al método web de puntos de conexión cuando el método web de versión indica que hay una nueva versión disponible.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-191">As a general best practice, only call the endpoints web method when the version web method indicates that a new version is available.</span></span>

<span data-ttu-id="8fc6f-192">El resultado del método web de puntos de conexión es una matriz de registros en la que cada registro representa un conjunto específico de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-192">The result from the endpoints web method is an array of records in which each record represents a specific endpoint set.</span></span> <span data-ttu-id="8fc6f-193">Los elementos de cada registro son:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-193">The elements for each record are:</span></span>

- <span data-ttu-id="8fc6f-194">id: el número de identificador inmutable del conjunto de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-194">id — The immutable id number of the endpoint set.</span></span>
- <span data-ttu-id="8fc6f-195">serviceArea: el área de servicio que forma parte de: _Common_, _Exchange_, _SharePoint_ o _Skype_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-195">serviceArea — The service area that this is part of: _Common_, _Exchange_, _SharePoint_, or _Skype_.</span></span>
- <span data-ttu-id="8fc6f-196">urls: las URL del conjunto de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-196">urls — URLs for the endpoint set.</span></span> <span data-ttu-id="8fc6f-197">Una matriz JSON de registros DNS.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-197">A JSON array of DNS records.</span></span> <span data-ttu-id="8fc6f-198">Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-198">Omitted if blank.</span></span>
- <span data-ttu-id="8fc6f-199">tcpPorts: puertos TCP del conjunto de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-199">tcpPorts — TCP ports for the endpoint set.</span></span> <span data-ttu-id="8fc6f-200">El formato de todos los elementos de los puertos es una lista separada por coma de puertos o intervalos de puertos separados por un carácter de guión (-).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-200">All ports elements are formatted as a comma-separated list of ports or port ranges separated by a dash character (-).</span></span> <span data-ttu-id="8fc6f-201">Los puertos se aplican a todas las direcciones IP y URL en el conjunto de puntos de conexión de una categoría determinada.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-201">Ports apply to all IP addresses and all URLs in the endpoint set for a given category.</span></span> <span data-ttu-id="8fc6f-202">Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-202">Omitted if blank.</span></span>
- <span data-ttu-id="8fc6f-203">udpPorts: los puertos UDP de los intervalos de direcciones IP en este conjunto de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-203">udpPorts — UDP ports for the IP address ranges in this endpoint set.</span></span> <span data-ttu-id="8fc6f-204">Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-204">Omitted if blank.</span></span>
- <span data-ttu-id="8fc6f-205">ips: los intervalos de direcciones IP asociados a este punto de conexión asociado a los puertos TCP o UDP indicados.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-205">ips — The IP address ranges associated with this endpoint set as associated with the listed TCP or UDP ports.</span></span> <span data-ttu-id="8fc6f-206">Una matriz JSON de intervalos de direcciones IP.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-206">A JSON array of IP address ranges.</span></span> <span data-ttu-id="8fc6f-207">Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-207">Omitted if blank.</span></span>
- <span data-ttu-id="8fc6f-208">category: la categoría de conectividad del conjunto de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-208">category — The connectivity category for the endpoint set.</span></span> <span data-ttu-id="8fc6f-209">Los valores válidos son _Optimize_, _Allow_ y _Default_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-209">Valid values are _Optimize_, _Allow_, and _Default_.</span></span> <span data-ttu-id="8fc6f-210">Si busca el resultado del método web de puntos de conexión para la categoría de una dirección IP o dirección URL específica, es posible que la consulta devuelva varias categorías.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-210">If you search the endpoints web method output for the category of a specific IP address or URL, it is possible that your query will return multiple categories.</span></span> <span data-ttu-id="8fc6f-211">En ese caso, siga la recomendación de la categoría de prioridad más alta.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-211">In such a case, follow the recommendation for the highest priority category.</span></span> <span data-ttu-id="8fc6f-212">Por ejemplo, si el punto de conexión se muestra tanto en _Optimize_ como en _Allow_, debe seguir los requisitos de _Optimize_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-212">For example, if the endpoint appears in both _Optimize_ and _Allow_, you should follow the requirements for _Optimize_.</span></span> <span data-ttu-id="8fc6f-213">Obligatorio.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-213">Required.</span></span>
- <span data-ttu-id="8fc6f-214">expressRoute: _True_ si este conjunto de puntos de conexión se enruta a través de ExpressRoute; _False_ en caso contrario.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-214">expressRoute — _True_ if this endpoint set is routed over ExpressRoute, _False_ if not.</span></span>
- <span data-ttu-id="8fc6f-215">required: _True_ si se requiere que el conjunto de puntos de conexión tenga conectividad para que sea compatible Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-215">required — _True_ if this endpoint set is required to have connectivity for Office 365 to be supported.</span></span> <span data-ttu-id="8fc6f-216">_False_ si este conjunto de puntos de conexión es opcional.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-216">_False_ if this endpoint set is optional.</span></span>
- <span data-ttu-id="8fc6f-217">notes: para puntos de conexión opcionales, este texto describe la funcionalidad de Office 365 que no será disponible si no se puede tener acceso a las direcciones IP o las direcciones URL en este conjunto de puntos de conexión en el nivel de red.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-217">notes — For optional endpoints, this text describes Office 365 functionality that would be unavailable if IP addresses or URLs in this endpoint set cannot be accessed at the network layer.</span></span> <span data-ttu-id="8fc6f-218">Se omite si está en blanco.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-218">Omitted if blank.</span></span>

### <a name="examples"></a><span data-ttu-id="8fc6f-219">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-219">Examples:</span></span>

<span data-ttu-id="8fc6f-220">Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-220">Example 1 request URI: [https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8fc6f-221">Este URI obtiene todos los puntos de conexión de la instancia Worldwide de Office 365 para todas las cargas de trabajo.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-221">This URI obtains all endpoints for the Office 365 worldwide instance for all workloads.</span></span> <span data-ttu-id="8fc6f-222">Ejemplo de resultado en el que se muestra un extracto del resultado:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-222">Example result that shows an excerpt of the output:</span></span>

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

<span data-ttu-id="8fc6f-223">Tenga en cuenta que el resultado completo de la solicitud en este ejemplo contiene otros conjuntos de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-223">Note that the full output of the request in this example would contain other endpoint sets.</span></span>

<span data-ttu-id="8fc6f-224">Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-224">Example 2 request URI: [https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/endpoints/Worldwide?ServiceAreas=Exchange&amp;ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8fc6f-225">Este ejemplo obtiene extremos de la instancia Worldwide de Office 365 para Exchange Online y solo dependencias.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-225">This example obtains endpoints for the Office 365 Worldwide instance for Exchange Online and dependencies only.</span></span>

<span data-ttu-id="8fc6f-226">El resultado para el ejemplo 2 es similar al del ejemplo 1, excepto que los resultados no incluirán puntos de conexión para SharePoint Online o Skype Empresarial Online.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-226">The output for example 2 is similar to example 1 except that the results would not include endpoints for SharePoint Online or Skype for Business Online.</span></span>

## <a name="changes-web-method"></a><span data-ttu-id="8fc6f-227">Método web de cambios</span><span class="sxs-lookup"><span data-stu-id="8fc6f-227">Changes web method</span></span>

<span data-ttu-id="8fc6f-228">El método web de cambios devuelve las actualizaciones más recientes que se han publicado y, por lo general, los cambios en los intervalos de direcciones IP y URL del mes anterior.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-228">The changes web method returns the most recent updates that have been published, typically the previous month's changes to IP address ranges and URLs.</span></span>

<span data-ttu-id="8fc6f-229">Los cambios a datos de los puntos de conexión más críticos son las direcciones IP y URL nuevas.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-229">The most critical changes to endpoints data are new URLs and IP addresses.</span></span> <span data-ttu-id="8fc6f-230">Si no se agrega una dirección IP a la lista de control de acceso de un firewall o una dirección URL a la lista de omisiones del servidor proxy, los usuarios de Office 365 de ese dispositivo de red pueden experimentar una interrupción.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-230">Failure to add an IP address to a firewall access control list or a URL to a proxy server bypass list can cause an outage for Office 365 users behind that network device.</span></span> <span data-ttu-id="8fc6f-231">Independientemente de los requisitos operativos, los nuevos puntos de conexión se publican en el servicio web 30 días antes de la fecha en la que se aprovisionan los puntos de conexión, para darle tiempo de actualizar las listas de control de acceso y las listas de omisión del servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-231">Notwithstanding operational requirements, new endpoints are published to the web service 30 days in advance of the date the endpoints are provisioned for use to give you time to update access control lists and proxy server bypass lists.</span></span>

<span data-ttu-id="8fc6f-232">El parámetro obligatorio del método web de cambios es:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-232">The required parameter for the changes web method is:</span></span>

- <span data-ttu-id="8fc6f-233">**Version=\<YYYYMMDDNN>**: parámetro obligatorio de ruta de URL.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-233">**Version=\<YYYYMMDDNN>** — Required URL route parameter.</span></span> <span data-ttu-id="8fc6f-234">Este valor es la versión que ha implementado actualmente.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-234">This value is the version that you have currently implemented.</span></span> <span data-ttu-id="8fc6f-235">El servicio web devolverá los cambios desde esa versión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-235">The web service will return the changes since that version.</span></span> <span data-ttu-id="8fc6f-236">El formato es _AAAAMMDDNN_, donde _NN_ es un número natural incrementado si hay varias versiones que deben publicarse en un solo día, con _00_ representando la primera actualización para un día determinado.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-236">The format is _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day, with _00_ representing the first update for a given day.</span></span> <span data-ttu-id="8fc6f-237">El servicio web requiere que el parámetro _versión_ contenga exactamente 10 dígitos.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-237">The web service requires the _version_ parameter to contain exactly 10 digits.</span></span>

<span data-ttu-id="8fc6f-238">El método de web de cambios tiene una tasa limitada al igual que el método web de puntos de conexión. </span><span class="sxs-lookup"><span data-stu-id="8fc6f-238">The changes web method is rate limited in the same way as the endpoints web method.</span></span> <span data-ttu-id="8fc6f-239">Si recibe un código de respuesta HTTP 429, espere 1 hora antes de repetir la solicitud o genere un nuevo GUID.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-239">If you receive a 429 HTTP response code, wait 1 hour before repeating your request or generate a new GUID for the request.</span></span>

<span data-ttu-id="8fc6f-240">El resultado del método web de cambios es una matriz de registros en la que cada uno representa un cambio de una versión específica de los puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-240">The result from the changes web method is an array of records in which each record represents a change in a specific version of the endpoints.</span></span> <span data-ttu-id="8fc6f-241">Los elementos de cada registro son:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-241">The elements for each record are:</span></span>

- <span data-ttu-id="8fc6f-242">id: el identificador inmutable del registro de cambios.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-242">id — The immutable id of the change record.</span></span>
- <span data-ttu-id="8fc6f-243">endpointSetId: el identificador del registro del conjunto de puntos de conexión que se ha modificado.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-243">endpointSetId — The ID of the endpoint set record that is changed.</span></span>
- <span data-ttu-id="8fc6f-244">disposition: describe el resultado del cambio en el registro de conjuntos de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-244">disposition — Describes what the change did to the endpoint set record.</span></span> <span data-ttu-id="8fc6f-245">Los valores _change_, _add_ o_remove_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-245">Values are _change_, _add_, or _remove_.</span></span>
- <span data-ttu-id="8fc6f-246">impact: no todos los cambios serán igualmente importantes para todos los entornos.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-246">impact — Not all changes will be equally important to every environment.</span></span> <span data-ttu-id="8fc6f-247">Este elemento describe el impacto previsto en un entorno perimetral de red de empresa como resultado de este cambio.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-247">This element describes the expected impact to an enterprise network perimeter environment as a result of this change.</span></span> <span data-ttu-id="8fc6f-248">Este elemento solo se incluye en los registros de cambio de la versión **2018112800** y posteriores.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-248">This element is included only in change records of version **2018112800** and later.</span></span> <span data-ttu-id="8fc6f-249">Las opciones para el impacto son: AddedIp, una dirección IP se ha agregado a Office 365 y pronto estará disponible en el servicio.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-249">Options for the impact are: — AddedIp – An IP address was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="8fc6f-250">Este es un cambio que debe realizar en un firewall u otro dispositivo de red perimetral de nivel 3.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-250">This represents a change you need to take on a firewall or other layer 3 network perimeter device.</span></span> <span data-ttu-id="8fc6f-251">Si no agrega esto antes de empezar a usarlo, puede experimentar una interrupción.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-251">If you don’t add this before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="8fc6f-252">AddedUrl: se ha agregado una URL a Office 365 y pronto estará disponible en el servicio.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-252">— AddedUrl – A URL was added to Office 365 and will be live on the service soon.</span></span> <span data-ttu-id="8fc6f-253">Esto representa un cambio que debe realizar en un servidor proxy u otro dispositivo de red perimetral de análisis de URL.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-253">This represents a change you need to take on a proxy server or URL parsing network perimeter device.</span></span> <span data-ttu-id="8fc6f-254">Si no agrega esta URL antes de empezar a usarlo, puede experimentar una interrupción.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-254">If you don’t add this URL before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="8fc6f-255">AddedIpAndUrl: se han agregado una dirección IP y una URL.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-255">— AddedIpAndUrl — Both an IP address and a URL were added.</span></span> <span data-ttu-id="8fc6f-256">Este es un cambio que necesita llevar a cabo en un dispositivo de nivel 3 de firewall, en un servidor proxy o un dispositivo de análisis de URL.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-256">This represents a change you need to take on either a firewall layer 3 device or a proxy server or URL parsing device.</span></span> <span data-ttu-id="8fc6f-257">Si no agrega este par IP/URL antes de empezar a usarlo, puede experimentar una interrupción.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-257">If you don’t add this IP/URL pair before we start using it, you may experience an outage.</span></span>
  <span data-ttu-id="8fc6f-258">RemovedIpOrUrl: se ha eliminado al menos una dirección IP o una dirección URL de Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-258">— RemovedIpOrUrl – At least one IP address or URL was removed from Office 365.</span></span> <span data-ttu-id="8fc6f-259">Elimine los puntos de conexión de red de sus dispositivos perimetrales, pero no hay una fecha límite para hacerlo.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-259">Remove the network endpoints from your perimeter devices, but there’s no deadline for you to do this.</span></span>
  <span data-ttu-id="8fc6f-260">ChangedIsExpressRoute: se ha cambiado el atributo de compatibilidad ExpressRoute.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-260">— ChangedIsExpressRoute – The ExpressRoute support attribute was changed.</span></span> <span data-ttu-id="8fc6f-261">Si usa ExpressRoute, es posible que deba realizar una acción en función de la configuración.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-261">If you use ExpressRoute, you might need to take action depending on your configuration.</span></span>
  <span data-ttu-id="8fc6f-262">MovedIpOrUrl: se ha pasado una dirección IP o una dirección URL entre este conjunto de puntos de conexión y otro.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-262">— MovedIpOrUrl – We moved an IP address or Url between this endpoint set and another one.</span></span> <span data-ttu-id="8fc6f-263">Por lo general, no es necesario realizar ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-263">Generally no action is required.</span></span>
  <span data-ttu-id="8fc6f-264">RemovedDuplicateIpOrUrl: se ha eliminado una dirección IP o URL duplicada, pero aún está publicada para Office 365.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-264">— RemovedDuplicateIpOrUrl – We removed a duplicate IP address or Url but it’s still published for Office 365.</span></span> <span data-ttu-id="8fc6f-265">Por lo general, no es necesario realizar ninguna acción.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-265">Generally no action is required.</span></span>
  <span data-ttu-id="8fc6f-266">OtherNonPriorityChanges: se ha cambiado algo menos importante que todas las demás opciones, como el contenido de un campo de nota.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-266">— OtherNonPriorityChanges – We changed something less critical than all of the other options, such as the contents of a note field.</span></span>
- <span data-ttu-id="8fc6f-267">version: la versión del conjunto de puntos de conexión publicado en la que se ha introducido el cambio.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-267">version — The version of the published endpoint set in which the change was introduced.</span></span> <span data-ttu-id="8fc6f-268">Los números de versión tienen el formato _YYYYMMDDNN_, donde _NN_ es un número natural incrementado si hay varias versiones que deben publicarse en un solo día.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-268">Version numbers are of the format _YYYYMMDDNN_, where _NN_ is a natural number incremented if there are multiple versions required to be published on a single day.</span></span>
- <span data-ttu-id="8fc6f-269">previous: una subestructura en la que se detallan los valores anteriores de los elementos modificados en el conjunto de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-269">previous — A substructure detailing previous values of changed elements on the endpoint set.</span></span> <span data-ttu-id="8fc6f-270">Esto no se incluye para los conjuntos de extremos recién añadidos. </span><span class="sxs-lookup"><span data-stu-id="8fc6f-270">This will not be included for newly added endpoint sets.</span></span> <span data-ttu-id="8fc6f-271">Incluye _ExpressRoute_, _serviceArea_, _category,_, _required_, _tcpPorts_, _udpPorts_ y _notes_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-271">Includes  _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="8fc6f-272">current: una subestructura en la que se detallan los valores actualizados de los elementos de los cambios en el conjunto de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-272">current — A substructure detailing updated values of changes elements on the endpoint set.</span></span> <span data-ttu-id="8fc6f-273">Incluye _ExpressRoute_, _serviceArea_, _category,_, _required_, _tcpPorts_, _udpPorts_ y _notes_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-273">Includes _ExpressRoute_, _serviceArea_, _category_, _required_, _tcpPorts_, _udpPorts_, and _notes_.</span></span>
- <span data-ttu-id="8fc6f-274">add: una subestructura en la que se detallan los elementos que se agregarán a colecciones de conjuntos de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-274">add — A substructure detailing items to be added to endpoint set collections.</span></span> <span data-ttu-id="8fc6f-275">Se omite si no hay adiciones.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-275">Omitted if there are no additions.</span></span>
  <span data-ttu-id="8fc6f-276">effectiveDate: define los datos cuando las adiciones estarán disponibles en el servicio.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-276">— effectiveDate — Defines the data when the additions will be live in the service.</span></span>
  <span data-ttu-id="8fc6f-277">ips: los elementos que se agregarán a la matriz _ips_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-277">— ips — Items to be added to the _ips_ array.</span></span>
  <span data-ttu-id="8fc6f-278">urls: los elementos que se agregarán a la matriz _urls_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-278">— urls- Items to be added to the _urls_ array.</span></span>
- <span data-ttu-id="8fc6f-279">remove: una subestructura en la que se detallan los elementos que se eliminarán del conjunto de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-279">remove — A substructure detailing items to be removed from the endpoint set.</span></span> <span data-ttu-id="8fc6f-280">Se omite si no hay eliminaciones.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-280">Omitted if there are no removals.</span></span>
  <span data-ttu-id="8fc6f-281">ips: los elementos que se eliminarán de la matriz _ips_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-281">— ips — Items to be removed from the _ips_ array.</span></span>
  <span data-ttu-id="8fc6f-282">urls: los elementos que se eliminarán de la matriz _urls_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-282">— urls- Items to be removed from the _urls_ array.</span></span>

### <a name="examples"></a><span data-ttu-id="8fc6f-283">Ejemplos:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-283">Examples:</span></span>

<span data-ttu-id="8fc6f-284">Ejemplo 1 de URI de solicitud: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-284">Example 1 request URI: [https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/0000000000?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8fc6f-p144">Se solicitan todos los cambios anteriores a la instancia de servicio worldwide de Office 365. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-p144">This requests all previous changes to the Office 365 worldwide service instance. Example result:</span></span>

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

<span data-ttu-id="8fc6f-287">Ejemplo 2 de URI de solicitud: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="8fc6f-287">Example 2 request URI: [https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7](https://endpoints.office.com/changes/worldwide/2018062700?ClientRequestId=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span>

<span data-ttu-id="8fc6f-p145">Se solicitan los cambios desde la versión especificada a la instancia Worldwide de Office 365. En este caso, la versión especificada es la más reciente. Resultado de ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-p145">This requests changes since the specified version to the Office 365 Worldwide instance. In this case, the version specified is the latest. Example result:</span></span>

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

## <a name="example-powershell-script"></a><span data-ttu-id="8fc6f-291">Ejemplo de script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fc6f-291">Example PowerShell Script</span></span>

<span data-ttu-id="8fc6f-292">Este es un script de PowerShell que puede ejecutar para ver si hay acciones que debe realizar para los datos actualizados.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-292">You can run this PowerShell script to see if there are actions you need to take for updated data.</span></span> <span data-ttu-id="8fc6f-293">Puede ejecutar este script como tarea programada para comprobar si hay una actualización de la versión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-293">You can run this script as a scheduled task to check for a version update.</span></span> <span data-ttu-id="8fc6f-294">Para evitar una carga excesiva en el servicio web, intente no ejecutar el script más de una vez cada hora.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-294">To avoid excessive load on the web service, try not to run the script more than once an hour.</span></span>

<span data-ttu-id="8fc6f-295">Este script hace lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-295">The script does the following:</span></span>

- <span data-ttu-id="8fc6f-296">Comprueba el número de versión de los puntos de conexión de las instancias Worldwide de Office 365 actuales llamando a la API de REST del servicio web.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-296">Checks the version number of the current Office 365 Worldwide instance endpoints by calling the web service REST API.</span></span>
- <span data-ttu-id="8fc6f-297">Comprueba si hay un archivo de versión actual en _$env:TEMP\O365_endpoints_latestversion.txt_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-297">Checks for a current version file at _$Env:TEMP\O365_endpoints_latestversion.txt_.</span></span> <span data-ttu-id="8fc6f-298">La ruta de acceso de la variable global **$env:Temp** es, por lo general, _C:\Users\\ <nombre_usuario\>\AppData\Local\Temp_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-298">The path of the global variable **$Env:TEMP** is usually _C:\Users\\<username\>\AppData\Local\Temp_.</span></span>
- <span data-ttu-id="8fc6f-299">Si esta es la primera vez que se ejecuta el script, este devuelve la versión actual y todas las direcciones IP y URL actuales, escribe la versión de los puntos de conexión en el archivo _$env:TEMP\O365_endpoints_latestversion.txt_ y el resultado de los datos de los puntos de conexión en el archivo _$env:TEMP\O365_endpoints_data.txt_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-299">If this is the first time the script has been run, the script returns the current version and all current IP addresses and URLs, writes the endpoints version to the file _$Env:TEMP\O365_endpoints_latestversion.txt_ and the endpoints data output to the file _$Env:TEMP\O365_endpoints_data.txt_.</span></span> <span data-ttu-id="8fc6f-300">Puede modificar la ruta de acceso y/o el nombre del archivo de salida editando las líneas siguientes:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-300">You can modify the path and/or name of the output file by editing these lines:</span></span>

    ``` powershell
    $versionpath = $Env:TEMP + "\O365_endpoints_latestversion.txt"
    $datapath = $Env:TEMP + "\O365_endpoints_data.txt"
    ```

- <span data-ttu-id="8fc6f-301">En cada ejecución subsiguiente del script, si la versión más reciente del servicio web es la misma que la versión del archivo _O365_endpoints_latestversion.txt_, el script saldrá sin realizar cambios.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-301">On each subsequent execution of the script, if the latest web service version is identical to the version in the _O365_endpoints_latestversion.txt_ file, the script exits without making any changes.</span></span>
- <span data-ttu-id="8fc6f-302">Si la versión más reciente del servicio web es más reciente que la versión del archivo _O365_endpoints_latestversion.txt_, el script devuelve los puntos de conexión y los filtros de los puntos de conexión de las categorías **Allow** y **Optimize**, actualiza la versión en el archivo _O365_endpoints_latestversion.txt_ y escribe los datos actualizados en el archivo _O365_endpoints_data.txt_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-302">When the latest web service version is newer than the version in the _O365_endpoints_latestversion.txt_ file, the script returns the endpoints and filters for the **Allow** and **Optimize** category endpoints, updates the version in the _O365_endpoints_latestversion.txt_ file, and writes the updated data to the _O365_endpoints_data.txt_ file.</span></span>

<span data-ttu-id="8fc6f-303">El script genera un _ClientRequestId_ único para el equipo en el que se ejecuta y reutiliza este identificador en varias llamadas.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-303">The script generates a unique _ClientRequestId_ for the computer it is executed on, and reuses this ID across multiple calls.</span></span> <span data-ttu-id="8fc6f-304">Este ID se almacena en el archivo _O365_endpoints_latestversion.txt_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-304">This ID is stored in the _O365_endpoints_latestversion.txt_ file.</span></span>

### <a name="to-run-the-powershell-script"></a><span data-ttu-id="8fc6f-305">Ejecución del script de PowerShell</span><span class="sxs-lookup"><span data-stu-id="8fc6f-305">To run the PowerShell script</span></span>

1. <span data-ttu-id="8fc6f-306">Copie el script y guárdelo en su unidad de disco duro local o en la ubicación de scripts como _Get-O365WebServiceUpdates.ps1_.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-306">Copy the script and save it to your local hard drive or script location as _Get-O365WebServiceUpdates.ps1_.</span></span>
1. <span data-ttu-id="8fc6f-307">Ejecute el script en el editor de scripts que prefiera, como PowerShell ISE o VS Code, o desde una consola de PowerShell con el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-307">Execute the script in your preferred script editor such as the PowerShell ISE or VS Code, or from a PowerShell console using the following command:</span></span>

    ``` powershell
   powershell.exe -file <path>\Get-O365WebServiceUpdates.ps1
    ```

    <span data-ttu-id="8fc6f-308">No hay ningún parámetro para pasar al script.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-308">There are no parameters to pass to the script.</span></span>

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

## <a name="example-python-script"></a><span data-ttu-id="8fc6f-309">Ejemplo de script de Python</span><span class="sxs-lookup"><span data-stu-id="8fc6f-309">Example Python Script</span></span>

<span data-ttu-id="8fc6f-p150">Este es un script de Python, probado con Python 3.6.3 en Windows 10, que puede ejecutar para ver si hay acciones que debe seguir para los datos actualizados. Este script comprueba el número de versión de los extremos de la instancia Worldwide de Office 365. Cuando se produce un cambio, se descargan los extremos y filtros de los extremos de categoría _Allow_ y _Optimize_. También se usa un único ClientRequestId en varias llamadas y se guarda la versión más reciente que se encuentra en un archivo temporal. Debe llamar a este script una vez cada hora para comprobar si hay una actualización de versión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-p150">Here is a Python script, tested with Python 3.6.3 on Windows 10, that you can run to see if there are actions you need to take for updated data. This script checks the version number for the Office 365 Worldwide instance endpoints. When there is a change, it downloads the endpoints and filters for the _Allow_ and _Optimize_ category endpoints. It also uses a unique ClientRequestId across multiple calls and saves the latest version found in a temporary file. You should call this script once an hour to check for a version update.</span></span>

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

## <a name="web-service-interface-versioning"></a><span data-ttu-id="8fc6f-315">Control de versiones de la interfaz de servicio web</span><span class="sxs-lookup"><span data-stu-id="8fc6f-315">Web Service interface versioning</span></span>

<span data-ttu-id="8fc6f-316">En el futuro, es posible que se necesiten actualizaciones de los parámetros o resultados de estos métodos de servicio web.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-316">Updates to the parameters or results for these web service methods may be required in the future.</span></span> <span data-ttu-id="8fc6f-317">Después de que se publique la versión de disponibilidad general de estos servicios web, Microsoft hará lo posible para avisar con antelación sobre actualizaciones de material en el servicio web.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-317">After the general availability version of these web services is published, Microsoft will make reasonable efforts to provide advance notice of material updates to the web service.</span></span> <span data-ttu-id="8fc6f-318">Cuando Microsoft cree que una actualización necesitará realizar cambios en los clientes que usan el servicio web, mantendrá la versión previa (una versión anterior) del servicio web disponible durante al menos 12 meses después de la publicación de la nueva versión.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-318">When Microsoft believes that an update will require changes to clients using the web service, Microsoft will keep the previous version (one version back) of the web service available for at least 12 months after the release of the new version.</span></span> <span data-ttu-id="8fc6f-319">Es posible que los clientes que no se actualicen durante ese tiempo no puedan tener acceso al servicio web y a sus métodos.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-319">Customers who do not upgrade during that time may be unable to access the web service and its methods.</span></span> <span data-ttu-id="8fc6f-320">Los clientes deben asegurarse de que los clientes del servicio web sigan funcionando sin errores si se llevan a cabo los siguientes cambios en la firma de la interfaz de servicio web:</span><span class="sxs-lookup"><span data-stu-id="8fc6f-320">Customers must ensure that clients of the web service continue working without error if the following changes are made to the web service interface signature:</span></span>

- <span data-ttu-id="8fc6f-321">Agregar un nuevo parámetro opcional a un método web existente que no tenga que facilitarse mediante clientes antiguos y que no afecte al resultado que recibe un cliente anterior.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-321">Adding a new optional parameter to an existing web method that doesn't have to be provided by older clients and doesn't impact the result an older client receives.</span></span>
- <span data-ttu-id="8fc6f-322">Agregar un nuevo atributo con nombre en uno de los elementos REST de respuesta o una de las columnas adicionales a la respuesta CSV.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-322">Adding a new named attribute in one of the response REST items or additional columns to the response CSV.</span></span>
- <span data-ttu-id="8fc6f-323">Agregar un nuevo método web con otro nombre al que no llamen los clientes anteriores.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-323">Adding a new web method with a new name that is not called by the older clients.</span></span>

## <a name="update-notifications"></a><span data-ttu-id="8fc6f-324">Notificaciones de actualización</span><span class="sxs-lookup"><span data-stu-id="8fc6f-324">Update notifications</span></span>

<span data-ttu-id="8fc6f-325">Puede usar algunos métodos diferentes para recibir notificaciones de correo electrónico cuando se publiquen cambios en las direcciones IP y URL en el servicio web.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-325">You can use a few different methods to get email notifications when changes to the IP addresses and URLs are published to the web service.</span></span>

- <span data-ttu-id="8fc6f-326">Para usar una solución de Microsoft Flow, vea [Usar Microsoft Flow para recibir un correo electrónico de cambios en las direcciones IP y URL de Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-326">To use a Microsoft Flow solution, see [Use Microsoft Flow to receive an email for changes to Office 365 IP Addresses and URLs](https://techcommunity.microsoft.com/t5/Office-365-Networking/Use-Microsoft-Flow-to-receive-an-email-for-changes-to-Office-365/m-p/240651).</span></span>
- <span data-ttu-id="8fc6f-327">Para implementar una aplicación lógica de Azure con una plantilla de ARM, vea [Notificación de actualización de Office 365 (v1.1)](https://aka.ms/ipurlws-updates-template).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-327">To deploy an Azure Logic App using an ARM template, see [Office 365 Update Notification (v1.1)](https://aka.ms/ipurlws-updates-template).</span></span>
- <span data-ttu-id="8fc6f-328">Para escribir su propio script de notificación con PowerShell, vea [Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-328">To write your own notification script using PowerShell, see [Send-MailMessage](https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/send-mailmessage).</span></span>

## <a name="exporting-a-proxy-pac-file"></a><span data-ttu-id="8fc6f-329">Exportar un archivo proxy PAC</span><span class="sxs-lookup"><span data-stu-id="8fc6f-329">Exporting a Proxy PAC file</span></span>

<span data-ttu-id="8fc6f-330">[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) es un script de PowerShell que lee los puntos de conexión de red más recientes desde el servicio web URL y la dirección IP de Office 365, y crea un archivo PAC de ejemplo.</span><span class="sxs-lookup"><span data-stu-id="8fc6f-330">[Get-PacFile](https://www.powershellgallery.com/packages/Get-PacFile) is a PowerShell script that reads the latest network endpoints from the Office 365 IP Address and URL web service and creates a sample PAC file.</span></span> <span data-ttu-id="8fc6f-331">Para obtener más información sobre cómo usar Get-PacFile, vea [Usar un archivo PAC para el enrutamiento directo del tráfico fundamental de Office 365](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).</span><span class="sxs-lookup"><span data-stu-id="8fc6f-331">For information on using Get-PacFile, see [Use a PAC file for direct routing of vital Office 365 traffic](managing-office-365-endpoints.md#use-a-pac-file-for-direct-routing-of-vital-office-365-traffic).</span></span>

## <a name="related-topics"></a><span data-ttu-id="8fc6f-332">Temas relacionados</span><span class="sxs-lookup"><span data-stu-id="8fc6f-332">Related Topics</span></span>
  
[<span data-ttu-id="8fc6f-333">Direcciones URL e intervalos de direcciones IP de Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc6f-333">Office 365 URLs and IP address ranges</span></span>](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)

[<span data-ttu-id="8fc6f-334">Administrar puntos de conexión de Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc6f-334">Managing Office 365 endpoints</span></span>](managing-office-365-endpoints.md)
  
[<span data-ttu-id="8fc6f-335">Preguntas frecuentes sobre extremos de Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc6f-335">Office 365 endpoints FAQ</span></span>](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)

[<span data-ttu-id="8fc6f-336">Principios de conectividad de red de Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc6f-336">Office 365 Network Connectivity Principles</span></span>](office-365-network-connectivity-principles.md)

[<span data-ttu-id="8fc6f-337">Red de Office 365 y ajuste de rendimiento</span><span class="sxs-lookup"><span data-stu-id="8fc6f-337">Office 365 network and performance tuning</span></span>](network-planning-and-performance.md)

[<span data-ttu-id="8fc6f-338">Evaluar la conectividad de red de Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc6f-338">Assessing Office 365 network connectivity</span></span>](assessing-network-connectivity.md)
  
[<span data-ttu-id="8fc6f-339">Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="8fc6f-339">Media Quality and Network Connectivity Performance in Skype for Business Online</span></span>](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[<span data-ttu-id="8fc6f-340">Optimización de la red para Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="8fc6f-340">Optimizing your network for Skype for Business Online</span></span>](https://support.office.com/article/b363bdca-b00d-4150-96c3-ec7eab5a8a43)

[<span data-ttu-id="8fc6f-341">Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento</span><span class="sxs-lookup"><span data-stu-id="8fc6f-341">Office 365 performance tuning using baselines and performance history</span></span>](performance-tuning-using-baselines-and-history.md)
  
[<span data-ttu-id="8fc6f-342">Plan de solución de problemas de rendimiento para Office 365</span><span class="sxs-lookup"><span data-stu-id="8fc6f-342">Performance troubleshooting plan for Office 365</span></span>](performance-troubleshooting-plan.md)
