---
title: Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumen: Use Office 365 PowerShell para configurar las propiedades de una o varias cuentas de usuario en el inquilino de Office 365.'
ms.openlocfilehash: 5748bd382357168e4184754fb49fb7304e2d2474
ms.sourcegitcommit: d1022143bdefdd5583d8eff08046808657b49c94
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/02/2020
ms.locfileid: "44004723"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="d8851-103">Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8851-103">Configure user account properties with Office 365 PowerShell</span></span>

<span data-ttu-id="d8851-104">Aunque puede usar el centro de administración de Microsoft 365 para configurar las propiedades de las cuentas de usuario de su inquilino de Office 365, también puede usar PowerShell de Office 365 y realizar algunas acciones que el centro de administración no puede.</span><span class="sxs-lookup"><span data-stu-id="d8851-104">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="d8851-105">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="d8851-105">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="d8851-106">Para configurar las propiedades de las cuentas de usuario con el módulo Azure Active Directory PowerShell para Graph, use el cmdlet [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) y especifique las propiedades que se deben establecer o cambiar.</span><span class="sxs-lookup"><span data-stu-id="d8851-106">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="d8851-107">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="d8851-107">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d8851-108">Cambiar las propiedades de una cuenta de usuario específica</span><span class="sxs-lookup"><span data-stu-id="d8851-108">Change properties for a specific user account</span></span>

