---
title: Usar PowerShell para realizar una migración preconfigurada a Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: a20f9dbd-6102-4ffa-b72c-ff813e700930
description: 'Resumen: Obtenga información sobre cómo usar Windows PowerShell para realizar una migración preconfigurada a Microsoft 365.'
ms.openlocfilehash: bc21ec403b0c6daa3fe2411f8f4fea790dd5e71c
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229796"
---
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a>Usar PowerShell para realizar una migración preconfigurada a Microsoft 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Puede migrar el contenido de los buzones de los usuarios desde un sistema de correo electrónico de origen a Microsoft 365 con el tiempo mediante una migración preconfigurada.
  
Este artículo le guiará a través de las tareas relacionadas con una migración preconfigurada de correo electrónico con Exchange Online PowerShell. El tema, [lo que debe saber sobre una migración preconfigurada de correo electrónico](https://go.microsoft.com/fwlink/p/?LinkId=536487), le ofrece información general sobre el proceso de migración. Cuando se sienta cómodo con el contenido de ese artículo, use este uno para empezar a migrar buzones de un sistema de correo electrónico a otro.
  
> [!NOTE]
> También puede usar el centro de administración de Exchange para realizar una migración preconfigurada. Consulte [realizar una migración preconfigurada de correo electrónico a Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de comenzar?

Tiempo estimado para finalizar esta tarea: 2-5 minutos para crear un lote de migración. Una vez iniciado el lote de migración, la duración de la migración variará en función del número de buzones de correo del lote, el tamaño de cada buzón y la capacidad de red disponible. Para obtener información acerca de otros factores que influyen en el tiempo necesario para migrar buzones a Microsoft 365, consulte [Migration performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Deberá tener permisos asignados para poder llevar a cabo estos procedimientos. Para ver qué permisos necesita, consulte la sección "Movimiento de buzón y permisos de migración" en el tema [Permisos de destinatarios](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Para usar los cmdlets de Exchange Online PowerShell, deberá iniciar sesión e importar los cmdlets en la sesión local de Windows PowerShell. Consulte [Conectarse a Exchange Online mediante PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obtener instrucciones.
  
Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Pasos de la migración

### <a name="step-1-prepare-for-a-staged-migration"></a>Paso 1: Prepararse para una migración preconfigurada

Antes de migrar los buzones a Microsoft 365 mediante una migración preconfigurada, hay algunos cambios que debe realizar en su entorno de Exchange.
  
 **Configure Outlook en cualquier lugar en su Exchange Server** local El servicio de migración de correo electrónico utiliza Outlook en cualquier lugar (también conocido como RPC sobre HTTP) para conectarse a su Exchange Server local. Para obtener información acerca de cómo configurar Outlook en cualquier lugar para Exchange Server 2007 y Exchange 2003, consulte los temas siguientes:
  
- [Exchange 2007: Cómo habilitar Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [Cómo configurar Outlook Anywhere con Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> Debe usar un certificado emitido por una entidad de certificación (CA) de confianza con su configuración de Outlook en cualquier lugar. Outlook en cualquier lugar no se puede configurar con un certificado autofirmado. Para obtener más información, consulte [Cómo configurar SSL para Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
 **Opcional: compruebe que puede conectarse a su organización Exchange con Outlook en cualquier lugar** Pruebe con uno de los métodos siguientes para probar la configuración de su conexión.
  
- Use Outlook desde fuera de la red corporativa para conectarse a su buzón de correo de Exchange local.
    
- Use el [analizador de conectividad remota de Microsoft](https://https://testconnectivity.microsoft.com/) para probar la configuración de conexión. Use las pruebas de Outlook Anywhere (RPC sobre HTTP) o de Outlook Autodiscover.
    
- Ejecute los comandos siguientes en Exchange Online PowerShell:
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 **Establecer permisos** La cuenta de usuario local que se usa para conectarse a la organización de Exchange local (también denominada administrador de migración) debe disponer de los permisos necesarios para tener acceso a los buzones locales que desea migrar a Microsoft 365. Esta cuenta de usuario se usa cuando se conecta a su sistema de correo electrónico mediante la creación de un extremo de migración más adelante en este procedimiento ([paso 3: crear un extremo de migración](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).
  
Para migrar los buzones de correo, el administrador debe tener uno de los siguientes conjuntos de permisos:
  
- Forme parte del grupo de **administradores de dominio** de Active Directory de la organización local.
    
    o bien
    
- Reciba el permiso **FullAccess** para cada buzón local y el permiso **WriteProperty** para modificar la propiedad **TargetAddress** en las cuentas de usuario locales.
    
    o bien
    
- Reciba el permiso **ReceiveAs** en la base de datos de buzones local en la que se almacenan los buzones de los usuarios y el permiso **WriteProperty** para modificar la propiedad **TargetAddress** en las cuentas de usuario locales.
    
Para obtener instrucciones acerca de cómo configurar estos permisos, consulte [asignar permisos para migrar buzones a Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656).
  
 **Deshabilitar mensajería unificada (UM)** Si la mensajería unificada está activada para los buzones locales que se van a migrar, desactive la mensajería unificada antes de la migración. Active la mensajería unificada para los buzones una vez completada la migración. Para obtener información sobre procedimientos, consulte[Cómo deshabilitar la mensajería unificada para un usuario](https://go.microsoft.com/fwlink/?LinkId=521891).
  
 **Use la sincronización de directorios para crear nuevos usuarios en Microsoft 365.** Use la sincronización de directorios para crear todos los usuarios locales de su organización de Microsoft 365.
  
Debe autorizar a los usuarios después de crearlos. Dispone de 30 días para agregar licencias después de haber creado los usuarios. Para conocer los pasos para agregar licencias, consulte [Paso 8: Finalizar las tareas posteriores a la migración](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).
  
 Puede usar la herramienta de sincronización de Microsoft Azure Active Directory (Azure AD) o los servicios de sincronización de Microsoft Azure AD para sincronizar y crear los usuarios locales en Microsoft 365. Después de migrar los buzones a Microsoft 365, administre las cuentas de usuario en su organización local y estén sincronizadas con la organización de Microsoft 365. Para obtener más información, consulte[integración de directorios](https://go.microsoft.com/fwlink/?LinkId=521788) .
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a>Paso 2: Crear un archivo CSV para un lote de migración preconfigurada

Después de identificar los usuarios cuyos buzones locales desea migrar a Microsoft 365, use un archivo de valores separados por comas (CSV) para crear un lote de migración. Cada fila del archivo CSV (usada por Microsoft 365 para ejecutar la migración) contiene información sobre un buzón local. 
  
> [!NOTE]
> No existe un límite para el número de buzones que se pueden migrar a Microsoft 365 mediante una migración preconfigurada. El archivo CSV de un lote de migración puede contener un máximo de 2.000 filas. Para migrar más de 2.000 buzones de correo, cree archivos CSV adicionales y use cada archivo para crear un nuevo lote de migración. 
  
 **Atributos admitidos**
  
El archivo CSV para una migración preconfigurada es compatible con los tres atributos siguientes. Cada fila del archivo CSV corresponde a un buzón y debe contener un valor para cada uno de estos atributos.
  
|**Atributo**|**Descripción**|**Obligatorio**|
|:-----|:-----|:-----|
|EmailAddress  <br/> |Especifica la dirección de correo electrónico SMTP principal (por ejemplo, pilarp@contoso.com) para los buzones locales.  <br/> Use la dirección SMTP principal para los buzones locales y no los identificadores de usuario de Microsoft 365. Por ejemplo, si el dominio local se denomina contoso.com, pero el dominio de correo electrónico de Microsoft 365 se denomina service.contoso.com, usaría el nombre de dominio contoso.com para las direcciones de correo electrónico en el archivo CSV.  <br/> |Necesario  <br/> |
|Contraseña  <br/> |La contraseña que se va a establecer para el nuevo buzón de correo de Microsoft 365. Las restricciones de contraseña que se aplican a la organización de Microsoft 365 también se aplican a las contraseñas incluidas en el archivo CSV.  <br/> |Opcional  <br/> |
|ForceChangePassword  <br/> |Especifica si un usuario debe cambiar la contraseña la primera vez que inicia sesión en el nuevo buzón de correo de Microsoft 365. Use **true** o **false** para el valor de este parámetro.<br/> > [!NOTE]> Si ha implementado una solución de inicio de sesión único (SSO) implantando los servicios de federación de Active Directory (AD FS) o superior en la organización local, debe usar **False** como valor del atributo **ForceChangePassword**.          |Opcional  <br/> |
   
 **Formato del archivo CSV**
  
A continuación, se muestra un ejemplo del formato del archivo CSV. En este ejemplo, se migran tres buzones locales a Microsoft 365.
  
En la primera fila, o fila de encabezado, del archivo CSV se enumeran los nombres de los atributos, o campos, especificados en las filas que le siguen. Los nombres de atributo se separan con una coma.
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

Cada fila que hay bajo la fila de encabezado representa a un usuario y proporciona la información que se usará para migrar el buzón del usuario. Los valores de atributo de cada fila deben seguir el mismo orden que los nombres de atributo de la fila de encabezado. 
  
Use cualquier editor de texto, o bien una aplicación como Excel para crear el archivo CSV. Guarde el archivo como .csv o .txt.
  
> [!NOTE]
> Si el archivo CSV contiene caracteres especiales o que no son ASCII, guárdelo con codificación UTF-8 o con otra codificación Unicode. Según la aplicación, puede resultar más fácil guardar el archivo CSV con codificación UTF-8 u otra codificación Unicode si la configuración regional del equipo coincide con el idioma utilizado en el archivo CSV. 
  
### <a name="step-3-create-a-migration-endpoint"></a>Paso 3: Crear un extremo de migración
<a name="BK_Endpoint"> </a>

Para migrar el correo electrónico correctamente, Microsoft 365 debe conectarse y comunicarse con el sistema de correo electrónico de origen. Para ello, Microsoft 365 usa un extremo de migración. Para crear un extremo de migración de Outlook en cualquier lugar con PowerShell, para la migración preconfigurada, primero [Conéctese a Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Para crear un extremo de migración de Outlook en cualquier lugar denominado "StagedEndpoint" en Exchange Online PowerShell, ejecute estos comandos:
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

Para obtener más información acerca del cmdlet **New-MigrationEndpoint**, consulte[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)
  
> [!NOTE]
> El cmdlet **New-MigrationEndpoint** puede usarse para especificar la base de datos que debe usar el servicio con la opción **-TargetDatabase**. Si no se hace, se asigna aleatoriamente una base de datos desde el sitio de Servicios de federación de Active Directory (AD FS) 2.0 donde se encuentra el buzón de administración.
  
#### <a name="verify-it-worked"></a>Compruebe que ha funcionado

En Exchange Online PowerShell, ejecute el siguiente comando para visualizar la información sobre el extremo de migración "StagedEndpoint":
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a>Paso 4: Crear e iniciar un lote de migración preconfigurada
<a name="BK_Endpoint"> </a>

Puede utilizar el cmdlet **New-MigrationBatch** en Exchange Online PowerShell para crear un lote de migración para una migración de traslado. Puede crear un lote de migración e iniciarlo automáticamente mediante la inclusión del parámetro _AutoStart_. O bien puede crear el lote de migración y, luego, iniciarlo posteriormente de forma manual mediante el uso del cmdlet **Start-MigrationBatch**. En este ejemplo se crea un lote de migración denominado "StagedBatch1" y se utiliza el extremo de migración que se creó en el paso anterior.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

En este ejemplo se crea también un lote de migración denominado "StagedBatch1" y se utiliza el extremo de migración que se creó en el paso anterior. Dado que no se incluye el parámetro  _AutoStart_, el lote de migración debe iniciarse manualmente en el panel Migración o con el cmdlet **Start-MigrationBatch**. Como se especificó anteriormente, solo puede existir un lote de migración total cada vez.
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a>Compruebe que ha funcionado

Ejecute el siguiente comando en Exchange Online PowerShell para visualizar la información sobre "StagedBatch1":
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

También puede comprobar que el lote se ha iniciado ejecutando el comando siguiente:
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

Para obtener más información sobre el cmdlet **Get-MigrationBatch**, consulte[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a>Paso 5: Convertir los buzones locales en usuarios habilitados para correo electrónico
<a name="BK_Endpoint"> </a>

Una vez que haya migrado correctamente un lote de buzones de correo, necesitará una forma de que los usuarios puedan acceder a su correo. Un usuario cuyo buzón de correo se ha migrado ahora tiene un buzón local y otro en Microsoft 365. Los usuarios que tienen un buzón en Microsoft 365 dejarán de recibir correo nuevo en su buzón local. 
  
Como no ha terminado con las migraciones, todavía no está listo para dirigir a todos los usuarios a Microsoft 365 por su correo electrónico. ¿Qué puede hacer para las personas que tienen ambos? Lo que puede hacer es cambiar los buzones locales que ya ha migrado a los usuarios habilitados para correo. Al cambiar de un buzón a un usuario habilitado para correo, puede dirigir al usuario a Microsoft 365 por su correo electrónico en lugar de ir a su buzón local. 
  
Otra razón importante para convertir los buzones locales en usuarios habilitados para correo electrónico es conservar las direcciones proxy de los buzones de Microsoft 365 copiando las direcciones proxy a los usuarios habilitados para correo. Esto le permite administrar los usuarios basados en la nube desde la organización local mediante Active Directory. Además, si decide retirar su organización local de Exchange Server una vez que todos los buzones se han migrado a Microsoft 365, las direcciones proxy que ha copiado a los usuarios habilitados para correo permanecerán en su Active Directory local.
    
### <a name="step-6-delete-a-staged-migration-batch"></a>Paso 6: Eliminar un lote de migración preconfigurada
<a name="BK_Endpoint"> </a>

 Cuando haya migrado correctamente todos los buzones de un lote de migración y haya convertido los buzones locales del lote en usuarios habilitados para correo, ya estará listo para eliminar un lote de migración preconfigurada. Asegúrese de comprobar que el correo se reenvía a los buzones de correo de Microsoft 365 en el lote de migración. Cuando elimina un lote de migración preconfigurada, el servicio de migración limpia todos los registros relacionados con el lote de migración y elimina dicho lote.
  
Para eliminar el lote de migración "StagedBatch1" en Exchange Online PowerShell, ejecute el comando siguiente.
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

Para obtener más información sobre el cmdlet **Remove-MigrationBatch**, consulte[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).
  
#### <a name="verify-it-worked"></a>Compruebe que ha funcionado

Ejecute el comando siguiente en Exchange Online PowerShell para visualizar la información sobre "IMAPBatch1":
  
```powershell
Get-MigrationBatch StagedBatch1
```

El comando devolverá el lote de migración con un estado **Quitando** o devolverá un error indicando que el lote de migración no se ha encontrado, lo que demuestra que el lote se ha eliminado.
  
Para obtener más información sobre el cmdlet **Get-MigrationBatch**, consulte[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
### <a name="step7-assign-licenses-to-microsoft-365-users"></a>STEP7: asignar licencias a usuarios de Microsoft 365
<a name="BK_Endpoint"> </a>

Active las cuentas de usuario 365 de Microsoft para las cuentas migradas asignando licencias. Si no asigna una licencia, el buzón se deshabilitará cuando finalice el periodo de gracia (30 días). Para asignar una licencia en el centro de administración de Microsoft 365, consulte [asignar o cancelar la asignación de licencias](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).
  
### <a name="step-8-complete-post-migration-tasks"></a>Paso 8: Finalizar las tareas posteriores a la migración
<a name="BK_Postmigration"> </a>

- **Cree un registro DNS de Detección automática para que los usuarios puedan acceder fácilmente a sus buzones.** Después de migrar todos los buzones locales a Microsoft 365, puede configurar un registro de detección automática de DNS para su organización de Microsoft 365 para permitir que los usuarios se conecten fácilmente a sus nuevos buzones de Microsoft 365 con Outlook y clientes móviles. Este nuevo registro DNS de detección automática tiene que usar el mismo espacio de nombres que está usando para la organización de Microsoft 365. Por ejemplo, si el espacio de nombres basado en la nube es cloud.contoso.com, el registro DNS de Detección automática que se debe crear es autodiscover.cloud.contoso.com.
    
    Microsoft 365 usa un registro CNAME para implementar el servicio de detección automática para Outlook y clientes móviles. El registro CNAME de Detección automática debe contener la información siguiente:
    
  - **Alias:** autodiscover
    
  - **Destino:** autodiscover.outlook.com
    
    Para obtener más información, vea [agregar registros DNS para conectar su dominio](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Retire los servidores de Exchange locales.** Después de comprobar que todo el correo electrónico se enruta directamente a los buzones de Microsoft 365 y que ya no necesita mantener su organización de correo electrónico local ni tener previsto implementar una solución de SSO, puede desinstalar Exchange de sus servidores y quitar su organización de Exchange local.
    
    Para obtener más información, vea los artículos siguientes:
    
  - [Modificar o quitar Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Cómo quitar una organización de Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Cómo desinstalar Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

