---
title: Redes para Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 014b3710-e6e9-485c-8550-975d510eb2fc
description: 'Resumen: Conozca la infraestructura de red de Contoso y cómo puede usar ExpressRoute para acceso optimizada para las ofertas de nube de Microsoft.'
ms.openlocfilehash: 89d4182d8a5ef44f936977ec51cc002b51f4b379
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915225"
---
# <a name="networking-for-the-contoso-corporation"></a>Redes para Contoso Corporation

 **Resumen:** Comprender la infraestructura de red de Contoso y cómo puede usar ExpressRoute para acceso optimizada para las ofertas de nube de Microsoft.
  
Para adoptar una infraestructura de nube inclusive, los ingenieros de red de Contoso obtienen el cambio fundamental en el modo en que el tráfico de red a los viajes de servicios basados en la nube. En lugar de optimizar únicamente el tráfico a los servidores locales y centros de datos, se debe prestar atención igual a la optimización de tráfico hasta el borde de Internet y a través de Internet.
  
## <a name="contosos-networking-infrastructure"></a>Infraestructura de red de Contoso

Contoso tiene la infraestructura de red que se muestra en la figura 1.
  
**Figura 1: Infraestructura WAN de Contoso**

![Infraestructura WAN de Contoso que vincula la sede central, los centros regionales y las oficinas satélite](media/Contoso-Poster/Contoso-WW-Net.png)
  
La figura 1 muestra las oficinas de Contoso en todo el mundo y el conjunto de vínculos WAN de oficinas regionales y satélite entre ellos.
  
Los elementos adicionales de la red son los siguientes:
  
- Red local
    
    Los vínculos WAN conectan las sedes centrales de París para las oficinas regionales y las oficinas regionales de oficinas satélites en una configuración de concentrador y radio. Dentro de cada oficina, enrutadores entregan el tráfico a los hosts o los puntos de acceso inalámbrico en subredes, que utilizan el espacio de direcciones IP privado.
    
- Conectividad a Internet
    
    Cada oficina tiene su propia conexión a Internet a través de un servidor proxy. Esto normalmente se implementa como una WAN vínculo a un ISP local que también proporciona las direcciones IP públicas para el servidor proxy.
    
- Presencia en Internet
    
    Contoso posee el nombre de dominio público de contoso.com. El sitio web público de Contoso para pedir productos es un conjunto de servidores en un centro de datos conectados a Internet en el campus de París. Contoso usa un /24 intervalo de direcciones IP pública en Internet.
    
## <a name="contosos-app-infrastructure"></a>Infraestructura de aplicación de Contoso

Contoso ha diseñado su infraestructura de servidores y aplicaciones para lo siguiente:




  
**Figura 2: Infraestructura de Contoso para aplicaciones internas**

![Infraestructura de Contoso para aplicaciones internas](media/Contoso-Poster/App-Infra.png)
  
- Las oficinas satélite usan servidores de almacenamiento en caché locales para almacenar documentos y sitios web internos a los que se accede frecuentemente.
    
- 
Los centros regionales usan servidores de aplicaciones para las oficinas regionales y satélite. Estos servidores se sincronizan con los servidores en la sede de París.
    
- Las instalaciones de París tienen los centros de datos que contienen los servidores de aplicaciones centralizados que sirven a toda la organización.
    
Para los usuarios de oficinas de centros regionales o satélite, el 60 % de los recursos que necesitan los empleados pueden obtenerse de los servidores de oficinas de concentradores regionales o satélite. El 40 % adicional de solicitudes de recursos debe realizarse a través del vínculo WAN a las instalaciones de París.
  
## <a name="contosos-network-analysis"></a>Análisis de la red de Contoso

Éstos son los resultados de análisis de Contoso de los cambios necesarios en su red para dar cabida a las diferentes categorías de las ofertas de nube de Microsoft:
  
|**Las ofertas de nube de SaaS: Office 365, EMS y Dynamics 365**|**PaaS Azure: Aplicaciones móviles**|**IaaS Azure: Las cargas de trabajo basadas en servidor**|
|:-----|:-----|:-----|
|Una adopción satisfactoria de los servicios SaaS por parte de los usuarios depende de una conectividad a Internet (o directamente a los servicios en la nube de Microsoft) de alto rendimiento y disponibilidad.
  <br/> En el caso de los usuarios móviles, se supone que disponen de un acceso a Internet adecuado.
  <br/> Para los usuarios de la intranet de Contoso, debe ser analizado y optimizado para el rendimiento a Internet y tiempos de ida y vuelta al centro de datos de Microsoft Europa que hospeda a los inquilinos de Office 365, EMS y Dynamics 365 cada oficina.  <br/> |Para ofrecer mejor soporte a los empleados móviles, las aplicaciones heredadas y algunos sitios de uso compartido de archivos se están remodelando e implementando como aplicaciones PaaS de Azure. Para un rendimiento óptimo, Contoso planea implementar las nuevas aplicaciones desde varios centros de datos de Azure en todo el mundo. Azure Traffic Manager para enviar solicitudes de aplicaciones cliente, provengan de un usuario móvil o de en un equipo en la oficina, al centro de datos de Azure más cercano que hospede la aplicación.  <br/>   

