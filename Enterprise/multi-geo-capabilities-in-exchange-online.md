---
title: Capacidades de Multi-Geo en Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.date: 4/11/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Expandir su presencia en Office 365 para varias regiones geográficas con capacidades de multi-geo en Exchange Online.
ms.openlocfilehash: 6378f8a010b790674f07150aa39cbbc38c60b7fe
ms.sourcegitcommit: 63e2844daa2863dddcd84819966a708c434e8580
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Capacidades de Multi-Geo en Exchange Online

Capacidades de Multi-Geo en Office 365 permiten un único arrendatario abarcar varias ubicaciones geográficas (Geos). Cuando Multi-Geo está habilitada, los clientes pueden seleccionar la ubicación del contenido del buzón de Exchange en línea (datos en reposo) en cada usuario.

La ubicación inicial del inquilino (denominada el "default" o "central" ubicación) se determina basándose en su dirección de facturación. Cuando Multi-Geo está habilitada, se pueden colocar buzones en ubicaciones adicionales "satélite" por:

- Crear un nuevo buzón de Exchange Online directamente en un satélite.

- Mover un buzón de Exchange en línea existente a un satélite.

- Incorporación de un buzón de correo desde una organización de Exchange local directamente en un satélite.

Las zonas siguientes están disponibles para su uso en una configuración Multi-Geo:

- Asia Pacífico

- Australia

- Canadá

- Unión Europea

- India (actualmente sólo está disponible para clientes con direcciones de facturación en la India)

- Japón

- Corea

- Reino Unido

- Estados Unidos

## <a name="prerequisite-configuration"></a>Configuración de requisitos previos
Antes de empezar a utilizar capacidades de Multi-Geo en Exchange Online, Microsoft tiene que configurar a su arrendatario Exchange Online para soporte de Multi-Geo. Este proceso de configuración inicial se desencadena al solicitar licencias del Multi-Geo y normalmente debe tener menos de 30 días para completar.

Recibirá notificaciones en el [Centro de mensajes de Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) cuando se ha iniciado y finalizado la configuración. Configuración se activa automáticamente al adquirir licencias del Multi-Geo.

## <a name="mailbox-placement-and-moves"></a>Los movimientos y colocación de buzón
Tras completa los pasos previos de configuración Multi-Geo, a Microsoft Exchange Online respeta el atributo **PreferredDataLocation** en objetos de usuario en AD de Azure.

Exchange Online sincroniza la propiedad **PreferredDataLocation** de Azure AD en la propiedad **MailboxRegion** en el servicio de directorio de Exchange en línea. El valor de **MailboxRegion** determina el Geo donde se colocarán los buzones de usuario y cualquier archivo asociado. No es posible configurar los buzones principales de buzón y archiving de un usuario para que residan en zonas distintas. Solo Geo puede configurarse por cada objeto de usuario.

- Cuando **PreferredDataLocation** está configurado en un usuario con un buzón existente, el buzón se moverán automáticamente a la Geo especificado. 

- Cuando **PreferredDataLocation** está configurado en un usuario sin un buzón existente, el buzón se aprovisionará en el Geo especificado. 

- Si no se especifica ningún Geo, el buzón se colocará en el valor predeterminado de Geo.

**Nota**: capacidades de Multi-Geo y Skype para reuniones de negocios en línea alojado regionalmente ambos utilizan la propiedad **PreferredDataLocation** en objetos de usuario para buscar servicios. Si configura los valores de **PreferredDataLocation** en objetos de usuario para reuniones regionalmente hospedados, el buzón y OneDrive para los usuarios se moverá automáticamente a la Geo especificado después de habilita Multi-Geo en el inquilino de Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitaciones de características para Multi-Geo en Exchange Online
1. Sólo los buzones de usuario, buzones de recursos (buzones de sala y equipo) y buzones compartidos admiten características de Multi-Geo. Sólo puede colocar buzones de carpetas públicas y grupos de Office 365 en Geo principal del cliente.
 
