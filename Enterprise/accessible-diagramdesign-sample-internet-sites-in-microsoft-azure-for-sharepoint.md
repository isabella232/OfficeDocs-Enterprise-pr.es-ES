---
title: 'Diagrama accesible: sitios de Internet de ejemplo de diseño en Microsoft Azure para SharePoint 2013'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.collection: Ent_O365
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.assetid: b91124bc-c7ec-4929-b77c-d6293db9f15e
description: 'Este artículo es una versión de texto accesible del diagrama Ejemplo de diseño: Sitios de Internet en Microsoft Azure con SharePoint Server 2013.'
ms.openlocfilehash: 52ae615cbdc6a355155e54e36bc6a3d733d84869
ms.sourcegitcommit: 35c04a3d76cbe851110553e5930557248e8d4d89
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2019
ms.locfileid: "38027634"
---
# <a name="accessible-diagram---design-sample-internet-sites-in-microsoft-azure-for-sharepoint-2013"></a>Diagrama accesible: Muestra de diseño. Sitios de Internet en Microsoft Azure para SharePoint 2013

**Resumen:** Este artículo es una versión de texto accesible del diagrama ejemplo de diseño: sitios de Internet en Microsoft Azure para SharePoint 2013.
  
Use este ejemplo de diseño como punto de partida para un sitio orientado a Internet en Azure con SharePoint 2013.
  
En este póster se muestra un ejemplo de cómo diseñar los siguientes aspectos de SharePoint 2013:
  
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
  
- Clientes anónimos: los clientes anónimos tienen acceso a través https://www.contoso.comde un sitio como. La zona que usan es la "zona de Internet/anónima", que usa la autenticación anónima.
    
- Clientes autenticados: los clientes autenticados tienen acceso a través de un https://secure.contoso.comsitio como. La zona que usan es la "zona de extranet/SAML", que usa Azure Active Directory con autenticación SAML.
    
- Autores y desarrolladores de sitios: los autores y programadores de sitios tienen acceso https://authoring.contoso.com:8000 a https://www.contoso.com:8000través de sitios como o. La zona que usan es la "zona predeterminada de Windows/integrada", que usa los servicios de dominio de Active Directory (AD DS).
    
- Cuenta de rastreo de búsqueda: la cuenta de rastreo de búsqueda https://authoring.contoso.com:8000 tiene https://www.contoso.com:8000acceso a través de sitios como o. La zona que usa es la "zona predeterminada integrada en Windows", que usa AD DS con autenticación NTLM de Windows.
    
## <a name="server-farm"></a>Granja de servidores

Los usuarios acceden a la granja de servidores a través de Azure. La granja de servidores contiene uno o varios servidores web.
  
## <a name="administration-site"></a>Sitio de administración

El sitio de administración contiene varios servidores de aplicaciones, que se comunican con un grupo de aplicaciones (grupo de aplicaciones 1 en el ejemplo) que usa el sitio de Administración Central de la aplicación web. El sitio de Administración central proporciona acceso a las colecciones de sitios dentro de la organización.
  
El sitio de administración también contiene servidores de Base de datos SQL, que son servidores de base de datos con SQL Server instalado y configurado para admitir la agrupación en clústeres de SQL, la creación de reflejos o AlwaysOn (AlwaysOn solo se aplica a SQL Server 2012).
  
## <a name="services"></a>Servicios

En el ejemplo de diseño se muestra un sitio web de Internet Information Services (IIS) y SharePoint Web Services. SharePoint Web Services contiene un grupo de aplicaciones (grupo de aplicaciones 2) con tres servicios, perfil de usuario, búsqueda y metadatos administrados.
  
Notas sobre los servicios para sitios de Internet:
  
> Metadatos administrados: no olvide seleccionar **Esta aplicación de servicio es la ubicación de almacenamiento predeterminada para conjuntos de términos específicos de columnas**.
    
> Administración de la aplicación: le aconsejamos que no use aplicaciones en un sitio de Internet público en Azure.
    
## <a name="application-pools-and-web-applications"></a>Grupos de aplicaciones y aplicaciones web

El grupo predeterminado en Azure muestra el grupo de aplicación 3, que contiene una aplicación web denominada Sitios de Contoso. Esta colección de sitios basada en rutas de acceso https://internal:8000se encuentra en.
  
## <a name="site-collections-and-sites"></a>Sitios y colecciones de sitios

Estas son algunas de las colecciones de sitios que se incluyen en el grupo de aplicaciones:
  
- Colección de sitios con nombre de host 1 para el rastreo (ubicación de ejemplohttps://authoring.contoso.com:8000)
    
- Colección de sitios con nombre de host 2 para consultas ( https://www.contoso.comubicaciones https://secure.contoso.comde ejemplo,,https://www.contoso.com:8000)
    
- Colección de sitios con nombre de host 3 para consultas ( https://assets.contoso.comubicaciones https://secureassets.contoso.comde ejemplo,,https://assets.contoso.com:8000)
    
## <a name="content-databases"></a>Bases de datos de contenido

En el ejemplo se muestran dos bases de datos de contenido. Una es para la colección de sitios 1 que se usa parahttps://authoring.contoso.com:8000)el rastreo (. La otra es para las dos colecciones de sitios 2 y 3 usadas para lashttps://www.contoso.comconsultas https://secure.contoso.com( https://www.contoso.com:8000,, https://assets.contoso.como https://secureassets.contoso.com, https://assets.contoso.com:8000),.
  
## <a name="zones-and-urls"></a>Zonas y direcciones URL

En el ejemplo se muestran tres zonas con las URL de carga equilibrada asociadas, usadas por distintas cuentas de usuario.  
  
La primera lista zonas y URL está relacionada con la colección de sitios 1 y contiene esta información:
  
- Usuarios-autores de sitios
    
- Zona-predeterminada
    
- URL de carga equilibrada:https://authoring.contoso.com:8000
    
La segunda lista de zonas y URL tiene tres tipos diferentes de usuarios en tres zonas diferentes. Está relacionada con la colección de sitios 2 y contiene esta información:
  
Primera zona:
  
- Usuarios-autores de sitios
    
- Zona-predeterminada
    
- URL de carga equilibrada:https://www.contoso.com:8000
    
Segunda zona:
  
- Usuarios: clientes anónimos
    
- Zona: Internet
    
- URL de carga equilibrada:https://www.contoso.com
    
Tercera zona:
  
- Clientes autenticados por usuarios
    
- Zone-extranet
    
- URL de carga equilibrada:https://secure.contoso.com
    
La tercera lista de zonas y URL tiene tres tipos diferentes de usuarios en tres zonas diferentes. Está relacionada con la colección de sitios 3 y contiene esta información:
  
Primera zona:
  
- Usuarios-autores de sitios
    
- Zona: Internet
    
- URL de carga equilibrada:https://assets.contoso.com:8000
    
Segunda zona:
  
- Usuarios: clientes anónimos
    
- Zona: Internet
    
- URL de carga equilibrada:https://assets.contoso.com
    
Tercera zona:
  
- Clientes autenticados por usuarios
    
- Zone-extranet
    
- URL de carga equilibrada:https://secureassets.contoso.com
    

