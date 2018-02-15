---
title: Asignar licencias a cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_Office_Other, LIL_Placement, PowerShell, O365ITProTrain
ms.assetid: ba235f4f-e640-4360-81ea-04507a3a70be
description: "Se explica cómo usar PowerShell de Office 365 para asignar una licencia de Office 365 a los usuarios sin licencia."
ms.openlocfilehash: 11724e7f295079b76bbb9006bad1fb5487087bd8
ms.sourcegitcommit: c16db80a2be81db876566c578bb04f3747dbd50c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2018
---
# <a name="assign-licenses-to-user-accounts-with-office-365-powershell"></a>Asignar licencias a cuentas de usuario con PowerShell de Office 365

**Resumen:** se explica cómo usar PowerShell de Office 365 para asignar una licencia de Office 365 a los usuarios sin licencia.
  
Es importante asignar licencias a las cuentas de usuario de Office 365, ya que los usuarios no pueden usar ningún servicio de Office 365 hasta que su cuenta tenga una licencia. Puede usar PowerShell de Office 365 para asignar de forma eficiente licencias a cuentas sin licencia, especialmente a varias cuentas. 

## <a name="before-you-begin"></a>Antes de empezar
<a name="RTT"> </a>

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Use el cmdlet **Get-MsolAccountSku** para ver los planes de licencias disponibles y el número de licencias disponibles en cada plan de la organización. El número de licencias disponibles en cada plan es **ActiveUnits** - **WarningUnits** - **ConsumedUnits**. Para obtener más información sobre los planes de licencias, las licencias y los servicios, vea [Ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md).
    
- Para buscar las cuentas sin licencia de la organización, ejecute el comando `Get-MsolUser -All -UnlicensedUsersOnly`.
    
- Solo puede asignar licencias a cuentas de usuario que tengan la propiedad **UsageLocation** establecida en un código de país ISO 3166-1 alpha-2 válido. Por ejemplo, “US” para Estados Unidos y “FR” para Francia. Algunos servicios de Office 365 no están disponibles en determinados países. Para obtener más información, vea [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730).
    
    Para buscar cuentas que no tengan un valor **UsageLocation**, ejecute el comando `Get-MsolUser -All | where {$_.UsageLocation -eq $null}`. Para establecer el valor **UsageLocation** en una cuenta, utilice la sintaxis `Set-MsolUser -UserPrincipalName "<Account>" -UsageLocation <CountryCode>`. Por ejemplo, `Set-MsolUser -UserPrincipalName "belindan@litwareinc.com" -UsageLocation US`.
    
- Si usa el cmdlet **Get-MsolUser** sin el parámetro `-All`, solo se devuelven las 500 primeras cuentas.
    
## <a name="the-short-version-instructions-without-explanations"></a>Versión corta (instrucciones sin explicaciones)
<a name="ShortVersion"> </a>

En esta sección, se presentan los procedimientos sin explicaciones detalladas. Si tiene preguntas o quiere obtener más información, lea el resto del tema.
  
Para asignar una licencia a un usuario, use la sintaxis siguiente en PowerShell de Office 365:
  
```
Set-MsolUserLicense -UserPrincipalName "<Account>" -AddLicenses "<AccountSkuId>"
```

En este ejemplo, se asigna una licencia desde el plan de licencias `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) al usuario sin licencia `belindan@litwareinc.com`.
  
```
Set-MsolUserLicense -UserPrincipalName "belindan@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Para asignar una licencia a varios usuarios sin licencia, use la sintaxis siguiente:
  
```
$x = Get-MsolUser -All -UnlicensedUsersOnly [<FilterableAttributes>]; $x | foreach {Set-MsolUserLicense -AddLicenses "<AccountSkuId>"}
```

 **Notas**
  
- No se pueden asignar varias licencias a un usuario desde el mismo plan de licencias.
    
- Si no dispone de licencias suficientes, las licencias se asignan a los usuarios en el orden en que los devuelve el cmdlet **Get-MsolUser** hasta que se agoten las licencias disponibles.
    
En este ejemplo, se asignan licencias desde el plan de licencias `litwareinc:ENTERPRISEPACK` (Office 365 Enterprise E3) a todos los usuarios sin licencia.
  
