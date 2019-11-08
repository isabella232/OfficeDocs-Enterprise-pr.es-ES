---
title: Recursos de arquitectura de TI de la nube de Microsoft
ms.author: bcarter
author: brendacarter
manager: laurawi
audience: ITPro
ms.topic: hub-page
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Architecture
ms.assetid: 28986107-e2fb-4116-bfdd-f66d751a7c16
search.appverid:
- MET150
description: 'Resumen: conozca los conceptos principales de arquitectura de la nube de identidad, seguridad, redes e híbrida de Microsoft. Revise las recomendaciones para proteger los archivos, las identidades y los dispositivos al usar la nube de Microsoft. Obtenga información sobre cómo implementar un escritorio moderno y seguro con Windows 10 y Office ProPlus.'
ms.openlocfilehash: 8fd86e045f0c40857c13e9875477eba23f1f6fca
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38032285"
---
# <a name="microsoft-cloud-it-architecture-resources"></a>Recursos de arquitectura de TI de la nube de Microsoft

 **Resumen:** conozca los conceptos principales de arquitectura de la nube de identidad, seguridad, redes e híbrida de Microsoft. Revise las recomendaciones para proteger los archivos, las identidades y los dispositivos al usar la nube de Microsoft. Obtenga información sobre cómo implementar un escritorio moderno y seguro con Windows 10 y Office ProPlus.
  
Estos pósteres y herramientas de arquitectura ofrecen información acerca de los servicios en la nube de Microsoft, como Office 365, Windows 10, Azure Active Directory, Microsoft Intune, Microsoft Dynamics 365 y las soluciones híbridas locales y en la nube. Los arquitectos y los responsables de la toma de decisiones de TI pueden usar estos recursos para determinar las soluciones ideales para sus cargas de trabajo y para tomar decisiones acerca de los componentes de la infraestructura básica, como la identidad y la seguridad. 
  
