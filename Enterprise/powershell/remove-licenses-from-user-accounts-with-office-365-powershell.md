---
title: Quitar licencias de 365 de Microsoft de cuentas de usuario con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explica cómo usar PowerShell para quitar licencias de 365 de Microsoft que se han asignado anteriormente a los usuarios.
ms.openlocfilehash: 5f46cfeb075d83504e3562e60e3dfd70a53dd136
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230396"
---
# <a name="remove-microsoft-365-licenses-from-user-accounts-with-powershell"></a><span data-ttu-id="ba18c-103">Quitar licencias de 365 de Microsoft de cuentas de usuario con PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba18c-103">Remove Microsoft 365 licenses from user accounts with PowerShell</span></span>

<span data-ttu-id="ba18c-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="ba18c-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="ba18c-105">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="ba18c-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="ba18c-106">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="ba18c-106">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="ba18c-107">A continuación, enumere los planes de licencia para el inquilino con este comando.</span><span class="sxs-lookup"><span data-stu-id="ba18c-107">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="ba18c-108">A continuación, obtenga el nombre de inicio de sesión de la cuenta para la que desea quitar una licencia, también conocido como nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="ba18c-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="ba18c-109">Por último, especifique los nombres de inicio de sesión y de plan de licencias de usuario, quite los caracteres "<" y ">" y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="ba18c-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

<span data-ttu-id="ba18c-110">Para quitar todas las licencias de una cuenta de usuario específica, especifique el nombre de inicio de sesión de usuario, quite los caracteres "<" y ">" y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="ba18c-110">To remove all of the licenses for a specific user account, specify the user sign-in name, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$licensePlanList = Get-AzureADSubscribedSku
$userList = Get-AzureADUser -ObjectID $userUPN | Select -ExpandProperty AssignedLicenses | Select SkuID
if($userList.Count -ne 0) {
if($userList -is [array]) {
for ($i=0; $i -lt $userList.Count; $i++) {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList[$i].SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList[$i].SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}
} else {
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = $userList.SkuId
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuID -Value $userList.SkuId -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
}}
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="ba18c-111">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba18c-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="ba18c-112">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="ba18c-112">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="ba18c-113">Para ver la información del plan de licencias (**AccountSkuID**) de su organización, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="ba18c-113">To view the licensing plan (**AccountSkuID**) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="ba18c-114">Ver licencias y servicios con PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba18c-114">View licenses and services with PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="ba18c-115">Ver los detalles de licencia y servicio de la cuenta con PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba18c-115">View account license and service details with PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="ba18c-116">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="ba18c-116">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="ba18c-117">Quitar licencias de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="ba18c-117">Removing licenses from user accounts</span></span>

<span data-ttu-id="ba18c-118">Para quitar licencias de una cuenta de usuario existente, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="ba18c-118">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="ba18c-119">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="ba18c-119">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="ba18c-120">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ba18c-120">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="ba18c-121">En este ejemplo se quita la licencia **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de la cuenta de usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="ba18c-121">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="ba18c-122">No puede usar el `Set-MsolUserLicense` cmdlet para anular la asignación de usuarios de licencias *canceladas* .</span><span class="sxs-lookup"><span data-stu-id="ba18c-122">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="ba18c-123">Debe hacerlo de forma individual para cada cuenta de usuario en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ba18c-123">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="ba18c-124">Para quitar todas las licencias de un grupo de usuarios con licencia existentes, use uno de los métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="ba18c-124">To remove all licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="ba18c-125">**Filtrar las cuentas basándose en un atributo de cuenta existente** Para ello, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="ba18c-125">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="ba18c-126">En este ejemplo se quitan todas las licencias de todas las cuentas de usuario del Departamento de ventas de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="ba18c-126">This example removes all licenses from all user accounts in the Sales department in the United States.</span></span>
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- <span data-ttu-id="ba18c-127">**Usar una lista de cuentas específicas para una licencia específica** Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="ba18c-127">**Use a list of specific accounts for a specific license** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="ba18c-128">Cree y guarde un archivo de texto que contenga una cuenta en cada línea de esta manera:</span><span class="sxs-lookup"><span data-stu-id="ba18c-128">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="ba18c-129">Utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="ba18c-129">Use the following syntax:</span></span>
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
<span data-ttu-id="ba18c-130">En este ejemplo se quita la licencia **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de las cuentas de usuario definidas en el archivo de texto c:\Mis Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="ba18c-130">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

<span data-ttu-id="ba18c-131">Para quitar todas las licencias de todas las cuentas de usuario existentes, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="ba18c-131">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="ba18c-132">Otra forma de liberar una licencia consiste en eliminar la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="ba18c-132">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="ba18c-133">Para obtener más información, vea [eliminar y restaurar cuentas de usuario con PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ba18c-133">For more information, see [Delete and restore user accounts with PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ba18c-134">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ba18c-134">See also</span></span>

[<span data-ttu-id="ba18c-135">Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba18c-135">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="ba18c-136">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="ba18c-136">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="ba18c-137">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="ba18c-137">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

