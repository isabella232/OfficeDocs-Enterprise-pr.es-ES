---
title: Escenarios de nube híbrida para SaaS de Microsoft (Office 365)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/30/2018
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: db117e59-389f-46f5-a5df-4eeac0040aa8
description: 'Resumen: Conozca la arquitectura híbrida y los escenarios de Microsoft basada en SaaS (Office 365) de las ofertas de nube.'
ms.openlocfilehash: 063cbd03a2cc65a6cd278ab2efcea235079f801b
ms.sourcegitcommit: 943d58b89459cd1edfc82e249c141d42dcf69641
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/01/2018
ms.locfileid: "27123417"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Escenarios de nube híbrida para Microsoft SaaS (Office 365)

 **Resumen:** Comprender la arquitectura híbrida y los escenarios de Microsoft basada en SaaS (Office 365) de las ofertas de nube.
  
Combine las implementaciones locales de Exchange, SharePoint o Skype Empresarial con sus equivalentes de Office 365 como parte de una migración a la nube o estrategia de integración a largo plazo.
  
## <a name="microsoft-saas-hybrid-scenario-architecture"></a>Arquitectura de escenario híbrido de SaaS de Microsoft

En la figura 1, se muestra la arquitectura de escenarios híbridos basados en SaaS de Microsoft para Office 365.
  
**Figura 1: Escenarios híbridos basados en SaaS de Microsoft para Office 365**

![Escenarios híbridos basados en SaaS de Microsoft para Office 365](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS.png)
  
Para cada capa de la arquitectura:
  
- Aplicaciones y escenarios
    
    Existe una gran variedad de escenarios híbridos basados en SaaS, que se alinean con los productos de Office Server y sus equivalentes de Office 365:
    
  - Exchange Server combinado con Exchange Online (Exchange Server híbrido)
    
  - Skype Empresarial Server combinado con Skype Empresarial Online y los nuevos escenarios PBX en la nube y Cloud Connector Edition
    
  - SharePoint Server 2019, 2016 de SharePoint Server o SharePoint Server 2013 combinadas con SharePoint Online (escenarios de varios)
    
    También existe Exchange Online con Skype Empresarial Server local, un escenario híbrido entre productos.
    
- Identidad
    
    Puede incluir la sincronización de directorios con Windows Server AD local. Como alternativa, puede configurar Azure AD para que se federe con un proveedor de identidades de terceros.
    
- Red
    
    Consta de la canalización de Internet existente o de una conexión de ExpressRoute con emparejamiento de Microsoft para Office 365 o Dynamics 365.
    
- Local
    
    Puede constar de los servidores existentes de Exchange, SharePoint y Skype Empresarial, que deberían estar actualizados a las versiones más recientes. Después, se pueden combinar con sus equivalentes de Office 365 para los escenarios híbridos.
    
Configurar su propio entorno de desarrollo y prueba de Office 365, consulte [Guías de laboratorio de prueba de Office 365](cloud-adoption-test-lab-guides-tlgs.md).
  
## <a name="skype-for-business-hybrid"></a>Skype para entornos híbridos de negocio

Skype para entornos híbridos de negocio le permite combinar una implementación local existente con Skype para profesionales en línea. Algunos usuarios son alojarse en local y algunos usuarios están hospedados en línea, pero los usuarios comparten el mismo dominio de protocolo de inicio de sesión (SIP), por ejemplo, contoso.com. Puede usar esta configuración híbrida para migrar de local a Office 365 con el tiempo, en la programación. También se puede integrar Skype para la empresa con [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).
  
**La figura 2: Skype para la configuración híbrida de negocio**

