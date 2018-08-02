---
title: Planear OneDrive para la Empresa con capacidades multigeográficas
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
description: Obtenga información sobre OneDrive para la Empresa con capacidades multigeográficas, cómo funcionan las Capacidades multigeográficas y qué ubicaciones geográficas están disponibles para el almacenamiento de datos.
ms.openlocfilehash: 26dc9d1b0f0f78e1740088036be4b77bea3ce176
ms.sourcegitcommit: 92d16c0926e4be3fd493fe9b4eb317fb54996bca
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/31/2018
ms.locfileid: "21549991"
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Planear OneDrive para la Empresa con capacidades multigeográficas

Esta guía está diseñada para administradores de compañías multinacionales (MNC) que estén preparando el espacio empresarial de SharePoint Online para expandirlo a otras geografías según la presencia de la compañía para cumplir con los requisitos de residencia de datos.

En una configuración de OneDrive con capacidades multigeográficas, el espacio empresarial de Office 365 está compuesto por una ubicación central (también conocida como ubicación predeterminada) y una o más ubicaciones geográficas satelitales. Es un único espacio empresarial que abarca varias ubicaciones geográficas. En OneDrive con capacidades multigeográficas, la información del espacio empresarial, incluidas las ubicaciones geográficas, se dominan en Azure Active Directory (AAD). 

Aquí encontrará algunos términos clave de Capacidades multigeográficas para ayudarle a comprender los conceptos básicos de la configuración:

