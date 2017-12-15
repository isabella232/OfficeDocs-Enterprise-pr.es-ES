---
title: Deshabilitar el acceso a servicios con PowerShell de Office 365
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
- Ent_Office_Other
- PowerShell
- LIL_Placement
- DecEntMigration
ms.assetid: 264f4f0d-e2cd-44da-a9d9-23bef250a720
description: "Explica cómo utilizar Office 365 PowerShell para agregar o quitar el acceso a los servicios de Office 365 para los usuarios de la organización."
ms.openlocfilehash: a371e6adc482a3f21ebfacac08aff02daf4fd5b2
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="disable-access-to-services-with-office-365-powershell"></a>Deshabilitar el acceso a servicios con PowerShell de Office 365

**Resumen:** Explica cómo utilizar Office 365 PowerShell para agregar o quitar el acceso a los servicios de Office 365 para los usuarios de la organización.
  
Cuando una cuenta de Office 365 se asigna una licencia de un plan de licencias, los servicios de Office 365 están disponibles para el usuario de esa licencia. Sin embargo, puede controlar los servicios de Office 365 que tiene acceso el usuario. Por ejemplo, aunque la licencia permite el acceso a SharePoint Online, puede deshabilitar el acceso a él. De hecho, puede utilizar Office 365 PowerShell para deshabilitar el acceso a cualquier número de servicios para:
- Una cuenta individual.
    
- Un grupo de cuentas.
    
- Todas las cuentas de su organización.
    
 **Contenido:** [La versión corta (instrucciones sin las explicaciones)](disable-access-to-services-with-office-365-powershell.md#ShortVersion) [La versión larga (instrucciones con explicaciones detalladas)](disable-access-to-services-with-office-365-powershell.md#LongVersion) [Vea también](disable-access-to-services-with-office-365-powershell.md#SeeAlso)
## <a name="before-you-begin"></a>Antes de empezar
<a name="RTT"> </a>

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Utilice el cmdlet **Get-MsolAccountSku** para ver los planes de licencias disponibles y los servicios de Office 365 que están disponibles en dichos planes. Para obtener más información, vea[ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).
    
- Para ver el antes y después de los resultados de los procedimientos de este tema, vea [Ver detalles de licencia y servicio cuenta con Office 365 PowerShell](view-account-license-and-service-details-with-office-365-powershell.md).
    
- Hay un script de PowerShell que automatiza los procedimientos descritos en este tema. En concreto, el script le permite ver y deshabilitar servicios de la organización de Office 365, incluido Sway. Para obtener más información, consulte [Deshabilitar el acceso a Sway con Office 365 PowerShell](disable-access-to-sway-with-office-365-powershell.md).
    
- Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.
    
## <a name="the-short-version-instructions-without-explanations"></a>Versión corta (instrucciones sin explicaciones)
<a name="ShortVersion"> </a>

En esta sección se presentan los procedimientos sin explicaciones superfluas. Si tiene preguntas o desea obtener más información, puede leer el resto del tema.
  
Para deshabilitar los servicios de Office 365 para los usuarios de un único plan de licencias, realice los pasos siguientes:
  
1. Identificar los servicios no deseados en el plan de licencias mediante la sintaxis siguiente:
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId <AccountSkuId> -DisabledPlans "<UndesirableService1>", "<UndesirableService2>"...
  ```

    Este ejemplo crea un objeto **LicenseOptions** que deshabilita los servicios de SharePoint Online y Office Online en el plan de licencia denominado `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3).
    
  ```
  $LO = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
  ```

2. Utilice el objeto **LicenseOptions** del paso 1 en uno o más usuarios.
    
  - Para crear una nueva cuenta con los servicios deshabilitados, use la sintaxis siguiente:
    
  ```
  New-MsolUser -UserPrincipalName <Account> -DisplayName <DisplayName> -FirstName <FirstName> -LastName <LastName> -LicenseAssignment <AccountSkuId> -LicenseOptions $LO -UsageLocation <CountryCode>
  ```

    En este ejemplo se crea una nueva cuenta para Allie Bellew que asigna la licencia y deshabilita los servicios descritos en el paso 1.
    
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

  - Para deshabilitar los servicios descritos en el paso 1 para todos los usuarios con licencia existentes, especifique el nombre de su plan de Office 365 desde la pantalla del cmdlet **Get-MsolAccountSku** (como **litwareinc:ENTERPRISEPACK** ) y, a continuación, ejecute los comandos siguientes:
    
  ```
  $acctSKU="<AccountSkuId>"
$AllLicensed = Get-MsolUser -All | Where {$_.isLicensed -eq $true -and $_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1)}
$AllLicensed | ForEach {Set-MsolUserLicense -LicenseOptions $LO}
  ```

  - Para deshabilitar los servicios para un grupo de usuarios existentes, use cualquiera de los métodos siguientes para identificar a los usuarios:
    
  - **Filtrar las cuentas basadas en un atributo de cuenta existente** Para ello, utilice la sintaxis siguiente:
    
  ```
  $x = Get-MsolUser -All <FilterableAttributes>
$x | ForEach {Set-MsolUserLicense -UserPrincipalName $_.UserPrincipalName -LicenseOptions $LO}
  ```

    En este ejemplo se deshabilitan los servicios para los usuarios del Departamento de Ventas en Estados Unidos.
    
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
    
