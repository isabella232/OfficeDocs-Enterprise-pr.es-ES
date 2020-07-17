---
title: Plan para Microsoft 365 Multi-Geo
ms.reviewer: adwood
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
ms.collection:
- Strat_SP_gtc
- SPO_Content
localization_priority: Priority
description: Obtenga información acerca de Microsoft 365 Multi-Geo, cómo funcionan las capacidades multigeográficas y qué ubicaciones geográficas están disponibles para el almacenamiento de datos.
ms.openlocfilehash: 8f06c43b9a622e06959ab12fa0e055c8653ca61c
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052463"
---
# <a name="plan-for-microsoft-365-multi-geo"></a>Plan para Microsoft 365 Multi-Geo

Esta guía está diseñada para administradores de compañías multinacionales (MNC) que estén preparando su cuenta empresarial de Microsoft 365 para expandirla a otras zonas geográficas según la presencia de la compañía para cumplir con los requisitos de residencia de datos.

En una configuración multigeográfica, la cuenta empresarial de Microsoft 365 está compuesta por una ubicación central y una o más ubicaciones por satélite. Se trata de una única cuenta empresarial que abarca varias ubicaciones geográficas. La información de la cuenta empresarial, incluidas las ubicaciones geográficas, se almacenan en Azure Active Directory (Azure AD).

Aquí encontrará algunos términos clave multigeográficos para ayudarle a comprender los conceptos básicos de la configuración:

