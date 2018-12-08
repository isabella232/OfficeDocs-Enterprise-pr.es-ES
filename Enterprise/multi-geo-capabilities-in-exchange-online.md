---
title: Capacidades de Multi-Geo en Exchange Online
ms.author: chrisda
author: chrisda
manager: serdars
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.custom: ''
localization_priority: Normal
ms.assetid: ''
description: Expanda su información de presencia de Office 365 a varias regiones geográficas con multi-ubican las capacidades de Exchange Online.
ms.openlocfilehash: 6acd2ffab1f35b74d06d6ab5f7bfcbf70f88f8b4
ms.sourcegitcommit: 03bb9edd52b1b7cd49791baf90645828b89b32b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/07/2018
ms.locfileid: "27200743"
---
# <a name="multi-geo-capabilities-in-exchange-online"></a>Capacidades de Multi-Geo en Exchange Online

Capacidades de Multi-ubican en Office 365 habilitar un inquilino único abarcar varias ubicaciones geográficas. Al multi-ubican está habilitada, los clientes pueden seleccionar la ubicación del contenido del buzón Exchange Online (datos en reposo) por usuario.

La ubicación inicial de inquilinos (denominada la ubicación central) se determina en función de su dirección de facturación. Cuando está habilitada la multi-ubican, puede poner los buzones de correo en ubicaciones de satélite adicionales por:

- Creación de un nuevo buzón de Exchange Online directamente en una ubicación de satélite.

- Mover un buzón de Exchange Online existente en una ubicación de satélite.

- Incorporación de un buzón de correo desde una organización de Exchange local directamente en una ubicación de satélite.

Las siguientes ubicaciones ubican están disponibles para su uso en una configuración de Multi-Geo:

- Asia Pacífico

- Australia

- Canadá

- Unión Europea

- Francia

- India

- Japón

- Corea

- Reino Unido

- Estados Unidos

## <a name="prerequisite-configuration"></a>Configuración de requisitos previos
Antes de empezar a usar las capacidades de Multi-Geo en Exchange Online, Microsoft tiene que configurar a su inquilino de Exchange Online para ofrecer compatibilidad con multi-ubican. Este proceso de configuración de una sola vez se desencadena después de haber ordenado que Office 365 Multi-Geo y las licencias se muestran en el inquilino. Este proceso de configuración única normalmente debe tardar menos de 30 días en completarse. Para solicitar Office 365 Multi-ubican, póngase en contacto con su representante de Microsoft. Para obtener más información, consulte https://aka.ms/Multi-Geo.

