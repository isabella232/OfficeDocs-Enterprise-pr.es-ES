---
title: Eliminar cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
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
- O365ITProTrain
ms.assetid: 209c9868-448c-49bc-baae-11e28b923a39
description: Obtenga información sobre cómo usar PowerShell de Office 365 para eliminar cuentas de usuario de Office 365.
ms.openlocfilehash: ea803d82bb54e5430ceb9a59e8c04a0f72b200fc
ms.sourcegitcommit: 069f56455252d6f4001ec0ecee792b83b585e692
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/13/2020
ms.locfileid: "43237811"
---
# <a name="delete-user-accounts-with-office-365-powershell"></a><span data-ttu-id="dd477-103">Eliminar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="dd477-103">Delete user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="dd477-104">Puede usar PowerShell de Office 365 para eliminar una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="dd477-104">You can use Office 365 PowerShell to delete a user account.</span></span>
   
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="dd477-105">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="dd477-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="dd477-106">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="dd477-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

<span data-ttu-id="dd477-107">Después de haberse conectado, use la sintaxis siguiente para eliminar una cuenta de usuario individual:</span><span class="sxs-lookup"><span data-stu-id="dd477-107">After you have connected, use the following syntax to remove an individual user account:</span></span>
  
```powershell
Remove-AzureADUser -ObjectID <sign-in name>
```

<span data-ttu-id="dd477-108">Este ejemplo elimina la cuenta de usuario fabricec@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="dd477-108">This example removes the user account fabricec@litwareinc.com.</span></span>
  
```powershell
Remove-AzureADUser -ObjectID fabricec@litwareinc.com
```

> [!NOTE]
> <span data-ttu-id="dd477-109">El parámetro **-objectId** en el cmdlet **Remove-AzureADUser** acepta tanto el nombre de inicio de sesión de la cuenta, también conocido como el nombre principal de usuario, o el identificador de objeto de la cuenta.</span><span class="sxs-lookup"><span data-stu-id="dd477-109">The **-ObjectID** parameter in the **Remove-AzureADUser** cmdlet accepts either the account's sign-in name, also known as the User Principal Name, or the account's object ID.</span></span>
  
<span data-ttu-id="dd477-110">Para mostrar el nombre de cuenta según el nombre de usuario, use los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="dd477-110">To display the account name based on the user's name, use the following commands:</span></span>
  
```powershell
$userName="<User name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="dd477-111">Este ejemplo muestra el nombre de cuenta para el usuario llamado Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="dd477-111">This example displays the account name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="dd477-112">Para eliminar una cuenta según el nombre para mostrar del usuario, use los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="dd477-112">To remove an account based on the user's display name, use the following commands:</span></span>
  
```powershell
$userName="<display name>"
Remove-AzureADUser -ObjectID (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="dd477-113">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd477-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="dd477-p101">Al eliminar una cuenta de usuario con el Módulo Microsoft Azure Active Directory para Windows PowerShell, esta no se elimina de forma permanente. Puede restaurar la cuenta de usuario eliminada durante los siguientes 30 días.</span><span class="sxs-lookup"><span data-stu-id="dd477-p101">When you delete a user account with the Microsoft Azure Active Directory Module for Windows PowerShell, the account isn't permanently deleted. You can restore the deleted user account within 30 days.</span></span>

<span data-ttu-id="dd477-116">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="dd477-116">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="dd477-117">Para eliminar una cuenta de usuario, utilice la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="dd477-117">To delete a user account, use the following syntax:</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName <sign-in name>
```

>[!Note]
><span data-ttu-id="dd477-118">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="dd477-118">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="dd477-119">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dd477-119">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="dd477-120">Este ejemplo elimina la cuenta de usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="dd477-120">This example deletes the user account BelindaN@litwareinc.com.</span></span>
  
```powershell
Remove-MsolUser -UserPrincipalName belindan@litwareinc.com
```

<span data-ttu-id="dd477-121">Para restaurar una cuenta de usuario eliminada dentro del periodo de gracia de 30 días, utilice la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="dd477-121">To restore a deleted user account within the 30-day grace period, use the following syntax:</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName <sign-in name>
```

<span data-ttu-id="dd477-122">Este ejemplo restaura la cuenta eliminada BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="dd477-122">This example restores the deleted account BelindaN@litwareinc.com.</span></span>
  
```powershell
Restore-MsolUser -UserPrincipalName BelindaN@litwareinc.com
```

 <span data-ttu-id="dd477-123">**Notas:**</span><span class="sxs-lookup"><span data-stu-id="dd477-123">**Notes:**</span></span>
  
- <span data-ttu-id="dd477-124">Para ver la lista de usuarios eliminados que pueden restaurarse, ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="dd477-124">To see the list of deleted users that can be restored, run the following command:</span></span>
    
  ```powershell
  Get-MsolUser -All -ReturnDeletedUsers
  ```

- <span data-ttu-id="dd477-125">Si otra cuenta usa el nombre principal de usuario original de la cuenta de usuario, use el parámetro _NewUserPrincipalName_ en vez de _UserPrincipalName_ para especificar un nombre principal de usuario al restaurar la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="dd477-125">If the user account's original user principal name is used by another account, use the _NewUserPrincipalName_ parameter instead of _UserPrincipalName_ to specify a different user principal name when you restore the user account.</span></span>


## <a name="see-also"></a><span data-ttu-id="dd477-126">Vea también</span><span class="sxs-lookup"><span data-stu-id="dd477-126">See also</span></span>

[<span data-ttu-id="dd477-127">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="dd477-127">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="dd477-128">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="dd477-128">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="dd477-129">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="dd477-129">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
