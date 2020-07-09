---
title: Configuración de inquilino de Microsoft 365 Multi-Geo
ms.reviewer: adwood
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
description: Obtenga información sobre cómo configurar Microsoft 365 Multi-Geo.
ms.openlocfilehash: 928033dcbec0ad0b52f24bd0bec4dd6b9f9331bc
ms.sourcegitcommit: c6a2256f746f55d1cfb739649ffeee1f2f2152aa
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/07/2020
ms.locfileid: "45052573"
---
# <a name="microsoft-365-multi-geo-tenant-configuration"></a>Configuración de inquilino de Microsoft 365 Multi-Geo

Antes de configurar su inquilino de Microsoft 365 Multi-Geo, asegúrese de haber leído [Plan para Microsoft 365 Multi-Geo](plan-for-multi-geo.md). Para seguir los pasos de este artículo, necesitará una lista de las ubicaciones geográficas que quiera habilitar como ubicaciones satélite y los usuarios de la prueba que quiera aprovisionar en esas ubicaciones.

## <a name="add-the-multi-geo-capabilities-in-your-microsoft-365-plan-to-your-tenant"></a>Agregar las capacidades multigeográficas del plan de Microsoft 365 al espacio empresarial

Para usar Microsoft 365 Multi-Geo, necesita el plan _Capacidades multigeográficas en Microsoft 365_. Trabaje con el equipo de cuentas para agregar este plan a su espacio empresarial. Su equipo de cuentas le pondrá en contacto con el especialista en licencias adecuado y configurará el espacio empresarial.

Note that the _Multi-Geo Capabilities in Microsoft 365_ plan are a user-level service plan. You need a license for each user that you want to host in a satellite location. You can add more licenses over time as you add users in satellite locations.

Cuando haya aprovisionado el espacio empresarial con el plan _Capacidades multigeográficas en Microsoft 365_, la pestaña **Ubicaciones geográficas** estará disponible en los centros de administración de OneDrive y SharePoint.

## <a name="add-satellite-locations-to-your-tenant"></a>Agregar ubicaciones satélite a su espacio empresarial

Debe añadir una ubicación satélite para cada ubicación geográfica donde quiere almacenar datos. En la tabla siguiente se muestran las ubicaciones geográficas disponibles:

[!INCLUDE [Microsoft 365 Multi-Geo locations](includes/office-365-multi-geo-locations.md)]

![Captura de pantalla de la página de ubicaciones geográficas en el Centro de administración de SharePoint](media/sharepoint-multi-geo-admin-center.png)

Para agregar una ubicación de satélite

1. Abra el Centro de administración de SharePoint.

2. Navegue a la pestaña **Geo locations** (Ubicaciones geográficas).

3. Haga clic en **Agregar ubicación**.

4. Seleccione la ubicación que quiere agregar y haga clic en **Siguiente**.

5. Escriba el dominio que quiere usar con la ubicación geográfica y haga clic en **Agregar**.

6. Haga clic en **Cerrar**.

Provisioning may take from a few hours up to 72 hours, depending on the size of your tenant. Once provisioning of a satellite location has completed, you will receive an email confirmation. When the new geo location appears in blue on the map on the **Geo locations** tab in the OneDrive admin center, you can proceed to set users' preferred data location to that geo location. 

> [!IMPORTANT]
> Your new satellite location will be set up with default settings. This will allow you to configure that satellite location as appropriate for your local compliance needs.

## <a name="setting-users-preferred-data-location"></a>Establecimiento de la ubicación de datos preferida de los usuarios
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Once you enable the needed satellite locations, you can update your user accounts to use the appropriate preferred data location. We recommend that you set a preferred data location for every user, even if that user is staying in the central location.

> [!IMPORTANT]
> Si se establece la ubicación de datos preferida de un usuario a una ubicación que no se ha configurado como una ubicación satélite o la ubicación central, el sistema usará de forma predeterminada la ubicación central para el aprovisionamiento de sitios de SharePoint, de OneDrive y de buzones de grupo.

