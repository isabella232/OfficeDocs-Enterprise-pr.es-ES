---
title: Administrar inquilinos de Microsoft 365 con Windows PowerShell para asociados de DAP
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
ms.custom: seo-marvel-apr2020
ms.assetid: f92d5116-5b66-4150-ad20-1452fc3dd712
description: En este artículo, obtenga información sobre cómo usar PowerShell para Microsoft 365 para administrar los arrendamientos de clientes.
ms.openlocfilehash: b1e0459b906bd0a06758147923dff0dcc0af1b3e
ms.sourcegitcommit: 8634215e257ba2d49832a8f5947700fd00f18ece
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/10/2020
ms.locfileid: "46605946"
---
# <a name="manage-microsoft-365-tenants-with-windows-powershell-for-delegated-access-permissions-dap-partners"></a><span data-ttu-id="ddb22-103">Administrar inquilinos de Microsoft 365 con Windows PowerShell para asociados con permiso de acceso delegado (DAP)</span><span class="sxs-lookup"><span data-stu-id="ddb22-103">Manage Microsoft 365 tenants with Windows PowerShell for Delegated Access Permissions (DAP) partners</span></span>

<span data-ttu-id="ddb22-104">*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*</span><span class="sxs-lookup"><span data-stu-id="ddb22-104">*This article applies to both Microsoft 365 Enterprise and Office 365 Enterprise.*</span></span>

<span data-ttu-id="ddb22-p101">Windows PowerShell permite la sindicación y los partners del proveedor de soluciones en la nube (CSP) para administrar fácilmente e informar sobre la configuración de la arrendamiento de clientes que no está disponible en el centro de administración de Microsoft 365. Tenga en cuenta que los permisos de administración en nombre de (AOBO) son necesarios para que la cuenta de administrador de asociados se conecte a sus arrendamientos de clientes.</span><span class="sxs-lookup"><span data-stu-id="ddb22-p101">Windows PowerShell allows Syndication and Cloud Solution Provider (CSP) partners to easily administer and report on customer tenancy settings that are not available in the Microsoft 365 admin center. Note that Administer on Behalf Of (AOBO) permissions are required for the partner administrator account to connect to its customer tenancies.</span></span>
  
<span data-ttu-id="ddb22-107">Los asociados con permiso de acceso delegado (DAP) son asociados de sindicación y proveedor de soluciones en la nube (CSP).</span><span class="sxs-lookup"><span data-stu-id="ddb22-107">Delegated Access Permission (DAP) partners are Syndication and Cloud Solution Providers (CSP) Partners.</span></span> <span data-ttu-id="ddb22-108">Con frecuencia son los proveedores de red o de telecomunicaciones para otras compañías.</span><span class="sxs-lookup"><span data-stu-id="ddb22-108">They are frequently network or telecom providers to other companies.</span></span> <span data-ttu-id="ddb22-109">Incluyen las suscripciones de Microsoft 365 en sus ofertas de servicio para sus clientes.</span><span class="sxs-lookup"><span data-stu-id="ddb22-109">They bundle Microsoft 365 subscriptions into their service offerings to their customers.</span></span> <span data-ttu-id="ddb22-110">Cuando venden una suscripción de 365 de Microsoft, se les conceden automáticamente permisos de administración en nombre de (AOBO) a los arrendamientos de clientes para que puedan administrar y informar sobre los arrendamientos de clientes.</span><span class="sxs-lookup"><span data-stu-id="ddb22-110">When they sell a Microsoft 365 subscription, they are automatically granted Administer On Behalf Of (AOBO) permissions to the customer tenancies so they can administer and report on the customer tenancies.</span></span>
## <a name="what-do-you-need-to-know-before-you-begin"></a><span data-ttu-id="ddb22-111">¿Qué necesita saber antes de comenzar?</span><span class="sxs-lookup"><span data-stu-id="ddb22-111">What do you need to know before you begin?</span></span>

<span data-ttu-id="ddb22-112">Los procedimientos de este tema requieren la conexión para [conectarse a Microsoft 365 con PowerShell](connect-to-office-365-powershell.md).</span><span class="sxs-lookup"><span data-stu-id="ddb22-112">The procedures in this topic require you to connect to [Connect to Microsoft 365 with PowerShell](connect-to-office-365-powershell.md).</span></span>
  
