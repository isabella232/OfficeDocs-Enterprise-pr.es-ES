---
title: Ver cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
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
description: 'Resumen: Ver, lista o mostrar las cuentas de usuario de varias formas con PowerShell de Office 365.'
ms.openlocfilehash: e95353602b96babe5c80f7d57462370636dd26fa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730325"
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="8b2bd-103">Ver cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="8b2bd-103">View user accounts with Office 365 PowerShell</span></span>

<span data-ttu-id="8b2bd-104">**Resumen:** Ver las cuentas de usuario de varias formas con PowerShell de Office 365.</span><span class="sxs-lookup"><span data-stu-id="8b2bd-104">**Summary:** View your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="8b2bd-105">Aunque puede usar el centro de administración de Office 365 para ver las cuentas para el inquilino de Office 365, también puede usar PowerShell de Office 365 y hacer cosas que no se puede el centro de administración de Office 365.</span><span class="sxs-lookup"><span data-stu-id="8b2bd-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="8b2bd-106">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="8b2bd-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="8b2bd-107">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
  
### <a name="view-all-accounts"></a><span data-ttu-id="8b2bd-108">Ver todas las cuentas</span><span class="sxs-lookup"><span data-stu-id="8b2bd-108">View all accounts</span></span>

<span data-ttu-id="8b2bd-109">Para mostrar la lista completa de las cuentas de usuario, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-109">To display the full list of user accounts, run this command:</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="8b2bd-110">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-110">You should see information similar to this:</span></span>
  
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

### <a name="view-a-specific-account"></a><span data-ttu-id="8b2bd-111">Ver una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="8b2bd-111">View a specific account</span></span>

<span data-ttu-id="8b2bd-112">Para mostrar una cuenta de usuario específica, quitar relleno en el nombre de inicio de sesión de la cuenta de la cuenta de usuario, también conocido como el nombre principal de usuario (UPN), el "<" y ">" caracteres y ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-112">To display a specific user account, fill in the sign-in account name of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

<span data-ttu-id="8b2bd-113">Aquí le mostramos un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-113">Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a><span data-ttu-id="8b2bd-114">Ver los valores de propiedad adicionales de una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="8b2bd-114">View additional property values for a specific account</span></span>

<span data-ttu-id="8b2bd-115">De forma predeterminada, el cmdlet **Get-AzureADUser** solo muestra las propiedades ObjectID, DisplayName y UserPrincipalName de cuentas.</span><span class="sxs-lookup"><span data-stu-id="8b2bd-115">By default, the **Get-AzureADUser** cmdlet only displays the ObjectID, DisplayName, and UserPrincipalName properties of accounts.</span></span>

<span data-ttu-id="8b2bd-p101">Para que sea más selectivos acerca de la lista de propiedades para mostrar, puede usar el cmdlet **Select-Object** en combinación con el cmdlet **Get-AzureADUser** . Para combinar los dos cmdlets, usamos el carácter "barra vertical" "|", que indica a Azure Active Directory PowerShell para gráfico para tomar los resultados de un comando y volver a enviar con el siguiente comando. Este es un comando de ejemplo que muestra el DisplayName, el departamento y la propiedad UsageLocation para cada cuenta de usuario:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p101">To be more selective about the list of properties to display, you can use the **Select-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays the DisplayName, Department, and UsageLocation for every user account:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="8b2bd-119">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8b2bd-120">Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-120">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8b2bd-121">Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, el departamento, la propiedad UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-121">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
  
<span data-ttu-id="8b2bd-p102">Para ver todas las propiedades para las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (\*) para mostrar todos ellos para una cuenta de usuario específica. Este es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p102">To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="8b2bd-124">Como otro ejemplo, puede comprobar el estado habilitado de una cuenta de usuario específica con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-124">As another example, you can check the enabled status of a specific user account with the following command:</span></span>
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="8b2bd-125">Ver algunas cuentas en función de una propiedad común</span><span class="sxs-lookup"><span data-stu-id="8b2bd-125">View some accounts based on a common property</span></span>