```
$AllUn = Get-MsolUser -All -UnlicensedUsersOnly; $AllUn | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

En este ejemplo se asignan esas mismas licencias a los usuarios sin licencia del departamento de ventas de los Estados Unidos.
  
```
$USSales = Get-MsolUser -All -Department "Sales" -UsageLocation "US" -UnlicensedUsersOnly; $USSales | foreach {Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versión larga (instrucciones con explicaciones detalladas)
<a name="LongVersion"> </a>

Tal y como se explica en el artículo [Ver los usuarios con licencia y sin licencia con PowerShell de Office 365](view-licensed-and-unlicensed-users-with-office-365-powershell.md), se puede dar la situación de tener usuarios con cuentas de usuario de Office 365 válidas, pero para los que no se haya emitido una licencia de Office 365. Esto quiere decir que, con cuenta válida o sin ella, estos usuarios no podrán iniciar sesión en Office 365. Y, si no pueden iniciar sesión, tampoco podrán disfrutar de ninguno de los servicios de Office 365.
  
El citado artículo también señala que podemos devolver una lista de cuentas de usuario sin licencia mediante la ejecución de este comando:
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Este comando devuelve información sobre qué usuarios se encuentran actualmente sin licencia de Office 365:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

Como puede ver, tenemos un usuario sin licencia: Belinda Newman. ¿Cómo asignamos a Belinda una licencia de Office 365?
  
Para empezar, ejecutaremos el cmdlet **Get-MsolAccountSku**, que se describe en el artículo [Ver licencias y servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md):
  
```
Get-MsolAccountSku
```

El comando devuelve unos datos similares a estos:
  
```
AccountSkuId               ActiveUnits    WarningUnits   ConsumedUnits
------------               -----------    ------------   -------------
litwareinc:ENTERPRISEPACK  25             0              24
```

¿Por qué hemos ejecutado **Get-MsolAccountSku**? (“Sku”, en caso de que se lo esté preguntando, es la abreviatura en inglés de “referencia de almacén”. Para nuestros fines, es jerga comercial de “producto”). La ejecución de **Get-MsolAccountSku** responde a dos motivos. En primer lugar, debemos asegurarnos de que disponemos de una licencia para asignar a Belinda. ¿Tenemos licencias disponibles para asignar? Para averiguarlo, tomamos el valor de la propiedad **ActiveUnits** (25) y le restamos los valores de las propiedades **WarningUnits** (0) y **ConsumedUnits** (24):
  
 `25 - 0 - 24 = 1`
  
La propiedad **ActiveUnits** nos dice cuántas licencias hemos adquirido, y el valor combinado de **WarningUnits** y **ConsumedUnits** nos indica cuántas licencias están en uso actualmente. Si restamos el número de licencias asignadas al número de licencias adquiridas, sabremos cuántas licencias siguen estando disponibles. Por suerte, tenemos una licencia disponible para su distribución:
  
 `25 - 0 - 24 = 1`
  
En segundo lugar, para poder asignar una nueva licencia a Belinda, necesitamos saber el nombre de nuestro plan de licencias (es decir, necesitamos conocer el **AccountSkuId**). En este caso, es fácil: solo tenemos un único plan de licencias (`litwareinc:ENTERPRISEPACK`). Sin embargo, tenga en cuenta que una organización puede tener varios planes de licencias. En ese caso, **Get-MsolAccountSku** devuelve dos **AccountSkuIds** diferentes, y tendrá que elegir el plan de licencias correspondiente al asignar licencias. Por ahora, sin embargo, vamos a seguir con el caso más sencillo y suponer que hay un solo plan de licencias.
  
Entonces, *¿cómo* asignamos a Belinda Newman una nueva licencia? Así:
  
```
Set-MsolUserLicense -UserPrincipalName "BelindaN@litwareinc.com" -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Esto es lo que tiene que hacer: simplemente llame al cmdlet **Set-MsolUserLicense**, asegurándose de especificar el parámetro _UserPrincipalName_ para el usuario y el plan de licencias correspondiente.
  
Cuando **Set-MsolUserLicense** termine de ejecutarse, verá algo parecido a esto en la pantalla:
  
 `PS C:\\windows\\system32>`
  
En otras palabras, parecerá que no sucedió nada. Para comprobar que se asignó una licencia al usuario, ejecute un comando como el siguiente:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com"
```

Si todo funcionó como se esperaba, debería ver que la propiedad isLicensed de Belinda ahora se establece en “true”:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  True
```

> [!SECURITY NOTE] Y ahora una buena pregunta: ¿qué pasa si comete un error e intenta asignar una licencia a un usuario que ya tiene una? ¿Acabará concediendo dos licencias a un solo usuario? > ¿La respuesta rápida? No; Office 365 no le permitirá asignar más de una licencia al mismo usuario. (Es decir, no le permitirá asignar más de una licencia del mismo plan de licencias). Si intenta hacerlo, se producirá un error en el comando con el siguiente mensaje de error: > `Set-MsolUserLicense : Unable to assign this license because it is invalid. Use the Get-MsolAccountSku cmdlet to retrieve a list of valid licenses.` > Ciertamente, ese mensaje de error es un poco engañoso: no es que la licencia no sea válida, es que se asignó a un usuario que ya *tiene* una licencia. Pero, dejando de lado el mensaje de error, lo importante es que un usuario no acabe con varias licencias.
  
Como ha visto, es muy fácil usar PowerShell de Office 365 para asignar una única licencia a un único usuario. Y esto nos lleva a una pregunta obvia: ¿no sería igual de fácil, o quizás aún más fácil, usar el Centro de administración de Office 365 para asignar una única licencia a un único usuario? Bueno, quizá; eso depende, en parte, de si se siente más cómodo usando Windows PowerShell o usando el Centro de administración de Office 365. Sin embargo, donde Windows PowerShell realmente destaca es cuando hay que asignar varias licencias a varios usuarios. Por ejemplo, este comando asigna una licencia de Office 365 a cualquiera de los usuarios que aún no tienen una licencia:
  
```
Get-MsolUser -All -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

En el comando anterior, usamos **Get-MsolUser** y el parámetro _UnlicensedUsersOnly_ para devolver una colección de todas las cuentas de usuario sin licencia. Después pasamos esa colección al cmdlet **Set-MsolUserLicense**. A su vez, **Set-MsolUserLicense** asigna una licencia (tomada del plan de licencias de `litwareinc:ENTERPRISEPACK`) a cada usuario de la colección.
  
Pero ¿qué sucede si tiene 5 usuarios sin licencia y solo una licencia disponible? En ese caso, **Set-MsolUserLicense** concederá la licencia disponible al primer usuario devuelto por **Get-MsolUser**. **Set-MsolUserLicense** intentará diligentemente asignar una licencia a los otros cuatro usuarios, pero los cuatro intentos generarán un error junto con el siguiente mensaje:
  
 `Set-MsolUserLicense : Unable to assign this license because the number of allowed licenses have been assigned.`
  
En otras palabras, el cmdlet MsolUserLicense no solo fallará ahí. Intentará asignar tantas licencias como sea posible. Será entonces cuando se produzca el error.
  
Vamos a poner otro ejemplo. Supongamos que quiere asignar una licencia a todos los usuarios del departamento de ventas. Pan comido:
  
```
Get-MsolUser -All -Department "Sales" | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

O bien, si realmente quiere ponerse sofisticado, y quiere mantener los mensajes de error y el procesamiento informático al mínimo, limítese a asignar una licencia a los usuarios sin licencia del departamento de ventas:
  
```
Get-MsolUser -All -Department "Sales" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Después de todo, no tiene ningún sentido tratar de conceder licencias a los usuarios que ya disponen de una. Como ya hemos visto, no funcionará.
  
Este es otro ejemplo. Tal vez le gustaría conceder licencias a todos los usuarios de EE. UU. que actualmente no cuentan con una licencia de Office 365. En ese caso:
  
```
Get-MsolUser -All -UsageLocation "US" -UnlicensedUsersOnly | Set-MsolUserLicense -AddLicenses "litwareinc:ENTERPRISEPACK"
```

Y así sucesivamente.
  
> [!NOTE]
> ¿Cuánto tiempo se necesita para ejecutar un comando que, por ejemplo, emita licencias para todos los usuarios sin licencia? Es difícil de responder: depende de todo, desde el número de usuarios que tenga hasta la velocidad de la conexión de red. Si tiene que conceder licencias a unos cientos de usuarios, será razonablemente rápido (es decir, no debería tardar más de uno o dos minutos). Si tiene que conceder licencias a 10 000 usuarios, obviamente tardará un poco más. Pero no tardaría tanto tiempo como en el caso de querer asignar licencias a 10 000 usuarios mediante el Centro de administración de Office 365. 
  
Y, ya que estamos tratando este asunto, es importante resaltar algo con lo que debemos tener cuidado al asignar licencias: si un usuario no tiene un valor configurado para la propiedad **UsageLocation**, no podrá asignarle a dicho usuario una licencia de Office 365. En su lugar, recibirá un mensaje de error similar al siguiente:
  
 `Set-MsolUserLicense : You must provide a required property: Parameter name: UsageLocation`
  
De una manera un poco indirecta, este mensaje de error indica que el usuario en cuestión no tiene asignada la propiedad **UsageLocation**. Como habrá adivinado, la propiedad **UsageLocation** (que indica la región o el país en el que el usuario suele usar Office 365) es extremadamente importante. ¿Por qué? Porque los servicios disponibles para un usuario dependen no solo del paquete de licencias que haya adquirido, sino también del lugar en el que viva el usuario. Debido a reglas y normativas locales, algunos servicios tal vez no estén disponibles para algunos usuarios. Si un usuario no tiene **UsageLocation**, Office 365 no tiene manera de saber qué servicios pueden exponerse legalmente a dicho usuario. Por lo tanto, Office 365 no puede ofrecer servicios a dicho usuario, al menos no hasta que se haya especificado la propiedad **UsageLocation**.
  
> [!NOTE]
> Al configurar una cuenta de usuario, sabrá inmediatamente si hay restricciones de licencia asociadas a una parte determinada del mundo. Por ejemplo, si cambia la propiedad **UsageLocation** de un usuario con licencia a Irán (`IR`), se producirá un error en el comando con este mensaje de error: `Set-MsolUser : Unable to update license for this user. One or more of the assigned service plans is not available in this user's country. Prohibited Service Plans: EXCHANGE_S_ENTERPRISE, SHAREPOINTENTERPRISE, SHAREPOINTWAC, MCOSTANDARD, OFFICESUBSCRIPTION, RMS_S_ENTERPRISE. Specific service plans can be disabled for a user by using the licenseoptions parameter.` > Esto se debe a que Office 365 no está disponible actualmente para los usuarios de Irán. Para obtener más información, vea [Sobre las restricciones de licencia](https://go.microsoft.com/fwlink/p/?LinkId=691730). Por cierto, Office 365 usa los códigos de país de dos letras producidos por la Organización Internacional de Normalización (ISO). Encontrará dichos códigos en el [sitio web de ISO](https://go.microsoft.com/fwlink/p/?LinkId=84073). 
  
Si quiere comprobar si un usuario determinado tiene una propiedad **UsageLocation**, puede usar un comando similar a este:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.com" | Select-Object UsageLocation
```

Como alternativa, puede devolver una lista de todos los usuarios que no tienen una propiedad **UsageLocation** con este comando:
  
```
Get-MsolUser -All | Where-Object {$_.UsageLocation -eq $null}
```

> [!NOTE]
> Al asignar una licencia a un usuario, este tendrá acceso de forma predeterminada a todos los servicios de Office 365 a los que tenga acceso la organización. Por ejemplo, si compró licencias de Office 365 Enterprise E3, el usuario al que asignó la licencia tendrá acceso de forma automática a servicios como Exchange Online, Skype Empresarial Online y SharePoint Online. Si prefiere limitar el acceso de un usuario a dichos servicios (por ejemplo, que tenga acceso a SharePoint Online, pero *no* a Exchange Online ni Skype Empresarial Online), vea el artículo [Deshabilitar el acceso a servicios con PowerShell de Office 365](disable-access-to-services-with-office-365-powershell.md). 
  
## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?

[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]

## <a name="see-also"></a>Vea también
<a name="SeeAlso"> </a>

Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:
  
- [Crear cuentas de usuario con PowerShell de Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear cuentas de usuario con PowerShell de Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Eliminar licencias de cuentas de usuario con PowerShell de Office 365](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [Get-MsolAccountSku](https://go.microsoft.com/fwlink/p/?LinkId=691549)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Set-MsolUserLicense](https://go.microsoft.com/fwlink/p/?LinkId=691548)
    
- [ForEach-Object](https://go.microsoft.com/fwlink/p/?LinkId=113300)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

