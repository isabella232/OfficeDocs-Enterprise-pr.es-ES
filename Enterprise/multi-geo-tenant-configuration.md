---
title: OneDrive para configuración de inquilinos de negocios Multi-Geo
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
ms.date: 4/3/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: Strat_SP_gtc
localization_priority: Normal
description: Aprenda a configurar OneDrive para negocios Multi-Geo.
ms.openlocfilehash: 56268acd319684ecb713e674b8accbe311d08dce
ms.sourcegitcommit: fa8a42f093abff9759c33c0902878128f30cafe2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="onedrive-for-business-multi-geo-tenant-configuration"></a>OneDrive para configuración de inquilinos de negocios Multi-Geo

Antes de configurar a su arrendatario para OneDrive de negocios Multi-Geo, asegúrese de que ha leído el [Plan de OneDrive de negocios Multi-Geo](plan-for-multi-geo.md). Para seguir los pasos de este artículo, necesitará una lista de las ubicaciones que desea habilitar y los usuarios de prueba que desee aprovisionar para dichas ubicaciones.

## <a name="add-the-multi-geo-capabilities-in-office-365-plan-to-your-tenant"></a>Agregar las capacidades Multi-Geo en el plan de Office 365 a los inquilinos

Para utilizar OneDrive para negocios Multi-Geo, necesita el plan _Multi-Geo capacidades de Office 365_ . Trabaje con su equipo de cuenta para agregar este plan a los inquilinos. Su equipo de cuentas se conectará con el especialista de licencia apropiado y obtener al inquilino configurado.

Tenga en cuenta que el plan de _Capacidades de Multi-Geo en Office 365_ es un servicio de nivel de usuario. Necesita una licencia para cada usuario que desee alojar en una ubicación de satélite. Puede agregar más licencias con el tiempo a medida que agrega los usuarios en ubicaciones de satélite.

