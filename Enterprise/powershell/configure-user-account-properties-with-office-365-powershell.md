---
title: Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/07/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumen: Use Office 365 PowerShell para configurar las propiedades de una o varias cuentas de usuario en el inquilino de Office 365.'
ms.openlocfilehash: 67ce7d3c57f286f0b2365aa2503fdf1c8bc13429
ms.sourcegitcommit: 4b057db053e93b0165f1ec6c4799cff4c2852566
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/25/2019
ms.locfileid: "39257661"
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="2adfe-103">Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="2adfe-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="2adfe-104">**Resumen:** Use Office 365 PowerShell para configurar las propiedades de una o varias cuentas de usuario en el inquilino de Office 365.</span><span class="sxs-lookup"><span data-stu-id="2adfe-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="2adfe-105">Aunque puede usar el centro de administración de Microsoft 365 para configurar las propiedades de las cuentas de usuario de su inquilino de Office 365, también puede usar PowerShell de Office 365 y realizar algunas acciones que el centro de administración no puede.</span><span class="sxs-lookup"><span data-stu-id="2adfe-105">Although you can use the Microsoft 365 admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the admin center cannot.</span></span>
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a><span data-ttu-id="2adfe-106">Use el módulo de PowerShell Azure Active Directory para Graph</span><span class="sxs-lookup"><span data-stu-id="2adfe-106">Use the Azure Active Directory PowerShell for Graph module</span></span>

<span data-ttu-id="2adfe-107">Para configurar las propiedades de las cuentas de usuario con el módulo Azure Active Directory PowerShell para Graph, use el cmdlet [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) y especifique las propiedades que se deben establecer o cambiar.</span><span class="sxs-lookup"><span data-stu-id="2adfe-107">To configure properties for user accounts with the Azure Active Directory PowerShell for Graph module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="2adfe-108">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span><span class="sxs-lookup"><span data-stu-id="2adfe-108">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).</span></span>
   
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="2adfe-109">Cambiar las propiedades de una cuenta de usuario específica</span><span class="sxs-lookup"><span data-stu-id="2adfe-109">Change properties for a specific user account</span></span>

<span data-ttu-id="2adfe-110">La cuenta se identifica con el parámetro **-objectId** y se establecen o cambian las propiedades específicas con parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="2adfe-110">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="2adfe-111">A continuación se muestra una lista de los parámetros más comunes.</span><span class="sxs-lookup"><span data-stu-id="2adfe-111">Here's a list of the most common parameters.</span></span>
  
- <span data-ttu-id="2adfe-112">-Department "\<nombre del Departamento>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-112">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="2adfe-113">-DisplayName "\<nombre de usuario completo>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-113">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="2adfe-114">-FacsimilieTelephoneNumber "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-114">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="2adfe-115">-GivenName "\<nombre de usuario>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-115">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="2adfe-116">-Apellidos\<"apellidos del usuario>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-116">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="2adfe-117">-Mobile "\<número de teléfono móvil>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-117">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="2adfe-118">-Cargo "\<nombre de trabajo>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-118">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="2adfe-119">-PreferredLanguage "\<> de idioma"</span><span class="sxs-lookup"><span data-stu-id="2adfe-119">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="2adfe-120">-Dirección "\<calle>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-120">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="2adfe-121">-City "\<nombre de la ciudad>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-121">-City "\<city name>"</span></span>
    
- <span data-ttu-id="2adfe-122">-Estado "\<nombre de estado>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-122">-State "\<state name>"</span></span>
    
- <span data-ttu-id="2adfe-123">-CódigoPostal "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="2adfe-123">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="2adfe-124">-Country "\<nombre de país>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-124">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="2adfe-125">-TelephoneNumber "\<número de teléfono de la oficina>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-125">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="2adfe-126">-UsageLocation "\<código de país o región de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-126">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="2adfe-127">Este es el código de país o región de dos letras ISO 3166-1 (a2).</span><span class="sxs-lookup"><span data-stu-id="2adfe-127">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="2adfe-128">Consulte [set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) para obtener más parámetros.</span><span class="sxs-lookup"><span data-stu-id="2adfe-128">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>


