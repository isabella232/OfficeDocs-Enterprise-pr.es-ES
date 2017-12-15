---
title: Deshabilitar el acceso a servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Explica cómo utilizar Office 365 PowerShell para agregar o quitar el acceso a los servicios de Office 365 para los usuarios de la organización."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="84862-103">Deshabilitar el acceso a servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="84862-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="84862-104">**Resumen:** Explica cómo utilizar Office 365 PowerShell para agregar o quitar el acceso a los servicios de Office 365 para los usuarios de la organización.</span><span class="sxs-lookup"><span data-stu-id="84862-104">**Summary:** Explains how to use Office 365 PowerShell to add or remove access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="84862-p101">Cuando una cuenta de Office 365 se asigna una licencia de un plan de licencias, los servicios de Office 365 están disponibles para el usuario de esa licencia. Sin embargo, puede controlar los servicios de Office 365 que tiene acceso el usuario. Por ejemplo, aunque la licencia permite el acceso a SharePoint Online, puede deshabilitar el acceso a él. De hecho, puede utilizar Office 365 PowerShell para deshabilitar el acceso a cualquier número de servicios para:</span><span class="sxs-lookup"><span data-stu-id="84862-p101">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license. However, you can control the Office 365 services that the user can access. For example, even though the license allows access to SharePoint Online, you can disable access to it. In fact, you can use Office 365 PowerShell to disable access to any number of services for:</span></span>
- <span data-ttu-id="84862-109">Una cuenta individual.</span><span class="sxs-lookup"><span data-stu-id="84862-109">An individual account.</span></span>
    
- <span data-ttu-id="84862-110">Un grupo de cuentas.</span><span class="sxs-lookup"><span data-stu-id="84862-110">A group of accounts.</span></span>
    
