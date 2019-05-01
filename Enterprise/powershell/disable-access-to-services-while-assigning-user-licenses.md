---
title: Deshabilitar el acceso a los servicios al asignar licencias de usuario
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
ms.audience: Admin
ms.topic: article
ms.collection: Ent_O365
ms.service: o365-administration
localization_priority: Normal
ms.custom:
- PowerShell
- Ent_Office_Other
ms.assetid: bb003bdb-3c22-4141-ae3b-f0656fc23b9c
description: Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específicos al mismo tiempo mediante Office 365 PowerShell.
ms.openlocfilehash: c93f54fcd5716a0ea53290c24a2594b8bc63cecf
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491316"
---
# <a name="disable-access-to-services-while-assigning-user-licenses"></a><span data-ttu-id="5ef92-103">Deshabilitar el acceso a los servicios al asignar licencias de usuario</span><span class="sxs-lookup"><span data-stu-id="5ef92-103">Disable access to services while assigning user licenses</span></span>

<span data-ttu-id="5ef92-104">**Resumen:**  Obtenga información sobre cómo asignar licencias a cuentas de usuario y deshabilitar planes de servicio específicos al mismo tiempo mediante Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ef92-104">**Summary:**  Learn how to assign licenses to user accounts and disable specific service plans at the same time using Office 365 PowerShell.</span></span>
  
<span data-ttu-id="5ef92-105">Las suscripciones de Office 365 incluyen planes de servicio para servicios individuales.</span><span class="sxs-lookup"><span data-stu-id="5ef92-105">Office 365 subscriptions come with service plans for individual services.</span></span> <span data-ttu-id="5ef92-106">Office 365 los administradores a menudo necesitan deshabilitar determinados planes al asignar licencias a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="5ef92-106">Office 365 administrators often need to disable certain plans when assigning licenses to users.</span></span> <span data-ttu-id="5ef92-107">Con las instrucciones de este artículo, puede asignar una licencia de Office 365 y deshabilitar los planes de servicio específicos con PowerShell para una cuenta de usuario individual o varias cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="5ef92-107">With the instructions in this article, you can assign an Office 365 license while disabling specific service plans using PowerShell for an individual user account or multiple user accounts.</span></span>


## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5ef92-108">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ef92-108">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5ef92-109">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5ef92-109">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="5ef92-110">A continuación, ejecute este comando para ver sus suscripciones actuales:</span><span class="sxs-lookup"><span data-stu-id="5ef92-110">Next, run this command to see your current subscriptions:</span></span>
  
```
Get-MsolAccountSku
```

<span data-ttu-id="5ef92-111">En la pantalla del `Get-MsolAccountSku` comando:</span><span class="sxs-lookup"><span data-stu-id="5ef92-111">In the display of the  `Get-MsolAccountSku` command:</span></span>
  
