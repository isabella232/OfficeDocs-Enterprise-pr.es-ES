---
title: Ver cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
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
ms.openlocfilehash: 0711bf945b863cb89d45a377f61a139b298ca6d7
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748408"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="41fe4-103">Ver cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="41fe4-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="41fe4-104">Aunque puede usar el centro de administración de Microsoft 365 para ver las cuentas de su inquilino de Office 365, también puede usar PowerShell de Office 365 y realizar algunas acciones que el centro de administración no puede.</span><span class="sxs-lookup"><span data-stu-id="41fe4-104">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="41fe4-105">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="41fe4-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="41fe4-106">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="41fe4-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="41fe4-107">Ver todas las cuentas</span><span class="sxs-lookup"><span data-stu-id="41fe4-107">View all accounts</span></span>

<span data-ttu-id="41fe4-108">Para mostrar la lista completa de cuentas de usuario, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="41fe4-108">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="41fe4-109">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="41fe4-109">You should see information similar to this:</span></span>
  
```powershell
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a><span data-ttu-id="41fe4-110">Ver una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="41fe4-110">View a specific account</span></span>

<span data-ttu-id="41fe4-111">Para mostrar una cuenta de usuario específica, rellene el nombre de la cuenta de inicio de sesión de la cuenta de usuario, también conocido como nombre principal de usuario (UPN), quite los caracteres "<" y ">" y ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="41fe4-111">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="41fe4-112">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="41fe4-112">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="41fe4-113">Ver valores de propiedades adicionales para una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="41fe4-113">View additional property values for a specific account</span></span>

<span data-ttu-id="41fe4-114">De forma predeterminada, el cmdlet **Get-AzureADUser** solo muestra las propiedades objectId, DisplayName y UserPrincipalName de las cuentas.</span><span class="sxs-lookup"><span data-stu-id="41fe4-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="41fe4-115">Para ser más selectivo acerca de la lista de propiedades que se mostrarán, puede usar el cmdlet **Select-Object** en combinación con el cmdlet **Get-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="41fe4-115">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="41fe4-116">Para combinar los dos cmdlets, usamos el carácter "canalización" "|", que indica a Azure Active Directory PowerShell para que Graph tome los resultados de un comando y lo envíe al siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="41fe4-116">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="41fe4-117">Este es un comando de ejemplo que muestra DisplayName, Department y UsageLocation para cada cuenta de usuario:</span><span class="sxs-lookup"><span data-stu-id="41fe4-117">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="41fe4-118">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="41fe4-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41fe4-119">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41fe4-120">Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-120">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="41fe4-121">Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (\*) para mostrarlos todos para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="41fe4-121">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="41fe4-122">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="41fe4-122">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="41fe4-123">Como otro ejemplo, puede comprobar el estado habilitado de una cuenta de usuario específica con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="41fe4-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="41fe4-124">Ver algunas cuentas basadas en una propiedad común</span><span class="sxs-lookup"><span data-stu-id="41fe4-124">View some accounts based on a common property</span></span>

<span data-ttu-id="41fe4-125">Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, puede usar el cmdlet **Where-Object** junto con el cmdlet **Get-AzureADUser**.</span><span class="sxs-lookup"><span data-stu-id="41fe4-125">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="41fe4-126">Para combinar los dos cmdlets, usamos el carácter "canalización" "|", que indica a Azure Active Directory PowerShell para que Graph tome los resultados de un comando y lo envíe al siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="41fe4-126">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="41fe4-127">A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="41fe4-127">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="41fe4-128">Este comando le indica a Azure Active Directory PowerShell para que Graph:</span><span class="sxs-lookup"><span data-stu-id="41fe4-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="41fe4-129">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41fe4-130">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **Where-Object {\_$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-130">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="41fe4-131">Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( \*\* $ \_. UsageLocation\*\* ) no está especificado ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-131">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="41fe4-132">La propiedad **UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="41fe4-132">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="41fe4-133">Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (\*) para mostrarlos todos para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="41fe4-133">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="41fe4-134">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="41fe4-134">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="41fe4-p106">Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="41fe4-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="41fe4-137">La sintaxis del cmdlet **Where-Object** que se muestra en estos ejemplos es **Where-Object {\_$.**</span><span class="sxs-lookup"><span data-stu-id="41fe4-137">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="41fe4-138">[nombre de propiedad de cuenta de usuario] [operador de comparación] Value **}**. > [operador de comparación] is **-EQ** para igual a, **-ne** para no es igual a, **-lt** para menor que, **-gt** para mayor que, y otros.</span><span class="sxs-lookup"><span data-stu-id="41fe4-138">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="41fe4-139">[VALUE] suele ser una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$null** para> sin especificar consulte [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="41fe4-139">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="41fe4-140">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="41fe4-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="41fe4-141">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="41fe4-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="41fe4-142">Ver todas las cuentas</span><span class="sxs-lookup"><span data-stu-id="41fe4-142">View all accounts</span></span>

<span data-ttu-id="41fe4-143">Para mostrar la lista completa de cuentas de usuario, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="41fe4-143">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

<span data-ttu-id="41fe4-144">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="41fe4-144">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="41fe4-145">El cmdlet **Get-MsolUser** también tiene un conjunto de parámetros para filtrar el conjunto de cuentas de usuario que se muestran.</span><span class="sxs-lookup"><span data-stu-id="41fe4-145">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="41fe4-146">Por ejemplo, para la lista de usuarios sin licencia (usuarios que se han agregado a Office 365 pero que todavía no han sido autorizados para usar ninguno de los servicios), ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="41fe4-146">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="41fe4-147">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="41fe4-147">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="41fe4-148">Para obtener más información acerca de los parámetros adicionales para filtrar la visualización del conjunto de cuentas de usuario que se muestra, consulte [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="41fe4-148">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="41fe4-149">Ver una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="41fe4-149">View a specific account</span></span>

<span data-ttu-id="41fe4-150">Para mostrar una cuenta de usuario específica, escriba el nombre de inicio de sesión de la cuenta de usuario de la cuenta de usuario, también conocido como nombre principal de usuario (UPN), quite los caracteres "<" y ">" y ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="41fe4-150">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="41fe4-151">Ver algunas cuentas basadas en una propiedad común</span><span class="sxs-lookup"><span data-stu-id="41fe4-151">View some accounts based on a common property</span></span>

<span data-ttu-id="41fe4-152">Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, puede usar el cmdlet **Where-Object** junto con el cmdlet **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="41fe4-152">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="41fe4-153">Para combinar los dos cmdlets, usamos el carácter "canal" "|", que indica a Office 365 PowerShell que debe tomar los resultados de un comando y enviarlo al siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="41fe4-153">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="41fe4-154">A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="41fe4-154">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="41fe4-155">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="41fe4-155">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41fe4-156">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-156">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41fe4-157">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **Where-Object {\_$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-157">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="41fe4-158">Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( \*\* $ \_. UsageLocation\*\* ) no está especificado ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-158">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="41fe4-159">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="41fe4-159">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="41fe4-160">La propiedad **UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="41fe4-160">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="41fe4-161">Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (\*) para mostrarlos todos para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="41fe4-161">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="41fe4-162">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="41fe4-162">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="41fe4-p112">Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="41fe4-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="41fe4-165">La sintaxis del cmdlet **Where-Object** que se muestra en estos ejemplos es **Where-Object {\_$.**</span><span class="sxs-lookup"><span data-stu-id="41fe4-165">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.**</span></span> <span data-ttu-id="41fe4-166">[nombre de propiedad de cuenta de usuario] [operador de comparación] Value **}**.</span><span class="sxs-lookup"><span data-stu-id="41fe4-166">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="41fe4-167">[Comparison Operator] es **-EQ** para igual a, **-ne** para no es igual a, **-lt** para menor que, **-gt** para mayor que, y otros.</span><span class="sxs-lookup"><span data-stu-id="41fe4-167">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="41fe4-168">[VALUE] suele ser una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$null** para no especificado.</span><span class="sxs-lookup"><span data-stu-id="41fe4-168">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="41fe4-169">Consulte [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="41fe4-169">See [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="41fe4-170">Puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="41fe4-170">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="41fe4-171">Ver los valores de propiedad adicionales de las cuentas</span><span class="sxs-lookup"><span data-stu-id="41fe4-171">View additional property values for accounts</span></span>

<span data-ttu-id="41fe4-172">De forma predeterminada, el cmdlet **Get-MsolUser** muestra tres propiedades de las cuentas de usuario:</span><span class="sxs-lookup"><span data-stu-id="41fe4-172">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="41fe4-173">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="41fe4-173">UserPrincipalName</span></span>
    
- <span data-ttu-id="41fe4-174">DisplayName</span><span class="sxs-lookup"><span data-stu-id="41fe4-174">DisplayName</span></span>
    
- <span data-ttu-id="41fe4-175">isLicensed</span><span class="sxs-lookup"><span data-stu-id="41fe4-175">isLicensed</span></span>
    
<span data-ttu-id="41fe4-176">Si necesita propiedades adicionales, como el Departamento en el que trabaja el usuario y el país o la región donde el usuario usa los servicios de Office 365, puede ejecutar **Get-MsolUser** en combinación con el cmdlet **Select-Object** para especificar la lista de propiedades de la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="41fe4-176">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="41fe4-177">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="41fe4-177">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="41fe4-178">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="41fe4-178">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41fe4-179">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-179">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41fe4-180">Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-180">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="41fe4-181">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="41fe4-181">You should see information similar to this:</span></span>
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="41fe4-182">El cmdlet **Select-Object** permite seleccionar y elegir las propiedades que desea que muestre un comando.</span><span class="sxs-lookup"><span data-stu-id="41fe4-182">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="41fe4-183">Para ver todas las propiedades de las cuentas de usuario, use el carácter comodín (\*) para mostrarlas todas para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="41fe4-183">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="41fe4-184">A continuación se muestra un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="41fe4-184">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="41fe4-p116">Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, también puede usar el cmdlet **Where-Object**. A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="41fe4-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="41fe4-187">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="41fe4-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="41fe4-188">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-188">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="41fe4-189">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **Where-Object {\_$. UsageLocation-EQ $Null}** ) y envía la información resultante al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-189">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="41fe4-190">Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( \*\* $ \_. UsageLocation\*\* ) no está especificado ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-190">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="41fe4-191">Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Select-Object DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="41fe4-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="41fe4-192">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="41fe4-192">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="41fe4-193">Si usa la sincronización de directorios para crear y administrar los usuarios de Office 365, puede mostrar la cuenta local de la que se ha proyectado un usuario de Office 365.</span><span class="sxs-lookup"><span data-stu-id="41fe4-193">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="41fe4-194">A continuación se supone que Azure AD Connect se ha configurado para usar el delimitador de origen predeterminado de ObjectGUID (para obtener más información sobre la configuración de un delimitador de origen, consulte [Azure ad Connect: Design Concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) y se supone que se ha instalado el módulo de Active Directory para PowerShell (consulte [las herramientas de RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="41fe4-194">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a><span data-ttu-id="41fe4-195">Vea también</span><span class="sxs-lookup"><span data-stu-id="41fe4-195">See also</span></span>

[<span data-ttu-id="41fe4-196">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="41fe4-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="41fe4-197">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="41fe4-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="41fe4-198">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="41fe4-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

