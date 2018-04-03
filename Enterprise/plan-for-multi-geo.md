---
title: Plan de OneDrive para el negocio Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
description: Conozca OneDrive para Multi-Geo del negocio, cómo funciona multi-geo y qué ubicaciones de geo están disponibles para el almacenamiento de datos.
ms.openlocfilehash: 22ba0f4ebc3fb3c4e11bc0386a1479fa6a889ad8
ms.sourcegitcommit: 3f3d2de6c0c5225156cfba01bc980994cd9ae848
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/03/2018
---
# <a name="plan-for-onedrive-for-business-multi-geo"></a>Plan de OneDrive para el negocio Multi-Geo

Esta guía está diseñada para administradores de empresas multinacionales (MNCs) que se están preparando su inquilino de SharePoint Online para expandirse a zonas geográficas adicionales con arreglo a la presencia de la empresa para satisfacer los requisitos de residencia de los datos.

En una configuración OneDrive Multi-Geo, el arrendatario Office 365 consiste en una ubicación central (también conocida como la ubicación predeterminada) y una o más ubicaciones de geo de satélite. Se trata de un solo usuario que abarca varias ubicaciones geo. En OneDrive Multi-Geo, su información de inquilinos, incluyendo geo ubicaciones, es usado en Azure Active Directory (DAA). 

Éstos son algunos de los términos clave multi-geo para ayudarle a comprender los conceptos básicos de la configuración:

