---
title: Asignar roles a cuentas de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/30/2019
audience: Admin
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
ms.openlocfilehash: d06b305c348d014ce526448d7f8401c26f4d1c47
ms.sourcegitcommit: 3100813cd7dff8b27b1a30a6d6ed5a7c4765c60f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/30/2019
ms.locfileid: "34586986"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="38fa8-103">Asignar roles a cuentas de usuario con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="38fa8-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="38fa8-104">Puede asignar roles a cuentas de usuario de forma rápida y sencilla mediante Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38fa8-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="38fa8-105">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="38fa8-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="38fa8-106">En primer lugar, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) con una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="38fa8-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="38fa8-107">A continuación, determine el nombre de inicio de sesión de la cuenta de usuario que desea agregar a un rol (ejemplo: fredsm@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="38fa8-107">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="38fa8-108">Esto también se conoce como el nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="38fa8-108">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="38fa8-109">A continuación, determine el nombre de la función.</span><span class="sxs-lookup"><span data-stu-id="38fa8-109">Next, determine the name of the role.</span></span> <span data-ttu-id="38fa8-110">Use esta [lista de permisos de roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="38fa8-110">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="38fa8-111">Preste atención a las notas de este artículo.</span><span class="sxs-lookup"><span data-stu-id="38fa8-111">Pay attention to the notes in this article.</span></span> <span data-ttu-id="38fa8-112">Algunos nombres de rol son diferentes para Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38fa8-112">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="38fa8-113">Por ejemplo, el rol "Administrador de SharePoint" en el centro de administración de Microsoft 365 se denomina "administrador del servicio de SharePoint" para Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38fa8-113">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="38fa8-114">A continuación, rellene los nombres de rol y de inicio de sesión y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="38fa8-114">Next, fill in the sign-in and role names and run these commands.</span></span>
  
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

<span data-ttu-id="38fa8-115">A continuación, se muestra un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="38fa8-115">Here is an example of a completed command set:</span></span>
  
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

<span data-ttu-id="38fa8-116">Para mostrar la lista de nombres de usuario para una función específica, use estos comandos.</span><span class="sxs-lookup"><span data-stu-id="38fa8-116">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="38fa8-117">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="38fa8-117">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="38fa8-118">En primer lugar, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="38fa8-118">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="38fa8-119">Para un cambio de función único</span><span class="sxs-lookup"><span data-stu-id="38fa8-119">For a single role change</span></span>

<span data-ttu-id="38fa8-120">Las formas más comunes de tener una cuenta de usuario específica son con su nombre para mostrar o su nombre de correo electrónico, también conocido como nombre principal de usuario (UPN) de nombre de inicio de sesión.</span><span class="sxs-lookup"><span data-stu-id="38fa8-120">The most common ways of specific user account is with its display name or its email name, also known its sign-in name user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="38fa8-121">Mostrar los nombres de las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="38fa8-121">Display names of user accounts</span></span>

<span data-ttu-id="38fa8-122">Si se usa para trabajar con los nombres para mostrar de las cuentas de usuario, determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="38fa8-122">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="38fa8-123">La cuenta de usuario que desea configurar.</span><span class="sxs-lookup"><span data-stu-id="38fa8-123">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="38fa8-124">Para especificar la cuenta de usuario, debe determinar su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="38fa8-124">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="38fa8-125">Para obtener una lista completa de cuentas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="38fa8-125">To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="38fa8-126">Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenados por nombre para mostrar, de una en una pantalla cada vez.</span><span class="sxs-lookup"><span data-stu-id="38fa8-126">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="38fa8-127">Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="38fa8-127">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="38fa8-128">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="38fa8-128">Here is an example:</span></span>
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="38fa8-129">Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".</span><span class="sxs-lookup"><span data-stu-id="38fa8-129">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="38fa8-130">El rol que desea asignar.</span><span class="sxs-lookup"><span data-stu-id="38fa8-130">The role you want to assign.</span></span>
    
    <span data-ttu-id="38fa8-131">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="38fa8-131">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="38fa8-132">Una vez que haya determinado el nombre para mostrar de la cuenta y el nombre de la función, use estos comandos para asignar el rol a la cuenta:</span><span class="sxs-lookup"><span data-stu-id="38fa8-132">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="38fa8-133">Copie los comandos y péguelos en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="38fa8-133">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="38fa8-134">Para las variables **$dispName** y **$roleName** , reemplace el texto de la descripción con sus valores, \< Quite los caracteres y > y deje las comillas.</span><span class="sxs-lookup"><span data-stu-id="38fa8-134">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="38fa8-135">Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas.</span><span class="sxs-lookup"><span data-stu-id="38fa8-135">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="38fa8-136">Como alternativa, puede usar el entorno de script integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38fa8-136">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="38fa8-137">A continuación, se muestra un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="38fa8-137">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="38fa8-138">Nombres de inicio de sesión de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="38fa8-138">Sign-in names of user accounts</span></span>

