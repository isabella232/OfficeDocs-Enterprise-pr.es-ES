---
title: Puntos de conexión de Office 365 de Alemania
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/09/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365_Setup
search.appverid: MOE150
ms.assetid: 8a113a50-0071-4155-bb8e-eba5a8dbd4c8
description: Si su organización usa Office 365 y restringe la conexión de los equipos de la red a Internet, a continuación encontrará los extremos (FQDN, puertos, direcciones URL e intervalos de direcciones IPv4 e IPv6) que debe incluir en las listas de permitidos de salida para asegurarse de que los equipos puedan usar correctamente Office 365.
hideEdit: true
ms.openlocfilehash: 416565d862038362c152505a89d2c51bd48c465e
ms.sourcegitcommit: c1a1b028195342affe0f3367db4e79c42429582a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2020
ms.locfileid: "45387733"
---
# <a name="office-365-germany-endpoints"></a><span data-ttu-id="5500b-103">Puntos de conexión de Office 365 de Alemania</span><span class="sxs-lookup"><span data-stu-id="5500b-103">Office 365 Germany endpoints</span></span>

 <span data-ttu-id="5500b-104">*Se aplica a: Office 365 administrador*</span><span class="sxs-lookup"><span data-stu-id="5500b-104">*Applies To: Office 365 Admin*</span></span>

<span data-ttu-id="5500b-105">Office 365 requiere conectividad a Internet.</span><span class="sxs-lookup"><span data-stu-id="5500b-105">Office 365 requires connectivity to the Internet.</span></span> <span data-ttu-id="5500b-106">Los puntos de conexión a continuación deben ser accesibles para los clientes que usen únicamente los planes de **Office 365 Germany** .</span><span class="sxs-lookup"><span data-stu-id="5500b-106">The endpoints below should be reachable for customers using **Office 365 Germany** plans only.</span></span>
  
 <span data-ttu-id="5500b-107">**Puntos de conexión de Office 365:** [mundial (incluido GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operado por 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany*  |  [Office 365 Administración Pública de Estados Unidos (DoD)](office-365-u-s-government-dod-endpoints.md) | [Office 365 Administración Pública de Estados Unidos (GCC High)](office-365-u-s-government-gcc-high-endpoints.md)  |</span><span class="sxs-lookup"><span data-stu-id="5500b-107">**Office 365 endpoints:** [Worldwide (including GCC)](urls-and-ip-address-ranges.md)  | [Office 365 operated by 21 Vianet](urls-and-ip-address-ranges-21vianet.md)  | *Office 365 Germany* | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md) | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md)  |</span></span>
  
