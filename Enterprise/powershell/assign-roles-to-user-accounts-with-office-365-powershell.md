---
title: Asignar roles a cuentas de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/18/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Resumen: Use Office 365 PowerShell para asignar roles a cuentas de usuario.'
ms.openlocfilehash: 78f2e08df6d46588b93dc217d0e16b7c3a350a88
ms.sourcegitcommit: 85974a1891ac45286efa13cc76eefa3cce28fc22
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/30/2019
ms.locfileid: "33491996"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d592a-103">Asignar roles a cuentas de usuario con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d592a-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d592a-104">Puede asignar roles a cuentas de usuario de forma rápida y sencilla mediante Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d592a-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d592a-105">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="d592a-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d592a-106">En primer lugar, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) con una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="d592a-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="d592a-107">A continuación, determine el nombre de inicio de sesión de la cuenta de usuario que desea agregar a un rol (ejemplo: fredsm@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="d592a-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="d592a-108">Esto también se conoce como el nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="d592a-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="d592a-109">A continuación, determine el nombre de la función.</span><span class="sxs-lookup"><span data-stu-id="d592a-109">Next, determine the name of the role.</span></span> <span data-ttu-id="d592a-110">Use esta [lista de permisos de roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="d592a-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="d592a-111">Preste atención a las notas de este artículo.</span><span class="sxs-lookup"><span data-stu-id="d592a-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="d592a-112">Algunos nombres de rol son diferentes para Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d592a-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="d592a-113">Por ejemplo, el rol "Administrador de SharePoint" en el centro de administración de Microsoft 365 se denomina "administrador del servicio de SharePoint" para Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d592a-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="d592a-114">A continuación, rellene los nombres de rol y de inicio de sesión y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="d592a-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="d592a-115">A continuación, se muestra un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="d592a-115">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="SharePoint Service Administrator"
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
if ($role -eq $null) {
$roleTemplate = Get-AzureADDirectoryRoleTemplate | Where {$_.displayName -eq $roleName}
Enable-AzureADDirectoryRole -RoleTemplateId $roleTemplate.ObjectId
$role = Get-AzureADDirectoryRole | Where {$_.displayName -eq $roleName}
}
Add-AzureADDirectoryRoleMember -ObjectId $role.ObjectId -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="d592a-116">Para mostrar la lista de nombres de usuario para una función específica, use estos comandos.</span><span class="sxs-lookup"><span data-stu-id="d592a-116">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d592a-117">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d592a-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d592a-118">En primer lugar, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="d592a-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="d592a-119">Para un cambio de función único</span><span class="sxs-lookup"><span data-stu-id="d592a-119">For a single role change</span></span>

<span data-ttu-id="d592a-120">Determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d592a-120">Determine the following:</span></span>
  
- <span data-ttu-id="d592a-121">La cuenta de usuario que desea configurar.</span><span class="sxs-lookup"><span data-stu-id="d592a-121">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="d592a-122">Para especificar la cuenta de usuario, debe determinar su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="d592a-122">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="d592a-123">Para obtener una lista completa de cuentas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d592a-123">To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d592a-124">Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenados por nombre para mostrar, de una en una pantalla cada vez.</span><span class="sxs-lookup"><span data-stu-id="d592a-124">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="d592a-125">Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="d592a-125">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="d592a-126">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d592a-126">Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d592a-127">Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".</span><span class="sxs-lookup"><span data-stu-id="d592a-127">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="d592a-128">El rol que desea asignar.</span><span class="sxs-lookup"><span data-stu-id="d592a-128">The role you want to assign.</span></span>
    
    <span data-ttu-id="d592a-129">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d592a-129">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="d592a-130">Una vez que haya determinado el nombre para mostrar de la cuenta y el nombre de la función, use estos comandos para asignar el rol a la cuenta:</span><span class="sxs-lookup"><span data-stu-id="d592a-130">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="d592a-131">Copie los comandos y péguelos en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="d592a-131">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="d592a-132">Para las variables **$dispName** y **$roleName** , reemplace el texto de la descripción con sus valores, \< Quite los caracteres y > y deje las comillas.</span><span class="sxs-lookup"><span data-stu-id="d592a-132">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="d592a-133">Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas.</span><span class="sxs-lookup"><span data-stu-id="d592a-133">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="d592a-134">Como alternativa, puede usar el entorno de script integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d592a-134">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="d592a-135">A continuación, se muestra un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="d592a-135">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="d592a-136">Para varios cambios de funciones</span><span class="sxs-lookup"><span data-stu-id="d592a-136">For multiple role changes</span></span>

<span data-ttu-id="d592a-137">Determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d592a-137">Determine the following:</span></span>
  
- <span data-ttu-id="d592a-138">Qué cuentas de usuario desea configurar.</span><span class="sxs-lookup"><span data-stu-id="d592a-138">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="d592a-139">Para especificar la cuenta de usuario, debe determinar su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="d592a-139">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="d592a-140">Para obtener una lista de cuentas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d592a-140">To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d592a-141">Este comando muestra el nombre para mostrar de todas las cuentas de usuario, ordenados por el nombre para mostrar, una pantalla cada vez.</span><span class="sxs-lookup"><span data-stu-id="d592a-141">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="d592a-142">Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="d592a-142">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="d592a-143">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d592a-143">Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d592a-144">Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".</span><span class="sxs-lookup"><span data-stu-id="d592a-144">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="d592a-145">Qué roles desea asignar a cada cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="d592a-145">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="d592a-146">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d592a-146">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="d592a-147">A continuación, cree un archivo de texto de valores separados por comas (CSV) que contenga los campos DisplayName y nombre de rol.</span><span class="sxs-lookup"><span data-stu-id="d592a-147">Next, create a comma-separated value (CSV) text file that has the DisplayName and role Name fields.</span></span> <span data-ttu-id="d592a-148">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d592a-148">Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="d592a-149">A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d592a-149">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="d592a-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="d592a-150">See also</span></span>

- [<span data-ttu-id="d592a-151">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d592a-151">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="d592a-152">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d592a-152">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="d592a-153">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d592a-153">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
