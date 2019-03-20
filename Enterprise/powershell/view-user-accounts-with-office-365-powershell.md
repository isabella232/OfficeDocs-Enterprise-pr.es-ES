---
title: Ver cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Resumen: vea, enumere o muestre las cuentas de usuario de varias formas con Office 365 PowerShell.'
ms.openlocfilehash: 717a7c11f4e7f6d2e5e0c452854df7d4c419007e
ms.sourcegitcommit: 1dc7b4731cf9899c5ae867624ed142dbab0c517f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "30683707"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="e2ed1-103">Ver cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="e2ed1-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="e2ed1-104">**Resumen:** Vea sus cuentas de usuario de varias formas con Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="e2ed1-105">Aunque puede usar el centro de administración de Office 365 para ver las cuentas de su inquilino de Office 365, también puede usar PowerShell de Office 365 y realizar algunas tareas que el centro de administración de Office 365 no puede.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="e2ed1-106">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="e2ed1-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="e2ed1-107">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="e2ed1-108">Ver todas las cuentas</span><span class="sxs-lookup"><span data-stu-id="e2ed1-108">View all accounts</span></span>

<span data-ttu-id="e2ed1-109">Para mostrar la lista completa de cuentas de usuario, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="e2ed1-110">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-110">You should see information similar to this:</span></span>
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="e2ed1-111">Ver una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="e2ed1-111">View a specific account</span></span>

<span data-ttu-id="e2ed1-112">Para mostrar una cuenta de usuario específica, rellene el nombre de la cuenta de inicio de sesión de la cuenta de usuario, también conocido como nombre principal de usuario (UPN), quite los caracteres "<" y ">" y ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="e2ed1-113">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="e2ed1-114">Ver valores de propiedades adicionales para una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="e2ed1-114">View additional property values for a specific account</span></span>

<span data-ttu-id="e2ed1-115">De forma predeterminada, el cmdlet **Get-AzureADUser** solo muestra las propiedades objectId, DisplayName y UserPrincipalName de las cuentas.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="e2ed1-116">Para ser más selectivo acerca de la lista de propiedades que se mostrarán, puede usar el cmdlet **Select-Object** en combinación con el cmdlet **Get-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="e2ed1-116">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="e2ed1-117">Para combinar los dos cmdlets, usamos el carácter "canalización" "|", que indica a Azure Active Directory PowerShell para que Graph tome los resultados de un comando y lo envíe al siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-117">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="e2ed1-118">Este es un comando de ejemplo que muestra DisplayName, Department y UsageLocation para cada cuenta de usuario:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-118">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="e2ed1-119">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e2ed1-120">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e2ed1-121">Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="e2ed1-122">Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (\*) para mostrarlos todos para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-122">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="e2ed1-123">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-123">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e2ed1-124">Como otro ejemplo, puede comprobar el estado habilitado de una cuenta de usuario específica con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="e2ed1-125">Ver algunas cuentas basadas en una propiedad común</span><span class="sxs-lookup"><span data-stu-id="e2ed1-125">View some accounts based on a common property</span></span>