<span data-ttu-id="8b2bd-p103">Para que sea más selectivos acerca de la lista de cuentas para mostrar, puede usar el cmdlet **Where-Object** en combinación con el cmdlet **Get-AzureADUser** . Para combinar los dos cmdlets, usamos el carácter "barra vertical" "|", que indica a Azure Active Directory PowerShell para gráfico para tomar los resultados de un comando y volver a enviar con el siguiente comando. Este es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Azure Active Directory PowerShell for Graph to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="8b2bd-129">Este comando indica a Azure Active Directory PowerShell para gráfico para:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-129">This command instructs Azure Active Directory PowerShell for Graph to:</span></span>
  
- <span data-ttu-id="8b2bd-130">Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8b2bd-p104">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. Propiedad UsageLocation - eq $Null}** ). Entre las llaves, el comando indica a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que la propiedad UsageLocation cuenta de usuario (propiedad) ( \*\* $ \_. Propiedad UsageLocation\*\* ) no está especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="8b2bd-p105">La propiedad de la **propiedad UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario. Para ver todas las propiedades para las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (\*) para mostrar todos ellos para una cuenta de usuario específica. Este es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="8b2bd-p106">Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="8b2bd-p107">La sintaxis para el cmdlet **Where-Object** , que se muestra en estos ejemplos es **Where-Object {$\_.** [nombre de propiedad de la cuenta de usuario] [operador de comparación] [valor] **}**. > [operador de comparación] es **-eq** para es igual a, **-ne** para no es igual a, **-lt** para menor que **-gt** para mayor y otros usuarios.  [valor] es normalmente una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$Null** para que no se especifica > vea [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) for more information.</span></span>
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="8b2bd-141">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b2bd-141">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="8b2bd-142">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-142">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

### <a name="view-all-accounts"></a><span data-ttu-id="8b2bd-143">Ver todas las cuentas</span><span class="sxs-lookup"><span data-stu-id="8b2bd-143">View all accounts</span></span>