<span data-ttu-id="38fa8-139">Si se usa para trabajar con los nombres de inicio de sesión o UPN de las cuentas de usuario, determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="38fa8-139">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="38fa8-140">El UPN de la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="38fa8-140">The user account's UPN.</span></span>
    
    <span data-ttu-id="38fa8-141">Si aún no conoce el UPN, use este comando:</span><span class="sxs-lookup"><span data-stu-id="38fa8-141">If you don't already know the UPN, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="38fa8-142">Este comando enumera el UPN de las cuentas de usuario, ordenados por el UPN, de una en una pantalla a la vez.</span><span class="sxs-lookup"><span data-stu-id="38fa8-142">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="38fa8-143">Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="38fa8-143">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="38fa8-144">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="38fa8-144">Here is an example:</span></span>
    
  ```
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="38fa8-145">Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".</span><span class="sxs-lookup"><span data-stu-id="38fa8-145">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="38fa8-146">El rol que desea asignar.</span><span class="sxs-lookup"><span data-stu-id="38fa8-146">The role you want to assign.</span></span>
    
    <span data-ttu-id="38fa8-147">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="38fa8-147">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="38fa8-148">Una vez que tenga el UPN de la cuenta y el nombre del rol, use estos comandos para asignar el rol a la cuenta:</span><span class="sxs-lookup"><span data-stu-id="38fa8-148">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="38fa8-149">Copie los comandos y péguelos en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="38fa8-149">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="38fa8-150">Para las variables **$upnName** y **$roleName** , reemplace el texto de la descripción con sus valores, \< Quite los caracteres y > y deje las comillas.</span><span class="sxs-lookup"><span data-stu-id="38fa8-150">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="38fa8-151">Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas.</span><span class="sxs-lookup"><span data-stu-id="38fa8-151">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="38fa8-152">Como alternativa, puede usar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="38fa8-152">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="38fa8-153">A continuación, se muestra un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="38fa8-153">Here is an example of a completed command set:</span></span>
  
```
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="38fa8-154">Para varios cambios de funciones</span><span class="sxs-lookup"><span data-stu-id="38fa8-154">For multiple role changes</span></span>

<span data-ttu-id="38fa8-155">Determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="38fa8-155">Determine the following:</span></span>
  
- <span data-ttu-id="38fa8-156">Qué cuentas de usuario desea configurar.</span><span class="sxs-lookup"><span data-stu-id="38fa8-156">Which user accounts that you want to configure.</span></span> <span data-ttu-id="38fa8-157">Puede usar los métodos de la sección anterior para recopilar el conjunto de nombres para mostrar o UPN.</span><span class="sxs-lookup"><span data-stu-id="38fa8-157">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="38fa8-158">Qué roles desea asignar a cada cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="38fa8-158">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="38fa8-159">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="38fa8-159">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="38fa8-160">A continuación, cree un archivo de texto de valores separados por comas (CSV) que tenga los campos nombre para mostrar o nombre de rol y UPN.</span><span class="sxs-lookup"><span data-stu-id="38fa8-160">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="38fa8-161">Puede hacerlo fácilmente con Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="38fa8-161">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="38fa8-162">Este es un ejemplo de nombres para mostrar:</span><span class="sxs-lookup"><span data-stu-id="38fa8-162">Here is an example for display names:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="38fa8-163">A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38fa8-163">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="38fa8-164">Este es un ejemplo para los UPN:</span><span class="sxs-lookup"><span data-stu-id="38fa8-164">Here is an example for UPNs:</span></span>
  
```
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="38fa8-165">A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38fa8-165">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```


## <a name="see-also"></a><span data-ttu-id="38fa8-166">Vea también</span><span class="sxs-lookup"><span data-stu-id="38fa8-166">See also</span></span>

- [<span data-ttu-id="38fa8-167">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="38fa8-167">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="38fa8-168">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="38fa8-168">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="38fa8-169">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="38fa8-169">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
