---
title: Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/06/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
search.appverid:
- MET150s
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- Ent_Solutions
ms.assetid: 34b1ab9c-814c-434d-8fd0-e5a82cd9bff6
description: 'Resumen: Configure la autenticación federada de alta disponibilidad para su suscripción de Office 365 en Microsoft Azure.'
ms.openlocfilehash: 9139019cf53b3a43bcc6d8ebcfbad5d4f7f5506f
ms.sourcegitcommit: 682b180061dc63cd602bee567d5414eae6942572
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/09/2019
ms.locfileid: "31741276"
---
# <a name="deploy-high-availability-federated-authentication-for-office-365-in-azure"></a>Implementar la autenticación federada de alta disponibilidad para Office 365 en Azure

 **Resumen:** Configure la autenticación federada de alta disponibilidad para su suscripción de Office 365 en Microsoft Azure.
  
Este artículo contiene vínculos a las instrucciones detalladas para implementar la autenticación federada de alta disponibilidad para Microsoft Office 365 en los servicios de infraestructura de Azure con estas máquinas virtuales:
  
- Dos servidores proxy de aplicación web
    
- Dos servidores de Servicios de federación de Active Directory (AD FS)
    
- Dos controladores de dominio de réplica
    
- Un servidor de sincronización de directorios (DirSync) que ejecute Azure AD Connect
    
Esta es la configuración, con nombres de marcador de posición para cada servidor.
  
**Una autenticación federada de alta disponibilidad para Office 365 en Azure**

![La configuración final de la infraestructura de la autenticación federada de Office 365 con alta disponibilidad en Azure](media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Todas las máquinas virtuales forman parte de una única red virtual entre locales de Azure (VNet). 
  
> [!NOTE]
> La autenticación federada de los usuarios individuales no se basa en los recursos locales. Sin embargo, si la conexión entre locales está disponible, los controladores de dominio de VNet no recibirán actualizaciones de grupos y cuentas de usuario realizados en el entorno de Servicios de dominio de Active Directory (AD DS) local. Para asegurarse de que esto no sucede, puede configurar la alta disponibilidad para la conexión entre locales. Para obtener más información, consulte [Conectividad de red virtual a red virtual y con alta disponibilidad entre locales](https://docs.microsoft.com/azure/vpn-gateway/vpn-gateway-highlyavailable).
  
Cada par de máquinas virtuales asignado a un rol específico forma parte de su propia subred y de su propio conjunto de disponibilidad.
  
> [!NOTE]
> Debido a que esta red virtual está conectada a la red local, la configuración no incluye máquinas virtuales intermedias ni de supervisión en una subred de administración. Para obtener más información, consulte [Running Windows VMs for an N-tier architecture](https://docs.microsoft.com/azure/guidance/guidance-compute-n-tier-vm). 
  
El resultado de esta configuración es que tendrá una autenticación federada para todos los usuarios de Office 365, en la que se pueden utilizar las credenciales de Active Directory Domain Services para iniciar sesión en lugar de la cuenta de Office 365. La infraestructura de autenticación federada utiliza un conjunto redundante de servidores que se implementan más fácilmente en servicios de la infraestructura de Azure en lugar de en la red perimetral local.
  
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
    
- [Fase 2: Configurar controladores de dominio](high-availability-federated-authentication-phase-2-configure-domain-controllers.md). Creación y configuración de controladores de dominio de réplica para Servicios de dominio de Active Directory (AD DS) y el servidor de DirSync.
    
- [Fase 3: Configurar servidores de AD FS](high-availability-federated-authentication-phase-3-configure-ad-fs-servers.md). Creación y configuración de los dos servidores de AD FS.
    
- [Fase 4: Configurar los servidores proxy de aplicación web](high-availability-federated-authentication-phase-4-configure-web-application-pro.md). Creación y configuración de los dos servidores proxy de aplicación web.
    
- [Fase 5: Configurar la autenticación federada para Office 365](high-availability-federated-authentication-phase-5-configure-federated-authentic.md). Configuración de la autenticación federada para su suscripción de Office 365.
    
En estos artículos, se proporciona una guía preceptiva dividida en fases para una arquitectura predefinida. Su objetivo es crear una autenticación federada de alta disponibilidad funcional para Office 365 en servicios de infraestructura de Azure. Tenga en cuenta lo siguiente:
  
- Si es un experimentado implementador de AD FS, no dude en adaptar las instrucciones que se detallan en las fases 3 y 4, así como en crear el conjunto de servidores que mejor se adapte a sus necesidades. 
    
- Si ya tiene una implementación existente de nube híbrida de Azure con una red virtual entre locales existente, no dude en adaptar u omitir las instrucciones que aparecen en las fases 1 y 2 y colocar los servidores proxy de aplicación web y AD FS en las subredes adecuadas.
    
Para crear un entorno de prueba o desarrollo o bien una prueba de concepto de esta configuración, consulte [Identidad federada para el entorno de desarrollo y pruebas de Office 365](federated-identity-for-your-office-365-dev-test-environment.md).
  
## <a name="next-step"></a>Paso siguiente

Inicie la configuración de esta carga de trabajo con [Fase 1 de la autenticación federada de alta disponibilidad: Configurar Azure](high-availability-federated-authentication-phase-1-configure-azure.md). 
  
<!--
> [!TIP]
> For a set of files to more quickly deploy your high availability federated authentication for Office 365 in Azure, see the [Federated Authentication for Office 365 in Azure Deployment Kit](https://gallery.technet.microsoft.com/Federated-Authentication-8a9f1664). 
--> 

