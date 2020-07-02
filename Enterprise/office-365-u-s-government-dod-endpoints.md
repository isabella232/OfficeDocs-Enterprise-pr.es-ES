---
title: Extremos DoD del gobierno de Estados Unidos de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/29/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
search.appverid:
- OGA150
- OGC150
- OGD150
- MOE150
ms.assetid: 5d7dce60-4892-4b58-b45e-ee42fe8a907f
f1.keywords:
- NOCSH
description: 'Resumen: Office 365 requiere conectividad a Internet. Los puntos de conexión a continuación deben ser accesibles para los clientes que usen solo planes de Office 365 U.S. Government DoD.'
hideEdit: true
ms.openlocfilehash: 15f6a39c5a17c9899ff6db24bc7c8d11565f0b37
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997602"
---
# <a name="office-365-us-government-dod-endpoints"></a>Extremos DoD del gobierno de Estados Unidos de Office 365

*Se aplica a: Office 365 administrador*

 Office 365 requiere conectividad a Internet. Los puntos de conexión a continuación deben ser accesibles para los clientes que usen solo planes de Office 365 U.S. Government DoD.
  
> [!NOTE]
> Microsoft has released a REST-based web service for the IP address and FQDN entries on this page. This new service will help you configure and update network perimeter devices such as firewalls and proxy servers. You can download the list of endpoints, the current version of the list, or specific changes. This service replaces the XML document linked from this page, which was deprecated on October 2, 2018. To try out this new service, go to [Web service](office-365-ip-web-service.md).
  
 **Puntos de conexión de Office 365:** [mundial (incluido GCC)](urls-and-ip-address-ranges.md) | [Office 365 operado por 21Vianet](urls-and-ip-address-ranges-21vianet.md)  | [Office 365 Germany](office-365-germany-endpoints.md)  |  *Office 365 Administración Pública de Estados Unidos (DoD)* | [Office 365 Administración Pública de Estados Unidos (GCC High)](office-365-u-s-government-gcc-high-endpoints.md) |
  
|||
|:-----|:-----|
|**Última actualización:** 06/29/2020- ![ ](media/5dc6bb29-25db-4f44-9580-77c735492c4b.png) [suscripción de registro de cambios](https://endpoints.office.com/version/USGOVDoD?allversions=true&format=rss&clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) de RSS <br/> |**Descargar:** lista completa en [formato JSON](https://endpoints.office.com/endpoints/USGOVDoD?clientrequestid=b10c5ed1-bad1-445f-b386-b919946339a7) <br/> |

 Comience con la administración de los puntos de conexión de [Office 365](managing-office-365-endpoints.md) para comprender nuestras recomendaciones para administrar la conectividad de red con estos datos. Los datos de puntos de conexión se actualizan al principio de cada mes con nuevas direcciones IP y direcciones URL publicadas 30 días antes de estar activo. Esto permite a los clientes que aún no tienen actualizaciones automatizadas para completar sus procesos antes de que sea necesaria una nueva conectividad. Los puntos de conexión también se pueden actualizar durante el mes si es necesario para resolver las escalaciones de soporte, los incidentes de seguridad u otros requisitos operativos inmediatos. Los datos que se muestran en esta página se generan a partir de los servicios web basados en REST. Si usa un script o un dispositivo de red para tener acceso a estos datos, debe ir directamente al [servicio Web](office-365-ip-web-service.md) .

Datos de extremo a continuación se enumeran los requisitos para la conectividad desde el equipo de un usuario a Office 365. No incluye conexiones de red de Microsoft en una red de cliente, a veces denominadas conexiones de red híbridas o entrantes. Para obtener más información, consulte [puntos de conexión adicionales no incluidos en el servicio Web](additional-office365-ip-addresses-and-urls.md). 

The endpoints are grouped into four service areas. The first three service areas can be independently selected for connectivity. The fourth service area is a common dependency (called Microsoft 365 Common and Office) and must always have network connectivity.

Estas son columnas de datos que se muestran:

- **ID**: The ID number of the row, also known as an endpoint set. This ID is the same as is returned by the web service for the endpoint set.

- **Category**: Shows whether the endpoint set is categorized as “Optimize”, “Allow”, or “Default”. You can read about these categories and guidance for management of them at [https://aka.ms/pnc](https://aka.ms/pnc). This column also lists which endpoint sets are required to have network connectivity. For endpoint sets which are not required to have network connectivity, we provide notes in this field to indicate what functionality would be missing if the endpoint set is blocked. If you are excluding an entire service area, the endpoint sets listed as required do not require connectivity.

- **Er**: esto es **sí** si el conjunto de puntos de conexión es compatible con Azure ExpressRoute con los prefijos de ruta de Office 365. La comunidad de BGP que incluye los prefijos de ruta que se muestran se alinea con el área de servicio enumerada. Cuando ER es **no**, significa que ExpressRoute no es compatible con este conjunto de puntos de conexión. Sin embargo, no debe suponerse que ninguna ruta se anuncie para un punto de conexión en el que ER es **no**. Si tiene previsto usar Azure AD Connect, lea la [sección consideraciones especiales](https://docs.microsoft.com/azure/active-directory/hybrid/reference-connect-instances#microsoft-azure-government) para asegurarse de que tiene la configuración adecuada de Azure ad Connect.

- **Addresses**: Lists the FQDNs or wildcard domain names and IP Address ranges for the endpoint set. Note that an IP Address range is in CIDR format and may include many individual IP Addresses in the specified network.
 
- **Ports**: Lists the TCP or UDP ports that are combined with the Addresses to form the network endpoint. You may notice some duplication in IP Address ranges where there are different ports listed.
 
[!INCLUDE [Office 365 U.S. Government DoD endpoints](./includes/office-365-u.s.-government-dod-endpoints.md)]
  
Notas sobre esta tabla:

- El centro de seguridad y cumplimiento (SCC) proporciona compatibilidad con Azure ExpressRoute para Office 365. Lo mismo se aplica a muchas características expuestas a través del SCC, como la creación de informes, la auditoría, la exhibición avanzada de documentos electrónicos, la DLP unificada y el gobierno de datos. Dos características específicas, la importación de PST y la exportación de exhibición de documentos electrónicos, actualmente no admiten Azure ExpressRoute con solo filtros de ruta de Office 365 debido a su dependencia del almacenamiento de blobs de Azure. Para usar estas características, necesitará conectividad independiente a Azure BLOB Storage mediante las opciones de conectividad de Azure que se puedan admitir, que incluyen conectividad a Internet o Azure ExpressRoute con filtros de ruta pública de Azure. Debe evaluar el establecimiento de dicha conectividad para ambas características. El equipo de protección de la información de Office 365 conoce esta limitación y está trabajando activamente para permitir que Azure ExpressRoute para Office 365 se limite a los filtros de ruta de Office 365 para ambas características.

- Hay puntos de conexión opcionales adicionales para las aplicaciones de Microsoft 365 para empresas que no se muestran y que no son necesarios para que los usuarios inicien aplicaciones de Microsoft 365 para aplicaciones empresariales y editar documentos. Los puntos de conexión opcionales se hospedan en centros de datos de Microsoft y no procesan, transmiten ni almacenan datos de clientes. Se recomienda que las conexiones de usuario con estos extremos se dirijan al perímetro de salida de Internet predeterminado.
