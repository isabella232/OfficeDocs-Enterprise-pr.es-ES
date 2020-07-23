---
title: Administrar directivas de Skype empresarial online con PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 07/17/2020
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: ff93a341-6f0f-4f06-9690-726052e1be64
description: 'Resumen: Use PowerShell para administrar las propiedades de la cuenta de usuario de Skype empresarial online con directivas.'
ms.openlocfilehash: 4310de23d47025468ea78a597f6379b51deaaa96
ms.sourcegitcommit: 0d1ebcea8c73a644cca3de127a93385c58f9a302
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/22/2020
ms.locfileid: "45230436"
---
# <a name="manage-skype-for-business-online-policies-with-powershell"></a>Administrar directivas de Skype empresarial online con PowerShell

*Este artículo se aplica tanto a Microsoft 365 Enterprise como a Office 365 Enterprise.*

Para administrar muchas propiedades de la cuenta de usuario de Skype empresarial online, debe especificarlas como propiedades de directivas con PowerShell para Microsoft 365.
  
## <a name="before-you-begin"></a>Antes de empezar

Siga estas instrucciones para preparar la ejecución de los comandos (omita los pasos que ya ha completado):
  
1. Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/download/details.aspx?id=39366).
    
2. Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos: 
    
```powershell
Import-Module SkypeOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
  ```

Cuando se le solicite, escriba el nombre y la contraseña de la cuenta de administrador en línea de Skype empresarial online.
    
## <a name="manage-user-account-policies"></a>Administrar directivas de cuentas de usuario

Muchas de las propiedades de las cuentas de usuario de Skype empresarial online se configuran mediante directivas. Las directivas son simplemente colecciones de opciones de configuración que se pueden aplicar a uno o más usuarios. Para echar un vistazo al modo en que se ha configurado la Directiva, puede ejecutar este comando de ejemplo para la Directiva FederationAndPICDefault:
  
```powershell
Get-CsExternalAccessPolicy -Identity "FederationAndPICDefault"
```

Por su parte, debería obtener algo similar a esto:
  
```powershell
Identity                          : Tag:FederationAndPICDefault
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : True
EnablePublicCloudAudioVideoAccess : True
EnableOutsideAccess               : True
```

En este ejemplo, los valores de esta directiva determinan lo que un uso puede o no hacer cuando se trata de comunicarse con usuarios federados. Por ejemplo, la propiedad EnableOutsideAccess debe establecerse en true para que un usuario pueda comunicarse con personas fuera de la organización. Tenga en cuenta que esta propiedad no aparece en el centro de administración de Microsoft 365. En su lugar, la propiedad se establece automáticamente en true o false en función de las otras selecciones que realice. Las otras dos propiedades de interés son:
  
- **EnableFederationAccess** indica si el usuario puede comunicarse con usuarios de dominios federados.
    
- **EnablePublicCloudAccess** indica si el usuario puede comunicarse con usuarios de Windows Live.
    
Por lo tanto, no cambie directamente las propiedades relacionadas con la Federación de las cuentas de usuario (por ejemplo, **set-CsUser-EnableFederationAccess $true**). En su lugar, asigna a una cuenta una directiva de acceso externo que tiene los valores de propiedad deseados preconfigurados. Si queremos que un usuario pueda comunicarse con usuarios federados y con usuarios de Windows Live, la cuenta de usuario debe tener asignada una directiva que permita estos tipos de comunicación.
  
Si desea saber si alguien puede comunicarse con usuarios externos a la organización, debe:
  
- Determinar qué directiva de acceso externo se ha asignado a dicho usuario.
    
- Determinar qué capacidades permite o no dicha directiva.
    
Por ejemplo, puede hacerlo con este comando:
  
```powershell
Get-CsOnlineUser -Identity "Alex Darrow" | ForEach {Get-CsExternalAccessPolicy -Identity $_.ExternalAccessPolicy}
```

Este comando busca la directiva asignada al usuario y, a continuación, busca las funciones habilitadas o deshabilitadas en esa Directiva.
  
Para administrar las directivas de Skype empresarial online con PowerShell, consulte los cmdlets de:

- [Directiva de cliente](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#client-policy-cmdlets)
- [Directiva de conferencia](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#conferencing-policy-cmdlets)
- [Directiva móvil](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#mobile-policy-cmdlets)
- [Directiva de correo de voz en línea](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#online-voicemail-policy-cmdlets)
- [Directiva de enrutamiento de voz](https://docs.microsoft.com/previous-versions//mt228132(v=technet.10)#voice-routing-policy-cmdlets)


> [!NOTE]
> Un plan de marcado de Skype empresarial online es una directiva en todos los aspectos excepto en el nombre. Se ha elegido el nombre "plan de marcado" en lugar de, por ejemplo, "Directiva de marcado" para proporcionar compatibilidad con versiones anteriores de Office Communications Server y con Exchange. 
  
Por ejemplo, para ver todas las directivas de voz disponibles para su uso, ejecute este comando:
  
```powershell
Get-CsVoicePolicy
```

> [!NOTE]
> Eso devuelve una lista de todas las directivas de voz disponibles para usted. No obstante, tenga en cuenta que no todas las directivas se pueden asignar a todos los usuarios. Esto se debe a varias restricciones relacionadas con la concesión de licencias y la ubicación geográfica. (El denominado "ubicación de[uso](https://msdn.microsoft.com/library/azure/dn194136.aspx)"). Si desea conocer las directivas de acceso externo y las directivas de conferencia que se pueden asignar a un usuario en particular, use comandos similares a los siguientes: 

```powershell
Get-CsConferencingPolicy -ApplicableTo "Alex Darrow"
Get-CsExternalAccessPolicy -ApplicableTo "Alex Darrow"
```

El parámetro ApplicableTo limita los datos devueltos a las directivas que se pueden asignar al usuario especificado (por ejemplo, Alex Darrow). Según las licencias y las restricciones de ubicación de uso, eso puede representar un subconjunto de todas las directivas disponibles. 
  
En algunos casos, las propiedades de las directivas no se usan con Microsoft 365, mientras que otras solo pueden ser administradas por el personal de soporte técnico de Microsoft. 
  
Con Skype empresarial online, los usuarios deben ser administrados por una directiva de algún tipo. Si una propiedad relacionada con directivas válida está en blanco, significa que el usuario en cuestión se administra mediante una directiva global, que es una directiva que se aplica automáticamente a un usuario a menos que se le asigne específicamente una directiva por usuario. Como no vemos una directiva de cliente listada para una cuenta de usuario, ésta se administra mediante la directiva global. Puede determinar la Directiva de cliente global con este comando:
  
```powershell
Get-CsClientPolicy -Identity "Global"
```

## <a name="see-also"></a>Consulte también

[Administrar Skype empresarial online con PowerShell](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Administrar Microsoft 365 con PowerShell](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell para Microsoft 365](getting-started-with-office-365-powershell.md)

