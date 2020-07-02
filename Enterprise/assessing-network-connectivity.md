---
title: Evaluar la conectividad de red de Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: laurawi
ms.date: 6/23/2020
audience: ITPro
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 64b420ef-0218-48f6-8a34-74bb27633b10
description: Microsoft 365 está diseñado para permitir que los clientes de todo el mundo se conecten al servicio con una conexión a Internet. A medida que el servicio evoluciona, la seguridad, el rendimiento y la confiabilidad de Microsoft 365 se han mejorado en función de los clientes que usan Internet para establecer una conexión con el servicio.
ms.openlocfilehash: 0ccf729dc8eddfd99ffc0b70c8ab56e31451be88
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997964"
---
# <a name="assessing-microsoft-365-network-connectivity"></a>Evaluar la conectividad de red de Microsoft 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Microsoft 365 está diseñado para permitir que los clientes de todo el mundo se conecten al servicio con una conexión a Internet. A medida que el servicio evoluciona, la seguridad, el rendimiento y la confiabilidad de Microsoft 365 se han mejorado en función de los clientes que usan Internet para establecer una conexión con el servicio.
  
Los clientes que planean usar Microsoft 365 deben evaluar sus necesidades de conectividad de Internet previstas y existentes como parte del proyecto de implementación. Para las implementaciones de clase empresarial, la conectividad de Internet fiable y con un tamaño adecuado es una parte fundamental del consumo de características y escenarios de Microsoft 365.
  
Las evaluaciones de red pueden ser realizadas por muchas personas y organizaciones diferentes según su tamaño y sus preferencias. El ámbito de red de la evaluación también puede variar según el lugar en el que se encuentra en el proceso de implementación. Para ayudarle a comprender mejor lo que necesita para realizar una evaluación de la red, hemos creado una guía de evaluación de la red que le ayudará a comprender las opciones disponibles. Esta evaluación determinará qué pasos y recursos se deben agregar al proyecto de implementación para permitirle adoptar correctamente Microsoft 365.
  
Una evaluación completa de la red proporcionará posibles soluciones a los desafíos de diseño de red junto con los detalles de implementación. Algunas evaluaciones de red mostrarán que la conectividad de red óptima con Microsoft 365 se puede acomodar con pequeños cambios en la configuración o el diseño de la red existente y de la infraestructura de salida de Internet.

