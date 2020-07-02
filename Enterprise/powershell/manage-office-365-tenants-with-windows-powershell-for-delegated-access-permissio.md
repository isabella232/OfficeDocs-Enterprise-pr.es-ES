---
title: Administrar inquilinos de Microsoft 365 con Windows PowerShell para asociados con permiso de acceso delegado (DAP)
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- M365-subscription-management
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: 'Resumen: use Windows PowerShell para Microsoft 365 para administrar los arrendamientos de clientes.'
ms.openlocfilehash: a57f66ec02f5ba69006c17a9cf734e622017b8fb
ms.sourcegitcommit: 6e608d957082244d1b4ffb47942e5847ec18c0b9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2020
ms.locfileid: "44998236"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="be910-103">Administrar inquilinos de Microsoft 365 con Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="be910-103">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="be910-104">Windows PowerShell permite la sindicación y los partners del proveedor de soluciones en la nube (CSP) para administrar fácilmente e informar sobre la configuración de la arrendamiento de clientes que no está disponible en el centro de administración de Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="be910-104">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center.</span></span> <span data-ttu-id="be910-105">Tenga en cuenta que los permisos Administrar en nombre de (AOBO) son necesarios para que la cuenta de administrador del asociado se conecte a los inquilinos del cliente.</span><span class="sxs-lookup"><span data-stu-id="be910-105">Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="be910-106">Los asociados con permiso de acceso delegado (DAP) son asociados de sindicación y proveedor de soluciones en la nube (CSP).</span><span class="sxs-lookup"><span data-stu-id="be910-106">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="be910-107">Con frecuencia son los proveedores de red o de telecomunicaciones para otras compañías.</span><span class="sxs-lookup"><span data-stu-id="be910-107">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="be910-108">Incluyen las suscripciones de Microsoft 365 en sus ofertas de servicio para sus clientes.</span><span class="sxs-lookup"><span data-stu-id="be910-108">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="be910-109">Cuando venden una suscripción de 365 de Microsoft, se les conceden automáticamente permisos de administración en nombre de (AOBO) a los arrendamientos de clientes para que puedan administrar y informar sobre los arrendamientos de clientes.</span><span class="sxs-lookup"><span data-stu-id="be910-109">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="be910-110">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="be910-110">What do you need to know before you begin?</span></span>

