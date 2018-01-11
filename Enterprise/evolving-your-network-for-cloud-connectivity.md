---
title: Desarrollo de la red para la conectividad en la nube
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 83e2859a-c673-47c4-880a-01cdfdadb93e
description: "Resumen: Le explicamos por qué la adopción de la nube requiere un nuevo enfoque de las inversiones en infraestructura de red."
ms.openlocfilehash: 18b4e5e10094a43f0d2b10cd0f01684f2352a0a8
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="evolving-your-network-for-cloud-connectivity"></a>Desarrollo de la red para la conectividad en la nube

 **Resumen:** Le explicamos por qué la adopción de la nube requiere un nuevo enfoque de las inversiones en infraestructura de red.
  
La migración a nube cambia el volumen y el carácter de los flujos de tráfico dentro y fuera de una red corporativa. También afecta a los métodos para mitigar los riesgos de seguridad.
  
- Antes de la llegada de la nube
    
    La mayoría de las inversiones en infraestructura de red se realizaban para garantizar la disponibilidad, la fiabilidad y el rendimiento de la conectividad a los centros de datos locales. Para muchas organizaciones, la conectividad a Internet no era crítica para las operaciones empresariales internas. Los límites de la red eran las principales defensas contra las infracciones de seguridad.
    
- Después de la llegada de la nube
    
    Con la productividad migrada y las nuevas cargas de trabajo de TI que se ejecutan en la nube, las inversiones en infraestructura se han trasladado de los centros de datos locales a la conectividad a Internet, que ahora es crítica para las operaciones empresariales internas. La conectividad federada traslada la estrategia de seguridad hacia la protección de las identidades y los datos que se transmiten a través de la red y los puntos de conectividad a los servicios en la nube de Microsoft.
    
Las inversiones en la infraestructura de red comienzan con la conectividad. Las inversiones adicionales dependen de la categoría del servicio en la nube.
  
- **Software como servicio (SaaS)**: los servicios SaaS de Microsoft incluyen Office 365, Intune Microsoft y Microsoft Dynamics 365. Una adopción satisfactoria de los servicios SaaS por parte de los usuarios depende de una conectividad a Internet (o directamente a los servicios en la nube de Microsoft) de alto rendimiento y disponibilidad.
    
    La arquitectura de la red se centra en un ancho de banda amplio y en una conectividad redundante y fiable. Las inversiones constantes incluyen la supervisión y el ajuste del rendimiento.
    
- **Plataforma de Azure como servicio (PaaS)**: además de las inversiones en servicios SaaS de Microsoft, las aplicaciones PaaS ubicadas en varios sitios o distribuidas geográficamente podrían requerir la gestión del Administrador de tráfico de Microsoft Azure para distribuir el tráfico de cliente. Las inversiones constantes incluyen pruebas de conmutación por error, supervisión y distribución del tráfico y el rendimiento.
    
- **Infraestructura de Azure como servicio (IaaS)**: además de las inversiones en los servicios SaaS y PaaS de Microsoft, ejecutar cargas de trabajo de TI en IaaS requiere diseñar y configurar redes virtuales de Azure que hospeden máquinas virtuales, una conectividad segura a las aplicaciones que se ejecutan en ellas, el enrutamiento, el direccionamiento IP, DNS y un equilibrio de carga. Las inversiones constantes incluyen la supervisión y la solución de problemas de rendimiento y seguridad.
    
## <a name="areas-of-networking-investment-for-success-in-the-cloud"></a>Áreas de inversión en redes para lograr el éxito en la nube

Las organizaciones empresariales se benefician de seguir un enfoque metódico para optimizar el rendimiento de la red en la intranet y a Internet. También se puede beneficiar de una conexión de ExpressRoute.
  
### <a name="optimize-intranet-connectivity-to-your-edge-network"></a>Optimizar la conectividad de la intranet a la red perimetral

