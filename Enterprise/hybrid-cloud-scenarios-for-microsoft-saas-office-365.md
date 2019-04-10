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
description: 'Resumen: comprenda la arquitectura y los escenarios híbridos de las ofertas de la nube basadas en SaaS de Microsoft (Office 365).'
ms.openlocfilehash: 90b751e4bbea42d723961eb2ac339d23faf8c259
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741396"
---
# <a name="hybrid-cloud-scenarios-for-microsoft-saas-office-365"></a>Escenarios de nube híbrida para Microsoft SaaS (Office 365)

 **Resumen:** Comprenda la arquitectura y los escenarios híbridos de las ofertas de la nube basadas en SaaS de Microsoft (Office 365).
  
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
    
  - SharePoint Server 2019, SharePoint Server 2016 o SharePoint Server 2013 combinado con SharePoint Online (varios escenarios)
    
    También existe Exchange Online con Skype Empresarial Server local, un escenario híbrido entre productos.
    
- Identidad
    
    Puede incluir la sincronización de directorios con los servicios de dominio de Active Directory (AD DS) locales. Como alternativa, puede configurar Azure AD para que se federe con un proveedor de identidades de terceros.
    
- Red
    
    Consta de la canalización de Internet existente o de una conexión de ExpressRoute con emparejamiento de Microsoft para Office 365 o Dynamics 365.
    
- Local
    
    Puede constar de los servidores existentes de Exchange, SharePoint y Skype Empresarial, que deberían estar actualizados a las versiones más recientes. Después, se pueden combinar con sus equivalentes de Office 365 para los escenarios híbridos.
    
Configurar su propio entorno de pruebas y desarrollo de Office 365, consulte las [guías del laboratorio de pruebas de office 365](cloud-adoption-test-lab-guides-tlgs.md).
  
## <a name="skype-for-business-hybrid"></a>Skype empresarial híbrido

Skype empresarial híbrido le permite combinar una implementación local existente con Skype empresarial online. Algunos usuarios se alojan de forma local y otros en línea, pero todos comparten el mismo dominio de Protocolo de inicio de sesión (SIP) como, por ejemplo, contoso.com. Puede usar esta configuración híbrida para la migración de local a Office 365 con el tiempo, según su programación. Skype empresarial también se puede integrar con [Exchange Online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/integration-with-exchange-and-sharepoint).
  
**Figura 2: la configuración híbrida de Skype empresarial**

![La configuración híbrida de Skype empresarial](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB.png)
  
En la figura 2, se muestra la configuración híbrida de Skype empresarial, que consta de un grupo de servidores front-end local de Skype empresarial y un servidor perimetral que se comunica con Skype empresarial online en Office 365.
  