<span data-ttu-id="2adfe-129">Para mostrar el nombre principal de usuario de las cuentas de usuario, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="2adfe-129">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```powershell
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="2adfe-130">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="2adfe-130">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="2adfe-131">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-131">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-132">Ordenar la lista de nombres principales de usuario alfabéticamente ( **Sort-Object UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-132">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-133">Mostrar solo la propiedad de nombre principal de usuario para cada cuenta ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-133">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="2adfe-134">Mostrar una pantalla a la vez ( **más** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-134">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="2adfe-135">En este comando se enumeran todas las cuentas.</span><span class="sxs-lookup"><span data-stu-id="2adfe-135">This command will list all of your accounts.</span></span> <span data-ttu-id="2adfe-136">Si desea mostrar el nombre principal de usuario de una cuenta en función de su nombre para mostrar (nombre y apellido), rellene la variable **$username** a continuación (quite \< los caracteres y >) y, a continuación, ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="2adfe-136">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="2adfe-137">En este ejemplo se muestra el nombre principal de usuario de la cuenta de usuario con el nombre para mostrar de los alféizares de Caleb.</span><span class="sxs-lookup"><span data-stu-id="2adfe-137">This example displays the User Principal Name for the user account with the display name of Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="2adfe-138">Mediante el uso de una variable **$UPN** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="2adfe-138">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="2adfe-139">Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificando su nombre para mostrar en lugar de su nombre principal de usuario:</span><span class="sxs-lookup"><span data-stu-id="2adfe-139">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="2adfe-140">Cambiar las propiedades de todas las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="2adfe-140">Change properties for all user accounts</span></span>

<span data-ttu-id="2adfe-141">Para cambiar las propiedades de todos los usuarios, puede usar la combinación de los cmdlets **Get-AzureADUser** y **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="2adfe-141">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="2adfe-142">En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios:</span><span class="sxs-lookup"><span data-stu-id="2adfe-142">The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="2adfe-143">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="2adfe-143">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="2adfe-144">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-144">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-145">Establezca la ubicación del usuario en Francia ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-145">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="2adfe-146">Cambiar las propiedades de un conjunto específico de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="2adfe-146">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="2adfe-147">Para cambiar las propiedades de un conjunto específico de cuentas de usuario, puede usar la combinación de los cmdlets **Get-AzureADUser**, **Where**y **set-AzureADUser** .</span><span class="sxs-lookup"><span data-stu-id="2adfe-147">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets.</span></span> <span data-ttu-id="2adfe-148">En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios del departamento de contabilidad:</span><span class="sxs-lookup"><span data-stu-id="2adfe-148">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="2adfe-149">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="2adfe-149">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="2adfe-150">Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-150">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-151">Busque todas las cuentas de usuario que tengan su propiedad Department establecida en "Accounting" ( **donde {$ _. Department-EQ "Accounting"}** ) y enviar la información resultante al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-151">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-152">Establezca la ubicación del usuario en Francia ( **set-AzureADUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-152">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="2adfe-153">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2adfe-153">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="2adfe-154">Para configurar las propiedades de las cuentas de usuario con el módulo Microsoft Azure Active Directory para Windows PowerShell, use el cmdlet Set-MsolUser y especifique las propiedades que se van a establecer o cambiar.</span><span class="sxs-lookup"><span data-stu-id="2adfe-154">To configure properties for user accounts with the Microsoft Azure Active Directory Module for Windows PowerShell, you use the Set-MsolUser cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="2adfe-155">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="2adfe-155">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>
  
>[!Note]
><span data-ttu-id="2adfe-156">PowerShell Core no es compatible con el módulo Microsoft Azure Active Directory para el módulo y los cmdlets de Windows PowerShell con **msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="2adfe-156">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="2adfe-157">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2adfe-157">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="2adfe-158">Cambiar las propiedades de una cuenta de usuario específica</span><span class="sxs-lookup"><span data-stu-id="2adfe-158">Change properties for a specific user account</span></span>

<span data-ttu-id="2adfe-159">Para configurar las propiedades de una cuenta de usuario específica, use el cmdlet [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) y especifique las propiedades que se van a establecer o cambiar.</span><span class="sxs-lookup"><span data-stu-id="2adfe-159">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change.</span></span> 

<span data-ttu-id="2adfe-160">La cuenta se identifica con el parámetro **-UserPrincipalName** y se establecen o cambian las propiedades específicas con parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="2adfe-160">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters.</span></span> <span data-ttu-id="2adfe-161">A continuación se muestra una lista con los parámetros más comunes.</span><span class="sxs-lookup"><span data-stu-id="2adfe-161">Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="2adfe-162">-City "\<nombre de la ciudad>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-162">-City "\<city name>"</span></span>
    
- <span data-ttu-id="2adfe-163">-Country "\<nombre de país>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-163">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="2adfe-164">-Department "\<nombre del Departamento>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-164">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="2adfe-165">-DisplayName "\<nombre de usuario completo>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-165">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="2adfe-166">-Fax "\<número de fax>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-166">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="2adfe-167">-FirstName "\<nombre de usuario>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-167">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="2adfe-168">-LastName "\<apellidos del usuario>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-168">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="2adfe-169">-MobilePhone "\<número de teléfono móvil>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-169">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="2adfe-170">-Office "\<ubicación de oficina>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-170">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="2adfe-171">-PhoneNumber "\<número de teléfono de la oficina>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-171">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="2adfe-172">-CódigoPostal "\<> de código postal"</span><span class="sxs-lookup"><span data-stu-id="2adfe-172">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="2adfe-173">-PreferredLanguage "\<> de idioma"</span><span class="sxs-lookup"><span data-stu-id="2adfe-173">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="2adfe-174">-Estado "\<nombre de estado>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-174">-State "\<state name>"</span></span>
    
- <span data-ttu-id="2adfe-175">-Dirección "\<calle>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-175">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="2adfe-176">-Title "\<nombre del título>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-176">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="2adfe-177">-UsageLocation "\<código de país o región de 2 caracteres>"</span><span class="sxs-lookup"><span data-stu-id="2adfe-177">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="2adfe-178">Este es el código de país o región de dos letras ISO 3166-1 (a2).</span><span class="sxs-lookup"><span data-stu-id="2adfe-178">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="2adfe-179">Consulte [set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) para obtener más parámetros.</span><span class="sxs-lookup"><span data-stu-id="2adfe-179">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>

<span data-ttu-id="2adfe-180">Para ver los nombres principales de usuario de todos los usuarios, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="2adfe-180">To see the User Principal Names of all your users, run the following command.</span></span>
  
```powershell
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="2adfe-181">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="2adfe-181">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="2adfe-182">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-182">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-183">Ordenar la lista de nombres principales de usuario alfabéticamente ( **Sort-Object UserPrincipalName** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-183">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-184">Mostrar solo la propiedad de nombre principal de usuario para cada cuenta ( **Select-Object UserPrincipalName** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-184">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="2adfe-185">Mostrar una pantalla a la vez ( **más** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-185">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="2adfe-186">En este comando se enumeran todas las cuentas.</span><span class="sxs-lookup"><span data-stu-id="2adfe-186">This command will list all of your accounts.</span></span> <span data-ttu-id="2adfe-187">Si desea mostrar el nombre principal de usuario de una cuenta en función de su nombre para mostrar (nombre y apellido), rellene la variable **$username** a continuación (quite \< los caracteres y >) y, a continuación, ejecute los siguientes comandos:</span><span class="sxs-lookup"><span data-stu-id="2adfe-187">If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```powershell
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="2adfe-188">En este ejemplo se muestra el nombre principal de usuario del usuario denominado Caleb alféizares.</span><span class="sxs-lookup"><span data-stu-id="2adfe-188">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```powershell
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="2adfe-189">Mediante el uso de una variable **$UPN** , puede realizar cambios en las cuentas individuales en función de su nombre para mostrar.</span><span class="sxs-lookup"><span data-stu-id="2adfe-189">By using a **$upn** variable, you can make changes to individual accounts based on their display name.</span></span> <span data-ttu-id="2adfe-190">Este es un ejemplo de configuración de la ubicación de uso de Belinda Newman en Francia, pero especificando su nombre para mostrar en lugar de su nombre principal de usuario:</span><span class="sxs-lookup"><span data-stu-id="2adfe-190">Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```powershell
$userName="<display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="2adfe-191">Cambiar las propiedades de todas las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="2adfe-191">Change properties for all user accounts</span></span>

<span data-ttu-id="2adfe-p110">Para cambiar las propiedades de todos los usuarios, puede combinar los cmdlets **Get-MsolUser** y **Set-MsolUser**. En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios:</span><span class="sxs-lookup"><span data-stu-id="2adfe-p110">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```powershell
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="2adfe-194">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="2adfe-194">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="2adfe-195">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-195">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-196">Establezca la ubicación del usuario en Francia ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-196">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="2adfe-197">Cambiar las propiedades de un conjunto específico de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="2adfe-197">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="2adfe-198">Para cambiar las propiedades de un conjunto específico de cuentas de usuario, puede usar la combinación de los cmdlets **Get-msoluser**, **Where-Object**y **set-MsolUser** .</span><span class="sxs-lookup"><span data-stu-id="2adfe-198">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets.</span></span> <span data-ttu-id="2adfe-199">En el siguiente ejemplo se cambia a Francia la ubicación de uso de todos los usuarios del departamento de contabilidad:</span><span class="sxs-lookup"><span data-stu-id="2adfe-199">The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```powershell
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="2adfe-200">Este comando indica a Office 365 PowerShell que:</span><span class="sxs-lookup"><span data-stu-id="2adfe-200">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="2adfe-201">Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-201">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-202">Busque todas las cuentas de usuario que tengan su propiedad Department establecida en "Accounting" ( **Where-Object {$ _. Department-EQ "Accounting"}** ) y enviar la información resultante al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-202">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="2adfe-203">Establezca la ubicación del usuario en Francia ( **set-MsolUser-UsageLocation "fr"** ).</span><span class="sxs-lookup"><span data-stu-id="2adfe-203">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    

## <a name="see-also"></a><span data-ttu-id="2adfe-204">Vea también</span><span class="sxs-lookup"><span data-stu-id="2adfe-204">See also</span></span>

[<span data-ttu-id="2adfe-205">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2adfe-205">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="2adfe-206">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2adfe-206">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="2adfe-207">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="2adfe-207">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
