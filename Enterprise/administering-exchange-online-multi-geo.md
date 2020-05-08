---
title: Administración de buzones de correo de Exchange Online en un entorno multigeográfico
ms.reviewer: adwood
ms.author: chrisda
author: chrisda
manager: serdars
audience: ITPro
ms.topic: article
ms.service: o365-solutions
f1.keywords:
- NOCSH
ms.custom: ''
localization_priority: Priority
description: Obtenga información sobre cómo administrar el ajuste multigeográfico de Exchange Online con Microsoft PowerShell.
ms.openlocfilehash: 5dac890d2b0d5a797f8c2507c115c14147add7ff
ms.sourcegitcommit: 012bf4d8ad132435f9baeffd6f7e5ed264a8bfe0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/06/2020
ms.locfileid: "44057656"
---
# <a name="administering-exchange-online-mailboxes-in-a-multi-geo-environment"></a>Administración de buzones de correo de Exchange Online en un entorno multigeográfico

Se requiere un PowerShell remoto para ver y configurar las propiedades multigeográficas en su entorno de Microsoft 365. Para conectarse a PowerShell de Exchange Online, consulte [Conectarse a PowerShell de Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell).

Necesitará la v1.1.166.0 o una versión posterior en la v1.x del [módulo PowerShell de Microsoft Azure Active Directory](https://social.technet.microsoft.com/wiki/contents/articles/28552.microsoft-azure-active-directory-powershell-module-version-release-history.aspx) para ver la propiedad **PreferredDataLocation** en los objetos de usuario. No se puede modificar el valor de **PreferredDataLocation** directamente a través del PowerShell de AAD en los objetos de usuario que se sincronizan en AAD a través de AAD Connect. Solo se pueden modificar objetos basados en la nube a través del PowerShell de AAD. Para conectarse al PowerShell de Azure AD, consulte [Conectarse al PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell).

## <a name="connect-directly-to-a-geo-location-using-exchange-online-powershell"></a>Conectarse directamente a una ubicación geográfica con el PowerShell de Exchange Online

Normalmente, el PowerShell de Exchange Online se conecta a la ubicación geográfica central. Sin embargo, también puede conectarse directamente a las ubicaciones geográficas satélite. Debido a las mejoras en el rendimiento, se recomienda conectarse directamente a la ubicación satélite si únicamente administra usuarios en esa ubicación.

Para conectarse a una ubicación geográfica específica, el parámetro *ConnectionUri* es diferente a las instrucciones de conexión normales. El resto de comandos y valores son los mismos. Estos pasos son:

1. En el equipo local, abra Windows PowerShell y ejecute el siguiente comando:

   ```powershell
   $UserCredential = Get-Credential
   ```

   En el cuadro de diálogo **Solicitud de credenciales para Windows PowerShell**, escriba el usuario de su cuenta profesional o educativa y la contraseña, y luego haga clic en **Aceptar**.

2. Reemplace `<emailaddress>` con la dirección de correo electrónico de **cualquier** buzón en la ubicación geográfica de destino y ejecute el comando siguiente. Los permisos en el buzón y la relación con sus credenciales en el paso 1 no se tienen en cuenta; la dirección de correo electrónico simplemente indica a Exchange Online dónde debe conectarse.
  
   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=<emailaddress> -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

   Por ejemplo, si olga@contoso.onmicrosoft.com es la dirección de correo electrónico de un buzón válido en la ubicación geográfica a la que desea conectarse, ejecute el siguiente comando:

   ```powershell
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell?email=olga@contoso.onmicrosoft.com -Credential $UserCredential -Authentication  Basic -AllowRedirection
   ```

3. Ejecute el siguiente comando:

    ```powershell
    Import-PSSession $Session
    ```

## <a name="view-the-available-geo-locations-that-are-configured-in-your-exchange-online-organization"></a>Ver las ubicaciones geográficas disponibles configuradas en su organización de Exchange Online

Para ver la lista de ubicaciones geográficas configuradas en Microsoft 365 Multi-Geo, ejecute el siguiente comando en el PowerShell de Exchange Online:

```powershell
Get-OrganizationConfig | Select -ExpandProperty AllowedMailboxRegions | Format-Table
```

## <a name="view-the-central-geo-location-for-your-exchange-online-organization"></a>Ver la ubicación geográfica central para su organización de Exchange Online

Para ver la ubicación geográfica central de su inquilino, ejecute el siguiente comando en el PowerShell de Exchange Online:

```powershell
Get-OrganizationConfig | Select DefaultMailboxRegion
```

## <a name="find-the-geo-location-of-a-mailbox"></a>Buscar la ubicación geográfica de un buzón

El cmdlet **Get-Mailbox** en el PowerShell de Exchange Online muestra las siguientes propiedades multigeográficas en buzones:

- **Database**: Las tres primeras letras del nombre de la base de datos corresponden al código geográfico, que indica dónde se encuentra el buzón. Para los buzones de archivo en línea, podría usarse la propiedad **ArchiveDatabase**.

- **MailboxRegion**: Especifica el código de ubicación geográfica definido por el administrador (sincronizado desde **PreferredDataLocation** en Azure AD).

- **MailboxRegionLastUpdateTime**: Indica cuándo se actualizó MailboxRegion por última vez (de forma automática o manual).

Para ver estas propiedades de un buzón, use la siguiente sintaxis:

```powershell
Get-Mailbox -Identity <MailboxIdentity> | Format-List Database,MailboxRegion*
```

Por ejemplo, para ver la información geográfica del buzón chris@contoso.onmicrosoft.com, ejecute el siguiente comando:

```powershell
Get-Mailbox -Identity chris@contoso.onmicrosoft.com | Format-List Database, MailboxRegion*
```

El resultado del comando tiene este aspecto:

```powershell
Database                    : EURPR03DG077-db007
MailboxRegion               : EUR
MailboxRegionLastUpdateTime : 2/6/2018 8:21:01 PM
```

> **Nota:** Si el código de ubicación geográfica en el nombre de la base de datos no coincide con el valor de **MailboxRegion**, el buzón se pondrá automáticamente en una cola de reubicación y se moverá a la ubicación geográfica especificada por el valor ** MailboxRegion** (Exchange Online busca un error de coincidencia entre estos valores de propiedad).

## <a name="move-an-existing-cloud-only-mailbox-to-a-specific-geo-location"></a>Mover un buzón existente basado únicamente en la nube a una ubicación geográfica específica

Un usuario basado únicamente en la nube es un usuario que no está sincronizado con el inquilino a través de AAD Connect. Dicho usuario se creó directamente en Azure AD. Use los cmdlets **Get-MsolUser** y **Set-MsolUser** en el módulo de Azure AD para Windows PowerShell para ver o especificar la ubicación geográfica donde se almacenará el buzón de un usuario basado únicamente en la nube.

Para ver el valor **PreferredDataLocation** de un usuario, use la siguiente sintaxis en el PowerShell de Azure AD:

```powershell
Get-MsolUser -UserPrincipalName <UserPrincipalName> | Format-List UserPrincipalName,PreferredDataLocation
```

Por ejemplo, para ver el valor de **PreferredDataLocation** para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:

```powershell
Get-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com | Format-List
```

Para modificar el valor de **PreferredDataLocation** para un objeto de un usuario basado únicamente en la nube, use la siguiente sintaxis en el PowerShell de Azure AD:

```powershell
Set-MsolUser -UserPrincipalName <UserPrincipalName> -PreferredDataLocation <GeoLocationCode>
```

Por ejemplo, para definir el valor de **PreferredDataLocation** en la ubicación geográfica Unión Europea (EUR) para el usuario michelle@contoso.onmicrosoft.com, ejecute el siguiente comando:

```powershell
Set-MsolUser -UserPrincipalName michelle@contoso.onmicrosoft.com -PreferredDataLocation EUR
```

**Notas**:

- Como se mencionó anteriormente, no puede usar este procedimiento para objetos sincronizados del usuario desde el entorno local de Active Directory. Tiene que cambiar el valor de **PreferredDataLocation** en Active Directory y sincronizarlo con AAD Connect. Para obtener más información, consulte [Sincronización de Azure Active Directory Connect: configurar la ubicación de datos preferida para recursos de Microsoft 365](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnectsync-feature-preferreddatalocation).

- El tiempo que se tarda en reubicar un buzón a una nueva ubicación geográfica depende de varios factores:

  - El tamaño y tipo de buzón.

  - La cantidad de buzones que se migrarán.

  - La disponibilidad de recursos de migración.

### <a name="move-disabled-mailboxes-that-are-on-litigation-hold"></a>Mover buzones deshabilitados que se encuentran en Retención por juicio

Los buzones deshabilitados en Retención por juicio que se conservan para eDiscovery no se pueden mover cambiando el valor de **PreferredDataLocation** en el estado deshabilitado. Para mover un buzón deshabilitado en Retención por juicio:

1. Asigne temporalmente una licencia al buzón.

2. Cambie el valor de **PreferredDataLocation**.

3. Elimine la licencia del buzón después de moverlo a la ubicación geográfica seleccionada para volver a definir el estado de deshabilitado.

## <a name="create-new-cloud-mailboxes-in-a-specific-geo-location"></a>Crear nuevos buzones basados en la nube en una ubicación geográfica específica

Para crear un nuevo buzón en una ubicación geográfica específica, debe realizar uno de estos pasos:

- Configurar el valor de **PreferredDataLocation** como se describe en la sección anterior *antes* de crear el buzón en Exchange Online. Por ejemplo, configure el valor de **PreferredDataLocation** de un usuario antes de asignarle una licencia.

- Asignar una licencia al mismo tiempo que se define el valor de **PreferredDataLocation**.

Para crear un nuevo usuario con licencia basado únicamente en la nube (que no esté sincronizado con AAD Connect) en una ubicación geográfica específica, use la siguiente sintaxis en el PowerShell de Azure AD:

```powershell
New-MsolUser -UserPrincipalName <UserPrincipalName> -DisplayName "<Display Name>" [-FirstName <FirstName>] [-LastName <LastName>] [-Password <Password>] [-LicenseAssignment <AccountSkuId>] -PreferredDataLocation <GeoLocationCode>
```

Este ejemplo crea una cuenta de usuario para Elizabeth Brunner con los valores siguientes:

- Nombre de usuario principal: ebrunner@contoso.onmicrosoft.com

- Nombre: Elizabeth

- Apellido: Brunner

- Nombre para mostrar: Elizabeth Brunner

- Contraseña: Se genera de forma aleatoria y se muestra en los resultados del comando (debido a que no se usa el parámetro *contraseña*)

- Licencia: `contoso:ENTERPRISEPREMIUM` (E5)

- Ubicación: Australia (AUS)

```powershell
New-MsolUser -UserPrincipalName ebrunner@contoso.onmicrosoft.com -DisplayName "Elizabeth Brunner" -FirstName Elizabeth -LastName Brunner -LicenseAssignment contoso:ENTERPRISEPREMIUM -PreferredDataLocation AUS
```

Para obtener más información sobre cómo crear nuevas cuentas de usuario y cómo encontrar valores de LicenseAssignment en el PowerShell de Azure AD, consulte [Crear cuentas de usuario con PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/create-user-accounts-with-office-365-powershell) y [Ver licencias y servicios con PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/view-licenses-and-services-with-office-365-powershell).

> [!NOTE]
> Si usa el PowerShell de Exchange Online para habilitar un buzón y necesita que este se cree directamente en la ubicación geográfica especificada en **PreferredDataLocation**, debe usar un cmdlet de Exchange Online como **Enable-Mailbox** o **New-Mailbox** directamente con el servicio basado en la nube. Si usa el cmdlet **Enable-RemoteMailbox** en el entorno local de Exchange PowerShell, el buzón se creará en la ubicación geográfica central.

## <a name="onboard-existing-on-premises-mailboxes-in-a-specific-geo-location"></a>Incorporar buzones existentes en el entorno local a una ubicación geográfica específica

Puede usar las herramientas y procesos de incorporación estándar para migrar un buzón del entorno local de una organización de Exchange a Exchange Online, incluidos el [Panel de migración en el EAC](https://support.office.com/article/d164b35c-f624-4f83-ac58-b7cae96ab331) y el cmdlet [New-MigrationBatch](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-migrationbatch) del PowerShell de Exchange Online.

El primer paso consiste en comprobar que existe un objeto de usuario para que cada buzón se quiere incorporar y comprobar que el valor de **PreferredDataLocation** está configurado correctamente en Azure AD. Las herramientas de incorporación respetarán el valor de **PreferredDataLocation** y migrarán los buzones directamente a la ubicación geográfica especificada.

Como alternativa, puede seguir los pasos a continuación para incorporar buzones directamente a una ubicación geográfica específica con el cmdlet [New-MoveRequest](https://docs.microsoft.com/powershell/module/exchange/move-and-migration/new-moverequest) del PowerShell de Exchange Online.

1. Compruebe que existe el objeto de usuario para cada buzón que se va a incorporar y que **PreferredDataLocation** está definido en el valor deseado en Azure AD. El valor de **PreferredDataLocation** se sincronizará con el atributo **MailboxRegion** del objeto de usuario del correo correspondiente en Exchange Online.

2. Conéctese directamente con la ubicación geográfica satélite específica siguiendo las instrucciones de conexión mostradas anteriormente en este tema.

3. En el PowerShell de Exchange Online, almacene en una variable las credenciales de administrador del entorno local que se usan para realizar una migración de buzones ejecutando el siguiente comando:

   ```powershell
   $RC = Get-Credential
   ```

4. En el PowerShell de Exchange Online, cree un nuevo **New-MoveRequest** similar al del ejemplo siguiente:

   ```powershell
   New-MoveRequest -Remote -RemoteHostName mail.contoso.com -RemoteCredential $RC -Identity user@contoso.com -TargetDeliveryDomain <YourAppropriateDomain>
   ```

5. Repita el paso 4 para cada buzón que quiera migrar del entorno local de Exchange a la ubicación geográfica satélite a la que está conectado actualmente.

6. Si quiere migrar más buzones a ubicaciones geográficas satélite diferentes, repita los pasos 2 a 4 para cada ubicación específica.

## <a name="multi-geo-reporting"></a>Informes multigeográficos

Los **Informes de uso multigeográfico** en el Centro de administración de Microsoft 365 muestran el número de usuarios por ubicación geográfica. El informe muestra la distribución de usuarios durante el mes actual y proporciona los datos históricos para los últimos 6 meses.

## <a name="see-also"></a>Consulte también

[Administración de Microsoft 365 y Exchange Online con Windows PowerShell](https://support.office.com//article/06a743bb-ceb6-49a9-a61d-db4ffdf54fa6)
