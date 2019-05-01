---
title: Diagrama accesible Opciones de plataformas de Microsoft SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b88200bf-ced0-4ae6-bbe5-5517377d1be1
description: Este artículo es una versión de texto accesible del diagrama Opciones de plataforma para Microsoft SharePoint 2013.
ms.openlocfilehash: 1f0d2bf4e74c7e1d28aaa27c6f88dac04f02b4a9
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33487826"
---
# <a name="accessible-diagram---microsoft-sharepoint-2013-platform-options"></a>Diagrama accesible: Opciones de plataformas de Microsoft SharePoint 2013

**Resumen:** este artículo es una versión de texto accesible del diagrama “Opciones de plataforma para Microsoft SharePoint 2013”.
  
Todo lo que los arquitectos y los responsables de decisiones empresariales necesitan saber sobre Office 365, Microsoft Azure y las implementaciones locales. 
  
Este póster tiene dos secciones: 
  
- Una comparación de cuatro implementaciones diferentes de SharePoint 2013: SharePoint en Office 365, un híbrido de Office 365 con una implementación local de SharePoint 2013, Azure y una implementación local de SharePoint 2013. 
    
- Una descripción de tres cargas de trabajo típicas para pasar a Azure. 
    
## <a name="comparison-of-four-different-deployments-for-the-sharepoint-2013-platform"></a>Comparación de cuatro implementaciones diferentes para la plataforma de SharePoint 2013

La comparación proporciona información sobre cada opción de implementación relacionada con las siguientes áreas: 
  
- Información general sobre las diferentes características de implementación 
    
- ¿Para qué es más adecuado cada tipo de implementación? 
    
- Requisitos de licencia 
    
- Tareas de arquitectura necesarias para implementar 
    
- Responsabilidades de los profesionales de TI para la implementación 
    
### <a name="overview"></a>Información general

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 en Office 365

Aumente su eficiencia y optimice los costos con los planes multiempresa de Office 365. 
  
El diagrama adjunto muestra SharePoint Online con un inquilino de Azure Active Directory que sincroniza nombres de cuentas y contraseñas entre el entorno local de Active Directory y el inquilino de Azure Active Directory. 
  
Descripción de las características: 
  
- Software como servicio (SaaS).  
    
- El amplio conjunto de características siempre está actualizado. 
    
- Incluye un inquilino de Azure Active Directory (se puede usar con otras aplicaciones). 
    
- La integración de directorios incluye la sincronización de nombres de cuentas y contraseñas entre el entorno de Active Directory local y el inquilino de Azure Active Directory. 
    
- Si se requiere inicio de sesión único (SSO), se pueden implementar los Servicios de federación de Active Directory (AD FS). 
    
- Comunicación con cliente por Internet mediante acceso cifrado y con autenticación (puerto 443). 
    
- La migración de datos se limita a lo que se puede cargar por Internet. 
    
- Personalizaciones: Aplicaciones para Office, SharePoint y SharePoint Designer 2013. 
    
#### <a name="hybrid-with-office-365"></a>Implementación híbrida con Office 365

Combine las ventajas de Office 365 con una implementación local de SharePoint 2013. 
  
En el diagrama adjunto se muestra Office 365 con SharePoint Online usando Servicios de conectividad empresarial (BCS) para conectarse a una granja de SharePoint Server 2013 local. 
  
Elija cuál de las siguientes características desea integrar: 
  
SharePoint Search 
  
- Los usuarios pueden ver los resultados de búsqueda de los dos entornos. 
    
- Los usuarios de la extranet pueden iniciar sesión de forma remota con una cuenta de Active Directory local y usar todas las funciones híbridas disponibles. 
    
BCS
  
De SharePoint Online: los usuarios pueden realizar operaciones de lectura y escritura. El servicio BCS se conecta a una granja de SharePoint Server 2013 local. El servicio BCS configurado en la granja local negocia la conexión con los extremos locales del servicio OData. 
  
