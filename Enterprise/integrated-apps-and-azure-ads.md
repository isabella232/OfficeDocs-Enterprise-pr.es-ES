---
title: Aplicaciones integradas y Azure AD para administradores de Office 365
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 3/5/2018
ms.audience: Admin
ms.topic: hub-page
ms.service: o365-administration
localization_priority: Normal
ms.custom: Adm_O365
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: cb2250e3-451e-416f-bf4e-363549652c2a
description: Obtenga información sobre cómo O365 integrar aplicaciones están registrados y administrarse en Azure AD
ms.openlocfilehash: 0482271f15dc5e2b81e36fd265b49da6eba18702
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915005"
---
# <a name="integrated-apps-and-azure-ad-for-office-365-administrators"></a>Aplicaciones integradas y Azure AD para administradores de Office 365

No hay más a la administración de aplicaciones integradas que acaba de [Aplicaciones integrado de activar o desactivar](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114). Con la llegada de las API de REST de Office 365, los usuarios pueden otorgar acceso de aplicaciones a sus datos de Office 365, como correo, calendarios, contactos, los usuarios, grupos, archivos y carpetas. De forma predeterminada, los usuarios necesitan conceder permisos para cada aplicación de forma individual, pero esto no se escala bien si desea autorizar a una aplicación una vez en el nivel de administrador global y desplegar a toda la organización a través del iniciador de la aplicación. Para ello, debe registrar la aplicación en Azure AD. Existen algunos pasos que debe tomar antes de que se puede registrar una aplicación en Azure AD y algunos información de fondo debe conocer que le ayudan a administrar las aplicaciones en la organización de Office 365. En este artículo le dirige a esos recursos.
  
## <a name="azure-ad-resources-for-office-365-admins"></a>Recursos de Azure AD para los administradores de Office 365

Tiene que hacer estos dos procedimientos antes de poder administrar las aplicaciones de Office 365 en Azure AD.
  
|**Requisitos previos**|**Comentarios**|
|:-----|:-----|
|[Registre su suscripción gratuita de Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617127) <br/> |Cada suscripción de pago a Office 365 incluye una suscripción gratuita a Azure Active Directory. Puede usar Azure AD para administrar sus aplicaciones y para crear y administrar cuentas de usuario y grupo. Para activar esta suscripción y obtener acceso al portal de administración de Azure, debe completar un proceso de registro único. Posteriormente, puede ir a Azure AD desde el centro de administración de Office 365.  <br/> |
|[Activar o desactivar la aplicaciones integrada](https://support.office.com/article/7e453a40-66df-44ab-92a1-96786cb7fb34#__toc379982114) <br/> |Debe activar aplicaciones integrada para los usuarios permitir que las aplicaciones de terceros tener acceso a su información de Office 365 y para registrar aplicaciones en Azure AD. Por ejemplo, cuando alguien utiliza una aplicación de terceros, es posible que pedir esa aplicación permiso para tener acceso a su calendario y para editar los archivos que se encuentran en un OneDrive para la carpeta Business.  <br/> |
   
Administración de aplicaciones de Office 365 requiere tener conocimientos de las aplicaciones de Azure AD. Estos artículos le ayudarán a la información que necesaria.
  
|**Artículo de fondo**|**Comentarios**|
|:-----|:-----|
|[Cumplir el iniciador de la aplicación de Office 365](https://support.office.com/article/79f12104-6fed-442f-96a0-eb089a3f476a) <br/> |Si está familiarizado con el iniciador de la aplicación, es posible que se pregunte qué es y cómo usarla. El iniciador de la aplicación está diseñado para que le ayudará a empezar a sus aplicaciones desde cualquier lugar en Office 365.  <br/> |
|[Agregar, actualizar y quitar una aplicación](https://go.microsoft.com/fwlink/?LinkId=617137) <br/> |En este tema se muestra cómo agregar, actualizar o quitar una aplicación en Azure Active Directory. Obtendrá información sobre los diferentes tipos de aplicaciones que se pueden integrar con Azure AD y cómo configurar las aplicaciones para tener acceso a otros recursos, como las API de web y mucho más.  <br/> |
|[Tiene la aplicación aparecen en el selector de la aplicación de Office 365](https://go.microsoft.com/fwlink/?LinkId=617138).  <br/> |El iniciador de aplicación en Office 365 que facilita a los usuarios encontrar y tener acceso a sus aplicaciones. En este artículo se describe las formas como un desarrollador puede obtener las aplicaciones que aparecen en los iniciadores de aplicación de los usuarios y también proporcionar una experiencia de inicio de sesión único (SSO) usando sus credenciales de Office 365.  <br/> |
|[Introducción a la plataforma de API de Office 365](https://go.microsoft.com/fwlink/?LinkId=617140) <br/> |Las API de Office 365 le permite proporcionar acceso a los datos de su cliente Office 365, incluidas las cosas que más les interesan: su correo, calendarios, contactos, los usuarios y grupos, archivos y carpetas. En este artículo que se muestra la relación entre las aplicaciones de Office 365, Azure AD, no hay un diagrama de buena y los datos que tienen acceso las aplicaciones.  <br/> |
|[Integración de aplicaciones en Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617141) <br/> | Obtenga información sobre las aplicaciones que se integran con Azure Active Directory y cómo registrar la aplicación, comprender los conceptos subyacentes a una aplicación registrada y obtenga información acerca de la personalización de marca directrices para múltiples aplicaciones de inquilinos.  <br/> |
|[Tutoriales de integración de Azure Active Directory](https://go.microsoft.com/fwlink/?LinkId=617144) <br/> |El objetivo de estos tutoriales es mostrar cómo configurar SSO de AD de Azure para las aplicaciones SaaS de terceros.  <br/> |
|[Escenarios de autenticación para Azure AD](https://go.microsoft.com/fwlink/?LinkId=617145) <br/> |Azure AD simplifica la autenticación para los desarrolladores proporcionando identidad como un servicio, con la compatibilidad con protocolos estándar del sector como OAuth 2.0 y OpenID conectarse, así como abrir bibliotecas de origen para distintas plataformas que le ayudarán a comenzar a codificar más rápidamente. Este documento le ayudará a comprender los distintos escenarios de Azure AD admite y muestra cómo empezar a usar.  <br/> |
|[Acceso a la aplicación](https://go.microsoft.com/fwlink/?LinkId=617146) <br/> |Azure AD permite una integración más fácil a muchas de software más populares de hoy en día como en el caso de las aplicaciones de servicio (SaaS); Proporciona una administración de identidades y acceso, y ofrece un Panel de acceso para los usuarios dónde pueden descubrir qué acceso de la aplicación que tienen y de que puedan usar SSO para tener acceso a sus aplicaciones. Este artículo proporciona vínculos a los recursos relacionados que le permiten obtener más información sobre las mejoras de acceso de la aplicación para Azure AD y cómo pueden contribuir a ellos.  <br/> |
|[Agregar o quitar fichas en el iniciador de la aplicación de Office 365](https://support.office.com/article/0b71362d-ce56-4d21-9b2f-bdb750a82b81) <br/> |Puede obtener acceso rápido a las aplicaciones que usan todos los días mediante la adición o eliminación de aplicaciones en el selector de la aplicación de Office 365.  <br/> |
   