- <span data-ttu-id="5ef92-112">**AccountSkuId** es una suscripción para su organización en \<el formato\<OrganizationName>: Subscription>.</span><span class="sxs-lookup"><span data-stu-id="5ef92-112">**AccountSkuId** is a subscription for your organization in \<OrganizationName>:\<Subscription> format.</span></span> <span data-ttu-id="5ef92-113">\<OrganizationName> es el valor que proporcionó cuando se inscribió en Office 365 y es único para su organización.</span><span class="sxs-lookup"><span data-stu-id="5ef92-113">The \<OrganizationName> is the value that you provided when you enrolled in Office 365, and is unique for your organization.</span></span> <span data-ttu-id="5ef92-114">El \<valor Subscription> es para una suscripción específica.</span><span class="sxs-lookup"><span data-stu-id="5ef92-114">The \<Subscription> value is for a specific subscription.</span></span> <span data-ttu-id="5ef92-115">Por ejemplo, para litwareinc: ENTERPRISEPACK, el nombre de la organización es litwareinc y el nombre de la suscripción es ENTERPRISEPACK (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="5ef92-115">For example, for litwareinc:ENTERPRISEPACK, the organization name is litwareinc, and the subscription name is ENTERPRISEPACK (Office 365 Enterprise E3).</span></span>
    
- <span data-ttu-id="5ef92-116">**ActiveUnits** es el número de licencias que ha comprado para la suscripción.</span><span class="sxs-lookup"><span data-stu-id="5ef92-116">**ActiveUnits** is the number of licenses that you've purchased for the subscription.</span></span>
    
- <span data-ttu-id="5ef92-117">**WarningUnits** es el número de licencias de una suscripción que no se renovaron y que expirarán después del período de gracia de 30 días.</span><span class="sxs-lookup"><span data-stu-id="5ef92-117">**WarningUnits** is the number of licenses in a subscription that you haven't renewed, and that will expire after the 30-day grace period.</span></span>
    
- <span data-ttu-id="5ef92-118">**ConsumedUnits** es el número de licencias que ha asignado a los usuarios para la suscripción.</span><span class="sxs-lookup"><span data-stu-id="5ef92-118">**ConsumedUnits** is the number of licenses that you've assigned to users for the subscription.</span></span>
    
<span data-ttu-id="5ef92-119">Tenga en cuenta el AccountSkuId de su suscripción de Office 365 que contiene los usuarios a los que desea conceder una licencia.</span><span class="sxs-lookup"><span data-stu-id="5ef92-119">Note the AccountSkuId for your Office 365 subscription that contains the users you want to license.</span></span> <span data-ttu-id="5ef92-120">Además, asegúrese de que hay suficientes licencias para asignar (reste **ConsumedUnits** a **ActiveUnits** ).</span><span class="sxs-lookup"><span data-stu-id="5ef92-120">Also, ensure that there are enough licenses to assign (subtract **ConsumedUnits** from **ActiveUnits** ).</span></span>
  
<span data-ttu-id="5ef92-121">A continuación, ejecute este comando para ver los detalles sobre los planes de servicio de Office 365 que están disponibles en todas las suscripciones:</span><span class="sxs-lookup"><span data-stu-id="5ef92-121">Next, run this command to see the details about the Office 365 service plans that are available in all your subscriptions:</span></span>
  
```
Get-MsolAccountSku | Select -ExpandProperty ServiceStatus
```

<span data-ttu-id="5ef92-122">En la pantalla de este comando, determine qué planes de servicio desea deshabilitar al asignar licencias a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="5ef92-122">From the display of this command, determine which service plans you would like to disable when you assign licenses to users.</span></span>
  
<span data-ttu-id="5ef92-123">A continuación se muestra una lista parcial de los planes de servicio y los servicios de Office 365 correspondientes.</span><span class="sxs-lookup"><span data-stu-id="5ef92-123">Here is a partial list of service plans and their corresponding Office 365 services.</span></span>

<span data-ttu-id="5ef92-124">En la tabla siguiente, se muestran los planes de servicio de Office 365, junto con sus nombres descriptivos, para los servicios más comunes.</span><span class="sxs-lookup"><span data-stu-id="5ef92-124">The following table shows the Office 365 service plans and their friendly names for the most common services.</span></span> <span data-ttu-id="5ef92-125">Su lista de planes de servicio puede ser diferente.</span><span class="sxs-lookup"><span data-stu-id="5ef92-125">Your list of service plans might be different.</span></span> 
  
|<span data-ttu-id="5ef92-126">**Plan de servicio**</span><span class="sxs-lookup"><span data-stu-id="5ef92-126">**Service plan**</span></span>|<span data-ttu-id="5ef92-127">**Descripción**</span><span class="sxs-lookup"><span data-stu-id="5ef92-127">**Description**</span></span>|
|:-----|:-----|
| `SWAY` <br/> |<span data-ttu-id="5ef92-128">Sway</span><span class="sxs-lookup"><span data-stu-id="5ef92-128">Sway</span></span>  <br/> |
| `TEAMS1` <br/> |<span data-ttu-id="5ef92-129">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5ef92-129">Microsoft Teams</span></span>  <br/> |
| `YAMMER_ENTERPRISE` <br/> |<span data-ttu-id="5ef92-130">Yammer</span><span class="sxs-lookup"><span data-stu-id="5ef92-130">Yammer</span></span>  <br/> |
| `RMS_S_ENTERPRISE` <br/> |<span data-ttu-id="5ef92-131">Azure Rights Management (RMS)</span><span class="sxs-lookup"><span data-stu-id="5ef92-131">Azure Rights Management (RMS)</span></span>  <br/> |
| `OFFICESUBSCRIPTION` <br/> |<span data-ttu-id="5ef92-132">Office Professional Plus</span><span class="sxs-lookup"><span data-stu-id="5ef92-132">Office Professional Plus</span></span>  <br/> |
| `MCOSTANDARD` <br/> |<span data-ttu-id="5ef92-133">Skype Empresarial Online</span><span class="sxs-lookup"><span data-stu-id="5ef92-133">Skype for Business Online</span></span>  <br/> |
| `SHAREPOINTWAC` <br/> |<span data-ttu-id="5ef92-134">Office Online</span><span class="sxs-lookup"><span data-stu-id="5ef92-134">Office Online</span></span>  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |<span data-ttu-id="5ef92-135">SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="5ef92-135">SharePoint Online</span></span>  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |<span data-ttu-id="5ef92-136">Plan 2 de Exchange Online</span><span class="sxs-lookup"><span data-stu-id="5ef92-136">Exchange Online Plan 2</span></span>  <br/> |
   
<span data-ttu-id="5ef92-137">Para obtener una lista completa de los planes de licencia (también conocidos como nombres de producto), sus planes de servicio incluidos y los nombres descriptivos correspondientes, consulte [Product Names and Service Plan Identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span><span class="sxs-lookup"><span data-stu-id="5ef92-137">For a complete list of license plans (also known as product names), their included service plans, and their corresponding friendly names, see [Product names and service plan identifiers for licensing](https://docs.microsoft.com/azure/active-directory/users-groups-roles/licensing-service-plan-reference).</span></span>
   
<span data-ttu-id="5ef92-138">Ahora que tiene los planes de AccountSkuId y servicio para deshabilitar, puede asignar licencias para un usuario individual o para varios usuarios.</span><span class="sxs-lookup"><span data-stu-id="5ef92-138">Now that you have the AccountSkuId and the service plans to disable, you can assign licenses for an individual user or for multiple users.</span></span>
  
### <a name="for-a-single-user"></a><span data-ttu-id="5ef92-139">Para un solo usuario</span><span class="sxs-lookup"><span data-stu-id="5ef92-139">For a single user</span></span>

<span data-ttu-id="5ef92-140">Para un solo usuario, escriba el nombre principal de usuario de la cuenta de usuario, el AccountSkuId y la lista de planes de servicio para deshabilitar y quitar el texto explicativo y los \< caracteres y >.</span><span class="sxs-lookup"><span data-stu-id="5ef92-140">For a single user, fill in the user principal name of the user account, the AccountSkuId, and the list of service plans to disable and remove the explanatory text and the \< and > characters.</span></span> <span data-ttu-id="5ef92-141">A continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ef92-141">Then, run the resulting commands at the PowerShell command prompt.</span></span>
  
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

<span data-ttu-id="5ef92-142">Este es un ejemplo de bloque de comandos para la cuenta denominada belindan@contoso.com, para la licencia de Contoso: ENTERPRISEPACK, y los planes de servicio que se van a deshabilitar son RMS_S_ENTERPRISE, SWAY, INTUNE_O365 y YAMMER_ENTERPRISE:</span><span class="sxs-lookup"><span data-stu-id="5ef92-142">Here is an example command block for the account named belindan@contoso.com, for the contoso:ENTERPRISEPACK license, and the service plans to disable are RMS_S_ENTERPRISE, SWAY, INTUNE_O365, and YAMMER_ENTERPRISE:</span></span>
  
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

### <a name="for-multiple-users"></a><span data-ttu-id="5ef92-143">Para varios usuarios</span><span class="sxs-lookup"><span data-stu-id="5ef92-143">For multiple users</span></span>

<span data-ttu-id="5ef92-144">Para realizar esta tarea de administración para varios usuarios, cree un archivo de texto de valores separados por comas (CSV) que contenga los campos UserPrincipalName y UsageLocation.</span><span class="sxs-lookup"><span data-stu-id="5ef92-144">To perform this administration task for multiple users, create a comma-separated value (CSV) text file that contains the UserPrincipalName and UsageLocation fields.</span></span> <span data-ttu-id="5ef92-145">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5ef92-145">Here is an example:</span></span>
  
```
UserPrincipalName,UsageLocation
ClaudeL@contoso.onmicrosoft.com,FR
LynneB@contoso.onmicrosoft.com,US
ShawnM@contoso.onmicrosoft.com,US
```

<span data-ttu-id="5ef92-146">A continuación, rellene la ubicación de los archivos CSV de entrada y salida, el identificador de SKU de cuenta y la lista de planes de servicio que se van a deshabilitar y, a continuación, ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5ef92-146">Next, fill in the location of the input and output CSV files, the account SKU ID, and the list of service plans to disable, and then run the resulting commands at the PowerShell command prompt.</span></span>
  
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
Set-MsolUserLicense -UserPrincipalName $upn -AddLicenses $accountSkuId -ErrorAction SilentlyContinue
sleep -Seconds 5
Set-MsolUserLicense -UserPrincipalName $upn -LicenseOptions $licenseOptions -ErrorAction SilentlyContinue
Set-MsolUser -UserPrincipalName $upn -UsageLocation $usageLocation
$users | Get-MsolUser | Select UserPrincipalName, Islicensed,Usagelocation | Export-Csv $outFileName
}
```

<span data-ttu-id="5ef92-147">Este bloque de comandos de PowerShell:</span><span class="sxs-lookup"><span data-stu-id="5ef92-147">This PowerShell command block:</span></span>
  
- <span data-ttu-id="5ef92-148">Muestra el nombre principal de usuario de cada usuario.</span><span class="sxs-lookup"><span data-stu-id="5ef92-148">Displays the user principal name of each user.</span></span>
    
- <span data-ttu-id="5ef92-149">Asigna licencias personalizadas a cada usuario.</span><span class="sxs-lookup"><span data-stu-id="5ef92-149">Assigns customized licenses to each user.</span></span>
    
- <span data-ttu-id="5ef92-150">Crea un archivo CSV con todos los usuarios que se procesaron y muestra su estado de licencia.</span><span class="sxs-lookup"><span data-stu-id="5ef92-150">Creates a CSV file with all the users that were processed and shows their license status.</span></span>
    
## <a name="see-also"></a><span data-ttu-id="5ef92-151">Vea también</span><span class="sxs-lookup"><span data-stu-id="5ef92-151">See also</span></span>

[<span data-ttu-id="5ef92-152">Deshabilitar el acceso a servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5ef92-152">Disable access to services with Office 365 PowerShell</span></span>](disable-access-to-services-with-office-365-powershell.md)
  
[<span data-ttu-id="5ef92-153">Deshabilitar el acceso a Sway con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5ef92-153">Disable access to Sway with Office 365 PowerShell</span></span>](disable-access-to-sway-with-office-365-powershell.md)
  
[<span data-ttu-id="5ef92-154">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5ef92-154">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5ef92-155">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5ef92-155">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)

