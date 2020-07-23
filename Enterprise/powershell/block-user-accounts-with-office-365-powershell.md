---
title: Bloquear cuentas de usuario 365 de Microsoft con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Explica cómo usar PowerShell para bloquear y desbloquear el acceso a cuentas de Microsoft 365.
ms.openlocfilehash: c18c0248c51096ab089b16b2e9e31eb0929de443
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230896"
---
# <a name="block-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="917ce-103">Bloquear cuentas de usuario 365 de Microsoft con PowerShell</span><span class="sxs-lookup"><span data-stu-id="917ce-103">Block Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="917ce-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="917ce-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="917ce-105">Al bloquear el acceso a una cuenta de Microsoft 365, cualquier usuario que no pueda usar la cuenta puede iniciar sesión y acceder a los servicios y datos de su organización de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="917ce-105">Blocking access to a Microsoft 365 account prevents anyone from using the account to sign in and access the services and data in your Microsoft 365 organization.</span></span> <span data-ttu-id="917ce-106">Puede usar PowerShell para bloquear el acceso a cuentas de usuario individuales y múltiples.</span><span class="sxs-lookup"><span data-stu-id="917ce-106">You can use PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="917ce-107">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="917ce-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="917ce-108">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="917ce-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="917ce-109">Bloquear el acceso a cuentas de usuario individuales</span><span class="sxs-lookup"><span data-stu-id="917ce-109">Block access to individual user accounts</span></span>

<span data-ttu-id="917ce-110">Use la siguiente sintaxis para bloquear una cuenta de usuario individual:</span><span class="sxs-lookup"><span data-stu-id="917ce-110">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="917ce-111">El parámetro-ObjectID en el cmdlet Set-AzureAD acepta el nombre de inicio de sesión de la cuenta, también conocido como nombre principal de usuario, o el identificador de objeto de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="917ce-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="917ce-112">Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="917ce-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="917ce-113">Para desbloquear esta cuenta de usuario, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="917ce-113">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="917ce-114">Para mostrar el UPN de la cuenta de usuario en función del nombre para mostrar del usuario, use los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="917ce-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="917ce-115">En este ejemplo se muestra el UPN de la cuenta de usuario para el usuario denominado Caleb alféizares.</span><span class="sxs-lookup"><span data-stu-id="917ce-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="917ce-116">Para bloquear una cuenta según el nombre para mostrar del usuario, use los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="917ce-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="917ce-117">En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="917ce-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="917ce-118">Bloquear el acceso a varias cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="917ce-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="917ce-119">Para bloquear el acceso a varias cuentas de usuario, cree un archivo de texto que contenga un nombre de inicio de sesión de la cuenta en cada línea de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="917ce-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="917ce-120">En los siguientes comandos, el archivo de texto de ejemplo es C:\Mis Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="917ce-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="917ce-121">Reemplácelo por la ruta de acceso y el nombre de archivo del archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="917ce-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="917ce-122">Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="917ce-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="917ce-123">Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="917ce-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="917ce-124">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="917ce-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="917ce-125">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="917ce-125">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="917ce-126">Bloquear el acceso a cuentas de usuario individuales</span><span class="sxs-lookup"><span data-stu-id="917ce-126">Block access to individual user accounts</span></span>

<span data-ttu-id="917ce-127">Utilice la sintaxis siguiente para bloquear el acceso a una cuenta de usuario individual:</span><span class="sxs-lookup"><span data-stu-id="917ce-127">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="917ce-128">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="917ce-128">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="917ce-129">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="917ce-129">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="917ce-130">Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="917ce-130">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="917ce-131">Para desbloquear la cuenta de usuario, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="917ce-131">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="917ce-132">En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="917ce-132">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="917ce-133">Bloquear el acceso a varias cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="917ce-133">Block access to multiple user accounts</span></span>

<span data-ttu-id="917ce-134">En primer lugar, cree un archivo de texto que contenga una cuenta en cada línea como esta:</span><span class="sxs-lookup"><span data-stu-id="917ce-134">First, create a text file that contains one account on each line like this:</span></span>
    
```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
```

<span data-ttu-id="917ce-135">En los siguientes comandos, el archivo de texto de ejemplo es C:\Mis Documents\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="917ce-135">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="917ce-136">Reemplácelo por la ruta de acceso y el nombre de archivo del archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="917ce-136">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="917ce-137">Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="917ce-137">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="917ce-138">Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="917ce-138">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="917ce-139">Consulte también</span><span class="sxs-lookup"><span data-stu-id="917ce-139">See also</span></span>

[<span data-ttu-id="917ce-140">Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="917ce-140">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="917ce-141">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="917ce-141">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="917ce-142">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="917ce-142">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
