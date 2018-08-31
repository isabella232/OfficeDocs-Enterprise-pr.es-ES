---
title: Configuración de espacios empresariales en OneDrive para la Empresa multigeográfico
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Priority
ms.collection: Strat_SP_gtc
description: Aprenda a configurar OneDrive para la Empresa multigeográfico.
ms.openlocfilehash: 1817eee1bb2ceefa0e2e167e327af417dd0c517d
ms.sourcegitcommit: 9bb65bafec4dd6bc17c7c07ed55e5eb6b94584c4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/21/2018
ms.locfileid: "22915255"
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>Configuración de espacios empresariales en OneDrive para la Empresa multigeográfico

Antes de configurar el espacio empresarial de OneDrive para la Empresa multigeográfico, asegúrese de haber leído [Planear OneDrive para la Empresa multigeográfico](plan-for-multi-geo.md). Para seguir los pasos de este artículo, necesitará una lista de las ubicaciones que quiera habilitar y los usuarios de la prueba que quiera aprovisionar en esas ubicaciones.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Agregar las capacidades multigeográficas del plan de Office 365 al espacio empresarial

Para usar OneDrive para la Empresa multigeográfico, necesita el plan _Multi-Geo Capabilities in Office 365_ (Capacidades multigeográficas de Office 365). Trabaje con el equipo de cuenta para agregar este plan a su espacio empresarial. Su equipo de cuenta le pondrá en contacto con el especialista en licencias adecuado y le configurará el espacio empresarial.

Tenga en cuenta que el plan _Multi-Geo Capabilities in Office 365_ (Capacidades multigeográficas de Office 365) es un plan de servicio de nivel de usuario. Necesita una licencia para cada usuario que quiera hospedar en una ubicación por satélite. Puede agregar más licencias a medida que agregue usuarios en las ubicaciones por satélite.

