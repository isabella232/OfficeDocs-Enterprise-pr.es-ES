---
title: Usar PowerShell para realizar una migración de IMAP a Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: c28de4a5-1e8e-4491-9421-af066cde7cdd
description: 'Resumen: aprenda a usar Windows PowerShell para realizar una migración IMAP a Office 365.'
ms.openlocfilehash: c7b80ea444fd9e8f0324cb0bc29edf46cd1219d0
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071166"
---
# <a name="use-powershell-to-perform-an-imap-migration-to-office-365"></a><span data-ttu-id="a071b-103">Usar PowerShell para realizar una migración de IMAP a Office 365</span><span class="sxs-lookup"><span data-stu-id="a071b-103">Use PowerShell to perform an IMAP migration to Office 365</span></span>

 <span data-ttu-id="a071b-104">**Resumen:** obtenga información sobre cómo usar Windows PowerShell para realizar una migración IMAP a Office 365.</span><span class="sxs-lookup"><span data-stu-id="a071b-104">**Summary:** Learn how to use Windows PowerShell to perform an IMAP migration to Office 365.</span></span>
  
<span data-ttu-id="a071b-p101">Como parte del proceso de implementación de Office 365, puede elegir migrar el contenido de los buzones de usuario de un servicio de correo electrónico de Internet Mail Access Protocol (IMAP) a Office 365. Este artículo le guiará a través de las tareas para migrar el correo electrónico IMAP con Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a071b-p101">As part of the process of deploying Office 365, you can choose to migrate the contents of user mailboxes from an Internet Mail Access Protocol (IMAP) email service to Office 365. This article walks you through the tasks for an email IMAP migration by using Exchange Online PowerShell.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="a071b-p102">También puede usar el centro de administración de Exchange para realizar una migración IMAP. Consulte [Migrar los buzones IMAP a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span><span class="sxs-lookup"><span data-stu-id="a071b-p102">You can also use the Exchange admin center to perform an IMAP migration. See [Migrate your IMAP mailboxes to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536685).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="a071b-109">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="a071b-109">What do you need to know before you begin?</span></span>

