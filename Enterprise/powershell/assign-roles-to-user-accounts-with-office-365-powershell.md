---
title: Asignar roles a cuentas de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 06/09/2020
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
- O365ITProTrain
- PowerShell
- Ent_Office_Other
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: 'Resumen: Use Office 365 PowerShell para asignar roles a cuentas de usuario.'
ms.openlocfilehash: 9a28ff27138b689ed0325580af956a90d7eb7982
ms.sourcegitcommit: ff1d21fe5eb8eba7a65d250aa37aadc8f503a10a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/11/2020
ms.locfileid: "44698917"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="d45af-103">Asignar roles a cuentas de usuario con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d45af-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="d45af-104">Puede asignar roles a cuentas de usuario de forma rápida y sencilla mediante Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d45af-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

>[!Note]
><span data-ttu-id="d45af-105">Para asignar roles a cuentas de usuario con el centro de administración de Microsoft 365, consulte [estas instrucciones](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="d45af-105">To assign roles to user accounts with the Microsoft 365 admin center, see [these instructions](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles).</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d45af-106">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="d45af-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d45af-107">En primer lugar, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) con una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="d45af-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="d45af-108">A continuación, determine el nombre de inicio de sesión de la cuenta de usuario que desea agregar a un rol (ejemplo: fredsm@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="d45af-108">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="d45af-109">Esto también se conoce como el nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="d45af-109">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="d45af-110">A continuación, determine el nombre de la función.</span><span class="sxs-lookup"><span data-stu-id="d45af-110">Next, determine the name of the role.</span></span> <span data-ttu-id="d45af-111">Use esta [lista de permisos de roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="d45af-111">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="d45af-112">Preste atención a las notas de este artículo.</span><span class="sxs-lookup"><span data-stu-id="d45af-112">Pay attention to the notes in this article.</span></span> <span data-ttu-id="d45af-113">Algunos nombres de rol son diferentes para Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d45af-113">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="d45af-114">Por ejemplo, el rol "Administrador de SharePoint" en el centro de administración de Microsoft 365 se denomina "administrador del servicio de SharePoint" para Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d45af-114">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="d45af-115">A continuación, rellene los nombres de rol y de inicio de sesión y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="d45af-115">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```powershell
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

<span data-ttu-id="d45af-116">A continuación, se muestra un ejemplo de un conjunto de comandos completado que asigna el rol de administrador de servicios de SharePoint a la cuenta belindan@contoso.com:</span><span class="sxs-lookup"><span data-stu-id="d45af-116">Here is an example of a completed command set that assigns the SharePoint Service Administrator role to the belindan@contoso.com account:</span></span>
  
```powershell
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

<span data-ttu-id="d45af-117">Para mostrar la lista de nombres de usuario para una función específica, use estos comandos.</span><span class="sxs-lookup"><span data-stu-id="d45af-117">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d45af-118">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d45af-118">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d45af-119">En primer lugar, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="d45af-119">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="d45af-120">Para un cambio de función único</span><span class="sxs-lookup"><span data-stu-id="d45af-120">For a single role change</span></span>

<span data-ttu-id="d45af-121">Las formas más comunes de una cuenta de usuario específica es con su nombre para mostrar o su nombre de correo electrónico, también conocido como nombre de inicio de sesión o nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="d45af-121">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="d45af-122">Mostrar los nombres de las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d45af-122">Display names of user accounts</span></span>

<span data-ttu-id="d45af-123">Si se usa para trabajar con los nombres para mostrar de las cuentas de usuario, determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d45af-123">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="d45af-124">La cuenta de usuario que desea configurar.</span><span class="sxs-lookup"><span data-stu-id="d45af-124">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="d45af-125">Para especificar la cuenta de usuario, debe determinar su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="d45af-125">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="d45af-126">Para obtener una lista completa de cuentas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d45af-126">To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d45af-127">Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenados por nombre para mostrar, de una en una pantalla cada vez.</span><span class="sxs-lookup"><span data-stu-id="d45af-127">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="d45af-128">Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="d45af-128">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="d45af-129">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d45af-129">Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="d45af-130">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="d45af-130">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d45af-131">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d45af-131">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="d45af-132">Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".</span><span class="sxs-lookup"><span data-stu-id="d45af-132">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="d45af-133">El rol que desea asignar.</span><span class="sxs-lookup"><span data-stu-id="d45af-133">The role you want to assign.</span></span>
    
    <span data-ttu-id="d45af-134">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d45af-134">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="d45af-135">Una vez que haya determinado el nombre para mostrar de la cuenta y el nombre de la función, use estos comandos para asignar el rol a la cuenta:</span><span class="sxs-lookup"><span data-stu-id="d45af-135">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="d45af-136">Copie los comandos y péguelos en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="d45af-136">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="d45af-137">Para las variables **$dispName** y **$roleName** , reemplace el texto de la descripción con sus valores, quite los \< and > caracteres y deje las comillas.</span><span class="sxs-lookup"><span data-stu-id="d45af-137">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="d45af-138">Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas.</span><span class="sxs-lookup"><span data-stu-id="d45af-138">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="d45af-139">Como alternativa, puede usar el entorno de script integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d45af-139">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="d45af-140">A continuación, se muestra un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="d45af-140">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="d45af-141">Nombres de inicio de sesión de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d45af-141">Sign-in names of user accounts</span></span>

<span data-ttu-id="d45af-142">Si se usa para trabajar con los nombres de inicio de sesión o UPN de las cuentas de usuario, determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d45af-142">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="d45af-143">El UPN de la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="d45af-143">The user account's UPN.</span></span>
    
    <span data-ttu-id="d45af-144">Si aún no conoce el UPN, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d45af-144">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="d45af-145">Este comando enumera el UPN de las cuentas de usuario, ordenados por el UPN, de una en una pantalla a la vez.</span><span class="sxs-lookup"><span data-stu-id="d45af-145">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="d45af-146">Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="d45af-146">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="d45af-147">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d45af-147">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="d45af-148">Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".</span><span class="sxs-lookup"><span data-stu-id="d45af-148">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="d45af-149">El rol que desea asignar.</span><span class="sxs-lookup"><span data-stu-id="d45af-149">The role you want to assign.</span></span>
    
    <span data-ttu-id="d45af-150">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d45af-150">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="d45af-151">Una vez que tenga el UPN de la cuenta y el nombre del rol, use estos comandos para asignar el rol a la cuenta:</span><span class="sxs-lookup"><span data-stu-id="d45af-151">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="d45af-152">Copie los comandos y péguelos en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="d45af-152">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="d45af-153">Para las variables **$upnName** y **$roleName** , reemplace el texto de la descripción con sus valores, quite los \< and > caracteres y deje las comillas.</span><span class="sxs-lookup"><span data-stu-id="d45af-153">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="d45af-154">Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas.</span><span class="sxs-lookup"><span data-stu-id="d45af-154">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="d45af-155">Como alternativa, puede usar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d45af-155">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="d45af-156">A continuación, se muestra un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="d45af-156">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="d45af-157">Varios cambios de funciones</span><span class="sxs-lookup"><span data-stu-id="d45af-157">Multiple role changes</span></span>

<span data-ttu-id="d45af-158">Para varios cambios de funciones, determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="d45af-158">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="d45af-159">Qué cuentas de usuario desea configurar.</span><span class="sxs-lookup"><span data-stu-id="d45af-159">Which user accounts that you want to configure.</span></span> <span data-ttu-id="d45af-160">Puede usar los métodos de la sección anterior para recopilar el conjunto de nombres para mostrar o UPN.</span><span class="sxs-lookup"><span data-stu-id="d45af-160">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="d45af-161">Qué roles desea asignar a cada cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="d45af-161">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="d45af-162">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="d45af-162">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="d45af-163">A continuación, cree un archivo de texto de valores separados por comas (CSV) que tenga los campos nombre para mostrar o nombre de rol y UPN.</span><span class="sxs-lookup"><span data-stu-id="d45af-163">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="d45af-164">Puede hacerlo fácilmente con Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="d45af-164">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="d45af-165">Este es un ejemplo de nombres para mostrar:</span><span class="sxs-lookup"><span data-stu-id="d45af-165">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="d45af-166">A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d45af-166">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="d45af-167">Este es un ejemplo para los UPN:</span><span class="sxs-lookup"><span data-stu-id="d45af-167">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="d45af-168">A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d45af-168">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="d45af-169">Vea también</span><span class="sxs-lookup"><span data-stu-id="d45af-169">See also</span></span>

- [<span data-ttu-id="d45af-170">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d45af-170">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="d45af-171">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d45af-171">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="d45af-172">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d45af-172">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
