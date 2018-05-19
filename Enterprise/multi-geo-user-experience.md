---
title: Experiencia del usuario en un entorno multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información sobre la experiencia del usuario de SharePoint y OneDrive en un entorno multigeográfico.
ms.openlocfilehash: 3c7e4b6802bddc78db016c9c282f5add0c71c491
ms.sourcegitcommit: 75842294e1ba7973728e984f5654a85d5d6172cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2018
---
# <a name="user-experience-in-a-multi-geo-environment"></a>Experiencia del usuario en un entorno multigeográfico

Esto es lo que verán los usuarios en una configuración de OneDrive multigeográfico:

#### <a name="users-onedrive-for-business-location"></a>Ubicación de la instancia de OneDrive para la Empresa del usuario

Los usuarios habrán aprovisionado su instancia de OneDrive para la Empresa en la ubicación de datos que prefieran. Si un usuario navega a una dirección URL de OneDrive que contiene una ubicación geográfica incorrecta (por ejemplo, un marcador de una ubicación geográfica anterior), se les redirige automáticamente a la instancia de OneDrive en la ubicación geográfica correspondiente.

#### <a name="sharing"></a>Uso compartido

La experiencia del selector de personas muestra a todos los usuarios independientemente de su ubicación geográfica. Esto permite a un usuario compartir con otro usuario en la misma geoárea común o en otra de las ubicaciones geográficas del espacio empresarial. El contenido procedente de distintas ubicaciones geográficas se mostrará en la vista **Compartidos conmigo** en la instancia de OneDrive para la Empresa del usuario y se tiene acceso a él con la experiencia de inicio de sesión único independientemente de la ubicación geográfica en que se hospede.

#### <a name="office-applications"></a>Aplicaciones de Office

Las aplicaciones de Office tales como Word, Excel y PowerPoint detectarán automáticamente la ubicación geográfica correcta de OneDrive para la Empresa de cada usuario cuando inicien sesión. Los usuarios no tienen que escribir la dirección URL específica de geoárea de su instancia de OneDrive.

#### <a name="onedrive-for-business-sync-client"></a>Cliente de sincronización de OneDrive para la Empresa

El cliente de sincronización de OneDrive para la Empresa (versión 17.3.6943.0625 y versiones posteriores) detectará automáticamente la ubicación geográfica correcta de OneDrive para la Empresa del usuario.

#### <a name="office-365-app-launcher"></a>Iniciador de aplicaciones de Office 365

El iniciador de aplicaciones es de reconocimiento multigeográfico y dirigirá cada icono a la ubicación geográfica correspondiente de la carga de trabajo. El icono de OneDrive apunta a la ubicación geográfica correcta en la que se hospeda la biblioteca de OneDrive del usuario, mientras que el icono de SharePoint apuntará a todos los usuarios de la ubicación central, ya que los sitios de grupo siguen hospedados allí.

#### <a name="delve-user-profiles"></a>Perfiles de usuarios de Delve

La información de perfiles de usuario se controla en la ubicación geográfica del usuario. Al seleccionar un usuario, se le dirigirá a la ubicación geográfica correcta del usuario, donde verá los detalles completos de su perfil.

Si Delve está desactivada, verá la experiencia de perfil clásica de SharePoint, que no es de reconocimiento multigeográfico.

#### <a name="delve"></a>Delve

En el caso de usuarios de Office 365 que se encuentran en instancias por satélite, se admite Delve multigeográfico, con la limitación de que Delve no se vincula a entradas de blog de SharePoint escritas por usuarios de otras regiones, solo a sus sitios de blog de SharePoint.

#### <a name="search"></a>Búsqueda

Cada ubicación geográfica tiene su propio índice de búsqueda y Centro de búsqueda. Cuando un usuario realiza una búsqueda, la consulta se envía a todas las ubicaciones geográficas y los resultados devueltos se combinan y luego se clasifican para que el usuario obtenga resultados unificados. Los usuarios obtienen resultados de todas las ubicaciones geográficas independientemente de su propia ubicación geográfica. Vea [Configurar la búsqueda en OneDrive para la Empresa multigeográfico](configure-search-for-multi-geo.md) para obtener más información.

Se admiten los siguientes clientes de búsqueda:

-   OneDrive para la Empresa

-   Delve

-   Página principal de SharePoint

-   Centro de búsqueda

-   Aplicaciones de búsqueda personalizada que usan la API de SharePoint Search

#### <a name="onedrive-ios-and-android"></a>OneDrive para iOS y Android 

Las aplicaciones móviles de OneDrive para iOS y Android mostrarán los archivos de OneDrive y los archivos compartidos con usted, independientemente de su ubicación geográfica. La búsqueda en las aplicaciones móviles de OneDrive mostrará resultados relevantes de todas las ubicaciones geográficas. Descargue la última versión de estas aplicaciones.

Vea [Usar OneDrive en iOS](https://support.office.com/article/08d5c5b2-ccc6-40eb-a244-fe3597a3c247) y [usar OneDrive para Android](https://support.office.com/article/eee1d31c-792d-41d4-8132-f9621b39eb36) para obtener más información.

#### <a name="teams-experience"></a>Experiencia de Teams

Teams es de reconocimiento multigeográfico. Independientemente de la ubicación geográfica del usuario se muestran los archivos de OneDrive y los archivos vistos recientemente. Las menciones con @ funcionan con usuarios de todas las ubicaciones multigeográficas.
