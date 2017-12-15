---
title: "Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell"
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: DecEntMigration
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: "Resumen: Uso Office 365 PowerShell para asignar a cada usuario configuración de comunicaciones con Skype para las políticas de negocios en línea."
ms.openlocfilehash: 91916b41ba420a204ecabb27eea2e451a91f6f25
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell

 **Resumen:** Utilice Office 365 PowerShell para asignar a cada usuario configuración de comunicaciones con Skype para las políticas de negocios en línea.
  
Con Office 365 PowerShell es una forma eficaz de asignar a cada usuario configuración de comunicaciones con Skype para las políticas de negocios en línea.
  
## <a name="before-you-begin"></a>Antes de empezar

Siga estas instrucciones para obtener configurado para ejecutar los comandos (sáltese los pasos que ya ha completado):
  
1. Descargue e instale el [Skype para el módulo de Business Connector en línea](https://www.microsoft.com/en-us/download/details.aspx?id=39366).
    
2. Abra un símbolo del sistema de Windows PowerShell y ejecute los comandos siguientes: 
    
  ```
  Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```
Cuando se le solicite, escriba su Skype para contraseña y nombre de cuenta de administrador de negocios en línea.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Actualizando la configuración de la comunicación externa para una cuenta de usuario

Suponga que desea cambiar la configuración de la comunicación externa en una cuenta de usuario. Por ejemplo, desea permitir que Alex para comunicarse con los usuarios federados (EnableFederationAccess es igual a True) pero no a los usuarios de Windows Live (EnablePublicCloudAccess es igual a falso). Para ello, debe hacer dos cosas:
  
1. Buscar una directiva de acceso externo que cumpla nuestros criterios.
    
2. Asignar esa directiva de acceso externo a Alex.
    
> [!NOTE]
>  No se puede crear una directiva personalizada todos nuestros propios. Eso es porque Skype para los negocios en línea no le permiten crear directivas personalizadas. En su lugar, debe asignar una de las directivas que se han creado específicamente para Office 365. Aquellos creados previamente las políticas incluyen: 4 políticas de cliente diferente, 224 conferencias diferentes directivas, 5 otros planes de marcado, 5 directivas de acceso externo diferente, directivas de correo de voz hospedado 1 y 4 otra voz directivas.
  
Entonces, ¿cómo puede determinar qué directiva de acceso externo para asignar a Alex? El siguiente comando devuelve todas las directivas de acceso externo donde EnableFederationAccess está establecida en True y EnablePublicCloudAccess se establece en False:
  
```
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Lo que hace el comando es devolver todas las directivas que cumplan dos criterios: la propiedad EnableFederationAccess está establecida en True, y la directiva EnablePublicCloudAccess está establecida en False. A su vez, ese comando devuelve una directiva que cumpla nuestros criterios (FederationOnly). Éste es un ejemplo:
  
```
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> La directiva de identidad indica etiqueta: FederationOnly. Según parece, la etiqueta: prefijo es un remanente de trabajo previo al lanzamiento temprano realizado en Microsoft Lync 2013. En cuanto a la asignación de directivas a los usuarios, debe eliminar la etiqueta: prefijo y utilizar simplemente el nombre de la directiva: FederationOnly. 
  
Ahora que sabe qué directiva para asignar a Alex, podemos asignar esa directiva mediante el cmdlet de [Concesión CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) . Éste es un ejemplo:
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

Asignación de una directiva es bastante sencilla: sólo tiene que especificar la identidad del usuario y el nombre de la directiva que se asignará. 
  
Y en cuanto a las políticas y las asignaciones de directivas, no está limitado a trabajar con cuentas de usuario una vez. Por ejemplo, suponga que necesita una lista de todos los usuarios que tienen permiso para comunicarse con los socios federados y con usuarios de Windows Live. Ya se sabe que los usuarios le ha asignado la directiva de acceso de usuario externo FederationAndPICDefault. Porque sabemos, mediante la ejecución de un comando simple puede mostrar una lista de todos los usuarios. Aquí está el comando:
  
```
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

En otras palabras, nos muestran todos los usuarios donde se establece la propiedad ExternalAccessPolicy a FederationAndPICDefault. (Y, con el fin de limitar la cantidad de información que aparece en la pantalla, use el cmdlet Select-Object para mostrar nos muestran sólo nombre para mostrar de cada usuario). 
  
Para configurar todas las cuentas de usuarios para utilizar esa misma directiva, use este comando:
  
```
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Este comando utiliza Get-CsOnlineUser para devolver una colección de todos los usuarios que se han habilitado para Lync, entonces envía toda esa información a CsExternalAccessPolicy de la concesión, que se asigna la directiva FederationAndPICDefault para cada usuario de la colección.
  
Como ejemplo adicional, supongamos que Alex previamente se ha asignado la directiva FederationAndPICDefault y ahora ha cambiado de opinión y desea que le sea administrado por la directiva global de acceso externo. No se puede asignar explícitamente la directiva global a nadie. Sólo se utiliza si no se ha asignado ninguna otra directiva por usuario. Por lo tanto, si queremos que Alex sea administrado por la directiva global, debe *desasignar* cualquier directiva por usuario previamente asignado a él. Aquí es un comando de ejemplo:
  
```
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Este comando establece el nombre de la directiva de acceso externo asignado a Alex en un valor nulo ($Null). NULL significa "nada". En otras palabras, no se asigna ninguna directiva de acceso externo a Alex. Cuando se ha asignado ninguna directiva de acceso externo a un usuario, dicho usuario obtiene administrado por la directiva global.
  
Para deshabilitar una cuenta de usuario con Windows PowerShell, usar los cmdlets de Azure Active Directory para quitar Skype de Alex para licencia de negocios en línea. Para obtener más información, vea [Deshabilitar el acceso a los servicios de Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).
  
## <a name="see-also"></a>See also

#### 

[Administrar Skype Empresarial Online con PowerShell de Office 365](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

