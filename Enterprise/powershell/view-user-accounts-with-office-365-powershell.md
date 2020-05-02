---
title: Ver cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/16/2019
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
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Resumen: vea, enumere o muestre las cuentas de usuario de varias formas con Office 365 PowerShell.'
ms.openlocfilehash: c97fd55b2516198f2beaddd558174c62972547c6
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004153"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="905a7-103">Ver cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="905a7-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="905a7-104">Aunque puede usar el centro de administración de Microsoft 365 para ver las cuentas de su inquilino de Office 365, también puede usar PowerShell de Office 365 y realizar algunas acciones que el centro de administración no puede.</span><span class="sxs-lookup"><span data-stu-id="905a7-104">Although you can use the Microsoft 365 admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="905a7-105">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="905a7-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="905a7-106">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="905a7-106">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="905a7-107">Ver todas las cuentas</span><span class="sxs-lookup"><span data-stu-id="905a7-107">View all accounts</span></span>

<span data-ttu-id="905a7-108">Para mostrar la lista completa de cuentas de usuario, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="905a7-108">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-AzureADUser
```

<span data-ttu-id="905a7-109">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="905a7-109">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="905a7-110">Ver una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="905a7-110">View a specific account</span></span>

<span data-ttu-id="905a7-111">Para mostrar una cuenta de usuario específica, rellene el nombre de la cuenta de inicio de sesión de la cuenta de usuario, también conocido como nombre principal de usuario (UPN), quite los caracteres "<" y ">" y ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="905a7-111">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="905a7-112">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="905a7-112">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="905a7-113">Ver valores de propiedades adicionales para una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="905a7-113">View additional property values for a specific account</span></span>

<span data-ttu-id="905a7-114">De forma predeterminada, el cmdlet **Get-AzureADUser** solo muestra las propiedades objectId, DisplayName y UserPrincipalName de las cuentas.</span><span class="sxs-lookup"><span data-stu-id="905a7-114">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="905a7-115">Para ser más selectivo acerca de la lista de propiedades que se mostrarán, puede usar el cmdlet **Select** junto con el cmdlet **Get-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="905a7-115">To be more selective about the list of properties to display, you can use the **Select** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="905a7-116">Para combinar los dos cmdlets, usamos el carácter "canalización" "|", que indica a Azure Active Directory PowerShell para que Graph tome los resultados de un comando y lo envíe al siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="905a7-116">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="905a7-117">Este es un comando de ejemplo que muestra DisplayName, Department y UsageLocation para cada cuenta de usuario:</span><span class="sxs-lookup"><span data-stu-id="905a7-117">Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```powershell
Get-AzureADUser | Select DisplayName,Department,UsageLocation
```

<span data-ttu-id="905a7-118">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="905a7-118">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="905a7-119">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-119">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="905a7-120">Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Seleccione DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-120">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="905a7-121">Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select** y el carácter comodín (\*) para mostrarlos todos para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="905a7-121">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="905a7-122">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="905a7-122">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="905a7-123">Como otro ejemplo, puede comprobar el estado habilitado de una cuenta de usuario específica con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="905a7-123">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="905a7-124">Ver algunas cuentas basadas en una propiedad común</span><span class="sxs-lookup"><span data-stu-id="905a7-124">View some accounts based on a common property</span></span>

<span data-ttu-id="905a7-125">Para ser más selectivo acerca de la lista de cuentas para mostrar, puede usar el cmdlet **Where** en combinación con el cmdlet **Get-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="905a7-125">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-AzureADUser** cmdlet.</span></span> <span data-ttu-id="905a7-126">Para combinar los dos cmdlets, usamos el carácter "canalización" "|", que indica a Azure Active Directory PowerShell para que Graph tome los resultados de un comando y lo envíe al siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="905a7-126">To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="905a7-127">A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="905a7-127">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="905a7-128">Este comando le indica a Azure Active Directory PowerShell para que Graph:</span><span class="sxs-lookup"><span data-stu-id="905a7-128">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="905a7-129">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-129">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="905a7-130">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **donde {\_$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-130">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="905a7-131">Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( \*\* $ \_. UsageLocation\*\* ) no está especificado ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-131">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="905a7-132">La propiedad **UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="905a7-132">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="905a7-133">Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select** y el carácter comodín (\*) para mostrarlos todos para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="905a7-133">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="905a7-134">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="905a7-134">Here is an example:</span></span>
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="905a7-p106">Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="905a7-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="905a7-137">La sintaxis del cmdlet **Where** que se muestra en estos ejemplos es **donde {\_$.**</span><span class="sxs-lookup"><span data-stu-id="905a7-137">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="905a7-138">[nombre de propiedad de cuenta de usuario] [operador de comparación] Value **}**. > [operador de comparación] is **-EQ** para igual a, **-ne** para no es igual a, **-lt** para menor que, **-gt** para mayor que, y otros.</span><span class="sxs-lookup"><span data-stu-id="905a7-138">[user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="905a7-139">[VALUE] suele ser una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$null** para> sin especificar vea [dónde](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="905a7-139">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="905a7-140">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="905a7-140">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="905a7-141">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="905a7-141">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="905a7-142">Ver todas las cuentas</span><span class="sxs-lookup"><span data-stu-id="905a7-142">View all accounts</span></span>

<span data-ttu-id="905a7-143">Para mostrar la lista completa de cuentas de usuario, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="905a7-143">To display the full list of user accounts, run this command:</span></span>
  
```powershell
Get-MsolUser
```

>[!Note]
><span data-ttu-id="905a7-144">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="905a7-144">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="905a7-145">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="905a7-145">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="905a7-146">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="905a7-146">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="905a7-147">El cmdlet **Get-MsolUser** también tiene un conjunto de parámetros para filtrar el conjunto de cuentas de usuario que se muestran.</span><span class="sxs-lookup"><span data-stu-id="905a7-147">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed.</span></span> <span data-ttu-id="905a7-148">Por ejemplo, para la lista de usuarios sin licencia (usuarios que se han agregado a Office 365 pero que todavía no han sido autorizados para usar ninguno de los servicios), ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="905a7-148">For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="905a7-149">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="905a7-149">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="905a7-150">Para obtener más información acerca de los parámetros adicionales para filtrar la visualización del conjunto de cuentas de usuario que se muestra, consulte [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="905a7-150">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  
### <a name="view-a-specific-account"></a><span data-ttu-id="905a7-151">Ver una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="905a7-151">View a specific account</span></span>

<span data-ttu-id="905a7-152">Para mostrar una cuenta de usuario específica, escriba el nombre de inicio de sesión de la cuenta de usuario de la cuenta de usuario, también conocido como nombre principal de usuario (UPN), quite los caracteres "<" y ">" y ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="905a7-152">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="905a7-153">Ver algunas cuentas basadas en una propiedad común</span><span class="sxs-lookup"><span data-stu-id="905a7-153">View some accounts based on a common property</span></span>

<span data-ttu-id="905a7-154">Para ser más selectivo acerca de la lista de cuentas para mostrar, puede usar el cmdlet **Where** en combinación con el cmdlet **Get-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="905a7-154">To be more selective about the list of accounts to display, you can use the **Where** cmdlet in combination with the **Get-MsolUser** cmdlet.</span></span> <span data-ttu-id="905a7-155">Para combinar los dos cmdlets, usamos el carácter "canal" "|", que indica a Office 365 PowerShell que debe tomar los resultados de un comando y enviarlo al siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="905a7-155">To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command.</span></span> <span data-ttu-id="905a7-156">A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="905a7-156">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="905a7-157">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="905a7-157">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="905a7-158">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-158">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="905a7-159">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **donde {\_$. UsageLocation-EQ $Null}** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-159">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ).</span></span> <span data-ttu-id="905a7-160">Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( \*\* $ \_. UsageLocation\*\* ) no está especificado ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-160">Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="905a7-161">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="905a7-161">You should see information similar to this:</span></span>
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="905a7-162">La propiedad **UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="905a7-162">The **UsageLocation** property is only one of many properties associated with a user account.</span></span> <span data-ttu-id="905a7-163">Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select** y el carácter comodín (\*) para mostrarlos todos para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="905a7-163">To see all of the properties for user accounts, use the **Select** cmdlet and the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="905a7-164">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="905a7-164">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="905a7-p113">Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="905a7-p113">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```powershell
Get-MsolUser | Where {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="905a7-167">La sintaxis del cmdlet **Where** que se muestra en estos ejemplos es **donde {\_$.**</span><span class="sxs-lookup"><span data-stu-id="905a7-167">The syntax for the **Where** cmdlet shown in these examples is **Where {$\_.**</span></span> <span data-ttu-id="905a7-168">[nombre de propiedad de cuenta de usuario] [operador de comparación] Value **}**.</span><span class="sxs-lookup"><span data-stu-id="905a7-168">[user account property name] [comparison operator] [value] **}**.</span></span>  <span data-ttu-id="905a7-169">[Comparison Operator] es **-EQ** para igual a, **-ne** para no es igual a, **-lt** para menor que, **-gt** para mayor que, y otros.</span><span class="sxs-lookup"><span data-stu-id="905a7-169">[comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.</span></span>  <span data-ttu-id="905a7-170">[VALUE] suele ser una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$null** para no especificado.</span><span class="sxs-lookup"><span data-stu-id="905a7-170">[value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified.</span></span> <span data-ttu-id="905a7-171">Vea [dónde](https://technet.microsoft.com/library/hh849715.aspx) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="905a7-171">See [Where](https://technet.microsoft.com/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="905a7-172">Puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="905a7-172">You can check the blocked status of a user account with the following command:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="905a7-173">Ver los valores de propiedad adicionales de las cuentas</span><span class="sxs-lookup"><span data-stu-id="905a7-173">View additional property values for accounts</span></span>

<span data-ttu-id="905a7-174">De forma predeterminada, el cmdlet **Get-MsolUser** muestra tres propiedades de las cuentas de usuario:</span><span class="sxs-lookup"><span data-stu-id="905a7-174">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="905a7-175">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="905a7-175">UserPrincipalName</span></span>
    
- <span data-ttu-id="905a7-176">DisplayName</span><span class="sxs-lookup"><span data-stu-id="905a7-176">DisplayName</span></span>
    
- <span data-ttu-id="905a7-177">isLicensed</span><span class="sxs-lookup"><span data-stu-id="905a7-177">isLicensed</span></span>
    
<span data-ttu-id="905a7-178">Si necesita propiedades adicionales, como el Departamento en el que trabaja el usuario y el país o la región donde el usuario usa los servicios de Office 365, puede ejecutar **Get-MsolUser** en combinación con el cmdlet **Select** para especificar la lista de propiedades de la cuenta de usuario.</span><span class="sxs-lookup"><span data-stu-id="905a7-178">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select** cmdlet to specify the list of user account properties.</span></span> <span data-ttu-id="905a7-179">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="905a7-179">Here is an example:</span></span>
  
```powershell
Get-MsolUser | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="905a7-180">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="905a7-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="905a7-181">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="905a7-182">Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Seleccione DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-182">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="905a7-183">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="905a7-183">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="905a7-184">El cmdlet **Select** permite seleccionar y elegir las propiedades que desea que muestre un comando.</span><span class="sxs-lookup"><span data-stu-id="905a7-184">The **Select** cmdlet lets you pick and choose the properties you want a command to display.</span></span> <span data-ttu-id="905a7-185">Para ver todas las propiedades de las cuentas de usuario, use el carácter comodín (\*) para mostrarlas todas para una cuenta de usuario específica.</span><span class="sxs-lookup"><span data-stu-id="905a7-185">To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account.</span></span> <span data-ttu-id="905a7-186">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="905a7-186">Here is an example:</span></span>
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select *
```

<span data-ttu-id="905a7-187">Para ser más selectivo acerca de la lista de cuentas para mostrar, también puede usar el cmdlet **Where** .</span><span class="sxs-lookup"><span data-stu-id="905a7-187">To be more selective about the list of accounts to display, you can also use the **Where** cmdlet.</span></span> <span data-ttu-id="905a7-188">A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="905a7-188">Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```powershell
Get-MsolUser | Where {$_.UsageLocation -eq $Null} | Select DisplayName, Department, UsageLocation
```

<span data-ttu-id="905a7-189">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="905a7-189">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="905a7-190">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-190">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="905a7-191">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **donde {\_$. UsageLocation-EQ $Null}** ) y envía la información resultante al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-191">Find all of the user accounts that have an unspecified usage location ( **Where {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ).</span></span> <span data-ttu-id="905a7-192">Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( \*\* $ \_. UsageLocation\*\* ) no está especificado ( **-EQ $null** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-192">Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="905a7-193">Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Seleccione DisplayName, Department, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="905a7-193">Display only the user account name, department, and usage location ( **Select DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="905a7-194">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="905a7-194">You should see information similar to this:</span></span>
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="905a7-195">Si usa la sincronización de directorios para crear y administrar los usuarios de Office 365, puede mostrar la cuenta local de la que se ha proyectado un usuario de Office 365.</span><span class="sxs-lookup"><span data-stu-id="905a7-195">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from.</span></span> <span data-ttu-id="905a7-196">El siguiente ejemplo presupone que Azure AD Connect se ha configurado para usar el delimitador de origen predeterminado de ObjectGUID (para obtener más información sobre la configuración de un delimitador de origen, consulte [Azure ad Connect: Design Concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) y se supone que se ha instalado el módulo de servicios de dominio de Active Directory para PowerShell (consulte [las herramientas de RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="905a7-196">The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory Domain Services module for PowerShell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

## <a name="see-also"></a><span data-ttu-id="905a7-197">Consulte también</span><span class="sxs-lookup"><span data-stu-id="905a7-197">See also</span></span>

[<span data-ttu-id="905a7-198">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="905a7-198">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="905a7-199">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="905a7-199">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="905a7-200">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="905a7-200">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

