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
ms.assetid: 94f4e86d-b8e5-42dd-b558-e6092f830ec9
description: Use los cmdlets de PowerShell de implementación centralizada como ayuda para implementar y administrar complementos de Office para su organización de Office 365.
ms.openlocfilehash: 404085d79827664437f3ad327fac4a99166adcf4
ms.sourcegitcommit: 08e1e1c09f64926394043291a77856620d6f72b5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "34071146"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Usar los cmdlets de PowerShell de Implementación centralizada para administrar complementos

Como administrador de Office 365, puede implementar complementos de Office para los usuarios a través de la característica de implementación centralizada (vea [Manage Deployment of office 365 Add-Ins in the office 365 admin Center](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f)). Además de implementar complementos de Office a través del centro de administración de Office 365, también puede usar PowerShell de Microsoft. [Descargue](https://go.microsoft.com/fwlink/p/?linkid=850850) los cmdlets de PowerShell de implementación centralizada desde el centro de descarga de Microsoft. 
  
## <a name="what-do-you-want-to-do"></a>¿Qué quiere hacer?

[Conectarse con las credenciales de administrador](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Connect)
  
[Cargar un manifiesto de complemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadManifest)
  
[Cargar un complemento de la tienda Office](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UploadAddin)
  
[Obtener detalles de un complemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetDetails)
  
[Activar o desactivar un complemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_TurnOnOff)
  
[Agregar o quitar usuarios de un complemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_AddRemove)
  
[Actualizar un complemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_UpdateAddin)
  
[Eliminar un complemento](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_Delete)
  
[Obtener ayuda detallada para cada cmdlet](use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins.md#BKMK_GetHelp)
  
## <a name="connect-using-your-admin-credentials"></a>Conectarse con las credenciales de administrador
<a name="BKMK_Connect"> </a>

Para poder usar los cmdlets de implementación centralizada, debe iniciar sesión.
  
1. Inicie PowerShell.
    
2. Conéctese a PowerShell con las credenciales de administrador de la compañía. Ejecute el siguiente cmdlet.
    
  ```
  Connect-OrganizationAddInService
  ```

3. En la página **escribir credenciales** , escriba sus credenciales de administrador global de Office 365. Como alternativa, puede escribir sus credenciales directamente en el cmdlet. 
    
    Ejecute el siguiente cmdlet especificando las credenciales de administrador de la compañía como un objeto PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Para obtener más información sobre el uso de PowerShell, vea [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Cargar un manifiesto de complemento
<a name="BKMK_UploadManifest"> </a>

Ejecute el cmdlet New-OrganizationAdd-in para cargar un manifiesto de complemento de una ruta de acceso, que puede ser una ubicación de archivo o una dirección URL. En el ejemplo siguiente se muestra una ubicación de archivo para el valor del parámetro _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

También puede ejecutar el cmdlet New-OrganizationAdd-in para cargar un complemento y asignarlo a usuarios o grupos directamente mediante el parámetro Members, __ como se muestra en el ejemplo siguiente. Separe las direcciones de correo electrónico de los miembros con una coma. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Cargar un complemento de la tienda Office
<a name="BKMK_UploadAddin"> </a>

Ejecute el cmdlet New-OrganizationAddIn para cargar un manifiesto de la tienda Office.
  
En el siguiente ejemplo, el cmdlet New-OrganizationAddIn especifica el assetId para un complemento para una ubicación de Estados Unidos y un mercado de contenido.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Para determinar el valor para el __ parámetro AssetID, puede copiarlo desde la dirección URL de la Página Web de la tienda Office para el complemento. AssetIds siempre comienza por "WA" seguido de un número. Por ejemplo, en el ejemplo anterior, el origen del valor de WA104099688 es la dirección URL de la Página Web de la tienda de Office para el complemento [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688):.
  
Los valores para el __ parámetro locale y el parámetro _ContentMarket_ son idénticos e indican el país o región desde el que está intentando instalar el complemento. El formato es en-US, fr-FR. y así sucesivamente. 
  
> [!NOTE]
> Los complementos cargados desde la tienda Office se actualizarán de forma automática dentro de unos días a partir de la actualización más reciente disponible en la tienda Office. 
  
## <a name="get-details-of-an-add-in"></a>Obtener detalles de un complemento
<a name="BKMK_GetDetails"> </a>

Ejecute el cmdlet Get-OrganizationAddIn como se muestra a continuación para obtener detalles de todos los complementos cargados en el inquilino, incluido el identificador de producto de un complemento.
  
```
Get-OrganizationAddIn
```

Ejecute el cmdlet Get-OrganizationAddIn con un valor para el parámetro _ProductID_ para especificar el complemento para el que desea recuperar los detalles. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Para obtener detalles completos de todos los complementos y los usuarios y grupos asignados, Canalice el resultado del cmdlet Get-OrganizationAddIn al cmdlet Format-List, tal como se muestra en el ejemplo siguiente.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Activar o desactivar un complemento
<a name="BKMK_TurnOnOff"> </a>

Para desactivar un complemento de modo que los usuarios y grupos que están asignados a él ya no tengan acceso, ejecute el cmdlet Set-OrganizationAddIn con el parámetro _ProductID_ y el parámetro _Enabled_ en `$false`, tal como se muestra en el ejemplo siguiente.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Para volver a activar un complemento, ejecute el mismo cmdlet con el parámetro _Enabled_ establecido en `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Agregar o quitar usuarios de un complemento
<a name="BKMK_AddRemove"> </a>

Para agregar usuarios y grupos a un complemento específico, ejecute el cmdlet Set-OrganizationAddInAssignments con los parámetros _ProductID_, _Add_y Members __ . Separe las direcciones de correo electrónico de los miembros con una coma. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para quitar usuarios y grupos, ejecute el mismo cmdlet con el parámetro _Remove_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para asignar un complemento a todos los usuarios en el inquilino, ejecute el mismo cmdlet mediante el parámetro _AssignToEveryone_ con el valor establecido en `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Para no asignar un complemento a todos los usuarios y revertir a los usuarios y grupos asignados previamente, puede ejecutar el mismo cmdlet y desactivar el parámetro _AssignToEveryone_ estableciendo su valor en `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Actualizar un complemento
<a name="BKMK_UpdateAddin"> </a>

Para actualizar un complemento desde un manifiesto, ejecute el cmdlet Set-OrganizationAddIn con los parámetros _ProductID_, _ManifestPath_y locale __ , tal y como se muestra en el siguiente ejemplo. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Los complementos cargados desde la tienda Office se actualizarán de forma automática dentro de unos días a partir de la actualización más reciente disponible en la tienda Office. 
  
## <a name="delete-an-add-in"></a>Eliminar un complemento
<a name="BKMK_Delete"> </a>

Para eliminar un complemento, ejecute el cmdlet Remove-OrganizationAddIn con el parámetro _ProductID_ , como se muestra en el ejemplo siguiente. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Obtener ayuda detallada para cada cmdlet
<a name="BKMK_GetHelp"> </a>

Puede consultar la ayuda detallada para cada cmdlet mediante el cmdlet Get-Help. Por ejemplo, el siguiente cmdlet proporciona información detallada sobre el cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