2. Seguridad y cumplimiento de normas características (por ejemplo, auditoría y eDiscovery) que están disponibles en el centro de administración de Exchange (EAF) no están disponibles en las organizaciones Multi-Geo. En su lugar, debe utilizar el [Centro de cumplimiento de normas y seguridad de Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar características de seguridad y cumplimiento de normas.

3. Outlook para usuarios de Mac puede experimentar una pérdida temporal de acceso a su carpeta de archiving en línea mientras mueve su buzón a un nuevo Geo. Esta condición se produce cuando del usuario principal y archive los buzones están en diferentes zonas, debido a movimientos de buzones entre Geo pueden completar en diferentes momentos.

4. Los usuarios no pueden compartir *carpetas del buzón* a través de zonas en Outlook en el web (anteriormente conocido como Outlook Web App u OWA). Por ejemplo, un usuario de la Unión Europea no puede utilizar Outlook en el web para abrir una carpeta compartida en un buzón que se encuentra en los Estados Unidos. Sin embargo, Outlook de los usuarios de web puede abrir *otros buzones* en distintas zonas utilizando una ventana de explorador independiente como se describe en [Abrir el buzón de otra persona en una ventana de explorador independiente en Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Nota**: compartir una carpeta buzón entre Geo es compatible con Outlook en Windows.

5. Actualmente, no es compatible entre Geo delegación de calendario en Outlook en el web. Delegación de calendario entre Geo es compatible con Outlook en Windows.

## <a name="administration"></a>Administración 
PowerShell remoto es requerido para ver y configurar propiedades de Geo en el entorno de Office 365. Para obtener información sobre los distintos módulos de PowerShell utilizados para administrar Office 365, vea [administración de Office 365 y Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).

- Necesita el [Módulo de PowerShell de Active Directory de Microsoft Azure](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o posterior de v1.x para ver la propiedad **PreferredDataLocation** en objetos de usuario. Para conectarse a Azure AD PowerShell, vea [conectarse a Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Para conectarse a Exchange Online PowerShell, vea [conectarse a Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Conectar directamente a un Geo específico usando PowerShell en línea de Exchange
Normalmente, Exchange Online PowerShell se conectará con el valor predeterminado de Geo. Sin embargo, también puede conectar directamente a zonas no predeterminada. Debido a las mejoras de rendimiento, le recomendamos conectarse directamente a la Geo no predeterminada cuando sólo administra los usuarios en ese Geo.

Para conectarse a un Geo específica, el parámetro *ConnectionUri* es diferente de las instrucciones de conexión normales. El resto de los comandos y los valores son los mismos. Los pasos son:

1. En el equipo local, abra Windows PowerShell y ejecute el siguiente comando:
    
    ```
    $UserCredential = Get-Credential
    ```
   En el cuadro de diálogo **Solicitud de credencial de Windows PowerShell** , escriba la contraseña o cuenta de escuela y trabajo y, a continuación, haga clic en **Aceptar**.
    
2. Reemplazar `<emailaddress>` con la dirección de correo electrónico de **cualquier** buzón del destino geográfico y ejecute el siguiente comando. Sus permisos en el buzón y la relación con sus credenciales en el paso 1 no son un factor; la dirección de correo electrónico simplemente indica a Exchange Online dónde conectar.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Por ejemplo, si olga@contoso.onmicrosoft.com es la dirección de correo electrónico de un buzón válido en el Geo que desea conectarse, ejecute el siguiente comando:

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Ejecute el siguiente comando:
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Requisitos de versión de Azure Connect de AD
Conectar DAA versión 1.1.524.0 o posterior es el único método admitido para establecer la propiedad **PreferredDataLocation** en objetos de usuario que se sincronizan desde local de Active Directory. Para obtener instrucciones detalladas, consulte [sincronización de directorio activo Azure Connect: configurar ubicación de datos preferido de recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Códigos de geo
Utilice códigos de tres letras para especificar el Geo en la propiedad **PreferredDataLocation** . En la siguiente tabla enumera los códigos para las zonas disponibles:

|Geo |Código |
|---------|---------|
|Asia y Pacífico |APC |
|Australia |AUSTRALIA |
|Canadá |PUEDE |
|Unión Europea |EUROS |
|India |IND |
|Japón |JPN |
|Corea |KOR |
|Reino Unido |GBR |
|Estados Unidos |NAM |

**Nota**: las propiedades **PreferredDataLocation** y **MailboxRegion** son cadenas con ninguna comprobación de errores. Si escribe un valor no válido (por ejemplo, NAN) el buzón se colocará en el valor predeterminado de Geo.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Ver las zonas disponibles que están configurados en la organización de Exchange Online
Para ver la lista de zonas configuradas en la organización de Exchange Online, ejecute el siguiente comando en Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table Region
```

El resultado del comando tiene este aspecto:

```
Region
------
APC
AUS
CAN
EUR
GBR
JPN
KOR
NAM
```

### <a name="find-the-geo-location-of-a-mailbox"></a>Buscar la ubicación geográfica de un buzón
El cmdlet **Get-Mailbox** en Exchange Online PowerShell muestra las propiedades siguientes relacionadas con el Geo en buzones:

- **Base de datos**: las 3 primeras letras del nombre de la base de datos corresponden al código geográfico, que indica dónde se encuentra el buzón.

- **MailboxRegion**: especifica el código geográfico establecido por el administrador (sincronizado desde **PreferredDataLocation** en Azure AD).

- **MailboxRegionLastUpdateTime**: indica MailboxRegion se actualizaron por última vez (automática o manualmente).

Para ver las propiedades de un buzón, utilice la sintaxis siguiente:

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Por ejemplo, para ver la información geográfica para el buzón de chris@contoso.onmicrosoft.com, ejecute el siguiente comando:

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

El resultado del comando tiene este aspecto:

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> [!NOTE]
> Si el código geográfico en el nombre de la base de datos no coincide con el valor de **MailboxRegion** , el buzón se moverá automáticamente a la Geo especificado por el valor de **MailboxRegion** (Exchange Online busca una falta de coincidencia entre estos valores de propiedad).

### <a name="move-an-existing-cloud-mailbox-to-a-specific-geo"></a>Mover un buzón existente de nube para un específico Geo
Use los cmdlets **Get-MsolUser** y **MsolUser del conjunto** del módulo de AD de Azure para Windows PowerShell para ver o especificar el Geo donde se almacenará el buzón de un usuario.

Para ver el valor de **PreferredDataLocation** para un usuario, utilice esta sintaxis en Azure AD PowerShell:

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Por ejemplo, para ver el valor de **PreferredDataLocation** de la michelle@contoso.onmicrosoft.com usuario, ejecute el siguiente comando:

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

El resultado del comando tiene este aspecto:

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

Para modificar el valor de **PreferredDataLocation** para un objeto de usuario sólo nube, utilice la siguiente sintaxis en Azure AD PowerShell:

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Por ejemplo, para establecer el valor de **PreferredDataLocation** a la Unión Europea (en euros) para la michelle@contoso.onmicrosoft.com usuario, ejecute el comando siguiente:

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Notas**:

- Como se mencionó anteriormente sincronizado para objetos de usuario de Active Directory de local, no puede utilizar este procedimiento. Debe cambiar el valor de **PreferredDataLocation** con conexión DAA. Para obtener más información, consulte [sincronización de directorio activo Azure Connect: configurar ubicación de datos preferido de recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- ¿Cuánto tiempo tarda en mover un buzón depende de varios factores:
 
  - El tamaño y el tipo de buzón.
 
  - El número de buzones que se mueve.
 
  - La disponibilidad de los recursos de movimiento.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Deshabilitado de mover los buzones que están en retención para litigios
Deshabilitado buzones en retención para litigios que se conservan para propósitos no se pueden mover cambiando su valor de **PreferredDataLocation** en su estado deshabilitado de eDiscovery. Para mover un buzón deshabilitado en retención para litigios:

1. Asignar temporalmente una licencia en el buzón.

2. Cambiar el **PreferredDataLocation**.

3. Eliminar la licencia del buzón de correo después de que se ha movido a la Geo seleccionada para volver a colocarla en el estado deshabilitado.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Crear nuevos buzones de nube en un geográfico específico 
Para crear un nuevo buzón en un geográfico específico, que debe hacer cualquiera de estos pasos:

- Configurar el valor de **PreferredDataLocation** como se describe en la anterior sección *antes de* crear el buzón de Exchange en línea (por ejemplo, al configurar el valor de **PreferredDataLocation** en un usuario antes de asignar una licencia). 

- Asignar una licencia a la vez que se establece el valor de **PreferredDataLocation** .

Para crear un nuevo sólo nube con licencia usuario (DAA conectar sincronizado) en un geográfico específico, utilice la siguiente sintaxis en Azure AD PowerShell:

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
Este ejemplo crea una nueva cuenta de usuario para Elizabeth Brunner con los siguientes valores:

- Nombre principal de usuario: ebrunner@contoso.onmicrosoft.com

- Nombre: Elizabeth

- Apellido: Arturo López

- Mostrar nombre Elizabeth Brunner

- Contraseña: genera de forma aleatoria y se muestra en los resultados del comando (ya no estamos utilizando el parámetro de *contraseña* )

- Licencia: contoso:ENTERPRISEPREMIUM (E5)

3-ubicación: Australia (AUS)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Para obtener más información sobre cómo crear nuevas cuentas de usuario y buscar valores LicenseAssignment en Azure AD PowerShell, consulte [crear cuentas de usuario con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) y [ver licencias y servicios con PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> [!NOTE]
> Si está utilizando Exchange PowerShell para habilitar un buzón y necesita el buzón que se creen directamente en el Geo que se especifica en **PreferredDataLocation**, necesitará utilizar un cmdlet Exchange Online como **Enable-Mailbox** o **New-Mailbox** directamente con el servicio de nube. Si utiliza el cmdlet de Exchange local **Enable-RemoteMailbox** , se creará el buzón en el valor predeterminado de Geo.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Existente incorporado local buzones en un geográfico específico
Puede utilizar las herramientas estándar de incorporación y procesos para migrar un buzón desde una organización de Exchange local para Exchange Online, que incluye el [panel de la migración en el CEF](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)y el cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) en Exchange Online PowerShell.

El primer paso es comprobar que existe un objeto de usuario para que cada buzón onboarded y compruebe que el valor correcto de la **PreferredDataLocation** está configurado en Azure AD. Las herramientas de incorporación respetarán el valor **PreferredDataLocation** y migrarán los buzones directamente a la Geo especificado.

O bien, puede utilizar los pasos siguientes para buzones incorporados directamente en un geográfico específico mediante el cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) de PowerShell en línea de Exchange.

1. Compruebe que existe el objeto de usuario para que cada buzón sea onboarded y que **PreferredDataLocation** se establece en el valor deseado en Azure AD. El valor de **PreferredDataLocation** se sincronizarán con el atributo **MailboxRegion** del objeto de usuario de correo correspondiente de Exchange en línea.

2. Conectar directamente con el satélite específico Geo mediante las instrucciones de conexión del anteriormente en este tema.

3. En PowerShell de Exchange Online, almacenar las credenciales de administrador local que se utiliza para realizar una migración de buzones en una variable ejecutando el comando siguiente:

    ```
    $RC = Get-Credential
    ```

4. En PowerShell en línea de Exchange, cree un nuevo **MoveRequest de nuevo** similar al ejemplo siguiente: 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Repita el paso 4 # para cada buzón que necesita para migrar desde Exchange local al satélite Geo actualmente está conectado a.

6. Si necesita migrar buzones adicionales a un satélite diferente Geo, repita los pasos 2 a 4 para cada satélite específico geográfico.

### <a name="multi-geo-reporting"></a>Reporting de Multi-Geo
**Informes de uso de Multi-Geo** en el centro de administración de Office 365 se muestra el número de usuarios por Geo. El informe muestra la distribución de usuario para el mes actual y proporciona datos históricos de los últimos 6 meses.
 
