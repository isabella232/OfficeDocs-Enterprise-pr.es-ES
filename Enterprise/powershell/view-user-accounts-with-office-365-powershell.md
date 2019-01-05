---
title: Ver cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 01/03/2019
ms.audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Resumen: Ver, lista o mostrar las cuentas de usuario de varias formas con PowerShell de Office 365.'
ms.openlocfilehash: e95353602b96babe5c80f7d57462370636dd26fa
ms.sourcegitcommit: a39d15b7cf758dfb262d2724bcfd283bba3d2ce1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2019
ms.locfileid: "27730325"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Ver cuentas de usuario con PowerShell de Office 365

**Resumen:** Ver las cuentas de usuario de varias formas con PowerShell de Office 365.
  
Aunque puede usar el centro de administración de Office 365 para ver las cuentas para el inquilino de Office 365, también puede usar PowerShell de Office 365 y hacer cosas que no se puede el centro de administración de Office 365.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Ver todas las cuentas

Para mostrar la lista completa de las cuentas de usuario, ejecute este comando:
  
```
Get-AzureADUser
```

Verá información similar a esta:
  
```
ObjectId                             DisplayName                                           UserPrincipalName
--------                             -----------                                           -----------------
032fc1fc-b5a2-46f1-8635-3d7dcb52c48d Adele Vance                                           AdeleV@litwareinc.OnMicr...
bd1e6af1-41e7-4f77-a2ac-5b209950135c Global Administrator                                  admin@litwareinc.onmicro...
ec37a4d6-232e-4eb7-82a5-1613490642a5 Alex Wilber                                           AlexW@litwareinc.OnMicro...
be4bdddd-c790-424c-9f96-a0cf609b7815 Allan Deyoung                                         AllanD@litwareinc.OnMicr...
598ab87b-76f0-4bf9-9538-bd46b10f4438 Christie Cline                                        ChristieC@litwareinc.OnM...
40722671-e520-4a5f-97d4-0bc9e9b2dc0f Debra Berger                                          DebraB@litwareinc.OnMicr...
```

### <a name="view-a-specific-account"></a>Ver una cuenta específica

Para mostrar una cuenta de usuario específica, quitar relleno en el nombre de inicio de sesión de la cuenta de la cuenta de usuario, también conocido como el nombre principal de usuario (UPN), el "<" y ">" caracteres y ejecute este comando:
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Aquí le mostramos un ejemplo:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Ver los valores de propiedad adicionales de una cuenta específica

De forma predeterminada, el cmdlet **Get-AzureADUser** solo muestra las propiedades ObjectID, DisplayName y UserPrincipalName de cuentas.

Para que sea más selectivos acerca de la lista de propiedades para mostrar, puede usar el cmdlet **Select-Object** en combinación con el cmdlet **Get-AzureADUser** . Para combinar los dos cmdlets, usamos el carácter "barra vertical" "|", que indica a Azure Active Directory PowerShell para gráfico para tomar los resultados de un comando y volver a enviar con el siguiente comando. Este es un comando de ejemplo que muestra el DisplayName, el departamento y la propiedad UsageLocation para cada cuenta de usuario:
  
```
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, el departamento, la propiedad UsageLocation** ).
  
Para ver todas las propiedades para las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario específica. Este es un ejemplo:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Como otro ejemplo, puede comprobar el estado habilitado de una cuenta de usuario específica con el siguiente comando:
  
```
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Ver algunas cuentas en función de una propiedad común

Para que sea más selectivos acerca de la lista de cuentas para mostrar, puede usar el cmdlet **Where-Object** en combinación con el cmdlet **Get-AzureADUser** . Para combinar los dos cmdlets, usamos el carácter "barra vertical" "|", que indica a Azure Active Directory PowerShell para gráfico para tomar los resultados de un comando y volver a enviar con el siguiente comando. Este es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:
  
```
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando indica a Azure Active Directory PowerShell para gráfico para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-AzureADUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. Propiedad UsageLocation - eq $Null}** ). Entre las llaves, el comando indica a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que la propiedad UsageLocation cuenta de usuario (propiedad) ( ** $ \_. Propiedad UsageLocation** ) no está especificado ( **-eq $Null** ).
    
La propiedad de la **propiedad UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario. Para ver todas las propiedades para las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario específica. Este es un ejemplo:
  
```
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:
  
