---
title: Deshabilitar el acceso a servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/17/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- CSH
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Use Office 365 PowerShell para deshabilitar el acceso a los servicios de Office 365 para los usuarios.
ms.openlocfilehash: eb6099ce5a41d0ea0d09aba0b737be00912ffbdc
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41841577"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="e8311-103">Deshabilitar el acceso a servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="e8311-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="e8311-104">Cuando se asigna una licencia a una cuenta de Office 365 a un plan de licencias, los servicios de Office 365 se ponen a disposición del usuario a partir de dicha licencia.</span><span class="sxs-lookup"><span data-stu-id="e8311-104">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="e8311-105">Sin embargo, puede controlar los servicios de Office 365 a los que el usuario puede tener acceso.</span><span class="sxs-lookup"><span data-stu-id="e8311-105">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="e8311-106">Por ejemplo, aunque la licencia permita el acceso al servicio de SharePoint Online, puede deshabilitar el acceso a ella.</span><span class="sxs-lookup"><span data-stu-id="e8311-106">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="e8311-107">Puede usar PowerShell para deshabilitar el acceso a cualquier número de servicios para un plan de licencias específico para:</span><span class="sxs-lookup"><span data-stu-id="e8311-107">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="e8311-108">Una cuenta individual.</span><span class="sxs-lookup"><span data-stu-id="e8311-108">An individual account.</span></span>
- <span data-ttu-id="e8311-109">Un grupo de cuentas.</span><span class="sxs-lookup"><span data-stu-id="e8311-109">A group of accounts.</span></span>
- <span data-ttu-id="e8311-110">Todas las cuentas de su organización.</span><span class="sxs-lookup"><span data-stu-id="e8311-110">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="e8311-111">Hay dependencias de servicio de Office 365 que pueden impedir que se deshabilite un servicio especificado cuando otros servicios dependen de él.</span><span class="sxs-lookup"><span data-stu-id="e8311-111">There are Office 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="e8311-112">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8311-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="e8311-113">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="e8311-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="e8311-114">A continuación, use este comando para ver los planes de licencias disponibles, también conocidos como Accountskuid:</span><span class="sxs-lookup"><span data-stu-id="e8311-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="e8311-115">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="e8311-115">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="e8311-116">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e8311-116">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="e8311-117">Para obtener más información, vea [ver licencias y servicios con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e8311-117">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="e8311-118">Para ver los resultados antes y después de los procedimientos de este tema, vea [View Account License and Service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e8311-118">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="e8311-119">Hay un script de PowerShell que automatiza los procedimientos descritos en este tema.</span><span class="sxs-lookup"><span data-stu-id="e8311-119">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="e8311-120">En concreto, el script permite ver y deshabilitar servicios en la organización de Office 365, incluido Sway.</span><span class="sxs-lookup"><span data-stu-id="e8311-120">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="e8311-121">Para obtener más información, consulte [Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e8311-121">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="e8311-122">Deshabilitar los servicios específicos de Office 365 para usuarios específicos para un plan de licencias específico</span><span class="sxs-lookup"><span data-stu-id="e8311-122">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="e8311-123">Para deshabilitar un conjunto específico de servicios de Office 365 para los usuarios de un plan de licencias específico, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="e8311-123">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="e8311-124">Paso 1: identificar los servicios no deseados en el plan de licencias mediante la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="e8311-124">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="e8311-125">En el ejemplo siguiente se crea un objeto **LicenseOptions** que deshabilita los servicios de Office y SharePoint Online en el plan `litwareinc:ENTERPRISEPACK` de licencias denominado (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="e8311-125">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="e8311-126">Paso 2: Use el objeto **LicenseOptions** del paso 1 en uno o más usuarios.</span><span class="sxs-lookup"><span data-stu-id="e8311-126">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="e8311-127">Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="e8311-127">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="e8311-128">En el ejemplo siguiente se crea una nueva cuenta para Naiara Padilla que asigna la licencia y deshabilita los servicios descritos en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="e8311-128">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="e8311-129">Para obtener más información acerca de la creación de cuentas de usuario en Office 365 PowerShell, consulte [Create User accounts with office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="e8311-129">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="e8311-130">Para deshabilitar los servicios para un usuario con licencia existente, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="e8311-130">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="e8311-131">En este ejemplo se deshabilitan los servicios para el usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="e8311-131">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="e8311-132">Para deshabilitar los servicios descritos en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre de su plan de Office 365 en la pantalla del cmdlet **Get-MsolAccountSku** (por ejemplo, **litwareinc: ENTERPRISEPACK**) y, a continuación, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="e8311-132">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="e8311-133">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_ , solo se devuelven las primeras 500 cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="e8311-133">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="e8311-134">Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:</span><span class="sxs-lookup"><span data-stu-id="e8311-134">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="e8311-135">**Método 1. Filtrar las cuentas basándose en un atributo de cuenta existente**</span><span class="sxs-lookup"><span data-stu-id="e8311-135">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="e8311-136">Para ello, utilice la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="e8311-136">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="e8311-137">En el siguiente ejemplo se deshabilitan los servicios para usuarios del Departamento de ventas de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="e8311-137">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="e8311-138">**Método 2: usar una lista de cuentas específicas**</span><span class="sxs-lookup"><span data-stu-id="e8311-138">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="e8311-139">Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="e8311-139">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="e8311-140">Cree un archivo de texto que contenga una cuenta en cada línea como en el ejemplo:</span><span class="sxs-lookup"><span data-stu-id="e8311-140">Create a text file that contains one account on each line like this:</span></span>
    
  ```powershell
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="e8311-141">En este ejemplo, el archivo de texto es C\\: mis\\documentos accounts. txt.</span><span class="sxs-lookup"><span data-stu-id="e8311-141">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="e8311-142">Ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="e8311-142">Run the following command:</span></span>
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="e8311-143">Si desea deshabilitar el acceso a los servicios para varios planes de licencias, repita las instrucciones anteriores para cada plan de licencias y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="e8311-143">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="e8311-144">Las cuentas de usuario se han asignado al plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="e8311-144">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="e8311-145">Los servicios que se deshabilitan están disponibles en el plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="e8311-145">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="e8311-146">Para deshabilitar los servicios de Office 365 para los usuarios mientras los está asignando a un plan de licencias, vea [deshabilitar el acceso a los servicios mientras se asignan licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="e8311-146">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="e8311-147">Vea también</span><span class="sxs-lookup"><span data-stu-id="e8311-147">See also</span></span>

[<span data-ttu-id="e8311-148">Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e8311-148">Manage user accounts, licenses, and groups with Office 365 PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="e8311-149">Administrar Office 365 con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="e8311-149">Manage Office 365 with Office 365 PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="e8311-150">Introducción a PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="e8311-150">Getting started with Office 365 PowerShell</span></span>](getting-started-with-office-365-powershell.md)