<span data-ttu-id="e2ed1-126">Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, puede usar el cmdlet **Where-Object** junto con el cmdlet **Get-AzureADUser**.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-126">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="e2ed1-127">Para combinar los dos cmdlets, usamos el carácter "canalización" "|", que indica a Azure Active Directory PowerShell para que Graph tome los resultados de un comando y lo envíe al siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-127">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="e2ed1-128">A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-128">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="e2ed1-129">Este comando le indica a Azure Active Directory PowerShell para que Graph:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="e2ed1-130">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e2ed1-131">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **Where-Object {\_$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-131">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="e2ed1-132">Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( \*\* $ \_. UsageLocation\*\* ) no está especificado ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-132">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="e2ed1-133">La propiedad **UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-133">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="e2ed1-134">Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (\*) para mostrarlos todos para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-134">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="e2ed1-135">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-135">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e2ed1-p106">Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="e2ed1-138">La sintaxis del cmdlet **Where-Object** que se muestra en estos ejemplos es **Where-Object {\_$.**</span><span class="sxs-lookup"><span data-stu-id="e2ed1-138">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="e2ed1-139">[nombre de propiedad de cuenta de usuario] [operador de comparación] Value **}**. > [Comparison Operator] is **-EQ** para igual a, **-ne** para no es igual a, **-lt** para menor que, **-gt** para mayor que, y otros.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-139">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="e2ed1-140">[VALUE] suele ser una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$null** para Unspecified> vea [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-140">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e2ed1-141">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e2ed1-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e2ed1-142">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="e2ed1-143">Ver todas las cuentas</span><span class="sxs-lookup"><span data-stu-id="e2ed1-143">View all accounts</span></span>

<span data-ttu-id="e2ed1-144">Para mostrar la lista completa de cuentas de usuario, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="e2ed1-145">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-145">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="e2ed1-146">El cmdlet **Get-MsolUser** también tiene un conjunto de parámetros para filtrar el conjunto de cuentas de usuario que se muestran.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-146">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="e2ed1-147">Por ejemplo, para la lista de usuarios sin licencia (usuarios que se han agregado a Office 365 pero que todavía no han sido autorizados para usar ninguno de los servicios), ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-147">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="e2ed1-148">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="e2ed1-149">Para obtener más información acerca de los parámetros adicionales para filtrar la visualización del conjunto de cuentas de usuario que se muestra, consulte [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="e2ed1-150">Ver una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="e2ed1-150">View a specific account</span></span>

<span data-ttu-id="e2ed1-151">Para mostrar una cuenta de usuario específica, escriba el nombre de inicio de sesión de la cuenta de usuario de la cuenta de usuario, también conocido como nombre principal de usuario (UPN), quite los caracteres "<" y ">" y ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="e2ed1-152">Ver algunas cuentas basadas en una propiedad común</span><span class="sxs-lookup"><span data-stu-id="e2ed1-152">View some accounts based on a common property</span></span>

<span data-ttu-id="e2ed1-153">Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, puede usar el cmdlet **Where-Object** junto con el cmdlet **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-153">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="e2ed1-154">Para combinar los dos cmdlets, usamos el carácter "canal" "|", que indica a Office 365 PowerShell que debe tomar los resultados de un comando y enviarlo al siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-154">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="e2ed1-155">A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-155">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="e2ed1-156">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e2ed1-157">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e2ed1-158">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **Where-Object {\_$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-158">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="e2ed1-159">Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( \*\* $ \_. UsageLocation\*\* ) no está especificado ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-159">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="e2ed1-160">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="e2ed1-161">La propiedad **UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-161">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="e2ed1-162">Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (\*) para mostrarlos todos para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-162">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="e2ed1-163">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-163">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e2ed1-p112">Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="e2ed1-166">La sintaxis del cmdlet **Where-Object** que se muestra en estos ejemplos es **Where-Object {\_$.**</span><span class="sxs-lookup"><span data-stu-id="e2ed1-166">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="e2ed1-167">[nombre de propiedad de cuenta de usuario] [operador de comparación] Value **}**.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-167">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="e2ed1-168">[Comparison Operator] es **-EQ** para igual a, **-ne** para no es igual a, **-lt** para menor que, **-gt** para mayor que, y otros.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-168">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="e2ed1-169">[VALUE] suele ser una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$null** para no especificado.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-169">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="e2ed1-170">Consulte [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-170">See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="e2ed1-171">Puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="e2ed1-172">Ver los valores de propiedad adicionales de las cuentas</span><span class="sxs-lookup"><span data-stu-id="e2ed1-172">View additional property values for accounts</span></span>

<span data-ttu-id="e2ed1-173">De forma predeterminada, el cmdlet **Get-MsolUser** muestra tres propiedades de las cuentas de usuario:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="e2ed1-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="e2ed1-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="e2ed1-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="e2ed1-175">DisplayName</span></span>
    
- <span data-ttu-id="e2ed1-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="e2ed1-176">isLicensed</span></span>
    
<span data-ttu-id="e2ed1-177">Si necesita más propiedades, como el Departamento en el que trabaja el usuario y el país o la región donde el usuario usa los servicios de Office 365, puede ejecutar <b0>Get-MsolUser</b0> en combinación con el cmdlet <b1>Select-Object</b1> para especificar la lista de cuentas de usuario. </a1>.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-177">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="e2ed1-178">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-178">Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="e2ed1-179">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e2ed1-180">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e2ed1-181">Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="e2ed1-182">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="e2ed1-183">El cmdlet **Select-Object** permite seleccionar y elegir las propiedades que desea que muestre un comando.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-183">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="e2ed1-184">Para ver todas las propiedades de las cuentas de usuario, use el carácter comodín (\*) para mostrarlas todas para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-184">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="e2ed1-185">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-185">Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="e2ed1-p116">Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, también puede usar el cmdlet **Where-Object**. A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="e2ed1-188">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="e2ed1-189">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="e2ed1-190">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **Where-Object {\_$. UsageLocation-EQ $Null}** ) y envía la información resultante al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-190">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="e2ed1-191">Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( \*\* $ \_. UsageLocation\*\* ) no está especificado ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-191">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="e2ed1-192">Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="e2ed1-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="e2ed1-193">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="e2ed1-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="e2ed1-194">Si usa la sincronización de directorios para crear y administrar los usuarios de Office 365, puede mostrar la cuenta local de la que se ha proyectado un usuario de Office 365.</span><span class="sxs-lookup"><span data-stu-id="e2ed1-194">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="e2ed1-195">El siguiente ejemplo presupone que Azure AD Connect se ha configurado para usar el delimitador de origen predeterminado de ObjectGUID (para obtener más información sobre la configuración de un delimitador de origen, consulte [Azure ad Connect: Design Concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) y se supone que el módulo de Active Directory para PowerShell tiene se ha instalado (consulte [herramientas de RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="e2ed1-195">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="e2ed1-196">Vea también</span><span class="sxs-lookup"><span data-stu-id="e2ed1-196">See also</span></span>

[<span data-ttu-id="e2ed1-197">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="e2ed1-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e2ed1-198">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="e2ed1-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e2ed1-199">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="e2ed1-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

