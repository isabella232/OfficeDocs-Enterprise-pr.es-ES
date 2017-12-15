---
title: Ver cuentas de usuario con PowerShell de Office 365
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
- LIL_Placement
- PowerShell
- apr17entnews
- Ent_Office_Other
- DecEntMigration
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Resumen: Ver, lista o mostrar las cuentas de usuario de varias maneras con Office 365 PowerShell.'
ms.openlocfilehash: b27f9045d26d4dabd3ada70766491f722d822a91
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Ver cuentas de usuario con PowerShell de Office 365

 **Resumen:** Ver, lista o mostrar las cuentas de usuario de varias maneras con Office 365 PowerShell.
  
Aunque puede utilizar el centro de administración de Office 365 para ver las cuentas de los inquilinos de Office 365, también puede utilizar Office 365 PowerShell y hacer algunas cosas que no puede el centro de administración de Office 365.
  
## <a name="before-you-begin"></a>Antes de empezar

Los procedimientos de este tema requieren conectarse a PowerShell de Office 365. Para obtener instrucciones, vea [Conectarse a PowerShell de Office 365](connect-to-office-365-powershell.md).
  
## <a name="display-office-365-user-account-information"></a>Mostrar información de la cuenta de usuario de Office 365

Para mostrar la lista completa de cuentas de usuario, ejecute este comando en el símbolo del sistema de Office 365 PowerShell o el entorno de secuencias de comandos integrado (ISE) de PowerShell.
  
```
Get-MsolUser
```

Verá información similar a esta:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
ZrinkaM@litwareinc.onmicrosoft.com    Zrinka Makovac        True
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

El cmdlet **Get-MsolUser** también tiene un conjunto de parámetros para filtrar el conjunto de cuentas de usuario que se muestran. Por ejemplo, para la lista de usuarios sin licencia (usuarios que han sido agregados a Office 365 pero aún no han ha autorizado para utilizar cualquiera de los servicios), ejecute este comando.
  
```
Get-MsolUser -UnlicensedUsersOnly
```

Verá información similar a esta:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Para obtener más información acerca de los parámetros adicionales para filtrar la visualización del conjunto de cuentas de usuario que se muestran, vea [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) .
  
Para ser más selectivo en cuanto a la lista de cuentas que desea mostrar, puede utilizar el cmdlet **Where-Object** en combinación con el cmdlet **Get-MsolUser** . Para combinar los dos cmdlets, utilizamos el carácter "barra vertical" "|", que indica a Office 365 PowerShell tomar los resultados de un comando y enviarlo al siguiente comando. Aquí es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Entre las llaves, el comando indica a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que el usuario UsageLocation cuenta propiedad ( ** $ \_. UsageLocation** ) no está especificado ( **-eq $Null** ).
    
