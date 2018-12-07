---
title: Escenarios de nube híbrida para IaaS de Azure
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
description: 'Resumen: Conozca la arquitectura híbrida y los escenarios para la infraestructura de Microsoft como un servicio (IaaS)-en función de las ofertas de nube en Azure.'
ms.openlocfilehash: 441565adae46d50ad1b7139525ff3146c5f88ca3
ms.sourcegitcommit: 82c8fe6393457f0271d1737a09402a420a81c986
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2018
ms.locfileid: "27181041"
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Escenarios de nube híbrida para Azure IaaS

 **Resumen:** Comprender la arquitectura híbrida y los escenarios para la infraestructura de Microsoft como un servicio (IaaS)-en función de las ofertas de nube en Azure.
  
Extienda su infraestructura informática y de identidad local a la nube mediante el hospedaje de las cargas de trabajo de TI que se ejecutan en redes virtuales (VNet) de Azure entre locales.  
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Arquitectura de escenario híbrido de IaaS de Azure

En la figura 1, se muestra la arquitectura de escenarios híbridos basados en IaaS de Microsoft en Azure.
  
**Figura 1: Escenarios híbridos basados en IaaS de Microsoft en Azure**

![Escenarios híbridos basados en IaaS de Microsoft en Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS.png)
  
Para cada capa de la arquitectura:
  
- Aplicaciones y escenarios
    
    Una carga de trabajo de TI suele ser una aplicación de alta disponibilidad y varios niveles formada por máquinas virtuales (VM) de Azure.
    
- Identidad
    
    Agregue servidores de identidades, como controladores de dominio de Windows Server AD, al conjunto de servidores que se ejecutan en redes virtuales de Azure para la autenticación local.
    
- Red
    
    Use una conexión VPN de sitio a sitio a través de Internet o una conexión de ExpressRoute con emparejamiento privado a IaaS de Azure.
    
- Local
    
    Contiene servidores de identidad que se sincronizan con los servidores de identidad que se ejecutan en Azure. También puede incluir recursos a los que pueden tener acceso las máquinas virtuales que se ejecutan en Azure, como la infraestructura de administración de sistemas y almacenamiento.
    
## <a name="directory-synchronization-server-for-office-365"></a>Servidor de sincronización de Active Directory para Office 365

Ejecuta el servidor de sincronización de Active directory desde un VNet de Azure, tal como se muestra en la figura 2, es un ejemplo de ampliación de la infraestructura informática y la identidad a la nube.
  
**La figura 2: Servidor de sincronización de Active Directory para Office 365 en IaaS de Azure**

![Servidor de sincronización de Active Directory para Office 365 en IaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-DirSync.png)
  
En la figura 2, una red local hospeda una infraestructura de Windows Server AD, con un servidor proxy y un enrutador en su borde. El enrutador se conecta a una puerta de enlace de Azure en el borde de un VNet de Azure con una conexión de sitio a sitio VPN o ExpressRoute. Dentro de la VNet, un servidor de sincronización de Active directory ejecuta en Azure Connect de AD.
  
Un servidor de sincronización de Active directory para Office 365 sincroniza la lista de cuentas en Windows Server AD con el inquilino de Azure AD de una suscripción a Office 365.
  
Un servidor de sincronización de Active directory es un servidor basado en Windows que se ejecuta Azure Connect de AD. El aprovisionamiento más rápidos o para reducir el número de servidores local de su organización, implementar el servidor de sincronización de Active directory en una red virtual (VNet) en Azure IaaS.
  
El servidor de sincronización de Active directory sondea Windows Server AD para que los cambios y, a continuación, sincroniza con la suscripción de Office 365.
  
Para obtener más información, vea [Implementar sincronización de directorios de Office 365 en Microsoft Azure](deploy-office-365-directory-synchronization-dirsync-in-microsoft-azure.md).
  
## <a name="line-of-business-lob-application"></a>Aplicación de línea de negocio (LOB)

