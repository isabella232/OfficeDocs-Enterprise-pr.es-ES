---
title: Aplicaciones integradas y Azure AD para administradores de Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
f1.keywords:
- CSH
ms.custom: Adm_O365
ms.collection: M365-subscription-management
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Obtenga información sobre cómo las aplicaciones integradas de O365 se registran y administran en Azure AD
ms.openlocfilehash: 0cb3ac73230e0ddce62366af9019a12ea2b04d09
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998095"
---
# <a name="integrated-apps-and-azure-ad-for-microsoft-365-administrators"></a>Aplicaciones integradas y Azure AD para administradores de Microsoft 365

Hay más información sobre la administración de aplicaciones integradas que la [activación o desactivación de las aplicaciones integradas](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114). Con la llegada de las API de REST de 365 de Microsoft, los usuarios pueden conceder acceso a las aplicaciones a sus datos de 365 de Microsoft, como correo, calendarios, contactos, usuarios, grupos, archivos y carpetas. De forma predeterminada, los usuarios deben conceder permisos individualmente para cada aplicación, pero esto no se escalará correctamente si desea autorizar una aplicación una vez en el nivel de administrador global y implementarla en toda la organización mediante el iniciador de aplicaciones. Para ello, debe registrar la aplicación en Azure AD. Hay algunos pasos que debe tener en cuenta antes de poder registrar una aplicación en Azure AD y la información básica que necesita saber que puede ayudarle a administrar las aplicaciones de su organización de Microsoft 365. Este artículo le dirige a esos recursos.
  
## <a name="azure-ad-resources-for-microsoft-365-admins"></a>Recursos de Azure AD para administradores de Microsoft 365

Debe realizar estos dos procedimientos para poder administrar las aplicaciones de Microsoft 365 en Azure AD.
  
|**Requisitos previos**|**Comments**|
|:-----|:-----|
|[Usar su suscripción gratuita de Azure Active Directory](https://docs.microsoft.com/microsoft-365/compliance/use-your-free-azure-ad-subscription-in-office-365) <br/> |Todas las suscripciones de pago a Microsoft 365 incluyen una suscripción gratuita a Azure Active Directory (Azure AD). Puede usar Azure AD para administrar las aplicaciones y para crear y administrar cuentas de usuario y de grupo. Para usar Azure AD, solo tiene que ir a Azure portal e iniciar sesión con su cuenta de Microsoft 365.  <br/> |
|[Activar o desactivar las aplicaciones integradas](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Debe activar las aplicaciones integradas para que los usuarios puedan permitir que las aplicaciones de terceros accedan a la información de Microsoft 365 y para registrar aplicaciones en Azure AD. Por ejemplo, cuando alguien usa una aplicación de terceros, es posible que esa aplicación le pida permiso para obtener acceso a su calendario y editar los archivos que se encuentran en una carpeta de OneDrive para la empresa.  <br/> |
   
Para administrar las aplicaciones de 365 de Microsoft, es necesario tener conocimientos de las aplicaciones en Azure AD. Estos artículos le proporcionan el fondo que necesita.
  
|**Artículo de segundo plano**|**Comments**|
|:-----|:-----|
|[Conozca el iniciador de aplicaciones de 365 de Microsoft](https://support.microsoft.com/office/meet-the-microsoft-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Si no está familiarizado con el iniciador de aplicaciones, es posible que se pregunte qué es y cómo usarlo. El iniciador de aplicaciones está diseñado para ayudarle a acceder a sus aplicaciones desde cualquier lugar en Microsoft 365.  <br/> |
|[Información general de las API de administración de Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-apis-overview) <br/> |Las API de 365 de Microsoft permiten proporcionar acceso a los datos de Microsoft 365, incluidos los aspectos que les interesan de la mayoría: el correo, los calendarios, los contactos, los usuarios y grupos, los archivos y las carpetas. Hay un buen diagrama en este artículo que ilustra la relación entre las aplicaciones de Microsoft 365, Azure AD y los datos a los que acceden las aplicaciones.  <br/> |
|[Integración de aplicaciones en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/develop/quickstart-v1-add-azure-ad-app) <br/> | Obtenga información sobre las aplicaciones que se integran con Azure AD y cómo registrar la aplicación, comprender los conceptos de una aplicación registrada y obtener información sobre las pautas de personalización de marca para las aplicaciones multiempresa.  <br/> |
|[Agregar mosaicos personalizados al iniciador de aplicaciones](https://docs.microsoft.com/office365/admin/manage/customize-the-app-launcher)  <br/> |El iniciador de aplicaciones de Microsoft 365 facilita a los usuarios la búsqueda y el acceso a sus aplicaciones. En este artículo se describen las formas en las que el desarrollador puede hacer que las aplicaciones aparezcan en los iniciadores de aplicaciones de los usuarios y darles una experiencia de inicio de sesión único (SSO) mediante sus credenciales de Microsoft 365.  <br/> |
|[Tutoriales de integración de Azure Active Directory](https://docs.microsoft.com/azure/active-directory/saas-apps/tutorial-list) <br/> |El objetivo de estos tutoriales es mostrarle cómo configurar el SSO de Azure AD para las aplicaciones SaaS de terceros.  <br/> |
|[Escenarios de autenticación de Azure AD](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD simplifica la autenticación para los desarrolladores al proporcionar identidad como un servicio, con compatibilidad para protocolos estándar de la industria como OAuth 2,0 y OpenID Connect, así como bibliotecas de código abierto para diferentes plataformas que le ayudarán a empezar a codificar rápidamente. Este documento le ayuda a comprender los diversos escenarios que Azure AD admite y le muestra cómo empezar.  <br/> |
|[Acceso a la aplicación](https://docs.microsoft.com/azure/active-directory/manage-apps/what-is-access-management) <br/> |Azure AD permite una integración sencilla con muchas de las aplicaciones de software de hoy en día (SaaS) más conocidas; proporciona administración de identidades y acceso, y ofrece un panel de acceso para los usuarios donde pueden descubrir qué acceso a la aplicación tienen y dónde pueden usar SSO para obtener acceso a sus aplicaciones. En este artículo se proporcionan vínculos a los recursos relacionados que le permiten obtener más información sobre las mejoras de acceso a la aplicación para Azure AD y cómo puede contribuir a ellas.  <br/> |
|[Personalizar su experiencia de Office 365](https://support.office.com/article/eb34a21b-52fa-4fbf-a8d5-146132242985) <br/> |Puede obtener acceso rápido a las aplicaciones que usa cada día si agrega o quita aplicaciones en el iniciador de aplicaciones de Microsoft 365.  <br/> |
   

