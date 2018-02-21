---
title: Deshabilitar el acceso a servicios con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 02/13/2018
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
description: "Explica cómo utilizar Office 365 PowerShell para deshabilitar el acceso a los servicios de Office 365 para los usuarios de su organización."
ms.openlocfilehash: 61d92a1a0c55a381f10fedbb43403dd099fcb69b
ms.sourcegitcommit: 07416472be80566370c30631aff740177b37b24c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/19/2018
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Deshabilitar el acceso a servicios con PowerShell de Office 365

**Resumen:** Explica cómo utilizar Office 365 PowerShell para deshabilitar el acceso a los servicios de Office 365 para los usuarios de su organización.
  
Cuando una cuenta de Office 365 se asigna una licencia de un plan de licencias, los servicios de Office 365 están disponibles para el usuario de esa licencia. Sin embargo, puede controlar los servicios de Office 365 que tiene acceso el usuario. Por ejemplo, aunque la licencia permite el acceso a SharePoint Online, puede deshabilitar el acceso a él. De hecho, puede utilizar Office 365 PowerShell para deshabilitar el acceso a cualquier número de servicios para:

- Una cuenta individual.
    
- Un grupo de cuentas.
    
- Todas las cuentas de su organización.
    
## <a name="before-you-begin"></a>Antes de empezar
<a name="RTT"> </a>

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Utilice el cmdlet **Get-MsolAccountSku** para ver los planes de licencias disponibles y los servicios de Office 365 que están disponibles en dichos planes. Para obtener más información, vea [ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).
    
