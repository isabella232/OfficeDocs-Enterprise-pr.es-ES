---
title: Conectividad de red a Office 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 11/01/2018
audience: ITPro
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
description: Office 365 está diseñado para permitir que los clientes de todo el mundo se conecten al servicio con una conexión a Internet. A medida que el servicio evoluciona, la seguridad, el rendimiento y la confiabilidad de Office 365 se han mejorado en función de los clientes que usan Internet para establecer una conexión con el servicio.
ms.openlocfilehash: 4510cb073c0fde64abc4ee796a55d7ef32662f8c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34069876"
---
# <a name="network-connectivity-to-office-365"></a>Conectividad de red a Office 365

Office 365 está diseñado para permitir que los clientes de todo el mundo se conecten al servicio con una conexión a Internet. A medida que el servicio evoluciona, la seguridad, el rendimiento y la confiabilidad de Office 365 se han mejorado en función de los clientes que usan Internet para establecer una conexión con el servicio.
  
Los clientes que planean usar Office 365 deben evaluar sus necesidades de conectividad de Internet previstas y existentes como parte del proyecto de implementación. En el caso de las implementaciones de clase empresarial, la conectividad a Internet fiable y de tamaño adecuado es una parte fundamental del consumo de características y escenarios de Office 365.
  
Las evaluaciones de red pueden ser realizadas por muchas personas y organizaciones diferentes según su tamaño y sus preferencias. El ámbito de red de la evaluación también puede variar según el lugar en el que se encuentra en el proceso de implementación. Para ayudarle a comprender mejor lo que necesita para realizar una evaluación de la red, hemos creado una guía de evaluación de la red que le ayudará a comprender las opciones disponibles. Esta evaluación determinará qué pasos y recursos se deben agregar al proyecto de implementación para permitirle adoptar correctamente Office 365.
  
Una evaluación completa de la red, como las prescritas en el [marco de operaciones de Skype](https://www.skypeoperationsframework.com/) , proporcionará posibles soluciones a los desafíos de diseño de red junto con los detalles de implementación. La mayoría de las evaluaciones de red indicarán que la conectividad de red con Office 365 se puede acomodar con [pequeños cambios en la configuración o el diseño](https://aka.ms/manageo365endpoints) de la red existente y de la infraestructura de salida de Internet.

Algunas evaluaciones indicarán que la conectividad de red con Office 365 necesitará inversiones adicionales en los componentes de red. Por ejemplo, inversiones en ancho de banda WAN o infraestructura de enrutamiento optimizada para admitir la conectividad de Internet a Office 365. En ocasiones, una evaluación indicará que la conectividad de red con Office 365 se ve afectada por los requisitos de regulación o rendimiento de los escenarios, como la calidad de los [medios de Skype empresarial online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Estos requisitos adicionales pueden dar lugar a inversiones en infraestructura de conectividad a Internet, optimización de enrutamiento y conectividad directa especializada.
  
> [!NOTE]
> Se requiere la autorización de Microsoft para usar ExpressRoute para Office 365. Microsoft revisa todas las solicitudes de los clientes y solo autoriza el uso de ExpressRoute para Office 365 cuando un requisito normativo del cliente exige la conectividad directa. Si tiene estos requisitos, proporcione el fragmento de texto y el vínculo Web al Reglamento que interpreta que significa que se requiere conectividad directa en el formulario de [solicitud de ExpressRoute para Office 365](https://aka.ms/O365ERReview) para comenzar una revisión de Microsoft. Las suscripciones no autorizadas que intenten crear filtros de ruta para Office 365 recibirán un [mensaje de error](https://support.microsoft.com/kb/3181709).
  
Puntos clave que se deben tener en cuenta al planear la evaluación de red de Office 365:
  
- Office 365 es un servicio seguro, confiable y de alto rendimiento que se ejecuta a través de Internet público. Seguimos invirtiendo para mejorar estos aspectos del servicio. Todos los servicios de Office 365 están disponibles a través de la conectividad de Internet.

- Estamos optimizando continuamente los aspectos básicos de Office 365 como la disponibilidad, el alcance global y el rendimiento de la conectividad basada en Internet. Por ejemplo, muchos servicios de Office 365 aprovechan un conjunto expandido de nodos perimetrales con conexión a Internet. Esta red perimetral ofrece la mejor proximidad y el máximo rendimiento a las conexiones que llegan a través de Internet.

- Al considerar el uso de Office 365 para cualquiera de los servicios incluidos como voz, vídeo o capacidades de reunión de Skype empresarial online, los clientes deben completar una evaluación de la red de un extremo a otro y cumplir con los requisitos mediante nuestro marco de operaciones de Skype. Estos clientes tendrán varias opciones para cumplir requisitos específicos para la conectividad en la nube, incluido ExpressRoute.

Eche un vistazo al estudio de caso de Microsoft [sobre la optimización del rendimiento de red para Microsoft Office 365](https://msdn.microsoft.com/en-us/library/mt450488.aspx). Si está evaluando Office 365 y no está seguro de dónde comenzar con la evaluación de la red o ha encontrado desafíos de diseño de red que necesita para solucionar problemas, trabaje con su equipo de la cuenta de Microsoft.
  
Además, lea los [principios de conectividad de red de office 365](https://aka.ms/o365networkingprinciples) para comprender los principios de conectividad para administrar de forma segura el tráfico de Office 365 y obtener el mejor rendimiento posible. Este artículo le ayudará a comprender las instrucciones más recientes para optimizar de manera segura la conectividad de red de Office 365.
  
Este es un vínculo breve que puede usar para volver: [ https://aka.ms/o365networkconnectivity.](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Vea también

[Administrar puntos de conexión de Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)
  
[Preguntas frecuentes sobre extremos de Office 365](https://support.office.com/article/d4088321-1c89-4b96-9c99-54c75cae2e6d)
  
[Red de Office 365 y ajuste de rendimiento](network-planning-and-performance.md)
  
[Azure ExpressRoute para Office 365](azure-expressroute.md)
  
[Enrutamiento con ExpressRoute para Office 365](routing-with-expressroute.md)
  
[Planeamiento de red con ExpressRoute para Office 365](network-planning-with-expressroute.md)
  
[Uso de las comunidades BGP en ExpressRoute para los escenarios de Office 365 (versión preliminar)](bgp-communities-in-expressroute.md)
  
[Calidad de medios y rendimiento de conectividad de red en Skype Empresarial Online](https://support.office.com/article/5fe3e01b-34cf-44e0-b897-b0b2a83f0917)
  
[Intervalos de direcciones IP y URL de Office 365](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2)
  
[Principios de conectividad de red de Office 365](https://aka.ms/o365networkingprinciples)
