---
title: Arquitectura de escenarios de nube híbrida de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: 'Resumen: Comprenda la arquitectura de las ofertas de nube híbrida de Microsoft.'
ms.openlocfilehash: 8a0c5c37c2e0dfd0c6641128b1cee89c89e16441
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22914925"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Arquitectura de escenarios de nube híbrida de Microsoft

 **Resumen:** Comprenda la arquitectura de las ofertas de nube híbrida de Microsoft.
  
Use un enfoque de arquitectura para planear e implementar escenarios de nube híbrida con plataformas y servicios en la nube de Microsoft.
  
**Figura 1: La pila de nube híbrida de Microsoft**

![La pila de nube híbrida de Microsoft](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
En la figura 1, se muestra la pila de nube híbrida de Microsoft y su capa, que puede ser Local, Red, Identidad, aplicaciones y escenarios, y la categoría de servicio en la nube (SaaS de Microsoft y PaaS de Azure).
  
La capa de aplicaciones y escenarios contiene los escenarios de nube híbrida específicos que se detallan en los artículos adicionales de este modelo. Las capas Identidad, Red y Local pueden ser comunes a las categorías de servicio en la nube (SaaS o PaaS).
  
- Local
    
    La infraestructura local para escenarios híbridos puede incluir servidores de SharePoint, Exchange, Skype Empresarial y aplicaciones de línea de negocio. También puede incluir almacenes de datos (bases de datos, listas, archivos). Sin conexiones de ExpressRoute, se debe permitir el acceso a los almacenes de datos locales a través de un proxy inverso o al hacer que el servidor o los datos sean accesibles en su red perimetral o extranet.
    
- Red
    
    Hay dos opciones para la conectividad con plataformas de nube de Microsoft y servicios: la canalización de Internet existente y ExpressRoute. Usar una conexión de ExpressRoute si el rendimiento predecible es importante. Puede usar una conexión de ExpressRoute para conectarse directamente a los servicios de Microsoft SaaS (Office 365 y Dynamics 365), los servicios de Azure PaaS y servicios de Azure IaaS.
    
- Identidad
    
    Para la infraestructura de identidad de la nube, hay dos formas de proceder, según la plataforma de nube de Microsoft. Para SaaS y PaaS de Azure, integre la infraestructura de identidad local con Azure AD o fedérese con los proveedores de identidad de terceros o de infraestructura de identidad local. Para máquinas virtuales que se ejecutan en Azure, puede ampliar su infraestructura de identidad local, como Windows Server AD, a las redes virtuales (VNets) en que se encuentran las máquinas virtuales.
    
## <a name="hybrid-cloud-scenarios-for-the-three-phase-cloud-adoption-process"></a>Escenarios de nube híbrida para el proceso de adopción de la nube de tres fases

Muchas empresas, incluida Microsoft, usan un enfoque de tres fases para la adopción de la nube. Los escenarios de nube híbrida pueden desempeñar un papel en cada fase.
  
1. Mover las cargas de trabajo de productividad a SaaS
    
    Para las cargas de trabajo de productividad locales o que deben permanecer locales, los escenarios híbridos permiten que se integren con sus equivalentes en la nube.
    
2. Desarrollar aplicaciones nuevas y modernas en PaaS de Azure
    
    Las aplicaciones PaaS híbridas de Azure pueden aprovechar con seguridad los recursos de almacenamiento o del servidor local.
    
3. Mover aplicaciones existentes a IaaS de Azure
    
    Para los escenarios de elevar y desplazar y compilar en la nube, las aplicaciones basadas en servidor que se ejecutan en máquinas virtuales de Azure ofrecen aprovisionamiento y escalado sencillos.
    
## <a name="see-also"></a>Vea también

[Microsoft Hybrid Cloud para arquitectos profesionales](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)



