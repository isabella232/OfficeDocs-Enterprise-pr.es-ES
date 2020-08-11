---
title: Asignar roles a cuentas de usuario de Microsoft 365 con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/16/2020
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
- seo-marvel-apr2020
ms.assetid: ede7598c-b5d5-4e3e-a488-195f02f26d93
description: En este artículo, obtenga información sobre cómo usar PowerShell para Microsoft 365 de forma rápida y sencilla para asignar roles a las cuentas de usuario.
ms.openlocfilehash: a3e1936dfa685c78f88e4f4333192f9a07de3cec
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46606446"
---
# <a name="assign-roles-to-microsoft-365-user-accounts-with-powershell"></a><span data-ttu-id="5f4cd-103">Asignar roles a cuentas de usuario de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f4cd-103">Assign roles to Microsoft 365 user accounts with PowerShell</span></span>

<span data-ttu-id="5f4cd-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="5f4cd-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="5f4cd-105">Puede asignar roles a cuentas de usuario de forma rápida y sencilla mediante PowerShell para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-105">You can quickly and easily assign roles to user accounts using PowerShell for Microsoft 365.</span></span>

>[!Note]
><span data-ttu-id="5f4cd-106">Para asignar roles a cuentas de usuario con el centro de administración de Microsoft 365, consulte [estas instrucciones](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="5f4cd-106">To assign roles to user accounts with the Microsoft 365 admin center, see [these instructions](https://docs.microsoft.com/microsoft-365/admin/add-users/assign-admin-roles).</span></span>
>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5f4cd-107">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="5f4cd-107">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5f4cd-108">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) con una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-108">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="5f4cd-109">A continuación, determine el nombre de inicio de sesión de la cuenta de usuario que desea agregar a un rol (ejemplo: fredsm@contoso.com).</span><span class="sxs-lookup"><span data-stu-id="5f4cd-109">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com).</span></span> <span data-ttu-id="5f4cd-110">Esto también se conoce como el nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="5f4cd-110">This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="5f4cd-111">A continuación, determine el nombre de la función.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-111">Next, determine the name of the role.</span></span> <span data-ttu-id="5f4cd-112">Use esta [lista de permisos de roles de administrador en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span><span class="sxs-lookup"><span data-stu-id="5f4cd-112">Use this [list of administrator role permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles).</span></span>

>[!Note]
><span data-ttu-id="5f4cd-113">Preste atención a las notas de este artículo.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-113">Pay attention to the notes in this article.</span></span> <span data-ttu-id="5f4cd-114">Algunos nombres de rol son diferentes para Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-114">Some role names are different for Azure AD PowerShell.</span></span> <span data-ttu-id="5f4cd-115">Por ejemplo, el rol "Administrador de SharePoint" en el centro de administración de Microsoft 365 se denomina "administrador del servicio de SharePoint" para Azure AD PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-115">For example, the "SharePoint Administrator" role in the Microsoft 365 admin center is named "SharePoint Service Administrator" for Azure AD PowerShell.</span></span>
>

<span data-ttu-id="5f4cd-116">A continuación, rellene los nombres de rol y de inicio de sesión y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-116">Next, fill in the sign-in and role names and run these commands.</span></span>
  
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

<span data-ttu-id="5f4cd-117">A continuación, se muestra un ejemplo de un conjunto de comandos completado que asigna el rol de administrador de servicios de SharePoint a la cuenta belindan@contoso.com:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-117">Here is an example of a completed command set that assigns the SharePoint Service Administrator role to the belindan@contoso.com account:</span></span>
  
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

<span data-ttu-id="5f4cd-118">Para mostrar la lista de nombres de usuario para una función específica, use estos comandos.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-118">To display the list of user names for a specific role, use these commands.</span></span>

```powershell
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5f4cd-119">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f4cd-119">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5f4cd-120">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) con una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-120">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="5f4cd-121">Para un cambio de función único</span><span class="sxs-lookup"><span data-stu-id="5f4cd-121">For a single role change</span></span>

<span data-ttu-id="5f4cd-122">Las formas más comunes de una cuenta de usuario específica es con su nombre para mostrar o su nombre de correo electrónico, también conocido como nombre de inicio de sesión o nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="5f4cd-122">The most common ways of specific user account is with its display name or its email name, also known its sign-in name or user principal name (UPN).</span></span>

#### <a name="display-names-of-user-accounts"></a><span data-ttu-id="5f4cd-123">Mostrar los nombres de las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="5f4cd-123">Display names of user accounts</span></span>

<span data-ttu-id="5f4cd-124">Si se usa para trabajar con los nombres para mostrar de las cuentas de usuario, determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-124">If you are used to working with the display names of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="5f4cd-125">La cuenta de usuario que desea configurar.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-125">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="5f4cd-126">Para especificar la cuenta de usuario, debe determinar su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-126">To specify the user account, you must determine its Display Name.</span></span> <span data-ttu-id="5f4cd-127">Para obtener una lista completa de cuentas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-127">To get a complete list accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="5f4cd-128">Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenados por nombre para mostrar, de una en una pantalla cada vez.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-128">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time.</span></span> <span data-ttu-id="5f4cd-129">Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="5f4cd-129">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="5f4cd-130">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-130">Here is an example:</span></span>

   >[!Note]
   ><span data-ttu-id="5f4cd-131">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-131">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="5f4cd-132">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-132">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
   >
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="5f4cd-133">Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".</span><span class="sxs-lookup"><span data-stu-id="5f4cd-133">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="5f4cd-134">El rol que desea asignar.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-134">The role you want to assign.</span></span>
    
    <span data-ttu-id="5f4cd-135">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-135">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="5f4cd-136">Una vez que haya determinado el nombre para mostrar de la cuenta y el nombre de la función, use estos comandos para asignar el rol a la cuenta:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-136">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="5f4cd-137">Copie los comandos y péguelos en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-137">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="5f4cd-138">Para las variables **$dispName** y **$roleName** , reemplace el texto de la descripción con sus valores, quite los \< and > caracteres y deje las comillas.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-138">For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="5f4cd-139">Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-139">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="5f4cd-140">Como alternativa, puede usar el entorno de script integrado (ISE) de Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-140">Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="5f4cd-141">A continuación, se muestra un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-141">Here is an example of a completed command set:</span></span>
  
```powershell
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser -All | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

#### <a name="sign-in-names-of-user-accounts"></a><span data-ttu-id="5f4cd-142">Nombres de inicio de sesión de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="5f4cd-142">Sign-in names of user accounts</span></span>

<span data-ttu-id="5f4cd-143">Si se usa para trabajar con los nombres de inicio de sesión o UPN de las cuentas de usuario, determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-143">If you are used to working with the sign-in names or UPNs of user accounts, determine the following:</span></span>
  
- <span data-ttu-id="5f4cd-144">El UPN de la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-144">The user account's UPN.</span></span>
    
    <span data-ttu-id="5f4cd-145">Si aún no conoce el UPN, use este comando:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-145">If you don't already know the UPN, use this command:</span></span>
    
  ```powershell
  Get-MsolUser -All | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="5f4cd-146">Este comando enumera el UPN de las cuentas de usuario, ordenados por el UPN, de una en una pantalla a la vez.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-146">This command lists the UPN of your user accounts, sorted by the UPN, one screen at a time.</span></span> <span data-ttu-id="5f4cd-147">Puede filtrar la lista para un conjunto más pequeño con el cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="5f4cd-147">You can filter the list to a smaller set by using the **Where** cmdlet.</span></span> <span data-ttu-id="5f4cd-148">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-148">Here is an example:</span></span>
    
  ```powershell
  Get-MsolUser -All | Where DisplayName -like "John*" | Sort UserPrincipalName | Select UserPrincipalName | More
  ```

    <span data-ttu-id="5f4cd-149">Este comando muestra sólo las cuentas de usuario para las que el nombre para mostrar empieza por "John".</span><span class="sxs-lookup"><span data-stu-id="5f4cd-149">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="5f4cd-150">El rol que desea asignar.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-150">The role you want to assign.</span></span>
    
    <span data-ttu-id="5f4cd-151">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-151">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="5f4cd-152">Una vez que tenga el UPN de la cuenta y el nombre del rol, use estos comandos para asignar el rol a la cuenta:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-152">Once you have the UPN of the account and the name of the role, use these commands to assign the role to the account:</span></span>
  
```powershell
$upnName="<The UPN of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

<span data-ttu-id="5f4cd-153">Copie los comandos y péguelos en el Bloc de notas.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-153">Copy the commands and paste them into Notepad.</span></span> <span data-ttu-id="5f4cd-154">Para las variables **$upnName** y **$roleName** , reemplace el texto de la descripción con sus valores, quite los \< and > caracteres y deje las comillas.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-154">For the **$upnName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes.</span></span> <span data-ttu-id="5f4cd-155">Copie las líneas modificadas y péguelas en su módulo de Windows Azure Active Directory para la ventana de Windows PowerShell para ejecutarlas.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-155">Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them.</span></span> <span data-ttu-id="5f4cd-156">Como alternativa, puede usar Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-156">Alternately, you can use the Windows PowerShell ISE.</span></span>
  
<span data-ttu-id="5f4cd-157">A continuación, se muestra un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-157">Here is an example of a completed command set:</span></span>
  
```powershell
$upnName="scottw@contoso.com"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress $upnName -RoleName $roleName
```

### <a name="multiple-role-changes"></a><span data-ttu-id="5f4cd-158">Varios cambios de funciones</span><span class="sxs-lookup"><span data-stu-id="5f4cd-158">Multiple role changes</span></span>

<span data-ttu-id="5f4cd-159">Para varios cambios de funciones, determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-159">For multiple role changes, determine the following:</span></span>
  
- <span data-ttu-id="5f4cd-160">Qué cuentas de usuario desea configurar.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-160">Which user accounts that you want to configure.</span></span> <span data-ttu-id="5f4cd-161">Puede usar los métodos de la sección anterior para recopilar el conjunto de nombres para mostrar o UPN.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-161">You can use the methods in the previous section to gather the set of display names or UPNs.</span></span>
    
- <span data-ttu-id="5f4cd-162">Qué roles desea asignar a cada cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-162">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="5f4cd-163">Para mostrar la lista de los roles disponibles que puede asignar a las cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-163">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```powershell
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="5f4cd-164">A continuación, cree un archivo de texto de valores separados por comas (CSV) que tenga los campos nombre para mostrar o nombre de rol y UPN.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-164">Next, create a comma-separated value (CSV) text file that has the display name or UPN and role name fields.</span></span> <span data-ttu-id="5f4cd-165">Puede hacerlo fácilmente con Microsoft Excel.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-165">You can do this easily with Microsoft Excel.</span></span>

<span data-ttu-id="5f4cd-166">Este es un ejemplo de nombres para mostrar:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-166">Here is an example for display names:</span></span>
  
```powershell
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"Scott Wallace","SharePoint Service Administrator"
```

<span data-ttu-id="5f4cd-167">A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-167">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

<span data-ttu-id="5f4cd-168">Este es un ejemplo para los UPN:</span><span class="sxs-lookup"><span data-stu-id="5f4cd-168">Here is an example for UPNs:</span></span>
  
```powershell
UserPrincipalName,RoleName
"belindan@contoso.com","Billing Administrator"
"scottw@contoso.com","SharePoint Service Administrator"
```

<span data-ttu-id="5f4cd-169">A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5f4cd-169">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```powershell
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach { Add-MsolRoleMember -RoleMemberEmailAddress $_.UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="5f4cd-170">Ver también</span><span class="sxs-lookup"><span data-stu-id="5f4cd-170">See also</span></span>

- [<span data-ttu-id="5f4cd-171">Administrar cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f4cd-171">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="5f4cd-172">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="5f4cd-172">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="5f4cd-173">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="5f4cd-173">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