<span data-ttu-id="be910-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span><span class="sxs-lookup"><span data-stu-id="be910-111">The procedures in this topic require you to connect to Windows PowerShell for Office 365.</span></span> <span data-ttu-id="be910-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="be910-112">For instructions, see [Connect to Office 365 PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="be910-113">Necesita también las credenciales del administrador de inquilinos del asociado.</span><span class="sxs-lookup"><span data-stu-id="be910-113">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="be910-114">¿Qué quiere hacer?</span><span class="sxs-lookup"><span data-stu-id="be910-114">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="be910-115">List all tenant IDs</span><span class="sxs-lookup"><span data-stu-id="be910-115">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="be910-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span><span class="sxs-lookup"><span data-stu-id="be910-116">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_.</span></span> <span data-ttu-id="be910-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="be910-117">This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="be910-118">Para obtener una lista de todos los identificadores de inquilinos de cliente a los que tiene acceso, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="be910-118">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="be910-119">Se mostrará una lista de todos los inquilinos de clientes por **TenantId**.</span><span class="sxs-lookup"><span data-stu-id="be910-119">This will display a listing of all your customer tenants by **TenantId**.</span></span>

>[!Note]
><span data-ttu-id="be910-120">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="be910-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="be910-121">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="be910-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="be910-122">Obtener un identificador de inquilino a través del nombre de dominio</span><span class="sxs-lookup"><span data-stu-id="be910-122">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="be910-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span><span class="sxs-lookup"><span data-stu-id="be910-123">To get the **TenantId** for a specific customer tenant by domain name, run this command.</span></span> <span data-ttu-id="be910-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span><span class="sxs-lookup"><span data-stu-id="be910-124">Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="be910-125">Hacer una lista de todos los dominios de un inquilino</span><span class="sxs-lookup"><span data-stu-id="be910-125">List all domains for a tenant</span></span>

<span data-ttu-id="be910-126">To get all domains for any one customer tenant, run this command.</span><span class="sxs-lookup"><span data-stu-id="be910-126">To get all domains for any one customer tenant, run this command.</span></span> <span data-ttu-id="be910-127">Replace  _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="be910-127">Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="be910-128">Si registró dominios adicionales, se devolverán todos los dominios asociados al **TenantId** del cliente.</span><span class="sxs-lookup"><span data-stu-id="be910-128">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="be910-129">Obtener una asignación de todos los inquilinos y los dominios registrados</span><span class="sxs-lookup"><span data-stu-id="be910-129">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="be910-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span><span class="sxs-lookup"><span data-stu-id="be910-130">The previous Windows PowerShell for Office 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span></span> <span data-ttu-id="be910-131">This command generates a listing of all your customer tenant IDs and their domains.</span><span class="sxs-lookup"><span data-stu-id="be910-131">This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="be910-132">Obtener todos los usuarios de un inquilino</span><span class="sxs-lookup"><span data-stu-id="be910-132">Get all users for a tenant</span></span>

<span data-ttu-id="be910-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span><span class="sxs-lookup"><span data-stu-id="be910-133">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant.</span></span> <span data-ttu-id="be910-134">Replace _<customer TenantId value>_ with the actual value.</span><span class="sxs-lookup"><span data-stu-id="be910-134">Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="be910-135">Obtener todos los detalles acerca de un usuario</span><span class="sxs-lookup"><span data-stu-id="be910-135">Get all details about a user</span></span>

<span data-ttu-id="be910-136">If you want to see all the properties of a particular user, run this command.</span><span class="sxs-lookup"><span data-stu-id="be910-136">If you want to see all the properties of a particular user, run this command.</span></span> <span data-ttu-id="be910-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span><span class="sxs-lookup"><span data-stu-id="be910-137">Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="be910-138">Agregar usuarios, establecer opciones y asignar licencias</span><span class="sxs-lookup"><span data-stu-id="be910-138">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="be910-139">La creación, la configuración y la concesión de licencias en masa de los usuarios de Microsoft 365 es particularmente eficiente mediante el uso de Windows PowerShell para Office 365.</span><span class="sxs-lookup"><span data-stu-id="be910-139">The bulk creation, configuration, and licensing of Microsoft 365 users is particularly efficient by using Windows PowerShell for Office 365.</span></span> <span data-ttu-id="be910-140">En este proceso de dos pasos, primero se crean entradas para todos los usuarios que desea agregar a un archivo de valores separados por comas (CSV) y, a continuación, se importa dicho archivo con Windows PowerShell para Office 365.</span><span class="sxs-lookup"><span data-stu-id="be910-140">In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using Windows PowerShell for Office 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="be910-141">Crear un archivo CSV</span><span class="sxs-lookup"><span data-stu-id="be910-141">Create a CSV file</span></span>

<span data-ttu-id="be910-142">Cree un archivo CSV con este formato:</span><span class="sxs-lookup"><span data-stu-id="be910-142">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="be910-143">donde:</span><span class="sxs-lookup"><span data-stu-id="be910-143">where:</span></span>
  
- <span data-ttu-id="be910-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span><span class="sxs-lookup"><span data-stu-id="be910-144">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user.</span></span> <span data-ttu-id="be910-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span><span class="sxs-lookup"><span data-stu-id="be910-145">The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703).</span></span> <span data-ttu-id="be910-146">For example, the code for the United States is US, and the code for Brazil is BR.</span><span class="sxs-lookup"><span data-stu-id="be910-146">For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="be910-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span><span class="sxs-lookup"><span data-stu-id="be910-147">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`.</span></span> <span data-ttu-id="be910-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span><span class="sxs-lookup"><span data-stu-id="be910-148">For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**.</span></span> <span data-ttu-id="be910-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span><span class="sxs-lookup"><span data-stu-id="be910-149">You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="be910-150">Importar el archivo CSV y crear los usuarios</span><span class="sxs-lookup"><span data-stu-id="be910-150">Import the CSV file and create the users</span></span>

<span data-ttu-id="be910-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span><span class="sxs-lookup"><span data-stu-id="be910-151">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify.</span></span> <span data-ttu-id="be910-152">Be sure to substitute the correct CSV file name.</span><span class="sxs-lookup"><span data-stu-id="be910-152">Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="be910-153">Consulte también</span><span class="sxs-lookup"><span data-stu-id="be910-153">See also</span></span>

#### 

[<span data-ttu-id="be910-154">Ayuda para asociados</span><span class="sxs-lookup"><span data-stu-id="be910-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

