---
title: Administrar Skype para políticas de negocios en línea con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 04/01/2019
ms.audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Resumen: Use Office 365 PowerShell para administrar las propiedades de la cuenta de usuario de Skype empresarial online con directivas.'
ms.openlocfilehash: 6bbfd4451552cd3a281dbbcafde0b458bb71907c
ms.sourcegitcommit: 201d3338d8bbc6da9389e62e2add8a17384fab4d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/02/2019
ms.locfileid: "31037904"
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>Administrar Skype para políticas de negocios en línea con Office 365 PowerShell

 **Resumen:** Use Office 365 PowerShell para administrar las propiedades de la cuenta de usuario de Skype empresarial online con directivas.
  
Para administrar muchas propiedades de la cuenta de usuario de Skype empresarial online, debe especificarlas como propiedades de directivas con Office 365 PowerShell.
  
## <a name="before-you-begin"></a>Antes de empezar

Siga estas instrucciones para preparar la ejecución de los comandos (omita los pasos que ya ha completado):
  
1. Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/download/details.aspx?id=39366).
    
2. Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos: 
    
```
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

Cuando se le solicite, escriba el nombre y la contraseña de la cuenta de administrador en línea de Skype empresarial online.
    
## <a name="manage-user-account-policies"></a>Administrar directivas de cuentas de usuario

Muchas de las propiedades de las cuentas de usuario de Skype empresarial online se configuran mediante directivas. Las directivas son simplemente colecciones de opciones de configuración que se pueden aplicar a uno o más usuarios. Para echar un vistazo al modo en que se ha configurado la Directiva, puede ejecutar este comando de ejemplo para la Directiva FederationAndPICDefault:
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Por su parte, debería obtener algo similar a esto:
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

En este ejemplo, los valores de esta directiva determinan lo que un uso puede o no hacer cuando se trata de comunicarse con usuarios federados. Por ejemplo, la propiedad EnableOutsideAccess debe establecerse en true para que un usuario pueda comunicarse con personas fuera de la organización. Tenga en cuenta que esta propiedad no aparece en el centro de administración de Office 365. En su lugar, la propiedad se establece automáticamente en true o false en función de las otras selecciones que realice. Las otras dos propiedades de interés son:
  
- **EnableFederationAccess** indica si el usuario puede comunicarse con usuarios de dominios federados.
    
- **EnablePublicCloudAccess** indica si el usuario puede comunicarse con usuarios de Windows Live.
    
Por lo tanto, no cambie directamente las propiedades relacionadas con la Federación de las cuentas de usuario (por ejemplo, **set-CsUser-EnableFederationAccess $true**). En su lugar, asigna a una cuenta una directiva de acceso externo que tiene los valores de propiedad deseados preconfigurados. Si queremos que un usuario pueda comunicarse con usuarios federados y con usuarios de Windows Live, la cuenta de usuario debe tener asignada una directiva que permita estos tipos de comunicación.
  
Si desea saber si alguien puede comunicarse con usuarios externos a la organización, debe:
  
- Determinar qué directiva de acceso externo se ha asignado a dicho usuario.
    
- Determinar qué capacidades permite o no dicha directiva.
    
Por ejemplo, puede hacerlo con este comando:
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Este comando busca la directiva asignada al usuario y, a continuación, busca las funciones habilitadas o deshabilitadas en esa Directiva.
  
Tenga en cuenta que no hay cmdlets para crear o modificar directivas. Debe usar las directivas suministradas previamente por Office 365. Si desea echar un vistazo a las diferentes directivas disponibles, puede usar estos comandos:
  
- Get-CsClientPolicy       
- Get-CsConferencingPolicy        
- Get-CsDialPlan            
- Get-CsExternalAccessPolicy                         
- Get-CsHostedVoicemailPolicy                        
- Get-CsPresencePolicy                               
- Get-CsVoicePolicy                                  

> [!NOTE]
> Un plan de marcado de Skype empresarial online es una directiva en todos los aspectos excepto en el nombre. Se ha elegido el nombre "plan de marcado" en lugar de, por ejemplo, "Directiva de marcado" para proporcionar compatibilidad con versiones anteriores de Office Communications Server y con Exchange. 
  
Por ejemplo, para ver todas las directivas de voz disponibles para su uso, ejecute este comando:
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> Eso devuelve una lista de todas las directivas de voz disponibles para usted. No obstante, tenga en cuenta que no todas las directivas se pueden asignar a todos los usuarios. Esto se debe a varias restricciones relacionadas con la concesión de licencias y la ubicación geográfica. (El denominado "ubicación de[uso](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx)"). Si desea conocer las directivas de acceso externo y las directivas de conferencia que se pueden asignar a un usuario en particular, use comandos similares a los siguientes: 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

El parámetro ApplicableTo limita los datos devueltos a las directivas que se pueden asignar al usuario especificado (por ejemplo, Alex Darrow). Según las licencias y las restricciones de ubicación de uso, eso puede representar un subconjunto de todas las directivas disponibles. 
  
En algunos casos, las propiedades de las directivas no se usan con Office 365, mientras que otras solo pueden ser administradas por el personal de soporte técnico de Microsoft. 
  
Con Skype empresarial online, los usuarios deben ser administrados por una directiva de algún tipo. Si una propiedad relacionada con directivas válida está en blanco, significa que el usuario en cuestión se administra mediante una directiva global, que es una directiva que se aplica automáticamente a un usuario a menos que se le asigne específicamente una directiva por usuario. Como no vemos una directiva de cliente listada para una cuenta de usuario, ésta se administra mediante la directiva global. Puede determinar la Directiva de cliente global con este comando:
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Vea también

#### 

[Administrar Skype Empresarial Online con PowerShell de Office 365](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

