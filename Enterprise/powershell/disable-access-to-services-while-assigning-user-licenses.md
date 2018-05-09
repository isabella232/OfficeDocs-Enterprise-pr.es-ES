---
title: Deshabilitar el acceso a los servicios durante la asignación de licencias de usuario
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/07/2018
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específico al mismo tiempo mediante PowerShell de Office 365.
ms.openlocfilehash: 7567d84490cdb3db7c149a51c4f2f04d39cad9ce
ms.sourcegitcommit: def3e311db9322e469753bac59ff03624349b140
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/09/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="afb29-103">Deshabilitar el acceso a los servicios durante la asignación de licencias de usuario</span><span class="sxs-lookup"><span data-stu-id="afb29-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="afb29-104">**Resumen:**  Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específico al mismo tiempo mediante PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="afb29-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="afb29-p101">Suscripciones a Office 365 se incluyen con planes de servicio para los servicios individuales. A menudo, los administradores de Office 365 necesitan deshabilitar determinados planes al asignar licencias a los usuarios. Con las instrucciones de este artículo, puede asignar una licencia de Office 365 al deshabilitar planes de servicio específicos de uso de PowerShell para una cuenta de usuario individual o varias cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="afb29-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="afb29-108">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="afb29-108">Before you begin</span></span>

<span data-ttu-id="afb29-p102">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="afb29-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="afb29-111">Recopilar información acerca de las suscripciones y planes de servicio</span><span class="sxs-lookup"><span data-stu-id="afb29-111">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="afb29-112">Ejecute este comando para ver sus suscripciones actuales:</span><span class="sxs-lookup"><span data-stu-id="afb29-112">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="afb29-113">En la presentación de la `Get-MsolAccountSku` comando:</span><span class="sxs-lookup"><span data-stu-id="afb29-113">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="afb29-p103">**AccountSkuId** es una suscripción a su organización en \<OrganizationName >:\<suscripción > formato. El \<OrganizationName > es el valor que proporcionó cuando se inscriben en Office 365 y es único para la organización. El \<suscripción > valor es para una suscripción específica. Por ejemplo, para litwareinc: enterprisepack, el nombre de la organización es litwareinc y el nombre de la suscripción es ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="afb29-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="afb29-118">**ActiveUnits** es el número de licencias que ha comprado para la suscripción.</span><span class="sxs-lookup"><span data-stu-id="afb29-118">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="afb29-119">**WarningUnits** es el número de licencias en una suscripción que todavía no lo renueva y que caducará después del período de gracia de 30 días.</span><span class="sxs-lookup"><span data-stu-id="afb29-119">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="afb29-120">**ConsumedUnits** es el número de licencias que haya asignado a los usuarios para la suscripción.</span><span class="sxs-lookup"><span data-stu-id="afb29-120">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="afb29-p104">Tenga en cuenta la AccountSkuId para la suscripción de Office 365 que contiene los usuarios que desea licencia. Además, asegúrese de que no hay suficientes licencias para asignar (restar **ConsumedUnits** de **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="afb29-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="afb29-123">A continuación, ejecute este comando para ver los detalles acerca de los planes de servicio de Office 365 que están disponibles en todas las suscripciones:</span><span class="sxs-lookup"><span data-stu-id="afb29-123">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="afb29-124">Desde la presentación de este comando, determine qué planes de servicio que le gustaría deshabilitar al asignar licencias a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="afb29-124">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="afb29-125">Aquí es una lista parcial de los planes de servicio y sus servicios de Office 365 correspondientes.</span><span class="sxs-lookup"><span data-stu-id="afb29-125">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="afb29-126">**Plan de servicio**</span><span class="sxs-lookup"><span data-stu-id="afb29-126">**Service plan**</span></span>|<span data-ttu-id="afb29-127">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="afb29-127">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="afb29-128">INFLUIR HORA DE ELEGIR</span><span class="sxs-lookup"><span data-stu-id="afb29-128">SWAY</span></span>  <br/> |<span data-ttu-id="afb29-129">Sway</span><span class="sxs-lookup"><span data-stu-id="afb29-129">Sway</span></span>  <br/> |
|<span data-ttu-id="afb29-130">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="afb29-130">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="afb29-131">Administración de dispositivos móviles para Office 365</span><span class="sxs-lookup"><span data-stu-id="afb29-131">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="afb29-132">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="afb29-132">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="afb29-133">Yammer</span><span class="sxs-lookup"><span data-stu-id="afb29-133">Yammer</span></span>  <br/> |
|<span data-ttu-id="afb29-134">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="afb29-134">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="afb29-135">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="afb29-135">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="afb29-136">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="afb29-136">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="afb29-137">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="afb29-137">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="afb29-138">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="afb29-138">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="afb29-139">Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="afb29-139">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="afb29-140">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="afb29-140">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="afb29-141">Office Online</span><span class="sxs-lookup"><span data-stu-id="afb29-141">Office Online</span></span>  <br/> |
|<span data-ttu-id="afb29-142">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="afb29-142">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="afb29-143">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="afb29-143">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="afb29-144">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="afb29-144">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="afb29-145">Plan 2 de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="afb29-145">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="afb29-146">Ahora que tiene el AccountSkuId y los planes de servicio para deshabilitar, puede asignar licencias para un usuario individual o para varios usuarios.</span><span class="sxs-lookup"><span data-stu-id="afb29-146">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="afb29-147">Para un único usuario</span><span class="sxs-lookup"><span data-stu-id="afb29-147">For a single user</span></span>

<span data-ttu-id="afb29-p105">Para un único usuario, rellene el nombre principal de usuario de la cuenta de usuario, la AccountSkuId y la lista de planes de servicio para deshabilitar y quitar el texto explicativo y la \< y > caracteres. A continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="afb29-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$userUPN="<the user's account name in email format>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the service plans to disable> )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $usageLocation
```

<span data-ttu-id="afb29-150">Aquí es un bloque de comandos de ejemplo para la cuenta denominado belindan@contoso.com, para la licencia de contoso:ENTERPRISEPACK, y los planes de servicio para deshabilitar son RMS_S_ENTERPRISE, BALANCEO, INTUNE_O365 y YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="afb29-150">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
```
$userUPN="belindan@contoso.com"
$accountSkuId="contoso:ENTERPRISEPACK"
$planList=@( "RMS_S_ENTERPRISE","SWAY","INTUNE_O365","YAMMER_ENTERPRISE" )
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
$user=Get-MsolUser -UserPrincipalName $userUPN
$usageLocation=$user.Usagelocation
Set-MsolUserLicense -UserPrincipalName $userUpn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
Sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $userUpn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $userUpn -UsageLocation $UsageLocation
```

## <a name="for-multiple-users"></a><span data-ttu-id="afb29-151">Para varios usuarios</span><span class="sxs-lookup"><span data-stu-id="afb29-151">For multiple users</span></span>

<span data-ttu-id="afb29-p106">Para realizar esta tarea de administración para varios usuarios, cree un archivo de texto de valores separados por comas (CSV) que contiene los campos UserPrincipalName y propiedad UsageLocation. Este es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="afb29-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="afb29-154">A continuación, rellene la ubicación de la entrada y los archivos CSV de salida, la cuenta de identificador de SKU y la lista de planes de servicio para deshabilitar y, a continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="afb29-154">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$inFileName="<path and file name of the input CSV file that contains the users, example: C:\admin\Users2License.CSV>"
$outFileName="<path and file name of the output CSV file that records the results, example: C:\admin\Users2License-Done.CSV>"
$accountSkuId="<the AccountSkuId from the Get-MsolAccountSku command>"
$planList=@( <comma-separated, double-quote enclosed list of the plans to disable> )
$users=Import-Csv $inFileName
$licenseOptions=New-MsolLicenseOptions -AccountSkuId $accountSkuId -DisabledPlans $planList
ForEach ($user in $users)
{
$user.Userprincipalname
$upn=$user.UserPrincipalName
$usageLocation=$user.UsageLocation
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $AccountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="afb29-155">En este bloque de comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="afb29-155">This PowerShell command block:</span></span>
  
- <span data-ttu-id="afb29-156">Muestra el nombre principal de usuario de cada usuario.</span><span class="sxs-lookup"><span data-stu-id="afb29-156">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="afb29-157">Asigna personalizar licencias para cada usuario.</span><span class="sxs-lookup"><span data-stu-id="afb29-157">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="afb29-158">Crea un archivo CSV con todos los usuarios que se han procesado y muestra su estado de licencia.</span><span class="sxs-lookup"><span data-stu-id="afb29-158">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="afb29-159">Ver también</span><span class="sxs-lookup"><span data-stu-id="afb29-159">See also</span></span>

[<span data-ttu-id="afb29-160">Deshabilitar el acceso a servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="afb29-160">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="afb29-161">Deshabilitar el acceso a balanceo con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="afb29-161">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="afb29-162">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="afb29-162">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="afb29-163">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="afb29-163">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

