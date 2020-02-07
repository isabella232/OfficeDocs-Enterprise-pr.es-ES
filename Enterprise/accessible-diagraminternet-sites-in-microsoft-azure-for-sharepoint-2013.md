---
title: Diagrama accesible Sitios de Internet en Microsoft Azure para SharePoint 2013
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: 71636974-fb99-487c-ac67-f15e9401acba
f1.keywords:
- NOCSH
description: Este artículo es una versión de texto accesible del diagrama con el nombre Sitios de Internet en Microsoft Azure para SharePoint 2013.
ms.openlocfilehash: a68c5f8a0e92c45e3c33caaca77be0d841aa6003
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41843901"
---
# <a name="accessible-diagram---internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagrama accesible: Sitios de Internet en Microsoft Azure para SharePoint 2013

**Resumen:** este artículo es una versión de texto accesible del diagrama “Sitios de Internet en Microsoft Azure para SharePoint 2013”.
  
Este póster describe e ilustra cómo los sitios de Internet públicos se benefician de la elasticidad de la nube y de Azure AD para cuentas de clientes. Hay seis diferentes escenarios que describen las ventajas de Azure para los sitios de Internet: 
  
- Diseño y cambio de tamaño de la topología de la granja de servidores. 
    
- Ajuste para Azure. 
    
- Elección del modelo de Active Directory. 
    
- Diseño de la administración de identidades, zonas y autenticación. 
    
- Diseño de sitios y URL para la publicación entre sitios. 
    
- Diseño del entorno de Azure. 
    
## <a name="design-and-size-the-farm-topology"></a>Diseño y cambio de tamaño de la topología de la granja de servidores

Use la guía sobre topología, capacidad y rendimiento de SharePoint 2013 que encontrará en TechNet para diseñar la topología de la granja de servidores. 
  
Asegúrese de que la granja de servidores que diseñe cumpla los objetivos de capacidad y rendimiento marcados. 
  
### <a name="example-medium-internet-sites-farm-85-page-views-per-second"></a>Ejemplo: Granja de servidores de sitios de Internet de tamaño medio (~85 vistas de página por segundo)

Esta granja ofrece una topología de granja de servidores de búsqueda de SharePoint 2013 con tolerancia a errores y optimizada para un conjunto de 3.400.000 elementos. 
  
La granja de servidores de ejemplo procesa de 100 a 200 documentos por segundo, en función del idioma, y admite 85 visualizaciones de página por segundo y 100 consultas por segundo. 
  
El diagrama adjunto muestra una granja de servidores de sitios de Internet de tamaño medio con tres tipos de servidores: 
  
- Servidores web 
    
- Servidores de aplicaciones 
    
- Servidores de base de datos 
    
#### <a name="web-servers"></a>Servidores web

En la sección de servidores web, hay tres servidores web, el Host A, el Host B y Host C. Cada servidor web contiene una memoria caché distribuida, perfiles de usuario, metadatos administrados y capacidades de procesamiento de consultas. También contienen una réplica de partición de índice que se encuentra en cada servidor. 
  
Para escalar horizontalmente, agregue otro servidor web con las mismas capacidades, esto permite tener 28 vistas de página por segundo adicionales. 
  
#### <a name="application-servers"></a>Servidores de aplicaciones

En la sección Servidores de aplicaciones, hay tres servidores de aplicaciones, el Host D, el Host E y el Host F. El Host D contiene componentes de procesamiento de rastreo, administración, análisis y contenido. El Host E contiene componentes de procesamiento de rastreo, administración y contenido. El Host F contiene componentes de procesamiento de rastreo y contenido. 
  
Para escalar horizontalmente, agregue un servidor de aplicaciones con un componente de rastreo y un componente de procesamiento de contenido para procesar 40 documentos más por segundo. 
  
#### <a name="database-servers"></a>Servidores de bases de datos

En la sección Servidores de bases de datos, hay dos servidores, el Host G y el Host H. Los servidores de bases de datos están en hosts emparejados para brindar tolerancia a errores. 
  
El Host G contiene todas bases de datos de SharePoint, incluida la base de datos de administración de búsqueda, la base de datos de vínculo, dos bases de datos de rastreo, una base de datos de análisis y el resto de bases de datos de SharePoint. El Host H contiene todas las bases de datos de SharePoint, incluidas copias redundantes de todas las bases de datos que usan clústeres de SQL, creación de reflejo o SQL Server 2012 AlwaysOn. 
  
## <a name="fine-tune-for-azure"></a>Ajuste para Azure

Podría ser necesario ajustar la granja de servidores de SharePoint para los conjuntos de disponibilidad en la plataforma de Azure. Para garantizar la alta disponibilidad de todos los componentes, asegúrese de que los roles de servidor estén configurados todos de forma idéntica. 
  
En el ejemplo de topología del diagrama: 
  
- Los servidores web y los servidores de bases de datos están configurados de forma idéntica. 
    
- Los tres servidores de aplicaciones no están configurados idénticamente. Estos roles de servidor requieren ajustes para los conjuntos de disponibilidad en Azure. 
    