En la figura 3 se muestra la configuración de una aplicación LOB basada en servidor que se ejecuta en IaaS de Azure.
  
**Figura 3: Aplicación LOB en IaaS de Azure**

![Aplicación de LOB basada en servidor en IaaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-Ex.png)
  
En la figura 3, una red local hospeda usuarios y una infraestructura de identidad. Está conectada a una puerta de enlace de IaaS de Azure con una VPN de sitio a sitio o con una conexión ExpressRoute. IaaS de Azure hospeda una red virtual que contiene los servidores de la aplicación LOB.
  
Puede crear aplicaciones LOB que se ejecuten en máquinas virtuales de Azure, que residen en subredes de una red virtual de Azure en un centro de datos de Azure (también conocido como una ubicación). 



  
Dado que básicamente está extendiendo su infraestructura local a Azure, debe asignar espacio de direcciones privadas únicas a su redes virtuales y actualizar sus tablas de enrutamiento locales para garantizar la accesibilidad a cada red virtual.
  
Una vez conectadas, estas máquinas virtuales pueden administrarse con conexiones a Escritorio remoto o con software de administración de sistemas, al igual que los servidores locales.
  
Al configurar puertos expuestos de forma pública, los usuarios móviles o remotos también pueden tener acceso a estas máquinas virtuales desde Internet.
  
Para obtener una configuración de prueba de concepto, consulte [Simulated cross-premises virtual network in Azure](simulated-cross-premises-virtual-network-in-azure.md).
  
Los siguientes son atributos de las aplicaciones LOB hospedadas en máquinas virtuales de Azure:
  
- Varios niveles
    
    Las aplicaciones LOB típicas usan un enfoque con niveles. Los conjuntos de servidores proporcionan identidad, procesamiento de base de datos, aplicación y procesamiento lógico, además de servidores front-end web para el acceso de empleados o clientes.  
    
- Alta disponibilidad
    
    Las aplicaciones LOB típicas proporcionan alta disponibilidad al usar varios servidores en cada nivel. IaaS de Azure proporciona un contrato de nivel de servicio de tiempo de actividad del 99,9 % para servidores en conjuntos de disponibilidad de Azure.  
    
- Distribución de la carga
    
    Para distribuir la carga del tráfico de red entre varios servidores de un nivel, puede usar un equilibrador de carga accesible desde Internet o de Azure interno. O bien, puede usar un dispositivo equilibrador de carga dedicado disponible en Azure Marketplace.
    
- Seguridad
    
    Para proteger los servidores del tráfico entrante no solicitado de Internet, puede usar grupos de seguridad de red de Azure. Puede definir el tráfico permitido o denegado de una subred o de la interfaz de red de una máquina virtual individual.
    
## <a name="sharepoint-server-2016-farm-in-azure"></a>Granja de servidores de SharePoint Server 2016 en Azure

Un ejemplo de una aplicación LOB de niveles múltiples y de alta disponibilidad en Azure es una granja de servidores de SharePoint Server 2016, como se muestra en la figura 4.
  
**Figura 4: Una granja de servidores de SharePoint Server 2016 de alta disponibilidad en laaS de Azure**

![Una granja de servidores de SharePoint Server 2016 de alta disponibilidad en laaS de Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-SP2016.png)
  
En la figura 4, una red local hospeda usuarios y una infraestructura de identidad. Está conectada a una puerta de enlace de IaaS de Azure con una VPN de sitio a sitio o con una conexión ExpressRoute. La red virtual de Azure contiene los servidores de la granja de SharePoint Server 2016, que incluye niveles independientes para los servidores de front-end, los servidores de aplicaciones, el clúster de SQL Server y los controladores de dominio.
  
Esta configuración tiene los siguientes atributos de aplicaciones LOB en Azure:  
  
- Niveles
    
    Los servidores que ejecutan diferentes roles dentro de la granja crean los niveles, y cada nivel tiene su propia subred.

    
