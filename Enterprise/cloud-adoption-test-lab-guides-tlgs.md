---
title: Probar Office 365 con guías de entorno de pruebas de adopción de la nube (TLG)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/09/2019
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
description: 'Resumen: Con estas Guías del laboratorio de pruebas (TLG) para la adopción de la nube, podrá configurar entornos de demostración, prueba de concepto y desarrollo y pruebas para Office 365.'
ms.openlocfilehash: a61716ae34d8dbe3f710696570c46cefd0f4aa4c
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34068146"
---
# <a name="test-office-365-with-cloud-adoption-test-lab-guides-tlgs"></a>Probar Office 365 con guías de entorno de pruebas de adopción de la nube (TLG)

 **Resumen:** Con estas Guías del laboratorio de pruebas (TLG) para la adopción de la nube, podrá configurar entornos de demostración, prueba de concepto y desarrollo y pruebas para Office 365.
  
Las TLG le permiten conocer los productos Microsoft de manera rápida. Son ideales para situaciones en las que necesita evaluar una tecnología o configuración antes de decidir si es adecuada y comenzar el diseño, planeación y lanzamiento para los usuarios. Esta experiencia práctica, que consiste en desarrollar la herramienta por sus propios medios y lograr que funcione, le permitirá entender los requisitos de implementación de un nuevo producto o solución, de modo que pueda planear mejor el hospedaje en la producción.
  
Las guías del laboratorio de pruebas también crean entornos representativos para desarrollo y pruebas de aplicaciones, también conocidos como entornos de desarrollo y pruebas.
  
![Guías del laboratorio de pruebas de Microsoft Cloud](media/24ad0d1b-3274-40fb-972a-b8188b7268d1.png)
  
Haga clic [aquí](http://aka.ms/catlgstack) para ver un mapa visual de todos los artículos en la pila de la Guía del laboratorio de pruebas de Office 365.
    
## <a name="office-365-devtest-environment"></a>Entorno de desarrollo y pruebas de Office 365

Use estos artículos para crear su entorno de desarrollo y pruebas de Office 365:
  
- [Entorno de desarrollo y pruebas de la configuración básica](base-configuration-dev-test-environment.md)
    
    Cree una intranet simplificada que se ejecute en los servicios de infraestructura de Azure. Este paso es opcional si quiere crear una configuración de empresa simulada.
    
- [Entorno de desarrollo y pruebas de Office 365](office-365-dev-test-environment.md)
    
    Cree una suscripción de prueba de Office 365 Enterprise E5, que puede realizar desde su equipo o desde una intranet simplificada que se ejecute en los servicios de infraestructura de Azure.
    
- [Sincronización de directorios (DirSync) para el entorno de desarrollo y pruebas de Office 365](dirsync-for-your-office-365-dev-test-environment.md)
    
    Instale y configure Azure AD Connect para la sincronización de directorios con sincronización de hash de contraseñas. Este paso es opcional si quiere crear una configuración de empresa simulada.
    
Para el entorno de desarrollo y pruebas de Office 365, use estos artículos para probar las características empresariales de Office 365:
  
- [Autenticación multifactor para el entorno de desarrollo y pruebas de Office 365](multi-factor-authentication-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe autenticación secundaria con un mensaje de texto enviado a su smartphone para una cuenta en su suscripción de Office 365.
    
- [Identidad federada para el entorno de desarrollo y pruebas de Office 365](federated-identity-for-your-office-365-dev-test-environment.md)
    
    Configure y demuestre autenticación federada con las cuentas de un dominio de Active Directory Domain Services (AD DS).
    
- [Cloud App Security para el entorno de desarrollo y pruebas de Office 365](cloud-app-security-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe la Office 365 Cloud App Security, que le permite crear directivas que supervisan e informan de actividades sospechosas en su suscripción de Office 365.
    
- [Protección contra amenazas avanzada en el entorno de desarrollo y pruebas de Office 365](advanced-threat-protection-for-your-office-365-dev-test-environment.md)
    
    Configure y pruebe la Protección contra amenazas avanzada, que es una característica de Exchange Online Protection (EOP), que le ayuda a evitar el malware en el correo electrónico.
    
- [eDiscovery avanzado para el entorno de desarrollo y pruebas de Office 365](advanced-ediscovery-for-your-office-365-dev-test-environment.md)
    
    Agregue datos de ejemplo y pruebe eDiscovery avanzado, que permite buscar y analizar rápidamente los datos que se almacenan en Office 365, como el correo electrónico y los documentos.
    
- [Protección de archivos confidenciales en el entorno de desarrollo y pruebas de Office 365](sensitive-file-protection-in-the-office-365-dev-test-environment.md)
    
    Pruebe el uso de Office 365 Information Rights Management para proteger los datos en documentos confidenciales, incluso cuando se han publicado accidentalmente en las carpetas de documentos incorrectas.
    
- [Etiquetado y clasificación de datos en el entorno de desarrollo y pruebas de Office 365](data-classification-and-labeling-in-the-office-365-dev-test-environment.md)
    
    Muestre cómo el cliente de Azure Information Protection puede usarse para clasificar documentos con varios niveles de seguridad.
    
- [Sitio de grupo de SharePoint Online aislado en su entorno para desarrollo y pruebas](isolated-sharepoint-online-team-site-dev-test-environment.md)
    
    Mostrar cómo crear un sitio de grupo de SharePoint Online aislado del resto de la organización para los recursos privados o muy confidenciales.
    

## <a name="simulated-cross-premises-devtest-environments"></a>Entornos de pruebas y desarrollo simulado de varias ubicaciones

Puede crear un entorno de pruebas y desarrollo simulado de varias ubicaciones que incluya una red virtual Azure y una red local simulada con estos artículos:
  
- [Red virtual entre locales simulada en Azure](simulated-cross-premises-virtual-network-in-azure.md)
    
    Cree una intranet simulada conectada a una red virtual de Azure en una configuración de la nube híbrida.
    
- [Intranet SharePoint Server 2016 en entorno de prueba y desarrollo de Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx)
    
    Cree una granja de un solo servidor de SharePoint Server 2016 en la red virtual de Azure y pruebe la conectividad y administración desde la red local simulada.
    
## <a name="sharepoint-server-2016-devtest-environments"></a>Entornos de desarrollo y pruebas de SharePoint Server 2016

Estos son entornos de desarrollo y pruebas de SharePoint Server 2016 que puede crear en los servicios de infraestructura de Azure:
  
- [Entorno de desarrollo y pruebas de SharePoint Server 2016 en Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-dev-test-environment-in-azure)
    
    Cree una granja de un solo servidor de SharePoint Server 2016 en los servicios de infraestructura de Azure.

- [SharePoint Server 2016 en un entorno de desarrollo y pruebas de Azure en una intranet](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment)
    
    Cree una granja de un solo servidor de SharePoint Server 2016 en los servicios de infraestructura de Azure y acceda a ella desde una intranet simulada.


## <a name="the-microsoft-365-enterprise-devtest-environments"></a>Los entornos de desarrollo y pruebas de Microsoft 365 Enterprise

Cree un entorno de desarrollo y pruebas para [Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365-enterprise/) con [estos artículos](https://docs.microsoft.com/microsoft-365/enterprise/m365-enterprise-test-lab-guides).  
    
## <a name="see-also"></a>Vea también

[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)
  
[Modelos de arquitectura para SharePoint, Exchange, Skype Empresarial y Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Soluciones híbridas](hybrid-solutions.md)
