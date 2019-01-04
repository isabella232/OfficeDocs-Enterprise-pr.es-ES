---
title: Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumen: Use PowerShell de Office 365 para configurar las propiedades de individuales o de varias cuentas de usuario en el inquilino de Office 365.'
ms.openlocfilehash: 4db63482fdcc1d6cb186e663fd55c13186b33813
ms.sourcegitcommit: 15db0f1e5f8036e46063662d7df22387906f8ba7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "27546491"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="5cd14-103">Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="5cd14-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="5cd14-104">**Resumen:** Usar Office 365 PowerShell para configurar las propiedades de individuales o de varias cuentas de usuario en el inquilino de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5cd14-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="5cd14-105">Aunque puede usar el centro de administración de Office 365 para configurar las propiedades de las cuentas de usuario de su inquilino de Office 365, también puede usar PowerShell de Office 365 y hacer cosas que no se puede el centro de administración de Office 365.</span><span class="sxs-lookup"><span data-stu-id="5cd14-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="5cd14-106">Usar Azure Active Directory PowerShell para el módulo de gráfico</span><span class="sxs-lookup"><span data-stu-id="5cd14-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="5cd14-107">Para configurar las propiedades de cuentas de usuario con Azure Active Directory PowerShell para el módulo de gráfico, use el cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) y especificar las propiedades para establecer o cambiar.</span><span class="sxs-lookup"><span data-stu-id="5cd14-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="5cd14-108">Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="5cd14-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="5cd14-109">Cambiar las propiedades de una cuenta de usuario específica</span><span class="sxs-lookup"><span data-stu-id="5cd14-109">Change properties for a specific user account</span></span>