![El Skype para la configuración híbrida de negocio](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
La figura 2 muestra la Skype para la configuración híbrida de negocio, formado por un Skype local para el grupo de servidores de negocio front-end y servidor perimetral comunicarse con Skype para profesionales en línea en Office 365.
  
Para obtener más información, consulte [Plan de conectividad híbrida entre Skype para Business Server y Skype para profesionales en línea](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>PBX en la nube con Skype Empresarial Server

En la nube PBX con Skype para Business Server le permite realizar la transición de un Skype existente para su implementación local Business Server en una topología con conectividad de red de teléfono de conmutada pública (RTC) local. 
  
**Figura 3: PBX en la nube con Skype Empresarial Server**

![PBX en la nube con Skype Empresarial Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
La figura 3 muestra la PBX en la nube con Skype para la configuración de servidor de negocio, que consta de un sistema PBX existente o puerta de enlace de telecomunicaciones, un Skype para Business Server y la RTC conectado a la PBX de nube de Microsoft en Office 365, que incluye Skype para la empresa-locales En línea.
  
Los usuarios de la organización alojados en la nube pueden recibir servicios de central de conmutación (PBX) de la nube de Microsoft, que incluyen señalización y correo de voz, pero la conectividad RTC (tono de marcado) se proporciona a través de la Telefonía IP empresarial desde la implementación de Skype Empresarial Server local.
  
Esto es un buen ejemplo de una configuración híbrida que le permite migrar gradualmente a un servicio basado en la nube. Puede conservar las capacidades de voz de los usuarios cuando comienza a mover a Skype para profesionales en línea. Puede mover los usuarios a su propio ritmo, sabiendo que sus características de voz seguirán no materia donde están hospedados. 
  
Para obtener más información, consulte [Plan de conectividad híbrida entre Skype para Business Server y Skype para profesionales en línea](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
  
Si aún no tiene ninguna implementación de Lync Server o Skype Empresarial Server, puede usar Skype Empresarial Cloud Connector Edition, un conjunto de máquinas virtuales (VM) empaquetadas que implementan la conectividad RTC local con PBX en la nube.
  
Para obtener más información, consulte [Plan de Skype para Business Edition de conector en la nube](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

  
## <a name="sharepoint-hybrid"></a>Entorno híbrido de SharePoint

SharePoint híbrido combina SharePoint Online en Office 365 con su granja de SharePoint local para ofrecer la mejor experiencia conectada de ambos mundos.
  
**Figura 4: La configuración híbrida de SharePoint**

![La configuración híbrida de SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
La figura 4 muestra la configuración híbrida de SharePoint, que consta de una granja de servidores de SharePoint local comunicarse con SharePoint Online en Office 365.
  
Escenarios híbridos de SharePoint:
  
- [OneDrive para la Empresa híbrido](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [B2B Extranet híbrida](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Búsqueda híbrida](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [Perfiles híbridos](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [Selector de híbrido](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    Es fácil habilitar escenarios híbridos mediante asistentes que automatizan la configuración híbrida, disponible desde el Centro de administración de SharePoint Online en Office 365.
    
- [Iniciador de aplicaciones híbrido extensible](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    Permite a los usuarios ver y usar las aplicaciones y experiencias de Office 365 Video y Delve en las páginas de su granja de SharePoint local.
    
Todos estos escenarios híbridos de SharePoint, excepto el iniciador de aplicaciones híbrido extensible, están disponibles para los usuarios de SharePoint 2016 y SharePoint 2013.
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 híbrido

Con Exchange Server 2016 híbrido, puede materializar los beneficios de Exchange Online en Office 365 para los usuarios en línea mientras los usuarios locales siguen usando la infraestructura existente de Exchange Server.  
  
**Figura 5: La configuración híbrida de Exchange 2016**

![La configuración híbrida de Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
La figura 5 muestra la configuración híbrida de Exchange 2016, formado por los servidores de buzón de correo de Exchange locales comunicarse con Exchange Online Protection y buzones de correo en Office 365.
  
Algunos usuarios tienen un servidor de correo local y otros usan Exchange Online, pero todos comparten el mismo espacio de direcciones de correo.  
  
Esta configuración híbrida:
  
- Aprovecha la infraestructura existente de Exchange Server durante la migración a Exchange Online con el tiempo, según su programación.



    
- Permite admitir sitios remotos sin invertir en infraestructura de sucursales.
    
- Permite enrutar el correo electrónico entrante de Internet a través de Exchange Online Protection en Office 365.
    
- Satisface las necesidades de organizaciones multinacionales con subsidiarias que necesitan que los datos residan localmente.
    
También puede integrar esta configuración híbrida con otras aplicaciones de Microsoft Office 365, como Skype Empresarial Online y SharePoint Online.
  
Para obtener más información, vea [Implementaciones híbridas de Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).
  
## <a name="see-also"></a>Vea también

[Microsoft Hybrid Cloud para arquitectos profesionales](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

