---
title: "Ejemplo de diseño diagrama accesible - sitios de Internet de Microsoft Azure para SharePoint 2013"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: "Este artículo es una versión de texto accesible del diagrama Ejemplo de diseño: Sitios de Internet en Microsoft Azure con SharePoint Server 2013."
ms.openlocfilehash: 1d84900a931bf9a01cd2e757a5fc671455e076f5
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagrama accesible: Muestra de diseño. Sitios de Internet en Microsoft Azure para SharePoint 2013

**Resumen:** Este artículo es una versión de texto accesible del diagrama denominado diseño sample: sitios de Internet de Microsoft Azure para 2013 de SharePoint.
  
Utilice este ejemplo de diseño como punto de partida para un sitio en Internet en Azure usando SharePoint 2013.
  
Este póster muestra un ejemplo de cómo diseñar los siguientes aspectos de 2013 de SharePoint:
  
- Usuarios
    
- Zonas y autenticación
    
- Granja de servidores
    
- Sitio de administración
    
- Servicios
    
- Grupos de aplicaciones y aplicaciones web
    
- Colecciones de sitios
    
- Sitios
    
- Bases de datos de contenido
    
- Zonas y direcciones URL
    
## <a name="users-zones-and-authentication"></a>Usuarios, zonas y autenticación

Hay cuatro tipos de cuentas de usuario en este diseño. Cada tipo de cuenta está asociado con un sitio para el acceso y con una zona que usa un tipo de autenticación específico.  
  
- Los clientes anónimos, los clientes anónimos tienen acceso a través de un sitio, por ejemplo, http://www.contoso.com. La zona que utilizan es la "zona Internet / anónimos", que utiliza la autenticación anónima.
    
- Autenticar clientes: los clientes autenticados tienen acceso a través de un sitio como https://secure.contoso.com. La zona que utilizan es la "zona de Extranet / SAML", que utiliza Active Directory de Azure con autenticación SAML.
    
- Autores y los desarrolladores del sitio, los autores de sitios y los desarrolladores tienen acceso a través de sitios como http://authoring.contoso.com:8000 o http://www.contoso.com:8000. La zona que utilizan es la "zona predeterminada Windows integrada", que utiliza los servicios de dominio de Active Directory (AD DS).
    
- Cuenta de rastreo de búsqueda: La cuenta de rastreo de búsqueda tiene acceso a través de sitios como http://authoring.contoso.com:8000 o http://www.contoso.com:8000. La zona que se utiliza es la "zona predeterminada Windows integrada", que usa AD DS con autenticación Windows NTLM.
    
## <a name="server-farm"></a>Granja de servidores

Los usuarios acceden a la granja de servidores a través de Azure. La granja de servidores contiene uno o varios servidores web.
  
## <a name="administration-site"></a>Sitio de administración

El sitio de administración contiene varios servidores de aplicaciones, que se comunican con un grupo de aplicaciones (grupo de aplicaciones 1 en el ejemplo) que usa el sitio de Administración Central de la aplicación web. El sitio de Administración central proporciona acceso a las colecciones de sitios dentro de la organización.
  
El sitio de administración también contiene servidores de Base de datos SQL, que son servidores de base de datos con SQL Server instalado y configurado para admitir la agrupación en clústeres de SQL, la creación de reflejos o AlwaysOn (AlwaysOn solo se aplica a SQL Server 2012).
  
## <a name="services"></a>Servicios

En el ejemplo de diseño se muestra un sitio web de Internet Information Services (IIS) y SharePoint Web Services. SharePoint Web Services contiene un grupo de aplicaciones (grupo de aplicaciones 2) con tres servicios, perfil de usuario, búsqueda y metadatos administrados.
  
Notas sobre los servicios para sitios de Internet:
  
> Metadatos administrados, No olvide seleccionar **esta aplicación de servicio es la ubicación de almacenamiento predeterminada para conjuntos de términos específicos de la columna**.
    
> Administración de la aplicación: le aconsejamos que no use aplicaciones en un sitio de Internet público en Azure.
    
## <a name="application-pools-and-web-applications"></a>Grupos de aplicaciones y aplicaciones web

El grupo predeterminado en Azure muestra el grupo de aplicación 3, que contiene una aplicación web denominada Sitios de Contoso. Esta colección de sitios basados en la ruta de acceso se encuentra en http://internal:8000.
  
## <a name="site-collections-and-sites"></a>Sitios y colecciones de sitios

Estas son algunas de las colecciones de sitios que se incluyen en el grupo de aplicaciones:
  
- Colección de sitios denominados host 1 para rastreo (ubicación de ejemplo http://authoring.contoso.com:8000)
    
- Colección de sitios denominados host 2 para consultas (ubicaciones de ejemplo http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000)
    
- Colección de sitios denominados host 3 para consultas (ubicaciones de ejemplo http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Bases de datos de contenido

En el ejemplo se muestran dos bases de datos de contenido. Una es para la colección de sitios 1 usada para rastreo (http://authoring.contoso.com:8000). La otra es para las dos colecciones de sitios 2 y 3 que se usan para consultas (http://www.contoso.com, https://secure.contoso.com, http://www.contoso.com:8000 o http://assets.contoso.com, https://secureassets.contoso.com, http://assets.contoso.com:8000).
  
## <a name="zones-and-urls"></a>Zonas y direcciones URL

En el ejemplo se muestran tres zonas con las URL de carga equilibrada asociadas, usadas por distintas cuentas de usuario.  
  
La primera lista zonas y URL está relacionada con la colección de sitios 1 y contiene esta información:
  
- Usuarios: los autores de sitios
    
- Zona - predeterminado
    
- URL de carga equilibrada - http://authoring.contoso.com:8000
    
La segunda lista de zonas y URL tiene tres tipos diferentes de usuarios en tres zonas diferentes. Está relacionada con la colección de sitios 2 y contiene esta información:
  
Primera zona:
  
- Usuarios: los autores de sitios
    
- Zona - predeterminado
    
- URL de carga equilibrada - http://www.contoso.com:8000
    
Segunda zona:
  
- Usuarios: clientes anónimos
    
- Zona - Internet
    
- Equilibrio de carga de URL - http://www.contoso.com
    
Tercera zona:
  
- Usuarios: los clientes autenticados
    
- Zona - Extranet
    
- Equilibrio de carga de URL - https://secure.contoso.com
    
La tercera lista de zonas y URL tiene tres tipos diferentes de usuarios en tres zonas diferentes. Está relacionada con la colección de sitios 3 y contiene esta información:
  
Primera zona:
  
- Usuarios: los autores de sitios
    
- Zona - Internet
    
- URL de carga equilibrada - http://assets.contoso.com:8000
    
Segunda zona:
  
- Usuarios: clientes anónimos
    
- Zona - Internet
    
- Equilibrio de carga de URL - http://assets.contoso.com
    
Tercera zona:
  
- Usuarios: los clientes autenticados
    
- Zona - Extranet
    
- Equilibrio de carga de URL - http://secureassets.contoso.com
    

