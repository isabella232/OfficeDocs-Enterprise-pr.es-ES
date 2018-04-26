---
title: Asignar roles a cuentas de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
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
description: 'Resumen: Utilice Office 365 PowerShell y el cmdlet Add-MsolRoleMember para asignar roles a cuentas de usuario.'
ms.openlocfilehash: 2af4409020cc4a4e3dd6ff3b8bfcf5f1138f26cd
ms.sourcegitcommit: 3b474e0b9f0c12bb02f8439fb42b80c2f4798ce1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/26/2018
---
# <a name="assign-roles-to-user-accounts-with-office-365-powershell"></a><span data-ttu-id="26b7b-103">Asignar roles a cuentas de usuario con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="26b7b-103">Assign roles to user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="26b7b-104">**Resumen:** Utilice Office 365 PowerShell y el cmdlet **Add-MsolRoleMember** para asignar roles a cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="26b7b-104">**Summary:** Use Office 365 PowerShell and the **Add-MsolRoleMember** cmdlet to assign roles to user accounts.</span></span>
  
<span data-ttu-id="26b7b-105">Puede asignar la funciones de forma rápida y sencilla a cuentas de usuario mediante Office 365 PowerShell identificando el nombre para mostrar de la cuenta de usuario y el nombre del rol.</span><span class="sxs-lookup"><span data-stu-id="26b7b-105">You can quickly and easily assign roles to user accounts using Office 365 PowerShell by identifying the user account's display name and the role name.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="26b7b-106">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="26b7b-106">Before you begin</span></span>

<span data-ttu-id="26b7b-p101">Los procedimientos de este tema requieren conectarse a Office 365 PowerShell utilizando una cuenta de administrador global. Para obtener instrucciones, vea [conectarse a Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="26b7b-p101">The procedures in this topic require you to connect to Office 365 PowerShell using a global administrator account. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="for-a-single-role-change"></a><span data-ttu-id="26b7b-109">Para un cambio de función única</span><span class="sxs-lookup"><span data-stu-id="26b7b-109">For a single role change</span></span>

<span data-ttu-id="26b7b-110">Determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="26b7b-110">Determine the following:</span></span>
  
- <span data-ttu-id="26b7b-111">La cuenta de usuario que desea configurar.</span><span class="sxs-lookup"><span data-stu-id="26b7b-111">The user account that you want to configure.</span></span>
    
    <span data-ttu-id="26b7b-p102">Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista completa de cuentas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="26b7b-p102">To specify the user account, you must determine its Display Name. To get a complete list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="26b7b-p103">Este comando muestra el nombre para mostrar de las cuentas de usuario, ordenadas por el nombre para mostrar, una pantalla a la vez. Mediante el cmdlet **donde** puede filtrar la lista a un conjunto más pequeño. Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="26b7b-p103">This command lists the Display Name of your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="26b7b-117">Este comando muestra sólo las cuentas de usuario para el que el nombre para mostrar empieza con "Juan".</span><span class="sxs-lookup"><span data-stu-id="26b7b-117">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="26b7b-118">La función que desea asignar.</span><span class="sxs-lookup"><span data-stu-id="26b7b-118">The role you want to assign.</span></span>
    
    <span data-ttu-id="26b7b-119">Para mostrar la lista de roles disponibles que se pueden asignar a cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="26b7b-119">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="26b7b-120">Una vez que haya determinado el nombre para mostrar de la cuenta y el nombre de la función, utilice estos comandos para asignar el rol a la cuenta:</span><span class="sxs-lookup"><span data-stu-id="26b7b-120">Once you have determined the Display Name of the account and the Name of the role, use these commands to assign the role to the account:</span></span>
  
```
$dispName="<The Display Name of the account>"
$roleName="<The role name you want to assign to the account>"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

<span data-ttu-id="26b7b-p104">Los comandos de copiar y pegarlos en el Bloc de notas. Para las variables **$dispName** y **$roleName** , reemplace el texto de la descripción con sus valores, quite el \< y > caracteres y dejar las comillas. Copie las líneas modificadas y pegarlos en la ventana de Windows Azure Active Directory módulo para Windows PowerShell para ejecutarlas. Como alternativa, puede utilizar el entorno integrado de secuencias de comandos de Windows PowerShell (ISE).</span><span class="sxs-lookup"><span data-stu-id="26b7b-p104">Copy the commands and paste them into Notepad. For the **$dispName** and **$roleName** variables, replace the description text with their values, remove the \< and > characters, and leave the quotes. Copy the modified lines and paste them into your Windows Azure Active Directory Module for Windows PowerShell window to run them. Alternately, you can use the Windows PowerShell Integrated Script Environment (ISE).</span></span>
  
<span data-ttu-id="26b7b-125">Aquí es un ejemplo de un conjunto de comandos completa:</span><span class="sxs-lookup"><span data-stu-id="26b7b-125">Here is an example of a completed command set:</span></span>
  
```
$dispName="Scott Wallace"
$roleName="SharePoint Service Administrator"
Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $dispName).UserPrincipalName -RoleName $roleName
```

## <a name="for-multiple-role-changes"></a><span data-ttu-id="26b7b-126">Varios cambios de función</span><span class="sxs-lookup"><span data-stu-id="26b7b-126">For multiple role changes</span></span>

<span data-ttu-id="26b7b-127">Determine lo siguiente:</span><span class="sxs-lookup"><span data-stu-id="26b7b-127">Determine the following:</span></span>
  
- <span data-ttu-id="26b7b-128">Qué cuentas de usuario que desea configurar.</span><span class="sxs-lookup"><span data-stu-id="26b7b-128">Which user accounts that you want to configure.</span></span>
    
    <span data-ttu-id="26b7b-p105">Para especificar la cuenta de usuario, debe determinar su nombre para mostrar. Para obtener una lista de cuentas, use este comando:</span><span class="sxs-lookup"><span data-stu-id="26b7b-p105">To specify the user account, you must determine its Display Name. To get a list accounts, use this command:</span></span>
    
  ```
  Get-MsolUser -All | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="26b7b-p106">Este comando muestra el nombre para mostrar de todas las cuentas de usuario, ordenadas por el nombre para mostrar, una pantalla a la vez. Mediante el cmdlet **donde** puede filtrar la lista a un conjunto más pequeño. Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="26b7b-p106">This command lists the Display Name of all your user accounts, sorted by the Display Name, one screen at a time. You can filter the list to a smaller set by using the **Where** cmdlet. Here is an example:</span></span>
    
  ```
  Get-MsolUser | Where DisplayName -like "John*" | Sort DisplayName | Select DisplayName | More
  ```

    <span data-ttu-id="26b7b-134">Este comando muestra sólo las cuentas de usuario para el que el nombre para mostrar empieza con "Juan".</span><span class="sxs-lookup"><span data-stu-id="26b7b-134">This command lists only the user accounts for which the Display Name starts with "John".</span></span>
    