- Alta disponibilidad
    
    Se obtiene usando más de un servidor en cada nivel y colocando todos los servidores de un nivel en el mismo conjunto de disponibilidad.
    
- Distribución de la carga
    
    Los equilibradores de carga internos de Azure distribuyen el tráfico web de cliente entrante a los servidores de front-end (WEB1 y WEB2) y a la dirección IP del agente de escucha del clúster de SQL Server (SQL1, SQL2 y MN1).
    
- Seguridad
    
    Los grupos de seguridad de red para cada subred le permiten configurar tráfico entrante y saliente permitido.
    
Siga esta ruta de acceso para realizar una adopción correcta:
  
1. Evaluar y experimentar
    
    Vea [2016 de servidor de SharePoint en Microsoft Azure](https://docs.microsoft.com/SharePoint/administration/sharepoint-server-2016-in-microsoft-azure) para comprender las ventajas de ejecutar SharePoint Server 2016 en Azure.
    
    Vea [2016 de servidor de SharePoint de Intranet en el entorno de desarrollo o prueba Azure](https://docs.microsoft.com/SharePoint/administration/intranet-sharepoint-server-2016-in-azure-dev-test-environment) para crear un entorno de desarrollo o prueba simulado
    
2. Diseño
    
    Vea el [Diseño de una granja de servidores de SharePoint Server 2016 en Azure](https://docs.microsoft.com/SharePoint/administration/designing-a-sharepoint-server-2016-farm-in-azure) paso a paso a través de un proceso para determinar el conjunto de redes de Azure IaaS, compute y elementos de almacenamiento para hospedar la granja de servidores y su configuración.
    
3. Implementación
    
    Vea la [implementación de SharePoint Server 2016 con grupos de disponibilidad de SQL Server AlwaysOn en Azure](https://docs.microsoft.com/SharePoint/administration/deploying-sharepoint-server-2016-with-sql-server-alwayson-availability-groups-in) paso a paso a través de la configuración de end-to-end de la granja de servidores de alta disponibilidad en cinco fases.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Identidad federada para Office 365 en Azure

Otro ejemplo de una aplicación de línea de negocio de varios nivel y de alta disponibilidad en Azure es la identidad federada para Office 365.
  
**La figura 5: Una infraestructura de identidad federada de alta disponibilidad para Office 365 en IaaS de Azure**

![Una alta disponibilidad Office 365 federados infraestructura de autenticación en Azure](media/Hybrid-Poster/Hybrid-Cloud-Stack-IaaS-ADFS.png)
  
En la figura 5, una red local hospeda una infraestructura de identidad y a los usuarios. Se conecta a una puerta de enlace de IaaS de Azure con una conexión de sitio a sitio VPN o ExpressRoute. El VNet de Azure contiene controladores de dominio de Windows Server Active Directory (AD), los servidores de servicios de federación de Active Directory (AD FS) y servidores proxy web.
  
Esta configuración tiene los siguientes atributos de aplicaciones LOB en Azure: 
  
- **Niveles:** Existen niveles para controladores de dominio de Windows Server AD, servidores de AD FS y servidores proxy web.
    
- **Distribución de carga:** Un equilibrador de carga externo de Azure distribuye las solicitudes de autenticación de cliente entrantes a los servidores proxy de web y un equilibrador de carga interno de Azure distribuye las solicitudes de autenticación a los servidores de AD FS.
    
Siga esta ruta de acceso para realizar una adopción correcta:
  
1. Evaluar y experimentar
    
    Vea la [identidad federada para el entorno de desarrollo y prueba de Office 365](federated-identity-for-your-office-365-dev-test-environment.md) para crear un entorno de desarrollo o prueba simulado para autenticación federada con Office 365.
    
2. Implementación
    
    Vea [autenticación federada de alta disponibilidad de implementación para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) paso a paso a través de la configuración de extremo a otro de la infraestructura de AD FS de alta disponibilidad en cinco fases.
    
    
## <a name="see-also"></a>Vea también

[Microsoft Hybrid Cloud para arquitectos profesionales](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)