-   **Inquilinos** : representación de una organización en la nube de Office 365, que normalmente tiene uno o más dominios asociados (por ejemplo, http://contoso.sharepoint.com). 

-   **Geo ubicaciones** , las ubicaciones geográficas donde se hospedan los datos de su arrendatario. Multi-geo arrendatarios abarcan más de una ubicación geográfica, por ejemplo, Norteamérica y Europa.

-   **Ubicaciones de datos permitido (ADL)** : las ubicaciones de geo para el cual el arrendatario se ha configurado para alojar los datos de OneDrive y SharePoint.

-   **Ubicación de datos preferidos (PDL)** : la ubicación geográfica donde se almacenan datos de OneDrive de un usuario individual. Esta propiedad puede establecerse por el administrador a cualquiera de las ubicaciones de datos permitidos que se han configurado para el arrendatario. Tenga en cuenta que si cambia el PDL para un usuario que ya tiene un sitio de OneDrive, sus datos OneDrive no se mueven a la nueva ubicación geográfica automáticamente. Para obtener más información, vea [mover una biblioteca de OneDrive a una ubicación geográfica diferente](move-onedrive-between-geo-locations.md) .

Habilitar Multi-Geo requiere cuatro pasos clave:

1.  Trabaje con su equipo de cuenta para agregar el plan de servicio _Multi-Geo capacidades de Office 365_ .

2.  Elija su deseado geo ubicaciones de satélite y agregarlos a los inquilinos.

3.  Establecer ubicación de datos preferido de los usuarios a la ubicación de geo satélite deseado. Cuando se aprovisiona un sitio nuevo de OneDrive para un usuario, se aprovisiona a su PDL.

4.  Migrar los sitios existentes de OneDrive de los usuarios desde el domicilio a su ubicación de datos preferido según sea necesario.

Para obtener información detallada sobre cada uno de estos pasos, consulte [Configurar OneDrive para negocios Multi-Geo](multi-geo-tenant-configuration.md) .

> [!IMPORTANT]
> Tenga en cuenta que las características de Multi-Geo de Office 365 no están diseñadas para los casos de optimización de rendimiento, están diseñados para satisfacer los requisitos de residencia de los datos. Para obtener información acerca de la optimización de rendimiento para Office 365, consulte [planificación de la red y ajuste del rendimiento para Office 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) o póngase en contacto con su grupo de soporte.

Puede configurar cualquiera de las siguientes ubicaciones para ser satélite geo ubicaciones donde puede alojar archivos de OneDrive. Mientras planea para multi-geo, haga una lista de las ubicaciones que desea agregar a su inquilino de Office 365. Recomendamos a partir de una o dos ubicaciones de satélite y expandiendo gradualmente en más ubicaciones geo, si es necesario.

<table>
<thead>
<tr class="header">
<th align="left"><strong>Ubicación</strong></th>
<th align="left"><strong>Código</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Asia y Pacífico</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Europa / Medio Oriente / África</td>
<td align="left">EUROS</td>
</tr>
<tr class="odd">
<td align="left">Norteamérica</td>
<td align="left">NAM</td>
</tr>
<tr class="even">
<td align="left">Australia</td>
<td align="left">AUSTRALIA</td>
</tr>
<tr class="odd">
<td align="left">Canadá</td>
<td align="left">PUEDE</td>
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
<td align="left">Reino Unido</td>
<td align="left">GBR</td>
</tr>
</tbody>
</table>

Ubicaciones próximas geo:
  
- Francia
- India

Al configurar multi-geo, considere la posibilidad de tomar esta oportunidad para consolidar su infraestructura local mientras la migración a Office 365. Por ejemplo, si tiene conjuntos de servidores locales en Singapur y Malasia, a continuación, puede consolidarlos a la ubicación de satélite APC, siempre que los requisitos de residencia de datos le permiten hacerlo.

## <a name="best-practices"></a>Procedimientos recomendados

Recomendamos que cree un usuario de prueba Office 365 realizar algunas pruebas iniciales. Le mostraremos algunos pasos de pruebas y comprobación con este usuario antes de continuar con los usuarios de producción integrada en la función OneDrive Multi-Geo.

Una vez que haya realizado la comprobación con el usuario de prueba, seleccione un grupo piloto: quizás en su departamento de TI: ser el primero en utilizar OneDrive en una nueva ubicación geográfica. Para este primer grupo, seleccione los usuarios que no tienen aún un OneDrive. Se recomiendan no más de cinco personas en este grupo inicial y expanda gradualmente siguiendo un enfoque de implementación por lotes.

Cada usuario debe tener una *ubicación de datos preferidos* (PDL) para que Office 365 puede determinar en qué ubicación geográfica aprovisionar su OneDrive. Ubicación de datos preferido del usuario debe coincidir con una de las ubicaciones de satélite elegido o su ubicación central. Aunque el campo PDL no es obligatorio, se recomienda que se establezca una PDL para todos los usuarios. Cargas de trabajo de un usuario sin una PDL se suministrará en la ubicación central basada en la lógica de Multi-Geo.   

Crear una lista de los usuarios e incluyen su nombre principal de usuario (UPN) y el código de almacén para la ubicación apropiada de datos preferido. Incluir para empezar con su usuario de prueba y el grupo piloto inicial. Necesitará esta lista para los procedimientos de configuración.

Si los usuarios se sincronizan desde un sistema de Active Directory (AD) local a Azure Active Directory (DAA), debe establecer la ubicación de datos preferido de usuarios sincronizados mediante el uso de directorio activo de Azure Connect. No se puede configurar directamente la ubicación de datos preferido de usuarios sincronizados mediante AD PowerShell de Azure. Se tratan los pasos para configurar PDL en AD y sincronizarla en [sincronización de directorio activo Azure Connect: configurar ubicación de datos preferido de recursos de Office 365](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

La administración de un arrendatario multi-geo puede diferir del inquilino-multi-geo, como muchas de las opciones de SharePoint y OneDrive y servicios son multi-geo. Recomendamos que revise [la administración de un entorno multi-geo](administering-a-multi-geo-environment.md) antes de continuar con la configuración.

Lea la [experiencia de usuario en un entorno de multgeo](multi-geo-user-experience.md) para obtener más información acerca de la experiencia de los usuarios finales en un entorno multi-geo.

Para empezar a configurar OneDrive para negocios Multi-Geo, vea [Configurar OneDrive para negocios Multi-Geo](multi-geo-tenant-configuration.md).

Una vez que haya completado la configuración, no olvide [migrar bibliotecas de OneDrive de los usuarios](move-onedrive-between-geo-locations.md) según sea necesario para permitir que los usuarios que trabajan desde sus ubicaciones de datos preferido.
