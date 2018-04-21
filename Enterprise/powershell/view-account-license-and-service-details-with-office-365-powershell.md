---
title: Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/19/2018
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- PowerShell
- Ent_Office_Other
- LIL_Placement
ms.assetid: ace07d8a-15ca-4b89-87f0-abbce809b519
description: Explica cómo utilizar Office 365 PowerShell para determinar los servicios de Office 365 que se han asignado a los usuarios.
ms.openlocfilehash: 5286a581a67b39d5d5ca921b998d6ea14b3ff50f
ms.sourcegitcommit: 8ff1cd7733dba438697b68f90189d4da72bbbefd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="view-account-license-and-service-details-with-office-365-powershell"></a>Ver los detalles del servicio y la licencia de la cuenta con PowerShell de Office 365

**Resumen:** Explica cómo utilizar Office 365 PowerShell para determinar los servicios de Office 365 que se han asignado a los usuarios.
  
Licencias de Office 365, desde planes de licencias (también llamados SKU o Office 365 planes) proporcionar a los usuarios acceso a los servicios de Office 365 definidos para dichos planes. Sin embargo, un usuario no puede tener acceso a todos los servicios que están disponibles en una licencia que está actualmente asignada a ellos. Puede utilizar Office 365 PowerShell para ver el estado de los servicios en las cuentas de usuario. 

## <a name="before-you-begin"></a>Antes de empezar
<a name="RTT"> </a>

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Utilice los comandos `Get-MsolAccountSku` y `(Get-MsolAccountSku | where {$_.AccountSkuId -eq '<AccountSkuId>'}).ServiceStatus` para encontrar la siguiente información:
    
  - Los planes de licencias que están disponibles en su organización.
    
  - Los servicios que están disponibles en cada plan de licencias y el orden en que muestran (el número de índice).
    
     Para obtener más información acerca de las licencias de los planes, licencias y servicios, consulte [ver licencias y servicios con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md).
    
- Utilice el comando `Get-MsolUser -UserPrincipalName <user account UPN> | Format-List DisplayName,Licenses` para encontrar las licencias que se asignan a un usuario y el orden en que están enumerados (el número de índice).
    
- Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.
    
<a name="ShortVersion"> </a>
## <a name="the-short-version-instructions-without-explanations"></a>Versión corta (instrucciones sin explicaciones)

Para ver todos los servicios de Office 365 PowerShell que un usuario tiene acceso, utilice la siguiente sintaxis:
  
```
(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus
```

En este ejemplo se muestra los servicios a que tiene acceso el usuario BelindaN@litwareinc.com. Muestra los servicios que están asociados con todas las licencias asignados a su cuenta.
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses.ServiceStatus
```

En este ejemplo se muestran los servicios a los que tiene acceso la usuaria BelindaN@litwareinc.com a partir de la primera licencia asignada a su cuenta (el número de índice es 0).
  
```
(Get-MsolUser -UserPrincipalName belindan@litwareinc.com).Licenses[0].ServiceStatus
```

Para buscar todos los usuarios con licencia que están habilitados o no habilitados para servicios específicos, use la sintaxis siguiente:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled" -and $_.Licenses[<LicenseIndexNumber> ].ServiceStatus[<ServiceIndexNumber> ].ProvisioningStatus <-eq | -ne> "Disabled"...}
```

Estos ejemplos usan la información siguiente:
  
- La licencia que da acceso a los servicios de Office 365 que nos interesa es la primera que se asigna a todos los usuarios (el número de índice es 0).
    
- Los servicios de Office 365 que nos interesa son Skype para los negocios en línea y Exchange Online. Para las licencias que están asociadas con el plan de licencias, Skype para los negocios en línea es el servicio de 6 enumerado (el número de índice es 5), y Exchange Online es el servicio 9o enumerados (el número de índice es 8).
    
Este ejemplo devuelve con licencia de todos los usuarios habilitados para Skype para los negocios en línea y Exchange Online.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Este ejemplo devuelve todos los usuarios con licencia que no están habilitados para Skype en Exchange Online o negocios en línea.
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[5].ProvisioningStatus -eq "Disabled" -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

<a name="LongVersion"> </a>
## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versión larga (instrucciones con explicaciones detalladas)

### <a name="find-the-office-365-powershell-services-that-a-user-has-access-to"></a>Encontrar los servicios de Office 365 PowerShell que un usuario tenga acceso a

