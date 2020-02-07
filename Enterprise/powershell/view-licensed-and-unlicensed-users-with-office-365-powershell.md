---
title: Ver los usuarios con licencia y sin licencia con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/18/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: Se explica cómo usar PowerShell de Office 365 para ver las cuentas de usuario con licencia y sin licencia.
ms.openlocfilehash: 4b2f2b5b3898b9f800cc3fb9416c5b666472d907
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844151"
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a><span data-ttu-id="c4cb5-103">Ver los usuarios con licencia y sin licencia con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="c4cb5-103">View licensed and unlicensed users with Office 365 PowerShell</span></span>

<span data-ttu-id="c4cb5-p101">Las cuentas de usuario de la organización de Office 365 pueden tener algunas, todas o ninguna de las licencias disponibles asignadas a ellas desde los planes de licencias que están disponibles en su organización. Puede usar PowerShell de Office 365 para encontrar rápidamente los usuarios con licencia y sin licencia de la organización.</span><span class="sxs-lookup"><span data-stu-id="c4cb5-p101">User accounts in your Office 365 organization may have some, all, or none of the available licenses assigned to them from the licensing plans that are available in your organization. You can use Office 365 PowerShell to quickly find the licensed and unlicensed users in your organization.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="c4cb5-106">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="c4cb5-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="c4cb5-107">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="c4cb5-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
 
<span data-ttu-id="c4cb5-108">Para ver la lista de todas las cuentas de usuario de la organización a las que no se ha asignado ninguno de los planes de licencias (usuarios sin licencia), ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c4cb5-108">To view the list of all user accounts in your organization that have NOT been assigned any of your licensing plans (unlicensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach{ $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $false) { Write-Host $_.UserPrincipalName} }
```

<span data-ttu-id="c4cb5-109">Para ver la lista de todas las cuentas de usuario de la organización a las que se han asignado los planes de licencias (usuarios con licencia), ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="c4cb5-109">To view the list of all user accounts in your organization that have been assigned any of your licensing plans (licensed users), run the following command:</span></span>
  
```powershell
Get-AzureAdUser | ForEach { $licensed=$False ; For ($i=0; $i -le ($_.AssignedLicenses | Measure).Count ; $i++) { If( [string]::IsNullOrEmpty(  $_.AssignedLicenses[$i].SkuId ) -ne $True) { $licensed=$true } } ; If( $licensed -eq $true) { Write-Host $_.UserPrincipalName} }
```

>[!Note]
><span data-ttu-id="c4cb5-110">Para obtener una lista de todos los usuarios de la suscripción, `Get-AzureAdUser -All $true` use el comando.</span><span class="sxs-lookup"><span data-stu-id="c4cb5-110">To list all of the users in your subscription, use the `Get-AzureAdUser -All $true` command.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="c4cb5-111">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4cb5-111">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="c4cb5-112">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="c4cb5-112">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="c4cb5-113">Para ver la lista de todas las cuentas de usuario y su estado de licencias en la organización, ejecute el comando siguiente en PowerShell de Office 365:</span><span class="sxs-lookup"><span data-stu-id="c4cb5-113">To view the list of all user accounts and their licensing status in your organization, run the following command in Office 365 PowerShell:</span></span>
  
```powershell
Get-MsolUser -All
```

>[!Note]
><span data-ttu-id="c4cb5-114">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="c4cb5-114">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="c4cb5-115">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c4cb5-115">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="c4cb5-116">Para ver la lista de todas las cuentas de usuario sin licencia de su organización, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="c4cb5-116">To view the list of all unlicensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All -UnlicensedUsersOnly
```

<span data-ttu-id="c4cb5-117">Para ver la lista de todas las cuentas de usuario con licencia de su organización, ejecute el comando siguiente:</span><span class="sxs-lookup"><span data-stu-id="c4cb5-117">To view the list of all licensed user accounts in your organization, run the following command:</span></span>
  
```powershell
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="see-also"></a><span data-ttu-id="c4cb5-118">Vea también</span><span class="sxs-lookup"><span data-stu-id="c4cb5-118">See also</span></span>

[<span data-ttu-id="c4cb5-119">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="c4cb5-119">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="c4cb5-120">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="c4cb5-120">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="c4cb5-121">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="c4cb5-121">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