Para obtener más información, consulte [planear la conectividad híbrida entre Skype empresarial Server y Skype empresarial online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
    
## <a name="cloud-pbx-with-skype-for-business-server"></a>PBX en la nube con Skype Empresarial Server

PBX en la nube con Skype empresarial Server le permite realizar la transición de una implementación local de Skype empresarial Server existente a una topología con conectividad de red telefónica conMutada (RTC) local. 
  
**Figura 3: PBX en la nube con Skype Empresarial Server**

![PBX en la nube con Skype Empresarial Server](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SfB-CloudPBX.png)
  
En la figura 3 se muestra la PBX en la nube con la configuración de Skype empresarial Server, que consta de una puerta de enlace de telecomunicaciones o PBX local existente, un servidor de Skype empresarial Server y la RTC conectada al PBX en la nube de Microsoft en Office 365, que incluye Skype empresarial Online.
  
Los usuarios de la organización alojados en la nube pueden recibir servicios de central de conmutación (PBX) de la nube de Microsoft, que incluyen señalización y correo de voz, pero la conectividad RTC (tono de marcado) se proporciona a través de la Telefonía IP empresarial desde la implementación de Skype Empresarial Server local.
  
Este es un buen ejemplo de una configuración híbrida que permite migrar gradualmente a un servicio basado en la nube. Puede conservar las capacidades de voz de los usuarios al comenzar a moverlos a Skype Empresarial Online. Puede mover los usuarios a su propio ritmo, con la seguridad de que sus características de voz seguirán sin importar dónde se alojen. 
  
Para obtener más información, consulte [planear la conectividad híbrida entre Skype empresarial Server y Skype empresarial online](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-hybrid-connectivity).
  
Si aún no tiene ninguna implementación de Lync Server o Skype Empresarial Server, puede usar Skype Empresarial Cloud Connector Edition, un conjunto de máquinas virtuales (VM) empaquetadas que implementan la conectividad RTC local con PBX en la nube.
  
Para obtener más información, consulte [Plan for Skype for Business Cloud Connector Edition](https://docs.microsoft.com/skypeforbusiness/skype-for-business-hybrid-solutions/plan-your-phone-system-cloud-pbx-solution/plan-skype-for-business-cloud-connector-edition).

  
## <a name="sharepoint-hybrid"></a>Entorno híbrido de SharePoint

SharePoint híbrido combina SharePoint Online en Office 365 con su granja de SharePoint local para ofrecer la mejor experiencia conectada de ambos mundos.
  
**Figura 4: La configuración híbrida de SharePoint**

![La configuración híbrida de SharePoint](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-SP.png)
  
La figura 4 muestra la configuración híbrida de SharePoint, que consta de una granja de SharePoint local que se comunica con SharePoint Online en Office 365.
  
Escenarios híbridos de SharePoint:
  
- [OneDrive para la Empresa híbrido](https://docs.microsoft.com/SharePoint/hybrid/configure-hybrid-onedrive-for-businessroadmap)
    
- [B2B de extranet híbrida](https://docs.microsoft.com/sharepoint/create-b2b-extranet)
    
- [Búsqueda híbrida](https://docs.microsoft.com/SharePoint/hybrid/configure-cloud-hybrid-searchroadmap)
    
- [Perfiles híbridos](https://docs.microsoft.com/SharePoint/hybrid/plan-hybrid-profiles)
    
- [Selector híbrido](https://docs.microsoft.com/SharePoint/hybrid/hybrid-picker-in-the-sharepoint-online-admin-center)
    
    Es fácil habilitar escenarios híbridos mediante asistentes que automatizan la configuración híbrida, disponible desde el Centro de administración de SharePoint Online en Office 365.
    
- [Iniciador de aplicaciones híbrido extensible](https://docs.microsoft.com/SharePoint/hybrid/the-extensible-hybrid-app-launcher)
    
    Permite a los usuarios ver y usar las aplicaciones y experiencias de Office 365 Video y Delve en las páginas de su granja de SharePoint local.
    
Todos estos escenarios híbridos de SharePoint, excepto el iniciador de aplicaciones híbrido extensible, están disponibles para los usuarios de SharePoint 2016 y SharePoint 2013.
  
## <a name="exchange-server-2016-hybrid"></a>Exchange Server 2016 híbrido

Con Exchange Server 2016 híbrido, puede materializar los beneficios de Exchange Online en Office 365 para los usuarios en línea mientras los usuarios locales siguen usando la infraestructura existente de Exchange Server.  
  
**Figura 5: La configuración híbrida de Exchange 2016**

![La configuración híbrida de Exchange 2016](media/Hybrid-Poster/Hybrid-Cloud-Stack-SaaS-EX.png)
  
La figura 5 muestra la configuración híbrida de Exchange 2016, que consta de los servidores de buzones de correo de Exchange locales que se comunican con la protección en línea de Exchange y los buzones en Office 365.
  
Algunos usuarios tienen un servidor de correo local y otros usan Exchange Online, pero todos comparten el mismo espacio de direcciones de correo.  
  
Esta configuración híbrida:
  
- Aprovecha la infraestructura existente de Exchange Server durante la migración a Exchange Online con el tiempo, según su programación.
    
- Permite admitir sitios remotos sin invertir en infraestructura de sucursales.
    
- Permite enrutar el correo electrónico entrante de Internet a través de Exchange Online Protection en Office 365.
    
- Satisface las necesidades de organizaciones multinacionales con subsidiarias que necesitan que los datos residan localmente.
    
También puede integrar esta configuración híbrida con otras aplicaciones de Microsoft Office 365, como Skype Empresarial Online y SharePoint Online.
  
Para obtener más información, consulte implementaciones híbridas de [Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid).
  
## <a name="see-also"></a>Vea también

[Microsoft Hybrid Cloud para arquitectos profesionales](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