Es sin duda importante para saber los usuarios que se hayan expedido licencias de Office 365 y los usuarios que aún no. (Vea el artículo [Ver usuarios con licenciados como sin con Office 365 PowerShell](view-licensed-and-unlicensed-users-with-office-365-powershell.md) para obtener más información). Sin embargo, basta con tener una licencia de Office 365 no sabrá nada acerca de lo que el usuario realmente puede hacer con Office 365. ¿Él o ella sirve Exchange Online o Skype para los negocios en línea? ¿Puede este usuario tener acceso a SharePoint Online? ¿Él o ella tiene acceso a Office Professional Plus? Una licencia significa simplemente que el usuario tiene la posibilidad de tener acceso a estos servicios. Sin embargo, las capacidades disponibles para el usuario dependen de los servicios que se han habilitado en su licencia.
  
Entonces, ¿cómo podemos determinar qué características de Office 365 un usuario tiene acceso a? Para ello, es necesario ejecutar un comando similar a este:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Select-Object -ExpandProperty Licenses | Select-Object -ExpandProperty ServiceStatus
```

En este comando, estamos utilizando el cmdlet **Get-MsolUser** para devolver información sobre la cuenta BelindaN@litwareinc.com. Una vez que nos hemos devuelto esa información, luego canalizar los datos de la cuenta al cmdlet **Select-Object** y solicitar **Select-Object** "expandir" el valor de la propiedad de **licencias** :
  
 `Select-Object -ExpandProperty Licenses`
  
¿Por qué lo hacemos? Bueno, de forma predeterminada, las **licencias de** propiedad sólo nos indica el nombre del paquete de licencias licencia de Belinda procedencia:
  
```
Licenses
--------
{litwareinc:ENTERPRISEPACK}
```

La propiedad de **licencias** "expansión" nos da un poco más de información:
  
```
ExtensionData     AccountSku       AccountSkuId ServiceStatus
-------------     ----------       ------------ -------------
System.Runtime... Microsoft.On...  litwarein... {Microsoft.Online.A...
```

Y, a continuación, expandiendo la propiedad **ServiceStatus** , podemos obtener aún más información:
  
|****Plan de servicio****|****Descripción****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Empresarial Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plan 2 de Exchange Online  <br/> |
   
> [!NOTE]
> ¿Se dice que es demasiado escribiendo? Bueno, si usted puede poner con un poco obtusidad de Windows PowerShell, puede ejecutar esta versión condensada del comando en su lugar: >`(Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com).Licenses[0].ServiceStatus`
  
En caso de que se lo está preguntando, podemos "expandir" la propiedad de **licencias** porque **licencias** es una propiedad multivalor: es una sola propiedad que puede almacenar varios valores. Cuando se expande un valor de propiedad para que se desglosará simplemente obtener estos valores adicionales que, de forma predeterminada, no se muestran en la pantalla.
  
> [!NOTE]
> ¿Cómo se supone que sabe que un valor es una propiedad multivalor? Bien, para buscar que fuera, prueba ejecutando un comando similar a éste: > `Get-MsolUser -UserPrincipalName BelindaN@litwareinc.com | Get-Member`> el cmdlet **Get-member** devuelve información sobre el objeto en Sí; en este caso, información sobre la propiedad valores que componen un objeto de cuenta de usuario. Aquí está lo que **Get-Member** tiene que decir sobre la propiedad de **licencias** : > `Licenses Property System.Collections.Generic.List[Microsoft.On...`> Si la definición de propiedad dice algo sobre colecciones (en este caso, `System.Collections.Generic.List`), a continuación, sabrá que usted está tratando con una propiedad multivalor. 
  
Así que ¿qué significa todo esto? Para averiguarlo, primero echemos otro vistazo a la información devuelta por el cmdlet **Get-MsolUser** :
  
```
ServicePlan                       ProvisioningStatus
-----------                       ------------------
SWAY                              Success
INTUNE_O365                       Success
YAMMER_ENTERPRISE                 PendingInput
RMS_S_ENTERPRISE                  Success
OFFICESUBSCRIPTION                Success
MCOSTANDARD                       Success
SHAREPOINTWAC                     Success
SHAREPOINTENTERPRISE              Success
EXCHANGE_S_ENTERPRISE             Success
```

Y también Echemos un vistazo a una tabla que explica lo que representan realmente estos planes de servicio denominada de forma extraña:
  
|****Plan de servicio****|****Descripción****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Empresarial Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plan 2 de Exchange Online  <br/> |
   
¿Lo ha entendido todo?  `MCOSTANDARD` es simplemente un nombre de programación interno de Skype para los negocios en línea, mientras que `OFFICESUSBCRIPTION` es simplemente el nombre de programación interno para Office Professional Plus. No es la solución más intuitiva del mundo, pero mientras tenga esta tabla a mano no tendrá muchos problemas cuando se trata de trabajar con los servicios de Office 365.
  
Pero espere un momento: hay más. Como vimos en el artículo [servicios con Office 365 PowerShell y licencias de vista](view-licenses-and-services-with-office-365-powershell.md), si se establece la **ProvisioningStatus** en `Success` que significa que el servicio se ha habilitado totalmente; Por ejemplo si `MCOSTANDARD` se establece en `Success` que significa que el usuario puede tener acceso a Skype para los negocios en línea. Si se establece la **ProvisioningStatus** en `PendingInput` que significa que Office 365 todavía está procesando la solicitud de servicio; Sin embargo, el usuario puede iniciar sesión normalmente y tener acceso al servicio, mientras que la solicitud finalice el procesamiento. ( `YAMMER_ENTERPRISE` siempre se mostrarán como `PendingInput`, pero eso está bien: que no impedirá que un usuario inicie sesión en Yammer).
  
> [!IMPORTANT]
> Los usuarios pueden instalar y activar una nueva instalación de Office Professional Plus al `OFFICESUBSCRIPTION` en el `PendingInput` estado.
  
Y, evidentemente, es un servicio está configurado para `Disabled` que significa que el servicio en cuestión no está disponible para el usuario.
  

### <a name="find-users-that-have-access-to-specific-office-365-powershell-services"></a>Buscar los usuarios que tienen acceso a servicios específicos de Office 365 PowerShell

En un artículo independiente, vimos cómo puede utilizar Office 365 PowerShell para deshabilitar el acceso del usuario a los servicios. (Si se perdió ese artículo, vea [Deshabilitar el acceso a los servicios de Office 365 PowerShell](disable-access-to-services-with-office-365-powershell.md)). Esto nos lleva a una pregunta obvia: ¿hay alguna manera de determinar qué *usuarios* (es decir, más de un usuario) tiene los servicios que habilitan o deshabilitan?
  
Esperamos que alguien pediría. Para poder responder a esa pregunta, vamos a revisar la tabla de servicios que primero analizamos en el artículo [ver licencias y servicios con Office 365 PowerShell](view-licenses-and-services-with-office-365-powershell.md) para nuestro plan de licencias sólo está disponible `litwareinc:ENTERPRISEPACK`:
  
|****Plan de servicio****|****Descripción****|
|:-----|:-----|
| `SWAY` <br/> |Sway  <br/> |
| `TEAMS1` <br/> |Microsoft Teams  <br/> |
| `YAMMER_ENTERPRISE` <br/> |Yammer  <br/> |
| `RMS_S_ENTERPRISE` <br/> |Azure Rights Management (RMS)  <br/> |
| `OFFICESUBSCRIPTION` <br/> |Office Professional Plus  <br/> |
| `MCOSTANDARD` <br/> |Skype Empresarial Online  <br/> |
| `SHAREPOINTWAC` <br/> |Office Online  <br/> |
| `SHAREPOINTENTERPRISE` <br/> |SharePoint Online  <br/> |
| `EXCHANGE_S_ENTERPRISE` <br/> |Plan 2 de Exchange Online  <br/> |
   
Como quizá recuerde, el plan de servicio no es más que el nombre de programación interno de un producto; Por ejemplo, `OFFICESUBSCRIPTION`, a nombre de uno, es el nombre de programación interno para Office Professional Plus. Si `OFFICESUBSCRIPTION` se muestra como `SUCCESS` en el plan de servicio de un usuario, a continuación, que significa que el usuario puede tener acceso a Office Professional Plus. Si `EXCHANGE_S_ENTERPRISE` aparece como `DISABLED` que significa que el usuario no puede utilizar Exchange Online.
  
> [!IMPORTANT]
> Los usuarios pueden instalar y activar una nueva instalación de Office Professional Plus al `OFFICESUBSCRIPTION` en el `PendingInput` estado.
  
Ahora es el momento donde es muy importante el orden en que aparecen los servicios. Windows PowerShell se asigna un número de índice a cada entrada de la lista. La primera entrada es 0, la siguiente entrada es 1 y así sucesivamente. Los resultados se explican en la siguiente tabla:
  
|Número de índice ***|****Plan de servicio****|
|:-----|:-----|
|0  <br/> | `SWAY` <br/> |
|1  <br/> | `INTUNE_O365` <br/> |
|2  <br/> | `YAMMER_ENTERPRISE` <br/> |
|3  <br/> | `RMS_S_ENTERPRISE` <br/> |
|4  <br/> | `OFFICESUBSCRIPTION` <br/> |
|5  <br/> | `MCOSTANDARD` <br/> |
|6  <br/> | `SHAREPOINTWAC` <br/> |
|7  <br/> | `SHAREPOINTENTERPRISE` <br/> |
|8  <br/> | `EXCHANGE_S_ENTERPRISE` <br/> |
   
Como puede ver, `SWAY` es el primer servicio de la lista, por lo que se obtiene asignado el número de índice 0.
  
> [!CAUTION]
> ¿Por qué no 1 y 0? Es algo de programación. En lenguajes de programación índices indican hasta qué punto un elemento "offset" desde el principio de la matriz. El primer elemento *es* el principio de la matriz, por lo que su desplazamiento es 0. El segundo elemento es 1 artículo desde el principio de la matriz, por lo que su desplazamiento es 1.
  
Probemos un ejemplo. Supongamos que nos gustaría una lista de todos los usuarios con licencia que no se han habilitado para Exchange Online. Para ello, podemos utilizar el siguiente comando:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses[0].ServiceStatus[8].ProvisioningStatus -eq "Disabled"}
```

Hay que reconocer que es un comando poco aspecto críptico, así que vamos a tardar un minuto a explicar cómo funciona. Esto es realmente un comando de dos partes, y la primera parte es muy sencilla: utilizamos el cmdlet **Get-MsolUser** para devolver una colección de todos los usuarios de Office 365 (con licencia y sin licencia):
  
```
Get-MsolUser
```

Entonces, esa información se canaliza hacia el cmdlet **Where-Object** . **Where-Object** pasa por todas las cuentas de usuario y busca aquellas cuentas que los criterios siguientes cumplan:
  
- Es igual a la propiedad **isLicensed** ( `-eq`) `True` ( `$true`). Que nos permite descartar los usuarios sin licencia.
    
- El valor de las licencias de **[0]. ServiceStatus [8]. ProvisioningStatus** propiedad es igual a ( `-eq`) `Disabled`. Para nuestros fines inmediatas, la parte importante de este nombre de propiedad inmanejable es esto:
    
     `ServiceStatus[8]`
    
    El `[8]` representa el número de índice para Exchange Online. (Sabemos el análisis de la tabla hace unos minutos). ¿Qué pasaría si quisiéramos encontrar todos los usuarios habilitados para Skype para los negocios en línea? Bueno, el número de índice de Skype para los negocios en línea es 5, por lo que utilizaríamos esta sintaxis:
    
     `ServiceStatus[5]`
    
    Etc., etc.
    
    Por cierto, `Licenses[0]` indica el plan de licencias que queremos mirar. Dado que nuestro dominio de prueba sólo tiene un plan de licencias esto no importa mucho. Pero supongamos que tenemos un usuario que se ha asignado licencias desde dos planes de licencias diferentes. En ese caso, `Licenses[0]` representaría el primer plan de licencias, y `Licenses[1]` representaría el segundo plan de licencias.
    
    Para encontrar las licencias que están asignadas a un usuario y el orden en que se muestran, ejecute el comando siguiente:
    
  ```
  Get-MsolUser -UserPrincipalName <Account>  | Format-List DisplayName,Licenses
  ```

¿Puede ver cómo funciona todo esto? El número de índice para Office Professional Plus es 4; por lo tanto, este comando devuelve una lista de todos los usuarios que no han sido habilitados para Office Professional Plus:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -eq "Disabled"}
```

Y ¿qué ocurre si deseáramos obtener una lista de usuarios que han sido *habilitados* para Office Professional Plus? Bueno, si ya ha habilitado y será su **ServiceStatus** `PendingInput` o `Success`; en otras palabras, su **ServiceStatus** será igual *no* ( `-ne`) `Disabled`. Eso significa que todo lo que tenemos que hacer es tomar nuestro comando anterior e intercambiar el `-eq` operador para la `-ne` operador:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[4].ProvisioningStatus -ne "Disabled"}
```

Como se suele decir va, que código probablemente no gana muchos concursos de belleza. Y, verdad sea dicha, el código puede obtener incluso más complicada. Por ejemplo, supongamos que queremos buscar usuarios que se han habilitado para ambos Skype para los negocios en línea y Exchange Online:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true -and $_.Licenses.ServiceStatus[5].ProvisioningStatus -ne "Disabled" -and $_.Licenses.ServiceStatus[8].ProvisioningStatus -ne "Disabled"}
```

Pero no se preocupe demasiado sobre cómo más complicadas que podría ser: lo importante es que, con relativamente poco esfuerzo, puede recuperar esta información. ¿No se obtener en la misma información mediante el centro de administración de Office 365? En teoría, sí pero, en términos prácticos, no. Para llegar a la misma información mediante el centro de administración de Office 365, deberá mirar la información de licencia para cada usuario, un usuario a la vez, y entonces manualmente realizar un seguimiento de quién se ha habilitado para *X* y que no se habían. Que debería funcionar, pero seamos sinceros: si tiene más de 10 u 11 usuarios, no va a hacerlo. Es demasiado tediosas y lentas.
  
Que, por supuesto, es por eso que tenemos de Windows PowerShell: Windows PowerShell le ayuda a ahorrar de tareas tediosas y lentas como el.
  
Aquí es un ejemplo de un comando para la visualización de información de servicio de un conjunto especificado de servicios que se identifican por sus índices de licencias y ServiceStatus para una suscripción de Office 365 E5:
  
```
Get-MsolUser | Select-Object DisplayName, @{Name="Sway";Expression={$_.Licenses[0].ServiceStatus[12].ProvisioningStatus}}, @{Name="Teams";Expression={$_.Licenses[0].ServiceStatus[7].ProvisioningStatus}}, @{Name="Yammer";Expression={$_.Licenses[0].ServiceStatus[20].ProvisioningStatus}}, @{Name="AD RMS";Expression={$_.Licenses[0].ServiceStatus[19].ProvisioningStatus}}, @{Name="OfficePro";Expression={$_.Licenses[0].ServiceStatus[21].ProvisioningStatus}}, @{Name="Skype";Expression={$_.Licenses[0].ServiceStatus[22].ProvisioningStatus}}, @{Name="SharePoint";Expression={$_.Licenses[0].ServiceStatus[24].ProvisioningStatus}}, @{Name="Exchange";Expression={$_.Licenses[0].ServiceStatus[23].ProvisioningStatus}} | ConvertTo-CSV > "C:\Service Info.csv"
```

Este comando crea un archivo CSV que muestra todos los usuarios y sus Estados de servicio para un conjunto específico de servicios (equipos, Yammer, AD RMS, OfficePro, Skype, SharePoint y Exchange).

>[!Note]
>Puede obtener la lista de servicios en una suscripción desde el `(Get-MsolUser -UserPrincipalName <user account UPN>).Licenses[<LicenseIndexNumber>].ServiceStatus` comando. En el resultado, iniciar la numeración de los índices de servicio 0. El comando anterior es sólo un ejemplo. Los números de índice de servicios puede cambiar con el tiempo.
>

  
<a name="SeeAlso"> </a>
## <a name="see-also"></a>Consulte también

Vea los siguientes temas adicionales acerca de cómo administrar usuarios con Office 365 PowerShell:
  
- [Crear cuentas de usuario con PowerShell de Office 365](create-user-accounts-with-office-365-powershell.md)
    
- [Eliminar y restaurar cuentas de usuario con PowerShell de Office 365](delete-and-restore-user-accounts-with-office-365-powershell.md)
    
- [Bloquear cuentas de usuario con PowerShell de Office 365](block-user-accounts-with-office-365-powershell.md)
    
- [Asignar licencias a cuentas de usuario con PowerShell de Office 365](assign-licenses-to-user-accounts-with-office-365-powershell.md)
    
- [Eliminar licencias de cuentas de usuario con PowerShell de Office 365](remove-licenses-from-user-accounts-with-office-365-powershell.md)
    
Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [ConvertTo-Html](https://go.microsoft.com/fwlink/p/?LinkId=113290)
    
- [Format-List](https://go.microsoft.com/fwlink/p/?LinkId=113302)
    
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691543)
    
- [Select-Object](https://go.microsoft.com/fwlink/p/?LinkId=113387)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

  
## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?


[!INCLUDE [LinkedIn Learning Info](../common/office/linkedin-learning-info.md)]