---
title: Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: O365ITProTrain, Ent_Office_Other, PowerShell
ms.assetid: 30813f8d-b08d-444b-98c1-53df7c29b4d7
description: 'Resumen: Uso Office 365 PowerShell para configurar las propiedades de la persona o a varias cuentas de usuario en los inquilinos de Office 365.'
ms.openlocfilehash: 65857511886534e18ba3e67b79ab4d74a0119568
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="configure-user-account-properties-with-office-365-powershell"></a><span data-ttu-id="d1016-103">Configurar las propiedades de la cuenta de usuario con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1016-103">Configure user account properties with Office 365 PowerShell</span></span>

 <span data-ttu-id="d1016-104">**Resumen:** Utilice Office 365 PowerShell para configurar las propiedades de la persona o a varias cuentas de usuario en los inquilinos de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d1016-104">**Summary:** Use Office 365 PowerShell to configure properties of individual or multiple user accounts in your Office 365 tenant.</span></span>
  
<span data-ttu-id="d1016-105">Aunque puede utilizar el centro de administración de Office 365 para configurar las propiedades de las cuentas de usuario de los inquilinos de Office 365, también puede utilizar Office 365 PowerShell y hacer algunas cosas que no puede el centro de administración de Office 365.</span><span class="sxs-lookup"><span data-stu-id="d1016-105">Although you can use the Office 365 Admin center to configure properties for the user accounts of your Office 365 tenant, you can also use Office 365 PowerShell and do some things that the Office 365 Admin center cannot.</span></span>
  
## <a name="before-you-begin"></a><span data-ttu-id="d1016-106">Antes de empezar</span><span class="sxs-lookup"><span data-stu-id="d1016-106">Before you begin</span></span>

<span data-ttu-id="d1016-p101">Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d1016-p101">The procedures in this topic require you to connect to Office 365 PowerShell. For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
## <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d1016-109">Cambiar las propiedades de una cuenta de usuario específica</span><span class="sxs-lookup"><span data-stu-id="d1016-109">Change properties for a specific user account</span></span>

<span data-ttu-id="d1016-p102">Para configurar las propiedades de una cuenta de usuario específica, use el cmdlet [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) y especificar las propiedades para establecer o cambiar. Este comando de ejemplo cambia la ubicación de uso de Belinda Newman en Francia:</span><span class="sxs-lookup"><span data-stu-id="d1016-p102">To configure properties for a specific user account, you use the [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) cmdlet and specify the properties to set or change. This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="d1016-p103">Identificar la cuenta con el parámetro **- UserPrincipalName** y establece o cambia las propiedades específicas con parámetros adicionales. Presentamos una lista de los parámetros más comunes.</span><span class="sxs-lookup"><span data-stu-id="d1016-p103">You identify the account with the **-UserPrincipalName** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d1016-114">-Ciudad "\<nombre de la ciudad >"</span><span class="sxs-lookup"><span data-stu-id="d1016-114">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d1016-115">-País "\<nombre de país >"</span><span class="sxs-lookup"><span data-stu-id="d1016-115">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d1016-116">-Departamento "\<nombre de departamento >"</span><span class="sxs-lookup"><span data-stu-id="d1016-116">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d1016-117">DisplayName: "\<nombre completo del usuario >"</span><span class="sxs-lookup"><span data-stu-id="d1016-117">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d1016-118">-Fax "\<número de fax >"</span><span class="sxs-lookup"><span data-stu-id="d1016-118">-Fax "\<fax number>"</span></span>
    
- <span data-ttu-id="d1016-119">-FirstName "\<nombre usuario >"</span><span class="sxs-lookup"><span data-stu-id="d1016-119">-FirstName "\<user first name>"</span></span>
    
- <span data-ttu-id="d1016-120">-Apellido "\<último nombre de usuario >"</span><span class="sxs-lookup"><span data-stu-id="d1016-120">-LastName "\<user last name>"</span></span>
    
- <span data-ttu-id="d1016-121">-Teléfono móvil "\<número de teléfono móvil >"</span><span class="sxs-lookup"><span data-stu-id="d1016-121">-MobilePhone "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d1016-122">-Office "\<ubicación de la oficina >"</span><span class="sxs-lookup"><span data-stu-id="d1016-122">-Office "\<office location>"</span></span>
    
