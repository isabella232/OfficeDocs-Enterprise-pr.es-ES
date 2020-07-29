---
title: Deshabilitar el acceso a los servicios de Microsoft 365 con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/27/2020
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Use PowerShell para deshabilitar el acceso a los servicios de Microsoft 365 para los usuarios.
ms.openlocfilehash: 7820bc44837af07975b2eeaeddf2cf20a9230fae
ms.sourcegitcommit: d9abb99b336170f07b8f3f6d00fac19ad2159d3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/28/2020
ms.locfileid: "46502645"
---
# <a name="disable-access-to-microsoft-365-services-with-powershell"></a><span data-ttu-id="9bcf1-103">Deshabilitar el acceso a los servicios de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bcf1-103">Disable access to Microsoft 365 services with PowerShell</span></span>

<span data-ttu-id="9bcf1-104">*Este artículo afecta tanto a Office 365 Enterprise como a Microsoft 365 Enterprise*</span><span class="sxs-lookup"><span data-stu-id="9bcf1-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="9bcf1-105">Cuando a una cuenta de Microsoft 365 se le asigna una licencia de un plan de licencias, los servicios de Microsoft 365 se ponen a disposición del usuario a partir de dicha licencia.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-105">When a Microsoft 365 account is assigned a license from a licensing plan, Microsoft 365 services are made available to the user from that license.</span></span> <span data-ttu-id="9bcf1-106">Sin embargo, puede controlar los servicios de Microsoft 365 a los que el usuario puede tener acceso.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-106">However, you can control the Microsoft 365 services that the user can access.</span></span> <span data-ttu-id="9bcf1-107">Por ejemplo, aunque la licencia permita el acceso al servicio de SharePoint Online, puede deshabilitar el acceso a ella.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-107">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="9bcf1-108">Puede usar PowerShell para deshabilitar el acceso a cualquier número de servicios para un plan de licencias específico para:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-108">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="9bcf1-109">Una cuenta individual.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-109">An individual account.</span></span>
- <span data-ttu-id="9bcf1-110">Un grupo de cuentas.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-110">A group of accounts.</span></span>
- <span data-ttu-id="9bcf1-111">Todas las cuentas de su organización.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-111">All accounts in your organization.</span></span>

>[!Note]
><span data-ttu-id="9bcf1-112">Hay dependencias de servicio de Microsoft 365 que pueden impedir que se deshabilite un servicio especificado cuando otros servicios dependen de él.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-112">There are Microsoft 365 service dependencies that can prevent you from disabling a specified service when other services depend on it.</span></span>
>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="9bcf1-113">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bcf1-113">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="9bcf1-114">En primer lugar, [Conéctese a su inquilino de Microsoft 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="9bcf1-114">First, [connect to your Microsoft 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="9bcf1-115">A continuación, use este comando para ver los planes de licencias disponibles, también conocidos como Accountskuid:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-115">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```powershell
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

>[!Note]
><span data-ttu-id="9bcf1-116">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-116">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="9bcf1-117">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-117">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>

<span data-ttu-id="9bcf1-118">Para obtener más información, vea [ver licencias y servicios con PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9bcf1-118">For more information, see [View licenses and services with PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="9bcf1-119">Para ver los resultados antes y después de los procedimientos de este tema, vea [View Account License and Service details with PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9bcf1-119">To see the before and after results of the procedures in this topic, see [View account license and service details with PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="9bcf1-120">Hay un script de PowerShell que automatiza los procedimientos descritos en este tema.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-120">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="9bcf1-121">En concreto, el script permite ver y deshabilitar servicios en la organización de Microsoft 365, incluido Sway.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-121">Specifically, the script lets you view and disable services in your Microsoft 365 organization, including Sway.</span></span> <span data-ttu-id="9bcf1-122">Para obtener más información, vea [deshabilitar el acceso a Sway con PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9bcf1-122">For more information, see [Disable access to Sway with PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="9bcf1-123">Deshabilitar los servicios específicos de Microsoft 365 para usuarios específicos para un plan de licencias específico</span><span class="sxs-lookup"><span data-stu-id="9bcf1-123">Disable specific Microsoft 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="9bcf1-124">Para deshabilitar un conjunto específico de servicios de Microsoft 365 para los usuarios de un plan de licencias específico, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-124">To disable a specific set of Microsoft 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
#### <a name="step-1-identify-the-undesirable-services-in-the-licensing-plan-by-using-the-following-syntax"></a><span data-ttu-id="9bcf1-125">Paso 1: identificar los servicios no deseados en el plan de licencias mediante la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-125">Step 1: Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
```

<span data-ttu-id="9bcf1-126">En el ejemplo siguiente se crea un objeto **LicenseOptions** que deshabilita los servicios de Office y SharePoint Online en el plan de licencias denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="9bcf1-126">The following example creates a **LicenseOptions** object that disables the Office and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
```powershell
$LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

#### <a name="step-2-use-the-licenseoptions-object-from-step-1-on-one-or-more-users"></a><span data-ttu-id="9bcf1-127">Paso 2: Use el objeto **LicenseOptions** del paso 1 en uno o más usuarios.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-127">Step 2: Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
<span data-ttu-id="9bcf1-128">Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-128">To create a new account that has the services disabled, use the following syntax:</span></span>
    
```powershell
New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
```

<span data-ttu-id="9bcf1-129">En el ejemplo siguiente se crea una nueva cuenta para Naiara Padilla que asigna la licencia y deshabilita los servicios descritos en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-129">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
```powershell
New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
```

<span data-ttu-id="9bcf1-130">Para obtener más información acerca de la creación de cuentas de usuario en PowerShell para Microsoft 365, consulte [Create User accounts with PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="9bcf1-130">For more information about creating user accounts in PowerShell for Microsoft 365, see [Create user accounts with PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="9bcf1-131">Para deshabilitar los servicios para un usuario con licencia existente, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-131">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
```