> [!TIP]
> Se recomienda iniciar las validaciones con un usuario de prueba o un grupo pequeño de usuarios antes de implementar la versión multigeográfica en la organización completa.

En Azure Active Directory (Azure AD) hay dos tipos de objetos de usuario: usuarios solo de nube y usuarios sincronizados. Siga las instrucciones adecuadas para el tipo de usuario.

### <a name="synchronize-users-preferred-data-location-using-azure-ad-connect"></a>Sincronizar la ubicación de datos preferida del usuario con Azure AD Connect 

Si los usuarios de su compañía se sincronizan con Azure AD desde un sistema local de Active Directory, sus PreferredDataLocation deben rellenarse en AD y sincronizarse en Azure AD.

Siga el proceso en [Sincronización de Azure Active Directory Connect: Configuración de la ubicación de datos preferida para los recursos de Office 365](/azure/active-directory/hybrid/how-to-connect-sync-feature-preferreddatalocation) para configurar la sincronización de la ubicación de datos preferida desde los servicios de dominio de Active Directory (AD DS) locales a Azure AD.

Se recomienda incluir el establecimiento de la ubicación de datos preferida del usuario como parte del flujo de trabajo de creación de usuarios estándar.

> [!IMPORTANT]
> Para los nuevos usuarios que no tengan aprovisionado OneDrive, espere como mínimo 24 horas tras sincronizar la PDL de un usuario con Azure AD para que los cambios se propaguen antes de que el usuario inicie sesión en OneDrive para la Empresa. (El establecimiento de la PDL antes de que el usuario inicie sesión para aprovisionar OneDrive para la Empresa garantiza que la nueva instancia de OneDrive del usuario se aprovisionará en la ubicación correcta).

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Establecimiento de la ubicación de datos preferida de usuarios solo de nube 

Si los usuarios de la compañía no se sincronizan con Azure AD en un sistema de Active Directory local, lo que indica que se crearon en Microsoft 365 o Azure AD, la PDL debe establecerse con el módulo de Microsoft Azure Active Directory para Windows PowerShell.

Los procedimientos de esta sección requieren el [Módulo de Microsoft Azure Active Directory para Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si ya tiene instalado este módulo, asegúrese de actualizarlo a la versión más reciente.

1.  [Conéctese e inicie sesión](/powershell/connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con las credenciales de administrador global para su espacio empresarial.

2.  Use the [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) cmdlet to set the preferred data location for each of your users. For example:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    You can check to confirm that the preferred data location was updated properly by using the Get-MsolUser cmdlet. For example:

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

## <a name="validating-the-microsoft-365-multi-geo-configuration"></a>Validar la configuración de Microsoft 365 Multi-Geo

A continuación se muestran algunos casos de uso básicos que tal vez quiera incluir en el plan de validación antes implementar Microsoft 365 Multi-Geo de manera general en la compañía. Después de completar estas pruebas y los casos de uso adicionales que sean relevantes para su compañía, puede continuar y agregar los usuarios al grupo piloto inicial.

**OneDrive para la Empresa**

Seleccione OneDrive desde el iniciador de aplicaciones de Microsoft 365 y confirme que le dirige automáticamente a la ubicación geográfica apropiada del usuario, en función de la PDL del usuario. OneDrive para la Empresa debería ahora comenzar el aprovisionamiento en esa ubicación. Una vez aprovisionado, pruebe a cargar y descargar algunos documentos.

**Aplicación móvil de OneDrive**

Inicie sesión en la aplicación móvil de OneDrive con sus credenciales de cuenta de evaluación. Confirme que puede ver sus archivos de OneDrive para la Empresa y puede interactuar con ellos desde su dispositivo móvil.

**Cliente de sincronización de OneDrive**

Confirm that the OneDrive sync client automatically detects your OneDrive for Business geo location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.

**Aplicaciones de Office**

Confirm that you can access OneDrive for Business by logging in from an Office application, such as Word. Open the Office application and select "OneDrive – <TenantName>". Office will detect your OneDrive location and show you the files that you can open.

**Uso compartido**

Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint online users regardless of their geo location.
