---
title: "Escenarios de nube híbrida para IaaS de Azure"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: overview
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Architecture
ms.assetid: 978f2b76-5aba-4e11-9434-f0efda987be1
description: "Resumen: Comprender los escenarios y la arquitectura híbrida para infraestructura de Microsoft como servicio (IaaS)-según las ofertas de nube en Azure."
ms.openlocfilehash: 5ec74058174724b6497a5cb41e67896818ef4d05
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="hybrid-cloud-scenarios-for-azure-iaas"></a>Escenarios de nube híbrida para IaaS de Azure

 **Resumen:** Comprender los escenarios y la arquitectura híbrida para infraestructura de Microsoft como servicio (IaaS)-según las ofertas de nube en Azure.
  
Extienda su infraestructura informática y de identidad local a la nube mediante el hospedaje de las cargas de trabajo de TI que se ejecutan en redes virtuales (VNet) de Azure entre locales.  
  
## <a name="azure-iaas-hybrid-scenario-architecture"></a>Arquitectura de escenario híbrido de IaaS de Azure

En la figura 1, se muestra la arquitectura de escenarios híbridos basados en IaaS de Microsoft en Azure.
  
**Figura 1: Escenarios de híbrida basada en IaaS Microsoft en Azure**

![Escenarios híbridos basados en IaaS de Microsoft en Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS.png)
  
Para cada capa de la arquitectura:
  
- Aplicaciones y escenarios
    
    Una carga de trabajo de TI suele ser una aplicación de alta disponibilidad y varios niveles formada por máquinas virtuales (VM) de Azure.
    
- Identidad
    
    Agregue servidores de identidades, como controladores de dominio de Windows Server AD, al conjunto de servidores que se ejecutan en redes virtuales de Azure para la autenticación local.
    
- Red
    
    Use una conexión VPN de sitio a sitio a través de Internet o una conexión de ExpressRoute con emparejamiento privado a IaaS de Azure.
    
- Local
    
    Contiene servidores de identidad que se sincronizan con los servidores de identidad que se ejecutan en Azure. También puede incluir recursos a los que pueden tener acceso las máquinas virtuales que se ejecutan en Azure, como la infraestructura de administración de sistemas y almacenamiento.
    
## <a name="dirsync-server-for-office-365"></a>Servidor de sincronización de directorios para Office 365

Ejecutar el servidor de sincronización de directorios (DirSync) desde una red virtual de Azure, como se muestra en la Figura 2, es un ejemplo de la ampliación de la infraestructura informática y de identidad a la nube.
  
**Figura 2: Servidor de sincronización de directorios para Office 365 en Azure IaaS**

![Servidor de sincronización de directorios para Office 365 en IaaS de Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_DirSync.png)
  
En la figura 2, una red local aloja una infraestructura Windows Server AD, con un servidor proxy y un enrutador en su borde. El enrutador se conecta a una puerta de enlace de Azure en el borde de un VNet de Azure con una conexión de sitio a sitio VPN o ExpressRoute. Dentro de la VNet, un servidor de sincronización de directorios ejecuta en Azure Connect de AD.
  
Un servidor de sincronización de directorios para Office 365 sincroniza la lista de cuentas en Windows Server AD con el inquilino de Azure AD de una suscripción de Office 365.
  
Un servidor de sincronización de directorios es un servidor basado en Windows que ejecuta Azure AD Connect. Para obtener un aprovisionamiento más rápido o para reducir el número de servidores locales en su organización, implemente su servidor de sincronización de directorios en una red virtual (VNet) en IaaS de Azure.
  
El servidor de sincronización de directorios sondea Windows Server AD para obtener los cambios y, después, los sincroniza con la suscripción de Office 365.
  