### <a name="before"></a>Antes

La parte superior del diagrama muestra la granja de servidores de SharePoint antes del ajuste para los conjuntos de disponibilidad en Azure. En el diagrama, los tres servidores de aplicaciones host no están configurados de forma idéntica. El número de componentes queda determinado por los objetivos de rendimiento y capacidad de la granja de servidores. Los tres servidores están configurados como sigue: 
  
- El servidor de aplicaciones Host D está configurado con los roles de procesamiento de rastreo, administración, análisis y contenido. 
    
- El servidor de aplicaciones Host E está configurado con los roles de procesamiento de rastreo, administración y contenido. 
    
- El servidor de aplicaciones Host F está configurado con los roles de procesamiento de rastreo y contenido. 
    
### <a name="after"></a>Después

Esta parte del diagrama muestra la granja de servidores de SharePoint después del ajuste para los conjuntos de disponibilidad de Azure. Para adaptar esta arquitectura para Azure, replicaremos los cuatro componentes en los tres servidores. Esto incrementa el número de componentes más allá de lo necesario para obtener el rendimiento y capacidad buscados. A cambio, este diseño garantiza la alta disponibilidad de los cuatro componentes en la plataforma de Azure cuando estas tres máquinas virtuales están asignadas a un conjunto de disponibilidad. 
  
Los tres servidores están configurados para contar con los roles de procesamiento de rastreo, administración, análisis y contenido. 
  
## <a name="choose-the-active-directory-model"></a>Elección del modelo de Active Directory

Todas las soluciones de SharePoint requieren Servicios de dominio de Windows Active Directory (AD DS). Actualmente, existen dos opciones para las soluciones de SharePoint en Azure. 
  
- Opción 1: Dominio dedicado. Puede implementar un dominio dedicado y aislado en Azure para obtener compatibilidad para una granja de servidores de SharePoint. Esta es una buena opción para sitios de Internet públicos. 
    
- Opción 2: Extender el dominio local a través de una conexión VPN sitio a sitio. Cuando el dominio local se extiende a través de una conexión VPN sitio a sitio, los usuarios tienen acceso a la granja de servidores de SharePoint como si estuvieran hospedados localmente. Puede aprovechar las implementaciones existentes de Active Directory y DNS. 
    
## <a name="design-for-identity-management-zones-and-authentication"></a>Diseño de la administración de identidades, zonas y autenticación

### <a name="design-for-accounts-and-authentication"></a>Diseño de cuentas y autenticación

Determine cómo se administrarán las cuentas y qué tipo de autenticación se usará. 
  
#### <a name="accounts-for-site-developers-and-authors"></a>Cuentas para desarrolladores y creadores de sitios

- Agregue las cuentas al dominio en Azure. 
    
- Use los servicios de federación de Active Directory (AD FS) locales para federar las cuentas internas al dominio en Azure. 
    
- Si el diseño incluye una conexión VPN sitio a sitio, use las cuentas internas. 
    
#### <a name="accounts-for-customers"></a>Cuentas de clientes

- Use Azure Active Directory. 
    
- Use un proveedor basado en SAML diferente. 
    
### <a name="design-for-zones"></a>Diseño de zonas

En SharePoint 2013, la administración de identidades se incluye en la configuración de las zonas y la autenticación. 
  
Este diseño distingue claramente entre las cuentas de los clientes y las demás cuentas. 
  
- Use este diseño si desea que las cuentas de clientes se traten de forma completamente distinta a como se tratan las cuentas internas de creadores y desarrolladores de sitios. 
    
- Mediante el uso de este diseño, puede usar directivas de zona para limitar las acciones del cliente dentro de una aplicación web. 
    
- Con este diseño se obtienen direcciones URL diferentes para las cuentas de clientes y para las cuentas internas. 
    
En este ejemplo: 
  
- Configure la zona predeterminada para las cuentas internas. 
    
- Configure la zona de extranet para el acceso autenticado de clientes. Use Azure Active Directory (AD) para las cuentas de cliente o use un proveedor basado en SAML diferente. 
    
- Configure la zona de Internet para el acceso anónimo. 
    
No use un diseño de dos zonas en el que todos los usuarios autenticados estén configurados para usar la zona predeterminada. 
  
El diagrama adjunto muestra un diseño de tres zonas que distingue entre cuentas internas y de clientes. 
  
Los visitantes y clientes tienen acceso al inquilino de Azure AD en la granja de servidores de SharePoint 2013 a través de aplicaciones web en una de dos zonas. Las dos zonas son: 
  
- Zona: Internet para los usuarios anónimos 
    
- Zona: Extranet para los usuarios autenticados 
    
Los usuarios con cuentas internas tienen acceso al inquilino de Azure Active Directory desde de AD DS y AD FS en el entorno local a través del túnel de VPN a Azure AD. La zona predeterminada proporciona la autenticación de Windows (NTLM). 
  
