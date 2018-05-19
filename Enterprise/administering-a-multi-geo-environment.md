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
description: Obtenga información cómo administrar los servicios de SharePoint y OneDrive en un entorno multigeográfico.
ms.openlocfilehash: 596db0e2cffedc74a4840ae4427a3350ba1e27d8
ms.sourcegitcommit: a4322cac992ce64b92f0335bf005a7420195d9be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="administering-a-multi-geo-environment"></a>Administración de un entorno de multigeográfico

Vea cómo funcionan los servicios de OneDrive y SharePoint en un entorno de multigeográfico.

#### <a name="onedrive-administrator-experience"></a>Experiencia del administrador de OneDrive

El [Centro de administración de OneDrive](https://admin.onedrive.com) tiene una pestaña **Geo locations** (Ubicaciones geográficas) en la navegación izquierda que cuenta con un mapa de ubicaciones geográficas en el que puede ver y administrar sus ubicaciones geográficas. Utilice esta página para agregar o eliminar ubicaciones geográficas en el espacio empresarial.

#### <a name="taxonomy"></a>Taxonomía

Se admite una [taxonomía](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificada para metadatos administrados empresariales en todas las ubicaciones geográficas, con el patrón hospedado en la ubicación central de la compañía. Se recomienda administrar la taxonomía global desde la ubicación central y agregar solo términos específicos de la ubicación a la taxonomía de la ubicación geográfica por satélite. Los términos de la taxonomía global se sincronizarán con las ubicaciones geográficas por satélite.

#### <a name="sharing"></a>Uso compartido

Los administradores pueden establecer y administrar directivas de uso compartido en cada una de sus ubicaciones. Los sitios de OneDrive de cada ubicación geográfica solo cumplirán la configuración de uso específica de la correspondiente geoárea. (Por ejemplo, puede permitir [uso compartido externo](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) en la ubicación central, pero no en la ubicación por satélite y viceversa). Tenga en cuenta que la configuración de uso compartido no permite configurar limitaciones de uso compartido entre ubicaciones geográficas.

En OneDrive multigeográfico, ha de administrar la configuración de uso compartido en cada ubicación geográfica, ya que no se sincroniza en todo el espacio empresarial. Para administrar el uso compartido, visite la página [OneDrive admin center sharing settings](https://admin.onedrive.com/?v=SharingSettings) (Configuración de uso compartido en el Centro de administración de OneDrive). El uso compartido externo con cualquier persona de cada ubicación por satélite está habilitado de forma predeterminada.

#### <a name="user-profile-application"></a>Aplicación de perfil de usuario

Existe una [aplicación de perfil de usuario](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) en cada ubicación geográfica. La información de perfil de cada usuario se hospeda en su ubicación geográfica y está disponible para el administrador de esa ubicación geográfica.

Si tiene propiedades de perfil personalizadas, se recomienda usar el mismo esquema de perfil en todo el mundo y rellenar las propiedades de perfil personalizadas en todas las ubicaciones geográficas o donde sea necesario. Para obtener instrucciones sobre cómo rellenar los datos de perfil de usuario mediante programación, consulte el artículo sobre la [API de actualización masiva de los perfiles de usuario](https://docs.microsoft.com/es-ES/sharepoint/dev/solution-guidance/bulk-user-profile-update-api-for-sharepoint-online)

#### <a name="bcs-secure-store-apps"></a>BCS, Secure Store, Apps

Los servicios BCS, Secure Store y Apps tienen todos instancias geográficas independientes, por lo que el Administrador de SharePoint Online debe administrarlos y configurarlos en cada instancia geográfica en la que quieren que estén presentes.

#### <a name="security-and-compliance-admin-center"></a>Centro de seguridad y cumplimiento

Existe un centro de cumplimiento centralizado para el inquilino multigeográfico: [Centro de seguridad y cumplimiento de Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Directiva de prevención de pérdida de datos (DLP) e Information Protection (IP)

Puede establecer directivas DLP IP para OneDrive para la Empresa en el centro de seguridad y cumplimiento, además de aplicar ámbito a las directivas según sea necesario para todo el espacio empresarial o a los usuarios que corresponda. Por ejemplo: si desea seleccionar una directiva para un usuario de OneDrive en una ubicación por satélite, seleccione esta opción para aplicar la directiva en un determinado OneDrive y escriba la dirección url de OneDrive del usuario. Vea [Información general sobre las directivas de prevención de pérdida de datos](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) para obtener instrucciones generales para crear directivas DLP.

Las directivas DLP se sincronizan automáticamente en función de su aplicabilidad a cada ubicación geográfica.

La implementación de directivas de prevención de pérdida de datos e Information Protection a todos los usuarios de una ubicación geográfica no es una opción disponible en la interfaz de usuario, en lugar de ello, debe seleccionar las cuentas de OneDrive a las que quiere aplicar la directiva o aplicar la directiva globalmente a todas las cuentas de OneDrive.

#### <a name="ediscovery"></a>eDiscovery 

De forma predeterminada, un administrador o un supervisor de eDiscovery de un inquilino multigeográfico solo podrán ejecutar eDiscovery en la ubicación central de ese espacio empresarial. Para que se pueda ejecutar eDiscovery en ubicaciones por satélite, hay un nuevo parámetro de filtro de seguridad de cumplimiento llamado "Región" disponible mediante PowerShell.

El administrador global de Office 365 debe asignar permisos de supervisor de eDiscovery para que otros usuarios puedan ejecutar eDiscovery y asignar un parámetro "Región" en el filtro de seguridad de cumplimiento correspondiente para especificar la región donde se ejecutará eDiscovery como ubicación por satélite; en caso contrario, no se ejecutará eDiscovery en la ubicación por satélite.

Cuando se establece el rol Administrador o Supervisor de eDiscovery para una ubicación geográfica concreta, el administrador o supervisor de eDiscovery solo podrán realizar acciones de búsqueda de eDiscovery en sitios de SharePoint y OneDrive situados en esa ubicación geográfica. Si un administrador o supervisor de eDiscovery intenta realizar búsquedas en sitios de SharePoint o OneDrive fuera de la región especificada, no se devolverá ningún resultado. Además, cuando el administrador o supervisor de eDiscovery de una región desencadena una exportación, los datos se exportan a la instancia de Azure de esa región. Esto ayuda a las organizaciones a mantener el cumplimiento al no permitir que el contenido se exporte a través de fronteras controladas.

> [!NOTE]
> Si es necesario que un supervisor de eDiscovery realice búsquedas en varias regiones de SharePoint, habrá que crear otra cuenta para el supervisor de eDiscovery que especifique la región alternativa en donde se encuentran los sitios de OneDrive o SharePoint.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Ubicaciones geográficas compatibles con capacidades multigeográficas</strong></th>
<th align="left"><strong>Los datos exportados de eDiscovery para SharePoint estarán en esta ubicación de datos de Azure Blob…</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">Centros de datos de EE. UU.</td>
</tr>
<tr class="even">
<td align="left"><strong>EUR</strong></td>
<td align="left">Centros de datos de Europa</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Centros de datos de Asia oriental o Asia Suroriental</td>
</tr>
<tr class="even">
<td align="left"><strong>CAN</strong></td>
<td align="left">Centros de datos de EE. UU.</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUS</strong></td>
<td align="left">Centros de datos de Asia oriental o Asia Suroriental</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">Ubicación de datos predeterminada del espacio empresarial</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Centros de datos de Europa</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN </strong></td>
<td align="left">Centros de datos de Asia oriental o Asia Suroriental</td>
</tr>
</tbody>
</table>

Para establecer el filtro de seguridad de cumplimiento para una región:

1.  Abra Windows PowerShell

2.  Escriba  
    $s = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -Credential $cred -Authentication Basic -AllowRedirection -SessionOption (New-PSSessionOption -SkipCACheck -SkipCNCheck -SkipRevocationCheck)

    $a = Import-PSSession $s -AllowClobber  

3.  **New-ComplianceSecurityFilter** **-Action** ALL **-FilterName** EnterTheNameYouWantToAssign **-Region** EnterTheRegionParameter **-Users** EnterTheUserPrincipalName

    Por ejemplo: **New-ComplianceSecurityFilter -Action** ALL **-FilterName** NAMEDISCOVERYMANAGERS **-Region** NAM **-Users** adwood@contosodemosx.onmicrosoft.com

Vea el articulo [New-ComplianceSecurityFilter](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) para obtener más parámetros y sintaxis

#### <a name="audit-log-search"></a>Búsqueda de registros de auditoría

Hay un [registro de auditoría](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) unificado de todas las ubicaciones geográficas disponible en la página de búsqueda de registros de auditoría de Office 365. Puede ver todas las entradas de registro de auditoría en todas las geoáreas, por ejemplo, las actividades de los usuarios de las geoáreas NAM y EUR se mostrarán en una vista de la organización y luego puede aplicar los filtros existentes para ver actividades específicas del usuario.
