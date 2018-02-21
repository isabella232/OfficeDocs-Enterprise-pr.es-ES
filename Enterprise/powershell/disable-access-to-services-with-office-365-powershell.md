---
title: Deshabilitar el acceso a servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
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
description: "Explica cómo utilizar Office 365 PowerShell para deshabilitar el acceso a los servicios de Office 365 para los usuarios de su organización."
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="f5127-103">Deshabilitar el acceso a servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="f5127-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="f5127-104">**Resumen:** Explica cómo utilizar Office 365 PowerShell para deshabilitar el acceso a los servicios de Office 365 para los usuarios de su organización.</span><span class="sxs-lookup"><span data-stu-id="f5127-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="f5127-p101">Cuando una cuenta de Office 365 se asigna una licencia de un plan de licencias, los servicios de Office 365 están disponibles para el usuario de esa licencia. Sin embargo, puede controlar los servicios de Office 365 que tiene acceso el usuario. Por ejemplo, aunque la licencia permite el acceso a SharePoint Online, puede deshabilitar el acceso a él. De hecho, puede utilizar Office 365 PowerShell para deshabilitar el acceso a cualquier número de servicios para:</span><span class="sxs-lookup"><span data-stu-id="f5127-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>

- <span data-ttu-id="f5127-109">Una cuenta individual.</span><span class="sxs-lookup"><span data-stu-id="f5127-109">An individual account.</span></span>
    
- <span data-ttu-id="f5127-110">Un grupo de cuentas.</span><span class="sxs-lookup"><span data-stu-id="f5127-110">A group of accounts.</span></span>
    
- <span data-ttu-id="f5127-111">Todas las cuentas de su organización.</span><span class="sxs-lookup"><span data-stu-id="f5127-111">All accounts in your organization.</span></span>
    
## <a name="before-you-begin"></a><span data-ttu-id="f5127-112">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="f5127-112">Before you begin</span></span>
<span data-ttu-id="f5127-113"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="f5127-113"></span></span>

