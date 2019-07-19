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
ms.openlocfilehash: c63a48d212bba4eda25fb6b8843f6321892dc54b
ms.sourcegitcommit: d53033c2d2d41d52047e3e2644d77373d4a5dd9a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/18/2019
ms.locfileid: "35791255"
---
# <a name="use-the-centralized-deployment-powershell-cmdlets-to-manage-add-ins"></a>Usar los cmdlets de PowerShell de Implementación centralizada para administrar complementos

Como Microsoft 365 global o administrador de Exchange, puede implementar complementos de Office para los usuarios a través de la característica de implementación centralizada (vea [deploy Office Add-Ins en el centro de administración](https://support.office.com/article/737e8c86-be63-44d7-bf02-492fa7cd9c3f.aspx)). Además de implementar complementos de Office a través del centro de administración de Microsoft 365, también puede usar PowerShell de Microsoft. Instale el [módulo de implementación de complementos centralizados de O365 para Windows PowerShell](https://www.powershellgallery.com/packages/O365CentralizedAddInDeployment). 

Una vez que haya descargado el módulo, abra una ventana normal de Windows PowerShell y ejecute el siguiente cmdlet:

```powershell
 Import-Module -Name O365CentralizedAddInDeployment
```
    
## <a name="connect-using-your-admin-credentials"></a>Conectarse con las credenciales de administrador

Para poder usar los cmdlets de implementación centralizada, debe iniciar sesión.
  
1. Inicie PowerShell.
    
2. Conéctese a PowerShell con las credenciales de administrador de la compañía. Ejecute el siguiente cmdlet.
    
  ```powershell
  Connect-OrganizationAddInService
  ```

3. En la página **escribir credenciales** , escriba sus credenciales de administrador global de Office 365. Como alternativa, puede escribir sus credenciales directamente en el cmdlet. 
    
    Ejecute el siguiente cmdlet especificando las credenciales de administrador de la compañía como un objeto PSCredential.
    
  ```powershell
  $secpasswd = ConvertTo-SecureString "MyPassword" -AsPlainText -Force
  $mycredentials = New-Object System.Management.Automation.PSCredential ("serviceaccount@contoso.com", $secpasswd)
  Connect-OrganizationAddInService -Credential $mycredentials
  ```

> [!NOTE]
> Para obtener más información sobre el uso de PowerShell, vea [Connect to Office 365 PowerShell](https://go.microsoft.com/fwlink/p/?linkid=848585). 
  
## <a name="upload-an-add-in-manifest"></a>Cargar un manifiesto de complemento

Ejecute el cmdlet **New-OrganizationAdd-in** para cargar un manifiesto de complemento de una ruta de acceso, que puede ser una ubicación de archivo o una dirección URL. En el ejemplo siguiente se muestra una ubicación de archivo para el valor del parámetro _ManifestPath_ . 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

También puede ejecutar el cmdlet **New-OrganizationAdd-in** para cargar un complemento y asignarlo a usuarios o grupos directamente mediante el parámetro Members, __ como se muestra en el ejemplo siguiente. Separe las direcciones de correo electrónico de los miembros con una coma. 
  
```powershell
New-OrganizationAddIn -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US' -Members  'KathyBonner@contoso.com', 'MaxHargrave@contoso.com'
```

## <a name="upload-an-add-in-from-the-office-store"></a>Cargar un complemento de la tienda Office

Ejecute el cmdlet **New-OrganizationAddIn** para cargar un manifiesto de la tienda Office.
  
En el siguiente ejemplo, el cmdlet **New-OrganizationAddIn** especifica el AssetID para un complemento para una ubicación de Estados Unidos y un mercado de contenido.
  
```powershell
New-OrganizationAddIn -AssetId 'WA104099688' -Locale 'en-US' -ContentMarket 'en-US'
```

Para determinar el valor para el __ parámetro AssetID, puede copiarlo desde la dirección URL de la Página Web de la tienda Office para el complemento. AssetIds siempre comienza por "WA" seguido de un número. Por ejemplo, en el ejemplo anterior, el origen del valor de WA104099688 es la dirección URL de la Página Web de la tienda de Office para el complemento [https://store.office.com/en-001/app.aspx?assetid=WA104099688](https://store.office.com/en-001/app.aspx?assetid=WA104099688):.
  
Los valores para el __ parámetro locale y el parámetro _ContentMarket_ son idénticos e indican el país o región desde el que está intentando instalar el complemento. El formato es en-US, fr-FR. y así sucesivamente. 
  
> [!NOTE]
> Los complementos cargados desde la tienda Office se actualizarán de forma automática dentro de unos días a partir de la actualización más reciente disponible en la tienda Office. 
  
## <a name="get-details-of-an-add-in"></a>Obtener detalles de un complemento

Ejecute el cmdlet **Get-OrganizationAddIn** como se muestra a continuación para obtener detalles de todos los complementos cargados en el inquilino, incluido el identificador de producto de un complemento.
  
```powershell
Get-OrganizationAddIn
```

Ejecute el cmdlet **Get-OrganizationAddIn** con un valor para el parámetro _ProductID_ para especificar el complemento para el que desea recuperar los detalles. 
  
```powershell
Get-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

Para obtener detalles completos de todos los complementos y los usuarios y grupos asignados, Canalice el resultado del cmdlet **Get-OrganizationAddIn** al cmdlet Format-List, tal como se muestra en el ejemplo siguiente.
  
```powershell
Get-OrganizationAddIn |Format-List
```

## <a name="turn-on-or-turn-off-an-add-in"></a>Activar o desactivar un complemento

Para desactivar un complemento de modo que los usuarios y grupos que están asignados a él ya no tengan acceso, ejecute el cmdlet **set-OrganizationAddIn** con el parámetro _ProductID_ y el parámetro _Enabled_ en `$false`, tal como se muestra en el siguiente ejemplo .
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $false
```

Para volver a activar un complemento, ejecute el mismo cmdlet con el parámetro _Enabled_ establecido en `$true`.
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Enabled $true
```

## <a name="add-or-remove-users-from-an-add-in"></a>Agregar o quitar usuarios de un complemento

Para agregar usuarios y grupos a un complemento específico, ejecute el cmdlet **set-OrganizationAddInAssignments** con los parámetros _ProductID_, _Add_y Members __ . Separe las direcciones de correo electrónico de los miembros con una coma. 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Add -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para quitar usuarios y grupos, ejecute el mismo cmdlet con el parámetro _Remove_ . 
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -Remove -Members 'KathyBonner@contoso.com','sales@contoso.com'
```

Para asignar un complemento a todos los usuarios en el inquilino, ejecute el mismo cmdlet mediante el parámetro _AssignToEveryone_ con el valor establecido en `$true`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $true
```

Para no asignar un complemento a todos los usuarios y revertir a los usuarios y grupos asignados previamente, puede ejecutar el mismo cmdlet y desactivar el parámetro _AssignToEveryone_ estableciendo su valor en `$false`.
  
```powershell
Set-OrganizationAddInAssignments -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -AssignToEveryone $false
```

## <a name="update-an-add-in"></a>Actualizar un complemento

Para actualizar un complemento desde un manifiesto, ejecute el cmdlet **set-OrganizationAddIn** con los parámetros _ProductID_, _ManifestPath_y locale __ , tal y como se muestra en el siguiente ejemplo. 
  
```powershell
Set-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122 -ManifestPath 'C:\Users\Me\Desktop\taskpane.xml' -Locale 'en-US'
```

> [!NOTE]
> Los complementos cargados desde la tienda Office se actualizarán de forma automática dentro de unos días a partir de la actualización más reciente disponible en la tienda Office. 
  
## <a name="delete-an-add-in"></a>Eliminar un complemento

Para eliminar un complemento, ejecute el cmdlet **Remove-OrganizationAddIn** con el parámetro _ProductID_ , como se muestra en el ejemplo siguiente. 
  
```powershell
Remove-OrganizationAddIn -ProductId 6a75788e-1c6b-4e9b-b5db-5975a2072122
```

## <a name="customize-microsoft-store-add-ins-for-your-organization"></a>Personalizar complementos de Microsoft Store para su organización

Debe personalizar el complemento antes de implementarlo en su organización. Esta característica no es compatible con los complementos anteriores a la versión 1,1. 

Tenga en cuenta también las siguientes restricciones:
- Todas las direcciones URL deben ser absolutas (incluidas http o https) y válidas.
- *DisplayName* no debe superar los 125 caracteres 
- *DisplayName*, ** Resources y *AppDomains* no deben incluir los siguientes caracteres: 
 
    - \<
    -  \>
    -  ;
    -  =   

Si desea personalizar un complemento que se ha implementado, debe desinstalarlo en el centro de administración y ver [quitar un complemento de la memoria caché local](#remove-an-add-in-from-local-cache) para conocer los pasos para quitarlo de cada equipo en el que se ha implementado.

Para personalizar un complemento, ejecute el cmdlet **set – OrganizationAddInOverrides** con *ProductID* como parámetro, seguido de la etiqueta que desea sobrescribir y el nuevo valor. Para averiguar cómo obtener el *ProductID* [, vea obtener detalles de un complemento](#get-details-of-an-add-in) en este artículo. Por ejemplo:

```powershell
 Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -IconUrl "http://site.com/img.jpg" 
```
Para personalizar varias etiquetas para un complemento, agregue las etiquetas a la línea de comandos:

```powershell
Set-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 -Hosts h1, 2 -DisplayName "New DocuSign W" -IconUrl "http://site.com/img.jpg" 
```

> [!IMPORTANT]
> Debe aplicar varias etiquetas personalizadas a un complemento como un comando. Si personaliza las etiquetas una a una, sólo se aplicará la última personalización. Además, si personaliza una etiqueta por error, debe quitar todas las personalizaciones y empezar de nuevo.

### <a name="tags-you-can-customize"></a>Etiquetas que puede personalizar

| Tag                  | Descripción          |
| :------------------- | :------------------- |
| \<> IconURL   </br>| La dirección URL de la imagen usada como el icono del complemento (en el centro de administración). </br> |
| \<DisplayName>| El título del complemento (en el centro de administración).|
| \<Hosts>| Lista de aplicaciones que admitirán el complemento.|
| \<> SourceLocation | La URL de origen a la que se conectará el complemento.| 
| \<AppDomain> | Una lista de dominios con los que se puede conectar el complemento. | 
| \<SupportURL>| La dirección URL que los usuarios pueden usar para tener acceso a ayuda y soporte técnico. | 
| \<Recursos>  | Esta etiqueta contiene un número de elementos que incluyen títulos, información sobre herramientas e iconos de diferentes tamaños.| 
|
### <a name="customize-resources-tag"></a>Personalizar etiqueta de recursos

Cualquier elemento de la <Resources> etiqueta del manifiesto se puede personalizar dinámicamente. Primero debe comprobar el manifiesto para encontrar el identificador de elemento al que desea asignar un nuevo valor. La <Resources> etiqueta tiene un aspecto similar a este:

```
<Resources>  
    <bt:Images> 
          <bt:Image id=”img16icon” DefaultValue=”http://site.com/img.jpg” 
    </bt:Images> 
</Resources> 
``` 
En este caso, el identificador de elemento de la imagen es "img16icon" y el valor asociado es "http:<i></i>//site. <i> </i>com/img. jpg. "

Una vez que haya identificado los elementos que desea personalizar, use el siguiente comando en PowerShell para asignar nuevos valores a los elementos:

```powershell
Set-OrganizationAddInOverrides -Resources @{“ElementID” = “New Value”; “NextElementID” = “Next New Value”} 
```

Puede personalizar tantos elementos con el comando como sea necesario.

### <a name="remove-customization-from-an-add-in"></a>Quitar la personalización de un complemento

La única opción disponible actualmente para eliminar personalizaciones es eliminar todas a la vez:

```powershell
Remove-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="view-add-in-customizations"></a>Ver personalizaciones de complementos

Para ver una lista de las personalizaciones aplicadas, ejecute el cmdlet **Get-OrganizationAddInOverrides** . Si **Get-OrganizationAddInOverrides** se ejecuta sin un *ProductID* , se devuelve una lista de todos los complementos con reemplazos aplicados.  

```powershell
Get-OrganizationAddInOverrides 
```
Si se especifica ProductId, se devuelve una lista de reemplazos aplicados a ese complemento. 

```powershell
Get-OrganizationAddInOverrides -ProductId 5b31b349-2c41-4f94-b720-6ee40349d391 
```

### <a name="remove-an-add-in-from-local-cache"></a>Quitar un complemento de la memoria caché local

Si se ha implementado un complemento, debe quitarse de la memoria caché en cada equipo antes de que se pueda personalizar. Para Remive un complemento de la memoria caché:

1. Navegue hasta la carpeta "usuarios" en C:\ 
1. Ir a la carpeta de usuario
1. Vaya a AppData\Local\Microsoft\Office y seleccione la carpeta asociada con su versión de Office.
1. En la carpeta *WEF* , elimine la carpeta *Manifests* .

## <a name="get-detailed-help-for-each-cmdlet"></a>Obtener ayuda detallada para cada cmdlet

Puede consultar la ayuda detallada para cada cmdlet mediante el cmdlet Get-Help. Por ejemplo, el siguiente cmdlet proporciona información detallada sobre el cmdlet Remove-OrganizationAddIn.
  
```powershell
Get-help Remove-OrganizationAddIn -Full
```


