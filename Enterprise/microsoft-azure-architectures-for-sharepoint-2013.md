---
title: Arquitecturas de Microsoft Azure para SharePoint 2013
ms.author: bcarter
author: brendacarter
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: conceptual
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Architecture
ms.assetid: 98fc1006-9399-4ff0-a216-c7c05820d822
description: 'Summary: SharePoint 2013 solutions can be hosted in Microsoft Azure virtual machines. Learn which type of solutions are a good fit and how to set up Microsoft Azure to host one.'
ms.openlocfilehash: fee388f56faf2b30534d9a56926d9d62a176df19
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997902"
---
# <a name="microsoft-azure-architectures-for-sharepoint-2013"></a>Arquitecturas de Microsoft Azure para SharePoint 2013

Azure es un buen entorno para hospedar una solución de SharePoint Server 2013. En la mayoría de los casos, recomendamos Microsoft 365, pero una granja de servidores de SharePoint Server hospedada en Azure puede ser una buena opción para soluciones específicas. En este artículo se describe cómo diseñar soluciones de SharePoint para que sean una buena opción en la plataforma de Azure. Se usan como ejemplo las dos soluciones específicas siguientes:
  
- [Recuperación ante desastres de SharePoint Server 2013 en Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)
    
- [Sitios de Internet en Microsoft Azure con SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
    
## <a name="recommended-sharepoint-solutions-for-azure-infrastructure-services"></a>Soluciones de SharePoint recomendadas para servicios de infraestructura de Azure

Azure infrastructure services is a compelling option for hosting SharePoint solutions. Some solutions are a better fit for this platform than others. The following table shows recommended solutions.
  
|**Solución**|**Por qué se recomienda esta solución para Azure**|
|:-----|:-----|
|Entornos de desarrollo y pruebas  <br/> |Es fácil crear y administrar estos entornos.  <br/> |
|Recuperación ante desastres de granjas de SharePoint locales para Azure  <br/> |**Centro de datos secundario y hospedado** Use Azure en lugar de invertir en un centro de datos secundario de una región diferente. <br/> **Lower-cost disaster-recovery environments** Maintain and pay for fewer resources than an on-premises disaster recovery environment. The number of resources depends on the disaster recovery environment you choose: cold standby, warm standby, or hot standby. <br/> **More elastic platform** In the event of a disaster, easily scale-out your recovery SharePoint farm to meet load requirements. Scale in when you no longer need the resources. <br/> Vea [Recuperación ante desastres de SharePoint Server 2013 en Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md).  <br/> |
|Sitios orientados a Internet que usan características y escala no disponibles en Microsoft 365  <br/> |**Centre sus esfuerzos** Concéntrese en crear el mejor sitio posible y no en tener que crear la infraestructura necesaria. <br/> **Take advantage of elasticity in Azure** Size the farm for the demand by adding new servers, and pay only for resources you need. Dynamic machine allocation is not supported (auto scale). <br/> **Use Azure Active Directory (AD)** Aproveche Azure AD para cuentas de clientes. <br/> **Agregar la funcionalidad de SharePoint no disponible en Microsoft 365** Agregar informes detallados y Web Analytics. <br/> Vea [Sitios de Internet en Microsoft Azure con SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md).  <br/> |
|Granjas de aplicaciones para admitir entornos locales de Microsoft 365 o  <br/> |**Cree, pruebe y hospede a aplicaciones** en Azure para admitir entornos locales y en la nube. <br/> **Hospede a este rol** en Azure en lugar de comprar hardware nuevo para entornos locales. <br/> |
   
Para intranet y cargas de trabajo y soluciones de colaboración, considere las siguientes opciones:
  
- Determine si Microsoft 365 cumple los requisitos empresariales o puede formar parte de la solución. Microsoft 365 proporciona un amplio conjunto de características que siempre está actualizado.
    
- Si Microsoft 365 no cumple todos los requisitos empresariales, considere una implementación estándar de SharePoint 2013 local de los servicios de consultoría de Microsoft (MCS). Una arquitectura estándar puede ser una solución más rápida, económica y sencilla que una solución personalizada. 
    
- Si una implementación estándar no cumple los requisitos empresariales, considere una solución local personalizada.
    
- If using a cloud platform is important for your business requirements, consider a standard or customized implementation of SharePoint 2013 hosted in Azure infrastructure services. SharePoint solutions are much easier to support in Azure than other non-native Microsoft public cloud platforms.
    
## <a name="before-you-design-the-azure-environment"></a>Antes de diseñar el entorno de Azure

While this article uses example SharePoint topologies, you can use these design concepts with any SharePoint farm topology. Before you design the Azure environment, use the following topology, architecture, capacity, and performance guidance to design the SharePoint farm:
  
- [Diseño de la arquitectura de SharePoint 2013 para profesionales de TI](https://technet.microsoft.com/sharepoint/fp123594.aspx)
    
- [Plan for performance and capacity management in SharePoint Server 2013](https://technet.microsoft.com/library/8dd52916-f77d-4444-b593-1f7d6f330e5f.aspx)
    
## <a name="determine-the-active-directory-domain-type"></a>Determinar el tipo de dominio de Active Directory

Each SharePoint Server farm relies on Active Directory to provide administrative accounts for farm setup. At this time, there are two options for SharePoint solutions in Azure. These are described in the following table.
  
|**Opción**|**Descripción**|
|:-----|:-----|
|Dominio dedicado  <br/> |You can deploy a dedicated and isolated Active Directory domain to Azure to support your SharePoint farm. This is a good choice for public-facing Internet sites.  <br/> |
|Extender el dominio local a través de una conexión entre locales  <br/> |When you extend the on-premises domain through a cross-premises connection, users access the SharePoint farm via your intranet as if it were hosted on-premises. You can take advantage of your on-premises Active Directory and DNS implementation.  <br/> Se requiere una conexión entre locales para crear un entorno de recuperación ante desastres en Azure y realizar la conmutación por error desde la granja local.  <br/> |
   
This article includes design concepts for extending the on-premises domain through a cross-premises connection. If your solution uses a dedicated domain, you don't need a cross-premises connection.
  
## <a name="design-the-virtual-network"></a>Diseñar la red virtual

First you need a virtual network in Azure, which includes subnets on which you will place your virtual machines. The virtual network needs a private IP address space, portions of which you assign to the subnets.
  
Si está ampliando su red local a Azure mediante una conexión entre locales (necesaria para un entorno de recuperación ante desastres), debe elegir un espacio de direcciones privadas que no esté ya en uso en otro lugar de la red de su organización, que puede incluir su entorno local y otras redes virtuales de Azure. 
  
**Figura 1: Entorno local con una red virtual en Azure**

![Microsoft Azure virtual network design for a SharePoint solution. One subnet for the Azure gateway. One subnet for the virtual machines.](media/OPrrasconWA-AZarch.png)
  
En este diagrama:
  
- A virtual network in Azure is illustrated side-by-side to the on-premises environment. The two environments are not yet connected by a cross-premises connection, which can be a site-to-site VPN connection or ExpressRoute.
    
- At this point, the virtual network just includes the subnets and no other architectural elements. One subnet will host the Azure gateway and other subnets host the tiers of the SharePoint farm, with an additional one for Active Directory and DNS.
    
## <a name="add-cross-premises-connectivity"></a>Agregar conectividad entre locales

The next deployment step is to create the cross-premises connection (if this applies to your solution). For cross-premises connections, a Azure gateway resides in a separate gateway subnet, which you must create and assign an address space. 
  
Al planear una conexión entre locales, define y crea una conexión y una puerta de enlace de Azure hacia un dispositivo de puerta de enlace local.
  
**Figura 2: Uso de una puerta de enlace de Azure y un dispositivo de puerta de enlace local para proporcionar conectividad de sitio a sitio entre el entorno local y Azure**

![Entorno local conectado a una red virtual de Azure mediante una conexión entre locales, que puede ser una conexión VPN de sitio a sitio o ExpressRoute.](media/AZarch-VPNgtwyconnct.png)
  
En este diagrama:
  
- Se agrega al diagrama previo el entorno local que está conectado a la red virtual de Azure mediante una conexión entre locales, que puede ser una conexión VPN de sitio a sitio o ExpressRoute.
    
- Una puerta de enlace de Azure se encuentra en una subred de puerta de enlace.
    
- El entorno local incluye un dispositivo de puerta de enlace, como un enrutador o un servidor VPN.
    
Para obtener información adicional para planear y crear una red virtual entre locales, consulte [Conectar una red local con una red virtual de Microsoft Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
## <a name="add-active-directory-domain-services-ad-ds-and-dns"></a>Adición de servicios de dominio de Active Directory (AD DS) y DNS

Para la recuperación ante desastres en Azure, debe implementar Windows Server AD y DNS en un escenario híbrido donde se implementa Windows Server AD tanto de forma local como en máquinas virtuales de Azure.
  
**Figura 3: Configuración híbrida de dominios de Active Directory**

![Dos máquinas virtuales implementadas en la red virtual de Azure y la subred de la granja de servidores de SharePoint son réplicas de controladores de dominio y servidores DNS.](media/AZarch-HyADdomainConfig.png)
  
This diagram builds on the previous diagrams by adding two virtual machines to a Windows Server AD and DNS subnet. These virtual machines are replica domain controllers and DNS servers. They are an extension of the on-premises Windows Server AD environment. 
  
The following table provides configuration recommendations for these virtual machines in Azure. Use these as a starting point for designing your own environment—even for a dedicated domain where your Azure environment doesn't communicate with your on-premises environment.
  
|**Elemento**|**Configuración**|
|:-----|:-----|
|Tamaño de las máquinas virtuales en Azure  <br/> |Tamaño A1 o A2 en el nivel estándar  <br/> |
|Sistema operativo  <br/> |Windows Server 2012 R2  <br/> |
|Rol de Active Directory  <br/> |AD DS domain controller designated as a global catalog server. This configuration reduces egress traffic across the cross-premises connection.  <br/> En un entorno de varios dominios con altos índices de cambio (esto no es común), configure controladores de dominio de forma local no para sincronizar con los servidores de catálogo globales en Azure, sino para reducir el tráfico de replicación.  <br/> |
|Rol de DNS  <br/> |Instale y configure el servicio de DNS Server en los controladores de dominio.  <br/> |
|Discos de datos  <br/> |Place the Active Directory database, logs, and SYSVOL on additional Azure data disks. Do not place these on the operating system disk or the temporary disks provided by Azure.  <br/> |
|Direcciones IP  <br/> |Utilice direcciones IP estáticas y configure la red virtual para que las asigne a las máquinas virtuales de la red virtual tras la configuración de los controladores de dominio.  <br/> |
   
> [!IMPORTANT]
> Before you deploy Active Directory in Azure, read [Guidelines for Deploying Windows Server Active Directory on Azure Virtual Machines](https://go.microsoft.com/fwlink/p/?linkid=392681). These help you determine if a different architecture or different configuration settings are needed for your solution. 
  
## <a name="add-the-sharepoint-farm"></a>Agregar la granja de SharePoint

Coloque las máquinas virtuales de la granja de servidores de SharePoint en niveles de las subredes apropiadas.
  
**Figura 4: Colocación de máquinas virtuales de SharePoint**

![Servidores de bases de datos y roles de servidor de SharePoint agregados a la red virtual Azure dentro de la subred de la granja de servidores de SharePoint.](media/AZarch-SPVMsinCloudSer.png)
  
Este diagrama es una continuación de los diagramas previos al agregar los roles de servidor de granja de SharePoint en sus respectivos niveles.
  
- Dos máquinas virtuales de base de datos que ejecutan SQL Server crean el nivel de base de datos.
    
- Dos máquinas virtuales ejecutan SharePoint Server 2013 para cada uno de los siguientes niveles: servidores front-end, servidores de caché distribuidos y servidores back-end.
    
## <a name="design-and-fine-tune-server-roles-for-availability-sets-and-fault-domains"></a>Diseñar y ajustar roles de servidor para conjuntos de disponibilidad y dominios de error

A fault domain is a grouping of hardware in which role instances run. Virtual machines within the same fault domain can be updated by the Azure infrastructure at the same time. Or, they can fail at the same time because they share the same rack. To avoid the risk of having two virtual machines on the same fault domain, you can configure your virtual machines as an availability set, which ensures that each virtual machine is in a different fault domain. If three virtual machines are configured as an availability set, Azure guarantees that no more than two of the virtual machines are located in the same fault domain.
  
When you design the Azure architecture for a SharePoint farm, configure identical server roles to be part of an availability set. This ensures that your virtual machines are spread across multiple fault domains.
  
**Figura 5: Uso de Conjuntos de disponibilidad de Azure para proporcionar alta disponibilidad para niveles de granja de servidores de SharePoint**

![Configuración de conjuntos de disponibilidad en la infraestructura de Azure para una solución de SharePoint 2013.](media/AZenv-WinAzureAvailSetsHA.png)
  
This diagram calls out the configuration of availability sets within the Azure infrastructure. Each of the following roles share a separate availability set:
  
- Active Directory y DNS
    
- Base de datos
    
- Back-end
    
- Caché distribuido
    
- Front-end
    
The SharePoint farm might need to be fine tuned in the Azure platform. To ensure high availability of all components, ensure that the server roles are all configured identically.
  
Here is an example that shows a standard Internet Sites architecture that meets specific capacity and performance goals. This example is featured in the following architecture model: [Internet Sites Search Architectures for SharePoint Server 2013](https://go.microsoft.com/fwlink/p/?LinkId=261519).
  
**Figura 6: Ejemplo de planeación para objetivos de capacidad y rendimiento en una granja de tres niveles**

![Arquitectura estándar de sitios de Internet de SharePoint 2013 con asignaciones de componentes que cumplen objetivos específicos de rendimiento y capacidad.](media/AZarch-CapPerfexmpArch.png)
  
En este diagrama:
  
- Se representa una granja de tres niveles: servidores web, servidores de aplicaciones y servidores de bases de datos.
    
- Los tres servidores web están configurados idénticamente con varios componentes.
    
- Los dos servidores de bases de datos están configurados idénticamente.
    
- The three application servers are not configured identically. These server roles require fine tuning for availability sets in Azure.
    
Observemos más cerca el nivel de servidor de aplicaciones
  
**Figura 7: Nivel de servidor de aplicaciones antes del ajuste**

![Ejemplo de nivel de servidor de la aplicación de SharePoint Server 2013 antes de la optimización para conjuntos de disponibilidad de Microsoft Azure.](media/AZarch-AppServtierBefore.png)
  
En este diagrama:
  
- Se incluyen tres servidores en el nivel de aplicación.
    
- El primer servidor incluye cuatro componentes.
    
- El segundo servidor incluye tres componentes.
    
- El tercer servidor incluye dos componentes.
    
You determine the number of components by the performance and capacity targets for the farm. To adapt this architecture for Azure, we'll replicate the four components across all three servers. This increases the number of components beyond what is necessary for performance and capacity. The tradeoff is that this design ensures high availability of all four components in the Azure platform when these three virtual machines are assigned to an availability set.
  
**Figura 8: Nivel de servidor de aplicaciones después del ajuste**

![Ejemplo de nivel de servidor de la aplicación de SharePoint Server 2013 después de la optimización para conjuntos de disponibilidad de Microsoft Azure.](media/AZarch-AppServtierAfter.png)
  
Este diagrama muestra los tres servidores de aplicaciones configurados de forma idéntica con los mismos cuatro componentes.
  
Cuando agregamos conjuntos de disponibilidad a los niveles de la granja de servidores de SharePoint, se completa la implementación.
  
**Figura 9: La granja de SharePoint completada en los servicios de infraestructura de Azure**

![Ejemplo de granja de servidores de SharePoint 2013 en los servicios de infraestructura de Azure con red virtual, conectividad entre locales, subredes, máquinas virtuales y conjuntos de disponibilidad.](media/7256292f-bf11-485b-8917-41ba206153ee.png)
  
Este diagrama muestra el conjunto de servidores de SharePoint implementado en los servicios de infraestructura de Azure, con conjuntos de disponibilidad para proporcionar dominios de error para los servidores de cada nivel.
  
## <a name="see-also"></a>Consulta también

[Adopción de la nube y soluciones híbridas](cloud-adoption-and-hybrid-solutions.yml)
  
[Sitios de Internet en Microsoft Azure con SharePoint Server 2013](internet-sites-in-microsoft-azure-using-sharepoint-server-2013.md)
  
[Recuperación ante desastres de SharePoint Server 2013 en Microsoft Azure](sharepoint-server-2013-disaster-recovery-in-microsoft-azure.md)