<span data-ttu-id="ddb22-113">Necesita también las credenciales del administrador de inquilinos del asociado.</span><span class="sxs-lookup"><span data-stu-id="ddb22-113">You also need your partner tenant administrator credentials.</span></span>
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="ddb22-114">¿Qué quiere hacer?</span><span class="sxs-lookup"><span data-stu-id="ddb22-114">What do you want to do?</span></span>

### <a name="list-all-tenant-ids"></a><span data-ttu-id="ddb22-115">List all tenant IDs</span><span class="sxs-lookup"><span data-stu-id="ddb22-115">List all tenant IDs</span></span>

> [!NOTE]
> <span data-ttu-id="ddb22-p103">Si tiene más de 500 inquilinos, limite la sintaxis del cmdlet con  _-All_ o _-MaxResultsParameter_. Esto se aplica a otros cmdlets que pueden dar un resultado de gran tamaño, como **Get-MsolUser**.</span><span class="sxs-lookup"><span data-stu-id="ddb22-p103">If you have more than 500 tenants, scope the cmdlet syntax with either  _-All_ or _-MaxResultsParameter_. This applies to other cmdlets that can give a large output, such as **Get-MsolUser**.</span></span>
  
<span data-ttu-id="ddb22-118">Para obtener una lista de todos los identificadores de inquilinos de cliente a los que tiene acceso, ejecute este comando.</span><span class="sxs-lookup"><span data-stu-id="ddb22-118">To list all customer tenant Ids that you have access to, run this command.</span></span>
  
```
Get-MsolPartnerContract -All | Select-Object TenantId
```

<span data-ttu-id="ddb22-119">Se mostrará una lista de todos los inquilinos de clientes por **TenantId**.</span><span class="sxs-lookup"><span data-stu-id="ddb22-119">This will display a listing of all your customer tenants by **TenantId**.</span></span>

>[!Note]
><span data-ttu-id="ddb22-120">PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre.</span><span class="sxs-lookup"><span data-stu-id="ddb22-120">PowerShell Core does not support the Microsoft Azure Active Directory Module for Windows PowerShell module and cmdlets with **Msol** in their name.</span></span> <span data-ttu-id="ddb22-121">Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ddb22-121">To continue using these cmdlets, you must run them from Windows PowerShell.</span></span>
>
  
### <a name="get-a-tenant-id-by-using-the-domain-name"></a><span data-ttu-id="ddb22-122">Obtener un identificador de inquilino a través del nombre de dominio</span><span class="sxs-lookup"><span data-stu-id="ddb22-122">Get a tenant ID by using the domain name</span></span>

<span data-ttu-id="ddb22-p105">Para obtener el **TenantId** para un inquilino de cliente específico por nombre de dominio, ejecute este comando. Reemplace _<domainname.onmicrosoft.com>_ por el nombre de dominio real del inquilino de cliente que desea.</span><span class="sxs-lookup"><span data-stu-id="ddb22-p105">To get the **TenantId** for a specific customer tenant by domain name, run this command. Replace _<domainname.onmicrosoft.com>_ with the actual domain name of the customer tenant that you want.</span></span>
  
```
Get-MsolPartnerContract -DomainName <domainname.onmicrosoft.com> | Select-Object TenantId
```

### <a name="list-all-domains-for-a-tenant"></a><span data-ttu-id="ddb22-125">Hacer una lista de todos los dominios de un inquilino</span><span class="sxs-lookup"><span data-stu-id="ddb22-125">List all domains for a tenant</span></span>

