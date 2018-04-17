---
title: Experiencia del usuario en un entorno de multgeo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Obtener información sobre la experiencia de usuario de SharePoint y OneDrive en un entorno multi-geo.
ms.openlocfilehash: 42e384d3e93ca3f5a06a8ee07a37b10e21477038
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Experiencia del usuario en un entorno multi-geo

Aquí es lo que verán los usuarios en una configuración OneDrive Multi-Geo:

#### <a name="users-onedrive-for-business-location"></a>OneDrive de usuario para la ubicación de la empresa

Los usuarios tendrán su OneDrive para el negocio aprovisionado en su ubicación de datos preferido. Si un usuario se desplaza a una dirección URL de OneDrive que contiene una ubicación geográfica incorrecta (por ejemplo, un marcador de una ubicación geográfica anterior), se le dirigirá automáticamente a la OneDrive en la ubicación geográfica correspondiente.

#### <a name="sharing"></a>Uso compartido

La experiencia de selector de personas muestra todos los usuarios independientemente de su ubicación geográfica. Esto permite que un usuario comparta con otro usuario en su mismo geográfico o de cualquier otra de ubicaciones de geo de su arrendatario. Geo diferentes ubicaciones se mostrarán en la vista **compartida conmigo** en OneDrive del usuario para el negocio y se pueden acceder con Single Sign On experiencia independientemente de qué ubicación geográfica se aloja en contenido.

#### <a name="office-applications"></a>Aplicaciones de Office

Aplicaciones de Office como Word, Excel y PowerPoint detectará automáticamente el OneDrive correcto para la ubicación geográfica de negocios para cada usuario cuando inician sesión. Los usuarios no necesitan especificar la URL específica de geo para su OneDrive.

#### <a name="onedrive-for-business-sync-client"></a>OneDrive para el cliente de sincronización del negocio

La OneDrive para el cliente de sincronización Business (versión 17.3.6943.0625 y posteriores) detectará automáticamente el OneDrive correcto para la ubicación geográfica de negocio para el usuario.

#### <a name="office-365-app-launcher"></a>Iniciador de aplicaciones de Office 365

El iniciador de la aplicación es Multi-Geo y dirigirá cada mosaico a la ubicación geográfica correspondiente de la carga de trabajo. El OneDrive mosaico apunta a la ubicación correcta geo donde se aloja la biblioteca del usuario OneDrive, mientras que el mosaico de SharePoint seleccione todos los usuarios en la ubicación central, como sitios de grupo siguen alojados allí.

#### <a name="delve-user-profiles"></a>Profundizar los perfiles de usuario

Información de perfil de usuario es usado en la ubicación del usuario geo. Al seleccionar un usuario, se le dirigirá a la ubicación geográfica apropiada para el usuario, donde podrá ver sus detalles de perfil completo.

Si Delve está desactivado, se verá el perfil clásico de experiencia en SharePoint, lo que no es multi-geo.

#### <a name="delve"></a>Delve

Para los usuarios de Office 365 que se encuentran en las instancias de satélite, Multi-Geo profundizar es compatible con la limitación de Delve no se vincula a entradas de blog de SharePoint escritos por usuarios de otras regiones, sólo a los sitios de blogs de SharePoint.

#### <a name="search"></a>Búsqueda

Cada ubicación geográfica tiene su propio centro de búsqueda e índices de búsqueda. Cuando un usuario realiza una búsqueda, la consulta se envía a todas las ubicaciones de geo y los resultados devueltos se combinan y se clasificarán por lo que el usuario obtiene resultados unificadas. Los usuarios Obtén resultados de todas las ubicaciones geo independientemente su propia ubicación geográfica. Para obtener información específica, vea [Configurar búsqueda de OneDrive de negocios Multi-Geo](configure-search-for-multi-geo.md) .

Se admiten los siguientes clientes de búsqueda:

-   OneDrive for Business

-   Delve

-   Inicio de SharePoint

-   El centro de búsqueda

-   Aplicaciones de búsqueda personalizadas que utilizan la API de búsqueda de SharePoint

#### <a name="onedrive-ios-and-android"></a>OneDrive iOS y Android 

El OneDrive iOS y Android aplicaciones móviles le mostrará los archivos OneDrive y compartido con usted, independientemente de su ubicación geográfica. Búsqueda de las aplicaciones móviles OneDrive mostrará resultados relevantes de todas las ubicaciones de geo. Descargue la versión más reciente de estas aplicaciones.

Para obtener más información, vea utilizar [OneDrive en iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) y [OneDrive de uso para Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) .

#### <a name="teams-experience"></a>Experiencia de los equipos

Equipos es multi-geo. Independientemente de la ubicación del usuario geo se muestran archivos de OneDrive y vistos recientemente. @ menciona el trabajo con usuarios de todas las ubicaciones de geo.
