---
title: Azure ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/5/2019
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Obtenga información sobre cómo se usa Azure ExpressRoute con Office 365 y cómo planear el proyecto de implementación de red que será necesario si está implementando Azure ExpressRoute para usarlo con Office 365.
ms.openlocfilehash: cf280ff386893f98844e5653ceed180339f701a6
ms.sourcegitcommit: 11751463c952f57f397b886eebfbd37790d461af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2020
ms.locfileid: "44009365"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute para Office 365

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Obtenga información sobre cómo se usa Azure ExpressRoute con Office 365 y cómo planear el proyecto de implementación de red que será necesario si está implementando Azure ExpressRoute para usarlo con Office 365. La infraestructura y los servicios de la plataforma que se ejecutan en Azure se beneficiarán con frecuencia al abordar la arquitectura de red y las consideraciones de rendimiento. En estos casos, se recomienda ExpressRoute para Azure. Las ofertas de software como servicio como Office 365 y Dynamics 365 se han creado para que se pueda acceder a ellos de forma segura y fiable a través de Internet. Puede obtener información sobre el rendimiento y la seguridad de Internet y cuándo puede considerar Azure ExpressRoute para Office 365 en el artículo [Evaluating Office 365 Network Connectivity](assessing-network-connectivity.md).

> [!NOTE]
> Se requiere la autorización de Microsoft para usar ExpressRoute para Office 365. Microsoft revisa todas las solicitudes de los clientes y autoriza el uso de ExpressRoute para Office 365 cuando los requisitos normativos de un cliente mantengan conectividad directa. Si tiene estos requisitos, proporcione el fragmento de texto y el vínculo Web al Reglamento que interpreta que significa que se requiere conectividad directa en el formulario de [solicitud de ExpressRoute para Office 365](https://aka.ms/O365ERReview) para comenzar una revisión de Microsoft. Las suscripciones no autorizadas que intenten crear filtros de ruta para Office 365 recibirán un [mensaje de error](https://support.microsoft.com/kb/3181709).

Ahora puede Agregar una conexión de red directa a Office 365 para el tráfico de red de Office 365 seleccionado. Azure ExpressRoute ofrece una conexión directa y un rendimiento predecible, e incluye un SLA de tiempo de actividad del 99,95% para los componentes de red de Microsoft. Todavía necesitará una conexión a Internet para los servicios que no son compatibles con Azure ExpressRoute.

## <a name="planning-azure-expressroute-for-office-365"></a>Planeación de Azure ExpressRoute para Office 365

Además de la conectividad a Internet, puede optar por enrutar un subconjunto del tráfico de red de Office 365 a través de una conexión directa que ofrezca previsibilidad y un 99,95% de acuerdo de tiempo de actividad para los componentes de red de Microsoft. Azure ExpressRoute le proporciona esta conexión de red dedicada a Office 365 y otros servicios en la nube de Microsoft.

Independientemente de si tiene una WAN MPLS existente, ExpressRoute puede agregarse a su arquitectura de red de tres maneras: a través de un proveedor de coubicación de Exchange en la nube admitido, un proveedor de conexiones de punto a punto Ethernet o a través de un proveedor de conexión MPLS. Vea qué [proveedores están disponibles en su región](https://azure.microsoft.com/documentation/articles/expressroute-locations/). La conexión de Direct ExpressRoute permitirá la conectividad a las aplicaciones descritas en [¿Qué servicios de Office 365 se incluyen?](azure-expressroute.md#BKMK_WhatDoIGet) a continuación. El tráfico de red para el resto de aplicaciones y servicios seguirá atravesando Internet.

Considere el siguiente diagrama de red de alto nivel que muestra un cliente típico de Office 365 que se conecta a los centros de recursos de Microsoft a través de Internet para obtener acceso a todas las aplicaciones de Microsoft, como Office 365, Windows Update y TechNet. Los clientes usan una ruta de red similar independientemente de si se van a conectar desde una red local o de una conexión a Internet independiente.

![Conectividad de red de Office 365](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Ahora mire el diagrama actualizado, que representa un cliente de Office 365 que usa Internet y ExpressRoute para conectarse a Office 365. Tenga en cuenta que algunas conexiones como los nodos de red DNS públicos y entrega de contenido todavía requieren la conexión pública a Internet. Observe también que los usuarios del cliente que no se encuentran en el edificio conectado de ExpressRoute se conectan a través de Internet.

![Conectividad de Office 365 con ExpressRoute](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

¿Todavía desea obtener más información? Obtenga información acerca de cómo [administrar el tráfico de red con Azure expressroute para office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) y aprenda a [configurar Azure ExpressRoute para Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). También hemos grabado una serie de [aprendizaje de Azure ExpressRoute para Office 365](https://channel9.msdn.com/series/aer) en Channel 9 para ayudarle a explicar los conceptos con mayor detalle.

## <a name="what-office-365-services-are-included"></a>¿Qué servicios de Office 365 están incluidos?
<a name="BKMK_WhatDoIGet"> </a>

En la siguiente tabla se enumeran los servicios de Office 365 que son compatibles con ExpressRoute. Consulte el artículo de puntos de conexión de [Office 365](https://aka.ms/o365endpoints) para saber qué solicitudes de red para estas aplicaciones requieren conectividad a Internet.

|**Aplicaciones incluidas**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Protección de Exchange Online<sup>1</sup> <br/> Delve<sup>1</sup> <br/> |
|Skype empresarial online<sup>1</sup> <br/> Microsoft Teams <sup>1</sup> <br/> |
|SharePoint Online<sup>1</sup> <br/> OneDrive para la empresa<sup>1</sup> <br/> Project online<sup>1</sup> <br/> |
|Portal y<sup>1</sup> compartido <br/> Azure Active Directory<sup>1</sup> <br/> Connect<sup>1</sup> de AAD <br/> Office<sup>1</sup> <br/> |

<sup>1</sup> Cada una de estas aplicaciones no es compatible con los requisitos de conectividad de Internet a través de ExpressRoute, consulte el artículo de puntos de conexión de [Office 365](https://aka.ms/o365endpoints) para obtener más información.

Los servicios que no se incluyen en ExpressRoute para Office 365 son Microsoft 365 apps for Enterprise Client downloads, el inicio de sesión de proveedor de identidades local y el servicio Office 365 (operado por 21 ViaNet) en China.

## <a name="implementing-expressroute-for-office-365"></a>Implementar ExpressRoute para Office 365

La implementación de ExpressRoute requiere la participación de los propietarios de la red y de la aplicación, y requiere una planificación minuciosa para determinar la nueva [arquitectura de enrutamiento de red](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), los requisitos de ancho de banda, dónde se implementará la seguridad, alta disponibilidad, etc. Para implementar ExpressRoute, necesitará:

1. Comprenda completamente la necesidad de que ExpressRoute satisfaga en su plan de conectividad de Office 365. Comprenda qué aplicaciones usarán Internet o ExpressRoute y planee completamente la capacidad de la red, la seguridad y las necesidades de alta disponibilidad en el contexto de usar tanto Internet como ExpressRoute para el tráfico de Office 365.

2. Determinar las ubicaciones de salida y emparejamiento para el tráfico de Internet y ExpressRoute<sup>1</sup>.

3. Determine la capacidad necesaria en las conexiones de Internet y ExpressRoute.

4. Disponer de un plan para implementar la seguridad y otros controles perimetrales estándar<sup>1</sup>.

5. Tener una cuenta de Microsoft Azure válida para suscribirse a ExpressRoute.

6. Seleccione un modelo de conectividad y un [proveedor aprobado](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Tenga en cuenta que los clientes pueden seleccionar varios modelos de conectividad o asociados y el socio no tiene que ser el mismo que el proveedor de red existente.

7. Validar la implementación antes de dirigir el tráfico a ExpressRoute.

8. Opcionalmente, [implemente QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) y evalúe la expansión regional.

<sup>1</sup> Consideraciones de rendimiento importantes. Las decisiones aquí pueden afectar drásticamente a la latencia, que es fundamental para las aplicaciones como Skype empresarial.

Para obtener referencias adicionales, use nuestra [Guía de enrutamiento](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) además de la documentación de [ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).

Para comprar ExpressRoute para Office 365, deberá trabajar con uno o más [proveedores aprobados](https://azure.microsoft.com/documentation/articles/expressroute-locations/) para aprovisionar los circuitos de tamaño y número que desee con una suscripción Premium de ExpressRoute. No hay licencias adicionales para comprar de Office 365.

Este es un vínculo breve que se puede usar para volver: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

¿Está preparado para registrarse para [ExpressRoute para Office 365](https://aka.ms/ert)?

## <a name="related-topics"></a>Temas relacionados

[Evaluar la red de Office 365](assessing-network-connectivity.md)

[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)

[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)

[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)

[Implementación de ExpressRoute para Office 365](implementing-expressroute.md)

[Uso de las comunidades BGP en ExpressRoute para los escenarios de Office 365 (versión preliminar)](bgp-communities-in-expressroute.md)

[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)

[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)

[Direcciones URL e intervalos de direcciones IP de Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)

## <a name="see-also"></a>Vea también

[Información general de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