### <a name="design-for-connecting-to-azure-ad"></a>Diseño para la conexión a Azure AD

 Azure AD proporciona capacidades de control de acceso y administración de identidades para servicios en la nube. Las capacidades incluyen almacenamiento basado en la nube para los datos del directorio y un conjunto principal de servicios de identidad (que comprende los procesos de inicio de sesión de usuarios, los servicios de autenticación y AD FS). Los servicios de identidad que se incluyen con Azure AD se integran fácilmente en las implementaciones locales de AD DS y son totalmente compatibles con los proveedores de identidades de terceros.
  
El diagrama adjunto muestra el siguiente escenario: 
  
Al integrar SharePoint 2013 con Azure Active Directory, el servicio de Control de acceso (ACS) de Azure cumple dos propósitos: 
  
-  Azure AD usa SAML 2.0 y SharePoint únicamente funciona con SAML 1.1. ACS admite ambos formatos y actúa como intermediario para transformar los formatos de token entre SharePoint y Azure AD.
    
- ACS reemplaza la necesidad del servicio de token de seguridad del proveedor de identidades (STS de IP) para este escenario de SAML. 
    
Para obtener más información, consulte el tema sobre configuración de Azure AD con SharePoint 2013 en la biblioteca de TechNet. 
  
## <a name="design-sites-and-urls-for-cross-site-publishing"></a>Diseño de sitios y URL para la publicación entre sitios

Se recomienda usar un diseño de una aplicación web para los escenarios de publicación. 
  
- Las funciones tanto de creación como de publicación de sitios están en la misma aplicación web. 
    
- La publicación en varios sitios se usa para publicar activos. 
    
Use colecciones de sitios con nombre de host y basados en rutas de acceso. 
  
- Es necesario contar con una colección de sitios raíz. Cree este sitio como un sitio basado en la ruta de acceso. 
    
- Cree el resto de las colecciones de sitios como colecciones con nombre de host. 
    
Direcciones URL de aplicaciones web y sitios raíz 
  
- Use un nombre interno para la URL de la aplicación web. SharePoint usa el nombre de la máquina local como nombre predeterminado a menos que se especifique un nombre distinto. Puede usar un nombre de dominio reservado para el entorno de red interno. 
    
- SharePoint asigna un número de puerto no estándar al momento de crear la aplicación web. Use este número de puerto en lugar del puerto 80 o el puerto 443. O use un número de puerto diferente pero que no sea estándar. 
    
- Use el mismo nombre y número de puerto que usó para la colección de sitios raíz, que es una colección de sitios basados en rutas de acceso. 
    
El diagrama adjunto muestra servicios para grupos de aplicaciones, como el servicio de búsqueda, interactuando con la colección de sitios que usan aplicaciones web. Las colecciones de sitios mostradas incluyen: 
  
- Una colección de sitios basados en la ruta de acceso que se encuentra en https://internal:8000 (sitio raíz). 
    
- Rastreo: Colecciones de sitios con nombre de host ubicadas en una dirección como https://authoring.contoso.com:8000. 
    
- Consultas: Dos colecciones de sitios independientes con nombre de host que se encuentran en direcciones como: 
    
  - https://www.contoso.com 
    
  - https://secure.contoso.com 
    
  - https://www.contoso.com:8000 
    
  - https://assets.contoso.com 
    
  - https://secureassets.contoso.com 
    
  - https://assets.contoso.com:8000 
    
## <a name="design-the-azure-environment"></a>Diseño del entorno de Azure

Esta arquitectura de ejemplo incluye los siguientes elementos: 
  
- Una conexión VPN sitio a sitio que es opcional y extiende Windows AD DS local y el entorno de DNS local a la red virtual en Azure. 
    
- Opcionalmente, puede usar un dominio dedicado en Azure para la compatibilidad con la granja de servidores de SharePoint. 
    
- Los servidores se dividen entre los servicios en la nube de Azure según su rol. 
    
- Conjuntos de disponibilidad que aseguran la alta disponibilidad de los roles de servidor configurados de forma idéntica. 
    
Para obtener más información, consulte el artículo de TechNet sobre arquitecturas de Azure para soluciones de SharePoint. 
  
El diagrama adjunto muestra un ejemplo de un entorno local conectado con una red virtual de Azure. 
  
En el entorno local, que es un elemento opcional del entorno de Azure, se incluyen los siguientes componentes: 
  
- RRAS de Windows Server 2012 
    
- AD DS 
    
- Una puerta de enlace de VPN desde Windows Server y AD DS a la subred de la puerta de enlace de VPN activa 
    
El entorno de red virtual de Azure incluye los siguientes componentes: 
  
- La subred de la puerta de enlace de VPN activa (superpuesta con el entorno local, si es aplicable) 
    
- Un servicio en la nube que incluye un conjunto de disponibilidad de AD DS y DNS (dos servidores) 
    
- Un servicio en la nube que incluye el conjunto de disponibilidad del servidor front-end (tres servidores de SharePoint) y el conjunto de disponibilidad del servidor de aplicaciones (tres servidores de SharePoint) 
    
- Un servicio de nube que contiene dos conjuntos de disponibilidad de bases de datos 
    

