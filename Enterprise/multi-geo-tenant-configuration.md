---
title: Configuración de inquilino Multi-Geo de Office 365
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.collection: Strat_SP_gtc
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Obtenga información sobre cómo configurar Office 365 Multi-Geo.
ms.openlocfilehash: 6768aaa552ee75bb5dad523df0efc2384f0241ee
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844611"
---
# <a name="office-365-multi-geo-tenant-configuration"></a>Configuración de inquilino Multi-Geo de Office 365

Antes de configurar su inquilino de Office 365 Multi-Geo, asegúrese de haber leído [Plan para Office 365 Multi-Geo](plan-for-multi-geo.md). Para seguir los pasos de este artículo, necesitará una lista de las ubicaciones geográficas que quiera habilitar como ubicaciones satélite y los usuarios de la prueba que quiera aprovisionar en esas ubicaciones.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Agregar las capacidades multigeográficas del plan de Office 365 al espacio empresarial

Para usar Office 365 Multi-Geo, necesita el plan _Capacidades multigeográficas en Office 365_. Trabaje con el equipo de cuentas para agregar este plan a su espacio empresarial. Su equipo de cuentas le pondrá en contacto con el especialista en licencias adecuado y configurará el espacio empresarial.

Tenga en cuenta que el plan _Multi-Geo Capabilities in Office 365_ (Capacidades multigeográficas de Office 365) es un plan de servicio de nivel de usuario. Necesita una licencia para cada usuario que quiera hospedar en una ubicación por satélite. Puede agregar más licencias a medida que agregue usuarios en las ubicaciones por satélite.

Cuando haya aprovisionado el espacio empresarial con el plan _Capacidades multigeográficas en Office 365_, la pestaña **Ubicaciones geográficas** estará disponible en los centros de administración de OneDrive y SharePoint.

## <a name="add-satellite-locations-to-your-tenant"></a>Agregar ubicaciones satélite a su espacio empresarial

Debe añadir una ubicación satélite para cada ubicación geográfica donde quiere almacenar datos. En la tabla siguiente se muestran las ubicaciones geográficas disponibles:

