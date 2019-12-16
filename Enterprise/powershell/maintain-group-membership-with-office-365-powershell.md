---
title: Mantener la pertenencia a grupos con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/06/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Obtenga información sobre cómo usar Office 365 PowerShell para mantener la pertenencia a grupos para Office 365.
ms.openlocfilehash: dfd3cad3f2e691930b5f4c754ee07205d3950e54
ms.sourcegitcommit: 7e65640fb1a86858a95c9ef0edbb58d0f171c5ee
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/06/2019
ms.locfileid: "39886666"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a><span data-ttu-id="caea9-103">Mantener la pertenencia a grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="caea9-103">Maintain group membership with Office 365 PowerShell</span></span>

<span data-ttu-id="caea9-104">Puede usar Office 365 PowerShell como una alternativa al centro de administración de Microsoft 365 para mantener la pertenencia a grupos en Office 365.</span><span class="sxs-lookup"><span data-stu-id="caea9-104">You can use Office 365 PowerShell as an alternative to the Microsoft 365 admin center to maintain group membership in Office 365.</span></span> 

> [!TIP]
> <span data-ttu-id="caea9-105">Para generar comandos de PowerShell listos para ejecutar mediante la especificación de nombres de grupos y cuentas de usuario, use este [libro de Microsoft Excel mantenimiento de grupos](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span><span class="sxs-lookup"><span data-stu-id="caea9-105">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="caea9-106">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="caea9-106">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="caea9-107">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="caea9-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="caea9-108">Agregar o quitar cuentas de usuario como miembros de un grupo</span><span class="sxs-lookup"><span data-stu-id="caea9-108">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="caea9-109">**Para agregar una cuenta de usuario por su UPN**, rellene el nombre principal de usuario (UPN) de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo, quitando los caracteres "<" y ">", y ejecute estos comandos en la ventana de PowerShell o en el entorno de scripting integrado (ISE) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="caea9-109">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="caea9-110">**Para agregar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-110">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="caea9-111">**Para quitar una cuenta de usuario por su UPN**, rellene el UPN de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-111">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="caea9-112">**Para quitar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-112">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="caea9-113">Agregar o quitar grupos como miembros de un grupo</span><span class="sxs-lookup"><span data-stu-id="caea9-113">Add or remove groups as members of a group</span></span>

<span data-ttu-id="caea9-114">Los grupos de seguridad pueden contener otros grupos como miembros.</span><span class="sxs-lookup"><span data-stu-id="caea9-114">Security groups can contain other groups as members.</span></span> <span data-ttu-id="caea9-115">Sin embargo, los grupos de Office 365 no pueden.</span><span class="sxs-lookup"><span data-stu-id="caea9-115">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="caea9-116">Esta sección contiene comandos de PowerShell para agregar o quitar grupos solo para un grupo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="caea9-116">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="caea9-117">**Para agregar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a agregar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-117">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="caea9-118">**Para quitar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a quitar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-118">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="caea9-119">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="caea9-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="caea9-120">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="caea9-120">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="caea9-121">Agregar o quitar cuentas de usuario como miembros de un grupo</span><span class="sxs-lookup"><span data-stu-id="caea9-121">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="caea9-122">**Para agregar una cuenta de usuario por su UPN**, rellene el nombre principal de usuario (UPN) de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo, quitando los caracteres "<" y ">" y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-122">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="caea9-123">**Para agregar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-123">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="caea9-124">**Para quitar una cuenta de usuario por su UPN**, rellene el UPN de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-124">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="caea9-125">**Para quitar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-125">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="caea9-126">Agregar o quitar grupos como miembros de un grupo</span><span class="sxs-lookup"><span data-stu-id="caea9-126">Add or remove groups as members of a group</span></span>

<span data-ttu-id="caea9-127">Los grupos de seguridad pueden contener otros grupos como miembros.</span><span class="sxs-lookup"><span data-stu-id="caea9-127">Security groups can contain other groups as members.</span></span> <span data-ttu-id="caea9-128">Sin embargo, los grupos de Office 365 no pueden.</span><span class="sxs-lookup"><span data-stu-id="caea9-128">Office 365 groups, however, cannot.</span></span> <span data-ttu-id="caea9-129">Esta sección contiene comandos de PowerShell para agregar o quitar grupos solo para un grupo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="caea9-129">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="caea9-130">**Para agregar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a agregar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-130">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="caea9-131">**Para quitar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a quitar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="caea9-131">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="caea9-132">Vea también</span><span class="sxs-lookup"><span data-stu-id="caea9-132">See also</span></span>

[<span data-ttu-id="caea9-133">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="caea9-133">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="caea9-134">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="caea9-134">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="caea9-135">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="caea9-135">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