El departamento de TI deberá agregar rendimiento de aplicaciones PaaS y distribución del tráfico a su solución de supervisión del estado de la red. <br/> |Para mover algunos servidores heredados y de archivo fuera de los centros de datos de las instalaciones de París y agregar servidores según sea necesario para el procesamiento de fin de trimestre, Contoso planea usar máquinas virtuales que se ejecutan en servicios de infraestructura de Azure. 

  <br/> Las redes virtuales de Azure que contienen estos servidores deben diseñarse para espacios de direcciones que no se superponen, enrutamiento y DNS integrado.

  <br/> El departamento de TI debe incluir estos nuevos servidores en su sistema de administración y supervisión de la red.  <br/> |
   
## <a name="contosos-use-of-expressroute"></a>Uso de Contoso de ExpressRoute

ExpressRoute es una conexión WAN dedicada desde su ubicación en una ubicación de interconexión de Microsoft que se conecta a la red a la red de la nube de Microsoft. Las conexiones de ExpressRoute proporcionan performance predecible y un tiempo de actividad del 99,9% SLA. .
  
Con una conexión ExpressRoute, están conectados a la red de la nube de Microsoft y todas las ubicaciones de centros de datos de Microsoft en el mismo continente. El tráfico entre la ubicación de interconexión de la nube y el centro de datos de Microsoft de destino se transmite a través de la red de la nube de Microsoft
  
**Figura 3: La red mundial en la nube de Microsoft**

![La red mundial en la nube de Microsoft](media/Contoso-Poster/MS-WW-Cloud.png)
  
La figura 3 muestra la red en la nube de Microsoft interconectada para las distintas regiones del mundo.
  
Con ExpressRoute Premium, puede llegar a cualquier centro de datos de Microsoft de cualquier continente y desde cualquier ubicación de emparejamiento de Microsoft de cualquier continente. El tráfico entre continentes se transmite a través de la red en la nube de Microsoft.
  
Según el análisis de tráfico actual y futuro para las ofertas de nube de Microsoft, Contoso tiene realiza una evaluación de la red y se implementa una conexión ExpressRoute (basadas en MPLS) y a cualquier para tener acceso a recursos de Azure, con interconexión privadas y públicas relaciones de la oficina central de París a la ubicación de interconexión de Microsoft en Europa.
  
Esta conexión le dará de al departamento de TI de Contoso:
  
- Rendimiento coherente para la administración de aplicaciones PaaS de Azure distribuidas
    
    Todos los de los desarrolladores de aplicaciones y la infraestructura central de TI de Contoso administradores están en el campus de París. Con aplicaciones de Azure PaaS distribuidas en diferentes centros de datos de Azure todo el mundo, Contoso necesita rendimiento coherente desde el campus París para administrar las aplicaciones y sus recursos de almacenamiento, que constan de TB de documentos.
    
- Rendimiento constante para la administración de servidores en IaaS de Azure
    
    Los administradores de centros de datos de Contoso están en el campus París y los servidores que se van a ser implementados en Azure son una extensión del centro de datos de París. Contoso necesita performance consistente en estos nuevos servidores para tener acceso a aplicaciones heredadas y almacenamiento de archivos y para el procesamiento de fin de trimestre.
    
## <a name="contosos-path-to-cloud-networking-readiness"></a>Ruta de acceso de Contoso en la nube de preparación de redes

Contoso usa los pasos siguientes para preparar su red para la nube de Microsoft:
  
1. Optimizar los equipos de los empleados para el acceso a Internet

    
    Se comprobarán los equipos individuales para garantizar que la pila de TCP/IP más reciente, el explorador, los controladores NIC y las actualizaciones de seguridad y del sistema operativo estén instalados.
    
2. Analizar el uso de la conexión a Internet en cada oficina y aumentarlo según sea necesario
    
    
Se analizarán todas las oficinas para conocer el uso actual de Internet y el ancho de banda del vínculo WAN aumentará si funciona con un uso del 70 % o superior.
    
3. Analizar los sistemas de red perimetral en todas las oficinas para conseguir un rendimiento óptimo

    
    Se analizarán los firewall, los ID y otros sistemas de la ruta de acceso de Internet para conseguir un rendimiento óptimo. Los servidores proxy se actualizarán según sea necesario.
    
4. Agregar ExpressRoute para las instalaciones de París
    
    Proporciona acceso coherente a los recursos de Azure para la administración de cargas de trabajo Azure PaaS e IaaS.
    
5. Crear y probar un perfil de Azure Traffic Manager para aplicaciones PaaS de Azure
    
    Probar un perfil de Azure Traffic Manager que use el método de enrutamiento del rendimiento para obtener experiencia en la distribución de tráfico de Internet a ubicaciones regionales.
    
6. Reservar espacio de direcciones privadas para redes virtuales de Azure

    
    Según el número de servidores proyectados a corto y largo plazo en IaaS de Azure, reserva el espacio de direcciones privadas para las redes virtuales de Azure y sus subredes.
    
## <a name="see-also"></a>See Also

[Contoso en la nube de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)



