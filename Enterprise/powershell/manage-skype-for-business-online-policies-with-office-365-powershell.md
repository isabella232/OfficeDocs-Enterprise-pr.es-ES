---
title: "Administrar Skype para políticas de negocios en línea con Office 365 PowerShell"
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
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: "Resumen: Uso Office 365 PowerShell para administrar su Skype para los negocios en línea propiedades de cuenta de usuario con las directivas."
ms.openlocfilehash: 9b3877d2680b2b36d155cb5dd2a69fa21c972fe3
ms.sourcegitcommit: d31cf57295e8f3d798ab971d405baf3bd3eb7a45
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/15/2017
---
# <a name="manage-skype-for-business-online-policies-with-office-365-powershell"></a>Administrar Skype para políticas de negocios en línea con Office 365 PowerShell

 **Resumen:** Utilice Office 365 PowerShell para administrar su Skype para los negocios en línea propiedades de cuenta de usuario con las directivas.
  
Para administrar muchas de las propiedades de cuenta de usuario de Skype para los negocios en línea, debe especificar como propiedades de directivas de Office 365 PowerShell.
  
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
    
## <a name="manage-user-account-policies"></a>Administrar las directivas de cuentas de usuario

Muchos Skype para los negocios en línea propiedades de cuenta de usuario se configuran mediante directivas. Las directivas son simplemente colecciones de configuraciones que se pueden aplicar a uno o más usuarios. Echar un vistazo a cómo se ha configurado una directiva, puede ejecutar este comando de ejemplo para la directiva de FederationAndPICDefault:
  
```
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

A su vez, debería obtener algo similar a esto:
  
```
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

En este ejemplo, los valores de esta directiva determinan lo que se puede utilizar o no pueden hacer cuando se trata de comunicarse con los usuarios federados. Por ejemplo, la propiedad EnableOutsideAccess debe establecerse en True para que un usuario pueda comunicarse con personas ajenas a la organización. Tenga en cuenta que esta propiedad no aparece en el centro de administración de Office 365. En su lugar, la propiedad se establece automáticamente en True o False según las selecciones realizadas. Las otras dos propiedades de interés son:
  
- **EnableFederationAccess** indica si el usuario puede comunicarse con usuarios de dominios federados.
    
- **EnablePublicCloudAccess** indica si el usuario puede comunicarse con los usuarios de Windows Live.
    
Por lo tanto, no cambia las propiedades relacionadas con la federación en las cuentas de usuario (por ejemplo, el **Conjunto CsUser-EnableFederationAccess $True**) directamente. En su lugar, asigne una cuenta de una directiva de acceso externo que tiene los valores de la propiedad deseada preconfigurados. Si queremos que un usuario pueda comunicarse con los usuarios federados y con usuarios de Windows Live, esa cuenta de usuario debe asignarse una directiva que permite a esos tipos de comunicación.
  
Si desea saber si alguien puede comunicarse con los usuarios de fuera de la organización, deberá:
  
- Determinar qué directiva de acceso externo se ha asignado a dicho usuario.
    
- Determinar qué capacidades permite o no dicha directiva.
    
Por ejemplo, se puede hacer mediante este comando:
  
```
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Este comando busca la directiva asignada para el usuario, busca después las funciones habilitada o deshabilitan en esa directiva.
  
Tenga en cuenta que no hay ningún cmdlets para crear o modificar las directivas. Debe utilizar las directivas previamente proporcionadas por Office 365. Si desea echar un vistazo a las diferentes directivas disponibles, puede utilizar estos comandos:
  
- Get-CsClientPolicy       
- Get-CsConferencingPolicy        
- Get-CsDialPlan            
- Get-CsExternalAccessPolicy                         
- Get-CsHostedVoicemailPolicy                        
- Get-CsPresencePolicy                               
- Get-CsVoicePolicy                                  

> [!NOTE]
> Un Skype para el plan de marcado de los negocios en línea es una directiva en todos los aspectos excepto el nombre. Se ha elegido el nombre "plan de marcado" en lugar de, digamos, "Directiva de marcado" con el fin de proporcionar compatibilidad con Office Communications Server y Exchange. 
  
Por ejemplo, para buscar en todos las directivas de voz disponibles para su uso, ejecute este comando:
  
```
Get-CsVoicePolicy
```

> [!NOTE]
> Devuelve una lista de todas las directivas de voz disponibles para usted. Tenga en cuenta, sin embargo, que no todas las directivas pueden asignarse a todos los usuarios. Esto es debido a diversas restricciones que implican la ubicación geográfica y con licencia. (Llamados "[ubicación de uso](https://msdn.microsoft.com/en-us/library/azure/dn194136.aspx).") Si desea conocer las directivas de acceso externo y las directivas de conferencias que pueden asignarse a un usuario concreto, utilice comandos similares a éstos: 

```
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

El parámetro ApplicableTo limita los datos devueltos a las directivas que se pueden asignar al usuario especificado (por ejemplo, Alex Darrow). Según las licencias y las restricciones de ubicación de uso, eso puede representar un subconjunto de todas las directivas disponibles. 
  
En algunos casos, las propiedades de directivas no se utilizan con Office 365, mientras que otros sólo pueden administrarse por personal de soporte técnico de Microsoft. 
  
Con Skype para los negocios en línea, los usuarios deben administrarse mediante una directiva de algún tipo. Si una propiedad válida relacionadas con la política está en blanco, significa que el usuario en cuestión está administrando una directiva global, que es una directiva que se aplica automáticamente a un usuario, a menos que él o ella se asigna específicamente una directiva por usuario. Porque no vemos una directiva de cliente para una cuenta de usuario, se administra la directiva global. Puede determinar la directiva de cliente global con este comando:
  
```
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>See also

#### 

[Administrar Skype Empresarial Online con PowerShell de Office 365](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)

