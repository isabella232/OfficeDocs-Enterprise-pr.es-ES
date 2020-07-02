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
# <a name="use-powershell-to-perform-a-cutover-migration-to-office-365"></a><span data-ttu-id="13161-103">Usar PowerShell para realizar una migración total a Office 365</span><span class="sxs-lookup"><span data-stu-id="13161-103">Use PowerShell to perform a cutover migration to Office 365</span></span>

<span data-ttu-id="13161-104">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="13161-104">You can migrate the contents of user mailboxes from a source email system to Office 365 all at once by using a cutover migration.</span></span> <span data-ttu-id="13161-105">This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13161-105">This article walks you through the tasks for an email cutover migration by using Exchange Online PowerShell.</span></span> 
  
<span data-ttu-id="13161-106">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process.</span><span class="sxs-lookup"><span data-stu-id="13161-106">By reviewing the topic, [What you need to know about a cutover email migration to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536688), you can get an overview of the migration process.</span></span> <span data-ttu-id="13161-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span><span class="sxs-lookup"><span data-stu-id="13161-107">When you're comfortable with the contents of that article, use this one to begin migrating mailboxes from one email system to another.</span></span>
  
> [!NOTE]
> <span data-ttu-id="13161-108">You can also use the Exchange admin center to perform a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="13161-108">You can also use the Exchange admin center to perform a cutover migration.</span></span> <span data-ttu-id="13161-109">See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span><span class="sxs-lookup"><span data-stu-id="13161-109">See [Perform a cutover migration of email to Office 365](https://go.microsoft.com/fwlink/p/?LinkId=536689).</span></span> 
  
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="13161-110">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="13161-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="13161-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span><span class="sxs-lookup"><span data-stu-id="13161-111">Estimated time to complete this task: 2-5 minutes to create a migration batch.</span></span> <span data-ttu-id="13161-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span><span class="sxs-lookup"><span data-stu-id="13161-112">After the migration batch is started, the duration of the migration will vary based on the number of mailboxes in the batch, the size of each mailbox, and your available network capacity.</span></span> <span data-ttu-id="13161-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span><span class="sxs-lookup"><span data-stu-id="13161-113">For information about other factors that affect how long it takes to migrate mailboxes to Office 365, see [Migration Performance](https://go.microsoft.com/fwlink/p/?LinkId=275079).</span></span>
  
<span data-ttu-id="13161-114">You need to be assigned permissions before you can perform this procedure or procedures.</span><span class="sxs-lookup"><span data-stu-id="13161-114">You need to be assigned permissions before you can perform this procedure or procedures.</span></span> <span data-ttu-id="13161-115">To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span><span class="sxs-lookup"><span data-stu-id="13161-115">To see what permissions you need, see the "Migration" entry in a table in the [Recipients Permissions](https://go.microsoft.com/fwlink/p/?LinkId=534105) topic.</span></span>
  
<span data-ttu-id="13161-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span><span class="sxs-lookup"><span data-stu-id="13161-116">To use the Exchange Online PowerShell cmdlets, you need to sign in and import the cmdlets into your local Windows PowerShell session.</span></span> <span data-ttu-id="13161-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span><span class="sxs-lookup"><span data-stu-id="13161-117">See [Connect to Exchange Online using remote PowerShell](https://go.microsoft.com/fwlink/p/?LinkId=534121) for instructions.</span></span>
  
<span data-ttu-id="13161-118">Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="13161-118">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
## <a name="migration-steps"></a><span data-ttu-id="13161-119">Pasos de la migración</span><span class="sxs-lookup"><span data-stu-id="13161-119">Migration steps</span></span>

### <a name="step-1-prepare-for-a-cutover-migration"></a><span data-ttu-id="13161-120">Paso 1: Prepararse para una migración total</span><span class="sxs-lookup"><span data-stu-id="13161-120">Step 1: Prepare for a cutover migration</span></span>
<span data-ttu-id="13161-121"><a name="BK_Step1"> </a></span><span class="sxs-lookup"><span data-stu-id="13161-121"><a name="BK_Step1"> </a></span></span>

- <span data-ttu-id="13161-122">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.**</span><span class="sxs-lookup"><span data-stu-id="13161-122">**Add your on-premises Exchange organization as an accepted domain of your Office 365 organization.**</span></span> <span data-ttu-id="13161-123">The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="13161-123">The migration service uses the SMTP address of your on-premises mailboxes to create the Microsoft Online Services user ID and email address for the new Office 365 mailboxes.</span></span> <span data-ttu-id="13161-124">Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="13161-124">Migration will fail if your Exchange domain isn't an accepted domain or the primary domain of your Office 365 organization.</span></span> <span data-ttu-id="13161-125">For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span><span class="sxs-lookup"><span data-stu-id="13161-125">For more information, see[Verify your domain in Office 365](https://go.microsoft.com/fwlink/p/?LinkId=534110).</span></span>
    
- <span data-ttu-id="13161-126">**Configure Outlook Anywhere on your on-premises Exchange server.**</span><span class="sxs-lookup"><span data-stu-id="13161-126">**Configure Outlook Anywhere on your on-premises Exchange server.**</span></span> <span data-ttu-id="13161-127">The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server.</span><span class="sxs-lookup"><span data-stu-id="13161-127">The email migration service uses RPC over HTTP, or Outlook Anywhere, to connect to your on-premises Exchange server.</span></span> <span data-ttu-id="13161-128">For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span><span class="sxs-lookup"><span data-stu-id="13161-128">For information about how to set up Outlook Anywhere for Exchange 2010, Exchange 2007, and Exchange 2003, see the following:</span></span>
    
  - [<span data-ttu-id="13161-129">Exchange 2010: Habilitar Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="13161-129">Exchange 2010: Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=187249)
    
  - [<span data-ttu-id="13161-130">Exchange 2007: Cómo habilitar Outlook Anywhere</span><span class="sxs-lookup"><span data-stu-id="13161-130">Exchange 2007: How to Enable Outlook Anywhere</span></span>](https://go.microsoft.com/fwlink/?LinkID=167210)
    
  - [<span data-ttu-id="13161-131">Exchange 2003: Situaciones de implementación para RPC a través de HTTP</span><span class="sxs-lookup"><span data-stu-id="13161-131">Exchange 2003: Deployment Scenarios for RPC over HTTP</span></span>](https://go.microsoft.com/fwlink/?LinkID=73657)
    
  - [<span data-ttu-id="13161-132">Cómo configurar Outlook Anywhere con Exchange 2003</span><span class="sxs-lookup"><span data-stu-id="13161-132">How to Configure Outlook Anywhere with Exchange 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=167209)
    
    > [!IMPORTANT]
    > <span data-ttu-id="13161-133">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA).</span><span class="sxs-lookup"><span data-stu-id="13161-133">Your Outlook Anywhere configuration must be configured with a certificate issued by a trusted certification authority (CA).</span></span> <span data-ttu-id="13161-134">It can't be configured with a self-signed certificate.</span><span class="sxs-lookup"><span data-stu-id="13161-134">It can't be configured with a self-signed certificate.</span></span> <span data-ttu-id="13161-135">For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span><span class="sxs-lookup"><span data-stu-id="13161-135">For more information, see [How to Configure SSL for Outlook Anywhere](https://go.microsoft.com/fwlink/?LinkID=80875).</span></span> 
  
- <span data-ttu-id="13161-136">**Verify that you can connect to your Exchange organization using Outlook Anywhere.**</span><span class="sxs-lookup"><span data-stu-id="13161-136">**Verify that you can connect to your Exchange organization using Outlook Anywhere.**</span></span> <span data-ttu-id="13161-137">Try one of these methods to test your connection settings:</span><span class="sxs-lookup"><span data-stu-id="13161-137">Try one of these methods to test your connection settings:</span></span>
    
  - <span data-ttu-id="13161-138">Utilice Microsoft Outlook desde fuera de la red corporativa para conectarse a su buzón de Exchange local.</span><span class="sxs-lookup"><span data-stu-id="13161-138">Use Microsoft Outlook from outside your corporate network to connect to your on-premises Exchange mailbox.</span></span>
    
  - <span data-ttu-id="13161-139">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings.</span><span class="sxs-lookup"><span data-stu-id="13161-139">Use the Microsoft [Exchange Remote Connectivity Analyzer](https://www.testexchangeconnectivity.com/) to test your connection settings.</span></span> <span data-ttu-id="13161-140">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span><span class="sxs-lookup"><span data-stu-id="13161-140">Use the Outlook Anywhere (RPC over HTTP) or Outlook Autodiscover tests.</span></span>
    
  - <span data-ttu-id="13161-141">Ejecute los comandos siguientes en Exchange Online PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13161-141">Run the following commands in Exchange Online PowerShell.</span></span>
    
  ```
  $Credentials = Get-Credential
  ```

  ```
  Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress <email address for on-premises administrator> -Credentials $credentials
  ```

- <span data-ttu-id="13161-142">**Asigne a una cuenta de usuario local los permisos necesarios para obtener acceso a los buzones de la organización de Exchange.**</span><span class="sxs-lookup"><span data-stu-id="13161-142">**Assign an on-premises user account the necessary permissions to access mailboxes in your Exchange organization.**</span></span> <span data-ttu-id="13161-143">La cuenta de usuario local que se usa para conectarse a la organización de Exchange local (también denominada administrador de migración) debe disponer de los permisos necesarios para tener acceso a los buzones locales que desea migrar a Office 365.</span><span class="sxs-lookup"><span data-stu-id="13161-143">The on-premises user account that you use to connect to your on-premises Exchange organization (also called the migration administrator) must have the necessary permissions to access the on-premises mailboxes that you want to migrate to Office 365.</span></span> <span data-ttu-id="13161-144">Esta cuenta de usuario se utiliza para crear un extremo de migración para la organización local.</span><span class="sxs-lookup"><span data-stu-id="13161-144">This user account is used to create a migration endpoint to your on-premises organization.</span></span>
    
    <span data-ttu-id="13161-145">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="13161-145">The following list shows the administrative privileges required to migrate mailboxes using a cutover migration.</span></span> <span data-ttu-id="13161-146">There are three possible options.</span><span class="sxs-lookup"><span data-stu-id="13161-146">There are three possible options.</span></span>
    
  - <span data-ttu-id="13161-147">El administrador de la migración debe ser miembro del grupo **Administradores del dominio** en Active Directory en la organización local.</span><span class="sxs-lookup"><span data-stu-id="13161-147">The migration administrator must be a member of the **Domain Admins** group in Active Directory in the on-premises organization.</span></span>
    
    <span data-ttu-id="13161-148">O bien:</span><span class="sxs-lookup"><span data-stu-id="13161-148">Or</span></span>
    
  - <span data-ttu-id="13161-149">El administrador de la migración debe contar con permiso de **acceso completo** para cada buzón local.</span><span class="sxs-lookup"><span data-stu-id="13161-149">The migration administrator must be assigned the **FullAccess** permission for each on-premises mailbox.</span></span>
    
    <span data-ttu-id="13161-150">O bien</span><span class="sxs-lookup"><span data-stu-id="13161-150">Or</span></span>
    
  - <span data-ttu-id="13161-151">El administrador de la migración debe tener el permiso **Recibir como** en la base de datos del buzón local que almacena los buzones de usuario.</span><span class="sxs-lookup"><span data-stu-id="13161-151">The migration administrator must be assigned the **Receive As** permission on the on-premises mailbox database that stores the user mailboxes.</span></span>
    
- <span data-ttu-id="13161-152">**Disable Unified Messaging.**</span><span class="sxs-lookup"><span data-stu-id="13161-152">**Disable Unified Messaging.**</span></span> <span data-ttu-id="13161-153">If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them.</span><span class="sxs-lookup"><span data-stu-id="13161-153">If the on-premises mailboxes you're migrating are enabled for Unified Messaging (UM), you have to disable UM on the mailboxes before you migrate them.</span></span> <span data-ttu-id="13161-154">You can then enable UM on the mailboxes after the migration is complete.</span><span class="sxs-lookup"><span data-stu-id="13161-154">You can then enable UM on the mailboxes after the migration is complete.</span></span>
    
- <span data-ttu-id="13161-155">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365.</span><span class="sxs-lookup"><span data-stu-id="13161-155">**Security Groups and Delegates** The email migration service cannot detect whether on-premises Active Directory groups are security groups or not, so it cannot provision any migrated groups as security groups in Office 365.</span></span> <span data-ttu-id="13161-156">If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration.</span><span class="sxs-lookup"><span data-stu-id="13161-156">If you want to have security groups in your Office 365 tenant, you must first provision an empty mail-enabled security group in your Office 365 tenant before starting the cutover migration.</span></span> <span data-ttu-id="13161-157">Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups.</span><span class="sxs-lookup"><span data-stu-id="13161-157">Additionally, this migration method only moves mailboxes, mail users, mail contacts, and mail-enabled groups.</span></span> <span data-ttu-id="13161-158">If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span><span class="sxs-lookup"><span data-stu-id="13161-158">If any other Active Directory object, such as user that is not migrated to Office 365, is assigned as a manager or delegate to an object being migrated, they must be removed from the object before you migrate.</span></span>
    
### <a name="step-2-create-a-migration-endpoint"></a><span data-ttu-id="13161-159">Paso 2: Crear un extremo de migración</span><span class="sxs-lookup"><span data-stu-id="13161-159">Step 2: Create a migration endpoint</span></span>
<span data-ttu-id="13161-160"><a name="BK_Step2"> </a></span><span class="sxs-lookup"><span data-stu-id="13161-160"><a name="BK_Step2"> </a></span></span>

<span data-ttu-id="13161-161">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span><span class="sxs-lookup"><span data-stu-id="13161-161">To migrate email successfully, Office 365 needs to connect and communicate with the source email system.</span></span> <span data-ttu-id="13161-162">To do this, Office 365 uses a migration endpoint.</span><span class="sxs-lookup"><span data-stu-id="13161-162">To do this, Office 365 uses a migration endpoint.</span></span> <span data-ttu-id="13161-163">To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span><span class="sxs-lookup"><span data-stu-id="13161-163">To create an Outlook Anywhere migration endpoint for cutover migration, first [connect to Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=534121).</span></span> 
  
<span data-ttu-id="13161-164">Para obtener una lista completa de los comandos de migración, consulte [Cmdlets de movimiento y migración](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span><span class="sxs-lookup"><span data-stu-id="13161-164">For a full list of migration commands, see [Move and migration cmdlets](https://go.microsoft.com/fwlink/p/?LinkId=534750).</span></span>
  
<span data-ttu-id="13161-165">Ejecute los comandos siguientes en Exchange Online PowerShell:</span><span class="sxs-lookup"><span data-stu-id="13161-165">Run the following commands in Exchange Online PowerShell:</span></span>
  
```
$Credentials = Get-Credential
```

<span data-ttu-id="13161-166">El ejemplo usa el cmdlet [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) para obtener y probar la configuración de conexión al servidor de Exchange local y luego utiliza dicha configuración de conexión para crear el extremo de migración denominado "CutoverEndpoint".</span><span class="sxs-lookup"><span data-stu-id="13161-166">The example uses the [Test-MigrationServerAvailability](https://go.microsoft.com/fwlink/p/?LinkId=534752) cmdlet to obtain and test the connection settings to the on-premises Exchange server, and then uses those connection settings to create the migration endpoint called "CutoverEndpoint".</span></span>
  
```
$TSMA = Test-MigrationServerAvailability -ExchangeOutlookAnywhere -Autodiscover -EmailAddress administrator@contoso.com -Credentials $credentials
```

```
New-MigrationEndpoint -ExchangeOutlookAnywhere -Name CutoverEndpoint -ConnectionSettings $TSMA.ConnectionSettings
```

> [!NOTE]
> <span data-ttu-id="13161-167">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span><span class="sxs-lookup"><span data-stu-id="13161-167">The **New-MigrationEndpoint** cmdlet can be used to specify a database for the service to use by using the **-TargetDatabase** option.</span></span> <span data-ttu-id="13161-168">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span><span class="sxs-lookup"><span data-stu-id="13161-168">Otherwise a database is randomly assigned from the Active Directory Federation Services (AD FS) 2.0 site where the management mailbox is located.</span></span>
  
#### <a name="verify-it-worked"></a><span data-ttu-id="13161-169">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="13161-169">Verify it worked</span></span>

<span data-ttu-id="13161-170">En Exchange Online PowerShell, ejecute el siguiente comando para visualizar la información sobre el extremo de migración "CutoverEndpoint":</span><span class="sxs-lookup"><span data-stu-id="13161-170">In Exchange Online PowerShell, run the following command to display information about the "CutoverEndpoint" migration endpoint:</span></span>
  
```
Get-MigrationEndpoint CutoverEndpoint | Format-List EndpointType,ExchangeServer,UseAutoDiscover,Max*

```

### <a name="step-3-create-the-cutover-migration-batch"></a><span data-ttu-id="13161-171">Paso 3: Crear el lote de migración total</span><span class="sxs-lookup"><span data-stu-id="13161-171">Step 3: Create the cutover migration batch</span></span>
<span data-ttu-id="13161-172"><a name="BK_Step3"> </a></span><span class="sxs-lookup"><span data-stu-id="13161-172"><a name="BK_Step3"> </a></span></span>

<span data-ttu-id="13161-173">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span><span class="sxs-lookup"><span data-stu-id="13161-173">You can use the **New-MigrationBatch** cmdlet in Exchange Online PowerShell to create a migration batch for a cutover migration.</span></span> <span data-ttu-id="13161-174">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span><span class="sxs-lookup"><span data-stu-id="13161-174">You can create a migration batch and start it automatically by including the _AutoStart_ parameter.</span></span> <span data-ttu-id="13161-175">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="13161-175">Alternatively, you can create the migration batch and then manually start it afterwards by using the **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="13161-176">This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="13161-176">This example creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint -AutoStart
```

<span data-ttu-id="13161-177">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span><span class="sxs-lookup"><span data-stu-id="13161-177">This example also creates a migration batch called "CutoverBatch" and uses the migration endpoint that was created in the previous step.</span></span> <span data-ttu-id="13161-178">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="13161-178">Because the  _AutoStart_ parameter isn't included, the migration batch has to be manually started on the migration dashboard or by using **Start-MigrationBatch** cmdlet.</span></span> <span data-ttu-id="13161-179">As previously stated, only one cutover migration batch can exist at a time.</span><span class="sxs-lookup"><span data-stu-id="13161-179">As previously stated, only one cutover migration batch can exist at a time.</span></span>
  
```
New-MigrationBatch -Name CutoverBatch -SourceEndpoint CutoverEndpoint
```

#### <a name="verify-it-worked"></a><span data-ttu-id="13161-180">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="13161-180">Verify it worked</span></span>

<span data-ttu-id="13161-181">Para comprobar que se ha creado correctamente un lote de migración para una migración total, ejecute el siguiente comando en Exchange Online PowerShell para visualizar la información sobre el nuevo lote de migración:</span><span class="sxs-lookup"><span data-stu-id="13161-181">To verify that you've successfully created a migration batch for a cutover migration, run the following command in Exchange Online PowerShell to display information about the new migration batch:</span></span>
  
```
Get-MigrationBatch | Format-List
```

### <a name="step-4-start-the-cutover-migration-batch"></a><span data-ttu-id="13161-182">Paso 4: Iniciar el lote de migración total</span><span class="sxs-lookup"><span data-stu-id="13161-182">Step 4: Start the cutover migration batch</span></span>
<span data-ttu-id="13161-183"><a name="BK_Step4"> </a></span><span class="sxs-lookup"><span data-stu-id="13161-183"><a name="BK_Step4"> </a></span></span>

<span data-ttu-id="13161-184">To start the migration batch in Exchange Online PowerShell, run the following command.</span><span class="sxs-lookup"><span data-stu-id="13161-184">To start the migration batch in Exchange Online PowerShell, run the following command.</span></span> <span data-ttu-id="13161-185">This will create a migration batch called "CutoverBatch".</span><span class="sxs-lookup"><span data-stu-id="13161-185">This will create a migration batch called "CutoverBatch".</span></span>
  
```
Start-MigrationBatch -Identity CutoverBatch
```

#### <a name="verify-it-worked"></a><span data-ttu-id="13161-186">Compruebe que ha funcionado</span><span class="sxs-lookup"><span data-stu-id="13161-186">Verify it worked</span></span>

<span data-ttu-id="13161-187">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing.</span><span class="sxs-lookup"><span data-stu-id="13161-187">If a migration batch is successfully started, its status on the migration dashboard is specified as Syncing.</span></span> <span data-ttu-id="13161-188">To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span><span class="sxs-lookup"><span data-stu-id="13161-188">To verify that you've successfully started a migration batch using Exchange Online PowerShell, run the following command:</span></span>
  
```
Get-MigrationBatch -Identity CutoverBatch |  Format-List Status
```

### <a name="step-5-route-your-email-to-office-365"></a><span data-ttu-id="13161-189">Paso 5: Enrutar el correo electrónico a Office 365</span><span class="sxs-lookup"><span data-stu-id="13161-189">Step 5: Route your email to Office 365</span></span>
<span data-ttu-id="13161-190"><a name="BK_Step5"> </a></span><span class="sxs-lookup"><span data-stu-id="13161-190"><a name="BK_Step5"> </a></span></span>

<span data-ttu-id="13161-191">Email systems use a DNS record called an MX record to figure out where to deliver emails.</span><span class="sxs-lookup"><span data-stu-id="13161-191">Email systems use a DNS record called an MX record to figure out where to deliver emails.</span></span> <span data-ttu-id="13161-192">During the email migration process, your MX record was pointing to your source email system.</span><span class="sxs-lookup"><span data-stu-id="13161-192">During the email migration process, your MX record was pointing to your source email system.</span></span> <span data-ttu-id="13161-193">Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365.</span><span class="sxs-lookup"><span data-stu-id="13161-193">Now that the email migration to Office 365 is complete, it's time to point your MX record at Office 365.</span></span> <span data-ttu-id="13161-194">This helps make sure that email is delivered to your Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="13161-194">This helps make sure that email is delivered to your Office 365 mailboxes.</span></span> <span data-ttu-id="13161-195">By moving the MX record, you can also you turn off your old email system when you're ready.</span><span class="sxs-lookup"><span data-stu-id="13161-195">By moving the MX record, you can also you turn off your old email system when you're ready.</span></span> 
  
<span data-ttu-id="13161-196">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163).</span><span class="sxs-lookup"><span data-stu-id="13161-196">For many DNS providers, there are specific instructions to [change your MX record](https://go.microsoft.com/fwlink/p/?LinkId=279163).</span></span> <span data-ttu-id="13161-197">If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span><span class="sxs-lookup"><span data-stu-id="13161-197">If your DNS provider isn't included, or if you want to get a sense of the general directions, [general MX record instructions ](https://go.microsoft.com/fwlink/?LinkId=397449) are provided as well.</span></span>
  
<span data-ttu-id="13161-198">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record.</span><span class="sxs-lookup"><span data-stu-id="13161-198">It can take up to 72 hours for the email systems of your customers and partners to recognize the changed MX record.</span></span> <span data-ttu-id="13161-199">Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span><span class="sxs-lookup"><span data-stu-id="13161-199">Wait at least 72 hours before you proceed to the next task: [Step 6: Delete the cutover migration batch](use-powershell-to-perform-a-cutover-migration-to-office-365.md#Bk_step6).</span></span> 
  
### <a name="step-6-delete-the-cutover-migration-batch"></a><span data-ttu-id="13161-200">Paso 6: Eliminar el lote de migración total</span><span class="sxs-lookup"><span data-stu-id="13161-200">Step 6: Delete the cutover migration batch</span></span>
<span data-ttu-id="13161-201"><a name="Bk_step6"> </a></span><span class="sxs-lookup"><span data-stu-id="13161-201"><a name="Bk_step6"> </a></span></span>

<span data-ttu-id="13161-202">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365.</span><span class="sxs-lookup"><span data-stu-id="13161-202">After you change the MX record and verify that all email is being routed to Office 365 mailboxes, notify the users that their mail is going to Office 365.</span></span> <span data-ttu-id="13161-203">After this, you can delete the cutover migration batch.</span><span class="sxs-lookup"><span data-stu-id="13161-203">After this, you can delete the cutover migration batch.</span></span> <span data-ttu-id="13161-204">Verify the following before you delete the migration batch.</span><span class="sxs-lookup"><span data-stu-id="13161-204">Verify the following before you delete the migration batch.</span></span>
  
- <span data-ttu-id="13161-205">All users are using Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="13161-205">All users are using Office 365 mailboxes.</span></span> <span data-ttu-id="13161-206">After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="13161-206">After the batch is deleted, mail sent to mailboxes on the on-premises Exchange Server isn't copied to the corresponding Office 365 mailboxes.</span></span>
    
- <span data-ttu-id="13161-207">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them.</span><span class="sxs-lookup"><span data-stu-id="13161-207">Office 365 mailboxes were synchronized at least once after mail began being sent directly to them.</span></span> <span data-ttu-id="13161-208">To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span><span class="sxs-lookup"><span data-stu-id="13161-208">To do this, make sure that the value in the Last Synced Time box for the migration batch is more recent than when mail started being routed directly to Office 365 mailboxes.</span></span>
    
<span data-ttu-id="13161-209">Para eliminar el lote de migración "CutoverBatch" en Exchange Online PowerShell, ejecute el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="13161-209">To delete the "CutoverBatch" migration batch in Exchange Online PowerShell, run the following command:</span></span>
  
```
Remove-MigrationBatch -Identity CutoverBatch
```

### <a name="section-7-assign-user-licenses"></a><span data-ttu-id="13161-210">Sección 7: Asignar licencias de usuario</span><span class="sxs-lookup"><span data-stu-id="13161-210">Section 7: Assign user licenses</span></span>
<span data-ttu-id="13161-211"><a name="BK_Step7"> </a></span><span class="sxs-lookup"><span data-stu-id="13161-211"><a name="BK_Step7"> </a></span></span>

 <span data-ttu-id="13161-212">**Active las cuentas de usuario de Office 365 para las cuentas migradas mediante la asignación de licencias.**</span><span class="sxs-lookup"><span data-stu-id="13161-212">**Activate Office 365 user accounts for the migrated accounts by assigning licenses.**</span></span> <span data-ttu-id="13161-213">Si no asigna una licencia, el buzón se deshabilitará cuando finalice el periodo de gracia (30 días).</span><span class="sxs-lookup"><span data-stu-id="13161-213">If you don't assign a license, the mailbox is disabled when the grace period ends (30 days).</span></span> <span data-ttu-id="13161-214">Para asignar una licencia en el centro de administración de 365 de Microsoft, vea[asignar o cancelar la asignación de licencias para Office 365 para empresas](https://go.microsoft.com/fwlink/?LinkId=536681).</span><span class="sxs-lookup"><span data-stu-id="13161-214">To assign a license in the Microsoft 365 admin center, see[Assign or unassign licenses for Office 365 for business](https://go.microsoft.com/fwlink/?LinkId=536681).</span></span>
  
### <a name="step-8-complete-post-migration-tasks"></a><span data-ttu-id="13161-215">Paso 8: Finalizar las tareas posteriores a la migración</span><span class="sxs-lookup"><span data-stu-id="13161-215">Step 8: Complete post-migration tasks</span></span>
<span data-ttu-id="13161-216"><a name="BK_Step8"> </a></span><span class="sxs-lookup"><span data-stu-id="13161-216"><a name="BK_Step8"> </a></span></span>

- <span data-ttu-id="13161-217">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span><span class="sxs-lookup"><span data-stu-id="13161-217">**Create an Autodiscover DNS record so users can easily get to their mailboxes.**</span></span> <span data-ttu-id="13161-218">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="13161-218">After all on-premises mailboxes are migrated to Office 365, you can configure an Autodiscover DNS record for your Office 365 organization to enable users to easily connect to their new Office 365 mailboxes with Outlook and mobile clients.</span></span> <span data-ttu-id="13161-219">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span><span class="sxs-lookup"><span data-stu-id="13161-219">This new Autodiscover DNS record has to use the same namespace that you're using for your Office 365 organization.</span></span> <span data-ttu-id="13161-220">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span><span class="sxs-lookup"><span data-stu-id="13161-220">For example, if your cloud-based namespace is cloud.contoso.com, the Autodiscover DNS record you need to create is autodiscover.cloud.contoso.com.</span></span>
    
    <span data-ttu-id="13161-221">Tras la migración, si mantiene su servidor Exchange, también debe asegurarse de que el registro DNS CNAME de Detección automática apunte a Office 365 tanto en el DNS interno como en el externo de modo que el cliente de Outlook se conecte al buzón correcto.</span><span class="sxs-lookup"><span data-stu-id="13161-221">If you keep your Exchange Server, you should also make sure that Autodiscover DNS CNAME record has to point to Office 365 in both internal and external DNS after the migration so that the Outlook client will to connect to the correct mailbox.</span></span>
    
    > [!NOTE]
    >  <span data-ttu-id="13161-222">En Exchange 2007, Exchange 2010 y Exchange 2013 también debe establecer  `Set-ClientAccessServer AutodiscoverInternalConnectionURI` como `Null`.</span><span class="sxs-lookup"><span data-stu-id="13161-222">In Exchange 2007, Exchange 2010, and Exchange 2013 you should also set `Set-ClientAccessServer AutodiscoverInternalConnectionURI` to `Null`.</span></span> 
  
    <span data-ttu-id="13161-223">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span><span class="sxs-lookup"><span data-stu-id="13161-223">Office 365 uses a CNAME record to implement the Autodiscover service for Outlook and mobile clients.</span></span> <span data-ttu-id="13161-224">The Autodiscover CNAME record must contain the following information:</span><span class="sxs-lookup"><span data-stu-id="13161-224">The Autodiscover CNAME record must contain the following information:</span></span>
    
  - <span data-ttu-id="13161-225">**Alias:** autodiscover</span><span class="sxs-lookup"><span data-stu-id="13161-225">**Alias:** autodiscover</span></span>
    
  - <span data-ttu-id="13161-226">**Destino:** autodiscover.outlook.com</span><span class="sxs-lookup"><span data-stu-id="13161-226">**Target:** autodiscover.outlook.com</span></span>
    
    <span data-ttu-id="13161-227">Para obtener más información, consulte [Crear registros DNS para Office 365 al administrar los registros DNS](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span><span class="sxs-lookup"><span data-stu-id="13161-227">For more information, see [Create DNS records for Office 365 when you manage your DNS records](https://go.microsoft.com/fwlink/p/?LinkId=535028).</span></span>
    
- <span data-ttu-id="13161-228">**Decommission on-premises Exchange servers.**</span><span class="sxs-lookup"><span data-stu-id="13161-228">**Decommission on-premises Exchange servers.**</span></span> <span data-ttu-id="13161-229">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span><span class="sxs-lookup"><span data-stu-id="13161-229">After you've verified that all email is being routed directly to the Office 365 mailboxes, and you no longer need to maintain your on-premises email organization or don't plan on implementing a single sign-on (SSO) solution, you can uninstall Exchange from your servers and remove your on-premises Exchange organization.</span></span>
    
    <span data-ttu-id="13161-230">Para obtener más información, vea los artículos siguientes:</span><span class="sxs-lookup"><span data-stu-id="13161-230">For more information, see the following:</span></span>
    
  - [<span data-ttu-id="13161-231">Modificar o quitar Exchange 2010</span><span class="sxs-lookup"><span data-stu-id="13161-231">Modify or Remove Exchange 2010</span></span>](https://go.microsoft.com/fwlink/?LinkId=217936)
    
  - [<span data-ttu-id="13161-232">Cómo quitar una organización de Exchange 2007</span><span class="sxs-lookup"><span data-stu-id="13161-232">How to Remove an Exchange 2007 Organization</span></span>](https://go.microsoft.com/fwlink/?LinkID=100485)
    
  - [<span data-ttu-id="13161-233">Cómo desinstalar Exchange Server 2003</span><span class="sxs-lookup"><span data-stu-id="13161-233">How to Uninstall Exchange Server 2003</span></span>](https://go.microsoft.com/fwlink/?LinkID=56561)
    