Duet Enterprise Online 
  
Desde SharePoint Online, los usuarios pueden realizar operaciones de lectura y escritura en un sistema SAP local. 
  
#### <a name="azure"></a>Azure

Aproveche las ventajas que le ofrece la nube a la vez que mantiene el control total sobre la plataforma y las funciones. 
  
En el diagrama adjunto se muestra Azure, que contiene dos servicios en la nube, una granja de SharePoint 2013 y Windows Server Active Directory con DNS; se conecta con los usuarios a través de Internet o se conecta a una implementación local de Active Directory mediante un túnel VPN. 
  
Entre las características se incluyen: 
  
-  Azure es una plataforma que ofrece la infraestructura y los servicios de aplicaciones necesarios para hospedar una granja de SharePoint 2013.
    
- Servicios de infraestructura. 
    
- Mejor plataforma en la nube nativa para SQL Server y SharePoint. 
    
- Los recursos informáticos están disponibles prácticamente de inmediato, sin concesiones. 
    
- Dé prioridad a las aplicaciones, en lugar de los centros de datos y las infraestructuras. 
    
- Entornos de desarrollo y de pruebas económicos. 
    
- Es posible acceder a las soluciones de SharePoint desde Internet o bien únicamente desde un entorno corporativo mediante un túnel VPN de sitio a sitio. 
    
- Personalizaciones sin límite. 
    
#### <a name="on-premises"></a>Implementación local

Tiene la propiedad de todo. 
  
En el diagrama adjunto se muestra un entorno local con servidores web, servidores de aplicaciones y Active Directory, que se comunica con todas las bases de datos y los servidores de aplicaciones dedicados para la búsqueda. 
  
Entre las características se incluyen:  
  
- Planeamiento de la capacidad y ajuste del tamaño. 
    
- Adquisición y configuración de servidores. 
    
- Implementación. 
    
- Escalado horizontal, revisiones y operaciones. 
    
- Copias de seguridad de datos. 
    
- Mantenimiento de un entorno de recuperación ante desastres. 
    
- Personalizaciones sin límite. 
    
### <a name="deployment-type-is-best-for---"></a>Tipo de implementación idóneo para...

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 en Office 365

- Colaboración y uso compartido con el exterior de forma segura (característica única). 
    
- Intranet: sitios de equipo, Mis sitios y colaboración interna. 
    
- Almacenamiento de documentos y control de versiones en la nube. 
    
- Sitio web básico de orientación pública. 
    
Características adicionales con los planes de suscripción dedicada de Office 365: 
  
- Equipo de centro de datos de Microsoft dedicado a su organización, que no se comparte con ninguna otra. 
    
- El entorno de cada cliente reside en una red físicamente separada. 
    
- Comunicación con el cliente mediante una red VPN con protección IPSec o una conexión privada propiedad del cliente. Autenticación en dos fases opcional. 
    
- Planes de compatibilidad con ITAR. 
    
#### <a name="hybrid-with-office-365"></a>Implementación híbrida con Office 365

- Use Office 365 para colaboración y uso compartido con el exterior, en lugar de establecer un entorno de extranet. 
    
- Mueva Mis sitios (OneDrive para la Empresa) a la nube para facilitar a los usuarios el acceso a sus archivos de forma remota. 
    
- Inicie nuevos sitios de grupo en Office 365. 
    
- Integre un sitio de Office 365 con el entorno de BCS de SharePoint local. 
    
#### <a name="azure"></a>Azure

- SharePoint para Internet Sites: sitios de orientación pública. Aproveche Azure AD para cuentas de cliente y autenticación. 
    
- Entornos de desarrollo, pruebas y almacenamiento provisional: aprovisionar y desaprovisionar entornos completos rápidamente. 
    
- Aplicaciones híbridas: aplicaciones presentes en el centro de datos y la nube. 
    