Algunas evaluaciones indicarán que la conectividad de red con Microsoft 365 necesitará inversiones adicionales en los componentes de red. Por ejemplo, las redes empresariales que abarcan sucursales y varias regiones geográficas pueden requerir inversiones en soluciones SD-WAN o una infraestructura de enrutamiento optimizada para admitir la conectividad de Internet con Microsoft 365. En ocasiones, una evaluación indicará que la conectividad de red con Microsoft 365 se ve afectada por los requisitos de regulación o rendimiento de los escenarios, como la calidad de los [medios de Skype empresarial online](https://support.office.com/article/Media-Quality-and-Network-Connectivity-Performance-in-Skype-for-Business-Online-5fe3e01b-34cf-44e0-b897-b0b2a83f0917). Estos requisitos adicionales pueden dar lugar a inversiones en infraestructura de conectividad a Internet, optimización de enrutamiento y conectividad directa especializada.

Algunos recursos para ayudarle a evaluar su red:

- Consulte [microsoft 365 Network Connectivity Overview](office-365-networking-overview.md) para obtener información conceptual sobre las redes de Microsoft 365.
- Consulte los [principios de conectividad de red de microsoft 365](https://aka.ms/o365networkingprinciples) para comprender los principios de conectividad para administrar de forma segura el tráfico de Microsoft 365 y obtener el mejor rendimiento posible.
- Regístrese en [Microsoft FastTrack](https://www.microsoft.com/fasttrack) para obtener asistencia guiada con la planeación, el diseño y la implementación de Microsoft 365. 
- Consulte la siguiente sección de [prueba de conectividad de 365](assessing-network-connectivity.md#the-microsoft-365-connectivity-test) para ejecutar pruebas de conectividad básicas que proporcionan una guía específica sobre las mejoras de conectividad de red que se pueden realizar entre una ubicación de usuario determinada y la 365 de Microsoft.

> [!NOTE]
> Se requiere la autorización de Microsoft para usar ExpressRoute para Office 365. Microsoft revisa todas las solicitudes de los clientes y solo autoriza el uso de ExpressRoute para Office 365 cuando un requisito normativo del cliente exige la conectividad directa. Si tiene estos requisitos, proporcione el fragmento de texto y el vínculo Web al Reglamento que interpreta que significa que se requiere conectividad directa en el formulario de [solicitud de ExpressRoute para Office 365](https://aka.ms/O365ERReview) para comenzar una revisión de Microsoft. Las suscripciones no autorizadas que intenten crear filtros de ruta para Office 365 recibirán un [mensaje de error](https://support.microsoft.com/kb/3181709).
  
Puntos clave que se deben tener en cuenta al planear la evaluación de red para Microsoft 365:
  
- Microsoft 365 es un servicio seguro, confiable y de alto rendimiento que se ejecuta a través de Internet público. Seguimos invirtiendo para mejorar estos aspectos del servicio. Todos los servicios de Microsoft 365 están disponibles a través de la conectividad de Internet.

- Estamos optimizando continuamente los aspectos básicos de Microsoft 365, como la disponibilidad, el alcance global y el rendimiento de la conectividad basada en Internet. Por ejemplo, muchos servicios de Microsoft 365 aprovechan un conjunto en expansión de nodos perimetrales con conexión a Internet. Esta red perimetral ofrece la mejor proximidad y el máximo rendimiento a las conexiones que llegan a través de Internet.

- Al considerar el uso de Microsoft 365 para cualquiera de los servicios incluidos, como Microsoft Teams o Skype for Business online Voice, video o las capacidades de reunión, los clientes deben completar una evaluación de la red de un extremo a otro y cumplir con los requisitos de conectividad mediante [Microsoft FastTrack](https://www.microsoft.com/fasttrack).

Si está evaluando Microsoft 365 y no está seguro de dónde comenzar con la evaluación de la red o ha encontrado desafíos de diseño de red que necesita para solucionar problemas, trabaje con su equipo de cuentas de Microsoft.

## <a name="the-microsoft-365-connectivity-test"></a>Prueba de conectividad de Microsoft 365

La [prueba de conectividad de microsoft 365](https://aka.ms/netonboard) es una herramienta de evaluación de la red de prueba de concepto (POC) que ejecuta pruebas de conectividad básicas en su espacio empresarial de Microsoft 365 y recomendaciones específicas de diseño de red para obtener un rendimiento óptimo de Microsoft 365. La herramienta resalta las opciones comunes de diseño de perímetro de red empresarial de gran tamaño que resultan útiles para la exploración Web de Internet, pero afectan el rendimiento de aplicaciones SaaS grandes como Microsoft 365.

La herramienta de incorporación de la red hace lo siguiente:

- Detecta su ubicación o puede especificar una ubicación para probarla
- Comprueba la ubicación de salida de la red.
- Prueba la ruta de red a la puerta delantera más cercana del servicio 365 de Microsoft
- Proporciona pruebas avanzadas usando una aplicación de Windows 10 descargable que hace recomendaciones de diseño de red perimetral relacionadas con servidores proxy, firewalls y DNS. La herramienta también ejecuta pruebas de rendimiento para Skype empresarial online, Microsoft Teams, SharePoint Online y Exchange Online.

La herramienta tiene dos componentes: una interfaz de usuario basada en el explorador que recopila información de conectividad básica y una aplicación descargable de Windows 10 que ejecuta pruebas avanzadas y devuelve datos de evaluación adicionales.

La herramienta basada en el explorador muestra la siguiente información:

- Ficha resultados e impacto
  - La ubicación en un mapa de la puerta de servicio en uso
  - La ubicación en un mapa de otras puertas de servicio que proporcionarían una conectividad óptima
  - Rendimiento relativo comparado con otros clientes de Microsoft 365 cerca de usted
- Pestaña detalles y soluciones
  - Ubicación del usuario por ciudad y país
  - Ubicación de salida de red por ciudad, estado y país
  - Distancia de salida de usuario a red
  - Microsoft 365 Exchange Online servicio ubicación de la puerta de delante
  - El servicio de Microsoft 365 Exchange Online es una puerta frontal (s) para la ubicación del usuario
  - Clientes de su área metropolitana con mejor rendimiento

La aplicación descargable de pruebas avanzadas proporciona la siguiente información adicional:

- Ficha detalles y soluciones (anexadas)
  - Puerta de enlace predeterminada del usuario
  - Servidor DNS de cliente
  - Resolución de nombres recursivos de DNS de cliente
  - Servidor DNS de Exchange Online
  - Servidor DNS de SharePoint Online
  - Identificación del servidor proxy
  - Comprobación de conectividad de medios
  - Pérdida de paquetes de calidad de medios
  - Latencia de calidad de medios
  - Vibración de calidad de medios
  - Reordenación de paquetes de calidad de medios
- Pruebas de conectividad a varios extremos específicos de características
- Diagnósticos de rutas de red que incluyen datos tracert y de latencia para los servicios de Exchange Online, SharePoint Online y Teams

Puede obtener información acerca de la prueba de conectividad de Microsoft 365 y enviar comentarios en el [POC de prueba de conectividad de microsoft 365 actualizado con nueva entrada de blog de recomendaciones de diseño de red](https://techcommunity.microsoft.com/t5/Office-365-Networking/Updated-Office-365-Network-Onboarding-Tool-POC-with-new-network/m-p/711130#M130) . Se publicará información sobre futuras actualizaciones de esta herramienta y otras actualizaciones de red de Microsoft 365 en el blog de [red de Office 365](https://techcommunity.microsoft.com/t5/Office-365-Networking/bd-p/Office365Networking) .
  
Este es un vínculo breve que puede usar para volver: [ https://aka.ms/o365networkconnectivity .](https://aka.ms/o365networkconnectivity)
  
## <a name="see-also"></a>Ver también

[Introducción a la conectividad de red 365 de Microsoft](office-365-networking-overview.md)

[Principios de conectividad de red de Microsoft 365](https://aka.ms/o365networkingprinciples)

[Administrar puntos de conexión de Office 365](managing-office-365-endpoints.md)

[Direcciones URL e intervalos de direcciones IP de Office 365](urls-and-ip-address-ranges.md)

[Dirección IP de Office 365 y servicio web de URL](office-365-ip-web-service.md)

[Ajuste del rendimiento y de la red 365 de Microsoft](network-planning-and-performance.md)

[Información general de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
