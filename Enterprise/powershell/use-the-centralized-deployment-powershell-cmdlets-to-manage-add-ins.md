---
title: Usar los cmdlets de PowerShell de Implementación centralizada para administrar complementos
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MBS150
- BCS160
f1.keywords:
- NOCSH
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Use los cmdlets de PowerShell de implementación centralizada como ayuda para implementar y administrar complementos de Office para su organización de Office 365.
ms.openlocfilehash: 586b66ac3632a5d86a63014a50f3c605b1c005e7
ms.sourcegitcommit: 99411927abdb40c2e82d2279489ba60545989bb1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2020
ms.locfileid: "41844161"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="dde17-103">Usar los cmdlets de PowerShell de Implementación centralizada para administrar complementos</span><span class="sxs-lookup"><span data-stu-id="dde17-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="dde17-104">Como administrador de Office 365, puede implementar complementos de Office para los usuarios a través de la característica de implementación centralizada (vea [Manage Deployment of office 365 Add-Ins in the admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span><span class="sxs-lookup"><span data-stu-id="dde17-104">As an Office 365 admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Manage deployment of Office 365 add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)).</span></span> <span data-ttu-id="dde17-105">Además de implementar complementos de Office a través del centro de administración, también puede usar PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dde17-105">In addition to deploying Office add-ins via the admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="dde17-106">[Descargue](https://go.microsoft.com/fwlink/p/?linkid=850850) los cmdlets de PowerShell de implementación centralizada desde el centro de descarga de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="dde17-106">[Download](https://go.microsoft.com/fwlink/p/?linkid=850850) the Centralized Deployment PowerShell cmdlets from the Microsoft Download Center.</span></span> 
  
## <a name="what-do-you-want-to-do"></a><span data-ttu-id="dde17-107">¿Qué quiere hacer?</span><span class="sxs-lookup"><span data-stu-id="dde17-107">What do you want to do?</span></span>

[<span data-ttu-id="dde17-108">Conectarse con las credenciales de administrador</span><span class="sxs-lookup"><span data-stu-id="dde17-108">Connect using your admin credentials</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[<span data-ttu-id="dde17-109">Cargar un manifiesto de complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-109">Upload an add-in manifest</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[<span data-ttu-id="dde17-110">Cargar un complemento de la tienda Office</span><span class="sxs-lookup"><span data-stu-id="dde17-110">Upload an add-in from the Office Store</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[<span data-ttu-id="dde17-111">Obtener detalles de un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-111">Get details of an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[<span data-ttu-id="dde17-112">Activar o desactivar un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-112">Turn on or turn off an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[<span data-ttu-id="dde17-113">Agregar o quitar usuarios de un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-113">Add or remove users from an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[<span data-ttu-id="dde17-114">Actualizar un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-114">Update an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[<span data-ttu-id="dde17-115">Eliminar un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-115">Delete an add-in</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[<span data-ttu-id="dde17-116">Obtener ayuda detallada para cada cmdlet</span><span class="sxs-lookup"><span data-stu-id="dde17-116">Get detailed help for each cmdlet</span></span>](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="dde17-117">Conectarse con las credenciales de administrador</span><span class="sxs-lookup"><span data-stu-id="dde17-117">Connect using your admin credentials</span></span>
<span data-ttu-id="dde17-118"><a name="BKMK_Connect"> </a></span><span class="sxs-lookup"><span data-stu-id="dde17-118"><a name="BKMK_Connect"> </a></span></span>

<span data-ttu-id="dde17-119">Para poder usar los cmdlets de implementación centralizada, debe iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="dde17-119">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="dde17-120">Inicie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dde17-120">Start PowerShell.</span></span>
    
2. <span data-ttu-id="dde17-121">Conéctese a PowerShell con las credenciales de administrador de la compañía.</span><span class="sxs-lookup"><span data-stu-id="dde17-121">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="dde17-122">Ejecute el siguiente cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dde17-122">Run the following cmdlet.</span></span>
    
  ```
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="dde17-123">En la página **escribir credenciales** , escriba sus credenciales de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="dde17-123">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="dde17-124">Como alternativa, puede escribir sus credenciales directamente en el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dde17-124">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="dde17-125">Ejecute el siguiente cmdlet especificando las credenciales de administrador de la compañía como un objeto PSCredential.</span><span class="sxs-lookup"><span data-stu-id="dde17-125">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="dde17-126">Para obtener más información sobre el uso de PowerShell, vea [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="dde17-126">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="dde17-127">Cargar un manifiesto de complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-127">Upload an add-in manifest</span></span>
<span data-ttu-id="dde17-128"><a name="BKMK_UploadManifest"> </a></span><span class="sxs-lookup"><span data-stu-id="dde17-128"><a name="BKMK_UploadManifest"> </a></span></span>

<span data-ttu-id="dde17-129">Ejecute el cmdlet New-OrganizationAdd-in para cargar un manifiesto de complemento de una ruta de acceso, que puede ser una ubicación de archivo o una dirección URL.</span><span class="sxs-lookup"><span data-stu-id="dde17-129">Run the New-OrganizationAdd-In cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="dde17-130">En el ejemplo siguiente se muestra una ubicación de archivo para el valor del parámetro _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="dde17-130">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="dde17-131">También puede ejecutar el cmdlet New-OrganizationAdd-in para cargar un complemento y asignarlo a usuarios o grupos directamente mediante el parámetro _Members_ , como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="dde17-131">You can also run the New-OrganizationAdd-In cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="dde17-132">Separe las direcciones de correo electrónico de los miembros con una coma.</span><span class="sxs-lookup"><span data-stu-id="dde17-132">Separate the email addresses of members with a comma.</span></span> 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="dde17-133">Cargar un complemento de la tienda Office</span><span class="sxs-lookup"><span data-stu-id="dde17-133">Upload an add-in from the Office Store</span></span>
<span data-ttu-id="dde17-134"><a name="BKMK_UploadAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="dde17-134"><a name="BKMK_UploadAddin"> </a></span></span>

<span data-ttu-id="dde17-135">Ejecute el cmdlet New-OrganizationAddIn para cargar un manifiesto de la tienda Office.</span><span class="sxs-lookup"><span data-stu-id="dde17-135">Run the New-OrganizationAddIn cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="dde17-136">En el siguiente ejemplo, el cmdlet New-OrganizationAddIn especifica el AssetID para un complemento para una ubicación de Estados Unidos y un mercado de contenido.</span><span class="sxs-lookup"><span data-stu-id="dde17-136">In the following example, the New-OrganizationAddIn cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="dde17-137">Para determinar el valor para el parámetro _AssetID_ , puede copiarlo desde la dirección URL de la Página Web de la tienda Office para el complemento.</span><span class="sxs-lookup"><span data-stu-id="dde17-137">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="dde17-138">AssetIds siempre comienza por "WA" seguido de un número.</span><span class="sxs-lookup"><span data-stu-id="dde17-138">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="dde17-139">Por ejemplo, en el ejemplo anterior, el origen del valor de WA104099688 es la dirección URL de la Página Web de la tienda de Office para el complemento [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688):.</span><span class="sxs-lookup"><span data-stu-id="dde17-139">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="dde17-140">Los valores para el parámetro _locale_ y el parámetro _ContentMarket_ son idénticos e indican el país o región desde el que está intentando instalar el complemento.</span><span class="sxs-lookup"><span data-stu-id="dde17-140">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="dde17-141">El formato es en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="dde17-141">The format is en-US, fr-FR.</span></span> <span data-ttu-id="dde17-142">y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="dde17-142">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="dde17-143">Los complementos cargados desde la tienda Office se actualizarán de forma automática dentro de unos días a partir de la actualización más reciente disponible en la tienda Office.</span><span class="sxs-lookup"><span data-stu-id="dde17-143">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="dde17-144">Obtener detalles de un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-144">Get details of an add-in</span></span>
<span data-ttu-id="dde17-145"><a name="BKMK_GetDetails"> </a></span><span class="sxs-lookup"><span data-stu-id="dde17-145"><a name="BKMK_GetDetails"> </a></span></span>

<span data-ttu-id="dde17-146">Ejecute el cmdlet Get-OrganizationAddIn como se muestra a continuación para obtener detalles de todos los complementos cargados en el inquilino, incluido el identificador de producto de un complemento.</span><span class="sxs-lookup"><span data-stu-id="dde17-146">Run the Get-OrganizationAddIn cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```
Get-OrganizationAddIn
```

<span data-ttu-id="dde17-147">Ejecute el cmdlet Get-OrganizationAddIn con un valor para el parámetro _ProductID_ para especificar el complemento para el que desea recuperar los detalles.</span><span class="sxs-lookup"><span data-stu-id="dde17-147">Run the Get-OrganizationAddIn cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="dde17-148">Para obtener detalles completos de todos los complementos y los usuarios y grupos asignados, Canalice el resultado del cmdlet Get-OrganizationAddIn al cmdlet Format-List, tal como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="dde17-148">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the Get-OrganizationAddIn cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="dde17-149">Activar o desactivar un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-149">Turn on or turn off an add-in</span></span>
<span data-ttu-id="dde17-150"><a name="BKMK_TurnOnOff"> </a></span><span class="sxs-lookup"><span data-stu-id="dde17-150"><a name="BKMK_TurnOnOff"> </a></span></span>

<span data-ttu-id="dde17-151">Para desactivar un complemento de modo que los usuarios y grupos que están asignados a él ya no tengan acceso, ejecute el cmdlet Set-OrganizationAddIn con el parámetro _ProductID_ y el parámetro _Enabled_ en `$false`, tal como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="dde17-151">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the Set-OrganizationAddIn cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="dde17-152">Para volver a activar un complemento, ejecute el mismo cmdlet con el parámetro _Enabled_ establecido en `$true`.</span><span class="sxs-lookup"><span data-stu-id="dde17-152">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="dde17-153">Agregar o quitar usuarios de un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-153">Add or remove users from an add-in</span></span>
<span data-ttu-id="dde17-154"><a name="BKMK_AddRemove"> </a></span><span class="sxs-lookup"><span data-stu-id="dde17-154"><a name="BKMK_AddRemove"> </a></span></span>

<span data-ttu-id="dde17-155">Para agregar usuarios y grupos a un complemento específico, ejecute el cmdlet Set-OrganizationAddInAssignments con los parámetros _ProductID_, _Add_y _Members_ .</span><span class="sxs-lookup"><span data-stu-id="dde17-155">To add users and groups to a specific add-in, run the Set-OrganizationAddInAssignments cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="dde17-156">Separe las direcciones de correo electrónico de los miembros con una coma.</span><span class="sxs-lookup"><span data-stu-id="dde17-156">Separate the email addresses of members with a comma.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="dde17-157">Para quitar usuarios y grupos, ejecute el mismo cmdlet con el parámetro _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="dde17-157">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="dde17-158">Para asignar un complemento a todos los usuarios en el inquilino, ejecute el mismo cmdlet mediante el parámetro _AssignToEveryone_ con el valor establecido en `$true`.</span><span class="sxs-lookup"><span data-stu-id="dde17-158">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="dde17-159">Para no asignar un complemento a todos los usuarios y revertir a los usuarios y grupos asignados previamente, puede ejecutar el mismo cmdlet y desactivar el parámetro _AssignToEveryone_ estableciendo su valor en `$false`.</span><span class="sxs-lookup"><span data-stu-id="dde17-159">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="dde17-160">Actualizar un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-160">Update an add-in</span></span>
<span data-ttu-id="dde17-161"><a name="BKMK_UpdateAddin"> </a></span><span class="sxs-lookup"><span data-stu-id="dde17-161"><a name="BKMK_UpdateAddin"> </a></span></span>

<span data-ttu-id="dde17-162">Para actualizar un complemento desde un manifiesto, ejecute el cmdlet Set-OrganizationAddIn con los parámetros _ProductID_, _ManifestPath_y _locale_ , tal y como se muestra en el siguiente ejemplo.</span><span class="sxs-lookup"><span data-stu-id="dde17-162">To update an add-in from a manifest, run the Set-OrganizationAddIn cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="dde17-163">Los complementos cargados desde la tienda Office se actualizarán de forma automática dentro de unos días a partir de la actualización más reciente disponible en la tienda Office.</span><span class="sxs-lookup"><span data-stu-id="dde17-163">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="dde17-164">Eliminar un complemento</span><span class="sxs-lookup"><span data-stu-id="dde17-164">Delete an add-in</span></span>
<span data-ttu-id="dde17-165"><a name="BKMK_Delete"> </a></span><span class="sxs-lookup"><span data-stu-id="dde17-165"><a name="BKMK_Delete"> </a></span></span>

<span data-ttu-id="dde17-166">Para eliminar un complemento, ejecute el cmdlet Remove-OrganizationAddIn con el parámetro _ProductID_ , como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="dde17-166">To delete an add-in, run the Remove-OrganizationAddIn cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="dde17-167">Obtener ayuda detallada para cada cmdlet</span><span class="sxs-lookup"><span data-stu-id="dde17-167">Get detailed help for each cmdlet</span></span>
<span data-ttu-id="dde17-168"><a name="BKMK_GetHelp"> </a></span><span class="sxs-lookup"><span data-stu-id="dde17-168"><a name="BKMK_GetHelp"> </a></span></span>

<span data-ttu-id="dde17-169">Puede consultar la ayuda detallada para cada cmdlet mediante el cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="dde17-169">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="dde17-170">Por ejemplo, el siguiente cmdlet proporciona información detallada sobre el cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="dde17-170">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```
Get-help Remove-OrganizationAddIn -Full
```