- Entorno de recuperación ante desastres: disfrutar de recuperación rápida en caso de desastre. Pague solo según uso. 
    
- Granjas que requieren auditorías o informes detallados. 
    
- Análisis web. 
    
- Cifrado de datos en reposo (los datos se cifran en las bases de datos SQL). 
    
#### <a name="data-encryption-at-rest-data-is-encrypted-in-the-sql-databases"></a>Cifrado de datos en reposo (los datos se cifran en las bases de datos SQL)

- Granjas en territorio nacional (cuando los datos deben encontrarse en el marco geográfico de una jurisdicción). 
    
- Soluciones de BI complejas que deben residir cerca de los datos de BI. 
    
- Soluciones de nube privada. 
    
- Soluciones muy personalizadas. 
    
- Soluciones heredadas con componentes de terceros que dependen de hardware y software que no son compatibles con Servicios de infraestructura de Azure. 
    
- Restricciones de privacidad que impiden la sincronización de cuentas de Active Directory con Azure Active Directory (un requisito para Office 365). 
    
- Ideal para organizaciones que prefieren tener el control completo de la plataforma y la solución. 
    
### <a name="license-requirements"></a>Requisitos de licencia

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 en Office 365

Modelo de suscripción. No se requieren licencias adicionales. 
  
#### <a name="hybrid-with-office-365"></a>Implementación híbrida con Office 365

- Office 365: modelo de suscripción. No se requieren licencias adicionales. 
    
- Implementación local: se aplican todas las licencias locales. 
    
#### <a name="azure"></a>Azure

-  Suscripción de Azure (incluye el sistema operativo del servidor)
    
- SQL Server 
    
- Licencia de servidor de SharePoint 2013 
    
- Licencia de acceso de cliente de SharePoint 2013 
    
#### <a name="on-premises"></a>Implementación local

- Sistema operativo del servidor 
    
- SQL Server 
    
- Licencia de servidor de SharePoint 2013 
    
- Licencia de acceso de cliente de SharePoint 2013 
    
### <a name="architecture-tasks"></a>Tareas de arquitectura

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 en Office 365

- Planee y diseñe la integración de directorios. Dos opciones. Cualquier de las dos opciones se puede implementar de forma local o en Azure: Sincronización de contraseñas (requiere un servidor de 64 bits). SSO (requiere AD FS y varios servidores). 
    
- Garantice la capacidad de la red y la disponibilidad a través de firewalls, servidores proxy, puertas de enlace y vínculos WAN. 
    
- Adquirir certificados SSL de terceros para proporcionar seguridad empresarial para las ofertas de servicio de Office 365. 
    
- Planee el nombre del inquilino y diseñe el gobierno y la arquitectura de la colección de sitios. 
    
- Planee personalizaciones, soluciones y aplicaciones para SharePoint Online. 
    
- Decida si desea conectarse a Office 365 usando el protocolo de Internet 6 (IPv6). Esta opción es poco frecuente. 
    
#### <a name="hybrid-with-office-365"></a>Implementación híbrida con Office 365

Además de las tareas para entornos Office 365 y locales: 
  
- Determine qué nivel de integración de características desea y elija la topología híbrida. Vea este póster modelo: ¿Qué topología híbrida debo usar? 
    
- Si es necesario, determine qué dispositivo servidor proxy se usará. 
    
#### <a name="azure"></a>Azure

Diseñar el entorno de red de Azure: 
  
- Red virtual en Azure, incluidas las subredes. 
    
- Entorno de dominio e integración con servidores locales. 
    
- Direcciones IP y DNS. 
    
- Grupos de afinidad y cuentas de almacenamiento. 
    
Diseñar el entorno de SharePoint en Azure: 
  
- Topología de granja de SharePoint y arquitectura lógica. 
    
-  Conjuntos de disponibilidad de Azure y dominios de actualización.
    
- Tamaños de máquinas virtuales. 
    
- Extremo con equilibrio de carga. 
    
