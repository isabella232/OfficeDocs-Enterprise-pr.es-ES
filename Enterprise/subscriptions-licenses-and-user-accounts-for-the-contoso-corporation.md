---
title: Suscripciones, licencias y cuentas de usuario para Contoso Corporation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: ec3b08f0-288c-4ba3-b822-dbf6352fa761
description: 'Resumen: Conozca la estructura de las suscripciones de nube de Contoso, licencias, las cuentas de usuario y los inquilinos.'
ms.openlocfilehash: cd196e0800f6a39973f4c5c82001ed3e9c330fee
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915515"
---
# <a name="subscriptions-licenses-and-user-accounts-for-the-contoso-corporation"></a>Suscripciones, licencias y cuentas de usuario para Contoso Corporation

 **Resumen:** Comprender la estructura de las suscripciones de nube de Contoso, licencias, las cuentas de usuario y los inquilinos.
  
Para proporcionar un uso coherente de las identidades y la facturación para todas las ofertas de nube, Microsoft ofrece una jerarquía de cuentas de organización, suscripciones, licencias y usuario.
  
- Organización
    
    La entidad empresarial que usa las ofertas de nube de Microsoft, normalmente identificadas por un nombre de dominio DNS público, como contoso.com.
    
- Suscripciones
    
    Para Microsoft SaaS (Office 365, Intune/EMS y Dynamics 365) las ofertas de nube, una suscripción es un producto específico y un conjunto de adquirir licencias de usuario. Para Azure, una suscripción a permite la facturación de los servicios de nube consumido a la organización.
    
- Licencias
    
    Para las ofertas de nube de Microsoft SaaS, una licencia permite una cuenta de usuario específica usar servicios de nube. Para Azure, licencias de software se basan en precios de servicio, pero en algunos casos que necesitará comprar licencias de software adicional.
    
- Cuentas de usuario
    
    Las cuentas de usuario se almacenan en un inquilino de Azure AD y pueden sincronizarse desde un proveedor de identidades local como Windows Server AD.
    
## <a name="contosos-structure"></a>Estructura de Contoso

Contoso determinó la siguiente estructura para la organización y sus suscripciones, licencias, cuentas e inquilinos:
  
**Figura 1: La organización, suscripciones, licencias, cuentas de usuario e inquilinos de Contoso.**

![Organización, suscripciones, licencias, cuentas de usuario e inquilinos de Contoso](media/Contoso-Poster/Subscriptions.png)
  
La figura 1 muestra cómo la organización Contoso incluye varias suscripciones y está vinculada a un inquilino común de Azure AD que contiene las cuentas de usuario que se sincronizan desde el bosque de Windows Server AD de contoso.com.
  
- **Organización** Contoso Corporation se identifica por su nombre de dominio público contoso.com.
    
  - **Suscripciones y licencias** La empresa Contoso es usar lo siguiente:
    
  - El producto de Office 365 Enterprise E3 con 5.000 licencias
    
  - Producto Office 365 Enterprise E5 con 200 licencias
    
  - El producto EMS con 5.000 licencias
    
  - Producto Dynamics 365 con 100 licencias

    
  - Varias suscripciones de Azure según las regiones
    
  - **Cuentas de usuario** Un inquilino de Azure AD comunes contiene la lista de cuentas de usuario y grupos utilizan todas las suscripciones de Contoso, a excepción de desarrollo o prueba suscripciones de Azure.
    
Para los inquilinos de Contoso:
  
- Para las ofertas de nube de SaaS, el inquilino es la ubicación regional que hospeda los servidores que proporcionan servicios en la nube. Contoso eligió la región europea para el hospedaje de sus inquilinos de Office 365, EMS y Dynamics 365.
  
    
- Los servicios de PaaS Azure y aplicaciones y cargas de trabajo de TI de IaaS pueden tener arrendamiento en cualquier centro de datos de Azure en todo el mundo. Un inquilino de Azure AD es una instancia específica de Azure AD que contiene las cuentas y grupos.
    
- El inquilino de Azure AD comunes que contiene las cuentas sincronizadas para el bosque de Contoso Windows Server AD proporciona IDaaS a través de las ofertas de nube de Microsoft.
    
Para obtener más información, vea [las suscripciones, licencias y cuentas e inquilinos para las ofertas de nube de Microsoft](subscriptions-licenses-accounts-and-tenants-for-microsoft-cloud-offerings.md).
  
## <a name="contosos-azure-subscriptions"></a>Suscripciones de Azure de Contoso

La figura 2 muestra el diseño jerárquico de las suscripciones de Azure de Contoso: 



  
**Figura 2: Estructura de Contoso para las suscripciones de Azure**

![Estructura de Contoso para las suscripciones a Azure](media/Contoso-Poster/Subscriptions-Nested.png)
  
- Contoso está en la parte superior, de acuerdo con su Contrato Enterprise con Microsoft.
    
- Hay un conjunto de cuentas correspondiente a las diferentes regiones de Contoso Corporation todo el mundo, en función de los dominios del bosque de Windows Server AD de Contoso.
    
- Dentro de cada región, hay una o más suscripciones en función de las necesidades de implementación de desarrollo, prueba y producción de la región.
    
Cada suscripción de Azure puede asociarse a un solo inquilino de Azure AD que contenga cuentas de usuario y grupos para la autenticación y la autorización para los servicios de Azure. Las suscripciones de producción usan el inquilino de Azure AD común de Contoso.
  
## <a name="see-also"></a>See Also

[Contoso en la nube de Microsoft](contoso-in-the-microsoft-cloud.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)