2. Ejecute el siguiente comando:
    
  ```
  Get-Content "C:\\My Documents\\Accounts.txt" | foreach {Set-MsolUserLicense -UserPrincipalName $_ -LicenseOptions $LO}
  ```

Para deshabilitar los servicios de Office 365 para usuarios mientras se les va a asignar a un plan de licencias, vea [Deshabilitar el acceso a los servicios al asignar licencias de usuario](disable-access-to-services-while-assigning-user-licenses.md).
  
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

3. Guardar la secuencia de comandos `RemoveO365Services.ps1` en una ubicación que sea fácil de encontrar. Para este ejemplo, se va a guardar el archivo en " `C:\\O365 Scripts`".
    
4. Ejecute la secuencia de comandos en Office 365 PowerShell utilizando el comando siguiente.
    
  ```
  &amp; "C:\\O365 Scripts\\RemoveO365Services.ps1"
  ```

> [!NOTE]
> Para invertir los efectos de uno de estos procedimientos (es decir, volver a habilitar los servicios deshabilitados), vuelva a ejecutar el procedimiento, pero utilice el valor `$null` para el parámetro _DisabledPlans_ .
  
[Volver al principio](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versión larga (instrucciones con explicaciones detalladas)
<a name="LongVersion"> </a>

De forma predeterminada, todos los servicios están habilitados cuando se emite una licencia mediante Office 365 PowerShell. Y a menudo es bueno: Esto significa que puede rápida y fácilmente asignar licencias a los usuarios sin tener que especificar que cada servicio esté habilitado en el camino.
  
Dicho esto, sin embargo, también es verdad que desea restringir los servicios disponibles algunos de los usuarios; Por ejemplo, tal vez algunos usuarios deben tener acceso a Office Professional Plus, Skype para los negocios en línea y en línea de Exchange, pero esos mismos usuarios no deberían tener acceso a SharePoint Online o a Office Online. ¿Puede restringir las cuentas de ese modo? Según parece, puede. Para ayudar a explicar cómo funciona esto, vamos a adoptar un enfoque de dos pasos para abordar este problema:
  
1. Asignar al usuario una licencia de Office 365 que habilita automáticamente todos los servicios.
    
2. Ejecutar un par de comandos de Office 365 PowerShell que deshabilitar servicios especificados para ese usuario.
    
Ya nos hemos tomado a cargo del paso 1: nuestro usuario (Belinda Newman) tiene una licencia de Office 365 que le proporciona acceso a todos los servicios de Office 365. Sin embargo, deseamos modificar cuenta de Belinda para que ella no tiene acceso a SharePoint Online ( `SHAREPOINTENTERPRISE`) o en Office Online ( `SHAREPOINTWAC`). Pero, ¿cómo se supone que debemos hacerlo?
  
Le mostramos cómo. Para comenzar con, vamos a utilizar el cmdlet **New-MsolLicenseOptions** para crear un objeto **LicenseOption** que contiene los servicios que queremos deshabilitados. En el caso de Belinda, que deseamos deshabilitar `SHAREPOINTENTERPRISE` y `SHAREPOINTWAC`, por eso usamos este comando:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

¿Para ver cómo funciona? Especificar el plan de licencia ( `litwareinc:ENTERPRISEPACK`) y, a continuación, indicar a cada uno de los servicios que desee deshabilitados, separar dichos servicios mediante comas.
  
> [!NOTE]
> Asegúrese de que el nuevo objeto de **LicenseOption** se almacena en una variable. En el ejemplo anterior, hemos utilizado `$x`, aunque se puede utilizar cualquier nombre válido de variable de Windows PowerShell. 
  
En este punto podemos utilizar el siguiente comando para deshabilitar el acceso a los dos servicios de Belinda:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Demasiado decorativo nada aquí, cualquiera: sólo llame el cmdlet **Set-MsolUserLicense** e incluya el parámetro _LicenseOptions_ , junto con la variable ( `$x`) que contiene los planes que deseamos deshabilitar. Y ¿qué vemos ahora si se Eche un vistazo a la información de licencia de Belinda ejecutando el comando: `(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus`? Esto es evidente:
  
```
ServicePlan                              ProvisioningStatus
-----------                              ------------------
SWAY                                     Success
INTUNE_O365                              Success
YAMMER_ENTERPRISE                        PendingInput
RMS_S_ENTERPRISE                         Success
OFFICESUBSCRIPTION                       Success
MCOSTANDARD                              Success
SHAREPOINTWAC                            Disabled
SHAREPOINTENTERPRISE                     Disabled
EXCHANGE_S_ENTERPRISE                    Success
```

Queda bien, ¿verdad? Y, por supuesto, podríamos hacer lo mismo a varios usuarios si deseáramos. Por ejemplo, estos comandos deshabilitar los mismos dos servicios para todos nuestros usuarios con licencia. Especificar el nombre de su plan de Office 365 desde la pantalla del cmdlet **Get-MsolAccountSku** (como **litwareinc:ENTERPRISEPACK** ) y, a continuación, ejecutarlas.
  
```
$acctSKU="<AccountSKU ID>"
Get-MsolUser | Where {$_.licenses[0].AccountSku.SkuPartNumber -eq ($acctSKU).Substring($acctSKU.IndexOf(":")+1, $acctSKU.Length-$acctSKU.IndexOf(":")-1) -and $_.IsLicensed -eq $True} | Set-MsolUserLicense -LicenseOptions $x
```

Tenga en cuenta que Belinda todavía tiene una licencia válida de Office 365; es sólo ahora tiene acceso a servicios de menos. Antes de que se deshabilitara los dos servicios, Belinda ha tenido acceso a suministros de noticias, OneDrive y SharePoint Online sitios:
  
![Usuario con acceso a SharePoint.](images/o365_powershell_with_sharepoint.png)
  
Ahora, esas opciones ya no están disponibles para ella:
  
![Usuario sin acceso a SharePoint.](images/o365_powershell_without_sharepoint.png)
  
Que es exactamente lo que esperábamos que sucediera.
  
Y ¿qué ocurre si cambiamos nuestra mente más adelante: ¿es posible volver a habilitar estos servicios? Por supuesto que sí que lo es. Para volver a habilitar todos los servicios de un usuario, utilizar este comando para crear el objeto **LicenseOption** siguiente:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

¿Qué hace este comando? Para empezar, la constante de Windows PowerShell `$null` significa "nada". (O, en lenguaje de ligeramente más técnico, significa "valor nulo".) Como recuerda, cuando usamos el cmdlet **New-MsolLicenseOptions** tenemos que indicar los servicios que queremos a deshabilitado. En este caso, no queremos que cualquiera de los servicios que se deshabilite. Que podría dar lugar a creer que podríamos usar un comando como el siguiente, un comando que no especificamos un valor para el parámetro _DisabledPlans_ :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans ""
```

Sin embargo, eso no funcionaría. En su lugar, genera un mensaje de error:
  
 `Set-MsolUserLicense : Cannot bind parameter 'LicenseOptions'. Cannot convert the "" value of type "System.String" to type "Microsoft.Online.Administration.LicenseOption".`
  
Afortunadamente para nosotros, establecer el valor del parámetro `$null` a trabajar:
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans $null
```

Esto significa simplemente que, cuando se ejecuta el cmdlet **Set-MsolUserLicense** , estamos diciendo **Conjunto MsolUserLicense** que no queremos que Belinda tenga los servicios deshabilitados:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -LicenseOptions $x
```

Y, como es lógico, si ninguno de los servicios se deshabilita, significa que todos los servicios están habilitados.
  
Ahora que entiende cómo funciona todo esto, le mostraremos cómo puede emitir una licencia y deshabilitar los servicios especificados y todos con el mismo comando. Eso suena bastante impresionante, pero, para ser sinceros, no hay realmente nada a ella: sólo incluye los parámetros _LicenseOptions_ y el _AddLicenses_ en el mismo comando. En otras palabras, primero cree el objeto **LicenseOption** :
  
```
$x = New-MsolLicenseOptions -AccountSkuId "litwareinc:ENTERPRISEPACK" -DisabledPlans "SHAREPOINTWAC", "SHAREPOINTENTERPRISE"
```

Y, a continuación, como se indicó anteriormente, utiliza los parámetros _LicenseOptions_ y el _AddLicenses_ en el comando:
  
```
Set-MsolUserLicense -UserPrincipalName BelindaN@litwareinc.com -AddLicenses "litwareinc:ENTERPRISEPACK" -LicenseOptions $x
```

Que comando emitirá Belinda Newman una licencia nueva, pero una licencia en qué Skype para los negocios en línea ( `SHAREPOINTWAC`) y SharePoint Online ( `SHAREPOINTENTERPRISE`) están ambos desactivados.
  
[Volver al principio](disable-access-to-services-with-office-365-powershell.md#RTT)
  
## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?
<a name="LongVersion"> </a>

||
|:-----|
|![El icono reducido de LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **¿Es la primera vez que usa Office 365?**         LinkedIn Learning pone a su disposición vídeos gratuitos de cursos de **Office 365 admins and IT pros**. |
   
## <a name="see-also"></a>See also
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
    
- [Nueva MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Conjunto de MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    
[Volver al principio](disable-access-to-services-with-office-365-powershell.md#RTT)
  