-   **Espacio empresarial:** la representación de una organización en la nube de Office 365, que suele tener uno o más dominios asociados (por ejemplo, http://contoso.sharepoint.com)). 

-   **Ubicaciones geográficas:** las ubicaciones geográficas donde se hospedan los datos del espacio empresarial. Los espacios empresariales de Capacidades multigeográficas abarcan más de una ubicación geográfica (por ejemplo, Norteamérica y Europa).

-   **Ubicaciones de datos permitidas (ADL):** las ubicaciones geográficas para las que se configuró el espacio empresarial para hospedar datos de OneDrive y SharePoint.

-   **Ubicación de datos preferida (PDL):** la ubicación geográfica donde se almacenan los datos de OneDrive de un usuario individual. Esta opción puede configurarla el administrador para cualquiera de las ubicaciones de datos permitidas configuradas para el espacio empresarial. Tenga en cuenta que, si cambia la PDL de un usuario que ya tenga un sitio de OneDrive, sus datos de OneDrive no se moverán automáticamente a la nueva ubicación geográfica. Para obtener más información, vea [Mover una biblioteca de OneDrive a otra ubicación geográfica](move-onedrive-between-geo-locations.md).

Para habilitar Capacidades multigeográficas es necesario completar cuatro pasos principales:

1.  Trabaje con el equipo de cuentas para agregar el plan de servicio _Capacidades multigeográficas en Office 365_.

2.  Seleccione las ubicaciones geográficas satelitales deseadas y agréguelas al espacio empresarial.

3.  Establezca la ubicación de datos preferida de los usuarios en la ubicación geográfica satelital que quiera usar. Cuando se aprovisione un sitio de OneDrive para un usuario, se realizará en su PDL.

4.  Migre los sitios de OneDrive existentes de los usuarios desde la ubicación inicial a la ubicación de datos preferida, según sea necesario.

Para obtener más información sobre estos pasos, vea [Configurar OneDrive para la Empresa con capacidades multigeográficas](multi-geo-tenant-configuration.md).

> [!IMPORTANT]
> Tenga en cuenta que las características de Capacidades multigeográficas de Office 365 no se diseñaron para casos de optimización del rendimiento, sino para cumplir con requisitos de residencia de datos. Para obtener información sobre la optimización del rendimiento para Office 365, vea [Planeamiento de la red y optimización del rendimiento para Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848), o bien póngase en contacto con su grupo de soporte técnico.

Puede configurar cualquiera de las ubicaciones siguientes para que sean ubicaciones geográficas satelitales donde podrá hospedar archivos de OneDrive. Al planear la implementación de Capacidades multigeográficas, realice una lista de las ubicaciones que quiera agregar a su espacio empresarial de Office 365. Le recomendamos que empiece con una o dos ubicaciones satelitales y que, después, se expanda de forma progresiva a más ubicaciones geográficas, si es necesario.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Ubicación</strong></th>
<th align="left"><strong>Código</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Asia-Pacífico</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Australia</td>
<td align="left">AUS</td>
</tr>
<tr class="odd">
<td align="left">Canadá</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">Europa, Oriente medio y África</td>
<td align="left">EUR</td>
</tr>
<tr class="odd">
<td align="left">Francia</td>
<td align="left">FRA</td>
</tr>
<tr class="odd">
<td align="left">Japón</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Corea</td>
<td align="left">KOR</td>
</tr>
<tr class="odd">
<td align="left">Norteamérica</td>
<td align="left">NAM</td>
</tr>
<tr class="odd">
<td align="left">Reino Unido</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

Próximas ubicaciones geográficas:
  
- India

Al configurar Capacidades multigeográficas, podrá consolidar su infraestructura local al migrar a Office 365. Por ejemplo, si tiene granjas de servidores locales en Singapur y Malasia, puede consolidarlas en la ubicación satelital de APC, siempre que los requisitos de residencia de datos le permitan hacerlo.

## <a name="best-practices"></a>Procedimientos recomendados

Le recomendamos que cree un usuario de prueba en Office 365 para realizar pruebas iniciales. Le indicaremos algunos pasos de verificación y pruebas con este usuario antes de continuar con la incorporación de los usuarios de producción en la característica de OneDrive con capacidades multigeográficas.

Después de completar las pruebas con el usuario de prueba, seleccione un grupo piloto (por ejemplo, del departamento de TI) para que sea el primero en usar OneDrive en una nueva ubicación geográfica. Para este primer grupo, seleccione usuarios que aún no tengan una cuenta de OneDrive. Le recomendamos que no agregue más de cinco usuarios a este grupo inicial y que se expanda de forma progresiva siguiendo un método de implementación por lotes.

Cada usuario necesita tener una *ubicación de datos preferida* (PDL) para que Office 365 pueda determinar en qué ubicación geográfica necesita aprovisionar la cuenta de OneDrive. La ubicación de datos preferida del usuario tiene que coincidir con una de las ubicaciones satelitales o con la ubicación central. Aunque el campo de PDL no es obligatorio, le recomendamos que establezca una PDL para todos los usuarios. Las cargas de trabajo de un usuario sin una PDL se aprovisionarán en la ubicación central basándose en la lógica de Capacidades multigeográficas.   

Cree una lista de los usuarios e incluya su nombre principal de usuario (UPN) y el código de ubicación para la ubicación de datos preferida. Incluya el usuario de prueba y el grupo piloto inicial para empezar. Necesitará esta lista en los procedimientos de configuración.

Si los usuarios se sincronizan desde un sistema local de Active Directory (AD) a Azure Active Directory (AAD), tendrá que establecer la ubicación de datos preferida para los usuarios sincronizados con Azure Active Directory Connect. No puede configurar directamente la ubicación de datos preferida para los usuarios sincronizados con Azure AD PowerShell. Los pasos para configurar PDL en AD y sincronizarlos se describen en [Sincronización de Azure Active Directory Connect: Configurar la ubicación de datos preferida para los recursos de Office 365](https://docs.microsoft.com/es-ES/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

La administración de un inquilino multigeográfico puede ser distinta de un espacio empresarial que no sea multigeográfico, ya que muchas de las opciones de configuración y servicios de SharePoint y OneDrive detectan las Capacidades multigeográficas. Le recomendamos que vea [Administrar un entorno multigeográfico](administering-a-multi-geo-environment.md) antes de continuar con la configuración.

Para obtener más información sobre la experiencia de los usuarios finales en un entorno multigeográfico, vea [Experiencia del usuario en un entorno multigeográfico](multi-geo-user-experience.md).

Para empezar a configurar OneDrive para la Empresa con capacidades multigeográficas, vea [Configurar OneDrive para la Empresa con capacidades multigeográficas](multi-geo-tenant-configuration.md).

Cuando complete la configuración, recuerde [migrar las bibliotecas de OneDrive de los usuarios](move-onedrive-between-geo-locations.md) según sea necesario para que los usuarios puedan trabajar desde sus ubicaciones de datos preferidas.
