---
title: Escenarios de nube híbrida para Azure IaaS
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
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: 'Resumen: comprenda la arquitectura y los escenarios híbridos de las ofertas de la nube basadas en la infraestructura como servicio (IaaS) de Microsoft en Azure.'
ms.openlocfilehash: 5d125780e8baf3dbbe71b0878f6bf57cbeb5740f
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037934"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Escenarios de nube híbrida para Azure IaaS

 **Resumen:** Comprenda la arquitectura y los escenarios híbridos de las ofertas de la nube basadas en infraestructura como servicio (IaaS) de Microsoft en Azure.
  
Extienda su infraestructura informática y de identidad local a la nube al hospedar las cargas de trabajo de ti que se ejecutan en redes virtuales (Vnet) de Azure entre locales. 
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Arquitectura de escenario híbrido de IaaS de Azure

En la figura 1 se muestra la arquitectura de escenarios híbridos basados en IaaS de Microsoft en Azure.
  
**Figura 1: escenarios híbridos basados en IaaS de Microsoft en Azure**

![Escenarios híbridos basados en IaaS de Microsoft en Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
Para cada capa de la arquitectura:
  
- Aplicaciones y escenarios
    
    Una carga de trabajo de ti suele ser una aplicación de alta disponibilidad y varios niveles formada por máquinas virtuales (VM) de Azure.
    
- Identidad
    
    Agregue servidores de identidad, como controladores de dominio de Windows Server AD, al conjunto de servidores que se ejecutan en redes virtuales de Azure para la autenticación local.
    
- Red
    
    Use una conexión VPN de sitio a sitio a través de Internet o una conexión de ExpressRoute con emparejamiento privado a IaaS de Azure.
    
- Local
    
    Contiene los servidores de identidad que se sincronizan con los servidores de identidades que se ejecutan en Azure. También puede contener recursos a los que pueden tener acceso las máquinas virtuales que se ejecutan en Azure, como la infraestructura de administración de sistemas y almacenamiento.
    
## <a name="directory-synchronization-server-for-office-365"></a>Servidor de sincronización de directorios para Office 365

Ejecutar el servidor de sincronización de directorios desde una red virtual de Azure, tal como se muestra en la figura 2, es un ejemplo de la ampliación de la infraestructura informática y de identidad a la nube.
  
**Figura 2: servidor de sincronización de directorios para Office 365 en IaaS de Azure**

![Servidor de sincronización de directorios para Office 365 en IaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
En la figura 2, una red local hospeda una infraestructura de Windows Server AD, con un servidor proxy y un enrutador en su periferia. El enrutador se conecta a una puerta de enlace de Azure en el perímetro de una red virtual de Azure con una conexión de ExpressRoute o VPN de sitio a sitio. Dentro de la red virtual, un servidor de sincronización de directorios ejecuta Azure AD Connect.
  
Un servidor de sincronización de directorios para Office 365 sincroniza la lista de cuentas de Windows Server AD con el espacio empresarial de Azure AD de una suscripción a Office 365.
  
Un servidor de sincronización de directorios es un servidor basado en Windows que ejecuta Azure AD Connect. Para un aprovisionamiento más rápido o para reducir el número de servidores locales de la organización, implemente el servidor de sincronización de directorios en una red virtual (VNet) en IaaS de Azure.
  
El servidor de sincronización de directorios sondea Windows Server AD para comprobar si hay cambios y, a continuación, los sincroniza con la suscripción de Office 365.
  
Para obtener más información, vea [deploy Office 365 Directory Synchronization in Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).
  
## <a name="line-of-business-lob-application"></a>Aplicación de línea de negocio (LOB)

La figura 3 muestra la configuración de una aplicación LOB basada en servidor que se ejecuta en IaaS de Azure.
  
**Figura 3: aplicación LOB en IaaS de Azure**

![Aplicación de LOB basada en servidor en IaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
En la figura 3, una red local hospeda una infraestructura de identidad y usuarios. Está conectado a una puerta de enlace de IaaS de Azure con una conexión de ExpressRoute o VPN de sitio a sitio. Azure IaaS hospeda una red virtual que contiene los servidores de la aplicación LOB.
  
Puede crear aplicaciones LOB que se ejecuten en máquinas virtuales de Azure, que residen en subredes de una VNet de Azure en un centro de recursos de Azure (también conocido como ubicación).
  
Como básicamente está extendiendo su infraestructura local a Azure, debe asignar un espacio de direcciones privadas únicas a sus redes virtuales y actualizar las tablas de enrutamiento local para garantizar la posibilidad de acceso a cada red virtual.
  
Una vez conectado, estas máquinas virtuales se pueden administrar con conexiones de escritorio remoto o con el software de administración de sistemas, al igual que los servidores locales.
  
Al configurar puertos expuestos de forma pública, los usuarios móviles o remotos también pueden tener acceso a estas máquinas virtuales desde Internet.
  
Para obtener una configuración de prueba de concepto, consulte [simulated Cross-premises Virtual Network in Azure](simulated-cross-premises-virtual-network-in-azure.md).
  
Los atributos de las aplicaciones LOB hospedadas en máquinas virtuales de Azure son los siguientes:
  
- Varios niveles
    
    Las aplicaciones de unidad de negocio típicas usan un enfoque en niveles. Los conjuntos de servidores proporcionan identidad, procesamiento de base de datos, procesamiento de aplicaciones y lógicas, y servidores web Front-end para el acceso de empleados o clientes. 
    
- Alta disponibilidad
    
    Las aplicaciones LOB típicas proporcionan alta disponibilidad mediante el uso de varios servidores en cada nivel. IaaS de Azure proporciona un SLA de tiempo de actividad del 99,9% para servidores en conjuntos de disponibilidad de Azure. 
    
- Distribución de la carga
    
    Para distribuir la carga de tráfico de red entre varios servidores de un nivel, puede usar un equilibrador de carga de Azure interno o con conexión a Internet. O bien, puede usar un dispositivo del equilibrador de carga dedicado disponible en Azure Marketplace.
    
- Seguridad
    
    Para proteger los servidores del tráfico entrante no solicitado de Internet, puede usar grupos de seguridad de red de Azure. Puede definir el tráfico permitido o denegado para una subred o la interfaz de red de una máquina virtual individual.
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Granja de servidores de SharePoint Server 2016 en Azure

Un ejemplo de una aplicación LOB de varios niveles y altamente disponible en Azure es una granja de servidores de SharePoint Server 2016, tal como se muestra en la figura 4.
  
**Figura 4: una granja de servidores de SharePoint Server 2016 de alta disponibilidad en IaaS de Azure**

![Una granja de servidores de alta disponibilidad de SharePoint Server 2016 en IaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
En la figura 4, una red local hospeda una infraestructura de identidad y usuarios. Está conectado a una puerta de enlace de IaaS de Azure con una conexión de ExpressRoute o VPN de sitio a sitio. La red virtual de Azure contiene los servidores de la granja de servidores de SharePoint Server 2016, que incluye niveles independientes para los servidores front-end, los servidores de aplicaciones, el clúster de SQL Server y los controladores de dominio.
  
Esta configuración tiene los siguientes atributos de aplicaciones LOB en Azure: 
  
- Niveles
    
    Los servidores que ejecutan diferentes roles dentro de la granja de servidores crean los niveles y cada nivel tiene su propia subred.
    
- Alta disponibilidad
    
    Se logra mediante el uso de más de un servidor en cada nivel y la colocación de todos los servidores de un nivel en el mismo conjunto de disponibilidad.
    
- Distribución de la carga
    
    Los equilibradores de carga internos de Azure distribuyen el tráfico web de cliente entrante a los servidores front-end (WEB1 y WEB2) y a la dirección IP del agente de escucha del clúster de SQL Server (SQL1, SQL2 y MN1).
    
- Seguridad
    
    Los grupos de seguridad de red para cada subred le permiten configurar el tráfico entrante y saliente permitido.
    
Siga esta ruta de acceso para una adopción correcta:
  
1. Evaluar y experimentar
    
    Vea [SharePoint server 2016 en Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) para conocer las ventajas de ejecutar SharePoint Server 2016 en Azure.
    
    Vea [intranet SharePoint Server 2016 en entorno de prueba y desarrollo de Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) para crear un entorno de pruebas y desarrollo simulado.
    
2. Diseño
    
    Vea [Designing a SharePoint Server 2016 Farm in Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) para recorrer un proceso para determinar el conjunto de elementos de red, cálculo y almacenamiento de la IaaS de Azure para hospedar la granja de servidores y su configuración.
    
3. Implementar
    
    Vea [Deploying SharePoint server 2016 with SQL Server alwaysOn Availability Groups in Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) para recorrer la configuración de un extremo a otro de la granja de servidores de alta disponibilidad en cinco fases.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Identidad federada para Office 365 en Azure

Otro ejemplo de una aplicación LOB de varios niveles y altamente disponible en Azure es la identidad federada para Office 365.
  
**Figura 5: una infraestructura de identidad federada de alta disponibilidad para Office 365 en IaaS de Azure**

![Una infraestructura de autenticación federada de Office 365 de alta disponibilidad en Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
En la figura 5, una red local hospeda una infraestructura de identidad y usuarios. Está conectado a una puerta de enlace de IaaS de Azure con una conexión de ExpressRoute o VPN de sitio a sitio. La red virtual de Azure contiene servidores proxy Web, servidores de servicios de Federación de Active Directory (AD FS) y controladores de dominio de servicios de dominio de Active Directory (AD DS).
  
Esta configuración tiene los siguientes atributos de aplicaciones LOB en Azure:
  
- **Niveles:** Hay niveles para los servidores proxy Web, los servidores de AD FS y los controladores de dominio de Windows Server AD.
    
- **Distribución de carga:** Un equilibrador de carga de Azure externo distribuye las solicitudes de autenticación de cliente entrantes a los proxy web y un equilibrador de carga interno de Azure distribuye las solicitudes de autenticación a los servidores de AD FS.
    
Siga esta ruta de acceso para una adopción correcta:
  
1. Evaluar y experimentar
    
    Consulte [Federated Identity for your Office 365 dev/test Environment](federated-identity-for-your-office-365-dev-test-environment.md) para crear un entorno de pruebas y desarrollo simulado para la autenticación federada con Office 365.
    
2. Implementar
    
    Consulte [deploy High Availability Federated Authentication for Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) para recorrer la configuración de un extremo a otro de la infraestructura de AD FS de alta disponibilidad en cinco fases.
    
    
## <a name="see-also"></a>Vea también

[Microsoft Hybrid Cloud para arquitectos profesionales](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de Microsoft Cloud](microsoft-cloud-it-architecture-resources.md)


