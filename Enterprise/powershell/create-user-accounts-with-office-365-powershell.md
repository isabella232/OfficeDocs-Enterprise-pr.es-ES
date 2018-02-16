---
title: Crear cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- O365ITProTrain
ms.assetid: 6770c5fa-b886-4512-8c67-ffd53226589e
description: Aprenda a usar PowerShell de Office 365 para crear cuentas de usuario en Office 365.
ms.openlocfilehash: e5fed572d0b835a42071e77b4aeaf8714f2178bd
ms.sourcegitcommit: 07be28bd96826e61b893b9bacbf64ba936400229
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="create-user-accounts-with-office-365-powershell"></a>Crear cuentas de usuario con PowerShell de Office 365

**Resumen:** obtenga información sobre cómo usar PowerShell de Office 365 para crear cuentas de usuario en Office 365.
  
Puede usar PowerShell de Office 365 para crear de forma eficaz cuentas de usuario, especialmente varias cuentas de usuario. Al crear cuentas de usuario en PowerShell de Office 365, siempre se requieren determinadas propiedades de la cuenta. Otras propiedades no son necesarias para crear la cuenta, pero aun así son importantes. Estas propiedades se describen en la tabla siguiente:
  
****

|**Nombre de propiedad**|**Obligatorio**|**Descripción**|
|:-----|:-----|:-----|
|**DisplayName** <br/> |Sí  <br/> |Este es el nombre para mostrar que se usa en servicios de Office 365. Por ejemplo, Caleb Sills.  <br/> |
|**UserPrincipalName** <br/> |Sí  <br/> |Este es el nombre de cuenta que se usa para iniciar sesión en servicios de Office 365. Por ejemplo, CalebS@contoso.onmicrosoft.com.  <br/> |
|**FirstName** <br/> |No  <br/> ||
|**Apellidos** <br/> |No  <br/> ||
|**LicenseAssignment** <br/> |No  <br/> |Este es el plan de licencias (también conocido como plan de Office 365 o SKU) desde el que se asigna una licencia disponible a la cuenta de usuario. La licencia define los servicios de Office 365 que están disponibles para la cuenta. No tiene que asignar una licencia a un usuario al crear la cuenta, pero la cuenta requiere una licencia para tener acceso a los servicios de Office 365. Dispone de 30 días para conceder una licencia a la cuenta de usuario después de crearla.<br/> Use el cmdlet **Get-MsolAccountSku** para ver los planes de licencias (**AccountSkuId**) y las licencias disponibles en la organización. Para obtener más información, vea [Ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).  <br/> |
|**Password** <br/> |No  <br/> | Si no especifica una contraseña, se asignará una contraseña aleatoria a la cuenta de usuario y la contraseña será visible en los resultados del comando. Si especifica una contraseña, debe cumplir los siguientes requisitos de complejidad: <br/>  De 8 a 16 caracteres de texto ASCII. <br/>  Caracteres de tres de los tipos siguientes: letras minúsculas, letras mayúsculas, números y símbolos. <br/> |
|**UsageLocation** <br/> |No  <br/> |Se trata de un código de país válido ISO 3166-1 alpha-2. Por ejemplo, US para Estados Unidos y FR para Francia. Es importante proporcionar este valor, ya que algunos servicios de Office 365 no están disponibles en determinados países, por lo que no se puede asignar una licencia a una cuenta de usuario a menos que la cuenta tenga este valor configurado. Para obtener más información, consulte [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).<br/> |
   
## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
  
## <a name="use-office-365-powershell-to-create-individual-user-accounts"></a>Usar PowerShell de Office 365 para crear cuentas de usuario individuales

Para crear una cuenta individual, use la sintaxis siguiente:
  
```
New-MsolUser -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -LicenseAssignment <AccountSkuID> [-Password <Password>]
```

En este ejemplo se crea una cuenta para el usuario de Estados Unidos llamado Caleb Sills y se asigna una licencia desde el plan de licencias  `contoso:ENTERPRISEPACK` (Office 365 Enterprise E3).
  
```
New-MsolUser -DisplayName "Caleb Sills" -FirstName Caleb -LastName Sills -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -LicenseAssignment contoso:ENTERPRISEPACK
```