<span data-ttu-id="ddb22-p106">Para obtener todos los dominios de cualquier inquilino de cliente, ejecute este comando. Reemplace el  _<customer TenantId value>_ por el valor real.</span><span class="sxs-lookup"><span data-stu-id="ddb22-p106">To get all domains for any one customer tenant, run this command. Replace  _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolDomain -TenantId <customer TenantId value>
```

<span data-ttu-id="ddb22-128">Si registró dominios adicionales, se devolverán todos los dominios asociados al **TenantId** del cliente.</span><span class="sxs-lookup"><span data-stu-id="ddb22-128">If you have registered additional domains, this will return all domains associated with the customer **TenantId**.</span></span>
  
### <a name="get-a-mapping-of-all-tenants-and-registered-domains"></a><span data-ttu-id="ddb22-129">Obtener una asignación de todos los inquilinos y los dominios registrados</span><span class="sxs-lookup"><span data-stu-id="ddb22-129">Get a mapping of all tenants and registered domains</span></span>

<span data-ttu-id="ddb22-130">Los comandos anteriores de PowerShell para Microsoft 365 muestran cómo recuperar los identificadores de inquilino o los dominios, pero no ambos al mismo tiempo, y sin una asignación clara entre todos ellos.</span><span class="sxs-lookup"><span data-stu-id="ddb22-130">The previous PowerShell for Microsoft 365 commands showed you how to retrieve either tenant IDs or domains but not both at the same time, and with no clear mapping between them all.</span></span> <span data-ttu-id="ddb22-131">Este comando genera una lista de todos los identificadores de inquilinos de clientes y sus dominios.</span><span class="sxs-lookup"><span data-stu-id="ddb22-131">This command generates a listing of all your customer tenant IDs and their domains.</span></span>
  
```
$Tenants = Get-MsolPartnerContract -All; $Tenants | foreach {$Domains = $_.TenantId; Get-MsolDomain -TenantId $Domains | fl @{Label="TenantId";Expression={$Domains}},name}
```

### <a name="get-all-users-for-a-tenant"></a><span data-ttu-id="ddb22-132">Obtener todos los usuarios de un inquilino</span><span class="sxs-lookup"><span data-stu-id="ddb22-132">Get all users for a tenant</span></span>

<span data-ttu-id="ddb22-p108">Se mostrarán los estados **UserPrincipalName**, **DisplayName** y **isLicensed** para todos los usuarios de un inquilino en particular. Reemplace el _<customer TenantId value>_ por el valor real.</span><span class="sxs-lookup"><span data-stu-id="ddb22-p108">This will display the **UserPrincipalName**, the **DisplayName**, and the **isLicensed** status for all users for a particular tenant. Replace _<customer TenantId value>_ with the actual value.</span></span>
  
```
Get-MsolUser -TenantID <customer TenantId value>
```

### <a name="get-all-details-about-a-user"></a><span data-ttu-id="ddb22-135">Obtener todos los detalles acerca de un usuario</span><span class="sxs-lookup"><span data-stu-id="ddb22-135">Get all details about a user</span></span>

<span data-ttu-id="ddb22-p109">Si desea ver todas las propiedades de un usuario concreto, ejecute este comando. Reemplace el  _<customer TenantId value>_ y el _<user principal name value>_ por los valores reales.</span><span class="sxs-lookup"><span data-stu-id="ddb22-p109">If you want to see all the properties of a particular user, run this command. Replace  _<customer TenantId value>_ and _<user principal name value>_ with the actual values.</span></span>
  
```
Get-MsolUser -TenantId <customer TenantId value> -UserPrincipalName <user principal name value>
```

### <a name="add-users-set-options-and-assign-licenses"></a><span data-ttu-id="ddb22-138">Agregar usuarios, establecer opciones y asignar licencias</span><span class="sxs-lookup"><span data-stu-id="ddb22-138">Add users, set options, and assign licenses</span></span>

<span data-ttu-id="ddb22-139">La creación, configuración y concesión de licencias en masa de los usuarios de Microsoft 365 es especialmente eficaz con PowerShell para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ddb22-139">The bulk creation, configuration, and licensing of Microsoft 365 users is particularly efficient by using PowerShell for Microsoft 365.</span></span> <span data-ttu-id="ddb22-140">En este proceso de dos pasos, primero creará entradas para todos los usuarios que desee agregar en un archivo de valores separados por comas (CSV) y, a continuación, importará el archivo con PowerShell para Microsoft 365.</span><span class="sxs-lookup"><span data-stu-id="ddb22-140">In this two-step process, you first create entries for all the users you want to add in a comma-separated value (CSV) file and then import that file by using PowerShell for Microsoft 365.</span></span> 
  
#### <a name="create-a-csv-file"></a><span data-ttu-id="ddb22-141">Crear un archivo CSV</span><span class="sxs-lookup"><span data-stu-id="ddb22-141">Create a CSV file</span></span>

<span data-ttu-id="ddb22-142">Cree un archivo CSV con este formato:</span><span class="sxs-lookup"><span data-stu-id="ddb22-142">Create a CSV file by using this format:</span></span>
  
-  `UserPrincipalName,FirstName,LastName,DisplayName,Password,TenantId,UsageLocation,LicenseAssignment`
    
<span data-ttu-id="ddb22-143">donde:</span><span class="sxs-lookup"><span data-stu-id="ddb22-143">where:</span></span>
  
- <span data-ttu-id="ddb22-p111">**UsageLocation**: El valor de esto es el código de país/región ISO de dos letras del usuario. Los códigos de país/región pueden buscarse en la[Plataforma de exploración en línea ISO](https://go.microsoft.com/fwlink/p/?LinkId=532703). Por ejemplo, el código para Estados Unidos es US y el código para Brasil es BR.</span><span class="sxs-lookup"><span data-stu-id="ddb22-p111">**UsageLocation**: The value for this is the two-letter ISO country/region code of the user. The country/region codes can be looked up at the[ISO Online Browsing Platform](https://go.microsoft.com/fwlink/p/?LinkId=532703). For example, the code for the United States is US, and the code for Brazil is BR.</span></span> 
    
- <span data-ttu-id="ddb22-p112">**LicenseAssignment**: el valor usa este formato: `syndication-account:<PROVISIONING_ID>`. Por ejemplo, si va a asignar licencias de O365_Business_Premium de usuarios de inquilino de cliente, el valor de **LicenseAssignment** se asemejará a: **syndication-account:O365_Business_Premium**. Encontrará los PROVISIONING_IDs en el portal de asociados de redifusión web al que tiene acceso como asociado de redifusión web o CSP.</span><span class="sxs-lookup"><span data-stu-id="ddb22-p112">**LicenseAssignment**: The value for this uses this format: `syndication-account:<PROVISIONING_ID>`. For example, if you are assigning customer tenant users O365_Business_Premium licenses, the **LicenseAssignment** value looks like this: **syndication-account:O365_Business_Premium**. You will find the PROVISIONING_IDs in the Syndication Partner Portal that you have access to as a Syndication or CSP partner.</span></span>
    
#### <a name="import-the-csv-file-and-create-the-users"></a><span data-ttu-id="ddb22-150">Importar el archivo CSV y crear los usuarios</span><span class="sxs-lookup"><span data-stu-id="ddb22-150">Import the CSV file and create the users</span></span>

<span data-ttu-id="ddb22-p113">Una vez que el archivo CSV esté creado, ejecute este comando para crear cuentas de usuario con contraseñas sin fecha de expiración que el usuario debe cambiar en el primer inicio de sesión y que asigna la licencia que el usuario especifique. Asegúrese de reemplazar el nombre de archivo CSV correcto.</span><span class="sxs-lookup"><span data-stu-id="ddb22-p113">After you have your CSV file created, run this command to create user accounts with non-expiring passwords that the user must change at first sign-in and that assigns the license you specify. Be sure to substitute the correct CSV file name.</span></span>
  
```
Import-Csv .\FILENAME.CSV | foreach {New-MsolUser -UserPrincipalName $_.UserPrincipalName -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -Password $_.Password -UsageLocation $_.UsageLocation -LicenseAssignment $_.LicenseAssignment -ForceChangePassword:$true -PasswordNeverExpires:$true -TenantId $_.TenantId}
```

## <a name="see-also"></a><span data-ttu-id="ddb22-153">Consulte también</span><span class="sxs-lookup"><span data-stu-id="ddb22-153">See also</span></span>

#### 

[<span data-ttu-id="ddb22-154">Ayuda para asociados</span><span class="sxs-lookup"><span data-stu-id="ddb22-154">Help for partners</span></span>](https://go.microsoft.com/fwlink/p/?LinkId=533477)