- Para ver el antes y después de los resultados de los procedimientos de este tema, vea [Ver detalles de licencia y servicio cuenta con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Hay un script de PowerShell que automatiza los procedimientos descritos en este tema. En concreto, el script le permite ver y deshabilitar servicios de la organización de Office 365, incluido Sway. Para obtener más información, consulte [Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Si utiliza el cmdlet **Get-MsolUser** sin utilizar el parámetro _All_ , se devuelven las primeras cuentas de usuario de 500.
    
## <a name="specific-office-365-services-for-specific-users-for-a-single-licensing-plan"></a>Servicios específicos de Office 365 para usuarios específicos para un único plan de licencias
  
Para deshabilitar un conjunto específico de servicios de Office 365 para los usuarios de un único plan de licencias, realice los pasos siguientes:
  
1. Identificar los servicios no deseados en el plan de licencias mediante la sintaxis siguiente:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    En el ejemplo siguiente se crea un objeto **LicenseOptions** que deshabilita los servicios de SharePoint Online y Office Online en el plan de licencia denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Utilice el objeto **LicenseOptions** del paso 1 en uno o más usuarios.
    
  - Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    En el ejemplo siguiente se crea una nueva cuenta para Allie Bellew que asigna la licencia y deshabilita los servicios descritos en el paso 1.
    
  ```
  New-MsolUser -UserPrincipalName allieb@litwareinc.com -DisplayName "Allie Bellew" -FirstName Allie -LastName Bellew -LicenseAssignment litwareinc:ENTERPRISEPACK -LicenseOptions $LO -UsageLocation US
  ```

    Para obtener más información acerca de cómo crear cuentas de usuario en Office 365 PowerShell, consulte [crear cuentas de usuario con Office 365 PowerShell](create-user-accounts-with-office-365-powershell.md).
    
  - Para deshabilitar los servicios para un usuario con licencia existente, use la siguiente sintaxis:
    
  ```
  Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $LO
  ```

    En este ejemplo se deshabilitan los servicios para el usuario BelindaN@litwareinc.com.
    
  ```
  Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $LO
  ```

  - Para deshabilitar los servicios descritos en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre de su plan de Office 365 desde la pantalla del cmdlet **Get-MsolAccountSku** (como **litwareinc:ENTERPRISEPACK**) y, a continuación, ejecute los comandos siguientes:
    
  ```
  $acctSKU="<AccountSkuId>"
  $AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
  $AllLicensed | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:
    
  - **Filtrar las cuentas basadas en un atributo de cuenta existente** Para ello, utilice la sintaxis siguiente:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
  $x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    En el ejemplo siguiente se deshabilita los servicios para los usuarios del departamento de ventas en los Estados Unidos.
    
  ```
  $USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US"
  $USSales | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

  - **Usar una lista de cuentas específicas** Para ello, siga estos pasos:
    
1. Cree un archivo de texto que contenga una cuenta en cada línea como en el ejemplo:
    
  ```
  akol@contoso.com
  tjohnston@contoso.com
  kakers@contoso.com
  ```

    En este ejemplo, el archivo de texto es C:\\documentos\\Accounts.txt.
    
2. Ejecute el comando siguiente:
    
  ```
  Get-Content "C:\My Documents\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Para deshabilitar los servicios de Office 365 para usuarios mientras se les va a asignar a un plan de licencias, vea [Deshabilitar el acceso a los servicios al asignar licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).
  
## <a name="specific-office-365-services-for-users-from-all-licensing-plans"></a>Servicios específicos de Office 365 para los usuarios de todos los planes de licencias
  
Para deshabilitar los servicios de Office 365 para los usuarios en todos los planes de licencias disponibles, siga estos pasos:
  
1. Copie y pegue este script en el Bloc de notas.
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
    Set-MsolUserLicense -UserPrincipalName <Account> -LicenseOptions $O365Licences
}
  ```

2. Personalice los valores siguientes para su entorno:
    
  -  _<UndesirableService>_En este ejemplo, vamos a utilizar SharePoint Online y Office Online.
    
  -  _<Account>_En este ejemplo, vamos a utilizar belindan@litwareinc.com.
    
    El script personalizado tiene el siguiente aspecto:
    
  ```
  $AllLicensingPlans = Get-MsolAccountSku
for($i = 0; $i -lt $AllLicensingPlans.Count; $i++)
{
    $O365Licences = New-MsolLicenseOptions -AccountSkuId $AllLicensingPlans[$i].AccountSkuId -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
    Set-MsolUserLicense -UserPrincipalName belindan@litwareinc.com -LicenseOptions $O365Licences
}
  ```

3. Guardar la secuencia de comandos `RemoveO365Services.ps1` en una ubicación que sea fácil de encontrar. Para este ejemplo, se va a guardar el archivo en `C:\\O365 Scripts`.
    
4. Ejecute la secuencia de comandos en Office 365 PowerShell utilizando el comando siguiente.
    
  ```
  & "C:\O365 Scripts\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Para invertir los efectos de uno de estos procedimientos (es decir, volver a habilitar los servicios deshabilitados), vuelva a ejecutar el procedimiento, pero utilice el valor `$null` para el parámetro _DisabledPlans_ .
  
[Volver al principio](disable-access-to-services-with-office-365-powershell.md#RTT)


## <a name="all-office-365-services-for-all-users-for-a-single-licensing-plan"></a>Todos los servicios de Office 365 para todos los usuarios de un plan individual de licencias
 
Para deshabilitar todos los servicios de Office 365 para todos los usuarios de un determinado plan de licencias, especifique el nombre de plan licencias para $acctSKU (como **litwareinc:ENTERPRISEPACK**) y, a continuación, ejecutar estos comandos en la ventana de comandos de PowerShell:

```
$acctSKU="<AccountSkuId>"
$servicesList=(Get-MsolAccountSku | Select -ExpandProperty ServiceStatus).ServicePlan.ServiceName
$lo = New-MsolLicenseOptions -AccountSkuId $acctSKU -DisabledPlans $servicesList
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -ObjectID $_.ObjectID -LicenseOptions $lo}
```

## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?
<a name="LinkedIn"> </a>

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]
   
## <a name="see-also"></a>Vea también
<a name="SeeAlso"> </a>

Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:
  
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear cuentas de usuario con PowerShell de Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Asignar licencias a cuentas de usuario con PowerShell de Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Crear cuentas de usuario con PowerShell de Office 365](create-user-accounts-with-office-365-powershell.md)
    
Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [Get-Content](https://go.microsoft.com/fwlink/p/?LinkId=289917)
    
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Nueva MsolLicenseOptions](https://go.microsoft.com/fwlink/p/?LinkId=691546)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [New-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
  