Cuando haya aprovisionado el espacio empresarial con el plan _Capacidades multigeográficas en Office 365_, la pestaña **Geo locations** (Ubicaciones geográficas) estará disponible en el [Centro de administración de OneDrive](https://admin.onedrive.com).

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Establecer las ubicaciones de datos permitidas (ADL) en el espacio empresarial

Debe establecer una ubicación de datos permitida para SharePoint en cada ubicación geográfica donde quiere usar OneDrive para la Empresa. Las ubicaciones geográficas disponibles se muestran en la tabla siguiente:

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
<tr class="even">
<td align="left">Canadá</td>
<td align="left">CAN</td>
</tr>
<tr class="even">
<td align="left">Europa, Oriente medio y África</td>
<td align="left">EUR</td>
</tr>
<tr class="even">
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

Para agregar una ubicación geográfica por satélite

1. Abra el [Centro de administración de OneDrive](https://admin.onedrive.com).

2. Navegue a la pestaña **Geo locations** (Ubicaciones geográficas).

3. Haga clic en **Agregar ubicación**.

4. Seleccione la ubicación que quiere agregar y haga clic en **Siguiente**.

5. Escriba el dominio que quiere usar con la ubicación geográfica y haga clic en **Agregar**.

6. Haga clic en **Cerrar**.

El aprovisionamiento puede tardar desde unas horas hasta 72 horas, dependiendo del tamaño del espacio empresarial. Una vez completado el aprovisionamiento de una ubicación por satélite, recibirá un correo electrónico de confirmación. Cuando la nueva ubicación geográfica aparezca en azul en el mapa de la pestaña **Ubicaciones geográficas** del Centro de administración de OneDrive, podrá proceder a establecer la ubicación de datos preferida de los usuarios a esa ubicación geográfica. 

> [!IMPORTANT]
> La nueva ubicación geográfica por satélite se configurará con la configuración predeterminada. Esto le permitirá configurar esa ubicación geográfica según sus necesidades de cumplimiento local.

## <a name="setting-users-preferred-data-location"></a>Establecimiento de la ubicación de datos preferida de los usuarios
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Cuando haya habilitado las ubicaciones de datos necesarias, puede actualizar su cuenta de usuario para que use la ubicación de datos adecuada. Se recomienda establecer una ubicación de datos preferida para cada uno de los usuarios, aunque el usuario permanezca en la ubicación de datos predeterminada.

> [!TIP]
> Se recomienda iniciar las validaciones con un usuario de prueba o un grupo pequeño de usuarios antes de implementar capacidades multigeográficas en la organización en general.

En AAD hay dos tipos de objetos de usuario: usuarios solo de nube y usuarios sincronizados. Siga las instrucciones adecuadas para el tipo de usuario.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Sincronizar la ubicación de datos preferida del usuario con AD Connect 

Si los usuarios de la compañía se sincronizan en un sistema de Active Directory (AD) local con Azure Active Directory (AAD), su PreferredDataLocation debe rellenarse en AD y sincronizarse con AAD. Siga el proceso de [Azure AD Connect sync: Make a change to the default configuration](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) para configurar la sincronización de la ubicación de datos preferida en AD local con AAD.

Se recomienda incluir el establecimiento de la ubicación de datos preferida del usuario como parte del flujo de trabajo de creación de usuarios estándar.

> [!IMPORTANT]
> Para los nuevos usuarios que no tengan aprovisionado OneDrive, espere como mínimo 24 horas tras sincronizar la ubicación de datos preferida (PDL) de un usuario con AAD para que los cambios se propaguen antes de que el usuario inicie sesión en OneDrive para la Empresa. (El establecimiento de la PDL antes de que el usuario inicie sesión para aprovisionar OneDrive para la Empresa garantiza que la nueva instancia de OneDrive del usuario se aprovisionará en la ubicación correcta).

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Establecimiento de la ubicación de datos preferida de usuarios solo de nube 

Si los usuarios de la compañía no se sincronizan en un sistema de Active Directory (AD) local con Azure Active Directory (AAD), lo que indica que se crearon en Office 365 o AAD, la PDL debe establecerse con AAD PowerShell.

Los procedimientos de esta sección requieren el [Módulo Microsoft Azure Active Directory para Windows PowerShell](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si ya tiene instalado AAD PowerShell, asegúrese de actualizarlo a la versión más reciente.

1.  Abra el Módulo Microsoft Azure Active Directory para Windows PowerShell.

2.  Ejecute `Connect-MsolService` y escriba las credenciales del administrador global del espacio empresarial.

3.  Use el cmdlet [Set-MsolUser](https://docs.microsoft.com/powershell/msonline/v1/set-msoluser) para establecer la ubicación de datos preferida de cada uno de los usuarios. Por ejemplo:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Puede comprobar que la ubicación de datos preferida se actualizó correctamente mediante el cmdlet Get-MsolUser. Por ejemplo:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration-image3.png)

Se recomienda incluir el establecimiento de la ubicación de datos preferida del usuario como parte del flujo de trabajo de creación de usuarios estándar.

> [!IMPORTANT]
> Para los nuevos usuarios que no tengan aprovisionado OneDrive, espere como mínimo 24 horas tras establecer la PDL de un usuario para que los cambios se propaguen antes de que el usuario inicie sesión en SharePoint OneDrive. (El establecimiento de la PDL antes de que el usuario inicie sesión para aprovisionar OneDrive para la Empresa garantiza que la nueva instancia de OneDrive del usuario se aprovisionará en la ubicación correcta).

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Aprovisionamiento de OneDrive y efecto de la PDL

Si el usuario ya ha creado un sitio de OneDrive en el espacio empresarial, el establecimiento de su PDL no trasladará automáticamente su instancia de OneDrive existente. Para mover la instancia de OneDrive de un usuario, vea [OneDrive for Business Geo Move](move-onedrive-between-geo-locations.md) (Transferencia geográfica de OneDrive para la Empresa) y siga las instrucciones para mover OneDrive de una ubicación geográfica a otra.

Si el usuario no tiene un sitio de OneDrive en el espacio empresarial, se le aprovisionará OneDrive de acuerdo con el valor de PDL, suponiendo que la PDL del usuario coincida con una de las ubicaciones de datos permitidas (ADL) de la compañía.

## <a name="configuring-multi-geo-search"></a>Configuración de la búsqueda multigeográfica

El inquilino multigeográfico tendrá funcionalidades de búsqueda agregada, lo que permite devolver resultados desde cualquier lugar en el espacio empresarial.

De forma predeterminada, las búsquedas en estos puntos de entrada devolverán resultados agregados, aunque cada índice de búsqueda se encuentre en la ubicación geográfica correspondiente:

- OneDrive para la Empresa

- Delve

- Página principal de SharePoint

- Centro de búsqueda

Además, pueden configurarse funcionalidades de búsqueda multigeográficas para las aplicaciones de búsqueda personalizada que usan la API de SharePoint Search.

Revise [Configurar la búsqueda en OneDrive para la Empresa multigeográfico](configure-search-for-multi-geo.md) para obtener instrucciones, incluidas las limitaciones y diferencias.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Validación de la configuración de OneDrive para la Empresa multigeográfico

A continuación se muestran algunos casos de uso básicos que tal vez quiera incluir en el plan de validación antes implementar OneDrive para la Empresa multigeográfico de manera general en la compañía. Después de completar estas pruebas y los casos de uso adicionales que sean relevantes para su compañía, puede continuar y agregar los usuarios al grupo piloto inicial.

**OneDrive para la Empresa**

Seleccione OneDrive desde el iniciador de aplicaciones de Office 365 y confirme que le dirige automáticamente a la ubicación geográfica apropiada del usuario, en función de la PDL del usuario. OneDrive para la Empresa debería ahora comenzar el aprovisionamiento en esa ubicación. Una vez aprovisionado, pruebe a cargar y descargar algunos documentos.

**Aplicación móvil de OneDrive**

Inicie sesión en la aplicación móvil de OneDrive con sus credenciales de cuenta de evaluación. Confirme que puede ver sus archivos de OneDrive para la Empresa y puede interactuar con ellos desde su dispositivo móvil.

**Cliente de sincronización de OneDrive**

Confirme que el cliente de sincronización de OneDrive detecta automáticamente la ubicación geográfica de OneDrive para la Empresa al iniciar sesión. Si quiere descargar el cliente de sincronización, puede hacer clic **Sincronización** en la biblioteca de OneDrive.

**Aplicaciones de Office**

Para confirmar que tiene acceso a OneDrive para la Empresa, inicie sesión desde una aplicación de Office como Word. Abra la aplicación de Office y seleccione "OneDrive – <TenantName>". Office detectará la ubicación de OneDrive y mostrará los archivos que se pueden abrir.

**Uso compartido**

Pruebe el uso compartido de archivos de OneDrive. Confirme que el selector de personas muestra todos los usuarios de SharePoint Online independientemente de su ubicación geográfica.
