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
ms.locfileid: "18812111"
---
# <a name="aggregate-customer-reporting-data-via-windows-powershell-for-delegated-access-permission-dap-partners"></a>Agregar datos de informes de clientes a través de Windows PowerShell para asociados con permiso de acceso delegado (DAP)

 **Resumen:** use Windows PowerShell para Office 365 para recuperar informes de todos los espacios empresariales de cliente y agregar los datos en una sola ubicación.
  
De forma predeterminada, Windows PowerShell para Office 365 no tiene una agregación integrada de informes de datos de varios arrendamientos de cliente. Sin embargo, puede usar este script de Windows PowerShell para Office 365 de ejemplo para recorrer en iteración todos los arrendamientos de cliente para recuperar un único informe para cada uno de los clientes y, a continuación, agregar los datos de informes a una única ubicación. El resultado es que tendrá un único informe para todos los inquilinos de cliente. 
  
Los asociados con permiso de acceso delegado (DAP) son asociados de sindicación y proveedor de soluciones en la nube (CSP). Con frecuencia son los proveedores de red o de telecomunicaciones para otras compañías. Empaquetan las suscripciones de Office 365 en sus ofertas de servicio a sus clientes. Cuando se vende una suscripción a Office 365, automáticamente se les conceden permisos Administrar en nombre de (AOBO) a losarrendamientos de cliente para que puedan administrar y notificar los arrendamientos de cliente.
## <a name="before-you-begin"></a>Antes de empezar

Para usar este script, sustituya sus valores determinados por estas variables:
  
- **$UserName**: es el nombre de usuario de administrador asociado. Estas credenciales se usarán para conectarse a todos los arrendamientos de cliente.
    
- **$OutputFile**: este es el archivo de valores separados por comas al cual se agregarán los datos de los informes.
    
- **$ErrorFile**: este es el archivo de texto de registro de errores.
    
- **$ScriptBlock**: este script de muestra usa **Get-MailboxActivityReport** y otros parámetros (como fechas de inicio y finalización) para tener una forma de comenzar. Si desea obtener otros informes, reemplace el nombre del informe que desea y los parámetros necesarios para **Get-MailboxActivityReport**.
    
- Abra una sesión remota de Windows PowerShell a Exchange Online mediante los pasos descritos en [Conectarse a los inquilinos de Exchange Online con el modo remoto de Windows PowerShell para asociados con permiso de acceso delegado (DAP)](connect-to-exchange-online-tenants-with-remote-windows-powershell-for-delegated.md)
    
## <a name="use-windows-powershell-to-aggregate-customer-tenant-reports-to-a-single-location"></a>Usar Windows PowerShell para agregar informes de inquilino de cliente a una única ubicación

1. Copie y pegue este script en el Bloc de notas.
    
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

2. Guarde el script como GetMailboxActivityReport.ps1 en una ubicación fácil de encontrar. Por ejemplo, el archivo se guarda en C:\\O365 Scripts. 
    
3. Ejecute el script en modo remoto de Windows PowerShell siguiendo esta sintaxis.
    
  ```
  &amp; "C:\O365 Scripts\GetMailboxActivityReport.ps1"
  ```

Este script de ejemplo coloca el informe agregado en el archivo ReportOutput.csv.
  
## <a name="see-also"></a>Consulte también

#### 

[Ayuda para partners](https://go.microsoft.com/fwlink/p/?LinkID=533477)
  
[Servicio web de informes de Office 365](https://go.microsoft.com/fwlink/p/?LinkId=532777)
  
[Cmdlets de informes en Exchange Online](https://go.microsoft.com/fwlink/p/?LinkId=526430)

