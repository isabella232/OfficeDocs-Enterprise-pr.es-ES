---
title: 'Diagrama accesible: Opciones de plataformas de Microsoft Lync 2013'
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 2858d1e7-be37-4484-b121-a99779742a38
description: "Este artículo es una versión de texto accesible del diagrama con el nombre Opciones de plataformas de Microsoft Lync 2013, que está disponible en Diagramas técnicos."
ms.openlocfilehash: 79342a30a0391980cf16304f3615f6a7e64d51ff
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---microsoft-lync-2013-platform-options"></a>Diagrama accesible: Opciones de plataformas de Microsoft Lync 2013

**Resumen:** este artículo es una versión de texto accesible del diagrama “Opciones de plataformas de Microsoft Lync 2013”, que está disponible en [Diagramas técnicos](http://go.microsoft.com/fwlink/?LinkID=519139&amp;clcid=0x409).
  
Este póster describe lo que los arquitectos y responsables de decisiones empresariales (BDM) necesitan saber sobre implementaciones de Lync Online (Office 365) y Lync Server. Incluye lo siguiente:
  
- Una comparación de cuatro diferentes opciones de implementación: Lync Online (Office 365), implementación híbrida de Lync Online/Server, Lync Server y Lync Server hospedado por el proveedor. 
    
- Dos escenarios de ejemplo para implementar Lync 2013.
    
## <a name="comparison-of-four-different-deployments-for-the-lync-2013-platform"></a>Comparación de cuatro implementaciones diferentes para la plataforma de Lync 2013

La comparación proporciona información sobre cada opción de implementación en las siguientes áreas: 
  
- Información general sobre las diferentes características de implementación
    
- Ventajas de la implementación de cada opción de implementación
    
- Requisitos de licencia
    
- Tareas de arquitectura requeridas
    
- Responsabilidades del profesional de TI para implementar cada opción de implementación
    
### <a name="overview"></a>Información general

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Aumente su eficiencia y optimice los costos con los planes multiempresa de Office 365.
  
El diagrama correspondiente muestra Lync Online con un inquilino de Azure Active Directory que sincroniza nombres y contraseñas de cuentas entre el entorno de Servicios de dominio de Active Directory (AD DS) y el inquilino de Azure Active Directory. 
  
Descripción de las características y funcionalidades:
  
- Software como servicio (SaaS).
    
- Amplio conjunto de características que siempre está actualizado.
    
- Incluye un inquilino de Azure Active Directory para cuentas en línea que se puede usar con otras aplicaciones. 
    
- La integración de directorios incluye sincronización de nombres y contraseñas de cuentas entre el entorno de Servicios de dominio de Active Directory (AD DS) local y el inquilino de Azure Active Directory.
    
- Si se requiere inicio de sesión único (SSO), se debe implementar los Servicios de federación de Active Directory (AD FS). 
    
- La comunicación con el cliente por Internet está cifrada y autenticada.
    
- La conectividad para el equipo telefónico heredado a través de la red telefónica conmutada (RTC) está disponible con proveedores de terceros.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Implementación híbrida de Lync Online/Server (dominio dividido)

Puede combinar las ventajas de Office 365 con una implementación local de Lync 2013.
  
En el diagrama adjunto se muestra Office 365 con Lync Online, donde algunos usuarios están alojados localmente y otros en línea. También se muestra un servidor perimetral implementado de manera local.
  
Descripción de las características y funcionalidades:
  
- Algunos usuarios se alojan de forma local y otros se alojan en línea, pero todos comparten el mismo dominio SIP (por ejemplo, contoso.com).
    
- Se aprovecha la infraestructura de Lync Server 2013 existente, incluidas las conexiones a la RTC.
    
- Agregue nuevos usuarios Lync Online fácilmente cuando no estos no requieran RTC.
    
- Migre desde Lync local a Lync Online con el transcurso del tiempo, según la programación deseada.
    
- Se integra con otras aplicaciones de Office 365, incluidas Exchange Online y SharePoint Online.
    
#### <a name="lync-server"></a>Lync Server

En esta implementación, todo es propiedad suya. El diagrama correspondiente muestra una infraestructura de Lync Server con un entorno de Active Directory Domain Services (AD DS) local donde los usuarios están alojados de forma local.
  
Descripción de las características y funcionalidades:
  
- Planeamiento de la capacidad y ajuste del tamaño.
    
- Adquisición y configuración de servidores.
    
- Implementación.
    
- Escalado horizontal, revisiones y operaciones.
    
- Copias de seguridad de datos.
    
- Mantenimiento de conmutación por error y recuperación ante desastres.
    
- Conexión de la infraestructura de Lync Server 2013 a la RTC.
    
- Integración con el equipo telefónico existente (centrales de conmutación privada [PBX], por ejemplo).
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado por el proveedor

En esta implementación, todo está en manos del proveedor. El diagrama adjunto muestra una red del proveedor, incluyendo sus servidores y equipo, con una conexión a un entorno local.
  
Descripción de las características y funcionalidades:
  
- Planeamiento de la capacidad y ajuste del tamaño.
    
- Adquisición y configuración de servidores.
    
- Implementación.
    
- Escalado horizontal, revisiones y operaciones.
    
- Copias de seguridad de datos.
    
- Mantenimiento de conmutación por error y recuperación ante desastres.
    
- Integración con el equipo telefónico existente (centrales de conmutación privada [PBX], por ejemplo).
    
- Además, el proveedor puede:
    
  - Instalar sus servidores y equipo en su propia red con una conexión a las instalaciones de la organización (línea continua).
    
  - Instalar sus servidores directamente en las instalaciones de la organización (línea discontinua).
    
### <a name="benefits-of-implementing-each-deployment-option"></a>Ventajas de la implementación de cada opción de implementación

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Carga operativa nula a los servidores locales o al software de los servidores.
    
- Capacidades de comunicación de Lync Server 2013 como servicio basado en la nube.
    
- Presencia de Lync, mensajería instantánea, llamadas de audio y vídeo, reuniones en línea enriquecidas y capacidades de conferencias web extensas.
    
- Útil para organizaciones dispersas geográficamente o con los empleados que se desplazan la mayor parte del tiempo.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Implementación híbrida de Lync Online/Server (dominio dividido)

- Uso de Lync Online con usuarios remotos y para la integración con sus asociados comerciales.
    
- Migración sencilla de Lync local a Lync Online.
    
- Compatibilidad con sitios remotos sin usar un equipo de la sucursal.
    
- Facilidad para agregar compatibilidad con Lync a las nuevas adquisiciones de la empresa.
    
#### <a name="lync-server"></a>Lync Server

- Soluciones de nube privada.
    
- Soluciones muy personalizadas.
    
- Soluciones heredadas con componentes de terceros que dependen de hardware y software no compatible con Lync Online.
    
- Restricciones de privacidad que evitan la sincronización de cuentas de AD DS con Office 365.
    
- Ideal para organizaciones que quieren tener el control completo de la plataforma y la solución.
    
- Sustitución de PBX por Enterprise Voice de Lync.
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado por el proveedor

- Ideal para organizaciones que desean la funcionalidad de Lync Server, pero quieren subcontratar su implementación y mantenimiento.
    
- Soluciones basadas en el proveedor.
    
- Soluciones muy personalizadas.
    
- Soluciones heredadas con componentes de terceros que dependen de hardware y software no compatible con Lync Online.
    
- Sustitución de PBX por Enterprise Voice de Lync.
    
### <a name="license-requirements"></a>Requisitos de licencia

#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Modelo de suscripción.
  
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Implementación híbrida de Lync Online/Server (dominio dividido)

- Office 365: modelo de suscripción. No se requieren licencias adicionales. 
    
- Implementación local: se aplican todas las licencias locales. 
    
#### <a name="lync-server"></a>Lync Server

- Sistema operativo del servidor
    
- SQL Server
    
- Licencia de Lync Server 2013
    
- Licencia de acceso de cliente de Lync 2013
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado por el proveedor

Los costos se basan en el acuerdo con el proveedor de soluciones de Lync.
  
### <a name="architecture-tasks"></a>Tareas de arquitectura

Esta sección muestra las tareas de arquitectura para cada opción de implementación.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

- Planee y diseñe la sincronización de directorios.
    
- Garantice la capacidad de la red y la disponibilidad a través de firewalls, servidores proxy, puertas de enlace y vínculos WAN.
    
- Adquirir certificados SSL de terceros para proporcionar seguridad empresarial para las ofertas de servicio de Office 365.
    
- Decida si desea conectarse a Office 365 con el protocolo de Internet versión 6 (IPv6).
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Implementación híbrida de Lync Online/Server (dominio dividido)

Además de las tareas para entornos Office 365 y locales:
  
- Determine el grado de integración de características que quiere usar con las versiones locales y en línea de Exchange Server y SharePoint.
    
- Si es necesario, determine el servidor proxy que se usará para las solicitudes de Office 365.
    
#### <a name="lync-server"></a>Lync Server

Diseñe el entorno de Lync en un entorno local existente:
  
- Topología de Lync para oficinas centrales y sucursales.
    
- Hardware del servidor (virtualización incluida).
    
- Integración con los Servicios de dominio de Active Directory (AD DS) y DNS.
    
- Equilibrio de carga para granjas de servidores de Lync.
    
- Conmutación por error y recuperación ante desastres.
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado por el proveedor

- Para una instalación basada en la nube, determine la conexión a la red del proveedor de servicios.
    
- Para una instalación local, determine la ubicación de los servidores de Lync del proveedor en su red.
    
- Para ambos tipos, determine la integración con AD DS y con el equipo de PBX.
    
### <a name="it-pro-responsibilities"></a>Responsabilidades del profesional de TI

Esta sección muestra las responsabilidades del profesional de TI para cada opción de implementación.
  
#### <a name="lync-online-office-365"></a>Lync Online (Office 365)

Implemente y administre Lync Online (Office 365):
  
- Implemente el plan de sincronización de directorios.
    
- Planee e implemente enrutamiento y registros DNS internos y externos.
    
- Configure el proxy o el firewall conforme a los requisitos de dirección IP y URL de Office 365.
    
- Administre las cuentas de usuario y la configuración de Lync Online.
    
#### <a name="lync-onlineserver-hybrid-split-domain"></a>Implementación híbrida de Lync Online/Server (dominio dividido)

Además de las tareas para entornos Office 365 y locales:
  
- Configure el servidor proxy, si es necesario.
    
- Configure la integración de características con las versiones locales y en línea de Exchange Server y SharePoint.
    
#### <a name="lync-server"></a>Lync Server

Implemente y administre el entorno local de Lync:
  
- Aprovisione los servidores.
    
- Implemente la topología de Lync.
    
- Actualice los servidores de Lync.
    
- Agregue o quite servidores de la topología según sea necesario con base en el uso.
    
- Implemente el entorno de conmutación por error y recuperación ante desastres.
    
#### <a name="provider-hosted-lync-server"></a>Lync Server hospedado por el proveedor

Colabore con el proveedor para:
  
- Integrar Lync Server a su red.
    
- Integre Lync Server con otros productos de Microsoft o soluciones personalizadas.
    
- Supervisar el cumplimiento del contrato de nivel de servicio (SLA) con el proveedor.
    
## <a name="two-example-scenarios-for-deploying-lync-2013"></a>Dos ejemplos de escenarios de implementación de Lync 2013

### <a name="directory-synchronization-components-in-microsoft-azure"></a>Componentes de sincronización de directorios en Microsoft Azure

La implementación de componentes de sincronización de directorios de Office 365 en Azure es más rápida gracias a la posibilidad de implementar máquinas virtuales a petición.
  
El diagrama correspondiente muestra Lync Online con un inquilino de Azure Active Directory que sincroniza nombres y contraseñas de cuentas entre el entorno de Active Directory (AD DS) y el inquilino de Azure Active Directory.
  
 **Solo servidor de sincronización de directorios**. En lugar de implementar el servidor de sincronización de directorios de 64 bits en el entorno local, se aprovisiona una máquina virtual en Azure a través de Internet.
  
 **Sincronización de directorios + AD FS**. Gracias a esta opción se admiten las identidades federadas de Office 365 sin necesidad de agregar hardware a la infraestructura local. También ofrece resistencia si el entorno Active Directory local no está disponible. Las características de esta opción incluyen:
  
- Ejecución de componentes de integración de directorios como máquinas virtuales de Azure.
    
- AD FS se publica en Internet a través de servidores proxy de AD FS en máquinas virtuales de Azure.
    
- En el caso de usuarios que se conectan desde ubicaciones no especificadas, el tráfico de autenticación de cliente se controla a través de servidores de AD FS y servidores proxy que se encuentran implementados en máquinas virtuales de Azure.
    
### <a name="lync-integration-with-exchange-and-sharepoint-in-office-365"></a>Integración de Lync con Exchange y SharePoint en Office 365

#### <a name="lync-server-with-exchange-online-and-sharepoint-online"></a>Lync Server con Exchange Online y SharePoint Online

En el diagrama adjunto se muestra Office 365 con Exchange Online y SharePoint Online, conectado a una granja de servidores de Lync Server 2013 local.
  
Las ventajas de esta implementación le permiten:
  
- Usar el conjunto completo de características de Lync Server 2013.
    
- Aprovechar su equipo telefónico local existente (por ejemplo los sistemas PBX).
    
- Usar Exchange Online para el correo electrónico, lo que reduce la carga de almacenamiento y de los servidores de correo electrónico locales.
    
- Usar SharePoint Online para la colaboración, lo que reduce la carga de mantenimiento de servidores de SharePoint locales.
    
- Usar las características integradas de Lync, Exchange y SharePoint, incluida la mensajería unificada (UM) en Office 365.
    
#### <a name="exchange-server-with-lync-online"></a>Exchange Server con Lync Online

En el diagrama adjunto se muestra Office 365 con Lync Online, conectado a una granja de servidores de Exchange Server local.
  
Las ventajas de esta implementación le permiten:
  
- Aprovechar su actual infraestructura de Exchange.
    
- Usar Lync Online para funciones de presencia, mensajería instantánea y conferencias.
    

