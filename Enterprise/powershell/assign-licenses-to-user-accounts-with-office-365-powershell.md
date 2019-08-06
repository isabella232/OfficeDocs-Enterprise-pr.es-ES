---
title: Asignar licencias a cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/05/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- LIL_Placement
- PowerShell
- O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
search.appverid:
- MET150
description: Cómo usar Office 365 PowerShell para asignar una licencia de Office 365 a los usuarios sin licencia.
ms.openlocfilehash: c244e60016cb04008e27e2df444703ac7e41db12
ms.sourcegitcommit: 6c3003380491fba6dacb299754716901c20ba629
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/05/2019
ms.locfileid: "36198652"
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="95686-103">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="95686-103">Assign licenses to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="95686-104">**Resumen:**  Cómo usar Office 365 PowerShell para asignar una licencia de Office 365 a los usuarios sin licencia.</span><span class="sxs-lookup"><span data-stu-id="95686-104">**Summary:**  How to use Office 365 PowerShell to assign an Office 365 license to unlicensed users.</span></span>
  
<span data-ttu-id="95686-105">Los usuarios no pueden usar ningún servicio de Office 365 hasta que su cuenta tenga asignada una licencia de un plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="95686-105">Users can't use any Office 365 services until their account has been assigned a license from a licensing plan.</span></span> <span data-ttu-id="95686-106">Puede usar Office 365 PowerShell para asignar licencias rápidamente a cuentas sin licencia.</span><span class="sxs-lookup"><span data-stu-id="95686-106">You can use Office 365 PowerShell to quickly assign licenses to unlicensed accounts.</span></span> 

>[!Note]
><span data-ttu-id="95686-107">Las cuentas de usuario deben tener asignada una ubicación.</span><span class="sxs-lookup"><span data-stu-id="95686-107">User accounts must be assigned a location.</span></span> <span data-ttu-id="95686-108">Puede hacerlo desde las propiedades de una cuenta de usuario en el centro de administración de Microsoft 365 o desde PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95686-108">You can do this from the properties of a user account in the Microsoft 365 admin center or from PowerShell.</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="95686-109">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="95686-109">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="95686-110">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="95686-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="95686-111">A continuación, enumere los planes de licencia para el inquilino con este comando.</span><span class="sxs-lookup"><span data-stu-id="95686-111">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="95686-112">A continuación, obtenga el nombre de inicio de sesión de la cuenta a la que desea agregar una licencia, también conocida como nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="95686-112">Next, get the sign-in name of the account to which you want add a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="95686-113">A continuación, asegúrese de que la cuenta de usuario tiene asignada una ubicación de uso.</span><span class="sxs-lookup"><span data-stu-id="95686-113">Next, ensure that the user account has a usage location assigned.</span></span>

```
Get-AzureADUser -ObjectID <user sign-in name (UPN)> | Select DisplayName, UsageLocation
```