-   **Cuenta empresarial**: la representación de una organización de Microsoft 365, que suele tener uno o más dominios asociados (por ejemplo, https://contoso.sharepoint.com). 

-   **Ubicaciones geográficas**: las ubicaciones geográficas disponibles para hospedar datos en una cuenta empresarial de Microsoft 365.

-   **Ubicaciones satélite**: las ubicaciones geográficas adicionales que ha configurado para hospedar datos en su cuenta empresarial de Microsoft 365. Las cuentas empresariales multigeográficas abarcan más de una ubicación geográfica, por ejemplo, Norteamérica y Europa.

-   **Ubicación de datos preferida (PDL)**: la ubicación geográfica donde se almacenan los datos de Exchange y OneDrive de un usuario individual. El administrador la puede establecer en cualquiera de las ubicaciones geográficas que se hayan configurado para la cuenta empresarial. Tenga en cuenta que si cambia la PDL de un usuario que ya tiene un sitio de OneDrive, sus datos de OneDrive no se mueven a la nueva ubicación geográfica automáticamente. Vea [Mover un sitio de OneDrive a otra ubicación geográfica](move-onedrive-between-geo-locations.md) para obtener más información. Si tiene un buzón de Exchange, el buzón se mueve automáticamente a la nueva ubicación de datos preferida.

Para habilitar Capacidades multigeográficas es necesario completar cuatro pasos principales:

1.  Trabaje con el equipo de cuentas para agregar el plan de servicio _Funciones multigeográficas en Microsoft 365_.

2.  Seleccione las ubicaciones satélite deseadas y agréguelas al espacio empresarial.

3.  Establezca la ubicación de datos preferida de los usuarios a la ubicación por satélite deseada. Cuando un nuevo sitio de OneDrive o buzón de Exchange está aprovisionado para un usuario, está aprovisionado para su PDL.

4.  Migre los sitios de OneDrive existentes de los usuarios desde la ubicación central a su ubicación de datos preferida según sea necesario. (Los buzones de Exchange se migran automáticamente al establecer la PDL de un usuario).

Para obtener más información sobre estos pasos, vea [Configuración de Microsoft 365 Multi-Geo](multi-geo-tenant-configuration.md).

> [!IMPORTANT]
> Tenga en cuenta que Microsoft 365 Multi-Geo no está diseñado principalmente para optimizar el rendimiento, sino para cumplir con los requisitos de residencia de datos. Para obtener información sobre la optimización del rendimiento de Microsoft 365, vea [Network planning and performance tuning for Microsoft 365](https://support.office.com/article/e5f1228c-da3c-4654-bf16-d163daee8848) (Planeamiento de red y ajuste de rendimiento para Microsoft 365) o póngase en contacto con su grupo de soporte técnico.

Puede configurar cualquiera de las siguientes ubicaciones como ubicaciones por satélite donde puede hospedar sitios de OneDrive y SharePoint y buzones de Exchange. Cuando planee el cambio a Multi-Geo, haga una lista de las ubicaciones que desea agregar a su cuenta empresarial de Microsoft 365. Se recomienda empezar con una o dos ubicaciones por satélite y expandirse gradualmente a más ubicaciones geográficas según sea preciso.

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

Al configurar capacidades multigeográficas, podrá consolidar su infraestructura local al migrar a Microsoft 365. Por ejemplo, si tiene granjas de servidores locales en Singapur y Malasia, puede consolidarlas en la ubicación satélite de APC, siempre que los requisitos de residencia de datos le permitan hacerlo.

## <a name="best-practices"></a>Procedimientos recomendados

Se recomienda crear un usuario de prueba de Microsoft 365 para realizar algunas pruebas iniciales. Le indicaremos algunos pasos de comprobación y pruebas con este usuario antes de incorporar los usuarios de producción en Microsoft 365 Multi-Geo.

Cuando haya terminado de realizar pruebas con el usuario de prueba, seleccione un grupo piloto, por ejemplo, de su departamento de TI, para que sea el primero en utilizar Exchange y OneDrive en una nueva ubicación geográfica. Para este primer grupo, seleccione usuarios que aún no tengan OneDrive. Le recomendamos que este grupo inicial no tenga más de cinco personas y que lo extienda gradualmente siguiendo un enfoque de lanzamiento por lotes.

Cada usuario debe disponer de una *ubicación de datos preferida* (PDL) para que Microsoft 365 pueda determinar en qué ubicación geográfica necesita aprovisionar la cuenta de OneDrive. La ubicación de datos preferida del usuario tiene que coincidir con una de las ubicaciones satélite o con la ubicación central. Aunque el campo de PDL no es obligatorio, le recomendamos que establezca una PDL para todos los usuarios. Las cargas de trabajo de un usuario sin una PDL se aprovisionarán en la ubicación central.

Cree una lista de los usuarios e incluya su nombre principal de usuario (UPN) y el código de ubicación para la ubicación de datos preferida. Incluya el usuario de prueba y el grupo piloto inicial para empezar. Necesitará esta lista en los procedimientos de configuración.

Si los usuarios se sincronizan desde un sistema de Active Directory local con Azure Active Directory, debe establecer la ubicación de datos preferida como un atributo de Active Directory y sincronizarla mediante el uso de Azure Active Directory Connect. No puede configurar directamente la ubicación de datos preferida para los usuarios sincronizados utilizando Azure AD PowerShell. Se tratan los pasos para configurar PDL en Active Directory y sincronizarlas en [Azure Active Directory Connect sync: Configure preferred data location for Microsoft 365 resources](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation) (Sincronización con Azure Active Directory Connect: configuración de ubicación de datos preferida para Recursos de Microsoft 365).

La administración de un inquilino multigeográfico puede ser distinta de un espacio empresarial que no sea multigeográfico, ya que muchas de las opciones de configuración y servicios de SharePoint y OneDrive detectan las Capacidades multigeográficas. Le recomendamos que vea [Administrar un entorno multigeográfico](administering-a-multi-geo-environment.md) antes de continuar con la configuración.

Para obtener más información sobre la experiencia de los usuarios finales en un entorno Multi-Geo, vea [Experiencia del usuario en un entorno multigeográfico](multi-geo-user-experience.md).

Para obtener más información sobre la experiencia de Teams en una cuenta empresarial de Microsoft 365 Multi-Geo, consulte [Experiencia de Teams en una cuenta empresarial multigeográfica de OneDrive y SharePoint Online de Microsoft 365](https://docs.microsoft.com/microsoftteams/teams-experience-o365odb-spo-multi-geo).

Para empezar a configurar Microsoft 365 Multi-Geo, consulte [Configuración de Microsoft 365 Multi-Geo5](multi-geo-tenant-configuration.md).

Cuando complete la configuración, recuerde [migrar las bibliotecas de OneDrive de los usuarios](move-onedrive-between-geo-locations.md) según sea necesario para que los usuarios puedan trabajar desde sus ubicaciones de datos preferidas.
