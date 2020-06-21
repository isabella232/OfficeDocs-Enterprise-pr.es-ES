---
title: Introducción a las características de exhibición de documentos electrónicos y búsqueda 365 de Microsoft
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
f1.keywords:
- NOCSH
description: Información general sobre la característica de exhibición de documentos electrónicos y otras características de búsqueda de Microsoft 365 para auditar el uso y la transparencia.
ms.openlocfilehash: d628bc9aa3964ffed671035a1f78f61d9632b87e
ms.sourcegitcommit: 4c519f054216c05c42acba5ac460fb9a821d6436
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/17/2020
ms.locfileid: "44774945"
---
# <a name="microsoft-365-ediscovery-and-search-features-overview"></a>Introducción a las características de exhibición de documentos electrónicos y búsqueda 365 de Microsoft 

## <a name="ediscovery"></a>eDiscovery

La característica eDiscovery proporciona un único espacio para que los administradores, los responsables de cumplimiento normativo y otros usuarios autorizados realicen una investigación exhaustiva sobre la actividad de los usuarios de Microsoft 365. Los responsables de seguridad con los permisos adecuados llevan a cabo búsquedas y realizan retenciones en el contenido. Los resultados de la búsqueda son los mismos que se obtienen de una búsqueda de contenido, excepto que los casos de eDiscovery se crean para las suspensiones aplicadas. Los resultados de las búsquedas de eDiscovery están cifrados para la seguridad y puede analizar los datos exportados con la [exhibición avanzada](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20)de documentos electrónicos.

## <a name="content-search"></a>Búsqueda de contenido

