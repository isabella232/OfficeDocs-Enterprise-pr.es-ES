---
title: Ver los usuarios con licencia y sin licencia con PowerShell de Office 365
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
- O365ITProTrain
- Ent_Office_Other
- PowerShell
ms.assetid: e4ee53ed-ed36-4993-89f4-5bec11031435
description: "Se explica cómo usar PowerShell de Office 365 para ver las cuentas de usuario con licencia y sin licencia."
ms.openlocfilehash: fe4f75d9d8dbc85efbc71856192dbaece3e84fbc
ms.sourcegitcommit: 9f1fe023f7e2924477d6e9003fdc805e3cb6e2be
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2018
---
# <a name="view-licensed-and-unlicensed-users-with-office-365-powershell"></a>Ver los usuarios con licencia y sin licencia con PowerShell de Office 365

**Resumen:** se explica cómo usar PowerShell de Office 365 para ver las cuentas de usuario con licencia y sin licencia.
  
Las cuentas de usuario de la organización de su Office 365 pueden tener algunas, todas o ninguna de las licencias disponibles asignadas a ellas desde los planes de licencias que están disponibles en su organización. Puede usar PowerShell de Office 365 para encontrar rápidamente los usuarios con licencia y sin licencia de la organización.
  
## <a name="before-you-begin"></a>Antes de empezar

- Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
    
- Si usa el cmdlet **Get-MsolUser** sin usar el parámetro _All_, solo se devuelven las 500 primeras cuentas.
    
## <a name="the-short-version-instructions-without-explanations"></a>Versión corta (instrucciones sin explicaciones)

En esta sección se presentan los procedimientos sin explicaciones superfluas. Si tiene preguntas o desea obtener más información, puede leer el resto del tema.
  
Para ver la lista de todas las cuentas de usuario y su estado de licencias en la organización, ejecute el comando siguiente en PowerShell de Office 365:
  
```
Get-MsolUser -All
```

Para ver la lista de todas las cuentas de usuario sin licencia de su organización, ejecute el comando siguiente:
  
```
Get-MsolUser -All -UnlicensedUsersOnly
```

Para ver la lista de todas las cuentas de usuario con licencia de su organización, ejecute el comando siguiente:
  
```
Get-MsolUser -All | where {$_.isLicensed -eq $true}
```

## <a name="the-long-version-instructions-with-detailed-explanations"></a>Versión larga (instrucciones con explicaciones detalladas)

Las cuentas de usuario de Office 365 y las licencias de Office 365 no necesitan tener una correspondencia de uno a uno: se pueden tener usuarios de Office 365 sin una licencia de Office 365 y, además, tener licencias de Office 365 que no estén asignadas a usuarios (de hecho, una sola cuenta de usuario puede, incluso, tener *varias* licencias de Office 365). Al crear una cuenta de usuario de Office 365 (para obtener más información, vea el artículo[Asignar licencias a usuarios de Office 365 con Windows PowerShell]((http://technet.microsoft.com/library/0ab9fcac-e5ea-4b5b-b72c-8c92c55565ac.aspx))), no es necesario asignar una licencia a ese usuario: el nuevo usuario tendrá una cuenta válida, pero no podrá iniciar sesión en Office 365. Si intenta iniciar sesión, verá algo parecido a esto:
  
![Usuario sin una licencia válida de Office 365.](images/o365_powershell_no_license.png)
  
Asimismo, puede tener un usuario que se tomará un tiempo libre prolongado, tal vez para un período sabático o para un permiso de maternidad o paternidad. En un caso como ese, se puede quitar la licencia del usuario y dejar la cuenta de usuario intacta (es decir, dejar todos los valores de propiedad, como la dirección y el número de teléfono, tal y como están). De esta forma, podría asignar esa licencia a otra persona como, por ejemplo, al trabajador temporal que sustituya a la persona que está de baja. Cuando el usuario vuelva a trabajar, le puede emitir una nueva licencia y podrá seguir trabajando como si nunca se hubiera ausentado.
  
Esto simplemente significa que, sí, es posible tener usuarios que tienen cuentas pero que no tienen licencias. O viceversa.
  
En el artículo [Ver las licencias y los servicios con PowerShell de Office 365](view-licenses-and-services-with-office-365-powershell.md) se explica cómo averiguar el número de licencias de Office 365 que ha adquirido la organización y cuántas de ellas se han asignado a usuarios. Esta información es muy importante. También lo es, sin embargo, saber quiénes tienen asignadas estas licencias y quiénes no. Y este artículo le explica cómo lograrlo.
  
Como probablemente sabrá, el cmdlet **Get-MsolUser** devuelve información sobre todas las cuentas de usuario de Office 365. ¿Necesita información rápida sobre todos los usuarios de Office 365? En ese caso, ejecute este comando en PowerShell de Office 365:
  
```
Get-MsolUser
```

A su vez, Get-MsolUser devuelve datos similares a estos:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BelindaN@litwareinc.com     Belinda Newman                  False
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

Como puede ver, uno de los valores de propiedad devueltos es el valor de la propiedad **isLicensed**. Si **isLicensed** es igual a `False`, significa que el usuario no tiene una licencia para Office 365. En otras palabras, si lo quisiera, simplemente podría desplazarse por la lista de usuarios y seleccionar aquellos en los que la propiedad **isLicensed** se establece en `False`.
  
En cualquier caso, desplazarse por una lista de usuarios para elegir a los usuarios sin licencia funciona siempre que tenga un número relativamente pequeño de usuarios. Si tiene un gran número de usuarios, desplazarse por la lista será, en el mejor de los casos, sumamente tedioso. (Y, según cómo se haya configurado Windows PowerShell, quizá imposible. Esto se debe a que existe un límite en cuanto a la cantidad de líneas de salida que se pueden mostrar en la consola de Windows PowerShell en cualquier momento).
  
Con eso en mente, una manera mucho mejor de hacer una lista de los usuarios sin licencia es ejecutar este comando:
  
```
Get-MsolUser -UnlicensedUsersOnly
```

Ese comando devuelve únicamente a los usuarios que no tienen una licencia para Office 365. En otras palabras:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
BelindaN@litwareinc.com     Belinda Newman                  False
```

Como puede ver, tenemos un usuario sin licencia. ¿Y si solo queremos una lista de los usuarios  *con licencia*  ? Eso es un poco más complicado, pero solo un poco:
  
```
Get-MsolUser | Where-Object {$_.isLicensed -eq $true}
```

Ese comando, que busca todas las cuentas de usuario donde la propiedad **isLicensed** es igual a `True`, devuelve información similar a la siguiente:
  
```
UserPrincipalName           DisplayName                     isLicensed
-----------------           -----------                     ----------
ZrinkaM@litwareinc.com      Zrinka Makovac                  True
BonnieK@litwareinc.com      Bonnie Kearney                  True
FabriceC@litwareinc.com     Fabrice Canel                   True
AnneW@litwareinc.com        Anne Wallace                    True
AlexD@litwareinc.com        Alex Darrow                     True
```

Como puede ver, no se devuelve ninguna información sobre Belinda Newman. ¿Por qué no? Acertó: porque la propiedad **isLicensed** para la cuenta de Belinda no está establecida en `True`.
  
## <a name="see-also"></a>Consulte también
<a name="SeeAlso"> </a>

Para obtener más información sobre los cmdlets que se usan en estos procedimientos, consulte los siguientes temas:
  
- [Get-MsolUser](https://go.microsoft.com/fwlink/p/?LinkId=691547)
    
- [Where-Object](https://go.microsoft.com/fwlink/p/?LinkId=113423)
    

