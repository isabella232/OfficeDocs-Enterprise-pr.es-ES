---
title: Usar PowerShell para realizar una migración total a Microsoft 365
ms.author: sirkkuw
author: sirkkuw
manager: laurawi
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
ms.assetid: b468cb4b-a35c-43d3-85bf-65446998af40
description: 'Resumen: Obtenga información sobre cómo usar Windows PowerShell para realizar una migración total a Microsoft 365.'
ms.openlocfilehash: 203c041e0bd5fe58d697d074e94b749726bb22bf
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229856"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-microsoft-365"></a>Usar PowerShell para realizar una migración total a Microsoft 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Puede migrar el contenido de los buzones de los usuarios de un sistema de correo electrónico de origen a Microsoft 365 todos a la vez mediante una migración total. Este artículo le guiará a través de las tareas para una migración total del correo electrónico con Exchange Online PowerShell. 
  
Al revisar el tema, lo que debe [saber sobre la migración total de correo electrónico a Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), puede obtener información general sobre el proceso de migración. Cuando se sienta cómodo con el contenido de ese artículo, úselo para empezar a migrar los buzones de un sistema de correo electrónico a otro.
  
> [!NOTE]
> También puede usar el centro de administración de Exchange para realizar una migración total. Consulte [realizar una migración total de correo electrónico a Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536689). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de comenzar?

