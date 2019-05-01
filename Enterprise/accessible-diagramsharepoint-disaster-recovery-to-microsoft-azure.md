---
title: 'Diagrama accesible: Recuperación ante desastres de SharePoint para Microsoft Azure'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 4b855224-8e67-4efa-a3a4-908ee0ca6412
description: Este artículo es una versión de texto accesible del diagrama con el nombre Recuperación ante desastres de SharePoint en Microsoft Azure.
ms.openlocfilehash: 545aaae05e3becbde60fe01c0e50e5610ee69f98
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487726"
---
# <a name="accessible-diagram---sharepoint-disaster-recovery-to-microsoft-azure"></a>Diagrama accesible: Recuperación ante desastres de SharePoint para Microsoft Azure

**Resumen:** Este artículo es una versión de texto accesible del diagrama con el nombre recuperación ante desastres de SharePoint en Microsoft Azure.
  
En este póster se proporcionan ejemplos de arquitecturas para la creación de un entorno de recuperación de Azure.  
  
## <a name="on-premises-environment-with-an-azure-recovery-environment"></a>Entorno local con un entorno de recuperación de Azure

El diagrama muestra un ejemplo de arquitectura para el entorno de producción de un entorno local que usa Azure para la recuperación.  
  
### <a name="on-premises-production-environment"></a>Entorno de producción local

El diagrama adjunto muestra un entorno de producción activo con cuatro niveles de servidores en una granja de servidores.  
  
#### <a name="tier-1"></a>Nivel 1

Hay dos servidores para servicios de front-end y procesamiento de consultas. Hay una partición de índice que proporciona una réplica de ambos servidores.  
  
#### <a name="tier-2"></a>Nivel 2

En este nivel hay dos servidores para la caché distribuida.  
  
#### <a name="tier-3"></a>Nivel 3

En este nivel hay tres servidores. Cada servidor proporciona los siguientes servicios:  
  
- Servicios de back-end  
    
- Admin 
    
- Administrador de flujos de trabajo 
    
- Rastreo 
    
- Procesamiento de contenido 
    
- Análisis 
    
#### <a name="tier-4"></a>Nivel 4

En este nivel hay dos servidores. Ambos servidores tienen tres grupos de disponibilidad, como se describe a continuación:  
  
- El grupo de disponibilidad 1 proporciona capacidades de búsqueda.  
    
- El grupo de disponibilidad 2 proporciona contenido, configuración y aplicaciones de servicio.  
    
- El grupo de disponibilidad 3 proporciona contenido.  
    
También hay un servidor de uso compartido de archivos en este nivel. Los servidores del nivel 4 usan el trasvase de registros para comunicarse con este servidor. Este servidor, a su vez, se comunica mediante el servicio Replicación del sistema de archivos distribuido (DFSR) con un servidor del recurso compartido de archivos en el entorno de recuperación de espera semiactiva de Azure, tal como se describe en la sección siguiente.  
  
### <a name="azure-recovery-environment"></a>Entorno de recuperación de Azure

#### <a name="warm-standby-environment-running-virtual-machines"></a>Entorno de espera semiactiva que ejecuta máquinas virtuales

El diagrama adjunto muestra el entorno local replicado exactamente en el entorno de recuperación de Azure. El servidor del recurso compartido de archivos en este entorno se vincula al entorno local a través de DFSR. DFSR transfiere los registros del entorno de producción al entorno de recuperación a través del servidor del recurso compartido de archivos.  
  
### <a name="overview"></a>Información general

El entorno de recuperación ante desastres para una granja de servidores de SharePoint 2013 local se puede hospedar en Azure. 
  
-   Servicios de infraestructura de Azure proporciona un centro de datos secundario. 
    
- Únicamente se pagan los recursos que se usan. 
    
- Permite escalar horizontalmente granjas de servidores de recuperación de tamaño pequeño después de un desastre para cumplir con los objetivos de escala y capacidad.  
    
La granja de servidores de recuperación en Azure se configura de forma tan idéntica como sea posible a la granja de servidores de producción local.  
  
- Misma representación de roles de servidor. 
    
- Misma configuración de personalizaciones.  
    
- Misma configuración de las características de búsqueda (pueden ser en una versión más pequeña de la granja de servidores de producción).  
    
El trasvase de registros y el servicio DFSR se usan para copiar las copias de seguridad de la base de datos y los registros de transacciones en la granja de servidores de Azure.  
  
- DFSR se usa para transferir los registros del entorno de producción al entorno de recuperación. En un escenario WAN, resulta más eficaz usar DFSR que trasvasar los registros directamente al servidor secundario en Azure. 
    
- Los registros se reproducen en los equipos con SQL Server basados en Azure.  
    
- Las bases de datos de registros trasvasados se asocian a la granja de servidores únicamente después de realizar un ejercicio de recuperación. 
    
Procedimientos de conmutación por error:  
  
1. Detenga el trasvase de registros. 
    
2. Deje de aceptar tráfico a la granja de servidores principal. 
    
3. Reproduzca los registros de transacciones finales. 
    
4. Adjunte las bases de datos de contenido a la granja de servidores. 
    
5. Inicie un rastreo completo. 
    
6. Restaure las aplicaciones de servicio a partir de las bases de datos de servicios que se han replicado. 
    
Los objetivos de recuperación que ofrece esta solución incluyen:  
  
- Sitios y contenido 
    
- Búsqueda (rastreos repetidos, falta de historial de búsqueda)  
    
- Servicios
    
Otros elementos que es posible resolver a través de los Servicios de Consultoría de Microsoft o de un asociado:  
  