<!--**[Microsoft's Enterprise Cloud Roadmap](microsoft-cloud-it-architecture-resources.md#roadmap)** (Sway) -->
    
- **[Serie de la nube de Microsoft para arquitectos empresariales](microsoft-cloud-it-architecture-resources.md#cloudarch)** 
    <!-- [Microsoft Cloud Services and Platform Options](microsoft-cloud-it-architecture-resources.md#platformoptions) -->
    - [Identidad de la nube de Microsoft para arquitectos empresariales](microsoft-cloud-it-architecture-resources.md#identity)
    - [Seguridad de la nube de Microsoft para arquitectos empresariales](microsoft-cloud-it-architecture-resources.md#security)
    - [Redes de la nube de Microsoft para arquitectos empresariales](microsoft-cloud-it-architecture-resources.md#networking)
    - [Nube híbrida de Microsoft para arquitectos empresariales](microsoft-cloud-it-architecture-resources.md#hybrid)
    - [Ataques comunes y funcionalidades de Microsoft que protegen su organización](#common-attacks-and-microsoft-capabilities-that-protect-your-organization)
    - [Infraestructura básica de Microsoft 365 Enterprise](#m365foundationinfra)
    - [Métodos de arquitectura para migraciones de inquilino a inquilino de la nube de Microsoft](#architecture-approaches-for-microsoft-cloud-tenant-to-tenant-migrations)
    
- **[Serie de soluciones de Microsoft 365 Enterprise](microsoft-cloud-it-architecture-resources.md#BKMK_o365solutions)**:
    - [Microsoft Teams y servicios de productividad relacionados de Microsoft 365 para arquitectos de TI](#microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects)
    - [Grupos en Microsoft 365 para arquitectos de TI](#groups-in-microsoft-365-for-it-architects)
    - [Protección de identidades y dispositivos para Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365IDP)
    - [Soluciones de protección de archivos en Office 365](microsoft-cloud-it-architecture-resources.md#BKMK_O365fileprotect)
    - [Information Protection de Office 365 para RGPD](#office-365-information-protection-for-gdpr)
    - [Instrucciones de seguridad de Microsoft para campañas políticas, organizaciones sin ánimo de lucro y otras organizaciones ágiles](#microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations)
    - [Soluciones de telefonía de Microsoft](#microsoft-telephony-solutions) 
    - [Implementar un escritorio seguro y moderno con Microsoft](microsoft-cloud-it-architecture-resources.md#msd)
    
Queremos conocer su opinión. Envíenos un correo electrónico a [cloudadopt@microsoft.com](mailto:cloudadopt@microsoft.com). 

<!--
<a name="roadmap"></a>
## Microsoft's Enterprise Cloud Roadmap

See the posters, icon sets, community venues, and other resources that describe the industry's most complete cloud solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumbnail for Enterprise Cloud Roadmap](media/c8b293b9-5992-4d29-b579-a6bbbd59d8d6.png)          ](https://aka.ms/cloudarchitecture) <br/> [Microsoft's Enterprise Cloud Roadmap](https://aka.ms/cloudarchitecture) (https://aka.ms/cloudarchitecture) <br/> |Swipe through this Sway experience for the resources that describe the industry's most complete cloud solution.  <br/> |
-->
  
<a name="cloudarch"></a>
## Serie de la nube de Microsoft para arquitectos empresariales

Estos pósteres de arquitectura en la nube le ofrecen información acerca de los servicios en la nube de Microsoft, como Office 365, Azure Active Directory, Microsoft Intune, Microsoft Dynamics CRM Online y las soluciones híbridas locales y en la nube. Los arquitectos y los responsables de la toma de decisiones de TI pueden usar estos recursos para determinar las soluciones ideales para sus cargas de trabajo y para tomar decisiones acerca de los componentes de la infraestructura básica, como la identidad y la seguridad.

<!--  
<a name="platformoptions"></a>
### Microsoft Cloud Services and Platform Options

Learn key differences between Microsoft cloud services and platform offerings. Find the best fit for your solution.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumb image of cloud architecture model with service options](media/ff5c74e2-afc6-40c1-9292-cc4cb128cdd1.png)          ](https://www.microsoft.com/download/details.aspx?id=54432) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524731)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=524732)  \| [More languages](https://www.microsoft.com/download/details.aspx?id=54432) <br/> | This model describes: <ul><li>  Software as a Service (SaaS) offerings, including Office 365 </li><li>  Platform as a Service (PaaS) features in Microsoft Azure </li><li>  Infrastructure as a Service (IaaS) features in Microsoft Azure </li><li>  Private cloud datacenter capabilities using Windows Server and System Center </li><li>  Learn how Microsoft's own IT department is migrating to these cloud services and building its hybrid cloud. </li></ul><br/>|
-->

   
<a name="identity"></a>
### Identidad de nube de Microsoft para arquitectos profesionales

Lo que los arquitectos de TI necesitan saber sobre el diseño de la identidad para las organizaciones que usan plataformas y servicios en la nube de Microsoft.
  
|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura del modelo de identidad de Microsoft Cloud](media/ffa145a1-97e6-4c36-b08b-01c4a4ae8b9b.png)          ](https://www.microsoft.com/download/details.aspx?id=54431) <br/> [PDF](https://go.microsoft.com/fwlink/p/?LinkId=524586)  \| [Visio](https://download.microsoft.com/download/2/3/8/238228E6-9017-4F6C-BD3C-5559E6708F82/MSFT_cloud_architecture_identity.vsd)           \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=54431) <br/> | Este modelo contiene lo siguiente: <ul><li>Introducción a la identidad con la nube de Microsoft </li><li>Capacidades de IDaaS de Azure AD </li><li>Integración de cuentas locales de Active Directory Domain Services con Microsoft Azure Active Directory </li><li>Colocación de componentes de directorio en Azure </li><li>Opciones de servicios de dominio para cargas de trabajo en IaaS de Azure </li></ul><br/>|
   
<a name="security"></a>
### <a name="microsoft-cloud-security-for-enterprise-architects"></a>Seguridad de nube de Microsoft para arquitectos empresariales

Lo que los arquitectos de TI necesitan saber sobre la seguridad en las plataformas y los servicios en la nube de Microsoft.
  
|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura del modelo de seguridad de Microsoft Cloud](media/5dc26f80-8888-4572-8ed9-a120d711e0f0.png)          ](https://www.microsoft.com/download/details.aspx?id=48121) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842070)  \| [Visio](https://go.microsoft.com/fwlink/p/?LinkId=842071)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=48121) <br/> | Este modelo contiene lo siguiente: <ul><li>Rol de Microsoft a la hora de proporcionar servicios y plataformas seguros</li><li>Responsabilidades del cliente para mitigar los riesgos de seguridad</li><li>Principales certificaciones de seguridad </li><li>Ofertas de seguridad proporcionadas por los servicios de consultoría de Microsoft </ul><br/>|
   
<a name="networking"></a>
### <a name="microsoft-cloud-networking-for-enterprise-architects"></a>Redes de nube de Microsoft para arquitectos empresariales

Lo que los arquitectos de TI necesitan saber sobre las redes para las plataformas y los servicios en la nube de Microsoft.
  
|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura del modelo de redes de Microsoft Cloud](media/95e8ab6a-b4d0-4836-acc1-b0b77ebf46e6.png)          ](https://www.microsoft.com/download/details.aspx?id=54425) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842073)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=842074)           \| [Artículo](https://technet.microsoft.com/library/mt733214.aspx) <br/>[Más idiomas](https://www.microsoft.com/download/details.aspx?id=54425) <br/> | Este modelo contiene las páginas siguientes: <ul><li> **Desarrollo de la red para la conectividad en la nube** La migración a nube cambia el volumen y el carácter de los flujos de tráfico dentro y fuera de una red corporativa. También afecta a los métodos para mitigar los riesgos de seguridad.</li><li> **Elementos comunes de la conectividad en la nube de Microsoft** La integración de las redes con la nube de Microsoft proporciona un acceso óptimo a una amplia gama de servicios. </li><li> **ExpressRoute para la conectividad en la nube de Microsoft** ExpressRoute proporciona una conexión de red privada, dedicada y de alto rendimiento para la nube de Microsoft. </li><li> **Diseño de redes para SaaS de Microsoft (Office 365, Microsoft Intune y Dynamics CRM Online)** La optimización de la red para los servicios SaaS de Microsoft requiere un análisis cuidadoso de su perímetro de Internet, los dispositivos cliente y las operaciones de TI típicas. </li><li> **Diseño de redes para PaaS de Azure** La optimización de las redes para aplicaciones PaaS de Azure requiere suficiente ancho de banda de Internet y puede requerir la distribución del tráfico de red por varios sitios o aplicaciones. </li><li> **Diseño de redes para la IaaS de Azure** Siga los pasos del proceso de diseño para crear una red virtual de Azure óptima para cargas de trabajo de TI basadas en servidores de hospedaje (subredes, espacios de direcciones, enrutamiento, DNS, equilibrio de carga y conectividad a Internet, a la red local y a otras redes virtuales). </li></ul><br/>  <br/>|
   
   
<a name="hybrid"></a>
### <a name="microsoft-hybrid-cloud-for-enterprise-architects"></a>Nube híbrida de Microsoft para arquitectos empresariales

Lo que los arquitectos de TI necesitan saber sobre la nube híbrida para las plataformas y los servicios Microsoft.
  
|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura del modelo de nube híbrida de Microsoft](media/9989c71e-f6a0-4dbe-906c-43e67b3ce537.png)          ](https://www.microsoft.com/download/details.aspx?id=54424) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=842082)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=842083)           \| [Artículo](https://technet.microsoft.com/library/mt750500.aspx) <br/>[Más idiomas](https://www.microsoft.com/download/details.aspx?id=54424) <br/> | Este modelo contiene las páginas siguientes: <ul><li> **Resumen de la nube híbrida** Ofertas de la nube de Microsoft (SaaS, Azure PaaS y Azure IaaS) y sus elementos comunes. </li><li> **Arquitectura de escenarios de nube híbrida de Microsoft** Esquema de la arquitectura de la nube híbrida para ofertas de Microsoft. Muestra las capas comunes de infraestructura local, redes e identidad. </li><li> **Escenarios de nube híbrida de Microsoft SaaS (Office 365)** Arquitectura del escenario híbrido de SaaS y descripciones de las configuraciones híbridas clave de Skype Empresarial, SharePoint Server y Exchange Server. </li><li> **Escenarios de nube híbrida de Azure PaaS** Arquitectura de escenarios híbridos de Azure PaaS, descripción de una aplicación híbrida de Azure PaaS con un ejemplo y descripción de la base de datos de SQL Server 2016 Stretch. </li><li> **Escenarios de nube híbrida de Azure IaaS** Arquitectura del escenario híbrido de Azure IaaS y descripción de una aplicación de línea de negocio (LOB) hospedada en Azure IaaS. </li></ul><br/>|
   
<a name="attacks"></a>
### <a name="common-attacks-and-microsoft-capabilities-that-protect-your-organization"></a>Ataques comunes y funcionalidades de Microsoft que protegen su organización
Obtenga información sobre los ciberataques más comunes y cómo Microsoft puede ser de utilidad a su organización en todas las fases de un ataque. 

|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura del póster Ataques comunes.](media/common%20attacks-thumb3.png) ](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) <br/> [PDF](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.pdf) \| [Visio](https://download.microsoft.com/download/F/A/C/FACFC1E9-FA35-4DF1-943C-8D4237B4275B/MSFT_Cloud_architecture_security_commonattacks.vsdx) <br/> | Este póster ilustra la ruta de acceso de los ataques comunes y en él se describen las funcionalidades que ayudan a detener a los intrusos en cada fase de un ataque. <br/>|

<a name="m365foundationinfra"></a>
### <a name="microsoft-365-enterprise-foundation-infrastructure"></a>Infraestructura básica de Microsoft 365 Enterprise

Obtenga una vista rápida de la [infraestructura básica](https://docs.microsoft.com/microsoft-365/enterprise/deploy-foundation-infrastructure) de Microsoft 365 Enterprise para comenzar su implementación.
  
|**Item**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura del póster de la infraestructura básica Microsoft 365 Enterprise](media/Microsoft365EnterpriseFoundInfra-thumb.png)](https://aka.ms/m365efoundinfraposter) <br/> [Ver en línea](https://aka.ms/m365efoundinfraposter) \| [PDF](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/enterprise/media/deploy-foundation-infrastructure/Microsoft365EnterpriseFoundInfra.pdf) <br/> | Este póster resume cada fase de la infraestructura básica en términos de objetivos, características y herramientas, decisiones de diseño, resultados de la configuración, incorporación y supervisión y actualizaciones constantes. <br/>| 

### <a name="architecture-approaches-for-microsoft-cloud-tenant-to-tenant-migrations"></a>Métodos de arquitectura para migraciones de inquilino a inquilino de la nube de Microsoft 
En esta serie de temas se muestran varios métodos de arquitectura para las fusiones, las adquisiciones, las ventas y otros casos que podrían llevarle a migrar a un nuevo inquilino en la nube. En estos temas se proporciona una guía inicial para la planeación.

|**Item**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura para el póster de la arquitectura lógica de Teams](downloads/msft-tenant-to-tenant-migration-thumb.png)](downloads/Microsoft-365-tenant-to-tenant-migration.pdf) <br/> [PDF](downloads/Microsoft-365-tenant-to-tenant-migration.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/Microsoft-365-tenant-to-tenant-migration.vsdx)     |Este modelo contiene lo siguiente: <ul><li>Una asignación de escenarios empresariales a métodos arquitectónicos</li><li>Consideraciones sobre diseño</li><li>Flujo de migración de evento único</li><li>Flujo de migración en fases</li><li>Flujo de desplazamiento o división del inquilino</li></ul>|

<!--<a name="santa"></a>
### The Santa cloud

How Santa and his elves use Microsoft's cloud offerings to make their annual deliveries.
  
|**Item**|**Description**|
|:-----|:-----|
|[![Thumbnail image of The Santa Cloud poster](media/d47e1448-329b-41b7-9e51-cfc4ea5d0069.png)](https://www.microsoft.com/download/details.aspx?id=55039) <br/> [View online](https://onedrive.live.com/?authkey=%21ANT1PMgxEdniCyY&cid=8A8EC4F6612625E0&id=8A8EC4F6612625E0%21440&parId=8A8EC4F6612625E0%21218&o=OneUp) \| [PDF](https://go.microsoft.com/fwlink/p/?linkid=842088) <br/> |To determine who is naughty or nice and the presents to deliver on December 24, Santa Claus and his elfish IT department use Office 365, Azure, Dynamics 365, and Intune.  <br/>| -->
   
<a name="BKMK_o365solutions"></a>
## Serie de soluciones de Microsoft 365 Enterprise

La serie de soluciones empresariales de Microsoft 365 ofrece orientación para implementar funcionalidades de Microsoft 365, sobre todo cuando estas abarcan varias tecnologías.

### <a name="microsoft-teams-and-related-productivity-services-in-microsoft-365-for-it-architects"></a>Microsoft Teams y servicios de productividad relacionados de Microsoft 365 para arquitectos de TI
La arquitectura lógica de los servicios de productividad en Microsoft 365, una de las más destacadas gracias a Microsoft Teams.

|**Item**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura para el póster de la arquitectura lógica de Teams](downloads/msft-teams-logical-architecture-thumb.png)](downloads/msft-m365-teams-logical-architecture.pdf) <br/> [PDF](downloads/msft-m365-teams-logical-architecture.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-teams-logical-architecture.vsdx)     |Microsoft proporciona un conjunto de servicios de productividad que funcionan en conjunto para proporcionar experiencias de colaboración con funcionalidades de gobierno, seguridad y cumplimiento. <br/> <br/>Esta serie de ilustraciones proporciona una vista de la arquitectura lógica de los servicios de productividad para arquitectos empresariales, que es una de las más destacadas gracias a Microsoft Teams.|


### <a name="groups-in-microsoft-365-for-it-architects"></a>Grupos en Microsoft 365 para arquitectos de TI
Lo que necesitan saber los arquitectos de TI sobre los grupos en Microsoft 365

|**Item**|**Descripción**|
|:-----|:-----|
|[![Imagen en miniatura para la infografía de grupos](downloads/msft-m365-groups-architecture-thumb.png)](downloads/msft-m365-groups.pdf) <br/> [PDF](downloads/msft-m365-groups.pdf) \| [Visio](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/downloads/msft-m365-groups.vsdx) |Estas ilustraciones detallan los diferentes tipos de grupos, cómo se crean y administran, y algunas recomendaciones para el gobierno de estos.|

   
<a name="BKMK_O365IDP"></a>
### <a name="identity-and-device-protection-for-office-365"></a>Protección de identidades y dispositivos para Office 365

Capacidades recomendadas para la protección de las identidades y los dispositivos que tienen acceso a Office 365, otros servicios de SaaS y aplicaciones locales publicadas con Proxy de la aplicación de Azure AD.
  
|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Póster del modelo: Protección de dispositivos e identidad para Office 365 y otras aplicaciones SaaS](media/c1cfb31b-5150-45ff-b46c-3a237e9f5581.png)          ](https://www.microsoft.com/download/details.aspx?id=55032) <br/> [PDF](https://go.microsoft.com/fwlink/p/?linkid=841656)  \| [Visio](https://go.microsoft.com/fwlink/p/?linkid=841657)  \| [Más idiomas](https://www.microsoft.com/download/details.aspx?id=55032) <br/> |Es importante usar siempre los mismos niveles de protección para todos sus datos, identidades y dispositivos. En este documento, se muestran las capacidades que son comparables con más información sobre las capacidades para proteger las identidades y los dispositivos.  <br/> |
   
<a name="BKMK_O365fileprotect"></a>
### <a name="file-protection-solutions-in-office-365"></a>Soluciones de protección de archivos en Office 365

Capacidades recomendadas para proteger archivos en Office 365 basándose en tres niveles de confidencialidad diferentes.
  
|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Miniatura de Soluciones de protección de archivos en el conjunto de minipósteres de Office 365](media/24be68b5-d852-4fdb-94ad-94491a19edd8.png)          ](https://www.microsoft.com/download/details.aspx?id=55523) <br/> [PDF](https://go.microsoft.com/fwlink/?linkid=2004320)  \| [Visio](https://download.microsoft.com/download/7/8/9/789645A5-BD10-4541-BC33-F8D1EFF5E911/MSFT_cloud_architecture_O365%20file%20protection.vsdx) <br/> |Es importante usar siempre los mismos niveles de protección para todos sus datos, identidades y dispositivos. En este documento, se muestran las capacidades que son comparables con más información sobre las capacidades para proteger archivos en Office 365.  <br/> |
   

### <a name="office-365-information-protection-for-gdpr"></a>Information Protection de Office 365 para RGPD

Recomendaciones para descubrir, clasificar, proteger y supervisar datos personales. Esta solución usa el Reglamento general de protección de datos (RGPD) como ejemplo, pero se puede aplicar el mismo proceso para lograr el cumplimiento con muchas otras normativas.

|**Elemento**|**Descripción**|
|:-----|:-----|
|![Miniatura para Information Protection de Office 365 para RGPD](media/o365infoprotectforgdpr-thumb.png)  <br/> [PDF](http://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.pdf) \| [Visio](http://download.microsoft.com/download/E/C/D/ECD5A339-EF10-4420-B3A9-99098884D716/MSFT_Cloud_architecture_information%20protection%20for%20GDPR.vsdx)    |Si desea ver este contenido en formato de artículo, haga clic en [Information Protection de Office 365 para RGPD](https://docs.microsoft.com/Office365/SecurityCompliance/office-365-information-protection-for-gdpr).      |

### <a name="microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-organizations"></a>Guía de seguridad de Microsoft para campañas políticas, ONG y otras organizaciones ágiles 

Estas instrucciones explican cómo implementar un entorno de nube seguro. Las instrucciones de solución se pueden usar en cualquier organización. Incluyen ayuda adicional para organizaciones ágiles con cuentas de invitado y de acceso BYOD. Puede usarlas como punto de partida para diseñar un entorno propio.


|**Elemento**|**Descripción**|
|:-----|:-----|
|**Guía de seguridad de Microsoft para campañas políticas** <br/> [![Miniatura de conjunto de minipósteres.](media/d370ce28-ca40-4930-9a2c-907312aa06c8.png)          ](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf) <br/> [PDF](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.pdf)  \| [Visio](https://download.microsoft.com/download/B/4/D/B4D520C3-4D0C-4B4D-BFB9-09F0651C2775/MSFT_Cloud_architecture_security%20for%20political%20campaigns.vsdx) <br/> |En esta guía, se usa una organización de campaña política como ejemplo. Use esta guía como punto inicial para cualquier entorno.  <br/> |
|**Guía de seguridad de Microsoft para ONG** <br/> [![Imagen en miniatura de archivo descargable](media/e4784889-1c69-4067-9a8f-31d31d1eceea.png)          ](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf) <br/> [PDF](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.pdf)  \| [Visio](https://download.microsoft.com/download/9/4/3/94389612-C679-4061-8DF2-D9A15D72B65F/Microsoft_Cloud%20Architecture_Security%20for%20Nonprofits.vsdx) <br/> |Estas Instrucciones se han modificado ligeramente para las organizaciones sin ánimo de lucro. Por ejemplo, hacen referencia a los planes sin ánimo de lucro de Office 365. Las instrucciones técnicas son las mismas que las de la campaña política.  <br/> |

Estas instrucciones incluyen Guías del entorno de pruebas. Para obtener más información, consulte [Instrucciones de seguridad de Microsoft para campañas políticas, organizaciones sin ánimo de lucro y otras organizaciones ágiles](https://docs.microsoft.com/Office365/SecurityCompliance/microsoft-security-guidance-for-political-campaigns-nonprofits-and-other-agile-o).

### <a name="microsoft-telephony-solutions"></a>Soluciones de telefonía de Microsoft

Microsoft es compatible con varias opciones cuando empieza a utilizar Teams en la nube de Microsoft. Este póster le ayudará a decidir qué solución de telefonía de Microsoft (sistema telefónico en la nube o Enterprise Voice para ubicaciones locales) es adecuada para los usuarios de su organización y cómo su organización puede conectarse a la red telefónica pública conmutada (RTC).

![Miniatura del póster de soluciones de telefonía de Microsoft](media/microsoft-telephony-solutions-thumb.png) <br/>
[PDF](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.pdf) | [Visio](https://github.com/MicrosoftDocs/OfficeDocs-SkypeForBusiness/blob/live/Teams/downloads/telephony-solutions/microsoft-telephony-solutions-12-18.vsdx) 

Para obtener más información, consulte el artículo de este póster: [Soluciones de telefonía de Microsoft](https://docs.microsoft.com/SkypeForBusiness/hybrid/msft-telephony-solutions).
  
<a name="msd"></a>
### <a name="deploy-a-modern-and-secure-desktop-with-microsoft"></a>Implementación de un escritorio seguro y moderno con Microsoft

Todo lo que los arquitectos de TI necesitan saber para implementar y administrar las actualizaciones de Office 365 ProPlus en Windows 10.
  
|**Elemento**|**Descripción**|
|:-----|:-----|
|[![Miniatura del modelo Implementación de un escritorio seguro y moderno con Microsoft](media/321dd59c-d992-4c7a-a7b6-c23a783858bd.png)          ](https://www.microsoft.com/download/details.aspx?id=55987) <br/> [PDF](https://download.microsoft.com/download/4/E/9/4E90E227-770A-41D1-99FE-925A64D81A55/MSFT_modern_secure_desktop.pdf)  \| [Visio](https://download.microsoft.com/download/4/E/9/4E90E227-770A-41D1-99FE-925A64D81A55/MSFT_modern_secure_desktop.vsdx) <br/> | Este modelo contiene lo siguiente: <ul><li>  Implementación de Windows 10 y Office ProPlus desde Microsoft Cloud </li><li>  Implementación de Windows 10 y Office ProPlus con System Center Configuration Manager </li><li>  Administración de las actualizaciones de Windows 10 y Office ProPlus desde Microsoft Cloud </li><li>  Administración de las actualizaciones de Windows 10 y Office ProPlus con System Center Configuration Manager </li><li>  Funciones de protección prediseñadas y adicionales para Windows 10 </li></ul><br/> |
   
## <a name="see-also"></a>Vea también

[Modelos de arquitectura para SharePoint, Exchange, Skype Empresarial y Lync](architectural-models-for-sharepoint-exchange-skype-for-business-and-lync.md)
  
[Guías de entorno de pruebas de adopción de la nube (TLG)](cloud-adoption-test-lab-guides-tlgs.md)
  
[Soluciones de seguridad](security-solutions.md)
  
[Soluciones híbridas](hybrid-solutions.md)

