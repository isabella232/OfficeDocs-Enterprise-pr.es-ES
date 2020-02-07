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
f1.keywords:
- CSH
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Obtenga información sobre cómo usar Office 365 PowerShell para mantener la pertenencia a grupos para Office 365.
ms.openlocfilehash: 397f8d93df5e9abef0779e4eb56df7bab9ef2344
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841487"
---
# <a name="maintain-group-membership-with-office-365-powershell"></a>Mantener la pertenencia a grupos con Office 365 PowerShell

Puede usar Office 365 PowerShell como una alternativa al centro de administración de Microsoft 365 para mantener la pertenencia a grupos en Office 365. 

> [!TIP]
> Para generar comandos de PowerShell listos para ejecutar mediante la especificación de nombres de grupos y cuentas de usuario, use este [libro de Microsoft Excel mantenimiento de grupos](https://github.com/MicrosoftDocs/OfficeDocs-Enterprise/raw/live/Enterprise/media/maintain-group-membership-with-office-365-powershell/GroupMaintPowerShellGenerator.xlsx). 

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph
Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Agregar o quitar cuentas de usuario como miembros de un grupo

**Para agregar una cuenta de usuario por su UPN**, rellene el nombre principal de usuario (UPN) de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo, quitando los caracteres "<" y ">", y ejecute estos comandos en la ventana de PowerShell o en el entorno de scripting integrado (ISE) de PowerShell.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para agregar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para quitar una cuenta de usuario por su UPN**, rellene el UPN de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para quitar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADUser | Where { $_.DisplayName -eq $userName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Agregar o quitar grupos como miembros de un grupo

Los grupos de seguridad pueden contener otros grupos como miembros. Sin embargo, los grupos de Office 365 no pueden. Esta sección contiene comandos de PowerShell para agregar o quitar grupos solo para un grupo de seguridad.

**Para agregar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a agregar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-AzureADGroupMember -RefObjectId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para quitar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a quitar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Remove-AzureADGroupMember -MemberId (Get-AzureADGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -ObjectID (Get-AzureADGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).


### <a name="add-or-remove-user-accounts-as-members-of-a-group"></a>Agregar o quitar cuentas de usuario como miembros de un grupo

**Para agregar una cuenta de usuario por su UPN**, rellene el nombre principal de usuario (UPN) de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo, quitando los caracteres "<" y ">" y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para agregar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$userName="<display name of the user account to add>"
$groupName="<display name of the group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para quitar una cuenta de usuario por su UPN**, rellene el UPN de la cuenta de usuario (ejemplo: belindan@contoso.com) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$userUPN="<UPN of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.UserPrincipalName -eq $userUPN }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

**Para quitar una cuenta de usuario por su nombre para mostrar**, rellene el nombre para mostrar de la cuenta de usuario (ejemplo: Belinda Newman) y el nombre para mostrar del grupo y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$userName="<display name of the user account to remove>"
$groupName="<display name of the group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolUser | Where { $_.DisplayName -eq $userName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID
```

### <a name="add-or-remove-groups-as-members-of-a-group"></a>Agregar o quitar grupos como miembros de un grupo

Los grupos de seguridad pueden contener otros grupos como miembros. Sin embargo, los grupos de Office 365 no pueden. Esta sección contiene comandos de PowerShell para agregar o quitar grupos solo para un grupo de seguridad.

**Para agregar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a agregar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group that will contain the member group>"
Add-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

**Para quitar un grupo por su nombre para mostrar**, rellene el nombre para mostrar del grupo que va a quitar y el nombre para mostrar del grupo que contendrá el grupo de miembros y ejecute estos comandos en la ventana de PowerShell o en PowerShell ISE.

```powershell
$groupMemberName="<display name of the group to add>"
$groupName="<display name of the group contains the member group>"
Remove-MsolGroupMember -GroupMemberObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupMemberName }).ObjectID -GroupObjectId (Get-MsolGroup | Where { $_.DisplayName -eq $groupName }).ObjectID -GroupMemberType Group
```

## <a name="see-also"></a>Vea también

[Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

