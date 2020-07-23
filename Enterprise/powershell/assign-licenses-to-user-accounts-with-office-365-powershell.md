---
title: Asignar licencias de 365 de Microsoft a cuentas de usuario con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Cómo usar PowerShell para asignar una licencia de Microsoft 365 a los usuarios sin licencia.
ms.openlocfilehash: 25a57158be82f985885a7ceaf89f526f9d522b4d
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45229836"
---
# <a name="assign-microsoft-365-licenses-to-user-accounts-with-powershell"></a><span data-ttu-id="abad3-103">Asignar licencias de 365 de Microsoft a cuentas de usuario con PowerShell</span><span class="sxs-lookup"><span data-stu-id="abad3-103">Assign Microsoft 365 licenses to user accounts with PowerShell</span></span>

<span data-ttu-id="abad3-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="abad3-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="abad3-105">Los usuarios no pueden usar ninguno de los servicios de Microsoft 365 hasta que su cuenta tenga asignada una licencia de un plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="abad3-105">Users can't use any Microsoft 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="abad3-106">Puede usar PowerShell para asignar licencias rápidamente a cuentas sin licencia.</span><span class="sxs-lookup"><span data-stu-id="abad3-106">You can use PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="abad3-107">Las cuentas de usuario deben tener asignada una ubicación.</span><span class="sxs-lookup"><span data-stu-id="abad3-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="abad3-108">Puede hacerlo desde las propiedades de una cuenta de usuario en el centro de administración de Microsoft 365 o desde PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abad3-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="abad3-109">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="abad3-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="abad3-110">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="abad3-110">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="abad3-111">A continuación, enumere los planes de licencia para el inquilino con este comando.</span><span class="sxs-lookup"><span data-stu-id="abad3-111">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="abad3-112">A continuación, obtenga el nombre de inicio de sesión de la cuenta a la que desea agregar una licencia, también conocida como nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="abad3-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="abad3-113">A continuación, asegúrese de que la cuenta de usuario tiene asignada una ubicación de uso.</span><span class="sxs-lookup"><span data-stu-id="abad3-113">Next, ensure that the user account has a usage location assigned.</span></span>

```powershell
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="abad3-114">Si no hay ninguna ubicación de uso asignada, puede asignar una con estos comandos:</span><span class="sxs-lookup"><span data-stu-id="abad3-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="abad3-115">Por último, especifique el nombre de inicio de sesión del usuario y el nombre del plan de licencia y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="abad3-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="abad3-116">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="abad3-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="abad3-117">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="abad3-117">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="abad3-118">Ejecute el `Get-MsolAccountSku` comando para ver los planes de licencias disponibles y el número de licencias disponibles en cada plan de la organización.</span><span class="sxs-lookup"><span data-stu-id="abad3-118">Run the `Get-MsolAccountSku` command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="abad3-119">El número de licencias disponibles en cada plan es **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="abad3-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="abad3-120">Para obtener más información acerca de los planes de licencias, las licencias y los servicios, consulte [ver licencias y servicios con PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="abad3-120">For more information about licensing plans, licenses, and services, see [View licenses and services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>

>[!Note]
><span data-ttu-id="abad3-121">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="abad3-121">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="abad3-122">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abad3-122">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="abad3-123">Para buscar las cuentas sin licencia de la organización, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="abad3-123">To find the unlicensed accounts in your organization, run this command.</span></span>

```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="abad3-124">Solo se pueden asignar licencias a cuentas de usuario que tengan la propiedad **UsageLocation** establecida en un código de país ISO 3166-1 alpha-2 válido.</span><span class="sxs-lookup"><span data-stu-id="abad3-124">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="abad3-125">Por ejemplo, US para Estados Unidos y FR para Francia.</span><span class="sxs-lookup"><span data-stu-id="abad3-125">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="abad3-126">Algunos servicios de Microsoft 365 no están disponibles en determinados países.</span><span class="sxs-lookup"><span data-stu-id="abad3-126">Some Microsoft 365 services aren't available in certain countries.</span></span> <span data-ttu-id="abad3-127">Para obtener más información, consulte [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="abad3-127">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="abad3-128">Para buscar las cuentas que no tienen un valor **UsageLocation** , ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="abad3-128">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```powershell
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="abad3-129">Para establecer el valor **UsageLocation** en una cuenta, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="abad3-129">To set the **UsageLocation** value on an account, run this command.</span></span>

