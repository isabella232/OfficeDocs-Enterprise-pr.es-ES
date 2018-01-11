---
title: Deshabilitar el acceso a los servicios al asignar licencias de usuario
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: "Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específico al mismo tiempo el uso de PowerShell de Office 365."
ms.openlocfilehash: 96ce12f811ee147a92da6b6928c2f6e3391c9b1f
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="2aa61-103">Deshabilitar el acceso a los servicios al asignar licencias de usuario</span><span class="sxs-lookup"><span data-stu-id="2aa61-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="2aa61-104">**Resumen:**  Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específico al mismo tiempo el uso de PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="2aa61-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="2aa61-p101">Suscripciones a Office 365 cuentan con planes de servicio para los servicios individuales. A menudo, los administradores de Office 365 necesitan deshabilitar ciertos planes al asignar licencias a los usuarios. Con las instrucciones de este artículo, puede asignar una licencia de Office 365 al deshabilitar el uso de PowerShell para un usuario individual o varias cuentas de usuario de planes de servicio específico.</span><span class="sxs-lookup"><span data-stu-id="2aa61-p101">Office 365 subscriptions come with service plans for individual services. Office 365 administrators often need to disable certain plans when assigning licenses to users. With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>
  
> [!NOTE]
> <span data-ttu-id="2aa61-108">En este artículo se basa en el trabajo de Siddhartha Parmar, un ingeniero de escalamiento de soporte de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2aa61-108">This article is based on the work of Siddhartha Parmar, a Microsoft Support Escalation Engineer.</span></span> 
  
## <a name="before-you-begin"></a><span data-ttu-id="2aa61-109">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="2aa61-109">Before you begin</span></span>

<span data-ttu-id="2aa61-p102">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="2aa61-p102">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="collect-information-about-subscriptions-and-service-plans"></a><span data-ttu-id="2aa61-112">Recopilar información sobre suscripciones y planes de servicio</span><span class="sxs-lookup"><span data-stu-id="2aa61-112">Collect information about subscriptions and service plans</span></span>