## <a name="use-office-365-powershell-to-create-multiple-user-accounts"></a>Usar PowerShell de Office 365 para crear varias cuentas de usuario

1. Cree un archivo de valores separados por comas (CSV) que contenga la información necesaria de la cuenta de usuario. Por ejemplo:
    
  ```
  UserPrincipalName,FirstName,LastName,DisplayName,UsageLocation,AccountSkuId
ClaudeL@contoso.onmicrosoft.com,Claude,Loiselle,Claude Loiselle,US,contoso:ENTERPRISEPACK
LynneB@contoso.onmicrosoft.com,Lynne,Baxter,Lynne Baxter,US,contoso:ENTERPRISEPACK
ShawnM@contoso.onmicrosoft.com,Shawn,Melendez,Shawn Melendez,US,contoso:ENTERPRISEPACK
  ```

 > [!NOTE]
>Los nombres de columna y su orden en la primera fila del archivo CSV son arbitrarios, pero asegúrese de que los datos del resto del archivo coincidan con el orden de los nombres de columna y use los nombres de columna para los valores de parámetro en el comando de PowerShell de Office 365.
    
2. Utilice la sintaxis siguiente:
    
  ```
  Import-Csv -Path <Input CSV File Path and Name> | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId [-Password $_.Password]} | Export-Csv -Path <Output CSV File Path and Name>
  ```

En este ejemplo se crean las cuentas de usuario a partir del archivo denominado C:\My Documents\NewAccounts.csv y se registran los resultados en el archivo denominado C:\My Documents\NewAccountResults.csv.
    
  ```
  Import-Csv -Path "C:\My Documents\NewAccounts.csv" | foreach {New-MsolUser -DisplayName $_.DisplayName -FirstName $_.FirstName -LastName $_.LastName -UserPrincipalName $_.UserPrincipalName -UsageLocation $_.UsageLocation -LicenseAssignment $_.AccountSkuId} | Export-Csv -Path "C:\My Documents\NewAccountResults.csv"
  ```

3. Revise el archivo de salida para ver los resultados. No se han especificado las contraseñas, por lo que las contraseñas aleatorias que se generaron son visibles en el archivo de salida.
    
## <a name="use-the-azure-active-directory-v2-powershell-module-to-create-individual-user-accounts"></a>Usar el módulo de PowerShell Azure Active Directory V2 para crear cuentas de usuario individuales

Para usar el cmdlet **New-AzureADUser** desde el módulo de PowerShell Azure Active Directory V2, primero tiene que conectarse a la suscripción. Para obtener instrucciones, vea [Conectarse con el módulo de PowerShell Azure Active Directory V2](https://go.microsoft.com/fwlink/?linkid=842218).
  
Después de haberse conectado, use la sintaxis siguiente para crear una cuenta individual:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="<user account password>"
New-AzureADUser -DisplayName <DisplayName> -GivenName <FirstName> -SurName <LastName> -UserPrincipalName <Account> -UsageLocation <CountryCode> -MailNickName <mailbox name> -PasswordProfile $PasswordProfile -AccountEnabled $true
```

En este ejemplo se crea una cuenta para el usuario de Estados Unidos llamado Caleb Sills:
  
```
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password="3Rv0y1q39/chsy"
New-AzureADUser -DisplayName "Caleb Sills" -GivenName "Caleb" -SurName "Sills" -UserPrincipalName calebs@contoso.onmicrosoft.com -UsageLocation US -MailNickName calebs -PasswordProfile $PasswordProfile -AccountEnabled $true
```
  
## <a name="see-also"></a>Consulte también

Vea estos temas adicionales sobre cómo administrar usuarios con PowerShell de Office 365:
  
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear cuentas de usuario con PowerShell de Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Asignar licencias a cuentas de usuario con PowerShell de Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Eliminar licencias de cuentas de usuario con PowerShell de Office 365](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [Export-Csv](https://go.microsoft.com/fwlink/p/?LinkId=113299)
    
- [Import-Csv](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.utility/import-csv)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [New-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/new-azureaduser?view=azureadps-2.0)
    

