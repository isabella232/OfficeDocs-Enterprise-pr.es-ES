---
title: Asignar roles a cuentas de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/31/2019
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
description: 'Resumen: Use PowerShell de Office 365 para asignar roles a cuentas de usuario.'
ms.openlocfilehash: 702c7358ccca9bb36bd106d742b5c454283ee8b4
ms.sourcegitcommit: d0c870c7a487eda48b11f649b30e4818fd5608aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2019
ms.locfileid: "29690441"
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="a5247-103">Asignar roles a cuentas de usuario con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5247-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="a5247-104">Puede asignar rápida y fácilmente la roles a cuentas de usuario con PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="a5247-104">You can quickly and easily assign roles to user accounts using Office 365 PowerShell.</span></span>

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="a5247-105">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="a5247-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="a5247-106">Primero, [conectarse a su inquilino Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) utilizando una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a5247-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module) using a global administrator account.</span></span>
  
<span data-ttu-id="a5247-p101">A continuación, determine el nombre de inicio de sesión de la cuenta de usuario que desea agregar a una función (ejemplo: fredsm@contoso.com). Esto es también conocido como el nombre principal de usuario (UPN).</span><span class="sxs-lookup"><span data-stu-id="a5247-p101">Next, determine the sign-in name of the user account that you want to add to a role (example: fredsm@contoso.com). This is also known as the user principal name (UPN).</span></span>

<span data-ttu-id="a5247-p102">A continuación, determine el nombre de la función. Use este comando para obtener una lista de las funciones que se pueden asignar con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5247-p102">Next, determine the name of the role. Use this command to list the roles that you can assign with PowerShell.</span></span>

````
Get-AzureADDirectoryRole
````

<span data-ttu-id="a5247-111">A continuación, rellene los nombres de inicio de sesión y la función y ejecute estos comandos.</span><span class="sxs-lookup"><span data-stu-id="a5247-111">Next, fill in the sign-in and role names and run these commands.</span></span>
  
```
$userName="<sign-in name of the account>"
$roleName="<role name>"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="a5247-112">Este es un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="a5247-112">Here is an example of a completed command set:</span></span>
  
```
$userName="belindan@contoso.com"
$roleName="Lync Service Administrator"
Add-AzureADDirectoryRoleMember -ObjectId (Get-AzureADDirectoryRole | Where {$_.DisplayName -eq $roleName}).ObjectID -RefObjectId (Get-AzureADUser | Where {$_.UserPrincipalName -eq $userName}).ObjectID
```

<span data-ttu-id="a5247-113">Para mostrar la lista de nombres de usuario para un rol específico, use estos comandos.</span><span class="sxs-lookup"><span data-stu-id="a5247-113">To display the list of user names for a specific role, use these commands.</span></span>

```
$roleName="<role name>"
Get-AzureADDirectoryRole | Where { $_.DisplayName -eq $roleName } | Get-AzureADDirectoryRoleMember | Ft DisplayName
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="a5247-114">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a5247-114">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="a5247-115">Primero, [conectarse a su inquilino Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) utilizando una cuenta de administrador global.</span><span class="sxs-lookup"><span data-stu-id="a5247-115">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) using a global administrator account.</span></span>
  
### <a name="for-a-single-role-change"></a><span data-ttu-id="a5247-116">Para un cambio de función única</span><span class="sxs-lookup"><span data-stu-id="a5247-116">For a single role change</span></span>

<span data-ttu-id="a5247-117">Determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a5247-117">Determine the following:</span></span>
  
- <span data-ttu-id="a5247-118">La cuenta de usuario que desea configurar.</span><span class="sxs-lookup"><span data-stu-id="a5247-118">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="a5247-p103">Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista completa de las cuentas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="a5247-p103">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a5247-p104">Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenadas por el nombre para mostrar, una pantalla a la vez. Puede filtrar la lista a un conjunto más pequeño mediante el cmdlet **donde** . Este es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a5247-p104">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a5247-124">Este comando enumera sólo las cuentas de usuario para el que el nombre para mostrar comienza por "John".</span><span class="sxs-lookup"><span data-stu-id="a5247-124">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="a5247-125">La función que desea asignar.</span><span class="sxs-lookup"><span data-stu-id="a5247-125">The role you want to assign.</span></span>
    
    <span data-ttu-id="a5247-126">Para mostrar la lista de roles disponibles que se pueden asignar a cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="a5247-126">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="a5247-127">Una vez que haya determinado el nombre para mostrar de la cuenta y el nombre de la función, utilice estos comandos para asignar el rol a la cuenta:</span><span class="sxs-lookup"><span data-stu-id="a5247-127">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="a5247-p105">Copie los comandos y péguelos en el Bloc de notas. Para las variables **$dispName** y **$roleName** , reemplace el texto de descripción con sus valores, quite el \< y > caracteres y deje las comillas. Copie las líneas modificadas y péguelas en la ventana de Windows Azure Active Directory módulo para Windows PowerShell para ejecutarlas. Como alternativa, puede utilizar el entorno integrado de secuencia de comandos de Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="a5247-p105">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="a5247-132">Este es un ejemplo de un conjunto de comandos completado:</span><span class="sxs-lookup"><span data-stu-id="a5247-132">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

### <a name="for-multiple-role-changes"></a><span data-ttu-id="a5247-133">Para varios cambios de rol</span><span class="sxs-lookup"><span data-stu-id="a5247-133">For multiple role changes</span></span>

<span data-ttu-id="a5247-134">Determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="a5247-134">Determine the following:</span></span>
  
- <span data-ttu-id="a5247-135">Qué cuentas de usuario que desea configurar.</span><span class="sxs-lookup"><span data-stu-id="a5247-135">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="a5247-p106">Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista de cuentas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="a5247-p106">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a5247-p107">Este comando muestra el nombre para mostrar de todas las cuentas de usuario, ordenadas por el nombre para mostrar, una pantalla a la vez. Puede filtrar la lista a un conjunto más pequeño mediante el cmdlet **donde** . Este es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a5247-p107">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="a5247-141">Este comando enumera sólo las cuentas de usuario para el que el nombre para mostrar comienza por "John".</span><span class="sxs-lookup"><span data-stu-id="a5247-141">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="a5247-142">Los roles que desea asignar a cada cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="a5247-142">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="a5247-143">Para mostrar la lista de roles disponibles que se pueden asignar a cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="a5247-143">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="a5247-p108">A continuación, cree un archivo de texto de valores separados por comas (CSV) que tiene el DisplayName y la función de nombres de los campos. Este es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="a5247-p108">Next, create a comma-separated value (CSV) text file that has the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="a5247-146">A continuación, rellene la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a5247-146">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that has the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="a5247-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="a5247-147">See also</span></span>

- [<span data-ttu-id="a5247-148">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a5247-148">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="a5247-149">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a5247-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="a5247-150">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="a5247-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
