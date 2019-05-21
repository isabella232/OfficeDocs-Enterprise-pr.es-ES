---
title: Planeación de Office 365 Enterprise
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-subscription-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 712fced7-f9d0-4fde-8b79-286262a5d0bc
description: Obtenga acceso a los recursos para planear la implementación empresarial de Office 365.
ms.openlocfilehash: 29510c6e3df5dfd6064b6e7e96e236e4bd8c0c47
ms.sourcegitcommit: 2a7177c666dce3c00462b97463a6855e9e3a81f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/20/2019
ms.locfileid: "34249478"
---
# <a name="plan-for-office-365-enterprise"></a>Planeación de Office 365 Enterprise

Al mover una organización empresarial a Office 365, es importante planear con antelación y tomar las decisiones de diseño clave que optimizarán la implementación de ti y la adopción de usuarios. 

## <a name="planning-with-office-365-fasttrack"></a>Planeación con Office 365 FastTrack

[FastTrack para Office 365](https://docs.microsoft.com/fasttrack/O365-fasttrack-benefit-for-office-365) es el mejor método para obtener ayuda de Microsoft para planear la implementación de Office 365. FastTrack puede ayudarle a través de las consideraciones de diseño más comunes y puede responder a preguntas durante el proceso. 

>[!Note]
>También puede obtener ayuda de un [socio de Microsoft](https://www.microsoft.com/solution-providers/home).
>

## <a name="do-it-yourself-planning-for-office-365"></a>Realice una planificación para Office 365

Para planificar Office 365 por su cuenta, determine las decisiones de diseño correctas para estas áreas:

- Su inquilino de Office 365

  Incluye la planeación de las conexiones de red a Internet, las identidades de Office 365 y la integración con aplicaciones, local, Azure y otros elementos. Empiece [aquí](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).

- Compatibilidad con los clientes

  Incluye la autenticación basada en certificados, la administración de dispositivos móviles, las opciones de autenticación y la colaboración entre espacios empresariales. Empiece [aquí](office-365-client-support-certificate-based-authentication.md).

- Compatibilidad con la autenticación moderna híbrida

  Incluye la planeación de la autenticación moderna cuando se usan configuraciones híbridas de las cargas de trabajo de la clave de Office 365. Empiece [aquí](hybrid-modern-auth-overview.md).

- Clientes y servidores antiguos de Office

  Incluye información de migración para los productos de cliente y servidor de Office 2007 y Office 2010. Empiece [aquí](plan-upgrade-previous-versions-office.md).

También puede iniciar sesión en su suscripción y usar los [asesores de implementación para los servicios de Office 365](deployment-advisors-for-office-365.md).


<!--

This checklist will help your organization as you plan and prepare for a migration to Office 365. The phases and steps in the checklist are aligned with the guidance provided by the [Onboarding Center](https://go.microsoft.com/fwlink/?LinkId=517115). Feel free to adapt this checklist to your organization's needs.

Most organizations don't need to do anything to prepare for Office 365. It's an application on the web and people are able to use it as soon as they have an account. Other organizations have more locations, security practices, or other requirements that create the need for more planning. For enterprise-level organizations, follow the checklist items below to get started with Office 365.
  
If you want help getting Office 365 set up, [FastTrack](https://fasttrack.microsoft.com/office) is the easiest way to deploy Office 365, you can also sign in and use the [Deployment advisors for Office 365 services](deployment-advisors-for-office-365.md).
  
|**Choose one or more to get started:**||
|:-----|:-----|
| [System requirements for Office](https://products.office.com/office-system-requirements) |- Microsoft Office Professional, Office 365, Office 365 ProPlus, and each Office application for Windows, Mac, iOS, and Android all have specific system requirements. Ensure your hardware and software meet the minimum system requirements.|
|**Most** customers connect their on-premises directory to Office 365. Get a head start on directory preparation by [installing and running IdFix on your network](https://www.microsoft.com/download/details.aspx?id=36832). <br> Use the [AAD Connect advisor](https://aka.ms/aadconnectpwsync) and the [Azure AD Premium set up guide](https://aka.ms/aadpguidance) to get customized set up guidance. <br> |- Automated checks against your directory to [validate people's accounts will properly synchronize](https://support.office.com/article/Prepare-to-provision-users-through-directory-synchronization-to-Office-365-01920974-9e6f-4331-a370-13aea4e82b3e). <br> - Recommends changes to directory objects and offers to automate the changes for you. <br> - [More details on using the IdFix tool](prepare-directory-attributes-for-synch-with-idfix.md). |
|**Read** our [network performance guidance](https://aka.ms/tune) and use our tools to ensure you have the connectivity and performance configuration necessary to provide people with the best experience.  <br> | - Ensure you can connect to Office 365, if you filter or scan outbound traffic, you'll want to understand what [managing Office 365 endpoints](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a) means for your organization.  <br>  - [Model and test your network capacity](https://support.office.com/article/Network-and-migration-planning-for-Office-365-f5ee6c33-bcd7-4b0b-b0f8-dc1d9fb8d132) or move to an [Azure ExpressRoute for Office 365](https://support.office.com/article/Azure-ExpressRoute-for-Office-365-6d2534a2-c19c-4a99-be5e-33a0cee5d3bd) circuit for a more predictable experience.   |
|**Use** our [planning checklist](https://support.office.com/article/Deployment-planning-checklist-for-Office-365-5fa4f6ef-35ad-4840-91c1-4834df3df5a0) as a starting place for building your own deployment plan.  <br> | - In-depth overview of possible areas you'll need to plan for with links to reference or how-to information to help you plan. |
|**Use** the [Exchange Server Large Item Script](https://gallery.technet.microsoft.com/Exchange-Server-Large-Item-b9546cc6) to find mail items that may be too large to migrate.  <br> | - Uses Exchange Web Services to impersonate, access, scan the mailbox for file sizes you specify, and dumps the results in a CSV file. Read the [detailed instructions on how to use the script](https://blogs.technet.com/b/mikehall/archive/2013/06/27/large-mail-item-script.aspx). |
|**Take** advantage of [Microsoft deployment experts](https://go.microsoft.com/fwlink/?LinkId=517115) who can help you from planning to helping everyone start using the new services and applications.  <br> Use the [Deployment wizards for Office 365 services](https://support.office.com/article/Deployment-wizards-for-Office-365-services-165f46e8-3533-4d76-be57-97f81ebd40f2) to get customized set up guidance.  <br> | - The Onboarding center works directly with customers and with partner organizations. Give them a call today. |
|**Use** the [templates and resources in the Office 365 success center](https://www.microsoft.com/fasttrack/resources) to share your deployment and onboarding plans with the people in your organization.  <br> | - Communication with everyone before, during, and after the transition to Office 365 is critical.  <br> - Use our templates, guides, and handouts to improve your communications. |
|**Read** the article [Office 365 Network Connectivity Principles](https://aka.ms/o365networkingprinciples) to understand the connectivity principles for securely managing Office 365 traffic and getting the best possible performance.  <br> | - This article will help you understand the most recent guidance for securely optimizing Office 365 network connectivity. |
   
Want more resources to help you integrate Office 365 with your broader cloud strategy? Here are the [Microsoft cloud IT architecture resources](https://docs.microsoft.com/en-us/office365/enterprise/microsoft-cloud-it-architecture-resources).
  
## Want to talk with support?

We're here to help, [contact support](https://support.office.com/article/32a17ca7-6fa0-4870-8a8d-e25ba4ccfd4b) for business products.


--> 