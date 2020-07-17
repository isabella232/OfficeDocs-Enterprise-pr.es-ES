---
title: Usar PowerShell para realizar una migración total a Office 365
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
description: 'Resumen: aprenda a usar Windows PowerShell para realizar una migración total a Office 365.'
ms.openlocfilehash: b40c6ac53a173f700c6b931781d98d7965a2be7c
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998575"
---
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="a9555-103">Usar PowerShell para realizar una migración total a Office 365</span><span class="sxs-lookup"><span data-stu-id="a9555-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

<span data-ttu-id="a9555-p101">Puede migrar el contenido de los buzones de usuario de un sistema de correo electrónico de origen a Office 365 a la vez con una migración total. Este artículo le guiará a través de las tareas para una migración total del correo electrónico con Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9555-p101">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration. This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="a9555-p102">Al revisar el tema [Lo que debe saber sobre la migración total de correo electrónico a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), puede obtener una visión general del proceso de migración. Cuando se sienta cómodo con el contenido de ese artículo, úselo para empezar a migrar los buzones de un sistema de correo electrónico a otro.</span><span class="sxs-lookup"><span data-stu-id="a9555-p102">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="a9555-p103">También puede usar el centro de administración de Exchange para realizar una migración total. Consulte [Realizar una migración total de correo electrónico a Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span><span class="sxs-lookup"><span data-stu-id="a9555-p103">You can also use the Exchange admin center to perform a cutover migration. See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="a9555-110">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="a9555-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="a9555-p104">Tiempo estimado para finalizar esta tarea: entre 2 y 5 minutos para crear un lote de migración. Después de que haya iniciado el lote de migración, la duración de la migración variará según la cantidad de buzones del lote, el tamaño de cada buzón y la capacidad de red disponible. Para obtener información acerca de otros factores que afectan a la duración de la migración de buzones a Office 365, consulte [Rendimiento de la migración de Exchange Online y procedimientos recomendados](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="a9555-p104">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="a9555-p105">Deberá tener permisos asignados para poder llevar a cabo estos procedimientos. Para ver qué permisos necesita, consulte la entrada "Movimiento de buzón y permisos de migración" en una tabla del tema [Permisos de destinatarios](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="a9555-p105">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="a9555-p106">Para usar los cmdlets de Exchange Online PowerShell, deberá iniciar sesión e importar los cmdlets en la sesión local de Windows PowerShell. Consulte [Conectarse a Exchange Online mediante PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="a9555-p106">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="a9555-118">Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="a9555-118">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="a9555-119">Pasos de la migración</span><span class="sxs-lookup"><span data-stu-id="a9555-119">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="a9555-120">Paso 1: Prepararse para una migración total</span><span class="sxs-lookup"><span data-stu-id="a9555-120">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="a9555-121"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="a9555-121"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="a9555-p107">**Agregue la organización de Exchange local como un dominio aceptado de la organización de Office 365.** El servicio de migración utiliza la dirección SMTP de los buzones locales para crear el identificador de usuario y la dirección de correo electrónico de Microsoft Online Services para los nuevos buzones de Office 365. La migración no se realizará correctamente si el dominio de Exchange no es un dominio aceptado o el dominio principal de la organización de Office 365. Para obtener más información, consulte[Comprobar el dominio en Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="a9555-p107">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.** The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes. Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization. For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="a9555-p108">**Configure Outlook en cualquier lugar en el servidor Exchange local.** El servicio de migración de correo electrónico utiliza RPC sobre HTTP, u Outlook en cualquier lugar, para conectarse al servidor Exchange local. Para obtener más información acerca de cómo configurar Outlook en cualquier lugar para Exchange 2010, Exchange 2007 y Exchange 2003, consulte lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a9555-p108">**Configure Outlook Anywhere on your on-premises Exchange server.** The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server. For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="a9555-129">Exchange 2010: Habilitar Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="a9555-129">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="a9555-130">Exchange 2007: Cómo habilitar Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="a9555-130">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="a9555-131">Exchange 2003: Situaciones de implementación para RPC a través de HTTP</span><span class="sxs-lookup"><span data-stu-id="a9555-131">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="a9555-132">Cómo configurar Outlook Anywhere con Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="a9555-132">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="a9555-p109">La configuración de Outlook en cualquier lugar se debe realizar con un certificado emitido por una entidad de certificación (CA) de confianza. No se puede configurar con un certificado autofirmado. Para obtener más información, consulte [Cómo configurar SSL para Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="a9555-p109">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA). It can't be configured with a self-signed certificate. For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="a9555-p110">**Compruebe que puede conectarse a la organización de Exchange mediante Outlook en cualquier lugar.** Intente uno de estos métodos para probar la configuración de conexión:</span><span class="sxs-lookup"><span data-stu-id="a9555-p110">**Verify that you can connect to your Exchange organization using Outlook Anywhere.** Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="a9555-138">Utilice Microsoft Outlook desde fuera de la red corporativa para conectarse a su buzón de Exchange local.</span><span class="sxs-lookup"><span data-stu-id="a9555-138">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="a9555-p111">Utilice el [Analizador de conectividad remota de Microsoft Exchange](https://www.testexchangeconnectivity.com/) para probar la configuración de la conexión. Utilice Outlook en cualquier lugar (RPC sobre HTTP) o las pruebas de Detección automática de Outlook.</span><span class="sxs-lookup"><span data-stu-id="a9555-p111">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="a9555-141">Ejecute los comandos siguientes en Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a9555-141">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="a9555-142">**Asigne a una cuenta de usuario local los permisos necesarios para obtener acceso a los buzones de la organización de Exchange.**</span><span class="sxs-lookup"><span data-stu-id="a9555-142">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.**</span></span> <span data-ttu-id="a9555-143">La cuenta de usuario local que se usa para conectarse a la organización de Exchange local (también denominada administrador de migración) debe disponer de los permisos necesarios para tener acceso a los buzones locales que desea migrar a Office 365.</span><span class="sxs-lookup"><span data-stu-id="a9555-143">The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="a9555-144">Esta cuenta de usuario se utiliza para crear un extremo de migración para la organización local.</span><span class="sxs-lookup"><span data-stu-id="a9555-144">This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="a9555-p113">En la lista siguiente, se muestran los privilegios administrativos necesarios para migrar buzones con una migración total. Hay tres opciones posibles.</span><span class="sxs-lookup"><span data-stu-id="a9555-p113">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration. There are three possible options.</span></span>
    
  - <span data-ttu-id="a9555-147">El administrador de la migración debe ser miembro del grupo **Administradores del dominio** en Active Directory en la organización local.</span><span class="sxs-lookup"><span data-stu-id="a9555-147">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="a9555-148">O bien:</span><span class="sxs-lookup"><span data-stu-id="a9555-148">Or</span></span>
    
  - <span data-ttu-id="a9555-149">El administrador de la migración debe contar con permiso de **acceso completo** para cada buzón local.</span><span class="sxs-lookup"><span data-stu-id="a9555-149">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="a9555-150">O bien</span><span class="sxs-lookup"><span data-stu-id="a9555-150">Or</span></span>
    
  - <span data-ttu-id="a9555-151">El administrador de la migración debe tener el permiso **Recibir como** en la base de datos del buzón local que almacena los buzones de usuario.</span><span class="sxs-lookup"><span data-stu-id="a9555-151">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="a9555-p114">**Deshabilite la mensajería unificada.** Si los buzones locales que va a migrar están habilitados para la mensajería unificada, debe deshabilitarla en los buzones antes de migrarlos. A continuación, puede habilitar la mensajería unificada en los buzones una vez completada la migración.</span><span class="sxs-lookup"><span data-stu-id="a9555-p114">**Disable Unified Messaging.** If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them. You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="a9555-p115">**Grupos de seguridad y delegados** El servicio de migración de correo electrónico no puede detectar si los grupos de Active Directory locales son grupos de seguridad o no, por lo que no puede aprovisionar grupos migrados como grupos de seguridad en Office 365. Si desea tener grupos de seguridad en su inquilino de Office 365, primero debe aprovisionar un grupo de seguridad habilitado para correo vacío en su inquilino de Office 365 antes de iniciar la migración total. Además, este método de migración solo mueve buzones, usuarios de correo, contactos de correo y grupos habilitados para correo. Si otro objeto de Active Directory, como un usuario que no se migre a Office 365, se asigna como administrador o delegado de un objeto que se va a migrar, debe quitarse del objeto antes de la migración.</span><span class="sxs-lookup"><span data-stu-id="a9555-p115">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365. If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration. Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups. If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="a9555-159">Paso 2: Crear un extremo de migración</span><span class="sxs-lookup"><span data-stu-id="a9555-159">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="a9555-160"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="a9555-160"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="a9555-p116">Para migrar el correo electrónico correctamente, Office 365 debe conectarse y comunicarse con el sistema de correo electrónico de origen. Para ello, Office 365 usa un extremo de migración. Para crear un extremo de migración de Outlook en cualquier lugar para la migración total, primero debe [Conectarse a Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="a9555-p116">To migrate email successfully, Office 365 needs to connect and communicate with the source email system. To do this, Office 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="a9555-164">Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="a9555-164">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="a9555-165">Ejecute los comandos siguientes en Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="a9555-165">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="a9555-166">El ejemplo usa el cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) para obtener y probar la configuración de conexión al servidor de Exchange local y luego utiliza dicha configuración de conexión para crear el extremo de migración denominado "CutoverEndpoint".</span><span class="sxs-lookup"><span data-stu-id="a9555-166">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="a9555-p117">El cmdlet **New-MigrationEndpoint** puede usarse para especificar la base de datos que debe usar el servicio con la opción **-TargetDatabase**. Si no se hace, se asigna aleatoriamente una base de datos desde el sitio de Servicios de federación de Active Directory (AD FS) 2.0 donde se encuentra el buzón de administración.</span><span class="sxs-lookup"><span data-stu-id="a9555-p117">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="a9555-169">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="a9555-169">Verify it worked</span></span>

<span data-ttu-id="a9555-170">En Exchange Online PowerShell, ejecute el siguiente comando para visualizar la información sobre el extremo de migración "CutoverEndpoint":</span><span class="sxs-lookup"><span data-stu-id="a9555-170">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="a9555-171">Paso 3: Crear el lote de migración total</span><span class="sxs-lookup"><span data-stu-id="a9555-171">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="a9555-172"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="a9555-172"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="a9555-p118">Puede utilizar el cmdlet **New-MigrationBatch** en Exchange Online PowerShell para crear un lote de migración para una migración total. Puede crear un lote de migración e iniciarlo automáticamente mediante la inclusión del parámetro _AutoStart_. O bien puede crear el lote de migración y, luego, iniciarlo posteriormente de forma manual mediante el uso del cmdlet **Start-MigrationBatch**. En este ejemplo se crea un lote de migración denominado "CutoverBatch" y se utiliza el extremo de migración que se creó en el paso anterior.</span><span class="sxs-lookup"><span data-stu-id="a9555-p118">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="a9555-p119">En este ejemplo se crea también un lote de migración denominado "CutoverBatch" y se utiliza el extremo de migración que se creó en el paso anterior. Dado que no se incluye el parámetro  _AutoStart_, el lote de migración debe iniciarse manualmente en el panel Migración o con el cmdlet **Start-MigrationBatch**. Como se especificó anteriormente, solo puede existir un lote de migración total cada vez.</span><span class="sxs-lookup"><span data-stu-id="a9555-p119">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="a9555-180">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="a9555-180">Verify it worked</span></span>

<span data-ttu-id="a9555-181">Para comprobar que se ha creado correctamente un lote de migración para una migración total, ejecute el siguiente comando en Exchange Online PowerShell para visualizar la información sobre el nuevo lote de migración:</span><span class="sxs-lookup"><span data-stu-id="a9555-181">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="a9555-182">Paso 4: Iniciar el lote de migración total</span><span class="sxs-lookup"><span data-stu-id="a9555-182">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="a9555-183"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="a9555-183"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="a9555-p120">Para iniciar el lote de migración en Exchange Online PowerShell, ejecute el comando siguiente. Esto creará un lote de migración denominado "CutoverBatch".</span><span class="sxs-lookup"><span data-stu-id="a9555-p120">To start the migration batch in Exchange Online PowerShell, run the following command. This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="a9555-186">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="a9555-186">Verify it worked</span></span>

<span data-ttu-id="a9555-p121">Si un lote de migración se inicia correctamente, su estado en el panel Migración aparece como Sincronizando. Para comprobar que ha iniciado correctamente un lote de migración con Exchange Online PowerShell, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="a9555-p121">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing. To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="a9555-189">Paso 5: Enrutar el correo electrónico a Office 365</span><span class="sxs-lookup"><span data-stu-id="a9555-189">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="a9555-190"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="a9555-190"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="a9555-p122">Los sistemas de correo electrónico utilizan un registro DNS que se denomina registro MX para averiguar dónde deben entregar los mensajes de correo electrónico. Durante el proceso de migración del correo electrónico, el registro MX apuntaba al sistema de correo electrónico de origen. Ahora que la migración del correo electrónico a Office 365 ha finalizado, es el momento de que el registro MX apunte a Office 365. Eso ayuda a asegurarse de que el correo electrónico se entrega a los buzones de Office 365. Al mover el registro MX, también puede desactivar el sistema de correo electrónico antiguo cuando esté listo.</span><span class="sxs-lookup"><span data-stu-id="a9555-p122">Email systems use a DNS record called an MX record to figure out where to deliver emails. During the email migration process, your MX record was pointing to your source email system. Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365. This helps make sure that email is delivered to your Office 365 mailboxes. By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="a9555-p123">Para muchos proveedores de DNS, hay instrucciones específicas para [Cambiar el registro MX](https://go.microsoft.com/fwlink/p/?LinkId=279163). Si su proveedor de DNS no está incluido, o si desea obtener una idea de las instrucciones generales, se proporcionan también [Instrucciones generales del registro MX ](https://go.microsoft.com/fwlink/?LinkId=397449).</span><span class="sxs-lookup"><span data-stu-id="a9555-p123">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163). If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="a9555-p124">Los sistemas de correo electrónico de sus clientes y socios pueden tardar hasta 72 horas en reconocer el registro MX cambiado. Espere al menos 72 horas antes de continuar con la tarea siguiente: [Paso 6: Eliminar el lote de migración total](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="a9555-p124">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record. Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="a9555-200">Paso 6: Eliminar el lote de migración total</span><span class="sxs-lookup"><span data-stu-id="a9555-200">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="a9555-201"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="a9555-201"><a name="Bk_step6"> </a></span></span>

<span data-ttu-id="a9555-p125">Después de cambiar el registro MX y comprobar que todo el correo electrónico se enruta a los buzones de Office 365, notifique a los usuarios que el correo se va a Office 365. Después, puede eliminar el lote de migración total. Compruebe lo siguiente antes de eliminar el lote de migración.</span><span class="sxs-lookup"><span data-stu-id="a9555-p125">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365. After this, you can delete the cutover migration batch. Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="a9555-p126">Todos los usuarios utilizan buzones de Office 365. Después de haber eliminado el lote, el correo enviado a los buzones en el servidor Exchange local no se copiará a los buzones de Office 365 correspondientes.</span><span class="sxs-lookup"><span data-stu-id="a9555-p126">All users are using Office 365 mailboxes. After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="a9555-p127">Los buzones de Office 365 se han sincronizado al menos una vez después de que se les haya empezado a enviar el correo directamente. Para hacerlo, asegúrese de que el valor en el cuadro Hora de última sincronización para el lote de migración es más reciente que el momento en que el correo se ha empezado a enrutar directamente a los buzones de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a9555-p127">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them. To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="a9555-209">Para eliminar el lote de migración "CutoverBatch" en Exchange Online PowerShell, ejecute el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="a9555-209">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="a9555-210">Sección 7: Asignar licencias de usuario</span><span class="sxs-lookup"><span data-stu-id="a9555-210">Section 7: Assign user licenses</span></span>
<span data-ttu-id="a9555-211"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="a9555-211"><a name="BK_Step7"> </a></span></span>

 <span data-ttu-id="a9555-212">**Active las cuentas de usuario de Office 365 para las cuentas migradas mediante la asignación de licencias.**</span><span class="sxs-lookup"><span data-stu-id="a9555-212">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.**</span></span> <span data-ttu-id="a9555-213">Si no asigna una licencia, el buzón se deshabilitará cuando finalice el periodo de gracia (30 días).</span><span class="sxs-lookup"><span data-stu-id="a9555-213">If you don't assign a license, the mailbox is disabled when the grace period ends (30 days).</span></span> <span data-ttu-id="a9555-214">Para asignar una licencia en el centro de administración de 365 de Microsoft, vea[asignar o cancelar la asignación de licencias para Office 365 para empresas](https://go.microsoft.com/fwlink/?LinkId=536681).</span><span class="sxs-lookup"><span data-stu-id="a9555-214">To assign a license in the Microsoft 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="a9555-215">Paso 8: Finalizar las tareas posteriores a la migración</span><span class="sxs-lookup"><span data-stu-id="a9555-215">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="a9555-216"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="a9555-216"><a name="BK_Step8"> </a></span></span>

- <span data-ttu-id="a9555-p129">**Cree un registro DNS de Detección automática para que los usuarios puedan acceder fácilmente a sus buzones.** Después de haber migrado todos los correos locales a Office 365, puede configurar un registro DNS de Detección automática para su organización Office 365 con el fin de permitir a los usuarios conectarse fácilmente a sus nuevos buzones de Office 365 con Outlook y los clientes móviles. Este nuevo registro DNS de Detección automática debe utilizar el mismo espacio de nombres que se utiliza para la organización de Office 365. Por ejemplo, si el espacio de nombres basado en la nube es cloud.contoso.com, el registro DNS de Detección automática que se debe crear es autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="a9555-p129">**Create an Autodiscover DNS record so users can easily get to their mailboxes.** After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients. This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization. For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="a9555-221">Tras la migración, si mantiene su servidor Exchange, también debe asegurarse de que el registro DNS CNAME de Detección automática apunte a Office 365 tanto en el DNS interno como en el externo de modo que el cliente de Outlook se conecte al buzón correcto.</span><span class="sxs-lookup"><span data-stu-id="a9555-221">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="a9555-222">En Exchange 2007, Exchange 2010 y Exchange 2013 también debe establecer  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` como `Null`.</span><span class="sxs-lookup"><span data-stu-id="a9555-222">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="a9555-p130">Office 365 utiliza un registro CNAME para implementar el servicio de Detección automática para Outlook y los clientes móviles. El registro CNAME de Detección automática debe contener la información siguiente:</span><span class="sxs-lookup"><span data-stu-id="a9555-p130">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients. The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="a9555-225">**Alias:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="a9555-225">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="a9555-226">**Destino:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="a9555-226">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="a9555-227">Para obtener más información, consulte [Crear registros DNS para Office 365 al administrar los registros DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="a9555-227">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="a9555-p131">**Retire los servidores de Exchange locales.** Después de haber comprobado que todo el correo electrónico se enruta directamente a los buzones de Office 365 y cuando ya no necesite mantener la organización de correo electrónico local o no tenga pensado implementar una solución de inicio de sesión único (SSO), puede desinstalar Exchange de los servidores y quitar la organización local de Exchange.</span><span class="sxs-lookup"><span data-stu-id="a9555-p131">**Decommission on-premises Exchange servers.** After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="a9555-230">Para obtener más información, vea los artículos siguientes:</span><span class="sxs-lookup"><span data-stu-id="a9555-230">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="a9555-231">Modificar o quitar Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="a9555-231">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="a9555-232">Cómo quitar una organización de Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="a9555-232">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="a9555-233">Cómo desinstalar Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="a9555-233">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