- Extremos externos para acceso público, si se prefiere así. 
    
- Entorno de recuperación ante desastres. 
    
#### <a name="on-premises"></a>Implementación local

Diseñar el entorno de SharePoint en un entorno local existente: 
  
- Topología de granja de SharePoint y arquitectura lógica.  
    
- Hardware de servidores. 
    
- Entorno virtual, si se usa. 
    
- Equilibrio de carga. 
    
- Integración con AD DS y DNS. 
    
- Entorno de recuperación ante desastres. 
    
### <a name="it-pro-responsibilities"></a>Responsabilidades del profesional de TI

#### <a name="sharepoint-2013-in-office-365"></a>SharePoint 2013 en Office 365

- Asegurarse de que las estaciones de trabajo de los usuarios cumplen los requisitos previos de cliente de Office 365. 
    
- Implementar el plan de integración de directorios. 
    
- Planee e implemente enrutamiento y registros DNS internos y externos. 
    
- Configurar el proxy o el servidor de seguridad conforme a los requisitos de dirección IP y URL de Office 365. 
    
- Cree y asigne permisos a colecciones de sitios. 
    
- Implemente personalizaciones, soluciones y aplicaciones para SharePoint Online. 
    
- Supervise la disponibilidad de red e identifique posibles cuellos de botella. 
    
#### <a name="hybrid-with-office-365"></a>Implementación híbrida con Office 365

Además de las tareas para entornos Office 365 y locales: 
  
- Configure el servidor proxy, si es necesario. 
    
- Configure la infraestructura híbrida de administración de identidades: SSO y autenticación de servidor a servidor entre los dos entornos. 
    
- Configurar la integración de las características elegidas: búsqueda, BCS, Duet Enterprise Online. 
    
#### <a name="azure"></a>Azure

Implementar y administrar el entorno de Azure y SharePoint: 
  
- Implemente y administre el entorno de red de Azure. 
    
- Implemente el entorno de SharePoint. 
    
- Actualice los servidores de la granja de SharePoint. 
    
- Agregue o desconecte máquinas virtuales según sea necesario en función del uso de la granja. 
    
- Aumente o reduzca el tamaño de las máquinas virtuales, en función de las necesidades. 
    
- Haga copia de seguridad del entorno de SharePoint. 
    
- Implemente el entorno de recuperación ante desastres y el protocolo.  
    
#### <a name="on-premises"></a>Implementación local

Implementar y administrar el entorno SharePoint local: 
  
- Aprovisionar servidores. 
    
- Implementar el entorno SharePoint. 
    
- Actualice los servidores de la granja de SharePoint. 
    
- Agregue o quite servidores de la granja según sea necesario en función del uso de la granja de servidores. 
    
- Haga copia de seguridad del entorno de SharePoint. 
    
- Implemente el entorno de recuperación ante desastres y el protocolo. 
    
## <a name="three-typical-workloads-to-move-to-azure"></a>Tres cargas de trabajo típicas para pasar a Azure

### <a name="office-365-plus-directory-components-in-azure"></a>Office 365 y componentes de directorio de Azure

Implementar los componentes de integración de directorios de Office 365 en Azure es más rápido porque permite implementar máquinas virtuales a petición. 
  
#### <a name="directory-synchronization-server-only"></a>Solo servidor de sincronización de directorios

En lugar de implementar el servidor de sincronización de directorios de 64 bits en el entorno local, se aprovisiona una máquina virtual en Azure. 
  
En el diagrama adjunto se muestra SharePoint Online con un inquilino de Azure Active Directory que sincroniza nombres de cuentas y contraseñas entre el entorno local de Active Directory y el inquilino de Azure Active Directory. 
  
#### <a name="directory-synchronization-plus-ad-fs"></a>Sincronización de directorios + AD FS

Gracias a esta opción, se admiten las identidades federadas de Office 365 sin necesidad de agregar hardware a la infraestructura local. También ofrece resistencia si el entorno de Active Directory local no está disponible. 
  
