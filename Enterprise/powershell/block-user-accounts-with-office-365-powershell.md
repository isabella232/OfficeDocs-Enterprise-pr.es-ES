---
title: Bloquear cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
ms.assetid: 04e58c2a-400b-496a-acd4-8ec5d37236dc
description: Se explica cómo usar PowerShell de Office 365 para bloquear y desbloquear el acceso a cuentas de Office 365.
ms.openlocfilehash: 0e1ac3f61acafedd77c2af760b8316aa6b936e7b
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546481"
---
# <a name="block-user-accounts-with-office-365-powershell"></a><span data-ttu-id="83d3a-103">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="83d3a-103">Block user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="83d3a-104">**Resumen:**  Se explica cómo usar PowerShell de Office 365 para bloquear y desbloquear el acceso a cuentas de Office 365.</span><span class="sxs-lookup"><span data-stu-id="83d3a-104">**Summary:**  Explains how to use Office 365 PowerShell to block and unblock access to Office 365 accounts.</span></span>
  
<span data-ttu-id="83d3a-p101">Bloquear el acceso a una cuenta de Office 365 impide que alguien pueda usar la cuenta para iniciar sesión y tener acceso a los servicios y los datos de la organización de Office 365. Puede usar PowerShell de Office 365 para bloquear el acceso a una persona y varias cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="83d3a-p101">Blocking access to an Office 365 account prevents anyone from using the account to sign in and access the services and data in your Office 365 organization. You can use Office 365 PowerShell to block access to individual and multiple user accounts.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="83d3a-107">Usar Azure Active Directory PowerShell para el módulo de gráfico</span><span class="sxs-lookup"><span data-stu-id="83d3a-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="83d3a-108">Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="83d3a-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="83d3a-109">Bloquear el acceso a las cuentas de usuario individuales</span><span class="sxs-lookup"><span data-stu-id="83d3a-109">Block access to individual user accounts</span></span>

<span data-ttu-id="83d3a-110">Para bloquear una cuenta de usuario individual, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="83d3a-110">Use the following syntax to block an individual user account:</span></span>
  
```
Set-AzureADUser -ObjectID <sign-in name of the user account> -AccountEnabled $false
```

> [!NOTE]
> <span data-ttu-id="83d3a-111">El parámetro - ObjectID en el cmdlet Set-AzureAD acepta puede ser el inicio de sesión de nombre de cuenta, también conocida como el nombre Principal de usuario o identificador de objeto. de la cuenta</span><span class="sxs-lookup"><span data-stu-id="83d3a-111">The -ObjectID parameter in the Set-AzureAD cmdlet accepts either the account sign-in name, also known as the User Principal Name, or the account's object ID.</span></span> 
  
<span data-ttu-id="83d3a-112">Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="83d3a-112">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $false
```

<span data-ttu-id="83d3a-113">Para desbloquear esta cuenta de usuario, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="83d3a-113">To unblock this user account, run the following command:</span></span>
  
```
Set-AzureADUser -ObjectID fabricec@litwareinc.com -AccountEnabled $true
```

<span data-ttu-id="83d3a-114">Para mostrar la cuenta de usuario que UPN basado en nombre para mostrar del usuario, use los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="83d3a-114">To display the user account UPN based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName

```

<span data-ttu-id="83d3a-115">En este ejemplo se muestra la cuenta de usuario UPN para el usuario llamado Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="83d3a-115">This example displays the user account UPN for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="83d3a-116">Para bloquear una cuenta basada en el nombre para mostrar del usuario, use los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="83d3a-116">To block an account based on the user's display name, use the following commands:</span></span>
  
```
$userName="<display name>"
Set-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName -AccountEnabled $false

```

<span data-ttu-id="83d3a-117">En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="83d3a-117">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-AzureADUser -UserPrincipalName <UPN of user account> | Select DisplayName,AccountEnabled
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="83d3a-118">Bloquear el acceso a varias cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="83d3a-118">Block access to multiple user accounts</span></span>