<span data-ttu-id="95686-114">Si no hay ninguna ubicación de uso asignada, puede asignar una con estos comandos:</span><span class="sxs-lookup"><span data-stu-id="95686-114">If there is no usage location assigned, you can assign one with these commands:</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$userLoc="<ISO 3166-1 alpha-2 country code>"
Set-AzureADUser -ObjectID $userUPN -UsageLocation $userLoc
```

<span data-ttu-id="95686-115">Por último, especifique el nombre de inicio de sesión del usuario y el nombre del plan de licencia y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="95686-115">Finally, specify the user sign-in name and license plan name and run these commands.</span></span>

```
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="95686-116">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="95686-116">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="95686-117">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="95686-117">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="95686-118">Ejecute el comando **Get-MsolAccountSku** para ver los planes de licencias disponibles y el número de licencias disponibles en cada plan de la organización.</span><span class="sxs-lookup"><span data-stu-id="95686-118">Run the **Get-MsolAccountSku** command to view the available licensing plans and the number of available licenses in each plan in your organization.</span></span> <span data-ttu-id="95686-119">El número de licencias disponibles en cada plan es **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span><span class="sxs-lookup"><span data-stu-id="95686-119">The number of available licenses in each plan is **ActiveUnits** - **WarningUnits** - **ConsumedUnits**.</span></span> <span data-ttu-id="95686-120">Para obtener más información acerca de los planes de licencias, las licencias y los servicios, consulte [ver licencias y servicios con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="95686-120">For more information about licensing plans, licenses, and services, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="95686-121">Para buscar las cuentas sin licencia de la organización, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="95686-121">To find the unlicensed accounts in your organization, run this command.</span></span>

```
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="95686-122">Solo se pueden asignar licencias a cuentas de usuario que tengan la propiedad **UsageLocation** establecida en un código de país ISO 3166-1 alpha-2 válido.</span><span class="sxs-lookup"><span data-stu-id="95686-122">You can only assign licenses to user accounts that have the **UsageLocation** property set to a valid ISO 3166-1 alpha-2 country code.</span></span> <span data-ttu-id="95686-123">Por ejemplo, US para Estados Unidos y FR para Francia.</span><span class="sxs-lookup"><span data-stu-id="95686-123">For example, US for the United States, and FR for France.</span></span> <span data-ttu-id="95686-124">Algunos servicios de Office 365 no están disponibles en determinados países.</span><span class="sxs-lookup"><span data-stu-id="95686-124">Some Office 365 services aren't available in certain countries.</span></span> <span data-ttu-id="95686-125">Para obtener más información, consulte [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span><span class="sxs-lookup"><span data-stu-id="95686-125">For more information, see [About license restrictions](https://go.microsoft.com/fwlink/p/?LinkId=691730).</span></span>
    
<span data-ttu-id="95686-126">Para buscar las cuentas que no tienen un valor **UsageLocation** , ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="95686-126">To find accounts that don't have a **UsageLocation** value, run this command.</span></span>

```
Get-MsolUser -All | where {$_.UsageLocation -eq $null}
```

<span data-ttu-id="95686-127">Para establecer el valor **UsageLocation** en una cuenta, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="95686-127">To set the **UsageLocation** value on an account, run this command.</span></span>

```
Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>
```

<span data-ttu-id="95686-128">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="95686-128">For example:</span></span>

```
Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US
```
    
<span data-ttu-id="95686-129">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro **All**, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="95686-129">If you use the **Get-MsolUser** cmdlet without using the **-All** parameter, only the first 500 accounts are returned.</span></span>

### <a name="assigning-licenses-to-user-accounts"></a><span data-ttu-id="95686-130">Asignar licencias a cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="95686-130">Assigning licenses to user accounts</span></span>
    
<span data-ttu-id="95686-131">Para asignar una licencia a un usuario, use el siguiente comando en Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="95686-131">To assign a license to a user, use the following command in Office 365 PowerShell.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

<span data-ttu-id="95686-132">En este ejemplo se asigna una licencia desde el plan de licencias **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) al usuario sin licencia **belindan@litwareinc.com**:</span><span class="sxs-lookup"><span data-stu-id="95686-132">This example assigns a license from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to the unlicensed user **belindan@litwareinc.com**:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="95686-133">Para asignar una licencia a muchos usuarios sin licencia, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="95686-133">To assign a license to many unlicensed users, run this command.</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>] | Set-MsolUserLicense -AddLicenses "<AccountSkuId>"
```
  
>[!Note]
><span data-ttu-id="95686-134">No se pueden asignar varias licencias a un usuario desde el mismo plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="95686-134">You can't assign multiple licenses to a user from the same licensing plan.</span></span> <span data-ttu-id="95686-135">Si no dispone de licencias suficientes, las licencias se asignan a los usuarios en el orden en que los devuelve el cmdlet **Get-MsolUser** hasta que se agoten las licencias disponibles.</span><span class="sxs-lookup"><span data-stu-id="95686-135">If you don't have enough available licenses, the licenses are assigned to users in the order that they're returned by the **Get-MsolUser** cmdlet until the available licenses run out.</span></span>
>

<span data-ttu-id="95686-136">En este ejemplo se asignan licencias desde el plan de licencias **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) a todos los usuarios sin licencia:</span><span class="sxs-lookup"><span data-stu-id="95686-136">This example assigns licenses from the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licensing plan to all unlicensed users:</span></span>
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="95686-137">En este ejemplo se asignan las mismas licencias a los usuarios sin licencia del Departamento de ventas de Estados Unidos:</span><span class="sxs-lookup"><span data-stu-id="95686-137">This example assigns those same licenses to unlicensed users in the Sales department in the United States:</span></span>
  
```
Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```
  
## <a name="new-to-office-365"></a><span data-ttu-id="95686-138">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="95686-138">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a><span data-ttu-id="95686-139">Consulte también</span><span class="sxs-lookup"><span data-stu-id="95686-139">See also</span></span>

[<span data-ttu-id="95686-140">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="95686-140">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="95686-141">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="95686-141">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="95686-142">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="95686-142">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
