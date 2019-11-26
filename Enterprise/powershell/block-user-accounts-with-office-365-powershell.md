---
title: Bloquear cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Explica cómo usar Office 365 PowerShell para bloquear y desbloquear el acceso a cuentas de Office 365.
ms.openlocfilehash: 09cfdaf1485837713d03949cca456b9d07b66b00
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257671"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="5a83f-103">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5a83f-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="5a83f-104">**Resumen:**  Explica cómo usar Office 365 PowerShell para bloquear y desbloquear el acceso a cuentas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5a83f-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="5a83f-105">Al bloquear el acceso a una cuenta de Office 365, cualquier usuario que no pueda usar la cuenta puede iniciar sesión y acceder a los servicios y datos de su organización de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5a83f-105">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization.</span></span> <span data-ttu-id="5a83f-106">Puede usar Office 365 PowerShell para bloquear el acceso a cuentas de usuario individuales y múltiples.</span><span class="sxs-lookup"><span data-stu-id="5a83f-106">You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5a83f-107">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="5a83f-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5a83f-108">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="5a83f-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="5a83f-109">Bloquear el acceso a cuentas de usuario individuales</span><span class="sxs-lookup"><span data-stu-id="5a83f-109">Block access to individual user accounts</span></span>

<span data-ttu-id="5a83f-110">Use la siguiente sintaxis para bloquear una cuenta de usuario individual:</span><span class="sxs-lookup"><span data-stu-id="5a83f-110">Use the following syntax to block an individual user account:</span></span>
  
```powershell
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="5a83f-111">El parámetro-ObjectID en el cmdlet Set-AzureAD acepta el nombre de inicio de sesión de la cuenta, también conocido como nombre principal de usuario, o el identificador de objeto de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="5a83f-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="5a83f-112">Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="5a83f-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="5a83f-113">Para desbloquear esta cuenta de usuario, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5a83f-113">To unblock this user account, run the following command:</span></span>
  
```powershell
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="5a83f-114">Para mostrar el UPN de la cuenta de usuario en función del nombre para mostrar del usuario, use los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="5a83f-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="5a83f-115">En este ejemplo se muestra el UPN de la cuenta de usuario para el usuario denominado Caleb alféizares.</span><span class="sxs-lookup"><span data-stu-id="5a83f-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5a83f-116">Para bloquear una cuenta según el nombre para mostrar del usuario, use los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="5a83f-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="5a83f-117">En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5a83f-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="5a83f-118">Bloquear el acceso a varias cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="5a83f-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="5a83f-119">Para bloquear el acceso a varias cuentas de usuario, cree un archivo de texto que contenga un nombre de inicio de sesión de la cuenta en cada línea de la siguiente manera:</span><span class="sxs-lookup"><span data-stu-id="5a83f-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="5a83f-120">En los siguientes comandos, el archivo de texto de ejemplo es C:\Mis Documentos\cuentas.txt.</span><span class="sxs-lookup"><span data-stu-id="5a83f-120">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="5a83f-121">Reemplácelo por la ruta de acceso y el nombre de archivo del archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="5a83f-121">Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="5a83f-122">Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5a83f-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="5a83f-123">Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5a83f-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```powershell
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5a83f-124">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a83f-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5a83f-125">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5a83f-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="5a83f-126">Bloquear el acceso a cuentas de usuario individuales</span><span class="sxs-lookup"><span data-stu-id="5a83f-126">Block access to individual user accounts</span></span>

<span data-ttu-id="5a83f-127">Utilice la sintaxis siguiente para bloquear el acceso a una cuenta de usuario individual:</span><span class="sxs-lookup"><span data-stu-id="5a83f-127">Use the following syntax to block access to an individual user account:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

>[!Note]
><span data-ttu-id="5a83f-128">PowerShell Core no es compatible con el módulo Microsoft Azure Active Directory para el módulo y los cmdlets de Windows PowerShell con **msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="5a83f-128">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="5a83f-129">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a83f-129">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="5a83f-130">Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="5a83f-130">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="5a83f-131">Para desbloquear la cuenta de usuario, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5a83f-131">To unblock the user account, run the following command:</span></span>
  
```powershell
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="5a83f-132">En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5a83f-132">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="5a83f-133">Bloquear el acceso a varias cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="5a83f-133">Block access to multiple user accounts</span></span>

<span data-ttu-id="5a83f-134">En primer lugar, cree un archivo de texto que contenga una cuenta en cada línea como esta:</span><span class="sxs-lookup"><span data-stu-id="5a83f-134">First, create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="5a83f-135">En los siguientes comandos, el archivo de texto de ejemplo es C:\Mis Documentos\cuentas.txt.</span><span class="sxs-lookup"><span data-stu-id="5a83f-135">In the following commands, the example text file is C:\My Documents\Accounts.txt.</span></span> <span data-ttu-id="5a83f-136">Reemplácelo por la ruta de acceso y el nombre de archivo del archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="5a83f-136">Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="5a83f-137">Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5a83f-137">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="5a83f-138">Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="5a83f-138">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="5a83f-139">Consulte también</span><span class="sxs-lookup"><span data-stu-id="5a83f-139">See also</span></span>

[<span data-ttu-id="5a83f-140">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5a83f-140">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5a83f-141">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5a83f-141">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5a83f-142">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5a83f-142">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