Recibirá notificaciones en el [Centro de mensajes de Office 365](https://support.office.com/article/Message-center-in-Office-365-38FB3333-BFCC-4340-A37B-DEDA509C2093) cuando haya finalizado la configuración. Configuración se activa automáticamente una vez que las licencias de multi-ubican aparezcan en el inquilino.

## <a name="mailbox-placement-and-moves"></a>Se desplaza y colocación de buzón de correo
Después de que Microsoft lleva a cabo los pasos de configuración de multi-ubican necesario como requisito previo, Exchange Online respeta el atributo **PreferredDataLocation** en objetos de usuario en Azure AD.

Exchange Online se sincroniza la propiedad **PreferredDataLocation** de Azure AD en la propiedad **MailboxRegion** en el servicio de directorio Exchange Online. El valor de **MailboxRegion** determina el ubican donde se colocará los buzones de usuario y cualquier archivo asociado. No es posible configurar los buzones principales de buzón de correo y de archivo de un usuario para residen en ubican diferentes ubicaciones. Se puede configurar una única ubicación ubican por objeto de usuario.

- Cuando **PreferredDataLocation** está configurado en un usuario con un buzón existente, el buzón de correo se coloque en una cola de reubicación y se mueve automáticamente a la ubicación geográfica especificada. 

- Cuando **PreferredDataLocation** está configurado en un usuario sin un buzón existente, se aprovisionará el buzón de correo en la ubicación geográfica especificada. 

- Cuando no se especifica **PreferredDataLocation** en un usuario, el buzón de correo se colocará en la ubicación central.

- Si el código de **PreferredDataLocation** es incorrecto (por ejemplo, un tipo de NAN en lugar del nombre), el buzón de correo se colocará en la ubicación central.

**Nota**: multi-ubican capacidades y Skype para profesionales reuniones en línea hospedado regional ambos usan la propiedad **PreferredDataLocation** en objetos de usuario para localizan los servicios. Si configura los valores de **PreferredDataLocation** en objetos de usuario para las reuniones de ámbito regional hospedados, el buzón de correo para esos usuarios se moverá automáticamente a la ubicación especificada ubican después de habilita multi-ubican en el inquilino de Office 365.

## <a name="feature-limitations-for-multi-geo-in-exchange-online"></a>Limitaciones de características para Multi-Geo en Exchange Online
1. Sólo buzones de usuario, buzones de recursos (buzones de correo de sala y equipamiento) y buzones compartidos admiten características de multi-ubican. Públicas buzones de carpetas y grupos de Office 365 permanecen en la ubicación central.
 
2. Seguridad y cumplimiento de normas características (por ejemplo, auditoría y exhibición de documentos electrónicos) que están disponibles en el centro de administración de Exchange (EAC) no están disponibles en las organizaciones multi-ubican. En su lugar, debe usar el [Centro de cumplimiento y seguridad de Office 365](https://support.office.com/article/7e696a40-b86b-4a20-afcc-559218b7b1b8) para configurar las características de seguridad y cumplimiento de normas.

3. Outlook para los usuarios de Mac puede experimentar una pérdida temporal de acceso a su carpeta de archivo en línea mientras su buzón se mueve a una nueva ubicación geográfica. Esta condición se produce cuando del usuario principal y buzones de archivo se encuentran en ubicaciones diferentes ubican, debido a que los movimientos de buzones entre ubican pueden completar en momentos diferentes.

4. Los usuarios no pueden compartir *las carpetas de buzón de correo* en las ubicaciones de ubican en Outlook en el web (anteriormente conocido como Outlook Web App u OWA). Por ejemplo, un usuario en la Unión Europea no puede usar Outlook en la web para abrir una carpeta compartida en un buzón que se encuentra en los Estados Unidos. Sin embargo, Outlook en los usuarios de Web puede abrir *otros buzones de correo* en diferentes zonas mediante el uso de una ventana del explorador independiente como se describe en [Abra el buzón de otra persona en una ventana del explorador independiente en Outlook Web App](https://support.office.com/article/A909AD30-E413-40B5-A487-0EA70B763081#__toc372210362).

    **Nota**: compartir una carpeta buzón entre geo se admite en Outlook en Windows.

## <a name="administration"></a>Administración 
PowerShell remoto es necesario para ver y configurar las propiedades de múltiples ubican en el entorno de Office 365. Para obtener información sobre los distintos módulos de PowerShell que se utiliza para Office 365, vea [administración de Office 365 y Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6).

- Necesitará el [Módulo de PowerShell de Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) v1.1.166.0 o más adelante en v1.x para ver la propiedad **PreferredDataLocation** en objetos de usuario. Objetos de usuario sincronizados a través de AAD conectar en AAD no pueden tener su valor **PreferredDataLocation** modificar directamente a través de PowerShell AAD. Objetos de usuario solo en nube pueden modificarse a través de PowerShell AAD. Para conectarse a AD de Windows Azure PowerShell, vea [Connect to Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell). 

- Para conectarse a Exchange Online PowerShell, vea [Connect to Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). 

### <a name="connect-directly-to-a-specific-geo-using-exchange-online-powershell"></a>Conectar directamente a un ubican específica con Exchange Online PowerShell
Normalmente, Exchange Online PowerShell se conectará a la ubicación predeterminada de geo. Sin embargo, también puede conectarse directamente a ubicaciones ubican no predeterminado. Debido a las mejoras de rendimiento, se recomienda conectarse directamente a la ubicación no predeterminada ubican al administrar sólo los usuarios de esa ubicación geográfica.

Para conectarse a un ubican específica, el parámetro *ConnectionUri* es diferente de las instrucciones de conexión regular. El resto de los comandos y los valores son los mismos. Los pasos son:

1. En el equipo local, abra Windows PowerShell y ejecute el siguiente comando:
    
    ```
    $UserCredential = Get-Credential
    ```
   En el cuadro de diálogo **Solicitud de credenciales de Windows PowerShell** , escriba su trabajo o escuela cuenta y su contraseña y, a continuación, haga clic en **Aceptar**.
    
2. Reemplace `<emailaddress>` con la dirección de correo electrónico de **cualquier** buzón de correo en la ubicación de destino geo y ejecute el comando siguiente. Los permisos en el buzón de correo y la relación con sus credenciales en el paso 1 no son un factor; la dirección de correo electrónico simplemente indica a Exchange Online dónde debe conectarse.
  
   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Por ejemplo, si olga@contoso.onmicrosoft.com es la dirección de correo electrónico de un buzón de correo válido en el Geo va a conectar, ejecute el siguiente comando:

   ```
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```
3. Ejecute el comando siguiente:
    
    ```
    Import-PSSession $Session
    ```

### <a name="azure-ad-connect-version-requirements"></a>Requisitos de versión de Azure Connect de AD
Conectar AAD versión 1.1.524.0 o posterior es el único método admitido para establecer la propiedad **PreferredDataLocation** en los objetos de usuario que se sincronizan desde Active Directory local. Objetos de usuario sincronizados a través de AAD conectar en AAD no pueden tener su valor **PreferredDataLocation** modificar directamente a través de PowerShell AAD. Objetos de usuario solo en nube pueden modificarse a través de PowerShell AAD. Para obtener instrucciones detalladas, consulte [sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferido para recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

### <a name="geo-codes"></a>Códigos de geo
Use los códigos de tres letras para especificar el ubican en la propiedad **PreferredDataLocation** . En la siguiente tabla se enumera los códigos de las zonas disponibles:

|Geo |Código |
|---------|---------|
|Asia Pacífico |APC |
|Australia |AUS |
|Canadá |CAN |
|Unión Europea |EUR |
|Francia |FRA|
|India |IND |
|Japón |JPN |
|Corea |KOR |
|Reino Unido |GBR |
|Estados Unidos |NAM |

**Nota**: las propiedades **PreferredDataLocation** y **MailboxRegion** son cadenas con ninguna comprobación de errores. Si escribe un valor no válido (por ejemplo, NAN) el buzón de correo se colocará en el valor predeterminado ubican.

### <a name="view-the-available-geos-that-are-configured-in-your-exchange-online-organization"></a>Ver las zonas disponibles que están configurados en la organización de Exchange Online
Para ver la lista de zonas configuradas en la organización de Exchange Online, ejecute el siguiente comando en Exchange Online PowerShell:

```
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

El resultado del comando tiene este aspecto:

```
APC
AUS
CAN
EUR
FRA
GBR
JPN
KOR
NAM
```

### <a name="view-the-default-geo-for-your-exchange-online-organization"></a>Ver el valor predeterminado Geo para la organización de Exchange Online
Para ver la ubican predeterminada de la organización de Exchange Online, ejecute el siguiente comando en Exchange Online PowerShell:

```
Get-OrganizationConfig | Select DefaultMailboxRegion
```

El resultado del comando tiene este aspecto:

```
DefaultMailboxRegion
--------------------
NAM
```


### <a name="find-the-geo-location-of-a-mailbox"></a>Busque la ubicación geográfica de un buzón de correo
El cmdlet **Get-Mailbox** en Exchange Online PowerShell muestra el siguiente multi-ubican relacionados con las propiedades de buzones de correo:

- **Base de datos**: el primero 3 letras del nombre de base de datos se corresponden con el código ubican, que indica donde se encuentra actualmente el buzón de correo. Propiedad debe utilizarse para buzones de archivo en línea la **ArchiveDatabase** .

- **MailboxRegion**: especifica el código de ubicación geográfica que se ha establecido por el administrador (sincronizado desde **PreferredDataLocation** en Azure AD).

- **MailboxRegionLastUpdateTime**: indica cuándo se actualizó por última vez las MailboxRegion (automático o manual).

Para ver estas propiedades para un buzón de correo, use la siguiente sintaxis:

```
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Por ejemplo, para ver la información de Geo para el buzón de correo chris@contoso.onmicrosoft.com, ejecute el siguiente comando:

```
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

El resultado del comando tiene este aspecto:

```
Database                    : EURPR03DG077-db007 
MailboxRegion               : EUR 
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM 
```

> **Nota:** Si el código de ubicación geográfica en el nombre de la base de datos no coincide con el valor de **MailboxRegion** , el buzón de correo será automáticamente pueden colocarse en una cola de reubicación y se mueve a la ubicación geográfica especificada por el valor de **MailboxRegion** (Exchange Online busca un Error de coincidencia entre estos valores de propiedad).

### <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo"></a>Mover un buzón de nube existente a un ubican específico
Un usuario sólo en la nube es un usuario no sincronizar en el inquilino a través de AAD conectar. Este usuario se creó directamente en Azure AD. Use los cmdlets **Get-MsolUser** y **Set-MsolUser** en el módulo de AD de Azure para Windows PowerShell para ver o especificar la ubican donde se almacenará el buzón de un usuario sólo en la nube.

Para ver el valor de **PreferredDataLocation** para un usuario, use esta sintaxis en Azure AD PowerShell:

```
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Por ejemplo, para ver el valor de **PreferredDataLocation** para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:

```
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

El resultado del comando tiene este aspecto:

```
UserPrincipalName     : michelle@contoso.onmicrosoft.com
PreferredDataLocation : EUR
```

Para modificar el valor de **PreferredDataLocation** para un objeto de usuario sólo en la nube, use la siguiente sintaxis en Azure AD PowerShell:

``` 
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoCode>
```

Por ejemplo, para establecer el valor de **PreferredDataLocation** en el ubican Unión Europea (EUR) para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:

``` 
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Notas**:

- Como se ha mencionado anteriormente no puede usar este procedimiento sincronizada para objetos de usuario de Active Directory local. Debe cambiar el valor de **PreferredDataLocation** mediante AAD conectar. Para obtener más información, vea [sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferido para recursos de Office 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation). 

- Cuánto tiempo tarda para reubicar un mailboxfrom que su ubican actual a la nueva ubicación deseada ubican depende de varios factores:
 
  - El tamaño y el tipo de buzón de correo.
 
  - El número de buzones que se va a mover.
 
  - La disponibilidad de recursos de movimiento.

#### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Move deshabilita los buzones de correo que se encuentran en suspensión por litigio
Deshabilita los buzones en suspensión por litigio que se conservan para exhibición de documentos electrónicos con fines no se puede mover mediante la modificación de su valor de **PreferredDataLocation** en su estado deshabilitado. Para mover un buzón deshabilitado en juicio:

1. Asignar temporalmente una licencia para el buzón de correo.

2. Cambiar el **PreferredDataLocation**.

3. Quitar la licencia desde el buzón de correo después de que se ha movido a la ubicación geográfica seleccionada para volver a colocarla en el estado deshabilitado.

### <a name="create-new-cloud-mailboxes-in-a-specific-geo"></a>Crear nuevos buzones de correo en la nube en un ubican específico 
Para crear un nuevo buzón de correo en una ubicación específica ubican, necesita realizar cualquiera de estos pasos:

- Configure el valor de **PreferredDataLocation** como se describe en la anterior sección *antes de* que crear el buzón en Exchange Online. Por ejemplo, configure el valor de **PreferredDataLocation** en un usuario antes de asignar una licencia. 

- Asignar una licencia al mismo tiempo, que se establece el valor de **PreferredDataLocation** .

Para crear un nuevo solo en nube con licencia usuario (no AAD conectarse sincronizado) en un ubican específica, use la siguiente sintaxis en Azure AD PowerShell:

```
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoCode> 
```
En este ejemplo se crea una nueva cuenta de usuario para Elizabeth Brunner con los siguientes valores:

- Nombre principal de usuario: ebrunner@contoso.onmicrosoft.com

- Nombre: Elizabeth

- Apellido: Arturo López

- Nombre para mostrar Elizabeth Brunner

- Contraseña: genera de forma aleatoria y se muestra en los resultados del comando (debido a que no estamos utilizando el parámetro *Password* )

- Licencia: contoso:ENTERPRISEPREMIUM (E5)

- Ubicación: Australia (Australia)

```
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Para obtener más información sobre cómo crear nuevas cuentas de usuario y búsqueda de valores de LicenseAssignment en Azure AD PowerShell, vea [crear cuentas de usuario con Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) y [ver licencias y servicios con PowerShell de Office 365](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> **Nota:** Si usa Exchange Online PowerShell para habilitar un buzón de correo y necesita el buzón de correo que se creará directamente en el ubican que se especifica en **PreferredDataLocation**, debe usar un cmdlet de Exchange Online como **Enable-Mailbox** o **New-Mailbox **directamente en el servicio de nube. Si usa el cmdlet de Exchange local **Enable-RemoteMailbox** , se creará el buzón de correo en el valor predeterminado ubican.

### <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo"></a>Incorporado existentes buzones locales en un ubican específico
Puede usar las herramientas de incorporación estándar y procesos para migrar un buzón de correo de una organización de Exchange local a Exchange Online, incluido el [panel de la migración en el EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331)y el cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) en Exchange Online PowerShell.

El primer paso es comprobar que existe un objeto de usuario para que cada buzón de correo ser onboarded y compruebe que el valor correcto de **PreferredDataLocation** está configurado en Azure AD. Las herramientas de incorporación respetarán el valor **PreferredDataLocation** y migrarán los buzones de correo directamente a la ubican especificado.

O bien, puede usar los siguientes pasos para los buzones de correo incorporados directamente en una ubicación geográfica específica mediante el cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) en Exchange Online PowerShell.

1. Compruebe si que existe el objeto de usuario para que cada buzón de correo ser onboarded y que **PreferredDataLocation** está establecida en el valor deseado de Azure AD. El valor de **PreferredDataLocation** se sincronizarán con el atributo **MailboxRegion** del objeto de usuario correspondiente de correo en Exchange Online.

2. Conectarse directamente al satélite específico ubican siguiendo las instrucciones de conexión desde anteriormente en este tema.

3. En Exchange Online PowerShell, almacenar las credenciales de administrador local que se utiliza para realizar una migración de buzones de correo en una variable, ejecute el comando siguiente:

    ```
    $RC = Get-Credential
    ```

4. En Exchange Online PowerShell, cree un nuevo **New-MoveRequest** similar al siguiente ejemplo: 

    ```
    New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
    ```

5. Repita el paso 4 # para cada buzón que necesita para migrar de Exchange local a la ubicación de satélite que está actualmente conectado.

6. Si necesita migrar buzones de correo adicionales a una ubicación diferente de satélite, repita los pasos del 2 al 4 para cada ubicación de satélite específicos.

### <a name="multi-geo-reporting"></a>Multi-ubican informes
**Multi-ubican los informes de uso** en el centro de administración de Office 365 muestra el recuento de usuarios por ubicación geográfica. El informe muestra la distribución de usuario para el mes actual y proporciona datos históricos de los últimos 6 meses.
