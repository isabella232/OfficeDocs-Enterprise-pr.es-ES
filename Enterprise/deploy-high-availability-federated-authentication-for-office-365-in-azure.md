---
title: Implementar la autenticación federada de alta disponibilidad para Microsoft 365 en Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'Resumen: configure la autenticación federada de alta disponibilidad para su suscripción a Microsoft 365 en Microsoft Azure.'
ms.openlocfilehash: 98b8bdff708d02f866a3e2f2d2521bec5b011bb7
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230056"
---
# <a name="deploy-high-availability-federated-authentication-for-microsoft-365-in-azure"></a>Implementar la autenticación federada de alta disponibilidad para Microsoft 365 en Azure

Este artículo contiene vínculos a las instrucciones paso a paso para implementar la autenticación federada de alta disponibilidad para Microsoft 365 en los servicios de infraestructura de Azure con estas máquinas virtuales:
  
- Dos servidores proxy de aplicación web
    
- Dos servidores de Servicios de federación de Active Directory (AD FS)
    
- Dos controladores de dominio de réplica
    
- Un servidor de sincronización de directorios que ejecute Azure AD Connect
    
Esta es la configuración, con nombres de marcador de posición para cada servidor.
  
**Una autenticación federada de alta disponibilidad para la infraestructura 365 de Microsoft en Azure**

![La configuración final de la infraestructura de autenticación federada de Microsoft 365 de alta disponibilidad en Azure](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Todas las máquinas virtuales forman parte de una única red virtual entre locales de Azure (VNet). 
  
> [!NOTE]
> La autenticación federada de los usuarios individuales no se basa en los recursos locales. Sin embargo, si la conexión entre locales está disponible, los controladores de dominio de VNet no recibirán actualizaciones de grupos y cuentas de usuario realizados en el entorno de Servicios de dominio de Active Directory (AD DS) local. Para asegurarse de que esto no sucede, puede configurar la alta disponibilidad para la conexión entre locales. Para obtener más información, consulte [Conectividad de red virtual a red virtual y con alta disponibilidad entre locales](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable).
  
Cada par de máquinas virtuales asignado a un rol específico forma parte de su propia subred y de su propio conjunto de disponibilidad.
  
> [!NOTE]
> Debido a que esta red virtual está conectada a la red local, la configuración no incluye máquinas virtuales intermedias ni de supervisión en una subred de administración. Para obtener más información, consulte [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm). 
  
El resultado de esta configuración es que tendrá autenticación federada para todos los usuarios de Microsoft 365, en los que pueden usar sus credenciales de AD DS para iniciar sesión en lugar de la cuenta de Microsoft 365. La infraestructura de autenticación federada utiliza un conjunto redundante de servidores que se implementan más fácilmente en servicios de la infraestructura de Azure en lugar de en la red perimetral en local.
  
## <a name="bill-of-materials"></a>Lista de materiales

Esta configuración de línea base requiere el siguiente conjunto de componentes y servicios de Azure:
  
- Siete máquinas virtuales
    
- Una red virtual entre locales con cuatro subredes
    
- Cuatro grupos de recursos
    
- Tres conjuntos de disponibilidad
    
- Una suscripción a Azure
    
Estas son las máquinas virtuales y sus tamaños predeterminados para esta configuración.
  
|**Elemento**|**Descripción de la máquina virtual**|**Imagen de la galería de Azure**|**Tamaño predeterminado**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Primer controlador de dominio  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|2.  <br/> |Segundo controlador de dominio  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|3.  <br/> |Servidor de Azure AD Connect  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|4.  <br/> |Primer servidor de AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|5.  <br/> |Segundo servidor de AD FS  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|6.  <br/> |Primer servidor proxy de aplicación web  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
|7.  <br/> |Segundo servidor proxy de aplicación web  <br/> |Windows Server 2016 Datacenter  <br/> |D2  <br/> |
   
Para calcular los costos estimados para esta configuración, consulte la [Calculadora de precios de Azure](https://azure.microsoft.com/pricing/calculator/).
  
## <a name="phases-of-deployment"></a>Fases de implementación

Implementará esta carga de trabajo en las fases siguientes:
  
- [Fase 1: Configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md). Creación de grupos de recursos, cuentas de almacenamiento, conjuntos de disponibilidad y una red virtual entre locales.
    
- [Fase 2: Configurar controladores de dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Cree y configure controladores de dominio de AD DS réplica y el servidor de sincronización de directorios.
    
- [Fase 3: Configurar servidores de AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Creación y configuración de los dos servidores de AD FS.
    
- [Fase 4: Configurar los servidores proxy de aplicación web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Creación y configuración de los dos servidores proxy de aplicación web.
    
- [Fase 5: configurar la autenticación federada para Microsoft 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configure la autenticación federada para su suscripción a Microsoft 365.
    
En estos artículos se proporciona una guía preceptiva para cada fase de una arquitectura predefinida para crear una autenticación federada funcional y de alta disponibilidad para Microsoft 365 en los servicios de infraestructura de Azure. Tenga en cuenta lo siguiente:
  
- Si es un experimentado implementador de AD FS, no dude en adaptar las instrucciones que se detallan en las fases 3 y 4, así como en crear el conjunto de servidores que mejor se adapte a sus necesidades. 
    
- Si ya tiene una implementación existente de nube híbrida de Azure con una red virtual entre locales existente, no dude en adaptar u omitir las instrucciones que aparecen en las fases 1 y 2 y colocar los servidores proxy de aplicación web y AD FS en las subredes adecuadas.
    
Para crear un entorno de desarrollo y pruebas o una prueba de concepto de esta configuración, consulte [Federated Identity for your Microsoft 365 dev/test Environment](https://docs.microsoft.com/microsoft-365/enterprise/federated-identity-for-your-office-365-dev-test-environment).
  
## <a name="next-step"></a>Siguiente paso

Inicie la configuración de esta carga de trabajo con la [Fase 1: Configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
  
