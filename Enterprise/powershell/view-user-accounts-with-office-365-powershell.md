---
title: Ver cuentas de usuario con PowerShell de Office 365
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
- LIL_Placement
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Resumen: Ver, lista o mostrar las cuentas de usuario de varias maneras con Office 365 PowerShell.'
ms.openlocfilehash: b27f9045d26d4dabd3ada70766491f722d822a91
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="view-user-accounts-with-office-365-powershell"></a><span data-ttu-id="fffeb-103">Ver cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="fffeb-103">View user accounts with Office 365 PowerShell</span></span>

 <span data-ttu-id="fffeb-104">**Resumen:** Ver, lista o mostrar las cuentas de usuario de varias maneras con Office 365 PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fffeb-104">**Summary:** View, list, or display your user accounts in various ways with Office 365 PowerShell.</span></span>
  
<span data-ttu-id="fffeb-105">Aunque puede utilizar el centro de administración de Office 365 para ver las cuentas de los inquilinos de Office 365, también puede utilizar Office 365 PowerShell y hacer algunas cosas que no puede el centro de administración de Office 365.</span><span class="sxs-lookup"><span data-stu-id="fffeb-105">Although you can use the Office 365 Admin center to view the accounts for your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="fffeb-106">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="fffeb-106">Before you begin</span></span>

<span data-ttu-id="fffeb-p101">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="fffeb-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="display-office-365-user-account-information"></a><span data-ttu-id="fffeb-109">Mostrar información de la cuenta de usuario de Office 365</span><span class="sxs-lookup"><span data-stu-id="fffeb-109">Display Office 365 user account information</span></span>

