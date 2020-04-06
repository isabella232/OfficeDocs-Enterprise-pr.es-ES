---
title: Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection: Ent_O365
f1.keywords:
- NOCSH
ms.custom: ''
ms.assetid: 36743c86-46c2-46be-b9ed-ad9d4e85d186
description: 'Resumen: Use Office 365 PowerShell para asignar configuraciones de comunicación por usuario con directivas de Skype empresarial online.'
ms.openlocfilehash: 615deca2790e206e6cf117283321307aa01eac74
ms.sourcegitcommit: f2aefbc2dbbe969fea9db3a4c558651496532413
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2020
ms.locfileid: "43146815"
---
# <a name="assign-per-user-skype-for-business-online-policies-with-office-365-powershell"></a>Asignar cada usuario Skype para las políticas de negocios en línea con Office 365 PowerShell

El uso de Office 365 PowerShell es una forma eficaz de asignar configuraciones de comunicación por usuario con directivas de Skype empresarial online.
  
## <a name="before-you-begin"></a>Antes de empezar

Siga estas instrucciones para preparar la ejecución de los comandos (omita los pasos que ya ha completado):
  
1. Descargue e instale el [módulo de conector de Skype empresarial online](https://www.microsoft.com/download/details.aspx?id=39366).
    
2. Abra un símbolo del sistema de Windows PowerShell y ejecute los siguientes comandos: 
    
```powershell
Import-Module LyncOnlineConnector
$userCredential = Get-Credential
$sfbSession = New-CsOnlineSession -Credential $userCredential
Import-PSSession $sfbSession
```

Cuando se le solicite, escriba el nombre y la contraseña de la cuenta de administrador en línea de Skype empresarial online.
    
## <a name="updating-external-communication-settings-for-a-user-account"></a>Actualización de la configuración de comunicación externa para una cuenta de usuario

Supongamos que desea cambiar la configuración de comunicación externa en una cuenta de usuario. Por ejemplo, desea permitir que Alex se comunique con los usuarios federados (EnableFederationAccess es igual a true) pero no con los usuarios de Windows Live (EnablePublicCloudAccess es igual a false). Para ello, debe hacer dos cosas:
  
1. Buscar una directiva de acceso externo que cumpla nuestros criterios.
    
2. Asignar esa directiva de acceso externo a Alex.
    
> [!NOTE]
>  No se puede crear una directiva personalizada todo lo mismo. Esto se debe a que Skype empresarial online no permite crear directivas personalizadas. En su lugar, debe asignar una de las directivas creadas específicamente para Office 365. Estas directivas predefinidas incluyen: 4 directivas de cliente diferentes, 224 distintas directivas de conferencia, 5 planes de marcado diferentes, 5 directivas de acceso externo diferentes, una directiva de correo de voz hospedado y 4 directivas de voz distintas.
  
¿Cómo se determina qué directiva de acceso externo asignara Alex? El siguiente comando devuelve todas las directivas de acceso externo donde EnableFederationAccess se establece en True y EnablePublicCloudAccess se establece en False:
  
```powershell
Get-CsExternalAccessPolicy | Where-Object {$_.EnableFederationAccess -eq $True -and $_.EnablePublicCloudAccess -eq $False}
```

Lo que hace el comando devuelve todas las directivas que cumplen dos criterios: la propiedad EnableFederationAccess se establece en true y la Directiva EnablePublicCloudAccess se establece en false. A su vez, el comando devuelve una directiva que cumple nuestros criterios (FederationOnly). Aquí le mostramos un ejemplo:
  
```powershell
Identity                          : Tag:FederationOnly
Description                       :
EnableFederationAccess            : True
EnableXmppAccess                  : False
EnablePublicCloudAccess           : False
EnablePublicCloudAudioVideoAccess : False
EnableOutsideAccess               : True
```

> [!NOTE]
> La identidad de la Directiva dice etiqueta: FederationOnly. Como resultado, el prefijo de etiqueta es un remanente del trabajo anterior de la versión preliminar que se hizo en Microsoft Lync 2013. Cuando se trata de asignar directivas a los usuarios, debe eliminar el prefijo de etiqueta y usar únicamente el nombre de directiva: FederationOnly. 
  
Ahora que ya sabe qué directiva asignar a Alex, podemos asignar esa Directiva mediante el cmdlet [Grant-CsExternalAccessPolicy](https://go.microsoft.com/fwlink/?LinkId=523974) . Aquí le mostramos un ejemplo:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName "FederationOnly"
```

La asignación de una directiva es muy sencilla: simplemente especifique la identidad del usuario y el nombre de la Directiva que se va a asignar. 
  
En lo que se refiere a las directivas y asignaciones de directivas, no se limita a trabajar con cuentas de usuario una vez. Por ejemplo, supongamos que necesita una lista de todos los usuarios que tienen permiso para comunicarse con los socios federados y los usuarios de Windows Live. Ya sabemos que a esos usuarios se les ha asignado la directiva de acceso de usuario externo FederationAndPICDefault. Como sabemos, puede mostrar una lista de todos los usuarios mediante la ejecución de un comando sencillo. Este es el comando:
  
```powershell
Get-CsOnlineUser -Filter {ExternalAccessPolicy -eq "FederationAndPICDefault"} | Select-Object DisplayName
```

En otras palabras, veremos a todos los usuarios donde la propiedad ExternalAccessPolicy se establece en FederationAndPICDefault. (Y, para limitar la cantidad de información que aparece en la pantalla, use el cmdlet Select-Object para mostrar solo el nombre para mostrar de cada usuario). 
  
Para configurar todas las cuentas de usuario para que usen la misma directiva, use este comando:
  
```powershell
Get-CsOnlineUser | Grant-CsExternalAccessPolicy "FederationAndPICDefault"
```

Este comando usa Get-CsOnlineUser para devolver una colección de todos los usuarios que se han habilitado para Lync y, a continuación, envía toda la información a Grant-CsExternalAccessPolicy, que asigna la Directiva FederationAndPICDefault a todos y cada uno de los usuarios de la colección.
  
Por ejemplo, supongamos que anteriormente ha asignado a Alex la Directiva FederationAndPICDefault y que ahora ha cambiado de opinión y desea que se administre mediante la directiva global de acceso externo. No se puede asignar explícitamente la directiva global a nadie. Solo se usa si no se ha asignado ninguna otra directiva por usuario. Por lo tanto, si queremos que Alex administre la directiva global, debe *anular la asignación* de la Directiva por usuario que se le haya asignado anteriormente. A continuación se muestra un ejemplo:
  
```powershell
Grant-CsExternalAccessPolicy -Identity "Alex Darrow" -PolicyName $Null
```

Este comando establece el nombre de la Directiva de acceso externo asignada a Alex en un valor nulo ($Null). Null significa "Nothing". Es decir, no se asigna ninguna directiva de acceso externo a Alex. Cuando no se asigna ninguna directiva de acceso externo a un usuario, dicho usuario se administra mediante la directiva global.
  
Para deshabilitar una cuenta de usuario con Windows PowerShell, use los cmdlets de Azure Active Directory para quitar la licencia de Skype empresarial online de Alex. Para obtener más información, vea [deshabilitar el acceso a servicios con Office 365 PowerShell](assign-licenses-to-user-accounts-with-office-365-powershell.md).

## <a name="managing-large-numbers-of-users"></a>Administración de grandes cantidades de usuarios

Para administrar un gran número de usuarios (1000 o más), debe procesar los comandos mediante un bloque de script mediante el cmdlet [Invoke-Command](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/invoke-command?view=powershell-7) .  En los ejemplos anteriores, cada vez que se ejecuta un cmdlet, debe configurar la llamada y, a continuación, esperar el resultado antes de volver a enviarlo.  Cuando se usa un bloque de script, esto permite que se ejecuten los cmdlets de forma remota y, una vez finalizado, se devuelven los datos. 

```powershell
Import-Module LyncOnlineConnector
$sfbSession = New-CsOnlineSession
$users = Get-CsOnlineUser -Filter { ClientPolicy -eq $null } -ResultSize 500

$batch = 50
$filter = ''
$total = $users.Count
$count = 0
    $users | ForEach-Object {
    $upn = $_.UserPrincipalName
    $filter += "(UserPrincipalName -eq '$upn')"
    $batch--
    $count++
    if (($batch -eq 0) -or ($count -eq $total)) {
        $filterSB=[ScriptBlock]::Create($filter)
        Invoke-Command -Session $s -ScriptBlock {param($f) Get-CsOnlineUser -filter $f | Grant-CsClientPolicy -PolicyName "ClientPolicyNoIMURL" -Passthru | Grant-CsExternalAccessPolicy -PolicyName "FederationAndPICDefault"} -ArgumentList $filterSB

        # Reset
        $batch = 50
        $filter = ''
    } else {
        $filter += " -or "
    }
}
```

Esto buscará 500 usuarios a la vez que no tienen una directiva de cliente. Se le concederá la Directiva de cliente "ClientPolicyNoIMURL" y la Directiva de acceso externo "FederationAndPicDefault". Los resultados se procesan por lotes en grupos de 50 y, a continuación, cada lote de 50 se envía al equipo remoto.
  
## <a name="see-also"></a>Vea también

[Administrar Skype Empresarial Online con PowerShell de Office 365](manage-skype-for-business-online-with-office-365-powershell.md)
  
[Administrar Office 365 con PowerShell de Office 365](manage-office-365-with-office-365-powershell.md)
  
[Introducción a PowerShell de Office 365](getting-started-with-office-365-powershell.md)