Para obtener más información, vea [Implementar Office 365 DirSync en Azure](https://technet.microsoft.com/library/dn635310.aspx).
  
## <a name="line-of-business-lob-application"></a>Aplicación de línea de negocio (LOB)

En la figura 3 se muestra la configuración de una aplicación LOB basada en servidor que se ejecuta en IaaS de Azure.
  
**Figura 3: Aplicación de LOB en Azure IaaS**

![Aplicación de LOB basada en servidor en IaaS de Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_Ex.png)
  
En la figura 3, una red local hospeda usuarios y una infraestructura de identidad. Está conectada a una puerta de enlace de IaaS de Azure con una VPN de sitio a sitio o con una conexión ExpressRoute. IaaS de Azure hospeda una red virtual que contiene los servidores de la aplicación LOB.
  
Puede crear aplicaciones de LOB ejecuta en Azure VM, que residen en las subredes de un VNet de Azure en un centro de datos de Azure (también conocido como una ubicación).
  
Dado que básicamente está extendiendo su infraestructura local a Azure, debe asignar espacio de direcciones privadas únicas a su redes virtuales y actualizar sus tablas de enrutamiento locales para garantizar la accesibilidad a cada red virtual.
  
Una vez conectadas, estas máquinas virtuales pueden administrarse con conexiones a Escritorio remoto o con software de administración de sistemas, al igual que los servidores locales.
  
Al configurar puertos expuestos de forma pública, los usuarios móviles o remotos también pueden tener acceso a estas máquinas virtuales desde Internet.
  
Para una configuración de prueba de concepto, vea [simulada entre local red virtual en Azure](simulated-cross-premises-virtual-network-in-azure.md).
  
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
  
**Figura 4: Una granja de alta disponibilidad 2016 de SharePoint Server en Azure IaaS**

![Una granja de servidores de SharePoint Server 2016 de alta disponibilidad en laaS de Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_SP2016.png)
  
En la figura 4, una red local hospeda usuarios y una infraestructura de identidad. Está conectada a una puerta de enlace de IaaS de Azure con una VPN de sitio a sitio o con una conexión ExpressRoute. La red virtual de Azure contiene los servidores de la granja de SharePoint Server 2016, que incluye niveles independientes para los servidores de front-end, los servidores de aplicaciones, el clúster de SQL Server y los controladores de dominio.
  
Esta configuración tiene los siguientes atributos de aplicaciones LOB en Azure:  
  
- Niveles
    
    Ejecutan funciones diferentes dentro de la granja de servidores crean los niveles y cada nivel tiene su propia subred.
    
- Alta disponibilidad
    
    Se obtiene usando más de un servidor en cada nivel y colocando todos los servidores de un nivel en el mismo conjunto de disponibilidad.
    
- Distribución de la carga
    
    Los equilibradores de carga internos de Azure distribuyen el tráfico web de cliente entrante a los servidores de front-end (WEB1 y WEB2) y a la dirección IP del agente de escucha del clúster de SQL Server (SQL1, SQL2 y MN1).
    
- Seguridad
    
    Los grupos de seguridad de red para cada subred le permiten configurar tráfico entrante y saliente permitido.
    
Siga esta ruta de acceso para realizar una adopción correcta:
  
1. Evaluar y experimentar
    
    Consulte [SharePoint Server 2016 en Azure de Microsoft](https://technet.microsoft.com/library/mt779107%28v=office.16%29.aspx) a comprender las ventajas de ejecutar SharePoint Server 2016 en Azure.
    
    Ver [Intranet 2016 de servidor de SharePoint en el entorno de pruebas y desarrollo de Azure](https://technet.microsoft.com/library/mt806351%28v=office.16%29.aspx) para crear un entorno de desarrollo/pruebas simuladas
    
2. Diseño
    
    Vea el [Diseño de una granja de SharePoint Server 2016 en Azure](https://technet.microsoft.com/library/mt779108%28v=office.16%29.aspx) paso a paso a través de un proceso para determinar el conjunto de redes de IaaS Azure compute y elementos de almacenamiento para alojar el conjunto de servidores y su configuración.
    
3. Implementar
    
    Vea [implementar SharePoint Server 2016 con grupos de disponibilidad de SQL Server AlwaysOn en Azure](https://technet.microsoft.com/library/mt793552%28v=office.16%29.aspx) paso a paso a través de la configuración de end-to-end de la granja de servidores de alta disponibilidad en cinco fases.
    
## <a name="federated-identity-for-office-365-in-azure"></a>Identidad federada para Office 365 en Azure

Otro ejemplo de una aplicación empresarial de varios niveles y altamente disponible en Azure es identidad federada para Office 365.
  
**Figura 5: Una infraestructura de alta disponibilidad de identidad federada para Office 365 en Azure IaaS**

![La configuración final de la infraestructura de la autenticación federada de Office 365 con alta disponibilidad en Azure](images/Hybrid_Poster/Hybrid_Cloud_Stack_IaaS_ADFS.png)
  
En la figura 5, una red local aloja usuarios y una infraestructura de identidad. Está conectado a una puerta de enlace de Azure IaaS con una conexión de sitio a sitio VPN o ExpressRoute. El VNet de Azure contiene controladores de dominio de Windows Server Active Directory (AD), servidores de servicios de federación de Active Directory (AD FS) y servidores proxy web.
  
Esta configuración tiene los siguientes atributos de aplicaciones LOB en Azure: 
  
- **Niveles:** Existen niveles para controladores de dominio de Windows Server AD, servidores de AD FS y servidores proxy web.
    
- **Distribución de carga:** Un equilibrador de carga externo de Azure distribuye las solicitudes de autenticación de cliente entrantes a los servidores proxy de web y un equilibrador de carga interno de Azure distribuye las solicitudes de autenticación a los servidores de AD FS.
    
Siga esta ruta de acceso para realizar una adopción correcta:
  
1. Evaluar y experimentar
    
    Vea la [identidad federada para su entorno de pruebas y desarrollo de Office 365](federated-identity-for-your-office-365-dev-test-environment.md) para crear un entorno de desarrollo/pruebas simuladas para autenticación federados con Office 365.
    
2. Implementar
    
    Vea [autenticación federados de alta disponibilidad de implementación para Office 365 en Azure](deploy-high-availability-federated-authentication-for-office-365-in-azure.md) paso a paso a través de la configuración de end-to-end de la infraestructura de AD FS de alta disponibilidad en cinco fases.
    
Consulte estos recursos adicionales:
  
- [Diseñar entornos de nube híbrida](https://gallery.technet.microsoft.com/Architecting-Hybrid-Cloud-a7dc9f24/file/147475/1/Architecting%20Hybrid%20Cloud%20Environments%20V1.docx)
    
- [Ampliar su centro de datos para el curso de la nube de Microsoft Virtual Academy](https://mva.microsoft.com/en-US/training-courses/extend-your-datacenter-to-the-cloud-13908?l=7fG3tAouB_7100115881)
    
- [Diseñar y construir una aplicación LOB en Azure](https://techcommunity.microsoft.com/t5/CAAB-Cloud-Adoption-Advisory/EXTRA-November-2016-Webinar/m-p/30058#M41)
    
## <a name="see-also"></a>Vea también

[Microsoft Hybrid Cloud para arquitectos profesionales](microsoft-hybrid-cloud-for-enterprise-architects.md)
  
[Recursos de arquitectura de TI de la nube de Microsoft](microsoft-cloud-it-architecture-resources.md)

[Mapa de ruta de Enterprise Cloud de Microsoft: Recursos para los responsables de decisiones de TI](https://sway.com/FJ2xsyWtkJc2taRD)