<span data-ttu-id="83d3a-119">Para bloquear el acceso a varias cuentas de usuario, cree un archivo de texto que contiene un inicio de sesión de nombre de cuenta en cada línea como la siguiente:</span><span class="sxs-lookup"><span data-stu-id="83d3a-119">To block access to multiple user accounts, create a text file that contains one account sign-in name on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

<span data-ttu-id="83d3a-p102">En los siguientes comandos, el archivo de texto de ejemplo es C:\My Documents\Accounts.txt. Reemplazar por la ruta de acceso y el nombre de su archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="83d3a-p102">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
  
<span data-ttu-id="83d3a-122">Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="83d3a-122">To block access to the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $false }
```

<span data-ttu-id="83d3a-123">Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="83d3a-123">To unblock the accounts listed in the text file, run the following command:</span></span>
    
```
Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-AzureADUSer -ObjectID $_ -AccountEnabled $true }
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="83d3a-124">Usar el módulo de Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="83d3a-124">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="83d3a-125">Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="83d3a-125">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

    
### <a name="block-access-to-individual-user-accounts"></a><span data-ttu-id="83d3a-126">Bloquear el acceso a las cuentas de usuario individuales</span><span class="sxs-lookup"><span data-stu-id="83d3a-126">Block access to individual user accounts</span></span>

<span data-ttu-id="83d3a-127">Utilice la sintaxis siguiente para bloquear el acceso a una cuenta de usuario individual:</span><span class="sxs-lookup"><span data-stu-id="83d3a-127">Use the following syntax to block access to an individual user account:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $true
```

<span data-ttu-id="83d3a-128">Este ejemplo bloquea el acceso a la cuenta de usuario fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="83d3a-128">This example blocks access to the user account fabricec@litwareinc.com.</span></span>
  
```
Set-MsolUser -UserPrincipalName fabricec@litwareinc.com -BlockCredential $true
```

<span data-ttu-id="83d3a-129">Para desbloquear la cuenta de usuario, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="83d3a-129">To unblock the user account, run the following command:</span></span>
  
```
Set-MsolUser -UserPrincipalName <sign-in name of user account>  -BlockCredential $false
```

<span data-ttu-id="83d3a-130">En cualquier momento, puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="83d3a-130">At any time, you can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of user account> | Select DisplayName,BlockCredential
```

### <a name="block-access-to-multiple-user-accounts"></a><span data-ttu-id="83d3a-131">Bloquear el acceso a varias cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="83d3a-131">Block access to multiple user accounts</span></span>

<span data-ttu-id="83d3a-132">En primer lugar, cree un archivo de texto que contiene una cuenta en cada línea como la siguiente:</span><span class="sxs-lookup"><span data-stu-id="83d3a-132">First, create a text file that contains one account on each line like this:</span></span>
    
  ```
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```
<span data-ttu-id="83d3a-p103">En los siguientes comandos, el archivo de texto de ejemplo es C:\My Documents\Accounts.txt. Reemplazar por la ruta de acceso y el nombre de su archivo de texto.</span><span class="sxs-lookup"><span data-stu-id="83d3a-p103">In the following commands, the example text file is C:\My Documents\Accounts.txt. Replace this with the path and file name of your text file.</span></span>
    
<span data-ttu-id="83d3a-135">Para bloquear el acceso a las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="83d3a-135">To block access to the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $true }
  ```
<span data-ttu-id="83d3a-136">Para desbloquear las cuentas enumeradas en el archivo de texto, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="83d3a-136">To unblock the accounts listed in the text file, run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUser -UserPrincipalName $_ -BlockCredential $false }
  ```

## <a name="see-also"></a><span data-ttu-id="83d3a-137">Consulte también</span><span class="sxs-lookup"><span data-stu-id="83d3a-137">See also</span></span>

[<span data-ttu-id="83d3a-138">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="83d3a-138">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="83d3a-139">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="83d3a-139">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="83d3a-140">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="83d3a-140">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