<span data-ttu-id="8b2bd-144">Para mostrar la lista completa de las cuentas de usuario, ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-144">To display the full list of user accounts, run this command:</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="8b2bd-145">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-145">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="8b2bd-p108">El cmdlet **Get-MsolUser** también tiene un conjunto de parámetros para filtrar el conjunto de cuentas de usuario que se muestra. Por ejemplo, para la lista de los usuarios sin licencia (los usuarios que se han añadido a Office 365, pero aún no han se ha licencia para usar cualquiera de los servicios), ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p108">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="8b2bd-148">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-148">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="8b2bd-149">Para obtener más información acerca de los parámetros adicionales para filtrar la visualización del conjunto de cuentas de usuario que se muestra, vea [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-149">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).</span></span>
  

### <a name="view-a-specific-account"></a><span data-ttu-id="8b2bd-150">Ver una cuenta específica</span><span class="sxs-lookup"><span data-stu-id="8b2bd-150">View a specific account</span></span>

<span data-ttu-id="8b2bd-151">Para mostrar una cuenta de usuario específica, quitar relleno en el nombre de inicio de sesión de la cuenta de usuario de la cuenta de usuario, también conocido como el nombre principal de usuario (UPN), el "<" y ">" caracteres y ejecute este comando:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-151">To display a specific user account, fill in the sign-in name of the user account of the user account, also known as the user principal name (UPN), remove the "<" and ">" characters, and run this command:</span></span>
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a><span data-ttu-id="8b2bd-152">Ver algunas cuentas en función de una propiedad común</span><span class="sxs-lookup"><span data-stu-id="8b2bd-152">View some accounts based on a common property</span></span>

<span data-ttu-id="8b2bd-p109">Para que sea más selectivos acerca de la lista de cuentas para mostrar, puede usar el cmdlet **Where-Object** en combinación con el cmdlet **Get-MsolUser** . Para combinar los dos cmdlets, usamos el carácter "barra vertical" "|", que indica a Office 365 PowerShell tomar los resultados de un comando y enviar con el siguiente comando. Este es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p109">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="8b2bd-156">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-156">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8b2bd-157">Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-157">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8b2bd-p110">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. Propiedad UsageLocation - eq $Null}** ). Entre las llaves, el comando indica a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que la propiedad UsageLocation cuenta de usuario (propiedad) ( \*\* $ \_. Propiedad UsageLocation\*\* ) no está especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p110">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="8b2bd-160">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-160">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="8b2bd-p111">La propiedad de la **propiedad UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario. Para ver todas las propiedades para las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (\*) para mostrar todos ellos para una cuenta de usuario específica. Este es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p111">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="8b2bd-p112">Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p112">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="8b2bd-p113">La sintaxis para el cmdlet **Where-Object** , que se muestra en estos ejemplos es **Where-Object {$\_.** [nombre de propiedad de la cuenta de usuario] [operador de comparación] [valor] **}**.  [operador de comparación] es **-eq** para es igual a, **-ne** para no es igual a, **-lt** para menor que **-gt** para mayor y otros usuarios.  [valor] es normalmente una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$Null** para que no se especifica. Para obtener más información, consulte [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p113">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others.  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified. See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="8b2bd-171">Puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-171">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a><span data-ttu-id="8b2bd-172">Ver los valores de propiedades adicionales para las cuentas</span><span class="sxs-lookup"><span data-stu-id="8b2bd-172">View additional property values for accounts</span></span>

<span data-ttu-id="8b2bd-173">El cmdlet **Get-MsolUser** de forma predeterminada muestra las tres propiedades de cuentas de usuario:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-173">The **Get-MsolUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="8b2bd-174">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="8b2bd-174">UserPrincipalName</span></span>
    
- <span data-ttu-id="8b2bd-175">DisplayName</span><span class="sxs-lookup"><span data-stu-id="8b2bd-175">DisplayName</span></span>
    
- <span data-ttu-id="8b2bd-176">isLicensed</span><span class="sxs-lookup"><span data-stu-id="8b2bd-176">isLicensed</span></span>
    
<span data-ttu-id="8b2bd-p114">Si necesita propiedades adicionales, como el departamento para que el usuario trabaja y el país o región donde el usuario usa servicios de Office 365, puede ejecutar **Get-MsolUser** en combinación con el cmdlet **Select-Object** para especificar la lista de cuenta de usuario Propiedades. Este es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p114">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="8b2bd-179">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8b2bd-180">Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8b2bd-181">Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, el departamento, la propiedad UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-181">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="8b2bd-182">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-182">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

<span data-ttu-id="8b2bd-p115">El cmdlet **Select-Object** le permite elegir y seleccionar las propiedades que desee un comando que se va a mostrar. Para ver todas las propiedades para las cuentas de usuario, use el carácter comodín (\*) para mostrar todos ellos para una cuenta de usuario específica. Este es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p115">The **Select-Object** cmdlet lets you pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (\*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

<span data-ttu-id="8b2bd-p116">Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, también puede usar el cmdlet **Where-Object**. A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p116">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="8b2bd-188">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-188">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="8b2bd-189">Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-189">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="8b2bd-p117">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. Propiedad UsageLocation - eq $Null}** ) y enviar la información resultante con el siguiente comando ( **|** ). Entre las llaves, el comando es indicar a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que la propiedad UsageLocation cuenta de usuario (propiedad) ( \*\* $ \_. Propiedad UsageLocation\*\* ) no está especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p117">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="8b2bd-192">Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, el departamento, la propiedad UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="8b2bd-192">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="8b2bd-193">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="8b2bd-193">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

<span data-ttu-id="8b2bd-p118">Si se usa la sincronización de Active directory para crear y administrar los usuarios de Office 365, puede mostrar qué cuenta local de un usuario de Office 365 se han proyectado desde. Los siguientes se da por supuesto que Azure Connect AD se ha configurado para utilizar el delimitador de origen predeterminado de GUID de objeto (para obtener más información acerca de cómo configurar un delimitador de origen, vea [Azure Connect AD: conceptos de diseño](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) y se supone que tiene el módulo de Active Directory para powershell sido instalado (consulte [Herramientas RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span><span class="sxs-lookup"><span data-stu-id="8b2bd-p118">If you are using directory synchronization to create and manage your Office 365 users, you can display which local account an Office 365 user has been projected from. The following assumes that Azure AD Connect has been configured to use the default source anchor of ObjectGUID (for more on configuring a source anchor, see [Azure AD Connect: Design concepts](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) and assumes that the Active Directory module for powershell has been installed (see [RSAT tools](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):</span></span>

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a><span data-ttu-id="8b2bd-196">Vea también</span><span class="sxs-lookup"><span data-stu-id="8b2bd-196">See also</span></span>

[<span data-ttu-id="8b2bd-197">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="8b2bd-197">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="8b2bd-198">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="8b2bd-198">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="8b2bd-199">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="8b2bd-199">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