<span data-ttu-id="2aa61-113">Ejecute este comando para ver sus suscripciones actuales:</span><span class="sxs-lookup"><span data-stu-id="2aa61-113">Run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="2aa61-114">En la presentación de la `Get-MsolAccountSku` comando:</span><span class="sxs-lookup"><span data-stu-id="2aa61-114">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="2aa61-p103">**AccountSkuId** es una suscripción para su organización en \<NombreDeOrganización >:\<suscripción > formato. El \<NombreDeOrganización > es el valor que proporciona cuando se inscribe en Office 365 y es exclusivo para su organización. El \<suscripción > es el valor de una suscripción específica. Por ejemplo, para litwareinc:ENTERPRISEPACK, el nombre de la organización es litwareinc y el nombre de la suscripción es ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="2aa61-p103">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format. The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization. The \<Subscription> value is for a specific subscription. For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="2aa61-119">**ActiveUnits** es el número de licencias que ha adquirido para la suscripción.</span><span class="sxs-lookup"><span data-stu-id="2aa61-119">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="2aa61-120">**WarningUnits** es el número de licencias en una suscripción que usted no ha renovado y que caducará después del período de gracia de 30 días.</span><span class="sxs-lookup"><span data-stu-id="2aa61-120">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="2aa61-121">**ConsumedUnits** es el número de licencias que haya asignado a los usuarios para la suscripción.</span><span class="sxs-lookup"><span data-stu-id="2aa61-121">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="2aa61-p104">Tenga en cuenta el AccountSkuId de la suscripción de Office 365 que contiene los usuarios que desea licencia. Además, asegúrese de que hay suficientes licencias para asignar (restar **ConsumedUnits** de **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="2aa61-p104">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license. Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="2aa61-124">A continuación, ejecute este comando para ver los detalles acerca de los planes de servicio de Office 365 que están disponibles en todas las suscripciones:</span><span class="sxs-lookup"><span data-stu-id="2aa61-124">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="2aa61-125">En la pantalla de este comando, determinar qué planes de servicio que le gustaría deshabilitar al asignar licencias a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="2aa61-125">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="2aa61-126">Aquí es una lista parcial de los planes de servicio y sus correspondientes servicios de Office 365.</span><span class="sxs-lookup"><span data-stu-id="2aa61-126">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>
  
|<span data-ttu-id="2aa61-127">**Plan de servicio**</span><span class="sxs-lookup"><span data-stu-id="2aa61-127">**Service plan**</span></span>|<span data-ttu-id="2aa61-128">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="2aa61-128">**Description**</span></span>|
|:-----|:-----|
|<span data-ttu-id="2aa61-129">BALANCEO</span><span class="sxs-lookup"><span data-stu-id="2aa61-129">SWAY</span></span>  <br/> |<span data-ttu-id="2aa61-130">Sway</span><span class="sxs-lookup"><span data-stu-id="2aa61-130">Sway</span></span>  <br/> |
|<span data-ttu-id="2aa61-131">INTUNE_O365</span><span class="sxs-lookup"><span data-stu-id="2aa61-131">INTUNE_O365</span></span>  <br/> |<span data-ttu-id="2aa61-132">Administración de dispositivos móviles para Office 365</span><span class="sxs-lookup"><span data-stu-id="2aa61-132">Mobile Device Management for Office 365</span></span>  <br/> |
|<span data-ttu-id="2aa61-133">YAMMER_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="2aa61-133">YAMMER_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="2aa61-134">Yammer</span><span class="sxs-lookup"><span data-stu-id="2aa61-134">Yammer</span></span>  <br/> |
|<span data-ttu-id="2aa61-135">RMS_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="2aa61-135">RMS_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="2aa61-136">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="2aa61-136">Azure Rights Management (RMS)</span></span>  <br/> |
|<span data-ttu-id="2aa61-137">OFFICESUBSCRIPTION</span><span class="sxs-lookup"><span data-stu-id="2aa61-137">OFFICESUBSCRIPTION</span></span>  <br/> |<span data-ttu-id="2aa61-138">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="2aa61-138">Office Professional Plus</span></span>  <br/> |
|<span data-ttu-id="2aa61-139">MCOSTANDARD</span><span class="sxs-lookup"><span data-stu-id="2aa61-139">MCOSTANDARD</span></span>  <br/> |<span data-ttu-id="2aa61-140">Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="2aa61-140">Skype for Business Online</span></span>  <br/> |
|<span data-ttu-id="2aa61-141">SHAREPOINTWAC</span><span class="sxs-lookup"><span data-stu-id="2aa61-141">SHAREPOINTWAC</span></span>  <br/> |<span data-ttu-id="2aa61-142">Office Online</span><span class="sxs-lookup"><span data-stu-id="2aa61-142">Office Online</span></span>  <br/> |
|<span data-ttu-id="2aa61-143">SHAREPOINTENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="2aa61-143">SHAREPOINTENTERPRISE</span></span>  <br/> |<span data-ttu-id="2aa61-144">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="2aa61-144">SharePoint Online</span></span>  <br/> |
|<span data-ttu-id="2aa61-145">EXCHANGE_S_ENTERPRISE</span><span class="sxs-lookup"><span data-stu-id="2aa61-145">EXCHANGE_S_ENTERPRISE</span></span>  <br/> |<span data-ttu-id="2aa61-146">Plan 2 de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="2aa61-146">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="2aa61-147">Ahora que tiene el AccountSkuId y los planes de servicio para deshabilitar, puede asignar licencias para un usuario individual o para varios usuarios.</span><span class="sxs-lookup"><span data-stu-id="2aa61-147">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
## <a name="for-a-single-user"></a><span data-ttu-id="2aa61-148">Para un único usuario</span><span class="sxs-lookup"><span data-stu-id="2aa61-148">For a single user</span></span>

<span data-ttu-id="2aa61-p105">Para un solo usuario, rellene el nombre principal de usuario de la cuenta de usuario, la AccountSkuId y la lista de planes de servicio para deshabilitar y quitar el texto explicativo y los \< y > caracteres. A continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2aa61-p105">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters. Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="2aa61-151">Aquí es un bloque de comandos de ejemplo para la cuenta denominada belindan@contoso.com, para la licencia de contoso:ENTERPRISEPACK, y los planes de servicio para deshabilitar son RMS_S_ENTERPRISE, SWAY, INTUNE_O365 y YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="2aa61-151">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
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

## <a name="for-multiple-users"></a><span data-ttu-id="2aa61-152">Para varios usuarios</span><span class="sxs-lookup"><span data-stu-id="2aa61-152">For multiple users</span></span>

<span data-ttu-id="2aa61-p106">Para realizar esta tarea de administración de varios usuarios, cree un archivo de texto de valores separados por comas (CSV) que contiene los campos UserPrincipalName y UsageLocation. Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="2aa61-p106">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields. Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="2aa61-155">A continuación, especifique la ubicación de la entrada y salida CSV archivos, la cuenta ID de SKU y la lista de planes de servicio para deshabilitar y, a continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2aa61-155">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="2aa61-156">Este bloque de comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="2aa61-156">This PowerShell command block:</span></span>
  
- <span data-ttu-id="2aa61-157">Muestra el nombre principal de usuario de cada usuario.</span><span class="sxs-lookup"><span data-stu-id="2aa61-157">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="2aa61-158">Asigna personalizar licencias para cada usuario.</span><span class="sxs-lookup"><span data-stu-id="2aa61-158">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="2aa61-159">Crea un archivo CSV con todos los usuarios que se han procesado y muestra su estado de licencia.</span><span class="sxs-lookup"><span data-stu-id="2aa61-159">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="2aa61-160">Consulte también</span><span class="sxs-lookup"><span data-stu-id="2aa61-160">See also</span></span>

#### 

[<span data-ttu-id="2aa61-161">Deshabilitar el acceso a servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2aa61-161">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="2aa61-162">Deshabilitar el acceso al dominio con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2aa61-162">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="2aa61-163">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2aa61-163">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="2aa61-164">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2aa61-164">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