- <span data-ttu-id="26b7b-135">Los roles que desea asignar a cada cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="26b7b-135">Which roles you want to assign to each user account.</span></span>
    
    <span data-ttu-id="26b7b-136">Para mostrar la lista de roles disponibles que se pueden asignar a cuentas de usuario, use este comando:</span><span class="sxs-lookup"><span data-stu-id="26b7b-136">To display the list of available roles that you can assign to user accounts, use this command:</span></span>
    
  ```
  Get-MsolRole | Sort Name | Select Name,Description
  ```

<span data-ttu-id="26b7b-p107">A continuación, cree un archivo de texto de valores separados por comas (CSV) que contiene el DisplayName y la función de nombres de los campos. Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="26b7b-p107">Next, create a comma-separated value (CSV) text file that contains the DisplayName and role Name fields. Here is an example:</span></span>
  
```
DisplayName,RoleName
"Belinda Newman","Billing Administrator"
"John Doe","SharePoint Service Administrator"
"Alice Smithers","Lync Service Administrator"
```

<span data-ttu-id="26b7b-139">A continuación, especifique la ubicación del archivo CSV y ejecute los comandos resultantes en el símbolo del sistema de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26b7b-139">Next, fill in the location of the CSV file and run the resulting commands at the PowerShell command prompt.</span></span>
  
```
$fileName="<path and file name of the input CSV file that contains the role changes, example: C:\admin\RoleUpdates.CSV>"
$roleChanges=Import-Csv $fileName | ForEach {Add-MsolRoleMember -RoleMemberEmailAddress (Get-MsolUser | Where DisplayName -eq $_.DisplayName).UserPrincipalName -RoleName $_.RoleName }

```

## <a name="see-also"></a><span data-ttu-id="26b7b-140">Consulte también</span><span class="sxs-lookup"><span data-stu-id="26b7b-140">See also</span></span>

- [<span data-ttu-id="26b7b-141">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="26b7b-141">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
- [<span data-ttu-id="26b7b-142">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="26b7b-142">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
- [<span data-ttu-id="26b7b-143">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="26b7b-143">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
- [<span data-ttu-id="26b7b-144">MsolRoleMember agregar</span><span class="sxs-lookup"><span data-stu-id="26b7b-144">Add-MsolRoleMember</span></span>](https://msdn.microsoft.com/library/dn194120.aspx)