- Sincronización de soluciones de granja personalizadas 
    
- Conexiones a orígenes de datos locales (conectividad a datos empresariales [BDC] y búsqueda de orígenes de contenido)  
    
- Escenarios de restauración de búsqueda 
    
- Objetivos de tiempo de recuperación (RTO) y objetivos de punto de recuperación (RPO) 
    
#### <a name="cold-standby-environment-running-virtual-machines"></a>Entorno de espera pasiva que ejecuta máquinas virtuales

Los entornos de espera pasiva tardan más en iniciarse pero son más económicos.  
  
- La granja de servidores se crearon por completo, pero las máquinas virtuales se detuvieron después de crear la granja. Únicamente se pagan costos de procesamiento cuando las máquinas virtuales están en ejecución, pero sí se aplican costos de transferencia de datos de red y de almacenamiento.  
    
- En caso de desastre, todas las máquinas virtuales en la granja de servidores se inician y se revisan.  
    
- Las copias de seguridad y los registros de transacciones se aplican a las bases de datos de la granja de servidores.  
    
En la siguiente lista se describen procedimientos adicionales para los entornos de espera pasiva:  
  
- Active las máquinas virtuales con regularidad para revisar, actualizar y comprobar el entorno.  
    
- Ejecute procedimientos para actualizar las direcciones IP y DNS.  
    
- Configure SQL AlwaysOn después de una conmutación por error.  
    
El diagrama adjunto muestra un entorno de recuperación replicado en máquinas virtuales. Después de una conmutación por error a un entorno de espera pasiva, todas las máquinas virtuales se inician y los grupos de disponibilidad se configuran usando la reproducción de registros para que los servidores de base de datos queden disponibles.  
  
## <a name="sharepoint-recovery-environment-in-azure"></a>Entorno de recuperación de SharePoint en Azure

Diseñe y cree el entorno de conmutación por error en Azure.  
  
- Cree una red virtual en Azure. 
    
- Conecte la red local a la red virtual en Azure con una conexión VPN sitio a sitio. Esta conexión usa una puerta de enlace dinámica en Azure.  
    
- Implemente uno o más controladores de dominio en la red virtual de Azure y configúrelos para que funcionen con el dominio local. Estos controladores de dominio son servidores de catálogo.  
    
- Adapte la granja de servidores de SharePoint para los servicios en la nube y conjuntos de disponibilidad.   
    
- Implemente la granja de servidores de SharePoint y un servidor de archivos para hospedar recursos compartidos de archivos.  
    
- Configure el trasvase de registros y DFSR entre el entorno local y el entorno de recuperación basado en Azure.  
    
El diagrama adjunto muestra el entorno local y la red virtual de Azure con las siguientes características:  
  
### <a name="on-premises-environment"></a>Entorno local

- RRAS de Windows Server 2012 
    
- Servidor de Active Directory 
    
La red local interactúa con la red virtual Azure a través de una puerta de enlace de red privada virtual (VPN).  
  
### <a name="azure-virtual-network"></a>Red virtual de Azure

La puerta de enlace de VPN interactúa con una subred de puerta de enlace de VPN activa.  
  
Hay tres servicios en la nube en el entorno de red virtual de Azure: 
  
- El primer servicio en la nube tiene dos servidores de Active Directory y DNS con un conjunto de disponibilidad.  
    
- El segundo servicio en la nube tiene tres granjas de servidores: Dos servidores de caché distribuida con un conjunto de disponibilidad. Dos servidores de front-end con un conjunto de disponibilidad. Dos servidores de back-end con un conjunto de disponibilidad.
    
- El tercer servicio en la nube tiene tres servidores de bases de datos con un conjunto de disponibilidad. Uno de estos servidores de bases de datos es un recurso compartido de archivos para el trasvase de registros y un tercer nodo de una mayoría de nodos para SQL Server AlwaysOn  
    
### <a name="build-the-ad-ds-hybrid-environment"></a>Crear el entorno híbrido de AD DS

La configuración de AD DS para esta solución consiste en un escenario de implementación híbrida en el que AD DS se implementa parcialmente en las instalaciones locales y parcialmente en máquinas virtuales de Azure.  
  
Importante: antes de implementar AD DS en Azure, lea las directrices para implementar Windows Server Active Directory en máquinas virtuales de Microsoft Azurehttp://msdn.microsoft.com/en-us/library/windowsazure/jj156090.aspx)(. 
  
Para obtener instrucciones completas sobre el diseño y la implementación de entornos de http://TechNet.microsoft.comActive Directory, consulte. 
  
Esta arquitectura de referencia incluye dos máquinas virtuales configuradas como controladores de dominio. Cada una está configurada del modo siguiente:·  
  
- Tamaño: pequeño.  
    
- Sistema operativo: Windows Server 2012.   
    
- Rol: controlador de dominio de AD DS designado como servidor de catálogo global. Esta configuración reduce el tráfico de salida a través de la conexión VPN. En un entorno de varios dominios con altas tasas de cambio, configure los controladores de dominio localmente para que no se sincronicen con los servidores de catálogo global en Azure.   
    
- Discos de datos: es importante que coloque la base de datos, los registros y SYSVOL de AD DS en discos de datos de Azure. No los coloque en el disco del sistema operativo ni en los discos temporales proporcionados por Azure. 
    
- Rol: instale y configure el DNS de Windows en los controladores de dominio. 
    
- Direcciones IP: use direcciones IP dinámicas. Esto requiere la creación de una red virtual de Azure.  
    

