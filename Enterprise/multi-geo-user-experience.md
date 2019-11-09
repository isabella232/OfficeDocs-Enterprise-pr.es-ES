---
title: Experiencia del usuario en un entorno multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
ms.custom: ''
localization_priority: Priority
description: Obtenga información sobre la experiencia del usuario de SharePoint, OneDrive y Exchange en un entorno multigeográfico.
ms.openlocfilehash: ca6c27b29eae84a245c6fe22fd6ba928b79a975d
ms.sourcegitcommit: 5fe1c9be652222d6956c7dad5949ddcf0bd27041
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/08/2019
ms.locfileid: "38076244"
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Experiencia del usuario en un entorno multigeográfico

Esto es lo que verán los usuarios en una configuración de OneDrive multigeográfico:

## <a name="exchange-mailbox"></a>Buzón de Exchange

El buzón de Exchange de un usuario se aprovisiona en su ubicación de datos preferida y si esta cambia el buzón se reubica automáticamente. Los usuarios pueden usar Outlook y Outlook en la Web normalmente sin cambios en la experiencia del usuario en un entorno de multigeográfico.

## <a name="hub-sites"></a>Sitios centrales

Los sitios centrales de SharePoint mejoran la detección y la participación con contenido para los empleados, al crear una representación completa y coherente de proyectos, departamentos o regiones. En un entorno multigeográfico, los sitios de ubicaciones satélite pueden asociarse fácilmente con un sitio central independientemente de su ubicación geográfica. Los usuarios pueden buscar y obtener resultados en la central mediante una experiencia de búsqueda única, independientemente de la ubicación geográfica de los sitios.

## <a name="office-365-app-launcher"></a>Iniciador de aplicaciones de Office 365

El iniciador de aplicaciones es compatible con múltiples ubicaciones geográficas y dirigirá cada icono a la ubicación geográfica correspondiente de la carga de trabajo. Los iconos de SharePoint y OneDrive apuntarán al usuario a la ubicación correspondiente a la ubicación geográfica aprovisionada del usuario. Esto significa que si el usuario tiene un OneDrive en la ubicación central, el icono de SharePoint apuntarán a la página principal de SharePoint en la ubicación central, pero se aprovisionará su sitio de grupo en la ubicación correspondiente a su ubicación de datos preferida. 

## <a name="office-applications"></a>Aplicaciones de Office

Las aplicaciones de Office tales como Word, Excel y PowerPoint detectarán automáticamente la ubicación geográfica correcta de OneDrive para la Empresa de cada usuario cuando inicien sesión. Los usuarios no tienen que escribir la dirección URL específica de geoárea de su instancia de OneDrive.

## <a name="onedrive-for-business-sync-client"></a>Cliente de sincronización de OneDrive para la Empresa

El cliente de sincronización de OneDrive para la Empresa (versión 17.3.6943.0625 y versiones posteriores) detectará automáticamente la ubicación geográfica correcta de OneDrive para la Empresa del usuario. La compatibilidad con clientes de sincronización incluye la posibilidad de sincronizar sitios basados en grupos independientemente de su ubicación geográfica. Tenga en cuenta que el cliente de sincronización de Groove no es compatible con las capacidades multigeográficas. 

## <a name="onedrive-for-business-location"></a>Ubicación de la instancia de OneDrive para la Empresa

Los usuarios habrán aprovisionado su instancia de OneDrive para la Empresa en la ubicación de datos que prefieran. Si un usuario navega a una dirección URL de OneDrive que contiene una ubicación geográfica incorrecta (por ejemplo, un marcador de una ubicación geográfica anterior), se les redirige automáticamente a la instancia de OneDrive en la ubicación geográfica correspondiente.

## <a name="onedrive-ios-and-android"></a>OneDrive para iOS y Android 

