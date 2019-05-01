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
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487306"
---
# <a name="designing-networking-for-microsoft-saas"></a>Diseño de redes para SaaS de Microsoft

 **Resumen:** Aprenda a optimizar la red para tener acceso a los servicios de SaaS de Microsoft, como Office 365, Microsoft Intune y Dynamics 365.
  
La optimización de la red para los servicios SaaS de Microsoft requiere la configuración de dispositivos perimetrales e internos para dirigir las diferentes categorías de tráfico a los servicios SaaS de Microsoft.
  
## <a name="steps-to-prepare-your-network-for-microsoft-saas-services"></a>Pasos para preparar la red para los servicios SaaS de Microsoft

Siga estos pasos para optimizar la red para los servicios SaaS de Microsoft:
  
1. Vea la sección **Pasos para preparar la red para Servicios en la nube de Microsoft** en [Elementos comunes de conectividad de Microsoft Cloud](common-elements-of-microsoft-cloud-connectivity.md).
    
2. Agregue una conexión a Internet a cada una de las oficinas.
    
3. Asegúrese de que los ISP de todas las conexiones a Internet usen un servidor DNS con una dirección IP local.
    
4. Examine el las redirecciones de red, los destinos intermedios como los servicios de seguridad basados en la nube y elimínelos si es posible.
    
5. Configure los dispositivos perimetrales para omitir el procesamiento de las categorías optimizar y permitir del tráfico SaaS de Microsoft.

## <a name="optimizing-traffic-to-microsofts-saas-services"></a>Optimización del tráfico a los servicios SaaS de Microsoft    

Hay tres categorías de tráfico SaaS de Microsoft:

- Optimizar

  Necesario para la conectividad con todos los servicios SaaS de Microsoft y representan el 75% del ancho de banda, las conexiones y el volumen de datos de SaaS de Microsoft.

- Permitir

  Necesario para la conectividad a características y servicios específicos de SaaS de Microsoft, pero no tan sensibles al rendimiento y la latencia de la red como los de la categoría optimizar.

- Valor predeterminado

  Representa los servicios SaaS de Microsoft y las dependencias que no requieren optimización. Puede tratar el tráfico de categorías predeterminado, por ejemplo, el tráfico normal de Internet.


**Figura 1: configuración recomendada para el tráfico SaaS de Microsoft para todas las oficinas**

![Figura 1: configuración recomendada para el tráfico SaaS de Microsoft para todas las oficinas](media/Network-Poster/SaaS1.png)

En la figura 1 se muestra la configuración recomendada de todas las oficinas, incluidas las sucursales y las regionales o las centrales, en las que:

- La categoría **predeterminada** y el tráfico general de Internet se enrutan a las oficinas que tienen servidores proxy y otros dispositivos perimetrales para proporcionar protección frente a los riesgos de seguridad basados en Internet.
- **Optimizar** y **permitir** el tráfico de categorías se reenvía directamente al perímetro del front-end de la red de Microsoft más cercano a la oficina que contiene el usuario que realiza la conexión, omitiendo los servidores proxy y otros dispositivos perimetrales.

Los dispositivos de red de área extensa (SD-WAN) definidos por software en las sucursales separan el tráfico para que: 

- La categoría **predeterminada** y el tráfico general de Internet van a una oficina central o regional a través de la red troncal WAN. 
- **Optimizar** y **permitir** el tráfico de categoría va al ISP que proporciona la conexión local a Internet.
  
Para obtener más información, vea:
  
- [Principios de conectividad de red](https://aka.ms/expressrouteoffice365)

- [Planeación de la migración y red para Office 365](https://aka.ms/tune)
    
## <a name="next-step"></a>Paso siguiente

[Diseño de redes para PaaS de Microsoft Azure](designing-networking-for-microsoft-azure-paas.md)
    
## <a name="see-also"></a>Ver también

[Microsoft Cloud Networking para arquitectos profesionales](microsoft-cloud-networking-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

