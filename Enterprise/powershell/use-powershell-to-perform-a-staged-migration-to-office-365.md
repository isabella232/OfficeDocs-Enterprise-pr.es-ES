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
# <a name="use-powershell-to-perform-a-staged-migration-to-microsoft-365"></a><span data-ttu-id="b39db-103">Usar PowerShell para realizar una migración preconfigurada a Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="b39db-103">Use PowerShell to perform a staged migration to Microsoft 365</span></span>

<span data-ttu-id="b39db-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="b39db-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="b39db-105">Puede migrar el contenido de los buzones de los usuarios desde un sistema de correo electrónico de origen a Microsoft 365 con el tiempo mediante una migración preconfigurada.</span><span class="sxs-lookup"><span data-stu-id="b39db-105">You can migrate the contents of user mailboxes from a source email system to Microsoft 365 over time using a staged migration.</span></span>
  
<span data-ttu-id="b39db-p101">Este artículo le guiará a través de las tareas relacionadas con una migración preconfigurada de correo electrónico con Exchange Online PowerShell. El tema, [lo que debe saber sobre una migración preconfigurada de correo electrónico](https://go.microsoft.com/fwlink/p/?LinkId=536487), le ofrece información general sobre el proceso de migración. Cuando se sienta cómodo con el contenido de ese artículo, use este uno para empezar a migrar buzones de un sistema de correo electrónico a otro.</span><span class="sxs-lookup"><span data-stu-id="b39db-p101">This article walks you through the tasks involved with for a staged email migration using Exchange Online PowerShell. The topic, [What you need to know about a staged email migration](https://go.microsoft.com/fwlink/p/?LinkId=536487), gives you an overview of the migration process. When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b39db-p102">También puede usar el centro de administración de Exchange para realizar una migración preconfigurada. Consulte [realizar una migración preconfigurada de correo electrónico a Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span><span class="sxs-lookup"><span data-stu-id="b39db-p102">You can also use the Exchange admin center to perform staged migration. See [Perform a staged migration of email to Microsoft 365](https://go.microsoft.com/fwlink/p/?LinkId=536687).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="b39db-111">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="b39db-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="b39db-p103">Tiempo estimado para finalizar esta tarea: 2-5 minutos para crear un lote de migración. Una vez iniciado el lote de migración, la duración de la migración variará en función del número de buzones de correo del lote, el tamaño de cada buzón y la capacidad de red disponible. Para obtener información acerca de otros factores que influyen en el tiempo necesario para migrar buzones a Microsoft 365, consulte [Migration performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="b39db-p103">Estimated time to complete this task: 2-5 minutes to create a migration batch. After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity. For information about other factors that affect how long it takes to migrate mailboxes to Microsoft 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="b39db-p104">Deberá tener permisos asignados para poder llevar a cabo estos procedimientos. Para ver qué permisos necesita, consulte la sección "Movimiento de buzón y permisos de migración" en el tema [Permisos de destinatarios](https://go.microsoft.com/fwlink/p/?LinkId=534105).</span><span class="sxs-lookup"><span data-stu-id="b39db-p104">You need to be assigned permissions before you can perform this procedure or procedures. To see what permissions you need, see the "Migration" entry in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="b39db-p105">Para usar los cmdlets de Exchange Online PowerShell, deberá iniciar sesión e importar los cmdlets en la sesión local de Windows PowerShell. Consulte [Conectarse a Exchange Online mediante PowerShell remoto](https://go.microsoft.com/fwlink/p/?LinkId=534121) para obtener instrucciones.</span><span class="sxs-lookup"><span data-stu-id="b39db-p105">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session. See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="b39db-119">Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="b39db-119">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="b39db-120">Pasos de la migración</span><span class="sxs-lookup"><span data-stu-id="b39db-120">Migration steps</span></span>

### <a name="step-1-prepare-for-a-staged-migration"></a><span data-ttu-id="b39db-121">Paso 1: Prepararse para una migración preconfigurada</span><span class="sxs-lookup"><span data-stu-id="b39db-121">Step 1: Prepare for a staged migration</span></span>

<span data-ttu-id="b39db-122">Antes de migrar los buzones a Microsoft 365 mediante una migración preconfigurada, hay algunos cambios que debe realizar en su entorno de Exchange.</span><span class="sxs-lookup"><span data-stu-id="b39db-122">Before you migrate mailboxes to Microsoft 365 by using a staged migration, there are a few changes you must make to your Exchange environment.</span></span>
  
 <span data-ttu-id="b39db-p106">**Configure Outlook en cualquier lugar en su Exchange Server** local El servicio de migración de correo electrónico utiliza Outlook en cualquier lugar (también conocido como RPC sobre HTTP) para conectarse a su Exchange Server local. Para obtener información acerca de cómo configurar Outlook en cualquier lugar para Exchange Server 2007 y Exchange 2003, consulte los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="b39db-p106">**Configure Outlook Anywhere on your on-premises Exchange Server** The email migration service uses Outlook Anywhere (also known as RPC over HTTP), to connect to your on-premises Exchange Server. For information about how to set up Outlook Anywhere for Exchange Server 2007, and Exchange 2003, see the following:</span></span>
  
- [<span data-ttu-id="b39db-125">Exchange 2007: Cómo habilitar Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="b39db-125">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
- [<span data-ttu-id="b39db-126">Cómo configurar Outlook Anywhere con Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="b39db-126">How to configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
> [!IMPORTANT]
> <span data-ttu-id="b39db-p107">Debe usar un certificado emitido por una entidad de certificación (CA) de confianza con su configuración de Outlook en cualquier lugar. Outlook en cualquier lugar no se puede configurar con un certificado autofirmado. Para obtener más información, consulte [Cómo configurar SSL para Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="b39db-p107">You must use a certificate issued by a trusted certification authority (CA) with your Outlook Anywhere configuration. Outlook Anywhere can't be configured with a self-signed certificate. For more information, see [How to configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
 <span data-ttu-id="b39db-130">**Opcional: compruebe que puede conectarse a su organización Exchange con Outlook en cualquier lugar** Pruebe con uno de los métodos siguientes para probar la configuración de su conexión.</span><span class="sxs-lookup"><span data-stu-id="b39db-130">**Optional: Verify that you can connect to your Exchange organization using Outlook Anywhere** Try one of the following methods to test your connection settings.</span></span>
  
- <span data-ttu-id="b39db-131">Use Outlook desde fuera de la red corporativa para conectarse a su buzón de correo de Exchange local.</span><span class="sxs-lookup"><span data-stu-id="b39db-131">Use Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
- <span data-ttu-id="b39db-p108">Use el [analizador de conectividad remota de Microsoft](https://https://testconnectivity.microsoft.com/) para probar la configuración de conexión. Use las pruebas de Outlook Anywhere (RPC sobre HTTP) o de Outlook Autodiscover.</span><span class="sxs-lookup"><span data-stu-id="b39db-p108">Use the [Microsoft Remote Connectivity Analyzer](https://https://testconnectivity.microsoft.com/) to test your connection settings. Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
- <span data-ttu-id="b39db-134">Ejecute los comandos siguientes en Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b39db-134">Run the following commands in Exchange Online PowerShell:</span></span>
    
  ```powershell
  $Credentials = Get-Credential
  ```

  ```powershell
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

 <span data-ttu-id="b39db-p109">**Establecer permisos** La cuenta de usuario local que se usa para conectarse a la organización de Exchange local (también denominada administrador de migración) debe disponer de los permisos necesarios para tener acceso a los buzones locales que desea migrar a Microsoft 365. Esta cuenta de usuario se usa cuando se conecta a su sistema de correo electrónico mediante la creación de un extremo de migración más adelante en este procedimiento ([paso 3: crear un extremo de migración](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span><span class="sxs-lookup"><span data-stu-id="b39db-p109">**Set permissions** The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Microsoft 365. This user account is used when you connect to your email system by creating a migration endpoint later in this procedure ([Step 3: Create a migration endpoint](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Endpoint) ).</span></span>
  
<span data-ttu-id="b39db-137">Para migrar los buzones de correo, el administrador debe tener uno de los siguientes conjuntos de permisos:</span><span class="sxs-lookup"><span data-stu-id="b39db-137">To migrate the mailboxes, the admin must have one of the following permission sets:</span></span>
  
- <span data-ttu-id="b39db-138">Forme parte del grupo de **administradores de dominio** de Active Directory de la organización local.</span><span class="sxs-lookup"><span data-stu-id="b39db-138">Be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="b39db-139">o bien</span><span class="sxs-lookup"><span data-stu-id="b39db-139">or</span></span>
    
- <span data-ttu-id="b39db-140">Reciba el permiso **FullAccess** para cada buzón local y el permiso **WriteProperty** para modificar la propiedad **TargetAddress** en las cuentas de usuario locales.</span><span class="sxs-lookup"><span data-stu-id="b39db-140">Be assigned the **FullAccess** permission for each on-premises mailbox and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
    <span data-ttu-id="b39db-141">o bien</span><span class="sxs-lookup"><span data-stu-id="b39db-141">or</span></span>
    
- <span data-ttu-id="b39db-142">Reciba el permiso **ReceiveAs** en la base de datos de buzones local en la que se almacenan los buzones de los usuarios y el permiso **WriteProperty** para modificar la propiedad **TargetAddress** en las cuentas de usuario locales.</span><span class="sxs-lookup"><span data-stu-id="b39db-142">Be assigned the **Receive As** permission on the on-premises mailbox database that stores user mailboxes and the **WriteProperty** permission to modify the **TargetAddress** property on the on-premises user accounts.</span></span>
    
<span data-ttu-id="b39db-143">Para obtener instrucciones acerca de cómo configurar estos permisos, consulte [asignar permisos para migrar buzones a Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span><span class="sxs-lookup"><span data-stu-id="b39db-143">For instructions about how to set these permissions, see [Assign permissions to migrate mailboxes to Microsoft 365](https://go.microsoft.com/fwlink/?LinkId=521656).</span></span>
  
 <span data-ttu-id="b39db-p110">**Deshabilitar mensajería unificada (UM)** Si la mensajería unificada está activada para los buzones locales que se van a migrar, desactive la mensajería unificada antes de la migración. Active la mensajería unificada para los buzones una vez completada la migración. Para obtener información sobre procedimientos, consulte[Cómo deshabilitar la mensajería unificada para un usuario](https://go.microsoft.com/fwlink/?LinkId=521891).</span><span class="sxs-lookup"><span data-stu-id="b39db-p110">**Disable Unified Messaging (UM)** If UM is turned on for the on-premises mailboxes you're migrating, turn off UM before migration. Turn on UM for the mailboxes after migration is complete. For how-to steps, see[disable unified messaging](https://go.microsoft.com/fwlink/?LinkId=521891).</span></span>
  
 <span data-ttu-id="b39db-p111">**Use la sincronización de directorios para crear nuevos usuarios en Microsoft 365.** Use la sincronización de directorios para crear todos los usuarios locales de su organización de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="b39db-p111">**Use directory synchronization to create new users in Microsoft 365.** You use directory synchronization to create all the on-premises users in your Microsoft 365 organization.</span></span>
  
<span data-ttu-id="b39db-p112">Debe autorizar a los usuarios después de crearlos. Dispone de 30 días para agregar licencias después de haber creado los usuarios. Para conocer los pasos para agregar licencias, consulte [Paso 8: Finalizar las tareas posteriores a la migración](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span><span class="sxs-lookup"><span data-stu-id="b39db-p112">You need to license the users after they're created. You have 30 days to add licenses after the users are created. For steps to add licenses, see [Step 8: Complete post-migration tasks](use-powershell-to-perform-a-staged-migration-to-office-365.md#BK_Postmigration).</span></span>
  
 <span data-ttu-id="b39db-p113">Puede usar la herramienta de sincronización de Microsoft Azure Active Directory (Azure AD) o los servicios de sincronización de Microsoft Azure AD para sincronizar y crear los usuarios locales en Microsoft 365. Después de migrar los buzones a Microsoft 365, administre las cuentas de usuario en su organización local y estén sincronizadas con la organización de Microsoft 365. Para obtener más información, consulte[integración de directorios](https://go.microsoft.com/fwlink/?LinkId=521788) .</span><span class="sxs-lookup"><span data-stu-id="b39db-p113">You can use either the Microsoft Azure Active Directory (Azure AD) Synchronization Tool or the Microsoft Azure AD Sync Services  to synchronize and create your on-premises users in Microsoft 365. After mailboxes are migrated to Microsoft 365, you manage user accounts in your on-premises organization, and they're synchronized with your Microsoft 365 organization. For more information, see[Directory Integration](https://go.microsoft.com/fwlink/?LinkId=521788) .</span></span>
  
### <a name="step-2-create-a-csv-file-for-a-staged-migration-batch"></a><span data-ttu-id="b39db-155">Paso 2: Crear un archivo CSV para un lote de migración preconfigurada</span><span class="sxs-lookup"><span data-stu-id="b39db-155">Step 2: Create a CSV file for a staged migration batch</span></span>

<span data-ttu-id="b39db-p114">Después de identificar los usuarios cuyos buzones locales desea migrar a Microsoft 365, use un archivo de valores separados por comas (CSV) para crear un lote de migración. Cada fila del archivo CSV (usada por Microsoft 365 para ejecutar la migración) contiene información sobre un buzón local.</span><span class="sxs-lookup"><span data-stu-id="b39db-p114">After you identify the users whose on-premises mailboxes you want to migrate to Microsoft 365, you use a comma separated value (CSV ) file to create a migration batch. Each row in the CSV file—used by Microsoft 365 to run the migration—contains information about an on-premises mailbox.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="b39db-p115">No existe un límite para el número de buzones que se pueden migrar a Microsoft 365 mediante una migración preconfigurada. El archivo CSV de un lote de migración puede contener un máximo de 2.000 filas. Para migrar más de 2.000 buzones de correo, cree archivos CSV adicionales y use cada archivo para crear un nuevo lote de migración.</span><span class="sxs-lookup"><span data-stu-id="b39db-p115">There isn't a limit for the number of mailboxes that you can migrate to Microsoft 365 using a staged migration. The CSV file for a migration batch can contain a maximum of 2,000 rows. To migrate more than 2,000 mailboxes, create additional CSV files and use each file to create a new migration batch.</span></span> 
  
 <span data-ttu-id="b39db-161">**Atributos admitidos**</span><span class="sxs-lookup"><span data-stu-id="b39db-161">**Supported attributes**</span></span>
  
<span data-ttu-id="b39db-p116">El archivo CSV para una migración preconfigurada es compatible con los tres atributos siguientes. Cada fila del archivo CSV corresponde a un buzón y debe contener un valor para cada uno de estos atributos.</span><span class="sxs-lookup"><span data-stu-id="b39db-p116">The CSV file for a staged migration supports the following three attributes. Each row in the CSV file corresponds to a mailbox and must contain a value for each of these attributes.</span></span>
  
|<span data-ttu-id="b39db-164">**Atributo**</span><span class="sxs-lookup"><span data-stu-id="b39db-164">**Attribute**</span></span>|<span data-ttu-id="b39db-165">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="b39db-165">**Description**</span></span>|<span data-ttu-id="b39db-166">**Obligatorio**</span><span class="sxs-lookup"><span data-stu-id="b39db-166">**Required?**</span></span>|
|:-----|:-----|:-----|
|<span data-ttu-id="b39db-167">EmailAddress</span><span class="sxs-lookup"><span data-stu-id="b39db-167">EmailAddress</span></span>  <br/> |<span data-ttu-id="b39db-168">Especifica la dirección de correo electrónico SMTP principal (por ejemplo, pilarp@contoso.com) para los buzones locales.</span><span class="sxs-lookup"><span data-stu-id="b39db-168">Specifies the primary SMTP email address, for example, pilarp@contoso.com, for on-premises mailboxes.</span></span>  <br/> <span data-ttu-id="b39db-p117">Use la dirección SMTP principal para los buzones locales y no los identificadores de usuario de Microsoft 365. Por ejemplo, si el dominio local se denomina contoso.com, pero el dominio de correo electrónico de Microsoft 365 se denomina service.contoso.com, usaría el nombre de dominio contoso.com para las direcciones de correo electrónico en el archivo CSV.</span><span class="sxs-lookup"><span data-stu-id="b39db-p117">Use the primary SMTP address for on-premises mailboxes and not user IDs from the Microsoft 365. For example, if the on-premises domain is named contoso.com but the Microsoft 365 email domain is named service.contoso.com, you would use the contoso.com domain name for email addresses in the CSV file.</span></span>  <br/> |<span data-ttu-id="b39db-171">Necesario</span><span class="sxs-lookup"><span data-stu-id="b39db-171">Required</span></span>  <br/> |
|<span data-ttu-id="b39db-172">Contraseña</span><span class="sxs-lookup"><span data-stu-id="b39db-172">Password</span></span>  <br/> |<span data-ttu-id="b39db-p118">La contraseña que se va a establecer para el nuevo buzón de correo de Microsoft 365. Las restricciones de contraseña que se aplican a la organización de Microsoft 365 también se aplican a las contraseñas incluidas en el archivo CSV.</span><span class="sxs-lookup"><span data-stu-id="b39db-p118">The password to be set for the new Microsoft 365 mailbox. Any password restrictions that are applied to your Microsoft 365 organization also apply to the passwords included in the CSV file.</span></span>  <br/> |<span data-ttu-id="b39db-175">Opcional</span><span class="sxs-lookup"><span data-stu-id="b39db-175">Optional</span></span>  <br/> |
|<span data-ttu-id="b39db-176">ForceChangePassword</span><span class="sxs-lookup"><span data-stu-id="b39db-176">ForceChangePassword</span></span>  <br/> |<span data-ttu-id="b39db-p119">Especifica si un usuario debe cambiar la contraseña la primera vez que inicia sesión en el nuevo buzón de correo de Microsoft 365. Use **true** o **false** para el valor de este parámetro.</span><span class="sxs-lookup"><span data-stu-id="b39db-p119">Specifies whether a user must change the password the first time they sign in to their new Microsoft 365 mailbox. Use **True** or **False** for the value of this parameter. </span></span><br/> <span data-ttu-id="b39db-179">> [!NOTE]> Si ha implementado una solución de inicio de sesión único (SSO) implantando los servicios de federación de Active Directory (AD FS) o superior en la organización local, debe usar **False** como valor del atributo **ForceChangePassword**.</span><span class="sxs-lookup"><span data-stu-id="b39db-179">> [!NOTE]> If you've implemented a single sign-on (SSO) solution by deploying Active Directory Federation Services (AD FS) or greater in your on-premises organization, you must use **False** for the value of the **ForceChangePassword** attribute.</span></span>          |<span data-ttu-id="b39db-180">Opcional</span><span class="sxs-lookup"><span data-stu-id="b39db-180">Optional</span></span>  <br/> |
   
 <span data-ttu-id="b39db-181">**Formato del archivo CSV**</span><span class="sxs-lookup"><span data-stu-id="b39db-181">**CSV file format**</span></span>
  
<span data-ttu-id="b39db-p120">A continuación, se muestra un ejemplo del formato del archivo CSV. En este ejemplo, se migran tres buzones locales a Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="b39db-p120">Here's an example of the format for the CSV file. In this example, three on-premises mailboxes are migrated to Microsoft 365.</span></span>
  
<span data-ttu-id="b39db-p121">En la primera fila, o fila de encabezado, del archivo CSV se enumeran los nombres de los atributos, o campos, especificados en las filas que le siguen. Los nombres de atributo se separan con una coma.</span><span class="sxs-lookup"><span data-stu-id="b39db-p121">The first row, or header row, of the CSV file lists the names of the attributes, or fields, specified in the rows that follow. Each attribute name is separated by a comma.</span></span>
  
```powershell
EmailAddress,Password,ForceChangePassword 
pilarp@contoso.com,Pa$$w0rd,False 
tobyn@contoso.com,Pa$$w0rd,False 
briant@contoso.com,Pa$$w0rd,False 
```

<span data-ttu-id="b39db-p122">Cada fila que hay bajo la fila de encabezado representa a un usuario y proporciona la información que se usará para migrar el buzón del usuario. Los valores de atributo de cada fila deben seguir el mismo orden que los nombres de atributo de la fila de encabezado.</span><span class="sxs-lookup"><span data-stu-id="b39db-p122">Each row under the header row represents one user and supplies the information that will be used to migrate the user's mailbox. The attribute values in each row must be in the same order as the attribute names in the header row.</span></span> 
  
<span data-ttu-id="b39db-p123">Use cualquier editor de texto, o bien una aplicación como Excel para crear el archivo CSV. Guarde el archivo como .csv o .txt.</span><span class="sxs-lookup"><span data-stu-id="b39db-p123">Use any text editor, or an application like Excel , to create the CSV file. Save the file as a .csv or .txt file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="b39db-p124">Si el archivo CSV contiene caracteres especiales o que no son ASCII, guárdelo con codificación UTF-8 o con otra codificación Unicode. Según la aplicación, puede resultar más fácil guardar el archivo CSV con codificación UTF-8 u otra codificación Unicode si la configuración regional del equipo coincide con el idioma utilizado en el archivo CSV.</span><span class="sxs-lookup"><span data-stu-id="b39db-p124">If the CSV file contains non-ASCII or special characters, save the CSV file with UTF-8 or other Unicode encoding. Depending on the application, saving the CSV file with UTF-8 or other Unicode encoding can be easier when the system locale of the computer matches the language used in the CSV file.</span></span> 
  
### <a name="step-3-create-a-migration-endpoint"></a><span data-ttu-id="b39db-192">Paso 3: Crear un extremo de migración</span><span class="sxs-lookup"><span data-stu-id="b39db-192">Step 3: Create a migration endpoint</span></span>
<span data-ttu-id="b39db-193"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="b39db-193"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="b39db-p125">Para migrar el correo electrónico correctamente, Microsoft 365 debe conectarse y comunicarse con el sistema de correo electrónico de origen. Para ello, Microsoft 365 usa un extremo de migración. Para crear un extremo de migración de Outlook en cualquier lugar con PowerShell, para la migración preconfigurada, primero [Conéctese a Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="b39db-p125">To migrate email successfully, Microsoft 365 needs to connect and communicate with the source email system. To do this, Microsoft 365 uses a migration endpoint. To create an Outlook Anywhere migration endpoint by using PowerShell, for staged migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="b39db-197">Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="b39db-197">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="b39db-198">Para crear un extremo de migración de Outlook en cualquier lugar denominado "StagedEndpoint" en Exchange Online PowerShell, ejecute estos comandos:</span><span class="sxs-lookup"><span data-stu-id="b39db-198">To create an Outlook Anywhere migration endpoint called "StagedEndpoint" in Exchange Online PowerShell, run the following commands:</span></span>
  
```powershell
$Credentials = Get-Credential
```

```powershell
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name StagedEndpoint -Autodiscover -EmailAddress administrator@contoso.com -Credentials $Credentials
```

<span data-ttu-id="b39db-199">Para obtener más información acerca del cmdlet **New-MigrationEndpoint**, consulte[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437)</span><span class="sxs-lookup"><span data-stu-id="b39db-199">For more information about the **New-MigrationEndpoint** cmdlet, see[New-MigrationEndpoint](https://go.microsoft.com/fwlink/p/?LinkId=536437).</span></span>
  
> [!NOTE]
> <span data-ttu-id="b39db-p126">El cmdlet **New-MigrationEndpoint** puede usarse para especificar la base de datos que debe usar el servicio con la opción **-TargetDatabase**. Si no se hace, se asigna aleatoriamente una base de datos desde el sitio de Servicios de federación de Active Directory (AD FS) 2.0 donde se encuentra el buzón de administración.</span><span class="sxs-lookup"><span data-stu-id="b39db-p126">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option. Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="b39db-202">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="b39db-202">Verify it worked</span></span>

<span data-ttu-id="b39db-203">En Exchange Online PowerShell, ejecute el siguiente comando para visualizar la información sobre el extremo de migración "StagedEndpoint":</span><span class="sxs-lookup"><span data-stu-id="b39db-203">In Exchange Online PowerShell, run the following command to display information about the "StagedEndpoint" migration endpoint:</span></span>
  
```powershell
Get-MigrationEndpoint StagedEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*
```

### <a name="step-4-create-and-start-a-stage-migration-batch"></a><span data-ttu-id="b39db-204">Paso 4: Crear e iniciar un lote de migración preconfigurada</span><span class="sxs-lookup"><span data-stu-id="b39db-204">Step 4: Create and start a stage migration batch</span></span>
<span data-ttu-id="b39db-205"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="b39db-205"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="b39db-p127">Puede utilizar el cmdlet **New-MigrationBatch** en Exchange Online PowerShell para crear un lote de migración para una migración de traslado. Puede crear un lote de migración e iniciarlo automáticamente mediante la inclusión del parámetro _AutoStart_. O bien puede crear el lote de migración y, luego, iniciarlo posteriormente de forma manual mediante el uso del cmdlet **Start-MigrationBatch**. En este ejemplo se crea un lote de migración denominado "StagedBatch1" y se utiliza el extremo de migración que se creó en el paso anterior.</span><span class="sxs-lookup"><span data-stu-id="b39db-p127">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration. You can create a migration batch and start it automatically by including the _AutoStart_ parameter. Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet. This example creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint -AutoStart
```

<span data-ttu-id="b39db-p128">En este ejemplo se crea también un lote de migración denominado "StagedBatch1" y se utiliza el extremo de migración que se creó en el paso anterior. Dado que no se incluye el parámetro  _AutoStart_, el lote de migración debe iniciarse manualmente en el panel Migración o con el cmdlet **Start-MigrationBatch**. Como se especificó anteriormente, solo puede existir un lote de migración total cada vez.</span><span class="sxs-lookup"><span data-stu-id="b39db-p128">This example also creates a migration batch called "StagedBatch1" and uses the migration endpoint that was created in the previous step. Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet. As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```powershell
New-MigrationBatch -Name StagedBatch1 -SourceEndpoint StagedEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="b39db-213">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="b39db-213">Verify it worked</span></span>

<span data-ttu-id="b39db-214">Ejecute el siguiente comando en Exchange Online PowerShell para visualizar la información sobre "StagedBatch1":</span><span class="sxs-lookup"><span data-stu-id="b39db-214">Run the following command in Exchange Online PowerShell to display information about the "StagedBatch1":</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List
```

<span data-ttu-id="b39db-215">También puede comprobar que el lote se ha iniciado ejecutando el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="b39db-215">You can also verify that the batch has started by running the following command:</span></span>
  
```powershell
Get-MigrationBatch -Identity StagedBatch1 | Format-List Status
```

<span data-ttu-id="b39db-216">Para obtener más información sobre el cmdlet **Get-MigrationBatch**, consulte[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="b39db-216">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step-5-convert-on-premises-mailboxes-to-mail-enabled-users"></a><span data-ttu-id="b39db-217">Paso 5: Convertir los buzones locales en usuarios habilitados para correo electrónico</span><span class="sxs-lookup"><span data-stu-id="b39db-217">Step 5: Convert on-premises mailboxes to mail-enabled users</span></span>
<span data-ttu-id="b39db-218"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="b39db-218"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="b39db-p129">Una vez que haya migrado correctamente un lote de buzones de correo, necesitará una forma de que los usuarios puedan acceder a su correo. Un usuario cuyo buzón de correo se ha migrado ahora tiene un buzón local y otro en Microsoft 365. Los usuarios que tienen un buzón en Microsoft 365 dejarán de recibir correo nuevo en su buzón local.</span><span class="sxs-lookup"><span data-stu-id="b39db-p129">After you have successfully migrated a batch of mailboxes, you need some way to let users get to their mail. A user whose mailbox has been migrated now has both a mailbox on-premises and one in Microsoft 365. Users who have a mailbox in Microsoft 365 will stop receiving new mail in their on-premises mailbox.</span></span> 
  
<span data-ttu-id="b39db-p130">Como no ha terminado con las migraciones, todavía no está listo para dirigir a todos los usuarios a Microsoft 365 por su correo electrónico. ¿Qué puede hacer para las personas que tienen ambos? Lo que puede hacer es cambiar los buzones locales que ya ha migrado a los usuarios habilitados para correo. Al cambiar de un buzón a un usuario habilitado para correo, puede dirigir al usuario a Microsoft 365 por su correo electrónico en lugar de ir a su buzón local.</span><span class="sxs-lookup"><span data-stu-id="b39db-p130">Because you are not done with your migrations, you are not yet ready to direct all users to Microsoft 365 for their email. So what do you do for those people who have both? What you can do is change the on-premises mailboxes that you've already migrated to mail-enabled users. When you change from a mailbox to a mail-enabled user, you can direct the user to Microsoft 365 for their email instead of going to their on-premises mailbox.</span></span> 
  
<span data-ttu-id="b39db-p131">Otra razón importante para convertir los buzones locales en usuarios habilitados para correo electrónico es conservar las direcciones proxy de los buzones de Microsoft 365 copiando las direcciones proxy a los usuarios habilitados para correo. Esto le permite administrar los usuarios basados en la nube desde la organización local mediante Active Directory. Además, si decide retirar su organización local de Exchange Server una vez que todos los buzones se han migrado a Microsoft 365, las direcciones proxy que ha copiado a los usuarios habilitados para correo permanecerán en su Active Directory local.</span><span class="sxs-lookup"><span data-stu-id="b39db-p131">Another important reason to convert on-premises mailboxes to mail-enabled users is to retain proxy addresses from the Microsoft 365 mailboxes by copying proxy addresses to the mail-enabled users. This lets you manage cloud-based users from your on-premises organization by using Active Directory. Also, if you decide to decommission your on-premises Exchange Server organization after all mailboxes are migrated to Microsoft 365, the proxy addresses you've copied to the mail-enabled users will remain in your on-premises Active Directory.</span></span>
    
### <a name="step-6-delete-a-staged-migration-batch"></a><span data-ttu-id="b39db-229">Paso 6: Eliminar un lote de migración preconfigurada</span><span class="sxs-lookup"><span data-stu-id="b39db-229">Step 6: Delete a staged migration batch</span></span>
<span data-ttu-id="b39db-230"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="b39db-230"><a name="BK_Endpoint"> </a></span></span>

 <span data-ttu-id="b39db-231">Cuando haya migrado correctamente todos los buzones de un lote de migración y haya convertido los buzones locales del lote en usuarios habilitados para correo, ya estará listo para eliminar un lote de migración preconfigurada.</span><span class="sxs-lookup"><span data-stu-id="b39db-231">After all mailboxes in a migration batch have been successfully migrated, and you've converted the on-premises mailboxes in the batch to mail-enabled users, you're ready to delete a staged migration batch.</span></span> <span data-ttu-id="b39db-232">Asegúrese de comprobar que el correo se reenvía a los buzones de correo de Microsoft 365 en el lote de migración.</span><span class="sxs-lookup"><span data-stu-id="b39db-232">Be sure to verify that mail is being forwarded to the Microsoft 365 mailboxes in the migration batch.</span></span> <span data-ttu-id="b39db-233">Cuando elimina un lote de migración preconfigurada, el servicio de migración limpia todos los registros relacionados con el lote de migración y elimina dicho lote.</span><span class="sxs-lookup"><span data-stu-id="b39db-233">When you delete a staged migration batch, the migration service cleans up any records related to the migration batch and deletes the migration batch.</span></span>
  
<span data-ttu-id="b39db-234">Para eliminar el lote de migración "StagedBatch1" en Exchange Online PowerShell, ejecute el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="b39db-234">To delete the "StagedBatch1" migration batch in Exchange Online PowerShell, run the following command.</span></span>
  
```powershell
Remove-MigrationBatch -Identity StagedBatch1
```

<span data-ttu-id="b39db-235">Para obtener más información sobre el cmdlet **Remove-MigrationBatch**, consulte[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span><span class="sxs-lookup"><span data-stu-id="b39db-235">For more information about the **Remove-MigrationBatch** cmdlet, see[Remove-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536481).</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="b39db-236">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="b39db-236">Verify it worked</span></span>

<span data-ttu-id="b39db-237">Ejecute el comando siguiente en Exchange Online PowerShell para visualizar la información sobre "IMAPBatch1":</span><span class="sxs-lookup"><span data-stu-id="b39db-237">Run the following command in Exchange Online PowerShell to display information about the "IMAPBatch1":</span></span>
  
```powershell
Get-MigrationBatch StagedBatch1
```

<span data-ttu-id="b39db-238">El comando devolverá el lote de migración con un estado **Quitando** o devolverá un error indicando que el lote de migración no se ha encontrado, lo que demuestra que el lote se ha eliminado.</span><span class="sxs-lookup"><span data-stu-id="b39db-238">The command will return either the migration batch with a status of **Removing**, or it will return an error stating that migration batch couldn't be found, verifying that the batch was deleted.</span></span>
  
<span data-ttu-id="b39db-239">Para obtener más información sobre el cmdlet **Get-MigrationBatch**, consulte[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span><span class="sxs-lookup"><span data-stu-id="b39db-239">For more information about the **Get-MigrationBatch** cmdlet, see[Get-MigrationBatch](https://go.microsoft.com/fwlink/p/?LinkId=536441).</span></span>
  
### <a name="step7-assign-licenses-to-microsoft-365-users"></a><span data-ttu-id="b39db-240">STEP7: asignar licencias a usuarios de Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="b39db-240">Step7: Assign licenses to Microsoft 365 users</span></span>
<span data-ttu-id="b39db-241"><a name="BK_Endpoint"> </a></span><span class="sxs-lookup"><span data-stu-id="b39db-241"><a name="BK_Endpoint"> </a></span></span>

<span data-ttu-id="b39db-242">Active las cuentas de usuario 365 de Microsoft para las cuentas migradas asignando licencias.</span><span class="sxs-lookup"><span data-stu-id="b39db-242">Activate Microsoft 365 user accounts for the migrated accounts by assigning licenses.</span></span> <span data-ttu-id="b39db-243">Si no asigna una licencia, el buzón se deshabilitará cuando finalice el periodo de gracia (30 días).</span><span class="sxs-lookup"><span data-stu-id="b39db-243">If you don't assign a license, the mailbox is disabled when the grace period (30 days) ends.</span></span> <span data-ttu-id="b39db-244">Para asignar una licencia en el centro de administración de Microsoft 365, consulte [asignar o cancelar la asignación de licencias](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).</span><span class="sxs-lookup"><span data-stu-id="b39db-244">To assign a license in the Microsoft 365 admin center, see [Assign or unassign licenses](https://docs.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="b39db-245">Paso 8: Finalizar las tareas posteriores a la migración</span><span class="sxs-lookup"><span data-stu-id="b39db-245">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="b39db-246"><a name="BK_Postmigration"> </a></span><span class="sxs-lookup"><span data-stu-id="b39db-246"><a name="BK_Postmigration"> </a></span></span>

- <span data-ttu-id="b39db-247">**Cree un registro DNS de Detección automática para que los usuarios puedan acceder fácilmente a sus buzones.**</span><span class="sxs-lookup"><span data-stu-id="b39db-247">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="b39db-248">Después de migrar todos los buzones locales a Microsoft 365, puede configurar un registro de detección automática de DNS para su organización de Microsoft 365 para permitir que los usuarios se conecten fácilmente a sus nuevos buzones de Microsoft 365 con Outlook y clientes móviles.</span><span class="sxs-lookup"><span data-stu-id="b39db-248">After all on-premises mailboxes are migrated to Microsoft 365, you can configure an Autodiscover DNS record for your Microsoft 365 organization to enable users to easily connect to their new Microsoft 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="b39db-249">Este nuevo registro DNS de detección automática tiene que usar el mismo espacio de nombres que está usando para la organización de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="b39db-249">This new Autodiscover DNS record has to use the same namespace that you're using for your Microsoft 365 organization.</span></span> <span data-ttu-id="b39db-250">Por ejemplo, si el espacio de nombres basado en la nube es cloud.contoso.com, el registro DNS de Detección automática que se debe crear es autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="b39db-250">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="b39db-251">Microsoft 365 usa un registro CNAME para implementar el servicio de detección automática para Outlook y clientes móviles.</span><span class="sxs-lookup"><span data-stu-id="b39db-251">Microsoft 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="b39db-252">El registro CNAME de Detección automática debe contener la información siguiente:</span><span class="sxs-lookup"><span data-stu-id="b39db-252">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="b39db-253">**Alias:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="b39db-253">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="b39db-254">**Destino:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="b39db-254">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="b39db-255">Para obtener más información, vea [agregar registros DNS para conectar su dominio](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="b39db-255">For more information, see [Add DNS records to connect your domain](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="b39db-256">**Retire los servidores de Exchange locales.**</span><span class="sxs-lookup"><span data-stu-id="b39db-256">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="b39db-257">Después de comprobar que todo el correo electrónico se enruta directamente a los buzones de Microsoft 365 y que ya no necesita mantener su organización de correo electrónico local ni tener previsto implementar una solución de SSO, puede desinstalar Exchange de sus servidores y quitar su organización de Exchange local.</span><span class="sxs-lookup"><span data-stu-id="b39db-257">After you've verified that all email is being routed directly to the Microsoft 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing an SSO solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="b39db-258">Para obtener más información, vea los artículos siguientes:</span><span class="sxs-lookup"><span data-stu-id="b39db-258">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="b39db-259">Modificar o quitar Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="b39db-259">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="b39db-260">Cómo quitar una organización de Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="b39db-260">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="b39db-261">Cómo desinstalar Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="b39db-261">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