La [búsqueda de contenido](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a) es una herramienta de búsqueda de exhibición de documentos electrónicos que proporciona capacidades mejoradas de escalabilidad y rendimiento en las herramientas de búsqueda anteriores de eDiscovery. Use la búsqueda de contenido para buscar en buzones, carpetas públicas, sitios de SharePoint Online y ubicaciones de OneDrive para la empresa. La búsqueda de contenido admite búsquedas grandes. No hay ningún límite con respecto al número de buzones y sitios en los que se puede buscar. Tampoco hay límites en el número de búsquedas que se ejecutan al mismo tiempo. Después de ejecutar una búsqueda, el número de orígenes de contenido y el número estimado de resultados de la búsqueda se muestran en el panel de detalles de la página de búsqueda. Puede obtener una vista previa de los resultados o exportarlos a un equipo local. Si su organización tiene una suscripción a Microsoft 365 E5, puede [preparar los resultados](https://support.office.com/article/Run-a-Content-Search-in-the-Office-365-Security-Compliance-Center-61852fd9-fe8a-4880-a339-cb19ed3bff4a#prepare) para el análisis con las eficaces características de análisis de [Microsoft 365 Advanced eDiscovery](https://docs.microsoft.com/microsoft-365/compliance/overview-ediscovery-20).

## <a name="audit-log-search"></a>Búsqueda de registros de auditoría

Además de realizar un seguimiento de los cambios en la organización de Microsoft 365, puede ver los informes de auditoría y exportar los registros de auditoría. Una vez que la auditoría está habilitada para un espacio empresarial de Microsoft 365, las actividades administrativas y de usuario se registran en los registros de eventos y pueden realizar búsquedas. Por ejemplo, puede usar el registro de auditoría de buzones de correo para realizar un seguimiento de las acciones realizadas en un buzón por otros usuarios que no sean el propietario del buzón. Los responsables de cumplimiento normativo pueden usar las capacidades de búsqueda y filtro para actividades de usuario específicas. Por ejemplo, para identificar a los usuarios que han visto o descargado un documento específico, si los administradores han realizado actividades de administración de usuarios o para ver los cambios en la configuración de inquilinos en los últimos 90 días. Los resultados de la búsqueda contienen información forense valiosa sobre actividades específicas realizadas por un usuario o un administrador. Consulte [Buscar en el registro de auditoría](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance) para obtener una descripción de las actividades administrativas y de usuario registradas en Microsoft 365.

Los eventos de SharePoint Online y OneDrive para la empresa se muestran en el registro en un plazo de 30 minutos de repeticiones. Los eventos de Exchange Online aparecen en los registros de auditoría en un plazo de 24 horas de repeticiones. Los eventos de inicio de sesión de Azure AD están disponibles en minutos de su ocurrencia y otros eventos de directorio de Azure AD están disponibles en un plazo de 24 horas de repeticiones. Puede exportar los purgadores en los resultados de búsqueda de registros de auditoría para un análisis más detallada. Se exporta un máximo de 50.000 entradas de una sola búsqueda de registro de auditoría. Para exportar más entradas que este límite, reduzca el intervalo de fechas o ejecute varias búsquedas en el registro de auditoría.

En la tabla siguiente se detalla parte de la información que se muestra en los informes de actividad. Vea las [propiedades detalladas en el registro de auditoría](https://docs.microsoft.com/microsoft-365/compliance/detailed-properties-in-the-office-365-audit-log) para obtener más información acerca de las propiedades recopiladas por cada carga de trabajo de Microsoft 365.

| Propiedad | Descripción |
|----------------|----------------------------------------------------------------------------------------------------------------------|
| Fecha | Fecha y hora del evento |
| User | Usuario que realizó la acción |
| ClientIP | Dirección IPv4 o IPv6 del dispositivo que se usó cuando se registró la actividad. |
| CreationTime | Fecha y hora en la hora universal coordinada (UTC) cuando el usuario llevó a cabo la actividad. |
| EventSource | Identifica que se ha producido un evento. Los valores posibles son SharePoint y ObjectModel. |
| ID | IDENTIFICADOR de la entrada de informe. El identificador identifica de forma única la entrada del informe. |
| Operación | Nombre del usuario o actividad, que corresponde al valor seleccionado en la actividad mostrar resultados para este usuario. |
| OrganizationId | GUID para el servicio Microsoft 365 de la organización en el que se ha producido el evento. |
| UserAgent | Información sobre el explorador del usuario, proporcionada por el explorador. |
| UserId | Usuario que realizó la acción (especificado en la propiedad Operation) que resultó en el registro que se está registrando. |
| UserType | Tipo de usuario que realizó la operación. Los siguientes valores indican el tipo de usuario. |
|  | 0 indica un usuario normal. |
|  | 2 indica un administrador de la organización de Microsoft 365. |
|  | 3 indica un administrador de centro de recursos de Microsoft o una cuenta de sistema de centro de recursos. |
| Carga de trabajo | Servicio de Microsoft 365 donde se produjo la actividad. Los valores posibles para esta propiedad son: |
|  | Exchange Online |
|  | SharePoint Online |
|  | OneDrive para la Empresa |
|  | Informes de Azure Active Directory |

Para obtener los pasos detallados para buscar registros de auditoría de Microsoft 365, vea [Buscar el registro de auditoría en el centro de seguridad & cumplimiento](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance).

## <a name="search-unified-audit-log"></a>Buscar registro de auditoría unificado

Use la característica de búsqueda de registros de auditoría para buscar en el registro de auditoría unificado. Microsoft 365 también ofrece la posibilidad de realizar búsquedas en este registro mediante PowerShell remoto. El [cmdlet Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/Search-UnifiedAuditLog?view=exchange-ps) en Exchange Online PowerShell se usa para buscar en el registro de auditoría unificado de eventos relacionados con las operaciones de usuario de Exchange Online, SharePoint Online, OneDrive para la empresa y Azure ad. 

Puede buscar todos los eventos de un intervalo de fechas especificado o puede filtrar los resultados en función de criterios específicos, como una acción específica, el usuario que realizó la acción o el objeto de destino. Los administradores pueden usar hasta tres simultáneamente sesiones de PowerShell de Exchange Online para dividir grandes búsquedas de intervalo de fechas.