- <span data-ttu-id="f5127-p102">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f5127-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f5127-p103">Utilice el cmdlet **Get-MsolAccountSku** para ver los planes de licencias disponibles y los servicios de Office 365 que están disponibles en dichos planes. Para obtener más información, vea [ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f5127-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f5127-118">Para ver el antes y después de los resultados de los procedimientos de este tema, vea [Ver detalles de licencia y servicio cuenta con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f5127-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f5127-p104">Hay un script de PowerShell que automatiza los procedimientos descritos en este tema. En concreto, el script le permite ver y deshabilitar servicios de la organización de Office 365, incluido Sway. Para obtener más información, consulte [Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f5127-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="f5127-122">Si utiliza el cmdlet **Get-MsolUser** sin utilizar el parámetro _All_ , se devuelven las primeras cuentas de usuario de 500.</span><span class="sxs-lookup"><span data-stu-id="f5127-122">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a><span data-ttu-id="f5127-123">Servicios específicos de Office 365 para usuarios específicos para un único plan de licencias</span><span class="sxs-lookup"><span data-stu-id="f5127-123">Specific Office 365 services for specific users for a single licensing plan</span></span>
  
<span data-ttu-id="f5127-124">Para deshabilitar un conjunto específico de servicios de Office 365 para los usuarios de un único plan de licencias, realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="f5127-124">To disable a specific set of Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="f5127-125">Identificar los servicios no deseados en el plan de licencias mediante la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="f5127-125">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="f5127-126">En el ejemplo siguiente se crea un objeto **LicenseOptions** que deshabilita los servicios de SharePoint Online y Office Online en el plan de licencia denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="f5127-126">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="f5127-127">Utilice el objeto **LicenseOptions** del paso 1 en uno o más usuarios.</span><span class="sxs-lookup"><span data-stu-id="f5127-127">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="f5127-128">Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="f5127-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="f5127-129">En el ejemplo siguiente se crea una nueva cuenta para Allie Bellew que asigna la licencia y deshabilita los servicios descritos en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="f5127-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="f5127-130">Para obtener más información acerca de cómo crear cuentas de usuario en Office 365 PowerShell, consulte [crear cuentas de usuario con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="f5127-130">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="f5127-131">Para deshabilitar los servicios para un usuario con licencia existente, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="f5127-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="f5127-132">En este ejemplo se deshabilitan los servicios para el usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="f5127-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="f5127-133">Para deshabilitar los servicios descritos en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre de su plan de Office 365 desde la pantalla del cmdlet **Get-MsolAccountSku** (como **litwareinc:ENTERPRISEPACK**) y, a continuación, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="f5127-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="f5127-134">Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:</span><span class="sxs-lookup"><span data-stu-id="f5127-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="f5127-135">**Filtrar las cuentas basadas en un atributo de cuenta existente** Para ello, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="f5127-135">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="f5127-136">En el ejemplo siguiente se deshabilita los servicios para los usuarios del departamento de ventas en los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="f5127-136">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="f5127-137">**Usar una lista de cuentas específicas** Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="f5127-137">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="f5127-138">Cree un archivo de texto que contenga una cuenta en cada línea como en el ejemplo:</span><span class="sxs-lookup"><span data-stu-id="f5127-138">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    <span data-ttu-id="f5127-139">En este ejemplo, el archivo de texto es C:\\documentos\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="f5127-139">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="f5127-140">Ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="f5127-140">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="f5127-141">Para deshabilitar los servicios de Office 365 para usuarios mientras se les va a asignar a un plan de licencias, vea [Deshabilitar el acceso a los servicios al asignar licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="f5127-141">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a><span data-ttu-id="f5127-142">Servicios específicos de Office 365 para los usuarios de todos los planes de licencias</span><span class="sxs-lookup"><span data-stu-id="f5127-142">Specific Office 365 services for users from all licensing plans</span></span>
  
<span data-ttu-id="f5127-143">Para deshabilitar los servicios de Office 365 para los usuarios en todos los planes de licencias disponibles, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="f5127-143">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="f5127-144">Copie y pegue este script en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="f5127-144">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="f5127-145">Personalice los valores siguientes para su entorno:</span><span class="sxs-lookup"><span data-stu-id="f5127-145">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="f5127-146">_<UndesirableService>_En este ejemplo, vamos a utilizar SharePoint Online y Office Online.</span><span class="sxs-lookup"><span data-stu-id="f5127-146">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="f5127-147">_<Account>_En este ejemplo, vamos a utilizar belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="f5127-147">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="f5127-148">El script personalizado tiene el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="f5127-148">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="f5127-p105">Guardar la secuencia de comandos `RemoveO365Services.ps1` en una ubicación que sea fácil de encontrar. Para este ejemplo, se va a guardar el archivo en `C:\\O365 Scripts`.</span><span class="sxs-lookup"><span data-stu-id="f5127-p105">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in `C:\\O365 Scripts`.</span></span>
    
4. <span data-ttu-id="f5127-151">Ejecute la secuencia de comandos en Office 365 PowerShell utilizando el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="f5127-151">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="f5127-152">Para invertir los efectos de uno de estos procedimientos (es decir, volver a habilitar los servicios deshabilitados), vuelva a ejecutar el procedimiento, pero utilice el valor `$null` para el parámetro _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="f5127-152">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="f5127-153">Volver al principio</span><span class="sxs-lookup"><span data-stu-id="f5127-153">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a><span data-ttu-id="f5127-154">Todos los servicios de Office 365 para todos los usuarios de un plan individual de licencias</span><span class="sxs-lookup"><span data-stu-id="f5127-154">All Office 365 services for all users for a single licensing plan</span></span>
 
<span data-ttu-id="f5127-155">Para deshabilitar todos los servicios de Office 365 para todos los usuarios de un determinado plan de licencias, especifique el nombre de plan licencias para $acctSKU (como **litwareinc:ENTERPRISEPACK**) y, a continuación, ejecutar estos comandos en la ventana de comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f5127-155">To disable all Office 365 services for all users in a specific licensing plan, specify the licensing plan name for $acctSKU (such as **litwareinc:ENTERPRISEPACK**), and then run these commands in the PowerShell command window:</span></span>

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a><span data-ttu-id="f5127-156">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="f5127-156">New to Office 365?</span></span>
<span data-ttu-id="f5127-157"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="f5127-157"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="f5127-158">Vea también</span><span class="sxs-lookup"><span data-stu-id="f5127-158">See also</span></span>
<span data-ttu-id="f5127-159"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="f5127-159"></span></span>

<span data-ttu-id="f5127-160">Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="f5127-160">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="f5127-161">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="f5127-161">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f5127-162">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="f5127-162">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f5127-163">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="f5127-163">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f5127-164">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="f5127-164">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="f5127-165">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="f5127-165">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="f5127-166">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="f5127-166">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="f5127-167">Get-Content</span><span class="sxs-lookup"><span data-stu-id="f5127-167">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="f5127-168">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="f5127-168">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="f5127-169">Nueva MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="f5127-169">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="f5127-170">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="f5127-170">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="f5127-171">New-MsolUser</span><span class="sxs-lookup"><span data-stu-id="f5127-171">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="f5127-172">Set-MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="f5127-172">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="f5127-173">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="f5127-173">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="f5127-174">Where-Object</span><span class="sxs-lookup"><span data-stu-id="f5127-174">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

