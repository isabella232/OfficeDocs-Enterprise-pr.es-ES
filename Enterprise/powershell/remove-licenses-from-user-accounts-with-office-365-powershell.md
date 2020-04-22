---
title: Eliminar licencias de cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/20/2020
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
ms.openlocfilehash: ea762e992056ac3265336055eabb860f67482093
ms.sourcegitcommit: f2e640ffdbef95c6d98845f85fd9bea21a7388aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2020
ms.locfileid: "43580927"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="3c5d4-103">Eliminar licencias de cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3c5d4-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="3c5d4-104">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="3c5d4-104">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="3c5d4-105">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="3c5d4-105">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="3c5d4-106">A continuación, enumere los planes de licencia para el inquilino con este comando.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-106">Next, list the license plans for your tenant with this command.</span></span>

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="3c5d4-107">A continuación, obtenga el nombre de inicio de sesión de la cuenta para la que desea quitar una licencia, también conocido como nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="3c5d4-107">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="3c5d4-108">Por último, especifique los nombres de inicio de sesión y de plan de licencias de usuario, quite los caracteres "<" y ">" y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-108">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="3c5d4-109">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c5d4-109">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="3c5d4-110">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="3c5d4-110">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
   
<span data-ttu-id="3c5d4-111">Para ver la información del plan de licencias (**AccountSkuID** ) de la organización, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="3c5d4-111">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="3c5d4-112">Ver las licencias y los servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3c5d4-112">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="3c5d4-113">Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3c5d4-113">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="3c5d4-114">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-114">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="3c5d4-115">Quitar licencias de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="3c5d4-115">Removing licenses from user accounts</span></span>

<span data-ttu-id="3c5d4-116">Para quitar licencias de una cuenta de usuario existente, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="3c5d4-116">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
><span data-ttu-id="3c5d4-117">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-117">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="3c5d4-118">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-118">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="3c5d4-119">En este ejemplo se quita la licencia **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de la cuenta de usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-119">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
><span data-ttu-id="3c5d4-120">No puede usar el `Set-MsolUserLicense` cmdlet para anular la asignación de usuarios de licencias *canceladas* .</span><span class="sxs-lookup"><span data-stu-id="3c5d4-120">You cannot use the `Set-MsolUserLicense` cmdlet to unassign users from *canceled* licenses.</span></span> <span data-ttu-id="3c5d4-121">Debe hacerlo de forma individual para cada cuenta de usuario en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-121">You must do this individually for each user account in the Microsoft 365 admin center.</span></span>
>

<span data-ttu-id="3c5d4-122">Para quitar licencias de un grupo de usuarios con licencia existentes, utilice uno de los métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="3c5d4-122">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="3c5d4-123">**Filtrar las cuentas basándose en un atributo de cuenta existente** Para ello, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="3c5d4-123">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="3c5d4-124">En este ejemplo se quitan las licencias **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de todas las cuentas de los usuarios del Departamento de ventas de los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-124">This example removes the  **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="3c5d4-125">**Usar una lista de cuentas específicas** Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="3c5d4-125">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="3c5d4-126">Cree y guarde un archivo de texto que contenga una cuenta en cada línea de esta manera:</span><span class="sxs-lookup"><span data-stu-id="3c5d4-126">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="3c5d4-127">Utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="3c5d4-127">Use the following syntax:</span></span>
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

<span data-ttu-id="3c5d4-128">En este ejemplo se quita la licencia **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de las cuentas de usuario definidas en el archivo de texto c:\Mis documentos\cuentas.txt.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-128">This example removes the **litwareinc:ENTERPRISEPACK** (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="3c5d4-129">Para quitar todas las licencias de todas las cuentas de usuario existentes, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="3c5d4-129">To remove all licenses from all existing user accounts, use the following syntax:</span></span>
  
```powershell
$users = Get-MsolUser -All | where {$_.isLicensed -eq $true}
ForEach($user in $users)
{
$licenses = $user.Licenses.AccountSkuId
ForEach ($lic in $licenses)
{ Set-MsolUserLicense -UserPrincipalName $user.UserPrincipalName -RemoveLicenses $lic }
}
```

<span data-ttu-id="3c5d4-130">Otra forma de liberar una licencia consiste en eliminar la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="3c5d4-130">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="3c5d4-131">Para obtener más información, vea [eliminar y restaurar cuentas de usuario con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="3c5d4-131">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3c5d4-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="3c5d4-132">See also</span></span>

[<span data-ttu-id="3c5d4-133">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="3c5d4-133">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="3c5d4-134">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3c5d4-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="3c5d4-135">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="3c5d4-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

