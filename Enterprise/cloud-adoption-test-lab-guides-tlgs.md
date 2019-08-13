---
title: Probar Office 365 con Guías de laboratorio de pruebas (TLG)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/12/2019
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Resumen: Con estas Guías del laboratorio de pruebas (TLG), podrá configurar entornos de demostración, prueba de concepto y desarrollo y pruebas para Office 365.'
ms.openlocfilehash: 32675683846789f1e7be0e398e5b140d25d7ba80
ms.sourcegitcommit: d58cdc7b2296df12f7a05d14ba05ab224ffb3e0c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/13/2019
ms.locfileid: "36302742"
---
# <a name="test-office-365-with-test-lab-guides-tlgs"></a>Probar Office 365 con Guías de laboratorio de pruebas (TLG)

 **Resumen**: use estos artículos para configurar entornos de demostración, prueba de concepto y desarrollo y pruebas para Office 365.
  
Las TLG le permiten conocer los productos Microsoft de manera rápida. Son ideales para situaciones en las que necesita evaluar una tecnología o configuración antes de decidir si es adecuada y comenzar el diseño, planeación y lanzamiento para los usuarios. Esta experiencia práctica, que consiste en desarrollar la herramienta por sus propios medios y lograr que funcione, le permitirá entender los requisitos de implementación de un nuevo producto o solución, de modo que pueda planear mejor el hospedaje en la producción.
  
Las guías del laboratorio de pruebas también crean entornos representativos para desarrollo y pruebas de aplicaciones, también conocidos como entornos de desarrollo y pruebas.
  
![Guías del laboratorio de pruebas de Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
## <a name="office-365-devtest-environment"></a>Entorno de desarrollo y pruebas de Office 365

Use estos artículos para crear su entorno de desarrollo y pruebas de Office 365:
  
- [Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
    
    Cree una intranet simplificada que se ejecute en los servicios de infraestructura de Azure. Este paso es opcional si quiere crear una configuración de empresa simulada.
    
- [Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
    
    Cree una suscripción de prueba de Office 365 Enterprise E5, que puede realizar desde su equipo o desde una intranet simplificada que se ejecute en los servicios de infraestructura de Azure.
    
- [Sincronización de directorios](dirsync-for-your-office-365-dev-test-environment.md)
    
    Instale y configure Azure AD Connect para la sincronización de directorios con sincronización de hash de contraseñas. Este paso es opcional si quiere crear una configuración de empresa simulada.
    
Para el entorno de desarrollo y pruebas de Office 365, use estos artículos para probar las características empresariales de Office 365:
  
- [Autenticación multifactor](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe autenticación secundaria con un mensaje de texto enviado a su smartphone para una cuenta en su suscripción de Office 365.
    
- [Identidad federada](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configure y demuestre autenticación federada con las cuentas de un dominio de Active Directory Domain Services (AD DS).
    
- [Protección contra amenazas avanzada](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe la Protección contra amenazas avanzada, que es una característica de Exchange Online Protection (EOP), que le ayuda a evitar el malware en el correo electrónico.

## <a name="simulated-cross-premises-devtest-environment"></a>Entornos de pruebas y desarrollo simulado de varias ubicaciones

Cree una [intranet simulada](simulated-cross-premises-virtual-network-in-azure.md) conectada a una red virtual de Azure en una configuración de la nube híbrida.
    
## <a name="sharepoint-server-2016-devtest-environment"></a>Entornos de desarrollo y pruebas de SharePoint Server 2016

Cree una [granja de un solo servidor de SharePoint Server 2016](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure) en los servicios de infraestructura de Azure.

## <a name="microsoft-365-enterprise-devtest-environment"></a>Entorno de desarrollo y pruebas de Microsoft 365 Enterprise

Cree un entorno de desarrollo y pruebas para el [Entorno de desarrollo y pruebas de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides)  
    
## <a name="see-also"></a>Vea también

[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Modelos de arquitectura para SharePoint, Exchange, Skype Empresarial y Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluciones híbridas](hybrid-solutions.md)