Las aplicaciones móviles de OneDrive para iOS y Android mostrarán los archivos de OneDrive y los archivos compartidos con usted, independientemente de su ubicación geográfica. La búsqueda en las aplicaciones móviles de OneDrive mostrará resultados relevantes de todas las ubicaciones geográficas. Descargue la última versión de estas aplicaciones.

Vea [Usar OneDrive en iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) y [usar OneDrive para Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) para obtener más información.

## <a name="onedrive-mobile-client"></a>Cliente móvil de OneDrive 

El cliente móvil de OneDrive es compatible con las capacidades multigeográficas y mostrará el contenido y los resultados relevantes de todas las ubicaciones geográfica.

## <a name="search"></a>Búsqueda

Cada ubicación geográfica tiene su propio índice de búsqueda y Centro de búsqueda. Cuando un usuario realiza una búsqueda, la consulta se envía a todas las ubicaciones geográficas y los resultados devueltos se combinan y luego se clasifican para que el usuario obtenga resultados unificados. Los usuarios obtienen resultados de todas las ubicaciones geográficas independientemente de su propia ubicación geográfica. Vea [Configurar la búsqueda en OneDrive para la Empresa multigeográfico](configure-search-for-multi-geo.md) para obtener más información.

Se admiten los siguientes clientes de búsqueda:

-   OneDrive para la Empresa

-   Delve

-   Página principal de SharePoint

-   Centro de búsqueda

-   Aplicaciones de búsqueda personalizada que usan la API de SharePoint Search

## <a name="sharepoint-home"></a>Página principal de SharePoint 

En SharePoint Multi-Geo su página principal de SharePoint se hospeda en la ubicación donde se encuentra el usuario según su ubicación de OneDrive para la Empresa. Por ejemplo: si el usuario tiene hospedado OneDrive en una ubicación satélite de Europa, la página principal de SharePoint se representará desde Europa. La página principal de SharePoint incluye todo el contenido relevante para el usuario independientemente de su ubicación geográfica. 

**Sitios seguidos, noticias de sitios, sitios recientes, sitios frecuentes y sitios sugeridos**

Todos estos componentes se mostrarán con independencia de la ubicación geográfica donde se hospeda el contenido, siempre y cuando el usuario tenga permisos para dicho contenido. 

**Vínculos destacados**

Los administradores pueden configurar vínculos destacados en la página principal de SharePoint según sea adecuado para cada ubicación geográfica. Esto permite que el administrador destaque en la página principal de SharePoint de cada región los vínculos que sean apropiados para los usuarios de la región. 

## <a name="sharepoint-mobile-client"></a>Cliente móvil de SharePoint 

El cliente móvil de SharePoint es compatible con las capacidades multigeográficas y mostrará el contenido y los resultados relevantes de todas las ubicaciones geográfica.

## <a name="sharing"></a>Uso compartido

La experiencia de selector de personas muestra todos los usuarios, independientemente de su ubicación geográfica. Esto permite que un usuario pueda compartir con otro de su misma ubicación geográfica o en cualquier otra ubicación geográfica de su inquilino. El contenido de diferentes ubicaciones geográficas se mostrará en la vista **Compartido conmigo** OneDrive para la Empresa del usuario y puede accederse a el con la experiencia inicio de sesión único independientemente de la ubicación geográfica en la que se hospeda.

## <a name="teams-experience"></a>Experiencia de Teams

Teams es compatible con las capacidades multigeográficas. Los archivos de OneDrive y los archivos vistos recientemente se muestran independientemente de la ubicación geográfica del usuario. Las @menciones funcionan con los usuarios de todas las ubicaciones geográficas.

## <a name="user-profiles"></a>Perfiles de usuario

La información de perfiles de usuario se controla en la ubicación geográfica del usuario. Al seleccionar un usuario, se le dirigirá a la ubicación geográfica correcta del usuario, donde verá los detalles completos de su perfil.

Si Delve está desactivada, verá la experiencia de perfil clásica de SharePoint, que no es de reconocimiento multigeográfico.


