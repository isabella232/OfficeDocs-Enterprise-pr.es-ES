---
title: Eliminar licencias de cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/12/2020
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
- PowerShell
- Ent_Office_Other
- LIL_Placement
- O365ITProTrain
ms.assetid: e7e4dc5e-e299-482c-9414-c265e145134f
description: Explica cómo usar Office 365 PowerShell para quitar licencias de Office 365 que se han asignado anteriormente a los usuarios.
ms.openlocfilehash: 4a99fb115b7c3241beb2cb3b0dd83666622747d5
ms.sourcegitcommit: dce58576a61f2c8efba98657b3f6e277a12a3a7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208761"
---
# <a name="remove-licenses-from-user-accounts-with-office-365-powershell"></a>Eliminar licencias de cuentas de usuario con PowerShell de Office 365

## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

A continuación, enumere los planes de licencia para el inquilino con este comando.

```powershell
Get-AzureADSubscribedSku | Select SkuPartNumber
```

A continuación, obtenga el nombre de inicio de sesión de la cuenta para la que desea quitar una licencia, también conocido como nombre principal de usuario (UPN).

Por último, especifique los nombres de inicio de sesión y de plan de licencias de usuario, quite los caracteres "<" y ">" y ejecute estos comandos.

```powershell
$userUPN="<user sign-in name (UPN)>"
$planName="<license plan name from the list of license plans>"
$license = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$licenses = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$license.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
$licenses.AddLicenses = $license
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
$Licenses.AddLicenses = @()
$Licenses.RemoveLicenses =  (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value $planName -EQ).SkuID
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $licenses
```

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).
   
Para ver la información del plan de licencias (**AccountSkuID**) de su organización, vea los temas siguientes:
    
  - [Ver las licencias y los servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md)
    
  - [Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365](view-account-license-and-service-details-with-office-365-powershell.md)
    
Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.
    
### <a name="removing-licenses-from-user-accounts"></a>Quitar licencias de cuentas de usuario

Para quitar licencias de una cuenta de usuario existente, utilice la sintaxis siguiente:
  
```powershell
Set-MsolUserLicense -UserPrincipalName <Account> -RemoveLicenses "<AccountSkuId1>", "<AccountSkuId2>"...
```

>[!Note]
>PowerShell Core no es compatible con el Módulo Microsoft Azure Active Directory para Windows PowerShell ni los cmdlet que llevan **Msol** en su nombre. Para seguir usando estos cmdlets, debe ejecutarlos desde Windows PowerShell.
>

En este ejemplo se quita la licencia **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de la cuenta de usuario BelindaN@litwareinc.com.
  
```powershell
Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -RemoveLicenses "litwareinc:ENTERPRISEPACK"
```

>[!Note]
>No puede usar el `Set-MsolUserLicense` cmdlet para anular la asignación de usuarios de licencias *canceladas* . Debe hacerlo de forma individual para cada cuenta de usuario en el centro de administración de Microsoft 365.
>

Para quitar todas las licencias de un grupo de usuarios con licencia existentes, use uno de los métodos siguientes:
  
- **Filtrar las cuentas basándose en un atributo de cuenta existente** Para ello, use la sintaxis siguiente:
    
```powershell
$userArray = Get-MsolUser -All <FilterableAttributes> | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

En este ejemplo se quitan todas las licencias de todas las cuentas de usuario del Departamento de ventas de Estados Unidos.
    
```powershell
$userArray = Get-MsolUser -All -Department "Sales" -UsageLocation "US" | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

- **Usar una lista de cuentas específicas para una licencia específica** Para ello, siga estos pasos:
    
1. Cree y guarde un archivo de texto que contenga una cuenta en cada línea de esta manera:
    
  ```powershell
akol@contoso.com
tjohnston@contoso.com
kakers@contoso.com
  ```

2. Utilice la sintaxis siguiente:
    
  ```powershell
  Get-Content "<FileNameAndPath>" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "<AccountSkuId>" }
  ```

En este ejemplo se quita la licencia **litwareinc: ENTERPRISEPACK** (Office 365 Enterprise E3) de las cuentas de usuario definidas en el archivo de texto c:\Mis documentos\cuentas.txt.
    
  ```powershell
  Get-Content "C:\My Documents\Accounts.txt" | ForEach { Set-MsolUserLicense -UserPrincipalName $_ -RemoveLicenses "litwareinc:ENTERPRISEPACK" }
  ```

Para quitar todas las licencias de todas las cuentas de usuario existentes, use la siguiente sintaxis:
  
```powershell
$userArray = Get-MsolUser -All | where {$_.isLicensed -eq $true}
for ($i=0; $i -lt $userArray.Count; $i++)
{
Set-MsolUserLicense -UserPrincipalName $userArray[$i].UserPrincipalName -RemoveLicenses $userArray[$i].licenses.accountskuid
}
```

Otra forma de liberar una licencia consiste en eliminar la cuenta de usuario. Para obtener más información, vea [eliminar y restaurar cuentas de usuario con Office 365 PowerShell](delete-and-restore-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>Vea también

[Administrar cuentas de usuario, licencias y grupos con Office 365 PowerShell](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

