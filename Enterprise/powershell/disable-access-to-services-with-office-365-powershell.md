---
title: Deshabilitar el acceso a servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/28/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- Ent_Office_Other
- PowerShell
- LIL_Placement
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: Use Office 365 PowerShell para deshabilitar el acceso a los servicios de Office 365 para los usuarios.
ms.openlocfilehash: 0f2c603edd624c9d53a28b37c1c9795bad05ec0f
ms.sourcegitcommit: 29f937b7430c708c9dbec23bdc4089e86c37c225
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/29/2019
ms.locfileid: "31001823"
---
# <a name="disable-access-to-services-with-office-365-powershell"></a><span data-ttu-id="d4a07-103">Deshabilitar el acceso a servicios con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d4a07-103">Disable access to services with Office 365 PowerShell</span></span>

<span data-ttu-id="d4a07-104">**Resumen:** Explica cómo usar Office 365 PowerShell para deshabilitar el acceso a los servicios de Office 365 para los usuarios de la organización.</span><span class="sxs-lookup"><span data-stu-id="d4a07-104">**Summary:** Explains how to use Office 365 PowerShell to disable access to Office 365 services for users in your organization.</span></span>
  
<span data-ttu-id="d4a07-105">Cuando se asigna una licencia a una cuenta de Office 365 a un plan de licencias, los servicios de Office 365 se ponen a disposición del usuario a partir de dicha licencia.</span><span class="sxs-lookup"><span data-stu-id="d4a07-105">When an Office 365 account is assigned a license from a licensing plan, Office 365 services are made available to the user from that license.</span></span> <span data-ttu-id="d4a07-106">Sin embargo, puede controlar los servicios de Office 365 a los que el usuario puede tener acceso.</span><span class="sxs-lookup"><span data-stu-id="d4a07-106">However, you can control the Office 365 services that the user can access.</span></span> <span data-ttu-id="d4a07-107">Por ejemplo, aunque la licencia permita el acceso al servicio de SharePoint Online, puede deshabilitar el acceso a ella.</span><span class="sxs-lookup"><span data-stu-id="d4a07-107">For example, even though the license allows access to the SharePoint Online service, you can disable access to it.</span></span> <span data-ttu-id="d4a07-108">Puede usar PowerShell para deshabilitar el acceso a cualquier número de servicios para un plan de licencias específico para:</span><span class="sxs-lookup"><span data-stu-id="d4a07-108">You can use PowerShell to disable access to any number of services for a specific licensing plan for:</span></span>

- <span data-ttu-id="d4a07-109">Una cuenta individual.</span><span class="sxs-lookup"><span data-stu-id="d4a07-109">An individual account.</span></span>
    
- <span data-ttu-id="d4a07-110">Un grupo de cuentas.</span><span class="sxs-lookup"><span data-stu-id="d4a07-110">A group of accounts.</span></span>
    
- <span data-ttu-id="d4a07-111">Todas las cuentas de su organización.</span><span class="sxs-lookup"><span data-stu-id="d4a07-111">All accounts in your organization.</span></span>

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a><span data-ttu-id="d4a07-112">Use el Módulo Microsoft Azure Active Directory para Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d4a07-112">Use the Microsoft Azure Active Directory Module for Windows PowerShell</span></span>

<span data-ttu-id="d4a07-113">Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="d4a07-113">First, [connect to your Office 365 tenant](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).</span></span>

<span data-ttu-id="d4a07-114">A continuación, use este comando para ver los planes de licencias disponibles, también conocidos como Accountskuid:</span><span class="sxs-lookup"><span data-stu-id="d4a07-114">Next, use this command to view your available licensing plans, also known as AccountSkuIds:</span></span>

```
Get-MsolAccountSku | Select AccountSkuId | Sort AccountSkuId
```

