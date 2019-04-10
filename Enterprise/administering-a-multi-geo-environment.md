---
title: Administración de un entorno de multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
ms.collection: Strat_SP_gtc
localization_priority: Priority
description: Obtenga información sobre cómo administrar los servicios de SharePoint y OneDrive en un entorno multigeográfico.
ms.openlocfilehash: 7a9865424a18a681dcdbf89b607ab2ae73f44098
ms.sourcegitcommit: 8ba20f1b1839630a199585da0c83aaebd1ceb9fc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/27/2019
ms.locfileid: "30931679"
---
# <a name="administering-a-multi-geo-environment"></a>Administración de un entorno multigeográfico

A continuación, se muestra cómo funcionan los servicios de Office 365 en un entorno multigeográfico.

## <a name="audit-log-search"></a>Búsqueda de registros de auditoría

En la página de búsqueda de registros de auditoría de Office 365 podrá encontrar un [registro de auditoría](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unificado de todas las ubicaciones satélite. Puede ver todas las entradas de registro de auditoría entre ubicaciones geográficas, por ejemplo, las actividades de los usuarios de NAM y EUR se mostrarán en una vista de la organización y, después, puede aplicar filtros existentes para ver las actividades de un usuario específico.

## <a name="bcs-secure-store-apps"></a>BCS, Secure Store, Apps

Los servicios BCS, Secure Store y Apps tienen todos instancias independientes en cada ubicación satélite, por lo que el Administrador de SharePoint Online debe administrarlos y configurarlos independientemente de la ubicación satélite.

## <a name="ediscovery"></a>eDiscovery 

De forma predeterminada, un administrador de eDiscovery o de un espacio empresarial multigeográfico podrá usar eDiscovery solo en la ubicación central de ese espacio empresarial. El administrador global de Office 365 debe asignar permisos de supervisor de eDiscovery para que otros usuarios puedan ejecutar eDiscovery y asignar un parámetro "Región" en el filtro de seguridad de cumplimiento correspondiente para especificar la región donde se ejecutará eDiscovery como ubicación por satélite; en caso contrario, no se ejecutará eDiscovery en la ubicación por satélite. Para configurar el filtro de seguridad de cumplimiento de una región, vea [Configurar eDiscovery de Office 365 Multi-Geo](multi-geo-ediscovery-configuration.md).

## <a name="exchange-mailboxes"></a>Buzones de Exchange

Los buzones de Exchange de los usuarios se mueven automáticamente si cambia su PDL. Cuando se crea un nuevo buzón, se aprovisiona en la PDL del usuario o en ubicación central si no se ha establecido ningún valor para la PDL del usuario.

## <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Directiva de prevención de pérdida de datos (DLP) e Information Protection (IP)

Puede establecer directivas de DLP e IP para OneDrive para la Empresa, SharePoint y Exchange en el Centro de seguridad y cumplimiento, incluyendo directivas necesarias para todo el espacio empresarial o para usuarios correspondientes. Por ejemplo: si quiere seleccionar una directiva para un usuario en una ubicación satélite, seleccione esta opción para aplicar la directiva a un determinado OneDrive y escriba la dirección URL de OneDrive del usuario. Vea [Información general sobre directivas de prevención de pérdida de datos](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) para obtener instrucciones generales para crear directivas de DLP.

Las directivas DLP se sincronizan automáticamente en función de su aplicabilidad a cada ubicación geográfica.

La implementación de directivas de prevención de pérdida de datos e Information Protection a todos los usuarios de una ubicación geográfica no es una opción disponible en la interfaz de usuario. Debe seleccionar las cuentas a las que quiere aplicar la directiva o aplicar la directiva globalmente a todas las cuentas.

## <a name="microsoft-flow"></a>Microsoft Flow

Los flujos creados para la ubicación satélite usarán el punto final que se encuentra en la ubicación geográfica predeterminada del espacio empresarial.  Microsoft Flow no es un servicio multigeográfico. 

## <a name="microsoft-powerapps"></a>Microsoft PowerApps

PowerApps creado para la ubicación satélite usará el punto final en la ubicación central del espacio empresarial. Microsoft PowerApps no es un servicio multigeográfico. 

## <a name="onedrive-administrator-experience"></a>Experiencia del administrador de OneDrive

El [Centro de administración de OneDrive](https://admin.onedrive.com) tiene una pestaña **Geo locations** (Ubicaciones geográficas) en la navegación izquierda que cuenta con un mapa de ubicaciones geográficas en el que puede ver y administrar sus ubicaciones geográficas. Utilice esta página para agregar o eliminar ubicaciones geográficas en el espacio empresarial.

## <a name="security-and-compliance-admin-center"></a>Centro de seguridad y cumplimiento

Existe un centro de cumplimiento centralizado para un espacio empresarial multigeográfico: [Centro de seguridad y cumplimiento de Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).

## <a name="sharepoint-storage-quota"></a>Cuota de almacenamiento de SharePoint

De forma predeterminada, todas las ubicaciones geográficas de un entorno multigeográfico comparten la cuota de almacenamiento del espacio empresarial disponible.  También puede administrar la cuota de almacenamiento asignando una cuota específica para una ubicación geográfica determinada. Para obtener más información, vea las [Cuotas de almacenamiento de SharePoint en entornos multigeográficos](sharepoint-multi-geo-storage-quota.md).

## <a name="sharing"></a>Uso compartido

Los administradores pueden configurar y administrar directivas de uso compartido para cada una de sus ubicaciones. Los sitios de OneDrive y SharePoint en cada ubicación geográfica respetarán solo la configuración geográfica de uso compartido específica correspondiente. (Por ejemplo, puede permitir el [uso compartido externo](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) para su ubicación central, pero no para la ubicación satélite o viceversa). Tenga en cuenta que la configuración de uso compartido no permite configurar limitaciones de uso compartido entre ubicaciones geográficas.

## <a name="taxonomy"></a>Taxonomía

Se admite una [taxonomía](https://docs.microsoft.com/sharepoint/managed-metadata) unificada para metadatos administrados por empresas entre las ubicaciones geográficas, con el principal hospedado en la ubicación central de su compañía. Se recomienda administrar una taxonomía global desde la ubicación central y agregar solo términos específicos de la ubicación a la taxonomía de la ubicación satélite. Los términos de la taxonomía global se sincronizarán con las ubicaciones satélites.

Vea [Administrar metadatos en un espacio empresarial multigeográfico](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-managedmetadata) para obtener detalles adicionales y orientación para desarrolladores.

## <a name="user-profile-application"></a>Aplicación de perfil de usuario

Hay una [aplicación de perfil de usuario](https://docs.microsoft.com/sharepoint/manage-user-profiles) en cada ubicación geográfica. La información de perfil de cada usuario se hospeda en su ubicación geográfica y está disponible para el administrador de esa ubicación geográfica.

Si tiene propiedades de perfil personalizadas, se recomienda usar el mismo esquema de perfil en todas las zonas geográficas y rellenar las propiedades de perfil personalizadas en todas las ubicaciones geográficas o cuando sea necesario. Para obtener instrucciones sobre cómo rellenar los datos de perfil de usuario mediante programación, consulte la [API de actualización de Perfil de usuario masiva](https://docs.microsoft.com/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online).

Vea [Trabajar con perfiles de usuario en un espacio empresarial multigeográfico](https://docs.microsoft.com/sharepoint/dev/solution-guidance/multigeo-userprofileexperience) para obtener detalles adicionales y orientación para desarrolladores.

## <a name="video-portal"></a>Portal de Video

En un espacio empresarial multigeográfico, el portal de Office 365 Video se sirve solo desde la zona geográfica predeterminada y todos los usuarios se redirigirán a esa URL del portal central. Por ello, se usará Remote Media Service (RMS) para esa región como sigue, según su ubicación central.

Stream está disponible actualmente en las regiones siguientes:

- América del Norte, hospedado en los Estados Unidos 
- Europa
- Asia Pacífico

Pero Stream no aún está disponible en las siguientes regiones que actualmente son compatibles con Office 365 Video, por lo tanto, para estas instancias locales, usaremos RMS en la región admitida más cercana.

- Australia
- Canada
- India
- Reino Unido