Verá información similar a esta:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La propiedad **UsageLocation** es sólo una de las muchas propiedades asociadas a una cuenta de usuario. Para ver todas las propiedades de cuentas de usuario, utilice el cmdlet **Select-Object** y el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario específica. Éste es un ejemplo:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Por ejemplo, en esta lista, **la ciudad** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede utilizar el siguiente comando para enumerar todas las cuentas de usuario para los usuarios que viven en Londres:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintaxis para el cmdlet **Where-Object** se muestra en estos ejemplos es **Where-Object {$\_.** [nombre de propiedad de la cuenta de usuario] [operador] [valor] **}**. > [operador] es **-eq** para equals, **-ne** para no igual a, **-lt** para menor que **-gt** para mayor y otros > [valor] es normalmente una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$Null** para sin especifica > consulte [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obtener más información.
  
Puede comprobar el estado de bloqueo de cuenta de usuario con el siguiente comando:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select DisplayName,BlockCredential
```

## <a name="select-the-user-account-properties-to-display"></a>Seleccionar las propiedades de la cuenta de usuario que se van a mostrar

El cmdlet [Get-MsolUser](https://msdn.microsoft.com/library/azure/dn194133.aspx) de forma predeterminada muestra tres propiedades de cuentas de usuario:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Si tiene propiedades adicionales, como el departamento para que el usuario trabaja y el país o la región donde el usuario utiliza los servicios de Office 365, puede ejecutar **Get-MsolUser** en combinación con el cmdlet **Select-Object** para especificar la lista de cuenta de usuario Propiedades. Éste es un ejemplo:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, departamento, UsageLocation** ).
    
Verá información similar a esta:
  
```
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Zrinka Makovac          Sales & Marketing                    US
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
David Longmuir      Operations                               US
Scott Wallace            Operations
```

El cmdlet **Select-Object** le permite elegir las propiedades que desea que muestre un comando. Para ver todas las propiedades de cuentas de usuario, utilice el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario específica. Éste es un ejemplo:
  
```
Get-MsolUser -UserPrincipalName "BelindaN@litwareinc.onmicosoft.com" | Select-Object *
```

Para ser más selectivo en cuanto a la lista de cuentas que desea mostrar, puede también utilizar el cmdlet **Where-Object** . Aquí es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ) y enviar la información resultante con el siguiente comando ( **|** ). Entre las llaves, el comando es instruir a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que el usuario UsageLocation cuenta propiedad ( ** $ \_. UsageLocation** ) no está especificado ( **-eq $Null** ).
    
- Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, departamento, UsageLocation** ).
    
Verá información similar a esta:
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

## <a name="use-the-azure-active-directory-v2-powershell-module-to-display-user-accounts"></a>Usar el módulo de PowerShell Azure Active Directory V2 para mostrar cuentas de usuario

Para mostrar las propiedades de cuentas de usuario con el módulo de Active Directory V2 PowerShell de Azure, use el cmdlet [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser?view=azureadps-2.0) . Pero en primer lugar, debe conectarse a su suscripción. Para las instrucciones, vea[Conectar con el módulo de Active Directory V2 PowerShell de Azure](https://go.microsoft.com/fwlink/?linkid=842218).
  
### <a name="display-office-365-user-account-information"></a>Mostrar información de la cuenta de usuario de Office 365

Para mostrar la lista completa de cuentas de usuario, ejecute este comando en el símbolo del sistema de Office 365 PowerShell o el entorno de secuencias de comandos integrado (ISE) de PowerShell.
  
```
Get-AzureADUser
```

El cmdlet **Get-AzureADUser** de forma predeterminada muestra tres propiedades de cuentas de usuario:
  
- ObjectID
    
- DisplayName
    
- UserPrincipalName
    
Para ser más selectivo en cuanto a la lista de cuentas que desea mostrar, puede utilizar el cmdlet **Where-Object** en combinación con el cmdlet **Get-AzureADUser** . Para combinar los dos cmdlets, utilizamos el carácter "barra vertical" "|", que indica a Office 365 PowerShell tomar los resultados de un comando y enviarlo al siguiente comando. Aquí es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ). Entre las llaves, el comando indica a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que el usuario UsageLocation cuenta propiedad ( ** $ \_. UsageLocation** ) no está especificado ( **-eq $Null** ).
    
La propiedad **UsageLocation** es sólo una de las muchas propiedades asociadas a una cuenta de usuario. Para ver todas las propiedades de cuentas de usuario, utilice el cmdlet **Select-Object** y el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario, una página cada vez ( **más** ). Éste es un ejemplo:
  
```
Get-AzureADUser -ObjectID "BelindaN@litwareinc.onmicosoft.com" | Select-Object * | More
```

Por ejemplo, **Ciudad** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede utilizar el siguiente comando para enumerar todas las cuentas de usuario para los usuarios que viven en Londres:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintaxis para el cmdlet **Where-Object** se muestra en estos ejemplos es **Where-Object {$\_.** [nombre de propiedad de la cuenta de usuario] [operador] [valor] **}**. > [operador] es **-eq** para equals, **-ne** para no igual a, **-lt** para menor que **-gt** para mayor y otros > [valor] es normalmente una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$Null** para sin especifica > consulte[Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) para obtener más información.
  
### <a name="select-the-user-account-properties-to-display"></a>Seleccionar las propiedades de la cuenta de usuario que se van a mostrar

El cmdlet **Get-AzureADUser** de forma predeterminada muestra las propiedades UserPrincipalName, DisplayName y ObjectID de cuentas de usuario. Si tiene propiedades adicionales, como el departamento para que el usuario trabaja y el país o la región donde el usuario utiliza los servicios de Office 365, puede ejecutar **Get-AzureADUser** en combinación con el cmdlet **Select-Object** para especificar la lista de los usuarios propiedades de la cuenta. Éste es un ejemplo:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, departamento, UsageLocation** ).
    
Para ser más selectivo en cuanto a la lista de cuentas que desea mostrar, puede también utilizar el cmdlet **Where-Object** . Aquí es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Este comando indica a Office 365 PowerShell:
  
- Obtenga toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. UsageLocation - eq $Null}** ) y enviar la información resultante con el siguiente comando ( **|** ). Entre las llaves, el comando es instruir a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que el usuario UsageLocation cuenta propiedad ( ** $ \_. UsageLocation** ) no está especificado ( **-eq $Null** ).
    
- Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, departamento, UsageLocation** ).
    
## <a name="new-to-office-365"></a>¿Es la primera vez que usa Office 365?

||
|:-----|
|![El icono reducido de LinkedIn Learning](images/d547e1cb-7c66-422b-85be-7e7db2a9cf97.png) **¿Es la primera vez que usa Office 365?**         LinkedIn Learning pone a su disposición vídeos gratuitos de cursos de [Office 365 admins and IT pros](https://support.office.com/article/Office-365-admin-and-IT-pro-courses-68cc9b95-0bdc-491e-a81f-ee70b3ec63c5). |
   
## <a name="see-also"></a>See also

#### 

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