<span data-ttu-id="5cd14-p101">Identificar la cuenta con el parámetro **- ObjectID** y establecer o cambiar las propiedades específicas con parámetros adicionales. Aquí tiene una lista de los parámetros más comunes.</span><span class="sxs-lookup"><span data-stu-id="5cd14-p101">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="5cd14-112">-Departamento "\<nombre de departamento >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="5cd14-113">-DisplayName "\<nombre completo del usuario >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="5cd14-114">-FacsimilieTelephoneNumber "\<número de fax >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="5cd14-115">-GivenName "\<nombre de usuario >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="5cd14-116">-Apellido "\<apellidos del usuario >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="5cd14-117">-Móvil "\<número de teléfono móvil >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="5cd14-118">-JobTitle "\<puesto >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="5cd14-119">-PreferredLanguage "\<idioma >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="5cd14-120">-StreetAddress "\<dirección postal >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="5cd14-121">-Ciudad "\<nombre de la ciudad >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="5cd14-122">-Estado "\<nombre de estado >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="5cd14-123">-PostalCode "\<código postal >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="5cd14-124">-País "\<nombre del país >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="5cd14-125">-TelephoneNumber "\<número de teléfono de office >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="5cd14-126">Propiedad - UsageLocation "\<código de país o región 2 caracteres >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="5cd14-127">Este es el código de región o país de dos letras ISO 3166-1 alfa-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="5cd14-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="5cd14-128">Vea [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="5cd14-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="5cd14-129">Para mostrar el nombre Principal de usuario para las cuentas de usuario, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="5cd14-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="5cd14-130">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="5cd14-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5cd14-131">Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-132">Ordenar alfabéticamente la lista de nombres principales de usuario ( **Objeto Sort UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-133">Mostrar sólo la propiedad de nombre Principal de usuario para cada cuenta ( **UserPrincipalName Select-Object** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="5cd14-134">Mostrarlos una pantalla a la vez ( **más** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="5cd14-p102">Este comando obtendrá una lista con todas las cuentas. Si desea mostrar el nombre Principal de usuario de una cuenta en función de su presentación name (nombre y el apellido), rellene la variable **$userName** más abajo (eliminación de la \< y > caracteres), y, a continuación, ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="5cd14-p102">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5cd14-137">En este ejemplo se muestra el nombre Principal de usuario para la cuenta de usuario con el nombre para mostrar de Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="5cd14-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5cd14-p103">Mediante el uso de una variable de **$upn** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar. Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificar su nombre para mostrar en lugar de su nombre Principal de usuario:</span><span class="sxs-lookup"><span data-stu-id="5cd14-p103">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="5cd14-140">Cambiar las propiedades de todas las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="5cd14-140">Change properties for all user accounts</span></span>

<span data-ttu-id="5cd14-p104">Para cambiar las propiedades de todos los usuarios, puede usar la combinación de los cmdlets **Get-AzureADUser** y **Set-AzureADUser** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios a Francia:</span><span class="sxs-lookup"><span data-stu-id="5cd14-p104">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="5cd14-143">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="5cd14-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5cd14-144">Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-145">Establezca la ubicación del usuario en Francia ( **Set-AzureADUser-propiedad UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="5cd14-146">Cambiar las propiedades de un conjunto específico de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="5cd14-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="5cd14-p105">Para cambiar las propiedades de un conjunto específico de la cuenta de usuario, puede usar la combinación de los cmdlets **Get-AzureADUser**, **donde**y **Set-AzureADUser** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios del departamento de contabilidad a Francia:</span><span class="sxs-lookup"><span data-stu-id="5cd14-p105">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="5cd14-149">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="5cd14-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5cd14-150">Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-151">Buscar todas las cuentas de usuario que tienen su propiedad departamento establecida en "Contabilidad" ( **donde {$_. Departamento - eq "Contabilidad"}** ) y enviar la información resultante con el siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-152">Establezca la ubicación del usuario en Francia ( **Set-AzureADUser-propiedad UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="5cd14-153">Usar el módulo de Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5cd14-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="5cd14-154">Para configurar las propiedades de cuentas de usuario con el Microsoft Azure Active Directory módulo para Windows PowerShell, use el cmdlet Set-MsolUser y especificar las propiedades para establecer o cambiar.</span><span class="sxs-lookup"><span data-stu-id="5cd14-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="5cd14-155">Primero, [Conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="5cd14-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="5cd14-156">Cambiar las propiedades de una cuenta de usuario específica</span><span class="sxs-lookup"><span data-stu-id="5cd14-156">Change properties for a specific user account</span></span>

<span data-ttu-id="5cd14-157">Para configurar las propiedades de una cuenta de usuario específica, use el cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) y especificar las propiedades para establecer o cambiar.</span><span class="sxs-lookup"><span data-stu-id="5cd14-157">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="5cd14-p106">Identificar la cuenta con el parámetro **- UserPrincipalName** y establecer o cambiar las propiedades específicas con parámetros adicionales. Aquí tiene una lista de los parámetros más comunes.</span><span class="sxs-lookup"><span data-stu-id="5cd14-p106">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="5cd14-160">-Ciudad "\<nombre de la ciudad >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-160">-City "\<city name>"</span></span>
    
- <span data-ttu-id="5cd14-161">-País "\<nombre del país >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-161">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="5cd14-162">-Departamento "\<nombre de departamento >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-162">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="5cd14-163">-DisplayName "\<nombre completo del usuario >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-163">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="5cd14-164">-Fax "\<número de fax >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-164">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="5cd14-165">-FirstName "\<nombre de usuario >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-165">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="5cd14-166">-LastName "\<apellidos del usuario >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-166">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="5cd14-167">-MobilePhone "\<número de teléfono móvil >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-167">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="5cd14-168">-Office "\<ubicación de la oficina >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-168">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="5cd14-169">-PhoneNumber "\<número de teléfono de office >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-169">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="5cd14-170">-PostalCode "\<código postal >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-170">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="5cd14-171">-PreferredLanguage "\<idioma >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-171">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="5cd14-172">-Estado "\<nombre de estado >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-172">-State "\<state name>"</span></span>
    
- <span data-ttu-id="5cd14-173">-StreetAddress "\<dirección postal >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="5cd14-174">-Title "\<nombre título >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-174">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="5cd14-175">Propiedad - UsageLocation "\<código de país o región 2 caracteres >"</span><span class="sxs-lookup"><span data-stu-id="5cd14-175">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="5cd14-176">Este es el código de región o país de dos letras ISO 3166-1 alfa-2 (A2).</span><span class="sxs-lookup"><span data-stu-id="5cd14-176">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="5cd14-177">Vea [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="5cd14-177">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="5cd14-178">Para ver los nombres de entidad de seguridad de usuario de todos los usuarios, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="5cd14-178">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="5cd14-179">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="5cd14-179">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5cd14-180">Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-180">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-181">Ordenar alfabéticamente la lista de nombres principales de usuario ( **Objeto Sort UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-181">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-182">Mostrar sólo la propiedad de nombre Principal de usuario para cada cuenta ( **UserPrincipalName Select-Object** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-182">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="5cd14-183">Mostrarlos una pantalla a la vez ( **más** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-183">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="5cd14-p107">Este comando obtendrá una lista con todas las cuentas. Si desea mostrar el nombre Principal de usuario de una cuenta en función de su presentación name (nombre y el apellido), rellene la variable **$userName** más abajo (eliminación de la \< y > caracteres), y, a continuación, ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="5cd14-p107">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5cd14-186">En este ejemplo se muestra el nombre de entidad de seguridad de usuario para el usuario llamado Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="5cd14-186">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="5cd14-p108">Mediante el uso de una variable de **$upn** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar. Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificar su nombre para mostrar en lugar de su nombre Principal de usuario:</span><span class="sxs-lookup"><span data-stu-id="5cd14-p108">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="5cd14-189">Cambiar las propiedades de todas las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="5cd14-189">Change properties for all user accounts</span></span>

<span data-ttu-id="5cd14-p109">Para cambiar las propiedades de todos los usuarios, puede combinar los cmdlets **Get-MsolUser** y **Set-MsolUser**. En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios:</span><span class="sxs-lookup"><span data-stu-id="5cd14-p109">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="5cd14-192">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="5cd14-192">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5cd14-193">Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-193">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-194">Establezca la ubicación del usuario en Francia ( **Set-MsolUser-propiedad UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-194">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="5cd14-195">Cambiar las propiedades de un conjunto específico de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="5cd14-195">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="5cd14-p110">Para cambiar las propiedades de un conjunto específico de la cuenta de usuario, puede usar la combinación de los cmdlets **Get-MsolUser**, **Where-Object**y **Set-MsolUser** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios del departamento de contabilidad a Francia:</span><span class="sxs-lookup"><span data-stu-id="5cd14-p110">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="5cd14-198">Este comando indica a Office 365 PowerShell para:</span><span class="sxs-lookup"><span data-stu-id="5cd14-198">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="5cd14-199">Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-199">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-200">Buscar todas las cuentas de usuario que tienen su propiedad departamento establecido en "Contabilidad" ( **Where-Object {$_. Departamento - eq "Contabilidad"}** ) y enviar la información resultante con el siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-200">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="5cd14-201">Establezca la ubicación del usuario en Francia ( **Set-MsolUser-propiedad UsageLocation "FR"** ).</span><span class="sxs-lookup"><span data-stu-id="5cd14-201">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="5cd14-202">Vea también</span><span class="sxs-lookup"><span data-stu-id="5cd14-202">See also</span></span>

[<span data-ttu-id="5cd14-203">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5cd14-203">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="5cd14-204">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5cd14-204">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="5cd14-205">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="5cd14-205">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