```powershell
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="abad3-130">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="abad3-130">For example:</span></span>

```powershell
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="abad3-131">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro **All**, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="abad3-131">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="abad3-132">Asignar licencias a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="abad3-132">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="abad3-133">Para asignar una licencia a un usuario, use el siguiente comando en PowerShell.</span><span class="sxs-lookup"><span data-stu-id="abad3-133">To assign a license to a user, use the following command in PowerShell.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="abad3-134">En este ejemplo se asigna una licencia desde el plan de licencias **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) al usuario sin licencia \*\* \@ litwareinc.com\*\*:</span><span class="sxs-lookup"><span data-stu-id="abad3-134">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan\@litwareinc.com**:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="abad3-135">Para asignar una licencia a todos los usuarios sin licencia, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="abad3-135">To assign a license to all unlicensed users, run this command.</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="abad3-136">No se pueden asignar varias licencias a un usuario desde el mismo plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="abad3-136">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="abad3-137">Si no dispone de licencias suficientes, las licencias se asignan a los usuarios en el orden en que los devuelve el cmdlet **Get-MsolUser** hasta que se agoten las licencias disponibles.</span><span class="sxs-lookup"><span data-stu-id="abad3-137">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="abad3-138">En este ejemplo se asignan licencias desde el plan de licencias **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a todos los usuarios sin licencia:</span><span class="sxs-lookup"><span data-stu-id="abad3-138">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="abad3-139">En este ejemplo se asignan las mismas licencias a los usuarios sin licencia del Departamento de ventas de Estados Unidos:</span><span class="sxs-lookup"><span data-stu-id="abad3-139">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```powershell
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="move-a-user-to-a-different-subscription-license-plan-with-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="abad3-140">Mover un usuario a una suscripción diferente (plan de licencia) con el módulo Azure Active Directory PowerShell para Graph</span><span class="sxs-lookup"><span data-stu-id="abad3-140">Move a user to a different subscription (license plan) with the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="abad3-141">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="abad3-141">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
<span data-ttu-id="abad3-142">A continuación, obtenga el nombre de inicio de sesión de la cuenta de usuario para la que desea cambiar las suscripciones, también conocido como nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="abad3-142">Next, get the sign-in name of the user account for which you want switch subscriptions, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="abad3-143">A continuación, enumere las suscripciones (planes de licencia) para el inquilino con este comando.</span><span class="sxs-lookup"><span data-stu-id="abad3-143">Next, list the subscriptions (license plans) for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="abad3-144">A continuación, enumere las suscripciones que la cuenta de usuario tiene actualmente con estos comandos.</span><span class="sxs-lookup"><span data-stu-id="abad3-144">Next, list the subscriptions that the user account currently has with these commands.</span></span>

```powershell
$userUPN="<user account UPN>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

<span data-ttu-id="abad3-145">Identifique la suscripción que el usuario tiene actualmente (la suscripción de) y la suscripción a la que está moviendo el usuario (la suscripción a).</span><span class="sxs-lookup"><span data-stu-id="abad3-145">Identify the subscription the user currently has (the FROM subscription) and the subscription to which the user is moving (the TO subscription).</span></span>

<span data-ttu-id="abad3-146">Por último, especifique los nombres de suscripción para y de (números de parte de SKU) y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="abad3-146">Finally, specify the TO and FROM subscription names (SKU part numbers) and run these commands.</span></span>

```powershell
$subscriptionFrom="<SKU part number of the current subscription>"
$subscriptionTo="<SKU part number of the new subscription>"
# Unassign
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$licenses.AddLicenses = @()
$licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionFrom -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
# Assign
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $subscriptionTo -EQ).SkuID
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$licenses.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

<span data-ttu-id="abad3-147">Puede comprobar el cambio de suscripción de la cuenta de usuario con estos comandos.</span><span class="sxs-lookup"><span data-stu-id="abad3-147">You can verify the change in subscription for the user account with these commands.</span></span>

```powershell
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID 
$userList | ForEach { $sku=$_.SkuId ; $licensePlanList | ForEach { If ( $sku -eq $_.ObjectId.substring($_.ObjectId.length - 36, 36) ) { Write-Host $_.SkuPartNumber } } }
```

## <a name="see-also"></a><span data-ttu-id="abad3-148">Consulte también</span><span class="sxs-lookup"><span data-stu-id="abad3-148">See also</span></span>

[<span data-ttu-id="abad3-149">Administrar cuentas de usuario, licencias y grupos con PowerShell</span><span class="sxs-lookup"><span data-stu-id="abad3-149">Manage user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="abad3-150">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="abad3-150">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="abad3-151">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="abad3-151">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
