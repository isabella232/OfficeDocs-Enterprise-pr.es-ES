---
title: Agregar datos de informes de clientes a través de Windows PowerShell para asociados con permiso de acceso delegado (DAP)
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: 0f946b46-200a-4bdd-9b1b-019a554ddcc6
description: 'Resumen: Use Windows PowerShell para Office 365 para recuperar informes de todos los arrendamientos de cliente y agregar los datos a una sola ubicación.'
ms.openlocfilehash: eba2c3be848b878670321485718317b5552b2db3
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a><span data-ttu-id="1e725-103">Agregar datos de informes de clientes a través de Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="1e725-103">Aggregate customer reporting data via Windows PowerShell for Delegated Access Permission (DAP) partners</span></span>

 <span data-ttu-id="1e725-104">**Resumen:** use Windows PowerShell para Office 365 para recuperar informes de todos los espacios empresariales de cliente y agregar los datos en una sola ubicación.</span><span class="sxs-lookup"><span data-stu-id="1e725-104">**Summary:** Use Windows PowerShell for Office 365 to retrieve reports on all customer tenancies and aggregate the data into a single location.</span></span>
  
<span data-ttu-id="1e725-p101">De forma predeterminada, Windows PowerShell para Office 365 no tiene una agregación integrada de informes de datos de varios arrendamientos de cliente. Sin embargo, puede usar este script de Windows PowerShell para Office 365 de ejemplo para recorrer en iteración todos los arrendamientos de cliente para recuperar un único informe para cada uno de los clientes y, a continuación, agregar los datos de informes a una única ubicación. El resultado es que tendrá un único informe para todos los inquilinos de cliente.</span><span class="sxs-lookup"><span data-stu-id="1e725-p101">By default, Windows PowerShell for Office 365 does not have a built-in aggregation of reporting data from multiple customer tenancies. However, you can use this sample Windows PowerShell for Office 365 script to iterate through all your customer tenancies to retrieve a single report for each of your customers and then aggregate the reporting data into a single location. The result is that you'll have a single report for all your customer tenants.</span></span> 
  
<span data-ttu-id="1e725-p102">Los asociados con permiso de acceso delegado (DAP) son asociados de sindicación y proveedor de soluciones en la nube (CSP). Con frecuencia son los proveedores de red o de telecomunicaciones para otras compañías. Empaquetan las suscripciones de Office 365 en sus ofertas de servicio a sus clientes. Cuando se vende una suscripción a Office 365, automáticamente se les conceden permisos Administrar en nombre de (AOBO) a losarrendamientos de cliente para que puedan administrar y notificar los arrendamientos de cliente.</span><span class="sxs-lookup"><span data-stu-id="1e725-p102">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners. They are frequently network or telecom providers to other companies. They bundle Office 365 subscriptions into their service offerings to their customers. When they sell an Office 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to thecustomer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="1e725-112">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="1e725-112">Before you begin</span></span>

<span data-ttu-id="1e725-113">Para usar este script, sustituya sus valores determinados por estas variables:</span><span class="sxs-lookup"><span data-stu-id="1e725-113">To use this script, substitute your particular values in for these variables:</span></span>
  
- <span data-ttu-id="1e725-p103">**$UserName**: es el nombre de usuario de administrador asociado. Estas credenciales se usarán para conectarse a todos los arrendamientos de cliente.</span><span class="sxs-lookup"><span data-stu-id="1e725-p103">**$UserName** - This is your partner administrator user name. These credentials will be used to connect to all your customer tenancies.</span></span>
    
- <span data-ttu-id="1e725-116">**$OutputFile**: este es el archivo de valores separados por comas al cual se agregarán los datos de los informes.</span><span class="sxs-lookup"><span data-stu-id="1e725-116">**$OutputFile** - This is the comma-separated value file that reporting data will be aggregated to.</span></span>
    
- <span data-ttu-id="1e725-117">**$ErrorFile**: este es el archivo de texto de registro de errores.</span><span class="sxs-lookup"><span data-stu-id="1e725-117">**$ErrorFile** - This is the text log file for errors.</span></span>
    
- <span data-ttu-id="1e725-p104">**$ScriptBlock**: este script de muestra usa **Get-MailboxActivityReport** y otros parámetros (como fechas de inicio y finalización) para tener una forma de comenzar. Si desea obtener otros informes, reemplace el nombre del informe que desea y los parámetros necesarios para **Get-MailboxActivityReport**.</span><span class="sxs-lookup"><span data-stu-id="1e725-p104">**$ScriptBlock** - This sample script uses **Get-MailboxActivityReport** and parameters (such as start and end dates) so you have a way to get started. If you want other reports, substitute the report name that you want and necessary parameters for **Get-MailboxActivityReport**.</span></span>
    