<span data-ttu-id="fffeb-110">Para mostrar la lista completa de cuentas de usuario, ejecute este comando en el símbolo del sistema de Office 365 PowerShell o el entorno de secuencias de comandos integrado (ISE) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fffeb-110">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-MsolUser
```

<span data-ttu-id="fffeb-111">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="fffeb-111">You should see information similar to this:</span></span>
  
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

<span data-ttu-id="fffeb-p102">El cmdlet **Get-MsolUser** también tiene un conjunto de parámetros para filtrar el conjunto de cuentas de usuario que se muestran. Por ejemplo, para la lista de usuarios sin licencia (usuarios que han sido agregados a Office 365 pero aún no han ha autorizado para utilizar cualquiera de los servicios), ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="fffeb-p102">The **Get-MsolUser** cmdlet also has a set of parameters to filter the set of user accounts displayed. For example, for the list of unlicensed users (users who've been added to Office 365 but haven't yet been licensed to use any of the services), run this command.</span></span>
  
```
Get-MsolUser -UnlicensedUsersOnly
```

<span data-ttu-id="fffeb-114">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="fffeb-114">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

<span data-ttu-id="fffeb-115">Para obtener más información acerca de los parámetros adicionales para filtrar la visualización del conjunto de cuentas de usuario que se muestran, vea [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span><span class="sxs-lookup"><span data-stu-id="fffeb-115">For more information about additional parameters to filter the display the set of user accounts displayed, see [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .</span></span>
  
<span data-ttu-id="fffeb-p103">Para ser más selectivo en cuanto a la lista de cuentas que desea mostrar, puede utilizar el cmdlet **Where-Object** en combinación con el cmdlet **Get-MsolUser** . Para combinar los dos cmdlets, utilizamos el carácter "barra vertical" "|", que indica a Office 365 PowerShell tomar los resultados de un comando y enviarlo al siguiente comando. Aquí es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p103">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-MsolUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="fffeb-119">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fffeb-119">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fffeb-120">Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-120">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fffeb-p104">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Entre las llaves, el comando indica a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que el usuario UsageLocation cuenta propiedad ( ** $ \_. UsageLocation** ) no está especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-p104">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="fffeb-123">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="fffeb-123">You should see information similar to this:</span></span>
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

<span data-ttu-id="fffeb-p105">La propiedad **UsageLocation** es sólo una de las muchas propiedades asociadas a una cuenta de usuario. Para ver todas las propiedades de cuentas de usuario, utilice el cmdlet **Select-Object** y el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario específica. Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p105">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="fffeb-p106">Por ejemplo, en esta lista, **la ciudad** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede utilizar el siguiente comando para enumerar todas las cuentas de usuario para los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p106">For example, from this list, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="fffeb-p107">La sintaxis para el cmdlet **Where-Object** se muestra en estos ejemplos es **Where-Object {$\_.** [nombre de propiedad de la cuenta de usuario] [operador] [valor] **}**. > [operador] es **-eq** para equals, **-ne** para no igual a, **-lt** para menor que **-gt** para mayor y otros > [valor] es normalmente una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$Null** para sin especifica > consulte [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="fffeb-p107">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
<span data-ttu-id="fffeb-131">Puede comprobar el estado de bloqueo de cuenta de usuario con el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="fffeb-131">You can check the blocked status of a user account with the following command:</span></span>
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="fffeb-132">Seleccionar las propiedades de la cuenta de usuario que se van a mostrar</span><span class="sxs-lookup"><span data-stu-id="fffeb-132">Select the user account properties to display</span></span>

<span data-ttu-id="fffeb-133">El cmdlet [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) de forma predeterminada muestra tres propiedades de cuentas de usuario:</span><span class="sxs-lookup"><span data-stu-id="fffeb-133">The [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="fffeb-134">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="fffeb-134">UserPrincipalName</span></span>
    
- <span data-ttu-id="fffeb-135">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fffeb-135">DisplayName</span></span>
    
- <span data-ttu-id="fffeb-136">isLicensed</span><span class="sxs-lookup"><span data-stu-id="fffeb-136">isLicensed</span></span>
    
<span data-ttu-id="fffeb-p108">Si tiene propiedades adicionales, como el departamento para que el usuario trabaja y el país o la región donde el usuario utiliza los servicios de Office 365, puede ejecutar **Get-MsolUser** en combinación con el cmdlet **Select-Object** para especificar la lista de cuenta de usuario Propiedades. Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p108">If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-MsolUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="fffeb-139">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fffeb-139">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fffeb-140">Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-140">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fffeb-141">Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-141">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="fffeb-142">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="fffeb-142">You should see information similar to this:</span></span>
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

<span data-ttu-id="fffeb-p109">El cmdlet **Select-Object** le permite elegir las propiedades que desea que muestre un comando. Para ver todas las propiedades de cuentas de usuario, utilice el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario específica. Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p109">The **Select-Object** cmdlet allows you to pick and choose the properties you want a command to display. To see all of the properties for user accounts, use the wildcard character (*) to display them all for a specific user account. Here is an example:</span></span>
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

<span data-ttu-id="fffeb-p110">Para ser más selectivo en cuanto a la lista de cuentas que desea mostrar, puede también utilizar el cmdlet **Where-Object** . Aquí es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p110">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="fffeb-148">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fffeb-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fffeb-149">Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-149">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fffeb-p111">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ) y enviar la información resultante con el siguiente comando ( **|** ). Entre las llaves, el comando es instruir a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que el usuario UsageLocation cuenta propiedad ( ** $ \_. UsageLocation** ) no está especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-p111">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="fffeb-152">Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-152">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="fffeb-153">Verá información similar a esta:</span><span class="sxs-lookup"><span data-stu-id="fffeb-153">You should see information similar to this:</span></span>
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a><span data-ttu-id="fffeb-154">Usar el módulo de PowerShell Azure Active Directory V2 para mostrar cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="fffeb-154">Use the Azure Active Directory V2 PowerShell module to display user accounts</span></span>

<span data-ttu-id="fffeb-p112">Para mostrar las propiedades de cuentas de usuario con el módulo de Active Directory V2 PowerShell de Azure, use el cmdlet [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Pero en primer lugar, debe conectarse a su suscripción. Para las instrucciones, vea[Conectar con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="fffeb-p112">To display properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) cmdlet. But first, you must connect to your subscription. For the instructions, see[Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="display-office-365-user-account-information"></a><span data-ttu-id="fffeb-158">Mostrar información de la cuenta de usuario de Office 365</span><span class="sxs-lookup"><span data-stu-id="fffeb-158">Display Office 365 user account information</span></span>

<span data-ttu-id="fffeb-159">Para mostrar la lista completa de cuentas de usuario, ejecute este comando en el símbolo del sistema de Office 365 PowerShell o el entorno de secuencias de comandos integrado (ISE) de PowerShell.</span><span class="sxs-lookup"><span data-stu-id="fffeb-159">To display the full list of user accounts, run this command in your Office 365 PowerShell command prompt or the PowerShell Integrated Script Environment (ISE).</span></span>
  
```
Get-AzureADUser
```

<span data-ttu-id="fffeb-160">El cmdlet **Get-AzureADUser** de forma predeterminada muestra tres propiedades de cuentas de usuario:</span><span class="sxs-lookup"><span data-stu-id="fffeb-160">The **Get-AzureADUser** cmdlet by default displays three properties of user accounts:</span></span>
  
- <span data-ttu-id="fffeb-161">ObjectID</span><span class="sxs-lookup"><span data-stu-id="fffeb-161">ObjectID</span></span>
    
- <span data-ttu-id="fffeb-162">DisplayName</span><span class="sxs-lookup"><span data-stu-id="fffeb-162">DisplayName</span></span>
    
- <span data-ttu-id="fffeb-163">UserPrincipalName</span><span class="sxs-lookup"><span data-stu-id="fffeb-163">UserPrincipalName</span></span>
    
<span data-ttu-id="fffeb-p113">Para ser más selectivo en cuanto a la lista de cuentas que desea mostrar, puede utilizar el cmdlet **Where-Object** en combinación con el cmdlet **Get-AzureADUser** . Para combinar los dos cmdlets, utilizamos el carácter "barra vertical" "|", que indica a Office 365 PowerShell tomar los resultados de un comando y enviarlo al siguiente comando. Aquí es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p113">To be more selective about the list of accounts to display, you can use the **Where-Object** cmdlet in combination with the **Get-AzureADUser** cmdlet. To combine the two cmdlets, we use the "pipe" character "|", which tells Office 365 PowerShell to take the results of one command and send it to the next command. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

<span data-ttu-id="fffeb-167">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fffeb-167">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fffeb-168">Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-168">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fffeb-p114">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Entre las llaves, el comando indica a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que el usuario UsageLocation cuenta propiedad ( ** $ \_. UsageLocation** ) no está especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-p114">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ). Inside the braces, the command instructs Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
<span data-ttu-id="fffeb-p115">La propiedad **UsageLocation** es sólo una de las muchas propiedades asociadas a una cuenta de usuario. Para ver todas las propiedades de cuentas de usuario, utilice el cmdlet **Select-Object** y el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario, una página cada vez ( **más** ). Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p115">The **UsageLocation** property is only one of many properties associated with a user account. To see all of the properties for user accounts, use the **Select-Object** cmdlet and the wildcard character (*) to display them all for a specific user account, one page at a time ( **More** ). Here is an example:</span></span>
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

<span data-ttu-id="fffeb-p116">Por ejemplo, **Ciudad** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede utilizar el siguiente comando para enumerar todas las cuentas de usuario para los usuarios que viven en Londres:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p116">For example, **City** is the name of a user account property. This means you can use the following command to list all of the user accounts for users living in London:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  <span data-ttu-id="fffeb-p117">La sintaxis para el cmdlet **Where-Object** se muestra en estos ejemplos es **Where-Object {$\_.** [nombre de propiedad de la cuenta de usuario] [operador] [valor] **}**. > [operador] es **-eq** para equals, **-ne** para no igual a, **-lt** para menor que **-gt** para mayor y otros > [valor] es normalmente una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$Null** para sin especifica > consulte[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obtener más información.</span><span class="sxs-lookup"><span data-stu-id="fffeb-p117">The syntax for the **Where-Object** cmdlet shown in these examples is **Where-Object {$\_.** [user account property name] [comparison operator] [value] **}**.>  [comparison operator] is **-eq** for equals, **-ne** for not equals, **-lt** for less than, **-gt** for greater than, and others>  [value] is typically a string (a sequence of letters, numbers, and other characters), a numerical value, or **$Null** for unspecified>  See[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) for more information.</span></span>
  
### <a name="select-the-user-account-properties-to-display"></a><span data-ttu-id="fffeb-178">Seleccionar las propiedades de la cuenta de usuario que se van a mostrar</span><span class="sxs-lookup"><span data-stu-id="fffeb-178">Select the user account properties to display</span></span>

<span data-ttu-id="fffeb-p118">El cmdlet **Get-AzureADUser** de forma predeterminada muestra las propiedades UserPrincipalName, DisplayName y ObjectID de cuentas de usuario. Si tiene propiedades adicionales, como el departamento para que el usuario trabaja y el país o la región donde el usuario utiliza los servicios de Office 365, puede ejecutar **Get-AzureADUser** en combinación con el cmdlet **Select-Object** para especificar la lista de los usuarios propiedades de la cuenta. Éste es un ejemplo:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p118">The **Get-AzureADUser** cmdlet by default displays the ObjectID, DisplayName, and UserPrincipalName properties of user accounts. If you need additional properties, such as the department the user works for and the country/region where the user uses Office 365 services, you can run **Get-AzureADUser** in combination with the **Select-Object** cmdlet to specify the list of user account properties. Here is an example:</span></span>
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

<span data-ttu-id="fffeb-182">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fffeb-182">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fffeb-183">Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-183">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fffeb-184">Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-184">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
<span data-ttu-id="fffeb-p119">Para ser más selectivo en cuanto a la lista de cuentas que desea mostrar, puede también utilizar el cmdlet **Where-Object** . Aquí es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:</span><span class="sxs-lookup"><span data-stu-id="fffeb-p119">To be more selective about the list of accounts to display, you can also use the **Where-Object** cmdlet. Here is an example command that displays only those user accounts that have an unspecified usage location:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

<span data-ttu-id="fffeb-187">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="fffeb-187">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="fffeb-188">Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-188">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="fffeb-p120">Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ) y enviar la información resultante con el siguiente comando ( **|** ). Entre las llaves, el comando es instruir a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que el usuario UsageLocation cuenta propiedad ( ** $ \_. UsageLocation** ) no está especificado ( **-eq $Null** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-p120">Find all of the user accounts that have an unspecified usage location ( **Where-Object {$\_.UsageLocation -eq $Null}** ) and send the resulting information to the next command ( **|** ). Inside the braces, the command is instructing Office 365 PowerShell to only find the set of accounts in which the UsageLocation user account property ( **$\_.UsageLocation** ) is not specified ( **-eq $Null** ).</span></span>
    
- <span data-ttu-id="fffeb-191">Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, departamento, UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="fffeb-191">Display only the user account name, department, and usage location ( **Select-Object DisplayName, Department, UsageLocation** ).</span></span>
    
## <a name="new-to-office-365"></a><span data-ttu-id="fffeb-192">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="fffeb-192">New to Office 365?</span></span>

||
|:-----|
|<span data-ttu-id="fffeb-p121">![El icono reducido de LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **¿Es la primera vez que usa Office 365?**         LinkedIn Learning pone a su disposición vídeos gratuitos de cursos de [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5).</span><span class="sxs-lookup"><span data-stu-id="fffeb-p121">![The short icon for LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **New to Office 365?**         Discover free video courses for [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5), brought to you by LinkedIn Learning.</span></span> |
   
## <a name="see-also"></a><span data-ttu-id="fffeb-195">See also</span><span class="sxs-lookup"><span data-stu-id="fffeb-195">See also</span></span>

#### 

[<span data-ttu-id="fffeb-196">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="fffeb-196">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="fffeb-197">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="fffeb-197">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="fffeb-198">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="fffeb-198">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

