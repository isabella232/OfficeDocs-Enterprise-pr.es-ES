---
title: Configurar la red de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/19/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: ''
description: 'Resumen: Vea estos artículos para comprender las redes de Office 365.'
ms.openlocfilehash: c1976a6b1ae5bff0b5f6f909ee9ab8495f371653
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844031"
---
# <a name="set-up-your-network-for-office-365"></a>Configurar la red de Office 365

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Una parte importante de la integración de Office 365 es asegurarse de que la red y las conexiones a Internet están configuradas para el acceso optimizado. Configurar la red local para obtener acceso a una nube distribuida globalmente de software como servicio (SaaS) es diferente de una red tradicional que está optimizada para el tráfico a los centros de datos locales. 

Use estos artículos para comprender las principales diferencias, así como para modificar los dispositivos perimetrales, los equipos cliente y la red local a fin de obtener el mejor rendimiento para sus usuarios locales.

## <a name="how-office-365-networking-works"></a>Funcionamiento de las redes de Office 365

Vea estos artículos para obtener información general sobre la conectividad de Office 365:

- [Información general de conectividad de red de Office 365](office-365-networking-overview.md)
- [Principios de conectividad de red de Office 365](office-365-network-connectivity-principles.md)
- [Evaluar la conexión de red de Office 365](assessing-network-connectivity.md)

Para obtener información sobre cómo mejorar el rendimiento, vea [Planear la red y ajustar el rendimiento de Office 365](network-planning-and-performance.md).

## <a name="support-office-365-networking-as-a-network-equipment-vendor"></a>Admitir las redes de Office 365 como un proveedor de equipos de red

Si es un proveedor de equipos de red, únase al [Programa para partners de redes de Office 365](office-365-networking-partner-program.md). Inscríbase en el programa para compilar principios de conectividad de red de Office 365 en sus productos y soluciones. 

## <a name="office-365-endpoints"></a>Puntos de conexión de Office 365

Los puntos de conexión son el conjunto de direcciones IP de destino, nombres de dominio DNS y URL para el tráfico de Office 365 en Internet. 

Para optimizar el rendimiento de los servicios basados en la nube de Office 365, algunos puntos de conexión necesitan un tratamiento especial por parte de los exploradores cliente y los dispositivos de la red perimetral. Estos dispositivos incluyen firewalls, inspección e interrupción SSL, dispositivos de inspección de paquetes y sistemas de prevención de pérdida de datos.

Vea [Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md) para obtener detalles.

Actualmente, hay cinco nubes diferentes de Office 365. En esta tabla se le indicará la lista de puntos de conexión de cada una.

|||
|:-------|:-----|
| [Puntos de conexión mundiales](urls-and-ip-address-ranges.md) | Puntos de conexión para suscripciones a Office 365 de todo el mundo, que incluyen Government Community Cloud (GCC) de Estados Unidos. |
| [Puntos de conexión de DoD de Estados Unidos](office-365-u-s-government-dod-endpoints.md) | Puntos de conexión para las suscripciones del Department of Defense (DoD) de Estados Unidos. |
| [Puntos de conexión de GCC High de Estados Unidos](office-365-u-s-government-gcc-high-endpoints.md) | Puntos de conexión para suscripciones a Government Community Cloud High (GCC High) de Estados Unidos. |
| [Puntos de conexión de Office 365 operado por 21Vianet](urls-and-ip-address-ranges-21vianet.md) | Puntos de conexión de Office 365 operado por 21Vianet, que está diseñado para satisfacer las necesidades de Office 365 en China. |
| [Puntos de conexión de Office 365 Germany](office-365-germany-endpoints.md) | Puntos de conexión de una nube independiente en Europa para los clientes con más regulaciones en Alemania, la Unión Europea (UE) y la Asociación Europea de Libre Comercio (AELC). |
|||

Para automatizar la obtención de la lista más reciente de puntos de conexión para su nube de Office 365, vea [Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md).

Para consultar puntos de conexión adicionales, vea estos artículos:

- [Puntos de conexión adicionales no incluidos en el servicio web](additional-office365-ip-addresses-and-urls.md)
- [Solicitudes de red en Office 2016 para Mac](network-requests-in-office-2016-for-mac.md)


## <a name="additional-topics-for-office-365-networking"></a>Otros temas sobre las redes de Office 365

Vea estos artículos para consultar temas especializados sobre las redes de Office 365:

- [Redes de entrega de contenido](content-delivery-networks.md)
- [Compatibilidad con IPv6 en servicios de Office 365](ipv6-support.md)
- [Compatibilidad de NAT con Office 365](nat-support-with-office-365.md)

## <a name="expressroute-for-office-365"></a>ExpressRoute para Office 365

Vea estos artículos para obtener información sobre el uso de ExpressRoute para el tráfico de Office 365:

- [Azure ExpressRoute para Office 365](azure-expressroute.md)
- [Implementación de ExpressRoute para Office 365](implementing-expressroute.md)
- [Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)
- [Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