<span data-ttu-id="9bcf1-132">En este ejemplo se deshabilitan los servicios para el usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-132">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
```

<span data-ttu-id="9bcf1-133">Para deshabilitar los servicios descritos en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre del plan 365 de Microsoft en la pantalla del cmdlet **Get-MsolAccountSku** (por ejemplo, **litwareinc: ENTERPRISEPACK**) y, a continuación, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-133">To disable the services described in Step 1 for all existing licensed users, specify the name of your Microsoft 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
```powershell
$acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses.AccountSku.SkuPartNumber -contains ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

 <span data-ttu-id="9bcf1-134">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_ , solo se devuelven las primeras 500 cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-134">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>

<span data-ttu-id="9bcf1-135">Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-135">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
<span data-ttu-id="9bcf1-136">**Método 1. Filtrar las cuentas basándose en un atributo de cuenta existente**</span><span class="sxs-lookup"><span data-stu-id="9bcf1-136">**Method 1. Filter the accounts based on an existing account attribute**</span></span> 

<span data-ttu-id="9bcf1-137">Para ello, utilice la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-137">To do this, use the following syntax:</span></span>
    
```powershell
$x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="9bcf1-138">En el siguiente ejemplo se deshabilitan los servicios para usuarios del Departamento de ventas de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-138">The following example disables the services for users in the Sales department in the United States.</span></span>
    
```powershell
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
$USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
```

<span data-ttu-id="9bcf1-139">**Método 2: usar una lista de cuentas específicas**</span><span class="sxs-lookup"><span data-stu-id="9bcf1-139">**Method 2: Use a list of specific accounts**</span></span> 

<span data-ttu-id="9bcf1-140">Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-140">To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="9bcf1-141">Cree un archivo de texto que contenga una cuenta en cada línea como en el ejemplo:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-141">Create a text file that contains one account on each line like this:</span></span>
    
   ```powershell
   akol@contoso.com
   tjohnston@contoso.com
   kakers@contoso.com
   ```

   <span data-ttu-id="9bcf1-142">En este ejemplo, el archivo de texto es C: \\ Mis documentos \\Accounts.txt.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-142">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="9bcf1-143">Ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-143">Run the following command:</span></span>
    
   ```powershell
   Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
   ```

<span data-ttu-id="9bcf1-144">Si desea deshabilitar el acceso a los servicios para varios planes de licencias, repita las instrucciones anteriores para cada plan de licencias y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-144">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="9bcf1-145">Las cuentas de usuario se han asignado al plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-145">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="9bcf1-146">Los servicios que se deshabilitan están disponibles en el plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="9bcf1-146">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="9bcf1-147">Para deshabilitar los servicios de Microsoft 365 para los usuarios mientras los está asignando a un plan de licencias, vea [deshabilitar el acceso a los servicios mientras se asignan licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="9bcf1-147">To disable Microsoft 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>

### <a name="assign-all-services-in-a-licensing-plan-to-a-user-account"></a><span data-ttu-id="9bcf1-148">Asignar todos los servicios de un plan de licencias a una cuenta de usuario</span><span class="sxs-lookup"><span data-stu-id="9bcf1-148">Assign all services in a licensing plan to a user account</span></span>

<span data-ttu-id="9bcf1-149">Para las cuentas de usuario que han deshabilitado los servicios, puede habilitar todos los servicios para un plan de licencias específico con estos comandos:</span><span class="sxs-lookup"><span data-stu-id="9bcf1-149">For user accounts that have had services disabled, you can enable all services for a specific licensing plan with these commands:</span></span>

```powershell
$userUPN="<user account UPN>"
$acctSKU="<AccountSkuId>"
$LO = New-MsolLicenseOptions -AccountSkuId $acctSKU
Set-MsolUserLicense -UserPrincipalName $userUPN -LicenseOptions $LO
```

## <a name="see-also"></a><span data-ttu-id="9bcf1-150">Vea también</span><span class="sxs-lookup"><span data-stu-id="9bcf1-150">See also</span></span>

[<span data-ttu-id="9bcf1-151">Administración de cuentas de usuario, licencias y grupos de Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bcf1-151">Manage Microsoft 365 user accounts, licenses, and groups with PowerShell</span></span>](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[<span data-ttu-id="9bcf1-152">Administrar Microsoft 365 con PowerShell</span><span class="sxs-lookup"><span data-stu-id="9bcf1-152">Manage Microsoft 365 with PowerShell</span></span>](manage-office-365-with-office-365-powershell.md)
  
[<span data-ttu-id="9bcf1-153">Introducción a PowerShell para Microsoft 365</span><span class="sxs-lookup"><span data-stu-id="9bcf1-153">Getting started with PowerShell for Microsoft 365</span></span>](getting-started-with-office-365-powershell.md)
