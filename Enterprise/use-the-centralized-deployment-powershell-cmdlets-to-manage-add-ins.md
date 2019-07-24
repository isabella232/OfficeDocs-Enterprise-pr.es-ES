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
- MET150
- MOE150
- MED150
- MBS150
- BCS160
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Use los cmdlets de PowerShell de implementación centralizada como ayuda para implementar y administrar complementos de Office para su organización de Office 365.
ms.openlocfilehash: 301e44da4c663fa54c4e2b753552b0b345e2a6e5
ms.sourcegitcommit: 9cd3dcf1e90b21c7651d367dcd3306d6fe0bcbcb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/23/2019
ms.locfileid: "35834240"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a><span data-ttu-id="2acef-103">Usar los cmdlets de PowerShell de Implementación centralizada para administrar complementos</span><span class="sxs-lookup"><span data-stu-id="2acef-103">Use the Centralized Deployment PowerShell cmdlets to manage add-ins</span></span>

<span data-ttu-id="2acef-104">Como Microsoft 365 global o administrador de Exchange, puede implementar complementos de Office para los usuarios a través de la característica de implementación centralizada (vea [deploy Office Add-Ins en el centro de administración](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span><span class="sxs-lookup"><span data-stu-id="2acef-104">As a Microsoft 365 global, or Exchange admin, you can deploy Office add-ins to users via the Centralized Deployment feature (see [Deploy Office Add-ins in the admin center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)).</span></span> <span data-ttu-id="2acef-105">Además de implementar complementos de Office a través del centro de administración de Microsoft 365, también puede usar PowerShell de Microsoft.</span><span class="sxs-lookup"><span data-stu-id="2acef-105">In addition to deploying Office add-ins via the Microsoft 365 admin center, you can also use Microsoft PowerShell.</span></span> <span data-ttu-id="2acef-106">Instale el [módulo de implementación de complementos centralizados de O365 para Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span><span class="sxs-lookup"><span data-stu-id="2acef-106">Install the [O365 Centralized Add-In Deployment Module for Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment).</span></span> 

<span data-ttu-id="2acef-107">Una vez que haya descargado el módulo, abra una ventana normal de Windows PowerShell y ejecute el siguiente cmdlet:</span><span class="sxs-lookup"><span data-stu-id="2acef-107">After you download the module, open a regular Windows PowerShell window and run the following cmdlet:</span></span>

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a><span data-ttu-id="2acef-108">Conectarse con las credenciales de administrador</span><span class="sxs-lookup"><span data-stu-id="2acef-108">Connect using your admin credentials</span></span>

<span data-ttu-id="2acef-109">Para poder usar los cmdlets de implementación centralizada, debe iniciar sesión.</span><span class="sxs-lookup"><span data-stu-id="2acef-109">Before you can use the Centralized Deployment cmdlets, you need to sign in.</span></span>
  
1. <span data-ttu-id="2acef-110">Inicie PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2acef-110">Start PowerShell.</span></span>
    
2. <span data-ttu-id="2acef-111">Conéctese a PowerShell con las credenciales de administrador de la compañía.</span><span class="sxs-lookup"><span data-stu-id="2acef-111">Connect to PowerShell by using your company admin credentials.</span></span> <span data-ttu-id="2acef-112">Ejecute el siguiente cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2acef-112">Run the following cmdlet.</span></span>
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. <span data-ttu-id="2acef-113">En la página **escribir credenciales** , escriba sus credenciales de administrador global de Office 365.</span><span class="sxs-lookup"><span data-stu-id="2acef-113">In the **Enter Credentials** page, enter your Office 365 global admin credentials.</span></span> <span data-ttu-id="2acef-114">Como alternativa, puede escribir sus credenciales directamente en el cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2acef-114">Alternately, you can enter your credentials directly into the cmdlet.</span></span> 
    
    <span data-ttu-id="2acef-115">Ejecute el siguiente cmdlet especificando las credenciales de administrador de la compañía como un objeto PSCredential.</span><span class="sxs-lookup"><span data-stu-id="2acef-115">Run the following cmdlet specifying your company admin credentials as a PSCredential object.</span></span>
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> <span data-ttu-id="2acef-116">Para obtener más información sobre el uso de PowerShell, vea [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span><span class="sxs-lookup"><span data-stu-id="2acef-116">For more information about using PowerShell, see [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585).</span></span> 
  
## <a name="upload-an-add-in-manifest"></a><span data-ttu-id="2acef-117">Cargar un manifiesto de complemento</span><span class="sxs-lookup"><span data-stu-id="2acef-117">Upload an add-in manifest</span></span>

<span data-ttu-id="2acef-118">Ejecute el cmdlet **New-OrganizationAdd-in** para cargar un manifiesto de complemento de una ruta de acceso, que puede ser una ubicación de archivo o una dirección URL.</span><span class="sxs-lookup"><span data-stu-id="2acef-118">Run the **New-OrganizationAdd-In** cmdlet to upload an add-in manifest from a path, which can be either a file location or URL.</span></span> <span data-ttu-id="2acef-119">En el ejemplo siguiente se muestra una ubicación de archivo para el valor del parámetro _ManifestPath_ .</span><span class="sxs-lookup"><span data-stu-id="2acef-119">The following example shows a file location for the value of the  _ManifestPath_ parameter.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

<span data-ttu-id="2acef-120">También puede ejecutar el cmdlet **New-OrganizationAdd-in** para cargar un complemento y asignarlo a usuarios o grupos directamente mediante el parámetro Members, __ como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="2acef-120">You can also run the **New-OrganizationAdd-In** cmdlet to upload an add-in and assign it to users or groups directly by using the  _Members_ parameter, as shown in the following example.</span></span> <span data-ttu-id="2acef-121">Separe las direcciones de correo electrónico de los miembros con una coma.</span><span class="sxs-lookup"><span data-stu-id="2acef-121">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a><span data-ttu-id="2acef-122">Cargar un complemento de la tienda Office</span><span class="sxs-lookup"><span data-stu-id="2acef-122">Upload an add-in from the Office Store</span></span>

<span data-ttu-id="2acef-123">Ejecute el cmdlet **New-OrganizationAddIn** para cargar un manifiesto de la tienda Office.</span><span class="sxs-lookup"><span data-stu-id="2acef-123">Run the **New-OrganizationAddIn** cmdlet to upload a manifest from the Office Store.</span></span>
  
<span data-ttu-id="2acef-124">En el siguiente ejemplo, el cmdlet **New-OrganizationAddIn** especifica el AssetID para un complemento para una ubicación de Estados Unidos y un mercado de contenido.</span><span class="sxs-lookup"><span data-stu-id="2acef-124">In the following example, the **New-OrganizationAddIn** cmdlet specifies the AssetId for an add-in for a United States location and content market.</span></span>
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

<span data-ttu-id="2acef-125">Para determinar el valor para el __ parámetro AssetID, puede copiarlo desde la dirección URL de la Página Web de la tienda Office para el complemento.</span><span class="sxs-lookup"><span data-stu-id="2acef-125">To determine the value for the  _AssetId_ parameter, you can copy it from the URL of the Office Store webpage for the add-in.</span></span> <span data-ttu-id="2acef-126">AssetIds siempre comienza por "WA" seguido de un número.</span><span class="sxs-lookup"><span data-stu-id="2acef-126">AssetIds always begin with "WA" followed by a number.</span></span> <span data-ttu-id="2acef-127">Por ejemplo, en el ejemplo anterior, el origen del valor de WA104099688 es la dirección URL de la Página Web de la tienda de Office para el complemento [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688):.</span><span class="sxs-lookup"><span data-stu-id="2acef-127">For example, in the previous example, the source for the AssetId value of WA104099688 is the Office Store webpage URL for the add-in: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).</span></span>
  
<span data-ttu-id="2acef-128">Los valores para el __ parámetro locale y el parámetro _ContentMarket_ son idénticos e indican el país o región desde el que está intentando instalar el complemento.</span><span class="sxs-lookup"><span data-stu-id="2acef-128">The values for the  _Locale_ parameter and the  _ContentMarket_ parameter are identical and indicate the country/region you're trying to install the add-in from.</span></span> <span data-ttu-id="2acef-129">El formato es en-US, fr-FR.</span><span class="sxs-lookup"><span data-stu-id="2acef-129">The format is en-US, fr-FR.</span></span> <span data-ttu-id="2acef-130">y así sucesivamente.</span><span class="sxs-lookup"><span data-stu-id="2acef-130">and so forth.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="2acef-131">Los complementos cargados desde la tienda Office se actualizarán de forma automática dentro de unos días a partir de la actualización más reciente disponible en la tienda Office.</span><span class="sxs-lookup"><span data-stu-id="2acef-131">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="get-details-of-an-add-in"></a><span data-ttu-id="2acef-132">Obtener detalles de un complemento</span><span class="sxs-lookup"><span data-stu-id="2acef-132">Get details of an add-in</span></span>

<span data-ttu-id="2acef-133">Ejecute el cmdlet **Get-OrganizationAddIn** como se muestra a continuación para obtener detalles de todos los complementos cargados en el inquilino, incluido el identificador de producto de un complemento.</span><span class="sxs-lookup"><span data-stu-id="2acef-133">Run the **Get-OrganizationAddIn** cmdlet as shown below to get details of all add-ins uploaded to the tenant, included an add-in's product ID.</span></span>
  
```powershell
Get-OrganizationAddIn
```

<span data-ttu-id="2acef-134">Ejecute el cmdlet **Get-OrganizationAddIn** con un valor para el parámetro _ProductID_ para especificar el complemento para el que desea recuperar los detalles.</span><span class="sxs-lookup"><span data-stu-id="2acef-134">Run the **Get-OrganizationAddIn** cmdlet with a value for the  _ProductId_ parameter to specify which add-in you want to retrieve details for.</span></span> 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

<span data-ttu-id="2acef-135">Para obtener detalles completos de todos los complementos y los usuarios y grupos asignados, Canalice el resultado del cmdlet **Get-OrganizationAddIn** al cmdlet Format-List, tal como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="2acef-135">To get full details of all the add-ins plus the assigned users and groups, pipe the output of the **Get-OrganizationAddIn** cmdlet to the Format-List cmdlet, as shown in the following example.</span></span>
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a><span data-ttu-id="2acef-136">Activar o desactivar un complemento</span><span class="sxs-lookup"><span data-stu-id="2acef-136">Turn on or turn off an add-in</span></span>

<span data-ttu-id="2acef-137">Para desactivar un complemento de modo que los usuarios y grupos que están asignados a él ya no tengan acceso, ejecute el cmdlet **set-OrganizationAddIn** con el parámetro _ProductID_ y el parámetro _Enabled_ en `$false`, tal como se muestra en el siguiente ejemplo .</span><span class="sxs-lookup"><span data-stu-id="2acef-137">To turn off an add-in so users and groups that are assigned to it will no longer have access, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_ parameter and the  _Enabled_ parameter set to  `$false`, as shown in the following example.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

<span data-ttu-id="2acef-138">Para volver a activar un complemento, ejecute el mismo cmdlet con el parámetro _Enabled_ establecido en `$true`.</span><span class="sxs-lookup"><span data-stu-id="2acef-138">To turn an add-in back on, run the same cmdlet with the  _Enabled_ parameter set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a><span data-ttu-id="2acef-139">Agregar o quitar usuarios de un complemento</span><span class="sxs-lookup"><span data-stu-id="2acef-139">Add or remove users from an add-in</span></span>

<span data-ttu-id="2acef-140">Para agregar usuarios y grupos a un complemento específico, ejecute el cmdlet **set-OrganizationAddInAssignments** con los parámetros _ProductID_, _Add_y Members __ .</span><span class="sxs-lookup"><span data-stu-id="2acef-140">To add users and groups to a specific add-in, run the **Set-OrganizationAddInAssignments** cmdlet with the  _ProductId_,  _Add_, and  _Members_ parameters.</span></span> <span data-ttu-id="2acef-141">Separe las direcciones de correo electrónico de los miembros con una coma.</span><span class="sxs-lookup"><span data-stu-id="2acef-141">Separate the email addresses of members with a comma.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="2acef-142">Para quitar usuarios y grupos, ejecute el mismo cmdlet con el parámetro _Remove_ .</span><span class="sxs-lookup"><span data-stu-id="2acef-142">To remove users and groups, run the same cmdlet using the  _Remove_ parameter.</span></span> 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

<span data-ttu-id="2acef-143">Para asignar un complemento a todos los usuarios en el inquilino, ejecute el mismo cmdlet mediante el parámetro _AssignToEveryone_ con el valor establecido en `$true`.</span><span class="sxs-lookup"><span data-stu-id="2acef-143">To assign an add-in to all users on the tenant, run the same cmdlet using the  _AssignToEveryone_ parameter with the value set to  `$true`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

<span data-ttu-id="2acef-144">Para no asignar un complemento a todos los usuarios y revertir a los usuarios y grupos asignados previamente, puede ejecutar el mismo cmdlet y desactivar el parámetro _AssignToEveryone_ estableciendo su valor en `$false`.</span><span class="sxs-lookup"><span data-stu-id="2acef-144">To not assign an add-in to everyone and revert to the previously assigned users and groups, you can run the same cmdlet and turn off the  _AssignToEveryone_ parameter by setting its value to  `$false`.</span></span>
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a><span data-ttu-id="2acef-145">Actualizar un complemento</span><span class="sxs-lookup"><span data-stu-id="2acef-145">Update an add-in</span></span>

<span data-ttu-id="2acef-146">Para actualizar un complemento desde un manifiesto, ejecute el cmdlet **set-OrganizationAddIn** con los parámetros _ProductID_, _ManifestPath_y locale __ , tal y como se muestra en el siguiente ejemplo.</span><span class="sxs-lookup"><span data-stu-id="2acef-146">To update an add-in from a manifest, run the **Set-OrganizationAddIn** cmdlet with the  _ProductId_,  _ManifestPath_, and  _Locale_ parameters, as shown in the following example.</span></span> 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> <span data-ttu-id="2acef-147">Los complementos cargados desde la tienda Office se actualizarán de forma automática dentro de unos días a partir de la actualización más reciente disponible en la tienda Office.</span><span class="sxs-lookup"><span data-stu-id="2acef-147">Add-ins uploaded from the Office Store will update automatically within a few days of the latest update being available on the Office Store.</span></span> 
  
## <a name="delete-an-add-in"></a><span data-ttu-id="2acef-148">Eliminar un complemento</span><span class="sxs-lookup"><span data-stu-id="2acef-148">Delete an add-in</span></span>

<span data-ttu-id="2acef-149">Para eliminar un complemento, ejecute el cmdlet **Remove-OrganizationAddIn** con el parámetro _ProductID_ , como se muestra en el ejemplo siguiente.</span><span class="sxs-lookup"><span data-stu-id="2acef-149">To delete an add-in, run the **Remove-OrganizationAddIn** cmdlet with the  _ProductId_ parameter, as shown in the following example.</span></span> 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a><span data-ttu-id="2acef-150">Personalizar complementos de Microsoft Store para su organización</span><span class="sxs-lookup"><span data-stu-id="2acef-150">Customize Microsoft Store add-ins for your organization</span></span>

<span data-ttu-id="2acef-151">Debe personalizar el complemento antes de implementarlo en su organización.</span><span class="sxs-lookup"><span data-stu-id="2acef-151">You must customize the add-in before you deploy it to your organization.</span></span> <span data-ttu-id="2acef-152">Esta característica no es compatible con los complementos anteriores a la versión 1,1.</span><span class="sxs-lookup"><span data-stu-id="2acef-152">Add-ins older than version 1.1 are not supported by this feature.</span></span> 

<span data-ttu-id="2acef-153">Le recomendamos que primero implemente un complemento personalizado para asegurarse de que funciona según lo esperado antes de implementarlo en toda la organización.</span><span class="sxs-lookup"><span data-stu-id="2acef-153">We recommend that you deploy a customized add-in  to yourself first to make sure it works as expected before you deploy it to your entire organization.</span></span>

<span data-ttu-id="2acef-154">Tenga en cuenta también las siguientes restricciones:</span><span class="sxs-lookup"><span data-stu-id="2acef-154">Note also the following restrictions:</span></span>
- <span data-ttu-id="2acef-155">Todas las direcciones URL deben ser absolutas (incluidas http o https) y válidas.</span><span class="sxs-lookup"><span data-stu-id="2acef-155">All URLs must be absolute (include http or https) and valid.</span></span>
- <span data-ttu-id="2acef-156">*DisplayName* no debe superar los 125 caracteres</span><span class="sxs-lookup"><span data-stu-id="2acef-156">*DisplayName* must not exceed 125 characters</span></span> 
- <span data-ttu-id="2acef-157">*DisplayName*, \*\* Resources y *AppDomains* no deben incluir los siguientes caracteres:</span><span class="sxs-lookup"><span data-stu-id="2acef-157">*DisplayName*, *Resources* and *AppDomains* must not include the following characters:</span></span> 
 
    - \<
    -  \>
    -  <span data-ttu-id="2acef-158">;</span><span class="sxs-lookup"><span data-stu-id="2acef-158"></span></span>
    -  =   

<span data-ttu-id="2acef-159">Si desea personalizar un complemento que se ha implementado, debe desinstalarlo en el centro de administración y ver [quitar un complemento de la memoria caché local](#remove-an-add-in-from-local-cache) para conocer los pasos para quitarlo de cada equipo en el que se ha implementado.</span><span class="sxs-lookup"><span data-stu-id="2acef-159">If you want to customize an add-in that has been deployed, you have to uninstall it in the admin center, and see [remove an add-in from local cache](#remove-an-add-in-from-local-cache) for steps to remove it from each computer it has been deployed to.</span></span>

<span data-ttu-id="2acef-160">Para personalizar un complemento, ejecute el cmdlet **set – OrganizationAddInOverrides** con *ProductID* como parámetro, seguido de la etiqueta que desea sobrescribir y el nuevo valor.</span><span class="sxs-lookup"><span data-stu-id="2acef-160">To customize an add-in, run the **Set –OrganizationAddInOverrides** cmdlet with the *ProductId* as a parameter, followed by the tag you want to overwrite and the new value.</span></span> <span data-ttu-id="2acef-161">Para averiguar cómo obtener el *ProductID* [, vea obtener detalles de un complemento](#get-details-of-an-add-in) en este artículo.</span><span class="sxs-lookup"><span data-stu-id="2acef-161">To find out how to get the *ProductId* see [get details of an add-in](#get-details-of-an-add-in) in this article.</span></span> <span data-ttu-id="2acef-162">Por ejemplo:</span><span class="sxs-lookup"><span data-stu-id="2acef-162">For example:</span></span>

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
<span data-ttu-id="2acef-163">Para personalizar varias etiquetas para un complemento, agregue las etiquetas a la línea de comandos:</span><span class="sxs-lookup"><span data-stu-id="2acef-163">To customize multiple tags for an add-in, add those tags to the commandline:</span></span>

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> <span data-ttu-id="2acef-164">Debe aplicar varias etiquetas personalizadas a un complemento como un comando.</span><span class="sxs-lookup"><span data-stu-id="2acef-164">You must apply multiple customized tags to one add-in as one command.</span></span> <span data-ttu-id="2acef-165">Si personaliza las etiquetas una a una, sólo se aplicará la última personalización.</span><span class="sxs-lookup"><span data-stu-id="2acef-165">If you customize tags one by one, only the last customization will be applied.</span></span> <span data-ttu-id="2acef-166">Además, si personaliza una etiqueta por error, debe quitar todas las personalizaciones y empezar de nuevo.</span><span class="sxs-lookup"><span data-stu-id="2acef-166">Additionally, if you customize a tag by mistake, you must remove all customizations and start over.</span></span>

### <a name="tags-you-can-customize"></a><span data-ttu-id="2acef-167">Etiquetas que puede personalizar</span><span class="sxs-lookup"><span data-stu-id="2acef-167">Tags you can customize</span></span>

| <span data-ttu-id="2acef-168">Tag</span><span class="sxs-lookup"><span data-stu-id="2acef-168">Tag</span></span>                  | <span data-ttu-id="2acef-169">Descripción</span><span class="sxs-lookup"><span data-stu-id="2acef-169">Description</span></span>          |
| :------------------- | :------------------- |
| <span data-ttu-id="2acef-170">\<> IconURL</span><span class="sxs-lookup"><span data-stu-id="2acef-170">\<IconURL></span></span>   </br>| <span data-ttu-id="2acef-171">La dirección URL de la imagen usada como el icono del complemento (en el centro de administración).</span><span class="sxs-lookup"><span data-stu-id="2acef-171">The URL of the image used as the add-in’s icon (in admin center).</span></span> </br> |
| <span data-ttu-id="2acef-172">\<DisplayName></span><span class="sxs-lookup"><span data-stu-id="2acef-172">\<DisplayName></span></span>| <span data-ttu-id="2acef-173">El título del complemento (en el centro de administración).</span><span class="sxs-lookup"><span data-stu-id="2acef-173">The title of the add-in  (in admin center).</span></span>|
| <span data-ttu-id="2acef-174">\<Hosts></span><span class="sxs-lookup"><span data-stu-id="2acef-174">\<Hosts></span></span>| <span data-ttu-id="2acef-175">Lista de aplicaciones que admitirán el complemento.</span><span class="sxs-lookup"><span data-stu-id="2acef-175">List of apps that will support the add-in.</span></span>|
| <span data-ttu-id="2acef-176">\<> SourceLocation</span><span class="sxs-lookup"><span data-stu-id="2acef-176">\<SourceLocation></span></span> | <span data-ttu-id="2acef-177">La URL de origen a la que se conectará el complemento.</span><span class="sxs-lookup"><span data-stu-id="2acef-177">The source URL that the add-in will connect to.</span></span>| 
| <span data-ttu-id="2acef-178">\<AppDomain></span><span class="sxs-lookup"><span data-stu-id="2acef-178">\<AppDomains></span></span> | <span data-ttu-id="2acef-179">Una lista de dominios con los que se puede conectar el complemento.</span><span class="sxs-lookup"><span data-stu-id="2acef-179">A list of domains that the add-in can connect with.</span></span> | 
| <span data-ttu-id="2acef-180">\<SupportURL></span><span class="sxs-lookup"><span data-stu-id="2acef-180">\<SupportURL></span></span>| <span data-ttu-id="2acef-181">La dirección URL que los usuarios pueden usar para tener acceso a ayuda y soporte técnico.</span><span class="sxs-lookup"><span data-stu-id="2acef-181">The URL users can use to access help and support.</span></span> | 
| <span data-ttu-id="2acef-182">\<Recursos></span><span class="sxs-lookup"><span data-stu-id="2acef-182">\<Resources></span></span>  | <span data-ttu-id="2acef-183">Esta etiqueta contiene un número de elementos que incluyen títulos, información sobre herramientas e iconos de diferentes tamaños.</span><span class="sxs-lookup"><span data-stu-id="2acef-183">This tag contains a number of elements including titles, tooltips, and icons of different sizes.</span></span>| 
|
### <a name="customize-resources-tag"></a><span data-ttu-id="2acef-184">Personalizar etiqueta de recursos</span><span class="sxs-lookup"><span data-stu-id="2acef-184">Customize Resources tag</span></span>

<span data-ttu-id="2acef-185">Cualquier elemento de la <Resources> etiqueta del manifiesto se puede personalizar dinámicamente.</span><span class="sxs-lookup"><span data-stu-id="2acef-185">Any element in the <Resources> tag of the manifest can be customized dynamically.</span></span> <span data-ttu-id="2acef-186">Primero debe comprobar el manifiesto para encontrar el identificador de elemento al que desea asignar un nuevo valor.</span><span class="sxs-lookup"><span data-stu-id="2acef-186">You first need to check the manifest to find the element id to which you want to assign a new value.</span></span> <span data-ttu-id="2acef-187">La <Resources> etiqueta tiene un aspecto similar a este:</span><span class="sxs-lookup"><span data-stu-id="2acef-187">The <Resources> tag looks like this:</span></span>

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
<span data-ttu-id="2acef-188">En este caso, el identificador de elemento de la imagen es "img16icon" y el valor asociado es "http:<i></i>//site. <i> </i>com/img. jpg. "</span><span class="sxs-lookup"><span data-stu-id="2acef-188">In this case, the element id for the image is “img16icon” and the value associated with it is “http:<i></i>//site.<i></i>com/img.jpg.”</span></span>

<span data-ttu-id="2acef-189">Una vez que haya identificado los elementos que desea personalizar, use el siguiente comando en PowerShell para asignar nuevos valores a los elementos:</span><span class="sxs-lookup"><span data-stu-id="2acef-189">Once you have identified the elements you want to customize, use the following command in Powershell to assign new values to the elements:</span></span>

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

<span data-ttu-id="2acef-190">Puede personalizar tantos elementos con el comando como sea necesario.</span><span class="sxs-lookup"><span data-stu-id="2acef-190">You can customize as many elements with the command as you need to.</span></span>

### <a name="remove-customization-from-an-add-in"></a><span data-ttu-id="2acef-191">Quitar la personalización de un complemento</span><span class="sxs-lookup"><span data-stu-id="2acef-191">Remove customization from an add-in</span></span>

<span data-ttu-id="2acef-192">La única opción disponible actualmente para eliminar personalizaciones es eliminar todas a la vez:</span><span class="sxs-lookup"><span data-stu-id="2acef-192">The only option currently available for deleting customizations is to delete all of them at once:</span></span>

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a><span data-ttu-id="2acef-193">Ver personalizaciones de complementos</span><span class="sxs-lookup"><span data-stu-id="2acef-193">View add-in customizations</span></span>

<span data-ttu-id="2acef-194">Para ver una lista de las personalizaciones aplicadas, ejecute el cmdlet **Get-OrganizationAddInOverrides** .</span><span class="sxs-lookup"><span data-stu-id="2acef-194">To view a list of applied customizations, run the **Get-OrganizationAddInOverrides** cmdlet.</span></span> <span data-ttu-id="2acef-195">Si **Get-OrganizationAddInOverrides** se ejecuta sin un *ProductID* , se devuelve una lista de todos los complementos con reemplazos aplicados.</span><span class="sxs-lookup"><span data-stu-id="2acef-195">If **Get-OrganizationAddInOverrides** is run without a *ProductId* then a list of all add-ins with applied overrides are returned.</span></span>  

```powershell
Get-OrganizationAddInOverrides 
```
<span data-ttu-id="2acef-196">Si se especifica ProductId, se devuelve una lista de reemplazos aplicados a ese complemento.</span><span class="sxs-lookup"><span data-stu-id="2acef-196">If ProductId is specified, then a list of overrides applied to that add-in is returned.</span></span> 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a><span data-ttu-id="2acef-197">Quitar un complemento de la memoria caché local</span><span class="sxs-lookup"><span data-stu-id="2acef-197">Remove an add-in from local cache</span></span>

<span data-ttu-id="2acef-198">Si se ha implementado un complemento, debe quitarse de la memoria caché en cada equipo antes de que se pueda personalizar.</span><span class="sxs-lookup"><span data-stu-id="2acef-198">If an add-in has been deployed, it has to be removed from the cache in each computer before it can be customized.</span></span> <span data-ttu-id="2acef-199">Para Remive un complemento de la memoria caché:</span><span class="sxs-lookup"><span data-stu-id="2acef-199">To remive an add-in from cache:</span></span>

1. <span data-ttu-id="2acef-200">Navegue hasta la carpeta "usuarios" en C:</span><span class="sxs-lookup"><span data-stu-id="2acef-200">Navigate to the “Users” folder in C:</span></span>\ 
1. <span data-ttu-id="2acef-201">Ir a la carpeta de usuario</span><span class="sxs-lookup"><span data-stu-id="2acef-201">Go to your user folder</span></span>
1. <span data-ttu-id="2acef-202">Vaya a AppData\Local\Microsoft\Office y seleccione la carpeta asociada con su versión de Office.</span><span class="sxs-lookup"><span data-stu-id="2acef-202">Navigate to AppData\Local\Microsoft\Office and select the folder associated with your version of Office</span></span>
1. <span data-ttu-id="2acef-203">En la carpeta *WEF* , elimine la carpeta *Manifests* .</span><span class="sxs-lookup"><span data-stu-id="2acef-203">In the *Wef* folder delete the *Manifests* folder.</span></span>

## <a name="get-detailed-help-for-each-cmdlet"></a><span data-ttu-id="2acef-204">Obtener ayuda detallada para cada cmdlet</span><span class="sxs-lookup"><span data-stu-id="2acef-204">Get detailed help for each cmdlet</span></span>

<span data-ttu-id="2acef-205">Puede consultar la ayuda detallada para cada cmdlet mediante el cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="2acef-205">You can look at detailed help for each cmdlet by using the Get-help cmdlet.</span></span> <span data-ttu-id="2acef-206">Por ejemplo, el siguiente cmdlet proporciona información detallada sobre el cmdlet Remove-OrganizationAddIn.</span><span class="sxs-lookup"><span data-stu-id="2acef-206">For example, the following cmdlet provides detailed information about the Remove-OrganizationAddIn cmdlet.</span></span>
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


