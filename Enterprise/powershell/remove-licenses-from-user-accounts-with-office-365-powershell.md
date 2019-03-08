---
title: Eliminar licencias de cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/07/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explica cómo usar Office 365 PowerShell para quitar licencias de Office 365 que se han asignado anteriormente a los usuarios.
ms.openlocfilehash: 66ffe7275bcfd936c7df70d3969b96fefafb355d
ms.sourcegitcommit: 0a99abcb67fc8ee7594cb66f5f7fd0e6e94eb3fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/07/2019
ms.locfileid: "30474181"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a><span data-ttu-id="864b0-103">Eliminar licencias de cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="864b0-103">Remove licenses from user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="864b0-104">**Resumen:** Explica cómo usar Office 365 PowerShell para quitar licencias de Office 365 que se han asignado anteriormente a los usuarios.</span><span class="sxs-lookup"><span data-stu-id="864b0-104">**Summary:** Explains how to use Office 365 PowerShell to remove Office 365 licenses that were previously assigned to users.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="864b0-105">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="864b0-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="864b0-106">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="864b0-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  

<span data-ttu-id="864b0-107">A continuación, enumere los planes de licencia para el inquilino con este comando.</span><span class="sxs-lookup"><span data-stu-id="864b0-107">Next, list the license plans for your tenant with this command.</span></span>

```
Get-AzureADSubscribedSku | Select SkuPartNumber
```

<span data-ttu-id="864b0-108">A continuación, obtenga el nombre de inicio de sesión de la cuenta para la que desea quitar una licencia, también conocido como nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="864b0-108">Next, get the sign-in name of the account for which you want remove a license, also known as the user principal name (UPN).</span></span>

<span data-ttu-id="864b0-109">Por último, especifique los nombres de inicio de sesión y de plan de licencias de usuario, quite los caracteres "<" y ">" y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="864b0-109">Finally, specify the user sign-in and license plan names, remove the "<" and ">" characters, and run these commands.</span></span>

```
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

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="864b0-110">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="864b0-110">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="864b0-111">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="864b0-111">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

   
<span data-ttu-id="864b0-112">Para ver la información del plan de licencias (**AccountSkuID** ) de la organización, consulte los siguientes temas:</span><span class="sxs-lookup"><span data-stu-id="864b0-112">To view the licensing plan (**AccountSkuID** ) information in your organization, see the following topics:</span></span>
    
  - [<span data-ttu-id="864b0-113">Ver las licencias y los servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="864b0-113">View licenses and services with Office 365 PowerShell</span></span>](view-licenses-and-services-with-office-365-powershell.md)
    
  - [<span data-ttu-id="864b0-114">Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="864b0-114">View account license and service details with Office 365 PowerShell</span></span>](view-account-license-and-service-details-with-office-365-powershell.md)
    
<span data-ttu-id="864b0-115">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.</span><span class="sxs-lookup"><span data-stu-id="864b0-115">If you use the **Get-MsolUser** cmdlet without using the _-All_ parameter, only the first 500 accounts are returned.</span></span>
    
### <a name="removing-licenses-from-user-accounts"></a><span data-ttu-id="864b0-116">Quitar licencias de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="864b0-116">Removing licenses from user accounts</span></span>

<span data-ttu-id="864b0-117">Para quitar licencias de una cuenta de usuario existente, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="864b0-117">To remove licenses from an existing user account, use the following syntax:</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

<span data-ttu-id="864b0-118">En este ejemplo se `litwareinc:ENTERPRISEPACK` quita la licencia (Office 365 Enterprise E3) de la cuenta de usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="864b0-118">This example removes the `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user account BelindaN@litwareinc.com.</span></span>
  
```
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

<span data-ttu-id="864b0-119">Para quitar licencias de un grupo de usuarios con licencia existentes, utilice uno de los métodos siguientes:</span><span class="sxs-lookup"><span data-stu-id="864b0-119">To remove licenses from a group of existing licensed users, use either of the following methods:</span></span>
  
- <span data-ttu-id="864b0-120">**Filtrar las cuentas basándose en un atributo de cuenta existente** Para ello, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="864b0-120">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
```
$x = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
$x | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="864b0-121">En este ejemplo se `litwareinc:ENTERPRISEPACK` quitan las licencias (Office 365 Enterprise E3) de todas las cuentas de los usuarios del Departamento de ventas de los Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="864b0-121">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) licenses from all accounts for users in the Sales department in the United States.</span></span>
    
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
$USSales | foreach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

- <span data-ttu-id="864b0-122">**Usar una lista de cuentas específicas** Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="864b0-122">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="864b0-123">Cree y guarde un archivo de texto que contenga una cuenta en cada línea de esta manera:</span><span class="sxs-lookup"><span data-stu-id="864b0-123">Create and save a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. <span data-ttu-id="864b0-124">Utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="864b0-124">Use the following syntax:</span></span>
    
  ```
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"... }
  ```

<span data-ttu-id="864b0-125">En este ejemplo se `litwareinc:ENTERPRISEPACK` quita la licencia (Office 365 Enterprise E3) de las cuentas de usuario definidas en el archivo de texto c:\Mis documentos\cuentas.txt.</span><span class="sxs-lookup"><span data-stu-id="864b0-125">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from the user accounts defined in the text file C:\My Documents\Accounts.txt.</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

<span data-ttu-id="864b0-126">Para quitar las licencias de todas las cuentas de usuario, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="864b0-126">To remove licenses from all existing user accounts, use the following syntax:</span></span>
  
```
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...}
```

<span data-ttu-id="864b0-127">En este ejemplo se `litwareinc:ENTERPRISEPACK` quita la licencia (Office 365 Enterprise E3) de todas las cuentas de usuario con licencia existentes.</span><span class="sxs-lookup"><span data-stu-id="864b0-127">This example removes the  `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) license from all existing licensed user accounts.</span></span>
  
```
$x = Get-MsolUser -All  | Where {$_.isLicensed -eq $true}
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -RemoveLicenses "litwareinc:ENTERPRISEPACK"}
```

<span data-ttu-id="864b0-128">Otra forma de liberar una licencia consiste en eliminar la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="864b0-128">Another way to free up a license is by deleting the user account.</span></span> <span data-ttu-id="864b0-129">Para obtener más información, vea [eliminar y restaurar cuentas de usuario con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="864b0-129">For more information, see [Delete and restore user accounts with Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="864b0-130">Vea también</span><span class="sxs-lookup"><span data-stu-id="864b0-130">See also</span></span>

[<span data-ttu-id="864b0-131">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="864b0-131">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="864b0-132">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="864b0-132">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="864b0-133">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="864b0-133">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

    
## <a name="new-to-office-365"></a><span data-ttu-id="864b0-134">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="864b0-134">New to Office 365?</span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   