- Los componentes de integración de directorios residen en Azure. 
    
- AD FS se publica en Internet a través de servidores proxy de AD FS en Azure. 
    
- En el caso de usuarios que se conectan desde cualquier ubicación, el tráfico de autenticación de cliente se controla a través de servidores de AD FS y servidores proxy que se encuentran implementados en Azure. 
    
### <a name="public-facing-internet-site-and-azure-ad-for-customer-authentication"></a>Sitio de Internet de orientación pública y Azure AD para autenticación de clientes

Traiga su sitio de Internet a Azure y disfrute de la posibilidad de escalar recursos fácilmente según sus necesidades. Use Azure AD para almacenar cuentas de clientes. 
  
#### <a name="azure-advantages-for-internet-sites"></a>Ventajas de Azure para sitios de Internet

- Pague solo por los recursos que necesite ampliando el número de máquinas virtuales en función del uso de la granja de servidores. 
    
- Agregue informes detallados y análisis web. 
    
- Céntrese en desarrollar un sitio impresionante en lugar de tener que crear una infraestructura. 
    
#### <a name="azure-ad"></a>Azure AD

Azure AD proporciona capacidades de control de acceso y administración de identidades para servicios en la nube. Entre las capacidades se incluye un almacén basado en la nube para los datos del directorio y un conjunto esencial de servicios de identidad (que incluye procesos de inicio de sesión del usuario, servicios de autenticación y AD FS). Los servicios de identidad que se incluyen con Azure AD se integran fácilmente en las implementaciones locales de Active Directory y son totalmente compatibles con los proveedores de identidades de terceros. 
  
En el diagrama adjunto se muestra la configuración de las zonas y la autenticación que son importantes para los sitios orientados a Internet. En el diagrama se muestra el inquilino de Azure Active Directory, que contiene una granja de SharePoint en Azure con dos zonas: 
  
- Una zona de Internet que interactúa con los visitantes anónimos y autenticados y clientes fuera de la red. 
    
- Una zona predeterminada que contiene NTLM para rastreo y la autenticación de Windows que interactúa con la implementación local de Active Directory a través de un túnel VPN. 
    
### <a name="on-premises-farm-plus-disaster-recovery-in-azure"></a>Granja local y recuperación ante desastres en Azure

Elija una opción de recuperación ante desastres que se adapte a los requisitos de su empresa. Azure ofrece opciones básicas para empresas que están comenzando en la recuperación ante desastres, así como opciones avanzadas para empresas que requieren un alto nivel de resistencia. 
  
#### <a name="cold-standby"></a>Espera pasiva

- La granja de servidores se ha creado por completo, pero las máquinas virtuales están detenidas (solo paga cuando se están ejecutando). 
    
- Para realizar el mantenimiento del entorno, hay que iniciar las máquinas virtuales de vez en cuando, revisar, actualizar y comprobar el entorno. 
    
- En caso de desastre, inicie el entorno completo. 
    
#### <a name="warm-standby"></a>Espera semiactiva

- Incluye una pequeña granja aprovisionada y en funcionamiento. 
    
- La granja puede atender a los usuarios inmediatamente en caso de conmutación por error. 
    
- Puede ampliar la granja con rapidez para dar servicio a toda la base de usuarios. 
    
#### <a name="hot-standby"></a>Espera activa

Se aprovisiona y ejecuta una granja completa en modo de espera. 
  
En el diagrama adjunto se muestra una granja local que interactúa con el entorno de recuperación ante desastres de SharePoint en Azure. Las bases de datos locales usan el trasvase de registros de SQL Server a través del túnel VPN para acceder al entorno de recuperación ante desastres de SharePoint, que incluye dos servidores de Base de datos SQL que contienen las bases de datos de SharePoint, dos servidores front-end web y dos servidores de aplicaciones de SharePoint. 
  

