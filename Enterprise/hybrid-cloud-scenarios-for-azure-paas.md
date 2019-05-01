---
title: Escenarios de nube híbrida para Azure PaaS
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
ms.assetid: 5f4f5d0d-4638-48e8-a517-bd804856b617
description: 'Resumen: Comprenda la arquitectura y los escenarios híbridos de las ofertas de nubes basadas en Plataforma como servicio (PaaS) de Microsoft en Azure.'
ms.openlocfilehash: f4d90d51a7627063fae6fd168681bdf96cb4d6bc
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491216"
---
# <a name="hybrid-cloud-scenarios-for-azure-paas"></a>Escenarios de nube híbrida para PaaS de Azure

 **Resumen:** Comprenda la arquitectura y los escenarios híbridos de las ofertas de nubes basadas en Plataforma como servicio (PaaS) de Microsoft en Azure.
  
Combine datos locales o recursos de proceso con aplicaciones nuevas o convertidas que se ejecuten en PaaS de Azure, que puedan aprovechar el rendimiento, la confiabilidad y la escalabilidad de la nube, además de proporcionar soporte técnico mejorado para los usuarios móviles. 
  
## <a name="azure-paas-hybrid-scenario-architecture"></a>Arquitectura de escenario híbrido de PaaS de Azure

En la figura 1, se muestra la arquitectura de escenarios híbridos basados en PaaS de Microsoft en Azure.
  
**Figura 1: Escenarios híbridos basados en PaaS de Microsoft en Azure**

![Escenarios híbridos basados en PaaS de Microsoft en Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS.png)
  
Para cada capa de la arquitectura:
  
- Aplicaciones y escenarios
    
    Una aplicación PaaS híbrida se ejecuta en Azure y usa los recursos de proceso o almacenamiento locales.
    
- Identidad
    
    Consta de la sincronización de directorios o la federación con un proveedor de identidades de terceros.
    
- Red
    
    Consta de la canalización de Internet existente o de una conexión de ExpressRoute con emparejamiento público a PaaS de Azure. Debe incluir una forma para que la aplicación de PaaS de Azure tenga acceso al recurso de almacenamiento o proceso local.
    
- Local
    
    Consta de infraestructura de identidad y seguridad, así como de aplicaciones de línea de negocio (LOB) o servidores de bases de datos existentes, a los que una aplicación PaaS de Azure puede tener acceso con seguridad.
    
## <a name="azure-paas-hybrid-application"></a>Aplicación híbrida de PaaS de Azure

En la figura 2, se muestra la configuración de una aplicación híbrida que se ejecuta en Azure.
  
**Figura 2: Aplicación híbrida basada en PaaS de Azure**

![Aplicación híbrida basada en PaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps.png)
  
En la figura 2, una red local hospeda almacenamiento o aplicaciones en servidores y una red perimetral que contiene un servidor proxy. Está conectada a los servicios de PaaS de Azure en Internet o con una conexión de ExpressRoute.
  
Para poner sus recursos de proceso o almacenamiento a disposición de la aplicación PaaS de Azure híbrida, una organización puede hacer lo siguiente:
  
- Hospedar el recurso en servidores de la red perimetral.
    
- Hospedar un servidor proxy inverso en la red perimetral, que permite las solicitudes autenticadas, entrantes, basadas en HTTPS para el recurso ubicado de manera local.
    
La aplicación de Azure puede usar las credenciales de:
  
- Azure AD, que se puede sincronizar con el proveedor de identidades local, como servicios de dominio de Active Directory (AD DS).
    
- Un proveedor de identidades de terceros.
    
### <a name="example-azure-paas-hybrid-application"></a>Aplicación PaaS de Azure híbrida de ejemplo

En la figura 3, se muestra un ejemplo de aplicación híbrida que se ejecuta en Azure.
  
**Figura 3: Un ejemplo de aplicación híbrida basada en PaaS de Azure**

![Un ejemplo de aplicación híbrida basada en PaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-PaaS-Apps-Ex.png)
  
En la figura 3, una red local hospeda una aplicación LOB. PaaS de Azure hospeda una aplicación móvil personalizada. Un smartphone en Internet tiene acceso a la aplicación móvil personalizada en Azure, que envía solicitudes de datos a la aplicación LOB local.
  
Esta aplicación PaaS de Azure híbrida de ejemplo es una aplicación móvil personalizada que proporciona información de contacto actualizada de los empleados. El escenario híbrido completo consta de:
  
- Una aplicación para smartphone que necesita credenciales locales validadas para funcionar.
    
- Una aplicación móvil personalizada que se ejecuta en PaaS de Azure, que solicita información sobre empleados específicos según las consultas de la aplicación para smartphone de un usuario.
    
- Un servidor proxy inverso en la red perimetral que valida la aplicación móvil personalizada y reenvía la solicitud.
    
- Una granja de servidores de aplicaciones LOB que atiende la solicitud de contacto, sujeta a los permisos de la cuenta del usuario.
    
Dado que el proveedor de identidades local se ha sincronizado con Azure AD, la aplicación móvil personalizada y la aplicación LOB pueden validar el nombre de cuenta del usuario que realiza la solicitud.
  
## <a name="see-also"></a>Vea también

[Microsoft Hybrid Cloud para arquitectos profesionales](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)