- <span data-ttu-id="1e725-120">Abra una sesión remota de Windows PowerShell a Exchange Online mediante los pasos descritos en [Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span><span class="sxs-lookup"><span data-stu-id="1e725-120">Open a remote Windows PowerShell session to Exchange Online by using the steps in [Connect to Exchange Online tenants with remote Windows PowerShell for Delegated Access Permissions (DAP) partners](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)</span></span>
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a><span data-ttu-id="1e725-121">Usar Windows PowerShell para agregar informes de inquilino de cliente a una única ubicación</span><span class="sxs-lookup"><span data-stu-id="1e725-121">Use Windows PowerShell to aggregate customer tenant reports to a single location</span></span>

1. <span data-ttu-id="1e725-122">Copie y pegue este script en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="1e725-122">Copy and paste this script into Notepad.</span></span>
    
  ```
  # Import the MSOnline module to allow connectivity to Office 365.

Import-Module MSOnline

# This is the partner admin user name to be used to run the report.

$UserName = "admin@contoso.onmicrosoft.com"

# These are the locations for the report output and error log.

$OutputFile = ".\ReportOutput.csv"

$ErrorFile = ".\Errors.txt"

# This is the report to run and all the necessary parameters.

$ScriptBlock = {Get-MailboxActivityReport -ReportType Daily -StartDate 03/18/2015 -EndDate 03/18/2015}

$LinesToSkip = 0

# This is the prompt for the password of the partner admin user name.

$Cred = get-credential -Credential $UserName

# Establish a Windows PowerShell session with Office 365.

Connect-MsolService -Credential $Cred

# Get all the contracts for the signed-in partner.  
# Contracts define the AOBO/DAP relationship between the partner and the customers.

$Contracts = Get-MsolPartnerContract -All

Write-Host "Found $($Contracts.Count) customers for this Partner."

# For each of the contracts (customers), run the specified report and output the information.

foreach ($c in $contracts) { 

    # Get the initial domain for the customer.

    $InitialDomain = Get-MsolDomain -TenantId $c.TenantId | Where {$_.IsInitial -eq $true}

    # Construct the URL with the DelegatedOrg parameter.
    
    $DelegatedOrgURL = "https://ps.outlook.com/powershell-liveid?DelegatedOrg=" + $InitialDomain.Name
        
    Write-Host "Running report for $($InitialDomain.Name)"

    # Invoke-Command establishes a Windows PowerShell session based on the URL,
    # runs the command, and closes the Windows PowerShell session.
    
    $ReportInfo = Invoke-Command -ConnectionUri $DelegatedOrgURL -Credential $Cred -Authentication Basic -ConfigurationName Microsoft.Exchange -AllowRedirection -ScriptBlock $ScriptBlock -HideComputerName

    # If Invoke-Command returned information (that is, it's not NULL), format and output the information.
    
    If ($ReportInfo) {

        Write-Host "Writing report information for $($InitialDomain.Name) to $OutputFile"  -foregroundcolor green

        # Convert the report data to CSV format.
        # For the first time, don't skip any lines, so include the header.
        # For all other times, skip the first line (so don't rewrite the header).
        
        $OutputInfo = $ReportInfo |  ConvertTo-CSV -NoTypeInformation | Select -Skip $LinesToSkip

        Out-File $OutputFile -InputObject $OutputInfo -Append

        $LinesToSkip = 1

    } else {

        # If Invoke-Command didn't return and report data, log an error.
        
        Write-Host "No report information for $($InitialDomain.Name)." -foregroundcolor yellow
           
        Out-File $ErrorFile  -InputObject @("No report information for $($InitialDomain.Name).") -Append
    }

}

  ```

2. <span data-ttu-id="1e725-p105">Guarde el script como GetMailboxActivityReport.ps1 en una ubicación fácil de encontrar. Por ejemplo, el archivo se guarda en C:\\O365 Scripts.</span><span class="sxs-lookup"><span data-stu-id="1e725-p105">Save the script as GetMailboxActivityReport.ps1 in a location that's easy for you to find. For the example, the file is saved in C:\\O365 Scripts.</span></span> 
    
3. <span data-ttu-id="1e725-125">Ejecute el script en modo remoto de Windows PowerShell siguiendo esta sintaxis.</span><span class="sxs-lookup"><span data-stu-id="1e725-125">Run the script in remote Windows PowerShell by following this syntax.</span></span>
    
  ```
  &amp; "C:\O365 Scripts\GetMailboxActivityReport.ps1"
  ```

<span data-ttu-id="1e725-126">Este script de ejemplo coloca el informe agregado en el archivo ReportOutput.csv.</span><span class="sxs-lookup"><span data-stu-id="1e725-126">This sample script places the aggregated report in the ReportOutput.csv file.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1e725-127">Consulte también</span><span class="sxs-lookup"><span data-stu-id="1e725-127">See also</span></span>

#### 

[<span data-ttu-id="1e725-128">Ayuda para partners</span><span class="sxs-lookup"><span data-stu-id="1e725-128">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[<span data-ttu-id="1e725-129">Servicio web de informes de Office 365</span><span class="sxs-lookup"><span data-stu-id="1e725-129">Office 365 Reporting web service</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[<span data-ttu-id="1e725-130">Cmdlets de informes en Exchange Online</span><span class="sxs-lookup"><span data-stu-id="1e725-130">Reporting cmdlets in Exchange Online</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=526430)

