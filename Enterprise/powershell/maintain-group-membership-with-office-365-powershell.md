---
title: Mantener la pertenencia a grupos de Microsoft 365 con PowerShell
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
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Obtenga información sobre cómo usar PowerShell para mantener la pertenencia a grupos de Microsoft 365.
ms.openlocfilehash: f75587c9c50a1fce3a5abfb00ddba2845318e9c4
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230656"
---
# <a name="maintain-microsoft-365-group-membership-with-powershell"></a><span data-ttu-id="fa140-103">Mantener la pertenencia a grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa140-103">Maintain Microsoft 365 group membership with PowerShell</span></span>

<span data-ttu-id="fa140-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="fa140-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="fa140-105">Puede usar PowerShell para Microsoft 365 como una alternativa al centro de administración de Microsoft 365 para mantener la pertenencia a grupos en Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="fa140-105">You can use PowerShell for Microsoft 365 as an alternative to the Microsoft 365 admin center to maintain group membership in Microsoft 365.</span></span> 

> [!TIP]
> <span data-ttu-id="fa140-106">Para generar comandos de PowerShell listos para ejecutar mediante la especificación de nombres de grupos y cuentas de usuario, use este [libro de Microsoft Excel mantenimiento de grupos](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span><span class="sxs-lookup"><span data-stu-id="fa140-106">To generate ready-to-run PowerShell commands by specifying user account and group names, use this [group maintenance Microsoft Excel workbook](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx).</span></span> 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="fa140-107">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="fa140-107">Use the Azure Active Directory PowerShell for Graph module</span></span>
<span data-ttu-id="fa140-108">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="fa140-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="fa140-109">Agregar o quitar cuentas de usuario como miembros de un grupo</span><span class="sxs-lookup"><span data-stu-id="fa140-109">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="fa140-110">**Para agregar una cuenta de usuario por su UPN**, rellene el nombre principal de usuario (UPN) de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo, quitando los caracteres "<" y ">", y ejecute estos comandos en la ventana de PowerShell o en el entorno de scripting integrado (ISE) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fa140-110">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell Integrated Script Environment (ISE).</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="fa140-111">**Para agregar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-111">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="fa140-112">**Para quitar una cuenta de usuario por su UPN**, rellene el UPN de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-112">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="fa140-113">**Para quitar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-113">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="fa140-114">Agregar o quitar grupos como miembros de un grupo</span><span class="sxs-lookup"><span data-stu-id="fa140-114">Add or remove groups as members of a group</span></span>

<span data-ttu-id="fa140-115">Los grupos de seguridad pueden contener otros grupos como miembros.</span><span class="sxs-lookup"><span data-stu-id="fa140-115">Security groups can contain other groups as members.</span></span> <span data-ttu-id="fa140-116">No obstante, los grupos de Microsoft 365 no pueden.</span><span class="sxs-lookup"><span data-stu-id="fa140-116">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="fa140-117">Esta sección contiene comandos de PowerShell para agregar o quitar grupos solo para un grupo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="fa140-117">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="fa140-118">**Para agregar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a agregar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-118">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="fa140-119">**Para quitar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a quitar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-119">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="fa140-120">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa140-120">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="fa140-121">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="fa140-121">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a><span data-ttu-id="fa140-122">Agregar o quitar cuentas de usuario como miembros de un grupo</span><span class="sxs-lookup"><span data-stu-id="fa140-122">Add or remove user accounts as members of a group</span></span>

<span data-ttu-id="fa140-123">**Para agregar una cuenta de usuario por su UPN**, rellene el nombre principal de usuario (UPN) de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo, quitando los caracteres "<" y ">" y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-123">**To add a user account by its UPN**, fill in the user account User Principal Name (UPN) (example: belindan@contoso.com) and the group display name, removing the “<” and “>” characters, and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="fa140-124">**Para agregar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-124">**To add a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="fa140-125">**Para quitar una cuenta de usuario por su UPN**, rellene el UPN de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-125">**To remove a user account by its UPN**, fill in the user account UPN (example: belindan@contoso.com) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

<span data-ttu-id="fa140-126">**Para quitar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-126">**To remove a user account by its display name**, fill in the user account display name (example: Belinda Newman) and the group display name and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a><span data-ttu-id="fa140-127">Agregar o quitar grupos como miembros de un grupo</span><span class="sxs-lookup"><span data-stu-id="fa140-127">Add or remove groups as members of a group</span></span>

<span data-ttu-id="fa140-128">Los grupos de seguridad pueden contener otros grupos como miembros.</span><span class="sxs-lookup"><span data-stu-id="fa140-128">Security groups can contain other groups as members.</span></span> <span data-ttu-id="fa140-129">No obstante, los grupos de Microsoft 365 no pueden.</span><span class="sxs-lookup"><span data-stu-id="fa140-129">Microsoft 365 groups, however, cannot.</span></span> <span data-ttu-id="fa140-130">Esta sección contiene comandos de PowerShell para agregar o quitar grupos solo para un grupo de seguridad.</span><span class="sxs-lookup"><span data-stu-id="fa140-130">This section contains PowerShell commands to add or remove groups only for a security group.</span></span>

<span data-ttu-id="fa140-131">**Para agregar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a agregar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-131">**To add a group by its display name**, fill in the display name of the group you’re going to add and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

<span data-ttu-id="fa140-132">**Para quitar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a quitar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="fa140-132">**To remove a group by its display name**, fill in the display name of the group you’re going to remove and the display name of the group that will contain the member group and run these commands in the PowerShell window or the PowerShell ISE.</span></span>

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a><span data-ttu-id="fa140-133">Consulte también</span><span class="sxs-lookup"><span data-stu-id="fa140-133">See also</span></span>

[<span data-ttu-id="fa140-134">Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa140-134">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="fa140-135">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="fa140-135">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fa140-136">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="fa140-136">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)

