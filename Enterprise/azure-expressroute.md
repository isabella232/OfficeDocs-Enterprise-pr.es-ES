---
title: Azure ExpressRoute para Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 6d2534a2-c19c-4a99-be5e-33a0cee5d3bd
description: Obtenga información sobre cómo se usa ExpressRoute de Azure con Office 365 y cómo planear el proyecto de implementación de red que será necesario si va a implementar ExpressRoute de Azure para su uso con Office 365.
ms.openlocfilehash: c8cff4ef85c4383ba04829cf3cf8da3a1bc36715
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25911404"
---
# <a name="azure-expressroute-for-office-365"></a>Azure ExpressRoute para Office 365

Obtenga información sobre cómo se usa ExpressRoute de Azure con Office 365 y cómo planear el proyecto de implementación de red que será necesario si va a implementar ExpressRoute de Azure para su uso con Office 365. Servicios de infraestructura y plataforma que se ejecutan en Azure a menudo se beneficiarán hacer frente a las consideraciones de rendimiento y arquitectura de red. En estos casos se recomienda ExpressRoute de Azure. Software como una ofertas de servicios como Office 365 y Dynamics 365 se han creado para tener acceso de forma segura y fiable a través de Internet. Puede leer acerca de seguridad y el rendimiento de Internet y cuándo puede resultar conveniente ExpressRoute de Azure para Office 365 en el artículo de [la conectividad de red a Office 365](network-connectivity.md).

