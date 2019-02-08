---
title: Deshabilitar el acceso a servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/11/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Se explica cómo usar PowerShell de Office 365 para deshabilitar el acceso a los servicios de Office 365 para los usuarios de su organización.
ms.openlocfilehash: 66f6c04c1488f14d5752974a5475e7ef11279406
ms.sourcegitcommit: bbbe304bb1878b04e719103be4287703fb3ef292
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2019
ms.locfileid: "25897423"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="6004c-103">Deshabilitar el acceso a servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6004c-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="6004c-104">**Resumen:** Se explica cómo usar PowerShell de Office 365 para deshabilitar el acceso a los servicios de Office 365 para los usuarios de su organización.</span><span class="sxs-lookup"><span data-stu-id="6004c-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="6004c-p101">Cuando una cuenta de Office 365 se asigna una licencia de un plan de licencias, servicios de Office 365 están disponibles para el usuario de la licencia. Sin embargo, puede controlar los servicios de Office 365 que puede obtener acceso el usuario. Por ejemplo, aunque la licencia permite el acceso al servicio de SharePoint Online, puede deshabilitar el acceso a ella. Puede usar PowerShell de Office 365 para deshabilitar el acceso a cualquier número de servicios para un plan de licencias específico para:</span><span class="sxs-lookup"><span data-stu-id="6004c-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to the SharePoint Online service, you can disable access to it. You can use Office 365 PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="6004c-109">Una cuenta individual.</span><span class="sxs-lookup"><span data-stu-id="6004c-109">An individual account.</span></span>
    
- <span data-ttu-id="6004c-110">Un grupo de cuentas.</span><span class="sxs-lookup"><span data-stu-id="6004c-110">A group of accounts.</span></span>
    
- <span data-ttu-id="6004c-111">Todas las cuentas de su organización.</span><span class="sxs-lookup"><span data-stu-id="6004c-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="6004c-112">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="6004c-112">Before you begin</span></span>
<span data-ttu-id="6004c-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="6004c-113"></span></span>

- <span data-ttu-id="6004c-p102">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6004c-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6004c-p103">Use el cmdlet **Get-MsolAccountSku** para ver los planes de licencias disponibles y los servicios de Office 365 que están disponibles en esos planes. Para obtener más información, vea [ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6004c-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6004c-118">Para ver el antes y después de los resultados de los procedimientos descritos en este tema, vea [Ver los detalles de licencia y servicio cuenta con PowerShell de Office 365](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6004c-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6004c-p104">Un script de PowerShell está disponible que automatiza los procedimientos descritos en este tema. En concreto, la secuencia de comandos le permite ver y deshabilitar los servicios de la organización de Office 365, incluidos balanceo. Para obtener más información, vea [Deshabilitar el acceso a balanceo con PowerShell de Office 365](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6004c-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script lets you view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="6004c-122">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_ , se devuelven las primeras cuentas de usuario de 500.</span><span class="sxs-lookup"><span data-stu-id="6004c-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="6004c-123">Deshabilitar los servicios específicos de Office 365 para usuarios específicos para un plan de licencias específico</span><span class="sxs-lookup"><span data-stu-id="6004c-123">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="6004c-124">Para deshabilitar un conjunto específico de servicios de Office 365 para los usuarios de un plan de licencias específico, realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="6004c-124">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="6004c-125">Identificar los servicios no deseados en el plan de licencias mediante la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="6004c-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="6004c-126">En el ejemplo siguiente se crea un objeto **Addlicenses** que deshabilita los servicios de SharePoint Online y Office Online en el plan de licencias denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="6004c-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="6004c-127">Use el objeto **LicenseOptions** del paso 1 en uno o más usuarios.</span><span class="sxs-lookup"><span data-stu-id="6004c-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="6004c-128">Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="6004c-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="6004c-129">En el ejemplo siguiente se crea una nueva cuenta para Allie Bellew que asigna la licencia y deshabilita los servicios que se describen en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="6004c-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="6004c-130">Para obtener más información sobre la creación de cuentas de usuario en PowerShell de Office 365, vea [crear cuentas de usuario con PowerShell de Office 365](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="6004c-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="6004c-131">Para deshabilitar los servicios para un usuario con licencia existente, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="6004c-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="6004c-132">En este ejemplo se deshabilitan los servicios para el usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="6004c-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="6004c-133">Para deshabilitar los servicios que se describen en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre del plan de Office 365 de la presentación del cmdlet **Get-MsolAccountSku** (por ejemplo, **litwareinc: enterprisepack**) y, a continuación, ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="6004c-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="6004c-134">Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:</span><span class="sxs-lookup"><span data-stu-id="6004c-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="6004c-135">**Filtrar las cuentas basadas en un atributo de cuenta existente** Para ello, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="6004c-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="6004c-136">El siguiente ejemplo deshabilita los servicios para los usuarios del departamento de ventas en los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="6004c-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="6004c-137">**Usar una lista de cuentas específicas** Para ello, realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="6004c-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="6004c-138">Cree un archivo de texto que contenga una cuenta en cada línea como en el ejemplo:</span><span class="sxs-lookup"><span data-stu-id="6004c-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="6004c-139">En este ejemplo, el archivo de texto es C:\\Mis documentos\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="6004c-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="6004c-140">Ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="6004c-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="6004c-141">Si desea deshabilitar el acceso a los servicios para varios planes de licencias, repita las instrucciones anteriores para cada plan de licencias, asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="6004c-141">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="6004c-142">Las cuentas de usuario se han asignado el plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="6004c-142">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="6004c-143">Para deshabilitar los servicios de están disponibles en el plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="6004c-143">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="6004c-144">Para deshabilitar los servicios de Office 365 para los usuarios mientras se asigna a un plan de licencias, vea [Deshabilitar el acceso a los servicios durante la asignación de licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="6004c-144">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="6004c-145">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="6004c-145">New to Office 365?</span></span>
<span data-ttu-id="6004c-146"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="6004c-146"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="6004c-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="6004c-147">See also</span></span>
<span data-ttu-id="6004c-148"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="6004c-148"></span></span>

<span data-ttu-id="6004c-149">Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="6004c-149">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="6004c-150">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6004c-150">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6004c-151">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6004c-151">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6004c-152">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6004c-152">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6004c-153">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6004c-153">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="6004c-154">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="6004c-154">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="6004c-155">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="6004c-155">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="6004c-156">Get-Content</span><span class="sxs-lookup"><span data-stu-id="6004c-156">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="6004c-157">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="6004c-157">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="6004c-158">Nueva MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="6004c-158">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="6004c-159">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="6004c-159">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="6004c-160">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="6004c-160">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="6004c-161">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="6004c-161">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="6004c-162">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="6004c-162">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="6004c-163">Where-Object</span><span class="sxs-lookup"><span data-stu-id="6004c-163">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

