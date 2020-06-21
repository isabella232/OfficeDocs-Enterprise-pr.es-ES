---
title: Intervalos de direcciones IP y URL de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/16/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- MBS150
- MOM160
- BCS160
ms.assetid: 8548a211-3fe7-47cb-abb1-355ea5aa88a2
description: 'Summary: Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).'
hideEdit: true
ms.openlocfilehash: 58453be147fec41bb35b7d6d758ce3d5df5a4148
ms.sourcegitcommit: f2a4b77c8c3932beb1a78bf2f5bf793fefb3fa49
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/16/2020
ms.locfileid: "44747376"
---
# <a name="office-365-urls-and-ip-address-ranges"></a>Intervalos de direcciones IP y URL de Office 365

 **Summary:** Office 365 requires connectivity to the Internet. The endpoints below should be reachable for customers using Office 365 plans, including Government Community Cloud (GCC).
  
> [!NOTE]
> Como parte de la respuesta de Microsoft a la crisis de COVID-19, Microsoft ha declarado una moratoria temporal en algunos cambios de direcciones IP y URL planeados. Esta moratoria está diseñada para proporcionar a los clientes la confianza y la simplicidad en la implementación de optimizaciones de red recomendadas para escenarios de trabajo desde casa de Office 365. Desde el 24 de marzo de 2020 hasta el 30 de junio de 2020 esta moratoria detendrá los cambios de los servicios clave de Office 365 (Exchange Online, SharePoint Online y Microsoft Teams) en intervalos de IP y URL incluidos en la categoría Optimizar. Los cambios en otras categorías de puntos de conexión se producirán de la forma habitual. Durante este período, los clientes pueden usar las definiciones de puntos de conexión de servicio de categoría Optimizar de Office 365 de forma estática para realizar optimizaciones de red dirigidas (como reservas de ancho de banda o configuración de túnel VPN dividido) con un riesgo mínimo para la conectividad de Office 365 gracias a los cambios en la red de la nube. Para garantizar que no se produzcan interrupciones de servicio al final del período de moratoria, Microsoft recomienda que los clientes implementen procesos de administración de cambios y/o de automatización para los puntos de conexión de servicio de Office 365 con las instrucciones proporcionadas en [Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md).

> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
*Office 365 mundial (incluido GCC)* | [Office 365 operado por 21Vianet ](urls-and-ip-address-ranges-21vianet.md) | [Office 365 Germany](office-365-germany-endpoints.md) | [Office 365 U.S. Government DoD](office-365-u-s-government-dod-endpoints.md)  | [Office 365 U.S. Government GCC High](office-365-u-s-government-gcc-high-endpoints.md) |
  
||||
|:-----|:-----|:-----|
|**Última actualización:** 06/16/2020- ![ ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [suscripción de registro de cambios](https://endpoints.office.com/version/worldwide?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) de RSS <br/> |**Descargue:** todos los destinos obligatorios y opcionales en una lista de [formato JSON](https://endpoints.office.com/endpoints/worldwide?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7).  <br/> | **Use:** nuestros [archivos PAC](managing-office-365-endpoints.md#pacfiles) de proxy <br/> |

 Start with [Managing Office 365 endpoints](managing-office-365-endpoints.md) to understand our recommendations for managing network connectivity using this data. Endpoints data is updated at the beginning of each month with new IP Addresses and URLs published 30 days in advance of being active. This allows for customers who do not yet have automated updates to complete their processes before new connectivity is required. Endpoints may also be updated during the month if needed to address support escalations, security incidents, or other immediate operational requirements. The data shown on this page below is all generated from the REST-based web services. If you are using a script or a network device to access this data, you should go to the [Web service](office-365-ip-web-service.md) directly.

Endpoint data below lists requirements for connectivity from a user's machine to Office 365. It does not include network connections from Microsoft into a customer network, sometimes called hybrid or inbound network connections. See [Additional endpoints](additional-office365-ip-addresses-and-urls.md) for more information.

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Estas son columnas de datos que se muestran:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as "Optimize", "Allow", or "Default". You can read about these categories and guidance for management of them at [New Office 365 endpoint categories](https://docs.microsoft.com/office365/enterprise/office-365-network-connectivity-principles#new-office-365-endpoint-categories). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **ER**: This is **Yes** if the endpoint set is supported over Azure ExpressRoute with Office 365 route prefixes. The BGP community that includes the route prefixes shown aligns with the service area listed. When ER is **No**, this means that ExpressRoute is not supported for this endpoint set. However, it should not be assumed that no routes are advertised for an endpoint set where ER is **No**.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.

[!INCLUDE [Office 365 worldwide endpoints](./includes/office-365-worldwide-endpoints.md)]

>[!Note]
>Para obtener recomendaciones sobre las direcciones URL y direcciones IP de Yammer, consulte [esta entrada de blog](https://techcommunity.microsoft.com/t5/Yammer-Blog/Using-hard-coded-IP-addresses-for-Yammer-is-not-recommended/ba-p/276592).
>

## <a name="related-topics"></a>Temas relacionados

[Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md)
  
[Solución de problemas de conectividad de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d.aspx)
  
[Conectividad de clientes](https://support.office.com/article/client-connectivity-4232abcf-4ae5-43aa-bfa1-9a078a99c78b)
  
[Redes de entrega de contenido](https://support.office.com/article/content-delivery-networks-0140f704-6614-49bb-aa6c-89b75dcd7f1f)
  
[Intervalos IP del centro de datos de Microsoft Azure](https://www.microsoft.com/download/details.aspx?id=41653)
  
[Espacio IP público de Microsoft](https://www.microsoft.com/download/details.aspx?id=53602)