|||
|:-----|:-----|
|<span data-ttu-id="5500b-108">**Última actualización:** 09/07/2020 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Suscripción del registro de cambios](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span><span class="sxs-lookup"><span data-stu-id="5500b-108">**Last updated:** 07/09/2020 - ![RSS](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [Change Log subscription](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7)</span></span> |<span data-ttu-id="5500b-109">**Descargue:** todos los destinos obligatorios y opcionales en una lista de [formato JSON](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="5500b-109">**Download:** all required and optional destinations in one [JSON formatted](https://endpoints.office.com/endpoints/Germany?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) list.</span></span>  <br/> |

<span data-ttu-id="5500b-110">Comience con la administración de los puntos de conexión de [Office 365](managing-office-365-endpoints.md) para comprender nuestras recomendaciones para administrar la conectividad de red con estos datos.</span><span class="sxs-lookup"><span data-stu-id="5500b-110">Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data.</span></span> <span data-ttu-id="5500b-111">Los datos de puntos de conexión se actualizan al principio de cada mes con nuevas direcciones IP y direcciones URL publicadas 30 días antes de estar activo.</span><span class="sxs-lookup"><span data-stu-id="5500b-111">Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active.</span></span> <span data-ttu-id="5500b-112">Esto permite a los clientes que aún no tienen actualizaciones automatizadas para completar sus procesos antes de que sea necesaria una nueva conectividad.</span><span class="sxs-lookup"><span data-stu-id="5500b-112">This lets customers who do not yet have automated updates to complete their processes before new connectivity is required.</span></span> <span data-ttu-id="5500b-113">Los puntos de conexión también se pueden actualizar durante el mes si es necesario para resolver las escalaciones de soporte, los incidentes de seguridad u otros requisitos operativos inmediatos.</span><span class="sxs-lookup"><span data-stu-id="5500b-113">Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements.</span></span> <span data-ttu-id="5500b-114">Siempre puede consultar la suscripción de [registro de cambios](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span><span class="sxs-lookup"><span data-stu-id="5500b-114">You can always refer to the [change log subscription](https://endpoints.office.com/version/Germany?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).</span></span>

<span data-ttu-id="5500b-115">Los datos que se muestran en esta página se generan a partir de los servicios web basados en REST.</span><span class="sxs-lookup"><span data-stu-id="5500b-115">The data shown on this page below is all generated from the REST-based web services.</span></span> <span data-ttu-id="5500b-116">Si usa un script o un dispositivo de red para tener acceso a estos datos, debe ir directamente al [servicio Web](office-365-ip-web-service.md) .</span><span class="sxs-lookup"><span data-stu-id="5500b-116">If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.</span></span>

<span data-ttu-id="5500b-p104">Los siguientes datos de puntos de conexión enumeran los requisitos para la conectividad del equipo de un usuario a Office 365. No incluye las conexiones de red de Microsoft a una red de clientes, a veces denominadas híbridas o conexiones de red de entrada.</span><span class="sxs-lookup"><span data-stu-id="5500b-p104">Endpoint data below lists requirements for connectivity from a user’s machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections.</span></span>

<span data-ttu-id="5500b-p105">Los puntos de conexión se agrupan en cuatro áreas de servicio. Las tres primeras se pueden seleccionar por separado para la conectividad; la cuarta área de servicio es una dependencia común (denominada de Microsoft 365 Common y Office) y debe disponer de conectividad de red en todo momento.</span><span class="sxs-lookup"><span data-stu-id="5500b-p105">The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.</span></span>

<span data-ttu-id="5500b-122">Estas son columnas de datos que se muestran:</span><span class="sxs-lookup"><span data-stu-id="5500b-122">Data columns shown are:</span></span>

- <span data-ttu-id="5500b-p106">**ID**: el número de identificación de la fila, también conocido como un conjunto de puntos de conexión. Este identificador es el mismo que devuelve el servicio web para el conjunto de puntos de conexión.</span><span class="sxs-lookup"><span data-stu-id="5500b-p106">**ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.</span></span>

- <span data-ttu-id="5500b-p107">**Categoría**: muestra si el conjunto de puntos de conexión se clasifica como "Optimizar", "Permitir" o "Predeterminado". Puede leer acerca de estas categorías y encontrar indicaciones para su administración en [https://aka.ms/pnc](https://aka.ms/pnc). Esta columna también muestra los conjuntos de puntos de conexión que deben tener conectividad de red. Para los conjuntos de puntos de conexión que no necesitan conectividad de red, le proporcionamos notas en este campo para indicar qué funcionalidad faltaría si se bloqueara el conjunto de puntos de conexión. Si va a excluir un área de servicio completa, los conjuntos de puntos de conexión enumerados como necesarios no necesitan conectividad.</span><span class="sxs-lookup"><span data-stu-id="5500b-p107">**Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.</span></span>

- <span data-ttu-id="5500b-p108">**EMERGENCIA**: aparece como **Sí** si el conjunto de puntos de conexión se admite en Azure ExpressRoute con prefijos de ruta de Office 365. La comunidad de BGP que incluye los prefijos de ruta que aparecen se alinea con el área de servicio que se muestra. Si EMERGENCIA aparece como **No**, esto significa que ExpressRoute no es compatible con este conjunto de puntos de conexión. Sin embargo, no se debe dar por hecho que no se anuncia ninguna ruta para un conjunto de puntos de conexión cuando EMERGENCIA se establezca como **No**.</span><span class="sxs-lookup"><span data-stu-id="5500b-p108">**ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.</span></span>

- <span data-ttu-id="5500b-p109">**Direcciones**: enumera los FQDN o nombres de dominio con caracteres comodín y los intervalos de direcciones IP para el conjunto de puntos de conexión. Tenga en cuenta que un intervalo de direcciones IP está en formato CIDR y puede incluir varias direcciones IP individuales en la red especificada.</span><span class="sxs-lookup"><span data-stu-id="5500b-p109">**Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.</span></span>
 
- <span data-ttu-id="5500b-p110">**Puertos**: muestra los puertos TCP o UDP que se combinan con las direcciones para formar el punto de conexión de la red. Es posible que observe repeticiones de intervalos de direcciones IP cuando se enumeran diferentes puertos.</span><span class="sxs-lookup"><span data-stu-id="5500b-p110">**Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.</span></span>

[!INCLUDE [Office 365 Germany endpoints](./includes/office-365-germany-endpoints.md)]

 