<span data-ttu-id="d8851-109">La cuenta se identifica con el parámetro **-objectId** y se establecen o cambian las propiedades específicas con parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="d8851-109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="d8851-110">A continuación se muestra una lista de los parámetros más comunes.</span><span class="sxs-lookup"><span data-stu-id="d8851-110">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d8851-111">-Department "\<nombre del Departamento>"</span><span class="sxs-lookup"><span data-stu-id="d8851-111">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d8851-112">-DisplayName "\<nombre de usuario completo>"</span><span class="sxs-lookup"><span data-stu-id="d8851-112">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d8851-113">-FacsimilieTelephoneNumber "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="d8851-113">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="d8851-114">-GivenName "\<nombre de usuario>"</span><span class="sxs-lookup"><span data-stu-id="d8851-114">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="d8851-115">-Apellidos\<"apellidos del usuario>"</span><span class="sxs-lookup"><span data-stu-id="d8851-115">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="d8851-116">-Mobile "\<número de teléfono móvil>"</span><span class="sxs-lookup"><span data-stu-id="d8851-116">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d8851-117">-Cargo "\<nombre de trabajo>"</span><span class="sxs-lookup"><span data-stu-id="d8851-117">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="d8851-118">-PreferredLanguage "\<> de idioma"</span><span class="sxs-lookup"><span data-stu-id="d8851-118">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d8851-119">-Dirección "\<calle>"</span><span class="sxs-lookup"><span data-stu-id="d8851-119">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d8851-120">-City "\<nombre de la ciudad>"</span><span class="sxs-lookup"><span data-stu-id="d8851-120">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d8851-121">-Estado "\<nombre de estado>"</span><span class="sxs-lookup"><span data-stu-id="d8851-121">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d8851-122">-CódigoPostal "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="d8851-122">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d8851-123">-Country "\<nombre de país>"</span><span class="sxs-lookup"><span data-stu-id="d8851-123">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d8851-124">-TelephoneNumber "\<número de teléfono de la oficina>"</span><span class="sxs-lookup"><span data-stu-id="d8851-124">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d8851-125">-UsageLocation "\<código de país o región de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="d8851-125">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d8851-126">Este es el código de país o región de dos letras ISO 3166-1 (a2).</span><span class="sxs-lookup"><span data-stu-id="d8851-126">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d8851-127">Consulte [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para obtener más parámetros.</span><span class="sxs-lookup"><span data-stu-id="d8851-127">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="d8851-128">Para mostrar el nombre principal de usuario de las cuentas de usuario, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="d8851-128">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="d8851-129">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="d8851-129">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d8851-130">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-130">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-131">Ordenar la lista de nombres principales de usuario alfabéticamente ( **ordenar UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-131">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-132">Mostrar solo la propiedad de nombre principal de usuario para cada cuenta ( **Seleccione UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-132">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>

- <span data-ttu-id="d8851-133">Mostrar una pantalla a la vez ( **más** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-133">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d8851-134">En este comando se enumeran todas las cuentas.</span><span class="sxs-lookup"><span data-stu-id="d8851-134">This command will list all of your accounts.</span></span> <span data-ttu-id="d8851-135">Si desea mostrar el nombre principal de usuario de una cuenta en función de su nombre para mostrar (nombre y apellido), rellene la variable **$username** a continuación (quite \< los caracteres y >) y, a continuación, ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="d8851-135">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d8851-136">En este ejemplo se muestra el nombre principal de usuario de la cuenta de usuario con el nombre para mostrar de los alféizares de Caleb.</span><span class="sxs-lookup"><span data-stu-id="d8851-136">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d8851-137">Mediante el uso de una variable **$UPN** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="d8851-137">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="d8851-138">Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificando su nombre para mostrar en lugar de su nombre principal de usuario:</span><span class="sxs-lookup"><span data-stu-id="d8851-138">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d8851-139">Cambiar las propiedades de todas las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d8851-139">Change properties for all user accounts</span></span>

<span data-ttu-id="d8851-140">Para cambiar las propiedades de todos los usuarios, puede usar la combinación de los cmdlets **Get-AzureADUser** y **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="d8851-140">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="d8851-141">En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios:</span><span class="sxs-lookup"><span data-stu-id="d8851-141">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d8851-142">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="d8851-142">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d8851-143">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-143">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-144">Establezca la ubicación del usuario en Francia ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-144">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d8851-145">Cambiar las propiedades de un conjunto específico de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d8851-145">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d8851-146">Para cambiar las propiedades de un conjunto específico de cuentas de usuario, puede usar la combinación de los cmdlets **Get-AzureADUser**, **Where**y **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="d8851-146">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="d8851-147">En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios del departamento de contabilidad:</span><span class="sxs-lookup"><span data-stu-id="d8851-147">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d8851-148">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="d8851-148">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d8851-149">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-149">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-150">Busque todas las cuentas de usuario que tengan su propiedad Department establecida en "Accounting" ( **donde {$ _. Department-EQ "Accounting"}** ) y enviar la información resultante al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-150">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-151">Establezca la ubicación del usuario en Francia ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-151">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d8851-152">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8851-152">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d8851-153">Para configurar las propiedades de las cuentas de usuario con el módulo Microsoft Azure Active Directory para Windows PowerShell, use el cmdlet **set-MsolUser** y especifique las propiedades que se van a establecer o cambiar.</span><span class="sxs-lookup"><span data-stu-id="d8851-153">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the **Set-MsolUser** cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="d8851-154">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d8851-154">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="d8851-155">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="d8851-155">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="d8851-156">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d8851-156">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d8851-157">Cambiar las propiedades de una cuenta de usuario específica</span><span class="sxs-lookup"><span data-stu-id="d8851-157">Change properties for a specific user account</span></span>

<span data-ttu-id="d8851-158">Para configurar las propiedades de una cuenta de usuario específica, use el cmdlet [set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) y especifique las propiedades que se van a establecer o cambiar.</span><span class="sxs-lookup"><span data-stu-id="d8851-158">To configure properties for a specific user account, you use the [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="d8851-159">La cuenta se identifica con el parámetro **-UserPrincipalName** y se establecen o cambian las propiedades específicas con parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="d8851-159">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="d8851-160">A continuación se muestra una lista con los parámetros más comunes.</span><span class="sxs-lookup"><span data-stu-id="d8851-160">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d8851-161">-City "\<nombre de la ciudad>"</span><span class="sxs-lookup"><span data-stu-id="d8851-161">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d8851-162">-Country "\<nombre de país>"</span><span class="sxs-lookup"><span data-stu-id="d8851-162">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d8851-163">-Department "\<nombre del Departamento>"</span><span class="sxs-lookup"><span data-stu-id="d8851-163">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d8851-164">-DisplayName "\<nombre de usuario completo>"</span><span class="sxs-lookup"><span data-stu-id="d8851-164">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d8851-165">-Fax "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="d8851-165">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="d8851-166">-FirstName "\<nombre de usuario>"</span><span class="sxs-lookup"><span data-stu-id="d8851-166">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="d8851-167">-LastName "\<apellidos del usuario>"</span><span class="sxs-lookup"><span data-stu-id="d8851-167">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="d8851-168">-MobilePhone "\<número de teléfono móvil>"</span><span class="sxs-lookup"><span data-stu-id="d8851-168">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d8851-169">-Office "\<ubicación de oficina>"</span><span class="sxs-lookup"><span data-stu-id="d8851-169">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="d8851-170">-PhoneNumber "\<número de teléfono de la oficina>"</span><span class="sxs-lookup"><span data-stu-id="d8851-170">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d8851-171">-CódigoPostal "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="d8851-171">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d8851-172">-PreferredLanguage "\<> de idioma"</span><span class="sxs-lookup"><span data-stu-id="d8851-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d8851-173">-Estado "\<nombre de estado>"</span><span class="sxs-lookup"><span data-stu-id="d8851-173">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d8851-174">-Dirección "\<calle>"</span><span class="sxs-lookup"><span data-stu-id="d8851-174">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d8851-175">-Title "\<nombre del título>"</span><span class="sxs-lookup"><span data-stu-id="d8851-175">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="d8851-176">-UsageLocation "\<código de país o región de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="d8851-176">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d8851-177">Este es el código de país o región de dos letras ISO 3166-1 (a2).</span><span class="sxs-lookup"><span data-stu-id="d8851-177">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d8851-178">Consulte [set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) para obtener más parámetros.</span><span class="sxs-lookup"><span data-stu-id="d8851-178">See [Set-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194136(v=azure.100)) for additional parameters.</span></span>

<span data-ttu-id="d8851-179">Para ver los nombres principales de usuario de todos los usuarios, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="d8851-179">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort UserPrincipalName | Select UserPrincipalName | More
```

<span data-ttu-id="d8851-180">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="d8851-180">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d8851-181">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-181">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-182">Ordenar la lista de nombres principales de usuario alfabéticamente ( **ordenar UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-182">Sort the list of User Principal Names alphabetically ( **Sort UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-183">Mostrar solo la propiedad de nombre principal de usuario para cada cuenta ( **Seleccione UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-183">Display just the User Principal Name property for each account ( **Select UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="d8851-184">Mostrar una pantalla a la vez ( **más** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-184">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d8851-185">En este comando se enumeran todas las cuentas.</span><span class="sxs-lookup"><span data-stu-id="d8851-185">This command will list all of your accounts.</span></span> <span data-ttu-id="d8851-186">Si desea mostrar el nombre principal de usuario de una cuenta en función de su nombre para mostrar (nombre y apellido), rellene la variable **$username** a continuación (quite \< los caracteres y >) y, a continuación, ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="d8851-186">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d8851-187">En este ejemplo se muestra el nombre principal de usuario del usuario denominado Caleb alféizares.</span><span class="sxs-lookup"><span data-stu-id="d8851-187">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d8851-188">Mediante el uso de una variable **$UPN** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="d8851-188">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="d8851-189">Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificando su nombre para mostrar en lugar de su nombre principal de usuario:</span><span class="sxs-lookup"><span data-stu-id="d8851-189">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d8851-190">Cambiar las propiedades de todas las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d8851-190">Change properties for all user accounts</span></span>

<span data-ttu-id="d8851-p110">Para cambiar las propiedades de todos los usuarios, puede combinar los cmdlets **Get-MsolUser** y **Set-MsolUser**. En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios:</span><span class="sxs-lookup"><span data-stu-id="d8851-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d8851-193">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="d8851-193">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d8851-194">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-194">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-195">Establezca la ubicación del usuario en Francia ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-195">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d8851-196">Cambiar las propiedades de un conjunto específico de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d8851-196">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d8851-197">Para cambiar las propiedades de un conjunto específico de cuentas de usuario, puede usar la combinación de los cmdlets **Get-msoluser**, **Where**y **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="d8851-197">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="d8851-198">En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios del departamento de contabilidad:</span><span class="sxs-lookup"><span data-stu-id="d8851-198">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d8851-199">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="d8851-199">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d8851-200">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-200">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-201">Busque todas las cuentas de usuario que tengan su propiedad Department establecida en "Accounting" ( **donde {$ _. Department-EQ "Accounting"}** ) y enviar la información resultante al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-201">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d8851-202">Establezca la ubicación del usuario en Francia ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="d8851-202">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="d8851-203">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d8851-203">See also</span></span>

[<span data-ttu-id="d8851-204">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d8851-204">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d8851-205">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d8851-205">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d8851-206">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d8851-206">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
