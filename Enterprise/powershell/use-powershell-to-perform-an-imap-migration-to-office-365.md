---
title: Usar PowerShell para realizar una migración IMAP a Microsoft 365
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
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: 'Resumen: Obtenga información sobre cómo usar Windows PowerShell para realizar una migración IMAP a Microsoft 365.'
ms.openlocfilehash: fa53fd1829121bb697277805e4f07d25ec2179b9
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229776"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-microsoft-365"></a>Usar PowerShell para realizar una migración IMAP a Microsoft 365

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Como parte del proceso de implementación de Microsoft 365, puede optar por migrar el contenido de los buzones de usuario de un servicio de correo electrónico de protocolo de acceso a correo de Internet (IMAP) a Microsoft 365. Este artículo le guiará a través de las tareas de una migración de IMAP por correo electrónico mediante Exchange Online PowerShell. 
  
> [!NOTE]
> También puede usar el centro de administración de Exchange para realizar una migración IMAP. Consulte [migrar los buzones de correo IMAP](https://go.microsoft.com/fwlink/p/?LinkId=536685). 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a>¿Qué necesita saber antes de comenzar?

Tiempo estimado para finalizar esta tarea: 2-5 minutos para crear un lote de migración. Una vez iniciado el lote de migración, la duración de la migración variará en función del número de buzones de correo del lote, el tamaño de cada buzón y la capacidad de red disponible. Para obtener información acerca de otros factores que influyen en el tiempo necesario para migrar buzones a Microsoft 365, consulte [Migration performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).
  
Deberá tener permisos asignados para poder llevar a cabo estos procedimientos. Para ver qué permisos necesita, consulte la entrada "Movimiento de buzón y permisos de migración" en una tabla del tema [Permisos de destinatarios](https://go.microsoft.com/fwlink/p/?LinkId=534105).
  
Para usar los cmdlets de Exchange Online PowerShell, deberá iniciar sesión e importar los cmdlets en la sesión local de Windows PowerShell. Consulte [Conectarse a Exchange Online mediante PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obtener instrucciones.
  
Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
En las migraciones IMAP existen las restricciones siguientes:
  
- Solo es posible migrar elementos de la bandeja de entrada o de otras carpetas de correo de un usuario. No se pueden migrar los contactos, los elementos de calendario ni las tareas.
    
- Es posible migrar un máximo de 500.000 elementos desde el buzón de un usuario.
    
- El tamaño máximo de un mensaje que se puede migrar es de 35 MB.
    
## <a name="migration-steps"></a>Pasos de la migración

### <a name="step-1-prepare-for-an-imap-migration"></a>Paso 1: Preparar una migración IMAP
<a name="BK_Step1"> </a>

- **Si tiene un dominio para la organización de IMAP, agréguelo como un dominio aceptado de su organización de Microsoft 365.** Si quiere usar el mismo dominio que ya posee para sus buzones de correo de Microsoft 365, primero tiene que agregarlo como un dominio aceptado a Microsoft 365. Una vez que la haya agregado, puede crear los usuarios en Microsoft 365. Para obtener más información, consulte[comprobar el dominio](https://go.microsoft.com/fwlink/p/?LinkId=534110).
    
- **Agregue cada usuario a Microsoft 365 para que tenga un buzón de correo.** Para obtener instrucciones, consulte[Agregar usuarios a Microsoft 365 para empresas](https://go.microsoft.com/fwlink/p/?LinkId=535065).
    
- **Obtenga el FQDN del servidor IMAP**. Debe indicar el nombre de dominio completo (FQDN) (también denominado nombre de equipo completo) del servidor IMAP desde el que migrará los datos de buzones al crear un extremo de migración IMAP. Use un cliente IMAP o el comando PING para comprobar si puede usar el FQDN para comunicarse a través de Internet con el servidor IMAP.
    
- **Configure el servidor de seguridad para permitir las conexiones IMAP**. Es posible que deba abrir puertos en el servidor de seguridad de la organización que hospeda el servidor IMAP para que el tráfico de red con origen en el centro de datos de Microsoft durante la migración pueda entrar en la organización que hospeda el servidor IMAP. Para obtener una lista de direcciones IP utilizadas por los centros de datos de Microsoft, consulte [Direcciones URL e intervalos de direcciones IP de Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=535066).
    
- **Asigne al administrador permisos de cuenta para tener acceso a los buzones de su organización IMAP**. Si utiliza credenciales de administrador en el archivo CSV, la cuenta que utilice debe tener los permisos necesarios para tener acceso a los buzones locales. Cada servidor IMAP determina los permisos necesarios para tener acceso a los buzones de usuario. 
    
- **Para usar los cmdlets de Exchange Online PowerShell**, deberá iniciar sesión e importar los cmdlets en la sesión local de Windows PowerShell. Consulte [Conectarse a Exchange Online mediante PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obtener instrucciones.
    
    Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).
    
- **Compruebe que puede conectarse a su servidor IMAP**. Ejecute el siguiente comando en Exchange Online PowerShell para probar la configuración de conexión al servidor IMAP.
    
  ```powershell
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    Para el valor del parámetro **Puerto**, es normal usar 143 para las conexiones no cifradas o de Seguridad de la capa de transporte (TLS) y 993 para las conexiones SSL.
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a>Paso 2: Crear un archivo CSV para un lote de migración IMAP
<a name="BK_Step2"> </a>

Identifique el grupo de usuarios cuyos buzones de correo quiere migrar en un lote de migración de IMAP. Cada fila del archivo CSV contiene la información necesaria para conectar a un buzón del sistema de mensajería de IMAP.
  
Los siguientes son los atributos necesarios para cada usuario: 
  
- **EmailAddress** especifica el identificador de usuario del buzón de correo de Microsoft 365 del usuario.
    
- **UserName** especifica el nombre de inicio de sesión que usará la cuenta para tener acceso al buzón en el servidor IMAP.
    
- **Password** especifica la contraseña de la cuenta en la columna **UserName**.
    
A continuación, se muestra un ejemplo del formato del archivo CSV. En este ejemplo, se migran tres buzones:
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

Para el atributo **UserName**, además del nombre de usuario, puede usar las credenciales de una cuenta a la que se hayan asignado los permisos necesarios para tener acceso a los buzones en el servidor IMAP. A continuación, se enumeran algunos de los formatos específicos usados para algunos servidores IMAP:
  
 **Microsoft Exchange:**
  
Si va a migrar correo electrónico desde la implementación IMAP de Microsoft Exchange, use el formato **Domain/Admin_UserName/User_UserName** para el atributo **UserName** del archivo CSV. Supongamos que desea migrar el correo electrónico de Exchange de Terry Adams, Ann Beebe y Paul Cannon. Tiene una cuenta de administrador de correo, cuyo nombre de usuario es **mailadmin** y cuya contraseña es **P@ssw0rd**. Este es el aspecto que tendría el archivo CSV:
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 **Dovecot:**
  
En el caso de servidores IMAP compatibles con Nivel de seguridad y autenticación simples (SASL), como el servidor IMAP Dovecot, use el formato **User_UserName*Admin_UserName**, donde el asterisco (*) es un carácter separador que se puede configurar. Imaginemos ahora que va a migrar el correo electrónico de esos mismos usuarios desde un servidor IMAP Dovecot con las credenciales de administrador **mailadmin** y **P@ssw0rd**. Este es el aspecto que tendría el archivo CSV:
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 **Mirapoint:**
  
Si va a migrar el correo electrónico desde el servidor de mensajes Mirapoint, utilice el formato **#user@domain#Admin_UserName#** para las credenciales de administrador. Para migrar el correo electrónico desde Mirapoint utilizando las credenciales de administrador **mailadmin** y **P@ssw0rd**, el archivo CSV tendría este aspecto:
  
```powershell
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 **Courier IMAP:**
  
Algunos sistemas de correo electrónico de origen, como Courier IMAP, no admiten el uso de credenciales de administrador de buzones para migrar buzones a Microsoft 365. En su lugar, puede configurar su sistema de correo electrónico de origen para que use carpetas compartidas virtuales. Mediante el uso de carpetas compartidas virtuales, puede usar las credenciales de administrador del buzón para obtener acceso a los buzones de usuario en el sistema de correo electrónico de origen. Para obtener más información acerca de cómo configurar carpetas compartidas virtuales para Courier IMAP, consulte [carpetas compartidas](https://go.microsoft.com/fwlink/p/?LinkId=398870).
  
Para migrar buzones después de configurar las carpetas compartidas virtuales en el sistema de correo electrónico de origen, debe incluir el atributo opcional **UserRoot** en el archivo de migración. Este atributo especifica la ubicación del buzón de cada usuario en la estructura de carpetas compartidas virtuales del sistema de correo electrónico de origen. Por ejemplo, la ruta de acceso al buzón de Terry es /users/terry.adams.
  
Este es un ejemplo de un archivo CSV que contiene el atributo **UserRoot**:
  
```powershell
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a>Paso 3: Crear un extremo de migración IMAP
<a name="BK_Step3"> </a>

Para migrar el correo electrónico correctamente, Microsoft 365 debe conectarse y comunicarse con el sistema de correo electrónico de origen. Para ello, Microsoft 365 usa un extremo de migración. El extremo de migración también define el número de buzones que se van a migrar simultáneamente y el número de buzones que se van a sincronizar simultáneamente durante la sincronización incremental, lo que ocurre una vez cada 24 horas. Para crear un punto final de migración para la migración de IMAP, primero [Conéctese a Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121). 
  
Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).
  
Para crear el extremo de migración IMAP denominado "IMAPEndpoint" en Exchange Online PowerShell, ejecute el comando siguiente:
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

También puede agregar parámetros para especificar las migraciones simultáneas, las migraciones incrementales simultáneas y el puerto que se va a usar. El siguiente comando de Exchange Online PowerShell crea un extremo de migración IMAP denominado "IMAPEndpoint" que admite 50 migraciones simultáneas y hasta 25 sincronizaciones incrementales simultáneas. También configura el extremo para que use el puerto 143 para el cifrado TLS.
  
```powershell
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

Para obtener más información acerca del cmdlet **New-MigrationEndpoint**, consulte[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)
  
#### <a name="verify-it-worked"></a>Compruebe que ha funcionado

Ejecute el siguiente comando en Exchange Online PowerShell para visualizar la información acerca de "IMAPEndpoint":
  
```powershell
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a>Paso 4: Crear e iniciar un lote de migración IMAP
<a name="BK_Step4"> </a>

Puede usar el cmdlet [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) para crear un lote de migración para una migración IMAP. Puede crear un lote de migración e iniciarlo automáticamente mediante la inclusión del parámetro _AutoStart_. Como alternativa, puede crear el lote de migración y, luego, iniciarlo posteriormente con el cmdlet [Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440).
  
El siguiente comando de Exchange Online PowerShell iniciará automáticamente el lote de migración denominado "IMAPBatch1" usando el extremo IMAP denominado"IMAPEndpoint":
  
```powershell
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a>Compruebe que ha funcionado

Ejecute el [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) para ver información acerca de la "IMAPBatch1":
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

También puede comprobar que el lote se ha iniciado ejecutando el comando siguiente:
  
```powershell
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-microsoft-365"></a>Paso 5: enrutar el correo electrónico a Microsoft 365
<a name="BK_Step5"> </a>

Los sistemas de correo electrónico usan un registro DNS denominado registro MX para averiguar dónde entregar los correos electrónicos. Durante el proceso de migración de correo electrónico, el registro MX señalaba a su sistema de correo electrónico de origen. Ahora que se ha completado la migración de correo electrónico a Microsoft 365, es el momento de apuntar el registro MX en Microsoft 365. Esto le ayudará a asegurarse de que el correo electrónico se entregue a sus buzones de correo de Microsoft 365. Al mover el registro MX, también puede desactivar su antiguo sistema de correo electrónico cuando esté listo. 
  
Para muchos proveedores de DNS, hay instrucciones específicas para cambiar el registro MX. Si su proveedor de DNS no está incluido o si desea obtener una idea de las directrices generales, también se proporcionan [instrucciones de registro MX generales](https://go.microsoft.com/fwlink/?LinkId=397449) .
  
Los sistemas de correo electrónico de sus clientes y socios pueden tardar hasta 72 horas en reconocer el registro MX cambiado. Espere al menos 72 horas antes de continuar con la tarea siguiente: Paso 6: Eliminar el lote de migración IMAP. 
  
### <a name="step-6-delete-imap-migration-batch"></a>Paso 6: Eliminar el lote de migración IMAP
<a name="BK_Step6"> </a>

Después de cambiar el registro MX y comprobar que todo el correo se enruta a los buzones de Microsoft 365, notifique a los usuarios que su correo va a Microsoft 365. Después de esto, puede eliminar el lote de migración de IMAP. Compruebe lo siguiente antes de eliminar el lote de migración.
  
- Todos los usuarios usan buzones de correo de Microsoft 365. Una vez eliminado el lote, el correo enviado a los buzones en el servidor de Exchange local no se copia a los buzones de correo de Microsoft 365 correspondientes.
    
- Los buzones de correo de Microsoft 365 se sincronizaron al menos una vez cuando comenzó el envío directo a ellos. Para ello, asegúrese de que el valor en el último cuadro de tiempo sincronizado del lote de migración es más reciente que cuando el correo empezó a enrutarse directamente a los buzones de Microsoft 365.
    
Para eliminar el lote de migración "IMAPBatch1" de Exchange Online PowerShell, ejecute el comando siguiente:
  
```powershell
Remove-MigrationBatch -Identity IMAPBatch1
```

Para obtener más información sobre el cmdlet **Remove-MigrationBatch**, consulte[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).
  
#### <a name="verify-it-worked"></a>Compruebe que ha funcionado

Ejecute el comando siguiente en Exchange Online PowerShell para visualizar la información sobre "IMAPBatch1":
  
```powershell
Get-MigrationBatch IMAPBatch1"
```

El comando devolverá el lote de migración con un estado **Quitando** o devolverá un error indicando que el lote de migración no se ha encontrado, lo que demuestra que el lote se ha eliminado.
  
Para obtener más información sobre el cmdlet **Get-MigrationBatch**, consulte[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).
  
## <a name="see-also"></a>Consulte también

[Solucionador de problemas de migración IMAP](https://go.microsoft.com/fwlink/p/?LinkId=536482)

