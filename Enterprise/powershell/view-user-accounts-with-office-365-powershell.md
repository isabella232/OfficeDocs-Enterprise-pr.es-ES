---
title: Ver cuentas de usuario con PowerShell de Office 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/19/2019
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- LIL_Placement
- PowerShell
- Ent_Office_Other
ms.assetid: bb12f49d-a85d-4f3b-ada2-5c4e33977b10
description: 'Resumen: vea, enumere o muestre las cuentas de usuario de varias formas con Office 365 PowerShell.'
ms.openlocfilehash: 0711bf945b863cb89d45a377f61a139b298ca6d7
ms.sourcegitcommit: f316aef1c122f8eb25c43a56bc894c4aa61c8e0c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "38748408"
---
# <a name="view-user-accounts-with-office-365-powershell"></a>Ver cuentas de usuario con PowerShell de Office 365

Aunque puede usar el centro de administración de Microsoft 365 para ver las cuentas de su inquilino de Office 365, también puede usar PowerShell de Office 365 y realizar algunas acciones que el centro de administración no puede.
  
## <a name="use-the-azure-active-directory-powershell-for-graph-module"></a>Use el módulo de PowerShell Azure Active Directory para Graph

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).
  
### <a name="view-all-accounts"></a>Ver todas las cuentas

Para mostrar la lista completa de cuentas de usuario, ejecute este comando:
  
```powershell
Get-AzureADUser
```

Verá información similar a esta:
  
```powershell
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

Para mostrar una cuenta de usuario específica, rellene el nombre de la cuenta de inicio de sesión de la cuenta de usuario, también conocido como nombre principal de usuario (UPN), quite los caracteres "<" y ">" y ejecute este comando:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account>
```

Aquí le mostramos un ejemplo:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com
```

### <a name="view-additional-property-values-for-a-specific-account"></a>Ver valores de propiedades adicionales para una cuenta específica

De forma predeterminada, el cmdlet **Get-AzureADUser** solo muestra las propiedades objectId, DisplayName y UserPrincipalName de las cuentas.

Para ser más selectivo acerca de la lista de propiedades que se mostrarán, puede usar el cmdlet **Select-Object** en combinación con el cmdlet **Get-AzureADUser** . Para combinar los dos cmdlets, usamos el carácter "canalización" "|", que indica a Azure Active Directory PowerShell para que Graph tome los resultados de un comando y lo envíe al siguiente comando. Este es un comando de ejemplo que muestra DisplayName, Department y UsageLocation para cada cuenta de usuario:
  
```powershell
Get-AzureADUser | Select-Object DisplayName,Department,UsageLocation
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).
    
- Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Select-Object DisplayName, Department, UsageLocation** ).
  
Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (*) para mostrarlos todos para una cuenta de usuario específica. Aquí le mostramos un ejemplo:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Como otro ejemplo, puede comprobar el estado habilitado de una cuenta de usuario específica con el siguiente comando:
  
```powershell
Get-AzureADUser -ObjectID <sign-in name of the user account> | Select-Object DisplayName,UserPrincipalName,AccountEnabled
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Ver algunas cuentas basadas en una propiedad común

Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, puede usar el cmdlet **Where-Object** junto con el cmdlet **Get-AzureADUser**. Para combinar los dos cmdlets, usamos el carácter "canalización" "|", que indica a Azure Active Directory PowerShell para que Graph tome los resultados de un comando y lo envíe al siguiente comando. A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:
  
```powershell
Get-AzureADUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando le indica a Azure Active Directory PowerShell para que Graph:
  
- Obtener toda la información de las cuentas de usuario ( **Get-AzureADUser** ) y enviarla al comando siguiente ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **Where-Object {\_$. UsageLocation-EQ $Null}** ). Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( ** $ \_. UsageLocation** ) no está especificado ( **-EQ $null** ).
    
La propiedad **UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario. Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (*) para mostrarlos todos para una cuenta de usuario específica. Aquí le mostramos un ejemplo:
  