- <span data-ttu-id="d1016-123">-El número de teléfono "\<número de teléfono de oficina >"</span><span class="sxs-lookup"><span data-stu-id="d1016-123">-PhoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d1016-124">-PostalCode "\<código postal >"</span><span class="sxs-lookup"><span data-stu-id="d1016-124">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d1016-125">-PreferredLanguage "\<idioma >"</span><span class="sxs-lookup"><span data-stu-id="d1016-125">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d1016-126">-Estado "\<nombre de estado >"</span><span class="sxs-lookup"><span data-stu-id="d1016-126">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d1016-127">-StreetAddress "\<dirección >"</span><span class="sxs-lookup"><span data-stu-id="d1016-127">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d1016-128">-Título "\<nombre del título >"</span><span class="sxs-lookup"><span data-stu-id="d1016-128">-Title "\<title name>"</span></span>
    
- <span data-ttu-id="d1016-129">-UsageLocation "\<código de país o región de 2 caracteres >"</span><span class="sxs-lookup"><span data-stu-id="d1016-129">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d1016-130">Esto es el país de dos letras ISO 3166-1 alpha-2 (A2) o el código de región.</span><span class="sxs-lookup"><span data-stu-id="d1016-130">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d1016-131">Consulte [MsolUser del conjunto](https://msdn.microsoft.com/library/azure/dn194136.aspx) de parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="d1016-131">See [Set-MsolUser](https://msdn.microsoft.com/library/azure/dn194136.aspx) for additional parameters.</span></span>
  
<span data-ttu-id="d1016-132">Para ver los nombres principales de usuario de todos los usuarios, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="d1016-132">To see the User Principal Names of all your users, run the following command.</span></span>
  
```
Get-MSolUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="d1016-133">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d1016-133">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1016-134">Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-134">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-135">Ordenar alfabéticamente la lista de nombres principales de usuario ( **UserPrincipalName de Sort-Object** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-135">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-136">Mostrar sólo la propiedad de nombre Principal de usuario para cada cuenta ( **UserPrincipalName de Select-Object** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-136">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
    
- <span data-ttu-id="d1016-137">Muestra una pantalla a la vez ( **más** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-137">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d1016-p104">Este comando mostrará todas las cuentas. Si desea mostrar el nombre Principal de usuario de una cuenta basada en su presentación name (nombre y apellido), rellene la siguiente variable de **$userName** (quitando el \< y > caracteres), y, a continuación, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="d1016-p104">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d1016-140">Este ejemplo muestra el nombre Principal de usuario para el usuario llamado Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="d1016-140">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d1016-p105">Mediante el uso de una variable de **$upn** , puede realizar cambios en cuentas individuales basadas en su nombre para mostrar. Aquí es un ejemplo de establecer ubicación de uso de Belinda Newman en Francia, pero especifica su nombre para mostrar en lugar de su nombre Principal de usuario:</span><span class="sxs-lookup"><span data-stu-id="d1016-p105">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="<Display name>"
$upn=(Get-MsolUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-MsolUser -UserPrincipalName $upn -UsageLocation "FR"
```

## <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d1016-143">Cambiar las propiedades de todas las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d1016-143">Change properties for all user accounts</span></span>

<span data-ttu-id="d1016-p106">Para cambiar las propiedades de todos los usuarios, puede utilizar la combinación de los cmdlets **Get-MsolUser** y **MsolUser del conjunto** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios a Francia:</span><span class="sxs-lookup"><span data-stu-id="d1016-p106">To change properties for all users, you can use the combination of the **Get-MsolUser** and **Set-MsolUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-MsolUser | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d1016-146">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d1016-146">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1016-147">Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-147">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-148">Establecer la ubicación del usuario en Francia ( **"FR" Set-MsolUser-UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-148">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
## <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d1016-149">Cambiar las propiedades de un conjunto específico de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d1016-149">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d1016-p107">Para cambiar las propiedades de un conjunto específico de la cuenta de usuario, puede utilizar la combinación de los cmdlets **Get-MsolUser**, **Where-Object**y **MsolUser del conjunto** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios del departamento de contabilidad a Francia:</span><span class="sxs-lookup"><span data-stu-id="d1016-p107">To change properties for a specific set of user account, you can use the combination of the **Get-MsolUser**, **Where-Object**, and **Set-MsolUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-MsolUser | Where-Object {$_.Department -eq "Accounting"} | Set-MsolUser -UsageLocation "FR"
```

<span data-ttu-id="d1016-152">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d1016-152">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1016-153">Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-153">Get all of the information on the user accounts ( **Get-MsolUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-154">Buscar todas las cuentas de usuario que tengan su propiedad departamento sea "Contabilidad" ( **Where-Object {$_. Departamento - eq "Contabilidad"}** ) y enviar la información resultante con el siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-154">Find all of the user accounts that have their Department property set to "Accounting" ( **Where-Object {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-155">Establecer la ubicación del usuario en Francia ( **"FR" Set-MsolUser-UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-155">Set the user location to France ( **Set-MsolUser -UsageLocation "FR"** ).</span></span>
    
- <span data-ttu-id="d1016-156">Muestra una pantalla a la vez ( **más** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-156">Display them one screen at a time ( **More** ).</span></span>
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-configure-user-account-properties"></a><span data-ttu-id="d1016-157">Utilice el módulo de Active Directory V2 PowerShell de Azure para configurar las propiedades de la cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="d1016-157">Use the Azure Active Directory V2 PowerShell module to configure user account properties</span></span>

<span data-ttu-id="d1016-p108">Para configurar las propiedades de cuentas de usuario con el módulo de Active Directory V2 PowerShell de Azure, use el cmdlet [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) y especificar las propiedades para establecer o cambiar. Pero en primer lugar, debe conectarse a su suscripción. Para las instrucciones, vea [Conectar con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).</span><span class="sxs-lookup"><span data-stu-id="d1016-p108">To configure properties for user accounts with the Azure Active Directory V2 PowerShell module, you use the [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) cmdlet and specify the properties to set or change. But first, you must connect to your subscription. For the instructions, see [Connect with the Azure Active Directory V2 PowerShell module](https://go.microsoft.com/fwlink/?linkid=842218).</span></span>
  
### <a name="change-properties-for-a-specific-user-account"></a><span data-ttu-id="d1016-161">Cambiar las propiedades de una cuenta de usuario específica</span><span class="sxs-lookup"><span data-stu-id="d1016-161">Change properties for a specific user account</span></span>

<span data-ttu-id="d1016-162">Este comando de ejemplo cambia la ubicación de uso de Belinda Newman en Francia:</span><span class="sxs-lookup"><span data-stu-id="d1016-162">This example command changes Belinda Newman's usage location to France:</span></span>
  
```
Set-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" -UsageLocation "FR"
```

<span data-ttu-id="d1016-p109">Identificar la cuenta con el parámetro **- ObjectID** y establece o cambia las propiedades específicas con parámetros adicionales. Presentamos una lista de los parámetros más comunes.</span><span class="sxs-lookup"><span data-stu-id="d1016-p109">You identify the account with the **-ObjectID** parameter and set or change specific properties with additional parameters. Here is a list of the most common parameters.</span></span>
  
- <span data-ttu-id="d1016-165">-Departamento "\<nombre de departamento >"</span><span class="sxs-lookup"><span data-stu-id="d1016-165">-Department "\<department name>"</span></span>
    
- <span data-ttu-id="d1016-166">DisplayName: "\<nombre completo del usuario >"</span><span class="sxs-lookup"><span data-stu-id="d1016-166">-DisplayName "\<full user name>"</span></span>
    
- <span data-ttu-id="d1016-167">-FacsimilieTelephoneNumber "\<número de fax >"</span><span class="sxs-lookup"><span data-stu-id="d1016-167">-FacsimilieTelephoneNumber "\<fax number>"</span></span>
    
- <span data-ttu-id="d1016-168">-GivenName "\<nombre usuario >"</span><span class="sxs-lookup"><span data-stu-id="d1016-168">-GivenName "\<user first name>"</span></span>
    
- <span data-ttu-id="d1016-169">-El apellido "\<último nombre de usuario >"</span><span class="sxs-lookup"><span data-stu-id="d1016-169">-Surname "\<user last name>"</span></span>
    
- <span data-ttu-id="d1016-170">-Móvil "\<número de teléfono móvil >"</span><span class="sxs-lookup"><span data-stu-id="d1016-170">-Mobile "\<mobile phone number>"</span></span>
    
- <span data-ttu-id="d1016-171">-JobTitle "\<puesto >"</span><span class="sxs-lookup"><span data-stu-id="d1016-171">-JobTitle "\<job title>"</span></span>
    
- <span data-ttu-id="d1016-172">-PreferredLanguage "\<idioma >"</span><span class="sxs-lookup"><span data-stu-id="d1016-172">-PreferredLanguage "\<language>"</span></span>
    
- <span data-ttu-id="d1016-173">-StreetAddress "\<dirección >"</span><span class="sxs-lookup"><span data-stu-id="d1016-173">-StreetAddress "\<street address>"</span></span>
    
- <span data-ttu-id="d1016-174">-Ciudad "\<nombre de la ciudad >"</span><span class="sxs-lookup"><span data-stu-id="d1016-174">-City "\<city name>"</span></span>
    
- <span data-ttu-id="d1016-175">-Estado "\<nombre de estado >"</span><span class="sxs-lookup"><span data-stu-id="d1016-175">-State "\<state name>"</span></span>
    
- <span data-ttu-id="d1016-176">-PostalCode "\<código postal >"</span><span class="sxs-lookup"><span data-stu-id="d1016-176">-PostalCode "\<postal code>"</span></span>
    
- <span data-ttu-id="d1016-177">-País "\<nombre de país >"</span><span class="sxs-lookup"><span data-stu-id="d1016-177">-Country "\<country name>"</span></span>
    
- <span data-ttu-id="d1016-178">-TelephoneNumber "\<número de teléfono de oficina >"</span><span class="sxs-lookup"><span data-stu-id="d1016-178">-TelephoneNumber "\<office phone number>"</span></span>
    
- <span data-ttu-id="d1016-179">-UsageLocation "\<código de país o región de 2 caracteres >"</span><span class="sxs-lookup"><span data-stu-id="d1016-179">-UsageLocation "\<2-character country or region code>"</span></span>
    
    <span data-ttu-id="d1016-180">Esto es el país de dos letras ISO 3166-1 alpha-2 (A2) o el código de región.</span><span class="sxs-lookup"><span data-stu-id="d1016-180">This is the ISO 3166-1 alpha-2 (A2) two-letter country or region code.</span></span>
    
<span data-ttu-id="d1016-181">Consulte [AzureADUser del conjunto](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) de parámetros adicionales.</span><span class="sxs-lookup"><span data-stu-id="d1016-181">See [Set-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/set-azureaduser?view=azureadps-2.0) for additional parameters.</span></span>
  
<span data-ttu-id="d1016-182">Para mostrar el nombre Principal de usuario para las cuentas de usuario, ejecute el siguiente comando.</span><span class="sxs-lookup"><span data-stu-id="d1016-182">To display the User Principal Name for your user accounts, run the following command.</span></span>
  
```
Get-AzureADUser | Sort-Object UserPrincipalName | Select-Object UserPrincipalName | More
```

<span data-ttu-id="d1016-183">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d1016-183">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1016-184">Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-184">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-185">Ordenar alfabéticamente la lista de nombres principales de usuario ( **UserPrincipalName de Sort-Object** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-185">Sort the list of User Principal Names alphabetically ( **Sort-Object UserPrincipalName** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-186">Mostrar sólo la propiedad de nombre Principal de usuario para cada cuenta ( **UserPrincipalName de Select-Object** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-186">Display just the User Principal Name property for each account ( **Select-Object UserPrincipalName** ).</span></span>
- <span data-ttu-id="d1016-187">Muestra una pantalla a la vez ( **más** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-187">Display them one screen at a time ( **More** ).</span></span>
    
<span data-ttu-id="d1016-p110">Este comando mostrará todas las cuentas. Si desea mostrar el nombre Principal de usuario de una cuenta basada en su presentación name (nombre y apellido), rellene la siguiente variable de **$userName** (quitando el \< y > caracteres), y, a continuación, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="d1016-p110">This command will list all of your accounts. If you want to display the User Principal Name for an account based on its display name (first and last name), fill in the **$userName** variable below (removing the \< and > characters), and then run the following commands:</span></span>
  
```
$userName="<Display name>"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d1016-190">Este ejemplo muestra el nombre Principal de usuario para el usuario llamado Caleb Sills.</span><span class="sxs-lookup"><span data-stu-id="d1016-190">This example displays the User Principal Name for the user named Caleb Sills.</span></span>
  
```
$userName="Caleb Sills"
Write-Host (Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
```

<span data-ttu-id="d1016-p111">Mediante el uso de una variable de **$upn** , puede realizar cambios en cuentas individuales basadas en su nombre para mostrar. Aquí es un ejemplo de establecer ubicación de uso de Belinda Newman en Francia, pero especifica su nombre para mostrar en lugar de su nombre Principal de usuario:</span><span class="sxs-lookup"><span data-stu-id="d1016-p111">By using a **$upn** variable, you can make changes to individual accounts based on their display name. Here is an example of setting Belinda Newman's usage location to France, but specifying her display name rather than her User Principal Name:</span></span>
  
```
$userName="Belinda Newman"
$upn=(Get-AzureADUser | where {$_.DisplayName -eq $userName}).UserPrincipalName
Set-AzureADUser -ObjectID $upn -UsageLocation "FR"
```

### <a name="change-properties-for-all-user-accounts"></a><span data-ttu-id="d1016-193">Cambiar las propiedades de todas las cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d1016-193">Change properties for all user accounts</span></span>

<span data-ttu-id="d1016-p112">Para cambiar las propiedades de todos los usuarios, puede utilizar la combinación de los cmdlets **Get-AzureADUser** y **AzureADUser del conjunto** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios a Francia:</span><span class="sxs-lookup"><span data-stu-id="d1016-p112">To change properties for all users, you can use the combination of the **Get-AzureADUser** and **Set-AzureADUser** cmdlets. The following example changes the usage location for all users to France:</span></span>
  
```
Get-AzureADUser | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d1016-196">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d1016-196">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1016-197">Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-197">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-198">Establecer la ubicación del usuario en Francia ( **"FR" Set-AzureADUser-UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-198">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
### <a name="change-properties-for-a-specific-set-of-user-accounts"></a><span data-ttu-id="d1016-199">Cambiar las propiedades de un conjunto específico de cuentas de usuario</span><span class="sxs-lookup"><span data-stu-id="d1016-199">Change properties for a specific set of user accounts</span></span>

<span data-ttu-id="d1016-p113">Para cambiar las propiedades de un conjunto específico de la cuenta de usuario, puede utilizar la combinación de los cmdlets **Get-AzureADUser**, **donde**y **AzureADUser del conjunto** . En el ejemplo siguiente se cambia la ubicación de uso para todos los usuarios del departamento de contabilidad a Francia:</span><span class="sxs-lookup"><span data-stu-id="d1016-p113">To change properties for a specific set of user account, you can use the combination of the **Get-AzureADUser**, **Where**, and **Set-AzureADUser** cmdlets. The following example changes the usage location for all the users in the Accounting department to France:</span></span>
  
```
Get-AzureADUser | Where-Object {$_.Department -eq "Accounting"} | Set-AzureADUser -UsageLocation "FR"
```

<span data-ttu-id="d1016-202">Este comando indica a Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d1016-202">This command instructs Office 365 PowerShell to:</span></span>
  
- <span data-ttu-id="d1016-203">Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-203">Get all of the information on the user accounts ( **Get-AzureADUser** ) and send it to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-204">Buscar todas las cuentas de usuario que tienen su propiedad departamento a "Accounting" ( **donde {$_. Departamento - eq "Contabilidad"}** ) y enviar la información resultante con el siguiente comando ( **|** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-204">Find all of the user accounts that have their Department property set to "Accounting" ( **Where {$_.Department -eq "Accounting"}** ) and send the resulting information to the next command ( **|** ).</span></span>
    
- <span data-ttu-id="d1016-205">Establecer la ubicación del usuario en Francia ( **"FR" Set-AzureADUser-UsageLocation** ).</span><span class="sxs-lookup"><span data-stu-id="d1016-205">Set the user location to France ( **Set-AzureADUser -UsageLocation "FR"** ).</span></span>
    
## <a name="see-also"></a><span data-ttu-id="d1016-206">Consulte también</span><span class="sxs-lookup"><span data-stu-id="d1016-206">See also</span></span>

#### 

[<span data-ttu-id="d1016-207">Administrar licencias y cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d1016-207">Manage user accounts and licenses with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="d1016-208">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d1016-208">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="d1016-209">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d1016-209">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)