Con el paso de los años, muchas organizaciones han optimizado la conectividad a la intranet y el rendimiento de la aplicaciones que se ejecutan en centros de datos locales. Con la productividad y las cargas de trabajo de TI que se ejecutan en la nube de Microsoft, la inversión adicional debe garantizar una disponibilidad de gran conectividad y que el rendimiento del tráfico entre la red perimetral y los usuarios de la intranet sea óptimo.
  
### <a name="optimize-throughput-at-your-edge-network"></a>Optimizar el rendimiento en la red perimetral

A medida que aumenta el tráfico de productividad que viaja a la nube a diario, debemos examinar exhaustivamente el conjunto de sistemas que hay en la red perimetral para garantizar que están actualizados, proporcionen una alta disponibilidad y tengan capacidad suficiente para satisfacer las cargas máximas.
  
### <a name="for-a-high-sla-to-azure-office-365-and-dynamics-365-use-expressroute"></a>Para un SLA elevado a Azure, Office 365 y Dynamics 365, use ExpressRoute.

Aunque puede usar la conexión a Internet actual de la red perimetral, el tráfico que entra y sale de los servicios en la nube de Microsoft debe compartir la canalización con otro tráfico de la intranet que se dirige a Internet. Además, el tráfico a los servicios en la nube de Microsoft varía según la congestión del tráfico de Internet.
  
Para lograr un SLA elevado y el mejor rendimiento, use ExpressRoute, una conexión WAN dedicada entre su red y Azure, Office 365, Dynamics 365 o los tres. 
  
ExpressRoute pueden aprovechar el proveedor de red existente para establecer una conexión dedicada. Los recursos que conecta ExpressRoute aparecen como si estuvieran en la WAN, incluso en las organizaciones distribuidas geográficamente.
  
Para obtener más información, consulte [ExpressRoute para la conectividad en la nube de Microsoft](expressroute-for-microsoft-cloud-connectivity.md).
  
## <a name="scope-of-network-investments"></a>Ámbito de las inversiones en la red

El ámbito de las inversiones en la red dependen de la categoría del servicio en la nube. Invertir en la nube de Microsoft maximiza las inversiones de los equipos de redes. Por ejemplo, las inversiones de los servicios IaaS sirven para todas las áreas de inversión.
  
|||||
|:-----|:-----|:-----|:-----|
|Área de inversión  <br/> |SaaS  <br/> |PaaS  <br/> |IaaS  <br/> |
|Crear una arquitectura de conectividad a Internet redundante, fiable y con un ancho de banda amplio  <br/> |Aplicable  <br/> |Aplicable  <br/> |Aplicable  <br/> |
|Supervisar y ajustar la capacidad de proceso de Internet en relación con el rendimiento  <br/> |Aplicable  <br/> |Aplicable  <br/> |Aplicable  <br/> |
|Solucionar problemas de conectividad a Internet y de capacidad de proceso  <br/> |Aplicable  <br/> |Aplicable  <br/> |Aplicable  <br/> |
|Diseñar Administrador de tráfico de Azure para que equilibre la carga del tráfico que se dirige a distintos puntos de conexión  <br/> ||Aplicable  <br/> |Aplicable  <br/> |
|Crear una arquitectura de conectividad a las redes virtuales de Azure redundante, fiable y con un buen rendimiento  <br/> |||Aplicable  <br/> |
|Diseñar una conectividad segura a las máquinas virtuales de Azure  <br/> |||Aplicable  <br/> |
|Diseñar e implementar el enrutamiento entre ubicaciones locales y redes virtuales  <br/> |||Aplicable  <br/> |
|Diseñar e implementar el equilibrio de carga para cargas de trabajo de TI internas y orientadas a Internet  <br/> |||Aplicable  <br/> |
|Solucionar problemas de conectividad a máquinas virtuales y de capacidad de proceso  <br/> |||Aplicable  <br/> |
   
## <a name="see-also"></a>Vea también

[Microsoft Cloud Networking para arquitectos profesionales](microsoft-cloud-networking-for-enterprise-architects.md)
  
[ExpressRoute para la conectividad en la nube de Microsoft](expressroute-for-microsoft-cloud-connectivity.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI]((https://sway.com/FJ2xsyWtkJc2taRD))