[!INCLUDE [Office 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Captura de pantalla de la página de ubicaciones geográficas en el Centro de administración de SharePoint](media/sharepoint-multi-geo-admin-center.png)

Para agregar una ubicación de satélite

1. Abra el Centro de administración de SharePoint.

2. Navegue a la pestaña **Geo locations** (Ubicaciones geográficas).

3. Haga clic en **Agregar ubicación**.

4. Seleccione la ubicación que quiere agregar y haga clic en **Siguiente**.

5. Escriba el dominio que quiere usar con la ubicación geográfica y haga clic en **Agregar**.

6. Haga clic en **Cerrar**.

El aprovisionamiento puede tardar desde unas horas hasta 72 horas, dependiendo del tamaño del espacio empresarial. Una vez completado el aprovisionamiento de una ubicación por satélite, recibirá un correo electrónico de confirmación. Cuando la nueva ubicación geográfica aparezca en azul en el mapa de la pestaña **Ubicaciones geográficas** del Centro de administración de OneDrive, podrá proceder a establecer la ubicación de datos preferida de los usuarios a esa ubicación geográfica. 

> [!IMPORTANT]
> La nueva ubicación por satélite se configurará con la configuración predeterminada. Esto le permitirá configurar esa ubicación por satélite según sus necesidades de cumplimiento local.

## <a name="setting-users-preferred-data-location"></a>Establecimiento de la ubicación de datos preferida de los usuarios
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Cuando haya habilitado las ubicaciones de satélite necesarias, puede actualizar su cuenta de usuario para que use la ubicación de datos adecuada. Se recomienda establecer una ubicación de datos preferida para cada uno de los usuarios, aunque el usuario permanezca en la ubicación central.

> [!IMPORTANT]
> Si se establece la ubicación de datos preferida de un usuario a una ubicación que no se ha configurado como una ubicación satélite o la ubicación central, el sistema usará de forma predeterminada la ubicación central para el aprovisionamiento de sitios de SharePoint, de OneDrive y de buzones de grupo.

> [!TIP]
> Se recomienda iniciar las validaciones con un usuario de prueba o un grupo pequeño de usuarios antes de implementar la versión multigeográfica en la organización completa.

En Azure Active Directory hay dos tipos de objetos de usuario: usuarios solo de nube y usuarios sincronizados. Siga las instrucciones adecuadas para el tipo de usuario.

### <a name="synchronize-users-preferred-data-location-using-azure-active-directory-connect"></a>Sincronizar la ubicación de datos preferida del usuario con Azure Active Directory Connect 

Si los usuarios de la compañía se sincronizan en un sistema de Active Directory local con Azure Active Directory, el elemento PreferredDataLocation tiene que rellenarse en AD y sincronizarse con AAD. Siga el proceso de [Sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferida de recursos de Office 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) para configurar la sincronización de la ubicación de datos preferida del entorno local de Active Directory en Azure Active Directory.

Se recomienda incluir el establecimiento de la ubicación de datos preferida del usuario como parte del flujo de trabajo de creación de usuarios estándar.

> [!IMPORTANT]
> Para los nuevos usuarios que no tengan aprovisionado OneDrive, espere como mínimo 24 horas tras sincronizar la ubicación de datos preferida (PDL) de un usuario con Azure Active Directory para que los cambios se propaguen antes de que el usuario inicie sesión en OneDrive para la Empresa. (El establecimiento de la PDL antes de que el usuario inicie sesión para aprovisionar OneDrive para la Empresa garantiza que la nueva instancia de OneDrive del usuario se aprovisionará en la ubicación correcta).

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Establecimiento de la ubicación de datos preferida de usuarios solo de nube 

Si los usuarios de la compañía no se sincronizan en un sistema de Active Directory local con Azure Active Directory, lo que indica que se crearon en Office 365 o Azure Active Directory, la PDL debe establecerse con Azure Active Directory PowerShell.

Los procedimientos de esta sección requieren el [Módulo Microsoft Azure Active Directory para Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si ya tiene instalado Azure Active Directory PowerShell, asegúrese de actualizarlo a la versión más reciente.

1.  Abra el Módulo Microsoft Azure Active Directory para Windows PowerShell.

2.  Ejecute `Connect-MsolService` y escriba las credenciales del administrador global del espacio empresarial.

3.  Use el cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) para establecer la ubicación de datos preferida de cada uno de los usuarios. Por ejemplo:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Puede comprobar que la ubicación de datos preferida se actualizó correctamente mediante el cmdlet Get-MsolUser. Por ejemplo:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![Captura de pantalla de la ventana de PowerShell que muestra set-msoluser](media/multi-geo-tenant-configuration-image3.png)

Se recomienda incluir el establecimiento de la ubicación de datos preferida del usuario como parte del flujo de trabajo de creación de usuarios estándar.

> [!IMPORTANT]
> Para los nuevos usuarios que no tengan aprovisionado OneDrive, espere como mínimo 24 horas tras establecer la PDL de un usuario para que los cambios se propaguen antes de que el usuario inicie sesión en OneDrive. (El establecimiento de la PDL antes de que el usuario inicie sesión para aprovisionar OneDrive para la Empresa garantiza que la nueva instancia de OneDrive del usuario se aprovisionará en la ubicación correcta).

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Aprovisionamiento de OneDrive y efecto de la PDL

Si el usuario ya ha creado un sitio de OneDrive en el espacio empresarial, el establecimiento de su PDL no trasladará automáticamente su instancia de OneDrive existente. Para mover la instancia de OneDrive de un usuario, vea [Transferencia geográfica de OneDrive para la Empresa](move-onedrive-between-geo-locations.md) y siga las instrucciones para mover OneDrive de una ubicación geográfica a otra. (Tenga en cuenta que el buzón de Exchange del usuario se mueve automáticamente al establecer la PDL del usuario)

Si el usuario no tiene un sitio de OneDrive en el espacio empresarial, se le aprovisionará OneDrive de acuerdo con el valor de PDL, suponiendo que la PDL del usuario coincida con una de las ubicaciones satélite de la empresa.

## <a name="configuring-multi-geo-search"></a>Configuración de la búsqueda multigeográfica

El espacio empresarial multigeográfico tendrá funcionalidades de búsqueda agregada, lo que permite devolver resultados desde cualquier lugar en el espacio empresarial.

De forma predeterminada, las búsquedas en estos puntos de entrada devolverán resultados agregados, aunque cada índice de búsqueda se encuentre en la ubicación geográfica correspondiente:

- OneDrive para la Empresa

- Delve

- Página principal de SharePoint

- Centro de búsqueda

Además, pueden configurarse funcionalidades de búsqueda multigeográficas para las aplicaciones de búsqueda personalizada que usan la API de SharePoint Search.

Revise [Configurar la búsqueda en OneDrive para la Empresa multigeográfico](configure-search-for-multi-geo.md) para obtener instrucciones, incluidas las limitaciones y diferencias.

## <a name="validating-the-office-365-multi-geo-configuration"></a>Validar la configuración de Office 365 Multi-Geo

A continuación se muestran algunos casos de uso básicos que tal vez quiera incluir en el plan de validación antes implementar Office 365 Multi-Geo de manera general en la compañía. Después de completar estas pruebas y los casos de uso adicionales que sean relevantes para su compañía, puede continuar y agregar los usuarios al grupo piloto inicial.

**OneDrive para la Empresa**

Seleccione OneDrive desde el iniciador de aplicaciones de Office 365 y confirme que le dirige automáticamente a la ubicación geográfica apropiada del usuario, en función de la PDL del usuario. OneDrive para la Empresa debería ahora comenzar el aprovisionamiento en esa ubicación. Una vez aprovisionado, pruebe a cargar y descargar algunos documentos.

**Aplicación móvil de OneDrive**

Inicie sesión en la aplicación móvil de OneDrive con sus credenciales de cuenta de evaluación. Confirme que puede ver sus archivos de OneDrive para la Empresa y puede interactuar con ellos desde su dispositivo móvil.

**Cliente de sincronización de OneDrive**

Confirme que el cliente de sincronización de OneDrive detecta automáticamente la ubicación geográfica de OneDrive para la Empresa al iniciar sesión. Si quiere descargar el cliente de sincronización, puede hacer clic en **Sincronización** en la biblioteca de OneDrive.

**Aplicaciones de Office**

Para confirmar que tiene acceso a OneDrive para la Empresa, inicie sesión desde una aplicación de Office como Word. Abra la aplicación de Office y seleccione "OneDrive – <TenantName>". Office detectará la ubicación de OneDrive y mostrará los archivos que se pueden abrir.

**Uso compartido**

Pruebe el uso compartido de archivos de OneDrive. Confirme que el selector de personas muestra todos los usuarios de SharePoint Online independientemente de su ubicación geográfica.