```
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintaxis para el cmdlet **Where-Object** , que se muestra en estos ejemplos es **Where-Object {$\_.** [nombre de propiedad de la cuenta de usuario] [operador de comparación] [valor] **}**. > [operador de comparación] es **-eq** para es igual a, **-ne** para no es igual a, **-lt** para menor que **-gt** para mayor y otros usuarios.  [valor] es normalmente una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$Null** para que no se especifica > vea [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) para obtener más información.
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Ver todas las cuentas

Para mostrar la lista completa de las cuentas de usuario, ejecute este comando:
  
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

El cmdlet **Get-MsolUser** también tiene un conjunto de parámetros para filtrar el conjunto de cuentas de usuario que se muestra. Por ejemplo, para la lista de los usuarios sin licencia (los usuarios que se han añadido a Office 365, pero aún no han se ha licencia para usar cualquiera de los servicios), ejecute este comando.
  
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

Para obtener más información acerca de los parámetros adicionales para filtrar la visualización del conjunto de cuentas de usuario que se muestra, vea [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  

### <a name="view-a-specific-account"></a>Ver una cuenta específica

Para mostrar una cuenta de usuario específica, quitar relleno en el nombre de inicio de sesión de la cuenta de usuario de la cuenta de usuario, también conocido como el nombre principal de usuario (UPN), el "<" y ">" caracteres y ejecute este comando:
  
```
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Ver algunas cuentas en función de una propiedad común

Para que sea más selectivos acerca de la lista de cuentas para mostrar, puede usar el cmdlet **Where-Object** en combinación con el cmdlet **Get-MsolUser** . Para combinar los dos cmdlets, usamos el carácter "barra vertical" "|", que indica a Office 365 PowerShell tomar los resultados de un comando y enviar con el siguiente comando. Este es un comando de ejemplo que muestra sólo aquellas cuentas de usuario que tienen una ubicación de uso no especificado:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. Propiedad UsageLocation - eq $Null}** ). Entre las llaves, el comando indica a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que la propiedad UsageLocation cuenta de usuario (propiedad) ( ** $ \_. Propiedad UsageLocation** ) no está especificado ( **-eq $Null** ).
    
Verá información similar a esta:
  
```
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La propiedad de la **propiedad UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario. Para ver todas las propiedades para las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario específica. Este es un ejemplo:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:
  
```
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintaxis para el cmdlet **Where-Object** , que se muestra en estos ejemplos es **Where-Object {$\_.** [nombre de propiedad de la cuenta de usuario] [operador de comparación] [valor] **}**.  [operador de comparación] es **-eq** para es igual a, **-ne** para no es igual a, **-lt** para menor que **-gt** para mayor y otros usuarios.  [valor] es normalmente una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$Null** para que no se especifica. Para obtener más información, consulte [Where-Object](https://technet.microsoft.com/en-us/library/hh849715.aspx) .
  
Puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:
  
```
Get-MolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Ver los valores de propiedades adicionales para las cuentas

El cmdlet **Get-MsolUser** de forma predeterminada muestra las tres propiedades de cuentas de usuario:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Si necesita propiedades adicionales, como el departamento para que el usuario trabaja y el país o región donde el usuario usa servicios de Office 365, puede ejecutar **Get-MsolUser** en combinación con el cmdlet **Select-Object** para especificar la lista de cuenta de usuario Propiedades. Este es un ejemplo:
  
```
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, el departamento, la propiedad UsageLocation** ).
    
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
Scott Wallace           Operations
```

El cmdlet **Select-Object** le permite elegir y seleccionar las propiedades que desee un comando que se va a mostrar. Para ver todas las propiedades para las cuentas de usuario, use el carácter comodín (*) para mostrar todos ellos para una cuenta de usuario específica. Este es un ejemplo:
  
```
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, también puede usar el cmdlet **Where-Object**. A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:
  
```
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Este comando indica a Office 365 PowerShell para:
  
- Obtener toda la información en las cuentas de usuario ( **Get-MsolUser** ) y enviarlo al siguiente comando ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificado ( **Where-Object {$\_. Propiedad UsageLocation - eq $Null}** ) y enviar la información resultante con el siguiente comando ( **|** ). Entre las llaves, el comando es indicar a Office 365 PowerShell para buscar sólo el conjunto de cuentas en la que la propiedad UsageLocation cuenta de usuario (propiedad) ( ** $ \_. Propiedad UsageLocation** ) no está especificado ( **-eq $Null** ).
    
- Mostrar sólo el usuario nombre, departamento y uso de la ubicación de la cuenta ( **Select-Object DisplayName, el departamento, la propiedad UsageLocation** ).
    
Verá información similar a esta:
  
```
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Si se usa la sincronización de Active directory para crear y administrar los usuarios de Office 365, puede mostrar qué cuenta local de un usuario de Office 365 se han proyectado desde. Los siguientes se da por supuesto que Azure Connect AD se ha configurado para utilizar el delimitador de origen predeterminado de GUID de objeto (para obtener más información acerca de cómo configurar un delimitador de origen, vea [Azure Connect AD: conceptos de diseño](https://docs.microsoft.com/en-us/azure/active-directory/hybrid/plan-connect-design-concepts)) y se supone que tiene el módulo de Active Directory para powershell sido instalado (consulte [Herramientas RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):

```
(Get-ADUser [guid][system.convert]::frombase64string((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).Guid
```

    
## <a name="see-also"></a>Vea también

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