Tiempo estimado para finalizar esta tarea: entre 2 y 5 minutos para crear un lote de migración. Después de que haya iniciado el lote de migración, la duración de la migración variará según la cantidad de buzones del lote, el tamaño de cada buzón y la capacidad de red disponible. Para obtener información acerca de otros factores que influyen en el tiempo necesario para migrar buzones a Microsoft 365, consulte [Migration performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Deberá tener permisos asignados para poder llevar a cabo estos procedimientos. Para ver qué permisos necesita, consulte la entrada "Movimiento de buzón y permisos de migración" en una tabla del tema [Permisos de destinatarios](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Para usar los cmdlets de Exchange Online PowerShell, deberá iniciar sesión e importar los cmdlets en la sesión local de Windows PowerShell. Consulte [Conectarse a Exchange Online mediante PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obtener instrucciones.
  
Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
## <a name="migration-steps"></a>Pasos de la migración

### <a name="step-1-prepare-for-a-cutover-migration"></a>Paso 1: Prepararse para una migración total
<a name="BK_Step1"> </a>

- **Agregue su organización de Exchange local como un dominio aceptado de su organización de Microsoft 365.** El servicio de migración usa la dirección SMTP de sus buzones locales para crear el identificador de usuario y la dirección de correo electrónico de Microsoft Online Services para los nuevos buzones de Microsoft 365. Se producirá un error en la migración si el dominio de Exchange no es un dominio aceptado o el dominio principal de la organización de Microsoft 365. Para obtener más información, consulte [comprobar el dominio](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Configure Outlook en cualquier lugar en el servidor Exchange local.** El servicio de migración de correo electrónico utiliza RPC sobre HTTP, u Outlook en cualquier lugar, para conectarse al servidor Exchange local. Para obtener más información acerca de cómo configurar Outlook en cualquier lugar para Exchange 2010, Exchange 2007 y Exchange 2003, consulte lo siguiente:
    
  - [Exchange 2010: Habilitar Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [Exchange 2007: Cómo habilitar Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [Exchange 2003: Situaciones de implementación para RPC a través de HTTP](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [Cómo configurar Outlook Anywhere con Exchange 2003](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > La configuración de Outlook en cualquier lugar se debe realizar con un certificado emitido por una entidad de certificación (CA) de confianza. No se puede configurar con un certificado autofirmado. Para obtener más información, consulte [Cómo configurar SSL para Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875). 
  
- **Compruebe que puede conectarse a la organización de Exchange mediante Outlook en cualquier lugar.** Intente uno de estos métodos para probar la configuración de conexión:
    
  - Utilice Microsoft Outlook desde fuera de la red corporativa para conectarse a su buzón de Exchange local.
    
  - Utilice el [Analizador de conectividad remota de Microsoft Exchange](https://www.testexchangeconnectivity.com/) para probar la configuración de la conexión. Utilice Outlook en cualquier lugar (RPC sobre HTTP) o las pruebas de Detección automática de Outlook.
    
  - Ejecute los comandos siguientes en Exchange Online PowerShell.
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- **Asigne a una cuenta de usuario local los permisos necesarios para obtener acceso a los buzones de la organización de Exchange.** La cuenta de usuario local que se usa para conectarse a la organización de Exchange local (también denominada administrador de migración) debe disponer de los permisos necesarios para tener acceso a los buzones locales que desea migrar a Microsoft 365. Esta cuenta de usuario se utiliza para crear un extremo de migración para la organización local.
    
    En la lista siguiente, se muestran los privilegios administrativos necesarios para migrar buzones con una migración total. Hay tres opciones posibles.
    
  - El administrador de la migración debe ser miembro del grupo **Administradores del dominio** en Active Directory en la organización local.
    
    O bien:
    
  - El administrador de la migración debe contar con permiso de **acceso completo** para cada buzón local.
    
    O bien
    
  - El administrador de la migración debe tener el permiso **Recibir como** en la base de datos del buzón local que almacena los buzones de usuario.
    
- **Deshabilite la mensajería unificada.** Si los buzones locales que va a migrar están habilitados para la mensajería unificada, debe deshabilitarla en los buzones antes de migrarlos. A continuación, puede habilitar la mensajería unificada en los buzones una vez completada la migración.
    
- **Grupos de seguridad y delegados** El servicio de migración de correo electrónico no puede detectar si los grupos de Active Directory local son grupos de seguridad o no, por lo que no puede aprovisionar grupos migrados como grupos de seguridad en Microsoft 365. Si quiere tener grupos de seguridad en su inquilino de Microsoft 365, primero debe aprovisionar un grupo de seguridad habilitado para correo en su inquilino de Microsoft 365 antes de iniciar la migración total. Además, este método de migración solo mueve buzones, usuarios de correo, contactos de correo y grupos habilitados para correo. Si cualquier otro objeto de Active Directory, como un usuario que no se migra a Microsoft 365, está asignado como administrador o delegado en un objeto que se va a migrar, debe quitarse del objeto antes de migrar.
    
### <a name="step-2-create-a-migration-endpoint"></a>Paso 2: Crear un extremo de migración
<a name="BK_Step2"> </a>

Para migrar el correo electrónico correctamente, Microsoft 365 debe conectarse y comunicarse con el sistema de correo electrónico de origen. Para ello, Microsoft 365 usa un extremo de migración. Para crear un extremo de migración de Outlook en cualquier lugar para la migración total, primero debe [Conectarse a Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Ejecute los comandos siguientes en Exchange Online PowerShell:
  
```
$Credentials = Get-Credential
```

El ejemplo usa el cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) para obtener y probar la configuración de conexión al servidor de Exchange local y luego utiliza dicha configuración de conexión para crear el extremo de migración denominado "CutoverEndpoint".
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> El cmdlet **New-MigrationEndpoint** puede usarse para especificar la base de datos que debe usar el servicio con la opción **-TargetDatabase**. Si no se hace, se asigna aleatoriamente una base de datos desde el sitio de Servicios de federación de Active Directory (AD FS) 2.0 donde se encuentra el buzón de administración.
  
#### <a name="verify-it-worked"></a>Compruebe que ha funcionado

En Exchange Online PowerShell, ejecute el siguiente comando para visualizar la información sobre el extremo de migración "CutoverEndpoint":
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a>Paso 3: Crear el lote de migración total
<a name="BK_Step3"> </a>

Puede utilizar el cmdlet **New-MigrationBatch** en Exchange Online PowerShell para crear un lote de migración para una migración total. Puede crear un lote de migración e iniciarlo automáticamente mediante la inclusión del parámetro _AutoStart_. O bien puede crear el lote de migración y, luego, iniciarlo posteriormente de forma manual mediante el uso del cmdlet **Start-MigrationBatch**. En este ejemplo se crea un lote de migración denominado "CutoverBatch" y se utiliza el extremo de migración que se creó en el paso anterior.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

En este ejemplo se crea también un lote de migración denominado "CutoverBatch" y se utiliza el extremo de migración que se creó en el paso anterior. Dado que no se incluye el parámetro  _AutoStart_, el lote de migración debe iniciarse manualmente en el panel Migración o con el cmdlet **Start-MigrationBatch**. Como se especificó anteriormente, solo puede existir un lote de migración total cada vez.
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a>Compruebe que ha funcionado

Para comprobar que se ha creado correctamente un lote de migración para una migración total, ejecute el siguiente comando en Exchange Online PowerShell para visualizar la información sobre el nuevo lote de migración:
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a>Paso 4: Iniciar el lote de migración total
<a name="BK_Step4"> </a>

Para iniciar el lote de migración en Exchange Online PowerShell, ejecute el comando siguiente. Esto creará un lote de migración denominado "CutoverBatch".
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a>Compruebe que ha funcionado

Si un lote de migración se inicia correctamente, su estado en el panel Migración aparece como Sincronizando. Para comprobar que ha iniciado correctamente un lote de migración con Exchange Online PowerShell, ejecute el comando siguiente:
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Paso 5: enrutar el correo electrónico a Microsoft 365
<a name="BK_Step5"> </a>

Los sistemas de correo electrónico utilizan un registro DNS denominado registro MX para averiguar dónde entregar los correos electrónicos. Durante el proceso de migración del correo electrónico, el registro MX apuntaba al sistema de correo electrónico de origen. Ahora que se ha completado la migración de correo electrónico a Microsoft 365, es el momento de apuntar el registro MX en Microsoft 365. Esto le ayudará a asegurarse de que el correo electrónico se entregue a sus buzones de correo de Microsoft 365. Al mover el registro MX, también puede desactivar el sistema de correo electrónico antiguo cuando esté listo. 
  
Para muchos proveedores de DNS, hay instrucciones específicas para [Cambiar el registro MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Si su proveedor de DNS no está incluido, o si desea obtener una idea de las instrucciones generales, se proporcionan también [Instrucciones generales del registro MX ](https://go.microsoft.com/fwlink/?LinkId=397449).
  
Los sistemas de correo electrónico de sus clientes y socios pueden tardar hasta 72 horas en reconocer el registro MX cambiado. Espere al menos 72 horas antes de continuar con la tarea siguiente: [Paso 6: Eliminar el lote de migración total](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6). 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a>Paso 6: Eliminar el lote de migración total
<a name="Bk_step6"> </a>

Después de cambiar el registro MX y comprobar que todo el correo se enruta a los buzones de Microsoft 365, notifique a los usuarios que su correo va a Microsoft 365. Después, puede eliminar el lote de migración total. Compruebe lo siguiente antes de eliminar el lote de migración.
  
- Todos los usuarios usan buzones de correo de Microsoft 365. Una vez eliminado el lote, el correo enviado a los buzones en el servidor de Exchange local no se copia a los buzones de correo de Microsoft 365 correspondientes.
    
- Los buzones de correo de Microsoft 365 se sincronizaron al menos una vez cuando comenzó el envío directo a ellos. Para ello, asegúrese de que el valor en el último cuadro de tiempo sincronizado del lote de migración es más reciente que cuando el correo empezó a enrutarse directamente a los buzones de Microsoft 365.
    
Para eliminar el lote de migración "CutoverBatch" en Exchange Online PowerShell, ejecute el comando siguiente.
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a>Sección 7: Asignar licencias de usuario
<a name="BK_Step7"> </a>

 **Active las cuentas de usuario 365 de Microsoft para las cuentas migradas asignando licencias.** Si no asigna una licencia, el buzón se deshabilitará cuando finalice el periodo de gracia (30 días). Para asignar una licencia en el centro de administración de Microsoft 365, consulte [asignar o cancelar la asignación de licencias](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).
  
### <a name="step-8-complete-post-migration-tasks"></a>Paso 8: Finalizar las tareas posteriores a la migración
<a name="BK_Step8"> </a>

- **Cree un registro DNS de Detección automática para que los usuarios puedan acceder fácilmente a sus buzones.** Después de migrar todos los buzones locales a Microsoft 365, puede configurar un registro de detección automática de DNS para su organización de Microsoft 365 para permitir que los usuarios se conecten fácilmente a sus nuevos buzones de Microsoft 365 con Outlook y clientes móviles. Este nuevo registro DNS de detección automática tiene que usar el mismo espacio de nombres que está usando para la organización de Microsoft 365. Por ejemplo, si el espacio de nombres basado en la nube es cloud.contoso.com, el registro DNS de Detección automática que se debe crear es autodiscover.cloud.contoso.com.
    
    Si mantiene su servidor de Exchange, también debe asegurarse de que el registro CNAME de DNS de detección automática tenga que apuntar a Microsoft 365 en el DNS interno y externo después de la migración para que el cliente de Outlook se conecte al buzón correcto.
    
    > [!NOTE]
    >  En Exchange 2007, Exchange 2010 y Exchange 2013 también debe establecer  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` como `Null`. 
  
    Microsoft 365 usa un registro CNAME para implementar el servicio de detección automática para Outlook y clientes móviles. El registro CNAME de Detección automática debe contener la información siguiente:
    
  - **Alias:** autodiscover
    
  - **Destino:** autodiscover.outlook.com
    
    Para obtener más información, vea [agregar registros DNS para conectar su dominio](https://go.microsoft.com/fwlink/p/?LinkId=535028).
    
- **Retire los servidores de Exchange locales.** Una vez que haya comprobado que todo el correo se enruta directamente a los buzones de Microsoft 365 y que ya no necesita mantener su organización de correo electrónico local o no tiene previsto implementar una solución de inicio de sesión único (SSO), puede desinstalar Exchange de sus servidores y quitar su organización de Exchange local.
    
    Para obtener más información, vea los artículos siguientes:
    
  - [Modificar o quitar Exchange 2010](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [Cómo quitar una organización de Exchange 2007](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [Cómo desinstalar Exchange Server 2003](https://go.microsoft.com/fwlink/?LinkID=56561)
    