```powershell
Get-AzureADUser -ObjectID BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:
  
```powershell
Get-AzureADUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintaxis del cmdlet **Where-Object** que se muestra en estos ejemplos es **Where-Object {\_$.** [nombre de propiedad de cuenta de usuario] [operador de comparación] Value **}**. > [operador de comparación] is **-EQ** para igual a, **-ne** para no es igual a, **-lt** para menor que, **-gt** para mayor que, y otros.  [VALUE] suele ser una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$null** para> sin especificar consulte [Where-Object](https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Core/Where-Object?view=powershell-5.1) para obtener más información.
  

## <a name="use-the-microsoft-azure-active-directory-module-for-windows-powershell"></a>Use el Módulo Microsoft Azure Active Directory para Windows PowerShell

Primero, [conéctese a su inquilino de Office 365](connect-to-office-365-powershell.md#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell).

### <a name="view-all-accounts"></a>Ver todas las cuentas

Para mostrar la lista completa de cuentas de usuario, ejecute este comando:
  
```powershell
Get-MsolUser
```

Verá información similar a esta:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BonnieK@litwareinc.onmicrosoft.com    Bonnie Kearney        True
FabriceC@litwareinc.onmicrosoft.com   Fabrice Canel         True
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
AnneWlitwareinc.onmicrosoft.com       Anne Wallace          True
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

El cmdlet **Get-MsolUser** también tiene un conjunto de parámetros para filtrar el conjunto de cuentas de usuario que se muestran. Por ejemplo, para la lista de usuarios sin licencia (usuarios que se han agregado a Office 365 pero que todavía no han sido autorizados para usar ninguno de los servicios), ejecute este comando.
  
```powershell
Get-MsolUser -UnlicensedUsersOnly
```

Verá información similar a esta:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False
```

Para obtener más información acerca de los parámetros adicionales para filtrar la visualización del conjunto de cuentas de usuario que se muestra, consulte [Get-MsolUser](https://docs.microsoft.com/previous-versions/azure/dn194133(v=azure.100)).
  

### <a name="view-a-specific-account"></a>Ver una cuenta específica

Para mostrar una cuenta de usuario específica, escriba el nombre de inicio de sesión de la cuenta de usuario de la cuenta de usuario, también conocido como nombre principal de usuario (UPN), quite los caracteres "<" y ">" y ejecute este comando:
  
```powershell
Get-MsolUser -UserPrincipalName <sign-in name of the user account>
```

### <a name="view-some-accounts-based-on-a-common-property"></a>Ver algunas cuentas basadas en una propiedad común

Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, puede usar el cmdlet **Where-Object** junto con el cmdlet **Get-MsolUser**. Para combinar los dos cmdlets, usamos el carácter "canal" "|", que indica a Office 365 PowerShell que debe tomar los resultados de un comando y enviarlo al siguiente comando. A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null}
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **Where-Object {\_$. UsageLocation-EQ $Null}** ). Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( ** $ \_. UsageLocation** ) no está especificado ( **-EQ $null** ).
    
Verá información similar a esta:
  
```powershell
UserPrincipalName                     DisplayName           isLicensed
-----------------                     -----------           ----------
BrianJ@litwareinc.onmicrosoft.com     Brian Johnson         False 
ScottW@litwareinc.onmicrosoft.com     Scott Wallace         False

```

La propiedad **UsageLocation** es solo una de las muchas propiedades asociadas con una cuenta de usuario. Para ver todas las propiedades de las cuentas de usuario, use el cmdlet **Select-Object** y el carácter comodín (*) para mostrarlos todos para una cuenta de usuario específica. Aquí le mostramos un ejemplo:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Por ejemplo, en esta lista, **City** es el nombre de una propiedad de la cuenta de usuario. Esto significa que puede usar el comando siguiente para enumerar todas las cuentas de los usuarios que viven en Londres:
  
```powershell
Get-MsolUser | Where-Object {$_.City -eq "London"}
```

> [!TIP]
>  La sintaxis del cmdlet **Where-Object** que se muestra en estos ejemplos es **Where-Object {\_$.** [nombre de propiedad de cuenta de usuario] [operador de comparación] Value **}**.  [Comparison Operator] es **-EQ** para igual a, **-ne** para no es igual a, **-lt** para menor que, **-gt** para mayor que, y otros.  [VALUE] suele ser una cadena (una secuencia de letras, números y otros caracteres), un valor numérico o **$null** para no especificado. Consulte [Where-Object](https://technet.microsoft.com/library/hh849715.aspx) para obtener más información.
  
Puede comprobar el estado de bloqueo de una cuenta de usuario con el siguiente comando:
  
```powershell
Get-MsolUser -UserPrincipalName <UPN of user account> | Select-Object DisplayName,BlockCredential
```

### <a name="view-additional-property-values-for-accounts"></a>Ver los valores de propiedad adicionales de las cuentas

De forma predeterminada, el cmdlet **Get-MsolUser** muestra tres propiedades de las cuentas de usuario:
  
- UserPrincipalName
    
- DisplayName
    
- isLicensed
    
Si necesita propiedades adicionales, como el Departamento en el que trabaja el usuario y el país o la región donde el usuario usa los servicios de Office 365, puede ejecutar **Get-MsolUser** en combinación con el cmdlet **Select-Object** para especificar la lista de propiedades de la cuenta de usuario. Aquí le mostramos un ejemplo:
  
```powershell
Get-MsolUser | Select-Object DisplayName, Department, UsageLocation
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).
    
- Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Select-Object DisplayName, Department, UsageLocation** ).
    
Verá información similar a esta:
  
```powershell
DisplayName             Department                       UsageLocation
-----------             ----------                       -------------
Bonnie Kearney          Sales & Marketing                    US
Fabrice Canel           Legal                                US
Brian Johnson
Anne Wallace            Executive Management                 US
Alex Darrow             Sales & Marketing                    US
Scott Wallace           Operations
```

El cmdlet **Select-Object** permite seleccionar y elegir las propiedades que desea que muestre un comando. Para ver todas las propiedades de las cuentas de usuario, use el carácter comodín (*) para mostrarlas todas para una cuenta de usuario específica. A continuación se muestra un ejemplo:
  
```powershell
Get-MsolUser -UserPrincipalName BelindaN@litwareinc.onmicosoft.com | Select-Object *
```

Para ser más selectivo en lo que respecta a la lista de cuentas que se va a mostrar, también puede usar el cmdlet **Where-Object**. A continuación se incluye un comando de ejemplo que muestra solo las cuentas de usuario que tienen una ubicación de uso no especificada:
  
```powershell
Get-MsolUser | Where-Object {$_.UsageLocation -eq $Null} | Select-Object DisplayName, Department, UsageLocation
```

Este comando indica a Office 365 PowerShell que:
  
- Obtener toda la información de las cuentas de usuario ( **Get-MsolUser** ) y enviarla al comando siguiente ( **|** ).
    
- Buscar todas las cuentas de usuario que tienen una ubicación de uso no especificada ( **Where-Object {\_$. UsageLocation-EQ $Null}** ) y envía la información resultante al siguiente comando ( **|** ). Dentro de las llaves, el comando indica a Office 365 PowerShell que solo busque el conjunto de cuentas en el que la propiedad de la cuenta de usuario UsageLocation ( ** $ \_. UsageLocation** ) no está especificado ( **-EQ $null** ).
    
- Mostrar solo el nombre de la cuenta de usuario, el Departamento y la ubicación de uso ( **Select-Object DisplayName, Department, UsageLocation** ).
    
Verá información similar a esta:
  
```powershell
DisplayName              Department                      UsageLocation
-----------              ----------                      -------------
Brian Johnson 
Scott Wallace            Operations
```

Si usa la sincronización de directorios para crear y administrar los usuarios de Office 365, puede mostrar la cuenta local de la que se ha proyectado un usuario de Office 365. A continuación se supone que Azure AD Connect se ha configurado para usar el delimitador de origen predeterminado de ObjectGUID (para obtener más información sobre la configuración de un delimitador de origen, consulte [Azure ad Connect: Design Concepts](https://docs.microsoft.com/azure/active-directory/hybrid/plan-connect-design-concepts)) y se supone que se ha instalado el módulo de Active Directory para PowerShell (consulte [las herramientas de RSAT](https://www.microsoft.com/en-gb/download/details.aspx?id=45520)):

```powershell
Get-ADUser ([guid][System.Convert]::FromBase64String((Get-MsolUser -UserPrincipalName <UPN of user account>).ImmutableID)).guid
```

    
## <a name="see-also"></a>Vea también

[Administrar licencias y cuentas de usuario con PowerShell de Office 365](manage-user-accounts-and-licenses-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