> [!NOTE]
> Autorización de Microsoft es necesario para usar ExpressRoute para Office 365. Microsoft revisa cada solicitud de cliente y autoriza ExpressRoute para el uso de Office 365 cuando conectividad directa obliga a requisitos legales de un cliente. Si tiene estos requisitos, proporcione el vínculo web y se muestra un extracto de texto al Reglamento que interpretar para indicar que se necesita conectividad directa en la [ExpressRoute para el formulario de solicitud de Office 365](https://aka.ms/O365ERReview) para comenzar una revisión de Microsoft. Las suscripciones no autorizadas intenta crear filtros de ruta para Office 365 recibirá un [mensaje de error](https://support.microsoft.com/kb/3181709). 

Ahora puede agregar una conexión de red directa a Office 365 para el tráfico de red de Office 365 seleccionado. ExpressRoute Azure ofrece una conexión directa, performance predecible y se proporciona con un SLA de 99,95% de tiempo de actividad de los componentes de red de Microsoft. Aún podrá requieren una conexión a internet para los servicios que no se admiten a través de ExpressRoute de Azure.

## <a name="planning-azure-expressroute-for-office-365"></a>Planeación de ExpressRoute Azure para Office 365

Además de la conectividad a internet, es posible que elija enrutar un subconjunto de su tráfico de red de Office 365 a través de una conexión directa que ofrece la capacidad de predicción y un tiempo de actividad de 99,95% SLA para los componentes de red de Microsoft. ExpressRoute Azure proporciona esta conexión de red dedicada a Office 365 y otros servicios de nube de Microsoft.

Independientemente de si tienen una WAN de MPLS existente, se puede agregar ExpressRoute a la arquitectura de red en una de estas tres maneras; a través de un proveedor de co-ubicación exchange admitidos en la nube, un proveedor de conexión de punto a punto de Ethernet, o a través de un proveedor de conexión de MPLS. Vea ¿qué [proveedores están disponibles en su región](https://azure.microsoft.com/documentation/articles/expressroute-locations/). La conexión directa de ExpressRoute va a habilitar la conectividad con las aplicaciones que se describen en [se incluyen servicios de qué Office 365?](azure-expressroute.md#BKMK_WhatDoIGet) por debajo. El tráfico de red para todos los otros servicios y aplicaciones seguirán atravesar internet.

Tenga en cuenta el siguiente diagrama de red de nivel alto que muestra a un cliente de Office 365 típico conectarse a centros de datos de Microsoft a través de internet para el acceso a todas las aplicaciones de Microsoft, como Office 365, Windows Update y TechNet. Los clientes usar una ruta de acceso de red similar, independientemente de si va a conectar desde una red local o desde una conexión a internet independientes.

![Conectividad de red de Office 365](media/9d8bc622-4a38-4a3b-a0f3-68657712d460.png)

Ahora, mire el diagrama actualizado que refleja a un cliente de Office 365 que usa internet y ExpressRoute para conectarse a Office 365. Tenga en cuenta que algunas conexiones como nodos DNS pública y la red de entrega de contenido sigue siendo necesitan la conexión a internet pública. Tenga en cuenta también los usuarios del cliente que no se encuentran en su ExpressRoute creación conectado se conectan a través de Internet.

![Conectividad de Office 365 con ExpressRoute](media/251788c4-0937-4584-9b2c-df08e11611fc.png)

¿Aún desea más información? Obtenga información sobre cómo [administrar el tráfico de red con ExpressRoute de Azure para Office 365](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408) y obtenga información sobre cómo [Configurar ExpressRoute de Azure para Office 365](https://azure.microsoft.com/documentation/articles/expressroute-faqs/). También que hemos registrado una serie 10 [ExpressRoute de Azure para Office 365 aprendizaje](https://channel9.msdn.com/series/aer) en Channel 9 para ayudar a explicar los conceptos más detenidamente.

([ExpressRoute de azure para Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="what-office-365-services-are-included"></a>¿Qué servicios de Office 365 se incluyen?
<a name="BKMK_WhatDoIGet"> </a>

En la siguiente tabla se enumera los servicios de Office 365 se admiten a través de ExpressRoute. Por favor, revise el [artículo de los extremos de Office 365](https://aka.ms/o365endpoints) para comprender qué solicitudes de red para estas aplicaciones requieren conectividad a internet.

|**Aplicaciones incluidas**|
|:-----|
|Exchange Online<sup>1</sup> <br/> Exchange Online Protection<sup>1</sup> <br/> Profundizar<sup>1</sup> <br/> |
|Skype para profesionales en línea<sup>1</sup> <br/> |
|<sup>1</sup> de SharePoint Online <br/> OneDrive for Business<sup>1</sup> <br/> Project Online<sup>1</sup> <br/> |
|Portal y compartida<sup>1</sup> <br/> <sup>1</sup> de Azure Active Directory <br/> AAD conectar<sup>1</sup> <br/> Office Online<sup>1</sup> <br/> |

<sup>1</sup> Cada una de estas aplicaciones tienen requisitos de conectividad de internet no se admite a través de ExpressRoute, vea el [artículo de los extremos de Office 365](https://aka.ms/o365endpoints) para obtener más información.

Los servicios que no se incluyen con ExpressRoute para Office 365 son descargas del cliente de Office 365 ProPlus, inicio de sesión de proveedor de identidad de local y servicio de Office 365 (operado por Vianet 21) en China.

([ExpressRoute de azure para Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="implementing-expressroute-for-office-365"></a>Implementación de ExpressRoute para Office 365

Implementación ExpressRoute requiere la participación de los propietarios de red y las aplicaciones y requiere implementa cuidadosa planeación determinar la nueva [arquitectura de enrutamiento de red](https://support.office.com/article/e1da26c6-2d39-4379-af6f-4da213218408), los requisitos de ancho de banda, donde será la seguridad, alta disponibilidad y así sucesivamente. Para implementar ExpressRoute, necesitará:

1. Comprender la necesidad de que expressroute satisfaga en la planeación de la conectividad de Office 365. Comprender qué aplicaciones usarán la internet o ExpressRoute y planee totalmente la capacidad de red, seguridad y alta disponibilidad necesitan en el contexto del uso de internet y ExpressRoute para Office 365 el tráfico.

2. Determine la salida y las ubicaciones de interconexión de internet y el tráfico de ExpressRoute<sup>1</sup>.

3. Determinar la capacidad necesaria en internet y en conexiones de ExpressRoute.

4. Tener un plan para implementación de seguridad y otros controles de perímetro estándar<sup>1</sup>.

5. Tener una cuenta válida de Microsoft Azure para suscribirse a ExpressRoute.

6. Seleccione un modelo de conectividad y un [aprobada por el proveedor](https://azure.microsoft.com/documentation/articles/expressroute-locations/). Tenga en cuenta, los clientes pueden seleccionar varios modelos de conectividad a o socios y si el socio no necesita ser la misma que su proveedor de red existente.

7. Validar la implementación antes de dirigir el tráfico a ExpressRoute.

8. Opcionalmente, puede [implementar QoS](https://support.office.com/article/ExpressRoute-and-QoS-in-Skype-for-Business-Online-20c654da-30ee-4e4f-a764-8b7d8844431d) y evaluar la expansión regional.

<sup>1</sup> Consideraciones de rendimiento importantes. Decisiones aquí pueden afectar considerablemente a latencia que es fundamental para las aplicaciones como Skype para la empresa.

Para obtener otras referencias, use nuestra [Guía enrutamiento](https://support.office.com/article/Routing-with-ExpressRoute-for-Office-365-e1da26c6-2d39-4379-af6f-4da213218408) además de la [documentación de ExpressRoute](https://azure.microsoft.com/documentation/articles/expressroute-introduction/).

Para adquirir ExpressRoute para Office 365, debe trabajar con uno o más [aprobado proveedores](https://azure.microsoft.com/documentation/articles/expressroute-locations/) para aprovisionar el número que desee y circuitos de tamaño con una suscripción ExpressRoute Premium. No hay licencias adicionales para comprar de Office 365.

Este es un vínculo breve que se puede usar para volver: [https://aka.ms/expressrouteoffice365](https://aka.ms/expressrouteoffice365)

¿Está listo para inscripción para [ExpressRoute para Office 365](https://aka.ms/ert)?

([ExpressRoute de azure para Office 365](azure-expressroute.md#BKMK_HOME))

## <a name="related-topics"></a>Temas relacionados

[Conectividad de red a Office 365](network-connectivity.md)

[Administrar ExpressRoute para la conectividad de Office 365](managing-expressroute-for-connectivity.md)

[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)

[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)

[Implementación de ExpressRoute para Office 365](implementing-expressroute.md)

[Uso de comunidades BGP en ExpressRoute para escenarios de Office 365 (versión preliminar)](bgp-communities-in-expressroute.md)

[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)

[Ajuste del rendimiento de Office 365 mediante líneas base y el historial de rendimiento](performance-tuning-using-baselines-and-history.md)

[Plan de solución de problemas de rendimiento para Office 365](performance-troubleshooting-plan.md)

[Direcciones URL e intervalos de direcciones IP de Office 365](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges)

[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)
