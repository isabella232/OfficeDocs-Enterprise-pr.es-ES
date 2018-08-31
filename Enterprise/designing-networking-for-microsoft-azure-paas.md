---
title: Diseño de redes para PaaS de Microsoft Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 19568184-705b-493b-b713-b484367adba9
description: 'Resumen: aprenda a optimizar la red para obtener acceso a PaaS de Microsoft Azure.'
ms.openlocfilehash: d20bb5adb46592363926a2926752ed345823c26e
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915115"
---
# <a name="designing-networking-for-microsoft-azure-paas"></a>Diseño de redes para PaaS de Microsoft Azure

 **Resumen:** aprenda a optimizar la red para obtener acceso a PaaS de Microsoft Azure.
  
La optimización de las redes para aplicaciones PaaS de Azure requiere un ancho de banda de Internet adecuado y puede exigir la distribución del tráfico de red por varios sitios o aplicaciones.
  
## <a name="planning-steps-for-hosting-organization-paas-applications-in-azure"></a>Pasos de planeamiento para hospedar aplicaciones PaaS de una organización en Azure

1. Vea la sección **Pasos para preparar la red para los servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Para optimizar el ancho de banda de Internet, siga los pasos 2 a 4 de la sección **Pasos para preparar la red para los servicios SaaS de Microsoft** del artículo [Diseño de redes para SaaS de Microsoft](designing-networking-for-microsoft-saas.md).
    
3. Determine si necesita una conexión de ExpressRoute a Azure.
    
4. En el caso de las cargas de trabajo basadas en web, determinar si necesita la Puerta de enlace de aplicaciones de Azure.
    
5. En el caso de la distribución de tráfico a distintos puntos de conexión en diferentes centros de datos, decidir si necesita Administrador de tráfico de Azure.
    
## <a name="internet-bandwidth-for-organization-paas-applications"></a>Ancho de banda de Internet para las aplicaciones PaaS de la organización

Las aplicaciones de la organización hospedadas en PaaS de Azure requieren ancho de banda de Internet para los usuarios de la intranet. Hay dos opciones:
  
- **Opción 1:** Use la canalización existente optimizada para el tráfico de Internet con la capacidad para controlar las cargas máximas. Consulte[Diseño de redes para SaaS de Microsoft](designing-networking-for-microsoft-saas.md) para informarse sobre el perímetro de Internet, el uso de clientes y las consideraciones sobre las operaciones de TI.
    
- **Opción 2:** Para las necesidades de ancho de banda de alto o de baja latencia, use una conexión de ExpressRoute a Azure.
    
**Figura 1: Opciones de conexión para conectarse a los servicios PaaS de Azure**

![Figura 1: Opciones de conexión de los servicios PaaS de Azure](media/Network-Poster/PaaS1.png)
  
La figura 1 muestra una red local que se conecta a los servicios PaaS de Azure a través de una canalización de Internet o ExpressRoute.
  
## <a name="azure-application-gateway"></a>Puerta de enlace de aplicación de Azure

Enrutamiento de nivel de aplicación y servicios de equilibrio de carga que permiten compilar un front-end web escalable y altamente disponible en Azure para las aplicaciones web, los servicios en la nube y las máquinas virtuales. 
  
**Figura 2: Puerta de enlace de aplicaciones de Azure**

![Figura 2: Servicio de puerta de enlace de aplicaciones de Azure](media/Network-Poster/PaaS2.png)
  
La figura 2 muestra la Puerta de enlace de aplicaciones de Azure y cómo las solicitudes de usuario que proceden de Internet pueden enrutarse hacia las aplicaciones web de Azure, los servicios en la nube o las máquinas virtuales.
  
Actualmente, la Puerta de enlace de aplicaciones admite la entrega de aplicaciones de capa 7 para lo siguiente:
  
- Equilibrio de carga HTTP
    
- Afinidad de sesión basada en cookies
    
- Descarga SSL
    
Para obtener más información, consulte [Application Gateway](https://docs.microsoft.com/azure/application-gateway/application-gateway-introduction).
  
## <a name="azure-traffic-manager"></a>Administrador de tráfico de Azure

Distribución de tráfico a distintos puntos de conexión, que pueden incluir servicios en la nube o aplicaciones web de Azure ubicadas en diferentes centros de datos o puntos de conexión externos.
  
Administrador de tráfico usa los siguientes métodos de enrutamiento:
  
- **Conmutación por error:** los puntos de conexión están en los mismos centros de datos Azure o en otros distintos y queremos usar un punto de conexión principal para todo el tráfico, pero también proporcionar copias de seguridad en caso de que los puntos de conexión principales o de copia de seguridad no estén disponibles.
    
- **Round robin:** quiere distribuir la carga en un conjunto de puntos de conexión en el mismo centro de datos o en centros de datos distintos.
    
- **Rendimiento:** tenemos puntos de conexión en distintas ubicaciones geográficas y queremos que los clientes solicitantes usen el punto de conexión "más próximo", es decir, el de menor latencia.
    
Este es un ejemplo de tres aplicaciones web distribuidas geográficamente.
  
**Figura 3: Administrador de tráfico de Azure**

![Figura 3: Administrador de tráfico de Azure](media/Network-Poster/PaaS3.png)
  
La figura 3 muestra el proceso básico que el Administrador de tráfico usa para enrutar las solicitudes hacia tres aplicaciones web de Azure diferentes en Estados Unidos, Europa y Asia. En el ejemplo:
  
1. Una consulta de DNS de usuario para solicitar la dirección URL de un sitio web se dirige al Administrador de tráfico de Azure, que, a su vez, devuelve el nombre de una aplicación web regional basándose en el método de enrutamiento del rendimiento.
    
2. El usuario inicia el tráfico con la aplicación web regional en Europa.
    
Para obtener más información, vea [Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview).

## <a name="next-step"></a>Paso siguiente

[Diseño de redes para IaaS de Microsoft Azure](designing-networking-for-microsoft-azure-iaas.md)
 
## <a name="see-also"></a>Ver también

[Microsoft Cloud Networking para arquitectos profesionales](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)



