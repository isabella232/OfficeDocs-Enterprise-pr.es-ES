---
title: Arquitectura de los escenarios de nube híbrida de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 06d8c959-39e5-4150-b1ae-aaf0eee4c058
description: 'Resumen: Comprenda la arquitectura de las ofertas de nube híbrida de Microsoft.'
ms.openlocfilehash: 513e45629a7092803cc644241d84985a37e43876
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068326"
---
# <a name="architecture-of-microsoft-hybrid-cloud-scenarios"></a>Arquitectura de escenarios de nube híbrida de Microsoft

 **Resumen:** Comprenda la arquitectura de las ofertas de nube híbrida de Microsoft.
  
Use un enfoque de arquitectura para planear e implementar escenarios de nube híbrida con plataformas y servicios en la nube de Microsoft.
  
**Figura 1: La pila de nube híbrida de Microsoft**

![La pila de nube híbrida de Microsoft](media/Hybrid-Poster/Hybrid-Cloud-Stack.png)
  
En la figura 1, se muestra la pila de nube híbrida de Microsoft y su capa, que puede ser Local, Red, Identidad, aplicaciones y escenarios, y la categoría de servicio en la nube (SaaS de Microsoft y PaaS de Azure).
  
El nivel de aplicaciones y escenarios tiene los escenarios de nube híbrida específicos que se detallan en los artículos adicionales de este modelo. Las capas Identidad, Red y Local pueden ser comunes a las categorías de servicio en la nube (SaaS o PaaS).
  
- Local
    
    La infraestructura local para escenarios híbridos puede incluir servidores de SharePoint, Exchange, Skype Empresarial y aplicaciones de línea de negocio. También puede incluir almacenes de datos (bases de datos, listas, archivos). Sin conexiones de ExpressRoute, se debe permitir el acceso a los almacenes de datos locales a través de un proxy inverso o al hacer que el servidor o los datos sean accesibles en su red perimetral o extranet.
    
- Red
    
    Hay dos opciones de conectividad con plataformas y servicios de nube de Microsoft: la canalización de Internet existente y ExpressRoute. Use una conexión de ExpressRoute si es importante el rendimiento predecible. Puede usar una conexión de ExpressRoute para conectarse directamente a los servicios de SaaS de Microsoft (Office 365 y Dynamics 365), los servicios PaaS de Azure y los servicios de IaaS de Azure.
    
- Identidad
    
    Para la infraestructura de identidad de la nube, hay dos formas de proceder, según la plataforma de nube de Microsoft. Para SaaS y PaaS de Azure, integre la infraestructura de identidad local con Azure AD o fedérese con los proveedores de identidad de terceros o de infraestructura de identidad local. Para las máquinas virtuales que se ejecutan en Azure, puede ampliar la infraestructura de identidades local, como los servicios de dominio de Active Directory (AD DS), a las redes virtuales (Vnet) donde residen las VM.
    
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
  
[Recursos de arquitectura de TI de Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

