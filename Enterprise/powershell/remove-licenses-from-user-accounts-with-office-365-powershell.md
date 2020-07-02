---
title: Eliminar licencias de cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/30/2020
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
description: Explica cómo usar Office 365 PowerShell para quitar licencias de Office 365 que se han asignado anteriormente a los usuarios.
ms.openlocfilehash: 0b21415b5acbd2c332d9bc171a5ab80cb7954b95
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44997416"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="be7b1-103">Eliminar licencias de cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="be7b1-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="be7b1-104">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="be7b1-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="be7b1-105">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="be7b1-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="be7b1-106">A continuación, enumere los planes de licencia para el inquilino con este comando.</span><span class="sxs-lookup"><span data-stu-id="be7b1-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="be7b1-107">A continuación, obtenga el nombre de inicio de sesión de la cuenta para la que desea quitar una licencia, también conocido como nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="be7b1-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="be7b1-108">Por último, especifique los nombres de inicio de sesión y de plan de licencias de usuario, quite los caracteres "<" y ">" y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="be7b1-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$License.RemoveLicenses = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $license
```

<span data-ttu-id="be7b1-109">Para quitar todas las licencias de una cuenta de usuario específica, especifique el nombre de inicio de sesión de usuario, quite los caracteres "<" y ">" y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="be7b1-109">To remove all of the licenses for a specific user account, specify the user sign-in name, remove the "<" and ">" characters, and run these commands.</span></span>

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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="be7b1-110">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="be7b1-110">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="be7b1-111">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="be7b1-111">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="be7b1-112">Para ver la información del plan de licencias (**AccountSkuID**) de su organización, vea los temas siguientes:</span><span class="sxs-lookup"><span data-stu-id="be7b1-112">To view the licensing plan (**AccountSkuID**) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="be7b1-113">Ver las licencias y los servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="be7b1-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="be7b1-114">Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="be7b1-114">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="be7b1-115">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="be7b1-115">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="be7b1-116">Quitar licencias de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="be7b1-116">Removing licenses from user accounts</span></span>

<span data-ttu-id="be7b1-117">Para quitar licencias de una cuenta de usuario existente, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="be7b1-117">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="be7b1-118">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="be7b1-118">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="be7b1-119">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be7b1-119">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="be7b1-120">En este ejemplo se quita la licencia **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de la cuenta de usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="be7b1-120">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="be7b1-121">No puede usar el `Set-MsolUserLicense` cmdlet para anular la asignación de usuarios de licencias *canceladas* .</span><span class="sxs-lookup"><span data-stu-id="be7b1-121">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="be7b1-122">Debe hacerlo de forma individual para cada cuenta de usuario en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="be7b1-122">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="be7b1-123">Para quitar todas las licencias de un grupo de usuarios con licencia existentes, use uno de los métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="be7b1-123">To remove all licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="be7b1-124">**Filtrar las cuentas basándose en un atributo de cuenta existente** Para ello, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="be7b1-124">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="be7b1-125">En este ejemplo se quitan todas las licencias de todas las cuentas de usuario del Departamento de ventas de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="be7b1-125">This example removes all licenses from all user accounts in the Sales department in the United States.</span></span>
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- <span data-ttu-id="be7b1-126">**Usar una lista de cuentas específicas para una licencia específica** Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="be7b1-126">**Use a list of specific accounts for a specific license** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="be7b1-127">Cree y guarde un archivo de texto que contenga una cuenta en cada línea de esta manera:</span><span class="sxs-lookup"><span data-stu-id="be7b1-127">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="be7b1-128">Utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="be7b1-128">Use the following syntax:</span></span>
    
  ```powershell
  $x=Get-Content "<FileNameAndPath>"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "<AccountSkuId1>","<AccountSkuId2>"...
  }
  ```
<span data-ttu-id="be7b1-129">En este ejemplo se quita la licencia **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de las cuentas de usuario definidas en el archivo de texto c:\Mis Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="be7b1-129">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  $x=Get-Content "C:\My Documents\Accounts.txt"
  for ($i=0; $i -lt $x.Count; $i++)
  {
  Set-MsolUserLicense -UserPrincipalName $x[$i] -RemoveLicenses "litwareinc:ENTERPRISEPACK"
  }
  ```

<span data-ttu-id="be7b1-130">Para quitar todas las licencias de todas las cuentas de usuario existentes, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="be7b1-130">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

<span data-ttu-id="be7b1-131">Otra forma de liberar una licencia consiste en eliminar la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="be7b1-131">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="be7b1-132">Para obtener más información, vea [eliminar y restaurar cuentas de usuario con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="be7b1-132">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="be7b1-133">Ver también</span><span class="sxs-lookup"><span data-stu-id="be7b1-133">See also</span></span>

[<span data-ttu-id="be7b1-134">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="be7b1-134">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="be7b1-135">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="be7b1-135">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="be7b1-136">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="be7b1-136">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