<span data-ttu-id="d4a07-115">Para obtener más información, vea [ver licencias y servicios con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d4a07-115">For more information, see [View licenses and services with Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="d4a07-116">Para ver los resultados antes y después de los procedimientos de este tema, vea [View Account License and Service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d4a07-116">To see the before and after results of the procedures in this topic, see [View account license and service details with Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).</span></span>
    
<span data-ttu-id="d4a07-117">Hay un script de PowerShell que automatiza los procedimientos descritos en este tema.</span><span class="sxs-lookup"><span data-stu-id="d4a07-117">A PowerShell script is available that automates the procedures described in this topic.</span></span> <span data-ttu-id="d4a07-118">En concreto, el script permite ver y deshabilitar servicios en la organización de Office 365, incluido Sway.</span><span class="sxs-lookup"><span data-stu-id="d4a07-118">Specifically, the script lets you view and disable services in your Office 365 organization, including Sway.</span></span> <span data-ttu-id="d4a07-119">Para obtener más información, consulte [Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d4a07-119">For more information, see [Disable access to Sway with Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).</span></span>
    
    
### <a name="disable-specific-office-365-services-for-specific-users-for-a-specific-licensing-plan"></a><span data-ttu-id="d4a07-120">DesHabilitar los servicios específicos de Office 365 para usuarios específicos para un plan de licencias específico</span><span class="sxs-lookup"><span data-stu-id="d4a07-120">Disable specific Office 365 services for specific users for a specific licensing plan</span></span>
  
<span data-ttu-id="d4a07-121">Para deshabilitar un conjunto específico de servicios de Office 365 para los usuarios de un plan de licencias específico, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="d4a07-121">To disable a specific set of Office 365 services for users for a specific licensing plan, perform the following steps:</span></span>
  
1. <span data-ttu-id="d4a07-122">Identifique los servicios no deseados en el plan de licencias mediante la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="d4a07-122">Identify the undesirable services in the licensing plan by using the following syntax:</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

  <span data-ttu-id="d4a07-123">En el ejemplo siguiente se crea un objeto **LicenseOptions** que deshabilita los servicios de Office Online y SharePoint Online en el plan `litwareinc:ENTERPRISEPACK` de licencias denominado (Office 365 Enterprise E3).</span><span class="sxs-lookup"><span data-stu-id="d4a07-123">The following example creates a **LicenseOptions** object that disables the Office Online and SharePoint Online services in the licensing plan named `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).</span></span>
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. <span data-ttu-id="d4a07-124">Use el objeto **LicenseOptions** del paso 1 en uno o más usuarios.</span><span class="sxs-lookup"><span data-stu-id="d4a07-124">Use the **LicenseOptions** object from Step 1 on one or more users.</span></span>
    
  - <span data-ttu-id="d4a07-125">Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="d4a07-125">To create a new account that has the services disabled, use the following syntax:</span></span>
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

  <span data-ttu-id="d4a07-126">En el ejemplo siguiente se crea una nueva cuenta para Naiara Padilla que asigna la licencia y deshabilita los servicios descritos en el paso 1.</span><span class="sxs-lookup"><span data-stu-id="d4a07-126">The following example creates a new account for Allie Bellew that assigns the license and disables the services described in Step 1.</span></span>
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

  <span data-ttu-id="d4a07-127">Para obtener más información acerca de la creación de cuentas de usuario en Office 365 PowerShell, consulte [Create User accounts with office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="d4a07-127">For more information about creating user accounts in Office 365 PowerShell, see [Create user accounts with Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).</span></span>
    
  - <span data-ttu-id="d4a07-128">Para deshabilitar los servicios para un usuario con licencia existente, use la siguiente sintaxis:</span><span class="sxs-lookup"><span data-stu-id="d4a07-128">To disable the services for an existing licensed user, use the following syntax:</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

  <span data-ttu-id="d4a07-129">En este ejemplo se deshabilitan los servicios para el usuario BelindaN@litwareinc.com.</span><span class="sxs-lookup"><span data-stu-id="d4a07-129">This example disables the services for the user BelindaN@litwareinc.com.</span></span>
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - <span data-ttu-id="d4a07-130">Para deshabilitar los servicios descritos en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre de su plan de Office 365 en la pantalla del cmdlet **Get-MsolAccountSku** (por ejemplo, **litwareinc: ENTERPRISEPACK**) y, a continuación, ejecute los comandos siguientes:</span><span class="sxs-lookup"><span data-stu-id="d4a07-130">To disable the services described in Step 1 for all existing licensed users, specify the name of your Office 365 plan from the display of the **Get-MsolAccountSku** cmdlet (such as **litwareinc:ENTERPRISEPACK**), and then run the following commands:</span></span>
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="d4a07-131">Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_ , solo se devuelven las primeras 500 cuentas de usuario.</span><span class="sxs-lookup"><span data-stu-id="d4a07-131">If you use the **Get-MsolUser** cmdlet without using the _All_ parameter, only the first 500 user accounts are returned.</span></span>


  - <span data-ttu-id="d4a07-132">Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:</span><span class="sxs-lookup"><span data-stu-id="d4a07-132">To disable the services for a group of existing users, use either of the following methods to identify the users:</span></span>
    
  - <span data-ttu-id="d4a07-133">**Filtrar las cuentas basándose en un atributo de cuenta existente** Para ello, use la sintaxis siguiente:</span><span class="sxs-lookup"><span data-stu-id="d4a07-133">**Filter the accounts based on an existing account attribute** To do this, use the following syntax:</span></span>
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  <span data-ttu-id="d4a07-134">En el siguiente ejemplo se deshabilitan los servicios para usuarios del Departamento de ventas de Estados Unidos.</span><span class="sxs-lookup"><span data-stu-id="d4a07-134">The following example disables the services for users in the Sales department in the United States.</span></span>
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - <span data-ttu-id="d4a07-135">**Usar una lista de cuentas específicas** Para ello, siga estos pasos:</span><span class="sxs-lookup"><span data-stu-id="d4a07-135">**Use a list of specific accounts** To do this, perform the following steps:</span></span>
    
1. <span data-ttu-id="d4a07-136">Cree un archivo de texto que contenga una cuenta en cada línea como en el ejemplo:</span><span class="sxs-lookup"><span data-stu-id="d4a07-136">Create a text file that contains one account on each line like this:</span></span>
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

  <span data-ttu-id="d4a07-137">En este ejemplo, el archivo de texto es C\\: mis\\documentos accounts. txt.</span><span class="sxs-lookup"><span data-stu-id="d4a07-137">In this example, the text file is C:\\My Documents\\Accounts.txt.</span></span>
    
2. <span data-ttu-id="d4a07-138">Ejecute el siguiente comando:</span><span class="sxs-lookup"><span data-stu-id="d4a07-138">Run the following command:</span></span>
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

<span data-ttu-id="d4a07-139">Si desea deshabilitar el acceso a los servicios para varios planes de licencias, repita las instrucciones anteriores para cada plan de licencias y asegúrese de que:</span><span class="sxs-lookup"><span data-stu-id="d4a07-139">If you want to disable access to services for multiple licensing plans, repeat the above instructions for each licensing plan, ensuring that:</span></span>

- <span data-ttu-id="d4a07-140">Las cuentas de usuario se han asignado al plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="d4a07-140">The user accounts have been assigned the licensing plan.</span></span>
- <span data-ttu-id="d4a07-141">Los servicios que se deshabilitan están disponibles en el plan de licencias.</span><span class="sxs-lookup"><span data-stu-id="d4a07-141">The services to disable are available in the licensing plan.</span></span>

<span data-ttu-id="d4a07-142">Para deshabilitar los servicios de Office 365 para los usuarios mientras los está asignando a un plan de licencias, vea desHabilitar el [acceso a los servicios mientras se asignan licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).</span><span class="sxs-lookup"><span data-stu-id="d4a07-142">To disable Office 365 services for users while you are assigning them to a licensing plan, see [Disable access to services while assigning user licenses](disable-access-to-services-while-assigning-user-licenses.md).</span></span>


## <a name="new-to-office-365"></a><span data-ttu-id="d4a07-143">¿Es la primera vez que usa Office 365?</span><span class="sxs-lookup"><span data-stu-id="d4a07-143">New to Office 365?</span></span>
<span data-ttu-id="d4a07-144"><a name="LinkedIn"> </a></span><span class="sxs-lookup"><span data-stu-id="d4a07-144"></span></span>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a><span data-ttu-id="d4a07-145">Vea también</span><span class="sxs-lookup"><span data-stu-id="d4a07-145">See also</span></span>
<span data-ttu-id="d4a07-146"><a name="SeeAlso"> </a></span><span class="sxs-lookup"><span data-stu-id="d4a07-146"></span></span>

<span data-ttu-id="d4a07-147">Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d4a07-147">See the following additional topics about managing users with Office 365 PowerShell:</span></span>
  
- [<span data-ttu-id="d4a07-148">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d4a07-148">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d4a07-149">Eliminar y restaurar cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d4a07-149">Delete and restore user accounts with Office 365 PowerShell</span></span>](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d4a07-150">Bloquear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d4a07-150">Block user accounts with Office 365 PowerShell</span></span>](block-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d4a07-151">Asignar licencias a cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d4a07-151">Assign licenses to user accounts with Office 365 PowerShell</span></span>](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [<span data-ttu-id="d4a07-152">Crear cuentas de usuario con PowerShell de Office 365</span><span class="sxs-lookup"><span data-stu-id="d4a07-152">Create user accounts with Office 365 PowerShell</span></span>](create-user-accounts-with-office-365-powershell.md)
    
