---
title: "Información general de la nube híbrida"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Ent_O365_Visuals
ms.custom:
- DecEntMigration
- Ent_Architecture
ms.assetid: 3ea3ee10-411e-4690-b9e5-f1b46f1f4d59
description: "Resumen: Comprenda la definición y los elementos de la nube híbrida de Microsoft."
ms.openlocfilehash: 9ece0f2e09384c0b9e6d9042b899d782be6327b5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="hybrid-cloud-overview"></a>Información general de la nube híbrida

 **Resumen:** Comprenda la definición y los elementos de la nube híbrida de Microsoft.
  
La nube híbrida usa recursos de proceso o almacenamiento en la red local y en la nube. Puede usar la nube híbrida como una ruta para migrar su empresa y sus necesidades de TI a la nube, o bien para integrar plataformas y servicios en la nube con su infraestructura local existente, como parte de su estrategia de TI.
  
## <a name="microsoft-hybrid-cloud"></a>Nube híbrida de Microsoft

La nube híbrida de Microsoft es un conjunto de escenarios empresariales que combinan una plataforma en la nube de Microsoft con un componente local como, por ejemplo: 
  
- Obtención de resultados de la búsqueda de contenido tanto de una granja de SharePoint local como de SharePoint Online en Office 365.
    
- Una aplicación móvil que se ejecuta en Azure y que consulta un almacén de datos local.
    
- Una carga de trabajo de TI de la intranet que se ejecuta en máquinas virtuales de Azure.
    
**Figura 1: Componentes de la nube híbrida de Microsoft**

![Componentes de la nube híbrida de Microsoft](images/Hybrid_Poster/MS_Hybrid_Cloud.png)
  
En la figura 1, se muestran los componentes de la nube híbrida de Microsoft, desde una red local al conjunto de servicios de Office 365, de la plataforma como servicio (PaaS) de Azure y de la infraestructura como servicio (IaaS) de Azure disponibles a través de Internet o una conexión de ExpressRoute.
  
Dado que Microsoft tiene la solución de nube más completa del mercado, que incluye Software como servicio (SaaS), PaaS e IaaS, puede hacer lo siguiente:
  
- Aprovechar sus inversiones locales existentes mientras migra aplicaciones y cargas de trabajo a la nube.
    
- Incorporar escenarios de nube híbrida en sus planes de TI a largo plazo, por ejemplo, cuando la normativa o las directivas no permitan mover datos específicos o cargas de trabajo a la nube.
    
- Crear escenarios híbridos adicionales que incluyan varios servicios y plataformas en la nube de Microsoft.
    
Los escenarios de nube híbrida con servicios en la nube de Microsoft varían según la plataforma.
  
- SaaS
    
    Los servicios SaaS de Microsoft incluyen Office 365, Microsoft Intune y Microsoft Dynamics 365. Los escenarios de nube híbrida con SaaS de Microsoft combinan estos servicios con aplicaciones o servicios locales. Por ejemplo, Exchange Online en ejecución en Office 365 puede integrarse con Skype Empresarial 2015, que está implementado de forma local.
    
- PaaS de Azure
    
    Los servicios de PaaS de Microsoft Azure le permiten crear aplicaciones basadas en la nube. Los escenarios de nube híbrida con servicios de PaaS de Azure combinan una aplicación de PaaS de Azure con recursos o aplicaciones locales. Por ejemplo, una aplicación de PaaS de Azure pudo consultar de forma segura un almacén de datos local para obtener información necesaria para mostrar a usuarios de aplicaciones móviles.
    
- IaaS de Azure
    
    Los servicios de IaaS de Azure permiten crear y ejecutar cargas de trabajo de TI basadas en servidor en la nube, en lugar de en su centro de datos local. Los escenarios de nube híbrida con servicios de IaaS de Azure suelen constar de una carga de trabajo de TI que se ejecuta en máquinas virtuales que están conectadas de forma transparente a la red local. Los usuarios locales no notarán la diferencia.
    
## <a name="elements-of-hybrid-cloud"></a>Elementos de la nube híbrida

Debe tener en cuenta los siguientes elementos al planear e implementar escenarios de nube híbrida con plataformas y servicios en la nube de Microsoft.
  
- Redes
    
    Las redes para escenarios de nube híbrida incluyen la conectividad a plataformas y servicios en la nube de Microsoft, así como ancho de banda suficiente para mantener el rendimiento durante las cargas máximas. Para obtener más información, consulte [Microsoft Cloud Networking para arquitectos profesionales](microsoft-cloud-networking-for-enterprise-architects.md).
    
- Identidad
    
    La identidad de los escenarios híbridos SaaS y PaaS de Azure puede incluir Azure AD como proveedor de identidades común, que se puede sincronizar con Windows Server AD local, o bien federarse con Windows Server AD u otros proveedores de identidades. También puede ampliar su infraestructura de identidad local a IaaS de Azure. Para obtener más información, consulte [Identidad de nube de Microsoft para arquitectos de empresa](microsoft-cloud-identity-for-enterprise-architects.md).
    
- Seguridad
    
    La seguridad de los escenarios de nube híbrida incluye protección y administración de identidades, protección de datos, administración de privilegios administrativos, reconocimiento de amenazas e implementación de directivas de control y seguridad de datos. Para obtener más información, consulte [Seguridad en la nube de Microsoft para arquitectos profesionales](https://technet.microsoft.com/library/dn919927.aspx#security).
    
- Administración
    
    La administración de escenarios de nube híbrida incluye la capacidad para mantener opciones de configuración, datos, cuentas, directivas y permisos, así como para supervisar el estado de los elementos del escenario y su rendimiento. También puede usar el mismo conjunto de herramientas, como Systems Management Server, para administrar máquinas virtuales en IaaS de Azure.
    
## <a name="see-also"></a>See Also

[Microsoft Hybrid Cloud para arquitectos profesionales](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)
 


