---
title: Administrar un entorno multi-geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Obtenga información acerca de cómo administrar servicios de SharePoint y OneDrive en un entorno multi-geo.
ms.openlocfilehash: f49cf35503ee6495b5982dc7d72f9b1936f564c6
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="administering-a-multi-geo-environment"></a>Administrar un entorno multi-geo

Aquí es un vistazo a cómo funcionan los servicios de OneDrive y SharePoint en un entorno multi-geo.

#### <a name="onedrive-administrator-experience"></a>Experiencia de administrador de OneDrive

El [Centro de administración de OneDrive](https://admin.onedrive.com) tiene una ficha **ubicaciones Geo** en la izquierda las características que se asignan un geo-ubicaciones donde puede ver y administrar las ubicaciones geo. Utilice esta página para agregar o eliminar ubicaciones de geo para el arrendatario.

#### <a name="taxonomy"></a>Taxonomía

Apoyamos [taxonomía](https://support.office.com/article/A180FA28-6405-4679-9EC3-81D2028C4EFC) unificada para metadatos empresariales administrados entre ubicaciones geo, con el maestro alojado en la ubicación central para su empresa. Se recomienda que administre su taxonomía global desde la ubicación central y sólo agregar términos específicos de la ubicación a la taxonomía de la ubicación geográfica de satélite. Términos de taxonomía global se sincronizarán con las ubicaciones de satélite geo.

#### <a name="sharing"></a>Uso compartido

Los administradores pueden establecer y administrar las directivas de uso compartidas para cada una de sus ubicaciones. Los sitios de OneDrive en cada ubicación geográfica respeta sólo la correspondiente geo para compartir valores específicos. Por ejemplo, puede permitir [Compartir externo](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) para su ubicación central, pero no para el satélite ubicación o viceversa. Para OneDrive Multi-Geo, debe administrar la configuración de uso compartido en cada ubicación geográfica como éstos no se sincronizan entre los inquilinos.

Administrar uso compartido visita la página del [Centro de administración de OneDrive configuración de uso compartido](https://admin.onedrive.com/?v=SharingSettings) . De forma predeterminada compartir externo está habilitado con nadie en cada ubicación de satélite.

#### <a name="user-profile-application"></a>Aplicación de perfil de usuario

Hay una [aplicación de perfil de usuario](https://support.office.com/article/494bec9c-6654-41f0-920f-f7f937ea9723) en cada ubicación geográfica. Información de perfil de cada usuario se aloja en su ubicación geográfica y están disponibles para el Administrador de esa ubicación geográfica.

Si dispone de propiedades de perfil personalizado, recomendamos que utilice el mismo esquema de perfil en todo el mundo y llenar las propiedades de perfil personalizado en todas las ubicaciones de geo o donde sea necesario.

#### <a name="bcs-secure-store-apps"></a>Seguro de BCS, almacén, aplicaciones

BCS, almacenamiento seguro y aplicaciones tienen instancias geo independiente, por lo tanto, el Administrador de SharePoint Online debe administrar y configurar estos servicios de cada instancia de geo dónde desean estar presentes.

#### <a name="security-and-compliance-admin-center"></a>Centro de administración de cumplimiento de normas y de seguridad

Hay un centro de cumplimiento central para el arrendatario Multi-Geo: [Centro de cumplimiento de normas y seguridad de Office 365](https://protection.office.com/?rfr=AdminCenter\#/homepage).

#### <a name="information-protection-ip-data-loss-prevention-dlp-policy"></a>Información protección (IP) Prevention (DLP) Directiva de DLP

Puede establecer su DLP IP directivas para OneDrive para el negocio en el centro de seguridad y cumplimiento de normas, directivas de ámbito según sea necesario a los inquilinos entero o a usuarios aplicables. Por ejemplo: si desea seleccionar una directiva para un usuario OneDrive en una ubicación de satélite, seleccione esta opción para aplicar la directiva a un OneDrive determinado y especifique el usuario la dirección url OneDrive. Ver [Resumen de las políticas de prevención de pérdida de datos](https://support.office.com/article/1966b2a7-d1e2-4d92-ab61-42efbb137f5e) para la dirección general de creación de directivas DLP.

Las directivas DLP se sincronizan automáticamente en función de su aplicabilidad a cada ubicación geográfica.

La implementación de las políticas de prevención de pérdida de datos y protección de la información a todos los usuarios en una ubicación geográfica no es una opción disponible en la interfaz de usuario, en su lugar debe seleccionar las cuentas de OneDrive aplicables de la directiva o la directiva se aplican globalmente a todas las cuentas de OneDrive.

#### <a name="ediscovery"></a>eDiscovery 

De forma predeterminada, un eDiscovery Manager o administrador de un arrendatario multi-geo podrá conducta eDiscovery sólo en la ubicación central de ese arrendatario. Para admitir la posibilidad de realizar eDiscovery para ubicaciones de satélite, un nuevo parámetro de filtro de seguridad de cumplimiento de normas llamado "Región" está disponible a través de PowerShell.

El administrador global de Office 365 debe asignar permisos de administrador de eDiscovery para permitir que otros usuarios realizan eDiscovery y asignar un parámetro de "Región" en su filtro de seguridad de cumplimiento de normas aplicables para especificar la región para llevar a cabo eDiscovery como satélite ubicación, en caso contrario que no eDiscovery se realizará para la ubicación de satélite.

Cuando se establece la función de administrador o administrador de eDiscovery para una ubicación particular geo, el eDiscovery Manager o administrador sólo podrá realizar acciones de búsqueda de eDiscovery en los sitios de SharePoint y sitios OneDrive que se encuentran en esa ubicación geográfica. Si un eDiscovery Manager o administrador intenta buscar en sitios de SharePoint o OneDrive fuera de la región determinada, no se devolverá ningún resultado. Además, cuando el eDiscovery Manager o administrador de una región, desencadena una exportación, los datos se exportan a la instancia de Azure de esa región. Esto ayuda a las organizaciones a cumplir las normas al no permitir que contenido exportarse fuera de las fronteras controladas.

> [!NOTE]
> Si es necesario que un administrador para buscar en varias regiones de SharePoint de eDiscovery, otra cuenta de usuario deberá crearse para el eDiscovery Manager que especifica la región alternativa donde se encuentran los sitios de SharePoint o de OneDrive.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Multi-Geo admite Geo ubicaciones</strong></th>
<th align="left"><strong>eDiscovery para SharePoint se exportan los datos estarán en esta ubicación de datos Blob de Azure...</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><strong>NAM</strong></td>
<td align="left">Centros de datos de EE.</td>
</tr>
<tr class="even">
<td align="left"><strong>EUROS</strong></td>
<td align="left">Centros de datos de Europa</td>
</tr>
<tr class="odd">
<td align="left"><strong>APC</strong></td>
<td align="left">Sudeste o centros de datos de Asia oriental</td>
</tr>
<tr class="even">
<td align="left"><strong>PUEDE</strong></td>
<td align="left">Centros de datos de EE.</td>
</tr>
<tr class="odd">
<td align="left"><strong>AUSTRALIA</strong></td>
<td align="left">Sudeste o centros de datos de Asia oriental</td>
</tr>
<tr class="even">
<td align="left"><strong>KOR</strong></td>
<td align="left">Ubicación de datos predeterminada del inquilino</td>
</tr>
<tr class="odd">
<td align="left"><strong>GBR</strong></td>
<td align="left">Centros de datos de Europa</td>
</tr>
<tr class="even">
<td align="left"><strong>JPN</strong></td>
<td align="left">Sudeste o centros de datos de Asia oriental</td>
</tr>
</tbody>
</table>

Para establecer el filtro de seguridad de cumplimiento para una región:

1.  Abrir Windows PowerShell

2.  Intro  
    $s = New-PSSession - ConfigurationName Microsoft.Exchange - ConnectionUri <https://ps.compliance.protection.outlook.com/powershell-liveid> -credenciales $cred-autenticación básica - AllowRedirection - SessionOption (New-PSSessionOption - SkipCACheck - SkipCNCheck - SkipRevocationCheck)

    $un = $s Import-PSSession - AllowClobber  

3.  **Nueva ComplianceSecurityFilter** **-Acción** Todos los EnterTheNameYouWantToAssign **NombreFiltro -** **-región** EnterTheRegionParameter **-usuarios** EnterTheUserPrincipalName

    Por ejemplo: **nuevo ComplianceSecurityFilter-acción** todos los NAMEDISCOVERYMANAGERS **NombreFiltro -** **-región** NAM **-usuarios** adwood@contosodemosx.onmicrosoft.com

Consulte el artículo [ComplianceSecurityFilter de nuevo](https://technet.microsoft.com/library/mt210915(v=exchg.160).aspx) para la sintaxis y los parámetros adicionales

#### <a name="audit-log-search"></a>Búsqueda de registros de auditoría

Un unificado de [registro de auditoría](https://support.office.com/article/0d4d0f35-390b-4518-800e-0c7ec95e946c) para todas las ubicaciones de geo está disponible desde la página de búsqueda de registro de auditoría de Office 365. Puede ver todas las entradas de registro de auditoría por zonas, por ejemplo, NOMBR & euros geo actividad de los usuarios se mostrará en una vista de la organización y, a continuación, puede aplicar los filtros existentes para ver las actividades del usuario específico.