- <span data-ttu-id="84862-111">Todas las cuentas de su organización.</span><span class="sxs-lookup"><span data-stu-id="84862-111">All accounts in your organization.</span></span>
    
 <span data-ttu-id="84862-112">**Contenido:** [La versión corta (instrucciones sin las explicaciones)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [La versión larga (instrucciones con explicaciones detalladas)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Vea también](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span><span class="sxs-lookup"><span data-stu-id="84862-112">**Contents:**[The short version (instructions without explanations)](disable-access-to-services-with-office-365-powershell.md#ShortVersion)[The long version (instructions with detailed explanations)](disable-access-to-services-with-office-365-powershell.md#LongVersion)[See also](disable-access-to-services-with-office-365-powershell.md#SeeAlso)</span></span>
## <a name="before-you-begin"></a><span data-ttu-id="84862-113">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="84862-113">Before you begin</span></span>
<span data-ttu-id="84862-114"><a name="RTT"> </a></span><span class="sxs-lookup"><span data-stu-id="84862-114"></span></span>

- <span data-ttu-id="84862-p102">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="84862-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="84862-p103">Utilice el cmdlet **Get-MsolAccountSku** para ver los planes de licencias disponibles y los servicios de Office 365 que están disponibles en dichos planes. Para obtener más información, vea[ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="84862-p103">You use the **Get-MsolAccountSku** cmdlet to view your available licensing plans, and the Office 365 services that are available in those plans. For more information, see[View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="84862-119">Para ver el antes y después de los resultados de los procedimientos de este tema, vea [Ver detalles de licencia y servicio cuenta con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="84862-119">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="84862-p104">Hay un script de PowerShell que automatiza los procedimientos descritos en este tema. En concreto, el script le permite ver y deshabilitar servicios de la organización de Office 365, incluido Sway. Para obtener más información, consulte [Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="84862-p104">A PowerShell script is available that automates the procedures described in this topic. Specifically, the script allows you to view and disable services in your Office 365 organization, including Sway. For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
- <span data-ttu-id="84862-123">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="84862-123">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 accounts are returned.</span></span>
    
## <a name="the-short-version-instructions-without-explanations"></a><span data-ttu-id="84862-124">Versión corta (instrucciones sin explicaciones)</span><span class="sxs-lookup"><span data-stu-id="84862-124">The short version (instructions without explanations)</span></span>
<span data-ttu-id="84862-125"><a name="ShortVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="84862-125"></span></span>

<span data-ttu-id="84862-p105">En esta sección se presentan los procedimientos sin explicaciones superfluas. Si tiene preguntas o desea obtener más información, puede leer el resto del tema.</span><span class="sxs-lookup"><span data-stu-id="84862-p105">This section presents the procedures without fanfare or superfluous explanation. If you have questions or want more information, you can read rest of the topic.</span></span>
  
<span data-ttu-id="84862-128">Para deshabilitar los servicios de Office 365 para los usuarios de un único plan de licencias, realice los pasos siguientes:</span><span class="sxs-lookup"><span data-stu-id="84862-128">To disable Office 365 services for users from a single licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="84862-129">Identificar los servicios no deseados en el plan de licencias mediante la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="84862-129">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    <span data-ttu-id="84862-130">Este ejemplo crea un objeto **LicenseOptions** que deshabilita los servicios de SharePoint Online y Office Online en el plan de licencia denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="84862-130">This example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="84862-131">Utilice el objeto **LicenseOptions** del paso 1 en uno o más usuarios.</span><span class="sxs-lookup"><span data-stu-id="84862-131">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="84862-132">Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="84862-132">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    <span data-ttu-id="84862-133">En este ejemplo se crea una nueva cuenta para Allie Bellew que asigna la licencia y deshabilita los servicios descritos en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="84862-133">This example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    <span data-ttu-id="84862-134">Para obtener más información acerca de cómo crear cuentas de usuario en Office 365 PowerShell, consulte [crear cuentas de usuario con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="84862-134">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="84862-135">Para deshabilitar los servicios para un usuario con licencia existente, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="84862-135">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    <span data-ttu-id="84862-136">En este ejemplo se deshabilitan los servicios para el usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="84862-136">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="84862-137">Para deshabilitar los servicios descritos en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre de su plan de Office 365 desde la pantalla del cmdlet **Get-MsolAccountSku** (como **litwareinc:ENTERPRISEPACK** ) y, a continuación, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="84862-137">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - <span data-ttu-id="84862-138">Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:</span><span class="sxs-lookup"><span data-stu-id="84862-138">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="84862-139">**Filtrar las cuentas basadas en un atributo de cuenta existente** Para ello, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="84862-139">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    <span data-ttu-id="84862-140">En este ejemplo se deshabilitan los servicios para los usuarios del Departamento de Ventas en Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="84862-140">This example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="84862-141">**Usar una lista de cuentas específicas** Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="84862-141">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="84862-142">Cree un archivo de texto que contenga una cuenta en cada línea como en el ejemplo:</span><span class="sxs-lookup"><span data-stu-id="84862-142">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

    <span data-ttu-id="84862-143">En este ejemplo, el archivo de texto es C:\\documentos\\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="84862-143">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="84862-144">Ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="84862-144">Run the following command:</span></span>
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="84862-145">Para deshabilitar los servicios de Office 365 para usuarios mientras se les va a asignar a un plan de licencias, vea [Deshabilitar el acceso a los servicios al asignar licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="84862-145">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>
  
<span data-ttu-id="84862-146">Para deshabilitar los servicios de Office 365 para los usuarios en todos los planes de licencias disponibles, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="84862-146">To disable Office 365 services for users in all available licensing plans, perform the following steps:</span></span>
  
1. <span data-ttu-id="84862-147">Copie y pegue este script en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="84862-147">Copy and paste this script into Notepad.</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. <span data-ttu-id="84862-148">Personalice los valores siguientes para su entorno:</span><span class="sxs-lookup"><span data-stu-id="84862-148">Customize the following values for your environment:</span></span>
    
  -  <span data-ttu-id="84862-149">_<UndesirableService>_En este ejemplo, vamos a utilizar SharePoint Online y Office Online.</span><span class="sxs-lookup"><span data-stu-id="84862-149">_<UndesirableService>_ In this example, we'll use Office Online and SharePoint Online.</span></span>
    
  -  <span data-ttu-id="84862-150">_<Account>_En este ejemplo, vamos a utilizar belindan@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="84862-150">_<Account>_ In this example, we'll use belindan@litwareinc.com.</span></span>
    
    <span data-ttu-id="84862-151">El script personalizado tiene el siguiente aspecto:</span><span class="sxs-lookup"><span data-stu-id="84862-151">The customized script looks like this:</span></span>
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. <span data-ttu-id="84862-p106">Guardar la secuencia de comandos `RemoveO365Services.ps1` en una ubicación que sea fácil de encontrar. Para este ejemplo, se va a guardar el archivo en " `C:\\O365 Scripts`".</span><span class="sxs-lookup"><span data-stu-id="84862-p106">Save the script as  `RemoveO365Services.ps1` in a location that's easy for you to find. For this example, we'll save the file in " `C:\\O365 Scripts`".</span></span>
    
4. <span data-ttu-id="84862-154">Ejecute la secuencia de comandos en Office 365 PowerShell utilizando el comando siguiente.</span><span class="sxs-lookup"><span data-stu-id="84862-154">Run the script in Office 365 PowerShell by using the following command.</span></span>
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> <span data-ttu-id="84862-155">Para invertir los efectos de uno de estos procedimientos (es decir, volver a habilitar los servicios deshabilitados), vuelva a ejecutar el procedimiento, pero utilice el valor `$null` para el parámetro _DisabledPlans_ .</span><span class="sxs-lookup"><span data-stu-id="84862-155">To reverse the effects of any of these procedures (that is, to re-enable the disabled services), run the procedure again, but use the value  `$null` for the _DisabledPlans_ parameter.</span></span>
  
[<span data-ttu-id="84862-156">Volver al principio</span><span class="sxs-lookup"><span data-stu-id="84862-156">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a><span data-ttu-id="84862-157">Versión larga (instrucciones con explicaciones detalladas)</span><span class="sxs-lookup"><span data-stu-id="84862-157">The long version (instructions with detailed explanations)</span></span>
<span data-ttu-id="84862-158"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="84862-158"></span></span>

<span data-ttu-id="84862-p107">De forma predeterminada, todos los servicios están habilitados cuando se emite una licencia mediante Office 365 PowerShell. Y a menudo es bueno: Esto significa que puede rápida y fácilmente asignar licencias a los usuarios sin tener que especificar que cada servicio esté habilitado en el camino.</span><span class="sxs-lookup"><span data-stu-id="84862-p107">By default, all services are enabled when you issue a license by using Office 365 PowerShell. And often that's a good thing: that means that you can quickly and easily assign licenses to users without having to specify that each and every service be enabled along the way.</span></span>
  
<span data-ttu-id="84862-p108">Dicho esto, sin embargo, también es verdad que desea restringir los servicios disponibles algunos de los usuarios; Por ejemplo, tal vez algunos usuarios deben tener acceso a Office Professional Plus, Skype para los negocios en línea y en línea de Exchange, pero esos mismos usuarios no deberían tener acceso a SharePoint Online o a Office Online. ¿Puede restringir las cuentas de ese modo? Según parece, puede. Para ayudar a explicar cómo funciona esto, vamos a adoptar un enfoque de dos pasos para abordar este problema:</span><span class="sxs-lookup"><span data-stu-id="84862-p108">Having said that, however, it's also true that you might want to restrict the services available some of your users; for example, maybe some users should have access to Office Professional Plus, Skype for Business Online, and Exchange Online, but those same users shouldn't have access to SharePoint Online or to Office Online. Can you restrict accounts in that fashion? As it turns out, you can. To help explain how this works, let's take a two-step approach to tackling this problem:</span></span>
  
1. <span data-ttu-id="84862-165">Asignar al usuario una licencia de Office 365 que habilita automáticamente todos los servicios.</span><span class="sxs-lookup"><span data-stu-id="84862-165">Assign the user an Office 365 license that automatically enables all the services.</span></span>
    
2. <span data-ttu-id="84862-166">Ejecutar un par de comandos de Office 365 PowerShell que deshabilitar servicios especificados para ese usuario.</span><span class="sxs-lookup"><span data-stu-id="84862-166">Run a pair of Office 365 PowerShell commands that disable specified services for that user.</span></span>
    
<span data-ttu-id="84862-p109">Ya nos hemos tomado a cargo del paso 1: nuestro usuario (Belinda Newman) tiene una licencia de Office 365 que le proporciona acceso a todos los servicios de Office 365. Sin embargo, deseamos modificar cuenta de Belinda para que ella no tiene acceso a SharePoint Online ( `SHAREPOINTENTERPRISE`) o en Office Online ( `SHAREPOINTWAC`). Pero, ¿cómo se supone que debemos hacerlo?</span><span class="sxs-lookup"><span data-stu-id="84862-p109">We've already taken care of step 1: our user (Belinda Newman) has an Office 365 license that provides her with access to all the Office 365 services. However, we want to modify Belinda's account so that she doesn't have access to SharePoint Online ( `SHAREPOINTENTERPRISE`) or to Office Online ( `SHAREPOINTWAC`). But how are we supposed to do that?</span></span>
  
<span data-ttu-id="84862-p110">Le mostramos cómo. Para comenzar con, vamos a utilizar el cmdlet **New-MsolLicenseOptions** para crear un objeto **LicenseOption** que contiene los servicios que queremos deshabilitados. En el caso de Belinda, que deseamos deshabilitar `SHAREPOINTENTERPRISE` y `SHAREPOINTWAC`, por eso usamos este comando:</span><span class="sxs-lookup"><span data-stu-id="84862-p110">Here's how. To begin with, we're going to use the **New-MsolLicenseOptions** cmdlet to create a **LicenseOption** object that contains the services that we want disabled. In Belinda's case, we want to disable `SHAREPOINTENTERPRISE` and `SHAREPOINTWAC`, so we use this command:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="84862-p111">¿Para ver cómo funciona? Especificar el plan de licencia ( `litwareinc:ENTERPRISEPACK`) y, a continuación, indicar a cada uno de los servicios que desee deshabilitados, separar dichos servicios mediante comas.</span><span class="sxs-lookup"><span data-stu-id="84862-p111">See how that works? You specify the licensing plan ( `litwareinc:ENTERPRISEPACK`) and then indicate each of the services that you want disabled, separating those services by using commas.</span></span>
  
> [!NOTE]
> <span data-ttu-id="84862-p112">Asegúrese de que el nuevo objeto de **LicenseOption** se almacena en una variable. En el ejemplo anterior, hemos utilizado `$x`, aunque se puede utilizar cualquier nombre válido de variable de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="84862-p112">Make sure you store your new **LicenseOption** object in a variable. In the preceding example, we used `$x`, although you can use any valid Windows PowerShell variable name.</span></span> 
  
<span data-ttu-id="84862-177">En este punto podemos utilizar el siguiente comando para deshabilitar el acceso a los dos servicios de Belinda:</span><span class="sxs-lookup"><span data-stu-id="84862-177">At this point we can use the following command to disable Belinda's access to the two services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="84862-p113">Demasiado decorativo nada aquí, cualquiera: sólo llame el cmdlet **Set-MsolUserLicense** e incluya el parámetro _LicenseOptions_ , junto con la variable ( `$x`) que contiene los planes que deseamos deshabilitar. Y ¿qué vemos ahora si se Eche un vistazo a la información de licencia de Belinda ejecutando el comando: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Esto es evidente:</span><span class="sxs-lookup"><span data-stu-id="84862-p113">Nothing too fancy here, either: we just call the **Set-MsolUserLicense** cmdlet and include the _LicenseOptions_ parameter, along with the variable ( `$x`) containing the plans we want to disable. And what do we see now if we take a peek at Belinda's license information by running the command:  `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? We see this:</span></span>
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

<span data-ttu-id="84862-p114">Queda bien, ¿verdad? Y, por supuesto, podríamos hacer lo mismo a varios usuarios si deseáramos. Por ejemplo, estos comandos deshabilitar los mismos dos servicios para todos nuestros usuarios con licencia. Especificar el nombre de su plan de Office 365 desde la pantalla del cmdlet **Get-MsolAccountSku** (como **litwareinc:ENTERPRISEPACK** ) y, a continuación, ejecutarlas.</span><span class="sxs-lookup"><span data-stu-id="84862-p114">Pretty cool, huh? And, of course, we could do this same thing to multiple users if we wanted to. For example, these commands disable the same two services for all our licensed users. Specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK** ), and then run them.</span></span>
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

<span data-ttu-id="84862-p115">Tenga en cuenta que Belinda todavía tiene una licencia válida de Office 365; es sólo ahora tiene acceso a servicios de menos. Antes de que se deshabilitara los dos servicios, Belinda ha tenido acceso a suministros de noticias, OneDrive y SharePoint Online sitios:</span><span class="sxs-lookup"><span data-stu-id="84862-p115">Keep in mind that Belinda still has a valid Office 365 license; it's just that now she has access to fewer services. Before we disabled the two services, Belinda had access to newsfeeds, OneDrive, and SharePoint Online sites:</span></span>
  
![Usuario con acceso a SharePoint.](images/o365_powershell_with_sharepoint.png)
  
<span data-ttu-id="84862-188">Ahora, esas opciones ya no están disponibles para ella:</span><span class="sxs-lookup"><span data-stu-id="84862-188">Now those options are no longer available to her:</span></span>
  
![Usuario sin acceso a SharePoint.](images/o365_powershell_without_sharepoint.png)
  
<span data-ttu-id="84862-190">Que es exactamente lo que esperábamos que sucediera.</span><span class="sxs-lookup"><span data-stu-id="84862-190">Which is exactly what we hoped would happen.</span></span>
  
<span data-ttu-id="84862-p116">Y ¿qué ocurre si cambiamos nuestra mente más adelante: ¿es posible volver a habilitar estos servicios? Por supuesto que sí que lo es. Para volver a habilitar todos los servicios de un usuario, utilizar este comando para crear el objeto **LicenseOption** siguiente:</span><span class="sxs-lookup"><span data-stu-id="84862-p116">And what if we change our mind later on: is it possible to re-enable these services? You bet it is. To re-enable all the services for a user, just use this command to create the following **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="84862-p117">¿Qué hace este comando? Para empezar, la constante de Windows PowerShell `$null` significa "nada". (O, en lenguaje de ligeramente más técnico, significa "valor nulo".) Como recuerda, cuando usamos el cmdlet **New-MsolLicenseOptions** tenemos que indicar los servicios que queremos a deshabilitado. En este caso, no queremos que cualquiera de los servicios que se deshabilite. Que podría dar lugar a creer que podríamos usar un comando como el siguiente, un comando que no especificamos un valor para el parámetro _DisabledPlans_ :</span><span class="sxs-lookup"><span data-stu-id="84862-p117">What does that command do? To begin with, the Windows PowerShell constant  `$null` means "nothing." (Or, in slightly-more technical language, it means a "null value.") As you recall, when we use the **New-MsolLicenseOptions** cmdlet we have to indicate the services that we want disabled. In this case, we don't want any of the services to be disabled. That might lead you to believe that we could use a command like the following, a command where we don't specify a value for the _DisabledPlans_ parameter:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

<span data-ttu-id="84862-p118">Sin embargo, eso no funcionaría. En su lugar, genera un mensaje de error:</span><span class="sxs-lookup"><span data-stu-id="84862-p118">However, that won't work. Instead, it generates an error message:</span></span>
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
<span data-ttu-id="84862-201">Afortunadamente para nosotros, establecer el valor del parámetro `$null` a trabajar:</span><span class="sxs-lookup"><span data-stu-id="84862-201">Fortunately for us, setting the parameter value to  `$null` does work:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

<span data-ttu-id="84862-202">Esto significa simplemente que, cuando se ejecuta el cmdlet **Set-MsolUserLicense** , estamos diciendo **Conjunto MsolUserLicense** que no queremos que Belinda tenga los servicios deshabilitados:</span><span class="sxs-lookup"><span data-stu-id="84862-202">This simply means that, when we run the **Set-MsolUserLicense** cmdlet, we're telling **Set-MsolUserLicense** that we don't want Belinda to have any disabled services:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

<span data-ttu-id="84862-203">Y, como es lógico, si ninguno de los servicios se deshabilita, significa que todos los servicios están habilitados.</span><span class="sxs-lookup"><span data-stu-id="84862-203">And, logically enough, if none of the services are disabled that must mean that all of the services are enabled.</span></span>
  
<span data-ttu-id="84862-p119">Ahora que entiende cómo funciona todo esto, le mostraremos cómo puede emitir una licencia y deshabilitar los servicios especificados y todos con el mismo comando. Eso suena bastante impresionante, pero, para ser sinceros, no hay realmente nada a ella: sólo incluye los parámetros _LicenseOptions_ y el _AddLicenses_ en el mismo comando. En otras palabras, primero cree el objeto **LicenseOption** :</span><span class="sxs-lookup"><span data-stu-id="84862-p119">Now that you understand how this all works, let's show you how you can issue a license and disable specified services, and all with the same command. That sounds pretty impressive, but, to be honest, there's really nothing to it: you just include both the  _AddLicenses_ and the _LicenseOptions_ parameters in the same command. In other words, you first create your **LicenseOption** object:</span></span>
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

<span data-ttu-id="84862-207">Y, a continuación, como se indicó anteriormente, utiliza los parámetros _LicenseOptions_ y el _AddLicenses_ en el comando:</span><span class="sxs-lookup"><span data-stu-id="84862-207">And then, as noted previously, you use both the  _AddLicenses_ and the _LicenseOptions_ parameters in your command:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

<span data-ttu-id="84862-208">Que comando emitirá Belinda Newman una licencia nueva, pero una licencia en qué Skype para los negocios en línea ( `SHAREPOINTWAC`) y SharePoint Online ( `SHAREPOINTENTERPRISE`) están ambos desactivados.</span><span class="sxs-lookup"><span data-stu-id="84862-208">That command will issue Belinda Newman a new license, but a license in which Skype for Business Online ( `SHAREPOINTWAC`) and SharePoint Online ( `SHAREPOINTENTERPRISE`) are both disabled.</span></span>
  
[<span data-ttu-id="84862-209">Volver al principio</span><span class="sxs-lookup"><span data-stu-id="84862-209">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a><span data-ttu-id="84862-210">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="84862-210">New to Office 365?</span></span>
<span data-ttu-id="84862-211"><a name="LongVersion"> </a></span><span class="sxs-lookup"><span data-stu-id="84862-211"></span></span>

||
|:-----|
|<span data-ttu-id="84862-p120">![El icono reducido de LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **¿Es la primera vez que usa Office 365?**         LinkedIn Learning pone a su disposición vídeos gratuitos de cursos de **Office 365 admins and IT pros**.</span><span class="sxs-lookup"><span data-stu-id="84862-p120">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for **Office 365 admins and IT pros**, brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="84862-214">See also</span><span class="sxs-lookup"><span data-stu-id="84862-214">See also</span></span>
<span data-ttu-id="84862-215"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="84862-215"></span></span>

<span data-ttu-id="84862-216">Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="84862-216">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="84862-217">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="84862-217">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="84862-218">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="84862-218">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="84862-219">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="84862-219">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="84862-220">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="84862-220">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="84862-221">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="84862-221">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
<span data-ttu-id="84862-222">Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="84862-222">For more information about the cmdlets that are used in these procedures, see the following topics:</span></span>
  
- [<span data-ttu-id="84862-223">Get-Content</span><span class="sxs-lookup"><span data-stu-id="84862-223">Get-Content</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [<span data-ttu-id="84862-224">Get-MsolAccountSku</span><span class="sxs-lookup"><span data-stu-id="84862-224">Get-MsolAccountSku</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [<span data-ttu-id="84862-225">Nueva MsolLicenseOptions</span><span class="sxs-lookup"><span data-stu-id="84862-225">New-MsolLicenseOptions</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [<span data-ttu-id="84862-226">Get-MsolUser</span><span class="sxs-lookup"><span data-stu-id="84862-226">Get-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [<span data-ttu-id="84862-227">Nueva MsolUser</span><span class="sxs-lookup"><span data-stu-id="84862-227">New-MsolUser</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [<span data-ttu-id="84862-228">Conjunto de MsolUserLicense</span><span class="sxs-lookup"><span data-stu-id="84862-228">Set-MsolUserLicense</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [<span data-ttu-id="84862-229">ForEach-Object</span><span class="sxs-lookup"><span data-stu-id="84862-229">ForEach-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [<span data-ttu-id="84862-230">Where-Object</span><span class="sxs-lookup"><span data-stu-id="84862-230">Where-Object</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[<span data-ttu-id="84862-231">Volver al principio</span><span class="sxs-lookup"><span data-stu-id="84862-231">Return to top</span></span>](disable-access-to-services-with-office-365-powershell.md#RTT)
  

