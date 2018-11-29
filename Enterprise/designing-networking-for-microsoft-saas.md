---
title: Diseño de redes para SaaS de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/28/2018
ms.audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 4194020a-3847-4259-9f2d-5c556a4510f9
description: 'Resumen: Aprenda a optimizar la red para tener acceso a los servicios de SaaS de Microsoft, como Office 365, Microsoft Intune y Dynamics 365.'
ms.openlocfilehash: 3d47c53de1bc1121ef72eb519c51c0ad9423fff9
ms.sourcegitcommit: 25a022f4ef4e56c5407e8e3a8a34265f8fc94264
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/29/2018
ms.locfileid: "26872271"
---
# <a name="designing-networking-for-microsoft-saas"></a>Diseño de redes para SaaS de Microsoft

 **Resumen:** Aprenda a optimizar la red para tener acceso a los servicios de SaaS de Microsoft, como Office 365, Microsoft Intune y Dynamics 365.
  
Optimización de la red para los servicios de Microsoft SaaS requiere la configuración de interno y dispositivos de extremo para enrutar las diferentes categorías de tráfico a los servicios de Microsoft SaaS.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Pasos para preparar la red para los servicios SaaS de Microsoft

Siga estos pasos para optimizar la red para los servicios SaaS de Microsoft:
  
1. Vea la sección **Pasos para preparar la red para Servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Agregar una conexión a Internet a cada uno de sus oficinas.
    
3. Asegúrese de que el ISP para todas las conexiones de Internet utilicen un servidor DNS con una dirección IP local.
    
4. Examine su hairpins de red, los destinos intermedios, como los servicios de seguridad basados en la nube y eliminarlos si es posible.
    
5. Configurar los dispositivos de borde para el desvío de procesamiento para optimizar y permitir que las categorías de tráfico de Microsoft SaaS.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Optimizar el tráfico de los servicios de Microsoft SaaS    

Existen tres categorías de Microsoft SaaS tráfico:

- Optimizar

  Necesario para la conectividad con cada servicio de Microsoft SaaS y representan más del 75% del ancho de banda de Microsoft SaaS, conexiones y volumen de datos.

- Permitir

  Necesarios para la conectividad con específicos Microsoft SaaS de servicios y sobre las características de pero no son tan confidenciales a rendimiento de la red y la latencia como los de la categoría de optimizar.

- Predeterminada

  Representan los servicios de Microsoft SaaS y dependencias que no requieren ninguna optimización. Puede tratar el tráfico de categoría predeterminada al igual que el tráfico normal de Internet.


**En la figura 1: Configuración recomendada para el tráfico de Microsoft SaaS para todas las oficinas**

![En la figura 1: Configuración recomendada para el tráfico de Microsoft SaaS para todas las oficinas](media/Network-Poster/SaaS1.png)

La figura 1 muestra la configuración recomendada de todas las oficinas, incluidas las sucursales y unos regionales o centrales, en la que:

- Categoría **predeterminada** y general se enruta el tráfico de Internet para las oficinas que tienen servidores proxy y otros dispositivos de borde para proporcionar protección frente a los riesgos de seguridad basados en Internet.
- **Optimizar** y **Permitir** el tráfico de categoría se reenvía directamente hasta el borde de front-end de red de Microsoft de más cercana a la oficina que contiene el usuario que se conecta, pasando por alto los servidores proxy y otros dispositivos de extremo.

Dispositivos de definidas por el software de área extensa (WAN SD) de red en las sucursales separan el tráfico de modo que: 

- Categoría **predeterminada** y general el tráfico de Internet va a una oficina central o regional a través de la red troncal de WAN. 
- **Optimizar** y **Permitir** el tráfico de categoría que se va al ISP que proporciona la conexión a Internet local.
  
Para obtener más información, vea:
  
- [Principios de conectividad de red](https://aka.ms/expressrouteoffice365)

- [Planeación de la migración y red para Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Paso siguiente

[Diseño de redes para PaaS de Microsoft Azure](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Ver también

[Microsoft Cloud Networking para arquitectos profesionales](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

