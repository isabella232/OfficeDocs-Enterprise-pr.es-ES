---
title: Integración de Azure con Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/09/2019
audience: Admin
ms.topic: overview
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Ent_O365
- M365-identity-device-management
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- MED150
- BCS160
ms.assetid: a5efce5d-9c9c-4190-b61b-fd273c1d425f
description: Su suscripción a Office 365 incluye una suscripción a Azure AD. Integre Office 365 con Azure AD si desea la sincronización de contraseña o el inicio de sesión único con el entorno local.
ms.openlocfilehash: 44231420ee92c37f14874d6fb0f9e926d8d4369d
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "38745793"
---
# <a name="azure-integration-with-office-365"></a>Integración de Azure con Office 365

*Este artículo se aplica tanto a Office 365 Enterprise como a Microsoft 365 Enterprise.*

Office 365 usa Azure Active Directory (Azure AD) para administrar las identidades de usuario en segundo plano. Su suscripción a Office 365 incluye una suscripción gratuita a Azure AD para que pueda integrar Office 365 con Azure AD si desea sincronizar contraseñas o configurar el inicio de sesión único con su entorno local. También puede comprar características avanzadas para administrar mejor sus cuentas.
  
Azure también ofrece otras funciones, como la administración de aplicaciones integradas, que puede usar para ampliar y personalizar sus suscripciones a Office 365.
  
Puede usar los asesores de implementación de Azure AD para una instalación guiada y una experiencia de configuración (debe haber iniciado sesión en Office 365):

 - [Azure AD Connect Advisor](https://aka.ms/aadconnectpwsync)
 - [Asesor de implementación de AD FS](https://aka.ms/adfsguidance)
 - [Guía de instalación de Azure AD Premium](https://aka.ms/aadpguidance)
  
## <a name="azure-ad-editions-and-office-365-identity-management"></a>Azure AD Editions y Office 365 Identity Management

Si tiene una suscripción de pago a Office 365, también tiene una suscripción gratuita a Azure AD. Puede usar Azure AD para crear y administrar cuentas de grupo y de usuario. Para activar esta suscripción tiene que completar un registro único. Después, puede tener acceso a Azure AD desde el portal de administración de Office 365. 

Para obtener instrucciones, consulte [usar la suscripción gratuita de Azure ad](https://go.microsoft.com/fwlink/p/?LinkId=617127). Siga las instrucciones para registrar la suscripción gratuita a Azure AD que se incluye con su suscripción a Office 365. No vaya directamente a azure.microsoft.com para registrarse o termine con una suscripción de prueba o de pago a Microsoft Azure que es independiente de su versión gratuita de una para Office 365. 
  
Con la suscripción gratuita, puede sincronizar con directorios locales, configurar el inicio de sesión único y sincronizar con muchos software como aplicaciones de servicio, como Salesforce, DropBox y muchos más.
  
Si desea la funcionalidad mejorada de servicios de dominio de Active Directory (AD DS), sincronización bidireccional y otras capacidades de administración, puede actualizar su suscripción gratuita a una suscripción Premium de pago. Para obtener información detallada, consulte [Azure Active Directory Editions](https://azure.microsoft.com/pricing/details/active-directory/).
  
Para obtener más información sobre Office 365 y Azure AD, consulte [Understanding office 365 Identity and Azure Active Directory](https://docs.microsoft.com/office365/enterprise/about-office-365-identity).
  
## <a name="extend-the-capabilities-of-your-office-365-tenant"></a>Ampliar las capacidades de su inquilino de Office 365

|**Característica**|**Descripción**|
|:-----|:-----|
|Aplicaciones integradas  <br/> |Puede conceder acceso a aplicaciones individuales a los datos de Office 365, como correo, calendarios, contactos, usuarios, grupos, archivos y carpetas. También puede autorizar estas aplicaciones en el nivel de administrador global y ponerlas a disposición de toda la empresa registrando las aplicaciones en Azure AD. Para obtener información detallada [, vea aplicaciones integradas y Azure ad para administradores de Office 365](https://support.office.com/article/cb2250e3-451e-416f-bf4e-363549652c2a).  <br/> Consulte también [el inicio de sesión único para las aplicaciones](https://go.microsoft.com/fwlink/p/?LinkId=698604).  <br/> |
|PowerApps  <br/> | Las aplicaciones Power se centran en aplicaciones para dispositivos móviles que se pueden conectar a los orígenes de datos existentes, como las listas de SharePoint y otras aplicaciones de datos. Consulte [Create a PowerApp for a List in SharePoint Online](https://support.office.com/article/9338b2d2-67ac-4b81-8e67-97da27e5e9ab) and [PowerApps Page](https://powerapps.microsoft.com/) for details.  <br/> |
   
Para obtener más información [, vea aplicaciones integradas y Azure ad para Office 365 administradores](integrated-apps-and-azure-ads.md) y la [Galería de aplicaciones de Azure ad y el inicio de sesión único](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-single-sign-on).

## <a name="see-also"></a>Vea también

[Información general de Microsoft 365 Enterprise](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview)
