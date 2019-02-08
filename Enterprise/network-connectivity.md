---
title: Conectividad de red a Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Office 365 está diseñado para permitir a los clientes de todo el mundo para conectarse al servicio con una conexión a internet. A medida que evoluciona el servicio, la seguridad, rendimiento y confiabilidad de Office 365 se han mejorado en función de los clientes que usen internet para establecer una conexión al servicio.
ms.openlocfilehash: da086aa3fcd23ccb4a82cde2a1f7d812c111071a
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25911394"
---
# <a name="network-connectivity-to-office-365"></a>Conectividad de red a Office 365

Office 365 está diseñado para permitir a los clientes de todo el mundo para conectarse al servicio con una conexión a internet. A medida que evoluciona el servicio, la seguridad, rendimiento y confiabilidad de Office 365 se han mejorado en función de los clientes que usen internet para establecer una conexión al servicio.
  
Los clientes que planean usar Office 365 deben evaluar sus necesidades de conectividad de internet existentes y previstas como parte del proyecto de implementación. Para las implementaciones de clase empresarial confiable y tamaño adecuado la conectividad a internet es una parte fundamental de consumo de escenarios y las características de Office 365.
  
Muchas personas diferentes y las organizaciones según el tamaño y las preferencias se pueden realizar las evaluaciones de la red. El ámbito de la evaluación de red también puede variar dependiendo de dónde está en proceso de implementación de. Para ayudar a obtener una mejor comprensión de lo que se necesita para realizar una evaluación de la red, nos hemos producido una guía de evaluación de la red para ayudarle a comprender las opciones disponibles para usted. Esta evaluación determina qué pasos y recursos deben agregarse al proyecto de implementación para que pueda adoptar correctamente Office 365.
  
Una evaluación integral de la red, como los que se indican en el [Marco de operaciones de Skype](https://www.skypeoperationsframework.com/) proporcionará soluciones posibles en los desafíos de diseño junto con los detalles de la implementación de la red. La mayoría de las evaluaciones de red que le indicará que se puede acomodar más conectividad de red a Office 365 con [configuración secundaria o cambios de diseño](https://aka.ms/manageo365endpoints) a la red existente y la infraestructura de salida de internet.

Algunos evaluaciones indicará la conectividad de red a Office 365 requiere las inversiones adicionales en componentes de red. Por ejemplo, las inversiones en infraestructura de enrutamiento optimizada para admitir la conectividad a internet a Office 365 o ancho de banda de WAN. En ocasiones, una evaluación indicará la conectividad de red a Office 365 está influenciada por Reglamento o el rendimiento de los requisitos para escenarios como [Skype para calidad de medios en línea de negocio](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Estos requisitos adicionales que puede producir las inversiones en infraestructura de conectividad a internet, optimización de enrutamiento y la conectividad directa especializada.
  
> [!NOTE]
> Autorización de Microsoft es necesario para usar ExpressRoute para Office 365. Microsoft revisa cada solicitud de cliente y sólo autoriza ExpressRoute para el uso de Office 365 cuando conectividad directa obliga a requisitos legales de un cliente. Si tiene estos requisitos, proporcione el vínculo web y se muestra un extracto de texto al Reglamento que interpretar para indicar que se necesita conectividad directa en la [ExpressRoute para el formulario de solicitud de Office 365](https://aka.ms/O365ERReview) para comenzar una revisión de Microsoft. Las suscripciones no autorizadas intenta crear filtros de ruta para Office 365 recibirá un [mensaje de error](https://support.microsoft.com/kb/3181709).
  
Puntos claves a tener en cuenta al planear la evaluación de la red para Office 365:
  
- Office 365 es un servicio segura, confiable y de alto rendimiento que se ejecuta a través de internet pública. Se seguirán invertir para mejorar estos aspectos del servicio. Todos los servicios de Office 365 están disponibles a través de la conectividad a internet.

- Constantemente estamos optimizando principales llegar aspectos de Office 365 como la disponibilidad, global y rendimiento para internet en función de conectividad. Por ejemplo, muchos de los servicios de Office 365 sacar provecho de un conjunto de expansión de internet conexión a nodos perimetrales. Esta red perimetral ofrece la mejor proximidad y rendimiento para conexiones procedentes a través de internet.

- Cuando se plantee con Office 365 para cualquiera de los servicios incluidos como Skype para capacidades de vídeo o convocatorias de reunión en línea de negocio de voz, los clientes deben completar una evaluación de la red de extremo a extremo y cumplir los requisitos de uso de nuestro Skype Operations Framework. Estos clientes dispone de varias opciones para satisfacer los requisitos específicos para la conectividad de la nube, incluyendo ExpressRoute.

Eche un vistazo a estudio de caso de Microsoft [optimizar el rendimiento de red para Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Si va a evaluar Office 365 y no está seguro de que dónde empezar con la evaluación de la red o han encontrado el diseño de la red desafíos que necesita ayuda para superar, trabajar con su equipo de cuentas de Microsoft.
  
Además, lea [Principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples) para comprender los principios de conectividad para administrar de forma segura el tráfico de Office 365 y obtener el mejor rendimiento posible. En este artículo le ayudará a comprender las instrucciones más reciente para optimizar de forma segura conectividad de red de Office 365.
  
Éste es un vínculo corto que puede usar para volver: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Vea también

[Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Uso de comunidades BGP en ExpressRoute para escenarios de Office 365 (versión preliminar)](bgp-communities-in-expressroute.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Direcciones URL e intervalos de direcciones IP de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples)