<span data-ttu-id="a071b-p103">Tiempo estimado para finalizar esta tarea: entre 2 y 5 minutos para crear un lote de migración. Después de que haya iniciado el lote de migración, la duración de la migración variará según la cantidad de buzones del lote, el tamaño de cada buzón y la capacidad de red disponible. Para obtener información acerca de otros factores que afectan a la duración de la migración de buzones a Office 365, consulte [Rendimiento de la migración de Exchange Online y procedimientos recomendados](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="a071b-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="a071b-p104">Deberá tener permisos asignados para poder llevar a cabo estos procedimientos. Para ver qué permisos necesita, consulte la entrada "Movimiento de buzón y permisos de migración" en una tabla del tema [Permisos de destinatarios](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="a071b-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="a071b-p105">Para usar los cmdlets de Exchange Online PowerShell, deberá iniciar sesión e importar los cmdlets en la sesión local de Windows PowerShell. Consulte [Conectarse a Exchange Online mediante PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="a071b-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="a071b-117">Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="a071b-117">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="a071b-118">En las migraciones IMAP existen las restricciones siguientes:</span><span class="sxs-lookup"><span data-stu-id="a071b-118">The following restrictions apply to IMAP migrations:</span></span>
  
- <span data-ttu-id="a071b-p106">Solo es posible migrar elementos de la bandeja de entrada o de otras carpetas de correo de un usuario. No se pueden migrar los contactos, los elementos de calendario ni las tareas.</span><span class="sxs-lookup"><span data-stu-id="a071b-p106">Only items in a user's inbox or other mail folders can be migrated. You can't migrate contacts, calendar items, or tasks.</span></span>
    
- <span data-ttu-id="a071b-121">Es posible migrar un máximo de 500.000 elementos desde el buzón de un usuario.</span><span class="sxs-lookup"><span data-stu-id="a071b-121">A maximum of 500,000 items can be migrated from a user's mailbox.</span></span>
    
- <span data-ttu-id="a071b-122">El tamaño máximo de un mensaje que se puede migrar es de 35 MB.</span><span class="sxs-lookup"><span data-stu-id="a071b-122">The maximum message size that can be migrated is 35 MB.</span></span>
    
## <a name="migration-steps"></a><span data-ttu-id="a071b-123">Pasos de la migración</span><span class="sxs-lookup"><span data-stu-id="a071b-123">Migration steps</span></span>

### <a name="step-1-prepare-for-an-imap-migration"></a><span data-ttu-id="a071b-124">Paso 1: Preparar una migración IMAP</span><span class="sxs-lookup"><span data-stu-id="a071b-124">Step 1: Prepare for an IMAP migration</span></span>
<span data-ttu-id="a071b-125"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="a071b-125"></span></span>

- <span data-ttu-id="a071b-p107">**Si tiene un dominio para la organización IMAP, debe agregarlo como un dominio aceptado de la organización de Office 365.** Si desea utilizar el mismo dominio que ya posee para sus buzones de Office 365, primero debe agregarlo como un dominio aceptado para Office 365. Una vez que lo haya agregado, puede crear los usuarios en Office 365. Para obtener más información, consulte[Comprobar el dominio en Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="a071b-p107">**If you have a domain for you IMAP organization, add it as an accepted domain of your Office 365 organization.** If you want to use the same domain you already own for your Office 365 mailboxes, you first have to add it as an accepted domain to Office 365. After you have added it, you can create your users in Office 365. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="a071b-p108">**Agregue a cada usuario a Office 365 para que estos tengan un buzón de Office 365.** Para obtener instrucciones, consulte[Agregar usuarios a Office 365 para empresas](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span><span class="sxs-lookup"><span data-stu-id="a071b-p108">**Add each user to Office 365 so that they have an Office 365 mailbox.** For instructions, see[Add users to Office 365 for business](https://go.microsoft.com/fwlink/p/?LinkId=535065).</span></span>
    
- <span data-ttu-id="a071b-p109">**Obtenga el FQDN del servidor IMAP**. Debe indicar el nombre de dominio completo (FQDN) (también denominado nombre de equipo completo) del servidor IMAP desde el que migrará los datos de buzones al crear un extremo de migración IMAP. Use un cliente IMAP o el comando PING para comprobar si puede usar el FQDN para comunicarse a través de Internet con el servidor IMAP.</span><span class="sxs-lookup"><span data-stu-id="a071b-p109">**Obtain the FQDN of the IMAP server**. You need to provide the fully qualified domain name (FQDN) (also called the full computer name) of the IMAP server that you will migrate mailbox data from when you create an IMAP migration endpoint. Use an IMAP client or the PING command to verify that you can use the FQDN to communicate with the IMAP server over the Internet.</span></span>
    
- <span data-ttu-id="a071b-p110">**Configure el servidor de seguridad para permitir las conexiones IMAP**. Es posible que deba abrir puertos en el servidor de seguridad de la organización que hospeda el servidor IMAP para que el tráfico de red con origen en el centro de datos de Microsoft durante la migración pueda entrar en la organización que hospeda el servidor IMAP. Para obtener una lista de direcciones IP utilizadas por los centros de datos de Microsoft, consulte [Direcciones URL e intervalos de direcciones IP de Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span><span class="sxs-lookup"><span data-stu-id="a071b-p110">**Configure the firewall to allow IMAP connections**. You might have to open ports in the firewall of the organization that hosts the IMAP server so network traffic originating from the Microsoft datacenter during the migration is allowed to enter the organization that hosts the IMAP server. For a list of IP addresses used by Microsoft datacenters, see [Exchange Online URLs and IP Address Ranges](https://go.microsoft.com/fwlink/p/?LinkId=535066).</span></span>
    
- <span data-ttu-id="a071b-p111">**Asigne al administrador permisos de cuenta para tener acceso a los buzones de su organización IMAP**. Si utiliza credenciales de administrador en el archivo CSV, la cuenta que utilice debe tener los permisos necesarios para tener acceso a los buzones locales. Cada servidor IMAP determina los permisos necesarios para tener acceso a los buzones de usuario.</span><span class="sxs-lookup"><span data-stu-id="a071b-p111">**Assign the administrator account permissions to access mailboxes in your IMAP organization**. If you use administrator credentials in the CSV file, the account that you use must have the necessary permissions to access the on-premises mailboxes. The permissions required to access user mailboxes is determined by the particular IMAP server.</span></span> 
    
- <span data-ttu-id="a071b-p112">**Para usar los cmdlets de Exchange Online PowerShell**, deberá iniciar sesión e importar los cmdlets en la sesión local de Windows PowerShell. Consulte [Conectarse a Exchange Online mediante PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="a071b-p112">**To use the Exchange Online PowerShell cmdlets**, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
    
    <span data-ttu-id="a071b-143">Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="a071b-143">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
    
- <span data-ttu-id="a071b-p113">**Compruebe que puede conectarse a su servidor IMAP**. Ejecute el siguiente comando en Exchange Online PowerShell para probar la configuración de conexión al servidor IMAP.</span><span class="sxs-lookup"><span data-stu-id="a071b-p113">**Verify that you can connect to your IMAP server**. Run the following command in Exchange Online PowerShell to test the connection settings to your IMAP server.</span></span>
    
  ```
  Test-MigrationServerAvailability -IMAP -RemoteServer <FQDN of IMAP server> -Port <143 or 993> -Security <None, Ssl, or Tls>
  ```

    <span data-ttu-id="a071b-146">Para el valor del parámetro **Puerto**, es normal usar 143 para las conexiones no cifradas o de Seguridad de la capa de transporte (TLS) y 993 para las conexiones SSL.</span><span class="sxs-lookup"><span data-stu-id="a071b-146">For the value of the **Port** parameter, it's typical to use 143 for unencrypted or Transport Layer Security (TLS) connections and to use 993 for SSL connections.</span></span>
    
### <a name="step-2-create-a-csv-file-for-an-imap-migration-batch"></a><span data-ttu-id="a071b-147">Paso 2: Crear un archivo CSV para un lote de migración IMAP</span><span class="sxs-lookup"><span data-stu-id="a071b-147">Step 2: Create a CSV file for an IMAP migration batch</span></span>
<span data-ttu-id="a071b-148"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="a071b-148"></span></span>

<span data-ttu-id="a071b-p114">Identifique el grupo de usuarios cuyos buzones de correo quiere migrar en un lote de migración de IMAP. Cada fila del archivo CSV contiene la información necesaria para conectar a un buzón del sistema de mensajería de IMAP.</span><span class="sxs-lookup"><span data-stu-id="a071b-p114">Identify the group of users whose mailboxes you want to migrate in an IMAP migration batch. Each row in the CSV file contains information necessary to connect to a mailbox in the IMAP messaging system.</span></span>
  
<span data-ttu-id="a071b-151">Los siguientes son los atributos necesarios para cada usuario:</span><span class="sxs-lookup"><span data-stu-id="a071b-151">Here are the required attributes for each user:</span></span> 
  
- <span data-ttu-id="a071b-152">**EmailAddress** especifica el identificador de usuario del buzón de Office 365 del usuario.</span><span class="sxs-lookup"><span data-stu-id="a071b-152">**EmailAddress** specifies the user ID for the user's Office 365 mailbox.</span></span>
    
- <span data-ttu-id="a071b-153">**UserName** especifica el nombre de inicio de sesión que usará la cuenta para tener acceso al buzón en el servidor IMAP.</span><span class="sxs-lookup"><span data-stu-id="a071b-153">**UserName** specifies the logon name for the account to use to access the mailbox on the IMAP server.</span></span>
    
- <span data-ttu-id="a071b-154">**Password** especifica la contraseña de la cuenta en la columna **UserName**.</span><span class="sxs-lookup"><span data-stu-id="a071b-154">**Password** specifies the password for the account in the **UserName** column.</span></span>
    
<span data-ttu-id="a071b-p115">A continuación, se muestra un ejemplo del formato del archivo CSV. En este ejemplo, se migran tres buzones:</span><span class="sxs-lookup"><span data-stu-id="a071b-p115">Here's an example of the format for the CSV file. In this example, three mailboxes are migrated:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams,1091990
annb@contoso.edu,ann.beebe,2111991
paulc@contoso.edu,paul.cannon,3281986
```

<span data-ttu-id="a071b-157">Para el atributo **UserName**, además del nombre de usuario, puede usar las credenciales de una cuenta a la que se hayan asignado los permisos necesarios para tener acceso a los buzones en el servidor IMAP. A continuación, se enumeran algunos de los formatos específicos usados para algunos servidores IMAP:</span><span class="sxs-lookup"><span data-stu-id="a071b-157">For the **UserName** attribute, in addition to the user name, you can use the credentials of an account that has been assigned the necessary permissions to access mailboxes on the IMAP server, the following are some of the specific formats used for some of the IMAP servers:</span></span>
  
 <span data-ttu-id="a071b-158">**Microsoft Exchange:**</span><span class="sxs-lookup"><span data-stu-id="a071b-158">**Microsoft Exchange:**</span></span>
  
<span data-ttu-id="a071b-p116">Si va a migrar correo electrónico desde la implementación IMAP de Microsoft Exchange, use el formato **Domain/Admin_UserName/User_UserName** para el atributo **UserName** del archivo CSV. Supongamos que desea migrar el correo electrónico de Exchange de Terry Adams, Ann Beebe y Paul Cannon. Tiene una cuenta de administrador de correo, cuyo nombre de usuario es **mailadmin** y cuya contraseña es **P@ssw0rd**. Este es el aspecto que tendría el archivo CSV:</span><span class="sxs-lookup"><span data-stu-id="a071b-p116">If you're migrating email from the IMAP implementation for Microsoft Exchange, use the format **Domain/Admin_UserName/User_UserName** for the **UserName** attribute in the CSV file. Let's say you're migrating email from Exchange for Terry Adams, Ann Beebe, and Paul Cannon. You have a mail administrator account, where the user name is **mailadmin** and the password is **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,contoso-students/mailadmin/terry.adams,P@ssw0rd
annb@contoso.edu,contoso-students/mailadmin/ann.beebe,P@ssw0rd
paulc@contoso.edu,contoso-students/mailadmin/paul.cannon,P@ssw0rd
```

 <span data-ttu-id="a071b-163">**Dovecot:**</span><span class="sxs-lookup"><span data-stu-id="a071b-163">**Dovecot:**</span></span>
  
<span data-ttu-id="a071b-p117">En el caso de servidores IMAP compatibles con Nivel de seguridad y autenticación simples (SASL), como el servidor IMAP Dovecot, use el formato **User_UserName\*Admin_UserName**, donde el asterisco (\*) es un carácter separador que se puede configurar. Imaginemos ahora que va a migrar el correo electrónico de esos mismos usuarios desde un servidor IMAP Dovecot con las credenciales de administrador **mailadmin** y **P@ssw0rd**. Este es el aspecto que tendría el archivo CSV:</span><span class="sxs-lookup"><span data-stu-id="a071b-p117">For IMAP servers that support Simple Authentication and Security Layer (SASL), such as a Dovecot IMAP server, use the format **User_UserName\*Admin_UserName**, where the asterisk ( \* ) is a configurable separator character. Let's say you're migrating those same users' email from a Dovecot IMAP server using the administrator credentials **mailadmin** and **P@ssw0rd**. Here's what your CSV file would look like:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,terry.adams*mailadmin,P@ssw0rd
annb@contoso.edu,ann.beebe*mailadmin,P@ssw0rd
paulc@contoso.edu,paul.cannon*mailadmin,P@ssw0rd
```

 <span data-ttu-id="a071b-167">**Mirapoint:**</span><span class="sxs-lookup"><span data-stu-id="a071b-167">**Mirapoint:**</span></span>
  
<span data-ttu-id="a071b-p118">Si va a migrar el correo electrónico desde el servidor de mensajes Mirapoint, utilice el formato **#user@domain#Admin_UserName#** para las credenciales de administrador. Para migrar el correo electrónico desde Mirapoint utilizando las credenciales de administrador **mailadmin** y **P@ssw0rd**, el archivo CSV tendría este aspecto:</span><span class="sxs-lookup"><span data-stu-id="a071b-p118">If you're migrating email from Mirapoint Message Server, use the format **#user@domain#Admin_UserName#** for the administrator credentials. To migrate email from Mirapoint using the administrator credentials **mailadmin** and **P@ssw0rd**, your CSV file would look like this:</span></span>
  
```
EmailAddress,UserName,Password
terrya@contoso.edu,#terry.adams@contoso-students.edu#mailadmin#,P@ssw0rd
annb@contoso.edu,#ann.beebe@contoso-students.edu#mailadmin#,P@ssw0rd
paulc@contoso.edu,#paul.cannon@contoso-students.edu#mailadmin#,P@ssw0rd
```

 <span data-ttu-id="a071b-170">**Courier IMAP:**</span><span class="sxs-lookup"><span data-stu-id="a071b-170">**Courier IMAP:**</span></span>
  
<span data-ttu-id="a071b-p119">Algunos sistemas de correo electrónico de origen, como Courier IMAP, no admiten el uso de credenciales de administrador de buzones para migrar buzones a Office 365. En su lugar, puede configurar el sistema de correo electrónico de origen para usar carpetas compartidas virtuales. Si usa carpetas compartidas virtuales, puede usar las credenciales de administrador de buzón para tener acceso a los buzones de usuario en el sistema de correo electrónico de origen. Para obtener más información acerca de cómo configurar las carpetas compartidas virtuales para Courier IMAP, consulte [Carpetas compartidas](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span><span class="sxs-lookup"><span data-stu-id="a071b-p119">Some source email systems, such as Courier IMAP, don't support using mailbox admin credentials to migrate mailboxes to Office 365. Instead, you can set up your source email system to use virtual shared folders. By using virtual shared folders, you can use the mailbox admin credentials to access user mailboxes on the source email system. For more information about how to configure virtual shared folders for Courier IMAP, see [Shared Folders](https://go.microsoft.com/fwlink/p/?LinkId=398870).</span></span>
  
<span data-ttu-id="a071b-p120">Para migrar buzones después de configurar las carpetas compartidas virtuales en el sistema de correo electrónico de origen, debe incluir el atributo opcional **UserRoot** en el archivo de migración. Este atributo especifica la ubicación del buzón de cada usuario en la estructura de carpetas compartidas virtuales del sistema de correo electrónico de origen. Por ejemplo, la ruta de acceso al buzón de Terry es /users/terry.adams.</span><span class="sxs-lookup"><span data-stu-id="a071b-p120">To migrate mailboxes after you set up virtual shared folders on your source email system, you have to include the optional attribute **UserRoot** in the migration file. This attribute specifies the location of each user's mailbox in the virtual shared folder structure on the source email system. For example, the path to Terry's mailbox is /users/terry.adams.</span></span>
  
<span data-ttu-id="a071b-178">Este es un ejemplo de un archivo CSV que contiene el atributo **UserRoot**:</span><span class="sxs-lookup"><span data-stu-id="a071b-178">Here's an example of a CSV file that contains the **UserRoot** attribute:</span></span>
  
```
EmailAddress,UserName,Password,UserRoot
terrya@contoso.edu,mailadmin,P@ssw0rd,/users/terry.adams
annb@contoso.edu,mailadmin,P@ssw0rd,/users/ann.beebe
paulc@contoso.edu,mailadmin,P@ssw0rd,/users/paul.cannon
```

### <a name="step-3-create-an-imap-migration-endpoint"></a><span data-ttu-id="a071b-179">Paso 3: Crear un extremo de migración IMAP</span><span class="sxs-lookup"><span data-stu-id="a071b-179">Step 3: Create an IMAP migration endpoint</span></span>
<span data-ttu-id="a071b-180"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="a071b-180"></span></span>

<span data-ttu-id="a071b-p121">Para migrar el correo electrónico correctamente, Office 365 debe conectarse y comunicarse con el sistema de correo electrónico de origen. Para ello, Office 365 utiliza un extremo de migración. El extremo de migración también define el número de buzones que se migrará simultáneamente y el número de buzones que se sincronizará simultáneamente durante la sincronización incremental, que se hace una vez cada 24 horas. Para crear un extremo de migración para la migración IMAP, primero debe [Conectarse a Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="a071b-p121">To migrate email successfully, Office 365 needs to connect to and communicate with the source email system. To do this, Office 365 uses a migration endpoint. The migration endpoint also defines the number of mailboxes to migrate simultaneously and the number of mailboxes to synchronize simultaneously during incremental synchronization, which occurs once every 24 hours. To create a migration end point for IMAP migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="a071b-185">Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="a071b-185">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="a071b-186">Para crear el extremo de migración IMAP denominado "IMAPEndpoint" en Exchange Online PowerShell, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="a071b-186">To create the IMAP migration endpoint called "IMAPEndpoint" in Exchange Online PowerShell, run the following command:</span></span>
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 993 -Security Ssl

```

<span data-ttu-id="a071b-p122">También puede agregar parámetros para especificar las migraciones simultáneas, las migraciones incrementales simultáneas y el puerto que se va a usar. El siguiente comando de Exchange Online PowerShell crea un extremo de migración IMAP denominado "IMAPEndpoint" que admite 50 migraciones simultáneas y hasta 25 sincronizaciones incrementales simultáneas. También configura el extremo para que use el puerto 143 para el cifrado TLS.</span><span class="sxs-lookup"><span data-stu-id="a071b-p122">You can also add parameters to specify concurrent migrations, concurrent incremental migrations, and the port to use. The following Exchange Online PowerShell command creates an IMAP migration endpoint called "IMAPEndpoint" that supports 50 concurrent migrations and up to 25 concurrent incremental synchronizations. It also configures the endpoint to use port 143 for TLS encryption.</span></span>
  
```
New-MigrationEndpoint -IMAP -Name IMAPEndpoint -RemoteServer imap.contoso.com -Port 143 -Security Tls -MaxConcurrentMigrations
50 -MaxConcurrentIncrementalSyncs 25
```

<span data-ttu-id="a071b-190">Para obtener más información acerca del cmdlet **New-MigrationEndpoint**, consulte[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)</span><span class="sxs-lookup"><span data-stu-id="a071b-190">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="a071b-191">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="a071b-191">Verify it worked</span></span>

<span data-ttu-id="a071b-192">Ejecute el siguiente comando en Exchange Online PowerShell para visualizar la información acerca de "IMAPEndpoint":</span><span class="sxs-lookup"><span data-stu-id="a071b-192">Run the following command in Exchange Online PowerShell to display information about the "IMAPEndpoint":</span></span>
  
```
Get-MigrationEndpoint IMAPEndpoint | Format-List EndpointType,RemoteServer,Port,Security,Max*
```

### <a name="step-4-create-and-start-an-imap-migration-batch"></a><span data-ttu-id="a071b-193">Paso 4: Crear e iniciar un lote de migración IMAP</span><span class="sxs-lookup"><span data-stu-id="a071b-193">Step 4: Create and start an IMAP migration batch</span></span>
<span data-ttu-id="a071b-194"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="a071b-194"></span></span>

<span data-ttu-id="a071b-p123">Puede usar el cmdlet [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) para crear un lote de migración para una migración IMAP. Puede crear un lote de migración e iniciarlo automáticamente mediante la inclusión del parámetro _AutoStart_. Como alternativa, puede crear el lote de migración y, luego, iniciarlo posteriormente con el cmdlet [Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440).</span><span class="sxs-lookup"><span data-stu-id="a071b-p123">You can use the [New-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536439) cmdlet to create a migration batch for an IMAP migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then start it afterwards by using the[Start-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536440) cmdlet.</span></span>
  
<span data-ttu-id="a071b-198">El siguiente comando de Exchange Online PowerShell iniciará automáticamente el lote de migración denominado "IMAPBatch1" usando el extremo IMAP denominado"IMAPEndpoint":</span><span class="sxs-lookup"><span data-stu-id="a071b-198">The following Exchange Online PowerShell command will automatically start the migration batch called "IMAPBatch1" using the IMAP endpoint called "IMAPEndpoint":</span></span>
  
```
New-MigrationBatch -Name IMAPBatch1 -SourceEndpoint IMAPEndpoint -CSVData ([System.IO.File]::ReadAllBytes("C:\Users\Administrator\Desktop\IMAPmigration_1.csv")) -AutoStart
```

#### <a name="verify-it-worked"></a><span data-ttu-id="a071b-199">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="a071b-199">Verify it worked</span></span>

<span data-ttu-id="a071b-200">Ejecute el [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) para ver información acerca de la "IMAPBatch1":</span><span class="sxs-lookup"><span data-stu-id="a071b-200">Run the [Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441) cmdlet to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List
```

<span data-ttu-id="a071b-201">También puede comprobar que el lote se ha iniciado ejecutando el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="a071b-201">You can also verify that the batch has started by running the following command:</span></span>
  
```
Get-MigrationBatch -Identity IMAPBatch1 | Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="a071b-202">Paso 5: Enrutar el correo electrónico a Office 365</span><span class="sxs-lookup"><span data-stu-id="a071b-202">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="a071b-203"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="a071b-203"></span></span>

<span data-ttu-id="a071b-p124">Los sistemas de correo electrónico utilizan un registro DNS que se denomina registro MX para averiguar dónde deben entregar los mensajes de correo electrónico. Durante el proceso de migración del correo electrónico, el registro MX apuntaba al sistema de correo electrónico de origen. Ahora que la migración del correo electrónico a Office 365 ha finalizado, es el momento de que el registro MX apunte a Office 365. Eso ayuda a asegurarse de que el correo electrónico se entrega a los buzones de Office 365. Al mover el registro MX, también puede desactivar el sistema de correo electrónico antiguo cuando esté listo.</span><span class="sxs-lookup"><span data-stu-id="a071b-p124">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="a071b-p125">Para muchos proveedores de DNS, hay instrucciones específicas para [Cambiar el registro MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Si su proveedor de DNS no está incluido, o si desea obtener una idea de las instrucciones generales, se proporcionan también [Instrucciones generales del registro MX ](https://go.microsoft.com/fwlink/?LinkId=397449).</span><span class="sxs-lookup"><span data-stu-id="a071b-p125">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="a071b-p126">Los sistemas de correo electrónico de sus clientes y socios pueden tardar hasta 72 horas en reconocer el registro MX cambiado. Espere al menos 72 horas antes de continuar con la tarea siguiente: Paso 6: Eliminar el lote de migración IMAP.</span><span class="sxs-lookup"><span data-stu-id="a071b-p126">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: Step 6: Delete IMAP migration batch.</span></span> 
  
### <a name="step-6-delete-imap-migration-batch"></a><span data-ttu-id="a071b-213">Paso 6: Eliminar el lote de migración IMAP</span><span class="sxs-lookup"><span data-stu-id="a071b-213">Step 6: Delete IMAP migration batch</span></span>
<span data-ttu-id="a071b-214"><a name="BK_Step6"> </a></span><span class="sxs-lookup"><span data-stu-id="a071b-214"></span></span>

<span data-ttu-id="a071b-p127">Después de cambiar el registro MX y comprobar que todo el correo electrónico se enruta a los buzones de Office 365, notifique a los usuarios que el correo se va a Office 365. Después, puede eliminar el lote de migración IMAP. Compruebe lo siguiente antes de eliminar el lote de migración.</span><span class="sxs-lookup"><span data-stu-id="a071b-p127">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the IMAP migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="a071b-p128">Todos los usuarios utilizan buzones de Office 365. Después de haber eliminado el lote, el correo enviado a los buzones en el servidor Exchange local no se copiará a los buzones de Office 365 correspondientes.</span><span class="sxs-lookup"><span data-stu-id="a071b-p128">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="a071b-p129">Los buzones de Office 365 se han sincronizado al menos una vez después de que se les haya empezado a enviar el correo directamente. Para hacerlo, asegúrese de que el valor en el cuadro Hora de última sincronización para el lote de migración es más reciente que el momento en que el correo se ha empezado a enrutar directamente a los buzones de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a071b-p129">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="a071b-222">Para eliminar el lote de migración "IMAPBatch1" de Exchange Online PowerShell, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="a071b-222">To delete the "IMAPBatch1" migration batch from Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity IMAPBatch1
```

<span data-ttu-id="a071b-223">Para obtener más información sobre el cmdlet **Remove-MigrationBatch**, consulte[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="a071b-223">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="a071b-224">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="a071b-224">Verify it worked</span></span>

<span data-ttu-id="a071b-225">Ejecute el comando siguiente en Exchange Online PowerShell para visualizar la información sobre "IMAPBatch1":</span><span class="sxs-lookup"><span data-stu-id="a071b-225">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```
Get-MigrationBatch IMAPBatch1"
```

<span data-ttu-id="a071b-226">El comando devolverá el lote de migración con un estado **Quitando** o devolverá un error indicando que el lote de migración no se ha encontrado, lo que demuestra que el lote se ha eliminado.</span><span class="sxs-lookup"><span data-stu-id="a071b-226">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="a071b-227">Para obtener más información sobre el cmdlet **Get-MigrationBatch**, consulte[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="a071b-227">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a071b-228">Consulte también</span><span class="sxs-lookup"><span data-stu-id="a071b-228">See also</span></span>

#### 

[<span data-ttu-id="a071b-229">Solucionador de problemas de migración IMAP</span><span class="sxs-lookup"><span data-stu-id="a071b-229">IMAP Migration Troubleshooter</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=536482)

