---
title: Usar los cmdlets de PowerShell de implementación centralizada para administrar complementos
ms.author: twerner
author: twernermsft
manager: scotv
ms.date: 5/31/2017
ms.audience: Admin
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
description: Use los cmdlets de PowerShell de implementación centralizado que le ayudarán a implementar y administrar complementos de Office para su organización de Office 365.
ms.openlocfilehash: 6199ad2d37a11166155b898b52d52304836599d0
ms.sourcegitcommit: 69d60723e611f3c973a6d6779722aa9da77f647f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/27/2018
ms.locfileid: "22542946"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Usar los cmdlets de PowerShell de implementación centralizada para administrar complementos

Como un administrador de Office 365, puede implementar los complementos de Office a los usuarios a través de la implementación centralizada de la característica (vea [implementar Office Add-ins en el centro de administración de Office 365](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Además de la implementación de complementos de Office mediante el centro de administración de Office 365, también puede usar Microsoft PowerShell. [Descargar](https://go.microsoft.com/fwlink/p/?linkid=850850) los cmdlets de PowerShell de implementación centralizada desde Microsoft Download Center. 
    
## <a name="connect-using-your-admin-credentials"></a>Conectarse con sus credenciales de administrador

Antes de que puede usar los cmdlets de implementación centralizado, tiene que iniciar sesión.
  
1. Inicie PowerShell.
    
2. Conectarse a PowerShell con sus credenciales de administrador de empresa. Ejecute el siguiente cmdlet.
    
  ```
  Connect-OrganizationAddInService
  ```

3. En la página **Especificar credenciales** , escriba sus credenciales de administrador global de Office 365. Como alternativa, puede escribir sus credenciales directamente en el cmdlet. 
    
    Ejecute el siguiente cmdlet que especifica la compañía credenciales de administrador como un objeto PSCredential.
    
  ```
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Para obtener más información acerca del uso de PowerShell, vea [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Cargar un complemento de manifiesto

Ejecute el cmdlet New-OrganizationAdd de entrada para cargar un manifiesto de complemento desde una ruta de acceso, que puede ser una ubicación de archivo o la dirección URL. En el ejemplo siguiente se muestra una ubicación de archivos para el valor del parámetro _ManifestPath_ . 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

También puede ejecutar el cmdlet New-OrganizationAdd de entrada para cargar un complemento y asignar a usuarios o grupos de directamente mediante el parámetro _Members_ , tal como se muestra en el siguiente ejemplo. Separe las direcciones de correo electrónico de miembros con una coma. 
  
```
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Cargar un complemento de la tienda Office

Ejecute el cmdlet New-OrganizationAddIn para cargar un manifiesto de la tienda Office.
  
En el siguiente ejemplo, el cmdlet New-OrganizationAddIn especifica el idtema para un complemento para un mercado de ubicación y el contenido de los Estados Unidos.
  
```
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Para determinar el valor para el parámetro _idtema_ , puede copiarlo desde la dirección URL de la tienda de Office página Web para el complemento AssetIds siempre comienzan con "WA" seguido de un número. Por ejemplo, en el ejemplo anterior, el origen para el valor idtema de WA104099688 es la dirección URL de página Web de almacén de Office para el complemento: [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688).
  
Los valores para el parámetro de _Configuración regional_ y el parámetro _ContentMarket_ son idénticos e indican el país o región que está intentando instalar el complemento de. El formato es en-US, fr-FR. y así sucesivamente. 
  
> [!NOTE]
> Complementos cargados desde el almacén de Office se actualizarán automáticamente dentro de unos días de la última actualización que están disponibles en la tienda de Office. 
  
## <a name="get-details-of-an-add-in"></a>Obtener detalles de un complemento

Ejecute el cmdlet Get-OrganizationAddIn tal y como se muestra a continuación obtener detalles de todos los complementos cargados en el inquilino, incluido identificador del producto. de un complemento
  
```
Get-OrganizationAddIn
```

Ejecute el cmdlet Get-OrganizationAddIn con un valor para el parámetro _ProductId_ especificar el complemento que desea recuperar detalles para. 
  
```
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Para obtener detalles completos de todos los complementos además de los grupos y usuarios asignados, canalizar la salida del cmdlet Get-OrganizationAddIn al cmdlet Format-List, tal como se muestra en el siguiente ejemplo.
  
```
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Activar o desactivar un complemento

Para desactivar un complemento por lo que los usuarios y grupos que se asignan a esta ya no tendrá acceso, ejecute el cmdlet Set-OrganizationAddIn con el parámetro _ProductId_ y el parámetro _Enabled_ se establece en `$false`, tal como se muestra en el siguiente ejemplo.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Para volver a activar un complemento, ejecute el cmdlet mismo con el parámetro _Enabled_ se establece en `$true`.
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Agregar o quitar usuarios de un complemento

Para agregar usuarios y grupos a un complemento específico, ejecute el cmdlet Set-OrganizationAddInAssignments con los parámetros de _ProductId_, _Agregar_y _miembros_ . Separe las direcciones de correo electrónico de miembros con una coma. 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para quitar usuarios y grupos, ejecute el cmdlet mismo mediante el parámetro _Quitar_ . 
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para asignar un complemento a todos los usuarios en el inquilino, ejecute el cmdlet mismo mediante el parámetro _AssignToEveryone_ con el valor establecido `$true`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Para no asignar un complemento para todos los usuarios y volver a los asignado previamente a los usuarios y grupos, puede ejecutar el cmdlet mismo y desactivar el parámetro _AssignToEveryone_ estableciendo su valor en `$false`.
  
```
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Actualizar un complemento

Para actualizar un complemento de un manifiesto, ejecute el cmdlet Set-OrganizationAddIn con el _ProductId_, _ManifestPath_y parámetros de _Configuración regional_ , como se muestra en el siguiente ejemplo. 
  
```
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Complementos cargados desde el almacén de Office se actualizarán automáticamente dentro de unos días de la última actualización que están disponibles en la tienda de Office. 
  
## <a name="delete-an-add-in"></a>Eliminación de un complemento

Para eliminar un complemento, ejecute el cmdlet Remove-OrganizationAddIn con el parámetro _ProductId_ , tal como se muestra en el siguiente ejemplo. 
  
```
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="get-detailed-help-for-each-cmdlet"></a>Obtener ayuda detallada para cada cmdlet

Puede buscar en la ayuda detallada para cada cmdlet mediante el cmdlet Get-help. Por ejemplo, el siguiente cmdlet proporciona información detallada sobre el cmdlet Remove-OrganizationAddIn.
  
```
Get-help Remove-OrganizationAddIn -Full
```