Una vez que el arrendatario se haya aprovisionado con el plan de _Capacidades de Multi-Geo en Office 365_ , la ficha **ubicaciones Geo** estará disponible en el [Centro de administración de OneDrive](https://admin.onedrive.com).

## <a name="set-the-allowed-data-locations-adl-to-your-tenant"></a>Establecer las ubicaciones de datos permitido (ADL) a los inquilinos

Debe establecer una ubicación de datos permitidos para SharePoint para cada ubicación geográfica donde desea utilizar OneDrive para el negocio. Geo-ubicaciones disponibles se muestran en la tabla siguiente:

<table>
<thead>
<tr class="header">
<th align="left"><strong>Ubicación</strong></th>
<th align="left"><strong>Código</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Norteamérica</td>
<td align="left">NAM</td>
</tr>
<tr class="even">
<td align="left">Europa / Medio Oriente / África</td>
<td align="left">EUROS</td>
</tr>
<tr class="odd">
<td align="left">Asia y Pacífico</td>
<td align="left">APC</td>
</tr>
<tr class="even">
<td align="left">Australia</td>
<td align="left">AUSTRALIA</td>
</tr>
<tr class="odd">
<td align="left">Japón</td>
<td align="left">JPN</td>
</tr>
<tr class="even">
<td align="left">Canadá</td>
<td align="left">PUEDE</td>
</tr>
<tr class="odd">
<td align="left">Reino Unido</td>
<td align="left">GBR</td>
</tr>
<tr class="even">
<td align="left">Corea</td>
<td align="left">KOR</td>
</tr>
</tbody>
</table>

Para agregar una ubicación de satélite geo

1. Abrir el [Centro de administración de OneDrive](https://admin.onedrive.com).

2. Vaya a la ficha **ubicación geográfica** .

3. Haga clic en **Agregar ubicación**.

4. Seleccione la ubicación que desea agregar y, a continuación, haga clic en **siguiente**.

5. Escriba el dominio que desea utilizar con la ubicación geográfica y, a continuación, haga clic en **Agregar**.

6. Haga clic en **Cerrar**.

Provisioning puede tardar de unas pocas horas a 72 horas, dependiendo del tamaño de los inquilinos. Una vez que haya completado el aprovisionamiento de una ubicación de satélite, recibirá una confirmación por correo electrónico. Cuando la nueva ubicación geográfica aparece en azul en el mapa en la ficha **ubicaciones de Geo** en el centro de administración de OneDrive, puede continuar para establecer la ubicación de datos preferido de los usuarios a esa ubicación geográfica. 

> [!IMPORTANT]
> La nueva ubicación del satélite geo se configurará con la configuración predeterminada. Esto le permitirá configurar esa ubicación geográfica según sus necesidades de cumplimiento de normas locales.

## <a name="setting-users-preferred-data-location"></a>Configuración de ubicación de datos preferido de los usuarios
<span id="_Setting_a_User's" class="anchor"><span id="_Toc508109326" class="anchor"></span></span> 

Después de habilitar las ubicaciones de los datos necesarios, puede actualizar las cuentas de usuario para utilizar la ubicación de datos adecuado. Se recomienda establecer una ubicación de datos preferido para todos los usuarios, incluso si ese usuario se encuentre en la ubicación predeterminada de los datos.

> [!TIP]
> Se recomienda empezar validaciones con un usuario de prueba o un pequeño grupo de usuarios antes de implementar capacidades de Multi-Geo a su organización más amplia.

En DAA hay dos tipos de objetos de usuario: sólo los usuarios y sincronizado de la nube. Siga las instrucciones apropiadas para su tipo de usuario.

### <a name="synchronize-users-preferred-data-location-using-ad-connect"></a>Sincronizar mediante AD conectar la ubicación de datos preferido del usuario 

Si los usuarios de su empresa se sincronizan desde un sistema de Active Directory (AD) local a Azure Active Directory (DAA), debe ser rellenado en AD y sincroniza con DAA su PreferredDataLocation. Siga el proceso de [sync de Azure Connect AD: realizar un cambio en la configuración predeterminada de](https://docs.microsoft.com/en-us/azure/active-directory/connect/active-directory-aadconnectsync-change-the-configuration) preferido de Configurar sincronización de ubicación de los datos de locales AD a DAA.

Recomendamos que incluya la configuración de ubicación de datos preferido del usuario como parte de su flujo de trabajo de creación de usuario estándar.

> [!IMPORTANT]
> Para los nuevos usuarios con ningún OneDrive aprovisionado, espere al menos 24 horas después PDL de un usuario se sincroniza con DAA para que los cambios se propaguen antes de que el usuario inicia sesión en OneDrive para el negocio. (Establecer los datos preferidos ubicación antes de que el usuario inicia una sesión en suministrar su OneDrive para el negocio asegura que se aprovisionará en la ubicación correcta nueva OneDrive del usuario.)

### <a name="setting-preferred-data-location-for-cloud-only-users"></a>Configuración de ubicación de datos preferido para la nube sólo los usuarios 

Si los usuarios de la compañía no se sincronizan desde un sistema de Active Directory (AD) local a Azure Active Directory (DAA), lo que significa que se crean en Office 365 o DAA, entonces PDL debe establecerse mediante PowerShell DAA.

Los procedimientos de esta sección requieren [Microsoft Azure Active Directory para Windows PowerShell módulo](https://www.powershellgallery.com/packages/MSOnline/1.1.166.0). Si ya dispone de PowerShell DAA instalado, asegúrese de que actualice a la versión más reciente.

1.  Abra el módulo de Active Directory de Microsoft Azure para Windows PowerShell.

2.  Ejecutar `Connect-MsolService` y especifique las credenciales de administrador global para el arrendatario.

3.  Utilice el cmdlet [Set-MsolUser](https://docs.microsoft.com/en-us/powershell/msonline/v1/set-msoluser) para establecer la ubicación de datos preferido para cada uno de los usuarios. Por ejemplo:

    `Set-MsolUser -userprincipalName Robyn.Buckley@Contoso.com -PreferredDatalocation EUR`

    Puede comprobar para confirmar que la ubicación de datos preferido se ha actualizado correctamente con el cmdlet Get-MsolUser. Por ejemplo:

    `(Get-MsolUser -userprincipalName Robyn.Buckley@Contoso.com).PreferredDatalocation`

![](media/multi-geo-tenant-configuration_image3.png)

Recomendamos que incluya la configuración de ubicación de datos preferido del usuario como parte de su flujo de trabajo de creación de usuario estándar.

> [!IMPORTANT]
> Para los nuevos usuarios con ningún OneDrive aprovisionado, espere al menos 24 horas después de PDL de un usuario se establece para que los cambios se propaguen antes de que el usuario inicie sesión SharePoint OneDrive. (Establecer los datos preferidos ubicación antes de que el usuario inicia una sesión en suministrar su OneDrive para el negocio asegura que se aprovisionará en la ubicación correcta nueva OneDrive del usuario.)

## <a name="onedrive-provisioning-and-the-effect-of-pdl"></a>Aprovisionamiento de OneDrive y el efecto de PDL

Si el usuario ya tiene un sitio de OneDrive creado en el inquilino, estableciendo su PDL no se moverá automáticamente su OneDrive existente. Para mover OneDrive un usuario, consulte [OneDrive de negocios Geo mover](move-onedrive-between-geo-locations.md) siga las instrucciones en OneDrive mover entre ubicaciones geo.

Si el usuario no tiene un sitio de OneDrive con el inquilino, OneDrive se aprovisionará para ellos de acuerdo con su valor PDL, suponiendo que el PDL del usuario coincide con uno de los almacenes de datos permitidos de la empresa (ADL).

## <a name="configuring-multi-geo-search"></a>Configurar la búsqueda Multi-Geo

El arrendatario Multi-Geo tendrán una capacidad de búsqueda agregado permitiendo una consulta de búsqueda para devolver los resultados desde cualquier lugar con el inquilino.

De forma predeterminada, las búsquedas de estos puntos de entrada devolverá resultados agregados, aunque cada índice de búsqueda se encuentra en su ubicación geográfica correspondiente:

- OneDrive para el negocio

- Delve

- Inicio de SharePoint

- Centro de búsqueda

Además, las capacidades de búsqueda Multi-Geo pueden configurarse para sus aplicaciones de búsqueda personalizada que utilice la API de búsqueda de SharePoint.

Consulte [Configurar búsqueda de OneDrive de negocios Multi-Geo](configure-search-for-multi-geo.md) para instrucciones incluidas las limitaciones y diferencias.

## <a name="validating-the-onedrive-for-business-multi-geo-configuration"></a>Validar la OneDrive para la configuración de negocios Multi-Geo

A continuación se presentan algunos casos de uso básico que desea incluir en el plan de validación antes de ampliamente implementar OneDrive para negocios Multi-Geo a su compañía. Una vez que haya completado estas pruebas y los casos de uso adicionales que son relevantes para su empresa, puede pasar a agregar los usuarios en el grupo piloto inicial.

**OneDrive para el negocio**

Seleccione OneDrive desde el selector de la aplicación de Office 365 y confirme que se dirige automáticamente a la ubicación geográfica correspondiente para el usuario, basándose en PDL del usuario. OneDrive para el negocio debe empezar ahora provisioning en esa ubicación. Pruebe una vez aprovisionado, carga y descarga de algunos documentos.

**Aplicación OneDrive Mobile**

Inicie sesión en su aplicación móvil OneDrive con sus credenciales de la cuenta de prueba. Confirme que puede ver la OneDrive de archivos de empresas y puede interactuar con ellos desde tu dispositivo móvil.

**Cliente de sincronización OneDrive**

Confirme que el cliente de sincronización OneDrive detecta automáticamente su OneDrive para la ubicación geográfica de negocio al iniciar sesión. Si necesita descargar al cliente de sincronización, puede hacer clic en **sincronizar** en la biblioteca OneDrive.

**Aplicaciones de Office**

Confirme que puede tener acceso a OneDrive para el negocio al iniciar sesión desde una aplicación de Office, como Word. Abra la aplicación y seleccione "OneDrive: <TenantName>". Office detectará su ubicación OneDrive y mostrar los archivos que se pueden abrir.

**Sharing**

Intenta compartir archivos de OneDrive. Confirme que el selector de personas muestra todos los usuarios en línea de SharePoint independientemente de su ubicación geográfica.
